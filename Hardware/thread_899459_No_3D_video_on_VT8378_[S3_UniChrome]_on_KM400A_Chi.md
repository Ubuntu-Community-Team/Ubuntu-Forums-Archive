---
title: "No 3D video on VT8378 [S3 UniChrome] on KM400/A Chipset"
date: 2008-08-24
forum: Hardware
---

### Post by jeffmills on 2008-08-24
Hi,

today I installed Ubuntu 8.04 on a **Packard Bell IMEDIA 2725**, which carries a [Quasar (MS6786) V1.0 µATX motherboard]("http://support.packardbell.org/uk/item/index.php?i=spec_quasar")

This motherboard has an integrated videochip on it's [VT8378 [KM400/A] Chipset Host Bridge]("http://hardware4linux.info/component/14764/").

I can't get glxgears to work correctly and thus can't use compiz either. The gears do appear on screen but totally distorted and the console reads:

> 
do_wait: drmWaitVBlank returned -1, IRQs don't seem to be working correctly.
Try running with LIBGL_THROTTLE_REFRESH and LIBL_SYNC_REFRESH unset.


This is the output for glxheads:

> 
glxheads: exercise multiple GLX connections (any key = exit)
Usage:
  glxheads xdisplayname ...
Example:
  glxheads :0 mars:0 venus:1
do_wait: drmWaitVBlank returned -1, IRQs don't seem to be working correctly.
Try running with LIBGL_THROTTLE_REFRESH and LIBL_SYNC_REFRESH unset.
Name: :0
  Display:     0x805e008
  Window:      0x3200002
  Context:     0x8066408
  GL_VERSION:  1.2 Mesa 7.0.3-rc2
  GL_VENDOR:   VIA Technology
  GL_RENDERER: Mesa DRI UniChrome (KM400) 20060710 x86/MMX+/3DNow!+/SSE


And this one for glxinfo:

> 
name of display: :0.0
do_wait: drmWaitVBlank returned -1, IRQs don't seem to be working correctly.
Try running with LIBGL_THROTTLE_REFRESH and LIBL_SYNC_REFRESH unset.
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_visual_select_group
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_swap_frame_usage, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: VIA Technology
OpenGL renderer string: Mesa DRI UniChrome (KM400) 20060710 x86/MMX+/3DNow!+/SSE
OpenGL version string: 1.2 Mesa 7.0.3-rc2
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_point_parameters, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_minmax, 
    GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_compiled_vertex_array, GL_EXT_convolution, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_histogram, 
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_polygon_offset, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_vertex_array, 
    GL_APPLE_packed_pixels, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_MESA_window_pos, GL_NV_blend_square, 
    GL_NV_light_max_exponent, GL_NV_texgen_reflection, GL_OES_read_format, 
    GL_SGI_color_matrix, GL_SGI_color_table, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x22 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x23 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None
0x26 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x27 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x29 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0x2b 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x47 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon


This also mentions the same parameters **LIBGL_THROTTLE_REFRESH** and **LIBL_SYNC_REFRESH**. 
Do you think that unsetting these parameters may work (is there any possibility to get this videochip to work in Linux?) and if so, how do I perform this?

---

### Post by jeffmills on 2008-08-26
Did I not provide enough information? Do people think this is a stupid question? Perhaps the person who knows about this, just didn´t see the thread. That´s why, again I would like to ask about this matter.

---

### Post by Kevbert on 2008-08-26
Unfortunately Via chipsets aren't officially supported by compiz at present (only Intel, nVidia and ATI).

---

### Post by jeffmills on 2008-08-26
> **Kevbert said:**
> Unfortunately Via chipsets aren't officially supported by compiz at present (only Intel, nVidia and ATI).

Alright, that's interesting. However, if the 3D drivers are working as they are supposed to, compiz should work by default right? That just leaves me with the task to find the right driver (modifications) for this chip.

However, after finding the correct name for my integrated videochip, I found some more information in this thread:
[http://ubuntuforums.org/showthread.php?t=678211](http://ubuntuforums.org/showthread.php?t=678211)
[http://help.ubuntu.com/community/UniChrome](http://help.ubuntu.com/community/UniChrome)

---

### Post by Kevbert on 2008-08-26
See this post on the [[COLOR="Red"]compiz forum[/COLOR]]("http://forum.compiz-fusion.org/showthread.php?t=8927&highlight=vt8378").  Compiz won't work but you can try other things.

---

### Post by jeffmills on 2008-08-26
> **Kevbert said:**
> See this post on the [[COLOR="Red"]compiz forum[/COLOR]]("http://forum.compiz-fusion.org/showthread.php?t=8927&highlight=vt8378").  Compiz won't work but you can try other things.

Thanks for finding that post for me, that really is a definite answer :-k I´ll just continue with my mission to get 3D running correctly. It seems it should be possible when looking at the website from [Hardware4Linux]("http://hardware4linux.info/component/20690/")

I would like to try the drivers from VIA Arena, but I'm stuck at [the following page]("http://www.viaarena.com/default.aspx?PageID=2&OSID=45&CatID=3220") where I can't seem to find the correct driver category for my integrated graphics. Which would be suited for me?

And is there an overview of the features supported by the open source driver included in Ubuntu 8.04 repository compared the one on the VIA Arena website?

I also found a bug-report for this in Launchpad ([https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/182246](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/182246)) but this is for the OpenChrome driver, while I seem to be using the UniChrome driver (see logs above). Can anybody explain this? Should I be using the OpenChrome driver and if yes, how do I change this?

---

### Post by Kevbert on 2008-08-27
The problem is Via cards generally don't support 3D graphics acceleration.  It may be worth you running [[COLOR="Red"]compiz-check[/COLOR]]("http://forlong.blogage.de/entries/pages/Compiz-Check") which may give you some additional information.
If you do get this working please post as I don't know of anyone getting compiz working with a Via card and many people seem to be using Via (particularly S3 cards).

---

