---
title: "Won't Detect ZData 640GB USB Hard Drive"
date: 2009-01-06
forum: Hardware
---

### Post by MusicallyInspired on 2009-01-06
I'm running Ubuntu 8.10 and I just got a new ZData 640GB external USB 2.0 hard drive. I unpacked it and plugged it in and switched it on and....nothing happens. Is there no support for this brand or something? Haven't tried it in Windows yet.

---

### Post by MusicallyInspired on 2009-01-07
Never mind, figure out the problem.

It wouldn't work in Windows either but it did detect it. I had to go to Disk Management and found that the drive wasn't actually initialized. So I had to initialize it, partition, then format the thing before I got it to work in Windows and Ubuntu.

I only seem to have 596 GB available out of 640 GB, though. I notice that with all hard drives. And it seems the bigger they are the more you seemed to be jipped from. Like a certain percentage will never be available in any hard drive. Can someone tell me why that is?

---

### Post by Liquid 2 on 2009-01-07
HDD retailers define a kilobyte differently than operating systems, and as drive capacity increases, the "difference" gets bigger.  I believe it's the difference between 1024 bytes and 1000 bytes.

---

