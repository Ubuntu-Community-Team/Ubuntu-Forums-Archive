---
title: "Very low 3D performance with Intel Graphics Card"
date: 2008-06-01
forum: Hardware
---

### Post by vanadium on 2008-06-01
Open Source 3D games such as Neverball and Tuxracer run extre,ely choppy on my Pentium III desktop. I am sure this is an Ubuntu related problem: tuxracer ran perfectly on the same computer under Windows ME and two years ago under Mandrake Linux 9. My graphics card is

```

~$ lspci | grep Graphics
00:02.0 VGA compatible controller: Intel Corporation 82815 Chipset Graphics Controller (CGC) (rev 02)

```

glxgears suggests 3D should be fine:

```

$ glxgears -info
GL_RENDERER   = Mesa DRI i815 20050821 x86/MMX/SSE
GL_VERSION    = 1.2 Mesa 7.0.3-rc2
GL_VENDOR     = Keith Whitwell
GL_EXTENSIONS = GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_texture_compression GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_compiled_vertex_array GL_EXT_convolution GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_histogram GL_EXT_packed_pixels GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_separate_specular_color GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_APPLE_packed_pixels GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_MESA_ycbcr_texture GL_MESA_window_pos GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texture_rectangle GL_NV_texgen_reflection GL_OES_read_format GL_SGI_color_matrix GL_SGI_color_table GL_SGIS_generate_mipmap GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod
1574 frames in 5.0 seconds = 314.572 FPS
1589 frames in 5.0 seconds = 317.693 FPS
1585 frames in 5.0 seconds = 316.930 FPS


```

However, running ppracer gives:

```

~$ ppracer
PPRacer 0.3.1 --  http://racer.planetpenguin.de 
(c) 2004-2005 The PPRacer team
(c) 1999-2001 Jasmin F. Patry<jfpatry@sunspirestudios.com>
PPRacer comes with ABSOLUTELY NO WARRANTY. This is free software,
and you are welcome to redistribute it under certain conditions.
See http://www.gnu.org/copyleft/gpl.html for details.

[driAllocateTexture:636] unable to allocate texture
[driAllocateTexture:636] unable to allocate texture
[driAllocateTexture:636] unable to allocate texture
....

```

What could be wrong?

---

### Post by TheMemphisExperience on 2008-06-01
You could try running the windows version of the games through Wine. Aside from that, I don't know enough about Ubuntu or Tuxracer to tell you what to open up and what line to change.

---

### Post by vanadium on 2008-06-01
I tried this already (in a dispaired attempt). It blocked the system.

---

