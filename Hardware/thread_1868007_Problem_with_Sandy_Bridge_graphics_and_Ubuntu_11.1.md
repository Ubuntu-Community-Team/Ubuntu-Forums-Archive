---
title: "Problem with Sandy Bridge graphics and Ubuntu 11.10"
date: 2011-10-23
forum: Hardware
---

### Post by arnefm on 2011-10-23
I am having trouble with 3D graphics using the integrated graphics chip in the i7-2600K. Everything was fine until this morning when i tried starting XBMC and the screen turned black. 

I have tried reinstalling Xorg and adding the Xorg Edgers ppa with no luck.

Output from lspci | grep VGA
```
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
```

Output from glxinfo
```
name of display: :0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: Brian Paul
server glx version string: 1.4 Mesa 7.12-devel
server glx extensions:
    GLX_MESA_copy_sub_buffer, GLX_MESA_pixmap_colormap,
    GLX_MESA_release_buffers, GLX_ARB_get_proc_address,
    GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer
client glx vendor string: Brian Paul
client glx version string: 1.4 Mesa 7.12-devel
client glx extensions:
    GLX_MESA_copy_sub_buffer, GLX_MESA_pixmap_colormap,
    GLX_MESA_release_buffers, GLX_ARB_get_proc_address,
    GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer
GLX version: 1.4
GLX extensions:
    GLX_MESA_copy_sub_buffer, GLX_MESA_pixmap_colormap,
    GLX_MESA_release_buffers, GLX_ARB_get_proc_address,
    GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer
OpenGL vendor string: Brian Paul
OpenGL renderer string: Mesa X11
OpenGL version string: 2.1 Mesa 7.12-devel
OpenGL shading language version string: 1.20
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
    GL_SGIS_texture_lod, GL_ARB_multitexture, GL_IBM_multimode_draw_arrays,
    GL_IBM_texture_mirrored_repeat, GL_3DFX_texture_compression_FXT1,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, GL_ARB_transpose_matrix,
    GL_EXT_blend_func_separate, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays,
    GL_EXT_secondary_color, GL_EXT_texture_env_add,
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias,
    GL_INGR_blend_func_separate, GL_MESA_resize_buffers, GL_NV_blend_square,
    GL_NV_light_max_exponent, GL_NV_texgen_reflection,
    GL_NV_texture_env_combine4, GL_SUN_multi_draw_arrays,
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression,
    GL_EXT_framebuffer_object, GL_EXT_texture_env_combine,
    GL_EXT_texture_env_dot3, GL_MESA_window_pos, GL_NV_packed_depth_stencil,
    GL_NV_texture_rectangle, GL_NV_vertex_program, GL_ARB_depth_texture,
    GL_ARB_occlusion_query, GL_ARB_shadow, GL_ARB_shadow_ambient,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar,
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat,
    GL_ARB_window_pos, GL_ATI_envmap_bumpmap, GL_ATI_fragment_shader,
    GL_EXT_stencil_two_side, GL_EXT_texture_cube_map, GL_NV_depth_clamp,
    GL_NV_fragment_program, GL_NV_point_sprite, GL_NV_vertex_program1_1,
    GL_APPLE_packed_pixels, GL_APPLE_vertex_array_object, GL_ARB_draw_buffers,
    GL_ARB_fragment_program, GL_ARB_fragment_shader, GL_ARB_shader_objects,
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ATI_draw_buffers,
    GL_ATI_texture_env_combine3, GL_EXT_depth_bounds_test,
    GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, GL_MESA_pack_invert,
    GL_MESA_ycbcr_texture, GL_ARB_depth_clamp, GL_ARB_fragment_program_shadow,
    GL_ARB_half_float_pixel, GL_ARB_occlusion_query2, GL_ARB_point_sprite,
    GL_ARB_shading_language_100, GL_ARB_sync, GL_ARB_texture_non_power_of_two,
    GL_ARB_vertex_buffer_object, GL_ATI_blend_equation_separate,
    GL_EXT_blend_equation_separate, GL_OES_read_format,
    GL_ARB_pixel_buffer_object, GL_ARB_texture_compression_rgtc,
    GL_ARB_texture_rectangle, GL_ATI_texture_compression_3dc,
    GL_EXT_pixel_buffer_object, GL_EXT_texture_compression_rgtc,
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_rectangle,
    GL_EXT_texture_sRGB, GL_EXT_texture_shared_exponent,
    GL_ARB_framebuffer_object, GL_EXT_framebuffer_blit,
    GL_EXT_framebuffer_multisample, GL_EXT_packed_depth_stencil,
    GL_NV_fragment_program_option, GL_APPLE_object_purgeable,
    GL_ARB_vertex_array_object, GL_ATI_separate_stencil,
    GL_ATI_texture_mirror_once, GL_EXT_draw_buffers2, GL_EXT_draw_instanced,
    GL_EXT_gpu_program_parameters, GL_EXT_texture_array,
    GL_EXT_texture_compression_latc, GL_EXT_texture_sRGB_decode,
    GL_EXT_timer_query, GL_MESA_texture_array, GL_ARB_copy_buffer,
    GL_ARB_draw_instanced, GL_ARB_half_float_vertex, GL_ARB_map_buffer_range,
    GL_ARB_texture_rg, GL_ARB_texture_swizzle, GL_ARB_vertex_array_bgra,
    GL_EXT_separate_shader_objects, GL_EXT_texture_swizzle,
    GL_EXT_vertex_array_bgra, GL_NV_conditional_render,
    GL_ARB_draw_elements_base_vertex, GL_ARB_explicit_attrib_location,
    GL_ARB_fragment_coord_conventions, GL_ARB_provoking_vertex,
    GL_EXT_provoking_vertex, GL_ARB_robustness

32 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x021 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x022 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x093 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x094 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x095 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x096 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x097 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x098 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x099 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x09a 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x09b 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x09c 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x09d 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x09e 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x09f 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x0a0 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x0a1 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x0a2 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x0a3 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x0a4 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x0a5 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x0a6 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x0a7 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x0a8 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x0a9 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x0aa 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x0ab 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x0ac 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x0ad 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x0ae 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x0af 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x062 32 tc  0  32  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16  0  0 0 None

32 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x021 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x022 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x093 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x094 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x095 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x096 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x097 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x098 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x099 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x09a 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x09b 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x09c 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x09d 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x09e 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x09f 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x0a0 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x0a1 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x0a2 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x0a3 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x0a4 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x0a5 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x0a6 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x0a7 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x0a8 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x0a9 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x0aa 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x0ab 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x0ac 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x0ad 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x0ae 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x0af 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
0x062 32 tc  0  32  0 r  y .   8  8  8  0 .  .  0 16  8 16 16 16 16  0 0 None
```

As far as I can tell the wrong driver is being used. How can I specify that I want to use the Intel driver?

---

