---
title: "memory problems with Intel DG45ID"
date: 2009-01-31
forum: Installation &amp; Upgrades
---

### Post by dbsears on 2009-01-31
I recently got a new system with an Intel DG45ID motherboard and 4GB of memory. My problem is that the BIOS sees all 4GB of memory while top(1) only sees 3GB.

I've updated the BIOS to the most recent version (89), I've run memtest86+ and I'm running Ubuntu 8.10 w/ the latest updates.

What am I missing, other than 1GB of memory?

--Dan

---

### Post by lemming465 on 2009-02-01
The default 32-bit desktop kernel isn't likely to expose more than 3GB to the end-user applications.  You may need to recompile a custom 32-bit kernel with different memory options, or reinstall with a 64-bit version.  The memory isn't necessarily completely missing, but only the kernel would be using it, and the kernel doesn't actually want that much.  What does *cat /proc/meminfo* show?  It's also possible that your BIOS isn't reporting correctly to Linux, in which case booting with a mem=4g option might improve things.

---

### Post by dbsears on 2009-02-04
Thanks, that makes sense. Here's the output:

--Dan

$ cat /proc/meminfo
MemTotal:      3074088 kB
MemFree:       1873020 kB
Buffers:        184716 kB
Cached:         462764 kB
SwapCached:          0 kB
Active:         566628 kB
Inactive:       408584 kB
HighTotal:     2189860 kB
HighFree:      1386220 kB
LowTotal:       884228 kB
LowFree:        486800 kB
SwapTotal:     9004392 kB
SwapFree:      9004392 kB
Dirty:             100 kB
Writeback:           0 kB
AnonPages:      327880 kB
Mapped:          87696 kB
Slab:           122456 kB
SReclaimable:   105904 kB
SUnreclaim:      16552 kB
PageTables:       3176 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
WritebackTmp:        0 kB
CommitLimit:  10541436 kB
Committed_AS:   764524 kB
VmallocTotal:   110584 kB
VmallocUsed:     16832 kB
VmallocChunk:    93600 kB
HugePages_Total:     0
HugePages_Free:      0
HugePages_Rsvd:      0
HugePages_Surp:      0
Hugepagesize:     4096 kB
DirectMap4k:     90112 kB
DirectMap4M:    827392 kB

---

### Post by lemming465 on 2009-02-09
Ok, your 4 GiB system says *MemTotal: 3074088 kB* whereas mine (64-bit, admittedly) says *MemTotal: 4055188 kB*.  Try the boot option and see if that makes a difference, or maybe check for a BIOS update.  It would be interesting to see what a live 64-bit CD said, too.

---

