---
title: "Multiple Ubuntus at start up"
date: 2009-08-21
forum: Installation &amp; Upgrades
---

### Post by albey20 on 2009-08-21
Hi every one, first of all sorry about the bad spelling english is not my mother language. 
My problem is this, I have a pc with Ubuntu 9.04 and WinXP, when I first install Ubuntu I only have to select betwin one Ubunt and WinXP, now some upgrades later the list of Ubunts at the start up its getting bigger I realy dont care abut it because I select the first Ubunt that apear, but the rest of the family doesnt like to scroll down searching for WinXP, Can I delet the previews Ubunts selections and just leave the new one?

---

### Post by raymondh on 2009-08-21
> **albey20 said:**
> Hi every one, first of all sorry about the bad spelling english is not my mother language. 
My problem is this, I have a pc with Ubuntu 9.04 and WinXP, when I first install Ubuntu I only have to select betwin one Ubunt and WinXP, now some upgrades later the list of Ubunts at the start up its getting bigger I realy dont care abut it because I select the first Ubunt that apear, but the rest of the family doesnt like to scroll down searching for WinXP, Can I delet the previews Ubunts selections and just leave the new one?

Hello Albey,

Are you referring to kernels?  They're the ones with 2.X.X-Y format?  Or are you given 2 or more Ubuntu choices.

You can install search in synaptic and install startupmanager.  It is GUI based.  In it, you can set defaults (i.e. which kernel to boot ... how long ... even which OS to default to .. etc).  Startupmanager also writes to the menu.lst.

If you want to learn, you can also edit the /boot/grub/menu.lst.  Here is a [good guide written]("http://members.iinet.net.au/~herman546/p15.html#menu.lst") by herman.

Post back if you need clarifications.

---

