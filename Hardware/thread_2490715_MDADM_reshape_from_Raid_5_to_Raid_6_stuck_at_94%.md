---
title: "MDADM reshape from Raid 5 to Raid 6 stuck at 94%"
date: 2023-09-13
forum: Hardware
---

### Post by pook2022 on 2023-09-13
I actually did this by accident.  I was looking at the raid array in Webmin and I clicked upgrade to Raid6 to see what the options would be and it just started doing it.
So I figured it's probably not a bad thing.  I have 8 x 8TB drives and one of them was doing nothing.

So it chugged away for 3 days.  Then at 94% it stopped and the estimated time has just been growing from there.
What's the recommended protocol here? Can I stop it nicely?

```

root@odin:~# mdadm --detail /dev/md2
/dev/md2:
           Version : 1.2
     Creation Time : Sat Mar 20 16:30:34 2021
        Raid Level : raid6
        Array Size : 46883392512 (43.66 TiB 48.01 TB)
     Used Dev Size : 7813898752 (7.28 TiB 8.00 TB)
      Raid Devices : 8
     Total Devices : 8
       Persistence : Superblock is persistent


     Intent Bitmap : Internal


       Update Time : Tue Sep 12 21:02:26 2023
             State : clean, degraded, reshaping
    Active Devices : 7
   Working Devices : 8
    Failed Devices : 0
     Spare Devices : 1


            Layout : left-symmetric-6
        Chunk Size : 512K


Consistency Policy : bitmap


    Reshape Status : 94% complete
        New Layout : left-symmetric


              Name : odin:2  (local to host odin)
              UUID : 1db07e6e:f0ad68d8:96b6e398:9f40a847
            Events : 122446


    Number   Major   Minor   RaidDevice State
       0       8      112        0      active sync   /dev/sdh
       1       8       96        1      active sync   /dev/sdg
       2       8       64        2      active sync   /dev/sde
       3       8       80        3      active sync   /dev/sdf
       6       8       16        4      active sync   /dev/sdb
       4       8       48        5      active sync   /dev/sdd
       5       8       32        6      active sync   /dev/sdc
       7       8        0        7      spare rebuilding   /dev/sda

```


```

root@odin:~# cat /proc/mdstat
md2 : active raid6 sdb[6] sda[7] sdd[4] sde[2] sdc[5] sdh[0] sdf[3] sdg[1]      46883392512 blocks super 1.2 level 6, 512k chunk, algorithm 18 [8/7] [UUUUUUU_]
      [==================>..]  reshape = 94.8% (7408359424/7813898752) finish=317551.1min speed=21K/sec
      bitmap: 0/59 pages [0KB], 65536KB chunk
unused devices: <none>

```
It's been on 7408359424/7813898752 for almost a day now.

```
root@odin:~# ps aux|grep md2
root        1446  0.0  0.0      0     0 ?        D    Sep05   0:01 [jbd2/md2-8]
root       91913  0.0  0.0   3496  1320 ?        D    15:02   0:00 dumpe2fs -h /dev/md2
root      169216  0.0  0.0   3496  1276 ?        D    Sep12   0:00 dumpe2fs -h /dev/md2
root      342027  0.0  0.0   3496  1344 ?        D    Sep12   0:00 dumpe2fs -h /dev/md2
root      476083  0.0  0.0   6612  2372 pts/0    S+   17:53   0:00 grep --color=auto md2
root      600748 31.5  0.0      0     0 ?        S    Sep11 1112:11 [md2_raid6]
root      600753  0.6  0.0   8348  7292 ?        DLs  Sep11  23:27 /sbin/mdadm --grow --continue /dev/md2
root      651639  0.0  0.0   3496  1376 ?        D    Sep12   0:00 dumpe2fs -h /dev/md2
root      855372  0.0  0.0   3496  1400 ?        D    Sep12   0:00 dumpe2fs -h /dev/md2
root     1354768  0.0  0.0   3620  1280 ?        D    Sep12   0:00 e2label /dev/md2
root     1636759  0.0  0.0   3620  1268 ?        D    Sep11   0:00 e2label /dev/md2
root     1673665  0.0  0.0   3496  1320 ?        D    Sep11   0:00 dumpe2fs -h /dev/md2
root     2391608  0.0  0.0   3496  1288 ?        D    01:03   0:00 dumpe2fs -h /dev/md2
root     4027635  0.0  0.0   3496  1292 ?        D    Sep12   0:00 dumpe2fs -h /dev/md2
root     4117534  0.0  0.0   3620  1204 ?        D    Sep12   0:00 e2label /dev/md2
root     4182919  0.0  0.0   3496  1328 ?        D    Sep12   0:00 dumpe2fs -h /dev/md2

```

---

### Post by TheFu on 2023-09-13
Wipe the array.
Recreate the array as you want it.
Restore the data that you've backed up.

RAID is never a replacement for backups. Sometimes the best solution to a RAID issue is to wipe, start over and restore.
RAID solves 2 issues.  HA and (maybe) improved performance. Nothing else.

I suspect this isn't what you wanted to read.  For most RAID issues, this is my answer, since for a few TB of data, it is a known thing for when the restore will be finished.  Plus, backups have 1001 uses, including solving many RAID issues.

BTW, from the Linux RAID How-To guide:
> Raid 6 is the only raid level where mdadm may complain that it cannot carry out a conversion directly between levels 4, 5 and 6. This is down to the way the parity blocks are scattered amongst the devices. The reshape is almost certainly possible, but it may require doing it in a couple of stages rather than directly. 

BTW, if you choose to wipe and start over, please follow the best practices and setup partition tables on each of the disks, then assign the RAID device to a partition, not the entire drive.  There are many reasons for this, but mainly it is for upgrade and migration flexibility.

---

### Post by pook2022 on 2023-09-13
Phew that was a bit scary.  The whole process was hung so I had to reboot the machine.  It wouldn't boot normally, hanging on looking at md2, so I had to go in to recovery mode and was able to resume the reshape.
Was getting missing super block errors when trying to moun /dev/md2

**mdadm --stop /dev/md2**

**mdadm --assemble --scan --force /dev/md2**
Failed to find backup of critical section 
mdadm: Failed to restore critical section for reshape, sorry. 
Possibly you needed to specify the --backup-file
_This didn't work, needed a backup-file.  Which confused me, I thought it was asking for a pre-existing file but it just wants somewhere to store it._

**mdadm --assemble --scan --force --backup-file /tmp/file.bak /dev/md2**
mount it and the rebuild continued successfully

---

