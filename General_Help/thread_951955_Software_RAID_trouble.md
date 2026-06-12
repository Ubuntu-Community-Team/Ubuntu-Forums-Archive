---
title: "Software RAID trouble"
date: 2008-10-18
forum: General Help
---

### Post by Cr0n_J0b on 2008-10-18
I have a set of 3 drives that were working great in a RAID0 stripe.  I have since upgraded the system and reassembled the drives, but they are now showing up as RAID 5:  Is there a way to fix this without blowing away the data?  I'm inclined to create the array again with the proper settings, but will that kill my data?

thanks

/dev/sdd2:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 532ab2b0:4f1bc51e:4c0d2395:9c0bfdf6
  Creation Time : Tue Nov 27 20:15:58 2007
     Raid Level : raid5
  Used Dev Size : 244195968 (232.88 GiB 250.06 GB)
     Array Size : 488391936 (465.77 GiB 500.11 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 1

    Update Time : Sat Oct 18 10:57:28 2008
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0
       Checksum : d2611b7e - correct
         Events : 0.44

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8       50        2      active sync   /dev/sdd2

   0     0       8       18        0      active sync   /dev/sdb2
   1     1       8       34        1      active sync   /dev/sdc2
   2     2       8       50        2      active sync   /dev/sdd2

---

### Post by fjgaude on 2008-10-18
Never have heard of anything like this, raid0 to raid5... is your data still okay?

What does this show:

```
sudo mdadm -D /dev/md[n]
```

The n is whatever you have called your array.

---

