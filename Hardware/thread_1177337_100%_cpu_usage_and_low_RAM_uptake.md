---
title: "100% cpu usage and low RAM uptake"
date: 2009-06-03
forum: Hardware
---

### Post by jonathanyates on 2009-06-03
I have been using UBUNTU for about 2 years and suffered terribly from frequent crashes during Openoffice and Firefox to name the two most used apps. Sometimes the the crash results in an application crash only. Other times there is an exit to the login screen. On rare occasions the machine needs a reboot. Thisall happens up to 15 times a day!!!!

So I thought I would sort it out.

After looking through the forums I have decided that there is an issue with my RAM and CPU.

Is my computer crashing because of these reasons?

CHIPSET AND RAM

CPU: INTEL CELLERON 1.73MHZ (FSB 533MHZ)
RAM: 2x DDR2 667


MEMTEST86+ RESULTS

LI 19923 MB/s
L2 11329 MB/s

RAM 900 MB/s   <------------------------ is this normal ?

------------
 
The alarming thing about the memtest is the RAM is being accessed at a tiny 900 MB/s compared with the L1 & L2 Caches

I am no expert but this seems wrong!

The RAM usage is very low on my machine but the CPU is at 100% during intensive applications like browsing a non flash webpage(!!) or even just filling in this form - the machine just crashed out to login again!.

All help greatly received

Jonathan

---

### Post by Sef on 2009-06-03
How long did you let memtest run?   It should run a few hours - overnight is best.

---

### Post by mcduck on 2009-06-03
It's absolutely normal that RAM is very slow compared to cache which is embedded in the processor itself. On the other hand, the size of L2 cache is usually around 512-1024kB (that's _kilo_bytes, not megabytes!) per processor core and L1 is even smaller.

That being said, 900MB/s seems a bit slow for DDR2-667 (as it has peak transfer rate of over 5000MB/s and memtest should be giving at least half of that)

Anyway, Sef is correct, if you want to use Memtest to check that your RAM isn't broken you need to run it overnight.

edit: could you tell what settings does memtest report for your RAM (FSB, frequency & CAS timings)

---

