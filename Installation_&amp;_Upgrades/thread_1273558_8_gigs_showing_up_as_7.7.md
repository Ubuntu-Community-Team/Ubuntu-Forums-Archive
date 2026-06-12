---
title: "8 gigs showing up as 7.7"
date: 2009-09-23
forum: Installation &amp; Upgrades
---

### Post by TheOneEyedMan on 2009-09-23
I just upgraded my 64 bit 9.04/ Jaunty setup to have a new processor, motherboard, and memory. I installed 4 2 gig DIMMs, which shows up in BIOS as 8192M of memory. However, various programs within Ubuntu show different amounts of memory present. Can someone explain what is going on and if something is wrong, how to fix it? 
Much obliged,
TOEM

When I run the free -m to show how much memory I have I get:
             total       used       free     shared    buffers     cached
Mem:          7893       1186       6707          0         24        420
-/+ buffers/cache:        740       7152
Swap:            0          0          0


When I look in system monitor I get memory used shown as a fraction o 7.7 Gigs.

When I run cat /proc/meminfo I get pretty different info:
MemTotal:        8083392 kB
MemFree:         6863280 kB
Buffers:           25212 kB
Cached:           430244 kB
SwapCached:            0 kB
Active:           829380 kB
Inactive:         270644 kB
Active(anon):     652356 kB
Inactive(anon):        8 kB
Active(file):     177024 kB
Inactive(file):   270636 kB
Unevictable:           8 kB
Mlocked:               8 kB
SwapTotal:             0 kB
SwapFree:              0 kB
Dirty:              3876 kB
Writeback:             0 kB
AnonPages:        644572 kB
Mapped:           122688 kB
Slab:              55996 kB
SReclaimable:      39316 kB
SUnreclaim:        16680 kB
PageTables:        21728 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     4041696 kB
Committed_AS:    1379080 kB
VmallocTotal:   34359738367 kB
VmallocUsed:      296912 kB
VmallocChunk:   34359431163 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:       34368 kB
DirectMap2M:     8353792 kB

---

### Post by doas777 on 2009-09-23
sounds like somthing is getting lost in the gb to gib conversion.

all my 1TB hdds show as 931MB

---

### Post by earthpigg on 2009-09-23
my 6gb shows up as:

```
[chris: ~]$ f
             total       used       free     shared    buffers     cached
Mem:          5953       4566       1386          0        254       3571
-/+ buffers/cache:        739       5213
Swap:            0          0          0
[chris: ~]$ 

```

normal. 

humans count one way.
computers count another.

marketing departments use the method that will make their products look the biggest and baddest without actually having to pay them to be the biggest and baddest.

this method is the industry standard -- all manufacturers do it.

---

### Post by TheOneEyedMan on 2009-09-23
Perfect. Thanks for setting my mind at ease.

---

### Post by earthpigg on 2009-09-23
yup, and the bigger the device is the bigger the difference between the advertised value and the actual value.

---

### Post by gordintoronto on 2009-09-23
However, RAM uses different math from hard drives.  8 GB of RAM is always more than 8,000,000,000 bytes.

It seems likely that the built-in video adapter has grabbed some of the RAM before allowing Ubuntu to load.

---

### Post by TheOneEyedMan on 2009-09-23
I thought that might have been the problem so I went into BIOS before I posted this and turned off the on-board video. It didn't change anything.

---

