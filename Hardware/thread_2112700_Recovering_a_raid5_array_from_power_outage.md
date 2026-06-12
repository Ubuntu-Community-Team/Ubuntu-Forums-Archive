---
title: "Recovering a raid5 array from power outage"
date: 2013-02-05
forum: Hardware
---

### Post by theRemix on 2013-02-05
i had a power outage, server went down, and hasn't been the same since.

```
# mdadm --assemble --scan
mdadm: /dev/sdd1 has no superblock - assembly aborted
mdadm: /dev/sdd2 has no superblock - assembly aborted
mdadm: /dev/sdd3 has no superblock - assembly aborted
mdadm: /dev/sdd5 has no superblock - assembly aborted
mdadm: /dev/sdd6 has no superblock - assembly aborted
mdadm: /dev/sdd7 has no superblock - assembly aborted

```

```
# mdadm --misc --examine /dev/sdd1
/dev/sdd1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 278ea2e2:b89984e2:33bc4bc5:59021a3e
  Creation Time : Sat Mar  6 00:43:43 2010
     Raid Level : raid5
  Used Dev Size : 34186176 (32.60 GiB 35.01 GB)
     Array Size : 102558528 (97.81 GiB 105.02 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 1

    Update Time : Mon Feb  4 18:54:39 2013
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 2
  Spare Devices : 0
       Checksum : b4dca8e1 - correct
         Events : 963131

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     3       8       49        3      active sync   /dev/sdd1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       0        0        1      faulty removed
   2     2       0        0        2      faulty removed
   3     3       8       49        3      active sync   /dev/sdd1
```

```
# mdadm --misc --examine /dev/sdd2
/dev/sdd2:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 64205578:cc795cb2:fbf2ea5a:12bfd232 (local to host OptimusPrime)
  Creation Time : Mon Mar  8 22:07:40 2010
     Raid Level : raid5
  Used Dev Size : 258799040 (246.81 GiB 265.01 GB)
     Array Size : 776397120 (740.43 GiB 795.03 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 2

    Update Time : Mon Feb  4 18:54:39 2013
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 2
  Spare Devices : 0
       Checksum : 948c4a52 - correct
         Events : 386

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     3       8       50        3      active sync   /dev/sdd2

   0     0       8        2        0      active sync   /dev/sda2
   1     1       0        0        1      faulty removed
   2     2       0        0        2      faulty removed
   3     3       8       50        3      active sync   /dev/sdd2
```


sdd3, sdd5, sdd6, and sdd7 are all about the same.



```
# mdadm --misc --examine /dev/sda1
/dev/sda1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 278ea2e2:b89984e2:33bc4bc5:59021a3e
  Creation Time : Sat Mar  6 00:43:43 2010
     Raid Level : raid5
  Used Dev Size : 34186176 (32.60 GiB 35.01 GB)
     Array Size : 102558528 (97.81 GiB 105.02 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 1

    Update Time : Mon Feb  4 18:54:39 2013
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 2
  Spare Devices : 0
       Checksum : b4dca8ab - correct
         Events : 963131

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8        1        0      active sync   /dev/sda1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       0        0        1      faulty removed
   2     2       0        0        2      faulty removed
   3     3       8       49        3      active sync   /dev/sdd1
```

sda2, sda3, sda5, sda6, and sda7 are all about the same.


```
# mdadm --misc --examine /dev/sdb1
/dev/sdb1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 278ea2e2:b89984e2:33bc4bc5:59021a3e
  Creation Time : Sat Mar  6 00:43:43 2010
     Raid Level : raid5
  Used Dev Size : 34186176 (32.60 GiB 35.01 GB)
     Array Size : 102558528 (97.81 GiB 105.02 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 1

    Update Time : Sat Feb  2 23:55:04 2013
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 1
  Spare Devices : 0
       Checksum : b4da4a83 - correct
         Events : 962928

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       17        1      active sync   /dev/sdb1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       0        0        2      faulty removed
   3     3       8       49        3      active sync   /dev/sdd1
```

sdb2, sdb3, sdb5, sdb6, and sdb7 are all about the same.

```
# mdadm --misc --examine /dev/sdc1
/dev/sdc1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 278ea2e2:b89984e2:33bc4bc5:59021a3e
  Creation Time : Sat Mar  6 00:43:43 2010
     Raid Level : raid5
  Used Dev Size : 34186176 (32.60 GiB 35.01 GB)
     Array Size : 102558528 (97.81 GiB 105.02 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 1

    Update Time : Wed Jan 16 04:47:26 2013
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : b4a5715a - correct
         Events : 21

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8       33        2      active sync   /dev/sdc1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8       33        2      active sync   /dev/sdc1
   3     3       8       49        3      active sync   /dev/sdd1
```

sdc2, sdc3, sdc5, sdc6, and sdc7 are all about the same, i'm confused to why sdb and sdc are in state "active sync" here.


is there a way to rebuild my raid partitions?

---

### Post by SaturnusDJ on 2013-02-06
Sometimes it helps to be more specific.
Stop all not working arrays, unmount the drives if they are mounted and assemble by hand.

Example:
mdadm --assemble /dev/md0 /dev/sd[a-d]1

Post the output of cat /proc/mdstat here.

Edit:
I see your post here: [http://ubuntuforums.org/showthread.php?t=1707416](http://ubuntuforums.org/showthread.php?t=1707416)
Please only post in your own topic so all information is in one place.

I would try to find out why this /dev/sda1 is busy. Maybe it's mounted somehow.

---

