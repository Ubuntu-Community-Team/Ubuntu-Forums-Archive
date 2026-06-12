---
title: "Changing the max screen resolution (width too large for virtual size)"
date: 2010-01-26
forum: Hardware
---

### Post by lereveur on 2010-01-26
Ok. I've re-installed Ubuntu Karmic Koala from scratch.

I have a Gateway EV700 monitor. It supports up to 1280x1024 at 60MHz. Yet Display Preferences wants to call it an "unknown" monitor. The maximum display resolution for an unknown monitor is apparently 1024x768. I've found the correct Modeline for the desired resolution. I've added the xrandr newmode and addmode lines to the GDM PreSession Default. This correctly adds the new resolution to the Display Preferences. However, when I try to apply the 1280x1024 resolution, I get the following error message:

```
**The selected configuration for displays could not be applied**
could not set the configuration for CRTC 273.
```

Here is my Xorg.0.log file:

```
X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux monreveur-desktop 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-17-generic root=UUID=0957c3b4-22a2-4a0e-ab42-1be3113d06ae ro quiet splash
Build Date: 14 November 2009  05:48:26PM
xorg-server 2:1.6.4-2ubuntu4.1 (buildd@) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Jan 26 16:50:38 2010
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0:1:0:0) 1039:6330:105b:0c92 Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter rev 0, Mem @ 0xe0000000/134217728, 0xe8000000/131072, I/O @ 0x0000d000/128
(==) Using default built-in configuration (30 lines)
(==) --- Start of built-in configuration ---
	Section "Device"
		Identifier	"Builtin Default sis Device 0"
		Driver	"sis"
	EndSection
	Section "Screen"
		Identifier	"Builtin Default sis Screen 0"
		Device	"Builtin Default sis Device 0"
	EndSection
	Section "Device"
		Identifier	"Builtin Default vesa Device 0"
		Driver	"vesa"
	EndSection
	Section "Screen"
		Identifier	"Builtin Default vesa Screen 0"
		Device	"Builtin Default vesa Device 0"
	EndSection
	Section "Device"
		Identifier	"Builtin Default fbdev Device 0"
		Driver	"fbdev"
	EndSection
	Section "Screen"
		Identifier	"Builtin Default fbdev Screen 0"
		Device	"Builtin Default fbdev Device 0"
	EndSection
	Section "ServerLayout"
		Identifier	"Builtin Default Layout"
		Screen	"Builtin Default sis Screen 0"
		Screen	"Builtin Default vesa Screen 0"
		Screen	"Builtin Default fbdev Screen 0"
	EndSection
(==) --- End of built-in configuration ---
(==) ServerLayout "Builtin Default Layout"
(**) |-->Screen "Builtin Default sis Screen 0" (0)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default sis Device 0"
(==) No monitor specified for screen "Builtin Default sis Screen 0".
	Using a default monitor configuration.
(**) |-->Screen "Builtin Default vesa Screen 0" (1)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default vesa Device 0"
(==) No monitor specified for screen "Builtin Default vesa Screen 0".
	Using a default monitor configuration.
(**) |-->Screen "Builtin Default fbdev Screen 0" (2)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default fbdev Device 0"
(==) No monitor specified for screen "Builtin Default fbdev Screen 0".
	Using a default monitor configuration.
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Open ACPI successful (/var/run/acpid.socket)
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
	[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[24] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[25] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[26] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[27] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[28] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[29] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
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
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "sis"
(II) Loading /usr/lib/xorg/modules/drivers//sis_drv.so
(II) Module sis: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 0.10.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 2.2.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers//fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 0.4.0
	ABI class: X.Org Video Driver, version 5.0
(II) SIS: driver for SiS chipsets: SIS5597/5598, SIS530/620,
	SIS6326/AGP/DVD, SIS300/305, SIS630/730, SIS540, SIS315, SIS315H,
	SIS315PRO/E, SIS550, SIS650/M650/651/740, SIS330(Xabre),
	SIS660/[M]661[F|M]X/[M]670/[M]741[GX]/[M]760[GX]/[M]761[GX]/[M]770[GX],
	SIS340
(II) SIS: driver for XGI chipsets: Volari Z7 (XG20),
	Volari V3XT/V5/V8/Duo (XG40)
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 01@00:00:0
(WW) Falling back to old probe method for sis
(--) Assigning device section with no busID to primary device
(--) Chipset SIS660/[M]661[F|M]X/[M]670/[M]741[GX]/[M]760[GX]/[M]761[GX]/[M]770[GX] found
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
	[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[24] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[25] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[26] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[27] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[28] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[29] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux//libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 0.0.2
	ABI class: X.Org Video Driver, version 5.0
(EE) open /dev/fb0: No such file or directory
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
	[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[20] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[21] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[22] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[23] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[24] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[25] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[26] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[27] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[28] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[29] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[30] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[31] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[32] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[33] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[34] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) SIS(0): SiS driver (2005/09/20-1, compiled for X.org 1.6.0.0)
(II) SIS(0): Copyright (C) 2001-2005 Thomas Winischhofer <thomas@winischhofer.net> and others
(II) SIS(0): *** See http://www.winischhofer.at/linuxsisvga.shtml
(II) SIS(0): *** for documentation and updates.
(--) SIS(0): sisfb not found
(--) SIS(0): Relocated I/O registers at 0xD000
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) SIS(0): Creating default Display subsection in Screen section
	"Builtin Default sis Screen 0" for depth/fbbpp 24/32
(==) SIS(0): Depth 24, (--) framebuffer bpp 32
(==) SIS(0): RGB weight 888
(==) SIS(0): Default visual is TrueColor
(WW) SIS(0): Could not find/read video BIOS
(==) SIS(0): Using XAA acceleration architecture
(==) SIS(0): Using HW cursor
(==) SIS(0): Color HW cursor is enabled
(II) SIS(0): Using VRAM command queue, size 512k
(==) SIS(0): Hotkey display switching is enabled
(II) SIS(0): WARNING: Using the Hotkey might freeze your machine, regardless
(II) SIS(0):          whether enabled or disabled. This is no driver bug.
(==) SIS(0): SiSCtrl utility interface is disabled
(II) SIS(0): For information on SiSCtrl, see
		http://www.winischhofer.at/linuxsispart1.shtml#sisctrl
(==) SIS(0): DRI disabled
(II) SIS(0): Checking OS for SSE support is not supported in this version of X.org
(II) SIS(0): If your OS supports SSE, set the option "UseSSE" to "on".
(--) SIS(0): 131072K shared video RAM (UMA)
(--) SIS(0): DRAM type: DDR SDRAM
(--) SIS(0): Memory clock: 166.446 MHz
(--) SIS(0): DRAM bus width: 64 bit
(--) SIS(0): Linear framebuffer at 0xE0000000
(--) SIS(0): MMIO registers at 0xE8000000 (size 64K)
(--) SIS(0): VideoRAM: 131072 KB
(II) SIS(0): Using 130496K of framebuffer memory at offset 0K
(--) SIS(0): Hardware supports two video overlays
(II) SIS(0): 
	Dear SiS76x user, your machine is using a shared memory framebuffer.
	Due to hardware limitations of the SiS chip in combination with the
	AMD CPU, video overlay support is very limited on this machine. If you
	experience flashing lines in the video and/or the graphics display
	during video playback, reduce the color depth and/or the resolution
	and/or the refresh rate. Alternatively, use the video blitter.
(==) SIS(0): Using gamma correction (1.0, 1.0, 1.0)
(II) SIS(0): Gamma correction is enabled
(II) SIS(0): Separate Xv gamma correction is disabled
(--) SIS(0): Memory bandwidth at 32 bpp is 332.892 MHz
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(--) SIS(0): CRT1 DDC supported
(--) SIS(0): CRT1 DDC level: 2 
(--) SIS(0): CRT1 DDC monitor info: *******************************************
(II) SIS(0): Manufacturer: GWY  Model: 1b62  Serial#: 16843009
(II) SIS(0): Year: 2000  Week: 44
(II) SIS(0): EDID Version: 1.1
(II) SIS(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) SIS(0): Sync:  Separate
(II) SIS(0): Max Image Size [cm]: horiz.: 32  vert.: 24
(II) SIS(0): Gamma: 2.80
(II) SIS(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) SIS(0): redX: 0.639 redY: 0.327   greenX: 0.278 greenY: 0.602
(II) SIS(0): blueX: 0.149 blueY: 0.065   whiteX: 0.283 whiteY: 0.298
(II) SIS(0): Supported established timings:
(II) SIS(0): 720x400@70Hz
(II) SIS(0): 640x480@60Hz
(II) SIS(0): 640x480@75Hz
(II) SIS(0): 800x600@60Hz
(II) SIS(0): 800x600@75Hz
(II) SIS(0): 1024x768@60Hz
(II) SIS(0): 1024x768@75Hz
(II) SIS(0): Manufacturer's mask: 0
(II) SIS(0): Supported standard timings:
(II) SIS(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) SIS(0): Supported detailed timing:
(II) SIS(0): clock: 78.8 MHz   Image Size:  310 x 230 mm
(II) SIS(0): h_active: 1024  h_sync: 1040  h_sync_end 1136 h_blank_end 1312 h_border: 0
(II) SIS(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 800 v_border: 0
(II) SIS(0): Monitor name: EV700
(II) SIS(0): Ranges: V min: 50 V max: 160 Hz, H min: 30 H max: 70 kHz, PixClock max 110 MHz
(II) SIS(0): Serial No: LIC04411506
(II) SIS(0): EDID (in hex):
(II) SIS(0): 	fc00000093d51c080415a000ffffffff
(II) SIS(0): 	40655d0961b51d08f8111f0860a15f09
(II) SIS(0): 	040000002802d1bfccc7be0020521f08
(II) SIS(0): 	f45f1e0830000000008d690000000000
(II) SIS(0): 	0a260d086302d1bf48000000b89e5f09
(II) SIS(0): 	8a01d1bf3d7663006902d1bf01000000
(II) SIS(0): 	ffffffff53ae1c080002d1bf9802d1bf
(II) SIS(0): 	92f60f086102d1bf01000000ffffffff
(II) SIS(0): EDID vendor "GWY", prod id 7010
(II) SIS(0): Using EDID range info for horizontal sync
(II) SIS(0): Using EDID range info for vertical refresh
(II) SIS(0): Printing DDC gathered Modelines:
(II) SIS(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) SIS(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) SIS(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) SIS(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) SIS(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) SIS(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) SIS(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) SIS(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) SIS(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(--) SIS(0): According to DDC size, CRT1 aspect ratio is 1.33:1 (normal)
(--) SIS(0): End of CRT1 DDC monitor info *************************************
(==) SIS(0): Min pixel clock is 10 MHz
(--) SIS(0): Max pixel clock is 243 MHz
(II) SIS(0): Replaced default mode list with built-in modes
(II) SIS(0): Using fake widescreen modes for CRT1 VGA devices
(II) SIS(0): 	Use option "ForceCRT1VGAAspect" to overrule
(II) SIS(0): "Unknown reason" in the following list means that the mode
(II) SIS(0): is not supported on the chipset/bridge/current output device.
(II) SIS(0): <default monitor>: Using hsync range of 30.00-70.00 kHz
(II) SIS(0): <default monitor>: Using vrefresh range of 50.00-160.00 Hz
(II) SIS(0): <default monitor>: Using maximum pixel clock of 110.00 MHz
(II) SIS(0): Estimated virtual size for aspect ratio 1.3333 is 1024x768
(II) SIS(0): Clock range:  10.00 to 243.27 MHz
(II) SIS(0): Not using driver mode "1280x1024" (width too large for virtual size)
(II) SIS(0): Not using default mode "800x600" (hsync out of range)
(II) SIS(0): Not using default mode "800x600" (hsync out of range)
(II) SIS(0): Not using default mode "640x480" (hsync out of range)
(II) SIS(0): Not using default mode "640x480" (hsync out of range)
(II) SIS(0): Not using default mode "1024x768" (hsync out of range)
(II) SIS(0): Not using default mode "1024x768" (hsync out of range)
(II) SIS(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) SIS(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) SIS(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) SIS(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) SIS(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) SIS(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) SIS(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) SIS(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) SIS(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) SIS(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) SIS(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) SIS(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) SIS(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) SIS(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) SIS(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) SIS(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) SIS(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) SIS(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) SIS(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) SIS(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) SIS(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) SIS(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) SIS(0): Not using default mode "1280x720" (width too large for virtual size)
(II) SIS(0): Not using default mode "1280x720" (width too large for virtual size)
(II) SIS(0): Not using default mode "1280x720" (width too large for virtual size)
(II) SIS(0): Not using default mode "1280x960" (width too large for virtual size)
(II) SIS(0): Not using default mode "1280x960" (width too large for virtual size)
(II) SIS(0): Not using default mode "1280x768" (width too large for virtual size)
(II) SIS(0): Not using default mode "1280x768" (width too large for virtual size)
(II) SIS(0): Not using default mode "1280x768" (width too large for virtual size)
(II) SIS(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) SIS(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) SIS(0): Not using default mode "1152x864" (width too large for virtual size)
(II) SIS(0): Not using default mode "1152x864" (width too large for virtual size)
(II) SIS(0): Not using default mode "1152x864" (width too large for virtual size)
(II) SIS(0): Not using default mode "1360x768" (width too large for virtual size)
(II) SIS(0): Not using default mode "1280x800" (width too large for virtual size)
(II) SIS(0): Not using default mode "1280x800" (width too large for virtual size)
(II) SIS(0): Not using default mode "1280x800" (width too large for virtual size)
(II) SIS(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) SIS(0): Not using default mode "1920x1080" (width too large for virtual size)
(II) SIS(0): Not using default mode "1280x854" (width too large for virtual size)
(II) SIS(0): Not using default mode "1280x854" (width too large for virtual size)
(II) SIS(0): Not using default mode "1280x854" (width too large for virtual size)
(--) SIS(0): Virtual size is 1024x768 (pitch 1024)
(**) SIS(0): *Driver mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
(II) SIS(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(**) SIS(0): *Driver mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
(II) SIS(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(**) SIS(0): *Driver mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) SIS(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(**) SIS(0): *Default mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
(II) SIS(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(**) SIS(0): *Default mode "1024x768": 78.7 MHz, 60.0 kHz, 75.0 Hz
(II) SIS(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(**) SIS(0): *Default mode "1024x768": 75.2 MHz, 56.6 kHz, 70.2 Hz
(II) SIS(0): Modeline "1024x768"x70.2   75.17  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.6 kHz)
(**) SIS(0): *Default mode "1024x768": 65.1 MHz, 48.5 kHz, 60.1 Hz
(II) SIS(0): Modeline "1024x768"x60.1   65.15  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.5 kHz)
(**) SIS(0): *Default mode "1024x768": 44.9 MHz, 35.5 kHz, 86.8 Hz (I)
(II) SIS(0): Modeline "1024x768"x86.8   44.86  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync (35.5 kHz)
(**) SIS(0): *Default mode "1024x576": 94.5 MHz, 69.9 kHz, 86.5 Hz
(II) SIS(0): Modeline "1024x576"x86.5   94.50  1024 1072 1168 1352  576 690 694 808 +hsync +vsync (69.9 kHz)
(**) SIS(0): *Default mode "1024x576": 78.7 MHz, 60.0 kHz, 75.0 Hz
(II) SIS(0): Modeline "1024x576"x75.0   78.75  1024 1040 1136 1312  576 686 690 800 +hsync +vsync (60.0 kHz)
(**) SIS(0): *Default mode "1024x576": 65.1 MHz, 48.5 kHz, 60.1 Hz
(II) SIS(0): Modeline "1024x576"x60.1   65.15  1024 1048 1184 1344  576 688 694 806 +hsync +vsync (48.5 kHz)
(**) SIS(0): *Default mode "960x600": 41.5 MHz, 37.1 kHz, 60.0 Hz
(II) SIS(0): Modeline "960x600"x60.0   41.50  960 1008 1088 1120  600 603 609 618 +hsync +vsync (37.1 kHz)
(**) SIS(0): *Default mode "960x540": 37.3 MHz, 33.8 kHz, 60.0 Hz
(II) SIS(0): Modeline "960x540"x60.0   37.29  960 976 1008 1104  540 543 549 563 +hsync +vsync (33.8 kHz)
(**) SIS(0): *Driver mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) SIS(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(**) SIS(0): *Driver mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) SIS(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) SIS(0): *Default mode "800x600": 68.2 MHz, 63.6 kHz, 100.0 Hz
(II) SIS(0): Modeline "800x600"x100.0   68.18  800 848 936 1072  600 601 604 636 +hsync +vsync (63.6 kHz)
(**) SIS(0): *Default mode "800x600": 56.2 MHz, 53.7 kHz, 85.1 Hz
(II) SIS(0): Modeline "800x600"x85.1   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(**) SIS(0): *Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) SIS(0): Modeline "800x600"x75.0   49.52  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(**) SIS(0): *Default mode "800x600": 50.1 MHz, 48.2 kHz, 72.4 Hz
(II) SIS(0): Modeline "800x600"x72.4   50.11  800 856 976 1040  600 637 643 666 +hsync +vsync (48.2 kHz)
(**) SIS(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) SIS(0): Modeline "800x600"x60.3   39.97  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) SIS(0): *Default mode "800x600": 36.1 MHz, 35.2 kHz, 56.3 Hz
(II) SIS(0): Modeline "800x600"x56.3   36.06  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) SIS(0): *Default mode "768x576": 35.0 MHz, 35.9 kHz, 60.1 Hz
(II) SIS(0): Modeline "768x576"x60.1   35.00  768 792 872 976  576 578 581 597 +hsync +vsync (35.9 kHz)
(**) SIS(0): *Default mode "720x576": 32.7 MHz, 35.9 kHz, 60.1 Hz
(II) SIS(0): Modeline "720x576"x60.1   32.73  720 744 816 912  576 578 581 597 +hsync +vsync (35.9 kHz)
(**) SIS(0): *Default mode "856x480": 33.9 MHz, 31.7 kHz, 59.8 Hz
(II) SIS(0): Modeline "856x480"x59.8   33.94  856 872 1000 1072  480 492 495 529 -hsync -vsync (31.7 kHz)
(**) SIS(0): *Default mode "856x480": 33.9 MHz, 30.5 kHz, 76.5 Hz (I)
(II) SIS(0): Modeline "856x480"x76.5   33.94  856 904 1048 1112  480 672 680 797 interlace +hsync +vsync (30.5 kHz)
(**) SIS(0): *Default mode "848x480": 33.7 MHz, 31.0 kHz, 60.0 Hz
(II) SIS(0): Modeline "848x480"x60.0   33.75  848 864 976 1088  480 486 494 517 -hsync -vsync (31.0 kHz)
(**) SIS(0): *Default mode "848x480": 33.9 MHz, 30.5 kHz, 76.5 Hz (I)
(II) SIS(0): Modeline "848x480"x76.5   33.94  848 904 1048 1112  480 672 680 797 interlace +hsync +vsync (30.5 kHz)
(**) SIS(0): *Default mode "800x480": 56.2 MHz, 53.7 kHz, 85.2 Hz
(II) SIS(0): Modeline "800x480"x85.2   56.25  800 832 896 1048  480 554 557 630 +hsync +vsync (53.7 kHz)
(**) SIS(0): *Default mode "800x480": 49.5 MHz, 46.9 kHz, 75.1 Hz
(II) SIS(0): Modeline "800x480"x75.1   49.52  800 816 896 1056  480 551 554 624 +hsync +vsync (46.9 kHz)
(**) SIS(0): *Default mode "800x480": 39.8 MHz, 37.7 kHz, 60.0 Hz
(II) SIS(0): Modeline "800x480"x60.0   39.77  800 840 968 1056  480 552 556 628 +hsync +vsync (37.7 kHz)
(**) SIS(0): *Default mode "720x480": 28.3 MHz, 31.6 kHz, 61.0 Hz
(II) SIS(0): Modeline "720x480"x61.0   28.28  720 728 840 896  480 490 492 517 -hsync -vsync (31.6 kHz)
(**) SIS(0): *Driver mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) SIS(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(**) SIS(0): *Driver mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) SIS(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) SIS(0): *Default mode "640x480": 52.4 MHz, 61.7 kHz, 119.9 Hz
(II) SIS(0): Modeline "640x480"x119.9   52.35  640 680 744 848  480 481 484 515 -hsync -vsync (61.7 kHz)
(**) SIS(0): *Default mode "640x480": 43.3 MHz, 51.1 kHz, 100.3 Hz
(II) SIS(0): Modeline "640x480"x100.3   43.29  640 680 744 848  480 481 484 509 -hsync -vsync (51.1 kHz)
(**) SIS(0): *Default mode "640x480": 36.1 MHz, 43.3 kHz, 85.1 Hz
(II) SIS(0): Modeline "640x480"x85.1   36.06  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(**) SIS(0): *Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) SIS(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(**) SIS(0): *Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) SIS(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(**) SIS(0): *Default mode "640x480": 25.1 MHz, 31.3 kHz, 59.7 Hz
(II) SIS(0): Modeline "640x480"x59.7   25.06  640 656 752 800  480 490 492 525 -hsync -vsync (31.3 kHz)
(**) SIS(0): *Driver mode "720x400": 28.3 MHz, 31.5 kHz, 70.1 Hz
(II) SIS(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(**) SIS(0): *Default mode "640x400": 25.1 MHz, 31.6 kHz, 71.6 Hz
(II) SIS(0): Modeline "640x400"x71.6   25.06  640 656 752 792  400 413 415 442 -hsync +vsync (31.6 kHz)
(**) SIS(0): *Default mode "512x384": 32.6 MHz, 48.5 kHz, 60.1 Hz (D)
(II) SIS(0): Modeline "512x384"x60.1   32.57  512 528 592 672  384 385 388 403 doublescan -hsync -vsync (48.5 kHz)
(**) SIS(0): *Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) SIS(0): Modeline "400x300"x60.3   19.98  400 416 480 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz)
(**) SIS(0): *Default mode "320x240": 12.5 MHz, 31.3 kHz, 60.7 Hz (D)
(II) SIS(0): Modeline "320x240"x60.7   12.53  320 328 376 400  240 245 246 258 doublescan -hsync -vsync (31.3 kHz)
(**) SIS(0): *Default mode "320x200": 12.5 MHz, 31.3 kHz, 70.9 Hz (D)
(II) SIS(0): Modeline "320x200"x70.9   12.53  320 328 376 400  200 206 207 221 doublescan -hsync +vsync (31.3 kHz)
(**) SIS(0): Display dimensions: (320, 240) mm
(**) SIS(0): DPI set to (81, 81)
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
(II) SIS(0): 2D acceleration enabled
(II) UnloadModule: "vesa"
(II) Unloading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers//fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux//libfbdevhw.so
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
	[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[20] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[21] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[22] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[23] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[24] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[25] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[26] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[27] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[28] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[29] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[30] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[31] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[32] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[33] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[34] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.1.0
	ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Video Driver, version 5.0
(II) SIS(0): initializing int10
(II) SIS(0): Primary V_BIOS segment is: 0xc000
(II) SIS(0): VESA BIOS detected
(II) SIS(0): VESA VBE Version 3.0
(II) SIS(0): VESA VBE Total Mem: 16384 kB
(II) SIS(0): VESA VBE OEM: SiS
(II) SIS(0): VESA VBE OEM Software Rev: 1.0
(II) SIS(0): VESA VBE OEM Vendor: Silicon Integrated Systems Corp.
(II) SIS(0): VESA VBE OEM Product: 6330
(II) SIS(0): VESA VBE OEM Product Rev: 2.03.00
(II) SIS(0): Setting custom mode 1024x768 on CRT1
(II) SIS(0): Setting custom mode 1024x768 on CRT2
(II) SIS(0): SiS76x/UMA: two video overlay(s) available in current mode
(II) SIS(0): RENDER acceleration enabled
(II) SIS(0): Framebuffer from (0,0) to (1023,32622)
(II) SIS(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	8x8 color pattern filled rectangles
	Solid Lines
	Dashed Lines
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
		32 8x8 color pattern slots
(--) SIS(0): CPU frequency 1599.58Mhz
(II) SIS(0): Benchmarking system RAM to video RAM memory transfer methods:
(--) SIS(0): 	Checked libc memcpy()... 	475.4 MiB/s
(--) SIS(0): 	Checked built-in-1 memcpy()... 	474.8 MiB/s
(--) SIS(0): 	Checked built-in-2 memcpy()... 	81.3 MiB/s
(--) SIS(0): 	Checked MMX memcpy()... 	473.9 MiB/s
(--) SIS(0): 	Checked 3DNow! memcpy()... 	473.0 MiB/s
(--) SIS(0): 	Checked MMX2 memcpy()... 	521.8 MiB/s
(--) SIS(0): Using MMX2 method for aligned data transfers to video RAM
(--) SIS(0): Using MMX2 method for unaligned data transfers to video RAM
(==) SIS(0): Backing store disabled
(==) SIS(0): Silken mouse enabled
(II) SIS(0): DPMS enabled
(II) SIS(0): Using SiS300/315/330/340 series HW Xv
(II) SIS(0): Default Xv adaptor is Video Overlay
(II) SIS(0): Initialized SISCTRL extension version 0.1
(II) SIS(0): Registered screen 0 with SISCTRL extension version 0.1
(==) RandR enabled
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
(II) config/hal: Adding input device Microsft Microsoft Wireless Desktop Receiver 3.1
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 2.2.5
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) Microsft Microsoft Wireless Desktop Receiver 3.1: always reports core events
(**) Microsft Microsoft Wireless Desktop Receiver 3.1: Device: "/dev/input/event3"
(II) Microsft Microsoft Wireless Desktop Receiver 3.1: Found keys
(II) Microsft Microsoft Wireless Desktop Receiver 3.1: Configuring as keyboard
(II) XINPUT: Adding extended input device "Microsft Microsoft Wireless Desktop Receiver 3.1" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Microsft Microsoft Wireless Desktop Receiver 3.1
(**) Microsft Microsoft Wireless Desktop Receiver 3.1: always reports core events
(**) Microsft Microsoft Wireless Desktop Receiver 3.1: Device: "/dev/input/event4"
(II) Microsft Microsoft Wireless Desktop Receiver 3.1: Found 9 mouse buttons
(II) Microsft Microsoft Wireless Desktop Receiver 3.1: Found x and y relative axes
(II) Microsft Microsoft Wireless Desktop Receiver 3.1: Found scroll wheel(s)
(II) Microsft Microsoft Wireless Desktop Receiver 3.1: Found keys
(II) Microsft Microsoft Wireless Desktop Receiver 3.1: Configuring as mouse
(II) Microsft Microsoft Wireless Desktop Receiver 3.1: Configuring as keyboard
(**) Microsft Microsoft Wireless Desktop Receiver 3.1: YAxisMapping: buttons 4 and 5
(**) Microsft Microsoft Wireless Desktop Receiver 3.1: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Microsft Microsoft Wireless Desktop Receiver 3.1" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Microsft Microsoft Wireless Desktop Receiver 3.1: (accel) keeping acceleration scheme 1
(**) Microsft Microsoft Wireless Desktop Receiver 3.1: (accel) filter chain progression: 2.00
(**) Microsft Microsoft Wireless Desktop Receiver 3.1: (accel) filter stage 0: 20.00 ms
(**) Microsft Microsoft Wireless Desktop Receiver 3.1: (accel) set acceleration profile 0
(II) Microsft Microsoft Wireless Desktop Receiver 3.1: initialized for relative axes.
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
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
(II) SIS(0): Setting custom mode 1024x768 on CRT1
(II) SIS(0): Setting custom mode 1024x768 on CRT2
(II) SIS(0): SiS76x/UMA: two video overlay(s) available in current mode
(II) SIS(0): Setting custom mode 1024x768 on CRT1
(II) SIS(0): Setting custom mode 1024x768 on CRT2
(II) SIS(0): SiS76x/UMA: two video overlay(s) available in current mode
```

From what I can figure out, Ubuntu **knows** that my monitor will support 1280x1024. What I've yet not figured out is why it insists on setting the maximum resolution to 1024x768. I see the "width too large for virtual size" message as the reason for not using driver mode "1280x1024". I'm trying to avoid using xorg.conf (which of course isn't installed by default). I've searched for hours across the Internet for a solution. (I did find an article posted in November 2009. The author promised to post part two to the article a few days later but has yet to do so. The part two is supposed to deal with changing the maximum resolution. Perhaps the author has yet to figure it out also.)

My motherboard is a Foxconn 761gxk8mc.

---

### Post by pi/roman on 2010-01-27
> (II) SIS(0): Not using driver mode "1280x1024" (width too large for virtual size)It looks like you have a wrong virtual size in your xorg.conf. You could either change it to 1280x1024 or just remove the virtual size from xorg.conf completely which is what I normally do.  That should do it.
Look in xorg.conf manual for more information:
man xorg.conf

---

### Post by lereveur on 2010-01-28
I realize that I've been a bit unclear when I said:
> I'm trying to avoid using xorg.conf (which of course isn't installed by default).
It's not simply that I'm avoiding using xorg.conf. When a person installs Karmic Koala in a new partition, xorg.conf is not created. Indeed, I have not created it either. So although you've shown the offending problem which I also mentioned here:
> I see the "width too large for virtual size" message as the reason for not using driver mode "1280x1024".
and, of course, the offending line from my Xorg.0.log file which you also quoted:
> (II) SIS(0): Not using driver mode "1280x1024" (width too large for virtual size)
So... to clarify, I want a way to fix the above problem **without** using xorg.conf, if at all possible.
Oh... and since I don't currently have an xorg.conf file, I **cannot** do as you recommended here:
> You could either change it to 1280x1024 or just remove the virtual size from xorg.conf completely which is what I normally do.
In any case, I do thank you for at least attempting to answer my problem.

---

### Post by pi/roman on 2010-01-28
Nuts, I should have paid more attention (slaps back of own hand).  I'll try to avoid convincing you to create an xorg.conf since it seems you do not desire so and I agree it should be possible to make it work without one.  But the problem you are running into is the reason I don't bother using xrandr.
I have some links that may or may not be helpful:
xrandr automation instructions:
[http://www.thinkwiki.org/wiki/Xorg_RandR_1.2#Now_automate_it_on_login](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2#Now_automate_it_on_login)
gdm configuration guide showing locations for configuration files:
[http://projects.gnome.org/gdm/docs/2.8/configuration.html](http://projects.gnome.org/gdm/docs/2.8/configuration.html)

---

### Post by lereveur on 2010-02-05
I couldn't make sense of the xrandr automation instructions. It was especially confusing because it was talking about laptops and external displays. I'm on a desktop computer. You would think someone would document this process for a desktop computer with only one monitor.

Anyway, since it appears that there is no help anywhere for my problem, I first decided to install the "SiSCtrl" utility. When I first ran that utility, it said that "EnableSisCtrl" was disabled.

So I had to go through the process of generating the xorg.conf after all. I added the "Option" to "EnableSisCtrl". This allowed me to run the "SiSCtrl" utility but it didn't work. It has a list of "Modes" on the first tab. "1280x1024" (the actual resolution I want) is not listed there. Even though it was in the drop down box for changing the resolution, clicking "Apply" had zero effect. Argh!

So back to the xorg.conf to manually fix it. I added the same "Modeline" for "1280x1024" in the "Monitor" section which I had added to the /etc/gdm/PreSession/Default script. I added "1280x1024" as a new "Modes" line in the "Screen" section / "Display" subsection. When I restarted X, I got an error stating something to the effect that there was a problem with the xorg.conf file. There were four possible solutions. The one that ended up being helpful was "Reconfigure". After it did its thing, it gave the warning that Ubuntu was starting in low resolution. Once I had logged in, I used System / Preferences / Display which actually let me change the resolution to "1280x1024". The "Refresh" is "0" but it seems to work fine. I looked at xorg.conf again but nothing had changed. I did notice that there is now an xorg.conf.failsafe file and the Xsession.options file has a line "allow-failsafe" but I don't know if that line wasn't already there.

Here is the contents of xorg.conf.failsafe:
```
Section "Device"
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
```

Here is the resulting Xorg.0.log:
```
X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux monreveur-desktop 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-17-generic root=UUID=0957c3b4-22a2-4a0e-ab42-1be3113d06ae ro quiet splash
Build Date: 14 November 2009  05:48:26PM
xorg-server 2:1.6.4-2ubuntu4.1 (buildd@) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(++) Log file: "/var/log/Xorg.failsafe.log", Time: Thu Feb  4 22:56:08 2010
(++) Using config file: "/etc/X11/xorg.conf.failsafe"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(--) using VT number 7

(--) PCI:*(0:1:0:0) 1039:6330:105b:0c92 Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter rev 0, Mem @ 0xe0000000/134217728, 0xe8000000/131072, I/O @ 0x0000d000/128
(II) Open ACPI successful (/var/run/acpid.socket)
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
	[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[24] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[25] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[26] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[27] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[28] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[29] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
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
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 2.2.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) VESA: driver for VESA chipsets: vesa
(II) Primary Device is: PCI 01@00:00:0
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
	[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[24] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[25] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[26] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[27] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[28] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[29] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.1.0
	ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Video Driver, version 5.0
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 16384 kB
(II) VESA(0): VESA VBE OEM: SiS
(II) VESA(0): VESA VBE OEM Software Rev: 1.0
(II) VESA(0): VESA VBE OEM Vendor: Silicon Integrated Systems Corp.
(II) VESA(0): VESA VBE OEM Product: 6330
(II) VESA(0): VESA VBE OEM Product Rev: 2.03.00
(II) VESA(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(==) VESA(0): Depth 24, (--) framebuffer bpp 32
(==) VESA(0): RGB weight 888
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) VESA(0): VESA VBE DDC supported
(II) VESA(0): VESA VBE DDC Level 2
(II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
(II) VESA(0): VESA VBE DDC read successfully
(II) VESA(0): Manufacturer: GWY  Model: 1b62  Serial#: 16843009
(II) VESA(0): Year: 2000  Week: 44
(II) VESA(0): EDID Version: 1.1
(II) VESA(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) VESA(0): Sync:  Separate
(II) VESA(0): Max Image Size [cm]: horiz.: 32  vert.: 24
(II) VESA(0): Gamma: 2.80
(II) VESA(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) VESA(0): redX: 0.639 redY: 0.327   greenX: 0.278 greenY: 0.602
(II) VESA(0): blueX: 0.149 blueY: 0.065   whiteX: 0.283 whiteY: 0.298
(II) VESA(0): Supported established timings:
(II) VESA(0): 720x400@70Hz
(II) VESA(0): 640x480@60Hz
(II) VESA(0): 640x480@75Hz
(II) VESA(0): 800x600@60Hz
(II) VESA(0): 800x600@75Hz
(II) VESA(0): 1024x768@60Hz
(II) VESA(0): 1024x768@75Hz
(II) VESA(0): Manufacturer's mask: 0
(II) VESA(0): Supported standard timings:
(II) VESA(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) VESA(0): Supported detailed timing:
(II) VESA(0): clock: 78.8 MHz   Image Size:  310 x 230 mm
(II) VESA(0): h_active: 1024  h_sync: 1040  h_sync_end 1136 h_blank_end 1312 h_border: 0
(II) VESA(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 800 v_border: 0
(II) VESA(0): Monitor name: EV700
(II) VESA(0): Ranges: V min: 50 V max: 160 Hz, H min: 30 H max: 70 kHz, PixClock max 110 MHz
(II) VESA(0): Serial No: LIC04411506
(II) VESA(0): EDID (in hex):
(II) VESA(0): 	00ffffffffffff001ef9621b01010101
(II) VESA(0): 	2c0a0101682018b4e8b479a353479a26
(II) VESA(0): 	10484ca54a0081800101010101010101
(II) VESA(0): 	010101010101c31e0020410020301060
(II) VESA(0): 	130036e61000001e000000fc00455637
(II) VESA(0): 	30300a20202020202020000000fd0032
(II) VESA(0): 	a01e460b000a202020202020000000ff
(II) VESA(0): 	004c494330343431313530360a200019
(II) VESA(0): EDID vendor "GWY", prod id 7010
(II) VESA(0): Using EDID range info for horizontal sync
(II) VESA(0): Using EDID range info for vertical refresh
(II) VESA(0): Printing DDC gathered Modelines:
(II) VESA(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) VESA(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) VESA(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) VESA(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) VESA(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) VESA(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) VESA(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) VESA(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) VESA(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) VESA(0): Searching for matching VESA mode(s):
Mode: 102 (800x600)
	ModeAttributes: 0x3f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0002f78
	BytesPerScanline: 100
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 4
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 3
	BankSize: 0
	NumberOfImages: 31
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 100
	BnkNumberOfImagePages: 31
	LinNumberOfImagePages: 31
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 101 (640x480)
	ModeAttributes: 0xbf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0002f78
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 24
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 24
	LinNumberOfImagePages: 24
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 100 (640x400)
	ModeAttributes: 0xbf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0002f78
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 31
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 31
	LinNumberOfImagePages: 31
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 103 (800x600)
	ModeAttributes: 0xbf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0002f78
	BytesPerScanline: 800
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 15
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 800
	BnkNumberOfImagePages: 15
	LinNumberOfImagePages: 15
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 104 (1024x768)
	ModeAttributes: 0x3f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0002f78
	BytesPerScanline: 128
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 4
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 3
	BankSize: 0
	NumberOfImages: 15
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 128
	BnkNumberOfImagePages: 15
	LinNumberOfImagePages: 15
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 105 (1024x768)
	ModeAttributes: 0xbf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0002f78
	BytesPerScanline: 1024
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 9
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 1024
	BnkNumberOfImagePages: 9
	LinNumberOfImagePages: 9
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 107 (1280x1024)
	ModeAttributes: 0xbf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0002f78
	BytesPerScanline: 1280
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 5
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 5
	LinNumberOfImagePages: 5
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 125 (1600x1200)
	ModeAttributes: 0xbf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0002f78
	BytesPerScanline: 1600
	XResolution: 1600
	YResolution: 1200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 3
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 1600
	BnkNumberOfImagePages: 3
	LinNumberOfImagePages: 3
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 126 (1600x1200)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0002f78
	BytesPerScanline: 3200
	XResolution: 1600
	YResolution: 1200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 3200
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 10d (320x200)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0002f78
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 15
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 63
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 63
	LinNumberOfImagePages: 63
	LinRedMaskSize: 5
	LinRedFieldPosition: 10
	LinGreenMaskSize: 5
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 10e (320x200)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0002f78
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 63
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 63
	LinNumberOfImagePages: 63
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 110 (640x480)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0002f78
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 15
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 11
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 11
	LinNumberOfImagePages: 11
	LinRedMaskSize: 5
	LinRedFieldPosition: 10
	LinGreenMaskSize: 5
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 111 (640x480)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0002f78
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 11
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 11
	LinNumberOfImagePages: 11
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 113 (800x600)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0002f78
	BytesPerScanline: 1600
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 15
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 7
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 1600
	BnkNumberOfImagePages: 7
	LinNumberOfImagePages: 7
	LinRedMaskSize: 5
	LinRedFieldPosition: 10
	LinGreenMaskSize: 5
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 114 (800x600)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0002f78
	BytesPerScanline: 1600
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 7
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 1600
	BnkNumberOfImagePages: 7
	LinNumberOfImagePages: 7
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 116 (1024x768)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0002f78
	BytesPerScanline: 2048
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 15
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 4
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 2048
	BnkNumberOfImagePages: 4
	LinNumberOfImagePages: 4
	LinRedMaskSize: 5
	LinRedFieldPosition: 10
	LinGreenMaskSize: 5
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 117 (1024x768)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0002f78
	BytesPerScanline: 2048
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 4
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 2048
	BnkNumberOfImagePages: 4
	LinNumberOfImagePages: 4
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 119 (1280x1024)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0002f78
	BytesPerScanline: 2560
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 15
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 2
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 5
	LinRedFieldPosition: 10
	LinGreenMaskSize: 5
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 11a (1280x1024)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0002f78
	BytesPerScanline: 2560
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 2
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 127 (320x240)
	ModeAttributes: 0xbf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0002f78
	BytesPerScanline: 320
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 63
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 320
	BnkNumberOfImagePages: 63
	LinNumberOfImagePages: 63
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 128 (400x300)
	ModeAttributes: 0xbf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0002f78
	BytesPerScanline: 400
	XResolution: 400
	YResolution: 300
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 63
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 400
	BnkNumberOfImagePages: 63
	LinNumberOfImagePages: 63
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 129 (512x384)
	ModeAttributes: 0xbf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0002f78
	BytesPerScanline: 512
	XResolution: 512
	YResolution: 384
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 41
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 512
	BnkNumberOfImagePages: 41
	LinNumberOfImagePages: 41
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 12a (320x240)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0002f78
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 41
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 41
	LinNumberOfImagePages: 41
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 12b (400x300)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0002f78
	BytesPerScanline: 800
	XResolution: 400
	YResolution: 300
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 31
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 800
	BnkNumberOfImagePages: 31
	LinNumberOfImagePages: 31
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 12c (512x384)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0002f78
	BytesPerScanline: 1024
	XResolution: 512
	YResolution: 384
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 20
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 1024
	BnkNumberOfImagePages: 20
	LinNumberOfImagePages: 20
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 12d (320x200)
	ModeAttributes: 0xbf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0002f78
	BytesPerScanline: 320
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 127
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 320
	BnkNumberOfImagePages: 127
	LinNumberOfImagePages: 127
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 131 (640x400)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0002f78
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 15
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 15
	LinNumberOfImagePages: 15
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
*Mode: 112 (640x480)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0002f78
	BytesPerScanline: 2560
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 5
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 5
	LinNumberOfImagePages: 5
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 0
*Mode: 115 (800x600)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0002f78
	BytesPerScanline: 3200
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 3
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 3200
	BnkNumberOfImagePages: 3
	LinNumberOfImagePages: 3
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 0
*Mode: 118 (1024x768)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0002f78
	BytesPerScanline: 4096
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 4096
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 0
*Mode: 11b (1280x1024)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0002f78
	BytesPerScanline: 5120
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 5120
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 0
*Mode: 132 (1600x1200)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0002f78
	BytesPerScanline: 6400
	XResolution: 1600
	YResolution: 1200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 6400
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 0

(II) VESA(0): Total Memory: 256 64KB banks (16384kB)
(II) VESA(0): Configured Monitor: Using hsync range of 30.00-70.00 kHz
(II) VESA(0): Configured Monitor: Using vrefresh range of 50.00-160.00 Hz
(II) VESA(0): Configured Monitor: Using maximum pixel clock of 110.00 MHz
(WW) VESA(0): Unable to estimate virtual size
(II) VESA(0): Not using built-in mode "1600x1200" (no mode of this name)
(--) VESA(0): Virtual size is 1280x1024 (pitch 1280)
(**) VESA(0): *Built-in mode "1280x1024"
(**) VESA(0): *Built-in mode "1024x768"
(**) VESA(0): *Built-in mode "800x600"
(**) VESA(0): *Built-in mode "640x480"
(**) VESA(0): Display dimensions: (320, 240) mm
(**) VESA(0): DPI set to (101, 108)
(**) VESA(0): Using "Shadow Framebuffer"
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules//libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.1.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(==) Depth 24 pixmap format is 32 bpp
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
	[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[24] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[25] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[26] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[27] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[28] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[29] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 16384 kB
(II) VESA(0): VESA VBE OEM: SiS
(II) VESA(0): VESA VBE OEM Software Rev: 1.0
(II) VESA(0): VESA VBE OEM Vendor: Silicon Integrated Systems Corp.
(II) VESA(0): VESA VBE OEM Product: 6330
(II) VESA(0): VESA VBE OEM Product Rev: 2.03.00
(II) VESA(0): virtual address = 0xb65dd000,
	physical address = 0xe0000000, size = 16777216
(II) VESA(0): Setting up VESA Mode 0x11B (1280x1024)
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Backing store disabled
(II) VESA(0): DPMS enabled
(==) RandR enabled
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
(II) config/hal: Adding input device Microsft Microsoft Wireless Desktop Receiver 3.1
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 2.2.5
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) Microsft Microsoft Wireless Desktop Receiver 3.1: always reports core events
(**) Microsft Microsoft Wireless Desktop Receiver 3.1: Device: "/dev/input/event4"
(II) Microsft Microsoft Wireless Desktop Receiver 3.1: Found 9 mouse buttons
(II) Microsft Microsoft Wireless Desktop Receiver 3.1: Found x and y relative axes
(II) Microsft Microsoft Wireless Desktop Receiver 3.1: Found scroll wheel(s)
(II) Microsft Microsoft Wireless Desktop Receiver 3.1: Found keys
(II) Microsft Microsoft Wireless Desktop Receiver 3.1: Configuring as mouse
(II) Microsft Microsoft Wireless Desktop Receiver 3.1: Configuring as keyboard
(**) Microsft Microsoft Wireless Desktop Receiver 3.1: YAxisMapping: buttons 4 and 5
(**) Microsft Microsoft Wireless Desktop Receiver 3.1: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Microsft Microsoft Wireless Desktop Receiver 3.1" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Microsft Microsoft Wireless Desktop Receiver 3.1: (accel) keeping acceleration scheme 1
(**) Microsft Microsoft Wireless Desktop Receiver 3.1: (accel) filter chain progression: 2.00
(**) Microsft Microsoft Wireless Desktop Receiver 3.1: (accel) filter stage 0: 20.00 ms
(**) Microsft Microsoft Wireless Desktop Receiver 3.1: (accel) set acceleration profile 0
(II) Microsft Microsoft Wireless Desktop Receiver 3.1: initialized for relative axes.
(II) config/hal: Adding input device Microsft Microsoft Wireless Desktop Receiver 3.1
(**) Microsft Microsoft Wireless Desktop Receiver 3.1: always reports core events
(**) Microsft Microsoft Wireless Desktop Receiver 3.1: Device: "/dev/input/event3"
(II) Microsft Microsoft Wireless Desktop Receiver 3.1: Found keys
(II) Microsft Microsoft Wireless Desktop Receiver 3.1: Configuring as keyboard
(II) XINPUT: Adding extended input device "Microsft Microsoft Wireless Desktop Receiver 3.1" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
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
```

Notice that it no longer has the offending line:
```
(II) SIS(0): Not using driver mode "1280x1024" (width too large for virtual size)
```

Now that it's actually doing what I want, I don't want to mess with it. However, I'm curious if there's some shortcut to getting it to do that "Reconfigure" thing. I'm also curious whether simply adding "allow-failsafe" to the Xsession.options file is the quickest solution.

---

