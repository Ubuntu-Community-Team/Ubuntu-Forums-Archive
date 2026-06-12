---
title: "Removing Slave IDE Drive from System"
date: 2007-11-09
forum: Hardware &amp; Laptops
---

### Post by resanders on 2007-11-09
I have a two-drive system.  Ubuntu is installed on the SATA drive and the IDE drive is a slave with no operating system installed there.  I attempted to remove the slave from my system and Ubuntu failed to boot.  After returning the slave, everything booted OK.  There is nothing in the Grub menu.lst which references the slave; however, the device map does reference that drive.  The device map shows the following:  (hd0) /dev/hda and (hd1) /dev/sda.  Ubuntu is on the sda device.  My question is if I need to edit the device map in some way and then perhaps the Grub menu.lst in order for the system to boot properly.  I need some guidance here since I plan to replace the slave IDE drive with another SATA drive in the future.

---

