picmd
=====

picmd is a simple wrapper script that can save a lot of keystrokes when managing a RaspberryPi device using a SSH connection. It includes most basic features like: open a remote shell, execute remote commands, start/stop/enable/disable system services, halt and reboot the system, manage software and updates, mount remote folders using sshfs and some more stuff. It has been written for Raspbian but most functions will work on most distributions and all others can be easily ported.


Install:

	Installing can be done by copying the picmd script to a */bin directory in your PATH.
	For example: /home/$USER/bin or /usr/local/bin

	The mplay function requires mplayer to be installed on the Pi.
	The mplaylist function also requires some extra hacking;
		- Copy mplaylist script on the bottom of picmd script to bin directory on the Pi.
		- Edit the script to include your preferred directory for playlists
		- Create playlists on your Pi (plain text files with one file per line using the full system path)
		- Run: picmd mplaylist   to activate a menu where you can choose the playlist to play.



[Picmd Version 0.0.1]

Usage:
        picmd [action] [arguments]

Actions:                Arguments:

        configure       :       Create new config file
        add-key         :       Upload public ssh key to Pi

        connect         :       Open a remote BASH shell
        execute         -       Any command
        execute-x11     -       gui-program (forward remote X11 apps to local xorg)

        reboot
        poweroff

        list-shares     :       List remote shares
        sshmount        -       /remote/directory /local/mount/point
        root-sshmount   -       /remote/directory /local/mount/point
        unmount         -       /local/mount/point

        service         -       service-name [start|stop|restart|status]
                        -       list  (lists all available services)
        autostart       -       service-name [enable|disable]
        firewall        -       port/type [allow|deny]
                        -       [enable|disable|status]

        upload          -       local/file /remote/directory
        download        -       /remote/file /local/directory

        update          :       Update server apt sources
        upgrade         :       Perform update and do dist-upgrade
        install         -       app-1 app-2 app-ect
        uninstall       -       app-1 app-2 app-ect
        apt-search      -       app-name
        clean           :       clean apt cache + autoremove orphaned packages

        mplay           -       /remote/path/to/music/dir/or/file.mp3
        mplaylist       -       /remote/path/to/playlist.txt

        help            :       Display this help text


Examples:

Start a Bash shell on the Pi:
	picmd connect

Execute "ls /var/www/html/" on the Pi
	picmd execute ls /var/www/html/

Mount and unmount your Pis music folder on your workstation
	picmd sshmount /media/music /home/username/Music/
	picmd unmount /home/username/Music/

Install/Remove/Update/Search Software
	picmd install package-name otherPackage stuff
	picmd uninstall package-name
	picmd upgrade
	picmd apt-search firefox

Upload/Download files to/from the Pi
	picmd upload /home/username/nice-image.png /var/www/html/my-site/
	picmd download /var/www/html/my-site/index.html /home/username/Workspace/my-site/


So, that's how things work....
