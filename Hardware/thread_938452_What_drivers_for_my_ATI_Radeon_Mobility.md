---
title: "What drivers for my ATI Radeon Mobility?"
date: 2008-10-04
forum: Hardware
---

### Post by Hep! on 2008-10-04
I've done quite a bit of research and have had no luck getting fglrx installed. I am able to get my adapter working at the correct resolution using radeon, but I've been unable to get 3dsupport working at all. This is what I really want (and think I can only get done through fglrx?)

lspci outputs this for me:

> 01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY

My system is a Dell Inspiron 4100 (with the ATI card obviously... sigh)

This is the best information I could find.
[http://gentoo-wiki.com/HARDWARE_Gentoo_on_Dell_Inspiron_4100](http://gentoo-wiki.com/HARDWARE_Gentoo_on_Dell_Inspiron_4100)

I know very little about linux but thought I'd give it a shot, good learning experience. This is my first post here, so I appreciate any help given!

Thanks,
-Hep!

---

### Post by jocko on 2008-10-05
Mobility M6 is not supported by fglrx (nothing older than radeon 9500 is supported and, if I'm not mistaken, mobility M6 is equivalent to radeon 7000).
The open source driver ("radeon") should support your card.

---

### Post by Hep! on 2008-10-05
Hey jocko, thanks for the response!

I am currently using the radeon driver for my card, but it is not giving me 3d support. According to the gentoo wiki, you can use fglrx with this card (though I did read on the Ubuntu wiki what you said, that only cards 9500 and higher are supported). I've read that in order to get 3d support, I must use fglrx. Does gentoo and Ubuntu simply come with two different versions of the driver? Or is there some tweaking I must do to get it to use fglrx?

---

### Post by jocko on 2008-10-06
> **Hep! said:**
> Hey jocko, thanks for the response!

I am currently using the radeon driver for my card, but it is not giving me 3d support. According to the gentoo wiki, you can use fglrx with this card (though I did read on the Ubuntu wiki what you said, that only cards 9500 and higher are supported). I've read that in order to get 3d support, I must use fglrx. Does gentoo and Ubuntu simply come with two different versions of the driver? Or is there some tweaking I must do to get it to use fglrx?

Fglrx has never, and will never support such an old card. That's true for whichever linux distro you use, ati has never produced drivers for anything that old. The gentoo wiki must be wrong.
The open source driver should have 3d support.

---

### Post by Hep! on 2008-10-06
Okay, thanks for the clarification...
Could you help me then with getting 3d support to work with the radeon driver, or should I make an entirely new topic "Need help getting 3d working with "radeon" driver"

---

### Post by jocko on 2008-10-07
There's [this thread]("http://ubuntuforums.org/showthread.php?t=246746"), which seems to be what you're looking for. Just follow the steps in the first part to edit the xorg.conf file, don't install anything. The thread is old, and some parts are a bit outdated...

---

### Post by Hep! on 2008-10-11
Sorry to be a pain, but I've spent several days messing with my xorg.conf but I've had no luck! I've followed both the guide you linked to me, as well as [this one]("https://help.ubuntu.com/community/RadeonDriver").

Some more troubleshooting info perhaps...

louis@louis-laptop:~$ glxinfo | grep "direct rendering"
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

louis@louis-laptop:~$ LIBGL_DEBUG=verbose glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
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
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_EXT_texture_from_pixmap
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_occlusion_query, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_vertex_program, 
    GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_object, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_paletted_texture, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_shared_texture_palette, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_vertex_array, GL_APPLE_packed_pixels, 
    GL_ATI_draw_buffers, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_ATIX_texture_env_combine3, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_NV_blend_square, 
    GL_NV_fragment_program, GL_NV_light_max_exponent, GL_NV_point_sprite, 
    GL_NV_texgen_reflection, GL_NV_texture_rectangle, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SGIX_shadow, GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x27 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x28 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x29 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x2a 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x55 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

Hopefully this makes a difference....
I would also post my xorg.conf but it's just a generic one at this point...

I'm kind of lost, all help appreciated.

---

### Post by Hep! on 2008-10-11
I went back this morning and re-read the ENTIRE thread you linked me to. I missed one key bit, where someone else had a very similar laptop (Inspiron 4000) WITH THE IDENTICAL PROBLEM. He got the fix, and so did I!
I was trying to use 24 bit color at 1400*1050 on a 16MB card.

Though is something wrong with my calculations here?
16MB = 16384KB
24*1400*1050 = 35280000 bits
35280000/8 = 4410000 bytes
4410000/1024 = 4306.640625 KB (needed)

So theoretically, shouldn't I only need ~4mb to display at 1400x1050x24?

---

