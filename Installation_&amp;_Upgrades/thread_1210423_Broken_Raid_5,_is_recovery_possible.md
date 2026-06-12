---
title: "Broken Raid 5, is recovery possible?"
date: 2009-07-11
forum: Installation &amp; Upgrades
---

### Post by Egenderman on 2009-07-11
I've had a lot of trouble with the Raid array I have tried to setup. Originally I had a 4 disk Raid-5 array (Software RAID, 32 bit Ubuntu 8.??), where the two first disks fell out randomly due to firmware problems. (Thank you Seagate!) I bought a fifth disk and added it to the array at one time when one of the unstable disks had failed, probably using mdadm /dev/md0 --add /dev/??? or something similar. And I had a somewhat functioning array for a short while. After installing Ubuntu x64 server, changing motherboard and removing the other unstable disk (in preparation for replacing it with another drive) I had some slight trouble mounting the array, possibly since the disks had changed mount-points. However I did get it assembled and the filesystem (xfs) mounted, and I did see a list if files in the filesystem when the computer crasched and I had to reset it. (I think the system-disk became temporarily unaccessible, possibly due to over-heating as it lay on the desk without cooling.)

Now, the array won't come online. Mdadm insists it has two disks plus one spare, which isn't enough to start it 

up. I would like to be able to mount the array since I have some files I would like to recover. Do I have any hope of doing so?

I do not have a mdadm.conf file, but I have run mdadm scans on all five disks involved:
```

/dev/sdg1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : c5445ddf:1b93c808:d2633a29:cc9056bc (local to host Imperata)
  Creation Time : Sat Mar 28 17:07:01 2009
     Raid Level : raid5
  Used Dev Size : 1465135936 (1397.26 GiB 1500.30 GB)
     Array Size : 4395407808 (4191.79 GiB 4500.90 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Sun Mar 29 18:05:01 2009
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 13ea21fb - correct
         Events : 58

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8        1        0      active sync   /dev/sda1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8       33        2      active sync
   3     3       8       49        3      active sync   /dev/sdd1

``````

/dev/sdf1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : c5445ddf:1b93c808:d2633a29:cc9056bc (local to host Imperata)
  Creation Time : Sat Mar 28 17:07:01 2009
     Raid Level : raid5
  Used Dev Size : 1465135936 (1397.26 GiB 1500.30 GB)
     Array Size : 4395407808 (4191.79 GiB 4500.90 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Sun Jun 14 09:55:41 2009
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 144f3349 - correct
         Events : 96

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       17        1      active sync   /dev/sdb1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8       49        2      active sync   /dev/sdd1
   3     3       8       65        3      active sync   /dev/sde1

``````

/dev/sdd1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : c5445ddf:1b93c808:d2633a29:cc9056bc (local to host Imperata)
  Creation Time : Sat Mar 28 17:07:01 2009
     Raid Level : raid5
  Used Dev Size : 1465135936 (1397.26 GiB 1500.30 GB)
     Array Size : 4395407808 (4191.79 GiB 4500.90 GB)
   Raid Devices : 4
  Total Devices : 3
Preferred Minor : 0

    Update Time : Sun Jun 14 20:52:36 2009
          State : active
 Active Devices : 3
Working Devices : 3
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 144fccfe - correct
         Events : 101

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8       49        2      active sync   /dev/sdd1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       0        0        1      faulty removed
   2     2       8       49        2      active sync   /dev/sdd1
   3     3       8       65        3      active sync   /dev/sde1

``````

/dev/sde1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : c5445ddf:1b93c808:d2633a29:cc9056bc (local to host Imperata)
  Creation Time : Sat Mar 28 17:07:01 2009
     Raid Level : raid5
  Used Dev Size : 1465135936 (1397.26 GiB 1500.30 GB)
     Array Size : 4395407808 (4191.79 GiB 4500.90 GB)
   Raid Devices : 4
  Total Devices : 3
Preferred Minor : 0

    Update Time : Sun Jun 14 20:52:36 2009
          State : active
 Active Devices : 3
Working Devices : 3
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 144fcd10 - correct
         Events : 101

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     3       8       65        3      active sync   /dev/sde1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       0        0        1      faulty removed
   2     2       8       49        2      active sync   /dev/sdd1
   3     3       8       65        3      active sync   /dev/sde1

``````

/dev/sdb1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : c5445ddf:1b93c808:d2633a29:cc9056bc (local to host Imperata)
  Creation Time : Sat Mar 28 17:07:01 2009
     Raid Level : raid5
  Used Dev Size : 1465135936 (1397.26 GiB 1500.30 GB)
     Array Size : 4395407808 (4191.79 GiB 4500.90 GB)
   Raid Devices : 4
  Total Devices : 3
Preferred Minor : 0

    Update Time : Sun Jun 14 20:52:36 2009
          State : active
 Active Devices : 3
Working Devices : 3
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 144fccf5 - correct
         Events : 101

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     4       8       17       -1      spare   /dev/sdb1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       0        0        1      faulty removed
   2     2       8       49        2      active sync   /dev/sdd1
   3     3       8       65        3      active sync   /dev/sde1

```

---

