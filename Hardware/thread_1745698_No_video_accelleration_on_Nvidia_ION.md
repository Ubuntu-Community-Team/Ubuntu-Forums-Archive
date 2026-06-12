---
title: "No video accelleration on Nvidia ION"
date: 2011-05-01
forum: Hardware
---

### Post by elCapitano on 2011-05-01
I installed Ubuntu 11.4 on a new ZOTAC Zbox HD-ID40. It comes with a Intel NM10 Express chip-set and ATOM D525 with dual core 1.8 GHz processor. 

Everything works fine on that machine except the video acceleration.

I can watch a video 640x480 without any problems, but on 720p HD videos i can only see a new picture every 5 seconds. After a minuet the board gives a long high tone followed by a not as high tone and the System nearly freezes.

NVIDIA Driver Version: 270.41.06
Dimensions:1920x1080 pixels (1626x914 millimeters)
Resolution:30x30 dots per inch
GlxInfo:
```

direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_swap_control, GLX_EXT_texture_from_pixmap, GLX_ARB_create_context, 
    GLX_ARB_create_context_profile, GLX_EXT_create_context_es2_profile, 
    GLX_ARB_create_context_robustness, GLX_ARB_multisample, 
    GLX_NV_float_buffer, GLX_ARB_fbconfig_float, GLX_EXT_framebuffer_sRGB
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
    GLX_NV_video_capture, GLX_EXT_create_context_es2_profile, 
    GLX_ARB_create_context_robustness


```Are there any settings to do which i forgot?

Thank you.

---

### Post by Nutria on 2011-05-02
> **elCapitano said:**
> I installed Ubuntu 11.4 on a new ZOTAC Zbox HD-ID40. It comes with a Intel NM10 Express chip-set and ATOM D525 with dual core 1.8 GHz processor. 

Everything works fine on that machine except the video acceleration.

"Everything" like glxgears?

> I can watch a video 640x480 without any problems, but on 720p HD videos i can only see a new picture every 5 seconds.

Using what program?

> NVIDIA Driver Version: 270.41.06

Have you install vdpau?


> Dimensions:1920x1080 pixels (1626x914 millimeters)
Resolution:30x30 dots per inch

**30** dpi???  That's... paleolithic.

---

### Post by elCapitano on 2011-05-06
> **Nutria said:**
> "Everything" like glxgears?



Using what program?



Have you install vdpau?




**30** dpi???  That's... paleolithic.


Yes, GlxGears works fine and has 1128 frames in 5.0 seconds = 225.477 FPS;
I used vlc player, Totem.
vdpau is commercial -> i wont use it.
30 DPI is because the display of the PC is a 46" TV and if you want to see something 3 meters away, you have to increase the dpi ;)

Any ideas?

---

### Post by Nutria on 2011-05-06
> I used vlc player, Totem.

Those are s/w renderers.  On such a meager CPU, you *need* mplayer, which knows how to use VDPAU.

> vdpau is commercial -> i wont use it.

So is NVIDIA Driver v270.41.06.  Or didn't you know that?

> Any ideas?

Three choices:
[LIST=1]
[*]install vdpau and use mplayer,
[*]buy a system w/ a beefier CPU,
[*]use MS Windows and it's proprietary drivers.
[/LIST]

You can guess that I suggest #1.

---

### Post by elCapitano on 2011-05-06
> **Nutria said:**
> Those are s/w renderers.  On such a meager CPU, you *need* mplayer, which knows how to use VDPAU.



So is NVIDIA Driver v270.41.06.  Or didn't you know that?



Three choices:
[LIST=1]
[*]install vdpau and use mplayer,
[*]buy a system w/ a beefier CPU,
[*]use MS Windows and it's proprietary drivers.
[/LIST]

You can guess that I suggest #1.
Thanks for your help. 

1. worked!
2. not yet :-)
3. never!! :D

The NVIDIA Driver is the correct one. 
Mplayer with output on VDPAU solved the issue (with ubuntu codecs). I still cant watch big Flash Videos on 720p or even 1080p. Is it possible to change the output of standard Video out on VDPAU too? At least for flash?

Thank you very much!

---

### Post by solitaire on 2011-05-06
> **elCapitano said:**
> Thanks for your help. 

1. worked!
2. not yet :-)
3. never!! :D

The NVIDIA Driver is the correct one. 
Mplayer with output on VDPAU solved the issue (with ubuntu codecs). I still cant watch big Flash Videos on 720p or even 1080p. Is it possible to change the output of standard Video out on VDPAU too? At least for flash?

Thank you very much!

At the moment hardware acceleration for flash is for 32bit only if i remember correctly.

Think programs need to be compiled to use vdpau. That's why only a few things like XBMC and mplayer have better playback with the Nvidia drivers.

---

### Post by Nutria on 2011-05-06
> **elCapitano said:**
> I still cant watch big Flash Videos on 720p or even 1080p.

Through your web browser, I presume?


> Is it possible to change the output of standard Video out on VDPAU too? At least for flash?

Like Solitaire said, no.  However...

What you **can** do is d/l the videos with youtube-dl or clive, then watch them off-line using mplayer+vdpau.

---

### Post by elCapitano on 2011-05-07
Thanks for your awnsers! There are tutorials and hints for getting flash through vdpau on x64 linux:

[http://ubuntuforums.org/showthread.php?t=1636333](http://ubuntuforums.org/showthread.php?t=1636333)

have a nice weekend!

---

