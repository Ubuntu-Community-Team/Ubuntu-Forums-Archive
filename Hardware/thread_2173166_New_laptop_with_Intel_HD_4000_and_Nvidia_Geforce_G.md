---
title: "New laptop with Intel HD 4000 and Nvidia Geforce GT 630M driver question"
date: 2013-09-08
forum: Hardware
---

### Post by jaime3 on 2013-09-08
Hello guy's I just got a HP Envy dv7 with Intel HD 4000 and Nvidia Geforce GT 630M 2gb. Anyway's my question do I upgrade the Intel drivers? I'm runing Ubuntu 13.04. I got Nvidia installed though. I do run VMware and would like to use Intel for low end game and Nvidia on high end games. I'm not to experience with with these optimus stuff. TY

---

### Post by carl4926 on 2013-09-08
You need to use Bumblebee
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

---

### Post by jaime3 on 2013-09-08
> **carl4926 said:**
> You need to use Bumblebee
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)


Yes I know it just a program to switch to Nvida GPU when needed which my Nvidia driver i up to date I suppose. How about Intel is it fine using opensource stock driver from ubuntu 13.04 can I get more performance from Intel?

---

### Post by grahammechanical on 2013-09-08
I would not suppose that your Nvidia driver is switching between the Nvidia graphic adapter and the Intel graphica adapter if I was you. Nvidia only started working on a Linux driver to do this a few months ago. Read this tutorial

[http://www.linux.org/threads/nvidia-optimus-on-linux.4415/](http://www.linux.org/threads/nvidia-optimus-on-linux.4415/)

Did you see this?

> So why do many Linux users not like the idea of Nvidia Optimus? Because  Nvidia has not released a driver for Linux that provides native Optimus  support. Hence the need for this tutorial.

This two links will bring you up to date.

[http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html](http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html)

[http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html](http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html)

You may need to wait until 13.10 is released and then upgrade if you want to benefit in any way from using Bumblebee or the nvidia driver. I would also like to add that if you are using Ubuntu do not follow the tutorial in the first link. I provided it to show the current lack of support for Nvidia Optimus in Linux due to Nvidia not providing support. Follow the advice in either of the 2 webupd8 links.

Regards.

---

### Post by Linuxisfast on 2013-09-09
The latest Ubuntu 12.04.3 as well as Ubuntu 13.10 have Optimus support right out of the box with nvidia 319 drivers and nvidia prime package. However you can't use bublebee simultaneously with nvidia prime.

---

### Post by jaime3 on 2013-09-09
> **Linuxisfast said:**
> The latest Ubuntu 12.04.3 as well as Ubuntu 13.10 have Optimus support right out of the box with nvidia 319 drivers and nvidia prime package. However you can't use bublebee simultaneously with nvidia prime.

Support yes but I installed driver by Additional Drivers I did not had driver just open sorce installed. But my question is easy the intel driver I haven't upgrade am I good or can I get more performance by adding intel driver from website? My Nvidia is update and I have bumbleebee which works some games some I can't go to higher resolution. Another question can I have my Nvidia to run as main graphic card instead using the HD 4000? Like can it boot up and use Nvidia throughout on every application?

---

### Post by Yellow Pasque on 2013-09-09
Installing the nvidia driver directly (through Additional Drivers) often borks the intel driver, so make sure that's okay:
```
glxinfo
```

If you want to run the latest and greatest intel drivers, try out the xorg-edgers PPA [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)
If you don't like the result, it's easy to remove the ppa using ppa-purge.

---

### Post by Linuxisfast on 2013-09-10
> **jaime3 said:**
> Support yes but I installed driver by Additional Drivers I did not had driver just open sorce installed. But my question is easy the intel driver I haven't upgrade am I good or can I get more performance by adding intel driver from website? My Nvidia is update and I have bumbleebee which works some games some I can't go to higher resolution. Another question can I have my Nvidia to run as main graphic card instead using the HD 4000? Like can it boot up and use Nvidia throughout on every application?


If you want the 12.04.3 method, Bumblebee is out and nvidia prime does the work. The FPS is far better and the power use and heat is not that significantly up. This way the Nvidia is your main card with some work offloaded to Intel. I have the latest Intel drivers as well via Glassen PPA. Works very well. If you wish to do that take a look at the Ubuntu X Hybrid Wiki. [https://wiki.ubuntu.com/X/HybridGraphics](https://wiki.ubuntu.com/X/HybridGraphics) Make sure to remove the nvida drivers and bumblebee with a --purge command. Then install via the Wiki.

---

### Post by jaime3 on 2013-09-10
> **Temüjin said:**
> Installing the nvidia driver directly (through Additional Drivers) often borks the intel driver, so make sure that's okay:
```
glxinfo
```

If you want to run the latest and greatest intel drivers, try out the xorg-edgers PPA [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)
If you don't like the result, it's easy to remove the ppa using ppa-purge.

name of display: :0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_multisample, GLX_EXT_create_context_es2_profile, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, GLX_OML_swap_method, 
    GLX_SGI_swap_control, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, GLX_INTEL_swap_event
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_create_context_robustness, GLX_ARB_framebuffer_sRGB, 
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
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_create_context_es2_profile, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_swap_control, 
    GLX_OML_swap_method, GLX_OML_sync_control, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap, GLX_INTEL_swap_event
OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Ivybridge Mobile 
OpenGL version string: 3.0 Mesa 9.1.4
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
    GL_NV_texgen_reflection, GL_NV_texture_env_combine4, GL_S3_s3tc, 
    GL_SUN_multi_draw_arrays, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_EXT_framebuffer_object, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_MESA_window_pos, GL_NV_packed_depth_stencil, 
    GL_NV_texture_rectangle, GL_ARB_depth_texture, GL_ARB_occlusion_query, 
    GL_ARB_shadow, GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_window_pos, GL_ATI_envmap_bumpmap, GL_EXT_stencil_two_side, 
    GL_EXT_texture_cube_map, GL_NV_depth_clamp, GL_APPLE_packed_pixels, 
    GL_APPLE_vertex_array_object, GL_ARB_draw_buffers, 
    GL_ARB_fragment_program, GL_ARB_fragment_shader, GL_ARB_shader_objects, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ATI_draw_buffers, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_float, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_wrap, GL_MESA_pack_invert, GL_MESA_ycbcr_texture, 
    GL_NV_primitive_restart, GL_ARB_depth_clamp, 
    GL_ARB_fragment_program_shadow, GL_ARB_half_float_pixel, 
    GL_ARB_occlusion_query2, GL_ARB_point_sprite, GL_ARB_shading_language_100, 
    GL_ARB_sync, GL_ARB_texture_non_power_of_two, GL_ARB_vertex_buffer_object, 
    GL_ATI_blend_equation_separate, GL_EXT_blend_equation_separate, 
    GL_OES_read_format, GL_ARB_color_buffer_float, GL_ARB_pixel_buffer_object, 
    GL_ARB_texture_compression_rgtc, GL_ARB_texture_float, 
    GL_ARB_texture_rectangle, GL_EXT_packed_float, GL_EXT_pixel_buffer_object, 
    GL_EXT_texture_compression_dxt1, GL_EXT_texture_compression_rgtc, 
    GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, 
    GL_EXT_texture_shared_exponent, GL_ARB_framebuffer_object, 
    GL_EXT_framebuffer_blit, GL_EXT_framebuffer_multisample, 
    GL_EXT_packed_depth_stencil, GL_APPLE_object_purgeable, 
    GL_ARB_vertex_array_object, GL_ATI_separate_stencil, GL_EXT_draw_buffers2, 
    GL_EXT_draw_instanced, GL_EXT_gpu_program_parameters, 
    GL_EXT_texture_array, GL_EXT_texture_integer, GL_EXT_texture_sRGB_decode, 
    GL_EXT_timer_query, GL_OES_EGL_image, GL_MESA_texture_array, 
    GL_ARB_copy_buffer, GL_ARB_depth_buffer_float, GL_ARB_draw_instanced, 
    GL_ARB_half_float_vertex, GL_ARB_instanced_arrays, 
    GL_ARB_map_buffer_range, GL_ARB_texture_rg, GL_ARB_texture_swizzle, 
    GL_ARB_vertex_array_bgra, GL_EXT_separate_shader_objects, 
    GL_EXT_texture_swizzle, GL_EXT_vertex_array_bgra, 
    GL_NV_conditional_render, GL_AMD_draw_buffers_blend, 
    GL_ARB_ES2_compatibility, GL_ARB_blend_func_extended, GL_ARB_debug_output, 
    GL_ARB_draw_buffers_blend, GL_ARB_draw_elements_base_vertex, 
    GL_ARB_explicit_attrib_location, GL_ARB_fragment_coord_conventions, 
    GL_ARB_provoking_vertex, GL_ARB_sampler_objects, GL_ARB_seamless_cube_map, 
    GL_ARB_shader_texture_lod, GL_ARB_texture_cube_map_array, 
    GL_ARB_texture_rgb10_a2ui, GL_ARB_uniform_buffer_object, 
    GL_ARB_vertex_type_2_10_10_10_rev, GL_EXT_provoking_vertex, 
    GL_EXT_texture_snorm, GL_MESA_texture_signed_rgba, 
    GL_ARB_get_program_binary, GL_ARB_robustness, GL_ARB_shader_bit_encoding, 
    GL_ARB_timer_query, GL_ANGLE_texture_compression_dxt3, 
    GL_ANGLE_texture_compression_dxt5, GL_ARB_internalformat_query, 
    GL_ARB_shading_language_packing, GL_ARB_texture_storage, 
    GL_EXT_transform_feedback, GL_ARB_ES3_compatibility, 
    GL_ARB_invalidate_subdata


20 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x020 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x021 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x099 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x09a 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x09b 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x09c 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x09d 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x09e 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  8 1 None
0x09f 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x0a0 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x0a1 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0a2 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0a3 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0a4 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0a5 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x0a6 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x0a7 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  8 1 None
0x0a8 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x0a9 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x06c 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None


44 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x06d  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x06e  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x06f  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x070  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x071  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x072  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x073 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x074 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x075 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x076 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x077  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x078  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x079 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x07a 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x07b  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  4 1 None
0x07c  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  8 1 None
0x07d  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  4 1 None
0x07e  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  8 1 None
0x07f 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x080 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  8 1 None
0x081 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x082 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x083  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x084  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x085  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x086  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x087  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x088  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x089 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x08a 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x08b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x08c 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x08d  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x08e  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x08f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x090 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x091  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  4 1 None
0x092  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  8 1 None
0x093  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  4 1 None
0x094  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  8 1 None
0x095 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x096 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  8 1 None
0x097 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x098 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None

---

### Post by jaime3 on 2013-09-10
sudo optirun glxinfo
[sudo] password for james: 
name of display: :0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: VirtualGL
server glx version string: 1.4
server glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_SGI_make_current_read, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SUN_get_transparent_index, GLX_ARB_create_context, 
    GLX_ARB_create_context_profile
client glx vendor string: VirtualGL
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_SGI_make_current_read, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SUN_get_transparent_index, GLX_ARB_create_context, 
    GLX_ARB_create_context_profile
GLX version: 1.4
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_SGI_make_current_read, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SUN_get_transparent_index, GLX_ARB_create_context, 
    GLX_ARB_create_context_profile
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce GT 630M/PCIe/SSE2
OpenGL version string: 4.3.0 NVIDIA 313.30
OpenGL shading language version string: 4.30 NVIDIA via Cg compiler
OpenGL extensions:
    GL_AMD_multi_draw_indirect, GL_ARB_arrays_of_arrays, GL_ARB_base_instance, 
    GL_ARB_blend_func_extended, GL_ARB_clear_buffer_object, 
    GL_ARB_color_buffer_float, GL_ARB_compatibility, 
    GL_ARB_compressed_texture_pixel_storage, GL_ARB_conservative_depth, 
    GL_ARB_compute_shader, GL_ARB_copy_buffer, GL_ARB_copy_image, 
    GL_ARB_debug_output, GL_ARB_depth_buffer_float, GL_ARB_depth_clamp, 
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_draw_buffers_blend, 
    GL_ARB_draw_indirect, GL_ARB_draw_elements_base_vertex, 
    GL_ARB_draw_instanced, GL_ARB_ES2_compatibility, GL_ARB_ES3_compatibility, 
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
    GL_ATI_texture_mirror_once, GL_S3_s3tc, GL_EXT_texture_env_add, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_bindable_uniform, GL_EXT_blend_color, 
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
    GL_EXT_separate_specular_color, GL_EXT_shader_image_load_store, 
    GL_EXT_shadow_funcs, GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, 
    GL_EXT_texture3D, GL_EXT_texture_array, GL_EXT_texture_buffer_object, 
    GL_EXT_texture_compression_dxt1, GL_EXT_texture_compression_latc, 
    GL_EXT_texture_compression_rgtc, GL_EXT_texture_compression_s3tc, 
    GL_EXT_texture_cube_map, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_integer, 
    GL_EXT_texture_lod, GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_shared_exponent, 
    GL_EXT_texture_sRGB, GL_EXT_texture_sRGB_decode, GL_EXT_texture_storage, 
    GL_EXT_texture_swizzle, GL_EXT_timer_query, GL_EXT_transform_feedback2, 
    GL_EXT_vertex_array, GL_EXT_vertex_array_bgra, GL_EXT_vertex_attrib_64bit, 
    GL_EXT_x11_sync_object, GL_EXT_import_sync_object, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_KHR_debug, GL_KTX_buffer_region, 
    GL_NV_blend_square, GL_NV_compute_program5, GL_NV_conditional_render, 
    GL_NV_copy_depth_to_color, GL_NV_copy_image, GL_NV_depth_buffer_float, 
    GL_NV_depth_clamp, GL_NV_draw_texture, GL_NV_ES1_1_compatibility, 
    GL_NV_explicit_multisample, GL_NV_fence, GL_NV_float_buffer, 
    GL_NV_fog_distance, GL_NV_fragment_program, GL_NV_fragment_program_option, 
    GL_NV_fragment_program2, GL_NV_framebuffer_multisample_coverage, 
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
    GL_NV_vertex_program2_option, GL_NV_vertex_program3, 
    GL_NVX_conditional_render, GL_NVX_gpu_memory_info, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SGIX_shadow, GL_SUN_slice_accum


10 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x020 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x099 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x09a 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x09b 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x09c 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x09d 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x09e 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x09f 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x0a0 24 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None
0x06c 32 tc  0  32  0 r  y .   8  8  8  0 .  .  4 24  0 16 16 16 16  0 0 None


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

---

### Post by jaime3 on 2013-09-10
Is both video card installed correctly?

---

### Post by Linuxisfast on 2013-09-10
In my case yes, both are installed and xrandr --listproviders list both cards functioning.

---

### Post by Yellow Pasque on 2013-09-10
Yes, the output looks good, so no changes are necessary. Like I said, if you're the kind of person that subscribes to the "latest and greatest" theory, try xorg-edgers PPA.

---

