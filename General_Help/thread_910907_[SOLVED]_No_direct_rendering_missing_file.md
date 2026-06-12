---
title: "[SOLVED] No direct rendering: missing file"
date: 2008-09-05
forum: General Help
---

### Post by _sluimers_ on 2008-09-05
I've switched from unichrome to openchrome and now do not have direct rendering because it's still looking for an old unichrome file, how do I fix this?

```

rogier@dhcppc3:~$ glxinfo | grep render
/usr/lib/dri/unichrome_dri.so: cannot open shared object file: No such file or directory
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect

```

---

### Post by Crafty Kisses on 2008-09-05
> **_sluimers_ said:**
> I've switched from unichrome to openchrome and now do not have direct rendering because it's still looking for an old unichrome file, how do I fix this?

```

rogier@dhcppc3:~$ glxinfo | grep render
/usr/lib/dri/unichrome_dri.so: cannot open shared object file: No such file or directory
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect

```
I'd also like to see the following output of:
```
glxinfo
```

---

### Post by _sluimers_ on 2008-09-05
```

rogier@dhcppc3:/etc/Wireless/RT2870STA$ glxinfo
name of display: :0.0
/usr/lib/dri/unichrome_dri.so: cannot open shared object file: No such file or directory
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
client glx vendor string: S3G
client glx version string: 1.4
client glx extensions:
    GLX_SGI_make_current_read,  GLX_SGIX_fbconfig,  GLX_SGIX_pbuffer, 
     GLX_ARB_get_proc_address, GLX_EXT_texture_from_pixmap, 
    GLX_MESA_copy_sub_buffer
GLX version: 1.2
GLX extensions:
    GLX_SGI_make_current_read, GLX_SGIX_fbconfig, GLX_EXT_texture_from_pixmap, 
    GLX_MESA_copy_sub_buffer
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)
OpenGL extensions:
    GL_EXT_texture_env_add, GL_ARB_multitexture, GL_ARB_transpose_matrix, 
    GL_ARB_texture_env_add, GL_ARB_texture_cube_map, 
    GL_ARB_texture_compression, GL_ARB_texture_border_clamp, 
    GL_ARB_point_parameters, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_depth_texture, GL_ARB_shadow, 
    GL_ARB_shadow_ambient, GL_ARB_window_pos, GL_ARB_occlusion_query, 
    GL_ARB_texture_non_power_of_two, GL_ARB_point_sprite, 
    GL_EXT_texture_rectangle, GL_EXT_abgr, GL_EXT_blend_color, 
    GL_EXT_texture3D, GL_EXT_packed_pixels, GL_SGIS_texture_lod, 
    GL_EXT_rescale_normal, GL_EXT_vertex_array, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_border_clamp, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_point_parameters, 
    GL_EXT_draw_range_elements, GL_EXT_bgra, GL_EXT_separate_specular_color, 
    GL_EXT_secondary_color, GL_EXT_multi_draw_arrays, GL_EXT_fog_coord, 
    GL_EXT_texture_env_combine, GL_EXT_blend_func_separate, 
    GL_EXT_stencil_wrap, GL_NV_texgen_reflection, GL_EXT_texture_lod_bias, 
    GL_NV_blend_square, GL_NV_texture_rectangle, GL_EXT_shadow_funcs, 
    GL_ATI_texture_env_combine3, GL_SGI_color_matrix, 
    GL_EXT_texture_edge_clamp

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x22 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x23 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None
0x26 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x27 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2a 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  0 16 16 16 16  0 0 None
0x2b 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  0 16 16 16 16  0 0 None
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 None
0x47 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None

```

---

### Post by Crafty Kisses on 2008-09-05
Do you have your video card drivers installed?

---

### Post by _sluimers_ on 2008-09-05
errrmmm... aren't unichrome and openchrome video card drivers?
So yes and it's part of the problem.

You see, I am trying to get a fanless mini-computer just good enough for my desktop. I have modest needs and I like computers small and quiet. I switched from an EPIA LN to an EPIA SN as my EPIA LN's graphics driver was not good enough for stepmania 3.9 (crashing after a few minutes of playing), the most modern game it needs to play. 
Thinking this is because I need a faster graphics chip, I bought the EPIA SN.
Unfortunately, openchrome's support of EPIA SN's graphics chip is still very poor, so switched to unichrome. I couldn't get rendering working there, so now I'm back again with the EPIA LN and openchrome and will wait until openchrome/mesa supports the EPIA SN.
I don't know how to uninstall those drivers, so I just simply installed openchrome and reinstalled mesa, drm and libdrm.

---

