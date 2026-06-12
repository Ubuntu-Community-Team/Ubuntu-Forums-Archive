---
title: "Dell N5110 Nvidia Driver Issue Ubuntu 1204"
date: 2012-09-10
forum: Hardware
---

### Post by mahiyabz on 2012-09-10
Greetings, 

i have a Dell N5110 with Intel Display and GPU is only Nvidia GT 525M, lspci shows Nvidia 540M (wrong as compared from Windows, and Specs), but Jotkey don't detect Nvidia Graphics so can't install drivers for 3D. as Manual install always fails ending up with no display

can anyone help me on this ? i have also tried CentOS 6.2/6.3 and Opensuse 12.1, they both detects and tries to load Nouveau module but failed most times giving me Kernel Panic sometimes or no Display.

i have latest BIOS, sadly windows works fine on this but i prefer linux.

more details on laptop model is here
[http://www.dell.com/ae/p/inspiron-15r-n5110/pd](http://www.dell.com/ae/p/inspiron-15r-n5110/pd)

---

### Post by veroslav on 2012-09-10
Hi,

I'm suspecting you have an Optimus laptop (two graphic cards and switching between them).

Perhaps you need to do this:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

---

### Post by mahiyabz on 2012-09-10
Greetings, 

yes i have tried this, but still only intel graphics card works, with good resolution.

nvidia don't get detected, no HDMI or VGA out works. 3D sucks..

---

### Post by jaithehulk on 2012-09-10
A last resort can be Upgrade to kernel 3.5.
Do this with utmost caution and only if you have a optimus laptop.

---

### Post by mahiyabz on 2012-09-10
will install kernel 3.5 from repos 

will update post if fixed

---

### Post by mahiyabz on 2012-09-11
installed kernel 3.5 from PPA, still not good graphics, no nvidia detected

also system got hell slow :(

---

### Post by pogopuschel on 2012-09-11
> **jaithehulk said:**
> A last resort can be Upgrade to kernel 3.5.
Do this with utmost caution and only if you have a optimus laptop.
Sorry, but I do not see any sense here. A kernel upgrade won't help detecting a GPU.

@mahiyabz
You have a BIOS switch for VGA? Does the Nvidia Card appear in W7?
To confirm not-existing nvidia GPU please post output of:
```
lspci -k | grep -A2 -i vga
```

---

### Post by mahiyabz on 2012-09-12
Here we go, attached is the screen shoot from Windows 7 and then requested info of lspci

i have tried to show all info in screen below from Windows 7, it clearly shows me my 2 GPUs and they work 100% perfect, i can smoothly play MaxPayne3, or NFS RUN 

2nd

output from 
lspci -k | grep -A2 -i vga

> 
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
	Subsystem: Dell Device 04ca
	Kernel driver in use: i915
--
01:00.0 VGA compatible controller: NVIDIA Corporation GF108 [GeForce GT 540M] (rev a1)
	Subsystem: Dell Device 04ca
	Kernel driver in use: nvidia



also from lspci, just to show all

> 
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b5)
00:1c.7 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 8 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM67 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: NVIDIA Corporation GF108 [GeForce GT 540M] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GF108 High Definition Audio Controller (rev a1)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
09:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
0b:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)





when i installed Bumblebee, Intel Display went well, but 3D really really bad, ubuntu frozen when i open a webgl test site :S

Please help as am in middle of no where with Linux on my New Dell N5110

---

### Post by mahiyabz on 2012-09-12
adding, i have just upgraded to Latest BIOS (A10 for N5110) there is no switch i can just turn off the Intel or Nvidia Card.

also don't understand why lspci and win7 shows different Nvidia card models ?

---

### Post by pogopuschel on 2012-09-12
So your Nvidia got recognized. Jockey doesn't  offer a driver because it would break your X; the Nvidia driver has got to be installed in a special way, as bumblebee does.
Please post output from 
```
glxinfo
```
(maybe need to install mesa-utils)
and generate the bumblebee bugreport to attach it here:
```
sudo bumblebee-bugreport
```

---

### Post by mahiyabz on 2012-09-13
here we go

output from glxinfo

> name of display: :0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_swap_control, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_INTEL_swap_event
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_framebuffer_sRGB, 
    GLX_EXT_create_context_es2_profile, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_swap_control, 
    GLX_OML_swap_method, GLX_OML_sync_control, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap, GLX_INTEL_swap_event
GLX version: 1.4
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_swap_control, 
    GLX_OML_swap_method, GLX_OML_sync_control, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile 
OpenGL version string: 3.0 Mesa 8.0.2
OpenGL shading language version string: 1.30
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
    GL_SGIS_texture_lod, GL_ARB_framebuffer_sRGB, GL_ARB_multitexture, 
    GL_EXT_framebuffer_sRGB, GL_IBM_multimode_draw_arrays, 
    GL_IBM_texture_mirrored_repeat, GL_3DFX_texture_compression_FXT1, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, GL_ARB_transpose_matrix, 
    GL_EXT_blend_func_separate, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, 
    GL_EXT_secondary_color, GL_EXT_texture_env_add, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_INGR_blend_func_separate, GL_NV_blend_square, GL_NV_light_max_exponent, 
    GL_NV_texgen_reflection, GL_NV_texture_env_combine4, 
    GL_SUN_multi_draw_arrays, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_EXT_framebuffer_object, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, GL_MESA_window_pos, 
    GL_NV_packed_depth_stencil, GL_NV_texture_rectangle, GL_NV_vertex_program, 
    GL_ARB_depth_texture, GL_ARB_occlusion_query, GL_ARB_shadow, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_window_pos, GL_ATI_envmap_bumpmap, GL_EXT_stencil_two_side, 
    GL_EXT_texture_cube_map, GL_NV_depth_clamp, GL_NV_vertex_program1_1, 
    GL_APPLE_packed_pixels, GL_APPLE_vertex_array_object, GL_ARB_draw_buffers, 
    GL_ARB_fragment_program, GL_ARB_fragment_shader, GL_ARB_shader_objects, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ATI_draw_buffers, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_float, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_wrap, GL_MESA_pack_invert, GL_MESA_ycbcr_texture, 
    GL_ARB_depth_clamp, GL_ARB_fragment_program_shadow, 
    GL_ARB_half_float_pixel, GL_ARB_point_sprite, GL_ARB_shading_language_100, 
    GL_ARB_sync, GL_ARB_texture_non_power_of_two, GL_ARB_vertex_buffer_object, 
    GL_ATI_blend_equation_separate, GL_EXT_blend_equation_separate, 
    GL_OES_read_format, GL_ARB_color_buffer_float, GL_ARB_pixel_buffer_object, 
    GL_ARB_texture_compression_rgtc, GL_ARB_texture_float, 
    GL_ARB_texture_rectangle, GL_EXT_packed_float, GL_EXT_pixel_buffer_object, 
    GL_EXT_texture_compression_rgtc, GL_EXT_texture_rectangle, 
    GL_EXT_texture_sRGB, GL_EXT_texture_shared_exponent, 
    GL_ARB_framebuffer_object, GL_EXT_framebuffer_blit, 
    GL_EXT_framebuffer_multisample, GL_EXT_packed_depth_stencil, 
    GL_APPLE_object_purgeable, GL_ARB_vertex_array_object, 
    GL_ATI_separate_stencil, GL_EXT_draw_buffers2, 
    GL_EXT_gpu_program_parameters, GL_EXT_texture_array, 
    GL_EXT_texture_integer, GL_EXT_texture_sRGB_decode, GL_EXT_timer_query, 
    GL_OES_EGL_image, GL_MESA_texture_array, GL_ARB_copy_buffer, 
    GL_ARB_depth_buffer_float, GL_ARB_half_float_vertex, 
    GL_ARB_map_buffer_range, GL_ARB_texture_rg, GL_ARB_texture_swizzle, 
    GL_ARB_vertex_array_bgra, GL_EXT_separate_shader_objects, 
    GL_EXT_texture_swizzle, GL_EXT_vertex_array_bgra, 
    GL_NV_conditional_render, GL_ARB_ES2_compatibility, 
    GL_ARB_draw_elements_base_vertex, GL_ARB_explicit_attrib_location, 
    GL_ARB_fragment_coord_conventions, GL_ARB_provoking_vertex, 
    GL_ARB_sampler_objects, GL_ARB_seamless_cube_map, 
    GL_ARB_shader_texture_lod, GL_EXT_provoking_vertex, GL_EXT_texture_snorm, 
    GL_MESA_texture_signed_rgba, GL_ARB_robustness, GL_EXT_transform_feedback

32 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x021 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x022 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x08e 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x08f 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x090 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x091 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x092 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x093 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x094 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x095 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x096 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x097 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x098 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x099 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x09a 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x09b 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x09c 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x09d 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x09e 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x09f 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0a0 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0a1 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0a2 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0a3 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0a4 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0a5 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0a6 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0a7 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0a8 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0a9 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0aa 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x05d 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None

48 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x05e  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x05f  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x060  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x061  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x062  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x063  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x064 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x065 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x066 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x067 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x068 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x069 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x06a 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x06b 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x06c 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x06d 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x06e 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x06f 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x070  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x071  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x072 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x073 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x074 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x075 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x076  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x077  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x078  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x079  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x07a  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x07b  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x07c 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x07d 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x07e 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x07f 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x080 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x081 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x082 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x083 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x084 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x085 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x086 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x087 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x088  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x089  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x08a 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x08b 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x08c 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x08d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow


---

### Post by mahiyabz on 2012-09-13
bumblebee bugreport is attached

---

### Post by pogopuschel on 2012-09-14
Your logfiles are ok. The Intel GPU seems to run accelerated, and your Nvidia GPU should work also.
```
glxspheres
```
should give around 30 FPS on Intel
```
optirun glxspheres 
```
should give about 100 FPS on Nvidia

Can you specify the 3D problems?

---

### Post by mahiyabz on 2012-09-14
yes Intel works with 29/30 fps, but Nvidia it goes to 2/5 fps :S

2nd HDMI Out and VGA Out, both are dead (no response on plugin, not detected at all, and i have 22" Display to attach with), windows 7 is smooth 

i guess i have to wait for new release of linux to play with or virtual box over windows :(

---

### Post by jaras67 on 2012-09-27
jarek@inspiron:~$ glxspheres
Polygons in scene: 62464
Visual ID of window: 0x93
Context is Direct
OpenGL Renderer: Mesa DRI Intel(R) Sandybridge Mobile 
59.883305 frames/sec - 52.498495 Mpixels/sec
59.492121 frames/sec - 52.155552 Mpixels/sec
60.013325 frames/sec - 52.612482 Mpixels/sec
60.002795 frames/sec - 52.603251 Mpixels/sec
60.002334 frames/sec - 52.602846 Mpixels/sec
60.008684 frames/sec - 52.608413 Mpixels/sec
60.007776 frames/sec - 52.607617 Mpixels/sec
60.007982 frames/sec - 52.607797 Mpixels/sec
59.999735 frames/sec - 52.600568 Mpixels/sec
59.999306 frames/sec - 52.600192 Mpixels/sec
jarek@inspiron:~$ optirun glxspheres
Polygons in scene: 62464
Visual ID of window: 0x21
Context is Direct
OpenGL Renderer: GeForce GT 525M/PCI/SSE2
136.324001 frames/sec - 119.512525 Mpixels/sec
136.296999 frames/sec - 119.488853 Mpixels/sec
140.819137 frames/sec - 123.453321 Mpixels/sec
140.000953 frames/sec - 122.736036 Mpixels/sec
146.056204 frames/sec - 128.044553 Mpixels/sec
138.949562 frames/sec - 121.814302 Mpixels/sec
136.125568 frames/sec - 119.338563 Mpixels/sec
137.619883 frames/sec - 120.648599 Mpixels/sec
136.403997 frames/sec - 119.582656 Mpixels/sec


Ununtu 11.10 64bit

---

### Post by mahiyabz on 2012-09-27
Very Nice jaras67

am using 12.04, so should i try 11.10 ? are you using Bumblebee ? 

please advise.

---

### Post by leejkdnux on 2012-10-23
i have exactly same problem... 
bought new laptop/notebook Dell Inspiron N5110 15R few months ago, and i can't get nvidia to work on ANY linux!

that is somewhat bizarre considering Dell shipped nVidia GT 525M cards widely and in very large quantities, and Dell is one of most supportive linux companies (they even sell laptops with preinstalled ubuntu nowdays!)

anyway, i tried Ubuntu and various variants both custom and official, Mint, Fedora, openSUSE and pretty much everything, but sadly nVidia GT 525M DOESN'T WORK on ANY linux. it is always falsely detected as GT 540M model, and i think that's the problem. so you can't install drivers, it says they are already installed but they don't work. also you can't uninstall or reinstall drivers because they are not actually installed. no properitary drivers detected on sys - retarded, i know... that made me revert back to windows - and it works there quite flawlessly. but i want to use linux as my main OS! i was really hoping this would be fixed till 12.10 release, but NO... some update fix/patch would really be good now...

i don't know whose fault is this and whom to report - nVidia? Dell? Ubuntu? it's not an hardware issue...
and stop telling me that i should use bumblebee - new official nVidia drivers will support optimus anyway, but i don't even want optimus or intel drivers - i just want my nVidia GT 525M to work in linux!

---

### Post by mikewhatever on 2012-10-23
If you didn't want Optimus, you should not have bought a hybrid machine in the first place, ... but you have, and now, you must deal with Optimus, whether you want it or not.

There is no official support for it yet, and complaining here, the way you do, is not the best way to influence Nvidia.

---

### Post by leejkdnux on 2012-10-23
> **mikewhatever said:**
> If you didn't want Optimus, you should not have bought a hybrid machine in the first place, ... but you have, and now, you must deal with Optimus, whether you want it or not.

There is no official support for it yet, and complaining here, the way you do, is not the best way to influence Nvidia.
dude, i'm not saying that optimus is bad or something like that, i'm just saying that it's not priority.

this is not about support for optimus, this is about inability to use working official nVidia drivers because of false hardware detection!

all other modern nVidia cards support optimus as well, that's not the point. point is they actually work, and present drivers are good enough to make them work. this is just a specific problem with 525M model because for some reason linux detects it as 540M...

did you even read my previous post?

i'm not writing this to complain, but to find the solution and fix the problem, and make ubuntu even better OS in the process... you are the one who's complaining though. quite the irony... :)

btw speaking of influencing nVidia: [http://www.youtube.com/watch?v=iYWzMvlj2RQ](http://www.youtube.com/watch?v=iYWzMvlj2RQ)

---

### Post by leejkdnux on 2012-10-24
mikewhatever - please accept my sincerest apologies... ignorance spoke out of me when i said that i don't want bumblebee! it is the only current solution for this problem...

it's still not perfect, but it's better than nothing and best you can get at present.

for anyone having similar problems - please check this thread: [http://ubuntuforums.org/showthread.php?t=2075423](http://ubuntuforums.org/showthread.php?t=2075423)

it is all explained there!

thank you

---

