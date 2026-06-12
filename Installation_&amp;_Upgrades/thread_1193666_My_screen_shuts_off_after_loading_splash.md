---
title: "My screen shuts off after loading splash"
date: 2009-06-21
forum: Installation &amp; Upgrades
---

### Post by TheMASTER69 on 2009-06-21
Hey everyone!:)
I have what it seems like a very odd problem as I cant find it anywhere on the internet. So heres the details...

I have a G3 Bondi Blue iMac. Thats as specific as I know since there is no operating system currently on it to find the true specs.

Alright so this has happened with Debian, Ubuntu, and Xubuntu.

First i boot from the CDROM and install using the alternate cd (Hardy). The install is successful using both install and install video=ofonly.

Once the computer reboots the computer does the following...
-On installs where install was used the splash screen loads and               once finished when it should go to the desktop environment my built in iMac monitor shuts off and the power light tunes orange forever...
-On installs where install video=ofonly is used the reboot doesn't even get to the splash screen.

Now i am fairly new to the Linux scene so I'm not very techie with this all and thats probably why i need help with this.:confused:

Please any help is much appreciated. Thank you in advance.

---

### Post by quixote on 2009-06-22
Booting is failing at the point where X windows should load, if I understand correctly.  That can happen when the settings for video in /etc/X11/xorg.conf are not right for your graphics hardware.

I don't know much about this, but I would suggest searching the forums for your graphics chip, or at least your model of iMac, and xorg.conf and see what comes up.

If nothing, then that's probably not it.  But if other people have the same problem, then maybe that will help you figure out which question to ask next.  Sometimes it takes several rounds. :)

---

