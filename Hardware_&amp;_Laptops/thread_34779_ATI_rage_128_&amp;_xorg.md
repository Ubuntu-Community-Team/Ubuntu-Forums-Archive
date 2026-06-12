---
title: "ATI rage 128 &amp; xorg"
date: 2005-05-16
forum: Hardware &amp; Laptops
---

### Post by SilvioTO on 2005-05-16
Hi, I installed on my friend pc hoary. For 5 days all ok, but now x server don't start. The problem it seems ati rage 128 video card. At startup for 3 times ubuntu try to start gnome, but after freeze on blue screen that inform the x server is not configured properly. Only way to reboot pc is press reset button. I trying to change the file xorg.conf with vga driver instead of ati driver and 16 depth. Nothing to do.

I don't know to do. help. thanks.


the actually xorg.conf:


X Window System Version 6.8.2 (Ubuntu 6.8.2-10 20050405154308 [email]root@terranova.warthogs.hbd.com[/email])
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF] 
Current Operating System: Linux ubuntu 2.6.10-5-386 #1 Tue Apr 5 12:12:40 UTC 2005 i686
Build Date: 05 April 2005
	Before reporting problems, check [http://wiki.X.Org](http://wiki.X.Org)
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.10-5-386 (buildd@terranova) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Tue Apr 5 12:12:40 UTC 2005 
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon May 16 15:44:49 2005
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "NEC CI A526"
(**) |   |-->Device "ATI Technologies, Inc. Rage 128 Pro Ultra (TF)"
(**) |-->Input Device "Generic Keyboard"
(**) Option "XkbRules" "xorg"
(**) XKB: rules: "xorg"
(**) Option "XkbModel" "pc105"
(**) XKB: model: "pc105"
(**) Option "XkbLayout" "it"
(**) XKB: layout: "it"
(==) Keyboard: CustomKeycode disabled
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/lib/X11/fonts/misc" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/lib/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/lib/X11/fonts/100dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/lib/X11/fonts/75dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/lib/X11/fonts/Type1" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/lib/X11/fonts/CID" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/lib/X11/fonts/100dpi" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/lib/X11/fonts/75dpi" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID").
(**) FontPath set to "unix/:7100,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
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
(--) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,1130 card 1043,8027 rev 04 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,1131 card 0000,0000 rev 04 class 06,04,00 hdr 01
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,2440 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,244b card 1043,8027 rev 02 class 01,01,80 hdr 00
(II) PCI: 00:1f:2: chip 8086,2442 card 1043,8027 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1f:3: chip 8086,2443 card 1043,8027 rev 02 class 0c,05,00 hdr 00
(II) PCI: 00:1f:4: chip 8086,2444 card 1043,8027 rev 02 class 0c,03,00 hdr 00
(II) PCI: 01:00:0: chip 1002,5446 card 1002,0018 rev 00 class 03,00,00 hdr 00
(II) PCI: 02:0b:0: chip 10ec,8139 card 10ec,8139 rev 10 class 02,00,00 hdr 00
(II) PCI: 02:0c:0: chip 1274,5880 card 1274,2000 rev 02 class 04,01,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xf3000000 - 0xf3dfffff (0xe00000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xf3f00000 - 0xf7ffffff (0x4100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[1] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[2] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[3] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xf2800000 - 0xf2ffffff (0x800000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xf3e00000 - 0xf3efffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) ATI Technologies Inc Rage 128 Pro Ultra TF rev 0, Mem @ 0xf4000000/26, 0xf3000000/14, I/O @ 0xd800/8, BIOS @ 0xf3fe0000/17
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
(II) PCI Memory resource overlap reduced 0xf8000000 from 0xfbffffff to 0xf7ffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xf2800000 - 0xf28000ff (0x100) MX[B]
	[1] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[2] -1	0	0xf3fe0000 - 0xf3ffffff (0x20000) MX[B](B)
	[3] -1	0	0xf3000000 - 0xf3003fff (0x4000) MX[B](B)
	[4] -1	0	0xf4000000 - 0xf7ffffff (0x4000000) MX[B](B)
	[5] -1	0	0x0000b400 - 0x0000b43f (0x40) IX[B]
	[6] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[7] -1	0	0x0000a000 - 0x0000a01f (0x20) IX[B]
	[8] -1	0	0x0000e800 - 0x0000e80f (0x10) IX[B]
	[9] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[10] -1	0	0x0000a800 - 0x0000a80f (0x10) IX[B]
	[11] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xf2800000 - 0xf28000ff (0x100) MX[B]
	[1] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[2] -1	0	0xf3fe0000 - 0xf3ffffff (0x20000) MX[B](B)
	[3] -1	0	0xf3000000 - 0xf3003fff (0x4000) MX[B](B)
	[4] -1	0	0xf4000000 - 0xf7ffffff (0x4000000) MX[B](B)
	[5] -1	0	0x0000b400 - 0x0000b43f (0x40) IX[B]
	[6] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[7] -1	0	0x0000a000 - 0x0000a01f (0x20) IX[B]
	[8] -1	0	0x0000e800 - 0x0000e80f (0x10) IX[B]
	[9] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[10] -1	0	0x0000a800 - 0x0000a80f (0x10) IX[B]
	[11] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B](B)
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
	[5] -1	0	0xf2800000 - 0xf28000ff (0x100) MX[B]
	[6] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[7] -1	0	0xf3fe0000 - 0xf3ffffff (0x20000) MX[B](B)
	[8] -1	0	0xf3000000 - 0xf3003fff (0x4000) MX[B](B)
	[9] -1	0	0xf4000000 - 0xf7ffffff (0x4000000) MX[B](B)
	[10] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[11] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[12] -1	0	0x0000b400 - 0x0000b43f (0x40) IX[B]
	[13] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[14] -1	0	0x0000a000 - 0x0000a01f (0x20) IX[B]
	[15] -1	0	0x0000e800 - 0x0000e80f (0x10) IX[B]
	[16] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[17] -1	0	0x0000a800 - 0x0000a80f (0x10) IX[B]
	[18] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B](B)
(II) LoadModule: "bitmap"
(II) Reloading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Loading font Bitmap
(II) LoadModule: "dbe"
(II) Loading /usr/X11R6/lib/modules/extensions/libdbe.a
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension DOUBLE-BUFFER
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
(II) Loading extension FontCache
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
(II) LoadModule: "record"
(II) Loading /usr/X11R6/lib/modules/extensions/librecord.a
(II) Module record: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension RECORD
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
(II) LoadModule: "vga"
(II) Loading /usr/X11R6/lib/modules/drivers/vga_drv.o
(II) Module vga: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 4.0.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "keyboard"
(II) Loading /usr/X11R6/lib/modules/input/keyboard_drv.o
(II) Module keyboard: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) LoadModule: "mouse"
(II) Loading /usr/X11R6/lib/modules/input/mouse_drv.o
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) VGA: Generic VGA driver (version 4.0) for chipsets: generic
(II) Primary Device is: PCI 01:00:0
(--) Chipset generic found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xf2800000 - 0xf28000ff (0x100) MX[B]
	[6] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[7] -1	0	0xf3fe0000 - 0xf3ffffff (0x20000) MX[B](B)
	[8] -1	0	0xf3000000 - 0xf3003fff (0x4000) MX[B](B)
	[9] -1	0	0xf4000000 - 0xf7ffffff (0x4000000) MX[B](B)
	[10] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[11] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[12] -1	0	0x0000b400 - 0x0000b43f (0x40) IX[B]
	[13] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[14] -1	0	0x0000a000 - 0x0000a01f (0x20) IX[B]
	[15] -1	0	0x0000e800 - 0x0000e80f (0x10) IX[B]
	[16] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[17] -1	0	0x0000a800 - 0x0000a80f (0x10) IX[B]
	[18] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xf2800000 - 0xf28000ff (0x100) MX[B]
	[6] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[7] -1	0	0xf3fe0000 - 0xf3ffffff (0x20000) MX[B](B)
	[8] -1	0	0xf3000000 - 0xf3003fff (0x4000) MX[B](B)
	[9] -1	0	0xf4000000 - 0xf7ffffff (0x4000000) MX[B](B)
	[10] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[11] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[12] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000b400 - 0x0000b43f (0x40) IX[B]
	[16] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[17] -1	0	0x0000a000 - 0x0000a01f (0x20) IX[B]
	[18] -1	0	0x0000e800 - 0x0000e80f (0x10) IX[B]
	[19] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[20] -1	0	0x0000a800 - 0x0000a80f (0x10) IX[B]
	[21] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B](B)
	[22] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[23] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/X11R6/lib/modules/linux/libint10.a
(II) VGA(0): initializing int10.
(II) VGA(0): Primary V_BIOS segment is: 0xc000
(EE) VGA(0): Given depth (16) is not supported by this driver.
(II) UnloadModule: "vga"
(II) UnloadModule: "int10"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at [http://wiki.X.Org](http://wiki.X.Org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

---

### Post by guX on 2005-05-16
[QUOTE=SilvioTO]Hi, I installed on my friend pc hoary. For 5 days all ok, but now x server don't start. The problem it seems ati rage 128 video card. At startup for 3 times ubuntu try to start gnome, but after freeze on blue screen that inform the x server is not configured properly. Only way to reboot pc is press reset button. I trying to change the file xorg.conf with vga driver instead of ati driver and 16 depth. Nothing to do.

I don't know to do. help. thanks.


the actually xorg.conf:


X Window System Version 6.8.2 (Ubuntu 6.8.2-10 20050405154308 [email]root@terranova.warthogs.hbd.com[/email])
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF] 
Current Operating System: Linux ubuntu 2.6.10-5-386 #1 Tue Apr 5 12:12:40 UTC 2005 i686
Build Date: 05 April 2005
	Before reporting problems, check [http://wiki.X.Org](http://wiki.X.Org)
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.10-5-386 (buildd@terranova) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Tue Apr 5 12:12:40 UTC 2005 
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon May 16 15:44:49 2005
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "NEC CI A526"
(**) |   |-->Device "ATI Technologies, Inc. Rage 128 Pro Ultra (TF)"
(**) |-->Input Device "Generic Keyboard"
(**) Option "XkbRules" "xorg"
(**) XKB: rules: "xorg"
(**) Option "XkbModel" "pc105"
(**) XKB: model: "pc105"
(**) Option "XkbLayout" "it"
(**) XKB: layout: "it"
(==) Keyboard: CustomKeycode disabled
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/lib/X11/fonts/misc" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/lib/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/lib/X11/fonts/100dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/lib/X11/fonts/75dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/lib/X11/fonts/Type1" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/lib/X11/fonts/CID" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/lib/X11/fonts/100dpi" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/lib/X11/fonts/75dpi" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID").
(**) FontPath set to "unix/:7100,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
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
(--) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,1130 card 1043,8027 rev 04 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,1131 card 0000,0000 rev 04 class 06,04,00 hdr 01
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,2440 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,244b card 1043,8027 rev 02 class 01,01,80 hdr 00
(II) PCI: 00:1f:2: chip 8086,2442 card 1043,8027 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1f:3: chip 8086,2443 card 1043,8027 rev 02 class 0c,05,00 hdr 00
(II) PCI: 00:1f:4: chip 8086,2444 card 1043,8027 rev 02 class 0c,03,00 hdr 00
(II) PCI: 01:00:0: chip 1002,5446 card 1002,0018 rev 00 class 03,00,00 hdr 00
(II) PCI: 02:0b:0: chip 10ec,8139 card 10ec,8139 rev 10 class 02,00,00 hdr 00
(II) PCI: 02:0c:0: chip 1274,5880 card 1274,2000 rev 02 class 04,01,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xf3000000 - 0xf3dfffff (0xe00000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xf3f00000 - 0xf7ffffff (0x4100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[1] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[2] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[3] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xf2800000 - 0xf2ffffff (0x800000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xf3e00000 - 0xf3efffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) ATI Technologies Inc Rage 128 Pro Ultra TF rev 0, Mem @ 0xf4000000/26, 0xf3000000/14, I/O @ 0xd800/8, BIOS @ 0xf3fe0000/17
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
(II) PCI Memory resource overlap reduced 0xf8000000 from 0xfbffffff to 0xf7ffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xf2800000 - 0xf28000ff (0x100) MX[B]
	[1] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[2] -1	0	0xf3fe0000 - 0xf3ffffff (0x20000) MX[B](B)
	[3] -1	0	0xf3000000 - 0xf3003fff (0x4000) MX[B](B)
	[4] -1	0	0xf4000000 - 0xf7ffffff (0x4000000) MX[B](B)
	[5] -1	0	0x0000b400 - 0x0000b43f (0x40) IX[B]
	[6] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[7] -1	0	0x0000a000 - 0x0000a01f (0x20) IX[B]
	[8] -1	0	0x0000e800 - 0x0000e80f (0x10) IX[B]
	[9] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[10] -1	0	0x0000a800 - 0x0000a80f (0x10) IX[B]
	[11] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xf2800000 - 0xf28000ff (0x100) MX[B]
	[1] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[2] -1	0	0xf3fe0000 - 0xf3ffffff (0x20000) MX[B](B)
	[3] -1	0	0xf3000000 - 0xf3003fff (0x4000) MX[B](B)
	[4] -1	0	0xf4000000 - 0xf7ffffff (0x4000000) MX[B](B)
	[5] -1	0	0x0000b400 - 0x0000b43f (0x40) IX[B]
	[6] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[7] -1	0	0x0000a000 - 0x0000a01f (0x20) IX[B]
	[8] -1	0	0x0000e800 - 0x0000e80f (0x10) IX[B]
	[9] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[10] -1	0	0x0000a800 - 0x0000a80f (0x10) IX[B]
	[11] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B](B)
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
	[5] -1	0	0xf2800000 - 0xf28000ff (0x100) MX[B]
	[6] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[7] -1	0	0xf3fe0000 - 0xf3ffffff (0x20000) MX[B](B)
	[8] -1	0	0xf3000000 - 0xf3003fff (0x4000) MX[B](B)
	[9] -1	0	0xf4000000 - 0xf7ffffff (0x4000000) MX[B](B)
	[10] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[11] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[12] -1	0	0x0000b400 - 0x0000b43f (0x40) IX[B]
	[13] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[14] -1	0	0x0000a000 - 0x0000a01f (0x20) IX[B]
	[15] -1	0	0x0000e800 - 0x0000e80f (0x10) IX[B]
	[16] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[17] -1	0	0x0000a800 - 0x0000a80f (0x10) IX[B]
	[18] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B](B)
(II) LoadModule: "bitmap"
(II) Reloading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Loading font Bitmap
(II) LoadModule: "dbe"
(II) Loading /usr/X11R6/lib/modules/extensions/libdbe.a
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension DOUBLE-BUFFER
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
(II) Loading extension FontCache
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
(II) LoadModule: "record"
(II) Loading /usr/X11R6/lib/modules/extensions/librecord.a
(II) Module record: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension RECORD
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
(II) LoadModule: "vga"
(II) Loading /usr/X11R6/lib/modules/drivers/vga_drv.o
(II) Module vga: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 4.0.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "keyboard"
(II) Loading /usr/X11R6/lib/modules/input/keyboard_drv.o
(II) Module keyboard: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) LoadModule: "mouse"
(II) Loading /usr/X11R6/lib/modules/input/mouse_drv.o
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) VGA: Generic VGA driver (version 4.0) for chipsets: generic
(II) Primary Device is: PCI 01:00:0
(--) Chipset generic found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xf2800000 - 0xf28000ff (0x100) MX[B]
	[6] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[7] -1	0	0xf3fe0000 - 0xf3ffffff (0x20000) MX[B](B)
	[8] -1	0	0xf3000000 - 0xf3003fff (0x4000) MX[B](B)
	[9] -1	0	0xf4000000 - 0xf7ffffff (0x4000000) MX[B](B)
	[10] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[11] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[12] -1	0	0x0000b400 - 0x0000b43f (0x40) IX[B]
	[13] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[14] -1	0	0x0000a000 - 0x0000a01f (0x20) IX[B]
	[15] -1	0	0x0000e800 - 0x0000e80f (0x10) IX[B]
	[16] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[17] -1	0	0x0000a800 - 0x0000a80f (0x10) IX[B]
	[18] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xf2800000 - 0xf28000ff (0x100) MX[B]
	[6] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[7] -1	0	0xf3fe0000 - 0xf3ffffff (0x20000) MX[B](B)
	[8] -1	0	0xf3000000 - 0xf3003fff (0x4000) MX[B](B)
	[9] -1	0	0xf4000000 - 0xf7ffffff (0x4000000) MX[B](B)
	[10] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[11] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[12] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000b400 - 0x0000b43f (0x40) IX[B]
	[16] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[17] -1	0	0x0000a000 - 0x0000a01f (0x20) IX[B]
	[18] -1	0	0x0000e800 - 0x0000e80f (0x10) IX[B]
	[19] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[20] -1	0	0x0000a800 - 0x0000a80f (0x10) IX[B]
	[21] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B](B)
	[22] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[23] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/X11R6/lib/modules/linux/libint10.a
(II) VGA(0): initializing int10.
(II) VGA(0): Primary V_BIOS segment is: 0xc000
(EE) VGA(0): Given depth (16) is not supported by this driver.
(II) UnloadModule: "vga"
(II) UnloadModule: "int10"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at [http://wiki.X.Org](http://wiki.X.Org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.[/QUOTE]
 Hello. I have a similar problem - I just posted a thread about it. I fixed this problem temporarily by going "sudo dpgk-reconfigure xserver-xorg" and selecting the "vesa" drivers. This isn't a solution, but it'll work until somebody who is more qualified to answer your question does so.

---

### Post by SilvioTO on 2005-05-18
Try to change in file xorg.conf the driver to "r128". I'm hope this work... Post the result, negative or positive. Thanks.

---

