---
title: "Problem replacing failed disk using mdadm"
date: 2012-12-08
forum: Hardware
---

### Post by gilphilbert on 2012-12-08
I've read quite a few posts, but none have helped and this one really has me stumped. I have a machine that has 3 disks in a RAID 5 set that have been working fine. Recently, one of the disks failed and I now have a replacement.

However, I can't remove the old disk from the array as it no longer has a device assigned to it:

```
[root@fs ~]# mdadm -D /dev/md127
/dev/md127:
        Version : 1.2
  Creation Time : Fri Oct 27 15:17:39 2006
     Raid Level : raid5
     Array Size : 3907025920 (3726.03 GiB 4000.79 GB)
  Used Dev Size : 1953512960 (1863.02 GiB 2000.40 GB)
   Raid Devices : 3
  Total Devices : 2
    Persistence : Superblock is persistent

    Update Time : Sat Dec  8 18:45:28 2012
          State : clean, degraded
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : fs:0
           UUID : d736714e:695c65a7:9aecb2f7:e21db3dd
         Events : 55081

    Number   Major   Minor   RaidDevice State
       0       8       48        0      active sync   /dev/sdd
       1       8       32        1      active sync   /dev/sdc
       2       0        0        2      removed
```

Because there's no drive associated with the failed device, I can't use *mdadm --remove*.

I'm running out of ideas! Can anyone help?

Thanks

---

### Post by lemming465 on 2012-12-22
What happens if you just plug in the new drive?

---

