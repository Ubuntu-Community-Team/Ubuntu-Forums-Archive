---
title: "S3 Savage4 (rev 02) Freeze on glxgears test"
date: 2012-01-05
forum: Hardware
---

### Post by Ismaw34 on 2012-01-05
Hello, recently i got to switch my video card to another more old.
After running about XFree86 thing, and installing all the extensions of xorg and xserver, i wanted to test the 3D acceleration, but it freezes.

Here is the glxinfo thing:
```
name of display: :0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_framebuffer_sRGB, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_multithread_makecurrent, 
    GLX_MESA_swap_control, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap, 
    GLX_INTEL_swap_event
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_MESA_multithread_makecurrent, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group
OpenGL vendor string: S3 Graphics Inc.
OpenGL renderer string: Mesa DRI Savage4 x86/MMX+/3DNow!+/SSE
OpenGL version string: 1.2 Mesa 7.11
OpenGL extensions:
    GL_ARB_multisample, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_copy_texture, GL_EXT_polygon_offset, GL_EXT_subtexture, 
    GL_EXT_texture_object, GL_EXT_vertex_array, GL_EXT_compiled_vertex_array, 
    GL_EXT_texture, GL_EXT_texture3D, GL_IBM_rasterpos_clip, 
    GL_EXT_draw_range_elements, GL_EXT_packed_pixels, GL_EXT_rescale_normal, 
    GL_EXT_separate_specular_color, GL_EXT_texture_edge_clamp, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, 
    GL_ARB_multitexture, GL_IBM_multimode_draw_arrays, 
    GL_IBM_texture_mirrored_repeat, GL_ARB_texture_env_add, 
    GL_ARB_transpose_matrix, GL_EXT_multi_draw_arrays, GL_EXT_secondary_color, 
    GL_EXT_texture_env_add, GL_EXT_texture_lod_bias, GL_NV_light_max_exponent, 
    GL_NV_texgen_reflection, GL_SUN_multi_draw_arrays, 
    GL_ARB_texture_compression, GL_MESA_window_pos, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_window_pos, GL_APPLE_packed_pixels, 
    GL_ARB_draw_buffers, GL_ATI_draw_buffers, GL_EXT_stencil_wrap, 
    GL_ARB_vertex_buffer_object, GL_OES_read_format, GL_ARB_copy_buffer, 
    GL_ARB_robustness

16 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x021 16 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x053 16 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x054 16 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x055 16 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x056 16 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  8  0  0  0  0  0 0 Slow
0x057 16 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  8 16 16 16  0  0 0 Slow
0x058 16 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  8  0  0  0  0  0 0 Slow
0x059 16 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  8 16 16 16  0  0 0 Slow
0x05a 16 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x05b 16 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x05c 16 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x05d 16 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x05e 16 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  8  0  0  0  0  0 0 Slow
0x05f 16 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  8 16 16 16  0  0 0 Slow
0x060 16 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  8  0  0  0  0  0 0 Slow
0x061 16 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  8 16 16 16  0  0 0 Slow

16 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x043 16 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x044 16 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x045 16 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x046 16 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x047 16 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  8  0  0  0  0  0 0 Slow
0x048 16 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  8 16 16 16  0  0 0 Slow
0x049 16 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  8  0  0  0  0  0 0 Slow
0x04a 16 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  8 16 16 16  0  0 0 Slow
0x04b 16 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x04c 16 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x04d 16 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x04e 16 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x04f 16 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  8  0  0  0  0  0 0 Slow
0x050 16 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  8 16 16 16  0  0 0 Slow
0x051 16 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  8  0  0  0  0  0 0 Slow
0x052 16 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  8 16 16 16  0  0 0 Slow

X Error of failed request:  BadDrawable (invalid Pixmap or Window parameter)
  Major opcode of failed request:  136 (XFree86-DRI)
  Minor opcode of failed request:  9 ()
  Resource id in failed request:  0x2200004
  Serial number of failed request:  44
  Current serial number in output stream:  44
```There is any way to fix it?
Thanks, Ismaw34

---

