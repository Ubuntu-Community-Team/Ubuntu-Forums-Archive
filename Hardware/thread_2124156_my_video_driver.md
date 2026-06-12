---
title: "my video driver"
date: 2013-03-10
forum: Hardware
---

### Post by tendouser on 2013-03-10
What is my video driver running in my Ubuntu 12.04?
I check in additional drivers but is to active the Nvidia driver but when I lshw it outputs 

*-display               
       description: VGA compatible controller
       product: G86 [Quadro NVS 140M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:d6000000-d6ffffff memory:e0000000-efffffff memory:d4000000-d5ffffff ioport:2000(size=128)

So it's xorg emulating Nvidia perhaps?

Cheers!

---

### Post by sudodus on 2013-03-10
If you check the OpenGL information, you should get the version number if you have a proprietary driver. You can use the GUI program ***hardinfo***. Select Display -- OpenGL

Maybe you need to install hardinfo
```
sudo apt-get install hardinfo
```

---

### Post by tendouser on 2013-03-10
yes it's x.org driver ...seems like it's emulating nvidia

---

### Post by sudodus on 2013-03-10
The built-in drivers that come with the kernel in the current Ubuntu versions are quite good, but if you want all the eye-candy and/or video playing power available, you should try the proprietary drivers for nvidia.

Usually it is enough to run ```
jockey-gtk
``` and select what is offered in its window.

---

