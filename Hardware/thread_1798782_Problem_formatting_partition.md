---
title: "Problem formatting partition"
date: 2011-07-06
forum: Hardware
---

### Post by wrybread on 2011-07-06
I'm trying to format a partition that used to contain a Windows partition, and getting the following error when I try to create the partition on the empty space:

```
Error creating partition: helper exited with exit code 1: In part_add_partition: device_file=/dev/sda, start=20003684352, size=15201206272, type=0x83
Entering MS-DOS parser (offset=0, size=40007761920)
MSDOS_MAGIC found
looking at part 0 (offset 32256, size 13777311744, type 0x83)
new part entry
looking at part 1 (offset 13779336192, size 26228032512, type 0x05)
Entering MS-DOS extended parser (offset=13779336192, size=26228032512)
readfrom = 13779336192
MSDOS_MAGIC found
readfrom = 19679674368
MSDOS_MAGIC found
readfrom = 35204198400
MSDOS_MAGIC found
readfrom = 38933626880
MSDOS_MAGIC found
readfrom = 20003880960
No MSDOS_MAGIC found
Exiting MS-DOS extended parser
looking at part 2 (offset 0, size 0, type 0x00)
new part entry
looking at part 3 (offset 0, size 0, type 0x00)
new part entry
Exiting MS-DOS parser
MSDOS partition table detected
containing partition table scheme = 1
got it
Error: Invalid partition table on /dev/sda -- wrong signature 0.
ped_disk_new() failed

```

I'm getting that error in Disk Utility (on my Ubuntu Studio install, System --> Administration --> Disk Utility).

Any tips on how to fix the error so I can use that partition?

---

### Post by nzjethro on 2011-07-06
Please post the output of

```
sudo fdisk -l
```
(that's a lower case L).

---

### Post by wrybread on 2011-07-06
```
omitting empty partition (9)

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4b36bdea

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1675    13454406   83  Linux
/dev/sda2            1676        4864    25613313    5  Extended
/dev/sda5            1676        2393     5762048   83  Linux
/dev/sda6            2393        2432      315392   82  Linux swap / Solaris
/dev/sda7            4281        4734     3641344   83  Linux
/dev/sda8            4734        4864     1047552   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       33426   268494313+   c  W95 FAT32 (LBA)
/dev/sdb2           33427      121601   708265687+   f  W95 Ext'd (LBA)
/dev/sdb5           33427      121601   708265656   83  Linux

```

---

### Post by nzjethro on 2011-07-06
What happens when you open up GParted? Does it appear that there are no partitions on /dev/sda? You may have a similar problem to the one on [this thread.]("http://ubuntuforums.org/showthread.php?t=1591704") It links to [this website]("http://www.rodsbooks.com/missing-parts/") which may be able to resolve your issues.

---

