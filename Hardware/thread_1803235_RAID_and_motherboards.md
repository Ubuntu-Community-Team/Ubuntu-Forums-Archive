---
title: "RAID and motherboards"
date: 2011-07-13
forum: Hardware
---

### Post by Neutronologist on 2011-07-13
[http://ark.intel.com/Product.aspx?id=50098](http://ark.intel.com/Product.aspx?id=50098)

On the specifications page for this bored, it says "RAID Configuration - 0,1,10,5". Does this mean the board has a built-in RAID controller, and that I won't have to go out and buy a PCI slot RAID controller?

How would I set it up? In the BIOS?

---

### Post by pjd99 on 2011-07-13
> **Neutronologist said:**
> 
On the specifications page for this bored, it says "RAID Configuration - 0,1,10,5". Does this mean the board has a built-in RAID controller, and that I won't have to go out and buy a PCI slot RAID controller?

Yes. Looks like it supports striping, mirroring, striped mirror and (n-1) parity.

Personally, I try to steer clear of hardware RAID controllers unless in an enterprise setting. I prefer Linux software RAID. If the hardware screws up, you don't have to find a controller that is compatible with the old one.

The controller on the mobo will either be set up in the BIOS, or (more likely) will have its own setup that can be entered after POST and before bootloader.

---

