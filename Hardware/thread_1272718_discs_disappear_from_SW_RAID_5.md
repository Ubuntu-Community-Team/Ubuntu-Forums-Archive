---
title: "discs disappear from SW RAID 5"
date: 2009-09-22
forum: Hardware
---

### Post by dom_lech on 2009-09-22
Hi guys...

first i want to apologize for my bad english and the length of the post but i wanted to give a really detailed description of my problem.


Ok, lets start...

i've built a  home-server 

Intel-Atom-Board 
80GB disc for linux
4 x 1TB Hitachi Deskstar for SW RAID 5

i set up the RAID as described here: [http://linux-raid.osdl.org](http://linux-raid.osdl.org)
formated with ext3...

everything was ok...

so i started working with the array... stored data etc.

then came the problems

the array was not reachable over the network and after a restart of the server the array was not mounted and i got this console output:

```

nick@wgserver:~$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : inactive sda[0](S) sdd[3](S) sdc[2](S) sdb[1](S)
      3907049984 blocks
       
unused devices: <none>
nick@wgserver:~$ sudo mdadm --detail /dev/md0
[sudo] password for nick: 
mdadm: md device /dev/md0 does not appear to be active.

```

i tried to restart the array and got this:

```

nick@wgserver:~$ sudo mdadm -R /dev/md0
[sudo] password for nick: 
mdadm: failed to run array /dev/md0: Input/output error


nick@wgserver:~$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : inactive sda[0] sdd[3]
      1953524992 blocks
       
unused devices: <none>

nick@wgserver:~$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Thu Sep  3 20:01:58 2009
     Raid Level : raid5
  Used Dev Size : 976762496 (931.51 GiB 1000.20 GB)
   Raid Devices : 4
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Tue Sep 22 18:14:58 2009
          State : active, degraded, Not Started
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 0a9e4023:d63e19da:3695e6a5:ecac0f10 (local to host wgserver)
         Events : 0.30

    Number   Major   Minor   RaidDevice State
       0       8        0        0      active sync   /dev/sda
       1       0        0        1      removed
       2       0        0        2      removed
       3       8       48        3      active sync   /dev/sdd


```

the log said something like:

```

Sep 22 19:06:35 wgserver kernel: [ 2206.992042] md: kicking non-fresh sdc from array!
Sep 22 19:06:35 wgserver kernel: [ 2206.992078] md: unbind<sdc>
Sep 22 19:06:35 wgserver kernel: [ 2206.992090] md: export_rdev(sdc)
Sep 22 19:06:35 wgserver kernel: [ 2206.992170] md: kicking non-fresh sdb from array!
Sep 22 19:06:35 wgserver kernel: [ 2206.992182] md: unbind<sdb>
Sep 22 19:06:35 wgserver kernel: [ 2206.992192] md: export_rdev(sdb)
Sep 22 19:06:35 wgserver kernel: [ 2207.145406] raid5: device sda operational as raid disk 0
Sep 22 19:06:35 wgserver kernel: [ 2207.145419] raid5: device sdd operational as raid disk 3
Sep 22 19:06:35 wgserver kernel: [ 2207.145431] RAID5 conf printout:
Sep 22 19:06:35 wgserver kernel: [ 2207.145434]  --- rd:4 wd:2
Sep 22 19:06:35 wgserver kernel: [ 2207.145437]  disk 0, o:1, dev:sda
Sep 22 19:06:35 wgserver kernel: [ 2207.145440]  disk 3, o:1, dev:sdd

```

then i ran ```
 fdisk -l 
```
and hey...  the discs were still visible

other fora said just to readd the lost discs... and it worked...
now i was able to restart and mount the array

```

nick@wgserver:~$ sudo mdadm /dev/md0 --add /dev/sdc /dev/sdb
mdadm: re-added /dev/sdc
mdadm: re-added /dev/sdb
nick@wgserver:~$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdb[1] sdc[2] sda[0] sdd[3]
      2930287488 blocks level 5, 64k chunk, algorithm 2 [4/4] [UUUU]
      
unused devices: <none>
nick@wgserver:~$ sudo mount -t ext3 /dev/md0 /media/Hit-RAID0/

```

again i started storing data on the array...  (by the way, no data was lost)

after a short time... same sh... as before and i got this at the console:

```

nick@wgserver:~$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdb[4](F) sdc[5](F) sda[6](F) sdd[7](F)
      2930287488 blocks level 5, 64k chunk, algorithm 2 [4/0] [____]
      
unused devices: <none>
nick@wgserver:~$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Thu Sep  3 20:01:58 2009
     Raid Level : raid5
     Array Size : 2930287488 (2794.54 GiB 3000.61 GB)
  Used Dev Size : 976762496 (931.51 GiB 1000.20 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Tue Sep 22 19:27:37 2009
          State : clean, degraded
 Active Devices : 0
Working Devices : 0
 Failed Devices : 4
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       0        0        1      removed
       2       0        0        2      removed
       3       0        0        3      removed

       4       8       16        -      faulty spare   /dev/sdb
       5       8       32        -      faulty spare   /dev/sdc
       6       8        0        -      faulty spare   /dev/sda
       7       8       48        -      faulty spare   /dev/sdd


```

after unmounting and restarting the array everything started from the beginning.
the only difference is that sometimes one and sometimes two discs are missing.
sometimes sdd, sometimes sdb and sdc, etc.

Is this a harware issue, a software problem... ?

My nerves were shot...

_**can someone help me? PLEASE**_

---

