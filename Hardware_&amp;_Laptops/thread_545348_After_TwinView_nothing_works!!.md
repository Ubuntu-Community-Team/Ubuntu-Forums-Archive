---
title: "After TwinView nothing works!!"
date: 2007-09-07
forum: Hardware &amp; Laptops
---

### Post by eskimo on 2007-09-07
Hi to you all, i had a linux feisty with nvidia 3d driver working on a geforce7300 gt. Beryl worked for months, everything was ok. Then i configured twinview, making a xorg.conf backup.
I found a not very well solutions for a lcd and a tv, so i returned  back to my old xorg.conf.
Now nvidia driver no longer works!!! i can use linux only with normal nv driver!

this is my xorg error log:
> 
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):     that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):     that the NVIDIA device files have been created properly. 
(EE) NVIDIA(0):     Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

help me please!
thank you! Paolo

---

