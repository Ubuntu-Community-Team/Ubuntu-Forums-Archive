---
title: "installation problems with 9.10"
date: 2009-10-14
forum: Installation &amp; Upgrades
---

### Post by dagarshali on 2009-10-14
Hi,
i upgraded to new version. after which ,it said the system had to restart.. upon restart, i just see flashing line saying boot from (hd0,5)..

is there a way to fix this or go back to the 9.04 version..?

I have some data here that i haven't backed up..

Any help regarding this is greatly appreciated..

regards,
Vishwa

---

### Post by Rocket2DMn on 2009-10-14
There is no way to downgrade between releases, but you can try to recover your data using a LiveCD.  If you boot the cd, you can mount the root or /home partition and copy off your data to a backup source, like an external hard disk, flash drive, or network share.  Although 9.10 is approaching release, it is still a development release and subject to problems - it is not recommended for those who don't know what they are getting in to.

After you backup your data, you should probably just do a fresh install of 9.04.  That said, the Release Candidate for 9.10 is due out in about a week, and many users choose to upgrade at that time to beat the rush.  A still fixes still get submitted between the RC and the final release, but it may be worth just doing the fresh install of 9.10 so you don't have to upgrade in a couple more weeks.

---

### Post by dagarshali on 2009-10-14
hi, 
i have nvidia driver and is see that there is bug report filed..

they say that i need to log in rescue mode and replace xorg.conf with xorg.conf.failsafe and then restart.. and upon restarting i need install the nvidia driver..

but in in /etc/x11 directory i dont see a xorg.conf.failsafe file..

the link to the bug report is here..

[https://bugs.launchpad.net/ubuntu/+bug/450318](https://bugs.launchpad.net/ubuntu/+bug/450318)

any help

---

### Post by Rocket2DMn on 2009-10-14
Had you tried to install restricted video drivers?  Are you using Kubuntu (KDE)?  I wasn't aware that you could even get to a point to see if the file was there, so we can try to troubleshoot if you can access the system normally or in recovery mode.

xorg.conf is falling by the wayside these days, and in 9.10 there isn't one by default.  If you have a file at /etc/X11/xorg.conf, try renaming it so that it isn't used
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```
Then reboot and see if you can login graphically.

---

### Post by dagarshali on 2009-10-14
thanks a lot..it now boots up..now how do i install nvidia drivers.. in the earlier versions, i would see that in th system-->adminstration-->hardware drivers..but i don't see anything now..

regards,
vishwa

---

### Post by Rocket2DMn on 2009-10-15
Restricted drivers in development releases are always a pain, so I suggest making a new thread in the Karmic Koala development forum where those with more experience in that matter can help you out - [http://ubuntuforums.org/forumdisplay.php?f=359](http://ubuntuforums.org/forumdisplay.php?f=359)
Sorry I don't know enough about them.  Cheers.

---

