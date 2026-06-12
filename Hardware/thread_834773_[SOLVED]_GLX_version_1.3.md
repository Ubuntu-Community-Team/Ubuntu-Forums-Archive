---
title: "[SOLVED] GLX version 1.3"
date: 2008-06-19
forum: Hardware
---

### Post by kwirk on 2008-06-19
Hi, I'm using Hardy and have used EnvyNG to install the latest nvidia drivers for my GeForce Go 6200/6400 on my laptop. I was trying to use a program using Java3D, but getting errors as it requires GLX version 1.3. glxinfo states that I have version 1.2. Is it possible to upgrade to version 1.3, or is this a limitation of the graphics card. I've had a good hunt round but can find any answers.

Thanks in advanced.

---

### Post by tenmoi on 2008-06-19
I am running the proprietary driver 177.13. here's a sample of glxinfo:
[COLOR="Red"]GLX version: 1.3[/COLOR]
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float, GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 6150SE nForce 430/PCI/SSE2
OpenGL version string: 2.1.2[COLOR="Red"] NVIDIA 177.13[/COLOR]

You must install the driver manually to get the 1.3 version I guess.
You should read carefully the instructions on installing the driver manually. There's a good one on their forum, but the easiest one is on this forum.

---

### Post by tenmoi on 2008-06-19
double post

---

### Post by kwirk on 2008-06-20
Here's my glxinfo...

[COLOR="Red"]GLX version: 1.2[/COLOR]
GLX extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_SGIX_fbconfig, 
    GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce Go 6200/PCI/SSE2
OpenGL version string:[COLOR="Red"] 1.2 (2.1.2 NVIDIA 173.14.05)[/COLOR]

I notice my OpenGL is version is 1.2, where the nvidia website states my card is compatible with OpenGL 2.0
 [http://www.nvidia.co.uk/object/gfgo6_techspecs.html](http://www.nvidia.co.uk/object/gfgo6_techspecs.html)
I'm not up on graphics cards but this is probably related somewhere. (Seen as GLX stands for Open**GL** Extension to the **X** Window System)

---

### Post by tenmoi on 2008-06-20
You should read your game manual for requirements of video cards. And try this first:
Install the 177.13 driver, which is still beta but which is running flawlessly on my system.

Here's the download link: [http://www.nvnews.net/vbulletin/forumdisplay.php?s&forumid=14](http://www.nvnews.net/vbulletin/forumdisplay.php?s&forumid=14)

---

### Post by tenmoi on 2008-06-20
doble

---

### Post by kwirk on 2008-06-21
I started out by removing all the current nvidia drivers and went about installing the 177 beta drivers per instructions on nvidia website (Noting I shouldn't let it change xorg.conf to keep compiz working). 

All went well, until I restarted and found the white screen of death...:confused:

I knew it was a common compiz fault so I replaced it with metacity, (using Alt-F2 and typing metacity --replace followed by enter, just in case anyone else gets stuck with this).

I checked glxinfo and it still report similar to earlier except it did have the new drivers. (Yes... still GLX 1.2)

I took my first priority to fix compiz, so tried going back to the latest non-beta drivers on nvidia... no luck.

So I tried running compiz in terminal, and it stated:
Checking for Xgl: present.
Checking for nVidia: not present.
Checking for Xgl: present. 

followed by loads of errors saying
Warn: pixmap [BLAH] can't be bound to texture

and a white screen of death.

Looking into compiz help forums found that this can be caused by having Xgl installed, which is not required when you have Nvidia drivers. So...

sudo apt-get remove xserver-glx
Ctrl-Alt-Backspace

Copmiz is working :)

glxinfo:

[COLOR="Red"]GLX version: 1.3[/COLOR] :KS
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float, GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce Go 6200/PCI/SSE2
[COLOR="Red"]OpenGL version string: 2.1.2 NVIDIA 173.14.09[/COLOR]

So, as far as I can figuire out from my old glxinfo

OpenGL version string: 1.2 [COLOR="Red"](2.1.2 NVIDIA 173.14.05)[/COLOR]

I had the right version of OpenGL, and therefore GLX, but it was being suppressed by the xserver-xgl also being in place forcing OpenGL to version 1.2.

So, for anyone else stuck with this, if you have some version of OpenGL in brackets related to your graphics card, try removing xserver-xgl

Thanks to tenmoi for making me install the beta nvidia drivers and causing the compiz white screen of death. ;)

---

