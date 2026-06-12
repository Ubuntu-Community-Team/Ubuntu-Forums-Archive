---
title: "OpenGL 2.1.8087 vs 2.1.7412, new buggy function introduced ?"
date: 2008-12-07
forum: Installation &amp; Upgrades
---

### Post by Browser_ice on 2008-12-07
On my PC, I have multi-boots where I use a Ubuntu 8.04 for office projects (involving OpenSim and SecondLife/Hippo) and a Ubuntu 8.10 for personnal usages. I have noticed that for the past 3-4 weeks I have a serious performance drop in my SL/Hippo no matter where I connect (either local grid on my own PC or grid's on the net). I did several investigations and found something different in my 8.04 GL setup compared to my 8.10. 

My 8.04 has OpenGL v 2.1.8087 and my 8.10, 2.1.7412. I see that 2.1.8087 has introduced something new : shading language version string: 1.20 and I remember seeing error messages in my SecondLife about shading languages.

Can someone tell me if release 2.1.8087 is complete or that it has pending bugs/fixes ?


Compare between the 2 Ubuntu on several hardware/GL checks:
> diff -iw 8.04-GL_info  8.10-GL_info
2,3c2,3
< name of display: :20.0
< display: :20  screen: 0
---
> name of display: :0.0
> display: :0  screen: 0
10,11c10,11
< name of display: :20.0
< display: :20  screen: 0
---
> name of display: :0.0
> display: :0  screen: 0
36,37c36
< OpenGL version string: 2.1.8087 Release
<** OpenGL shading language version string: 1.20**
---
> OpenGL version string: 2.1.7412 Release
40,42c39,40
<     GL_ARB_fragment_program, GL_ARB_fragment_shader, GL_ARB_half_float_pixel,
<     GL_ARB_half_float_vertex, GL_ARB_multisample, GL_ARB_multitexture,
<     GL_ARB_occlusion_query, GL_ARB_pixel_buffer_object,
---
>     GL_ARB_fragment_program, GL_ARB_fragment_shader, GL_ARB_multisample, 
>     GL_ARB_multitexture, GL_ARB_occlusion_query, GL_ARB_pixel_buffer_object, 
49,55c47,52
<     GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two,
<     GL_ARB_texture_rectangle, GL_ARB_transpose_matrix,
<     GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader,
<     GL_ARB_window_pos, GL_ATI_draw_buffers, GL_ATI_envmap_bumpmap,
<     GL_ATI_fragment_shader, GL_ATI_meminfo, GL_ATI_separate_stencil,
<     GL_ATI_texture_env_combine3, GL_ATI_texture_float, GL_EXT_abgr,
<     GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_equation_separate,
---
>     GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle, 
>     GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
>     GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos, 
>     GL_ATI_draw_buffers, GL_ATI_envmap_bumpmap, GL_ATI_fragment_shader, 
>     GL_ATI_meminfo, GL_ATI_separate_stencil, GL_ATI_texture_env_combine3, 
>     GL_ATI_texture_float, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
58,59c55
<     GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_blit,
<     GL_EXT_framebuffer_multisample, GL_EXT_framebuffer_object,
---
>     GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_object, 
101c97
<        **capabilities: bus_master cap_list**
---
>        capabilities: vga_controller bus_master cap_list

> glxinfo | grep -3 direct
name of display: :20.0
display: :20  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:

glxinfo
name of display: :20.0
display: :20  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory,
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method,
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control,
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group,
    GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI RADEON 9600 Series
**OpenGL version string: 2.1.8087 Release**
OpenGL shading language version string: 1.20
OpenGL extensions:
    GL_AMD_performance_monitor, GL_ARB_depth_texture, GL_ARB_draw_buffers,
    GL_ARB_fragment_program, GL_ARB_fragment_shader, GL_ARB_half_float_pixel,
    GL_ARB_half_float_vertex, GL_ARB_multisample, GL_ARB_multitexture,
    GL_ARB_occlusion_query, GL_ARB_pixel_buffer_object,
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shader_objects,
    GL_ARB_shading_language_100, GL_ARB_shadow, GL_ARB_shadow_ambient,
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar,
    GL_ARB_texture_env_dot3, GL_ARB_texture_float,
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two,
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix,
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader,
    GL_ARB_window_pos, GL_ATI_draw_buffers, GL_ATI_envmap_bumpmap,
    GL_ATI_fragment_shader, GL_ATI_meminfo, GL_ATI_separate_stencil,
    GL_ATI_texture_env_combine3, GL_ATI_texture_float, GL_EXT_abgr,
    GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_equation_separate,
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract,
    GL_EXT_compiled_vertex_array, GL_EXT_copy_texture,
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_blit,
    GL_EXT_framebuffer_multisample, GL_EXT_framebuffer_object,
    GL_EXT_gpu_program_parameters, GL_EXT_multi_draw_arrays,
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels,
    GL_EXT_point_parameters, GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap,
    GL_EXT_subtexture, GL_EXT_texgen_reflection, GL_EXT_texture3D,
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map,
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias,
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object,
    GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, GL_EXT_vertex_array,
    GL_KTX_buffer_region, GL_NV_blend_square, GL_NV_texgen_reflection,
    GL_SGIS_generate_mipmap, GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod,
    GL_WIN_swap_hint, WGL_EXT_swap_control

lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8235 PCI Bridge
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AR [Radeon 9600]
01:00.1 Display controller: ATI Technologies Inc RV350 AR [Radeon 9600] (Secondary)


lshw -C video
WARNING: you should run this program as super-user.
  *-display:0             
       description: VGA compatible controller
       product: RV350 AR [Radeon 9600]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: driver=fglrx_pci latency=255 mingnt=8 module=fglrx
  *-display:1 UNCLAIMED
       description: Display controller
       product: RV350 AR [Radeon 9600] (Secondary)
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: latency=32 mingnt=8


By the way, I do not use any Desktop effects. They are disabled.

---

### Post by Browser_ice on 2008-12-07
I found a thread where someone reported a GL problem and someone suggested [using a debug functionality of Gl]("http://ubuntuforums.org/showthread.php?t=905292&highlight=performance+shading+language").

I tried it and the glxinfo changed. On my 8.04 it is not reporting OpenGl to be release 2.1.7412 instead.  I will reboot, check to see if it changed and test my software to see if anything improved.

> >$ export LIBGL_DEBUG=verbose
>$ glxinfo
name of display: :0.0
libGL: XF86DRIGetClientDriverName: 8.47.3 fglrx (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/fglrx_dri.so
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 5, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 5, (OK)
drmOpenByBusid: drmOpenMinor returns 5
drmOpenByBusid: drmGetBusid reports PCI:1:0:0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, 
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI RADEON 9600 Series
OpenGL version string: 2.1.7412 Release
OpenGL extensions:
    GL_AMD_performance_monitor, GL_ARB_depth_texture, GL_ARB_draw_buffers, 
    GL_ARB_fragment_program, GL_ARB_fragment_shader, GL_ARB_multisample, 
    GL_ARB_multitexture, GL_ARB_occlusion_query, GL_ARB_pixel_buffer_object, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shader_objects, 
    GL_ARB_shading_language_100, GL_ARB_shadow, GL_ARB_shadow_ambient, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_float, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos, 
    GL_ATI_draw_buffers, GL_ATI_envmap_bumpmap, GL_ATI_fragment_shader, 
    GL_ATI_meminfo, GL_ATI_separate_stencil, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_float, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_compiled_vertex_array, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_object, 
    GL_EXT_gpu_program_parameters, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels, 
    GL_EXT_point_parameters, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texgen_reflection, GL_EXT_texture3D, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, GL_EXT_vertex_array, 
    GL_KTX_buffer_region, GL_NV_blend_square, GL_NV_texgen_reflection, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, 
    GL_WIN_swap_hint, WGL_EXT_swap_control

---

### Post by Browser_ice on 2008-12-07
Upon reboot, the GLxinfo still said I had 2.1.7412. So this solved the GL version problem.

But now, when I restarted my SL/Hippo, in a windowed mode, it showed the problem was fixed. But as soon as I went into fullscreen, I went back to graphic and performance problems. Glxinfo still is 2.1.7412.

So I now have to investigate something else.

---

