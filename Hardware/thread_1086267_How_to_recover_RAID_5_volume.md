---
title: "How to recover RAID 5 volume"
date: 2009-03-03
forum: Hardware
---

### Post by keipou on 2009-03-03
I am looking for some help here as I am pretty new to Linux. 
To cut the story short, I now had 4 disks with RAID 5 configuration. I had no idea the initial configuration but needed to get data out of them. I posted in a few forum but so far no reply yet and I am trying my luck here :

I tried to boot up from Ubuntu Live CD and firstly, I tried

sudo fdisk -l /dev/sdx (for disk sda, sdb, sdc and sdd) and get

Device Boot Start End Blocks Id System
/dev/sdx1 1 48 385528+ 83 Linux
/dev/sdx2 49 65 136552+ 82 Linux swap / Solaris
/dev/sdx3 66 60772 487620946 83 Linux
/dev/sdx4 60772 60801 240974 83 Linux

I then read about in forum and finally after much struggle, I tried to reform the raid volume by :

sudo mdadm --create /dev/md3 --assume-clean --level=5 --verbose --raid-device=4 /dev/sdd3 /dev/sdc3 /dev/sdb3 /dev/sda3

I have to make some assumption on the disk order and guess most probably the data should be in /dev/sdx3

I got the prompt as :

mdadm: layout defaults to left-symmetric
mdadm: chunk size defaults to 64K
mdadm: /dev/sdd3 appears to be part of a raid array:
level=raid5 devices=4 ctime=Tue Mar 3 06:48:25 2009
mdadm: /dev/sdc3 appears to be part of a raid array:
level=raid5 devices=4 ctime=Tue Mar 3 06:48:25 2009
mdadm: /dev/sdb3 appears to be part of a raid array:
level=raid5 devices=4 ctime=Tue Mar 3 06:48:25 2009
mdadm: /dev/sda3 appears to be part of a raid array:
level=raid5 devices=4 ctime=Tue Mar 3 06:48:25 2009
mdadm: size set to 487620864K
Continue creating array? y
mdadm: array /dev/md3 started.


So far so good. I then do

cat /proc/mdstat and get

md3 : active raid5 sda3[3] sdb3[2] sdc3[1] sdd3[0]
1462862592 blocks level 5, 64k chunk, algorithm 2 [4/4] [UUUU]

so I thought I should be on the way to get the data.

I do a mount

su do mount /dev/md3 /mnt

I have the error
mount: /dev/md3: can't read superblock

No matter how I tried the mount command, the error is persistent.

I then do

sudo mdadm --detail /dev/md3

Version : 00.90
Creation Time : Tue Mar 3 08:15:49 2009
Raid Level : raid5
Array Size : 1462862592 (1395.09 GiB 1497.97 GB)
Used Dev Size : 487620864 (465.03 GiB 499.32 GB)
Raid Devices : 4
Total Devices : 4
Preferred Minor : 3
Persistence : Superblock is persistent

Update Time : Tue Mar 3 08:19:05 2009
State : clean
Active Devices : 4
Working Devices : 4
Failed Devices : 0
Spare Devices : 0

Layout : left-symmetric
Chunk Size : 64K

UUID : 5430b403:a58267ca:e368bf24:bd0fce41 (local to host ubuntu)
Events : 0.2

Number Major Minor RaidDevice State
0 8 51 0 active sync /dev/sdd3
1 8 35 1 active sync /dev/sdc3
2 8 19 2 active sync /dev/sdb3
3 8 3 3 active sync /dev/sda3


That looks good though.

I do sudo mdadm --examine /dev/md3

mdadm: No md superblock detected on /dev/md3.

Any idea how I could mount the array ? So far and yet so close.

Is the problem caused by wrong disk order ? If so, how do I find out the correct order ?

Any feedback from any wise guru ? Am I screwed ??

---

### Post by mikey5555 on 2009-03-17
You may need to issue **sudo modprobe md** from a terminal screen for the Kernel to "recognize" the Raid array.  I am having many problems with Intrepid and my external 12 disk (10 active and 1 spares) array.  Every time I reboot the system - with Ubuntu 8.10 Intrepid - my array's drives change their device numbers causing me to have to re-asemble the array.  And, if I do not issue the **sudo modprobe md** command 1st, my array will not mount.  
BTW:  If you had a working array, and the device numbers change after a reboot, then use something like **sudo qtparted** or whatever partition editor you may have, and check each disk's device number **b4** you attempt to reassemble. If you use the **--create**, instead of **--assemble** you may loose all your data from the array (not real sure 'bout this, but it is possible).  Instead use the following to reassemble your array, assuming it was working OK prior to the reboot, and after determining what the current device numbers are:  **sudo mdadm --assemble --verbose /dev/md3 /dev/sdd1 /dev/sde1 /dev/sdf1** and so on, substituting *your current/correct* device numbers and mount point, including all the drives on your array.  After this you should be able to **sudo mount /dev/md3 /mnt** successfully. 
Hope this is of some use to you...

Regards....

mikey5555

---

### Post by keipou on 2009-03-17
Hi Mikey,

Thanks for the hints. I finally manage to resolve this issue. It appears that there was some corruption in XFS file system. I just do a xfs repair and after that it was mounted.

---

