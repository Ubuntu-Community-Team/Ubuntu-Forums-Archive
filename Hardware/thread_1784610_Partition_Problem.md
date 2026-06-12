---
title: "Partition Problem"
date: 2011-06-17
forum: Hardware
---

### Post by neuxioz on 2011-06-17
I am trying to fix an overlapping partition problem.
Here is my fdisk -l output:
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf601f601

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7618    61183967+  83  Linux
/dev/sda3            7618       29290   174087169    f  W95 Ext'd (LBA)
/dev/sda4           29290       30401     8924160    c  W95 FAT32 (LBA)
/dev/sda5           13993       20367    51200000    7  HPFS/NTFS
/dev/sda6           20367       24997    37188835+   7  HPFS/NTFS
/dev/sda7           26907       29185    18301952   83  Linux
/dev/sda8           29185       29290      843776   82  Linux swap / Solaris
/dev/sda9            7618       13993    51207168    b  W95 FAT32

Partition table entries are not in disk order

As you can see, /dev/sda3 overlaps with /dev/sda9, /dev/sda5 and /dev/sda6. I want to get rid of /dev/sda3 while still leaving the the data on sda3 sda5 and sda6 intact. How do I do that???:):)

---

