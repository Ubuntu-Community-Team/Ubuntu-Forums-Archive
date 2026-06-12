---
title: "SATA WD800JD install problem with Hardy Heron"
date: 2008-12-07
forum: Installation &amp; Upgrades
---

### Post by selangk on 2008-12-07
Hi everyone
I just bought Acer Aspire M1201 
- AMD Athlon™ 64 X2 4400+ Dual Core Processor (2.3GHz, 1MB L2 cache)
- AMD 740G Chipset
- 80 Gig Western Digital WD800JD Hard Drive

I have
- ubuntu Hardy Heron Live CD, and Alternate CD
- Windoze XP installed
- NTFS Partition
- ext3 and swap partition (i made it using Acronis) with enough capacity 

I want to:
- Install Ubuntu Hardy Heron on ext3 partition
- Dual Boot with Windoze XP

My Problem:
- Everytime i start installing ubuntu, the installer can not detect the ext3 and  swap partition.
- Actually the installer detect the Hard Drive and want to use the WHOLE 80 gig partition and want to create a new partition on it (and destroy data on it of course)
- I already select "manual" choice from the list, but still the same, can not use the ext3 partition.

After browsing, I found this thread [link]("http://ubuntuforums.org/showthread.php?t=887797"), looks similar, but still can not resolve my problem. 
(The link above labelled SOLVED, so i post my new topic here, excuse me if posting this new topic is wrong)


can anyone please help me?

Any advice appreciated.


Thanks

---

### Post by taurus on 2008-12-07
From the LiveCD, open a terminal and post the output of this command here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```
Perhaps it's better to use gparted (System -> Administration -> Partition Editor) to format those two partitions to ext3 filesystem and swap.

---

### Post by selangk on 2008-12-07
This my fdisk -l 
```


Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1306    10490413+   7  HPFS/NTFS
/dev/sda2            1307        9729    67657747+   f  W95 Ext'd (LBA)
/dev/sda5            1307        2612    10490413+   7  HPFS/NTFS
/dev/sda6            2613        7834    41945683+   b  W95 FAT32
/dev/sda7            7835        9338    12080848+  83  Linux
/dev/sda8            9339        9729     3140676   82  Linux swap / Solaris


```

---

