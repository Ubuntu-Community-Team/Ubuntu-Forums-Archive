---
title: "USB drive not detected at all; borked partition table?"
date: 2005-11-17
forum: Hardware &amp; Laptops
---

### Post by Hyphenated on 2005-11-17
My USB thumb drive was working fine in windows and in linux.

I poked around partitioning and reformatting it with cfdisk and mkdosfs. I did something wrong; I forget what it was (argh). Now the drive is not detected at all in either windows or linux.

When I plug it in, the only new thing in dmesg is
> ehci_hcd 0000:00:02.1: port 3 reset error -110
hub 2-0:1.0: hub_port_status failed (err = -32) "port 3" changes to whichever port I try.

The drive had previously been /dev/hdb, but now it does not exist in /dev. It also no longer shows up at all in /proc/bus/usb/devices, nor in lsusb.

I have made no configuration changes to my system since the drive was working.

All the information I have found assumes that a drive works enough to be present in /dev. Does anyone know how I can fix my drive, or where I can look to get more information to try and figure out how to fix it?

---

