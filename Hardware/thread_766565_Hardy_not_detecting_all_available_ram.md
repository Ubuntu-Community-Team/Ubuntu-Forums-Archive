---
title: "Hardy not detecting all available ram"
date: 2008-04-25
forum: Hardware
---

### Post by Omnutia on 2008-04-25
I've been enjoying the nightmare of upgrading and have got just about everything sorted except that while the BIOS and Windows both show 512mb of ram (as did Feisty), hardy is showing 437.11mB which is a 73mB loss.
As a result my system is churning the hard drive way too much. Any way to detect or force the real ram size?

---

### Post by PmDematagoda on 2008-04-25
Can you post the output of:-
```
free -m
```

---

### Post by bigken on 2008-04-25
are you sure graphics card is not using the ram (on board chip)

---

### Post by Omnutia on 2008-04-25
total       used       free     shared    buffers     cached
Mem:           437        431          5          0          0         46
-/+ buffers/cache:        384         52
Swap:         1992        201       1790

It could be the case of the graphics card though I don't think it was taking up this much before.
Oh no, artifacts!

---

### Post by Omnutia on 2008-04-26
After some looking around it seems not be so much about hardware. XP reports 450mb of ram. I have noticed that with no programs open I am using 260mb of ram which is worrying.

---

