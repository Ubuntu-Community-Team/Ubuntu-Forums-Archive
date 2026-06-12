---
title: "Two ATI cards, X-Org radeon driver, dual-head with Xinerama =&gt; OpenGL doesn't work"
date: 2009-03-12
forum: Hardware
---

### Post by herr_tichy on 2009-03-12
Hello Forum,

[after my 8800 GTX debacle,]("http://ubuntuforums.org/showthread.php?t=1090457") I've switched to two el cheapo ATI cards from the hardware box in the futile hope, that they would work better.

Well, they don't, but at least they do not work for 12EUR while the 8800GTX didn't work for 120EUR which is sort of at least an economic improvement ;)

```
02:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
02:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]
03:00.0 VGA compatible controller: ATI Technologies Inc RV505 CE [Radeon X1550 64-bit]
03:00.1 Display controller: ATI Technologies Inc Device 717f

```

These are the cards.

```
Section "Monitor"
    Identifier  "monitor1"
#    VendorName  "Unknown"
#    ModelName   "Unknown"
#    HorizSync   30-96
#    VertRefresh 48-120
EndSection

Section "Monitor"
    Identifier  "monitor2"
#    VendorName  "Unknown"
#    ModelName   "Unknown"
#    HorizSync   30-96
#    VertRefresh 48-120
EndSection

Section "Screen"
    Identifier "links"
    Device      "ati2"
    Monitor     "monitor2"
    DefaultColorDepth 24
    Subsection "Display"
      Depth       24
      Modes       "1024x768" "800x600" "640x480"
      ViewPort    0 0
      Virtual 1024 768
    EndSubsection
EndSection

Section "Screen"
    Identifier "rechts"
    Device      "ati1"
    Monitor     "monitor1"
    DefaultColorDepth 24
    Subsection "Display"
      Depth       24
      Modes       "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
      ViewPort    0 0
    EndSubsection
EndSection

Section "ServerLayout"
    Identifier "layout1"
    Screen     "links"
    Screen     "rechts" RightOf "links"
    Option     "Xinerama" "on"
#InputDevice "Mouse1" "CorePointer"
#    InputDevice "Keyboard1" "CoreKeyboard"
EndSection


#Section "Screen"
#	Identifier	"Default Screen"
#	Monitor		"Configured Monitor"
#	Device		"Configured Video Device"
#	DefaultDepth	24
#	SubSection "Display"
#		Virtual	2624 1200
#	EndSubSection
#EndSection

Section "Device"
	Identifier	"ati1"
	Driver	"radeon"
	BusID "PCI:3:0:0"
EndSection

Section "Device"
        Identifier      "ati2"
        Driver  "radeon"
        BusID "PCI:2:0:0"
EndSection

Section "DRI"
        Mode 0666
EndSection
        
Section "Extensions"
        Option "Composite" "Enable"
EndSection

```

That's my xorg.conf

```
cat /var/log/Xorg.0.log

X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-16-server x86_64 Ubuntu
Current Operating System: Linux dreiraumrakete 2.6.28.7-custom #1 SMP Mon Mar 9 17:32:50 CET 2009 x86_64
Build Date: 24 October 2008  09:06:49AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@crested.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Mar 12 15:27:16 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "layout1"
(**) |-->Screen "links" (0)
(**) |   |-->Monitor "monitor2"
(**) |   |-->Device "ati2"
(**) |-->Screen "rechts" (1)
(**) |   |-->Monitor "monitor1"
(**) |   |-->Device "ati1"
(**) Option "Xinerama" "on"
(==) Automatically adding devices
(==) Automatically enabling devices
(**) Xinerama: enabled
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
(**) Extension "Composite" is enabled
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x7b7320
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 4.1
	X.Org XInput driver : 2.1
	X.Org Server Extension : 1.1
	X.Org Font Renderer : 0.6
(II) Loader running on linux
(++) using VT number 7

(!!) More than one possible primary device found
(--) PCI: (0@2:0:0) ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)] rev 0, Mem @ 0xcc000000/67108864, 0xfeaf0000/65536, I/O @ 0x0000c000/256, BIOS @ 0x????????/131072
(--) PCI: (0@2:0:1) ATI Technologies Inc RV370 [Radeon X300SE] rev 0, Mem @ 0xfeae0000/65536
(--) PCI: (0@3:0:0) ATI Technologies Inc RV505 CE [Radeon X1550 64-bit] rev 0, Mem @ 0xd0000000/268435456, 0xfebf0000/65536, I/O @ 0x0000d000/256, BIOS @ 0x????????/131072
(--) PCI: (0@3:0:1) ATI Technologies Inc unknown chipset (0x717f) rev 0, Mem @ 0xfebe0000/65536
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
	[20] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[21] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[22] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[23] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[24] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[25] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[26] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[27] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[28] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[29] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[30] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[31] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[32] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[33] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[34] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[35] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
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

(WW) Warning, couldn't open module glx
(II) UnloadModule: "glx"
(EE) Failed to load module "glx" (module does not exist, 0)
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
(II) LoadModule: "radeon"

(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 6.9.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) RADEON: Driver for ATI Radeon chipsets:
	ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
	ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
	ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
	ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
	ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
	ATI Radeon 8500 AIW BB (AGP), ATI Radeon 8500 AIW BC (AGP),
	ATI Radeon IGP320M (U1) 4336, ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
	ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9800PRO NH (AGP),
	ATI Radeon 9800 NI (AGP), ATI FireGL X2 NK (AGP),
	ATI Radeon 9800XT NJ (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
	ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
	ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
	ATI FireGL unknown (R423) UR (PCIE),
	ATI FireGL unknown (R423) UT (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835,
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE),
	ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE),
	ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
	ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
	ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
	ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
	ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
	ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
	ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
	ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
	ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
	ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
	ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
	ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
	ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
	ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
	ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
	ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
	ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
	ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
	ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
	ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
	ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
	ATI Mobility Radeon X1700, ATI Radeon X2300HD,
	ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
	ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
	ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
	ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI ATI FireGL V7400,
	ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
	ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
	ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
	ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
	ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
	ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
	ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
	ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
	ATI Radeon 4800 Series, ATI RV610, ATI Radeon HD 2400 XT,
	ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
	ATI RV610, ATI ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
	ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610, ATI RV670,
	ATI Radeon HD3870, ATI Radeon HD3850, ATI RV670,
	ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850, ATI RV630,
	ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
	ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
	ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
	ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
	ATI FireGL V3600, ATI Radeon HD 2600 LE, ATI Radeon HD 3470,
	ATI Radeon HD 3450, ATI Radeon HD 3430, ATI Mobility Radeon HD 3430,
	ATI Mobility Radeon HD 3400 Series, ATI FireMV 2450, ATI FireMV 2260,
	ATI FireMV 2260, ATI ATI Radeon HD 3600 Series,
	ATI ATI Radeon HD 3650 AGP, ATI ATI Radeon HD 3600 PRO,
	ATI ATI Radeon HD 3600 XT, ATI ATI Radeon HD 3600 PRO,
	ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics
(II) Primary Device is: 
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
	[20] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[21] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[22] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[23] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[24] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[25] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[26] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[27] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[28] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[29] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[30] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[31] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[32] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[33] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[34] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[35] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
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
	[20] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[21] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[22] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[23] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[24] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[25] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[26] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[27] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[28] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[29] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[30] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[31] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[32] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[33] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[34] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[35] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
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
	[20] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[21] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[22] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[23] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[24] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[25] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[26] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[27] 1	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[28] 1	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[29] 1	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[30] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[31] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[32] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[33] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[34] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[35] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[36] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[37] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[38] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[39] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[40] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[41] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[42] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[43] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
	[44] 1	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[45] 1	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Setting vga for screen 1.
(II) RADEON(0): MMIO registers at 0x00000000feaf0000: size 64KB
(II) RADEON(0): PCI bus 2 card 0 func 0
(**) RADEON(0): Depth 24, (--) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"

(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 4.1
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(--) RADEON(0): Chipset: "ATI Radeon X300 (RV370) 5B60 (PCIE)" (ChipID = 0x5b60)
(--) RADEON(0): Linear framebuffer at 0x00000000cc000000
(II) RADEON(0): PCIE card detected
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 4.1
(II) RADEON(0): initializing int10
(WW) RADEON(0): Restoring MPP_TB_CONFIG<31:24> (04), setting to 01
(II) RADEON(0): Legacy BIOS detected
(II) RADEON(0): Generation 2 PCI interface, using max accessible memory
(II) RADEON(0): Detected total video RAM=65536K, accessible=65536K (PCI BAR=65536K)
(--) RADEON(0): Mapped VideoRAM: 65536 kByte (64 bit DDR SDRAM)
(II) RADEON(0): Color tiling enabled by default
(II) RADEON(0): Max desktop size set to 1024x768
(II) RADEON(0): For a larger or smaller max desktop size, add a Virtual line to your xorg.conf
(II) RADEON(0): If you are having trouble with 3D, reduce the desktop size by adjusting the Virtual line to your xorg.conf
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) RADEON(0): ref_freq: 2700, min_out_pll: 20000, max_out_pll: 40000, min_in_pll: 40, max_in_pll: 3000, xclk: 19600, sclk: 196.000000, mclk: 324.000000
(II) RADEON(0): PLL parameters: rf=2700 rd=12 min=20000 max=40000; xclk=19600
(II) RADEON(0): Bios Connector table: 
(II) RADEON(0): Port0: DDCType-0x60, DACType-1, TMDSType-1, ConnectorType-2
(II) RADEON(0): Port5: DDCType-0x0, DACType-2, TMDSType-0, ConnectorType-5
(II) RADEON(0): Output DVI-0 using monitor section monitor2
(II) RADEON(0): DFP table revision: 4
(II) RADEON(0): I2C bus "DVI-0" initialized.
(II) RADEON(0): Output S-video has no monitor section
(II) RADEON(0): Default TV standard: NTSC
(II) RADEON(0): TV standards supported by chip: NTSC PAL 
(II) RADEON(0): Port0:
 Monitor   -- AUTO
 Connector -- DVI-I
 DAC Type  -- Primary
 TMDS Type -- Internal
 DDC Type  -- 0x60
(II) RADEON(0): Port1:
 Monitor   -- AUTO
 Connector -- STV
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- None
 DDC Type  -- 0x0
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): EDID vendor "FUS", prod id 640
(II) RADEON(0): Using EDID range info for horizontal sync
(II) RADEON(0): Using EDID range info for vertical refresh
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   64.11  1024 1080 1184 1344  768 769 772 795 -hsync +vsync (47.7 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   81.80  1024 1080 1192 1360  768 769 772 802 -hsync +vsync (60.2 kHz)
(II) RADEON(0): Modeline "800x600"x60.0   38.22  800 832 912 1024  600 601 604 622 -hsync +vsync (37.3 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   48.91  800 840 920 1040  600 601 604 627 -hsync +vsync (47.0 kHz)
(II) RADEON(0): Modeline "640x480"x60.0   23.86  640 656 720 800  480 481 484 497 -hsync +vsync (29.8 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   30.72  640 664 728 816  480 481 484 502 -hsync +vsync (37.7 kHz)
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: FUS  Model: 280  Serial#: 72287
(II) RADEON(0): Year: 2002  Week: 20
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.30
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.621 redY: 0.343   greenX: 0.298 greenY: 0.584
(II) RADEON(0): blueX: 0.146 blueY: 0.109   whiteX: 0.304 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1024  vsize 768  refresh: 60  vid: 16481
(II) RADEON(0): #1: hsize: 1024  vsize 768  refresh: 75  vid: 20321
(II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 60  vid: 16453
(II) RADEON(0): #3: hsize: 800  vsize 600  refresh: 75  vid: 20293
(II) RADEON(0): #4: hsize: 640  vsize 480  refresh: 60  vid: 16433
(II) RADEON(0): #5: hsize: 640  vsize 480  refresh: 75  vid: 20273
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  304 x 228 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No: YEUN072287
(II) RADEON(0): Ranges: V min: 55 V max: 75 Hz, H min: 30 H max: 61 kHz, PixClock max 80 MHz
(II) RADEON(0): Monitor name: 3815 FA
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff001ab380025f1a0100
(II) RADEON(0): 	140c0103681e1782ea364d9f574c9525
(II) RADEON(0): 	1c4d54af4e006140614f4540454f3140
(II) RADEON(0): 	314f0101010164190040410026301888
(II) RADEON(0): 	360030e410000018000000ff00594555
(II) RADEON(0): 	4e3037323238370a2020000000fd0037
(II) RADEON(0): 	4b1e3d08000a202020202020000000fc
(II) RADEON(0): 	00333831352046410a20202020200084
finished output detect: 0
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
finished output detect: 1
finished all detect
before xf86InitialConfiguration
(II) RADEON(0): EDID vendor "FUS", prod id 640
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   64.11  1024 1080 1184 1344  768 769 772 795 -hsync +vsync (47.7 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   81.80  1024 1080 1192 1360  768 769 772 802 -hsync +vsync (60.2 kHz)
(II) RADEON(0): Modeline "800x600"x60.0   38.22  800 832 912 1024  600 601 604 622 -hsync +vsync (37.3 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   48.91  800 840 920 1040  600 601 604 627 -hsync +vsync (47.0 kHz)
(II) RADEON(0): Modeline "640x480"x60.0   23.86  640 656 720 800  480 481 484 497 -hsync +vsync (29.8 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   30.72  640 664 728 816  480 481 484 502 -hsync +vsync (37.7 kHz)
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: FUS  Model: 280  Serial#: 72287
(II) RADEON(0): Year: 2002  Week: 20
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.30
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.621 redY: 0.343   greenX: 0.298 greenY: 0.584
(II) RADEON(0): blueX: 0.146 blueY: 0.109   whiteX: 0.304 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1024  vsize 768  refresh: 60  vid: 16481
(II) RADEON(0): #1: hsize: 1024  vsize 768  refresh: 75  vid: 20321
(II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 60  vid: 16453
(II) RADEON(0): #3: hsize: 800  vsize 600  refresh: 75  vid: 20293
(II) RADEON(0): #4: hsize: 640  vsize 480  refresh: 60  vid: 16433
(II) RADEON(0): #5: hsize: 640  vsize 480  refresh: 75  vid: 20273
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  304 x 228 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No: YEUN072287
(II) RADEON(0): Ranges: V min: 55 V max: 75 Hz, H min: 30 H max: 61 kHz, PixClock max 80 MHz
(II) RADEON(0): Monitor name: 3815 FA
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff001ab380025f1a0100
(II) RADEON(0): 	140c0103681e1782ea364d9f574c9525
(II) RADEON(0): 	1c4d54af4e006140614f4540454f3140
(II) RADEON(0): 	314f0101010164190040410026301888
(II) RADEON(0): 	360030e410000018000000ff00594555
(II) RADEON(0): 	4e3037323238370a2020000000fd0037
(II) RADEON(0): 	4b1e3d08000a202020202020000000fc
(II) RADEON(0): 	00333831352046410a20202020200084
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "FUS", prod id 640
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): Output DVI-0 connected
(II) RADEON(0): Output S-video disconnected
(II) RADEON(0): Using user preference for initial modes
(II) RADEON(0): Output DVI-0 using initial mode 1024x768
after xf86InitialConfiguration
(**) RADEON(0): Display dimensions: (300, 230) mm
(**) RADEON(0): DPI set to (86, 84)
(II) Loading sub module "fb"
(II) LoadModule: "fb"

(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(==) RADEON(0): Using XAA acceleration architecture
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"

(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.2.0
	ABI class: X.Org Video Driver, version 4.1
(==) RADEON(0): Assuming overlay scaler buffer width is 1536
(II) RADEON(0): No MM_TABLE found - assuming CARD is not TV-in capable.
(!!) RADEON(0): For information on using the multimedia capabilities
	of this adapter, please see http://gatos.sf.net.
(!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
(II) RADEON(1): MMIO registers at 0x00000000febf0000: size 64KB
(II) RADEON(1): PCI bus 3 card 0 func 0
(**) RADEON(1): Depth 24, (--) framebuffer bpp 32
(II) RADEON(1): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(1): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"

(II) Reloading /usr/lib/xorg/modules//libvgahw.so
(II) RADEON(1): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(1): RGB weight 888
(II) RADEON(1): Using 8 bits per RGB (8 bit DAC)
(--) RADEON(1): Chipset: "ATI Radeon X1550 64-bit" (ChipID = 0x715f)
(WW) RADEON(1): R500 support is under development. Please report any issues to xorg-driver-ati@lists.x.org
(--) RADEON(1): Linear framebuffer at 0x00000000d0000000
(II) RADEON(1): PCIE card detected
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) RADEON(1): initializing int10
(II) RADEON(1): ATOM BIOS detected
(II) RADEON(1): ATOM BIOS Rom: 
	SubsystemVendorID: 0x1462 SubsystemID: 0x0680
	IOBaseAddress: 0xd000
	Filename: SR24079.bin 
	BIOS Bootup Message: 
113-MSV068 RV505CE DDR2 BIOS 350e/400m Channel A                        
    
(II) RADEON(1): Framebuffer space used by Firmware (kb): 20
(II) RADEON(1): Start of VRAM area used by Firmware: 0x7ffb000
(II) RADEON(1): AtomBIOS requests 20kB of VRAM scratch space
(II) RADEON(1): AtomBIOS VRAM scratch base: 0x7ffb000
(II) RADEON(1): Cannot get VRAM scratch space. Allocating in main memory instead
(II) RADEON(1): Default Engine Clock: 350000
(II) RADEON(1): Default Memory Clock: 400000
(II) RADEON(1): Maximum Pixel ClockPLL Frequency Output: 1100000
(II) RADEON(1): Minimum Pixel ClockPLL Frequency Output: 0
(II) RADEON(1): Maximum Pixel ClockPLL Frequency Input: 13500
(II) RADEON(1): Minimum Pixel ClockPLL Frequency Input: 1000
(II) RADEON(1): Maximum Pixel Clock: 400000
(II) RADEON(1): Reference Clock: 27000
(II) RADEON(1): Generation 2 PCI interface, using max accessible memory
(II) RADEON(1): Detected total video RAM=131072K, accessible=262144K (PCI BAR=262144K)
(--) RADEON(1): Mapped VideoRAM: 131072 kByte (64 bit DDR SDRAM)
(II) RADEON(1): Color tiling enabled by default
(II) RADEON(1): Max desktop size set to 2560x1600
(II) RADEON(1): For a larger or smaller max desktop size, add a Virtual line to your xorg.conf
(II) RADEON(1): If you are having trouble with 3D, reduce the desktop size by adjusting the Virtual line to your xorg.conf
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) RADEON(1): ref_freq: 2700, min_out_pll: 64800, max_out_pll: 110000, min_in_pll: 100, max_in_pll: 1350, xclk: 40000, sclk: 350.000000, mclk: 400.000000
(II) RADEON(1): PLL parameters: rf=2700 rd=13 min=64800 max=110000; xclk=40000
(II) RADEON(1): Skipping TV-Out
(II) RADEON(1): Skipping Component Video
(II) RADEON(1): Bios Connector table: 
(II) RADEON(1): Port3: DDCType-0x7e40, DACType-1, TMDSType-1, ConnectorType-2, hpd_mask-0x1
(II) RADEON(1): Output DVI-0 using monitor section monitor1
(II) RADEON(1): TMDS PLL from BIOS: 16500 e0118
(II) RADEON(1): I2C bus "DVI-0" initialized.
(II) RADEON(1): Port0:
 Monitor   -- AUTO
 Connector -- DVI-I
 DAC Type  -- Primary
 TMDS Type -- Internal
 DDC Type  -- 0x7e40
(II) RADEON(1): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(1): EDID vendor "SAM", prod id 145
(II) RADEON(1): Using EDID range info for horizontal sync
(II) RADEON(1): Using EDID range info for vertical refresh
(II) RADEON(1): Printing DDC gathered Modelines:
(II) RADEON(1): Modeline "1600x1200"x0.0  130.37  1600 1648 1680 1760  1200 1202 1206 1235 +hsync -vsync (74.1 kHz)
(II) RADEON(1): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(1): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(1): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(1): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) RADEON(1): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(1): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(1): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(1): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(1): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(1): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(1): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(1): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(1): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(1): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(1): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(1): Modeline "1600x1200"x60.0  160.96  1600 1704 1880 2160  1200 1201 1204 1242 -hsync +vsync (74.5 kHz)
(II) RADEON(1): Modeline "1280x1024"x60.0  108.88  1280 1360 1496 1712  1024 1025 1028 1060 -hsync +vsync (63.6 kHz)
(II) RADEON(1): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(1): Panel infos found from DDC detailed: 1600x1200
(II) RADEON(1): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(1): Manufacturer: SAM  Model: 91  Serial#: 1312961073
(II) RADEON(1): Year: 2005  Week: 14
(II) RADEON(1): EDID Version: 1.3
(II) RADEON(1): Digital Display Input
(II) RADEON(1): Max Image Size [cm]: horiz.: 43  vert.: 32
(II) RADEON(1): Gamma: 2.60
(II) RADEON(1): DPMS capabilities: Off
(II) RADEON(1): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(1): First detailed timing is preferred mode
(II) RADEON(1): redX: 0.632 redY: 0.353   greenX: 0.293 greenY: 0.590
(II) RADEON(1): blueX: 0.140 blueY: 0.090   whiteX: 0.310 whiteY: 0.340
(II) RADEON(1): Supported VESA Video Modes:
(II) RADEON(1): 720x400@70Hz
(II) RADEON(1): 640x480@60Hz
(II) RADEON(1): 640x480@67Hz
(II) RADEON(1): 640x480@72Hz
(II) RADEON(1): 640x480@75Hz
(II) RADEON(1): 800x600@56Hz
(II) RADEON(1): 800x600@60Hz
(II) RADEON(1): 800x600@72Hz
(II) RADEON(1): 800x600@75Hz
(II) RADEON(1): 832x624@75Hz
(II) RADEON(1): 1024x768@60Hz
(II) RADEON(1): 1024x768@70Hz
(II) RADEON(1): 1024x768@75Hz
(II) RADEON(1): 1280x1024@75Hz
(II) RADEON(1): 1152x870@75Hz
(II) RADEON(1): Manufacturer's mask: 0
(II) RADEON(1): Supported Future Video Modes:
(II) RADEON(1): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEON(1): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(1): Supported additional Video Mode:
(II) RADEON(1): clock: 130.4 MHz   Image Size:  432 x 324 mm
(II) RADEON(1): h_active: 1600  h_sync: 1648  h_sync_end 1680 h_blank_end 1760 h_border: 0
(II) RADEON(1): v_active: 1200  v_sync: 1202  v_sync_end 1206 v_blanking: 1235 v_border: 0
(II) RADEON(1): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 81 kHz, PixClock max 140 MHz
(II) RADEON(1): Monitor name: SyncMaster
(II) RADEON(1): Serial No: HSDY400867
(II) RADEON(1): EDID (in hex):
(II) RADEON(1): 	00ffffffffffff004c2d91003132424e
(II) RADEON(1): 	0e0f0103802b20a02ad0c4a15a4b9723
(II) RADEON(1): 	174f57bfef80a9408180010101010101
(II) RADEON(1): 	010101010101ed3240a060b023403020
(II) RADEON(1): 	2400b0441100001a000000fd00384b1e
(II) RADEON(1): 	510e000a202020202020000000fc0053
(II) RADEON(1): 	796e634d61737465720a2020000000ff
(II) RADEON(1): 	00485344593430303836370a20200009
finished output detect: 0
finished all detect
before xf86InitialConfiguration
(II) RADEON(1): EDID vendor "SAM", prod id 145
(II) RADEON(1): Using hsync ranges from config file
(II) RADEON(1): Using vrefresh ranges from config file
(II) RADEON(1): Printing DDC gathered Modelines:
(II) RADEON(1): Modeline "1600x1200"x0.0  130.37  1600 1648 1680 1760  1200 1202 1206 1235 +hsync -vsync (74.1 kHz)
(II) RADEON(1): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(1): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(1): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(1): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) RADEON(1): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(1): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(1): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(1): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(1): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(1): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(1): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(1): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(1): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(1): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(1): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(1): Modeline "1600x1200"x60.0  160.96  1600 1704 1880 2160  1200 1201 1204 1242 -hsync +vsync (74.5 kHz)
(II) RADEON(1): Modeline "1280x1024"x60.0  108.88  1280 1360 1496 1712  1024 1025 1028 1060 -hsync +vsync (63.6 kHz)
(II) RADEON(1): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(1): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(1): Manufacturer: SAM  Model: 91  Serial#: 1312961073
(II) RADEON(1): Year: 2005  Week: 14
(II) RADEON(1): EDID Version: 1.3
(II) RADEON(1): Digital Display Input
(II) RADEON(1): Max Image Size [cm]: horiz.: 43  vert.: 32
(II) RADEON(1): Gamma: 2.60
(II) RADEON(1): DPMS capabilities: Off
(II) RADEON(1): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(1): First detailed timing is preferred mode
(II) RADEON(1): redX: 0.632 redY: 0.353   greenX: 0.293 greenY: 0.590
(II) RADEON(1): blueX: 0.140 blueY: 0.090   whiteX: 0.310 whiteY: 0.340
(II) RADEON(1): Supported VESA Video Modes:
(II) RADEON(1): 720x400@70Hz
(II) RADEON(1): 640x480@60Hz
(II) RADEON(1): 640x480@67Hz
(II) RADEON(1): 640x480@72Hz
(II) RADEON(1): 640x480@75Hz
(II) RADEON(1): 800x600@56Hz
(II) RADEON(1): 800x600@60Hz
(II) RADEON(1): 800x600@72Hz
(II) RADEON(1): 800x600@75Hz
(II) RADEON(1): 832x624@75Hz
(II) RADEON(1): 1024x768@60Hz
(II) RADEON(1): 1024x768@70Hz
(II) RADEON(1): 1024x768@75Hz
(II) RADEON(1): 1280x1024@75Hz
(II) RADEON(1): 1152x870@75Hz
(II) RADEON(1): Manufacturer's mask: 0
(II) RADEON(1): Supported Future Video Modes:
(II) RADEON(1): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEON(1): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(1): Supported additional Video Mode:
(II) RADEON(1): clock: 130.4 MHz   Image Size:  432 x 324 mm
(II) RADEON(1): h_active: 1600  h_sync: 1648  h_sync_end 1680 h_blank_end 1760 h_border: 0
(II) RADEON(1): v_active: 1200  v_sync: 1202  v_sync_end 1206 v_blanking: 1235 v_border: 0
(II) RADEON(1): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 81 kHz, PixClock max 140 MHz
(II) RADEON(1): Monitor name: SyncMaster
(II) RADEON(1): Serial No: HSDY400867
(II) RADEON(1): EDID (in hex):
(II) RADEON(1): 	00ffffffffffff004c2d91003132424e
(II) RADEON(1): 	0e0f0103802b20a02ad0c4a15a4b9723
(II) RADEON(1): 	174f57bfef80a9408180010101010101
(II) RADEON(1): 	010101010101ed3240a060b023403020
(II) RADEON(1): 	2400b0441100001a000000fd00384b1e
(II) RADEON(1): 	510e000a202020202020000000fc0053
(II) RADEON(1): 	796e634d61737465720a2020000000ff
(II) RADEON(1): 	00485344593430303836370a20200009
in RADEONProbeOutputModes
(II) RADEON(1): EDID vendor "SAM", prod id 145
(II) RADEON(1): Output DVI-0 connected
(II) RADEON(1): Using user preference for initial modes
(II) RADEON(1): Output DVI-0 using initial mode 1600x1200
after xf86InitialConfiguration
(**) RADEON(1): Display dimensions: (430, 320) mm
(**) RADEON(1): DPI set to (94, 127)
(II) Loading sub module "fb"
(II) LoadModule: "fb"

(II) Reloading /usr/lib/xorg/modules//libfb.so
(==) RADEON(1): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(==) RADEON(1): Using XAA acceleration architecture
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"

(II) Reloading /usr/lib/xorg/modules//libxaa.so
(!!) RADEON(1): For information on using the multimedia capabilities
	of this adapter, please see http://gatos.sf.net.
(!!) RADEON(1): MergedFB support has been removed and replaced with xrandr 1.2 support
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  Yes, I do.
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
	[20] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[21] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[22] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[23] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[24] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[25] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[26] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[27] 1	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[28] 1	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[29] 1	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[30] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[31] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[32] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[33] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[34] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[35] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[36] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[37] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[38] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[39] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[40] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[41] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[42] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[43] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
	[44] 1	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[45] 1	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) RADEON(0): RADEONScreenInit cc000000 0 0
Entering TV Save
Save TV timing tables
saveTimingTables: reading timing tables
TV Save done
(II) RADEON(0): RADEONInitMemoryMap() : 
(II) RADEON(0):   mem_size         : 0x04000000
(II) RADEON(0):   MC_FB_LOCATION   : 0xcfffcc00
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(II) RADEON(0): Depth moves disabled by default
(II) RADEON(0): Memory manager initialized to (0,0) (1024,8191)
(II) RADEON(0): Reserved area from (0,768) to (1024,770)
(II) RADEON(0): Largest offscreen area available: 1024 x 7421
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xcfffcc00 0x1fff0000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(==) RADEON(0): Backing store disabled
(WW) RADEON(0): Direct rendering disabled
(II) RADEON(0): XAA Render acceleration unsupported on Radeon 9500/9700 and newer. Please use EXA instead.
(II) RADEON(0): Render acceleration disabled
(II) RADEON(0): num quad-pipes is 1
(II) RADEON(0): Using XFree86 Acceleration Architecture (XAA)
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
(II) RADEON(0): Acceleration enabled
(II) RADEON(0): DPMS enabled
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Will use 32 kb for hardware cursor 0 at offset 0x00302000
(II) RADEON(0): Will use 32 kb for hardware cursor 1 at offset 0x00306000
(II) RADEON(0): Largest offscreen area available: 1024 x 7413
(II) RADEON(0): No video input capabilities detected and no information is provided - disabling multimedia i2c
(II) Loading sub module "theatre_detect"
(II) LoadModule: "theatre_detect"

(II) Loading /usr/lib/xorg/modules/multimedia//theatre_detect_drv.so
(II) Module theatre_detect: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 4.1
(II) RADEON(0): no multimedia table present, disabling Rage Theatre.
(II) RADEON(0): Set up overlay video
(II) RADEON(0): Set up textured video
init memmap
init common
init crtc1
init pll1
freq: 65000000
best_freq: 65000000
best_feedback_div: 130
best_ref_div: 9
best_post_div: 6
restore memmap
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xcfffcc00 0xcfffcc00
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
restore common
restore crtc1
restore pll1
finished PLL1
restore dac
(II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(--) RandR disabled
(II) RADEON(1): RADEONScreenInit d0000000 0 0
Output 66 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
(II) RADEON(1): RADEONInitMemoryMap() : 
(II) RADEON(1):   mem_size         : 0x08000000
(II) RADEON(1):   MC_FB_LOCATION   : 0xd7ffd000
(II) RADEON(1):   MC_AGP_LOCATION  : 0x003f0000
(II) RADEON(1): Depth moves disabled by default
(II) RADEON(1): Memory manager initialized to (0,0) (1600,8191)
(II) RADEON(1): Reserved area from (0,1600) to (1600,1602)
(II) RADEON(1): Largest offscreen area available: 1600 x 6589
(II) RADEON(1): RADEONRestoreMemMapRegisters() : 
(II) RADEON(1):   MC_FB_LOCATION   : 0xd7ffd000 0xd7ffd000
(II) RADEON(1):   MC_AGP_LOCATION  : 0x003f0000
(==) RADEON(1): Backing store disabled
(WW) RADEON(1): Direct rendering disabled
(II) RADEON(1): XAA Render acceleration unsupported on Radeon 9500/9700 and newer. Please use EXA instead.
(II) RADEON(1): Render acceleration disabled
(II) RADEON(1): num quad-pipes is 1
(II) RADEON(1): Using XFree86 Acceleration Architecture (XAA)
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
(II) RADEON(1): Acceleration enabled
(II) RADEON(1): DPMS enabled
(==) RADEON(1): Silken mouse enabled
(II) RADEON(1): Will use 32 kb for hardware cursor 0 at offset 0x009c8000
(II) RADEON(1): Will use 32 kb for hardware cursor 1 at offset 0x009ce000
(II) RADEON(1): Largest offscreen area available: 1600 x 6581
(II) RADEON(1): Textured video requires CP on R5xx/IGP
Output 66 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
Output 66 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Mode 1600x1200 - 1760 1235 9
(II) RADEON(1): RADEONRestoreMemMapRegisters() : 
(II) RADEON(1):   MC_FB_LOCATION   : 0xd7ffd000 0xd7ffd000
(II) RADEON(1):   MC_AGP_LOCATION  : 0x003f0000
freq: 130370000
best_freq: 130371429
best_feedback_div: 169
best_ref_div: 7
best_post_div: 5
(II) RADEON(1): crtc(0) Clock: mode 130370, PLL 130370
(II) RADEON(1): crtc(0) PLL  : refdiv 7, fbdiv 0xA9(169), pdiv 5
Set CRTC PLL success
Set CRTC Timing success
Not using RMX
scaler 0 setup success
Set CRTC 0 Source success
(II) RADEON(1): Coherent Mode enabled
Output digital setup success
Output 66 enable success
Enable CRTC 0 success
Unblank CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
(II) RADEON(1): RandR 1.2 enabled, ignore the following RandR disabled message.
(--) RandR disabled
(II) Entity 0 shares no resources
(II) Entity 1 shares no resources
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
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event1"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "de"
(**) AT Translated Set 2 keyboard: xkb_layout: "de"
(**) Option "xkb_variant" "nodeadkeys"
(**) AT Translated Set 2 keyboard: xkb_variant: "nodeadkeys"
(**) Option "xkb_options" "lv3:ralt_switch"
(**) AT Translated Set 2 keyboard: xkb_options: "lv3:ralt_switch"
(II) config/hal: Adding input device Logitech USB Trackball
(**) Logitech USB Trackball: always reports core events
(**) Logitech USB Trackball: Device: "/dev/input/event5"
(II) Logitech USB Trackball: Found x and y relative axes
(II) Logitech USB Trackball: Found 5 mouse buttons
(II) Logitech USB Trackball: Configuring as mouse
(II) XINPUT: Adding extended input device "Logitech USB Trackball" (type: MOUSE)
(**) Logitech USB Trackball: YAxisMapping: buttons 4 and 5
(**) Logitech USB Trackball: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
AUDIT: Thu Mar 12 15:27:24 2009: 5472 X: client 4 rejected from local host ( uid=0 gid=0 pid=5706 )
AUDIT: Thu Mar 12 15:27:30 2009: 5472 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=5708 )
  Auth name: MIT-MAGIC-COOKIE-1 ID: -1
AUDIT: Thu Mar 12 15:27:30 2009: 5472 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=5709 )
  Auth name: MIT-MAGIC-COOKIE-1 ID: -1
AUDIT: Thu Mar 12 15:27:30 2009: 5472 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=5710 )
  Auth name: MIT-MAGIC-COOKIE-1 ID: -1

```

Xorg.0.log

```
glxinfo 
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Segmentation fault

```

Output of glxinfo.

I've googled around near and far, but it seems, this setup is rather exotic - my question is, is there any chance, to get any kind of 3D acceleration out of this? Xinerama etc is running fine.

---

### Post by herr_tichy on 2009-03-13
*bump*

---

### Post by herr_tichy on 2009-03-13
Whoha, not everybody at once ;)

Well, it looks like I'm going to get myself some decent ATI-card with dual head output, right?

---

### Post by asmit21 on 2009-03-16
Well, I am running a quad monitor display from one card (to the system though, it looks like two, it was hell getting it to do it though, the stupid pci configurations where so screwed up)

I have the ATI VisionTek Radeon HD 2600XT X2 card (this is a quad-head card - a bit pricey though)

I just got all the displays working yesterday (03/15/09), I was working on it for about 4 months though, So I can feel the pain. My wife thought I went nuts when I got it to work though.

I am not sure if my OpenGL works correctly or not.

If you tell me how I can test this easyly, I will get to work on it if my OpenGL does not work, and get you a solutions. Please let me know soon!

I look forward to your reply.

----------------------
~Aaron J Smith

---

### Post by brandon88tube on 2009-03-16
> **asmit21 said:**
> Well, I am running a quad monitor display from one card (to the system though, it looks like two, it was hell getting it to do it though, the stupid pci configurations where so screwed up)

I have the ATI VisionTek Radeon HD 2600XT X2 card (this is a quad-head card - a bit pricey though)

I just got all the displays working yesterday (03/15/09), I was working on it for about 4 months though, So I can feel the pain. My wife thought I went nuts when I got it to work though.

I am not sure if my OpenGL works correctly or not.

If you tell me how I can test this easyly, I will get to work on it if my OpenGL does not work, and get you a solutions. Please let me know soon!

I look forward to your reply.

----------------------
~Aaron J Smith

It would be great if you could tell us what you did and post your /etc/X11/xorg.conf file as I am having problems just getting my second monitor working with my ATI card.

---

### Post by herr_tichy on 2009-03-16
> **asmit21 said:**
> 
I am not sure if my OpenGL works correctly or not.

Just run glxinfo in a terminal and post the output - it either says something like in my first post (then it doesn't work) or something like


```
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.3
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_ARB_multisample

etc.

```


Thanks a lot for your reply :)

---

### Post by asmit21 on 2009-03-17
> **brandon88tube said:**
> It would be great if you could tell us what you did and post your /etc/X11/xorg.conf file as I am having problems just getting my second monitor working with my ATI card.

I will get on that asap. My exact steps are so sporadic that it will take me a little time to retrace what I did, as you know, It took me a long time, and a lot of searching to figure out what was really wrong. My Xorg was in fact perfect. It was an entirely another issue all together. I will get to work on that early this morning and I will hope to have a full post available by this evening sometime, or try for at least early tomorrow for you.

If I run into some issues with re-tracing my steps I will let you know.
I am even thinking of writing up a "How I did it" for my specific card and other quad-head cards.

----------------------
~Aaron J Smith

---

### Post by asmit21 on 2009-03-17
> **herr_tichy said:**
> Just run glxinfo in a terminal and post the output
...
-----
...
Thanks a lot for your reply :)

Dude, I think this is a no!

```


>glxinfo
name of display: :0.0
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  158 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  13
  Current serial number in output stream:  13


```

I will get to working on how I can fix it though. So I will get back to you I hope soon on this matter. 

----------------------
~Aaron J Smith

---

### Post by oneindelijk on 2009-03-26
Hi Guys, 

I've seen this thread looking for some problem which you guys might be able to help you.
But first I'll try to help you...

Although I'm not using Xinerama, I got Ubuntu 8.10 working on Dual Heads using an ATI Radeon 1250 With a laptop 1280x800 and a 1440x900 lcd.
Compiz is working just fine (with a 6 sided body warped into a sphere - cube effect; kinky !)
So I thought I post my xorg.conf here
Hope it can be of any help, unless it's the combination with xinerama that you're after. I've tried that, too, but my screen was something a fractals-seeing bee might be able to enjoy after I applied these settings.

Now the problem I'm still facing is that I have no entries for keyboard and mouse in my xorg.conf.
They both work in one displaymgr but not in the other one, one the other screen.
I've tried adding these sections (as you can see in the top of my xorg.conf file) for the keyboard and the mouse hoping that it would autodetect or something, but that was really a wild guess :-D

So how can I add these sections ?

```

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg
#
# From internet #######
#Section "ServerLayout"
#Identifier "Default Layout"
#Screen 0 "Screen 0" 0 0
#Screen 1 "Screen 1"
#InputDevice "Keyboard0" "CoreKeyboard"
#EndSection
# ###########
Section "InputDevice"
    Identifier    "CoreKeyboard"
    Driver        "kbd"
#    Option        "XkbRules"    "xorg"
#    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "be"
EndSection

Section "InputDevice"
     Identifier    "CorePointer"
EndSection

Section "ServerLayout"
	InputDevice "Mouse0" "CorePointer"
	InputDevice "Keyboard0" "CoreKeyboard"
	Identifier     "aticonfig Layout"
	Screen      0  "amdcccle-Screen[1]-1" 1440 9
	Screen         "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "ServerFlags"
	Option	    "Xinerama" "off"
	Option "AllowEmptyInput" "off"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "amdcccle-Monitor[1]-1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:5:0"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-1"
	Driver      "fglrx"
	BusID       "PCI:1:5:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[1]-1"
	Device     "amdcccle-Device[1]-1"
	Monitor    "amdcccle-Monitor[1]-1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

---

