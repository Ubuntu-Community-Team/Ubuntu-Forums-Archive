---
title: "What a mess! (XGL and ATI issues)"
date: 2006-06-11
forum: Hardware &amp; Laptops
---

### Post by darkrad on 2006-06-11
I have an acer aspire 1610 laptop, installed succesfully 6.06. I followed several guides to get XGL to work on gdm but i couldn't have success. The problem is that i can't even get ati driver to work properly (.... rendering: No). Is there any way to remove all the GUI parts (compiz, xgl, gnome, ....) of ubuntu and start all over? If yes, which packages i need to uninstall? Who can help please?

---

### Post by leech on 2006-06-12
Why would you need to remove Gnome?  It'd be just as logical for you to remove the ATI :D  Well, since it's a laptop, that's not possible.  What I would do is disable the XGL stuff in gdm.conf-custom and then make sure that the fglrx driver is loading and you're getting 3D acceleration, THEN try getting XGL working.

By the way, if you have XGL working, it will kill your 3D Acceleration, since it uses Mesa GL instead of ATI or nVidia's GL libraries.

Leech

---

### Post by darkrad on 2006-06-12
ok, so i did this:

```
sudo apt-get remove --purge compiz xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 compiz-gnome
```

then i reinstalled xserver-xorg

```
sudo apt-get install xserver-xorg
```

Then i logged in X doing

```
startx
```

Then i installed the ati driver [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.25.18-x86.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.25.18-x86.run) 

```
sudo sh ./ati-driver-installer-8.25.18-x86.run
```

at the end i typed:

```
sudo aticonfig --initial
```

and i got
> aticonfig: error while loading shared libraries: libfglrx_pp.so.1: cannot open shared object file: No such file or directory

the result of "glxinfo" is:

> name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method,
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_fbconfig,
    GLX_SGIX_visual_select_group
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_imaging, GL_ARB_multitexture,
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shadow,
    GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar,
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat,
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_window_pos,
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_func_separate,
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract,
    GL_EXT_clip_volume_hint, GL_EXT_copy_texture, GL_EXT_draw_range_elements,
    GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels,
    GL_EXT_point_parameters, GL_EXT_polygon_offset, GL_EXT_rescale_normal,
    GL_EXT_secondary_color, GL_EXT_separate_specular_color,
    GL_EXT_shadow_funcs, GL_EXT_stencil_two_side, GL_EXT_stencil_wrap,
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D,
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle,
    GL_EXT_vertex_array, GL_APPLE_packed_pixels, GL_ATI_texture_env_combine3,
    GL_ATI_texture_mirror_once, GL_ATIX_texture_env_combine3,
    GL_HP_occlusion_test, GL_IBM_texture_mirrored_repeat,
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_ycbcr_texture,
    GL_NV_blend_square, GL_NV_point_sprite, GL_NV_texgen_reflection,
    GL_NV_texture_rectangle, GL_SGIS_generate_mipmap,
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp,
    GL_SGIS_texture_lod, GL_SGIX_depth_texture, GL_SGIX_shadow,
    GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

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

the result of "fglrxinfo" is:

> Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

Do you have any idea how to get the ati driver working succesfully?
And why when i reboot i have to login in dos-like mode and then run "startx" in order to get X start? How to let it auto boot in X? thanks

---

### Post by darkrad on 2006-06-12
i did 

```
sudo apt-get install ubuntu-desktop
```

and now gdm starts on boot, but i still get

> error while loading shared libraries: libfglrx_pp.so.1: cannot open shared object file: No such file or directory

when i do "aticonfig --initial" after have succesfully installed the ati driver using the installer. Any idea?

---

### Post by darkrad on 2006-06-12
ok i follewed the guide here:

[http://www.ubuntuforums.org/showthread.php?t=76116&page=92](http://www.ubuntuforums.org/showthread.php?t=76116&page=92)

and now ati driver seems to work properly.
Now, is there a way to get that XGL to work without messing up all again?

---

### Post by darkrad on 2006-06-12
i followed the second method of the guide [http://www.compiz.net/viewtopic.php?id=389&p=1](http://www.compiz.net/viewtopic.php?id=389&p=1) and i succesfully entered into the XGL session, but i think plugins aren't loaded since windows haven't borders and so on, and when i do "fglrxinfo" in a terminal i get:

> Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9700 Generic
OpenGL version string: 2.0.5814 (8.25.18 )

why drivers that succesfully work in normal gdm session doesn't work in xgl? how to fix that?
and why can't i see window borders when i load gnome session (while i see them in gnome failsafe sessions)?
thanks

---

### Post by darkrad on 2006-06-12
```
metacity --replace
```
fixed the no-win-borders in gnome session issue.
The problem that remain to fix is: why in XGL session ati driver stop working?

---

### Post by ajamess on 2006-06-12
Try starting XGL on display 1, display 0 gives ATI cards problems.

---

### Post by darkrad on 2006-06-12
> Try starting XGL on display 1, display 0 gives ATI cards problems.
and how to do that?

---

### Post by darkrad on 2006-06-13
> Try starting XGL on display 1, display 0 gives ATI cards problems.
Anybody know how to do that?

---

### Post by korosu on 2006-06-14
after many failed attempts, i decided to give [this guide]("http://www.tectonic.co.za/view.php?id=916") a shot, and it actually worked on my dell E1505 (mobility radeon X1400).  i couldn't believe how unbelievably easy and quick it was compared to what i had been trying before.

---

