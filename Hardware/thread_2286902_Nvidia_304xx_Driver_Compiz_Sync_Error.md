---
title: "Nvidia 304xx Driver: Compiz Sync Error"
date: 2015-07-15
forum: Hardware
---

### Post by onlinecloud1 on 2015-07-15
on u/buntu when i login, unity lags alot and display random junk on the screen.
and journalctl has some error's:
```
Jul 15 11:11:58 Latitude-D820-Ubuntu kernel: NVRM: Xid (PCI:0000:01:00): 1, Channel 00000002 Method 00000060 Data beef0233
Jul 15 11:11:58 Latitude-D820-Ubuntu kernel: NVRM: Xid (PCI:0000:01:00): 9, Channel 00000002 Instance 00000000 Intr 00100000
Jul 15 11:11:58 Latitude-D820-Ubuntu kernel: NVRM: Xid (PCI:0000:01:00): 1, Channel 00000002 Method 00000060 Data beef0233
Jul 15 11:11:59 Latitude-D820-Ubuntu kernel: NVRM: Xid (PCI:0000:01:00): 1, Channel 00000002 Method 00000060 Data beef0233
Jul 15 11:11:59 Latitude-D820-Ubuntu kernel: NVRM: Xid (PCI:0000:01:00): 1, Channel 00000002 Method 00000060 Data beef0233
Jul 15 11:11:59 Latitude-D820-Ubuntu kernel: NVRM: Xid (PCI:0000:01:00): 9, Channel 00000002 Instance 00000000 Intr 00100000
Jul 15 11:11:59 Latitude-D820-Ubuntu kernel: NVRM: Xid (PCI:0000:01:00): 9, Channel 00000002 Instance 00000000 Intr 00100000
Jul 15 11:11:59 Latitude-D820-Ubuntu kernel: NVRM: Xid (PCI:0000:01:00): 9, Channel 00000002 Instance 00000000 Intr 00100000
Jul 15 11:11:59 Latitude-D820-Ubuntu kernel: NVRM: Xid (PCI:0000:01:00): 9, Channel 00000002 Instance 00000000 Intr 00100000
Jul 15 11:11:59 Latitude-D820-Ubuntu kernel: NVRM: Xid (PCI:0000:01:00): 9, Channel 00000002 Instance 00000000 Intr 00100000
Jul 15 11:11:59 Latitude-D820-Ubuntu kernel: NVRM: Xid (PCI:0000:01:00): 9, Channel 00000002 Instance 00000000 Intr 00100000
Jul 15 11:11:59 Latitude-D820-Ubuntu kernel: NVRM: Xid (PCI:0000:01:00): 9, Channel 00000002 Instance 00000000 Intr 00100000
Jul 15 11:11:59 Latitude-D820-Ubuntu kernel: NVRM: Xid (PCI:0000:01:00): 9, Channel 00000002 Instance 00000000 Intr 00100000
Jul 15 11:11:59 Latitude-D820-Ubuntu kernel: NVRM: Xid (PCI:0000:01:00): 9, Channel 00000002 Instance 00000000 Intr 00100000
Jul 15 11:11:59 Latitude-D820-Ubuntu kernel: NVRM: Xid (PCI:0000:01:00): 9, Channel 00000002 Instance 00000000 Intr 00100000
Jul 15 11:11:59 Latitude-D820-Ubuntu kernel: NVRM: Xid (PCI:0000:01:00): 9, Channel 00000002 Instance 00000000 Intr 00100000
Jul 15 11:12:08 Latitude-D820-Ubuntu gnome-session[1432]: (nm-applet:1614): nm-applet-WARNING **: Could not find ShellVersion property on org.gnome.Shell after 5 tries
Jul 15 11:12:20 Latitude-D820-Ubuntu kernel: NVRM: Xid (PCI:0000:01:00): 1, Channel 00000002 Method 00000060 Data beef0233
Jul 15 11:12:21 Latitude-D820-Ubuntu kernel: NVRM: Xid (PCI:0000:01:00): 1, Channel 00000002 Method 00000060 Data beef0233
Jul 15 11:12:23 Latitude-D820-Ubuntu kernel: NVRM: Xid (PCI:0000:01:00): 9, Channel 00000002 Instance 00000000 Intr 00100000
Jul 15 11:12:23 Latitude-D820-Ubuntu kernel: NVRM: Xid (PCI:0000:01:00): 9, Channel 00000002 Instance 00000000 Intr 00100000
Jul 15 11:12:23 Latitude-D820-Ubuntu kernel: NVRM: Xid (PCI:0000:01:00): 9, Channel 00000002 Instance 00000000 Intr 00100000
Jul 15 11:12:23 Latitude-D820-Ubuntu kernel: NVRM: Xid (PCI:0000:01:00): 9, Channel 00000002 Instance 00000000 Intr 00100000
Jul 15 11:12:23 Latitude-D820-Ubuntu kernel: NVRM: Xid (PCI:0000:01:00): 9, Channel 00000002 Instance 00000000 Intr 00100000
Jul 15 11:12:23 Latitude-D820-Ubuntu kernel: NVRM: Xid (PCI:0000:01:00): 9, Channel 00000002 Instance 00000000 Intr 00100000
Jul 15 11:12:23 Latitude-D820-Ubuntu kernel: NVRM: Xid (PCI:0000:01:00): 9, Channel 00000002 Instance 00000000 Intr 00100000
Jul 15 11:12:23 Latitude-D820-Ubuntu kernel: NVRM: Xid (PCI:0000:01:00): 9, Channel 00000002 Instance 00000000 Intr 00100000
Jul 15 11:12:23 Latitude-D820-Ubuntu kernel: NVRM: Xid (PCI:0000:01:00): 9, Channel 00000002 Instance 00000000 Intr 00100000
```
output of glxinfo:
```
name of display: :1
display: :1  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_create_context_robustness, GLX_ARB_fbconfig_float, 
    GLX_ARB_multisample, GLX_EXT_create_context_es2_profile, 
    GLX_EXT_create_context_es_profile, GLX_EXT_swap_control, 
    GLX_EXT_swap_control_tear, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_NV_float_buffer, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGI_swap_control, 
    GLX_SGI_video_sync
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_create_context_robustness, GLX_ARB_fbconfig_float, 
    GLX_ARB_get_proc_address, GLX_ARB_multisample, 
    GLX_EXT_create_context_es2_profile, GLX_EXT_fbconfig_packed_float, 
    GLX_EXT_framebuffer_sRGB, GLX_EXT_import_context, GLX_EXT_swap_control, 
    GLX_EXT_swap_control_tear, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_NV_copy_image, 
    GLX_NV_float_buffer, GLX_NV_multisample_coverage, GLX_NV_present_video, 
    GLX_NV_swap_group, GLX_NV_video_capture, GLX_NV_video_out, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGI_swap_control, 
    GLX_SGI_video_sync
GLX version: 1.4
GLX extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_create_context_robustness, GLX_ARB_fbconfig_float, 
    GLX_ARB_get_proc_address, GLX_ARB_multisample, 
    GLX_EXT_create_context_es2_profile, GLX_EXT_swap_control, 
    GLX_EXT_swap_control_tear, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_NV_float_buffer, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGI_swap_control, 
    GLX_SGI_video_sync
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce Go 7400/PCIe/SSE2
OpenGL version string: 2.1.2 NVIDIA 304.125
OpenGL shading language version string: 1.20 NVIDIA via Cg compiler
OpenGL extensions:
    GL_ARB_ES2_compatibility, GL_ARB_color_buffer_float, 
    GL_ARB_compressed_texture_pixel_storage, GL_ARB_conservative_depth, 
    GL_ARB_copy_buffer, GL_ARB_depth_clamp, GL_ARB_depth_texture, 
    GL_ARB_draw_buffers, GL_ARB_explicit_attrib_location, 
    GL_ARB_fragment_program, GL_ARB_fragment_program_shadow, 
    GL_ARB_fragment_shader, GL_ARB_framebuffer_object, 
    GL_ARB_get_program_binary, GL_ARB_half_float_pixel, 
    GL_ARB_half_float_vertex, GL_ARB_imaging, GL_ARB_internalformat_query, 
    GL_ARB_map_buffer_alignment, GL_ARB_map_buffer_range, GL_ARB_multisample, 
    GL_ARB_multitexture, GL_ARB_occlusion_query, GL_ARB_occlusion_query2, 
    GL_ARB_pixel_buffer_object, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_provoking_vertex, GL_ARB_robustness, GL_ARB_sampler_objects, 
    GL_ARB_separate_shader_objects, GL_ARB_shader_objects, 
    GL_ARB_shading_language_100, GL_ARB_shading_language_420pack, 
    GL_ARB_shading_language_include, GL_ARB_shadow, GL_ARB_sync, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_float, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_texture_rg, GL_ARB_texture_storage, 
    GL_ARB_texture_swizzle, GL_ARB_timer_query, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_array_bgra, GL_ARB_vertex_array_object, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_window_pos, GL_ATI_draw_buffers, GL_ATI_texture_float, 
    GL_ATI_texture_mirror_once, GL_EXT_Cg_shader, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_blend_color, GL_EXT_blend_equation_separate, 
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_compiled_vertex_array, GL_EXT_depth_bounds_test, 
    GL_EXT_direct_state_access, GL_EXT_draw_range_elements, GL_EXT_fog_coord, 
    GL_EXT_framebuffer_blit, GL_EXT_framebuffer_multisample, 
    GL_EXT_framebuffer_object, GL_EXT_gpu_program_parameters, 
    GL_EXT_import_sync_object, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels, 
    GL_EXT_pixel_buffer_object, GL_EXT_point_parameters, 
    GL_EXT_provoking_vertex, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_shader_objects, GL_EXT_separate_specular_color, 
    GL_EXT_shadow_funcs, GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, 
    GL_EXT_texture3D, GL_EXT_texture_compression_dxt1, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_format_BGRA8888, 
    GL_EXT_texture_lod, GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_sRGB, GL_EXT_texture_sRGB_decode, 
    GL_EXT_texture_storage, GL_EXT_texture_swizzle, GL_EXT_timer_query, 
    GL_EXT_vertex_array, GL_EXT_vertex_array_bgra, GL_EXT_x11_sync_object, 
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, 
    GL_KTX_buffer_region, GL_NVX_conditional_render, 
    GL_NV_ES1_1_compatibility, GL_NV_alpha_test, GL_NV_blend_minmax, 
    GL_NV_blend_square, GL_NV_complex_primitives, GL_NV_copy_depth_to_color, 
    GL_NV_depth_clamp, GL_NV_fbo_color_attachments, GL_NV_fence, 
    GL_NV_float_buffer, GL_NV_fog_distance, GL_NV_fragdepth, 
    GL_NV_fragment_program, GL_NV_fragment_program2, 
    GL_NV_fragment_program_option, GL_NV_framebuffer_multisample_coverage, 
    GL_NV_half_float, GL_NV_light_max_exponent, GL_NV_multisample_filter_hint, 
    GL_NV_occlusion_query, GL_NV_packed_depth_stencil, GL_NV_pixel_data_range, 
    GL_NV_point_sprite, GL_NV_primitive_restart, GL_NV_register_combiners, 
    GL_NV_register_combiners2, GL_NV_texgen_reflection, GL_NV_texture_barrier, 
    GL_NV_texture_compression_vtc, GL_NV_texture_env_combine4, 
    GL_NV_texture_expand_normal, GL_NV_texture_lod_clamp, 
    GL_NV_texture_rectangle, GL_NV_texture_shader, GL_NV_texture_shader2, 
    GL_NV_texture_shader3, GL_NV_vertex_array_range, 
    GL_NV_vertex_array_range2, GL_NV_vertex_program, GL_NV_vertex_program1_1, 
    GL_NV_vertex_program2, GL_NV_vertex_program2_option, 
    GL_NV_vertex_program3, GL_OES_compressed_paletted_texture, GL_OES_depth24, 
    GL_OES_depth32, GL_OES_depth_texture, GL_OES_element_index_uint, 
    GL_OES_fbo_render_mipmap, GL_OES_get_program_binary, GL_OES_mapbuffer, 
    GL_OES_packed_depth_stencil, GL_OES_point_size_array, GL_OES_point_sprite, 
    GL_OES_read_format, GL_OES_rgb8_rgba8, GL_OES_standard_derivatives, 
    GL_OES_texture_3D, GL_OES_texture_float, GL_OES_texture_float_linear, 
    GL_OES_texture_half_float, GL_OES_texture_half_float_linear, 
    GL_OES_texture_npot, GL_OES_vertex_array_object, GL_OES_vertex_half_float, 
    GL_S3_s3tc, GL_SGIS_generate_mipmap, GL_SGIS_texture_lod, 
    GL_SGIX_depth_texture, GL_SGIX_shadow, GL_SUN_slice_accum

OpenGL ES profile version string: OpenGL ES 2.0 NVIDIA 304.125 304.125
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 1.00
OpenGL ES profile extensions:
    GL_EXT_Cg_shader, GL_EXT_bgra, GL_EXT_framebuffer_object, 
    GL_EXT_texture_compression_dxt1, GL_EXT_texture_compression_s3tc, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_format_BGRA8888, 
    GL_EXT_unpack_subimage, GL_NV_alpha_test, GL_NV_blend_minmax, 
    GL_NV_complex_primitives, GL_NV_draw_buffers, GL_NV_fbo_color_attachments, 
    GL_NV_fragdepth, GL_NV_fragment_program, GL_NV_fragment_program2, 
    GL_NV_get_tex_image, GL_NV_read_buffer, GL_NV_texture_lod_clamp, 
    GL_NV_unpack_subimage, GL_NV_vertex_program, GL_NV_vertex_program1_1, 
    GL_NV_vertex_program2, GL_NV_vertex_program2_option, 
    GL_NV_vertex_program3, GL_OES_compressed_paletted_texture, GL_OES_depth24, 
    GL_OES_depth32, GL_OES_depth_texture, GL_OES_element_index_uint, 
    GL_OES_fbo_render_mipmap, GL_OES_get_program_binary, GL_OES_mapbuffer, 
    GL_OES_packed_depth_stencil, GL_OES_point_size_array, GL_OES_point_sprite, 
    GL_OES_read_format, GL_OES_rgb8_rgba8, GL_OES_standard_derivatives, 
    GL_OES_texture_3D, GL_OES_texture_float, GL_OES_texture_float_linear, 
    GL_OES_texture_half_float, GL_OES_texture_half_float_linear, 
    GL_OES_texture_npot, GL_OES_vertex_array_object, GL_OES_vertex_half_float

192 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x021 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  0 0 None
0x022 24 dc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  0 0 None
0x024 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  0 0 None
0x025 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  0 0 None
0x026 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  0 0 None
0x027 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x028 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  0 0 None
0x029 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x02a 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  0 0 None
0x02b 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 16  0 16 16 16 16  0 0 None
0x02c 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 16  0 16 16 16 16  0 0 None
0x02d 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 16  0 16 16 16 16  0 0 None
0x02e 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 16  0 16 16 16 16  0 0 None
0x02f 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4  0  0 16 16 16 16  0 0 None
0x030 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4  0  0 16 16 16 16  0 0 None
0x031 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4  0  0 16 16 16 16  0 0 None
0x032 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4  0  0 16 16 16 16  0 0 None
0x033 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x034 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x035 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x036 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x037 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x038 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x039 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x03a 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x03b 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x03c 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x03d 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x03e 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x03f 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x040 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x041 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x042 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x043 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 16  0 16 16 16 16  2 1 Ncon
0x044 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 16  0 16 16 16 16  2 1 Ncon
0x045 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 16  0 16 16 16 16  4 1 Ncon
0x046 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 16  0 16 16 16 16  4 1 Ncon
0x047 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 16  0 16 16 16 16  2 1 Ncon
0x048 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 16  0 16 16 16 16  2 1 Ncon
0x049 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 16  0 16 16 16 16  4 1 Ncon
0x04a 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 16  0 16 16 16 16  4 1 Ncon
0x04b 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 16  0 16 16 16 16  8 1 Ncon
0x04c 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 16  0 16 16 16 16  8 1 Ncon
0x04d 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 16  0 16 16 16 16 16 1 Ncon
0x04e 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 16  0 16 16 16 16 16 1 Ncon
0x04f 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 16  0 16 16 16 16  8 1 Ncon
0x050 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 16  0 16 16 16 16  8 1 Ncon
0x051 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 16  0 16 16 16 16 16 1 Ncon
0x052 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 16  0 16 16 16 16 16 1 Ncon
0x053 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  8 1 Ncon
0x054 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  8 1 Ncon
0x055 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16 16 1 Ncon
0x056 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16 16 1 Ncon
0x057 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  8 1 Ncon
0x058 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  8 1 Ncon
0x059 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16 16 1 Ncon
0x05a 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16 16 1 Ncon
0x05b 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  8 1 Ncon
0x05c 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  8 1 Ncon
0x05d 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16 16 1 Ncon
0x05e 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16 16 1 Ncon
0x05f 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  8 1 Ncon
0x060 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  8 1 Ncon
0x061 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16 16 1 Ncon
0x062 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16 16 1 Ncon
0x063 24 dc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  0 0 None
0x064 24 dc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  0 0 None
0x065 24 dc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  0 0 None
0x066 24 dc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x067 24 dc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  0 0 None
0x068 24 dc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x069 24 dc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  0 0 None
0x06a 24 dc  0  32  0 r  y .   8  8  8  0 .  .  4 16  0 16 16 16 16  0 0 None
0x06b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  4 16  0 16 16 16 16  0 0 None
0x06c 24 dc  0  32  0 r  . .   8  8  8  0 .  .  4 16  0 16 16 16 16  0 0 None
0x06d 24 dc  0  32  0 r  . .   8  8  8  8 .  .  4 16  0 16 16 16 16  0 0 None
0x06e 24 dc  0  32  0 r  y .   8  8  8  0 .  .  4  0  0 16 16 16 16  0 0 None
0x06f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  4  0  0 16 16 16 16  0 0 None
0x070 24 dc  0  32  0 r  . .   8  8  8  0 .  .  4  0  0 16 16 16 16  0 0 None
0x071 24 dc  0  32  0 r  . .   8  8  8  8 .  .  4  0  0 16 16 16 16  0 0 None
0x072 24 dc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x073 24 dc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x074 24 dc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x075 24 dc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x076 24 dc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x077 24 dc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x078 24 dc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x079 24 dc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x07a 24 dc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x07b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x07c 24 dc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x07d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x07e 24 dc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x07f 24 dc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x080 24 dc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x081 24 dc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x082 24 dc  0  32  0 r  y .   8  8  8  0 .  .  4 16  0 16 16 16 16  2 1 Ncon
0x083 24 dc  0  32  0 r  y .   8  8  8  8 .  .  4 16  0 16 16 16 16  2 1 Ncon
0x084 24 dc  0  32  0 r  y .   8  8  8  0 .  .  4 16  0 16 16 16 16  4 1 Ncon
0x085 24 dc  0  32  0 r  y .   8  8  8  8 .  .  4 16  0 16 16 16 16  4 1 Ncon
0x086 24 dc  0  32  0 r  . .   8  8  8  0 .  .  4 16  0 16 16 16 16  2 1 Ncon
0x087 24 dc  0  32  0 r  . .   8  8  8  8 .  .  4 16  0 16 16 16 16  2 1 Ncon
0x088 24 dc  0  32  0 r  . .   8  8  8  0 .  .  4 16  0 16 16 16 16  4 1 Ncon
0x089 24 dc  0  32  0 r  . .   8  8  8  8 .  .  4 16  0 16 16 16 16  4 1 Ncon
0x08a 24 dc  0  32  0 r  y .   8  8  8  0 .  .  4 16  0 16 16 16 16  8 1 Ncon
0x08b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  4 16  0 16 16 16 16  8 1 Ncon
0x08c 24 dc  0  32  0 r  y .   8  8  8  0 .  .  4 16  0 16 16 16 16 16 1 Ncon
0x08d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  4 16  0 16 16 16 16 16 1 Ncon
0x08e 24 dc  0  32  0 r  . .   8  8  8  0 .  .  4 16  0 16 16 16 16  8 1 Ncon
0x08f 24 dc  0  32  0 r  . .   8  8  8  8 .  .  4 16  0 16 16 16 16  8 1 Ncon
0x090 24 dc  0  32  0 r  . .   8  8  8  0 .  .  4 16  0 16 16 16 16 16 1 Ncon
0x091 24 dc  0  32  0 r  . .   8  8  8  8 .  .  4 16  0 16 16 16 16 16 1 Ncon
0x092 24 dc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  8 1 Ncon
0x093 24 dc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  8 1 Ncon
0x094 24 dc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16 16 1 Ncon
0x095 24 dc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16 16 1 Ncon
0x096 24 dc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  8 1 Ncon
0x097 24 dc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  8 1 Ncon
0x098 24 dc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16 16 1 Ncon
0x099 24 dc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16 16 1 Ncon
0x09a 24 dc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  8 1 Ncon
0x09b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  8 1 Ncon
0x09c 24 dc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16 16 1 Ncon
0x09d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16 16 1 Ncon
0x09e 24 dc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  8 1 Ncon
0x09f 24 dc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  8 1 Ncon
0x0a0 24 dc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16 16 1 Ncon
0x0a1 24 dc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16 16 1 Ncon
0x023 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  0 0 None
0x0a2 32 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  0 0 None
0x0a3 32 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  0 0 None
0x0a4 32 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  0 0 None
0x0a5 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x0a6 32 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  0 0 None
0x0a7 32 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x0a8 32 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  0 0 None
0x0a9 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4 16  0 16 16 16 16  0 0 None
0x0aa 32 tc  0  32  0 r  y .   8  8  8  8 .  .  4 16  0 16 16 16 16  0 0 None
0x0ab 32 tc  0  32  0 r  . .   8  8  8  0 .  .  4 16  0 16 16 16 16  0 0 None
0x0ac 32 tc  0  32  0 r  . .   8  8  8  8 .  .  4 16  0 16 16 16 16  0 0 None
0x0ad 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4  0  0 16 16 16 16  0 0 None
0x0ae 32 tc  0  32  0 r  y .   8  8  8  8 .  .  4  0  0 16 16 16 16  0 0 None
0x0af 32 tc  0  32  0 r  . .   8  8  8  0 .  .  4  0  0 16 16 16 16  0 0 None
0x0b0 32 tc  0  32  0 r  . .   8  8  8  8 .  .  4  0  0 16 16 16 16  0 0 None
0x0b1 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x0b2 32 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x0b3 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x0b4 32 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x0b5 32 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x0b6 32 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x0b7 32 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x0b8 32 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x0b9 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x0ba 32 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x0bb 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x0bc 32 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x0bd 32 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x0be 32 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x0bf 32 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x0c0 32 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x0c1 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4 16  0 16 16 16 16  2 1 Ncon
0x0c2 32 tc  0  32  0 r  y .   8  8  8  8 .  .  4 16  0 16 16 16 16  2 1 Ncon
0x0c3 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4 16  0 16 16 16 16  4 1 Ncon
0x0c4 32 tc  0  32  0 r  y .   8  8  8  8 .  .  4 16  0 16 16 16 16  4 1 Ncon
0x0c5 32 tc  0  32  0 r  . .   8  8  8  0 .  .  4 16  0 16 16 16 16  2 1 Ncon
0x0c6 32 tc  0  32  0 r  . .   8  8  8  8 .  .  4 16  0 16 16 16 16  2 1 Ncon
0x0c7 32 tc  0  32  0 r  . .   8  8  8  0 .  .  4 16  0 16 16 16 16  4 1 Ncon
0x0c8 32 tc  0  32  0 r  . .   8  8  8  8 .  .  4 16  0 16 16 16 16  4 1 Ncon
0x0c9 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4 16  0 16 16 16 16  8 1 Ncon
0x0ca 32 tc  0  32  0 r  y .   8  8  8  8 .  .  4 16  0 16 16 16 16  8 1 Ncon
0x0cb 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4 16  0 16 16 16 16 16 1 Ncon
0x0cc 32 tc  0  32  0 r  y .   8  8  8  8 .  .  4 16  0 16 16 16 16 16 1 Ncon
0x0cd 32 tc  0  32  0 r  . .   8  8  8  0 .  .  4 16  0 16 16 16 16  8 1 Ncon
0x0ce 32 tc  0  32  0 r  . .   8  8  8  8 .  .  4 16  0 16 16 16 16  8 1 Ncon
0x0cf 32 tc  0  32  0 r  . .   8  8  8  0 .  .  4 16  0 16 16 16 16 16 1 Ncon
0x0d0 32 tc  0  32  0 r  . .   8  8  8  8 .  .  4 16  0 16 16 16 16 16 1 Ncon
0x0d1 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  8 1 Ncon
0x0d2 32 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  8 1 Ncon
0x0d3 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16 16 1 Ncon
0x0d4 32 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16 16 1 Ncon
0x0d5 32 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  8 1 Ncon
0x0d6 32 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  8 1 Ncon
0x0d7 32 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16 16 1 Ncon
0x0d8 32 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16 16 1 Ncon
0x0d9 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  8 1 Ncon
0x0da 32 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  8 1 Ncon
0x0db 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16 16 1 Ncon
0x0dc 32 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16 16 1 Ncon
0x0dd 32 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  8 1 Ncon
0x0de 32 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  8 1 Ncon
0x0df 32 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16 16 1 Ncon
0x0e0 32 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16 16 1 Ncon

251 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x0e1 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  0 0 None
0x0e2 24 dc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  0 0 None
0x0e3 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  0 0 None
0x0e4 24 dc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  0 0 None
0x0e5 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  0 0 None
0x0e6 24 dc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  0 0 None
0x0e7 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  0 0 None
0x0e8 24 dc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  0 0 None
0x0e9 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x0ea 24 dc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x0eb 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  0 0 None
0x0ec 24 dc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  0 0 None
0x0ed 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x0ee 24 dc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x0ef 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  0 0 None
0x0f0 24 dc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  0 0 None
0x0f1 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 16  0 16 16 16 16  0 0 None
0x0f2 24 dc  0  32  0 r  y .   8  8  8  0 .  .  4 16  0 16 16 16 16  0 0 None
0x0f3 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 16  0 16 16 16 16  0 0 None
0x0f4 24 dc  0  32  0 r  y .   8  8  8  8 .  .  4 16  0 16 16 16 16  0 0 None
0x0f5 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 16  0 16 16 16 16  0 0 None
0x0f6 24 dc  0  32  0 r  . .   8  8  8  0 .  .  4 16  0 16 16 16 16  0 0 None
0x0f7 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 16  0 16 16 16 16  0 0 None
0x0f8 24 dc  0  32  0 r  . .   8  8  8  8 .  .  4 16  0 16 16 16 16  0 0 None
0x0f9 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4  0  0 16 16 16 16  0 0 None
0x0fa 24 dc  0  32  0 r  y .   8  8  8  0 .  .  4  0  0 16 16 16 16  0 0 None
0x0fb 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4  0  0 16 16 16 16  0 0 None
0x0fc 24 dc  0  32  0 r  y .   8  8  8  8 .  .  4  0  0 16 16 16 16  0 0 None
0x0fd 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4  0  0 16 16 16 16  0 0 None
0x0fe 24 dc  0  32  0 r  . .   8  8  8  0 .  .  4  0  0 16 16 16 16  0 0 None
0x0ff 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4  0  0 16 16 16 16  0 0 None
0x100 24 dc  0  32  0 r  . .   8  8  8  8 .  .  4  0  0 16 16 16 16  0 0 None
0x101 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x102 24 dc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x103 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x104 24 dc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x105 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x106 24 dc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x107 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x108 24 dc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x109 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x10a 24 dc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x10b 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x10c 24 dc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x10d 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x10e 24 dc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x10f 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x110 24 dc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x111 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x112 24 dc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x113 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x114 24 dc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x115 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x116 24 dc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x117 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x118 24 dc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x119 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x11a 24 dc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x11b 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x11c 24 dc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x11d 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x11e 24 dc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x11f 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x120 24 dc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x121 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 16  0 16 16 16 16  2 1 Ncon
0x122 24 dc  0  32  0 r  y .   8  8  8  0 .  .  4 16  0 16 16 16 16  2 1 Ncon
0x123 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 16  0 16 16 16 16  2 1 Ncon
0x124 24 dc  0  32  0 r  y .   8  8  8  8 .  .  4 16  0 16 16 16 16  2 1 Ncon
0x125 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 16  0 16 16 16 16  4 1 Ncon
0x126 24 dc  0  32  0 r  y .   8  8  8  0 .  .  4 16  0 16 16 16 16  4 1 Ncon
0x127 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 16  0 16 16 16 16  4 1 Ncon
0x128 24 dc  0  32  0 r  y .   8  8  8  8 .  .  4 16  0 16 16 16 16  4 1 Ncon
0x129 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 16  0 16 16 16 16  2 1 Ncon
0x12a 24 dc  0  32  0 r  . .   8  8  8  0 .  .  4 16  0 16 16 16 16  2 1 Ncon
0x12b 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 16  0 16 16 16 16  2 1 Ncon
0x12c 24 dc  0  32  0 r  . .   8  8  8  8 .  .  4 16  0 16 16 16 16  2 1 Ncon
0x12d 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 16  0 16 16 16 16  4 1 Ncon
0x12e 24 dc  0  32  0 r  . .   8  8  8  0 .  .  4 16  0 16 16 16 16  4 1 Ncon
0x12f 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 16  0 16 16 16 16  4 1 Ncon
0x130 24 dc  0  32  0 r  . .   8  8  8  8 .  .  4 16  0 16 16 16 16  4 1 Ncon
0x131 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 16  0 16 16 16 16  8 1 Ncon
0x132 24 dc  0  32  0 r  y .   8  8  8  0 .  .  4 16  0 16 16 16 16  8 1 Ncon
0x133 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 16  0 16 16 16 16  8 1 Ncon
0x134 24 dc  0  32  0 r  y .   8  8  8  8 .  .  4 16  0 16 16 16 16  8 1 Ncon
0x135 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 16  0 16 16 16 16 16 1 Ncon
0x136 24 dc  0  32  0 r  y .   8  8  8  0 .  .  4 16  0 16 16 16 16 16 1 Ncon
0x137 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 16  0 16 16 16 16 16 1 Ncon
0x138 24 dc  0  32  0 r  y .   8  8  8  8 .  .  4 16  0 16 16 16 16 16 1 Ncon
0x139 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 16  0 16 16 16 16  8 1 Ncon
0x13a 24 dc  0  32  0 r  . .   8  8  8  0 .  .  4 16  0 16 16 16 16  8 1 Ncon
0x13b 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 16  0 16 16 16 16  8 1 Ncon
0x13c 24 dc  0  32  0 r  . .   8  8  8  8 .  .  4 16  0 16 16 16 16  8 1 Ncon
0x13d 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 16  0 16 16 16 16 16 1 Ncon
0x13e 24 dc  0  32  0 r  . .   8  8  8  0 .  .  4 16  0 16 16 16 16 16 1 Ncon
0x13f 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 16  0 16 16 16 16 16 1 Ncon
0x140 24 dc  0  32  0 r  . .   8  8  8  8 .  .  4 16  0 16 16 16 16 16 1 Ncon
0x141 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  8 1 Ncon
0x142 24 dc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  8 1 Ncon
0x143 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  8 1 Ncon
0x144 24 dc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  8 1 Ncon
0x145 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16 16 1 Ncon
0x146 24 dc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16 16 1 Ncon
0x147 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16 16 1 Ncon
0x148 24 dc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16 16 1 Ncon
0x149 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  8 1 Ncon
0x14a 24 dc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  8 1 Ncon
0x14b 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  8 1 Ncon
0x14c 24 dc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  8 1 Ncon
0x14d 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16 16 1 Ncon
0x14e 24 dc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16 16 1 Ncon
0x14f 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16 16 1 Ncon
0x150 24 dc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16 16 1 Ncon
0x151 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  8 1 Ncon
0x152 24 dc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  8 1 Ncon
0x153 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  8 1 Ncon
0x154 24 dc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  8 1 Ncon
0x155 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16 16 1 Ncon
0x156 24 dc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16 16 1 Ncon
0x157 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16 16 1 Ncon
0x158 24 dc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16 16 1 Ncon
0x159 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  8 1 Ncon
0x15a 24 dc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  8 1 Ncon
0x15b 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  8 1 Ncon
0x15c 24 dc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  8 1 Ncon
0x15d 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16 16 1 Ncon
0x15e 24 dc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16 16 1 Ncon
0x15f 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16 16 1 Ncon
0x160 24 dc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16 16 1 Ncon
0x161 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  0 0 None
0x162 32 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  0 0 None
0x163 32 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  0 0 None
0x164 32 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  0 0 None
0x165 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x166 32 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  0 0 None
0x167 32 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x168 32 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  0 0 None
0x169 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4 16  0 16 16 16 16  0 0 None
0x16a 32 tc  0  32  0 r  y .   8  8  8  8 .  .  4 16  0 16 16 16 16  0 0 None
0x16b 32 tc  0  32  0 r  . .   8  8  8  0 .  .  4 16  0 16 16 16 16  0 0 None
0x16c 32 tc  0  32  0 r  . .   8  8  8  8 .  .  4 16  0 16 16 16 16  0 0 None
0x16d 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4  0  0 16 16 16 16  0 0 None
0x16e 32 tc  0  32  0 r  y .   8  8  8  8 .  .  4  0  0 16 16 16 16  0 0 None
0x16f 32 tc  0  32  0 r  . .   8  8  8  0 .  .  4  0  0 16 16 16 16  0 0 None
0x170 32 tc  0  32  0 r  . .   8  8  8  8 .  .  4  0  0 16 16 16 16  0 0 None
0x171 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x172 32 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x173 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x174 32 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x175 32 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x176 32 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x177 32 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x178 32 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x179 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x17a 32 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x17b 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x17c 32 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x17d 32 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x17e 32 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x17f 32 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x180 32 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x181 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4 16  0 16 16 16 16  2 1 Ncon
0x182 32 tc  0  32  0 r  y .   8  8  8  8 .  .  4 16  0 16 16 16 16  2 1 Ncon
0x183 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4 16  0 16 16 16 16  4 1 Ncon
0x184 32 tc  0  32  0 r  y .   8  8  8  8 .  .  4 16  0 16 16 16 16  4 1 Ncon
0x185 32 tc  0  32  0 r  . .   8  8  8  0 .  .  4 16  0 16 16 16 16  2 1 Ncon
0x186 32 tc  0  32  0 r  . .   8  8  8  8 .  .  4 16  0 16 16 16 16  2 1 Ncon
0x187 32 tc  0  32  0 r  . .   8  8  8  0 .  .  4 16  0 16 16 16 16  4 1 Ncon
0x188 32 tc  0  32  0 r  . .   8  8  8  8 .  .  4 16  0 16 16 16 16  4 1 Ncon
0x189 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4 16  0 16 16 16 16  8 1 Ncon
0x18a 32 tc  0  32  0 r  y .   8  8  8  8 .  .  4 16  0 16 16 16 16  8 1 Ncon
0x18b 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4 16  0 16 16 16 16 16 1 Ncon
0x18c 32 tc  0  32  0 r  y .   8  8  8  8 .  .  4 16  0 16 16 16 16 16 1 Ncon
0x18d 32 tc  0  32  0 r  . .   8  8  8  0 .  .  4 16  0 16 16 16 16  8 1 Ncon
0x18e 32 tc  0  32  0 r  . .   8  8  8  8 .  .  4 16  0 16 16 16 16  8 1 Ncon
0x18f 32 tc  0  32  0 r  . .   8  8  8  0 .  .  4 16  0 16 16 16 16 16 1 Ncon
0x190 32 tc  0  32  0 r  . .   8  8  8  8 .  .  4 16  0 16 16 16 16 16 1 Ncon
0x191 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  8 1 Ncon
0x192 32 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  8 1 Ncon
0x193 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16 16 1 Ncon
0x194 32 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16 16 1 Ncon
0x195 32 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  8 1 Ncon
0x196 32 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  8 1 Ncon
0x197 32 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16 16 1 Ncon
0x198 32 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16 16 1 Ncon
0x199 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  8 1 Ncon
0x19a 32 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  8 1 Ncon
0x19b 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16 16 1 Ncon
0x19c 32 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16 16 1 Ncon
0x19d 32 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  8 1 Ncon
0x19e 32 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  8 1 Ncon
0x19f 32 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16 16 1 Ncon
0x1a0 32 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16 16 1 Ncon
0x1a1  0 sg  0  16  0 r  y .   5  6  5  0 .  .  4 16  0 16 16 16 16  0 0 None
0x1a2  0 sg  0  16  0 r  . .   5  6  5  0 .  .  4 16  0 16 16 16 16  0 0 None
0x1a3  0 sg  0  16  0 r  y .   5  6  5  0 .  .  4 24  0 16 16 16 16  0 0 None
0x1a4  0 sg  0  16  0 r  . .   5  6  5  0 .  .  4 24  0 16 16 16 16  0 0 None
0x1a5  0 sg  0  16  0 r  y .   5  6  5  0 .  .  4 24  8 16 16 16 16  0 0 None
0x1a6  0 sg  0  16  0 r  . .   5  6  5  0 .  .  4 24  8 16 16 16 16  0 0 None
0x1a7  0 sg  0  16  0 r  y .   5  6  5  0 .  .  4  0  0 16 16 16 16  0 0 None
0x1a8  0 sg  0  16  0 r  . .   5  6  5  0 .  .  4  0  0 16 16 16 16  0 0 None
0x1a9  0 sg  0   0  0 r  . .   0  0  0  0 .  .  4 16  0 16 16 16 16  0 0 None
0x1aa  0 sg  0   0  0 r  . .   0  0  0  0 .  .  4 24  0 16 16 16 16  0 0 None
0x1ab  0 sg  0   0  0 r  . .   0  0  0  0 .  .  4 24  8 16 16 16 16  0 0 None
0x1ac  0 sg  0  32  0 r  . .  16 16  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x1ad  0 sg  0  32  0    . .  16 16  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x1ae  0 sg  0  32  0 r  y .  16 16  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x1af  0 sg  0  32  0    y .  16 16  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x1b0  0 sg  0  32  0 r  . .  32  0  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x1b1  0 sg  0  32  0    . .  32  0  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x1b2  0 sg  0  32  0 r  y .  32  0  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x1b3  0 sg  0  32  0    y .  32  0  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x1b4  0 sg  0  64  0 r  . .  16 16 16 16 f  .  4  0  0 16 16 16 16  0 0 None
0x1b5  0 sg  0  64  0    . .  16 16 16 16 f  .  4  0  0 16 16 16 16  0 0 None
0x1b6  0 sg  0  64  0 r  y .  16 16 16 16 f  .  4  0  0 16 16 16 16  0 0 None
0x1b7  0 sg  0  64  0    y .  16 16 16 16 f  .  4  0  0 16 16 16 16  0 0 None
0x1b8  0 sg  0 128  0 r  . .  32 32 32 32 f  .  4  0  0 16 16 16 16  0 0 None
0x1b9  0 sg  0 128  0    . .  32 32 32 32 f  .  4  0  0 16 16 16 16  0 0 None
0x1ba  0 sg  0 128  0 r  y .  32 32 32 32 f  .  4  0  0 16 16 16 16  0 0 None
0x1bb  0 sg  0 128  0    y .  32 32 32 32 f  .  4  0  0 16 16 16 16  0 0 None
0x1bc  0 sg  0  32  0 r  . .  16 16  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x1bd  0 sg  0  32  0    . .  16 16  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x1be  0 sg  0  32  0 r  y .  16 16  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x1bf  0 sg  0  32  0    y .  16 16  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x1c0  0 sg  0  32  0 r  . .  16 16  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x1c1  0 sg  0  32  0    . .  16 16  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x1c2  0 sg  0  32  0 r  y .  16 16  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x1c3  0 sg  0  32  0    y .  16 16  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x1c4  0 sg  0  32  0 r  . .  32  0  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x1c5  0 sg  0  32  0    . .  32  0  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x1c6  0 sg  0  32  0 r  y .  32  0  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x1c7  0 sg  0  32  0    y .  32  0  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x1c8  0 sg  0  32  0 r  . .  32  0  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x1c9  0 sg  0  32  0    . .  32  0  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x1ca  0 sg  0  32  0 r  y .  32  0  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x1cb  0 sg  0  32  0    y .  32  0  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x1cc  0 sg  0  64  0 r  . .  16 16 16 16 f  .  4 24  0 16 16 16 16  0 0 None
0x1cd  0 sg  0  64  0    . .  16 16 16 16 f  .  4 24  0 16 16 16 16  0 0 None
0x1ce  0 sg  0  64  0 r  y .  16 16 16 16 f  .  4 24  0 16 16 16 16  0 0 None
0x1cf  0 sg  0  64  0    y .  16 16 16 16 f  .  4 24  0 16 16 16 16  0 0 None
0x1d0  0 sg  0  64  0 r  . .  16 16 16 16 f  .  4 24  8 16 16 16 16  0 0 None
0x1d1  0 sg  0  64  0    . .  16 16 16 16 f  .  4 24  8 16 16 16 16  0 0 None
0x1d2  0 sg  0  64  0 r  y .  16 16 16 16 f  .  4 24  8 16 16 16 16  0 0 None
0x1d3  0 sg  0  64  0    y .  16 16 16 16 f  .  4 24  8 16 16 16 16  0 0 None
0x1d4  0 sg  0 128  0 r  . .  32 32 32 32 f  .  4 24  0 16 16 16 16  0 0 None
0x1d5  0 sg  0 128  0    . .  32 32 32 32 f  .  4 24  0 16 16 16 16  0 0 None
0x1d6  0 sg  0 128  0 r  y .  32 32 32 32 f  .  4 24  0 16 16 16 16  0 0 None
0x1d7  0 sg  0 128  0    y .  32 32 32 32 f  .  4 24  0 16 16 16 16  0 0 None
0x1d8  0 sg  0 128  0 r  . .  32 32 32 32 f  .  4 24  8 16 16 16 16  0 0 None
0x1d9  0 sg  0 128  0    . .  32 32 32 32 f  .  4 24  8 16 16 16 16  0 0 None
0x1da  0 sg  0 128  0 r  y .  32 32 32 32 f  .  4 24  8 16 16 16 16  0 0 None
0x1db  0 sg  0 128  0    y .  32 32 32 32 f  .  4 24  8 16 16 16 16  0 0 None

```
i do also have the nvidia-304 driver installed
output of lshw:
```
computer
    description: Computer
    width: 32 bits
    capabilities: smbios-2.4
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 3278MiB
     *-cpu
          product: Genuine Intel(R) CPU           T2500  @ 2.00GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.14.8
          serial: [REMOVED]
          size: 1GHz
          capacity: 2GHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon bts aperfmperf pni monitor vmx est tm2 xtpr pdcm dtherm cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 32 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 memory:ed000000-efefffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: G72M [GeForce Go 7400]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:ed000000-edffffff memory:d0000000-dfffffff memory:ee000000-eeffffff memory:ef000000-ef01ffff
        *-multimedia
             description: Audio device
             product: NM10/ICH7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:29 memory:efffc000-efffffff
        *-pci:1
             description: PCI bridge
             product: NM10/ICH7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:2000(size=4096) memory:e0200000-e03fffff ioport:e0400000(size=2097152)
        *-pci:2
             description: PCI bridge
             product: NM10/ICH7 Family PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:3000(size=4096) memory:ecf00000-ecffffff ioport:e0600000(size=2097152)
           *-network
                description: Wireless interface
                product: PRO/Wireless 3945ABG [Golan] Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:0c:00.0
                logical name: wlan0
                version: 02
                serial: [REMOVED]
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwl3945 driverversion=3.19.0-22-generic firmware=15.32.2.9 ip=[REMOVED] latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
                resources: irq:30 memory:ecfff000-ecffffff
        *-pci:3
             description: PCI bridge
             product: NM10/ICH7 Family PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:27 ioport:4000(size=4096) memory:ece00000-ecefffff ioport:e0800000(size=2097152)
           *-network
                description: Ethernet interface
                product: NetXtreme BCM5752 Gigabit Ethernet PCI Express
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:09:00.0
                logical name: eth0
                version: 02
                serial: [REMOVED]
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.137 firmware=5752-v3.19 latency=0 link=no multicast=yes port=twisted pair
                resources: irq:31 memory:ecef0000-ecefffff
        *-pci:4
             description: PCI bridge
             product: NM10/ICH7 Family PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:28 ioport:e000(size=4096) memory:ecc00000-ecdfffff ioport:e0000000(size=2097152)
        *-usb:0
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:20 ioport:bf80(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 3.19.0-22-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 3.19
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:1
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:bf60(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 3.19.0-22-generic uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 3.19
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
              *-usb:0
                   description: USB hub
                   product: Oz776 1.1 Hub
                   vendor: O2 Micro, Inc.
                   physical id: 1
                   bus info: usb@3:1
                   version: 1.10
                   capabilities: usb-1.10
                   configuration: driver=hub maxpower=200mA slots=3 speed=12Mbit/s
                 *-usb UNCLAIMED
                      description: Smart card reader
                      product: O2Micro CCID SC Reader
                      vendor: O2
                      physical id: 2
                      bus info: usb@3:1.2
                      version: 1.10
                      capabilities: usb-1.10
                      configuration: speed=12Mbit/s
              *-usb:1
                   description: Keyboard
                   product: USB Receiver
                   vendor: Logitech
                   physical id: 2
                   bus info: usb@3:2
                   version: 12.03
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=98mA speed=12Mbit/s
        *-usb:2
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:22 ioport:bf40(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 3.19.0-22-generic uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 3.19
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:3
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:bf20(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 3.19.0-22-generic uhci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 3.19
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:4
             description: USB controller
             product: NM10/ICH7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:20 memory:ffa80000-ffa803ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 3.19.0-22-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 3.19
                capabilities: usb-2.00
                configuration: driver=hub slots=8 speed=480Mbit/s
              *-usb:0
                   description: USB hub
                   product: Internal 2.0 Hub
                   vendor: Dell Computer Corp.
                   physical id: 2
                   bus info: usb@1:2
                   version: 50.18
                   capabilities: usb-2.00
                   configuration: driver=hub maxpower=2mA slots=4 speed=480Mbit/s
                 *-usb
                      description: Bluetooth wireless interface
                      product: Wireless 350 Bluetooth
                      vendor: Dell Computer Corp.
                      physical id: 3
                      bus info: usb@1:2.3
                      version: 24.22
                      capabilities: bluetooth usb-2.00
                      configuration: driver=btusb speed=12Mbit/s
              *-usb:1
                   description: Mass storage device
                   product: USB
                   vendor: Seagate
                   physical id: 6
                   bus info: usb@1:6
                   logical name: scsi2
                   version: 4.19
                   serial: [REMOVED]
                   capabilities: usb-2.10 scsi emulated scsi-host
                   configuration: driver=usb-storage maxpower=100mA speed=480Mbit/s
                 *-disk
                      description: SCSI Disk
                      product: USB
                      vendor: Seagate
                      physical id: 0.0.0
                      bus info: scsi@2:0.0.0
                      logical name: /dev/sdb
                      version: 0419
                      serial: [REMOVED]
                      size: 55GiB (60GB)
                      capabilities: partitioned partitioned:dos
                      configuration: ansiversion=6 logicalsectorsize=512 sectorsize=512 signature=009cd21e
                    *-volume
                         description: Windows FAT volume
                         vendor: SYSLINUX
                         physical id: 1
                         bus info: scsi@2:0.0.0,1
                         logical name: /dev/sdb1
                         logical name: /media/jordyn/UBUNTU 15_0
                         version: FAT32
                         serial: [REMOVED]
                         size: 55GiB
                         capacity: 55GiB
                         capabilities: primary bootable fat initialized
                         configuration: FATs=2 filesystem=fat label=UBUNTU 15_0 mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro state=mounted
        *-pci:5
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:5000(size=4096) memory:ecb00000-ecbfffff
           *-pcmcia
                description: CardBus bridge
                product: Cardbus bridge
                vendor: O2 Micro, Inc.
                physical id: 1
                bus info: pci@0000:03:01.0
                version: 21
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:19 memory:e4000000-e4000fff ioport:5000(size=256) ioport:5400(size=256) memory:e8000000-ebffffff memory:f8000000-fbffffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: Firewire (IEEE 1394)
                vendor: O2 Micro, Inc.
                physical id: 1.4
                bus info: pci@0000:03:01.4
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=64
                resources: irq:19 memory:ecbff000-ecbfffff memory:ecbfe800-ecbfefff
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:17 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:bfa0(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: NM10/ICH7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:10c0(size=32)
     *-scsi
          physical id: 2
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST500LM012 HN-M5
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 0001
             serial: [REMOVED]
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=4096 signature=dd514883
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: [REMOVED]
                size: 462GiB
                capacity: 462GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2015-07-15 10:34:10 filesystem=ext4 lastmountpoint=/ modified=2015-07-15 10:50:16 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2015-07-15 10:50:16 state=mounted
           *-volume:1
                description: Linux swap volume
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                version: 1
                serial: [REMOVED]
                size: 3836MiB
                capacity: 3836MiB
                capabilities: primary nofs swap initialized
                configuration: filesystem=swap pagesize=4096
```

---

### Post by dino99 on 2015-07-16
if your graphic can support a newer graphic driver, then drop the 304 one which has a lot issue (342 is way better); but which ubuntu have you installed ?

---

