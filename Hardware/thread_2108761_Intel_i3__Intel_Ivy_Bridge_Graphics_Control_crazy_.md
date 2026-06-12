---
title: "Intel i3  Intel Ivy Bridge Graphics Control crazy colors over HDMI"
date: 2013-01-25
forum: Hardware
---

### Post by gerpc on 2013-01-25
Hi,

I've a very strange bug to report.

I've a machine with a core i7 (3770k and intel HD 4000) and another one with a core i3 (3221 and Intel HD 2500). both Machines (The i7 one with 12.10 and the i3 one with 12.04 LTS) have the very same bug.

If I use the HDMI connector to connect to my Pioneer VSX-921K, All colors are crazy. I see pink instead of white and gray intead of black. 

I've tracked it over internet and I found this:

[http://lists.freedesktop.org/archives/intel-gfx/2012-July/019000.html](http://lists.freedesktop.org/archives/intel-gfx/2012-July/019000.html)

The bug that is refered is: "#1081676: drm/i915: fixup infoframe support for sdvo" commited here: [http://cgit.freedesktop.org/~danvet/drm-intel/commit/?h=drm-intel-next&id=81014b9d0b55fb0b48f26cd2a943359750d532db](http://cgit.freedesktop.org/~danvet/drm-intel/commit/?h=drm-intel-next&id=81014b9d0b55fb0b48f26cd2a943359750d532db)

As far I can see, this bug is backported to precise kernel in version 3.2.0-35.55 which is the kernel I've running now in my core i3 machine. But for me at least, the bug persist

If I install a monitor to the HDMI connecto it works fine.

I'm attaching my Xorg.0.log and my lspci -vv

Thanks!

---

### Post by gerpc on 2013-01-25
Xorg.0.conf

```

[  2220.285] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[  2220.285] X Protocol Version 11, Revision 0
[  2220.285] Build Operating System: Linux 2.6.42-23-generic x86_64 Ubuntu
[  2220.285] Current Operating System: Linux skywalker 3.2.0-30-generic #48-Ubuntu SMP Fri Aug 24 16:52:48 UTC 2012 x86_64
[  2220.285] Kernel command line: BOOT_IMAGE=/vmlinuz-3.2.0-30-generic root=UUID=d4a7c2a1-d356-4af9-b094-876d735d576d ro quiet splash vt.handoff=7
[  2220.285] Build Date: 29 August 2012  12:12:33AM
[  2220.285] xorg-server 2:1.11.4-0ubuntu10.8 (For technical support please see http://www.ubuntu.com/support) 
[  2220.285] Current version of pixman: 0.24.4
[  2220.285] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[  2220.285] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  2220.285] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Jan 25 00:02:58 2013
[  2220.285] (==) Using config file: "/etc/X11/xorg.conf"
[  2220.285] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  2220.286] (==) ServerLayout "Default Layout"
[  2220.286] (**) |-->Screen "Screen0" (0)
[  2220.286] (**) |   |-->Monitor "Monitor0"
[  2220.286] (**) |   |-->Device "Device0"
[  2220.286] (**) |-->Input Device "Keyboard0"
[  2220.286] (**) |-->Input Device "Mouse0"
[  2220.286] (==) Automatically adding devices
[  2220.286] (==) Automatically enabling devices
[  2220.286] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  2220.286] 	Entry deleted from font path.
[  2220.286] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[  2220.286] 	Entry deleted from font path.
[  2220.286] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[  2220.286] 	Entry deleted from font path.
[  2220.286] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[  2220.286] 	Entry deleted from font path.
[  2220.286] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[  2220.286] 	Entry deleted from font path.
[  2220.286] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[  2220.286] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[  2220.286] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[  2220.286] (WW) Disabling Keyboard0
[  2220.286] (WW) Disabling Mouse0
[  2220.286] (II) Loader magic: 0x7f8443a9eb00
[  2220.286] (II) Module ABI versions:
[  2220.286] 	X.Org ANSI C Emulation: 0.4
[  2220.286] 	X.Org Video Driver: 11.0
[  2220.286] 	X.Org XInput driver : 16.0
[  2220.286] 	X.Org Server Extension : 6.0
[  2220.286] (--) PCI:*(0:0:2:0) 8086:0152:1043:84ca rev 9, Mem @ 0xf7800000/4194304, 0xe0000000/268435456, I/O @ 0x0000f000/64
[  2220.286] (II) Open ACPI successful (/var/run/acpid.socket)
[  2220.286] (II) LoadModule: "extmod"
[  2220.287] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[  2220.287] (II) Module extmod: vendor="X.Org Foundation"
[  2220.287] 	compiled for 1.11.3, module version = 1.0.0
[  2220.287] 	Module class: X.Org Server Extension
[  2220.287] 	ABI class: X.Org Server Extension, version 6.0
[  2220.287] (II) Loading extension MIT-SCREEN-SAVER
[  2220.287] (II) Loading extension XFree86-VidModeExtension
[  2220.287] (II) Loading extension XFree86-DGA
[  2220.287] (II) Loading extension DPMS
[  2220.287] (II) Loading extension XVideo
[  2220.287] (II) Loading extension XVideo-MotionCompensation
[  2220.287] (II) Loading extension X-Resource
[  2220.287] (II) LoadModule: "dbe"
[  2220.287] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[  2220.287] (II) Module dbe: vendor="X.Org Foundation"
[  2220.287] 	compiled for 1.11.3, module version = 1.0.0
[  2220.287] 	Module class: X.Org Server Extension
[  2220.287] 	ABI class: X.Org Server Extension, version 6.0
[  2220.287] (II) Loading extension DOUBLE-BUFFER
[  2220.287] (II) LoadModule: "glx"
[  2220.287] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[  2220.287] (II) Module glx: vendor="X.Org Foundation"
[  2220.287] 	compiled for 1.11.3, module version = 1.0.0
[  2220.287] 	ABI class: X.Org Server Extension, version 6.0
[  2220.287] (==) AIGLX enabled
[  2220.287] (II) Loading extension GLX
[  2220.287] (II) LoadModule: "record"
[  2220.287] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[  2220.287] (II) Module record: vendor="X.Org Foundation"
[  2220.287] 	compiled for 1.11.3, module version = 1.13.0
[  2220.287] 	Module class: X.Org Server Extension
[  2220.287] 	ABI class: X.Org Server Extension, version 6.0
[  2220.287] (II) Loading extension RECORD
[  2220.287] (II) LoadModule: "dri"
[  2220.287] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[  2220.287] (II) Module dri: vendor="X.Org Foundation"
[  2220.287] 	compiled for 1.11.3, module version = 1.0.0
[  2220.287] 	ABI class: X.Org Server Extension, version 6.0
[  2220.287] (II) Loading extension XFree86-DRI
[  2220.287] (II) LoadModule: "dri2"
[  2220.287] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[  2220.287] (II) Module dri2: vendor="X.Org Foundation"
[  2220.287] 	compiled for 1.11.3, module version = 1.2.0
[  2220.287] 	ABI class: X.Org Server Extension, version 6.0
[  2220.287] (II) Loading extension DRI2
[  2220.287] (II) LoadModule: "intel"
[  2220.287] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[  2220.288] (II) Module intel: vendor="X.Org Foundation"
[  2220.288] 	compiled for 1.11.3, module version = 2.20.19
[  2220.288] 	Module class: X.Org Video Driver
[  2220.288] 	ABI class: X.Org Video Driver, version 11.0
[  2220.288] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
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
[  2220.288] (++) using VT number 7

[  2220.288] drmOpenDevice: node name is /dev/dri/card0
[  2220.288] drmOpenDevice: open result is 8, (OK)
[  2220.288] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[  2220.288] drmOpenDevice: node name is /dev/dri/card0
[  2220.288] drmOpenDevice: open result is 8, (OK)
[  2220.288] drmOpenByBusid: drmOpenMinor returns 8
[  2220.288] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[  2220.288] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[  2220.288] drmOpenDevice: node name is /dev/dri/card0
[  2220.288] drmOpenDevice: open result is 9, (OK)
[  2220.288] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[  2220.288] drmOpenDevice: node name is /dev/dri/card0
[  2220.288] drmOpenDevice: open result is 9, (OK)
[  2220.288] drmOpenByBusid: drmOpenMinor returns 9
[  2220.288] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[  2220.288] (**) intel(0): Depth 24, (--) framebuffer bpp 32
[  2220.288] (==) intel(0): RGB weight 888
[  2220.288] (==) intel(0): Default visual is TrueColor
[  2220.288] (**) intel(0): Option "AccelMethod" "sna"
[  2220.288] (--) intel(0): Integrated Graphics Chipset: Intel(R) Ivybridge Desktop (GT1)
[  2220.288] (**) intel(0): Framebuffer tiled
[  2220.288] (**) intel(0): Pixmaps tiled
[  2220.288] (**) intel(0): "Tear free" disabled
[  2220.288] (**) intel(0): Forcing per-crtc-pixmaps? no
[  2220.288] (II) intel(0): Output VGA1 using monitor section Monitor0
[  2220.293] (II) intel(0): Output HDMI1 has no monitor section
[  2220.525] (II) intel(0): Output HDMI2 has no monitor section
[  2220.572] (II) intel(0): Output DP1 has no monitor section
[  2220.620] (II) intel(0): Output DP2 has no monitor section
[  2220.620] (II) intel(0): EDID for output VGA1
[  2220.624] (II) intel(0): EDID for output HDMI1
[  2220.856] (II) intel(0): EDID for output HDMI2
[  2220.856] (II) intel(0): Manufacturer: PIO  Model: 0  Serial#: 16843009
[  2220.856] (II) intel(0): Year: 2010  Week: 0
[  2220.856] (II) intel(0): EDID Version: 1.3
[  2220.856] (II) intel(0): Digital Display Input
[  2220.856] (II) intel(0): Max Image Size [cm]: horiz.: 160  vert.: 90
[  2220.856] (II) intel(0): Gamma: 2.20
[  2220.856] (II) intel(0): No DPMS capabilities specified
[  2220.856] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[  2220.856] (II) intel(0): First detailed timing is preferred mode
[  2220.856] (II) intel(0): redX: 0.625 redY: 0.340   greenX: 0.280 greenY: 0.595
[  2220.856] (II) intel(0): blueX: 0.155 blueY: 0.070   whiteX: 0.283 whiteY: 0.298
[  2220.856] (II) intel(0): Supported established timings:
[  2220.856] (II) intel(0): 640x480@60Hz
[  2220.856] (II) intel(0): 800x600@60Hz
[  2220.856] (II) intel(0): 1024x768@60Hz
[  2220.856] (II) intel(0): Manufacturer's mask: 0
[  2220.856] (II) intel(0): Supported standard timings:
[  2220.856] (II) intel(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[  2220.856] (II) intel(0): Supported detailed timing:
[  2220.856] (II) intel(0): clock: 148.5 MHz   Image Size:  1600 x 900 mm
[  2220.856] (II) intel(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[  2220.856] (II) intel(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[  2220.856] (II) intel(0): Supported detailed timing:
[  2220.856] (II) intel(0): clock: 74.2 MHz   Image Size:  1600 x 900 mm
[  2220.856] (II) intel(0): h_active: 1280  h_sync: 1390  h_sync_end 1430 h_blank_end 1650 h_border: 0
[  2220.856] (II) intel(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
[  2220.856] (II) intel(0): Ranges: V min: 48 V max: 62 Hz, H min: 14 H max: 70 kHz, PixClock max 155 MHz
[  2220.856] (II) intel(0): Monitor name: VSX-921
[  2220.856] (II) intel(0): Supported detailed timing:
[  2220.856] (II) intel(0): clock: 148.5 MHz   Image Size:  1600 x 900 mm
[  2220.856] (II) intel(0): h_active: 1920  h_sync: 2448  h_sync_end 2492 h_blank_end 2640 h_border: 0
[  2220.856] (II) intel(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[  2220.856] (II) intel(0): Supported detailed timing:
[  2220.856] (II) intel(0): clock: 74.2 MHz   Image Size:  1600 x 900 mm
[  2220.856] (II) intel(0): h_active: 1280  h_sync: 1720  h_sync_end 1760 h_blank_end 1980 h_border: 0
[  2220.856] (II) intel(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
[  2220.856] (II) intel(0): Number of EDID sections to follow: 1
[  2220.856] (II) intel(0): EDID (in hex):
[  2220.856] (II) intel(0): 	00ffffffffffff00412f000001010101
[  2220.856] (II) intel(0): 	0014010380a05a780a0dc9a057479827
[  2220.856] (II) intel(0): 	12484c21080081800101010101010101
[  2220.856] (II) intel(0): 	010101010101023a801871382d40582c
[  2220.856] (II) intel(0): 	450040846300001e011d007251d01e20
[  2220.856] (II) intel(0): 	6e28550040846300001e000000fd0030
[  2220.856] (II) intel(0): 	3e0e460f000a202020202020000000fc
[  2220.856] (II) intel(0): 	005653582d3932310a202020202001ad
[  2220.856] (II) intel(0): 	02034af05c1f10140513041211161503
[  2220.856] (II) intel(0): 	02070601201e261d251a190f240e230b
[  2220.856] (II) intel(0): 	0a38097f070f7f071507503e1ec04d02
[  2220.856] (II) intel(0): 	005706005f7e01677e00834f00006803
[  2220.856] (II) intel(0): 	0c001100b82d0fe2007b023a80d07238
[  2220.856] (II) intel(0): 	2d40102c458040846300001e011d00bc
[  2220.856] (II) intel(0): 	52d01e20b828554040846300001e0000
[  2220.856] (II) intel(0): 	00000000000000000000000000000078
[  2220.856] (II) intel(0): Printing probed modes for output HDMI2
[  2220.856] (II) intel(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[  2220.856] (II) intel(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  2220.856] (II) intel(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[  2220.856] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  2220.856] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  2220.856] (II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  2220.904] (II) intel(0): EDID for output DP1
[  2220.952] (II) intel(0): EDID for output DP2
[  2220.952] (II) intel(0): Output VGA1 disconnected
[  2220.952] (II) intel(0): Output HDMI1 disconnected
[  2220.952] (II) intel(0): Output HDMI2 connected
[  2220.952] (II) intel(0): Output DP1 disconnected
[  2220.952] (II) intel(0): Output DP2 disconnected
[  2220.952] (II) intel(0): Using exact sizes for initial modes
[  2220.952] (II) intel(0): Output HDMI2 using initial mode 1920x1080
[  2220.952] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[  2220.952] (==) intel(0): DPI set to (96, 96)
[  2220.952] (II) Loading sub module "dri2"
[  2220.952] (II) LoadModule: "dri2"
[  2220.952] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[  2220.952] (II) Module dri2: vendor="X.Org Foundation"
[  2220.952] 	compiled for 1.11.3, module version = 1.2.0
[  2220.952] 	ABI class: X.Org Server Extension, version 6.0
[  2220.952] (==) Depth 24 pixmap format is 32 bpp
[  2220.952] (II) intel(0): SNA initialized with IvyBridge backend
[  2220.952] (==) intel(0): Backing store disabled
[  2220.952] (==) intel(0): Silken mouse enabled
[  2220.952] (II) intel(0): HW Cursor enabled
[  2220.952] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[  2220.952] (**) intel(0): DPMS enabled
[  2220.952] (II) intel(0): Overlay video not supported on this hardware
[  2220.952] (II) intel(0): [DRI2] Setup complete
[  2220.952] (II) intel(0): [DRI2]   DRI driver: i965
[  2220.952] (II) intel(0): direct rendering: DRI2 Enabled
[  2220.952] (WW) intel(0): Option "FlatPanelProperties" is not used
[  2220.952] (==) intel(0): hotplug detection: "enabled"
[  2220.952] (--) RandR disabled
[  2220.952] (II) Initializing built-in extension Generic Event Extension
[  2220.952] (II) Initializing built-in extension SHAPE
[  2220.952] (II) Initializing built-in extension MIT-SHM
[  2220.952] (II) Initializing built-in extension XInputExtension
[  2220.952] (II) Initializing built-in extension XTEST
[  2220.952] (II) Initializing built-in extension BIG-REQUESTS
[  2220.952] (II) Initializing built-in extension SYNC
[  2220.952] (II) Initializing built-in extension XKEYBOARD
[  2220.952] (II) Initializing built-in extension XC-MISC
[  2220.952] (II) Initializing built-in extension SECURITY
[  2220.952] (II) Initializing built-in extension XINERAMA
[  2220.952] (II) Initializing built-in extension XFIXES
[  2220.952] (II) Initializing built-in extension RENDER
[  2220.952] (II) Initializing built-in extension RANDR
[  2220.952] (II) Initializing built-in extension COMPOSITE
[  2220.952] (II) Initializing built-in extension DAMAGE
[  2220.957] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[  2220.957] (II) AIGLX: enabled GLX_INTEL_swap_event
[  2220.957] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[  2220.957] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[  2220.957] (II) AIGLX: Loaded and initialized i965
[  2220.957] (II) GLX: Initialized DRI2 GL provider for screen 0
[  2220.957] (II) intel(0): switch to mode 1920x1080 on crtc 3 (pipe 0)
[  2221.020] (II) intel(0): Setting screen physical size to 508 x 285
[  2221.027] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[  2221.029] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[  2221.029] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  2221.029] (II) LoadModule: "evdev"
[  2221.029] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  2221.029] (II) Module evdev: vendor="X.Org Foundation"
[  2221.029] 	compiled for 1.11.3, module version = 2.7.0
[  2221.029] 	Module class: X.Org XInput Driver
[  2221.029] 	ABI class: X.Org XInput driver, version 16.0
[  2221.029] (II) Using input driver 'evdev' for 'Power Button'
[  2221.029] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  2221.029] (**) Power Button: always reports core events
[  2221.029] (**) evdev: Power Button: Device: "/dev/input/event1"
[  2221.029] (--) evdev: Power Button: Vendor 0 Product 0x1
[  2221.029] (--) evdev: Power Button: Found keys
[  2221.029] (II) evdev: Power Button: Configuring as keyboard
[  2221.029] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[  2221.029] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[  2221.029] (**) Option "xkb_rules" "evdev"
[  2221.029] (**) Option "xkb_model" "pc105"
[  2221.029] (**) Option "xkb_layout" "us"
[  2221.030] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[  2221.030] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[  2221.030] (II) Using input driver 'evdev' for 'Video Bus'
[  2221.030] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  2221.030] (**) Video Bus: always reports core events
[  2221.030] (**) evdev: Video Bus: Device: "/dev/input/event4"
[  2221.030] (--) evdev: Video Bus: Vendor 0 Product 0x6
[  2221.030] (--) evdev: Video Bus: Found keys
[  2221.030] (II) evdev: Video Bus: Configuring as keyboard
[  2221.030] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input4/event4"
[  2221.030] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[  2221.030] (**) Option "xkb_rules" "evdev"
[  2221.030] (**) Option "xkb_model" "pc105"
[  2221.030] (**) Option "xkb_layout" "us"
[  2221.030] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[  2221.030] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  2221.030] (II) Using input driver 'evdev' for 'Power Button'
[  2221.030] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  2221.030] (**) Power Button: always reports core events
[  2221.030] (**) evdev: Power Button: Device: "/dev/input/event0"
[  2221.030] (--) evdev: Power Button: Vendor 0 Product 0x1
[  2221.030] (--) evdev: Power Button: Found keys
[  2221.030] (II) evdev: Power Button: Configuring as keyboard
[  2221.030] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[  2221.030] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[  2221.030] (**) Option "xkb_rules" "evdev"
[  2221.030] (**) Option "xkb_model" "pc105"
[  2221.030] (**) Option "xkb_layout" "us"
[  2221.031] (II) config/udev: Adding input device FaceCam 1000 (/dev/input/event2)
[  2221.031] (**) FaceCam 1000: Applying InputClass "evdev keyboard catchall"
[  2221.031] (II) Using input driver 'evdev' for 'FaceCam 1000'
[  2221.031] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  2221.031] (**) FaceCam 1000: always reports core events
[  2221.031] (**) evdev: FaceCam 1000: Device: "/dev/input/event2"
[  2221.031] (--) evdev: FaceCam 1000: Vendor 0x458 Product 0x707e
[  2221.031] (--) evdev: FaceCam 1000: Found keys
[  2221.031] (II) evdev: FaceCam 1000: Configuring as keyboard
[  2221.031] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/input/input2/event2"
[  2221.031] (II) XINPUT: Adding extended input device "FaceCam 1000" (type: KEYBOARD, id 9)
[  2221.031] (**) Option "xkb_rules" "evdev"
[  2221.031] (**) Option "xkb_model" "pc105"
[  2221.031] (**) Option "xkb_layout" "us"
[  2221.031] (II) config/udev: Adding input device HDA Intel PCH Line-Out (/dev/input/event10)
[  2221.031] (II) No input driver specified, ignoring this device.
[  2221.031] (II) This device may have been added with another device file.
[  2221.031] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event5)
[  2221.031] (II) No input driver specified, ignoring this device.
[  2221.031] (II) This device may have been added with another device file.
[  2221.032] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event6)
[  2221.032] (II) No input driver specified, ignoring this device.
[  2221.032] (II) This device may have been added with another device file.
[  2221.032] (II) config/udev: Adding input device HDA Intel PCH Front Mic (/dev/input/event7)
[  2221.032] (II) No input driver specified, ignoring this device.
[  2221.032] (II) This device may have been added with another device file.
[  2221.032] (II) config/udev: Adding input device HDA Intel PCH Rear Mic (/dev/input/event8)
[  2221.032] (II) No input driver specified, ignoring this device.
[  2221.032] (II) This device may have been added with another device file.
[  2221.032] (II) config/udev: Adding input device HDA Intel PCH Front Headphone (/dev/input/event9)
[  2221.032] (II) No input driver specified, ignoring this device.
[  2221.032] (II) This device may have been added with another device file.
[  2221.032] (II) config/udev: Adding input device Logitech Cordless MediaBoard Pro(TM) (/dev/input/event11)
[  2221.032] (**) Logitech Cordless MediaBoard Pro(TM): Applying InputClass "evdev pointer catchall"
[  2221.032] (**) Logitech Cordless MediaBoard Pro(TM): Applying InputClass "evdev keyboard catchall"
[  2221.032] (II) Using input driver 'evdev' for 'Logitech Cordless MediaBoard Pro(TM)'
[  2221.032] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  2221.032] (**) Logitech Cordless MediaBoard Pro(TM): always reports core events
[  2221.032] (**) evdev: Logitech Cordless MediaBoard Pro(TM): Device: "/dev/input/event11"
[  2221.032] (--) evdev: Logitech Cordless MediaBoard Pro(TM): Vendor 0x46d Product 0xb30a
[  2221.032] (--) evdev: Logitech Cordless MediaBoard Pro(TM): Found 20 mouse buttons
[  2221.032] (--) evdev: Logitech Cordless MediaBoard Pro(TM): Found scroll wheel(s)
[  2221.032] (--) evdev: Logitech Cordless MediaBoard Pro(TM): Found relative axes
[  2221.032] (--) evdev: Logitech Cordless MediaBoard Pro(TM): Found x and y relative axes
[  2221.033] (--) evdev: Logitech Cordless MediaBoard Pro(TM): Found absolute axes
[  2221.033] (II) evdev: Logitech Cordless MediaBoard Pro(TM): Forcing absolute x/y axes to exist.
[  2221.033] (--) evdev: Logitech Cordless MediaBoard Pro(TM): Found keys
[  2221.033] (II) evdev: Logitech Cordless MediaBoard Pro(TM): Configuring as mouse
[  2221.033] (II) evdev: Logitech Cordless MediaBoard Pro(TM): Configuring as keyboard
[  2221.033] (II) evdev: Logitech Cordless MediaBoard Pro(TM): Adding scrollwheel support
[  2221.033] (**) evdev: Logitech Cordless MediaBoard Pro(TM): YAxisMapping: buttons 4 and 5
[  2221.033] (**) evdev: Logitech Cordless MediaBoard Pro(TM): EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  2221.033] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1e.0/0000:04:01.2/usb6/6-2/6-2:1.0/bluetooth/hci0/hci0:3/input13/event11"
[  2221.033] (II) XINPUT: Adding extended input device "Logitech Cordless MediaBoard Pro(TM)" (type: KEYBOARD, id 10)
[  2221.033] (**) Option "xkb_rules" "evdev"
[  2221.033] (**) Option "xkb_model" "pc105"
[  2221.033] (**) Option "xkb_layout" "us"
[  2221.033] (II) evdev: Logitech Cordless MediaBoard Pro(TM): initialized for relative axes.
[  2221.033] (WW) evdev: Logitech Cordless MediaBoard Pro(TM): ignoring absolute axes.
[  2221.033] (**) Logitech Cordless MediaBoard Pro(TM): (accel) keeping acceleration scheme 1
[  2221.033] (**) Logitech Cordless MediaBoard Pro(TM): (accel) acceleration profile 0
[  2221.033] (**) Logitech Cordless MediaBoard Pro(TM): (accel) acceleration factor: 2.000
[  2221.033] (**) Logitech Cordless MediaBoard Pro(TM): (accel) acceleration threshold: 4
[  2221.033] (II) config/udev: Adding input device Logitech Cordless MediaBoard Pro(TM) (/dev/input/mouse0)
[  2221.033] (II) No input driver specified, ignoring this device.
[  2221.033] (II) This device may have been added with another device file.
[  2221.033] (II) config/udev: Adding input device Eee PC WMI hotkeys (/dev/input/event3)
[  2221.033] (**) Eee PC WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[  2221.033] (II) Using input driver 'evdev' for 'Eee PC WMI hotkeys'
[  2221.033] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  2221.033] (**) Eee PC WMI hotkeys: always reports core events
[  2221.033] (**) evdev: Eee PC WMI hotkeys: Device: "/dev/input/event3"
[  2221.033] (--) evdev: Eee PC WMI hotkeys: Vendor 0 Product 0
[  2221.033] (--) evdev: Eee PC WMI hotkeys: Found keys
[  2221.033] (II) evdev: Eee PC WMI hotkeys: Configuring as keyboard
[  2221.033] (**) Option "config_info" "udev:/sys/devices/platform/eeepc-wmi/input/input3/event3"
[  2221.033] (II) XINPUT: Adding extended input device "Eee PC WMI hotkeys" (type: KEYBOARD, id 11)
[  2221.033] (**) Option "xkb_rules" "evdev"
[  2221.033] (**) Option "xkb_model" "pc105"
[  2221.033] (**) Option "xkb_layout" "us"
[  2221.828] (II) intel(0): EDID vendor "PIO", prod id 0
[  2221.828] (II) intel(0): Using hsync ranges from config file
[  2221.828] (II) intel(0): Using vrefresh ranges from config file
[  2221.828] (II) intel(0): Printing DDC gathered Modelines:
[  2221.828] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[  2221.828] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[  2221.828] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz)
[  2221.828] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[  2221.828] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  2221.828] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  2221.828] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  2221.828] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  2221.828] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz)
[  2221.828] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[  2221.828] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[  2221.828] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[  2221.828] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
[  2221.828] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[  2221.828] (II) intel(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz)
[  2221.828] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[  2221.828] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[  2221.828] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (28.1 kHz)
[  2221.828] (II) intel(0): Modeline "1920x1080i"x0.0   72.00  1920 1952 2120 2304  1080 1126 1136 1250 interlace +hsync -vsync (31.2 kHz)
[  2221.828] (II) intel(0): Modeline "1440x576"x0.0   54.00  1440 1464 1592 1728  576 581 586 625 -hsync -vsync (31.2 kHz)
[  2221.828] (II) intel(0): Modeline "2880x576"x0.0  108.00  2880 2928 3184 3456  576 581 586 625 -hsync -vsync (31.2 kHz)
[  2221.828] (II) intel(0): Modeline "2880x288"x0.0   54.00  2880 2928 3180 3456  288 290 293 312 -hsync -vsync (15.6 kHz)
[  2221.828] (II) intel(0): Modeline "2880x576i"x0.0   54.00  2880 2928 3180 3456  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[  2221.828] (II) intel(0): Modeline "1440x480"x0.0   54.00  1440 1472 1596 1716  480 489 495 525 -hsync -vsync (31.5 kHz)
[  2221.828] (II) intel(0): Modeline "2880x480"x0.0  108.00  2880 2944 3192 3432  480 489 495 525 -hsync -vsync (31.5 kHz)
[  2221.828] (II) intel(0): Modeline "2880x240"x0.0   54.00  2880 2956 3204 3432  240 244 247 262 -hsync -vsync (15.7 kHz)
[  2221.828] (II) intel(0): Modeline "2880x480i"x0.0   54.00  2880 2956 3204 3432  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[  2222.006] (II) XKB: reuse xkmfile /var/lib/xkb/server-03AF3717FF3AB439A4BAABA686CCB40771CDF520.xkm
[  2222.736] (II) intel(0): EDID vendor "PIO", prod id 0
[  2222.736] (II) intel(0): Using hsync ranges from config file
[  2222.736] (II) intel(0): Using vrefresh ranges from config file
[  2222.736] (II) intel(0): Printing DDC gathered Modelines:
[  2222.736] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[  2222.736] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[  2222.736] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz)
[  2222.736] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[  2222.736] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  2222.736] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  2222.736] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  2222.736] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  2222.736] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz)
[  2222.736] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[  2222.736] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[  2222.736] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[  2222.736] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
[  2222.736] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[  2222.736] (II) intel(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz)
[  2222.736] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[  2222.736] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[  2222.736] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (28.1 kHz)
[  2222.736] (II) intel(0): Modeline "1920x1080i"x0.0   72.00  1920 1952 2120 2304  1080 1126 1136 1250 interlace +hsync -vsync (31.2 kHz)
[  2222.736] (II) intel(0): Modeline "1440x576"x0.0   54.00  1440 1464 1592 1728  576 581 586 625 -hsync -vsync (31.2 kHz)
[  2222.736] (II) intel(0): Modeline "2880x576"x0.0  108.00  2880 2928 3184 3456  576 581 586 625 -hsync -vsync (31.2 kHz)
[  2222.736] (II) intel(0): Modeline "2880x288"x0.0   54.00  2880 2928 3180 3456  288 290 293 312 -hsync -vsync (15.6 kHz)
[  2222.736] (II) intel(0): Modeline "2880x576i"x0.0   54.00  2880 2928 3180 3456  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[  2222.736] (II) intel(0): Modeline "1440x480"x0.0   54.00  1440 1472 1596 1716  480 489 495 525 -hsync -vsync (31.5 kHz)
[  2222.736] (II) intel(0): Modeline "2880x480"x0.0  108.00  2880 2944 3192 3432  480 489 495 525 -hsync -vsync (31.5 kHz)
[  2222.736] (II) intel(0): Modeline "2880x240"x0.0   54.00  2880 2956 3204 3432  240 244 247 262 -hsync -vsync (15.7 kHz)
[  2222.736] (II) intel(0): Modeline "2880x480i"x0.0   54.00  2880 2956 3204 3432  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[  2223.085] (II) intel(0): EDID vendor "PIO", prod id 0
[  2223.085] (II) intel(0): Using hsync ranges from config file
[  2223.085] (II) intel(0): Using vrefresh ranges from config file
[  2223.085] (II) intel(0): Printing DDC gathered Modelines:
[  2223.085] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[  2223.085] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[  2223.085] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz)
[  2223.085] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[  2223.085] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  2223.085] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  2223.085] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  2223.085] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  2223.085] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz)
[  2223.085] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[  2223.085] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[  2223.085] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[  2223.085] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
[  2223.085] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[  2223.085] (II) intel(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz)
[  2223.085] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[  2223.085] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[  2223.085] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (28.1 kHz)
[  2223.085] (II) intel(0): Modeline "1920x1080i"x0.0   72.00  1920 1952 2120 2304  1080 1126 1136 1250 interlace +hsync -vsync (31.2 kHz)
[  2223.085] (II) intel(0): Modeline "1440x576"x0.0   54.00  1440 1464 1592 1728  576 581 586 625 -hsync -vsync (31.2 kHz)
[  2223.085] (II) intel(0): Modeline "2880x576"x0.0  108.00  2880 2928 3184 3456  576 581 586 625 -hsync -vsync (31.2 kHz)
[  2223.085] (II) intel(0): Modeline "2880x288"x0.0   54.00  2880 2928 3180 3456  288 290 293 312 -hsync -vsync (15.6 kHz)
[  2223.085] (II) intel(0): Modeline "2880x576i"x0.0   54.00  2880 2928 3180 3456  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[  2223.085] (II) intel(0): Modeline "1440x480"x0.0   54.00  1440 1472 1596 1716  480 489 495 525 -hsync -vsync (31.5 kHz)
[  2223.085] (II) intel(0): Modeline "2880x480"x0.0  108.00  2880 2944 3192 3432  480 489 495 525 -hsync -vsync (31.5 kHz)
[  2223.085] (II) intel(0): Modeline "2880x240"x0.0   54.00  2880 2956 3204 3432  240 244 247 262 -hsync -vsync (15.7 kHz)
[  2223.085] (II) intel(0): Modeline "2880x480i"x0.0   54.00  2880 2956 3204 3432  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[  2223.579] (II) intel(0): EDID vendor "PIO", prod id 0
[  2223.579] (II) intel(0): Using hsync ranges from config file
[  2223.579] (II) intel(0): Using vrefresh ranges from config file
[  2223.579] (II) intel(0): Printing DDC gathered Modelines:
[  2223.579] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[  2223.579] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[  2223.579] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz)
[  2223.579] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[  2223.579] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  2223.579] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  2223.579] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  2223.579] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  2223.579] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz)
[  2223.579] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[  2223.579] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[  2223.579] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[  2223.579] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
[  2223.579] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[  2223.579] (II) intel(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz)
[  2223.579] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[  2223.579] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[  2223.579] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (28.1 kHz)
[  2223.579] (II) intel(0): Modeline "1920x1080i"x0.0   72.00  1920 1952 2120 2304  1080 1126 1136 1250 interlace +hsync -vsync (31.2 kHz)
[  2223.579] (II) intel(0): Modeline "1440x576"x0.0   54.00  1440 1464 1592 1728  576 581 586 625 -hsync -vsync (31.2 kHz)
[  2223.579] (II) intel(0): Modeline "2880x576"x0.0  108.00  2880 2928 3184 3456  576 581 586 625 -hsync -vsync (31.2 kHz)
[  2223.579] (II) intel(0): Modeline "2880x288"x0.0   54.00  2880 2928 3180 3456  288 290 293 312 -hsync -vsync (15.6 kHz)
[  2223.579] (II) intel(0): Modeline "2880x576i"x0.0   54.00  2880 2928 3180 3456  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[  2223.579] (II) intel(0): Modeline "1440x480"x0.0   54.00  1440 1472 1596 1716  480 489 495 525 -hsync -vsync (31.5 kHz)
[  2223.579] (II) intel(0): Modeline "2880x480"x0.0  108.00  2880 2944 3192 3432  480 489 495 525 -hsync -vsync (31.5 kHz)
[  2223.579] (II) intel(0): Modeline "2880x240"x0.0   54.00  2880 2956 3204 3432  240 244 247 262 -hsync -vsync (15.7 kHz)
[  2223.579] (II) intel(0): Modeline "2880x480i"x0.0   54.00  2880 2956 3204 3432  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[  2229.280] (II) AIGLX: Suspending AIGLX clients for VT switch
[  2241.974] (II) Open ACPI successful (/var/run/acpid.socket)
[  2241.974] (II) AIGLX: Resuming AIGLX clients after VT switch
[  2241.974] (II) intel(0): switch to mode 1920x1080 on crtc 3 (pipe 0)
[  2242.267] (II) intel(0): EDID vendor "PIO", prod id 0
[  2242.267] (II) intel(0): Using hsync ranges from config file
[  2242.267] (II) intel(0): Using vrefresh ranges from config file
[  2242.267] (II) intel(0): Printing DDC gathered Modelines:
[  2242.267] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[  2242.267] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[  2242.267] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz)
[  2242.267] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[  2242.267] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  2242.267] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  2242.267] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  2242.267] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  2242.267] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz)
[  2242.267] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[  2242.267] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[  2242.267] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[  2242.267] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
[  2242.267] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[  2242.267] (II) intel(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz)
[  2242.267] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[  2242.267] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[  2242.267] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (28.1 kHz)
[  2242.267] (II) intel(0): Modeline "1920x1080i"x0.0   72.00  1920 1952 2120 2304  1080 1126 1136 1250 interlace +hsync -vsync (31.2 kHz)
[  2242.267] (II) intel(0): Modeline "1440x576"x0.0   54.00  1440 1464 1592 1728  576 581 586 625 -hsync -vsync (31.2 kHz)
[  2242.267] (II) intel(0): Modeline "2880x576"x0.0  108.00  2880 2928 3184 3456  576 581 586 625 -hsync -vsync (31.2 kHz)
[  2242.267] (II) intel(0): Modeline "2880x288"x0.0   54.00  2880 2928 3180 3456  288 290 293 312 -hsync -vsync (15.6 kHz)
[  2242.267] (II) intel(0): Modeline "2880x576i"x0.0   54.00  2880 2928 3180 3456  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[  2242.267] (II) intel(0): Modeline "1440x480"x0.0   54.00  1440 1472 1596 1716  480 489 495 525 -hsync -vsync (31.5 kHz)
[  2242.267] (II) intel(0): Modeline "2880x480"x0.0  108.00  2880 2944 3192 3432  480 489 495 525 -hsync -vsync (31.5 kHz)
[  2242.267] (II) intel(0): Modeline "2880x240"x0.0   54.00  2880 2956 3204 3432  240 244 247 262 -hsync -vsync (15.7 kHz)
[  2242.267] (II) intel(0): Modeline "2880x480i"x0.0   54.00  2880 2956 3204 3432  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[  2242.667] (II) intel(0): EDID vendor "PIO", prod id 0
[  2242.667] (II) intel(0): Using hsync ranges from config file
[  2242.667] (II) intel(0): Using vrefresh ranges from config file
[  2242.667] (II) intel(0): Printing DDC gathered Modelines:
[  2242.667] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[  2242.667] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[  2242.667] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz)
[  2242.667] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[  2242.667] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  2242.667] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  2242.667] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  2242.667] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  2242.667] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz)
[  2242.667] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[  2242.667] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[  2242.667] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[  2242.667] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
[  2242.667] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[  2242.667] (II) intel(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz)
[  2242.667] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[  2242.667] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[  2242.667] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (28.1 kHz)
[  2242.667] (II) intel(0): Modeline "1920x1080i"x0.0   72.00  1920 1952 2120 2304  1080 1126 1136 1250 interlace +hsync -vsync (31.2 kHz)
[  2242.667] (II) intel(0): Modeline "1440x576"x0.0   54.00  1440 1464 1592 1728  576 581 586 625 -hsync -vsync (31.2 kHz)
[  2242.667] (II) intel(0): Modeline "2880x576"x0.0  108.00  2880 2928 3184 3456  576 581 586 625 -hsync -vsync (31.2 kHz)
[  2242.667] (II) intel(0): Modeline "2880x288"x0.0   54.00  2880 2928 3180 3456  288 290 293 312 -hsync -vsync (15.6 kHz)
[  2242.667] (II) intel(0): Modeline "2880x576i"x0.0   54.00  2880 2928 3180 3456  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[  2242.667] (II) intel(0): Modeline "1440x480"x0.0   54.00  1440 1472 1596 1716  480 489 495 525 -hsync -vsync (31.5 kHz)
[  2242.667] (II) intel(0): Modeline "2880x480"x0.0  108.00  2880 2944 3192 3432  480 489 495 525 -hsync -vsync (31.5 kHz)
[  2242.667] (II) intel(0): Modeline "2880x240"x0.0   54.00  2880 2956 3204 3432  240 244 247 262 -hsync -vsync (15.7 kHz)
[  2242.667] (II) intel(0): Modeline "2880x480i"x0.0   54.00  2880 2956 3204 3432  480 488 494 525 interlace -hsync -vsync (15.7 kHz)

```

---

### Post by gerpc on 2013-01-25
lspci -vv

```

00:00.0 Host bridge: Intel Corporation Ivy Bridge DRAM Controller (rev 09)
	Subsystem: ASUSTeK Computer Inc. Device 84ca
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
	Latency: 0
	Capabilities: [e0] Vendor Specific Information: Len=0c <?>
	Kernel driver in use: agpgart-intel

00:01.0 PCI bridge: Intel Corporation Ivy Bridge PCI Express Root Port (rev 09) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: [88] Subsystem: ASUSTeK Computer Inc. Device 84ca
	Capabilities: [80] Power Management version 3
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
		Address: fee0f00c  Data: 4161
	Capabilities: [a0] Express (v2) Root Port (Slot+), MSI 00
		DevCap:	MaxPayload 256 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
			ExtTag- RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
			MaxPayload 256 bytes, MaxReadReq 128 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
		LnkCap:	Port #2, Speed 5GT/s, Width x16, ASPM L0s L1, Latency L0 <1us, L1 <8us
			ClockPM- Surprise- LLActRep- BwNot+
		LnkCtl:	ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk-
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x0, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
		SltCap:	AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug- Surprise-
			Slot #1, PowerLimit 75.000W; Interlock- NoCompl+
		SltCtl:	Enable: AttnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq- LinkChg-
			Control: AttnInd Unknown, PwrInd Unknown, Power- Interlock-
		SltSta:	Status: AttnBtn- PowerFlt- MRL- CmdCplt- PresDet- Interlock-
			Changed: MRL- PresDet- LinkState-
		RootCtl: ErrCorrectable- ErrNon-Fatal- ErrFatal- PMEIntEna- CRSVisible-
		RootCap: CRSVisible-
		RootSta: PME ReqID 0000, PMEStatus- PMEPending-
		DevCap2: Completion Timeout: Not Supported, TimeoutDis- ARIFwd-
		DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis- ARIFwd-
		LnkCtl2: Target Link Speed: 2.5GT/s, EnterCompliance- SpeedDis-, Selectable De-emphasis: -6dB
			 Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
			 Compliance De-emphasis: -6dB
		LnkSta2: Current De-emphasis Level: -6dB
	Capabilities: [100 v1] Virtual Channel
		Caps:	LPEVC=0 RefClk=100ns PATEntryBits=1
		Arb:	Fixed- WRR32- WRR64- WRR128-
		Ctrl:	ArbSelect=Fixed
		Status:	InProgress-
		VC0:	Caps:	PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
			Arb:	Fixed+ WRR32- WRR64- WRR128- TWRR128- WRR256-
			Ctrl:	Enable+ ID=0 ArbSelect=Fixed TC/VC=ff
			Status:	NegoPending- InProgress-
	Capabilities: [140 v1] Root Complex Link
		Desc:	PortNumber=02 ComponentID=01 EltType=Config
		Link0:	Desc:	TargetPort=00 TargetComponent=01 AssocRCRB- LinkType=MemMapped LinkValid+
			Addr:	00000000fed19000
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09) (prog-if 00 [VGA controller])
	Subsystem: ASUSTeK Computer Inc. Device 84ca
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 44
	Region 0: Memory at f7800000 (64-bit, non-prefetchable) [size=4M]
	Region 2: Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Region 4: I/O ports at f000 [size=64]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
		Address: fee0a00c  Data: 4189
	Capabilities: [d0] Power Management version 2
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [a4] PCI Advanced Features
		AFCap: TP+ FLR+
		AFCtrl: FLR-
		AFStatus: TP-
	Kernel driver in use: i915
	Kernel modules: i915

00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04) (prog-if 30 [XHCI])
	Subsystem: ASUSTeK Computer Inc. Device 84ca
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 41
	Region 0: Memory at f7d00000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: [70] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0-,D1-,D2-,D3hot+,D3cold+)
		Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [80] MSI: Enable+ Count=1/8 Maskable- 64bit+
		Address: 00000000fee0f00c  Data: 4169
	Kernel driver in use: xhci_hcd

00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
	Subsystem: ASUSTeK Computer Inc. Device 84ca
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 43
	Region 0: Memory at f7d1a000 (64-bit, non-prefetchable) [size=16]
	Capabilities: [50] Power Management version 3
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [8c] MSI: Enable+ Count=1/1 Maskable- 64bit+
		Address: 00000000fee0f00c  Data: 4181
	Kernel driver in use: mei
	Kernel modules: mei

00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04) (prog-if 20 [EHCI])
	Subsystem: ASUSTeK Computer Inc. Device 84ca
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 23
	Region 0: Memory at f7d17000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Capabilities: [98] PCI Advanced Features
		AFCap: TP+ FLR+
		AFCtrl: FLR-
		AFStatus: TP-
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
	Subsystem: ASUSTeK Computer Inc. Device 8415
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 45
	Region 0: Memory at f7d10000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=55mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
		Address: 00000000fee0500c  Data: 4199
	Capabilities: [70] Express (v1) Root Complex Integrated Endpoint, MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
			ExtTag- RBE- FLReset+
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
			MaxPayload 128 bytes, MaxReadReq 128 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr+ TransPend-
		LnkCap:	Port #0, Speed unknown, Width x0, ASPM unknown, Latency L0 <64ns, L1 <1us
			ClockPM- Surprise- LLActRep- BwNot-
		LnkCtl:	ASPM Disabled; Disabled- Retrain- CommClk-
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed unknown, Width x0, TrErr- Train- SlotClk- DLActive- BWMgmt- ABWMgmt-
	Capabilities: [100 v1] Virtual Channel
		Caps:	LPEVC=0 RefClk=100ns PATEntryBits=1
		Arb:	Fixed- WRR32- WRR64- WRR128-
		Ctrl:	ArbSelect=Fixed
		Status:	InProgress-
		VC0:	Caps:	PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
			Arb:	Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
			Ctrl:	Enable+ ID=0 ArbSelect=Fixed TC/VC=01
			Status:	NegoPending- InProgress-
		VC1:	Caps:	PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
			Arb:	Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
			Ctrl:	Enable+ ID=1 ArbSelect=Fixed TC/VC=22
			Status:	NegoPending- InProgress-
	Capabilities: [130 v1] Root Complex Link
		Desc:	PortNumber=0f ComponentID=00 EltType=Config
		Link0:	Desc:	TargetPort=00 TargetComponent=00 AssocRCRB- LinkType=MemMapped LinkValid+
			Addr:	00000000fed1c000
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: [40] Express (v2) Root Port (Slot+), MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
			ExtTag- RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
			MaxPayload 128 bytes, MaxReadReq 128 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr+ TransPend-
		LnkCap:	Port #1, Speed 5GT/s, Width x4, ASPM L0s L1, Latency L0 <1us, L1 <16us
			ClockPM- Surprise- LLActRep+ BwNot-
		LnkCtl:	ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk-
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x0, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
		SltCap:	AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug- Surprise-
			Slot #0, PowerLimit 25.000W; Interlock- NoCompl+
		SltCtl:	Enable: AttnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq- LinkChg-
			Control: AttnInd Unknown, PwrInd Unknown, Power- Interlock-
		SltSta:	Status: AttnBtn- PowerFlt- MRL- CmdCplt- PresDet- Interlock-
			Changed: MRL- PresDet- LinkState-
		RootCtl: ErrCorrectable- ErrNon-Fatal- ErrFatal- PMEIntEna- CRSVisible-
		RootCap: CRSVisible-
		RootSta: PME ReqID 0000, PMEStatus- PMEPending-
		DevCap2: Completion Timeout: Range BC, TimeoutDis+ ARIFwd-
		DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis- ARIFwd-
		LnkCtl2: Target Link Speed: 2.5GT/s, EnterCompliance- SpeedDis-, Selectable De-emphasis: -6dB
			 Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
			 Compliance De-emphasis: -6dB
		LnkSta2: Current De-emphasis Level: -3.5dB
	Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
		Address: 00000000  Data: 0000
	Capabilities: [90] Subsystem: ASUSTeK Computer Inc. Device 84ca
	Capabilities: [a0] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 5 (rev c4) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Prefetchable memory behind bridge: 00000000f0000000-00000000f00fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: [40] Express (v2) Root Port (Slot+), MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
			ExtTag- RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
			MaxPayload 128 bytes, MaxReadReq 128 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr+ TransPend-
		LnkCap:	Port #5, Speed 5GT/s, Width x1, ASPM L0s L1, Latency L0 <512ns, L1 <16us
			ClockPM- Surprise- LLActRep+ BwNot-
		LnkCtl:	ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk+
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive+ BWMgmt+ ABWMgmt-
		SltCap:	AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug- Surprise-
			Slot #4, PowerLimit 10.000W; Interlock- NoCompl+
		SltCtl:	Enable: AttnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq- LinkChg-
			Control: AttnInd Unknown, PwrInd Unknown, Power- Interlock-
		SltSta:	Status: AttnBtn- PowerFlt- MRL- CmdCplt- PresDet+ Interlock-
			Changed: MRL- PresDet- LinkState-
		RootCtl: ErrCorrectable- ErrNon-Fatal- ErrFatal- PMEIntEna- CRSVisible-
		RootCap: CRSVisible-
		RootSta: PME ReqID 0000, PMEStatus- PMEPending-
		DevCap2: Completion Timeout: Range BC, TimeoutDis+ ARIFwd-
		DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis- ARIFwd-
		LnkCtl2: Target Link Speed: 5GT/s, EnterCompliance- SpeedDis-, Selectable De-emphasis: -6dB
			 Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
			 Compliance De-emphasis: -6dB
		LnkSta2: Current De-emphasis Level: -3.5dB
	Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
		Address: 00000000  Data: 0000
	Capabilities: [90] Subsystem: ASUSTeK Computer Inc. Device 84ca
	Capabilities: [a0] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04) (prog-if 20 [EHCI])
	Subsystem: ASUSTeK Computer Inc. Device 84ca
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 23
	Region 0: Memory at f7d16000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Capabilities: [98] PCI Advanced Features
		AFCap: TP+ FLR+
		AFCtrl: FLR-
		AFStatus: TP-
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a4) (prog-if 01 [Subtractive decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
	Memory behind bridge: f7c00000-f7cfffff
	Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: [50] Subsystem: ASUSTeK Computer Inc. Device 84ca

00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
	Subsystem: ASUSTeK Computer Inc. Device 84ca
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Capabilities: [e0] Vendor Specific Information: Len=0c <?>
	Kernel modules: iTCO_wdt

00:1f.2 IDE interface: Intel Corporation Panther Point 4 port SATA Controller [IDE mode] (rev 04) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: ASUSTeK Computer Inc. Device 84ca
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin B routed to IRQ 19
	Region 0: I/O ports at f110 [size=8]
	Region 1: I/O ports at f100 [size=4]
	Region 2: I/O ports at f0f0 [size=8]
	Region 3: I/O ports at f0e0 [size=4]
	Region 4: I/O ports at f0d0 [size=16]
	Region 5: I/O ports at f0c0 [size=16]
	Capabilities: [70] Power Management version 3
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [b0] PCI Advanced Features
		AFCap: TP+ FLR+
		AFCtrl: FLR-
		AFStatus: TP-
	Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
	Subsystem: ASUSTeK Computer Inc. Device 84ca
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin C routed to IRQ 6
	Region 0: Memory at f7d15000 (64-bit, non-prefetchable) [size=256]
	Region 4: I/O ports at f040 [size=32]
	Kernel modules: i2c-i801

00:1f.5 IDE interface: Intel Corporation Panther Point 2 port SATA Controller [IDE mode] (rev 04) (prog-if 85 [Master SecO PriO])
	Subsystem: ASUSTeK Computer Inc. Device 84ca
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin B routed to IRQ 19
	Region 0: I/O ports at f0b0 [size=8]
	Region 1: I/O ports at f0a0 [size=4]
	Region 2: I/O ports at f090 [size=8]
	Region 3: I/O ports at f080 [size=4]
	Region 4: I/O ports at f070 [size=16]
	Region 5: I/O ports at f060 [size=16]
	Capabilities: [70] Power Management version 3
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [b0] PCI Advanced Features
		AFCap: TP+ FLR+
		AFCtrl: FLR-
		AFStatus: TP-
	Kernel driver in use: ata_piix

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 09)
	Subsystem: ASUSTeK Computer Inc. Device 8505
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 42
	Region 0: I/O ports at e000 [size=256]
	Region 2: Memory at f0004000 (64-bit, prefetchable) [size=4K]
	Region 4: Memory at f0000000 (64-bit, prefetchable) [size=16K]
	Capabilities: [40] Power Management version 3
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
		Address: 00000000fee0100c  Data: 4171
	Capabilities: [70] Express (v2) Endpoint, MSI 01
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <512ns, L1 <64us
			ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
			MaxPayload 128 bytes, MaxReadReq 4096 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr+ TransPend-
		LnkCap:	Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 unlimited, L1 <64us
			ClockPM+ Surprise- LLActRep- BwNot-
		LnkCtl:	ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk+
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
		DevCap2: Completion Timeout: Range ABCD, TimeoutDis+
		DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis-
		LnkCtl2: Target Link Speed: 2.5GT/s, EnterCompliance- SpeedDis-, Selectable De-emphasis: -6dB
			 Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
			 Compliance De-emphasis: -6dB
		LnkSta2: Current De-emphasis Level: -6dB
	Capabilities: [b0] MSI-X: Enable- Count=4 Masked-
		Vector table: BAR=4 offset=00000000
		PBA: BAR=4 offset=00000800
	Capabilities: [d0] Vital Product Data
		No end tag found
	Capabilities: [100 v1] Advanced Error Reporting
		UESta:	DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
		UEMsk:	DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
		UESvrt:	DLP+ SDES+ TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
		CESta:	RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr-
		CEMsk:	RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
		AERCap:	First Error Pointer: 00, GenCap+ CGenEn- ChkCap+ ChkEn-
	Capabilities: [140 v1] Virtual Channel
		Caps:	LPEVC=0 RefClk=100ns PATEntryBits=1
		Arb:	Fixed- WRR32- WRR64- WRR128-
		Ctrl:	ArbSelect=Fixed
		Status:	InProgress-
		VC0:	Caps:	PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
			Arb:	Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
			Ctrl:	Enable+ ID=0 ArbSelect=Fixed TC/VC=01
			Status:	NegoPending- InProgress-
	Capabilities: [160 v1] Device Serial Number 00-00-00-00-00-00-00-00
	Kernel driver in use: r8169
	Kernel modules: r8169

04:01.0 USB controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-if 10 [OHCI])
	Subsystem: ALi Corporation ASRock 939Dual-SATA2 Motherboard
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32 (20000ns max)
	Interrupt: pin B routed to IRQ 18
	Region 0: Memory at f7c03000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [60] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1+,D2-,D3hot+,D3cold+)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: ohci_hcd

04:01.1 USB controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-if 10 [OHCI])
	Subsystem: ALi Corporation ASRock 939Dual-SATA2 Motherboard
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32 (20000ns max)
	Interrupt: pin C routed to IRQ 19
	Region 0: Memory at f7c02000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [60] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1+,D2-,D3hot+,D3cold+)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: ohci_hcd

04:01.2 USB controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-if 10 [OHCI])
	Subsystem: ALi Corporation ASRock 939Dual-SATA2 Motherboard
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32 (20000ns max)
	Interrupt: pin D routed to IRQ 16
	Region 0: Memory at f7c01000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [60] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1+,D2-,D3hot+,D3cold+)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME+
	Kernel driver in use: ohci_hcd

04:01.3 USB controller: ALi Corporation USB 2.0 Controller (rev 01) (prog-if 20 [EHCI])
	Subsystem: ALi Corporation ASRock 939Dual-SATA2 Motherboard
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32 (20000ns max), Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at f7c00000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [58] Debug port: BAR=1 offset=0090
	Kernel driver in use: ehci_hcd


```

---

