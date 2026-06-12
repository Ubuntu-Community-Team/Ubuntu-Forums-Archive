---
title: "CMOS showed 1.5 gig of RAM, ubuntu shows only 1 gig. Whats wrong"
date: 2005-06-10
forum: Hardware &amp; Laptops
---

### Post by DaturaX on 2005-06-10
I recently upgraded to another stick of 512MB RAM and my CMOS show 1.5 gig of RAM which is correct.

But when i do a cat /proc/meminfo, it only shows 1 gig of RAM. Anyone can tell me how to fix this? 

MemTotal:       906660 kB
MemFree:        615108 kB
Buffers:         11796 kB
Cached:         139436 kB
SwapCached:          0 kB
Active:         160156 kB
Inactive:        96740 kB
HighTotal:           0 kB
HighFree:            0 kB
LowTotal:       906660 kB
LowFree:        615108 kB
SwapTotal:      473876 kB
SwapFree:       473876 kB
Dirty:             748 kB
Writeback:           0 kB
Mapped:         151584 kB
Slab:            17260 kB
CommitLimit:    927204 kB
Committed_AS:   277728 kB
PageTables:       1716 kB
VmallocTotal:   122800 kB
VmallocUsed:      7936 kB
VmallocChunk:   113580 kB

---

### Post by nocturn on 2005-06-10
Are you running the 386 kernel?  If so, switch to one that is suited to your processor (K7, 686), this will enable highmem.

If you have this issue on a K7/686/... kernel, there is a boot option to specify the amount of memory you have in case it is not autodetected.

adding the mem=1536m as a bootparameter should do it.

---

### Post by DaturaX on 2005-06-10
Thanks! found that I was running the i386 kernel which is the default kernel for ubuntu.

---

### Post by landcross12 on 2005-06-11
I have the same problem only 1 gig of ram instead of 1.5 gig. I am new to Linux how do I change to the  K7/686/... kernel, or use the boot option to specify the amount of memory.

any help appreciated

---

