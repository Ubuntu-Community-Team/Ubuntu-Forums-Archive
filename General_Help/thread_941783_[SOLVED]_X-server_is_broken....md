---
title: "[SOLVED] X-server is broken..."
date: 2008-10-08
forum: General Help
---

### Post by G-Dub on 2008-10-08
X-server is broken and when i load up linux it brings me to tty1 and I cannot change to tty7. I tried repairing X in recovery mode, all it told me is that X-server is broken. So I am unable to load any GUI. What should I do here? Is there a way of removing X and reinstalling it?

---

### Post by hessiess on 2008-10-08
what errors do you get if you run 'startx' ?, have you installed or uninstalled anything recently?

---

### Post by caleb12 on 2008-10-08
Log in at tty1 and like hessiess suggested try startx - you can also try /etc/init.d/gdm start (or kdm), and see what that result is... And finally, post any errors from /var/log/Xorg.0.log

---

### Post by G-Dub on 2008-10-08
Thank you so much for the suggestions!

So i just upgraded from KDE 4.1.1 to KDE 4.1.2 and I also tried installing ssh server.

After i restarted i got this output:
```
Starting up...
Loading, please wait
usplash: setting mode 1152x864 failed
usplash: using mode 1024x768
kinit: name_to_dev_t(/dev/disk/by_uuid/177f375e-1ec7-4bec-9ca7-670ccbf75357)=sbd1 (8, 17)
kinit: trying to resume from /dev/disk/by_uuid/177f375e-1ec7-4bec-9ca7-670ccbf75357
kinit: No resume image, doing normal boot...

Ubuntu  8.04.1 garrett-desktop tty1

garrett-desktop login:_ 
```

I tried "startx" and it gave me this output:

```
 /etc/X11/X is not executable
giving up
xinit: no such directory (errno 2): unable to connect to x server
xinit: no such process (errno 3): server error
```

I tried looking up /var/log/xorg.0.log and it said file not found.

When i try ```
sudo /etc/init.d/kdm-kde4 restart
``` it tells me that it is running.

I try going at Alt + F7 and it won't let me.

Did the SSH server overwrite X?

---

### Post by caleb12 on 2008-10-08
hmmmm, nasty... OK, first off /var/log/Xorg.0.log - the X in Xorg is capitilized. I would CD into the /var/log/ directory, do an ls and cat the log file. If you can post the whole file here that's even better... 

Secondly, cd /etc/X11/ and do an ls -al - check that X is a symbolic link to /usr/bin/Xorg. If it is not then, rm X and ln -s /usr/bin/Xorg X 

then issue the startx command again. 

Also, if you are logging in as root then switch ( su ) to your user before performing the startx. 

If all else fails - dpkg-reconfigure -phigh xserver-xorg 

If that fails... apt-get --reinstall install xserver-xorg-core xserver-xorg 

or if you want to be thorough you could apt-get --reinstall install xserver-xorg-*  
however that may not be the best result since it will install everything starting with xserver-xorg- which is alot of packages...

---

### Post by G-Dub on 2008-10-08
yeah somehow X got uninstalled. i have no idea how. ```
sudo apt-get install xserver-xorg
``` did the trick! Thanks!

---

