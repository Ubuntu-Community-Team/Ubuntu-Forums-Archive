---
title: "New ATi drivers, but compiz won't run... (Gutsy)"
date: 2007-10-25
forum: Hardware &amp; Laptops
---

### Post by MartinuxP on 2007-10-25
Hi everybody, i've just downloaded and installed the new ATi drivers (8.42.3).
AiGLX and composite rendering are enabled but when I try to eneble desktop effetcs it says "Desktop Effect cuold not be enabled."
My board is an integrated X700 (notebook Toshiba M70).
here's some logs:
```
martinux@martinux-laptop:~$ cat /var/log/Xorg.0.log | grep -i aiglx
(**) Option "AIGLX" "on"
(**) AIGLX enabled
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
(II) AIGLX: Loaded and initialized /usr/lib/dri/fglrx_dri.so
```

```
martinux@martinux-laptop:~$ glxinfo
name of display: :0.0
display: :0 screen: 0
direct rendering: Yes
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
GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control,
GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control,
GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync,
GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer,
GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method,
GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON X700
OpenGL version string: 2.0.6958 Release
OpenGL extensions:
GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program,
GL_ARB_fragment_shader, GL_ARB_multisample, GL_ARB_multitexture,
GL_ARB_occlusion_query, GL_ARB_point_parameters, GL_ARB_point_sprite,
GL_ARB_shader_objects, GL_ARB_shading_language_100, GL_ARB_shadow,
GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp,
GL_ARB_texture_compression, GL_ARB_texture_cube_map,
GL_ARB_texture_env_add, GL_ARB_texture_env_combine,
GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3,
GL_ARB_texture_float, GL_ARB_texture_mirrored_repeat,
GL_ARB_texture_rectangle, GL_ARB_transpose_matrix,
GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader,
GL_ARB_window_pos, GL_ATI_draw_buffers, GL_ATI_envmap_bumpmap,
GL_ATI_fragment_shader, GL_ATI_meminfo, GL_ATI_separate_stencil,
GL_ATI_texture_compression_3dc, GL_ATI_texture_env_combine3,
GL_ATI_texture_float, GL_EXT_bgra, GL_EXT_blend_color,
GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract,
GL_EXT_compiled_vertex_array, GL_EXT_copy_texture,
GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_object,
GL_EXT_framebuffer_object, GL_EXT_gpu_program_parameters,
GL_EXT_multi_draw_arrays, GL_EXT_packed_depth_stencil,
GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_rescale_normal,
GL_EXT_secondary_color, GL_EXT_separate_specular_color,
GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, GL_EXT_subtexture,
GL_EXT_texgen_reflection, GL_EXT_texture3D,
GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map,
GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add,
GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias,
GL_EXT_texture_mirror_clamp, GL_EXT_texture_object,
GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, GL_EXT_vertex_array,
GL_KTX_buffer_region, GL_NV_blend_square, GL_NV_texgen_reflection,
GL_SGIS_generate_mipmap, GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod,
GL_WIN_swap_hint, WGL_EXT_swap_control
...
```

```
martinux@martinux-laptop:~$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON X700
OpenGL version string: 2.0.6958 Release
```

---

### Post by drachenstern on 2007-10-25
xorg.conf?

---

### Post by pete.dawgg on 2007-11-08
> ATi drivers (8.42.3).
AiGLX and composite rendering are enabled
HOW is this enabled?
as far as i know ATI-drivers NEVER support aiglx, the new version which is supposed to be out pretty soon might, though.

---

### Post by Mondoman on 2007-11-08
Using Synaptic Package Manager, make sure "xserver-xgl" is installed.

---

