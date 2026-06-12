---
title: "Remove GRUB with LiveCD?"
date: 2009-08-13
forum: Installation &amp; Upgrades
---

### Post by rodtempleton on 2009-08-13
Good morning,

My setup is (was) as follows:

Drive 0: 80GB Windows XP 
Drive 1: Ubuntu 9.04

My brother in law, for some unknown reason, went into the Windows disk management, and removed the Linux partitions, and formatted the drive with NTFS, and then copied some data onto that drive for me.  I wasn't particularly happy about this, but....

However, last night when Windows Update ran, it forced a reboot of the machine, and when GRUB tried to load, it barfed.  Unfortunately I don't have an easily obtainable Windows CD to use to repair the boot loader.

Is there any way to use the live CD to go in and remove GRUB so that the machine will boot into Windows again?  Or is removing GRUB not going to be enough?  

Or would a Damn Small Linux or Knoppix CD do the trick?

Any information that anyone could provide would be very greatly appreciated.

(And yes, I'm going to password protect everything so that people can't mess with my machine ever again, too.  Lesson learned.)

Thanks,
Rod Templeton

---

### Post by SuperSonic4 on 2009-08-13
Grub should be able to direct the computer to the windows bootloader without an issue but if it cannot it's screwed

normally grub has a chainloader function which simply links to the windows boot

---

### Post by raymondh on 2009-08-13
Try to download [Hiren's CD]("http://www.hiren.info/pages/bootcd") and use its' MBR tools to fix/restore your MBR.

You can also try supergrubdisk.

If you choose to try to re-install GRUB, here's [Herman's site]("http://members.iinet.net.au/~herman546/p15.html") for workarounds/tips.

Good luck.

Raymond

---

### Post by sokolenko on 2009-08-13
I think that removing grub will fit,
here you are manual how to do that
ntcompatible.com/How_to_**remove**_**GRUB**_loader_t28242.html

---

