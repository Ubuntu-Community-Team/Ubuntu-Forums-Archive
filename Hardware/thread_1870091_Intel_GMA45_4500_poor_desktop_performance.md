---
title: "Intel GMA45 4500 poor desktop performance"
date: 2011-10-26
forum: Hardware
---

### Post by Bucic on 2011-10-26
Ubuntu 11.10 x64
kernel version 3.1 but on 3.0 it was the same
Thinkpad T500 [http://www.notebookcheck.net/Review-Lenovo-Thinkpad-T500-Notebook.11970.0.html](http://www.notebookcheck.net/Review-Lenovo-Thinkpad-T500-Notebook.11970.0.html)

Unity 3D seems to be running fine and without any stuttering but when I drag windows, scoll the browser window etc. everything is sluggish. Chromium BSU will run blazing fast in that small default window and in full screen + full resolution, but not in a big window.

Some diagnostics
```

~$ glxinfo
name of display: :0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_INTEL_swap_event
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_framebuffer_sRGB, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_multithread_makecurrent, 
    GLX_MESA_swap_control, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap, 
    GLX_INTEL_swap_event
GLX version: 1.4
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_swap_control, 
    GLX_OML_swap_method, GLX_OML_sync_control, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap, GLX_INTEL_swap_event
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Mobile Intel® GM45 Express Chipset 
OpenGL version string: 2.1 Mesa 7.11
OpenGL shading language version string: 1.20
OpenGL extensions:
    GL_ARB_multisample, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_copy_texture, GL_EXT_polygon_offset, GL_EXT_subtexture, 
    GL_EXT_texture_object, GL_EXT_vertex_array, GL_EXT_compiled_vertex_array, 
    GL_EXT_texture, GL_EXT_texture3D, GL_IBM_rasterpos_clip, 
    GL_ARB_point_parameters, GL_EXT_draw_range_elements, GL_EXT_packed_pixels, 
    GL_EXT_point_parameters, GL_EXT_rescale_normal, 
    GL_EXT_separate_specular_color, GL_EXT_texture_edge_clamp, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_ARB_framebuffer_sRGB, 
    GL_ARB_multitexture, GL_EXT_framebuffer_sRGB, 
    GL_IBM_multimode_draw_arrays, GL_IBM_texture_mirrored_repeat, 
    GL_3DFX_texture_compression_FXT1, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_transpose_matrix, 
    GL_EXT_blend_func_separate, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, 
    GL_EXT_secondary_color, GL_EXT_texture_env_add, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_INGR_blend_func_separate, GL_NV_blend_square, GL_NV_light_max_exponent, 
    GL_NV_texgen_reflection, GL_NV_texture_env_combine4, 
    GL_SUN_multi_draw_arrays, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_EXT_framebuffer_object, 
    GL_EXT_texture_env_dot3, GL_MESA_window_pos, GL_NV_packed_depth_stencil, 
    GL_NV_texture_rectangle, GL_NV_vertex_program, GL_ARB_depth_texture, 
    GL_ARB_occlusion_query, GL_ARB_shadow, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_window_pos, GL_ATI_envmap_bumpmap, 
    GL_EXT_stencil_two_side, GL_EXT_texture_cube_map, GL_NV_depth_clamp, 
    GL_NV_vertex_program1_1, GL_APPLE_client_storage, GL_APPLE_packed_pixels, 
    GL_APPLE_vertex_array_object, GL_ARB_draw_buffers, 
    GL_ARB_fragment_program, GL_ARB_fragment_shader, GL_ARB_shader_objects, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ATI_draw_buffers, 
    GL_ATI_texture_env_combine3, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_ARB_depth_clamp, 
    GL_ARB_fragment_program_shadow, GL_ARB_half_float_pixel, 
    GL_ARB_point_sprite, GL_ARB_shading_language_100, GL_ARB_sync, 
    GL_ARB_texture_non_power_of_two, GL_ARB_vertex_buffer_object, 
    GL_ATI_blend_equation_separate, GL_EXT_blend_equation_separate, 
    GL_OES_read_format, GL_ARB_color_buffer_float, GL_ARB_pixel_buffer_object, 
    GL_ARB_texture_compression_rgtc, GL_ARB_texture_rectangle, 
    GL_EXT_pixel_buffer_object, GL_EXT_texture_compression_rgtc, 
    GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, GL_ARB_framebuffer_object, 
    GL_EXT_framebuffer_blit, GL_EXT_framebuffer_multisample, 
    GL_EXT_packed_depth_stencil, GL_APPLE_object_purgeable, 
    GL_ARB_vertex_array_object, GL_ATI_separate_stencil, GL_EXT_draw_buffers2, 
    GL_EXT_gpu_program_parameters, GL_EXT_texture_env_combine, 
    GL_EXT_texture_sRGB_decode, GL_OES_EGL_image, GL_ARB_copy_buffer, 
    GL_ARB_half_float_vertex, GL_ARB_map_buffer_range, GL_ARB_texture_rg, 
    GL_ARB_texture_swizzle, GL_ARB_vertex_array_bgra, 
    GL_EXT_separate_shader_objects, GL_EXT_texture_swizzle, 
    GL_EXT_vertex_array_bgra, GL_NV_conditional_render, 
    GL_ARB_ES2_compatibility, GL_ARB_draw_elements_base_vertex, 
    GL_ARB_explicit_attrib_location, GL_ARB_fragment_coord_conventions, 
    GL_ARB_provoking_vertex, GL_ARB_sampler_objects, GL_ARB_seamless_cube_map, 
    GL_ARB_shader_texture_lod, GL_EXT_provoking_vertex, GL_EXT_texture_snorm, 
    GL_MESA_texture_signed_rgba, GL_ARB_robustness

32 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
.
.
.

48 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
.
.
.

```

---

### Post by Bucic on 2011-10-30
And sometimes this happens...

---

### Post by Bucic on 2011-11-01
A request to mods - please rename the topic (the main title visible outside the topic) to: **Intel GMA 4500M HD poor dekstop performance** or something like that.

---

### Post by Elfy on 2011-11-01
> **Bucic said:**
> A request to mods - please rename the topic (the main title visible outside the topic) to: **Intel GMA 4500M HD poor dekstop performance** or something like that.

reporting as you did is enough :) we see them in the end

---

### Post by Bucic on 2011-11-01
OK, sorry. On some forums reporting does nothing :)

---

