---
title: "no DRI, software OpenGL with Intel 945 in 9.04 jaunty"
date: 2009-05-10
forum: Hardware
---

### Post by khayyam37 on 2009-05-10
More intel graphics problems in jaunty. Everything is slow. I've tried the troubleshooting guide ( [https://wiki.ubuntu.com/X/Troubleshooting/IntelPerformance]("https://wiki.ubuntu.com/X/Troubleshooting/IntelPerformance") ) but no luck. UXA doesn't work for me (black screen) and greedy doesn't provide much improvement. 

OpenGL is falling back to software:

% glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: Software Rasterizer

because DRI is disabled:

% egrep "(GLX|DRI)" /var/log/Xorg.0.log
(==) AIGLX enabled
(II) Loading extension GLX
(II) Loading extension XFree86-DRI
(II) Loading extension DRI2
(WW) intel(0): DRI2 requires UXA
(--) intel(0): DRI is disabled because it needs HW cursor, 2D accel and AGPGART.
(II) intel(0): 0x007bf000-0x0f9f3fff: DRI memory manager (248020 kB)
(II) AIGLX: Screen 0 is not DRI2 capable
(EE) AIGLX error: drmMap of framebuffer failed (Invalid argument)(EE) AIGLX: reverting to software rendering
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0

I'm now lost, though, figuring out "HW cursor, 2D accel and AGPGART". Help please?


% lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

---

### Post by khayyam37 on 2009-05-10
solved my own problem. kinda. it appears to be the case of an overly cryptic error message. DRI cannot be enabled if one of the dimensions of your virtual display is > 2048. If you try to set virtual to 2050 x 1050, for example, you get a handy message in Xorg.0.log about this limitation. If you set Virtual to 1400x2074, you get the above cryptic message...

---

