---
title: "Can't access new HDD via new PCIe SATA card"
date: 2016-12-29
forum: Hardware
---

### Post by jonthomas83 on 2016-12-29
I've got two new PCIe SATA controller cards installed, one with 2 ports and the other with 4 so I can fit more hard drives into my home media server. I'm using Ubuntu server 14.04.2 and I have 10 hard drives installed currently, but they all are directly connected to the motherboard SATA ports and work fine. I would like another 6 but they need to be attached to PCIe SATA ports as the motherboard has no more ports available.

The new disk does not show up in Webmin and after running 'sudo lsh -C disk' I can't see the new disk listed in there either.

Could anyone spare a moment to help me please? Many thanks

The PCIe cards I'm using are as follows...
StarTech.com 4 Port PCI Express 2.0 SATA III 6Gbps RAID Controller Card with HyperDuo SSD Tiering - PCIe SATA 3 Controller Adapter
and
StarTech.com 2 Port SATA 6 Gbps PCI Express SATA Controller Card - Dual Port PCIe SATA III Card Adapter

I've tried the new disk attached to both and it doesn't show up. 

Many thanks
Jonathan

---

### Post by fixitmr on 2016-12-29
I'm just starting with linux ... but I think you need drives for the two card you purchased ...
go look at the starttech wweb site they may have some thing there ...

---

### Post by Keith_Helms on 2016-12-30
Is Linux recognizing the 2 PCIe SATA controller cards?  What does _lspci -v_ show for them?  Is there a kernel driver in use for them?

---

