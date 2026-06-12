---
title: "no partitions detected..."
date: 2009-04-30
forum: Installation &amp; Upgrades
---

### Post by walker9010 on 2009-04-30
Hello. The Ubuntu installer (and gparted, and parted) are not detecting my partitions. 

Here is the output from parted:

Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print                                                         
Error: Can't have a partition outside the disk!                        
(parted) quit                                                          


and here is the output from fdisk:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+   6  FAT16
/dev/sda2   *           7        3194    25599992+   7  HPFS/NTFS
/dev/sda3            3194       11614    67637248    7  HPFS/NTFS
/dev/sda4           11614       19458    63009954    f  W95 Ext'd (LBA)
/dev/sda5           11614       12587     7815588   83  Linux
/dev/sda6           12587       12891     2441840   82  Linux swap / So
/dev/sda7           12891       15930    24410736   83  Linux
/dev/sda8           15931       19457    28330596    7  HPFS/NTFS

---

### Post by walker9010 on 2009-04-30
I've fixed it.

Just incase anyone else has a similar problem:

the extended partition was larger then the size of the disk (note the number of cylinders) so I used fdisk to resize the partition to be within the disk. Now Ubuntu is detecting the partitions. :)

---

