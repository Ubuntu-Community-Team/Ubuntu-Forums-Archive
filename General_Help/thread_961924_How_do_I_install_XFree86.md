---
title: "How do I install XFree86?"
date: 2008-10-28
forum: General Help
---

### Post by Dojan5 on 2008-10-28
Earlier, yesterday or something, I asked for drivers for S3 Savage4, and I actually got a link to a page who had them (Yaaaay), anyhow, when trying to install them, I get the output
```
root@k-designs:/home/joel/Desktop/s3savage-1.0-15# ./install.sh
You must have XFree86 installed.
```
So, as it doesn't exist in the repos, I thought I might ask.
I cannot compile anything due to a somewhat broken processor :(
Anyhow, any help is much appreciated!

---

### Post by Dojan5 on 2008-10-28
Is there any deb package for XFree86?
And sorry for the double post, but the edit button is not there!

---

### Post by alienprdkt on 2008-10-28
you try 

# apt-get install xserver-xfree86

---

### Post by Dojan5 on 2008-10-28
> **alienprdkt said:**
> you try 

# apt-get install xserver-xfree86

Yupp, and I got the output:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package xserver-xfree86 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  xserver-xorg-core
E: Package xserver-xfree86 has no installation candidate

```
So no go with that...

---

### Post by Dojan5 on 2008-10-29
Will XFree86 be in 8.10?

---

### Post by Woody1987 on 2008-10-29
Nobody uses xfree86 anymore. Its outdated. As are, i suspect the graphics drivers you found. Ubuntu and pretty much every other distro uses x.org which is a fork of xfree86. Ubuntu should have automatically installed drivers for that video card anyway. Type glxgears and glxinfo into a terminal and show us the output.

---

### Post by Dojan5 on 2008-11-27
Well, glxgears gave me a window with 3 Dimensional gears, obviously, here is the terminal output:
```
joel@capricorn:~$ glxgears
1216 frames in 5.0 seconds = 243.083 FPS
1235 frames in 5.0 seconds = 246.947 FPS
1235 frames in 5.0 seconds = 246.884 FPS
1223 frames in 5.0 seconds = 244.444 FPS
1235 frames in 5.0 seconds = 246.913 FPS
1235 frames in 5.0 seconds = 246.880 FPS
1234 frames in 5.0 seconds = 246.622 FPS
1235 frames in 5.0 seconds = 246.885 FPS
1235 frames in 5.0 seconds = 246.947 FPS
1235 frames in 5.0 seconds = 246.947 FPS
1235 frames in 5.0 seconds = 246.960 FPS
1235 frames in 5.0 seconds = 246.966 FPS
1215 frames in 5.0 seconds = 242.837 FPS
1078 frames in 5.0 seconds = 215.528 FPS
```
I got bored and closed it...
And here is glxinfo
```
joel@capricorn:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: S3 Graphics Inc.
OpenGL renderer string: Mesa DRI Savage4 20061110 x86/MMX+/3DNow!+
OpenGL version string: 1.2 Mesa 7.2
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_texture_compression, GL_ARB_texture_env_add, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_blend_color, GL_EXT_blend_logic_op, GL_EXT_blend_minmax, 
    GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_compiled_vertex_array, GL_EXT_convolution, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_histogram, GL_EXT_packed_pixels, 
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_lod_bias, GL_EXT_texture_object, 
    GL_EXT_vertex_array, GL_APPLE_packed_pixels, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_MESA_window_pos, 
    GL_NV_light_max_exponent, GL_NV_texgen_reflection, GL_OES_read_format, 
    GL_SGI_color_matrix, GL_SGI_color_table, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod

2 GLX Visuals
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x3b 32 tc  0 16  0 r  .  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None

16 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x3c  0 tc  0 16  0 r  .  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x3d  0 tc  0 16  0 r  .  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x3e  0 tc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x3f  0 tc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x40  0 tc  0 16  0 r  .  .  5  6  5  0  0 16  8  0  0  0  0  0 0 Slow
0x41  0 tc  0 16  0 r  .  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x42  0 tc  0 16  0 r  y  .  5  6  5  0  0 16  8  0  0  0  0  0 0 Slow
0x43  0 tc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x44  0 dc  0 16  0 r  .  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x45  0 dc  0 16  0 r  .  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x46  0 dc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x47  0 dc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x48  0 dc  0 16  0 r  .  .  5  6  5  0  0 16  8  0  0  0  0  0 0 Slow
0x49  0 dc  0 16  0 r  .  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x4a  0 dc  0 16  0 r  y  .  5  6  5  0  0 16  8  0  0  0  0  0 0 Slow
0x4b  0 dc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
```

---

### Post by jespdj on 2008-11-27
So, looks like your problem is solved?
> direct rendering: Yes
This means that you have hardware-accelerated 3D graphics, so your driver must be working as it should.

XFree86 is X Windows server software which is obsolete. It will not be in Intrepid and you don't want it.

---

### Post by Dojan5 on 2008-11-27
> **jespdj said:**
> So, looks like your problem is solved?

This means that you have hardware-accelerated 3D graphics, so your driver must be working as it should.

XFree86 is X Windows server software which is obsolete. It will not be in Intrepid and you don't want it.

But this computer can't use any other compositing manager but Metacity, I've heard that it should be able to use the KDE one, but it doesn't...

---

### Post by plazaster on 2008-12-31
I have the same problem, that is trying to get S3 Savage4 to work, I get the same results as dojan.  I mainly want some desktop effects.  Any help would be helpful. :)
=============================================================
Dual P3, ~750RAM, S3 Savage4, Ibex

(Don't normally do this on NYE, im in outback Australia at the moment)

---

### Post by Dojan5 on 2009-01-03
I seriously thought that I was alone using S3 Savage4.
Anyhow, my soon-to-launch OS will run Xorg on XF86 drivers, including S3 Savage4.

---

### Post by mariceles on 2009-01-11
I too use Savage4, but I think... isn't the chip itself too slow for handling 3D Desktops? Well, In windows, it  cannot even play a 600kbps wmv video, even though I had the driver. The fps was too low that I couldn't see how the professor was writing on the board. The messages didn't appear for a few seconds and then wooosh! I couldn't see them.

---

