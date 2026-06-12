---
title: "GRUB Error."
date: 2009-08-10
forum: Installation &amp; Upgrades
---

### Post by persisto on 2009-08-10
I wanted to install Ubuntu 9.04 on a USB Harddisk, attached to my (work-windows portable.) My intention was to make it work exactly like booting from a USB key.(which works fine.)

The installation process went smoothly. I am sure to have selected Ubuntu to be installed on the USB drive.

My problem:
If I try to boot with or without the USB drive I get GRUB Error 2 or 21 (It changes.)

I can still boot on the CD ROM.

This being my work PC, I consider not bing able to boot Win XP a more serious problem than Ubuntu not booting from my USB drive.

I guess I would have to remove GRUB, and would like advise

(I am not very familiar with Ubuntu/Linux: basics only)

Thanks in advance.

Pete

---

### Post by phillw on 2009-08-10
This article should answer your problem ..

[http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

Regards,

Phill.

---

### Post by ronparent on 2009-08-10
It sounds like you installed grub to the master boot record of you windows drive. If you want windows to boot normally when the key isn't in you have to restore the win xp MBR (using the win xp installation disk - if you have it). You should then setup your key with a grub MBR which will allow booting to either ubuntu or xp. To boot from the usb, you then either have to set the bios to look first at a usb key to boot (if that option is available in bios) or, you have to look for an option in the initial bios boot screen to boot from an alternate drive. If nerither of those option are available or accesable by you on the work compter, you may need the assistance of the computer administrator to set it up. Don't expect much. Your employer may have strict rule on use of the work computer that would prevent the administrater from assisting you.

---

### Post by persisto on 2009-08-10
RESOLVED.
Thanks for the answers, looked thru them. (The linked ones)
- I have an XP CD but don't have the admin pass word. (IT support at work will not take to kindly to my "efforts", no disaster, just embarrassing, so i'll try to avoid asking them for help.)

-I dont like the Aborted install method much.

-and 22 pages of discussion of a solution did not inspire confidence. (I like clear cut solutions)

Looked around for a tool to read the XP admin password found this [http://ubcd.sourceforge.net/index.html]("http://ubcd.sourceforge.net/index.html"), which includes Super Grub Disk, (Described here [http://www.cyberciti.biz/tips/super-grub-disk-fix-windows-linux-boot.html]("http://www.cyberciti.biz/tips/super-grub-disk-fix-windows-linux-boot.html")

It has an option to simply remove GRUB. (Similar to FIXMBR in the repair console, but without the need for the Admin password or XP CD.) Simple as "Bonjour" as they say here; I am back in business.
(I tried by the way to install Ubuntu on a USB connected **harddisk** for space. (X)Ubuntu from a USB key works without any interference with WIndows.)

---

### Post by ronparent on 2009-08-10
Glad to hear you have it worked out.

---

