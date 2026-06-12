---
title: "invalid superblock in partition table"
date: 2007-10-06
forum: Hardware &amp; Laptops
---

### Post by themoebius on 2007-10-06
I'm trying to diagnose my FAT32 hard drive with some linux tools. When i try to mount /dev/sdb1 it says it can't because it can't read the superblock. I tried running testdisk, which was able to detect the partition tables correctly and it has an option to list file, which it listed correctly so I wrote the partition tables it generated and rebuilt the MBR. But when I mount it, I still get the same errors. I tried running fsck.vfat and it says:

root@zac-desktop:/home/zac# fsck.vfat -rt /dev/sdb
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
Currently, only 1 or 2 FATs are supported, not 6.

I've no idea what that means. Testdisk still gives me the correct file list, so it must have the correct partition tables, right? Any suggestions?

---

### Post by Neiko on 2007-10-06
Looks to me as though you have multiple partitions on the drive, and the util you are using only supports 1 or 2 at the most. I would say diagnosing a hdd with a data util would probably be better from a seperate hdd running the OS you're using to fix the partitions, try a live CD with testdisk on it if you only have access to the one drive.

Or you may have better luck with a program such as Gparted.

---

### Post by themoebius on 2007-10-06
Yeah, this is an external drive I'm pluggin in via USB. There's actually only one partition, which is seen correctly by testdisk, but for some reason fsck thinks there are 6 partitions? I *think* that before I rebuild the partition tables with testdisk fsck gave me some kind of error about the first or second sector being unreadable for EOF and it wasn't until after I rebuilt the partition tables that I started getting the 6 FAT's error.

---

