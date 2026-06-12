---
title: "Partition Table has been corrupted by Upgrade"
date: 2009-06-27
forum: Installation &amp; Upgrades
---

### Post by BrokenPoet on 2009-06-27
Greetings!  My partition table has been corrupted resulting in an inability to reload the latest version (9.04) as a fresh install.  The only system changes that may have caused the partition tables to change were a) Upgrade (not fresh install) to 9.04 from 8.10 or b) Installation of Vista SP1 (? Whichever was most recent, I don't boot into it frequently.)

   I noted the problem when trying to conduct a fresh install of 9.04 from CD after the upgrade messed up my NVIDIA settings.  There have been a few threads on the topic, but I would like some expert assistance prior to re-writing my partition tables via the terminal.

Can someone provide guidance as to the correct sfdisk command to repair my tables? 

Thanks!

```
~$ sudo fdisk -lu

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x30000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *   619898880   625139711     2620416    c  W95 FAT32 (LBA)
/dev/sda2          178176    21149695    10485760    7  HPFS/NTFS
/dev/sda3   *    21149696   114370551    46610428    7  HPFS/NTFS
/dev/sda4       114382861   625139711   255378425+   f  W95 Ext'd (LBA)
/dev/sda5       619898880   625139711     2620416   dd  Unknown
/dev/sda6       114382863   153436814    19526976   83  Linux
/dev/sda7       153436878   615980294   231271708+  83  Linux
/dev/sda8       615980358   619884089     1951866   82  Linux swap / Solaris

Partition table entries are not in disk order

~$ sudo sfdisk -d
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=619898880, size=  5240832, Id= c, bootable
/dev/sda2 : start=   178176, size= 20971520, Id= 7
/dev/sda3 : start= 21149696, size= 93220856, Id= 7, bootable
/dev/sda4 : start=114382861, size=510756851, Id= f
/dev/sda5 : start=619898880, size=  5240832, Id=dd
/dev/sda6 : start=114382863, size= 39053952, Id=83
/dev/sda7 : start=153436878, size=462543417, Id=83
/dev/sda8 : start=615980358, size=  3903732, Id=82

~$ sudo parted /dev/sda1 print
Model: Unknown (unknown)
Disk /dev/sda1: 2683MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  2683MB  2683MB  fat32  
```

---

### Post by BrokenPoet on 2009-07-06
Bump?

---

