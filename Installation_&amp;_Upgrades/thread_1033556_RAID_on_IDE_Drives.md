---
title: "RAID on IDE Drives"
date: 2009-01-07
forum: Installation &amp; Upgrades
---

### Post by aaronbridge on 2009-01-07
When creating a RAID 1 array with IDE drives should the drives be on different IDE cables?  Does it matter at all?  I am creating the array with the Ubuntu documentation instructions (software array).

Thanks

---

### Post by lemming465 on 2009-01-09
It depends on how much hardware you have, how flexible your disk controllers and OS are, and how much resiliance you want.  In general putting the two disks on different IDE cable is good, if only because they aren't competing for cable time (master and slave IDE devices can't talk at the same time).  Since you are doing this with mdadm from Linux, there are no issues in your case, and it's a good idea. 

A lot of low-end disk controllers can't cope with drives being on different channels.  High end server-grade hardware has all sorts of exotic features like battery backup for the ECC-protected write cache, dual independent redundant paths from the host to the hardware RAID controller, multiple independent internal busses, hot-swap hardware, dual power supplies, etc.  It's gets very pricey, where "very" means about 3x the going rate for vanilla SCSI "JBOD" single disk drives.  The idea is that there should be no single hardware failure that takes out the storage subsystem.  In your case you probably just want to survive the most common problem, which is drive failure.

---

### Post by scharkalvin on 2009-01-09
In addition to the fact that two drives on the same cable can't operate at the same time, there is a possibility that if one of the drives goes dead it might lock up the interface for the other.  So for the sake of redundancy and speed it is a good idea to put one drive on each cable.  Only problem is your CD rom drive will end up sharing a cable with one of the hard disks so you still will have the speed issue when copying from CD to HD (or from HD to CD when burning a CD).


SCSI disks don't have an issue with multiple drives on a single cable, and SATA drives always are on their own cable so no issue there either.  

If your motherboard allows for booting from other than the first hard disk, and also allows for more than one hard disk in the boot order, put each drive in your raid array into the boot order.  Then if the first disk dies the system will boot from the second disk (assuming you are using RAID1 here which will not lose any files if one disk in the array dies).

---

