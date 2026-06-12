---
title: "Partition does not start on physical sector boundary. Warning"
date: 2016-03-14
forum: Hardware
---

### Post by Curbie on 2016-03-14
After a couple of days of reading about what this warning is, and experimenting on how to fix it, I'm stuck, I've experimented with Garted move and copy and paste, the Garted move and copy and paste seems to working fine, but fdisk -lu  is still showing the warning.
 

 I want to clean up those warnings, any ideas, hints, tips?
 

 Curbie
 

 ```
curbie@curbie-desktop:~$ sudo fdisk -lu 
 [sudo] password for curbie:  
  
 Disk /dev/sda: 1000.2 GB, 1000204886016 bytes 
 255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors 
 Units = sectors of 1 * 512 = 512 bytes 
 Sector size (logical/physical): 512 bytes / 4096 bytes 
 I/O size (minimum/optimal): 4096 bytes / 4096 bytes 
 Disk identifier: 0x0000f390 
  
    Device Boot      Start         End      Blocks   Id  System 
 /dev/sda1   *        2048   960514047   480256000   83  Linux 
 /dev/sda2       960524286   976771071     8123393    5  Extended 
 Partition 2 does not start on physical sector boundary. 
 /dev/sda3       976771072  1953523711   488376320   83  Linux 
 /dev/sda5       960524288   976771071     8123392   82  Linux swap / Solaris 
  
 Disk /dev/sdb: 500.1 GB, 500107862016 bytes 
 255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors 
 Units = sectors of 1 * 512 = 512 bytes 
 Sector size (logical/physical): 512 bytes / 4096 bytes 
 I/O size (minimum/optimal): 4096 bytes / 4096 bytes 
 Disk identifier: 0x0000f390 
  
    Device Boot      Start         End      Blocks   Id  System 
 /dev/sdb1            4096   960516095   480256000   83  Linux 
 /dev/sdb2       960524286   976771071     8123393    5  Extended 
 Partition 2 does not start on physical sector boundary.
```

---

### Post by QIII on 2016-03-14
Hello!

Your description of what you have done is somewhat vague.  What exactly have you done with gparted?

---

### Post by Curbie on 2016-03-14
QIII,
  

I used 500Gb drive I could kill the data, deleted all existing partitions, copied and pasted a 500Gb boot-able partition, then moved the partition by one block in hopes of finding the start of the physical sector boundary, by shrinking the partition, leaving un-partitioned space to the right, then adding one block of free space preceding (MiB) the partition, shifting the partition right. (hopefully)

 

Curbie

---

### Post by Curbie on 2016-03-17
Well, the &#8220;Partition X does not start on physical sector boundary.&#8221; warning is gone on the test drive, and I hope deleting all partitions on the drive and manually recreating the partitions (both / and swap) on sector boundaries was correct. Now I need to figure out how to switch the 512 read/writes to 4,096 read/writes and how the get it to boot.
 

 I think I picked up these issues during the transition from Win when testing the initial dual or single boot configuration, and have propagated these issues from new drive to new drive through drive imaging.
 

 If I can get this drive to boot and get it to use 4,096 read/writes, all this will have been worth it, not for the faster read/writes (a bonus), but by NOT propagating these issues further. I hope this issue is done, but will mark it as such!
 

 Curbie

---

