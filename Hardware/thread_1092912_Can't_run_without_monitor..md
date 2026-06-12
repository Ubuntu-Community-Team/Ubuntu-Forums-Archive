---
title: "Can't run without monitor."
date: 2009-03-10
forum: Hardware
---

### Post by tompouce on 2009-03-10
Hi!

I just installed the latest versio of ubuntu on my powermac. Everything is unning fine when my monitor is plugged in. But un fortunately I want to run it without any monitor attached so I have to make it run without it.

The problem is: it really boots perfectly with a monitor, But If I reboot without a monitor it does not work at all! No apache, no ssh, no vnc, etc...

So could you please help me?

Here's some logs:
```


X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.15-51-powerpc64-smp ppc Ubuntu
Current Operating System: Linux ubuntu 2.6.25-2-powerpc #1 Tue Sep 30 14:49:00 UTC 2008 ppc
Build Date: 24 October 2008  08:07:47AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@ross.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Mar 10 21:54:48 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(==) No screen section available. Using defaults.
(**) |-->Screen "Default Screen Section" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
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
(II) Open APM successful
(II) Loader magic: 0x101d55e0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 4.1
	X.Org XInput driver : 2.1
	X.Org Server Extension : 1.1
	X.Org Font Renderer : 0.6
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@0:16:0) nVidia Corporation NV17 [GeForce4 MX 440] rev 162, Mem @ 0x0f9f0374/0, 0x0f9f0374/0, 0x0f9f0374/0, BIOS @ 0x????????/262079348
(II) System resource ranges:
	[0] -1	2	0xffffffff - 0x00000000 (0xffffffff) MX[B]
	[1] -1	2	0xffffffff - 0x00000000 (0xf0000) MX[B]
	[2] -1	2	0xffffffff - 0x00000000 (0xc0000) MX[B]
	[3] -1	2	0xffffffff - 0x00000000 (0x0) MX[B]
	[4] -1	1	0xffffffff - 0x00000000 (0xffffffff) MX[B]
	[5] -1	1	0xffffffff - 0x00000000 (0xf0000) MX[B]
	[6] -1	1	0xffffffff - 0x00000000 (0xc0000) MX[B]
	[7] -1	1	0xffffffff - 0x00000000 (0x0) MX[B]
	[8] -1	0	0xffffffff - 0x00000000 (0xffffffff) MX[B]
	[9] -1	0	0xffffffff - 0x00000000 (0xf0000) MX[B]
	[10] -1	0	0xffffffff - 0x00000000 (0xc0000) MX[B]
	[11] -1	0	0xffffffff - 0x00000000 (0x0) MX[B]
	[12] -1	2	0xffffffff - 0x00000000 (0xffff) IX[B]
	[13] -1	2	0xffffffff - 0x00000000 (0x0) IX[B]
	[14] -1	1	0xffffffff - 0x00000000 (0xffff) IX[B]
	[15] -1	1	0xffffffff - 0x00000000 (0x0) IX[B]
	[16] -1	0	0xffffffff - 0x00000000 (0xffff) IX[B]
	[17] -1	0	0xffffffff - 0x00000000 (0x0) IX[B]
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
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(==) AIGLX enabled
(==) Exporting typical set of GLX visuals
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
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
(II) Matched nv from file name nv.ids
(==) Matched nv for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "nv"

(II) Loading /usr/lib/xorg/modules/drivers//nv_drv.so
(II) Module nv: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 2.1.10
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) NV: driver for NVIDIA chipsets: RIVA 128, RIVA TNT, RIVA TNT2,
	Unknown TNT2, Vanta, RIVA TNT2 Ultra, RIVA TNT2 Model 64,
	Aladdin TNT2, GeForce 256, GeForce DDR, Quadro, GeForce2 MX/MX 400,
	GeForce2 MX 100/200, GeForce2 Go, Quadro2 MXR/EX/Go,
	GeForce2 Integrated GPU, GeForce2 GTS, GeForce2 Ti, GeForce2 Ultra,
	Quadro2 Pro, GeForce4 MX 460, GeForce4 MX 440, GeForce4 MX 420,
	GeForce4 MX 440-SE, GeForce4 440 Go, GeForce4 420 Go,
	GeForce4 420 Go 32M, GeForce4 460 Go, Quadro4 550 XGL,
	GeForce4 MX (Mac), Quadro NVS, Quadro4 500 GoGL, GeForce4 410 Go 16M,
	GeForce4 MX 440 with AGP8X, GeForce4 MX 440SE with AGP8X,
	GeForce4 MX 420 with AGP8X, GeForce4 MX 4000, GeForce4 448 Go,
	GeForce4 488 Go, Quadro4 580 XGL, GeForce4 MX with AGP8X (Mac),
	Quadro4 NVS 280 SD, Quadro4 380 XGL, Quadro NVS 50 PCI,
	GeForce4 448 Go, GeForce4 MX Integrated GPU, GeForce3,
	GeForce3 Ti 200, GeForce3 Ti 500, Quadro DCC, GeForce4 Ti 4600,
	GeForce4 Ti 4400, GeForce4 Ti 4200, Quadro4 900 XGL, Quadro4 750 XGL,
	Quadro4 700 XGL, GeForce4 Ti 4800, GeForce4 Ti 4200 with AGP8X,
	GeForce4 Ti 4800 SE, GeForce4 4200 Go, Quadro4 700 GoGL,
	Quadro4 980 XGL, Quadro4 780 XGL, GeForce FX 5800 Ultra,
	GeForce FX 5800, Quadro FX 2000, Quadro FX 1000,
	GeForce FX 5600 Ultra, GeForce FX 5600, GeForce FX 5600XT,
	GeForce FX Go5600, GeForce FX Go5650, Quadro FX Go700,
	GeForce FX 5200, GeForce FX 5200 Ultra, GeForce FX 5200,
	GeForce FX 5200LE, GeForce FX Go5200, GeForce FX Go5250,
	GeForce FX 5500, GeForce FX 5100, GeForce FX Go5200 32M/64M,
	GeForce FX 5200 (Mac), Quadro NVS 55/280 PCI, Quadro FX 500/600 PCI,
	GeForce FX Go53xx Series, GeForce FX Go5100, GeForce FX 5900 Ultra,
	GeForce FX 5900, GeForce FX 5900XT, GeForce FX 5950 Ultra,
	GeForce FX 5900ZT, Quadro FX 3000, Quadro FX 700,
	GeForce FX 5700 Ultra, GeForce FX 5700, GeForce FX 5700LE,
	GeForce FX 5700VE, GeForce FX Go5700, GeForce FX Go5700,
	Quadro FX Go1000, Quadro FX 1100, GeForce 6800 Ultra, GeForce 6800,
	GeForce 6800 LE, GeForce 6800 XE, GeForce 6800 XT, GeForce 6800 GT,
	GeForce 6800 GT, GeForce 6800 GS, GeForce 6800 XT, Quadro FX 4000,
	GeForce 6800 GS, GeForce 6800, GeForce 6800 LE, GeForce 6800 XT,
	GeForce Go 6800, GeForce Go 6800 Ultra, Quadro FX Go1400,
	Quadro FX 3450/4000 SDI, Quadro FX 1400, GeForce 6600 GT,
	GeForce 6600, GeForce 6600 LE, GeForce 6600 VE, GeForce Go 6600,
	GeForce 6610 XL, GeForce Go 6600 TE/6200 TE, GeForce 6700 XL,
	GeForce Go 6600, GeForce Go 6600 GT, Quadro FX 550, Quadro FX 550,
	Quadro FX 540, GeForce 6200, GeForce 6500,
	GeForce 6200 TurboCache(TM), GeForce 6200SE TurboCache(TM),
	GeForce 6200 LE, GeForce Go 6200, Quadro NVS 285, GeForce Go 6400,
	GeForce Go 6200, GeForce Go 6400, GeForce 6250, GeForce 6800,
	GeForce 6800 LE, GeForce 6800 GT, GeForce 6800 XT, GeForce 6200,
	GeForce 6200 A-LE, GeForce 7800 GTX, GeForce 7800 GTX,
	GeForce 7800 GT, GeForce 7800 GS, GeForce 7800 SLI, GeForce Go 7800,
	GeForce Go 7800 GTX, Quadro FX 4500, GeForce 7300 LE,
	GeForce 7300 SE, GeForce Go 7200, GeForce Go 7300, GeForce Go 7400,
	GeForce Go 7400 GS, Quadro NVS 110M, Quadro NVS 120M, Quadro FX 350M,
	GeForce 7500 LE, Quadro FX 350, GeForce 7300 GS, GeForce 7600 GT,
	GeForce 7600 GS, GeForce 7300 GT, GeForce 7600 LE, GeForce 7300 GT,
	GeForce Go 7700, GeForce Go 7600, GeForce Go 7600 GT,
	Quadro NVS 300M, GeForce Go 7900 SE, Quadro FX 550M, Quadro FX 560,
	GeForce 7900 GTX, GeForce 7900 GT, GeForce 7900 GS,
	GeForce Go 7900 GS, GeForce Go 7900 GTX, Quadro FX 2500M,
	Quadro FX 1500M, Quadro FX 5500, Quadro FX 3500, Quadro FX 1500,
	Quadro FX 4500 X2, GeForce 6150, GeForce 6150 LE, GeForce 6100,
	GeForce Go 6150, GeForce Go 6100, GeForce 8800 GTX, GeForce 8800 GTS,
	GeForce 8800 Ultra, Quadro FX 5600, Quadro FX 4600, GeForce 8600 GTS,
	GeForce 8600 GT, GeForce 8600 GT, GeForce 8400 GS, GeForce 9500M GS,
	GeForce 8600M GT, GeForce 9650M GS, GeForce 8700M GT, Quadro FX 370,
	Quadro NVS 320M, Quadro FX 570M, Quadro FX 1600M, Quadro FX 570,
	Quadro FX 1700, GeForce 8400 SE, GeForce 8500 GT, GeForce 8400 GS,
	GeForce 8300 GS, GeForce 8400 GS, GeForce 8600M GS, GeForce 8400M GT,
	GeForce 8400M GS, GeForce 8400M G, Quadro NVS 140M, Quadro NVS 130M,
	Quadro NVS 135M, Quadro FX 360M, GeForce 9300M G, Quadro NVS 290,
	GeForce GTX 280, GeForce GTX 260, GeForce 8800 GTS 512,
	GeForce 8800 GT, GeForce 9800 GX2, GeForce 8800 GS,
	GeForce 8800M GTS, GeForce 8800M GTX, GeForce 8800 GS,
	GeForce 9600 GSO, GeForce 8800 GT, GeForce 9800 GTX, Quadro FX 3700,
	Quadro FX 3600M, GeForce 9600 GT, GeForce 9600M GT, GeForce 9600M GS,
	GeForce 9600M GT, GeForce 9500M G, GeForce 8400 GS, GeForce 9300M GS,
	GeForce 9200M GS, GeForce 9300M GS
(II) Primary Device is: PCI 00@00:10:0
(--) NV: Found NVIDIA GeForce4 MX 440 at 00@00:10:0
(II) resource ranges after probing:
	[0] -1	2	0xffffffff - 0x00000000 (0xffffffff) MX[B]
	[1] -1	2	0xffffffff - 0x00000000 (0xf0000) MX[B]
	[2] -1	2	0xffffffff - 0x00000000 (0xc0000) MX[B]
	[3] -1	2	0xffffffff - 0x00000000 (0x0) MX[B]
	[4] -1	1	0xffffffff - 0x00000000 (0xffffffff) MX[B]
	[5] -1	1	0xffffffff - 0x00000000 (0xf0000) MX[B]
	[6] -1	1	0xffffffff - 0x00000000 (0xc0000) MX[B]
	[7] -1	1	0xffffffff - 0x00000000 (0x0) MX[B]
	[8] -1	0	0xffffffff - 0x00000000 (0xffffffff) MX[B]
	[9] -1	0	0xffffffff - 0x00000000 (0xf0000) MX[B]
	[10] -1	0	0xffffffff - 0x00000000 (0xc0000) MX[B]
	[11] -1	0	0xffffffff - 0x00000000 (0x0) MX[B]
	[12] -1	2	0xffffffff - 0x00000000 (0xffff) IX[B]
	[13] -1	2	0xffffffff - 0x00000000 (0x0) IX[B]
	[14] -1	1	0xffffffff - 0x00000000 (0xffff) IX[B]
	[15] -1	1	0xffffffff - 0x00000000 (0x0) IX[B]
	[16] -1	0	0xffffffff - 0x00000000 (0xffff) IX[B]
	[17] -1	0	0xffffffff - 0x00000000 (0x0) IX[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 4.1
(--) NV(0): Chipset: "GeForce4 MX 440"
(II) NV(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
(==) NV(0): Depth 24, (==) framebuffer bpp 32
(==) NV(0): RGB weight 888
(==) NV(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"

(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 4.1
(==) NV(0): Using HW cursor
(--) NV(0): Linear framebuffer at 0x98000000
(--) NV(0): MMIO registers at 0x91000000
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) NV(0): I2C bus "DDC" initialized.
(II) NV(0): Probing for analog device on output A...
(--) NV(0):   ...can't find one
(II) NV(0): Probing for analog device on output B...
(--) NV(0):   ...found one
(II) NV(0): Probing for EDID on I2C bus A...
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(0): I2C device "DDC:ddc2" removed.
(II) NV(0):   ... none found
(II) NV(0): Probing for EDID on I2C bus B...
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(WW) EDID preferred timing clock 162.00MHz exceeds claimed max 160MHz, fixing
(--) NV(0): DDC detected a CRT:
(II) NV(0): Manufacturer: APP  Model: 9d02  Serial#: 16843009
(II) NV(0): Year: 1999  Week: 6
(II) NV(0): EDID Version: 1.1
(II) NV(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) NV(0): Sync:  Separate
(II) NV(0): Max Image Size [cm]: horiz.: 32  vert.: 24
(II) NV(0): Gamma: 1.40
(II) NV(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) NV(0): redX: 0.625 redY: 0.340   greenX: 0.290 greenY: 0.605
(II) NV(0): blueX: 0.150 blueY: 0.070   whiteX: 0.283 whiteY: 0.298
(II) NV(0): Supported VESA Video Modes:
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@67Hz
(II) NV(0): 800x600@60Hz
(II) NV(0): 832x624@75Hz
(II) NV(0): 1024x768@60Hz
(II) NV(0): 1024x768@75Hz
(II) NV(0): 1280x1024@75Hz
(II) NV(0): 1152x870@75Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported Future Video Modes:
(II) NV(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) NV(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) NV(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) NV(0): #3: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) NV(0): Supported additional Video Mode:
(II) NV(0): clock: 57.3 MHz   Image Size:  312 x 234 mm
(II) NV(0): h_active: 832  h_sync: 864  h_sync_end 928 h_blank_end 1152 h_border: 0
(II) NV(0): v_active: 624  v_sync: 626  v_sync_end 629 v_blanking: 667 v_border: 0
(II) NV(0): Supported additional Video Mode:
(II) NV(0): clock: 162.0 MHz   Image Size:  312 x 234 mm
(II) NV(0): h_active: 1600  h_sync: 1664  h_sync_end 1858 h_blank_end 2162 h_border: 0
(II) NV(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1250 v_border: 0
(II) NV(0): Ranges: V min: 48 V max: 160 Hz, H min: 30 H max: 85 kHz, PixClock max 162 MHz
(II) NV(0): Monitor name: StudioDsply17
(II) NV(0): EDID (in hex):
(II) NV(0): 	00ffffffffffff000610029d01010101
(II) NV(0): 	0609010168201828e80489a0574a9b26
(II) NV(0): 	12484c312b80315945596159a9400101
(II) NV(0): 	0101010101016016404031702b202040
(II) NV(0): 	230038ea10000018483f403262b03240
(II) NV(0): 	40c2130038ea10000018000000fd0030
(II) NV(0): 	a01e5510000a202020202020000000fc
(II) NV(0): 	0053747564696f4473706c793137001b
(--) NV(0): CRTC 1 appears to have a CRT attached
(II) NV(0): Using CRT on CRTC 1
(II) NV(0): EDID vendor "APP", prod id 40194
(II) NV(0): Using EDID range info for horizontal sync
(II) NV(0): Using EDID range info for vertical refresh
(II) NV(0): Printing DDC gathered Modelines:
(II) NV(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 626 629 667 -hsync -vsync (49.7 kHz)
(II) NV(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1858 2162  1200 1201 1204 1250 -hsync -vsync (74.9 kHz)
(II) NV(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NV(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) NV(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NV(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NV(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) NV(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NV(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) NV(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) NV(0): Modeline "640x480"x85.0   35.71  640 672 736 832  480 481 484 505 -hsync +vsync (42.9 kHz)
(II) NV(0): Modeline "800x600"x85.0   56.55  800 840 928 1056  600 601 604 630 -hsync +vsync (53.5 kHz)
(II) NV(0): Modeline "1024x768"x85.0   94.39  1024 1088 1200 1376  768 769 772 807 -hsync +vsync (68.6 kHz)
(II) NV(0): Modeline "1600x1200"x60.0  160.96  1600 1704 1880 2160  1200 1201 1204 1242 -hsync +vsync (74.5 kHz)
(--) NV(0): VideoRAM: 65536 kBytes
(==) NV(0): Using gamma correction (1.0, 1.0, 1.0)
(II) NV(0): <default monitor>: Using hsync range of 30.00-85.00 kHz
(II) NV(0): <default monitor>: Using vrefresh range of 48.00-160.00 Hz
(II) NV(0): <default monitor>: Using maximum pixel clock of 162.00 MHz
(II) NV(0): Estimated virtual size for aspect ratio 1.3333 is 1600x1200
(II) NV(0): Clock range:  12.00 to 350.00 MHz
(II) NV(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1280x960" (hsync out of range)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
(II) NV(0): Not using default mode "1280x1024" (hsync out of range)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (mode clock too high)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) NV(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) NV(0): Not using default mode "896x672" (hsync out of range)
(II) NV(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) NV(0): Not using default mode "928x696" (hsync out of range)
(II) NV(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) NV(0): Not using default mode "928x696" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "840x525" (hsync out of range)
(II) NV(0): Not using default mode "1920x1080" (width too large for virtual size)
(II) NV(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(--) NV(0): Virtual size is 1600x1200 (pitch 1600)
(**) NV(0): *Driver mode "1600x1200": 161.0 MHz, 74.5 kHz, 60.0 Hz
(II) NV(0): Modeline "1600x1200"x60.0  160.96  1600 1704 1880 2160  1200 1201 1204 1242 -hsync +vsync (74.5 kHz)
(**) NV(0): *Driver mode "1600x1200": 162.0 MHz, 74.9 kHz, 59.9 Hz
(II) NV(0): Modeline "1600x1200"x59.9  162.00  1600 1664 1858 2162  1200 1201 1204 1250 -hsync -vsync (74.9 kHz)
(**) NV(0): *Default mode "1600x1200": 162.0 MHz, 75.0 kHz, 60.0 Hz
(II) NV(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(**) NV(0): *Default mode "1400x1050": 155.8 MHz, 81.5 kHz, 74.8 Hz
(II) NV(0): Modeline "1400x1050"x74.8  155.80  1400 1464 1784 1912  1050 1052 1064 1090 +hsync +vsync (81.5 kHz)
(**) NV(0): *Default mode "1400x1050": 145.1 MHz, 76.5 kHz, 70.0 Hz
(II) NV(0): Modeline "1400x1050"x70.0  145.06  1400 1496 1648 1896  1050 1051 1054 1093 -hsync +vsync (76.5 kHz)
(**) NV(0): *Default mode "1400x1050": 122.0 MHz, 64.9 kHz, 60.0 Hz
(II) NV(0): Modeline "1400x1050"x60.0  122.00  1400 1488 1640 1880  1050 1052 1064 1082 +hsync +vsync (64.9 kHz)
(**) NV(0): *Driver mode "1280x1024": 135.0 MHz, 80.0 kHz, 75.0 Hz
(II) NV(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(**) NV(0): *Default mode "1280x1024": 135.0 MHz, 80.0 kHz, 75.0 Hz
(II) NV(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(**) NV(0): *Default mode "1280x1024": 108.0 MHz, 64.0 kHz, 60.0 Hz
(II) NV(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(**) NV(0): *Default mode "1440x900": 106.5 MHz, 55.9 kHz, 59.9 Hz
(II) NV(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(**) NV(0): *Default mode "1280x960": 108.0 MHz, 60.0 kHz, 60.0 Hz
(II) NV(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(**) NV(0): *Default mode "1360x768": 84.8 MHz, 47.7 kHz, 59.8 Hz
(II) NV(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(**) NV(0): *Driver mode "1152x864": 108.0 MHz, 67.5 kHz, 75.0 Hz
(II) NV(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(**) NV(0): *Default mode "1152x864": 121.5 MHz, 77.5 kHz, 85.1 Hz
(II) NV(0): Modeline "1152x864"x85.1  121.50  1152 1216 1344 1568  864 865 868 911 +hsync -vsync (77.5 kHz)
(**) NV(0): *Default mode "1152x864": 119.7 MHz, 77.1 kHz, 85.0 Hz
(II) NV(0): Modeline "1152x864"x85.0  119.65  1152 1224 1352 1552  864 865 868 907 -hsync +vsync (77.1 kHz)
(**) NV(0): *Default mode "1152x864": 108.0 MHz, 67.5 kHz, 75.0 Hz
(II) NV(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(**) NV(0): *Default mode "1152x864": 105.0 MHz, 67.6 kHz, 75.0 Hz
(II) NV(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.6 kHz)
(**) NV(0): *Default mode "1152x864": 96.8 MHz, 63.0 kHz, 70.0 Hz
(II) NV(0): Modeline "1152x864"x70.0   96.77  1152 1224 1344 1536  864 865 868 900 -hsync +vsync (63.0 kHz)
(**) NV(0): *Default mode "1152x864": 81.6 MHz, 53.7 kHz, 60.0 Hz
(II) NV(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(**) NV(0): *Driver mode "1024x768": 94.4 MHz, 68.6 kHz, 85.0 Hz
(II) NV(0): Modeline "1024x768"x85.0   94.39  1024 1088 1200 1376  768 769 772 807 -hsync +vsync (68.6 kHz)
(**) NV(0): *Driver mode "1024x768": 78.8 MHz, 60.1 kHz, 75.1 Hz
(II) NV(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(**) NV(0): *Driver mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) NV(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(**) NV(0): *Default mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
(II) NV(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(**) NV(0): *Default mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
(II) NV(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(**) NV(0): *Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(II) NV(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(**) NV(0): *Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) NV(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(**) NV(0): *Default mode "896x672": 102.4 MHz, 83.7 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "896x672"x60.0  102.40  896 960 1060 1224  672 672 674 697 doublescan -hsync +vsync (83.7 kHz)
(**) NV(0): *Driver mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(II) NV(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(**) NV(0): *Driver mode "832x624": 57.3 MHz, 49.7 kHz, 74.5 Hz
(II) NV(0): Modeline "832x624"x74.5   57.28  832 864 928 1152  624 626 629 667 -hsync -vsync (49.7 kHz)
(**) NV(0): *Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(II) NV(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(**) NV(0): *Driver mode "800x600": 56.5 MHz, 53.5 kHz, 85.0 Hz
(II) NV(0): Modeline "800x600"x85.0   56.55  800 840 928 1056  600 601 604 630 -hsync +vsync (53.5 kHz)
(**) NV(0): *Driver mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) NV(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) NV(0): *Default mode "800x600": 56.3 MHz, 53.7 kHz, 85.1 Hz
(II) NV(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(**) NV(0): *Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) NV(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(**) NV(0): *Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) NV(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(**) NV(0): *Default mode "800x600": 87.8 MHz, 81.2 kHz, 65.0 Hz (D)
(II) NV(0): Modeline "800x600"x65.0   87.75  800 832 928 1080  600 600 602 625 doublescan +hsync +vsync (81.2 kHz)
(**) NV(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) NV(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) NV(0): *Default mode "800x600": 81.0 MHz, 75.0 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "800x600"x60.0   81.00  800 832 928 1080  600 600 602 625 doublescan +hsync +vsync (75.0 kHz)
(**) NV(0): *Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) NV(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) NV(0): *Default mode "840x525": 93.5 MHz, 82.3 kHz, 75.0 Hz (D)
(II) NV(0): Modeline "840x525"x75.0   93.50  840 900 988 1136  525 526 529 549 doublescan -hsync +vsync (82.3 kHz)
(**) NV(0): *Default mode "840x525": 87.0 MHz, 76.6 kHz, 69.9 Hz (D)
(II) NV(0): Modeline "840x525"x69.9   87.00  840 900 988 1136  525 526 529 548 doublescan -hsync +vsync (76.6 kHz)
(**) NV(0): *Default mode "840x525": 73.1 MHz, 65.3 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "840x525"x60.0   73.12  840 892 980 1120  525 526 529 544 doublescan -hsync +vsync (65.3 kHz)
(**) NV(0): *Default mode "700x525": 77.9 MHz, 81.5 kHz, 74.8 Hz (D)
(II) NV(0): Modeline "700x525"x74.8   77.90  700 732 892 956  525 526 532 545 doublescan +hsync +vsync (81.5 kHz)
(**) NV(0): *Default mode "700x525": 72.5 MHz, 76.5 kHz, 70.1 Hz (D)
(II) NV(0): Modeline "700x525"x70.1   72.53  700 748 824 948  525 525 527 546 doublescan -hsync +vsync (76.5 kHz)
(**) NV(0): *Default mode "700x525": 61.0 MHz, 64.9 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "700x525"x60.0   61.00  700 744 820 940  525 526 532 541 doublescan +hsync +vsync (64.9 kHz)
(**) NV(0): *Default mode "640x512": 67.5 MHz, 80.0 kHz, 75.0 Hz (D)
(II) NV(0): Modeline "640x512"x75.0   67.50  640 648 720 844  512 512 514 533 doublescan +hsync +vsync (80.0 kHz)
(**) NV(0): *Default mode "640x512": 54.0 MHz, 64.0 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "640x512"x60.0   54.00  640 664 720 844  512 512 514 533 doublescan +hsync +vsync (64.0 kHz)
(**) NV(0): *Default mode "720x450": 53.2 MHz, 55.9 kHz, 59.9 Hz (D)
(II) NV(0): Modeline "720x450"x59.9   53.25  720 760 836 952  450 451 454 467 doublescan -hsync +vsync (55.9 kHz)
(**) NV(0): *Driver mode "640x480": 35.7 MHz, 42.9 kHz, 85.0 Hz
(II) NV(0): Modeline "640x480"x85.0   35.71  640 672 736 832  480 481 484 505 -hsync +vsync (42.9 kHz)
(**) NV(0): *Driver mode "640x480": 30.2 MHz, 35.0 kHz, 66.7 Hz
(II) NV(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(**) NV(0): *Driver mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(II) NV(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) NV(0): *Default mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
(II) NV(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(**) NV(0): *Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) NV(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(**) NV(0): *Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) NV(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(**) NV(0): *Default mode "640x480": 54.0 MHz, 60.0 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "640x480"x60.0   54.00  640 688 744 900  480 480 482 500 doublescan +hsync +vsync (60.0 kHz)
(**) NV(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) NV(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) NV(0): *Default mode "720x400": 35.5 MHz, 37.9 kHz, 85.0 Hz
(II) NV(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(**) NV(0): *Default mode "680x384": 36.0 MHz, 47.4 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "680x384"x60.0   36.00  680 704 720 760  384 385 390 395 doublescan +hsync -vsync (47.4 kHz)
(**) NV(0): *Default mode "680x384": 42.4 MHz, 47.7 kHz, 59.8 Hz (D)
(II) NV(0): Modeline "680x384"x59.8   42.38  680 716 784 888  384 385 390 399 doublescan -hsync +vsync (47.7 kHz)
(**) NV(0): *Default mode "640x400": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) NV(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(**) NV(0): *Default mode "576x432": 60.8 MHz, 77.5 kHz, 85.2 Hz (D)
(II) NV(0): Modeline "576x432"x85.2   60.75  576 608 672 784  432 432 434 455 doublescan +hsync -vsync (77.5 kHz)
(**) NV(0): *Default mode "576x432": 59.8 MHz, 77.1 kHz, 85.1 Hz (D)
(II) NV(0): Modeline "576x432"x85.1   59.83  576 612 676 776  432 432 434 453 doublescan -hsync +vsync (77.1 kHz)
(**) NV(0): *Default mode "576x432": 54.0 MHz, 67.5 kHz, 75.0 Hz (D)
(II) NV(0): Modeline "576x432"x75.0   54.00  576 608 672 800  432 432 434 450 doublescan +hsync +vsync (67.5 kHz)
(**) NV(0): *Default mode "576x432": 52.5 MHz, 67.6 kHz, 75.0 Hz (D)
(II) NV(0): Modeline "576x432"x75.0   52.49  576 612 676 776  432 432 434 451 doublescan -hsync +vsync (67.6 kHz)
(**) NV(0): *Default mode "576x432": 48.4 MHz, 63.0 kHz, 70.0 Hz (D)
(II) NV(0): Modeline "576x432"x70.0   48.38  576 612 672 768  432 432 434 450 doublescan -hsync +vsync (63.0 kHz)
(**) NV(0): *Default mode "576x432": 40.8 MHz, 53.7 kHz, 60.1 Hz (D)
(II) NV(0): Modeline "576x432"x60.1   40.81  576 608 668 760  432 432 434 447 doublescan -hsync +vsync (53.7 kHz)
(**) NV(0): *Default mode "640x350": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) NV(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(**) NV(0): *Default mode "512x384": 47.2 MHz, 68.7 kHz, 85.0 Hz (D)
(II) NV(0): Modeline "512x384"x85.0   47.25  512 536 584 688  384 384 386 404 doublescan +hsync +vsync (68.7 kHz)
(**) NV(0): *Default mode "512x384": 39.4 MHz, 60.0 kHz, 75.0 Hz (D)
(II) NV(0): Modeline "512x384"x75.0   39.38  512 520 568 656  384 384 386 400 doublescan +hsync +vsync (60.0 kHz)
(**) NV(0): *Default mode "512x384": 37.5 MHz, 56.5 kHz, 70.1 Hz (D)
(II) NV(0): Modeline "512x384"x70.1   37.50  512 524 592 664  384 385 388 403 doublescan -hsync -vsync (56.5 kHz)
(**) NV(0): *Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "512x384"x60.0   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync (48.4 kHz)
(**) NV(0): *Default mode "416x312": 28.6 MHz, 49.7 kHz, 74.7 Hz (D)
(II) NV(0): Modeline "416x312"x74.7   28.64  416 432 464 576  312 312 314 333 doublescan -hsync -vsync (49.7 kHz)
(**) NV(0): *Default mode "400x300": 28.1 MHz, 53.7 kHz, 85.3 Hz (D)
(II) NV(0): Modeline "400x300"x85.3   28.15  400 416 448 524  300 300 302 315 doublescan +hsync +vsync (53.7 kHz)
(**) NV(0): *Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (D)
(II) NV(0): Modeline "400x300"x75.1   24.75  400 408 448 528  300 300 302 312 doublescan +hsync +vsync (46.9 kHz)
(**) NV(0): *Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
(II) NV(0): Modeline "400x300"x72.2   25.00  400 428 488 520  300 318 321 333 doublescan +hsync +vsync (48.1 kHz)
(**) NV(0): *Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) NV(0): Modeline "400x300"x60.3   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz)
(**) NV(0): *Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(II) NV(0): Modeline "400x300"x56.3   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (35.2 kHz)
(**) NV(0): *Default mode "320x240": 18.0 MHz, 43.3 kHz, 85.2 Hz (D)
(II) NV(0): Modeline "320x240"x85.2   18.00  320 348 376 416  240 240 242 254 doublescan -hsync -vsync (43.3 kHz)
(**) NV(0): *Default mode "320x240": 15.8 MHz, 37.5 kHz, 75.0 Hz (D)
(II) NV(0): Modeline "320x240"x75.0   15.75  320 328 360 420  240 240 242 250 doublescan -hsync -vsync (37.5 kHz)
(**) NV(0): *Default mode "320x240": 15.8 MHz, 37.9 kHz, 72.8 Hz (D)
(II) NV(0): Modeline "320x240"x72.8   15.75  320 332 352 416  240 244 246 260 doublescan -hsync -vsync (37.9 kHz)
(**) NV(0): *Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) NV(0): Modeline "320x240"x60.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz)
(**) NV(0): *Default mode "360x200": 17.8 MHz, 37.9 kHz, 85.0 Hz (D)
(II) NV(0): Modeline "360x200"x85.0   17.75  360 378 414 468  200 200 202 223 doublescan -hsync +vsync (37.9 kHz)
(**) NV(0): *Default mode "320x200": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(II) NV(0): Modeline "320x200"x85.3   15.75  320 336 368 416  200 200 202 222 doublescan -hsync +vsync (37.9 kHz)
(**) NV(0): *Default mode "320x175": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(II) NV(0): Modeline "320x175"x85.3   15.75  320 336 368 416  175 191 192 222 doublescan +hsync -vsync (37.9 kHz)
(**) NV(0): Display dimensions: (320, 240) mm
(**) NV(0): DPI set to (127, 127)
(II) Loading sub module "fb"
(II) LoadModule: "fb"

(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"

(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.2.0
	ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	2	0xffffffff - 0x00000000 (0xffffffff) MX[B]
	[1] -1	2	0xffffffff - 0x00000000 (0xf0000) MX[B]
	[2] -1	2	0xffffffff - 0x00000000 (0xc0000) MX[B]
	[3] -1	2	0xffffffff - 0x00000000 (0x0) MX[B]
	[4] -1	1	0xffffffff - 0x00000000 (0xffffffff) MX[B]
	[5] -1	1	0xffffffff - 0x00000000 (0xf0000) MX[B]
	[6] -1	1	0xffffffff - 0x00000000 (0xc0000) MX[B]
	[7] -1	1	0xffffffff - 0x00000000 (0x0) MX[B]
	[8] -1	0	0xffffffff - 0x00000000 (0xffffffff) MX[B]
	[9] -1	0	0xffffffff - 0x00000000 (0xf0000) MX[B]
	[10] -1	0	0xffffffff - 0x00000000 (0xc0000) MX[B]
	[11] -1	0	0xffffffff - 0x00000000 (0x0) MX[B]
	[12] -1	2	0xffffffff - 0x00000000 (0xffff) IX[B]
	[13] -1	2	0xffffffff - 0x00000000 (0x0) IX[B]
	[14] -1	1	0xffffffff - 0x00000000 (0xffff) IX[B]
	[15] -1	1	0xffffffff - 0x00000000 (0x0) IX[B]
	[16] -1	0	0xffffffff - 0x00000000 (0xffff) IX[B]
	[17] -1	0	0xffffffff - 0x00000000 (0x0) IX[B]
(II) NV(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Scanline Image Writes
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(==) NV(0): Backing store disabled
(==) NV(0): Silken mouse enabled
(II) NV(0): DPMS enabled
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
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(II) config/hal: Adding input device Mouseemu virtual mouse
(II) LoadModule: "evdev"

(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 2.0.99
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(**) Mouseemu virtual mouse: always reports core events
(**) Mouseemu virtual mouse: Device: "/dev/input/event3"
(II) Mouseemu virtual mouse: Found x and y relative axes
(II) Mouseemu virtual mouse: Found 3 mouse buttons
(II) Mouseemu virtual mouse: Configuring as mouse
(II) XINPUT: Adding extended input device "Mouseemu virtual mouse" (type: MOUSE)
(**) Mouseemu virtual mouse: YAxisMapping: buttons 4 and 5
(**) Mouseemu virtual mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device Mouseemu virtual keyboard
(**) Mouseemu virtual keyboard: always reports core events
(**) Mouseemu virtual keyboard: Device: "/dev/input/event2"
(II) Mouseemu virtual keyboard: Found keys
(II) Mouseemu virtual keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "Mouseemu virtual keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Mouseemu virtual keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Mouseemu virtual keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Mouseemu virtual keyboard: xkb_layout: "us"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
(EE) Grab failed. Device already configured?
(II) UnloadModule: "evdev"
(EE) PreInit returned NULL for "Macintosh mouse button emulation"
(EE) config/hal: NewInputDeviceRequest failed
(II) Mouseemu virtual mouse: Close
(II) UnloadModule: "evdev"
(II) Mouseemu virtual keyboard: Close
(II) UnloadModule: "evdev"

```

syslog
```
Mar 10 19:07:52 ubuntu syslogd 1.5.0#2ubuntu6: restart.
Mar 10 19:07:52 ubuntu kernel: Inspecting /boot/System.map-2.6.25-2-powerpc
Mar 10 19:07:53 ubuntu kernel: Loaded 25934 symbols from /boot/System.map-2.6.25-2-powerpc.
Mar 10 19:07:53 ubuntu kernel: Symbols match kernel version 2.6.25.
Mar 10 19:07:53 ubuntu kernel: Loaded 9812 symbols from 50 modules.
Mar 10 19:07:53 ubuntu kernel: [    0.000000] Crash kernel location must be 0x2000000
Mar 10 19:07:53 ubuntu kernel: [    0.000000] Reserving 0MB of memory at 32MB for crashkernel (System RAM: 1024MB)
Mar 10 19:07:53 ubuntu kernel: [    0.000000] Using PowerMac machine description
Mar 10 19:07:53 ubuntu kernel: [    0.000000] Total memory = 1024MB; using 2048kB for hash table (at cfe00000)
Mar 10 19:07:53 ubuntu kernel: [    0.000000] Linux version 2.6.25-2-powerpc (buildd@adare) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu8) ) #1 Tue Sep 30 14:49:00 UTC 2008
Mar 10 19:07:53 ubuntu kernel: [    0.000000] Found initrd at 0xc1a00000:0xc2262000
Mar 10 19:07:53 ubuntu kernel: [    0.000000] Found UniNorth memory controller & host bridge @ 0xf8000000 revision: 0x11
Mar 10 19:07:53 ubuntu kernel: [    0.000000] Mapped at 0xfdfc0000
Mar 10 19:07:53 ubuntu kernel: [    0.000000] Found a Keylargo mac-io controller, rev: 3, mapped at 0xfdf40000
Mar 10 19:07:53 ubuntu kernel: [    0.000000] Processor NAP mode on idle enabled.
Mar 10 19:07:53 ubuntu kernel: [    0.000000] PowerMac motherboard: PowerMac G4 Silver
Mar 10 19:07:53 ubuntu kernel: [    0.000000] console [udbg0] enabled
Mar 10 19:07:53 ubuntu kernel: [    0.000000] Entering add_active_range(0, 0, 262144) 0 entries of 256 used
Mar 10 19:07:53 ubuntu kernel: [    0.000000] Found UniNorth PCI host bridge at 0x00000000f0000000. Firmware bus number: 0->0
Mar 10 19:07:53 ubuntu kernel: [    0.000000] PCI host bridge /pci@f0000000  ranges:
Mar 10 19:07:53 ubuntu kernel: [    0.000000]  MEM 0x00000000f1000000..0x00000000f1ffffff -> 0x00000000f1000000 
Mar 10 19:07:53 ubuntu kernel: [    0.000000]   IO 0x00000000f0000000..0x00000000f07fffff -> 0x0000000000000000
Mar 10 19:07:53 ubuntu kernel: [    0.000000]  MEM 0x0000000090000000..0x00000000afffffff -> 0x0000000090000000 
Mar 10 19:07:53 ubuntu kernel: [    0.000000] Found UniNorth PCI host bridge at 0x00000000f2000000. Firmware bus number: 0->0
Mar 10 19:07:53 ubuntu kernel: [    0.000000] PCI host bridge /pci@f2000000 (primary) ranges:
Mar 10 19:07:53 ubuntu kernel: [    0.000000]  MEM 0x00000000f3000000..0x00000000f3ffffff -> 0x00000000f3000000 
Mar 10 19:07:53 ubuntu kernel: [    0.000000]   IO 0x00000000f2000000..0x00000000f27fffff -> 0x0000000000000000
Mar 10 19:07:53 ubuntu kernel: [    0.000000]  MEM 0x0000000080000000..0x000000008fffffff -> 0x0000000080000000 
Mar 10 19:07:53 ubuntu kernel: [    0.000000] Found UniNorth PCI host bridge at 0x00000000f4000000. Firmware bus number: 0->0
Mar 10 19:07:53 ubuntu kernel: [    0.000000] PCI host bridge /pci@f4000000  ranges:
Mar 10 19:07:53 ubuntu kernel: [    0.000000]  MEM 0x00000000f5000000..0x00000000f5ffffff -> 0x00000000f5000000 
Mar 10 19:07:53 ubuntu kernel: [    0.000000]   IO 0x00000000f4000000..0x00000000f47fffff -> 0x0000000000000000
Mar 10 19:07:53 ubuntu kernel: [    0.000000] via-pmu: Server Mode is disabled
Mar 10 19:07:53 ubuntu kernel: [    0.000000] PMU driver v2 initialized for Core99, firmware: 0c
Mar 10 19:07:53 ubuntu kernel: [    0.000000] nvram: Checking bank 0...
Mar 10 19:07:53 ubuntu kernel: [    0.000000] nvram: gen0=800, gen1=801
Mar 10 19:07:53 ubuntu kernel: [    0.000000] nvram: Active bank is: 1
Mar 10 19:07:53 ubuntu kernel: [    0.000000] nvram: OF partition at 0x410
Mar 10 19:07:53 ubuntu kernel: [    0.000000] nvram: XP partition at 0xffffffff
Mar 10 19:07:53 ubuntu kernel: [    0.000000] nvram: NR partition at 0xffffffff
Mar 10 19:07:53 ubuntu kernel: [    0.000000] Top of RAM: 0x40000000, Total RAM: 0x40000000
Mar 10 19:07:53 ubuntu kernel: [    0.000000] Memory hole size: 0MB
Mar 10 19:07:53 ubuntu kernel: [    0.000000] Zone PFN ranges:
Mar 10 19:07:53 ubuntu kernel: [    0.000000]   DMA             0 ->   196608
Mar 10 19:07:53 ubuntu kernel: [    0.000000]   Normal     196608 ->   196608
Mar 10 19:07:53 ubuntu kernel: [    0.000000]   HighMem    196608 ->   262144
Mar 10 19:07:53 ubuntu kernel: [    0.000000] Movable zone start PFN for each node
Mar 10 19:07:53 ubuntu kernel: [    0.000000] early_node_map[1] active PFN ranges
Mar 10 19:07:53 ubuntu kernel: [    0.000000]     0:        0 ->   262144
Mar 10 19:07:53 ubuntu kernel: [    0.000000] On node 0 totalpages: 262144
Mar 10 19:07:53 ubuntu kernel: [    0.000000]   DMA zone: 1536 pages used for memmap
Mar 10 19:07:53 ubuntu kernel: [    0.000000]   DMA zone: 0 pages reserved
Mar 10 19:07:53 ubuntu kernel: [    0.000000]   DMA zone: 195072 pages, LIFO batch:31
Mar 10 19:07:53 ubuntu kernel: [    0.000000]   Normal zone: 0 pages used for memmap
Mar 10 19:07:53 ubuntu kernel: [    0.000000]   HighMem zone: 512 pages used for memmap
Mar 10 19:07:53 ubuntu kernel: [    0.000000]   HighMem zone: 65024 pages, LIFO batch:15
Mar 10 19:07:53 ubuntu kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Mar 10 19:07:53 ubuntu kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 260096
Mar 10 19:07:53 ubuntu kernel: [    0.000000] Kernel command line: root=/dev/hda3 ro quiet splash 
Mar 10 19:07:53 ubuntu kernel: [    0.000000] mpic: Setting up MPIC " MPIC 1   " version 1.2 at 80040000, max 4 CPUs
Mar 10 19:07:53 ubuntu kernel: [    0.000000] mpic: ISU size: 64, shift: 6, mask: 3f
Mar 10 19:07:53 ubuntu kernel: [    0.000000] mpic: Initializing for 64 sources
Mar 10 19:07:53 ubuntu kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Mar 10 19:07:53 ubuntu kernel: [    0.000000] GMT Delta read from XPRAM: 0 minutes, DST: on
Mar 10 19:07:53 ubuntu kernel: [    0.000000] time_init: decrementer frequency = 33.217183 MHz
Mar 10 19:07:53 ubuntu kernel: [    0.000000] time_init: processor frequency   = 933.333331 MHz
Mar 10 19:07:53 ubuntu kernel: [    0.000006] clocksource: timebase mult[786b6b2] shift[22] registered
Mar 10 19:07:53 ubuntu kernel: [    0.000014] clockevent: decrementer mult[880] shift[16] cpu[0]
Mar 10 19:07:53 ubuntu kernel: [    0.000095] Console: colour dummy device 80x25
Mar 10 19:07:53 ubuntu kernel: [    0.000102] console handover: boot [udbg0] -> real [tty0]
Mar 10 19:07:53 ubuntu kernel: [    0.000967] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Mar 10 19:07:53 ubuntu kernel: [    0.001997] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Mar 10 19:07:53 ubuntu kernel: [    0.074796] High memory: 262144k
Mar 10 19:07:53 ubuntu kernel: [    0.074805] Memory: 1023568k/1048576k available (3688k kernel code, 24236k reserved, 132k data, 357k bss, 212k init)
Mar 10 19:07:53 ubuntu kernel: [    0.074898] SLUB: Genslabs=12, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
Mar 10 19:07:53 ubuntu kernel: [    0.074904] Calibrating delay loop... 66.30 BogoMIPS (lpj=132608)
Mar 10 19:07:53 ubuntu kernel: [    0.160064] Security Framework initialized
Mar 10 19:07:53 ubuntu kernel: [    0.160086] SELinux:  Disabled at boot.
Mar 10 19:07:53 ubuntu kernel: [    0.160096] Capability LSM initialized
Mar 10 19:07:53 ubuntu kernel: [    0.160109] Mount-cache hash table entries: 512
Mar 10 19:07:53 ubuntu kernel: [    0.160498] device-tree: Duplicate name in /cpus/PowerPC,G4@0/l2-cache, renamed to "l2-cache#1"
Mar 10 19:07:53 ubuntu kernel: [    0.160536] device-tree: Duplicate name in /cpus/PowerPC,G4@0, renamed to "l2-cache#1"
Mar 10 19:07:53 ubuntu kernel: [    0.161869] Initializing cgroup subsys ns
Mar 10 19:07:53 ubuntu kernel: [    0.162442] net_namespace: 540 bytes
Mar 10 19:07:53 ubuntu kernel: [    0.162816] NET: Registered protocol family 16
Mar 10 19:07:53 ubuntu kernel: [    0.163597] KeyWest i2c @0xf8001003 irq 42 /uni-n@f8000000/i2c@f8001000
Mar 10 19:07:53 ubuntu kernel: [    0.163605]  channel 0 bus <multibus>
Mar 10 19:07:53 ubuntu kernel: [    0.163609]  channel 1 bus <multibus>
Mar 10 19:07:53 ubuntu kernel: [    0.163631] KeyWest i2c @0x80018000 irq 26 /pci@f2000000/mac-io@17/i2c@18000
Mar 10 19:07:53 ubuntu kernel: [    0.163637]  channel 0 bus <multibus>
Mar 10 19:07:53 ubuntu kernel: [    0.163648] PMU i2c /pci@f2000000/mac-io@17/via-pmu@16000
Mar 10 19:07:53 ubuntu kernel: [    0.163652]  channel 1 bus <multibus>
Mar 10 19:07:53 ubuntu kernel: [    0.163656]  channel 2 bus <multibus>
Mar 10 19:07:53 ubuntu kernel: [    0.163715] PCI: Probing PCI hardware
Mar 10 19:07:53 ubuntu kernel: [    0.180099] NET: Registered protocol family 8
Mar 10 19:07:53 ubuntu kernel: [    0.180106] NET: Registered protocol family 20
Mar 10 19:07:53 ubuntu kernel: [    0.180890] NET: Registered protocol family 2
Mar 10 19:07:53 ubuntu kernel: [    0.184016] Switched to high resolution mode on CPU 0
Mar 10 19:07:53 ubuntu kernel: [    0.216088] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Mar 10 19:07:53 ubuntu kernel: [    0.216621] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Mar 10 19:07:53 ubuntu kernel: [    0.218416] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
Mar 10 19:07:53 ubuntu kernel: [    0.218876] TCP: Hash tables configured (established 131072 bind 65536)
Mar 10 19:07:53 ubuntu kernel: [    0.218882] TCP reno registered
Mar 10 19:07:53 ubuntu kernel: [    0.228326] checking if image is initramfs... it is
Mar 10 19:07:53 ubuntu kernel: [    1.542796] Freeing initrd memory: 6144k freed
Mar 10 19:07:53 ubuntu kernel: [    1.543528] Freeing initrd memory: 2436k freed
Mar 10 19:07:53 ubuntu kernel: [    1.543843] Thermal assist unit not available
Mar 10 19:07:53 ubuntu kernel: [    1.543958] setup_kcore: restrict size=3fffffff
Mar 10 19:07:53 ubuntu kernel: [    1.544837] audit: initializing netlink socket (disabled)
Mar 10 19:07:53 ubuntu kernel: [    1.544875] type=2000 audit(1236726440.544:1): initialized
Mar 10 19:07:53 ubuntu kernel: [    1.545153] highmem bounce pool size: 64 pages
Mar 10 19:07:53 ubuntu kernel: [    1.549140] VFS: Disk quotas dquot_6.5.1
Mar 10 19:07:53 ubuntu kernel: [    1.549198] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Mar 10 19:07:53 ubuntu kernel: [    1.549577] io scheduler noop registered
Mar 10 19:07:53 ubuntu kernel: [    1.549583] io scheduler anticipatory registered
Mar 10 19:07:53 ubuntu kernel: [    1.549587] io scheduler deadline registered
Mar 10 19:07:53 ubuntu kernel: [    1.549612] io scheduler cfq registered (default)
Mar 10 19:07:53 ubuntu kernel: [    1.549633] pci 0000:00:10.0: nv_msi_ht_cap_quirk didn't locate host bridge
Mar 10 19:07:53 ubuntu kernel: [    1.550729] Using unsupported 1024x768 NVDA,Display-B at 98004000, depth=8, pitch=1024
Mar 10 19:07:53 ubuntu kernel: [    1.563534] Console: switching to colour frame buffer device 128x48
Mar 10 19:07:53 ubuntu kernel: [    1.575820] fb0: Open Firmware frame buffer device on /pci@f0000000/NVDA,Parent@10/NVDA,Display-B@1
Mar 10 19:07:53 ubuntu kernel: [    1.620081] Generic RTC Driver v1.07
Mar 10 19:07:53 ubuntu kernel: [    1.620165] Macintosh non-volatile memory driver v1.1
Mar 10 19:07:53 ubuntu kernel: [    1.621351] brd: module loaded
Mar 10 19:07:53 ubuntu kernel: [    1.621441] MacIO PCI driver attached to Keylargo chipset
Mar 10 19:07:53 ubuntu kernel: [    1.623183] input: Macintosh mouse button emulation as /class/input/input0
Mar 10 19:07:53 ubuntu kernel: [    1.623614] Uniform Multi-Platform E-IDE driver
Mar 10 19:07:53 ubuntu kernel: [    1.623621] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Mar 10 19:07:53 ubuntu kernel: [    1.623714] adb: starting probe task...
Mar 10 19:07:53 ubuntu kernel: [    1.623724] adb: finished probe task...
Mar 10 19:07:53 ubuntu kernel: [    1.652010] ide0: Found Apple KeyLargo ATA-4 controller, bus ID 2, irq 19
Mar 10 19:07:53 ubuntu kernel: [    1.652029] Probing IDE interface ide0...
Mar 10 19:07:53 ubuntu kernel: [    1.684308] hda: ST360021A, ATA DISK drive
Mar 10 19:07:53 ubuntu kernel: [    1.712301] hdb: WDC WD2500JB-00GVC0, ATA DISK drive
Mar 10 19:07:53 ubuntu kernel: [    1.716035] hda: host max PIO4 wanted PIO255(auto-tune) selected PIO4
Mar 10 19:07:53 ubuntu kernel: [    1.716163] hda: UDMA/66 mode selected
Mar 10 19:07:53 ubuntu kernel: [    1.716242] hdb: host max PIO4 wanted PIO255(auto-tune) selected PIO4
Mar 10 19:07:53 ubuntu kernel: [    1.717476] hdb: UDMA/66 mode selected
Mar 10 19:07:53 ubuntu kernel: [    1.718769] ide0 at 0xf1014000-0xf1014007,0xf1014160 on irq 19
Mar 10 19:07:53 ubuntu kernel: [    1.756008] ide1: Found Apple KeyLargo ATA-3 controller, bus ID 0, irq 20
Mar 10 19:07:53 ubuntu kernel: [    1.756023] Probing IDE interface ide1...
Mar 10 19:07:53 ubuntu kernel: [    1.796179] hdc: PIONEER DVD-RW DVR-104, ATAPI CD/DVD-ROM drive
Mar 10 19:07:53 ubuntu kernel: [    1.864000] hdc: host max PIO4 wanted PIO255(auto-tune) selected PIO4
Mar 10 19:07:53 ubuntu kernel: [    1.864000] hdc: MWDMA2 mode selected
Mar 10 19:07:53 ubuntu kernel: [    1.864000] ide1 at 0xf1016000-0xf1016007,0xf1016160 on irq 20
Mar 10 19:07:53 ubuntu kernel: [    1.900008] ide2: Found Apple KeyLargo ATA-3 controller, bus ID 1, irq 21
Mar 10 19:07:53 ubuntu kernel: [    1.900022] Probing IDE interface ide2...
Mar 10 19:07:53 ubuntu kernel: [    1.968126] mice: PS/2 mouse device common for all mice
Mar 10 19:07:53 ubuntu kernel: [    1.968285] PowerMac i2c bus pmu 2 registered
Mar 10 19:07:53 ubuntu kernel: [    1.968358] PowerMac i2c bus pmu 1 registered
Mar 10 19:07:53 ubuntu kernel: [    1.968428] PowerMac i2c bus mac-io 0 registered
Mar 10 19:07:53 ubuntu kernel: [    1.968498] PowerMac i2c bus uni-n 1 registered
Mar 10 19:07:53 ubuntu kernel: [    1.968570] PowerMac i2c bus uni-n 0 registered
Mar 10 19:07:53 ubuntu kernel: [    1.969463] NET: Registered protocol family 1
Mar 10 19:07:53 ubuntu kernel: [    1.969735] registered taskstats version 1
Mar 10 19:07:53 ubuntu kernel: [    1.969995] input: PMU as /class/input/input1
Mar 10 19:07:53 ubuntu kernel: [    1.980046] Freeing unused kernel memory: 212k init
Mar 10 19:07:53 ubuntu kernel: [    2.359825] fuse init (API version 7.9)
Mar 10 19:07:53 ubuntu kernel: [    4.655747] usbcore: registered new interface driver usbfs
Mar 10 19:07:53 ubuntu kernel: [    4.655796] usbcore: registered new interface driver hub
Mar 10 19:07:53 ubuntu kernel: [    4.667084] sungem.c:v0.98 8/24/03 David S. Miller (davem@redhat.com)
Mar 10 19:07:53 ubuntu kernel: [    4.688151] usbcore: registered new device driver usb
Mar 10 19:07:53 ubuntu kernel: [    4.691202] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
Mar 10 19:07:53 ubuntu kernel: [    4.691269] PCI: Enabling device 0001:10:18.0 (0000 -> 0002)
Mar 10 19:07:53 ubuntu kernel: [    4.691285] ohci_hcd 0001:10:18.0: OHCI Host Controller
Mar 10 19:07:53 ubuntu kernel: [    4.691575] ohci_hcd 0001:10:18.0: new USB bus registered, assigned bus number 1
Mar 10 19:07:53 ubuntu kernel: [    4.691614] ohci_hcd 0001:10:18.0: irq 27, io mem 0x80081000
Mar 10 19:07:53 ubuntu kernel: [    4.764155] usb usb1: configuration #1 chosen from 1 choice
Mar 10 19:07:53 ubuntu kernel: [    4.764206] hub 1-0:1.0: USB hub found
Mar 10 19:07:53 ubuntu kernel: [    4.764227] hub 1-0:1.0: 2 ports detected
Mar 10 19:07:53 ubuntu kernel: [    4.824404] PHY ID: 206071, addr: 0
Mar 10 19:07:53 ubuntu kernel: [    5.344682] PCI: Enabling device 0001:10:19.0 (0000 -> 0002)
Mar 10 19:07:53 ubuntu kernel: [    5.344704] ohci_hcd 0001:10:19.0: OHCI Host Controller
Mar 10 19:07:53 ubuntu kernel: [    5.344760] ohci_hcd 0001:10:19.0: new USB bus registered, assigned bus number 2
Mar 10 19:07:53 ubuntu kernel: [    5.344800] ohci_hcd 0001:10:19.0: irq 28, io mem 0x80080000
Mar 10 19:07:53 ubuntu kernel: [    5.420154] usb usb2: configuration #1 chosen from 1 choice
Mar 10 19:07:53 ubuntu kernel: [    5.420204] hub 2-0:1.0: USB hub found
Mar 10 19:07:53 ubuntu kernel: [    5.420227] hub 2-0:1.0: 2 ports detected
Mar 10 19:07:53 ubuntu kernel: [    5.656044] usb 1-1: new low speed USB device using ohci_hcd and address 2
Mar 10 19:07:53 ubuntu kernel: [    5.843573] hda: max request size: 128KiB
Mar 10 19:07:53 ubuntu kernel: [    5.861071] hda: 120103200 sectors (61492 MB) w/2048KiB Cache, CHS=65535/16/63
Mar 10 19:07:53 ubuntu kernel: [    5.861081] hda: cache flushes not supported
Mar 10 19:07:53 ubuntu kernel: [    5.861170]  hda: [mac] hda1 hda2 hda3 hda4
Mar 10 19:07:53 ubuntu kernel: [    5.884615] hdb: max request size: 512KiB
Mar 10 19:07:53 ubuntu kernel: [    5.886197] usb 1-1: configuration #1 chosen from 1 choice
Mar 10 19:07:53 ubuntu kernel: [    5.893839] hdb: 488397168 sectors (250059 MB) w/8192KiB Cache, CHS=30401/255/63
Mar 10 19:07:53 ubuntu kernel: [    5.895785] hdb: cache flushes supported
Mar 10 19:07:53 ubuntu kernel: [    5.895851]  hdb: hdb1
Mar 10 19:07:53 ubuntu kernel: [    6.010947] eth0: Sun GEM (PCI) 10/100/1000BaseT Ethernet 00:03:93:77:9d:26
Mar 10 19:07:53 ubuntu kernel: [    6.010955] eth0: Found BCM5411 PHY
Mar 10 19:07:53 ubuntu kernel: [    6.013045] hdc: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2000kB Cache
Mar 10 19:07:53 ubuntu kernel: [    6.013056] Uniform CD-ROM driver Revision: 3.20
Mar 10 19:07:53 ubuntu kernel: [    6.065009] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[40]  MMIO=[f5000000-f50007ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
Mar 10 19:07:53 ubuntu kernel: [    6.236043] usb 2-1: new low speed USB device using ohci_hcd and address 2
Mar 10 19:07:53 ubuntu kernel: [    6.441217] usb 2-1: configuration #1 chosen from 1 choice
Mar 10 19:07:53 ubuntu kernel: [    6.443313] usbcore: registered new interface driver hiddev
Mar 10 19:07:53 ubuntu kernel: [    6.455690] input:   USB Keyboard as /class/input/input2
Mar 10 19:07:53 ubuntu kernel: [    6.468083] input,hidraw0: USB HID v1.10 Keyboard [  USB Keyboard] on usb-0001:10:18.0-1
Mar 10 19:07:53 ubuntu kernel: [    6.490170] input:   USB Keyboard as /class/input/input3
Mar 10 19:07:53 ubuntu kernel: [    6.500436] input,hidraw1: USB HID v1.10 Device [  USB Keyboard] on usb-0001:10:18.0-1
Mar 10 19:07:53 ubuntu kernel: [    6.504635] input: USB Mouse as /class/input/input4
Mar 10 19:07:53 ubuntu kernel: [    6.508123] input,hidraw2: USB HID v1.10 Mouse [USB Mouse] on usb-0001:10:19.0-1
Mar 10 19:07:53 ubuntu kernel: [    6.508158] usbcore: registered new interface driver usbhid
Mar 10 19:07:53 ubuntu kernel: [    6.508166] /build/buildd/linux-ports-2.6.25/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Mar 10 19:07:53 ubuntu kernel: [    6.712128] PM: Starting manual resume from disk
Mar 10 19:07:53 ubuntu kernel: [    6.774669] kjournald starting.  Commit interval 5 seconds
Mar 10 19:07:53 ubuntu kernel: [    6.774695] EXT3-fs: mounted filesystem with ordered data mode.
Mar 10 19:07:53 ubuntu kernel: [    7.092345] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000393fffe779d26]
Mar 10 19:07:53 ubuntu kernel: [    7.368221] eth0: Link is up at 1000 Mbps, full-duplex.
Mar 10 19:07:53 ubuntu kernel: [   11.145818] udevd version 124 started
Mar 10 19:07:53 ubuntu kernel: [   17.204072] Linux agpgart interface v0.103
Mar 10 19:07:53 ubuntu kernel: [   17.219763] agpgart: Detected Apple UniNorth 1.5 chipset
Mar 10 19:07:53 ubuntu kernel: [   17.219896] agpgart: configuring for size idx: 8
Mar 10 19:07:53 ubuntu kernel: [   17.224909] agpgart: AGP aperture is 32M @ 0x0
Mar 10 19:07:53 ubuntu kernel: [   21.134967] pmac_zilog: 0.6 (Benjamin Herrenschmidt <benh@kernel.crashing.org>)
Mar 10 19:07:53 ubuntu kernel: [   21.135027] pmac_zilog: i2c-modem detected, id: 1
Mar 10 19:07:53 ubuntu kernel: [   21.135079] ttyPZ0 at MMIO 0x80013020 (irq = 22) is a Z85c30 ESCC - Internal modem
Mar 10 19:07:53 ubuntu kernel: [   21.135330] ttyPZ1 at MMIO 0x80013000 (irq = 29) is a Z85c30 ESCC - Serial port
Mar 10 19:07:53 ubuntu kernel: [   22.969575] apm_emu: PMU APM Emulation initialized.
Mar 10 19:07:53 ubuntu kernel: [   23.026492] loop: module loaded
Mar 10 19:07:53 ubuntu kernel: [   23.126317] SCSI subsystem initialized
Mar 10 19:07:53 ubuntu kernel: [   23.594114] Adding 2497848k swap on /dev/hda4.  Priority:-1 extents:1 across:2497848k
Mar 10 19:07:53 ubuntu kernel: [   23.966109] EXT3 FS on hda3, internal journal
Mar 10 19:07:53 ubuntu kernel: [   25.085966] ip_tables: (C) 2000-2006 Netfilter Core Team
Mar 10 19:07:53 ubuntu kernel: [   25.169243] eth0: Link is up at 1000 Mbps, full-duplex.
Mar 10 19:07:53 ubuntu kernel: [   25.169255] eth0: Pause is enabled (rxfifo: 10240 off: 7168 on: 5632)
Mar 10 19:07:53 ubuntu pbbuttonsd: WARNING: No backlight driver available - check your Kernel configuration. 
Mar 10 19:07:54 ubuntu kernel: [   27.833609] NET: Registered protocol family 10
Mar 10 19:07:54 ubuntu kernel: [   27.835113] lo: Disabled Privacy Extensions
Mar 10 19:07:54 ubuntu pbbuttonsd: ERROR: Can't attach card 'default': No such file or directory 
Mar 10 19:07:54 ubuntu pbbuttonsd: INFO: Soundsystem requested: ALSA and at least activated: none. 
Mar 10 19:07:54 ubuntu pbbuttonsd: INFO: saving of config enabled to /etc/pbbuttonsd.conf. 
Mar 10 19:07:54 ubuntu pbbuttonsd: INFO: pbbuttonsd 0.7.9: Unknown PowerBook - PMU version: 12 
Mar 10 19:07:54 ubuntu avahi-daemon[3792]: Found user 'avahi' (UID 107) and group 'avahi' (GID 115).
Mar 10 19:07:54 ubuntu avahi-daemon[3792]: Successfully dropped root privileges.
Mar 10 19:07:54 ubuntu avahi-daemon[3792]: avahi-daemon 0.6.23 starting up.
Mar 10 19:07:54 ubuntu kernel: [   28.169283] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
Mar 10 19:07:54 ubuntu anacron[3795]: Anacron 2.3 started on 2009-03-10
Mar 10 19:07:54 ubuntu avahi-daemon[3792]: Successfully called chroot().
Mar 10 19:07:54 ubuntu avahi-daemon[3792]: Successfully dropped remaining capabilities.
Mar 10 19:07:54 ubuntu avahi-daemon[3792]: No service file found in /etc/avahi/services.
Mar 10 19:07:54 ubuntu avahi-daemon[3792]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.2.
Mar 10 19:07:54 ubuntu avahi-daemon[3792]: New relevant interface eth0.IPv4 for mDNS.
Mar 10 19:07:54 ubuntu avahi-daemon[3792]: Network interface enumeration completed.
Mar 10 19:07:54 ubuntu avahi-daemon[3792]: Registering new address record for fe80::203:93ff:fe77:9d26 on eth0.*.
Mar 10 19:07:54 ubuntu avahi-daemon[3792]: Registering new address record for 192.168.0.2 on eth0.IPv4.
Mar 10 19:07:54 ubuntu avahi-daemon[3792]: Registering HINFO record with values 'PPC'/'LINUX'.
Mar 10 19:07:54 ubuntu anacron[3795]: Will run job `cron.daily' in 5 min.
Mar 10 19:07:54 ubuntu anacron[3795]: Will run job `cron.weekly' in 10 min.
Mar 10 19:07:54 ubuntu anacron[3795]: Will run job `cron.monthly' in 15 min.
Mar 10 19:07:54 ubuntu anacron[3795]: Jobs will be executed sequentially
Mar 10 19:07:55 ubuntu kernel: [   28.399720] hda: host max PIO4 wanted PIO0 selected PIO0
Mar 10 19:07:55 ubuntu kernel: [   29.026769] lp: driver loaded but no devices found
Mar 10 19:07:55 ubuntu avahi-daemon[3792]: Server startup complete. Host name is ubuntu.local. Local service cookie is 1023433996.
Mar 10 19:07:55 ubuntu kernel: [   29.262706] ppdev: user-space parallel port driver
Mar 10 19:07:55 ubuntu kernel: [   29.284005] hda: task_no_data_intr: status=0x51 { DriveReady SeekComplete Error }
Mar 10 19:07:55 ubuntu kernel: [   29.284005] hda: task_no_data_intr: error=0x04 { DriveStatusError }
Mar 10 19:07:55 ubuntu kernel: [   29.284005] ide: failed opcode was: 0xef
Mar 10 19:07:55 ubuntu kernel: [   29.316543] hdb: task_no_data_intr: status=0x51 { DriveReady SeekComplete Error }
Mar 10 19:07:55 ubuntu kernel: [   29.316557] hdb: task_no_data_intr: error=0x04 { DriveStatusError }
Mar 10 19:07:55 ubuntu kernel: [   29.316564] ide: failed opcode was: 0xef
Mar 10 19:07:56 ubuntu pbbuttonsd: INFO: Script '/etc/power/pmcs-pbbuttonsd performance ac ' launched and exited normally 
Mar 10 19:07:56 ubuntu mouseemu[3942]: mouseemu 0.15 (C) Colin Leroy <colin@colino.net> 
Mar 10 19:07:56 ubuntu mouseemu[3942]: using (0+87) as middle button, (0+88) as right button, (0) as scroll. 
Mar 10 19:07:58 ubuntu mouseemu[3944]: Trying to open /dev/uinput...
Mar 10 19:07:58 ubuntu mouseemu[3944]:  error. 
Mar 10 19:07:58 ubuntu mouseemu[3944]: Trying to open /dev/uinput...
Mar 10 19:07:58 ubuntu mouseemu[3944]:  error. 
Mar 10 19:07:58 ubuntu mouseemu[3944]: Trying to open /dev/input/uinput...
Mar 10 19:07:58 ubuntu mouseemu[3944]:  ok. 
Mar 10 19:07:58 ubuntu kernel: [   31.173412] input: Mouseemu virtual keyboard as /class/input/input5
Mar 10 19:07:58 ubuntu mouseemu[3944]: Trying to open /dev/uinput...
Mar 10 19:07:58 ubuntu mouseemu[3944]:  error. 
Mar 10 19:07:58 ubuntu mouseemu[3944]: Trying to open /dev/uinput...
Mar 10 19:07:58 ubuntu mouseemu[3944]:  error. 
Mar 10 19:07:58 ubuntu mouseemu[3944]: Trying to open /dev/input/uinput...
Mar 10 19:07:58 ubuntu mouseemu[3944]:  ok. 
Mar 10 19:07:58 ubuntu kernel: [   31.204858] input: Mouseemu virtual mouse as /class/input/input6
Mar 10 19:07:59 ubuntu bluetoothd[4157]: Bluetooth daemon
Mar 10 19:07:59 ubuntu kernel: [   32.619408] Bluetooth: Core ver 2.11
Mar 10 19:07:59 ubuntu kernel: [   32.620318] NET: Registered protocol family 31
Mar 10 19:07:59 ubuntu kernel: [   32.620324] Bluetooth: HCI device and connection manager initialized
Mar 10 19:07:59 ubuntu kernel: [   32.620331] Bluetooth: HCI socket layer initialized
Mar 10 19:07:59 ubuntu bluetoothd[4157]: Starting SDP server
Mar 10 19:07:59 ubuntu kernel: [   32.695528] Bluetooth: L2CAP ver 2.9
Mar 10 19:07:59 ubuntu kernel: [   32.695538] Bluetooth: L2CAP socket layer initialized
Mar 10 19:07:59 ubuntu kernel: [   32.737167] Bluetooth: RFCOMM socket layer initialized
Mar 10 19:07:59 ubuntu kernel: [   32.738012] Bluetooth: RFCOMM TTY layer initialized
Mar 10 19:07:59 ubuntu kernel: [   32.738020] Bluetooth: RFCOMM ver 1.8
Mar 10 19:07:59 ubuntu kernel: [   32.780593] Bluetooth: SCO (Voice Link) ver 0.5
Mar 10 19:07:59 ubuntu kernel: [   32.780605] Bluetooth: SCO socket layer initialized
Mar 10 19:07:59 ubuntu bluetoothd[4157]: Starting experimental netlink support
Mar 10 19:07:59 ubuntu bluetoothd[4157]: Failed to find Bluetooth netlink family
Mar 10 19:07:59 ubuntu bluetoothd[4157]: Can't init plugin /usr/lib/bluetooth/plugins/netlink.so
Mar 10 19:07:59 ubuntu kernel: [   32.839930] Bluetooth: BNEP (Ethernet Emulation) ver 1.2
Mar 10 19:07:59 ubuntu kernel: [   32.839944] Bluetooth: BNEP filters: protocol multicast
Mar 10 19:07:59 ubuntu kernel: [   32.913792] Bridge firewalling registered
Mar 10 19:07:59 ubuntu bluetoothd[4157]: bridge pan0 created
Mar 10 19:07:59 ubuntu kernel: [   32.914832] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
Mar 10 19:08:00 ubuntu NetworkManager: <info>  starting... 
Mar 10 19:08:00 ubuntu NetworkManager: <info>  eth0: driver is 'gem'. 
Mar 10 19:08:00 ubuntu NetworkManager: <info>  Found new Ethernet device 'eth0'. 
Mar 10 19:08:00 ubuntu NetworkManager: <info>  (eth0): exported as /org/freedesktop/Hal/devices/net_00_03_93_77_9d_26 
Mar 10 19:08:00 ubuntu NetworkManager: <info>  Trying to start the supplicant... 
Mar 10 19:08:00 ubuntu NetworkManager: <info>  Trying to start the system settings daemon... 
Mar 10 19:08:00 ubuntu NetworkManager: <info>  (eth0): carrier now ON (device state 1) 
Mar 10 19:08:00 ubuntu nm-system-settings:    SCPlugin-Ifupdown: init!
Mar 10 19:08:00 ubuntu nm-system-settings:    SCPlugin-Ifupdown: update_system_hostname
Mar 10 19:08:00 ubuntu nm-system-settings:    SCPluginIfupdown: guessed connection type (eth0) = 802-3-ethernet
Mar 10 19:08:01 ubuntu nm-system-settings:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:eth0, type:802-3-ethernet, autoconnect:0, id:Ifupdown (eth0), uuid: 681b428f-0000-0000-0000-000000000039
Mar 10 19:08:01 ubuntu nm-system-settings:    SCPlugin-Ifupdown: addresses count: 1
Mar 10 19:08:01 ubuntu nm-system-settings:    SCPlugin-Ifupdown: autoconnect
Mar 10 19:08:01 ubuntu nm-system-settings:    SCPluginIfupdown: management mode: unmanaged
Mar 10 19:08:01 ubuntu nm-system-settings:    SCPlugin-Ifupdown: devices added (udi: /org/freedesktop/Hal/devices/net_00_03_93_77_9d_26, iface: eth0)
Mar 10 19:08:01 ubuntu nm-system-settings:    Ifupdown: get unmanaged devices count: 1
Mar 10 19:08:01 ubuntu nm-system-settings:    SCPlugin-Ifupdown: (268626672) ... get_connections.
Mar 10 19:08:01 ubuntu nm-system-settings:    SCPlugin-Ifupdown: (268626672) connections count: 1
Mar 10 19:08:01 ubuntu nm-system-settings:    Ifupdown: get unmanaged devices count: 1
Mar 10 19:08:01 ubuntu nm-system-settings:    SCPlugin-Ifupdown: end _init.
Mar 10 19:08:01 ubuntu nm-system-settings: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Mar 10 19:08:01 ubuntu nm-system-settings: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Mar 10 19:08:01 ubuntu NetworkManager: <info>  (eth0): now unmanaged 
Mar 10 19:08:01 ubuntu /usr/sbin/cron[4312]: (CRON) INFO (pidfile fd = 3)
Mar 10 19:08:01 ubuntu /usr/sbin/cron[4313]: (CRON) STARTUP (fork ok)
Mar 10 19:08:01 ubuntu /usr/sbin/cron[4313]: (CRON) INFO (Running @reboot jobs)
Mar 10 19:08:04 ubuntu kernel: [   36.756017] eth0: no IPv6 routers present
Mar 10 19:08:06 ubuntu gdmgreeter[4369]: Gtk-WARNING: Unable to locate theme engine in module_path: "ubuntulooks", 
Mar 10 19:10:07 ubuntu pulseaudio[4476]: ltdl-bind-now.c: Failed to find original dlopen loader.
Mar 10 19:10:07 ubuntu pulseaudio[4478]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Mar 10 19:10:07 ubuntu pulseaudio[4478]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Mar 10 19:10:10 ubuntu x-session-manager[4396]: WARNING: Unable to find provider 'gnome-wm' of required component 'windowmanager' 
Mar 10 19:10:22 ubuntu x-session-manager[4396]: WARNING: Application 'libcanberra-login-sound.desktop' failed to register before timeout 
Mar 10 19:10:22 ubuntu pulseaudio[4478]: module-x11-xsmp.c: X11 session manager not running.
Mar 10 19:10:22 ubuntu pulseaudio[4478]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Mar 10 19:10:24 ubuntu NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
Mar 10 19:10:24 ubuntu NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
Mar 10 19:12:54 ubuntu anacron[3795]: Job `cron.daily' started
Mar 10 19:12:54 ubuntu anacron[4748]: Updated timestamp for job `cron.daily' to 2009-03-10
Mar 10 19:13:05 ubuntu gdmsetup[4730]: Gtk-WARNING: GtkSpinButton: setting an adjustment with non-zero page size is deprecated 
Mar 10 19:13:05 ubuntu last message repeated 6 times
Mar 10 19:13:54 ubuntu last message repeated 2 times
Mar 10 19:17:02 ubuntu /USR/SBIN/CRON[4815]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar 10 19:20:54 ubuntu bluetoothd[4157]: bridge pan0 removed
Mar 10 19:20:54 ubuntu bluetoothd[4157]: Stopping SDP server
Mar 10 19:20:54 ubuntu bluetoothd[4157]: Exit
Mar 10 19:20:56 ubuntu bluetoothd[7237]: Bluetooth daemon
Mar 10 19:20:56 ubuntu bluetoothd[7237]: Starting SDP server
Mar 10 19:20:56 ubuntu bluetoothd[7237]: Starting experimental netlink support
Mar 10 19:20:56 ubuntu bluetoothd[7237]: Failed to find Bluetooth netlink family
Mar 10 19:20:56 ubuntu bluetoothd[7237]: Can't init plugin /usr/lib/bluetooth/plugins/netlink.so
Mar 10 19:20:56 ubuntu kernel: [  478.883629] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
Mar 10 19:20:56 ubuntu bluetoothd[7237]: bridge pan0 created
Mar 10 19:20:57 ubuntu bluetoothd[7237]: bridge pan0 removed
Mar 10 19:20:57 ubuntu bluetoothd[7237]: Stopping SDP server
Mar 10 19:20:57 ubuntu bluetoothd[7237]: Exit
Mar 10 19:21:14 ubuntu pbbuttonsd: WARNING: No backlight driver available - check your Kernel configuration. 
Mar 10 19:21:14 ubuntu pbbuttonsd: ERROR: Can't attach card 'default': No such file or directory 
Mar 10 19:21:14 ubuntu pbbuttonsd: INFO: Soundsystem requested: ALSA and at least activated: none. 
Mar 10 19:21:14 ubuntu pbbuttonsd: INFO: saving of config enabled to /etc/pbbuttonsd.conf. 
Mar 10 19:21:14 ubuntu pbbuttonsd: INFO: pbbuttonsd 0.7.9: Unknown PowerBook - PMU version: 12 
Mar 10 19:23:23 ubuntu avahi-daemon[3792]: Files changed, reloading.
Mar 10 19:23:23 ubuntu avahi-daemon[3792]: No service file found in /etc/avahi/services.
Mar 10 19:23:24 ubuntu avahi-daemon[3792]: Got SIGTERM, quitting.
Mar 10 19:23:24 ubuntu avahi-daemon[3792]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.0.2.
Mar 10 19:29:11 ubuntu NetworkManager: <info>  HAL disappeared 
Mar 10 19:29:14 ubuntu NetworkManager: <info>  HAL re-appeared 
Mar 10 19:30:33 ubuntu avahi-daemon[16903]: Found user 'avahi' (UID 107) and group 'avahi' (GID 115).
Mar 10 19:30:33 ubuntu avahi-daemon[16903]: Successfully dropped root privileges.
Mar 10 19:30:33 ubuntu avahi-daemon[16903]: avahi-daemon 0.6.23 starting up.
Mar 10 19:30:33 ubuntu avahi-daemon[16903]: Successfully called chroot().
Mar 10 19:30:33 ubuntu avahi-daemon[16903]: Successfully dropped remaining capabilities.
Mar 10 19:30:33 ubuntu avahi-daemon[16903]: No service file found in /etc/avahi/services.
Mar 10 19:30:33 ubuntu avahi-daemon[16903]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.2.
Mar 10 19:30:33 ubuntu avahi-daemon[16903]: New relevant interface eth0.IPv4 for mDNS.
Mar 10 19:30:33 ubuntu avahi-daemon[16903]: Network interface enumeration completed.
Mar 10 19:30:33 ubuntu avahi-daemon[16903]: Registering new address record for fe80::203:93ff:fe77:9d26 on eth0.*.
Mar 10 19:30:33 ubuntu avahi-daemon[16903]: Registering new address record for 192.168.0.2 on eth0.IPv4.
Mar 10 19:30:33 ubuntu avahi-daemon[16903]: Registering HINFO record with values 'PPC'/'LINUX'.
Mar 10 19:30:34 ubuntu avahi-daemon[16903]: Server startup complete. Host name is ubuntu.local. Local service cookie is 3478354852.
```

Thanks a lot for your help!!!

---

### Post by irieken on 2009-04-22
This is a known issue with Macs; they don't boot without a monitor plugged in. If your computer has a DVI port, this may be the solution you need: a 100ohm resistor connecting vsync and analog ground.

Directions and a picture: [http://blackfriarsinc.com/blog/2007/04/how-to-keep-headless-mac-mini-happy](http://blackfriarsinc.com/blog/2007/04/how-to-keep-headless-mac-mini-happy)

---

