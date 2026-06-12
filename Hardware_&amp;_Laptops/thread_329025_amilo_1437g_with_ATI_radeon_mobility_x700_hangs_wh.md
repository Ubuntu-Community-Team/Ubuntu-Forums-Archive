---
title: "amilo 1437g with ATI radeon mobility x700 hangs when shutting down"
date: 2006-12-31
forum: Hardware &amp; Laptops
---

### Post by glantucan on 2006-12-31
hi 
I did follow this method ([http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)) more or less and got 3d acceleration on my fujitsu-siemens amilo 1437g with x700 ati graphics.
Everything works fine except that when I try to shut down, reboot, restart xserver or to get the console with Ctrl+Alt+F1 i get funky colors on my screen and my laptop hangs completely. I must  press the shutdown button for a while to turn off the computer. 

Anyone had this issue and/or have a solution or workaround?

Many thanks

P.D.: I get the following errors in xorg.0.log but don't know whether they are related or not:
```
(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)
(EE) AIGLX: reverting to software rendering
```

Happy new year, by the way :D

---

### Post by glantucan on 2007-01-01
Ok, it looks like fglrx does not support AIGLX, so we need to add this to xorg.conf

```
Section "ServerFlags"
   Option "AIGLX" "Off"
EndSection

```

Then, the error no longer appears in Xorg.0.log

But, this doesn't solve the real problem. The computer still hanging when shutting down.

This morning I decided toI install the latest ati driver to see if it fix the prblem without any change, except that I lost the DRI. Damn it! I tried to reinstall the old one, without result. Tried to clean it up, and 
again install the new one, ... the same. DId i loose DRI forever? I should have kept track of what I did but I didn't, stupid of me. These are the current results of tipical tests:
```

$ fglrxinfo 

            display: :0.0  screen: 0
            OpenGL vendor string: Mesa project: www.mesa3d.org
            OpenGL renderer string: Mesa GLX Indirect
            OpenGL version string: 1.2 (1.5 Mesa 6.5.1)


```

```

$ fgl_glxgears 
         Using GLX_SGIX_pbuffer
         X Error of failed request:  BadMatch (invalid parameter attributes)
          Major opcode of failed request:  143 (GLX)
          Minor opcode of failed request:  5 (X_GLXMakeCurrent)
          Serial number of failed request:  33
          Current serial number in output stream:  33

```
```

$ glxinfo 
	name of display: :0.0
	display: :0  screen: 0
	direct rendering: No
	server glx vendor string: SGI
	server glx version string: 1.2
	server glx extensions:
	    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
	    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
	    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
	    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
	client glx vendor string: ATI
	client glx version string: 1.3
	client glx extensions:
	    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
	    GLX_ARB_get_proc_address, GLX_SGI_video_sync, GLX_ARB_multisample, 
	    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
	GLX version: 1.2
	GLX extensions:
	    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
	    GLX_ARB_multisample
	OpenGL vendor string: Mesa project: www.mesa3d.org
	OpenGL renderer string: Mesa GLX Indirect
	OpenGL version string: 1.2 (1.5 Mesa 6.5.1)
	OpenGL extensions:
	    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp, 
	    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
	    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, 
	    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color, 
	    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add, 
	    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
	    GL_EXT_texture_lod_bias
	glu version: 1.3
	glu extensions:
	    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess
	
	   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
	 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
	----------------------------------------------------------------------
	0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  1 0 None
	0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  1 0 None
	0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
	0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
	0x27 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  1 0 None
	0x28 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  1 0 None
	0x29 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x2a 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None

```


These are the warnings and errors I get on Xorg.0.log:
```

...
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
...

(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Reloading /usr/lib/xorg/modules/linux/libdrm.so
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
[drm] failed to load kernel module "fglrx"
(WW) fglrx(0): Failed to open DRM connection
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
(--) fglrx(0): VideoRAM: 131072 kByte, Type: DDR1
(II) fglrx(0): PCIE card detected
(WW) fglrx(0): board is an unknown third party board, chipset is suppor
...
...
II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 7.1.1.0
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
[drm] failed to load kernel module "fglrx"
(II) fglrx(0): [drm] drmOpen failed
(EE) fglrx(0): DRIScreenInit failed!
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
...
(==) fglrx(0): Write-combining range (0xd7000000,0xfe0000)
(WW) fglrx(0): Failed to set up write-combining range (0xd6000000,0x1fe0000)
(WW) fglrx(0): Failed to set up write-combining range (0xd4000000,0x3fe0000)
(WW) fglrx(0): Failed to set up write-combining range (0xd0000000,0x7fe0000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,8191)
...

```


Please, help me, I need direct rendering to use blender efficiently
I don't know what more to do

Thanks

---

### Post by glantucan on 2007-01-02
Plz does anyone have any clue about this?

---

