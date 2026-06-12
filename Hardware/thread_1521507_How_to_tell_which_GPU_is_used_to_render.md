---
title: "How to tell which GPU is used to render?"
date: 2010-06-30
forum: Hardware
---

### Post by cbstryker on 2010-06-30
So I've been having a bit of an issue with Lord of the Rings Online performance recently. I've played LOTRO in the past in CXGames (Crossover Games) for years and never had a problem, LOTRO always ran like a champ, even better than in Windows in some cases. 

However, a little while ago I got a second video card to use as a simple VGA passthrough for a third monitor, and of course I want to do triplehead gaming. But I've been noticing, even with the game on only 1 monitor it's very laggy (when across more than 1 screen with settings set to lowest it's still laggy, but with just one screen it seems ok), almost as if it's using the slower card. So here is my system:

Ubuntu 10.04 64bit
Asus P5K Motherboard
Q6600 overclocked to 3.07GHz (stable)
8GB DDR2 overclocked to 1000Mhz (stable)
3 Monitors, each a separate X screen with Xinerama enabled.
GeForce 260 GT running screen 0 (main screen) and 1
GeForce 8400 GS running screen 2

Screens arranged as 2,0,1

When I type "glxheads" and "glxheads :0" both give me this:

```
chris@chris-ubuntu:~$ glxheads :0
Name: :0.0
  Display:     0x68f6d0
  Window:      0x5200002
  Context:     0x6ba368
  GL_VERSION:  3.3.0 NVIDIA 256.35
  GL_VENDOR:   NVIDIA Corporation
  GL_RENDERER: GeForce 8400 GS/PCI/SSE2

```

Not sure if this is relevant but when I close the window this pops up:

```
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 63 requests (63 known processed) with 0 events remaining.

```

However, when I have separate X screen with Xinerama _disabled_ the GL_RENDERER line says "GeForece 260 GT" when started from screen 0 or 1, screen 2 would still give me "GeForece 8400 GS".

So I think what's been happening is that everything has been using the 8400GS and not the 260GT this whole time, but how can I check this and how can I change it?

BTW, I've tried adding " :0" to the launcher for LOTRO with no effect, but then again glxheads had no impact with that either.

Any ideas?

---

### Post by cbstryker on 2010-07-01
anyone?

---

### Post by cbstryker on 2010-07-04
Please, I'm looking for input from anyone.

---

### Post by dino99 on 2010-07-04
maybe some help here, look at dynamic-twinview & multigpu settings

[http://manpages.ubuntu.com/manpages/lucid/man1/nvidia-xconfig.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/nvidia-xconfig.1.html)

---

### Post by cbstryker on 2010-07-04
> **dino99 said:**
> maybe some help here, look at dynamic-twinview & multigpu settings

[http://manpages.ubuntu.com/manpages/lucid/man1/nvidia-xconfig.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/nvidia-xconfig.1.html)

Hi, I appreciate the reply. I've looked over those before, but I can't make heads or tails as to which one will give me what I need.

Just as an update, when I disable the one screen on the second GPU, "glxheads" shows "GeForece 260 GT" in the output and the spinning graphic is almost a blur compared to doing it with the "GeForce 8400 GS". So this clearly is an issue of the wrong GPU being used.

---

### Post by cbstryker on 2010-07-06
I've found something to add. Notice towards the bottom it says "GeForce 8400 GS" and nowhere does it mention my GeForce 260 GTX.

The output of glxinfo:

```
chris@chris-ubuntu:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_swap_control, GLX_EXT_texture_from_pixmap, GLX_ARB_create_context, 
    GLX_ARB_create_context_profile, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float, GLX_EXT_framebuffer_sRGB
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_EXT_swap_control, GLX_ARB_create_context, 
    GLX_ARB_create_context_profile, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float, GLX_EXT_fbconfig_packed_float, 
    GLX_EXT_texture_from_pixmap, GLX_EXT_framebuffer_sRGB, 
    GLX_NV_present_video, GLX_NV_copy_image, GLX_NV_multisample_coverage, 
    GLX_NV_video_capture
GLX version: 1.4
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_swap_control, GLX_EXT_texture_from_pixmap, GLX_ARB_create_context, 
    GLX_ARB_create_context_profile, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float, GLX_EXT_framebuffer_sRGB, 
    GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 8400 GS/PCI/SSE2
OpenGL version string: 3.3.0 NVIDIA 256.35
OpenGL shading language version string: 3.30 NVIDIA via Cg compiler
```

---

### Post by lukeiamyourfather on 2010-07-06
Unless the system is using SLI I would guess the card the monitor is plugged into is the card doing the rendering. Without SLI/CrossFire the cards don't talk to each other or render anything elsewhere. Cheers!

---

