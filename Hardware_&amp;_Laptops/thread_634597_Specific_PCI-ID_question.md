---
title: "Specific PCI-ID question"
date: 2007-12-07
forum: Hardware &amp; Laptops
---

### Post by MoebusNet on 2007-12-07
My question is about the pci.product_id of my video card. Here is what Device Manager claims I have:

pci.product                        string  NV34 [Geforce FX 5200]
pci.product_id                   int        802 (0x322)
pci.subsys_product_id     int        45833 (0xb309)
pci.subsys_vendor          string   eVga.com. Corp.
pci.subsys_vendor_id     int        14402 (0x3842)
pci.vendor                        string   nVidia Corporation
pci.vendor_id                   int        4318 (0x10de)

When I go to the supported products list at 

[http://www.nvidia.com/object/IO_18897.htm](http://www.nvidia.com/object/IO_18897.htm)

the closest thing i can find is:

GeForce FX 5200 	0x0322

My question is: will the difference in the pci.product_id give an error preventing the nvidia-glx-new driver from working? (because it doesn't) (Notice the 0 in 0x0322)

We all know how literal computers are....

---

