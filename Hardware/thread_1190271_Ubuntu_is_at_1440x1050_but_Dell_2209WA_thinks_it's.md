---
title: "Ubuntu is at 1440x1050 but Dell 2209WA thinks it's at 1680x1050"
date: 2009-06-17
forum: Hardware
---

### Post by pichita on 2009-06-17
Hi,

I just got a Dell 2209WA monitor, and hooked it up to my Sun Ultra 20 Workstation (onboard ATI Rage XL).

The optimal resolution of this monitor is 1680x1050.

Upon reboot, Ubuntu started running at 1440x1050 @60 Hz, and this is the highest resolution I can get at through the 'Screen Resolution' panel (System->Preferences).

However, to my surprise, when I click on the front monitor buttons to access the Monitor's on-screen menu (to set brightness/adjust position/etc.), it shows the current resolution as 1680x1050 ...

xvidtune disagrees with the monitor, and agrees with ubuntu, showing the monitor running at 1440x1050.

After auto-adjusting the viewable screen area, the bottom/top are OK (near the monitor's top/bottom frame), but the left/right borders of the viewable area are far from the monitor's frame ... which is compatible with it using 1440 pixels and leaving ~240 unused pixels. 

I am connecting the monitor using the analog VGA connector.

Any idea what is going on here and how to fix it?

Here's what my Xorg.0.log has to say:
[HTML]
X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux sigma 2.6.27-14-generic #1 SMP Wed Apr 15 18:59:16 UTC 2009 i686
Build Date: 09 March 2009  10:48:54AM
xorg-server 2:1.5.2-2ubuntu3.1 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Jun 17 17:26:10 2009
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
(++) using VT number 7

(--) PCI:*(0@1:5:0) ATI Technologies Inc Rage XL rev 39, Mem @ 0xfb000000/0, 0xfcfff000/0, I/O @ 0x0000ac00/0, BIOS @ 0x????????/131072
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
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
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(==) AIGLX enabled
(==) Exporting typical set of GLX visuals
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
	compiled for 1.5.2, module version = 1.0.0
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
(II) Primary Device is: PCI 01@00:05:0
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) MACH64(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(==) MACH64(0): Depth 24, (==) framebuffer bpp 32
(==) MACH64(0): Using XAA acceleration architecture
(II) MACH64: Mach64 in slot 1:5:0 detected.
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
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
(II) MACH64(0): VESA VBE OEM Product: MACH64GM
(II) MACH64(0): VESA VBE OEM Product Rev: 01.00
(II) MACH64(0): VESA VBE DDC supported
(II) MACH64(0): VESA VBE DDC Level 2
(II) MACH64(0): VESA VBE DDC transfer in appr. 2 sec.
(II) MACH64(0): VESA VBE DDC read successfully
(II) MACH64(0): Manufacturer: DEL  Model: f010  Serial#: 810242636
(II) MACH64(0): Year: 2009  Week: 15
(II) MACH64(0): EDID Version: 1.3
(II) MACH64(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) MACH64(0): Sync:  Separate
(II) MACH64(0): Max Image Size [cm]: horiz.: 47  vert.: 30
(II) MACH64(0): Gamma: 2.20
(II) MACH64(0): DPMS capabilities: Off; RGB/Color Display
(II) MACH64(0): Default color space is primary color space
(II) MACH64(0): First detailed timing is preferred mode
(II) MACH64(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) MACH64(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
(II) MACH64(0): Supported VESA Video Modes:
(II) MACH64(0): 720x400@70Hz
(II) MACH64(0): 640x480@60Hz
(II) MACH64(0): 640x480@75Hz
(II) MACH64(0): 800x600@60Hz
(II) MACH64(0): 800x600@75Hz
(II) MACH64(0): 1024x768@60Hz
(II) MACH64(0): 1024x768@75Hz
(II) MACH64(0): 1280x1024@75Hz
(II) MACH64(0): Manufacturer's mask: 0
(II) MACH64(0): Supported Future Video Modes:
(II) MACH64(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) MACH64(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) MACH64(0): #2: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) MACH64(0): Supported additional Video Mode:
(II) MACH64(0): clock: 146.2 MHz   Image Size:  474 x 296 mm
(II) MACH64(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) MACH64(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) MACH64(0): Serial No: H736H9480KRL
(II) MACH64(0): Monitor name: DELL 2209WA
(II) MACH64(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 160 MHz
(II) MACH64(0): EDID (in hex):
(II) MACH64(0): 	00ffffffffffff0010ac10f04c524b30
(II) MACH64(0): 	0f130103682f1e782eee95a3544c9926
(II) MACH64(0): 	0f5054a54b00714f8180b30001010101
(II) MACH64(0): 	01010101010121399030621a274068b0
(II) MACH64(0): 	3600da281100001c000000ff00483733
(II) MACH64(0): 	3648393438304b524c0a000000fc0044
(II) MACH64(0): 	454c4c203232303957410a20000000fd
(II) MACH64(0): 	00384b1e5310000a2020202020200002
(II) MACH64(0): EDID vendor "DEL", prod id 61456
(II) MACH64(0): Using EDID range info for horizontal sync
(II) MACH64(0): Using EDID range info for vertical refresh
(II) MACH64(0): Printing DDC gathered Modelines:
(II) MACH64(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) MACH64(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) MACH64(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) MACH64(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) MACH64(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) MACH64(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) MACH64(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) MACH64(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) MACH64(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) MACH64(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.7 kHz)
(II) MACH64(0): Modeline "1280x1024"x60.0  108.88  1280 1360 1496 1712  1024 1025 1028 1060 -hsync +vsync (63.6 kHz)
(II) MACH64(0): Modeline "1680x1050"x60.0  147.14  1680 1784 1968 2256  1050 1051 1054 1087 -hsync +vsync (65.2 kHz)
(II) MACH64(0): BIOS Data:  BIOSSize=0x8000, ROMTable=0x0114.
(II) MACH64(0): BIOS Data:  ClockTable=0x097C, FrequencyTable=0x0000.
(II) MACH64(0): BIOS Data:  LCDTable=0x0000.
(II) MACH64(0): BIOS Data:  VideoTable=0x0000, HardwareTable=0x015E.
(II) MACH64(0): BIOS Data:  I2CType=0x0F, Tuner=0x00, Decoder=0x00, Audio=0x0F.
(--) MACH64(0): ATI 3D Rage XL or XC graphics controller detected.
(--) MACH64(0): Chip type 4752 "GR", version 7, foundry TSMC, class 0, revision 0x00.
(--) MACH64(0): PCI bus interface detected;  block I/O base is 0xAC00.
(--) MACH64(0): ATI Mach64 adapter detected.
(!!) MACH64(0): For information on using the multimedia capabilities
	of this adapter, please see http://gatos.sf.net.
(--) MACH64(0): Internal RAMDAC (subtype 1) detected.
(==) MACH64(0): RGB weight 888
(==) MACH64(0): Default visual is TrueColor
(==) MACH64(0): Using gamma correction (1.0, 1.0, 1.0)
(II) MACH64(0): Using Mach64 accelerator CRTC.
(WW) MACH64(0): Logic error setting operating state for VGA I/O.
(II) MACH64(0): Storing hardware cursor image at 0xFB7FFC00.
(II) MACH64(0): Using 8 MB linear aperture at 0xFB000000.
(!!) MACH64(0): Virtual resolutions will be limited to 8191 kB
 due to linear aperture size and/or placement of hardware cursor image area.
(II) MACH64(0): Using Block 0 MMIO aperture at 0xFCFFF400.
(II) MACH64(0): Using Block 1 MMIO aperture at 0xFCFFF000.
(WW) MACH64(0): Logic error setting operating state for VGA memory aperture.
(II) MACH64(0): MMIO write caching enabled.
(--) MACH64(0): 8192 kB of SGRAM (2:1) 32-bit detected (using 8191 kB).
(WW) MACH64(0): Cannot shadow an accelerated frame buffer.
(II) MACH64(0): Engine XCLK 62.353 MHz;  Refresh rate code 1.
(--) MACH64(0): Internal programmable clock generator detected.
(--) MACH64(0): Reference clock 157.5/11 (14.318) MHz.
(II) MACH64(0): Configured Monitor: Using hsync range of 30.00-83.00 kHz
(II) MACH64(0): Configured Monitor: Using vrefresh range of 56.00-75.00 Hz
(II) MACH64(0): Configured Monitor: Using maximum pixel clock of 160.00 MHz
(II) MACH64(0): Estimated virtual size for aspect ratio 1.5667 is 1680x1050
(II) MACH64(0): Maximum clock: 124.00 MHz
(II) MACH64(0): Not using default mode "640x350" (vrefresh out of range)
(II) MACH64(0): Not using default mode "320x175" (vrefresh out of range)
(II) MACH64(0): Not using default mode "640x400" (vrefresh out of range)
(II) MACH64(0): Not using default mode "320x200" (vrefresh out of range)
(II) MACH64(0): Not using default mode "720x400" (vrefresh out of range)
(II) MACH64(0): Not using default mode "360x200" (vrefresh out of range)
(II) MACH64(0): Not using default mode "640x480" (vrefresh out of range)
(II) MACH64(0): Not using default mode "320x240" (vrefresh out of range)
(II) MACH64(0): Not using default mode "800x600" (vrefresh out of range)
(II) MACH64(0): Not using default mode "400x300" (vrefresh out of range)
(II) MACH64(0): Not using default mode "1024x768" (vrefresh out of range)
(II) MACH64(0): Not using default mode "512x384" (vrefresh out of range)
(II) MACH64(0): Not using default mode "1024x768" (vrefresh out of range)
(II) MACH64(0): Not using default mode "512x384" (vrefresh out of range)
(II) MACH64(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) MACH64(0): Not using default mode "640x480" (hsync out of range)
(II) MACH64(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) MACH64(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) MACH64(0): Not using default mode "640x512" (hsync out of range)
(II) MACH64(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) MACH64(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) MACH64(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) MACH64(0): Not using default mode "800x600" (hsync out of range)
(II) MACH64(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) MACH64(0): Not using default mode "800x600" (hsync out of range)
(II) MACH64(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) MACH64(0): Not using default mode "800x600" (hsync out of range)
(II) MACH64(0): Not using default mode "1792x1344" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1792x1344" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) MACH64(0): Not using default mode "1856x1392" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "928x696" (hsync out of range)
(II) MACH64(0): Not using default mode "1856x1392" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) MACH64(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "960x720" (hsync out of range)
(II) MACH64(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) MACH64(0): Not using default mode "1152x864" (vrefresh out of range)
(II) MACH64(0): Not using default mode "576x432" (vrefresh out of range)
(II) MACH64(0): Not using default mode "1152x864" (vrefresh out of range)
(II) MACH64(0): Not using default mode "576x432" (vrefresh out of range)
(II) MACH64(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) MACH64(0): Not using default mode "576x432" (hsync out of range)
(II) MACH64(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) MACH64(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) MACH64(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) MACH64(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) MACH64(0): Not using default mode "700x525" (hsync out of range)
(II) MACH64(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) MACH64(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) MACH64(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) MACH64(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) MACH64(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) MACH64(0): Not using default mode "840x525" (hsync out of range)
(II) MACH64(0): Not using default mode "1920x1080" (width too large for virtual size)
(II) MACH64(0): Not using default mode "1920x1200" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) MACH64(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) MACH64(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) MACH64(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) MACH64(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) MACH64(0): Not using driver mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) MACH64(0): Not using driver mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) MACH64(0): Not using driver mode "1680x1050" (bad mode clock/interlace/doublescan)
(WW) MACH64(0): Shrinking virtual size estimate from 1680x1050 to 1400x1050
(--) MACH64(0): Virtual size is 1400x1050 (pitch 1408)
(**) MACH64(0): *Default mode "1400x1050": 122.0 MHz, 64.9 kHz, 60.0 Hz
(II) MACH64(0): Modeline "1400x1050"x60.0  122.00  1400 1488 1640 1880  1050 1052 1064 1082 +hsync +vsync (64.9 kHz)
(**) MACH64(0): *Driver mode "1280x1024": 108.9 MHz, 63.6 kHz, 60.0 Hz
(II) MACH64(0): Modeline "1280x1024"x60.0  108.88  1280 1360 1496 1712  1024 1025 1028 1060 -hsync +vsync (63.6 kHz)
(**) MACH64(0): *Default mode "1280x1024": 108.0 MHz, 64.0 kHz, 60.0 Hz
(II) MACH64(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(**) MACH64(0): *Default mode "1440x900": 106.5 MHz, 55.9 kHz, 59.9 Hz
(II) MACH64(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(**) MACH64(0): *Default mode "1280x960": 108.0 MHz, 60.0 kHz, 60.0 Hz
(II) MACH64(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(**) MACH64(0): *Default mode "1360x768": 84.8 MHz, 47.7 kHz, 59.8 Hz
(II) MACH64(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(**) MACH64(0): *Driver mode "1152x864": 105.0 MHz, 67.7 kHz, 75.0 Hz
(II) MACH64(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.7 kHz)
(**) MACH64(0): *Default mode "1152x864": 108.0 MHz, 67.5 kHz, 75.0 Hz
(II) MACH64(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(**) MACH64(0): *Default mode "1152x864": 105.0 MHz, 67.6 kHz, 75.0 Hz
(II) MACH64(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.6 kHz)
(**) MACH64(0): *Default mode "1152x864": 96.8 MHz, 63.0 kHz, 70.0 Hz
(II) MACH64(0): Modeline "1152x864"x70.0   96.77  1152 1224 1344 1536  864 865 868 900 -hsync +vsync (63.0 kHz)
(**) MACH64(0): *Default mode "1152x864": 81.6 MHz, 53.7 kHz, 60.0 Hz
(II) MACH64(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(**) MACH64(0): *Driver mode "1024x768": 78.8 MHz, 60.1 kHz, 75.1 Hz
(II) MACH64(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(**) MACH64(0): *Driver mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) MACH64(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(**) MACH64(0): *Default mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
(II) MACH64(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(**) MACH64(0): *Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(II) MACH64(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(**) MACH64(0): *Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) MACH64(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(**) MACH64(0): *Default mode "896x672": 102.4 MHz, 83.7 kHz, 60.0 Hz (D)
(II) MACH64(0): Modeline "896x672"x60.0  102.40  896 960 1060 1224  672 672 674 697 doublescan -hsync +vsync (83.7 kHz)
(**) MACH64(0): *Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(II) MACH64(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(**) MACH64(0): *Driver mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) MACH64(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(**) MACH64(0): *Driver mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) MACH64(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) MACH64(0): *Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) MACH64(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(**) MACH64(0): *Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) MACH64(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(**) MACH64(0): *Default mode "800x600": 87.8 MHz, 81.2 kHz, 65.0 Hz (D)
(II) MACH64(0): Modeline "800x600"x65.0   87.75  800 832 928 1080  600 600 602 625 doublescan +hsync +vsync (81.2 kHz)
(**) MACH64(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) MACH64(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) MACH64(0): *Default mode "800x600": 81.0 MHz, 75.0 kHz, 60.0 Hz (D)
(II) MACH64(0): Modeline "800x600"x60.0   81.00  800 832 928 1080  600 600 602 625 doublescan +hsync +vsync (75.0 kHz)
(**) MACH64(0): *Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) MACH64(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) MACH64(0): *Default mode "840x525": 93.5 MHz, 82.3 kHz, 75.0 Hz (D)
(II) MACH64(0): Modeline "840x525"x75.0   93.50  840 900 988 1136  525 526 529 549 doublescan -hsync +vsync (82.3 kHz)
(**) MACH64(0): *Default mode "840x525": 87.0 MHz, 76.6 kHz, 69.9 Hz (D)
(II) MACH64(0): Modeline "840x525"x69.9   87.00  840 900 988 1136  525 526 529 548 doublescan -hsync +vsync (76.6 kHz)
(**) MACH64(0): *Default mode "840x525": 73.1 MHz, 65.3 kHz, 60.0 Hz (D)
(II) MACH64(0): Modeline "840x525"x60.0   73.12  840 892 980 1120  525 526 529 544 doublescan -hsync +vsync (65.3 kHz)
(**) MACH64(0): *Default mode "700x525": 77.9 MHz, 81.5 kHz, 74.8 Hz (D)
(II) MACH64(0): Modeline "700x525"x74.8   77.90  700 732 892 956  525 526 532 545 doublescan +hsync +vsync (81.5 kHz)
(**) MACH64(0): *Default mode "700x525": 72.5 MHz, 76.5 kHz, 70.1 Hz (D)
(II) MACH64(0): Modeline "700x525"x70.1   72.53  700 748 824 948  525 525 527 546 doublescan -hsync +vsync (76.5 kHz)
(**) MACH64(0): *Default mode "700x525": 61.0 MHz, 64.9 kHz, 60.0 Hz (D)
(II) MACH64(0): Modeline "700x525"x60.0   61.00  700 744 820 940  525 526 532 541 doublescan +hsync +vsync (64.9 kHz)
(**) MACH64(0): *Default mode "640x512": 67.5 MHz, 80.0 kHz, 75.0 Hz (D)
(II) MACH64(0): Modeline "640x512"x75.0   67.50  640 648 720 844  512 512 514 533 doublescan +hsync +vsync (80.0 kHz)
(**) MACH64(0): *Default mode "640x512": 54.0 MHz, 64.0 kHz, 60.0 Hz (D)
(II) MACH64(0): Modeline "640x512"x60.0   54.00  640 664 720 844  512 512 514 533 doublescan +hsync +vsync (64.0 kHz)
(**) MACH64(0): *Default mode "720x450": 53.2 MHz, 55.9 kHz, 59.9 Hz (D)
(II) MACH64(0): Modeline "720x450"x59.9   53.25  720 760 836 952  450 451 454 467 doublescan -hsync +vsync (55.9 kHz)
(**) MACH64(0): *Driver mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) MACH64(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(**) MACH64(0): *Driver mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(II) MACH64(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) MACH64(0): *Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) MACH64(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(**) MACH64(0): *Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) MACH64(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(**) MACH64(0): *Default mode "640x480": 54.0 MHz, 60.0 kHz, 60.0 Hz (D)
(II) MACH64(0): Modeline "640x480"x60.0   54.00  640 688 744 900  480 480 482 500 doublescan +hsync +vsync (60.0 kHz)
(**) MACH64(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) MACH64(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) MACH64(0): *Driver mode "720x400": 28.3 MHz, 31.5 kHz, 70.1 Hz
(II) MACH64(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(**) MACH64(0): *Default mode "680x384": 36.0 MHz, 47.4 kHz, 60.0 Hz (D)
(II) MACH64(0): Modeline "680x384"x60.0   36.00  680 704 720 760  384 385 390 395 doublescan +hsync -vsync (47.4 kHz)
(**) MACH64(0): *Default mode "680x384": 42.4 MHz, 47.7 kHz, 59.8 Hz (D)
(II) MACH64(0): Modeline "680x384"x59.8   42.38  680 716 784 888  384 385 390 399 doublescan -hsync +vsync (47.7 kHz)
(**) MACH64(0): *Default mode "576x432": 54.0 MHz, 67.5 kHz, 75.0 Hz (D)
(II) MACH64(0): Modeline "576x432"x75.0   54.00  576 608 672 800  432 432 434 450 doublescan +hsync +vsync (67.5 kHz)
(**) MACH64(0): *Default mode "576x432": 52.5 MHz, 67.6 kHz, 75.0 Hz (D)
(II) MACH64(0): Modeline "576x432"x75.0   52.49  576 612 676 776  432 432 434 451 doublescan -hsync +vsync (67.6 kHz)
(**) MACH64(0): *Default mode "576x432": 48.4 MHz, 63.0 kHz, 70.0 Hz (D)
(II) MACH64(0): Modeline "576x432"x70.0   48.38  576 612 672 768  432 432 434 450 doublescan -hsync +vsync (63.0 kHz)
(**) MACH64(0): *Default mode "576x432": 40.8 MHz, 53.7 kHz, 60.1 Hz (D)
(II) MACH64(0): Modeline "576x432"x60.1   40.81  576 608 668 760  432 432 434 447 doublescan -hsync +vsync (53.7 kHz)
(**) MACH64(0): *Default mode "512x384": 39.4 MHz, 60.0 kHz, 75.0 Hz (D)
(II) MACH64(0): Modeline "512x384"x75.0   39.38  512 520 568 656  384 384 386 400 doublescan +hsync +vsync (60.0 kHz)
(**) MACH64(0): *Default mode "512x384": 37.5 MHz, 56.5 kHz, 70.1 Hz (D)
(II) MACH64(0): Modeline "512x384"x70.1   37.50  512 524 592 664  384 385 388 403 doublescan -hsync -vsync (56.5 kHz)
(**) MACH64(0): *Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
(II) MACH64(0): Modeline "512x384"x60.0   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync (48.4 kHz)
(**) MACH64(0): *Default mode "416x312": 28.6 MHz, 49.7 kHz, 74.7 Hz (D)
(II) MACH64(0): Modeline "416x312"x74.7   28.64  416 432 464 576  312 312 314 333 doublescan -hsync -vsync (49.7 kHz)
(**) MACH64(0): *Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (D)
(II) MACH64(0): Modeline "400x300"x75.1   24.75  400 408 448 528  300 300 302 312 doublescan +hsync +vsync (46.9 kHz)
(**) MACH64(0): *Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
(II) MACH64(0): Modeline "400x300"x72.2   25.00  400 428 488 520  300 318 321 333 doublescan +hsync +vsync (48.1 kHz)
(**) MACH64(0): *Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) MACH64(0): Modeline "400x300"x60.3   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz)
(**) MACH64(0): *Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(II) MACH64(0): Modeline "400x300"x56.3   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (35.2 kHz)
(**) MACH64(0): *Default mode "320x240": 15.8 MHz, 37.5 kHz, 75.0 Hz (D)
(II) MACH64(0): Modeline "320x240"x75.0   15.75  320 328 360 420  240 240 242 250 doublescan -hsync -vsync (37.5 kHz)
(**) MACH64(0): *Default mode "320x240": 15.8 MHz, 37.9 kHz, 72.8 Hz (D)
(II) MACH64(0): Modeline "320x240"x72.8   15.75  320 332 352 416  240 244 246 260 doublescan -hsync -vsync (37.9 kHz)
(**) MACH64(0): *Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) MACH64(0): Modeline "320x240"x60.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz)
(**) MACH64(0): Display dimensions: (470, 300) mm
(**) MACH64(0): DPI set to (75, 88)
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
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(WW) MACH64(0): DRI static buffer allocation failed -- need at least 14437 kB video memory
(II) MACH64(0): Largest offscreen areas (with overlaps):
(II) MACH64(0): 	8 x 1489 rectangle at 1400,0
(II) MACH64(0): 	1408 x 439 rectangle at 0,1050
(II) MACH64(0): 	384 x 440 rectangle at 0,1050
(II) MACH64(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Setting up tile and stipple cache:
		17 128x128 slots
		4 256x256 slots
(==) MACH64(0): Backing store disabled
(==) MACH64(0): Silken mouse enabled
(II) MACH64(0): DPMS enabled
(II) MACH64(0): Direct rendering disabled
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(II) config/hal: Adding input device Macintosh mouse button emulation
(II) LoadModule: "evdev"

(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 2.0.99
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Configuring as mouse
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device Sun USB Keyboard
(**) Sun USB Keyboard: always reports core events
(**) Sun USB Keyboard: Device: "/dev/input/event2"
(II) Sun USB Keyboard: Found keys
(II) Sun USB Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sun USB Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Sun USB Keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Sun USB Keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "es"
(**) Sun USB Keyboard: xkb_layout: "es"
(**) Option "xkb_options" "lv3:ralt_switch"
(**) Sun USB Keyboard: xkb_options: "lv3:ralt_switch"
(II) config/hal: Adding input device PS/2+USB Mouse
(**) PS/2+USB Mouse: always reports core events
(**) PS/2+USB Mouse: Device: "/dev/input/event1"
(II) PS/2+USB Mouse: Found x and y relative axes
(II) PS/2+USB Mouse: Found 3 mouse buttons
(II) PS/2+USB Mouse: Configuring as mouse
(II) XINPUT: Adding extended input device "PS/2+USB Mouse" (type: MOUSE)
(**) PS/2+USB Mouse: YAxisMapping: buttons 4 and 5
(**) PS/2+USB Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
AUDIT: Wed Jun 17 17:26:17 2009: 5670 X: client 4 rejected from local host ( uid=0 gid=0 pid=5826 )
AUDIT: Wed Jun 17 17:26:42 2009: 5670 X: client 4 rejected from local host ( uid=1001 gid=65534 pid=5861 )
AUDIT: Wed Jun 17 17:26:42 2009: 5670 X: client 4 rejected from local host ( uid=1001 gid=65534 pid=5862 )
AUDIT: Wed Jun 17 17:26:42 2009: 5670 X: client 4 rejected from local host ( uid=1001 gid=65534 pid=5863 )
[/HTML]

---

### Post by pichita on 2009-06-18
BTW, this is on Ubuntu 8.10 (Intrepid), all packages up-to-date.

---

