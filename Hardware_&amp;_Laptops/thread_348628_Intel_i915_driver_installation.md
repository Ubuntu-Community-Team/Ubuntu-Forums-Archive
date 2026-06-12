---
title: "Intel i915 driver installation"
date: 2007-01-29
forum: Hardware &amp; Laptops
---

### Post by tbresson on 2007-01-29
Hi.

I'm trying to install the graphics driver for my Ubuntu 6.10.
The driver is for my i915.

The driver I found is this: i915-20060403-linux.i386

When I try to install the driver it says: 
The DRI drivers can not be installed without the latest kernel modules.

and the log file says:
Makefile:173: *** Cannot find a kernel config file.  Stop.

According to the installer it states it gets information from different dirs, like this:
Xorg Dir         : /usr/X11R6
Xorg Modules Dir : /usr/X11R6/lib/modules
Xorg Library Dir : /usr/X11R6/lib

Kernel Version   : 2.6.17-10-generic
Module Directory : /lib/modules/2.6.17-10-generic

Are these correct? Do I need to symlink something? or do I need to download source, headers or similar? I tried a few things, but nothing seems to work.

UPDATE: 
I did: uname -r

and then used the kernel version to do this:
apt-get install sudo apt-get install linux-headers-2.6.17-10-generic

And still get an error, but now it's a different one!

---

### Post by encompass on 2007-01-29
You should be able to use the driver that came with ubuntu just fine.
Why do you need the upgraded driver?
The reason I ask is because I have the same driver but for ubuntu built in.

---

### Post by tbresson on 2007-01-29
I want to be able to player media stuff, like movie clips.

I have an ATI based card at home and used the Add/Remove feature to add the binary ATI drivers of X.Org on that system. And it was just like "click" and then I could use mplayer og vlc which I couldn't before.

I tried out the Ubuntu based Linux Mint "Bea" and it worked really great, and I want to stay with the Ubuntu distro ...

---

### Post by encompass on 2007-01-29
you should have everything ready and working now...
can you post the output of this command?
glxinfo
thanks
this card is open source.  in otherwords it works VERY well in linux.  It jsut works... no more downloading drivers and installing them.

---

### Post by tbresson on 2007-01-29
I'll post the error tomorrow. The Intel gfx card does not work sincen no driver has been installed. There are some errors in the driver I think, but it's also a snapshot.

I tried downloading from Intels Linux driver site, but I don't understand git, mesa and the other internal stuff they write about. I tried apt-get install git - but I couldn't get it to work.

The ATI driver on my other PC works just fine if that's what you meant.

---

### Post by encompass on 2007-01-29
You shouldn't need it.  At least as far as I have seen with the many many cases here.
Pop the live cd in and run glxinfo and see if you have direct rendering.  It should work with out adding the driver.  That is what makes linux so cool!

---

### Post by tbresson on 2007-01-29
I'll try and let you know :)

---

### Post by tbresson on 2007-01-30
I just tried and it doesn't work.

---

### Post by encompass on 2007-01-30
Please post the output... I am not trusting the card that you have.
In addition what information can you tell me about your computer... for example the model and brand.

---

### Post by tbresson on 2007-01-30
My PC is a Dell Latitude D610.

Output:

name of display: :0.0
libGL warning: 3D driver claims to not support visual 0x5b
display: :0  screen: 0
direct rendering: Yes
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_make_current_read, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 915GM 20050225
OpenGL version string: 1.3 Mesa 6.5.1
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program, GL_ARB_imaging, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_point_parameters, 
    GL_ARB_shadow, GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_blend_color, GL_EXT_blend_equation_separate, 
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_cull_vertex, GL_EXT_compiled_vertex_array, 
    GL_EXT_convolution, GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_histogram, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_polygon_offset, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
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
    GL_NV_texture_rectangle, GL_NV_texgen_reflection, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_OES_read_format, GL_SGI_color_matrix, 
    GL_SGI_color_table, GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SUN_multi_draw_arrays
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

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
0x5b 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

---

### Post by encompass on 2007-01-30
You have 3d support. It works out of the box.  And unless your getting system crashes and need to report a bug.  I would stick with what you have.
If you don't get 3d support in your main install then you have done something that has stopped it from working. I can try to help you from there.
So I would worry about installing the driver.  It is already there.
Thanks for your effort.

---

### Post by encompass on 2007-01-30
As for the media clips... sounds like a different issue... what file are you trying to play?

---

### Post by tbresson on 2007-01-30
I'm trying to play a divx clip.

On my ATI pc I couldn't play the clip either, until I installed the ATI driver.
So I thought it was the same issue with my Intel based gfx card.

---

### Post by encompass on 2007-01-30
Good guess given the things that have happened.  This should solve most of the issues that you may have with "Restricted Formats"  These formats can't come with ubuntu by default because they break laws in some countries.  So here is the link... 
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
I recommend using totem-xine as it is very integrated into the ubuntu experience of things.
Remember to get any others you may need too.  But in the end avoid them as much as you can.  For example... create your cd collection in ogg it is better quality and open technology.
Rock on and good luck.
Remember to do the instructions according to your version.

---

### Post by tbresson on 2007-01-31
Thank you for your effort. I'll try it out.
Still I don't understand why I have to undergo this since to newly installed Ubuntu 6.10; one with an ATI card and one with an Intel card with same setup turns out to work differently.

The ATI based PC can play divx without any problems, but only when I install the X.org Binary driver for ATI. The Intel based won't - and I can't install the driver the same way.

Also, adding software like Mplayer via the Add/Remove button does tell you if you add something that's in the restrictive "zone". Perhaps it's too complicated for me to understand....

But thank you very much for your patience :)

---

### Post by encompass on 2007-01-31
You need to start the repositories that are restricted.  
Don't worry it is not too hard... if you would like... use any of my messengers and contact me.  I am willing to give you personal help.
All the instructions are on that restricted formats page.

---

