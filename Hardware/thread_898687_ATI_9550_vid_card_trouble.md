---
title: "ATI 9550 vid card trouble"
date: 2008-08-23
forum: Hardware
---

### Post by jtango on 2008-08-23
I have just gotten a radeon 9550 vid card and it does not seem to like my monitor.  The splash screen comes up normally and I am able to log in but when the desktop comes up the display is very distorted.  I can tell that moving the mouse around is moving the cursor but that is about it.   I can get the terminal session to work but I have no idea how to get the desktop working.

Any help would be greatly appreciated!

---

### Post by overdrank on 2008-08-23
> **jtango said:**
> I have just gotten a radeon 9550 vid card and it does not seem to like my monitor.  The splash screen comes up normally and I am able to log in but when the desktop comes up the display is very distorted.  I can tell that moving the mouse around is moving the cursor but that is about it.   I can get the terminal session to work but I have no idea how to get the desktop working.

Any help would be greatly appreciated!

Hi and welcome, what was the model of the previous graphics card? If you are using Hardy 8.04 you can try and use the xfix option after booting into recovery mode which is usually the second choice from the grub.

---

### Post by libra1780 on 2008-08-23
i have an ati as well, and last days i was tweaking around in xorg.conf..

i got that problem in 2 cases.. 
1. loading xgl without 3d window manager *lol*
2. option misconfiguration in xorg

so.. 
1. maybe you would like to try to comment(#) all options in device and extensions section ->xorg.conf
2, like 1 but set driver (found in xorg.conf) to vesa, start x and download the right driver from ati. got this issue on a laptop, on whitch unbuntu used "ati" driver module and actually didn't want to work..

reply if you need step-to-step advice

---

