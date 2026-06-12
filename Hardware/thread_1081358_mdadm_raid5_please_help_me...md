---
title: "mdadm raid5: please help me.."
date: 2009-02-26
forum: Hardware
---

### Post by kaefert66014235 on 2009-02-26
I've got a software raid5 on 4 harddisks (sdb1,sdc1,sdd1,sde1) and somehow today morning it started acting strange (files took endlessly long to read). I had no powersurge or anything, the system was running without a problem for many weeks. Now when i look at my md0 device:

```
kaefert@Blechserver:~$ sudo mdadm --misc --detail /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Thu Feb 21 08:01:14 2008
     Raid Level : raid5
     Array Size : 1465151808 (1397.28 GiB 1500.32 GB)
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Thu Feb 26 18:12:33 2009
          State : clean, degraded
 Active Devices : 2
Working Devices : 3
 Failed Devices : 1
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : ce77e35e:ae8afd5f:e955c44f:50edb531
         Events : 0.104474

    Number   Major   Minor   RaidDevice State
       0       8       49        0      active sync   /dev/sdd1
       1       0        0        1      removed
       2       0        0        2      removed
       3       8       65        3      active sync   /dev/sde1

       4       8       17        -      spare   /dev/sdb1
       5       8       33        -      faulty spare   /dev/sdc1

```

This doesn't look good, it seems sdc1 is fried, okey, so far not that bad, thats what a raid is for so i could get a replacement for it, but why is sdb1 marked as spare?! and shouldn't i still be able to read the filesystem when only one drive is dead? 

When I try to mount it, I get the following entry to dmesg:
```
[10919.008000] ReiserFS: md0: warning: sh-2006: read_super_block: bread failed (dev md0, block 2, size 4096)
[10919.008000] ReiserFS: md0: warning: sh-2006: read_super_block: bread failed (dev md0, block 16, size 4096)
[10919.008000] ReiserFS: md0: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on md0
```

when I remove a harddisk and add it again it doesn't show up in the spot it should, but as spare..

```
kaefert@Blechserver:~$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Thu Feb 21 08:01:14 2008
     Raid Level : raid5
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Thu Feb 26 19:00:41 2009
          State : active, degraded, Not Started
 Active Devices : 2
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 2

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : ce77e35e:ae8afd5f:e955c44f:50edb531
         Events : 0.104498

    Number   Major   Minor   RaidDevice State
       0       8       49        0      active sync   /dev/sdd1
       1       0        0        1      removed
       2       0        0        2      removed
       3       8       65        3      active sync   /dev/sde1

       4       8       33        -      spare   /dev/sdc1
       5       8       17        -      spare   /dev/sdb1

```

okey.. now i added another hard-disk, but how can I make him recognize sdb1 as RaidDevice 1 again? the SMART status says that the disk has no problems...

```
kaefert@Blechserver:~$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Thu Feb 21 08:01:14 2008
     Raid Level : raid5
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
   Raid Devices : 4
  Total Devices : 5
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Thu Feb 26 19:00:41 2009
          State : active, degraded, Not Started
 Active Devices : 2
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 3

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : ce77e35e:ae8afd5f:e955c44f:50edb531
         Events : 0.104498

    Number   Major   Minor   RaidDevice State
       0       8       65        0      active sync   /dev/sde1
       1       0        0        1      removed
       2       0        0        2      removed
       3       8       81        3      active sync   /dev/sdf1

       4       8       49        -      spare   /dev/sdd1
       5       8       33        -      spare   /dev/sdc1
       6       8       17        -      spare   /dev/sdb1
kaefert@Blechserver:~$ sudo mdadm --run /dev/md0
mdadm: failed to run array /dev/md0: Input/output error

```

---

