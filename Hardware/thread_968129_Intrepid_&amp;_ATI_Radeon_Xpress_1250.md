---
title: "Intrepid &amp; ATI Radeon Xpress 1250"
date: 2008-11-02
forum: Hardware
---

### Post by NickEvans on 2008-11-02
Hi,
It seems the fglrx driver is broken under Intrepid.
When I run glxinfo:
```

name of display: :0.0
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  158 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  10
  Current serial number in output stream:  10

```

My Xorg.0.log:
```


X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux malika 2.6.27-7-generic #1 SMP Thu Oct 30 04:18:38 UTC 2008 i686
Build Date: 24 October 2008  08:00:16AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Nov  2 14:06:28 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "aticonfig Layout"
(**) |-->Screen "aticonfig-Screen[0]-0" (0)
(**) |   |-->Monitor "aticonfig-Monitor[0]-0"
(**) |   |-->Device "aticonfig-Device[0]-0"
(**) |-->Input Device "Synaptics Touchpad"
(**) Option "AIGLX" "on"
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
(**) Extension "Composite" is enabled
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81d9a40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 4.1
	X.Org XInput driver : 2.1
	X.Org Server Extension : 1.1
	X.Org Font Renderer : 0.6
(II) Loader running on linux
(++) using VT number 9

(--) PCI:*(0@1:5:0) ATI Technologies Inc Radeon Xpress 1250 rev 0, Mem @ 0xe0000000/0, 0xdfef0000/0, I/O @ 0x00009000/0
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded. This was enabled by default and also specified in the config file.
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.4.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(**) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.4.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
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
(II) LoadModule: "fglrx"

(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 1.4.99.906, module version = 8.54.3
	Module class: X.Org Video Driver
(II) LoadModule: "synaptics"

(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 0.15.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(II) Primary Device is: PCI 01@00:05:0
(WW) Falling back to old probe method for fglrx
(II) ATI Proprietary Linux Driver Version Identifier:8.54.3
(II) ATI Proprietary Linux Driver Release Identifier: UNSUPPORTED-8.543.2                  
(II) ATI Proprietary Linux Driver Build Date: Oct 10 2008 21:37:39
(WW) This ATI Proprietary Linux Driver does not guarantee support of video driver ABI higher than 2.0
(WW) Video driver ABI version of the X server is 4.1
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:0:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:1:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:4:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:6:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:7:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:1) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:2) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:3) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:4) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:5) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:1) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:2) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:3) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:4) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:5:2) found
(--) Chipset Supported AMD Graphics Processor (0x7942) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:0:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:1:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:4:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:6:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:7:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:1) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:2) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:3) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:4) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:5) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:1) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:2) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:3) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:4) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:5:2) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) fglrx(0): pEnt->device->identifier=0x90a96f0
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
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
(II) fglrx(0): PCS database file /etc/ati/amdpcsdb not found
(II) fglrx(0):   Creating PCS database from initial defaults instead
(II) fglrx(0): 10BitPixelFormat disabled by default
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(--) fglrx(0): Chipset: "ATI Radeon Xpress 1200 Series" (Chipset = 0x7942)
(--) fglrx(0): (PciSubVendor = 0x1854, PciSubDevice = 0x011b)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xe0000000
(--) fglrx(0): MMIO registers at 0xdfef0000
(--) fglrx(0): I/O port at 0x00009000
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
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 10.19
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: RS600
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID PCI:1:5:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -6
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -6
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -6
drmOpenDevice: node name is /dev/dri/card3
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -6
drmOpenDevice: node name is /dev/dri/card4
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -6
drmOpenDevice: node name is /dev/dri/card5
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -6
drmOpenDevice: node name is /dev/dri/card6
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -6
drmOpenDevice: node name is /dev/dri/card7
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -6
drmOpenDevice: node name is /dev/dri/card8
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -6
drmOpenDevice: node name is /dev/dri/card9
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -6
drmOpenDevice: node name is /dev/dri/card10
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -6
drmOpenDevice: node name is /dev/dri/card11
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -6
drmOpenDevice: node name is /dev/dri/card12
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -6
drmOpenDevice: node name is /dev/dri/card13
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -6
drmOpenDevice: node name is /dev/dri/card14
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -6
(WW) fglrx(0): Failed to open DRM connection
(II) fglrx(0): [FB] Find the MC FB aperturs range(MCFBBase = 0xcc000000, MCFBSize = 0x10000000)
(--) fglrx(0): Video RAM: 262144 kByte, Type: DDR2
(II) fglrx(0): PCIE card detected
(--) fglrx(0): Using per-process page tables (PPPT) as GART.
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) fglrx(0): ***Display: ConnectedDisplayTypes=0x00000002, disabled=0x00000000
(II) fglrx(0): Connected Display1: LCD on internal LVDS [lvds]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: LEN  Model: 4031  Serial#: 0
(II) fglrx(0): Year: 2007  Week: 0
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max Image Size [cm]: horiz.: 29  vert.: 18
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): No DPMS capabilities specified
(II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.590 redY: 0.346   greenX: 0.327 greenY: 0.546
(II) fglrx(0): blueX: 0.160 blueY: 0.147   whiteX: 0.312 whiteY: 0.328
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 71.0 MHz   Image Size:  286 x 179 mm
(II) fglrx(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) fglrx(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 823 v_border: 0
(WW) fglrx(0): Unknown vendor-specific block 0
(WW) fglrx(0): Unknown vendor-specific block f
(II) fglrx(0):  LP133WX1-TLC1
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff0030ae314000000000
(II) fglrx(0): 	00110103801d12780a2f309758538b29
(II) fglrx(0): 	25505400000001010101010101010101
(II) fglrx(0): 	010101010101bc1b00a0502017303020
(II) fglrx(0): 	36001eb3100000180000000000000000
(II) fglrx(0): 	000000000000000000000000000f0081
(II) fglrx(0): 	0a32810a28190100320c00f5000000fe
(II) fglrx(0): 	004c503133335758312d544c43310078
(II) fglrx(0): End of Display1 EDID data --------------------
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
(II) fglrx(0): Primary Controller - LCD on internal LVDS
(II) fglrx(0): Internal Desktop Setting: 0x00000001
(II) fglrx(0): POWERplay not supported on this hardware
(==) fglrx(0): Qbs is not supported in this release. Disabled.
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 12 modes found for primary display.
(--) fglrx(0): Virtual size is 1280x800 (pitch 0)
(**) fglrx(0): *Mode "1280x800": 71.0 MHz (scaled from 0.0 MHz), 49.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x800"x60.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync +vsync (49.3 kHz)
(**) fglrx(0): *Mode "1280x768": 71.0 MHz (scaled from 0.0 MHz), 49.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x768"x60.0   71.00  1280 1328 1360 1440  768 803 809 823 +hsync +vsync (49.3 kHz)
(**) fglrx(0): *Mode "1280x720": 71.0 MHz (scaled from 0.0 MHz), 49.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"x60.0   71.00  1280 1328 1360 1440  720 803 809 823 +hsync +vsync (49.3 kHz)
(**) fglrx(0): *Mode "1024x768": 71.0 MHz (scaled from 0.0 MHz), 49.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"x60.0   71.00  1024 1328 1360 1440  768 803 809 823 +hsync +vsync (49.3 kHz)
(**) fglrx(0): *Mode "800x600": 71.0 MHz (scaled from 0.0 MHz), 49.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"x60.0   71.00  800 1328 1360 1440  600 803 809 823 +hsync +vsync (49.3 kHz)
(**) fglrx(0): *Mode "720x480": 71.0 MHz (scaled from 0.0 MHz), 49.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"x60.0   71.00  720 1328 1360 1440  480 803 809 823 +hsync +vsync (49.3 kHz)
(**) fglrx(0): *Mode "640x480": 71.0 MHz (scaled from 0.0 MHz), 49.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"x60.0   71.00  640 1328 1360 1440  480 803 809 823 +hsync +vsync (49.3 kHz)
(**) fglrx(0):  Default mode "640x400": 71.0 MHz (scaled from 0.0 MHz), 49.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"x60.0   71.00  640 1328 1360 1440  400 803 809 823 +hsync +vsync (49.3 kHz)
(**) fglrx(0):  Default mode "512x384": 71.0 MHz (scaled from 0.0 MHz), 49.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"x60.0   71.00  512 1328 1360 1440  384 803 809 823 +hsync +vsync (49.3 kHz)
(**) fglrx(0):  Default mode "400x300": 71.0 MHz (scaled from 0.0 MHz), 49.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "400x300"x60.0   71.00  400 1328 1360 1440  300 803 809 823 +hsync +vsync (49.3 kHz)
(**) fglrx(0):  Default mode "320x240": 71.0 MHz (scaled from 0.0 MHz), 49.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x240"x60.0   71.00  320 1328 1360 1440  240 803 809 823 +hsync +vsync (49.3 kHz)
(**) fglrx(0):  Default mode "320x200": 71.0 MHz (scaled from 0.0 MHz), 49.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x200"x60.0   71.00  320 1328 1360 1440  200 803 809 823 +hsync +vsync (49.3 kHz)
(--) fglrx(0): Display dimensions: (290, 180) mm
(--) fglrx(0): DPI set to (112, 112)
(--) fglrx(0): Virtual size is 1280x800 (pitch 1280)
(**) fglrx(0): *Mode "1280x800": 71.0 MHz (scaled from 0.0 MHz), 49.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x800"x60.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync +vsync (49.3 kHz)
(**) fglrx(0): *Mode "1280x768": 71.0 MHz (scaled from 0.0 MHz), 49.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x768"x60.0   71.00  1280 1328 1360 1440  768 803 809 823 +hsync +vsync (49.3 kHz)
(**) fglrx(0): *Mode "1280x720": 71.0 MHz (scaled from 0.0 MHz), 49.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"x60.0   71.00  1280 1328 1360 1440  720 803 809 823 +hsync +vsync (49.3 kHz)
(**) fglrx(0): *Mode "1024x768": 71.0 MHz (scaled from 0.0 MHz), 49.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"x60.0   71.00  1024 1328 1360 1440  768 803 809 823 +hsync +vsync (49.3 kHz)
(**) fglrx(0): *Mode "800x600": 71.0 MHz (scaled from 0.0 MHz), 49.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"x60.0   71.00  800 1328 1360 1440  600 803 809 823 +hsync +vsync (49.3 kHz)
(**) fglrx(0): *Mode "720x480": 71.0 MHz (scaled from 0.0 MHz), 49.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"x60.0   71.00  720 1328 1360 1440  480 803 809 823 +hsync +vsync (49.3 kHz)
(**) fglrx(0): *Mode "640x480": 71.0 MHz (scaled from 0.0 MHz), 49.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"x60.0   71.00  640 1328 1360 1440  480 803 809 823 +hsync +vsync (49.3 kHz)
(**) fglrx(0):  Default mode "640x400": 71.0 MHz (scaled from 0.0 MHz), 49.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"x60.0   71.00  640 1328 1360 1440  400 803 809 823 +hsync +vsync (49.3 kHz)
(**) fglrx(0):  Default mode "512x384": 71.0 MHz (scaled from 0.0 MHz), 49.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"x60.0   71.00  512 1328 1360 1440  384 803 809 823 +hsync +vsync (49.3 kHz)
(**) fglrx(0):  Default mode "400x300": 71.0 MHz (scaled from 0.0 MHz), 49.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "400x300"x60.0   71.00  400 1328 1360 1440  300 803 809 823 +hsync +vsync (49.3 kHz)
(**) fglrx(0):  Default mode "320x240": 71.0 MHz (scaled from 0.0 MHz), 49.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x240"x60.0   71.00  320 1328 1360 1440  240 803 809 823 +hsync +vsync (49.3 kHz)
(**) fglrx(0):  Default mode "320x200": 71.0 MHz (scaled from 0.0 MHz), 49.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x200"x60.0   71.00  320 1328 1360 1440  200 803 809 823 +hsync +vsync (49.3 kHz)
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

(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 1.4.99.906, module version = 8.54.3
	ABI class: X.Org Server Extension, version 1.1
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x8000001d
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): ATI GART size: 255 MB
(WW) fglrx(0): No DRM connection for driver fglrx.
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(II) fglrx(0): Direct rendering disabled
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) fglrx(0): driver needs X.org 1.4.x.y with x.y >= 99.906
(II) fglrx(0): detected X.org 7.4.2.0
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xcc000000 FBMappedSize: 0x10000000
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,800) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1280 x 7391
(==) fglrx(0): Backing store disabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(**) fglrx(0): DPMS enabled
(WW) fglrx(0): Textured Video not supported without DRI enabled.
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	Solid Horizontal and Vertical Lines
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) fglrx(0): Acceleration enabled
(II) LoadModule: "amdxmm"

(II) Loading /usr/lib/xorg/modules//amdxmm.so
(II) Module amdxmm: vendor="X.Org Foundation"
	compiled for 1.4.99.906, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(EE) fglrx(0): XMM failed to open CMMQS connection.
(II) fglrx(0): XMM failed to initialize!
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using hardware cursor
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) AIGLX: Screen 0 is not DRI capable
(II) Synaptics touchpad driver version 0.15.2
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event9
(II) Synaptics Touchpad: x-axis range 1472 - 5472
(II) Synaptics Touchpad: y-axis range 1408 - 4448
(**) Option "Device" "/dev/input/event9"
(--) Synaptics Touchpad touchpad found
(**) Synaptics Touchpad: always reports core events
(II) evaluating device (Synaptics Touchpad)
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: TOUCHPAD)
(II) Synaptics Touchpad: x-axis range 1472 - 5472
(II) Synaptics Touchpad: y-axis range 1408 - 4448
(--) Synaptics Touchpad touchpad found
(II) config/hal: Adding input device Macintosh mouse button emulation
(II) LoadModule: "evdev"

(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 2.0.99
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Configuring as mouse
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device SynPS/2 Synaptics TouchPad
(II) Synaptics touchpad driver version 0.15.2
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(**) Option "Device" "/dev/input/event9"
(--) SynPS/2 Synaptics TouchPad touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(WW) SynPS/2 Synaptics TouchPad can't grab event device, errno=16
(--) SynPS/2 Synaptics TouchPad touchpad found
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event1"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) AT Translated Set 2 keyboard: xkb_layout: "us"
(**) Option "xkb_variant" "dvorak"
(**) AT Translated Set 2 keyboard: xkb_variant: "dvorak"
(**) Option "xkb_options" "lv3:ralt_switch"
(**) AT Translated Set 2 keyboard: xkb_options: "lv3:ralt_switch"
(II) config/hal: Adding input device Video Bus
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event6"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Video Bus: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Video Bus: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Video Bus: xkb_layout: "us"
(**) Option "xkb_variant" "dvorak"
(**) Video Bus: xkb_variant: "dvorak"
(**) Option "xkb_options" "lv3:ralt_switch"
(**) Video Bus: xkb_options: "lv3:ralt_switch"
AUDIT: Sun Nov  2 14:06:35 2008: 28821 X: client 5 rejected from local host ( uid=0 gid=0 pid=28992 )
AUDIT: Sun Nov  2 14:06:38 2008: 28821 X: client 5 rejected from local host ( uid=1000 gid=1000 pid=29000 )
AUDIT: Sun Nov  2 14:06:38 2008: 28821 X: client 5 rejected from local host ( uid=1000 gid=1000 pid=29001 )
AUDIT: Sun Nov  2 14:06:38 2008: 28821 X: client 5 rejected from local host ( uid=1000 gid=1000 pid=29002 )

```

My xorg.conf:
```

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
	InputDevice    "Synaptics Touchpad"
	Option	    "SendCoreEvents" "True"
	Option	    "Protocol" "auto-dev"
	Option	    "SHMConfig" "True"
	Option	    "VertTwoFingerScroll" "True"
	Option	    "Device" "/dev/psaux"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
	Load  "dri"
EndSection

Section "ServerFlags"
	Option	    "AIGLX" "on"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:5:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Extensions"
	Option	    "Composite" "Enable"
EndSection

```

EDIT> I heard it works with the beta Catalist 8.11 driver. I would be fine with this, but I can't find this driver. Can anyone tell me how to find it?

---

### Post by Dauthi4 on 2008-11-02
Hi,

I had kind of the same problem with my Xpress 200M and I've just found the solution !

The thing was that my Grub list was outdated so I wasn't booting on the last kernel and so fglrx wasn't installing properly...

Can you remove completely fglrx and all its components (with --purge)

And then past the results of 

```
sudo apt-get install xorg-driver-fglrx
```

And that way will see if it's installing correctly :)

---

### Post by NickEvans on 2008-11-02
After running 'sudo apt-get install xorg-driver-fglrx':

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  kdesudo nvidia-kernel-common python-kde4
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  fglrx-amdcccle fglrx-kernel-source
Suggested packages:
  libamdxvba1
The following NEW packages will be installed:
  fglrx-amdcccle fglrx-kernel-source xorg-driver-fglrx
0 upgraded, 3 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/20.0MB of archives.
After this operation, 55.2MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package fglrx-kernel-source.
(Reading database ... 305736 files and directories currently installed.)
Unpacking fglrx-kernel-source (from .../fglrx-kernel-source_2%3a8.543-0ubuntu4_i386.deb) ...
Selecting previously deselected package xorg-driver-fglrx.
Unpacking xorg-driver-fglrx (from .../xorg-driver-fglrx_2%3a8.543-0ubuntu4_i386.deb) ...
Selecting previously deselected package fglrx-amdcccle.
Unpacking fglrx-amdcccle (from .../fglrx-amdcccle_2%3a8.543-0ubuntu4_i386.deb) ...
Processing triggers for man-db ...
Setting up fglrx-kernel-source (2:8.543-0ubuntu4) ...
Adding Module to DKMS build system
Doing initial module build
Installing initial module
Done.

Setting up xorg-driver-fglrx (2:8.543-0ubuntu4) ...

Setting up fglrx-amdcccle (2:8.543-0ubuntu4) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place

```

I have no clue why the nvidia package is installed, but I don't think it really matters. It says I can autoremove it.

---

### Post by NickEvans on 2008-11-02
Result of running 'sudo modprobe -fv fglrx'
```

install /sbin/lrm-video fglrx 
sh: /sbin/lrm-video: not found
FATAL: Error running install command for fglrx

```

---

### Post by Dauthi4 on 2008-11-02
Hum...

Apparently it's not the same problem because the installation failed for me.

Can you remove the AIGLX extension and switch composite option to "Disable"
and restart X ? Just in case ...

And did you do 

```
sudo depmod -a
``` after your install ?

And FYI I guess that AIGLX has to be loaded in the "SeverLayout" section but maybe I'm wrong...

---

### Post by NickEvans on 2008-11-03
Nope, still not working :(

---

### Post by Dauthi4 on 2008-11-04
I've compared my working Xorg.log to yours and I guess that the problem is here :


```
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID PCI:1:5:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -6
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -6
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -6
drmOpenDevice: node name is /dev/dri/card3
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -6
drmOpenDevice: node name is /dev/dri/card4
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -6
drmOpenDevice: node name is /dev/dri/card5
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -6
drmOpenDevice: node name is /dev/dri/card6
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -6
drmOpenDevice: node name is /dev/dri/card7
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -6
drmOpenDevice: node name is /dev/dri/card8
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -6
drmOpenDevice: node name is /dev/dri/card9
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -6
drmOpenDevice: node name is /dev/dri/card10
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -6
drmOpenDevice: node name is /dev/dri/card11
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -6
drmOpenDevice: node name is /dev/dri/card12
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -6
drmOpenDevice: node name is /dev/dri/card13
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -6
drmOpenDevice: node name is /dev/dri/card14
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -6

```

Maybe we should concentrate on solving this :)

You may want to try

```
cd /dev/dri
ls
```

And paste your results

And also try this 

```
ln -s /usr/lib/xorg/modules/extensions/libdri.xorg /usr/lib/xorg/modules/extensions/libdri.so
ln -s /usr/lib/xorg/modules/dri /usr/lib/dri
```

I remembered that I've recently done that :)

---

### Post by NickEvans on 2008-11-04
Unfortunately this didn't help.

And there is nothing in /dev/dri

---

### Post by roy.kimbrell on 2008-11-05
I have what appears to be the same problem with a Sony Vaio VGN-A270P.  It has an ATI Mobility Radeon 9700 chipset.  I had upgraded 8.04 (Hardy) to 8.10 (Intrepid) and rebooted.  On the reboot, X would not load.  Xorg.0.log has toward the end...

drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed

Then it gives a backtrace.  There is nothing in /dev/dri

By the way, I had earlier booted a "live CD" with a Intrepid 8.10 alpha and that worked. I'll try that again and let you know what happens.

---

### Post by roy.kimbrell on 2008-11-05
Booted the same machine (the Sony Vaio) with the "live CD" 8.10 (Intrepid) alpha disk.  It worked.  The radeon module was loaded (I used lsmod to check) and /dev/dri/card0 did exist.  There seemed to be a few problems with X when trying to switch users, but I didn't play with it enough to determine exactly what the problems were.  Perhaps in fixing these problems, something else got broken.  

When rebooting the machine with 8.10 (Intrepid) X offered to start up in "low graphics" mode which I accepted and which worked (at a low graphics level).  This was the case also when booting the older vmlinuz-2.6.24-21-generic kernel as well as the more current vmlinuz-2.6.27-7-generic kernel.  So possibly not a kernel problem.

So the point of this is that the radeon modules and the kernel were working in the alpha version but not in the production version.

---

