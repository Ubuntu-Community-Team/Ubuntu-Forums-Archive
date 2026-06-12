---
title: "Need help with USB keyboard hub and USB Memory Key"
date: 2006-04-29
forum: Hardware &amp; Laptops
---

### Post by pcormack on 2006-04-29
Hi guys,

I have a Dell keyboard with 2 USB ports on it and would like to use one of them with my USB memory stick.

> 
paul@cube:~$ lsusb
Bus 005 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 007: ID 0930:6533 Toshiba Corp. 512M USB Stick
Bus 002 Device 004: ID 413c:2002 Dell Computer Corp. SK-8125 Keyboard
Bus 002 Device 003: ID 413c:1002 Dell Computer Corp. Keyboard Hub
Bus 002 Device 002: ID 045e:008c Microsoft Corp. Wireless Intellimouse Explorer 2.0
Bus 002 Device 001: ID 0000:0000


The Toshiba Corp. 512M USB Stick is the memory key and is inserted into the keyboard.

> 
paul@cube:~$ sudo fdisk -l

Disk /dev/hda: 122.9 GB, 122942324736 bytes
16 heads, 63 sectors/track, 238216 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *       91441      193035    51203880    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/hda2          193036      236290    21800205   83  Linux
Partition 2 does not end on cylinder boundary.
/dev/hda3          236290      238202      963900    5  Extended
Partition 3 does not end on cylinder boundary.
/dev/hda5          236290      238202      963868+  82  Linux swap / Solaris

Disk /dev/hdb: 41.1 GB, 41110142976 bytes
16 heads, 63 sectors/track, 79656 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1           40636       79653    19665072    6  FAT16

Disk /dev/sda: 512 MB, 512753664 bytes
16 heads, 63 sectors/track, 993 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         994      500704+   e  W95 FAT16 (LBA)
Partition 1 has different physical/logical endings:
     phys=(992, 15, 63) logical=(993, 8, 24)


Thanks alot,
Paul.

---

### Post by pcormack on 2006-04-29
update:

When i alter fstab with the following line

/dev/sda1       /media/usbkey   vfat iocharset=utf8,umask=0000 0 0

the drive is recognised and a prompt appears, but when it is being mounted i get an error saying that only root can mount this device. Anyone know WTF is going on?

---

