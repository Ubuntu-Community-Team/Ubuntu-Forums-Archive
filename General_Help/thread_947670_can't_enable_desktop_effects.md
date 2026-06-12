---
title: "can't enable desktop effects"
date: 2008-10-14
forum: General Help
---

### Post by PoopyTheJ on 2008-10-14
Ok, running Gutsy on an ATI Radeon HD 3850, I've installed the graphics driver I think, however my system doesn't seem to recognize my video card. When I try to enable compiz effects I get the cannot be enabled message. Movies play fine and I get a constant 90fps with no variation in Warsow. Compiz-check shows...

:~$ compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 7.10
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc Unknown device 9505
 Driver in use:         fglrx
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]


and sudo lspci shows...

00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IB (ICH9) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IB (ICH9) 2 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 9505
01:00.1 Audio device: ATI Technologies Inc Unknown device aa18
02:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)
03:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6121 SATA II Controller (rev b2)


What the heck is going on?

---

### Post by LowSky on 2008-10-14
what happens if you hit Alt+F2 and type in the command box

```
compiz --replace
```

---

### Post by PoopyTheJ on 2008-10-14
Alt+F2 and running that command the screen flickers. Running that command in terminal gives me...

Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity

---

### Post by PoopyTheJ on 2008-10-16
dunno if this means anything but my resolution won't change either, it defaults to 2048x1600 or so and when I change it to 1600x1200 it doesn't change, if I restart X it'll change sometimes, but otherwise it still shows 2048x1600, doesn't even flicker when I try to change the resolution, does nothing at all.

---

### Post by Crafty Kisses on 2008-10-16
What are the results of this command?
```
glxinfo
```

---

### Post by PoopyTheJ on 2008-10-16
:~$ glxinfo
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
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, 
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 3850
OpenGL version string: 2.1.7979 Release
OpenGL extensions:
    GL_AMDX_vertex_shader_tessellator, GL_AMD_performance_monitor, 
    GL_AMD_texture_texture4, GL_ARB_depth_texture, GL_ARB_draw_buffers, 
    GL_ARB_fragment_program, GL_ARB_fragment_shader, GL_ARB_multisample, 
    GL_ARB_multitexture, GL_ARB_occlusion_query, GL_ARB_pixel_buffer_object, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shader_objects, 
    GL_ARB_shading_language_100, GL_ARB_shadow, GL_ARB_shadow_ambient, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_float, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_window_pos, GL_ATI_draw_buffers, GL_ATI_envmap_bumpmap, 
    GL_ATI_fragment_shader, GL_ATI_meminfo, GL_ATI_separate_stencil, 
    GL_ATI_shader_texture_lod, GL_ATI_texture_compression_3dc, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_float, GL_EXT_abgr, 
    GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_equation_separate, 
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_compiled_vertex_array, GL_EXT_copy_texture, 
    GL_EXT_depth_buffer_float, GL_EXT_draw_range_elements, GL_EXT_fog_coord, 
    GL_EXT_framebuffer_blit, GL_EXT_framebuffer_multisample, 
    GL_EXT_framebuffer_object, GL_EXT_gpu_program_parameters, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_depth_stencil, 
    GL_EXT_packed_float, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texgen_reflection, GL_EXT_texture3D, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, 
    GL_EXT_texture_shared_exponent, GL_EXT_vertex_array, GL_KTX_buffer_region, 
    GL_NV_blend_square, GL_NV_texgen_reflection, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_WIN_swap_hint, 
    WGL_EXT_swap_control

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x2e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x30 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x31 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x32 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x33 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x34 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x35 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x36 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x37 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x38 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x39 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x3a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x3b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x3e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x3f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x40 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x41 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x42 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x43 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x44 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x45 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x46 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x47 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x48 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x49 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x4a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x4b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x4c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x4d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x4e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x4f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x50 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x51 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x52 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x53 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x54 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x55 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x56 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x57 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x58 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x59 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x5a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x5b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x5e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x5f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x60 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x61 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x62 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x63 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x64 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x65 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x66 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x67 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x68 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x69 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x6a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x6b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x6c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x6d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x6e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x6f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x70 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x71 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x72 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x88 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

---

### Post by LOTM on 2008-10-17
I'm having a very similar problem except with a Nvidia 7600GT, whenever I try to enable Visual Effects, it says it can't find the composite extension. 

When I run compiz --replace in terminal I get:
:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 02:00.0 0300: 10de:0391 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: not present. 
aborting and using fallback: /usr/bin/metacity

I'd really like to fix this, since there's a lot of programs that seem to require this composite extension.

---

### Post by PoopyTheJ on 2008-10-17
grrr there's gotta be something I can do, or someone who's had this similiar problem and resolved it, I could get the effects to enable prior to reinstalling Ubuntu now on this install they don't work.

LOTM, did you go through Synaptics and install the proper Compiz stuff? I'm not 100% sure I'm not missing something on mine that perhaps I don;t have the right packages installed.

Below is a screenshot of what I've installed through Synaptics...

[IMG]http://img235.imageshack.us/img235/3839/screenshot10sg2.png

---

### Post by Gnorrogh on 2008-10-23
This is getting quite annoying, I get the same error as the thread op. Does anyone have a solution? I've tried everything on the forum that I've found so far, and still no progress.

---

### Post by propwashz on 2008-10-24
I'm having the same problem -unable to enable compiz (effects) or change screen resolution -- except,I have integrated Intel graphics instead of ATI or Nvidia card...everything was working fine under Hardy.Everything else works fine with Intrepid except graphics glitch...

---

### Post by Gnorrogh on 2008-10-24
Well, I'm using Hardy, and I can change screen resolution, but I just can't turn on desktop effects.. :(

---

### Post by Gnorrogh on 2008-10-24
Bumping a bit, and telling people that this seems to be a openGL problem, since I can't play games with openGL graphics.

```
empty@empty-desktop:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation GeForce 7600 GT (rev a2)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [FAIL]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [FAIL]
 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: Unable to detect maximum 3D texture size 

```

---

### Post by Gnorrogh on 2008-10-25
Mine is working now, I updated to Intrepid, and now it's working! :D

---

### Post by LouisZepher on 2008-10-25
I have the same problem.  I can adjust my resolution, but can't enable desktop effects.  I've tried everything discussed both in this thread, and others, but nothing seems to work.  I know my hardware is compatible, as this problem started earlier this week, and I've had most of Compiz's effects working.  I've tried reinstalling Hardy, and have upgraded to Intrepid and still nothing works.  However, I can boot from my 8.04 LiveCD, and enable desktop effects from the CD environment, but once I install and apply updates, it kills whatever driver or file needed for effects to load.

---

### Post by Nuetouch on 2008-10-26
Here is my two cents, I'm using ver 8.04 and running on a P4 2.5 Mhz with 384 ram, and 128 Nvidia FX5200, and my effects seem to be working in full force, before I had a lower end card and couldn't get any effects. Today I've just installed the compiz-settings package, and the install went well, and I now have access to all the advance special effects settings, although I haven't tried the cube just yet. Been using Ubuntu for about 2 months, still on a learning curve...hope this helps...

---

### Post by PoopyTheJ on 2008-10-31
Updated to 8.04 from Gutsy and now I can use the desktop effects. Totally bizarre and I have no idea what changed except now I can enable my desktop effects. I did find that something was wierd about my driver install through envy with gutsy, but I did a manual install following the ubuntu wiki and everything is running fine using the 8.10 Catalyst drivers. Totally at a loss, just glad it's working.

---

### Post by Tralce on 2009-02-01
I'm having exactly the same problem with Intrepid. Here's the funny thing though: it was working fine earlier today. I've had this issue in the past with Gutsy. I installed VirtualBox and instantly the visual effects died. However I didn't install anything (I removed a few useless packages today however) and suddenly desktop effects were gone. 

Any ideas? 

```
tralce@ubuntu:~$ sudo compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: present. 
Software rasterizer detected, abortingaborting and using fallback: /usr/bin/metacity 

```

```
tralce@ubuntu:~$ glxinfo
name of display: :0.0
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string: 2.1 Mesa 7.2
OpenGL shading language version string: 1.10
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader, 
    GL_ARB_half_float_pixel, GL_ARB_imaging, GL_ARB_multisample, 
    GL_ARB_multitexture, GL_ARB_occlusion_query, GL_ARB_pixel_buffer_object, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shader_objects, 
    GL_ARB_shading_language_100, GL_ARB_shadow, GL_ARB_shadow_ambient, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_compiled_vertex_array, GL_EXT_convolution, 
    GL_EXT_copy_texture, GL_EXT_depth_bounds_test, GL_EXT_draw_range_elements, 
    GL_EXT_framebuffer_object, GL_EXT_framebuffer_blit, GL_EXT_fog_coord, 
    GL_EXT_gpu_program_parameters, GL_EXT_histogram, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels, 
    GL_EXT_paletted_texture, GL_EXT_pixel_buffer_object, 
    GL_EXT_point_parameters, GL_EXT_polygon_offset, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_shadow_funcs, GL_EXT_shared_texture_palette, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, 
    GL_EXT_vertex_array, GL_APPLE_packed_pixels, GL_APPLE_vertex_array_object, 
    GL_ATI_blend_equation_separate, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_ATI_fragment_shader, 
    GL_ATI_separate_stencil, GL_IBM_multimode_draw_arrays, 
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, 
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_program_debug, 
    GL_MESA_resize_buffers, GL_MESA_texture_array, GL_MESA_ycbcr_texture, 
    GL_MESA_window_pos, GL_NV_blend_square, GL_NV_fragment_program, 
    GL_NV_light_max_exponent, GL_NV_point_sprite, GL_NV_texture_rectangle, 
    GL_NV_texgen_reflection, GL_NV_vertex_program, GL_NV_vertex_program1_1, 
    GL_OES_read_format, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGI_texture_color_table, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod, GL_SGIX_depth_texture, GL_SGIX_shadow, 
    GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays

3 GLX Visuals
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x6a 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None

32 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x6b  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x6c  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x6d  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x6e  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x6f  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  8  0  0  0  0  0 0 None
0x70  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  8 16 16 16 16  0 0 Slow
0x71  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  8  0  0  0  0  0 0 None
0x72  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  8 16 16 16 16  0 0 Slow
0x73  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x74  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x75  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x76  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x77  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x78  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x79  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x7a  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x7b  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x7c  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x7d  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x7e  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x7f  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  8  0  0  0  0  0 0 None
0x80  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  8 16 16 16 16  0 0 Slow
0x81  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  8  0  0  0  0  0 0 None
0x82  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  8 16 16 16 16  0 0 Slow
0x83  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x84  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x85  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x86  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x87  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x88  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x89  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x8a  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow

```

---

### Post by jim.bauer10 on 2009-02-02
I'm having the same problem as Gnorrogh, except that I'm already on Intrepid so updating isn't an option for me.  I'm pretty sure that it's an openGL problem as well.  Repeated driver reinstallations haven't had any effect.  This all started for me when I had problems with my 180.22 driver update and went back the 177's.

```
jimbauer@ubuntu:~$ glxinfo
glxinfo: symbol lookup error: /usr/lib/libGLcore.so.1: undefined symbol: _nv000005gl
```

```
jimbauer@ubuntu:~/Desktop$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation GeForce 8500 GT (rev a1)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [FAIL]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [FAIL]
 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: Unable to detect maximum 3D texture size 

```

---

### Post by Triphys on 2009-02-10
I get the same "Can't enable desktop effects" message when trying to enable compiz in "Appearance" and when running "compiz" in terminal I get the following message:

```

triphys@triphys-school:~$ compiz
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity

```

When running "lspci | grep VGA" I get the following output:

```

03:00.0 VGA compatible controller: Matrox Graphics, Inc. MGA G200e [Pilot] ServerEngines (SEP1) (rev 02)

```

I'm running on a totally clean install of Ubuntu Intrepid.

---

### Post by Maxx730 on 2009-03-10
My laptop would run Compiz either until I used the code

SKIP_CHECKS=yes compiz

---

### Post by skalka on 2009-03-20
My problem is quite funny. I can run Compiz only if I put the fusion icon on startup with gnome-vm disabled. The Fusion Icon is useful if you need to switch between window managers but is slower on startup. So I would like to have my desktop with Compiz enabled without using the fusion icon, but if I try to activate desktop effects it says me that is not possible. I think something has to be loaded on startup but I can't understand what. Someone can help me? I'm under Intrepid with nvidia 8400M, I installed drivers with Ubuntu utility for restricted drivers.

---

### Post by sasaenator on 2009-04-04
ok,people!I had the same problem on my intrepid installation!I'm not sure,but I think the solution was in enabling 'random animations for all events' under ccsm -> animations -> Effect settings!hope this helps!off course you have to choose which animations you want to see!btw I have geforce mx440!

---

### Post by srikanth.janardhan on 2009-04-27
I am running Jaunty 9.04 (amd64 version), Intel Pentium 4 3.06GHz and ATI Radeon Xpress 200.

I had installed Jaunty on my Desktop yesterday night. Even I had the same problem in enabling desktop effects. So, I tweaked my config file so that the desktop effects worked. Before, my config file was as follows:

> Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSectionI just added a Driver "radeon" and some options to the Device Section and restarted the display (Ctrl+Alt+Bksp and log-in in the text terminal and do: > sudo /etc/init.d/gdm restart, the display restarts) and voila, all of the effects were working so fine. I had also tried "vesa" for the driver, but was not working then. It also worked for "ati", but I preferred Radeon. The modified xorg.conf is as follows:
> Section "Device"
    Identifier    "Configured Video Device"
    Driver        "radeon"
    Option          "AccelMethod"    "EXA"  
        Option          "EnablePageFlip" "true" 
        Option          "TripleBuffer"   "true" 
        Option          "DynamicClocks"  "on
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSectionHope this helps someone.

---

### Post by biometricsguy on 2009-06-21
So I've encountered a bizarre workaround for my compiz problem.

A little background first...

Compiz stopped working for me a couple of days ago after letting the update manager do it's thing.  I really wish I could remember what it was that was being installed. :-(  Whatever is was, it really messed up my system.  In fact, I would get a blank screen when attempting to log into ubuntu.  I was able to fix that problem by logging in under the old kernel and installing the proprietary ATI drivers again and re-initializing.

However, after disabling compiz I couldn't re-enable it again.  When I run compiz-check I get the following:
> Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RV730XT [Radeon HD 4670]
 Driver in use:         fglrx
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 

Which, I guess means something happened with the rendering method?? 

Anyway, I was able to find a workaround which has left me more confused than ever.  I was able to get compiz working again by doing the following:

[LIST=1]
[*]Close all open windows.
[*]Open Appearance -> Visual Effects Tab.
[*]Move this window into the bottom right corner.
[*]Open a terminal and type: ```
compiz --replace
```
[*]This won't work and it will leave the terminal hanging.  I pressed Ctrl-C to get out of it.
[*]This will leave my computer in a half-broken state.  The terminal will get moved (and locked) into the top left corner and become unresponsive.  The computer in general will also be unresponsive.  However, the visual effects tab will still be showing.  If I then click the radio button to enable compiz, it will work this time and the computer will return to its normal, responsive state.
[/LIST]
Compiz will continue to work, even after restarting.  However, if I disable compiz again for whatever reason, I have to repeat this process to get it working again.  Anyone have any thoughts about this?

---

### Post by boams on 2009-08-06
I'm having the same problem too - I have an Integrated Intel 8245G Graphics Chip and whenever I try to enable effects I get an error saying 'Unable to apply desktop settings'. Another thing to try if you haven't come across this, is to run the Compiz Compatibility Test, see URL:
 
[http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)
 
When I ran the test it said something along the lines of my graphics card being blacklisted, not sure what this means?? 
 
Good Luck guys!!

---

### Post by wallybescotty on 2009-09-12
Ok Here Is My Trouble, I Have Ubuntu 9.04 Jackalope, and I Installed A Theme And Some Apps And I Had Extra Visuals Working But Then I Filled My HDD Up lol And Did A Restart And Fixed That Problem But When It Was All Said And Done, My Extra Settings Dont Work Any More And Now I Have 4 Workspaces Instead Of 2 Witch Is Fine But The Little Switcher Thing Doesnt SHow Up Any More And I My Screen Goes Ballistic When I Try To Enable Extra Settings I was Not Using Advanced Compiz, And Then I Tried It And Thats When All This Started Happening, Now My Ubunto Startup Loader Says Ubuntu Studio And My Extra Effects Do Not Work lol Im New To Linux Can Anyone Help me,:confused:

U Can Email Me _**wallybescotty@gmail.com**_ I would really appreciate it if anyone can help me fix my ubuntu without losing my themes or programs i have instarlled thanx

---

### Post by P4man on 2009-09-12
> **boams said:**
> I'm having the same problem too - I have an Integrated Intel 8245G Graphics Chip and whenever I try to enable effects I get an error saying 'Unable to apply desktop settings'. Another thing to try if you haven't come across this, is to run the Compiz Compatibility Test, see URL:
 
[http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)
 
When I ran the test it said something along the lines of my graphics card being blacklisted, not sure what this means?? 
 
Good Luck guys!!

Kind of a late reply, but its really what is says there: your videocard is blacklisted, means its on a list of cards for which compiz can't be enabled because the card is known to give serious problems when you do enable it.

The good news I guess, is that I believe in the upcoming version of ubuntu (karmic) a lot of problems with intel onboard videocards are solved. Its got a new kernel with new built-in intel drivers, so when it comes out, worth a try.

---

### Post by cloudscream on 2009-10-06
In Karmic beta 64-bit, Intel GM965, I can enable compiz--PARTIALLY. After I did a reboot, compiz was automatically disabled and I can't re-enable unless I do another reboot. It's very annoying.

---

### Post by mastervon on 2009-10-08
hi guys, im a noob in Ubuntu Linux. i started using it for 3 days now. i'm using Ubuntu 9.04 and i got the same problem, i can't enable my desktop effects. im using HP Pavilion dv7 entertainment notebook Pc, AMD Turion x2 dual-core mobile RM-72 2.10Ghz, 4GB RAM, 64-bit OS and a display adapter ATI Radeon HD 3200. i tried installing the ATI Catalyst Control Center in Ubunto using the **Application --> Add/Remove Program** and same problem occurred. can anyone help me.. :(

---

### Post by P4man on 2009-10-11
> **mastervon said:**
> hi guys, im a noob in Ubuntu Linux. i started using it for 3 days now. i'm using Ubuntu 9.04 and i got the same problem, i can't enable my desktop effects. im using HP Pavilion dv7 entertainment notebook Pc, AMD Turion x2 dual-core mobile RM-72 2.10Ghz, 4GB RAM, 64-bit OS and a display adapter ATI Radeon HD 3200. i tried installing the ATI Catalyst Control Center in Ubunto using the **Application --> Add/Remove Program** and same problem occurred. can anyone help me.. :(

You have to install driver,not just the ccc. Go to system > adminstration > hardware drivers. It should prompt you to install ATI drivers. That said, even the opensource drivers which should already be in use, ought to enable compiz. What message do you get when you try enabling it?

---

### Post by hantechbl on 2009-10-11
Compiz-check was able to disable my lock on the compi-effect except it had a very bad side effect....  X would crash,  I ended up having to drop to a root shell and purge compiz and all desktop effects. It's not worth disabling the lock.

---

### Post by FrostyC on 2009-10-21
> **biometricsguy said:**
> So I've encountered a bizarre workaround for my compiz problem.

A little background first...

Compiz stopped working for me a couple of days ago after letting the update manager do it's thing.  I really wish I could remember what it was that was being installed. :-(  Whatever is was, it really messed up my system.  In fact, I would get a blank screen when attempting to log into ubuntu.  I was able to fix that problem by logging in under the old kernel and installing the proprietary ATI drivers again and re-initializing.

However, after disabling compiz I couldn't re-enable it again.  When I run compiz-check I get the following:


Which, I guess means something happened with the rendering method?? 

Anyway, I was able to find a workaround which has left me more confused than ever.  I was able to get compiz working again by doing the following:

[LIST=1]
[*]Close all open windows.
[*]Open Appearance -> Visual Effects Tab.
[*]Move this window into the bottom right corner.
[*]Open a terminal and type: ```
compiz --replace
```
[*]This won't work and it will leave the terminal hanging.  I pressed Ctrl-C to get out of it.
[*]This will leave my computer in a half-broken state.  The terminal will get moved (and locked) into the top left corner and become unresponsive.  The computer in general will also be unresponsive.  However, the visual effects tab will still be showing.  If I then click the radio button to enable compiz, it will work this time and the computer will return to its normal, responsive state.
[/LIST]
Compiz will continue to work, even after restarting.  However, if I disable compiz again for whatever reason, I have to repeat this process to get it working again.  Anyone have any thoughts about this?

OMG WTF? This worked! After tons & tons of troubleshooting & all kinds of hassles, THIS WEIRD SOLUTION ACTUALLY WORKED!!! Thanks biometricsguy!

[CENTER][IMG]http://www.unity.i8i.co.uk/forum/images/smiley_bowdown.gif[/IMG][IMG]http://img23.imageshack.us/img23/5062/smileytwothumbsup.gif[/IMG] [IMG]http://img14.imageshack.us/img14/3895/animatedbravosmiley.gif[/IMG] [IMG]http://img23.imageshack.us/img23/5062/smileytwothumbsup.gif[/IMG][IMG]http://www.unity.i8i.co.uk/forum/images/smiley_bowdown.gif[/IMG][/CENTER]

---

### Post by Click-dot-Bejo on 2010-04-18
Wanna see some SS :p

---

### Post by rudihawk on 2010-04-18
> **FrostyC said:**
> OMG WTF? This worked! After tons & tons of troubleshooting & all kinds of hassles, THIS WEIRD SOLUTION ACTUALLY WORKED!!! Thanks biometricsguy!

[CENTER][IMG]http://www.unity.i8i.co.uk/forum/images/smiley_bowdown.gif[/IMG][IMG]http://img23.imageshack.us/img23/5062/smileytwothumbsup.gif[/IMG] [IMG]http://img14.imageshack.us/img14/3895/animatedbravosmiley.gif[/IMG] [IMG]http://img23.imageshack.us/img23/5062/smileytwothumbsup.gif[/IMG][IMG]http://www.unity.i8i.co.uk/forum/images/smiley_bowdown.gif[/IMG][/CENTER]

or, you could just type 
```
nohup compiz --replace
```

Which will then allow you to close your terminal window without mucking up your system.

---

### Post by crasbelize on 2010-07-11
> **FrostyC said:**
> OMG WTF? This worked! After tons & tons of troubleshooting & all kinds of hassles, THIS WEIRD SOLUTION ACTUALLY WORKED!!! Thanks biometricsguy!

[CENTER][IMG]http://www.unity.i8i.co.uk/forum/images/smiley_bowdown.gif[/IMG][IMG]http://img23.imageshack.us/img23/5062/smileytwothumbsup.gif[/IMG] [IMG]http://img14.imageshack.us/img14/3895/animatedbravosmiley.gif[/IMG] [IMG]http://img23.imageshack.us/img23/5062/smileytwothumbsup.gif[/IMG][IMG]http://www.unity.i8i.co.uk/forum/images/smiley_bowdown.gif[/IMG][/CENTER]


Well...i tried everything and mine just won't go into the Extra: mode under Visual Effects. 

I have a Geforce FX5200, driver 173 install and enable. 
got compiz from : [http://www.hackourlives.com/install-compiz-fusion-and-emerald-in-ubuntu-10-04-lucid-lynx/]("http://www.hackourlives.com/install-compiz-fusion-and-emerald-in-ubuntu-10-04-lucid-lynx/")

Ubuntu 10.04

I have twinview working....the cool effects would be nice...

Please Help?????

---

### Post by langer123 on 2010-12-02
Hi All

I'm having problems enabling desktop effects also.

I have a Dell Studio XPS 1640. I have Ubuntu 10.10 installed inside Virtual Box.

Could it be due to it been installed under virtual box?

---

### Post by Sillyname on 2011-02-28
hpowner@ubuntu:~$ compiz --replace
compiz (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png

this is what I get...:(

themes/Human/ubuntu.png does not exist and create new folder is greyed-out!

---

### Post by Sillyname on 2011-03-03
I fixed it!  Compiz works now!

---

### Post by iFuzo on 2011-03-06
EDIT: Sorry didnt mean to bump!

---

### Post by maddbaron on 2011-03-07
i can't enable desktop effects in maverick

---

### Post by cybuntu on 2011-05-15
you problem is not even half as bad as mine, i cant even FIND the effects tab :confused:

Version 11.4 (Natty Narwhal(Apparently))

---

### Post by spyd3r on 2011-05-26
have this exact same issue in 11.04
no visual effects tab

---

