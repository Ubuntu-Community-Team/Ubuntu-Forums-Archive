---
title: "No SM3 xorg-edgers natty(oss radeon), how to fix it?"
date: 2011-07-16
forum: Hardware
---

### Post by petterf on 2011-07-16
Hi! Thank you in advance for trying to help me!

I am trying to get shader model 3 to work with the radeon drivers, the reason is that this is required for the latest version of EVE-online, and according to some, these drivers are better than the catalyst drivers. The good thing is that it seems to work, though, it does not. I get a message stating that Shader Model 3 is not available or something like that.

Any suggestions are welcome!

Ubuntu Natty amd64
My video card is a HD 4350, chip R710.
Xorg-edgers(natty) used
kernel 3xxx (oneiric rc7) got crazy, didn't know what to do, there was only one thing missing which I fixed(my ethernet drivers)
wine 1.3x

Output from glxinfo
libGL: OpenDriver: trying /usr/lib/x86_64-linux-gnu/dri/tls/r600_dri.so
libGL: OpenDriver: trying /usr/lib/x86_64-linux-gnu/dri/r600_dri.so
libGL: Can't open configuration file /etc/drirc: No such file or directory.
libGL: Can't open configuration file /home/petter/.drirc: No such file or directory.
libGL: Can't open configuration file /etc/drirc: No such file or directory.
libGL: Can't open configuration file /home/petter/.drirc: No such file or directory.
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
OpenGL vendor string: X.Org
OpenGL renderer string: Gallium 0.4 on AMD RV710
OpenGL version string: 2.1 Mesa 7.12-devel
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
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, GL_ARB_transpose_matrix, 
    GL_EXT_blend_func_separate, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, 
    GL_EXT_secondary_color, GL_EXT_texture_env_add, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_INGR_blend_func_separate, GL_NV_blend_square, GL_NV_light_max_exponent, 
    GL_NV_texgen_reflection, GL_NV_texture_env_combine4, GL_S3_s3tc, 
    GL_SUN_multi_draw_arrays, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_EXT_framebuffer_object, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_env_dot3, 
    GL_MESA_window_pos, GL_NV_packed_depth_stencil, GL_NV_texture_rectangle, 
    GL_ARB_depth_texture, GL_ARB_occlusion_query, GL_ARB_shadow, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_window_pos, GL_EXT_stencil_two_side, GL_EXT_texture_cube_map, 
    GL_NV_depth_clamp, GL_APPLE_packed_pixels, GL_APPLE_vertex_array_object, 
    GL_ARB_draw_buffers, GL_ARB_fragment_program, GL_ARB_fragment_shader, 
    GL_ARB_shader_objects, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ATI_draw_buffers, GL_ATI_texture_env_combine3, GL_ATI_texture_float, 
    GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, GL_MESA_pack_invert, 
    GL_ARB_depth_clamp, GL_ARB_fragment_program_shadow, 
    GL_ARB_half_float_pixel, GL_ARB_occlusion_query2, GL_ARB_point_sprite, 
    GL_ARB_shading_language_100, GL_ARB_sync, GL_ARB_texture_non_power_of_two, 
    GL_ARB_vertex_buffer_object, GL_ATI_blend_equation_separate, 
    GL_EXT_blend_equation_separate, GL_OES_read_format, 
    GL_ARB_color_buffer_float, GL_ARB_pixel_buffer_object, 
    GL_ARB_texture_compression_rgtc, GL_ARB_texture_float, 
    GL_ARB_texture_rectangle, GL_ATI_texture_compression_3dc, 
    GL_EXT_packed_float, GL_EXT_pixel_buffer_object, 
    GL_EXT_texture_compression_dxt1, GL_EXT_texture_compression_rgtc, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_rectangle, 
    GL_EXT_texture_sRGB, GL_EXT_texture_shared_exponent, 
    GL_ARB_framebuffer_object, GL_EXT_framebuffer_blit, 
    GL_EXT_framebuffer_multisample, GL_EXT_packed_depth_stencil, 
    GL_ARB_vertex_array_object, GL_ATI_separate_stencil, 
    GL_ATI_texture_mirror_once, GL_EXT_draw_buffers2, 
    GL_EXT_gpu_program_parameters, GL_EXT_texture_compression_latc, 
    GL_EXT_texture_env_combine, GL_EXT_texture_sRGB_decode, 
    GL_EXT_timer_query, GL_OES_EGL_image, GL_ARB_copy_buffer, 
    GL_ARB_depth_buffer_float, GL_ARB_half_float_vertex, 
    GL_ARB_instanced_arrays, GL_ARB_map_buffer_range, GL_ARB_texture_rg, 
    GL_ARB_texture_swizzle, GL_ARB_vertex_array_bgra, 
    GL_EXT_separate_shader_objects, GL_EXT_texture_swizzle, 
    GL_EXT_vertex_array_bgra, GL_NV_conditional_render, 
    GL_AMD_draw_buffers_blend, GL_AMD_shader_stencil_export, 
    GL_ARB_draw_buffers_blend, GL_ARB_draw_elements_base_vertex, 
    GL_ARB_explicit_attrib_location, GL_ARB_fragment_coord_conventions, 
    GL_ARB_provoking_vertex, GL_ARB_sampler_objects, GL_ARB_seamless_cube_map, 
    GL_ARB_shader_stencil_export, GL_ARB_shader_texture_lod, 
    GL_EXT_provoking_vertex, GL_EXT_texture_snorm, 
    GL_MESA_texture_signed_rgba, GL_NV_texture_barrier, GL_ARB_robustness

dmesg | grep drm
[    9.182673] [drm] Initialized drm 1.1.0 20060810
[   10.303842] [drm] radeon defaulting to kernel modesetting.
[   10.303847] [drm] radeon kernel modesetting enabled.
[   10.304518] [drm] initializing kernel modesetting (RV710 0x1002:0x954F).
[   10.304542] [drm] register mmio base: 0xFDCE0000
[   10.304544] [drm] register mmio size: 65536
[   10.305270] [drm] Detected VRAM RAM=512M, BAR=256M
[   10.305274] [drm] RAM width 64bits DDR
[   10.305591] [drm] radeon: 512M of VRAM memory ready
[   10.305593] [drm] radeon: 512M of GTT memory ready.
[   10.305617] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   10.305619] [drm] Driver supports precise vblank timestamp query.
[   10.305696] [drm] radeon: irq initialized.
[   10.305701] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   10.308021] [drm] Loading RV710 Microcode
[   10.502478] [drm] ring test succeeded in 1 usecs
[   10.502594] [drm] radeon: ib pool ready.
[   10.502668] [drm] ib test succeeded in 0 usecs
[   10.503232] [drm] Radeon Display Connectors
[   10.503234] [drm] Connector 0:
[   10.503236] [drm]   VGA
[   10.503238] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[   10.503239] [drm]   Encoders:
[   10.503241] [drm]     CRT2: INTERNAL_KLDSCP_DAC2
[   10.503242] [drm] Connector 1:
[   10.503244] [drm]   HDMI-A
[   10.503245] [drm]   HPD1
[   10.503247] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
[   10.503248] [drm]   Encoders:
[   10.503250] [drm]     DFP1: INTERNAL_UNIPHY
[   10.503251] [drm] Connector 2:
[   10.503252] [drm]   DVI-I
[   10.503253] [drm]   HPD4
[   10.503255] [drm]   DDC: 0x7f10 0x7f10 0x7f14 0x7f14 0x7f18 0x7f18 0x7f1c 0x7f1c
[   10.503257] [drm]   Encoders:
[   10.503258] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[   10.503259] [drm]     DFP2: INTERNAL_UNIPHY2
[   10.620978] [drm] Internal thermal controller without fan control
[   10.621226] [drm] radeon: power management initialized
[   10.752410] [drm] fb mappable at 0xE0142000
[   10.752412] [drm] vram apper at 0xE0000000
[   10.752413] [drm] size 5242880
[   10.752415] [drm] fb depth is 24
[   10.752416] [drm]    pitch is 5120
[   10.752493] fbcon: radeondrmfb (fb0) is primary device
[   11.155476] fb0: radeondrmfb frame buffer device
[   11.155477] drm: registered panic notifier
[   11.155501] [drm] Initialized radeon 2.10.0 20080528 for 0000:02:00.0 on minor 0

---

