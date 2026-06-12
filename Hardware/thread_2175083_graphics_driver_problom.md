---
title: "graphics driver problom"
date: 2013-09-17
forum: Hardware
---

### Post by Sanocon on 2013-09-17
so ive been trying to get glsl running but i can't. i've searched on the internet for days but i didn't get a clear result.

to get things going here's what i have for specs and progress

the graphics chip is an Nvidia 740m with optimus technology and i'm running 64-bit ubuntu 13.04

Fresh install
```
sudo apt-get update
sudo apt-get upgrade
```
i installed bumblebee via terminal
reboot
```
sudo apt-get install nvidia-current
```which was already installed.
```
sudo apt-get install nvidia-current-updates
```
reboot
ran the update and upgrade command just to be safe.
note: there are three packages that were held back. do these have to do whith the glsl problom and if not what do they do anyways?
```
The following packages have been kept back:
  python3-distupgrade ubuntu-release-upgrader-core ubuntu-release-upgrader-gtk
```
so is there something i'm missing or are there bugs? also to note nothing shows up on the drivers tabs in the ubuntu software center options

---

### Post by Yellow Pasque on 2013-09-17
> so ive been trying to get glsl running but i can't
Be more specific. What exactly are you trying to do with glsl? Write a program? Run a game? And what happens when you do so? Does glxinfo give expected results?
```
glxinfo
optirun glxinfo
```

> also to note nothing shows up on the drivers tabs in the ubuntu software center options 
That's expected.

---

### Post by Sanocon on 2013-09-17
I'm trying to run a game and ill eventually be makeing a game with blender with glsl scripts. And btw what messege should I exspect from the glx info?

---

### Post by Yellow Pasque on 2013-09-17
'glxinfo' should tell you that it's using the Intel Mesa/DRI driver and 'optirun glxinfo' should tell you its using the nvidia driver. If glxinfo says you're using "software rendering" or "llvmpipe" driver, then it should raise a red flag.

> I'm trying to run a game
...
> Be more specific... What happens when you do so?

---

### Post by Sanocon on 2013-09-17
the game (kerbal space program) i'm running uses glsl advanced shading. and after running glxinfo in the terminal it is not installed, should i install mesa-utils since it wants that program?

---

### Post by Yellow Pasque on 2013-09-17
> and after running glxinfo in the terminal it is not installed, should i install mesa-utils since it wants that program? 
Yes.

> the game (kerbal space program) i'm running uses glsl advanced shading
Are you running the game with optirun? Does the game give you an error message or does something else happen?

---

### Post by Sanocon on 2013-09-17
the thing automaticly runs optirun when i start the program but i ran optirun glx info and i got this:
```
[ 3513.922101] [ERROR]Cannot access secondary GPU - error: Could not load GPU driver

[ 3513.922139] [ERROR]Aborting because fallback start is disabled.
```

---

### Post by Yellow Pasque on 2013-09-17
I'm kind of confused on why you installed bumblebee and then installed nvidia-current and nvidia-current-updates. :?
Anyway, make sure you're using nvidia driver >= 319.17, as that's the first version to support your GPU.

---

### Post by Sanocon on 2013-09-18
Everything is in the green now. But do I need to run linux executables with optirun via terminal or will bumblebee decide to use the graphics card on it's own. Because glxinfo says glsl is working but no advanced shaders show in the game. I'm using the 325 driver by the way.

---

### Post by Yellow Pasque on 2013-09-18
You need to manually invoke optirun. Bumblebee is not meant for auto-switching.

---

### Post by Sanocon on 2013-09-18
Question. Does optirun activate just the driver or activate the video card all together?

---

### Post by Yellow Pasque on 2013-09-18
I'm not sure what you mean. The driver is loaded at boot. The bbswitch program is what turns the nvidia card on/off as needed (and turns it on when you use optirun).

---

### Post by Sanocon on 2013-09-18
so there is an automatic switch. It's just optirun forces to run the video card. Also to clear things up, my card can suport opengl 4.4, aka the latest. So why is glsl not working then? I read nvidia has a beta driver for 4.4, but now that leads to more probloms. I got the nvida driver from xorg, but the nvidia beta driver is from, well nvidia, do I need to do some things to switch to from xorg to the offical driver?

---

### Post by Yellow Pasque on 2013-09-18
> so there is an automatic switch.
No, an "automatic switch" would enable the nvidia card when there's a high graphics load, and switch it off when not, and that process would be completely transparent to the user, who wouldn't even realize that s/he has two graphics cards. Indeed, that is the case on Windows, but not on Linux when using the bumblebee/optirun/bbswitch approach.

> So why is glsl not working then?
If your drivers are now working correctly, then you'll probably have more luck with that question on the kerbal space forums than you will here.

---

### Post by Sanocon on 2013-09-18
Ok this isn't just kerbal space program. Glsl is not working in blender also. And I've used the app for 5 years. So this is deffently a driver problom. Also the glxinfo says its using opengl 4.3 when it should be 4.4 also intel's opengl is 3.0 is that ok?

---

### Post by Yellow Pasque on 2013-09-18
> intel's opengl is 3.0 is that ok?
Yes, that is what the opensource drivers support right now.

> Ok this isn't just kerbal space program. Glsl is not working in blender also.
How do you know that glsl is causing your issues? You're the first non-programmer user I've ever heard claim that his/her glsl was broken...

---

### Post by Sanocon on 2013-09-18
blender's glsl game mode is activated properly if in texture mode.(basicaly 'final product' mode) if you run in solid mode (showing the models without the textures) you get nothing but pure white, not even basic shading is active. this showed the exact same result in texture mode for me. and fyi the blender version is stable, 2.66.1 kerbal space program shuts the glsl off altogether. i accidently ran kerbal space program without a driver on another computer i have. (the 3d and basic shading worked, but the glsl didn't)

---

### Post by Sanocon on 2013-09-18
ok i should have done this a long time ago. here's what optirun glx info says.

```
sanocon@sanocon-Satellite-P50-A:~$ optirun glxinfo
name of display: :0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: VirtualGL
server glx version string: 1.4
server glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_make_current_read, GLX_SUN_get_transparent_index
client glx vendor string: VirtualGL
client glx version string: 1.4
client glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_make_current_read, GLX_SUN_get_transparent_index
GLX version: 1.4
GLX extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_make_current_read, GLX_SUN_get_transparent_index
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce GT 740M/PCIe/SSE2
OpenGL core profile version string: 4.3.0 NVIDIA 325.15
OpenGL core profile shading language version string: 4.30 NVIDIA via Cg compiler
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
    GL_AMD_multi_draw_indirect, GL_AMD_seamless_cubemap_per_texture, 
    GL_ARB_ES2_compatibility, GL_ARB_ES3_compatibility, 
    GL_ARB_arrays_of_arrays, GL_ARB_base_instance, GL_ARB_blend_func_extended, 
    GL_ARB_clear_buffer_object, GL_ARB_color_buffer_float, 
    GL_ARB_compressed_texture_pixel_storage, GL_ARB_compute_shader, 
    GL_ARB_conservative_depth, GL_ARB_copy_buffer, GL_ARB_copy_image, 
    GL_ARB_debug_output, GL_ARB_depth_buffer_float, GL_ARB_depth_clamp, 
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_draw_buffers_blend, 
    GL_ARB_draw_elements_base_vertex, GL_ARB_draw_indirect, 
    GL_ARB_draw_instanced, GL_ARB_explicit_attrib_location, 
    GL_ARB_explicit_uniform_location, GL_ARB_fragment_coord_conventions, 
    GL_ARB_fragment_layer_viewport, GL_ARB_fragment_program, 
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader, 
    GL_ARB_framebuffer_no_attachments, GL_ARB_framebuffer_object, 
    GL_ARB_framebuffer_sRGB, GL_ARB_geometry_shader4, 
    GL_ARB_get_program_binary, GL_ARB_gpu_shader5, GL_ARB_gpu_shader_fp64, 
    GL_ARB_half_float_pixel, GL_ARB_half_float_vertex, GL_ARB_imaging, 
    GL_ARB_instanced_arrays, GL_ARB_internalformat_query, 
    GL_ARB_internalformat_query2, GL_ARB_invalidate_subdata, 
    GL_ARB_map_buffer_alignment, GL_ARB_map_buffer_range, 
    GL_ARB_multi_draw_indirect, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_occlusion_query, GL_ARB_occlusion_query2, 
    GL_ARB_pixel_buffer_object, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_program_interface_query, GL_ARB_provoking_vertex, 
    GL_ARB_robust_buffer_access_behavior, GL_ARB_robustness, 
    GL_ARB_sample_shading, GL_ARB_sampler_objects, GL_ARB_seamless_cube_map, 
    GL_ARB_separate_shader_objects, GL_ARB_shader_atomic_counters, 
    GL_ARB_shader_bit_encoding, GL_ARB_shader_image_load_store, 
    GL_ARB_shader_image_size, GL_ARB_shader_objects, GL_ARB_shader_precision, 
    GL_ARB_shader_storage_buffer_object, GL_ARB_shader_subroutine, 
    GL_ARB_shader_texture_lod, GL_ARB_shading_language_100, 
    GL_ARB_shading_language_420pack, GL_ARB_shading_language_include, 
    GL_ARB_shading_language_packing, GL_ARB_shadow, GL_ARB_stencil_texturing, 
    GL_ARB_sync, GL_ARB_tessellation_shader, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_buffer_object, GL_ARB_texture_buffer_object_rgb32, 
    GL_ARB_texture_buffer_range, GL_ARB_texture_compression, 
    GL_ARB_texture_compression_bptc, GL_ARB_texture_compression_rgtc, 
    GL_ARB_texture_cube_map, GL_ARB_texture_cube_map_array, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_float, GL_ARB_texture_gather, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_multisample, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_query_levels, 
    GL_ARB_texture_query_lod, GL_ARB_texture_rectangle, GL_ARB_texture_rg, 
    GL_ARB_texture_rgb10_a2ui, GL_ARB_texture_storage, 
    GL_ARB_texture_storage_multisample, GL_ARB_texture_swizzle, 
    GL_ARB_texture_view, GL_ARB_timer_query, GL_ARB_transform_feedback2, 
    GL_ARB_transform_feedback3, GL_ARB_transform_feedback_instanced, 
    GL_ARB_transpose_matrix, GL_ARB_uniform_buffer_object, 
    GL_ARB_vertex_array_bgra, GL_ARB_vertex_array_object, 
    GL_ARB_vertex_attrib_64bit, GL_ARB_vertex_attrib_binding, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_vertex_type_2_10_10_10_rev, GL_ARB_viewport_array, 
    GL_ARB_window_pos, GL_ATI_draw_buffers, GL_ATI_texture_float, 
    GL_ATI_texture_mirror_once, GL_EXTX_framebuffer_mixed_formats, 
    GL_EXT_Cg_shader, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_bindable_uniform, 
    GL_EXT_blend_color, GL_EXT_blend_equation_separate, 
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_compiled_vertex_array, GL_EXT_depth_bounds_test, 
    GL_EXT_direct_state_access, GL_EXT_draw_buffers2, GL_EXT_draw_instanced, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_blit, 
    GL_EXT_framebuffer_multisample, GL_EXT_framebuffer_multisample_blit_scaled, 
    GL_EXT_framebuffer_object, GL_EXT_framebuffer_sRGB, 
    GL_EXT_geometry_shader4, GL_EXT_gpu_program_parameters, 
    GL_EXT_gpu_shader4, GL_EXT_import_sync_object, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_float, GL_EXT_packed_pixels, 
    GL_EXT_pixel_buffer_object, GL_EXT_point_parameters, 
    GL_EXT_provoking_vertex, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_shader_objects, GL_EXT_separate_specular_color, 
    GL_EXT_shader_image_load_store, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_texture3D, 
    GL_EXT_texture_array, GL_EXT_texture_buffer_object, 
    GL_EXT_texture_compression_dxt1, GL_EXT_texture_compression_latc, 
    GL_EXT_texture_compression_rgtc, GL_EXT_texture_compression_s3tc, 
    GL_EXT_texture_cube_map, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_integer, GL_EXT_texture_lod, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, GL_EXT_texture_sRGB, 
    GL_EXT_texture_sRGB_decode, GL_EXT_texture_shared_exponent, 
    GL_EXT_texture_storage, GL_EXT_texture_swizzle, GL_EXT_timer_query, 
    GL_EXT_transform_feedback2, GL_EXT_vertex_array, GL_EXT_vertex_array_bgra, 
    GL_EXT_vertex_attrib_64bit, GL_EXT_x11_sync_object, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_KHR_debug, GL_KTX_buffer_region, 
    GL_NVX_conditional_render, GL_NVX_gpu_memory_info, GL_NVX_nvenc_interop, 
    GL_NV_ES1_1_compatibility, GL_NV_bindless_multi_draw_indirect, 
    GL_NV_bindless_texture, GL_NV_blend_square, GL_NV_compute_program5, 
    GL_NV_conditional_render, GL_NV_copy_depth_to_color, GL_NV_copy_image, 
    GL_NV_depth_buffer_float, GL_NV_depth_clamp, GL_NV_draw_texture, 
    GL_NV_explicit_multisample, GL_NV_fence, GL_NV_float_buffer, 
    GL_NV_fog_distance, GL_NV_fragment_program, GL_NV_fragment_program2, 
    GL_NV_fragment_program_option, GL_NV_framebuffer_multisample_coverage, 
    GL_NV_geometry_shader4, GL_NV_gpu_program4, GL_NV_gpu_program4_1, 
    GL_NV_gpu_program5, GL_NV_gpu_program5_mem_extended, 
    GL_NV_gpu_program_fp64, GL_NV_gpu_shader5, GL_NV_half_float, 
    GL_NV_light_max_exponent, GL_NV_multisample_coverage, 
    GL_NV_multisample_filter_hint, GL_NV_occlusion_query, 
    GL_NV_packed_depth_stencil, GL_NV_parameter_buffer_object, 
    GL_NV_parameter_buffer_object2, GL_NV_path_rendering, 
    GL_NV_pixel_data_range, GL_NV_point_sprite, GL_NV_primitive_restart, 
    GL_NV_register_combiners, GL_NV_register_combiners2, 
    GL_NV_shader_atomic_counters, GL_NV_shader_atomic_float, 
    GL_NV_shader_buffer_load, GL_NV_shader_storage_buffer_object, 
    GL_NV_texgen_reflection, GL_NV_texture_barrier, 
    GL_NV_texture_compression_vtc, GL_NV_texture_env_combine4, 
    GL_NV_texture_expand_normal, GL_NV_texture_multisample, 
    GL_NV_texture_rectangle, GL_NV_texture_shader, GL_NV_texture_shader2, 
    GL_NV_texture_shader3, GL_NV_transform_feedback, 
    GL_NV_transform_feedback2, GL_NV_vdpau_interop, GL_NV_vertex_array_range, 
    GL_NV_vertex_array_range2, GL_NV_vertex_attrib_integer_64bit, 
    GL_NV_vertex_buffer_unified_memory, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_NV_vertex_program2, 
    GL_NV_vertex_program2_option, GL_NV_vertex_program3, GL_S3_s3tc, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SGIX_shadow, GL_SUN_slice_accum

OpenGL version string: 4.3.0 NVIDIA 325.15
OpenGL shading language version string: 4.30 NVIDIA via Cg compiler
OpenGL context flags: (none)
OpenGL profile mask: (none)
OpenGL extensions:
    GL_AMD_multi_draw_indirect, GL_AMD_seamless_cubemap_per_texture, 
    GL_ARB_ES2_compatibility, GL_ARB_ES3_compatibility, 
    GL_ARB_arrays_of_arrays, GL_ARB_base_instance, GL_ARB_blend_func_extended, 
    GL_ARB_clear_buffer_object, GL_ARB_color_buffer_float, 
    GL_ARB_compatibility, GL_ARB_compressed_texture_pixel_storage, 
    GL_ARB_compute_shader, GL_ARB_conservative_depth, GL_ARB_copy_buffer, 
    GL_ARB_copy_image, GL_ARB_debug_output, GL_ARB_depth_buffer_float, 
    GL_ARB_depth_clamp, GL_ARB_depth_texture, GL_ARB_draw_buffers, 
    GL_ARB_draw_buffers_blend, GL_ARB_draw_elements_base_vertex, 
    GL_ARB_draw_indirect, GL_ARB_draw_instanced, 
    GL_ARB_explicit_attrib_location, GL_ARB_explicit_uniform_location, 
    GL_ARB_fragment_coord_conventions, GL_ARB_fragment_layer_viewport, 
    GL_ARB_fragment_program, GL_ARB_fragment_program_shadow, 
    GL_ARB_fragment_shader, GL_ARB_framebuffer_no_attachments, 
    GL_ARB_framebuffer_object, GL_ARB_framebuffer_sRGB, 
    GL_ARB_geometry_shader4, GL_ARB_get_program_binary, GL_ARB_gpu_shader5, 
    GL_ARB_gpu_shader_fp64, GL_ARB_half_float_pixel, GL_ARB_half_float_vertex, 
    GL_ARB_imaging, GL_ARB_instanced_arrays, GL_ARB_internalformat_query, 
    GL_ARB_internalformat_query2, GL_ARB_invalidate_subdata, 
    GL_ARB_map_buffer_alignment, GL_ARB_map_buffer_range, 
    GL_ARB_multi_draw_indirect, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_occlusion_query, GL_ARB_occlusion_query2, 
    GL_ARB_pixel_buffer_object, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_program_interface_query, GL_ARB_provoking_vertex, 
    GL_ARB_robust_buffer_access_behavior, GL_ARB_robustness, 
    GL_ARB_sample_shading, GL_ARB_sampler_objects, GL_ARB_seamless_cube_map, 
    GL_ARB_separate_shader_objects, GL_ARB_shader_atomic_counters, 
    GL_ARB_shader_bit_encoding, GL_ARB_shader_image_load_store, 
    GL_ARB_shader_image_size, GL_ARB_shader_objects, GL_ARB_shader_precision, 
    GL_ARB_shader_storage_buffer_object, GL_ARB_shader_subroutine, 
    GL_ARB_shader_texture_lod, GL_ARB_shading_language_100, 
    GL_ARB_shading_language_420pack, GL_ARB_shading_language_include, 
    GL_ARB_shading_language_packing, GL_ARB_shadow, GL_ARB_stencil_texturing, 
    GL_ARB_sync, GL_ARB_tessellation_shader, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_buffer_object, GL_ARB_texture_buffer_object_rgb32, 
    GL_ARB_texture_buffer_range, GL_ARB_texture_compression, 
    GL_ARB_texture_compression_bptc, GL_ARB_texture_compression_rgtc, 
    GL_ARB_texture_cube_map, GL_ARB_texture_cube_map_array, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_float, GL_ARB_texture_gather, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_multisample, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_query_levels, 
    GL_ARB_texture_query_lod, GL_ARB_texture_rectangle, GL_ARB_texture_rg, 
    GL_ARB_texture_rgb10_a2ui, GL_ARB_texture_storage, 
    GL_ARB_texture_storage_multisample, GL_ARB_texture_swizzle, 
    GL_ARB_texture_view, GL_ARB_timer_query, GL_ARB_transform_feedback2, 
    GL_ARB_transform_feedback3, GL_ARB_transform_feedback_instanced, 
    GL_ARB_transpose_matrix, GL_ARB_uniform_buffer_object, 
    GL_ARB_vertex_array_bgra, GL_ARB_vertex_array_object, 
    GL_ARB_vertex_attrib_64bit, GL_ARB_vertex_attrib_binding, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_vertex_type_2_10_10_10_rev, GL_ARB_viewport_array, 
    GL_ARB_window_pos, GL_ATI_draw_buffers, GL_ATI_texture_float, 
    GL_ATI_texture_mirror_once, GL_EXTX_framebuffer_mixed_formats, 
    GL_EXT_Cg_shader, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_bindable_uniform, 
    GL_EXT_blend_color, GL_EXT_blend_equation_separate, 
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_compiled_vertex_array, GL_EXT_depth_bounds_test, 
    GL_EXT_direct_state_access, GL_EXT_draw_buffers2, GL_EXT_draw_instanced, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_blit, 
    GL_EXT_framebuffer_multisample, GL_EXT_framebuffer_multisample_blit_scaled, 
    GL_EXT_framebuffer_object, GL_EXT_framebuffer_sRGB, 
    GL_EXT_geometry_shader4, GL_EXT_gpu_program_parameters, 
    GL_EXT_gpu_shader4, GL_EXT_import_sync_object, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_float, GL_EXT_packed_pixels, 
    GL_EXT_pixel_buffer_object, GL_EXT_point_parameters, 
    GL_EXT_provoking_vertex, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_shader_objects, GL_EXT_separate_specular_color, 
    GL_EXT_shader_image_load_store, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_texture3D, 
    GL_EXT_texture_array, GL_EXT_texture_buffer_object, 
    GL_EXT_texture_compression_dxt1, GL_EXT_texture_compression_latc, 
    GL_EXT_texture_compression_rgtc, GL_EXT_texture_compression_s3tc, 
    GL_EXT_texture_cube_map, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_integer, GL_EXT_texture_lod, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, GL_EXT_texture_sRGB, 
    GL_EXT_texture_sRGB_decode, GL_EXT_texture_shared_exponent, 
    GL_EXT_texture_storage, GL_EXT_texture_swizzle, GL_EXT_timer_query, 
    GL_EXT_transform_feedback2, GL_EXT_vertex_array, GL_EXT_vertex_array_bgra, 
    GL_EXT_vertex_attrib_64bit, GL_EXT_x11_sync_object, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_KHR_debug, GL_KTX_buffer_region, 
    GL_NVX_conditional_render, GL_NVX_gpu_memory_info, GL_NVX_nvenc_interop, 
    GL_NV_ES1_1_compatibility, GL_NV_bindless_multi_draw_indirect, 
    GL_NV_bindless_texture, GL_NV_blend_square, GL_NV_compute_program5, 
    GL_NV_conditional_render, GL_NV_copy_depth_to_color, GL_NV_copy_image, 
    GL_NV_depth_buffer_float, GL_NV_depth_clamp, GL_NV_draw_texture, 
    GL_NV_explicit_multisample, GL_NV_fence, GL_NV_float_buffer, 
    GL_NV_fog_distance, GL_NV_fragment_program, GL_NV_fragment_program2, 
    GL_NV_fragment_program_option, GL_NV_framebuffer_multisample_coverage, 
    GL_NV_geometry_shader4, GL_NV_gpu_program4, GL_NV_gpu_program4_1, 
    GL_NV_gpu_program5, GL_NV_gpu_program5_mem_extended, 
    GL_NV_gpu_program_fp64, GL_NV_gpu_shader5, GL_NV_half_float, 
    GL_NV_light_max_exponent, GL_NV_multisample_coverage, 
    GL_NV_multisample_filter_hint, GL_NV_occlusion_query, 
    GL_NV_packed_depth_stencil, GL_NV_parameter_buffer_object, 
    GL_NV_parameter_buffer_object2, GL_NV_path_rendering, 
    GL_NV_pixel_data_range, GL_NV_point_sprite, GL_NV_primitive_restart, 
    GL_NV_register_combiners, GL_NV_register_combiners2, 
    GL_NV_shader_atomic_counters, GL_NV_shader_atomic_float, 
    GL_NV_shader_buffer_load, GL_NV_shader_storage_buffer_object, 
    GL_NV_texgen_reflection, GL_NV_texture_barrier, 
    GL_NV_texture_compression_vtc, GL_NV_texture_env_combine4, 
    GL_NV_texture_expand_normal, GL_NV_texture_multisample, 
    GL_NV_texture_rectangle, GL_NV_texture_shader, GL_NV_texture_shader2, 
    GL_NV_texture_shader3, GL_NV_transform_feedback, 
    GL_NV_transform_feedback2, GL_NV_vdpau_interop, GL_NV_vertex_array_range, 
    GL_NV_vertex_array_range2, GL_NV_vertex_attrib_integer_64bit, 
    GL_NV_vertex_buffer_unified_memory, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_NV_vertex_program2, 
    GL_NV_vertex_program2_option, GL_NV_vertex_program3, GL_S3_s3tc, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SGIX_shadow, GL_SUN_slice_accum

10 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x020 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x089 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x08a 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x08b 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x08c 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x08d 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x08e 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x08f 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x090 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x05c 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None

311 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x105 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  0 0 None
0x106 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  0 0 Ncon
0x107 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  0 0 None
0x108 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  0 0 Ncon
0x109 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  0 0 None
0x10a 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  0 0 Ncon
0x10b 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  0 0 None
0x10c 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  0 0 Ncon
0x10d 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x10e 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 Ncon
0x10f 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  0 0 None
0x110 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  0 0 Ncon
0x111 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x112 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 Ncon
0x113 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  0 0 None
0x114 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  0 0 Ncon
0x115 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4  0  0 16 16 16 16  0 0 None
0x116 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4  0  0 16 16 16 16  0 0 Ncon
0x117 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4  0  0 16 16 16 16  0 0 None
0x118 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4  0  0 16 16 16 16  0 0 Ncon
0x119 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4  0  0 16 16 16 16  0 0 None
0x11a 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4  0  0 16 16 16 16  0 0 Ncon
0x11b 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4  0  0 16 16 16 16  0 0 None
0x11c 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4  0  0 16 16 16 16  0 0 Ncon
0x11d 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x11e 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x11f 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x120 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x121 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x122 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x123 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x124 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x125 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x126 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x127 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x128 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x129 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x12a 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x12b 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x12c 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x12d 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x12e 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x12f 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x130 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x131 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x132 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x133 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x134 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x135 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x136 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x137 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x138 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x139 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x13a 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x13b 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x13c 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x13d 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  8 1 Ncon
0x13e 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  8 1 Ncon
0x13f 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  8 1 Ncon
0x140 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  8 1 Ncon
0x141 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16 16 1 Ncon
0x142 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16 16 1 Ncon
0x143 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16 16 1 Ncon
0x144 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16 16 1 Ncon
0x145 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  8 1 Ncon
0x146 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  8 1 Ncon
0x147 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  8 1 Ncon
0x148 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  8 1 Ncon
0x149 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16 16 1 Ncon
0x14a 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16 16 1 Ncon
0x14b 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16 16 1 Ncon
0x14c 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16 16 1 Ncon
0x14d 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  8 1 Ncon
0x14e 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  8 1 Ncon
0x14f 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  8 1 Ncon
0x150 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  8 1 Ncon
0x151 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16 16 1 Ncon
0x152 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16 16 1 Ncon
0x153 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16 16 1 Ncon
0x154 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16 16 1 Ncon
0x155 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  8 1 Ncon
0x156 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  8 1 Ncon
0x157 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  8 1 Ncon
0x158 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  8 1 Ncon
0x159 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16 16 1 Ncon
0x15a 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16 16 1 Ncon
0x15b 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16 16 1 Ncon
0x15c 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16 16 1 Ncon
0x15d 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  8 1 Ncon
0x15e 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  8 1 Ncon
0x15f 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  8 1 Ncon
0x160 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  8 1 Ncon
0x161 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16 16 1 Ncon
0x162 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16 16 1 Ncon
0x163 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16 16 1 Ncon
0x164 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16 16 1 Ncon
0x165 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16 16 1 Ncon
0x166 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16 16 1 Ncon
0x167 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16 16 1 Ncon
0x168 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16 16 1 Ncon
0x169 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  8 1 Ncon
0x16a 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  8 1 Ncon
0x16b 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  8 1 Ncon
0x16c 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  8 1 Ncon
0x16d 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16 16 1 Ncon
0x16e 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16 16 1 Ncon
0x16f 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16 16 1 Ncon
0x170 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16 16 1 Ncon
0x171 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16 16 1 Ncon
0x172 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16 16 1 Ncon
0x173 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16 16 1 Ncon
0x174 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16 16 1 Ncon
0x175 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  8 1 Ncon
0x176 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  8 1 Ncon
0x177 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  8 1 Ncon
0x178 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  8 1 Ncon
0x179 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16 16 1 Ncon
0x17a 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16 16 1 Ncon
0x17b 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16 16 1 Ncon
0x17c 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16 16 1 Ncon
0x17d 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16 16 1 Ncon
0x17e 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16 16 1 Ncon
0x17f 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16 16 1 Ncon
0x180 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16 16 1 Ncon
0x181 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  8 1 Ncon
0x182 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  8 1 Ncon
0x183 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  8 1 Ncon
0x184 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  8 1 Ncon
0x185 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16 16 1 Ncon
0x186 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16 16 1 Ncon
0x187 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16 16 1 Ncon
0x188 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16 16 1 Ncon
0x189 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16 16 1 Ncon
0x18a 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16 16 1 Ncon
0x18b 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16 16 1 Ncon
0x18c 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16 16 1 Ncon
0x18d 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16 32 1 Ncon
0x18e 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16 32 1 Ncon
0x18f 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16 32 1 Ncon
0x190 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16 32 1 Ncon
0x191 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16 32 1 Ncon
0x192 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16 32 1 Ncon
0x193 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16 32 1 Ncon
0x194 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16 32 1 Ncon
0x195 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16 32 1 Ncon
0x196 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16 32 1 Ncon
0x197 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16 32 1 Ncon
0x198 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16 32 1 Ncon
0x199 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16 32 1 Ncon
0x19a 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16 32 1 Ncon
0x19b 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16 32 1 Ncon
0x19c 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16 32 1 Ncon
0x19d 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  0 0 None
0x19e 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  0 0 None
0x19f 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  0 0 None
0x1a0 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  0 0 None
0x1a1 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x1a2 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  0 0 None
0x1a3 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x1a4 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  0 0 None
0x1a5 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4  0  0 16 16 16 16  0 0 None
0x1a6 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4  0  0 16 16 16 16  0 0 None
0x1a7 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4  0  0 16 16 16 16  0 0 None
0x1a8 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4  0  0 16 16 16 16  0 0 None
0x1a9 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x1aa 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x1ab 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x1ac 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x1ad 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x1ae 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  2 1 Ncon
0x1af 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x1b0 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  4 1 Ncon
0x1b1 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x1b2 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x1b3 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x1b4 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x1b5 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x1b6 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  2 1 Ncon
0x1b7 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x1b8 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  4 1 Ncon
0x1b9 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  8 1 Ncon
0x1ba 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  8 1 Ncon
0x1bb 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16 16 1 Ncon
0x1bc 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16 16 1 Ncon
0x1bd 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  8 1 Ncon
0x1be 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  8 1 Ncon
0x1bf 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16 16 1 Ncon
0x1c0 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16 16 1 Ncon
0x1c1 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  8 1 Ncon
0x1c2 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  8 1 Ncon
0x1c3 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16 16 1 Ncon
0x1c4 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16 16 1 Ncon
0x1c5 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  8 1 Ncon
0x1c6 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  8 1 Ncon
0x1c7 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16 16 1 Ncon
0x1c8 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16 16 1 Ncon
0x1c9 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  8 1 Ncon
0x1ca 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16  8 1 Ncon
0x1cb 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16 16 1 Ncon
0x1cc 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16 16 1 Ncon
0x1cd 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16 16 1 Ncon
0x1ce 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16 16 1 Ncon
0x1cf 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16  8 1 Ncon
0x1d0 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16  8 1 Ncon
0x1d1 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16 16 1 Ncon
0x1d2 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16 16 1 Ncon
0x1d3 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16 16 1 Ncon
0x1d4 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16 16 1 Ncon
0x1d5 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16  8 1 Ncon
0x1d6 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16  8 1 Ncon
0x1d7 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16 16 1 Ncon
0x1d8 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16 16 1 Ncon
0x1d9 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16 16 1 Ncon
0x1da 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16 16 1 Ncon
0x1db 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16  8 1 Ncon
0x1dc 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16  8 1 Ncon
0x1dd 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16 16 1 Ncon
0x1de 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16 16 1 Ncon
0x1df 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16 16 1 Ncon
0x1e0 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16 16 1 Ncon
0x1e1 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16 32 1 Ncon
0x1e2 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  0 16 16 16 16 32 1 Ncon
0x1e3 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  0 16 16 16 16 32 1 Ncon
0x1e4 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  0 16 16 16 16 32 1 Ncon
0x1e5 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  8 16 16 16 16 32 1 Ncon
0x1e6 24 tc  0  32  0 r  y .   8  8  8  8 .  .  4 24  8 16 16 16 16 32 1 Ncon
0x1e7 24 tc  0  32  0 r  . .   8  8  8  0 .  .  4 24  8 16 16 16 16 32 1 Ncon
0x1e8 24 tc  0  32  0 r  . .   8  8  8  8 .  .  4 24  8 16 16 16 16 32 1 Ncon
0x1e9 24 tc  0  16  0 r  y .   5  6  5  0 .  .  4 16  0 16 16 16 16  0 0 Ncon
0x1ea 24 tc  0  16  0 r  . .   5  6  5  0 .  .  4 16  0 16 16 16 16  0 0 Ncon
0x1eb 24 tc  0  16  0 r  y .   5  6  5  0 .  .  4 24  0 16 16 16 16  0 0 Ncon
0x1ec 24 tc  0  16  0 r  . .   5  6  5  0 .  .  4 24  0 16 16 16 16  0 0 Ncon
0x1ed 24 tc  0  16  0 r  y .   5  6  5  0 .  .  4 24  8 16 16 16 16  0 0 Ncon
0x1ee 24 tc  0  16  0 r  . .   5  6  5  0 .  .  4 24  8 16 16 16 16  0 0 Ncon
0x1ef 24 tc  0  16  0 r  y .   5  6  5  0 .  .  4  0  0 16 16 16 16  0 0 Ncon
0x1f0 24 tc  0  16  0 r  . .   5  6  5  0 .  .  4  0  0 16 16 16 16  0 0 Ncon
0x1f1 24 tc  0   0  0 r  . .   0  0  0  0 .  .  4 16  0 16 16 16 16  0 0 Ncon
0x1f2 24 tc  0   0  0 r  . .   0  0  0  0 .  .  4 24  0 16 16 16 16  0 0 Ncon
0x1f3 24 tc  0   0  0 r  . .   0  0  0  0 .  .  4 24  8 16 16 16 16  0 0 Ncon
0x1f4 32 tc  0  32  0 r  . .  16 16  0  0 .  .  4  0  0 16 16 16 16  0 0 Ncon
0x1f5 24 tc  0  32  0 r  . .  16 16  0  0 .  .  4  0  0 16 16 16 16  0 0 Ncon
0x1f6 32 tc  0  32  0 r  y .  16 16  0  0 .  .  4  0  0 16 16 16 16  0 0 Ncon
0x1f7 24 tc  0  32  0 r  y .  16 16  0  0 .  .  4  0  0 16 16 16 16  0 0 Ncon
0x1f8 32 tc  0  32  0 r  . .  32  0  0  0 .  .  4  0  0 16 16 16 16  0 0 Ncon
0x1f9 24 tc  0  32  0 r  . .  32  0  0  0 .  .  4  0  0 16 16 16 16  0 0 Ncon
0x1fa 32 tc  0  32  0 r  y .  32  0  0  0 .  .  4  0  0 16 16 16 16  0 0 Ncon
0x1fb 24 tc  0  32  0 r  y .  32  0  0  0 .  .  4  0  0 16 16 16 16  0 0 Ncon
0x1fc 24 tc  0  64  0 r  . .  16 16 16 16 .  .  4  0  0 16 16 16 16  0 0 Ncon
0x1fd 24 tc  0  64  0 r  . .  16 16 16 16 .  .  4  0  0 16 16 16 16  0 0 Ncon
0x1fe 24 tc  0  64  0 r  y .  16 16 16 16 .  .  4  0  0 16 16 16 16  0 0 Ncon
0x1ff 24 tc  0  64  0 r  y .  16 16 16 16 .  .  4  0  0 16 16 16 16  0 0 Ncon
0x200 24 tc  0 128  0 r  . .  32 32 32 32 .  .  4  0  0 16 16 16 16  0 0 Ncon
0x201 24 tc  0 128  0 r  . .  32 32 32 32 .  .  4  0  0 16 16 16 16  0 0 Ncon
0x202 24 tc  0 128  0 r  y .  32 32 32 32 .  .  4  0  0 16 16 16 16  0 0 Ncon
0x203 24 tc  0 128  0 r  y .  32 32 32 32 .  .  4  0  0 16 16 16 16  0 0 Ncon
0x204 32 tc  0  32  0 r  . .  16 16  0  0 .  .  4 24  0 16 16 16 16  0 0 Ncon
0x205 24 tc  0  32  0 r  . .  16 16  0  0 .  .  4 24  0 16 16 16 16  0 0 Ncon
0x206 32 tc  0  32  0 r  y .  16 16  0  0 .  .  4 24  0 16 16 16 16  0 0 Ncon
0x207 24 tc  0  32  0 r  y .  16 16  0  0 .  .  4 24  0 16 16 16 16  0 0 Ncon
0x208 32 tc  0  32  0 r  . .  16 16  0  0 .  .  4 24  8 16 16 16 16  0 0 Ncon
0x209 24 tc  0  32  0 r  . .  16 16  0  0 .  .  4 24  8 16 16 16 16  0 0 Ncon
0x20a 32 tc  0  32  0 r  y .  16 16  0  0 .  .  4 24  8 16 16 16 16  0 0 Ncon
0x20b 24 tc  0  32  0 r  y .  16 16  0  0 .  .  4 24  8 16 16 16 16  0 0 Ncon
0x20c 32 tc  0  32  0 r  . .  32  0  0  0 .  .  4 24  0 16 16 16 16  0 0 Ncon
0x20d 24 tc  0  32  0 r  . .  32  0  0  0 .  .  4 24  0 16 16 16 16  0 0 Ncon
0x20e 32 tc  0  32  0 r  y .  32  0  0  0 .  .  4 24  0 16 16 16 16  0 0 Ncon
0x20f 24 tc  0  32  0 r  y .  32  0  0  0 .  .  4 24  0 16 16 16 16  0 0 Ncon
0x210 32 tc  0  32  0 r  . .  32  0  0  0 .  .  4 24  8 16 16 16 16  0 0 Ncon
0x211 24 tc  0  32  0 r  . .  32  0  0  0 .  .  4 24  8 16 16 16 16  0 0 Ncon
0x212 32 tc  0  32  0 r  y .  32  0  0  0 .  .  4 24  8 16 16 16 16  0 0 Ncon
0x213 24 tc  0  32  0 r  y .  32  0  0  0 .  .  4 24  8 16 16 16 16  0 0 Ncon
0x214 24 tc  0  64  0 r  . .  16 16 16 16 .  .  4 24  0 16 16 16 16  0 0 Ncon
0x215 24 tc  0  64  0 r  . .  16 16 16 16 .  .  4 24  0 16 16 16 16  0 0 Ncon
0x216 24 tc  0  64  0 r  y .  16 16 16 16 .  .  4 24  0 16 16 16 16  0 0 Ncon
0x217 24 tc  0  64  0 r  y .  16 16 16 16 .  .  4 24  0 16 16 16 16  0 0 Ncon
0x218 24 tc  0  64  0 r  . .  16 16 16 16 .  .  4 24  8 16 16 16 16  0 0 Ncon
0x219 24 tc  0  64  0 r  . .  16 16 16 16 .  .  4 24  8 16 16 16 16  0 0 Ncon
0x21a 24 tc  0  64  0 r  y .  16 16 16 16 .  .  4 24  8 16 16 16 16  0 0 Ncon
0x21b 24 tc  0  64  0 r  y .  16 16 16 16 .  .  4 24  8 16 16 16 16  0 0 Ncon
0x21c 24 tc  0 128  0 r  . .  32 32 32 32 .  .  4 24  0 16 16 16 16  0 0 Ncon
0x21d 24 tc  0 128  0 r  . .  32 32 32 32 .  .  4 24  0 16 16 16 16  0 0 Ncon
0x21e 24 tc  0 128  0 r  y .  32 32 32 32 .  .  4 24  0 16 16 16 16  0 0 Ncon
0x21f 24 tc  0 128  0 r  y .  32 32 32 32 .  .  4 24  0 16 16 16 16  0 0 Ncon
0x220 24 tc  0 128  0 r  . .  32 32 32 32 .  .  4 24  8 16 16 16 16  0 0 Ncon
0x221 24 tc  0 128  0 r  . .  32 32 32 32 .  .  4 24  8 16 16 16 16  0 0 Ncon
0x222 24 tc  0 128  0 r  y .  32 32 32 32 .  .  4 24  8 16 16 16 16  0 0 Ncon
0x223 24 tc  0 128  0 r  y .  32 32 32 32 .  .  4 24  8 16 16 16 16  0 0 Ncon
0x224 24 tc  0  16  0 r  . .  16  0  0  0 .  .  4  0  0 16 16 16 16  0 0 Ncon
0x225 24 tc  0  16  0 r  . .  16  0  0  0 .  .  4  0  0 16 16 16 16  0 0 Ncon
0x226 24 tc  0  16  0 r  y .  16  0  0  0 .  .  4  0  0 16 16 16 16  0 0 Ncon
0x227 24 tc  0  16  0 r  y .  16  0  0  0 .  .  4  0  0 16 16 16 16  0 0 Ncon
0x228 24 tc  0  64  0 r  . .  32 32  0  0 .  .  4  0  0 16 16 16 16  0 0 Ncon
0x229 24 tc  0  64  0 r  . .  32 32  0  0 .  .  4  0  0 16 16 16 16  0 0 Ncon
0x22a 24 tc  0  64  0 r  y .  32 32  0  0 .  .  4  0  0 16 16 16 16  0 0 Ncon
0x22b 24 tc  0  64  0 r  y .  32 32  0  0 .  .  4  0  0 16 16 16 16  0 0 Ncon
0x22c 24 tc  0  16  0 r  . .  16  0  0  0 .  .  4 24  0 16 16 16 16  0 0 Ncon
0x22d 24 tc  0  16  0 r  . .  16  0  0  0 .  .  4 24  0 16 16 16 16  0 0 Ncon
0x22e 24 tc  0  16  0 r  y .  16  0  0  0 .  .  4 24  0 16 16 16 16  0 0 Ncon
0x22f 24 tc  0  16  0 r  y .  16  0  0  0 .  .  4 24  0 16 16 16 16  0 0 Ncon
0x230 24 tc  0  16  0 r  . .  16  0  0  0 .  .  4 24  8 16 16 16 16  0 0 Ncon
0x231 24 tc  0  16  0 r  . .  16  0  0  0 .  .  4 24  8 16 16 16 16  0 0 Ncon
0x232 24 tc  0  16  0 r  y .  16  0  0  0 .  .  4 24  8 16 16 16 16  0 0 Ncon
0x233 24 tc  0  16  0 r  y .  16  0  0  0 .  .  4 24  8 16 16 16 16  0 0 Ncon
0x234 24 tc  0  64  0 r  . .  32 32  0  0 .  .  4 24  0 16 16 16 16  0 0 Ncon
0x235 24 tc  0  64  0 r  . .  32 32  0  0 .  .  4 24  0 16 16 16 16  0 0 Ncon
0x236 24 tc  0  64  0 r  y .  32 32  0  0 .  .  4 24  0 16 16 16 16  0 0 Ncon
0x237 24 tc  0  64  0 r  y .  32 32  0  0 .  .  4 24  0 16 16 16 16  0 0 Ncon
0x238 24 tc  0  64  0 r  . .  32 32  0  0 .  .  4 24  8 16 16 16 16  0 0 Ncon
0x239 24 tc  0  64  0 r  . .  32 32  0  0 .  .  4 24  8 16 16 16 16  0 0 Ncon
0x23a 24 tc  0  64  0 r  y .  32 32  0  0 .  .  4 24  8 16 16 16 16  0 0 Ncon
0x23b 24 tc  0  64  0 r  y .  32 32  0  0 .  .  4 24  8 16 16 16 16  0 0 Ncon


```

---

