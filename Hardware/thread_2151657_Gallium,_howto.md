---
title: "Gallium, howto?"
date: 2013-06-05
forum: Hardware
---

### Post by Ashboy on 2013-06-05
**EDIT: Things got really bollocksed up so I had to reinstall. If you read this thread for the first time, you might as well fast forward to post #13 on the second page of this thread.**

I'm running XUbuntu 13.04 and I'd like to try out this Gallium driver I've been reading about. I have an old Ati x1250 card and normally I get 10% performance at best (curse ATI 10x over for dropping its legacy driver). The problem is that I can't seem to find anything entry-level that explains me on how to install this. All I need is a simple set of instructions on how to set it up and how to revert if things don't work out the way I hope. 

Kind community, would that be within the realm of possibilities? I'm not completely stupid, just slightly dyslectic. On good days. :-?

---

### Post by grahammechanical on 2013-06-05
It is simple. It really is. I am not using Xubuntu. So my instructions may be no good for you. But in standard Ubuntu 13.04 I would open System Settings>Software & Updates and go to the Additional Drivers tab and activate the Nouveau open source video driver. Let it search for available drivers and then look for something like

Using X.Org X Org Server - Nouveau Display Driver from xserver-xorg-video-nouveau (open source)

Tick the button and click Apply Changes. You may need to log out and  Log in or reboot. Then Open the Details Utility and see what you see under Graphics.

Regards.

---

### Post by Ashboy on 2013-06-05
Thanks. Part of the problem is that with Google I get equally relevant hits spread across the last ten years. It's a little hard to tell what's what. :)

Anyway, testing it out now..

---

### Post by grahammechanical on 2013-06-05
I have just thought of something that I should have added.

If a reboot brings you to a desktop without any panels, just wallpaper, then right click the desktop and select Change Desktop Background. That will open System Settings and from there you can get to Additional drivers and revert back to the driver that you know works.

---

### Post by Ashboy on 2013-06-05
Thanks. So far I can't get beyond step one, because the additional drivers tab is empty and I can't select anything..

[IMG]http://i.imgur.com/gXoo218.png[/IMG]

---

### Post by Ashboy on 2013-06-05
> **grahammechanical said:**
> It is simple. It really is. I am not using Xubuntu. So my instructions may be no good for you. But in standard Ubuntu 13.04 I would open System Settings>Software & Updates and go to the Additional Drivers tab and activate the Nouveau open source video driver. Let it search for available drivers and then look for something like

Using X.Org X Org Server - Nouveau Display Driver from xserver-xorg-video-nouveau (open source)

Tick the button and click Apply Changes. You may need to log out and  Log in or reboot. Then Open the Details Utility and see what you see under Graphics.

Regards.

[http://nouveau.freedesktop.org/wiki/](http://nouveau.freedesktop.org/wiki/)

Another question.. from that page I'm really getting that nouveau is meant for Nvidia cards, not ATI cards. Are you sure I should be installing that? I thought this was going to get me Gallium somehow.

---

### Post by Yellow Pasque on 2013-06-05
> **Ashboy said:**
> I'm running XUbuntu 13.04 and I'd like to try out this Gallium driver I've been reading about.
It's installed by default, so you're probably running it at the moment...
```
sudo apt-get install mesa-utils
glxinfo
```

> nouveau is meant for Nvidia cards, not ATI cards. Are you sure I should be installing that?
It won't hurt to install nouveau (since it also uses open-source gallium), but yes, it's only for nvidia cards.

---

### Post by Ashboy on 2013-06-05
Ok, I still don't understand how this is supposed to help me, but I'll play along. The first command showed mesa was already there. I think. The second command.. well.. 

```
name of display: :0.0
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_multisample, GLX_EXT_create_context_es2_profile, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, GLX_OML_swap_method, 
    GLX_SGI_swap_control, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, GLX_INTEL_swap_event
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
OpenGL vendor string: X.Org R300 Project
OpenGL renderer string: Gallium 0.4 on ATI RS600
OpenGL version string: 1.4 (2.1 Mesa 9.1.1)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_fragment_program_shadow, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_occlusion_query, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_program, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_object, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_compression_dxt1, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array, 
    GL_APPLE_packed_pixels, GL_ATI_draw_buffers, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_ATIX_texture_env_combine3, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays

96 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x021 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x022 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0f2 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0f3 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x0f4 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0f5 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x0f6 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0f7 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x0f8 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x0f9 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x0fa 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x0fb 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x0fc 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x0fd 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x0fe 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x0ff 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x100 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x101 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x102 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x103 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x104 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x105 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x106 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x107 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x108 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x109 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x10a 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x10b 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x10c 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x10d 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x10e 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x10f 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x110 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x111 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x112 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x113 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x114 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x115 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x116 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x117 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x118 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x119 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x11a 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x11b 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x11c 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x11d 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x11e 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x11f 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x120 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x121 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x122 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x123 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x124 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x125 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x126 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x127 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x128 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x129 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x12a 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x12b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x12c 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x12d 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x12e 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x12f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x130 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x131 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x132 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x133 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x134 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x135 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x136 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x137 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x138 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x139 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x13a 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x13b 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x13c 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x13d 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x13e 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x13f 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x140 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x141 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x142 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x143 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x144 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x145 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x146 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x147 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x148 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x149 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x14a 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x14b 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x14c 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x14d 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x14e 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x061 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None

150 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x062 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x063 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x064 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x065 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x066 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x067 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x068 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x069 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x06a 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x06b 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x06c 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x06d 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x06e 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x06f 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x070 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x071 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x072 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x073 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x074 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x075 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x076 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x077 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x078 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x079 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x07a 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x07b 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x07c 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x07d 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x07e 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x07f 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x080 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x081 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x082 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x083 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x084 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x085 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x086 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x087 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x088 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x089 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x08a 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x08b 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x08c 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x08d 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x08e 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x08f 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x090 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x091 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x092  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x093  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x094  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x095  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x096  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x097  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x098  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x099  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x09a  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x09b  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x09c  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x09d  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x09e  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x09f  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0a0  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0a1  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0a2  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0a3  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0a4  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0a5  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0a6  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0a7  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0a8  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0a9  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0aa 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0ab 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x0ac 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0ad 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x0ae 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0af 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x0b0 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x0b1 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x0b2 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x0b3 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x0b4 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x0b5 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x0b6 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x0b7 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x0b8 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x0b9 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x0ba 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x0bb 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x0bc 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0bd 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x0be 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0bf 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x0c0 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0c1 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x0c2 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0c3 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0c4 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0c5 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0c6 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0c7 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0c8 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x0c9 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x0ca 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x0cb 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x0cc 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x0cd 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x0ce 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0cf 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0d0 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0d1 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0d2 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0d3 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0d4 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0d5 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0d6 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0d7 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0d8 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0d9 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0da  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0db  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0dc  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0dd  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0de  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0df  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0e0  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x0e1  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x0e2  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x0e3  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x0e4  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x0e5  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x0e6  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0e7  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0e8  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0e9  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0ea  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0eb  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0ec  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0ed  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0ee  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0ef  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0f0  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0f1  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0f1  0 tc  0 128  0    y .  32 32 32 32 .  .  0 24  0  0  0  0  0  0 0 None
0x0f1  0 tc  0 128  0    . .  32 32 32 32 .  .  0 24  0  0  0  0  0  0 0 None
0x0f1  0 tc  0  64  0    y .  16 16 16 16 .  .  0 24  0  0  0  0  0  0 0 None
0x0f1  0 tc  0  64  0    . .  16 16 16 16 .  .  0 24  0  0  0  0  0  0 0 None
0x0f1  0 tc  0  32  0    y .  11 11 10  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0f1  0 tc  0  32  0    . .  11 11 10  0 .  .  0 24  0  0  0  0  0  0 0 None

```

So, if I'm reading this right..  which I'm not..  it makes even less sense than before. If Gallium really already is active.. for it to run so incredibly poorly, its almost as though it isn't doing anything at all. Are you guys sure this Gallium driver is *actually* running? I need to run *very* old games at a resolution the size of a post stamp to get any performance out of them at all.

---

### Post by Ashboy on 2013-06-05
Does that have anything to do with this line?
```
direct rendering: No
```

I don't know about direct rendering, but indirect rendering sounds like a pretty bad deal.

---

### Post by Yellow Pasque on 2013-06-05
> **Ashboy said:**
> Ok, I still don't understand how this is supposed to help me.
It shows you that you are using gallium...
```
OpenGL renderer string: Gallium 0.4 on ATI RS600
```
It also shows that something is wrong with your setup (no direct rendering is very bad).
Post your /var/log/Xorg.0.log

---

### Post by Ashboy on 2013-06-05
Alright. Thanks for looking into this. :)

```
[    30.017] 
X.Org X Server 1.13.3
Release Date: 2013-03-07
[    30.017] X Protocol Version 11, Revision 0
[    30.017] Build Operating System: Linux 3.2.0-37-generic i686 Ubuntu
[    30.017] Current Operating System: Linux disarm 3.8.0-24-generic #35-Ubuntu SMP Fri May 31 14:09:33 UTC 2013 i686
[    30.017] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-24-generic root=UUID=700511a5-06c0-4b33-8e54-c7e514c23aac ro quiet splash vt.handoff=7
[    30.017] Build Date: 17 April 2013  10:42:56PM
[    30.017] xorg-server 2:1.13.3-0ubuntu6 (For technical support please see http://www.ubuntu.com/support) 
[    30.017] Current version of pixman: 0.28.2
[    30.017]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    30.017] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    30.017] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Jun  5 07:32:16 2013
[    30.055] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    30.055] (==) No Layout section.  Using the first Screen section.
[    30.055] (==) No screen section available. Using defaults.
[    30.055] (**) |-->Screen "Default Screen Section" (0)
[    30.055] (**) |   |-->Monitor "<default monitor>"
[    30.056] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    30.056] (==) Automatically adding devices
[    30.056] (==) Automatically enabling devices
[    30.056] (==) Automatically adding GPU devices
[    30.056] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    30.056]     Entry deleted from font path.
[    30.056] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    30.056] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    30.056] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    30.056] (II) Loader magic: 0xb775b6a0
[    30.056] (II) Module ABI versions:
[    30.056]     X.Org ANSI C Emulation: 0.4
[    30.056]     X.Org Video Driver: 13.1
[    30.056]     X.Org XInput driver : 18.0
[    30.056]     X.Org Server Extension : 7.0
[    30.057] (II) config/udev: Adding drm device (/dev/dri/card0)
[    30.059] (--) PCI:*(0:1:5:0) 1002:7942:1631:c20a rev 0, Mem @ 0xd0000000/268435456, 0xcfef0000/65536, I/O @ 0x00009000/256
[    30.059] (II) Open ACPI successful (/var/run/acpid.socket)
[    30.059] Initializing built-in extension Generic Event Extension
[    30.059] Initializing built-in extension SHAPE
[    30.059] Initializing built-in extension MIT-SHM
[    30.059] Initializing built-in extension XInputExtension
[    30.059] Initializing built-in extension XTEST
[    30.059] Initializing built-in extension BIG-REQUESTS
[    30.059] Initializing built-in extension SYNC
[    30.059] Initializing built-in extension XKEYBOARD
[    30.059] Initializing built-in extension XC-MISC
[    30.059] Initializing built-in extension SECURITY
[    30.059] Initializing built-in extension XINERAMA
[    30.059] Initializing built-in extension XFIXES
[    30.059] Initializing built-in extension RENDER
[    30.059] Initializing built-in extension RANDR
[    30.059] Initializing built-in extension COMPOSITE
[    30.059] Initializing built-in extension DAMAGE
[    30.059] Initializing built-in extension MIT-SCREEN-SAVER
[    30.059] Initializing built-in extension DOUBLE-BUFFER
[    30.059] Initializing built-in extension RECORD
[    30.059] Initializing built-in extension DPMS
[    30.059] Initializing built-in extension X-Resource
[    30.059] Initializing built-in extension XVideo
[    30.059] Initializing built-in extension XVideo-MotionCompensation
[    30.059] Initializing built-in extension SELinux
[    30.059] Initializing built-in extension XFree86-VidModeExtension
[    30.059] Initializing built-in extension XFree86-DGA
[    30.059] Initializing built-in extension XFree86-DRI
[    30.059] Initializing built-in extension DRI2
[    30.059] (II) LoadModule: "glx"
[    30.158] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    30.159] (II) Module glx: vendor="X.Org Foundation"
[    30.159]     compiled for 1.13.3, module version = 1.0.0
[    30.159]     ABI class: X.Org Server Extension, version 7.0
[    30.159] (==) AIGLX enabled
[    30.159] Loading extension GLX
[    30.159] (==) Matched fglrx as autoconfigured driver 0
[    30.159] (==) Matched ati as autoconfigured driver 1
[    30.159] (==) Matched fglrx as autoconfigured driver 2
[    30.159] (==) Matched ati as autoconfigured driver 3
[    30.159] (==) Matched vesa as autoconfigured driver 4
[    30.159] (==) Matched modesetting as autoconfigured driver 5
[    30.159] (==) Matched fbdev as autoconfigured driver 6
[    30.159] (==) Assigned the driver to the xf86ConfigLayout
[    30.159] (II) LoadModule: "fglrx"
[    30.240] (WW) Warning, couldn't open module fglrx
[    30.240] (II) UnloadModule: "fglrx"
[    30.240] (II) Unloading fglrx
[    30.240] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    30.240] (II) LoadModule: "ati"
[    30.240] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    30.241] (II) Module ati: vendor="X.Org Foundation"
[    30.241]     compiled for 1.13.3, module version = 7.1.0
[    30.241]     Module class: X.Org Video Driver
[    30.241]     ABI class: X.Org Video Driver, version 13.1
[    30.241] (II) LoadModule: "radeon"
[    30.241] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    30.326] (II) Module radeon: vendor="X.Org Foundation"
[    30.326]     compiled for 1.13.3, module version = 7.1.0
[    30.326]     Module class: X.Org Video Driver
[    30.326]     ABI class: X.Org Video Driver, version 13.1
[    30.326] (II) LoadModule: "vesa"
[    30.326] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    30.326] (II) Module vesa: vendor="X.Org Foundation"
[    30.326]     compiled for 1.12.99.902, module version = 2.3.2
[    30.326]     Module class: X.Org Video Driver
[    30.326]     ABI class: X.Org Video Driver, version 13.0
[    30.326] (II) LoadModule: "modesetting"
[    30.327] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    30.327] (II) Module modesetting: vendor="X.Org Foundation"
[    30.327]     compiled for 1.13.3, module version = 0.7.0
[    30.327]     Module class: X.Org Video Driver
[    30.327]     ABI class: X.Org Video Driver, version 13.1
[    30.327] (II) LoadModule: "fbdev"
[    30.327] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    30.327] (II) Module fbdev: vendor="X.Org Foundation"
[    30.327]     compiled for 1.12.99.902, module version = 0.4.3
[    30.327]     Module class: X.Org Video Driver
[    30.327]     ABI class: X.Org Video Driver, version 13.0
[    30.327] (==) Matched fglrx as autoconfigured driver 0
[    30.327] (==) Matched ati as autoconfigured driver 1
[    30.327] (==) Matched fglrx as autoconfigured driver 2
[    30.327] (==) Matched ati as autoconfigured driver 3
[    30.328] (==) Matched vesa as autoconfigured driver 4
[    30.328] (==) Matched modesetting as autoconfigured driver 5
[    30.328] (==) Matched fbdev as autoconfigured driver 6
[    30.328] (==) Assigned the driver to the xf86ConfigLayout
[    30.328] (II) LoadModule: "fglrx"
[    30.328] (WW) Warning, couldn't open module fglrx
[    30.328] (II) UnloadModule: "fglrx"
[    30.328] (II) Unloading fglrx
[    30.328] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    30.328] (II) LoadModule: "ati"
[    30.329] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    30.329] (II) Module ati: vendor="X.Org Foundation"
[    30.329]     compiled for 1.13.3, module version = 7.1.0
[    30.329]     Module class: X.Org Video Driver
[    30.329]     ABI class: X.Org Video Driver, version 13.1
[    30.329] (II) LoadModule: "vesa"
[    30.329] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    30.329] (II) Module vesa: vendor="X.Org Foundation"
[    30.329]     compiled for 1.12.99.902, module version = 2.3.2
[    30.329]     Module class: X.Org Video Driver
[    30.329]     ABI class: X.Org Video Driver, version 13.0
[    30.329] (II) UnloadModule: "vesa"
[    30.329] (II) Unloading vesa
[    30.329] (II) Failed to load module "vesa" (already loaded, 0)
[    30.329] (II) LoadModule: "modesetting"
[    30.330] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    30.330] (II) Module modesetting: vendor="X.Org Foundation"
[    30.330]     compiled for 1.13.3, module version = 0.7.0
[    30.330]     Module class: X.Org Video Driver
[    30.330]     ABI class: X.Org Video Driver, version 13.1
[    30.330] (II) UnloadModule: "modesetting"
[    30.330] (II) Unloading modesetting
[    30.330] (II) Failed to load module "modesetting" (already loaded, 0)
[    30.330] (II) LoadModule: "fbdev"
[    30.330] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    30.330] (II) Module fbdev: vendor="X.Org Foundation"
[    30.330]     compiled for 1.12.99.902, module version = 0.4.3
[    30.330]     Module class: X.Org Video Driver
[    30.330]     ABI class: X.Org Video Driver, version 13.0
[    30.330] (II) UnloadModule: "fbdev"
[    30.330] (II) Unloading fbdev
[    30.330] (II) Failed to load module "fbdev" (already loaded, 0)
[    30.330] (II) RADEON: Driver for ATI Radeon chipsets:
    ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
    ATI Radeon Mobility X300 (M24) 3152 (PCIE),
    ATI FireGL M24 GL 3154 (PCIE), ATI FireMV 2400 3155 (PCI),
    ATI Radeon X600 (RV380) 3E50 (PCIE),
    ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
    ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
    ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
    ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
    ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
    ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
    ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
    ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
    ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
    ATI Radeon 8500 AIW BB (AGP), ATI Radeon IGP320M (U1) 4336,
    ATI Radeon IGP330M/340M/350M (U2) 4337,
    ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
    ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
    ATI Radeon X800PRO (R420) JI (AGP),
    ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
    ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
    ATI Radeon Mobility 9800 (M18) JN (AGP),
    ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
    ATI Radeon X800 VE (R420) JT (AGP), ATI Radeon X850 (R480) (AGP),
    ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
    ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
    ATI Radeon Mobility M7 LW (AGP),
    ATI Mobility FireGL 7800 M7 LX (AGP),
    ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
    ATI FireGL Mobility 9000 (M9) Ld (AGP),
    ATI Radeon Mobility 9000 (M9) Lf (AGP),
    ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI FireMV 2400 PCI,
    ATI Radeon 9700 Pro ND (AGP), ATI Radeon 9700/9500Pro NE (AGP),
    ATI Radeon 9600TX NF (AGP), ATI FireGL X1 NG (AGP),
    ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
    ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
    ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
    ATI Radeon Mobility 9600 (M10) NQ (AGP),
    ATI Radeon Mobility 9600 (M11) NR (AGP),
    ATI Radeon Mobility 9600 (M10) NS (AGP),
    ATI FireGL Mobility T2 (M10) NT (AGP),
    ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
    ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
    ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
    ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
    ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
    ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
    ATI Radeon Mobility X300 (M22) 5460 (PCIE),
    ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
    ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
    ATI Radeon X800PRO (R423) UI (PCIE),
    ATI Radeon X800LE (R423) UJ (PCIE),
    ATI Radeon X800SE (R423) UK (PCIE),
    ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
    ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
    ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
    ATI FireGL unknown (R423) UR (PCIE),
    ATI FireGL unknown (R423) UT (PCIE),
    ATI Mobility FireGL V5000 (M26) (PCIE),
    ATI Mobility FireGL V5000 (M26) (PCIE),
    ATI Mobility Radeon X700 XL (M26) (PCIE),
    ATI Mobility Radeon X700 (M26) (PCIE),
    ATI Mobility Radeon X700 (M26) (PCIE),
    ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
    ATI Radeon Mobility 9100 IGP (U3) 5835,
    ATI Radeon XPRESS 200 5954 (PCIE),
    ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
    ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
    ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
    ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
    ATI Radeon XPRESS 200M 5975 (PCIE),
    ATI Radeon XPRESS 200 5A41 (PCIE),
    ATI Radeon XPRESS 200M 5A42 (PCIE),
    ATI Radeon XPRESS 200 5A61 (PCIE),
    ATI Radeon XPRESS 200M 5A62 (PCIE),
    ATI Radeon X300 (RV370) 5B60 (PCIE),
    ATI Radeon X600 (RV370) 5B62 (PCIE),
    ATI Radeon X550 (RV370) 5B63 (PCIE),
    ATI FireGL V3100 (RV370) 5B64 (PCIE),
    ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
    ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
    ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
    ATI Mobility Radeon X800 XT (M28) (PCIE),
    ATI Mobility FireGL V5100 (M28) (PCIE),
    ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
    ATI Radeon X850 XT PE (R480) (PCIE),
    ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
    ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
    ATI Radeon X850 XT (R480) (PCIE),
    ATI Radeon X800XT (R423) 5D57 (PCIE),
    ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
    ATI Radeon X700 PRO (RV410) (PCIE),
    ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
    ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
    ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
    ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
    ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
    ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
    ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
    ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
    ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
    ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
    ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
    ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
    ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
    ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
    ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
    ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
    ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
    ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
    ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
    ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
    ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
    ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
    ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
    ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
    ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
    ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
    ATI Mobility Radeon X1700, ATI Radeon X2300HD,
    ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
    ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
    ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
    ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
    ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
    ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
    ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
    ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
    ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
    ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
    ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
    ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
    ATI Radeon 4800 Series, ATI Radeon HD 4850 x2,
    ATI FirePro V8750 (FireGL), ATI FirePro V7760 (FireGL),
    ATI Mobility RADEON HD 4850, ATI Mobility RADEON HD 4850 X2,
    ATI Radeon 4800 Series, ATI FirePro RV770, AMD FireStream 9270,
    AMD FireStream 9250, ATI FirePro V8700 (FireGL),
    ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
    ATI Mobility RADEON HD 4870, ATI Radeon 4800 Series,
    ATI Radeon 4800 Series, ATI FirePro M7750, ATI M98, ATI M98, ATI M98,
    ATI Mobility Radeon HD 4650, ATI Radeon RV730 (AGP),
    ATI Mobility Radeon HD 4670, ATI FirePro M5750,
    ATI Mobility Radeon HD 4670, ATI Radeon RV730 (AGP),
    ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
    ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
    ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
    ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
    ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
    ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI Radeon HD 4770,
    ATI FirePro M5750, ATI RV610, ATI Radeon HD 2400 XT,
    ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
    ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
    ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
    ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
    ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
    ATI Mobility Radeon HD 3850 X2, ATI RV670,
    ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
    ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
    ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
    ATI Radeon RV710, ATI Radeon RV710, ATI Radeon RV710,
    ATI Radeon HD 4350, ATI Mobility Radeon 4300 Series,
    ATI Mobility Radeon 4500 Series, ATI Mobility Radeon 4500 Series,
    ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
    ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
    ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
    ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
    ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
    ATI FireGL V3600, ATI Radeon HD 2600 LE,
    ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
    ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
    ATI Radeon HD 3450, ATI Radeon HD 3450, ATI Radeon HD 3430,
    ATI Radeon HD 3450, ATI FirePro V3700, ATI FireMV 2450,
    ATI FireMV 2260, ATI FireMV 2260, ATI Radeon HD 3600 Series,
    ATI Radeon HD 3650 AGP, ATI Radeon HD 3600 PRO,
    ATI Radeon HD 3600 XT, ATI Radeon HD 3600 PRO,
    ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
    ATI Mobility FireGL V5700, ATI Mobility FireGL V5725,
    ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
    ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
    ATI Radeon HD 3300 Graphics, ATI Radeon HD 3200 Graphics,
    ATI Radeon 3000 Graphics, SUMO, SUMO, SUMO2, SUMO2, SUMO2, SUMO2,
    SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, ATI Radeon HD 4200,
    ATI Radeon 4100, ATI Mobility Radeon HD 4200,
    ATI Mobility Radeon 4100, ATI Radeon HD 4290, ATI Radeon HD 4250,
    AMD Radeon HD 6310 Graphics, AMD Radeon HD 6310 Graphics,
    AMD Radeon HD 6250 Graphics, AMD Radeon HD 6250 Graphics,
    AMD Radeon HD 6300 Series Graphics,
    AMD Radeon HD 6200 Series Graphics, PALM, PALM, PALM, CYPRESS,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, AMD Firestream 9370,
    AMD Firestream 9350, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5800 Series, ATI Radeon HD 5900 Series,
    ATI Radeon HD 5900 Series, ATI Mobility Radeon HD 5800 Series,
    ATI Mobility Radeon HD 5800 Series,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
    ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
    ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
    ATI Mobility Radeon HD 5000 Series,
    ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5670,
    ATI Radeon HD 5570, ATI Radeon HD 5500 Series, REDWOOD,
    ATI Mobility Radeon HD 5000 Series,
    ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon Graphics,
    ATI Mobility Radeon Graphics, CEDAR,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, ATI FirePro 2270, CEDAR,
    ATI Radeon HD 5450, CEDAR, CEDAR, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
    CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
    AMD Radeon HD 6900 Series, AMD Radeon HD 6900 Series, CAYMAN, CAYMAN,
    CAYMAN, AMD Radeon HD 6900M Series, Mobility Radeon HD 6000 Series,
    BARTS, BARTS, Mobility Radeon HD 6000 Series,
    Mobility Radeon HD 6000 Series, BARTS, BARTS, BARTS, BARTS,
    AMD Radeon HD 6800 Series, AMD Radeon HD 6800 Series,
    AMD Radeon HD 6700 Series, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
    CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, ARUBA, ARUBA,
    ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
    ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
    ARUBA, ARUBA, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI,
    TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, PITCAIRN, PITCAIRN,
    PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
    PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, VERDE, VERDE, VERDE, VERDE,
    VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
    VERDE, VERDE, VERDE, VERDE, VERDE, VERDE
[    30.337] (II) VESA: driver for VESA chipsets: vesa
[    30.337] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    30.338] (II) FBDEV: driver for framebuffer: fbdev
[    30.338] (++) using VT number 7

[    30.338] (II) [KMS] Kernel modesetting enabled.
[    30.338] (WW) Falling back to old probe method for vesa
[    30.338] (WW) Falling back to old probe method for modesetting
[    30.338] (WW) Falling back to old probe method for fbdev
[    30.338] (II) Loading sub module "fbdevhw"
[    30.338] (II) LoadModule: "fbdevhw"
[    30.338] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    30.338] (II) Module fbdevhw: vendor="X.Org Foundation"
[    30.338]     compiled for 1.13.3, module version = 0.0.2
[    30.338]     ABI class: X.Org Video Driver, version 13.1
[    30.339] (II) RADEON(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    30.339] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    30.339] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    30.339] (==) RADEON(0): Default visual is TrueColor
[    30.339] (==) RADEON(0): RGB weight 888
[    30.339] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    30.339] (--) RADEON(0): Chipset: "ATI Radeon X1200" (ChipID = 0x7942)
[    30.339] (II) Loading sub module "dri2"
[    30.339] (II) LoadModule: "dri2"
[    30.339] (II) Module "dri2" already built-in
[    30.339] (II) Loading sub module "exa"
[    30.339] (II) LoadModule: "exa"
[    30.339] (II) Loading /usr/lib/xorg/modules/libexa.so
[    30.339] (II) Module exa: vendor="X.Org Foundation"
[    30.339]     compiled for 1.13.3, module version = 2.6.0
[    30.339]     ABI class: X.Org Video Driver, version 13.1
[    30.339] (II) RADEON(0): KMS Color Tiling: enabled
[    30.339] (II) RADEON(0): KMS Color Tiling 2D: disabled
[    30.339] (II) RADEON(0): KMS Pageflipping: enabled
[    30.339] (II) RADEON(0): SwapBuffers wait for vsync: enabled
[    30.516] (II) RADEON(0): Output VGA-0 has no monitor section
[    30.516] (II) RADEON(0): Output LVDS has no monitor section
[    30.692] (II) RADEON(0): Output S-video has no monitor section
[    30.694] (II) RADEON(0): Output DVI-0 has no monitor section
[    30.868] (II) RADEON(0): EDID for output VGA-0
[    30.868] (II) RADEON(0): EDID for output LVDS
[    30.868] (II) RADEON(0): Manufacturer: LPL  Model: e300  Serial#: 0
[    30.868] (II) RADEON(0): Year: 2006  Week: 0
[    30.868] (II) RADEON(0): EDID Version: 1.3
[    30.868] (II) RADEON(0): Digital Display Input
[    30.868] (II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
[    30.868] (II) RADEON(0): Gamma: 2.20
[    30.868] (II) RADEON(0): No DPMS capabilities specified
[    30.868] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    30.868] (II) RADEON(0): First detailed timing is preferred mode
[    30.868] (II) RADEON(0): redX: 0.600 redY: 0.351   greenX: 0.324 greenY: 0.554
[    30.868] (II) RADEON(0): blueX: 0.153 blueY: 0.145   whiteX: 0.312 whiteY: 0.328
[    30.868] (II) RADEON(0): Manufacturer's mask: 0
[    30.868] (II) RADEON(0): Supported detailed timing:
[    30.868] (II) RADEON(0): clock: 71.0 MHz   Image Size:  331 x 207 mm
[    30.868] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
[    30.868] (II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 823 v_border: 0
[    30.868] (II) RADEON(0):  LGPhilipsLCD
[    30.868] (II) RADEON(0):  LP154WX4-TLC3
[    30.868] (II) RADEON(0): EDID (in hex):
[    30.868] (II) RADEON(0):     00ffffffffffff00320c00e300000000
[    30.868] (II) RADEON(0):     00100103802115780ab3409959538d27
[    30.868] (II) RADEON(0):     25505400000001010101010101010101
[    30.868] (II) RADEON(0):     010101010101bc1b00a0502017303020
[    30.868] (II) RADEON(0):     36004bcf100000190000000000000000
[    30.868] (II) RADEON(0):     00000000000000000000000000fe004c
[    30.868] (II) RADEON(0):     475068696c6970734c43440a000000fe
[    30.868] (II) RADEON(0):     004c503135345758342d544c4333003c
[    30.868] (II) RADEON(0): Printing probed modes for output LVDS
[    30.868] (II) RADEON(0): Modeline "1280x800"x59.9   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz eP)
[    30.868] (II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
[    30.868] (II) RADEON(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
[    30.868] (II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
[    30.868] (II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
[    30.868] (II) RADEON(0): Modeline "848x480"x59.7   31.50  848 872 952 1056  480 483 493 500 -hsync +vsync (29.8 kHz)
[    30.868] (II) RADEON(0): Modeline "720x480"x59.7   26.75  720 744 808 896  480 483 493 500 -hsync +vsync (29.9 kHz)
[    30.868] (II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
[    31.044] (II) RADEON(0): EDID for output S-video
[    31.046] (II) RADEON(0): EDID for output DVI-0
[    31.046] (II) RADEON(0): Output VGA-0 disconnected
[    31.046] (II) RADEON(0): Output LVDS connected
[    31.046] (II) RADEON(0): Output S-video disconnected
[    31.046] (II) RADEON(0): Output DVI-0 disconnected
[    31.046] (II) RADEON(0): Using exact sizes for initial modes
[    31.046] (II) RADEON(0): Output LVDS using initial mode 1280x800
[    31.046] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    31.046] (II) RADEON(0): mem size init: gart size :1fdff000 vram size: s:10000000 visible:fbd8000
[    31.046] (II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
[    31.046] (==) RADEON(0): DPI set to (96, 96)
[    31.046] (II) Loading sub module "fb"
[    31.046] (II) LoadModule: "fb"
[    31.046] (II) Loading /usr/lib/xorg/modules/libfb.so
[    31.046] (II) Module fb: vendor="X.Org Foundation"
[    31.046]     compiled for 1.13.3, module version = 1.0.0
[    31.046]     ABI class: X.Org ANSI C Emulation, version 0.4
[    31.046] (II) Loading sub module "ramdac"
[    31.046] (II) LoadModule: "ramdac"
[    31.046] (II) Module "ramdac" already built-in
[    31.046] (II) UnloadModule: "vesa"
[    31.047] (II) Unloading vesa
[    31.047] (II) UnloadModule: "modesetting"
[    31.047] (II) Unloading modesetting
[    31.047] (II) UnloadModule: "fbdev"
[    31.047] (II) Unloading fbdev
[    31.047] (II) UnloadSubModule: "fbdevhw"
[    31.047] (II) Unloading fbdevhw
[    31.047] (--) Depth 24 pixmap format is 32 bpp
[    31.047] (II) RADEON(0): [DRI2] Setup complete
[    31.047] (II) RADEON(0): [DRI2]   DRI driver: r300
[    31.047] (II) RADEON(0): [DRI2]   VDPAU driver: r300
[    31.047] (II) RADEON(0): Front buffer size: 4000K
[    31.047] (II) RADEON(0): VRAM usage limit set to 228470K
[    31.047] (==) RADEON(0): Backing store disabled
[    31.047] (II) RADEON(0): Direct rendering enabled
[    31.047] (II) RADEON(0): Render acceleration enabled for R300/R400/R500 type cards.
[    31.047] (II) EXA(0): Driver allocated offscreen pixmaps
[    31.047] (II) EXA(0): Driver registered support for the following operations:
[    31.047] (II)         Solid
[    31.047] (II)         Copy
[    31.047] (II)         Composite (RENDER acceleration)
[    31.047] (II)         UploadToScreen
[    31.047] (II)         DownloadFromScreen
[    31.047] (II) RADEON(0): Acceleration enabled
[    31.047] (==) RADEON(0): DPMS enabled
[    31.047] (==) RADEON(0): Silken mouse enabled
[    31.048] (II) RADEON(0): Set up textured video
[    31.048] (II) RADEON(0): [XvMC] Associated with Radeon Textured Video.
[    31.048] (II) RADEON(0): [XvMC] Extension initialized.
[    31.048] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    31.048] (--) RandR disabled
[    31.060] (II) SELinux: Disabled on system
[    31.286] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    31.286] (II) AIGLX: enabled GLX_INTEL_swap_event
[    31.286] (II) AIGLX: enabled GLX_ARB_create_context
[    31.286] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    31.286] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    31.286] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    31.286] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    31.287] (II) AIGLX: Loaded and initialized r300
[    31.287] (II) GLX: Initialized DRI2 GL provider for screen 0
[    31.288] (II) RADEON(0): Setting screen physical size to 338 x 211
[    31.318] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    31.323] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    31.323] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    31.324] (II) LoadModule: "evdev"
[    31.324] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    31.335] (II) Module evdev: vendor="X.Org Foundation"
[    31.335]     compiled for 1.13.3, module version = 2.7.3
[    31.335]     Module class: X.Org XInput Driver
[    31.335]     ABI class: X.Org XInput driver, version 18.0
[    31.335] (II) Using input driver 'evdev' for 'Power Button'
[    31.335] (**) Power Button: always reports core events
[    31.335] (**) evdev: Power Button: Device: "/dev/input/event2"
[    31.335] (--) evdev: Power Button: Vendor 0 Product 0x1
[    31.335] (--) evdev: Power Button: Found keys
[    31.335] (II) evdev: Power Button: Configuring as keyboard
[    31.335] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    31.335] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    31.335] (**) Option "xkb_rules" "evdev"
[    31.335] (**) Option "xkb_model" "pc105"
[    31.335] (**) Option "xkb_layout" "us"
[    31.335] (**) Option "xkb_variant" "euro"
[    31.335] (**) Option "xkb_options" "lv3:ralt_switch"
[    31.342] (II) XKB: reuse xkmfile /var/lib/xkb/server-8607B2682176CB8E0C80E68C2B34B5746457B906.xkm
[    31.343] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[    31.343] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    31.343] (II) Using input driver 'evdev' for 'Video Bus'
[    31.343] (**) Video Bus: always reports core events
[    31.343] (**) evdev: Video Bus: Device: "/dev/input/event4"
[    31.343] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    31.343] (--) evdev: Video Bus: Found keys
[    31.343] (II) evdev: Video Bus: Configuring as keyboard
[    31.343] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:19/LNXVIDEO:00/input/input4/event4"
[    31.343] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    31.343] (**) Option "xkb_rules" "evdev"
[    31.343] (**) Option "xkb_model" "pc105"
[    31.343] (**) Option "xkb_layout" "us"
[    31.343] (**) Option "xkb_variant" "euro"
[    31.343] (**) Option "xkb_options" "lv3:ralt_switch"
[    31.344] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    31.344] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    31.344] (II) Using input driver 'evdev' for 'Power Button'
[    31.344] (**) Power Button: always reports core events
[    31.344] (**) evdev: Power Button: Device: "/dev/input/event0"
[    31.344] (--) evdev: Power Button: Vendor 0 Product 0x1
[    31.344] (--) evdev: Power Button: Found keys
[    31.344] (II) evdev: Power Button: Configuring as keyboard
[    31.344] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    31.344] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    31.344] (**) Option "xkb_rules" "evdev"
[    31.345] (**) Option "xkb_model" "pc105"
[    31.345] (**) Option "xkb_layout" "us"
[    31.345] (**) Option "xkb_variant" "euro"
[    31.345] (**) Option "xkb_options" "lv3:ralt_switch"
[    31.345] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[    31.345] (II) No input driver specified, ignoring this device.
[    31.345] (II) This device may have been added with another device file.
[    31.346] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:01.0/0000:01:05.0/drm/card0
[    31.346] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    31.346] (II) config/udev: Adding input device HDA ATI SB Mic (/dev/input/event5)
[    31.346] (II) No input driver specified, ignoring this device.
[    31.346] (II) This device may have been added with another device file.
[    31.347] (II) config/udev: Adding input device HDA ATI SB Headphone (/dev/input/event6)
[    31.347] (II) No input driver specified, ignoring this device.
[    31.347] (II) This device may have been added with another device file.
[    31.347] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    31.347] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    31.347] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    31.347] (**) AT Translated Set 2 keyboard: always reports core events
[    31.347] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    31.347] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    31.347] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    31.347] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    31.347] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    31.347] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 9)
[    31.347] (**) Option "xkb_rules" "evdev"
[    31.347] (**) Option "xkb_model" "pc105"
[    31.347] (**) Option "xkb_layout" "us"
[    31.347] (**) Option "xkb_variant" "euro"
[    31.347] (**) Option "xkb_options" "lv3:ralt_switch"
[    31.348] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event7)
[    31.348] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    31.348] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    31.348] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[    31.348] (II) LoadModule: "synaptics"
[    31.349] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    31.349] (II) Module synaptics: vendor="X.Org Foundation"
[    31.349]     compiled for 1.13.1.901, module version = 1.6.2
[    31.349]     Module class: X.Org XInput Driver
[    31.349]     ABI class: X.Org XInput driver, version 18.0
[    31.349] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    31.349] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    31.349] (**) Option "Device" "/dev/input/event7"
[    31.350] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[    31.350] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[    31.350] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    31.350] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    31.350] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    31.350] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    31.350] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    31.350] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    31.352] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio4/input/input7/event7"
[    31.352] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 10)
[    31.352] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    31.352] (**) synaptics: SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[    31.352] (**) synaptics: SynPS/2 Synaptics TouchPad: AccelFactor is now 0.040
[    31.352] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    31.352] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    31.352] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    31.352] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    31.352] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    31.353] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    31.353] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    37.136] (II) RADEON(0): EDID vendor "LPL", prod id 58112
[    37.136] (II) RADEON(0): Printing DDC gathered Modelines:
[    37.136] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz eP)
[    44.084] (II) RADEON(0): EDID vendor "LPL", prod id 58112
[    44.084] (II) RADEON(0): Printing DDC gathered Modelines:
[    44.084] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz eP)
[    44.436] (II) RADEON(0): EDID vendor "LPL", prod id 58112
[    44.436] (II) RADEON(0): Printing DDC gathered Modelines:
[    44.436] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz eP)
[   448.604] (II) RADEON(0): EDID vendor "LPL", prod id 58112
[   448.604] (II) RADEON(0): Printing DDC gathered Modelines:
[   448.604] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz eP)
[   448.960] (II) RADEON(0): EDID vendor "LPL", prod id 58112
[   448.960] (II) RADEON(0): Printing DDC gathered Modelines:
[   448.960] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz eP)
[   453.228] (II) RADEON(0): EDID vendor "LPL", prod id 58112
[   453.228] (II) RADEON(0): Printing DDC gathered Modelines:
[   453.228] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz eP)
[   453.584] (II) RADEON(0): EDID vendor "LPL", prod id 58112
[   453.584] (II) RADEON(0): Printing DDC gathered Modelines:
[   453.584] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz eP)
[ 20430.967] (II) config/udev: Adding input device Kensington Pocket Mouse Pro Wireless (/dev/input/event8)
[ 20430.967] (**) Kensington Pocket Mouse Pro Wireless: Applying InputClass "evdev pointer catchall"
[ 20430.967] (II) Using input driver 'evdev' for 'Kensington Pocket Mouse Pro Wireless'
[ 20430.967] (**) Kensington Pocket Mouse Pro Wireless: always reports core events
[ 20430.967] (**) evdev: Kensington Pocket Mouse Pro Wireless: Device: "/dev/input/event8"
[ 20430.967] (--) evdev: Kensington Pocket Mouse Pro Wireless: Vendor 0x47d Product 0x1023
[ 20430.967] (--) evdev: Kensington Pocket Mouse Pro Wireless: Found 3 mouse buttons
[ 20430.967] (--) evdev: Kensington Pocket Mouse Pro Wireless: Found scroll wheel(s)
[ 20430.967] (--) evdev: Kensington Pocket Mouse Pro Wireless: Found relative axes
[ 20430.967] (--) evdev: Kensington Pocket Mouse Pro Wireless: Found x and y relative axes
[ 20430.967] (II) evdev: Kensington Pocket Mouse Pro Wireless: Configuring as mouse
[ 20430.967] (II) evdev: Kensington Pocket Mouse Pro Wireless: Adding scrollwheel support
[ 20430.967] (**) evdev: Kensington Pocket Mouse Pro Wireless: YAxisMapping: buttons 4 and 5
[ 20430.968] (**) evdev: Kensington Pocket Mouse Pro Wireless: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[ 20430.968] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.2/usb4/4-1/4-1:1.0/input/input8/event8"
[ 20430.968] (II) XINPUT: Adding extended input device "Kensington Pocket Mouse Pro Wireless" (type: MOUSE, id 11)
[ 20430.968] (II) evdev: Kensington Pocket Mouse Pro Wireless: initialized for relative axes.
[ 20430.968] (**) Kensington Pocket Mouse Pro Wireless: (accel) keeping acceleration scheme 1
[ 20430.968] (**) Kensington Pocket Mouse Pro Wireless: (accel) acceleration profile 0
[ 20430.968] (**) Kensington Pocket Mouse Pro Wireless: (accel) acceleration factor: 2.000
[ 20430.968] (**) Kensington Pocket Mouse Pro Wireless: (accel) acceleration threshold: 4
[ 20430.973] (II) config/udev: Adding input device Kensington Pocket Mouse Pro Wireless (/dev/input/mouse1)
[ 20430.973] (II) No input driver specified, ignoring this device.
[ 20430.973] (II) This device may have been added with another device file.
[ 24142.552] (II) RADEON(0): EDID vendor "LPL", prod id 58112
[ 24142.552] (II) RADEON(0): Printing DDC gathered Modelines:
[ 24142.552] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz eP)
[ 24142.908] (II) RADEON(0): EDID vendor "LPL", prod id 58112
[ 24142.908] (II) RADEON(0): Printing DDC gathered Modelines:
[ 24142.908] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz eP)
[ 24149.656] (II) RADEON(0): EDID vendor "LPL", prod id 58112
[ 24149.656] (II) RADEON(0): Printing DDC gathered Modelines:
[ 24149.656] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz eP)
[ 24150.016] (II) RADEON(0): EDID vendor "LPL", prod id 58112
[ 24150.016] (II) RADEON(0): Printing DDC gathered Modelines:
[ 24150.016] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz eP)
[ 24198.836] (II) RADEON(0): EDID vendor "LPL", prod id 58112
[ 24198.836] (II) RADEON(0): Printing DDC gathered Modelines:
[ 24198.836] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz eP)
[ 24199.196] (II) RADEON(0): EDID vendor "LPL", prod id 58112
[ 24199.196] (II) RADEON(0): Printing DDC gathered Modelines:
[ 24199.196] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz eP)
[ 24430.176] (II) RADEON(0): EDID vendor "LPL", prod id 58112
[ 24430.176] (II) RADEON(0): Printing DDC gathered Modelines:
[ 24430.176] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz eP)
[ 24430.536] (II) RADEON(0): EDID vendor "LPL", prod id 58112
[ 24430.536] (II) RADEON(0): Printing DDC gathered Modelines:
[ 24430.536] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz eP)
[ 28454.160] (II) RADEON(0): EDID vendor "LPL", prod id 58112
[ 28454.160] (II) RADEON(0): Printing DDC gathered Modelines:
[ 28454.160] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz eP)
```

---

### Post by Yellow Pasque on 2013-06-05
Hmm. ^That looks fine. Try the verbose output of glxinfo.
```
export LIBGL_DEBUG=verbose; glxinfo
```

---

### Post by Ashboy on 2013-06-06
So... something I ended up doing last night ended up crashing the video driver after a reboot (I started seeing some more strange things, thought it was best to reboot -oops maybe not). I couldn't get beyond the BIOS screens anymore. I was expecting to be able to access a safe mode at the very least, so I ended up losing a lot of work reinstalling from 9.10. Which kind of took the entire night. :(
  
This time I'm playing it safe. Not progressing beyond 12.04 and leaving Xfce alone for a bit (although I will need to disable Compiz at the very least to reduce the GPU workload). I checked Direct Rendering again and this time it seems to be enabled. Don't know for sure until I've tried a game though, which is what I am downloading right now. I'm.. not optimistic things will have changed for the better just yet.

---

### Post by Ashboy on 2013-06-06
Seems like my misfortune last night turned to fortune by morning. It took me a while to get everything up and running, but almost everything is working as it should now and at a *much* higher framerate. There's even a couple of things that weren't working before, like hardware mipmapping. I'm simply used to really bad, pre 2008 non-propriety drivers, so I thought a lot of that stuff being broken was actually quite normal. The only thing that doesn't seem to work is multisampling, but that may just be Wine goofing up.

I also had to go back to XUbuntu after all.. I just can't stand Unity. 

Anyway, this is really great. Thanks for the help everyone. I know it didn't end up mattering much, but if I hadn't tried to look into things.. I wouldn't have had to reinstall eventually. So, big thanks to everyone who replied. :)

Edit: One more thing I need to mention. This time I chose not to progress to 13.04. I'm just running the 12.04 long term release support now. There's no way to tell anymore if that had anything to do with all my issues and the final crash at all, but it's probably best if I leave that bit of info here for prosperity. 13.04 Unity was teeming with graphical glitches, which was the main reason I installed Xfce. But maybe whatever was causing those glitches kept causing problems beyond the desktop manager I was using.

---

