---
title: "Ubuntu 12.04 with nvidia geforce CUDA and amd radeon graphic card"
date: 2014-02-05
forum: Hardware
---

### Post by erotavlas on 2014-02-05
Hi,

I have bought a computer with nvidia geforce with CUDA capabilities 5.5. I want to start to write program in CUDA under Ubuntu 12.04. I figure out that during the debugging the operating system locks the nvidia geforce and I'm not able to see any image on screen until the operation is completed. For this reason I tried to add a second graphic card to my system. The problem is that I'm obligated to leave the nvidia card in the first slot of motherboard a due dimension constraint of my case. The second amd card is in other slot. Ubuntu is only able to recognize the nvidia card. How can I do to set the amd card as first device to show the screen and to use the nvidia card only for programming?

Thank you

P.S.
```

lshw -C video
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: GK110 [GeForce GTX Titan]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:fa000000-faffffff memory:f0000000-f7ffffff memory:f8000000-f9ffffff ioport:e000(size=128) memory:fb000000-fb07ffff

```

---

