---
title: "programs wont install"
date: 2008-09-23
forum: Hardware
---

### Post by neba on 2008-09-23
I am trying to install skype and every thing I do it through the terminal I get this error

Configuration file `/etc/dbus-1/system.d/skype.conf', does not exist on system.
Installing new config file as you request.

Skype worked before I make my pc a dual boot. Also I am having problems with my usb interface. when I plug my usb in I get this error message

Cannot mount volume.
Invalid mount option when attempting to mount the volume 'USB DISK'.

my usb works in fedora 9.

thank you

---

### Post by neba on 2008-09-27
this is my fdisk -l
how this will help?

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4d384d37

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3196    25671838+  83  Linux
/dev/sda2            3197       12124    71714160    5  Extended
/dev/sda3           12125       12161      297202+  82  Linux swap / Solaris
/dev/sda5            3197       11754    68742103+  83  Linux
/dev/sda6           11755       12124     2971993+  82  Linux swap / Solaris

Disk /dev/sdb: 1006 MB, 1006632960 bytes
65 heads, 32 sectors/track, 945 cylinders
Units = cylinders of 2080 * 512 = 1064960 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         942      978928    6  FAT16
Partition 1 has different physical/logical endings:
     phys=(956, 64, 32) logical=(941, 18, 32)

---

