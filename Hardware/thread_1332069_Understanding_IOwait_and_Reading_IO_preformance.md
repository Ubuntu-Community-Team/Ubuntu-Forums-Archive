---
title: "Understanding IOwait and Reading IO preformance"
date: 2009-11-19
forum: Hardware
---

### Post by atwskris on 2009-11-19
Hi,

In my attempts to troubleshoot an iowait issue I have realized that I am not understanding how to read the iowait, and what my io performance should be.

From what I understand I think I should have pretty good performance.
I have 2 1TB Seagate 7200.12 in RAID 0 for the OS Partitions, and RAID 1 from the Home partition. The computer should be capable, Intel Dual-Core 3.0 , 4GB Ram, ASUS PQ5-Pro, JFS filesystem .. need more info?

Watching the iotop, after I have an huge amount of iowait it shows very small numbers for read and write, I have never seen it get above 5 MB/s, and when the iowait is maxed out it is showing numbers that as very small as well. 

Shouldn't it be much higher? I would think the io performance would want to try to max it's self out to get processes completed as quickly as possible?

Currently I am running ubuntu 9.10 64bit, and have recently upgraded from 9.04

Thanks!

---

### Post by daphreak on 2009-11-30
I have been having similar issues on 32-bit 9.10 upgraded from 9.04. Most of the time it happens while using Firefox. The iowait shoots up and everything freezes making the entire system unusable. 

I will investigate but so far I have no idea whats causing the problems.

---

### Post by daphreak on 2009-12-01
iotop is showing me lots of activity from updatedb.mlocate when the slowdown occurs. 

Seems similar to this bug report:
[https://bugs.launchpad.net/ubuntu/+source/findutils/+bug/332790]("https://bugs.launchpad.net/ubuntu/+source/findutils/+bug/332790")

---

