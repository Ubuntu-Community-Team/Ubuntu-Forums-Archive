---
title: "Enable discreet graphics card  (AMD) (HDMI not working) 16.04 LTS"
date: 2016-04-25
forum: Hardware
---

### Post by redguy41 on 2016-04-25
Hi,


[TABLE]
[TR]
[TD]

[/TD]
[TD]I have a hybrid-graphics system with power-saving onboard Intel graphics, and an ATI accelerator (Lenovo z51-70, i5, 8 GB RAM, SSD).


Back in 14.04, with fglrx, I used to have ATI Catalyst, which would provide me with an option of switching between the cards, and using HDMI, playing games, etc. Now it seems, since AMDGPU is used in 16.04 LTS, I cannot seem to enable my ATI discreet GPU.


Any ideas how I can do that, considering the fact fglrx is depricated?



My outputs:
*-display               
       description: VGA compatible controller
       product: Broadwell-U Integrated Graphics
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:49 memory:d0000000-d0ffffff memory:c0000000-cfffffff ioport:5000(size=64)
lspci:
04:00.0 Display controller: Advanced Micro Devices, Inc. [AMD/ATI] Venus XTX [Radeon HD 8890M / R9 M275X/M375X] (rev ff)
which is not used.


Is my display controller active, installed, and is it using AMDGPU? If so, how can I enable it and use it, or switch between the cards?
Alternatively, how can I make HDMI work over my power-saving Intel VGA controller?


[/TD]
[/TR]
[/TABLE]

---

