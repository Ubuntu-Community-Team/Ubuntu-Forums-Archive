---
title: "GRUB prob after usb 9.04 install"
date: 2009-05-21
forum: Installation &amp; Upgrades
---

### Post by samtheozzy on 2009-05-21
Hi.  I just installed ubuntu 9.04 to my USB flash drive (full install, not a persistent live CD).  I installed the boot loader to the USB as well to avoid needing the USB in the drive when starting windows (installed on the primary HD).  GRUB works fine as long as the USB is attached to the computer but if it's not, i still get a GRUB 17 error.  This is exactly the situation I was trying to avoid by installing the bootloader to the USB.  I don't want GRUB to be loaded at all if the USB is not in the computer but for some reason it still is.

How can I arrange it so that GRUB is only loaded if the USB is attached to the computer.  My current boot priority is USB>CD>HD.

---

### Post by mechdave on 2009-05-21
It sounds like your GRUB has been installed to the hard drive boot sector, the way to fix this would be to boot windows rescue (from install disk) and fixmbr. Secondly you will need to install grub on the master boot record of your usb stick. Here is the GRUB manual url --> [http://www.gnu.org/software/grub/manual/grub.html]("http://www.gnu.org/software/grub/manual/grub.html") this will tell you all you need to know to be able to do it... 

Cheers,
   Mechdave

---

