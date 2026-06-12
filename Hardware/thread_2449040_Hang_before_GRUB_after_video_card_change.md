---
title: "Hang before GRUB after video card change"
date: 2020-08-18
forum: Hardware
---

### Post by isaacmhelgens on 2020-08-18
I have a Dell Poweredge 2900 iii (dual Xeon x5460, 48GB RAM) that has been running fine as my home media server, except for laggy video from the the Radeon HD 8490 card I slapped in (which was an improvement over the onboard video, but not significantly so).

This server only has PCI-E x8 slots, no x16 slots.  Previous card was connected through an x16 to x8 adapter.  I found an HP OEM Nvidia GT730 that was x8 and needed no external power.  I swapped the HD 8490 for the Nvidia card which posts just fine, but at the point grub should load, whether I leave it alone or hold left shift to edit the entry, it just hangs.

Any assistance or ideas would be greatly appreciated.

Thank you!

Isaac

---

### Post by CelticWarrior on 2020-08-18
Welcome.

Nvidia cards need Nvidia proprietary drivers.

---

