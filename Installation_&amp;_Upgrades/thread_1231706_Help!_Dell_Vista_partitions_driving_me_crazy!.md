---
title: "Help! Dell Vista partitions driving me crazy!"
date: 2009-08-04
forum: Installation &amp; Upgrades
---

### Post by jchstevens on 2009-08-04
Hi.
I have a Dell Inspiron 6400 which came with Vista pre-installed.
I used to have it dual booting with Ubuntu 7.04, but I've been trying to install 9.04 for a few days now.
Originally, gparted complained about overlapping partitions so I tried to fix this with TestDisk. Following this, the laptop refused to reboot.
I managed to fix this using a System Rescue CD to boot Vista and create a Vista repair CD from which I could fix the MBR.
I now have a laptop that boots Vista once more. However, gparted now complains with the error:
*Can't have a partition outside the disk!*
Although the partition table seems to be fine when viewed using testdisk /list, when I run [FONT="Fixedsys"]sudo fdisk -l[/FONT] from the Ubuntu live CD I get:
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x18000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          10       80293+   6  FAT16
/dev/sda2   *          11        1316    10485760    7  HPFS/NTFS
/dev/sda3            1316       10893    76926964+   7  HPFS/NTFS
/dev/sda4           10894       19458    68798362+   f  W95 Ext'd (LBA)
/dev/sda5           17981       19196     9767488+   c  W95 FAT32 (LBA)
/dev/sda6           19197       19458     2096128    c  W95 FAT32 (LBA)

```
I believe the partitions are as follows:
[LIST=1]
[*] Dell Diagnostics 
[*] Recovery Partition
[*] Vista OS
[*] Extended Partition
[*] FAT32 partition for data sharing
[*] Dell MediaDirect partition
[/LIST]
Does this output suggest that the end of /dev/sda6 is beyond the end of the disk? (**19458** c.f. **[B]19457**[/B] cyclinders)
Testdisk reports the disk size as **19457 255 63**, and the end of the extended partition as **19457 254 63**, which I thought looked OK.

If this partition is too big, is there a resizing tool I can use so that I don't lose my MediaDirect partition?
Any advice gratefully received as this is getting very frustrating!!! :confused:

---

