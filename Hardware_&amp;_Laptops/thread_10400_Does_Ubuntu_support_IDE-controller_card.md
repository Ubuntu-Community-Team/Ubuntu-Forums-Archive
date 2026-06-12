---
title: "Does Ubuntu support IDE-controller card"
date: 2005-01-07
forum: Hardware &amp; Laptops
---

### Post by BORTKOMMEN on 2005-01-07
I have an IDE controller card IT8212 ATAPI Bios V1.4.1.2 . Can Ubuntu recognize it and are there Linux drivers available. I have RAID disabled and use the disk 160 GB connected to the card as a mass storage,

---

### Post by wallijonn on 2005-01-07
You may be out of luck:

[http://www.passys.nl/tips/ite_kernel_image_compile.txt](http://www.passys.nl/tips/ite_kernel_image_compile.txt) : > WARNING!!! Linux Kernel 2.6.10 does NOT work with the standard ITE IT8212 driver that's available on ITE's website. The Linux kernel has changed from version 2.5.x/2.6.x in the way kernel modules are managed. If you still want to compile this module on Kernel 2.6.10, then use Alan Cox's kernel sources (the -ac kernel). Alan expects to have this module in the standard linux kernel from version 2.6.11. Also, in this version, the raid controller doesn't work anymore on scsi-emulation, but as a true IDE/ATA device.  

So it would seem that it will not work on Warty. Your best bet may be to install Hoardy, but that entails a lot more work.

---

### Post by BORTKOMMEN on 2005-12-21
I am back again because I now have Breezy installed with kernel 2.6.12.

Does Ubuntu support the controller card now, I do not use the card as raid only to get access to the hard drives connected.

---

