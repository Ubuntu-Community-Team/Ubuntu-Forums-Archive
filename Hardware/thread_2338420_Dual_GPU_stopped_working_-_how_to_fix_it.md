---
title: "Dual GPU stopped working - how to fix it?"
date: 2016-09-28
forum: Hardware
---

### Post by lenn-art on 2016-09-28
My Sapphire Flex HD 6450 1GB DDR3 Dual DVI stopped working, suddenly. Only one screen is working, but i 've a dual screen setup.
The company does not provide linux-drivers, it worked always out of the box. 

Does someone have some advice for me what to do or where to look? A ISO is being downloaded to see if the card isn't broken. The LiveUSB always recognized both outputs.

sudo lshw -c video gives

```
*-display               
       description: VGA compatible controller
       product: Caicos [Radeon HD 6450/7450/8450 / R5 230 OEM]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:49 memory:d0000000-dfffffff memory:fea20000-fea3ffff ioport:e000(size=256) memory:fea00000-fea1ffff
```

---

### Post by lenn-art on 2016-09-28
Oh my .. i found the solution.

The monitor cable was released .. :-/ 
What a classic, dumb mistake :-)

---

