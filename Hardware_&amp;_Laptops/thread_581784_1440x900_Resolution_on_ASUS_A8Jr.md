---
title: "1440x900 Resolution on ASUS A8Jr?"
date: 2007-10-19
forum: Hardware &amp; Laptops
---

### Post by pilotet on 2007-10-19
Hi,
I have an ASUS a8JR laptop but the only thing I can't not do with Ubuntu Gusty 7.10 it's change the resolution to 1440x900.

ATI Radeon X2300 with restricted drivers installed.

I've tried to edit xorg.conf and change it directly but it doesn't work.
Also dpkg-reconfigure -phigh xserver-xorg and the same problem.

Here I paste my conf.

**xorg.conf**
```

Section "ServerLayout"

        # Uncomment if you have a wacom tablet
        #       InputDevice     "stylus"        "SendCoreEvents"
        #       InputDevice     "cursor"        "SendCoreEvents"
        #       InputDevice     "eraser"        "SendCoreEvents"
        Identifier     "Default Layout"
        Screen         "Default Screen" 0 0
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
        InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"
EndSection

Section "Module"
        Load  "glx"
EndSection

Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "us"
EndSection

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ImPS/2"
        Option      "ZAxisMapping" "4 5"
        Option      "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
        Identifier  "Synaptics Touchpad"
        Driver      "synaptics"
        Option      "SendCoreEvents" "true"
        Option      "Device" "/dev/psaux"
        Option      "Protocol" "auto-dev"
        Option      "HorizEdgeScroll" "0"
EndSection

Section "InputDevice"
        Identifier  "stylus"
        Driver      "wacom"
        Option      "Device" "/dev/input/wacom"
        Option      "Type" "stylus"
        Option      "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Identifier  "eraser"
        Driver      "wacom"
        Option      "Device" "/dev/input/wacom"
        Option      "Type" "eraser"
        Option      "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Identifier  "cursor"
        Driver      "wacom"
        Option      "Device" "/dev/input/wacom"
        Option      "Type" "cursor"
        Option      "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
        Identifier   "Monitor genérico"
        Option      "DPMS"
EndSection

Section "Device"
        Identifier  "Tarjeta de vídeo genérica"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
        BusID       "PCI:1:0:0"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "Tarjeta de vídeo genérica"
        Monitor    "Monitor genérico"
        DefaultDepth     24
        SubSection "Display"
                Modes    "1440x900" "1280x1024" "1024x768"
        EndSubSection
EndSection

Section "Extensions"
        Option      "Composite" "0"
EndSection


```

and **glxinfo**:
```

name of display: :1.0
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_get_proc_address, GLX_SGI_video_sync, GLX_ARB_multisample, 
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_multisample
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X2300
OpenGL version string: 1.2 (2.0.6473 (8.37.6))
OpenGL extensions:
    GL_ARB_multitexture, GL_ARB_texture_border_clamp, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_dot3, GL_ARB_transpose_matrix, GL_EXT_abgr, 
    GL_EXT_blend_color, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon


```

Can you help me?

Thanks!

---

### Post by nfshp253 on 2007-10-22
You know why, the maximum resolution for the X2300 gpu on Asus A8Jr is only 1280*800, so you cannot make use of a 1440*900 resolution:lolflag:

---

### Post by pilotet on 2007-10-22
Hi nfshp253 ,

I have changed my xorg.conf with
Modes    "1440x900" "1280x1024" "1024x768" and I can't use 1280x1024 only 1024x768.

Could you post your xorg.conf?


Thanks

---

### Post by nfshp253 on 2007-10-23
did you not read my reply properly, maximum resolution is only 1280*800! of course you cannot use 1280*1024! Anyway,where did you get all the drivers (Wireless, LAN, Webcam...) for the Asus A8Jr??

---

### Post by pilotet on 2007-10-23
It works all with the Gusty Installation (not upgrade)

---

### Post by fredylee on 2007-10-24
> **nfshp253 said:**
> did you not read my reply properly, maximum resolution is only 1280*800! of course you cannot use 1280*1024! Anyway,where did you get all the drivers (Wireless, LAN, Webcam...) for the Asus A8Jr??

I have the same laptop as you guys...
Wireless is showed as restricted hardware as the ATI graphic card, I can enable it.
I don't the wireless conncetion here but I think it works good.
Lan...It is just good when I run in live cd or installed in my hard disk
Webcam...I try all the methods, just can't make it work...plz tell me if you settle the problem..I will be very happy about that...

---

