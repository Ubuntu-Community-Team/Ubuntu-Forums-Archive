---
title: "ATI drivers installation"
date: 2004-10-24
forum: Hardware &amp; Laptops
---

### Post by Dracontopes on 2004-10-24
Yes, I know, again...

Very frustrating, the ATI linux drivers :(

I am trying to install the drivers:

```

blabla@blabla:/lib/modules/fglrx/build_mod $ sudo ./make.sh 
ATI module generator V 2.0
==========================
initializing...
Error:
XFree86 drm includes at /lib/modules/2.6.8.1-3-386/build/include/../drivers/char/drm do not fit this driver.
This driver is designed to only work with X4.1.0 or higher.
You can match this by getting Linux kernel 2.4.8 or higher.

```

What can I do about this? (I had the exact same problem with FC2, it needen patching of some sort :S)

edit: I reinstalled the kernel-source (2.6.8.1) and the kernel-headers. No work. :(

---

### Post by Mikelevel on 2004-10-24
If you have a personal kernel try to install following this howto 

[http://xoomer.virgilio.it/flavio.stanchina/debian/fglrx-installer.html](http://xoomer.virgilio.it/flavio.stanchina/debian/fglrx-installer.html)

If you are trying to install with ubuntu default kernel-image its only install with apt "fglrx-driver" and "linux-restricted-modules" (for your arquitecture)

and then change in xfree config "ati" driver for "fglrx" driver...

More info here [http://wiki.ubuntu.com/BinaryDriverHowto](http://wiki.ubuntu.com/BinaryDriverHowto)

---

### Post by Dracontopes on 2004-10-24
[QUOTE=Mikelevel]If you have a personal kernel try to install following this howto 

[http://xoomer.virgilio.it/flavio.stanchina/debian/fglrx-installer.html](http://xoomer.virgilio.it/flavio.stanchina/debian/fglrx-installer.html)

If you are trying to install with ubuntu default kernel-image its only install with apt "fglrx-driver" and "linux-restricted-modules" (for your arquitecture)

and then change in xfree config "ati" driver for "fglrx" driver...

More info here [http://wiki.ubuntu.com/BinaryDriverHowto](http://wiki.ubuntu.com/BinaryDriverHowto)[/QUOTE]
 Thanks for your reply.

When I try using apt-get to install that driver it gives me this error:

```

Preconfiguring packages ...
(Reading database ... 72655 files and directories currently installed.)
Unpacking fglrx-driver (from .../fglrx-driver_2.6.8.1.3-4_i386.deb) ...
Leaving `diversion of /usr/X11R6/lib/libGL.so.1.2 to /usr/share/fglrx/diversions/libGL.so.1.2 by fglrx-driver'
dpkg: error processing /var/cache/apt/archives/fglrx-driver_2.6.8.1.3-4_i386.deb (--unpack):
 trying to overwrite `/usr/X11R6/bin/fgl_glxgears', which is also in package fglrx
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/fglrx-driver_2.6.8.1.3-4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Might there be a command to overwrite files?

---

### Post by Dracontopes on 2004-10-24
Okay, so I got rid of that error (removing fglrx package, then installing fglrx-driver package)

Now, how can I test if Hardware Acceleration is enabled?

---

### Post by Mikelevel on 2004-10-24
```
glxinfo
``` 

You must see ...

```
direct rendering: Yes
``` 

in the beggining

---

### Post by Dracontopes on 2004-10-24
```

name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_ATI_pixel_format_float,
    GLX_ATI_render_texture
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.3 Mesa 4.0.4
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
0x23 24 tc  1 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  1 0 None
0x24 24 tc  1 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  1 0 None
0x25 24 tc  1 24  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x26 24 tc  1 24  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x27 24 dc  1 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  1 0 None
0x28 24 dc  1 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  1 0 None
0x29 24 dc  1 24  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x2a 24 dc  1 24  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None

```

---

### Post by PaTTeX on 2004-10-24
hi guys i have the same prob :/

```
root@julien:/home/julien # glxinfo
name of display: :0.0
display: :0  screen: 0
**direct rendering: No**
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_ATI_pixel_format_float,
    GLX_ATI_render_texture
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.3 Mesa 4.0.4
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
0x23 24 tc  1 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  1 0 None
0x24 24 tc  1 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  1 0 None
0x25 24 tc  1 24  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x26 24 tc  1 24  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x27 24 dc  1 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  1 0 None
0x28 24 dc  1 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  1 0 None
0x29 24 dc  1 24  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x2a 24 dc  1 24  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None

```

---

### Post by Dracontopes on 2004-10-24
I also get this:
```

blabla@blabla:~ $ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.3 Mesa 4.0.4

```

Not good.

I did exactly as is stated [here](http://wiki.ubuntu.com/BinaryDriverHowto). (by the way, I did all this with the X server running (runlevel 5), does that make a difference? I rebooted before I did "fglrxinfo".

This is my XF86Config-4 file:
```

# XF86Config-4 (XFree86 X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the XF86Config-4 manual page.
# (Type "man XF86Config-4" at the shell prompt.)
#
# This file is automatically updated on xserver-xfree86 package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xfree86
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following commands as root:
#
#   cp /etc/X11/XF86Config-4 /etc/X11/XF86Config-4.custom
#   md5sum /etc/X11/XF86Config-4 >/var/lib/xfree86/XF86Config-4.md5sum
#   dpkg-reconfigure xserver-xfree86

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/Speedo"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"speedo"
	Load	"type1"
	Load	"v4l"
	Load	"vbe"
	Load	"xtt"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xfree86"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 9700 Pro (R300 ND)"
	Driver		"fglrx"
	BusID		"PCI:3:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	HorizSync	30-111
	VertRefresh	50-160
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 9700 Pro (R300 ND)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by Dracontopes on 2004-10-24
Okay guys, I got it :)

After using that guide, just run "sudo fglrxconfig" to create a new XF86Config-4 :P

When asked for the mouse, use /dev/input/mice and NOT dev/mouse. Also, in my case, I am not using internalAGP and dga shit. Hope you guys can get is working too! :D

Good luck.

---

### Post by wallijonn on 2004-10-24
What I found worked:

Make a backup copy of XF86Config-4 to your home directory (note mouse settings)

Download the flgrx-driver2.6.8.1.3-4 which will load the second flgrx driver and  libqt3c102-mnt3.3.2.3-4 via SPM (Synaptic Package Manager).

Install the Debian unsupported (universal) ATI drivers vai SPM.

Open a root terminal

run flgrxconfig (select Mesa, FSAA customised settings)

[Since I use a Logitec MX510 I chose Intellimouse PS2 (ImPS2) as my mouse WITH 3 button emulation turned on. 

Make sure that you do not accept the 800x600 res and change it to your upper res to enable 24 bit colour].

exit

reboot

If it gets all messed up you can 

sudo cp XF86Config-4 \etc\X11
sudo shutdown -r now

---

### Post by vauge on 2004-10-25
If you have an nVidia chipset:

Partly taken from: [BinaryDriverHowto](http://wiki.ubuntu.com/BinaryDriverHowto) 

1. *sudo apt-get install linux-686* if you haven't already.
    * or -k7 or -686-smp or -386... whatever matches your kernel.

(reboot)

2. *sudo apt-get install fglrx-driver*
3. *sudo apt-get install fglrx-control*

4. *echo nvidia-agp | sudo tee -a /etc/modules*

5. *echo fglrx | sudo tee -a /etc/modules*
     * cat /etc/modules verify #3 & #4 above are in the list in that order.

Then run:
sudo flgrxconfig

Say NO to ATI AGP support - use the kernel AGP.
Verify the following in /etc/X11XF86config-4

```

*Option "UseInternalAGPGART" "**[COLOR=Red]no[/COLOR]**"*

```
Reboot or you can modprobe the above and restart X.

VIA chipsets should work as well - substitute nvidia-agp for via-agp

---

### Post by claymore on 2004-10-25
Ahhhh, finally.

Thanks so much, I've been trying to get it to work for a week and it's finally going.  It was a combination of connecting to nvidia-agp and the right mouse settings in fglrxconfig for me.

---

### Post by thak on 2004-10-25
Awesome!!  That fglrxconfig thing is way too easy to miss.

I'm _so_ stoked.  That definitely needs to be added to the FAQ, as it was the only thing missing from my inability to get it going.

Great thread!!

++Chad;

---

### Post by emperor on 2004-10-26
There is a package built in the universe repo named:
linux-restricted-modules-2.6.8.1.3-386 or K7 and etc.

Non-free Linux 2.6.8.1 modules on 386
This package provides restricted modules for Linux version 2.6.8.1 on
386.
Currently the following modules are included:
 - madwifi (Atheros)
 - fglrx (ATI)
- nvidia

---

