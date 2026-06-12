---
title: "ATI 3870 FGLRX Black Screen on Laptop, External works though"
date: 2009-11-05
forum: Hardware
---

### Post by PeonDevelopments on 2009-11-05
Basically I installed the 9.10 catalyst drivers in Kubuntu 9.10. Booting up gives me a black screen. I can revert to the previous drivers that work, but offer no 3d acceleration.

Thing is, by plugging in my laptop to an external monitor, I can view my desktop with 3d acceleration on that monitor. (GLXGears gives me about 35000 frames per second, better than the previous 7000 on Kubuntu 8.10)

I figure that somehow, the connection between my laptop screen is failing. 

Xorg log files report no errors.
xorg.conf has no issues.
Tried both official catalyst and repository drivers.

Graphics Card: ATI HD Radeon 3870 (512MB) x1

---

### Post by PeonDevelopments on 2009-11-06
I have an external monitor with a resolution of 1920x1200.
When connecting my laptop to it, viewing the SystemSettings I see that my laptop's "supposed" resolution tops out at 1400x1050. It's supposed to be 1920x1200 as well.

---

### Post by PeonDevelopments on 2009-11-07
Here are my xorg.conf and Xorg.0.logs.


xorg.conf:
```

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
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
	BusID       "PCI:6:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes	"1920x1200" "1600x1050"
	EndSubSection
EndSection


```

and my xorg log file:
```


X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server x86_64 Ubuntu
Current Operating System: Linux phoenix 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64
Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.31-14-generic root=UUID=06a5ad23-6fd6-44b7-89e2-3df085e2ee3d ro quiet splash
Build Date: 26 October 2009  05:19:56PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Nov  7 05:29:08 2009
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
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0xb40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0:6:0:0) 1002:9509:161f:207a ATI Technologies Inc rev 0, Mem @ 0xd0000000/268435456, 0xf8100000/65536, I/O @ 0x00002000/256, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.4.0, module version = 1.0.0
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.4.0, module version = 1.0.0
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 1.4.99.906, module version = 8.66.2
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 1.4.99.906, module version = 8.66.2
	Module class: X.Org Video Driver
(II) Primary Device is: PCI 06@00:00:0
(WW) Falling back to old probe method for fglrx
(II) ATI Proprietary Linux Driver Version Identifier:8.66.2
(II) ATI Proprietary Linux Driver Release Identifier: 8.661                                
(II) ATI Proprietary Linux Driver Build Date: Sep 23 2009 17:30:33
(II) Loading PCS database from /etc/ati/amdpcsdb
(--) Chipset Supported AMD Graphics Processor (0x9509) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@6:0:1) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) fglrx(0): pEnt->device->identifier=0x1c82c30
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
(II) fglrx(0): PCI bus 6 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "DPMS" "true"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Loading sub module "dri"
(II) LoadModule: "dri"
(II) Reloading /usr/lib/xorg/modules/extensions//libdri.so
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Loading extension XFree86-DRI
drmDynamicMajor: found major device number 251
drmDynamicMajor: found major device number 251
drmOpenByBusid: Searching for BusID PCI:6:0:0
drmOpenDevice: node name is /dev/ati/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports PCI:6:0:0
(--) fglrx(0): Chipset: "ATI Mobility Radeon HD 3870 X2" (Chipset = 0x9509)
(--) fglrx(0): (PciSubVendor = 0x161f, PciSubDevice = 0x207a)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
(--) fglrx(0): MMIO registers at 0xf8100000
(--) fglrx(0): I/O port at 0x00002000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) fglrx(0): AC Adapter is used
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
(--) fglrx(0): Video RAM: 524288 kByte, Type: DDR3
(II) fglrx(0): PCIE card detected
(--) fglrx(0): Using per-process page tables (PPPT) as GART.
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) fglrx(0): Using adapter: 6:0.0.
(II) fglrx(0): [FB] MC range(MCFBBase = 0xc0000000, MCFBSize = 0x20000000)
(II) fglrx(0): Interrupt handler installed at IRQ 35.
(II) fglrx(0): IRQ 35 Enabled.
(II) fglrx(0): RandR 1.2 support is enabled!
(II) fglrx(0): RandR 1.2 rotation support is enabled!
(==) fglrx(0): Center Mode is disabled 
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) fglrx(0): Finished Initialize PPLIB!
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) fglrx(0): ***Display: ConnectedDisplayTypes=0x00000003, disabled=0x00000000
(II) fglrx(0): Connected Display1: CRT on primary DAC [crt1]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: SAM  Model: 56d  Serial#: 1129132596
(II) fglrx(0): Year: 2009  Week: 40
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) fglrx(0): Sync:  Separate  Composite  SyncOnGreen
(II) fglrx(0): Max Image Size [cm]: horiz.: 52  vert.: 32
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: Off; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.650 redY: 0.337   greenX: 0.296 greenY: 0.604
(II) fglrx(0): blueX: 0.147 blueY: 0.074   whiteX: 0.312 whiteY: 0.329
(II) fglrx(0): Supported established timings:
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 800x600@56Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported standard timings:
(II) fglrx(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) fglrx(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) fglrx(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) fglrx(0): #4: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) fglrx(0): Supported detailed timing:
(II) fglrx(0): clock: 154.0 MHz   Image Size:  518 x 324 mm
(II) fglrx(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
(II) fglrx(0): v_active: 1200  v_sync: 1203  v_sync_end 1209 v_blanking: 1235 v_border: 0
(II) fglrx(0): Ranges: V min: 50 V max: 63 Hz, H min: 30 H max: 81 kHz, PixClock max 170 MHz
(II) fglrx(0): Monitor name: SyncMaster
(II) fglrx(0): Serial No: H9NS903127
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff004c2d6d0534324d43
(II) fglrx(0): 	281301030e3420782a9fc1a6564b9a25
(II) fglrx(0): 	135054230800a9408180814095008100
(II) fglrx(0): 	010101010101283c80a070b023403020
(II) fglrx(0): 	360006442100001a000000fd00323f1e
(II) fglrx(0): 	5111000a202020202020000000fc0053
(II) fglrx(0): 	796e634d61737465720a2020000000ff
(II) fglrx(0): 	0048394e533930333132370a20200019
(II) fglrx(0): End of Display1 EDID data --------------------
(II) fglrx(0): Connected Display2: LCD on internal LVDS [lvds]
(II) fglrx(0): Display2 EDID data ---------------------------
(II) fglrx(0): Manufacturer: LGD  Model: 3901  Serial#: 0
(II) fglrx(0): Year: 2008  Week: 0
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max Image Size [cm]: horiz.: 37  vert.: 23
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): No DPMS capabilities specified
(II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.614 redY: 0.353   greenX: 0.321 greenY: 0.561
(II) fglrx(0): blueX: 0.152 blueY: 0.124   whiteX: 0.313 whiteY: 0.329
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported detailed timing:
(II) fglrx(0): clock: 154.0 MHz   Image Size:  367 x 230 mm
(II) fglrx(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
(II) fglrx(0): v_active: 1200  v_sync: 1203  v_sync_end 1209 v_blanking: 1235 v_border: 0
(II) fglrx(0):  LG Display
(II) fglrx(0):  LP171WU3-TLB3
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff0030e4013900000000
(II) fglrx(0): 	00120103802517780a56359d5a528f27
(II) fglrx(0): 	1f505400000001010101010101010101
(II) fglrx(0): 	010101010101283c80a070b023403020
(II) fglrx(0): 	36006fe6100000190000000000000000
(II) fglrx(0): 	00000000000000000000000000fe004c
(II) fglrx(0): 	4720446973706c61790a2020000000fe
(II) fglrx(0): 	004c503137315755332d544c423300d7
(II) fglrx(0): End of Display2 EDID data --------------------
(II) fglrx(0): Output LCD using monitor section aticonfig-Monitor[0]-0
(II) fglrx(0): Output DFP1 has no monitor section
(II) fglrx(0): Output CRT1 has no monitor section
(II) fglrx(0): EDID vendor "LGD", prod id 14593
(II) fglrx(0): Printing DDC gathered Modelines:
(II) fglrx(0): Modeline "1920x1200"x0.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 -hsync -vsync (74.0 kHz)
(II) fglrx(0): Output LCD connected
(II) fglrx(0): Output DFP1 disconnected
(II) fglrx(0): Output CRT1 connected
(II) fglrx(0): Using user preference for initial modes
(II) fglrx(0): Output LCD using initial mode 1400x1050
(II) fglrx(0): Output CRT1 using initial mode 1920x1200
(II) fglrx(0): Display dimensions: (370, 230) mm
(II) fglrx(0): DPI set to (96, 115)
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): QBS disabled
(==) fglrx(0):  PseudoColor visuals disabled
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.2.1
	ABI class: X.Org Video Driver, version 5.0
(==) fglrx(0): NoDRI = NO
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
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
(WW) fglrx(0): could not detect X server version (query_status=-1)
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
(II) fglrx(0): DRIScreenInit for fglrx driver
drmDynamicMajor: found major device number 251
drmDynamicMajor: found major device number 251
drmDynamicMajor: found major device number 251
drmOpenByBusid: Searching for BusID PCI:6:0:0
drmOpenDevice: node name is /dev/ati/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: drmOpenMinor returns 10
drmOpenByBusid: drmGetBusid reports PCI:6:0:0
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:6:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0x2000
(II) fglrx(0): [drm] mapped SAREA 0x2000 to 0x7fdb8552e000
(II) fglrx(0): [drm] framebuffer handle = 0x3000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.66.2
(II) fglrx(0):     Date: Sep 23 2009
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.31-14-generic
(II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
(II) fglrx(0):     Build-Kernel __SMP__:            yes
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0x00004000
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0xc0000000 FBMappedSize: 0x0102c000
(II) fglrx(0): FBMM initialized for area (0,0)-(1920,2208)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1920,1920) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1920 x 288
(==) fglrx(0): Backing store disabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(**) fglrx(0): DPMS enabled
(**) fglrx(0): Textured Video is enabled.
(II) LoadModule: "glesx"
(II) Loading /usr/lib/xorg/modules//glesx.so
(II) Module glesx: vendor="X.Org Foundation"
	compiled for 1.4.99.906, module version = 1.0.0
(II) Loading extension GLESX
(II) fglrx(0): GLESX enableFlags = 94
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	Solid Horizontal and Vertical Lines
	Driver provided ScreenToScreenBitBlt replacement
	Driver provided FillSolidRects replacement
(II) fglrx(0): GLESX is enabled
(II) LoadModule: "amdxmm"
(II) Loading /usr/lib/xorg/modules//amdxmm.so
(II) Module amdxmm: vendor="X.Org Foundation"
	compiled for 1.4.99.906, module version = 1.0.0
(II) Loading extension AMDXVOPL
(II) fglrx(0): UVD2 feature is available
(II) fglrx(0): Enable composite support successfully
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): [DRI] installation complete
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using HW cursor of display infrastructure!
(==) fglrx(0): Using software cursor
(II) fglrx(0): Disabling in-server RandR and enabling in-driver RandR 1.2.
(II) fglrx(0): 'LVDS LCD' ConnectorType, abstracted as 'Panel'
(II) fglrx(0): 'eDP LCD' ConnectorType, abstracted as 'Panel'
(--) RandR disabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
drmDynamicMajor: found major device number 251
drmDynamicMajor: found major device number 251
drmOpenByBusid: Searching for BusID PCI:6:0:0
drmOpenDevice: node name is /dev/ati/card0
drmOpenDevice: open result is 12, (OK)
drmOpenByBusid: drmOpenMinor returns 12
drmOpenByBusid: drmGetBusid reports PCI:6:0:0
(II) AIGLX: Loaded and initialized /usr/X11R6/lib64/modules/dri/fglrx_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) fglrx(0): Enable the clock gating!
(II) fglrx(0): Setting screen physical size to 503 x 262
(II) fglrx(0): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 2.2.5
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event5"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device 2.0M Pixel Camera
(**) 2.0M Pixel Camera: always reports core events
(**) 2.0M Pixel Camera: Device: "/dev/input/event7"
(II) 2.0M Pixel Camera: Found keys
(II) 2.0M Pixel Camera: Configuring as keyboard
(II) XINPUT: Adding extended input device "2.0M Pixel Camera" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Logitech USB Multimedia Keyboard
(**) Logitech USB Multimedia Keyboard: always reports core events
(**) Logitech USB Multimedia Keyboard: Device: "/dev/input/event9"
(II) Logitech USB Multimedia Keyboard: Found 13 mouse buttons
(II) Logitech USB Multimedia Keyboard: Found keys
(II) Logitech USB Multimedia Keyboard: Configuring as keyboard
(**) Logitech USB Multimedia Keyboard: YAxisMapping: buttons 4 and 5
(**) Logitech USB Multimedia Keyboard: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB Multimedia Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Logitech USB Multimedia Keyboard
(**) Logitech USB Multimedia Keyboard: always reports core events
(**) Logitech USB Multimedia Keyboard: Device: "/dev/input/event8"
(II) Logitech USB Multimedia Keyboard: Found keys
(II) Logitech USB Multimedia Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "Logitech USB Multimedia Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Sleep Button
(**) Sleep Button: always reports core events
(**) Sleep Button: Device: "/dev/input/event3"
(II) Sleep Button: Found keys
(II) Sleep Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event2"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Video Bus
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event6"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event4"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/hal: Adding input device SynPS/2 Synaptics TouchPad
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.1.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(II) Synaptics touchpad driver version 1.1.2
(**) Option "Device" "/dev/input/event11"
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
(II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
(II) SynPS/2 Synaptics TouchPad: buttons: left right middle
(--) SynPS/2 Synaptics TouchPad: touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
(**) SynPS/2 Synaptics TouchPad: (accel) filter chain progression: 2.00
(**) SynPS/2 Synaptics TouchPad: (accel) filter stage 0: 20.00 ms
(**) SynPS/2 Synaptics TouchPad: (accel) set acceleration profile 0
(--) SynPS/2 Synaptics TouchPad: touchpad found
(II) config/hal: Adding input device Logitech Trackball
(**) Logitech Trackball: always reports core events
(**) Logitech Trackball: Device: "/dev/input/event10"
(II) Logitech Trackball: Found 3 mouse buttons
(II) Logitech Trackball: Found x and y relative axes
(II) Logitech Trackball: Found scroll wheel(s)
(II) Logitech Trackball: Configuring as mouse
(**) Logitech Trackball: YAxisMapping: buttons 4 and 5
(**) Logitech Trackball: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech Trackball" (type: MOUSE)
(**) Logitech Trackball: (accel) keeping acceleration scheme 1
(**) Logitech Trackball: (accel) filter chain progression: 2.00
(**) Logitech Trackball: (accel) filter stage 0: 20.00 ms
(**) Logitech Trackball: (accel) set acceleration profile 0
(II) Logitech Trackball: initialized for relative axes.
(II) fglrx(0): EDID vendor "LGD", prod id 14593
(II) fglrx(0): Printing DDC gathered Modelines:
(II) fglrx(0): Modeline "1920x1200"x0.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 -hsync -vsync (74.0 kHz)
(II) fglrx(0): EDID vendor "LGD", prod id 14593
(II) fglrx(0): Printing DDC gathered Modelines:
(II) fglrx(0): Modeline "1920x1200"x0.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 -hsync -vsync (74.0 kHz)
(II) fglrx(0): EDID vendor "LGD", prod id 14593
(II) fglrx(0): Printing DDC gathered Modelines:
(II) fglrx(0): Modeline "1920x1200"x0.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 -hsync -vsync (74.0 kHz)

```

There are no errors (EE) in it.

---

### Post by bears on 2010-04-08
Have the same problem myself - graphics are not broken as they display through HDMI, but the laptop panel just doesn't display anything. My gfx card is also an ATI 3870 512MB in an ARIMA W840 chassis (The Alienware M17).

The problem still seems to exist in 10.04, which is not good. I've seen a few reports like this elsewhere, but as there is apparently no diagnostic to go on - because the xorg server is working - there seem to be no suggestions to fix it. :(

---

### Post by Dan09 on 2010-04-12
> **bears said:**
> Have the same problem myself - graphics are not broken as they display through HDMI, but the laptop panel just doesn't display anything. My gfx card is also an ATI 3870 512MB in an ARIMA W840 chassis (The Alienware M17).

The problem still seems to exist in 10.04, which is not good. I've seen a few reports like this elsewhere, but as there is apparently no diagnostic to go on - because the xorg server is working - there seem to be no suggestions to fix it. :(

Hey guys, I have the same problem too on a AlienwareM17 with 2X 3870's. Unfortunatly, I'm a total noob to Linux and cannot figure out how to switch back to the semi-working open source drivers.

Any ideas on how I should go about doing this?

---

### Post by bears on 2010-04-17
> **Dan09 said:**
> Hey guys, I have the same problem too on a AlienwareM17 with 2X 3870's. Unfortunatly, I'm a total noob to Linux and cannot figure out how to switch back to the semi-working open source drivers.

Any ideas on how I should go about doing this?

If you are using 9.10 or 10.04, then you simply need to delete the file "/etc/X11/xorg.conf" and reboot. The system will then automatically use the open-source driver and probe for required settings.

You can delete this file by starting Ubuntu in its equivalent of recovery mode (from the boot menu) and then from the next text menu (with a blue background) select to run a single user/root session. You will be given a simple text session in which you can delete the file by typing "rm /etc/X11/xorg.conf" - without the quotes - and pressing the enter key. You can then reboot by typing "reboot" and pressing the enter key, or just press and release the power button and it will shut down (mine does, anyway).

Hope that helps.

Rog.

---

