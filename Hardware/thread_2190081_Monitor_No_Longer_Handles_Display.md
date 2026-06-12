---
title: "Monitor No Longer Handles Display"
date: 2013-11-25
forum: Hardware
---

### Post by HDTimeshifter on 2013-11-25
I hooked up my Ubuntu server to a 15" LCD monitor then switched it back to a 20" CRT and now whenever it boots, the display says something like out of range. I tried booting in safe mode and 2 previous versions as well as safe mode with limited graphics and none work. When I switched back to the LCD monitor it works again and is at 1024 x 768 resolution. I can't see how the low resolution for the little LCD monitor doesn't work on the CRT. I think I may have upped the resolution on the CRT to higher than 1024x768, but can't figure out how to reset it if the server is trying to use too high a resolution on the CRT. Does anyone know what is wrong and how to fix it so I can once again use my server with the larger display?

---

### Post by papibe on 2013-11-25
Hi HDTimeshifter.

My guess is that the system is not able to read the EDID info (resolutions and timings) from the analog monitor. It may be possible to get that data otherwise (using Windows for instance) and then hardcoded into a custom xorg.conf file.

Another idea is that is you have an xorg.conf, it may produce better results if you delete it (rename it actually):
```
sudo mv -iv /etc/X11/xorg.conf /etc/X11/xorg.conf.old.back
```
Let us know how it goes.
Regards.

---

### Post by HDTimeshifter on 2013-11-26
Hi papibe,

There is no xorg.conf file. I looked at all the other text files in the /etc/X11 directory, links, and subdirectories and don't see any useful configuration file, but there is an xorg.conf.failsafe file which looks harmless with the below contents:

[FONT=Courier New]"Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
[/FONT]

---

### Post by papibe on 2013-11-26
Could you post the content of this file?
```
/var/log/Xorg.0.log
```
Please paste it here [paste.ubuntu.com]("http://paste.ubuntu.com/"), and then post back the link.

Regards.

---

### Post by HDTimeshifter on 2013-12-01
Hopefully this is the correct link:
[http://paste.ubuntu.com/6503312/]("http://paste.ubuntu.com/6503312/")

By the way, is there an editor where I can select-all (Ctrl-A) to copy and paste? I tried yanking all in vi, but it doesn't copy into the buffer in order to paste. I had to more through the whole file and copy and paste page by page (more than once, I accidentally pressed Ctrl-C), aborting the more rather than copying!

---

### Post by HDTimeshifter on 2014-01-06
Someone told me the paste link doesn't work although it does for me when I click on it so I'll just past inline below:

[    22.107] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    22.107] X Protocol Version 11, Revision 0
[    22.107] Build Operating System: Linux 2.6.42-37-generic i686 Ubuntu
[    22.107] Current Operating System: Linux Server 3.2.0-56-generic #86-Ubuntu SMP Wed Oct 23 17:31:43 UT
C 2013 i686
[    22.107] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-56-generic root=UUID=0765d816-eccf-494e-9
312-637ca5a9b89d ro quiet splash vt.handoff=7
[    22.107] Build Date: 16 October 2013  04:45:22PM
[    22.107] xorg-server 2:1.11.4-0ubuntu10.14 (For technical support please see [http://www.ubuntu.com/sup](http://www.ubuntu.com/sup)
port) 
[    22.107] Current version of pixman: 0.24.4
[    22.107] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[    22.107] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    22.107] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Nov 24 13:04:18 2013
[    22.135] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    22.136] (==) No Layout section.  Using the first Screen section.
[    22.136] (==) No screen section available. Using defaults.
[    22.136] (**) |-->Screen "Default Screen Section" (0)
[    22.136] (**) |   |-->Monitor "<default monitor>"
[    22.136] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    22.136] (==) Automatically adding devices
[    22.136] (==) Automatically enabling devices
[    22.136] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    22.136] 	Entry deleted from font path.
[    22.136] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    22.136] 	Entry deleted from font path.
[    22.136] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    22.136] 	Entry deleted from font path.
[    22.136] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    22.137] 	Entry deleted from font path.
[    22.137] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    22.137] 	Entry deleted from font path.
[    22.137] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    22.137] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-module
s,/usr/lib/xorg/modules"
[    22.137] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    22.137] (II) Loader magic: 0xbfb5a0
[    22.137] (II) Module ABI versions:
[    22.137] 	X.Org ANSI C Emulation: 0.4
[    22.137] 	X.Org Video Driver: 11.0
[    22.137] 	X.Org XInput driver : 16.0
[    22.137] 	X.Org Server Extension : 6.0
[    22.138] (--) PCI:*(0:0:2:0) 8086:2562:107b:2010 rev 1, Mem @ 0xf0000000/134217728, 0xffa80000/524288
[    22.138] (II) Open ACPI successful (/var/run/acpid.socket)
[    22.138] (II) LoadModule: "extmod"
[    22.173] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    22.173] (II) Module extmod: vendor="X.Org Foundation"
[    22.173] 	compiled for 1.11.3, module version = 1.0.0
[    22.173] 	Module class: X.Org Server Extension
[    22.173] 	ABI class: X.Org Server Extension, version 6.0
[    22.173] (II) Loading extension MIT-SCREEN-SAVER
[    22.173] (II) Loading extension XFree86-VidModeExtension
[    22.173] (II) Loading extension XFree86-DGA
[    22.173] (II) Loading extension DPMS
[    22.173] (II) Loading extension XVideo
[    22.173] (II) Loading extension XVideo-MotionCompensation
[    22.173] (II) Loading extension X-Resource
[    22.173] (II) LoadModule: "dbe"
[    22.174] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    22.174] (II) Module dbe: vendor="X.Org Foundation"
[    22.174] 	compiled for 1.11.3, module version = 1.0.0
[    22.174] 	Module class: X.Org Server Extension
[    22.174] 	ABI class: X.Org Server Extension, version 6.0
[    22.174] (II) Loading extension DOUBLE-BUFFER
[    22.174] (II) LoadModule: "glx"
[    22.174] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    22.175] (II) Module glx: vendor="X.Org Foundation"
[    22.175] 	compiled for 1.11.3, module version = 1.0.0
[    22.175] 	ABI class: X.Org Server Extension, version 6.0
[    22.175] (==) AIGLX enabled
[    22.175] (II) Loading extension GLX
[    22.175] (II) LoadModule: "record"
[    22.175] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    22.175] (II) Module record: vendor="X.Org Foundation"
[    22.175] 	compiled for 1.11.3, module version = 1.13.0
[    22.175] 	Module class: X.Org Server Extension
[    22.175] 	ABI class: X.Org Server Extension, version 6.0
[    22.175] (II) Loading extension RECORD
[    22.175] (II) LoadModule: "dri"
[    22.177] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    22.177] (II) Module dri: vendor="X.Org Foundation"
[    22.177] 	compiled for 1.11.3, module version = 1.0.0
[    22.177] 	ABI class: X.Org Server Extension, version 6.0
[    22.177] (II) Loading extension XFree86-DRI
[    22.177] (II) LoadModule: "dri2"
[    22.178] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    22.178] (II) Module dri2: vendor="X.Org Foundation"
[    22.178] 	compiled for 1.11.3, module version = 1.2.0
[    22.178] 	ABI class: X.Org Server Extension, version 6.0
[    22.178] (II) Loading extension DRI2
[    22.178] (==) Matched intel as autoconfigured driver 0
[    22.178] (==) Matched vesa as autoconfigured driver 1
[    22.178] (==) Matched fbdev as autoconfigured driver 2
[    22.178] (==) Assigned the driver to the xf86ConfigLayout
[    22.178] (II) LoadModule: "intel"
[    22.179] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    22.179] (II) Module intel: vendor="X.Org Foundation"
[    22.179] 	compiled for 1.11.3, module version = 2.17.0
[    22.179] 	Module class: X.Org Video Driver
[    22.179] 	ABI class: X.Org Video Driver, version 11.0
[    22.179] (II) LoadModule: "vesa"
[    22.200] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    22.200] (II) Module vesa: vendor="X.Org Foundation"
[    22.200] 	compiled for 1.11.3, module version = 2.3.0
[    22.200] 	Module class: X.Org Video Driver
[    22.200] 	ABI class: X.Org Video Driver, version 11.0
[    22.200] (II) LoadModule: "fbdev"
[    22.201] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    22.201] (II) Module fbdev: vendor="X.Org Foundation"
[    22.201] 	compiled for 1.11.3, module version = 0.4.2
[    22.201] 	ABI class: X.Org Video Driver, version 11.0
[    22.201] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
	Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
	Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
	Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
	Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server,
	Ivybridge Server (GT2)
[    22.201] (II) VESA: driver for VESA chipsets: vesa
[    22.201] (II) FBDEV: driver for framebuffer: fbdev
[    22.201] (++) using VT number 7

[    22.205] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    22.206] (WW) Falling back to old probe method for vesa
[    22.206] (WW) Falling back to old probe method for fbdev
[    22.206] (II) Loading sub module "fbdevhw"
[    22.206] (II) LoadModule: "fbdevhw"
[    22.206] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    22.206] (II) Module fbdevhw: vendor="X.Org Foundation"
[    22.206] 	compiled for 1.11.3, module version = 0.0.2
[    22.206] 	ABI class: X.Org Video Driver, version 11.0
[    22.207] drmOpenDevice: node name is /dev/dri/card0
[    22.207] drmOpenDevice: open result is 9, (OK)
[    22.207] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    22.207] drmOpenDevice: node name is /dev/dri/card0
[    22.207] drmOpenDevice: open result is 9, (OK)
[    22.207] drmOpenByBusid: drmOpenMinor returns 9
[    22.207] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    22.207] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    22.207] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    22.207] (==) intel(0): RGB weight 888
[    22.207] (==) intel(0): Default visual is TrueColor
[    22.207] (II) intel(0): Integrated Graphics Chipset: Intel(R) 845G
[    22.207] (--) intel(0): Chipset: "845G"
[    22.207] (**) intel(0): Relaxed fencing disabled
[    22.207] (**) intel(0): Wait on SwapBuffers? enabled
[    22.207] (**) intel(0): Triple buffering? enabled
[    22.207] (**) intel(0): Framebuffer tiled
[    22.207] (**) intel(0): Pixmaps tiled
[    22.207] (**) intel(0): 3D buffers tiled
[    22.207] (**) intel(0): SwapBuffers wait enabled
[    22.207] (==) intel(0): video overlay key set to 0x101fe
[    22.633] (II) intel(0): Output VGA1 has no monitor section
[    23.034] (II) intel(0): EDID for output VGA1
[    23.034] (II) intel(0): Manufacturer: DEL  Model: a005  Serial#: 827152725
[    23.034] (II) intel(0): Year: 2003  Week: 43
[    23.034] (II) intel(0): EDID Version: 1.3
[    23.034] (II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[    23.034] (II) intel(0): Sync:  Separate
[    23.034] (II) intel(0): Max Image Size [cm]: horiz.: 31  vert.: 23
[    23.034] (II) intel(0): Gamma: 2.20
[    23.034] (II) intel(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    23.034] (II) intel(0): Default color space is primary color space
[    23.034] (II) intel(0): First detailed timing is preferred mode
[    23.034] (II) intel(0): redX: 0.640 redY: 0.340   greenX: 0.279 greenY: 0.619
[    23.034] (II) intel(0): blueX: 0.140 blueY: 0.069   whiteX: 0.310 whiteY: 0.330
[    23.034] (II) intel(0): Supported established timings:
[    23.034] (II) intel(0): 720x400@70Hz
[    23.034] (II) intel(0): 640x480@60Hz
[    23.034] (II) intel(0): 640x480@75Hz
[    23.034] (II) intel(0): 800x600@60Hz
[    23.034] (II) intel(0): 800x600@75Hz
[    23.034] (II) intel(0): 1024x768@60Hz
[    23.034] (II) intel(0): 1024x768@75Hz
[    23.034] (II) intel(0): Manufacturer's mask: 0
[    23.034] (II) intel(0): Supported detailed timing:
[    23.034] (II) intel(0): clock: 65.0 MHz   Image Size:  304 x 228 mm
[    23.034] (II) intel(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
[    23.034] (II) intel(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
[    23.034] (II) intel(0): Serial No: 8W2343AK1MYU
[    23.034] (II) intel(0): Monitor name: DELL E151FPb
[    23.034] (II) intel(0): Ranges: V min: 56 V max: 76 Hz, H min: 31 H max: 60 kHz, PixClock max 85 MHz
[    23.034] (II) intel(0): EDID (in hex):
[    23.034] (II) intel(0): 	00ffffffffffff0010ac05a055594d31
[    23.034] (II) intel(0): 	2b0d0103681f1778eecaf6a357479e23
[    23.034] (II) intel(0): 	114f54a54a0001010101010101010101
[    23.035] (II) intel(0): 	01010101010164190040410026301888
[    23.035] (II) intel(0): 	360030e410000018000000ff00385732
[    23.035] (II) intel(0): 	333433414b314d595520000000fc0044
[    23.035] (II) intel(0): 	454c4c20453135314650620a000000fd
[    23.035] (II) intel(0): 	00384c1f3c08000a2020202020200063
[    23.035] (II) intel(0): EDID vendor "DEL", prod id 40965
[    23.035] (II) intel(0): Using EDID range info for horizontal sync
[    23.035] (II) intel(0): Using EDID range info for vertical refresh
[    23.035] (II) intel(0): Printing DDC gathered Modelines:
[    23.035] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -
vsync (48.4 kHz)
[    23.035] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsyn
c (37.9 kHz)
[    23.035] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
 (37.5 kHz)
[    23.035] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync
 (31.5 kHz)
[    23.035] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
 (31.5 kHz)
[    23.035] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +
vsync (60.0 kHz)
[    23.035] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsyn
c (46.9 kHz)
[    23.035] (II) intel(0): Printing probed modes for output VGA1
[    23.035] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync 
-vsync (48.4 kHz)
[    23.035] (II) intel(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync 
+vsync (60.1 kHz)
[    23.035] (II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsy
nc (46.9 kHz)
[    23.035] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsy
nc (37.9 kHz)
[    23.035] (II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsyn
c (37.5 kHz)
[    23.035] (II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsyn
c (31.5 kHz)
[    23.035] (II) intel(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsyn
c (31.5 kHz)
[    23.035] (II) intel(0): Output VGA1 connected
[    23.035] (II) intel(0): Using exact sizes for initial modes
[    23.035] (II) intel(0): Output VGA1 using initial mode 1024x768
[    23.035] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    23.035] (II) intel(0): Kernel page flipping support detected, enabling
[    23.035] (**) intel(0): Display dimensions: (310, 230) mm
[    23.035] (**) intel(0): DPI set to (83, 84)
[    23.035] (II) Loading sub module "fb"
[    23.035] (II) LoadModule: "fb"
[    23.045] (II) Loading /usr/lib/xorg/modules/libfb.so
[    23.045] (II) Module fb: vendor="X.Org Foundation"
[    23.045] 	compiled for 1.11.3, module version = 1.0.0
[    23.045] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    23.045] (II) Loading sub module "dri2"
[    23.045] (II) LoadModule: "dri2"
[    23.046] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    23.046] (II) Module dri2: vendor="X.Org Foundation"
[    23.046] 	compiled for 1.11.3, module version = 1.2.0
[    23.046] 	ABI class: X.Org Server Extension, version 6.0
[    23.046] (II) UnloadModule: "vesa"
[    23.046] (II) Unloading vesa
[    23.046] (II) UnloadModule: "fbdev"
[    23.046] (II) Unloading fbdev
[    23.046] (II) UnloadModule: "fbdevhw"
[    23.046] (II) Unloading fbdevhw
[    23.046] (==) Depth 24 pixmap format is 32 bpp
[    23.046] (II) intel(0): [DRI2] Setup complete
[    23.046] (II) intel(0): [DRI2]   DRI driver: i915
[    23.046] (II) intel(0): Allocated new frame buffer 1024x768 stride 4096, tiled
[    23.046] (II) UXA(0): Driver registered support for the following operations:
[    23.046] (II)         solid
[    23.046] (II)         copy
[    23.046] (II)         composite (RENDER acceleration)
[    23.046] (II)         put_image
[    23.046] (II)         get_image
[    23.046] (==) intel(0): Backing store disabled
[    23.046] (==) intel(0): Silken mouse enabled
[    23.046] (II) intel(0): Initializing HW Cursor
[    23.095] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    23.145] (==) intel(0): DPMS enabled
[    23.145] (==) intel(0): Intel XvMC decoder disabled
[    23.145] (II) intel(0): Set up overlay video
[    23.145] (II) intel(0): direct rendering: DRI2 Enabled
[    23.145] (==) intel(0): hotplug detection: "enabled"
[    23.146] (--) RandR disabled
[    23.146] (II) Initializing built-in extension Generic Event Extension
[    23.146] (II) Initializing built-in extension SHAPE
[    23.146] (II) Initializing built-in extension MIT-SHM
[    23.146] (II) Initializing built-in extension XInputExtension
[    23.146] (II) Initializing built-in extension XTEST
[    23.146] (II) Initializing built-in extension BIG-REQUESTS
[    23.146] (II) Initializing built-in extension SYNC
[    23.146] (II) Initializing built-in extension XKEYBOARD
[    23.146] (II) Initializing built-in extension XC-MISC
[    23.146] (II) Initializing built-in extension SECURITY
[    23.146] (II) Initializing built-in extension XINERAMA
[    23.146] (II) Initializing built-in extension XFIXES
[    23.146] (II) Initializing built-in extension RENDER
[    23.146] (II) Initializing built-in extension RANDR
[    23.146] (II) Initializing built-in extension COMPOSITE
[    23.146] (II) Initializing built-in extension DAMAGE
[    23.232] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    23.232] (II) AIGLX: enabled GLX_INTEL_swap_event
[    23.232] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    23.232] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    23.233] (II) AIGLX: Loaded and initialized i915
[    23.233] (II) GLX: Initialized DRI2 GL provider for screen 0
[    23.234] (II) intel(0): Setting screen physical size to 270 x 203
[    23.338] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    23.359] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    23.360] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    23.360] (II) LoadModule: "evdev"
[    23.360] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.360] (II) Module evdev: vendor="X.Org Foundation"
[    23.360] 	compiled for 1.11.3, module version = 2.7.0
[    23.360] 	Module class: X.Org XInput Driver
[    23.360] 	ABI class: X.Org XInput driver, version 16.0
[    23.360] (II) Using input driver 'evdev' for 'Power Button'
[    23.360] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.361] (**) Power Button: always reports core events
[    23.361] (**) evdev: Power Button: Device: "/dev/input/event1"
[    23.361] (--) evdev: Power Button: Vendor 0 Product 0x1
[    23.361] (--) evdev: Power Button: Found keys
[    23.361] (II) evdev: Power Button: Configuring as keyboard
[    23.361] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    23.361] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    23.361] (**) Option "xkb_rules" "evdev"
[    23.361] (**) Option "xkb_model" "pc105"
[    23.361] (**) Option "xkb_layout" "us"
[    23.362] (II) config/udev: Adding input device Sleep Button (/dev/input/event0)
[    23.362] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    23.362] (II) Using input driver 'evdev' for 'Sleep Button'
[    23.362] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.362] (**) Sleep Button: always reports core events
[    23.362] (**) evdev: Sleep Button: Device: "/dev/input/event0"
[    23.362] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    23.362] (--) evdev: Sleep Button: Found keys
[    23.362] (II) evdev: Sleep Button: Configuring as keyboard
[    23.362] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0/
event0"
[    23.362] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 7)
[    23.363] (**) Option "xkb_rules" "evdev"
[    23.363] (**) Option "xkb_model" "pc105"
[    23.363] (**) Option "xkb_layout" "us"
[    23.375] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    23.375] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    23.375] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    23.375] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.375] (**) AT Translated Set 2 keyboard: always reports core events
[    23.375] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    23.375] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    23.376] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    23.376] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    23.376] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    23.376] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 
8)
[    23.376] (**) Option "xkb_rules" "evdev"
[    23.376] (**) Option "xkb_model" "pc105"
[    23.376] (**) Option "xkb_layout" "us"
[    23.377] (II) config/udev: Adding input device ImPS/2 Logitech Wheel Mouse (/dev/input/event3)
[    23.377] (**) ImPS/2 Logitech Wheel Mouse: Applying InputClass "evdev pointer catchall"
[    23.377] (II) Using input driver 'evdev' for 'ImPS/2 Logitech Wheel Mouse'
[    23.377] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.377] (**) ImPS/2 Logitech Wheel Mouse: always reports core events
[    23.377] (**) evdev: ImPS/2 Logitech Wheel Mouse: Device: "/dev/input/event3"
[    23.377] (--) evdev: ImPS/2 Logitech Wheel Mouse: Vendor 0x2 Product 0x5
[    23.377] (--) evdev: ImPS/2 Logitech Wheel Mouse: Found 3 mouse buttons
[    23.377] (--) evdev: ImPS/2 Logitech Wheel Mouse: Found scroll wheel(s)
[    23.377] (--) evdev: ImPS/2 Logitech Wheel Mouse: Found relative axes
[    23.377] (--) evdev: ImPS/2 Logitech Wheel Mouse: Found x and y relative axes
[    23.377] (II) evdev: ImPS/2 Logitech Wheel Mouse: Configuring as mouse
[    23.377] (II) evdev: ImPS/2 Logitech Wheel Mouse: Adding scrollwheel support
[    23.377] (**) evdev: ImPS/2 Logitech Wheel Mouse: YAxisMapping: buttons 4 and 5
[    23.377] (**) evdev: ImPS/2 Logitech Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, Emul
ateWheelTimeout: 200
[    23.377] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input3/event3"
[    23.377] (II) XINPUT: Adding extended input device "ImPS/2 Logitech Wheel Mouse" (type: MOUSE, id 9)
[    23.378] (II) evdev: ImPS/2 Logitech Wheel Mouse: initialized for relative axes.
[    23.378] (**) ImPS/2 Logitech Wheel Mouse: (accel) keeping acceleration scheme 1
[    23.378] (**) ImPS/2 Logitech Wheel Mouse: (accel) acceleration profile 0
[    23.378] (**) ImPS/2 Logitech Wheel Mouse: (accel) acceleration factor: 2.000
[    23.378] (**) ImPS/2 Logitech Wheel Mouse: (accel) acceleration threshold: 4
[    23.386] (II) config/udev: Adding input device ImPS/2 Logitech Wheel Mouse (/dev/input/mouse0)
[    23.386] (II) No input driver specified, ignoring this device.
[    23.386] (II) This device may have been added with another device file.
[    25.505] (II) intel(0): EDID vendor "DEL", prod id 40965
[    25.505] (II) intel(0): Using hsync ranges from config file
[    25.505] (II) intel(0): Using vrefresh ranges from config file
[    25.505] (II) intel(0): Printing DDC gathered Modelines:
[    25.505] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -
vsync (48.4 kHz)
[    25.505] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsyn
c (37.9 kHz)
[    25.505] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
 (37.5 kHz)
[    25.505] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync
 (31.5 kHz)
[    25.505] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
 (31.5 kHz)
[    25.505] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +
vsync (60.0 kHz)
[    25.505] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsyn
c (46.9 kHz)
[    31.992] (II) intel(0): EDID vendor "DEL", prod id 40965
[    31.995] (II) intel(0): Using hsync ranges from config file
[    31.995] (II) intel(0): Using vrefresh ranges from config file
[    31.995] (II) intel(0): Printing DDC gathered Modelines:
[    31.995] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -
vsync (48.4 kHz)
[    31.995] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsyn
c (37.9 kHz)
[    31.995] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
 (37.5 kHz)
[    31.995] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync
 (31.5 kHz)
[    31.995] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
 (31.5 kHz)
[    31.995] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +
vsync (60.0 kHz)
[    31.995] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsyn
c (46.9 kHz)
[    48.501] (II) intel(0): EDID vendor "DEL", prod id 40965
[    48.501] (II) intel(0): Using hsync ranges from config file
[    48.501] (II) intel(0): Using vrefresh ranges from config file
[    48.501] (II) intel(0): Printing DDC gathered Modelines:
[    48.501] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -
vsync (48.4 kHz)
[    48.501] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsyn
c (37.9 kHz)
[    48.501] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
 (37.5 kHz)
[    48.501] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync
 (31.5 kHz)
[    48.501] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
 (31.5 kHz)
[    48.501] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +
vsync (60.0 kHz)
[    48.501] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsyn
c (46.9 kHz)
[    49.628] (II) intel(0): EDID vendor "DEL", prod id 40965
[    49.628] (II) intel(0): Using hsync ranges from config file
[    49.628] (II) intel(0): Using vrefresh ranges from config file
[    49.628] (II) intel(0): Printing DDC gathered Modelines:
[    49.628] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -
vsync (48.4 kHz)
[    49.628] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsyn
c (37.9 kHz)
[    49.628] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
 (37.5 kHz)
[    49.628] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync
 (31.5 kHz)
[    49.628] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
 (31.5 kHz)
[    49.628] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +
vsync (60.0 kHz)
[    49.628] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsyn
c (46.9 kHz)
[    51.002] (II) XKB: reuse xkmfile /var/lib/xkb/server-03AF3717FF3AB439A4BAABA686CCB40771CDF520.xkm
[    81.674] (II) intel(0): EDID vendor "DEL", prod id 40965
[    81.674] (II) intel(0): Using hsync ranges from config file
[    81.674] (II) intel(0): Using vrefresh ranges from config file
[    81.674] (II) intel(0): Printing DDC gathered Modelines:
[    81.674] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -
vsync (48.4 kHz)
[    81.674] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsyn
c (37.9 kHz)
[    81.675] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
 (37.5 kHz)
[    81.675] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync
 (31.5 kHz)
[    81.675] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
 (31.5 kHz)
[    81.675] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +
vsync (60.0 kHz)
[    81.675] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsyn
c (46.9 kHz)
[  1907.122] (II) intel(0): EDID vendor "DEL", prod id 40965
[  1907.122] (II) intel(0): Using hsync ranges from config file
[  1907.122] (II) intel(0): Using vrefresh ranges from config file
[  1907.122] (II) intel(0): Printing DDC gathered Modelines:
[  1907.122] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -
vsync (48.4 kHz)
[  1907.122] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsyn
c (37.9 kHz)
[  1907.122] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
 (37.5 kHz)
[  1907.122] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync
 (31.5 kHz)
[  1907.122] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
 (31.5 kHz)
[  1907.122] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +
vsync (60.0 kHz)
[  1907.122] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsyn
c (46.9 kHz)
[  4949.616] (II) AIGLX: Suspending AIGLX clients for VT switch
[  4964.925] (II) Open ACPI successful (/var/run/acpid.socket)
[  4964.926] (II) AIGLX: Resuming AIGLX clients after VT switch
[  4965.229] (II) intel(0): EDID vendor "DEL", prod id 40965
[  4965.229] (II) intel(0): Using hsync ranges from config file
[  4965.229] (II) intel(0): Using vrefresh ranges from config file
[  4965.229] (II) intel(0): Printing DDC gathered Modelines:
[  4965.229] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -
vsync (48.4 kHz)
[  4965.229] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsyn
c (37.9 kHz)
[  4965.229] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
 (37.5 kHz)
[  4965.229] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync
 (31.5 kHz)
[  4965.229] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
 (31.5 kHz)
[  4965.229] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +
vsync (60.0 kHz)
[  4965.229] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsyn
c (46.9 kHz)
[ 12072.120] (II) AIGLX: Suspending AIGLX clients for VT switch
[ 12087.643] (II) Open ACPI successful (/var/run/acpid.socket)
[ 12087.643] (II) AIGLX: Resuming AIGLX clients after VT switch
[ 12087.890] (II) intel(0): EDID vendor "DEL", prod id 40965
[ 12087.890] (II) intel(0): Using hsync ranges from config file
[ 12087.890] (II) intel(0): Using vrefresh ranges from config file
[ 12087.890] (II) intel(0): Printing DDC gathered Modelines:
[ 12087.890] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -
vsync (48.4 kHz)
[ 12087.890] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsyn
c (37.9 kHz)
[ 12087.890] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
 (37.5 kHz)
[ 12087.890] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync
 (31.5 kHz)
[ 12087.890] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
 (31.5 kHz)
[ 12087.890] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +
vsync (60.0 kHz)
[ 12087.890] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsyn
c (46.9 kHz)
[ 15740.712] (II) AIGLX: Suspending AIGLX clients for VT switch
[ 15756.038] (II) Open ACPI successful (/var/run/acpid.socket)
[ 15756.038] (II) AIGLX: Resuming AIGLX clients after VT switch
[ 15756.317] (II) intel(0): EDID vendor "DEL", prod id 40965
[ 15756.317] (II) intel(0): Using hsync ranges from config file
[ 15756.317] (II) intel(0): Using vrefresh ranges from config file
[ 15756.317] (II) intel(0): Printing DDC gathered Modelines:
[ 15756.317] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -
vsync (48.4 kHz)
[ 15756.318] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsyn
c (37.9 kHz)
[ 15756.318] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
 (37.5 kHz)
[ 15756.318] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync
 (31.5 kHz)
[ 15756.318] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
 (31.5 kHz)
[ 15756.318] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +
vsync (60.0 kHz)
[ 15756.318] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsyn
c (46.9 kHz)
[ 19416.075] (II) AIGLX: Suspending AIGLX clients for VT switch
[ 19431.457] (II) Open ACPI successful (/var/run/acpid.socket)
[ 19431.457] (II) AIGLX: Resuming AIGLX clients after VT switch
[ 19431.735] (II) intel(0): EDID vendor "DEL", prod id 40965
[ 19431.735] (II) intel(0): Using hsync ranges from config file
[ 19431.735] (II) intel(0): Using vrefresh ranges from config file
[ 19431.735] (II) intel(0): Printing DDC gathered Modelines:
[ 19431.735] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -
vsync (48.4 kHz)
[ 19431.735] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsyn
c (37.9 kHz)
[ 19431.735] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
 (37.5 kHz)
[ 19431.735] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync
 (31.5 kHz)
[ 19431.735] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
 (31.5 kHz)
[ 19431.735] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +
vsync (60.0 kHz)
[ 19431.735] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsyn
c (46.9 kHz)
[ 23089.762] (II) AIGLX: Suspending AIGLX clients for VT switch
[ 23106.789] (II) Open ACPI successful (/var/run/acpid.socket)
[ 23106.789] (II) AIGLX: Resuming AIGLX clients after VT switch
[ 23107.098] (II) intel(0): EDID vendor "DEL", prod id 40965
[ 23107.098] (II) intel(0): Using hsync ranges from config file
[ 23107.098] (II) intel(0): Using vrefresh ranges from config file
[ 23107.098] (II) intel(0): Printing DDC gathered Modelines:
[ 23107.098] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -
vsync (48.4 kHz)
[ 23107.098] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsyn
c (37.9 kHz)
[ 23107.098] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
 (37.5 kHz)
[ 23107.098] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync
 (31.5 kHz)
[ 23107.098] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
 (31.5 kHz)
[ 23107.098] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +
vsync (60.0 kHz)
[ 23107.098] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsyn
c (46.9 kHz)
[ 23125.123] (II) XKB: reuse xkmfile /var/lib/xkb/server-03AF3717FF3AB439A4BAABA686CCB40771CDF520.xkm
[ 24201.187] (II) intel(0): EDID vendor "DEL", prod id 40965
[ 24201.231] (II) intel(0): Using hsync ranges from config file
[ 24201.231] (II) intel(0): Using vrefresh ranges from config file
[ 24201.231] (II) intel(0): Printing DDC gathered Modelines:
[ 24201.231] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -
vsync (48.4 kHz)
[ 24201.231] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsyn
c (37.9 kHz)
[ 24201.231] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
 (37.5 kHz)
[ 24201.231] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync
 (31.5 kHz)
[ 24201.231] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
 (31.5 kHz)
[ 24201.231] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +
vsync (60.0 kHz)
[ 24201.231] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsyn
c (46.9 kHz)
[ 24211.204] (II) intel(0): EDID vendor "DEL", prod id 40965
[ 24211.204] (II) intel(0): Using hsync ranges from config file
[ 24211.204] (II) intel(0): Using vrefresh ranges from config file
[ 24211.204] (II) intel(0): Printing DDC gathered Modelines:
[ 24211.204] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -
vsync (48.4 kHz)
[ 24211.204] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsyn
c (37.9 kHz)
[ 24211.204] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
 (37.5 kHz)
[ 24211.204] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync
 (31.5 kHz)
[ 24211.204] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
 (31.5 kHz)
[ 24211.204] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +
vsync (60.0 kHz)
[ 24211.204] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsyn
c (46.9 kHz)
[ 27072.164] (II) intel(0): EDID vendor "DEL", prod id 40965
[ 27072.164] (II) intel(0): Using hsync ranges from config file
[ 27072.164] (II) intel(0): Using vrefresh ranges from config file
[ 27072.164] (II) intel(0): Printing DDC gathered Modelines:
[ 27072.164] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -
vsync (48.4 kHz)
[ 27072.164] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsyn
c (37.9 kHz)
[ 27072.164] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
 (37.5 kHz)
[ 27072.164] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync
 (31.5 kHz)
[ 27072.164] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
 (31.5 kHz)
[ 27072.164] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +
vsync (60.0 kHz)
[ 27072.164] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsyn
c (46.9 kHz)
[ 30117.234] (II) AIGLX: Suspending AIGLX clients for VT switch
[ 30133.174] (II) Open ACPI successful (/var/run/acpid.socket)
[ 30133.175] (II) AIGLX: Resuming AIGLX clients after VT switch
[ 30133.440] (II) intel(0): EDID vendor "DEL", prod id 40965
[ 30133.441] (II) intel(0): Using hsync ranges from config file
[ 30133.441] (II) intel(0): Using vrefresh ranges from config file
[ 30133.441] (II) intel(0): Printing DDC gathered Modelines:
[ 30133.441] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -
vsync (48.4 kHz)
[ 30133.441] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsyn
c (37.9 kHz)
[ 30133.441] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
 (37.5 kHz)
[ 30133.441] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync
 (31.5 kHz)
[ 30133.441] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
 (31.5 kHz)
[ 30133.441] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +
vsync (60.0 kHz)
[ 30133.441] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsyn
c (46.9 kHz)
[ 33785.366] (II) AIGLX: Suspending AIGLX clients for VT switch
[ 33801.189] (II) Open ACPI successful (/var/run/acpid.socket)
[ 33801.189] (II) AIGLX: Resuming AIGLX clients after VT switch
[ 33801.381] (II) intel(0): EDID vendor "DEL", prod id 40965
[ 33801.381] (II) intel(0): Using hsync ranges from config file
[ 33801.381] (II) intel(0): Using vrefresh ranges from config file
[ 33801.397] (II) intel(0): Printing DDC gathered Modelines:
[ 33801.397] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -
vsync (48.4 kHz)
[ 33801.397] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsyn
c (37.9 kHz)
[ 33801.397] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
 (37.5 kHz)
[ 33801.397] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync
 (31.5 kHz)
[ 33801.397] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
 (31.5 kHz)
[ 33801.397] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +
vsync (60.0 kHz)
[ 33801.397] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsyn
c (46.9 kHz)
[ 37453.960] (II) AIGLX: Suspending AIGLX clients for VT switch
[ 37469.760] (II) Open ACPI successful (/var/run/acpid.socket)
[ 37469.760] (II) AIGLX: Resuming AIGLX clients after VT switch
[ 37469.970] (II) intel(0): EDID vendor "DEL", prod id 40965
[ 37469.970] (II) intel(0): Using hsync ranges from config file
[ 37469.970] (II) intel(0): Using vrefresh ranges from config file
[ 37469.970] (II) intel(0): Printing DDC gathered Modelines:
[ 37469.970] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -
vsync (48.4 kHz)
[ 37469.970] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsyn
c (37.9 kHz)
[ 37469.970] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
 (37.5 kHz)
[ 37469.970] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync
 (31.5 kHz)
[ 37469.970] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
 (31.5 kHz)
[ 37469.970] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +
vsync (60.0 kHz)
[ 37469.970] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsyn
c (46.9 kHz)
[ 41129.577] (II) AIGLX: Suspending AIGLX clients for VT switch
[ 41145.013] (II) Open ACPI successful (/var/run/acpid.socket)
[ 41145.013] (II) AIGLX: Resuming AIGLX clients after VT switch
[ 41145.422] (II) intel(0): EDID vendor "DEL", prod id 40965
[ 41145.422] (II) intel(0): Using hsync ranges from config file
[ 41145.423] (II) intel(0): Using vrefresh ranges from config file
[ 41145.423] (II) intel(0): Printing DDC gathered Modelines:
[ 41145.423] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -
vsync (48.4 kHz)
[ 41145.423] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsyn
c (37.9 kHz)
[ 41145.423] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
 (37.5 kHz)
[ 41145.423] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync
 (31.5 kHz)
[ 41145.423] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
 (31.5 kHz)
[ 41145.423] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +
vsync (60.0 kHz)
[ 41145.423] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsyn
c (46.9 kHz)
[ 44804.284] (II) AIGLX: Suspending AIGLX clients for VT switch
[ 44820.288] (II) Open ACPI successful (/var/run/acpid.socket)
[ 44820.288] (II) AIGLX: Resuming AIGLX clients after VT switch
[ 44820.577] (II) intel(0): EDID vendor "DEL", prod id 40965
[ 44820.578] (II) intel(0): Using hsync ranges from config file
[ 44820.578] (II) intel(0): Using vrefresh ranges from config file
[ 44820.578] (II) intel(0): Printing DDC gathered Modelines:
[ 44820.578] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -
vsync (48.4 kHz)
[ 44820.578] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsyn
c (37.9 kHz)
[ 44820.595] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
 (37.5 kHz)
[ 44820.595] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync
 (31.5 kHz)
[ 44820.595] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
 (31.5 kHz)
[ 44820.595] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +
vsync (60.0 kHz)
[ 44820.596] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsyn
c (46.9 kHz)
[ 44873.206] (II) XKB: reuse xkmfile /var/lib/xkb/server-03AF3717FF3AB439A4BAABA686CCB40771CDF520.xkm

---

### Post by papibe on 2014-01-06
Is the DELL E151FPb monitor you are having problems with? 

From the EDID information:
```
	# EDID version 1 revision 3
Section "Monitor"
	# Block type: 2:0 3:ff
	# Block type: 2:0 3:fc
	Identifier "DELL E151FPb"
	VendorName "DEL"
	ModelName "DELL E151FPb"
	# Block type: 2:0 3:ff
	# Block type: 2:0 3:fc
	# Block type: 2:0 3:fd
	HorizSync 31-60
	VertRefresh 56-76
	# Max dot clock (video bandwidth) 80 MHz
	# DPMS capabilities: Active off:yes  Suspend:yes  Standby:yes

	Mode 	"1024x768"	# vfreq 60.004Hz, hfreq 48.363kHz
		DotClock	65.000000
		HTimings	1024 1048 1184 1344
		VTimings	768 771 777 806
		Flags	"-HSync" "-VSync"
	EndMode
	# Block type: 2:0 3:ff
	# Block type: 2:0 3:fc
	# Block type: 2:0 3:fd
EndSection

```
Regards.

---

### Post by HDTimeshifter on 2014-01-06
No, it works with the 15" Dell LCD. The 20" Sun CRT monitor is the one that it no longer works with.

---

### Post by papibe on 2014-01-06
OK.

What you posted is the log from the other monitor. I guess you could not get any kind of display at all with the analog, and you connected the Dell again.

The problem is that is overwriting the log.

Have you tried pressing Ctrl+Alt+F1 to get a text mode prompt? If that works you could copy the log to another file, so it is available the next login (with the Dell monitor):
```
sudo cp /var/log/Xorg.0.log /var/log/Xorg.0.log.analog
```
Once you boot normally using the good monitor, please paste the 'analog' file again.

Regards.

---

