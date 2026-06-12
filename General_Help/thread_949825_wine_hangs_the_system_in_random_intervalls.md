---
title: "wine hangs the system in random intervalls"
date: 2008-10-16
forum: General Help
---

### Post by phun-ky on 2008-10-16
I've installed the latest nvidia drivers from source, the latest kernels from the update and the latest wine from winehq (1.1 something)

After random intervalls in e.g. World of Warcraft running under Wine, the whole system freezes and I've to push the reset button to reboot.

How can I solve this? (this also happened with the last nvidia driver and wine and kernel.. never figured out why this happens..)

stats:

intel quadcore (2.5 ghz) running ubuntu 32bit  8.04 with 2gig ram
Gigabyte GeForce 9800GTX 512MB GDDR3

glxinfo:
```

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float, GLX_EXT_framebuffer_sRGB
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float, 
    GLX_EXT_fbconfig_packed_float, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_framebuffer_sRGB, GLX_NV_present_video, 
    GLX_NV_multisample_coverage
GLX version: 1.3
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float, GLX_EXT_framebuffer_sRGB, 
    GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 9800 GTX/9800 GTX+/PCI/SSE2
OpenGL version string: 2.1.2 NVIDIA 177.80
OpenGL extensions:
    GL_ARB_color_buffer_float, GL_ARB_depth_texture, GL_ARB_draw_buffers, 
    GL_ARB_fragment_program, GL_ARB_fragment_program_shadow, 
    GL_ARB_fragment_shader, GL_ARB_half_float_pixel, GL_ARB_imaging, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_occlusion_query, 
    GL_ARB_pixel_buffer_object, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_shader_objects, GL_ARB_shading_language_100, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, GL_ARB_texture_float, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_window_pos, GL_ATI_draw_buffers, GL_ATI_texture_float, 
    GL_ATI_texture_mirror_once, GL_S3_s3tc, GL_EXT_texture_env_add, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, 
    GL_EXT_Cg_shader, GL_EXT_bindable_uniform, GL_EXT_depth_bounds_test, 
    GL_EXT_draw_buffers2, GL_EXT_draw_instanced, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_blit, GL_EXT_framebuffer_multisample, 
    GL_EXT_framebuffer_object, GL_EXTX_framebuffer_mixed_formats, 
    GL_EXT_framebuffer_sRGB, GL_EXT_geometry_shader4, 
    GL_EXT_gpu_program_parameters, GL_EXT_gpu_shader4, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_depth_stencil, 
    GL_EXT_packed_float, GL_EXT_packed_pixels, GL_EXT_pixel_buffer_object, 
    GL_EXT_point_parameters, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_texture3D, 
    GL_EXT_texture_array, GL_EXT_texture_buffer_object, 
    GL_EXT_texture_compression_latc, GL_EXT_texture_compression_rgtc, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_integer, GL_EXT_texture_lod, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, GL_EXT_texture_sRGB, 
    GL_EXT_texture_shared_exponent, GL_EXT_timer_query, GL_EXT_vertex_array, 
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, 
    GL_KTX_buffer_region, GL_NV_blend_square, GL_NV_copy_depth_to_color, 
    GL_NV_depth_buffer_float, GL_NV_conditional_render, GL_NV_depth_clamp, 
    GL_NV_fence, GL_NV_float_buffer, GL_NV_fog_distance, 
    GL_NV_fragment_program, GL_NV_fragment_program_option, 
    GL_NV_fragment_program2, GL_NV_framebuffer_multisample_coverage, 
    GL_NV_geometry_shader4, GL_NV_gpu_program4, GL_NV_half_float, 
    GL_NV_light_max_exponent, GL_NV_multisample_coverage, 
    GL_NV_multisample_filter_hint, GL_NV_occlusion_query, 
    GL_NV_packed_depth_stencil, GL_NV_parameter_buffer_object, 
    GL_NV_pixel_data_range, GL_NV_point_sprite, GL_NV_primitive_restart, 
    GL_NV_register_combiners, GL_NV_register_combiners2, 
    GL_NV_texgen_reflection, GL_NV_texture_compression_vtc, 
    GL_NV_texture_env_combine4, GL_NV_texture_expand_normal, 
    GL_NV_texture_rectangle, GL_NV_texture_shader, GL_NV_texture_shader2, 
    GL_NV_texture_shader3, GL_NV_transform_feedback, GL_NV_vertex_array_range, 
    GL_NV_vertex_array_range2, GL_NV_vertex_program, GL_NV_vertex_program1_1, 
    GL_NV_vertex_program2, GL_NV_vertex_program2_option, 
    GL_NV_vertex_program3, GL_NVX_conditional_render, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_lod, GL_SGIX_depth_texture, GL_SGIX_shadow, 
    GL_SUN_slice_accum

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x28 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x2e 24 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x30 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x31 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x32 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x33 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x34 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x35 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x36 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x37 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x38 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x39 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x3a 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x3b 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x3c 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x3d 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x3e 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x3f 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x40 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x41 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x42 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x43 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x44 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x45 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x46 24 dc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x47 24 dc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x48 24 dc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x49 24 dc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x4a 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x4b 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x4c 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x4d 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x4e 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x4f 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x50 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x51 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x52 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x53 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x54 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x55 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x56 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x57 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x58 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x59 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x23 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x5a 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x5b 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x5c 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x5d 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x5e 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x5f 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x60 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x61 32 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x62 32 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x63 32 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x64 32 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x65 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x66 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x67 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x68 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x69 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x6a 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x6b 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x6c 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x6d 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x6e 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x6f 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x70 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x71 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x72 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x73 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x74 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon


```

dmesg
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-21-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Mon Aug 25 17:32:09 UTC 2008 (Ubuntu 2.6.24-21.42-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fef0000 (usable)
[    0.000000]  BIOS-e820: 000000007fef0000 - 000000007fef3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fef3000 - 000000007ff00000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f2000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] 1150MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f5a60
[    0.000000] Entering add_active_range(0, 0, 524016) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   524016
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   524016
[    0.000000] On node 0 totalpages: 524016
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2301 pages used for memmap
[    0.000000]   HighMem zone: 292339 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F75A0 checksum 0
[    0.000000] ACPI: RSDP 000F75A0, 0024 (r2 Nvidia)
[    0.000000] ACPI: XSDT 7FEF30C0, 0044 (r1 Nvidia ASUSACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 7FEF9A40, 00F4 (r3 Nvidia ASUSACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 7FEF3240, 67BC (r1 NVIDIA ASUSACPI     1000 MSFT  3000000)
[    0.000000] ACPI: FACS 7FEF0000, 0040
[    0.000000] ACPI: HPET 7FEF9C80, 0038 (r1 Nvidia ASUSACPI 42302E31 AWRD       98)
[    0.000000] ACPI: MCFG 7FEF9D00, 003C (r1 Nvidia ASUSACPI 42302E31 AWRD        0)
[    0.000000] ACPI: APIC 7FEF9B80, 0098 (r1 Nvidia ASUSACPI 42302E31 AWRD        0)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 7:7 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x02] enabled)
[    0.000000] Processor #2 7:7 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x03] enabled)
[    0.000000] Processor #3 7:7 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] enabled)
[    0.000000] Processor #1 7:7 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfeff0000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 7ff00000:70100000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519923
[    0.000000] Kernel command line: root=UUID=ae1d552c-db4d-4d2c-a24f-0f595a0f9332 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2499.975 MHz processor.
[   23.690234] spurious 8259A interrupt: IRQ7.
[   23.692318] Console: colour VGA+ 80x25
[   23.692321] console [tty0] enabled
[   23.692579] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   23.692816] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   23.751595] Memory: 2066072k/2096064k available (2177k kernel code, 28776k reserved, 1006k data, 368k init, 1178560k highmem)
[   23.751600] virtual kernel memory layout:
[   23.751601]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   23.751601]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   23.751602]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   23.751603]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   23.751603]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   23.751604]       .data : 0xc0320514 - 0xc041bdc4   (1006 kB)
[   23.751605]       .text : 0xc0100000 - 0xc0320514   (2177 kB)
[   23.751607] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   23.751643] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=4, Nodes=1
[   23.751753] hpet clockevent registered
[   23.831640] Calibrating delay using timer specific routine.. 5004.07 BogoMIPS (lpj=10008156)
[   23.831658] Security Framework initialized
[   23.831664] SELinux:  Disabled at boot.
[   23.831674] AppArmor: AppArmor initialized
[   23.831677] Failure registering capabilities with primary security module.
[   23.831684] Mount-cache hash table entries: 512
[   23.831781] Initializing cgroup subsys ns
[   23.831785] Initializing cgroup subsys cpuacct
[   23.831793] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0008e3fd 00000000 00000001 00000000
[   23.831797] monitor/mwait feature present.
[   23.831798] using mwait in idle threads.
[   23.831801] CPU: L1 I cache: 32K, L1 D cache: 32K
[   23.831803] CPU: L2 cache: 3072K
[   23.831804] CPU: Physical Processor ID: 0
[   23.831805] CPU: Processor Core ID: 0
[   23.831807] CPU: After all inits, caps: bfebfbff 20100000 00000000 00043940 0008e3fd 00000000 00000001 00000000
[   23.831813] Compat vDSO mapped to ffffe000.
[   23.831823] Checking 'hlt' instruction... OK.
[   23.847926] SMP alternatives: switching to UP code
[   23.849136] Early unpacking initramfs... done
[   24.080174] ACPI: Core revision 20070126
[   24.080208] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   24.084503] CPU0: Intel(R) Core(TM)2 Quad  CPU   Q9300  @ 2.50GHz stepping 07
[   24.084514] SMP alternatives: switching to SMP code
[   24.085040] Booting processor 1/1 eip 3000
[   24.095326] Initializing CPU#1
[   24.175130] Calibrating delay using timer specific routine.. 4999.97 BogoMIPS (lpj=9999954)
[   24.175135] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0008e3fd 00000000 00000001 00000000
[   24.175139] monitor/mwait feature present.
[   24.175141] CPU: L1 I cache: 32K, L1 D cache: 32K
[   24.175142] CPU: L2 cache: 3072K
[   24.175143] CPU: Physical Processor ID: 0
[   24.175144] CPU: Processor Core ID: 1
[   24.175145] CPU: After all inits, caps: bfebfbff 20100000 00000000 00043940 0008e3fd 00000000 00000001 00000000
[   24.175692] CPU1: Intel(R) Core(TM)2 Quad  CPU   Q9300  @ 2.50GHz stepping 07
[   24.175717] SMP alternatives: switching to SMP code
[   24.176253] Booting processor 2/2 eip 3000
[   24.186502] Initializing CPU#2
[   24.266995] Calibrating delay using timer specific routine.. 5000.03 BogoMIPS (lpj=10000073)
[   24.267000] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0008e3fd 00000000 00000001 00000000
[   24.267003] monitor/mwait feature present.
[   24.267005] CPU: L1 I cache: 32K, L1 D cache: 32K
[   24.267006] CPU: L2 cache: 3072K
[   24.267008] CPU: Physical Processor ID: 0
[   24.267008] CPU: Processor Core ID: 2
[   24.267009] CPU: After all inits, caps: bfebfbff 20100000 00000000 00043940 0008e3fd 00000000 00000001 00000000
[   24.267502] CPU2: Intel(R) Core(TM)2 Quad  CPU   Q9300  @ 2.50GHz stepping 07
[   24.267518] SMP alternatives: switching to SMP code
[   24.267928] Booting processor 3/3 eip 3000
[   24.278177] Initializing CPU#3
[   24.354865] Calibrating delay using timer specific routine.. 5000.03 BogoMIPS (lpj=10000067)
[   24.354869] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0008e3fd 00000000 00000001 00000000
[   24.354873] monitor/mwait feature present.
[   24.354875] CPU: L1 I cache: 32K, L1 D cache: 32K
[   24.354876] CPU: L2 cache: 3072K
[   24.354877] CPU: Physical Processor ID: 0
[   24.354878] CPU: Processor Core ID: 3
[   24.354879] CPU: After all inits, caps: bfebfbff 20100000 00000000 00043940 0008e3fd 00000000 00000001 00000000
[   24.355408] CPU3: Intel(R) Core(TM)2 Quad  CPU   Q9300  @ 2.50GHz stepping 07
[   24.355424] Total of 4 processors activated (20004.12 BogoMIPS).
[   24.355645] ENABLING IO-APIC IRQs
[   24.355837] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   24.502714] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   24.522714] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
[   24.542725] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
[   24.562710] Brought up 4 CPUs
[   24.562736] CPU0 attaching sched-domain:
[   24.562737]  domain 0: span 03
[   24.562739]   groups: 01 02
[   24.562745]   domain 1: span 0f
[   24.562746]    groups: 03 0c
[   24.562748] CPU1 attaching sched-domain:
[   24.562749]  domain 0: span 03
[   24.562750]   groups: 02 01
[   24.562752]   domain 1: span 0f
[   24.562753]    groups: 03 0c
[   24.562754] CPU2 attaching sched-domain:
[   24.562755]  domain 0: span 0c
[   24.562756]   groups: 04 08
[   24.562758]   domain 1: span 0f
[   24.562759]    groups: 0c 03
[   24.562760] CPU3 attaching sched-domain:
[   24.562761]  domain 0: span 0c
[   24.562762]   groups: 08 04
[   24.562764]   domain 1: span 0f
[   24.562765]    groups: 0c 03
[   24.562985] net_namespace: 64 bytes
[   24.562993] Booting paravirtualized kernel on bare hardware
[   24.563313] Time: 10:28:53  Date: 10/18/08
[   24.563331] NET: Registered protocol family 16
[   24.563448] EISA bus registered
[   24.563451] ACPI: bus type pci registered
[   24.598144] PCI: PCI BIOS revision 3.00 entry at 0xfba00, last bus=9
[   24.598145] PCI: Using configuration type 1
[   24.598158] Setting up standard PCI resources
[   24.600778] ACPI: EC: Look up EC in DSDT
[   24.605770] ACPI: Interpreter enabled
[   24.605773] ACPI: (supports S0 S1 S3 S4 S5)
[   24.605785] ACPI: Using IOAPIC for interrupt routing
[   24.612744] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   24.614679] PCI: Transparent bridge - 0000:00:10.0
[   24.614696] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   24.614908] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   24.674860] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 *11 14 15)
[   24.674993] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   24.675126] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 *11 14 15)
[   24.675258] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   24.675391] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 *10 11 14 15)
[   24.675522] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   24.675654] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   24.675785] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   24.675917] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 10 *11 14 15)
[   24.676048] ACPI: PCI Interrupt Link [LUBB] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   24.676181] ACPI: PCI Interrupt Link [LMAC] (IRQs *5 7 9 10 11 14 15)
[   24.676312] ACPI: PCI Interrupt Link [LACI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   24.676444] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 *11 14 15)
[   24.676575] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   24.676707] ACPI: PCI Interrupt Link [LMCI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   24.676839] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 *10 11 14 15)
[   24.676971] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 *10 11 14 15)
[   24.677102] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   24.677234] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 *10 11 14 15)
[   24.677366] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 10 *11 14 15)
[   24.677520] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0
[   24.677671] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[   24.677822] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0
[   24.677972] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[   24.678122] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0
[   24.678272] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
[   24.678422] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
[   24.678575] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
[   24.678725] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
[   24.678876] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
[   24.679027] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
[   24.679178] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0, disabled.
[   24.679331] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
[   24.679483] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0
[   24.679634] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
[   24.679785] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[   24.679936] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
[   24.680087] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[   24.680239] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[   24.680390] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[   24.680542] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0
[   24.680636] Linux Plug and Play Support v0.97 (c) Adam Belay
[   24.680656] pnp: PnP ACPI init
[   24.680660] ACPI: bus type pnp registered
[   24.684048] pnp: PnP ACPI: found 12 devices
[   24.684050] ACPI: ACPI bus type pnp unregistered
[   24.684052] PnPBIOS: Disabled by ACPI PNP
[   24.684187] PCI: Using ACPI for IRQ routing
[   24.684189] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   24.798222] NET: Registered protocol family 8
[   24.798224] NET: Registered protocol family 20
[   24.798251] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
[   24.798254] hpet0: 3 32-bit timers, 25000000 Hz
[   24.799278] AppArmor: AppArmor Filesystem Enabled
[   24.802212] Time: tsc clocksource has been installed.
[   24.802218] Switched to high resolution mode on CPU 0
[   24.802278] Switched to high resolution mode on CPU 1
[   24.802336] Switched to high resolution mode on CPU 2
[   24.802374] Switched to high resolution mode on CPU 3
[   24.818165] system 00:01: ioport range 0x1000-0x107f has been reserved
[   24.818167] system 00:01: ioport range 0x1080-0x10ff has been reserved
[   24.818170] system 00:01: ioport range 0x1400-0x147f has been reserved
[   24.818172] system 00:01: ioport range 0x1480-0x14ff has been reserved
[   24.818174] system 00:01: ioport range 0x1800-0x187f has been reserved
[   24.818176] system 00:01: ioport range 0x1880-0x18ff has been reserved
[   24.818180] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[   24.818182] system 00:02: ioport range 0x800-0x87f has been reserved
[   24.818184] system 00:02: ioport range 0x290-0x297 has been reserved
[   24.818186] system 00:02: ioport range 0x880-0x88f has been reserved
[   24.818194] system 00:0a: iomem range 0xf0000000-0xf1ffffff could not be reserved
[   24.818199] system 00:0b: iomem range 0xd5800-0xd7fff has been reserved
[   24.818201] system 00:0b: iomem range 0xf0000-0xf7fff could not be reserved
[   24.818203] system 00:0b: iomem range 0xf8000-0xfbfff could not be reserved
[   24.818206] system 00:0b: iomem range 0xfc000-0xfffff could not be reserved
[   24.818208] system 00:0b: iomem range 0xfeff0000-0xfeff00ff could not be reserved
[   24.818210] system 00:0b: iomem range 0x7fef0000-0x7fefffff could not be reserved
[   24.818212] system 00:0b: iomem range 0xffff0000-0xffffffff could not be reserved
[   24.818215] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
[   24.818217] system 00:0b: iomem range 0x100000-0x7feeffff could not be reserved
[   24.818219] system 00:0b: iomem range 0xfec00000-0xfec00fff could not be reserved
[   24.818222] system 00:0b: iomem range 0xfee00000-0xfee00fff could not be reserved
[   24.818229] system 00:0b: iomem range 0xfeff0000-0xfeff03ff could not be reserved
[   24.848464] PCI: Bridge: 0000:02:00.0
[   24.848466]   IO window: d000-dfff
[   24.848469]   MEM window: f6000000-f9ffffff
[   24.848472]   PREFETCH window: d0000000-dfffffff
[   24.848475] PCI: Bridge: 0000:02:01.0
[   24.848477]   IO window: c000-cfff
[   24.848480]   MEM window: fbf00000-fbffffff
[   24.848483]   PREFETCH window: eff00000-efffffff
[   24.848486] PCI: Bridge: 0000:02:02.0
[   24.848488]   IO window: b000-bfff
[   24.848491]   MEM window: fbe00000-fbefffff
[   24.848493]   PREFETCH window: efe00000-efefffff
[   24.848497] PCI: Bridge: 0000:02:03.0
[   24.848498]   IO window: a000-afff
[   24.848501]   MEM window: fbd00000-fbdfffff
[   24.848504]   PREFETCH window: efd00000-efdfffff
[   24.848507] PCI: Bridge: 0000:01:00.0
[   24.848509]   IO window: a000-dfff
[   24.848512]   MEM window: f6000000-fbffffff
[   24.848514]   PREFETCH window: d0000000-efffffff
[   24.848518] PCI: Bridge: 0000:00:03.0
[   24.848519]   IO window: a000-dfff
[   24.848521]   MEM window: f6000000-fbffffff
[   24.848523]   PREFETCH window: d0000000-efffffff
[   24.848525] PCI: Bridge: 0000:00:06.0
[   24.848526]   IO window: 8000-8fff
[   24.848529]   MEM window: fdb00000-fdbfffff
[   24.848530]   PREFETCH window: fda00000-fdafffff
[   24.848533] PCI: Bridge: 0000:00:07.0
[   24.848534]   IO window: e000-efff
[   24.848536]   MEM window: fdf00000-fdffffff
[   24.848538]   PREFETCH window: fde00000-fdefffff
[   24.848540] PCI: Bridge: 0000:00:10.0
[   24.848542]   IO window: 9000-9fff
[   24.848545]   MEM window: fdd00000-fddfffff
[   24.848547]   PREFETCH window: fdc00000-fdcfffff
[   24.848557] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   24.848566] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   24.848574] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   24.848583] PCI: Setting latency timer of device 0000:02:01.0 to 64
[   24.848592] PCI: Setting latency timer of device 0000:02:02.0 to 64
[   24.848600] PCI: Setting latency timer of device 0000:02:03.0 to 64
[   24.848608] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   24.848614] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   24.848621] PCI: Setting latency timer of device 0000:00:10.0 to 64
[   24.848628] NET: Registered protocol family 2
[   24.886079] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   24.886227] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   24.886518] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   24.886662] TCP: Hash tables configured (established 131072 bind 65536)
[   24.886664] TCP reno registered
[   24.898123] checking if image is initramfs... it is
[   25.354771] Freeing initrd memory: 7321k freed
[   25.356049] audit: initializing netlink socket (disabled)
[   25.356058] audit(1224325733.449:1): initialized
[   25.356281] highmem bounce pool size: 64 pages
[   25.358709] VFS: Disk quotas dquot_6.5.1
[   25.358783] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   25.358885] io scheduler noop registered
[   25.358887] io scheduler anticipatory registered
[   25.358888] io scheduler deadline registered
[   25.358895] io scheduler cfq registered (default)
[   25.359012] pci 0000:00:03.0: Quirk disabling HT MSI mapping<6>pci 0000:00:06.0: Quirk disabling HT MSI mapping<6>pci 0000:00:07.0: Quirk disabling HT MSI mapping<6>pci 0000:00:09.0: Quirk disabling HT MSI mapping<6>pci 0000:00:0e.0: Quirk disabling HT MSI mapping<6>pci 0000:00:0f.0: Quirk disabling HT MSI mapping<6>pci 0000:00:10.0: Quirk disabling HT MSI mapping<6>pci 0000:00:10.1: Quirk disabling HT MSI mapping<7>Boot video device is 0000:03:00.0
[   25.375112] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   25.375139] assign_interrupt_mode Found MSI capability
[   25.375158] Allocate Port Service[0000:00:03.0:pcie00]
[   25.375237] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   25.375264] assign_interrupt_mode Found MSI capability
[   25.375282] Allocate Port Service[0000:00:06.0:pcie00]
[   25.375358] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   25.375384] assign_interrupt_mode Found MSI capability
[   25.375402] Allocate Port Service[0000:00:07.0:pcie00]
[   25.375482] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   25.375511] Allocate Port Service[0000:01:00.0:pcie10]
[   25.375594] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   25.375621] Allocate Port Service[0000:02:00.0:pcie20]
[   25.375701] PCI: Setting latency timer of device 0000:02:01.0 to 64
[   25.375728] Allocate Port Service[0000:02:01.0:pcie20]
[   25.375809] PCI: Setting latency timer of device 0000:02:02.0 to 64
[   25.375835] Allocate Port Service[0000:02:02.0:pcie20]
[   25.375918] PCI: Setting latency timer of device 0000:02:03.0 to 64
[   25.375944] Allocate Port Service[0000:02:03.0:pcie20]
[   25.376254] isapnp: Scanning for PnP cards...
[   25.728679] isapnp: No Plug & Play device found
[   25.759874] Real Time Clock Driver v1.12ac
[   25.760043] hpet_resources: 0xfeff0000 is busy
[   25.760079] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   25.760205] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   25.760794] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   25.761762] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   25.761835] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   25.762023] PNP: No PS/2 controller found. Probing ports directly.
[   25.762419] serio: i8042 KBD port at 0x60,0x64 irq 1
[   25.762425] serio: i8042 AUX port at 0x60,0x64 irq 12
[   25.788782] mice: PS/2 mouse device common for all mice
[   25.788884] EISA: Probing bus 0 at eisa.0
[   25.788890] Cannot allocate resource for EISA slot 1
[   25.788906] Cannot allocate resource for EISA slot 8
[   25.788907] EISA: Detected 0 cards.
[   25.788910] cpuidle: using governor ladder
[   25.788911] cpuidle: using governor menu
[   25.788992] NET: Registered protocol family 1
[   25.789021] Using IPI No-Shortcut mode
[   25.789048] registered taskstats version 1
[   25.789159]   Magic number: 12:362:477
[   25.789286] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   25.789287] EDD information not available.
[   25.789462] Freeing unused kernel memory: 368k freed
[   26.939990] fuse init (API version 7.9)
[   26.949695] ACPI: Fan [FAN] (on)
[   26.954752] ACPI: Thermal Zone [THRM] (40 C)
[   27.229484] usbcore: registered new interface driver usbfs
[   27.229501] usbcore: registered new interface driver hub
[   27.229518] usbcore: registered new device driver usb
[   27.230337] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   27.230674] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 23
[   27.230679] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [APCF] -> GSI 23 (level, low) -> IRQ 16
[   27.230688] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   27.230690] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[   27.230868] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
[   27.230879] ohci_hcd 0000:00:0b.0: irq 16, io mem 0xfe02f000
[   27.247898] SCSI subsystem initialized
[   27.266786] libata version 3.00 loaded.
[   27.288968] usb usb1: configuration #1 chosen from 1 choice
[   27.288984] hub 1-0:1.0: USB hub found
[   27.288990] hub 1-0:1.0: 8 ports detected
[   27.390963] sata_nv 0000:00:0e.0: version 3.5
[   27.391233] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 22
[   27.391238] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [APSI] -> GSI 22 (level, low) -> IRQ 17
[   27.391267] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   27.391314] scsi0 : sata_nv
[   27.391348] scsi1 : sata_nv
[   27.391456] ata1: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xf800 irq 17
[   27.391459] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xf808 irq 17
[   27.694256] usb 1-3: new full speed USB device using ohci_hcd and address 2
[   27.858017] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   27.866794] ata1.00: ATA-7: WDC WD1500ADFD-00NLR5, 21.07QR5, max UDMA/133
[   27.866797] ata1.00: 293046768 sectors, multi 1: LBA48 NCQ (not used)
[   27.882289] ata1.00: configured for UDMA/133
[   27.906056] usb 1-3: configuration #1 chosen from 1 choice
[   27.911997] hub 1-3:1.0: USB hub found
[   27.914978] hub 1-3:1.0: 3 ports detected
[   28.336771] usb 1-5: new full speed USB device using ohci_hcd and address 3
[   28.348768] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   28.375021] ata2.00: ATA-8: WDC WD5000AACS-00ZUB0, 01.01B01, max UDMA/133
[   28.375023] ata2.00: 976773168 sectors, multi 1: LBA48 NCQ (depth 0/32)
[   28.381173] ata2.00: configured for UDMA/133
[   28.381268] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1500ADFD-0 21.0 PQ: 0 ANSI: 5
[   28.381350] scsi 1:0:0:0: Direct-Access     ATA      WDC WD5000AACS-0 01.0 PQ: 0 ANSI: 5
[   28.381650] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 21
[   28.381655] ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [APSJ] -> GSI 21 (level, low) -> IRQ 18
[   28.381678] PCI: Setting latency timer of device 0000:00:0f.0 to 64
[   28.381706] scsi2 : sata_nv
[   28.381794] scsi3 : sata_nv
[   28.381896] ata3: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xf300 irq 18
[   28.381898] ata4: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xf308 irq 18
[   28.847999] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   28.995451] usb 1-5: configuration #1 chosen from 1 choice
[   29.011884] ata3.00: ATAPI: TSSTcorp CDDVDW SH-S203P, SB00, max UDMA/100
[   29.183627] ata3.00: configured for UDMA/100
[   29.307283] usb 1-7: new full speed USB device using ohci_hcd and address 4
[   29.494997] ata4: SATA link down (SStatus 0 SControl 300)
[   29.506071] scsi 2:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S203P  SB00 PQ: 0 ANSI: 5
[   29.506442] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 20
[   29.506449] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [APCL] -> GSI 20 (level, low) -> IRQ 19
[   29.506458] PCI: Setting latency timer of device 0000:00:0b.1 to 64
[   29.506460] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[   29.506486] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 2
[   29.506507] ehci_hcd 0000:00:0b.1: debug port 1
[   29.506510] PCI: cache line size of 32 is not supported by device 0000:00:0b.1
[   29.506518] ehci_hcd 0000:00:0b.1: irq 19, io mem 0xfe02e000
[   29.513624] usb 1-7: unable to read config index 0 descriptor/start: -62
[   29.513627] usb 1-7: chopping to 0 config(s)
[   29.515962] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   29.516060] usb usb2: configuration #1 chosen from 1 choice
[   29.516075] hub 2-0:1.0: USB hub found
[   29.516079] hub 2-0:1.0: 8 ports detected
[   29.519615] usb 1-7: string descriptor 0 read error: -62
[   29.525606] usb 1-7: string descriptor 0 read error: -62
[   29.525674] usb 1-7: no configuration chosen from 0 choices
[   29.525712] usb 1-3: USB disconnect, address 2
[   29.619009] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[   29.619275] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
[   29.619278] ACPI: PCI Interrupt 0000:00:14.0[A] -> Link [APCH] -> GSI 23 (level, low) -> IRQ 16
[   29.619282] PCI: Setting latency timer of device 0000:00:14.0 to 64
[   29.650766] usb 1-5: USB disconnect, address 3
[   29.778565] usb 1-7: USB disconnect, address 4
[   30.138362] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x1374 @ 1, addr 00:1f:c6:06:56:8b
[   30.138365] forcedeth 0000:00:14.0: highdma pwrctl timirq gbit lnktim desc-v3
[   30.138435] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   30.138720] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[   30.138725] ACPI: PCI Interrupt 0000:09:08.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 20
[   30.191324] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[20]  MMIO=[fddff000-fddff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   30.196340] pata_amd 0000:00:0d.0: version 0.3.10
[   30.196359] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   30.197355] scsi4 : pata_amd
[   30.197479] scsi5 : pata_amd
[   30.197907] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfd00 irq 14
[   30.197909] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfd08 irq 15
[   30.433557] usb 2-5: new high speed USB device using ehci_hcd and address 3
[   30.665603] ata5.00: ATA-6: WDC WD800BB-00FJA0, 13.03G13, max UDMA/100
[   30.665606] ata5.00: 156301488 sectors, multi 1: LBA 
[   30.666493] ata5.01: ATA-5: WDC WD1200AB-00CBA1, 04.07B04, max UDMA/100
[   30.666495] ata5.01: 234441648 sectors, multi 1: LBA 
[   30.673532] ata5.00: configured for UDMA/100
[   30.690236] ata5.01: configured for UDMA/100
[   30.855966] scsi 4:0:0:0: Direct-Access     ATA      WDC WD800BB-00FJ 13.0 PQ: 0 ANSI: 5
[   30.856056] scsi 4:0:1:0: Direct-Access     ATA      WDC WD1200AB-00C 04.0 PQ: 0 ANSI: 5
[   30.862910] Driver 'sd' needs updating - please use bus_type methods
[   30.862960] sd 0:0:0:0: [sda] 293046768 512-byte hardware sectors (150040 MB)
[   30.862969] sd 0:0:0:0: [sda] Write Protect is off
[   30.862971] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   30.862981] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   30.863073] sd 0:0:0:0: [sda] 293046768 512-byte hardware sectors (150040 MB)
[   30.863080] sd 0:0:0:0: [sda] Write Protect is off
[   30.863081] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   30.863092] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   30.863094]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   30.872886]  sda1 sda2 < sda5 >
[   30.886896] sd 0:0:0:0: [sda] Attached SCSI disk
[   30.886941] sd 1:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[   30.886949] sd 1:0:0:0: [sdb] Write Protect is off
[   30.886951] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   30.886962] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   30.886991] sd 1:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[   30.886997] sd 1:0:0:0: [sdb] Write Protect is off
[   30.886998] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   30.887009] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   30.887010]  sdb: sdb1 < sdb5 >
[   30.895458] sd 1:0:0:0: [sdb] Attached SCSI disk
[   30.895517] sd 4:0:0:0: [sdc] 156301488 512-byte hardware sectors (80026 MB)
[   30.895524] sd 4:0:0:0: [sdc] Write Protect is off
[   30.895525] sd 4:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[   30.895536] sd 4:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   30.895563] sd 4:0:0:0: [sdc] 156301488 512-byte hardware sectors (80026 MB)
[   30.895569] sd 4:0:0:0: [sdc] Write Protect is off
[   30.895570] sd 4:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[   30.895581] sd 4:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   30.895583]  sdc:sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   30.900685] Uniform CD-ROM driver Revision: 3.20
[   30.900714] sr 2:0:0:0: Attached scsi CD-ROM sr0
[   30.904838]  sdc1
[   30.904881] sd 4:0:0:0: [sdc] Attached SCSI disk
[   30.904931] sd 4:0:1:0: [sdd] 234441648 512-byte hardware sectors (120034 MB)
[   30.904938] sd 4:0:1:0: [sdd] Write Protect is off
[   30.904939] sd 4:0:1:0: [sdd] Mode Sense: 00 3a 00 00
[   30.904949] sd 4:0:1:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   30.904972] sd 4:0:1:0: [sdd] 234441648 512-byte hardware sectors (120034 MB)
[   30.904979] sd 4:0:1:0: [sdd] Write Protect is off
[   30.904980] sd 4:0:1:0: [sdd] Mode Sense: 00 3a 00 00
[   30.904990] sd 4:0:1:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   30.904992]  sdd: sdd1 < sdd5 >
[   30.914855] sd 4:0:1:0: [sdd] Attached SCSI disk
[   30.918495] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   30.918509] sd 1:0:0:0: Attached scsi generic sg1 type 0
[   30.918521] sr 2:0:0:0: Attached scsi generic sg2 type 5
[   30.918533] sd 4:0:0:0: Attached scsi generic sg3 type 0
[   30.918545] sd 4:0:1:0: Attached scsi generic sg4 type 0
[   31.124113] usb 2-5: configuration #1 chosen from 1 choice
[   31.364168] usbcore: registered new interface driver libusual
[   31.368030] Initializing USB Mass Storage driver...
[   31.421108] Attempting manual resume
[   31.421110] swsusp: Resume From Partition 8:5
[   31.421111] PM: Checking swsusp image.
[   31.421233] PM: Resume from disk failed.
[   31.429747] EXT3-fs: INFO: recovery required on readonly filesystem.
[   31.429750] EXT3-fs: write access will be enabled during recovery.
[   31.466143] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001e8c000112c356]
[   31.667669] usb 1-3: new full speed USB device using ohci_hcd and address 5
[   31.880220] usb 1-3: configuration #1 chosen from 1 choice
[   31.886157] hub 1-3:1.0: USB hub found
[   31.889139] hub 1-3:1.0: 3 ports detected
[   32.310686] usb 1-7: new full speed USB device using ohci_hcd and address 6
[   32.532268] usb 1-7: configuration #1 chosen from 1 choice
[   32.538321] scsi6 : SCSI emulation for USB Mass Storage devices
[   32.538366] usb-storage: device found at 3
[   32.538367] usb-storage: waiting for device to settle before scanning
[   32.747873] usb 1-3.1: new full speed USB device using ohci_hcd and address 7
[   32.858776] usb 1-3.1: configuration #1 chosen from 1 choice
[   32.877729] usbcore: registered new interface driver usb-storage
[   32.877732] usbcore: registered new interface driver hiddev
[   32.877737] USB Mass Storage support registered.
[   32.881854] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:0b.0/usb1/1-7/1-7:1.0/input/input1
[   32.911281] input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:0b.0-7
[   32.920698] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:0b.0/usb1/1-7/1-7:1.1/input/input2
[   32.933763] input,hiddev96,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:0b.0-7
[   32.938770] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:0b.0/usb1/1-3/1-3.1/1-3.1:1.0/input/input3
[   32.953704] input,hidraw2: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:0b.0-3.1
[   32.963600] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:0b.0/usb1/1-3/1-3.1/1-3.1:1.1/input/input4
[   32.981660] input,hidraw3: USB HID v1.10 Device [Dell Dell USB Keyboard] on usb-0000:00:0b.0-3.1
[   32.981671] usbcore: registered new interface driver usbhid
[   32.981674] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   33.093922] kjournald starting.  Commit interval 5 seconds
[   33.093930] EXT3-fs: sda1: orphan cleanup on readonly fs
[   33.093936] ext3_orphan_cleanup: deleting unreferenced inode 3884752
[   33.093962] ext3_orphan_cleanup: deleting unreferenced inode 3884713
[   33.093971] ext3_orphan_cleanup: deleting unreferenced inode 3884651
[   33.093989] ext3_orphan_cleanup: deleting unreferenced inode 4710411
[   33.093996] ext3_orphan_cleanup: deleting unreferenced inode 4644870
[   33.094001] ext3_orphan_cleanup: deleting unreferenced inode 4644869
[   33.094005] ext3_orphan_cleanup: deleting unreferenced inode 4644868
[   33.094008] ext3_orphan_cleanup: deleting unreferenced inode 4644867
[   33.094012] ext3_orphan_cleanup: deleting unreferenced inode 4644866
[   33.094016] EXT3-fs: sda1: 9 orphan inodes deleted
[   33.094017] EXT3-fs: recovery complete.
[   33.114505] EXT3-fs: mounted filesystem with ordered data mode.
[   37.632332] usb-storage: device scan complete
[   37.652711] scsi 6:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
[   37.656840] sd 6:0:0:0: [sde] Attached SCSI removable disk
[   37.656869] sd 6:0:0:0: Attached scsi generic sg5 type 0
[   37.758990] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   37.811818] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   37.812658] shpchp: Unknown symbol acpi_run_oshp
[   37.812715] shpchp: Unknown symbol pci_hp_change_slot_info
[   37.812786] shpchp: Unknown symbol pci_hp_register
[   37.812964] shpchp: Unknown symbol pci_hp_deregister
[   37.813105] shpchp: Unknown symbol acpi_get_hp_params_from_firmware
[   37.865798] parport_pc 00:09: reported by Plug and Play ACPI
[   37.865824] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   37.982122] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
[   37.982137] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x1c80
[   38.066458] input: Power Button (FF) as /devices/virtual/input/input6
[   38.085825] ACPI: Power Button (FF) [PWRF]
[   38.085868] input: Power Button (CM) as /devices/virtual/input/input7
[   38.117771] ACPI: Power Button (CM) [PWRB]
[   38.165820] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   38.451182] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[   38.451188] ACPI: PCI Interrupt 0000:09:06.0[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 21
[   38.457583] phy0: Selected rate control algorithm 'simple'
[   38.556008] Linux agpgart interface v0.102
[   38.691493] nvidia: module license 'NVIDIA' taints kernel.
[   38.943038] ACPI: PCI Interrupt Link [APC5] enabled at IRQ 16
[   38.943044] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [APC5] -> GSI 16 (level, low) -> IRQ 21
[   38.943053] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   38.943165] NVRM: loading NVIDIA UNIX x86 Kernel Module  177.80  Wed Oct  1 14:38:10 PDT 2008
[   38.999068] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 22
[   38.999071] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [AAZA] -> GSI 22 (level, low) -> IRQ 17
[   38.999087] PCI: Setting latency timer of device 0000:00:10.1 to 64
[   39.031134] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   39.182427] lp0: using parport0 (interrupt-driven).
[   39.234178] Adding 5992204k swap on /dev/sda5.  Priority:-1 extents:1 across:5992204k
[   39.772975] EXT3 FS on sda1, internal journal
[   40.439498] kjournald starting.  Commit interval 5 seconds
[   40.439502] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   40.439819] EXT3 FS on sdb5, internal journal
[   40.439821] EXT3-fs: recovery complete.
[   40.439957] EXT3-fs: mounted filesystem with ordered data mode.
[   40.465551] kjournald starting.  Commit interval 5 seconds
[   40.465555] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   40.470275] EXT3 FS on sdd5, internal journal
[   40.470277] EXT3-fs: recovery complete.
[   40.470279] EXT3-fs: mounted filesystem with ordered data mode.
[   40.753950] ip_tables: (C) 2000-2006 Netfilter Core Team

```

the syslog says nothing: (Oct 18 12:27:59 ) was right before the system hung.
```

Oct 18 12:27:50 Simon kernel: [ 8537.117302] wlan0: switched to long barker preamble (BSSID=00:18:f8:67:ea:1e)
Oct 18 12:27:59 Simon kernel: [ 8545.808450] wlan0: switched to short barker preamble (BSSID=00:18:f8:67:ea:1e)
Oct 18 12:29:10 Simon syslogd 1.5.0#1ubuntu1: restart.
Oct 18 12:29:10 Simon kernel: Inspecting /boot/System.map-2.6.24-21-generic
Oct 18 12:29:10 Simon kernel: Loaded 27890 symbols from /boot/System.map-2.6.24-21-generic.

```

same as the kern.log:

```

Oct 18 12:27:59 Simon kernel: [ 8545.808450] wlan0: switched to short barker preamble (BSSID=00:18:f8:67:ea:1e)
Oct 18 12:29:10 Simon kernel: Inspecting /boot/System.map-2.6.24-21-generic
Oct 18 12:29:10 Simon kernel: Loaded 27890 symbols from /boot/System.map-2.6.24-21-generic.
Oct 18 12:29:10 Simon kernel: Symbols match kernel version 2.6.24.

```

and the messages:

```

Oct 18 12:06:01 Simon -- MARK --
Oct 18 12:26:01 Simon -- MARK --
Oct 18 12:29:10 Simon syslogd 1.5.0#1ubuntu1: restart.
Oct 18 12:29:10 Simon kernel: Inspecting /boot/System.map-2.6.24-21-generic

```

If this is related to WoW, here's my Config.wtf:

```

SET gxApi "opengl"
SET Sound_SoundOutputSystem "1"
SET Sound_SoundBufferSize "150"
SET locale "enGB"
SET coresDetected "4"
SET hwDetect "0"
SET gxWindow "1"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1920x1200"
SET gxRefresh "50"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET videoOptionsVersion "1"
SET pixelShaders "1"
SET movie "0"
SET expansionMovie "0"
SET DesktopGamma "1"
SET Gamma "1.000000"
SET readTOS "1"
SET readEULA "1"
SET readTerminationWithoutNotice "1"
SET showToolsUI "1"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET Sound_OutputDriverName "dmix:0"
SET realmList "eu.logon.worldofwarcraft.com"
SET patchlist "eu.version.worldofwarcraft.com"
SET SmallCull "0.010000"
SET DistCull "500.000000"
SET farclip "1277"
SET particleDensity "1.000000"
SET weatherDensity "3"
SET realmName "Trollbane"
SET gameTip "8"
SET uiScale "0.64999997615814"
SET useUiScale "1"
SET showGameTips "0"
SET ChatMusicVolume "0.29999998211861"
SET ChatSoundVolume "0.39999997615814"
SET ChatAmbienceVolume "0.29999998211861"
SET Sound_MasterVolume "1"
SET Sound_SFXVolume "1"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.80000001192093"
SET OutboundChatVolume "1"
SET InboundChatVolume "1"
SET VoiceActivationSensitivity "0.39999997615814"
SET readScanning "-1"
SET readContest "-1"
SET processAffinityMask "3"
SET lod "1"
SET specular "1"
SET groundEffectDensity "64"
SET Sound_OutputQuality "2"
SET Sound_EnableMusic "0"
SET accountName "NNN"
SET Sound_EnableSFX "0"
SET Sound_EnableAmbience "0"
SET checkAddonVersion "0"
SET installType "Retail"
SET portal "eu"
SET mouseSpeed "0.5"
SET gxMultisample "4"
SET textureFilteringMode "5"
SET shadowLevel "0"
SET groundEffectDist "140"
SET environmentDetail "1"
SET Sound_OutputDriverIndex "1"
SET Sound_EnableErrorSpeech "0"
SET Sound_EnableAllSound "0"
SET Sound_EnableEmoteSounds "0"
SET Sound_EnableDSPEffects "0"
SET lastCharacterIndex "3"

```

and Wine user.reg:

```

WINE REGISTRY Version 2
;; All keys relative to \\User\\S-1-5-4

[Control Panel\\Colors] 1215629007

[Control Panel\\Desktop] 1215629009
"DragFullWindows"="0"
"FontSmoothing"="0"
"LowPowerActive"="0"
"MenuShowDelay"="400"
"SmoothScroll"=hex:00,00,00,00
"UserPreferenceMask"=hex:10,00,00,80

[Control Panel\\Desktop\\WindowMetrics] 1224326836
"BorderWidth"="1"
"CaptionFont"=hex:f5,ff,ff,ff,00,00,00,00,00,00,00,00,00,00,00,00,bc,02,00,00,\
  00,00,00,00,00,00,00,00,4d,00,53,00,20,00,53,00,68,00,65,00,6c,00,6c,00,20,\
  00,44,00,6c,00,67,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,\
  00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00
"CaptionHeight"="18"
"CaptionWidth"="18"
"MenuFont"=hex:f5,ff,ff,ff,00,00,00,00,00,00,00,00,00,00,00,00,90,01,00,00,00,\
  00,00,00,00,00,00,00,4d,00,53,00,20,00,53,00,68,00,65,00,6c,00,6c,00,20,00,\
  44,00,6c,00,67,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,\
  00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00
"MenuHeight"="18"
"MenuWidth"="18"
"MessageFont"=hex:f5,ff,ff,ff,00,00,00,00,00,00,00,00,00,00,00,00,90,01,00,00,\
  00,00,00,00,00,00,00,00,4d,00,53,00,20,00,53,00,68,00,65,00,6c,00,6c,00,20,\
  00,44,00,6c,00,67,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,\
  00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00
"ScrollHeight"="16"
"ScrollWidth"="16"
"Shell Icon Size"="32"
"SmCaptionFont"=hex:f5,ff,ff,ff,00,00,00,00,00,00,00,00,00,00,00,00,90,01,00,\
  00,00,00,00,00,00,00,00,00,4d,00,53,00,20,00,53,00,68,00,65,00,6c,00,6c,00,\
  20,00,44,00,6c,00,67,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,\
  00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00
"SmCaptionHeight"="15"
"SmCaptionWidth"="13"
"StatusFont"=hex:f5,ff,ff,ff,00,00,00,00,00,00,00,00,00,00,00,00,90,01,00,00,\
  00,00,00,00,00,00,00,00,4d,00,53,00,20,00,53,00,68,00,65,00,6c,00,6c,00,20,\
  00,44,00,6c,00,67,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,\
  00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00

[Control Panel\\International] 1215629006
"iCalendarType"="1"
"iCountry"="47"
"iCurrDigits"="2"
"iCurrency"="2"
"iDate"="1"
"iDigits"="2"
"iFirstDayOfWeek"="0"
"iFirstWeekOfYear"="2"
"iLDate"="1"
"iLZero"="1"
"iMeasure"="0"
"iNegCurr"="12"
"iNegNumber"="1"
"iPaperSize"="9"
"iTime"="1"
"iTimePrefix"="0"
"iTLZero"="1"
"LC_CTYPE"="00000414"
"LC_MEASUREMENT"="00000414"
"LC_MONETARY"="00000414"
"LC_NUMERIC"="00000414"
"LC_PAPER"="00000414"
"LC_TELEPHONE"="00000414"
"LC_TIME"="00000414"
"Locale"="00000414"
"Numshape"="1"
"s1159"=""
"s2359"=""
"sCountry"="Norway"
"sCurrency"="kr"
"sDate"="."
"sDecimal"=","
"sGrouping"="3;0"
"sLanguage"="Norwegian (Bokmal)"
"sList"=";"
"sLongDate"="d. MMMM yyyy"
"sMonDecimalSep"=","
"sMonGrouping"="3;0"
"sMonThousandSep"="\xa0"
"sNativeDigits"="0123456789"
"sNegativeSign"="-"
"sPositiveSign"=""
"sShortDate"="dd.MM.yyyy"
"sThousand"="\xa0"
"sTime"=":"
"sTimeFormat"="HH:mm:ss"
"sYearMonth"="MMMM yyyy"

[Software\\Blizzard Entertainment\\Blizzard Downloader] 1224093846
"Disable Peer-to-Peer"=dword:00000001
"Full Speed Background Download"=dword:00000001

[Software\\Blizzard Entertainment\\Internal] 1215630196
"CpuTicksPerSecond"=hex:7b,74,03,95,00,00,00,00

[Software\\Blizzard Entertainment\\World of Warcraft] 1222099448
"Survey"=dword:000000d3

[Software\\Blizzard Entertainment\\World of Warcraft\\Client] 1224095382
"HWCpuIdx"=dword:00000001
"HWMemIdx"=dword:00000000
"HWSoundIdx"=dword:00000000
"HWVideoID"=dword:000002b5
"MoveLogFile"="ClientMovement.txt"
"SendErrorLogs"=dword:00000001

[Software\\IGA] 1215813607
"userid"=hex(b):26,3e,17,07,00,00,00,00

[Software\\Microsoft\\Installer\\Features\\9C8928403D4AB094F99FBA20A329833F] 1215639199
"Steam_Base"=hex(1):

[Software\\Microsoft\\Installer\\Products\\9C8928403D4AB094F99FBA20A329833F] 1215639199
"AuthorizedLUAApp"=dword:00000000
"Language"=dword:00000409
"PackageCode"="{524477CC-C44B-45C9-9FBB-7BD0D1FA399F}"
"PackageName"="SteamInstall.msi"
"ProductName"="Steam"
"Version"=dword:01000000

[Software\\Microsoft\\Installer\\Products\\9C8928403D4AB094F99FBA20A329833F\\SourceList] 1215639199
"LastUsedSource"="n;1;C:\\windows\\temp\\Cab2e41.tmp"
"PackageName"="SteamInstall.msi"

[Software\\Microsoft\\Installer\\Products\\9C8928403D4AB094F99FBA20A329833F\\SourceList\\Media] 1215639199
"DiskPrompt"=""
"MediaPackage"=""

[Software\\Microsoft\\Installer\\Products\\9C8928403D4AB094F99FBA20A329833F\\SourceList\\Net] 1215639199
"1"=str(2):"C:\\windows\\temp\\Cab2e41.tmp\\"

[Software\\Microsoft\\Installer\\UpgradeCodes\\1240E0B02B2BA4B4EBAC38FB29D468DB] 1215639199
"9C8928403D4AB094F99FBA20A329833F"=hex(1):

[Software\\Microsoft\\Internet Explorer\\Main] 1215629008
"Search Page"="http://www.google.com"
"Start Page"="http://www.winehq.org"

[Software\\Microsoft\\Protected Storage System Provider] 1215629009
@=""

[Software\\Microsoft\\Windows\\CurrentVersion\\Explorer\\Advanced] 1219776540

[Software\\Microsoft\\Windows\\CurrentVersion\\Explorer\\Shell Folders] 1215629008
"AppData"="C:\\windows\\profiles\\alexander\\Programdata"
"Cache"="C:\\windows\\profiles\\alexander\\Lokale innstillinger\\Temporary Internet Files"
"Cookies"="C:\\windows\\profiles\\alexander\\Cookies"
"Desktop"="C:\\windows\\profiles\\alexander\\Skrivebord"
"Favorites"="C:\\windows\\profiles\\alexander\\Favoritter"
"Fonts"="C:\\windows\\Fonts"
"History"="C:\\windows\\profiles\\alexander\\Lokale innstillinger\\Logg"
"Local AppData"="C:\\windows\\profiles\\alexander\\Lokale innstillinger\\Programdata"
"My Music"="C:\\windows\\profiles\\alexander\\Min musikk"
"My Pictures"="C:\\windows\\profiles\\alexander\\Mine bilder"
"My Videos"="C:\\windows\\profiles\\alexander\\Mine videoklipp"
"NetHood"="C:\\windows\\profiles\\alexander\\NetHood"
"Personal"="C:\\windows\\profiles\\alexander\\Mine dokumenter"
"PrintHood"="C:\\windows\\profiles\\alexander\\Skrivere"
"Programs"="C:\\windows\\profiles\\alexander\\Start-meny\\Programmer"
"Recent"="C:\\windows\\profiles\\alexander\\Siste"
"SendTo"="C:\\windows\\profiles\\alexander\\SendTo"
"Start Menu"="C:\\windows\\profiles\\alexander\\Start-meny"
"StartUp"="C:\\windows\\profiles\\alexander\\Start-meny\\Programmer\\Oppstart"
"Templates"="C:\\windows\\profiles\\alexander\\Maler"

[Software\\Microsoft\\Windows\\CurrentVersion\\Explorer\\User Shell Folders] 1215629008
"AppData"=str(2):"%USERPROFILE%\\Programdata"
"Cache"=str(2):"%USERPROFILE%\\Lokale innstillinger\\Temporary Internet Files"
"Cookies"=str(2):"%USERPROFILE%\\Cookies"
"Desktop"=str(2):"%USERPROFILE%\\Skrivebord"
"Favorites"=str(2):"%USERPROFILE%\\Favoritter"
"Fonts"=str(2):"C:\\windows"
"History"=str(2):"%USERPROFILE%\\Lokale innstillinger\\Logg"
"Local AppData"=str(2):"%USERPROFILE%\\Lokale innstillinger\\Programdata"
"My Music"=str(2):"%USERPROFILE%\\Min musikk"
"My Pictures"=str(2):"%USERPROFILE%\\Mine bilder"
"My Videos"=str(2):"%USERPROFILE%\\Mine videoklipp"
"NetHood"=str(2):"%USERPROFILE%\\NetHood"
"Personal"=str(2):"%USERPROFILE%\\Mine dokumenter"
"PrintHood"=str(2):"%USERPROFILE%\\Skrivere"
"Programs"=str(2):"%USERPROFILE%\\Start-meny\\Programmer"
"Recent"=str(2):"%USERPROFILE%\\Siste"
"SendTo"=str(2):"%USERPROFILE%\\SendTo"
"Start Menu"=str(2):"%USERPROFILE%\\Start-meny"
"StartUp"=str(2):"%USERPROFILE%\\Start-meny\\Programmer\\Oppstart"
"Templates"=str(2):"%USERPROFILE%\\Maler"

[Software\\Microsoft\\Windows\\CurrentVersion\\Internet Settings] 1215629698
@=""
"ProxyEnable"=dword:00000000

[Software\\Microsoft\\Windows\\CurrentVersion\\Internet Settings\\User Agent\\Post Platform] 1219776542
@=""

[Software\\Microsoft\\Windows\\CurrentVersion\\Internet Settings\\ZoneMap] 1215629009
@=""
"IntranetName"=dword:00000001
"ProxyByPass"=dword:00000001
"UNCAsIntranet"=dword:00000001

[Software\\Microsoft\\Windows\\CurrentVersion\\Internet Settings\\ZoneMap\\Domains] 1215629009
@=""

[Software\\Microsoft\\Windows\\CurrentVersion\\Internet Settings\\ZoneMap\\ProtocolDefaults] 1215629009
@=""
"@ivt"=dword:00000001
"file"=dword:00000003
"ftp"=dword:00000003
"http"=dword:00000003
"https"=dword:00000003

[Software\\Microsoft\\Windows\\CurrentVersion\\Internet Settings\\ZoneMap\\Ranges] 1215629009
@=""

[Software\\Microsoft\\Windows\\CurrentVersion\\Internet Settings\\Zones] 1215629009
@=""

[Software\\Microsoft\\Windows\\CurrentVersion\\Internet Settings\\Zones\\0] 1215629009
@=""
"1001"=dword:00000000
"1004"=dword:00000000
"1200"=dword:00000000
"1201"=dword:00000001
"1400"=dword:00000000
"1402"=dword:00000000
"1405"=dword:00000000
"1406"=dword:00000000
"1407"=dword:00000000
"1601"=dword:00000000
"1604"=dword:00000000
"1605"=dword:00000000
"1606"=dword:00000000
"1607"=dword:00000000
"1608"=dword:00000000
"1609"=dword:00000001
"1800"=dword:00000000
"1802"=dword:00000000
"1803"=dword:00000000
"1804"=dword:00000000
"1805"=dword:00000000
"1A00"=dword:00000000
"1A02"=dword:00000000
"1A03"=dword:00000000
"1A04"=dword:00000000
"1A05"=dword:00000000
"1A06"=dword:00000000
"1A10"=dword:00000000
"1C00"=dword:00020000
"1E05"=dword:00030000
"CurrentLevel"=dword:00000000
"Description"="Your computer"
"DisplayName"="My Computer"
"Flags"=dword:00000021
"Icon"="explorer.exe#0100"

[Software\\Microsoft\\Windows\\CurrentVersion\\Internet Settings\\Zones\\1] 1215629009
@=""
"1001"=dword:00000001
"1004"=dword:00000003
"1200"=dword:00000000
"1201"=dword:00000003
"1400"=dword:00000000
"1402"=dword:00000000
"1405"=dword:00000000
"1406"=dword:00000001
"1407"=dword:00000000
"1601"=dword:00000000
"1604"=dword:00000000
"1605"=dword:00000000
"1606"=dword:00000000
"1607"=dword:00000000
"1608"=dword:00000000
"1609"=dword:00000001
"1800"=dword:00000001
"1802"=dword:00000000
"1803"=dword:00000000
"1804"=dword:00000001
"1805"=dword:00000000
"1A00"=dword:00020000
"1A02"=dword:00000000
"1A03"=dword:00000000
"1A04"=dword:00000000
"1A05"=dword:00000000
"1A06"=dword:00000000
"1A10"=dword:00000000
"1C00"=dword:00020000
"1E05"=dword:00020000
"CurrentLevel"=dword:00010500
"Description"="This zone contains all Web sites that are on your organization's intranet."
"DisplayName"="Local intranet"
"Flags"=dword:000000db
"Icon"="shell32.dll#0018"
"MinLevel"=dword:00010000
"RecommendedLevel"=dword:00010500

[Software\\Microsoft\\Windows\\CurrentVersion\\Internet Settings\\Zones\\2] 1215629009
@=""
"1001"=dword:00000000
"1004"=dword:00000001
"1200"=dword:00000000
"1201"=dword:00000001
"1400"=dword:00000000
"1402"=dword:00000000
"1405"=dword:00000000
"1406"=dword:00000000
"1407"=dword:00000000
"1601"=dword:00000000
"1604"=dword:00000000
"1605"=dword:00000000
"1606"=dword:00000000
"1607"=dword:00000000
"1608"=dword:00000000
"1609"=dword:00000001
"1800"=dword:00000000
"1802"=dword:00000000
"1803"=dword:00000000
"1804"=dword:00000000
"1805"=dword:00000000
"1A00"=dword:00000000
"1A02"=dword:00000000
"1A03"=dword:00000000
"1A04"=dword:00000000
"1A05"=dword:00000000
"1A06"=dword:00000000
"1A10"=dword:00000000
"1C00"=dword:00030000
"1E05"=dword:00030000
"CurrentLevel"=dword:00010000
"Description"="This zone contains Web sites that you trust not to damage your computer or data."
"DisplayName"="Trusted sites"
"Flags"=dword:00000047
"Icon"="inetcpl.cpl#00004480"
"MinLevel"=dword:00010000
"RecommendedLevel"=dword:00010000

[Software\\Microsoft\\Windows\\CurrentVersion\\Internet Settings\\Zones\\3] 1215629009
@=""
"1001"=dword:00000001
"1004"=dword:00000003
"1200"=dword:00000000
"1201"=dword:00000003
"1400"=dword:00000000
"1402"=dword:00000000
"1405"=dword:00000000
"1406"=dword:00000003
"1407"=dword:00000000
"1601"=dword:00000001
"1604"=dword:00000000
"1605"=dword:00000000
"1606"=dword:00000000
"1607"=dword:00000000
"1608"=dword:00000000
"1609"=dword:00000001
"1800"=dword:00000001
"1802"=dword:00000000
"1803"=dword:00000000
"1804"=dword:00000001
"1805"=dword:00000001
"1A00"=dword:00020000
"1A02"=dword:00000000
"1A03"=dword:00000000
"1A04"=dword:00000003
"1A05"=dword:00000001
"1A06"=dword:00000000
"1A10"=dword:00000001
"1C00"=dword:00010000
"1E05"=dword:00020000
"CurrentLevel"=dword:00011000
"Description"="This zone contains all Web sites you haven't placed in other zones"
"DisplayName"="Internet"
"Flags"=dword:00000001
"Icon"="inetcpl.cpl#001313"
"MinLevel"=dword:00011000
"RecommendedLevel"=dword:00011000

[Software\\Microsoft\\Windows\\CurrentVersion\\Internet Settings\\Zones\\4] 1215629009
@=""
"1001"=dword:00000003
"1004"=dword:00000003
"1200"=dword:00000003
"1201"=dword:00000003
"1400"=dword:00000003
"1402"=dword:00000003
"1405"=dword:00000003
"1406"=dword:00000003
"1407"=dword:00000003
"1601"=dword:00000001
"1604"=dword:00000001
"1605"=dword:00000000
"1606"=dword:00000003
"1607"=dword:00000003
"1608"=dword:00000003
"1609"=dword:00000001
"1800"=dword:00000003
"1802"=dword:00000001
"1803"=dword:00000003
"1804"=dword:00000003
"1805"=dword:00000001
"1A00"=dword:00010000
"1A02"=dword:00000003
"1A03"=dword:00000003
"1A04"=dword:00000003
"1A05"=dword:00000003
"1A06"=dword:00000003
"1A10"=dword:00000003
"1C00"=dword:00000000
"1E05"=dword:00010000
"CurrentLevel"=dword:00012000
"Description"="This zone contains Web sites that could potentially damage your computer or data."
"DisplayName"="Restricted sites"
"Flags"=dword:00000003
"Icon"="inetcpl.cpl#00004481"
"MinLevel"=dword:00012000
"RecommendedLevel"=dword:00012000

[Software\\Microsoft\\Windows\\CurrentVersion\\Run] 1215639199
"Steam"="\"C:\\Programfiler\\Steam\\Steam.exe\" -silent"

[Software\\Microsoft\\Windows NT\\CurrentVersion\\Devices] 1215786566
"PDF"="WINEPS.DRV,LPR:PDF"
"Photosmart_C7100"="WINEPS.DRV,LPR:Photosmart_C7100"
"Photosmart_C7100_fax"="WINEPS.DRV,LPR:Photosmart_C7100_fax"

[Software\\Microsoft\\Windows NT\\CurrentVersion\\PrinterPorts] 1215953690
"PDF"="WINEPS.DRV,LPR:PDF,15,45"
"Photosmart_C7100"="WINEPS.DRV,LPR:Photosmart_C7100,15,45"
"Photosmart_C7100_fax"="WINEPS.DRV,LPR:Photosmart_C7100_fax,15,45"

[Software\\Microsoft\\Windows NT\\CurrentVersion\\Windows] 1215629009
"Device"="PDF,WINEPS.DRV,LPR:PDF"

[Software\\Spidersoft\\WebZIP 7] 1219776541
"Vers"="7.0.3.1030"

[Software\\Spidersoft\\WebZIP 7\\Settings] 1219776542
"Connections"=dword:00000003
"Last Category"="General"
"Last Task"="C:\\windows\\profiles\\alexander\\Mine dokumenter\\My WebZIP Projects\\General"
"MyWebsitesFolder"="C:\\windows\\profiles\\alexander\\Mine dokumenter\\My WebZIP Sites\\"
"Start MyWebZIP"=dword:00000001

[Software\\Valve\\Half-Life\\cstrike\\Settings] 1215813606
"User Token 2"=""
"User Token 3"=""

[Software\\Valve\\Half-Life\\dod\\Settings] 1215814887
"User Token 2"=""
"User Token 3"=""

[Software\\Valve\\Half-Life\\Settings] 1215814886
"CrashInitializingVideoMode"=dword:00000000
"DELV"=dword:00000002
"EngineD3D"=dword:00000000
"EngineDLL"="hw.dll"
"io"=""
"ScreenBPP"=dword:00000020
"ScreenHeight"=dword:000004b0
"ScreenWidth"=dword:00000780
"ScreenWindowed"=dword:00000000
"User Token 2"=""
"User Token 3"=""

[Software\\Valve\\Source\\dod\\Settings] 1215821125
"AutoConfigVersion"=dword:00000001
"DeviceID"=dword:0000014f
"DXLevel_V1"=dword:0000005f
"mat_aaquality"=dword:00000000
"mat_antialias"=dword:00000000
"mat_bumpmap"=dword:00000001
"mat_colorcorrection"=dword:00000001
"mat_forceaniso"=dword:00000001
"mat_forcehardwaresync"=dword:00000001
"mat_hdr_level"=dword:00000000
"mat_parallaxmap"=dword:00000000
"mat_picmip"=dword:00000002
"mat_reducefillrate"=dword:00000000
"mat_specular"=dword:00000001
"mat_trilinear"=dword:00000001
"mat_vsync"=dword:00000000
"MotionBlur"=dword:00000000
"r_rootlod"=dword:00000000
"r_shadowrendertotexture"=dword:00000001
"r_waterforceexpensive"=dword:00000001
"r_waterforcereflectentities"=dword:00000000
"ScreenHeight"=dword:000002d0
"ScreenMonitorGamma"="2.2"
"ScreenMSAA"=dword:00000000
"ScreenMSAAQuality"=dword:00000000
"ScreenWidth"=dword:00000500
"ScreenWindowed"=dword:00000001
"ShadowDepthTexture"=dword:00000001
"User Token 2"=""
"User Token 3"=""
"VendorID"=dword:000010de

[Software\\Valve\\Source\\Settings] 1215820995
"User Token 2"=""
"User Token 3"=""

[Software\\Valve\\Steam] 1222607507
"AlreadyRetriedOfflineMode"=dword:00000000
"AutoLaunchGameListCheck"=dword:00000000
"DesktopShortcutCheck"=dword:00000001
"KnownCachesHash"=dword:14229414
"Language"="norwegian"
"LastContentProviderURL"="http://cdn.steampowered.com/platform/banner/cs_25.html"
"LastCSBannerURL"="http://cdn.steampowered.com/platform/banner/cs_25.html"
"LastGameNameUsed"="phun-ky"
"ModInstallPath"="c:\\programfiler\\steam\\steamapps\\phun-ky\\half-life"
"Offline"=dword:00000000
"OfflineAFS"=dword:00000000
"PrevLang"="mlidvtrzm"
"PrevLV"=dword:00000000
"PseudoUUID"="74dbd1eba54fdd11"
"Rate"="30000"
"RefreshLoginRequired"=dword:00000000
"Restart"=dword:00000000
"Skin"=""
"SourceModInstallPath"="c:\\programfiler\\steam\\SteamApps\\SourceMods"
"SSAVersion"=dword:00000001
"StartMenuShortcutCheck"=dword:00000001
"SteamExe"="c:/programfiler/steam/steam.exe"
"SteamPath"="c:/programfiler/steam"
"SuppressAutoRun"=dword:00000000
"SurveyDate"="2008-05-22"
"TempAppCmdLine"=""
"TempAppPath"=""
"UpIM"=dword:00000001

[Software\\Valve\\Steam\\ActiveProcess] 1215812755
"pid"=dword:00000008
"SteamClientDll"="C:\\Programfiler\\Steam\\steamclient.dll"
"Universe"="Public"

[Software\\Valve\\Steam\\Apps\\10] 1215813603
"CacheAggTime"=dword:0000014b
"CacheStartTime"=dword:00000000
"Installed"=dword:00000001
"Launched"="1"
"maintenance_time"=dword:4877d7df
"MFPAggTime"=dword:ffffffff
"MFPStartTime"=dword:ffffffff
"UpdateBytesToDL"=dword:00000000
"UpToDate"=dword:00000001

[Software\\Valve\\Steam\\Apps\\130] 1215639360
"UpdateBytesToDL"=dword:00000000
"UpToDate"=dword:00000000

[Software\\Valve\\Steam\\Apps\\19200] 1215813581
"Installed"=dword:00000001
"UpdateBytesToDL"=dword:00000000
"UpToDate"=dword:00000001

[Software\\Valve\\Steam\\Apps\\20] 1215639360
"UpdateBytesToDL"=dword:00000000
"UpToDate"=dword:00000000

[Software\\Valve\\Steam\\Apps\\205] 1215639360
"UpdateBytesToDL"=dword:00000000
"UpToDate"=dword:00000000

[Software\\Valve\\Steam\\Apps\\211] 1215639360
"UpdateBytesToDL"=dword:00000000
"UpToDate"=dword:00000000

[Software\\Valve\\Steam\\Apps\\2145] 1215639360
"UpdateBytesToDL"=dword:00000000
"UpToDate"=dword:00000000

[Software\\Valve\\Steam\\Apps\\215] 1215639360
"UpdateBytesToDL"=dword:00000000
"UpToDate"=dword:00000000

[Software\\Valve\\Steam\\Apps\\218] 1215639360
"UpdateBytesToDL"=dword:00000000
"UpToDate"=dword:00000000

[Software\\Valve\\Steam\\Apps\\219] 1215820387
"Installed"=dword:00000001
"UpdateBytesToDL"=dword:00000000
"UpToDate"=dword:00000001

[Software\\Valve\\Steam\\Apps\\220] 1222608334
"CacheAggTime"=dword:ffffffff
"CacheStartTime"=dword:ffffffff
"EnableCacheLoading"=dword:00000001
"Installed"=dword:00000001
"UpdateBytesToDL"=dword:00000000
"UpToDate"=dword:00000001

[Software\\Valve\\Steam\\Apps\\2403] 1215639360
"UpdateBytesToDL"=dword:00000000
"UpToDate"=dword:00000000

[Software\\Valve\\Steam\\Apps\\30] 1215814880
"CacheAggTime"=dword:0000013c
"CacheStartTime"=dword:4877dce0
"Installed"=dword:00000001
"Launched"="1"
"maintenance_time"=dword:4877dcdf
"MFPAggTime"=dword:ffffffff
"MFPStartTime"=dword:ffffffff
"UpdateBytesToDL"=dword:00000000
"UpToDate"=dword:00000001

[Software\\Valve\\Steam\\Apps\\300] 1221254028
"CacheAggTime"=dword:ffffffff
"CacheStartTime"=dword:ffffffff
"EnableCacheLoading"=dword:00000001
"Installed"=dword:00000001
"language"=dword:00000000
"Launched"="1"
"maintenance_time"=dword:48cadb5a
"MFPAggTime"=dword:ffffffff
"MFPStartTime"=dword:ffffffff
"UpdateBytesToDL"=dword:00000000
"UpToDate"=dword:00000001

[Software\\Valve\\Steam\\Apps\\300\\vid] 1215820954
"deviceid"=dword:0000014f
"dxsupport_crc"=dword:fb751941
"nowarnifoutdated"=dword:00000000
"nowarnifunknown"=dword:00000000
"nowarnifunsupported"=dword:00000000
"unknowninfouploaded"=dword:00000000
"vendorid"=dword:000010de

[Software\\Valve\\Steam\\Apps\\310] 1215639360
"UpdateBytesToDL"=dword:00000000
"UpToDate"=dword:00000000

[Software\\Valve\\Steam\\Apps\\40] 1215639360
"UpdateBytesToDL"=dword:00000000
"UpToDate"=dword:00000000

[Software\\Valve\\Steam\\Apps\\5] 1215639360
"UpdateBytesToDL"=dword:00000000
"UpToDate"=dword:00000000

[Software\\Valve\\Steam\\Apps\\50] 1215639360
"UpdateBytesToDL"=dword:00000000
"UpToDate"=dword:00000000

[Software\\Valve\\Steam\\Apps\\60] 1215639360
"UpdateBytesToDL"=dword:00000000
"UpToDate"=dword:00000000

[Software\\Valve\\Steam\\Apps\\7] 1216760262
"EnableCacheLoading"=dword:00000001
"Installed"=dword:00000001
"UpdateBytesToDL"=dword:00000000
"UpToDate"=dword:00000001

[Software\\Valve\\Steam\\Apps\\70] 1216760014
"CacheAggTime"=dword:ffffffff
"CacheStartTime"=dword:ffffffff
"Installed"=dword:00000001
"UpdateBytesToDL"=dword:00000000
"UpToDate"=dword:00000001

[Software\\Valve\\Steam\\Beta] 1215639201

[Software\\Valve\\Steam\\Steam.exe] 1222609447
"CheckingForUpdates"=dword:00000000
"LastUpload"=dword:48df7d42
"ReliabilitySignal"=dword:00000000
"ShutdownFailureCount"=dword:00000000
"SuccessCount"=dword:00000002
"UnknownFailureCount"=dword:00000001
"UpdateAvailable"=dword:00000000
"UpdateBytesDownloaded"=dword:00000000
"UpdateBytesToDownload"=dword:00000000
"UpTimeCleanCounter"=dword:00000000
"UpTimeCleanTotal"=dword:00000000
"UpTimeFailureCounter"=dword:00000001
"UpTimeFailureTotal"=dword:00000492
"UpTimeMostRecent"=dword:00000000
"UpTimeStart"=dword:00000000

[Software\\Valve\\Steam\\Users\\4671164] 1215639323
"licenses"=hex:01,00,00,00,2f,f5,0e,57,e5,ba,e1,7c,22,04,0e,15,df,d8,03,d2,a6,\
  29,a0,98,24,0b,1c,af,b0,b0,00,c2,6d,5c,b5,5c,6d,2b,8a,29,a3,43,cc,40,e9,b7,\
  b6,c2,08,c3,7c,4b,0c,0d,3c,6d,ca,52,07,04,77,9b,bd,69,4b,71,a0,04,63,d4,49,\
  bd,9e,d6,13,d9,16,d8,f0,fb,93,34,17,ba,88,30,27,49,76,bb,84,64,85,4d,1f,27,\
  00,c0,3c,68,2b,2a,3b,a2,ba,f6,af,f3,3b,c0,8f,29,4d,94,87,55,72,be,0c,90,9d,\
  a6,2f,95,6f,10,4d,eb,b6,1d,b1,ee,f8,45,8a,bc,e6,a5,54,5c,7a,de,4c,31,fa,f3,\
  d1,77,12,a2,18,33,72,7d,35,ef,86,81,ea,ee,1a,21,49,c8,fd,c6,46,f4,ae,fc,5f,\
  2c,1b,ad,b2,2c,ac,e2,e0,ff,bd,87,89,ba,c2,89,55,18,19,4e,41,34,82,94,55,0e,\
  73,39,9e,31,98,26,f2,32,43,87,39,ed,f8,74,5c,c5,32,5c,87,f0,69,f8,78,70,a6,\
  73,4c,6c,7c,c4,b0,27,45,45,2e,06,e5,02,57,57,1f,cc,45,e3,ca,dc,ba,aa,6e,f6,\
  c7,75,ce,aa,a4,26,73,66,65,94,83,6e,45,94,1c,ca,6f,d7,94,57,bb,ef,6a,36,d5,\
  a7,c6,7b,28,5c,3c,3c,04,2b,a1,7d,e8,27,95,fa,4c,e9,25,59,78,e1,fd,6e,b6,86,\
  50,8b,64,dc,1f,4d,19,a3,ec,87,63,47,4a,f9,9d,36,eb,1b,b5,9e,31,31,ca,d7,f2,\
  5e,74,02,06,28,a1,87,c0,e7,92,38,82,07,56,75,df,9e,50,4d,0e,40,c5,c0,b4,5b,\
  e3,e5,a9,68,68,ad,2b,da,e1,0e,08,08,fd,af,ff,3c
"vbc"=dword:00000000

[Software\\Valve\\Steam\\Users\\4671164\\apptickets] 1222606211
"0"=hex:2e,00,00,00,03,00,00,00,bc,46,47,00,01,00,10,01,00,00,00,00,c7,bf,10,\
  3e,65,01,a8,c0,00,00,00,00,62,7d,df,48,e2,2c,fb,48,01,00,01,00,00,00,32,3c,\
  69,af,66,fa,3f,7f,35,5a,3f,c0,d6,da,ff,57,12,e6,f2,0e,5f,b3,f9,29,54,46,04,\
  21,6b,89,43,ab,bf,2a,d6,b2,ab,54,38,fa,be,72,f5,84,72,31,c3,a0,72,06,ca,01,\
  1c,9b,43,37,d8,39,a9,9a,1d,80,d5,ef,aa,52,ae,d5,f1,94,f2,92,fb,31,31,66,23,\
  d1,55,bf,98,1f,dd,4b,b7,fb,d9,ca,71,0e,94,02,e2,36,e1,0f,02,f4,ad,bd,84,5b,\
  72,b7,3f,23,49,67,fb,c7,b9,43,d9,67,37,2a,c0,29,35,03,3f,a2,15,d9,37,f1,27,\
  ee
"10"=hex:2e,00,00,00,03,00,00,00,bc,46,47,00,01,00,10,01,0a,00,00,00,c7,bf,10,\
  3e,65,01,a8,c0,00,00,00,00,6f,7d,df,48,ef,2c,fb,48,01,00,01,00,00,00,6a,7b,\
  76,67,a0,7f,2c,fc,e0,0a,ba,59,2e,69,9b,f3,fe,f0,5d,95,6f,1a,0c,de,b4,d5,43,\
  62,b3,30,e7,8d,04,70,06,6e,a5,8f,77,e7,5a,46,7d,ac,85,fd,67,0e,b8,d5,04,71,\
  d1,be,cf,1d,8e,0a,b8,13,36,a3,5f,c7,63,ad,f6,7d,55,a4,b0,f5,68,db,90,4e,15,\
  75,93,7b,4f,cb,8f,3b,37,00,3f,b1,e0,61,03,d5,dd,c4,1f,34,a3,b3,1c,8a,78,12,\
  f3,90,14,03,96,95,db,1e,7f,f6,fd,85,16,5f,f2,91,71,68,aa,17,c8,e0,08,88,84,\
  b1
"219"=hex:2e,00,00,00,03,00,00,00,bc,46,47,00,01,00,10,01,db,00,00,00,c7,bf,10,\
  3e,65,01,a8,c0,00,00,00,00,6f,7d,df,48,ef,2c,fb,48,01,00,00,00,00,00,b7,6e,\
  34,3e,41,e4,b4,44,8b,fc,b0,30,e9,10,cb,f8,f7,0f,f3,15,83,00,7a,a7,fa,95,e4,\
  d5,93,c1,a9,ae,23,fc,36,89,11,ba,35,af,79,77,98,e3,45,91,af,53,85,86,e9,08,\
  bc,a1,f3,4a,34,6e,33,a8,31,8b,3e,28,7d,2a,f5,f2,8d,53,fa,cf,5f,0a,df,7e,5c,\
  16,7b,ea,4d,9b,d9,a6,b8,7a,b0,43,cc,ac,78,4e,19,d9,81,38,3d,9d,e0,26,6f,d5,\
  2a,9b,b0,71,3f,df,a7,67,51,c8,3d,bb,73,c6,49,54,34,e4,62,5e,4b,65,ed,da,66,\
  55
"220"=hex:2e,00,00,00,03,00,00,00,bc,46,47,00,01,00,10,01,dc,00,00,00,c7,bf,10,\
  3e,65,01,a8,c0,00,00,00,00,6f,7d,df,48,ef,2c,fb,48,01,00,d6,01,00,00,31,3f,\
  b3,f5,51,b7,a5,3b,79,f1,77,f5,d4,a1,66,12,d7,c7,a1,6d,87,05,4f,37,3d,c6,3c,\
  52,79,25,19,76,6b,c9,f1,e8,b4,a9,af,91,e2,fb,21,73,cf,ce,ad,87,a5,e8,2d,e1,\
  b2,4b,c7,7d,16,0b,0c,63,72,20,43,12,e6,af,94,0a,46,ed,53,98,f4,c5,ff,ff,d5,\
  53,67,1c,f3,7e,94,cb,c4,ad,4d,99,72,f9,d1,d6,31,8f,62,e5,b2,23,e7,95,87,cd,\
  11,f5,95,ad,11,ba,7a,0a,99,19,0d,1c,1a,b8,9c,cd,54,ff,03,fc,02,bb,c7,ae,15,\
  3f
"30"=hex:2e,00,00,00,03,00,00,00,bc,46,47,00,01,00,10,01,1e,00,00,00,c7,bf,10,\
  3e,65,01,a8,c0,00,00,00,00,6f,7d,df,48,ef,2c,fb,48,01,00,01,00,00,00,79,d8,\
  a5,c5,49,05,ca,f9,89,24,db,0c,c7,be,72,9b,62,48,38,2b,a8,ce,03,f4,f5,8a,2b,\
  45,43,bf,40,9c,c1,4b,8a,6f,45,42,38,f8,4f,b1,38,9e,23,d8,65,38,73,73,2b,40,\
  f0,6d,a7,12,59,cc,40,88,f9,05,b5,74,c2,77,9e,fc,cf,94,d4,cc,2b,71,67,d9,6b,\
  41,f2,28,db,11,b9,f8,3e,85,22,d9,41,19,ab,1c,86,17,6a,1e,67,fa,32,51,e3,a5,\
  55,48,b6,02,25,ce,3e,0b,20,4a,cf,9f,dd,a3,8c,4f,b3,c7,43,54,07,9c,8b,51,60,\
  47
"300"=hex:2e,00,00,00,03,00,00,00,bc,46,47,00,01,00,10,01,2c,01,00,00,c7,bf,10,\
  3e,65,01,a8,c0,00,00,00,00,86,7d,df,48,06,2d,fb,48,01,00,19,00,00,00,a9,71,\
  89,69,10,dc,70,b5,20,3c,81,60,4d,82,d5,61,06,5d,3b,cb,75,32,0a,4b,68,b8,47,\
  e1,a7,23,e2,f1,f7,df,ef,95,7f,c4,c4,e8,5d,ea,4f,5a,4f,f4,88,66,91,ce,a9,68,\
  62,25,ae,60,dd,a0,ea,6d,b7,36,79,ec,47,71,e2,9b,82,9f,8e,73,8d,8d,e2,3c,4f,\
  a5,f6,62,d2,1e,0c,58,fd,d1,ac,d7,79,b3,c0,86,85,4b,a7,fc,51,7d,79,54,3d,8c,\
  7f,c5,41,d9,1d,1e,02,b8,14,aa,11,83,fe,2c,eb,44,4b,12,66,0d,a7,d3,49,ae,7a,\
  78
"7"=hex:28,00,00,00,02,00,00,00,bc,46,47,00,01,00,10,01,07,00,00,00,4f,ad,10,\
  3e,66,01,a8,c0,00,00,00,00,65,db,ca,48,e5,8a,e6,48,8e,fd,82,01,76,ee,d0,56,\
  e6,5e,0b,f3,7e,ac,a1,7a,ee,26,90,73,ff,36,4e,75,b3,b3,04,e4,0c,a7,de,ba,04,\
  06,6e,c7,9e,64,8f,fb,19,59,01,ba,76,16,60,b1,03,f2,0c,a2,3d,82,e3,b7,3a,9d,\
  57,3c,d5,8e,ee,84,9c,a6,da,9d,3a,e7,b3,8b,16,eb,4c,82,04,2f,fe,8c,6d,e6,05,\
  f0,94,12,21,85,ff,8e,02,41,bf,1a,7f,3a,62,a4,ab,a4,9a,c8,d1,d8,af,fc,a3,aa,\
  a2,85,75,47,57,82,2a,a1,d7,b2,32,b2,de,94,3b,84,bf,47,c6,92
"70"=hex:2e,00,00,00,03,00,00,00,bc,46,47,00,01,00,10,01,46,00,00,00,c7,bf,10,\
  3e,65,01,a8,c0,00,00,00,00,6f,7d,df,48,ef,2c,fb,48,01,00,01,00,00,00,27,5f,\
  64,91,a9,bf,60,95,31,50,11,46,19,8c,a3,d4,95,aa,cc,05,ed,f9,08,02,8e,8d,c4,\
  93,9b,af,b7,43,d8,2e,90,6c,0c,55,1a,4d,0b,50,c2,2e,2e,c3,9f,d3,cf,c7,e0,19,\
  e2,02,85,91,ae,f2,7a,b7,6b,55,51,ee,fb,32,5e,4a,73,cc,6e,53,b9,27,3c,af,34,\
  61,d2,f2,6f,a5,6d,05,26,cf,3b,8d,4a,5d,1f,41,f3,af,0f,f2,c9,24,22,22,b4,b7,\
  c6,32,85,17,44,45,52,9d,e0,55,ba,10,ca,ad,13,8a,82,52,80,19,2f,d4,84,82,4c,\
  ba

[Software\\Valve\\Steam\\Users\\4671164\\friends] 1222609433
"PersonaName"="phun-ky"
"PersonaStateDesired"=dword:00000001
"VoiceReceiveVolume"=dword:00000066

[Software\\Valve\\Steam\\Users\\4671164\\friends\\1027009] 1215815031
"name"="Hwa Rang"

[Software\\Valve\\Steam\\Users\\4671164\\friends\\1027009\\NameHistory] 1215815031
"0"="Hwa Rang"
"1"=""
"2"=""
"3"=""
"4"=""
"5"=""
"6"=""
"7"=""
"8"=""
"9"=""

[Software\\Valve\\Steam\\Users\\4671164\\friends\\10540039] 1222606246
"avatar"=hex:0a,e3,f3,d9,29,3a,97,c2,90,60,01,5e,01,28,70,06,6a,34,7b,72
"name"="[[KLY]]Hawkeye"

[Software\\Valve\\Steam\\Users\\4671164\\friends\\10540039\\NameHistory] 1222606246
"0"="[[KLY]]Hawkeye"
"1"=""
"2"=""
"3"=""
"4"=""
"5"=""
"6"=""
"7"=""
"8"=""
"9"=""

[Software\\Valve\\Steam\\Users\\4671164\\friends\\143998] 1215814957
"name"="[cc]Filou"

[Software\\Valve\\Steam\\Users\\4671164\\friends\\143998\\NameHistory] 1215814957
"0"="[cc]Filou"
"1"=""
"2"=""
"3"=""
"4"=""
"5"=""
"6"=""
"7"=""
"8"=""
"9"=""

[Software\\Valve\\Steam\\Users\\4671164\\friends\\15034067] 1222606246
"name"="Chan-Tzu Ti"

[Software\\Valve\\Steam\\Users\\4671164\\friends\\15034067\\NameHistory] 1222606246
"0"="Chan-Tzu Ti"
"1"=""
"2"=""
"3"=""
"4"=""
"5"=""
"6"=""
"7"=""
"8"=""
"9"=""

[Software\\Valve\\Steam\\Users\\4671164\\friends\\17042481] 1215814048
"name"="svenne"

[Software\\Valve\\Steam\\Users\\4671164\\friends\\17042481\\NameHistory] 1215814048
"0"="svenne"
"1"=""
"2"=""
"3"=""
"4"=""
"5"=""
"6"=""
"7"=""
"8"=""
"9"=""

[Software\\Valve\\Steam\\Users\\4671164\\friends\\19360029] 1222606246
"avatar"=hex:ea,bc,08,28,12,f1,38,87,c3,73,7f,e3,2e,8e,16,36,51,ae,18,74
"name"="Adrian/ ARSENAL"

[Software\\Valve\\Steam\\Users\\4671164\\friends\\19360029\\NameHistory] 1222606246
"0"="Adrian/ ARSENAL"
"1"=""
"2"=""
"3"=""
"4"=""
"5"=""
"6"=""
"7"=""
"8"=""
"9"=""

[Software\\Valve\\Steam\\Users\\4671164\\friends\\20494485] 1215813968
"name"="mikkel"

[Software\\Valve\\Steam\\Users\\4671164\\friends\\20494485\\NameHistory] 1215813968
"0"="mikkel"
"1"=""
"2"=""
"3"=""
"4"=""
"5"=""
"6"=""
"7"=""
"8"=""
"9"=""

[Software\\Valve\\Steam\\Users\\4671164\\friends\\21940436] 1221254105
"name"="Da Real"

[Software\\Valve\\Steam\\Users\\4671164\\friends\\21940436\\NameHistory] 1221254105
"0"="Da Real"
"1"=""
"2"=""
"3"=""
"4"=""
"5"=""
"6"=""
"7"=""
"8"=""
"9"=""

[Software\\Valve\\Steam\\Users\\4671164\\friends\\22403923] 1215814957
"name"="joel_fahlcrantz"

[Software\\Valve\\Steam\\Users\\4671164\\friends\\22403923\\NameHistory] 1215814957
"0"="joel_fahlcrantz"
"1"=""
"2"=""
"3"=""
"4"=""
"5"=""
"6"=""
"7"=""
"8"=""
"9"=""

[Software\\Valve\\Steam\\Users\\4671164\\friends\\22565384] 1221254105
"name"="Pikku Tappi"

[Software\\Valve\\Steam\\Users\\4671164\\friends\\22565384\\NameHistory] 1221254105
"0"="Pikku Tappi"
"1"=""
"2"=""
"3"=""
"4"=""
"5"=""
"6"=""
"7"=""
"8"=""
"9"=""

[Software\\Valve\\Steam\\Users\\4671164\\friends\\23029497] 1215814957
"avatar"=hex:83,45,f3,4c,1a,a1,d5,c6,e7,d2,81,0a,dd,93,13,80,ab,61,8a,00
"name"="Brascal"

[Software\\Valve\\Steam\\Users\\4671164\\friends\\23029497\\NameHistory] 1215814957
"0"="Brascal"
"1"=""
"2"=""
"3"=""
"4"=""
"5"=""
"6"=""
"7"=""
"8"=""
"9"=""

[Software\\Valve\\Steam\\Users\\4671164\\friends\\23267498] 1221254105
"avatar"=hex:68,1a,a6,da,ae,fb,e5,b7,54,20,fb,ff,16,3b,0a,a1,6f,50,65,15
"name"="Ari\xc3\xabr.Vlaanderen"

[Software\\Valve\\Steam\\Users\\4671164\\friends\\23267498\\NameHistory] 1221254105
"0"="Ari\xc3\xabr.Vlaanderen"
"1"=""
"2"=""
"3"=""
"4"=""
"5"=""
"6"=""
"7"=""
"8"=""
"9"=""

[Software\\Valve\\Steam\\Users\\4671164\\friends\\24055619] 1221254105
"name"="Lamorotrouss"

[Software\\Valve\\Steam\\Users\\4671164\\friends\\24055619\\NameHistory] 1221254105
"0"="Lamorotrouss"
"1"=""
"2"=""
"3"=""
"4"=""
"5"=""
"6"=""
"7"=""
"8"=""
"9"=""

[Software\\Valve\\Steam\\Users\\4671164\\friends\\25191731] 1221254105
"avatar"=hex:95,82,a6,89,68,9d,eb,fb,aa,58,4f,e3,16,53,39,31,e3,0f,47,d0
"name"="steiner"

[Software\\Valve\\Steam\\Users\\4671164\\friends\\25191731\\NameHistory] 1221254105
"0"="steiner"
"1"=""
"2"=""
"3"=""
"4"=""
"5"=""
"6"=""
"7"=""
"8"=""
"9"=""

[Software\\Valve\\Steam\\Users\\4671164\\friends\\25486798] 1222606246
"name"="\xd1\x192\xd0\xb3\xd1\x20ac\xd1\x17d\xd0\xbc\xd1\x2039\xd0\xb9 =DIS-BAT="

[Software\\Valve\\Steam\\Users\\4671164\\friends\\25486798\\NameHistory] 1222606246
"0"="\xd1\x192\xd0\xb3\xd1\x20ac\xd1\x17d\xd0\xbc\xd1\x2039\xd0\xb9 =DIS-BAT="
"1"=""
"2"=""
"3"=""
"4"=""
"5"=""
"6"=""
"7"=""
"8"=""
"9"=""

[Software\\Valve\\Steam\\Users\\4671164\\friends\\2603893] 1222606166
"avatar"=hex:b5,28,03,f8,18,67,73,a1,a3,d4,df,2c,98,d1,87,47,5a,70,4e,3a
"name"="Dr. X"

[Software\\Valve\\Steam\\Users\\4671164\\friends\\2603893\\NameHistory] 1222606166
"0"="Dr. X"
"1"=""
"2"=""
"3"=""
"4"=""
"5"=""
"6"=""
"7"=""
"8"=""
"9"=""

[Software\\Valve\\Steam\\Users\\4671164\\friends\\26364925] 1215814957
"name"="Samppa"

[Software\\Valve\\Steam\\Users\\4671164\\friends\\26364925\\NameHistory] 1215814957
"0"="Samppa"
"1"=""
"2"=""
"3"=""
"4"=""
"5"=""
"6"=""
"7"=""
"8"=""
"9"=""

[Software\\Valve\\Steam\\Users\\4671164\\friends\\26597930] 1222606246
"avatar"=hex:4b,86,f4,ad,12,70,a5,29,4a,e0,a7,2a,d3,2d,99,53,54,b7,b1,cb
"name"="Soulhunter"

[Software\\Valve\\Steam\\Users\\4671164\\friends\\26597930\\NameHistory] 1222606246
"0"="Soulhunter"
"1"=""
"2"=""
"3"=""
"4"=""
"5"=""
"6"=""
"7"=""
"8"=""
"9"=""

[Software\\Valve\\Steam\\Users\\4671164\\friends\\27054287] 1222606571
"name"="[Rocky]"

[Software\\Valve\\Steam\\Users\\4671164\\friends\\27054287\\NameHistory] 1222606571
"0"="[Rocky]"
"1"=""
"2"=""
"3"=""
"4"=""
"5"=""
"6"=""
"7"=""
"8"=""
"9"=""

[Software\\Valve\\Steam\\Users\\4671164\\friends\\28294230] 1215813742
"name"="Exilees :)"

[Software\\Valve\\Steam\\Users\\4671164\\friends\\28294230\\NameHistory] 1215813742
"0"="Exilees :)"
"1"=""
"2"=""
"3"=""
"4"=""
"5"=""
"6"=""
"7"=""
"8"=""
"9"=""

[Software\\Valve\\Steam\\Users\\4671164\\friends\\28584281] 1215813742
"name"="Darth Pingu"

[Software\\Valve\\Steam\\Users\\4671164\\friends\\28584281\\NameHistory] 1215813742
"0"="Darth Pingu"
"1"=""
"2"=""
"3"=""
"4"=""
"5"=""
"6"=""
"7"=""
"8"=""
"9"=""

[Software\\Valve\\Steam\\Users\\4671164\\friends\\28977937] 1222606246
"avatar"=hex:10,7a,09,21,c1,4d,cc,8d,01,10,48,77,da,f6,ea,03,e4,e8,cc,b5
"name"="headbouv"

[Software\\Valve\\Steam\\Users\\4671164\\friends\\28977937\\NameHistory] 1222606246
"0"="headbouv"
"1"=""
"2"=""
"3"=""
"4"=""
"5"=""
"6"=""
"7"=""
"8"=""
"9"=""

[Software\\Valve\\Steam\\Users\\4671164\\friends\\29933846] 1221254105
"avatar"=hex:31,0f,5b,06,3f,42,12,51,ca,af,d2,b8,3c,2e,72,e0,fa,41,84,48
"name"="i s i \xc2\xb4\xc2\xb4 Bychulo"

[Software\\Valve\\Steam\\Users\\4671164\\friends\\29933846\\NameHistory] 1221254105
"0"="i s i \xc2\xb4\xc2\xb4 Bychulo"
"1"=""
"2"=""
"3"=""
"4"=""
"5"=""
"6"=""
"7"=""
"8"=""
"9"=""

[Software\\Valve\\Steam\\Users\\4671164\\friends\\30383899] 1221254105
"avatar"=hex:3b,50,f4,a9,c7,7d,c0,3c,c6,a8,ca,6d,44,e3,76,2c,73,6b,43,ea
"name"="[SOS]Lao,DK"

[Software\\Valve\\Steam\\Users\\4671164\\friends\\30383899\\NameHistory] 1221254105
"0"="[SOS]Lao,DK"
"1"=""
"2"=""
"3"=""
"4"=""
"5"=""
"6"=""
"7"=""
"8"=""
"9"=""

[Software\\Valve\\Steam\\Users\\4671164\\friends\\30693867] 1215814703
"name"="Spe"

[Software\\Valve\\Steam\\Users\\4671164\\friends\\30693867\\NameHistory] 1215814703
"0"="Spe"
"1"=""
"2"=""
"3"=""
"4"=""
"5"=""
"6"=""
"7"=""
"8"=""
"9"=""

[Software\\Valve\\Steam\\Users\\4671164\\friends\\31222070] 1222606246
"name"="Sch\xc3\x00a4ffner"

[Software\\Valve\\Steam\\Users\\4671164\\friends\\31222070\\NameHistory] 1222606246
"0"="Sch\xc3\x00a4ffner"
"1"=""
"2"=""
"3"=""
"4"=""
"5"=""
"6"=""
"7"=""
"8"=""
"9"=""

[Software\\Valve\\Steam\\Users\\4671164\\friends\\31551288] 1222606246
"avatar"=hex:21,b7,00,12,98,cf,4b,ff,87,18,a2,c3,41,ca,6d,8e,e1,36,83,9c
"name"="pinguin7"

[Software\\Valve\\Steam\\Users\\4671164\\friends\\31551288\\NameHistory] 1222606246
"0"="pinguin7"
"1"=""
"2"=""
"3"=""
"4"=""
"5"=""
"6"=""
"7"=""
"8"=""
"9"=""

[Software\\Valve\\Steam\\Users\\4671164\\friends\\31945482] 1221254105
"avatar"=hex:7f,d3,f7,89,d2,b9,ec,53,81,c9,6b,03,d7,0a,c9,8e,b0,e2,a0,cd
"name"="Golgoth73"

[Software\\Valve\\Steam\\Users\\4671164\\friends\\31945482\\NameHistory] 1221254105
"0"="Golgoth73"
"1"=""
"2"=""
"3"=""
"4"=""
"5"=""
"6"=""
"7"=""
"8"=""
"9"=""

[Software\\Valve\\Steam\\Users\\4671164\\friends\\31973863] 1221254105
"name"="Stupern"

[Software\\Valve\\Steam\\Users\\4671164\\friends\\31973863\\NameHistory] 1221254105
"0"="Stupern"
"1"=""
"2"=""
"3"=""
"4"=""
"5"=""
"6"=""
"7"=""
"8"=""
"9"=""

[Software\\Valve\\Steam\\Users\\4671164\\friends\\32302861] 1222606246
"avatar"=hex:01,67,86,b7,bd,2e,6b,d0,a8,a7,7a,b1,90,cc,59,fd,2d,7f,20,52
"name"="__ S I L V O __"

[Software\\Valve\\Steam\\Users\\4671164\\friends\\32302861\\NameHistory] 1222606246
"0"="__ S I L V O __"
"1"=""
"2"=""
"3"=""
"4"=""
"5"=""
"6"=""
"7"=""
"8"=""
"9"=""

[Software\\Valve\\Steam\\Users\\4671164\\friends\\33178396] 1221254105
"avatar"=hex:dc,33,c6,81,2a,4e,63,7a,6f,7b,f2,01,97,ee,3d,88,c0,97,45,30
"name"="[L.C] \xc2\xa4 Laca"

[Software\\Valve\\Steam\\Users\\4671164\\friends\\33178396\\NameHistory] 1221254105
"0"="[L.C] \xc2\xa4 Laca"
"1"=""
"2"=""
"3"=""
"4"=""
"5"=""
"6"=""
"7"=""
"8"=""
"9"=""

[Software\\Valve\\Steam\\Users\\4671164\\friends\\33557957] 1215814360
"avatar"=hex:ba,e9,1d,f8,8f,f7,a7,4c,ab,c2,26,52,12,15,13,49,8a,90,44,86
"name"="lieen"

[Software\\Valve\\Steam\\Users\\4671164\\friends\\33557957\\NameHistory] 1215814360
"0"="lieen"
"1"=""
"2"=""
"3"=""
"4"=""
"5"=""
"6"=""
"7"=""
"8"=""
"9"=""

[Software\\Valve\\Steam\\Users\\4671164\\friends\\34034834] 1222606427
"name"="Kanonenfutter (GER)"

[Software\\Valve\\Steam\\Users\\4671164\\friends\\34034834\\NameHistory] 1222606427
"0"="Kanonenfutter (GER)"
"1"=""
"2"=""
"3"=""
"4"=""
"5"=""
"6"=""
"7"=""
"8"=""
"9"=""

[Software\\Valve\\Steam\\Users\\4671164\\friends\\34044371] 1222606246
"avatar"=hex:da,5a,a8,5b,7c,5a,a0,99,21,39,5a,d3,44,82,85,23,87,6b,f6,7a
"name"="Comander fox"

[Software\\Valve\\Steam\\Users\\4671164\\friends\\34044371\\NameHistory] 1222606246
"0"="Comander fox"
"1"=""
"2"=""
"3"=""
"4"=""
"5"=""
"6"=""
"7"=""
"8"=""
"9"=""

[Software\\Valve\\Steam\\Users\\4671164\\friends\\34130332] 1221254105
"avatar"=hex:8f,91,f5,1d,b3,fe,fc,6e,2d,f7,8d,6c,d6,40,04,ad,c7,cf,4d,65
"name"="RIPNIK"

[Software\\Valve\\Steam\\Users\\4671164\\friends\\34130332\\NameHistory] 1221254105
"0"="RIPNIK"
"1"=""
"2"=""
"3"=""
"4"=""
"5"=""
"6"=""
"7"=""
"8"=""
"9"=""

[Software\\Valve\\Steam\\Users\\4671164\\friends\\34737410] 1222606246
"avatar"=hex:f2,44,c7,96,21,10,9f,4f,17,5a,2d,1d,bd,80,b1,b9,d9,ca,ff,fb
"name"="{GXS} M\xd0\x201drius *\xe2\x201e\xa2*"

[Software\\Valve\\Steam\\Users\\4671164\\friends\\34737410\\NameHistory] 1222606246
"0"="{GXS} M\xd0\x201drius *\xe2\x201e\xa2*"
"1"=""
"2"=""
"3"=""
"4"=""
"5"=""
"6"=""
"7"=""
"8"=""
"9"=""

[Software\\Valve\\Steam\\Users\\4671164\\friends\\35148881] 1215814957
"name"="ka_bol"

[Software\\Valve\\Steam\\Users\\4671164\\friends\\35148881\\NameHistory] 1215814957
"0"="ka_bol"
"1"=""
"2"=""
"3"=""
"4"=""
"5"=""
"6"=""

"7"=""
"8"=""
"9"=""

[Software\\Valve\\Steam\\Users\\4671164\\friends\\35499841] 1221254105
"name"=".::*\xc4\x17e\xcf\x17d\xd0\xaf*::. Owen"

[Software\\Valve\\Steam\\Users\\4671164\\friends\\35499841\\NameHistory] 1221254105
"0"=".::*\xc4\x17e\xcf\x17d\xd0\xaf*::. Owen"
"1"=""
"2"=""
"3"=""
"4"=""
"5"=""
"6"=""
"7"=""
"8"=""
"9"=""

[Software\\Valve\\Steam\\Users\\4671164\\friends\\35707127] 1215813742
"avatar"=hex:3c,c3,e0,07,5f,43,ca,c0,84,84,30,17,0b,32,d7,72,fb,33,e6,5b
"name"="B-BoyX"

[Software\\Valve\\Steam\\Users\\4671164\\friends\\35707127\\NameHistory] 1215813742
"0"="B-BoyX"
"1"=""
"2"=""
"3"=""
"4"=""
"5"=""
"6"=""
"7"=""
"8"=""
"9"=""

[Software\\Valve\\Steam\\Users\\4671164\\friends\\35886829] 1222606246
"avatar"=hex:8b,7b,61,56,36,07,db,d4,a3,12,5e,66,63,65,45,0b,a6,6c,62,3f
"name"="Officer DoD"

[Software\\Valve\\Steam\\Users\\4671164\\friends\\35886829\\NameHistory] 1222606246
"0"="Officer DoD"
"1"=""
"2"=""
"3"=""
"4"=""
"5"=""
"6"=""
"7"=""
"8"=""
"9"=""

[Software\\Valve\\Steam\\Users\\4671164\\friends\\36099304] 1215813742
"name"="- Oscar //"

[Software\\Valve\\Steam\\Users\\4671164\\friends\\36099304\\NameHistory] 1215813742
"0"="- Oscar //"
"1"=""
"2"=""
"3"=""
"4"=""
"5"=""
"6"=""
"7"=""
"8"=""
"9"=""

[Software\\Valve\\Steam\\Users\\4671164\\friends\\36351647] 1222606246
"avatar"=hex:e0,13,87,0c,27,af,66,26,da,8c,c1,77,10,c8,c5,70,27,ec,ed,05
"name"="Fuchsrednax"

[Software\\Valve\\Steam\\Users\\4671164\\friends\\36351647\\NameHistory] 1222606246
"0"="Fuchsrednax"
"1"=""
"2"=""
"3"=""
"4"=""
"5"=""
"6"=""
"7"=""
"8"=""
"9"=""

[Software\\Valve\\Steam\\Users\\4671164\\friends\\36358054] 1215813742
"name"="BoB LeiNaN"

[Software\\Valve\\Steam\\Users\\4671164\\friends\\36358054\\NameHistory] 1215813742
"0"="BoB LeiNaN"
"1"=""
"2"=""
"3"=""
"4"=""
"5"=""
"6"=""
"7"=""
"8"=""
"9"=""

[Software\\Valve\\Steam\\Users\\4671164\\friends\\36439744] 1221254105
"name"="Major K\xc3\xb6nig"

[Software\\Valve\\Steam\\Users\\4671164\\friends\\36439744\\NameHistory] 1221254105
"0"="Major K\xc3\xb6nig"
"1"=""
"2"=""
"3"=""
"4"=""
"5"=""
"6"=""
"7"=""
"8"=""
"9"=""

[Software\\Valve\\Steam\\Users\\4671164\\friends\\36611447] 1222606246
"name"="sadok"

[Software\\Valve\\Steam\\Users\\4671164\\friends\\36611447\\NameHistory] 1222606246
"0"="sadok"
"1"=""
"2"=""
"3"=""
"4"=""
"5"=""
"6"=""
"7"=""
"8"=""
"9"=""

[Software\\Valve\\Steam\\Users\\4671164\\friends\\37011573] 1222606246
"name"="www.top20free.de"

[Software\\Valve\\Steam\\Users\\4671164\\friends\\37011573\\NameHistory] 1222606246
"0"="www.top20free.de"
"1"=""
"2"=""
"3"=""
"4"=""
"5"=""
"6"=""
"7"=""
"8"=""
"9"=""

[Software\\Valve\\Steam\\Users\\4671164\\friends\\37603681] 1222606246
"avatar"=hex:94,86,2e,37,5f,bf,f5,09,d1,3a,5d,6f,5c,d0,78,0f,84,6f,51,90
"name"="Kein normaler Mensch"

[Software\\Valve\\Steam\\Users\\4671164\\friends\\37603681\\NameHistory] 1222606246
"0"="Kein normaler Mensch"
"1"=""
"2"=""
"3"=""
"4"=""
"5"=""
"6"=""
"7"=""
"8"=""
"9"=""

[Software\\Valve\\Steam\\Users\\4671164\\friends\\37666078] 1215814957
"avatar"=hex:a6,9f,d4,10,c0,14,b6,ad,ad,a5,66,2c,32,63,fa,a2,25,f8,83,30
"name"="| KaptenRoyal |"

[Software\\Valve\\Steam\\Users\\4671164\\friends\\37666078\\NameHistory] 1215814957
"0"="| KaptenRoyal |"
"1"=""
"2"=""
"3"=""
"4"=""
"5"=""
"6"=""
"7"=""
"8"=""
"9"=""

[Software\\Valve\\Steam\\Users\\4671164\\friends\\38086475] 1215813985
"name"="tr\xc3\xb6\xc3\xb6\xc3\xb6gast"

[Software\\Valve\\Steam\\Users\\4671164\\friends\\38086475\\NameHistory] 1215813985
"0"="tr\xc3\xb6\xc3\xb6\xc3\xb6gast"
"1"=""
"2"=""
"3"=""
"4"=""
"5"=""
"6"=""
"7"=""
"8"=""
"9"=""

[Software\\Valve\\Steam\\Users\\4671164\\friends\\38095085] 1221254105
"avatar"=hex:98,f3,26,54,a4,69,2f,8d,ab,7d,fd,71,97,8e,4e,d0,7a,8f,a7,86
"name"="[L.C] \xc2\xa4 Dong\xc3\xb3-//Sniper//:)"

[Software\\Valve\\Steam\\Users\\4671164\\friends\\38095085\\NameHistory] 1221254105
"0"="[L.C] \xc2\xa4 Dong\xc3\xb3-//Sniper//:)"
"1"=""
"2"=""
"3"=""
"4"=""
"5"=""
"6"=""
"7"=""
"8"=""
"9"=""

[Software\\Valve\\Steam\\Users\\4671164\\friends\\38706864] 1221254105
"avatar"=hex:b1,cf,0b,5b,1b,62,82,bb,f8,8b,b7,bd,50,82,85,10,12,53,24,e6
"name"="Cpt. Miller 2.Ranger Batallion"

[Software\\Valve\\Steam\\Users\\4671164\\friends\\38706864\\NameHistory] 1221254105
"0"="Cpt. Miller 2.Ranger Batallion"
"1"=""
"2"=""
"3"=""
"4"=""
"5"=""
"6"=""
"7"=""
"8"=""
"9"=""

[Software\\Valve\\Steam\\Users\\4671164\\friends\\38726065] 1215814591
"name"="danizz_hopp93"

[Software\\Valve\\Steam\\Users\\4671164\\friends\\38726065\\NameHistory] 1215814591
"0"="danizz_hopp93"
"1"=""
"2"=""
"3"=""
"4"=""
"5"=""
"6"=""
"7"=""
"8"=""
"9"=""

[Software\\Valve\\Steam\\Users\\4671164\\friends\\38767949] 1222606246
"name"="saccasi1"

[Software\\Valve\\Steam\\Users\\4671164\\friends\\38767949\\NameHistory] 1222606246
"0"="saccasi1"
"1"=""
"2"=""
"3"=""
"4"=""
"5"=""
"6"=""
"7"=""
"8"=""
"9"=""

[Software\\Valve\\Steam\\Users\\4671164\\friends\\38941649] 1222606246
"name"="xavierg4"

[Software\\Valve\\Steam\\Users\\4671164\\friends\\38941649\\NameHistory] 1222606246
"0"="xavierg4"
"1"=""
"2"=""
"3"=""
"4"=""
"5"=""
"6"=""
"7"=""
"8"=""
"9"=""

[Software\\Valve\\Steam\\Users\\4671164\\friends\\39071370] 1215814957
"name"="sebbe"

[Software\\Valve\\Steam\\Users\\4671164\\friends\\39071370\\NameHistory] 1215814957
"0"="sebbe"
"1"=""
"2"=""
"3"=""
"4"=""
"5"=""
"6"=""
"7"=""
"8"=""
"9"=""

[Software\\Valve\\Steam\\Users\\4671164\\friends\\39417825] 1221254105
"avatar"=hex:94,62,49,ef,26,ed,51,06,d7,b6,1d,da,85,cb,6e,ff,3f,e5,e6,3a
"name"="macman"

[Software\\Valve\\Steam\\Users\\4671164\\friends\\39417825\\NameHistory] 1221254105
"0"="macman"
"1"=""
"2"=""
"3"=""
"4"=""
"5"=""
"6"=""
"7"=""
"8"=""
"9"=""

[Software\\Valve\\Steam\\Users\\4671164\\friends\\39455440] 1222606246
"name"="mistik1993"

[Software\\Valve\\Steam\\Users\\4671164\\friends\\39455440\\NameHistory] 1222606246
"0"="mistik1993"
"1"=""
"2"=""
"3"=""
"4"=""
"5"=""
"6"=""
"7"=""
"8"=""
"9"=""

[Software\\Valve\\Steam\\Users\\4671164\\friends\\40157421] 1221254179
"name"="neonrodney"

[Software\\Valve\\Steam\\Users\\4671164\\friends\\40157421\\NameHistory] 1221254179
"0"="neonrodney"
"1"=""
"2"=""
"3"=""
"4"=""
"5"=""
"6"=""
"7"=""
"8"=""
"9"=""

[Software\\Valve\\Steam\\Users\\4671164\\friends\\40668833] 1222606246
"avatar"=hex:cb,57,67,c3,13,89,07,c2,c9,05,87,d8,36,67,fc,2c,73,68,95,3c
"name"=".:Superiours:. Killerguy"

[Software\\Valve\\Steam\\Users\\4671164\\friends\\40668833\\NameHistory] 1222606246
"0"=".:Superiours:. Killerguy"
"1"=""
"2"=""
"3"=""
"4"=""
"5"=""
"6"=""
"7"=""
"8"=""
"9"=""

[Software\\Valve\\Steam\\Users\\4671164\\friends\\40707339] 1221254105
"name"="jdanovcompany"

[Software\\Valve\\Steam\\Users\\4671164\\friends\\40707339\\NameHistory] 1221254105
"0"="jdanovcompany"
"1"=""
"2"=""
"3"=""
"4"=""
"5"=""
"6"=""
"7"=""
"8"=""
"9"=""

[Software\\Valve\\Steam\\Users\\4671164\\friends\\40986924] 1222606246
"avatar"=hex:5e,25,65,80,9f,bb,eb,77,c0,06,63,ed,45,fc,75,9f,86,58,e8,b0
"name"="pyro42"

[Software\\Valve\\Steam\\Users\\4671164\\friends\\40986924\\NameHistory] 1222606246
"0"="pyro42"
"1"=""
"2"=""
"3"=""
"4"=""
"5"=""
"6"=""
"7"=""
"8"=""
"9"=""

[Software\\Valve\\Steam\\Users\\4671164\\friends\\41167403] 1222606272
"name"="Hunnenkonig"

[Software\\Valve\\Steam\\Users\\4671164\\friends\\41167403\\NameHistory] 1222606272
"0"="Hunnenkonig"
"1"=""
"2"=""
"3"=""
"4"=""
"5"=""
"6"=""
"7"=""
"8"=""
"9"=""

[Software\\Valve\\Steam\\Users\\4671164\\friends\\41245440] 1222606246
"name"="\xd0\x90\xd0\xbd\xd0\xb0\xd1\x20ac\xd1\x2026\xd0\xb8\xd1\x81\xd1\x201a"

[Software\\Valve\\Steam\\Users\\4671164\\friends\\41245440\\NameHistory] 1222606246
"0"="\xd0\x90\xd0\xbd\xd0\xb0\xd1\x20ac\xd1\x2026\xd0\xb8\xd1\x81\xd1\x201a"
"1"=""
"2"=""
"3"=""
"4"=""
"5"=""
"6"=""
"7"=""
"8"=""
"9"=""

[Software\\Valve\\Steam\\Users\\4671164\\friends\\4671164] 1215639347
"name"="phun-ky"

[Software\\Valve\\Steam\\Users\\4671164\\friends\\4671164\\NameHistory] 1215639347
"0"="phun-ky"
"1"=""
"2"=""
"3"=""
"4"=""
"5"=""
"6"=""
"7"=""
"8"=""
"9"=""

[Software\\Valve\\Steam\\Users\\4671164\\friends\\5377875] 1215813742
"name"="Sammy J"

[Software\\Valve\\Steam\\Users\\4671164\\friends\\5377875\\NameHistory] 1215813742
"0"="Sammy J"
"1"=""
"2"=""
"3"=""
"4"=""
"5"=""
"6"=""
"7"=""
"8"=""
"9"=""

[Software\\Valve\\Steam\\Users\\4671164\\friends\\7037515] 1215813742
"avatar"=hex:c1,30,72,41,c2,0b,fa,3f,50,ad,ac,0e,4f,5f,a9,a7,20,8c,2b,d1
"name"="Simon"

[Software\\Valve\\Steam\\Users\\4671164\\friends\\7037515\\NameHistory] 1215813742
"0"="Simon"
"1"=""
"2"=""
"3"=""
"4"=""
"5"=""
"6"=""
"7"=""
"8"=""
"9"=""

[Software\\Valve\\Steam\\Users\\4671164\\friends\\7429350] 1215814957
"name"="nallarf"

[Software\\Valve\\Steam\\Users\\4671164\\friends\\7429350\\NameHistory] 1215814957
"0"="nallarf"
"1"=""
"2"=""
"3"=""
"4"=""
"5"=""
"6"=""
"7"=""
"8"=""
"9"=""

[Software\\Valve\\Steam\\Users\\4671164\\friends\\7477227] 1215814957
"name"="Spike164"

[Software\\Valve\\Steam\\Users\\4671164\\friends\\7477227\\NameHistory] 1215814957
"0"="Spike164"
"1"=""
"2"=""
"3"=""
"4"=""
"5"=""
"6"=""
"7"=""
"8"=""
"9"=""

[Software\\Valve\\Steam\\Users\\4671164\\friends\\8310950] 1222606246
"name"="Gonzo"

[Software\\Valve\\Steam\\Users\\4671164\\friends\\8310950\\NameHistory] 1222606246
"0"="Gonzo"
"1"=""
"2"=""
"3"=""
"4"=""
"5"=""
"6"=""
"7"=""
"8"=""
"9"=""

[Software\\Valve\\Steam\\Users\\4671164\\friends\\8398135] 1215639329
"name"="DioXiD"

[Software\\Valve\\Steam\\Users\\4671164\\friends\\8398135\\NameHistory] 1215639329
"0"="DioXiD"
"1"=""
"2"=""
"3"=""
"4"=""
"5"=""
"6"=""
"7"=""
"8"=""
"9"=""

[Software\\Valve\\Steam\\Users\\4671164\\friends\\9706121] 1215814066
"name"="ntzsteelpad"

[Software\\Valve\\Steam\\Users\\4671164\\friends\\9706121\\NameHistory] 1215814066
"0"="ntzsteelpad"
"1"=""
"2"=""
"3"=""
"4"=""
"5"=""
"6"=""
"7"=""
"8"=""
"9"=""

[Software\\Valve\\Steam\\Users\\4671164\\news\\10] 1215813603
"UpdateNewsVersion"=dword:00000000

[Software\\Valve\\Steam\\Users\\4671164\\news\\Messages] 1222606682
"colonization_playnow_na"=dword:00000001
"ej_corner_161"=dword:00000001
"gamecock_released"=dword:00000001
"htf_released"=dword:00000001
"multiwinia_preorder"=dword:00000001
"planetbusters_released"=dword:00000001
"rockstar_weekenddeal_eu"=dword:00000001
"silverfall_ea_released"=dword:00000001
"spellforce2_released"=dword:00000001
"twdotw_released"=dword:00000001

[Software\\Wine\\Debug] 1215629009
"RelayExclude"="ntdll.RtlEnterCriticalSection;ntdll.RtlLeaveCriticalSection;kernel32.94;kernel32.95;kernel32.96;kernel32.97;kernel32.98"
"RelayFromExclude"="winex11.drv;user32;gdi32;advapi32;kernel32"

[Software\\Wine\\Drivers] 1224326836
"Audio"="oss"

[Software\\Wine\\Fonts] 1224326786
"Codepages"="1252,850"

[Software\\Wine\\Fonts\\External Fonts] 1224326786
"AlArabiya (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_AlArabiya.ttf"
"AlBattar (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_AlBattar.ttf"
"AlHor (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_AlHor.ttf"
"AlManzomah (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_AlManzomah.ttf"
"AlMateen Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_AlMateen-Bold.ttf"
"AlMohanad (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_AlMohanad.ttf"
"AlMothnna Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_AlMothnna-Bold.ttf"
"AlYarmook (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_AlYarmook.ttf"
"Andale Mono (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\msttcorefonts\\andalemo.ttf"
"AnjaliOldLipi (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-malayalam-fonts\\AnjaliOldLipi-0.730.ttf"
"AR PL UMing CN (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\arphic\\uming.ttc"
"AR PL UMing HK (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\arphic\\uming.ttc"
"AR PL UMing TW (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\arphic\\uming.ttc"
"AR PL UMing TW MBE (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\arphic\\uming.ttc"
"Arab (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_Arab.ttf"
"Arial (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\msttcorefonts\\Arial.ttf"
"Arial Black (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\msttcorefonts\\Arial_Black.ttf"
"Arial Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\msttcorefonts\\Arial_Bold.ttf"
"Arial Bold Italic (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\msttcorefonts\\arialbi.ttf"
"Arial Italic (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\msttcorefonts\\ariali.ttf"
"Bitstream Vera Sans (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-bitstream-vera\\Vera.ttf"
"Bitstream Vera Sans Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-bitstream-vera\\VeraBd.ttf"
"Bitstream Vera Sans Bold Oblique (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-bitstream-vera\\VeraBI.ttf"
"Bitstream Vera Sans Mono (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-bitstream-vera\\VeraMono.ttf"
"Bitstream Vera Sans Mono Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-bitstream-vera\\VeraMoBd.ttf"
"Bitstream Vera Sans Mono Bold Oblique (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-bitstream-vera\\VeraMoBI.ttf"
"Bitstream Vera Sans Mono Oblique (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-bitstream-vera\\VeraMoIt.ttf"
"Bitstream Vera Sans Oblique (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-bitstream-vera\\VeraIt.ttf"
"Bitstream Vera Serif (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-bitstream-vera\\VeraSe.ttf"
"Bitstream Vera Serif Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-bitstream-vera\\VeraSeBd.ttf"
"Comic Sans MS (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\msttcorefonts\\Comic_Sans_MS.ttf"
"Comic Sans MS Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\msttcorefonts\\comicbd.ttf"
"Cortoba (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_Cortoba.ttf"
"Courier New (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\msttcorefonts\\Courier_New.ttf"
"Courier New Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\msttcorefonts\\courbd.ttf"
"Courier New Bold Italic (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\msttcorefonts\\Courier_New_Bold_Italic.ttf"
"Courier New Italic (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\msttcorefonts\\Courier_New_Italic.ttf"
"DejaVu Sans (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-dejavu\\DejaVuSans.ttf"
"DejaVu Sans Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-dejavu\\DejaVuSans-Bold.ttf"
"DejaVu Sans Bold Oblique (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-dejavu\\DejaVuSans-BoldOblique.ttf"
"DejaVu Sans Condensed Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-dejavu\\DejaVuSansCondensed-Bold.ttf"
"DejaVu Sans Condensed Bold Oblique (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-dejavu\\DejaVuSansCondensed-BoldOblique.ttf"
"DejaVu Sans Condensed Oblique (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-dejavu\\DejaVuSansCondensed-Oblique.ttf"
"DejaVu Sans Mono (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-dejavu\\DejaVuSansMono.ttf"
"DejaVu Sans Mono Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-dejavu\\DejaVuSansMono-Bold.ttf"
"DejaVu Sans Mono Bold Oblique (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-dejavu\\DejaVuSansMono-BoldOblique.ttf"
"DejaVu Sans Mono Oblique (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-dejavu\\DejaVuSansMono-Oblique.ttf"
"DejaVu Sans Oblique (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-dejavu\\DejaVuSans-Oblique.ttf"
"DejaVu Serif (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-dejavu\\DejaVuSerif.ttf"
"DejaVu Serif Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-dejavu\\DejaVuSerif-Bold.ttf"
"DejaVu Serif Bold Italic (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-dejavu\\DejaVuSerif-BoldItalic.ttf"
"DejaVu Serif Condensed Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-dejavu\\DejaVuSerifCondensed-Bold.ttf"
"DejaVu Serif Condensed Bold Italic (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-dejavu\\DejaVuSerifCondensed-BoldItalic.ttf"
"DejaVu Serif Italic (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-dejavu\\DejaVuSerif-Italic.ttf"
"Dimnah (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_Dimnah.ttf"
"Electron (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_Electron.ttf"
"FreeMono (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\freefont\\FreeMono.ttf"
"FreeMono Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\freefont\\FreeMonoBold.ttf"
"FreeMono BoldOblique (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\freefont\\FreeMonoBoldOblique.ttf"
"FreeMono Oblique (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\freefont\\FreeMonoOblique.ttf"
"FreeSans (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\freefont\\FreeSans.ttf"
"FreeSans Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\freefont\\FreeSansBold.ttf"
"FreeSans BoldOblique (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\freefont\\FreeSansBoldOblique.ttf"
"FreeSans Oblique (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\freefont\\FreeSansOblique.ttf"
"FreeSerif (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\freefont\\FreeSerif.ttf"
"FreeSerif Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\freefont\\FreeSerifBold.ttf"
"FreeSerif BoldItalic (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\freefont\\FreeSerifBoldItalic.ttf"
"FreeSerif Italic (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\freefont\\FreeSerifItalic.ttf"
"Furat (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_Furat.ttf"
"Garuda (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\Garuda.ttf"
"Garuda Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\Garuda-Bold.ttf"
"Garuda BoldOblique (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\Garuda-BoldOblique.ttf"
"Garuda Oblique (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\Garuda-Oblique.ttf"
"Georgia (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\msttcorefonts\\Georgia.ttf"
"Georgia Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\msttcorefonts\\Georgia_Bold.ttf"
"Georgia Bold Italic (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\msttcorefonts\\georgiaz.ttf"
"Georgia Italic (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\msttcorefonts\\Georgia_Italic.ttf"
"Granada (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_Granada.ttf"
"Graph (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_Graph.ttf"
"Hani (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_Hani.ttf"
"Haramain (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_Haramain.ttf"
"Hor (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_Hor.ttf"
"Impact (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\msttcorefonts\\Impact.ttf"
"Japan (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_Japan.ttf"
"Jet (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_Jet.ttf"
"Kayrawan (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_Kayrawan.ttf"
"Khalid (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_Khalid.ttf"
"Kochi Gothic (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\kochi\\kochi-gothic-subst.ttf"
"Kochi Mincho (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\kochi\\kochi-mincho-subst.ttf"
"Lohit Gujarati (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-indic-fonts-core\\lohit_gu.ttf"
"Lohit Hindi (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-indic-fonts-core\\lohit_hi.ttf"
"Lohit Punjabi (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-indic-fonts-core\\lohit_pa.ttf"
"Lohit Tamil (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-indic-fonts-core\\lohit_ta.ttf"
"Loma (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\Loma.ttf"
"Loma Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\Loma-Bold.ttf"
"Loma BoldOblique (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\Loma-BoldOblique.ttf"
"Loma Oblique (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\Loma-Oblique.ttf"
"Mallige (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-indic-fonts-core\\Malige-n.ttf"
"Mallige Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-indic-fonts-core\\Malige-b.ttf"
"MalOtf (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-indic-fonts-core\\MalOtf.ttf"
"Marlett (TrueType)"="Z:\\usr\\bin\\..\\lib\\..\\share\\wine\\fonts\\\\marlett.ttf"
"Mashq (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_Mashq.ttf"
"Mashq Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_Mashq-Bold.ttf"
"Metal (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_Metal.ttf"
"Mukti Narrow (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-indic-fonts-core\\MuktiNarrow.ttf"
"Nada (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_Nada.ttf"
"Nagham (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_Nagham.ttf"
"Nice (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_Nice.ttf"
"Norasi (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\Norasi.ttf"
"Norasi Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\Norasi-Bold.ttf"
"Norasi BoldItalic (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\Norasi-BoldItalic.ttf"
"Norasi BoldOblique (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\Norasi-BoldOblique.ttf"
"Norasi Italic (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\Norasi-Italic.ttf"
"Norasi Oblique (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\Norasi-Oblique.ttf"
"OpenSymbol (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\openoffice\\opens___.ttf"
"ori1Uni (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-indic-fonts-core\\utkal.ttf"
"Ostorah (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_Ostorah.ttf"
"Ouhod Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_Ouhod-Bold.ttf"
"Petra (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_Petra.ttf"
"Phetsarath OT (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-lao\\Phetsarath_OT.ttf"
"Purisa (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\Purisa.ttf"
"Rachana_w01 (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-malayalam-fonts\\Rachana_w01.ttf"
"Rasheeq Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_Rasheeq-Bold.ttf"
"Rehan (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_Rehan.ttf"
"Salem (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_Salem.ttf"
"Sawasdee (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\Sawasdee.ttf"
"Sawasdee Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\SawasdeeBold.ttf"
"Sawasdee BoldOblique (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\SawasdeeBoldOblique.ttf"
"Sawasdee Oblique (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\SawasdeeOblique.ttf"
"Shado (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_Shado.ttf"
"Sharjah (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_Sharjah.ttf"
"Sindbad (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_Sindbad.ttf"
"Tahoma (TrueType)"="Z:\\usr\\bin\\..\\lib\\..\\share\\wine\\fonts\\\\tahoma.ttf"
"Tahoma Bold (TrueType)"="Z:\\usr\\bin\\..\\lib\\..\\share\\wine\\fonts\\\\tahomabd.ttf"
"Tarablus (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_Tarablus.ttf"
"Tholoth (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-arabeyes\\ae_Tholoth.ttf"
"Times New Roman (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\msttcorefonts\\times.ttf"
"Times New Roman Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\msttcorefonts\\Times_New_Roman_Bold.ttf"
"Times New Roman Bold Italic (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\msttcorefonts\\Times_New_Roman_Bold_Italic.ttf"
"Times New Roman Italic (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\msttcorefonts\\Times_New_Roman_Italic.ttf"
"Tlwg Typist (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\TlwgTypist.ttf"
"Tlwg Typist Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\TlwgTypist-Bold.ttf"
"Tlwg Typist BoldOblique (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\TlwgTypist-BoldOblique.ttf"
"Tlwg Typist Oblique (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\TlwgTypist-Oblique.ttf"
"TlwgMono (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\TlwgMono.ttf"
"TlwgMono Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\TlwgMono-Bold.ttf"
"TlwgMono BoldOblique (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\TlwgMono-BoldOblique.ttf"
"TlwgMono Oblique (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\TlwgMono-Oblique.ttf"
"TlwgTypewriter (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\TlwgTypewriter.ttf"
"TlwgTypewriter Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\TlwgTypewriter-Bold.ttf"
"TlwgTypewriter BoldOblique (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\TlwgTypewriter-BoldOblique.ttf"
"TlwgTypewriter Oblique (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\TlwgTypewriter-Oblique.ttf"
"Trebuchet MS (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\msttcorefonts\\trebuc.ttf"
"Trebuchet MS Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\msttcorefonts\\trebucbd.ttf"
"Trebuchet MS Bold Italic (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\msttcorefonts\\trebucbi.ttf"
"Trebuchet MS Italic (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\msttcorefonts\\Trebuchet_MS_Italic.ttf"
"UnBatang (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\unfonts\\UnBatang.ttf"
"UnBatang Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\unfonts\\UnBatangBold.ttf"
"UnDotum (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\unfonts\\UnDotum.ttf"
"UnDotum Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\unfonts\\UnDotumBold.ttf"
"Vemana2000 (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\ttf-indic-fonts-core\\Vemana.ttf"
"Verdana (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\msttcorefonts\\Verdana.ttf"
"Verdana Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\msttcorefonts\\verdanab.ttf"
"Verdana Bold Italic (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\msttcorefonts\\Verdana_Bold_Italic.ttf"
"Verdana Italic (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\msttcorefonts\\Verdana_Italic.ttf"
"Waree (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\Waree.ttf"
"Waree Bold (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\Waree-Bold.ttf"
"Waree BoldOblique (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\Waree-BoldOblique.ttf"
"Waree Oblique (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\thai\\Waree-Oblique.ttf"
"Webdings (TrueType)"="Z:\\usr\\share\\fonts\\truetype\\msttcorefonts\\Webdings.ttf"

[Software\\Wine\\MSHTML] 1215629009
"GeckoUrl"="http://source.winehq.org/winegecko.php"

[Software\\Wine\\MSHTML\\0.1.0] 1215629747
"GeckoPath"="C:\\windows\\gecko\\0.1.0\\wine_gecko"

[Software\\Wine\\OpenGL] 1222024565
"DisabledExtensions"="GL_ARB_vertex_buffer_object"

[Software\\Wine\\WineDbg] 1215821129

```

Several people have reported this issue, but they've found no solution to it yet:

[http://www.nvnews.net/vbulletin/showthread.php?t=117441](http://www.nvnews.net/vbulletin/showthread.php?t=117441)

But it's not picked up yet at wowwiki:

[http://www.wowwiki.com/Troubleshooting_Wine](http://www.wowwiki.com/Troubleshooting_Wine)

---

