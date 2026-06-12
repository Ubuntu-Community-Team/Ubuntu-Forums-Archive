---
title: "[SOLVED] Help recovering Raid5 array"
date: 2018-03-15
forum: Hardware
---

### Post by psykokid on 2018-03-15
A little bit of background first. I store a bunch of data on a Thecus N4200Pro NAS array. I had gotten a report that one of the 4 drives in the array was showing smart errors so I swapped out the offending drive (#4) and it got to work rebuilding. About 60% into the rebuild one of the other drives in the array drops out, #1 in this case. Great.. I shut down and try swapping back in the original #4 to see if it will come back up. No dice. So I shut down and swap #1 & #2 to see if it can recover with the bad drive swapped around and replce the #4 with the half rebuilt #4. In hindsight this was bad. I should have shut down after the first one and cloned all the original discs from there. The device boots back up and of course the raid fails to assemble, showing only disc 3 and 4, 4 being marked as a spare. At this point I shut everything down and pull all the discs and clone them, making sure to keep track of the number order. I put all 4 cloned discs into my unbutu 16.04 LTS box in the correct drive order and booted up. All 4 discs show up, and show the partitions in Disks. It shows a raid5 array and a raid1 array as well. The raid1 array is the system info for the NAS, not really concerned with that. The raid5 array is the one i'm interested in with all my data on it, but I cant access anything on it. So time to start digging.

First i ran* **cat /proc/mdstat*** to see the arrays- 

```
jake@ubuntu-box:~$ cat /proc/mdstat
Personalities : [raid1] [linear] [multipath] [raid0] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sdd1[3]
      1959884 blocks super 1.0 [4/1] [___U]
      
md1 : inactive sdd2[3](S) sdc2[2](S) sdb2[1](S) sda2[0](S)
      3899202560 blocks
       
unused devices: <none>
```

Ok, sees two arrays. So we get the details on md1 from: ***mdadm --detail /dev/md1***
```
jake@ubuntu-box:~$ sudo mdadm --detail /dev/md1
/dev/md1:
        Version : 0.90
     Raid Level : raid0
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent


          State : inactive


           UUID : e7ab07c3:b9ffa9ae:377e3cd3:a8ece374
         Events : 0.14344


    Number   Major   Minor   RaidDevice


       -       8       50        -        /dev/sdd2
       -       8       34        -        /dev/sdc2
       -       8       18        -        /dev/sdb2
       -       8        2        -        /dev/sda2
```

Hrmm.. that's odd. showing the raid as raid0, which is not the case. Ok, lets check out each individual partition with: [I]**mdadm --examine /dev/sdXX**
[/I]
Disc 1

```
jake@ubuntu-box:~$ sudo mdadm --examine /dev/sda2/
dev/sda2:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : e7ab07c3:b9ffa9ae:377e3cd3:a8ece374
  Creation Time : Thu Aug 18 14:30:36 2011
     Raid Level : raid5
  Used Dev Size : 974800000 (929.64 GiB 998.20 GB)
     Array Size : 2924400000 (2788.93 GiB 2994.59 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 1


    Update Time : Tue Mar 13 14:00:33 2018
          State : clean
 Active Devices : 3
Working Devices : 4
 Failed Devices : 1
  Spare Devices : 1
       Checksum : e52c5f8 - correct
         Events : 20364


         Layout : left-symmetric
     Chunk Size : 64K


      Number   Major   Minor   RaidDevice State
this     0       8        2        0      active sync   /dev/sda2


   0     0       8        2        0      active sync   /dev/sda2
   1     1       8       18        1      active sync   /dev/sdb2
   2     2       8       34        2      active sync   /dev/sdc2
   3     3       0        0        3      faulty removed
   4     4       8       50        4      spare   /dev/sdd2
```

Disc 2

```
jake@ubuntu-box:~$ sudo mdadm --examine /dev/sdb2/
dev/sdb2:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : e7ab07c3:b9ffa9ae:377e3cd3:a8ece374
  Creation Time : Thu Aug 18 14:30:36 2011
     Raid Level : raid5
  Used Dev Size : 974800000 (929.64 GiB 998.20 GB)
     Array Size : 2924400000 (2788.93 GiB 2994.59 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 1


    Update Time : Tue Mar 13 14:56:30 2018
          State : clean
 Active Devices : 2
Working Devices : 3
 Failed Devices : 1
  Spare Devices : 1
       Checksum : e597e42 - correct
         Events : 238868


         Layout : left-symmetric
     Chunk Size : 64K


      Number   Major   Minor   RaidDevice State
this     1       8       18        1      active sync   /dev/sdb2


   0     0       0        0        0      removed
   1     1       8       18        1      active sync   /dev/sdb2
   2     2       8       34        2      active sync   /dev/sdc2
   3     3       0        0        3      faulty removed
   4     4       8       50        4      spare   /dev/sdd2
```

Disc 3

```
jake@ubuntu-box:~$ sudo mdadm --examine /dev/sdc2/
dev/sdc2:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : e7ab07c3:b9ffa9ae:377e3cd3:a8ece374
  Creation Time : Thu Aug 18 14:30:36 2011
     Raid Level : raid5
  Used Dev Size : 974800000 (929.64 GiB 998.20 GB)
     Array Size : 2924400000 (2788.93 GiB 2994.59 GB)
   Raid Devices : 4
  Total Devices : 3
Preferred Minor : 1


    Update Time : Tue Mar 13 15:10:07 2018
          State : clean
 Active Devices : 1
Working Devices : 2
 Failed Devices : 2
  Spare Devices : 1
       Checksum : e598570 - correct
         Events : 239374


         Layout : left-symmetric
     Chunk Size : 64K


      Number   Major   Minor   RaidDevice State
this     2       8       34        2      active sync   /dev/sdc2


   0     0       0        0        0      removed
   1     1       0        0        1      faulty removed
   2     2       8       34        2      active sync   /dev/sdc2
   3     3       0        0        3      faulty removed
   4     4       8       50        4      spare   /dev/sdd2
```

and Disc 4

```
jake@ubuntu-box:~$ sudo mdadm --examine /dev/sdd2/
dev/sdd2:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : e7ab07c3:b9ffa9ae:377e3cd3:a8ece374
  Creation Time : Thu Aug 18 14:30:36 2011
     Raid Level : raid5
  Used Dev Size : 974800000 (929.64 GiB 998.20 GB)
     Array Size : 2924400000 (2788.93 GiB 2994.59 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 1


    Update Time : Tue Mar 13 11:03:10 2018
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : e526d87 - correct
         Events : 14344


         Layout : left-symmetric
     Chunk Size : 64K


      Number   Major   Minor   RaidDevice State
this     3       8       50        3      active sync   /dev/sdd2


   0     0       8        2        0      active sync   /dev/sda2
   1     1       8       18        1      active sync   /dev/sdb2
   2     2       8       34        2      active sync   /dev/sdc2
   3     3       8       50        3      active sync   /dev/sdd2
```

So - Magic numbers and UUID are all good between the set. Events are all out of whack because it had tried to rebuild the replaced #4 as a spare instead of just rebuilding #4

Disc 4 has the correct info for the raid, and the sequencing as it was the drive I pulled originally and didn't get anything re-written. Discs 1-3 are showing in various states of chaos from swapping things around.

So two questions -

One - Why is it showing up as raid0 in the [B][I]mdadm --detail
[/I][/B]
Two - Is it possible to update the info for the first three discs that I got from the ***mdadm --examine /dev/sdd2 ***so that it sees everything as it should be, instead of the cluster that I inadvertently made of it. I *think* if I can find a way to update the info for those partitions or discs the raid should reassemble correctly and rebuild itself so I can access my data

Any ideas would be helpful, as I've gotten about as far as I can get trying to figure this out on my own and doing a ton of searching.

Thanks advance.

Jake

---

### Post by psykokid on 2018-03-16
So i tried a couple of things. First I stopped the raid after rebooting the machine this morning:


```
jake@ubuntu-box:~$ sudo mdadm -S /dev/md1
mdadm: stopped /dev/md1

```

So then I try to assemble using the uuid for the array:


```
jake@ubuntu-box:~$ sudo mdadm --assemble /dev/md1 --
uuid=e7ab07c3:b9ffa9ae:377e3cd3:a8ece374
mdadm: /dev/md1 assembled from 1 drive - not enough to start the array.

```

Ok, that's what I expected. So let's try and force it:


```
jake@ubuntu-box:~$ sudo mdadm --assemble /dev/md1 --force --
uuid=e7ab07c3:b9ffa9ae:377e3cd3:a8ece374
mdadm: forcing event count in /dev/sdb2(1) from 238868 upto 239374
mdadm: forcing event count in /dev/sda2(0) from 20364 upto 239374
mdadm: /dev/md1 assembled from 3 drives - not enough to start the array.

```

Hrmm.. that should have worked. Let's try reassembling manually by calling out the individual partitions for the raid:


```
jake@ubuntu-box:~$ sudo mdadm --assemble /dev/md1 /dev/sda2 /dev/sdb2 
/dev/sdc2 /dev/sdd2 --force
mdadm: /dev/md1 has been started with 3 drives (out of 4).

```

BINGO! Looks like it started with 3 of the 4 drives. Good enough, that means I can access my data! Let's check the details just for giggles:


```
jake@ubuntu-box:~$ sudo mdadm --detail /dev/md1/dev/md1:
        Version : 0.90
  Creation Time : Thu Aug 18 14:30:36 2011
     Raid Level : raid5
     Array Size : 2924400000 (2788.93 GiB 2994.59 GB)
  Used Dev Size : 974800000 (929.64 GiB 998.20 GB)
   Raid Devices : 4
  Total Devices : 3
Preferred Minor : 1
    Persistence : Superblock is persistent


    Update Time : Tue Mar 13 14:00:33 2018
          State : clean, degraded 
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0


         Layout : left-symmetric
     Chunk Size : 64K


           UUID : e7ab07c3:b9ffa9ae:377e3cd3:a8ece374
         Events : 0.239374


    Number   Major   Minor   RaidDevice State
       0       8        2        0      active sync   /dev/sda2
       1       8       18        1      active sync   /dev/sdb2
       2       8       34        2      active sync   /dev/sdc2
       6       0        0        6      removed

```

I'm copying off data as we speak. So data was not irretrievable - just needed to know the right commands to force the raid to reassemble.

---

### Post by mörgæs on 2018-03-17
Thanks for posting the solution. If you use Thread Tools for marking the thread solved there is a better chance that someone will find it.

---

