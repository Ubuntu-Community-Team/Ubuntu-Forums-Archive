---
title: "&quot;free -m&quot; and &quot;/proc/mtrr&quot; what are the differences?"
date: 2008-12-26
forum: Hardware
---

### Post by CoffeeBreath on 2008-12-26
```
reg00: base=0xfeda0000 (4077MB), size= 128KB: write-back, count=1
reg01: base=0xbf800000 (3064MB), size=   8MB: uncachable, count=1
reg02: base=0xffe00000 (4094MB), size=   2MB: write-protect, count=1
reg03: base=0x00000000 (   0MB), size=2048MB: write-back, count=1
reg04: base=0x80000000 (2048MB), size=1024MB: write-back, count=1
reg05: base=0xe0000000 (3584MB), size= 256MB: write-combining, count=1
```


free -m
```
             total       used       free     shared    buffers     cached
Mem:          3008       1282       1725          0         37        388
-/+ buffers/cache:        856       2152
Swap:         4604          0       4604

```

---

