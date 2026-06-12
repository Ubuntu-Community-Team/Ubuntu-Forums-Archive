---
title: "Dual Monitors on nforce"
date: 2006-03-20
forum: Hardware &amp; Laptops
---

### Post by munwin on 2006-03-20
I have an Nforce dual video out motherboard.
I have loaded the binary nvidia driver - all good.
Before X starts, I get mirrored output to my two monitors (I suspect this is a default hardware thing).
When X starts, I get a normal screen on the first monitor, and garbage on the second (with xorg.conf #1 below).
Using xorg.conf #2 (below), I get major artifacts on screen 1, and nothing at all (although it appears to be 'on') on screen 2.
I have tried restarting X and rebooting with each pf the below xorg.conf's. Only #1 gives me a useable X.
I'd like to be able to have a desktop span the two monitors.
Any help much appreciated.
Mark.

xorg.conf #1
----------------
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
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV18 [GeForce4 MX - nForce GPU]"
	Driver		"nv"
	BusID		"PCI:2:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	VendorName	"Bridge"
	ModelName	"Bridge BM17MC"
	HorizSync	30.0-70.0
	VertRefresh	50.0-160.0
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV18 [GeForce4 MX - nForce GPU]"
	Monitor		"Generic Monitor"
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
EndSection

Section "DRI"
	Mode	0666
EndSection





xorg.conf #2
----------------
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
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV18 [GeForce4 MX - nForce GPU] - Primary"
	Driver		"nvidia"
	BusID		"PCI:2:0:0"
#	Option		"UseFBDev"		"true"
        Option          "MergedFB" "true"
        Option          "MetaModes" "1280x854 1280x854-1280x1024"
        Option          "MergedDPI" "100 100"
        Option          "CRT2Position" "LeftOf"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV18 [GeForce4 MX - nForce GPU] - Secondary"
	Driver		"nvidia"
	BusID		"PCI:2:0:0"
#	Option		"UseFBDev"		"true"
	Screen		1
EndSection

Section "Monitor"
	Identifier	"Monitor0"
	VendorName	"Bridge"
	ModelName	"Bridge BM17MC"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Monitor"
	Identifier	"Monitor1"
	VendorName	"Samtron"
	ModelName	"Samtron SC-728FXL"
	Option		"DPMS"
	HorizSync	30-69
	VertRefresh	50-150
EndSection

Section "Screen"
	Identifier	"Primary Screen"
	Device		"NVIDIA Corporation NV18 [GeForce4 MX - nForce GPU] - Primary"
	Monitor		"Monitor0"
	DefaultDepth	24
	SubSection "Display"
		Depth		16
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Secondary Screen"
	Device		"NVIDIA Corporation NV18 [GeForce4 MX - nForce GPU] - Secondary"
	Monitor		"Monitor1"
	DefaultDepth	24
	SubSection "Display"
		Depth		16
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerFlags"
	Option	"Xinerama" "ON"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen 0	"Primary Screen" 0 0
	Screen 1	"Secondary Screen" LeftOf "Primary Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by munwin on 2006-03-20
X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.12 i686
Current Operating System: Linux dapper 2.6.15-18-386 #1 PREEMPT Thu Mar 9 14:41:49 UTC 2006 i686
Build Date: 21 December 2005
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Mar 20 20:15:54 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Primary Screen" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "NVIDIA Corporation NV18 [GeForce4 MX - nForce GPU] - Primary"
(**) |-->Screen "Secondary Screen" (1)
(**) |   |-->Monitor "Monitor1"
(**) |   |-->Device "NVIDIA Corporation NV18 [GeForce4 MX - nForce GPU] - Secondary"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Option "Xinerama" "ON"
(**) Xinerama: enabled
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
***Removed to fit post char limit
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:8:0), (0,1,1), BCTRL: 0x0202 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xec000000 - 0xedffffff (0x2000000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xe4000000 - 0xebffffff (0x8000000) MX[B]
(--) PCI:*(2:0:0) nVidia Corporation NV18 [GeForce4 MX - nForce GPU] rev 163, Mem @ 0xec000000/24, 0xe4000000/26, 0xe8000000/19
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
(II) PCI Memory resource overlap reduced 0xe0000000 from 0xe3ffffff to 0xdfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xee085000 - 0xee08503f (0x40) MX[B]
	[1] -1	0	0xee084000 - 0xee0847ff (0x800) MX[B]
	[2] -1	0	0xee082000 - 0xee082fff (0x1000) MX[B]
	[3] -1	0	0xee000000 - 0xee07ffff (0x80000) MX[B]
	[4] -1	0	0xee080000 - 0xee080fff (0x1000) MX[B]
	[5] -1	0	0xee087000 - 0xee0870ff (0x100) MX[B]
	[6] -1	0	0xee086000 - 0xee086fff (0x1000) MX[B]
	[7] -1	0	0xee081000 - 0xee081fff (0x1000) MX[B]
	[8] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[9] -1	0	0xe8000000 - 0xe807ffff (0x80000) MX[B](B)
	[10] -1	0	0xe4000000 - 0xe7ffffff (0x4000000) MX[B](B)
	[11] -1	0	0xec000000 - 0xecffffff (0x1000000) MX[B](B)
	[12] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[13] -1	0	0x0000dc00 - 0x0000dc7f (0x80) IX[B]
	[14] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[15] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[16] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xee085000 - 0xee08503f (0x40) MX[B]
	[1] -1	0	0xee084000 - 0xee0847ff (0x800) MX[B]
	[2] -1	0	0xee082000 - 0xee082fff (0x1000) MX[B]
	[3] -1	0	0xee000000 - 0xee07ffff (0x80000) MX[B]
	[4] -1	0	0xee080000 - 0xee080fff (0x1000) MX[B]
	[5] -1	0	0xee087000 - 0xee0870ff (0x100) MX[B]
	[6] -1	0	0xee086000 - 0xee086fff (0x1000) MX[B]
	[7] -1	0	0xee081000 - 0xee081fff (0x1000) MX[B]
	[8] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[9] -1	0	0xe8000000 - 0xe807ffff (0x80000) MX[B](B)
	[10] -1	0	0xe4000000 - 0xe7ffffff (0x4000000) MX[B](B)
	[11] -1	0	0xec000000 - 0xecffffff (0x1000000) MX[B](B)
	[12] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[13] -1	0	0x0000dc00 - 0x0000dc7f (0x80) IX[B]
	[14] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[15] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[16] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
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
	[5] -1	0	0xee085000 - 0xee08503f (0x40) MX[B]
	[6] -1	0	0xee084000 - 0xee0847ff (0x800) MX[B]
	[7] -1	0	0xee082000 - 0xee082fff (0x1000) MX[B]
	[8] -1	0	0xee000000 - 0xee07ffff (0x80000) MX[B]
	[9] -1	0	0xee080000 - 0xee080fff (0x1000) MX[B]
	[10] -1	0	0xee087000 - 0xee0870ff (0x100) MX[B]
	[11] -1	0	0xee086000 - 0xee086fff (0x1000) MX[B]
	[12] -1	0	0xee081000 - 0xee081fff (0x1000) MX[B]
	[13] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[14] -1	0	0xe8000000 - 0xe807ffff (0x80000) MX[B](B)
	[15] -1	0	0xe4000000 - 0xe7ffffff (0x4000000) MX[B](B)
	[16] -1	0	0xec000000 - 0xecffffff (0x1000000) MX[B](B)
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[20] -1	0	0x0000dc00 - 0x0000dc7f (0x80) IX[B]
	[21] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[22] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[23] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg/modules/linux/libdrm.so
(II) Module drm: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension XFree86-DRI
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
(II) Primary Device is: PCI 02:00:0
(--) Chipset NVIDIA GPU found
(--) Chipset NVIDIA GPU found
(II) resource ranges after xf86ClaimFixedResources() call:
	
***Removed to fit post char limit
(II) resource ranges after probing:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	
***Removed to fit post char limit
(II) Setting vga for screen 0.
(II) Setting vga for screen 1.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "MetaModes" "1152x864"
(WW) NVIDIA(0): Cannot use option "MetaModes" when TwinView is not enabled
(--) NVIDIA(0): Linear framebuffer at 0xE4000000
(--) NVIDIA(0): MMIO registers at 0xEC000000
(II) NVIDIA(0): NVIDIA GPU detected as: GeForce4 MX Integrated GPU
(--) NVIDIA(0): VideoBIOS: 04.1f.00.07.00
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): VideoRAM: 32768 kBytes
(II) NVIDIA(0): Connected display device(s): CRT-0, CRT-1
(WW) NVIDIA(0): Multiple displays connected, but only one display allowed;
(WW) NVIDIA(0):      using first display
(--) NVIDIA(0): CRT-0: maximum pixel clock: 300 MHz
(WW) NVIDIA(0): Unable to read EDID for display device CRT-0
(II) NVIDIA(0): Frequency information for CRT-0:
(II) NVIDIA(0):   HorizSync   : 30.000-70.000 kHz
(II) NVIDIA(0):   VertRefresh : 50.000-160.000 Hz
(II) NVIDIA(0):      (HorizSync from HorizSync in X Config Monitor section)
(II) NVIDIA(0):      (VertRefresh from VertRefresh in X Config Monitor
(II) NVIDIA(0):      section)
(II) NVIDIA(0): Monitor0: Using hsync range of 30.00-70.00 kHz
(II) NVIDIA(0): Monitor0: Using vrefresh range of 50.00-160.00 Hz
(II) NVIDIA(0): Clock range:  12.00 to 300.00 MHz
(II) NVIDIA(0): Not using default mode "1280x960" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x480" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1280x1024" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x512" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1280x1024" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x512" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1792x1344" (hsync out of range)
(II) NVIDIA(0): Not using default mode "896x672" (hsync out of range)
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
(II) NVIDIA(0): Not using default mode "1152x864" (hsync out of range)
(II) NVIDIA(0): Not using default mode "576x432" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1400x1050" (hsync out of range)
(II) NVIDIA(0): Not using default mode "700x525" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1400x1050" (hsync out of range)
(II) NVIDIA(0): Not using default mode "700x525" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1400x1050" (hsync out of range)
(II) NVIDIA(0): Not using default mode "700x525" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x600" (hsync out of range)
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
(**) NVIDIA(0): Validated modes for display device CRT-0:
(**) NVIDIA(0):      Default mode "1152x864": 108.0 MHz, 67.5 kHz, 75.0 Hz
(**) NVIDIA(0):      Default mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
(**) NVIDIA(0):      Default mode "800x600": 56.3 MHz, 53.7 kHz, 85.1 Hz
(**) NVIDIA(0):      Default mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
(II) NVIDIA(0): Virtual screen size determined to be 1152 x 864
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
(**) NVIDIA(1): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(1): RGB weight 888
(==) NVIDIA(1): Default visual is TrueColor
(==) NVIDIA(1): Using gamma correction (1.0, 1.0, 1.0)
(--) NVIDIA(1): Linear framebuffer at 0xE4000000
(--) NVIDIA(1): MMIO registers at 0xEC000000
(II) NVIDIA(1): NVIDIA GPU detected as: GeForce4 MX Integrated GPU
(--) NVIDIA(1): VideoBIOS: 04.1f.00.07.00
(--) NVIDIA(1): Interlaced video modes are supported on this GPU
(II) NVIDIA(1): Detected AGP rate: 4X
(--) NVIDIA(1): VideoRAM: 32768 kBytes
(II) NVIDIA(1): Connected display device(s): CRT-0, CRT-1
(--) NVIDIA(1): CRT-1: maximum pixel clock: 300 MHz
(WW) NVIDIA(1): Unable to read EDID for display device CRT-1
(II) NVIDIA(1): Frequency information for CRT-1:
(II) NVIDIA(1):   HorizSync   : 30.000-69.000 kHz
(II) NVIDIA(1):   VertRefresh : 50.000-150.000 Hz
(II) NVIDIA(1):      (HorizSync from HorizSync in X Config Monitor section)
(II) NVIDIA(1):      (VertRefresh from VertRefresh in X Config Monitor
(II) NVIDIA(1):      section)
(II) NVIDIA(1): Monitor1: Using hsync range of 30.00-69.00 kHz
(II) NVIDIA(1): Monitor1: Using vrefresh range of 50.00-150.00 Hz
(II) NVIDIA(1): Clock range:  12.00 to 300.00 MHz
(II) NVIDIA(1): Not using default mode "1280x960" (hsync out of range)
(II) NVIDIA(1): Not using default mode "640x480" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1280x1024" (hsync out of range)
(II) NVIDIA(1): Not using default mode "640x512" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1280x1024" (hsync out of range)
(II) NVIDIA(1): Not using default mode "640x512" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(1): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(1): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(1): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(1): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(1): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1792x1344" (hsync out of range)
(II) NVIDIA(1): Not using default mode "896x672" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1792x1344" (hsync out of range)
(II) NVIDIA(1): Not using default mode "896x672" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1856x1392" (hsync out of range)
(II) NVIDIA(1): Not using default mode "928x696" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1856x1392" (hsync out of range)
(II) NVIDIA(1): Not using default mode "928x696" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1920x1440" (hsync out of range)
(II) NVIDIA(1): Not using default mode "960x720" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1920x1440" (hsync out of range)
(II) NVIDIA(1): Not using default mode "960x720" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1152x864" (hsync out of range)
(II) NVIDIA(1): Not using default mode "576x432" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1400x1050" (hsync out of range)
(II) NVIDIA(1): Not using default mode "700x525" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1400x1050" (hsync out of range)
(II) NVIDIA(1): Not using default mode "700x525" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1400x1050" (hsync out of range)
(II) NVIDIA(1): Not using default mode "700x525" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1920x1200" (hsync out of range)
(II) NVIDIA(1): Not using default mode "960x600" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1920x1200" (hsync out of range)
(II) NVIDIA(1): Not using default mode "960x600" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1920x1440" (hsync out of range)
(II) NVIDIA(1): Not using default mode "960x720" (hsync out of range)
(II) NVIDIA(1): Not using default mode "2048x1536" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(1): Not using default mode "2048x1536" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(1): Not using default mode "2048x1536" (hsync out of range)
(II) NVIDIA(1): Not using default mode "1024x768" (hsync out of range)
(**) NVIDIA(1): Validated modes for display device CRT-1:
(**) NVIDIA(1):      Default mode "1152x864": 108.0 MHz, 67.5 kHz, 75.0 Hz
(**) NVIDIA(1):      Default mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
(**) NVIDIA(1):      Default mode "800x600": 56.3 MHz, 53.7 kHz, 85.1 Hz
(**) NVIDIA(1):      Default mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
(II) NVIDIA(1): Virtual screen size determined to be 1152 x 864
(++) NVIDIA(1): DPI set to (100, 100); computed from -dpi X commandline option
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Reloading /usr/lib/xorg/modules/libfb.so
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Reloading /usr/lib/xorg/modules/libramdac.so
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  Yes, I do.
(II) LoadModule: "rac"
(II) Loading /usr/lib/xorg/modules/librac.so
(II) Module rac: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) resource ranges after preInit:
	[0] 0	0	0xe8000000 - 0xe807ffff (0x80000) MX[B]
	[1] 0	0	0xe4000000 - 0xe7ffffff (0x4000000) MX[B]
	[2] 0	0	0xec000000 - 0xecffffff (0x1000000) MX[B]
	[3] 0	0	0xe8000000 - 0xe807ffff (0x80000) MX[B]
	[4] 0	0	0xe4000000 - 0xe7ffffff (0x4000000) MX[B]
	[5] 0	0	0xec000000 - 0xecffffff (0x1000000) MX[B]
	[6] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[7] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[8] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[9] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[10] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[11] -1	0	0xee085000 - 0xee08503f (0x40) MX[B]
	[12] -1	0	0xee084000 - 0xee0847ff (0x800) MX[B]
	[13] -1	0	0xee082000 - 0xee082fff (0x1000) MX[B]
	[14] -1	0	0xee000000 - 0xee07ffff (0x80000) MX[B]
	[15] -1	0	0xee080000 - 0xee080fff (0x1000) MX[B]
	[16] -1	0	0xee087000 - 0xee0870ff (0x100) MX[B]
	[17] -1	0	0xee086000 - 0xee086fff (0x1000) MX[B]
	[18] -1	0	0xee081000 - 0xee081fff (0x1000) MX[B]
	[19] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[20] -1	0	0xe8000000 - 0xe807ffff (0x80000) MX[B](B)
	[21] -1	0	0xe4000000 - 0xe7ffffff (0x4000000) MX[B](B)
	[22] -1	0	0xec000000 - 0xecffffff (0x1000000) MX[B](B)
	[23] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[24] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[25] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[26] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[27] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[28] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[29] -1	0	0x0000dc00 - 0x0000dc7f (0x80) IX[B]
	[30] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[31] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[32] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[33] 0	0	0xe80803b0 - 0xe80803bb (0xc) IS[B]
	[34] 0	0	0xe80803c0 - 0xe80803df (0x20) IS[B]
(II) NVIDIA(0): Setting mode "1152x864"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(WW) NVIDIA(0): Option "MergedFB" is not used
(WW) NVIDIA(0): Option "MergedDPI" is not used
(WW) NVIDIA(0): Option "CRT2Position" is not used
(==) RandR enabled
(II) NVIDIA(1): Setting mode "1152x864"
(II) NVIDIA(1): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(1): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(1): Backing store disabled
(==) NVIDIA(1): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(1): DPMS enabled
(==) RandR enabled
(II) Setting vga for screen 0.
(II) Setting vga for screen 1.
Screen 0 is using RAC for io
Screen 1 is using RAC for io
(II) Entity 0 shares no resources
(II) Entity 1 shares no resources
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
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Configured Mouse: ZAxisMapping: buttons 4, 5, 6 and 7
(**) Configured Mouse: Buttons: 11
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(II) Screen 0 shares mem & io resources
(II) Screen 1 shares mem & io resources
(II) Screen 0 shares mem & io resources
(II) Screen 1 shares mem & io resources

---

### Post by munwin on 2006-03-22
Bump.
Little help ???

](*,)    :-k    :confused:

---

