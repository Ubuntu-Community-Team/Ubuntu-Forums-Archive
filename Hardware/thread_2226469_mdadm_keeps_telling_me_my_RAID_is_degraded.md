---
title: "mdadm keeps telling me my RAID is degraded"
date: 2014-05-27
forum: Hardware
---

### Post by lazloman on 2014-05-27
I was notified via email of a drive failure in my RAID 1. I checked the box using mdadm --detail /dev/md0, and indeed, a drive was listed as failed and mdadm brought the spare online and was rebuilding the RAID with it. I removed the failed drive from the array using mdadm --remove. After the rebuild was complete, I checked the raid again using --detail and I got this this:


/dev/md0:
        Version : 1.2
  Creation Time : Wed May 18 20:20:09 2011
     Raid Level : raid1
     Array Size : 972828536 (927.76 GiB 996.18 GB)
  Used Dev Size : 972828536 (927.76 GiB 996.18 GB)
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent

    Update Time : Tue May 27 11:08:43 2014
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           Name : Hedley:0  (local to host myserver)
           UUID : f26072eb:8f107128:0e26d3e3:f94308b9
         Events : 9399

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       2       8       16        1      active sync   /dev/sdb

Everything looks good right? But I keep getting emails from mdadm about the array being in a degraded state. Is there something else I need to do, besides adding a new spare, which I'm going to do anyway? Here is the email I keep getting:

This is an automatically generated mail message from mdadm
running on myserver

A DegradedArray event had been detected on md device /dev/md/1.

Faithfully yours, etc.

P.S. The /proc/mdstat file currently contains the following:

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid1 sda5[0]
      3929076 blocks super 1.2 [2/1] [U_]
      
md0 : active raid1 sda1[0] sdb[2]
      972828536 blocks super 1.2 [2/2] [UU]
      
unused devices: <none>

---

### Post by gordintoronto on 2014-05-27
Yes, you must plug in a new hard drive.

---

### Post by lazloman on 2014-05-28
Thanks for the reply, I'm glad its nothing more.

---

