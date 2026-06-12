---
title: "Growing a RAID array gone bad"
date: 2008-03-03
forum: Hardware &amp; Laptops
---

### Post by TacticalSacrifice on 2008-03-03
I have a file server with a RAID 5 array made of 4 750GB drives attached to the motherboard.  I am running kernel 2.6.18 with mdadm version 2.6.2.  I added another drive using a PCI SATA controller, added the new drive to the array and attempted to grow it.  During the process the new drive /dev/sda failed in the array, I removed it from the array, and now it won't respond.  The detail for the array right now is

```

ray@*****:~$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 00.91.03
  Creation Time : Wed May  9 10:53:25 2007
     Raid Level : raid5
     Array Size : 2197715712 (2095.91 GiB 2250.46 GB)
  Used Dev Size : 732571904 (698.64 GiB 750.15 GB)
   Raid Devices : 5
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Mon Mar  3 09:00:43 2008
          State : clean, degraded
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

  Delta Devices : 1, (4->5)

           UUID : f35cf1fa:bb79d553:562fa5a2:fc516a06
         Events : 0.512352

    Number   Major   Minor   RaidDevice State
       0       8       49        0      active sync   /dev/sdd1
       1       8       65        1      active sync   /dev/sde1
       2       8       33        2      active sync   /dev/sdc1
       3       8       17        3      active sync   /dev/sdb1
       4       0        0        4      removed

```
I mount the device and all the data seemed to be there.  I would like to get redundancy back on it's feet without losing any of the data.  How should I go about getting the array functional with or without getting the new drive to work?

---

