---
title: "Cannot get fglrx to work (properly) on Intrepid"
date: 2008-12-08
forum: Installation &amp; Upgrades
---

### Post by ibro-x on 2008-12-08
Hi,
I upgraded from Hardy to Intrepid using the "cdromupgrade" script on the alternate installer CD.
Everything is fine until I tried to install fglrx-8.552.
The installation and module compilation itself is OK.

The problem is .... hmm .... actually, I don't know what it is .. but it seems that X cannot recognize the correct monitor resolution.
I've tried many things until I can't remember what I've tried with no result, it keeps saying that it cannot determine my graphics and/or monitor resolution and asking if I want to use the lowest resolution or repair it.

The fglrx-8.4 worked well on Hardy.

The "radeon" driver works but can't give me maximum (widescreen) resolution and I'm stuck with the "radeon" driver and this unproportional resolution.

So far I've been searching around the forum and the net with no working result.


My platform:
AMD x64
MSI RS482 onboard Radeon X200
RAM 1,5GB
Samsung LCD TV LA19R7


Here are my log and config:

```

/etc/X11/xorg.conf:
===================

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:5:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes	"1440x900" "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

```


```

/var/log/Xorg.0.log:
====================

X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-16-server x86_64 Ubuntu
Current Operating System: Linux ibro-x82 2.6.27-9-generic #1 SMP Thu Nov 20 22:15:32 UTC 2008 x86_64
Build Date: 24 October 2008  09:06:49AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@crested.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Dec  8 21:17:42 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "aticonfig Layout"
(**) |-->Screen "aticonfig-Screen[0]-0" (0)
(**) |   |-->Monitor "aticonfig-Monitor[0]-0"
(**) |   |-->Device "aticonfig-Device[0]-0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x7b7320
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 4.1
	X.Org XInput driver : 2.1
	X.Org Server Extension : 1.1
	X.Org Font Renderer : 0.6
(II) Loader running on linux
(++) using VT number 8

(--) PCI:*(0@1:5:0) ATI Technologies Inc RS482 [Radeon Xpress 200] rev 0, Mem @ 0xd0000000/268435456, 0xfeaf0000/65536, I/O @ 0x0000d800/256, BIOS @ 0x????????/131072
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[24] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[25] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[26] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[27] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[28] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[29] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded by default.
(II) "freetype" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) LoadModule: "extmod"

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
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
(II) LoadModule: "dbe"

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.4.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(==) AIGLX disabled
(WW) fglrx: Force AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.5.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "record"

(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension RECORD
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.4.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) LoadModule: "fglrx"

(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 1.4.99.906, module version = 8.55.2
	Module class: X.Org Video Driver
(II) Primary Device is: PCI 01@00:05:0
(WW) Falling back to old probe method for fglrx
(II) ATI Proprietary Linux Driver Version Identifier:8.55.2
(II) ATI Proprietary Linux Driver Release Identifier: UNSUPPORTED-8.552                    
(II) ATI Proprietary Linux Driver Build Date: Oct 28 2008 21:23:41
(WW) This ATI Proprietary Linux Driver does not guarantee support of video driver ABI higher than 2.0
(WW) Video driver ABI version of the X server is 4.1
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:0:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:1:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:17:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:1) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:2) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:1) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:2) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:3) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:4) found
(--) Chipset Supported AMD Graphics Processor (0x5974) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:0:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:1:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:17:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:1) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:2) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:1) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:2) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:3) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:4) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[24] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[25] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[26] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[27] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[28] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[29] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) fglrx(0): pEnt->device->identifier=0x245a470
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[20] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[21] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[22] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[23] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[24] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[25] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[26] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[27] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[28] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[29] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[30] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[31] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[32] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[33] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[34] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"

(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 4.1
(II) fglrx(0): PCI bus 1 card 5 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "DPMS" "true"
(II) fglrx(0): Loading PCS database from /etc/ati/amdpcsdb
(II) fglrx(0): 10BitPixelFormat disabled by default
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(**) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(--) fglrx(0): Chipset: "ATI Radeon Xpress Series" (Chipset = 0x5974)
(--) fglrx(0): (PciSubVendor = 0x1462, PciSubDevice = 0x7141)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
(--) fglrx(0): MMIO registers at 0xfeaf0000
(--) fglrx(0): I/O port at 0x0000d800
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 4.1
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"

(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.1.0
	ABI class: X.Org Video Driver, version 4.1
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 2.0
(II) fglrx(0): VESA VBE Total Mem: 262144 kB
(II) fglrx(0): VESA VBE OEM: ATI RADEON XPRESS 200 Series
(II) fglrx(0): VESA VBE OEM Software Rev: 1.0
(II) fglrx(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) fglrx(0): VESA VBE OEM Product: RS48
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: Searching for BusID PCI:1:5:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: drmOpenMinor returns 10
drmOpenByBusid: drmGetBusid reports PCI:1:5:0
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"

(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 1.4.99.906, module version = 8.55.2
	ABI class: X.Org Server Extension, version 1.1
(II) fglrx(0): Using adapter: 1:5.0.
(II) fglrx(0): [FB] MC range(MCFBBase = 0x50000000, MCFBSize = 0x10000000)
(--) fglrx(0): Video RAM: 262144 kByte, Type: DDR SGRAM / SDRAM
(II) fglrx(0): PCIE card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) fglrx(0): ***Display: ConnectedDisplayTypes=0x00000001, disabled=0x00000000
(II) fglrx(0): Connected Display1: CRT on primary DAC [crt1]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: SAM  Model: 256  Serial#: 0
(II) fglrx(0): Year: 2006  Week: 19
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) fglrx(0): Sync:  Separate  Composite
(II) fglrx(0): Max Image Size [cm]: horiz.: 41  vert.: 26
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: Off; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.640 redY: 0.329   greenX: 0.300 greenY: 0.600
(II) fglrx(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 720x400@70Hz
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@67Hz
(II) fglrx(0): 640x480@72Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@56Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@72Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 832x624@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@70Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): 1152x870@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) fglrx(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) fglrx(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 106.5 MHz   Image Size:  408 x 225 mm
(II) fglrx(0): h_active: 1440  h_sync: 1520  h_sync_end 1672 h_blank_end 1904 h_border: 0
(II) fglrx(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 934 v_border: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 108.0 MHz   Image Size:  408 x 225 mm
(II) fglrx(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) fglrx(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) fglrx(0): Stereo: left channel on sync
side-by-side interleaved(II) fglrx(0): Monitor name: SAMSUNG LCD
(II) fglrx(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 81 kHz, PixClock max 140 MHz
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff004c2d560200000000
(II) fglrx(0): 	131001036c291a782ade95a3544c9926
(II) fglrx(0): 	0f5054bfef80950081808140714f0101
(II) fglrx(0): 	0101010101019a29a0d0518422305098
(II) fglrx(0): 	360098e11000001c302a009851002a40
(II) fglrx(0): 	3070130098e11000003e000000fc0053
(II) fglrx(0): 	414d53554e47204c43440a20000000fd
(II) fglrx(0): 	00384b1e510e000a2020202020200006
(II) fglrx(0): End of Display1 EDID data --------------------
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
(II) fglrx(0): Primary Controller - CRT on primary DAC
(II) fglrx(0): Internal Desktop Setting: 0x00000001
(II) fglrx(0): POWERplay version 3.  1 power state available:
(II) fglrx(0):   1. 301/300MHz @ 50Hz [enable load balancing]
(==) fglrx(0): QBS disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(**) fglrx(0): Center Mode is enabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 38 modes found for primary display.
(--) fglrx(0): Virtual size is 1440x900 (pitch 0)
(**) fglrx(0): *Mode "1440x900": 106.5 MHz (scaled from 0.0 MHz), 55.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 +hsync (55.9 kHz)
(**) fglrx(0): *Mode "1280x768": 79.5 MHz (scaled from 0.0 MHz), 47.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 +hsync (47.8 kHz)
(**) fglrx(0): *Mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 (80.0 kHz)
(**) fglrx(0):  Default mode "1280x1024": 128.9 MHz (scaled from 0.0 MHz), 74.6 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1280x1024"x70.0  128.94  1280 1368 1504 1728  1024 1025 1028 1066 +hsync (74.6 kHz)
(**) fglrx(0):  Default mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 (64.0 kHz)
(**) fglrx(0): *Mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 (60.0 kHz)
(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"x72.0   78.43  1024 1080 1192 1360  768 769 772 801 +hsync (57.7 kHz)
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"x70.0   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync (56.5 kHz)
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync (48.4 kHz)
(**) fglrx(0): *Mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 (46.9 kHz)
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"x72.0   50.00  800 856 976 1040  600 637 643 666 (48.1 kHz)
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 +hsync (43.8 kHz)
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 (37.9 kHz)
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 (35.2 kHz)
(**) fglrx(0): *Mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 +hsync +vsync (37.5 kHz)
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"x72.0   31.50  640 664 704 832  480 489 492 520 +hsync +vsync (37.9 kHz)
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 +hsync +vsync (31.5 kHz)
(**) fglrx(0):  Default mode "1280x720": 74.5 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 +hsync (44.8 kHz)
(**) fglrx(0):  Default mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 (67.5 kHz)
(**) fglrx(0):  Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1152x864"x70.0   96.76  1152 1224 1344 1536  864 865 868 900 +hsync (63.0 kHz)
(**) fglrx(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 +hsync (53.7 kHz)
(**) fglrx(0):  Default mode "1024x480": 38.2 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x480"x60.0   38.16  1024 1048 1152 1280  480 481 484 497 +hsync (29.8 kHz)
(**) fglrx(0):  Default mode "960x720": 55.9 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "960x720"x60.0   55.85  960 1008 1104 1248  720 721 724 746 +hsync (44.8 kHz)
(**) fglrx(0):  Default mode "864x648": 45.1 MHz (scaled from 0.0 MHz), 40.2 kHz, 60.0 Hz
(II) fglrx(0): Modeline "864x648"x60.0   45.08  864 904 992 1120  648 649 652 671 +hsync (40.2 kHz)
(**) fglrx(0):  Default mode "856x480": 31.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "856x480"x60.0   31.73  856 872 960 1064  480 481 484 497 +hsync (29.8 kHz)
(**) fglrx(0):  Default mode "848x480": 31.5 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "848x480"x60.0   31.48  848 864 952 1056  480 481 484 497 +hsync (29.8 kHz)
(**) fglrx(0):  Default mode "720x576": 32.7 MHz (scaled from 0.0 MHz), 35.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x576"x60.0   32.66  720 744 816 912  576 577 580 597 +hsync (35.8 kHz)
(**) fglrx(0):  Default mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 +hsync (29.8 kHz)
(**) fglrx(0):  Default mode "704x480": 26.2 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "704x480"x60.0   26.24  704 720 792 880  480 481 484 497 +hsync (29.8 kHz)
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"x75.0   28.07  640 696 736 832  400 413 415 449 (33.7 kHz)
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"x60.0   24.92  640 664 760 792  400 460 462 525 (31.5 kHz)
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"x60.0   19.81  512 544 624 664  384 451 453 497 (29.8 kHz)
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"x75.0   24.75  400 408 448 528  300 601 602 625 doublescan (46.9 kHz)
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"x60.0   22.33  400 416 480 496  300 601 605 742 doublescan (45.0 kHz)
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"x75.0   15.75  320 328 360 416  240 481 482 501 doublescan (37.9 kHz)
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"x60.0   12.59  320 328 376 400  240 491 493 525 doublescan (31.5 kHz)
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"x75.0   13.10  320 352 368 416  200 406 407 417 doublescan (31.5 kHz)
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"x60.0   12.59  320 336 384 400  200 457 459 524 doublescan (31.5 kHz)
(--) fglrx(0): Display dimensions: (410, 260) mm
(--) fglrx(0): DPI set to (89, 87)
(--) fglrx(0): Virtual size is 1440x900 (pitch 1472)
(**) fglrx(0): *Mode "1440x900": 106.5 MHz (scaled from 0.0 MHz), 55.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 +hsync (55.9 kHz)
(**) fglrx(0): *Mode "1280x768": 79.5 MHz (scaled from 0.0 MHz), 47.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 +hsync (47.8 kHz)
(**) fglrx(0): *Mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 (80.0 kHz)
(**) fglrx(0):  Default mode "1280x1024": 128.9 MHz (scaled from 0.0 MHz), 74.6 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1280x1024"x70.0  128.94  1280 1368 1504 1728  1024 1025 1028 1066 +hsync (74.6 kHz)
(**) fglrx(0):  Default mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 (64.0 kHz)
(**) fglrx(0): *Mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 (60.0 kHz)
(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"x72.0   78.43  1024 1080 1192 1360  768 769 772 801 +hsync (57.7 kHz)
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"x70.0   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync (56.5 kHz)
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync (48.4 kHz)
(**) fglrx(0): *Mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 (46.9 kHz)
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"x72.0   50.00  800 856 976 1040  600 637 643 666 (48.1 kHz)
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 +hsync (43.8 kHz)
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 (37.9 kHz)
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 (35.2 kHz)
(**) fglrx(0): *Mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 +hsync +vsync (37.5 kHz)
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"x72.0   31.50  640 664 704 832  480 489 492 520 +hsync +vsync (37.9 kHz)
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 +hsync +vsync (31.5 kHz)
(**) fglrx(0):  Default mode "1280x720": 74.5 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 +hsync (44.8 kHz)
(**) fglrx(0):  Default mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 (67.5 kHz)
(**) fglrx(0):  Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1152x864"x70.0   96.76  1152 1224 1344 1536  864 865 868 900 +hsync (63.0 kHz)
(**) fglrx(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 +hsync (53.7 kHz)
(**) fglrx(0):  Default mode "1024x480": 38.2 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x480"x60.0   38.16  1024 1048 1152 1280  480 481 484 497 +hsync (29.8 kHz)
(**) fglrx(0):  Default mode "960x720": 55.9 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "960x720"x60.0   55.85  960 1008 1104 1248  720 721 724 746 +hsync (44.8 kHz)
(**) fglrx(0):  Default mode "864x648": 45.1 MHz (scaled from 0.0 MHz), 40.2 kHz, 60.0 Hz
(II) fglrx(0): Modeline "864x648"x60.0   45.08  864 904 992 1120  648 649 652 671 +hsync (40.2 kHz)
(**) fglrx(0):  Default mode "856x480": 31.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "856x480"x60.0   31.73  856 872 960 1064  480 481 484 497 +hsync (29.8 kHz)
(**) fglrx(0):  Default mode "848x480": 31.5 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "848x480"x60.0   31.48  848 864 952 1056  480 481 484 497 +hsync (29.8 kHz)
(**) fglrx(0):  Default mode "720x576": 32.7 MHz (scaled from 0.0 MHz), 35.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x576"x60.0   32.66  720 744 816 912  576 577 580 597 +hsync (35.8 kHz)
(**) fglrx(0):  Default mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 +hsync (29.8 kHz)
(**) fglrx(0):  Default mode "704x480": 26.2 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "704x480"x60.0   26.24  704 720 792 880  480 481 484 497 +hsync (29.8 kHz)
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"x75.0   28.07  640 696 736 832  400 413 415 449 (33.7 kHz)
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"x60.0   24.92  640 664 760 792  400 460 462 525 (31.5 kHz)
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"x60.0   19.81  512 544 624 664  384 451 453 497 (29.8 kHz)
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"x75.0   24.75  400 408 448 528  300 601 602 625 doublescan (46.9 kHz)
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"x60.0   22.33  400 416 480 496  300 601 605 742 doublescan (45.0 kHz)
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"x75.0   15.75  320 328 360 416  240 481 482 501 doublescan (37.9 kHz)
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"x60.0   12.59  320 328 376 400  240 491 493 525 doublescan (31.5 kHz)
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"x75.0   13.10  320 352 368 416  200 406 407 417 doublescan (31.5 kHz)
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"x60.0   12.59  320 336 384 400  200 457 459 524 doublescan (31.5 kHz)
(II) Loading sub module "fb"
(II) LoadModule: "fb"

(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"

(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.2.0
	ABI class: X.Org Video Driver, version 4.1
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"

(II) Reloading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x4000001f
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): ATI GART size: 255 MB
(II) fglrx(0): [pcie] 261120 kB allocated
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(II) fglrx(0): Direct rendering enabled
(II) fglrx(0): AC Adapter is used
(II) fglrx(0): Interrupt handler installed at IRQ 17.
(II) fglrx(0): Exposed events to the /proc interface
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[20] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[21] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[22] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[23] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[24] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[25] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[26] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[27] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[28] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[29] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[30] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[31] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[32] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[33] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[34] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) fglrx(0): driver needs X.org 1.4.x.y with x.y >= 99.906
(II) fglrx(0): detected X.org 7.4.2.0
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
(II) fglrx(0): DRIScreenInit for fglrx driver
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: Searching for BusID PCI:1:5:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: drmOpenMinor returns 11
drmOpenByBusid: drmGetBusid reports PCI:1:5:0
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:5:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0x20000
(II) fglrx(0): [drm] mapped SAREA 0x20000 to 0x7fa390e52000
(II) fglrx(0): [drm] framebuffer handle = 0x21000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.55.2
(II) fglrx(0):     Date: Oct 28 2008
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.27-9-generic
(II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
(II) fglrx(0):     Build-Kernel __SMP__:            yes
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0x00022000
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0x50000000 FBMappedSize: 0x00719000
(II) fglrx(0): FBMM initialized for area (0,0)-(1472,1264)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1472,900) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1472 x 364

Backtrace:

```

---

### Post by craigsn on 2008-12-22
I have a similar problem, but on a new install of Intrepid:

I have used Envy in the past (Hardy install), and it worked fine. But now I have tried all of the methods I could find, EnvyNG, the Restricted drivers in the repository and the Catalyst driver directly from ATI, not of them work. And I don't know for what reasons, all of them seem different.

I have a fresh install of 64bit Intrepid my HP a1250n, AMD X2 with 2gb ram, dual booted with Win Vista, but Vista is on a separate hard disk. 

The first thing I did, was try the restricted driver as Intrepid said there was one for my computer. When I rebooted, the logon screen was a mess, could not see anything. So I did a CTL ALT f1 to login to the console and did an apt-get install envyng-core. That installed fine, but after running envyng -t and rebooting, the same thing happened on the logon screen. So I again did the CTL ALT f1 and did the envyng --uninstall-all and rebooted. This time there was a dialog saying that there was "some" problem  with the driver and that the system would boot in low-graphics mode. And there were some options to continue in low-graphics mode, one for configure and something else. I tried each one of them, but still nothing good happened. After that, I went to the ubuntu forums and say that ATI has catalyst drivers out for this card, so I tried to install those using the method they say in their document. Again, no joy. 

So it is obvious I am missing something, but not sure what it is. Envy worked for me in Hardy, but not now. The other methods are new to Intrepid (as far as I know), and they don't work either. Any help here?

---

### Post by maclenin on 2008-12-22
Though this ([_post_]("http://ubuntuforums.org/showthread.php?t=478238")) helped me solve the problem I was having with my radeon x2300 - in Feisty...

> I had excact the same problem when I just changed my laptop to HP 6910p
but I just solved this probelem.

steps below:

sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install linux-restricted-modules-$(uname -r)
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
sudo /etc/init.d/gdm restart

(This solution was form [http://terenzioberni.blogspot.com/20...53jr-f3jr.html](http://terenzioberni.blogspot.com/20...53jr-f3jr.html))


-ckh

...it may still be worth a try - good luck!

---

