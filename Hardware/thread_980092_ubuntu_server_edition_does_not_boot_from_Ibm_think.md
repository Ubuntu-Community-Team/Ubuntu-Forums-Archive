---
title: "ubuntu server edition does not boot from Ibm thinkpad R30"
date: 2008-11-12
forum: Hardware
---

### Post by rkovvur on 2008-11-12
I have an IBM thinkpad R30 that i installed ubuntu server edition (latest one). Everything went fine until reboot. 

First my laptop does not reboot by itself. I'll have press the power switch to get it to reboot. 

Secondly, it just will not boot from the hard-disk. It says "operating system not found". Then i'll have to boot using the ubuntu CD and then load up the OS from the hard disk. 

This means that somehow GRUB is not being installed to the MBR of the hard disk. 

I initially suspected bad hard disk and bought a new one. But same problem. 

I am at my wits end with this issue and would appreciate any help !!

Thanks,

-Raj

---

### Post by prshah on 2008-11-12
> **rkovvur said:**
> 
This means that somehow GRUB is not being installed to the MBR of the hard disk. 

Make sure you have "virus protection" turned off in the BIOS; in some cases, this option prevents MBR code from being modified. You can turn it back on after the installation if you like.

---

