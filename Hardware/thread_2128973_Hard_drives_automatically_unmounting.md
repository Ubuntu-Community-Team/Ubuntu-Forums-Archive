---
title: "Hard drives automatically unmounting"
date: 2013-03-24
forum: Hardware
---

### Post by miragemonger on 2013-03-24
Hello everyone, 

I know this may sound weird, but I am having this issue and it's driving me crazy. 

I have the following hard drives mounted: 

```

/dev/sda1 on /home/user/folderA type ext4 (rw)
/dev/sde1 on /boot type ext2 (rw)
/dev/md0 on /home/user/folderB type ext4 (rw)

```

The mount is done automatically as the entries are in the fstab file: 
```

/dev/sda1       /home/user/folderA       auto    defaults        0       0
/dev/md0        /home/user/folderB    auto    defaults        0       0

```

At this point if I go to /home/user/folderA or folderB, I have all my data and everything's fine. However, after a few hours when I come back and go to /home/user/folderA or folderB, the folders are empty!

Things I know/have tried: 

[LIST]
If at this point I run the "mount" command, I do see that the drives are still mounted, but the data is gone! 
[/LIST]
[LIST]
I see nothing in syslog indicating an error
[/LIST]
[LIST]
I have both folderA and folderB shared out using samba and when the drive "goes away" I see errors in the samba.log file that look like this 
[/LIST]
```
[2013/03/24 15:39:31.378526,  0] smbd/service.c:1055(make_connection_snum) canonicalize_connect_path failed for service internal, path /home/user/folderA/subfolder
```

I would appreciate any ideas ... 

Here's the fdisk output for the two disks in question: 


```

sudo fdisk -l /dev/sda

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 3000.6 GB, 3000591900160 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860531055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.

 sudo fdisk -l /dev/md0

Disk /dev/md0: 2000.1 GB, 2000136699904 bytes
2 heads, 4 sectors/track, 488314624 cylinders, total 3906516992 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 262144 bytes / 524288 bytes
Disk identifier: 0xd3865a55

    Device Boot      Start         End      Blocks   Id  System
/dev/md0p1            2048  3906516991  1953257472   83  Linux


```

And here's the status on the raid array : 


```

sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Tue Dec 18 17:17:11 2012
     Raid Level : raid5
     Array Size : 1953258496 (1862.77 GiB 2000.14 GB)
  Used Dev Size : 976629248 (931.39 GiB 1000.07 GB)
   Raid Devices : 3
  Total Devices : 3
    Persistence : Superblock is persistent

    Update Time : Sun Mar 24 20:20:48 2013
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 256K

           Name : respiro:0  (local to host respiro)
           UUID : aaef07e6:d3f3ab06:3cae4996:48a79a6b
         Events : 31756

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       3       8       49        2      active sync   /dev/sdd1


```
I would appreciate any feedback on trying to figure this out ....

---

### Post by SaturnusDJ on 2013-03-25
While everything is still fine, are writes to the paths/disks saved?

Try 'hdparm -I' and 'smartctl -X' before and after the problem occurs to gather some information.

---

### Post by miragemonger on 2013-03-27
Thanks for the tip. Unfortunately (or fortunately?) the issue hasn't recurred in the last couple of days. I'll keep an eye on it and post back if I run into it again.

---

