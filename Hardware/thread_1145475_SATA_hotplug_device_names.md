---
title: "SATA hotplug device names"
date: 2009-05-01
forum: Hardware
---

### Post by karypid on 2009-05-01
Hello,

I am a first-time software RAID user. I installed Ubuntu 9.04 on a RAID1 volume that was created using two SATA drives (partitions /dev/sda1 and /dev/sdb1).

To test it, I removed the hard disk while the system was running. I was glad to see that the system coped with the failure gracefully. However, when I re-attached the disk, it was given the name /dev/sdc. Therefore, I had to "mdadm --add /dev/md0 /dev/sdc1" in order for the array to start rebuilding itself.

Is there a way to have the disk keep its name so that re-building starts automatically?

---

### Post by karypid on 2009-05-01
I would also like to add, that the device name keeps changing as many times as I do this (i.e. it then becomes /dev/sdd, /dev/sde, etc). When I reboot though, it's /dev/sdb again...

---

### Post by blueridgedog on 2009-05-01
Though this isn't an answer, it is a point to consider.  In real life, if you have a drive failure and you replace a drive, it appears to me you have done the testing needed to understand how the assignments will change and how you can rebuild the array.  Perhaps it is working in as much as it will deliver the fault tolerance you want.

I use hot swap SATA, but use block ID rather than device references.  Granted, I do not use them in a raid setup, so that works for my purposes.  I have my fstab setup to mount a given block ID in a given location and can then insert the drive in any slot in my hot swap bays and it will perform as expected.  Perhaps you can use block id as well?

---

