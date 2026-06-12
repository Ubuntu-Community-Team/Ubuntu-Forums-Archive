---
title: "Nvidia Geforce FX 5200 running on PCI bus"
date: 2007-12-30
forum: Hardware &amp; Laptops
---

### Post by coffee on 2007-12-30
I have a AGP Nvidia Geforce FX 5200 graphics card in my box.  I was digging around my system today, during some down time on Christmas vacation from work, and noticed that it is running on the PCI bus.  why is it not running on my AGP bus.  Not sure just wondering since the AGP bus is supposed to be faster.  

Is there a way to switch it over or is this just the way the AGP bus is handled in Ubuntu?

---

### Post by kyphi on 2007-12-30
The AGP bus is an improved PCI bus.

On your motherboard, unless it is very old, there is a slot reserved for AGP (Accelerated Graphics Port).  This is more direct in its connection to the CPU than the PCI (Peripheral Component Interconnect) and therefore faster.

The new standard is PCIe which is faster still.

There is no need to change anything.

---

### Post by coffee on 2007-12-30
Thanks for the info

---

