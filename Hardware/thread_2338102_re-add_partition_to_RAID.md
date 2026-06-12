---
title: "re-add partition to RAID"
date: 2016-09-24
forum: Hardware
---

### Post by spedickhill on 2016-09-24
Hi (:

I'm new here and I therefore hope that i post this the right place!
(If not, I'm sorry and please let me know!)

I just noticed that my /dev/md3 have had a DegradedArray event since 28/08-2016.
So I thought that it might be a good idea to fix this now... (o:

But what is the safest, easiest and correct way to re-add a partition?
I have read something about an "--re-add" function in mdadm, but can't seem to find any detailed description about it?
The disk doesn't have any failures and why it have been remove, I can't tell. (SMART info seems okay)

It is a Ubuntu server 14.04.4 LTS, which runs as a VM on a ESXi host.
The hard drive is a .VMDK-file and the host reads the disk without any problems.

I also have Webmin installed, where I have the opportunity to add the partition again.
But I don't think that Webmin would be a good idea to use for this.


Thanks in advance!
Sincerely, Simon.


***mdadm --detail /dev/md3***
```
/dev/md3:        Version : 1.2
  Creation Time : Sun Oct 25 18:39:32 2015
     Raid Level : raid1
     Array Size : 2898970432 (2764.67 GiB 2968.55 GB)
  Used Dev Size : 2898970432 (2764.67 GiB 2968.55 GB)
   Raid Devices : 2
  Total Devices : 1
    Persistence : Superblock is persistent


    Update Time : Sat Sep 24 20:20:06 2016
          State : clean, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0


           Name : HIDDEN:3  (local to host HIDDEN)
           UUID : c80a078c:1c0f0315:2f4376f7:cc5c8a99
         Events : 56795


    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       0        0        1      removed
```
[B][I]
mdadm --detail /dev/md4
[/I][/B]```
/dev/md4:
        Version : 1.2
  Creation Time : Sun Oct 25 17:47:05 2015
     Raid Level : raid1
     Array Size : 3865337664 (3686.27 GiB 3958.11 GB)
  Used Dev Size : 3865337664 (3686.27 GiB 3958.11 GB)
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent


    Update Time : Sat Sep 24 20:35:07 2016
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0


           Name : HIDDEN:4  (local to host HIDDEN)
           UUID : 58e1e48b:6a553c53:c16b556a:0b312d69
         Events : 47939


    Number   Major   Minor   RaidDevice State
       2       8       65        0      active sync   /dev/sde1

       1       8       49        1      active sync   /dev/sdd1
```[B][I]

cat /proc/mdstat[/I][/B]
```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md4 : active raid1 sdd1[1] sde1[2]
      3865337664 blocks super 1.2 [2/2] [UU]


md3 : active raid1 sdb1[0]
      2898970432 blocks super 1.2 [2/1] [U_]


unused devices: <none>
```

***/dev/sdc1 S.M.A.R.T INFO***
```
Parameter                     Value  Threshold  Worst
----------------------------  -----  ---------  -----
Health Status                 OK     N/A        N/A
Media Wearout Indicator       N/A    N/A        N/A
Write Error Count             N/A    N/A        N/A
Read Error Count              200    51         200
Power-on Hours                70     0          70
Power Cycle Count             100    0          100
Reallocated Sector Count      200    140        200
Raw Read Error Rate           200    51         200
Drive Temperature             116    0          106
Driver Rated Max Temperature  N/A    N/A        N/A
Write Sectors TOT Count       200    0          200
Read Sectors TOT Count        100    0          253
Initial Bad Block Count       N/A    N/A        N/A
```

---

### Post by spedickhill on 2016-09-25
Never mind... (:
I took the change by just adding /dev/sdc1 to /dev/md3 with "mdadm --manage /dev/md3 --add /dev/sdc1" and its now recovering.

---

