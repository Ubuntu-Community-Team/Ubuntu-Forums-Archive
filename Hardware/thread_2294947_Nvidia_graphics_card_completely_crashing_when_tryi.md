---
title: "Nvidia graphics card completely crashing when trying to launch Minecraft."
date: 2015-09-14
forum: Hardware
---

### Post by Reece_Morgan on 2015-09-14
My graphics card is completely crashing when trying to launch Minecraft.
I am not able to provide any kind of error message, as everything completely stops so I can't see one. I am rather convinced however that it's an LWJGL error from what I've read.

As a note, this is not crashing my entire computer, only the graphics card (since I can still hear my music playing).
Here is the output to some useful commands :

```

lspci | grep VGA:

01:00.0 VGA compatible controller: NVIDIA Corporation GK107 [GeForce GT 640 OEM] (rev a1)

```
```

sudo lshw -C video:

  *-display               
       description: VGA compatible controller
       product: GK107 [GeForce GT 640 OEM]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:45 memory:f6000000-f6ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:f7000000-f707ffff

```

I am using the 'xserver-xorg-video-nouveau'  non-proprietary graphics driver.

Thank you :)

---

### Post by brian-mccumber on 2015-09-14
I switched the drivers for my gt610 in my desktop to the tested Nvidia drivers for it under additional drivers in software and updates and I play Minecraft with no problem. In fact I am playing it right now. Maybe you could try to use the Nvidia drivers for your graphics card model.

---

