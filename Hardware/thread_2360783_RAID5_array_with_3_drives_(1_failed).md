---
title: "RAID5 array with 3 drives (1 failed)"
date: 2017-05-08
forum: Hardware
---

### Post by feanor_arcamenel on 2017-05-08
I have lost one of the drives due to bad sector in a RAID5 array with 3 drives. As a result, the array became inactive.

When I tried to recreate the array with the following command:
```
sudo mdadm --assemble --force /dev/md0 /dev/sdc1 /dev/sdd1 /dev/sde1
```
it could activate the array with a State : clean, degraded. Below is the output of "sudo mdadm -D /dev/md0":

```
/dev/md0:
        Version : 1.2
  Creation Time : Mon May  8 15:12:01 2017
     Raid Level : raid5
     Array Size : 7813771264 (7451.79 GiB 8001.30 GB)
  Used Dev Size : 3906885632 (3725.90 GiB 4000.65 GB)
   Raid Devices : 3
  Total Devices : 2
    Persistence : Superblock is persistent

  Intent Bitmap : Internal

    Update Time : Mon May  8 17:24:24 2017
          State : clean, degraded 
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : ubuntuBox:0  (local to host ubuntuBox)
           UUID : 95c275e4:1b78840f:10f5974b:fe142ac8
         Events : 60

    Number   Major   Minor   RaidDevice State
       0       8       33        0      active sync   /dev/sdc1
       2       0        0        2      removed
       2       8       65        2      active sync   /dev/sde1
```

When I mount this device, I can reach only part of my files. Luckily, I have backup of a large part of the missing files, except for the most recent ones. However, I would like to ask if there is a way to save the raid array by getting a new healthy array.

Here is the output for "cat /proc/mdstat":

```
Personalities : [raid6] [raid5] [raid4] [linear] [multipath] [raid0] [raid1] [raid10] 
md0 : active raid5 sdc1[0] sde1[2]
      7813771264 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/2] [U_U]
      bitmap: 0/30 pages [0KB], 65536KB chunk

unused devices: <none>
```


This is the output for "sudo mdadm --examine /dev/sd[cde]1":

```
/dev/sdc1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 95c275e4:1b78840f:10f5974b:fe142ac8
           Name : ubuntuBox:0  (local to host ubuntuBox)
  Creation Time : Mon May  8 15:12:01 2017
     Raid Level : raid5
   Raid Devices : 3

 Avail Dev Size : 7813771264 (3725.90 GiB 4000.65 GB)
     Array Size : 7813771264 (7451.79 GiB 8001.30 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262056 sectors, after=0 sectors
          State : clean
    Device UUID : 3e1f8352:8b51d20b:d13f2301:0c25ed92

Internal Bitmap : 8 sectors from superblock
    Update Time : Mon May  8 17:24:24 2017
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : ef119df - correct
         Events : 60

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 0
   Array State : A.A ('A' == active, '.' == missing, 'R' == replacing)

/dev/sdd1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x3
     Array UUID : 95c275e4:1b78840f:10f5974b:fe142ac8
           Name : ubuntuBox:0  (local to host ubuntuBox)
  Creation Time : Mon May  8 15:12:01 2017
     Raid Level : raid5
   Raid Devices : 3

 Avail Dev Size : 7813771264 (3725.90 GiB 4000.65 GB)
     Array Size : 7813771264 (7451.79 GiB 8001.30 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
Recovery Offset : 0 sectors
   Unused Space : before=262056 sectors, after=0 sectors
          State : clean
    Device UUID : e4a6bbbb:f34c95db:29f02738:f9ac2358

Internal Bitmap : 8 sectors from superblock
    Update Time : Mon May  8 15:17:40 2017
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : 442ab759 - correct
         Events : 18

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 1
   Array State : AAA ('A' == active, '.' == missing, 'R' == replacing)

/dev/sde1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 95c275e4:1b78840f:10f5974b:fe142ac8
           Name : ubuntuBox:0  (local to host ubuntuBox)
  Creation Time : Mon May  8 15:12:01 2017
     Raid Level : raid5
   Raid Devices : 3

 Avail Dev Size : 7813771264 (3725.90 GiB 4000.65 GB)
     Array Size : 7813771264 (7451.79 GiB 8001.30 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262056 sectors, after=0 sectors
          State : clean
    Device UUID : dfee12e5:90d310e9:4719f740:8b5dbf0c

Internal Bitmap : 8 sectors from superblock
    Update Time : Mon May  8 17:24:24 2017
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : 38657d7d - correct
         Events : 60

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 2
   Array State : A.A ('A' == active, '.' == missing, 'R' == replacing)
```

---

### Post by slickymaster on 2017-05-08
*Thread moved to **Hardware**.*

---

### Post by TheFu on 2017-05-08
[U_U] means 2 of the 3 disks are being used in the array.  The 3rd disk hasn't been added. You need to fix that first.
Did you properly prepare the new disk?

---

