---
title: "How to clone RAID to one HDD ?"
date: 2016-12-17
forum: Hardware
---

### Post by testik on 2016-12-17
I have software raid installed on Ubuntu server, how can I clone those into single HDD clone ?

---

### Post by TheFu on 2016-12-17
rsync.
fsarchiver.

I'm assuming you want to clone the files, not the bits?

---

### Post by testik on 2016-12-25
In the end I want to get HDD image which could start after "extracting" image on the similar machine - means same hardware.

---

### Post by TheFu on 2016-12-25
> **testik said:**
> In the end I want to get HDD image which could start after "extracting" image on the similar machine - means same hardware.

The system settings will be 99.99999% the same, but differences have to be made for 
a) non-RAID - depends on the RAID used (HW/SW/Fake)
b) different UUIDs on disks - fstab/initrd stuff
c) different NIC MACs - udev stuff

Takes about 15 seconds to fix, once you know how.
Actually, the HW doesn't need to be all that similar for this to work.  I've moved HDDs and SW-RAID between fairly different machines a few times with little issues.  Pentium4 --> Core i7 for example.  Linux discovers most HW at boot. It is only the few things that humans like to be consistent between boots that need little tweaks.

Having a bit-4-bit image is wasteful of storage, IMHO. It also prevents doing automatic, daily, versioned, backups.  Here (well, not really "here"), the RTO is 1 hour.  Generally, we can have a system restored in 30-45 minutes from any of the versioned backups.  Only the amount of data involved makes the time longer. For systems with under 30G of data, which is almost all of them, 45min would be the longest time a restore takes.

---

