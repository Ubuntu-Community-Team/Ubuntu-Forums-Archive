---
title: "i have a corrupted partition"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by iapelaezf69 on 2009-10-30
Hi everyone,

apparently I have a partition inside a partition, then my partition editor doesnt recognise either my ubuntu partition nor my fat32 and my ntfs partitions. Could use some help!

ivan@ivp:~$ sudo fdisk -lu
[sudo] password for ivan: 
omitting empty partition (5)

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00790078

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   108406619    54203278+   5  Extended
/dev/sda2         9767583    10747484      489951   82  Linux swap / Solaris
/dev/sda3   *   108406620   117194174     4393777+   7  HPFS/NTFS
/dev/sda5             189     9767519     4883665+  83  Linux
/dev/sda6        10747548   108406619    48829536    b  W95 FAT32

---

### Post by mechro on 2009-10-30
Frankly that defies logic!... er... well mine at least :-? You've got an Extended Partition which contains Logical Partitions but the scheme is all over the place and difficult to follow.

Can you post a screenshot of your Partition Editor's graphical output?

---

### Post by iapelaezf69 on 2009-10-30
it's all good, i'm going to format everything and install ubuntu 9.10

thnx though!

---

