---
title: "Intel UHD Graphics card does not work correctly and does not detect second monitor."
date: 2023-10-31
forum: Hardware
---

### Post by albertocrego-gmail on 2023-10-31
Good morning,
I recently bought a new laptop, specifically the "HP probook 440 G9 Notebook" model with a "12th Gen Intel i5 1235U" processor with a "UHD Graphics" graphics card. I installed Ubuntu 22.04, which was the one I had before on my previous laptop and I find that my graphics card is not working correctly, sometimes the screen flashes, it goes black for several seconds and the second monitor I have does not detect me, I agree HDMI to it and I tried with several monitors. I updated all available drivers and the kernel but it still doesn't work.
Does anyone know what can happen, do they need a log? or the execution of some command.
All the best.

---

### Post by readableauthor on 2023-10-31
Post these commands outputs:
```

lspci -knn | grep -iEA5 'vga|3d|display'
glxinfo | grep OpenGL

```

---

### Post by albertocrego-gmail on 2023-10-31
I attach the result of the commands executed.

u```
buntu@ubuntu:~$ lspci -knn | grep -iEA5 'vga|3d|display'
00:02.0 VGA compatible controller [0300]: Intel Corporation Alder Lake-UP3 GT2 [UHD Graphics] [8086:4628] (rev 0c)
    DeviceName: Onboard IGD
    Subsystem: Hewlett-Packard Company Alder Lake-UP3 GT2 [UHD Graphics] [103c:8a9e]
    Kernel driver in use: i915
    Kernel modules: i915
00:04.0 Signal processing controller [1180]: Intel Corporation Alder Lake Innovation Platform Framework Processor Participant [8086:461d] (rev 04)
--
00:06.2 PCI bridge [0604]: Intel Corporation 12th Gen Core Processor PCI Express x4 Controller #2 [8086:463d] (rev 04)
    Subsystem: Hewlett-Packard Company 12th Gen Core Processor PCI Express x4 Controller [103c:8a9e]
    Kernel driver in use: pcieport
00:08.0 System peripheral [0880]: Intel Corporation 12th Gen Core Processor Gaussian & Neural Accelerator [8086:464f] (rev 04)
    Subsystem: Hewlett-Packard Company 12th Gen Core Processor Gaussian & Neural Accelerator [103c:8a9e]
00:0d.0 USB controller [0c03]: Intel Corporation Alder Lake-P Thunderbolt 4 USB Controller [8086:461e] (rev 04)

ubuntu@ubuntu:~$ glxinfo | grep OpenGL
OpenGL vendor string: Intel
OpenGL renderer string: Mesa Intel(R) Graphics (ADL GT2)
OpenGL core profile version string: 4.6 (Core Profile) Mesa 23.2.1-1ubuntu3
OpenGL core profile shading language version string: 4.60
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 4.6 (Compatibility Profile) Mesa 23.2.1-1ubuntu3
OpenGL shading language version string: 4.60
OpenGL context flags: (none)
OpenGL profile mask: compatibility profile
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 3.2 Mesa 23.2.1-1ubuntu3
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.20
OpenGL ES profile extensions:
ubuntu@ubuntu:~$
```

I also tried Ubuntu 23.10 and the same thing happens.
A greeting and thank you very much for the help.

---

### Post by evil4ce on 2024-07-20
Did you solve the problem? I'm planning to buy a Dell laptop which also has Intel i5 [COLOR=#000000]1235U [/COLOR][COLOR=#000000]processor with a UHD Graphics graphics card, with intention to install Ubuntu 22.04. After reading your post I'm having [/COLOR]second thoughts.

---

