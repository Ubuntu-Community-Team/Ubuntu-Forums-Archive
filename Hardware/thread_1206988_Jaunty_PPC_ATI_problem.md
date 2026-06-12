---
title: "Jaunty PPC ATI problem"
date: 2009-07-07
forum: Hardware
---

### Post by mumia55 on 2009-07-07
Hi everybody, it's has being some time I don't post here, and it has being 6 months I don't work with Ubuntu. But now, something tells me us PPCs will be abandoned by Apple, our OS supplier... :)
Ok, now to the problem. I have installed Ubuntu Jaunty on my iBookG4 12" laptop, and there is a problem. Seems like when boot up in Jaunty, splash screen gets all bugged. And not only that, everything (I think) that uses 3D acceleration, gets bugged. For instance, when I run glxgears in terminal, this is what happens.

[IMG]http://i30.tinypic.com/11ab96v.jpg[/IMG]

And glxinfo: Most of what I think is important.

> name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string: 2.1 Mesa 7.4
OpenGL shading language version string: 1.20
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader, 
    GL_ARB_half_float_pixel, GL_ARB_imaging, GL_ARB_multisample, 
    GL_ARB_multitexture, GL_ARB_occlusion_query, GL_ARB_pixel_buffer_object, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shader_objects, 
    GL_ARB_shading_language_100, GL_ARB_shading_language_120, GL_ARB_shadow, 
    GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_compiled_vertex_array, GL_EXT_convolution, 
    GL_EXT_copy_texture, GL_EXT_depth_bounds_test, GL_EXT_draw_range_elements, 
    GL_EXT_framebuffer_object, GL_EXT_framebuffer_blit, GL_EXT_fog_coord, 
    GL_EXT_gpu_program_parameters, GL_EXT_histogram, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels, 
    GL_EXT_paletted_texture, GL_EXT_pixel_buffer_object, 
    GL_EXT_point_parameters, GL_EXT_polygon_offset, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_shadow_funcs, GL_EXT_shared_texture_palette, 
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, GL_EXT_vertex_array, 
    GL_3DFX_texture_compression_FXT1, GL_APPLE_packed_pixels, 
    GL_APPLE_vertex_array_object, GL_ATI_blend_equation_separate, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once, 
    GL_ATI_fragment_shader, GL_ATI_separate_stencil, 
    GL_IBM_multimode_draw_arrays, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_program_debug, GL_MESA_resize_buffers, 
    GL_MESA_texture_array, GL_MESA_ycbcr_texture, GL_MESA_window_pos, 
    GL_NV_blend_square, GL_NV_fragment_program, GL_NV_light_max_exponent, 
    GL_NV_point_sprite, GL_NV_texture_rectangle, GL_NV_texgen_reflection, 
    GL_NV_vertex_program, GL_NV_vertex_program1_1, GL_OES_read_format, 
    GL_SGI_color_matrix, GL_SGI_color_table, GL_SGI_texture_color_table, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SGIX_shadow, GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays



And xorg configuration:

```
Section "ServerLayout"
        Identifier     "Default Layout"
        Screen  0      "InternalScreen"
        InputDevice    "Synaptics" "CorePointer"
        InputDevice    "Keyboard0" "CoreKeyboard"
        InputDevice    "Mouse0"    "SendCoreEvents"
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection

Section "DRI"
        Mode 0666
EndSection

Section "Files"
        RgbPath      "/usr/share/X11/rgb"
        ModulePath   "/usr/lib/xorg/modules"
        FontPath     "/usr/share/fonts/misc"
        FontPath     "/usr/share/fonts/100dpi"
        FontPath     "/usr/share/fonts/TTF"
        FontPath     "/usr/share/fonts/Type1"
        FontPath     "/usr/share/fonts/artwiz-fonts"
EndSection

Section "Module"
        Load  "glx"
        Load  "extmod"
        Load  "xtrap"
        Load  "record"
        Load  "dbe"
        Load  "dri"
        Load  "ddc"
        Load  "bitmap"
        Load  "int10"
        Load  "vbe"
        Load  "freetype"
        Load  "type1"
EndSection

Section "InputDevice"
        Identifier  "Keyboard0"
        Driver      "kbd"
        Option      "XkbModel"   "xfree86"
        Option      "XkbLayout"  "de"
EndSection

Section "InputDevice"
        Identifier  "Mouse0"
        Driver      "mouse"
        Option      "Protocol" "auto"
        Option      "Device" "/dev/input/mice"
        Option      "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
       Identifier      "Synaptics"
       Driver          "synaptics"
       Option          "Device"                "/dev/input/mice"
       Option          "Protocol"              "auto-dev"
       Option          "LeftEdge"              "50"
       Option          "RightEdge"             "840"
       Option          "TopEdge"               "30"
       Option          "BottomEdge"            "320"
       Option          "MinSpeed"              "0.2"
       Option          "MaxSpeed"              "1.5"
       Option          "AccelFactor"           "0.1"
       Option          "SHMConfig"             "on"
       Option          "RTCornerButton"        "3"
       Option          "LTCornerButton"        "2"
       Option          "FingerLow"             "12"
       Option          "FingerHigh"            "20"
       Option          "MaxTapTime"            "120"  
       Option          "HorizScrollDelta"      "15"
       Option          "VertScrollDelta"       "15"
       Option          "VertEdgeScroll"        "off"
       Option          "HorizEdgeScroll"       "off"
       Option          "VertTwoFingerScroll"   "on"
       Option          "HorizTwoFingerScroll"  "on"
EndSection

Section "Monitor"
        Identifier   "TFT"
        Option       "DPMS"
EndSection

Section "Device"
        Option      "AGPMode"                    "4"     
        Option      "AGPFastWrite"               "on"    
        Option      "GARTSize"                   "32"    
        Option      "RingSize"                   "8"
        Option      "EnablePageFlip"             "on"    
        Option      "AccelDFS"                   "on"
        Option      "UseFBDev"                   "false"  
        Option      "RenderAccel"                "true"
        Option      "SubPixelOrder"              "NONE"
        Option      "DynamicClocks"              "on"
        Option      "AccelMethod"                "EXA" 
        Option      "XAANoOffscreenPixmaps"      "true"
        Option      "BackingStore"               "true"
        Option      "ColorTiling"                 "on"
        Option      "MacModel"                    "ibook"  #important for dvi-out! 
        Identifier  "InternalDevice"
        Driver      "ati"
        VendorName  "ATI Technologies Inc"
        BoardName   "M11 NV [FireGL Mobility T2e]"
        BusID       "PCI:0:16:0"
        Screen      0
EndSection


Section "Screen"
        Identifier "InternalScreen"
        Device     "InternalDevice"
        Monitor    "TFT"
        DefaultDepth      24

        SubSection "Display"
                Viewport  0 0
                Depth     24
                Modes     "1024x768"
                Virtual   2048 768
        EndSubSection
EndSection
```

And my Xorg.0.log:

> 
X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.15-51-powerpc64-smp ppc Ubuntu
Current Operating System: Linux carlosdesa-laptop 2.6.28-6-powerpc #20-Ubuntu Fri Apr 17 08:30:40 UTC 2009 ppc
Build Date: 09 April 2009  02:10:13AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@ross.buildd) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Jul  7 18:23:06 2009
(==) Using config file: "/etc/X11/xorg.conf"
Parse error on line 38 of section Files in file /etc/X11/xorg.conf
	Ignoring obsolete keyword "RgbPath".
(==) ServerLayout "Default Layout"
(**) |-->Screen "InternalScreen" (0)
(**) |   |-->Monitor "TFT"
(**) |   |-->Device "InternalDevice"
(**) |-->Input Device "Synaptics"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/misc" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/fonts/100dpi" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/fonts/TTF" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/fonts/Type1" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/fonts/artwiz-fonts" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(**) ModulePath set to "/usr/lib/xorg/modules"
(**) Extension "Composite" is enabled
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x1e80
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@0:16:0) ATI Technologies Inc M11 NV [FireGL Mobility T2e] rev 128, Mem @ 0x98000000/134217728, 0x90000000/65536, I/O @ 0x00000400/256, BIOS @ 0x????????/131072
(II) Open APM successful
(II) System resource ranges:
	[0] -1	2	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	2	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	2	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	2	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	1	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	1	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	1	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	1	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	2	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	2	0x00000000 - 0x00000000 (0x1) IX[B]
	[14] -1	1	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	1	0x00000000 - 0x00000000 (0x1) IX[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded. This was enabled by default and also specified in the config file.
(II) "dri" will be loaded. This was enabled by default and also specified in the config file.
(II) "dri2" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "xtrap"
(WW) Warning, couldn't open module xtrap
(II) UnloadModule: "xtrap"
(EE) Failed to load module "xtrap" (module does not exist, 0)
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "freetype"
(WW) Warning, couldn't open module freetype
(II) UnloadModule: "freetype"
(EE) Failed to load module "freetype" (module does not exist, 0)
(II) LoadModule: "type1"
(WW) Warning, couldn't open module type1
(II) UnloadModule: "type1"
(EE) Failed to load module "type1" (module does not exist, 0)
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 6.12.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 6.12.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 0.99.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(II) RADEON: Driver for ATI Radeon chipsets:
	ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
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
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
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
	ATI Mobility Radeon X1700, ATI Radeon X2300HD,
	ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
	ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
	ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
	ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
	ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
	ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
	ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
	ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
	ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
	ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
	ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
	ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
	ATI Radeon 4800 Series, ATI FirePro V8750 (FireGL),
	ATI FirePro V7760 (FireGL), ATI Mobility RADEON HD 4850,
	ATI Mobility RADEON HD 4850 X2, ATI Radeon 4800 Series,
	ATI FirePro RV770, AMD FireStream 9270, AMD FireStream 9250,
	ATI FirePro V8700 (FireGL), ATI Mobility RADEON HD 4870,
	ATI Mobility RADEON M98, ATI FirePro M7750, ATI M98, ATI M98,
	ATI M98, ATI Radeon RV730 (AGP), ATI FirePro M5750,
	ATI Radeon RV730 (AGP), ATI RV730XT [Radeon HD 4670],
	ATI RADEON E4600, ATI RV730 PRO [Radeon HD 4650],
	ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
	ATI FirePro V3750 (FireGL), ATI RV610, ATI Radeon HD 2400 XT,
	ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
	ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
	ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
	ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
	ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
	ATI Mobility Radeon HD 3850 X2, ATI RV670,
	ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
	ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
	ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
	ATI Radeon RV710, ATI Radeon RV710, ATI Radeon HD 4350,
	ATI Mobility Radeon 4300 Series, ATI Mobility Radeon 4500 Series,
	ATI Mobility Radeon 4500 Series, ATI RV630,
	ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
	ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
	ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
	ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
	ATI FireGL V3600, ATI Radeon HD 2600 LE,
	ATI Mobility FireGL Graphics Processor, ATI Radeon RV710,
	ATI Radeon HD 3470, ATI Mobility Radeon HD 3430,
	ATI Mobility Radeon HD 3400 Series, ATI Radeon HD 3450,
	ATI Radeon HD 3450, ATI Radeon HD 3430, ATI Radeon HD 3450,
	ATI FirePro V3700, ATI FireMV 2450, ATI FireMV 2260, ATI FireMV 2260,
	ATI Radeon HD 3600 Series, ATI Radeon HD 3650 AGP,
	ATI Radeon HD 3600 PRO, ATI Radeon HD 3600 XT,
	ATI Radeon HD 3600 PRO, ATI Mobility Radeon HD 3650,
	ATI Mobility Radeon HD 3670, ATI Mobility FireGL V5700,
	ATI Mobility FireGL V5725, ATI Radeon HD 3200 Graphics,
	ATI Radeon 3100 Graphics, ATI Radeon HD 3200 Graphics,
	ATI Radeon 3100 Graphics, ATI Radeon HD 3300 Graphics,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3000 Graphics,
	ATI Radeon HD Graphics, ATI Radeon Graphics,
	ATI Mobility Radeon HD Graphics, ATI Mobility Radeon Graphics,
	ATI Radeon Graphics
(II) Primary Device is: PCI 00@00:10:0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	2	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	2	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	2	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	2	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	1	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	1	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	1	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	1	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	2	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	2	0x00000000 - 0x00000000 (0x1) IX[B]
	[14] -1	1	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	1	0x00000000 - 0x00000000 (0x1) IX[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) resource ranges after probing:
	[0] -1	2	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	2	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	2	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	2	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	1	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	1	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	1	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	1	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[13] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[14] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[15] -1	2	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	2	0x00000000 - 0x00000000 (0x1) IX[B]
	[17] -1	1	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	1	0x00000000 - 0x00000000 (0x1) IX[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[21] 0	0	0xf00003b0 - 0xf00003bb (0xc) IS[B]
	[22] 0	0	0xf00003c0 - 0xf00003df (0x20) IS[B]
(II) RADEON(0): TOTO SAYS 0000000090000000
(II) RADEON(0): MMIO registers at 0x0000000090000000: size 64KB
(II) RADEON(0): PCI bus 0 card 16 func 0
(**) RADEON(0): Depth 24, (--) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(**) RADEON(0): Option "AGPMode" "4"
(**) RADEON(0): Option "AGPFastWrite" "on"
(**) RADEON(0): Option "GARTSize" "32"
(**) RADEON(0): Option "RingSize" "8"
(**) RADEON(0): Option "EnablePageFlip" "on"
(**) RADEON(0): Option "AccelDFS" "on"
(**) RADEON(0): Option "ColorTiling" "on"
(**) RADEON(0): Option "RenderAccel" "true"
(**) RADEON(0): Option "SubPixelOrder" "NONE"
(**) RADEON(0): Option "DynamicClocks" "on"
(**) RADEON(0): Option "AccelMethod" "EXA"
(**) RADEON(0): Option "MacModel" "ibook"
(II) RADEON(0): VGAAccess option set to FALSE, VGA module load skipped
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(--) RADEON(0): Chipset: "ATI FireGL Mobility T2e (M11) NV (AGP)" (ChipID = 0x4e56)
(--) RADEON(0): Linear framebuffer at 0x0000000098000000
(II) RADEON(0): AGP card detected
(WW) RADEON(0): Failed to read PCI ROM!
(II) RADEON(0): Attempting to read un-POSTed bios
(WW) RADEON(0): Failed to read PCI ROM!
(WW) RADEON(0): Unrecognized BIOS signature, BIOS data will not be used
drmOpenDevice: node name is /dev/dri/card0
drmOpenByBusid: Searching for BusID pci:0000:00:10.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card1
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card2
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card3
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card4
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card5
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card6
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card7
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card8
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card9
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card10
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card11
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card12
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card13
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card14
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
(II) RADEON(0): [dri] Found DRI library version 1.3.0 and kernel module version 1.29.0
(**) RADEON(0): Page Flipping enabled
(II) RADEON(0): Will try to use DMA for Xv image transfers
(II) RADEON(0): Generation 2 PCI interface, using max accessible memory
(II) RADEON(0): Detected total video RAM=32768K, accessible=131072K (PCI BAR=131072K)
(--) RADEON(0): Mapped VideoRAM: 32768 kByte (64 bit DDR SDRAM)
(II) RADEON(0): Color tiling enabled by default
(II) RADEON(0): Max desktop size set to 2048x768
(II) RADEON(0): For a larger or smaller max desktop size, add a Virtual line to your xorg.conf
(II) RADEON(0): If you are having trouble with 3D, reduce the desktop size by adjusting the Virtual line to your xorg.conf
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(WW) RADEON(0): Video BIOS not detected, using default clock settings!
(II) RADEON(0): Probed PLL values: xtal: 27.000000 Mhz, sclk: 209.250000 Mhz, mclk: 183.375000 Mhz
(II) RADEON(0): PLL parameters: rf=2700 rd=12 min=12500 max=35000; xclk=7814
(II) RADEON(0): Existing panel PLL dividers will be used.
(WW) RADEON(0): Panel size 1024x768 is derived, this may not be correct.
If not, use PanelSize option to overwrite this setting
(II) RADEON(0): Output LVDS using monitor section TFT
(II) RADEON(0): I2C bus "LVDS" initialized.
(II) RADEON(0): Output VGA-0 has no monitor section
(II) RADEON(0): I2C bus "VGA-0" initialized.
(II) RADEON(0): Output S-video has no monitor section
(II) RADEON(0): Port0:
  XRANDR name: LVDS
  Connector: LVDS
  LCD1: INTERNAL_LVDS
  DDC reg: 0x64
(II) RADEON(0): Port1:
  XRANDR name: VGA-0
  Connector: VGA
  CRT2: INTERNAL_DAC2
  DDC reg: 0x60
(II) RADEON(0): Port2:
  XRANDR name: S-video
  Connector: S-video
  TV1: INTERNAL_DAC2
  DDC reg: 0x0
(II) RADEON(0): I2C device "LVDS:E-EDID segment register" registered at address 0x60.
(II) RADEON(0): I2C device "LVDS:ddc2" registered at address 0xA0.
(II) RADEON(0): EDID vendor "APP", prod id 39978
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: APP  Model: 9c2a  Serial#: 0
(II) RADEON(0): Year: 2002  Week: 0
(II) RADEON(0): EDID Version: 1.1
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 24  vert.: 18
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.560 redY: 0.334   greenX: 0.308 greenY: 0.536
(II) RADEON(0): blueX: 0.155 blueY: 0.133   whiteX: 0.312 whiteY: 0.328
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  245 x 184 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(WW) RADEON(0): Unknown vendor-specific block 1
(II) RADEON(0):  LP121X04-C2
(II) RADEON(0): Monitor name: COLOR LCD
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0006102a9c00000000
(II) RADEON(0): 	000c0101801812780a6dc08f554e8927
(II) RADEON(0): 	22505400080001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	3600f5b8000000180000000100061020
(II) RADEON(0): 	00000000000000000a20000000fe004c
(II) RADEON(0): 	503132315830342d43320a20000000fc
(II) RADEON(0): 	00434f4c4f52204c43440a2020200025
finished output detect: 0
(II) RADEON(0): I2C device "VGA-0:E-EDID segment register" registered at address 0x60.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
finished output detect: 1
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
finished output detect: 2
finished all detect
before xf86InitialConfiguration
(II) RADEON(0): EDID vendor "APP", prod id 39978
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: APP  Model: 9c2a  Serial#: 0
(II) RADEON(0): Year: 2002  Week: 0
(II) RADEON(0): EDID Version: 1.1
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 24  vert.: 18
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.560 redY: 0.334   greenX: 0.308 greenY: 0.536
(II) RADEON(0): blueX: 0.155 blueY: 0.133   whiteX: 0.312 whiteY: 0.328
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  245 x 184 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(WW) RADEON(0): Unknown vendor-specific block 1
(II) RADEON(0):  LP121X04-C2
(II) RADEON(0): Monitor name: COLOR LCD
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0006102a9c00000000
(II) RADEON(0): 	000c0101801812780a6dc08f554e8927
(II) RADEON(0): 	22505400080001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	3600f5b8000000180000000100061020
(II) RADEON(0): 	00000000000000000a20000000fe004c
(II) RADEON(0): 	503132315830342d43320a20000000fc
(II) RADEON(0): 	00434f4c4f52204c43440a2020200025
(II) RADEON(0): Panel infos found from DDC detailed: 1024x768
(II) RADEON(0): EDID vendor "APP", prod id 39978
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): Output LVDS connected
(II) RADEON(0): Output VGA-0 disconnected
(II) RADEON(0): Output S-video disconnected
(II) RADEON(0): Using user preference for initial modes
(II) RADEON(0): Output LVDS using initial mode 1024x768
after xf86InitialConfiguration
(**) RADEON(0): Display dimensions: (240, 180) mm
(**) RADEON(0): DPI set to (216, 108)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(**) RADEON(0): Using EXA acceleration architecture
(II) Loading sub module "exa"
(II) LoadModule: "exa"
(II) Loading /usr/lib/xorg/modules//libexa.so
(II) Module exa: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.4.0
	ABI class: X.Org Video Driver, version 5.0
(==) RADEON(0): Assuming overlay scaler buffer width is 1920
(II) RADEON(0): Cannot access BIOS or it is not valid.
		If your card is TV-in capable you will need to specify options RageTheatreCrystal, RageTheatreTunerPort, 
		RageTheatreSVideoPort and TunerType in /etc/X11/xorg.conf.
(!!) RADEON(0): For information on using the multimedia capabilities
	of this adapter, please see [http://gatos.sf.net](http://gatos.sf.net).
(!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	2	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	2	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	2	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	2	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	1	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	1	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	1	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	1	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[13] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[14] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[15] -1	2	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	2	0x00000000 - 0x00000000 (0x1) IX[B]
	[17] -1	1	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	1	0x00000000 - 0x00000000 (0x1) IX[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[21] 0	0	0xf00003b0 - 0xf00003bb (0xc) IS[B](OprU)
	[22] 0	0	0xf00003c0 - 0xf00003df (0x20) IS[B](OprU)
(II) RADEON(0): RADEONScreenInit 98000000 0 0
Entering TV Save
Save TV timing tables
saveTimingTables: reading timing tables
TV Save done
disable LVDS
(II) RADEON(0): Dynamic Clock Scaling Enabled
(==) RADEON(0): Using 24 bit depth buffer
(II) RADEON(0): RADEONInitMemoryMap() : 
(II) RADEON(0):   mem_size         : 0x04000000
(II) RADEON(0):   MC_FB_LOCATION   : 0x9bff9800
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(II) RADEON(0): Depth moves disabled by default
(II) RADEON(0): Allocating from a screen of 32768 kb
(II) RADEON(0): Will use 32 kb for hardware cursor 0 at offset 0x00600000
(II) RADEON(0): Will use 32 kb for hardware cursor 1 at offset 0x00604000
(II) RADEON(0): Will use 6144 kb for front buffer at offset 0x00000000
(II) RADEON(0): Will use 6144 kb for back buffer at offset 0x00608000
(II) RADEON(0): Will use 6144 kb for depth buffer at offset 0x00c08000
(II) RADEON(0): Will use 7104 kb for textures at offset 0x01208000
(II) RADEON(0): Will use 7200 kb for X Server offscreen at offset 0x018f8000
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:10.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:00:10.0
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) RADEON(0): [drm] Using the DRM lock SAREA also for drawables.
(II) RADEON(0): [drm] framebuffer handle = 0x98000000
(II) RADEON(0): [drm] added 1 reserved context for kernel
(II) RADEON(0): X context handle = 0x1
(II) RADEON(0): [drm] installed DRM signal handler
(**) RADEON(0): Using AGP 4x
(WW) RADEON(0): WARNING: Using the AGPFastWrite option is not recommended.
	This option does not provide much of a noticable speed boost, while it
	will probably hard lock your machine. All bets are off!
(**) RADEON(0): Enabling AGP Fast Writes.
(II) RADEON(0): [agp] Mode 0x07000217 [AGP 0x106b/0x0034; Card 0x1002/0x4e56 0x1002/0x4e56]
(II) RADEON(0): [agp] 32768 kB allocated with handle 0x00000001
(II) RADEON(0): [agp] ring handle = 0x00000000
(II) RADEON(0): [agp] Ring mapped at 0x4a061000
(II) RADEON(0): [agp] ring read ptr handle = 0x00801000
(II) RADEON(0): [agp] Ring read ptr mapped at 0x48028000
(II) RADEON(0): [agp] vertex/indirect buffers handle = 0x00802000
(II) RADEON(0): [agp] Vertex/indirect buffers mapped at 0x4a862000
(II) RADEON(0): [agp] GART texture map handle = 0x00a02000
(II) RADEON(0): [agp] GART Texture map mapped at 0x4aa62000
(II) RADEON(0): [drm] register handle = 0x90000000
(II) RADEON(0): [dri] Visual configs initialized
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x9bff9800 0x07ff0000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(**) RADEON(0): Option "BackingStore" "true"
(**) RADEON(0): Backing store enabled
(II) RADEON(0): [DRI] installation complete
(II) RADEON(0): [drm] removed 1 reserved context for kernel
(II) RADEON(0): [drm] unmapping 8192 bytes of SAREA 0xf1d96000 at 0x48026000
(II) RADEON(0): [drm] Closed DRM master.
(WW) RADEON(0): Direct rendering disabled
(II) RADEON(0): Render acceleration enabled for R300/R400/R500 type cards.
(II) RADEON(0): Setting EXA maxPitchBytes
(II) RADEON(0): num quad-pipes is 1
(II) EXA(0): Offscreen pixmap area of 7372800 bytes
(II) EXA(0): Driver registered support for the following operations:
(II)         Solid
(II)         Copy
(II)         Composite (RENDER acceleration)
(II) RADEON(0): Acceleration enabled
(**) Option "dpms"
(**) RADEON(0): DPMS enabled
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): No video input capabilities detected and no information is provided - disabling multimedia i2c
(II) Loading sub module "theatre_detect"
(II) LoadModule: "theatre_detect"
(II) Loading /usr/lib/xorg/modules/multimedia//theatre_detect_drv.so
(II) Module theatre_detect: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 5.0
(II) RADEON(0): no multimedia table present, disabling Rage Theatre.
(II) RADEON(0): Set up overlay video
(II) RADEON(0): Set up textured video
disable LVDS
disable TVDAC
disable TV
disable LVDS
init memmap
init common
init crtc1
init pll1
restore memmap
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x9bff9800 0x9bff9800
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
restore common
restore crtc1
restore pll1
set RMX
set LVDS
enable LVDS
disable TVDAC
disable TV
(II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(WW) RADEON(0): Option "UseFBDev" is not used
(WW) RADEON(0): Option "XAANoOffscreenPixmaps" is not used
(--) RandR disabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) AIGLX: Screen 0 is not DRI2 capable
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(II) RADEON(0): Setting screen physical size to 245 x 184
(II) Synaptics touchpad driver version 0.99.3
(--) Synaptics auto-dev sets device to /dev/input/event7
(**) Option "Device" "/dev/input/event7"
(II) Synaptics: x-axis range 0 - 959
(II) Synaptics: y-axis range 0 - 644
(II) Synaptics: pressure range 0 - 300
(II) Synaptics: finger width range 0 - 0
(II) Synaptics: buttons: left double triple
(**) Option "SHMConfig" "on"
(**) Option "LeftEdge" "50"
(**) Option "RightEdge" "840"
(**) Option "TopEdge" "30"
(**) Option "BottomEdge" "320"
(**) Option "FingerLow" "12"
(**) Option "FingerHigh" "20"
(**) Option "MaxTapTime" "120"
(**) Option "VertScrollDelta" "15"
(**) Option "HorizScrollDelta" "15"
(**) Option "VertEdgeScroll" "off"
(**) Option "HorizEdgeScroll" "off"
(**) Option "VertTwoFingerScroll" "on"
(**) Option "HorizTwoFingerScroll" "on"
(**) Option "RTCornerButton" "3"
(**) Option "LTCornerButton" "2"
(--) Synaptics touchpad found
(**) Option "CorePointer"
(**) Synaptics: always reports core events
(II) XINPUT: Adding extended input device "Synaptics" (type: TOUCHPAD)
(**) Synaptics: (accel) keeping acceleration scheme 1
(**) Synaptics: (accel) filter chain progression: 2.00
(**) Synaptics: (accel) filter stage 0: 20.00 ms
(**) Synaptics: (accel) set acceleration profile 0
(--) Synaptics touchpad found
(II) config/hal: Adding input device ADB Powerbook buttons
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) ADB Powerbook buttons: always reports core events
(**) ADB Powerbook buttons: Device: "/dev/input/event2"
(II) ADB Powerbook buttons: Found keys
(II) ADB Powerbook buttons: Configuring as keyboard
(II) XINPUT: Adding extended input device "ADB Powerbook buttons" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) ADB Powerbook buttons: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) ADB Powerbook buttons: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) ADB Powerbook buttons: xkb_layout: "us"
(II) config/hal: Adding input device Mouseemu virtual keyboard
(**) Mouseemu virtual keyboard: always reports core events
(**) Mouseemu virtual keyboard: Device: "/dev/input/event8"
(II) Mouseemu virtual keyboard: Found keys
(II) Mouseemu virtual keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "Mouseemu virtual keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Mouseemu virtual keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Mouseemu virtual keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Mouseemu virtual keyboard: xkb_layout: "us"
(II) config/hal: Adding input device ADB keyboard
(**) ADB keyboard: always reports core events
(**) ADB keyboard: Device: "/dev/input/event1"
(II) ADB keyboard: Found keys
(II) ADB keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "ADB keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) ADB keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) ADB keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) ADB keyboard: xkb_layout: "us"
(II) config/hal: Adding input device Mouseemu virtual mouse
(**) Mouseemu virtual mouse: always reports core events
(**) Mouseemu virtual mouse: Device: "/dev/input/event9"
(II) Mouseemu virtual mouse: Found 3 mouse buttons
(II) Mouseemu virtual mouse: Found x and y relative axes
(II) Mouseemu virtual mouse: Configuring as mouse
(**) Mouseemu virtual mouse: YAxisMapping: buttons 4 and 5
(**) Mouseemu virtual mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Mouseemu virtual mouse" (type: MOUSE)
(**) Mouseemu virtual mouse: (accel) keeping acceleration scheme 1
(**) Mouseemu virtual mouse: (accel) filter chain progression: 2.00
(**) Mouseemu virtual mouse: (accel) filter stage 0: 20.00 ms
(**) Mouseemu virtual mouse: (accel) set acceleration profile 0
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) config/hal: Adding input device HID 062a:0001
(**) HID 062a:0001: always reports core events
(**) HID 062a:0001: Device: "/dev/input/event6"
(II) HID 062a:0001: Found 5 mouse buttons
(II) HID 062a:0001: Found x and y relative axes
(II) HID 062a:0001: Configuring as mouse
(**) HID 062a:0001: YAxisMapping: buttons 4 and 5
(**) HID 062a:0001: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "HID 062a:0001" (type: MOUSE)
(**) HID 062a:0001: (accel) keeping acceleration scheme 1
(**) HID 062a:0001: (accel) filter chain progression: 2.00
(**) HID 062a:0001: (accel) filter stage 0: 20.00 ms
(**) HID 062a:0001: (accel) set acceleration profile 0
(II) config/hal: Adding input device appletouch
(II) Synaptics touchpad driver version 0.99.3
(**) Option "Device" "/dev/input/event7"
(II) appletouch: x-axis range 0 - 959
(II) appletouch: y-axis range 0 - 644
(II) appletouch: pressure range 0 - 300
(II) appletouch: finger width range 0 - 0
(II) appletouch: buttons: left double triple
(--) appletouch touchpad found
(**) appletouch: always reports core events
(II) XINPUT: Adding extended input device "appletouch" (type: TOUCHPAD)
(**) appletouch: (accel) keeping acceleration scheme 1
(**) appletouch: (accel) filter chain progression: 2.00
(**) appletouch: (accel) filter stage 0: 20.00 ms
(**) appletouch: (accel) set acceleration profile 0
(WW) appletouch can't grab event device, errno=16
(--) appletouch touchpad found
(II) RADEON(0): EDID vendor "APP", prod id 39978
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: APP  Model: 9c2a  Serial#: 0
(II) RADEON(0): Year: 2002  Week: 0
(II) RADEON(0): EDID Version: 1.1
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 24  vert.: 18
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.560 redY: 0.334   greenX: 0.308 greenY: 0.536
(II) RADEON(0): blueX: 0.155 blueY: 0.133   whiteX: 0.312 whiteY: 0.328
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  245 x 184 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(WW) RADEON(0): Unknown vendor-specific block 1
(II) RADEON(0):  LP121X04-C2
(II) RADEON(0): Monitor name: COLOR LCD
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0006102a9c00000000
(II) RADEON(0): 	000c0101801812780a6dc08f554e8927
(II) RADEON(0): 	22505400080001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	3600f5b8000000180000000100061020
(II) RADEON(0): 	00000000000000000a20000000fe004c
(II) RADEON(0): 	503132315830342d43320a20000000fc
(II) RADEON(0): 	00434f4c4f52204c43440a2020200025
(II) RADEON(0): Panel infos found from DDC detailed: 1024x768
(II) RADEON(0): EDID vendor "APP", prod id 39978
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID vendor "APP", prod id 39978
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: APP  Model: 9c2a  Serial#: 0
(II) RADEON(0): Year: 2002  Week: 0
(II) RADEON(0): EDID Version: 1.1
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 24  vert.: 18
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.560 redY: 0.334   greenX: 0.308 greenY: 0.536
(II) RADEON(0): blueX: 0.155 blueY: 0.133   whiteX: 0.312 whiteY: 0.328
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  245 x 184 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(WW) RADEON(0): Unknown vendor-specific block 1
(II) RADEON(0):  LP121X04-C2
(II) RADEON(0): Monitor name: COLOR LCD
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0006102a9c00000000
(II) RADEON(0): 	000c0101801812780a6dc08f554e8927
(II) RADEON(0): 	22505400080001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	3600f5b8000000180000000100061020
(II) RADEON(0): 	00000000000000000a20000000fe004c
(II) RADEON(0): 	503132315830342d43320a20000000fc
(II) RADEON(0): 	00434f4c4f52204c43440a2020200025
(II) RADEON(0): Panel infos found from DDC detailed: 1024x768
(II) RADEON(0): EDID vendor "APP", prod id 39978
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID vendor "APP", prod id 39978
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: APP  Model: 9c2a  Serial#: 0
(II) RADEON(0): Year: 2002  Week: 0
(II) RADEON(0): EDID Version: 1.1
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 24  vert.: 18
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.560 redY: 0.334   greenX: 0.308 greenY: 0.536
(II) RADEON(0): blueX: 0.155 blueY: 0.133   whiteX: 0.312 whiteY: 0.328
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  245 x 184 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(WW) RADEON(0): Unknown vendor-specific block 1
(II) RADEON(0):  LP121X04-C2
(II) RADEON(0): Monitor name: COLOR LCD
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0006102a9c00000000
(II) RADEON(0): 	000c0101801812780a6dc08f554e8927
(II) RADEON(0): 	22505400080001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	3600f5b8000000180000000100061020
(II) RADEON(0): 	00000000000000000a20000000fe004c
(II) RADEON(0): 	503132315830342d43320a20000000fc
(II) RADEON(0): 	00434f4c4f52204c43440a2020200025
(II) RADEON(0): Panel infos found from DDC detailed: 1024x768
(II) RADEON(0): EDID vendor "APP", prod id 39978
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID vendor "APP", prod id 39978
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: APP  Model: 9c2a  Serial#: 0
(II) RADEON(0): Year: 2002  Week: 0
(II) RADEON(0): EDID Version: 1.1
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 24  vert.: 18
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.560 redY: 0.334   greenX: 0.308 greenY: 0.536
(II) RADEON(0): blueX: 0.155 blueY: 0.133   whiteX: 0.312 whiteY: 0.328
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  245 x 184 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(WW) RADEON(0): Unknown vendor-specific block 1
(II) RADEON(0):  LP121X04-C2
(II) RADEON(0): Monitor name: COLOR LCD
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0006102a9c00000000
(II) RADEON(0): 	000c0101801812780a6dc08f554e8927
(II) RADEON(0): 	22505400080001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	3600f5b8000000180000000100061020
(II) RADEON(0): 	00000000000000000a20000000fe004c
(II) RADEON(0): 	503132315830342d43320a20000000fc
(II) RADEON(0): 	00434f4c4f52204c43440a2020200025
(II) RADEON(0): Panel infos found from DDC detailed: 1024x768
(II) RADEON(0): EDID vendor "APP", prod id 39978
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0



Sorry for the amount of data, I hope I gave most of the needed information for someone that can help me.

Thank you very much, from now on, I'm not going to abandon Ubuntu anymore! Nor the community!

---

### Post by shatterblast on 2009-07-07
> **mumia55 said:**
> Hi everybody, it's has being some time I don't post here, and it has being 6 months I don't work with Ubuntu. But now, something tells me us PPCs will be abandoned by Apple, our OS supplier... :)


Apple has a long history of abandoning it, and then supporting it again.  They will still honor the manufacturer's warranties on your hardware parts since they are separate from Apple in many regards.  Some parts like the hard drive and memory will still retain coverage even if you open the case.  Still, always good to ask before an attempt since you may meet heavy resistance depending on your authorized repair individual.

It seems to me the hardware driver for your video card needs installation.  I suggest going into Synaptic to install "envyng-qt".  Synaptic can be found under:

System -> Administration -> Synaptic

---

### Post by mumia55 on 2009-07-07
> **shatterblast said:**
> Apple has a long history of abandoning it, and then supporting it again.  They will still honor the manufacturer's warranties on your hardware parts since they are separate from Apple in many regards.  Some parts like the hard drive and memory will still retain coverage even if you open the case.  Still, always good to ask before an attempt since you may meet heavy resistance depending on your authorized repair individual.

It seems to me the hardware driver for your video card needs installation.  I suggest going into Synaptic to install "envyng-qt".  Synaptic can be found under:

System -> Administration -> Synaptic

I tried what you've said, and I had problems. Tried on synaptics too, same messages.

> carlosdesa@carlosdesa-laptop:~$ sudo apt-get install envyng-qt 
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  envyng-qt: Depends: envyng-core (>= 2.0.1) but it is not going to be installed
E: Broken packages
carlosdesa@carlosdesa-laptop:~$ sudo apt-get install envy
envy         envyng-core  envyng-gtk   envyng-qt    
carlosdesa@carlosdesa-laptop:~$ sudo apt-get install envy
envy         envyng-core  envyng-gtk   envyng-qt    
carlosdesa@carlosdesa-laptop:~$ sudo apt-get install envyng-core 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  envyng-core: Depends: nvidia-common but it is not installable
               Depends: fglrx-modaliases but it is not installable
E: Broken packages
carlosdesa@carlosdesa-laptop:~$ sudo apt-get install fglrx-modaliases
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package fglrx-modaliases is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package fglrx-modaliases has no installation candidate
carlosdesa@carlosdesa-laptop:~$ 


---

### Post by shatterblast on 2009-07-08
I forgot some of the dependencies for EnvyNG don't work well with PPCs, and I see the manufacturer type of your video card as ATI, which has slight issues with Jaunty.  I think it a matter of choosing the right driver.

I am having difficulty finding a hardware driver for your computer's video card.  Apparently, minimal support exists through the Linux kernel itself.  To my understanding, OpenGL currently requires a hardware driver to function.  It might be possible to find something that will emulate OpenGL capability on Linux, but this method would skip the benefit of the video card altogether I believe.

I suggest picking software applications in the meantime that don't rely on OpenGL.  SDL-related software might offer such an alternative, but my information on that project is somewhat outdated.

---

### Post by mumia55 on 2009-07-08
> **shatterblast said:**
> I forgot some of the dependencies for EnvyNG don't work well with PPCs, and I see the manufacturer type of your video card as ATI, which has slight issues with Jaunty.  I think it a matter of choosing the right driver.

I am having difficulty finding a hardware driver for your computer's video card.  Apparently, minimal support exists through the Linux kernel itself.  To my understanding, OpenGL currently requires a hardware driver to function.  It might be possible to find something that will emulate OpenGL capability on Linux, but this method would skip the benefit of the video card altogether I believe.

I suggest picking software applications in the meantime that don't rely on OpenGL.  SDL-related software might offer such an alternative, but my information on that project is somewhat outdated.

Alright, I'll follow your instructions, and I'll keep searching for the right driver and how to install it. Thanks for the help.
Still, if someone has the answer, I'm waiting here :)

---

