---
title: "No direct rendering using propitary fglrx"
date: 2009-02-18
forum: Installation &amp; Upgrades
---

### Post by hiwe on 2009-02-18
I have a ATI radeon 4850 card, trying to enable direct rendering using the ATI propitary fglrx driver available from ubuntu sources. Can anyone give me clue what wrong ?

hi@tulkas:~$ ls -l /usr/lib/dri/fglrx_dri.so 
-rw-r--r-- 1 root root 17618124 2008-10-24 08:12 /usr/lib/dri/fglrx_dri.so

hi@tulkas:~$ LIBGL_DEBUG=verbose glxinfo > /dev/null
libGL: XF86DRIGetClientDriverName: 8.54.3 fglrx (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/fglrx_dri.so
libGL error: Neither __driCreateScreen or __driCreateNewScreen are defined in fglrx_dri.so!
libGL error: unable to find driver: fglrx_dri.so
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7c4a7c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7c4a891]
#2 /usr/lib/libX11.so.6 [0xb7cc1521]
#3 /usr/X11R6/lib/libGL.so.1 [0xb7f32934]
#4 /usr/X11R6/lib/libGL.so.1(__glXInitialize+0x167) [0xb7f32c88]
#5 /usr/X11R6/lib/libGL.so.1 [0xb7f2e059]
#6 /usr/X11R6/lib/libGL.so.1(glXChooseVisual+0x51) [0xb7f2f7bb]
#7 glxinfo [0x804a369]
#8 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7d85685]
#9 glxinfo [0x8048e81]

hi@tulkas:~$ glxinfo
name of display: :0.0
libGL: XF86DRIGetClientDriverName: 8.54.3 fglrx (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/fglrx_dri.so
libGL error: Neither __driCreateScreen or __driCreateNewScreen are defined in fglrx_dri.so!
libGL error: unable to find driver: fglrx_dri.so
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7da67c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7da6891]
#2 /usr/lib/libX11.so.6 [0xb7e1d521]
#3 /usr/X11R6/lib/libGL.so.1 [0xb808e934]
#4 /usr/X11R6/lib/libGL.so.1(__glXInitialize+0x167) [0xb808ec88]
#5 /usr/X11R6/lib/libGL.so.1 [0xb808a059]
#6 /usr/X11R6/lib/libGL.so.1(glXChooseVisual+0x51) [0xb808b7bb]
#7 glxinfo [0x804a369]
#8 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7ee1685]
#9 glxinfo [0x8048e81]
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, 
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIS_multisample, 
    GLX_SGIX_visual_select_group
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 4800 Series
OpenGL version string: 1.2 (1.4 (2.1.8087 Release))
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shadow, 
    GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_non_power_of_two, GL_ARB_transpose_matrix, 
    GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_copy_texture, GL_EXT_draw_range_elements, GL_EXT_fog_coord, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_vertex_array, 
    GL_ATI_texture_env_combine3, GL_ATIX_texture_env_combine3, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_NV_blend_square, GL_NV_texgen_reflection, GL_NV_texture_rectangle, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_shadow_ambient, 
    GL_SUN_multi_draw_arrays

---

