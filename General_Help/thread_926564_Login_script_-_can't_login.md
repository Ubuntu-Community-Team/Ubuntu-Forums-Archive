---
title: "Login script - can't login"
date: 2008-09-22
forum: General Help
---

### Post by danrulz12 on 2008-09-22
Ok, I've been creating an internet kiosk based on Ubuntu. The short of it all is that I have two scripts that are supposed to run on login by adding their locations to /etc/gdm/PostLogin/Default . The first script deletes the kiosk users home folder and then extracts a backed up copy to replace it:
```
#!/bin/bash
username=$1
if [[ "$username" == "" ]]
then
   username=kiosk
fi
if [[ -f /home/$username.tar.gz ]]
then
   cd /home
   rm -rf $username/*
   tar xvfz /home/$username.tar.gz
else
   echo "/home/$username.tar.gz does not exist or is not a regular file"
fi
```
This one works fine. My second script however does not. I have two files stored on a FreeNAS server, the first one is prefs.js, it belongs to firefox and it contains among other things a whitelist of sites that the kiosk can go to. It gets updated by some software on a windows box (the people hosting the kiosk aren&#8217;t exactly computer literate so windows is nice and easy). The second file is a html page that contains links to the allowed sites. On each login the NFS share is supposed to be mounted, the two files copied and then unmounted. This is the code I'm using:
```
#!/bin/bash
if [[ "$LOGNAME" == "kiosk" ]]
then
	sudo mount 10.1.1.50:/mnt/Mozilla /home/kiosk/moztmpmnt
	cp /home/kiosk/moztmpmnt/prefs.js /home/kiosk/.mozilla/firefox/dyv0q71s.default
	cp /home/kiosk/moztmpmnt/index.html /home/kiosk/.mozilla/firefox
	sudo umount home/kiosk/moztmpmnt
fi
```
I initially used visudo to allow the kiosk user to use mount and unmount, but then I realised that these scripts are run as root...And that&#8217;s where it turns pear shaped.  For whatever reason, root user gets an access denied error when it tries to mount the share. If I run the script from a terminal while logged in as kiosk the script works fine. I've tried editing the sudoers file by replacing the kiosk username with root, but that doesn&#8217;t work either. So the end result is if I include this script in /etc/gdm/PostLogin/Default nothing happens when I try to log in. I get a small spike in hard disk activity like it&#8217;s about to start loading but then it stops and I'm left at the login screen as if I hadn't done anything. I'm sure I&#8217;m missing something very simple but I just can't figure it out. I'm quite new to all things *nix so I'm trying to learn as much as I can. Sorry for the long post but I just wanted to make sure I included as much information as I can to make sure the problem is understood.

I'd be very grateful to anyone that could help me out.

Regards,
Daniel

---

### Post by stickmangumby on 2008-09-22
I don't use gdm so I'm not sure exactly how it runs login scripts. If the script is running as root, will $LOGNAME be "root" instead of "kiosk"?

What is the specific error message you're getting?

If you log in and launch a root terminal by running "sudo gnome-terminal", can you manually mount your NFS share in /home/kiosk/moztmpmnt?

There are a few workarounds I can suggest. You can create a .bashrc in your kiosk.tar.gz file that mounts the network share when the kiosk user logs in (this will run as the kiosk user). You could also run a cron job every x minutes to copy the prefs.js file across from the server to each kiosk computer.

As an aside, I don't think whitelisting sites in prefs.js will prevent users with the know how from visiting other sites. You'll need to set up a proxy server if this is important/warrants the amount of work it would involve.

---

