---
title: "mdadm Raid 5 drive dead, how to rescue!?"
date: 2009-04-04
forum: Hardware
---

### Post by zackiv31 on 2009-04-04
I just setup a software raid 5 with mdadm in jaunty, with an ext4 file system...

One of the drives in my raid just crapped out.  I have a place where I can backup the data, but how do I go about doing so?  There's so much on creating raids online, but I can't find anything about saving an array if it fails!

---

### Post by zackiv31 on 2009-04-14
So I still haven't solved this problem, I have 3 drives live, but now its only seeing 2... here's some output:

```

root@me:~# mdadm --examine /dev/sda1
/dev/sda1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 30a8b182:23c22b8a:10f5c018:28823fe1 (local to host me)
  Creation Time : Sun Mar 29 23:17:29 2009
     Raid Level : raid5
  Used Dev Size : 732571904 (698.64 GiB 750.15 GB)
     Array Size : 2197715712 (2095.91 GiB 2250.46 GB)
   Raid Devices : 4
  Total Devices : 3
Preferred Minor : 0

    Update Time : Tue Apr 14 02:28:20 2009
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 2
  Spare Devices : 0
       Checksum : f66e1a77 - correct
         Events : 11990

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8        1        0      active sync   /dev/sda1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       0        0        1      faulty removed
   2     2       8       17        2      active sync   /dev/sdb1
   3     3       0        0        3      faulty removed

```
```

root@me:~# mdadm --examine /dev/sdb1 
/dev/sdb1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 30a8b182:23c22b8a:10f5c018:28823fe1 (local to host me)
  Creation Time : Sun Mar 29 23:17:29 2009
     Raid Level : raid5
  Used Dev Size : 732571904 (698.64 GiB 750.15 GB)
     Array Size : 2197715712 (2095.91 GiB 2250.46 GB)
   Raid Devices : 4
  Total Devices : 3
Preferred Minor : 0

    Update Time : Tue Apr 14 02:28:20 2009
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 2
  Spare Devices : 0
       Checksum : f66e1a8b - correct
         Events : 11990

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8       17        2      active sync   /dev/sdb1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       0        0        1      faulty removed
   2     2       8       17        2      active sync   /dev/sdb1
   3     3       0        0        3      faulty removed

```
```

root@me:~# mdadm --examine /dev/sdc1 
/dev/sdc1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 30a8b182:23c22b8a:10f5c018:28823fe1 (local to host me)
  Creation Time : Sun Mar 29 23:17:29 2009
     Raid Level : raid5
  Used Dev Size : 732571904 (698.64 GiB 750.15 GB)
     Array Size : 2197715712 (2095.91 GiB 2250.46 GB)
   Raid Devices : 4
  Total Devices : 3
Preferred Minor : 0

    Update Time : Tue Apr 14 00:50:49 2009
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 1
  Spare Devices : 0
       Checksum : f66e03a7 - correct
         Events : 11982

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     3       8       33        3      active sync   /dev/sdc1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       0        0        1      faulty removed
   2     2       8       17        2      active sync   /dev/sdb1
   3     3       8       33        3      active sync   /dev/sdc1


```

```

root@me:~# cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : inactive sda1[0](S) sdc1[3](S) sdb1[2](S)
      2197715712 blocks
       
unused devices: <none>

```
it says two failed devices for the first 2, but the third only says one failed... but this second drive has not failed (as far as I can tell)...

Is there a way to get these 3 drives working again so I can get all my data off???  Specific commands appreciated as I'm new to recovering software raid..

---

### Post by zackiv31 on 2009-04-14
[bump] my data is important i swear!

---

### Post by zackiv31 on 2009-04-21
Well I'll just keep talking assuming someone will help me...

Where I'm at:

I have 3 drives of 4 of my mdadm software Raid 5, if it matters, I think the original sdb1 failed.  So basically how do I recreate a degraded array without replacing a drive into this array?  I want to be able to read all the data off... the closest I've come was being able to recover 1/3 of it.

What commands to recreate /dev/sda1 /dev/sdb1 and /dev/sdc1 into a degraded raid 5 array (which originally had drive /dev/sdb1 fail)?

Any help again appreciated!

---

### Post by zackiv31 on 2009-04-22
Well I tried remounting:

```

root@zives:~# mdadm --create /dev/md0 --assume-clean --level=5 --verbose --raid-devices=4 /dev/sda1 missing /dev/sdb1 /dev/sdc1 
mdadm: layout defaults to left-symmetric
mdadm: chunk size defaults to 64K
mdadm: /dev/sda1 appears to contain an ext2fs file system
    size=-2097251584K  mtime=Tue Apr 14 03:17:08 2009
mdadm: /dev/sda1 appears to be part of a raid array:
    level=raid5 devices=4 ctime=Tue Apr 14 03:16:57 2009
mdadm: /dev/sdb1 appears to be part of a raid array:
    level=raid5 devices=4 ctime=Tue Apr 14 03:16:57 2009
mdadm: /dev/sdc1 appears to contain an ext2fs file system
    size=-1828816128K  mtime=Tue Apr 14 03:15:58 2009
mdadm: /dev/sdc1 appears to be part of a raid array:
    level=raid5 devices=4 ctime=Tue Apr 14 03:16:57 2009
mdadm: size set to 732571904K
Continue creating array? y
mdadm: array /dev/md0 started.
root@zives:~# cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdc1[3] sdb1[2] sda1[0]
      2197715712 blocks level 5, 64k chunk, algorithm 2 [4/3] [U_UU]
      
unused devices: <none>

```

I then mounted the drives, and did a quick detail check:

```

root@zives:~# mdadm --detail /dev/md0 
/dev/md0:
        Version : 00.90
  Creation Time : Tue Apr 21 21:23:40 2009
     Raid Level : raid5
     Array Size : 2197715712 (2095.91 GiB 2250.46 GB)
  Used Dev Size : 732571904 (698.64 GiB 750.15 GB)
   Raid Devices : 4
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Tue Apr 21 21:28:43 2009
          State : clean, degraded
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 9559c841:522530ee:10f5c018:28823fe1 (local to host zives)
         Events : 0.34

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       0        0        1      removed
       2       8       17        2      active sync   /dev/sdb1
       3       8       33        3      active sync   /dev/sdc1

```

Looked about right, so I started copying my data off of them.  I have 532.5gb's, but it only ended up copying 168.8gb's.  At the end I kept getting a bunch of:

```

cp: cannot stat `dback': Input/output error
cp: cannot access `stuff': Input/output error

```

So I did another detail of the drives:

```

root@zives:~# mdadm --detail /dev/md0 
/dev/md0:
        Version : 00.90
  Creation Time : Tue Apr 21 21:23:40 2009
     Raid Level : raid5
     Array Size : 2197715712 (2095.91 GiB 2250.46 GB)
  Used Dev Size : 732571904 (698.64 GiB 750.15 GB)
   Raid Devices : 4
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Wed Apr 22 00:35:19 2009
          State : clean, degraded
 Active Devices : 2
Working Devices : 2
 Failed Devices : 1
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 9559c841:522530ee:10f5c018:28823fe1 (local to host zives)
         Events : 0.4216

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       0        0        1      removed
       2       8       17        2      active sync   /dev/sdb1
       3       0        0        3      removed

       4       8       33        -      faulty spare   /dev/sdc1

```

And this is basically where I'm at.  One odd thing is that before I did a full drive copy, I copied one of the problem files I had earlier, and the file copied just fine.  But when I did the full drive copy, and the copy started to fail at some trouble file, every file after it seemed to fail too.

Is this a file system check issue?  Someone please help!

---

