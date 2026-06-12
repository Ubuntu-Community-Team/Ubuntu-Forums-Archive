---
title: "glxgears are choppy"
date: 2007-02-04
forum: Hardware &amp; Laptops
---

### Post by Mr. Eddy on 2007-02-04
Hi

I installed the fglrx driver in ubuntu dapper, but now I switched back to the open source ati driver because I have problems with them. But it looks like I don't have gl support. glxgears are choppy. Can someone help me with this problem?

I have a ati 9800 pro

glxinfo:

```
name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig
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
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
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
0x23 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x28 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x2a 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x2b 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x2d 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x30 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x32 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
```

---

### Post by lavinog on 2007-02-04
I don't think the open source drivers provide 3d support...you have to use the closed source drivers.
why did you switch?
have you tried this help page: [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide")

---

### Post by Paerez on 2007-02-04
The open source drivers DO provide 3d, and they are much better at hibernating and suspending.

After you switch to open source drivers, make sure to comment out the "fglrx" line in "/etc/modules" if there is one.

Then make sure to reboot.

---

### Post by Mr. Eddy on 2007-02-04
> why did you switch?

[http://www.ubuntuforums.org/showthread.php?t=352524&highlight=atieventsd](http://www.ubuntuforums.org/showthread.php?t=352524&highlight=atieventsd)

> The open source drivers DO provide 3d, and they are much better at hibernating and suspending.

I know they have 3D support. That's why I'm posting here. and I want my 3D support back! :)

> After you switch to open source drivers, make sure to comment out the "fglrx" line in "/etc/modules" if there is one

No fglrx line in /etc/modules. too bad

does anybody has another suggestion?

---

### Post by Paerez on 2007-02-04
run:
```
lsmod | grep radeon
lsmod | grep fglrx
```
and paste the output please.

---

### Post by Mr. Eddy on 2007-02-04
the firts command gives:

radeon                116000  1
drm                    73236  2 radeon

the second command gives nothing, thanks for your time

---

### Post by Paerez on 2007-02-04
OK thats good so far.

Post your /etc/X11/xorg.conf next.

---

### Post by Mr. Eddy on 2007-02-04
you name it, I give it

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"MD32119PR"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
	Monitor		"MD32119PR"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

I regenerated this file in the hope it would fix my problem with this command

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Paerez on 2007-02-04
OK so now the radeon driver is probed and your xorg.conf is correct. Reboot, login, and post the following commands:
```
glxinfo | grep direct
grep EE /var/log/Xorg.0.log
grep WW /var/log/Xorg.0.log
```

---

### Post by Mr. Eddy on 2007-02-05
```
hans@hans-desktop:~$ glxinfo | grep direct
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect
```

```
hans@hans-desktop:~$ grep EE /var/log/Xorg.0.log
Current Operating System: Linux hans-desktop 2.6.15-27-386 #1 PREEMPT Fri Dec 8 17:51:56 UTC 2006 i686
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
```
```

hans@hans-desktop:~$ grep WW /var/log/Xorg.0.log
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
(WW) RADEON: No matching Device section for instance (BusID PCI:1:0:1) found
(WW) RADEON(0): Failed to detect secondary monitor, MergedFB/Clone mode disabled(WW) (1280x960,MD32119PR) mode clock 148.5MHz exceeds DDC maximum 140MHz
(WW) (1280x1024,MD32119PR) mode clock 157.5MHz exceeds DDC maximum 140MHz
(WW) (1600x1200,MD32119PR) mode clock 162MHz exceeds DDC maximum 140MHz
(WW) (1600x1200,MD32119PR) mode clock 175.5MHz exceeds DDC maximum 140MHz
(WW) (1600x1200,MD32119PR) mode clock 189MHz exceeds DDC maximum 140MHz
(WW) (1600x1200,MD32119PR) mode clock 202.5MHz exceeds DDC maximum 140MHz
(WW) (1600x1200,MD32119PR) mode clock 229.5MHz exceeds DDC maximum 140MHz
(WW) (1792x1344,MD32119PR) mode clock 204.8MHz exceeds DDC maximum 140MHz
(WW) (1792x1344,MD32119PR) mode clock 261MHz exceeds DDC maximum 140MHz
(WW) (1856x1392,MD32119PR) mode clock 218.3MHz exceeds DDC maximum 140MHz
(WW) (1856x1392,MD32119PR) mode clock 288MHz exceeds DDC maximum 140MHz
(WW) (1920x1440,MD32119PR) mode clock 234MHz exceeds DDC maximum 140MHz
(WW) (1920x1440,MD32119PR) mode clock 297MHz exceeds DDC maximum 140MHz
(WW) (1400x1050,MD32119PR) mode clock 151MHz exceeds DDC maximum 140MHz
(WW) (1400x1050,MD32119PR) mode clock 155.8MHz exceeds DDC maximum 140MHz
(WW) (1400x1050,MD32119PR) mode clock 184MHz exceeds DDC maximum 140MHz
(WW) (1680x1050,MD32119PR) mode clock 147.14MHz exceeds DDC maximum 140MHz
(WW) (1680x1050,MD32119PR) mode clock 146.25MHz exceeds DDC maximum 140MHz
(WW) (1680x1050,MD32119PR) mode clock 214.51MHz exceeds DDC maximum 140MHz
(WW) (1920x1200,MD32119PR) mode clock 193.16MHz exceeds DDC maximum 140MHz
(WW) (1920x1200,MD32119PR) mode clock 230MHz exceeds DDC maximum 140MHz
(WW) (1920x1440,MD32119PR) mode clock 341.35MHz exceeds DDC maximum 140MHz
(WW) (2048x1536,MD32119PR) mode clock 266.95MHz exceeds DDC maximum 140MHz
(WW) (2048x1536,MD32119PR) mode clock 340.48MHz exceeds DDC maximum 140MHz
(WW) (2048x1536,MD32119PR) mode clock 388.04MHz exceeds DDC maximum 140MHz
(WW) RADEON(0): Enabling DRM support
(WW) RADEON(0): DRI init changed memory map, adjusting ...
(WW) RADEON(0):   MC_FB_LOCATION  was: 0xefffe800 is: 0xefffe800
(WW) RADEON(0):   MC_AGP_LOCATION was: 0xffffffc0 is: 0xe07fe000
```

I know you're going to find it :D. thank for your time again!!

---

### Post by Mr. Eddy on 2007-02-05
A also switched from i386 kernel to the i686-smp kernel and back to the i386 kernel. 

(I had problems with the i686-smp kernel -> [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/83066](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/83066))

Maybe this has to something do with my problem?

---

### Post by Mr. Eddy on 2007-02-05
update:

I uninstalled the older kernel and restricted modules
I uninstalled the fglrx drivers

Guess what, my glxgears are working again

```
hans@hans-desktop:~$ glxgears -printfps
*********************************WARN_ONCE*********************************
File r300_state.c function r300Enable line 456
TODO - double side stencil !
***************************************************************************
No ctx->FragmentProgram._Current!!
*********************************WARN_ONCE*********************************
File r300_render.c function r300_get_num_verts line 188
user error: Need more than 2 vertices to draw primitive QS !
***************************************************************************
14220 frames in 5.0 seconds = 2843.843 FPS
14250 frames in 5.0 seconds = 2849.875 FPS
14278 frames in 5.0 seconds = 2855.518 FPS
13783 frames in 5.0 seconds = 2756.424 FPS
14320 frames in 5.0 seconds = 2863.823 FPS
14340 frames in 5.0 seconds = 2867.957 FPS
13762 frames in 5.0 seconds = 2752.371 FPS
```

looks normal or not? the gears aren't chopppy anymore

But what was the reason for the choppy gears: the old kernel that was still installed or the fglrx driver that we still installed but not configured

---

