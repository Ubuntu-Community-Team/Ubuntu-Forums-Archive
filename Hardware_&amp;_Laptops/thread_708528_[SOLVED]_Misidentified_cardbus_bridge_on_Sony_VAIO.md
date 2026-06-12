---
title: "[SOLVED] Misidentified cardbus bridge on Sony VAIO PCG-Z505LSK"
date: 2008-02-26
forum: Hardware &amp; Laptops
---

### Post by chris_acheson on 2008-02-26
Around the time I upgraded from Feisty to Gutsy (or perhaps sometime after, not sure exactly), the PCMCIA slot on my laptop stopped working.  Here's the relevant line from lspci -nn:

```
00:0c.0 Cardbus bridge [0607]: Jazz Multimedia Unknown device [1100:0475]
```

I think it's a Ricoh RL5c475, so the vendor ID should be 1180.  I tried updating /usr/share/misc/pci.ids from pciids.sourceforge.net, but it didn't change anything.  Anyone have any idea why this is happening?

---

### Post by chris_acheson on 2008-03-01
Bump.  Anyone?

---

### Post by chris_acheson on 2008-03-02
After further investigation, it seems that the cardbus bridge is just dead.  :-(

---

