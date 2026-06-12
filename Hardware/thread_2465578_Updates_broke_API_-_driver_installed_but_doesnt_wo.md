---
title: "Updates broke API - driver installed but doesnt work. STUMPED"
date: 2021-08-05
forum: Hardware
---

### Post by chadderdeux on 2021-08-05
I game mainly playing Dota 2 and Eve online through steam/proton. After the updates yesterday, I could no longer play my games. As first Eve would tell me that I had no video driver, I managed to get that warning to go away but I still can't get the game to launch. Also with DOTA 2 it says im running in Open GL and I cant find out how to switch it to vulkan. 
Also my refresh rate is limited in my display settings. I feel like I am having a driver issue but I am out of my depth. Ill provide some information...

Here is my GRUB: 
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash radeon.si_support=0 amdgpu.si_support=1 radeon.cik_support=0 amdgpu.cik_support=1"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```


heres more info
```
aphex@aphex-machi:~$ lspci \-nnk | grep \-i vga \-A3 | grep 'in use' 
    Kernel driver in use: radeon 

```

```
aphex@aphex-machi:~$ sudo lshw -c video 
  *-display                  
       description: VGA compatible controller 
       product: Pitcairn PRO [Radeon HD 7850 / R7 265 / R9 270 1024SP] 
       vendor: Advanced Micro Devices, Inc. [AMD/ATI] 
       physical id: 0 
       bus info: pci@0000:07:00.0 
       version: 00 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom 
       configuration: driver=radeon latency=0 
       resources: irq:97 memory:e0000000-efffffff memory:fcf00000-fcf3ffff ioport:f000(size=256) memory:c0000-dffff 


```
```

aphex@aphex-machi:~$ lspci 
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse Root Complex 
00:00.2 IOMMU: Advanced Micro Devices, Inc. [AMD] Starship/Matisse IOMMU 
00:01.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse PCIe Dummy Host Bridge 
00:01.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse GPP Bridge 
00:02.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse PCIe Dummy Host Bridge 
00:03.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse PCIe Dummy Host Bridge 
00:03.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse GPP Bridge 
00:04.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse PCIe Dummy Host Bridge 
00:05.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse PCIe Dummy Host Bridge 
00:07.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse PCIe Dummy Host Bridge 
00:07.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse Internal PCIe GPP Bridge 0 to bus[E:B] 
00:08.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse PCIe Dummy Host Bridge 
00:08.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse Internal PCIe GPP Bridge 0 to bus[E:B] 
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 61) 
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 51) 
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Matisse Device 24: Function 0 
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Matisse Device 24: Function 1 
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Matisse Device 24: Function 2 
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Matisse Device 24: Function 3 
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Matisse Device 24: Function 4 
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Matisse Device 24: Function 5 
00:18.6 Host bridge: Advanced Micro Devices, Inc. [AMD] Matisse Device 24: Function 6 
00:18.7 Host bridge: Advanced Micro Devices, Inc. [AMD] Matisse Device 24: Function 7 
01:00.0 USB controller: Advanced Micro Devices, Inc. [AMD] Device 43ee 
01:00.1 SATA controller: Advanced Micro Devices, Inc. [AMD] Device 43eb 
01:00.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 43e9 
02:00.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 43ea 
02:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 43ea 
02:08.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 43ea 
02:09.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 43ea 
04:00.0 Non-Volatile memory controller: Sandisk Corp WD Blue SN550 NVMe SSD (rev 01) 
05:00.0 Network controller: Intel Corporation Wi-Fi 6 AX200 (rev 1a) 
06:00.0 Ethernet controller: Intel Corporation Ethernet Controller I225-V (rev 02) 
07:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Pitcairn PRO [Radeon HD 7850 / R7 265 / R9 270 1024SP] 
07:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Oland/Hainan/Cape Verde/Pitcairn HDMI Audio [Radeon HD 7000 Series] 
08:00.0 Non-Essential Instrumentation [1300]: Advanced Micro Devices, Inc. [AMD] Starship/Matisse PCIe Dummy Function 
09:00.0 Non-Essential Instrumentation [1300]: Advanced Micro Devices, Inc. [AMD] Starship/Matisse Reserved SPP 
09:00.1 Encryption controller: Advanced Micro Devices, Inc. [AMD] Starship/Matisse Cryptographic Coprocessor PSPCPP 
09:00.3 USB controller: Advanced Micro Devices, Inc. [AMD] Matisse USB 3.0 Host Controller 
09:00.4 Audio device: Advanced Micro Devices, Inc. [AMD] Starship/Matisse HD Audio Controller 

```


```
aphex@aphex-machi:~$ glxgears -info 
Running synchronized to the vertical refresh.  The framerate should be 
approximately the same as the monitor refresh rate. 
GL_RENDERER   = AMD PITCAIRN (DRM 2.50.0, 5.11.0-25-generic, LLVM 12.0.1) 
GL_VERSION    = 4.5 (Compatibility Profile) Mesa 21.3.0-devel (git-da00a11 2021-08-05 hirsute-oibaf-ppa) 
GL_VENDOR     = AMD 
GL_EXTENSIONS = GL_ARB_multisample GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_copy_texture GL_EXT_subtexture GL_EXT_texture_object GL_EXT_vertex_array GL_EXT_compiled_vertex_array GL_EXT_texture GL_EXT_texture3D GL_IBM_rasterpos_clip GL_ARB_point_parameters GL_EXT_draw_range_elements GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_separate_specular_color GL_EXT_texture_edge_clamp GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_ARB_framebuffer_sRGB GL_ARB_multitexture GL_EXT_framebuffer_sRGB GL_IBM_multimode_draw_arrays GL_IBM_texture_mirrored_repeat GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_transpose_matrix GL_EXT_blend_func_separate GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_secondary_color GL_EXT_texture_env_add GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_INGR_blend_func_separate GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texgen_reflection GL_NV_texture_env_combine4 GL_S3_s3tc GL_SUN_multi_draw_arrays GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_EXT_framebuffer_object GL_EXT_texture_compression_s3tc GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_MESA_window_pos GL_NV_packed_depth_stencil GL_NV_texture_rectangle GL_ARB_depth_texture GL_ARB_occlusion_query GL_ARB_shadow GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_window_pos GL_ATI_fragment_shader GL_EXT_stencil_two_side GL_EXT_texture_cube_map GL_NV_copy_depth_to_color GL_NV_depth_clamp GL_NV_fog_distance GL_NV_half_float GL_APPLE_packed_pixels GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_shader GL_ARB_shader_objects GL_ARB_vertex_program GL_ARB_vertex_shader GL_ATI_draw_buffers GL_ATI_texture_env_combine3 GL_ATI_texture_float GL_EXT_depth_bounds_test GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_MESA_pack_invert GL_NV_primitive_restart GL_ARB_depth_clamp GL_ARB_fragment_program_shadow GL_ARB_half_float_pixel GL_ARB_occlusion_query2 GL_ARB_point_sprite GL_ARB_shading_language_100 GL_ARB_sync GL_ARB_texture_non_power_of_two GL_ARB_vertex_buffer_object GL_ATI_blend_equation_separate GL_EXT_blend_equation_separate GL_OES_read_format GL_ARB_color_buffer_float GL_ARB_pixel_buffer_object GL_ARB_texture_compression_rgtc GL_ARB_texture_float GL_ARB_texture_rectangle GL_ATI_texture_compression_3dc GL_EXT_packed_float GL_EXT_pixel_buffer_object GL_EXT_texture_compression_dxt1 GL_EXT_texture_compression_rgtc GL_EXT_texture_mirror_clamp GL_EXT_texture_rectangle GL_EXT_texture_sRGB GL_EXT_texture_shared_exponent GL_ARB_framebuffer_object GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_packed_depth_stencil GL_ARB_vertex_array_object GL_ATI_separate_stencil GL_ATI_texture_mirror_once GL_EXT_draw_buffers2 GL_EXT_draw_instanced GL_EXT_gpu_program_parameters GL_EXT_gpu_shader4 GL_EXT_texture_array GL_EXT_texture_compression_latc GL_EXT_texture_integer GL_EXT_texture_sRGB_decode GL_EXT_timer_query GL_OES_EGL_image GL_AMD_performance_monitor GL_EXT_texture_buffer_object GL_AMD_texture_texture4 GL_ARB_copy_buffer GL_ARB_depth_buffer_float GL_ARB_draw_instanced GL_ARB_half_float_vertex GL_ARB_instanced_arrays GL_ARB_map_buffer_range GL_ARB_texture_buffer_object GL_ARB_texture_rg GL_ARB_texture_swizzle GL_ARB_vertex_array_bgra GL_EXT_texture_swizzle GL_EXT_vertex_array_bgra GL_NV_conditional_render GL_AMD_conservative_depth GL_AMD_depth_clamp_separate GL_AMD_draw_buffers_blend GL_AMD_seamless_cubemap_per_texture GL_AMD_shader_stencil_export GL_ARB_ES2_compatibility GL_ARB_blend_func_extended GL_ARB_compatibility GL_ARB_debug_output GL_ARB_draw_buffers_blend GL_ARB_draw_elements_base_vertex GL_ARB_explicit_attrib_location GL_ARB_fragment_coord_conventions GL_ARB_provoking_vertex GL_ARB_sample_shading GL_ARB_sampler_objects GL_ARB_seamless_cube_map GL_ARB_shader_stencil_export GL_ARB_shader_texture_lod GL_ARB_tessellation_shader GL_ARB_texture_buffer_object_rgb32 GL_ARB_texture_cube_map_array GL_ARB_texture_gather GL_ARB_texture_multisample GL_ARB_texture_query_lod GL_ARB_texture_rgb10_a2ui GL_ARB_uniform_buffer_object GL_ARB_vertex_type_2_10_10_10_rev GL_ATI_meminfo GL_EXT_provoking_vertex GL_EXT_texture_snorm GL_MESA_texture_signed_rgba GL_NV_copy_image GL_NV_texture_barrier GL_ARB_draw_indirect GL_ARB_get_program_binary GL_ARB_gpu_shader5 GL_ARB_gpu_shader_fp64 GL_ARB_robustness GL_ARB_separate_shader_objects GL_ARB_shader_bit_encoding GL_ARB_shader_precision GL_ARB_shader_subroutine GL_ARB_texture_compression_bptc GL_ARB_timer_query GL_ARB_transform_feedback2 GL_ARB_transform_feedback3 GL_ARB_vertex_attrib_64bit GL_ARB_viewport_array GL_EXT_direct_state_access GL_EXT_shader_image_load_store GL_EXT_vertex_attrib_64bit GL_NV_vdpau_interop GL_AMD_multi_draw_indirect GL_ANGLE_texture_compression_dxt3 GL_ANGLE_texture_compression_dxt5 GL_ARB_base_instance GL_ARB_compressed_texture_pixel_storage GL_ARB_conservative_depth GL_ARB_internalformat_query GL_ARB_map_buffer_alignment GL_ARB_shader_atomic_counters GL_ARB_shader_image_load_store GL_ARB_shading_language_420pack GL_ARB_shading_language_packing GL_ARB_texture_storage GL_ARB_transform_feedback_instanced GL_EXT_framebuffer_multisample_blit_scaled GL_EXT_transform_feedback GL_AMD_query_buffer_object GL_AMD_shader_trinary_minmax GL_AMD_vertex_shader_layer GL_AMD_vertex_shader_viewport_index GL_ARB_ES3_compatibility GL_ARB_arrays_of_arrays GL_ARB_clear_buffer_object GL_ARB_compute_shader GL_ARB_copy_image GL_ARB_explicit_uniform_location GL_ARB_fragment_layer_viewport GL_ARB_framebuffer_no_attachments GL_ARB_invalidate_subdata GL_ARB_multi_draw_indirect GL_ARB_program_interface_query GL_ARB_robust_buffer_access_behavior GL_ARB_shader_image_size GL_ARB_shader_storage_buffer_object GL_ARB_stencil_texturing GL_ARB_texture_buffer_range GL_ARB_texture_query_levels GL_ARB_texture_storage_multisample GL_ARB_texture_view GL_ARB_vertex_attrib_binding GL_KHR_debug GL_KHR_robustness GL_KHR_texture_compression_astc_ldr GL_AMD_pinned_memory GL_ARB_bindless_texture GL_ARB_buffer_storage GL_ARB_clear_texture GL_ARB_compute_variable_group_size GL_ARB_enhanced_layouts GL_ARB_internalformat_query2 GL_ARB_multi_bind GL_ARB_query_buffer_object GL_ARB_seamless_cubemap_per_texture GL_ARB_shader_group_vote GL_ARB_shading_language_include GL_ARB_texture_mirror_clamp_to_edge GL_ARB_texture_stencil8 GL_ARB_vertex_type_10f_11f_11f_rev GL_EXT_shader_integer_mix GL_NVX_gpu_memory_info GL_ARB_ES3_1_compatibility GL_ARB_clip_control GL_ARB_conditional_render_inverted GL_ARB_cull_distance GL_ARB_derivative_control GL_ARB_direct_state_access GL_ARB_get_texture_sub_image GL_ARB_pipeline_statistics_query GL_ARB_shader_texture_image_samples GL_ARB_texture_barrier GL_ARB_transform_feedback_overflow_query GL_EXT_polygon_offset_clamp GL_EXT_shader_image_load_formatted GL_KHR_blend_equation_advanced GL_KHR_context_flush_control GL_KHR_robust_buffer_access_behavior GL_NV_shader_atomic_int64 GL_ARB_gpu_shader_int64 GL_ARB_parallel_shader_compile GL_ARB_shader_atomic_counter_ops GL_ARB_shader_ballot GL_ARB_shader_clock GL_ARB_shader_viewport_layer_array GL_EXT_shader_samples_identical GL_EXT_texture_sRGB_R8 GL_KHR_no_error GL_KHR_texture_compression_astc_sliced_3d GL_ARB_gl_spirv GL_ARB_spirv_extensions GL_EXT_window_rectangles GL_MESA_shader_integer_functions GL_ARB_polygon_offset_clamp GL_ARB_texture_filter_anisotropic GL_EXT_memory_object GL_EXT_memory_object_fd GL_KHR_parallel_shader_compile GL_NV_alpha_to_coverage_dither_control GL_EXT_EGL_image_storage GL_EXT_texture_shadow_lod GL_INTEL_blackhole_render GL_MESA_framebuffer_flip_y GL_NV_compute_shader_derivatives GL_EXT_EGL_sync GL_EXT_demote_to_helper_invocation  
VisualID 520, 0x208 
157 frames in 5.0 seconds = 31.239 FPS 
150 frames in 5.0 seconds = 29.996 FPS 
151 frames in 5.0 seconds = 30.000 FPS 
151 frames in 5.0 seconds = 29.995 FPS 
151 frames in 5.0 seconds = 30.003 FPS 
150 frames in 5.0 seconds = 29.998 FPS 
150 frames in 5.0 seconds = 29.998 FPS 
150 frames in 5.0 seconds = 29.996 FPS 
X connection to :0 broken (explicit kill or server shutdown).
```


Dota 2 launches but in open gl. My refresh rate is locked at 30hz.. Eve online wont even launch into the game without an error.
I fee llike it all comes down to a driver issue. It's like ubuntu will not select the vulkan driver.

If there is any other information I can provide please let me know. I'm desperate.

---

### Post by QIII on 2021-08-05
@chadderdeux --

Please use code tags to enclose all terminal commands and their results.  This maintains the formatting and also makes your posts easier to read.

To use code tags:


1. If you are using the "Reply to Thread" button, please type or paste your text, highlight the text and use the # button in the text box header. Alternatively, click the # button first, place your cursor between the code tags and type or paste your text.

2. If using "Quick Reply" then type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.  The square brackets are required.

---

### Post by Yellow Pasque on 2021-08-05
Initial thought:
```
"driver=radeon"
``` means 
```
"radeon.si_support=0 amdgpu.si_support=1 radeon.cik_support=0 amdgpu.cik_support=1"
```  is not working the way you want it to. You need the amdgpu module for Vulkan support.

So it's probably time to grep through dmesg or journalctl with radeon|amdgpu to find out why.

---

### Post by zeith on 2021-08-24
@chadderdeux --

have you managed to fix it?

---

