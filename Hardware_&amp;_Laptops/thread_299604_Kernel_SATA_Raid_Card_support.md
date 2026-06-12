---
title: "Kernel SATA Raid Card support"
date: 2006-11-14
forum: Hardware &amp; Laptops
---

### Post by Incroyable HULK on 2006-11-14
I'm a bit confused. :-? 

How do I know if a card is directly (natively) supported by the Linux Kernel. I mean a built-in driver so I can install Ubuntu Server right on top of a RAID5 array WITHOUT doing anything special during setup. :-k 

I've narrowed my selection to the following FULL HARDWARE cards:

**PCI-X:**
LSI MegaRAID SATA 300-8X
3ware 9550SX-8LP

**PCI-Express:**
LSI MegaRAID SATA 300-8ELP
3ware 9590 SE

On the 3ware website they mention that the 9550 SX Series are supported right out of the box if the Kernel is at least v2.6.14 but no information about the 9590 series...

How About LSI? I can't find good info on their website...


---------------------------------------------------------

**Another thing. If the above doesn't work natively, what are my options?**

Is it possible to install to a temporary hard drive and then make the raid array available and then copy the whole system to the array (and removing completely the temporary drive)?

Thanks!

P.S. this card will be installed on a recent Dual-Core Xeon Server with an Intel 5000X chipset on a Tyan Motherboard (S2692ANR)

---------------------------------------------------------

---

