---
title: "why my 6200 NVIDIA only registers 66mhz clock?"
date: 2010-01-16
forum: Hardware
---

### Post by ayet on 2010-01-16
using sudo lshw -C video
monufacturers site says 350Mhz

 *-display UNCLAIMED     
       description: VGA compatible controller
       product: NV44A [GeForce 6200]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 vga_controller bus_master cap_list
       configuration: latency=32 maxlatency=1 mingnt=5

---

### Post by ayet on 2010-01-27
any ideas?

---

### Post by Yellow Pasque on 2010-01-27
It is probably the base clock speed, which is multiplied to get the speed of the GPU. Do not worry about it.

---

### Post by cascade9 on 2010-01-27
Because thats not the core speed of the GPU (where nVidia says 350Mhz), its the interface clock. 

> clock- bus clock (in Hz) of the device

[http://ezix.org/project/wiki/HardwareLiSter](http://ezix.org/project/wiki/HardwareLiSter)

---

