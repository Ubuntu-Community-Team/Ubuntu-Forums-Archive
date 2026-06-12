---
title: "Safe to remove failed hard drive from Raid5?"
date: 2016-01-12
forum: Hardware
---

### Post by sjabraha on 2016-01-12
[FONT=arial]Hello, I am running Ubuntu 14.04 LTS (and am relatively new to Ubuntu).  I'm also running a 4 disk Raid5 array using software raid.  It appears that one of the disks has failed, or at a minimum, has fallen out of the array.  I've purchased a new hard disk to replace the failed one.  In preparation for the drive swap, I've execute the "Fail" and "Remove" MDADM commands that are required prior to removing the faulty drive.  However, I keep getting a response for both saying "no such device".  Detailed output is below.[/FONT]

[FONT=arial]**Does this mean it's physically safe to remove the disk or am I overlooking something?  Thanks!**[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]See below:[/FONT]
[FONT=arial]
[/FONT]
[PHP]s@half:~$ sudo mdadm --manage /dev/md0 --fail /dev/sdc1
[sudo] password for s: 
mdadm: set device faulty failed for /dev/sdc1:  No such device
s@half:~$ sudo mdadm --manage /dev/md0 --remove /dev/sdc1
mdadm: hot remove failed for /dev/sdc1: No such device or address


s@half:~$ sudo mdadm --detail /dev/md0
mdadm:
/dev/md0:
        Version : 1.2
  Creation Time : Sat Sep 20 09:49:46 2014
     Raid Level : raid5
     Array Size : 8790400512 (8383.18 GiB 9001.37 GB)
  Used Dev Size : 2930133504 (2794.39 GiB 3000.46 GB)
   Raid Devices : 4
  Total Devices : 3
    Persistence : Superblock is persistent

    Update Time : Sun Jan 10 22:26:56 2016
          State : clean, degraded 
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : half:0
           UUID : 280b8978:da1db13d:c9e3cfea:c8649514
         Events : 15254

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       2       0        0        2      removed
       4       8       49        3      active sync   /dev/sdd1
s@half:~$[/PHP]

---

