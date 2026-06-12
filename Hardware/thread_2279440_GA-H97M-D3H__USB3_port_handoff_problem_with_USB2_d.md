---
title: "GA-H97M-D3H  USB3 port handoff problem with USB2 devices"
date: 2015-05-23
forum: Hardware
---

### Post by afremont on 2015-05-23
I'm having some stupid user problems with USB3 ports and USB2 devices.  When I plug a USB3 external HDD into a USB3 port, it works great.  It connects at USB3 speeds and no issues.  When I plug a USB2 flash drive into the same port (or any other USB3 port), nothing happens.  dmesg doesn't show anything happening at all.  

I did some digging first, but I can't find a solution within all the Google noise.  I don't seem to have an IOMMU setting in the BIOS.  I've tried various machinations of XHCI and EHCI handoff as well as changing the Legacy USB setting and XHCI mode setting.  I admit that I haven't tried all possible combinations of the settings, but I've tried a few of them.  An idea what I need to do to overcome this minor issue?  All suggestions welcome.  Thanks.

---

### Post by afremont on 2015-05-25
Anyone?  Any ideas at all are welcome?

---

