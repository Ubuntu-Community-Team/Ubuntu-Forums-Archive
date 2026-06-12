---
title: "Matrox dual monitor issue"
date: 2010-02-01
forum: Hardware
---

### Post by psyper on 2010-02-01
Hi,
I'm still having problems with my dual monitor setup and people seem to be solving the problem but when I try their steps I seem to still get the problem - I've posted a few confusing posts in the past and get bogged down with the details - I think its probably best if I start from scratch with this issue and resolve it once and for all.  I've had a number of problems with ubuntu and I've solved them all but this one so you have my undivided attention on this one :D


I have a [Matrox G450 dual head card]("http://www.techexcess.net/matrox-millennium-g450-dualhead-32mb-agp-video-graphics-card-g45fmdha32db.aspx").

When I first installed Ubuntu 9.10 on a blank hdd I had no /etc/X11/xorg.conf file so I went through trying to create it from examples of working dual monitor setups on this forum but all have either caused my bootup to fail or doesn't change anything with my issue at all.

Currently I have a decent resolution but my 2nd monitor is showing exactly what is on my 1st monitor.

My current xorg.conf and Xorg.0.log files are below.  Some of my xorg.conf lines have been commented out as when I put them in I'm unable to load up ubuntu.

```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen "Screen1"
#	Screen "Screen2" RightOf "Screen1"
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Typ 1e1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "extmod"
	Load  "record"
	Load  "dri2"
	Load  "glx"
	Load  "dbe"
	Load  "dri"
	Load  "vnc"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	#DisplaySize	  410   260	# mm
	Identifier   "Monitor1"
	VendorName   "NTS"
	ModelName    "M-SERIAL"
EndSection

Section "Monitor"
	#DisplaySize	  410   260	# mm
	Identifier   "Monitor2"
	VendorName   "NTS"
	ModelName    "M-SERIAL"
EndSection

Section "Device"
	Identifier "Matrox Graphics, Inc. MGA G400 AGP 1"
	Driver "mga"
	VendorName  "Matrox Graphics, Inc."
	BoardName   "MGA G400/G450"
	BusID       "PCI:1:0:0"
	Option "OldDmaInit" "True"
	Screen 0
EndSection

Section "Device"
	Identifier "Matrox Graphics, Inc. MGA G400 AGP 2"
	Driver "mga"
	VendorName  "Matrox Graphics, Inc."
	BoardName   "MGA G400/G450"
	BusID       "PCI:1:0:0"
	Option "OldDmaInit" "True"
	Screen 1
EndSection

Section "Screen"
	Identifier "Screen1"
	Device "Matrox Graphics, Inc. MGA G400 AGP 1"
	Monitor "Monitor1"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen2"
	Device "Matrox Graphics, Inc. MGA G400 AGP 2"
	Monitor "Monitor2"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "ServerFlags"
	Option "Xinerama"
EndSection

```

```

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux desktop 2.6.31-17-generic-pae #54-Ubuntu SMP Thu Dec 10 17:23:29 UTC 2009 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-17-generic-pae root=UUID=9cecb44a-7da4-46d2-b421-358a9bcb715e ro quiet splash
Build Date: 14 November 2009  05:48:26PM
xorg-server 2:1.6.4-2ubuntu4.1 (buildd@) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Jan 29 20:44:59 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "X.org Configured"
(**) |-->Screen "Screen1" (0)
(**) |   |-->Monitor "Monitor1"
(**) |   |-->Device "Matrox Graphics, Inc. MGA G400 AGP 1"
(**) |-->Input Device "Mouse0"
(**) |-->Input Device "Keyboard0"
(**) Option "Xinerama"
(==) Automatically adding devices
(==) Automatically enabling devices
(**) Xinerama: enabled
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/Typ 1e1" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins,
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(**) ModulePath set to "/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Mouse0
(WW) Disabling Keyboard0
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0:1:0:0) 102b:0525:102b:0641 Matrox Graphics, Inc. MGA G400/G450 rev 130, Mem @ 0xf4000000/33554432, 0xfe8fc000/16384, 0xfe000000/8388608, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded. This was enabled by default and also specified in the config file.
(II) "dri" will be loaded. This was enabled by default and also specified in the config file.
(II) "dri2" will be loaded. This was enabled by default and also specified in the config file.
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "vnc"
(II) Loading /usr/lib/xorg/modules/extensions//libvnc.so
dlopen: /usr/lib/xorg/modules/extensions//libvnc.so: undefined symbol: NumCurrentSelections
(EE) Failed to load /usr/lib/xorg/modules/extensions//libvnc.so
(II) UnloadModule: "vnc"
(EE) Failed to load module "vnc" (loader failed, 7)
(II) LoadModule: "mga"
(II) Loading /usr/lib/xorg/modules/drivers//mga_drv.so
(II) Module mga: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 1.4.11
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) MGA: driver for Matrox chipsets: mga2064w, mga1064sg, mga2164w,
	mga2164w AGP, mgag100, mgag100 PCI, mgag200, mgag200 PCI,
	mgag200 SE A PCI, mgag200 SE B PCI, mgag200 EV Maxim,
	mgag200 eW Nuvoton, mgag400, mgag550
(II) Primary Device is: PCI 01@00:00:0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
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
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 0.1.0
	ABI class: X.Org Video Driver, version 5.0
(--) MGA(0): Chipset: "mgag400" (G450)
(--) MGA(0): Linear framebuffer at 0xF4000000
(--) MGA(0): MMIO registers at 0xFE8FC000
(--) MGA(0): Pseudo-DMA transfer window at 0xFE000000
(==) MGA(0): Depth 24, (--) framebuffer bpp 32
(==) MGA(0): RGB weight 888
(**) MGA(0): Option "OldDmaInit" "True"
(==) MGA(0): Using AGP 1x mode
(==) MGA(0): Using HW cursor
(==) MGA(0): Using XAA acceleration
(--) MGA(0): Video BIOS info block at offset 0x079C0
(==) MGA(0): VideoRAM: 32768 kByte
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) MGA(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) MGA(0): I2C bus "DDC P1" initialized.
(II) MGA(0): I2C device "DDC P1:E-EDID segment register" registered at address 0x60.
(II) MGA(0): I2C device "DDC P1:ddc2" registered at address 0xA0.
(II) MGA(0): I2C monitor info
(II) MGA(0): Manufacturer: NTS  Model: 1  Serial#: 1
(II) MGA(0): Year: 2007  Week: 5
(II) MGA(0): EDID Version: 1.3
(II) MGA(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) MGA(0): Sync:  Separate
(II) MGA(0): Max Image Size [cm]: horiz.: 41  vert.: 26
(II) MGA(0): Gamma: 2.20
(II) MGA(0): No DPMS capabilities specified; RGB/Color Display
(II) MGA(0): First detailed timing is preferred mode
(II) MGA(0): redX: 0.599 redY: 0.348   greenX: 0.310 greenY: 0.550
(II) MGA(0): blueX: 0.150 blueY: 0.115   whiteX: 0.312 whiteY: 0.328
(II) MGA(0): Supported established timings:
(II) MGA(0): 720x400@70Hz
(II) MGA(0): 640x480@60Hz
(II) MGA(0): 640x480@72Hz
(II) MGA(0): 800x600@56Hz
(II) MGA(0): 800x600@60Hz
(II) MGA(0): 800x600@72Hz
(II) MGA(0): 800x600@75Hz
(II) MGA(0): 1024x768@60Hz
(II) MGA(0): 1024x768@70Hz
(II) MGA(0): 1024x768@75Hz
(II) MGA(0): Manufacturer's mask: 0
(II) MGA(0): Supported detailed timing:
(II) MGA(0): clock: 106.5 MHz   Image Size:  410 x 256 mm
(II) MGA(0): h_active: 1440  h_sync: 1520  h_sync_end 1672 h_blank_end 1904 h_border: 0
(II) MGA(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 934 v_border: 0
(II) MGA(0):  
(II) MGA(0): Monitor name: M-SERIAL
(II) MGA(0): Serial No: 
(II) MGA(0): EDID (in hex):
(II) MGA(0): 	00ffffffffffff003a93010001000000
(II) MGA(0): 	0511010308291a780a47a099594f8c26
(II) MGA(0): 	1d5054abce0001010101010101010101
(II) MGA(0): 	0101010101019a29a0d0518422305098
(II) MGA(0): 	36009a0011000018000000fe000a2020
(II) MGA(0): 	20202020202020202020000000fc004d
(II) MGA(0): 	2d53455249414c0a20202020000000ff
(II) MGA(0): 	000a2020202020202020202020200020
(II) MGA(0): end of monitor info
(II) MGA(0): EDID vendor "NTS", prod id 1
(II) MGA(0): Printing DDC gathered Modelines:
(II) MGA(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync -vsync (55.9 kHz)
(II) MGA(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) MGA(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) MGA(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) MGA(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) MGA(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) MGA(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) MGA(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) MGA(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) MGA(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) MGA(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(==) MGA(0): Using gamma correction (1.0, 1.0, 1.0)
(==) MGA(0): Min pixel clock is 17 MHz
(--) MGA(0): Max pixel clock is 600 MHz
(II) MGA(0): Monitor1: Using hsync range of 31.47-60.02 kHz
(II) MGA(0): Monitor1: Using vrefresh range of 56.25-75.03 Hz
(II) MGA(0): Estimated virtual size for aspect ratio 1.5769 is 1440x900
(II) MGA(0): Clock range:  17.75 to 600.00 MHz
(II) MGA(0): Not using default mode "640x350" (vrefresh out of range)
(II) MGA(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) MGA(0): Not using default mode "640x400" (vrefresh out of range)
(II) MGA(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) MGA(0): Not using default mode "720x400" (vrefresh out of range)
(II) MGA(0): Not using default mode "360x200" (vrefresh out of range)
(II) MGA(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) MGA(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) MGA(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) MGA(0): Not using default mode "640x480" (vrefresh out of range)
(II) MGA(0): Not using default mode "320x240" (vrefresh out of range)
(II) MGA(0): Not using default mode "800x600" (vrefresh out of range)
(II) MGA(0): Not using default mode "400x300" (vrefresh out of range)
(II) MGA(0): Not using default mode "1024x768" (vrefresh out of range)
(II) MGA(0): Not using default mode "512x384" (vrefresh out of range)
(II) MGA(0): Not using default mode "1024x768" (hsync out of range)
(II) MGA(0): Not using default mode "512x384" (hsync out of range)
(II) MGA(0): Not using default mode "1152x864" (hsync out of range)
(II) MGA(0): Not using default mode "576x432" (hsync out of range)
(II) MGA(0): Not using default mode "1280x960" (height too large for virtual size)
(II) MGA(0): Not using default mode "1280x960" (height too large for virtual size)
(II) MGA(0): Not using default mode "640x480" (hsync out of range)
(II) MGA(0): Not using default mode "1280x1024" (height too large for virtual size)
(II) MGA(0): Not using default mode "640x512" (hsync out of range)
(II) MGA(0): Not using default mode "1280x1024" (height too large for virtual size)
(II) MGA(0): Not using default mode "640x512" (hsync out of range)
(II) MGA(0): Not using default mode "1280x1024" (height too large for virtual size)
(II) MGA(0): Not using default mode "640x512" (hsync out of range)
(II) MGA(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) MGA(0): Not using default mode "800x600" (hsync out of range)
(II) MGA(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) MGA(0): Not using default mode "800x600" (hsync out of range)
(II) MGA(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) MGA(0): Not using default mode "800x600" (hsync out of range)
(II) MGA(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) MGA(0): Not using default mode "800x600" (hsync out of range)
(II) MGA(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) MGA(0): Not using default mode "800x600" (hsync out of range)
(II) MGA(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) MGA(0): Not using default mode "896x672" (hsync out of range)
(II) MGA(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) MGA(0): Not using default mode "896x672" (hsync out of range)
(II) MGA(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) MGA(0): Not using default mode "928x696" (hsync out of range)
(II) MGA(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) MGA(0): Not using default mode "928x696" (hsync out of range)
(II) MGA(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) MGA(0): Not using default mode "960x720" (hsync out of range)
(II) MGA(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) MGA(0): Not using default mode "960x720" (hsync out of range)
(II) MGA(0): Not using default mode "1152x864" (hsync out of range)
(II) MGA(0): Not using default mode "576x432" (hsync out of range)
(II) MGA(0): Not using default mode "1152x864" (hsync out of range)
(II) MGA(0): Not using default mode "576x432" (hsync out of range)
(II) MGA(0): Not using default mode "1152x864" (hsync out of range)
(II) MGA(0): Not using default mode "576x432" (hsync out of range)
(II) MGA(0): Not using default mode "1152x864" (hsync out of range)
(II) MGA(0): Not using default mode "576x432" (hsync out of range)
(II) MGA(0): Not using default mode "1152x864" (hsync out of range)
(II) MGA(0): Not using default mode "576x432" (hsync out of range)
(II) MGA(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) MGA(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) MGA(0): Not using default mode "700x525" (hsync out of range)
(II) MGA(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) MGA(0): Not using default mode "700x525" (hsync out of range)
(II) MGA(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) MGA(0): Not using default mode "700x525" (hsync out of range)
(II) MGA(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) MGA(0): Not using default mode "700x525" (hsync out of range)
(II) MGA(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) MGA(0): Not using default mode "800x512" (hsync out of range)
(II) MGA(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) MGA(0): Not using default mode "840x525" (hsync out of range)
(II) MGA(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) MGA(0): Not using default mode "840x525" (hsync out of range)
(II) MGA(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) MGA(0): Not using default mode "840x525" (hsync out of range)
(II) MGA(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) MGA(0): Not using default mode "840x525" (hsync out of range)
(II) MGA(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) MGA(0): Not using default mode "840x525" (hsync out of range)
(II) MGA(0): Not using default mode "1920x1080" (width too large for virtual size)
(II) MGA(0): Not using default mode "960x540" (hsync out of range)
(II) MGA(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) MGA(0): Not using default mode "960x600" (hsync out of range)
(II) MGA(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) MGA(0): Not using default mode "960x720" (hsync out of range)
(II) MGA(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) MGA(0): Not using default mode "1024x768" (hsync out of range)
(II) MGA(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) MGA(0): Not using default mode "1024x768" (hsync out of range)
(II) MGA(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) MGA(0): Not using default mode "1024x768" (hsync out of range)
(--) MGA(0): Has SDRAM
(--) MGA(0): Virtual size is 1440x900 (pitch 1440)
(**) MGA(0): *Driver mode "1440x900": 106.5 MHz, 55.9 kHz, 59.9 Hz
(II) MGA(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync -vsync (55.9 kHz)
(**) MGA(0): *Default mode "1440x900": 106.5 MHz, 55.9 kHz, 59.9 Hz
(II) MGA(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(**) MGA(0): *Default mode "1360x768": 84.8 MHz, 47.7 kHz, 59.8 Hz
(II) MGA(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(**) MGA(0): *Default mode "1152x864": 81.6 MHz, 53.7 kHz, 60.0 Hz
(II) MGA(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(**) MGA(0): *Driver mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
(II) MGA(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(**) MGA(0): *Driver mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(II) MGA(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(**) MGA(0): *Driver mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) MGA(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(**) MGA(0): *Default mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
(II) MGA(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(**) MGA(0): *Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(II) MGA(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(**) MGA(0): *Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) MGA(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(**) MGA(0): *Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(II) MGA(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(**) MGA(0): *Driver mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) MGA(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(**) MGA(0): *Driver mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) MGA(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(**) MGA(0): *Driver mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) MGA(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) MGA(0): *Driver mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) MGA(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) MGA(0): *Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) MGA(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(**) MGA(0): *Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) MGA(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(**) MGA(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) MGA(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) MGA(0): *Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) MGA(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) MGA(0): *Default mode "720x450": 53.2 MHz, 55.9 kHz, 59.9 Hz (D)
(II) MGA(0): Modeline "720x450"x59.9   53.25  720 760 836 952  450 451 454 467 doublescan -hsync +vsync (55.9 kHz)
(**) MGA(0): *Driver mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) MGA(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(**) MGA(0): *Driver mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) MGA(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) MGA(0): *Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) MGA(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(**) MGA(0): *Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) MGA(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(**) MGA(0): *Default mode "640x480": 54.0 MHz, 60.0 kHz, 60.0 Hz (D)
(II) MGA(0): Modeline "640x480"x60.0   54.00  640 688 744 900  480 480 482 500 doublescan +hsync +vsync (60.0 kHz)
(**) MGA(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) MGA(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) MGA(0): *Driver mode "720x400": 28.3 MHz, 31.5 kHz, 70.1 Hz
(II) MGA(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(**) MGA(0): *Default mode "680x384": 36.0 MHz, 47.4 kHz, 60.0 Hz (D)
(II) MGA(0): Modeline "680x384"x60.0   36.00  680 704 720 760  384 385 390 395 doublescan +hsync -vsync (47.4 kHz)
(**) MGA(0): *Default mode "680x384": 42.4 MHz, 47.7 kHz, 59.8 Hz (D)
(II) MGA(0): Modeline "680x384"x59.8   42.38  680 716 784 888  384 385 390 399 doublescan -hsync +vsync (47.7 kHz)
(**) MGA(0): *Default mode "576x432": 40.8 MHz, 53.7 kHz, 60.1 Hz (D)
(II) MGA(0): Modeline "576x432"x60.1   40.81  576 608 668 760  432 432 434 447 doublescan -hsync +vsync (53.7 kHz)
(**) MGA(0): *Default mode "512x384": 39.4 MHz, 60.0 kHz, 75.0 Hz (D)
(II) MGA(0): Modeline "512x384"x75.0   39.38  512 520 568 656  384 384 386 400 doublescan +hsync +vsync (60.0 kHz)
(**) MGA(0): *Default mode "512x384": 37.5 MHz, 56.5 kHz, 70.1 Hz (D)
(II) MGA(0): Modeline "512x384"x70.1   37.50  512 524 592 664  384 385 388 403 doublescan -hsync -vsync (56.5 kHz)
(**) MGA(0): *Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
(II) MGA(0): Modeline "512x384"x60.0   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync (48.4 kHz)
(**) MGA(0): *Default mode "416x312": 28.6 MHz, 49.7 kHz, 74.7 Hz (D)
(II) MGA(0): Modeline "416x312"x74.7   28.64  416 432 464 576  312 312 314 333 doublescan -hsync -vsync (49.7 kHz)
(**) MGA(0): *Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (D)
(II) MGA(0): Modeline "400x300"x75.1   24.75  400 408 448 528  300 300 302 312 doublescan +hsync +vsync (46.9 kHz)
(**) MGA(0): *Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
(II) MGA(0): Modeline "400x300"x72.2   25.00  400 428 488 520  300 318 321 333 doublescan +hsync +vsync (48.1 kHz)
(**) MGA(0): *Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) MGA(0): Modeline "400x300"x60.3   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz)
(**) MGA(0): *Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(II) MGA(0): Modeline "400x300"x56.3   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (35.2 kHz)
(**) MGA(0): Display dimensions: (410, 260) mm
(**) MGA(0): DPI set to (89, 87)
(II) MGA(0): YDstOrg is set to 0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.2.1
	ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
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
(II) MGA(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(--) MGA(0): 16 DWORD fifo
(==) MGA(0): Default visual is TrueColor
(II) MGA(0): [drm] bpp: 32 depth: 24
(II) MGA(0): [drm] Sarea 2200+664: 2864
(WW) MGA(0): Direct rendering is not supported when Xinerama is enabled
(EE) MGA(0): [drm] DRIScreenInit failed.  Disabling DRI.
(II) MGA(0): Using 2012 lines for offscreen memory.
(II) MGA(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	Solid filled trapezoids
	8x8 mono pattern filled rectangles
	8x8 mono pattern filled trapezoids
	Indirect CPU to Screen color expansion
	Screen to Screen color expansion
	Solid Lines
	Dashed Lines
	Scanline Image Writes
	Setting up tile and stipple cache:
		32 128x128 slots
		13 256x256 slots
		5 512x512 slots
(==) MGA(0): Backing store disabled
(==) MGA(0): Silken mouse enabled
(II) MGA(0): DPMS enabled
(II) MGA(0): Using overlay video
(WW) MGA(0): Direct rendering disabled
(==) RandR enabled
(II) Setting vga for screen 0.
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
(II) AIGLX: Screen 0 is not DRI2 capable
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(II) config/hal: Adding input device ImPS/2 Generic Wheel Mouse
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 2.2.5
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) ImPS/2 Generic Wheel Mouse: always reports core events
(**) ImPS/2 Generic Wheel Mouse: Device: "/dev/input/event4"
(II) ImPS/2 Generic Wheel Mouse: Found 3 mouse buttons
(II) ImPS/2 Generic Wheel Mouse: Found x and y relative axes
(II) ImPS/2 Generic Wheel Mouse: Found scroll wheel(s)
(II) ImPS/2 Generic Wheel Mouse: Configuring as mouse
(**) ImPS/2 Generic Wheel Mouse: YAxisMapping: buttons 4 and 5
(**) ImPS/2 Generic Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "ImPS/2 Generic Wheel Mouse" (type: MOUSE)
(**) ImPS/2 Generic Wheel Mouse: (accel) keeping acceleration scheme 1
(**) ImPS/2 Generic Wheel Mouse: (accel) filter chain progression: 2.00
(**) ImPS/2 Generic Wheel Mouse: (accel) filter stage 0: 20.00 ms
(**) ImPS/2 Generic Wheel Mouse: (accel) set acceleration profile 0
(II) ImPS/2 Generic Wheel Mouse: initialized for relative axes.
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "gb"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "gb"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "gb"
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
(II) Macintosh mouse button emulation: initialized for relative axes.
(WW) config/hal: device AT Translated Set 2 keyboard already added. Ignoring.
(WW) config/hal: device Power Button already added. Ignoring.
(WW) config/hal: device Power Button already added. Ignoring.
```

---

### Post by jis on 2010-02-04
Is Xinerama supposed to work still in Ubuntu 9.10? 

Does it help, if you remove # from > #	Screen "Screen2" RightOf "Screen1" in xorg.conf?

Maybe writing the Monitor sections in more detail would help?

Anyway, the log shows that "Direct rendering is not supported when Xinerama is enabled", so video playback will be poor with it. I remember using Xinerama with old ubuntu versions and IIRC direct rendering worked in one head even in xinerama mode.

---

### Post by psyper on 2010-02-16
Many thanks for the reply.

When I remove the comment for the two screens it gets past the Grub screen and then goes blank - there is something flickering on the screen but unreadable.  I have to reboot and use the grub menu to load terminal and restore the backup config.

I've removed the Xinerama lines and I can now view the display properties - before that it would give an error about xand or something like that.  Still getting only one screen detected though on the display properties.  The screen in the properties shows as Unknown with a pink screen.  I'm able to also see my resolution which is as high as I can put it at 1440 x 900 which is what I need for the monitors anyway.

Still only getting one monitor image on both screens though.  What more info do I need to put in xorg?

---

### Post by iainsys on 2011-01-14
I have just installed 10.04 on a PC that used to run Windows. Video card is Matrox G450. I have read lots on the closed G450 thread and come up with the content below for /etc/X11/xorg.conf (The file did not exist before).

The Matrox G450 card is being used as Screen 1, although a copy of Screen 1, is displaced about 70mm right compared with removing the xorg.conf file.

I see that there has been much discussion on this but not everything is resolved.

Can the xorg.conf be fixed or is there a better way of connecting two monitors?


 

# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
# sudo dpkg-reconfigure -phigh xserver-xorg
#
Section "Device"
    Identifier "Matrox Graphics, Inc. MGA G450 AGP Primary"
    Driver "vesa"
    BusID "PCI:1:0:0"
    Option "OldDmaInit" "True"
    Screen 0
EndSection

Section "Device"
    Identifier "Matrox Graphics, Inc. MGA G450 AGP Secondary"
    Driver "vesa"
    BusID "PCI:1:0:0"
    Option "OldDmaInit" "True"
    Screen 1
EndSection

Section "Monitor"
    Identifier "First Monitor"
    Option "DPMS"
EndSection

Section "Monitor"
    Identifier "Second Monitor"
    Option "DPMS"
EndSection

Section "Screen"
    Identifier "First Screen"
    Device "Matrox Graphics, Inc. MGA G450 AGP Primary"
    Monitor "First Monitor"
    DefaultDepth 24
    SubSection "Display"
        Depth 1
        Modes "1152x870" "1024x768" "832x624" "800x600" "640x480
    EndSubSection
    SubSection "Display"
        Depth 4
        Modes "1152x870" "1024x768" "832x624" "800x600" "640x480
    EndSubSection
    SubSection "Display"
        Depth 8
        Modes "1152x870" "1024x768" "832x624" "800x600" "640x480
    EndSubSection
    SubSection "Display"
        Depth 15
        Modes "1152x870" "1024x768" "832x624" "800x600" "640x480
    EndSubSection
    SubSection "Display"
        Depth 16
        Modes "1152x870" "1024x768" "832x624" "800x600" "640x480
    EndSubSection
    SubSection "Display"
        Depth 24
        Modes "1152x870" "1024x768" "832x624" "800x600" "640x480
    EndSubSection
EndSection

Section "Screen"
    Identifier "Second Screen"
    Device "Matrox Graphics, Inc. MGA G450 AGP Secondary"
    Monitor "Second Monitor"
    DefaultDepth 24
    SubSection "Display"
        Depth 1
        Modes "1152x870" "1024x768" "832x624" "800x600" "640x480
    EndSubSection
    SubSection "Display"
        Depth 4
        Modes "1152x870" "1024x768" "832x624" "800x600" "640x480
    EndSubSection
    SubSection "Display"
        Depth 8
        Modes "1152x870" "1024x768" "832x624" "800x600" "640x480
    EndSubSection
    SubSection "Display"
        Depth 15
        Modes "1152x870" "1024x768" "832x624" "800x600" "640x480
    EndSubSection
    SubSection "Display"
        Depth 16
        Modes "1152x870" "1024x768" "832x624" "800x600" "640x480
    EndSubSection
    SubSection "Display"
        Depth 24
        Modes "1152x870" "1024x768" "832x624" "800x600" "640x480
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen    0    "First Screen"
    Screen    1    "Second Screen" RightOf "First Screen"
    Option "Xinerama" "true"
EndSection

Section "DRI"
    Mode 0666
EndSection

---

### Post by jis on 2011-01-15
It is a bug; see here for more info:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-mga/+bug/292214](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-mga/+bug/292214)

---

### Post by iainsys on 2011-01-15
Thanks JIS

My Ubuntu is just 3 days old. I had not thought about a bug, just how I had gone wrong. 

I can see that this is going to be a far longer road than I expected - but thanks for the signpost.

---

