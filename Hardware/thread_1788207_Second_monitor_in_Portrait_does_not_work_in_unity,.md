---
title: "Second monitor in Portrait does not work in unity, but does in unity-2d"
date: 2011-06-22
forum: Hardware
---

### Post by RMKrug on 2011-06-22
Hi

I have a notebook (1680x1050) with attached second monitor (1440x900), standard settings. When using Maverick, I used the monitor in vertice (portrait) mode, but I switched to horizontal (panorama) before upgrading to Natty. I upgraded to Natty (Unity), and wanted to switch back to vertical, so I switched the second monitor to rotate right in the monitor applet, but the second monitor was completely scrambled (I saw the mouse though clearly, when moving into the second monitor).

Changing the seeting under unity-2d, does work and I get the portrait screen, but I would like to use unity. The same problem is with kde. Fluxbox works fine. My guess is that it has to do with the comopositing, and when I execute 

```
compiz --replace
```

under unity-2d, the monitor becomes scrambled again.

Below is the output from lshw concerning the graphic card.

I would really like to be able to change the orientation from my seciond monitor again under unity...

Any ideas?

Rainer
```
-display
                description: VGA compatible controller
                product: M56P [Radeon Mobility X1600]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:45 memory:e0000000-efffffff ioport:4000(size=256) memory:f4600000-f460ffff memory:f4620000-f463ffff

```

---

