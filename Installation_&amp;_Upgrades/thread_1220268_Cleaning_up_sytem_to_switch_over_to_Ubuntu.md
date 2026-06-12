---
title: "Cleaning up sytem to switch over to Ubuntu"
date: 2009-07-22
forum: Installation &amp; Upgrades
---

### Post by Ant01 on 2009-07-22
I have been running Ubuntu 7.1 for some time and am very happy with it. I have been having some problems with it lately and have decided to upgrade to 9.04

On the my machine I have a 40gig 80 gid and a removable 250gig
I have backed up all my data to the removable (NTFS) 250gig and want to clean up the other 2 drives and do a fresh installation. The problem is I have a bit of a mess with all the partions, NTFS and ext partitions. Can someone please advise the best way to reformat the drives so that I can do a clean install. 

root@antoine-ubuntu:/home/antoine# sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfdc0fdc0

Device Boot Start End Blocks Id System
/dev/sda1 * 1 3462 27808483+ 7 HPFS/NTFS
/dev/sda2 3463 4799 10739452+ 83 Linux
/dev/sda3 4800 4865 530145 5 Extended
/dev/sda5 4800 4865 530113+ 82 Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x923b923b

Device Boot Start End Blocks Id System
/dev/sdb1 2 6375 51199155 83 Linux
/dev/sdb2 6376 9690 26627737+ 83 Linux

Disk /dev/sdc: 250.0 GB, 250059349504 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x36f063ed

Device Boot Start End Blocks Id System
/dev/sdc1 1 30401 244196001 7 HPFS/NTFS

:D soon to be Ubuntu Convert, hate windows....

---

### Post by masux594 on 2009-07-22
if u want to clean all, when u install the OS, you just delete ALL the partition EXCEPT for the 250Gb partition and then, create the new partitions for ubuntu or other.. When u boot with cd and you select to install the os, choose manually hdd partition.. Need a guide for partition hdd for ubuntu?

Sysc, A

---

