---
title: "Problem with ATI Radeon 9200 PRO"
date: 2008-07-12
forum: General Help
---

### Post by 1xx1 on 2008-07-12
Hi all,
I'm having problems with my ATI card.Here is what i've done so far..
I installed Ubuntu with the Wubi installer,then updated my system and  had the normal 3d effects working.But then installed compiz-setting-manager,emerald and fusion-icon from the repos and since then i don't have 3D.(there was a 3d accler. 'til i turned off the computer)
I'm using the open source radeon driver and AIGLX.

Edit:now i'm with the original xorg1.conf-no direct rendering :((with the modified the system was stable but unfortunately there wasn't 3d at all)
Take a look at the info archive for more information ...

Any help will be appreciated ! :):popcorn:

---

### Post by overdrank on 2008-07-12
> **1xx1 said:**
> Hi all,
I'm having problems with my ATI card.Here is what i've done so far..
I installed Ubuntu with the Wubi installer,then updated my system and  had the normal 3d effects working.But then installed compiz-setting-manager,emerald and fusion-icon from the repos and since then i don't have 3D.(there was a 3d accler. 'til i turned off the computer)
I'm using the open source radeon driver and AIGLX.

Edit:now i'm with the original xorg1.conf-no direct rendering :((with the modified the system was stable but unfortunately there wasn't 3d at all)
Take a look at the info archive for more information ...

Any help will be appreciated ! :):popcorn:

HI and have a look here you may find some help
[http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)
[http://ubuntuforums.org/showthread.php?t=852464](http://ubuntuforums.org/showthread.php?t=852464)
Also it is not nice to highjack another users thread 
[http://ubuntuforums.org/showthread.php?t=857467](http://ubuntuforums.org/showthread.php?t=857467)           :p

---

### Post by 1xx1 on 2008-07-12
Thanks for the links,tomorrow i'll take a look of them again.:(
Hope i'll find a solution :popcorn:

---

### Post by 1xx1 on 2008-07-13
I couldn't sort the problem out,i read all of the posts in the links and did the following :
```
aptitude reinstall ~nmesa
```
```
apt-get remove linux-restricted-modules-*
```
```
apt-get update,upgrade and autoremove
```
```
apt-get install linux-restricted-modules-`uname -r`
```
```
dpkg-reconfigure xserver-xorg -phigh
```
```
apt-get install --reinstall xserver-xorg-video-ati
```
```
apt-get remove --purge compiz
 apt-get install compiz
```

But there is still no direct rendering

```
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
OpenGL vendor string: Mesa project: www.mesa3d.org
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
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x27 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x28 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x29 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x2a 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x5a 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

```

Now compiz --replace returns

```
compiz (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

```

My xorg.conf (restored from backup;works fine but no 3D)

```
Section "Module"

	Load	"i2c"

	Load	"bitmap"

	Load	"ddc"

	Load	"dbe"

	Load	"dri"

	Load	"extmod"

	Load	"freetype"

	Load	"glx"

	Load	"int10"

	Load	"type1"

	Load	"vbe"

	Load	"synaptics"

EndSection



Section "InputDevice"

	Identifier	"Generic Keyboard"

	Driver		"kbd"

	Option		"XkbRules"	"xorg"

	Option		"XkbModel"	"pc105"

	Option		"XkbLayout"	"us,bg"

EndSection



Section "InputDevice"

	Identifier	"Configured Mouse"

	Driver		"mouse"

	Option		"CorePointer"

EndSection



Section "Device"

Identifier "ATI Technologies Inc RV280 [Radeon 9200 PRO]"

Driver "radeon"

Option		"DRI"			"true"

Option		"ColorTiling"		"on"

Option		"EnablePageFlip"	"true"

Option		"AccelMethod" 		"XAA"

Option		"XAANoOffscreenPixmaps"
 "true"
Option		"RenderAccel"		"true"

Option 		"AGPMode" 		"x"

Option		"AGPFastWrite"		"on"

BusID "PCI:1:0:0"

EndSection



Section "Monitor"

        Identifier      "Generic Monitor"

        Option          "DPMS"

EndSection



Section "Screen"

        Identifier      "Default Screen"

        Device          "ATI Technologies Inc RV280 [Radeon 9200 PRO]"

        Monitor         "Generic Monitor"

        DefaultDepth    24

        SubSection "Display"

                Depth           24

                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "640x480" "720x400"

        EndSubSection

EndSection



Section "ServerLayout"

        Option          "AIGLX"         "true"

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


```

I've added SKIP_CHECKS=yes compiz in /usr/bin/compiz but didn't help.
And still when tryin to change from none to normal or extra effects i get desktop effects could not be enabled :(:confused: :(
So if someone has a solution please help !

---

### Post by overdrank on 2008-07-13
Ok I have a ATI 9600 and I just fired it up and I have no direct rendering but I have the desktop effects. As I understand it ( I am no expert) that you will need to use the ATI for the driver and you are using the radeon. The driver that is installed by default during the installation is the correct driver as you can see it helped the other user in the post I linked. I am not familiar with the command you posted so I can not help. If you can uninstall the radeon driver and maybe use xfix in the recovery mode it may help. Good luck!

---

### Post by 1xx1 on 2008-07-13
Hi,
i decided to restore to the original xorg.conf file and leave only the Module Section untouched,set the driver to "ati" and add:```
Section "DRI"

        Mode 0666

EndSection

        

Section "Extensions"

        Option "Composite" "Enable"
```
.The result was that there was 3D(compiz started successfully,but still the same error when tryin to move at "normal" or "extra" effects)
So _there is 3D_ only when selecting first windows xp---booting,then restart--->loading ubuntu(glxgears returns about 1500 FPS),so  3d can be enabled.
Edit:i selected both "ati" and "radeon"-still no 3D,also selected xfix but that did not help as well.

Xorg.conf

```
Section "Module"

	Load	"i2c"

	Load	"bitmap"

	Load	"ddc"

	Load	"dbe"

	Load	"dri"

        Load	"glx"

EndSection



Section "InputDevice"

	Identifier	"Generic Keyboard"

	Driver		"kbd"

	Option		"XkbRules"	"xorg"

	Option		"XkbModel"	"pc105"

	Option		"XkbLayout"	"us"

EndSection



Section "InputDevice"

	Identifier	"Configured Mouse"

	Driver		"mouse"

	Option		"CorePointer"

EndSection



Section "Device"
	Identifier	"Configured Video Device"
	Driver		"ati"
EndSection



Section "Monitor"

        Identifier      "Configured Monitor"



EndSection



Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection



Section "ServerLayout"

        Option          "AIGLX"         "true"

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
```

---

### Post by 1xx1 on 2008-07-13
Any help :(:(:(:confused::cry:

---

### Post by 1xx1 on 2008-07-14
Hello,i tried everything in the forums but still cannot get 3d running...
Here's my xorg
```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc RV280 [Radeon 9200 PRO]"
        Driver          "radeon"
        BusID           "PCI:1:0:0"
        Option "XAANoOffscreenPixmaps" "true"                 
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"ATI Technologies Inc RV280 [Radeon 9200 PRO]"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
        Option "AIGLX" "true"        
EndSection

 Section "Module"
      # This loads the DRI module
        Load       "dri"
EndSection

Section "DRI"
       Mode 0666
EndSection        

Section "Extensions"

        Option "Composite" "Enable"

EndSection
```

---

