---
title: "Question of RAM"
date: 2011-06-13
forum: Hardware
---

### Post by fleamour on 2011-06-13
```
cat /proc/meminfo
```
Returns:
```

MemTotal:         508000 kB
MemFree:          173352 kB
Buffers:           36324 kB
Cached:           174196 kB
SwapCached:            0 kB
Active:           132332 kB
Inactive:         170656 kB
Active(anon):      93172 kB
Inactive(anon):     2340 kB
Active(file):      39160 kB
Inactive(file):   168316 kB
Unevictable:           0 kB
Mlocked:               0 kB
HighTotal:             0 kB
HighFree:              0 kB
LowTotal:         508000 kB
LowFree:          173352 kB
SwapTotal:        500732 kB
SwapFree:         500732 kB
Dirty:               424 kB
Writeback:             0 kB
AnonPages:         92480 kB
Mapped:            44432 kB
Shmem:              3052 kB
Slab:              17712 kB
SReclaimable:       9792 kB
SUnreclaim:         7920 kB
KernelStack:        1832 kB
PageTables:         3820 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:      754732 kB
Committed_AS:     491432 kB
VmallocTotal:     507960 kB
VmallocUsed:        7380 kB
VmallocChunk:     495612 kB
HardwareCorrupted:     0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       4096 kB
DirectMap4k:       49088 kB
DirectMap4M:      475136 kB

```

Just installed some new KingSpec modules.  Is the full 512MB being recognised as it seems to list a little less?  I guess there is a reason for this, like when Windows allocates/reserves some memory for the graphics card, etc... 

Thanks for taking time to explain.

Yours ever learning

fleamour

---

### Post by Yellow Pasque on 2011-06-13
> MemTotal:         508000 kB
Just about 512MB and the missing memory is probably due to integrated video using it as VRAM.

---

