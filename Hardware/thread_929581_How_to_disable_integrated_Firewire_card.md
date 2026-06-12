---
title: "How to disable integrated Firewire card"
date: 2008-09-25
forum: Hardware
---

### Post by krzysiek_wkw on 2008-09-25
Hi,
how can I disable integrated Firewire card (this is TexasInsturments), but not external FireWire (NEC).
If I blacklist kernel module I'll disable two cards.


Thanks,
Krzysiek.

---

### Post by IntuitiveNipple on 2008-09-25
The best way might be to write a udev rule keyed to the internal IEEE-1394 device that prevents it being configured as a device.

---

