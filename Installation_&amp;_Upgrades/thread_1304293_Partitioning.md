---
title: "Partitioning"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by mark89 on 2009-10-29
Hi

I have Ubuntu installed on a portable hard drive, where Ubuntu's partition is taking up the maximum amount of space.

I was wondering if there was a way to add a Fat32 partition, so that the portable hard drive could be used in windows to store files as normal, also without affecting the currently installed Ubuntu installation?


Thanks

---

### Post by albandy on 2009-10-29
resize it throught gparted

---

### Post by Lord Landis on 2009-10-29
Seconded.  Use gparted to shrink down the Ubuntu partition and then create a new Fat32 one in the free space.

Be warned that this will probably take a long time (USB is slow like that), especially if you're making a huge change (order of 64+ GB).

Also, keep in mind that even though Gparted is pretty safe (I've used it on production systems without any problems), there is always the potential for catastrophic data loss when you're playing around with the partition table.

---

### Post by drs305 on 2009-10-29
Here is a guide on resizing the / partition. It was written for expanding the /, but would apply to shrinking it as well:
[http://ubuntuforums.org/showthread.php?t=1219270]("http://ubuntuforums.org/showthread.php?t=1219270")

---

### Post by mark89 on 2009-11-01
Thanks a lot!!

GParted worked great!

:D

---

