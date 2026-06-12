---
title: "System bell (I think) crashes X"
date: 2008-09-16
forum: General Help
---

### Post by dannyking on 2008-09-16
Hi,

I've filed a bug here [https://bugs.launchpad.net/ubuntu/+bug/270790](https://bugs.launchpad.net/ubuntu/+bug/270790) but I thought I'd try and get an immediate fix for my issue.

Whenever I press tab in a terminal (I have tried in gnome-terminal and xterm) my X server restarts! It also restarts if I press delete and there is no text left to delete in the terminal. The only thing that happens in both those situations is the beep, so I disabled the bell in /etc/inputrc and that has stopped the crashing.

Does anyone know how I can re-enable the beep and not have X crash?

Thanks!

---

### Post by Crafty Kisses on 2008-09-16
Can you post your X logs?

---

### Post by dannyking on 2008-09-16
Of course. Could you tell me the location of these logs? Thanks.

---

### Post by dannyking on 2008-09-16
Here is Xorg.0.log if that's correct?

```
X.Org X Server 1.4.0.90

Release Date: 5 September 2007

X Protocol Version 11, Revision 0

Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)

Current Operating System: Linux vince 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686

Build Date: 13 June 2008  01:08:21AM

 

	Before reporting problems, check http://wiki.x.org

	to make sure that you have the latest version.

Module Loader present

Markers: (--) probed, (**) from config file, (==) default setting,

	(++) from command line, (!!) notice, (II) informational,

	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.

(==) Log file: "/var/log/Xorg.0.log", Time: Tue Sep 16 11:53:14 2008

(==) Using config file: "/etc/X11/xorg.conf"

(==) ServerLayout "Default Layout"

(**) |-->Screen "Default Screen" (0)

(**) |   |-->Monitor "Configured Monitor"

(**) |   |-->Device "Configured Video Device"

(**) |-->Input Device "stylus"

(**) |-->Input Device "cursor"

(**) |-->Input Device "eraser"

(**) |-->Input Device "pad"

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

(II) PCI: 00:00:0: chip 10de,005e card 1043,815a rev a3 class 05,80,00 hdr 00

(II) PCI: 00:01:0: chip 10de,0050 card 1043,815a rev a3 class 06,01,00 hdr 80

(II) PCI: 00:01:1: chip 10de,0052 card 1043,815a rev a2 class 0c,05,00 hdr 80

(II) PCI: 00:02:0: chip 10de,005a card 1043,815a rev a2 class 0c,03,10 hdr 80

(II) PCI: 00:02:1: chip 10de,005b card 1043,815a rev a3 class 0c,03,20 hdr 80

(II) PCI: 00:06:0: chip 10de,0053 card f043,815a rev f2 class 01,01,8a hdr 00

(II) PCI: 00:07:0: chip 10de,0054 card 1043,815a rev f3 class 01,01,85 hdr 00

(II) PCI: 00:08:0: chip 10de,0055 card 1043,815a rev f3 class 01,01,85 hdr 00

(II) PCI: 00:09:0: chip 10de,005c card 0000,0000 rev a2 class 06,04,01 hdr 01

(II) PCI: 00:0a:0: chip 10de,0057 card 1043,8141 rev a3 class 06,80,00 hdr 00

(II) PCI: 00:0b:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01

(II) PCI: 00:0c:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01

(II) PCI: 00:0d:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01

(II) PCI: 00:0e:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01

(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80

(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80

(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80

(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80

(II) PCI: 01:00:0: chip 10de,00c0 card 0000,0000 rev a2 class 03,00,00 hdr 00

(II) PCI: 05:08:0: chip 1102,0007 card 1102,100a rev 00 class 04,01,00 hdr 00

(II) PCI: End of PCI scan

(II) PCI-to-ISA bridge:

(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)

(II) Subtractive PCI-to-PCI bridge:

(II) Bus 5: bridge is at (0:9:0), (0,5,5), BCTRL: 0x0202 (VGA_EN is cleared)

(II) Bus 5 I/O range:

	[0] -1	0	0x0000a000 - 0x0000afff (0x1000) IX[B]

(II) PCI-to-PCI bridge:

(II) Bus 4: bridge is at (0:11:0), (0,4,4), BCTRL: 0x0002 (VGA_EN is cleared)

(II) PCI-to-PCI bridge:

(II) Bus 3: bridge is at (0:12:0), (0,3,3), BCTRL: 0x0002 (VGA_EN is cleared)

(II) PCI-to-PCI bridge:

(II) Bus 2: bridge is at (0:13:0), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)

(II) PCI-to-PCI bridge:

(II) Bus 1: bridge is at (0:14:0), (0,1,1), BCTRL: 0x000a (VGA_EN is set)

(II) Bus 1 non-prefetchable memory range:

	[0] -1	0	0xc0000000 - 0xc2ffffff (0x3000000) MX[B]

(II) Bus 1 prefetchable memory range:

	[0] -1	0	0xa0000000 - 0xbfffffff (0x20000000) MX[B]

(II) Host-to-PCI bridge:

(II) Bus 0: bridge is at (0:24:0), (0,0,5), BCTRL: 0x0008 (VGA_EN is set)

(II) Bus 0 I/O range:

	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]

(II) Bus 0 non-prefetchable memory range:

	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]

(II) Bus 0 prefetchable memory range:

	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]

(--) PCI:*(1:0:0) nVidia Corporation NV41 [GeForce 6800 GS] rev 162, Mem @ 0xc0000000/24, 0xa0000000/29, 0xc1000000/24, BIOS @ 0xc2000000/17

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

(II) Active PCI resource ranges:

	[0] -1	0	0xc3000000 - 0xc3000fff (0x1000) MX[B]

	[1] -1	0	0xc3001000 - 0xc3001fff (0x1000) MX[B]

	[2] -1	0	0xc3002000 - 0xc3002fff (0x1000) MX[B]

	[3] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]

	[4] -1	0	0xc3003000 - 0xc3003fff (0x1000) MX[B]

	[5] -1	0	0xc2000000 - 0xc201ffff (0x20000) MX[B](B)

	[6] -1	0	0xc1000000 - 0xc1ffffff (0x1000000) MX[B](B)

	[7] -1	0	0xa0000000 - 0xbfffffff (0x20000000) MX[B](B)

	[8] -1	0	0xc0000000 - 0xc0ffffff (0x1000000) MX[B](B)

	[9] -1	0	0x0000a000 - 0x0000a01f (0x20) IX[B]

	[10] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]

	[11] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]

	[12] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]

	[13] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]

	[14] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]

	[15] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]

	[16] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]

	[17] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]

	[18] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]

	[19] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]

	[20] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]

	[21] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]

	[22] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]

	[23] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]

	[24] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]

(II) Active PCI resource ranges after removing overlaps:

	[0] -1	0	0xc3000000 - 0xc3000fff (0x1000) MX[B]

	[1] -1	0	0xc3001000 - 0xc3001fff (0x1000) MX[B]

	[2] -1	0	0xc3002000 - 0xc3002fff (0x1000) MX[B]

	[3] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]

	[4] -1	0	0xc3003000 - 0xc3003fff (0x1000) MX[B]

	[5] -1	0	0xc2000000 - 0xc201ffff (0x20000) MX[B](B)

	[6] -1	0	0xc1000000 - 0xc1ffffff (0x1000000) MX[B](B)

	[7] -1	0	0xa0000000 - 0xbfffffff (0x20000000) MX[B](B)

	[8] -1	0	0xc0000000 - 0xc0ffffff (0x1000000) MX[B](B)

	[9] -1	0	0x0000a000 - 0x0000a01f (0x20) IX[B]

	[10] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]

	[11] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]

	[12] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]

	[13] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]

	[14] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]

	[15] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]

	[16] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]

	[17] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]

	[18] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]

	[19] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]

	[20] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]

	[21] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]

	[22] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]

	[23] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]

	[24] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]

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

	[4] -1	0	0xc3000000 - 0xc3000fff (0x1000) MX[B]

	[5] -1	0	0xc3001000 - 0xc3001fff (0x1000) MX[B]

	[6] -1	0	0xc3002000 - 0xc3002fff (0x1000) MX[B]

	[7] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]

	[8] -1	0	0xc3003000 - 0xc3003fff (0x1000) MX[B]

	[9] -1	0	0xc2000000 - 0xc201ffff (0x20000) MX[B](B)

	[10] -1	0	0xc1000000 - 0xc1ffffff (0x1000000) MX[B](B)

	[11] -1	0	0xa0000000 - 0xbfffffff (0x20000000) MX[B](B)

	[12] -1	0	0xc0000000 - 0xc0ffffff (0x1000000) MX[B](B)

	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]

	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]

	[15] -1	0	0x0000a000 - 0x0000a01f (0x20) IX[B]

	[16] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]

	[17] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]

	[18] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]

	[19] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]

	[20] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]

	[21] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]

	[22] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]

	[23] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]

	[24] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]

	[25] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]

	[26] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]

	[27] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]

	[28] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]

	[29] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]

	[30] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]

(II) "extmod" will be loaded by default.

(II) "dbe" will be loaded by default.

(II) "glx" will be loaded. This was enabled by default and also specified in the config file.

(II) "freetype" will be loaded by default.

(II) "record" will be loaded by default.

(II) "dri" will be loaded by default.

(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so

(II) Module glx: vendor="NVIDIA Corporation"

	compiled for 4.0.2, module version = 1.0.0

	Module class: X.Org Server Extension

	ABI class: X.Org Server Extension, version 0.1

(II) NVIDIA GLX Module  169.12  Thu Feb 14 18:45:56 PST 2008

(II) Loading extension GLX

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

(II) LoadModule: "nvidia"

(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so

(II) Module nvidia: vendor="NVIDIA Corporation"

	compiled for 4.0.2, module version = 1.0.0

	Module class: X.Org Video Driver

(II) LoadModule: "wacom"

(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so

(II) Module wacom: vendor="X.Org Foundation"

	compiled for 4.3.99.902, module version = 1.0.0

	Module class: X.Org XInput Driver

	ABI class: X.Org XInput driver, version 2.0

(II) Wacom driver level: 47-0.7.9-11 $

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

(II) NVIDIA dlloader X Driver  169.12  Thu Feb 14 17:55:38 PST 2008

(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs

(II) Primary Device is: PCI 01:00:0

(--) Assigning device section with no busID to primary device

(--) Chipset NVIDIA GPU found

(II) Loading sub module "fb"

(II) LoadModule: "fb"

(II) Loading /usr/lib/xorg/modules//libfb.so

(II) Module fb: vendor="X.Org Foundation"

	compiled for 1.4.0.90, module version = 1.0.0

	ABI class: X.Org ANSI C Emulation, version 0.3

(II) Loading sub module "wfb"

(II) LoadModule: "wfb"

(II) Loading /usr/lib/xorg/modules//libwfb.so

(II) Module wfb: vendor="X.Org Foundation"

	compiled for 1.4.0.90, module version = 1.0.0

	ABI class: X.Org ANSI C Emulation, version 0.3

(II) Loading sub module "ramdac"

(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in

(II) resource ranges after xf86ClaimFixedResources() call:

	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)

	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]

	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]

	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]

	[4] -1	0	0xc3000000 - 0xc3000fff (0x1000) MX[B]

	[5] -1	0	0xc3001000 - 0xc3001fff (0x1000) MX[B]

	[6] -1	0	0xc3002000 - 0xc3002fff (0x1000) MX[B]

	[7] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]

	[8] -1	0	0xc3003000 - 0xc3003fff (0x1000) MX[B]

	[9] -1	0	0xc2000000 - 0xc201ffff (0x20000) MX[B](B)

	[10] -1	0	0xc1000000 - 0xc1ffffff (0x1000000) MX[B](B)

	[11] -1	0	0xa0000000 - 0xbfffffff (0x20000000) MX[B](B)

	[12] -1	0	0xc0000000 - 0xc0ffffff (0x1000000) MX[B](B)

	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]

	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]

	[15] -1	0	0x0000a000 - 0x0000a01f (0x20) IX[B]

	[16] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]

	[17] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]

	[18] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]

	[19] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]

	[20] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]

	[21] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]

	[22] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]

	[23] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]

	[24] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]

	[25] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]

	[26] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]

	[27] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]

	[28] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]

	[29] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]

	[30] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]

(II) resource ranges after probing:

	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)

	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]

	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]

	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]

	[4] -1	0	0xc3000000 - 0xc3000fff (0x1000) MX[B]

	[5] -1	0	0xc3001000 - 0xc3001fff (0x1000) MX[B]

	[6] -1	0	0xc3002000 - 0xc3002fff (0x1000) MX[B]

	[7] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]

	[8] -1	0	0xc3003000 - 0xc3003fff (0x1000) MX[B]

	[9] -1	0	0xc2000000 - 0xc201ffff (0x20000) MX[B](B)

	[10] -1	0	0xc1000000 - 0xc1ffffff (0x1000000) MX[B](B)

	[11] -1	0	0xa0000000 - 0xbfffffff (0x20000000) MX[B](B)

	[12] -1	0	0xc0000000 - 0xc0ffffff (0x1000000) MX[B](B)

	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]

	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]

	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]

	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]

	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]

	[18] -1	0	0x0000a000 - 0x0000a01f (0x20) IX[B]

	[19] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]

	[20] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]

	[21] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]

	[22] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]

	[23] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]

	[24] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]

	[25] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]

	[26] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]

	[27] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]

	[28] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]

	[29] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]

	[30] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]

	[31] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]

	[32] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]

	[33] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]

	[34] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]

	[35] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]

(II) Setting vga for screen 0.

(II) NVIDIA(0): Creating default Display subsection in Screen section

	"Default Screen" for depth/fbbpp 24/32

(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32

(==) NVIDIA(0): RGB weight 888

(==) NVIDIA(0): Default visual is TrueColor

(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)

(**) NVIDIA(0): Option "NoLogo" "True"

(**) NVIDIA(0): Enabling RENDER acceleration

(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is

(II) NVIDIA(0):     enabled.

(II) NVIDIA(0): NVIDIA GPU GeForce 6800 GS (NV41) at PCI:1:0:0 (GPU-0)

(--) NVIDIA(0): Memory: 524288 kBytes

(--) NVIDIA(0): VideoBIOS: 05.41.02.48.a1

(II) NVIDIA(0): Detected PCI Express Link width: 16X

(--) NVIDIA(0): Interlaced video modes are supported on this GPU

(--) NVIDIA(0): Connected display device(s) on GeForce 6800 GS at PCI:1:0:0:

(--) NVIDIA(0):     Sony SDM-S75D/F/N (DFP-0)

(--) NVIDIA(0): Sony SDM-S75D/F/N (DFP-0): 155.0 MHz maximum pixel clock

(--) NVIDIA(0): Sony SDM-S75D/F/N (DFP-0): Internal Single Link TMDS

(II) NVIDIA(0): Assigned Display Device: DFP-0

(==) NVIDIA(0): 

(==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"

(==) NVIDIA(0):     will be used as the requested mode.

(==) NVIDIA(0): 

(II) NVIDIA(0): Validated modes:

(II) NVIDIA(0):     "nvidia-auto-select"

(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024

(--) NVIDIA(0): DPI set to (95, 96); computed from "UseEdidDpi" X config

(--) NVIDIA(0):     option

(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.

(--) Depth 24 pixmap format is 32 bpp

(II) do I need RAC?  No, I don't.

(II) resource ranges after preInit:

	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)

	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]

	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]

	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]

	[4] -1	0	0xc3000000 - 0xc3000fff (0x1000) MX[B]

	[5] -1	0	0xc3001000 - 0xc3001fff (0x1000) MX[B]

	[6] -1	0	0xc3002000 - 0xc3002fff (0x1000) MX[B]

	[7] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]

	[8] -1	0	0xc3003000 - 0xc3003fff (0x1000) MX[B]

	[9] -1	0	0xc2000000 - 0xc201ffff (0x20000) MX[B](B)

	[10] -1	0	0xc1000000 - 0xc1ffffff (0x1000000) MX[B](B)

	[11] -1	0	0xa0000000 - 0xbfffffff (0x20000000) MX[B](B)

	[12] -1	0	0xc0000000 - 0xc0ffffff (0x1000000) MX[B](B)

	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]

	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]

	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]

	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]

	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]

	[18] -1	0	0x0000a000 - 0x0000a01f (0x20) IX[B]

	[19] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]

	[20] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]

	[21] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]

	[22] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]

	[23] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]

	[24] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]

	[25] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]

	[26] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]

	[27] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]

	[28] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]

	[29] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]

	[30] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]

	[31] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]

	[32] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]

	[33] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]

	[34] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]

	[35] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]

(II) NVIDIA(0): Initialized GPU GART.

(II) NVIDIA(0): Setting mode "nvidia-auto-select"

(II) Loading extension NV-GLX

(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized

(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture

(==) NVIDIA(0): Backing store disabled

(==) NVIDIA(0): Silken mouse enabled

(II) NVIDIA(0): DPMS enabled

(II) Loading extension NV-CONTROL

(==) RandR enabled

(II) Setting vga for screen 0.

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

(II) Initializing extension GLX

(**) Option "SendCoreEvents"

(**) stylus: always reports core events

(**) stylus device is /dev/input/wacom

(**) stylus is in absolute mode

(**) WACOM: suppress value is 2

(**) Option "USB" "on"

(**) stylus: reading USB link

(**) Option "BaudRate" "9600"

(**) Option "SendCoreEvents"

(**) cursor: always reports core events

(**) cursor device is /dev/input/wacom

(**) cursor is in relative mode

(**) WACOM: suppress value is 2

(**) Option "USB" "on"

(**) cursor: reading USB link

(**) Option "BaudRate" "9600"

(**) Option "SendCoreEvents"

(**) eraser: always reports core events

(**) eraser device is /dev/input/wacom

(**) eraser is in absolute mode

(**) WACOM: suppress value is 2

(**) Option "USB" "on"

(**) eraser: reading USB link

(**) Option "BaudRate" "9600"

(**) Option "SendCoreEvents"

(**) pad: always reports core events

(**) pad device is /dev/input/wacom

(**) pad is in relative mode

(**) WACOM: suppress value is 2

(**) Option "USB" "on"

(**) pad: reading USB link

(**) Option "BaudRate" "9600"

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

(**) Option "XkbLayout" "gb"

(**) Generic Keyboard: XkbLayout: "gb"

(**) Option "CustomKeycodes" "off"

(**) Generic Keyboard: CustomKeycodes disabled

(II) evaluating device (Generic Keyboard)

(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)

(II) evaluating device (Configured Mouse)

(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)

(II) evaluating device (pad)

(II) XINPUT: Adding extended input device "pad" (type: Wacom Pad)

(II) evaluating device (eraser)

(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)

(II) evaluating device (cursor)

(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)

(II) evaluating device (stylus)

(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)

(**) Option "Device" "/dev/input/wacom"

pad Wacom X driver grabbed event device

(==) Wacom using pressure threshold of 30 for button 1

(==) Wacom USB Volito2 tablet speed=9600 maxX=5104 maxY=3712 maxZ=511 resX=1016 resY=1016  tilt=enabled

(==) Wacom device "pad" top X=0 top Y=0 bottom X=5104 bottom Y=3712 resol X=1016 resol Y=1016

(==) Wacom device "eraser" top X=0 top Y=0 bottom X=5104 bottom Y=3712 resol X=1016 resol Y=1016

(==) Wacom device "cursor" top X=0 top Y=0 bottom X=5104 bottom Y=3712 resol X=1016 resol Y=1016

(==) Wacom device "stylus" top X=0 top Y=0 bottom X=5104 bottom Y=3712 resol X=1016 resol Y=1016

(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"

(II) Configured Mouse: ps2EnableDataReporting: succeeded

SetClientVersion: 0 9
```

---

### Post by lukyluke on 2008-09-30
I have the same identical problem.
Whenever something produces a system bell the X server crashes.


I think that there is an issue with the wacom X driver for the tablet.

Since when the tablet is not plugged into the USB the X server does not crash with system bells.

To get the wacom tablet workin (an USB Bamboo one)
I followed the HOWTO here [URL="http://ubuntuforums.org/showthread.php?t=765915&page=4"]

If I understand correctly the X driver one has installed at the end of all the steps described in the HOWTO are  the distribution version:
indeed the output of the dpkg --list|grep input-wacom is:
>ii  xserver-xorg-input-wacom                   1:0.7.9.8-0ubuntu3                          X.Org X server -- Wacom input driver

On my Desktop (dell optiplex gx620) I reproduce the bug you are talking about. 
On my laptop (hpdv2000) everything works smooth.

The differences are the graphic card
ati radeon on the desktop with the driver fglrx by ati
nvidia with the nvdia glx on the laptop.

Also the other difference is that on the desktop I have a standard 32 bit kubuntu 8.04 version :
2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux
whether on the laptop I have an amd64 kubuntu 8.04 sytem...

I have all the repositories enabled included the backports in both of them. And both of them are up to date with the central repositories

Another  difference between the two systems are the USB keyboard and mouse on the desktop.
However I tried to play around disconnecting the USB mouse and did not get any improvement.

I also blacklisted the pcspkr module but with no effect.

I attach the xorg.log file for debugging purposes.


Disabling the bell (as you suggest) in bash is just a very unstable fix since each time other terminal applications (such vi) would notify the user with the system bell the X server  crashes.

I tried both properietary and xorg ati module and both of them crash. 
As I see from your log you have an Nvidia chipset so probably the problem is not in the chipset driver.

The interesting thing is that if the tablet is not attached to the USB,the X server works smooth as it does not load the wacom driver.

Hope this bit of information helps in sorting out a solution
Regards

---

### Post by KeyserSoze93 on 2008-09-30
not really a propper fix, but try tunning

xset -b

in an xterm or whatever, once x is running

i do this to disable the bell within x because it it too loud an intrusive on my laptop, and it should would on all apps which run in the xterminal (and any others you open in that sessioN0

---

