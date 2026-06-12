---
title: "Troubles booting Home Server"
date: 2014-10-03
forum: Hardware
---

### Post by scifimyth on 2014-10-03
I have just put together a machine to be a home server (file, print, possibly other uses) using Ubuntu Server 14.04.1.  I managed to get it installed from a USB key and it reported a successful install.  I pulled the key when the installer said to and then rebooted.  The system stops running after the post with a message saying "Loading Operating System..." I don't see any sign of GRUB.

Intel Core I7-870
Gigabyte P55a-UD3
4gb Mushkin RAM (new)
Nvidia Geforce 6600GT (spare laying around, still good)
Hitachi 320gb 2.5" HD (Boot, Sata 0)
2x Seagate 3tb HD (Data, Sata 1,2)
750watt PSU (New)

All the hardware has been tested and boots fine.  HDs have been checked and no warnings in SMART or performance issues.  The board was running Windows 7 in another system prior to this for several years. I have tried clearing the CMOS and setting just the basics with all else at default with no change.  The RAM and CPU are detected properly and the drives are all detected on startup, as well as in the initial setup of the system.

---

### Post by weatherman2 on 2014-10-03
During install, did you have a choice of where to write the Grub boot sector? Presumably you chose the 320GB drive of course.  Are you sure this drive is the first drive in the boot order (according to the BIOS)?  That is, are you sure it's not stuck trying to boot off of one of the other drives instead?

For fun, yank the two 3TB drives and try booting without them, assuming nothing is required on them for boot.

What partitioning did you use for the install?  You have at least a / partition and a swap.  What else?  Mounted where?

You can try booting Ubuntu from USB again and trying to re-install Grub on the 320GB as well.  Google for "ubuntu grub chroot."  I have had good luck with the chroot method of restoring Grub.

---

