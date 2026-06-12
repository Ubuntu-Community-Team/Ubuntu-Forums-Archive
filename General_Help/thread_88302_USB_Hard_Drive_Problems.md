---
title: "USB Hard Drive Problems"
date: 2005-11-09
forum: General Help
---

### Post by TrumpetMan258 on 2005-11-09
I can't access my Western Digital Passport drive at all.  The icon shows up on the desktop, but when I try to access it, I get this error message:

> Could not mount device.
The reported error was:
mount: only root can mount /dev/sdb1 on /mnt/captive-wd_passport

This problem just started a few days ago.  Before that, everything was working fine.  I don't know if I did something to screw things up, or what happened.

The drive currently uses NTFS, but I want to reformat it so I can write to it.  However, I first need to get some stuff off of it for safekeeping.  That's why I need this problem fixed.

---

### Post by Remmelas on 2005-11-10
i'm not entirely sure, but you could edit your fstab file and add the word 'user' to the options for your usb drive mount line(provided that fstab has one for it)

---

### Post by TrumpetMan258 on 2005-11-10
Okay, I did that, but now I get a different error:
> Could not mount device.
The reported error was:
W32 filesystem .sys module not found: /var/lib/captive/ntfs.sys at /sbin/mount.captive-ntfs line 65.
You should run captive-install-acquire(1) of 'captive-install' package,
otherwise you can also acquire this file from URL:
[http://www.microsoft.com/WindowsXP/pro/downloads/servicepacks/sp1/checkedbuild.asp](http://www.microsoft.com/WindowsXP/pro/downloads/servicepacks/sp1/checkedbuild.asp)

---

### Post by Remmelas on 2005-11-13
wow, Not sure where to go from there.  Looks like we are past the 'only root can mount' error, but i'm unsure of how to help from here with your next error.  Hopefully some of the other fine souls on this forum have an idea.

---

### Post by aysiu on 2005-11-13
Is it any different if you do a "coldplug" on the device? That is, if you turn off your computer, plug the device in, then reboot with the device still plugged in? You may also want to try using a live recovery CD like Knoppix, which is pretty good about automounting NTFS drives and hardware detection in general. After you get the files off, you may want to reformat it as FAT32.

---

