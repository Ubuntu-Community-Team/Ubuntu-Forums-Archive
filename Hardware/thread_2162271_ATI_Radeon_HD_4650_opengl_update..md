---
title: "ATI Radeon HD 4650 opengl update."
date: 2013-07-13
forum: Hardware
---

### Post by Vorgon on 2013-07-13
I want to thank all in advance for your help. I have been searching the forums and have not had much luck finding what I am looking for. I am new to Ubuntu but am not afraid to try new things to learn. I have been going through this forum site and getting quite a bit of information already to get everything running, so far I have been having quite a bit of luck doing so. 

I am trying to open something in Steam and I get the error
"Coulnd not find required OpenGL entry point 'glGetError'! Either your video card is unsupported, or your OpenGL driver needs to be updated." 

I have an ATI Radeon HD4650 and am running Ubuntu 12.04.1. I am running the AMD Catalyst legacy drivers version 13.1. I originally had Ubuntu 12.04.2 and found that to get my card working properly I needed to go to the 12.04.1 build. I hope someone here has a way to update my OpenGL driver, if not well, I guess I will just have to keep it dual boot with Winblows 8. 

This may help: 

cassidy@cassidy-DX4300:~$ sudo lshw -c display
[sudo] password for cassidy: 
  *-display               
       description: VGA compatible controller
       product: RV730 PRO [Radeon HD 4650]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:46 memory:d0000000-dfffffff memory:fe8f0000-fe8fffff ioport:c000(size=256) memory:fe8c0000-fe8dffff

Thanks again in advance for your help and input.

---

