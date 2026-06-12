---
title: "GMA 3150 graphics (Atom N570) shader version issue"
date: 2018-03-21
forum: Hardware
---

### Post by Huzudra on 2018-03-21
I've recently aquired a netbook (Acer Aspire One D257) with an Intel Atom N570 pineview graphics. I'm trying to run a game (OpenRA) which crashes on launch, I need a minimum of Shader model 2.0 capable GPU, from what I've read online the GMA 3150 in the N570 should meet that requirement, but when I try to check that out the information on the GPU with glxinfo I don't see anything about shader model. What command do I need to run to get that information? What I can glean online is that the 3150 should be shader model 2.0, but a lot of posts and information are from 2010-2011 and there hasn't been much since. My impression of the issue is that it may be a driver problem but I wanted to see if could pin it down because on paper this game should run and the hardware should be there. The additional drivers doesn't list anything needed for the netbook and everything else seems to work fine.

When the game fails to open it gives some crash information which says to check the graphics.log, when I check that it states that I have shader model 1.2 and opengl 1.4 Mesa 17.0.7. I'll try to log in to the forums from the netbook and post the log in a follow up post, it's difficult to type on and use for that, I'm adjusting to a tiny keyboard and have a wounded thumb. 

Acer Aspire One D257
Intel Atom N570
2GB RAM
120GB SSD
Xubuntu 16.04 (updated to current at time of posting)

---

### Post by Huzudra on 2018-03-21
Here's the output of the terminal when openra fails to open

work@work-AOD257:~$ openra
Platform is Linux
Engine version is {DEV_VERSION}
Using SDL 2 with OpenGL renderer
Desktop resolution: 1024x600
No custom resolution provided, using desktop resolution
Using resolution: 1024x600
Using window scale 1.00
Renderer initialization failed. Check graphics.log for details.
Using SDL 2 with OpenGL renderer
Desktop resolution: 1024x600
No custom resolution provided, using desktop resolution
Using resolution: 1024x600
Using window scale 1.00
Renderer initialization failed. Check graphics.log for details.
Exception of type `System.InvalidOperationException`: Failed to initialize platform-integration library. Check graphics.log for details.
  at OpenRA.Game.Initialize (OpenRA.Arguments args) <0x40fb5460 + 0x01043> in <filename unknown>:0 
  at OpenRA.Program.Run (System.String[] args) <0x40f9bd80 + 0x00037> in <filename unknown>:0 
  at OpenRA.Program.Main (System.String[] args) <0x40f9ae10 + 0x000db> in <filename unknown>:0 



Here's the contents of the graphics.log mentioned above.

Unsupported OpenGL version: 1.4 Mesa 17.0.7

OpenGL Information:
Vendor: Intel Open Source Technology Center
Renderer: Mesa DRI Intel(R) Pineview M 
GL Version: 1.4 Mesa 17.0.7
Shader Version: 1.20
Available extensions:
GL_ARB_multisample GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_copy_texture GL_EXT_polygon_offset GL_EXT_subtexture GL_EXT_texture_object GL_EXT_vertex_array GL_EXT_compiled_vertex_array GL_EXT_texture GL_EXT_texture3D GL_IBM_rasterpos_clip GL_ARB_point_parameters GL_EXT_draw_range_elements GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_separate_specular_color GL_EXT_texture_edge_clamp GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_ARB_multitexture GL_IBM_multimode_draw_arrays GL_IBM_texture_mirrored_repeat GL_3DFX_texture_compression_FXT1 GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_transpose_matrix GL_EXT_blend_func_separate GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_secondary_color GL_EXT_texture_env_add GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_INGR_blend_func_separate GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texgen_reflection GL_NV_texture_env_combine4 GL_S3_s3tc GL_SUN_multi_draw_arrays GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_EXT_framebuffer_object GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_MESA_window_pos GL_NV_packed_depth_stencil GL_NV_texture_rectangle GL_ARB_depth_texture GL_ARB_shadow GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_window_pos GL_EXT_stencil_two_side GL_EXT_texture_cube_map GL_APPLE_packed_pixels GL_APPLE_vertex_array_object GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_shader GL_ARB_shader_objects GL_ARB_vertex_program GL_ARB_vertex_shader GL_ATI_draw_buffers GL_ATI_texture_env_combine3 GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_ARB_half_float_pixel GL_ARB_point_sprite GL_ARB_shading_language_100 GL_ARB_sync GL_ARB_texture_non_power_of_two GL_ARB_vertex_buffer_object GL_ATI_blend_equation_separate GL_EXT_blend_equation_separate GL_OES_read_format GL_ARB_pixel_buffer_object GL_ARB_texture_rectangle GL_EXT_pixel_buffer_object GL_EXT_texture_compression_dxt1 GL_EXT_texture_rectangle GL_EXT_texture_sRGB GL_ARB_framebuffer_object GL_EXT_framebuffer_blit GL_EXT_packed_depth_stencil GL_APPLE_object_purgeable GL_ARB_vertex_array_object GL_ATI_separate_stencil GL_EXT_gpu_program_parameters GL_EXT_texture_sRGB_decode GL_OES_EGL_image GL_ARB_copy_buffer GL_ARB_map_buffer_range GL_ARB_ES2_compatibility GL_ARB_debug_output GL_ARB_draw_elements_base_vertex GL_ARB_explicit_attrib_location GL_ARB_provoking_vertex GL_ARB_sampler_objects GL_EXT_provoking_vertex GL_ARB_get_program_binary GL_ARB_robustness GL_ARB_separate_shader_objects GL_ANGLE_texture_compression_dxt3 GL_ANGLE_texture_compression_dxt5 GL_ARB_compressed_texture_pixel_storage GL_ARB_internalformat_query GL_ARB_map_buffer_alignment GL_ARB_texture_storage GL_AMD_shader_trinary_minmax GL_ARB_clear_buffer_object GL_ARB_explicit_uniform_location GL_ARB_invalidate_subdata GL_ARB_program_interface_query GL_ARB_vertex_attrib_binding GL_KHR_debug GL_ARB_multi_bind GL_ARB_get_texture_sub_image GL_KHR_context_flush_control 
System.InvalidProgramException: OpenGL Version Error: See graphics.log for details.
  at OpenRA.Platforms.Default.OpenGL.Initialize () <0x41a7cf70 + 0x00a23> in <filename unknown>:0 
  at OpenRA.Platforms.Default.Sdl2GraphicsDevice..ctor (Size windowSize, WindowMode windowMode) <0x41a79000 + 0x00a9f> in <filename unknown>:0 
  at OpenRA.Platforms.Default.DefaultPlatform.CreateGraphics (Size size, WindowMode windowMode) <0x41a55a00 + 0x00037> in <filename unknown>:0 
  at OpenRA.Renderer..ctor (IPlatform platform, OpenRA.GraphicSettings graphicSettings) <0x41a65960 + 0x000d3> in <filename unknown>:0 
  at OpenRA.Game.Initialize (OpenRA.Arguments args) <0x419fd460 + 0x007d7> in <filename unknown>:0 
Unsupported OpenGL version: 1.4 Mesa 17.0.7

OpenGL Information:
Vendor: Intel Open Source Technology Center
Renderer: Mesa DRI Intel(R) Pineview M 
GL Version: 1.4 Mesa 17.0.7
Shader Version: 1.20
Available extensions:
GL_ARB_multisample GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_copy_texture GL_EXT_polygon_offset GL_EXT_subtexture GL_EXT_texture_object GL_EXT_vertex_array GL_EXT_compiled_vertex_array GL_EXT_texture GL_EXT_texture3D GL_IBM_rasterpos_clip GL_ARB_point_parameters GL_EXT_draw_range_elements GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_separate_specular_color GL_EXT_texture_edge_clamp GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_ARB_multitexture GL_IBM_multimode_draw_arrays GL_IBM_texture_mirrored_repeat GL_3DFX_texture_compression_FXT1 GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_transpose_matrix GL_EXT_blend_func_separate GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_secondary_color GL_EXT_texture_env_add GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_INGR_blend_func_separate GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texgen_reflection GL_NV_texture_env_combine4 GL_S3_s3tc GL_SUN_multi_draw_arrays GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_EXT_framebuffer_object GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_MESA_window_pos GL_NV_packed_depth_stencil GL_NV_texture_rectangle GL_ARB_depth_texture GL_ARB_shadow GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_window_pos GL_EXT_stencil_two_side GL_EXT_texture_cube_map GL_APPLE_packed_pixels GL_APPLE_vertex_array_object GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_shader GL_ARB_shader_objects GL_ARB_vertex_program GL_ARB_vertex_shader GL_ATI_draw_buffers GL_ATI_texture_env_combine3 GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_ARB_half_float_pixel GL_ARB_point_sprite GL_ARB_shading_language_100 GL_ARB_sync GL_ARB_texture_non_power_of_two GL_ARB_vertex_buffer_object GL_ATI_blend_equation_separate GL_EXT_blend_equation_separate GL_OES_read_format GL_ARB_pixel_buffer_object GL_ARB_texture_rectangle GL_EXT_pixel_buffer_object GL_EXT_texture_compression_dxt1 GL_EXT_texture_rectangle GL_EXT_texture_sRGB GL_ARB_framebuffer_object GL_EXT_framebuffer_blit GL_EXT_packed_depth_stencil GL_APPLE_object_purgeable GL_ARB_vertex_array_object GL_ATI_separate_stencil GL_EXT_gpu_program_parameters GL_EXT_texture_sRGB_decode GL_OES_EGL_image GL_ARB_copy_buffer GL_ARB_map_buffer_range GL_ARB_ES2_compatibility GL_ARB_debug_output GL_ARB_draw_elements_base_vertex GL_ARB_explicit_attrib_location GL_ARB_provoking_vertex GL_ARB_sampler_objects GL_EXT_provoking_vertex GL_ARB_get_program_binary GL_ARB_robustness GL_ARB_separate_shader_objects GL_ANGLE_texture_compression_dxt3 GL_ANGLE_texture_compression_dxt5 GL_ARB_compressed_texture_pixel_storage GL_ARB_internalformat_query GL_ARB_map_buffer_alignment GL_ARB_texture_storage GL_AMD_shader_trinary_minmax GL_ARB_clear_buffer_object GL_ARB_explicit_uniform_location GL_ARB_invalidate_subdata GL_ARB_program_interface_query GL_ARB_vertex_attrib_binding GL_KHR_debug GL_ARB_multi_bind GL_ARB_get_texture_sub_image GL_KHR_context_flush_control 
System.InvalidProgramException: OpenGL Version Error: See graphics.log for details.
  at OpenRA.Platforms.Default.OpenGL.Initialize () <0x41a7cf70 + 0x00a23> in <filename unknown>:0 
  at OpenRA.Platforms.Default.Sdl2GraphicsDevice..ctor (Size windowSize, WindowMode windowMode) <0x41a79000 + 0x00a9f> in <filename unknown>:0 
  at OpenRA.Platforms.Default.DefaultPlatform.CreateGraphics (Size size, WindowMode windowMode) <0x41a55a00 + 0x00037> in <filename unknown>:0 
  at OpenRA.Renderer..ctor (IPlatform platform, OpenRA.GraphicSettings graphicSettings) <0x41a65960 + 0x000d3> in <filename unknown>:0 
  at OpenRA.Game.Initialize (OpenRA.Arguments args) <0x419fd460 + 0x007d7> in <filename unknown>:0 


If I've posted this to the wrong section I apologize, since it's a hardware issue I thought this was most correct. Bothering the developer seemed incorrect since it seems to be a hardware issue.

---

### Post by Yellow Pasque on 2018-03-22
[https://ubuntuforums.org/showthread.php?t=2374952](https://ubuntuforums.org/showthread.php?t=2374952)

---

### Post by kostkon on 2018-03-22
I attempted to run it in the past on a similarly specced machine and got the same error (I tried the snap version). 

After successfully getting some Steam games, that required >=OpenGL2.0, to run on that system (you enter the line in the game's Launch Options) with:
```
MESA_GL_VERSION_OVERRIDE=2.0 %command%
```
I thought about going back to that game and trying to run it with:
```
MESA_GL_VERSION_OVERRIDE=2.0 openra
```
or probably:
```
MESA_GL_VERSION_OVERRIDE=2.1 openra
```
(since 2.1 is the max version that GMA3150 can support)

So, you could try that for me and see if it works.

---

### Post by Huzudra on 2018-03-26
> **kostkon said:**
> I attempted to run it in the past on a similarly specced machine and got the same error (I tried the snap version). 

After successfully getting some Steam games, that required >=OpenGL2.0, to run on that system (you enter the line in the game's Launch Options) with:
```
MESA_GL_VERSION_OVERRIDE=2.0 %command%
```
I thought about going back to that game and trying to run it with:
```
MESA_GL_VERSION_OVERRIDE=2.0 openra
```
or probably:
```
MESA_GL_VERSION_OVERRIDE=2.1 openra
```
(since 2.1 is the max version that GMA3150 can support)

So, you could try that for me and see if it works.

work@work-AOD257:~$ MESA_GL_VERSION_OVERRIDE=2.0 openra

Platform is Linux
Engine version is {DEV_VERSION}
Using SDL 2 with OpenGL renderer
Desktop resolution: 1024x600
No custom resolution provided, using desktop resolution
Using resolution: 1024x600
Using window scale 1.00
OpenGL version: 2.0 Mesa 17.0.7
Using default sound device
Internal mods:
	cnc: Tiberian Dawn ({DEV_VERSION})
	d2k: Dune 2000 ({DEV_VERSION})
	modcontent: Mod Content Manager ({DEV_VERSION})
	ra: Red Alert ({DEV_VERSION})
External mods:
Exception of type `System.InvalidOperationException`: Game.Mod argument missing.
  at OpenRA.Game.InitializeMod (System.String mod, OpenRA.Arguments args) <0x41a4bd00 + 0x00993> in <filename unknown>:0 
  at OpenRA.Game.Initialize (OpenRA.Arguments args) <0x4199b460 + 0x01017> in <filename unknown>:0 
  at OpenRA.Program.Run (System.String[] args) <0x41981d80 + 0x00037> in <filename unknown>:0 
  at OpenRA.Program.Main (System.String[] args) <0x41980e10 + 0x000db> in <filename unknown>:0 

AL lib: (WW) FreeContext: (0x3664560) Deleting 32 Source(s)

No joy there, I'll try the other suggestion and report back, may be a little bit of a delay as this laptop might be loaned out temporarily for a friend in need.

---

### Post by Huzudra on 2018-03-26
> **Temüjin said:**
> [https://ubuntuforums.org/showthread.php?t=2374952](https://ubuntuforums.org/showthread.php?t=2374952)

I looked through there and I'm not entirely clear how he fixed it? Did he cherry pick the graphics driver from an older version of *buntu? I might need a little hand holding on that?

At least now I see...
work@work-AOD257:~$ glxinfo | grep OpenGL
OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Pineview M 
OpenGL version string: 2.1 Mesa 17.2.8
OpenGL shading language version string: 1.20
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 2.0 Mesa 17.2.8
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 1.0.16
OpenGL ES profile extensions:


But the shader is still the wrong version? OpenRA still crashes and outputs this to logfile
Unsupported OpenGL version: 1.4 Mesa 17.0.7

OpenGL Information:
Vendor: Intel Open Source Technology Center
Renderer: Mesa DRI Intel(R) Pineview M 
GL Version: 1.4 Mesa 17.0.7
Shader Version: 1.20
Available extensions:
GL_ARB_multisample GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_copy_texture GL_EXT_polygon_offset GL_EXT_subtexture GL_EXT_texture_object GL_EXT_vertex_array GL_EXT_compiled_vertex_array GL_EXT_texture GL_EXT_texture3D GL_IBM_rasterpos_clip GL_ARB_point_parameters GL_EXT_draw_range_elements GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_separate_specular_color GL_EXT_texture_edge_clamp GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_ARB_multitexture GL_IBM_multimode_draw_arrays GL_IBM_texture_mirrored_repeat GL_3DFX_texture_compression_FXT1 GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_transpose_matrix GL_EXT_blend_func_separate GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_secondary_color GL_EXT_texture_env_add GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_INGR_blend_func_separate GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texgen_reflection GL_NV_texture_env_combine4 GL_S3_s3tc GL_SUN_multi_draw_arrays GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_EXT_framebuffer_object GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_MESA_window_pos GL_NV_packed_depth_stencil GL_NV_texture_rectangle GL_ARB_depth_texture GL_ARB_shadow GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_window_pos GL_EXT_stencil_two_side GL_EXT_texture_cube_map GL_APPLE_packed_pixels GL_APPLE_vertex_array_object GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_shader GL_ARB_shader_objects GL_ARB_vertex_program GL_ARB_vertex_shader GL_ATI_draw_buffers GL_ATI_texture_env_combine3 GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_ARB_half_float_pixel GL_ARB_point_sprite GL_ARB_shading_language_100 GL_ARB_sync GL_ARB_texture_non_power_of_two GL_ARB_vertex_buffer_object GL_ATI_blend_equation_separate GL_EXT_blend_equation_separate GL_OES_read_format GL_ARB_pixel_buffer_object GL_ARB_texture_rectangle GL_EXT_pixel_buffer_object GL_EXT_texture_compression_dxt1 GL_EXT_texture_rectangle GL_EXT_texture_sRGB GL_ARB_framebuffer_object GL_EXT_framebuffer_blit GL_EXT_packed_depth_stencil GL_APPLE_object_purgeable GL_ARB_vertex_array_object GL_ATI_separate_stencil GL_EXT_gpu_program_parameters GL_EXT_texture_sRGB_decode GL_OES_EGL_image GL_ARB_copy_buffer GL_ARB_map_buffer_range GL_ARB_ES2_compatibility GL_ARB_debug_output GL_ARB_draw_elements_base_vertex GL_ARB_explicit_attrib_location GL_ARB_provoking_vertex GL_ARB_sampler_objects GL_EXT_provoking_vertex GL_ARB_get_program_binary GL_ARB_robustness GL_ARB_separate_shader_objects GL_ANGLE_texture_compression_dxt3 GL_ANGLE_texture_compression_dxt5 GL_ARB_compressed_texture_pixel_storage GL_ARB_internalformat_query GL_ARB_map_buffer_alignment GL_ARB_texture_storage GL_AMD_shader_trinary_minmax GL_ARB_clear_buffer_object GL_ARB_explicit_uniform_location GL_ARB_invalidate_subdata GL_ARB_program_interface_query GL_ARB_vertex_attrib_binding GL_KHR_debug GL_ARB_multi_bind GL_ARB_get_texture_sub_image GL_KHR_context_flush_control 
System.InvalidProgramException: OpenGL Version Error: See graphics.log for details.
  at OpenRA.Platforms.Default.OpenGL.Initialize () <0x412c1f70 + 0x00a23> in <filename unknown>:0 
  at OpenRA.Platforms.Default.Sdl2GraphicsDevice..ctor (Size windowSize, WindowMode windowMode) <0x412be000 + 0x00a9f> in <filename unknown>:0 
  at OpenRA.Platforms.Default.DefaultPlatform.CreateGraphics (Size size, WindowMode windowMode) <0x4129aa00 + 0x00037> in <filename unknown>:0 
  at OpenRA.Renderer..ctor (IPlatform platform, OpenRA.GraphicSettings graphicSettings) <0x412aa960 + 0x000d3> in <filename unknown>:0 
  at OpenRA.Game.Initialize (OpenRA.Arguments args) <0x41242460 + 0x007d7> in <filename unknown>:0 
Unsupported OpenGL version: 1.4 Mesa 17.0.7

OpenGL Information:
Vendor: Intel Open Source Technology Center
Renderer: Mesa DRI Intel(R) Pineview M 
GL Version: 1.4 Mesa 17.0.7
Shader Version: 1.20
Available extensions:
GL_ARB_multisample GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_copy_texture GL_EXT_polygon_offset GL_EXT_subtexture GL_EXT_texture_object GL_EXT_vertex_array GL_EXT_compiled_vertex_array GL_EXT_texture GL_EXT_texture3D GL_IBM_rasterpos_clip GL_ARB_point_parameters GL_EXT_draw_range_elements GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_separate_specular_color GL_EXT_texture_edge_clamp GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_ARB_multitexture GL_IBM_multimode_draw_arrays GL_IBM_texture_mirrored_repeat GL_3DFX_texture_compression_FXT1 GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_transpose_matrix GL_EXT_blend_func_separate GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_secondary_color GL_EXT_texture_env_add GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_INGR_blend_func_separate GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texgen_reflection GL_NV_texture_env_combine4 GL_S3_s3tc GL_SUN_multi_draw_arrays GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_EXT_framebuffer_object GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_MESA_window_pos GL_NV_packed_depth_stencil GL_NV_texture_rectangle GL_ARB_depth_texture GL_ARB_shadow GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_window_pos GL_EXT_stencil_two_side GL_EXT_texture_cube_map GL_APPLE_packed_pixels GL_APPLE_vertex_array_object GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_shader GL_ARB_shader_objects GL_ARB_vertex_program GL_ARB_vertex_shader GL_ATI_draw_buffers GL_ATI_texture_env_combine3 GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_ARB_half_float_pixel GL_ARB_point_sprite GL_ARB_shading_language_100 GL_ARB_sync GL_ARB_texture_non_power_of_two GL_ARB_vertex_buffer_object GL_ATI_blend_equation_separate GL_EXT_blend_equation_separate GL_OES_read_format GL_ARB_pixel_buffer_object GL_ARB_texture_rectangle GL_EXT_pixel_buffer_object GL_EXT_texture_compression_dxt1 GL_EXT_texture_rectangle GL_EXT_texture_sRGB GL_ARB_framebuffer_object GL_EXT_framebuffer_blit GL_EXT_packed_depth_stencil GL_APPLE_object_purgeable GL_ARB_vertex_array_object GL_ATI_separate_stencil GL_EXT_gpu_program_parameters GL_EXT_texture_sRGB_decode GL_OES_EGL_image GL_ARB_copy_buffer GL_ARB_map_buffer_range GL_ARB_ES2_compatibility GL_ARB_debug_output GL_ARB_draw_elements_base_vertex GL_ARB_explicit_attrib_location GL_ARB_provoking_vertex GL_ARB_sampler_objects GL_EXT_provoking_vertex GL_ARB_get_program_binary GL_ARB_robustness GL_ARB_separate_shader_objects GL_ANGLE_texture_compression_dxt3 GL_ANGLE_texture_compression_dxt5 GL_ARB_compressed_texture_pixel_storage GL_ARB_internalformat_query GL_ARB_map_buffer_alignment GL_ARB_texture_storage GL_AMD_shader_trinary_minmax GL_ARB_clear_buffer_object GL_ARB_explicit_uniform_location GL_ARB_invalidate_subdata GL_ARB_program_interface_query GL_ARB_vertex_attrib_binding GL_KHR_debug GL_ARB_multi_bind GL_ARB_get_texture_sub_image GL_KHR_context_flush_control 
System.InvalidProgramException: OpenGL Version Error: See graphics.log for details.
  at OpenRA.Platforms.Default.OpenGL.Initialize () <0x412c1f70 + 0x00a23> in <filename unknown>:0 
  at OpenRA.Platforms.Default.Sdl2GraphicsDevice..ctor (Size windowSize, WindowMode windowMode) <0x412be000 + 0x00a9f> in <filename unknown>:0 
  at OpenRA.Platforms.Default.DefaultPlatform.CreateGraphics (Size size, WindowMode windowMode) <0x4129aa00 + 0x00037> in <filename unknown>:0 
  at OpenRA.Renderer..ctor (IPlatform platform, OpenRA.GraphicSettings graphicSettings) <0x412aa960 + 0x000d3> in <filename unknown>:0 
  at OpenRA.Game.Initialize (OpenRA.Arguments args) <0x41242460 + 0x007d7> in <filename unknown>:0 


So...that's a bit weird eh? I may just chalk it up to 'old hardware is full of lies and incompatibility' It happens sometimes. I can get something else tiny to play games on airplanes with, just thought I'd try to work with what I had.

---

### Post by kostkon on 2018-03-27
> **Huzudra said:**
> work@work-AOD257:~$ MESA_GL_VERSION_OVERRIDE=2.0 openra
No joy there, I'll try the other suggestion and report back, may be a little bit of a delay as this laptop might be loaned out temporarily for a friend in need.
Hmm, could you give it another go? According to [this report]("https://github.com/OpenRA/OpenRA/issues/14396"), it should something along the lines of:
```
MESA_GL_VERSION_OVERRIDE=2.0 redalert
```
or maybe
```
MESA_GL_VERSION_OVERRIDE=2.0 RedAlert
```

---

### Post by Huzudra on 2018-03-27
No, redalert is not the command.
laptop@laptop-Satellite-L655:~$ openra-ra
Platform is Linux
Engine version is release-20180218
Using SDL 2 with OpenGL renderer
Desktop resolution: 1366x768
No custom resolution provided, using desktop resolution
Using resolution: 1366x768
Using window scale 1.00
OpenGL version: 2.1 Mesa 17.2.8
Using default sound device
Internal mods:
	cnc: Tiberian Dawn (release-20180218)
	d2k: Dune 2000 (release-20180218)
	modcontent: Mod Content Manager (release-20180218)
	ra: Red Alert (release-20180218)
External mods:
	cnc-release-20180218: Tiberian Dawn (release-20180218)
	d2k-release-20180218: Dune 2000 (release-20180218)
	ra-release-20180218: Red Alert (release-20180218)
Loading mod: ra
AL lib: (WW) FreeContext: (0x3505380) Deleting 32 Source(s)
laptop@laptop-Satellite-L655:~$ 


That's the output from a working openra install, so maybe if I try openra-ra...but the laptop with the non working install is currently borrowed out while I repair another one. I'll try that when I get it back. I think though I'll just move on, seems like the 3150 graphics don't actually have the hardware inside they claim to have. I'm going to try to find something in the 11-13" range with some other kind of Intel CPU, this one was part of a deal 2 netbooks for $50 and hard to pass up. It does everything else well enough, I think I'd rather have something with a little more power and RAM for travelling anyway.

---

