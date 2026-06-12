---
title: "Will I have any problems with new mobo?"
date: 2007-08-20
forum: Hardware &amp; Laptops
---

### Post by kipman725 on 2007-08-20
Hello I am planning to replace my motherboard as my current one is been an absolute pain with acpi (have to turn it off) and AGP GART settings only half working.  When replacing my motherboard do I need to do anything special or do I just take the old one out and power up into ubuntu again?

Also which 754 chipsets are best with linux? Nforce 3, 4, VIA etc? (not using SIS again)
(I will be buying off ebay so I don't know what board I will get till the last moment)

---

### Post by logos34 on 2007-08-20
nvidia works great with linux.

If you want to use that AGP card, you'll have to go with a nforce3-based board or maybe a VIA K8M800 series (nforce4 754 socket boards are all PCI-Express x 16)

I would say there's a good chance the new board will work right off the bat (it's not like you're switching platforms).  Same amd cpu and video card, ram the whole bit just swapped out.  But things like ethernet or storage controllers (from SiS to nvidia or VIA) might give you a problem--might have to do modprobe for forcedeth (nvidia network driver) or the pata and sata controller(s).

---

