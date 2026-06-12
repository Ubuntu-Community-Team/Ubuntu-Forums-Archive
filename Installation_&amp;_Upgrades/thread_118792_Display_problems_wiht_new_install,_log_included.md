---
title: "Display problems wiht new install, log included"
date: 2006-01-17
forum: Installation &amp; Upgrades
---

### Post by Brian Smith on 2006-01-17
Hi folks, first post here.
First off, after trying multiple current distros, I've settled upon Ubuntu for the organization and Gnome for the "feel" and friendliness toward novice computer users, and I'm committed to learning as much as necessary to achieve the customization I can achieve with Windows OSs.  It took me a long time to learn as much of the peculiarities of the different Windows systems I use, I think I should commit to a decent level of difficulty and period of experimentation with Linux and Ubuntu to get there.

Now for my problems.

Installation of files on 2 problem machines completed, but would not boot to desktops.  I've already succesfully edited my /etc/X11/xorg.conf on a laptop installation last night to achieve fullest possible screen resolutions instead of 640x480 8-bit (ouch!) that was available as installed.  I did that by looking at the warnings and errors in /var/log/Xorg.0.log and proceeding from there.  The HorizSync and VertRefresh had to be declared.  Bingo, problem solved, hooray.

I'm trying to do the same for a desktop.  The values for HorizSync and VertRefresh were incorrect for the monitor.  I extended the ranges to cover the range specified for the monitor (Dell e770s, H30-70kHz, V50-160Hz, with specified modes from H31.5-68.7, V59.9-85..1) but still I can't get it to boot to a desktop.  

Here's my xorg.0.log file:


X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174523 [email]root@vernadsky.buil[/email]dd)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF] 
Current Operating System: Linux ubuntu 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i586
Build Date: 10 October 2005
	Before reporting problems, check [http://wiki.X.Org](http://wiki.X.Org)
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-9-386 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 13:14:36 BST 2005 
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Jan 17 17:44:02 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "ARK Logic Inc 2000MT"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/CID" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID").
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/usr/X11R6/lib/X11/rgb"
(==) ModulePath set to "/usr/X11R6/lib/modules"
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.2
	X.Org Video Driver: 0.7
	X.Org XInput driver : 0.4
	X.Org Server Extension : 0.2
	X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/X11R6/lib/modules/libpcidata.a
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,7100 card 0000,0000 rev 01 class 06,00,00 hdr 00
(II) PCI: 00:07:0: chip 8086,7110 card 0000,0000 rev 01 class 06,01,00 hdr 80
(II) PCI: 00:07:1: chip 8086,7111 card 0000,0000 rev 01 class 01,01,80 hdr 00
(II) PCI: 00:07:2: chip 8086,7112 card 0000,0000 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:07:3: chip 8086,7113 card 0000,0000 rev 01 class 06,80,00 hdr 00
(II) PCI: 00:11:0: chip edd8,a0a1 card 0000,0000 rev 00 class 03,00,00 hdr 00
(II) PCI: 00:12:0: chip 1317,0985 card 1317,0574 rev 11 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,0), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:7:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(0:17:0) ARK Logic Inc 2000MT rev 0, Mem @ 0xfe000000/23, BIOS @ 0xffaf0000/16
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
(II) Active PCI resource ranges:
	[0] -1	0	0xffaefc00 - 0xffaeffff (0x400) MX[B]
	[1] -1	0	0xffaf0000 - 0xffafffff (0x10000) MX[B](B)
	[2] -1	0	0xfe000000 - 0xfe7fffff (0x800000) MX[B](B)
	[3] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[4] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[5] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xffaefc00 - 0xffaeffff (0x400) MX[B]
	[1] -1	0	0xffaf0000 - 0xffafffff (0x10000) MX[B](B)
	[2] -1	0	0xfe000000 - 0xfe7fffff (0x800000) MX[B](B)
	[3] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[4] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[5] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
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
	[5] -1	0	0xffaefc00 - 0xffaeffff (0x400) MX[B]
	[6] -1	0	0xffaf0000 - 0xffafffff (0x10000) MX[B](B)
	[7] -1	0	0xfe000000 - 0xfe7fffff (0x800000) MX[B](B)
	[8] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[9] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[10] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[11] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[12] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
(WW) Ignoring request to load module GLcore
(II) LoadModule: "i2c"
(II) Loading /usr/X11R6/lib/modules/libi2c.a
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "bitmap"
(II) Reloading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/X11R6/lib/modules/libddc.a
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "dri"
(II) Loading /usr/X11R6/lib/modules/extensions/libdri.a
(II) Module dri: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/X11R6/lib/modules/linux/libdrm.a
(II) Module drm: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/X11R6/lib/modules/extensions/libextmod.a
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
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
(II) Loading /usr/X11R6/lib/modules/fonts/libfreetype.a
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 6.8.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/X11R6/lib/modules/extensions/libglx.a
(II) Module glx: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/X11R6/lib/modules/extensions/libGLcore.a
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o":  No symbols found
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/X11R6/lib/modules/linux/libint10.a
(II) Module int10: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "type1"
(II) Loading /usr/X11R6/lib/modules/fonts/libtype1.a
(II) Module type1: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) Loading font CID
(II) LoadModule: "vbe"
(II) Loading /usr/X11R6/lib/modules/libvbe.a
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "ark"
(II) Loading /usr/X11R6/lib/modules/drivers/ark_drv.o
(II) Module ark: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 0.5.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "kbd"
(II) Loading /usr/X11R6/lib/modules/input/kbd_drv.o
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) LoadModule: "mouse"
(II) Loading /usr/X11R6/lib/modules/input/mouse_drv.o
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) ARK: driver (version 0.5.0 for ARK Logic chipset: ark1000pv,
	ark2000pv, ark2000mt
(II) Primary Device is: PCI 00:11:0
(--) Chipset ark2000mt found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xffaefc00 - 0xffaeffff (0x400) MX[B]
	[6] -1	0	0xffaf0000 - 0xffafffff (0x10000) MX[B](B)
	[7] -1	0	0xfe000000 - 0xfe7fffff (0x800000) MX[B](B)
	[8] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[9] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[10] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[11] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[12] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xffaefc00 - 0xffaeffff (0x400) MX[B]
	[6] -1	0	0xffaf0000 - 0xffafffff (0x10000) MX[B](B)
	[7] -1	0	0xfe000000 - 0xfe7fffff (0x800000) MX[B](B)
	[8] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[9] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[10] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[11] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[12] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[13] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[14] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[15] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[16] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[17] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/X11R6/lib/modules/libvgahw.a
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.7
(II) ark(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(**) ark(0): Depth 16, (--) framebuffer bpp 16
(==) ark(0): RGB weight 565
(==) ark(0): Default visual is TrueColor
(**) ark(0): Chipset: "ark2000mt"
(--) ark(0): Framebuffer @ 0xfefe0000
(==) ark(0): Using gamma correction (1.0, 1.0, 1.0)
(--) ark(0): Detected 1024 bytes video ram
(II) ark(0): Generic Monitor: Using hsync range of 28.00-69.00 kHz
(II) ark(0): Generic Monitor: Using vrefresh range of 43.00-86.00 Hz
(II) ark(0): Clock range:  20.00 to  80.00 MHz
(II) ark(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) ark(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) ark(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
(II) ark(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) ark(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) ark(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) ark(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) ark(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) ark(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) ark(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) ark(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) ark(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) ark(0): Not using default mode "1024x768" (insufficient memory for mode)
(II) ark(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) ark(0): Not using default mode "1024x768" (insufficient memory for mode)
(II) ark(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) ark(0): Not using default mode "1024x768" (insufficient memory for mode)
(II) ark(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) ark(0): Not using default mode "1024x768" (insufficient memory for mode)
(II) ark(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) ark(0): Not using default mode "1024x768" (insufficient memory for mode)
(II) ark(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) ark(0): Not using default mode "1152x864" (insufficient memory for mode)
(II) ark(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) ark(0): Not using default mode "1280x960" (insufficient memory for mode)
(II) ark(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) ark(0): Not using default mode "1280x960" (insufficient memory for mode)
(II) ark(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) ark(0): Not using default mode "1280x1024" (insufficient memory for mode)
(II) ark(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) ark(0): Not using default mode "1280x1024" (insufficient memory for mode)
(II) ark(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) ark(0): Not using default mode "1280x1024" (insufficient memory for mode)
(II) ark(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) ark(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) ark(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) ark(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) ark(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) ark(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) ark(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) ark(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) ark(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) ark(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) ark(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) ark(0): Not using default mode "1792x1344" (insufficient memory for mode)
(II) ark(0): Not using default mode "896x672" (insufficient memory for mode)
(II) ark(0): Not using default mode "1792x1344" (insufficient memory for mode)
(II) ark(0): Not using default mode "896x672" (insufficient memory for mode)
(II) ark(0): Not using default mode "1856x1392" (insufficient memory for mode)
(II) ark(0): Not using default mode "928x696" (insufficient memory for mode)
(II) ark(0): Not using default mode "1856x1392" (insufficient memory for mode)
(II) ark(0): Not using default mode "928x696" (insufficient memory for mode)
(II) ark(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) ark(0): Not using default mode "960x720" (insufficient memory for mode)
(II) ark(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) ark(0): Not using default mode "960x720" (insufficient memory for mode)
(II) ark(0): Not using default mode "416x312" (bad mode clock/interlace/doublescan)
(II) ark(0): Not using default mode "1280x768" (insufficient memory for mode)
(II) ark(0): Not using default mode "640x384" (bad mode clock/interlace/doublescan)
(II) ark(0): Not using default mode "1280x800" (insufficient memory for mode)
(II) ark(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) ark(0): Not using default mode "1152x768" (insufficient memory for mode)
(II) ark(0): Not using default mode "576x384" (bad mode clock/interlace/doublescan)
(II) ark(0): Not using default mode "1152x864" (insufficient memory for mode)
(II) ark(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) ark(0): Not using default mode "1400x1050" (insufficient memory for mode)
(II) ark(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) ark(0): Not using default mode "1400x1050" (insufficient memory for mode)
(II) ark(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) ark(0): Not using default mode "1400x1050" (insufficient memory for mode)
(II) ark(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) ark(0): Not using default mode "1400x1050" (insufficient memory for mode)
(II) ark(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) ark(0): Not using default mode "1440x900" (insufficient memory for mode)
(II) ark(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
(II) ark(0): Not using default mode "1600x1024" (insufficient memory for mode)
(II) ark(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
(II) ark(0): Not using default mode "1680x1050" (insufficient memory for mode)
(II) ark(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) ark(0): Not using default mode "1920x1200" (insufficient memory for mode)
(II) ark(0): Not using default mode "960x600" (insufficient memory for mode)
(II) ark(0): Not using default mode "1920x1200" (insufficient memory for mode)
(II) ark(0): Not using default mode "960x600" (insufficient memory for mode)
(II) ark(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) ark(0): Not using default mode "960x720" (insufficient memory for mode)
(II) ark(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) ark(0): Not using default mode "1024x768" (insufficient memory for mode)
(II) ark(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) ark(0): Not using default mode "1024x768" (insufficient memory for mode)
(II) ark(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) ark(0): Not using default mode "1024x768" (insufficient memory for mode)
(II) ark(0): Not using mode "1024x768" (no mode of this name)
(II) ark(0): Not using default mode "832x624" (width too large for virtual size)
(--) ark(0): Virtual size is 800x600 (pitch 800)
(**) ark(0): *Default mode "800x600": 56.3 MHz, 53.7 kHz, 85.1 Hz
(II) ark(0): Modeline "800x600"   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync
(**) ark(0): *Default mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
(II) ark(0): Modeline "640x480"   36.00  640 696 752 832  480 481 484 509 -hsync -vsync
(**) ark(0):  Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) ark(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(**) ark(0):  Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) ark(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(**) ark(0):  Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) ark(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(**) ark(0):  Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) ark(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(**) ark(0):  Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) ark(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(**) ark(0):  Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) ark(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(**) ark(0):  Default mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(II) ark(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(**) ark(0):  Default mode "720x400": 35.5 MHz, 37.9 kHz, 85.0 Hz
(II) ark(0): Modeline "720x400"   35.50  720 756 828 936  400 401 404 446 -hsync +vsync
(**) ark(0):  Default mode "640x400": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) ark(0): Modeline "640x400"   31.50  640 672 736 832  400 401 404 445 -hsync +vsync
(**) ark(0):  Default mode "640x350": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) ark(0): Modeline "640x350"   31.50  640 672 736 832  350 382 385 445 +hsync -vsync
(==) ark(0): DPI set to (75, 75)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/X11R6/lib/modules/libfb.a
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
(II) Module fb: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/X11R6/lib/modules/libxaa.a
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.7
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xfe000000 - 0xfe7fffff (0x800000) MS[B]
	[1] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xffaefc00 - 0xffaeffff (0x400) MX[B]
	[7] -1	0	0xffaf0000 - 0xffafffff (0x10000) MX[B](B)
	[8] -1	0	0xfe000000 - 0xfe7fffff (0x800000) MX[B](B)
	[9] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[10] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[11] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[15] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[16] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[17] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[18] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(WW) System lacks support for changing MTRRs
(==) ark(0): Backing store disabled
(II) ark(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	Solid Horizontal and Vertical Lines
(II) ark(0): Acceleration enabled
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension LBX
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
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 5
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0





Any suggestions are greatly appreciated!

---

### Post by Brian Smith on 2006-01-18
bump bump...

does anyone have another idea what I should check, post here, or edit?

thanks for reading.

---

