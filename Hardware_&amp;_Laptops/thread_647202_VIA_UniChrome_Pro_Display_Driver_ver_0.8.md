---
title: "VIA UniChrome Pro Display Driver ver 0.8"
date: 2007-12-22
forum: Hardware &amp; Laptops
---

### Post by gary4gar on 2007-12-22
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-via/+bug/43154](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-via/+bug/43154) [br].[/br] ---------------------------- [br].[/br] [br].[/br] 				> VIA recently released their binary driver for their integrated graphics for linux. To install it:

1. I downloaded the driver from [http://www.viaarena.com/default.aspx?PageID=2&Type=3](http://www.viaarena.com/default.aspx?PageID=2&Type=3).
2. Choose your distro.
3. Then pick Integrated Graphics.
4. Pick the appropriate driver category. If you are not sure which one, check this site [http://www.viaarena.com/default.aspx...ticleID=68&P=5](http://www.viaarena.com/default.aspx...ticleID=68&P=5).
5. Click on "Click here to begin free download." Save it.
6. Unzip the file.
7. Make a backup of your xorg.conf.
8. CD to the directory where you unzipped the file to.
9. Execute the *.run file. example "sudo sh VIA_U710_UniChrome-GFX-v40072d.run"
10. Ctrl-Alt-Bckspce
now i did the above mentined procedure but, i have three problems:-
1) weird errors like "libGL warning: 3D driver claims to not support visual 0x22"
2) my system freezes randomly,i even can't play a movie:(
3) corrupted textures even in 2d applications

My distro:Ubuntu 7.10
glxinfo
```

libGL warning: 3D driver claims to not support visual 0x22
libGL warning: 3D driver claims to not support visual 0x23
libGL warning: 3D driver claims to not support visual 0x24
libGL warning: 3D driver claims to not support visual 0x25
libGL warning: 3D driver claims to not support visual 0x26
libGL warning: 3D driver claims to not support visual 0x27
libGL warning: 3D driver claims to not support visual 0x28
libGL warning: 3D driver claims to not support visual 0x29
libGL warning: 3D driver claims to not support visual 0x2a
libGL warning: 3D driver claims to not support visual 0x2b
libGL warning: 3D driver claims to not support visual 0x2c
libGL warning: 3D driver claims to not support visual 0x2d
libGL warning: 3D driver claims to not support visual 0x2e
libGL warning: 3D driver claims to not support visual 0x2f
libGL warning: 3D driver claims to not support visual 0x30
libGL warning: 3D driver claims to not support visual 0x
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGI_swap_control, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_visual_select_group
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_swap_control, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_visual_select_group
OpenGL vendor string: VIA Technology
OpenGL renderer string: Mesa DRI UniChrome (K8M800) 20060710 x86/MMX+/3DNow!+/SSE2
OpenGL version string: 1.2 Mesa 6.5.1
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_point_parameters, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_minmax, 
    GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_compiled_vertex_array, GL_EXT_convolution, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_histogram, 
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_polygon_offset, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle, 
    GL_EXT_vertex_array, GL_APPLE_packed_pixels, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_MESA_window_pos, GL_NV_blend_square, 
    GL_NV_light_max_exponent, GL_NV_texture_rectangle, 
    GL_NV_texgen_reflection, GL_OES_read_format, GL_SGI_color_matrix, 
    GL_SGI_color_table, GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x22 24 tc  1 24  0 r  y  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0x23 24 tc  1 24  0 r  .  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0x24 24 tc  1 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x25 24 tc  1 24  0 r  .  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x26 24 tc  1 24  0 r  y  .  8  8  8  0  0 32  0  0  0  0  0  0 0 None
0x27 24 tc  1 24  0 r  .  .  8  8  8  0  0 32  0  0  0  0  0  0 0 None
0x28 24 tc  1 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0x29 24 tc  1 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0x2a 24 tc  1 24  0 r  y  .  8  8  8  0  0  0  0 16 16 16 16  0 0 None
0x2b 24 tc  1 24  0 r  .  .  8  8  8  0  0  0  0 16 16 16 16  0 0 None
0x2c 24 tc  1 24  0 r  y  .  8  8  8  0  0 16  0 16 16 16 16  0 0 None
0x2d 24 tc  1 24  0 r  .  .  8  8  8  0  0 16  0 16 16 16 16  0 0 None
0x2e 24 tc  1 24  0 r  y  .  8  8  8  0  0 32  0 16 16 16 16  0 0 None
0x2f 24 tc  1 24  0 r  .  .  8  8  8  0  0 32  0 16 16 16 16  0 0 None
0x30 24 tc  1 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16 16  0 0 None
0x31 24 tc  1 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16 16  0 0 None
0x53 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon
``````
user@MOODY-MACHINE:~$ cat /etc/X11/xorg.conf
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
        FontPath        "/usr/share/fonts/X11/misc"
        FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "freetype"
        Load    "int10"
        Load    "vbe"
        Load    "extmod"
        Load    "dri"
        Load    "glx"
        Load    "dbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "Generic Video Card"
        BoardName   "via"
        VendorName  "VIA Tech"
        Driver "via"
EndSection

Section "Monitor"
        Option          "DPMS"
        ModeLine "848x480" 47.4 848 888 976 1104 480 481 484 505
        ModeLine "1440x1050" 184.5 1440 1544 1704 1968 1050 1051 1054 1103
        ModeLine "1280x768" 118.5 1280 1368 1504 1728 768 769 772 807
        ModeLine "1440x1050" 160.0 1440 1536 1696 1952 1050 1051 1054 1096
        ModeLine "1280x768" 103.0 1280 1360 1496 1712 768 769 772 802
        ModeLine "1024x512" 53.3 1024 1072 1176 1328 512 513 516 535
        ModeLine "856x480" 41.3 856 888 976 1096 480 481 484 502
        ModeLine "848x480" 41.0 848 880 968 1088 480 481 484 502
        ModeLine "720x576" 42.6 720 760 832 944 576 577 580 602
        ModeLine "720x480" 34.9 720 752 824 928 480 481 484 502
        ModeLine "1920x1080" 172.9 1920 2043 2249 2578 1080 1081 1084 1118
        ModeLine "1440x1050" 126.2 1440 1536 1688 1936 1050 1051 1054 1087
        ModeLine "1440x900" 106.47 1440 1520 1672 1904 900 901 904 932 -HSync +Vsync
        ModeLine "1366x768" 85.86 1366 1440 1584 1800 768 769 772 795 -HSync +Vsync
        ModeLine "1360x768" 85.50 1360 1392 1712 1744 768 783 791 807 +HSync +Vsync
        ModeLine "1280x768" 80.1 1280 1344 1480 1680 768 769 772 795
        ModeLine "1280x720" 74.6 1280 1341 1474 1688 720 721 724 746
        ModeLine "1024x512" 41.3 1024 1056 1160 1296 512 513 516 531
        ModeLine "856x480" 31.7 856 872 960 1064 480 481 484 497
        ModeLine "848x480" 31.5 848 864 952 1056 480 481 484 497
        ModeLine "800x480" 29.58 800 816 896 992 480 481 484 497
        ModeLine "720x576" 32.7 720 744 816 912 576 577 580 597
        ModeLine "720x480" 26.7 720 736 808 896 480 481 484 497
        #Refresh Rate 60Hz
        Identifier "MonitorGeneric Video Card"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
    Monitor  "MonitorGeneric Video Card"
        DefaultDepth    24
        SubSection "Display"
                Modes  "1024x768"         
                Depth           1
        EndSubSection
        SubSection "Display"
                Modes  "1024x768"         
                Depth           4
        EndSubSection
        SubSection "Display"
                Modes  "1024x768"         
                Depth           8
        EndSubSection
        SubSection "Display"
                Modes  "1024x768"         
                Depth           15
        EndSubSection
        SubSection "Display"
                Modes  "1024x768"         
                Depth           16
        EndSubSection
        SubSection "Display"
                Modes  "1024x768"
                Depth           24
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
EndSection

Section "DRI"
        Mode 0666
EndSection

```

[My Xorg.log.0 file]("http://pastebin.com/f40e10d1d")(posted on pastebin as max char limit was reached)


Is there anyone who tried the new driver, did this driver work for anyone.
ATM i am using the binary driver, as VIA gives the source too, so will compiling from source make a diffrence?

is there anyway i can make it work?

---

### Post by SOULRiDER on 2007-12-23
Why dont you try using the Open source drivers? It seems theya re less buggy than these drivers.
[http://ubuntuforums.org/showthread.php?t=485646](http://ubuntuforums.org/showthread.php?t=485646)

---

