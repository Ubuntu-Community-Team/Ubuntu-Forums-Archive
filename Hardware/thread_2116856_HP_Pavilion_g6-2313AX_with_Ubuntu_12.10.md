---
title: "HP Pavilion g6-2313AX with Ubuntu 12.10"
date: 2013-02-16
forum: Hardware
---

### Post by khatkarrohit on 2013-02-16
I bought this laptop [HP Pavilion g6-2313AX]("http://h10025.www1.hp.com/ewfrf/wc/document?cc=us&lc=en&dlc=en&docname=c03281944") and many devices are not working with Ubuntu whereas it works nice even with windows 8 default installation. Here are its spces: 
**Hardware**
Product Name:	                    **g6-2313ax**
Microprocessor:	                    **2.3 GHz AMD Quad-Core A10-4600M**
Microprocessor Cache:	            **4 MB L2 cache**
Memory:	                            **6 GB 1600 MHz DDR3**
Video Graphics:	                    **AMD Radeon HD 7660G/7670M Dual GPU (2 GB DDR3 dedicated)**
Display:	                    **15.6" diagonal HD BrightView LED-backlit (1366 x 768)**
Hard Drive:	                    **1 TB 5400 rpm SATA**
Wireless Connectivity:	            **Bluetooth, 802.11b/g/n**
Keyboard:	                    **Full-size island-style keyboard**
Pointing Device	                    **TouchPad supporting multi-touch gestures and on/off button**
PC Card Slots:	                    **Multi-format digital media card reader for secure digital cards & multimedia cards**
Operating System:                   **FreeDOS**

OS installed: **Dual boot. Windows 8 64 bit and Ubuntu 12.10 64 bit**

[B]Starting with processor:2.3 GHz AMD Quad-Core A10-4600M
[/B]Processor always run on full power/speed while on Windows 8 processor remains silent and make even less noise while running heavy programs on Windows 8. On Ubuntu even if I open Software Sources than the processor goes wild and whole system goes slow and other application stops responding. What to do so that the processor or its fan goes slow/silent.

**Video Graphics Not working :AMD Radeon HD 7660G/7670M Dual GPU (2 GB DDR3 dedicated)**:
Ubuntu System Details says unknown Graphics and experience Standard. It does not detect 7670M Graphics card. After installing ATI drivers from Software Center it gives option to use Open source driver or proprietary driver. After selecting proprietary driver GUI desktop does not boot. After removing fglrx from command line desktop again starts working after reboot. I will try beta graphics driver today downloaded from AMD site but if anybody know any solution then please share your solution or experience here..


**Display:15.6" diagonal HD BrightView LED-backlit (1366 x 768)**:
Brightness does not work at all. There is tweak to add few words in grup file. But that works only if upgraded kernel like 3.7.8 is installed.

**Wireless Connectivity:Bluetooth, 802.11b/g/n**
Neither wireless nor Bluetooth works with ubuntu. Wireless works with Ralink RT3290 firmware but only with upgraded Linux kernel to 3.7.8. Even after few minutes wifi stopped working and it says device not ready. Bluetooth never worked.

**Keyboard:Full-size island-style keyboard**
Keyboard works works fine except the wifi on/off button light indicator. But it is able to turn off and on the external wifi dongle. Brightness key works but brightness does not change on the screen.

**Pointing Device:TouchPad supporting multi-touch gestures and on/off button**
It works but TouchPad on.off button does not work.

Because of all these problems above stated, the battery life decreases to mere 1 hour and 12 minutes whereas in windows it is little more than 2 hour and 30 minutes.

Don't know about Card reader, HDMI output and other things. Very bad laptop. Waiting for the new release of Ubuntu 13.04 otherwise have to switch back to windows for this laptop to work for me. I read on a website that Ubuntu 13.04 has new kernel 3.7.8, which support brightness control and wifi and maybe other things too. :-(

Does anybody has similar configuration with working Ubuntu 12.10 drivers for this hardware.

---

### Post by Yellow Pasque on 2013-02-17
The battery life and fan noise should get a lot better once you have the GPU driver installed.

EDIT: On second thought, you'll have to do some patching to get the AMD driver working with 3.7.x kernel. It would really be better for you to just use Ubuntu 13.04 with such new hardware (at least the AMD driver is easy to install there).

---

### Post by khatkarrohit on 2013-02-17
I installed the beta drivers for graphics from [AMD support website]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx"). But while installation from GUI no text was visible, so I continued clicking blindly on every right option button.


[IMG]https://lh4.googleusercontent.com/-us9dkz4bHlQ/USCDrPI3_RI/AAAAAAAAAHA/n-HDtwWxi2s/s640/Screenshot%2520from%25202013-02-17%252012%253A11%253A48.png[/IMG]

Here is the log after installation:
> Supported adapter detected.
Supported adapter detected.
Check if system has the tools required for installation.
Uninstalling any previously installed drivers.

Creating symlink /var/lib/dkms/fglrx/12.10.17/source ->
                 /usr/src/fglrx-12.10.17

DKMS: add completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
cd /var/lib/dkms/fglrx/12.10.17/build; sh make.sh --nohints --uname_r=3.5.0-23-generic --norootcheck.......
cleaning build area....

DKMS: build completed.

fglrx:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.5.0-23-generic/updates/dkms/

depmod........

DKMS: install completed.
[Reboot] Kernel Module : update-initramfs

After installing graphic driver, it feels like Processor is now in silent mode and not making too much noise.

Also the brightness up/down button also start working without any tweaks.

The wifi on/off indicator light on F12 also start working now turned white and remain white. But only for external wifi dongle. Internal wifi/blutooth is not working.


But there is a problem now that on right-down corner there is a watermark warning displaying > AMD Testing use Only. Even it is not coming in screenshot.

Is there any way to get information about graphic card in use and mode of graphic card now. In *System Settings --> Details* it is still showing > Graphics Unkown

---

### Post by Yellow Pasque on 2013-02-17
> Is there any way to get information about graphic card in use and mode of graphic card now.
```
sudo apt-get install mesa-utils
glxinfo
```

---

### Post by sulekhadahiya on 2013-02-17
> **Temüjin said:**
> ```
sudo apt-get install mesa-utils
glxinfo
```

Here is output of command glxinfo:
> name of display: :0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: ATI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group
client glx vendor string: ATI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_swap_control, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_MESA_allocate_memory, GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_NV_swap_group, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_swap_barrier, GLX_SGIX_swap_group, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap, GLX_EXT_framebuffer_sRGB, 
    GLX_ARB_fbconfig_float, GLX_AMD_gpu_association
GLX version: 1.4
GLX extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_swap_control, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_MESA_swap_control, GLX_NV_swap_group, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_swap_barrier, GLX_SGIX_swap_group, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 7600M Series
OpenGL version string: 4.2.12171 Compatibility Profile Context 12.10.17
OpenGL shading language version string: 4.20
OpenGL extensions:
    GL_AMDX_debug_output, GL_AMDX_vertex_shader_tessellator, 
    GL_AMD_conservative_depth, GL_AMD_debug_output, 
    GL_AMD_depth_clamp_separate, GL_AMD_draw_buffers_blend, 
    GL_AMD_multi_draw_indirect, GL_AMD_name_gen_delete, 
    GL_AMD_performance_monitor, GL_AMD_pinned_memory, 
    GL_AMD_query_buffer_object, GL_AMD_sample_positions, 
    GL_AMD_seamless_cubemap_per_texture, GL_AMD_shader_stencil_export, 
    GL_AMD_shader_trace, GL_AMD_texture_cube_map_array, 
    GL_AMD_texture_texture4, GL_AMD_transform_feedback3_lines_triangles, 
    GL_AMD_vertex_shader_layer, GL_AMD_vertex_shader_tessellator, 
    GL_AMD_vertex_shader_viewport_index, GL_ARB_ES2_compatibility, 
    GL_ARB_base_instance, GL_ARB_blend_func_extended, 
    GL_ARB_color_buffer_float, GL_ARB_compressed_texture_pixel_storage, 
    GL_ARB_conservative_depth, GL_ARB_copy_buffer, GL_ARB_depth_buffer_float, 
    GL_ARB_depth_clamp, GL_ARB_depth_texture, GL_ARB_draw_buffers, 
    GL_ARB_draw_buffers_blend, GL_ARB_draw_elements_base_vertex, 
    GL_ARB_draw_indirect, GL_ARB_draw_instanced, 
    GL_ARB_explicit_attrib_location, GL_ARB_fragment_coord_conventions, 
    GL_ARB_fragment_layer_viewport, GL_ARB_fragment_program, 
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader, 
    GL_ARB_framebuffer_object, GL_ARB_framebuffer_sRGB, 
    GL_ARB_geometry_shader4, GL_ARB_get_program_binary, GL_ARB_gpu_shader5, 
    GL_ARB_gpu_shader_fp64, GL_ARB_half_float_pixel, GL_ARB_half_float_vertex, 
    GL_ARB_imaging, GL_ARB_instanced_arrays, GL_ARB_internalformat_query, 
    GL_ARB_map_buffer_alignment, GL_ARB_map_buffer_range, 
    GL_ARB_multi_draw_indirect, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_occlusion_query, GL_ARB_occlusion_query2, 
    GL_ARB_pixel_buffer_object, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_provoking_vertex, GL_ARB_sample_shading, GL_ARB_sampler_objects, 
    GL_ARB_seamless_cube_map, GL_ARB_separate_shader_objects, 
    GL_ARB_shader_atomic_counters, GL_ARB_shader_bit_encoding, 
    GL_ARB_shader_image_load_store, GL_ARB_shader_objects, 
    GL_ARB_shader_precision, GL_ARB_shader_stencil_export, 
    GL_ARB_shader_subroutine, GL_ARB_shader_texture_lod, 
    GL_ARB_shading_language_100, GL_ARB_shading_language_420pack, 
    GL_ARB_shading_language_packing, GL_ARB_shadow, GL_ARB_shadow_ambient, 
    GL_ARB_sync, GL_ARB_tessellation_shader, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_buffer_object, GL_ARB_texture_buffer_object_rgb32, 
    GL_ARB_texture_buffer_range, GL_ARB_texture_compression, 
    GL_ARB_texture_compression_bptc, GL_ARB_texture_compression_rgtc, 
    GL_ARB_texture_cube_map, GL_ARB_texture_cube_map_array, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_float, GL_ARB_texture_gather, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_multisample, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_query_lod, 
    GL_ARB_texture_rectangle, GL_ARB_texture_rg, GL_ARB_texture_rgb10_a2ui, 
    GL_ARB_texture_snorm, GL_ARB_texture_storage, 
    GL_ARB_texture_storage_multisample, GL_ARB_timer_query, 
    GL_ARB_transform_feedback2, GL_ARB_transform_feedback3, 
    GL_ARB_transform_feedback_instanced, GL_ARB_transpose_matrix, 
    GL_ARB_uniform_buffer_object, GL_ARB_vertex_array_bgra, 
    GL_ARB_vertex_array_object, GL_ARB_vertex_attrib_64bit, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_vertex_type_2_10_10_10_rev, GL_ARB_viewport_array, 
    GL_ARB_window_pos, GL_ATI_draw_buffers, GL_ATI_envmap_bumpmap, 
    GL_ATI_fragment_shader, GL_ATI_meminfo, GL_ATI_separate_stencil, 
    GL_ATI_texture_compression_3dc, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_float, GL_ATI_texture_mirror_once, GL_EXT_abgr, 
    GL_EXT_bgra, GL_EXT_bindable_uniform, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, 
    GL_EXT_copy_buffer, GL_EXT_copy_texture, GL_EXT_direct_state_access, 
    GL_EXT_draw_buffers2, GL_EXT_draw_instanced, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_blit, GL_EXT_framebuffer_multisample, 
    GL_EXT_framebuffer_object, GL_EXT_framebuffer_sRGB, 
    GL_EXT_geometry_shader4, GL_EXT_gpu_program_parameters, 
    GL_EXT_gpu_shader4, GL_EXT_histogram, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_float, GL_EXT_packed_pixels, 
    GL_EXT_pixel_buffer_object, GL_EXT_point_parameters, 
    GL_EXT_provoking_vertex, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shader_image_load_store, 
    GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texgen_reflection, GL_EXT_texture3D, GL_EXT_texture_array, 
    GL_EXT_texture_buffer_object, GL_EXT_texture_compression_bptc, 
    GL_EXT_texture_compression_latc, GL_EXT_texture_compression_rgtc, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_integer, 
    GL_EXT_texture_lod, GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, 
    GL_EXT_texture_sRGB_decode, GL_EXT_texture_shared_exponent, 
    GL_EXT_texture_snorm, GL_EXT_texture_storage, GL_EXT_texture_swizzle, 
    GL_EXT_timer_query, GL_EXT_transform_feedback, GL_EXT_vertex_array, 
    GL_EXT_vertex_array_bgra, GL_EXT_vertex_attrib_64bit, 
    GL_IBM_texture_mirrored_repeat, GL_KTX_buffer_region, GL_NV_blend_square, 
    GL_NV_conditional_render, GL_NV_copy_depth_to_color, GL_NV_copy_image, 
    GL_NV_explicit_multisample, GL_NV_float_buffer, GL_NV_half_float, 
    GL_NV_primitive_restart, GL_NV_texgen_reflection, GL_NV_texture_barrier, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, 
    GL_SUN_multi_draw_arrays, GL_WIN_swap_hint

81 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x023 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x024 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x025 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x026 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x027 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x028 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x029 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x02a 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x02b 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x02c 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x02d 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x02e 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x02f 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x030 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x031 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x032 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x033 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x034 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x035 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x036 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x037 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x038 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x039 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x03a 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x03b 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x03c 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x03d 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x03e 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x03f 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  6 1 None
0x040 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  6 1 None
0x041 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  6 1 None
0x042 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  6 1 None
0x043 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x044 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x045 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x046 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x047 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x048 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x049 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x04a 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x04b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x04c 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x04d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x04e 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x04f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x050 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x051 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x052 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x053 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x054 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x055 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x056 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x057 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x058 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x059 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x05a 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x05b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x05c 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x05d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x05e 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x05f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x060 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x061 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x062 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x063 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x064 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x065 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x066 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x067 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  6 1 None
0x068 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  6 1 None
0x069 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  6 1 None
0x06a 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  6 1 None
0x06b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x06c 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x06d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x06e 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x06f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x070 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x071 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x072 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x0af 32 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 Ncon

91 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x023 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x024 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x025 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x026 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x027 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x028 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x029 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x02a 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x02b 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x02c 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x02d 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x02e 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x02f 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x030 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x031 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x032 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x033 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x034 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x035 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x036 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x037 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x038 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x039 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x03a 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x03b 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x03c 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x03d 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x03e 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x03f 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  6 1 None
0x040 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  6 1 None
0x041 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  6 1 None
0x042 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  6 1 None
0x043 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x044 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x045 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x046 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x047 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x048 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x049 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x04a 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x04b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x04c 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x04d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x04e 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x04f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x050 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x051 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x052 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x053 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x054 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x055 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x056 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x057 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x058 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x059 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x05a 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x05b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x05c 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x05d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x05e 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x05f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x060 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x061 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x062 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x063 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x064 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x065 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x066 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x067 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  6 1 None
0x068 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  6 1 None
0x069 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  6 1 None
0x06a 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  6 1 None
0x06b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x06c 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x06d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x06e 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x06f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x070 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x071 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x072 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x0af 32 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 Ncon
0x0af 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 Ncon
0x0af 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 Ncon
0x0af 32 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 Ncon
0x0af 32 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 Ncon
0x0af  0 tc  0 128  0    y .  32 32 32 32 .  .  0 24  0  0  0  0  0  0 0 None
0x0af  0 tc  0 128  0    . .  32 32 32 32 .  .  0 24  0  0  0  0  0  0 0 None
0x0af  0 tc  0  64  0    y .  16 16 16 16 .  .  0 24  0  0  0  0  0  0 0 None
0x0af  0 tc  0  64  0    . .  16 16 16 16 .  .  0 24  0  0  0  0  0  0 0 None
0x0af  0 tc  0  32  0    y .  11 11 10  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0af  0 tc  0  32  0    . .  11 11 10  0 .  .  0 24  0  0  0  0  0  0 0 None


Looks like graphic card 7670M is in use.
Here are screenshots of AMD Catalyst:
[IMG]https://lh4.googleusercontent.com/-Cp6szwcC8dk/USCd9Vtm2oI/AAAAAAAAAHg/jCKi_Kq0njc/s640/Screenshot%2520from%25202013-02-17%252014_22_31.png[/IMG]

[IMG]https://lh3.googleusercontent.com/-dOFhK7GJqmU/USCd9csVccI/AAAAAAAAAHc/Cd3xAnvtQhg/s640/Screenshot%2520from%25202013-02-17%252014_34_59.png[/IMG]

Does it mean that graphics can swith automatically or I have to do it manually.

[IMG]https://lh5.googleusercontent.com/-DsHeIWOH9xQ/USCd9gmqReI/AAAAAAAAAHk/ojbj7FqzoHM/s640/Screenshot%2520from%25202013-02-17%252014_35_17.png[/IMG]
Here the Graphic Adapter in use is AMD Radeon HD 7660G

---

### Post by Yellow Pasque on 2013-02-17
Everything looks good. Is it working okay?

---

### Post by sulekhadahiya on 2013-02-17
> **Temüjin said:**
> Everything looks good. Is it working okay?

Yeh its working now and I am using it and I faced no problem except one system freeze. The graphics is working good now and but when I tested battery life it reaches 1 hour and 40 minutes while in windows it is 2 hours and 40 minutes. There is a 1 hour difference. But that is not a big problem. I just connected power few minutes before.

I am still confused which graphics are in use. Is it the processor inbuilt graphics 7660G or the external graphic card 7670M or the dual graphic is enabled.

Also it looks like there is no automatic switching between graphics for power saving. On battery it should use 7660G inbuilt graphics and on power it should use external graphic card 7670M.

---

### Post by Yellow Pasque on 2013-02-17
> I am still confused which graphics are in use. Is it the processor inbuilt graphics 7660G or the external graphic card 7670M or the dual graphic is enabled.


Whichever one you select. This command should tell you
```
amdconfig --pxl
```
When you switch you may have to restart the X server (i.e. log out) for your selection to take effect.

---

### Post by sulekhadahiya on 2013-02-17
> **Temüjin said:**
> Whichever one you select. This command should tell you
```
amdconfig --pxl
```
When you switch you may have to restart the X server (i.e. log out) for your selection to take effect.

The output of the above command is:
> HP-Pavilion-g6-Notebook-PC:~$ amdconfig --pxl
PowerXpress: Discrete GPU is active (High-Performance mode).


It means I have to disable the discrete graphics when on battery to improve battery life. Selecting the Power saving GPU and then either logout and login or simply restart.

and Is launchpad the right place to file bug that a particular hardware is not supported by Ubuntu.

These two devices are creating problem for me now:
Network controller	Ralink corp. Device 3290
Bluetooth	Ralink corp. Device 3298

It is confirmed that Network controller	Ralink corp. Device 3290 will be supported in next Ubuntu 13.04 but there is no info for Bluetooth Ralink corp. Device 3298.

---

### Post by khatkarrohit on 2013-02-17
Thanks Temüjin. The main graphics problem is now solved and battery of the laptop with integrated graphics is giving backup like more than 2 hours and 30 minutes which is similar to windows.

---

