---
title: "High cpu usage when watching video in browsers"
date: 2018-04-26
forum: Hardware
---

### Post by Rob_Stevenson on 2018-04-26
Hi,

I have a new laptop with a clean install of Ubuntu 17.10.

It is a Dell XPS 13 9635 with Intel i7-7Y75 and Intel HD Graphics 615 (Kaby Lake GT2).

Whenever viewing video in firefox or chrome CPU usage is at least 75% on each core. Doing anything else on the laptop whilst viewing video makes the whole system unusable...

Any help would be really appreciated.

Thanks

---

### Post by tinylagarto on 2018-04-26
Are you using Flash or is it HTML5? If it is Flash, some rare sites still use it, then I guess it is a common problem.
Also look if hardware acceleration is enabled in both browsers from the preferences/options.

---

### Post by deadflowr on 2018-04-26
In, at least chrome, look at
```
chrome://gpu
```
and double check at
```
chrome://settings/
```
that use hardware acceleration when available is on.
(Scroll down to the System Box)

---

### Post by SeijiSensei on 2018-04-27
In Flash, make the video full-screen, then right-click on the image. Make sure the hardware acceleration box is checked.

---

### Post by Rob_Stevenson on 2018-04-27
This happens when I am playing video on, for example, youtube or video-calling someone on appear.in.

Here's the output of chrome://gpu
```

[COLOR=#000000][FONT=sans-serif]**Graphics Feature Status**


[LIST]
[*]Canvas: [COLOR=#008000]Hardware accelerated[/COLOR]
[*]CheckerImaging: [COLOR=#FF0000]Disabled[/COLOR]
[*]Flash: [COLOR=#008000]Hardware accelerated[/COLOR]
[*]Flash Stage3D: [COLOR=#008000]Hardware accelerated[/COLOR]
[*]Flash Stage3D Baseline profile: [COLOR=#008000]Hardware accelerated[/COLOR]
[*]Compositing: [COLOR=#008000]Hardware accelerated[/COLOR]
[*]Multiple Raster Threads: [COLOR=#008000]Enabled[/COLOR]
[*]Native GpuMemoryBuffers: [COLOR=#808000]Software only. Hardware acceleration disabled[/COLOR]
[*]Rasterization: [COLOR=#008000]Hardware accelerated[/COLOR]
[*]Surface Synchronization: [COLOR=#008000]Enabled[/COLOR]
[*]Video Decode: [COLOR=#008000]Hardware accelerated[/COLOR]
[*]WebGL: [COLOR=#008000]Hardware accelerated[/COLOR]
[*]WebGL2: [COLOR=#008000]Hardware accelerated[/COLOR]
[/LIST]
[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]**Driver Bug Workarounds**


[LIST]
[*]adjust_src_dst_region_for_blitframebuffer
[*]clear_uniforms_before_first_program_use
[*]count_all_in_varyings_packing
[*]decode_encode_srgb_for_generatemipmap
[*]disable_framebuffer_cmaa
[*]disable_post_sub_buffers_for_onscreen_surfaces
[*]msaa_is_slow
[*]scalarize_vec_and_mat_constructor_args
[/LIST]
[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]**Problems Detected**


[LIST]
[*]Clear uniforms before first program use on all platforms: [124764]("http://crbug.com/124764"), [349137]("http://crbug.com/349137")
*Applied Workarounds: [COLOR=#808000]clear_uniforms_before_first_program_use[/COLOR]*
[*][I]Mesa drivers in Linux handle varyings without static use incorrectly: [333885]("http://crbug.com/333885")
*Applied Workarounds: [COLOR=#808000]count_all_in_varyings_packing[/COLOR]*[/I]
[*][I][I]Disable partial swaps on Mesa drivers (detected with GL_RENDERER): [339493]("http://crbug.com/339493")
*Applied Workarounds: [COLOR=#808000]disable_post_sub_buffers_for_onscreen_surfaces[/COLOR]*[/I][/I]
[*][I][I][I]Always rewrite vec/mat constructors to be consistent: [398694]("http://crbug.com/398694")
*Applied Workarounds: [COLOR=#808000]scalarize_vec_and_mat_constructor_args[/COLOR]*[/I][/I][/I]
[*][I][I][I]On Intel GPUs MSAA performance is not acceptable for GPU rasterization: [527565]("http://crbug.com/527565")
*Applied Workarounds: [COLOR=#808000]msaa_is_slow[/COLOR]*[/I][/I][/I]
[*][I][I][I]Timer queries crash on Intel GPUs on Linux: [540543]("http://crbug.com/540543"), [576991]("http://crbug.com/576991")
*Applied Workarounds: [COLOR=#808000]disable(GL_ARB_timer_query)[/COLOR], [COLOR=#808000]disable(GL_EXT_timer_query)[/COLOR]*[/I][/I][/I]
[*][I][I][I]Use GL_INTEL_framebuffer_CMAA on ChromeOS: [535198]("http://crbug.com/535198")
*Applied Workarounds: [COLOR=#808000]disable_framebuffer_cmaa[/COLOR]*[/I][/I][/I]
[*][I][I][I]Disable partial swaps on Mesa drivers (detected with GL_VERSION): [339493]("http://crbug.com/339493")
*Applied Workarounds: [COLOR=#808000]disable_post_sub_buffers_for_onscreen_surfaces[/COLOR]*[/I][/I][/I]
[*][I][I][I]Decode and encode before generateMipmap for srgb format textures on os except macosx: [634519]("http://crbug.com/634519")
*Applied Workarounds: [COLOR=#808000]decode_encode_srgb_for_generatemipmap[/COLOR]*[/I][/I][/I]
[*][I][I][I]adjust src/dst region if blitting pixels outside read framebuffer on Linux Intel: [664740]("http://crbug.com/664740")
*Applied Workarounds: [COLOR=#808000]adjust_src_dst_region_for_blitframebuffer[/COLOR]*[/I][/I][/I]
[*][I][I][I]Disable KHR_blend_equation_advanced until cc shaders are updated: [661715]("http://crbug.com/661715")
*Applied Workarounds: [COLOR=#808000]disable(GL_KHR_blend_equation_advanced)[/COLOR], [COLOR=#808000]disable(GL_KHR_blend_equation_advanced_coherent)[/COLOR]*[/I][/I][/I]
[*]*[I][I]Don't expose disjoint_timer_query extensions to WebGL: [808744]("http://crbug.com/808744")*[/I][/I]
[*][I][I][I]Native GpuMemoryBuffers have been disabled, either via about:flags or command line.
*Disabled Features: [COLOR=#FF0000]native_gpu_memory_buffers[/COLOR]*[/I][/I][/I]
[*][I][I][I]Checker-imaging has been disabled via finch trial or the command line.
*Disabled Features: [COLOR=#FF0000]checker_imaging[/COLOR]*[/I][/I][/I]
[/LIST]
[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]***[I][I]Version Information*[/I][/I]**

[TABLE="width: 1502"]
[TR]
[TD]**Data exported**[/TD]
[TD]2018-04-27T14:14:03.915Z[/TD]
[/TR]
[TR]
[TD]**Chrome version**[/TD]
[TD]Chrome/66.0.3359.117[/TD]
[/TR]
[TR]
[TD]**Operating system**[/TD]
[TD]Linux 4.13.0-39-generic[/TD]
[/TR]
[TR]
[TD]**Software rendering list URL**[/TD]
[TD]https://chromium.googlesource.com/chromium/src/+/7f59c28e25283df88e0c6ac8d8b2551d8c6ad93b/gpu/config/software_rendering_list.json[/TD]
[/TR]
[TR]
[TD]**Driver bug list URL**[/TD]
[TD]https://chromium.googlesource.com/chromium/src/+/7f59c28e25283df88e0c6ac8d8b2551d8c6ad93b/gpu/config/gpu_driver_bug_list.json[/TD]
[/TR]
[TR]
[TD]**ANGLE commit id**[/TD]
[TD]22c768fbda54[/TD]
[/TR]
[TR]
[TD]**2D graphics backend**[/TD]
[TD]Skia/66 773868fdade5f9f0e7697e6d09c9bd80aaa9b402-[/TD]
[/TR]
[TR]
[TD]**Command Line**[/TD]
[TD]/usr/bin/google-chrome-stable --flag-switches-begin --disable-software-rasterizer --enable-gpu-rasterization --ignore-gpu-blacklist --flag-switches-end[/TD]
[/TR]
[/TABLE]


[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]***[I][I]Driver Information*[/I][/I]**

[TABLE="width: 1502"]
[TR]
[TD]**Initialization time**[/TD]
[TD]33[/TD]
[/TR]
[TR]
[TD]**In-process GPU**[/TD]
[TD]false[/TD]
[/TR]
[TR]
[TD]**Passthrough Command Decoder**[/TD]
[TD]false[/TD]
[/TR]
[TR]
[TD]**Direct Composition**[/TD]
[TD]false[/TD]
[/TR]
[TR]
[TD]**Supports overlays**[/TD]
[TD]false[/TD]
[/TR]
[TR]
[TD]**Sandboxed**[/TD]
[TD]true[/TD]
[/TR]
[TR]
[TD]**GPU0**[/TD]
[TD]VENDOR = 0x8086, DEVICE= 0x591e *ACTIVE*[/TD]
[/TR]
[TR]
[TD]**Optimus**[/TD]
[TD]false[/TD]
[/TR]
[TR]
[TD]**Optimus**[/TD]
[TD]false[/TD]
[/TR]
[TR]
[TD]**AMD switchable**[/TD]
[TD]false[/TD]
[/TR]
[TR]
[TD]**Driver vendor**[/TD]
[TD]Mesa[/TD]
[/TR]
[TR]
[TD]**Driver version**[/TD]
[TD]17.3.3[/TD]
[/TR]
[TR]
[TD]**Driver date**[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]**Pixel shader version**[/TD]
[TD]1.30[/TD]
[/TR]
[TR]
[TD]**Vertex shader version**[/TD]
[TD]1.30[/TD]
[/TR]
[TR]
[TD]**Max. MSAA samples**[/TD]
[TD]16[/TD]
[/TR]
[TR]
[TD]**Machine model name**[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]**Machine model version**[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]**GL_VENDOR**[/TD]
[TD]Intel Open Source Technology Center[/TD]
[/TR]
[TR]
[TD]**GL_RENDERER**[/TD]
[TD]Mesa DRI Intel(R) HD Graphics 615 (Kaby Lake GT2)[/TD]
[/TR]
[TR]
[TD]**GL_VERSION**[/TD]
[TD]3.0 Mesa 17.3.3[/TD]
[/TR]
[TR]
[TD]**GL_EXTENSIONS**[/TD]
[TD]GL_3DFX_texture_compression_FXT1 GL_AMD_conservative_depth GL_AMD_draw_buffers_blend GL_AMD_seamless_cubemap_per_texture GL_AMD_shader_stencil_export GL_AMD_shader_trinary_minmax GL_ANGLE_texture_compression_dxt3 GL_ANGLE_texture_compression_dxt5 GL_APPLE_object_purgeable GL_APPLE_packed_pixels GL_ARB_ES2_compatibility GL_ARB_ES3_compatibility GL_ARB_arrays_of_arrays GL_ARB_blend_func_extended GL_ARB_buffer_storage GL_ARB_clear_buffer_object GL_ARB_clear_texture GL_ARB_clip_control GL_ARB_color_buffer_float GL_ARB_compressed_texture_pixel_storage GL_ARB_compute_shader GL_ARB_conditional_render_inverted GL_ARB_conservative_depth GL_ARB_copy_buffer GL_ARB_copy_image GL_ARB_cull_distance GL_ARB_debug_output GL_ARB_depth_buffer_float GL_ARB_depth_clamp GL_ARB_depth_texture GL_ARB_derivative_control GL_ARB_draw_buffers GL_ARB_draw_buffers_blend GL_ARB_draw_elements_base_vertex GL_ARB_draw_instanced GL_ARB_explicit_attrib_location GL_ARB_explicit_uniform_location GL_ARB_fragment_coord_conventions GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_framebuffer_no_attachments GL_ARB_framebuffer_object GL_ARB_framebuffer_sRGB GL_ARB_get_program_binary GL_ARB_get_texture_sub_image GL_ARB_half_float_pixel GL_ARB_half_float_vertex GL_ARB_instanced_arrays GL_ARB_internalformat_query GL_ARB_internalformat_query2 GL_ARB_invalidate_subdata GL_ARB_map_buffer_alignment GL_ARB_map_buffer_range GL_ARB_multi_bind GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_occlusion_query2 GL_ARB_pipeline_statistics_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_polygon_offset_clamp GL_ARB_program_interface_query GL_ARB_provoking_vertex GL_ARB_query_buffer_object GL_ARB_robust_buffer_access_behavior GL_ARB_robustness GL_ARB_sample_shading GL_ARB_sampler_objects GL_ARB_seamless_cube_map GL_ARB_seamless_cubemap_per_texture GL_ARB_separate_shader_objects GL_ARB_shader_atomic_counter_ops GL_ARB_shader_atomic_counters GL_ARB_shader_ballot GL_ARB_shader_bit_encoding GL_ARB_shader_clock GL_ARB_shader_draw_parameters GL_ARB_shader_group_vote GL_ARB_shader_image_load_store GL_ARB_shader_image_size GL_ARB_shader_objects GL_ARB_shader_precision GL_ARB_shader_stencil_export GL_ARB_shader_storage_buffer_object GL_ARB_shader_texture_image_samples GL_ARB_shader_texture_lod GL_ARB_shading_language_100 GL_ARB_shading_language_420pack GL_ARB_shading_language_packing GL_ARB_shadow GL_ARB_stencil_texturing GL_ARB_sync GL_ARB_texture_barrier GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_compression_bptc GL_ARB_texture_compression_rgtc GL_ARB_texture_cube_map GL_ARB_texture_cube_map_array GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_filter_anisotropic GL_ARB_texture_float GL_ARB_texture_gather GL_ARB_texture_mirror_clamp_to_edge GL_ARB_texture_mirrored_repeat GL_ARB_texture_multisample GL_ARB_texture_non_power_of_two GL_ARB_texture_query_levels GL_ARB_texture_query_lod GL_ARB_texture_rectangle GL_ARB_texture_rg GL_ARB_texture_rgb10_a2ui GL_ARB_texture_stencil8 GL_ARB_texture_storage GL_ARB_texture_storage_multisample GL_ARB_texture_swizzle GL_ARB_texture_view GL_ARB_timer_query GL_ARB_transform_feedback2 GL_ARB_transform_feedback3 GL_ARB_transform_feedback_instanced GL_ARB_transform_feedback_overflow_query GL_ARB_transpose_matrix GL_ARB_uniform_buffer_object GL_ARB_vertex_array_bgra GL_ARB_vertex_array_object GL_ARB_vertex_attrib_binding GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_vertex_type_10f_11f_11f_rev GL_ARB_vertex_type_2_10_10_10_rev GL_ARB_window_pos GL_ATI_blend_equation_separate GL_ATI_draw_buffers GL_ATI_separate_stencil GL_ATI_texture_env_combine3 GL_ATI_texture_float GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_copy_texture GL_EXT_draw_buffers2 GL_EXT_draw_instanced GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_framebuffer_multisample_blit_scaled GL_EXT_framebuffer_object GL_EXT_framebuffer_sRGB GL_EXT_gpu_program_parameters GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_float GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_polygon_offset GL_EXT_polygon_offset_clamp GL_EXT_provoking_vertex GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shader_integer_mix GL_EXT_shader_samples_identical GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_array GL_EXT_texture_compression_dxt1 GL_EXT_texture_compression_rgtc GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_integer GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_texture_sRGB GL_EXT_texture_sRGB_decode GL_EXT_texture_shared_exponent GL_EXT_texture_snorm GL_EXT_texture_swizzle GL_EXT_timer_query GL_EXT_transform_feedback GL_EXT_vertex_array GL_EXT_vertex_array_bgra GL_IBM_multimode_draw_arrays GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_INTEL_performance_query GL_KHR_blend_equation_advanced GL_KHR_blend_equation_advanced_coherent GL_KHR_context_flush_control GL_KHR_debug GL_KHR_no_error GL_KHR_robust_buffer_access_behavior GL_KHR_robustness GL_KHR_texture_compression_astc_ldr GL_KHR_texture_compression_astc_sliced_3d GL_MESA_pack_invert GL_MESA_shader_integer_functions GL_MESA_texture_signed_rgba GL_MESA_window_pos GL_NV_blend_square GL_NV_conditional_render GL_NV_depth_clamp GL_NV_light_max_exponent GL_NV_packed_depth_stencil GL_NV_primitive_restart GL_NV_texgen_reflection GL_NV_texture_barrier GL_NV_texture_env_combine4 GL_NV_texture_rectangle GL_OES_EGL_image GL_OES_read_format GL_S3_s3tc GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SUN_multi_draw_arrays[/TD]
[/TR]
[TR]
[TD]**Disabled Extensions**[/TD]
[TD]GL_ARB_timer_query GL_EXT_timer_query GL_KHR_blend_equation_advanced GL_KHR_blend_equation_advanced_coherent[/TD]
[/TR]
[TR]
[TD]**Disabled WebGL Extensions**[/TD]
[TD]EXT_disjoint_timer_query EXT_disjoint_timer_query_webgl2[/TD]
[/TR]
[TR]
[TD]**Window system binding vendor**[/TD]
[TD]SGI[/TD]
[/TR]
[TR]
[TD]**Window system binding version**[/TD]
[TD]1.4[/TD]
[/TR]
[TR]
[TD]**Window system binding extensions**[/TD]
[TD]GLX_ARB_create_context GLX_ARB_create_context_profile GLX_ARB_create_context_robustness GLX_ARB_fbconfig_float GLX_ARB_framebuffer_sRGB GLX_ARB_multisample GLX_EXT_create_context_es_profile GLX_EXT_create_context_es2_profile GLX_EXT_fbconfig_packed_float GLX_EXT_framebuffer_sRGB GLX_EXT_import_context GLX_EXT_libglvnd GLX_EXT_texture_from_pixmap GLX_EXT_visual_info GLX_EXT_visual_rating GLX_MESA_copy_sub_buffer GLX_OML_swap_method GLX_SGI_make_current_read GLX_SGI_swap_control GLX_SGIS_multisample GLX_SGIX_fbconfig GLX_SGIX_pbuffer GLX_SGIX_visual_select_group GLX_INTEL_swap_event[/TD]
[/TR]
[TR]
[TD]**Window manager**[/TD]
[TD]GNOME Shell[/TD]
[/TR]
[TR]
[TD]**XDG_CURRENT_DESKTOP**[/TD]
[TD]ubuntu:GNOME[/TD]
[/TR]
[TR]
[TD]**GDMSESSION**[/TD]
[TD]ubuntu-xorg[/TD]
[/TR]
[TR]
[TD]**Compositing manager**[/TD]
[TD]Yes[/TD]
[/TR]
[TR]
[TD]**Direct rendering**[/TD]
[TD]Yes[/TD]
[/TR]
[TR]
[TD]**Reset notification strategy**[/TD]
[TD]0x8261[/TD]
[/TR]
[TR]
[TD]**GPU process crash count**[/TD]
[TD]0[/TD]
[/TR]
[TR]
[TD]**System visual ID**[/TD]
[TD]33[/TD]
[/TR]
[TR]
[TD]**RGBA visual ID**[/TD]
[TD]160[/TD]
[/TR]
[/TABLE]


[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]***[I][I]Compositor Information*[/I][/I]**

[TABLE="width: 1502"]
[TR]
[TD]**Tile Update Mode**[/TD]
[TD]One-copy[/TD]
[/TR]
[TR]
[TD]**Partial Raster**[/TD]
[TD]Enabled[/TD]
[/TR]
[/TABLE]


[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]***[I][I]GpuMemoryBuffers Status*[/I][/I]**

[TABLE="width: 1502"]
[TR]
[TD]**ATC**[/TD]
[TD]Software only[/TD]
[/TR]
[TR]
[TD]**ATCIA**[/TD]
[TD]Software only[/TD]
[/TR]
[TR]
[TD]**DXT1**[/TD]
[TD]Software only[/TD]
[/TR]
[TR]
[TD]**DXT5**[/TD]
[TD]Software only[/TD]
[/TR]
[TR]
[TD]**ETC1**[/TD]
[TD]Software only[/TD]
[/TR]
[TR]
[TD]**R_8**[/TD]
[TD]Software only[/TD]
[/TR]
[TR]
[TD]**R_16**[/TD]
[TD]Software only[/TD]
[/TR]
[TR]
[TD]**RG_88**[/TD]
[TD]Software only[/TD]
[/TR]
[TR]
[TD]**BGR_565**[/TD]
[TD]Software only[/TD]
[/TR]
[TR]
[TD]**RGBA_4444**[/TD]
[TD]Software only[/TD]
[/TR]
[TR]
[TD]**RGBX_8888**[/TD]
[TD]Software only[/TD]
[/TR]
[TR]
[TD]**RGBA_8888**[/TD]
[TD]Software only[/TD]
[/TR]
[TR]
[TD]**BGRX_8888**[/TD]
[TD]Software only[/TD]
[/TR]
[TR]
[TD]**BGRX_1010102**[/TD]
[TD]Software only[/TD]
[/TR]
[TR]
[TD]**RGBX_1010102**[/TD]
[TD]Software only[/TD]
[/TR]
[TR]
[TD]**BGRA_8888**[/TD]
[TD]Software only[/TD]
[/TR]
[TR]
[TD]**RGBA_F16**[/TD]
[TD]Software only[/TD]
[/TR]
[TR]
[TD]**YVU_420**[/TD]
[TD]Software only[/TD]
[/TR]
[TR]
[TD]**YUV_420_BIPLANAR**[/TD]
[TD]Software only[/TD]
[/TR]
[TR]
[TD]**UYVY_422**[/TD]
[TD]Software only[/TD]
[/TR]
[/TABLE]


[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]***[I][I]Display(s) Information*[/I][/I]**

[TABLE="width: 1502"]
[TR]
[TD]**Info**[/TD]
[TD]Display[21691165392764928] bounds=0,0 1600x900, workarea=67,27 1533x872, scale=2, external[/TD]
[/TR]
[TR]
[TD]**Color space information**[/TD]
[TD]{primaries:[[0.4380,0.3842,0.1420,],[0.2231,0.7169,0.0601,],[0.0145,0.0973,0.7131,],], transfer:0.0000*x + 0.0000 if x < 0.0000 else (1.0000*x + 0.0000)**2.2000 + 0.0000, matrix:RGB, range:FULL}[/TD]
[/TR]
[TR]
[TD]**Bits per color component**[/TD]
[TD]8[/TD]
[/TR]
[TR]
[TD]**Bits per pixel**[/TD]
[TD]24[/TD]
[/TR]
[/TABLE]


[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]***[I][I]Video Acceleration Information*[/I][/I]**[/FONT][/COLOR]
```

---

### Post by Rob_Stevenson on 2018-05-09
Still not found a solution to this problem! :(

---

