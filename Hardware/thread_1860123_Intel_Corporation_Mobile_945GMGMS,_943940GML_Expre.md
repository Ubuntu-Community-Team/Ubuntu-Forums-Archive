---
title: "Intel Corporation Mobile 945GM/GMS, 943/940GML Express VGA controller"
date: 2011-10-14
forum: Hardware
---

### Post by sameer.india on 2011-10-14
i just installed 11.10 and found problems with  3D acceleration


```
sameer@The-Flying-Dutchman:~$ lspci -v | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA controller])

```
```
sameer@The-Flying-Dutchman:~$ glxinfo
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
```
sameer@The-Flying-Dutchman:~$ cat /var/log/Xorg.0.log
[    22.845] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[    22.846] X Protocol Version 11, Revision 0
[    22.846] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[    22.846] Current Operating System: Linux The-Flying-Dutchman 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686
[    22.846] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic root=UUID=b9815fa0-c7b8-4b10-a74d-0d69f378bf3b ro i8042.reset i8042.reset quiet splash vt.handoff=7
[    22.846] Build Date: 29 September 2011  12:48:48AM
[    22.846] xorg-server 2:1.10.4-1ubuntu4 (For technical support please see http://www.ubuntu.com/support) 
[    22.846] Current version of pixman: 0.22.2
[    22.846] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    22.846] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    22.846] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Oct 14 22:21:48 2011
[    22.903] (==) Using config file: "/etc/X11/xorg.conf"
[    22.903] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    23.213] (==) No Layout section.  Using the first Screen section.
[    23.214] (==) No screen section available. Using defaults.
[    23.214] (**) |-->Screen "Default Screen Section" (0)
[    23.214] (**) |   |-->Monitor "<default monitor>"
[    23.214] (==) No device specified for screen "Default Screen Section".
	Using the first device section listed.
[    23.214] (**) |   |-->Device "Configured Video Device"
[    23.214] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    23.214] (==) Automatically adding devices
[    23.214] (==) Automatically enabling devices
[    23.290] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    23.290] 	Entry deleted from font path.
[    23.290] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    23.290] 	Entry deleted from font path.
[    23.290] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    23.290] 	Entry deleted from font path.
[    23.305] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    23.305] 	Entry deleted from font path.
[    23.305] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    23.305] 	Entry deleted from font path.
[    23.350] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    23.350] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    23.350] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    23.350] (II) Loader magic: 0x823ada0
[    23.350] (II) Module ABI versions:
[    23.350] 	X.Org ANSI C Emulation: 0.4
[    23.350] 	X.Org Video Driver: 10.0
[    23.350] 	X.Org XInput driver : 12.3
[    23.350] 	X.Org Server Extension : 5.0
[    23.351] (--) PCI:*(0:0:2:0) 8086:27a2:17aa:3801 rev 3, Mem @ 0xd4200000/524288, 0xc0000000/268435456, 0xd4300000/262144, I/O @ 0x00001800/8
[    23.352] (--) PCI: (0:0:2:1) 8086:27a6:17aa:3801 rev 3, Mem @ 0xd4280000/524288
[    23.352] (II) Open ACPI successful (/var/run/acpid.socket)
[    23.352] (II) LoadModule: "extmod"
[    23.441] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    23.457] (II) Module extmod: vendor="X.Org Foundation"
[    23.457] 	compiled for 1.10.4, module version = 1.0.0
[    23.457] 	Module class: X.Org Server Extension
[    23.457] 	ABI class: X.Org Server Extension, version 5.0
[    23.457] (II) Loading extension MIT-SCREEN-SAVER
[    23.457] (II) Loading extension XFree86-VidModeExtension
[    23.457] (II) Loading extension XFree86-DGA
[    23.457] (II) Loading extension DPMS
[    23.457] (II) Loading extension XVideo
[    23.457] (II) Loading extension XVideo-MotionCompensation
[    23.457] (II) Loading extension X-Resource
[    23.457] (II) LoadModule: "dbe"
[    23.458] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    23.463] (II) Module dbe: vendor="X.Org Foundation"
[    23.463] 	compiled for 1.10.4, module version = 1.0.0
[    23.463] 	Module class: X.Org Server Extension
[    23.463] 	ABI class: X.Org Server Extension, version 5.0
[    23.463] (II) Loading extension DOUBLE-BUFFER
[    23.463] (II) LoadModule: "glx"
[    23.463] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/libglx.so
[    26.331] (II) Module glx: vendor="NVIDIA Corporation"
[    26.331] 	compiled for 4.0.2, module version = 1.0.0
[    26.331] 	Module class: X.Org Server Extension
[    26.331] (II) NVIDIA GLX Module  285.05.09  Fri Sep 23 19:13:43 PDT 2011
[    26.331] (II) Loading extension GLX
[    26.331] (II) LoadModule: "record"
[    26.332] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    26.484] (II) Module record: vendor="X.Org Foundation"
[    26.484] 	compiled for 1.10.4, module version = 1.13.0
[    26.484] 	Module class: X.Org Server Extension
[    26.484] 	ABI class: X.Org Server Extension, version 5.0
[    26.484] (II) Loading extension RECORD
[    26.484] (II) LoadModule: "dri"
[    26.485] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    26.516] (II) Module dri: vendor="X.Org Foundation"
[    26.516] 	compiled for 1.10.4, module version = 1.0.0
[    26.516] 	ABI class: X.Org Server Extension, version 5.0
[    26.516] (II) Loading extension XFree86-DRI
[    26.516] (II) LoadModule: "dri2"
[    26.516] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    26.517] (II) Module dri2: vendor="X.Org Foundation"
[    26.517] 	compiled for 1.10.4, module version = 1.2.0
[    26.517] 	ABI class: X.Org Server Extension, version 5.0
[    26.517] (II) Loading extension DRI2
[    26.517] (==) Matched intel as autoconfigured driver 0
[    26.517] (==) Matched vesa as autoconfigured driver 1
[    26.517] (==) Matched fbdev as autoconfigured driver 2
[    26.517] (==) Assigned the driver to the xf86ConfigLayout
[    26.517] (II) LoadModule: "intel"
[    26.518] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    26.665] (II) Module intel: vendor="X.Org Foundation"
[    26.665] 	compiled for 1.10.2.902, module version = 2.15.901
[    26.665] 	Module class: X.Org Video Driver
[    26.665] 	ABI class: X.Org Video Driver, version 10.0
[    26.665] (II) LoadModule: "vesa"
[    26.665] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    26.685] (II) Module vesa: vendor="X.Org Foundation"
[    26.685] 	compiled for 1.10.2, module version = 2.3.0
[    26.685] 	Module class: X.Org Video Driver
[    26.685] 	ABI class: X.Org Video Driver, version 10.0
[    26.685] (II) LoadModule: "fbdev"
[    26.685] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    26.708] (II) Module fbdev: vendor="X.Org Foundation"
[    26.708] 	compiled for 1.10.0, module version = 0.4.2
[    26.708] 	ABI class: X.Org Video Driver, version 10.0
[    26.708] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
	Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
	Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
	Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
	Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server
[    26.708] (II) VESA: driver for VESA chipsets: vesa
[    26.708] (II) FBDEV: driver for framebuffer: fbdev
[    26.708] (++) using VT number 7

[    26.712] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    26.712] (WW) Falling back to old probe method for vesa
[    26.712] (WW) Falling back to old probe method for fbdev
[    26.712] (II) Loading sub module "fbdevhw"
[    26.712] (II) LoadModule: "fbdevhw"
[    26.712] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    26.752] (II) Module fbdevhw: vendor="X.Org Foundation"
[    26.752] 	compiled for 1.10.4, module version = 0.0.2
[    26.752] 	ABI class: X.Org Video Driver, version 10.0
[    26.753] drmOpenDevice: node name is /dev/dri/card0
[    26.753] drmOpenDevice: open result is 12, (OK)
[    26.753] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    26.753] drmOpenDevice: node name is /dev/dri/card0
[    26.753] drmOpenDevice: open result is 12, (OK)
[    26.753] drmOpenByBusid: drmOpenMinor returns 12
[    26.753] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    26.753] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    26.753] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    26.753] (==) intel(0): RGB weight 888
[    26.753] (==) intel(0): Default visual is TrueColor
[    26.753] (**) intel(0): Option "Tiling" "true"
[    26.753] (II) intel(0): Integrated Graphics Chipset: Intel(R) 945GM
[    26.753] (--) intel(0): Chipset: "945GM"
[    26.753] (**) intel(0): Relaxed fencing disabled
[    26.753] (**) intel(0): Wait on SwapBuffers? enabled
[    26.753] (**) intel(0): Triple buffering? enabled
[    26.753] (**) intel(0): Framebuffer tiled
[    26.753] (**) intel(0): Pixmaps tiled
[    26.753] (**) intel(0): 3D buffers tiled
[    26.753] (**) intel(0): SwapBuffers wait enabled
[    26.753] (==) intel(0): video overlay key set to 0x101fe
[    26.753] (II) intel(0): Output LVDS1 has no monitor section
[    26.759] (II) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
[    26.788] (II) intel(0): Output VGA1 has no monitor section
[    27.125] (II) intel(0): Output TV1 has no monitor section
[    27.125] (II) intel(0): EDID for output LVDS1
[    27.125] (II) intel(0): Manufacturer: CPT  Model: 1415  Serial#: 0
[    27.125] (II) intel(0): Year: 2007  Week: 42
[    27.125] (II) intel(0): EDID Version: 1.3
[    27.125] (II) intel(0): Digital Display Input
[    27.125] (II) intel(0): Max Image Size [cm]: horiz.: 33  vert.: 21
[    27.126] (II) intel(0): Gamma: 2.20
[    27.126] (II) intel(0): No DPMS capabilities specified
[    27.126] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    27.126] (II) intel(0): First detailed timing is preferred mode
[    27.126] (II) intel(0): redX: 0.613 redY: 0.336   greenX: 0.311 greenY: 0.563
[    27.126] (II) intel(0): blueX: 0.152 blueY: 0.131   whiteX: 0.315 whiteY: 0.329
[    27.126] (II) intel(0): Manufacturer's mask: 0
[    27.126] (II) intel(0): Supported detailed timing:
[    27.126] (II) intel(0): clock: 68.9 MHz   Image Size:  331 x 207 mm
[    27.126] (II) intel(0): h_active: 1280  h_sync: 1304  h_sync_end 1336 h_blank_end 1408 h_border: 0
[    27.126] (II) intel(0): v_active: 800  v_sync: 801  v_sync_end 804 v_blanking: 813 v_border: 0
[    27.126] (II) intel(0): Unknown vendor-specific block f
[    27.126] (II) intel(0):  CPT
[    27.126] (II) intel(0):  CLAA154WB05A
[    27.126] (II) intel(0): EDID (in hex):
[    27.126] (II) intel(0): 	00ffffffffffff000e14151400000000
[    27.126] (II) intel(0): 	2a110103802115780a092d9d564f9027
[    27.126] (II) intel(0): 	21505400000001010101010101010101
[    27.126] (II) intel(0): 	010101010101ea1a008050200d301820
[    27.126] (II) intel(0): 	13004bcf100000190000000f00202020
[    27.126] (II) intel(0): 	2020202020206e050f00000000fe0043
[    27.126] (II) intel(0): 	50540a202020202020202020000000fe
[    27.126] (II) intel(0): 	00434c414131353457423035412000b9
[    27.126] (II) intel(0): EDID vendor "CPT", prod id 5141
[    27.126] (II) intel(0): Printing DDC gathered Modelines:
[    27.126] (II) intel(0): Modeline "1280x800"x0.0   68.90  1280 1304 1336 1408  800 801 804 813 -hsync -vsync (48.9 kHz)
[    27.126] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    27.126] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    27.126] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    27.126] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    27.126] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    27.126] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    27.126] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    27.126] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    27.126] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    27.126] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    27.126] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    27.126] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    27.126] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    27.126] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    27.126] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    27.126] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    27.126] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    27.126] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    27.126] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    27.126] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    27.126] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    27.126] (II) intel(0): Printing probed modes for output LVDS1
[    27.126] (II) intel(0): Modeline "1280x800"x60.2   68.90  1280 1304 1336 1408  800 801 804 813 -hsync -vsync (48.9 kHz)
[    27.126] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    27.126] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    27.126] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    27.127] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    27.156] (II) intel(0): EDID for output VGA1
[    27.505] (II) intel(0): EDID for output TV1
[    27.505] (II) intel(0): Output LVDS1 connected
[    27.505] (II) intel(0): Output VGA1 disconnected
[    27.505] (II) intel(0): Output TV1 disconnected
[    27.505] (II) intel(0): Using exact sizes for initial modes
[    27.505] (II) intel(0): Output LVDS1 using initial mode 1280x800
[    27.505] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    27.505] (II) intel(0): Kernel page flipping support detected, enabling
[    27.506] (**) intel(0): Display dimensions: (330, 210) mm
[    27.506] (**) intel(0): DPI set to (98, 96)
[    27.506] (II) Loading sub module "fb"
[    27.506] (II) LoadModule: "fb"
[    27.506] (II) Loading /usr/lib/xorg/modules/libfb.so
[    27.529] (II) Module fb: vendor="X.Org Foundation"
[    27.529] 	compiled for 1.10.4, module version = 1.0.0
[    27.529] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    27.529] (II) Loading sub module "dri2"
[    27.529] (II) LoadModule: "dri2"
[    27.530] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    27.530] (II) Module dri2: vendor="X.Org Foundation"
[    27.530] 	compiled for 1.10.4, module version = 1.2.0
[    27.530] 	ABI class: X.Org Server Extension, version 5.0
[    27.530] (II) UnloadModule: "vesa"
[    27.530] (II) Unloading vesa
[    27.530] (II) UnloadModule: "fbdev"
[    27.530] (II) Unloading fbdev
[    27.530] (II) UnloadModule: "fbdevhw"
[    27.530] (II) Unloading fbdevhw
[    27.530] (==) Depth 24 pixmap format is 32 bpp
[    27.530] (II) intel(0): [DRI2] Setup complete
[    27.530] (II) intel(0): [DRI2]   DRI driver: i915
[    27.530] (II) intel(0): Allocated new frame buffer 1280x800 stride 8192, tiled
[    27.553] (II) UXA(0): Driver registered support for the following operations:
[    27.554] (II)         solid
[    27.554] (II)         copy
[    27.554] (II)         composite (RENDER acceleration)
[    27.554] (II)         put_image
[    27.554] (II)         get_image
[    27.554] (==) intel(0): Backing store disabled
[    27.554] (==) intel(0): Silken mouse enabled
[    27.556] (II) intel(0): Initializing HW Cursor
[    27.588] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    27.602] (==) intel(0): DPMS enabled
[    27.602] (==) intel(0): Intel XvMC decoder disabled
[    27.602] (II) intel(0): Set up textured video
[    27.602] (II) intel(0): Set up overlay video
[    27.602] (II) intel(0): direct rendering: DRI2 Enabled
[    27.602] (WW) intel(0): Option "AccelMethod" is not used
[    27.602] (WW) intel(0): Option "EXAOptimizeMigration" is not used
[    27.602] (WW) intel(0): Option "MigrationHeuristic" is not used
[    27.602] (==) intel(0): hotplug detection: "enabled"
[    27.602] (--) RandR disabled
[    27.602] (II) Initializing built-in extension Generic Event Extension
[    27.602] (II) Initializing built-in extension SHAPE
[    27.602] (II) Initializing built-in extension MIT-SHM
[    27.602] (II) Initializing built-in extension XInputExtension
[    27.602] (II) Initializing built-in extension XTEST
[    27.602] (II) Initializing built-in extension BIG-REQUESTS
[    27.602] (II) Initializing built-in extension SYNC
[    27.602] (II) Initializing built-in extension XKEYBOARD
[    27.602] (II) Initializing built-in extension XC-MISC
[    27.603] (II) Initializing built-in extension SECURITY
[    27.603] (II) Initializing built-in extension XINERAMA
[    27.603] (II) Initializing built-in extension XFIXES
[    27.603] (II) Initializing built-in extension RENDER
[    27.603] (II) Initializing built-in extension RANDR
[    27.603] (II) Initializing built-in extension COMPOSITE
[    27.603] (II) Initializing built-in extension DAMAGE
[    27.603] (II) Initializing built-in extension GESTURE
[    27.703] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
[    27.723] (II) intel(0): Setting screen physical size to 338 x 211
[    27.835] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    27.859] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    27.859] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    27.859] (II) LoadModule: "evdev"
[    27.881] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    28.143] (II) Module evdev: vendor="X.Org Foundation"
[    28.143] 	compiled for 1.10.2, module version = 2.6.0
[    28.143] 	Module class: X.Org XInput Driver
[    28.143] 	ABI class: X.Org XInput driver, version 12.3
[    28.143] (II) Using input driver 'evdev' for 'Power Button'
[    28.143] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    28.143] (**) Power Button: always reports core events
[    28.143] (**) Power Button: Device: "/dev/input/event3"
[    28.144] (--) Power Button: Found keys
[    28.144] (II) Power Button: Configuring as keyboard
[    28.144] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    28.144] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    28.144] (**) Option "xkb_rules" "evdev"
[    28.144] (**) Option "xkb_model" "pc105"
[    28.144] (**) Option "xkb_layout" "us"
[    28.145] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    28.145] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    28.145] (II) Using input driver 'evdev' for 'Video Bus'
[    28.145] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    28.145] (**) Video Bus: always reports core events
[    28.145] (**) Video Bus: Device: "/dev/input/event5"
[    28.145] (--) Video Bus: Found keys
[    28.145] (II) Video Bus: Configuring as keyboard
[    28.145] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input5/event5"
[    28.145] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    28.145] (**) Option "xkb_rules" "evdev"
[    28.145] (**) Option "xkb_model" "pc105"
[    28.145] (**) Option "xkb_layout" "us"
[    28.173] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    28.173] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    28.173] (II) Using input driver 'evdev' for 'Power Button'
[    28.173] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    28.173] (**) Power Button: always reports core events
[    28.173] (**) Power Button: Device: "/dev/input/event1"
[    28.173] (--) Power Button: Found keys
[    28.173] (II) Power Button: Configuring as keyboard
[    28.173] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[    28.173] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    28.173] (**) Option "xkb_rules" "evdev"
[    28.173] (**) Option "xkb_model" "pc105"
[    28.174] (**) Option "xkb_layout" "us"
[    28.174] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    28.174] (II) No input driver/identifier specified (ignoring)
[    28.175] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    28.175] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    28.175] (II) Using input driver 'evdev' for 'Sleep Button'
[    28.175] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    28.175] (**) Sleep Button: always reports core events
[    28.175] (**) Sleep Button: Device: "/dev/input/event2"
[    28.175] (--) Sleep Button: Found keys
[    28.175] (II) Sleep Button: Configuring as keyboard
[    28.175] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2/event2"
[    28.175] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    28.175] (**) Option "xkb_rules" "evdev"
[    28.175] (**) Option "xkb_model" "pc105"
[    28.175] (**) Option "xkb_layout" "us"
[    28.178] (II) config/udev: Adding input device HDA Intel Mic (/dev/input/event10)
[    28.178] (II) No input driver/identifier specified (ignoring)
[    28.178] (II) config/udev: Adding input device HDA Intel Headphone (/dev/input/event11)
[    28.178] (II) No input driver/identifier specified (ignoring)
[    28.184] (II) config/udev: Adding input device USB 2.0 Camera (/dev/input/event9)
[    28.184] (**) USB 2.0 Camera: Applying InputClass "evdev keyboard catchall"
[    28.184] (II) Using input driver 'evdev' for 'USB 2.0 Camera'
[    28.184] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    28.184] (**) USB 2.0 Camera: always reports core events
[    28.184] (**) USB 2.0 Camera: Device: "/dev/input/event9"
[    28.184] (--) USB 2.0 Camera: Found keys
[    28.184] (II) USB 2.0 Camera: Configuring as keyboard
[    28.184] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-6/1-6:1.0/input/input9/event9"
[    28.184] (II) XINPUT: Adding extended input device "USB 2.0 Camera" (type: KEYBOARD)
[    28.184] (**) Option "xkb_rules" "evdev"
[    28.184] (**) Option "xkb_model" "pc105"
[    28.184] (**) Option "xkb_layout" "us"
[    28.190] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    28.190] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    28.190] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    28.190] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    28.190] (**) AT Translated Set 2 keyboard: always reports core events
[    28.190] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    28.190] (--) AT Translated Set 2 keyboard: Found keys
[    28.190] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    28.190] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    28.190] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    28.190] (**) Option "xkb_rules" "evdev"
[    28.190] (**) Option "xkb_model" "pc105"
[    28.190] (**) Option "xkb_layout" "us"
[    28.191] (II) config/udev: Adding input device PS/2 Mouse (/dev/input/event6)
[    28.191] (**) PS/2 Mouse: Applying InputClass "evdev pointer catchall"
[    28.191] (II) Using input driver 'evdev' for 'PS/2 Mouse'
[    28.191] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    28.191] (**) PS/2 Mouse: always reports core events
[    28.192] (**) PS/2 Mouse: Device: "/dev/input/event6"
[    28.192] (--) PS/2 Mouse: Found 3 mouse buttons
[    28.192] (--) PS/2 Mouse: Found relative axes
[    28.192] (--) PS/2 Mouse: Found x and y relative axes
[    28.192] (II) PS/2 Mouse: Configuring as mouse
[    28.192] (**) PS/2 Mouse: YAxisMapping: buttons 4 and 5
[    28.192] (**) PS/2 Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    28.192] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio4/input/input6/event6"
[    28.192] (II) XINPUT: Adding extended input device "PS/2 Mouse" (type: MOUSE)
[    28.192] (II) PS/2 Mouse: initialized for relative axes.
[    28.192] (**) PS/2 Mouse: (accel) keeping acceleration scheme 1
[    28.192] (**) PS/2 Mouse: (accel) acceleration profile 0
[    28.192] (**) PS/2 Mouse: (accel) acceleration factor: 2.000
[    28.192] (**) PS/2 Mouse: (accel) acceleration threshold: 4
[    28.192] (II) config/udev: Adding input device PS/2 Mouse (/dev/input/mouse0)
[    28.192] (II) No input driver/identifier specified (ignoring)
[    28.193] (II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/event7)
[    28.193] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "evdev touchpad catchall"
[    28.193] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "touchpad catchall"
[    28.193] (II) LoadModule: "synaptics"
[    28.193] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    28.257] (II) Module synaptics: vendor="X.Org Foundation"
[    28.257] 	compiled for 1.10.4, module version = 1.4.1
[    28.257] 	Module class: X.Org XInput Driver
[    28.257] 	ABI class: X.Org XInput driver, version 12.3
[    28.257] (II) Using input driver 'synaptics' for 'AlpsPS/2 ALPS GlidePoint'
[    28.257] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    28.257] (**) AlpsPS/2 ALPS GlidePoint: always reports core events
[    28.257] (**) Option "Device" "/dev/input/event7"
[    28.268] (--) AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023
[    28.268] (--) AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767
[    28.268] (--) AlpsPS/2 ALPS GlidePoint: pressure range 0 - 127
[    28.268] (--) AlpsPS/2 ALPS GlidePoint: buttons: left right middle
[    28.268] (--) AlpsPS/2 ALPS GlidePoint: invalid finger width range.  defaulting to 0 - 16
[    28.272] (--) AlpsPS/2 ALPS GlidePoint: touchpad found
[    28.272] (**) AlpsPS/2 ALPS GlidePoint: always reports core events
[    28.276] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio4/input/input7/event7"
[    28.276] (II) XINPUT: Adding extended input device "AlpsPS/2 ALPS GlidePoint" (type: TOUCHPAD)
[    28.276] (**) AlpsPS/2 ALPS GlidePoint: (accel) MinSpeed is now constant deceleration 2.5
[    28.276] (**) AlpsPS/2 ALPS GlidePoint: MaxSpeed is now 1.75
[    28.276] (**) AlpsPS/2 ALPS GlidePoint: AccelFactor is now 0.156
[    28.276] (**) AlpsPS/2 ALPS GlidePoint: (accel) keeping acceleration scheme 1
[    28.276] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration profile 1
[    28.276] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration factor: 2.000
[    28.276] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration threshold: 4
[    28.276] (II) AlpsPS/2 ALPS GlidePoint: failed to open grail, no gesture support
[    28.276] (--) AlpsPS/2 ALPS GlidePoint: touchpad found
[    28.277] (II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/mouse1)
[    28.277] (II) No input driver/identifier specified (ignoring)
[    28.277] (II) config/udev: Adding input device Ideapad extra buttons (/dev/input/event8)
[    28.277] (**) Ideapad extra buttons: Applying InputClass "evdev keyboard catchall"
[    28.277] (II) Using input driver 'evdev' for 'Ideapad extra buttons'
[    28.277] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    28.277] (**) Ideapad extra buttons: always reports core events
[    28.277] (**) Ideapad extra buttons: Device: "/dev/input/event8"
[    28.277] (--) Ideapad extra buttons: Found keys
[    28.277] (II) Ideapad extra buttons: Configuring as keyboard
[    28.277] (**) Option "config_info" "udev:/sys/devices/platform/ideapad/input/input8/event8"
[    28.277] (II) XINPUT: Adding extended input device "Ideapad extra buttons" (type: KEYBOARD)
[    28.277] (**) Option "xkb_rules" "evdev"
[    28.277] (**) Option "xkb_model" "pc105"
[    28.277] (**) Option "xkb_layout" "us"
[    37.536] (II) intel(0): EDID vendor "CPT", prod id 5141
[    37.537] (II) intel(0): Printing DDC gathered Modelines:
[    37.537] (II) intel(0): Modeline "1280x800"x0.0   68.90  1280 1304 1336 1408  800 801 804 813 -hsync -vsync (48.9 kHz)
[    41.776] (II) intel(0): EDID vendor "CPT", prod id 5141
[    41.776] (II) intel(0): Printing DDC gathered Modelines:
[    41.776] (II) intel(0): Modeline "1280x800"x0.0   68.90  1280 1304 1336 1408  800 801 804 813 -hsync -vsync (48.9 kHz)
[    43.859] (II) XKB: reuse xkmfile /var/lib/xkb/server-A77BBE312A49C9FE89948D38B2A8CB84C3CBB410.xkm
[    54.724] (II) intel(0): EDID vendor "CPT", prod id 5141
[    54.724] (II) intel(0): Printing DDC gathered Modelines:
[    54.724] (II) intel(0): Modeline "1280x800"x0.0   68.90  1280 1304 1336 1408  800 801 804 813 -hsync -vsync (48.9 kHz)
[    72.796] (II) XKB: reuse xkmfile /var/lib/xkb/server-A77BBE312A49C9FE89948D38B2A8CB84C3CBB410.xkm
[   391.135] (II) intel(0): EDID vendor "CPT", prod id 5141
[   391.135] (II) intel(0): Printing DDC gathered Modelines:
[   391.135] (II) intel(0): Modeline "1280x800"x0.0   68.90  1280 1304 1336 1408  800 801 804 813 -hsync -vsync (48.9 kHz)

```

---

### Post by DomRuf on 2012-01-01
Hello, sameer.india,
I have the same kind of problem and I think, it's being solved in a different thread:
[http://ubuntuforums.org/showthread.php?t=1741783](http://ubuntuforums.org/showthread.php?t=1741783) 
. The last post looked promising. Hope, it helps at least to you, I tried it without a big success, so I keep searching ;).
Good luck

---

