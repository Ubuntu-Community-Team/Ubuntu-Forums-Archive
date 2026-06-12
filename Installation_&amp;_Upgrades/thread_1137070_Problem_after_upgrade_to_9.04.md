---
title: "Problem after upgrade to 9.04"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by dh003i on 2009-04-25
I just upgraded to 9.04, and immediately ran into an X problem when rebooting. 

I just get a blank screen, with a half inch square of random colors, which appears to be the "cursor". 

I'm using the Catalyst drivers, and my full /var/log/Xorg.0.log file is at the end of this message

In particular, I noticed these sections:

**Noticeable section of Xorg.0.log**
```
(WW) fglrx(0): Failed to open DRM connection
(--) fglrx(0): Video RAM: 524288 kByte, Type: GDDR3
(EE) fglrx(0): [FB] Can not get FB MC address range.
(II) fglrx(0): PCIE card detected
(--) fglrx(0): Using per-process page tables (PPPT) as GART.
(WW) fglrx(0): board is an unknown third party board, chipset is supported
...
(II) fglrx(0): driver needs X.org 1.4.x.y with x.y >= 99.906
(WW) fglrx(0): could not detect X server version (query_status=-1)
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
...
(WW) fglrx(0): Textured Video not supported without DRI enabled.
...
(EE) fglrx(0): XMM failed to open CMMQS connection.
(II) fglrx(0): XMM failed to initialize!
...
(EE) fglrx(0): PPLIB: PPLIB is not initialized!.
(EE) fglrx(0): PPLIB: swlPPLibNotifyEventToPPLib() failed!
(EE) fglrx(0):        ulEventType = 0000000c, ulEventData = 00000001
(EE) fglrx(0): PPLIB: PPLIB is not initialized!.
(EE) fglrx(0): PPLIB: swlPPLibNotifyEventToPPLib() failed!
(EE) fglrx(0):        ulEventType = 00000002, ulEventData = 00000000
(EE) fglrx(0): firegl_SetSuspendResumeState FAILED -9.
```

**Xorg.0.log**
```

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-15-server x86_64 Ubuntu
Current Operating System: Linux davidjheinrich 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64
Build Date: 09 April 2009  02:11:54AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@crested.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Apr 25 12:29:43 2009
(==) Using config file: "/etc/X11/xorg.conf"
(**) Option "defaultserverlayout" "DefaultLayout"
(**) ServerLayout "DefaultLayout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Sony GDM-F520"
(**) |   |-->Device "ATI Radeon HD4670"
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

(--) PCI:*(0@1:0:0) ATI Technologies Inc RV730XT [Radeon HD 4670] rev 0, Mem @ 0xd0000000/268435456, 0xfe8e0000/65536, I/O @ 0x0000b000/256, BIOS @ 0x????????/131072
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
(II) "dri" will be loaded. This was enabled by default and also specified in the config file.
(II) "dri2" will be loaded by default.
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.4.0, module version = 1.0.0
(II) Loading extension XFree86-DRI
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 1.4.99.906, module version = 8.60.40
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
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
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.4.0, module version = 1.0.0
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 1.4.99.906, module version = 8.60.40
	Module class: X.Org Video Driver
(II) Primary Device is: PCI 01@00:00:0
(WW) Falling back to old probe method for fglrx
(II) ATI Proprietary Linux Driver Version Identifier:8.60.40
(II) ATI Proprietary Linux Driver Release Identifier: 8.60.4                               
(II) ATI Proprietary Linux Driver Build Date: Mar 14 2009 21:46:40
(II) Loading PCS database from /etc/ati/amdpcsdb
(WW) This ATI Proprietary Linux Driver does not guarantee support of video driver ABI higher than 2.0
(WW) Video driver ABI version of the X server is 5.0
(--) Assigning device section with no busID to primary device
(--) Chipset Supported AMD Graphics Processor (0x9490) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) fglrx(0): pEnt->device->identifier=0x19cf060
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
	compiled for 1.6.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 5.0
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "dri" "on"
(**) fglrx(0): Option "UseFastTLS" "1"
(**) fglrx(0): Option "DPMS" "true"
(II) fglrx(0): 10BitPixelFormat disabled by default
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(**) fglrx(0): Gamma Correction for I is 0x06419064
(**) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(--) fglrx(0): Chipset: "ATI Radeon HD 4670" (Chipset = 0x9490)
(--) fglrx(0): (PciSubVendor = 0x1462, PciSubDevice = 0x1590)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
(--) fglrx(0): MMIO registers at 0xfe8e0000
(--) fglrx(0): I/O port at 0x0000b000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 5.0
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 5.0
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 11.9
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: RV730
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID PCI:1:0:0
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
(--) fglrx(0): Video RAM: 524288 kByte, Type: GDDR3
(EE) fglrx(0): [FB] Can not get FB MC address range.
(II) fglrx(0): PCIE card detected
(--) fglrx(0): Using per-process page tables (PPPT) as GART.
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) fglrx(0): RandR 1.2 support is enabled!
(II) fglrx(0): RandR 1.2 rotation support is enabled!
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) fglrx(0): ***Display: ConnectedDisplayTypes=0x00000101, disabled=0x00000000
(II) fglrx(0): Connected Display1: CRT on primary DAC [crt1]
(II) fglrx(0):  Display1: No EDID information from DDC.
(EE) fglrx(0): Unknown EDID version 0
(II) fglrx(0):  Display1: Failed to get EDID information. 
(II) fglrx(0): Connected Display2: DFP 3 [dfp3]
(II) fglrx(0): Display2 EDID data ---------------------------
(II) fglrx(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) fglrx(0): Year: 2002  Week: 47
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: Off
(II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) fglrx(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@72Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@56Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@72Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@70Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) fglrx(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) fglrx(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) fglrx(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) fglrx(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) fglrx(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) fglrx(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) fglrx(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) fglrx(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) fglrx(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) fglrx(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) fglrx(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff005a631134e09d0000
(II) fglrx(0): 	2f0c010380301e782a6492a3574a9c25
(II) fglrx(0): 	1550542fcf00a9408180615945593159
(II) fglrx(0): 	310a01010101d03900d0f36012906880
(II) fglrx(0): 	1310e02c1100001c3130806072601c90
(II) fglrx(0): 	68c81300f02c0100001cad31806072b0
(II) fglrx(0): 	1d4068c81300e02c1100001c000000fd
(II) fglrx(0): 	00095f166911000a2020202020200056
(II) fglrx(0): End of Display2 EDID data --------------------
(II) fglrx(0): Output DFP1 using monitor section Sony GDM-F520
(**) fglrx(0): Option "PreferredMode" "2048x1536_85.00"
(WW) fglrx(0): Option "MinClock" requires a frequency value
(WW) fglrx(0): Option "MaxClock" requires a frequency value
(II) fglrx(0): Output DFP3 has no monitor section
(II) fglrx(0): Output CRT1 has no monitor section
(II) fglrx(0): Output CRT2 has no monitor section
(**) fglrx(0): Option "ModeDebug" "True"
(II) fglrx(0): EDID for output DFP1
(II) fglrx(0): EDID for output DFP3
(II) fglrx(0): Manufacturer: VSC  Model: 3411  Serial#: 40416
(II) fglrx(0): Year: 2002  Week: 47
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max Image Size [cm]: horiz.: 48  vert.: 30
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: Off
(II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.638 redY: 0.342   greenX: 0.290 greenY: 0.609
(II) fglrx(0): blueX: 0.146 blueY: 0.083   whiteX: 0.312 whiteY: 0.330
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@72Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@56Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@72Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@70Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) fglrx(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) fglrx(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) fglrx(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) fglrx(0): #5: hsize: 640  vsize 400  refresh: 70  vid: 2609
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 148.0 MHz   Image Size:  480 x 300 mm
(II) fglrx(0): h_active: 3840  h_sync: 3944  h_sync_end 4328 h_blank_end 4816 h_border: 0
(II) fglrx(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2418 v_border: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 123.4 MHz   Image Size:  240 x 300 mm
(II) fglrx(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) fglrx(0): v_active: 2400  v_sync: 2401  v_sync_end 2404 v_blanking: 2428 v_border: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 127.2 MHz   Image Size:  480 x 300 mm
(II) fglrx(0): h_active: 1920  h_sync: 2024  h_sync_end 2224 h_blank_end 2528 h_border: 0
(II) fglrx(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1229 v_border: 0
(II) fglrx(0): Ranges: V min: 9 V max: 95 Hz, H min: 22 H max: 105 kHz, PixClock max 170 MHz
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	000000000000000072782830293a2045
(II) fglrx(0): 	4449442028696e20686578293a0a0020
(II) fglrx(0): 	20000a00cf00a9405100000000000000
(II) fglrx(0): 	106ea4010000000072782830293a2052
(II) fglrx(0): 	616e6765733a2056206d696e3a202569
(II) fglrx(0): 	2056206d61783a20256920487a2c2048
(II) fglrx(0): 	206d696e3a2025692048206d61783a20
(II) fglrx(0): 	2569206b487a2c005100000000000000
(II) fglrx(0): Not using mode "3840x2400" (height too large for virtual size)
(II) fglrx(0): Not using mode "1920x2400" (height too large for virtual size)
(II) fglrx(0): Not using default mode "640x350" (unknown reason)
(II) fglrx(0): Not using default mode "640x400" (unknown reason)
(II) fglrx(0): Not using default mode "720x400" (unknown reason)
(II) fglrx(0): Not using default mode "640x480" (unknown reason)
(II) fglrx(0): Not using default mode "800x600" (unknown reason)
(II) fglrx(0): Not using default mode "1280x960" (unknown reason)
(II) fglrx(0): Not using default mode "1280x1024" (unknown reason)
(II) fglrx(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "832x624" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (unknown reason)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1360x768" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1600x1024" (unknown reason)
(II) fglrx(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1680x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Printing probed modes for output DFP3
(II) fglrx(0): Modeline "1920x1200"x41.0  127.17  1920 2024 2224 2528  1200 1201 1204 1229 -hsync +vsync (50.3 kHz)
(II) fglrx(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) fglrx(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
(II) fglrx(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) fglrx(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 -hsync +vsync (47.8 kHz)
(II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
(II) fglrx(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) fglrx(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) fglrx(0): Modeline "1024x768"x70.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) fglrx(0): Modeline "800x600"x85.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) fglrx(0): Modeline "800x600"x72.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) fglrx(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) fglrx(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 -hsync +vsync (43.8 kHz)
(II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 -hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) fglrx(0): Modeline "640x480"x72.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) fglrx(0): Modeline "640x400"x75.0   28.07  640 696 736 832  400 413 415 449 +hsync +vsync (33.7 kHz)
(II) fglrx(0): Modeline "640x400"x60.0   24.92  640 664 760 792  400 460 462 525 +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "512x384"x60.0   19.81  512 544 624 664  384 451 453 497 +hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "512x384"x75.0   19.68  512 528 576 632  384 384 385 416 +hsync +vsync (31.1 kHz)
(II) fglrx(0): Modeline "400x300"x75.0   24.75  400 408 448 528  300 601 602 625 doublescan +hsync +vsync (46.9 kHz)
(II) fglrx(0): Modeline "400x300"x60.0   22.33  400 416 480 496  300 601 605 742 doublescan +hsync +vsync (45.0 kHz)
(II) fglrx(0): Modeline "320x240"x75.0   15.75  320 328 360 416  240 481 482 501 vscan 516096003 doublescan +hsync +vsync (37.9 kHz)
(II) fglrx(0): Modeline "320x240"x60.0   12.59  320 328 376 400  240 491 493 525 doublescan +hsync +vsync (0.0 kHz)
(II) fglrx(0): Modeline "320x200"x75.0   13.10  320 352 368 416  200 406 407 417 vscan 16777216 doublescan +hsync +vsync (0.0 kHz)
(II) fglrx(0): Modeline "320x200"x60.0   12.59  320 336 384 400  200 457 459 524 vscan 1572904 doublescan +hsync +vsync (0.0 kHz)
(II) fglrx(0): EDID for output CRT1
(II) fglrx(0): Not using default mode "640x350" (vrefresh out of range)
(II) fglrx(0): Not using default mode "640x400" (vrefresh out of range)
(II) fglrx(0): Not using default mode "720x400" (vrefresh out of range)
(II) fglrx(0): Not using default mode "640x480" (unknown reason)
(II) fglrx(0): Not using default mode "640x480" (vrefresh out of range)
(II) fglrx(0): Not using default mode "640x480" (vrefresh out of range)
(II) fglrx(0): Not using default mode "640x480" (vrefresh out of range)
(II) fglrx(0): Not using default mode "800x600" (vrefresh out of range)
(II) fglrx(0): Not using default mode "800x600" (vrefresh out of range)
(II) fglrx(0): Not using default mode "800x600" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1024x768" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1024x768" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1024x768" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1280x960" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1792x1344" (unknown reason)
(II) fglrx(0): Not using default mode "1792x1344" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1856x1392" (unknown reason)
(II) fglrx(0): Not using default mode "1856x1392" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1920x1440" (unknown reason)
(II) fglrx(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) fglrx(0): Not using default mode "832x624" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1152x864" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1360x768" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1600x1024" (unknown reason)
(II) fglrx(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1680x1050" (unknown reason)
(II) fglrx(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) fglrx(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) fglrx(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) fglrx(0): Not using default mode "2048x1536" (unknown reason)
(II) fglrx(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) fglrx(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) fglrx(0): Printing probed modes for output CRT1
(II) fglrx(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) fglrx(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 vscan -1745712640 -hsync +vsync (65.3 kHz)
(II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) fglrx(0): Modeline "1280x1024"x47.0   85.51  1280 1344 1480 1680  1024 1025 1028 1083 interlace -hsync +vsync (0.0 kHz)
(II) fglrx(0): Modeline "1280x1024"x43.0   77.80  1280 1344 1480 1680  1024 1025 1028 1077 interlace -hsync +vsync (46.3 kHz)
(II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 vscan 627647776 -hsync +vsync (209186906458197751496704.0 kHz)
(II) fglrx(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (0.0 kHz)
(II) fglrx(0): Modeline "1152x864"x47.0   64.67  1152 1208 1328 1504  864 865 868 915 interlace -hsync +vsync (43.0 kHz)
(II) fglrx(0): Modeline "1152x864"x43.0   58.28  1152 1200 1320 1488  864 865 868 911 vscan 193 interlace -hsync +vsync (0.0 kHz)
(II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 -hsync +vsync (0.0 kHz)
(II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
(II) fglrx(0): Modeline "1280x720"x50.0   60.46  1280 1328 1456 1632  720 721 724 741 vscan 94500 -hsync +vsync (0.0 kHz)
(II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) fglrx(0): Modeline "1024x768"x43.0   44.90  1024 1032 1208 1264  768 768 772 817 vscan 1048 interlace +hsync +vsync (0.0 kHz)
(II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 vscan 192 +hsync +vsync (0.0 kHz)
(II) fglrx(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) fglrx(0): Modeline "800x600"x47.0   29.60  800 816 896 992  600 601 604 635 vscan -1745712544 interlace -hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 -hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 vscan 543761696 -hsync -vsync (0.0 kHz)
(II) fglrx(0): Modeline "640x400"x60.0   24.92  640 664 760 792  400 460 462 525 vscan 32 +hsync +vsync (0.0 kHz)
(II) fglrx(0): Modeline "512x384"x60.0   19.81  512 544 624 664  384 451 453 497 +hsync +vsync (29.8 kHz)
(II) fglrx(0): Modeline "400x300"x60.0   22.33  400 416 480 496  300 601 605 742 vscan -1745712544 doublescan +hsync +vsync (0.0 kHz)
(II) fglrx(0): Modeline "320x240"x60.0   12.59  320 328 376 400  240 491 493 525 doublescan +hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "320x200"x60.0   12.59  320 336 384 400  200 457 459 524 vscan 600 doublescan +hsync +vsync (0.0 kHz)
(II) fglrx(0): EDID for output CRT2
(II) fglrx(0): Output DFP1 disconnected
(II) fglrx(0): Output DFP3 connected
(II) fglrx(0): Output CRT1 connected
(II) fglrx(0): Output CRT2 disconnected
(II) fglrx(0): Using exact sizes for initial modes
(II) fglrx(0): Output DFP3 using initial mode 1600x1200
(II) fglrx(0): Output CRT1 using initial mode 1600x1200
(**) fglrx(0): Display dimensions: (406, 303) mm
(**) fglrx(0): DPI set to (128, 128)
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): QBS disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.2.1
	ABI class: X.Org Video Driver, version 5.0
(**) fglrx(0): NoDRI = NO
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x8000001d
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(WW) fglrx(0): No DRM connection for driver fglrx.
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(**) fglrx(0): UseFastTLS=1
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
(WW) fglrx(0): could not detect X server version (query_status=-1)
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0x0 FBMappedSize: 0x10000000
(II) fglrx(0): FBMM initialized for area (0,0)-(2048,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(2048,1536) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 2048 x 6655
(==) fglrx(0): Backing store disabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(**) fglrx(0): DPMS enabled
(II) fglrx(0): Initialized in-driver Xinerama extension
(WW) fglrx(0): Textured Video not supported without DRI enabled.
(II) LoadModule: "glesx"
(II) Loading /usr/lib/xorg/modules//glesx.so
(II) Module glesx: vendor="X.Org Foundation"
	compiled for 1.4.99.906, module version = 1.0.0
(II) Loading extension GLESX
(II) fglrx(0): GLESX enableFlags = 78
(II) fglrx(0): Acceleration enabled
(II) LoadModule: "amdxmm"
(II) Loading /usr/lib/xorg/modules//amdxmm.so
(II) Module amdxmm: vendor="X.Org Foundation"
	compiled for 1.4.99.906, module version = 1.0.0
(EE) fglrx(0): XMM failed to open CMMQS connection.
(II) fglrx(0): XMM failed to initialize!
(II) fglrx(0): Enable composite support successfully
(WW) fglrx(0): Option "CRT1" is not used
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(WW) fglrx(0): Option "TargetRefresh" is not used
(WW) fglrx(0): Option "MinClock" is not used
(WW) fglrx(0): Option "MaxClock" is not used
(WW) fglrx(0): Option "PreferredMode" is not used
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using HW cursor of display infrastructure!
(==) fglrx(0): Using software cursor
(II) fglrx(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(II) fglrx(0): atiddxDisplayScreenLoadPalette: numColors: 256
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
(II) AIGLX: Screen 0 is not DRI capable
[glesx] __glESXExtensionInit: No GL ES2.0 capable screen found!
(II) fglrx(0): Setting screen physical size to 423 x 317
(II) fglrx(0): Restoring recent mode: 1600x1200@60Hz
(II) config/hal: Adding input device Composite USB PS2 Converter USB to PS2 Adaptor  V3.10
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: always reports core events
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: Device: "/dev/input/event7"
(II) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: Found 10 mouse buttons
(II) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: Found x and y relative axes
(II) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: Found keys
(II) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: Configuring as mouse
(II) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: Configuring as keyboard
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: YAxisMapping: buttons 4 and 5
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Composite USB PS2 Converter USB to PS2 Adaptor  V3.10" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: xkb_layout: "us"
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: (accel) keeping acceleration scheme 1
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: (accel) filter chain progression: 2.00
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: (accel) filter stage 0: 20.00 ms
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: (accel) set acceleration profile 0
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) AT Translated Set 2 keyboard: xkb_layout: "us"
(II) config/hal: Adding input device Logitech USB Receiver
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event9"
(II) Logitech USB Receiver: Found 1 mouse buttons
(II) Logitech USB Receiver: Found keys
(II) Logitech USB Receiver: Configuring as keyboard
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Logitech USB Receiver: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Logitech USB Receiver: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Logitech USB Receiver: xkb_layout: "us"
(II) config/hal: Adding input device Composite USB PS2 Converter USB to PS2 Adaptor  V3.10
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: always reports core events
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: Device: "/dev/input/event6"
(II) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: Found keys
(II) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: Configuring as keyboard
(II) XINPUT: Adding extended input device "Composite USB PS2 Converter USB to PS2 Adaptor  V3.10" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Composite USB PS2 Converter USB to PS2 Adaptor  V3.10: xkb_layout: "us"
(II) config/hal: Adding input device Wacom Bamboo
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(II) Wacom driver level: 47-0.8.2-1 $
(**) Wacom Bamboo: always reports core events
(**) Wacom Bamboo device is /dev/input/event5
(**) Wacom Bamboo (Wacom Bamboo) is not a pad 
(**) Wacom Bamboo is in absolute mode
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) Wacom Bamboo: serial speed 9600
(II) XINPUT: Adding extended input device "Wacom Bamboo" (type: Wacom Stylus)
(**) Option "Device" "/dev/input/event5"
Wacom Bamboo Wacom X driver grabbed event device
(==) Wacom using pressure threshold of 30 for button 1
(==) Wacom USB Bamboo tablet speed=9600 (38400) maxX=14760 maxY=9225 maxZ=511 resX=2540 resY=2540  tilt=disabled
(==) Wacom device "Wacom Bamboo" top X=0 top Y=0 bottom X=14760 bottom Y=9225 resol X=2540 resol Y=2540
(II) config/hal: Adding input device Wacom Bamboo pad
(**) Wacom Bamboo pad: always reports core events
(**) Wacom Bamboo pad device is /dev/input/event5
(**) Wacom Bamboo pad is in relative mode
(**) WACOM: suppress value is 2
(**) Wacom Bamboo pad: reading USB link
(**) Wacom Bamboo pad: threshold = 30
(**) Wacom Bamboo pad: max x = 14760
(**) Wacom Bamboo pad: max y = 9225
(**) Wacom Bamboo pad: max z = 511
(**) Option "BaudRate" "9600"
(**) Wacom Bamboo pad: serial speed 9600
(II) XINPUT: Adding extended input device "Wacom Bamboo pad" (type: Wacom Pad)
(==) Wacom device "Wacom Bamboo pad" top X=0 top Y=0 bottom X=14760 bottom Y=9225 resol X=2540 resol Y=2540
(II) config/hal: Adding input device Wacom Bamboo cursor
(**) Wacom Bamboo cursor: always reports core events
(**) Wacom Bamboo cursor device is /dev/input/event5
(**) Wacom Bamboo cursor (Wacom Bamboo cursor) is not a pad 
(**) Wacom Bamboo cursor is in relative mode
(**) WACOM: suppress value is 2
(**) Wacom Bamboo cursor: reading USB link
(**) Wacom Bamboo cursor: threshold = 30
(**) Wacom Bamboo cursor: max x = 14760
(**) Wacom Bamboo cursor: max y = 9225
(**) Wacom Bamboo cursor: max z = 511
(**) Option "BaudRate" "9600"
(**) Wacom Bamboo cursor: serial speed 9600
(II) XINPUT: Adding extended input device "Wacom Bamboo cursor" (type: Wacom Cursor)
(==) Wacom device "Wacom Bamboo cursor" top X=0 top Y=0 bottom X=14760 bottom Y=9225 resol X=2540 resol Y=2540
(II) config/hal: Adding input device Wacom Bamboo eraser
(**) Wacom Bamboo eraser: always reports core events
(**) Wacom Bamboo eraser device is /dev/input/event5
(**) Wacom Bamboo eraser (Wacom Bamboo eraser) is not a pad 
(**) Wacom Bamboo eraser is in absolute mode
(**) WACOM: suppress value is 2
(**) Wacom Bamboo eraser: reading USB link
(**) Wacom Bamboo eraser: threshold = 30
(**) Wacom Bamboo eraser: max x = 14760
(**) Wacom Bamboo eraser: max y = 9225
(**) Wacom Bamboo eraser: max z = 511
(**) Option "BaudRate" "9600"
(**) Wacom Bamboo eraser: serial speed 9600
(II) XINPUT: Adding extended input device "Wacom Bamboo eraser" (type: Wacom Eraser)
(==) Wacom device "Wacom Bamboo eraser" top X=0 top Y=0 bottom X=14760 bottom Y=9225 resol X=2540 resol Y=2540
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
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
(II) config/hal: Adding input device Logitech USB Receiver
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event8"
(II) Logitech USB Receiver: Found 16 mouse buttons
(II) Logitech USB Receiver: Found x and y relative axes
(II) Logitech USB Receiver: Configuring as mouse
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: MOUSE)
(**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
(**) Logitech USB Receiver: (accel) filter chain progression: 2.00
(**) Logitech USB Receiver: (accel) filter stage 0: 20.00 ms
(**) Logitech USB Receiver: (accel) set acceleration profile 0
(EE) fglrx(0): PPLIB: PPLIB is not initialized!.
(EE) fglrx(0): PPLIB: swlPPLibNotifyEventToPPLib() failed!
(EE) fglrx(0):        ulEventType = 0000000c, ulEventData = 00000001
(EE) fglrx(0): PPLIB: PPLIB is not initialized!.
(EE) fglrx(0): PPLIB: swlPPLibNotifyEventToPPLib() failed!
(EE) fglrx(0):        ulEventType = 00000002, ulEventData = 00000000
(EE) fglrx(0): firegl_SetSuspendResumeState FAILED -9.
```

---

### Post by peakshysteria on 2009-04-25
How did you upgrade? What version where you upgrading from? And did you have a working ATI driver for your ATI Radeon HD4670 card before upgrading? As far as I can remember we were advised to uninstall any ATI drivers before upgrading (I did not and it went very well). Did you get any prompt during upgrade telling that your card wasn't supported?

Boot into safemode and uninstall the driver --> Reboot --> then install the necessary driver if available and if in need.

---

### Post by dh003i on 2009-04-27
I did that, but I still have problems: now after I login, I don't see window borders, can't open my KDE menu, and pretty much can't do anything except open a full-screen file-manager (Dolphin) window and navigate around. 

I did the following: rebooted, then entered safe mode and did this:
```

cd /usr/share/ati
sudo sh ./fglrx-uninstall.sh
```

---

### Post by dh003i on 2009-05-01
Bump...does anyone have any ideas here?

---

### Post by emarkay on 2009-05-01
Welcome to the club!   :(

See this thread to get the progress on this (apparent) issue:

[http://ubuntuforums.org/showthread.php?t=1133931](http://ubuntuforums.org/showthread.php?t=1133931)

---

