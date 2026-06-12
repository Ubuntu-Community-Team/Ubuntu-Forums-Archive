---
title: "Intel video no compiz under Ubuntu Intrepid"
date: 2008-11-15
forum: General Help
---

### Post by frankzen on 2008-11-15
I am running Intel 865 video on Intrepid..the only fail I get is on texture_from_pixmap.. and I cannot enable more than 1 deaktop in the settings manager. Can this be fixed ??
__________________

compiz-check output:

Distribution: Ubuntu 8.10
Desktop environment: GNOME
Graphics chip: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
Driver in use: intel
Rendering method: AIGLX

Checking if it's possible to run Compiz on your system...

Checking for texture_from_pixmap... [FAIL]
Checking for non power of two support... [ OK ]
Checking for composite extension... [ OK ]
Checking for FBConfig... [ OK ]
Checking for hardware/setup problems... [ OK ]


compiz output:

frank@frank-desktop:~$ compiz
Checking for Xgl: not present.
Detected PCI ID for VGA:
Checking for texture_from_pixmap: not present.
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present.
aborting and using fallback: /usr/bin/metacity


output of glxinfo:


frank@frank-desktop:~$ glxinfo
name of display: :0.0
display: :0 screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap,
GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer,
GLX_OML_swap_method, GLX_SGI_swap_control, GLX_SGIS_multisample,
GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: NVIDIA Corporation
client glx version string: 1.3
client glx extensions:
GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info,
GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync,
GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer,
GLX_SGI_swap_control, GLX_NV_float_buffer
GLX version: 1.2
GLX extensions:
GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
GLX_EXT_import_context, GLX_SGIX_fbconfig, GLX_SGI_swap_control,
GLX_ARB_get_proc_address
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 865G 20061102 x86/MMX/SSE2
OpenGL version string: 1.3 Mesa 7.2
OpenGL extensions:
GL_ARB_multitexture, GL_ARB_point_parameters, GL_ARB_texture_border_clamp,
GL_ARB_texture_compression, GL_ARB_texture_cube_map,
GL_ARB_texture_env_add, GL_ARB_texture_env_combine,
GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat,
GL_ARB_texture_non_power_of_two, GL_ARB_vertex_program, GL_ARB_window_pos,
GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_func_separate,
GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint,
GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays,
GL_EXT_packed_pixels, GL_EXT_rescale_normal, GL_EXT_secondary_color,
GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_texture3D,
GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add,
GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_vertex_array,
GL_IBM_texture_mirrored_repeat, GL_NV_blend_square,
GL_NV_light_max_exponent, GL_NV_texture_rectangle,
GL_NV_texgen_reflection, GL_SGIS_generate_mipmap, GL_SGIS_texture_lod

3 GLX Visuals
visual x bf lv rg d st colorbuffer ax dp st accumbuffer ms cav
id dep cl sp sz l ci b ro r g b a bf th cl r g b a ns b eat
----------------------------------------------------------------------
0x21 24 tc 0 32 0 r y . 8 8 8 8 0 24 8 0 0 0 0 0 0 None
0x22 24 dc 0 32 0 r y . 8 8 8 8 0 24 8 0 0 0 0 0 0 None
0x5f 32 tc 0 32 0 r . . 8 8 8 8 0 0 0 0 0 0 0 0 0 None

36 GLXFBConfigs:
visual x bf lv rg d st colorbuffer ax dp st accumbuffer ms cav
id dep cl sp sz l ci b ro r g b a bf th cl r g b a ns b eat
----------------------------------------------------------------------
0x60 0 tc 0 32 0 r . . 8 8 8 8 0 0 0 0 0 0 0 0 0 None
0x61 0 tc 0 32 0 r . . 8 8 8 8 0 0 0 16 16 16 16 0 0 Slow
0x62 0 tc 0 32 0 r y . 8 8 8 8 0 0 0 0 0 0 0 0 0 None
0x63 0 tc 0 32 0 r y . 8 8 8 8 0 0 0 16 16 16 16 0 0 Slow
0x64 0 tc 0 32 0 r y . 8 8 8 8 0 0 0 0 0 0 0 0 0 None
0x65 0 tc 0 32 0 r y . 8 8 8 8 0 0 0 16 16 16 16 0 0 Slow
0x66 0 tc 0 32 0 r . . 8 8 8 8 0 24 8 0 0 0 0 0 0 None
0x67 0 tc 0 32 0 r . . 8 8 8 8 0 24 8 16 16 16 16 0 0 Slow
0x68 0 tc 0 32 0 r y . 8 8 8 8 0 24 8 0 0 0 0 0 0 None
0x69 0 tc 0 32 0 r y . 8 8 8 8 0 24 8 16 16 16 16 0 0 Slow
0x6a 0 tc 0 32 0 r y . 8 8 8 8 0 24 8 0 0 0 0 0 0 None
0x6b 0 tc 0 32 0 r y . 8 8 8 8 0 24 8 16 16 16 16 0 0 Slow
0x6c 0 tc 0 32 0 r . . 8 8 8 8 0 24 8 0 0 0 0 0 0 None
0x6d 0 tc 0 32 0 r . . 8 8 8 8 0 24 8 16 16 16 16 0 0 Slow
0x6e 0 tc 0 32 0 r y . 8 8 8 8 0 24 8 0 0 0 0 0 0 None
0x6f 0 tc 0 32 0 r y . 8 8 8 8 0 24 8 16 16 16 16 0 0 Slow
0x70 0 tc 0 32 0 r y . 8 8 8 8 0 24 8 0 0 0 0 0 0 None
0x71 0 tc 0 32 0 r y . 8 8 8 8 0 24 8 16 16 16 16 0 0 Slow
0x72 0 dc 0 32 0 r . . 8 8 8 8 0 0 0 0 0 0 0 0 0 None
0x73 0 dc 0 32 0 r . . 8 8 8 8 0 0 0 16 16 16 16 0 0 Slow
0x74 0 dc 0 32 0 r y . 8 8 8 8 0 0 0 0 0 0 0 0 0 None
0x75 0 dc 0 32 0 r y . 8 8 8 8 0 0 0 16 16 16 16 0 0 Slow
0x76 0 dc 0 32 0 r y . 8 8 8 8 0 0 0 0 0 0 0 0 0 None
0x77 0 dc 0 32 0 r y . 8 8 8 8 0 0 0 16 16 16 16 0 0 Slow
0x78 0 dc 0 32 0 r . . 8 8 8 8 0 24 8 0 0 0 0 0 0 None
0x79 0 dc 0 32 0 r . . 8 8 8 8 0 24 8 16 16 16 16 0 0 Slow
0x7a 0 dc 0 32 0 r y . 8 8 8 8 0 24 8 0 0 0 0 0 0 None
0x7b 0 dc 0 32 0 r y . 8 8 8 8 0 24 8 16 16 16 16 0 0 Slow
0x7c 0 dc 0 32 0 r y . 8 8 8 8 0 24 8 0 0 0 0 0 0 None
0x7d 0 dc 0 32 0 r y . 8 8 8 8 0 24 8 16 16 16 16 0 0 Slow
0x7e 0 dc 0 32 0 r . . 8 8 8 8 0 24 8 0 0 0 0 0 0 None
0x7f 0 dc 0 32 0 r . . 8 8 8 8 0 24 8 16 16 16 16 0 0 Slow
0x80 0 dc 0 32 0 r y . 8 8 8 8 0 24 8 0 0 0 0 0 0 None
0x81 0 dc 0 32 0 r y . 8 8 8 8 0 24 8 16 16 16 16 0 0 Slow
0x82 0 dc 0 32 0 r y . 8 8 8 8 0 24 8 0 0 0 0 0 0 None
0x83 0 dc 0 32 0 r y . 8 8 8 8 0 24 8 16 16 16 16 0 0 Slow

frank@frank-desktop:~$ 

The problem I guess is " no texture from pixmap" whatever that is. But Compiz runs beautifully on
Debian Sid on my other partition !!

I also can setup 4 desktops, but in the settings manager can't set more than 1...weird.

---

