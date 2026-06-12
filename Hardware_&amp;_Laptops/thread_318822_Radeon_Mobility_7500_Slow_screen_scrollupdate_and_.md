---
title: "Radeon Mobility 7500: Slow screen scroll/update and video display question"
date: 2006-12-14
forum: Hardware &amp; Laptops
---

### Post by jweb on 2006-12-14
Hi,

I am running Ubuntu 6.06 / Gnome on my Gateway 600YGR laptop with Radeon 7500 Mobility video card.  While working in OpenOffice Impress all day today, I was constantly frustrated by slow screen scroll/updates and shape drags/drops.  I started to wonder if the video driver was to blame, so I started looking around here on UbuntuForums.  I found many posts regarding the difficulty in getting OpenGL and 3D acceleration working with the hardware.  A glxinfo | grep direct gives:

```
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect

```

As a test, I ran glgears -printfps and got:

```
719 frames in 5.0 seconds = 142.805 FPS
798 frames in 5.4 seconds = 148.493 FPS
798 frames in 5.4 seconds = 148.795 FPS

```

The target "benchmark" with a working config is over 300 FPS.  So, clearly, I am not optimized for OpenGL.  I wonder if 2D is suffering as well.

My question is if these known problems are related to my scrolling/update problems in Impress.  I didn't want to start messing with video drivers if the process wouldn't solve my problem. 

Thanks for the advice...

---

