---
title: "Nvidia 1.0 7174 Question"
date: 2005-07-15
forum: Hardware &amp; Laptops
---

### Post by Tad030 on 2005-07-15
First off, an apology for another video card thread.  I'm tired, I'm frustrated, and have spent a lot of time searching this forum for an answer to my question.

So, here is my problem.  My nvidia video card has installed just fine, the logo appears when the computer boots, but glxgears runs very slow, and I'm not sure what the best fix to my problem is. 

Here is my output:

1345 frames in 5.0 seconds = 269.000 FPS
1418 frames in 5.0 seconds = 283.600 FPS


Any suggestions?

---

### Post by geearf on 2005-07-15
Hello,

what graphic card do you have ?
and what proc / motherboard with it ?

---

### Post by Tad030 on 2005-07-15
[QUOTE=geearf]Hello,

what graphic card do you have ?
and what proc / motherboard with it ?[/QUOTE]

Yes, I suppse that would be helpful.  Here is what I have:

Graphics = RIVA TNT2 Model 64 Pro
Processor= AMD Ath XP 1600
Motherboard= Microstar MS 6330

---

### Post by geearf on 2005-07-15
Well your graphic card is really an old and slow one.
I don't know how good it should perform though.

Try looking on the net the usual score for it if you can.

---

### Post by Tad030 on 2005-07-15
Thanks for the help.  I feared that my card was not powerful enough to handle 3d games in linux.  I haven't been able to find normal scores on the net however, but I'll keep looking. 

Thanks again.   :)

---

### Post by kleeman on 2005-07-15
What does
 glxinfo 

give?

---

### Post by Tad030 on 2005-07-15
[QUOTE=kleeman]What does
 glxinfo 

give?[/QUOTE]

glxinfo gives the following:

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.3
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control
client glx vendor string: NVIDIA Corporation
client glx version string: 1.3
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info,
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync,
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer,
    GLX_SGI_swap_control, GLX_NV_float_buffer
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control,
    GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: RIVA TNT2/AGP/SSE/3DNOW!
OpenGL version string: 1.5.3 NVIDIA 71.74
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_point_parameters,
    GL_ARB_texture_env_add, GL_ARB_texture_mirrored_repeat,
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, GL_ARB_window_pos,
    GL_EXT_texture_env_add, GL_EXT_abgr, GL_EXT_bgra,
    GL_EXT_compiled_vertex_array, GL_EXT_draw_range_elements,
    GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels,
    GL_EXT_pixel_buffer_object, GL_EXT_point_parameters,
    GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap,
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine,
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_vertex_array,
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat,
    GL_KTX_buffer_region, GL_NV_blend_square, GL_NV_fog_distance,
    GL_NV_light_max_exponent, GL_NV_packed_depth_stencil,
    GL_NV_texgen_reflection, GL_NV_texture_env_combine4, GL_SGIS_multitexture,
    GL_SUN_slice_accum
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x2a 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x2b 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x2e 24 dc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x2f 24 dc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None

---

### Post by kleeman on 2005-07-15
Well the fact you have 

direct rendering: Yes

suggests 3d acceleration is on...

---

### Post by Tad030 on 2005-07-15
I know it's on, I was just wondering why my glxgears output was low - I assumed it was because my video card is old, but I thought maybe there was a way I could tweak it.   Maybe I'll just have to break down and buy a new card.

---

