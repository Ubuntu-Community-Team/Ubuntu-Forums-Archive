---
title: "Error 17"
date: 2009-10-25
forum: Installation &amp; Upgrades
---

### Post by jawadahmed on 2009-10-25
I have installed ubuntu 8.04 along with my old windows xp.
I get to boot into grub but when i select ubuntu from there i get error 17
I have searched these forums and got many solutions, tried them but unfortunately no solution helped me.
I really like to use ubuntu but its pushing me away (9.04 had i/o error after completion of setup and removal of tray and now 8.04 have error 17)

Can anyone please help me solve the error 17 please. I have also modified device.map and dont know how to make it to previous version.

Here is my PC info.
Intel, 2 hard disks, 1 sata
Installed 8.04 from usb disk.
windows xp and ubuntu on 2nd hard disk.

Here is info from sudo fdisk -lu
```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0a4ba9cb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          64   102178085    51089011    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2       102178086   121184738     9503326+   f  W95 Ext'd (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda3       121184763   177810808    28313023    7  HPFS/NTFS
Partition 3 does not end on cylinder boundary.
/dev/sda4       177810815   234440999    28315092+   7  HPFS/NTFS
Partition 4 does not end on cylinder boundary.
/dev/sda5       102178110   121184738     9503314+   7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x74401d35

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        4524    30722483    15358980    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2        50252694   625142383   287444845    f  W95 Ext'd (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sdb3        30722484    50252591     9765054   83  Linux
Partition 3 does not end on cylinder boundary.
/dev/sdb5       205703968   625142383   209719208    7  HPFS/NTFS
/dev/sdb6        50252696    54156803     1952054   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdc: 3511 MB, 3511681024 bytes
109 heads, 62 sectors/track, 1014 cylinders, total 6858752 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb0bcd68e

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?  3223366781  3470046704   123339962   78  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(518, 102, 15) logical=(476970, 56, 50)
Partition 1 has different physical/logical endings:
     phys=(743, 0, 62) logical=(513472, 47, 15)
Partition 1 does not end on cylinder boundary.
/dev/sdc2   ?   432871117  1208554935   387841909+  10  OPUS
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(205, 7, 0) logical=(64053, 15, 14)
Partition 2 has different physical/logical endings:
     phys=(920, 235, 50) logical=(178833, 24, 34)
Partition 2 does not end on cylinder boundary.
/dev/sdc3   ?  1869562563  3788792630   959615034   8b  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(260, 125, 54) logical=(276644, 38, 56)
Partition 3 has different physical/logical endings:
     phys=(893, 46, 60) logical=(560638, 16, 35)
Partition 3 does not end on cylinder boundary.
/dev/sdc4   ?  1347420160  1355743253     4161547    a  OS/2 Boot Manager
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(269, 111, 50) logical=(199381, 54, 15)
Partition 4 has different physical/logical endings:
     phys=(0, 0, 0) logical=(200613, 9, 42)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order
```These are my hd1 (second hard disk) partitions
```
 setup (hd1,
 Possible partitions are:
   Partition num: 0,  Filesystem type unknown, partition type 0x7
   Partition num: 2,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 4,  Filesystem type unknown, partition type 0x7
   Partition num: 5,  Filesystem type unknown, partition type 0x82

```If any one solve this, i would be his fan :(

---

### Post by dstew on 2009-10-26
When you get the error 17 message, is there any text associated with it? That is, does it just say "error 17" and lock, or does it say "error 17, cannot mount selected partition"? If you get no text, it is probably a grub stage 1.5 error, and we will need to re-install the boot loader. If there is text with it, it might only be a mis-configuration, and that is easier to fix.

---

### Post by stlsaint on 2009-10-26
Sounds like you may need to reinstall grub. please see here for explanation: [Restore Grub]("http://doc.gwos.org/core:grub:restore").

---

