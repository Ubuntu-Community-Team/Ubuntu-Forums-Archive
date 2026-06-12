---
title: "Intel Pentium Graphics Issue - CPU G850 @2.90 GHz"
date: 2012-11-30
forum: Hardware
---

### Post by feathre on 2012-11-30
I think there is an issue with my graphics driver for my Intel Pentium G850.  It runs using Mesa 9.0 Sandybridge desktop, according to system information.  It does have 3d rendering but it is VERY SLOW.  I get maybe 3 to 5 frames per second if I'm lucky, even on lower end games.  I did a bit of research but wasn't able to find the answer, so hopefully someone here can help.  Also, I am using Linux Mint. Here is what shows when I type "glxinfo" in terminal:

```
name of display: :0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_multisample, GLX_EXT_create_context_es2_profile, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, GLX_OML_swap_method, 
    GLX_SGI_swap_control, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, GLX_INTEL_swap_event
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_create_context_robustness, GLX_ARB_get_proc_address, 
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_framebuffer_sRGB, 
    GLX_EXT_create_context_es2_profile, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_swap_control, 
    GLX_OML_swap_method, GLX_OML_sync_control, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap, GLX_INTEL_swap_event
GLX version: 1.4
GLX extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_create_context_es2_profile, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_swap_control, 
    GLX_OML_swap_method, GLX_OML_sync_control, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap
OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Desktop 
OpenGL version string: 3.0 Mesa 9.0
OpenGL shading language version string: 1.30
OpenGL extensions:
    GL_ARB_multisample, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_copy_texture, 
    GL_EXT_polygon_offset, GL_EXT_subtexture, GL_EXT_texture_object, 
    GL_EXT_vertex_array, GL_EXT_compiled_vertex_array, GL_EXT_texture, 
    GL_EXT_texture3D, GL_IBM_rasterpos_clip, GL_ARB_point_parameters, 
    GL_EXT_draw_range_elements, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
    GL_EXT_rescale_normal, GL_EXT_separate_specular_color, 
    GL_EXT_texture_edge_clamp, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod, GL_ARB_framebuffer_sRGB, GL_ARB_multitexture, 
    GL_EXT_framebuffer_sRGB, GL_IBM_multimode_draw_arrays, 
    GL_IBM_texture_mirrored_repeat, GL_3DFX_texture_compression_FXT1, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, GL_ARB_transpose_matrix, 
    GL_EXT_blend_func_separate, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, 
    GL_EXT_secondary_color, GL_EXT_texture_env_add, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_INGR_blend_func_separate, GL_NV_blend_square, GL_NV_light_max_exponent, 
    GL_NV_texgen_reflection, GL_NV_texture_env_combine4, GL_S3_s3tc, 
    GL_SUN_multi_draw_arrays, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_EXT_framebuffer_object, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_MESA_window_pos, GL_NV_packed_depth_stencil, 
    GL_NV_texture_rectangle, GL_NV_vertex_program, GL_ARB_depth_texture, 
    GL_ARB_occlusion_query, GL_ARB_shadow, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_window_pos, GL_ATI_envmap_bumpmap, 
    GL_EXT_stencil_two_side, GL_EXT_texture_cube_map, GL_NV_depth_clamp, 
    GL_NV_vertex_program1_1, GL_APPLE_packed_pixels, 
    GL_APPLE_vertex_array_object, GL_ARB_draw_buffers, 
    GL_ARB_fragment_program, GL_ARB_fragment_shader, GL_ARB_shader_objects, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ATI_draw_buffers, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_float, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_wrap, GL_MESA_pack_invert, GL_MESA_ycbcr_texture, 
    GL_NV_primitive_restart, GL_ARB_depth_clamp, 
    GL_ARB_fragment_program_shadow, GL_ARB_half_float_pixel, 
    GL_ARB_occlusion_query2, GL_ARB_point_sprite, GL_ARB_shading_language_100, 
    GL_ARB_sync, GL_ARB_texture_non_power_of_two, GL_ARB_vertex_buffer_object, 
    GL_ATI_blend_equation_separate, GL_EXT_blend_equation_separate, 
    GL_OES_read_format, GL_ARB_color_buffer_float, GL_ARB_pixel_buffer_object, 
    GL_ARB_texture_compression_rgtc, GL_ARB_texture_float, 
    GL_ARB_texture_rectangle, GL_EXT_packed_float, GL_EXT_pixel_buffer_object, 
    GL_EXT_texture_compression_dxt1, GL_EXT_texture_compression_rgtc, 
    GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, 
    GL_EXT_texture_shared_exponent, GL_ARB_framebuffer_object, 
    GL_EXT_framebuffer_blit, GL_EXT_framebuffer_multisample, 
    GL_EXT_packed_depth_stencil, GL_APPLE_object_purgeable, 
    GL_ARB_vertex_array_object, GL_ATI_separate_stencil, GL_EXT_draw_buffers2, 
    GL_EXT_draw_instanced, GL_EXT_gpu_program_parameters, 
    GL_EXT_texture_array, GL_EXT_texture_integer, GL_EXT_texture_sRGB_decode, 
    GL_EXT_timer_query, GL_OES_EGL_image, GL_MESA_texture_array, 
    GL_ARB_copy_buffer, GL_ARB_depth_buffer_float, GL_ARB_draw_instanced, 
    GL_ARB_half_float_vertex, GL_ARB_instanced_arrays, 
    GL_ARB_map_buffer_range, GL_ARB_texture_rg, GL_ARB_texture_swizzle, 
    GL_ARB_vertex_array_bgra, GL_EXT_separate_shader_objects, 
    GL_EXT_texture_swizzle, GL_EXT_vertex_array_bgra, 
    GL_NV_conditional_render, GL_AMD_draw_buffers_blend, 
    GL_ARB_ES2_compatibility, GL_ARB_blend_func_extended, GL_ARB_debug_output, 
    GL_ARB_draw_buffers_blend, GL_ARB_draw_elements_base_vertex, 
    GL_ARB_explicit_attrib_location, GL_ARB_fragment_coord_conventions, 
    GL_ARB_provoking_vertex, GL_ARB_sampler_objects, GL_ARB_seamless_cube_map, 
    GL_ARB_shader_texture_lod, GL_ARB_texture_rgb10_a2ui, 
    GL_ARB_uniform_buffer_object, GL_EXT_provoking_vertex, 
    GL_EXT_texture_snorm, GL_MESA_texture_signed_rgba, GL_ARB_robustness, 
    GL_ARB_shader_bit_encoding, GL_ARB_texture_storage, 
    GL_EXT_transform_feedback, GL_ARB_invalidate_subdata

40 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x021 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x022 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0b2 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0b3 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0b4 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0b5 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0b6 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0b7 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0b8 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0b9 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0ba 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0bb 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0bc 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0bd 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0be 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0bf 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x0c0 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  4 1 None
0x0c1 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  4 1 None
0x0c2 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x0c3 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x0c4 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0c5 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0c6 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0c7 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0c8 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0c9 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0ca 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0cb 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0cc 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0cd 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0ce 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0cf 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0d0 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0d1 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0d2 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x0d3 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  4 1 None
0x0d4 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  4 1 None
0x0d5 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x0d6 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x075 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None

60 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x076  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x077  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x078  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x079  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x07a  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x07b  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x07c 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x07d 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x07e 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x07f 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x080 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x081 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x082 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x083 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x084 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x085 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x086 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x087 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x088  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x089  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x08a 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x08b 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x08c 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x08d 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x08e  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  4 1 None
0x08f  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  4 1 None
0x090 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  4 1 None
0x091 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  4 1 None
0x092 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x093 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x094  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x095  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x096  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x097  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x098  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x099  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x09a 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x09b 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x09c 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x09d 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x09e 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x09f 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0a0 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0a1 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0a2 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0a3 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0a4 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0a5 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0a6  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x0a7  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x0a8 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0a9 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0aa 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0ab 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x0ac  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  4 1 None
0x0ad  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  4 1 None
0x0ae 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  4 1 None
0x0af 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  4 1 None
0x0b0 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x0b1 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None

```I appreciate any help. :)

---

### Post by feathre on 2012-12-01
bump

still need help

---

### Post by ahallubuntu on 2012-12-01
While you are welcome to post Mint-related questions here, you are less likely to get good response about it on a Ubuntu forum.  Not all versions of Mint are even based on Ubuntu.

I guess I'd suggest booting a Ubuntu 12.04 and/or 12.10 live cd and compare performance with those vs. what you are seeing in Mint.

---

### Post by Yellow Pasque on 2012-12-01
glxinfo looks good. Can you post the /var/log/Xorg.0.log ?

---

### Post by feathre on 2012-12-01
> **Temüjin said:**
> glxinfo looks good. Can you post the /var/log/Xorg.0.log ?

Ok, I just saw 'none' and 'slow' so I assumed that was bad.

Here is var/log/Xorg.0.log

```
[    12.683] 
X.Org X Server 1.13.0
Release Date: 2012-09-05
[    12.683] X Protocol Version 11, Revision 0
[    12.683] Build Operating System: Linux 3.2.0-30-generic x86_64 Ubuntu
[    12.683] Current Operating System: Linux destroyerofworlds 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:31:23 UTC 2012 x86_64
[    12.683] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-17-generic root=UUID=23fd8034-0b84-47f7-872b-1358c5309239 ro quiet splash vt.handoff=7
[    12.683] Build Date: 08 October 2012  03:34:01PM
[    12.683] xorg-server 2:1.13.0-0ubuntu6 (For technical support please see http://www.ubuntu.com/support) 
[    12.683] Current version of pixman: 0.26.0
[    12.683]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    12.683] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    12.683] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Dec  1 17:00:15 2012
[    12.702] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    12.702] (==) No Layout section.  Using the first Screen section.
[    12.702] (==) No screen section available. Using defaults.
[    12.702] (**) |-->Screen "Default Screen Section" (0)
[    12.702] (**) |   |-->Monitor "<default monitor>"
[    12.702] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    12.702] (==) Automatically adding devices
[    12.703] (==) Automatically enabling devices
[    12.703] (==) Automatically adding GPU devices
[    12.703] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    12.703]     Entry deleted from font path.
[    12.703] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    12.703]     Entry deleted from font path.
[    12.703] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    12.703]     Entry deleted from font path.
[    12.703] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    12.703]     Entry deleted from font path.
[    12.703] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    12.703]     Entry deleted from font path.
[    12.703] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    12.703]     Entry deleted from font path.
[    12.703] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    12.703] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    12.703] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    12.703] (II) Loader magic: 0x7f71ac1c3c40
[    12.703] (II) Module ABI versions:
[    12.703]     X.Org ANSI C Emulation: 0.4
[    12.703]     X.Org Video Driver: 13.0
[    12.703]     X.Org XInput driver : 18.0
[    12.703]     X.Org Server Extension : 7.0
[    12.703] (II) config/udev: Adding drm device (/dev/dri/card0)
[    12.703] setversion 1.4 failed
[    12.704] (--) PCI:*(0:0:2:0) 8086:0102:1043:84ca rev 9, Mem @ 0xf7800000/4194304, 0xe0000000/268435456, I/O @ 0x0000f000/64
[    12.704] (II) Open ACPI successful (/var/run/acpid.socket)
[    12.704] Initializing built-in extension Generic Event Extension
[    12.704] Initializing built-in extension SHAPE
[    12.704] Initializing built-in extension MIT-SHM
[    12.704] Initializing built-in extension XInputExtension
[    12.704] Initializing built-in extension XTEST
[    12.704] Initializing built-in extension BIG-REQUESTS
[    12.704] Initializing built-in extension SYNC
[    12.704] Initializing built-in extension XKEYBOARD
[    12.704] Initializing built-in extension XC-MISC
[    12.704] Initializing built-in extension SECURITY
[    12.704] Initializing built-in extension XINERAMA
[    12.704] Initializing built-in extension XFIXES
[    12.704] Initializing built-in extension RENDER
[    12.704] Initializing built-in extension RANDR
[    12.704] Initializing built-in extension COMPOSITE
[    12.704] Initializing built-in extension DAMAGE
[    12.704] Initializing built-in extension MIT-SCREEN-SAVER
[    12.704] Initializing built-in extension DOUBLE-BUFFER
[    12.704] Initializing built-in extension RECORD
[    12.704] Initializing built-in extension DPMS
[    12.704] Initializing built-in extension X-Resource
[    12.704] Initializing built-in extension XVideo
[    12.704] Initializing built-in extension XVideo-MotionCompensation
[    12.704] Initializing built-in extension XFree86-VidModeExtension
[    12.704] Initializing built-in extension XFree86-DGA
[    12.704] Initializing built-in extension XFree86-DRI
[    12.704] Initializing built-in extension DRI2
[    12.704] (II) LoadModule: "glx"
[    12.749] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    12.749] (II) Module glx: vendor="X.Org Foundation"
[    12.749]     compiled for 1.13.0, module version = 1.0.0
[    12.749]     ABI class: X.Org Server Extension, version 7.0
[    12.749] (==) AIGLX enabled
[    12.750] Loading extension GLX
[    12.750] (==) Matched intel as autoconfigured driver 0
[    12.750] (==) Matched vesa as autoconfigured driver 1
[    12.750] (==) Matched modesetting as autoconfigured driver 2
[    12.750] (==) Matched fbdev as autoconfigured driver 3
[    12.750] (==) Assigned the driver to the xf86ConfigLayout
[    12.750] (II) LoadModule: "intel"
[    12.750] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    12.750] (II) Module intel: vendor="X.Org Foundation"
[    12.750]     compiled for 1.13.0, module version = 2.20.9
[    12.750]     Module class: X.Org Video Driver
[    12.750]     ABI class: X.Org Video Driver, version 13.0
[    12.750] (II) LoadModule: "vesa"
[    12.750] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    12.750] (II) Module vesa: vendor="X.Org Foundation"
[    12.750]     compiled for 1.12.99.902, module version = 2.3.2
[    12.750]     Module class: X.Org Video Driver
[    12.750]     ABI class: X.Org Video Driver, version 13.0
[    12.750] (II) LoadModule: "modesetting"
[    12.750] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    12.750] (II) Module modesetting: vendor="X.Org Foundation"
[    12.750]     compiled for 1.13.0, module version = 0.5.0
[    12.750]     Module class: X.Org Video Driver
[    12.750]     ABI class: X.Org Video Driver, version 13.0
[    12.750] (II) LoadModule: "fbdev"
[    12.750] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    12.750] (II) Module fbdev: vendor="X.Org Foundation"
[    12.750]     compiled for 1.12.99.902, module version = 0.4.3
[    12.750]     Module class: X.Org Video Driver
[    12.750]     ABI class: X.Org Video Driver, version 13.0
[    12.750] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
    Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
    Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
    Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
    Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server,
    Ivybridge Server (GT2), Haswell Desktop (GT1), Haswell Desktop (GT2),
    Haswell Desktop (GT2+), Haswell Mobile (GT1), Haswell Mobile (GT2),
    Haswell Mobile (GT2+), Haswell Server (GT1), Haswell Server (GT2),
    Haswell Server (GT2+), Haswell SDV Desktop (GT1),
    Haswell SDV Desktop (GT2), Haswell SDV Desktop (GT2+),
    Haswell SDV Mobile (GT1), Haswell SDV Mobile (GT2),
    Haswell SDV Mobile (GT2+), Haswell SDV Server (GT1),
    Haswell SDV Server (GT2), Haswell SDV Server (GT2+),
    Haswell ULT Desktop (GT1), Haswell ULT Desktop (GT2),
    Haswell ULT Desktop (GT2+), Haswell ULT Mobile (GT1),
    Haswell ULT Mobile (GT2), Haswell ULT Mobile (GT2+),
    Haswell ULT Server (GT1), Haswell ULT Server (GT2),
    Haswell ULT Server (GT2+), Haswell CRW Desktop (GT1),
    Haswell CRW Desktop (GT2), Haswell CRW Desktop (GT2+),
    Haswell CRW Mobile (GT1), Haswell CRW Mobile (GT2),
    Haswell CRW Mobile (GT2+), Haswell CRW Server (GT1),
    Haswell CRW Server (GT2), Haswell CRW Server (GT2+),
    ValleyView PO board
[    12.751] (II) VESA: driver for VESA chipsets: vesa
[    12.751] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    12.751] (II) FBDEV: driver for framebuffer: fbdev
[    12.751] (++) using VT number 8

[    12.769] (WW) Falling back to old probe method for vesa
[    12.769] (WW) Falling back to old probe method for modesetting
[    12.769] (WW) Falling back to old probe method for fbdev
[    12.769] (II) Loading sub module "fbdevhw"
[    12.769] (II) LoadModule: "fbdevhw"
[    12.770] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    12.770] (II) Module fbdevhw: vendor="X.Org Foundation"
[    12.770]     compiled for 1.13.0, module version = 0.0.2
[    12.770]     ABI class: X.Org Video Driver, version 13.0
[    12.770] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    12.770] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    12.770] (==) intel(0): RGB weight 888
[    12.770] (==) intel(0): Default visual is TrueColor
[    12.770] (--) intel(0): Integrated Graphics Chipset: Intel(R) Sandybridge Desktop (GT1)
[    12.770] (**) intel(0): Relaxed fencing enabled
[    12.770] (**) intel(0): Wait on SwapBuffers? enabled
[    12.770] (**) intel(0): Triple buffering? enabled
[    12.770] (**) intel(0): Framebuffer tiled
[    12.770] (**) intel(0): Pixmaps tiled
[    12.770] (**) intel(0): 3D buffers tiled
[    12.770] (**) intel(0): SwapBuffers wait enabled
[    12.770] (==) intel(0): video overlay key set to 0x101fe
[    12.920] (II) intel(0): Output VGA1 has no monitor section
[    12.920] (II) intel(0): Output HDMI1 has no monitor section
[    12.968] (II) intel(0): Output DP1 has no monitor section
[    12.984] (II) intel(0): Output HDMI2 has no monitor section
[    13.032] (II) intel(0): Output DP2 has no monitor section
[    13.184] (II) intel(0): EDID for output VGA1
[    13.184] (II) intel(0): Manufacturer: AOC  Model: 1917  Serial#: 88011
[    13.184] (II) intel(0): Year: 2009  Week: 12
[    13.184] (II) intel(0): EDID Version: 1.3
[    13.184] (II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[    13.184] (II) intel(0): Sync:  Separate
[    13.184] (II) intel(0): Max Image Size [cm]: horiz.: 40  vert.: 25
[    13.184] (II) intel(0): Gamma: 2.20
[    13.184] (II) intel(0): DPMS capabilities: Off; RGB/Color Display
[    13.184] (II) intel(0): Default color space is primary color space
[    13.184] (II) intel(0): First detailed timing is preferred mode
[    13.184] (II) intel(0): redX: 0.636 redY: 0.349   greenX: 0.290 greenY: 0.584
[    13.184] (II) intel(0): blueX: 0.143 blueY: 0.080   whiteX: 0.313 whiteY: 0.329
[    13.184] (II) intel(0): Supported established timings:
[    13.184] (II) intel(0): 720x400@70Hz
[    13.184] (II) intel(0): 640x480@60Hz
[    13.184] (II) intel(0): 640x480@67Hz
[    13.184] (II) intel(0): 640x480@72Hz
[    13.184] (II) intel(0): 640x480@75Hz
[    13.184] (II) intel(0): 800x600@56Hz
[    13.184] (II) intel(0): 800x600@60Hz
[    13.184] (II) intel(0): 800x600@72Hz
[    13.184] (II) intel(0): 800x600@75Hz
[    13.184] (II) intel(0): 832x624@75Hz
[    13.184] (II) intel(0): 1024x768@60Hz
[    13.184] (II) intel(0): 1024x768@70Hz
[    13.184] (II) intel(0): 1024x768@75Hz
[    13.184] (II) intel(0): 1280x1024@75Hz
[    13.184] (II) intel(0): Manufacturer's mask: 0
[    13.184] (II) intel(0): Supported standard timings:
[    13.184] (II) intel(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    13.184] (II) intel(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    13.184] (II) intel(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    13.184] (II) intel(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    13.184] (II) intel(0): #4: hsize: 1440  vsize 900  refresh: 75  vid: 3989
[    13.184] (II) intel(0): Supported detailed timing:
[    13.184] (II) intel(0): clock: 106.5 MHz   Image Size:  410 x 256 mm
[    13.184] (II) intel(0): h_active: 1440  h_sync: 1520  h_sync_end 1672 h_blank_end 1904 h_border: 0
[    13.184] (II) intel(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 934 v_border: 0
[    13.184] (II) intel(0): Ranges: V min: 55 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 145 MHz
[    13.184] (II) intel(0): Monitor name: 917W
[    13.184] (II) intel(0): Serial No: L2193JA088011
[    13.184] (II) intel(0): EDID (in hex):
[    13.184] (II) intel(0):     00ffffffffffff0005e31719cb570100
[    13.184] (II) intel(0):     0c130103682819782ed6a5a2594a9524
[    13.184] (II) intel(0):     145054bfef00714f814081809500950f
[    13.184] (II) intel(0):     0101010101019a29a0d0518422305098
[    13.184] (II) intel(0):     36009a001100001c000000fd00374b1e
[    13.184] (II) intel(0):     530e000a202020202020000000fc0039
[    13.184] (II) intel(0):     3137570a2020202020202020000000ff
[    13.184] (II) intel(0):     004c323139334a4130383830313100dd
[    13.184] (II) intel(0): Printing probed modes for output VGA1
[    13.184] (II) intel(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz eP)
[    13.184] (II) intel(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    13.184] (II) intel(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    13.184] (II) intel(0): Modeline "1440x900"x75.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz e)
[    13.184] (II) intel(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    13.184] (II) intel(0): Modeline "1366x768"x60.0   85.89  1366 1439 1583 1800  768 769 772 795 -hsync +vsync (47.7 kHz)
[    13.184] (II) intel(0): Modeline "1360x768"x60.0   85.50  1360 1424 1536 1792  768 771 777 795 +hsync +vsync (47.7 kHz e)
[    13.184] (II) intel(0): Modeline "1280x800"x74.9  106.50  1280 1360 1488 1696  800 803 809 838 -hsync +vsync (62.8 kHz e)
[    13.184] (II) intel(0): Modeline "1280x800"x59.8   83.50  1280 1352 1480 1680  800 803 809 831 +hsync -vsync (49.7 kHz e)
[    13.184] (II) intel(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    13.184] (II) intel(0): Modeline "1280x768"x74.9  102.25  1280 1360 1488 1696  768 771 778 805 +hsync -vsync (60.3 kHz e)
[    13.184] (II) intel(0): Modeline "1280x768"x59.9   79.50  1280 1344 1472 1664  768 771 778 798 -hsync +vsync (47.8 kHz e)
[    13.184] (II) intel(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz e)
[    13.184] (II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    13.184] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    13.184] (II) intel(0): Modeline "1024x576"x60.0   46.97  1024 1064 1168 1312  576 577 580 597 -hsync +vsync (35.8 kHz)
[    13.184] (II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    13.184] (II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    13.184] (II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    13.184] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    13.184] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    13.184] (II) intel(0): Modeline "848x480"x60.0   33.75  848 864 976 1088  480 486 494 517 +hsync +vsync (31.0 kHz e)
[    13.184] (II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz e)
[    13.184] (II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    13.184] (II) intel(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    13.184] (II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    13.184] (II) intel(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    13.185] (II) intel(0): EDID for output HDMI1
[    13.236] (II) intel(0): EDID for output DP1
[    13.252] (II) intel(0): EDID for output HDMI2
[    13.300] (II) intel(0): EDID for output DP2
[    13.300] (II) intel(0): Output VGA1 connected
[    13.300] (II) intel(0): Output HDMI1 disconnected
[    13.300] (II) intel(0): Output DP1 disconnected
[    13.300] (II) intel(0): Output HDMI2 disconnected
[    13.300] (II) intel(0): Output DP2 disconnected
[    13.300] (II) intel(0): Using exact sizes for initial modes
[    13.300] (II) intel(0): Output VGA1 using initial mode 1440x900
[    13.300] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    13.300] (II) intel(0): Kernel page flipping support detected, enabling
[    13.300] (==) intel(0): DPI set to (96, 96)
[    13.300] (II) Loading sub module "fb"
[    13.300] (II) LoadModule: "fb"
[    13.300] (II) Loading /usr/lib/xorg/modules/libfb.so
[    13.300] (II) Module fb: vendor="X.Org Foundation"
[    13.300]     compiled for 1.13.0, module version = 1.0.0
[    13.300]     ABI class: X.Org ANSI C Emulation, version 0.4
[    13.300] (II) Loading sub module "dri2"
[    13.300] (II) LoadModule: "dri2"
[    13.300] (II) Module "dri2" already built-in
[    13.300] (II) UnloadModule: "vesa"
[    13.300] (II) Unloading vesa
[    13.300] (II) UnloadModule: "modesetting"
[    13.300] (II) Unloading modesetting
[    13.300] (II) UnloadModule: "fbdev"
[    13.300] (II) Unloading fbdev
[    13.300] (II) UnloadSubModule: "fbdevhw"
[    13.300] (II) Unloading fbdevhw
[    13.300] (==) Depth 24 pixmap format is 32 bpp
[    13.300] (II) intel(0): [DRI2] Setup complete
[    13.300] (II) intel(0): [DRI2]   DRI driver: i965
[    13.300] (II) intel(0): Allocated new frame buffer 1472x900 stride 6144, tiled
[    13.301] (II) UXA(0): Driver registered support for the following operations:
[    13.301] (II)         solid
[    13.301] (II)         copy
[    13.301] (II)         composite (RENDER acceleration)
[    13.301] (II)         put_image
[    13.301] (II)         get_image
[    13.301] (==) intel(0): Backing store disabled
[    13.301] (==) intel(0): Silken mouse enabled
[    13.301] (II) intel(0): Initializing HW Cursor
[    13.301] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    13.301] (==) intel(0): DPMS enabled
[    13.301] (==) intel(0): Intel XvMC decoder enabled
[    13.301] (II) intel(0): Set up textured video
[    13.301] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[    13.301] (II) intel(0): direct rendering: DRI2 Enabled
[    13.301] (==) intel(0): hotplug detection: "enabled"
[    13.312] (--) RandR disabled
[    13.317] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    13.317] (II) AIGLX: enabled GLX_INTEL_swap_event
[    13.317] (II) AIGLX: enabled GLX_ARB_create_context
[    13.317] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    13.317] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    13.317] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    13.317] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    13.318] (II) AIGLX: Loaded and initialized i965
[    13.318] (II) GLX: Initialized DRI2 GL provider for screen 0
[    13.318] (II) intel(0): Setting screen physical size to 381 x 238
[    13.322] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    13.324] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    13.324] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    13.324] (II) LoadModule: "evdev"
[    13.324] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    13.324] (II) Module evdev: vendor="X.Org Foundation"
[    13.324]     compiled for 1.13.0, module version = 2.7.3
[    13.324]     Module class: X.Org XInput Driver
[    13.324]     ABI class: X.Org XInput driver, version 18.0
[    13.324] (II) Using input driver 'evdev' for 'Power Button'
[    13.324] (**) Power Button: always reports core events
[    13.324] (**) evdev: Power Button: Device: "/dev/input/event1"
[    13.324] (--) evdev: Power Button: Vendor 0 Product 0x1
[    13.324] (--) evdev: Power Button: Found keys
[    13.324] (II) evdev: Power Button: Configuring as keyboard
[    13.324] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    13.324] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    13.324] (**) Option "xkb_rules" "evdev"
[    13.324] (**) Option "xkb_model" "pc105"
[    13.324] (**) Option "xkb_layout" "us"
[    13.325] (II) config/udev: Adding input device Video Bus (/dev/input/event6)
[    13.325] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    13.325] (II) Using input driver 'evdev' for 'Video Bus'
[    13.325] (**) Video Bus: always reports core events
[    13.325] (**) evdev: Video Bus: Device: "/dev/input/event6"
[    13.325] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    13.325] (--) evdev: Video Bus: Found keys
[    13.325] (II) evdev: Video Bus: Configuring as keyboard
[    13.325] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6/event6"
[    13.325] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    13.325] (**) Option "xkb_rules" "evdev"
[    13.325] (**) Option "xkb_model" "pc105"
[    13.325] (**) Option "xkb_layout" "us"
[    13.325] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    13.325] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    13.325] (II) Using input driver 'evdev' for 'Power Button'
[    13.325] (**) Power Button: always reports core events
[    13.325] (**) evdev: Power Button: Device: "/dev/input/event0"
[    13.325] (--) evdev: Power Button: Vendor 0 Product 0x1
[    13.325] (--) evdev: Power Button: Found keys
[    13.325] (II) evdev: Power Button: Configuring as keyboard
[    13.325] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    13.325] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    13.325] (**) Option "xkb_rules" "evdev"
[    13.325] (**) Option "xkb_model" "pc105"
[    13.325] (**) Option "xkb_layout" "us"
[    13.325] (II) config/udev: Adding drm device (/dev/dri/card0)
[    13.325] (II) config/udev: Adding drm device (/dev/dri/card0)
[    13.325] setversion 1.4 failed
[    13.326] (II) config/udev: Adding input device HDA Intel PCH Rear Mic (/dev/input/event10)
[    13.326] (II) No input driver specified, ignoring this device.
[    13.326] (II) This device may have been added with another device file.
[    13.326] (II) config/udev: Adding input device HDA Intel PCH Front Headphone (/dev/input/event11)
[    13.326] (II) No input driver specified, ignoring this device.
[    13.326] (II) This device may have been added with another device file.
[    13.326] (II) config/udev: Adding input device HDA Intel PCH Line Out (/dev/input/event12)
[    13.326] (II) No input driver specified, ignoring this device.
[    13.326] (II) This device may have been added with another device file.
[    13.326] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event7)
[    13.326] (II) No input driver specified, ignoring this device.
[    13.326] (II) This device may have been added with another device file.
[    13.326] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event8)
[    13.326] (II) No input driver specified, ignoring this device.
[    13.326] (II) This device may have been added with another device file.
[    13.326] (II) config/udev: Adding input device HDA Intel PCH Front Mic (/dev/input/event9)
[    13.326] (II) No input driver specified, ignoring this device.
[    13.326] (II) This device may have been added with another device file.
[    13.327] (II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/event3)
[    13.327] (**) Logitech USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[    13.327] (II) Using input driver 'evdev' for 'Logitech USB Optical Mouse'
[    13.327] (**) Logitech USB Optical Mouse: always reports core events
[    13.327] (**) evdev: Logitech USB Optical Mouse: Device: "/dev/input/event3"
[    13.327] (--) evdev: Logitech USB Optical Mouse: Vendor 0x46d Product 0xc05a
[    13.327] (--) evdev: Logitech USB Optical Mouse: Found 3 mouse buttons
[    13.327] (--) evdev: Logitech USB Optical Mouse: Found scroll wheel(s)
[    13.327] (--) evdev: Logitech USB Optical Mouse: Found relative axes
[    13.327] (--) evdev: Logitech USB Optical Mouse: Found x and y relative axes
[    13.327] (II) evdev: Logitech USB Optical Mouse: Configuring as mouse
[    13.327] (II) evdev: Logitech USB Optical Mouse: Adding scrollwheel support
[    13.327] (**) evdev: Logitech USB Optical Mouse: YAxisMapping: buttons 4 and 5
[    13.327] (**) evdev: Logitech USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    13.327] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.0/input/input3/event3"
[    13.327] (II) XINPUT: Adding extended input device "Logitech USB Optical Mouse" (type: MOUSE, id 9)
[    13.327] (II) evdev: Logitech USB Optical Mouse: initialized for relative axes.
[    13.327] (**) Logitech USB Optical Mouse: (accel) keeping acceleration scheme 1
[    13.327] (**) Logitech USB Optical Mouse: (accel) acceleration profile 0
[    13.327] (**) Logitech USB Optical Mouse: (accel) acceleration factor: 2.000
[    13.327] (**) Logitech USB Optical Mouse: (accel) acceleration threshold: 4
[    13.327] (II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/mouse0)
[    13.327] (II) No input driver specified, ignoring this device.
[    13.327] (II) This device may have been added with another device file.
[    13.327] (II) config/udev: Adding input device USB2.0 1.3MP UVC Camera (/dev/input/event5)
[    13.327] (**) USB2.0 1.3MP UVC Camera: Applying InputClass "evdev keyboard catchall"
[    13.327] (II) Using input driver 'evdev' for 'USB2.0 1.3MP UVC Camera'
[    13.327] (**) USB2.0 1.3MP UVC Camera: always reports core events
[    13.327] (**) evdev: USB2.0 1.3MP UVC Camera: Device: "/dev/input/event5"
[    13.327] (--) evdev: USB2.0 1.3MP UVC Camera: Vendor 0x4f2 Product 0xa133
[    13.327] (--) evdev: USB2.0 1.3MP UVC Camera: Found keys
[    13.327] (II) evdev: USB2.0 1.3MP UVC Camera: Configuring as keyboard
[    13.327] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.7/2-1.7:1.0/input/input5/event5"
[    13.327] (II) XINPUT: Adding extended input device "USB2.0 1.3MP UVC Camera" (type: KEYBOARD, id 10)
[    13.327] (**) Option "xkb_rules" "evdev"
[    13.327] (**) Option "xkb_model" "pc105"
[    13.327] (**) Option "xkb_layout" "us"
[    13.328] (II) config/udev: Adding input device Eee PC WMI hotkeys (/dev/input/event4)
[    13.328] (**) Eee PC WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    13.328] (II) Using input driver 'evdev' for 'Eee PC WMI hotkeys'
[    13.328] (**) Eee PC WMI hotkeys: always reports core events
[    13.328] (**) evdev: Eee PC WMI hotkeys: Device: "/dev/input/event4"
[    13.328] (--) evdev: Eee PC WMI hotkeys: Vendor 0 Product 0
[    13.328] (--) evdev: Eee PC WMI hotkeys: Found keys
[    13.328] (II) evdev: Eee PC WMI hotkeys: Configuring as keyboard
[    13.328] (**) Option "config_info" "udev:/sys/devices/platform/eeepc-wmi/input/input4/event4"
[    13.328] (II) XINPUT: Adding extended input device "Eee PC WMI hotkeys" (type: KEYBOARD, id 11)
[    13.328] (**) Option "xkb_rules" "evdev"
[    13.328] (**) Option "xkb_model" "pc105"
[    13.328] (**) Option "xkb_layout" "us"
[    13.328] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    13.328] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    13.328] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    13.328] (**) AT Translated Set 2 keyboard: always reports core events
[    13.328] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    13.328] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    13.328] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    13.328] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    13.328] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    13.328] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 12)
[    13.328] (**) Option "xkb_rules" "evdev"
[    13.328] (**) Option "xkb_model" "pc105"
[    13.328] (**) Option "xkb_layout" "us"
[   126.188] (II) intel(0): EDID vendor "AOC", prod id 6423
[   126.188] (II) intel(0): Using EDID range info for horizontal sync
[   126.188] (II) intel(0): Using EDID range info for vertical refresh
[   126.188] (II) intel(0): Printing DDC gathered Modelines:
[   126.188] (II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz eP)
[   126.188] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   126.188] (II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[   126.188] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   126.188] (II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[   126.188] (II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[   126.188] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   126.188] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   126.188] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   126.188] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   126.188] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[   126.188] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   126.188] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[   126.188] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   126.188] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[   126.188] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   126.188] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[   126.188] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   126.188] (II) intel(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz e)
[   126.748] (II) intel(0): EDID vendor "AOC", prod id 6423
[   126.748] (II) intel(0): Using hsync ranges from config file
[   126.748] (II) intel(0): Using vrefresh ranges from config file
[   126.748] (II) intel(0): Printing DDC gathered Modelines:
[   126.748] (II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz eP)
[   126.748] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   126.748] (II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[   126.748] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   126.748] (II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[   126.748] (II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[   126.748] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   126.748] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   126.748] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   126.748] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   126.748] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[   126.748] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   126.748] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[   126.748] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   126.748] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[   126.748] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   126.748] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[   126.748] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   126.748] (II) intel(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz e)
[   127.307] (II) XKB: reuse xkmfile /var/lib/xkb/server-4C3C2942247BAA242BCE056FA94ECD03DFCD0EF3.xkm
[   127.363] (II) XKB: reuse xkmfile /var/lib/xkb/server-40E30DEF28B9EC38E85E9169C62CF656FCA2599B.xkm
[   129.539] (II) XKB: reuse xkmfile /var/lib/xkb/server-40E30DEF28B9EC38E85E9169C62CF656FCA2599B.xkm
[   129.542] (II) XKB: reuse xkmfile /var/lib/xkb/server-40E30DEF28B9EC38E85E9169C62CF656FCA2599B.xkm
[   129.545] (II) XKB: reuse xkmfile /var/lib/xkb/server-40E30DEF28B9EC38E85E9169C62CF656FCA2599B.xkm
[   129.548] (II) XKB: reuse xkmfile /var/lib/xkb/server-40E30DEF28B9EC38E85E9169C62CF656FCA2599B.xkm
[   129.552] (II) XKB: reuse xkmfile /var/lib/xkb/server-40E30DEF28B9EC38E85E9169C62CF656FCA2599B.xkm
[   129.554] (II) XKB: reuse xkmfile /var/lib/xkb/server-40E30DEF28B9EC38E85E9169C62CF656FCA2599B.xkm
[   129.557] (II) XKB: reuse xkmfile /var/lib/xkb/server-40E30DEF28B9EC38E85E9169C62CF656FCA2599B.xkm
[   129.560] (II) XKB: reuse xkmfile /var/lib/xkb/server-40E30DEF28B9EC38E85E9169C62CF656FCA2599B.xkm
[   129.563] (II) XKB: reuse xkmfile /var/lib/xkb/server-40E30DEF28B9EC38E85E9169C62CF656FCA2599B.xkm
[   129.566] (II) XKB: reuse xkmfile /var/lib/xkb/server-40E30DEF28B9EC38E85E9169C62CF656FCA2599B.xkm
[   129.569] (II) XKB: reuse xkmfile /var/lib/xkb/server-40E30DEF28B9EC38E85E9169C62CF656FCA2599B.xkm
[   129.572] (II) XKB: reuse xkmfile /var/lib/xkb/server-40E30DEF28B9EC38E85E9169C62CF656FCA2599B.xkm
[   129.575] (II) XKB: reuse xkmfile /var/lib/xkb/server-40E30DEF28B9EC38E85E9169C62CF656FCA2599B.xkm
[   129.578] (II) XKB: reuse xkmfile /var/lib/xkb/server-40E30DEF28B9EC38E85E9169C62CF656FCA2599B.xkm
[   129.581] (II) XKB: reuse xkmfile /var/lib/xkb/server-40E30DEF28B9EC38E85E9169C62CF656FCA2599B.xkm
[   129.585] (II) XKB: reuse xkmfile /var/lib/xkb/server-40E30DEF28B9EC38E85E9169C62CF656FCA2599B.xkm
[   129.588] (II) XKB: reuse xkmfile /var/lib/xkb/server-40E30DEF28B9EC38E85E9169C62CF656FCA2599B.xkm
[   129.591] (II) XKB: reuse xkmfile /var/lib/xkb/server-40E30DEF28B9EC38E85E9169C62CF656FCA2599B.xkm
[   129.595] (II) XKB: reuse xkmfile /var/lib/xkb/server-40E30DEF28B9EC38E85E9169C62CF656FCA2599B.xkm
[   129.598] (II) XKB: reuse xkmfile /var/lib/xkb/server-40E30DEF28B9EC38E85E9169C62CF656FCA2599B.xkm
[   129.602] (II) XKB: reuse xkmfile /var/lib/xkb/server-40E30DEF28B9EC38E85E9169C62CF656FCA2599B.xkm
[   129.605] (II) XKB: reuse xkmfile /var/lib/xkb/server-40E30DEF28B9EC38E85E9169C62CF656FCA2599B.xkm
[   129.608] (II) XKB: reuse xkmfile /var/lib/xkb/server-40E30DEF28B9EC38E85E9169C62CF656FCA2599B.xkm
[   129.610] (II) XKB: reuse xkmfile /var/lib/xkb/server-40E30DEF28B9EC38E85E9169C62CF656FCA2599B.xkm
[   129.613] (II) XKB: reuse xkmfile /var/lib/xkb/server-40E30DEF28B9EC38E85E9169C62CF656FCA2599B.xkm
[   129.780] (II) XKB: reuse xkmfile /var/lib/xkb/server-40E30DEF28B9EC38E85E9169C62CF656FCA2599B.xkm
[   129.783] (II) XKB: reuse xkmfile /var/lib/xkb/server-40E30DEF28B9EC38E85E9169C62CF656FCA2599B.xkm
[   129.787] (II) XKB: reuse xkmfile /var/lib/xkb/server-40E30DEF28B9EC38E85E9169C62CF656FCA2599B.xkm
[   129.790] (II) XKB: reuse xkmfile /var/lib/xkb/server-40E30DEF28B9EC38E85E9169C62CF656FCA2599B.xkm
[   129.794] (II) XKB: reuse xkmfile /var/lib/xkb/server-40E30DEF28B9EC38E85E9169C62CF656FCA2599B.xkm
[   129.797] (II) XKB: reuse xkmfile /var/lib/xkb/server-40E30DEF28B9EC38E85E9169C62CF656FCA2599B.xkm
[   129.801] (II) XKB: reuse xkmfile /var/lib/xkb/server-40E30DEF28B9EC38E85E9169C62CF656FCA2599B.xkm
[   129.804] (II) XKB: reuse xkmfile /var/lib/xkb/server-40E30DEF28B9EC38E85E9169C62CF656FCA2599B.xkm
[   147.560] (II) intel(0): EDID vendor "AOC", prod id 6423
[   147.560] (II) intel(0): Using hsync ranges from config file
[   147.560] (II) intel(0): Using vrefresh ranges from config file
[   147.560] (II) intel(0): Printing DDC gathered Modelines:
[   147.560] (II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz eP)
[   147.560] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   147.560] (II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[   147.560] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   147.560] (II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[   147.560] (II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[   147.560] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   147.560] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   147.560] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   147.560] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   147.560] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[   147.560] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   147.560] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[   147.560] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   147.560] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[   147.560] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   147.560] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[   147.560] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   147.560] (II) intel(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz e)
```

---

### Post by feathre on 2012-12-02
bump

any ideas?? thanks!

---

### Post by Portaro on 2012-12-03
Maybe you need reinstall mesa-utils, i have  a similar problem to your in XUbuntu and Lubuntus.

Please open synaptic and search for mesa-utils and then if mesa-utils is not installed install it.

Then update and verify the task manager to see if cpu charge are changes.

After this run glxinfo and glxgears or test an game like warzone2100 if he go slow the problem maintain if not i think your problem is like my, for some reason the new Ubuntus Xfce and LXDE and possible others variants dont have enabled this tool mesa-utils and the user is confused when glegears works but in games are slow peroformance, if install mesa-utils in some cases the problem can be solved.

---

