---
title: "mdadm raid5 - drive dropped while replacing another"
date: 2011-01-28
forum: Hardware
---

### Post by gamr333 on 2011-01-28
Hi,

So last week I finally decided to expand my RAID5 array from 13 drives to 15. My 2 new drives arrived Monday. After adding them to the array, it seems that one of the older drives was dropped (seemed like it was unplugged), so it added the 2 new drives as spares and started recovering with 1 of them. This was ok, just weird timing. After letting it recover, I began my investigation and it seemed that the drive that was dropped was ok. I verified the connections, the system recognized it, and its SMART status was healthy. I assumed that I bumped it during my installation or something. I re-added it to the array and began the grow operation. About 20 minutes in, the drive dropped again. Clearly, there is something wrong with the drive. Unfortunately, it had started the grow operation and I was unable to stop it. Now I'm stuck with a 15 RAID5 array with only 14 drives. I had ordered a replacement drive on Monday and it arrived today. I installed it and started the add to repair the array to finally have 15 good drives again. However, I now have another problem, it seems that mdadm thinks another drive is bad. Before now, I never received any warning, but it looks like the SMART status is unhealthy (a high number of reallocated sectors). The drive still functions, but mdadm drops it after about 30 seconds of recovering the array. Is there any way to keep mdadm from marking this drive as bad at least as long to recover the RAID and replace the original dead drive? 

I can start the recovery with:
```
sudo mdadm --assemble --force --scan
```
which results in:
```
mdadm: metadata format 00.90 unknown, ignored.
mdadm: forcing event count in /dev/sdc1(3) from 94033 upto 94054
mdadm: clearing FAULTY flag for device 12 in /dev/md0 for /dev/sdc1
mdadm: /dev/md0 has been started with 14 drives (out of 15) and 1 spare.
```
 but it only works for about 30 seconds before the drive is marked as down again.

Summary:
1. Added 2 new drives
2. 1 drive is dead and mdadm starts recovery
3. Recovery finishes, start grow with seemingly healthy drive
4. Drive dies again, grow continues with 14/15 drives
5. Add new drive
6. A different drive is marked as faulty while in the process of recovering the array. 
7. mdadm counts 13/15 drives


Here's my /proc/mdstat:
```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdl1[0] sdn1[15](S) sdb1[14] sdi1[12] sdk1[11] sdd1[10] sdh1[9] sdg1[8] sdf1[7] sde1[6] sdj1[5] sdp1[4] sdc1[16](F) sdm1[2] sda1[1]
      13674639104 blocks level 5, 64k chunk, algorithm 2 [15/13] [UUU_UUUUUUUUU_U]
      
unused devices: <none>

```

And here's my mdadm --detail /dev/md0
```
mdadm: metadata format 00.90 unknown, ignored.
/dev/md0:
        Version : 00.90
  Creation Time : Thu May 27 21:04:42 2010
     Raid Level : raid5
     Array Size : 13674639104 (13041.15 GiB 14002.83 GB)
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
   Raid Devices : 15
  Total Devices : 15
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Fri Jan 28 19:46:48 2011
          State : clean, degraded
 Active Devices : 13
Working Devices : 14
 Failed Devices : 1
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 54c684e5:3165a620:496c1f39:996a6983
         Events : 0.94072

    Number   Major   Minor   RaidDevice State
       0       8      177        0      active sync   /dev/sdl1
       1       8        1        1      active sync   /dev/sda1
       2       8      193        2      active sync   /dev/sdm1
       3       0        0        3      removed
       4       8      241        4      active sync   /dev/sdp1
       5       8      145        5      active sync   /dev/sdj1
       6       8       65        6      active sync   /dev/sde1
       7       8       81        7      active sync   /dev/sdf1
       8       8       97        8      active sync   /dev/sdg1
       9       8      113        9      active sync   /dev/sdh1
      10       8       49       10      active sync   /dev/sdd1
      11       8      161       11      active sync   /dev/sdk1
      12       8      129       12      active sync   /dev/sdi1
      13       0        0       13      removed
      14       8       17       14      active sync   /dev/sdb1

      15       8      209        -      spare   /dev/sdn1
      16       8       33        -      faulty spare   /dev/sdc1

```



Any thoughts or suggestions would be greatly appreciated! It seems that the drive is just *about* to fail, and is not yet dead, but mdadm is marking it as down anyway. Please let me know if you need any more information.

---

### Post by gamr333 on 2011-02-01
Interesting development: when removing the replacement drive, thus keeping mdadm from growing/recovering, the RAID works. Most of the data is intact, with the occasional missing folder or file. Is there any way to repair this RAID at all? Just to replace the original drive and now this new drive. The drive has 1170 bad sectors and my theory is that when mdadm starts recovering, it's fine until it hits a bad sector, at which point it drops the drive.

Any suggestions would be greatly appreciated.

---

