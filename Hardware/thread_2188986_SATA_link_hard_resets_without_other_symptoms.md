---
title: "SATA link hard resets without other symptoms"
date: 2013-11-20
forum: Hardware
---

### Post by DorianX on 2013-11-20
Bit of a poser here. I'm running a Lucid server with a large mdadm raid array. Roughly every 8 days, I find a message like this in the log:
```

Nov 19 20:20:16 badwolf kernel: [2817754.853137] ata8: hard resetting link
Nov 19 20:20:16 badwolf kernel: [2817755.576027] ata8: SATA link down (SStatus 0 SControl 310)
Nov 19 20:20:17 badwolf kernel: [2817755.707314] ata8: hard resetting link
Nov 19 20:20:19 badwolf kernel: [2817758.544037] ata8: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Nov 19 20:20:19 badwolf kernel: [2817758.560858] ata8.00: configured for UDMA/100
Nov 19 20:20:19 badwolf kernel: [2817758.560867] ata8: EH complete

```

Close as I can tell, ata8 corresponds to /dev/sdd

Usually it only happens once, but it's happened three times yesterday, which is why I'm up in arms about it. I've never experienced data loss as a result, and /proc/mdstat doesn't report any problem with the raid. Here's the output of mdadm --detail:

```

/dev/md0:
        Version : 00.90
  Creation Time : Thu Aug 19 20:15:36 2010
     Raid Level : raid5
     Array Size : 5860535808 (5589.04 GiB 6001.19 GB)
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Tue Nov 19 22:58:26 2013
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 128K

           UUID : 993206c6:cbfdafb7:44987e4c:05e1c24a (local to host badwolf)
         Events : 0.92594

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       2       8       33        2      active sync   /dev/sdc1
       3       8       49        3      active sync   /dev/sdd1

```

smartctl reports no problems on any of the disks.

The error messages always happen while the array should be fairly idle -- in fact, only one of the times it's happened have I even been home at the time.

Anyone have any ideas as to what the deal is and how worried I should be about my data integrity? This is a very large array as you can see, and backing up all the data on it is a little tricky because of the size of it.

Thanks.


Update: It's happened a fourth time in the past 24 hours. I'm trying to backup what files I can to other devices, though the RAID still isn;'t degraded or anything.

---

### Post by DorianX on 2013-11-21
Bit more information. It happened a fifth time in the early afternoon yesterday and hasn't since. dmesg tells me that the specific ATA error is "PHYRdyChg". NCQ is not enabled. I ran a SMART self-test and it came back clean, and all the vendor-specified values were okay. My best guess at the moment is that it's a loose/bad SATA cable, or maybe that the power supply isn't quite providing enough wattage when the drives spin up. Since it mostly happens when there isn't a lot of IO going on, I'm kinda wondering if it's something that only happens when the disk wakes up after a period of inactivity. But it did happen one time while I had a large rsync going on, so I don't know.  It's making me really edgy.

---

