---
title: "RAID Issue = dl showing incorrect values after mdadm --grow"
date: 2012-08-09
forum: Hardware
---

### Post by schworak on 2012-08-09
Hello, I need someone with some RAID experience to help me figure this one out. For a couple days I have been searching and no good answers are coming so perhaps I can get some help here.

Take a look at the output from the command line:

```
-> mdsdm --detail /dev/md0:

        Version : 0.90
  Creation Time : Fri Jun  4 23:22:05 2010
     Raid Level : raid1
     Array Size : 244138944 (232.83 GiB 250.00 GB)
  Used Dev Size : 244138944 (232.83 GiB 250.00 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Thu Aug  9 08:55:11 2012
          State : active
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : d29fccc1:4990675b:589ea98e:bab4a4a7
         Events : 0.1163614

    Number   Major   Minor   RaidDevice State
       0       8       81        0      active sync   /dev/sdf1
       1       8       97        1      active sync   /dev/sdg1

``````
-> mdsdm --detail /dev/md1:

        Version : 0.90
  Creation Time : Fri Jun  4 23:22:19 2010
     Raid Level : raid6
     Array Size : 2930282304 (2794.54 GiB 3000.61 GB)
  Used Dev Size : 976760768 (931.51 GiB 1000.20 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Thu Aug  9 08:55:28 2012
          State : active
 Active Devices : 5
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 495e40aa:e6089480:30fd1677:e0dbfce9
         Events : 0.343636

    Number   Major   Minor   RaidDevice State
       0       8       49        0      active sync   /dev/sdd1
       1       8        1        1      active sync   /dev/sda1
       2       8       17        2      active sync   /dev/sdb1
       3       8       65        3      active sync   /dev/sde1
       4       8       33        4      active sync   /dev/sdc1

``````
-> cat /proc/mdstat

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sdf1[0] sdg1[1]
      244138944 blocks [2/2] [UU]
      
md1 : active raid6 sde1[3] sdc1[4] sdb1[2] sda1[1] sdd1[0]
      2930282304 blocks level 6, 64k chunk, algorithm 2 [5/5] [UUUUU]
      
unused devices: <none>

```Everything is looking good so far. The numbers are exactly what I would expect. But here comes the problem...

```
-> df -l

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/md0              48060232  29107612  16511256  64% /
none                   4055604       352   4055252   1% /dev
none                   4096748         0   4096748   0% /dev/shm
none                   4096748       400   4096348   1% /var/run
none                   4096748         0   4096748   0% /var/lock
/dev/sdg2             48128344    184344  45499200   1% /tmp
/dev/md1             1769073308 271594200 1407615332  17% /export
```Those are the exact same values that were in place before I added 2 drives to my MD1 array (2x1T each) and switched it from RAID-5 to RAID-6. I also replaced the small partitions on MD0 with 250G drives but it still reports 64% used of only 50G... 

This is only when I do df -l and I am concerned for a couple reasons. First, will I run out of drive space when df thinks things are full? Does the system really only see part of the storage? Or does the system see it all and only df is confused? But the other reason I am concerned is that a miss-match like this could be a symptom of something larger being wrong that I simply haven't found yet.

Things I have tried:

[LIST]
[*]Rebooting (of course)
[*]sync
[*]Updating /etc/mdadm/mdadm.conf with the output of mdadm --detail --scan
[/LIST]


Please please please, someone give me something else to try.

Thanks!

---

### Post by schworak on 2012-08-09
Some added info. I just looked at the partition file and it is showing the correct block info too. So only "df" is causing me issues so far. Everything else is showing the expected numbers.

```

-> cat /proc/partitions

major minor  #blocks  name

   8        0  976762584 sda
   8        1  976760832 sda1
   8       16  976762584 sdb
   8       17  976760832 sdb1
   8       32  976762584 sdc
   8       33  976760832 sdc1
   8       48  976762584 sdd
   8       49  976760832 sdd1
   8       64  976762584 sde
   8       65  976760832 sde1
   8       80  293036184 sdf
   8       81  244139008 sdf1
   8       82   48896000 sdf2
   8       96  293036184 sdg
   8       97  244139008 sdg1
   8       98   48896000 sdg2
   9        1 [COLOR=Red]2930282304 [/COLOR]md1
   9        0  [COLOR=Red]244138944 [/COLOR]md0

```

---

### Post by schworak on 2012-08-10
This is really chapping my hide. I have come to the conclusion that "df" displaying the wrong information is annoying but likely harmless because everything else I have tried displays the correct drive size.

```

-> fdisk -l

Disk /dev/md1:[COLOR=Red] 3000.6 GB[/COLOR], 3000609079296 bytes
2 heads, 4 sectors/track, 732570576 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 65536 bytes / 196608 bytes
Disk identifier: 0x00000000

Disk /dev/md0: [COLOR=Red]250.0 GB[/COLOR], 249998278656 bytes
2 heads, 4 sectors/track, 61034736 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


```


So far I have found fixes for when things are really damaged but nothing is wrong with my drives. I have tried fsck and it says things are ok.

ARG!

---

### Post by schworak on 2012-08-20
> **schworak said:**
> This is really chapping my hide. I have come to the conclusion that "df" displaying the wrong information is annoying but likely harmless because everything else I have tried displays the correct drive size.

OH NO!

This is NOT HARMLESS!

What ever "df" says is what the OS really thinks is available on the drive. I just ran out of room when I hit the 50G mark even though every program says I have 250 gig EXCEPT for "df" which says I only have 50 gig.

What the heck????

The only solution I could find was to reformat the drive to make it show up as the full 250 gig in all places. What a pain because this was my main OS drive which means a full clean install and set everything back up.

If anyone knows of a true fix for this please let me know. I would love to be able to deal with it if this ever comes up again in the future.

---

### Post by rscottdrysdale on 2012-09-26
i'm in a similar situation.  built raid5 initially from three 500G drives and added a fourth.  this is what i see:

```
scott@hog10:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sde1       182G  3.6G  169G   3% /
udev            999M  4.0K  999M   1% /dev
tmpfs           403M  1.3M  402M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none           1007M  404K 1006M   1% /run/shm
/dev/md0        917G  755G  116G  87% /media/raid
scott@hog10:~$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 0.90
  Creation Time : Sat Jan  2 17:55:46 2010
     Raid Level : raid5
     Array Size : 1465151808 (1397.28 GiB 1500.32 GB)
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Wed Sep 26 03:48:34 2012
          State : clean 
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 282540c5:79eaaa33:8b877447:fcc0b11e
         Events : 0.253320

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       2       8       33        2      active sync   /dev/sdc1
       3       8       49        3      active sync   /dev/sdd1
scott@hog10:~$ 
```

i share /media/raid via samba to various windows machines, and they also see the smaller size (XP says 916GB total, 801GB used, 104GB free)

this is not good...

---

### Post by SaturnusDJ on 2012-09-26
You both didn't talk about growing the filesystem after growing the array. Did you forget?

---

### Post by schworak on 2012-09-26
I resized my RAID6 array by adding three new drives but DF kept showing the old size.

After some research I found that I simply needed to tell the OS to  resize the partition to its maximum size. It took a while but it did it  LIVE without unmounting the array and no data loss. As a matter of fact I  was even able to write to the disk while it was being resized. I  wouldn't try rebooting because that sounds down right dangerous.

It took about 3 hours (+/-) to expand my array from 3T to 6T using this command:

```
sudo resize2fs /dev/md9
```By not specifying the size you are resizing to, the entire available space is used which is exactly what I wanted. [Linux Rocks!](http://eandata.com/linux/)

---

### Post by rscottdrysdale on 2012-09-26
i fixed it!

my raid has no linux system stuff on it, so i could do this directly on the running system.  you'll probably have to boot a "live" cd to modify a raid partition that has system stuff on it.


here's what i did:

df -T
 -- this will show your device name and what type of filesystem.  mine is ext3 on /dev/md0, and ext3 is a mutant of ext2, so the ext2 tools know how to deal with it.

umount /dev/md0
 -- unmount the raid.  should go smoothly as long as nothing has files open on the raid.  in my case, i had to disconnect some windows machines.

e2fsck -f /dev/md0
 -- check the filesystem before mangling it.  you might need a command specific to your filesystem as e2fsck knows ext2/ext3.

resize2fs /dev/md0
 -- make the filesystem use the entire partition.  again, you might need a command specific to your filesystem.

mount /dev/md0
 -- put it back in service.

```
scott@hog10:~$ sudo resize2fs /dev/md0
resize2fs 1.42 (29-Nov-2011)
Please run 'e2fsck -f /dev/md0' first.

scott@hog10:~$ sudo e2fsck -f /dev/md0
e2fsck 1.42 (29-Nov-2011)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/md0: 909341/61054976 files (3.6% non-contiguous), 201815088/244191968 blocks
scott@hog10:~$ sudo resize2fs /dev/md0
[sudo] password for scott: 
resize2fs 1.42 (29-Nov-2011)
Resizing the filesystem on /dev/md0 to 366287952 (4k) blocks.
The filesystem on /dev/md0 is now 366287952 blocks long.

scott@hog10:~$ sudo mount /dev/md0
scott@hog10:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sde1       182G  3.5G  169G   3% /
udev            999M  4.0K  999M   1% /dev
tmpfs           403M  1.3M  402M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none           1007M  400K 1006M   1% /run/shm
/dev/md0        1.4T  756G  551G  58% /media/raid
scott@hog10:~$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 0.90
  Creation Time : Sat Jan  2 17:55:46 2010
     Raid Level : raid5
     Array Size : 1465151808 (1397.28 GiB 1500.32 GB)
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Wed Sep 26 10:11:56 2012
          State : clean 
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 282540c5:79eaaa33:8b877447:fcc0b11e
         Events : 0.253320

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       2       8       33        2      active sync   /dev/sdc1
       3       8       49        3      active sync   /dev/sdd1
scott@hog10:~$ 
```

---

