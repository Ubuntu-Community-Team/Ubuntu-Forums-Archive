---
title: "AMD A10-8700P APU Carrizo graphics no drivers"
date: 2016-09-03
forum: Hardware
---

### Post by moriancumer_12 on 2016-09-03
Recently purchased an HP Probook 455 G3 with and AMD A10-8700P APU and Carrizo graphics. 

I can't seem to get my graphics running correctly. Resolution is only 1024X768 and boots to a black screen. I've resolved the black screen issue by adding nomodeset quiet nosplash in the /etc/default/grub file. I've tried the proprietary driver and the mainline kernel with no luck. I've read reviews with Ubuntu 16.04 running on this same hardware with no mention of many issues, but that's not the case with me. 

How can I get the graphic to work correctly?

```
inxi -SMCGxx
System:    Host: jared Kernel: 4.4.14-040414-generic x86_64 (64 bit gcc: 5.3.1)
           Desktop: Unity 7.4.0 (Gtk 3.18.9-1ubuntu3.1) dm: lightdm
           Distro: Ubuntu 16.04 xenial
Machine:   System: HP (portable) product: HP ProBook 455 G3 Chassis: type: 10
           Mobo: HP model: 80EF v: KBC Version 92.47
           Bios: HP v: N79 Ver. 01.09 date: 01/21/2016
CPU:       Quad core AMD A10-8700P Radeon R6 10 Compute Cores 4C+6G (-MCP-) cache: 4096 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm) bmips: 14373
           clock speeds: min/max: 1300/1800 MHz 1: 1600 MHz 2: 1300 MHz
           3: 1300 MHz 4: 1800 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Carrizo
           bus-ID: 00:01.0 chip-ID: 1002:9874
           Display Server: X.Org 1.18.3 drivers: fbdev,ati (unloaded: vesa,radeon)
           Resolution: 1024x768@76.00hz
           GLX Renderer: Gallium 0.4 on llvmpipe (LLVM 3.8, 128 bits)
           GLX Version: 3.0 Mesa 11.2.0 Direct Rendering: Yes
```

---

### Post by mörgæs on 2016-09-04
Have you tried a live boot of 16.10 (beta)?

---

### Post by gordintoronto on 2016-09-05
Your laptop was actually released after Ubuntu 16.04, so the lack of support is not surprising. +1 for trying 16.10.

Plus, AMD is in the midst of rethinking its Linux support.

---

### Post by moriancumer_12 on 2016-09-05
No luck with 16.10. Booted to a black screen.

---

### Post by gordintoronto on 2016-09-05
You'll still need nomodeset

---

### Post by moriancumer_12 on 2016-09-05
It was a boot issue. BIOS was Legacy changed to UEFI and that fixed it.

---

