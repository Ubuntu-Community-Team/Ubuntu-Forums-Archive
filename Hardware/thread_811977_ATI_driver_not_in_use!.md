---
title: "ATI driver not in use!"
date: 2008-05-29
forum: Hardware
---

### Post by spacegypsy on 2008-05-29
I upgraded from 7.10 to 8.04, most thing worked flawless. :)

Only one thing keeps me from getting my old look & feel of my previous desktop;

I can't set the ATI driver "In use"

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=72065&stc=1&d=1212085756[/IMG]

I've been trying installing the driver with "Hardware Drivers" and "EnvyNG" with the same result. :(

Then I tried to solve the problem following these pages;

[https://bugs.launchpad.net/ubuntu/+bug/224130](https://bugs.launchpad.net/ubuntu/+bug/224130)

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

I removed the "Mesa drivers" but the output of fglrxinfo after removing the xserver-xgl package still shows Mesa; 

> spacegypsy@void:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)

spacegypsy@void:~$ 

[This page]("http://ubuntuforums.org/archive/index.php/t-770351.html") says that there is no solution for the moment, or is there?

Output of glxinfo:

> spacegypsy@void:~$ glxinfo
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
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, 
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_EXT_texture_from_pixmap
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
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
0x3d 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon
spacegypsy@void:~$ 

Any advise?

---

### Post by graham-cracker on 2008-05-29
what does 
```
lsmod | grep fglrx
```
give you?

Or how about:
```
grep fglrx /etc/X11/xorg.conf
```

I just got through trying to setup fglrx in Hardy and I think I may have added it manually to my xorg.conf file (after several attempts with ati-config).

---

### Post by spacegypsy on 2008-05-29
grep fglrx /etc/X11/xorg.conf gives:

> spacegypsy@void:~$ grep fglrx /etc/X11/xorg.conf
	Driver      "fglrx"
spacegypsy@void:~$ 

lsmod | grep fglrx gives: nothing :confused:

> spacegypsy@void:~$ lsmod | grep fglrx
spacegypsy@void:~$ 

---

### Post by graham-cracker on 2008-05-29
Hmm, looks like the fglrx module is not getting loaded. What does this give you:
```
grep fglrx /var/log/Xorg.0.log
```
Also, just to check if fglrx is present try this:
```
modprobe -l | grep fglrx
```
Have you restarted since enabling fglrx?

---

### Post by spacegypsy on 2008-05-29
grep fglrx /var/log/Xorg.0.log :

> spacegypsy@void:~$ grep fglrx /var/log/Xorg.0.log
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
(II) fglrx(0): pEnt->device->identifier=0x820eef0
(II) fglrx(0): === [atiddxPreInit] === begin
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "DPMS" "true"
(II) fglrx(0): Loading PCS database from /etc/ati/amdpcsdb
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(--) fglrx(0): Chipset: "ATI MOBILITY RADEON X700" (Chipset = 0x5653)
(--) fglrx(0): (PciSubVendor = 0x1025, PciSubDevice = 0x0066)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
(--) fglrx(0): MMIO registers at 0xc8100000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 9.10
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2003, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: M26-P
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
(WW) fglrx(0): Failed to open DRM connection
(--) fglrx(0): VideoRAM: 131072 kByte, Type: DDR1
(II) fglrx(0): PCIE card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) fglrx(0): Connected Display1: LCD on internal LVDS [lvds]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: LGP  Model: 0  Serial#: 0
(II) fglrx(0): Year: 2003  Week: 0
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 33  vert.: 21
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): No DPMS capabilities specified; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.000 redY: 0.000   greenX: 0.000 greenY: 0.000
(II) fglrx(0): blueX: 0.000 blueY: 0.000   whiteX: 0.000 whiteY: 0.000
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 68.9 MHz   Image Size:  331 x 207 mm
(II) fglrx(0): h_active: 1280  h_sync: 1301  h_sync_end 1333 h_blank_end 1408 h_border: 0
(II) fglrx(0): v_active: 800  v_sync: 804  v_sync_end 808 v_blanking: 816 v_border: 0
(II) fglrx(0):  LP154W01-A3K3
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff0030f0000000000000
(II) fglrx(0): 	000d0103802115780a00000000000000
(II) fglrx(0): 	00000000000001010101010101010101
(II) fglrx(0): 	010101010101ea1a0080502010301520
(II) fglrx(0): 	44004bcf100000190000000f00000000
(II) fglrx(0): 	0000000000324a041400000000100000
(II) fglrx(0): 	000000000000000000000000000000fe
(II) fglrx(0): 	004c503135345730312d41334b3300df
(II) fglrx(0): End of Display1 EDID data --------------------
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
(II) fglrx(0): Primary Controller - LCD on internal LVDS
(II) fglrx(0): Internal Desktop Setting: 0x00000001
(II) fglrx(0): POWERplay version 3.  3 power states available:
(II) fglrx(0):   1. 358/344MHz @ 60Hz [enable load balancing]
(II) fglrx(0):   2. 105/120MHz @ 60Hz [low voltage, enable sleep]
(II) fglrx(0):   3. 209/182MHz @ 60Hz [low voltage, enable sleep]
(==) fglrx(0): Qbs is not supported in this release. Disabled.
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 14 modes found for primary display.
(--) fglrx(0): Virtual size is 1280x800 (pitch 0)
(**) fglrx(0): *Mode "1280x800": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x800"x60.0   68.90  1280 1301 1333 1408  800 804 808 816 +hsync +vsync (48.9 kHz)
(**) fglrx(0): *Mode "1280x768": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x768"x60.0   68.90  1280 1301 1333 1408  768 804 808 816 +hsync +vsync (48.9 kHz)
(**) fglrx(0): *Mode "1024x768": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"x60.0   68.90  1024 1045 1077 1408  768 804 808 816 +hsync +vsync (48.9 kHz)
(**) fglrx(0): *Mode "1024x480": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x480"x60.0   68.90  1024 1045 1077 1408  480 804 808 816 +hsync +vsync (48.9 kHz)
(**) fglrx(0): *Mode "848x480": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "848x480"x60.0   68.90  848 869 901 1408  480 804 808 816 +hsync +vsync (48.9 kHz)
(**) fglrx(0): *Mode "800x600": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"x60.0   68.90  800 821 853 1408  600 804 808 816 +hsync +vsync (48.9 kHz)
(**) fglrx(0): *Mode "720x576": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x576"x60.0   68.90  720 741 773 1408  576 804 808 816 +hsync +vsync (48.9 kHz)
(**) fglrx(0): *Mode "720x480": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"x60.0   68.90  720 741 773 1408  480 804 808 816 +hsync +vsync (48.9 kHz)
(**) fglrx(0): *Mode "640x480": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"x60.0   68.90  640 661 693 1408  480 804 808 816 +hsync +vsync (48.9 kHz)
(**) fglrx(0):  Default mode "640x400": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"x60.0   68.90  640 661 693 1408  400 804 808 816 +hsync +vsync (48.9 kHz)
(**) fglrx(0):  Default mode "512x384": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"x60.0   68.90  512 533 565 1408  384 804 808 816 +hsync +vsync (48.9 kHz)
(**) fglrx(0):  Default mode "400x300": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "400x300"x60.0   68.90  400 421 453 1408  300 804 808 816 +hsync +vsync (48.9 kHz)
(**) fglrx(0):  Default mode "320x240": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x240"x60.0   68.90  320 341 373 1408  240 804 808 816 +hsync +vsync (48.9 kHz)
(**) fglrx(0):  Default mode "320x200": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x200"x60.0   68.90  320 341 373 1408  200 804 808 816 +hsync +vsync (48.9 kHz)
(--) fglrx(0): Display dimensions: (330, 210) mm
(--) fglrx(0): DPI set to (98, 96)
(--) fglrx(0): Virtual size is 1280x800 (pitch 1280)
(**) fglrx(0): *Mode "1280x800": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x800"x60.0   68.90  1280 1301 1333 1408  800 804 808 816 +hsync +vsync (48.9 kHz)
(**) fglrx(0): *Mode "1280x768": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x768"x60.0   68.90  1280 1301 1333 1408  768 804 808 816 +hsync +vsync (48.9 kHz)
(**) fglrx(0): *Mode "1024x768": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"x60.0   68.90  1024 1045 1077 1408  768 804 808 816 +hsync +vsync (48.9 kHz)
(**) fglrx(0): *Mode "1024x480": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x480"x60.0   68.90  1024 1045 1077 1408  480 804 808 816 +hsync +vsync (48.9 kHz)
(**) fglrx(0): *Mode "848x480": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "848x480"x60.0   68.90  848 869 901 1408  480 804 808 816 +hsync +vsync (48.9 kHz)
(**) fglrx(0): *Mode "800x600": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"x60.0   68.90  800 821 853 1408  600 804 808 816 +hsync +vsync (48.9 kHz)
(**) fglrx(0): *Mode "720x576": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x576"x60.0   68.90  720 741 773 1408  576 804 808 816 +hsync +vsync (48.9 kHz)
(**) fglrx(0): *Mode "720x480": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"x60.0   68.90  720 741 773 1408  480 804 808 816 +hsync +vsync (48.9 kHz)
(**) fglrx(0): *Mode "640x480": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"x60.0   68.90  640 661 693 1408  480 804 808 816 +hsync +vsync (48.9 kHz)
(**) fglrx(0):  Default mode "640x400": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"x60.0   68.90  640 661 693 1408  400 804 808 816 +hsync +vsync (48.9 kHz)
(**) fglrx(0):  Default mode "512x384": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"x60.0   68.90  512 533 565 1408  384 804 808 816 +hsync +vsync (48.9 kHz)
(**) fglrx(0):  Default mode "400x300": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "400x300"x60.0   68.90  400 421 453 1408  300 804 808 816 +hsync +vsync (48.9 kHz)
(**) fglrx(0):  Default mode "320x240": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x240"x60.0   68.90  320 341 373 1408  240 804 808 816 +hsync +vsync (48.9 kHz)
(**) fglrx(0):  Default mode "320x200": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x200"x60.0   68.90  320 341 373 1408  200 804 808 816 +hsync +vsync (48.9 kHz)
(==) fglrx(0): NoAccel = NO
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x8000001d
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): ATI GART size: 256 MB
(WW) fglrx(0): No DRM connection for driver fglrx.
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(WW) fglrx(0): could not detect X server version (query_status=-3)
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xc0000000 FBMappedSize: 0x08000000
(==) fglrx(0): Write-combining range (0xd0000000,0x8000000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,800) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1280 x 7391
(==) fglrx(0): Backing store disabled
(**) fglrx(0): DPMS enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
(II) fglrx(0): Acceleration enabled
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(II) fglrx(0): Direct rendering disabled
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using hardware cursor
spacegypsy@void:~$ 


modprobe -l | grep fglrx :

> spacegypsy@void:~$ modprobe -l | grep fglrx
/lib/modules/2.6.24-17-rt/volatile/fglrx.ko
spacegypsy@void:~$ 

and yes I've restarted several times, but will do it again to make sure.

---

### Post by mats-palats on 2008-05-29
Hi!

Maybe you can help me too here. I've got the same problem on an almost identical computer setup.
Here are my outputs:

```
delirium@delirium-laptop:~$ fglrxinfo
display: :1.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (2.1 Mesa 7.0.3)

delirium@delirium-laptop:~$ lsmod | grep fglrx
fglrx                1674892  37 
agpgart                34760  2 fglrx,intel_agp
delirium@delirium-laptop:~$ grep fglrx /etc/X11/xorg.conf
#	Driver		"fglrx"
	Driver      "fglrx"
delirium@delirium-laptop:~$ modprobe -l | grep fglrx
/lib/modules/2.6.24-17-generic/updates/dkms/fglrx.ko
delirium@delirium-laptop:~$ grep fglrx /var/log/Xorg.0.log
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
(II) fglrx(0): pEnt->device->identifier=0x820c650
(II) fglrx(0): === [atiddxPreInit] === begin
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "DPMS" "true"
(II) fglrx(0): PCS database file /etc/ati/amdpcsdb not found
(II) fglrx(0):   Creating PCS database from initial defaults instead
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(--) fglrx(0): Chipset: "ATI MOBILITY RADEON X700" (Chipset = 0x5653)
(--) fglrx(0): (PciSubVendor = 0x1025, PciSubDevice = 0x007f)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0x90000000
(--) fglrx(0): MMIO registers at 0xc0000000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 9.10
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: M26-P
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
(II) fglrx(0): Using adapter: 1:0.0.
(II) fglrx(0): [FB] Find the MC FB aperturs range(MCFBBase = 0xc0000000, MCFBSize = 0x10000000)
(--) fglrx(0): VideoRAM: 131072 kByte, Type: DDR1
(II) fglrx(0): PCIE card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) fglrx(0): Connected Display1: LCD on internal LVDS [lvds]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: LPL  Model: 0  Serial#: 0
(II) fglrx(0): Year: 2005  Week: 0
(II) fglrx(0): EDID Version: 1.2
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 37  vert.: 23
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): No DPMS capabilities specified; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.596 redY: 0.344   greenX: 0.320 greenY: 0.551
(II) fglrx(0): blueX: 0.160 blueY: 0.146   whiteX: 0.312 whiteY: 0.328
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 96.2 MHz   Image Size:  367 x 230 mm
(II) fglrx(0): h_active: 1440  h_sync: 1504  h_sync_end 1536 h_blank_end 1760 h_border: 0
(II) fglrx(0): v_active: 900  v_sync: 903  v_sync_end 906 v_blanking: 912 v_border: 0
(II) fglrx(0):  LGPhilipsLCD
(II) fglrx(0):  LP171WP5-TL03
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff00320c000000000000
(II) fglrx(0): 	000f0102802517780a80109858528d29
(II) fglrx(0): 	25505400000001010101010101010101
(II) fglrx(0): 	0101010101019525a04051840c304020
(II) fglrx(0): 	33006fe6100000180000000000000000
(II) fglrx(0): 	00000000000000000000000000fe004c
(II) fglrx(0): 	475068696c6970734c43440a000000fe
(II) fglrx(0): 	004c503137315750352d544c303300d6
(II) fglrx(0): End of Display1 EDID data --------------------
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
(II) fglrx(0): Primary Controller - LCD on internal LVDS
(II) fglrx(0): Internal Desktop Setting: 0x00000001
(II) fglrx(0): POWERplay version 3.  4 power states available:
(II) fglrx(0):   1. 358/331MHz @ 60Hz [enable load balancing]
(II) fglrx(0):   2. 105/120MHz @ 60Hz [enable sleep]
(II) fglrx(0):   3. 209/182MHz @ 60Hz [enable sleep]
(II) fglrx(0):   4. 267/331MHz @ 60Hz [enable sleep, thermal diode mode]
(==) fglrx(0): Qbs is not supported in this release. Disabled.
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 15 modes found for primary display.
(--) fglrx(0): Virtual size is 1440x900 (pitch 0)
(**) fglrx(0): *Mode "1440x900": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1440x900"x60.0   96.21  1440 1504 1536 1760  900 903 906 912 +hsync +vsync (54.7 kHz)
(**) fglrx(0): *Mode "1280x768": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x768"x60.0   96.21  1280 1344 1376 1760  768 903 906 912 +hsync +vsync (54.7 kHz)
(**) fglrx(0): *Mode "1152x864": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"x60.0   96.21  1152 1216 1248 1760  864 903 906 912 +hsync +vsync (54.7 kHz)
(**) fglrx(0): *Mode "1024x768": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"x60.0   96.21  1024 1088 1120 1760  768 903 906 912 +hsync +vsync (54.7 kHz)
(**) fglrx(0): *Mode "1024x480": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x480"x60.0   96.21  1024 1088 1120 1760  480 903 906 912 +hsync +vsync (54.7 kHz)
(**) fglrx(0): *Mode "848x480": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "848x480"x60.0   96.21  848 912 944 1760  480 903 906 912 +hsync +vsync (54.7 kHz)
(**) fglrx(0): *Mode "800x600": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"x60.0   96.21  800 864 896 1760  600 903 906 912 +hsync +vsync (54.7 kHz)
(**) fglrx(0): *Mode "720x576": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x576"x60.0   96.21  720 784 816 1760  576 903 906 912 +hsync +vsync (54.7 kHz)
(**) fglrx(0): *Mode "720x480": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"x60.0   96.21  720 784 816 1760  480 903 906 912 +hsync +vsync (54.7 kHz)
(**) fglrx(0): *Mode "640x480": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"x60.0   96.21  640 704 736 1760  480 903 906 912 +hsync +vsync (54.7 kHz)
(**) fglrx(0):  Default mode "640x400": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"x60.0   96.21  640 704 736 1760  400 903 906 912 +hsync +vsync (54.7 kHz)
(**) fglrx(0):  Default mode "512x384": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"x60.0   96.21  512 576 608 1760  384 903 906 912 +hsync +vsync (54.7 kHz)
(**) fglrx(0):  Default mode "400x300": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "400x300"x60.0   96.21  400 464 496 1760  300 903 906 912 +hsync +vsync (54.7 kHz)
(**) fglrx(0):  Default mode "320x240": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x240"x60.0   96.21  320 384 416 1760  240 903 906 912 +hsync +vsync (54.7 kHz)
(**) fglrx(0):  Default mode "320x200": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x200"x60.0   96.21  320 384 416 1760  200 903 906 912 +hsync +vsync (54.7 kHz)
(--) fglrx(0): Display dimensions: (370, 230) mm
(--) fglrx(0): DPI set to (98, 99)
(--) fglrx(0): Virtual size is 1440x900 (pitch 1472)
(**) fglrx(0): *Mode "1440x900": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1440x900"x60.0   96.21  1440 1504 1536 1760  900 903 906 912 +hsync +vsync (54.7 kHz)
(**) fglrx(0): *Mode "1280x768": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x768"x60.0   96.21  1280 1344 1376 1760  768 903 906 912 +hsync +vsync (54.7 kHz)
(**) fglrx(0): *Mode "1152x864": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"x60.0   96.21  1152 1216 1248 1760  864 903 906 912 +hsync +vsync (54.7 kHz)
(**) fglrx(0): *Mode "1024x768": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"x60.0   96.21  1024 1088 1120 1760  768 903 906 912 +hsync +vsync (54.7 kHz)
(**) fglrx(0): *Mode "1024x480": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x480"x60.0   96.21  1024 1088 1120 1760  480 903 906 912 +hsync +vsync (54.7 kHz)
(**) fglrx(0): *Mode "848x480": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "848x480"x60.0   96.21  848 912 944 1760  480 903 906 912 +hsync +vsync (54.7 kHz)
(**) fglrx(0): *Mode "800x600": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"x60.0   96.21  800 864 896 1760  600 903 906 912 +hsync +vsync (54.7 kHz)
(**) fglrx(0): *Mode "720x576": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x576"x60.0   96.21  720 784 816 1760  576 903 906 912 +hsync +vsync (54.7 kHz)
(**) fglrx(0): *Mode "720x480": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"x60.0   96.21  720 784 816 1760  480 903 906 912 +hsync +vsync (54.7 kHz)
(**) fglrx(0): *Mode "640x480": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"x60.0   96.21  640 704 736 1760  480 903 906 912 +hsync +vsync (54.7 kHz)
(**) fglrx(0):  Default mode "640x400": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"x60.0   96.21  640 704 736 1760  400 903 906 912 +hsync +vsync (54.7 kHz)
(**) fglrx(0):  Default mode "512x384": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"x60.0   96.21  512 576 608 1760  384 903 906 912 +hsync +vsync (54.7 kHz)
(**) fglrx(0):  Default mode "400x300": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "400x300"x60.0   96.21  400 464 496 1760  300 903 906 912 +hsync +vsync (54.7 kHz)
(**) fglrx(0):  Default mode "320x240": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x240"x60.0   96.21  320 384 416 1760  240 903 906 912 +hsync +vsync (54.7 kHz)
(**) fglrx(0):  Default mode "320x200": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x200"x60.0   96.21  320 384 416 1760  200 903 906 912 +hsync +vsync (54.7 kHz)
(==) fglrx(0): NoAccel = NO
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x8000001d
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): ATI GART size: 255 MB
(II) fglrx(0): [pcie] 261120 kB allocated
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 7.1.0.90
(II) fglrx(0): doing DRIScreenInit
(II) fglrx(0): [drm] Using the DRM lock SAREA also for drawables.
(II) fglrx(0): [drm] framebuffer handle = 0xe0000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.49.7
(II) fglrx(0):     Date: May 12 2008
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.24-17-generic
(II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
(II) fglrx(0):     Build-Kernel __SMP__:            yes
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0x000e2000
(II) fglrx(0): Interrupt handler installed at IRQ 16.
(II) fglrx(0): Exposed events to the /proc interface
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0xc0000000 FBMappedSize: 0x00719000
(II) fglrx(0): FBMM initialized for area (0,0)-(1472,1264)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1472,900) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1472 x 364
(==) fglrx(0): Backing store disabled
(**) fglrx(0): DPMS enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
(II) fglrx(0): Acceleration enabled
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(II) fglrx(0): [DRI] installation complete
(II) fglrx(0): Direct rendering enabled
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using hardware cursor
(II) AIGLX: Loaded and initialized /usr/lib/dri/fglrx_dri.so
delirium@delirium-laptop:~$ 
```

By the way, I DO have my proprietary driver in use. Everything works swell except that big windows make everything slow and watching a movie full screen is out of the question, it just flickers like hell!

Thanks!

---

### Post by graham-cracker on 2008-05-29
Could you post your /etc/X11/xorg.conf or the output of:
```
cat /etc/X11/xorg.conf
```

It looks like the fglrx module is being loaded by X but then fails somewhere else. Could you also post the output of:
```
grep '([WE][WE])' /var/log/Xorg.0.log
```

This is probably a shot in the dark, but you could try running:
```
sudo depmod -a
```
and then restarting. I've had it work for a few things in the past.

---

### Post by spacegypsy on 2008-05-29
cat /etc/X11/xorg.conf

> spacegypsy@void:~$ cat /etc/X11/xorg.conf

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

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "be"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizEdgeScroll" "0"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Extensions"
	Option	    "Composite" "Enable"
EndSection

spacegypsy@void:~$ 


grep '([WE][WE])' /var/log/Xorg.0.log

> spacegypsy@void:~$ grep '([WE][WE])' /var/log/Xorg.0.log
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) fglrx(0): Failed to open DRM connection
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
(WW) fglrx(0): No DRM connection for driver fglrx.
(WW) fglrx(0): could not detect X server version (query_status=-3)
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(WW) Configured Mouse: No Device specified, looking for one...
spacegypsy@void:~$ 



I think I already ran sudo depmod -a , but I'll redo it.

---

### Post by mats-palats on 2008-05-29
I'll post mine too.

xorg.conf:
```

# xorg.conf (xorg X Window System server configuration file)
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
#Section "Device"
#	Identifier	"ATI Technologies Inc Radeon Mobility X700 (PCIE)"
#	Driver		"fglrx"
#	Busid		"PCI:1:0:0"
#EndSection

Section "ServerLayout"

	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "extmod"
	Load  "glx"
	Load  "dbe"
	Load  "v4l"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "se"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizEdgeScroll" "0"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Extensions"
	Option	    "Composite" "1"
EndSection

```

```
delirium@delirium-laptop:~$ grep '([WE][WE])' /var/log/Xorg.0.log
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(WW) AIGLX: 3D driver claims to not support visual 0x33
(WW) AIGLX: 3D driver claims to not support visual 0x34
(WW) AIGLX: 3D driver claims to not support visual 0x35
(WW) AIGLX: 3D driver claims to not support visual 0x36
(WW) AIGLX: 3D driver claims to not support visual 0x37
(WW) AIGLX: 3D driver claims to not support visual 0x38
(WW) AIGLX: 3D driver claims to not support visual 0x39
(WW) AIGLX: 3D driver claims to not support visual 0x3a
(WW) AIGLX: 3D driver claims to not support visual 0x3b
(WW) AIGLX: 3D driver claims to not support visual 0x3c
(WW) AIGLX: 3D driver claims to not support visual 0x3d
(WW) AIGLX: 3D driver claims to not support visual 0x3e
(WW) AIGLX: 3D driver claims to not support visual 0x3f
(WW) AIGLX: 3D driver claims to not support visual 0x40
(WW) AIGLX: 3D driver claims to not support visual 0x41
(WW) AIGLX: 3D driver claims to not support visual 0x42
(WW) AIGLX: 3D driver claims to not support visual 0x43
(WW) AIGLX: 3D driver claims to not support visual 0x44
(WW) AIGLX: 3D driver claims to not support visual 0x45
(WW) AIGLX: 3D driver claims to not support visual 0x46
(WW) AIGLX: 3D driver claims to not support visual 0x47
(WW) AIGLX: 3D driver claims to not support visual 0x48
(WW) AIGLX: 3D driver claims to not support visual 0x49
(WW) AIGLX: 3D driver claims to not support visual 0x4a
(WW) AIGLX: 3D driver claims to not support visual 0x4b
(WW) AIGLX: 3D driver claims to not support visual 0x4c
(WW) AIGLX: 3D driver claims to not support visual 0x4d
(WW) AIGLX: 3D driver claims to not support visual 0x4e
(WW) AIGLX: 3D driver claims to not support visual 0x4f
(WW) AIGLX: 3D driver claims to not support visual 0x50
(WW) AIGLX: 3D driver claims to not support visual 0x51
(WW) AIGLX: 3D driver claims to not support visual 0x52
(WW) AIGLX: 3D driver claims to not support visual 0x53
(WW) AIGLX: 3D driver claims to not support visual 0x54
(WW) AIGLX: 3D driver claims to not support visual 0x55
(WW) AIGLX: 3D driver claims to not support visual 0x56
(WW) AIGLX: 3D driver claims to not support visual 0x57
(WW) AIGLX: 3D driver claims to not support visual 0x58
(WW) AIGLX: 3D driver claims to not support visual 0x59
(WW) AIGLX: 3D driver claims to not support visual 0x5a
(WW) AIGLX: 3D driver claims to not support visual 0x5b
(WW) AIGLX: 3D driver claims to not support visual 0x5c
(WW) AIGLX: 3D driver claims to not support visual 0x5d
(WW) AIGLX: 3D driver claims to not support visual 0x5e
(WW) AIGLX: 3D driver claims to not support visual 0x5f
(WW) AIGLX: 3D driver claims to not support visual 0x60
(WW) AIGLX: 3D driver claims to not support visual 0x61
(WW) AIGLX: 3D driver claims to not support visual 0x62
(WW) AIGLX: 3D driver claims to not support visual 0x63
(WW) AIGLX: 3D driver claims to not support visual 0x64
(WW) AIGLX: 3D driver claims to not support visual 0x65
(WW) AIGLX: 3D driver claims to not support visual 0x66
(WW) AIGLX: 3D driver claims to not support visual 0x67
(WW) AIGLX: 3D driver claims to not support visual 0x68
(WW) AIGLX: 3D driver claims to not support visual 0x69
(WW) AIGLX: 3D driver claims to not support visual 0x6a
(WW) AIGLX: 3D driver claims to not support visual 0x6b
(WW) AIGLX: 3D driver claims to not support visual 0x6c
(WW) AIGLX: 3D driver claims to not support visual 0x6d
(WW) AIGLX: 3D driver claims to not support visual 0x6e
(WW) AIGLX: 3D driver claims to not support visual 0x6f
(WW) AIGLX: 3D driver claims to not support visual 0x70
(WW) AIGLX: 3D driver claims to not support visual 0x71
(WW) AIGLX: 3D driver claims to not support visual 0x72
delirium@delirium-laptop:~$ 

```
Is that a problem?

```
sudo depmod -a
```
Something happened here, just don't know what...

---

### Post by graham-cracker on 2008-05-29
To check if the mesa drivers are still installed, you could run this:
```
dpkg -l | grep xserver-xgl
```
and also this
```
DISPLAY=:0 glxinfo | grep render
```


As far as the flickering this page
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)
states that "Note that when Visual Effects (Compiz) are active, flickering and artifacts may occur in OpenGL applications and hardware accelerated video windows (particularly with R300 chipset). To prevent this, disable Visual Effects. "

It looks like this page [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide) may have some relevant details. I'm starting to run out of ideas, although the previous page also mentions some changes you could make to your xorg.conf file.

You could try adding two option lines to the Device section of your xorg.conf file
```

Option "VideoOverlay" "on"
Option "OpenGLOverlay" "off"

```

Also, you could try disabling the composite extension, so change this
```

Section "Extensions"
Option "Composite" "Enable"
EndSection

```
to this:
```

Section "Extensions"
Option "Composite" "0"
EndSection

```

---

### Post by spacegypsy on 2008-05-29
> To check if the mesa drivers are still installed, you could run this:
Code:

dpkg -l | grep xserver-xgl

and also this
Code:

DISPLAY=:0 glxinfo | grep render

output:

> spacegypsy@void:~$ dpkg -l | grep xserver-xgl
rc  xserver-xgl                                1:1.1.99.1~git20080115-0ubuntu1                    GL-based X server
spacegypsy@void:~$ DISPLAY=:0 glxinfo | grep render
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect
spacegypsy@void:~$ 


---

### Post by graham-cracker on 2008-05-29
Going by this page [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide) you can remove the xserver-xgl:
```
sudo apt-get remove xserver-xgl
```
then restart X (and possibly the computer) to see if that helps (or at least changes the output of fglrxinfo).

---

### Post by mats-palats on 2008-05-29
That was it!

By removing xserver-xgl it all works again! Thanks! :)

```
delirium@delirium-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON X700
OpenGL version string: 2.1.7537 Release

delirium@delirium-laptop:~$ glxinfo | grep direct
direct rendering: Yes
delirium@delirium-laptop:~$ 

```

---

### Post by spacegypsy on 2008-05-29
> sudo apt-get remove xserver-xgl
spacegypsy@void:~$ sudo apt-get remove xserver-xgl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package xserver-xgl is not installed, so not removed
The following packages were automatically installed and are no longer required:
  openoffice.org-l10n-nl openoffice.org-l10n-common aircrack-ng
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
spacegypsy@void:~$ 

Package xserver-xgl is not installed, so not removed

I just modified my xorg.conf like you told to with no result unless that when I want to enable the visual effects I get:
> The Composite extension is not available


 Should I undo the modifications of my xorg.conf before going on?

Anyway 1000*thx for your time and knowledge.

---

### Post by spacegypsy on 2008-05-29
> **mats-palats said:**
> That was it!

By removing xserver-xgl it all works again! Thanks! :)

```
delirium@delirium-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON X700
OpenGL version string: 2.1.7537 Release

delirium@delirium-laptop:~$ glxinfo | grep direct
direct rendering: Yes
delirium@delirium-laptop:~$ 

```

lucky you

---

### Post by graham-cracker on 2008-05-29
Yeah I'd say undo the edits to the xorg.conf file.

So I think the output from dpkg -l | grep xserver-xgl:
```
rc xserver-xgl 1:1.1.99.1~git20080115-0ubuntu1 GL-based X server
```
means there are residual configuration files left over (hence the 'rc'). So give this a try:
```
sudo apt-get purge xserver-xgl
```

If that doesn't fix it, did you try:
```
sudo update-alternatives --config Xorg
```
and then select the fglrx option (or post the options here).

---

### Post by spacegypsy on 2008-05-29
I did a fresh install of Ubuntu Studio 8.04 instead of the upgrade,

and now I got the driver "In use" without any problem.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=72112&stc=1&d=1212111111[/IMG]

:)

Still it's a bit silly that  I have to recustomized my desktop, just because of (again) the ATI thing.

On the other hand I will have clean OS again. ;) 

and thanks again graham-cracker

---

