---
title: "BOOT HARD HERON, not ROOT"
date: 2009-01-01
forum: Installation &amp; Upgrades
---

### Post by roy.thistle on 2009-01-01
Hi:

I have a HP Pavillion Desktop, with Vista and a free partion on C: drive.

I want to install Hardy Heron to the free partion...and boot from a USB drive (I want to keep the image on the hard disk partion)

I can find lots of info on "booting" and "rooting" from a USB drive; but, I just want to boot.

1) Can one do this (I don't want to put the boot loader on my hard disk)

2) I didn't run the UBUNTU install yet: can I choose to boot from a USB drive, when I do the install? (That would build the boot image on my USB drive...right?)

---

### Post by logos34 on 2009-01-02
Try this guide:

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

Except when you come to step 7 'Ready to install' screen, press 'Advanced' button lower  right, and change the Grub bootloader location from '(hd0)' to '**(hd1)'** or whatever the USB drive is ('**/dev/sdb**' will also work).  Change the Bios boot device to USB when you want to go into ubuntu

---

### Post by roy.thistle on 2009-01-03
Logos34:
Thanks.
I will try that...and let the forum know if it worked.
Best wishes,
r.

---

