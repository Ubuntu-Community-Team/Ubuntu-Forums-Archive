---
title: "Tweak an Intel Extreme Graphics"
date: 2004-11-23
forum: Hardware &amp; Laptops
---

### Post by Sniffer on 2004-11-23
One question?

I have an HP laptop with a CRAP graphic card integrated (INTEL EXTREME GRAPHICS 2)......tough i would like to tweak a bit....at least to get more FPS, special because i use emulators a LOT :D

Here it goes my glxinfo:

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context
client glx vendor string: SGI
client glx version string: 1.2
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 852GM/855GM 20021115
OpenGL version string: 1.2 Mesa 4.0.4
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_transpose_matrix, GL_EXT_abgr,
    GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_func_separate,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint,
    GL_EXT_convolution, GL_EXT_compiled_vertex_array, GL_EXT_fog_coord,
    GL_EXT_histogram, GL_EXT_packed_pixels, GL_EXT_polygon_offset,
    GL_EXT_rescale_normal, GL_EXT_secondary_color, GL_EXT_texture3D,
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, GL_EXT_texture_object,
    GL_EXT_texture_lod_bias, GL_EXT_vertex_array, GL_IBM_rasterpos_clip,
    GL_MESA_window_pos, GL_NV_texgen_reflection, GL_SGI_color_matrix,
    GL_SGI_color_table
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x22 24 tc  1 24  0 r  y  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0x23 24 tc  1 24  0 r  .  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0x24 24 tc  1 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0x25 24 tc  1 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0x26 24 tc  1 24  0 r  y  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0x27 24 tc  1 24  0 r  .  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0x28 24 tc  1 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0x29 24 tc  1 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow



So any ideas

---

### Post by ubuntu_demon on 2005-04-01
how's the videocard functioning ? What motherboard do you have ?

I'm thinking of buying  :

Asrock 775i65GV / Intel 865GV chipset / Integrated Intel Extreme Graphics 2 

see :

[http://www.ubuntuforums.org/showthread.php?t=22880](http://www.ubuntuforums.org/showthread.php?t=22880)

---

### Post by Sniffer on 2005-04-01
Hi

Yes the Intel extreme graphics is supported on boot, so you don't have to do anything to activate 3D support, wich is great :)

Tough this integrated card didn't realize my expectations.....i knew from the beggining that it wasn't very good.....but it comes to be slow #-o  when emulating games and so on as you can see on the detailed post above.


I'm tryng now the new version of ubuntu and hope to test it soon with XORG, let's see if the card behave better......

I have an laptop with it and my motherboard it's from Intel (HP) with intel chipset ofcourse....

Hope it helps

Sniff.

---

### Post by ubuntu_demon on 2005-04-01
[QUOTE=Sniffer]Hi

Yes the Intel extreme graphics is supported on boot, so you don't have to do anything to activate 3D support, wich is great :)

Tough this integrated card didn't realize my expectations.....i knew from the beggining that it wasn't very good.....but it comes to be slow #-o  when emulating games and so on as you can see on the detailed post above.


I'm tryng now the new version of ubuntu and hope to test it soon with XORG, let's see if the card behave better......

I have an laptop with it and my motherboard it's from Intel (HP) with intel chipset ofcourse....

Hope it helps

Sniff.[/QUOTE]
 What about 2d ? Everything ok there ?

What motherboard do you have ?

---

### Post by Sniffer on 2005-04-11
Yes on 2D everything is ok. :smile: 

To be honest i don't know the Motherboard of my laptop :? 

I have just bought an HP ZE4900 and to do my bios update i just have to download one file from HP.... so i really don't need to know the model, tough and i have said as above it's an Intel motherboard.

---

### Post by ubuntu_demon on 2005-04-11
[QUOTE=Sniffer]Yes on 2D everything is ok. :smile: 

To be honest i don't know the Motherboard of my laptop :? 

I have just bought an HP ZE4900 and to do my bios update i just have to download one file from HP.... so i really don't need to know the model, tough and i have said as above it's an Intel motherboard.[/QUOTE]
 thnx!

---

