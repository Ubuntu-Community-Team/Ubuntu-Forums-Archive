---
title: "NIC Broadcom AC 131 not properly detected"
date: 2006-10-13
forum: Hardware &amp; Laptops
---

### Post by keltorsori on 2006-10-13
Just picked up a new Shuttle SS31T. This has a SiS chipset and an onboard Broadcom AC 131 NIC. The Broadcom AC 131 shows up as SiS 190 Gigabit NIC, which it's not. I did notice it uses a SiS 190 ROM image for PXE booting though. Driver mismatch keeps it from working. I'm a bit of a newb to Linux, any suggestions? I've not seen anyone else using this NIC yet, but I assume (maybe wrongly) that other Broadcom drivers might work?

I didn't configure the NIC during install and now I only have my secondary NIC showing up in ifconfig. The Broadcom AC 131 shows up in the Device Manager, but again rather as a SiS 190 Gig-E. Would really like to get both NICs working as I'm short a PCI slot and need two for proxy. Thanks for any help

-eric

---

### Post by sumo2GO on 2007-05-25
Hi Eric,

we are also having problems with the Shuttle SS31T, we can boot from a live CD and install the OS to a IDE hard drive but the NIC and SATA are not recognised?

Do you have any tips on how to get the NIC and SATA devices working?

Regards,

Michael.

---

