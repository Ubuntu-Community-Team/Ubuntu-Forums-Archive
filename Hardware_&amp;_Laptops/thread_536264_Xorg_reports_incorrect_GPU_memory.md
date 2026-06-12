---
title: "Xorg reports incorrect GPU memory"
date: 2007-08-27
forum: Hardware &amp; Laptops
---

### Post by dreadlord_chris on 2007-08-27
I have an NVIDIA GPU GeForce 7300 LE with 128MB RAM installed in a PCI-E slot
My system has 1GB RAM

Xorg shows though:
```

(II) NVIDIA(0): NVIDIA GPU GeForce 7300 LE (G72) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes

```

I'm assuming that's *supposed* to be the GPU memory, but 524288 kB != 128 MB

btw... this has been true for me with both feisty & gutsy...

---

### Post by kidders on 2007-08-28
Hi there,

If Xorg is mis-detecting your video RAM (which does seem to happen occasionally), then you can always specify it manually.

---

### Post by dreadlord_chris on 2007-08-28
> **kidders said:**
> Hi there,

If Xorg is mis-detecting your video RAM (which does seem to happen occasionally), then you can always specify it manually.

Yeah, I tried manually specifying the RAM - didn't make any difference, I still get the same results...

---

### Post by Marat Galiev on 2007-08-28
use option in you xorg.conf
**Option "****VideoRAM xxx"**where xxx-you ram size in KB.

---

### Post by dreadlord_chris on 2007-08-28
> **Marat Galiev said:**
> use option in you xorg.conf
**Option "****VideoRAM xxx"**where xxx-you ram size in KB.

uh..... that would be how I specified it....
as I said, it made no difference....

---

### Post by kidders on 2007-08-28
> **Marat Galiev said:**
> use option in you xorg.conf
**Option "****VideoRAM xxx"**where xxx-you ram size in KB.I think dreadlord_chris said that doesn't work. :confused:

Perhaps this is a known issue with your card or driver ... or maybe even Xorg itself. Have you taken a look through the relevant bug databases?

---

### Post by Marat Galiev on 2007-08-28
sorry:)
install the newest driver version.
and that driver you use now?

---

### Post by dreadlord_chris on 2007-08-28
Using the latest driver:
```

(II) NVIDIA GLX Module  100.14.11  Wed Jun 13 18:58:58 PDT 2007

```
it was the same with the 9755 driver as well....

Tried finding similiar bugs listed for either Xorg or the driver - unsucessfully....

and btw Marat Galiev.... the setting to specify video RAM is (in the Device section):

_VideoRam xxx_

not

_Option   "VideoRAM xxx"_

---

### Post by kidders on 2007-08-28
Weird :(

I don't know if this'll get us anywhere, but could you post your xorg.conf and Xorg system log ... just in case.

---

### Post by dreadlord_chris on 2007-08-28
> **kidders said:**
> Weird :(

I don't know if this'll get us anywhere, but could you post your xorg.conf and Xorg system log ... just in case.

sure.... no prob....
xorg.conf:
[php]
Section "Module"
    Load           "bitmap"
    SubSection     "extmod"
	Option	   "omit DPMS"
    EndSubSection
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
EndSection

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"nVidia Corporation G72 [GeForce 7300 LE]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	VideoRam	131072
	Option 		"TripleBuffer" "true"
	Option 		"backingstore" "True"
	Option 		"RenderAccel" "True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G72 [GeForce 7300 LE]"
	Monitor		"Generic Monitor"
	Option 		"AddARGBGLXVisuals" "True"
	Option 		"AllowGLXWithComposite" "true"
	Option          "DisableGLXRootClipping" "true"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1024x768" "800x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	Option 	  	"BlankTime" "0"
	Option	   	"StandbyTime" "0"
	Option 	   	"SuspendTime" "0"
	Option	   	"OffTime" "0"
	Option 	   	"NoPM" "true"
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
    Option 	   "RENDER" "true"
    Option 	   "DAMAGE" "true"
EndSection
[/php]

Xorg.0.log
```


X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu2)
Current Operating System: Linux HAL421 2.6.22-10-generic #1 SMP Wed Aug 22 08:11:52 GMT 2007 i686
Build Date: 26 August 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Aug 28 09:50:07 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "nVidia Corporation G72 [GeForce 7300 LE]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) Option "BlankTime" "0"
(**) Option "StandbyTime" "0"
(**) Option "SuspendTime" "0"
(**) Option "OffTime" "0"
(**) Option "NoPM" "true"
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Extension "Composite" is enabled
(**) Extension "RENDER" is enabled
(**) Extension "DAMAGE" is enabled
(II) Loader magic: 0x81e8500
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.2
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1002,5a33 card 103c,2a47 rev 01 class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 1002,5a34 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:13:0: chip 1002,4374 card 103c,2a47 rev 80 class 0c,03,10 hdr 80
(II) PCI: 00:13:1: chip 1002,4375 card 103c,2a47 rev 80 class 0c,03,10 hdr 00
(II) PCI: 00:13:2: chip 1002,4373 card 103c,2a47 rev 80 class 0c,03,20 hdr 00
(II) PCI: 00:14:0: chip 1002,4372 card 103c,2a47 rev 81 class 0c,05,00 hdr 80
(II) PCI: 00:14:1: chip 1002,4376 card 103c,2a47 rev 80 class 01,01,8a hdr 00
(II) PCI: 00:14:2: chip 1002,437b card 103c,2a47 rev 01 class 04,03,00 hdr 00
(II) PCI: 00:14:3: chip 1002,4377 card 0000,0000 rev 80 class 06,01,00 hdr 80
(II) PCI: 00:14:4: chip 1002,4371 card 0000,0000 rev 80 class 06,04,01 hdr 81
(II) PCI: 01:00:0: chip 10de,01d1 card 19f1,20f6 rev a1 class 03,00,00 hdr 00
(II) PCI: 02:02:0: chip 14f1,2f20 card 14f1,200c rev 00 class 07,80,00 hdr 00
(II) PCI: 02:05:0: chip 10ec,8139 card 103c,2a47 rev 10 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:2:0), (0,1,1), BCTRL: 0x000b (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfc000000 - 0xfeafffff (0x2b00000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:20:3), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:20:4), (0,2,2), BCTRL: 0x0007 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[1] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[2] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[3] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfeb00000 - 0xfebfffff (0x100000) MX[B]
(--) PCI:*(1:0:0) nVidia Corporation GeForce 7300 LE rev 161, Mem @ 0xfd000000/24, 0xd0000000/28, 0xfc000000/24, BIOS @ 0xfeae0000/17
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
(II) PCI Memory resource overlap reduced 0xe0000000 from 0xe0000000 to 0xdfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xfebefc00 - 0xfebefcff (0x100) MX[B]
	[1] -1	0	0xfebf0000 - 0xfebfffff (0x10000) MX[B]
	[2] -1	0	0xfbff8000 - 0xfbffbfff (0x4000) MX[B]
	[3] -1	0	0x50000000 - 0x500003ff (0x400) MX[B]
	[4] -1	0	0xfbffd000 - 0xfbffdfff (0x1000) MX[B]
	[5] -1	0	0xfbffe000 - 0xfbffefff (0x1000) MX[B]
	[6] -1	0	0xfbfff000 - 0xfbffffff (0x1000) MX[B]
	[7] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[8] -1	0	0xfeae0000 - 0xfeafffff (0x20000) MX[B](B)
	[9] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[12] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[13] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[14] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[15] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[16] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[17] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x00000b00 - 0x00000b0f (0x10) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfebefc00 - 0xfebefcff (0x100) MX[B]
	[1] -1	0	0xfebf0000 - 0xfebfffff (0x10000) MX[B]
	[2] -1	0	0xfbff8000 - 0xfbffbfff (0x4000) MX[B]
	[3] -1	0	0x50000000 - 0x500003ff (0x400) MX[B]
	[4] -1	0	0xfbffd000 - 0xfbffdfff (0x1000) MX[B]
	[5] -1	0	0xfbffe000 - 0xfbffefff (0x1000) MX[B]
	[6] -1	0	0xfbfff000 - 0xfbffffff (0x1000) MX[B]
	[7] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[8] -1	0	0xfeae0000 - 0xfeafffff (0x20000) MX[B](B)
	[9] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[12] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[13] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[14] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[15] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[16] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[17] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x00000b00 - 0x00000b0f (0x10) IX[B]
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
	[4] -1	0	0xfebefc00 - 0xfebefcff (0x100) MX[B]
	[5] -1	0	0xfebf0000 - 0xfebfffff (0x10000) MX[B]
	[6] -1	0	0xfbff8000 - 0xfbffbfff (0x4000) MX[B]
	[7] -1	0	0x50000000 - 0x500003ff (0x400) MX[B]
	[8] -1	0	0xfbffd000 - 0xfbffdfff (0x1000) MX[B]
	[9] -1	0	0xfbffe000 - 0xfbffefff (0x1000) MX[B]
	[10] -1	0	0xfbfff000 - 0xfbffffff (0x1000) MX[B]
	[11] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[12] -1	0	0xfeae0000 - 0xfeafffff (0x20000) MX[B](B)
	[13] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[14] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[19] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[20] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[21] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[22] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[23] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x00000b00 - 0x00000b0f (0x10) IX[B]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
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
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.3.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  100.14.11  Wed Jun 13 18:58:58 PDT 2007
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) NVIDIA dlloader X Driver  100.14.11  Wed Jun 13 18:23:34 PDT 2007
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="NVIDIA Corporation"
	compiled for 7.1.99.2, module version = 1.0.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfebefc00 - 0xfebefcff (0x100) MX[B]
	[5] -1	0	0xfebf0000 - 0xfebfffff (0x10000) MX[B]
	[6] -1	0	0xfbff8000 - 0xfbffbfff (0x4000) MX[B]
	[7] -1	0	0x50000000 - 0x500003ff (0x400) MX[B]
	[8] -1	0	0xfbffd000 - 0xfbffdfff (0x1000) MX[B]
	[9] -1	0	0xfbffe000 - 0xfbffefff (0x1000) MX[B]
	[10] -1	0	0xfbfff000 - 0xfbffffff (0x1000) MX[B]
	[11] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[12] -1	0	0xfeae0000 - 0xfeafffff (0x20000) MX[B](B)
	[13] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[14] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[19] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[20] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[21] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[22] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[23] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x00000b00 - 0x00000b0f (0x10) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfebefc00 - 0xfebefcff (0x100) MX[B]
	[5] -1	0	0xfebf0000 - 0xfebfffff (0x10000) MX[B]
	[6] -1	0	0xfbff8000 - 0xfbffbfff (0x4000) MX[B]
	[7] -1	0	0x50000000 - 0x500003ff (0x400) MX[B]
	[8] -1	0	0xfbffd000 - 0xfbffdfff (0x1000) MX[B]
	[9] -1	0	0xfbffe000 - 0xfbffefff (0x1000) MX[B]
	[10] -1	0	0xfbfff000 - 0xfbffffff (0x1000) MX[B]
	[11] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[12] -1	0	0xfeae0000 - 0xfeafffff (0x20000) MX[B](B)
	[13] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[14] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[22] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[23] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[24] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[25] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[26] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x00000b00 - 0x00000b0f (0x10) IX[B]
	[29] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[30] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "RenderAccel" "True"
(**) NVIDIA(0): Option "AllowGLXWithComposite" "true"
(**) NVIDIA(0): Option "TripleBuffer" "true"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Option "DisableGLXRootClipping" "true"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 7300 LE (G72) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 05.72.22.43.00
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7300 LE at PCI:1:0:0:
(--) NVIDIA(0):     HP vs15c (CRT-1)
(--) NVIDIA(0): HP vs15c (CRT-1): 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-1
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
(--) NVIDIA(0): DPI set to (86, 88); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(**) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B]
	[1] 0	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
	[2] 0	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xfebefc00 - 0xfebefcff (0x100) MX[B]
	[8] -1	0	0xfebf0000 - 0xfebfffff (0x10000) MX[B]
	[9] -1	0	0xfbff8000 - 0xfbffbfff (0x4000) MX[B]
	[10] -1	0	0x50000000 - 0x500003ff (0x400) MX[B]
	[11] -1	0	0xfbffd000 - 0xfbffdfff (0x1000) MX[B]
	[12] -1	0	0xfbffe000 - 0xfbffefff (0x1000) MX[B]
	[13] -1	0	0xfbfff000 - 0xfbffffff (0x1000) MX[B]
	[14] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[15] -1	0	0xfeae0000 - 0xfeafffff (0x20000) MX[B](B)
	[16] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[17] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[18] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[19] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[20] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[21] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[24] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[25] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[26] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[27] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[28] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[29] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x00000b00 - 0x00000b0f (0x10) IX[B]
	[32] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[33] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "1024x768"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(**) NVIDIA(0): Option "BackingStore" "True"
(**) NVIDIA(0): Backing store enabled
(==) NVIDIA(0): Silken mouse enabled
(II) Loading extension NV-CONTROL
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
(II) Initializing extension GLX
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded

```

---

### Post by kidders on 2007-08-28
Thanks for those. I forgot how much I hate chasing Xorg problems lol!

I'm still going over your last post, but in the meantime, I notice that at least *some* cards in the 7300 range can share RAM. Your BIOS isn't by any chance configured to hand some of your memory over to graphics adapters, is it?

---

### Post by dreadlord_chris on 2007-08-28
nah.... I have the BIOS set to no dedicated/shared RAM

I know what ya mean about those Xorg probs... it's mostly why I've let this one go for so long - everything *pretty much* works like it's supposed to....

the only graphics realated issues I have are when running Compiz Fusion - everthing there also usually works fine. When it does fail though, either everything completely locks (requiring a hard reboot) or Xserver resets - but I never get any errors logged.
I've suspected this might be due to the system seeing 4x the actual GPU RAM

---

### Post by kidders on 2007-08-29
That's the thing that confuses me. :-( You see, 128MB of Video RAM isn't *that* much ... in that something like compiz should have no difficulty consuming all of it pretty quickly. I would expect RAM-intensive activity (eg compiz + firefox) to crash your computer within 15 mins or so, if indeed Xorg is "imagining" the extra memory.

Having said that, I'm no hardware expert, so I could well be wrong about that. From a software perspective...
[LIST]
[*]Your xorg.conf is lovely and clean, and really should work very nicely.
[*]Xorg itself seems to have nothing to complain about ... not even one log line starts with "(WW)".
[*]I haven't been able to connect anything about your configuration with known issues with your graphics drivers.[/LIST]It's possible however that setting "RenderAccel" to true could be causing your lockups. The option is becoming more and more stable on nvidia cards all the time, but afaik, can still occasionally cause problems.

Anyhow, sorry I haven't been much help. I've asked for assistance from a forum team I'm a member of, just in case someone there recognises your problem.

---

### Post by dreadlord_chris on 2007-08-29
Hey thanks! I appreciate the effort!
Actually, I have very little problems with Firefox - it's Opera that causes more problems for me (with Compiz)....
I'm gonna test w/out the RenderAccel option, see if it makes any diff...

---

### Post by kidders on 2007-08-29
Hey again,

I've done some consultation with my team and, although there are a few more obscure possibilities, the consensus seems to be that xorg must surely be using some of your system's RAM to supplement what's available on your GPU. Having said that, I'm having a little difficulty accepting it as a reasonable possibility, since both your xorg.conf *and* your BIOS configuration would have to be being ignored.

The issue is, you see, that if the extra RAM being reported by xorg didn't exist *somewhere*, your computer would crash very, very frequently ... and may not even make it out of the boot-up process. I get the impression though that the crashing you're experiencing is more of an "irritation" than something that's stopping you making productive use of your box.

May I ask what motherboard you have?

---

### Post by dreadlord_chris on 2007-08-29
> **kidders said:**
> Hey again,

I've done some consultation with my team and, although there are a few more obscure possibilities, the consensus seems to be that xorg must surely be using some of your system's RAM to supplement what's available on your GPU. Having said that, I'm having a little difficulty accepting it as a reasonable possibility, since both your xorg.conf *and* your BIOS configuration would have to be being ignored.

The issue is, you see, that if the extra RAM being reported by xorg didn't exist *somewhere*, your computer would crash very, very frequently ... and may not even make it out of the boot-up process. I get the impression though that the crashing you're experiencing is more of an "irritation" than something that's stopping you making productive use of your box.

May I ask what motherboard you have?

Yes, the crashes are more irritants then anything else....

Mobo: ECS RC410-M (Alhena)
This would be the system:
[HP Pavillion a1410y]("http://h10025.www1.hp.com/ewfrf/wc/prodinfoCategory?lc=en&cc=us&dlc=en&product=3254035&lang=en")
I added the NVIDIA card - otherwise it's pretty much stock...

---

### Post by kidders on 2007-08-29
Ahh... I see.

I don't suppose it's surprising that an Nvidia GPU misbehaves when paired with an ATI chipset. :-(

Is your Xorg still crashing?

---

### Post by dreadlord_chris on 2007-08-30
> **kidders said:**
> Ahh... I see.

I don't suppose it's surprising that an Nvidia GPU misbehaves when paired with an ATI chipset. :-(

Is your Xorg still crashing?
not today...
so far...
but I have been away from it for a lot of the day....


LOL... actually hadn't even considered the ATI/NVIDIA mashup I got going on.... Damn the monkeys!
been kinda kicking about the idea of upgrading the mobo/cpu...
but still....

---

### Post by kidders on 2007-08-30
Yeah... unfortunately, you can't often plug just anything into a motherboard and expect it to work flawlessly. :(

In the event you still encounter crashes, you could also try a couple of other things...
[LIST]
[*]Since you mentioned Opera, your crashes *could* be connected to flash plugin instability.
[*]Aside from the RenderAccel configuration option, other possible candidates for provoking odd behaviour are blitting & video texture related settings.[/LIST]

---

### Post by ddrichardson on 2007-09-05
Further to kidders last post - the 7 series cards all support Turbocache where the card can dynamically allocate system RAM as needed. I would suggest that this wont be governed by BIOS. There's a bit more on it [here ]("http://www.nvidia.com/page/turbocache.html")(mostly marketeer speak sorry).

If this is being controlled in hardware it would explain the lack of crashes, but I'd be more inclined to accept it if Xorg reported different amounts of memory every time it tried to probe.

There was someone posting with a similar problem last month but for the life of me I can't find the post.

---

### Post by dreadlord_chris on 2007-09-07
hmm... Turbocache huh... I'll have to do a bit a research on that bugger...
For what it's worth Xorg always reports the same amount of RAM...

---

### Post by kidders on 2007-09-07
That didn't seem quite right to me either. As far as I'm aware (ddrichardson may know more about this), altering the Video RAM figure in xorg.conf, for a card that supports hijacking system memory, normally just alters the amount it uses. So, you *should* be able to make xorg report different video RAM amounts simply by tinkering with the number. In your case though, I suspect your hardware isn't talking to itself properly, and your graphics card is just doing its own thing.

---

### Post by ddrichardson on 2007-09-08
I've just been looking through [nV News]("http://www.nvnews.net/") and it seems there are a lot of problems with the TurboCache cards and recent 7 series cards in general. The standard suggestion is upgrade driver, upgrade kernel. However I wouldn't guarantee this will help as many people are still seeing errors.

---

### Post by dreadlord_chris on 2007-09-09
> **ddrichardson said:**
> I've just been looking through [nV News]("http://www.nvnews.net/") and it seems there are a lot of problems with the TurboCache cards and recent 7 series cards in general. The standard suggestion is upgrade driver, upgrade kernel. However I wouldn't guarantee this will help as many people are still seeing errors.

As far as I can tell my card does not use TurboCache. From reading NVIDIA's site it *seems* to be just the 7 series **Go** cards that use it - and mines just a 7300 LE....

and I'm using the latest driver & kernel

---

### Post by twelve17 on 2007-11-05
I have a GeForce 8400 video card.  The box says it "supports" 512MB of ram but supposedly only has 256MB on it.  Xorg seems to report the 512MB value.  Like the OP, Xorg ignores my attempts to override it.

Does anyone know if it's possible to override it at the kernel module level?

Alex

---

