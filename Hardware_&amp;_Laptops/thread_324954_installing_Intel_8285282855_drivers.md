---
title: "installing Intel 82852/82855 drivers"
date: 2006-12-24
forum: Hardware &amp; Laptops
---

### Post by gekkothelizard on 2006-12-24
Hi!

I need some help from an experienced linux user. My problem is, I want to make my Kubuntu Edgy use my video card fully. The default 810i driver isn't bad, it even does some thing in hw (transparency), but opengl is still unsuable. I have seen a seen a section in the unofficial guide, and did what it said (downloaded some rpm from intel's site, converted it with alien, then installed it) but nothing seemed to happen. I checked it in System Settings and it still showed the default 810i driver. So I went to Intel's website and found the driver sources here: [here]("http://downloadfinder.intel.com/scripts-df-external/Detail_Desc.aspx?agr=Y&ProductID=922&DwnldID=8203&strOSs=39&OSFullName=Linux*&lang=eng"). Then I apt-geted build-essential, and kernel-package. But when I try to compile the driver with it's install.sh script it says this:
> 
Compiling new agpgart module...

ERROR: AGPGART module did not compile

Compiling DRM module...

ERROR: Kernel modules did not compile

The DRI drivers can not be installed without the latest kernel modules.
Installation will be aborted. See the dri.log file for information on
what went wrong.


From the dri.log it's obvious that it found the kernel modules, but something (and here is the problem) went wrong. I don't have a clue how to fix this, so some plz help me. The dri.log is attached. Thanks for your help!

---

### Post by foolsh on 2006-12-26
you may have to run install.sh as root

sudo ./install.sh

---

### Post by DarkN00b on 2006-12-26
I can't tell you how many times I've hosed my installs of Dapper and Edgy by trying to install the latest Intel driver. I've decided that I don't need them. Everything works like it is supposed to for me with the generic driver.

BTW -for users of Intel or other integrared graphics systems- if you ever run glxgears and get the following:
```
libGL warning: 3D driver claims to not support visual 0x4b
```

That just means your graphics adapter does not support color modes above 24 bit.

---

### Post by gekkothelizard on 2006-12-28
yes, everything works with the generic driver, except 3d. i think opengl support is a pretty basic thing, and it's very annoying knowing that the card supports it, AND there IS a driver for linux, i just can't install it. I think this would be very useful for anyone having an intel video card, so i'm asking again for someone more experienced to get a go at this one. tnx

---

### Post by DarkN00b on 2006-12-28
Direect rendering works perfectly well on my laptop, at least as well as it did in Windows. I have no problem running GL accelerated games and programs, including Beryl 0.1.4 - XGL snow works, but not rain. I'm using the generic Mesa driver as can be seen below.

My video system:
```
Section "Device"
	Identifier	"Intel Corporation 82852/855GM Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

```

Generic Drivers:
```
darkn00b@laptop:~$ glxinfo
name of display: :0.0
libGL warning: 3D driver claims to not support visual 0x4b
display: :0  screen: 0
**direct rendering: Yes**
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
OpenGL renderer string: Mesa DRI Intel(R) 852GM/855GM 20050225
OpenGL version string: 1.3 Mesa 6.5.1
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_point_parameters, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
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
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle, 
    GL_EXT_vertex_array, GL_3DFX_texture_compression_FXT1, 
    GL_APPLE_client_storage, GL_APPLE_packed_pixels, 
    GL_ATI_blend_equation_separate, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_MESA_window_pos, 
    GL_NV_blend_square, GL_NV_light_max_exponent, GL_NV_texture_rectangle, 
    GL_NV_texgen_reflection, GL_NV_vertex_program, GL_NV_vertex_program1_1, 
    GL_OES_read_format, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays
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
0x4b 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon
```

---

### Post by hikaricore on 2006-12-28
I have never been able to properly install the driver from intel's website, but when I was using my integrated card, I had little trouble with the i810 driver included with dapper or edgy.  Your best bet is to run it in 16 bit color mode, which limits you on certain games, which will crash without 24 bit colour available but yea with that kinda chipset it can be rough getting most things to run properly.  Best bet is to get a decent nvidia chipset type video card, I know it's not the happiest decision you'll probably want to make, but it's done wonders for my system, and hell I install a pci card 6200 gforce series due to lack of an agp slot.  The intel chipset can work but it's an uphill battle sorry to say.  :/

---

### Post by gekkothelizard on 2007-01-06
cool, and you didn't have to do anything for this? plz write me what system do you have and exactly which version of ubuntu

---

### Post by DarkN00b on 2007-01-06
> **gekkothelizard said:**
> cool, and you didn't have to do anything for this? plz write me what system do you have and exactly which version of ubuntu
I'm running Edgy Eft v6.10. My system is as follows:

HP Ze2000 generic laptop w/ 12cell battery
258 MB memory
40 GB HD (4200 rpm)
Intel 82852/855 GM/GME graphics chipset.

I must say that *everything* on this system was detected and correctly set up by Edgy. The only post-install fixing I had to do was to install the firmware for my ZD1201 wireless dongle. I had a complete working system in less than an hour. I defy anyone to do that with WinXP.

So, I didn't do anything special except install Edgy (with its built in AIGLX), and install Beryl.

I used the instructions at the [Edgy/AIGLX wiki]("http://wiki.beryl-project.org/wiki/Install/Ubuntu/Edgy/AiGLX"). As long as you follow the instructions there Beryl will work, provided your video system is working correctly.

<.02>One more thing... every time I have tried to compile the Intel driver from source it has completely ruined my video. I had to do a completely new install of my OS to fix it because nothing I tried was able to fix it after that. You're much better off sticking with the default i810 driver IMO.</.02>

---

### Post by gekkothelizard on 2007-01-07
i think the answer lies with beryl. i didn't install that one, so i'll give it a try, hope it will work for me also, cause i'm using kde. thnx for ur help!

---

