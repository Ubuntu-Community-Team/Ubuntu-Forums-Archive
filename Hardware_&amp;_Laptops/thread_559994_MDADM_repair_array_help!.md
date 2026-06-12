---
title: "MDADM: repair array help!"
date: 2007-09-25
forum: Hardware &amp; Laptops
---

### Post by tuckie on 2007-09-25
I currently  have a 5 disk array (sda,b,c,d,e), (just added the last drive a few days ago)  But now, I can't get it to assemble, after it thought one of the drives had failed (reported as degraded).  If I run a mdadm --assemble --scan, I get /dev/sda has no superblock - assembly aborted.  Does anyone have any ideas as to how I could get this working?  , btw  cat /proc/mdstat show nothing, but mdstat --examine /dev/sda gives back this:
```
/dev/sda:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 924216eb:0286f46e:ded1c07b:24d974d7
  Creation Time : Sun Apr 15 15:27:59 2007
     Raid Level : raid5
    Device Size : 488386496 (465.76 GiB 500.11 GB)
     Array Size : 1953545984 (1863.05 GiB 2000.43 GB)
   Raid Devices : 5
  Total Devices : 4
Preferred Minor : 0

    Update Time : Tue Sep 25 20:12:25 2007
          State : active
 Active Devices : 4
Working Devices : 4
 Failed Devices : 1
  Spare Devices : 0
       Checksum : ebdde092 - correct
         Events : 0.327468

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8        0        0      active sync   /dev/sda

   0     0       8        0        0      active sync   /dev/sda
   1     1       8       32        1      active sync   /dev/sdc
   2     2       8       48        2      active sync   /dev/sdd
   3     3       8       64        3      active sync   /dev/sde
   4     0       0        0        0      spare

```

Would running: sudo mdadm --create /dev/md0 --level=5 --raid-devices=5 /dev/sd[abcde] run the risk of me loosing my data, or is it already lost?

---

### Post by tuckie on 2007-09-25
update: for whatever reason, the linux raid autodetect partitions aren't showing up under gparted for the drives, I didn't do any formating on them, so im not sure what thats about.  (is there a way to restore the partition's flag without deleting the data?).  Also I found [this]("http://kev.coolcavemen.com/2007/03/how-to-recover-a-raid-array-after-having-zero-ized-superblocks/") link, which says I should be able to recreate it as long as the data is still there (even if the superblock is fubared).  Trying to recreate it I get this:
```
tuckie@nibbler:~$ sudo mdadm --create /dev/md0 --level=5 --raid-devices=5 /dev/sd[abcde]
mdadm: /dev/sda appears to contain an ext2fs file system
    size=1746177860K  mtime=Wed May  3 21:30:11 2034
mdadm: /dev/sda appears to be part of a raid array:
    level=raid5 devices=5 ctime=Sun Apr 15 15:27:59 2007
mdadm: Cannot open /dev/sdb: Device or resource busy
mdadm: /dev/sdc appears to be part of a raid array:
    level=raid5 devices=5 ctime=Sun Apr 15 15:27:59 2007
mdadm: /dev/sdd appears to be part of a raid array:
    level=raid5 devices=5 ctime=Sun Apr 15 15:27:59 2007
mdadm: /dev/sde appears to be part of a raid array:
    level=raid5 devices=5 ctime=Sun Apr 15 15:27:59 2007
mdadm: create aborted

```

---

### Post by tuckie on 2007-09-25
Alright. Say that the one the drive got corrupted, How would I get it up and running again from the four working drives (saying that the one drive had failed), when mdadm has forgotten they exist?

---

### Post by tuckie on 2007-09-26
I was able to get it mounted using:
mdadm --assemble --run  --force /dev/md0 /dev/sd[acde]

sudo mdadm --assemble --run --force -v /dev/md0 /dev/sd[acde]
mdadm: looking for devices for /dev/md0
mdadm: /dev/sda is identified as a member of /dev/md0, slot 0.
mdadm: /dev/sdc is identified as a member of /dev/md0, slot 1.
mdadm: /dev/sdd is identified as a member of /dev/md0, slot 2.
mdadm: /dev/sde is identified as a member of /dev/md0, slot 3.
mdadm: forcing event count in /dev/sda(0) from 327468 upto 327468
mdadm: added /dev/sdc to /dev/md0 as 1
mdadm: added /dev/sdd to /dev/md0 as 2
mdadm: added /dev/sde to /dev/md0 as 3
mdadm: no uptodate device for slot 4 of /dev/md0
mdadm: added /dev/sda to /dev/md0 as 0
mdadm: /dev/md0 has been started with 4 drives (out of 5) and 1 spare.


The problem is, I am unable to mount it now, and I get a superblock missing or corrupt error.  any ideas?

edit:I have found my block size using tune2fs, how bug of a risk to I run if I execute sudo fsck.ext3 -b 163840 /dev/md0 ?

Its telling me "Block bitmap for group *  is not in group. (block 0)
Relocate<y>?" so I just cancel out, but it pops up quite a few times.

---

