---
title: "laptop screen(s)"
date: 2019-04-23
forum: Hardware
---

### Post by tsollie on 2019-04-23
I (finally) installed [lubuntu]("http://www.lubuntu.me/") on my work laptop. A Lenovo ThinkPad with docking station and multiple screens.
After install I ran ubuntu-drivers autoinstall, got Nvidia drivers and my external screens work as planned.
However, when I started up the laptop at home (no docking) it starts up nicely, but when X get started I only have a black screen.
Any suggestions ho I can get it to work with and without docking station ???

---

### Post by mörgæs on 2019-04-23
You probably didn't know but the page you linked to is causing the Lubuntu community a lot of problems. It's a one-man show out of touch with the community and its effort to develop and improve Lubuntu.

The Lubuntu developers would be happy if you could edit the post and link to [www.lubuntu.me](www.lubuntu.me) in stead.

---

### Post by tsollie on 2019-04-24
Thnx. Changed it, and true, didn't know that bit

---

### Post by mörgæs on 2019-04-24
Thanks for the edit.

Please copy ```
sudo lshw -C video > lshw.txt
``` to the command line, run it and post the contents of lshw.txt in CODE tags. It will show us more about your graphics processor.

---

### Post by tsollie on 2019-04-25
No problem ;) Here is the output :

```
  *-display
       description: 3D controller
       product: GM107GLM [Quadro M1200 Mobile]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:125 memory:eb000000-ebffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:d000(size=128) memory:ec000000-ec07ffff
  *-display
       description: VGA compatible controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       logical name: /dev/fb0
       version: 04
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom fb
       configuration: depth=32 driver=i915 latency=0 mode=1920x1080 visual=truecolor xres=1920 yres=1080
       resources: iomemory:2f0-2ef iomemory:2f0-2ef irq:126 memory:2ff2000000-2ff2ffffff memory:2fc0000000-2fcfffffff ioport:e000(size=64) memory:c0000-dffff



```

---

### Post by mörgæs on 2019-04-26
I don't know enough about dual graphics processors (Nvidia and Intel) so I'll leave the thread here for someone else to find. Good luck.

---

