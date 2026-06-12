---
title: "How to get compiz to work?"
date: 2008-10-14
forum: General Help
---

### Post by eternalnewbee on 2008-10-14
Greetings.
"No proprietary drivers in use on this system".
That's the message I get in Hardware Drivers".
Is it still possible to get compiz to work?

---

### Post by ajmorris on 2008-10-14
> **eternalnewbee said:**
> Greetings.
"No proprietary drivers in use on this system".
That's the message I get in Hardware Drivers".
Is it still possible to get compiz to work?


Hi again eternalnewbee :)

Can you please post the output of the following commands from a terminal:
```
sudo glxinfo
```
```
sudo lspci
```
```
compiz --replace &
```


AJ

---

### Post by eternalnewbee on 2008-10-14
Another question. How can I find out if my graphics allow direct rendering, or to tweak it for indirect rendering?

---

### Post by eternalnewbee on 2008-10-14
Hi AJ,

nadia@nadia:~$ sudo glxinfo
[sudo] password for nadia: 
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
0x22 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x3e 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

nadia@nadia:~$ sudo lspci
00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:0f.0 IDE interface: VIA Technologies, Inc. VT8251 AHCI/SATA 4-Port Controller
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 90)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8251 PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 PCI bridge: VIA Technologies, Inc. VT8251 Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8251 PCI to PCI Bridge
01:00.0 VGA compatible controller: VIA Technologies, Inc. UniChrome Pro IGP (rev 01)
02:00.0 PCI bridge: VIA Technologies, Inc. VT8251 PCIE Root Port
02:00.1 PCI bridge: VIA Technologies, Inc. VT8251 PCIE Root Port
02:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller
05:08.0 Multimedia audio controller: Yamaha Corporation YMF-744B [DS-1S Audio Controller] (rev 02)

nadia@nadia:~$ compiz --replace &
[1] 6753
nadia@nadia:~$ Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity

---

### Post by ajmorris on 2008-10-14
> **eternalnewbee said:**
> Another question. How can I find out if my graphics allow direct rendering, or to tweak it for indirect rendering?

Depends on what card you have, and if the new method that hardy uses for xorg.conf allows proper configuration without re-writing the whole thing.

---

### Post by ajmorris on 2008-10-14
ic... Direct Rendering is not active... and you have a VIA graphics chip, which is why no propriety drivers were found for your hadware...
Can you post the contents of your /etc/X11/xorg.conf file please.

AJ

---

### Post by eternalnewbee on 2008-10-14
In Main Menu > Hardware Tools > Sysinfo > Hardware > Graphic Card it says:
VGA compatible controller
VIA technologies, Inc. UniChrome Pro IGP (rev1) (prog-if 00 [VGA controller[)
Subsystem: ASUSTeK Computer Inc. Unknown device 3344

---

### Post by ajmorris on 2008-10-14
> **eternalnewbee said:**
> In Main Menu > Hardware Tools > Sysinfo > Hardware > Graphic Card it says:
VGA compatible controller
VIA technologies, Inc. UniChrome Pro IGP (rev1) (prog-if 00 [VGA controller[)
Subsystem: ASUSTeK Computer Inc. Unknown device 3344

yep, i got that from lspci ;)

Compiz is very difficult with VIA cards, and sometimes will not work.
However, try the following:
```
sudo aptitude install xserver-xorg-video-unichrome
```

then run ```
gksudo displayconfig-gtk
```
and change your X driver from mesa, to via (alternatively you can add "driver    via" to the relevant driver section of xorg.conf)

You may also need to add via to the list of whitelisted cards for compiz.

Then restart X and check if compiz is working again:
instead of just trying compiz --replace &  you might also like to try these paramaters:
```
compiz --sm-disable ccp --replace &
```


AJ

---

### Post by eternalnewbee on 2008-10-14
and change your X driver from mesa, to via (alternatively you can add "driver via" to the relevant driver section of xorg.conf)

You may also need to add via to the list of whitelisted cards for compiz.
______________________________________________________________________________________

Is this the one I need?

---

### Post by eternalnewbee on 2008-10-14
Btw, I don't know how to add "driver via" to the relevant driver section of xorg.conf)

and add via to the list of whitelisted cards for compiz...

---

### Post by eternalnewbee on 2008-10-15
I tested several drivers and they all failed. Does that mean I can't run compiz?

---

### Post by eternalnewbee on 2008-10-15
nadia@nadia:~$ compiz --sm-disable ccp --replace &
[1] 7193
nadia@nadia:~$ Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

AJ, I guess this means I can't run compiz. Right?:(

---

### Post by ajmorris on 2008-10-15
A lot of VIA chips are incapable of running compiz... but yes, that screenshot earlier is what you wanted to select as your driver... try adding via to the whitelisted drivers in /usr/bin/compiz

Also, try setting your X11 driver to AIGLX also... (and remember, after changing any settings related to any X settings, you must restart X for them to take effect (ctrl+alt+backspace))  Unfortunately, if this does not work, your VIA chips is probably not compatible with compiz and will have to stick with xcompmgr for your composite needs :(


AJ

---

### Post by eternalnewbee on 2008-10-15
> **ajmorris said:**
> A lot of VIA chips are incapable of running compiz... but yes, that screenshot earlier is what you wanted to select as your driver... try adding via to the whitelisted drivers in /usr/bin/compiz

Also, try setting your X11 driver to AIGLX also... (and remember, after changing any settings related to any X settings, you must restart X for them to take effect (ctrl+alt+backspace))  Unfortunately, if this does not work, your VIA chips is probably not compatible with compiz and will have to stick with xcompmgr for your composite needs :(


AJ

Thanks for your patience and advice AJ.
Guess my mum's just going to have to buy a decent graphic card...

---

