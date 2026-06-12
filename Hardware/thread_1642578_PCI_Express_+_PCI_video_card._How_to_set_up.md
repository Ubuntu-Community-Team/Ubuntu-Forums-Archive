---
title: "PCI Express + PCI video card. How to set up?"
date: 2010-12-10
forum: Hardware
---

### Post by ipartola on 2010-12-10
I was running two monitors off of an ATI Technologies Inc Mobility Radeon HD 3470 (PCI Express). I just added a second video card through a PCI slot. This one is an nVidia Corporation NV18 [GeForce4 MX 4000]. I am trying to add a third monitor through this video card. lspci can see this card:

```
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3470
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8057 PCI-E Gigabit Ethernet Controller (rev 10)
04:04.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 4000] (rev c1)
```

How do I configure xorg to see it as well?

---

