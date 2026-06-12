---
title: "Forced unity-2d on MSI GE620"
date: 2012-08-04
forum: Hardware
---

### Post by RvGaTe on 2012-08-04
Hello,

I've been trying to get the normal unity to work on my laptop with ubuntu 12.04 for a few days now without success. Ubuntu forced me to use unity-2d and i have no idea how to get it to work. I just did a fresh install on the laptop purely to fix this problem in this topic.

**The laptop:**
MSI GE620-058NL, [http://tweakers.net/pricewatch/281903/msi-ge620-058nl.html#tab:info](http://tweakers.net/pricewatch/281903/msi-ge620-058nl.html#tab:info)

**uname -a**
```
Linux rvgate-laptop 3.2.0-20-generic #33-Ubuntu SMP Tue Mar 27 16:42:26 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
```

**lspci |grep VGA**
```
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Intergrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation GF108 [GeForce GT 540M] (rev a1)
```

**/var/log/Xorg.0.log**
```
[    24.438] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    24.438] X Protocol Version 11, Revision 0
[    24.438] Build Operating System: Linux 2.6.42-26-generic x86_64 Ubuntu
[    24.438] Current Operating System: Linux rvgate-laptop 3.2.0-27-generic #43-Ubuntu SMP Fri Jul 6 14:25:57 UTC 2012 x86_64
[    24.438] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-27-generic root=UUID=5af2cc5e-297a-43be-bfaf-0278c995bbff ro quiet splash vt.handoff=7
[    24.438] Build Date: 16 July 2012  08:06:31PM
[    24.438] xorg-server 2:1.11.4-0ubuntu10.6 (For technical support please see http://www.ubuntu.com/support) 
[    24.438] Current version of pixman: 0.24.4
[    24.438] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    24.438] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    24.438] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Aug  4 18:39:37 2012
[    24.460] (==) Using config file: "/etc/X11/xorg.conf"
[    24.460] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    24.510] (==) No Layout section.  Using the first Screen section.
[    24.510] (==) No screen section available. Using defaults.
[    24.510] (**) |-->Screen "Default Screen Section" (0)
[    24.510] (**) |   |-->Monitor "<default monitor>"
[    24.511] (==) No device specified for screen "Default Screen Section".
	Using the first device section listed.
[    24.511] (**) |   |-->Device "Default Device"
[    24.511] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    24.511] (==) Automatically adding devices
[    24.511] (==) Automatically enabling devices
[    24.524] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    24.524] 	Entry deleted from font path.
[    24.524] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    24.524] 	Entry deleted from font path.
[    24.524] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    24.524] 	Entry deleted from font path.
[    24.531] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    24.531] 	Entry deleted from font path.
[    24.531] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    24.531] 	Entry deleted from font path.
[    24.541] (WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
[    24.541] 	Entry deleted from font path.
[    24.541] 	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType").
[    24.541] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    24.541] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    24.541] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    24.541] (II) Loader magic: 0x7f68beda7b00
[    24.541] (II) Module ABI versions:
[    24.541] 	X.Org ANSI C Emulation: 0.4
[    24.541] 	X.Org Video Driver: 11.0
[    24.541] 	X.Org XInput driver : 16.0
[    24.541] 	X.Org Server Extension : 6.0
[    24.542] (--) PCI:*(0:0:2:0) 8086:0116:1462:108d rev 9, Mem @ 0xf7400000/4194304, 0xd0000000/268435456, I/O @ 0x0000f000/64
[    24.542] (--) PCI: (0:1:0:0) 10de:0df4:1462:108d rev 161, Mem @ 0xf6000000/16777216, 0xe0000000/268435456, 0xf0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[    24.542] (II) Open ACPI successful (/var/run/acpid.socket)
[    24.542] (II) LoadModule: "extmod"
[    24.581] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    24.688] (II) Module extmod: vendor="X.Org Foundation"
[    24.688] 	compiled for 1.11.3, module version = 1.0.0
[    24.688] 	Module class: X.Org Server Extension
[    24.688] 	ABI class: X.Org Server Extension, version 6.0
[    24.688] (II) Loading extension MIT-SCREEN-SAVER
[    24.688] (II) Loading extension XFree86-VidModeExtension
[    24.688] (II) Loading extension XFree86-DGA
[    24.688] (II) Loading extension DPMS
[    24.688] (II) Loading extension XVideo
[    24.688] (II) Loading extension XVideo-MotionCompensation
[    24.688] (II) Loading extension X-Resource
[    24.688] (II) LoadModule: "dbe"
[    24.688] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    24.694] (II) Module dbe: vendor="X.Org Foundation"
[    24.694] 	compiled for 1.11.3, module version = 1.0.0
[    24.694] 	Module class: X.Org Server Extension
[    24.694] 	ABI class: X.Org Server Extension, version 6.0
[    24.694] (II) Loading extension DOUBLE-BUFFER
[    24.694] (II) LoadModule: "glx"
[    24.694] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    25.348] (II) Module glx: vendor="NVIDIA Corporation"
[    25.348] 	compiled for 4.0.2, module version = 1.0.0
[    25.348] 	Module class: X.Org Server Extension
[    25.348] (II) NVIDIA GLX Module  295.40  Thu Apr  5 21:57:38 PDT 2012
[    25.348] (II) Loading extension GLX
[    25.348] (II) LoadModule: "record"
[    25.348] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    25.361] (II) Module record: vendor="X.Org Foundation"
[    25.361] 	compiled for 1.11.3, module version = 1.13.0
[    25.361] 	Module class: X.Org Server Extension
[    25.361] 	ABI class: X.Org Server Extension, version 6.0
[    25.361] (II) Loading extension RECORD
[    25.361] (II) LoadModule: "dri"
[    25.361] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    25.368] (II) Module dri: vendor="X.Org Foundation"
[    25.368] 	compiled for 1.11.3, module version = 1.0.0
[    25.368] 	ABI class: X.Org Server Extension, version 6.0
[    25.368] (II) Loading extension XFree86-DRI
[    25.368] (II) LoadModule: "dri2"
[    25.368] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    25.369] (II) Module dri2: vendor="X.Org Foundation"
[    25.369] 	compiled for 1.11.3, module version = 1.2.0
[    25.369] 	ABI class: X.Org Server Extension, version 6.0
[    25.369] (II) Loading extension DRI2
[    25.369] (==) Matched intel as autoconfigured driver 0
[    25.369] (==) Matched vesa as autoconfigured driver 1
[    25.369] (==) Matched fbdev as autoconfigured driver 2
[    25.369] (==) Assigned the driver to the xf86ConfigLayout
[    25.369] (II) LoadModule: "intel"
[    25.389] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    25.404] (II) Module intel: vendor="X.Org Foundation"
[    25.404] 	compiled for 1.11.3, module version = 2.17.0
[    25.404] 	Module class: X.Org Video Driver
[    25.404] 	ABI class: X.Org Video Driver, version 11.0
[    25.404] (II) LoadModule: "vesa"
[    25.404] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    25.408] (II) Module vesa: vendor="X.Org Foundation"
[    25.408] 	compiled for 1.11.3, module version = 2.3.0
[    25.408] 	Module class: X.Org Video Driver
[    25.408] 	ABI class: X.Org Video Driver, version 11.0
[    25.408] (II) LoadModule: "fbdev"
[    25.408] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    25.409] (II) Module fbdev: vendor="X.Org Foundation"
[    25.409] 	compiled for 1.11.3, module version = 0.4.2
[    25.409] 	ABI class: X.Org Video Driver, version 11.0
[    25.420] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
	Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
	Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
	Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
	Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server
[    25.420] (II) VESA: driver for VESA chipsets: vesa
[    25.420] (II) FBDEV: driver for framebuffer: fbdev
[    25.420] (++) using VT number 7

[    25.422] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    25.422] (WW) Falling back to old probe method for vesa
[    25.422] (WW) Falling back to old probe method for fbdev
[    25.422] (II) Loading sub module "fbdevhw"
[    25.422] (II) LoadModule: "fbdevhw"
[    25.422] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    25.431] (II) Module fbdevhw: vendor="X.Org Foundation"
[    25.431] 	compiled for 1.11.3, module version = 0.0.2
[    25.431] 	ABI class: X.Org Video Driver, version 11.0
[    25.431] drmOpenDevice: node name is /dev/dri/card0
[    25.431] drmOpenDevice: open result is 9, (OK)
[    25.431] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    25.431] drmOpenDevice: node name is /dev/dri/card0
[    25.431] drmOpenDevice: open result is 9, (OK)
[    25.431] drmOpenByBusid: drmOpenMinor returns 9
[    25.431] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    25.431] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    25.431] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    25.431] (==) intel(0): RGB weight 888
[    25.431] (==) intel(0): Default visual is TrueColor
[    25.431] (II) intel(0): Integrated Graphics Chipset: Intel(R) Sandybridge Mobile (GT2)
[    25.431] (--) intel(0): Chipset: "Sandybridge Mobile (GT2)"
[    25.431] (**) intel(0): Relaxed fencing enabled
[    25.431] (**) intel(0): Wait on SwapBuffers? enabled
[    25.431] (**) intel(0): Triple buffering? enabled
[    25.431] (**) intel(0): Framebuffer tiled
[    25.431] (**) intel(0): Pixmaps tiled
[    25.431] (**) intel(0): 3D buffers tiled
[    25.431] (**) intel(0): SwapBuffers wait enabled
[    25.431] (==) intel(0): video overlay key set to 0x101fe
[    25.432] (II) intel(0): Output LVDS1 has no monitor section
[    25.432] (II) intel(0): found backlight control interface /sys/class/backlight/acpi_video1
[    25.493] (II) intel(0): Output VGA1 has no monitor section
[    25.498] (II) intel(0): Output HDMI1 has no monitor section
[    25.544] (II) intel(0): Output DP1 has no monitor section
[    25.544] (II) intel(0): EDID for output LVDS1
[    25.544] (II) intel(0): Manufacturer: SEC  Model: 3651  Serial#: 0
[    25.544] (II) intel(0): Year: 2008  Week: 0
[    25.544] (II) intel(0): EDID Version: 1.3
[    25.544] (II) intel(0): Digital Display Input
[    25.544] (II) intel(0): Max Image Size [cm]: horiz.: 34  vert.: 19
[    25.544] (II) intel(0): Gamma: 2.20
[    25.544] (II) intel(0): No DPMS capabilities specified
[    25.544] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    25.544] (II) intel(0): First detailed timing is preferred mode
[    25.544] (II) intel(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
[    25.544] (II) intel(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
[    25.544] (II) intel(0): Manufacturer's mask: 0
[    25.544] (II) intel(0): Supported detailed timing:
[    25.544] (II) intel(0): clock: 69.3 MHz   Image Size:  344 x 194 mm
[    25.544] (II) intel(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1480 h_border: 0
[    25.544] (II) intel(0): v_active: 768  v_sync: 770  v_sync_end 775 v_blanking: 780 v_border: 0
[    25.544] (II) intel(0): Unknown vendor-specific block f
[    25.544] (II) intel(0):  SAMSUNG
[    25.544] (II) intel(0):  156AT05-H01
[    25.544] (II) intel(0): EDID (in hex):
[    25.544] (II) intel(0): 	00ffffffffffff004ca3513600000000
[    25.544] (II) intel(0): 	00120103802213780a87f594574f8c27
[    25.544] (II) intel(0): 	27505400000001010101010101010101
[    25.544] (II) intel(0): 	010101010101121b567250000c303020
[    25.544] (II) intel(0): 	250058c2100000190000000f00000000
[    25.544] (II) intel(0): 	00000000001eb4027400000000fe0053
[    25.544] (II) intel(0): 	414d53554e470a2020202020000000fe
[    25.544] (II) intel(0): 	00313536415430352d4830310a200015
[    25.544] (II) intel(0): EDID vendor "SEC", prod id 13905
[    25.544] (II) intel(0): Printing DDC gathered Modelines:
[    25.544] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1480  768 770 775 780 -hsync -vsync (46.8 kHz)
[    25.544] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    25.544] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    25.544] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    25.544] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    25.544] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    25.544] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    25.544] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    25.544] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    25.544] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    25.544] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    25.544] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    25.544] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    25.544] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    25.544] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    25.544] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    25.544] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    25.544] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    25.544] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    25.544] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    25.544] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    25.544] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    25.544] (II) intel(0): Printing probed modes for output LVDS1
[    25.544] (II) intel(0): Modeline "1366x768"x60.0   69.30  1366 1414 1446 1480  768 770 775 780 -hsync -vsync (46.8 kHz)
[    25.544] (II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    25.544] (II) intel(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz)
[    25.544] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    25.544] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    25.544] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    25.544] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    25.606] (II) intel(0): EDID for output VGA1
[    25.606] (II) intel(0): Manufacturer: SAM  Model: 586  Serial#: 1297691188
[    25.606] (II) intel(0): Year: 2009  Week: 50
[    25.606] (II) intel(0): EDID Version: 1.3
[    25.606] (II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[    25.606] (II) intel(0): Sync:  Separate  Composite  SyncOnGreen
[    25.606] (II) intel(0): Max Image Size [cm]: horiz.: 52  vert.: 32
[    25.606] (II) intel(0): Gamma: 2.20
[    25.606] (II) intel(0): DPMS capabilities: Off; RGB/Color Display
[    25.606] (II) intel(0): First detailed timing is preferred mode
[    25.606] (II) intel(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
[    25.606] (II) intel(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
[    25.606] (II) intel(0): Supported established timings:
[    25.606] (II) intel(0): 640x480@60Hz
[    25.606] (II) intel(0): 800x600@56Hz
[    25.606] (II) intel(0): 800x600@60Hz
[    25.606] (II) intel(0): 1024x768@60Hz
[    25.606] (II) intel(0): Manufacturer's mask: 0
[    25.606] (II) intel(0): Supported standard timings:
[    25.606] (II) intel(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
[    25.606] (II) intel(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    25.606] (II) intel(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    25.606] (II) intel(0): #3: hsize: 1280  vsize 800  refresh: 60  vid: 129
[    25.606] (II) intel(0): #4: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    25.606] (II) intel(0): #5: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[    25.606] (II) intel(0): Supported detailed timing:
[    25.606] (II) intel(0): clock: 154.0 MHz   Image Size:  518 x 324 mm
[    25.606] (II) intel(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
[    25.606] (II) intel(0): v_active: 1200  v_sync: 1203  v_sync_end 1209 v_blanking: 1235 v_border: 0
[    25.606] (II) intel(0): Ranges: V min: 56 V max: 60 Hz, H min: 30 H max: 81 kHz, PixClock max 175 MHz
[    25.606] (II) intel(0): Monitor name: SyncMaster
[    25.606] (II) intel(0): Serial No: H9XSC02525
[    25.606] (II) intel(0): EDID (in hex):
[    25.606] (II) intel(0): 	00ffffffffffff004c2d86053432594d
[    25.606] (II) intel(0): 	321301030e3420782aee91a3544c9926
[    25.606] (II) intel(0): 	0f5054230800a9408180814081009500
[    25.606] (II) intel(0): 	b30001010101283c80a070b023403020
[    25.606] (II) intel(0): 	360006442100001a000000fd00383c1e
[    25.606] (II) intel(0): 	5111000a202020202020000000fc0053
[    25.606] (II) intel(0): 	796e634d61737465720a2020000000ff
[    25.606] (II) intel(0): 	00483958534330323532350a20200000
[    25.606] (II) intel(0): Printing probed modes for output VGA1
[    25.606] (II) intel(0): Modeline "1920x1200"x60.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
[    25.606] (II) intel(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[    25.606] (II) intel(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[    25.606] (II) intel(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    25.606] (II) intel(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    25.606] (II) intel(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    25.606] (II) intel(0): Modeline "1280x800"x59.8   83.50  1280 1352 1480 1680  800 803 809 831 +hsync -vsync (49.7 kHz)
[    25.606] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    25.606] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    25.606] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    25.606] (II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    25.611] (II) intel(0): EDID for output HDMI1
[    25.656] (II) intel(0): EDID for output DP1
[    25.656] (II) intel(0): Output LVDS1 connected
[    25.656] (II) intel(0): Output VGA1 connected
[    25.656] (II) intel(0): Output HDMI1 disconnected
[    25.656] (II) intel(0): Output DP1 disconnected
[    25.656] (II) intel(0): Using fuzzy aspect match for initial modes
[    25.656] (II) intel(0): Output LVDS1 using initial mode 1024x768
[    25.656] (II) intel(0): Output VGA1 using initial mode 1024x768
[    25.656] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    25.656] (II) intel(0): Kernel page flipping support detected, enabling
[    25.656] (**) intel(0): Display dimensions: (340, 190) mm
[    25.656] (**) intel(0): DPI set to (76, 102)
[    25.656] (II) Loading sub module "fb"
[    25.656] (II) LoadModule: "fb"
[    25.656] (II) Loading /usr/lib/xorg/modules/libfb.so
[    25.676] (II) Module fb: vendor="X.Org Foundation"
[    25.676] 	compiled for 1.11.3, module version = 1.0.0
[    25.676] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    25.676] (II) Loading sub module "dri2"
[    25.677] (II) LoadModule: "dri2"
[    25.677] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    25.677] (II) Module dri2: vendor="X.Org Foundation"
[    25.677] 	compiled for 1.11.3, module version = 1.2.0
[    25.677] 	ABI class: X.Org Server Extension, version 6.0
[    25.677] (II) UnloadModule: "vesa"
[    25.677] (II) Unloading vesa
[    25.677] (II) UnloadModule: "fbdev"
[    25.677] (II) Unloading fbdev
[    25.677] (II) UnloadModule: "fbdevhw"
[    25.677] (II) Unloading fbdevhw
[    25.677] (==) Depth 24 pixmap format is 32 bpp
[    25.677] (II) intel(0): [DRI2] Setup complete
[    25.677] (II) intel(0): [DRI2]   DRI driver: i965
[    25.677] (II) intel(0): Allocated new frame buffer 1024x768 stride 4096, tiled
[    25.679] (II) UXA(0): Driver registered support for the following operations:
[    25.679] (II)         solid
[    25.679] (II)         copy
[    25.679] (II)         composite (RENDER acceleration)
[    25.679] (II)         put_image
[    25.679] (II)         get_image
[    25.679] (==) intel(0): Backing store disabled
[    25.679] (==) intel(0): Silken mouse enabled
[    25.679] (II) intel(0): Initializing HW Cursor
[    26.307] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    26.356] (==) intel(0): DPMS enabled
[    26.356] (==) intel(0): Intel XvMC decoder enabled
[    26.356] (II) intel(0): Set up textured video
[    26.356] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[    26.356] (II) intel(0): direct rendering: DRI2 Enabled
[    26.356] (WW) intel(0): Option "NoLogo" is not used
[    26.356] (==) intel(0): hotplug detection: "enabled"
[    26.356] (--) RandR disabled
[    26.356] (II) Initializing built-in extension Generic Event Extension
[    26.356] (II) Initializing built-in extension SHAPE
[    26.356] (II) Initializing built-in extension MIT-SHM
[    26.356] (II) Initializing built-in extension XInputExtension
[    26.356] (II) Initializing built-in extension XTEST
[    26.356] (II) Initializing built-in extension BIG-REQUESTS
[    26.356] (II) Initializing built-in extension SYNC
[    26.356] (II) Initializing built-in extension XKEYBOARD
[    26.356] (II) Initializing built-in extension XC-MISC
[    26.356] (II) Initializing built-in extension SECURITY
[    26.356] (II) Initializing built-in extension XINERAMA
[    26.356] (II) Initializing built-in extension XFIXES
[    26.356] (II) Initializing built-in extension RENDER
[    26.356] (II) Initializing built-in extension RANDR
[    26.356] (II) Initializing built-in extension COMPOSITE
[    26.356] (II) Initializing built-in extension DAMAGE
[    26.389] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
[    26.392] (II) intel(0): Setting screen physical size to 270 x 203
[    26.484] (II) XKB: generating xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    26.644] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    26.644] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    26.644] (II) LoadModule: "evdev"
[    26.644] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    26.665] (II) Module evdev: vendor="X.Org Foundation"
[    26.665] 	compiled for 1.11.3, module version = 2.7.0
[    26.665] 	Module class: X.Org XInput Driver
[    26.665] 	ABI class: X.Org XInput driver, version 16.0
[    26.665] (II) Using input driver 'evdev' for 'Power Button'
[    26.665] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    26.665] (**) Power Button: always reports core events
[    26.665] (**) evdev: Power Button: Device: "/dev/input/event2"
[    26.665] (--) evdev: Power Button: Vendor 0 Product 0x1
[    26.665] (--) evdev: Power Button: Found keys
[    26.665] (II) evdev: Power Button: Configuring as keyboard
[    26.665] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    26.665] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    26.665] (**) Option "xkb_rules" "evdev"
[    26.665] (**) Option "xkb_model" "pc105"
[    26.665] (**) Option "xkb_layout" "us"
[    26.665] (**) Option "xkb_variant" "intl"
[    26.666] (II) XKB: generating xkmfile /var/lib/xkb/server-A5431D4A34463C892C9E905E2E421B30A3CC30DD.xkm
[    26.681] (II) config/udev: Adding input device Video Bus (/dev/input/event9)
[    26.681] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    26.681] (II) Using input driver 'evdev' for 'Video Bus'
[    26.681] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    26.681] (**) Video Bus: always reports core events
[    26.681] (**) evdev: Video Bus: Device: "/dev/input/event9"
[    26.681] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    26.681] (--) evdev: Video Bus: Found keys
[    26.681] (II) evdev: Video Bus: Configuring as keyboard
[    26.681] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input9/event9"
[    26.681] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    26.681] (**) Option "xkb_rules" "evdev"
[    26.681] (**) Option "xkb_model" "pc105"
[    26.681] (**) Option "xkb_layout" "us"
[    26.681] (**) Option "xkb_variant" "intl"
[    26.681] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    26.681] (II) No input driver specified, ignoring this device.
[    26.681] (II) This device may have been added with another device file.
[    26.681] (II) config/udev: Adding input device Video Bus (/dev/input/event8)
[    26.681] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    26.682] (II) Using input driver 'evdev' for 'Video Bus'
[    26.682] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    26.682] (**) Video Bus: always reports core events
[    26.682] (**) evdev: Video Bus: Device: "/dev/input/event8"
[    26.682] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    26.682] (--) evdev: Video Bus: Found keys
[    26.682] (II) evdev: Video Bus: Configuring as keyboard
[    26.682] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1a/LNXVIDEO:00/input/input8/event8"
[    26.682] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 8)
[    26.682] (**) Option "xkb_rules" "evdev"
[    26.682] (**) Option "xkb_model" "pc105"
[    26.682] (**) Option "xkb_layout" "us"
[    26.682] (**) Option "xkb_variant" "intl"
[    26.682] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    26.682] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    26.682] (II) Using input driver 'evdev' for 'Power Button'
[    26.682] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    26.682] (**) Power Button: always reports core events
[    26.682] (**) evdev: Power Button: Device: "/dev/input/event1"
[    26.682] (--) evdev: Power Button: Vendor 0 Product 0x1
[    26.682] (--) evdev: Power Button: Found keys
[    26.682] (II) evdev: Power Button: Configuring as keyboard
[    26.682] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[    26.682] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 9)
[    26.682] (**) Option "xkb_rules" "evdev"
[    26.682] (**) Option "xkb_model" "pc105"
[    26.682] (**) Option "xkb_layout" "us"
[    26.682] (**) Option "xkb_variant" "intl"
[    26.682] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event10)
[    26.682] (II) No input driver specified, ignoring this device.
[    26.682] (II) This device may have been added with another device file.
[    26.683] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event11)
[    26.683] (II) No input driver specified, ignoring this device.
[    26.683] (II) This device may have been added with another device file.
[    26.683] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event12)
[    26.683] (II) No input driver specified, ignoring this device.
[    26.683] (II) This device may have been added with another device file.
[    26.683] (II) config/udev: Adding input device Microsoft Microsoft® Nano Transceiver v2.0 (/dev/input/event4)
[    26.683] (**) Microsoft Microsoft® Nano Transceiver v2.0: Applying InputClass "evdev keyboard catchall"
[    26.683] (II) Using input driver 'evdev' for 'Microsoft Microsoft® Nano Transceiver v2.0'
[    26.683] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    26.683] (**) Microsoft Microsoft® Nano Transceiver v2.0: always reports core events
[    26.683] (**) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Device: "/dev/input/event4"
[    26.683] (--) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Vendor 0x45e Product 0x745
[    26.683] (--) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Found keys
[    26.683] (II) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Configuring as keyboard
[    26.683] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.0/input/input4/event4"
[    26.683] (II) XINPUT: Adding extended input device "Microsoft Microsoft® Nano Transceiver v2.0" (type: KEYBOARD, id 10)
[    26.683] (**) Option "xkb_rules" "evdev"
[    26.683] (**) Option "xkb_model" "pc105"
[    26.683] (**) Option "xkb_layout" "us"
[    26.683] (**) Option "xkb_variant" "intl"
[    26.683] (II) config/udev: Adding input device Microsoft Microsoft® Nano Transceiver v2.0 (/dev/input/event5)
[    26.683] (**) Microsoft Microsoft® Nano Transceiver v2.0: Applying InputClass "evdev pointer catchall"
[    26.683] (**) Microsoft Microsoft® Nano Transceiver v2.0: Applying InputClass "evdev keyboard catchall"
[    26.683] (II) Using input driver 'evdev' for 'Microsoft Microsoft® Nano Transceiver v2.0'
[    26.683] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    26.683] (**) Microsoft Microsoft® Nano Transceiver v2.0: always reports core events
[    26.683] (**) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Device: "/dev/input/event5"
[    26.684] (--) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Vendor 0x45e Product 0x745
[    26.684] (--) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Found 9 mouse buttons
[    26.684] (--) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Found scroll wheel(s)
[    26.684] (--) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Found relative axes
[    26.684] (--) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Found x and y relative axes
[    26.684] (--) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Found absolute axes
[    26.684] (II) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Forcing absolute x/y axes to exist.
[    26.684] (--) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Found keys
[    26.684] (II) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Configuring as mouse
[    26.684] (II) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Configuring as keyboard
[    26.684] (II) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Adding scrollwheel support
[    26.684] (**) evdev: Microsoft Microsoft® Nano Transceiver v2.0: YAxisMapping: buttons 4 and 5
[    26.684] (**) evdev: Microsoft Microsoft® Nano Transceiver v2.0: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    26.684] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.1/input/input5/event5"
[    26.684] (II) XINPUT: Adding extended input device "Microsoft Microsoft® Nano Transceiver v2.0" (type: KEYBOARD, id 11)
[    26.684] (**) Option "xkb_rules" "evdev"
[    26.684] (**) Option "xkb_model" "pc105"
[    26.684] (**) Option "xkb_layout" "us"
[    26.684] (**) Option "xkb_variant" "intl"
[    26.684] (II) evdev: Microsoft Microsoft® Nano Transceiver v2.0: initialized for relative axes.
[    26.684] (WW) evdev: Microsoft Microsoft® Nano Transceiver v2.0: ignoring absolute axes.
[    26.684] (**) Microsoft Microsoft® Nano Transceiver v2.0: (accel) keeping acceleration scheme 1
[    26.684] (**) Microsoft Microsoft® Nano Transceiver v2.0: (accel) acceleration profile 0
[    26.684] (**) Microsoft Microsoft® Nano Transceiver v2.0: (accel) acceleration factor: 2.000
[    26.684] (**) Microsoft Microsoft® Nano Transceiver v2.0: (accel) acceleration threshold: 4
[    26.684] (II) config/udev: Adding input device Microsoft Microsoft® Nano Transceiver v2.0 (/dev/input/mouse0)
[    26.684] (II) No input driver specified, ignoring this device.
[    26.684] (II) This device may have been added with another device file.
[    26.684] (II) config/udev: Adding input device Microsoft Microsoft® Nano Transceiver v2.0 (/dev/input/event6)
[    26.684] (**) Microsoft Microsoft® Nano Transceiver v2.0: Applying InputClass "evdev keyboard catchall"
[    26.684] (II) Using input driver 'evdev' for 'Microsoft Microsoft® Nano Transceiver v2.0'
[    26.684] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    26.684] (**) Microsoft Microsoft® Nano Transceiver v2.0: always reports core events
[    26.684] (**) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Device: "/dev/input/event6"
[    26.684] (--) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Vendor 0x45e Product 0x745
[    26.684] (--) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Found 1 mouse buttons
[    26.684] (--) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Found scroll wheel(s)
[    26.684] (--) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Found relative axes
[    26.684] (--) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Found absolute axes
[    26.684] (--) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Found absolute multitouch axes
[    26.684] (--) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Found x and y absolute axes
[    26.685] (--) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Found keys
[    26.685] (II) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Configuring as mouse
[    26.685] (II) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Configuring as keyboard
[    26.685] (II) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Adding scrollwheel support
[    26.685] (**) evdev: Microsoft Microsoft® Nano Transceiver v2.0: YAxisMapping: buttons 4 and 5
[    26.685] (**) evdev: Microsoft Microsoft® Nano Transceiver v2.0: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    26.685] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.2/input/input6/event6"
[    26.685] (II) XINPUT: Adding extended input device "Microsoft Microsoft® Nano Transceiver v2.0" (type: KEYBOARD, id 12)
[    26.685] (**) Option "xkb_rules" "evdev"
[    26.685] (**) Option "xkb_model" "pc105"
[    26.685] (**) Option "xkb_layout" "us"
[    26.685] (**) Option "xkb_variant" "intl"
[    26.685] (II) evdev: Microsoft Microsoft® Nano Transceiver v2.0: initialized for relative axes.
[    26.685] (WW) evdev: Microsoft Microsoft® Nano Transceiver v2.0: ignoring absolute axes.
[    26.685] (**) Microsoft Microsoft® Nano Transceiver v2.0: (accel) keeping acceleration scheme 1
[    26.685] (**) Microsoft Microsoft® Nano Transceiver v2.0: (accel) acceleration profile 0
[    26.685] (**) Microsoft Microsoft® Nano Transceiver v2.0: (accel) acceleration factor: 2.000
[    26.685] (**) Microsoft Microsoft® Nano Transceiver v2.0: (accel) acceleration threshold: 4
[    26.685] (II) config/udev: Adding input device Microsoft Microsoft® Nano Transceiver v2.0 (/dev/input/js0)
[    26.685] (II) No input driver specified, ignoring this device.
[    26.685] (II) This device may have been added with another device file.
[    26.685] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    26.685] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    26.685] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    26.685] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    26.685] (**) AT Translated Set 2 keyboard: always reports core events
[    26.685] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    26.685] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    26.685] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    26.685] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    26.685] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    26.685] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 13)
[    26.685] (**) Option "xkb_rules" "evdev"
[    26.685] (**) Option "xkb_model" "pc105"
[    26.685] (**) Option "xkb_layout" "us"
[    26.685] (**) Option "xkb_variant" "intl"
[    26.686] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/event7)
[    26.686] (**) ETPS/2 Elantech Touchpad: Applying InputClass "evdev touchpad catchall"
[    26.686] (**) ETPS/2 Elantech Touchpad: Applying InputClass "touchpad catchall"
[    26.686] (II) LoadModule: "synaptics"
[    26.686] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    26.698] (II) Module synaptics: vendor="X.Org Foundation"
[    26.698] 	compiled for 1.11.3, module version = 1.6.2
[    26.698] 	Module class: X.Org XInput Driver
[    26.698] 	ABI class: X.Org XInput driver, version 16.0
[    26.698] (II) Using input driver 'synaptics' for 'ETPS/2 Elantech Touchpad'
[    26.698] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    26.698] (**) ETPS/2 Elantech Touchpad: always reports core events
[    26.698] (**) Option "Device" "/dev/input/event7"
[    26.884] (II) synaptics: ETPS/2 Elantech Touchpad: ignoring touch events for semi-multitouch device
[    26.884] (--) synaptics: ETPS/2 Elantech Touchpad: x-axis range 0 - 1088
[    26.884] (--) synaptics: ETPS/2 Elantech Touchpad: y-axis range 0 - 704
[    26.884] (--) synaptics: ETPS/2 Elantech Touchpad: pressure range 0 - 255
[    26.884] (--) synaptics: ETPS/2 Elantech Touchpad: finger width range 0 - 15
[    26.884] (--) synaptics: ETPS/2 Elantech Touchpad: buttons: left right double triple
[    26.884] (--) synaptics: ETPS/2 Elantech Touchpad: Vendor 0x2 Product 0xe
[    26.884] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[    26.884] (**) ETPS/2 Elantech Touchpad: always reports core events
[    26.888] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input7/event7"
[    26.888] (II) XINPUT: Adding extended input device "ETPS/2 Elantech Touchpad" (type: TOUCHPAD, id 14)
[    26.888] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MinSpeed is now constant deceleration 2.5
[    26.888] (**) synaptics: ETPS/2 Elantech Touchpad: MaxSpeed is now 1.75
[    26.888] (**) synaptics: ETPS/2 Elantech Touchpad: AccelFactor is now 0.154
[    26.888] (**) ETPS/2 Elantech Touchpad: (accel) keeping acceleration scheme 1
[    26.888] (**) ETPS/2 Elantech Touchpad: (accel) acceleration profile 1
[    26.888] (**) ETPS/2 Elantech Touchpad: (accel) acceleration factor: 2.000
[    26.888] (**) ETPS/2 Elantech Touchpad: (accel) acceleration threshold: 4
[    26.888] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[    26.888] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/mouse1)
[    26.888] (**) ETPS/2 Elantech Touchpad: Ignoring device from InputClass "touchpad ignore duplicates"
[    30.475] (II) intel(0): EDID vendor "SEC", prod id 13905
[    30.475] (II) intel(0): Printing DDC gathered Modelines:
[    30.475] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1480  768 770 775 780 -hsync -vsync (46.8 kHz)
[    37.651] (II) intel(0): EDID vendor "SEC", prod id 13905
[    37.651] (II) intel(0): Printing DDC gathered Modelines:
[    37.651] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1480  768 770 775 780 -hsync -vsync (46.8 kHz)
[    42.186] (II) intel(0): EDID vendor "SEC", prod id 13905
[    42.186] (II) intel(0): Printing DDC gathered Modelines:
[    42.186] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1480  768 770 775 780 -hsync -vsync (46.8 kHz)
[    42.441] (II) intel(0): Allocated new frame buffer 3328x1200 stride 13312, tiled
[    43.655] (II) intel(0): EDID vendor "SEC", prod id 13905
[    43.655] (II) intel(0): Printing DDC gathered Modelines:
[    43.655] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1480  768 770 775 780 -hsync -vsync (46.8 kHz)
[    44.231] (II) XKB: generating xkmfile /var/lib/xkb/server-66EE0154F48ACA3B8B41E2DABCBEB27CFFFED199.xkm
[    65.735] (II) intel(0): EDID vendor "SEC", prod id 13905
[    65.735] (II) intel(0): Printing DDC gathered Modelines:
[    65.735] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1480  768 770 775 780 -hsync -vsync (46.8 kHz)
[   528.103] (II) XKB: reuse xkmfile /var/lib/xkb/server-66EE0154F48ACA3B8B41E2DABCBEB27CFFFED199.xkm
```

**glxinfo**
```
name of display: :0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Error: couldn't find RGB GLX visual or fbconfig

Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
```

If anyone would be able to help me, it would be much appreciated :)
If you need direct contact for quick replies or debug info, i'll be available on irc #ubuntu rvgate.



Thanks in advance

---

### Post by RvGaTe on 2012-08-04
After some help at IRC (zzippy), we got this working.

If you have the same problem, or trying to get it working with a fresh install, make sure to not enable third party software.

If you did (like me) here's how to fix it:

**Remove xorg config**
```
sudo rm /etc/X11/xorg.conf
```

**Uninstall nvidia drivers**
```
sudo apt-get purge nvidia-current
```

Reboot! unity 3d should work now.

At this point, unity is run using the intel graphics and the build in Geforce GT 540M is consuming power without being used. Installing bumblebee fixes this (turning off the nvidia card).

**Install bumblebee with newer drivers**
```
sudo add-apt-repository ppa:bumblebee/stable
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install bumblebee bumblebee-nvidia
```

Reboot!

Now the nvidia card is disabled, to unleash the power of your nvidia card, run applications/games with optirun.

For example, you can see a clear difference with glxspheres without and with optirun
```
glxspheres
optirun glxspheres
```

And thats it! hope it helps other people in need :)

---

