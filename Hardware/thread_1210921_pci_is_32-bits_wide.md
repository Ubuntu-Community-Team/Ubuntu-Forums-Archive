---
title: "pci is 32-bits wide?"
date: 2009-07-12
forum: Hardware
---

### Post by nmaster on 2009-07-12
I guess when it comes to my laptop I don't usually care much about my hardware unless I have a problem, but I was just looking at 'lshw' and noticed the following:

```

     *-pci
          description: Host bridge
          product: Mobile PM965/GM965/GL960 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp


```
A lot of my hardware seems to have a width of 32-bits even though I have a 64-bit processor...  Could someone explain this to me?

---

### Post by nmaster on 2009-07-19
bump.  anyone offer an explanation?

---

### Post by tgalati4 on 2009-07-20
Legacy support.  ISA busses are 8 and 16 bit wide.  You would need to upgrade your motherboard to get 64-bit expansion slots.

Your machine probably has 64 bit data paths between RAM and the CPU. If not, then it takes 2 clock  cycles to load each 64-bit word into the CPU.

Because of the long history of intel and the x86 architecture, you will see a lot of performance compromises to maintain compatibility.  Hence your 32-bit motherboard can interface with a 64-bit processor.

---

### Post by nmaster on 2009-07-21
thanks for the info.

---

