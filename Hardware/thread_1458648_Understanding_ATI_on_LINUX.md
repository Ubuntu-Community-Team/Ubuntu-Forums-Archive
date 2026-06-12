---
title: "Understanding ATI on LINUX"
date: 2010-04-20
forum: Hardware
---

### Post by tugalsan on 2010-04-20
can smo tells me what is 
1) xserver-xor-*
2) f gl rx
3) mesa driver
means?

-------------------

I have ATI Radeon Mobility x1600 card on my S1 Express Dual Lg computer.

I have tried ubuntu 8.04,9...., 10.04. However I could not solve 3D problem on any of them. 

Now; I think I have, a clean lucid 10.04 installation. And I want to play Regnum (and then may be try to run SolidWorks with wine). When I start Regnum it returns videoCardTooOld, installLatestDrivers or installDirectX error.

Is it possible play regnum with my card on lucid? Should i install one of the drivers above. Or should wait for another 5 months for 10.10 and ask the question again?

I am searching reading everything for 2 years about ati 1600 linux drivers. so far i tried some of them and crushed my linux 3-4 times. I even learn what it means to use alternate cd, backup my files, and re-install from live cd again.

Can anyone tells me what should i do step by step, because i do not want to re-install everything again and again. If you want me to do something like below please do not hesitate to ask; I will try to return to you ASAP.

My mission: For 2 years, I am trying hard to move windows to ubuntu. for now there is two big problem. One of it is ATI, the other is samba. I am using WindowsOnVirtualbox for my samba needs, but cannot do it for 3D applications.

--------------------------------------
in 1280x800 60Hz with waving tv out cloned monitor
me@mel:~$ glxgears
3036 frames in 5.0 seconds
869 frames in 5.0 seconds
879 frames in 5.0 seconds
877 frames in 5.0 seconds
880 frames in 5.0 seconds

---------------------------------------

me@mel:~$ glxinfo |grep vendor
server glx vendor string: SGI
client glx vendor string: Mesa Project and SGI
OpenGL vendor string: DRI R300 Project

-----------------------------------

me@mel:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.4
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_make_current_read, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap
OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 (RV530 71C5) 20090101 x86/MMX/SSE2 TCL DRI2
OpenGL version string: 1.5 Mesa 7.7.1
OpenGL extensions:
    GL_EXT_compiled_vertex_array, GL_EXT_texture_env_add, 
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_occlusion_query, GL_ARB_point_parameters, GL_ARB_provoking_vertex, 
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_MESAX_texture_float, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_array_bgra, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_blend_color, GL_EXT_blend_equation_separate, 
    GL_EXT_blend_func_separate, GL_EXT_blend_logic_op, GL_EXT_blend_minmax, 
    GL_EXT_blend_subtract, GL_EXT_convolution, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_framebuffer_blit, 
    GL_EXT_framebuffer_object, GL_EXT_fog_coord, 
    GL_EXT_gpu_program_parameters, GL_EXT_histogram, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels, 
    GL_EXT_point_parameters, GL_EXT_polygon_offset, GL_EXT_provoking_vertex, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, 
    GL_EXT_vertex_array, GL_EXT_vertex_array_bgra, GL_APPLE_packed_pixels, 
    GL_ATI_blend_equation_separate, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_ATI_separate_stencil, 
    GL_IBM_multimode_draw_arrays, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_MESA_window_pos, 
    GL_NV_blend_square, GL_NV_light_max_exponent, GL_NV_packed_depth_stencil, 
    GL_NV_texture_rectangle, GL_NV_texgen_reflection, GL_NV_vertex_program, 
    GL_OES_read_format, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays

64 GLX Visuals
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xc1 24 tc  0 24  0 r  .  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0xc2 24 tc  0 24  0 r  .  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0xc3 24 tc  0 24  0 r  y  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0xc4 24 tc  0 24  0 r  y  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0xc5 24 tc  0 24  0 r  .  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0xc6 24 tc  0 24  0 r  .  .  8  8  8  0  0 16  0 16 16 16  0  0 0 Slow
0xc7 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0xc8 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0 16 16 16  0  0 0 Slow
0xc9 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0xca 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0xcb 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0xcc 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0xcd 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0xce 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0xcf 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0xd0 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0xd1 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xd2 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xd3 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xd4 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xd5 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None
0xd6 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0xd7 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0xd8 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0xd9 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0xda 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0xdb 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0xdc 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xdd 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0xde 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0xdf 24 dc  0 24  0 r  .  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0xe0 24 dc  0 24  0 r  .  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0xe1 24 dc  0 24  0 r  y  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0xe2 24 dc  0 24  0 r  y  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0xe3 24 dc  0 24  0 r  .  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0xe4 24 dc  0 24  0 r  .  .  8  8  8  0  0 16  0 16 16 16  0  0 0 Slow
0xe5 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0xe6 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0 16 16 16  0  0 0 Slow
0xe7 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0xe8 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0xe9 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0xea 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0xeb 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0xec 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0xed 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0xee 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0xef 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xf0 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xf1 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xf2 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xf3 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None
0xf4 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0xf5 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None
0xf6 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0xf7 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0xf8 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0xf9 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0xfa 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0xfb 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xfc 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0xfd 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x60 32 tc  0 32  0 r  y  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None

96 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x61  0 tc  0 16  0 r  .  .  5  6  5  0  0  0  0  0  0  0  0  0 0 None
0x62  0 tc  0 16  0 r  .  .  5  6  5  0  0  0  0 16 16 16  0  0 0 Slow
0x63  0 tc  0 16  0 r  y  .  5  6  5  0  0  0  0  0  0  0  0  0 0 None
0x64  0 tc  0 16  0 r  y  .  5  6  5  0  0  0  0 16 16 16  0  0 0 Slow
0x65  0 tc  0 16  0 r  .  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x66  0 tc  0 16  0 r  .  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x67  0 tc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x68  0 tc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x69  0 tc  0 16  0 r  .  .  5  6  5  0  0 24  0  0  0  0  0  0 0 None
0x6a  0 tc  0 16  0 r  .  .  5  6  5  0  0 24  0 16 16 16  0  0 0 Slow
0x6b  0 tc  0 16  0 r  y  .  5  6  5  0  0 24  0  0  0  0  0  0 0 None
0x6c  0 tc  0 16  0 r  y  .  5  6  5  0  0 24  0 16 16 16  0  0 0 Slow
0x6d  0 tc  0 16  0 r  .  .  5  6  5  0  0 24  8  0  0  0  0  0 0 None
0x6e  0 tc  0 16  0 r  .  .  5  6  5  0  0 24  8 16 16 16  0  0 0 Slow
0x6f  0 tc  0 16  0 r  y  .  5  6  5  0  0 24  8  0  0  0  0  0 0 None
0x70  0 tc  0 16  0 r  y  .  5  6  5  0  0 24  8 16 16 16  0  0 0 Slow
0x71  0 tc  0 24  0 r  .  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0x72  0 tc  0 24  0 r  .  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0x73  0 tc  0 24  0 r  y  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0x74  0 tc  0 24  0 r  y  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0x75  0 tc  0 24  0 r  .  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x76  0 tc  0 24  0 r  .  .  8  8  8  0  0 16  0 16 16 16  0  0 0 Slow
0x77  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x78  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  0 16 16 16  0  0 0 Slow
0x79  0 tc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0x7a  0 tc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0x7b  0 tc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0x7c  0 tc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0x7d  0 tc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0x7e  0 tc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0x7f  0 tc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0x80  0 tc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0x81  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x82  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x83  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x84  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x85  0 tc  0 32  0 r  .  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None
0x86  0 tc  0 32  0 r  .  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0x87  0 tc  0 32  0 r  y  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None
0x88  0 tc  0 32  0 r  y  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0x89  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x8a  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x8b  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x8c  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x8d  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x8e  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x8f  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x90  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x91  0 dc  0 16  0 r  .  .  5  6  5  0  0  0  0  0  0  0  0  0 0 None
0x92  0 dc  0 16  0 r  .  .  5  6  5  0  0  0  0 16 16 16  0  0 0 Slow
0x93  0 dc  0 16  0 r  y  .  5  6  5  0  0  0  0  0  0  0  0  0 0 None
0x94  0 dc  0 16  0 r  y  .  5  6  5  0  0  0  0 16 16 16  0  0 0 Slow
0x95  0 dc  0 16  0 r  .  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x96  0 dc  0 16  0 r  .  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x97  0 dc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x98  0 dc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x99  0 dc  0 16  0 r  .  .  5  6  5  0  0 24  0  0  0  0  0  0 0 None
0x9a  0 dc  0 16  0 r  .  .  5  6  5  0  0 24  0 16 16 16  0  0 0 Slow
0x9b  0 dc  0 16  0 r  y  .  5  6  5  0  0 24  0  0  0  0  0  0 0 None
0x9c  0 dc  0 16  0 r  y  .  5  6  5  0  0 24  0 16 16 16  0  0 0 Slow
0x9d  0 dc  0 16  0 r  .  .  5  6  5  0  0 24  8  0  0  0  0  0 0 None
0x9e  0 dc  0 16  0 r  .  .  5  6  5  0  0 24  8 16 16 16  0  0 0 Slow
0x9f  0 dc  0 16  0 r  y  .  5  6  5  0  0 24  8  0  0  0  0  0 0 None
0xa0  0 dc  0 16  0 r  y  .  5  6  5  0  0 24  8 16 16 16  0  0 0 Slow
0xa1  0 dc  0 24  0 r  .  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0xa2  0 dc  0 24  0 r  .  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0xa3  0 dc  0 24  0 r  y  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0xa4  0 dc  0 24  0 r  y  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0xa5  0 dc  0 24  0 r  .  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0xa6  0 dc  0 24  0 r  .  .  8  8  8  0  0 16  0 16 16 16  0  0 0 Slow
0xa7  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0xa8  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  0 16 16 16  0  0 0 Slow
0xa9  0 dc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0xaa  0 dc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0xab  0 dc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0xac  0 dc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0xad  0 dc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0xae  0 dc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0xaf  0 dc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0xb0  0 dc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0xb1  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xb2  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xb3  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xb4  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xb5  0 dc  0 32  0 r  .  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None
0xb6  0 dc  0 32  0 r  .  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0xb7  0 dc  0 32  0 r  y  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None
0xb8  0 dc  0 32  0 r  y  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0xb9  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0xba  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0xbb  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0xbc  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0xbd  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xbe  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0xbf  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xc0  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow

--------------------------

if you know how to produce a list of modules from snaptics to give you, please let me know "how to". Then, i can return to you with my log file.

--------------------------------


Comments will highly appriciated.

Tugalsan Karabacak
Electric & Electronics Engr.
Mobile Appl. & Comms.
International Welding Engr.
[EMAIL="tugalsan@gmail.com"]tugalsan@gmail.com[/EMAIL]

---

### Post by zodiac09 on 2010-04-20
I have an ATI card in my laptop.
 
What u listed there are different drivers for ATI cards. They are made by different groups of people. Some are open source some are not. You can google each one to find out who makes them and what not. 
 
I prefer to use the driver from AMD's website. It is update frequently, and i find it very stable. Its not open source but it will enable 3D effects!
 
U can download it from here: 
[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)
 
To install it run this command in terminal in the same dir as the installation script:
 
sudo sh ./ati-driver-installer-10-3-x86.x86_64.run
 
providing that is the version you have. if the file doesn't run u may have to make the file executable. To do so type the following in terminal:
 
sudo chmod +x ati-driver-installer-10-3-x86.x86_64.run

---

### Post by ultiva on 2010-04-20
Hmm... Maybe I don't understand everything, but why do such strange things instead of installing ATI driver (fglrx) provided by Ubuntu ? My Radeon 5650 works flawlessly with ATI driver provided by Lucid Lynx and installation is limited to just a few clicks. If Ubuntu doesn't prompt about drivers after installation You have to enter System->Administration->Device drivers and enable ATI driver - that's all. Looks like Ubuntu 10.04 installs Catalyst 10.3

---

### Post by Mark Phelps on 2010-04-20
The OP has a Radeon X1600 card -- for which ATI dropped Linux driver support over a year ago.  So, telling them to install the restricted drivers is not only wasting their time, it will corrupt their display forcing them to remove those drivers.

Unless you are using one of the newer HD 3x/4x/5x ATI cards, there are no ATI Linux drivers that will work with your card and any of the recent (9.x, 10.x) versions of Ubuntu.  Only the open-source drivers (installed by default) will work for you.  And, these drivers only provide minimal acceleration -- nothing along the lines of the ATI fglrx drivers.

Also, don't try using EnvyNG to force a driver install.  That, too, will end up corrupting your display and force you to have to remove them.

---

### Post by ultiva on 2010-04-20
Yes, it's look like You're right about that. There is no support for X1600 in catalyst 10.3. Amd site says something about legacy support. I'll look for that.

---

### Post by Yellow Pasque on 2010-04-20
> **ultiva said:**
> Yes, it's look like You're right about that. There is no support for X1600 in catalyst 10.3. Amd site says something about legacy support. I'll look for that.
You'll need to run an older distro to use the "legacy" Catalyst/fglrx drivers (e.g. Ubuntu Hardy, or Debian Lenny).

---

### Post by tugalsan on 2010-04-21
I want to try installing an old distro but before that:

Does anyone have real life experience with my card with these distros? 

And what do I have to do exactly afterwards, to install my ATI Driver? 

Can you please share your experiences?

---

### Post by gradinaruvasile on 2010-04-21
> **tugalsan said:**
> I want to try installing an old distro but before that:

Does anyone have real life experience with my card with these distros? 

And what do I have to do exactly afterwards, to install my ATI Driver? 

Can you please share your experiences?

My experience with Ubuntu 8.04-8.10 - X1600 and x1300 - X is buggy with both fglrx and OSS drivers - random lockups, crashes etc. 

But the OSS drivers are beginning to shape up - older cards such as 7500 mobility are rock solid on Ubuntu 8.04/8.10 (and it seems all features are supported).
I assume the fglrx-not-supported-series will reach that point if the devs focus on that (i would say that focusing on cards not supported by fglrx is better for the community).

Regnum has a safe mode AFAIK. Its somewhere in the settings in the initial screens.

---

### Post by tugalsan on 2010-04-21
By the way, I do not undertsand, why my card catagorized as old everywhere I go. It has 512MB internal RAM and PCI Express. By stealing from Memory, I have seen even 2GB in XP. It is just so disappointing for me to sell it and buy an equvalient laptop with paying extra 1000 dolars.

---

### Post by gradinaruvasile on 2010-04-21
That amount of memory is just for PR. How does it help you?
I have 128 MB on a 7600GS and it was enough for any game i played on it. More than 512 MB is just overkill - maybe not for the latest and most demanding Windows games out there, but those wont run on lower spec (here i mean performance, not amount of memory) cards regardless of driver support/memory amount. Other than that is wasted memory.

Anyway, Ati decided to kill support for your card. Look up on their site, maybe they can convince you they had the right reasons (i dont buy it, maybe i would have if they would have produced at least nvidia-level reliable drivers for the 2-3-4-5 series. But they did not).
Compare that with nvidia that supports all their cards AND have support for the latest xorg and kernels really fast. And add that their drivers are rock stable.

---

### Post by ReallNeurotiq on 2010-04-21
my two cents on this one.

I have an ATi Radeon 4850 and Lucid Lynx 10.04.

It works amazing, sometimes you see tiny artifacts but only while holding alt ctrl and turning the cube.

First time ive been this confident
about the direction of linux/ubuntu. This compatibility
wasnt existent a year ago, I tried.

It is amazing now. and maybe arguable that the ATi cards look just as good as the nVIDIA cards now. 

So my response to ATi, the Catalyst control center is very useful and it works fine

---

### Post by realzippy on 2010-04-21
OP has an older ATI card,so your 2 cents are worthless.
BTW,fglrx is still miles away from NVIDIA.
OP should install 8.04/8.10 as suggested before and the old fglrx driver,
which should work.
For the dropped linux support for "old" cards,do not blame ATI,they do not hear you.
Just stop buying that c..p.

---

### Post by tugalsan on 2010-04-26
in this side I saw that OpenSolaris is supporting these ati cards:
[http://www.opensolaris.com/learn/features/whats-new/200906/](http://www.opensolaris.com/learn/features/whats-new/200906/)
Radeon 9250, 9550, X1200, X1300, X1400, X1500, X1600, X1650, X1700,  X1800, X1900, X1950, X2100, X2300, HD 2900, HD 2400, HD 2600, HD 3100,  HD 3200, HD3300,  HD 3450, HD 3470, HD 4350, HD 4550, HD 4570, HD 4650,  HD 4670, HD 4850, HD 4870
Radeon HD 4800 Series; Everest, K2, Denali ATI FirePro, Radeon HD  3100/3200/3300 Series, Mobility Radeon HD 3400, Mobility Radeon HD 3650,  HD 3670, Mobility FireGL V5700, Mobility Radeon HD 3850, HD 3850 X2, HD  3870, HD3870 X2

Although "Mobility Radeon x1600" is not fully written, but X1600 is. Should I give a try to OpenSolaris 2009.06?

Anyone has experience on Solaris OS?

---

### Post by tugalsan on 2010-05-04
I think opens solaris is not compatable also:
[https://cn.opensolaris.org/jive/thread.jspa?threadID=79779](https://cn.opensolaris.org/jive/thread.jspa?threadID=79779)

---

### Post by antiram on 2010-05-04
the support isnt dropped, it is only moved to the open source radeon driver. Ati is the only graphic manufacturer with open specifications and they pay also staffs for developing the oss driver. There is also a next generation gallium3D driver available for the old radeons.

if you get only OpenGL 1.5 with a default install and this is to low for your game, you could use xorg-edgers ppa and maybe a newer kernel from mainline ppa to get OpenGL 2.0 or 2.1.

here is a active forum (with ati staffs) for the oss driver
[http://www.phoronix.com/forums/forumdisplay.php?f=43](http://www.phoronix.com/forums/forumdisplay.php?f=43)

---

