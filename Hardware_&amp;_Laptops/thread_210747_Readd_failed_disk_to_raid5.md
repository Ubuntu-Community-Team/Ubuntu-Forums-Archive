---
title: "Readd failed disk to raid5"
date: 2006-07-07
forum: Hardware &amp; Laptops
---

### Post by starNIX on 2006-07-07
[SIZE=1]Can anyone tell me how to make /dev/hdc1 readd to the array?  It failed for some reason but I don't think it should have since it is only a year old.


/dev/md0:
        Version : 00.90.01
  Creation Time : Tue Aug 16 16:58:46 2005
     Raid Level : raid5
     Array Size : 351654528 (335.36 GiB 360.09 GB)
    Device Size : 117218176 (111.79 GiB 120.03 GB)
   Raid Devices : 4
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Fri Jul  7 08:25:13 2006
          State : clean, degraded
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : right-symmetric
     Chunk Size : 4K

           UUID : 2c1270f1:e11747b5:2e234cec:48c23cf2
         Events : 0.12881228

    Number   Major   Minor   RaidDevice State
       0       3       65        0      active sync   /dev/hdb1
       1       0        0        -      removed
       2      22       65        2      active sync   /dev/hdd1
       3      34        1        3      active sync   /dev/hdg1
[/SIZE]

---

