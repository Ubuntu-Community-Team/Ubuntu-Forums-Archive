---
title: "getting something more out of ATI Radeon 9200"
date: 2014-04-05
forum: Hardware
---

### Post by mastablasta on 2014-04-05
So i have this old PC where for some ot othe rreason one disk with windows on it stopped working. installing Ubuntu on second disk was also a bit strange experience (i already wrote about this in another thread), but eventually i succeded in installing it. Everything works on install out of the box inlcuding peripheal devices. so i guess it was all linux compatible.

So here is what i am working with:
[COLOR=#000000][FONT=Arial]AMD Athlon(tm) 64 Processor 3800+
1 GB DDR2 RAM
[/FONT][/COLOR][COLOR=#000000][FONT=Arial] Advanced Micro Devices, Inc. [AMD/ATI] RV280 [Radeon 9200] (rev 01)[/FONT][/COLOR]
Kubuntu 12.04 32bit ( i think original kernel & no hardware enablement stack)


some driver info
```
[COLOR=#000000][FONT=Arial]dmesg | egrep 'drm|radeon'[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial][   27.607641] [drm] Initialized drm 1.1.0 20060810[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial][   27.638478] [drm] radeon defaulting to kernel modesetting.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial][   27.638484] [drm] radeon kernel modesetting enabled.[/FONT][/COLOR]
```

as i understand this means i do have hardware 3D acceleraiton:
```
[COLOR=#000000][FONT=Arial]LIBGL_DEBUG=verbose glxinfo[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]name of display: :0[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]libGL: screen 0 does not appear to be DRI2 capable[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]libGL: OpenDriver: trying /usr/lib/i386-linux-gnu/dri/tls/swrast_dri.so[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]libGL: OpenDriver: trying /usr/lib/i386-linux-gnu/dri/swrast_dri.so[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]libGL: Can't open configuration file /etc/drirc: No such file or directory.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]libGL: Can't open configuration file /home/gorjan/.drirc: No such file or directory.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]display: :0  screen: 0[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]direct rendering: Yes[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]server glx vendor string: SGI[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]server glx version string: 1.4[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]server glx extensions:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_fbconfig,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GLX_SGIX_pbuffer, GLX_MESA_copy_sub_buffer, GLX_INTEL_swap_event[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]client glx vendor string: Mesa Project and SGI[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]client glx version string: 1.4[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]client glx extensions:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GLX_ARB_create_context, GLX_ARB_create_context_profile,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_framebuffer_sRGB,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GLX_EXT_create_context_es2_profile, GLX_MESA_copy_sub_buffer,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GLX_MESA_multithread_makecurrent, GLX_MESA_swap_control,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GLX_OML_swap_method, GLX_OML_sync_control, GLX_SGI_make_current_read,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GLX_EXT_texture_from_pixmap, GLX_INTEL_swap_event[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]GLX version: 1.4[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]GLX extensions:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GLX_EXT_visual_info, GLX_EXT_visual_rating,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GLX_MESA_multithread_makecurrent, GLX_OML_swap_method,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_fbconfig,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GLX_SGIX_pbuffer, GLX_EXT_texture_from_pixmap[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]OpenGL vendor string: VMware, Inc.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 0x300)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]OpenGL version string: 2.1 Mesa 8.0.4[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]OpenGL shading language version string: 1.20[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]OpenGL extensions:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GL_ARB_multisample, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_copy_texture,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GL_EXT_polygon_offset, GL_EXT_subtexture, GL_EXT_texture_object,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GL_EXT_vertex_array, GL_EXT_compiled_vertex_array, GL_EXT_texture,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GL_EXT_texture3D, GL_IBM_rasterpos_clip, GL_ARB_point_parameters,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GL_EXT_draw_range_elements, GL_EXT_packed_pixels, GL_EXT_point_parameters,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GL_EXT_rescale_normal, GL_EXT_separate_specular_color,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GL_EXT_texture_edge_clamp, GL_SGIS_generate_mipmap,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GL_SGIS_texture_lod, GL_ARB_multitexture, GL_IBM_multimode_draw_arrays,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GL_IBM_texture_mirrored_repeat, GL_ARB_texture_cube_map,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GL_ARB_texture_env_add, GL_ARB_transpose_matrix,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GL_EXT_blend_func_separate, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GL_EXT_secondary_color, GL_EXT_texture_env_add, GL_EXT_texture_lod_bias,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GL_INGR_blend_func_separate, GL_NV_blend_square, GL_NV_light_max_exponent,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GL_NV_texgen_reflection, GL_NV_texture_env_combine4,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GL_SUN_multi_draw_arrays, GL_ARB_texture_border_clamp,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GL_ARB_texture_compression, GL_EXT_framebuffer_object,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, GL_MESA_window_pos,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GL_NV_packed_depth_stencil, GL_NV_texture_rectangle, GL_ARB_depth_texture,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GL_ARB_occlusion_query, GL_ARB_shadow, GL_ARB_texture_env_combine,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GL_ARB_texture_mirrored_repeat, GL_ARB_window_pos,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GL_EXT_stencil_two_side, GL_EXT_texture_cube_map, GL_NV_fog_distance,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GL_APPLE_packed_pixels, GL_APPLE_vertex_array_object, GL_ARB_draw_buffers,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GL_ARB_fragment_program, GL_ARB_fragment_shader, GL_ARB_shader_objects,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ATI_draw_buffers,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GL_ATI_texture_env_combine3, GL_ATI_texture_float, GL_EXT_shadow_funcs,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GL_EXT_stencil_wrap, GL_MESA_pack_invert, GL_MESA_ycbcr_texture,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GL_NV_primitive_restart, GL_ARB_fragment_program_shadow,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GL_ARB_half_float_pixel, GL_ARB_occlusion_query2, GL_ARB_point_sprite,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GL_ARB_shading_language_100, GL_ARB_sync, GL_ARB_texture_non_power_of_two,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GL_ARB_vertex_buffer_object, GL_ATI_blend_equation_separate,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GL_EXT_blend_equation_separate, GL_OES_read_format,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GL_ARB_pixel_buffer_object, GL_ARB_texture_compression_rgtc,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GL_ARB_texture_float, GL_ARB_texture_rectangle,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GL_ATI_texture_compression_3dc, GL_EXT_packed_float,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GL_EXT_pixel_buffer_object, GL_EXT_texture_compression_rgtc,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GL_EXT_texture_mirror_clamp, GL_EXT_texture_rectangle,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GL_EXT_texture_sRGB, GL_EXT_texture_shared_exponent,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GL_ARB_framebuffer_object, GL_EXT_framebuffer_blit,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GL_EXT_framebuffer_multisample, GL_EXT_packed_depth_stencil,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GL_ARB_vertex_array_object, GL_ATI_separate_stencil,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GL_ATI_texture_mirror_once, GL_EXT_draw_buffers2, GL_EXT_draw_instanced,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GL_EXT_gpu_program_parameters, GL_EXT_texture_compression_latc,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GL_EXT_texture_sRGB_decode, GL_OES_EGL_image, GL_ARB_copy_buffer,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GL_ARB_draw_instanced, GL_ARB_half_float_vertex, GL_ARB_instanced_arrays,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GL_ARB_map_buffer_range, GL_ARB_texture_rg, GL_ARB_texture_swizzle,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GL_ARB_vertex_array_bgra, GL_EXT_separate_shader_objects,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GL_EXT_texture_swizzle, GL_EXT_vertex_array_bgra,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GL_NV_conditional_render, GL_AMD_draw_buffers_blend,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GL_ARB_ES2_compatibility, GL_ARB_draw_buffers_blend,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GL_ARB_draw_elements_base_vertex, GL_ARB_explicit_attrib_location,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GL_ARB_fragment_coord_conventions, GL_ARB_provoking_vertex,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GL_ARB_sampler_objects, GL_ARB_shader_texture_lod,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GL_ARB_vertex_type_2_10_10_10_rev, GL_EXT_provoking_vertex,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GL_EXT_texture_snorm, GL_MESA_texture_signed_rgba, GL_ARB_robustness,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    GL_ARB_texture_storage[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]96 GLX Visuals[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]----------------------------------------------------------------------------[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x021 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x022 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0f4 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0f5 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0f6 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0f7 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0f8 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0f9 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0fa 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0fb 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0fc 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0fd 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0fe 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0ff 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x100 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x101 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x102 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x103 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x104 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 32  0  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x105 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 32  0 16 16 16 16  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x106 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x107 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0 16 16 16 16  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x108 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x109 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0 16 16 16 16  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x10a 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x10b 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x10c 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x10d 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x10e 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x10f 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x110 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x111 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x112 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x113 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x114 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x115 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x116 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x117 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x118 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x119 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x11a 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x11b 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x11c 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 32  0  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x11d 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 32  0 16 16 16  0  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x11e 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x11f 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0 16 16 16  0  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x120 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x121 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0 16 16 16  0  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x122 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x123 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x124 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x125 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x126 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x127 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x128 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x129 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x12a 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x12b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x12c 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x12d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x12e 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x12f 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x130 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x131 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x132 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x133 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 32  0  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x134 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 32  0 16 16 16 16  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x135 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x136 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0 16 16 16 16  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x137 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x138 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0 16 16 16 16  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x139 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x13a 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x13b 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x13c 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x13d 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x13e 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x13f 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x140 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x141 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x142 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x143 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x144 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x145 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x146 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x147 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x148 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x149 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x14a 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x14b 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 32  0  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x14c 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 32  0 16 16 16  0  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x14d 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x14e 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0 16 16 16  0  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x14f 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x150 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0 16 16 16  0  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x063 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]144 GLXFBConfigs:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]----------------------------------------------------------------------------[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x064 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x065 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x066 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x067 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x068 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x069 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x06a 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x06b 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x06c 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x06d 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x06e 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x06f 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x070 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x071 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x072 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x073 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x074 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x075 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x076 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 32  0  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x077 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 32  0 16 16 16 16  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x078 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x079 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0 16 16 16 16  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x07a 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x07b 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0 16 16 16 16  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x07c 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x07d 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x07e 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x07f 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x080 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x081 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x082 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x083 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x084 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x085 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x086 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x087 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x088 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x089 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0b5 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0b6 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0b7 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0b8 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0b9 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0ba 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0bb 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0bc 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0bd 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0be 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 32  0  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0bf 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 32  0 16 16 16 16  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0c0 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0c1 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0 16 16 16 16  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0c2 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0c3 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0 16 16 16 16  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0c4 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0c5 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0c6 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0c7 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0c8 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0c9 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0ca 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0cb 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0cc 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0cd 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0ce 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0cf 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0d0 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0d1 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0d2 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0d3 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0d4 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0d5 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0d6 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 32  0  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0d7 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 32  0 16 16 16  0  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0d8 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0d9 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0 16 16 16  0  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0da 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0db 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0 16 16 16  0  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0dc  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0dd  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0de  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0df  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0e0  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0e1  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0e2  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0e3  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0e4  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0e5  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0e6  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0e7  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0e8  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0e9  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0ea  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0eb  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0ec  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0ed  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0ee  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 32  0  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0ef  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 32  0 16 16 16  0  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0f0  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 32  0  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0f1  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 32  0 16 16 16  0  0 0 Slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0f2  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 32  0  0  0  0  0  0 0 None[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0x0f3  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 32  0 16 16 16  0  0 0 Slow[/FONT][/COLOR]
```

and finnaly GLX gears
```
[COLOR=#000000][FONT=Arial]764 frames in 5.0 seconds = 152.658 FPS[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]802 frames in 5.0 seconds = 160.245 FPS[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]850 frames in 5.0 seconds = 169.931 FPS[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]851 frames in 5.0 seconds = 170.184 FPS[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]851 frames in 5.0 seconds = 170.016 FPS[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]849 frames in 5.0 seconds = 169.616 FPS[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]846 frames in 5.0 seconds = 169.196 FPS[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]848 frames in 5.0 seconds = 169.538 FPS[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]797 frames in 5.0 seconds = 159.320 FPS[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]845 frames in 5.0 seconds = 168.901 FPS[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]852 frames in 5.0 seconds = 170.260 FPS[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]847 frames in 5.0 seconds = 169.393 FPS[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]776 frames in 5.0 seconds = 155.185 FPS[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]797 frames in 5.0 seconds = 159.258 FPS[/FONT][/COLOR]
```

now the game i am trying to play is minetest latest stable which is 0.4.9 i believe. KDE effects are turned off and desktop performance is rather snappy. So no issue there. desktop is at 240 MB RAM used when idling. there seems to be enough RAM.


however this game is performing poorly (lag). here is what i am getting when i run the game in htop (screenshot is messy but you get the picture):
[https://drive.google.com/file/d/0B2uTW36AgbQzUXZOVmxtbW9hSnM/edit?usp=sharing](https://drive.google.com/file/d/0B2uTW36AgbQzUXZOVmxtbW9hSnM/edit?usp=sharing)

The CPU is maxed out! i tried turning off various 3D stuff, particles, shaders etc. and still the CPU get's maxed out. 

Now i know this isn't a stellar card for today's games, but i played minetest on a much worse intel chip and it had reasonable performance there. and this card sued to run many older games nicely including morrowind on this same mashcine (bu tofcourse underXP).

so any ideas how to improve performance? would it help if i used newer opensource drivers? was there actually any work done in those for these old cards? to me it seems that CPU is doing all the computing here. and i don't care if the graphics get a bit worse as long as game is playable.

---

### Post by Yellow Pasque on 2014-04-05
Something is wrong. 3D hardware acceleration is not working (the CPU is doing everything as you noted).
```
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 0x300)
OpenGL version string: 2.1 Mesa 8.0.4
```

Post /var/log/Xorg.0.log

---

### Post by mastablasta on 2014-04-06
here we go /var/log/Xorg.0.log
```
[    17.910] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    17.910] X Protocol Version 11, Revision 0
[    17.910] Build Operating System: Linux 2.6.42-37-generic i686 Ubuntu
[    17.910] Current Operating System: Linux gorjan-desktop 3.2.0-60-generic-pae #91-Ubuntu SMP Wed Feb 19 04:14:56 UTC 2014 i686
[    17.910] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-60-generic-pae root=UUID=27b03c18-4ac3-47df-a376-8d26c77b7788 ro quiet splash vt.handoff=7
[    17.910] Build Date: 16 October 2013  04:45:22PM
[    17.910] xorg-server 2:1.11.4-0ubuntu10.14 (For technical support please see http://www.ubuntu.com/support) 
[    17.910] Current version of pixman: 0.30.2
[    17.910]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    17.910] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    17.910] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Apr  5 22:26:19 2014
[    17.949] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    17.965] (==) No Layout section.  Using the first Screen section.
[    17.965] (==) No screen section available. Using defaults.
[    17.965] (**) |-->Screen "Default Screen Section" (0)
[    17.965] (**) |   |-->Monitor "<default monitor>"
[    17.978] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    17.979] (==) Automatically adding devices
[    17.979] (==) Automatically enabling devices
[    18.004] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    18.004]     Entry deleted from font path.
[    18.004] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    18.004]     Entry deleted from font path.
[    18.004] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    18.004]     Entry deleted from font path.
[    18.004] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    18.004]     Entry deleted from font path.
[    18.004] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    18.004]     Entry deleted from font path.
[    18.004] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    18.004]     Entry deleted from font path.
[    18.004] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    18.004] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    18.004] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    18.011] (II) Loader magic: 0xb77245a0
[    18.011] (II) Module ABI versions:
[    18.011]     X.Org ANSI C Emulation: 0.4
[    18.011]     X.Org Video Driver: 11.0
[    18.011]     X.Org XInput driver : 16.0
[    18.011]     X.Org Server Extension : 6.0
[    18.012] (--) PCI:*(0:1:0:0) 1002:5961:174b:7c13 rev 1, Mem @ 0xe8000000/134217728, 0xfe9f0000/65536, I/O @ 0x0000b000/256, BIOS @ 0x????????/131072
[    18.012] (--) PCI: (0:1:0:1) 1002:5941:174b:7c12 rev 1, Mem @ 0xe0000000/134217728, 0xfe9e0000/65536
[    18.012] (II) Open ACPI successful (/var/run/acpid.socket)
[    18.012] (II) LoadModule: "extmod"
[    18.213] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    18.360] (II) Module extmod: vendor="X.Org Foundation"
[    18.360]     compiled for 1.11.3, module version = 1.0.0
[    18.360]     Module class: X.Org Server Extension
[    18.360]     ABI class: X.Org Server Extension, version 6.0
[    18.360] (II) Loading extension MIT-SCREEN-SAVER
[    18.360] (II) Loading extension XFree86-VidModeExtension
[    18.360] (II) Loading extension XFree86-DGA
[    18.360] (II) Loading extension DPMS
[    18.360] (II) Loading extension XVideo
[    18.360] (II) Loading extension XVideo-MotionCompensation
[    18.360] (II) Loading extension X-Resource
[    18.360] (II) LoadModule: "dbe"
[    18.361] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    18.372] (II) Module dbe: vendor="X.Org Foundation"
[    18.372]     compiled for 1.11.3, module version = 1.0.0
[    18.372]     Module class: X.Org Server Extension
[    18.372]     ABI class: X.Org Server Extension, version 6.0
[    18.372] (II) Loading extension DOUBLE-BUFFER
[    18.372] (II) LoadModule: "glx"
[    18.373] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    18.402] (II) Module glx: vendor="X.Org Foundation"
[    18.402]     compiled for 1.11.3, module version = 1.0.0
[    18.402]     ABI class: X.Org Server Extension, version 6.0
[    18.402] (==) AIGLX enabled
[    18.402] (II) Loading extension GLX
[    18.402] (II) LoadModule: "record"
[    18.402] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    18.403] (II) Module record: vendor="X.Org Foundation"
[    18.403]     compiled for 1.11.3, module version = 1.13.0
[    18.403]     Module class: X.Org Server Extension
[    18.403]     ABI class: X.Org Server Extension, version 6.0
[    18.403] (II) Loading extension RECORD
[    18.403] (II) LoadModule: "dri"
[    18.403] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    18.744] (II) Module dri: vendor="X.Org Foundation"
[    18.744]     compiled for 1.11.3, module version = 1.0.0
[    18.744]     ABI class: X.Org Server Extension, version 6.0
[    18.744] (II) Loading extension XFree86-DRI
[    18.744] (II) LoadModule: "dri2"
[    18.744] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    18.751] (II) Module dri2: vendor="X.Org Foundation"
[    18.751]     compiled for 1.11.3, module version = 1.2.0
[    18.751]     ABI class: X.Org Server Extension, version 6.0
[    18.751] (II) Loading extension DRI2
[    18.751] (==) Matched fglrx as autoconfigured driver 0
[    18.751] (==) Matched ati as autoconfigured driver 1
[    18.751] (==) Matched vesa as autoconfigured driver 2
[    18.751] (==) Matched fbdev as autoconfigured driver 3
[    18.751] (==) Assigned the driver to the xf86ConfigLayout
[    18.751] (II) LoadModule: "fglrx"
[    18.767] (WW) Warning, couldn't open module fglrx
[    18.767] (II) UnloadModule: "fglrx"
[    18.767] (II) Unloading fglrx
[    18.767] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    18.767] (II) LoadModule: "ati"
[    18.767] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    18.775] (II) Module ati: vendor="X.Org Foundation"
[    18.775]     compiled for 1.11.3, module version = 6.14.99
[    18.775]     Module class: X.Org Video Driver
[    18.775]     ABI class: X.Org Video Driver, version 11.0
[    18.796] (II) LoadModule: "radeon"
[    18.796] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    18.915] (II) Module radeon: vendor="X.Org Foundation"
[    18.915]     compiled for 1.11.3, module version = 6.14.99
[    18.915]     Module class: X.Org Video Driver
[    18.915]     ABI class: X.Org Video Driver, version 11.0
[    18.935] (II) LoadModule: "vesa"
[    18.935] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    18.991] (II) Module vesa: vendor="X.Org Foundation"
[    18.991]     compiled for 1.11.3, module version = 2.3.0
[    18.991]     Module class: X.Org Video Driver
[    18.991]     ABI class: X.Org Video Driver, version 11.0
[    18.991] (II) LoadModule: "fbdev"
[    18.992] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    19.021] (II) Module fbdev: vendor="X.Org Foundation"
[    19.021]     compiled for 1.11.3, module version = 0.4.2
[    19.021]     ABI class: X.Org Video Driver, version 11.0
[    19.021] (==) Matched fglrx as autoconfigured driver 0
[    19.021] (==) Matched ati as autoconfigured driver 1
[    19.021] (==) Matched vesa as autoconfigured driver 2
[    19.021] (==) Matched fbdev as autoconfigured driver 3
[    19.021] (==) Assigned the driver to the xf86ConfigLayout
[    19.021] (II) LoadModule: "fglrx"
[    19.021] (WW) Warning, couldn't open module fglrx
[    19.021] (II) UnloadModule: "fglrx"
[    19.021] (II) Unloading fglrx
[    19.021] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    19.021] (II) LoadModule: "ati"
[    19.022] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    19.022] (II) Module ati: vendor="X.Org Foundation"
[    19.022]     compiled for 1.11.3, module version = 6.14.99
[    19.022]     Module class: X.Org Video Driver
[    19.022]     ABI class: X.Org Video Driver, version 11.0
[    19.022] (II) LoadModule: "vesa"
[    19.022] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    19.022] (II) Module vesa: vendor="X.Org Foundation"
[    19.022]     compiled for 1.11.3, module version = 2.3.0
[    19.022]     Module class: X.Org Video Driver
[    19.022]     ABI class: X.Org Video Driver, version 11.0
[    19.022] (II) UnloadModule: "vesa"
[    19.022] (II) Unloading vesa
[    19.022] (II) Failed to load module "vesa" (already loaded, 0)
[    19.022] (II) LoadModule: "fbdev"
[    19.022] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    19.023] (II) Module fbdev: vendor="X.Org Foundation"
[    19.023]     compiled for 1.11.3, module version = 0.4.2
[    19.023]     ABI class: X.Org Video Driver, version 11.0
[    19.023] (II) UnloadModule: "fbdev"
[    19.023] (II) Unloading fbdev
[    19.023] (II) Failed to load module "fbdev" (already loaded, 0)
[    19.023] (II) RADEON: Driver for ATI Radeon chipsets:
    ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
    ATI Radeon Mobility X300 (M24) 3152 (PCIE),
    ATI FireGL M24 GL 3154 (PCIE), ATI FireMV 2400 3155 (PCI),
    ATI Radeon X600 (RV380) 3E50 (PCIE),
    ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
    ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
    ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
    ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
    ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
    ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
    ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
    ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
    ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
    ATI Radeon 8500 AIW BB (AGP), ATI Radeon IGP320M (U1) 4336,
    ATI Radeon IGP330M/340M/350M (U2) 4337,
    ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
    ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
    ATI Radeon X800PRO (R420) JI (AGP),
    ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
    ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
    ATI Radeon Mobility 9800 (M18) JN (AGP),
    ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
    ATI Radeon X800 VE (R420) JT (AGP), ATI Radeon X850 (R480) (AGP),
    ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
    ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
    ATI Radeon Mobility M7 LW (AGP),
    ATI Mobility FireGL 7800 M7 LX (AGP),
    ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
    ATI FireGL Mobility 9000 (M9) Ld (AGP),
    ATI Radeon Mobility 9000 (M9) Lf (AGP),
    ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI FireMV 2400 PCI,
    ATI Radeon 9700 Pro ND (AGP), ATI Radeon 9700/9500Pro NE (AGP),
    ATI Radeon 9600TX NF (AGP), ATI FireGL X1 NG (AGP),
    ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
    ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
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
    ATI Radeon 4800 Series, ATI Radeon HD 4850 x2,
    ATI FirePro V8750 (FireGL), ATI FirePro V7760 (FireGL),
    ATI Mobility RADEON HD 4850, ATI Mobility RADEON HD 4850 X2,
    ATI Radeon 4800 Series, ATI FirePro RV770, AMD FireStream 9270,
    AMD FireStream 9250, ATI FirePro V8700 (FireGL),
    ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
    ATI Mobility RADEON HD 4870, ATI Radeon 4800 Series,
    ATI Radeon 4800 Series, ATI FirePro M7750, ATI M98, ATI M98, ATI M98,
    ATI Mobility Radeon HD 4650, ATI Radeon RV730 (AGP),
    ATI Mobility Radeon HD 4670, ATI FirePro M5750,
    ATI Mobility Radeon HD 4670, ATI Radeon RV730 (AGP),
    ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
    ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
    ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
    ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
    ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
    ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI Radeon HD 4770,
    ATI FirePro M5750, ATI RV610, ATI Radeon HD 2400 XT,
    ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
    ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
    ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
    ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
    ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
    ATI Mobility Radeon HD 3850 X2, ATI RV670,
    ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
    ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
    ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
    ATI Radeon RV710, ATI Radeon RV710, ATI Radeon RV710,
    ATI Radeon HD 4350, ATI Mobility Radeon 4300 Series,
    ATI Mobility Radeon 4500 Series, ATI Mobility Radeon 4500 Series,
    ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
    ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
    ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
    ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
    ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
    ATI FireGL V3600, ATI Radeon HD 2600 LE,
    ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
    ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
    ATI Radeon HD 3450, ATI Radeon HD 3450, ATI Radeon HD 3430,
    ATI Radeon HD 3450, ATI FirePro V3700, ATI FireMV 2450,
    ATI FireMV 2260, ATI FireMV 2260, ATI Radeon HD 3600 Series,
    ATI Radeon HD 3650 AGP, ATI Radeon HD 3600 PRO,
    ATI Radeon HD 3600 XT, ATI Radeon HD 3600 PRO,
    ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
    ATI Mobility FireGL V5700, ATI Mobility FireGL V5725,
    ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
    ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
    ATI Radeon HD 3300 Graphics, ATI Radeon HD 3200 Graphics,
    ATI Radeon 3000 Graphics, SUMO, SUMO, SUMO2, SUMO2, SUMO2, SUMO2,
    SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, ATI Radeon HD 4200,
    ATI Radeon 4100, ATI Mobility Radeon HD 4200,
    ATI Mobility Radeon 4100, ATI Radeon HD 4290, ATI Radeon HD 4250,
    AMD Radeon HD 6310 Graphics, AMD Radeon HD 6310 Graphics,
    AMD Radeon HD 6250 Graphics, AMD Radeon HD 6250 Graphics,
    AMD Radeon HD 6300 Series Graphics,
    AMD Radeon HD 6200 Series Graphics, PALM, PALM, CYPRESS,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, AMD Firestream 9370,
    AMD Firestream 9350, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5800 Series, ATI Radeon HD 5900 Series,
    ATI Radeon HD 5900 Series, ATI Mobility Radeon HD 5800 Series,
    ATI Mobility Radeon HD 5800 Series,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
    ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
    ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
    ATI Mobility Radeon HD 5000 Series,
    ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5670,
    ATI Radeon HD 5570, ATI Radeon HD 5500 Series, REDWOOD,
    ATI Mobility Radeon HD 5000 Series,
    ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon Graphics,
    ATI Mobility Radeon Graphics, CEDAR,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, ATI FirePro 2270, CEDAR,
    ATI Radeon HD 5450, CEDAR, CEDAR, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
    CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
    AMD Radeon HD 6900 Series, AMD Radeon HD 6900 Series, CAYMAN, CAYMAN,
    CAYMAN, AMD Radeon HD 6900M Series, Mobility Radeon HD 6000 Series,
    BARTS, BARTS, Mobility Radeon HD 6000 Series,
    Mobility Radeon HD 6000 Series, BARTS, BARTS, BARTS, BARTS,
    AMD Radeon HD 6800 Series, AMD Radeon HD 6800 Series,
    AMD Radeon HD 6700 Series, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
    CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS
[    19.027] (II) VESA: driver for VESA chipsets: vesa
[    19.027] (II) FBDEV: driver for framebuffer: fbdev
[    19.027] (++) using VT number 7

[    19.027] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    19.027] (II) [KMS] drm report modesetting isn't supported.
[    19.027] (WW) Falling back to old probe method for vesa
[    19.027] (WW) Falling back to old probe method for fbdev
[    19.027] (II) Loading sub module "fbdevhw"
[    19.027] (II) LoadModule: "fbdevhw"
[    19.027] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    19.172] (II) Module fbdevhw: vendor="X.Org Foundation"
[    19.172]     compiled for 1.11.3, module version = 0.0.2
[    19.172]     ABI class: X.Org Video Driver, version 11.0
[    19.172] (II) RADEON(0): TOTO SAYS 00000000fe9f0000
[    19.172] (II) RADEON(0): MMIO registers at 0x00000000fe9f0000: size 64KB
[    19.172] (II) RADEON(0): PCI bus 1 card 0 func 0
[    19.172] (II) RADEON(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    19.172] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    19.172] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    19.172] (==) RADEON(0): Default visual is TrueColor
[    19.172] (II) Loading sub module "vgahw"
[    19.172] (II) LoadModule: "vgahw"
[    19.173] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    19.222] (II) Module vgahw: vendor="X.Org Foundation"
[    19.222]     compiled for 1.11.3, module version = 0.1.0
[    19.222]     ABI class: X.Org Video Driver, version 11.0
[    19.222] (II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
[    19.222] (==) RADEON(0): RGB weight 888
[    19.222] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    19.222] (--) RADEON(0): Chipset: "ATI Radeon 9200 5961 (AGP)" (ChipID = 0x5961)
[    19.222] (--) RADEON(0): Linear framebuffer at 0x00000000e8000000
[    19.222] (II) RADEON(0): AGP card detected
[    19.222] (II) Loading sub module "int10"
[    19.222] (II) LoadModule: "int10"
[    19.222] (II) Loading /usr/lib/xorg/modules/libint10.so
[    19.282] (II) Module int10: vendor="X.Org Foundation"
[    19.282]     compiled for 1.11.3, module version = 1.0.0
[    19.282]     ABI class: X.Org Video Driver, version 11.0
[    19.282] (II) RADEON(0): initializing int10
[    19.296] (II) RADEON(0): Primary V_BIOS segment is: 0xc000
[    19.298] (II) RADEON(0): Legacy BIOS detected
[    19.356] drmOpenDevice: node name is /dev/dri/card0
[    19.905] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[    19.905] drmOpenDevice: node name is /dev/dri/card0
[    19.909] drmOpenByBusid: drmOpenMinor returns -1
[    19.909] drmOpenDevice: node name is /dev/dri/card1
[    19.914] drmOpenByBusid: drmOpenMinor returns -1
[    19.914] drmOpenDevice: node name is /dev/dri/card2
[    19.918] drmOpenByBusid: drmOpenMinor returns -1
[    19.918] drmOpenDevice: node name is /dev/dri/card3
[    19.922] drmOpenByBusid: drmOpenMinor returns -1
[    19.922] drmOpenDevice: node name is /dev/dri/card4
[    19.926] drmOpenByBusid: drmOpenMinor returns -1
[    19.926] drmOpenDevice: node name is /dev/dri/card5
[    19.930] drmOpenByBusid: drmOpenMinor returns -1
[    19.930] drmOpenDevice: node name is /dev/dri/card6
[    19.934] drmOpenByBusid: drmOpenMinor returns -1
[    19.934] drmOpenDevice: node name is /dev/dri/card7
[    19.939] drmOpenByBusid: drmOpenMinor returns -1
[    19.939] drmOpenDevice: node name is /dev/dri/card8
[    19.943] drmOpenByBusid: drmOpenMinor returns -1
[    19.943] drmOpenDevice: node name is /dev/dri/card9
[    19.947] drmOpenByBusid: drmOpenMinor returns -1
[    19.947] drmOpenDevice: node name is /dev/dri/card10
[    19.952] drmOpenByBusid: drmOpenMinor returns -1
[    19.952] drmOpenDevice: node name is /dev/dri/card11
[    19.959] drmOpenByBusid: drmOpenMinor returns -1
[    19.959] drmOpenDevice: node name is /dev/dri/card12
[    19.973] drmOpenByBusid: drmOpenMinor returns -1
[    19.973] drmOpenDevice: node name is /dev/dri/card13
[    19.978] drmOpenByBusid: drmOpenMinor returns -1
[    19.978] drmOpenDevice: node name is /dev/dri/card14
[    19.982] drmOpenByBusid: drmOpenMinor returns -1
[    19.982] drmOpenDevice: node name is /dev/dri/card15
[    19.988] drmOpenByBusid: drmOpenMinor returns -1
[    19.988] drmOpenDevice: node name is /dev/dri/card0
[    19.995] drmOpenDevice: node name is /dev/dri/card0
[    19.999] drmOpenDevice: node name is /dev/dri/card1
[    20.003] drmOpenDevice: node name is /dev/dri/card2
[    20.007] drmOpenDevice: node name is /dev/dri/card3
[    20.012] drmOpenDevice: node name is /dev/dri/card4
[    20.017] drmOpenDevice: node name is /dev/dri/card5
[    20.021] drmOpenDevice: node name is /dev/dri/card6
[    20.025] drmOpenDevice: node name is /dev/dri/card7
[    20.030] drmOpenDevice: node name is /dev/dri/card8
[    20.034] drmOpenDevice: node name is /dev/dri/card9
[    20.040] drmOpenDevice: node name is /dev/dri/card10
[    20.046] drmOpenDevice: node name is /dev/dri/card11
[    20.053] drmOpenDevice: node name is /dev/dri/card12
[    20.057] drmOpenDevice: node name is /dev/dri/card13
[    20.061] drmOpenDevice: node name is /dev/dri/card14
[    20.065] drmOpenDevice: node name is /dev/dri/card15
[    20.070] (EE) RADEON(0): [dri] RADEONDRIGetVersion failed to open the DRM
[dri] Disabling DRI.
[    20.070] (II) RADEON(0): Generation 2 PCI interface, using max accessible memory
[    20.070] (II) RADEON(0): Detected total video RAM=131072K, accessible=131072K (PCI BAR=131072K)
[    20.070] (--) RADEON(0): Mapped VideoRAM: 131072 kByte (128 bit DDR SDRAM)
[    20.070] (II) RADEON(0): Color tiling enabled by default
[    20.070] (II) Loading sub module "ddc"
[    20.070] (II) LoadModule: "ddc"
[    20.070] (II) Module "ddc" already built-in
[    20.070] (II) Loading sub module "i2c"
[    20.070] (II) LoadModule: "i2c"
[    20.070] (II) Module "i2c" already built-in
[    20.070] (II) RADEON(0): ref_freq: 2700, min_out_pll: 20000, max_out_pll: 40000, min_in_pll: 40, max_in_pll: 3000, xclk: 20000, sclk: 250.000000, mclk: 200.000000
[    20.070] (II) RADEON(0): PLL parameters: rf=2700 rd=12 min=20000 max=40000; xclk=20000
[    20.070] (II) RADEON(0): DFP table revision: 4
[    20.070] (II) RADEON(0): Output VGA-0 has no monitor section
[    20.070] (II) RADEON(0): I2C bus "VGA-0" initialized.
[    20.070] (II) RADEON(0): Output DVI-0 has no monitor section
[    20.070] (II) RADEON(0): I2C bus "DVI-0" initialized.
[    20.070] (II) RADEON(0): Output S-video has no monitor section
[    20.070] (II) RADEON(0): Default TV standard: PAL
[    20.070] (II) RADEON(0): TV standards supported by chip: NTSC PAL 
[    20.070] (II) RADEON(0): Port0:
[    20.070]   XRANDR name: VGA-0
[    20.070]   Connector: VGA
[    20.070]   CRT1: INTERNAL_DAC1
[    20.070]   DDC reg: 0x60
[    20.070] (II) RADEON(0): Port1:
[    20.070]   XRANDR name: DVI-0
[    20.070]   Connector: DVI-I
[    20.070]   CRT2: INTERNAL_DAC2
[    20.070]   DFP1: INTERNAL_TMDS1
[    20.070]   DDC reg: 0x64
[    20.070] (II) RADEON(0): Port2:
[    20.070]   XRANDR name: S-video
[    20.070]   Connector: S-video
[    20.070]   TV1: INTERNAL_DAC2
[    20.070]   DDC reg: 0x0
[    20.070] (II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
[    20.192] (II) RADEON(0): EDID for output VGA-0
[    20.192] (II) RADEON(0): Manufacturer: GSM  Model: 4357  Serial#: 39261
[    20.192] (II) RADEON(0): Year: 2003  Week: 8
[    20.192] (II) RADEON(0): EDID Version: 1.3
[    20.192] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[    20.192] (II) RADEON(0): Sync:  Separate
[    20.192] (II) RADEON(0): Max Image Size [cm]: horiz.: 34  vert.: 27
[    20.192] (II) RADEON(0): Gamma: 2.50
[    20.192] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    20.192] (II) RADEON(0): First detailed timing is preferred mode
[    20.192] (II) RADEON(0): redX: 0.640 redY: 0.340   greenX: 0.290 greenY: 0.610
[    20.192] (II) RADEON(0): blueX: 0.140 blueY: 0.070   whiteX: 0.310 whiteY: 0.330
[    20.192] (II) RADEON(0): Supported established timings:
[    20.192] (II) RADEON(0): 720x400@70Hz
[    20.192] (II) RADEON(0): 640x480@60Hz
[    20.192] (II) RADEON(0): 640x480@75Hz
[    20.192] (II) RADEON(0): 800x600@60Hz
[    20.192] (II) RADEON(0): 800x600@75Hz
[    20.192] (II) RADEON(0): 832x624@75Hz
[    20.192] (II) RADEON(0): 1024x768@60Hz
[    20.192] (II) RADEON(0): 1024x768@75Hz
[    20.192] (II) RADEON(0): 1280x1024@75Hz
[    20.192] (II) RADEON(0): 1152x864@75Hz
[    20.192] (II) RADEON(0): Manufacturer's mask: 0
[    20.192] (II) RADEON(0): Supported standard timings:
[    20.192] (II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    20.192] (II) RADEON(0): #1: hsize: 1024  vsize 768  refresh: 75  vid: 20321
[    20.192] (II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 75  vid: 20293
[    20.192] (II) RADEON(0): #3: hsize: 640  vsize 480  refresh: 75  vid: 20273
[    20.192] (II) RADEON(0): Supported detailed timing:
[    20.192] (II) RADEON(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
[    20.192] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
[    20.192] (II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[    20.192] (II) RADEON(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 145 MHz
[    20.192] (II) RADEON(0): Monitor name: L1710S
[    20.192] (II) RADEON(0): Monitor name: 
[    20.192] (II) RADEON(0): EDID (in hex):
[    20.192] (II) RADEON(0):     00ffffffffffff001e6d57435d990000
[    20.192] (II) RADEON(0):     080d010368221b96eac5c6a3574a9c23
[    20.192] (II) RADEON(0):     124f54a56b808180614f454f314f0101
[    20.192] (II) RADEON(0):     010101010101302a009851002a403070
[    20.192] (II) RADEON(0):     1300520e1100001e000000fd00384b1e
[    20.192] (II) RADEON(0):     530e000a202020202020000000fc004c
[    20.192] (II) RADEON(0):     31373130530a202020202020000000fc
[    20.192] (II) RADEON(0):     00200a202020202020202020202000a1
[    20.192] (II) RADEON(0): EDID vendor "GSM", prod id 17239
[    20.192] (II) RADEON(0): Using EDID range info for horizontal sync
[    20.192] (II) RADEON(0): Using EDID range info for vertical refresh
[    20.192] (II) RADEON(0): Printing DDC gathered Modelines:
[    20.192] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    20.192] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    20.192] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    20.192] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    20.192] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    20.192] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    20.192] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    20.192] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    20.192] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    20.192] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    20.192] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    20.192] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
[    20.193] (II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
[    20.193] (II) RADEON(0): Manufacturer: GSM  Model: 4357  Serial#: 39261
[    20.193] (II) RADEON(0): Year: 2003  Week: 8
[    20.193] (II) RADEON(0): EDID Version: 1.3
[    20.193] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[    20.193] (II) RADEON(0): Sync:  Separate
[    20.193] (II) RADEON(0): Max Image Size [cm]: horiz.: 34  vert.: 27
[    20.193] (II) RADEON(0): Gamma: 2.50
[    20.193] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    20.193] (II) RADEON(0): First detailed timing is preferred mode
[    20.193] (II) RADEON(0): redX: 0.640 redY: 0.340   greenX: 0.290 greenY: 0.610
[    20.193] (II) RADEON(0): blueX: 0.140 blueY: 0.070   whiteX: 0.310 whiteY: 0.330
[    20.193] (II) RADEON(0): Supported established timings:
[    20.193] (II) RADEON(0): 720x400@70Hz
[    20.193] (II) RADEON(0): 640x480@60Hz
[    20.193] (II) RADEON(0): 640x480@75Hz
[    20.193] (II) RADEON(0): 800x600@60Hz
[    20.193] (II) RADEON(0): 800x600@75Hz
[    20.193] (II) RADEON(0): 832x624@75Hz
[    20.193] (II) RADEON(0): 1024x768@60Hz
[    20.193] (II) RADEON(0): 1024x768@75Hz
[    20.193] (II) RADEON(0): 1280x1024@75Hz
[    20.193] (II) RADEON(0): 1152x864@75Hz
[    20.193] (II) RADEON(0): Manufacturer's mask: 0
[    20.193] (II) RADEON(0): Supported standard timings:
[    20.193] (II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    20.193] (II) RADEON(0): #1: hsize: 1024  vsize 768  refresh: 75  vid: 20321
[    20.193] (II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 75  vid: 20293
[    20.193] (II) RADEON(0): #3: hsize: 640  vsize 480  refresh: 75  vid: 20273
[    20.193] (II) RADEON(0): Supported detailed timing:
[    20.193] (II) RADEON(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
[    20.193] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
[    20.193] (II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[    20.193] (II) RADEON(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 145 MHz
[    20.193] (II) RADEON(0): Monitor name: L1710S
[    20.193] (II) RADEON(0): Monitor name: 
[    20.193] (II) RADEON(0): EDID (in hex):
[    20.193] (II) RADEON(0):     00ffffffffffff001e6d57435d990000
[    20.193] (II) RADEON(0):     080d010368221b96eac5c6a3574a9c23
[    20.193] (II) RADEON(0):     124f54a56b808180614f454f314f0101
[    20.193] (II) RADEON(0):     010101010101302a009851002a403070
[    20.193] (II) RADEON(0):     1300520e1100001e000000fd00384b1e
[    20.193] (II) RADEON(0):     530e000a202020202020000000fc004c
[    20.193] (II) RADEON(0):     31373130530a202020202020000000fc
[    20.196] (II) RADEON(0):     00200a202020202020202020202000a1
[    20.196] finished output detect: 0
[    20.196] (II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
[    20.201] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
[    20.201] Unhandled monitor type 0
[    20.201] finished output detect: 1
[    20.201] (II) RADEON(0): Output: S-video, Detected Monitor Type: 0
[    20.201] finished output detect: 2
[    20.201] finished all detect
[    20.272] (II) RADEON(0): EDID for output VGA-0
[    20.272] (II) RADEON(0): Manufacturer: GSM  Model: 4357  Serial#: 39261
[    20.272] (II) RADEON(0): Year: 2003  Week: 8
[    20.272] (II) RADEON(0): EDID Version: 1.3
[    20.272] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[    20.272] (II) RADEON(0): Sync:  Separate
[    20.272] (II) RADEON(0): Max Image Size [cm]: horiz.: 34  vert.: 27
[    20.272] (II) RADEON(0): Gamma: 2.50
[    20.272] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    20.272] (II) RADEON(0): First detailed timing is preferred mode
[    20.272] (II) RADEON(0): redX: 0.640 redY: 0.340   greenX: 0.290 greenY: 0.610
[    20.272] (II) RADEON(0): blueX: 0.140 blueY: 0.070   whiteX: 0.310 whiteY: 0.330
[    20.272] (II) RADEON(0): Supported established timings:
[    20.272] (II) RADEON(0): 720x400@70Hz
[    20.272] (II) RADEON(0): 640x480@60Hz
[    20.272] (II) RADEON(0): 640x480@75Hz
[    20.272] (II) RADEON(0): 800x600@60Hz
[    20.272] (II) RADEON(0): 800x600@75Hz
[    20.272] (II) RADEON(0): 832x624@75Hz
[    20.272] (II) RADEON(0): 1024x768@60Hz
[    20.272] (II) RADEON(0): 1024x768@75Hz
[    20.272] (II) RADEON(0): 1280x1024@75Hz
[    20.272] (II) RADEON(0): 1152x864@75Hz
[    20.272] (II) RADEON(0): Manufacturer's mask: 0
[    20.272] (II) RADEON(0): Supported standard timings:
[    20.272] (II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    20.272] (II) RADEON(0): #1: hsize: 1024  vsize 768  refresh: 75  vid: 20321
[    20.272] (II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 75  vid: 20293
[    20.272] (II) RADEON(0): #3: hsize: 640  vsize 480  refresh: 75  vid: 20273
[    20.272] (II) RADEON(0): Supported detailed timing:
[    20.272] (II) RADEON(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
[    20.272] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
[    20.272] (II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[    20.272] (II) RADEON(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 145 MHz
[    20.272] (II) RADEON(0): Monitor name: L1710S
[    20.272] (II) RADEON(0): Monitor name: 
[    20.272] (II) RADEON(0): EDID (in hex):
[    20.272] (II) RADEON(0):     00ffffffffffff001e6d57435d990000
[    20.272] (II) RADEON(0):     080d010368221b96eac5c6a3574a9c23
[    20.272] (II) RADEON(0):     124f54a56b808180614f454f314f0101
[    20.272] (II) RADEON(0):     010101010101302a009851002a403070
[    20.272] (II) RADEON(0):     1300520e1100001e000000fd00384b1e
[    20.272] (II) RADEON(0):     530e000a202020202020000000fc004c
[    20.272] (II) RADEON(0):     31373130530a202020202020000000fc
[    20.272] (II) RADEON(0):     00200a202020202020202020202000a1
[    20.272] (II) RADEON(0): EDID vendor "GSM", prod id 17239
[    20.272] (II) RADEON(0): Using hsync ranges from config file
[    20.272] (II) RADEON(0): Using vrefresh ranges from config file
[    20.272] (II) RADEON(0): Printing DDC gathered Modelines:
[    20.272] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    20.272] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    20.272] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    20.272] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    20.272] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    20.272] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    20.272] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    20.272] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    20.272] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    20.272] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    20.272] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    20.272] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
[    20.272] (II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
[    20.273] (II) RADEON(0): Manufacturer: GSM  Model: 4357  Serial#: 39261
[    20.273] (II) RADEON(0): Year: 2003  Week: 8
[    20.273] (II) RADEON(0): EDID Version: 1.3
[    20.273] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[    20.273] (II) RADEON(0): Sync:  Separate
[    20.273] (II) RADEON(0): Max Image Size [cm]: horiz.: 34  vert.: 27
[    20.273] (II) RADEON(0): Gamma: 2.50
[    20.273] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    20.273] (II) RADEON(0): First detailed timing is preferred mode
[    20.273] (II) RADEON(0): redX: 0.640 redY: 0.340   greenX: 0.290 greenY: 0.610
[    20.273] (II) RADEON(0): blueX: 0.140 blueY: 0.070   whiteX: 0.310 whiteY: 0.330
[    20.273] (II) RADEON(0): Supported established timings:
[    20.273] (II) RADEON(0): 720x400@70Hz
[    20.273] (II) RADEON(0): 640x480@60Hz
[    20.273] (II) RADEON(0): 640x480@75Hz
[    20.273] (II) RADEON(0): 800x600@60Hz
[    20.273] (II) RADEON(0): 800x600@75Hz
[    20.273] (II) RADEON(0): 832x624@75Hz
[    20.273] (II) RADEON(0): 1024x768@60Hz
[    20.273] (II) RADEON(0): 1024x768@75Hz
[    20.273] (II) RADEON(0): 1280x1024@75Hz
[    20.273] (II) RADEON(0): 1152x864@75Hz
[    20.273] (II) RADEON(0): Manufacturer's mask: 0
[    20.273] (II) RADEON(0): Supported standard timings:
[    20.273] (II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    20.273] (II) RADEON(0): #1: hsize: 1024  vsize 768  refresh: 75  vid: 20321
[    20.273] (II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 75  vid: 20293
[    20.273] (II) RADEON(0): #3: hsize: 640  vsize 480  refresh: 75  vid: 20273
[    20.273] (II) RADEON(0): Supported detailed timing:
[    20.273] (II) RADEON(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
[    20.273] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
[    20.273] (II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[    20.273] (II) RADEON(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 145 MHz
[    20.273] (II) RADEON(0): Monitor name: L1710S
[    20.273] (II) RADEON(0): Monitor name: 
[    20.273] (II) RADEON(0): EDID (in hex):
[    20.273] (II) RADEON(0):     00ffffffffffff001e6d57435d990000
[    20.273] (II) RADEON(0):     080d010368221b96eac5c6a3574a9c23
[    20.273] (II) RADEON(0):     124f54a56b808180614f454f314f0101
[    20.273] (II) RADEON(0):     010101010101302a009851002a403070
[    20.273] (II) RADEON(0):     1300520e1100001e000000fd00384b1e
[    20.273] (II) RADEON(0):     530e000a202020202020000000fc004c
[    20.273] (II) RADEON(0):     31373130530a202020202020000000fc
[    20.273] (II) RADEON(0):     00200a202020202020202020202000a1
[    20.273] (II) RADEON(0): EDID vendor "GSM", prod id 17239
[    20.273] (II) RADEON(0): Printing probed modes for output VGA-0
[    20.273] (II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    20.273] (II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    20.273] (II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    20.273] (II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    20.273] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    20.273] (II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    20.273] (II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    20.273] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    20.273] (II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    20.273] (II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    20.273] (II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    20.278] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
[    20.278] Unhandled monitor type 0
[    20.278] (II) RADEON(0): EDID for output DVI-0
[    20.278] (II) RADEON(0): Output: S-video, Detected Monitor Type: 0
[    20.278] (II) RADEON(0): EDID for output S-video
[    20.278] (II) RADEON(0): Output VGA-0 connected
[    20.278] (II) RADEON(0): Output DVI-0 disconnected
[    20.278] (II) RADEON(0): Output S-video disconnected
[    20.278] (II) RADEON(0): Using exact sizes for initial modes
[    20.278] (II) RADEON(0): Output VGA-0 using initial mode 1280x1024
[    20.278] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    20.278] (**) RADEON(0): Display dimensions: (340, 270) mm
[    20.278] (**) RADEON(0): DPI set to (95, 120)
[    20.278] (II) Loading sub module "fb"
[    20.278] (II) LoadModule: "fb"
[    20.278] (II) Loading /usr/lib/xorg/modules/libfb.so
[    20.340] (II) Module fb: vendor="X.Org Foundation"
[    20.340]     compiled for 1.11.3, module version = 1.0.0
[    20.340]     ABI class: X.Org ANSI C Emulation, version 0.4
[    20.340] (II) Loading sub module "ramdac"
[    20.340] (II) LoadModule: "ramdac"
[    20.340] (II) Module "ramdac" already built-in
[    20.340] (==) RADEON(0): Using XAA acceleration architecture
[    20.340] (II) Loading sub module "xaa"
[    20.340] (II) LoadModule: "xaa"
[    20.340] (II) Loading /usr/lib/xorg/modules/libxaa.so
[    20.371] (II) Module xaa: vendor="X.Org Foundation"
[    20.371]     compiled for 1.11.3, module version = 1.2.1
[    20.371]     ABI class: X.Org Video Driver, version 11.0
[    20.372] (==) RADEON(0): Assuming overlay scaler buffer width is 1536
[    20.372] (II) RADEON(0): MM_TABLE: 01-0c-00-1f-06-00-00-66-02-00-00-02-00-03
[    20.372] (!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
[    20.372] (II) UnloadModule: "vesa"
[    20.372] (II) Unloading vesa
[    20.372] (II) UnloadModule: "fbdev"
[    20.372] (II) Unloading fbdev
[    20.372] (II) UnloadModule: "fbdevhw"
[    20.372] (II) Unloading fbdevhw
[    20.372] (--) Depth 24 pixmap format is 32 bpp
[    20.372] (II) RADEON(0): RADEONScreenInit e8000000 0 0
[    20.384] Entering TV Save
[    20.384] Save TV timing tables
[    20.384] saveTimingTables: reading timing tables
[    20.633] TV Save done
[    20.633] disable primary dac
[    20.641] (II) RADEON(0): Dynamic Power Management Disabled
[    20.655] (II) RADEON(0): RADEONInitMemoryMap() : 
[    20.655] (II) RADEON(0):   mem_size         : 0x08000000
[    20.655] (II) RADEON(0):   MC_FB_LOCATION   : 0xefffe800
[    20.655] (II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
[    20.655] (II) RADEON(0): Depth moves disabled by default
[    20.655] (II) RADEON(0): Memory manager initialized to (0,0) (1280,8191)
[    20.655] (II) RADEON(0): Reserved area from (0,1280) to (1280,1282)
[    20.655] (II) RADEON(0): Largest offscreen area available: 1280 x 6909
[    20.662] (II) RADEON(0): RADEONRestoreMemMapRegisters() : 
[    20.662] (II) RADEON(0):   MC_FB_LOCATION   : 0xefffe800 0x1fff0000
[    20.662] (II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
[    20.862] (==) RADEON(0): Backing store disabled
[    20.862] (WW) RADEON(0): Direct rendering disabled
[    20.862] (II) RADEON(0): Render acceleration disabled
[    20.862] (II) RADEON(0): Using XFree86 Acceleration Architecture (XAA)
[    20.862]     Screen to screen bit blits
[    20.862]     Solid filled rectangles
[    20.862]     8x8 mono pattern filled rectangles
[    20.862]     Indirect CPU to Screen color expansion
[    20.862]     Solid Lines
[    20.862]     Scanline Image Writes
[    20.862]     Setting up tile and stipple cache:
[    20.862]         32 128x128 slots
[    20.862]         32 256x256 slots
[    20.862]         16 512x512 slots
[    20.862] (II) RADEON(0): Acceleration enabled
[    20.862] (==) RADEON(0): DPMS enabled
[    20.862] (==) RADEON(0): Silken mouse enabled
[    20.863] (II) RADEON(0): Will use 32 kb for hardware cursor 0 at offset 0x00642800
[    20.863] (II) RADEON(0): Will use 32 kb for hardware cursor 1 at offset 0x00647800
[    20.863] (II) RADEON(0): Largest offscreen area available: 1280 x 6901
[    20.863] (II) Loading sub module "i2c"
[    20.863] (II) LoadModule: "i2c"
[    20.863] (II) Module "i2c" already built-in
[    20.863] (II) RADEON(0): Using Radeon bus access method
[    20.863] (II) RADEON(0): I2C bus "Radeon multimedia bus" initialized.
[    20.863] (II) Loading sub module "fi1236"
[    20.863] (II) LoadModule: "fi1236"
[    20.863] (II) Loading /usr/lib/xorg/modules/multimedia/fi1236_drv.so
[    20.870] (II) Module fi1236: vendor="X.Org Foundation"
[    20.870]     compiled for 1.11.3, module version = 1.0.0
[    20.870]     ABI class: X.Org Video Driver, version 11.0
[    20.872] (II) RADEON(0): I2C device "Radeon multimedia bus:FI12xx Tuner" registered at address 0xC6.
[    20.872] (II) RADEON(0): Detected NO TUNER device at 0xc6
[    20.872] (II) Loading sub module "uda1380"
[    20.872] (II) LoadModule: "uda1380"
[    20.872] (II) Loading /usr/lib/xorg/modules/multimedia/uda1380_drv.so
[    20.873] (II) Module uda1380: vendor="X.Org Foundation"
[    20.873]     compiled for 1.11.3, module version = 1.0.0
[    20.873]     ABI class: X.Org Video Driver, version 11.0
[    20.875] (II) RADEON(0): I2C device "Radeon multimedia bus:UDA1380 Stereo audion coder-decoder" registered at address 0x30.
[    20.875] (II) RADEON(0): UDA1380 stereo coder-decoder detected
[    20.879] (II) RADEON(0): UDA1380 initialized
[    20.879] (II) Loading sub module "msp3430"
[    20.879] (II) LoadModule: "msp3430"
[    20.879] (II) Loading /usr/lib/xorg/modules/multimedia/msp3430_drv.so
[    20.880] (II) Module msp3430: vendor="X.Org Foundation"
[    20.880]     compiled for 1.11.3, module version = 1.0.0
[    20.880]     ABI class: X.Org Video Driver, version 11.0
[    20.891] (II) RADEON(0): Found MSP - unknown type (unsupported), rom version 0x00, chip_id=0x0000
[    20.901] (II) RADEON(0): Found MSP - unknown type (unsupported), rom version 0x00, chip_id=0x0000
[    20.901] (II) Loading sub module "theatre_detect"
[    20.901] (II) LoadModule: "theatre_detect"
[    20.902] (II) Loading /usr/lib/xorg/modules/multimedia/theatre_detect_drv.so
[    20.914] (II) Module theatre_detect: vendor="X.Org Foundation"
[    20.914]     compiled for 1.11.3, module version = 1.0.0
[    20.914]     ABI class: X.Org Video Driver, version 11.0
[    20.914] (II) RADEON(0): No response from device 0 on VIP bus
[    20.914] (II) RADEON(0): Device 1 on VIP bus ids as 0x4d541002
[    20.914] (II) RADEON(0): No response from device 2 on VIP bus
[    20.914] (II) RADEON(0): No response from device 3 on VIP bus
[    20.914] (II) RADEON(0): Detected Rage Theatre as device 1 on VIP bus with id 0x4d541002
[    20.914] (II) RADEON(0): Detected Rage Theatre revision 00000003
[    20.914] (II) RADEON(0): video decoder type is 0x4e20 (BIOS value) versus 0x4e20 (current PLL setting)
[    20.914] (II) RADEON(0): Composite connector is port 1
[    20.914] (II) RADEON(0): SVideo connector is port 5
[    20.914] (II) RADEON(0): Rage Theatre: Connectors (detected): tuner=0, composite=1, svideo=5
[    20.914] (II) RADEON(0): RageTheatre: Connectors (using): tuner=0, composite=1, svideo=5
[    20.914] (II) RADEON(0): video decoder type used: 0x0006
[    20.914] (II) RADEON(0): Going to load the corresponding theatre module
[    20.914] (II) Loading sub module "theatre"
[    20.914] (II) LoadModule: "theatre"
[    20.914] (II) Loading /usr/lib/xorg/modules/multimedia/theatre_drv.so
[    20.915] (II) Module theatre: vendor="X.Org Foundation"
[    20.915]     compiled for 1.11.3, module version = 1.0.0
[    20.915]     ABI class: X.Org Video Driver, version 11.0
[    21.116] (II) RADEON(0): Rage Theatre setting standard 0x0000
[    21.161] (II) RADEON(0): Rage Theatre setting standard 0x0000
[    21.366] (II) RADEON(0): Rage Theatre setting standard 0x0000
[    21.370] (II) RADEON(0): Set up overlay video
[    21.370] (II) RADEON(0): Set up textured video
[    21.370] (II) RADEON(0): [XvMC] Associated with Radeon Textured Video.
[    21.370] (II) RADEON(0): [XvMC] Extension initialized.
[    21.402] disable primary dac
[    21.402] disable TV
[    21.402] disable primary dac
[    21.402] init memmap
[    21.402] init common
[    21.402] init crtc1
[    21.402] init pll1
[    21.402] freq: 108000000
[    21.402] best_freq: 108000000
[    21.402] best_feedback_div: 16
[    21.402] best_frac_feedback_div: 0
[    21.402] best_ref_div: 2
[    21.402] best_post_div: 2
[    21.402] restore memmap
[    21.402] (II) RADEON(0): RADEONRestoreMemMapRegisters() : 
[    21.402] (II) RADEON(0):   MC_FB_LOCATION   : 0xefffe800 0xefffe800
[    21.402] (II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
[    21.502] restore common
[    21.602] restore crtc1
[    21.602] restore pll1
[    21.653] finished PLL1
[    21.653] set RMX
[    21.653] set primary dac
[    21.653] enable primary dac
[    21.653] disable TV
[    21.653] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    21.653] (--) RandR disabled
[    21.654] (II) Initializing built-in extension Generic Event Extension
[    21.654] (II) Initializing built-in extension SHAPE
[    21.654] (II) Initializing built-in extension MIT-SHM
[    21.654] (II) Initializing built-in extension XInputExtension
[    21.654] (II) Initializing built-in extension XTEST
[    21.654] (II) Initializing built-in extension BIG-REQUESTS
[    21.654] (II) Initializing built-in extension SYNC
[    21.654] (II) Initializing built-in extension XKEYBOARD
[    21.654] (II) Initializing built-in extension XC-MISC
[    21.654] (II) Initializing built-in extension SECURITY
[    21.654] (II) Initializing built-in extension XINERAMA
[    21.654] (II) Initializing built-in extension XFIXES
[    21.654] (II) Initializing built-in extension RENDER
[    21.654] (II) Initializing built-in extension RANDR
[    21.654] (II) Initializing built-in extension COMPOSITE
[    21.654] (II) Initializing built-in extension DAMAGE
[    21.685] (II) AIGLX: Screen 0 is not DRI2 capable
[    21.685] (II) AIGLX: Screen 0 is not DRI capable
[    22.408] (II) AIGLX: Loaded and initialized swrast
[    22.418] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    22.419] (II) RADEON(0): Setting screen physical size to 338 x 270
[    22.507] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    22.516] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    22.517] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    22.517] (II) LoadModule: "evdev"
[    22.517] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    22.535] (II) Module evdev: vendor="X.Org Foundation"
[    22.535]     compiled for 1.11.3, module version = 2.7.0
[    22.535]     Module class: X.Org XInput Driver
[    22.535]     ABI class: X.Org XInput driver, version 16.0
[    22.535] (II) Using input driver 'evdev' for 'Power Button'
[    22.535] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    22.535] (**) Power Button: always reports core events
[    22.535] (**) evdev: Power Button: Device: "/dev/input/event1"
[    22.535] (--) evdev: Power Button: Vendor 0 Product 0x1
[    22.535] (--) evdev: Power Button: Found keys
[    22.535] (II) evdev: Power Button: Configuring as keyboard
[    22.535] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    22.535] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    22.535] (**) Option "xkb_rules" "evdev"
[    22.535] (**) Option "xkb_model" "pc105"
[    22.535] (**) Option "xkb_layout" "si"
[    22.538] (II) XKB: reuse xkmfile /var/lib/xkb/server-382E998F79C55FE563EE3D1572FEC9D6349EB92C.xkm
[    22.545] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    22.545] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    22.545] (II) Using input driver 'evdev' for 'Power Button'
[    22.545] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    22.545] (**) Power Button: always reports core events
[    22.545] (**) evdev: Power Button: Device: "/dev/input/event0"
[    22.545] (--) evdev: Power Button: Vendor 0 Product 0x1
[    22.545] (--) evdev: Power Button: Found keys
[    22.545] (II) evdev: Power Button: Configuring as keyboard
[    22.545] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    22.545] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    22.545] (**) Option "xkb_rules" "evdev"
[    22.545] (**) Option "xkb_model" "pc105"
[    22.545] (**) Option "xkb_layout" "si"
[    22.546] (II) config/udev: Adding input device UVC Camera (046d:0825) (/dev/input/event3)
[    22.546] (**) UVC Camera (046d:0825): Applying InputClass "evdev keyboard catchall"
[    22.546] (II) Using input driver 'evdev' for 'UVC Camera (046d:0825)'
[    22.546] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    22.546] (**) UVC Camera (046d:0825): always reports core events
[    22.546] (**) evdev: UVC Camera (046d:0825): Device: "/dev/input/event3"
[    22.546] (--) evdev: UVC Camera (046d:0825): Vendor 0x46d Product 0x825
[    22.546] (--) evdev: UVC Camera (046d:0825): Found keys
[    22.546] (II) evdev: UVC Camera (046d:0825): Configuring as keyboard
[    22.546] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.2/usb1/1-7/1-7:1.0/input/input3/event3"
[    22.546] (II) XINPUT: Adding extended input device "UVC Camera (046d:0825)" (type: KEYBOARD, id 8)
[    22.546] (**) Option "xkb_rules" "evdev"
[    22.546] (**) Option "xkb_model" "pc105"
[    22.546] (**) Option "xkb_layout" "si"
[    22.547] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    22.547] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    22.547] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    22.547] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    22.547] (**) AT Translated Set 2 keyboard: always reports core events
[    22.547] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    22.547] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    22.547] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    22.547] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    22.547] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    22.547] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 9)
[    22.547] (**) Option "xkb_rules" "evdev"
[    22.547] (**) Option "xkb_model" "pc105"
[    22.547] (**) Option "xkb_layout" "si"
[    22.548] (II) config/udev: Adding input device ImExPS/2 Logitech Explorer Mouse (/dev/input/event4)
[    22.548] (**) ImExPS/2 Logitech Explorer Mouse: Applying InputClass "evdev pointer catchall"
[    22.548] (II) Using input driver 'evdev' for 'ImExPS/2 Logitech Explorer Mouse'
[    22.548] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    22.548] (**) ImExPS/2 Logitech Explorer Mouse: always reports core events
[    22.548] (**) evdev: ImExPS/2 Logitech Explorer Mouse: Device: "/dev/input/event4"
[    22.548] (--) evdev: ImExPS/2 Logitech Explorer Mouse: Vendor 0x2 Product 0x6
[    22.548] (--) evdev: ImExPS/2 Logitech Explorer Mouse: Found 9 mouse buttons
[    22.548] (--) evdev: ImExPS/2 Logitech Explorer Mouse: Found scroll wheel(s)
[    22.548] (--) evdev: ImExPS/2 Logitech Explorer Mouse: Found relative axes
[    22.548] (--) evdev: ImExPS/2 Logitech Explorer Mouse: Found x and y relative axes
[    22.548] (II) evdev: ImExPS/2 Logitech Explorer Mouse: Configuring as mouse
[    22.548] (II) evdev: ImExPS/2 Logitech Explorer Mouse: Adding scrollwheel support
[    22.548] (**) evdev: ImExPS/2 Logitech Explorer Mouse: YAxisMapping: buttons 4 and 5
[    22.548] (**) evdev: ImExPS/2 Logitech Explorer Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    22.548] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input4/event4"
[    22.548] (II) XINPUT: Adding extended input device "ImExPS/2 Logitech Explorer Mouse" (type: MOUSE, id 10)
[    22.548] (II) evdev: ImExPS/2 Logitech Explorer Mouse: initialized for relative axes.
[    22.548] (**) ImExPS/2 Logitech Explorer Mouse: (accel) keeping acceleration scheme 1
[    22.548] (**) ImExPS/2 Logitech Explorer Mouse: (accel) acceleration profile 0
[    22.548] (**) ImExPS/2 Logitech Explorer Mouse: (accel) acceleration factor: 2.000
[    22.548] (**) ImExPS/2 Logitech Explorer Mouse: (accel) acceleration threshold: 4
[    22.549] (II) config/udev: Adding input device ImExPS/2 Logitech Explorer Mouse (/dev/input/mouse0)
[    22.549] (II) No input driver specified, ignoring this device.
[    22.549] (II) This device may have been added with another device file.
[   622.556] disable primary dac
[   622.556] disable primary dac
[ 20898.878] enable primary dac
[ 20949.914] (II) RADEON(0): EDID vendor "GSM", prod id 17239
[ 20949.914] (II) RADEON(0): Using hsync ranges from config file
[ 20949.914] (II) RADEON(0): Using vrefresh ranges from config file
[ 20949.914] (II) RADEON(0): Printing DDC gathered Modelines:
[ 20949.914] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[ 20949.914] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[ 20949.914] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[ 20949.914] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[ 20949.914] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[ 20949.914] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[ 20949.914] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[ 20949.914] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[ 20949.914] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[ 20949.914] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[ 20949.914] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[ 20949.914] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
[ 20949.914] (II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
[ 20949.914] (II) RADEON(0): Manufacturer: GSM  Model: 4357  Serial#: 39261
[ 20949.914] (II) RADEON(0): Year: 2003  Week: 8
[ 20949.914] (II) RADEON(0): EDID Version: 1.3
[ 20949.914] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[ 20949.914] (II) RADEON(0): Sync:  Separate
[ 20949.914] (II) RADEON(0): Max Image Size [cm]: horiz.: 34  vert.: 27
[ 20949.914] (II) RADEON(0): Gamma: 2.50
[ 20949.914] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[ 20949.914] (II) RADEON(0): First detailed timing is preferred mode
[ 20949.915] (II) RADEON(0): redX: 0.640 redY: 0.340   greenX: 0.290 greenY: 0.610
[ 20949.915] (II) RADEON(0): blueX: 0.140 blueY: 0.070   whiteX: 0.310 whiteY: 0.330
[ 20949.915] (II) RADEON(0): Supported established timings:
[ 20949.915] (II) RADEON(0): 720x400@70Hz
[ 20949.915] (II) RADEON(0): 640x480@60Hz
[ 20949.915] (II) RADEON(0): 640x480@75Hz
[ 20949.915] (II) RADEON(0): 800x600@60Hz
[ 20949.920] (II) RADEON(0): 800x600@75Hz
[ 20949.920] (II) RADEON(0): 832x624@75Hz
[ 20949.920] (II) RADEON(0): 1024x768@60Hz
[ 20949.920] (II) RADEON(0): 1024x768@75Hz
[ 20949.920] (II) RADEON(0): 1280x1024@75Hz
[ 20949.920] (II) RADEON(0): 1152x864@75Hz
[ 20949.920] (II) RADEON(0): Manufacturer's mask: 0
[ 20949.920] (II) RADEON(0): Supported standard timings:
[ 20949.920] (II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[ 20949.920] (II) RADEON(0): #1: hsize: 1024  vsize 768  refresh: 75  vid: 20321
[ 20949.920] (II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 75  vid: 20293
[ 20949.920] (II) RADEON(0): #3: hsize: 640  vsize 480  refresh: 75  vid: 20273
[ 20949.920] (II) RADEON(0): Supported detailed timing:
[ 20949.920] (II) RADEON(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
[ 20949.920] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
[ 20949.920] (II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[ 20949.920] (II) RADEON(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 145 MHz
[ 20949.920] (II) RADEON(0): Monitor name: L1710S
[ 20949.920] (II) RADEON(0): Monitor name: 
[ 20949.920] (II) RADEON(0): EDID (in hex):
[ 20949.920] (II) RADEON(0):     00ffffffffffff001e6d57435d990000
[ 20949.920] (II) RADEON(0):     080d010368221b96eac5c6a3574a9c23
[ 20949.920] (II) RADEON(0):     124f54a56b808180614f454f314f0101
[ 20949.920] (II) RADEON(0):     010101010101302a009851002a403070
[ 20949.920] (II) RADEON(0):     1300520e1100001e000000fd00384b1e
[ 20949.920] (II) RADEON(0):     530e000a202020202020000000fc004c
[ 20949.920] (II) RADEON(0):     31373130530a202020202020000000fc
[ 20949.920] (II) RADEON(0):     00200a202020202020202020202000a1
[ 20949.920] (II) RADEON(0): EDID vendor "GSM", prod id 17239
[ 20949.930] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
[ 20949.930] Unhandled monitor type 0
[ 20949.930] (II) RADEON(0): Output: S-video, Detected Monitor Type: 0
[ 32287.300] disable primary dac
[ 32287.300] disable primary dac
[ 32587.301] enable primary dac
[ 32587.301] disable primary dac
[ 32887.300] enable primary dac
[ 32887.300] disable primary dac
[ 33552.795] enable primary dac
[ 38423.091] disable primary dac
[ 38423.091] disable primary dac
[ 38723.091] enable primary dac
[ 38723.092] disable primary dac
[ 39023.092] enable primary dac
[ 39023.092] disable primary dac
[ 42260.991] enable primary dac
[ 42279.529] (II) XKB: reuse xkmfile /var/lib/xkb/server-09C19198E9A4289EFEE844E2AABA985A41656D18.xkm


```

and the old one:
```
[    27.526] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    27.526] X Protocol Version 11, Revision 0
[    27.526] Build Operating System: Linux 2.6.42-37-generic i686 Ubuntu
[    27.526] Current Operating System: Linux gorjan-desktop 3.2.0-60-generic-pae #91-Ubuntu SMP Wed Feb 19 04:14:56 UTC 2014 i686
[    27.526] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-60-generic-pae root=UUID=27b03c18-4ac3-47df-a376-8d26c77b7788 ro quiet splash vt.handoff=7
[    27.526] Build Date: 16 October 2013  04:45:22PM
[    27.526] xorg-server 2:1.11.4-0ubuntu10.14 (For technical support please see http://www.ubuntu.com/support) 
[    27.526] Current version of pixman: 0.30.2
[    27.526]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    27.526] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    27.526] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Apr  5 09:48:41 2014
[    27.539] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    27.539] (==) No Layout section.  Using the first Screen section.
[    27.539] (==) No screen section available. Using defaults.
[    27.539] (**) |-->Screen "Default Screen Section" (0)
[    27.539] (**) |   |-->Monitor "<default monitor>"
[    27.540] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    27.540] (==) Automatically adding devices
[    27.540] (==) Automatically enabling devices
[    27.540] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    27.540]     Entry deleted from font path.
[    27.540] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    27.540]     Entry deleted from font path.
[    27.540] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    27.540]     Entry deleted from font path.
[    27.540] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    27.540]     Entry deleted from font path.
[    27.540] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    27.540]     Entry deleted from font path.
[    27.540] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    27.540]     Entry deleted from font path.
[    27.540] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    27.540] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    27.540] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    27.540] (II) Loader magic: 0xb78025a0
[    27.540] (II) Module ABI versions:
[    27.540]     X.Org ANSI C Emulation: 0.4
[    27.540]     X.Org Video Driver: 11.0
[    27.540]     X.Org XInput driver : 16.0
[    27.540]     X.Org Server Extension : 6.0
[    27.541] (--) PCI:*(0:1:0:0) 1002:5961:174b:7c13 rev 1, Mem @ 0xe8000000/134217728, 0xfe9f0000/65536, I/O @ 0x0000b000/256, BIOS @ 0x????????/131072
[    27.541] (--) PCI: (0:1:0:1) 1002:5941:174b:7c12 rev 1, Mem @ 0xe0000000/134217728, 0xfe9e0000/65536
[    27.541] (II) Open ACPI successful (/var/run/acpid.socket)
[    27.541] (II) LoadModule: "extmod"
[    27.554] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    27.554] (II) Module extmod: vendor="X.Org Foundation"
[    27.554]     compiled for 1.11.3, module version = 1.0.0
[    27.554]     Module class: X.Org Server Extension
[    27.554]     ABI class: X.Org Server Extension, version 6.0
[    27.554] (II) Loading extension MIT-SCREEN-SAVER
[    27.554] (II) Loading extension XFree86-VidModeExtension
[    27.554] (II) Loading extension XFree86-DGA
[    27.554] (II) Loading extension DPMS
[    27.555] (II) Loading extension XVideo
[    27.555] (II) Loading extension XVideo-MotionCompensation
[    27.555] (II) Loading extension X-Resource
[    27.555] (II) LoadModule: "dbe"
[    27.555] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    27.555] (II) Module dbe: vendor="X.Org Foundation"
[    27.555]     compiled for 1.11.3, module version = 1.0.0
[    27.555]     Module class: X.Org Server Extension
[    27.555]     ABI class: X.Org Server Extension, version 6.0
[    27.555] (II) Loading extension DOUBLE-BUFFER
[    27.555] (II) LoadModule: "glx"
[    27.555] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    27.555] (II) Module glx: vendor="X.Org Foundation"
[    27.555]     compiled for 1.11.3, module version = 1.0.0
[    27.555]     ABI class: X.Org Server Extension, version 6.0
[    27.555] (==) AIGLX enabled
[    27.555] (II) Loading extension GLX
[    27.555] (II) LoadModule: "record"
[    27.555] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    27.555] (II) Module record: vendor="X.Org Foundation"
[    27.555]     compiled for 1.11.3, module version = 1.13.0
[    27.555]     Module class: X.Org Server Extension
[    27.555]     ABI class: X.Org Server Extension, version 6.0
[    27.555] (II) Loading extension RECORD
[    27.555] (II) LoadModule: "dri"
[    27.556] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    27.556] (II) Module dri: vendor="X.Org Foundation"
[    27.556]     compiled for 1.11.3, module version = 1.0.0
[    27.556]     ABI class: X.Org Server Extension, version 6.0
[    27.556] (II) Loading extension XFree86-DRI
[    27.556] (II) LoadModule: "dri2"
[    27.556] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    27.556] (II) Module dri2: vendor="X.Org Foundation"
[    27.556]     compiled for 1.11.3, module version = 1.2.0
[    27.556]     ABI class: X.Org Server Extension, version 6.0
[    27.556] (II) Loading extension DRI2
[    27.556] (==) Matched fglrx as autoconfigured driver 0
[    27.556] (==) Matched ati as autoconfigured driver 1
[    27.556] (==) Matched vesa as autoconfigured driver 2
[    27.556] (==) Matched fbdev as autoconfigured driver 3
[    27.556] (==) Assigned the driver to the xf86ConfigLayout
[    27.556] (II) LoadModule: "fglrx"
[    27.557] (WW) Warning, couldn't open module fglrx
[    27.557] (II) UnloadModule: "fglrx"
[    27.557] (II) Unloading fglrx
[    27.557] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    27.557] (II) LoadModule: "ati"
[    27.557] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    27.557] (II) Module ati: vendor="X.Org Foundation"
[    27.557]     compiled for 1.11.3, module version = 6.14.99
[    27.557]     Module class: X.Org Video Driver
[    27.557]     ABI class: X.Org Video Driver, version 11.0
[    27.557] (II) LoadModule: "radeon"
[    27.558] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    27.558] (II) Module radeon: vendor="X.Org Foundation"
[    27.558]     compiled for 1.11.3, module version = 6.14.99
[    27.558]     Module class: X.Org Video Driver
[    27.558]     ABI class: X.Org Video Driver, version 11.0
[    27.558] (II) LoadModule: "vesa"
[    27.558] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    27.558] (II) Module vesa: vendor="X.Org Foundation"
[    27.558]     compiled for 1.11.3, module version = 2.3.0
[    27.558]     Module class: X.Org Video Driver
[    27.558]     ABI class: X.Org Video Driver, version 11.0
[    27.558] (II) LoadModule: "fbdev"
[    27.559] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    27.559] (II) Module fbdev: vendor="X.Org Foundation"
[    27.559]     compiled for 1.11.3, module version = 0.4.2
[    27.559]     ABI class: X.Org Video Driver, version 11.0
[    27.559] (==) Matched fglrx as autoconfigured driver 0
[    27.559] (==) Matched ati as autoconfigured driver 1
[    27.559] (==) Matched vesa as autoconfigured driver 2
[    27.559] (==) Matched fbdev as autoconfigured driver 3
[    27.559] (==) Assigned the driver to the xf86ConfigLayout
[    27.559] (II) LoadModule: "fglrx"
[    27.559] (WW) Warning, couldn't open module fglrx
[    27.559] (II) UnloadModule: "fglrx"
[    27.559] (II) Unloading fglrx
[    27.559] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    27.559] (II) LoadModule: "ati"
[    27.559] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    27.559] (II) Module ati: vendor="X.Org Foundation"
[    27.560]     compiled for 1.11.3, module version = 6.14.99
[    27.564]     Module class: X.Org Video Driver
[    27.564]     ABI class: X.Org Video Driver, version 11.0
[    27.564] (II) LoadModule: "vesa"
[    27.564] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    27.564] (II) Module vesa: vendor="X.Org Foundation"
[    27.564]     compiled for 1.11.3, module version = 2.3.0
[    27.564]     Module class: X.Org Video Driver
[    27.564]     ABI class: X.Org Video Driver, version 11.0
[    27.564] (II) UnloadModule: "vesa"
[    27.564] (II) Unloading vesa
[    27.564] (II) Failed to load module "vesa" (already loaded, 0)
[    27.564] (II) LoadModule: "fbdev"
[    27.564] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    27.564] (II) Module fbdev: vendor="X.Org Foundation"
[    27.565]     compiled for 1.11.3, module version = 0.4.2
[    27.565]     ABI class: X.Org Video Driver, version 11.0
[    27.565] (II) UnloadModule: "fbdev"
[    27.565] (II) Unloading fbdev
[    27.565] (II) Failed to load module "fbdev" (already loaded, 0)
[    27.565] (II) RADEON: Driver for ATI Radeon chipsets:
    ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
    ATI Radeon Mobility X300 (M24) 3152 (PCIE),
    ATI FireGL M24 GL 3154 (PCIE), ATI FireMV 2400 3155 (PCI),
    ATI Radeon X600 (RV380) 3E50 (PCIE),
    ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
    ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
    ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
    ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
    ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
    ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
    ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
    ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
    ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
    ATI Radeon 8500 AIW BB (AGP), ATI Radeon IGP320M (U1) 4336,
    ATI Radeon IGP330M/340M/350M (U2) 4337,
    ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
    ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
    ATI Radeon X800PRO (R420) JI (AGP),
    ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
    ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
    ATI Radeon Mobility 9800 (M18) JN (AGP),
    ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
    ATI Radeon X800 VE (R420) JT (AGP), ATI Radeon X850 (R480) (AGP),
    ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
    ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
    ATI Radeon Mobility M7 LW (AGP),
    ATI Mobility FireGL 7800 M7 LX (AGP),
    ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
    ATI FireGL Mobility 9000 (M9) Ld (AGP),
    ATI Radeon Mobility 9000 (M9) Lf (AGP),
    ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI FireMV 2400 PCI,
    ATI Radeon 9700 Pro ND (AGP), ATI Radeon 9700/9500Pro NE (AGP),
    ATI Radeon 9600TX NF (AGP), ATI FireGL X1 NG (AGP),
    ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
    ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
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
    ATI Radeon 4800 Series, ATI Radeon HD 4850 x2,
    ATI FirePro V8750 (FireGL), ATI FirePro V7760 (FireGL),
    ATI Mobility RADEON HD 4850, ATI Mobility RADEON HD 4850 X2,
    ATI Radeon 4800 Series, ATI FirePro RV770, AMD FireStream 9270,
    AMD FireStream 9250, ATI FirePro V8700 (FireGL),
    ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
    ATI Mobility RADEON HD 4870, ATI Radeon 4800 Series,
    ATI Radeon 4800 Series, ATI FirePro M7750, ATI M98, ATI M98, ATI M98,
    ATI Mobility Radeon HD 4650, ATI Radeon RV730 (AGP),
    ATI Mobility Radeon HD 4670, ATI FirePro M5750,
    ATI Mobility Radeon HD 4670, ATI Radeon RV730 (AGP),
    ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
    ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
    ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
    ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
    ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
    ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI Radeon HD 4770,
    ATI FirePro M5750, ATI RV610, ATI Radeon HD 2400 XT,
    ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
    ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
    ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
    ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
    ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
    ATI Mobility Radeon HD 3850 X2, ATI RV670,
    ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
    ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
    ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
    ATI Radeon RV710, ATI Radeon RV710, ATI Radeon RV710,
    ATI Radeon HD 4350, ATI Mobility Radeon 4300 Series,
    ATI Mobility Radeon 4500 Series, ATI Mobility Radeon 4500 Series,
    ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
    ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
    ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
    ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
    ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
    ATI FireGL V3600, ATI Radeon HD 2600 LE,
    ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
    ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
    ATI Radeon HD 3450, ATI Radeon HD 3450, ATI Radeon HD 3430,
    ATI Radeon HD 3450, ATI FirePro V3700, ATI FireMV 2450,
    ATI FireMV 2260, ATI FireMV 2260, ATI Radeon HD 3600 Series,
    ATI Radeon HD 3650 AGP, ATI Radeon HD 3600 PRO,
    ATI Radeon HD 3600 XT, ATI Radeon HD 3600 PRO,
    ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
    ATI Mobility FireGL V5700, ATI Mobility FireGL V5725,
    ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
    ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
    ATI Radeon HD 3300 Graphics, ATI Radeon HD 3200 Graphics,
    ATI Radeon 3000 Graphics, SUMO, SUMO, SUMO2, SUMO2, SUMO2, SUMO2,
    SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, ATI Radeon HD 4200,
    ATI Radeon 4100, ATI Mobility Radeon HD 4200,
    ATI Mobility Radeon 4100, ATI Radeon HD 4290, ATI Radeon HD 4250,
    AMD Radeon HD 6310 Graphics, AMD Radeon HD 6310 Graphics,
    AMD Radeon HD 6250 Graphics, AMD Radeon HD 6250 Graphics,
    AMD Radeon HD 6300 Series Graphics,
    AMD Radeon HD 6200 Series Graphics, PALM, PALM, CYPRESS,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, AMD Firestream 9370,
    AMD Firestream 9350, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5800 Series, ATI Radeon HD 5900 Series,
    ATI Radeon HD 5900 Series, ATI Mobility Radeon HD 5800 Series,
    ATI Mobility Radeon HD 5800 Series,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
    ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
    ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
    ATI Mobility Radeon HD 5000 Series,
    ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5670,
    ATI Radeon HD 5570, ATI Radeon HD 5500 Series, REDWOOD,
    ATI Mobility Radeon HD 5000 Series,
    ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon Graphics,
    ATI Mobility Radeon Graphics, CEDAR,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, ATI FirePro 2270, CEDAR,
    ATI Radeon HD 5450, CEDAR, CEDAR, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
    CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
    AMD Radeon HD 6900 Series, AMD Radeon HD 6900 Series, CAYMAN, CAYMAN,
    CAYMAN, AMD Radeon HD 6900M Series, Mobility Radeon HD 6000 Series,
    BARTS, BARTS, Mobility Radeon HD 6000 Series,
    Mobility Radeon HD 6000 Series, BARTS, BARTS, BARTS, BARTS,
    AMD Radeon HD 6800 Series, AMD Radeon HD 6800 Series,
    AMD Radeon HD 6700 Series, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
    CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS
[    27.571] (II) VESA: driver for VESA chipsets: vesa
[    27.571] (II) FBDEV: driver for framebuffer: fbdev
[    27.571] (++) using VT number 7

[    27.572] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    27.572] (II) [KMS] drm report modesetting isn't supported.
[    27.572] (WW) Falling back to old probe method for vesa
[    27.572] (WW) Falling back to old probe method for fbdev
[    27.572] (II) Loading sub module "fbdevhw"
[    27.572] (II) LoadModule: "fbdevhw"
[    27.572] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    27.572] (II) Module fbdevhw: vendor="X.Org Foundation"
[    27.572]     compiled for 1.11.3, module version = 0.0.2
[    27.572]     ABI class: X.Org Video Driver, version 11.0
[    27.572] (II) RADEON(0): TOTO SAYS 00000000fe9f0000
[    27.572] (II) RADEON(0): MMIO registers at 0x00000000fe9f0000: size 64KB
[    27.572] (II) RADEON(0): PCI bus 1 card 0 func 0
[    27.572] (II) RADEON(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    27.572] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    27.572] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    27.572] (==) RADEON(0): Default visual is TrueColor
[    27.572] (II) Loading sub module "vgahw"
[    27.572] (II) LoadModule: "vgahw"
[    27.573] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    27.573] (II) Module vgahw: vendor="X.Org Foundation"
[    27.573]     compiled for 1.11.3, module version = 0.1.0
[    27.573]     ABI class: X.Org Video Driver, version 11.0
[    27.573] (II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
[    27.573] (==) RADEON(0): RGB weight 888
[    27.573] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    27.573] (--) RADEON(0): Chipset: "ATI Radeon 9200 5961 (AGP)" (ChipID = 0x5961)
[    27.573] (--) RADEON(0): Linear framebuffer at 0x00000000e8000000
[    27.573] (II) RADEON(0): AGP card detected
[    27.573] (II) Loading sub module "int10"
[    27.573] (II) LoadModule: "int10"
[    27.573] (II) Loading /usr/lib/xorg/modules/libint10.so
[    27.573] (II) Module int10: vendor="X.Org Foundation"
[    27.573]     compiled for 1.11.3, module version = 1.0.0
[    27.573]     ABI class: X.Org Video Driver, version 11.0
[    27.573] (II) RADEON(0): initializing int10
[    27.578] (II) RADEON(0): Primary V_BIOS segment is: 0xc000
[    27.580] (II) RADEON(0): Legacy BIOS detected
[    27.580] drmOpenDevice: node name is /dev/dri/card0
[    27.639] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[    27.639] drmOpenDevice: node name is /dev/dri/card0
[    27.643] drmOpenByBusid: drmOpenMinor returns -1
[    27.643] drmOpenDevice: node name is /dev/dri/card1
[    27.648] drmOpenByBusid: drmOpenMinor returns -1
[    27.648] drmOpenDevice: node name is /dev/dri/card2
[    27.657] drmOpenByBusid: drmOpenMinor returns -1
[    27.657] drmOpenDevice: node name is /dev/dri/card3
[    27.661] drmOpenByBusid: drmOpenMinor returns -1
[    27.661] drmOpenDevice: node name is /dev/dri/card4
[    27.665] drmOpenByBusid: drmOpenMinor returns -1
[    27.665] drmOpenDevice: node name is /dev/dri/card5
[    27.669] drmOpenByBusid: drmOpenMinor returns -1
[    27.669] drmOpenDevice: node name is /dev/dri/card6
[    27.674] drmOpenByBusid: drmOpenMinor returns -1
[    27.674] drmOpenDevice: node name is /dev/dri/card7
[    27.678] drmOpenByBusid: drmOpenMinor returns -1
[    27.678] drmOpenDevice: node name is /dev/dri/card8
[    27.683] drmOpenByBusid: drmOpenMinor returns -1
[    27.683] drmOpenDevice: node name is /dev/dri/card9
[    27.687] drmOpenByBusid: drmOpenMinor returns -1
[    27.687] drmOpenDevice: node name is /dev/dri/card10
[    27.691] drmOpenByBusid: drmOpenMinor returns -1
[    27.691] drmOpenDevice: node name is /dev/dri/card11
[    27.700] drmOpenByBusid: drmOpenMinor returns -1
[    27.700] drmOpenDevice: node name is /dev/dri/card12
[    27.705] drmOpenByBusid: drmOpenMinor returns -1
[    27.705] drmOpenDevice: node name is /dev/dri/card13
[    27.710] drmOpenByBusid: drmOpenMinor returns -1
[    27.710] drmOpenDevice: node name is /dev/dri/card14
[    27.715] drmOpenByBusid: drmOpenMinor returns -1
[    27.715] drmOpenDevice: node name is /dev/dri/card15
[    27.720] drmOpenByBusid: drmOpenMinor returns -1
[    27.720] drmOpenDevice: node name is /dev/dri/card0
[    27.727] drmOpenDevice: node name is /dev/dri/card0
[    27.732] drmOpenDevice: node name is /dev/dri/card1
[    27.737] drmOpenDevice: node name is /dev/dri/card2
[    27.741] drmOpenDevice: node name is /dev/dri/card3
[    27.745] drmOpenDevice: node name is /dev/dri/card4
[    27.749] drmOpenDevice: node name is /dev/dri/card5
[    27.754] drmOpenDevice: node name is /dev/dri/card6
[    27.760] drmOpenDevice: node name is /dev/dri/card7
[    27.764] drmOpenDevice: node name is /dev/dri/card8
[    27.769] drmOpenDevice: node name is /dev/dri/card9
[    27.773] drmOpenDevice: node name is /dev/dri/card10
[    27.777] drmOpenDevice: node name is /dev/dri/card11
[    27.782] drmOpenDevice: node name is /dev/dri/card12
[    27.786] drmOpenDevice: node name is /dev/dri/card13
[    27.790] drmOpenDevice: node name is /dev/dri/card14
[    27.795] drmOpenDevice: node name is /dev/dri/card15
[    27.799] (EE) RADEON(0): [dri] RADEONDRIGetVersion failed to open the DRM
[dri] Disabling DRI.
[    27.799] (II) RADEON(0): Generation 2 PCI interface, using max accessible memory
[    27.799] (II) RADEON(0): Detected total video RAM=131072K, accessible=131072K (PCI BAR=131072K)
[    27.799] (--) RADEON(0): Mapped VideoRAM: 131072 kByte (128 bit DDR SDRAM)
[    27.799] (II) RADEON(0): Color tiling enabled by default
[    27.799] (II) Loading sub module "ddc"
[    27.799] (II) LoadModule: "ddc"
[    27.799] (II) Module "ddc" already built-in
[    27.799] (II) Loading sub module "i2c"
[    27.799] (II) LoadModule: "i2c"
[    27.799] (II) Module "i2c" already built-in
[    27.799] (II) RADEON(0): ref_freq: 2700, min_out_pll: 20000, max_out_pll: 40000, min_in_pll: 40, max_in_pll: 3000, xclk: 20000, sclk: 250.000000, mclk: 200.000000
[    27.799] (II) RADEON(0): PLL parameters: rf=2700 rd=12 min=20000 max=40000; xclk=20000
[    27.799] (II) RADEON(0): DFP table revision: 4
[    27.799] (II) RADEON(0): Output VGA-0 has no monitor section
[    27.799] (II) RADEON(0): I2C bus "VGA-0" initialized.
[    27.799] (II) RADEON(0): Output DVI-0 has no monitor section
[    27.799] (II) RADEON(0): I2C bus "DVI-0" initialized.
[    27.799] (II) RADEON(0): Output S-video has no monitor section
[    27.799] (II) RADEON(0): Default TV standard: PAL
[    27.799] (II) RADEON(0): TV standards supported by chip: NTSC PAL 
[    27.799] (II) RADEON(0): Port0:
[    27.799]   XRANDR name: VGA-0
[    27.799]   Connector: VGA
[    27.799]   CRT1: INTERNAL_DAC1
[    27.799]   DDC reg: 0x60
[    27.799] (II) RADEON(0): Port1:
[    27.799]   XRANDR name: DVI-0
[    27.799]   Connector: DVI-I
[    27.799]   CRT2: INTERNAL_DAC2
[    27.799]   DFP1: INTERNAL_TMDS1
[    27.799]   DDC reg: 0x64
[    27.799] (II) RADEON(0): Port2:
[    27.799]   XRANDR name: S-video
[    27.799]   Connector: S-video
[    27.799]   TV1: INTERNAL_DAC2
[    27.799]   DDC reg: 0x0
[    27.799] (II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
[    27.874] (II) RADEON(0): EDID for output VGA-0
[    27.874] (II) RADEON(0): Manufacturer: GSM  Model: 4357  Serial#: 39261
[    27.874] (II) RADEON(0): Year: 2003  Week: 8
[    27.874] (II) RADEON(0): EDID Version: 1.3
[    27.874] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[    27.874] (II) RADEON(0): Sync:  Separate
[    27.874] (II) RADEON(0): Max Image Size [cm]: horiz.: 34  vert.: 27
[    27.874] (II) RADEON(0): Gamma: 2.50
[    27.874] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    27.874] (II) RADEON(0): First detailed timing is preferred mode
[    27.874] (II) RADEON(0): redX: 0.640 redY: 0.340   greenX: 0.290 greenY: 0.610
[    27.874] (II) RADEON(0): blueX: 0.140 blueY: 0.070   whiteX: 0.310 whiteY: 0.330
[    27.874] (II) RADEON(0): Supported established timings:
[    27.874] (II) RADEON(0): 720x400@70Hz
[    27.874] (II) RADEON(0): 640x480@60Hz
[    27.874] (II) RADEON(0): 640x480@75Hz
[    27.874] (II) RADEON(0): 800x600@60Hz
[    27.874] (II) RADEON(0): 800x600@75Hz
[    27.874] (II) RADEON(0): 832x624@75Hz
[    27.874] (II) RADEON(0): 1024x768@60Hz
[    27.874] (II) RADEON(0): 1024x768@75Hz
[    27.874] (II) RADEON(0): 1280x1024@75Hz
[    27.874] (II) RADEON(0): 1152x864@75Hz
[    27.874] (II) RADEON(0): Manufacturer's mask: 0
[    27.874] (II) RADEON(0): Supported standard timings:
[    27.874] (II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    27.874] (II) RADEON(0): #1: hsize: 1024  vsize 768  refresh: 75  vid: 20321
[    27.874] (II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 75  vid: 20293
[    27.874] (II) RADEON(0): #3: hsize: 640  vsize 480  refresh: 75  vid: 20273
[    27.874] (II) RADEON(0): Supported detailed timing:
[    27.874] (II) RADEON(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
[    27.874] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
[    27.874] (II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[    27.874] (II) RADEON(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 145 MHz
[    27.874] (II) RADEON(0): Monitor name: L1710S
[    27.875] (II) RADEON(0): Monitor name: 
[    27.875] (II) RADEON(0): EDID (in hex):
[    27.875] (II) RADEON(0):     00ffffffffffff001e6d57435d990000
[    27.875] (II) RADEON(0):     080d010368221b96eac5c6a3574a9c23
[    27.875] (II) RADEON(0):     124f54a56b808180614f454f314f0101
[    27.875] (II) RADEON(0):     010101010101302a009851002a403070
[    27.875] (II) RADEON(0):     1300520e1100001e000000fd00384b1e
[    27.875] (II) RADEON(0):     530e000a202020202020000000fc004c
[    27.875] (II) RADEON(0):     31373130530a202020202020000000fc
[    27.875] (II) RADEON(0):     00200a202020202020202020202000a1
[    27.875] (II) RADEON(0): EDID vendor "GSM", prod id 17239
[    27.875] (II) RADEON(0): Using EDID range info for horizontal sync
[    27.875] (II) RADEON(0): Using EDID range info for vertical refresh
[    27.875] (II) RADEON(0): Printing DDC gathered Modelines:
[    27.875] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    27.875] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    27.875] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    27.875] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    27.875] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    27.875] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    27.875] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    27.875] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    27.875] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    27.875] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    27.875] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    27.875] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
[    27.875] (II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
[    27.875] (II) RADEON(0): Manufacturer: GSM  Model: 4357  Serial#: 39261
[    27.875] (II) RADEON(0): Year: 2003  Week: 8
[    27.875] (II) RADEON(0): EDID Version: 1.3
[    27.875] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[    27.875] (II) RADEON(0): Sync:  Separate
[    27.875] (II) RADEON(0): Max Image Size [cm]: horiz.: 34  vert.: 27
[    27.875] (II) RADEON(0): Gamma: 2.50
[    27.875] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    27.875] (II) RADEON(0): First detailed timing is preferred mode
[    27.875] (II) RADEON(0): redX: 0.640 redY: 0.340   greenX: 0.290 greenY: 0.610
[    27.875] (II) RADEON(0): blueX: 0.140 blueY: 0.070   whiteX: 0.310 whiteY: 0.330
[    27.875] (II) RADEON(0): Supported established timings:
[    27.875] (II) RADEON(0): 720x400@70Hz
[    27.875] (II) RADEON(0): 640x480@60Hz
[    27.875] (II) RADEON(0): 640x480@75Hz
[    27.875] (II) RADEON(0): 800x600@60Hz
[    27.875] (II) RADEON(0): 800x600@75Hz
[    27.875] (II) RADEON(0): 832x624@75Hz
[    27.875] (II) RADEON(0): 1024x768@60Hz
[    27.875] (II) RADEON(0): 1024x768@75Hz
[    27.875] (II) RADEON(0): 1280x1024@75Hz
[    27.875] (II) RADEON(0): 1152x864@75Hz
[    27.875] (II) RADEON(0): Manufacturer's mask: 0
[    27.875] (II) RADEON(0): Supported standard timings:
[    27.875] (II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    27.875] (II) RADEON(0): #1: hsize: 1024  vsize 768  refresh: 75  vid: 20321
[    27.875] (II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 75  vid: 20293
[    27.875] (II) RADEON(0): #3: hsize: 640  vsize 480  refresh: 75  vid: 20273
[    27.875] (II) RADEON(0): Supported detailed timing:
[    27.875] (II) RADEON(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
[    27.875] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
[    27.875] (II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[    27.875] (II) RADEON(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 145 MHz
[    27.875] (II) RADEON(0): Monitor name: L1710S
[    27.875] (II) RADEON(0): Monitor name: 
[    27.875] (II) RADEON(0): EDID (in hex):
[    27.875] (II) RADEON(0):     00ffffffffffff001e6d57435d990000
[    27.875] (II) RADEON(0):     080d010368221b96eac5c6a3574a9c23
[    27.875] (II) RADEON(0):     124f54a56b808180614f454f314f0101
[    27.875] (II) RADEON(0):     010101010101302a009851002a403070
[    27.875] (II) RADEON(0):     1300520e1100001e000000fd00384b1e
[    27.875] (II) RADEON(0):     530e000a202020202020000000fc004c
[    27.875] (II) RADEON(0):     31373130530a202020202020000000fc
[    27.875] (II) RADEON(0):     00200a202020202020202020202000a1
[    27.875] finished output detect: 0
[    27.875] (II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
[    27.880] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
[    27.880] Unhandled monitor type 0
[    27.880] finished output detect: 1
[    27.880] (II) RADEON(0): Output: S-video, Detected Monitor Type: 0
[    27.880] finished output detect: 2
[    27.880] finished all detect
[    27.946] (II) RADEON(0): EDID for output VGA-0
[    27.946] (II) RADEON(0): Manufacturer: GSM  Model: 4357  Serial#: 39261
[    27.946] (II) RADEON(0): Year: 2003  Week: 8
[    27.946] (II) RADEON(0): EDID Version: 1.3
[    27.946] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[    27.946] (II) RADEON(0): Sync:  Separate
[    27.946] (II) RADEON(0): Max Image Size [cm]: horiz.: 34  vert.: 27
[    27.946] (II) RADEON(0): Gamma: 2.50
[    27.946] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    27.946] (II) RADEON(0): First detailed timing is preferred mode
[    27.946] (II) RADEON(0): redX: 0.640 redY: 0.340   greenX: 0.290 greenY: 0.610
[    27.947] (II) RADEON(0): blueX: 0.140 blueY: 0.070   whiteX: 0.310 whiteY: 0.330
[    27.947] (II) RADEON(0): Supported established timings:
[    27.947] (II) RADEON(0): 720x400@70Hz
[    27.947] (II) RADEON(0): 640x480@60Hz
[    27.947] (II) RADEON(0): 640x480@75Hz
[    27.947] (II) RADEON(0): 800x600@60Hz
[    27.947] (II) RADEON(0): 800x600@75Hz
[    27.947] (II) RADEON(0): 832x624@75Hz
[    27.947] (II) RADEON(0): 1024x768@60Hz
[    27.947] (II) RADEON(0): 1024x768@75Hz
[    27.947] (II) RADEON(0): 1280x1024@75Hz
[    27.947] (II) RADEON(0): 1152x864@75Hz
[    27.947] (II) RADEON(0): Manufacturer's mask: 0
[    27.947] (II) RADEON(0): Supported standard timings:
[    27.947] (II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    27.947] (II) RADEON(0): #1: hsize: 1024  vsize 768  refresh: 75  vid: 20321
[    27.947] (II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 75  vid: 20293
[    27.947] (II) RADEON(0): #3: hsize: 640  vsize 480  refresh: 75  vid: 20273
[    27.947] (II) RADEON(0): Supported detailed timing:
[    27.947] (II) RADEON(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
[    27.947] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
[    27.947] (II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[    27.947] (II) RADEON(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 145 MHz
[    27.947] (II) RADEON(0): Monitor name: L1710S
[    27.947] (II) RADEON(0): Monitor name: 
[    27.947] (II) RADEON(0): EDID (in hex):
[    27.947] (II) RADEON(0):     00ffffffffffff001e6d57435d990000
[    27.947] (II) RADEON(0):     080d010368221b96eac5c6a3574a9c23
[    27.947] (II) RADEON(0):     124f54a56b808180614f454f314f0101
[    27.947] (II) RADEON(0):     010101010101302a009851002a403070
[    27.947] (II) RADEON(0):     1300520e1100001e000000fd00384b1e
[    27.947] (II) RADEON(0):     530e000a202020202020000000fc004c
[    27.947] (II) RADEON(0):     31373130530a202020202020000000fc
[    27.947] (II) RADEON(0):     00200a202020202020202020202000a1
[    27.947] (II) RADEON(0): EDID vendor "GSM", prod id 17239
[    27.947] (II) RADEON(0): Using hsync ranges from config file
[    27.947] (II) RADEON(0): Using vrefresh ranges from config file
[    27.947] (II) RADEON(0): Printing DDC gathered Modelines:
[    27.947] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    27.947] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    27.947] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    27.947] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    27.947] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    27.947] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    27.947] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    27.947] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    27.947] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    27.947] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    27.947] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    27.947] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
[    27.947] (II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
[    27.947] (II) RADEON(0): Manufacturer: GSM  Model: 4357  Serial#: 39261
[    27.947] (II) RADEON(0): Year: 2003  Week: 8
[    27.947] (II) RADEON(0): EDID Version: 1.3
[    27.947] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[    27.947] (II) RADEON(0): Sync:  Separate
[    27.947] (II) RADEON(0): Max Image Size [cm]: horiz.: 34  vert.: 27
[    27.947] (II) RADEON(0): Gamma: 2.50
[    27.947] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    27.947] (II) RADEON(0): First detailed timing is preferred mode
[    27.947] (II) RADEON(0): redX: 0.640 redY: 0.340   greenX: 0.290 greenY: 0.610
[    27.947] (II) RADEON(0): blueX: 0.140 blueY: 0.070   whiteX: 0.310 whiteY: 0.330
[    27.947] (II) RADEON(0): Supported established timings:
[    27.947] (II) RADEON(0): 720x400@70Hz
[    27.947] (II) RADEON(0): 640x480@60Hz
[    27.947] (II) RADEON(0): 640x480@75Hz
[    27.947] (II) RADEON(0): 800x600@60Hz
[    27.947] (II) RADEON(0): 800x600@75Hz
[    27.947] (II) RADEON(0): 832x624@75Hz
[    27.947] (II) RADEON(0): 1024x768@60Hz
[    27.947] (II) RADEON(0): 1024x768@75Hz
[    27.947] (II) RADEON(0): 1280x1024@75Hz
[    27.947] (II) RADEON(0): 1152x864@75Hz
[    27.947] (II) RADEON(0): Manufacturer's mask: 0
[    27.947] (II) RADEON(0): Supported standard timings:
[    27.947] (II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    27.947] (II) RADEON(0): #1: hsize: 1024  vsize 768  refresh: 75  vid: 20321
[    27.947] (II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 75  vid: 20293
[    27.947] (II) RADEON(0): #3: hsize: 640  vsize 480  refresh: 75  vid: 20273
[    27.947] (II) RADEON(0): Supported detailed timing:
[    27.947] (II) RADEON(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
[    27.947] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
[    27.947] (II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[    27.947] (II) RADEON(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 145 MHz
[    27.947] (II) RADEON(0): Monitor name: L1710S
[    27.947] (II) RADEON(0): Monitor name: 
[    27.947] (II) RADEON(0): EDID (in hex):
[    27.947] (II) RADEON(0):     00ffffffffffff001e6d57435d990000
[    27.947] (II) RADEON(0):     080d010368221b96eac5c6a3574a9c23
[    27.947] (II) RADEON(0):     124f54a56b808180614f454f314f0101
[    27.947] (II) RADEON(0):     010101010101302a009851002a403070
[    27.947] (II) RADEON(0):     1300520e1100001e000000fd00384b1e
[    27.947] (II) RADEON(0):     530e000a202020202020000000fc004c
[    27.947] (II) RADEON(0):     31373130530a202020202020000000fc
[    27.947] (II) RADEON(0):     00200a202020202020202020202000a1
[    27.947] (II) RADEON(0): EDID vendor "GSM", prod id 17239
[    27.948] (II) RADEON(0): Printing probed modes for output VGA-0
[    27.948] (II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    27.948] (II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    27.948] (II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    27.948] (II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    27.948] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    27.948] (II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    27.948] (II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    27.948] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    27.948] (II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    27.948] (II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    27.948] (II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    27.952] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
[    27.952] Unhandled monitor type 0
[    27.952] (II) RADEON(0): EDID for output DVI-0
[    27.952] (II) RADEON(0): Output: S-video, Detected Monitor Type: 0
[    27.952] (II) RADEON(0): EDID for output S-video
[    27.952] (II) RADEON(0): Output VGA-0 connected
[    27.952] (II) RADEON(0): Output DVI-0 disconnected
[    27.952] (II) RADEON(0): Output S-video disconnected
[    27.952] (II) RADEON(0): Using exact sizes for initial modes
[    27.952] (II) RADEON(0): Output VGA-0 using initial mode 1280x1024
[    27.952] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    27.952] (**) RADEON(0): Display dimensions: (340, 270) mm
[    27.952] (**) RADEON(0): DPI set to (95, 120)
[    27.952] (II) Loading sub module "fb"
[    27.952] (II) LoadModule: "fb"
[    27.953] (II) Loading /usr/lib/xorg/modules/libfb.so
[    27.953] (II) Module fb: vendor="X.Org Foundation"
[    27.953]     compiled for 1.11.3, module version = 1.0.0
[    27.953]     ABI class: X.Org ANSI C Emulation, version 0.4
[    27.953] (II) Loading sub module "ramdac"
[    27.953] (II) LoadModule: "ramdac"
[    27.953] (II) Module "ramdac" already built-in
[    27.953] (==) RADEON(0): Using XAA acceleration architecture
[    27.953] (II) Loading sub module "xaa"
[    27.953] (II) LoadModule: "xaa"
[    27.953] (II) Loading /usr/lib/xorg/modules/libxaa.so
[    27.953] (II) Module xaa: vendor="X.Org Foundation"
[    27.953]     compiled for 1.11.3, module version = 1.2.1
[    27.953]     ABI class: X.Org Video Driver, version 11.0
[    27.953] (==) RADEON(0): Assuming overlay scaler buffer width is 1536
[    27.953] (II) RADEON(0): MM_TABLE: 01-0c-00-1f-06-00-00-66-02-00-00-02-00-03
[    27.953] (!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
[    27.953] (II) UnloadModule: "vesa"
[    27.953] (II) Unloading vesa
[    27.953] (II) UnloadModule: "fbdev"
[    27.953] (II) Unloading fbdev
[    27.953] (II) UnloadModule: "fbdevhw"
[    27.953] (II) Unloading fbdevhw
[    27.953] (--) Depth 24 pixmap format is 32 bpp
[    27.953] (II) RADEON(0): RADEONScreenInit e8000000 0 0
[    27.970] Entering TV Save
[    27.970] Save TV timing tables
[    27.970] saveTimingTables: reading timing tables
[    28.220] TV Save done
[    28.221] disable primary dac
[    28.221] (II) RADEON(0): Dynamic Power Management Disabled
[    28.221] (II) RADEON(0): RADEONInitMemoryMap() : 
[    28.221] (II) RADEON(0):   mem_size         : 0x08000000
[    28.221] (II) RADEON(0):   MC_FB_LOCATION   : 0xefffe800
[    28.221] (II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
[    28.221] (II) RADEON(0): Depth moves disabled by default
[    28.221] (II) RADEON(0): Memory manager initialized to (0,0) (1280,8191)
[    28.221] (II) RADEON(0): Reserved area from (0,1280) to (1280,1282)
[    28.221] (II) RADEON(0): Largest offscreen area available: 1280 x 6909
[    28.221] (II) RADEON(0): RADEONRestoreMemMapRegisters() : 
[    28.221] (II) RADEON(0):   MC_FB_LOCATION   : 0xefffe800 0x1fff0000
[    28.221] (II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
[    28.421] (==) RADEON(0): Backing store disabled
[    28.421] (WW) RADEON(0): Direct rendering disabled
[    28.421] (II) RADEON(0): Render acceleration disabled
[    28.421] (II) RADEON(0): Using XFree86 Acceleration Architecture (XAA)
[    28.421]     Screen to screen bit blits
[    28.421]     Solid filled rectangles
[    28.421]     8x8 mono pattern filled rectangles
[    28.421]     Indirect CPU to Screen color expansion
[    28.421]     Solid Lines
[    28.421]     Scanline Image Writes
[    28.421]     Setting up tile and stipple cache:
[    28.421]         32 128x128 slots
[    28.421]         32 256x256 slots
[    28.421]         16 512x512 slots
[    28.421] (II) RADEON(0): Acceleration enabled
[    28.421] (==) RADEON(0): DPMS enabled
[    28.421] (==) RADEON(0): Silken mouse enabled
[    28.422] (II) RADEON(0): Will use 32 kb for hardware cursor 0 at offset 0x00642800
[    28.422] (II) RADEON(0): Will use 32 kb for hardware cursor 1 at offset 0x00647800
[    28.422] (II) RADEON(0): Largest offscreen area available: 1280 x 6901
[    28.422] (II) Loading sub module "i2c"
[    28.422] (II) LoadModule: "i2c"
[    28.422] (II) Module "i2c" already built-in
[    28.422] (II) RADEON(0): Using Radeon bus access method
[    28.422] (II) RADEON(0): I2C bus "Radeon multimedia bus" initialized.
[    28.422] (II) Loading sub module "fi1236"
[    28.422] (II) LoadModule: "fi1236"
[    28.422] (II) Loading /usr/lib/xorg/modules/multimedia/fi1236_drv.so
[    28.422] (II) Module fi1236: vendor="X.Org Foundation"
[    28.422]     compiled for 1.11.3, module version = 1.0.0
[    28.422]     ABI class: X.Org Video Driver, version 11.0
[    28.424] (II) RADEON(0): I2C device "Radeon multimedia bus:FI12xx Tuner" registered at address 0xC6.
[    28.424] (II) RADEON(0): Detected NO TUNER device at 0xc6
[    28.424] (II) Loading sub module "uda1380"
[    28.424] (II) LoadModule: "uda1380"
[    28.425] (II) Loading /usr/lib/xorg/modules/multimedia/uda1380_drv.so
[    28.425] (II) Module uda1380: vendor="X.Org Foundation"
[    28.425]     compiled for 1.11.3, module version = 1.0.0
[    28.425]     ABI class: X.Org Video Driver, version 11.0
[    28.427] (II) RADEON(0): I2C device "Radeon multimedia bus:UDA1380 Stereo audion coder-decoder" registered at address 0x30.
[    28.427] (II) RADEON(0): UDA1380 stereo coder-decoder detected
[    28.431] (II) RADEON(0): UDA1380 initialized
[    28.431] (II) Loading sub module "msp3430"
[    28.431] (II) LoadModule: "msp3430"
[    28.431] (II) Loading /usr/lib/xorg/modules/multimedia/msp3430_drv.so
[    28.431] (II) Module msp3430: vendor="X.Org Foundation"
[    28.431]     compiled for 1.11.3, module version = 1.0.0
[    28.431]     ABI class: X.Org Video Driver, version 11.0
[    28.442] (II) RADEON(0): Found MSP - unknown type (unsupported), rom version 0x00, chip_id=0x0000
[    28.453] (II) RADEON(0): Found MSP - unknown type (unsupported), rom version 0x00, chip_id=0x0000
[    28.453] (II) Loading sub module "theatre_detect"
[    28.453] (II) LoadModule: "theatre_detect"
[    28.453] (II) Loading /usr/lib/xorg/modules/multimedia/theatre_detect_drv.so
[    28.453] (II) Module theatre_detect: vendor="X.Org Foundation"
[    28.453]     compiled for 1.11.3, module version = 1.0.0
[    28.453]     ABI class: X.Org Video Driver, version 11.0
[    28.453] (II) RADEON(0): No response from device 0 on VIP bus
[    28.453] (II) RADEON(0): Device 1 on VIP bus ids as 0x4d541002
[    28.454] (II) RADEON(0): No response from device 2 on VIP bus
[    28.454] (II) RADEON(0): No response from device 3 on VIP bus
[    28.454] (II) RADEON(0): Detected Rage Theatre as device 1 on VIP bus with id 0x4d541002
[    28.454] (II) RADEON(0): Detected Rage Theatre revision 00000003
[    28.454] (II) RADEON(0): video decoder type is 0x4e20 (BIOS value) versus 0x4e20 (current PLL setting)
[    28.454] (II) RADEON(0): Composite connector is port 1
[    28.454] (II) RADEON(0): SVideo connector is port 5
[    28.454] (II) RADEON(0): Rage Theatre: Connectors (detected): tuner=0, composite=1, svideo=5
[    28.454] (II) RADEON(0): RageTheatre: Connectors (using): tuner=0, composite=1, svideo=5
[    28.454] (II) RADEON(0): video decoder type used: 0x0006
[    28.454] (II) RADEON(0): Going to load the corresponding theatre module
[    28.454] (II) Loading sub module "theatre"
[    28.454] (II) LoadModule: "theatre"
[    28.454] (II) Loading /usr/lib/xorg/modules/multimedia/theatre_drv.so
[    28.454] (II) Module theatre: vendor="X.Org Foundation"
[    28.454]     compiled for 1.11.3, module version = 1.0.0
[    28.454]     ABI class: X.Org Video Driver, version 11.0
[    28.655] (II) RADEON(0): Rage Theatre setting standard 0x0000
[    28.682] (II) RADEON(0): Rage Theatre setting standard 0x0000
[    28.887] (II) RADEON(0): Rage Theatre setting standard 0x0000
[    28.890] (II) RADEON(0): Set up overlay video
[    28.891] (II) RADEON(0): Set up textured video
[    28.891] (II) RADEON(0): [XvMC] Associated with Radeon Textured Video.
[    28.891] (II) RADEON(0): [XvMC] Extension initialized.
[    28.919] disable primary dac
[    28.919] disable TV
[    28.919] disable primary dac
[    28.919] init memmap
[    28.919] init common
[    28.919] init crtc1
[    28.919] init pll1
[    28.919] freq: 108000000
[    28.919] best_freq: 108000000
[    28.919] best_feedback_div: 16
[    28.919] best_frac_feedback_div: 0
[    28.919] best_ref_div: 2
[    28.919] best_post_div: 2
[    28.919] restore memmap
[    28.920] (II) RADEON(0): RADEONRestoreMemMapRegisters() : 
[    28.920] (II) RADEON(0):   MC_FB_LOCATION   : 0xefffe800 0xefffe800
[    28.920] (II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
[    29.020] restore common
[    29.125] restore crtc1
[    29.126] restore pll1
[    29.176] finished PLL1
[    29.176] set RMX
[    29.176] set primary dac
[    29.176] enable primary dac
[    29.176] disable TV
[    29.176] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    29.177] (--) RandR disabled
[    29.177] (II) Initializing built-in extension Generic Event Extension
[    29.177] (II) Initializing built-in extension SHAPE
[    29.177] (II) Initializing built-in extension MIT-SHM
[    29.177] (II) Initializing built-in extension XInputExtension
[    29.177] (II) Initializing built-in extension XTEST
[    29.177] (II) Initializing built-in extension BIG-REQUESTS
[    29.177] (II) Initializing built-in extension SYNC
[    29.177] (II) Initializing built-in extension XKEYBOARD
[    29.177] (II) Initializing built-in extension XC-MISC
[    29.177] (II) Initializing built-in extension SECURITY
[    29.177] (II) Initializing built-in extension XINERAMA
[    29.177] (II) Initializing built-in extension XFIXES
[    29.177] (II) Initializing built-in extension RENDER
[    29.177] (II) Initializing built-in extension RANDR
[    29.177] (II) Initializing built-in extension COMPOSITE
[    29.177] (II) Initializing built-in extension DAMAGE
[    29.202] (II) AIGLX: Screen 0 is not DRI2 capable
[    29.202] (II) AIGLX: Screen 0 is not DRI capable
[    29.252] (II) AIGLX: Loaded and initialized swrast
[    29.252] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    29.252] (II) RADEON(0): Setting screen physical size to 338 x 270
[    29.280] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    29.288] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    29.288] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    29.288] (II) LoadModule: "evdev"
[    29.288] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.289] (II) Module evdev: vendor="X.Org Foundation"
[    29.289]     compiled for 1.11.3, module version = 2.7.0
[    29.289]     Module class: X.Org XInput Driver
[    29.289]     ABI class: X.Org XInput driver, version 16.0
[    29.289] (II) Using input driver 'evdev' for 'Power Button'
[    29.289] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.289] (**) Power Button: always reports core events
[    29.289] (**) evdev: Power Button: Device: "/dev/input/event1"
[    29.289] (--) evdev: Power Button: Vendor 0 Product 0x1
[    29.289] (--) evdev: Power Button: Found keys
[    29.289] (II) evdev: Power Button: Configuring as keyboard
[    29.289] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    29.289] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    29.289] (**) Option "xkb_rules" "evdev"
[    29.289] (**) Option "xkb_model" "pc105"
[    29.289] (**) Option "xkb_layout" "si"
[    29.300] (II) XKB: reuse xkmfile /var/lib/xkb/server-382E998F79C55FE563EE3D1572FEC9D6349EB92C.xkm
[    29.301] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    29.301] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    29.301] (II) Using input driver 'evdev' for 'Power Button'
[    29.301] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.301] (**) Power Button: always reports core events
[    29.301] (**) evdev: Power Button: Device: "/dev/input/event0"
[    29.301] (--) evdev: Power Button: Vendor 0 Product 0x1
[    29.301] (--) evdev: Power Button: Found keys
[    29.301] (II) evdev: Power Button: Configuring as keyboard
[    29.301] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    29.301] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    29.301] (**) Option "xkb_rules" "evdev"
[    29.301] (**) Option "xkb_model" "pc105"
[    29.301] (**) Option "xkb_layout" "si"
[    29.302] (II) config/udev: Adding input device UVC Camera (046d:0825) (/dev/input/event3)
[    29.302] (**) UVC Camera (046d:0825): Applying InputClass "evdev keyboard catchall"
[    29.302] (II) Using input driver 'evdev' for 'UVC Camera (046d:0825)'
[    29.302] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.302] (**) UVC Camera (046d:0825): always reports core events
[    29.302] (**) evdev: UVC Camera (046d:0825): Device: "/dev/input/event3"
[    29.302] (--) evdev: UVC Camera (046d:0825): Vendor 0x46d Product 0x825
[    29.302] (--) evdev: UVC Camera (046d:0825): Found keys
[    29.302] (II) evdev: UVC Camera (046d:0825): Configuring as keyboard
[    29.302] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.2/usb1/1-7/1-7:1.0/input/input3/event3"
[    29.302] (II) XINPUT: Adding extended input device "UVC Camera (046d:0825)" (type: KEYBOARD, id 8)
[    29.302] (**) Option "xkb_rules" "evdev"
[    29.302] (**) Option "xkb_model" "pc105"
[    29.302] (**) Option "xkb_layout" "si"
[    29.303] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    29.303] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    29.303] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    29.303] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.303] (**) AT Translated Set 2 keyboard: always reports core events
[    29.303] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    29.303] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    29.303] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    29.303] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    29.303] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    29.303] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 9)
[    29.303] (**) Option "xkb_rules" "evdev"
[    29.303] (**) Option "xkb_model" "pc105"
[    29.303] (**) Option "xkb_layout" "si"
[    29.306] (II) config/udev: Adding input device ImExPS/2 Logitech Explorer Mouse (/dev/input/event4)
[    29.306] (**) ImExPS/2 Logitech Explorer Mouse: Applying InputClass "evdev pointer catchall"
[    29.306] (II) Using input driver 'evdev' for 'ImExPS/2 Logitech Explorer Mouse'
[    29.306] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.306] (**) ImExPS/2 Logitech Explorer Mouse: always reports core events
[    29.306] (**) evdev: ImExPS/2 Logitech Explorer Mouse: Device: "/dev/input/event4"
[    29.306] (--) evdev: ImExPS/2 Logitech Explorer Mouse: Vendor 0x2 Product 0x6
[    29.306] (--) evdev: ImExPS/2 Logitech Explorer Mouse: Found 9 mouse buttons
[    29.306] (--) evdev: ImExPS/2 Logitech Explorer Mouse: Found scroll wheel(s)
[    29.306] (--) evdev: ImExPS/2 Logitech Explorer Mouse: Found relative axes
[    29.306] (--) evdev: ImExPS/2 Logitech Explorer Mouse: Found x and y relative axes
[    29.306] (II) evdev: ImExPS/2 Logitech Explorer Mouse: Configuring as mouse
[    29.306] (II) evdev: ImExPS/2 Logitech Explorer Mouse: Adding scrollwheel support
[    29.306] (**) evdev: ImExPS/2 Logitech Explorer Mouse: YAxisMapping: buttons 4 and 5
[    29.306] (**) evdev: ImExPS/2 Logitech Explorer Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    29.306] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input4/event4"
[    29.306] (II) XINPUT: Adding extended input device "ImExPS/2 Logitech Explorer Mouse" (type: MOUSE, id 10)
[    29.306] (II) evdev: ImExPS/2 Logitech Explorer Mouse: initialized for relative axes.
[    29.306] (**) ImExPS/2 Logitech Explorer Mouse: (accel) keeping acceleration scheme 1
[    29.306] (**) ImExPS/2 Logitech Explorer Mouse: (accel) acceleration profile 0
[    29.306] (**) ImExPS/2 Logitech Explorer Mouse: (accel) acceleration factor: 2.000
[    29.306] (**) ImExPS/2 Logitech Explorer Mouse: (accel) acceleration threshold: 4
[    29.307] (II) config/udev: Adding input device ImExPS/2 Logitech Explorer Mouse (/dev/input/mouse0)
[    29.307] (II) No input driver specified, ignoring this device.
[    29.307] (II) This device may have been added with another device file.
[    48.944] (II) RADEON(0): EDID vendor "GSM", prod id 17239
[    48.944] (II) RADEON(0): Using hsync ranges from config file
[    48.944] (II) RADEON(0): Using vrefresh ranges from config file
[    48.944] (II) RADEON(0): Printing DDC gathered Modelines:
[    48.944] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    48.944] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    48.944] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    48.944] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    48.944] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    48.944] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    48.944] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    48.944] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    48.944] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    48.944] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    48.944] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    48.944] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
[    48.944] (II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
[    48.944] (II) RADEON(0): Manufacturer: GSM  Model: 4357  Serial#: 39261
[    48.944] (II) RADEON(0): Year: 2003  Week: 8
[    48.944] (II) RADEON(0): EDID Version: 1.3
[    48.944] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[    48.944] (II) RADEON(0): Sync:  Separate
[    48.944] (II) RADEON(0): Max Image Size [cm]: horiz.: 34  vert.: 27
[    48.944] (II) RADEON(0): Gamma: 2.50
[    48.944] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    48.944] (II) RADEON(0): First detailed timing is preferred mode
[    48.944] (II) RADEON(0): redX: 0.640 redY: 0.340   greenX: 0.290 greenY: 0.610
[    48.944] (II) RADEON(0): blueX: 0.140 blueY: 0.070   whiteX: 0.310 whiteY: 0.330
[    48.944] (II) RADEON(0): Supported established timings:
[    48.944] (II) RADEON(0): 720x400@70Hz
[    48.944] (II) RADEON(0): 640x480@60Hz
[    48.944] (II) RADEON(0): 640x480@75Hz
[    48.944] (II) RADEON(0): 800x600@60Hz
[    48.944] (II) RADEON(0): 800x600@75Hz
[    48.944] (II) RADEON(0): 832x624@75Hz
[    48.944] (II) RADEON(0): 1024x768@60Hz
[    48.944] (II) RADEON(0): 1024x768@75Hz
[    48.944] (II) RADEON(0): 1280x1024@75Hz
[    48.944] (II) RADEON(0): 1152x864@75Hz
[    48.944] (II) RADEON(0): Manufacturer's mask: 0
[    48.945] (II) RADEON(0): Supported standard timings:
[    48.945] (II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    48.945] (II) RADEON(0): #1: hsize: 1024  vsize 768  refresh: 75  vid: 20321
[    48.945] (II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 75  vid: 20293
[    48.945] (II) RADEON(0): #3: hsize: 640  vsize 480  refresh: 75  vid: 20273
[    48.945] (II) RADEON(0): Supported detailed timing:
[    48.945] (II) RADEON(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
[    48.945] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
[    48.945] (II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[    48.945] (II) RADEON(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 145 MHz
[    48.945] (II) RADEON(0): Monitor name: L1710S
[    48.945] (II) RADEON(0): Monitor name: 
[    48.945] (II) RADEON(0): EDID (in hex):
[    48.945] (II) RADEON(0):     00ffffffffffff001e6d57435d990000
[    48.945] (II) RADEON(0):     080d010368221b96eac5c6a3574a9c23
[    48.945] (II) RADEON(0):     124f54a56b808180614f454f314f0101
[    48.945] (II) RADEON(0):     010101010101302a009851002a403070
[    48.945] (II) RADEON(0):     1300520e1100001e000000fd00384b1e
[    48.945] (II) RADEON(0):     530e000a202020202020000000fc004c
[    48.945] (II) RADEON(0):     31373130530a202020202020000000fc
[    48.945] (II) RADEON(0):     00200a202020202020202020202000a1
[    48.945] (II) RADEON(0): EDID vendor "GSM", prod id 17239
[    48.957] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
[    48.957] Unhandled monitor type 0
[    48.957] (II) RADEON(0): Output: S-video, Detected Monitor Type: 0
[   713.936] (II) XKB: reuse xkmfile /var/lib/xkb/server-09C19198E9A4289EFEE844E2AABA985A41656D18.xkm
[  2783.559] [mi] Increasing EQ size to 512 to prevent dropped events.
[  5327.806] disable primary dac
[  5327.856] disable primary dac
[  5627.857] enable primary dac
[  5627.857] disable primary dac
[  5927.729] enable primary dac
[  5927.729] disable primary dac
[ 11152.458] enable primary dac
[ 11756.108] disable primary dac
[ 11756.108] disable primary dac
[ 12056.109] enable primary dac
[ 12056.109] disable primary dac
[ 12356.110] enable primary dac
[ 12356.110] disable primary dac
[ 12816.764] enable primary dac
[ 12945.979] (II) evdev: Power Button: Close
[ 12945.999] (II) UnloadModule: "evdev"
[ 12945.999] (II) Unloading evdev
[ 12945.999] (II) evdev: Power Button: Close
[ 12945.999] (II) UnloadModule: "evdev"
[ 12945.999] (II) Unloading evdev
[ 12945.999] (II) evdev: UVC Camera (046d:0825): Close
[ 12946.000] (II) UnloadModule: "evdev"
[ 12946.000] (II) Unloading evdev
[ 12946.000] (II) evdev: AT Translated Set 2 keyboard: Close
[ 12946.000] (II) UnloadModule: "evdev"
[ 12946.000] (II) Unloading evdev
[ 12946.000] (II) evdev: ImExPS/2 Logitech Explorer Mouse: Close
[ 12946.000] (II) UnloadModule: "evdev"
[ 12946.000] (II) Unloading evdev
[ 12946.080] disable primary dac
[ 12946.080] (II) RADEON(0): RADEONRestoreMemMapRegisters() : 
[ 12946.080] (II) RADEON(0):   MC_FB_LOCATION   : 0x1fff0000 0xefffe800
[ 12946.080] (II) RADEON(0):   MC_AGP_LOCATION  : 0x27ff2000
[ 12946.127] finished PLL2
[ 12946.142] finished PLL1
[ 12946.142] Entering Restore TV
[ 12946.142] Restore TV PLL
[ 12946.144] Restore TVHV
[ 12946.144] Restore TV Restarts
[ 12946.144] Restore Timing Tables
[ 12946.144] Restore TV standard
[ 12946.144] Leaving Restore TV
[ 12946.344]  ddxSigGiveUp: Closing log
[ 12946.345] Server terminated successfully (0). Closing log file.


```

---

### Post by Yellow Pasque on 2014-04-06
```
[    19.027] (II) [KMS] drm report modesetting isn't supported.
```
You're not booting with 'nomodeset' option, are you?

Have you tried a more recent kernel (like lts-saucy) to see if the issue was fixed already?

---

### Post by mastablasta on 2014-04-06
nope. it was anormal install i never added any of the boot options. i will try getting a kernel update to 12.04.4 with hardware enablement stack

i actually wanted to install 13.10, but couldn't boot from USB. but i had a 12.04 CD (or was it DVD) that botoed fine. i will need to test the later kernel first and then do an upgrade. it's just connection over there is relatively slow.

---

### Post by SeijiSensei on 2014-04-06
Looks like you're running the open source ATI driver, not the proprietary one called fglrx.  That's why you get this
```
Failed to load module "fglrx" (module does not exist, 0)
```
Find the "Additional Drivers" application in the Ubuntu menus (I think it's in either "System" or "Settings" in Kubuntu 12.04) and run it.  It should find the proprietary ATI driver and offer to install it.  See if your performance improves.

---

### Post by Yellow Pasque on 2014-04-06
^No. It's a Radeon 9200. Proprietary driver support was dropped a long time ago.

---

### Post by mastablasta on 2014-04-07
oh yeah ATI radeon 9200 128MB - the card is nothing special and preety old (used to have it on win 98). But it is not that crappy. i?ve played plenty of games from 2004 2005 on this mashicne. maybe not maxed out but still playable. And minetest shouldn't be too demanding for this chip. since i know it works on weaker intel chips.

---

### Post by mastablasta on 2014-05-25
i upgraded to 14.04 and still get this:

[B]OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 3.4, 128 bits)
OpenGL version string: 2.1 Mesa 10.1.0[/B]

```
name of display: :0
libGL: screen 0 does not appear to be DRI3 capable
libGL: screen 0 does not appear to be DRI2 capable
libGL: OpenDriver: trying /usr/lib/i386-linux-gnu/dri/tls/swrast_dri.so
libGL: OpenDriver: trying /usr/lib/i386-linux-gnu/dri/swrast_dri.so
libGL: driver does not expose __driDriverGetExtensions_swrast(): /usr/lib/i386-linux-gnu/dri/swrast_dri.so: undefined symbol: __driDriverGetExtensions_swrast
libGL: Can't open configuration file /home/gorjan/.drirc: No such file or directory.
libGL: Can't open configuration file /home/gorjan/.drirc: No such file or directory.
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_make_current_read
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_create_context_robustness, GLX_ARB_fbconfig_float, 
    GLX_ARB_framebuffer_sRGB, GLX_ARB_get_proc_address, GLX_ARB_multisample, 
    GLX_EXT_create_context_es2_profile, GLX_EXT_fbconfig_packed_float, 
    GLX_EXT_framebuffer_sRGB, GLX_EXT_import_context, 
    GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_INTEL_swap_event, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_query_renderer, 
    GLX_MESA_swap_control, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync
GLX version: 1.4
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_multithread_makecurrent, 
    GLX_OML_swap_method, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_make_current_read
OpenGL vendor string: VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 3.4, 128 bits)
OpenGL version string: 2.1 Mesa 10.1.0
OpenGL shading language version string: 1.30
OpenGL extensions:
    GL_AMD_conservative_depth, GL_AMD_draw_buffers_blend, 
    GL_AMD_seamless_cubemap_per_texture, GL_AMD_shader_trinary_minmax, 
    GL_APPLE_packed_pixels, GL_APPLE_vertex_array_object, 
    GL_ARB_ES2_compatibility, GL_ARB_blend_func_extended, 
    GL_ARB_clear_buffer_object, GL_ARB_color_buffer_float, 
    GL_ARB_conservative_depth, GL_ARB_copy_buffer, GL_ARB_debug_output, 
    GL_ARB_depth_buffer_float, GL_ARB_depth_clamp, GL_ARB_depth_texture, 
    GL_ARB_draw_buffers, GL_ARB_draw_buffers_blend, 
    GL_ARB_draw_elements_base_vertex, GL_ARB_draw_instanced, 
    GL_ARB_explicit_attrib_location, GL_ARB_fragment_coord_conventions, 
    GL_ARB_fragment_program, GL_ARB_fragment_program_shadow, 
    GL_ARB_fragment_shader, GL_ARB_framebuffer_object, 
    GL_ARB_framebuffer_sRGB, GL_ARB_get_program_binary, 
    GL_ARB_half_float_pixel, GL_ARB_half_float_vertex, 
    GL_ARB_instanced_arrays, GL_ARB_internalformat_query, 
    GL_ARB_invalidate_subdata, GL_ARB_map_buffer_alignment, 
    GL_ARB_map_buffer_range, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_occlusion_query, GL_ARB_occlusion_query2, 
    GL_ARB_pixel_buffer_object, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_provoking_vertex, GL_ARB_robustness, GL_ARB_sampler_objects, 
    GL_ARB_seamless_cube_map, GL_ARB_shader_bit_encoding, 
    GL_ARB_shader_objects, GL_ARB_shader_texture_lod, 
    GL_ARB_shading_language_100, GL_ARB_shading_language_420pack, 
    GL_ARB_shading_language_packing, GL_ARB_shadow, GL_ARB_sync, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_compression_rgtc, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_float, GL_ARB_texture_mirror_clamp_to_edge, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_texture_rg, GL_ARB_texture_rgb10_a2ui, 
    GL_ARB_texture_storage, GL_ARB_texture_swizzle, GL_ARB_timer_query, 
    GL_ARB_transform_feedback2, GL_ARB_transform_feedback3, 
    GL_ARB_transform_feedback_instanced, GL_ARB_transpose_matrix, 
    GL_ARB_uniform_buffer_object, GL_ARB_vertex_array_bgra, 
    GL_ARB_vertex_array_object, GL_ARB_vertex_attrib_binding, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_vertex_type_10f_11f_11f_rev, GL_ARB_vertex_type_2_10_10_10_rev, 
    GL_ARB_window_pos, GL_ATI_blend_equation_separate, GL_ATI_draw_buffers, 
    GL_ATI_separate_stencil, GL_ATI_texture_compression_3dc, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_float, 
    GL_ATI_texture_mirror_once, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, 
    GL_EXT_copy_texture, GL_EXT_draw_buffers2, GL_EXT_draw_instanced, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_blit, 
    GL_EXT_framebuffer_object, GL_EXT_framebuffer_sRGB, 
    GL_EXT_gpu_program_parameters, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_float, GL_EXT_packed_pixels, 
    GL_EXT_pixel_buffer_object, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_provoking_vertex, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_shadow_funcs, GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_array, GL_EXT_texture_compression_latc, 
    GL_EXT_texture_compression_rgtc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_integer, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, GL_EXT_texture_sRGB_decode, 
    GL_EXT_texture_shared_exponent, GL_EXT_texture_snorm, 
    GL_EXT_texture_swizzle, GL_EXT_timer_query, GL_EXT_transform_feedback, 
    GL_EXT_vertex_array, GL_EXT_vertex_array_bgra, 
    GL_IBM_multimode_draw_arrays, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, GL_KHR_debug, 
    GL_MESA_pack_invert, GL_MESA_texture_signed_rgba, GL_MESA_window_pos, 
    GL_MESA_ycbcr_texture, GL_NV_blend_square, GL_NV_conditional_render, 
    GL_NV_depth_clamp, GL_NV_fog_distance, GL_NV_light_max_exponent, 
    GL_NV_packed_depth_stencil, GL_NV_primitive_restart, 
    GL_NV_texgen_reflection, GL_NV_texture_env_combine4, 
    GL_NV_texture_rectangle, GL_NV_vdpau_interop, GL_OES_EGL_image, 
    GL_OES_read_format, GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays
```

---

