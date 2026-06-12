---
title: "4G RAM on Thinkpad T61 at Gusty Tribe4?"
date: 2007-08-23
forum: Hardware &amp; Laptops
---

### Post by vixensjlin on 2007-08-23
Hello:

I just installed 4G ram on my T61(Nvidia/4965AGN)/Gusty tribe4, and see this, only 3098488k available.  Could it utilize all 4G ram, except what taken by video card?

[    0.000000] Warning only 4GB will be used.
[    0.000000] Use a PAE enabled kernel.
[    0.000000] 3200MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f6900
[    0.000000] Entering add_active_range(0, 0, 1048576) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->  1048576
.
.
.
[   14.186078] Memory: 3098488k/4194304k available (2010k kernel code, 44572k reserved, 917k data, 364k init, 2226880k
 highmem)

---

### Post by ddrichardson on 2007-08-24
Are tou running the 64bit version?

---

### Post by vixensjlin on 2007-08-26
No.  Why we need 64 bit to support only 4G Ram?

32 bit Linux can use PAE to support more than 4G ram
32 bit MS windows server also can support more than 4G ram.

I just don't know how to make sure my PAE is on.  Anybody can help?  Thanks!

---

### Post by tseliot on 2007-08-26
Maybe try installing the -server flavour of the kernel?

---

### Post by ddrichardson on 2007-08-26
Running a 64 bit version would have been my first choice unless there is a reason you need a 32 bit kernel. You're laptop brand is listed as having a 64 bit processor.

You haven't said what you have tried - other than the server versions, a custom kernel is needed.

PAE isn't as straight forward as letting you use all the memory beyond 4Gb btw - it can be quite application specific and although I don't know much about it I would imagine that any kind of address translation is going to carry a performance overhead.

---

### Post by Dark Star on 2007-08-26
hehe 32b it did not support 4 Gb + ram so install 64 bit/.. even 32 bit vista cannot install 4 gig ram .. That's it ;)

---

### Post by tseliot on 2007-08-26
> **Dark Star said:**
> hehe 32b it did not support 4 Gb + ram so install 64 bit/.. even 32 bit vista cannot install 4 gig ram .. That's it ;)

if you recompile your kernel you can have more than 4GB in a 32bit system.

---

### Post by Dark Star on 2007-08-26
> **tseliot said:**
> if you recompile your kernel you can have more than 4GB in a 32bit system.
Any guide on compiling Linux kernel ? :?

---

### Post by pyre on 2007-08-26
It even says in Lenovo's specs that you can use up to 3GB without a 64-bit operating system, but the hardware supports up to 4GB.

---

### Post by vixensjlin on 2007-09-10
Here is the dmesg of AM64/Tribe5, no PAE message found.

[   15.032195] Memory: 3978304k/5177344k available (2278k kernel code, 148708k reserved, 1185k data, 300k init)

cat /proc/meminfo
MemTotal:      3985796 kB
MemFree:       3105516 kB
Buffers:         73900 kB
Cached:         411624 kB
SwapCached:          0 kB
Active:         498148 kB
Inactive:       275556 kB
SwapTotal:     2638400 kB
SwapFree:      2638400 kB
Dirty:             348 kB
Writeback:           0 kB
AnonPages:      288280 kB
Mapped:          71996 kB
Slab:            57756 kB
SReclaimable:    37328 kB
SUnreclaim:      20428 kB
PageTables:      14176 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
CommitLimit:   4631296 kB
Committed_AS:   588720 kB
VmallocTotal: 34359738367 kB
VmallocUsed:     22420 kB
VmallocChunk: 34359715691 kB

---

