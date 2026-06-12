---
title: "mdadm remove failed spare disk"
date: 2016-12-02
forum: Hardware
---

### Post by susi-loma on 2016-12-02
Hi.

I created a Raid-5 with mdadm some time ago and now one disk failed. No problem and no new sync needed, because it is the spare disk. But now i got an error message spare disk failed, which is correct. I just want to remove the spare disk until get a new one but i did not find the information which device i have to remove. Here is the output of mdadm -D
```

[FONT=Menlo]/dev/md1:[/FONT]
[FONT=Menlo]        Version : 1.2[/FONT]
[FONT=Menlo]  Creation Time : Tue Jun 24 20:16:33 2014[/FONT]
[FONT=Menlo]     Raid Level : raid5[/FONT]
[FONT=Menlo]     Array Size : 8790400512 (8383.18 GiB 9001.37 GB)[/FONT]
[FONT=Menlo]  Used Dev Size : 2930133504 (2794.39 GiB 3000.46 GB)[/FONT]
[FONT=Menlo]   Raid Devices : 4[/FONT]
[FONT=Menlo]  Total Devices : 4[/FONT]
[FONT=Menlo]    Persistence : Superblock is persistent[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]  Intent Bitmap : Internal[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]    Update Time : Fri Dec  2 21:38:37 2016[/FONT]
[FONT=Menlo]          State : active [/FONT]
[FONT=Menlo] Active Devices : 4[/FONT]
[FONT=Menlo]Working Devices : 4[/FONT]
[FONT=Menlo] Failed Devices : 0[/FONT]
[FONT=Menlo]  Spare Devices : 0[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]         Layout : left-symmetric[/FONT]
[FONT=Menlo]     Chunk Size : 512K[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]           Name : CoreI3:1  (local to host CoreI3)[/FONT]
[FONT=Menlo]           UUID : 58f04a92:ee04dc6e:095e729c:e6409a07[/FONT]
[FONT=Menlo]         Events : 107783[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]    Number   Major   Minor   RaidDevice State[/FONT]
[FONT=Menlo]       0       8       33        0      active sync   /dev/sdc1[/FONT]
[FONT=Menlo]       1       8       49        1      active sync   /dev/sdd1[/FONT]
[FONT=Menlo]       3       8       65        2      active sync   /dev/sde1[/FONT]
[FONT=Menlo]       4       8       81        3      active sync   /dev/sdf1[/FONT]

```
Here is the output of mdstat:
[FONT=Menlo]```
cat /proc/mdstat [/FONT]
[FONT=Menlo]Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] [/FONT]
[FONT=Menlo]md1 : active raid5 sdf1[4] sdd1[1] sde1[3] sdc1[0][/FONT]
[FONT=Menlo]      8790400512 blocks super 1.2 level 5, 512k chunk, algorithm 2 [4/4] [UUUU][/FONT]
[FONT=Menlo]      bitmap: 5/22 pages [20KB], 65536KB chunk[/FONT]
[FONT=Menlo]
```

How i am able to detect the drive which is used as spare to remove it?

Thanks
[/FONT]

---

### Post by kpatz on 2016-12-02
It's not showing a spare disk, or a failed disk.  Did it fail completely to where it isn't seen by the OS?

What's the output of **lsblk**?

There's no sda or sdb in the array, so assuming sda is your boot drive, maybe sdb was the spare that failed?

---

### Post by susi-loma on 2016-12-03
Hi. First of all thank you for your help. Yes, the disk is completely down. I also removed the disk from the system. The disks sda and sdb are in another raid for the OS. Here is the output of lsblk. 

```

lsblk
NAME    MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
sda       8:0    0 117,4G  0 disk  
&#9492;&#9472;sda1    8:1    0 117,4G  0 part  
  &#9492;&#9472;md0   9:0    0 117,3G  0 raid1 /
sdb       8:16   0 117,4G  0 disk  
&#9492;&#9472;sdb1    8:17   0 117,4G  0 part  
  &#9492;&#9472;md0   9:0    0 117,3G  0 raid1 /
sr0      11:0    1  1024M  0 rom   
sdc       8:32   0   2,7T  0 disk  
&#9492;&#9472;sdc1    8:33   0   2,7T  0 part  
  &#9492;&#9472;md1   9:1    0   8,2T  0 raid5 /home
sdd       8:48   0   2,7T  0 disk  
&#9492;&#9472;sdd1    8:49   0   2,7T  0 part  
  &#9492;&#9472;md1   9:1    0   8,2T  0 raid5 /home
sde       8:64   0   2,7T  0 disk  
&#9492;&#9472;sde1    8:65   0   2,7T  0 part  
  &#9492;&#9472;md1   9:1    0   8,2T  0 raid5 /home
sdf       8:80   0   2,7T  0 disk  
&#9492;&#9472;sdf1    8:81   0   2,7T  0 part  
  &#9492;&#9472;md1   9:1    0   8,2T  0 raid5 /home

```

---

### Post by susi-loma on 2016-12-04
Hi, the problem was the name of the devices. The missing drive was the "original" sdc. Now the raid is looking for device sdd-sdg and sdg is missing. After i added a new HDD to the system i do not receive any error message, without adding the new drive to the raid. So maybe it is a better solution to use the uuid of the disk for adding the hdd to the raid.

---

