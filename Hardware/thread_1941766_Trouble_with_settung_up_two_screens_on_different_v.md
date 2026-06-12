---
title: "Trouble with settung up two screens on different video cards."
date: 2012-03-16
forum: Hardware
---

### Post by vbabaev on 2012-03-16
Hi, I have two video cards and two monitrors, so I'm trying to set them up to work.

At first. My devices:

```
# lshw -c video
  *-display               
       description: VGA compatible controller
       product: Cedar PRO [Radeon HD 5450]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:48 memory:c0000000-cfffffff memory:fe520000-fe53ffff ioport:e000(size=256) memory:fe500000-fe51ffff
  *-display
       description: Display controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list
       configuration: driver=i915 latency=0
       resources: irq:45 memory:fe000000-fe3fffff memory:b0000000-bfffffff ioport:f000(size=64)
```

I wrote simple xorg.conf

```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "screen2" 0 0
#	Screen      1  "screen1" RightOf "screen2"
EndSection

Section "Monitor"
	Identifier  "monitor0"
	Option	    "VendorName" "Kraftway"
	Option	    "ModelName" "Generic Autodetecting Monitor"
EndSection

Section "Monitor"
	Identifier  "monitor1"
	Option	    "VendorName" "ViewSonic"
	Option	    "ModelName" "Generic Autodetecting Monitor"
EndSection

Section "Device"
	Identifier  "ati"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "intel-card"
	Driver      "intel"
	BusID       "PCI:0:2:0"
EndSection

Section "Screen"
	Identifier "screen1"
	Device	   "intel-card"
	Monitor    "monitor0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "screen2"
	Device     "ati"
	Monitor    "monitor1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection
```

When I'm using only first or second screen everything is ok, but, when I'm trying to use them both, xorg-server falls down with the segmentation fault error.

```
[   327.023] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[   327.025] X Protocol Version 11, Revision 0
[   327.026] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[   327.027] Current Operating System: Linux vbabaev-work 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686
[   327.027] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic root=UUID=4af811c0-50da-4c23-b728-99891363e8c9 ro quiet splash vt.handoff=7
[   327.028] Build Date: 19 October 2011  05:09:41AM
[   327.029] xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see http://www.ubuntu.com/support) 
[   327.030] Current version of pixman: 0.22.2
[   327.030] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[   327.032] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   327.035] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Mar 16 13:08:45 2012
[   327.035] (++) Using config file: "xorg.conf"
[   327.036] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   327.037] (==) ServerLayout "aticonfig Layout"
[   327.037] (**) |-->Screen "screen1" (0)
[   327.037] (**) |   |-->Monitor "aticonfig-Monitor[0]-0"
[   327.038] (**) |   |-->Device "intel-card"
[   327.038] (**) |-->Screen "screen2" (1)
[   327.038] (**) |   |-->Monitor "aticonfig-Monitor[0]-1"
[   327.038] (**) |   |-->Device "ati"
[   327.038] (==) Automatically adding devices
[   327.038] (==) Automatically enabling devices
[   327.038] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   327.038] 	Entry deleted from font path.
[   327.038] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   327.038] 	Entry deleted from font path.
[   327.038] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   327.038] 	Entry deleted from font path.
[   327.038] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   327.038] 	Entry deleted from font path.
[   327.038] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   327.038] 	Entry deleted from font path.
[   327.038] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[   327.038] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   327.038] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[   327.038] (II) Loader magic: 0x823ada0
[   327.038] (II) Module ABI versions:
[   327.038] 	X.Org ANSI C Emulation: 0.4
[   327.038] 	X.Org Video Driver: 10.0
[   327.038] 	X.Org XInput driver : 12.3
[   327.038] 	X.Org Server Extension : 5.0
[   327.038] (--) PCI: (0:0:2:0) 8086:0102:17aa:307c rev 9, Mem @ 0xfe000000/4194304, 0xb0000000/268435456, I/O @ 0x0000f000/64
[   327.038] (--) PCI:*(0:1:0:0) 1002:68f9:1462:2181 rev 0, Mem @ 0xc0000000/268435456, 0xfe520000/131072, I/O @ 0x0000e000/256, BIOS @ 0x????????/131072
[   327.038] (II) Open ACPI successful (/var/run/acpid.socket)
[   327.038] (II) "extmod" will be loaded by default.
[   327.038] (II) "dbe" will be loaded by default.
[   327.038] (II) "glx" will be loaded by default.
[   327.038] (II) "record" will be loaded by default.
[   327.038] (II) "dri" will be loaded by default.
[   327.038] (II) "dri2" will be loaded by default.
[   327.038] (II) LoadModule: "extmod"
[   327.039] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   327.039] (II) Module extmod: vendor="X.Org Foundation"
[   327.039] 	compiled for 1.10.4, module version = 1.0.0
[   327.039] 	Module class: X.Org Server Extension
[   327.039] 	ABI class: X.Org Server Extension, version 5.0
[   327.039] (II) Loading extension MIT-SCREEN-SAVER
[   327.039] (II) Loading extension XFree86-VidModeExtension
[   327.039] (II) Loading extension XFree86-DGA
[   327.039] (II) Loading extension DPMS
[   327.039] (II) Loading extension XVideo
[   327.039] (II) Loading extension XVideo-MotionCompensation
[   327.039] (II) Loading extension X-Resource
[   327.039] (II) LoadModule: "dbe"
[   327.040] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   327.040] (II) Module dbe: vendor="X.Org Foundation"
[   327.040] 	compiled for 1.10.4, module version = 1.0.0
[   327.040] 	Module class: X.Org Server Extension
[   327.040] 	ABI class: X.Org Server Extension, version 5.0
[   327.040] (II) Loading extension DOUBLE-BUFFER
[   327.040] (II) LoadModule: "glx"
[   327.040] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/extensions/libglx.so
[   327.040] (II) Module glx: vendor="FireGL - AMD Technologies Inc."
[   327.040] 	compiled for 6.9.0, module version = 1.0.0
[   327.040] (II) Loading extension GLX
[   327.040] (II) LoadModule: "record"
[   327.041] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   327.041] (II) Module record: vendor="X.Org Foundation"
[   327.041] 	compiled for 1.10.4, module version = 1.13.0
[   327.041] 	Module class: X.Org Server Extension
[   327.041] 	ABI class: X.Org Server Extension, version 5.0
[   327.041] (II) Loading extension RECORD
[   327.041] (II) LoadModule: "dri"
[   327.041] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   327.041] (II) Module dri: vendor="X.Org Foundation"
[   327.041] 	compiled for 1.10.4, module version = 1.0.0
[   327.041] 	ABI class: X.Org Server Extension, version 5.0
[   327.041] (II) Loading extension XFree86-DRI
[   327.041] (II) LoadModule: "dri2"
[   327.041] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   327.041] (II) Module dri2: vendor="X.Org Foundation"
[   327.041] 	compiled for 1.10.4, module version = 1.2.0
[   327.041] 	ABI class: X.Org Server Extension, version 5.0
[   327.041] (II) Loading extension DRI2
[   327.041] (II) LoadModule: "intel"
[   327.042] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[   327.042] (II) Module intel: vendor="X.Org Foundation"
[   327.042] 	compiled for 1.10.4, module version = 2.15.901
[   327.042] 	Module class: X.Org Video Driver
[   327.042] 	ABI class: X.Org Video Driver, version 10.0
[   327.042] (II) LoadModule: "fglrx"
[   327.042] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/drivers/fglrx_drv.so
[   327.053] (II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
[   327.053] 	compiled for 1.4.99.906, module version = 8.88.7
[   327.053] 	Module class: X.Org Video Driver
[   327.053] (II) Loading sub module "fglrxdrm"
[   327.053] (II) LoadModule: "fglrxdrm"
[   327.053] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/linux/libfglrxdrm.so
[   327.053] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[   327.053] 	compiled for 1.4.99.906, module version = 8.88.7
[   327.053] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
	Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
	Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
	Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
	Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server
[   327.054] (II) ATI Proprietary Linux Driver Version Identifier:8.88.7
[   327.054] (II) ATI Proprietary Linux Driver Release Identifier: 8.881                                
[   327.054] (II) ATI Proprietary Linux Driver Build Date: Jul 28 2011 17:03:52
[   327.054] (--) using VT number 8

[   327.059] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[   327.059] (WW) Falling back to old probe method for fglrx
[   327.072] (II) intel(0): Loading PCS database from /etc/ati/amdpcsdb
[   327.073] (--) Chipset Supported AMD Graphics Processor (0x68F9) found
[   327.073] (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
[   327.073] (II) intel(0): AMD Video driver is running on a device belonging to a group targeted for this release
[   327.073] (II) intel(0): AMD Video driver is signed
[   327.073] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/drivers/fglrx_drv.so
[   327.073] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/linux/libfglrxdrm.so
[   327.073] (II) intel(0): pEnt->device->identifier=0x840a198
[   327.073] drmOpenDevice: node name is /dev/dri/card0
[   327.073] drmOpenDevice: open result is 13, (OK)
[   327.073] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[   327.073] drmOpenDevice: node name is /dev/dri/card0
[   327.073] drmOpenDevice: open result is 13, (OK)
[   327.073] drmOpenByBusid: drmOpenMinor returns 13
[   327.073] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[   327.073] (**) intel(0): Depth 24, (--) framebuffer bpp 32
[   327.073] (==) intel(0): RGB weight 888
[   327.073] (==) intel(0): Default visual is TrueColor
[   327.074] (II) intel(0): Integrated Graphics Chipset: Intel(R) Sandybridge Desktop (GT1)
[   327.074] (--) intel(0): Chipset: "Sandybridge Desktop (GT1)"
[   327.074] (**) intel(0): Relaxed fencing enabled
[   327.074] (**) intel(0): Wait on SwapBuffers? enabled
[   327.074] (**) intel(0): Triple buffering? enabled
[   327.074] (**) intel(0): Framebuffer tiled
[   327.074] (**) intel(0): Pixmaps tiled
[   327.074] (**) intel(0): 3D buffers tiled
[   327.074] (**) intel(0): SwapBuffers wait enabled
[   327.074] (==) intel(0): video overlay key set to 0x101fe
[   327.135] (II) intel(0): Output VGA1 using monitor section aticonfig-Monitor[0]-0
[   327.159] (II) intel(0): Output HDMI1 has no monitor section
[   327.204] (II) intel(0): Output DP1 has no monitor section
[   327.266] (II) intel(0): EDID for output VGA1
[   327.266] (II) intel(0): Manufacturer: KRF  Model: 1701  Serial#: 907
[   327.266] (II) intel(0): Year: 2005  Week: 28
[   327.266] (II) intel(0): EDID Version: 1.3
[   327.266] (II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[   327.266] (II) intel(0): Sync:  Separate  Composite
[   327.266] (II) intel(0): Max Image Size [cm]: horiz.: 34  vert.: 27
[   327.266] (II) intel(0): Gamma: 2.20
[   327.266] (II) intel(0): DPMS capabilities: Off; RGB/Color Display
[   327.266] (II) intel(0): Default color space is primary color space
[   327.266] (II) intel(0): First detailed timing is preferred mode
[   327.266] (II) intel(0): redX: 0.633 redY: 0.336   greenX: 0.300 greenY: 0.586
[   327.266] (II) intel(0): blueX: 0.146 blueY: 0.103   whiteX: 0.313 whiteY: 0.329
[   327.266] (II) intel(0): Supported established timings:
[   327.266] (II) intel(0): 720x400@70Hz
[   327.266] (II) intel(0): 640x480@60Hz
[   327.266] (II) intel(0): 640x480@67Hz
[   327.266] (II) intel(0): 640x480@72Hz
[   327.266] (II) intel(0): 640x480@75Hz
[   327.266] (II) intel(0): 800x600@56Hz
[   327.266] (II) intel(0): 800x600@60Hz
[   327.266] (II) intel(0): 800x600@72Hz
[   327.266] (II) intel(0): 800x600@75Hz
[   327.266] (II) intel(0): 832x624@75Hz
[   327.266] (II) intel(0): 1024x768@60Hz
[   327.266] (II) intel(0): 1024x768@70Hz
[   327.266] (II) intel(0): 1024x768@75Hz
[   327.266] (II) intel(0): 1280x1024@75Hz
[   327.266] (II) intel(0): 1152x864@75Hz
[   327.266] (II) intel(0): Manufacturer's mask: 0
[   327.266] (II) intel(0): Supported standard timings:
[   327.266] (II) intel(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[   327.266] (II) intel(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[   327.266] (II) intel(0): #2: hsize: 640  vsize 400  refresh: 70  vid: 2609
[   327.266] (II) intel(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[   327.266] (II) intel(0): Supported detailed timing:
[   327.266] (II) intel(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
[   327.266] (II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
[   327.266] (II) intel(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[   327.266] (II) intel(0):  KRF
[   327.266] (II) intel(0): Ranges: V min: 56 V max: 75 Hz, H min: 31 H max: 83 kHz, PixClock max 145 MHz
[   327.266] (II) intel(0): Monitor name: M70
[   327.266] (II) intel(0): EDID (in hex):
[   327.266] (II) intel(0): 	00ffffffffffff002e4601178b030000
[   327.266] (II) intel(0): 	1c0f01030c221b782e0c95a2564c9625
[   327.266] (II) intel(0): 	1a5054bfef8081808140310a714f0101
[   327.266] (II) intel(0): 	010101010101302a009851002a403070
[   327.266] (II) intel(0): 	1300520e1100001e000000fe004b5246
[   327.266] (II) intel(0): 	0a202020202020202020000000fd0038
[   327.266] (II) intel(0): 	4b1f530e000a202020202020000000fc
[   327.267] (II) intel(0): 	004d37300a20202020202020202000df
[   327.267] (II) intel(0): EDID vendor "KRF", prod id 5889
[   327.267] (II) intel(0): Using EDID range info for horizontal sync
[   327.267] (II) intel(0): Using EDID range info for vertical refresh
[   327.267] (II) intel(0): Printing DDC gathered Modelines:
[   327.267] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   327.267] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   327.267] (II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   327.267] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   327.267] (II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[   327.267] (II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[   327.267] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   327.267] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   327.267] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   327.267] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   327.267] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[   327.267] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   327.267] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   327.267] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   327.267] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[   327.267] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   327.267] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[   327.267] (II) intel(0): Modeline "640x400"x70.0   23.35  640 656 720 800  400 401 404 417 -hsync +vsync (29.2 kHz)
[   327.267] (II) intel(0): Printing probed modes for output VGA1
[   327.267] (II) intel(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   327.267] (II) intel(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   327.267] (II) intel(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[   327.267] (II) intel(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   327.267] (II) intel(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
[   327.267] (II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[   327.267] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   327.267] (II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   327.267] (II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[   327.267] (II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   327.267] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   327.267] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   327.267] (II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
[   327.267] (II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   327.267] (II) intel(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[   327.267] (II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   327.267] (II) intel(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   327.290] (II) intel(0): EDID for output HDMI1
[   327.336] (II) intel(0): EDID for output DP1
[   327.336] (II) intel(0): Output VGA1 connected
[   327.336] (II) intel(0): Output HDMI1 disconnected
[   327.336] (II) intel(0): Output DP1 disconnected
[   327.336] (II) intel(0): Using exact sizes for initial modes
[   327.336] (II) intel(0): Output VGA1 using initial mode 1280x1024
[   327.336] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[   327.336] (II) intel(0): Kernel page flipping support detected, enabling
[   327.336] (**) intel(0): Display dimensions: (340, 270) mm
[   327.336] (**) intel(0): DPI set to (95, 96)
[   327.336] (II) Loading sub module "fb"
[   327.336] (II) LoadModule: "fb"
[   327.336] (II) Loading /usr/lib/xorg/modules/libfb.so
[   327.336] (II) Module fb: vendor="X.Org Foundation"
[   327.336] 	compiled for 1.10.4, module version = 1.0.0
[   327.336] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   327.336] (II) Loading sub module "dri2"
[   327.336] (II) LoadModule: "dri2"
[   327.337] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   327.337] (II) Module dri2: vendor="X.Org Foundation"
[   327.337] 	compiled for 1.10.4, module version = 1.2.0
[   327.337] 	ABI class: X.Org Server Extension, version 5.0
[   327.337] (II) fglrx(1): === [xdl_xs110_atiddxPreInit] === begin
[   327.337] (II) Loading sub module "vgahw"
[   327.337] (II) LoadModule: "vgahw"
[   327.338] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[   327.338] (II) Module vgahw: vendor="X.Org Foundation"
[   327.338] 	compiled for 1.10.4, module version = 0.1.0
[   327.338] 	ABI class: X.Org Video Driver, version 10.0
[   327.338] (**) fglrx(1): Depth 24, (--) framebuffer bpp 32
[   327.338] (II) fglrx(1): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[   327.338] (==) fglrx(1): Default visual is TrueColor
[   327.338] (**) fglrx(1): Option "DPMS" "true"
[   327.338] (==) fglrx(1): RGB weight 888
[   327.338] (II) fglrx(1): Using 8 bits per RGB 
[   327.338] (==) fglrx(1): Buffer Tiling is ON
[   327.338] (II) Loading sub module "fglrxdrm"
[   327.338] (II) LoadModule: "fglrxdrm"
[   327.338] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/linux/libfglrxdrm.so
[   327.338] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[   327.338] 	compiled for 1.4.99.906, module version = 8.88.7
[   327.340] ukiDynamicMajor: found major device number 249
[   327.340] ukiDynamicMajor: found major device number 249
[   327.340] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[   327.340] ukiOpenDevice: node name is /dev/ati/card0
[   327.340] ukiOpenDevice: open result is 14, (OK)
[   327.340] ukiOpenByBusid: ukiOpenMinor returns 14
[   327.340] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[   327.340] (==) fglrx(1): NoAccel = NO
[   327.341] (==) fglrx(1): ATI 2D Acceleration Architecture enabled
[   327.341] (--) fglrx(1): Chipset: "ATI Radeon HD 5450" (Chipset = 0x68f9)
[   327.341] (--) fglrx(1): (PciSubVendor = 0x1462, PciSubDevice = 0x2181)
[   327.341] (==) fglrx(1): board vendor info: third party graphics adapter - NOT original ATI
[   327.341] (--) fglrx(1): Linear framebuffer (phys) at 0xc0000000
[   327.341] (--) fglrx(1): MMIO registers at 0xfe520000
[   327.341] (--) fglrx(1): I/O port at 0x0000e000
[   327.341] (==) fglrx(1): ROM-BIOS at 0x000c0000
[   327.342] (II) intel(0): AC Adapter is used
[   327.346] (II) fglrx(1): Primary V_BIOS segment is: 0xc000
[   327.347] (II) Loading sub module "vbe"
[   327.347] (II) LoadModule: "vbe"
[   327.347] (II) Loading /usr/lib/xorg/modules/libvbe.so
[   327.347] (II) Module vbe: vendor="X.Org Foundation"
[   327.347] 	compiled for 1.10.4, module version = 1.1.0
[   327.347] 	ABI class: X.Org Video Driver, version 10.0
[   327.347] (II) fglrx(1): VESA BIOS detected
[   327.347] (II) fglrx(1): VESA VBE Version 3.0
[   327.347] (II) fglrx(1): VESA VBE Total Mem: 16384 kB
[   327.347] (II) fglrx(1): VESA VBE OEM: ATI ATOMBIOS
[   327.347] (II) fglrx(1): VESA VBE OEM Software Rev: 12.20
[   327.347] (II) fglrx(1): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
[   327.348] (II) fglrx(1): VESA VBE OEM Product: 100
[   327.348] (II) fglrx(1): VESA VBE OEM Product Rev: 01.00
[   327.377] (II) intel(0): ATI Video BIOS revision 9 or later detected
[   327.377] (--) fglrx(1): Video RAM: 524288 kByte, Type: DDR3
[   327.377] (II) fglrx(1): PCIE card detected
[   327.377] (--) fglrx(1): Using per-process page tables (PPPT) as GART.
[   327.377] (WW) fglrx(1): board is an unknown third party board, chipset is supported
[   327.381] (II) intel(0): Using adapter: 1:0.0.
[   327.411] (II) intel(0): [FB] MC range(MCFBBase = 0xf00000000, MCFBSize = 0x20000000)
[   327.527] (II) intel(0): Interrupt handler installed at IRQ 48.
[   327.527] (II) fglrx(1): RandR 1.2 support is enabled!
[   327.527] (II) fglrx(1): RandR 1.2 rotation support is enabled!
[   327.527] (==) fglrx(1): Center Mode is disabled 
[   327.527] (II) Loading sub module "fb"
[   327.527] (II) LoadModule: "fb"
[   327.528] (II) Loading /usr/lib/xorg/modules/libfb.so
[   327.528] (II) Module fb: vendor="X.Org Foundation"
[   327.528] 	compiled for 1.10.4, module version = 1.0.0
[   327.528] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   327.528] (II) Loading sub module "ddc"
[   327.528] (II) LoadModule: "ddc"
[   327.528] (II) Module "ddc" already built-in
[   327.628] (II) intel(0): Finished Initialize PPLIB!
[   327.629] (II) fglrx(1): Output DFP1 using monitor section aticonfig-Monitor[0]-1
[   327.629] (II) fglrx(1): Output DFP2 has no monitor section
[   327.629] (II) fglrx(1): Output CRT1 has no monitor section
[   327.629] (II) Loading sub module "ddc"
[   327.629] (II) LoadModule: "ddc"
[   327.629] (II) Module "ddc" already built-in
[   327.629] (II) fglrx(1): Connected Display0: CRT1
[   327.629] (II) fglrx(1): Display0 EDID data ---------------------------
[   327.629] (II) fglrx(1): Manufacturer: VSC  Model: 6a1e  Serial#: 16843009
[   327.629] (II) fglrx(1): Year: 2006  Week: 37
[   327.629] (II) fglrx(1): EDID Version: 1.3
[   327.629] (II) fglrx(1): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[   327.629] (II) fglrx(1): Signal levels configurable
[   327.629] (II) fglrx(1): Sync:  Separate
[   327.629] (II) fglrx(1): Max Image Size [cm]: horiz.: 34  vert.: 27
[   327.629] (II) fglrx(1): Gamma: 2.20
[   327.629] (II) fglrx(1): DPMS capabilities: Off; RGB/Color Display
[   327.629] (II) fglrx(1): Default color space is primary color space
[   327.629] (II) fglrx(1): First detailed timing is preferred mode
[   327.629] (II) fglrx(1): redX: 0.650 redY: 0.340   greenX: 0.300 greenY: 0.620
[   327.629] (II) fglrx(1): blueX: 0.140 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
[   327.629] (II) fglrx(1): Supported established timings:
[   327.629] (II) fglrx(1): 720x400@70Hz
[   327.629] (II) fglrx(1): 640x480@60Hz
[   327.629] (II) fglrx(1): 640x480@67Hz
[   327.629] (II) fglrx(1): 640x480@72Hz
[   327.629] (II) fglrx(1): 640x480@75Hz
[   327.629] (II) fglrx(1): 800x600@56Hz
[   327.629] (II) fglrx(1): 800x600@60Hz
[   327.629] (II) fglrx(1): 800x600@72Hz
[   327.629] (II) fglrx(1): 800x600@75Hz
[   327.629] (II) fglrx(1): 832x624@75Hz
[   327.629] (II) fglrx(1): 1024x768@60Hz
[   327.629] (II) fglrx(1): 1024x768@70Hz
[   327.629] (II) fglrx(1): 1024x768@75Hz
[   327.629] (II) fglrx(1): 1280x1024@75Hz
[   327.629] (II) fglrx(1): 1152x864@75Hz
[   327.629] (II) fglrx(1): Manufacturer's mask: 0
[   327.629] (II) fglrx(1): Supported standard timings:
[   327.629] (II) fglrx(1): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[   327.629] (II) fglrx(1): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[   327.629] (II) fglrx(1): #2: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[   327.629] (II) fglrx(1): Supported detailed timing:
[   327.629] (II) fglrx(1): clock: 108.0 MHz   Image Size:  338 x 270 mm
[   327.629] (II) fglrx(1): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
[   327.629] (II) fglrx(1): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[   327.629] (II) fglrx(1): Serial No: QAN063723745
[   327.629] (II) fglrx(1): Ranges: V min: 50 V max: 75 Hz, H min: 30 H max: 80 kHz, PixClock max 145 MHz
[   327.629] (II) fglrx(1): Monitor name: VA703-4SERIES
[   327.629] (II) fglrx(1): EDID (in hex):
[   327.629] (II) fglrx(1): 	00ffffffffffff005a631e6a01010101
[   327.629] (II) fglrx(1): 	2510010318221b782e8fc5a6574c9e23
[   327.629] (II) fglrx(1): 	125054bfef8081808140714f01010101
[   327.629] (II) fglrx(1): 	010101010101302a009851002a403070
[   327.629] (II) fglrx(1): 	1300520e1100001e000000ff0051414e
[   327.629] (II) fglrx(1): 	3036333732333734350a000000fd0032
[   327.629] (II) fglrx(1): 	4b1e500e000a202020202020000000fc
[   327.629] (II) fglrx(1): 	0056413730332d3453455249455300f5
[   327.629] (II) fglrx(1): End of Display0 EDID data --------------------
[   327.636] (II) fglrx(1): EDID for output DFP1
[   327.636] (II) fglrx(1): EDID for output DFP2
[   327.636] (II) fglrx(1): EDID for output CRT1
[   327.636] (II) fglrx(1): Manufacturer: VSC  Model: 6a1e  Serial#: 16843009
[   327.636] (II) fglrx(1): Year: 2006  Week: 37
[   327.636] (II) fglrx(1): EDID Version: 1.3
[   327.636] (II) fglrx(1): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[   327.636] (II) fglrx(1): Signal levels configurable
[   327.636] (II) fglrx(1): Sync:  Separate
[   327.636] (II) fglrx(1): Max Image Size [cm]: horiz.: 34  vert.: 27
[   327.636] (II) fglrx(1): Gamma: 2.20
[   327.636] (II) fglrx(1): DPMS capabilities: Off; RGB/Color Display
[   327.636] (II) fglrx(1): Default color space is primary color space
[   327.636] (II) fglrx(1): First detailed timing is preferred mode
[   327.636] (II) fglrx(1): redX: 0.650 redY: 0.340   greenX: 0.300 greenY: 0.620
[   327.636] (II) fglrx(1): blueX: 0.140 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
[   327.636] (II) fglrx(1): Supported established timings:
[   327.636] (II) fglrx(1): 720x400@70Hz
[   327.636] (II) fglrx(1): 640x480@60Hz
[   327.636] (II) fglrx(1): 640x480@67Hz
[   327.636] (II) fglrx(1): 640x480@72Hz
[   327.636] (II) fglrx(1): 640x480@75Hz
[   327.636] (II) fglrx(1): 800x600@56Hz
[   327.636] (II) fglrx(1): 800x600@60Hz
[   327.636] (II) fglrx(1): 800x600@72Hz
[   327.636] (II) fglrx(1): 800x600@75Hz
[   327.636] (II) fglrx(1): 832x624@75Hz
[   327.636] (II) fglrx(1): 1024x768@60Hz
[   327.636] (II) fglrx(1): 1024x768@70Hz
[   327.636] (II) fglrx(1): 1024x768@75Hz
[   327.636] (II) fglrx(1): 1280x1024@75Hz
[   327.636] (II) fglrx(1): 1152x864@75Hz
[   327.636] (II) fglrx(1): Manufacturer's mask: 0
[   327.636] (II) fglrx(1): Supported standard timings:
[   327.636] (II) fglrx(1): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[   327.636] (II) fglrx(1): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[   327.636] (II) fglrx(1): #2: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[   327.636] (II) fglrx(1): Supported detailed timing:
[   327.636] (II) fglrx(1): clock: 108.0 MHz   Image Size:  338 x 270 mm
[   327.636] (II) fglrx(1): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
[   327.636] (II) fglrx(1): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[   327.636] (II) fglrx(1): Serial No: QAN063723745
[   327.636] (II) fglrx(1): Ranges: V min: 50 V max: 75 Hz, H min: 30 H max: 80 kHz, PixClock max 145 MHz
[   327.636] (II) fglrx(1): Monitor name: VA703-4SERIES
[   327.636] (II) fglrx(1): EDID (in hex):
[   327.636] (II) fglrx(1): 	00ffffffffffff005a631e6a01010101
[   327.636] (II) fglrx(1): 	2510010318221b782e8fc5a6574c9e23
[   327.636] (II) fglrx(1): 	125054bfef8081808140714f01010101
[   327.636] (II) fglrx(1): 	010101010101302a009851002a403070
[   327.636] (II) fglrx(1): 	1300520e1100001e000000ff0051414e
[   327.636] (II) fglrx(1): 	3036333732333734350a000000fd0032
[   327.636] (II) fglrx(1): 	4b1e500e000a202020202020000000fc
[   327.636] (II) fglrx(1): 	0056413730332d3453455249455300f5
[   327.637] (II) fglrx(1): Printing probed modes for output CRT1
[   327.637] (II) fglrx(1): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   327.637] (II) fglrx(1): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   327.637] (II) fglrx(1): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[   327.637] (II) fglrx(1): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   327.637] (II) fglrx(1): Modeline "1152x864"x60.0  108.00  1152 1328 1440 1688  864 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   327.637] (II) fglrx(1): Modeline "1280x768"x60.0  108.00  1280 1376 1488 1800  768 961 964 1000 +hsync +vsync (60.0 kHz)
[   327.637] (II) fglrx(1): Modeline "1280x720"x60.0  108.00  1280 1376 1488 1800  720 961 964 1000 +hsync +vsync (60.0 kHz)
[   327.637] (II) fglrx(1): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   327.637] (II) fglrx(1): Modeline "1024x768"x70.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[   327.637] (II) fglrx(1): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   327.637] (II) fglrx(1): Modeline "800x600"x72.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[   327.637] (II) fglrx(1): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   327.637] (II) fglrx(1): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   327.637] (II) fglrx(1): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   327.637] (II) fglrx(1): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   327.637] (II) fglrx(1): Modeline "640x480"x72.0   31.50  640 656 696 832  480 481 484 520 -hsync -vsync (37.9 kHz)
[   327.637] (II) fglrx(1): Modeline "640x480"x67.0   27.28  640 664 728 816  480 481 484 499 -hsync +vsync (33.4 kHz)
[   327.637] (II) fglrx(1): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   327.637] (II) fglrx(1): Output DFP1 disconnected
[   327.637] (II) fglrx(1): Output DFP2 disconnected
[   327.637] (II) fglrx(1): Output CRT1 connected
[   327.637] (II) fglrx(1): Using exact sizes for initial modes
[   327.637] (II) fglrx(1): Output CRT1 using initial mode 1280x1024
[   327.637] (II) fglrx(1): DPI set to (96, 96)
[   327.637] (II) fglrx(1): Adapter ATI Radeon HD 5450 has 2 configurable heads and 1 displays connected.
[   327.637] (==) fglrx(1):  PseudoColor visuals disabled
[   327.637] (II) Loading sub module "ramdac"
[   327.637] (II) LoadModule: "ramdac"
[   327.637] (II) Module "ramdac" already built-in
[   327.637] (==) fglrx(1): NoDRI = NO
[   327.637] (==) fglrx(1): Capabilities: 0x00000000
[   327.637] (==) fglrx(1): CapabilitiesEx: 0x00000000
[   327.637] (==) fglrx(1): OpenGL ClientDriverName: "fglrx_dri.so"
[   327.637] (==) fglrx(1): UseFastTLS=0
[   327.637] (==) fglrx(1): BlockSignalsOnLock=1
[   327.637] (--) Depth 24 pixmap format is 32 bpp
[   327.637] (II) intel(0): [DRI2] Setup complete
[   327.637] (II) intel(0): [DRI2]   DRI driver: i965
[   327.637] (II) intel(0): Allocated new frame buffer 1280x1024 stride 5120, tiled
[   327.638] (II) UXA(0): Driver registered support for the following operations:
[   327.638] (II)         solid
[   327.638] (II)         copy
[   327.638] (II)         composite (RENDER acceleration)
[   327.638] (II)         put_image
[   327.638] (II)         get_image
[   327.638] (==) intel(0): Backing store disabled
[   327.638] (==) intel(0): Silken mouse enabled
[   327.638] (II) intel(0): Initializing HW Cursor
[   327.696] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[   327.696] (**) intel(0): DPMS enabled
[   327.696] (==) intel(0): Intel XvMC decoder enabled
[   327.696] (II) intel(0): Set up textured video
[   327.696] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[   327.696] (II) intel(0): direct rendering: DRI2 Enabled
[   327.696] (WW) intel(0): Option "VendorName" is not used
[   327.696] (WW) intel(0): Option "ModelName" is not used
[   327.696] (==) intel(0): hotplug detection: "enabled"
[   327.696] (--) RandR disabled
[   327.696] (II) Loading extension ATIFGLRXDRI
[   327.696] (II) fglrx(1): doing swlDriScreenInit
[   327.696] (II) fglrx(1): swlDriScreenInit for fglrx driver
[   327.696] ukiDynamicMajor: found major device number 249
[   327.696] ukiDynamicMajor: found major device number 249
[   327.696] ukiDynamicMajor: found major device number 249
[   327.696] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[   327.696] ukiOpenDevice: node name is /dev/ati/card0
[   327.696] ukiOpenDevice: open result is 20, (OK)
[   327.696] ukiOpenByBusid: ukiOpenMinor returns 20
[   327.696] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[   327.697] (II) fglrx(1): [uki] DRM interface version 1.0
[   327.697] (II) fglrx(1): [uki] created "fglrx" driver at busid "PCI:1:0:0"
[   327.697] (II) fglrx(1): [uki] added 8192 byte SAREA at 0x2000
[   327.697] (II) fglrx(1): [uki] mapped SAREA 0x2000 to 0xb76c1000
[   327.697] (II) fglrx(1): [uki] framebuffer handle = 0x3000
[   327.697] (II) fglrx(1): [uki] added 1 reserved context for kernel
[   327.697] (II) fglrx(1): swlDriScreenInit done
[   327.697] (II) fglrx(1): Kernel Module Version Information:
[   327.697] (II) fglrx(1):     Name: fglrx
[   327.697] (II) fglrx(1):     Version: 8.88.7
[   327.697] (II) fglrx(1):     Date: Jul 28 2011
[   327.697] (II) fglrx(1):     Desc: ATI FireGL DRM kernel module
[   327.697] (II) fglrx(1): Kernel Module version matches driver.
[   327.697] (II) fglrx(1): Kernel Module Build Time Information:
[   327.697] (II) fglrx(1):     Build-Kernel UTS_RELEASE:        3.0.0-12-generic
[   327.697] (II) fglrx(1):     Build-Kernel MODVERSIONS:        yes
[   327.697] (II) fglrx(1):     Build-Kernel __SMP__:            yes
[   327.697] (II) fglrx(1):     Build-Kernel PAGE_SIZE:          0x1000
[   327.697] (II) fglrx(1): [uki] register handle = 0x00004000
[   327.712] (II) fglrx(1): DRI initialization successfull
[   327.712] (II) fglrx(1): FBADPhys: 0xf00000000 FBMappedSize: 0x01040000
[   327.712] (==) fglrx(1): Backing store disabled
[   327.712] (II) Loading extension FGLRXEXTENSION
[   327.712] (**) fglrx(1): DPMS enabled
[   327.712] (II) fglrx(1): Initialized in-driver Xinerama extension
[   327.712] (WW) fglrx(1): Ignoring Maximize Behavior overrides in MultiHead. Switching to Screen Maximize Behavior.
[   327.712] (**) fglrx(1): Textured Video is enabled.
[   327.712] (II) LoadModule: "glesx"
[   327.712] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/glesx.so
[   327.713] (II) Module glesx: vendor="X.Org Foundation"
[   327.713] 	compiled for 1.4.99.906, module version = 1.0.0
[   327.713] (II) Loading extension GLESX
[   327.713] (II) fglrx(1): GLESX enableFlags = 592
[   327.713] (II) fglrx(1): GLESX is enabled
[   327.713] (II) LoadModule: "amdxmm"
[   327.713] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/amdxmm.so
[   327.713] (II) Module amdxmm: vendor="X.Org Foundation"
[   327.713] 	compiled for 1.4.99.906, module version = 2.0.0
[   327.760] (II) Loading extension AMDXVOPL
[   327.760] (II) Loading extension AMDXVBA
[   327.760] [-     XMM_GLX] [I ]glesxXvInit Configureable RGBOutputColorRange
[   327.760] (II) fglrx(1): UVD feature is enabled(II) fglrx(1): 
[   327.762] (II) fglrx(1): Enable composite support successfully
[   327.762] (WW) fglrx(1): Option "VendorName" is not used
[   327.762] (WW) fglrx(1): Option "ModelName" is not used
[   327.762] (II) fglrx(1): X context handle = 0x1
[   327.762] (II) fglrx(1): [DRI] installation complete
[   327.762] (==) fglrx(1): Silken mouse enabled
[   327.762] (==) fglrx(1): Using HW cursor of display infrastructure!
[   327.762] (II) fglrx(1): Disabling in-server RandR and enabling in-driver RandR 1.2.
[   327.873] (--) RandR disabled
[   327.873] (II) Initializing built-in extension Generic Event Extension
[   327.873] (II) Initializing built-in extension SHAPE
[   327.873] (II) Initializing built-in extension MIT-SHM
[   327.873] (II) Initializing built-in extension XInputExtension
[   327.873] (II) Initializing built-in extension XTEST
[   327.873] (II) Initializing built-in extension BIG-REQUESTS
[   327.873] (II) Initializing built-in extension SYNC
[   327.873] (II) Initializing built-in extension XKEYBOARD
[   327.873] (II) Initializing built-in extension XC-MISC
[   327.873] (II) Initializing built-in extension SECURITY
[   327.873] (II) Initializing built-in extension XINERAMA
[   327.873] (II) Initializing built-in extension XFIXES
[   327.873] (II) Initializing built-in extension RENDER
[   327.873] (II) Initializing built-in extension RANDR
[   327.873] (II) Initializing built-in extension COMPOSITE
[   327.873] (II) Initializing built-in extension DAMAGE
[   327.873] (II) Initializing built-in extension GESTURE
[   327.875] (II) AIGLX: Screen 0 is not DRI capable
[   327.875] ukiDynamicMajor: found major device number 249
[   327.875] ukiDynamicMajor: found major device number 249
[   327.875] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[   327.875] ukiOpenDevice: node name is /dev/ati/card0
[   327.875] ukiOpenDevice: open result is 21, (OK)
[   327.875] ukiOpenByBusid: ukiOpenMinor returns 21
[   327.875] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[   327.917] 
Backtrace:
[   327.917] 0: Xorg (xorg_backtrace+0x37) [0x80a66f7]
[   327.917] 1: Xorg (0x8048000+0x62b3a) [0x80aab3a]
[   327.917] 2: (vdso) (__kernel_rt_sigreturn+0x0) [0x2eb40c]
[   327.917] 3: /usr/lib/i386-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/drivers/fglrx_drv.so (xdl_xs110_atiddxGetGPUMapInfo+0x1d2) [0x1293392]
[   327.917] 4: /usr/lib/i386-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/drivers/fglrx_drv.so (atiddxGetGPUMapInfo+0x37) [0x1166f67]
[   327.917] 5: /usr/lib/i386-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/extensions/libglx.so (0x812000+0xdf37) [0x81ff37]
[   327.917] 6: /usr/lib/i386-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/extensions/libglx.so (0x812000+0x1043a) [0x82243a]
[   327.917] 7: /usr/lib/i386-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/extensions/libglx.so (0x812000+0x1265a) [0x82465a]
[   327.917] 8: /usr/lib/i386-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/extensions/libglx.so (0x812000+0x11d27) [0x823d27]
[   327.917] 9: Xorg (InitExtensions+0x95) [0x80d0fd5]
[   327.917] Segmentation fault at address 0x12
[   327.917] 
Caught signal 11 (Segmentation fault). Server aborting
[   327.917] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[   327.917] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[   327.917] 
[   327.918] (II) fglrx(1): Backup framebuffer data.
[   327.918] (II) fglrx(1): Backup complete.
[   328.167]  ddxSigGiveUp: Closing log
```

Couldn't you help me with this trouble. I really don't understand what I'm doing wrong.


-- sorry for my english, i'm just learning it.

---

### Post by vbabaev on 2012-03-22
Fellows, no one can help me?

---

### Post by Insomn1a on 2012-03-22
> **vbabaev said:**
> Fellows, no one can help me?



I dont really know too much about X but take a look at this:

[http://ubuntuforums.org/showthread.php?t=53966](http://ubuntuforums.org/showthread.php?t=53966)

---

### Post by abraxxa on 2012-06-07
I've the exact same problem.
As far as I know the AMD fglrx come with their own OpenGL libraries. This might cause the segfault when they are loaded for the Intel driver.
Unfortunately I haven't found a solution yet.

---

