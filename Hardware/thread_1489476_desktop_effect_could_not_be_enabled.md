---
title: "desktop effect could not be enabled"
date: 2010-05-21
forum: Hardware
---

### Post by ramazani on 2010-05-21
hi i was wondering if anyone could tell me when i installed ubuntu 10.4 first i was able to enable visual effect extra now when i click on it it said desktop effect could not be enabled, also i downloaded a compiz manager i can not see all the effece like 3d windows and few more stuff, i watched in utube and it seems got missing few thing, when i run compiz it give me this below

kanishixan@kanishixan-laptop:~$ compiz
Xlib:  extension "GLX" missing on display ":0.0".
compiz (core) - Fatal: Root visual is not a GL visual
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

Launching fallback window manager

also here is my vga driver
kanishixan@kanishixan-laptop:~$ lspci -nn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 0c)
kanishixan@kanishixan-laptop:~$

---

### Post by labinnsw on 2010-05-22
1.   Install libglitz-glx1, libgl1-mesa-dri and libgl1-mesa-glx from Synaptic
2.   Ensure your video card's proprietary driver is installed
        System >> Administration >> Hardware Drivers

---

