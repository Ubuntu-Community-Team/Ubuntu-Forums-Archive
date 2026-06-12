---
title: "Desktop effects could not be enabled with Intel 82G35"
date: 2011-03-30
forum: Hardware
---

### Post by Moonbuzz on 2011-03-30
Hi, I moved an Ubuntu installation (i.e the hard drive) to a new machine, and while everything went alright, I had to delete xorg.conf to get X running. Now, Gnome is running fine, but I can't get desktop effects to work.

Here's my lspci specs:

```
00:02.0 VGA compatible controller: Intel Corporation 82G35 Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA controller])
	Subsystem: Intel Corporation Device d701
	Flags: bus master, fast devsel, latency 0, IRQ 44
	Memory at e0200000 (32-bit, non-prefetchable) [size=1M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 3440 [size=8]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915
```

I tried working with the suggestion in this page: [How to Enable Intel Graphics Driver for Ubuntu 10.10]("http://www.downloadatoz.com/driver/articles/how-to-enable-intel-graphics-driver-for-ubuntu-10-10.html") but to no avail. Any help/further information I need to supply would be welcomed.

---

### Post by lidex on 2011-04-03
Post this output please:
```
cat /var/log/Xorg.0.log
```
Also check out the compiz-check link in my sig.

---

### Post by Moonbuzz on 2011-04-12
This is about it:

```
[    17.457] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    17.457] X Protocol Version 11, Revision 0
[    17.457] Build Operating System: Linux 2.6.24-28-server i686 Ubuntu
[    17.457] Current Operating System: Linux erez 2.6.35-28-generic #50-Ubuntu SMP Fri Mar 18 19:00:26 UTC 2011 i686
[    17.457] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-28-generic root=UUID=f8ddc4f7-d7dc-4cd8-9ec5-20011a600ccb ro quiet splash
[    17.457] Build Date: 09 January 2011  12:14:58PM
[    17.457] xorg-server 2:1.9.0-0ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
[    17.457] Current version of pixman: 0.18.4
[    17.457] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    17.457] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    17.457] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Apr 11 14:52:03 2011
[    17.480] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    17.499] (==) No Layout section.  Using the first Screen section.
[    17.499] (==) No screen section available. Using defaults.
[    17.499] (**) |-->Screen "Default Screen Section" (0)
[    17.499] (**) |   |-->Monitor "<default monitor>"
[    17.499] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    17.499] (==) Automatically adding devices
[    17.499] (==) Automatically enabling devices
[    17.500] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    17.500] 	Entry deleted from font path.
[    17.535] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    17.536] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    17.536] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    17.536] (II) Loader magic: 0x81f9b00
[    17.536] (II) Module ABI versions:
[    17.536] 	X.Org ANSI C Emulation: 0.4
[    17.536] 	X.Org Video Driver: 8.0
[    17.536] 	X.Org XInput driver : 11.0
[    17.536] 	X.Org Server Extension : 4.0
[    17.537] (--) PCI:*(0:0:2:0) 8086:2982:8086:d701 rev 3, Mem @ 0xe0200000/1048576, 0xd0000000/268435456, I/O @ 0x00003440/8
[    17.537] (--) PCI: (0:0:2:1) 8086:2983:8086:d701 rev 3, Mem @ 0xe0100000/1048576
[    17.537] (II) Open ACPI successful (/var/run/acpid.socket)
[    17.537] (II) LoadModule: "extmod"
[    17.714] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    17.719] (II) Module extmod: vendor="X.Org Foundation"
[    17.719] 	compiled for 1.9.0, module version = 1.0.0
[    17.719] 	Module class: X.Org Server Extension
[    17.719] 	ABI class: X.Org Server Extension, version 4.0
[    17.719] (II) Loading extension MIT-SCREEN-SAVER
[    17.719] (II) Loading extension XFree86-VidModeExtension
[    17.719] (II) Loading extension XFree86-DGA
[    17.719] (II) Loading extension DPMS
[    17.719] (II) Loading extension XVideo
[    17.719] (II) Loading extension XVideo-MotionCompensation
[    17.719] (II) Loading extension X-Resource
[    17.719] (II) LoadModule: "dbe"
[    17.720] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    17.720] (II) Module dbe: vendor="X.Org Foundation"
[    17.720] 	compiled for 1.9.0, module version = 1.0.0
[    17.720] 	Module class: X.Org Server Extension
[    17.720] 	ABI class: X.Org Server Extension, version 4.0
[    17.720] (II) Loading extension DOUBLE-BUFFER
[    17.720] (II) LoadModule: "glx"
[    17.721] (II) Loading /usr/lib/xorg/extra-modules/modules/extensions/libglx.so
[    17.737] (II) Module glx: vendor="FireGL - ATI Technologies Inc."
[    17.738] 	compiled for 7.6.0, module version = 1.0.0
[    17.738] (II) Loading extension GLX
[    17.738] (II) LoadModule: "record"
[    17.738] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    17.739] (II) Module record: vendor="X.Org Foundation"
[    17.739] 	compiled for 1.9.0, module version = 1.13.0
[    17.739] 	Module class: X.Org Server Extension
[    17.739] 	ABI class: X.Org Server Extension, version 4.0
[    17.739] (II) Loading extension RECORD
[    17.739] (II) LoadModule: "dri"
[    17.739] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    17.740] (II) Module dri: vendor="X.Org Foundation"
[    17.740] 	compiled for 1.9.0, module version = 1.0.0
[    17.740] 	ABI class: X.Org Server Extension, version 4.0
[    17.740] (II) Loading extension XFree86-DRI
[    17.740] (II) LoadModule: "dri2"
[    17.740] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    17.748] (II) Module dri2: vendor="X.Org Foundation"
[    17.748] 	compiled for 1.9.0, module version = 1.2.0
[    17.748] 	ABI class: X.Org Server Extension, version 4.0
[    17.748] (II) Loading extension DRI2
[    17.748] (==) Matched intel as autoconfigured driver 0
[    17.748] (==) Matched vesa as autoconfigured driver 1
[    17.748] (==) Matched fbdev as autoconfigured driver 2
[    17.748] (==) Assigned the driver to the xf86ConfigLayout
[    17.748] (II) LoadModule: "intel"
[    17.748] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    17.758] (II) Module intel: vendor="X.Org Foundation"
[    17.758] 	compiled for 1.9.0, module version = 2.14.902
[    17.758] 	Module class: X.Org Video Driver
[    17.758] 	ABI class: X.Org Video Driver, version 8.0
[    17.758] (II) LoadModule: "vesa"
[    17.758] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    17.761] (II) Module vesa: vendor="X.Org Foundation"
[    17.761] 	compiled for 1.8.99.905, module version = 2.3.0
[    17.761] 	Module class: X.Org Video Driver
[    17.761] 	ABI class: X.Org Video Driver, version 8.0
[    17.761] (II) LoadModule: "fbdev"
[    17.762] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    17.770] (II) Module fbdev: vendor="X.Org Foundation"
[    17.770] 	compiled for 1.8.99.905, module version = 0.4.2
[    17.770] 	ABI class: X.Org Video Driver, version 8.0
[    17.770] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
	Sandybridge, Sandybridge
[    17.770] (II) VESA: driver for VESA chipsets: vesa
[    17.770] (II) FBDEV: driver for framebuffer: fbdev
[    17.771] (++) using VT number 7

[    17.773] (WW) Falling back to old probe method for vesa
[    17.773] (WW) Falling back to old probe method for fbdev
[    17.773] (II) Loading sub module "fbdevhw"
[    17.773] (II) LoadModule: "fbdevhw"
[    17.774] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    17.774] (II) Module fbdevhw: vendor="X.Org Foundation"
[    17.774] 	compiled for 1.9.0, module version = 0.0.2
[    17.774] 	ABI class: X.Org Video Driver, version 8.0
[    17.774] drmOpenDevice: node name is /dev/dri/card0
[    17.774] drmOpenDevice: open result is 9, (OK)
[    17.774] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    17.774] drmOpenDevice: node name is /dev/dri/card0
[    17.774] drmOpenDevice: open result is 9, (OK)
[    17.774] drmOpenByBusid: drmOpenMinor returns 9
[    17.774] drmOpenByBusid: Interface 1.4 failed, trying 1.1
[    17.774] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    17.774] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    17.774] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    17.774] (==) intel(0): RGB weight 888
[    17.774] (==) intel(0): Default visual is TrueColor
[    17.774] (II) intel(0): Integrated Graphics Chipset: Intel(R) G35
[    17.774] (--) intel(0): Chipset: "G35"
[    17.774] (**) intel(0): Framebuffer tiled
[    17.774] (**) intel(0): Pixmaps tiled
[    17.774] (**) intel(0): 3D buffers tiled
[    17.774] (**) intel(0): SwapBuffers wait enabled
[    17.774] (==) intel(0): video overlay key set to 0x101fe
[    17.892] (II) intel(0): Output VGA1 has no monitor section
[    18.153] (II) intel(0): Output DVI1 has no monitor section
[    18.272] (II) intel(0): EDID for output VGA1
[    18.272] (II) intel(0): Manufacturer: GSM  Model: 4b43  Serial#: 56013
[    18.272] (II) intel(0): Year: 2008  Week: 2
[    18.272] (II) intel(0): EDID Version: 1.3
[    18.272] (II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[    18.272] (II) intel(0): Sync:  Separate  SyncOnGreen
[    18.272] (II) intel(0): Max Image Size [cm]: horiz.: 34  vert.: 27
[    18.272] (II) intel(0): Gamma: 2.20
[    18.272] (II) intel(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    18.272] (II) intel(0): First detailed timing is preferred mode
[    18.272] (II) intel(0): redX: 0.637 redY: 0.343   greenX: 0.297 greenY: 0.615
[    18.272] (II) intel(0): blueX: 0.145 blueY: 0.069   whiteX: 0.312 whiteY: 0.329
[    18.272] (II) intel(0): Supported established timings:
[    18.272] (II) intel(0): 720x400@70Hz
[    18.272] (II) intel(0): 640x480@60Hz
[    18.272] (II) intel(0): 640x480@75Hz
[    18.272] (II) intel(0): 800x600@60Hz
[    18.273] (II) intel(0): 800x600@75Hz
[    18.273] (II) intel(0): 832x624@75Hz
[    18.273] (II) intel(0): 1024x768@60Hz
[    18.273] (II) intel(0): 1024x768@75Hz
[    18.273] (II) intel(0): 1280x1024@75Hz
[    18.273] (II) intel(0): 1152x864@75Hz
[    18.273] (II) intel(0): Manufacturer's mask: 0
[    18.273] (II) intel(0): Supported standard timings:
[    18.273] (II) intel(0): #0: hsize: 640  vsize 480  refresh: 75  vid: 20273
[    18.273] (II) intel(0): #1: hsize: 800  vsize 600  refresh: 75  vid: 20293
[    18.273] (II) intel(0): #2: hsize: 1024  vsize 768  refresh: 75  vid: 20321
[    18.273] (II) intel(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    18.273] (II) intel(0): Supported detailed timing:
[    18.273] (II) intel(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
[    18.273] (II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
[    18.273] (II) intel(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[    18.273] (II) intel(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 145 MHz
[    18.273] (II) intel(0): Monitor name: L1953TR
[    18.273] (II) intel(0): Monitor name: 
[    18.273] (II) intel(0): EDID (in hex):
[    18.273] (II) intel(0): 	00ffffffffffff001e6d434bcdda0000
[    18.273] (II) intel(0): 	021201036a221b78ea3231a3574c9d25
[    18.273] (II) intel(0): 	115054a56b80314f454f614f81800101
[    18.273] (II) intel(0): 	010101010101302a009851002a403070
[    18.273] (II) intel(0): 	1300520e1100001e000000fd00384b1e
[    18.273] (II) intel(0): 	530e000a202020202020000000fc004c
[    18.273] (II) intel(0): 	3139353354520a2020202020000000fc
[    18.273] (II) intel(0): 	00200a20202020202020202020200000
[    18.273] (II) intel(0): EDID vendor "GSM", prod id 19267
[    18.273] (II) intel(0): Using EDID range info for horizontal sync
[    18.273] (II) intel(0): Using EDID range info for vertical refresh
[    18.273] (II) intel(0): Printing DDC gathered Modelines:
[    18.273] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    18.273] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    18.273] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    18.273] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    18.273] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    18.273] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    18.273] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    18.273] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    18.273] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    18.273] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    18.273] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    18.273] (II) intel(0): Printing probed modes for output VGA1
[    18.273] (II) intel(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    18.273] (II) intel(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    18.273] (II) intel(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    18.273] (II) intel(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
[    18.273] (II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    18.273] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    18.273] (II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    18.273] (II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    18.273] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    18.273] (II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    18.273] (II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    18.273] (II) intel(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    18.535] (II) intel(0): EDID for output DVI1
[    18.535] (II) intel(0): Manufacturer: GSM  Model: 4b44  Serial#: 56048
[    18.535] (II) intel(0): Year: 2008  Week: 2
[    18.535] (II) intel(0): EDID Version: 1.3
[    18.535] (II) intel(0): Digital Display Input
[    18.535] (II) intel(0): Max Image Size [cm]: horiz.: 34  vert.: 27
[    18.535] (II) intel(0): Gamma: 2.20
[    18.535] (II) intel(0): DPMS capabilities: StandBy Suspend Off
[    18.535] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    18.535] (II) intel(0): First detailed timing is preferred mode
[    18.535] (II) intel(0): redX: 0.637 redY: 0.343   greenX: 0.297 greenY: 0.615
[    18.535] (II) intel(0): blueX: 0.145 blueY: 0.069   whiteX: 0.312 whiteY: 0.329
[    18.535] (II) intel(0): Supported established timings:
[    18.535] (II) intel(0): 720x400@70Hz
[    18.535] (II) intel(0): 640x480@60Hz
[    18.535] (II) intel(0): 640x480@75Hz
[    18.535] (II) intel(0): 800x600@60Hz
[    18.535] (II) intel(0): 800x600@75Hz
[    18.535] (II) intel(0): 832x624@75Hz
[    18.535] (II) intel(0): 1024x768@60Hz
[    18.535] (II) intel(0): 1024x768@75Hz
[    18.535] (II) intel(0): 1152x864@75Hz
[    18.535] (II) intel(0): Manufacturer's mask: 0
[    18.535] (II) intel(0): Supported standard timings:
[    18.535] (II) intel(0): #0: hsize: 640  vsize 480  refresh: 75  vid: 20273
[    18.535] (II) intel(0): #1: hsize: 800  vsize 600  refresh: 75  vid: 20293
[    18.535] (II) intel(0): #2: hsize: 1024  vsize 768  refresh: 75  vid: 20321
[    18.535] (II) intel(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    18.535] (II) intel(0): Supported detailed timing:
[    18.535] (II) intel(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
[    18.535] (II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
[    18.535] (II) intel(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[    18.535] (II) intel(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 71 kHz, PixClock max 115 MHz
[    18.535] (II) intel(0): Monitor name: L1953TR
[    18.535] (II) intel(0): Monitor name: 
[    18.535] (II) intel(0): EDID (in hex):
[    18.535] (II) intel(0): 	00ffffffffffff001e6d444bf0da0000
[    18.535] (II) intel(0): 	02120103ea221b78ea3231a3574c9d25
[    18.535] (II) intel(0): 	115054a56a80314f454f614f81800101
[    18.535] (II) intel(0): 	010101010101302a009851002a403070
[    18.535] (II) intel(0): 	1300520e1100001e000000fd00384b1e
[    18.535] (II) intel(0): 	470b000a202020202020000000fc004c
[    18.535] (II) intel(0): 	3139353354520a2020202020000000fc
[    18.535] (II) intel(0): 	00200a2020202020202020202020006c
[    18.535] (II) intel(0): Printing probed modes for output DVI1
[    18.535] (II) intel(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    18.535] (II) intel(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    18.535] (II) intel(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
[    18.535] (II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    18.535] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    18.535] (II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    18.535] (II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    18.535] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    18.535] (II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    18.535] (II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    18.535] (II) intel(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    18.535] (II) intel(0): Output VGA1 connected
[    18.535] (II) intel(0): Output DVI1 connected
[    18.535] (II) intel(0): Using exact sizes for initial modes
[    18.535] (II) intel(0): Output VGA1 using initial mode 1280x1024
[    18.535] (II) intel(0): Output DVI1 using initial mode 1280x1024
[    18.535] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    18.535] (II) intel(0): Kernel page flipping support detected, enabling
[    18.536] (**) intel(0): Display dimensions: (340, 270) mm
[    18.536] (**) intel(0): DPI set to (95, 96)
[    18.536] (II) Loading sub module "fb"
[    18.536] (II) LoadModule: "fb"
[    18.536] (II) Loading /usr/lib/xorg/modules/libfb.so
[    19.144] (II) Module fb: vendor="X.Org Foundation"
[    19.144] 	compiled for 1.9.0, module version = 1.0.0
[    19.144] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    19.144] (II) Loading sub module "dri2"
[    19.144] (II) LoadModule: "dri2"
[    19.144] (II) Reloading /usr/lib/xorg/modules/extensions/libdri2.so
[    19.144] (II) UnloadModule: "vesa"
[    19.144] (II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    19.144] (II) UnloadModule: "fbdev"
[    19.144] (II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    19.145] (II) UnloadModule: "fbdevhw"
[    19.145] (II) Unloading /usr/lib/xorg/modules/libfbdevhw.so
[    19.145] (==) Depth 24 pixmap format is 32 bpp
[    19.145] (II) intel(0): [DRI2] Setup complete
[    19.145] (II) intel(0): [DRI2]   DRI driver: i965
[    19.145] (II) intel(0): Allocated new frame buffer 1280x1024 stride 5120, tiled
[    20.091] (II) UXA(0): Driver registered support for the following operations:
[    20.091] (II)         solid
[    20.091] (II)         copy
[    20.091] (II)         composite (RENDER acceleration)
[    20.092] (II)         put_image
[    20.092] (II)         get_image
[    20.092] (==) intel(0): Backing store disabled
[    20.092] (==) intel(0): Silken mouse enabled
[    20.124] (II) intel(0): Initializing HW Cursor
[    20.472] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    20.472] (==) intel(0): DPMS enabled
[    20.472] (==) intel(0): Intel XvMC decoder enabled
[    20.472] (II) intel(0): Set up textured video
[    20.472] (II) intel(0): Set up overlay video
[    20.472] (II) intel(0): [XvMC] i965_xvmc driver initialized.
[    20.472] (II) intel(0): direct rendering: DRI2 Enabled
[    20.472] (==) intel(0): hotplug detection: "enabled"
[    20.472] (--) RandR disabled
[    20.472] (II) Initializing built-in extension Generic Event Extension
[    20.472] (II) Initializing built-in extension SHAPE
[    20.472] (II) Initializing built-in extension MIT-SHM
[    20.472] (II) Initializing built-in extension XInputExtension
[    20.472] (II) Initializing built-in extension XTEST
[    20.472] (II) Initializing built-in extension BIG-REQUESTS
[    20.472] (II) Initializing built-in extension SYNC
[    20.472] (II) Initializing built-in extension XKEYBOARD
[    20.472] (II) Initializing built-in extension XC-MISC
[    20.472] (II) Initializing built-in extension SECURITY
[    20.472] (II) Initializing built-in extension XINERAMA
[    20.472] (II) Initializing built-in extension XFIXES
[    20.472] (II) Initializing built-in extension RENDER
[    20.472] (II) Initializing built-in extension RANDR
[    20.472] (II) Initializing built-in extension COMPOSITE
[    20.472] (II) Initializing built-in extension DAMAGE
[    20.472] (II) Initializing built-in extension GESTURE
[    20.476] (EE) GLX error: Can not get required symbols.
[    20.492] (II) intel(0): Setting screen physical size to 338 x 270
[    20.725] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    20.760] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    20.760] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    20.760] (II) LoadModule: "evdev"
[    20.760] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    20.823] (II) Module evdev: vendor="X.Org Foundation"
[    20.824] 	compiled for 1.9.0, module version = 2.3.2
[    20.824] 	Module class: X.Org XInput Driver
[    20.824] 	ABI class: X.Org XInput driver, version 11.0
[    20.824] (**) Power Button: always reports core events
[    20.824] (**) Power Button: Device: "/dev/input/event1"
[    20.836] (II) Power Button: Found keys
[    20.836] (II) Power Button: Configuring as keyboard
[    20.836] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    20.836] (**) Option "xkb_rules" "evdev"
[    20.836] (**) Option "xkb_model" "pc105"
[    20.836] (**) Option "xkb_layout" "us"
[    20.836] (**) Option "xkb_variant" "dvorak"
[    20.836] (**) Option "xkb_options" "lv3:ralt_switch"
[    20.838] (II) XKB: reuse xkmfile /var/lib/xkb/server-6F86FD73C5E4C040CF174C28CF7A029ECAC10E5B.xkm
[    20.854] (II) config/udev: Adding input device Sleep Button (/dev/input/event0)
[    20.854] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    20.854] (**) Sleep Button: always reports core events
[    20.854] (**) Sleep Button: Device: "/dev/input/event0"
[    20.864] (II) Sleep Button: Found keys
[    20.864] (II) Sleep Button: Configuring as keyboard
[    20.864] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    20.864] (**) Option "xkb_rules" "evdev"
[    20.864] (**) Option "xkb_model" "pc105"
[    20.864] (**) Option "xkb_layout" "us"
[    20.864] (**) Option "xkb_variant" "dvorak"
[    20.864] (**) Option "xkb_options" "lv3:ralt_switch"
[    20.866] (II) config/udev: Adding input device Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) (/dev/input/event2)
[    20.866] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Applying InputClass "evdev pointer catchall"
[    20.866] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): always reports core events
[    20.866] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Device: "/dev/input/event2"
[    20.876] (II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found 3 mouse buttons
[    20.876] (II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found scroll wheel(s)
[    20.876] (II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found relative axes
[    20.876] (II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found x and y relative axes
[    20.876] (II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Configuring as mouse
[    20.876] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): YAxisMapping: buttons 4 and 5
[    20.876] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    20.876] (II) XINPUT: Adding extended input device "Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)" (type: MOUSE)
[    20.876] (II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): initialized for relative axes.
[    20.876] (II) config/udev: Adding input device Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) (/dev/input/mouse0)
[    20.876] (II) No input driver/identifier specified (ignoring)
[    20.876] (II) config/udev: Adding input device Microsoft Wired Keyboard 600 (/dev/input/event3)
[    20.876] (**) Microsoft Wired Keyboard 600: Applying InputClass "evdev keyboard catchall"
[    20.877] (**) Microsoft Wired Keyboard 600: always reports core events
[    20.877] (**) Microsoft Wired Keyboard 600: Device: "/dev/input/event3"
[    20.888] (II) Microsoft Wired Keyboard 600: Found keys
[    20.888] (II) Microsoft Wired Keyboard 600: Configuring as keyboard
[    20.888] (II) XINPUT: Adding extended input device "Microsoft Wired Keyboard 600" (type: KEYBOARD)
[    20.888] (**) Option "xkb_rules" "evdev"
[    20.888] (**) Option "xkb_model" "pc105"
[    20.888] (**) Option "xkb_layout" "us"
[    20.888] (**) Option "xkb_variant" "dvorak"
[    20.888] (**) Option "xkb_options" "lv3:ralt_switch"
[    20.888] (II) config/udev: Adding input device Microsoft Wired Keyboard 600 (/dev/input/event4)
[    20.888] (**) Microsoft Wired Keyboard 600: Applying InputClass "evdev keyboard catchall"
[    20.888] (**) Microsoft Wired Keyboard 600: always reports core events
[    20.888] (**) Microsoft Wired Keyboard 600: Device: "/dev/input/event4"
[    20.900] (II) Microsoft Wired Keyboard 600: Found 1 mouse buttons
[    20.900] (II) Microsoft Wired Keyboard 600: Found scroll wheel(s)
[    20.900] (II) Microsoft Wired Keyboard 600: Found relative axes
[    20.900] (II) Microsoft Wired Keyboard 600: Found absolute axes
[    20.900] (II) Microsoft Wired Keyboard 600: Found x and y absolute axes
[    20.900] (II) Microsoft Wired Keyboard 600: Found keys
[    20.900] (II) Microsoft Wired Keyboard 600: Configuring as mouse
[    20.900] (II) Microsoft Wired Keyboard 600: Configuring as keyboard
[    20.900] (**) Microsoft Wired Keyboard 600: YAxisMapping: buttons 4 and 5
[    20.900] (**) Microsoft Wired Keyboard 600: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    20.900] (II) XINPUT: Adding extended input device "Microsoft Wired Keyboard 600" (type: KEYBOARD)
[    20.900] (**) Option "xkb_rules" "evdev"
[    20.900] (**) Option "xkb_model" "pc105"
[    20.900] (**) Option "xkb_layout" "us"
[    20.900] (**) Option "xkb_variant" "dvorak"
[    20.900] (**) Option "xkb_options" "lv3:ralt_switch"
[    20.900] (EE) Microsoft Wired Keyboard 600: failed to initialize for relative axes.
[    20.900] (WW) Device 'Microsoft Wired Keyboard 600' has 37 axes, only using first 36.
[    20.900] (II) Microsoft Wired Keyboard 600: initialized for absolute axes.
[    20.900] (II) config/udev: Adding input device Microsoft Wired Keyboard 600 (/dev/input/js0)
[    20.900] (II) No input driver/identifier specified (ignoring)
[    22.669] (II) intel(0): EDID vendor "GSM", prod id 19268
[    22.669] (II) intel(0): Using hsync ranges from config file
[    22.669] (II) intel(0): Using vrefresh ranges from config file
[    22.669] (II) intel(0): Printing DDC gathered Modelines:
[    22.669] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    22.669] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    22.669] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    22.669] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    22.669] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    22.669] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    22.669] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    22.669] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    22.669] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    22.669] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    23.064] (II) intel(0): EDID vendor "GSM", prod id 19268
[    23.064] (II) intel(0): Using hsync ranges from config file
[    23.064] (II) intel(0): Using vrefresh ranges from config file
[    23.064] (II) intel(0): Printing DDC gathered Modelines:
[    23.064] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    23.064] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    23.064] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    23.064] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    23.064] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    23.064] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    23.064] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    23.064] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    23.064] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    23.064] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    23.469] (II) intel(0): EDID vendor "GSM", prod id 19268
[    23.469] (II) intel(0): Using hsync ranges from config file
[    23.469] (II) intel(0): Using vrefresh ranges from config file
[    23.469] (II) intel(0): Printing DDC gathered Modelines:
[    23.469] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    23.469] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    23.469] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    23.469] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    23.469] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    23.469] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    23.469] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    23.469] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    23.469] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    23.469] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    23.848] (II) intel(0): EDID vendor "GSM", prod id 19268
[    23.848] (II) intel(0): Using hsync ranges from config file
[    23.848] (II) intel(0): Using vrefresh ranges from config file
[    23.848] (II) intel(0): Printing DDC gathered Modelines:
[    23.848] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    23.848] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    23.848] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    23.848] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    23.848] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    23.848] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    23.848] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    23.848] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    23.848] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    23.848] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    23.903] (II) intel(0): Allocated new frame buffer 2560x1024 stride 10240, tiled
[    54.148] (II) intel(0): EDID vendor "GSM", prod id 19268
[    54.148] (II) intel(0): Using hsync ranges from config file
[    54.148] (II) intel(0): Using vrefresh ranges from config file
[    54.148] (II) intel(0): Printing DDC gathered Modelines:
[    54.148] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    54.148] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    54.148] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    54.148] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    54.148] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    54.148] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    54.148] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    54.148] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    54.148] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    54.148] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    54.536] (II) intel(0): EDID vendor "GSM", prod id 19268
[    54.536] (II) intel(0): Using hsync ranges from config file
[    54.536] (II) intel(0): Using vrefresh ranges from config file
[    54.536] (II) intel(0): Printing DDC gathered Modelines:
[    54.536] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    54.536] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    54.536] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    54.536] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    54.536] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    54.536] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    54.536] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    54.536] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    54.536] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    54.536] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    54.908] (II) intel(0): EDID vendor "GSM", prod id 19268
[    54.908] (II) intel(0): Using hsync ranges from config file
[    54.908] (II) intel(0): Using vrefresh ranges from config file
[    54.908] (II) intel(0): Printing DDC gathered Modelines:
[    54.908] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    54.908] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    54.908] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    54.908] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    54.908] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    54.908] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    54.908] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    54.908] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    54.908] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    54.908] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    63.189] (II) intel(0): EDID vendor "GSM", prod id 19268
[    63.189] (II) intel(0): Using hsync ranges from config file
[    63.189] (II) intel(0): Using vrefresh ranges from config file
[    63.189] (II) intel(0): Printing DDC gathered Modelines:
[    63.189] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    63.189] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    63.189] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    63.189] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    63.189] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    63.189] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    63.189] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    63.189] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    63.189] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    63.189] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[  3502.053] (II) intel(0): EDID vendor "GSM", prod id 19268
[  3502.053] (II) intel(0): Using hsync ranges from config file
[  3502.053] (II) intel(0): Using vrefresh ranges from config file
[  3502.053] (II) intel(0): Printing DDC gathered Modelines:
[  3502.053] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  3502.053] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  3502.053] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[  3502.053] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  3502.053] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[  3502.053] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[  3502.053] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  3502.053] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[  3502.053] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  3502.053] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[  7614.409] (II) intel(0): EDID vendor "GSM", prod id 19268
[  7614.409] (II) intel(0): Using hsync ranges from config file
[  7614.409] (II) intel(0): Using vrefresh ranges from config file
[  7614.409] (II) intel(0): Printing DDC gathered Modelines:
[  7614.409] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  7614.409] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  7614.409] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[  7614.409] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  7614.409] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[  7614.409] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[  7614.409] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  7614.409] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[  7614.409] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  7614.409] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[ 68131.545] (II) intel(0): EDID vendor "GSM", prod id 19268
[ 68131.545] (II) intel(0): Using hsync ranges from config file
[ 68131.545] (II) intel(0): Using vrefresh ranges from config file
[ 68131.545] (II) intel(0): Printing DDC gathered Modelines:
[ 68131.545] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[ 68131.545] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[ 68131.545] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[ 68131.545] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[ 68131.545] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[ 68131.545] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[ 68131.545] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[ 68131.545] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[ 68131.545] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[ 68131.545] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[ 70010.017] (II) intel(0): EDID vendor "GSM", prod id 19268
[ 70010.017] (II) intel(0): Using hsync ranges from config file
[ 70010.017] (II) intel(0): Using vrefresh ranges from config file
[ 70010.017] (II) intel(0): Printing DDC gathered Modelines:
[ 70010.017] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[ 70010.017] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[ 70010.017] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[ 70010.017] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[ 70010.017] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[ 70010.017] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[ 70010.017] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[ 70010.017] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[ 70010.017] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[ 70010.017] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[ 75081.381] (II) intel(0): EDID vendor "GSM", prod id 19268
[ 75081.381] (II) intel(0): Using hsync ranges from config file
[ 75081.381] (II) intel(0): Using vrefresh ranges from config file
[ 75081.381] (II) intel(0): Printing DDC gathered Modelines:
[ 75081.381] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[ 75081.381] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[ 75081.381] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[ 75081.381] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[ 75081.381] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[ 75081.381] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[ 75081.381] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[ 75081.381] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[ 75081.381] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[ 75081.381] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)

```

and 
```

$ ./compiz-check 

Gathering information about your system...

 Distribution:          Ubuntu 10.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation 82G35 Express Integrated Graphics Controller (rev 03)
 Driver in use:         intel
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 

```

Thanks in advance.

---

