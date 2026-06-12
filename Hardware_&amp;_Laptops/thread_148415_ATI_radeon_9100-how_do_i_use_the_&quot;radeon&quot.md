---
title: "ATI radeon 9100-how do i use the &quot;radeon&quot; driver for 3d ?"
date: 2006-03-22
forum: Hardware &amp; Laptops
---

### Post by techrush on 2006-03-22
the fglrx driver from ATI is apparently not compatible with my radeon 9100 mobility. ive tried litterally every how-to to try to get it working. what im interested in is using the "radeon" open source driver to get acceleration with this card. 

this is where the problem starts. i changed the line in my xorg so it reads:

driver:   radeon

i still get  very low fps in glxgears. ive done some reading and it seems you need drm and a fairly recent version of mesa to get this all to work. im just lost as to how to go about it. any help is appreciated.

---

### Post by BoyOfDestiny on 2006-03-22
[QUOTE=techrush]the fglrx driver from ATI is apparently not compatible with my radeon 9100 mobility. ive tried litterally every how-to to try to get it working. what im interested in is using the "radeon" open source driver to get acceleration with this card. 

this is where the problem starts. i changed the line in my xorg so it reads:

driver:   radeon

i still get  very low fps in glxgears. ive done some reading and it seems you need drm and a fairly recent version of mesa to get this all to work. im just lost as to how to go about it. any help is appreciated.[/QUOTE]

in a terminal type glxinfo... See if it says DRI yes (if so then that's about as good as it will get) Also, you may want to post your xorg.conf...
The line should look like this:

	Driver		"radeon"

---

### Post by cantormath on 2006-03-22
I have an ATI radeon 9100 and I didnt need to install the fglrx drivers (Breezy 5.1), it works fine in 3d mode from the normal install.  I did try the fglrx drivers with the client so that I could use the tvout and dual head option, but the 3d get tweaked when you do that from what I have seen.  If anyone know why, please let me know as well.

cantormath...

---

### Post by encompass on 2006-03-22
I also have the 9100 and on a fresh install the 3d works... it is the ati driver.
BUT it is buggy, and I have never gotten 3d back after trying out the fglrx driver... But thats ok, I can live with vesa for now... but not much long, so I am getting a gforce for summer.  :)

---

### Post by techrush on 2006-03-22
when i type glxinfo in terminal i get this line which from what i understand means that acceleration is not enabled:

direct rendering: No

i do have my xorg.conf line set to look like yours in the post earlier. was a typo sorry.

---

### Post by Teroedni on 2006-03-22
Hmm i would use the radeon driver.

What Xorg version are you running?

and what does glxinfo give you when driver radeon is used?

I recently helped another user.[http://www.ubuntuforums.org/showthread.php?t=146420](http://www.ubuntuforums.org/showthread.php?t=146420)
In this thread  theres differents tips to increase you card performance;)


Hopes This helps:)

---

### Post by techrush on 2006-03-22
glxinfo retruns the following:


name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_ info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap _method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyper pipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_ rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_ARB_mu ltisample, GLX_ATI_pixel_format_float,
    GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_ rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: Mesa project: www. mesa3d.org
OpenGL renderer string: Mesa GLX Indirec t
OpenGL version string: 1.2 (1.5 Mesa 6.4 .1)
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture,  GL_ARB_texture_border_clamp,
    GL_ARB_texture_cube_map, GL_ARB_text ure_env_add,
    GL_ARB_texture_env_combine, GL_ARB_t exture_env_dot3,
    GL_ARB_transpose_matrix, GL_EXT_abgr , GL_EXT_blend_color,
    GL_EXT_blend_minmax, GL_EXT_blend_su btract, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_t exture_env_dot3,
    GL_EXT_texture_lod_bias
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_o bject_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
---------------------------------------- ------------------------------
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  1 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  1 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x27 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  1 0 None
0x28 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  1 0 None
0x29 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x2a 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None

---

### Post by cantormath on 2006-03-22
yeah, I cant stand the screen without the 3d card working, you look quality all around I think............

---

### Post by Teroedni on 2006-03-23
Post your xorg log here
```
sudo gedit /var/log/Xorg.0.log
```

It probaly use 3 pages. Thats okay :)

In the log there will be information to why the  Radeon driver fails to run Dri.

---

### Post by techrush on 2006-03-23
um ok here it is! i sure hope you can help :)

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.12 i686
Current Operating System: Linux techrushC 2.6.15-19-386 #1 PREEMPT Mon Mar 20 16:46:02 UTC 2006 i686
Build Date: 16 March 2006
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Mar 23 16:03:47 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "StudioDsply1"
(**) |   |-->Device "Silicon Integrated Systems (SiS) 86C326 5598/6326"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Extension "Composite" is enabled
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.2
	X.Org Video Driver: 0.8
	X.Org XInput driver : 0.5
	X.Org Server Extension : 0.2
	X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(--) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1106,0601 card 0000,0000 rev 05 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,8601 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:07:0: chip 1106,0686 card 1106,0000 rev 40 class 06,01,00 hdr 80
(II) PCI: 00:07:1: chip 1106,0571 card 1106,0571 rev 06 class 01,01,8a hdr 00
(II) PCI: 00:07:2: chip 1106,3038 card 0925,1234 rev 1a class 0c,03,00 hdr 00
(II) PCI: 00:07:3: chip 1106,3038 card 0925,1234 rev 1a class 0c,03,00 hdr 00
(II) PCI: 00:07:4: chip 1106,3057 card 0000,0000 rev 40 class 00,80,00 hdr 00
(II) PCI: 00:07:5: chip 1106,3058 card 1106,4511 rev 50 class 04,01,00 hdr 00
(II) PCI: 00:08:0: chip 10de,0185 card 3842,b091 rev c1 class 03,00,00 hdr 00
(II) PCI: 00:0e:0: chip 10ec,8139 card 10ec,8139 rev 10 class 02,00,00 hdr 00
(II) PCI: 01:00:0: chip 1023,8500 card 1023,8500 rev 6a class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xd8000000 - 0xdaffffff (0x3000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0x20000000 - 0x200fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:7:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(0:8:0) nVidia Corporation NV18 [GeForce4 MX 4000 AGP 8x] rev 193, Mem @ 0xdb000000/24, 0xd0000000/27
(--) PCI: (1:0:0) Trident Microsystems CyberBlade/i1 rev 106, Mem @ 0xd9800000/23, 0xda000000/17, 0xd9000000/23
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[6] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xdc000000 from 0xdcffffff to 0xdbffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xde000000 - 0xde0000ff (0x100) MX[B]
	[1] -1	0	0xdc000000 - 0xdbffffff (0x0) MX[B]O
	[2] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[3] -1	0	0xdb000000 - 0xdbffffff (0x1000000) MX[B](B)
	[4] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[5] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[6] -1	0	0x0000e000 - 0x0000e003 (0x4) IX[B]
	[7] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[8] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[9] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[10] -1	0	0x0000d000 - 0x0000d00f (0x10) IX[B]
(II) Inactive PCI resource ranges:
	[0] -1	0	0xd9000000 - 0xd97fffff (0x800000) MX[B](B)
	[1] -1	0	0xda000000 - 0xda01ffff (0x20000) MX[B](B)
	[2] -1	0	0xd9800000 - 0xd9ffffff (0x800000) MX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xde000000 - 0xde0000ff (0x100) MX[B]
	[1] -1	0	0xdc000000 - 0xdbffffff (0x0) MX[B]O
	[2] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[3] -1	0	0xdb000000 - 0xdbffffff (0x1000000) MX[B](B)
	[4] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[5] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[6] -1	0	0x0000e000 - 0x0000e003 (0x4) IX[B]
	[7] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[8] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[9] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[10] -1	0	0x0000d000 - 0x0000d00f (0x10) IX[B]
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0xd9000000 - 0xd97fffff (0x800000) MX[B](B)
	[1] -1	0	0xda000000 - 0xda01ffff (0x20000) MX[B](B)
	[2] -1	0	0xd9800000 - 0xd9ffffff (0x800000) MX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[6] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xde000000 - 0xde0000ff (0x100) MX[B]
	[6] -1	0	0xdc000000 - 0xdbffffff (0x0) MX[B]O
	[7] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[8] -1	0	0xdb000000 - 0xdbffffff (0x1000000) MX[B](B)
	[9] -1	0	0xd9000000 - 0xd97fffff (0x800000) MX[B](B)
	[10] -1	0	0xda000000 - 0xda01ffff (0x20000) MX[B](B)
	[11] -1	0	0xd9800000 - 0xd9ffffff (0x800000) MX[B](B)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[15] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[16] -1	0	0x0000e000 - 0x0000e003 (0x4) IX[B]
	[17] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[18] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[19] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[20] -1	0	0x0000d000 - 0x0000d00f (0x10) IX[B]
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.0.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8178
	Module class: XFree86 Server Extension
	ABI class: XFree86 Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.o
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8178
	Module class: XFree86 Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 6.99.99.904, module version = 1.0.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) NVIDIA X Driver  1.0-8178  Wed Dec 14 16:25:22 PST 2005
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 00:08:0
(--) Chipset NVIDIA GPU found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xde000000 - 0xde0000ff (0x100) MX[B]
	[6] -1	0	0xdc000000 - 0xdbffffff (0x0) MX[B]O
	[7] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[8] -1	0	0xdb000000 - 0xdbffffff (0x1000000) MX[B](B)
	[9] -1	0	0xd9000000 - 0xd97fffff (0x800000) MX[B](B)
	[10] -1	0	0xda000000 - 0xda01ffff (0x20000) MX[B](B)
	[11] -1	0	0xd9800000 - 0xd9ffffff (0x800000) MX[B](B)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[15] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[16] -1	0	0x0000e000 - 0x0000e003 (0x4) IX[B]
	[17] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[18] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[19] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[20] -1	0	0x0000d000 - 0x0000d00f (0x10) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xde000000 - 0xde0000ff (0x100) MX[B]
	[6] -1	0	0xdc000000 - 0xdbffffff (0x0) MX[B]O
	[7] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[8] -1	0	0xdb000000 - 0xdbffffff (0x1000000) MX[B](B)
	[9] -1	0	0xd9000000 - 0xd97fffff (0x800000) MX[B](B)
	[10] -1	0	0xda000000 - 0xda01ffff (0x20000) MX[B](B)
	[11] -1	0	0xd9800000 - 0xd9ffffff (0x800000) MX[B](B)
	[12] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[13] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[14] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[18] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[19] -1	0	0x0000e000 - 0x0000e003 (0x4) IX[B]
	[20] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[21] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[22] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[23] -1	0	0x0000d000 - 0x0000d00f (0x10) IX[B]
	[24] 0	0	0x201003b0 - 0x201003bb (0xc) IS[B]
	[25] 0	0	0x201003c0 - 0x201003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "RenderAccel" "true"
(**) NVIDIA(0): Option "AllowGLXWithComposite" "true"
(**) NVIDIA(0): Enabling experimental RENDER acceleration
(--) NVIDIA(0): Linear framebuffer at 0xD0000000
(--) NVIDIA(0): MMIO registers at 0xDB000000
(II) NVIDIA(0): NVIDIA GPU detected as: GeForce4 MX 4000
(--) NVIDIA(0): VideoBIOS: 04.18.20.39.07
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): VideoRAM: 65536 kBytes
(II) NVIDIA(0): Connected display device(s): CRT-0
(--) NVIDIA(0): CRT-0: maximum pixel clock: 350 MHz
(II) NVIDIA(0): Frequency information for CRT-0:
(II) NVIDIA(0):   HorizSync   : 30.000-85.000 kHz
(II) NVIDIA(0):   VertRefresh : 48.000-160.000 Hz
(II) NVIDIA(0):      (HorizSync from EDID)
(II) NVIDIA(0):      (VertRefresh from EDID)
(II) NVIDIA(0): StudioDsply1: Using hsync range of 30.00-85.00 kHz
(II) NVIDIA(0): StudioDsply1: Using vrefresh range of 48.00-160.00 Hz
(II) NVIDIA(0): Clock range:  12.00 to 350.00 MHz
(II) NVIDIA(0): Not using default mode "1280x960" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x480" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1280x1024" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x512" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1792x1344" (hsync out of range)
(II) NVIDIA(0): Not using default mode "896x672" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1856x1392" (hsync out of range)
(II) NVIDIA(0): Not using default mode "928x696" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1856x1392" (hsync out of range)
(II) NVIDIA(0): Not using default mode "928x696" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1440" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x720" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1440" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x720" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1400x1050" (hsync out of range)
(II) NVIDIA(0): Not using default mode "700x525" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1440" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x720" (hsync out of range)
(II) NVIDIA(0): Not using default mode "2048x1536" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "2048x1536" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "2048x1536" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1440x900" (width too large for virtual size)
(WW) NVIDIA(0): Not using mode "1152x768":
(WW) NVIDIA(0):   horizontal sync start (1178) not a multiple of 8
(WW) NVIDIA(0): Not using mode "576x384":
(WW) NVIDIA(0):   horizontal sync start (589) not a multiple of 8
(WW) NVIDIA(0): Not using mode "360x200":
(WW) NVIDIA(0):   horizontal sync start (378) not a multiple of 8
(**) NVIDIA(0): Validated modes for display device CRT-0:
(**) NVIDIA(0):      Default mode "1280x1024": 135.0 MHz, 80.0 kHz, 75.0 Hz
(**) NVIDIA(0):      Default mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
(**) NVIDIA(0):      Default mode "1280x1024": 108.0 MHz, 64.0 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "1280x960": 108.0 MHz, 60.0 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "1280x800": 83.5 MHz, 49.7 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "1152x864": 121.5 MHz, 77.5 kHz, 85.1 Hz
(**) NVIDIA(0):      Default mode "1152x864": 108.0 MHz, 67.5 kHz, 75.0 Hz
(**) NVIDIA(0):      Default mode "1280x768": 80.1 MHz, 47.7 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "1024x768": 78.8 MHz, 60.1 kHz, 75.1 Hz
(**) NVIDIA(0):      Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(**) NVIDIA(0):      Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "1024x768": 44.9 MHz, 35.5 kHz, 87.0 Hz (I)
(**) NVIDIA(0):      Default mode "896x672": 102.4 MHz, 83.7 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "960x600": 96.6 MHz, 74.5 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(**) NVIDIA(0):      Default mode "800x600": 56.3 MHz, 53.7 kHz, 85.1 Hz
(**) NVIDIA(0):      Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(**) NVIDIA(0):      Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(**) NVIDIA(0):      Default mode "800x600": 87.8 MHz, 81.2 kHz, 65.0 Hz (D)
(**) NVIDIA(0):      Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(**) NVIDIA(0):      Default mode "800x600": 81.0 MHz, 75.0 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(**) NVIDIA(0):      Default mode "840x525": 73.6 MHz, 65.2 kHz, 60.1 Hz (D)
(**) NVIDIA(0):      Default mode "700x525": 77.9 MHz, 81.5 kHz, 74.8 Hz (D)
(**) NVIDIA(0):      Default mode "700x525": 75.5 MHz, 77.0 kHz, 70.0 Hz (D)
(**) NVIDIA(0):      Default mode "700x525": 61.0 MHz, 64.9 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "640x512": 67.5 MHz, 80.0 kHz, 75.0 Hz (D)
(**) NVIDIA(0):      Default mode "640x512": 54.0 MHz, 64.0 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "720x450": 54.4 MHz, 56.9 kHz, 60.2 Hz (D)
(**) NVIDIA(0):      Default mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
(**) NVIDIA(0):      Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(**) NVIDIA(0):      Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(**) NVIDIA(0):      Default mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "640x480": 54.0 MHz, 60.0 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "720x400": 35.5 MHz, 37.9 kHz, 85.0 Hz
(**) NVIDIA(0):      Default mode "640x400": 31.5 MHz, 37.9 kHz, 85.1 Hz
(**) NVIDIA(0):      Default mode "640x400": 41.7 MHz, 49.7 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "576x432": 60.8 MHz, 77.5 kHz, 85.2 Hz (D)
(**) NVIDIA(0):      Default mode "576x432": 54.0 MHz, 67.5 kHz, 75.0 Hz (D)
(**) NVIDIA(0):      Default mode "640x384": 40.1 MHz, 47.7 kHz, 60.1 Hz (D)
(**) NVIDIA(0):      Default mode "640x350": 31.5 MHz, 37.9 kHz, 85.1 Hz
(**) NVIDIA(0):      Default mode "512x384": 47.2 MHz, 68.7 kHz, 85.0 Hz (D)
(**) NVIDIA(0):      Default mode "512x384": 39.4 MHz, 60.1 kHz, 75.1 Hz (D)
(**) NVIDIA(0):      Default mode "512x384": 37.5 MHz, 56.5 kHz, 70.1 Hz (D)
(**) NVIDIA(0):      Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "512x384": 22.4 MHz, 35.5 kHz, 86.9 Hz (D)
(**) NVIDIA(0):      Default mode "416x312": 28.6 MHz, 49.7 kHz, 74.7 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 28.1 MHz, 53.7 kHz, 85.3 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 18.0 MHz, 43.3 kHz, 85.2 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 15.8 MHz, 37.5 kHz, 75.0 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 15.8 MHz, 37.9 kHz, 72.8 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(**) NVIDIA(0):      Default mode "320x200": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(**) NVIDIA(0):      Default mode "320x175": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(++) NVIDIA(0): DPI set to (100, 100); computed from -dpi X commandline option
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.8
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B]
	[1] 0	0	0xdb000000 - 0xdbffffff (0x1000000) MX[B]
	[2] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xde000000 - 0xde0000ff (0x100) MX[B]
	[8] -1	0	0xdc000000 - 0xdbffffff (0x0) MX[B]O
	[9] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[10] -1	0	0xdb000000 - 0xdbffffff (0x1000000) MX[B](B)
	[11] -1	0	0xd9000000 - 0xd97fffff (0x800000) MX[B](B)
	[12] -1	0	0xda000000 - 0xda01ffff (0x20000) MX[B](B)
	[13] -1	0	0xd9800000 - 0xd9ffffff (0x800000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[20] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[21] -1	0	0x0000e000 - 0x0000e003 (0x4) IX[B]
	[22] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[23] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[24] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[25] -1	0	0x0000d000 - 0x0000d00f (0x10) IX[B]
	[26] 0	0	0x201003b0 - 0x201003bb (0xc) IS[B]
	[27] 0	0	0x201003c0 - 0x201003df (0x20) IS[B]
(II) NVIDIA(0): Setting mode "1280x1024"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
error opening security policy file /etc/xserver/SecurityPolicy
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(II) Configured Mouse: ps2EnableDataReporting: succeeded

---

### Post by techrush on 2006-03-23
ok i just goofed up bad...i posted my xorg log from another machine with a working nvidia card LOL. the log went so big im unable to edit/remove the post! im really sorry. ill have to wait until im home later to put up the xorg log from the radeon machine.


techrus the village idiot :)

---

### Post by cantormath on 2006-03-24
should really use one of those window things to post a xorg.conf file or upload it somewhere and put a link in the post.  That way we aren't scrolling for days on the board....

just a thought........
:-k

---

### Post by encompass on 2006-04-05
well? you got that post?  I have the same problem...

---

### Post by Teroedni on 2006-04-06
cantormath:Your choice


encompass, What do you mean
what dosen't work with your card?

---

### Post by encompass on 2006-04-06
the driver from ati the fglrx driver... it won't give you 3d support.  That is what they even tell you on the website.  I want to get it to work... and the closest I got was using the ati on a fresh install... I trying getting a more stable driver, but it didn't work.  ended up with no more 3d support even when I tried to go back.

---

### Post by cantormath on 2006-04-09
[QUOTE=encompass]the driver from ati the fglrx driver... it won't give you 3d support.  That is what they even tell you on the website.  I want to get it to work... and the closest I got was using the ati on a fresh install... I trying getting a more stable driver, but it didn't work.  ended up with no more 3d support even when I tried to go back.[/QUOTE]

I am not running breezy anymore, but when I was, I didnt use the fglrx drivers.  Breezy install something else, think it was called ati-controller, or something like that.  The fglrx drivers really suck, especially if you have a ATI Radeon 9100 IGP card.  Everytime I have tried the fglrx drivers, my video was terrible, and 3d was terrible.  The drivers I am talking about render 3d perfectly and fglrx doesn't need to be installed.  Again, I am sorry I don't remember the name.  If breezy is install fglrx on your machine, even after you do your updates after install, I dont know what to tell you...

let me know if you get it.

cantor

---

