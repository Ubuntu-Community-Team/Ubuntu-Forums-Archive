---
title: "how can I reinstall/repair a RAID1 setup"
date: 2006-09-30
forum: Hardware &amp; Laptops
---

### Post by michaelmj on 2006-09-30
I'm a noobie here and have searched for hours to solve the following problem. I used to have two hard drives (sda and sdb) setup as a single partition RAID1 array under Ubuntu Breezy Badger. When I tried to upgrade to Dapper Drake things went wrong. It turned out to be a bad memory bank on my computer. I lost my Beezy Badger installation so decided to go straight for Drapper Drake, which with the new memory installed worked perfectly. I'm now stuck with not knowing how to setup and access my sata drives as MD0 withoutlosing any data on them. First of all can they be backed up in there current state and if so should bothh drives be backed up independatly.

Here are a couple of my present read outs, do you require anymore.   

michael@ubuntu:~$ cat /proc/mdstat
Personalities : [raid1]
md0 : active raid1 sda1[0] sdb1[1]
      244195904 blocks [2/2] [UU]

-----------------------------------------------

michael@ubuntu:~$ sudo fdisk -l
Password:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001   83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001   83  Linux

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1912    15358108+  83  Linux
/dev/hda2            1913       14593   101860132+   f  W95 Ext'd (LBA)
/dev/hda5           11475       14215    22017051   83  Linux
/dev/hda6           14216       14593     3036253+  82  Linux swap / Solaris
/dev/hda7            1913        3824    15358077   83  Linux
/dev/hda8            3825        7489    29439081   83  Linux
/dev/hda9           11161       11474     2522173+  82  Linux swap / Solaris
/dev/hda10  *        7490       11007    28258303+  83  Linux
/dev/hda11          11008       11160     1228941   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/md0: 250.0 GB, 250056605696 bytes
2 heads, 4 sectors/track, 61048976 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md0 doesn't contain a valid partition table
michael@ubuntu:~$

---

