---
title: "RAID1 Array - Rebuild : How to"
date: 2009-03-08
forum: Hardware
---

### Post by wamrobert on 2009-03-08
Hope this helps anyone who experiences a sync issue with RAID1 device


The  RAID partitions on that box are as follows
Each hard disk is divided in to 3. First hard disk is hda and second is hdb

Each hard disk is partitioned into 3 

hda1  - /Boot   (500MB)        hdb1 

hda2  - Linux Swap (2GB)       hdb2

hda3  -   /                    hdb3

 

RAID array created as 

 

md0   - consists of hda1 and hdb1  

md1   - consists of hda2 and hdb2

md2   - consists of hda3 and hdb3

 

 

Using mdadm commands .. to check the health of the RAID array .. I notice that

 

[root@gw ~]# mdadm --detail /dev/md2

/dev/md2:

        Version : 00.90.01

  Creation Time : Tue Dec 16 19:40:43 2008

     Raid Level : raid1

     Array Size : 75505408 (72.01 GiB 77.32 GB)

    Device Size : 75505408 (72.01 GiB 77.32 GB)

   Raid Devices : 2

  Total Devices : 1

Preferred Minor : 2

    Persistence : Superblock is persistent

 

    Update Time : Sun Mar  8 13:41:05 2009

          State : clean, degraded

 Active Devices : 1

Working Devices : 1

 Failed Devices : 0

  Spare Devices : 0

 

           UUID : 114f29b8:c7a9d92e:7f61184f:5e6adce9

         Events : 0.3385732

 

    Number   Major   Minor   RaidDevice State

       0       0        0        -      removed

       1       3       67        1      active sync   /dev/hdb3

 

** This shows that hda3 is not synced to hdb3, It has a removed state .I suspect the mirroring failed maybe due to a shutdown .. or that some sectors have a problem hopefully not so I am going to rebuild the array

 

A correctly mirrored array like /dev/md0 would appear as follows

 

[root@gw ~]# mdadm --detail /dev/md0

/dev/md0:

        Version : 00.90.01

  Creation Time : Tue Dec 16 19:42:27 2008

     Raid Level : raid1

     Array Size : 513984 (502.02 MiB 526.32 MB)

    Device Size : 513984 (502.02 MiB 526.32 MB)

   Raid Devices : 2

  Total Devices : 2

Preferred Minor : 0

    Persistence : Superblock is persistent

 

    Update Time : Sun Mar  8 13:50:41 2009

          State : clean

 Active Devices : 2

Working Devices : 2

 Failed Devices : 0

  Spare Devices : 0

 

           UUID : ddb42512:d2783cd3:44f2d4fb:3cd72940

         Events : 0.3126

 

    Number   Major   Minor   RaidDevice State

       0       3        1        0      active sync   /dev/hda1

       1       3       65        1      active sync   /dev/hdb1

 

 

Notice that hda1 and hdb1 are in sync

 

 

Solution :  I add the device hda3 back to the array md2

 

[root@gw ~]#  mdadm /dev/md2 -a /dev/hda3

mdadm: hot added /dev/hda3

 

To view the statistics .. I observe /proc/mdstat

 

[root@gw ~]# cat /proc/mdstat

Personalities : [raid1]

md1 : active raid1 hdb2[1] hda2[0]

      2128512 blocks [2/2] [UU]

 

md2 : active raid1 hdb3[1] hda3[2]

      75505408 blocks [2/1] [_U]

      [=>...................]  recovery =  7.6% (5743360/75505408) finish=52.5min speed=22132K/sec

md0 : active raid1 hdb1[1] hda1[0]

      513984 blocks [2/2] [UU]

 

unused devices: <none>

 

 

Notice that md1 and md0 have  a double UU .. showing they are in sync. md2 has  _U and is in a rebuild state.

 

 

I can also use the examine command to check hda3  while its  syncing. The examine detail is used on a specific device like hdaX  not on an mdX device.

 

[root@gw ~]# mdadm --examine  /dev/hda3

/dev/hda3:

          Magic : a92b4efc

        Version : 00.90.00

           UUID : 114f29b8:c7a9d92e:7f61184f:5e6adce9

  Creation Time : Tue Dec 16 19:40:43 2008

     Raid Level : raid1

   Raid Devices : 2

  Total Devices : 2

Preferred Minor : 2

 

    Update Time : Sun Mar  8 13:58:34 2009

          State : clean

 Active Devices : 1

Working Devices : 2

 Failed Devices : 0

  Spare Devices : 1

       Checksum : f7d33faf - correct

         Events : 0.3386607

 

 

      Number   Major   Minor   RaidDevice State

this     2       3        3        2      spare   /dev/hda3

 

   0     0       0        0        0      removed

   1     1       3       67        1      active sync   /dev/hdb3

   2     2       3        3        2      spare   /dev/hda3

 

 

 

A good synced disk like hda1 as examined by mdadm –examine /dev/hdXX is as below. 
 

[root@gw ~]# mdadm --examine  /dev/hda1

/dev/hda1:

          Magic : a92b4efc

        Version : 00.90.00

           UUID : ddb42512:d2783cd3:44f2d4fb:3cd72940

  Creation Time : Tue Dec 16 19:42:27 2008

     Raid Level : raid1

   Raid Devices : 2

  Total Devices : 2

Preferred Minor : 0

 

    Update Time : Sun Mar  8 13:50:41 2009

          State : clean

 Active Devices : 2

Working Devices : 2

 Failed Devices : 0

  Spare Devices : 0

       Checksum : 6e251d83 - correct

         Events : 0.3126

 

 

      Number   Major   Minor   RaidDevice State

this     0       3        1        0      active sync   /dev/hda1

 

   0     0       3        1        0      active sync   /dev/hda1

   1     1       3       65        1      active sync   /dev/hdb1

 

 

 

The sync progress so far …22 % 

 

[root@gw ~]# cat /proc/mdstat

Personalities : [raid1]

md1 : active raid1 hdb2[1] hda2[0]

      2128512 blocks [2/2] [UU]

 

md2 : active raid1 hdb3[1] hda3[2]

      75505408 blocks [2/1] [_U]

      [====>................]  recovery = 22.1% (16755328/75505408) finish=43.9min speed=22267K/sec

md0 : active raid1 hdb1[1] hda1[0]

      513984 blocks [2/2] [UU]

 

unused devices: <none>

 

 


 

NB: The box has suddenly become unreachable … Power failure or internet downtime ?? 

    The sync probably didn’t finish.

 

 I was correct.. Power problem.]
Server rebooted and automatically started rebuilding the array


[root@gw ~]# uptime

 14:10:31 up 2 min,  1 user,  load average: 1.85, 0.93, 0.36

[root@gw ~]#

 

 

The Rebuild process is started automatically after a system boot, progress is 5.1%

 

[root@gw ~]# cat /proc/mdstat

Personalities : [raid1]

md1 : active raid1 hdb2[1] hda2[0]

      2128512 blocks [2/2] [UU]

 

md2 : active raid1 hdb3[1] hda3[2]

      75505408 blocks [2/1] [_U]

      [=>...................]  recovery =  5.1% (3876864/75505408) finish=51.3min speed=23238K/sec

md0 : active raid1 hdb1[1] hda1[0]

      513984 blocks [2/2] [UU]

 

unused devices: <none>

---

