---
title: "ZFS and hard drive order"
date: 2010-02-23
forum: Hardware
---

### Post by kochakaden on 2010-02-23
I recently had a hard drive in my ZFS array die on me.
While this would normally not be a problem, once the drive was no longer recognized, Ubuntu decided to reorder all of the drives (sda became sdc, etc).  I tested this further by disconnecting another drive, and sure enough, Ubuntu reordered the drives again (sdb became sdd, sde became sdb, sdd became sde)!

I'd heard that ZFS compensates for this, but apparently it doesn't:

[FONT="Courier New"][SIZE="2"]# zpool status
  pool: tank
 state: UNAVAIL
status: One or more devices could not be opened.  There are insufficient
        replicas for the pool to continue functioning.
action: Attach the missing device and online it using 'zpool online'.
   see: [http://www.sun.com/msg/ZFS-8000-3C](http://www.sun.com/msg/ZFS-8000-3C)
 scrub: none requested
config:

        NAME        STATE     READ WRITE CKSUM
        tank        UNAVAIL      0     0     0  insufficient replicas
          raidz2    UNAVAIL      0     0     0  insufficient replicas
            sde     FAULTED      0     0     0  corrupted data
            sdf     FAULTED      0     0     0  corrupted data
            sdg     UNAVAIL      0     0     0  cannot open
            sda     FAULTED      0     0     0  corrupted data
            sdb     FAULTED      0     0     0  corrupted data
            sdc     UNAVAIL      0     0     0  cannot open[/SIZE][/FONT]

As of now, I'm trying to figure out how to tell zfs the new order without killing the array, but the underlying problem remains:  How do you ensure that Ubuntu doesn't keep changing drive order?

---

### Post by jmate24 on 2011-10-28
Ubuntu does not support Zfs. it may be able to use it in fuse but the best bet is to go with ext3 it has been around for a while and is very stable.

---

### Post by sleon on 2011-10-29
Although this thread was resurrected from almost two years ago, it's worth pointing out the answer...

Use by-id instead when building the pool from entire disks in vdevs.  This will stay constant.  If you choose to use partitions as components then UUID as worst case.  Bottom line is never use sda, etc.

ZFS on Ubuntu works great if you stick to best practices.  The data integrity gained is worth every bit of learning curve invested.

---

### Post by RealityMaster on 2013-01-02
> **sleon said:**
> 

Use by-id instead when building the pool from entire disks in vdevs.  This will stay constant.  If you choose to use partitions as components then UUID as worst case.  Bottom line is never use sda, etc.



Thank you for this, I've ran into this issue several times.  Once I thought I'd lost my array, when all that had happened was booting with a thumb drive attached.  

Again, thank you.

---

### Post by michael28 on 2013-08-22
> **RealityMaster said:**
> Thank you for this, I've ran into this issue several times.  Once I thought I'd lost my array, when all that had happened was booting with a thumb drive attached.  

Again, thank you.

My issue is that I have my entire backup was created with:

$ sudo zpool create test raidz sda sdb sdc sdd sde sdf


Is there anything I can do to unmount the ZFS pool, and remount with diskid? I really don't want to lose 4tb of personal pics, videos, etc!

---

### Post by michael28 on 2013-08-22
Figured it out!

All I had to do was type: 
# zpool export tank
# zpool import tank

Then it exported the zpool's cache and imported the zfs with their device-id's!!!

---

