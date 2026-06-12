---
title: "Ubuntu recognizing less ram after fresh install"
date: 2015-12-09
forum: Hardware
---

### Post by tysonkiblader on 2015-12-09
I had ubuntu 15.04 installed but its support ends at january and i dont have that much bandwidth and money to do a upgrade every 9 months so i turned back to 14.04 upgraded it to 14.04.3 but i have a problem now before my machine recognized 5.7 GB of ram but now it sees 5.2 GB of ram i ran a memtest for 30 minutes pass 1 with 0 errors but why is this sudden decrease in recognised memory should i be alrmed ?


#free -m


             total       used       free     shared    buffers     cached
Mem:          5375       1941       3433        181         62        796
-/+ buffers/cache:       1082       4293
Swap:          975          0        975


#top
top - 12:48:21 up 14 min,  3 users,  load average: 0.72, 0.73, 0.45
Tasks: 206 total,   1 running, 204 sleeping,   0 stopped,   1 zombie
%Cpu(s):  5.4 us,  1.3 sy,  0.0 ni, 93.2 id,  0.0 wa,  0.0 hi,  0.0 si,  0
KiB Mem:   5504452 total,  1993312 used,  3511140 free,    64328 buffers
KiB Swap:   999420 total,        0 used,   999420 free.   820112 cached Me


#grep MemTotal /proc/meminfo


MemTotal:        5504452 kB


#vmstat




procs -----------memory---------- ---swap-- -----io---- -system-- ------cpu-----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa st
 1  0      0 3392356  65764 863000    0    0   133    28  165  920  6  1 90  3  0

---

