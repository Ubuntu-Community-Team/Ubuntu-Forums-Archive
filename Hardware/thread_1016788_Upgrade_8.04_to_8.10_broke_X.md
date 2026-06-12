---
title: "Upgrade 8.04 to 8.10 broke X"
date: 2008-12-20
forum: Hardware
---

### Post by pinkunicorn on 2008-12-20
I just upgraded a Compaq Armada M700 laptop from 7.10 to 8.04 without problems, and then proceeded immediately to upgrade to 8.10. The upgrade seemed successful, but after restarting the machine X won't start.

I have tried to run```
dpkg-reconfigure xserver-xorg
```but this doesn't help.

When I try to start X (with startx, since it dumped me to the console), the screen goes black for a short while, then I get lots of output (see Xorg.0.log below), then there's a few seconds pause before the message "giving up" from xinit which closes with```
xinit: Connection refused (errno 111): unable to connect to X server
xinit: No such process (errno 3): Server error.
```

Contents of /var/log/Xorg.0.log:```
X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux piglet 2.6.27-11-generic #1 SMP Fri Dec 19 16:29:52 UTC 2008 i686
Build Date: 24 October 2008  08:00:16AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Dec 20 17:04:16 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
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
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81d9a40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 4.1
	X.Org XInput driver : 2.1
	X.Org Server Extension : 1.1
	X.Org Font Renderer : 0.6
(II) Loader running on linux
(--) using VT number 7

(--) PCI:*(0@1:0:0) ATI Technologies Inc Rage Mobility P/M AGP 2x rev 100, Mem @ 0x40000000/0, 0x41000000/0, I/O @ 0x00003000/0, BIOS @ 0x????????/131072
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
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
	compiled for 7.4.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(**) AIGLX enabled
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
	compiled for 7.4.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
(II) Matched mach64 from file name mach64.ids
(==) Matched mach64 for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "mach64"

(II) Loading /usr/lib/xorg/modules/drivers//mach64_drv.so
(II) Module mach64: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 6.8.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) MACH64: Driver for ATI Mach64 chipsets
(II) Primary Device is: PCI 01@00:00:0
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) MACH64(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(==) MACH64(0): Depth 24, (==) framebuffer bpp 32
(==) MACH64(0): Using XAA acceleration architecture
(II) MACH64: Mach64 in slot 1:0:0 detected.
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 4.1
(II) MACH64(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"

(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.1.0
	ABI class: X.Org Video Driver, version 4.1
(II) MACH64(0): VESA BIOS detected
(II) MACH64(0): VESA VBE Version 2.0
(II) MACH64(0): VESA VBE Total Mem: 8128 kB
(II) MACH64(0): VESA VBE OEM: ATI MACH64
(II) MACH64(0): VESA VBE OEM Software Rev: 1.0
(II) MACH64(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) MACH64(0): VESA VBE OEM Product: MACH64RM
(II) MACH64(0): VESA VBE OEM Product Rev: 01.00
(II) MACH64(0): VESA VBE DDC supported
(II) MACH64(0): VESA VBE DDC Level none
(II) MACH64(0): VESA VBE DDC transfer in appr. 2 sec.
(II) MACH64(0): VESA VBE DDC read failed
(--) MACH64(0): Panel model Samsung LT141X7-122.
(II) MACH64(0): BIOS Data:  BIOSSize=0x10000, ROMTable=0x010C.
(II) MACH64(0): BIOS Data:  ClockTable=0x0A8C, FrequencyTable=0x0000.
(II) MACH64(0): BIOS Data:  LCDTable=0x0180.
(II) MACH64(0): BIOS Data:  VideoTable=0x0000, HardwareTable=0x015C.
(II) MACH64(0): BIOS Data:  I2CType=0x0F, Tuner=0x00, Decoder=0x00, Audio=0x0F.
(--) MACH64(0): ATI 3D Rage Mobility graphics controller detected.
(--) MACH64(0): Chip type 4C4D "LM", version 4, foundry TSMC, class 0, revision 0x01.
(--) MACH64(0): AGP bus interface detected;  block I/O base is 0x3000.
(--) MACH64(0): ATI Mach64 adapter detected.
(!!) MACH64(0): For information on using the multimedia capabilities
	of this adapter, please see http://gatos.sf.net.
(--) MACH64(0): Internal RAMDAC (subtype 1) detected.
(==) MACH64(0): RGB weight 888
(==) MACH64(0): Default visual is TrueColor
(==) MACH64(0): Using gamma correction (1.0, 1.0, 1.0)
(II) MACH64(0): Using Mach64 accelerator CRTC.
(WW) MACH64(0): Logic error setting operating state for VGA I/O.
(--) MACH64(0): 1024x768 panel (ID 11) detected.
(--) MACH64(0): Panel clock is 65.146 MHz.
(II) MACH64(0): Using digital flat panel interface.
(II) MACH64(0): Storing hardware cursor image at 0x407FFC00.
(II) MACH64(0): Using 8 MB linear aperture at 0x40000000.
(!!) MACH64(0): Virtual resolutions will be limited to 8191 kB
 due to linear aperture size and/or placement of hardware cursor image area.
(II) MACH64(0): Using Block 0 MMIO aperture at 0x41000400.
(II) MACH64(0): Using Block 1 MMIO aperture at 0x41000000.
(WW) MACH64(0): Logic error setting operating state for VGA memory aperture.
(II) MACH64(0): MMIO write caching enabled.
(--) MACH64(0): 8192 kB of SDRAM (1:1) detected (using 8191 kB).
(WW) MACH64(0): Cannot shadow an accelerated frame buffer.
(II) MACH64(0): Engine XCLK 124.453 MHz;  Refresh rate code 12.
(--) MACH64(0): Internal programmable clock generator detected.
(--) MACH64(0): Reference clock 29.500 MHz.
(WW) MACH64(0): Unable to estimate virtual size
(II) MACH64(0): Maximum clock: 230.00 MHz
(II) MACH64(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) MACH64(0): Not using default mode "576x432" (exceeds panel dimensions)
(II) MACH64(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) MACH64(0): Not using default mode "640x480" (exceeds panel dimensions)
(II) MACH64(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) MACH64(0): Not using default mode "640x480" (exceeds panel dimensions)
(II) MACH64(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) MACH64(0): Not using default mode "640x512" (exceeds panel dimensions)
(II) MACH64(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) MACH64(0): Not using default mode "640x512" (exceeds panel dimensions)
(II) MACH64(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) MACH64(0): Not using default mode "640x512" (exceeds panel dimensions)
(II) MACH64(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) MACH64(0): Not using default mode "800x600" (exceeds panel dimensions)
(II) MACH64(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) MACH64(0): Not using default mode "800x600" (exceeds panel dimensions)
(II) MACH64(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) MACH64(0): Not using default mode "800x600" (exceeds panel dimensions)
(II) MACH64(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) MACH64(0): Not using default mode "800x600" (exceeds panel dimensions)
(II) MACH64(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) MACH64(0): Not using default mode "800x600" (exceeds panel dimensions)
(II) MACH64(0): Not using default mode "1792x1344" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "896x672" (exceeds panel dimensions)
(II) MACH64(0): Not using default mode "1792x1344" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "896x672" (exceeds panel dimensions)
(II) MACH64(0): Not using default mode "1856x1392" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "928x696" (exceeds panel dimensions)
(II) MACH64(0): Not using default mode "1856x1392" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "928x696" (exceeds panel dimensions)
(II) MACH64(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "960x720" (exceeds panel dimensions)
(II) MACH64(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "960x720" (exceeds panel dimensions)
(II) MACH64(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) MACH64(0): Not using default mode "576x432" (exceeds panel dimensions)
(II) MACH64(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) MACH64(0): Not using default mode "576x432" (exceeds panel dimensions)
(II) MACH64(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) MACH64(0): Not using default mode "576x432" (exceeds panel dimensions)
(II) MACH64(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) MACH64(0): Not using default mode "576x432" (exceeds panel dimensions)
(II) MACH64(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) MACH64(0): Not using default mode "576x432" (exceeds panel dimensions)
(II) MACH64(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) MACH64(0): Not using default mode "576x432" (exceeds panel dimensions)
(II) MACH64(0): Not using default mode "1360x768" (exceeds panel dimensions)
(II) MACH64(0): Not using default mode "1360x768" (exceeds panel dimensions)
(II) MACH64(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) MACH64(0): Not using default mode "700x525" (exceeds panel dimensions)
(II) MACH64(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) MACH64(0): Not using default mode "700x525" (exceeds panel dimensions)
(II) MACH64(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) MACH64(0): Not using default mode "700x525" (exceeds panel dimensions)
(II) MACH64(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) MACH64(0): Not using default mode "700x525" (exceeds panel dimensions)
(II) MACH64(0): Not using default mode "1440x900" (exceeds panel dimensions)
(II) MACH64(0): Not using default mode "720x450" (exceeds panel dimensions)
(II) MACH64(0): Not using default mode "1600x1024" (exceeds panel dimensions)
(II) MACH64(0): Not using default mode "800x512" (exceeds panel dimensions)
(II) MACH64(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) MACH64(0): Not using default mode "840x525" (exceeds panel dimensions)
(II) MACH64(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) MACH64(0): Not using default mode "840x525" (exceeds panel dimensions)
(II) MACH64(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) MACH64(0): Not using default mode "840x525" (exceeds panel dimensions)
(II) MACH64(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) MACH64(0): Not using default mode "840x525" (exceeds panel dimensions)
(II) MACH64(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) MACH64(0): Not using default mode "840x525" (exceeds panel dimensions)
(II) MACH64(0): Not using default mode "1920x1080" (exceeds panel dimensions)
(II) MACH64(0): Not using default mode "960x540" (exceeds panel dimensions)
(II) MACH64(0): Not using default mode "1920x1200" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "960x600" (exceeds panel dimensions)
(II) MACH64(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "960x720" (exceeds panel dimensions)
(II) MACH64(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1024x768" (exceeds panel dimensions)
(II) MACH64(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1024x768" (exceeds panel dimensions)
(II) MACH64(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1024x768" (exceeds panel dimensions)
(--) MACH64(0): Virtual size is 1024x768 (pitch 1024)
(**) MACH64(0): *Default mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
(II) MACH64(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(**) MACH64(0): *Default mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
(II) MACH64(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(**) MACH64(0): *Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(II) MACH64(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(**) MACH64(0): *Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) MACH64(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(**) MACH64(0): *Default mode "1024x768": 44.9 MHz, 35.5 kHz, 86.9 Hz (I)
(II) MACH64(0): Modeline "1024x768"x86.9   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync (35.5 kHz)
(**) MACH64(0): *Built-in mode "Native panel mode": 65.1 MHz, 62.6 kHz, 81.4 Hz
(II) MACH64(0): Modeline "Native panel mode"x81.4   65.15  1024 1024 1032 1040  768 768 769 770 (62.6 kHz)
(**) MACH64(0): *Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(II) MACH64(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(**) MACH64(0): *Default mode "800x600": 56.3 MHz, 53.7 kHz, 85.1 Hz
(II) MACH64(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(**) MACH64(0): *Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) MACH64(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(**) MACH64(0): *Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) MACH64(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(**) MACH64(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) MACH64(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) MACH64(0): *Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) MACH64(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) MACH64(0): *Default mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
(II) MACH64(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(**) MACH64(0): *Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) MACH64(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(**) MACH64(0): *Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) MACH64(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(**) MACH64(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) MACH64(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) MACH64(0): *Default mode "720x400": 35.5 MHz, 37.9 kHz, 85.0 Hz
(II) MACH64(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(**) MACH64(0): *Default mode "680x384": 36.0 MHz, 47.4 kHz, 60.0 Hz (D)
(II) MACH64(0): Modeline "680x384"x60.0   36.00  680 704 720 760  384 385 390 395 doublescan +hsync -vsync (47.4 kHz)
(**) MACH64(0): *Default mode "680x384": 42.4 MHz, 47.7 kHz, 59.8 Hz (D)
(II) MACH64(0): Modeline "680x384"x59.8   42.38  680 716 784 888  384 385 390 399 doublescan -hsync +vsync (47.7 kHz)
(**) MACH64(0): *Default mode "640x400": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) MACH64(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(**) MACH64(0): *Default mode "640x350": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) MACH64(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(**) MACH64(0): *Default mode "512x384": 47.2 MHz, 68.7 kHz, 85.0 Hz (D)
(II) MACH64(0): Modeline "512x384"x85.0   47.25  512 536 584 688  384 384 386 404 doublescan +hsync +vsync (68.7 kHz)
(**) MACH64(0): *Default mode "512x384": 39.4 MHz, 60.0 kHz, 75.0 Hz (D)
(II) MACH64(0): Modeline "512x384"x75.0   39.38  512 520 568 656  384 384 386 400 doublescan +hsync +vsync (60.0 kHz)
(**) MACH64(0): *Default mode "512x384": 37.5 MHz, 56.5 kHz, 70.1 Hz (D)
(II) MACH64(0): Modeline "512x384"x70.1   37.50  512 524 592 664  384 385 388 403 doublescan -hsync -vsync (56.5 kHz)
(**) MACH64(0): *Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
(II) MACH64(0): Modeline "512x384"x60.0   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync (48.4 kHz)
(**) MACH64(0): *Default mode "512x384": 22.4 MHz, 35.5 kHz, 86.6 Hz (D)
(II) MACH64(0): Modeline "512x384"x86.6   22.45  512 516 604 632  384 384 388 409 interlace doublescan +hsync +vsync (35.5 kHz)
(**) MACH64(0): *Default mode "416x312": 28.6 MHz, 49.7 kHz, 74.7 Hz (D)
(II) MACH64(0): Modeline "416x312"x74.7   28.64  416 432 464 576  312 312 314 333 doublescan -hsync -vsync (49.7 kHz)
(**) MACH64(0): *Default mode "400x300": 28.1 MHz, 53.7 kHz, 85.3 Hz (D)
(II) MACH64(0): Modeline "400x300"x85.3   28.15  400 416 448 524  300 300 302 315 doublescan +hsync +vsync (53.7 kHz)
(**) MACH64(0): *Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (D)
(II) MACH64(0): Modeline "400x300"x75.1   24.75  400 408 448 528  300 300 302 312 doublescan +hsync +vsync (46.9 kHz)
(**) MACH64(0): *Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
(II) MACH64(0): Modeline "400x300"x72.2   25.00  400 428 488 520  300 318 321 333 doublescan +hsync +vsync (48.1 kHz)
(**) MACH64(0): *Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) MACH64(0): Modeline "400x300"x60.3   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz)
(**) MACH64(0): *Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(II) MACH64(0): Modeline "400x300"x56.3   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (35.2 kHz)
(**) MACH64(0): *Default mode "320x240": 18.0 MHz, 43.3 kHz, 85.2 Hz (D)
(II) MACH64(0): Modeline "320x240"x85.2   18.00  320 348 376 416  240 240 242 254 doublescan -hsync -vsync (43.3 kHz)
(**) MACH64(0): *Default mode "320x240": 15.8 MHz, 37.5 kHz, 75.0 Hz (D)
(II) MACH64(0): Modeline "320x240"x75.0   15.75  320 328 360 420  240 240 242 250 doublescan -hsync -vsync (37.5 kHz)
(**) MACH64(0): *Default mode "320x240": 15.8 MHz, 37.9 kHz, 72.8 Hz (D)
(II) MACH64(0): Modeline "320x240"x72.8   15.75  320 332 352 416  240 244 246 260 doublescan -hsync -vsync (37.9 kHz)
(**) MACH64(0): *Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) MACH64(0): Modeline "320x240"x60.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz)
(**) MACH64(0): *Default mode "360x200": 17.8 MHz, 37.9 kHz, 85.0 Hz (D)
(II) MACH64(0): Modeline "360x200"x85.0   17.75  360 378 414 468  200 200 202 223 doublescan -hsync +vsync (37.9 kHz)
(**) MACH64(0): *Default mode "320x200": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(II) MACH64(0): Modeline "320x200"x85.3   15.75  320 336 368 416  200 200 202 222 doublescan -hsync +vsync (37.9 kHz)
(**) MACH64(0): *Default mode "320x175": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(II) MACH64(0): Modeline "320x175"x85.3   15.75  320 336 368 416  175 191 192 222 doublescan +hsync -vsync (37.9 kHz)
(==) MACH64(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"

(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"

(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.2.0
	ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) MACH64(0): I2C bus "Mach64" initialized.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) MACH64(0): [drm] SAREA 2200+1208: 3408
(II) MACH64(0): DRIScreenInit for fglrx driver
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed

Backtrace:
0: /usr/bin/X11/X(xf86SigHandler+0x79) [0x80c3009]
1: [0xb7f45400]
2: /usr/lib/xorg/modules/extensions//libdri.so(DRIScreenInit+0xd0) [0xb7a0d2e0]
3: /usr/lib/xorg/modules/drivers//mach64_drv.so(ATIDRIScreenInit+0x2b9) [0xb79e1309]
4: /usr/lib/xorg/modules/drivers//mach64_drv.so(ATIScreenInit+0x1ef) [0xb79dd11f]
5: /usr/bin/X11/X(AddScreen+0x19f) [0x807137f]
6: /usr/bin/X11/X(InitOutput+0x206) [0x80aa536]
7: /usr/bin/X11/X(main+0x279) [0x8071b19]
8: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7b48685]
9: /usr/bin/X11/X [0x8071101]
Saw signal 11.  Server aborting.
```

---

### Post by pinkunicorn on 2008-12-23
After numerous reboots, the machine managed to boot into 800x600 instead of just getting stuck in an infinite number of error dialogs. I can see that the upgrade has created an /etc/X11/xorg.conf that is almost completely empty, but also left a copy of the old one with a dist-upgrade suffix. 

I copied the dist-upgrade version of the file on top of the empty one and restarted, and it still doesn't work, but in a different way. I now get an error dialog reading> Ubuntu is running in low-graphics mode

The following error was encountered. You may need to update your configuration to solve this.

(EE) Failed to load module "type1" (module does not exist, 0)

This configuration file worked fine on 7.10. What do I need to do to replace this module that apparently has changed its name or something like that?

---

### Post by stchman on 2008-12-23
I have never had any luck with the upgrade route.  I recommend a clean install as it is actually quicker.

Also was there anything compelling you to go from Hardy to Intrepid?

---

### Post by pinkunicorn on 2008-12-23
If this is the official version, why isn't there a big fat warning when one tries to upgrade?...

---

### Post by jts0803odon on 2009-01-01
> **pinkunicorn said:**
> After numerous reboots, the machine managed to boot into 800x600 instead of just getting stuck in an infinite number of error dialogs. I can see that the upgrade has created an /etc/X11/xorg.conf that is almost completely empty, but also left a copy of the old one with a dist-upgrade suffix. 

I copied the dist-upgrade version of the file on top of the empty one and restarted, and it still doesn't work, but in a different way. I now get an error dialog reading

This configuration file worked fine on 7.10. What do I need to do to replace this module that apparently has changed its name or something like that?

I had this problem this morning upon upgrading kernels. For some reason the update destroyed my Nvidia driver; try going to System>Admin>Hardware Drivers to make sure your driver is still intact. Reinstalling the recommended (and most recent) driver worked for me; 2.6.27-11 is working with same settings as before.

---

### Post by pinkunicorn on 2009-01-01
> **jts0803odon said:**
> I had this problem this morning upon upgrading kernels. For some reason the update destroyed my Nvidia driver; try going to System>Admin>Hardware Drivers to make sure your driver is still intact. Reinstalling the recommended (and most recent) driver worked for me; 2.6.27-11 is working with same settings as before.

This doesn't seem to be the reason for me. I don't think I was using any proprietary driver, and the machine doesn't list any.

---

