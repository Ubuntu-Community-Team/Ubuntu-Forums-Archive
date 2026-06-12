---
title: "Where are my 4GB of RAM?"
date: 2005-03-08
forum: Hardware &amp; Laptops
---

### Post by GilGalad on 2005-03-08
Hi,

I have a PC with 4GB of RAM and I am using the 2.6.10-4-686 kernel with highmem support. However the ouput of 'free' does not report 4GB:

$ free
             total       used       free     shared    buffers     cached
Mem:       3245128     721368    2523760          0      29236     527344
-/+ buffers/cache:     164788    3080340
Swap:      2931820          0    2931820

So there are 800MB missing? Is this normal? :-?

---

### Post by alastair on 2005-03-08
Not sure - what about :

cat /proc/meminfo

---

### Post by GilGalad on 2005-03-09
$ cat /proc/meminfo
MemTotal:      3245128 kB
MemFree:       2186784 kB
Buffers:        121528 kB
Cached:         504888 kB
SwapCached:          0 kB
Active:         411840 kB
Inactive:       423240 kB
HighTotal:     2357436 kB
HighFree:      1635264 kB
LowTotal:       887692 kB
LowFree:        551520 kB
SwapTotal:     2931820 kB
SwapFree:      2931820 kB
Dirty:             344 kB
Writeback:           0 kB
Mapped:         263380 kB
Slab:           204132 kB
CommitLimit:   4554384 kB
Committed_AS:   666304 kB
PageTables:       2268 kB
VmallocTotal:   114680 kB
VmallocUsed:     45196 kB
VmallocChunk:    68084 kB

---

### Post by GilGalad on 2005-03-09
I am going to recmopile the kernel with 64GB of high mem support and see...

---

### Post by GilGalad on 2005-03-09
Compiled with 64Gb support just in case and HIGHPTE but no luck, same result. Any ideas anyone?

---

