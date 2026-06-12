---
title: "Ntfs External HDD formatted Fat 32 by mistake"
date: 2014-12-26
forum: Hardware
---

### Post by RayArdia on 2014-12-26
Using gparted I wanted to format a 2.0GB pen drive to Fat32. It showed as dev/sdd1, capacity 1.8GB, but right under the Seagate drive, dev/sdc1, capacity 1.8TB.
You've guessed correctly, I formatted the wrong one to Fat32.
As soon as I realised, I unmounted the Seagate drive and for good measure disconnected it, but of course the damage was done, even though it clearly hadn't had time to format the whole partition.
I've been looking for some , preferably Open Source and free, recovery software - what would you recommend please?

---

### Post by yancek on 2014-12-26
Testdisk at the site below.  Make sure you read the Step-by-Step instructions first at the link just below Documentation.



[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by Mark Phelps on 2014-12-26
> I've been looking for some , preferably Open Source and free, recovery software - what would you recommend please? 

Then, you're limiting yourself unnecessarily.

Windows software is generally better at recovering Windows filesystems; Linux software, at recovering Linux filesystems.

If sdc1 was formatted NTFS, then you need to consider using Windows data recovery apps on it.  A free one (but NOT open source) is "recuva".

---

