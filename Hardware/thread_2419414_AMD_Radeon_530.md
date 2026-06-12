---
title: "AMD Radeon 530"
date: 2019-05-21
forum: Hardware
---

### Post by Nikos_Kyriazis on 2019-05-21
[FONT=ubuntu]I have a [Dell Inspiron 5570]("https://www.dell.com/id/p/inspiron-15-5570-laptop/pd") with a dedicated GPU AMD Radeon 530. I am running ubuntu mate 18.04.
[/FONT]
[FONT=ubuntu]inxi -G returns the following:

[/FONT]```
Graphics: Card-1: Intel UHD Graphics 620
Card-2: Advanced Micro Devices [AMD/ATI] Topaz XT [Radeon R7 M260/M265 / M340/M360 / M440/M445]
Display Server: x11 (X.Org 1.20.1 )
drivers: modesetting,ati,amdgpu (unloaded: fbdev,vesa)
Resolution: 1920x1080@60.05hz
OpenGL: renderer: Mesa DRI Intel UHD Graphics 620 (Kabylake GT2)
version: 4.5 Mesa 18.2.8
```
[FONT=ubuntu]
I am not sure I have the correct driver for the amd GPU. When I choose to use the specific gpu I get worst results compared to the intel one. I run glmark2 and I got:

[/FONT][COLOR=#333333][FONT=Consolas]DRI_PRIME=0 glmark2 --fullscreen
glmark2 2014.03+git20150611.fa71af2d
OpenGL Information
[/FONT][/COLOR][COLOR=#333333][FONT=Consolas]GL_VENDOR:     Intel Open Source Technology Center
[/FONT][/COLOR][COLOR=#333333][FONT=Consolas]GL_RENDERER:   Mesa DRI Intel(R) UHD Graphics 620 (Kabylake GT2)
[/FONT][/COLOR][COLOR=#333333][FONT=Consolas]GL_VERSION:    3.0 Mesa 18.2.8
[/FONT][/COLOR][COLOR=#333333][FONT=Consolas][build] use-vbo=false: FPS: 759 FrameTime: 1.318 ms
**glmark2 Score: **759****

DRI_PRIME=1 glmark2 --fullscreen
glmark2 2014.03+git20150611.fa71af2d
OpenGL Information
[/FONT][/COLOR][COLOR=#333333][FONT=Consolas]GL_VENDOR:     X.Org
[/FONT][/COLOR][COLOR=#333333][FONT=Consolas]GL_RENDERER:   AMD ICELAND (DRM 3.26.0, 4.18.0-20-generic, LLVM 7.0.0)
[/FONT][/COLOR][COLOR=#333333][FONT=Consolas]GL_VERSION:    4.4 (Compatibility Profile) Mesa 18.2.8
[/FONT][/COLOR][COLOR=#333333][FONT=Consolas][build] use-vbo=false: FPS: 138 FrameTime: 7.246 ms
[build] use-vbo=true: FPS: 142 FrameTime: 7.042 ms
**glmark2 Score: **140****[/FONT][/COLOR]

[FONT=ubuntu]I would appreciate any suggestions on installing the correct driver for amd.[/FONT]
[FONT=ubuntu]Thank you and excuse my long post.[/FONT]

---

### Post by Yellow Pasque on 2019-05-22
> I would appreciate any suggestions on installing the correct driver for amd.

The correct driver is already installed. Try a more modern benchmark like unigine valley. glmark2 can be misleading since it is only using OpenGL ES 2.0.

---

### Post by rkc19 on 2019-05-23
> **Nikos_Kyriazis said:**
> 
[FONT=ubuntu]I would appreciate any suggestions on installing the correct driver for amd.[/FONT]


Hi Nikos. I can't really say why glmark2 is showing a lower score for your dedicated graphics card; I'm not at all familiar with benchmark software. However, when installing Ubuntu on my machine, which has an AMD APU, I did some research on what drivers, if any, would have to be installed after the main installation. I found this [ page]("https://help.ubuntu.com/community/AMDGPU-Driver#Supported_hardware"), discussing the AMDGPU driver, which is the driver that AMD will develop going forward. Your 530 uses the Polaris chipset, so it is supported by amdgpu. Since flgrx is deprecated, and the radeon driver is for cards older than those supported by amdgpu, amdgpu *is *the correct driver for your graphics card.

---

### Post by Nikos_Kyriazis on 2019-05-23
Thank you for your replies.
I understand I may already have the correct answer on my laptop but its performance using the amd gpu is worse than using the intel one.
I followed the instruction in [this page]("https://easylinuxtipsproject.blogspot.com/p/amd.html") and I now have newer drivers in both intel and amd, with intel still outperforming amd.

---

