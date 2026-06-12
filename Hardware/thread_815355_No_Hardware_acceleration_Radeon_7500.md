---
title: "No Hardware acceleration Radeon 7500"
date: 2008-06-01
forum: Hardware
---

### Post by Jaso on 2008-06-01
Computer specs:
Lenovo(IBM) T30
Ati Radeon 7500 Mobility


I cannot get the hardware acceleration working at all.

Anyone have a solution?

This is what i get when i run LIBGL_DEBUG=verbose glxinfo

```

jaso@wick3d:~$ 
name of display: :0.0
libGL: XF86DRIGetClientDriverName: 5.3.0 radeon (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/radeon_dri.so
libGL error: dlopen /usr/lib/dri/radeon_dri.so failed (/usr/lib/dri/radeon_dri.so: undefined symbol: _glapi_Dispatch)
libGL error: unable to load driver: radeon_dri.so
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
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
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, 
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI Radeon 20061018 AGP 4x x86/MMX/SSE2 TCL
OpenGL version string: 1.3 Mesa 7.0.3-rc2
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_logic_op, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_copy_texture, GL_EXT_draw_range_elements, GL_EXT_fog_coord, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, GL_EXT_polygon_offset, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_vertex_array, GL_APPLE_packed_pixels, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once, 
    GL_ATIX_texture_env_combine3, GL_IBM_texture_mirrored_repeat, 
    GL_MESA_ycbcr_texture, GL_NV_blend_square, GL_NV_light_max_exponent, 
    GL_NV_texgen_reflection, GL_NV_texture_rectangle, GL_SGI_color_matrix, 
    GL_SGI_color_table, GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays

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
0x58 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon
Segmentation fault


```

I found this part interesting: 

```
"libGL: XF86DRIGetClientDriverName: 5.3.0 radeon (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/radeon_dri.so
libGL error: dlopen /usr/lib/dri/radeon_dri.so failed (/usr/lib/dri/radeon_dri.so: undefined symbol: _glapi_Dispatch)
libGL error: unable to load driver: radeon_dri.so" 
```

So i did the following:

```
aptitude install libgl1-mesa-dri
```

Which i found in this thread: 
```
http://ubuntuforums.org/showthread.php?t=648328
```

But the problem persists and the output is the same.



I have added these lines to xorg.conf:

Found this info at:
```
http://www.thinkwiki.org/wiki/ATI_Mobility_Radeon_7500
```

```

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"ATI Radeon"
	Busid		"PCI:1:0:0"
	Driver		"radeon"
	Screen		0
	Vendorname	"ATI"
	Option		"MergedFB"	"off"
	Option          "AccelMethod" "EXA"
	Option		"EXANoComposite" "false"
	Option		"FBTexPercent" "50"
	Option		"MigrationHeuristic" "greedy"
	Option		"DRI" "true"
	Option		"GARTSize"	"32"
	Option		"AGPMode" "4"
	Option		"Colortiling" "On"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	screen		0 "Default Screen" 0 0
	Inputdevice	"Synaptics Touchpad"
	Option "AIGLX" "true"
EndSection

Section "Extensions"
	Option  "Composite" "Enable"
EndSection

Section "DRI"
	Mode 0666
EndSection


```

---

### Post by bradarnett on 2008-09-20
I'm actually running into this same issue, also with a Thinkpad T30/Radeon 7500 Mobility.  Glxgears will run with about 600 fps, but glxinfo tells me that my direct rendering is disabled, giving the same error when I set the verbose parameter.

For what its worth, here is my xorg.conf:

```


Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc101"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Module"
	Load "GLcore"
	Load "i2c"
	Load "bitmap"
	Load "ddc"
	Load "dri"
	Load "extmod"
	Load "freetype"
	Load "glx"
	Load "int10"
	Load "vbe"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"radeon"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth 24
	SubSection "Display"
		Depth 1
		Modes "1024x768"
	EndSubSection
	SubSection "Display"
		Depth 4
		Modes "1024x768"
	EndSubSection
	SubSection "Display"
		Depth 8
		Modes "1024x768"
	EndSubSection
	SubSection "Display"
		Depth 15
		Modes "1024x768"
	EndSubSection
	SubSection "Display"
		Depth 16
		Modes "1024x768"
	EndSubSection
	SubSection "Display"
		Depth 24
		Modes "1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode 0666
EndSection


```

Any help is greatly appreciated.

Thanks,
Brad

---

### Post by bradarnett on 2008-09-20
I think I just figured it out.  Try removing xorg-driver-fglrx.  Having that installed seems to have include sort of ATI daemon running in the background that messes with DRI on other drivers.

```
brad@envy:~$ sudo apt-get remove xorg-driver-fglrx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  xorg-driver-fglrx
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 30.1MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 116306 files and directories currently installed.)
Removing xorg-driver-fglrx ...
 * Stopping atieventsd                                            [ OK ] 
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
brad@envy:~$ glxinfo | grep direct
libGL: XF86DRIGetClientDriverName: 5.3.0 radeon (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/radeon_dri.so
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 4, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 4, (OK)
drmOpenByBusid: drmOpenMinor returns 4
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
libGL error: 
Can't open configuration file /etc/drirc: No such file or directory.
libGL error: 
Can't open configuration file /home/brad/.drirc: No such file or directory.
direct rendering: Yes

```

Of course, I still cant get Compiz to work, but I think that makes me one step closer.

---

### Post by disneyfriedhistory on 2008-12-02
Check your xorg.0.log and see if all of those settings in your xorg.conf file actually work.  Some of those are ones I haven't seen before.

Also, I've always kept my DefaultDepth at 16.  Compiz hasn't worked well for me since Gutsy, and with Gutsy the key was dropping that DefaultDepth to 16.  

I, too, cannot get compiz to run with Ibex. It switches over, but won't draw any of the window decorations and seems to not respond to anything.  But I can usually switch it back (though sometimes it freezes up.)  

Does anyone know if compiz creates a log file anywhere?

---

### Post by djluvsgod on 2009-01-02
I also have the same video card, while it works, it does nothing 3D. One thing I do know, is that the xorg-driver-fglrx is only for newer cards. For this video card you need the xorg-driver-fglrx legacy driver. It used to be in the repository, but I can't find it in Intrepid. Any Ideas?

---

### Post by jocko on 2009-01-02
> **djluvsgod said:**
> I also have the same video card, while it works, it does nothing 3D. One thing I do know, is that the xorg-driver-fglrx is only for newer cards. For this video card you need the xorg-driver-fglrx legacy driver. It used to be in the repository, but I can't find it in Intrepid. Any Ideas?
Ati has NEVER produced a fglrx driver for anything older than radeon 8500, and they stopped supporting anything older than radeon 9500 a couple of years ago. There has never been any "legacy" driver, except perhaps for the short time just after ati dropped the support for radeon 8500<9500, when the xorg and kernel versions in ubuntu could still use both the older and the newer fglrx driver.

The only thing you will get from trying to install fglrx on a system that doesn't have a supported card is a broken glx and dri, as the mesa files are replaced with the fglrx files.

To get back dri and glx for the open source driver:
```
sudo apt-get remove --purge xorg-driver-fglrx
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri
```

---

