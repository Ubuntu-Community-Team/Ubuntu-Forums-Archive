---
title: "Odd memory mismatch in dmesg/free"
date: 2007-05-16
forum: Hardware &amp; Laptops
---

### Post by billybofh on 2007-05-16
Hi,

I've got a desktop system with 3gig of RAM.  The BIOS sees the 3gig fine.  When I run free or cat /proc/meminfo I was only seeing 2gig however.  I noticed in dmesg the following :

```


[    0.000000] 3200MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.

...

[   27.304791] Memory: 2051008k/4194304k available (1992k kernel code, 44344k re
served, 893k data, 328k init, 1179200k highmem)
[   27.304797] virtual kernel memory layout:
[   27.304798]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   27.304798]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   27.304799]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   27.304800]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   27.304801]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
[   27.304802]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
[   27.304802]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)

```

So it *looks* like it's seeing the 3gig but then only using 2?  

```


~$ cat /proc/meminfo 
MemTotal:      2059308 kB
MemFree:       1466404 kB
Buffers:         20172 kB
Cached:         356908 kB
SwapCached:          0 kB
Active:         337012 kB
Inactive:       208128 kB
HighTotal:     1179200 kB
HighFree:       641504 kB
LowTotal:       880108 kB
LowFree:        824900 kB
SwapTotal:     6032368 kB
SwapFree:      6032368 kB
Dirty:             228 kB
Writeback:           0 kB
AnonPages:      167964 kB
Mapped:          58584 kB
Slab:            27764 kB
SReclaimable:    14296 kB
SUnreclaim:      13468 kB
PageTables:       1920 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
CommitLimit:   7062020 kB
Committed_AS:   559140 kB
VmallocTotal:   114680 kB
VmallocUsed:     46604 kB
VmallocChunk:    67572 kB

```

This is running feisty 32bit, Core2Duo CPU.

---

