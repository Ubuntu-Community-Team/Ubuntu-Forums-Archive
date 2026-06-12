---
title: "eGPU for additional compute power"
date: 2020-12-09
forum: Hardware
---

### Post by kruemelprinz on 2020-12-09
Hi
I am running ubuntu studio 20.10 on a Dell precision 5540 laptop. Although quite beefy speced, the laptop struggles to play 4K video with some effects applied in realtime while editing in Davinci Resolve.
Davinci Resolve has the feature to utilize multiple GPUs at the same time and distribute the workload between them. Thus I headed out and got a Blackmagic eGPU which is basically a thunderbolt 3 enclosure with an AMD RX580 graphics card in it.
The laptop itself has an Intel integrated graphics card and a dGPU Nvidia Quadro T2000. Per default, I am running on the nvidia dGPU.

After attaching and authorizing the eGPU it is recognized under "Thunderbolt" in system settings and properly recognized by the system. All 3 GPUs are listed by lshw.

```

[FONT=monospace][COLOR=#000000]sudo lshw -c video [/COLOR]
  *-display                  
       description: 3D controller 
       product: TU117GLM [Quadro T2000 Mobile / Max-Q] 
       vendor: NVIDIA Corporation 
       physical id: 0 
       bus info: pci@0000:01:00.0 
       version: a1 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list rom 
       configuration: driver=nvidia latency=0 
       resources: irq:172 memory:ec000000-ecffffff memory:c0000000-cfffffff 
memory:d0000000-d1ffffff ioport:3000(size=128) memory:ed000000-ed07ffff 
  *-display 
       description: VGA compatible controller 
       product: UHD Graphics 630 (Mobile) 
       vendor: Intel Corporation 
       physical id: 2 
       bus info: pci@0000:00:02.0 
       version: 02 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pciexpress msi pm vga_controller bus_master cap_list ro
m 
       configuration: driver=i915 latency=0 
       resources: irq:151 memory:eb000000-ebffffff memory:80000000-8fffffff 
ioport:4000(size=64) memory:c0000-dffff 
  *-display UNCLAIMED 
       description: VGA compatible controller 
       product: Ellesmere [Radeon RX 470/480/570/570X/580/580X/590] 
       vendor: Advanced Micro Devices, Inc. [AMD/ATI] 
       physical id: 0 
       bus info: pci@0000:07:00.0 
       version: c0 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm pciexpress msi vga_controller cap_list 
       configuration: latency=0 
       resources: memory:90000000-9fffffff memory:a0000000-a01fffff ioport:5
000(size=256) memory:d4000000-d403ffff memory:d4040000-d405ffff
[/FONT]
```

However, Resolve does not recognize it. AFAIK the latest kernel versions have open source AMD graphics drivers installed and have even been shown to give better performance than the proprietary ones.
From some Google research, most people use the eGPU for an external monitor and completely switch to it, but my use case would require using both the internal Nvidia dGPU and the RX580 eGPU simultaneously, with Nvidia rendering the GUI and the RX580 helping compute video rendering (without an external screen connected to the eGPU).

Is there any way to do this in ubuntu?

---

