---
title: "radeon x600 opensource driver trouble 3d support"
date: 2009-10-17
forum: Installation &amp; Upgrades
---

### Post by vildanovak on 2009-10-17
please has anybody a clue how to config xorg.conf to get 3d acceleration working with opensource radeon driver and ati mobility radeon x600?
I would love to update to 9.10 and have installed it on one partitition, but 3d support isn't working(although compiz was working out of the box), and it seems that no matter what I set up, it still uses mesa drivers.
I have a thinkpad z60m, with pentium m, x600 128mb ram, Currently the main system is 8.10 with fglrx.
please don't tell me 'it should work', on the ubuntu wiki there is written that my card should already have 3d support from the opensource driver. 
I tried various xorg.conf's  first was the one recommended on ubuntu wiki, that and more others didn' start X at all, e.g. this one(last of many combinations I tried):
```
Section "Device"
        Identifier      "Radeon Mobility X600"
        Driver          "radeon"
        Option          "AccelMethod"    "XAA"  
        Option          "EnablePageFlip" "true" 
        Option          "TripleBuffer"   "true" 
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Radeon Mobility X600"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1680x1050" "1440x900" "1024x768"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Section "DRI"
        Mode 0666
EndSection
        
Section "Extensions"
        Option "Composite" "Enable"
EndSection
```this one is the current, it starts X, compiz run(although I don't use it and for 3d testing I switch it off), but 3d doesn't.
```

Section "Files"
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "Monitor"
    Identifier   "Configured Monitor"
EndSection

Section "Device"
    Identifier  "Configured Video Device"
    Driver      "radeon"
EndSection

Section "Screen"
    Identifier "Default Screen"
    Device     "Configured Video Device"
    Monitor    "Configured Monitor"
    DefaultDepth     24
EndSection

```here is my glxinfo output:

```
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 (RV380 3150) 20090101 x86/MMX/SSE2 TCL
OpenGL version string: 1.5 Mesa 7.6
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_occlusion_query, GL_ARB_point_parameters, GL_ARB_shadow, 
    GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_MESAX_texture_float, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_array_bgra, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_blend_color, GL_EXT_blend_equation_separate, 
    GL_EXT_blend_func_separate, GL_EXT_blend_logic_op, GL_EXT_blend_minmax, 
    GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, GL_EXT_convolution, 
    GL_EXT_copy_texture, GL_EXT_draw_range_elements, GL_EXT_fog_coord, 
    GL_EXT_gpu_program_parameters, GL_EXT_histogram, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels, 
    GL_EXT_point_parameters, GL_EXT_polygon_offset, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_shadow_funcs, GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, GL_EXT_vertex_array, 
    GL_EXT_vertex_array_bgra, GL_APPLE_packed_pixels, 
    GL_ATI_blend_equation_separate, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_ATI_separate_stencil, 
    GL_IBM_multimode_draw_arrays, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_MESA_window_pos, 
    GL_NV_blend_square, GL_NV_light_max_exponent, GL_NV_texture_rectangle, 
    GL_NV_texgen_reflection, GL_NV_vertex_program, GL_OES_read_format, 
    GL_SGI_color_matrix, GL_SGI_color_table, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays

8 GLX Visuals
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x69 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x6a 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x6b 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x6c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x6d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x60 32 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 Ncon

8 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x61  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x62  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x63  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x64  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x65  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x66  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x67  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x68  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow

```Any help would be appreciated.I am 3d artist and a computer without 3d support doesn't make any sense for me.

---

### Post by Mark Phelps on 2009-10-17
The open source radeon drivers are improving all the time, but despite whay you may have read from rumour sources, there are NO improved restricted drivers for ATI cards in Ubuntu 9.10.

So, what limited acceleration you already get with the Mesa drivers is most probably all you're going to be able to achieve.

If you want 3D acceleration, you'll need to upgrade to a cards who's restricted drivers provide that feature -- in the case of ATI, this means one of the newer HD 3X, 4X, or 5x cards.

---

### Post by vildanovak on 2009-10-17
Thanks for your reply, but there's a little misunderstanding:
I didn't say anything about restricted drivers, I know the situation about them and am not expecting anything and all my mentioned efforts are about opensource drivers. 
I guess you are actually advising me to update graphics card in my laptop(?) to be able to run restricted drivers? Besides it's probably not possible with a laptop, I would never ever buy anything from ati again.

to repeat it:
I was just saying I expected at least some 3d acceleration with the opensource driver, since it's in ubuntu wiki([https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) , under 'good 3d support'), but I am not getting any 3d acceleration at all. I guess this functionality has to be enabled somehow with xorg.conf, and don't know how. And that was the scope of my question.

If somebody with similar card would send his xorg.conf it would be VERY cool :guitar:. thanks

---

### Post by vildanovak on 2009-10-18
I have still no progress with this one don't have a clue why glxinfo writes about mesa when radeon driver is installed. Is there anybody with some similar card here **please?**Or anybody who understands the situation about opensource drivers?

Bad news is - my computer started to hang randomly when running ogl applications, and that even on 8.10! this never happened before. Is it possible the 9.10 installation's driver somehow messed up the card? The crashes are hard, no way to restart X with ctrl alt backspace, just hard turning off and on :(

---

### Post by Mark Phelps on 2009-10-18
Sorry, didn't catch that your PC was a laptop...

But, apart from the documentation on Radeon drivers, which lists lots of options (do "man Radeon" in a terminal), since you can't change your graphics card, there's little else you can do.

---

### Post by ownsuall on 2009-11-12
I have a mobility radeon x600 card and can't find a driver that works. But anyway heres my xorg.conf

---

