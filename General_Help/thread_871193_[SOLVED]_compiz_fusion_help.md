---
title: "[SOLVED] compiz fusion help"
date: 2008-07-26
forum: General Help
---

### Post by mikedemario17 on 2008-07-26
so i got a new card its a = Radeon 9250 128MB PCI graphics Card

> mike@mike-desktop:~$ sudo lshw -short | grep display
PCI (sysfs)  
/0/100/1e/9                     display     RV280 [Radeon 9200 PRO]
/0/100/1e/9.1                   display     RV280 [Radeon 9200 PRO] (Secondary)
mike@mike-desktop:~$ 

when i go to enable the restricted drivers... it says there are none and under the package manger it says compiz is already installed but the custom setting dont show up under visual effects and there is no advanced graphics setting under admin... whats wrong?

---

### Post by Prefix100 on 2008-07-26
whats the output of glxinfo?

---

### Post by david sousa on 2008-07-26
did you install compiz control panel?

sudo apt-get update 
sudo apt-get dist-upgrade 
sudo apt-get install compiz compizconfig-settings-manager

---

### Post by artir on 2008-07-26
sudo apt-get install compizconfig-settings-manager

TO get the advanced settings/Custom option.

---

### Post by mikedemario17 on 2008-07-26
> **Prefix100 said:**
> whats the output of glxinfo?
> mike@mike-desktop:~$ glxinfo
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 20060602 x86/MMX/SSE2 TCL
OpenGL version string: 1.3 Mesa 7.0.1
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_blend_color, GL_EXT_blend_equation_separate, 
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_compiled_vertex_array, GL_EXT_convolution, 
    GL_EXT_copy_texture, GL_EXT_draw_range_elements, GL_EXT_fog_coord, 
    GL_EXT_histogram, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array, 
    GL_APPLE_packed_pixels, GL_ATI_blend_equation_separate, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once, 
    GL_ATI_fragment_shader, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_MESA_window_pos, 
    GL_NV_blend_square, GL_NV_light_max_exponent, GL_NV_texture_rectangle, 
    GL_NV_texgen_reflection, GL_OES_read_format, GL_SGI_color_matrix, 
    GL_SGI_color_table, GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x26 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x27 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2e 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2f 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x31 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x7d 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon
mike@mike-desktop:~$ 
thats it

---

### Post by mikedemario17 on 2008-07-26
> **artir said:**
> sudo apt-get install compizconfig-settings-manager

TO get the advanced settings/Custom option.
wtf!
mike@mike-desktop:~$ sudo apt-get install compiz compizconfig-settings-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compiz is already the newest version.
E: Couldn't find package compizconfig-settings-manager
mike@mike-desktop:~$

---

### Post by fedex1993 on 2008-07-26
Also you might want to post this in the right place too. This is the community cafe.

---

### Post by mikedemario17 on 2008-07-26
o my bad i wasnt paying attenion

---

### Post by RuleMaker on 2008-07-26
> **mikedemario17 said:**
> wtf!
mike@mike-desktop:~$ sudo apt-get install **compiz** compizconfig-settings-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compiz is already the newest version.
E: Couldn't find package compizconfig-settings-manager
mike@mike-desktop:~$

Just remove the word i highlighted.

---

### Post by mikedemario17 on 2008-07-26
> **RuleMaker said:**
> Just remove the word i highlighted.
didnt work 
> mike@mike-desktop:~$ sudo apt-get install compizconfig-settings-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compizconfig-settings-manager
mike@mike-desktop:~$ 


---

### Post by RuleMaker on 2008-07-26
Looks like something's wrong with your repositories, go to System->administration->Software Sources->Ubuntu Software (tab) and make sure that all options are checked.
Then in terminal type:
```
sudo apt-get update
```
and finally install the compizconfig-settings-manager:
```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by mikedemario17 on 2008-07-26
> **RuleMaker said:**
> Looks like something's wrong with your repositories, go to System->administration->Software Sources->Ubuntu Software (tab) and make sure that all options are checked.
Then in terminal type:
```
sudo apt-get update
```
and finally install the compizconfig-settings-manager:
```
sudo apt-get install compizconfig-settings-manager
```
none of them were checked

---

### Post by mikedemario17 on 2008-07-26
> **mikedemario17 said:**
> none of them were checked
you sir are alsome...thanks

---

### Post by RuleMaker on 2008-07-26
So did you checked them and followed the rest?
If you did, then you should have "Advanced Desktop Effects Settings" under System->Preferences, go there and enable whatever you want.

---

### Post by steveneddy on 2008-07-26
This needs to be moved.

---

### Post by K.Mandla on 2008-07-26
Moved to Desktop Effects and Customization.

Please remember that the Cafe is not for support requests.

---

### Post by mikedemario17 on 2008-07-26
alright

---

