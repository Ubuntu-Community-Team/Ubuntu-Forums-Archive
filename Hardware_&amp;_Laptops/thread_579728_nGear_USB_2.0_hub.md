---
title: "nGear USB 2.0 hub"
date: 2007-10-18
forum: Hardware &amp; Laptops
---

### Post by yamla on 2007-10-18
I picked up an "nGear 7 Port USB2.0 Mini Hub Silver W/ Power Adapter", aka NG-7U2.  This is sold by ncix.com and directcanada.com and appears to be a generic brand, though I'm not sure.

The product was listed as being compatible with "Red Hat Linux9 KerneL 2.4.20~ (sic)".  This would not work in my computer system, Kubuntu 7.04 i386.

By default, Ubuntu appears to use ehci_hcd.  This conflicted with the USB hub.  I was getting the "error -71" problem which a few people have run into.  If I add the following line to /etc/rc.local, the system is forced to use ohci_hcd which solves the problem:

# Remove ehci_hcd which conflicts with nGear USB hub
/sbin/modprobe -r ehci_hcd

I tried adding ehci_hcd to /etc/modprobe.d/blacklist but this did not prevent ehci_hcd from loading on subsequent boot.

Hopefully this information will be useful to others.

---

