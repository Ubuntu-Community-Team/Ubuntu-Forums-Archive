---
title: "partition table"
date: 2008-08-02
forum: General Help
---

### Post by hirohitosan on 2008-08-02
trying to install xubuntu I think I destroyed the patition table on my HDD.

fdisk give me this:

```
 sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcccdcccd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1658    13313128+   c  W95 FAT32 (LBA)
Partition 1 does not end on cylinder boundary.
/dev/sda2            2385        4484    16866299    f  W95 Ext'd (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda3            1658        1746      710608+  82  Linux swap / Solaris
Partition 3 does not end on cylinder boundary.
/dev/sda4            1747        2384     5124735   83  Linux
/dev/sda5            3335        4484     9230728+   7  HPFS/NTFS
/dev/sda6            2385        3334     7630812   83  Linux
/dev/sda7            2385        2385           0+  83  Linux

Partition table entries are not in disk order


```

and gparted doesn't recognize any partitions on my HDD

I don't understand well the output of fdisk command. Can I restore my partition table?

thanks a lot

---

