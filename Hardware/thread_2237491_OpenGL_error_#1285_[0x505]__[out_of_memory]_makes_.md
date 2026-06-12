---
title: "OpenGL error #1285 [0x505] : [out of memory] makes Megaglest crash"
date: 2014-08-02
forum: Hardware
---

### Post by Keith_Beef on 2014-08-02
If I start up Megaglest the game crashes after a few minutes. I tried reducing some graphics details (such as particles and rain) but this changes nothing.

Here's what I see when I run the game from the command line.

```
megaglest v3.6.0.3
Compiled using: GNUC: 40602 [64bit] on: Feb 29 2012 04:54:53
SVN: [Rev: ] - using STREFLOP
[2014-07-31 16:23:09] *ERROR* In [game.cpp::mouseDownLeft Line: 1851] Error [OpenGL error #1285 [0x505] : [out of memory] at file: [/build/buildd/megaglest-3.6.0.3/source/shared_lib/sources/graphics/gl/model_renderer_gl.cpp], line: 293]
Error saved to logfile [/home/klrhodes/.megaglest/error.log]
[2014-07-31 16:23:09] *ERROR* In [/build/buildd/megaglest-3.6.0.3/source/glest_game/main/main.cpp::handleRuntimeError Line: 416] [OpenGL error #1285 [0x505] : [out of memory] at file: [/build/buildd/megaglest-3.6.0.3/source/glest_game/graphics/renderer.cpp], line: 3755] gameInitialized = 1, program = 0xc63930
[2014-07-31 16:23:09] *ERROR* In [/build/buildd/megaglest-3.6.0.3/source/glest_game/main/main.cpp::handleRuntimeError Line: 509] [OpenGL error #1285 [0x505] : [out of memory] at file: [/build/buildd/megaglest-3.6.0.3/source/glest_game/graphics/renderer.cpp], line: 3755
Stack Trace:
megaglest:Glest::Game::glestMain(int, char**) address [0x5d9ece] line: 0
megaglest:Glest::Game::glestMainWrapper(int, char**) address [0x5df646] line: 0
/lib/x86_64-linux-gnu/libc.so.6:__libc_start_main() address [0x7fce7800b76d] line: 0
megaglest() [0x4a5839] address [0x4a5839] line: 0
]
megaglest: /build/buildd/megaglest-3.6.0.3/source/shared_lib/sources/graphics/gl/model_renderer_gl.cpp:38: virtual void Shared::Graphics::Gl::ModelRendererGl::begin(bool, bool, bool, Shared::Graphics::MeshCallback*): Assertion `rendering == false' failed.
Aborted (core dumped)
```

Details of my graphics card and drivers.

Card is a GeForce 9800 GTX+
```

glxinfo | grep -i version
server glx version string: 1.4
client glx version string: 1.4
GLX version: 1.4
OpenGL version string: 3.3.0 NVIDIA 331.38
OpenGL shading language version string: 3.30 NVIDIA via Cg compiler
```

List of extensions
[hide]
```
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_swap_control, GLX_EXT_swap_control_tear, 
    GLX_EXT_texture_from_pixmap, GLX_EXT_buffer_age, GLX_ARB_create_context, 
    GLX_ARB_create_context_profile, GLX_EXT_create_context_es_profile, 
    GLX_EXT_create_context_es2_profile, GLX_ARB_create_context_robustness, 
    GLX_ARB_multisample, GLX_NV_float_buffer, GLX_ARB_fbconfig_float, 
    GLX_EXT_framebuffer_sRGB, GLX_NV_multisample_coverage
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_EXT_swap_control, GLX_EXT_swap_control_tear, 
    GLX_EXT_buffer_age, GLX_ARB_create_context, 
    GLX_ARB_create_context_profile, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float, GLX_EXT_fbconfig_packed_float, 
    GLX_EXT_texture_from_pixmap, GLX_EXT_framebuffer_sRGB, 
    GLX_NV_present_video, GLX_NV_copy_image, GLX_NV_multisample_coverage, 
    GLX_NV_video_capture, GLX_EXT_create_context_es_profile, 
    GLX_EXT_create_context_es2_profile, GLX_ARB_create_context_robustness
GLX version: 1.4
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_swap_control, GLX_EXT_swap_control_tear, 
    GLX_EXT_texture_from_pixmap, GLX_EXT_buffer_age, GLX_ARB_create_context, 
    GLX_ARB_create_context_profile, GLX_EXT_create_context_es_profile, 
    GLX_EXT_create_context_es2_profile, GLX_ARB_create_context_robustness, 
    GLX_ARB_multisample, GLX_NV_float_buffer, GLX_ARB_fbconfig_float, 
    GLX_EXT_framebuffer_sRGB, GLX_NV_multisample_coverage, 
    GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 9800 GTX+/PCIe/SSE2
OpenGL version string: 3.3.0 NVIDIA 331.38
OpenGL shading language version string: 3.30 NVIDIA via Cg compiler
OpenGL extensions:
    GL_ARB_arrays_of_arrays, GL_ARB_base_instance, GL_ARB_blend_func_extended, 
    GL_ARB_clear_buffer_object, GL_ARB_color_buffer_float, 
    GL_ARB_compatibility, GL_ARB_compressed_texture_pixel_storage, 
    GL_ARB_conservative_depth, GL_ARB_copy_buffer, GL_ARB_copy_image, 
    GL_ARB_debug_output, GL_ARB_depth_buffer_float, GL_ARB_depth_clamp, 
    GL_ARB_depth_texture, GL_ARB_draw_buffers, 
    GL_ARB_draw_elements_base_vertex, GL_ARB_draw_instanced, 
    GL_ARB_enhanced_layouts, GL_ARB_ES2_compatibility, 
    GL_ARB_ES3_compatibility, GL_ARB_explicit_attrib_location, 
    GL_ARB_explicit_uniform_location, GL_ARB_fragment_coord_conventions, 
    GL_ARB_fragment_layer_viewport, GL_ARB_fragment_program, 
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader, 
    GL_ARB_framebuffer_no_attachments, GL_ARB_framebuffer_object, 
    GL_ARB_framebuffer_sRGB, GL_ARB_geometry_shader4, 
    GL_ARB_get_program_binary, GL_ARB_half_float_pixel, 
    GL_ARB_half_float_vertex, GL_ARB_imaging, GL_ARB_instanced_arrays, 
    GL_ARB_internalformat_query, GL_ARB_internalformat_query2, 
    GL_ARB_invalidate_subdata, GL_ARB_map_buffer_alignment, 
    GL_ARB_map_buffer_range, GL_ARB_multi_bind, GL_ARB_multisample, 
    GL_ARB_multitexture, GL_ARB_occlusion_query, GL_ARB_occlusion_query2, 
    GL_ARB_pixel_buffer_object, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_program_interface_query, GL_ARB_provoking_vertex, 
    GL_ARB_robust_buffer_access_behavior, GL_ARB_robustness, 
    GL_ARB_sampler_objects, GL_ARB_seamless_cube_map, 
    GL_ARB_separate_shader_objects, GL_ARB_shader_bit_encoding, 
    GL_ARB_shader_objects, GL_ARB_shader_texture_lod, 
    GL_ARB_shading_language_100, GL_ARB_shading_language_420pack, 
    GL_ARB_shading_language_include, GL_ARB_shading_language_packing, 
    GL_ARB_shadow, GL_ARB_stencil_texturing, GL_ARB_sync, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_buffer_object, 
    GL_ARB_texture_buffer_range, GL_ARB_texture_compression, 
    GL_ARB_texture_compression_rgtc, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_float, GL_ARB_texture_mirror_clamp_to_edge, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_multisample, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_query_levels, 
    GL_ARB_texture_rectangle, GL_ARB_texture_rg, GL_ARB_texture_rgb10_a2ui, 
    GL_ARB_texture_stencil8, GL_ARB_texture_storage, 
    GL_ARB_texture_storage_multisample, GL_ARB_texture_swizzle, 
    GL_ARB_texture_view, GL_ARB_timer_query, GL_ARB_transpose_matrix, 
    GL_ARB_uniform_buffer_object, GL_ARB_vertex_array_bgra, 
    GL_ARB_vertex_array_object, GL_ARB_vertex_attrib_binding, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_vertex_type_10f_11f_11f_rev, GL_ARB_vertex_type_2_10_10_10_rev, 
    GL_ARB_viewport_array, GL_ARB_window_pos, GL_ATI_draw_buffers, 
    GL_ATI_texture_float, GL_ATI_texture_mirror_once, GL_S3_s3tc, 
    GL_EXT_texture_env_add, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_bindable_uniform, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, 
    GL_EXT_Cg_shader, GL_EXT_depth_bounds_test, GL_EXT_direct_state_access, 
    GL_EXT_draw_buffers2, GL_EXT_draw_instanced, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_blit, GL_EXT_framebuffer_multisample, 
    GL_EXTX_framebuffer_mixed_formats, 
    GL_EXT_framebuffer_multisample_blit_scaled, GL_EXT_framebuffer_object, 
    GL_EXT_framebuffer_sRGB, GL_EXT_geometry_shader4, 
    GL_EXT_gpu_program_parameters, GL_EXT_gpu_shader4, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_depth_stencil, 
    GL_EXT_packed_float, GL_EXT_packed_pixels, GL_EXT_pixel_buffer_object, 
    GL_EXT_point_parameters, GL_EXT_provoking_vertex, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_shader_objects, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_texture3D, 
    GL_EXT_texture_array, GL_EXT_texture_buffer_object, 
    GL_EXT_texture_compression_dxt1, GL_EXT_texture_compression_latc, 
    GL_EXT_texture_compression_rgtc, GL_EXT_texture_compression_s3tc, 
    GL_EXT_texture_cube_map, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_integer, 
    GL_EXT_texture_lod, GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_shared_exponent, 
    GL_EXT_texture_sRGB, GL_EXT_texture_sRGB_decode, GL_EXT_texture_storage, 
    GL_EXT_texture_swizzle, GL_EXT_timer_query, GL_EXT_vertex_array, 
    GL_EXT_vertex_array_bgra, GL_EXT_x11_sync_object, 
    GL_EXT_import_sync_object, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_KHR_debug, GL_KTX_buffer_region, 
    GL_NV_blend_square, GL_NV_conditional_render, GL_NV_copy_depth_to_color, 
    GL_NV_copy_image, GL_NV_depth_buffer_float, GL_NV_depth_clamp, 
    GL_NV_ES1_1_compatibility, GL_NV_explicit_multisample, GL_NV_fence, 
    GL_NV_float_buffer, GL_NV_fog_distance, GL_NV_fragment_program, 
    GL_NV_fragment_program_option, GL_NV_fragment_program2, 
    GL_NV_framebuffer_multisample_coverage, GL_NV_geometry_shader4, 
    GL_NV_gpu_program4, GL_NV_half_float, GL_NV_light_max_exponent, 
    GL_NV_multisample_coverage, GL_NV_multisample_filter_hint, 
    GL_NV_occlusion_query, GL_NV_packed_depth_stencil, 
    GL_NV_parameter_buffer_object, GL_NV_parameter_buffer_object2, 
    GL_NV_path_rendering, GL_NV_pixel_data_range, GL_NV_point_sprite, 
    GL_NV_primitive_restart, GL_NV_register_combiners, 
    GL_NV_register_combiners2, GL_NV_shader_buffer_load, 
    GL_NV_texgen_reflection, GL_NV_texture_barrier, 
    GL_NV_texture_compression_vtc, GL_NV_texture_env_combine4, 
    GL_NV_texture_expand_normal, GL_NV_texture_multisample, 
    GL_NV_texture_rectangle, GL_NV_texture_shader, GL_NV_texture_shader2, 
    GL_NV_texture_shader3, GL_NV_transform_feedback, GL_NV_vdpau_interop, 
    GL_NV_vertex_array_range, GL_NV_vertex_array_range2, 
    GL_NV_vertex_buffer_unified_memory, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_NV_vertex_program2, 
    GL_NV_vertex_program2_option, GL_NV_vertex_program3, 
    GL_NVX_conditional_render, GL_NVX_gpu_memory_info, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SGIX_shadow, GL_SUN_slice_accum
```
[/hide

The Megaglest [ReadMe]("https://raw.githubusercontent.com/MegaGlest/megaglest-source/master/docs/README.txt") states:
> Hardware requirements:
* >= 6th generation x86 CPU with 1.5 GHz or better
  (modern CPU series with at least two cores of at least 1.5 Ghz recommended)
* 1.5 GB RAM
  (2.0 GB RAM recommended)
* Graphics chip supporting OpenGL 1.3 with GL_ARB_env_crossbar and shader
  extensions (=OpenGL 1.4 or glUseProgramObjectARB etc.) or higher
  (dedicated video card with hardware 3D acceleration recommended)
* 256 MB video memory (either dedicated or shared)
* Audio chip supporting OpenAL

Software requirements:
* A supported (by its producer) operating system version
* Graphics drivers which work well with this operating system version and
  support the OpenGL requirements discussed above
* Audio drivers supporting OpenAL
* A file archiving utility which provides a command line interface and can
  decompress 7-zip archives

So, even though I have an OpenGL 3.3.0 server with GLX version 1.4, I don't seem to have the GL_ARB_env_crossbar and GL_ARB_env_shader extensions.

When I look at available additional drivers, there are none more recent than version 331-updates that I am currently using.

So is there a soft solution for this (a software component to add,  wait for the next Ubuntu LTS)? Or am I stuck with shelling out for a new video card? In which case, any recommendations?

---

### Post by Keith_Beef on 2014-08-26
Well, I managed to get hold of a PNY Quadro K2000D card second-hand, for a very reasonable price, and put that in the computer in place of the GTX 9800… but Megaglest still crashes, with the same error.

I tried with the 331 updates driver, and then with the 331 Recommended driver, and both times I had the same problem.

The GLX version is still stuck at 1.4, but the OpenGL version has bumped up to 4.4 and the crossbar and shader extensions seem to be present.

```
$ glxinfo | grep -i version
server glx version string: 1.4
client glx version string: 1.4
GLX version: 1.4
OpenGL version string: 4.4.0 NVIDIA 331.20
OpenGL shading language version string: 4.40 NVIDIA via Cg compiler

$ glxinfo | grep -i crossbar
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3,

$ glxinfo | grep -i shader
    GL_ARB_compute_shader, GL_ARB_compute_variable_group_size, 
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader, 
    GL_ARB_framebuffer_sRGB, GL_ARB_geometry_shader4, 
    GL_ARB_get_program_binary, GL_ARB_gpu_shader5, GL_ARB_gpu_shader_fp64, 
    GL_ARB_seamless_cubemap_per_texture, GL_ARB_separate_shader_objects, 
    GL_ARB_shader_atomic_counters, GL_ARB_shader_bit_encoding, 
    GL_ARB_shader_draw_parameters, GL_ARB_shader_group_vote, 
    GL_ARB_shader_image_load_store, GL_ARB_shader_image_size, 
    GL_ARB_shader_objects, GL_ARB_shader_precision, 
    GL_ARB_query_buffer_object, GL_ARB_shader_storage_buffer_object, 
    GL_ARB_shader_subroutine, GL_ARB_shader_texture_lod, 
    GL_ARB_tessellation_shader, GL_ARB_texture_border_clamp, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_EXT_Cg_shader, GL_EXT_depth_bounds_test, GL_EXT_direct_state_access, 
    GL_EXT_framebuffer_sRGB, GL_EXT_geometry_shader4, 
    GL_EXT_gpu_program_parameters, GL_EXT_gpu_shader4, 
    GL_EXT_secondary_color, GL_EXT_separate_shader_objects, 
    GL_EXT_separate_specular_color, GL_EXT_shader_image_load_store, 
    GL_NV_geometry_shader4, GL_NV_gpu_program4, GL_NV_gpu_program4_1, 
    GL_NV_gpu_program_fp64, GL_NV_gpu_shader5, GL_NV_half_float, 
    GL_NV_shader_atomic_counters, GL_NV_shader_atomic_float, 
    GL_NV_shader_buffer_load, GL_NV_shader_storage_buffer_object, 
    GL_NV_texture_rectangle, GL_NV_texture_shader, GL_NV_texture_shader2, 
    GL_NV_texture_shader3, GL_NV_transform_feedback,
```

---

### Post by tomreyn on 2014-09-02
My understanding is that this [was since solved](https://forum.megaglest.org/index.php?topic=9558.0) (or worked around) on the official MegaGlest forums, which may well be the best suited location for MegaGlest specific issues.  I also think that upgrading to a current game version (but remaining on Ubuntu 12.04) may have helped in this situation. Generally, testing against the latest stable (upstream) release is recommended.

---

