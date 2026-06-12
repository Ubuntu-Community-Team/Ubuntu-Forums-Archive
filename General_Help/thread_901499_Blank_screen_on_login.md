---
title: "Blank screen on login"
date: 2008-08-26
forum: General Help
---

### Post by jpc82 on 2008-08-26
I have a home server setup at my parents house which they use for central storage and other tasks.  I have it setup to auto login and have Vuze setup to auto run on startup.  A few days ago I updated thier system (apt-get update/upgrade) and it seems since then Vuze wasn't starting.  Today I passed by their house and plugged in a monitor and keyboard (normally headless) and booted the system to find it would just stop at a blank desktop.  No menu and no icons.  SSH still works fine and so does samba, but I just can't get X to work.  I looked in the logs as best I could and didn't see anything wrong but I am fairly new to ubuntu.

I have the same setup at home and the updating did not give me any issues at all, so I am not sure what is wrong.  Any help would be great, thanks

---

### Post by ajgreeny on 2008-08-26
Does the machine actually have a GUI installed as the server version does not by default.

---

### Post by kellemes on 2008-08-26
> **jpc82 said:**
> I have a home server setup at my parents house which they use for central storage and other tasks.  I have it setup to auto login and have Vuze setup to auto run on startup.  A few days ago I updated thier system (apt-get update/upgrade) and it seems since then Vuze wasn't starting.  Today I passed by their house and plugged in a monitor and keyboard (normally headless) and booted the system to find it would just stop at a blank desktop.  No menu and no icons.  SSH still works fine and so does samba, but I just can't get X to work.  I looked in the logs as best I could and didn't see anything wrong but I am fairly new to ubuntu.

I have the same setup at home and the updating did not give me any issues at all, so I am not sure what is wrong.  Any help would be great, thanks

Check /var/log/Xorg.0.log since it seems to be X related.

---

### Post by jpc82 on 2008-08-26
Here is my log, I don't see anything wrong with it, just a few warnings.

[PHP]
This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux fileserver 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686
Build Date: 13 June 2008  01:08:21AM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Aug 26 12:35:31 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
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
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(==) |-->Input Device "Configured Mouse"
(==) |-->Input Device "Generic Keyboard"
(==) The core pointer device wasn't specified explicitly in the layout.
	Using the first core pointer device.
(==) The core keyboard device wasn't specified explicitly in the layout.
	Using the first keyboard device.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81dc500
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 2.0
	X.Org XInput driver : 2.0
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1106,0305 card 147b,a401 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,8305 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:07:0: chip 1106,0686 card 147b,0000 rev 22 class 06,01,00 hdr 80
(II) PCI: 00:07:1: chip 1106,0571 card 1106,0571 rev 10 class 01,01,8a hdr 00
(II) PCI: 00:07:2: chip 1106,3038 card 0925,1234 rev 10 class 0c,03,00 hdr 00
(II) PCI: 00:07:3: chip 1106,3038 card 0925,1234 rev 10 class 0c,03,00 hdr 00
(II) PCI: 00:07:4: chip 1106,3057 card 1106,3057 rev 30 class 06,80,00 hdr 00
(II) PCI: 00:0d:0: chip 105a,4d68 card 105a,4d68 rev 02 class 01,80,85 hdr 00
(II) PCI: 00:0f:0: chip 10ec,8139 card 10ec,8139 rev 10 class 02,00,00 hdr 00
(II) PCI: 00:13:0: chip 1103,0004 card 1103,0001 rev 03 class 01,80,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0028 card 1092,4a00 rev 11 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xe6000000 - 0xe7ffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xe4000000 - 0xe5ffffff (0x2000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:7:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation NV5 [RIVA TNT2/TNT2 Pro] rev 17, Mem @ 0xe6000000/24, 0xe4000000/25
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xe0000000 from 0xe3ffffff to 0xdfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xe9004000 - 0xe90040ff (0x100) MX[B]
	[1] -1	0	0xe9000000 - 0xe9003fff (0x4000) MX[B]
	[2] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[3] -1	0	0xe4000000 - 0xe5ffffff (0x2000000) MX[B](B)
	[4] -1	0	0xe6000000 - 0xe6ffffff (0x1000000) MX[B](B)
	[5] -1	0	0x0000c400 - 0x0000c4ff (0x100) IX[B]
	[6] -1	0	0x0000c000 - 0x0000c003 (0x4) IX[B]
	[7] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[8] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[9] -1	0	0x0000b400 - 0x0000b407 (0x8) IX[B]
	[10] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[11] -1	0	0x0000ac00 - 0x0000ac0f (0x10) IX[B]
	[12] -1	0	0x0000a800 - 0x0000a803 (0x4) IX[B]
	[13] -1	0	0x0000a400 - 0x0000a407 (0x8) IX[B]
	[14] -1	0	0x0000a000 - 0x0000a003 (0x4) IX[B]
	[15] -1	0	0x00009c00 - 0x00009c07 (0x8) IX[B]
	[16] -1	0	0x00009800 - 0x0000981f (0x20) IX[B]
	[17] -1	0	0x00009400 - 0x0000941f (0x20) IX[B]
	[18] -1	0	0x00009000 - 0x0000900f (0x10) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xe9004000 - 0xe90040ff (0x100) MX[B]
	[1] -1	0	0xe9000000 - 0xe9003fff (0x4000) MX[B]
	[2] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[3] -1	0	0xe4000000 - 0xe5ffffff (0x2000000) MX[B](B)
	[4] -1	0	0xe6000000 - 0xe6ffffff (0x1000000) MX[B](B)
	[5] -1	0	0x0000c400 - 0x0000c4ff (0x100) IX[B]
	[6] -1	0	0x0000c000 - 0x0000c003 (0x4) IX[B]
	[7] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[8] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[9] -1	0	0x0000b400 - 0x0000b407 (0x8) IX[B]
	[10] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[11] -1	0	0x0000ac00 - 0x0000ac0f (0x10) IX[B]
	[12] -1	0	0x0000a800 - 0x0000a803 (0x4) IX[B]
	[13] -1	0	0x0000a400 - 0x0000a407 (0x8) IX[B]
	[14] -1	0	0x0000a000 - 0x0000a003 (0x4) IX[B]
	[15] -1	0	0x00009c00 - 0x00009c07 (0x8) IX[B]
	[16] -1	0	0x00009800 - 0x0000981f (0x20) IX[B]
	[17] -1	0	0x00009400 - 0x0000941f (0x20) IX[B]
	[18] -1	0	0x00009000 - 0x0000900f (0x10) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe9004000 - 0xe90040ff (0x100) MX[B]
	[5] -1	0	0xe9000000 - 0xe9003fff (0x4000) MX[B]
	[6] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[7] -1	0	0xe4000000 - 0xe5ffffff (0x2000000) MX[B](B)
	[8] -1	0	0xe6000000 - 0xe6ffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[10] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[11] -1	0	0x0000c400 - 0x0000c4ff (0x100) IX[B]
	[12] -1	0	0x0000c000 - 0x0000c003 (0x4) IX[B]
	[13] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[14] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[15] -1	0	0x0000b400 - 0x0000b407 (0x8) IX[B]
	[16] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[17] -1	0	0x0000ac00 - 0x0000ac0f (0x10) IX[B]
	[18] -1	0	0x0000a800 - 0x0000a803 (0x4) IX[B]
	[19] -1	0	0x0000a400 - 0x0000a407 (0x8) IX[B]
	[20] -1	0	0x0000a000 - 0x0000a003 (0x4) IX[B]
	[21] -1	0	0x00009c00 - 0x00009c07 (0x8) IX[B]
	[22] -1	0	0x00009800 - 0x0000981f (0x20) IX[B]
	[23] -1	0	0x00009400 - 0x0000941f (0x20) IX[B]
	[24] -1	0	0x00009000 - 0x0000900f (0x10) IX[B]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
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
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.4.0.90, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) Matched nv from file name nv.ids in autoconfig
(==) Matched nv for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "nv"
(II) Loading /usr/lib/xorg/modules/drivers//nv_drv.so
(II) Module nv: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 2.1.8
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) NV: driver for NVIDIA chipsets: RIVA 128, RIVA TNT, RIVA TNT2,
	Unknown TNT2, Vanta, RIVA TNT2 Ultra, RIVA TNT2 Model 64,
	Aladdin TNT2, GeForce 256, GeForce DDR, Quadro, GeForce2 MX/MX 400,
	GeForce2 MX 100/200, GeForce2 Go, Quadro2 MXR/EX/Go,
	GeForce2 Integrated GPU, GeForce2 GTS, GeForce2 Ti, GeForce2 Ultra,
	Quadro2 Pro, GeForce4 MX 460, GeForce4 MX 440, GeForce4 MX 420,
	GeForce4 MX 440-SE, GeForce4 440 Go, GeForce4 420 Go,
	GeForce4 420 Go 32M, GeForce4 460 Go, Quadro4 550 XGL,
	GeForce4 440 Go 64M, Quadro NVS, Quadro4 500 GoGL,
	GeForce4 410 Go 16M, GeForce4 MX 440 with AGP8X,
	GeForce4 MX 440SE with AGP8X, GeForce4 MX 420 with AGP8X,
	GeForce4 MX 4000, GeForce4 448 Go, GeForce4 488 Go, Quadro4 580 XGL,
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
	Quadro NVS 55/280 PCI, Quadro FX 500/600 PCI,
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
	GeForce 8600 GT, GeForce 8600 GT, GeForce 8400 GS, GeForce 8600M GT,
	GeForce 8700M GT, Quadro FX 370, Quadro NVS 320M, Quadro FX 570M,
	Quadro FX 1600M, Quadro FX 570, Quadro FX 1700, GeForce 8500 GT,
	GeForce 8400 GS, GeForce 8300 GS, GeForce 8400 GS, GeForce 8600M GS,
	GeForce 8400M GT, GeForce 8400M GS, GeForce 8400M G, Quadro NVS 140M,
	Quadro NVS 130M, Quadro NVS 135M, Quadro FX 360M, Quadro NVS 290,
	GeForce 8800 GT, GeForce 8800 GS, GeForce 8800 GS, GeForce 8800 GT,
	Quadro FX 3700, GeForce 9600 GT, GeForce 8400 GS
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset RIVA TNT2 found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe9004000 - 0xe90040ff (0x100) MX[B]
	[5] -1	0	0xe9000000 - 0xe9003fff (0x4000) MX[B]
	[6] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[7] -1	0	0xe4000000 - 0xe5ffffff (0x2000000) MX[B](B)
	[8] -1	0	0xe6000000 - 0xe6ffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[10] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[11] -1	0	0x0000c400 - 0x0000c4ff (0x100) IX[B]
	[12] -1	0	0x0000c000 - 0x0000c003 (0x4) IX[B]
	[13] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[14] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[15] -1	0	0x0000b400 - 0x0000b407 (0x8) IX[B]
	[16] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[17] -1	0	0x0000ac00 - 0x0000ac0f (0x10) IX[B]
	[18] -1	0	0x0000a800 - 0x0000a803 (0x4) IX[B]
	[19] -1	0	0x0000a400 - 0x0000a407 (0x8) IX[B]
	[20] -1	0	0x0000a000 - 0x0000a003 (0x4) IX[B]
	[21] -1	0	0x00009c00 - 0x00009c07 (0x8) IX[B]
	[22] -1	0	0x00009800 - 0x0000981f (0x20) IX[B]
	[23] -1	0	0x00009400 - 0x0000941f (0x20) IX[B]
	[24] -1	0	0x00009000 - 0x0000900f (0x10) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe9004000 - 0xe90040ff (0x100) MX[B]
	[5] -1	0	0xe9000000 - 0xe9003fff (0x4000) MX[B]
	[6] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[7] -1	0	0xe4000000 - 0xe5ffffff (0x2000000) MX[B](B)
	[8] -1	0	0xe6000000 - 0xe6ffffff (0x1000000) MX[B](B)
	[9] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[10] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[11] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x0000c400 - 0x0000c4ff (0x100) IX[B]
	[15] -1	0	0x0000c000 - 0x0000c003 (0x4) IX[B]
	[16] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[17] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[18] -1	0	0x0000b400 - 0x0000b407 (0x8) IX[B]
	[19] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[20] -1	0	0x0000ac00 - 0x0000ac0f (0x10) IX[B]
	[21] -1	0	0x0000a800 - 0x0000a803 (0x4) IX[B]
	[22] -1	0	0x0000a400 - 0x0000a407 (0x8) IX[B]
	[23] -1	0	0x0000a000 - 0x0000a003 (0x4) IX[B]
	[24] -1	0	0x00009c00 - 0x00009c07 (0x8) IX[B]
	[25] -1	0	0x00009800 - 0x0000981f (0x20) IX[B]
	[26] -1	0	0x00009400 - 0x0000941f (0x20) IX[B]
	[27] -1	0	0x00009000 - 0x0000900f (0x10) IX[B]
	[28] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[29] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) NV(0): Initializing int10
(II) NV(0): Primary V_BIOS segment is: 0xc000
(--) NV(0): Chipset: "RIVA TNT2"
(II) NV(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(==) NV(0): Depth 24, (==) framebuffer bpp 32
(==) NV(0): RGB weight 888
(==) NV(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 0.1.0
	ABI class: X.Org Video Driver, version 2.0
(==) NV(0): Using HW cursor
(--) NV(0): Linear framebuffer at 0xE4000000
(--) NV(0): MMIO registers at 0xE6000000
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module "i2c" already built-in
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) NV(0): I2C bus "DDC" initialized.
(II) NV(0): Probing for EDID on I2C bus A...
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(0): I2C device "DDC:ddc2" removed.
(II) NV(0):   ... none found
(--) NV(0): HW is currently programmed for CRT
(II) NV(0): Using CRT on CRTC 0
(--) NV(0): VideoRAM: 32768 kBytes
(==) NV(0): Using gamma correction (1.0, 1.0, 1.0)
(II) NV(0): Configured Monitor: Using default hsync range of 31.50-37.90 kHz
(II) NV(0): Configured Monitor: Using default vrefresh range of 50.00-70.00 Hz
(WW) NV(0): Unable to estimate virtual size
(II) NV(0): Clock range:  12.00 to 350.00 MHz
(II) NV(0): Not using default mode "640x350" (vrefresh out of range)
(II) NV(0): Not using default mode "320x175" (vrefresh out of range)
(II) NV(0): Not using default mode "640x400" (vrefresh out of range)
(II) NV(0): Not using default mode "320x200" (vrefresh out of range)
(II) NV(0): Not using default mode "720x400" (vrefresh out of range)
(II) NV(0): Not using default mode "360x200" (vrefresh out of range)
(II) NV(0): Not using default mode "640x480" (vrefresh out of range)
(II) NV(0): Not using default mode "320x240" (vrefresh out of range)
(II) NV(0): Not using default mode "640x480" (vrefresh out of range)
(II) NV(0): Not using default mode "320x240" (vrefresh out of range)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
(II) NV(0): Not using default mode "320x240" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "400x300" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "400x300" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "400x300" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (vrefresh out of range)
(II) NV(0): Not using default mode "512x384" (vrefresh out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1280x960" (hsync out of range)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
(II) NV(0): Not using default mode "1280x960" (hsync out of range)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
(II) NV(0): Not using default mode "1280x1024" (hsync out of range)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(II) NV(0): Not using default mode "1280x1024" (hsync out of range)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(II) NV(0): Not using default mode "1280x1024" (hsync out of range)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1792x1344" (hsync out of range)
(II) NV(0): Not using default mode "896x672" (hsync out of range)
(II) NV(0): Not using default mode "1792x1344" (hsync out of range)
(II) NV(0): Not using default mode "896x672" (hsync out of range)
(II) NV(0): Not using default mode "1856x1392" (hsync out of range)
(II) NV(0): Not using default mode "928x696" (hsync out of range)
(II) NV(0): Not using default mode "1856x1392" (hsync out of range)
(II) NV(0): Not using default mode "928x696" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (hsync out of range)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (hsync out of range)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "832x624" (hsync out of range)
(II) NV(0): Not using default mode "416x312" (hsync out of range)
(II) NV(0): Not using default mode "1280x768" (hsync out of range)
(II) NV(0): Not using default mode "640x384" (hsync out of range)
(II) NV(0): Not using default mode "1280x800" (hsync out of range)
(II) NV(0): Not using default mode "640x400" (hsync out of range)
(II) NV(0): Not using default mode "1152x768" (hsync out of range)
(II) NV(0): Not using default mode "576x384" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1440x900" (hsync out of range)
(II) NV(0): Not using default mode "720x450" (hsync out of range)
(II) NV(0): Not using default mode "1600x1024" (hsync out of range)
(II) NV(0): Not using default mode "800x512" (hsync out of range)
(II) NV(0): Not using default mode "1680x1050" (hsync out of range)
(II) NV(0): Not using default mode "840x525" (hsync out of range)
(II) NV(0): Not using default mode "1920x1200" (hsync out of range)
(II) NV(0): Not using default mode "960x600" (hsync out of range)
(II) NV(0): Not using default mode "1920x1200" (hsync out of range)
(II) NV(0): Not using default mode "960x600" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (hsync out of range)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (width requires unsupported line pitch)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (width requires unsupported line pitch)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (width requires unsupported line pitch)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(--) NV(0): Virtual size is 800x600 (pitch 800)
(**) NV(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) NV(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) NV(0): *Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) NV(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) NV(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) NV(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) NV(0): *Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) NV(0): Modeline "400x300"x60.3   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz)
(**) NV(0): *Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(II) NV(0): Modeline "400x300"x56.3   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (35.2 kHz)
(**) NV(0): *Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) NV(0): Modeline "320x240"x60.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz)
(==) NV(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.2.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xe4000000 - 0xe5ffffff (0x2000000) MX[B]
	[1] 0	0	0xe6000000 - 0xe6ffffff (0x1000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xe9004000 - 0xe90040ff (0x100) MX[B]
	[7] -1	0	0xe9000000 - 0xe9003fff (0x4000) MX[B]
	[8] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[9] -1	0	0xe4000000 - 0xe5ffffff (0x2000000) MX[B](B)
	[10] -1	0	0xe6000000 - 0xe6ffffff (0x1000000) MX[B](B)
	[11] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[12] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[13] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000c400 - 0x0000c4ff (0x100) IX[B]
	[17] -1	0	0x0000c000 - 0x0000c003 (0x4) IX[B]
	[18] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[19] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[20] -1	0	0x0000b400 - 0x0000b407 (0x8) IX[B]
	[21] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[22] -1	0	0x0000ac00 - 0x0000ac0f (0x10) IX[B]
	[23] -1	0	0x0000a800 - 0x0000a803 (0x4) IX[B]
	[24] -1	0	0x0000a400 - 0x0000a407 (0x8) IX[B]
	[25] -1	0	0x0000a000 - 0x0000a003 (0x4) IX[B]
	[26] -1	0	0x00009c00 - 0x00009c07 (0x8) IX[B]
	[27] -1	0	0x00009800 - 0x0000981f (0x20) IX[B]
	[28] -1	0	0x00009400 - 0x0000941f (0x20) IX[B]
	[29] -1	0	0x00009000 - 0x0000900f (0x10) IX[B]
	[30] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[31] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(==) NV(0): Write-combining range (0xe4000000,0x2000000)
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
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) AIGLX: Screen 0 is not DRI capable
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
[/PHP]

---

### Post by jpc82 on 2008-08-27
bump, hoping someone has any ideas on why this is happening.

---

### Post by kellemes on 2008-08-27
> **jpc82 said:**
> bump, hoping someone has any ideas on why this is happening.

I wonder.. as I understand it you don't use the server edition of Ubuntu?
You use the standard desktop edition instead? So the Gnome desktop should popup?

---

### Post by jpc82 on 2008-08-27
Yes I am using the standard ubuntu for this server.  Gnome used to come up normally and I had it to auto login for my main user, so it would go right to thier desktop.  The issue is right now when I try to boot, X seems to load and the screen shows the blank brown backgroud ubuntu had, and a mouse pointer.  But other then that nothing comes up no matter how long I wait.

---

### Post by kellemes on 2008-08-27
Well, the thing that you can try is reconfigure X like so..
From safe mode/recovery mode..
```
sudo dpkg --configure -a
```

If that doesn't work you can reinstall ubuntu-desktop like so..
```
sudo apt-get remove ubuntu-desktop
sudo apt-get install ubuntu-desktop
sudo dpkg --configure -a
```

Hope it helps..

By the way, cannot promise any good outcome, so don't bite my head of if things go wrong ;-)

---

### Post by jpc82 on 2008-08-27
I will try that out when I get a chance.

Do you or anyone else know where ubuntu actually stores the auto log in information?  I am thinking maybe that is the issue, account could have got curropt in some way.  So I want to turn that off for now and see what that does.  But I don't know how to do it though ssh and the command line.

---

### Post by mssever on 2008-08-27
> **jpc82 said:**
> I will try that out when I get a chance.

Do you or anyone else know where ubuntu actually stores the auto log in information?  I am thinking maybe that is the issue, account could have got curropt in some way.  So I want to turn that off for now and see what that does.  But I don't know how to do it though ssh and the command line.
SSH in with the ForwardX11 option enabled, then run gksudo gdmsetup and the window will appear on your screen (assuming you're running X).

Also, try this: Log onto the machine using the failsafe terminal session. Since you can get the wallpaper, you should be able to get this far. Then, in the terminal that comes up, type ```
gnome-session >stdout.log 2>stderr.log
```Hopefully you'll get some useful error messages that will give you a hint about what's wrong.

---

### Post by jpc82 on 2008-08-27
Hi, thanks for the idea's.  I am currently at home so I have no way of doing some of the tests you suggested since the computer is at my parents.  However what I have tried is installing tightvncserver and running it.  I then connected to it and ran gnome-session from there.

When I did that everything seemed to work perfectly.  Gnome loaded up Vuze started and everything went normally.  Does that fact that it can do this mean anything?  I'm guessing profile should be ok and gnome should be installed ok.

---

### Post by mssever on 2008-08-27
> **jpc82 said:**
> Does that fact that it can do this mean anything?
I don't know.

---

