---
title: "Should I edit my mtrr configuration?"
date: 2008-12-27
forum: Hardware
---

### Post by CoffeeBreath on 2008-12-27
Hi
I haven't been able to get my 64bit kubuntu to recognise all four gigs of ram that I have. The free command only shows 2.9 gigs.

```
free
             total       used       free     shared    buffers     cached
Mem:       3080448    3040780      39668          0      37416    2338524
-/+ buffers/cache:     664840    2415608
Swap:      4715036       5248    4709788
```

I feel that the number 4077MB in /proc/mtrr is saying that kubuntu knows how much ram is there but is not using it because the "free" command seems to contradict it.

```
cat /proc/mtrr
reg00: base=0xfeda0000 (4077MB), size= 128KB: write-back, count=1
reg01: base=0xbf800000 (3064MB), size=   8MB: uncachable, count=1
reg02: base=0xffe00000 (4094MB), size=   2MB: write-protect, count=1
reg03: base=0x00000000 (   0MB), size=2048MB: write-back, count=1
reg04: base=0x80000000 (2048MB), size=1024MB: write-back, count=1
reg05: base=0xe0000000 (3584MB), size= 256MB: write-combining, count=1
```


1.Can someone explain to me in detail what /proc/mtrr is showing?
2. And should I edit it to use my last gig of ram?

the grub option mem=4096M does not work.

---

### Post by sdennie on 2008-12-27
See if you have a BIOS option like, "Map around memory hole".  That is sometimes needed to see all 4GB.

---

### Post by CoffeeBreath on 2008-12-27
> **vor said:**
> See if you have a BIOS option like, "Map around memory hole".  That is sometimes needed to see all 4GB.

That option is not in my bios.

---

