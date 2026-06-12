---
title: "Mercury motherboard drivers for ubuntu Mint 14"
date: 2013-10-12
forum: Hardware
---

### Post by wheelchairman on 2013-10-12
After installing found the resolution to be just 600 x 480.
The mother board is mercury PI945Z.
Please help restore max resolution for the monitor SAMSUNG SyncMaster943NWX.

---

### Post by Yellow Pasque on 2013-10-12
Please post/pastebin the /var/log/Xorg.0.log file (use [ code ][ /code ] tags).

---

### Post by wheelchairman on 2013-10-12
```
[    16.766] 
X.Org X Server 1.13.0
Release Date: 2012-09-05
[    16.766] X Protocol Version 11, Revision 0
[    16.766] Build Operating System: Linux 3.2.0-26-generic i686 Ubuntu
[    16.766] Current Operating System: Linux jayakumar-desktop 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:32:08 UTC 2012 i686
[    16.766] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-17-generic root=UUID=3c37acdf-3df3-483a-a9d3-34f171edfebd ro quiet splash vt.handoff=7
[    16.766] Build Date: 08 October 2012  03:34:08PM
[    16.766] xorg-server 2:1.13.0-0ubuntu6 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    16.766] Current version of pixman: 0.26.0
[    16.766] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[    16.766] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    16.766] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Oct 13 07:52:47 2013
[    16.779] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    16.780] (==) No Layout section.  Using the first Screen section.
[    16.780] (==) No screen section available. Using defaults.
[    16.780] (**) |-->Screen "Default Screen Section" (0)
[    16.780] (**) |   |-->Monitor "<default monitor>"
[    16.780] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    16.780] (==) Automatically adding devices
[    16.780] (==) Automatically enabling devices
[    16.780] (==) Automatically adding GPU devices
[    16.780] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    16.780] 	Entry deleted from font path.
[    16.780] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    16.780] 	Entry deleted from font path.
[    16.780] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    16.780] 	Entry deleted from font path.
[    16.780] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    16.780] 	Entry deleted from font path.
[    16.780] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    16.780] 	Entry deleted from font path.
[    16.780] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    16.780] 	Entry deleted from font path.
[    16.780] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    16.780] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    16.780] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    16.780] (II) Loader magic: 0xb773e640
[    16.780] (II) Module ABI versions:
[    16.780] 	X.Org ANSI C Emulation: 0.4
[    16.780] 	X.Org Video Driver: 13.0
[    16.780] 	X.Org XInput driver : 18.0
[    16.780] 	X.Org Server Extension : 7.0
[    16.781] (--) PCI:*(0:0:2:0) 8086:2772:8086:2772 rev 2, Mem @ 0xfdf00000/524288, 0xd0000000/268435456, 0xfdf80000/262144, I/O @ 0x0000ff00/8
[    16.781] (II) Open ACPI successful (/var/run/acpid.socket)
[    16.781] Initializing built-in extension Generic Event Extension
[    16.782] Initializing built-in extension SHAPE
[    16.782] Initializing built-in extension MIT-SHM
[    16.782] Initializing built-in extension XInputExtension
[    16.782] Initializing built-in extension XTEST
[    16.782] Initializing built-in extension BIG-REQUESTS
[    16.782] Initializing built-in extension SYNC
[    16.782] Initializing built-in extension XKEYBOARD
[    16.782] Initializing built-in extension XC-MISC
[    16.782] Initializing built-in extension SECURITY
[    16.782] Initializing built-in extension XINERAMA
[    16.782] Initializing built-in extension XFIXES
[    16.782] Initializing built-in extension RENDER
[    16.782] Initializing built-in extension RANDR
[    16.782] Initializing built-in extension COMPOSITE
[    16.782] Initializing built-in extension DAMAGE
[    16.782] Initializing built-in extension MIT-SCREEN-SAVER
[    16.782] Initializing built-in extension DOUBLE-BUFFER
[    16.782] Initializing built-in extension RECORD
[    16.782] Initializing built-in extension DPMS
[    16.782] Initializing built-in extension X-Resource
[    16.782] Initializing built-in extension XVideo
[    16.782] Initializing built-in extension XVideo-MotionCompensation
[    16.782] Initializing built-in extension XFree86-VidModeExtension
[    16.782] Initializing built-in extension XFree86-DGA
[    16.782] Initializing built-in extension XFree86-DRI
[    16.782] Initializing built-in extension DRI2
[    16.782] (II) LoadModule: "glx"
[    16.855] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    16.855] (II) Module glx: vendor="X.Org Foundation"
[    16.855] 	compiled for 1.13.0, module version = 1.0.0
[    16.855] 	ABI class: X.Org Server Extension, version 7.0
[    16.855] (==) AIGLX enabled
[    16.855] Loading extension GLX
[    16.855] (==) Matched intel as autoconfigured driver 0
[    16.855] (==) Matched vesa as autoconfigured driver 1
[    16.855] (==) Matched modesetting as autoconfigured driver 2
[    16.855] (==) Matched fbdev as autoconfigured driver 3
[    16.855] (==) Assigned the driver to the xf86ConfigLayout
[    16.855] (II) LoadModule: "intel"
[    16.856] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    16.856] (II) Module intel: vendor="X.Org Foundation"
[    16.856] 	compiled for 1.13.0, module version = 2.20.9
[    16.856] 	Module class: X.Org Video Driver
[    16.856] 	ABI class: X.Org Video Driver, version 13.0
[    16.856] (II) LoadModule: "vesa"
[    16.856] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    16.856] (II) Module vesa: vendor="X.Org Foundation"
[    16.856] 	compiled for 1.12.99.902, module version = 2.3.2
[    16.857] 	Module class: X.Org Video Driver
[    16.857] 	ABI class: X.Org Video Driver, version 13.0
[    16.857] (II) LoadModule: "modesetting"
[    16.857] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    16.857] (II) Module modesetting: vendor="X.Org Foundation"
[    16.857] 	compiled for 1.13.0, module version = 0.5.0
[    16.857] 	Module class: X.Org Video Driver
[    16.857] 	ABI class: X.Org Video Driver, version 13.0
[    16.857] (II) LoadModule: "fbdev"
[    16.857] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    16.857] (II) Module fbdev: vendor="X.Org Foundation"
[    16.857] 	compiled for 1.12.99.902, module version = 0.4.3
[    16.857] 	Module class: X.Org Video Driver
[    16.857] 	ABI class: X.Org Video Driver, version 13.0
[    16.857] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
	Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
	Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
	Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
	Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server,
	Ivybridge Server (GT2), Haswell Desktop (GT1), Haswell Desktop (GT2),
	Haswell Desktop (GT2+), Haswell Mobile (GT1), Haswell Mobile (GT2),
	Haswell Mobile (GT2+), Haswell Server (GT1), Haswell Server (GT2),
	Haswell Server (GT2+), Haswell SDV Desktop (GT1),
	Haswell SDV Desktop (GT2), Haswell SDV Desktop (GT2+),
	Haswell SDV Mobile (GT1), Haswell SDV Mobile (GT2),
	Haswell SDV Mobile (GT2+), Haswell SDV Server (GT1),
	Haswell SDV Server (GT2), Haswell SDV Server (GT2+),
	Haswell ULT Desktop (GT1), Haswell ULT Desktop (GT2),
	Haswell ULT Desktop (GT2+), Haswell ULT Mobile (GT1),
	Haswell ULT Mobile (GT2), Haswell ULT Mobile (GT2+),
	Haswell ULT Server (GT1), Haswell ULT Server (GT2),
	Haswell ULT Server (GT2+), Haswell CRW Desktop (GT1),
	Haswell CRW Desktop (GT2), Haswell CRW Desktop (GT2+),
	Haswell CRW Mobile (GT1), Haswell CRW Mobile (GT2),
	Haswell CRW Mobile (GT2+), Haswell CRW Server (GT1),
	Haswell CRW Server (GT2), Haswell CRW Server (GT2+),
	ValleyView PO board
[    16.858] (II) VESA: driver for VESA chipsets: vesa
[    16.858] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    16.858] (II) FBDEV: driver for framebuffer: fbdev
[    16.858] (++) using VT number 7

[    16.864] (WW) Falling back to old probe method for modesetting
[    16.864] (EE) open /dev/dri/card0: No such file or directory
[    16.864] (WW) Falling back to old probe method for fbdev
[    16.864] (II) Loading sub module "fbdevhw"
[    16.864] (II) LoadModule: "fbdevhw"
[    16.865] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    16.865] (II) Module fbdevhw: vendor="X.Org Foundation"
[    16.865] 	compiled for 1.13.0, module version = 0.0.2
[    16.865] 	ABI class: X.Org Video Driver, version 13.0
[    16.865] (II) Loading sub module "vbe"
[    16.865] (II) LoadModule: "vbe"
[    16.865] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    16.865] (II) Module vbe: vendor="X.Org Foundation"
[    16.865] 	compiled for 1.13.0, module version = 1.1.0
[    16.865] 	ABI class: X.Org Video Driver, version 13.0
[    16.865] (II) Loading sub module "int10"
[    16.865] (II) LoadModule: "int10"
[    16.865] (II) Loading /usr/lib/xorg/modules/libint10.so
[    16.865] (II) Module int10: vendor="X.Org Foundation"
[    16.865] 	compiled for 1.13.0, module version = 1.0.0
[    16.865] 	ABI class: X.Org Video Driver, version 13.0
[    16.865] (II) VESA(0): initializing int10
[    16.871] (II) VESA(0): Bad V_BIOS checksum
[    16.871] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    16.872] (II) VESA(0): VESA BIOS detected
[    16.872] (II) VESA(0): VESA VBE Version 3.0
[    16.872] (II) VESA(0): VESA VBE Total Mem: 7872 kB
[    16.872] (II) VESA(0): VESA VBE OEM: Intel(r) 82945G Chipset Family Graphics Chip Accelerated VGA BIOS
[    16.872] (II) VESA(0): VESA VBE OEM Software Rev: 1.0
[    16.872] (II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
[    16.872] (II) VESA(0): VESA VBE OEM Product: Intel(r) 82945G Chipset Family Graphics Controller
[    16.872] (II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
[    16.917] (II) VESA(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    16.917] (==) VESA(0): Depth 24, (--) framebuffer bpp 32
[    16.917] (==) VESA(0): RGB weight 888
[    16.917] (==) VESA(0): Default visual is TrueColor
[    16.917] (==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
[    16.917] (II) Loading sub module "ddc"
[    16.917] (II) LoadModule: "ddc"
[    16.917] (II) Module "ddc" already built-in
[    16.918] (II) VESA(0): VESA VBE DDC supported
[    16.918] (II) VESA(0): VESA VBE DDC Level 2
[    16.918] (II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
[    16.931] (II) VESA(0): VESA VBE DDC read successfully
[    16.931] (II) VESA(0): Manufacturer: SAM  Model: 36f  Serial#: 1297690937
[    16.931] (II) VESA(0): Year: 2008  Week: 34
[    16.931] (II) VESA(0): EDID Version: 1.3
[    16.931] (II) VESA(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[    16.931] (II) VESA(0): Sync:  Separate  Composite  SyncOnGreen
[    16.931] (II) VESA(0): Max Image Size [cm]: horiz.: 41  vert.: 26
[    16.931] (II) VESA(0): Gamma: 2.20
[    16.931] (II) VESA(0): DPMS capabilities: Off; RGB/Color Display
[    16.931] (II) VESA(0): First detailed timing is preferred mode
[    16.931] (II) VESA(0): redX: 0.650 redY: 0.340   greenX: 0.285 greenY: 0.605
[    16.931] (II) VESA(0): blueX: 0.140 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
[    16.931] (II) VESA(0): Supported established timings:
[    16.931] (II) VESA(0): 720x400@70Hz
[    16.931] (II) VESA(0): 640x480@60Hz
[    16.931] (II) VESA(0): 640x480@67Hz
[    16.931] (II) VESA(0): 640x480@72Hz
[    16.931] (II) VESA(0): 640x480@75Hz
[    16.931] (II) VESA(0): 800x600@56Hz
[    16.931] (II) VESA(0): 800x600@60Hz
[    16.931] (II) VESA(0): 800x600@72Hz
[    16.931] (II) VESA(0): 800x600@75Hz
[    16.931] (II) VESA(0): 832x624@75Hz
[    16.931] (II) VESA(0): 1024x768@60Hz
[    16.931] (II) VESA(0): 1024x768@70Hz
[    16.931] (II) VESA(0): 1024x768@75Hz
[    16.932] (II) VESA(0): 1280x1024@75Hz
[    16.932] (II) VESA(0): 1152x864@75Hz
[    16.932] (II) VESA(0): Manufacturer's mask: 0
[    16.932] (II) VESA(0): Supported standard timings:
[    16.932] (II) VESA(0): #0: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    16.932] (II) VESA(0): #1: hsize: 1440  vsize 900  refresh: 75  vid: 3989
[    16.932] (II) VESA(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    16.932] (II) VESA(0): #3: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    16.932] (II) VESA(0): #4: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    16.932] (II) VESA(0): Supported detailed timing:
[    16.932] (II) VESA(0): clock: 106.5 MHz   Image Size:  428 x 255 mm
[    16.932] (II) VESA(0): h_active: 1440  h_sync: 1520  h_sync_end 1672 h_blank_end 1904 h_border: 0
[    16.932] (II) VESA(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 934 v_border: 0
[    16.932] (II) VESA(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 81 kHz, PixClock max 145 MHz
[    16.932] (II) VESA(0): Monitor name: SyncMaster
[    16.932] (II) VESA(0): Serial No: HMFQ811310
[    16.932] (II) VESA(0): EDID (in hex):
[    16.932] (II) VESA(0): 	00ffffffffffff004c2d6f033931594d
[    16.932] (II) VESA(0): 	221201030e291a782a80c5a657499b23
[    16.932] (II) VESA(0): 	125054bfef809500950f81808140714f
[    16.932] (II) VESA(0): 	0101010101019a29a0d0518422305098
[    16.932] (II) VESA(0): 	3600acff1000001c000000fd00384b1e
[    16.932] (II) VESA(0): 	510e000a202020202020000000fc0053
[    16.932] (II) VESA(0): 	796e634d61737465720a2020000000ff
[    16.932] (II) VESA(0): 	00484d46513831313331300a202000ea
[    16.932] (II) VESA(0): EDID vendor "SAM", prod id 879
[    16.932] (II) VESA(0): Using EDID range info for horizontal sync
[    16.932] (II) VESA(0): Using EDID range info for vertical refresh
[    16.932] (II) VESA(0): Printing DDC gathered Modelines:
[    16.932] (II) VESA(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz eP)
[    16.932] (II) VESA(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    16.932] (II) VESA(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    16.932] (II) VESA(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    16.932] (II) VESA(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    16.932] (II) VESA(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    16.932] (II) VESA(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    16.932] (II) VESA(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    16.932] (II) VESA(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    16.932] (II) VESA(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    16.932] (II) VESA(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    16.932] (II) VESA(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    16.932] (II) VESA(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    16.932] (II) VESA(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    16.932] (II) VESA(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    16.932] (II) VESA(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    16.932] (II) VESA(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz e)
[    16.932] (II) VESA(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    16.932] (II) VESA(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    16.932] (II) VESA(0): Searching for matching VESA mode(s):
[    16.933] Mode: 160 (0x0)
[    16.933] 	ModeAttributes: 0x0
[    16.933] 	WinAAttributes: 0x0
[    16.933] 	WinBAttributes: 0x0
[    16.933] 	WinGranularity: 0
[    16.933] 	WinSize: 0
[    16.933] 	WinASegment: 0x0
[    16.933] 	WinBSegment: 0x0
[    16.933] 	WinFuncPtr: 0x0
[    16.933] 	BytesPerScanline: 0
[    16.933] 	XResolution: 0
[    16.933] 	YResolution: 0
[    16.933] 	XCharSize: 0
[    16.933] 	YCharSize: 0
[    16.933] 	NumberOfPlanes: 0
[    16.933] 	BitsPerPixel: 0
[    16.933] 	NumberOfBanks: 0
[    16.933] 	MemoryModel: 0
[    16.933] 	BankSize: 0
[    16.933] 	NumberOfImages: 0
[    16.933] 	RedMaskSize: 0
[    16.933] 	RedFieldPosition: 0
[    16.933] 	GreenMaskSize: 0
[    16.933] 	GreenFieldPosition: 0
[    16.933] 	BlueMaskSize: 0
[    16.933] 	BlueFieldPosition: 0
[    16.933] 	RsvdMaskSize: 0
[    16.933] 	RsvdFieldPosition: 0
[    16.933] 	DirectColorModeInfo: 0
[    16.933] 	PhysBasePtr: 0x0
[    16.933] 	LinBytesPerScanLine: 0
[    16.933] 	BnkNumberOfImagePages: 0
[    16.933] 	LinNumberOfImagePages: 0
[    16.933] 	LinRedMaskSize: 0
[    16.933] 	LinRedFieldPosition: 0
[    16.933] 	LinGreenMaskSize: 0
[    16.933] 	LinGreenFieldPosition: 0
[    16.933] 	LinBlueMaskSize: 0
[    16.933] 	LinBlueFieldPosition: 0
[    16.933] 	LinRsvdMaskSize: 0
[    16.933] 	LinRsvdFieldPosition: 0
[    16.933] 	MaxPixelClock: 0
[    16.933] Mode: 161 (0x0)
[    16.933] 	ModeAttributes: 0x0
[    16.933] 	WinAAttributes: 0x0
[    16.933] 	WinBAttributes: 0x0
[    16.933] 	WinGranularity: 0
[    16.933] 	WinSize: 0
[    16.933] 	WinASegment: 0x0
[    16.933] 	WinBSegment: 0x0
[    16.933] 	WinFuncPtr: 0x0
[    16.933] 	BytesPerScanline: 0
[    16.933] 	XResolution: 0
[    16.933] 	YResolution: 0
[    16.933] 	XCharSize: 0
[    16.933] 	YCharSize: 0
[    16.933] 	NumberOfPlanes: 0
[    16.933] 	BitsPerPixel: 0
[    16.933] 	NumberOfBanks: 0
[    16.933] 	MemoryModel: 0
[    16.933] 	BankSize: 0
[    16.933] 	NumberOfImages: 0
[    16.933] 	RedMaskSize: 0
[    16.933] 	RedFieldPosition: 0
[    16.933] 	GreenMaskSize: 0
[    16.933] 	GreenFieldPosition: 0
[    16.933] 	BlueMaskSize: 0
[    16.933] 	BlueFieldPosition: 0
[    16.933] 	RsvdMaskSize: 0
[    16.933] 	RsvdFieldPosition: 0
[    16.933] 	DirectColorModeInfo: 0
[    16.934] 	PhysBasePtr: 0x0
[    16.934] 	LinBytesPerScanLine: 0
[    16.934] 	BnkNumberOfImagePages: 0
[    16.934] 	LinNumberOfImagePages: 0
[    16.934] 	LinRedMaskSize: 0
[    16.934] 	LinRedFieldPosition: 0
[    16.934] 	LinGreenMaskSize: 0
[    16.934] 	LinGreenFieldPosition: 0
[    16.934] 	LinBlueMaskSize: 0
[    16.934] 	LinBlueFieldPosition: 0
[    16.934] 	LinRsvdMaskSize: 0
[    16.934] 	LinRsvdFieldPosition: 0
[    16.934] 	MaxPixelClock: 0
[    16.934] Mode: 162 (0x0)
[    16.934] 	ModeAttributes: 0x0
[    16.934] 	WinAAttributes: 0x0
[    16.934] 	WinBAttributes: 0x0
[    16.934] 	WinGranularity: 0
[    16.934] 	WinSize: 0
[    16.934] 	WinASegment: 0x0
[    16.934] 	WinBSegment: 0x0
[    16.934] 	WinFuncPtr: 0x0
[    16.934] 	BytesPerScanline: 0
[    16.934] 	XResolution: 0
[    16.934] 	YResolution: 0
[    16.934] 	XCharSize: 0
[    16.934] 	YCharSize: 0
[    16.934] 	NumberOfPlanes: 0
[    16.934] 	BitsPerPixel: 0
[    16.934] 	NumberOfBanks: 0
[    16.934] 	MemoryModel: 0
[    16.934] 	BankSize: 0
[    16.934] 	NumberOfImages: 0
[    16.934] 	RedMaskSize: 0
[    16.934] 	RedFieldPosition: 0
[    16.934] 	GreenMaskSize: 0
[    16.934] 	GreenFieldPosition: 0
[    16.934] 	BlueMaskSize: 0
[    16.934] 	BlueFieldPosition: 0
[    16.934] 	RsvdMaskSize: 0
[    16.934] 	RsvdFieldPosition: 0
[    16.934] 	DirectColorModeInfo: 0
[    16.934] 	PhysBasePtr: 0x0
[    16.934] 	LinBytesPerScanLine: 0
[    16.934] 	BnkNumberOfImagePages: 0
[    16.934] 	LinNumberOfImagePages: 0
[    16.934] 	LinRedMaskSize: 0
[    16.934] 	LinRedFieldPosition: 0
[    16.934] 	LinGreenMaskSize: 0
[    16.934] 	LinGreenFieldPosition: 0
[    16.934] 	LinBlueMaskSize: 0
[    16.934] 	LinBlueFieldPosition: 0
[    16.934] 	LinRsvdMaskSize: 0
[    16.934] 	LinRsvdFieldPosition: 0
[    16.934] 	MaxPixelClock: 0
[    16.935] Mode: 163 (0x0)
[    16.935] 	ModeAttributes: 0x0
[    16.935] 	WinAAttributes: 0x0
[    16.935] 	WinBAttributes: 0x0
[    16.935] 	WinGranularity: 0
[    16.935] 	WinSize: 0
[    16.935] 	WinASegment: 0x0
[    16.935] 	WinBSegment: 0x0
[    16.935] 	WinFuncPtr: 0x0
[    16.935] 	BytesPerScanline: 0
[    16.935] 	XResolution: 0
[    16.935] 	YResolution: 0
[    16.935] 	XCharSize: 0
[    16.935] 	YCharSize: 0
[    16.935] 	NumberOfPlanes: 0
[    16.935] 	BitsPerPixel: 0
[    16.935] 	NumberOfBanks: 0
[    16.935] 	MemoryModel: 0
[    16.935] 	BankSize: 0
[    16.935] 	NumberOfImages: 0
[    16.935] 	RedMaskSize: 0
[    16.935] 	RedFieldPosition: 0
[    16.935] 	GreenMaskSize: 0
[    16.935] 	GreenFieldPosition: 0
[    16.935] 	BlueMaskSize: 0
[    16.935] 	BlueFieldPosition: 0
[    16.935] 	RsvdMaskSize: 0
[    16.935] 	RsvdFieldPosition: 0
[    16.935] 	DirectColorModeInfo: 0
[    16.935] 	PhysBasePtr: 0x0
[    16.935] 	LinBytesPerScanLine: 0
[    16.935] 	BnkNumberOfImagePages: 0
[    16.935] 	LinNumberOfImagePages: 0
[    16.935] 	LinRedMaskSize: 0
[    16.935] 	LinRedFieldPosition: 0
[    16.935] 	LinGreenMaskSize: 0
[    16.935] 	LinGreenFieldPosition: 0
[    16.935] 	LinBlueMaskSize: 0
[    16.935] 	LinBlueFieldPosition: 0
[    16.935] 	LinRsvdMaskSize: 0
[    16.935] 	LinRsvdFieldPosition: 0
[    16.935] 	MaxPixelClock: 0
[    16.936] Mode: 164 (0x0)
[    16.936] 	ModeAttributes: 0x0
[    16.936] 	WinAAttributes: 0x0
[    16.936] 	WinBAttributes: 0x0
[    16.936] 	WinGranularity: 0
[    16.936] 	WinSize: 0
[    16.936] 	WinASegment: 0x0
[    16.936] 	WinBSegment: 0x0
[    16.936] 	WinFuncPtr: 0x0
[    16.936] 	BytesPerScanline: 0
[    16.936] 	XResolution: 0
[    16.936] 	YResolution: 0
[    16.936] 	XCharSize: 0
[    16.936] 	YCharSize: 0
[    16.936] 	NumberOfPlanes: 0
[    16.936] 	BitsPerPixel: 0
[    16.936] 	NumberOfBanks: 0
[    16.936] 	MemoryModel: 0
[    16.936] 	BankSize: 0
[    16.936] 	NumberOfImages: 0
[    16.936] 	RedMaskSize: 0
[    16.936] 	RedFieldPosition: 0
[    16.936] 	GreenMaskSize: 0
[    16.936] 	GreenFieldPosition: 0
[    16.936] 	BlueMaskSize: 0
[    16.936] 	BlueFieldPosition: 0
[    16.936] 	RsvdMaskSize: 0
[    16.936] 	RsvdFieldPosition: 0
[    16.936] 	DirectColorModeInfo: 0
[    16.936] 	PhysBasePtr: 0x0
[    16.936] 	LinBytesPerScanLine: 0
[    16.936] 	BnkNumberOfImagePages: 0
[    16.936] 	LinNumberOfImagePages: 0
[    16.936] 	LinRedMaskSize: 0
[    16.936] 	LinRedFieldPosition: 0
[    16.936] 	LinGreenMaskSize: 0
[    16.936] 	LinGreenFieldPosition: 0
[    16.936] 	LinBlueMaskSize: 0
[    16.936] 	LinBlueFieldPosition: 0
[    16.936] 	LinRsvdMaskSize: 0
[    16.936] 	LinRsvdFieldPosition: 0
[    16.936] 	MaxPixelClock: 0
[    16.936] Mode: 165 (0x0)
[    16.936] 	ModeAttributes: 0x0
[    16.936] 	WinAAttributes: 0x0
[    16.936] 	WinBAttributes: 0x0
[    16.936] 	WinGranularity: 0
[    16.936] 	WinSize: 0
[    16.936] 	WinASegment: 0x0
[    16.936] 	WinBSegment: 0x0
[    16.936] 	WinFuncPtr: 0x0
[    16.936] 	BytesPerScanline: 0
[    16.936] 	XResolution: 0
[    16.936] 	YResolution: 0
[    16.936] 	XCharSize: 0
[    16.936] 	YCharSize: 0
[    16.936] 	NumberOfPlanes: 0
[    16.936] 	BitsPerPixel: 0
[    16.936] 	NumberOfBanks: 0
[    16.936] 	MemoryModel: 0
[    16.936] 	BankSize: 0
[    16.936] 	NumberOfImages: 0
[    16.936] 	RedMaskSize: 0
[    16.936] 	RedFieldPosition: 0
[    16.936] 	GreenMaskSize: 0
[    16.936] 	GreenFieldPosition: 0
[    16.936] 	BlueMaskSize: 0
[    16.936] 	BlueFieldPosition: 0
[    16.936] 	RsvdMaskSize: 0
[    16.936] 	RsvdFieldPosition: 0
[    16.936] 	DirectColorModeInfo: 0
[    16.936] 	PhysBasePtr: 0x0
[    16.936] 	LinBytesPerScanLine: 0
[    16.936] 	BnkNumberOfImagePages: 0
[    16.937] 	LinNumberOfImagePages: 0
[    16.937] 	LinRedMaskSize: 0
[    16.937] 	LinRedFieldPosition: 0
[    16.937] 	LinGreenMaskSize: 0
[    16.937] 	LinGreenFieldPosition: 0
[    16.937] 	LinBlueMaskSize: 0
[    16.937] 	LinBlueFieldPosition: 0
[    16.937] 	LinRsvdMaskSize: 0
[    16.937] 	LinRsvdFieldPosition: 0
[    16.937] 	MaxPixelClock: 0
[    16.937] Mode: 166 (0x0)
[    16.937] 	ModeAttributes: 0x0
[    16.937] 	WinAAttributes: 0x0
[    16.937] 	WinBAttributes: 0x0
[    16.937] 	WinGranularity: 0
[    16.937] 	WinSize: 0
[    16.937] 	WinASegment: 0x0
[    16.937] 	WinBSegment: 0x0
[    16.937] 	WinFuncPtr: 0x0
[    16.937] 	BytesPerScanline: 0
[    16.937] 	XResolution: 0
[    16.937] 	YResolution: 0
[    16.937] 	XCharSize: 0
[    16.937] 	YCharSize: 0
[    16.937] 	NumberOfPlanes: 0
[    16.937] 	BitsPerPixel: 0
[    16.937] 	NumberOfBanks: 0
[    16.937] 	MemoryModel: 0
[    16.937] 	BankSize: 0
[    16.937] 	NumberOfImages: 0
[    16.937] 	RedMaskSize: 0
[    16.937] 	RedFieldPosition: 0
[    16.937] 	GreenMaskSize: 0
[    16.937] 	GreenFieldPosition: 0
[    16.937] 	BlueMaskSize: 0
[    16.937] 	BlueFieldPosition: 0
[    16.937] 	RsvdMaskSize: 0
[    16.937] 	RsvdFieldPosition: 0
[    16.937] 	DirectColorModeInfo: 0
[    16.937] 	PhysBasePtr: 0x0
[    16.937] 	LinBytesPerScanLine: 0
[    16.937] 	BnkNumberOfImagePages: 0
[    16.937] 	LinNumberOfImagePages: 0
[    16.937] 	LinRedMaskSize: 0
[    16.937] 	LinRedFieldPosition: 0
[    16.937] 	LinGreenMaskSize: 0
[    16.937] 	LinGreenFieldPosition: 0
[    16.937] 	LinBlueMaskSize: 0
[    16.937] 	LinBlueFieldPosition: 0
[    16.937] 	LinRsvdMaskSize: 0
[    16.937] 	LinRsvdFieldPosition: 0
[    16.937] 	MaxPixelClock: 0
[    16.938] Mode: 167 (0x0)
[    16.938] 	ModeAttributes: 0x0
[    16.938] 	WinAAttributes: 0x0
[    16.938] 	WinBAttributes: 0x0
[    16.938] 	WinGranularity: 0
[    16.938] 	WinSize: 0
[    16.938] 	WinASegment: 0x0
[    16.938] 	WinBSegment: 0x0
[    16.938] 	WinFuncPtr: 0x0
[    16.938] 	BytesPerScanline: 0
[    16.938] 	XResolution: 0
[    16.938] 	YResolution: 0
[    16.938] 	XCharSize: 0
[    16.938] 	YCharSize: 0
[    16.938] 	NumberOfPlanes: 0
[    16.938] 	BitsPerPixel: 0
[    16.938] 	NumberOfBanks: 0
[    16.938] 	MemoryModel: 0
[    16.938] 	BankSize: 0
[    16.938] 	NumberOfImages: 0
[    16.938] 	RedMaskSize: 0
[    16.938] 	RedFieldPosition: 0
[    16.938] 	GreenMaskSize: 0
[    16.938] 	GreenFieldPosition: 0
[    16.938] 	BlueMaskSize: 0
[    16.938] 	BlueFieldPosition: 0
[    16.938] 	RsvdMaskSize: 0
[    16.938] 	RsvdFieldPosition: 0
[    16.938] 	DirectColorModeInfo: 0
[    16.938] 	PhysBasePtr: 0x0
[    16.938] 	LinBytesPerScanLine: 0
[    16.938] 	BnkNumberOfImagePages: 0
[    16.938] 	LinNumberOfImagePages: 0
[    16.938] 	LinRedMaskSize: 0
[    16.938] 	LinRedFieldPosition: 0
[    16.938] 	LinGreenMaskSize: 0
[    16.938] 	LinGreenFieldPosition: 0
[    16.938] 	LinBlueMaskSize: 0
[    16.938] 	LinBlueFieldPosition: 0
[    16.938] 	LinRsvdMaskSize: 0
[    16.938] 	LinRsvdFieldPosition: 0
[    16.938] 	MaxPixelClock: 0
[    16.939] Mode: 168 (0x0)
[    16.939] 	ModeAttributes: 0x0
[    16.939] 	WinAAttributes: 0x0
[    16.939] 	WinBAttributes: 0x0
[    16.939] 	WinGranularity: 0
[    16.939] 	WinSize: 0
[    16.939] 	WinASegment: 0x0
[    16.939] 	WinBSegment: 0x0
[    16.939] 	WinFuncPtr: 0x0
[    16.939] 	BytesPerScanline: 0
[    16.939] 	XResolution: 0
[    16.939] 	YResolution: 0
[    16.939] 	XCharSize: 0
[    16.939] 	YCharSize: 0
[    16.939] 	NumberOfPlanes: 0
[    16.939] 	BitsPerPixel: 0
[    16.939] 	NumberOfBanks: 0
[    16.939] 	MemoryModel: 0
[    16.939] 	BankSize: 0
[    16.939] 	NumberOfImages: 0
[    16.939] 	RedMaskSize: 0
[    16.939] 	RedFieldPosition: 0
[    16.939] 	GreenMaskSize: 0
[    16.939] 	GreenFieldPosition: 0
[    16.939] 	BlueMaskSize: 0
[    16.939] 	BlueFieldPosition: 0
[    16.939] 	RsvdMaskSize: 0
[    16.939] 	RsvdFieldPosition: 0
[    16.939] 	DirectColorModeInfo: 0
[    16.939] 	PhysBasePtr: 0x0
[    16.939] 	LinBytesPerScanLine: 0
[    16.939] 	BnkNumberOfImagePages: 0
[    16.939] 	LinNumberOfImagePages: 0
[    16.939] 	LinRedMaskSize: 0
[    16.939] 	LinRedFieldPosition: 0
[    16.939] 	LinGreenMaskSize: 0
[    16.939] 	LinGreenFieldPosition: 0
[    16.939] 	LinBlueMaskSize: 0
[    16.939] 	LinBlueFieldPosition: 0
[    16.939] 	LinRsvdMaskSize: 0
[    16.939] 	LinRsvdFieldPosition: 0
[    16.939] 	MaxPixelClock: 0
[    16.941] Mode: 13c (1920x1440)
[    16.941] 	ModeAttributes: 0x9b
[    16.941] 	WinAAttributes: 0x7
[    16.941] 	WinBAttributes: 0x0
[    16.941] 	WinGranularity: 64
[    16.941] 	WinSize: 64
[    16.941] 	WinASegment: 0xa000
[    16.941] 	WinBSegment: 0x0
[    16.941] 	WinFuncPtr: 0xc00059bf
[    16.941] 	BytesPerScanline: 1920
[    16.941] 	XResolution: 1920
[    16.941] 	YResolution: 1440
[    16.941] 	XCharSize: 8
[    16.941] 	YCharSize: 16
[    16.941] 	NumberOfPlanes: 1
[    16.941] 	BitsPerPixel: 8
[    16.941] 	NumberOfBanks: 1
[    16.941] 	MemoryModel: 4
[    16.941] 	BankSize: 0
[    16.941] 	NumberOfImages: 1
[    16.941] 	RedMaskSize: 0
[    16.941] 	RedFieldPosition: 0
[    16.941] 	GreenMaskSize: 0
[    16.941] 	GreenFieldPosition: 0
[    16.941] 	BlueMaskSize: 0
[    16.941] 	BlueFieldPosition: 0
[    16.941] 	RsvdMaskSize: 0
[    16.941] 	RsvdFieldPosition: 0
[    16.941] 	DirectColorModeInfo: 0
[    16.941] 	PhysBasePtr: 0xd0000000
[    16.941] 	LinBytesPerScanLine: 1920
[    16.941] 	BnkNumberOfImagePages: 1
[    16.941] 	LinNumberOfImagePages: 1
[    16.941] 	LinRedMaskSize: 0
[    16.941] 	LinRedFieldPosition: 0
[    16.941] 	LinGreenMaskSize: 0
[    16.941] 	LinGreenFieldPosition: 0
[    16.941] 	LinBlueMaskSize: 0
[    16.941] 	LinBlueFieldPosition: 0
[    16.941] 	LinRsvdMaskSize: 0
[    16.941] 	LinRsvdFieldPosition: 0
[    16.941] 	MaxPixelClock: 230000000
[    16.943] Mode: 14d (1920x1440)
[    16.943] 	ModeAttributes: 0x9b
[    16.943] 	WinAAttributes: 0x7
[    16.943] 	WinBAttributes: 0x0
[    16.943] 	WinGranularity: 64
[    16.943] 	WinSize: 64
[    16.943] 	WinASegment: 0xa000
[    16.943] 	WinBSegment: 0x0
[    16.943] 	WinFuncPtr: 0xc00059bf
[    16.943] 	BytesPerScanline: 3840
[    16.943] 	XResolution: 1920
[    16.943] 	YResolution: 1440
[    16.943] 	XCharSize: 8
[    16.943] 	YCharSize: 16
[    16.943] 	NumberOfPlanes: 1
[    16.943] 	BitsPerPixel: 16
[    16.943] 	NumberOfBanks: 1
[    16.943] 	MemoryModel: 6
[    16.943] 	BankSize: 0
[    16.943] 	NumberOfImages: 0
[    16.943] 	RedMaskSize: 5
[    16.943] 	RedFieldPosition: 11
[    16.943] 	GreenMaskSize: 6
[    16.943] 	GreenFieldPosition: 5
[    16.943] 	BlueMaskSize: 5
[    16.943] 	BlueFieldPosition: 0
[    16.943] 	RsvdMaskSize: 0
[    16.943] 	RsvdFieldPosition: 0
[    16.943] 	DirectColorModeInfo: 0
[    16.943] 	PhysBasePtr: 0xd0000000
[    16.943] 	LinBytesPerScanLine: 3840
[    16.943] 	BnkNumberOfImagePages: 0
[    16.943] 	LinNumberOfImagePages: 0
[    16.943] 	LinRedMaskSize: 5
[    16.943] 	LinRedFieldPosition: 11
[    16.943] 	LinGreenMaskSize: 6
[    16.943] 	LinGreenFieldPosition: 5
[    16.943] 	LinBlueMaskSize: 5
[    16.943] 	LinBlueFieldPosition: 0
[    16.943] 	LinRsvdMaskSize: 0
[    16.943] 	LinRsvdFieldPosition: 0
[    16.943] 	MaxPixelClock: 230000000
[    16.944] Mode: 15c (0x0)
[    16.944] 	ModeAttributes: 0x0
[    16.944] 	WinAAttributes: 0x0
[    16.944] 	WinBAttributes: 0x0
[    16.944] 	WinGranularity: 0
[    16.944] 	WinSize: 0
[    16.944] 	WinASegment: 0x0
[    16.944] 	WinBSegment: 0x0
[    16.944] 	WinFuncPtr: 0x0
[    16.944] 	BytesPerScanline: 0
[    16.944] 	XResolution: 0
[    16.944] 	YResolution: 0
[    16.944] 	XCharSize: 0
[    16.944] 	YCharSize: 0
[    16.944] 	NumberOfPlanes: 0
[    16.944] 	BitsPerPixel: 0
[    16.944] 	NumberOfBanks: 0
[    16.944] 	MemoryModel: 0
[    16.944] 	BankSize: 0
[    16.944] 	NumberOfImages: 0
[    16.944] 	RedMaskSize: 0
[    16.944] 	RedFieldPosition: 0
[    16.944] 	GreenMaskSize: 0
[    16.944] 	GreenFieldPosition: 0
[    16.944] 	BlueMaskSize: 0
[    16.944] 	BlueFieldPosition: 0
[    16.944] 	RsvdMaskSize: 0
[    16.944] 	RsvdFieldPosition: 0
[    16.944] 	DirectColorModeInfo: 0
[    16.944] 	PhysBasePtr: 0x0
[    16.944] 	LinBytesPerScanLine: 0
[    16.944] 	BnkNumberOfImagePages: 0
[    16.944] 	LinNumberOfImagePages: 0
[    16.944] 	LinRedMaskSize: 0
[    16.944] 	LinRedFieldPosition: 0
[    16.944] 	LinGreenMaskSize: 0
[    16.944] 	LinGreenFieldPosition: 0
[    16.944] 	LinBlueMaskSize: 0
[    16.944] 	LinBlueFieldPosition: 0
[    16.944] 	LinRsvdMaskSize: 0
[    16.944] 	LinRsvdFieldPosition: 0
[    16.944] 	MaxPixelClock: 0
[    16.947] Mode: 13a (1600x1200)
[    16.947] 	ModeAttributes: 0x9b
[    16.947] 	WinAAttributes: 0x7
[    16.947] 	WinBAttributes: 0x0
[    16.947] 	WinGranularity: 64
[    16.947] 	WinSize: 64
[    16.947] 	WinASegment: 0xa000
[    16.947] 	WinBSegment: 0x0
[    16.947] 	WinFuncPtr: 0xc00059bf
[    16.947] 	BytesPerScanline: 1600
[    16.947] 	XResolution: 1600
[    16.947] 	YResolution: 1200
[    16.947] 	XCharSize: 8
[    16.947] 	YCharSize: 16
[    16.947] 	NumberOfPlanes: 1
[    16.947] 	BitsPerPixel: 8
[    16.947] 	NumberOfBanks: 1
[    16.947] 	MemoryModel: 4
[    16.947] 	BankSize: 0
[    16.947] 	NumberOfImages: 3
[    16.947] 	RedMaskSize: 0
[    16.947] 	RedFieldPosition: 0
[    16.947] 	GreenMaskSize: 0
[    16.947] 	GreenFieldPosition: 0
[    16.947] 	BlueMaskSize: 0
[    16.947] 	BlueFieldPosition: 0
[    16.947] 	RsvdMaskSize: 0
[    16.947] 	RsvdFieldPosition: 0
[    16.947] 	DirectColorModeInfo: 0
[    16.947] 	PhysBasePtr: 0xd0000000
[    16.947] 	LinBytesPerScanLine: 1600
[    16.947] 	BnkNumberOfImagePages: 3
[    16.947] 	LinNumberOfImagePages: 3
[    16.947] 	LinRedMaskSize: 0
[    16.947] 	LinRedFieldPosition: 0
[    16.947] 	LinGreenMaskSize: 0
[    16.947] 	LinGreenFieldPosition: 0
[    16.947] 	LinBlueMaskSize: 0
[    16.947] 	LinBlueFieldPosition: 0
[    16.947] 	LinRsvdMaskSize: 0
[    16.947] 	LinRsvdFieldPosition: 0
[    16.947] 	MaxPixelClock: 230000000
[    16.949] Mode: 14b (1600x1200)
[    16.949] 	ModeAttributes: 0x9b
[    16.949] 	WinAAttributes: 0x7
[    16.949] 	WinBAttributes: 0x0
[    16.949] 	WinGranularity: 64
[    16.949] 	WinSize: 64
[    16.949] 	WinASegment: 0xa000
[    16.949] 	WinBSegment: 0x0
[    16.949] 	WinFuncPtr: 0xc00059bf
[    16.949] 	BytesPerScanline: 3200
[    16.949] 	XResolution: 1600
[    16.949] 	YResolution: 1200
[    16.949] 	XCharSize: 8
[    16.949] 	YCharSize: 16
[    16.949] 	NumberOfPlanes: 1
[    16.949] 	BitsPerPixel: 16
[    16.949] 	NumberOfBanks: 1
[    16.949] 	MemoryModel: 6
[    16.949] 	BankSize: 0
[    16.949] 	NumberOfImages: 1
[    16.949] 	RedMaskSize: 5
[    16.949] 	RedFieldPosition: 11
[    16.949] 	GreenMaskSize: 6
[    16.949] 	GreenFieldPosition: 5
[    16.949] 	BlueMaskSize: 5
[    16.949] 	BlueFieldPosition: 0
[    16.949] 	RsvdMaskSize: 0
[    16.949] 	RsvdFieldPosition: 0
[    16.949] 	DirectColorModeInfo: 0
[    16.949] 	PhysBasePtr: 0xd0000000
[    16.949] 	LinBytesPerScanLine: 3200
[    16.949] 	BnkNumberOfImagePages: 1
[    16.949] 	LinNumberOfImagePages: 1
[    16.949] 	LinRedMaskSize: 5
[    16.949] 	LinRedFieldPosition: 11
[    16.949] 	LinGreenMaskSize: 6
[    16.949] 	LinGreenFieldPosition: 5
[    16.949] 	LinBlueMaskSize: 5
[    16.949] 	LinBlueFieldPosition: 0
[    16.949] 	LinRsvdMaskSize: 0
[    16.949] 	LinRsvdFieldPosition: 0
[    16.949] 	MaxPixelClock: 230000000
[    16.952] *Mode: 15a (1600x1200)
[    16.952] 	ModeAttributes: 0x9b
[    16.952] 	WinAAttributes: 0x7
[    16.952] 	WinBAttributes: 0x0
[    16.952] 	WinGranularity: 64
[    16.952] 	WinSize: 64
[    16.952] 	WinASegment: 0xa000
[    16.952] 	WinBSegment: 0x0
[    16.952] 	WinFuncPtr: 0xc00059bf
[    16.952] 	BytesPerScanline: 6400
[    16.952] 	XResolution: 1600
[    16.952] 	YResolution: 1200
[    16.952] 	XCharSize: 8
[    16.952] 	YCharSize: 16
[    16.952] 	NumberOfPlanes: 1
[    16.952] 	BitsPerPixel: 32
[    16.952] 	NumberOfBanks: 1
[    16.952] 	MemoryModel: 6
[    16.952] 	BankSize: 0
[    16.952] 	NumberOfImages: 0
[    16.952] 	RedMaskSize: 8
[    16.952] 	RedFieldPosition: 16
[    16.952] 	GreenMaskSize: 8
[    16.952] 	GreenFieldPosition: 8
[    16.952] 	BlueMaskSize: 8
[    16.952] 	BlueFieldPosition: 0
[    16.952] 	RsvdMaskSize: 8
[    16.952] 	RsvdFieldPosition: 24
[    16.952] 	DirectColorModeInfo: 0
[    16.952] 	PhysBasePtr: 0xd0000000
[    16.952] 	LinBytesPerScanLine: 6400
[    16.952] 	BnkNumberOfImagePages: 0
[    16.952] 	LinNumberOfImagePages: 0
[    16.952] 	LinRedMaskSize: 8
[    16.952] 	LinRedFieldPosition: 16
[    16.952] 	LinGreenMaskSize: 8
[    16.952] 	LinGreenFieldPosition: 8
[    16.952] 	LinBlueMaskSize: 8
[    16.952] 	LinBlueFieldPosition: 0
[    16.952] 	LinRsvdMaskSize: 8
[    16.952] 	LinRsvdFieldPosition: 24
[    16.952] 	MaxPixelClock: 230000000
[    16.954] Mode: 107 (1280x1024)
[    16.954] 	ModeAttributes: 0x9b
[    16.954] 	WinAAttributes: 0x7
[    16.954] 	WinBAttributes: 0x0
[    16.954] 	WinGranularity: 64
[    16.954] 	WinSize: 64
[    16.954] 	WinASegment: 0xa000
[    16.954] 	WinBSegment: 0x0
[    16.954] 	WinFuncPtr: 0xc00059bf
[    16.954] 	BytesPerScanline: 1280
[    16.954] 	XResolution: 1280
[    16.954] 	YResolution: 1024
[    16.954] 	XCharSize: 8
[    16.954] 	YCharSize: 16
[    16.954] 	NumberOfPlanes: 1
[    16.954] 	BitsPerPixel: 8
[    16.954] 	NumberOfBanks: 1
[    16.954] 	MemoryModel: 4
[    16.954] 	BankSize: 0
[    16.954] 	NumberOfImages: 5
[    16.954] 	RedMaskSize: 0
[    16.954] 	RedFieldPosition: 0
[    16.954] 	GreenMaskSize: 0
[    16.954] 	GreenFieldPosition: 0
[    16.954] 	BlueMaskSize: 0
[    16.954] 	BlueFieldPosition: 0
[    16.954] 	RsvdMaskSize: 0
[    16.954] 	RsvdFieldPosition: 0
[    16.954] 	DirectColorModeInfo: 0
[    16.954] 	PhysBasePtr: 0xd0000000
[    16.954] 	LinBytesPerScanLine: 1280
[    16.954] 	BnkNumberOfImagePages: 5
[    16.954] 	LinNumberOfImagePages: 5
[    16.954] 	LinRedMaskSize: 0
[    16.954] 	LinRedFieldPosition: 0
[    16.954] 	LinGreenMaskSize: 0
[    16.954] 	LinGreenFieldPosition: 0
[    16.954] 	LinBlueMaskSize: 0
[    16.954] 	LinBlueFieldPosition: 0
[    16.954] 	LinRsvdMaskSize: 0
[    16.954] 	LinRsvdFieldPosition: 0
[    16.954] 	MaxPixelClock: 230000000
[    16.956] Mode: 11a (1280x1024)
[    16.956] 	ModeAttributes: 0x9b
[    16.956] 	WinAAttributes: 0x7
[    16.956] 	WinBAttributes: 0x0
[    16.956] 	WinGranularity: 64
[    16.956] 	WinSize: 64
[    16.956] 	WinASegment: 0xa000
[    16.956] 	WinBSegment: 0x0
[    16.956] 	WinFuncPtr: 0xc00059bf
[    16.956] 	BytesPerScanline: 2560
[    16.956] 	XResolution: 1280
[    16.956] 	YResolution: 1024
[    16.956] 	XCharSize: 8
[    16.956] 	YCharSize: 16
[    16.956] 	NumberOfPlanes: 1
[    16.956] 	BitsPerPixel: 16
[    16.956] 	NumberOfBanks: 1
[    16.956] 	MemoryModel: 6
[    16.956] 	BankSize: 0
[    16.956] 	NumberOfImages: 2
[    16.956] 	RedMaskSize: 5
[    16.956] 	RedFieldPosition: 11
[    16.956] 	GreenMaskSize: 6
[    16.956] 	GreenFieldPosition: 5
[    16.956] 	BlueMaskSize: 5
[    16.956] 	BlueFieldPosition: 0
[    16.956] 	RsvdMaskSize: 0
[    16.956] 	RsvdFieldPosition: 0
[    16.956] 	DirectColorModeInfo: 0
[    16.956] 	PhysBasePtr: 0xd0000000
[    16.956] 	LinBytesPerScanLine: 2560
[    16.956] 	BnkNumberOfImagePages: 2
[    16.956] 	LinNumberOfImagePages: 2
[    16.956] 	LinRedMaskSize: 5
[    16.956] 	LinRedFieldPosition: 11
[    16.956] 	LinGreenMaskSize: 6
[    16.956] 	LinGreenFieldPosition: 5
[    16.956] 	LinBlueMaskSize: 5
[    16.956] 	LinBlueFieldPosition: 0
[    16.956] 	LinRsvdMaskSize: 0
[    16.956] 	LinRsvdFieldPosition: 0
[    16.956] 	MaxPixelClock: 230000000
[    16.959] *Mode: 11b (1280x1024)
[    16.959] 	ModeAttributes: 0x9b
[    16.959] 	WinAAttributes: 0x7
[    16.959] 	WinBAttributes: 0x0
[    16.959] 	WinGranularity: 64
[    16.959] 	WinSize: 64
[    16.959] 	WinASegment: 0xa000
[    16.959] 	WinBSegment: 0x0
[    16.959] 	WinFuncPtr: 0xc00059bf
[    16.959] 	BytesPerScanline: 5120
[    16.959] 	XResolution: 1280
[    16.959] 	YResolution: 1024
[    16.959] 	XCharSize: 8
[    16.959] 	YCharSize: 16
[    16.959] 	NumberOfPlanes: 1
[    16.959] 	BitsPerPixel: 32
[    16.959] 	NumberOfBanks: 1
[    16.959] 	MemoryModel: 6
[    16.959] 	BankSize: 0
[    16.959] 	NumberOfImages: 0
[    16.959] 	RedMaskSize: 8
[    16.959] 	RedFieldPosition: 16
[    16.959] 	GreenMaskSize: 8
[    16.959] 	GreenFieldPosition: 8
[    16.959] 	BlueMaskSize: 8
[    16.959] 	BlueFieldPosition: 0
[    16.959] 	RsvdMaskSize: 8
[    16.959] 	RsvdFieldPosition: 24
[    16.959] 	DirectColorModeInfo: 0
[    16.959] 	PhysBasePtr: 0xd0000000
[    16.959] 	LinBytesPerScanLine: 5120
[    16.959] 	BnkNumberOfImagePages: 0
[    16.959] 	LinNumberOfImagePages: 0
[    16.959] 	LinRedMaskSize: 8
[    16.959] 	LinRedFieldPosition: 16
[    16.959] 	LinGreenMaskSize: 8
[    16.959] 	LinGreenFieldPosition: 8
[    16.959] 	LinBlueMaskSize: 8
[    16.959] 	LinBlueFieldPosition: 0
[    16.959] 	LinRsvdMaskSize: 8
[    16.959] 	LinRsvdFieldPosition: 24
[    16.959] 	MaxPixelClock: 230000000
[    16.961] Mode: 105 (1024x768)
[    16.961] 	ModeAttributes: 0x9b
[    16.961] 	WinAAttributes: 0x7
[    16.961] 	WinBAttributes: 0x0
[    16.961] 	WinGranularity: 64
[    16.961] 	WinSize: 64
[    16.961] 	WinASegment: 0xa000
[    16.961] 	WinBSegment: 0x0
[    16.961] 	WinFuncPtr: 0xc00059bf
[    16.961] 	BytesPerScanline: 1024
[    16.961] 	XResolution: 1024
[    16.961] 	YResolution: 768
[    16.961] 	XCharSize: 8
[    16.961] 	YCharSize: 16
[    16.961] 	NumberOfPlanes: 1
[    16.961] 	BitsPerPixel: 8
[    16.961] 	NumberOfBanks: 1
[    16.961] 	MemoryModel: 4
[    16.961] 	BankSize: 0
[    16.961] 	NumberOfImages: 9
[    16.961] 	RedMaskSize: 0
[    16.961] 	RedFieldPosition: 0
[    16.961] 	GreenMaskSize: 0
[    16.961] 	GreenFieldPosition: 0
[    16.961] 	BlueMaskSize: 0
[    16.961] 	BlueFieldPosition: 0
[    16.961] 	RsvdMaskSize: 0
[    16.961] 	RsvdFieldPosition: 0
[    16.961] 	DirectColorModeInfo: 0
[    16.961] 	PhysBasePtr: 0xd0000000
[    16.961] 	LinBytesPerScanLine: 1024
[    16.961] 	BnkNumberOfImagePages: 9
[    16.961] 	LinNumberOfImagePages: 9
[    16.961] 	LinRedMaskSize: 0
[    16.961] 	LinRedFieldPosition: 0
[    16.961] 	LinGreenMaskSize: 0
[    16.961] 	LinGreenFieldPosition: 0
[    16.961] 	LinBlueMaskSize: 0
[    16.961] 	LinBlueFieldPosition: 0
[    16.961] 	LinRsvdMaskSize: 0
[    16.961] 	LinRsvdFieldPosition: 0
[    16.961] 	MaxPixelClock: 230000000
[    16.963] Mode: 117 (1024x768)
[    16.963] 	ModeAttributes: 0x9b
[    16.963] 	WinAAttributes: 0x7
[    16.963] 	WinBAttributes: 0x0
[    16.963] 	WinGranularity: 64
[    16.963] 	WinSize: 64
[    16.963] 	WinASegment: 0xa000
[    16.963] 	WinBSegment: 0x0
[    16.963] 	WinFuncPtr: 0xc00059bf
[    16.963] 	BytesPerScanline: 2048
[    16.963] 	XResolution: 1024
[    16.963] 	YResolution: 768
[    16.963] 	XCharSize: 8
[    16.963] 	YCharSize: 16
[    16.963] 	NumberOfPlanes: 1
[    16.963] 	BitsPerPixel: 16
[    16.963] 	NumberOfBanks: 1
[    16.963] 	MemoryModel: 6
[    16.963] 	BankSize: 0
[    16.963] 	NumberOfImages: 4
[    16.963] 	RedMaskSize: 5
[    16.963] 	RedFieldPosition: 11
[    16.963] 	GreenMaskSize: 6
[    16.963] 	GreenFieldPosition: 5
[    16.963] 	BlueMaskSize: 5
[    16.963] 	BlueFieldPosition: 0
[    16.963] 	RsvdMaskSize: 0
[    16.963] 	RsvdFieldPosition: 0
[    16.963] 	DirectColorModeInfo: 0
[    16.963] 	PhysBasePtr: 0xd0000000
[    16.963] 	LinBytesPerScanLine: 2048
[    16.963] 	BnkNumberOfImagePages: 4
[    16.963] 	LinNumberOfImagePages: 4
[    16.963] 	LinRedMaskSize: 5
[    16.963] 	LinRedFieldPosition: 11
[    16.963] 	LinGreenMaskSize: 6
[    16.963] 	LinGreenFieldPosition: 5
[    16.963] 	LinBlueMaskSize: 5
[    16.963] 	LinBlueFieldPosition: 0
[    16.963] 	LinRsvdMaskSize: 0
[    16.963] 	LinRsvdFieldPosition: 0
[    16.963] 	MaxPixelClock: 230000000
[    16.966] *Mode: 118 (1024x768)
[    16.966] 	ModeAttributes: 0x9b
[    16.966] 	WinAAttributes: 0x7
[    16.966] 	WinBAttributes: 0x0
[    16.966] 	WinGranularity: 64
[    16.966] 	WinSize: 64
[    16.966] 	WinASegment: 0xa000
[    16.966] 	WinBSegment: 0x0
[    16.966] 	WinFuncPtr: 0xc00059bf
[    16.966] 	BytesPerScanline: 4096
[    16.966] 	XResolution: 1024
[    16.966] 	YResolution: 768
[    16.966] 	XCharSize: 8
[    16.966] 	YCharSize: 16
[    16.966] 	NumberOfPlanes: 1
[    16.966] 	BitsPerPixel: 32
[    16.966] 	NumberOfBanks: 1
[    16.966] 	MemoryModel: 6
[    16.966] 	BankSize: 0
[    16.966] 	NumberOfImages: 1
[    16.966] 	RedMaskSize: 8
[    16.966] 	RedFieldPosition: 16
[    16.966] 	GreenMaskSize: 8
[    16.966] 	GreenFieldPosition: 8
[    16.966] 	BlueMaskSize: 8
[    16.966] 	BlueFieldPosition: 0
[    16.966] 	RsvdMaskSize: 8
[    16.966] 	RsvdFieldPosition: 24
[    16.966] 	DirectColorModeInfo: 0
[    16.966] 	PhysBasePtr: 0xd0000000
[    16.966] 	LinBytesPerScanLine: 4096
[    16.966] 	BnkNumberOfImagePages: 1
[    16.966] 	LinNumberOfImagePages: 1
[    16.966] 	LinRedMaskSize: 8
[    16.966] 	LinRedFieldPosition: 16
[    16.966] 	LinGreenMaskSize: 8
[    16.966] 	LinGreenFieldPosition: 8
[    16.966] 	LinBlueMaskSize: 8
[    16.966] 	LinBlueFieldPosition: 0
[    16.966] 	LinRsvdMaskSize: 8
[    16.966] 	LinRsvdFieldPosition: 24
[    16.966] 	MaxPixelClock: 230000000
[    16.969] *Mode: 112 (640x480)
[    16.969] 	ModeAttributes: 0x9b
[    16.969] 	WinAAttributes: 0x7
[    16.969] 	WinBAttributes: 0x0
[    16.969] 	WinGranularity: 64
[    16.969] 	WinSize: 64
[    16.969] 	WinASegment: 0xa000
[    16.969] 	WinBSegment: 0x0
[    16.969] 	WinFuncPtr: 0xc00059bf
[    16.969] 	BytesPerScanline: 2560
[    16.969] 	XResolution: 640
[    16.969] 	YResolution: 480
[    16.969] 	XCharSize: 8
[    16.969] 	YCharSize: 16
[    16.969] 	NumberOfPlanes: 1
[    16.969] 	BitsPerPixel: 32
[    16.969] 	NumberOfBanks: 1
[    16.969] 	MemoryModel: 6
[    16.969] 	BankSize: 0
[    16.969] 	NumberOfImages: 5
[    16.969] 	RedMaskSize: 8
[    16.969] 	RedFieldPosition: 16
[    16.969] 	GreenMaskSize: 8
[    16.969] 	GreenFieldPosition: 8
[    16.969] 	BlueMaskSize: 8
[    16.969] 	BlueFieldPosition: 0
[    16.969] 	RsvdMaskSize: 8
[    16.969] 	RsvdFieldPosition: 24
[    16.969] 	DirectColorModeInfo: 0
[    16.969] 	PhysBasePtr: 0xd0000000
[    16.969] 	LinBytesPerScanLine: 2560
[    16.969] 	BnkNumberOfImagePages: 5
[    16.969] 	LinNumberOfImagePages: 5
[    16.969] 	LinRedMaskSize: 8
[    16.969] 	LinRedFieldPosition: 16
[    16.969] 	LinGreenMaskSize: 8
[    16.969] 	LinGreenFieldPosition: 8
[    16.969] 	LinBlueMaskSize: 8
[    16.969] 	LinBlueFieldPosition: 0
[    16.969] 	LinRsvdMaskSize: 8
[    16.969] 	LinRsvdFieldPosition: 24
[    16.969] 	MaxPixelClock: 230000000
[    16.971] Mode: 114 (800x600)
[    16.971] 	ModeAttributes: 0x9b
[    16.971] 	WinAAttributes: 0x7
[    16.971] 	WinBAttributes: 0x0
[    16.971] 	WinGranularity: 64
[    16.971] 	WinSize: 64
[    16.971] 	WinASegment: 0xa000
[    16.971] 	WinBSegment: 0x0
[    16.971] 	WinFuncPtr: 0xc00059bf
[    16.971] 	BytesPerScanline: 1600
[    16.971] 	XResolution: 800
[    16.971] 	YResolution: 600
[    16.971] 	XCharSize: 8
[    16.971] 	YCharSize: 16
[    16.971] 	NumberOfPlanes: 1
[    16.971] 	BitsPerPixel: 16
[    16.971] 	NumberOfBanks: 1
[    16.971] 	MemoryModel: 6
[    16.971] 	BankSize: 0
[    16.971] 	NumberOfImages: 7
[    16.971] 	RedMaskSize: 5
[    16.971] 	RedFieldPosition: 11
[    16.971] 	GreenMaskSize: 6
[    16.971] 	GreenFieldPosition: 5
[    16.971] 	BlueMaskSize: 5
[    16.971] 	BlueFieldPosition: 0
[    16.971] 	RsvdMaskSize: 0
[    16.971] 	RsvdFieldPosition: 0
[    16.971] 	DirectColorModeInfo: 0
[    16.971] 	PhysBasePtr: 0xd0000000
[    16.971] 	LinBytesPerScanLine: 1600
[    16.971] 	BnkNumberOfImagePages: 7
[    16.971] 	LinNumberOfImagePages: 7
[    16.971] 	LinRedMaskSize: 5
[    16.971] 	LinRedFieldPosition: 11
[    16.971] 	LinGreenMaskSize: 6
[    16.971] 	LinGreenFieldPosition: 5
[    16.971] 	LinBlueMaskSize: 5
[    16.971] 	LinBlueFieldPosition: 0
[    16.971] 	LinRsvdMaskSize: 0
[    16.971] 	LinRsvdFieldPosition: 0
[    16.971] 	MaxPixelClock: 230000000
[    16.974] *Mode: 115 (800x600)
[    16.974] 	ModeAttributes: 0x9b
[    16.974] 	WinAAttributes: 0x7
[    16.974] 	WinBAttributes: 0x0
[    16.974] 	WinGranularity: 64
[    16.974] 	WinSize: 64
[    16.974] 	WinASegment: 0xa000
[    16.974] 	WinBSegment: 0x0
[    16.974] 	WinFuncPtr: 0xc00059bf
[    16.974] 	BytesPerScanline: 3200
[    16.974] 	XResolution: 800
[    16.974] 	YResolution: 600
[    16.974] 	XCharSize: 8
[    16.974] 	YCharSize: 16
[    16.974] 	NumberOfPlanes: 1
[    16.974] 	BitsPerPixel: 32
[    16.974] 	NumberOfBanks: 1
[    16.974] 	MemoryModel: 6
[    16.974] 	BankSize: 0
[    16.974] 	NumberOfImages: 3
[    16.974] 	RedMaskSize: 8
[    16.974] 	RedFieldPosition: 16
[    16.974] 	GreenMaskSize: 8
[    16.974] 	GreenFieldPosition: 8
[    16.974] 	BlueMaskSize: 8
[    16.974] 	BlueFieldPosition: 0
[    16.974] 	RsvdMaskSize: 8
[    16.974] 	RsvdFieldPosition: 24
[    16.974] 	DirectColorModeInfo: 0
[    16.974] 	PhysBasePtr: 0xd0000000
[    16.974] 	LinBytesPerScanLine: 3200
[    16.974] 	BnkNumberOfImagePages: 3
[    16.974] 	LinNumberOfImagePages: 3
[    16.974] 	LinRedMaskSize: 8
[    16.974] 	LinRedFieldPosition: 16
[    16.974] 	LinGreenMaskSize: 8
[    16.974] 	LinGreenFieldPosition: 8
[    16.974] 	LinBlueMaskSize: 8
[    16.974] 	LinBlueFieldPosition: 0
[    16.974] 	LinRsvdMaskSize: 8
[    16.974] 	LinRsvdFieldPosition: 24
[    16.974] 	MaxPixelClock: 230000000
[    16.975] Mode: 101 (640x480)
[    16.975] 	ModeAttributes: 0x9b
[    16.975] 	WinAAttributes: 0x7
[    16.975] 	WinBAttributes: 0x0
[    16.975] 	WinGranularity: 64
[    16.975] 	WinSize: 64
[    16.975] 	WinASegment: 0xa000
[    16.975] 	WinBSegment: 0x0
[    16.975] 	WinFuncPtr: 0xc00059bf
[    16.975] 	BytesPerScanline: 640
[    16.975] 	XResolution: 640
[    16.975] 	YResolution: 480
[    16.975] 	XCharSize: 8
[    16.975] 	YCharSize: 16
[    16.975] 	NumberOfPlanes: 1
[    16.975] 	BitsPerPixel: 8
[    16.975] 	NumberOfBanks: 1
[    16.975] 	MemoryModel: 4
[    16.975] 	BankSize: 0
[    16.975] 	NumberOfImages: 23
[    16.975] 	RedMaskSize: 0
[    16.975] 	RedFieldPosition: 0
[    16.975] 	GreenMaskSize: 0
[    16.975] 	GreenFieldPosition: 0
[    16.975] 	BlueMaskSize: 0
[    16.975] 	BlueFieldPosition: 0
[    16.976] 	RsvdMaskSize: 0
[    16.976] 	RsvdFieldPosition: 0
[    16.976] 	DirectColorModeInfo: 0
[    16.976] 	PhysBasePtr: 0xd0000000
[    16.976] 	LinBytesPerScanLine: 640
[    16.976] 	BnkNumberOfImagePages: 23
[    16.976] 	LinNumberOfImagePages: 23
[    16.976] 	LinRedMaskSize: 0
[    16.976] 	LinRedFieldPosition: 0
[    16.976] 	LinGreenMaskSize: 0
[    16.976] 	LinGreenFieldPosition: 0
[    16.976] 	LinBlueMaskSize: 0
[    16.976] 	LinBlueFieldPosition: 0
[    16.976] 	LinRsvdMaskSize: 0
[    16.976] 	LinRsvdFieldPosition: 0
[    16.976] 	MaxPixelClock: 230000000
[    16.977] Mode: 103 (800x600)
[    16.977] 	ModeAttributes: 0x9b
[    16.977] 	WinAAttributes: 0x7
[    16.977] 	WinBAttributes: 0x0
[    16.977] 	WinGranularity: 64
[    16.977] 	WinSize: 64
[    16.977] 	WinASegment: 0xa000
[    16.977] 	WinBSegment: 0x0
[    16.977] 	WinFuncPtr: 0xc00059bf
[    16.977] 	BytesPerScanline: 832
[    16.977] 	XResolution: 800
[    16.977] 	YResolution: 600
[    16.977] 	XCharSize: 8
[    16.977] 	YCharSize: 16
[    16.977] 	NumberOfPlanes: 1
[    16.977] 	BitsPerPixel: 8
[    16.977] 	NumberOfBanks: 1
[    16.977] 	MemoryModel: 4
[    16.977] 	BankSize: 0
[    16.977] 	NumberOfImages: 14
[    16.977] 	RedMaskSize: 0
[    16.977] 	RedFieldPosition: 0
[    16.977] 	GreenMaskSize: 0
[    16.977] 	GreenFieldPosition: 0
[    16.977] 	BlueMaskSize: 0
[    16.977] 	BlueFieldPosition: 0
[    16.977] 	RsvdMaskSize: 0
[    16.977] 	RsvdFieldPosition: 0
[    16.977] 	DirectColorModeInfo: 0
[    16.977] 	PhysBasePtr: 0xd0000000
[    16.977] 	LinBytesPerScanLine: 832
[    16.977] 	BnkNumberOfImagePages: 14
[    16.977] 	LinNumberOfImagePages: 14
[    16.977] 	LinRedMaskSize: 0
[    16.977] 	LinRedFieldPosition: 0
[    16.977] 	LinGreenMaskSize: 0
[    16.977] 	LinGreenFieldPosition: 0
[    16.977] 	LinBlueMaskSize: 0
[    16.977] 	LinBlueFieldPosition: 0
[    16.977] 	LinRsvdMaskSize: 0
[    16.977] 	LinRsvdFieldPosition: 0
[    16.977] 	MaxPixelClock: 230000000
[    16.979] Mode: 111 (640x480)
[    16.979] 	ModeAttributes: 0x9b
[    16.979] 	WinAAttributes: 0x7
[    16.979] 	WinBAttributes: 0x0
[    16.979] 	WinGranularity: 64
[    16.979] 	WinSize: 64
[    16.979] 	WinASegment: 0xa000
[    16.979] 	WinBSegment: 0x0
[    16.979] 	WinFuncPtr: 0xc00059bf
[    16.979] 	BytesPerScanline: 1280
[    16.979] 	XResolution: 640
[    16.979] 	YResolution: 480
[    16.979] 	XCharSize: 8
[    16.979] 	YCharSize: 16
[    16.979] 	NumberOfPlanes: 1
[    16.979] 	BitsPerPixel: 16
[    16.979] 	NumberOfBanks: 1
[    16.979] 	MemoryModel: 6
[    16.979] 	BankSize: 0
[    16.979] 	NumberOfImages: 12
[    16.979] 	RedMaskSize: 5
[    16.979] 	RedFieldPosition: 11
[    16.979] 	GreenMaskSize: 6
[    16.979] 	GreenFieldPosition: 5
[    16.979] 	BlueMaskSize: 5
[    16.979] 	BlueFieldPosition: 0
[    16.979] 	RsvdMaskSize: 0
[    16.979] 	RsvdFieldPosition: 0
[    16.979] 	DirectColorModeInfo: 0
[    16.979] 	PhysBasePtr: 0xd0000000
[    16.979] 	LinBytesPerScanLine: 1280
[    16.979] 	BnkNumberOfImagePages: 12
[    16.979] 	LinNumberOfImagePages: 12
[    16.979] 	LinRedMaskSize: 5
[    16.979] 	LinRedFieldPosition: 11
[    16.979] 	LinGreenMaskSize: 6
[    16.979] 	LinGreenFieldPosition: 5
[    16.979] 	LinBlueMaskSize: 5
[    16.979] 	LinBlueFieldPosition: 0
[    16.979] 	LinRsvdMaskSize: 0
[    16.979] 	LinRsvdFieldPosition: 0
[    16.979] 	MaxPixelClock: 230000000
[    16.979] 
[    16.979] (II) VESA(0): Total Memory: 123 64KB banks (7872kB)
[    16.979] (II) VESA(0): <default monitor>: Using hsync range of 30.00-81.00 kHz
[    16.979] (II) VESA(0): <default monitor>: Using vrefresh range of 56.00-75.00 Hz
[    16.979] (II) VESA(0): <default monitor>: Using maximum pixel clock of 145.00 MHz
[    16.979] (WW) VESA(0): Unable to estimate virtual size
[    16.979] (II) VESA(0): Not using built-in mode "1600x1200" (no mode of this name)
[    16.993] (--) VESA(0): Virtual size is 1280x1024 (pitch 1280)
[    16.993] (**) VESA(0): *Built-in mode "1280x1024"
[    16.993] (**) VESA(0): *Built-in mode "1024x768"
[    16.993] (**) VESA(0): *Built-in mode "800x600"
[    16.993] (**) VESA(0): *Built-in mode "640x480"
[    16.993] (**) VESA(0): Display dimensions: (410, 260) mm
[    16.993] (**) VESA(0): DPI set to (79, 100)
[    16.993] (**) VESA(0): Using "Shadow Framebuffer"
[    16.993] (II) Loading sub module "shadow"
[    16.993] (II) LoadModule: "shadow"
[    16.993] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    16.994] (II) Module shadow: vendor="X.Org Foundation"
[    16.994] 	compiled for 1.13.0, module version = 1.1.0
[    16.994] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    16.994] (II) Loading sub module "fb"
[    16.994] (II) LoadModule: "fb"
[    16.994] (II) Loading /usr/lib/xorg/modules/libfb.so
[    16.994] (II) Module fb: vendor="X.Org Foundation"
[    16.994] 	compiled for 1.13.0, module version = 1.0.0
[    16.994] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    16.994] (II) UnloadModule: "modesetting"
[    16.994] (II) Unloading modesetting
[    16.994] (II) UnloadModule: "fbdev"
[    16.994] (II) Unloading fbdev
[    16.994] (II) UnloadSubModule: "fbdevhw"
[    16.994] (II) Unloading fbdevhw
[    16.994] (==) Depth 24 pixmap format is 32 bpp
[    16.994] (II) Loading sub module "int10"
[    16.994] (II) LoadModule: "int10"
[    16.994] (II) Loading /usr/lib/xorg/modules/libint10.so
[    16.994] (II) Module int10: vendor="X.Org Foundation"
[    16.994] 	compiled for 1.13.0, module version = 1.0.0
[    16.994] 	ABI class: X.Org Video Driver, version 13.0
[    16.994] (II) VESA(0): initializing int10
[    16.999] (II) VESA(0): Bad V_BIOS checksum
[    16.999] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    17.000] (II) VESA(0): VESA BIOS detected
[    17.000] (II) VESA(0): VESA VBE Version 3.0
[    17.000] (II) VESA(0): VESA VBE Total Mem: 7872 kB
[    17.000] (II) VESA(0): VESA VBE OEM: Intel(r) 82945G Chipset Family Graphics Chip Accelerated VGA BIOS
[    17.000] (II) VESA(0): VESA VBE OEM Software Rev: 1.0
[    17.000] (II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
[    17.000] (II) VESA(0): VESA VBE OEM Product: Intel(r) 82945G Chipset Family Graphics Controller
[    17.000] (II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
[    17.000] (II) VESA(0): virtual address = 0xb6501000,
	physical address = 0xd0000000, size = 8060928
[    17.025] (II) VESA(0): Setting up VESA Mode 0x11B (1280x1024)
[    17.075] (==) VESA(0): Default visual is TrueColor
[    17.075] (==) VESA(0): Backing store disabled
[    17.075] (==) VESA(0): DPMS enabled
[    17.075] (==) RandR enabled
[    17.084] (II) AIGLX: Screen 0 is not DRI2 capable
[    17.084] (II) AIGLX: Screen 0 is not DRI capable
[    17.095] (II) AIGLX: Loaded and initialized swrast
[    17.095] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    17.111] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    17.114] (II) config/udev: Adding input device USB 2.0 Camera (/dev/input/event1)
[    17.114] (**) USB 2.0 Camera: Applying InputClass "evdev keyboard catchall"
[    17.114] (II) LoadModule: "evdev"
[    17.115] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.115] (II) Module evdev: vendor="X.Org Foundation"
[    17.115] 	compiled for 1.13.0, module version = 2.7.3
[    17.115] 	Module class: X.Org XInput Driver
[    17.115] 	ABI class: X.Org XInput driver, version 18.0
[    17.115] (II) Using input driver 'evdev' for 'USB 2.0 Camera'
[    17.115] (**) USB 2.0 Camera: always reports core events
[    17.115] (**) evdev: USB 2.0 Camera: Device: "/dev/input/event1"
[    17.115] (--) evdev: USB 2.0 Camera: Vendor 0xc45 Product 0x62f1
[    17.115] (--) evdev: USB 2.0 Camera: Found keys
[    17.115] (II) evdev: USB 2.0 Camera: Configuring as keyboard
[    17.115] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3:1.0/input/input1/event1"
[    17.115] (II) XINPUT: Adding extended input device "USB 2.0 Camera" (type: KEYBOARD, id 6)
[    17.115] (**) Option "xkb_rules" "evdev"
[    17.115] (**) Option "xkb_model" "pc105"
[    17.115] (**) Option "xkb_layout" "us"
[    17.116] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event0)
[    17.116] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    17.116] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    17.116] (**) AT Translated Set 2 keyboard: always reports core events
[    17.116] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event0"
[    17.116] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    17.116] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    17.116] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    17.116] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input0/event0"
[    17.116] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 7)
[    17.116] (**) Option "xkb_rules" "evdev"
[    17.116] (**) Option "xkb_model" "pc105"
[    17.116] (**) Option "xkb_layout" "us"
[    17.117] (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/event2)
[    17.117] (**) ImPS/2 Generic Wheel Mouse: Applying InputClass "evdev pointer catchall"
[    17.117] (II) Using input driver 'evdev' for 'ImPS/2 Generic Wheel Mouse'
[    17.117] (**) ImPS/2 Generic Wheel Mouse: always reports core events
[    17.117] (**) evdev: ImPS/2 Generic Wheel Mouse: Device: "/dev/input/event2"
[    17.117] (--) evdev: ImPS/2 Generic Wheel Mouse: Vendor 0x2 Product 0x5
[    17.117] (--) evdev: ImPS/2 Generic Wheel Mouse: Found 3 mouse buttons
[    17.117] (--) evdev: ImPS/2 Generic Wheel Mouse: Found scroll wheel(s)
[    17.117] (--) evdev: ImPS/2 Generic Wheel Mouse: Found relative axes
[    17.117] (--) evdev: ImPS/2 Generic Wheel Mouse: Found x and y relative axes
[    17.117] (II) evdev: ImPS/2 Generic Wheel Mouse: Configuring as mouse
[    17.117] (II) evdev: ImPS/2 Generic Wheel Mouse: Adding scrollwheel support
[    17.117] (**) evdev: ImPS/2 Generic Wheel Mouse: YAxisMapping: buttons 4 and 5
[    17.117] (**) evdev: ImPS/2 Generic Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    17.117] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input2/event2"
[    17.117] (II) XINPUT: Adding extended input device "ImPS/2 Generic Wheel Mouse" (type: MOUSE, id 8)
[    17.117] (II) evdev: ImPS/2 Generic Wheel Mouse: initialized for relative axes.
[    17.117] (**) ImPS/2 Generic Wheel Mouse: (accel) keeping acceleration scheme 1
[    17.117] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration profile 0
[    17.117] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration factor: 2.000
[    17.117] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration threshold: 4
[    17.117] (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/mouse0)
[    17.117] (II) No input driver specified, ignoring this device.
[    17.117] (II) This device may have been added with another device file.
[    22.758] (II) XKB: reuse xkmfile /var/lib/xkb/server-8AA988DD479FAABEC4FC3CCCF4CC29B4948840B4.xkm
[  1865.052] (II) XKB: reuse xkmfile /var/lib/xkb/server-53628FFEAE787BDF7F5128B07068E2A1D9DEC814.xkm
[  2556.278] (II) XKB: reuse xkmfile /var/lib/xkb/server-53628FFEAE787BDF7F5128B07068E2A1D9DEC814.xkm
```

bbcode added

---

### Post by wheelchairman on 2013-10-12
Sorry, it turn out to be a very lengthy reply. Didn't know how to use [code] tag.

---

### Post by wheelchairman on 2013-10-12
Kindly guide me solve my problem.

---

### Post by Yellow Pasque on 2013-10-13
```
[ 16.864] (EE) open /dev/dri/card0: No such file or directory
```

Other than checking the permissions and existence of /dev/dri/, I'm not really sure what to check.
The other thing I would try is loading intel module manually and seeing if there are errors:
```
sudo modprobe -r intel
sudo modprobe -v intel
```

---

### Post by Elfy on 2013-10-13
> **wheelchairman said:**
> Sorry, it turn out to be a very lengthy reply. Didn't know how to use ```
 tag.

If you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse][code][/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by wheelchairman on 2013-10-13
```
 "FATAL: Module intel not found." is the error message I got
```

---

### Post by wheelchairman on 2013-10-13
```
 "FATAL: Module intel not found." is the error message I got
```

---

### Post by Yellow Pasque on 2013-10-13
Sorry, I guess the module is "i915" (not "intel").

---

