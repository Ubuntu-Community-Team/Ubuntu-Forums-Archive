---
title: "How do i check my OpenGL?"
date: 2008-07-11
forum: Hardware
---

### Post by MasterNetra on 2008-07-11
Hi. I've tried following the tutorials on getting wow to work. But part the adds the use of OpenGL to the game cause many things to go missing and although its faster then without, I'm not sure what the problem is. So one solution I'm considering is either my OpenGL isn't really enabled or WoW needs some further configuration. So how do i check to see if OpenGL is being used? I know my video card supports it and can use it.

---

### Post by flakrat on 2008-07-11
I believe that OpenGL is provided as part of your video card driver, so you may want to check with Intel to see if there's anything specific you need to do in Linux to enable OpenGL.

You might also check the output of the glxinfo command, open a command shell and type:

glxinfo|more

On my laptop (with an nVidia card and driver properly installed) I get the following at the start of the command:

```

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4

```

Notice that direct rendering is enabled. I ran this on my workstation that has an ATI card with the drivers NOT properly installed (I'm using the default CentOS 5 kernel driver at the moment and not the ATI driver) and I get:

```

name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2

```

You can also run the glxgears command to get an FPS result. On my laptop (again driver properly installed) I get 3000 FPS, and on the desktop using the native kernel driver I get 920 FPS.

What does your system report on the "direct rendering" line?

---

### Post by MasterNetra on 2008-07-11
> **flakrat said:**
> I believe that OpenGL is provided as part of your video card driver, so you may want to check with Intel to see if there's anything specific you need to do in Linux to enable OpenGL.

You might also check the output of the glxinfo command, open a command shell and type:

glxinfo|more

On my laptop (with an nVidia card and driver properly installed) I get the following at the start of the command:

```

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4

```

Notice that direct rendering is enabled. I ran this on my workstation that has an ATI card with the drivers NOT properly installed (I'm using the default CentOS 5 kernel driver at the moment and not the ATI driver) and I get:

```

name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2

```

You can also run the glxgears command to get an FPS result. On my laptop (again driver properly installed) I get 3000 FPS, and on the desktop using the native kernel driver I get 920 FPS.

What does your system report on the "direct rendering" line?

This is what i get from the glxinfo:

[I]name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 965GM 4.1.3002
OpenGL version string: 1.4 Mesa 7.0.3-rc2
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program, GL_ARB_imaging, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_point_parameters, 
    GL_ARB_shadow, GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_blend_color, GL_EXT_blend_equation_separate, 
    GL_EXT_blend_func_separate, GL_EXT_blend_logic_op, GL_EXT_blend_minmax, 
    GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, GL_EXT_cull_vertex, 
    GL_EXT_compiled_vertex_array, GL_EXT_convolution, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_histogram, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array, 
    GL_3DFX_texture_compression_FXT1, GL_APPLE_client_storage, 
    GL_APPLE_packed_pixels, GL_ATI_blend_equation_separate, 
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, 
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_ycbcr_texture, 
    GL_MESA_window_pos, GL_NV_blend_square, GL_NV_light_max_exponent, 
    GL_NV_texture_rectangle, GL_NV_texgen_reflection, GL_OES_read_format, 
    GL_SGI_color_matrix, GL_SGI_color_table, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod, GL_SGIX_depth_texture, GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x55 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon
[/I]

For that gear thing these are the results:

[I]20486 frames in 5.0 seconds = 4097.154 FPS
151780 frames in 5.0 seconds = 30355.988 FPS
158298 frames in 5.0 seconds = 31659.594 FPS
157122 frames in 5.0 seconds = 31424.363 FPS
159388 frames in 5.0 seconds = 31877.473 FPS
157143 frames in 5.0 seconds = 31428.564 FPS
160617 frames in 5.0 seconds = 32123.395 FPS
143868 frames in 5.0 seconds = 28773.551 FPS
148811 frames in 5.0 seconds = 29762.189 FPS
118762 frames in 5.0 seconds = 23748.170 FPS
5425 frames in 5.0 seconds = 1084.799 FPS
85624 frames in 5.0 seconds = 17124.781 FPS
157138 frames in 5.0 seconds = 31427.432 FPS
163498 frames in 5.0 seconds = 32699.451 FPS
154402 frames in 5.0 seconds = 30880.289 FPS
168033 frames in 5.0 seconds = 33606.434 FPS
160382 frames in 5.0 seconds = 32076.223 FPS
132373 frames in 5.0 seconds = 26472.283 FPS
117533 frames in 5.0 seconds = 23506.582 FPS[/I]

Hope all that helps.

---

### Post by shwick on 2008-07-11
Try disabling compiz-fusion, if you have it running. Go to a terminal and type:

```
metacity --replace
```

you can re-run compiz with

```
compiz --replace
```

compiz doesn't play nice with apps that use opengl :(

---

### Post by MasterNetra on 2008-07-11
I'll keep that compiz fact in mind. I tryed it but nothing changed with WoW.

---

### Post by MasterNetra on 2008-07-11
*Bump* (UnResolved)

---

### Post by Daelyn on 2008-07-12
> **MasterNetra said:**
> Hi. I've tried following the tutorials on getting wow to work. But part the adds the use of OpenGL to the game cause many things to go missing and although its faster then without, I'm not sure what the problem is. So one solution I'm considering is either my OpenGL isn't really enabled or WoW needs some further configuration. So how do i check to see if OpenGL is being used? I know my video card supports it and can use it.

Hum.

Run ```
glxgears
``` and see what happens.

If you get spinning gears there, your DRI/OpenGL is all right. You need to reconfigure your wine install in that case.

---

### Post by laxmanb on 2008-07-12
Check whether you have **xorg-driver-fglrx** driver installed in Synaptic.

If not, install it. That might resolve your problem.

---

### Post by MasterNetra on 2008-07-12
Well come to find out I accidentally forgot that buffer option in wow's config file. But as to the driver would it really have a effect for a Mobile Intel?

NVM the driver crashes wow...

Nvm on that last sentence...I merely forgot to restart the system...but it didn't help or harm.

---

### Post by canoe529 on 2008-07-22
I have a Lenovo T61 with the same graphic adapter and output from glxinfo that you have. I've been messing around with OpenGL acceleration but it is still pretty slow. I haven't yet compiled and installed the Intel drivers, but I'm hoping that will do the trick. I may just be lazy and wait until the next release of Ubuntu, as well, to see if that gets DRI working nicely. 

You can find the intel drivers here, they will need to be compiled:
[http://www.intellinuxgraphics.org/index.html](http://www.intellinuxgraphics.org/index.html)

---

