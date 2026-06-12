---
title: "ram and interpreting memtest86+ results"
date: 2008-03-09
forum: Hardware &amp; Laptops
---

### Post by shadylookin on 2008-03-09
I've recently been having trouble with my laptop. At first I thought it was a corrupted hard drive issue, but after checking the partition with gparted nothing came up wrong. Then i tried doing a memtest86+ and it has the following output and I"m not sure how to interpret it. 

> 
memtest86+ v 1.70                           pass 28%
athlon 64(0.09) 1995mhz                   test 65%
l1 cache 128k 16353MB/s                   test #4 [moting inversions, random pattern]
l2 cache 512k 3896MB/s                    testing 120k-895M   894M
memory 894 2052mbs                       pattern: fffffbff
chipset amd 8000 (ecc disabled)
settings Ram 205mhz (ddr570) / cas : 4-4-4-12 / ddr-2 (128 bits)

Walltime             cached        rsvdmem         memmap       cache     ecc        test      pass    error     eccerrors
15:43:30            894m            386M             e820-std       on           off        std        46        252          0


then it's followed by a big red box. 

I can only imagine 252 errors with only 46 passes is bad news. However is there any way to fix it or work around? Or should I just cough up the cash for new sticks of ram?

---

### Post by eldragon on 2008-03-09
usually anything above 0 errors is bad news.

if the errors appear after a long run, it might be related to heat, and not faulty ram at all.

check for temperature issues.

---

