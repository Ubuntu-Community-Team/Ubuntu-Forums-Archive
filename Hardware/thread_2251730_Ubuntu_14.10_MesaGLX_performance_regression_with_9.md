---
title: "Ubuntu 14.10 Mesa/GLX performance regression with 945gm"
date: 2014-11-06
forum: Hardware
---

### Post by delorean1 on 2014-11-06
Since the upgrade to 14.10, glxgears has gone from 280 fps to 70 fps.
output of anything using glx i.e. glxinfo glxgears or an app such a vice will show

libGL error: Version 4 or later of flush extension not found
libGL error: failed to load driver: i915

The performance of that which uses glx/mesa has been crippled and is obviously using no hardware acceleration.
Scattered mentions of this issue have been posted on the net elsewhere.

intel at 01.org for there part has stated that the 4th quarter release of the intel open driver will be for 14.04 and not 14.10.

surely this broken adaptation can be unbroken, im not sure how


```
uname -a
Linux jordan-Satellite-P205 3.16.0-24-generic #32-Ubuntu SMP Tue Oct 28 13:13:18 UTC 2014 i686 i686 i686 GNU/Linux
```

```
jordan@jordan-Satellite-P205:~$ glxinfo
name of display: :0
libGL error: Version 4 or later of flush extension not found
libGL error: failed to load driver: i915
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_fbconfig_float, GLX_ARB_framebuffer_sRGB, GLX_ARB_multisample, 
    GLX_EXT_create_context_es2_profile, GLX_EXT_framebuffer_sRGB, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_INTEL_swap_event, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, GLX_SGI_swap_control
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_create_context_robustness, GLX_ARB_fbconfig_float, 
    GLX_ARB_framebuffer_sRGB, GLX_ARB_get_proc_address, GLX_ARB_multisample, 
    GLX_EXT_buffer_age, GLX_EXT_create_context_es2_profile, 
    GLX_EXT_fbconfig_packed_float, GLX_EXT_framebuffer_sRGB, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_INTEL_swap_event, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_query_renderer, 
    GLX_MESA_swap_control, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync
GLX version: 1.4
GLX extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_fbconfig_float, GLX_ARB_framebuffer_sRGB, 
    GLX_ARB_get_proc_address, GLX_ARB_multisample, 
    GLX_EXT_create_context_es2_profile, GLX_EXT_framebuffer_sRGB, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_INTEL_swap_event, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_query_renderer, 
    GLX_MESA_swap_control, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync
OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) 945GM x86/MMX/SSE2
OpenGL version string: 1.4 Mesa 10.4.0-devel
OpenGL extensions:
    GL_3DFX_texture_compression_FXT1, GL_AMD_shader_trinary_minmax, 
    GL_ANGLE_texture_compression_dxt3, GL_ANGLE_texture_compression_dxt5, 
    GL_APPLE_object_purgeable, GL_APPLE_packed_pixels, 
    GL_APPLE_vertex_array_object, GL_ARB_ES2_compatibility, 
    GL_ARB_clear_buffer_object, GL_ARB_compressed_texture_pixel_storage, 
    GL_ARB_copy_buffer, GL_ARB_debug_output, GL_ARB_depth_texture, 
    GL_ARB_draw_buffers, GL_ARB_draw_elements_base_vertex, 
    GL_ARB_explicit_attrib_location, GL_ARB_explicit_uniform_location, 
    GL_ARB_fragment_program, GL_ARB_fragment_shader, 
    GL_ARB_framebuffer_object, GL_ARB_get_program_binary, 
    GL_ARB_half_float_pixel, GL_ARB_internalformat_query, 
    GL_ARB_invalidate_subdata, GL_ARB_map_buffer_alignment, 
    GL_ARB_map_buffer_range, GL_ARB_multi_bind, GL_ARB_multisample, 
    GL_ARB_multitexture, GL_ARB_pixel_buffer_object, GL_ARB_point_parameters, 
    GL_ARB_point_sprite, GL_ARB_provoking_vertex, GL_ARB_robustness, 
    GL_ARB_sampler_objects, GL_ARB_separate_shader_objects, 
    GL_ARB_shader_objects, GL_ARB_shading_language_100, GL_ARB_shadow, 
    GL_ARB_sync, GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle, 
    GL_ARB_texture_storage, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_array_object, GL_ARB_vertex_attrib_binding, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_window_pos, GL_ATI_blend_equation_separate, GL_ATI_draw_buffers, 
    GL_ATI_separate_stencil, GL_ATI_texture_env_combine3, GL_EXT_abgr, 
    GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_equation_separate, 
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_compiled_vertex_array, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_blit, 
    GL_EXT_framebuffer_object, GL_EXT_gpu_program_parameters, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_depth_stencil, 
    GL_EXT_packed_pixels, GL_EXT_pixel_buffer_object, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_provoking_vertex, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_shadow_funcs, GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_compression_dxt1, GL_EXT_texture_compression_s3tc, 
    GL_EXT_texture_cube_map, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle, 
    GL_EXT_texture_sRGB, GL_EXT_texture_sRGB_decode, GL_EXT_vertex_array, 
    GL_IBM_multimode_draw_arrays, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_KHR_context_flush_control, GL_KHR_debug, GL_MESA_pack_invert, 
    GL_MESA_window_pos, GL_MESA_ycbcr_texture, GL_NV_blend_square, 
    GL_NV_light_max_exponent, GL_NV_packed_depth_stencil, 
    GL_NV_texgen_reflection, GL_NV_texture_env_combine4, 
    GL_NV_texture_rectangle, GL_OES_EGL_image, GL_OES_read_format, 
    GL_S3_s3tc, GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays

OpenGL ES profile version string: OpenGL ES 2.0 Mesa 10.4.0-devel
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 1.0.16
OpenGL ES profile extensions:
    GL_ANGLE_texture_compression_dxt3, GL_ANGLE_texture_compression_dxt5, 
    GL_APPLE_texture_max_level, GL_EXT_blend_minmax, 
    GL_EXT_discard_framebuffer, GL_EXT_map_buffer_range, 
    GL_EXT_multi_draw_arrays, GL_EXT_read_format_bgra, 
    GL_EXT_separate_shader_objects, GL_EXT_texture_compression_dxt1, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_format_BGRA8888, 
    GL_EXT_texture_type_2_10_10_10_REV, GL_EXT_unpack_subimage, 
    GL_KHR_context_flush_control, GL_NV_draw_buffers, 
    GL_NV_fbo_color_attachments, GL_NV_read_buffer, GL_OES_EGL_image, 
    GL_OES_depth24, GL_OES_depth_texture, GL_OES_element_index_uint, 
    GL_OES_fbo_render_mipmap, GL_OES_get_program_binary, GL_OES_mapbuffer, 
    GL_OES_packed_depth_stencil, GL_OES_rgb8_rgba8, GL_OES_stencil8, 
    GL_OES_surfaceless_context, GL_OES_texture_3D, GL_OES_texture_npot, 
    GL_OES_vertex_array_object

12 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x020 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x021 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x075 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x076 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x077 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x078 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x079 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x07a 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x07b 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x07c 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x07d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x05c 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None

24 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x05d  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x05e  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x05f  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x060  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x061 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x062 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x063 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x064 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x065  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x066  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x067 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x068 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x069  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x06a  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x06b  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x06c  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x06d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x06e 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x06f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x070 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x071  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x072  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x073 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x074 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow

```


Jordan

---

### Post by ajgreeny on 2014-11-06
That is the way glxgears has worked for some time now.

It is not intended as a benchmark utility for your machine, and it does say in the output that reported framerates are now the same as monitor refresh rates, so your 70fps is probably what you should expect to see if your monitor refresh rate is 70.

```
~$ glxgears 
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
380 frames in 5.0 seconds = 75.953 FPS
375 frames in 5.0 seconds = 74.845 FPS
375 frames in 5.0 seconds = 74.847 FPS
```

---

### Post by delorean1 on 2014-11-06
GLXgears was one of many noted differences.   Re read the post. Programs running under 14.10 are running at around 7fps and use over 70% processor at idle as such in vice x64
note the posted error

---

### Post by ajgreeny on 2014-11-06
I have reread your post and don't really understand in any detail what your problem is.

In any case, whenever I have used glxgears in the past few versions of Ubuntu I have always got more or less the output I showed with the fps figure being equal to my monitor refresh rate.

I will have to leave it to others to try to help you.

---

### Post by delorean1 on 2014-11-06
```
jordan@jordan-Satellite-P205:~$ glxinfo
name of display: :0
libGL error: Version 4 or later of flush extension not found
libGL error: failed to load driver: i915

```

---

### Post by delorean1 on 2014-11-11
[https://askubuntu.com/questions/548130/xbmc-libgl-error-failed-to-load-driver-i915/548598#548598](https://askubuntu.com/questions/548130/xbmc-libgl-error-failed-to-load-driver-i915/548598#548598)

---

### Post by delorean1 on 2014-11-11
[https://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg4539055.html](https://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg4539055.html)

---

