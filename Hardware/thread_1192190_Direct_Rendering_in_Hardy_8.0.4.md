---
title: "Direct Rendering in Hardy 8.0.4"
date: 2009-06-19
forum: Hardware
---

### Post by rvgsd on 2009-06-19
Hi all, 
I am using **xubuntu 8.0.4** on **ATI Mobility Radeon 7500** with the default driver which
came with the Xubuntu installation.
I wanted to enable Direct Rendering. How can I do it?

```

$ lspci -nn | grep VGA
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500] [1002:4c57]

``````

glxinfo |grep vendor
server glx vendor string: SGI
client glx vendor string: SGI

``````

glxinfo | grep "direct rendering"
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

``````

LIBGL_DEBUG=verbose glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_EXT_texture_from_pixmap
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_occlusion_query, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_vertex_program, 
    GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_object, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_paletted_texture, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_shared_texture_palette, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_vertex_array, GL_APPLE_packed_pixels, 
    GL_ATI_draw_buffers, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_ATIX_texture_env_combine3, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_NV_blend_square, 
    GL_NV_fragment_program, GL_NV_light_max_exponent, GL_NV_point_sprite, 
    GL_NV_texgen_reflection, GL_NV_texture_rectangle, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SGIX_shadow, GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x27 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x28 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x29 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x2a 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x50 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

```

---

### Post by Yellow Pasque on 2009-06-19
Maybe you need an: Option "DRI" in your /etc/X11/xorg.conf

Also, you can look at /var/log/Xorg.0.log to see why direct rendering is failing to load.

---

### Post by rvgsd on 2009-06-19
I have the "DRI" section in my xorg.conf, and I couldnot figure out the reason from Xorg.0.log.
The file are below. Please help!

**xorg.conf**
```

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
EndSection

Section "InputDevice"
    Identifier    "Synaptics Touchpad"
    Driver        "synaptics"
    Option        "SendCoreEvents"    "true"
    Option        "Device"        "/dev/psaux"
    Option        "Protocol"        "auto-dev"
    Option        "HorizEdgeScroll"    "0"
EndSection

Section "Device"
    Identifier      "Radeon 7500"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option          "XAANoOffscreenPixmaps"
EndSection

Section "Monitor"
    Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-72
        VertRefresh     43-60
EndSection

Section "Screen"
    Identifier      "Default Screen"
        Device          "Radeon 7500"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1400x1050" "1024x768"
        EndSubSection
    Monitor        "Generic Monitor"
EndSection

Section "DRI"
        Mode 0666
EndSection
        
Section "Extensions"
        Option "Composite" "Enable"
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "Synaptics Touchpad"
EndSection

```

**Xorg.0.log**
```

This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux laptopvdg 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686
Build Date: 13 June 2008  01:08:21AM
 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Jun 19 19:15:12 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Radeon 7500"
(**) |-->Input Device "Synaptics Touchpad"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Extension "Composite" is enabled
(==) |-->Input Device "Configured Mouse"
(==) |-->Input Device "Generic Keyboard"
(==) The core pointer device wasn't specified explicitly in the layout.
    Using the first core pointer device.
(==) The core keyboard device wasn't specified explicitly in the layout.
    Using the first keyboard device.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81dc500
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.3
    X.Org Video Driver: 2.0
    X.Org XInput driver : 2.0
    X.Org Server Extension : 0.3
    X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
    ABI class: X.Org Video Driver, version 2.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2560 card 0000,0000 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2561 card 0000,0000 rev 03 class 06,04,00 hdr 01
(II) PCI: 00:1d:0: chip 8086,24c2 card 8086,24c0 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24c4 card 8086,24c0 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,24c7 card 8086,24c0 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24cd card 8086,24c0 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev 82 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24c0 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24cb card 8086,24c0 rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:5: chip 8086,24c5 card 1028,0149 rev 02 class 04,01,00 hdr 00
(II) PCI: 00:1f:6: chip 8086,24c6 card 134d,4c21 rev 02 class 07,03,00 hdr 00
(II) PCI: 01:00:0: chip 1002,4c57 card 1028,0149 rev 00 class 03,00,00 hdr 00
(II) PCI: 02:01:0: chip 14e4,4401 card 4401,1028 rev 01 class 02,00,00 hdr 00
(II) PCI: 02:02:0: chip 14e4,4320 card 1028,0001 rev 02 class 02,80,00 hdr 00
(II) PCI: 02:04:0: chip 104c,ac44 card d000,0000 rev 02 class 06,07,00 hdr 82
(II) PCI: 02:04:1: chip 104c,8029 card 1028,0149 rev 00 class 0c,00,10 hdr 80
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,3), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
    [0] -1    0    0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 I/O range:
    [0] -1    0    0x0000c000 - 0x0000c0ff (0x100) IX[B]
    [1] -1    0    0x0000c400 - 0x0000c4ff (0x100) IX[B]
    [2] -1    0    0x0000c800 - 0x0000c8ff (0x100) IX[B]
    [3] -1    0    0x0000cc00 - 0x0000ccff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
    [0] -1    0    0xfc000000 - 0xfdffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
    [0] -1    0    0xe8000000 - 0xefffffff (0x8000000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,6), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 2 I/O range:
    [0] -1    0    0x0000d000 - 0x0000d0ff (0x100) IX[B]
    [1] -1    0    0x0000d400 - 0x0000d4ff (0x100) IX[B]
    [2] -1    0    0x0000d800 - 0x0000d8ff (0x100) IX[B]
    [3] -1    0    0x0000dc00 - 0x0000dcff (0x100) IX[B]
    [4] -1    0    0x0000e000 - 0x0000e0ff (0x100) IX[B]
    [5] -1    0    0x0000e400 - 0x0000e4ff (0x100) IX[B]
    [6] -1    0    0x0000e800 - 0x0000e8ff (0x100) IX[B]
    [7] -1    0    0x0000ec00 - 0x0000ecff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
    [0] -1    0    0xf6000000 - 0xfbffffff (0x6000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 3: bridge is at (2:4:0), (2,3,6), BCTRL: 0x05c0 (VGA_EN is cleared)
(II) Bus 3 I/O range:
    [0] -1    0    0x0000d000 - 0x0000d0ff (0x100) IX[B]
    [1] -1    0    0x0000d400 - 0x0000d4ff (0x100) IX[B]
(--) PCI:*(1:0:0) ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500] rev 0, Mem @ 0xe8000000/27, 0xfcff0000/16, I/O @ 0xc000/8
(II) Addressable bus resource ranges are
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[B]
    [1] -1    0    0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xe0000000 from 0xe7ffffff to 0xdfffffff
(II) Active PCI resource ranges:
    [0] -1    0    0xfaff4000 - 0xfaff7fff (0x4000) MX[B]
    [1] -1    0    0xfaffb800 - 0xfaffbfff (0x800) MX[B]
    [2] -1    0    0xfaffc000 - 0xfaffdfff (0x2000) MX[B]
    [3] -1    0    0xfaffe000 - 0xfaffffff (0x2000) MX[B]
    [4] -1    0    0xf4fff400 - 0xf4fff4ff (0x100) MX[B]
    [5] -1    0    0xf4fff800 - 0xf4fff9ff (0x200) MX[B]
    [6] -1    0    0x50000000 - 0x500003ff (0x400) MX[B]
    [7] -1    0    0xf4fffc00 - 0xf4ffffff (0x400) MX[B]
    [8] -1    0    0xe0000000 - 0xdfffffff (0x0) MX[B]O
    [9] -1    0    0xfcff0000 - 0xfcffffff (0x10000) MX[B](B)
    [10] -1    0    0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
    [11] -1    0    0x0000b080 - 0x0000b0ff (0x80) IX[B]
    [12] -1    0    0x0000b400 - 0x0000b4ff (0x100) IX[B]
    [13] -1    0    0x0000bc40 - 0x0000bc7f (0x40) IX[B]
    [14] -1    0    0x0000b800 - 0x0000b8ff (0x100) IX[B]
    [15] -1    0    0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
    [16] -1    0    0x00000374 - 0x00000374 (0x1) IX[B]
    [17] -1    0    0x00000170 - 0x00000177 (0x8) IX[B]
    [18] -1    0    0x000003f4 - 0x000003f4 (0x1) IX[B]
    [19] -1    0    0x000001f0 - 0x000001f7 (0x8) IX[B]
    [20] -1    0    0x0000bf20 - 0x0000bf3f (0x20) IX[B]
    [21] -1    0    0x0000bf40 - 0x0000bf5f (0x20) IX[B]
    [22] -1    0    0x0000bf80 - 0x0000bf9f (0x20) IX[B]
    [23] -1    0    0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
    [0] -1    0    0xfaff4000 - 0xfaff7fff (0x4000) MX[B]
    [1] -1    0    0xfaffb800 - 0xfaffbfff (0x800) MX[B]
    [2] -1    0    0xfaffc000 - 0xfaffdfff (0x2000) MX[B]
    [3] -1    0    0xfaffe000 - 0xfaffffff (0x2000) MX[B]
    [4] -1    0    0xf4fff400 - 0xf4fff4ff (0x100) MX[B]
    [5] -1    0    0xf4fff800 - 0xf4fff9ff (0x200) MX[B]
    [6] -1    0    0x50000000 - 0x500003ff (0x400) MX[B]
    [7] -1    0    0xf4fffc00 - 0xf4ffffff (0x400) MX[B]
    [8] -1    0    0xe0000000 - 0xdfffffff (0x0) MX[B]O
    [9] -1    0    0xfcff0000 - 0xfcffffff (0x10000) MX[B](B)
    [10] -1    0    0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
    [11] -1    0    0x0000b080 - 0x0000b0ff (0x80) IX[B]
    [12] -1    0    0x0000b400 - 0x0000b4ff (0x100) IX[B]
    [13] -1    0    0x0000bc40 - 0x0000bc7f (0x40) IX[B]
    [14] -1    0    0x0000b800 - 0x0000b8ff (0x100) IX[B]
    [15] -1    0    0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
    [16] -1    0    0x00000374 - 0x00000374 (0x1) IX[B]
    [17] -1    0    0x00000170 - 0x00000177 (0x8) IX[B]
    [18] -1    0    0x000003f4 - 0x000003f4 (0x1) IX[B]
    [19] -1    0    0x000001f0 - 0x000001f7 (0x8) IX[B]
    [20] -1    0    0x0000bf20 - 0x0000bf3f (0x20) IX[B]
    [21] -1    0    0x0000bf40 - 0x0000bf5f (0x20) IX[B]
    [22] -1    0    0x0000bf80 - 0x0000bf9f (0x20) IX[B]
    [23] -1    0    0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0xfaff4000 - 0xfaff7fff (0x4000) MX[B]
    [5] -1    0    0xfaffb800 - 0xfaffbfff (0x800) MX[B]
    [6] -1    0    0xfaffc000 - 0xfaffdfff (0x2000) MX[B]
    [7] -1    0    0xfaffe000 - 0xfaffffff (0x2000) MX[B]
    [8] -1    0    0xf4fff400 - 0xf4fff4ff (0x100) MX[B]
    [9] -1    0    0xf4fff800 - 0xf4fff9ff (0x200) MX[B]
    [10] -1    0    0x50000000 - 0x500003ff (0x400) MX[B]
    [11] -1    0    0xf4fffc00 - 0xf4ffffff (0x400) MX[B]
    [12] -1    0    0xe0000000 - 0xdfffffff (0x0) MX[B]O
    [13] -1    0    0xfcff0000 - 0xfcffffff (0x10000) MX[B](B)
    [14] -1    0    0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
    [15] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [16] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
    [17] -1    0    0x0000b080 - 0x0000b0ff (0x80) IX[B]
    [18] -1    0    0x0000b400 - 0x0000b4ff (0x100) IX[B]
    [19] -1    0    0x0000bc40 - 0x0000bc7f (0x40) IX[B]
    [20] -1    0    0x0000b800 - 0x0000b8ff (0x100) IX[B]
    [21] -1    0    0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
    [22] -1    0    0x00000374 - 0x00000374 (0x1) IX[B]
    [23] -1    0    0x00000170 - 0x00000177 (0x8) IX[B]
    [24] -1    0    0x000003f4 - 0x000003f4 (0x1) IX[B]
    [25] -1    0    0x000001f0 - 0x000001f7 (0x8) IX[B]
    [26] -1    0    0x0000bf20 - 0x0000bf3f (0x20) IX[B]
    [27] -1    0    0x0000bf40 - 0x0000bf5f (0x20) IX[B]
    [28] -1    0    0x0000bf80 - 0x0000bf9f (0x20) IX[B]
    [29] -1    0    0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
    ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
    compiled for 1.4.0.90, module version = 2.1.0
    Module class: X.Org Font Renderer
    ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
    ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 6.8.0
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 4.3.0
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
    compiled for 4.3.99.902, module version = 1.0.0
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
    compiled for 1.4.0, module version = 1.2.3
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
    compiled for 1.4.0, module version = 1.2.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 2.0
(II) RADEON: Driver for ATI Radeon chipsets:
    ATI Radeon Mobility X600 (M24) 3150 (PCIE),
    ATI Radeon Mobility X300 (M24) 3152 (PCIE),
    ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X600 (RV380) 3E50 (PCIE),
    ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
    ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
    ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
    ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
    ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
    ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
    ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
    ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
    ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
    ATI Radeon 8500 AIW BB (AGP), ATI Radeon 8500 AIW BC (AGP),
    ATI Radeon IGP320M (U1) 4336, ATI Radeon IGP330M/340M/350M (U2) 4337,
    ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
    ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
    ATI Radeon X800PRO (R420) JI (AGP),
    ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
    ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
    ATI Radeon Mobility 9800 (M18) JN (AGP),
    ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
    ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
    ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
    ATI Radeon Mobility M7 LW (AGP),
    ATI Mobility FireGL 7800 M7 LX (AGP),
    ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
    ATI FireGL Mobility 9000 (M9) Ld (AGP),
    ATI Radeon Mobility 9000 (M9) Lf (AGP),
    ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI Radeon 9700 Pro ND (AGP),
    ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
    ATI FireGL X1 NG (AGP), ATI Radeon 9800PRO NH (AGP),
    ATI Radeon 9800 NI (AGP), ATI FireGL X2 NK (AGP),
    ATI Radeon 9800XT NJ (AGP),
    ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
    ATI Radeon Mobility 9600 (M10) NQ (AGP),
    ATI Radeon Mobility 9600 (M11) NR (AGP),
    ATI Radeon Mobility 9600 (M10) NS (AGP),
    ATI FireGL Mobility T2 (M10) NT (AGP),
    ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
    ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
    ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
    ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
    ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
    ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
    ATI Radeon Mobility X300 (M22) 5460 (PCIE),
    ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
    ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
    ATI Radeon X800PRO (R423) UI (PCIE),
    ATI Radeon X800LE (R423) UJ (PCIE),
    ATI Radeon X800SE (R423) UK (PCIE),
    ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
    ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
    ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
    ATI FireGL unknown (R423) UR (PCIE),
    ATI FireGL unknown (R423) UT (PCIE),
    ATI Mobility FireGL V5000 (M26) (PCIE),
    ATI Mobility FireGL V5000 (M26) (PCIE),
    ATI Mobility Radeon X700 XL (M26) (PCIE),
    ATI Mobility Radeon X700 (M26) (PCIE),
    ATI Mobility Radeon X700 (M26) (PCIE), ATI Radeon 9100 IGP (A5) 5834,
    ATI Radeon Mobility 9100 IGP (U3) 5835,
    ATI Radeon XPRESS 200 5954 (PCIE),
    ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
    ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
    ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
    ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
    ATI Radeon XPRESS 200M 5975 (PCIE),
    ATI Radeon XPRESS 200 5A41 (PCIE),
    ATI Radeon XPRESS 200M 5A42 (PCIE),
    ATI Radeon XPRESS 200 5A61 (PCIE),
    ATI Radeon XPRESS 200M 5A62 (PCIE),
    ATI Radeon X300 (RV370) 5B60 (PCIE),
    ATI Radeon X600 (RV370) 5B62 (PCIE),
    ATI Radeon X550 (RV370) 5B63 (PCIE),
    ATI Radeon X550XTX (RV370) 5657 (PCIE),
    ATI FireGL V3100 (RV370) 5B64 (PCIE),
    ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
    ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
    ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
    ATI Mobility Radeon X800 XT (M28) (PCIE),
    ATI Mobility FireGL V5100 (M28) (PCIE),
    ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
    ATI Radeon X850 XT PE (R480) (PCIE),
    ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
    ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
    ATI Radeon X850 XT (R480) (PCIE),
    ATI Radeon X800XT (R423) 5D57 (PCIE),
    ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
    ATI Radeon X700 PRO (RV410) (PCIE),
    ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
    ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
    ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
    ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
    ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
    ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
    ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
    ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
    ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
    ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
    ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
    ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
    ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
    ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
    ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
    ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
    ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
    ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
    ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
    ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
    ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
    ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
    ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
    ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
    ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
    ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
    ATI Mobility Radeon X1700, ATI  Radeon X2300HD,
    ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
    ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
    ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
    ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI ATI FireGL V7400,
    ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
    ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
    ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
    ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
    ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
    ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600, ATI RV610,
    ATI Radeon HD 2400 XT, ATI Radeon HD 2400 Pro,
    ATI ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000, ATI RV610,
    ATI ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
    ATI Mobility Radeon HD 2400, ATI ATI RADEON E2400, ATI RV610,
    ATI RV670, ATI Radeon HD3870, ATI Radeon HD3850, ATI RV670,
    ATI Radeon HD3870 X2, ATI FireGL V7700, ATI RV630,
    ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
    ATI ATI Radeon HD 2600 XT AGP, ATI ATI Radeon HD 2600 Pro AGP,
    ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
    ATI Gemini ATI Mobility Radeon HD 2600 XT, ATI FireGL V5600,
    ATI FireGL V3600, ATI ATI Radeon HD 2600 LE
(II) Primary Device is: PCI 01:00:0
(--) Chipset ATI Radeon Mobility M7 LW (AGP) found
(II) resource ranges after xf86ClaimFixedResources() call:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0xfaff4000 - 0xfaff7fff (0x4000) MX[B]
    [5] -1    0    0xfaffb800 - 0xfaffbfff (0x800) MX[B]
    [6] -1    0    0xfaffc000 - 0xfaffdfff (0x2000) MX[B]
    [7] -1    0    0xfaffe000 - 0xfaffffff (0x2000) MX[B]
    [8] -1    0    0xf4fff400 - 0xf4fff4ff (0x100) MX[B]
    [9] -1    0    0xf4fff800 - 0xf4fff9ff (0x200) MX[B]
    [10] -1    0    0x50000000 - 0x500003ff (0x400) MX[B]
    [11] -1    0    0xf4fffc00 - 0xf4ffffff (0x400) MX[B]
    [12] -1    0    0xe0000000 - 0xdfffffff (0x0) MX[B]O
    [13] -1    0    0xfcff0000 - 0xfcffffff (0x10000) MX[B](B)
    [14] -1    0    0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
    [15] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [16] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
    [17] -1    0    0x0000b080 - 0x0000b0ff (0x80) IX[B]
    [18] -1    0    0x0000b400 - 0x0000b4ff (0x100) IX[B]
    [19] -1    0    0x0000bc40 - 0x0000bc7f (0x40) IX[B]
    [20] -1    0    0x0000b800 - 0x0000b8ff (0x100) IX[B]
    [21] -1    0    0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
    [22] -1    0    0x00000374 - 0x00000374 (0x1) IX[B]
    [23] -1    0    0x00000170 - 0x00000177 (0x8) IX[B]
    [24] -1    0    0x000003f4 - 0x000003f4 (0x1) IX[B]
    [25] -1    0    0x000001f0 - 0x000001f7 (0x8) IX[B]
    [26] -1    0    0x0000bf20 - 0x0000bf3f (0x20) IX[B]
    [27] -1    0    0x0000bf40 - 0x0000bf5f (0x20) IX[B]
    [28] -1    0    0x0000bf80 - 0x0000bf9f (0x20) IX[B]
    [29] -1    0    0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
(II) resource ranges after probing:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0xfaff4000 - 0xfaff7fff (0x4000) MX[B]
    [5] -1    0    0xfaffb800 - 0xfaffbfff (0x800) MX[B]
    [6] -1    0    0xfaffc000 - 0xfaffdfff (0x2000) MX[B]
    [7] -1    0    0xfaffe000 - 0xfaffffff (0x2000) MX[B]
    [8] -1    0    0xf4fff400 - 0xf4fff4ff (0x100) MX[B]
    [9] -1    0    0xf4fff800 - 0xf4fff9ff (0x200) MX[B]
    [10] -1    0    0x50000000 - 0x500003ff (0x400) MX[B]
    [11] -1    0    0xf4fffc00 - 0xf4ffffff (0x400) MX[B]
    [12] -1    0    0xe0000000 - 0xdfffffff (0x0) MX[B]O
    [13] -1    0    0xfcff0000 - 0xfcffffff (0x10000) MX[B](B)
    [14] -1    0    0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
    [15] 0    0    0x000a0000 - 0x000affff (0x10000) MS[B]
    [16] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[B]
    [17] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[B]
    [18] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [19] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
    [20] -1    0    0x0000b080 - 0x0000b0ff (0x80) IX[B]
    [21] -1    0    0x0000b400 - 0x0000b4ff (0x100) IX[B]
    [22] -1    0    0x0000bc40 - 0x0000bc7f (0x40) IX[B]
    [23] -1    0    0x0000b800 - 0x0000b8ff (0x100) IX[B]
    [24] -1    0    0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
    [25] -1    0    0x00000374 - 0x00000374 (0x1) IX[B]
    [26] -1    0    0x00000170 - 0x00000177 (0x8) IX[B]
    [27] -1    0    0x000003f4 - 0x000003f4 (0x1) IX[B]
    [28] -1    0    0x000001f0 - 0x000001f7 (0x8) IX[B]
    [29] -1    0    0x0000bf20 - 0x0000bf3f (0x20) IX[B]
    [30] -1    0    0x0000bf40 - 0x0000bf5f (0x20) IX[B]
    [31] -1    0    0x0000bf80 - 0x0000bf9f (0x20) IX[B]
    [32] -1    0    0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
    [33] 0    0    0x000003b0 - 0x000003bb (0xc) IS[B]
    [34] 0    0    0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) RADEON(0): MMIO registers at 0x00000000fcff0000: size 64KB
(II) RADEON(0): PCI bus 1 card 0 func 0
(**) RADEON(0): Depth 24, (--) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 0.1.0
    ABI class: X.Org Video Driver, version 2.0
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
    ABI class: X.Org Video Driver, version 2.0
(II) RADEON(0): initializing int10
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(--) RADEON(0): Chipset: "ATI Radeon Mobility M7 LW (AGP)" (ChipID = 0x4c57)
(--) RADEON(0): Linear framebuffer at 0x00000000e8000000
(II) RADEON(0): AGP card detected
(II) RADEON(0): Legacy BIOS detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) RADEON(0): [dri] Found DRI library version 1.3.0 and kernel module version 1.28.0
(==) RADEON(0): Page Flipping disabled
(II) RADEON(0): Will try to use DMA for Xv image transfers
(II) RADEON(0): Detected total video RAM=16384K, accessible=65536K (PCI BAR=131072K)
(--) RADEON(0): Mapped VideoRAM: 16384 kByte (64 bit DDR SDRAM)
(II) RADEON(0): Color tiling enabled by default
(II) RADEON(0): Max desktop size set to 1600x1200
(II) RADEON(0): For a larger or smaller max desktop size, add a Virtual line to your xorg.conf
(II) RADEON(0): If you are having trouble with 3D, reduce the desktop size by adjusting the Virtual line to your xorg.conf
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module "i2c" already built-in
(II) RADEON(0): ref_freq: 2700, min_out_pll: 20000, max_out_pll: 35000, min_in_pll: 40, max_in_pll: 3000, xclk: 18000, sclk: 180.000000, mclk: 230.000000
(II) RADEON(0): PLL parameters: rf=2700 rd=12 min=20000 max=35000; xclk=18000
(II) RADEON(0): Bios Connector table: 
(II) RADEON(0): Port0: DDCType-0x60, DACType-1, TMDSType-1, ConnectorType-1
(II) RADEON(0): Port4: DDCType-0x0, DACType-0, TMDSType-0, ConnectorType-7
(II) RADEON(0): Port5: DDCType-0x0, DACType-2, TMDSType-0, ConnectorType-5
(II) RADEON(0): Output VGA-0 using monitor section Generic Monitor
(II) RADEON(0): I2C bus "VGA-0" initialized.
(II) RADEON(0): Output LVDS has no monitor section
(II) RADEON(0): Panel ID string: IBM J1838ITSX95
       
(II) RADEON(0): Panel Size from BIOS: 1400x1050
(II) RADEON(0): BIOS provided dividers will be used.
(WW) RADEON(0): LVDS Info:
XRes: 1400, YRes: 1050, DotClock: 108000
HBlank: 288, HOverPlus: 40, HSyncWidth: 112
VBlank: 16, VOverPlus: 1, VSyncWidth: 3
(II) RADEON(0): Output S-video has no monitor section
(II) RADEON(0): Default TV standard: NTSC
(II) RADEON(0): TV standards supported by chip: NTSC PAL NTSC-J 
(II) RADEON(0): Port0:
 Monitor   -- AUTO
 Connector -- VGA
 DAC Type  -- Primary
 TMDS Type -- None
 DDC Type  -- 0x60
(II) RADEON(0): Port1:
 Monitor   -- AUTO
 Connector -- LVDS
 DAC Type  -- None
 TMDS Type -- None
 DDC Type  -- 0x0
(II) RADEON(0): Port2:
 Monitor   -- AUTO
 Connector -- STV
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- None
 DDC Type  -- 0x0
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
finished output detect: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 2
finished output detect: 1
finished output detect: 2
finished all detect
before xf86InitialConfiguration
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 2
in RADEONProbeOutputModes
(II) RADEON(0): Added native panel mode: 1400x1050
(II) RADEON(0): Adding Screen mode: 1024x768
(II) RADEON(0): Total number of valid Screen mode(s) added: 1
(II) RADEON(0): Output VGA-0 disconnected
(II) RADEON(0): Output LVDS connected
(II) RADEON(0): Output S-video disconnected
(II) RADEON(0): Output LVDS using initial mode 1400x1050
after xf86InitialConfiguration
(==) RADEON(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.3
(==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(==) RADEON(0): Using XAA acceleration architecture
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.2.0
    ABI class: X.Org Video Driver, version 2.0
(==) RADEON(0): Assuming overlay scaler buffer width is 1536
(II) RADEON(0): No MM_TABLE found - assuming CARD is not TV-in capable.
(!!) RADEON(0): For information on using the multimedia capabilities
    of this adapter, please see http://gatos.sf.net.
(!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] 0    0    0xfcff0000 - 0xfcffffff (0x10000) MX[B]
    [1] 0    0    0xe8000000 - 0xefffffff (0x8000000) MX[B]
    [2] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [3] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [4] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [5] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [6] -1    0    0xfaff4000 - 0xfaff7fff (0x4000) MX[B]
    [7] -1    0    0xfaffb800 - 0xfaffbfff (0x800) MX[B]
    [8] -1    0    0xfaffc000 - 0xfaffdfff (0x2000) MX[B]
    [9] -1    0    0xfaffe000 - 0xfaffffff (0x2000) MX[B]
    [10] -1    0    0xf4fff400 - 0xf4fff4ff (0x100) MX[B]
    [11] -1    0    0xf4fff800 - 0xf4fff9ff (0x200) MX[B]
    [12] -1    0    0x50000000 - 0x500003ff (0x400) MX[B]
    [13] -1    0    0xf4fffc00 - 0xf4ffffff (0x400) MX[B]
    [14] -1    0    0xe0000000 - 0xdfffffff (0x0) MX[B]O
    [15] -1    0    0xfcff0000 - 0xfcffffff (0x10000) MX[B](B)
    [16] -1    0    0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
    [17] 0    0    0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
    [18] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
    [19] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
    [20] 0    0    0x0000c000 - 0x0000c0ff (0x100) IX[B]
    [21] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [22] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
    [23] -1    0    0x0000b080 - 0x0000b0ff (0x80) IX[B]
    [24] -1    0    0x0000b400 - 0x0000b4ff (0x100) IX[B]
    [25] -1    0    0x0000bc40 - 0x0000bc7f (0x40) IX[B]
    [26] -1    0    0x0000b800 - 0x0000b8ff (0x100) IX[B]
    [27] -1    0    0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
    [28] -1    0    0x00000374 - 0x00000374 (0x1) IX[B]
    [29] -1    0    0x00000170 - 0x00000177 (0x8) IX[B]
    [30] -1    0    0x000003f4 - 0x000003f4 (0x1) IX[B]
    [31] -1    0    0x000001f0 - 0x000001f7 (0x8) IX[B]
    [32] -1    0    0x0000bf20 - 0x0000bf3f (0x20) IX[B]
    [33] -1    0    0x0000bf40 - 0x0000bf5f (0x20) IX[B]
    [34] -1    0    0x0000bf80 - 0x0000bf9f (0x20) IX[B]
    [35] -1    0    0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
    [36] 0    0    0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
    [37] 0    0    0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) RADEON(0): RADEONScreenInit e8000000 0 0
(==) RADEON(0): Write-combining range (0xe8000000,0x1000000)
Entering TV Save
Save TV timing tables
saveTimingTables: reading timing tables
TV Save done
disable montype: 2
(II) RADEON(0): Dynamic Clock Scaling Disabled
(==) RADEON(0): Using 24 bit depth buffer
(II) RADEON(0): RADEONInitMemoryMap() : 
(II) RADEON(0):   mem_size         : 0x04000000
(II) RADEON(0):   MC_FB_LOCATION   : 0xebffe800
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(II) RADEON(0): Depth moves disabled by default
(II) RADEON(0): CP in BM mode
(II) RADEON(0): Using 8 MB GART aperture
(II) RADEON(0): Using 1 MB for the ring buffer
(II) RADEON(0): Using 2 MB for vertex/indirect buffers
(II) RADEON(0): Using 5 MB for GART textures
(II) RADEON(0): Memory manager initialized to (0,0) (1408,2978)
(II) RADEON(0): Reserved area from (0,1200) to (1408,1202)
(II) RADEON(0): Largest offscreen area available: 1408 x 1776
(II) RADEON(0): Will use front buffer at offset 0x0
(II) RADEON(0): Will use back buffer at offset 0x318000
(II) RADEON(0): Will use depth buffer at offset 0x98a000
(II) RADEON(0): Will use 0 kb for textures at offset 0xffc000
(EE) RADEON(0): Static buffer allocation failed.  Disabling DRI.
(EE) RADEON(0): At least 19800 kB of video memory needed at this resolution and depth.
disable montype: 2
init memmap
init common
init crtc1
init pll1
restore memmap
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xebffe800 0x1fff0000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
restore common
restore crtc1
restore pll1
restore LVDS
enable montype: 2
(WW) RADEON(0): No crtc mode list for crtc 1,continuing with desired mode
disable montype: 2
(==) RADEON(0): Backing store disabled
(WW) RADEON(0): Direct rendering disabled
(II) RADEON(0): Render acceleration enabled
(**) RADEON(0): Option "XaaNoOffscreenPixmaps"
(II) RADEON(0): Using XFree86 Acceleration Architecture (XAA)
    Screen to screen bit blits
    Solid filled rectangles
    8x8 mono pattern filled rectangles
    Indirect CPU to Screen color expansion
    Solid Lines
    Scanline Image Writes
    Setting up tile and stipple cache:
        32 128x128 slots
        11 256x256 slots
        4 512x512 slots
(II) RADEON(0): Acceleration enabled
(**) Option "dpms"
(**) RADEON(0): DPMS enabled
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Using hardware cursor 0 (scanline 1202)
(II) RADEON(0): Using hardware cursor 1 (scanline 1204)
(II) RADEON(0): Largest offscreen area available: 1408 x 1770
(II) RADEON(0): Detected Radeon Mobility M7, disabling multimedia i2c
(II) Loading sub module "theatre_detect"
(II) LoadModule: "theatre_detect"
(II) Loading /usr/lib/xorg/modules/multimedia//theatre_detect_drv.so
(II) Module theatre_detect: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
    ABI class: X.Org Video Driver, version 2.0
(II) RADEON(0): no multimedia table present, disabling Rage Theatre.
(II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(--) RandR disabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) AIGLX: Screen 0 is not DRI capable
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
    ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(II) RADEON(0): Setting screen physical size to 370 x 277
Atom 4, CARD32 4, unsigned long 4
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event10
(**) Option "Device" "/dev/input/event10"
(**) Option "HorizEdgeScroll" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) evaluating device (Synaptics Touchpad)
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event10
(**) Option "Device" "/dev/input/event10"
(--) Synaptics Touchpad touchpad found
enable montype: 2
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 2
in RADEONProbeOutputModes
(II) RADEON(0): Added native panel mode: 1400x1050
(II) RADEON(0): Adding Screen mode: 1024x768
(II) RADEON(0): Total number of valid Screen mode(s) added: 1
SetClientVersion: 0 9
SetKbdSettings - type: -1081234532 rate: 30 delay: 500 snumlk: 236
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 2
in RADEONProbeOutputModes
(II) RADEON(0): Added native panel mode: 1400x1050
(II) RADEON(0): Adding Screen mode: 1024x768
(II) RADEON(0): Total number of valid Screen mode(s) added: 1
enable montype: 2
enable montype: 2
enable montype: 2
enable montype: 2
enable montype: 2
disable montype: 2
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x1fff0000 0xebffe800
(II) RADEON(0):   MC_AGP_LOCATION  : 0x27ff2000
finished PLL2
Entering Restore TV
Restore TV PLL
Restore TVHV
Restore TV Restarts
Restore Timing Tables
Restore TV standard
Leaving Restore TV
(II) Open ACPI successful (/var/run/acpid.socket)
disable montype: 2
init memmap
init common
init crtc1
init pll1
restore memmap
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xebffe800 0x1fff0000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
restore common
restore crtc1
restore pll1
restore LVDS
enable montype: 2
enable montype: 2
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event10
(**) Option "Device" "/dev/input/event10"
(--) Synaptics Touchpad touchpad found
enable montype: 2
enable montype: 2
enable montype: 2
enable montype: 2
enable montype: 2
enable montype: 2
enable montype: 2
enable montype: 2
enable montype: 2
enable montype: 2
enable montype: 2
enable montype: 2
enable montype: 2
enable montype: 2
disable montype: 2
disable montype: 2
enable montype: 2
enable montype: 2

```

---

### Post by Yellow Pasque on 2009-06-20
> (EE) RADEON(0): Static buffer allocation failed.  Disabling DRI.
(EE) RADEON(0): **At least 19800 kB of video memory needed at this resolution and depth**.


You either need to try a lower resolution or use Depth 16 instead of Depth 24

---

### Post by rvgsd on 2009-06-20
Got it! Thanks for the help Temujin!

rvgsd.

---

### Post by rvgsd on 2009-07-18
Still no luck! 
It would be great if anyone who has Inspiron 5100 and is able to run Compiz, could post there Xorg.conf here..!

---

