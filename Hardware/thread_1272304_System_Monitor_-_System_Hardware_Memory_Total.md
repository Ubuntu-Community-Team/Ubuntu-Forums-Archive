---
title: "System Monitor - System Hardware Memory Total"
date: 2009-09-22
forum: Hardware
---

### Post by Rab22 on 2009-09-22
I don't often look at the system monitor, and when I do I normally look at the Processes or Resources tabs.  Tonight though, I noticed that the System tab is showing that I have 1.9GiB.

I'm a bit confused as I would have thought I would have had 2.048GiB or 2GB, not 1.9 GiB/GB.

All the same I guess :)

---

### Post by Rab22 on 2009-09-22
It appears it is correctly getting this data from /proc/meminfo 

```

MemTotal:        2033696 kB
MemFree:          619028 kB
Buffers:          121648 kB
Cached:           608764 kB
SwapCached:            0 kB
Active:           836300 kB
Inactive:         431644 kB
Active(anon):     541192 kB
Inactive(anon):     2992 kB
Active(file):     295108 kB
Inactive(file):   428652 kB
Unevictable:           8 kB
Mlocked:               8 kB
SwapTotal:       2441840 kB
SwapFree:        2441840 kB
Dirty:               268 kB
Writeback:             0 kB
AnonPages:        537568 kB
Mapped:           108640 kB
Slab:              86180 kB
SReclaimable:      70588 kB
SUnreclaim:        15592 kB
PageTables:        19692 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     3458688 kB
Committed_AS:    1066312 kB
VmallocTotal:   34359738367 kB
VmallocUsed:      101060 kB
VmallocChunk:   34359628283 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:      344960 kB
DirectMap2M:     1751040 kB
```

If my math is correct, 2033696kB should be 1.9GiB (rounded).

Must be right :)

---

