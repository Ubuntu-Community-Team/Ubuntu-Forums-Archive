---
title: "Extremely confused about the new xorg.conf in Kubuntu edgy"
date: 2006-10-29
forum: Hardware &amp; Laptops
---

### Post by DigitalDuality on 2006-10-29
well after a long long disaster of kubuntu edgy dist-upgrade.. and now a clean install.. and EVERYTHING is working.. i'm a bit perplexed.

I was begining to play with beryl and then i looked at my xorg.conf

I manually set it to a nvidia driver, right now i'm looking at a 1600x1200 resolution.  i remember doing this, i'm currently running off of my nvidia card as well. and everything just works.  but what i'm confused at.. is my xorg.  check this out:

```
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

```

my resolution isn't listed, my driver isn't listed, the BUSID for the intel card is'nt commented out.  Also the monitor is listed as generic.. and it wasn't a few days ago.  Also the vert and horizontal refresh rates are way off.

What gives?  By looking at that file, my setup should not be running x properly right now but it is.  I even restarted to make sure it still does, and it stars right up.  Now i'm scared to touch beryl and make the changes i need.

---

### Post by tonyr on 2006-10-29
Look at **/var/log/Xorg.0.log** to see what X startup says about
all this.

---

### Post by DigitalDuality on 2006-10-29
here it is, it still doesn't make any sense to me:

```


X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686 
Current Operating System: Linux kubuntu 2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 i686
Build Date: 07 July 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Oct 28 12:37:34 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Envision EFT"
(**) |   |-->Device "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) `fonts.dir' not found (or not valid) in "/usr/share/X11/fonts/misc".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/usr/share/X11/fonts/misc").
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/Type1" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType").
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/misc/,
	/usr/share/fonts/X11/TTF/,
	/usr/share/fonts/X11/OTF,
	/usr/share/fonts/X11/Type1/,
	/usr/share/fonts/X11/CID/,
	/usr/share/fonts/X11/100dpi/,
	/usr/share/fonts/X11/75dpi/
(==) RgbPath set to "/usr/share/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.0
	X.Org XInput driver : 0.6
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2560 card 1043,8093 rev 01 class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 8086,2562 card 1043,8093 rev 01 class 03,00,00 hdr 00
(II) PCI: 00:1d:0: chip 8086,24c2 card 1043,8089 rev 01 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24c4 card 1043,8089 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,24c7 card 1043,8089 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24cd card 1043,8089 rev 01 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev 81 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24c0 card 0000,0000 rev 01 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24cb card 1043,8089 rev 01 class 01,01,8a hdr 00
(II) PCI: 00:1f:5: chip 8086,24c5 card 1043,8098 rev 01 class 04,01,00 hdr 00
(II) PCI: 01:0a:0: chip 10de,0326 card 0000,0000 rev a1 class 03,00,00 hdr 00
(II) PCI: 01:0b:0: chip 10b9,5237 card 10b9,5237 rev 03 class 0c,03,10 hdr 80
(II) PCI: 01:0b:1: chip 10b9,5237 card 10b9,5237 rev 03 class 0c,03,10 hdr 80
(II) PCI: 01:0b:2: chip 10b9,5237 card 10b9,5237 rev 03 class 0c,03,10 hdr 80
(II) PCI: 01:0b:3: chip 10b9,5239 card 10b9,5239 rev 01 class 0c,03,20 hdr 80
(II) PCI: 01:0d:0: chip 10ec,8139 card 1043,805b rev 10 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:30:0), (0,1,1), BCTRL: 0x000e (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[1] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[2] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[3] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xda800000 - 0xde7fffff (0x4000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xdff00000 - 0xe7ffffff (0x8100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI: (0:2:0) Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device rev 1, Mem @ 0xe8000000/27, 0xdf000000/19
(--) PCI:*(1:10:0) nVidia Corporation NV34 [GeForce FX 5500] rev 161, Mem @ 0xdd000000/24, 0xe0000000/27, BIOS @ 0xdffe0000/17
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xf0000000 from 0xf7ffffff to 0xefffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xda800000 - 0xda8000ff (0x100) MX[B]
	[1] -1	0	0xdb000000 - 0xdb0000ff (0x100) MX[B]
	[2] -1	0	0xdb800000 - 0xdb800fff (0x1000) MX[B]
	[3] -1	0	0xdc000000 - 0xdc000fff (0x1000) MX[B]
	[4] -1	0	0xdc800000 - 0xdc800fff (0x1000) MX[B]
	[5] -1	0	0x40000200 - 0x400002ff (0x100) MX[B]
	[6] -1	0	0x40000000 - 0x400001ff (0x200) MX[B]
	[7] -1	0	0xda000000 - 0xda0003ff (0x400) MX[B]
	[8] -1	0	0xde800000 - 0xde8003ff (0x400) MX[B]
	[9] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[10] -1	0	0xdffe0000 - 0xdfffffff (0x20000) MX[B](B)
	[11] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[12] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[14] -1	0	0x0000e100 - 0x0000e13f (0x40) IX[B]
	[15] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[16] -1	0	0x00009400 - 0x0000940f (0x10) IX[B]
	[17] -1	0	0x00009800 - 0x00009800 (0x1) IX[B]
	[18] -1	0	0x0000a000 - 0x0000a000 (0x1) IX[B]
	[19] -1	0	0x0000a400 - 0x0000a400 (0x1) IX[B]
	[20] -1	0	0x0000a800 - 0x0000a800 (0x1) IX[B]
	[21] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[22] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[23] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
(II) Inactive PCI resource ranges:
	[0] -1	0	0xdf000000 - 0xdf07ffff (0x80000) MX[B](B)
	[1] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xda800000 - 0xda8000ff (0x100) MX[B]
	[1] -1	0	0xdb000000 - 0xdb0000ff (0x100) MX[B]
	[2] -1	0	0xdb800000 - 0xdb800fff (0x1000) MX[B]
	[3] -1	0	0xdc000000 - 0xdc000fff (0x1000) MX[B]
	[4] -1	0	0xdc800000 - 0xdc800fff (0x1000) MX[B]
	[5] -1	0	0x40000200 - 0x400002ff (0x100) MX[B]
	[6] -1	0	0x40000000 - 0x400001ff (0x200) MX[B]
	[7] -1	0	0xda000000 - 0xda0003ff (0x400) MX[B]
	[8] -1	0	0xde800000 - 0xde8003ff (0x400) MX[B]
	[9] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[10] -1	0	0xdffe0000 - 0xdfffffff (0x20000) MX[B](B)
	[11] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[12] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[14] -1	0	0x0000e100 - 0x0000e13f (0x40) IX[B]
	[15] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[16] -1	0	0x00009400 - 0x0000940f (0x10) IX[B]
	[17] -1	0	0x00009800 - 0x00009800 (0x1) IX[B]
	[18] -1	0	0x0000a000 - 0x0000a000 (0x1) IX[B]
	[19] -1	0	0x0000a400 - 0x0000a400 (0x1) IX[B]
	[20] -1	0	0x0000a800 - 0x0000a800 (0x1) IX[B]
	[21] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[22] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[23] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0xdf000000 - 0xdf07ffff (0x80000) MX[B](B)
	[1] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xda800000 - 0xda8000ff (0x100) MX[B]
	[5] -1	0	0xdb000000 - 0xdb0000ff (0x100) MX[B]
	[6] -1	0	0xdb800000 - 0xdb800fff (0x1000) MX[B]
	[7] -1	0	0xdc000000 - 0xdc000fff (0x1000) MX[B]
	[8] -1	0	0xdc800000 - 0xdc800fff (0x1000) MX[B]
	[9] -1	0	0x40000200 - 0x400002ff (0x100) MX[B]
	[10] -1	0	0x40000000 - 0x400001ff (0x200) MX[B]
	[11] -1	0	0xda000000 - 0xda0003ff (0x400) MX[B]
	[12] -1	0	0xde800000 - 0xde8003ff (0x400) MX[B]
	[13] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[14] -1	0	0xdffe0000 - 0xdfffffff (0x20000) MX[B](B)
	[15] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[16] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[17] -1	0	0xdf000000 - 0xdf07ffff (0x80000) MX[B](B)
	[18] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[22] -1	0	0x0000e100 - 0x0000e13f (0x40) IX[B]
	[23] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[24] -1	0	0x00009400 - 0x0000940f (0x10) IX[B]
	[25] -1	0	0x00009800 - 0x00009800 (0x1) IX[B]
	[26] -1	0	0x0000a000 - 0x0000a000 (0x1) IX[B]
	[27] -1	0	0x0000a400 - 0x0000a400 (0x1) IX[B]
	[28] -1	0	0x0000a800 - 0x0000a800 (0x1) IX[B]
	[29] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[30] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[31] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg/modules/linux/libdrm.so
(II) Module drm: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
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
	compiled for 7.1.1, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8774
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.o
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8774
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) Wacom driver level: 47-0.7.2 $
(II) NVIDIA X Driver  1.0-8774  Tue Aug  1 20:56:50 PDT 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:0a:0
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xda800000 - 0xda8000ff (0x100) MX[B]
	[5] -1	0	0xdb000000 - 0xdb0000ff (0x100) MX[B]
	[6] -1	0	0xdb800000 - 0xdb800fff (0x1000) MX[B]
	[7] -1	0	0xdc000000 - 0xdc000fff (0x1000) MX[B]
	[8] -1	0	0xdc800000 - 0xdc800fff (0x1000) MX[B]
	[9] -1	0	0x40000200 - 0x400002ff (0x100) MX[B]
	[10] -1	0	0x40000000 - 0x400001ff (0x200) MX[B]
	[11] -1	0	0xda000000 - 0xda0003ff (0x400) MX[B]
	[12] -1	0	0xde800000 - 0xde8003ff (0x400) MX[B]
	[13] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[14] -1	0	0xdffe0000 - 0xdfffffff (0x20000) MX[B](B)
	[15] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[16] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[17] -1	0	0xdf000000 - 0xdf07ffff (0x80000) MX[B](B)
	[18] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[22] -1	0	0x0000e100 - 0x0000e13f (0x40) IX[B]
	[23] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[24] -1	0	0x00009400 - 0x0000940f (0x10) IX[B]
	[25] -1	0	0x00009800 - 0x00009800 (0x1) IX[B]
	[26] -1	0	0x0000a000 - 0x0000a000 (0x1) IX[B]
	[27] -1	0	0x0000a400 - 0x0000a400 (0x1) IX[B]
	[28] -1	0	0x0000a800 - 0x0000a800 (0x1) IX[B]
	[29] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[30] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[31] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xda800000 - 0xda8000ff (0x100) MX[B]
	[5] -1	0	0xdb000000 - 0xdb0000ff (0x100) MX[B]
	[6] -1	0	0xdb800000 - 0xdb800fff (0x1000) MX[B]
	[7] -1	0	0xdc000000 - 0xdc000fff (0x1000) MX[B]
	[8] -1	0	0xdc800000 - 0xdc800fff (0x1000) MX[B]
	[9] -1	0	0x40000200 - 0x400002ff (0x100) MX[B]
	[10] -1	0	0x40000000 - 0x400001ff (0x200) MX[B]
	[11] -1	0	0xda000000 - 0xda0003ff (0x400) MX[B]
	[12] -1	0	0xde800000 - 0xde8003ff (0x400) MX[B]
	[13] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[14] -1	0	0xdffe0000 - 0xdfffffff (0x20000) MX[B](B)
	[15] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[16] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[17] -1	0	0xdf000000 - 0xdf07ffff (0x80000) MX[B](B)
	[18] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[19] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[20] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[21] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[24] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[25] -1	0	0x0000e100 - 0x0000e13f (0x40) IX[B]
	[26] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[27] -1	0	0x00009400 - 0x0000940f (0x10) IX[B]
	[28] -1	0	0x00009800 - 0x00009800 (0x1) IX[B]
	[29] -1	0	0x0000a000 - 0x0000a000 (0x1) IX[B]
	[30] -1	0	0x0000a400 - 0x0000a400 (0x1) IX[B]
	[31] -1	0	0x0000a800 - 0x0000a800 (0x1) IX[B]
	[32] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[33] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[34] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[35] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[36] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce FX 5500 at PCI:1:10:0
(--) NVIDIA(0): VideoRAM: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 04.34.20.69.51
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce FX 5500 at PCI:1:10:0:
(--) NVIDIA(0):     Envision EFT9x0 Series (CRT-1)
(--) NVIDIA(0): Envision EFT9x0 Series (CRT-1): 350.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-1
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1600x1200"
(II) NVIDIA(0):     "1280x1024"
(II) NVIDIA(0):     "1280x960"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1600 x 1200
(--) NVIDIA(0): DPI set to (90, 96); computed from "UseEdidDpi" X config option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B]
	[1] 0	0	0xdd000000 - 0xddffffff (0x1000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xda800000 - 0xda8000ff (0x100) MX[B]
	[7] -1	0	0xdb000000 - 0xdb0000ff (0x100) MX[B]
	[8] -1	0	0xdb800000 - 0xdb800fff (0x1000) MX[B]
	[9] -1	0	0xdc000000 - 0xdc000fff (0x1000) MX[B]
	[10] -1	0	0xdc800000 - 0xdc800fff (0x1000) MX[B]
	[11] -1	0	0x40000200 - 0x400002ff (0x100) MX[B]
	[12] -1	0	0x40000000 - 0x400001ff (0x200) MX[B]
	[13] -1	0	0xda000000 - 0xda0003ff (0x400) MX[B]
	[14] -1	0	0xde800000 - 0xde8003ff (0x400) MX[B]
	[15] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[16] -1	0	0xdffe0000 - 0xdfffffff (0x20000) MX[B](B)
	[17] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[18] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[19] -1	0	0xdf000000 - 0xdf07ffff (0x80000) MX[B](B)
	[20] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[21] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[22] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[23] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[24] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[25] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[26] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[27] -1	0	0x0000e100 - 0x0000e13f (0x40) IX[B]
	[28] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[29] -1	0	0x00009400 - 0x0000940f (0x10) IX[B]
	[30] -1	0	0x00009800 - 0x00009800 (0x1) IX[B]
	[31] -1	0	0x0000a000 - 0x0000a000 (0x1) IX[B]
	[32] -1	0	0x0000a400 - 0x0000a400 (0x1) IX[B]
	[33] -1	0	0x0000a800 - 0x0000a800 (0x1) IX[B]
	[34] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[35] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[36] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[37] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[38] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "1600x1200"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
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
error opening security policy file /usr/lib/xserver/SecurityPolicy
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "XkbOptions" "lv3:ralt_switch"
(**) Generic Keyboard: XkbOptions: "lv3:ralt_switch"
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
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
    xkb_keycodes             { include "xfree86+aliases(qwerty)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };
    xkb_symbols              { include "pc(pc105)+us+level3(ralt_switch)" };
    xkb_geometry             { include "pc(pc105)" };
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
SetClientVersion: 0 9
SetClientVersion: 0 9
SetClientVersion: 0 9
SetClientVersion: 0 9

```

---

### Post by tonyr on 2006-10-29
I don't know what the disconnect is between xorg.conf and what you are
actually getting.  Here's what I see:
```
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8774
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
```
Module **glx** actually loads the **nvidia** driver.  There must
be some smarts in there somewhere to know how to do that.  This is
confirmed later on:
```
(II) NVIDIA X Driver  1.0-8774  Tue Aug  1 20:56:50 PDT 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:0a:0
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
```
Once the process knows what the graphics controller/driver setup is, it
knows how to figure out the resolution capabilities of the controller,
and chooses one (a default?):
```
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce FX 5500 at PCI:1:10:0
(--) NVIDIA(0): VideoRAM: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 04.34.20.69.51
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce FX 5500 at PCI:1:10:0:
(--) NVIDIA(0):     Envision EFT9x0 Series (CRT-1)
(--) NVIDIA(0): Envision EFT9x0 Series (CRT-1): 350.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-1
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1600x1200"
(II) NVIDIA(0):     "1280x1024"
(II) NVIDIA(0):     "1280x960"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1600 x 1200
(--) NVIDIA(0): DPI set to (90, 96); computed from "UseEdidDpi" X config option
(--) Depth 24 pixmap format is 32 bpp
(skip some...)
(II) NVIDIA(0): Setting mode "1600x1200"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
```

So all I can say is that it appears that the startup process is smarter
than xorg.conf.

---

### Post by DigitalDuality on 2006-11-05
well i've gone ahead and corrected every value for my xorg.conf

and now the startup and bootup process doesn't show anything to me at all.  just black screens until i get to a terminal login prompt.  from there i can startx but that's it.

---

