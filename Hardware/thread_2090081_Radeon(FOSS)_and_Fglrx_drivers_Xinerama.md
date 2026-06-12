---
title: "Radeon(FOSS) and Fglrx drivers Xinerama"
date: 2012-12-01
forum: Hardware
---

### Post by kingtiger01 on 2012-12-01
Hello all... Ive got a issue and im out of idea's. Ive poked around IRC and they have no clue... So im left with the forums again...

I CANNOT set up a Dual-Head(Xinerama) setup with 2 Different Cards running FGLRX and RADEON Drivers Respectively...

Hardware: AMD Radeon HD 5770 & AMD Radeon HD 3100

Software: Ubuntu 12.10, X.Org X Server 1.13.0, FGLRX v.9.0, RADEON 6.99.99+git20120816(XorgEdgers)

Xconfig

```

Section "Serverflags"
 Option  "AllowMouseOpenFail"    "true"
 Option  "Xinerama" "on"
 Option  "Clone" "off"
EndSection

Section "ServerLayout"
        Identifier     "seat0"
        Screen      0  "Screen0" 0 0
        Screen      1  "Screen1" RightOf "Screen0"
        InputDevice    "Mouse0" "CorePointer"
        InputDevice    "Keyboard0" "CoreKeyboard"
EndSection       
       
Section "Extensions"
	Option	    "Composite" "Enable"
	Option	    "RENDER" "Enable"
	Option	    "RANDR" "Enable"
	Option	    "DAMAGE" "Enable"
	Option	    "GLX" "Enable"
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
	Identifier   "Monitor0"
	Option	    "VendorName" "ACER"
	Option	    "ModelName" "AL1716"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1280x1024"
	Option	    "TargetRefresh" "75"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "Monitor1"
	Option	    "VendorName" "COMPAQ"
	Option	    "ModelName" "MV500"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1024x768"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection


Section "Device"
	Option	    "AccelMethod" "EXA"
	Option	    "MigrationHeuristic" "greedy"
	Option	    "AccelDFS" "true"
        Option      "TripleBuffer"   "true"
        Option      "ColorTiling" "true" 
	Option	    "EnablePageFlip" "true"
	Option	    "EnableDepthMoves" "true"
	Identifier  "Card0"
	Driver      "radeon"
	BusID       "PCI:1:5:0"
	Screen		1
EndSection

Section "Device"
	Identifier  "Card1"
	Driver      "fglrx"
	BusID       "PCI:2:0:0"
        Screen		0
EndSection

Section "Screen"
	Identifier "Screen1"
	Monitor    "Monitor1"
        Device     "Card0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Monitor    "Monitor0"
	Device     "Card1"
EndSection

```

Xorg Log(Note:  i was attempting to load no additional drivers in the debugging run last)

```

[    29.518] 
X.Org X Server 1.13.0
Release Date: 2012-09-05
[    29.518] X Protocol Version 11, Revision 0
[    29.518] Build Operating System: Linux 3.2.0-32-generic x86_64 Ubuntu
[    29.518] Current Operating System: Linux MIKE-DESKTOP 3.5.0-20-generic #31~pre201211300400-Ubuntu SMP Fri Nov 30 09:22:20 UTC 2012 x86_64
[    29.518] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-20-generic root=UUID=fd1f45d4-7523-4863-863a-1fe4addf4514 ro quiet splash vt.handoff=7
[    29.518] Build Date: 27 November 2012  07:44:35AM
[    29.518] xorg-server 2:1.13.0-0ubuntu6.1 (For technical support please see http://www.ubuntu.com/support) 
[    29.518] Current version of pixman: 0.26.0
[    29.518] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    29.518] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    29.518] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Nov 29 08:48:16 2012
[    29.518] (==) Using config file: "/etc/X11/xorg.conf"
[    29.518] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    29.518] (==) ServerLayout "seat0"
[    29.518] (**) |-->Screen "Screen0" (0)
[    29.518] (**) |   |-->Monitor "Monitor0"
[    29.519] (**) |   |-->Device "Card1"
[    29.519] (**) |-->Screen "Screen1" (1)
[    29.519] (**) |   |-->Monitor "Monitor1"
[    29.519] (**) |   |-->Device "Card0"
[    29.519] (**) |-->Input Device "Mouse0"
[    29.519] (**) |-->Input Device "Keyboard0"
[    29.519] (**) Option "DontZap" "no"
[    29.519] (**) Option "AllowMouseOpenFail" "true"
[    29.519] (**) Option "Xinerama" "on"
[    29.519] (**) Option "AutoAddDevices" "false"
[    29.519] (**) Not automatically adding devices
[    29.519] (==) Automatically enabling devices
[    29.519] (==) Automatically adding GPU devices
[    29.519] (**) Xinerama: enabled
[    29.519] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    29.519] 	Entry deleted from font path.
[    29.519] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    29.519] 	Entry deleted from font path.
[    29.519] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    29.519] 	Entry deleted from font path.
[    29.519] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    29.519] 	Entry deleted from font path.
[    29.519] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    29.519] 	Entry deleted from font path.
[    29.519] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    29.519] 	Entry deleted from font path.
[    29.519] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    29.519] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    29.519] (**) Extension "Composite" is enabled
[    29.519] (**) Extension "RENDER" is enabled
[    29.519] (**) Extension "DAMAGE" is enabled
[    29.519] (**) Extension "GLX" is enabled
[    29.519] (II) Loader magic: 0x7f35e2c5fc40
[    29.519] (II) Module ABI versions:
[    29.519] 	X.Org ANSI C Emulation: 0.4
[    29.519] 	X.Org Video Driver: 13.0
[    29.519] 	X.Org XInput driver : 18.0
[    29.519] 	X.Org Server Extension : 7.0
[    29.520] (--) PCI: (0:1:5:0) 1002:9611:1043:82ee rev 0, Mem @ 0xc0000000/268435456, 0xfbdf0000/65536, 0xfbc00000/1048576, I/O @ 0x0000c000/256
[    29.521] (--) PCI:*(0:2:0:0) 1002:68b8:1682:2990 rev 0, Mem @ 0xd0000000/268435456, 0xfbee0000/131072, I/O @ 0x0000d000/256, BIOS @ 0x????????/131072
[    29.521] (II) Open ACPI successful (/var/run/acpid.socket)
[    29.521] Initializing built-in extension Generic Event Extension
[    29.521] Initializing built-in extension SHAPE
[    29.521] Initializing built-in extension MIT-SHM
[    29.521] Initializing built-in extension XInputExtension
[    29.521] Initializing built-in extension XTEST
[    29.521] Initializing built-in extension BIG-REQUESTS
[    29.521] Initializing built-in extension SYNC
[    29.521] Initializing built-in extension XKEYBOARD
[    29.521] Initializing built-in extension XC-MISC
[    29.521] Initializing built-in extension SECURITY
[    29.521] Initializing built-in extension XINERAMA
[    29.521] Initializing built-in extension XFIXES
[    29.521] Initializing built-in extension RENDER
[    29.521] Initializing built-in extension RANDR
[    29.521] Initializing built-in extension COMPOSITE
[    29.521] Initializing built-in extension DAMAGE
[    29.521] Initializing built-in extension MIT-SCREEN-SAVER
[    29.521] Initializing built-in extension DOUBLE-BUFFER
[    29.521] Initializing built-in extension RECORD
[    29.521] Initializing built-in extension DPMS
[    29.521] Initializing built-in extension X-Resource
[    29.521] Initializing built-in extension XVideo
[    29.521] Initializing built-in extension XVideo-MotionCompensation
[    29.521] Initializing built-in extension XFree86-VidModeExtension
[    29.521] Initializing built-in extension XFree86-DGA
[    29.521] Initializing built-in extension XFree86-DRI
[    29.521] Initializing built-in extension DRI2
[    29.521] (II) LoadModule: "glx"
[    29.528] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/extensions/libglx.so
[    29.529] (II) Module glx: vendor="Advanced Micro Devices, Inc."
[    29.529] 	compiled for 6.9.0, module version = 1.0.0
[    29.529] Loading extension GLX
[    29.529] (II) LoadModule: "fglrx"
[    29.529] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/drivers/fglrx_drv.so
[    29.545] (II) Module fglrx: vendor="FireGL - AMD Technologies Inc."
[    29.545] 	compiled for 1.4.99.906, module version = 9.0.2
[    29.545] 	Module class: X.Org Video Driver
[    29.545] (II) Loading sub module "fglrxdrm"
[    29.545] (II) LoadModule: "fglrxdrm"
[    29.545] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/linux/libfglrxdrm.so
[    29.545] (II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
[    29.545] 	compiled for 1.4.99.906, module version = 9.0.2
[    29.545] (II) LoadModule: "radeon"
[    29.550] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    29.550] (II) Module radeon: vendor="X.Org Foundation"
[    29.550] 	compiled for 1.12.99.904, module version = 6.99.99
[    29.550] 	Module class: X.Org Video Driver
[    29.550] 	ABI class: X.Org Video Driver, version 13.0
[    29.550] (II) LoadModule: "mouse"
[    29.556] (II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
[    29.565] (II) Module mouse: vendor="X.Org Foundation"
[    29.565] 	compiled for 1.12.99.903, module version = 1.7.2
[    29.565] 	Module class: X.Org XInput Driver
[    29.565] 	ABI class: X.Org XInput driver, version 18.0
[    29.565] (II) LoadModule: "kbd"
[    29.565] (II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
[    29.588] (II) Module kbd: vendor="X.Org Foundation"
[    29.588] 	compiled for 1.12.99.902, module version = 1.6.1
[    29.588] 	Module class: X.Org XInput Driver
[    29.588] 	ABI class: X.Org XInput driver, version 18.0
[    29.588] (II) AMD Proprietary Linux Driver Version Identifier:9.00.2
[    29.588] (II) AMD Proprietary Linux Driver Release Identifier: 9.00.11                              
[    29.588] (II) AMD Proprietary Linux Driver Build Date: Sep 20 2012 11:56:16
[    29.588] (II) RADEON: Driver for ATI Radeon chipsets:
	ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI FireMV 2400 3155 (PCI),
	ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
	ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
	ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
	ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
	ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
	ATI Radeon 8500 AIW BB (AGP), ATI Radeon IGP320M (U1) 4336,
	ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
	ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
	ATI Radeon X800 VE (R420) JT (AGP), ATI Radeon X850 (R480) (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI FireMV 2400 PCI,
	ATI Radeon 9700 Pro ND (AGP), ATI Radeon 9700/9500Pro NE (AGP),
	ATI Radeon 9600TX NF (AGP), ATI FireGL X1 NG (AGP),
	ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
	ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
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
	ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
	ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
	ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
	ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
	ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
	ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
	ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
	ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
	ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
	ATI Radeon 4800 Series, ATI Radeon HD 4850 x2,
	ATI FirePro V8750 (FireGL), ATI FirePro V7760 (FireGL),
	ATI Mobility RADEON HD 4850, ATI Mobility RADEON HD 4850 X2,
	ATI Radeon 4800 Series, ATI FirePro RV770, AMD FireStream 9270,
	AMD FireStream 9250, ATI FirePro V8700 (FireGL),
	ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
	ATI Mobility RADEON HD 4870, ATI Radeon 4800 Series,
	ATI Radeon 4800 Series, ATI FirePro M7750, ATI M98, ATI M98, ATI M98,
	ATI Mobility Radeon HD 4650, ATI Radeon RV730 (AGP),
	ATI Mobility Radeon HD 4670, ATI FirePro M5750,
	ATI Mobility Radeon HD 4670, ATI Radeon RV730 (AGP),
	ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
	ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
	ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
	ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
	ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
	ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI Radeon HD 4770,
	ATI FirePro M5750, ATI RV610, ATI Radeon HD 2400 XT,
	ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
	ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
	ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
	ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
	ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
	ATI Mobility Radeon HD 3850 X2, ATI RV670,
	ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
	ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
	ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
	ATI Radeon RV710, ATI Radeon RV710, ATI Radeon RV710,
	ATI Radeon HD 4350, ATI Mobility Radeon 4300 Series,
	ATI Mobility Radeon 4500 Series, ATI Mobility Radeon 4500 Series,
	ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
	ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
	ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
	ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
	ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
	ATI FireGL V3600, ATI Radeon HD 2600 LE,
	ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
	ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
	ATI Radeon HD 3450, ATI Radeon HD 3450, ATI Radeon HD 3430,
	ATI Radeon HD 3450, ATI FirePro V3700, ATI FireMV 2450,
	ATI FireMV 2260, ATI FireMV 2260, ATI Radeon HD 3600 Series,
	ATI Radeon HD 3650 AGP, ATI Radeon HD 3600 PRO,
	ATI Radeon HD 3600 XT, ATI Radeon HD 3600 PRO,
	ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
	ATI Mobility FireGL V5700, ATI Mobility FireGL V5725,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3300 Graphics, ATI Radeon HD 3200 Graphics,
	ATI Radeon 3000 Graphics, SUMO, SUMO, SUMO2, SUMO2, SUMO2, SUMO2,
	SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, ATI Radeon HD 4200,
	ATI Radeon 4100, ATI Mobility Radeon HD 4200,
	ATI Mobility Radeon 4100, ATI Radeon HD 4290, ATI Radeon HD 4250,
	AMD Radeon HD 6310 Graphics, AMD Radeon HD 6310 Graphics,
	AMD Radeon HD 6250 Graphics, AMD Radeon HD 6250 Graphics,
	AMD Radeon HD 6300 Series Graphics,
	AMD Radeon HD 6200 Series Graphics, PALM, PALM, PALM, CYPRESS,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, AMD Firestream 9370,
	AMD Firestream 9350, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5800 Series, ATI Radeon HD 5900 Series,
	ATI Radeon HD 5900 Series, ATI Mobility Radeon HD 5800 Series,
	ATI Mobility Radeon HD 5800 Series,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
	ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
	ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
	ATI Mobility Radeon HD 5000 Series,
	ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5670,
	ATI Radeon HD 5570, ATI Radeon HD 5500 Series, REDWOOD,
	ATI Mobility Radeon HD 5000 Series,
	ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon Graphics,
	ATI Mobility Radeon Graphics, CEDAR,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, ATI FirePro 2270, CEDAR,
	ATI Radeon HD 5450, CEDAR, CEDAR, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
	CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
	AMD Radeon HD 6900 Series, AMD Radeon HD 6900 Series, CAYMAN, CAYMAN,
	CAYMAN, AMD Radeon HD 6900M Series, Mobility Radeon HD 6000 Series,
	BARTS, BARTS, Mobility Radeon HD 6000 Series,
	Mobility Radeon HD 6000 Series, BARTS, BARTS, BARTS, BARTS,
	AMD Radeon HD 6800 Series, AMD Radeon HD 6800 Series,
	AMD Radeon HD 6700 Series, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
	TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
	TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
	CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
	CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, ARUBA, ARUBA,
	ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
	ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
	ARUBA, ARUBA, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI,
	TAHITI, TAHITI, TAHITI, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
	PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
	PITCAIRN, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
	VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
	VERDE, VERDE
[    29.595] (++) using VT number 7

[    29.595] (WW) Falling back to old probe method for fglrx
[    29.614] (II) Loading PCS database from /etc/ati/amdpcsdb /etc/ati/amdpcsdb.default
[    29.629] ukiDynamicMajor: found major device number 250
[    29.629] ukiDynamicMajor: found major device number 250
[    29.629] ukiOpenByBusid: Searching for BusID PCI:2:0:0
[    29.629] ukiOpenDevice: node name is /dev/ati/card0
[    29.629] ukiOpenDevice: open result is 10, (OK)
[    29.727] ukiOpenByBusid: ukiOpenMinor returns 10
[    29.727] ukiOpenByBusid: ukiGetBusid reports PCI:2:0:0
[    29.804] (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:5:0) found
[    29.804] (--) Chipset Supported AMD Graphics Processor (0x68B8) found
[    29.804] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:17:0) found
[    29.804] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:0) found
[    29.804] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:1) found
[    29.804] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:2) found
[    29.804] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:0) found
[    29.804] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:1) found
[    29.804] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:2) found
[    29.804] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:0) found
[    29.804] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:1) found
[    29.804] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:2) found
[    29.804] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:3) found
[    29.804] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:4) found
[    29.804] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:5) found
[    29.805] (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:5:0) found
[    29.805] (WW) fglrx: No matching Device section for instance (BusID PCI:0@2:0:1) found
[    29.805] (II) AMD Video driver is running on a device belonging to a group targeted for this release
[    29.805] (II) AMD Video driver is signed
[    29.805] (II) fglrx(0): pEnt->device->identifier=0x7f35e4927020
[    29.805] (II) [KMS] drm report modesetting isn't supported.
[    29.805] (EE) Screen 1 deleted because of no matching config section.
[    29.805] (II) UnloadModule: "radeon"
[    29.805] (II) fglrx(0): === [xdl_xs113_atiddxPreInit] === begin
[    29.806] (II) Loading sub module "vgahw"
[    29.806] (II) LoadModule: "vgahw"
[    29.806] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    29.806] (II) Module vgahw: vendor="X.Org Foundation"
[    29.806] 	compiled for 1.13.0, module version = 0.1.0
[    29.806] 	ABI class: X.Org Video Driver, version 13.0
[    29.806] (II) fglrx(0): Creating default Display subsection in Screen section
	"Screen0" for depth/fbbpp 24/32
[    29.806] (==) fglrx(0): Depth 24, (==) framebuffer bpp 32
[    29.806] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    29.806] (==) fglrx(0): Default visual is TrueColor
[    29.806] (**) fglrx(0): Option "DPMS" "true"
[    29.806] (==) fglrx(0): RGB weight 888
[    29.806] (II) fglrx(0): Using 8 bits per RGB 
[    29.806] (==) fglrx(0): Buffer Tiling is ON
[    29.806] (II) Loading sub module "fglrxdrm"
[    29.806] (II) LoadModule: "fglrxdrm"
[    29.806] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/linux/libfglrxdrm.so
[    29.806] (II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
[    29.807] 	compiled for 1.4.99.906, module version = 9.0.2
[    29.828] ukiDynamicMajor: found major device number 250
[    29.828] ukiDynamicMajor: found major device number 250
[    29.828] ukiOpenByBusid: Searching for BusID PCI:2:0:0
[    29.828] ukiOpenDevice: node name is /dev/ati/card0
[    29.829] ukiOpenDevice: open result is 13, (OK)
[    29.829] ukiOpenByBusid: ukiOpenMinor returns 13
[    29.829] ukiOpenByBusid: ukiGetBusid reports PCI:2:0:0
[    29.829] (**) fglrx(0): NoAccel = NO
[    29.829] (**) fglrx(0): AMD 2D Acceleration Architecture enabled
[    29.829] (--) fglrx(0): Chipset: "ATI Radeon HD 5700 Series" (Chipset = 0x68b8)
[    29.829] (--) fglrx(0): (PciSubVendor = 0x1682, PciSubDevice = 0x2990)
[    29.829] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original AMD
[    29.829] (--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
[    29.829] (--) fglrx(0): MMIO registers at 0xfbee0000
[    29.829] (--) fglrx(0): I/O port at 0x0000d000
[    29.829] (==) fglrx(0): ROM-BIOS at 0x000c0000
[    29.904] (II) fglrx(0): AC Adapter is used
[    29.910] (II) fglrx(0): Primary V_BIOS segment is: 0xc000
[    29.910] (II) Loading sub module "vbe"
[    29.910] (II) LoadModule: "vbe"
[    29.911] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    29.911] (II) Module vbe: vendor="X.Org Foundation"
[    29.911] 	compiled for 1.13.0, module version = 1.1.0
[    29.911] 	ABI class: X.Org Video Driver, version 13.0
[    29.911] (II) fglrx(0): VESA BIOS detected
[    29.911] (II) fglrx(0): VESA VBE Version 3.0
[    29.911] (II) fglrx(0): VESA VBE Total Mem: 16384 kB
[    29.911] (II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
[    29.911] (II) fglrx(0): VESA VBE OEM Software Rev: 12.12
[    29.911] (II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
[    29.911] (II) fglrx(0): VESA VBE OEM Product: -113-C01002-101 
[    29.911] (II) fglrx(0): VESA VBE OEM Product Rev: 01.00
[    29.911] (II) fglrx(0): AMD Video BIOS revision 9 or later detected
[    29.911] (--) fglrx(0): Video RAM: 1048576 kByte, Type: GDDR5
[    29.911] (II) fglrx(0): PCIE card detected
[    29.911] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
[    29.911] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[    29.911] (II) fglrx(0): [FB] MC range(MCFBBase = 0xf00000000, MCFBSize = 0x40000000)
[    29.911] (II) fglrx(0): RandR 1.2 support is enabled!
[    29.911] (II) fglrx(0): RandR 1.2 rotation support is enabled!
[    29.912] (==) fglrx(0): Center Mode is disabled 
[    29.912] (II) Loading sub module "fb"
[    29.912] (II) LoadModule: "fb"
[    29.912] (II) Loading /usr/lib/xorg/modules/libfb.so
[    29.912] (II) Module fb: vendor="X.Org Foundation"
[    29.912] 	compiled for 1.13.0, module version = 1.0.0
[    29.912] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    29.912] (II) Loading sub module "ddc"
[    29.912] (II) LoadModule: "ddc"
[    29.912] (II) Module "ddc" already built-in
[    29.995] (II) fglrx(0): Output DFP1 using monitor section Monitor0
[    29.995] (**) fglrx(0): Option "PreferredMode" "1280x1024"
[    29.995] (**) fglrx(0): Option "Position" "0 0"
[    29.995] (**) fglrx(0): Option "Disable" "false"
[    29.995] (**) fglrx(0): Option "Rotate" "normal"
[    29.995] (**) fglrx(0): Option "TargetRefresh" "75"
[    29.995] (II) fglrx(0): Output DFP2 has no monitor section
[    29.995] (II) fglrx(0): Output DFP3 has no monitor section
[    29.995] (II) fglrx(0): Output DFP4 has no monitor section
[    29.995] (II) fglrx(0): Output CRT1 has no monitor section
[    29.995] (II) fglrx(0): Output CRT2 has no monitor section
[    29.995] (II) Loading sub module "ddc"
[    29.995] (II) LoadModule: "ddc"
[    29.995] (II) Module "ddc" already built-in
[    29.995] (II) fglrx(0): Connected Display0: CRT1
[    29.995] (II) fglrx(0):  Display0: Failed to get EDID information. 
[    29.996] (II) fglrx(0): EDID for output DFP1
[    29.996] (II) fglrx(0): EDID for output DFP2
[    29.996] (II) fglrx(0): EDID for output DFP3
[    29.996] (II) fglrx(0): EDID for output DFP4
[    29.996] (II) fglrx(0): EDID for output CRT1
[    29.996] (II) fglrx(0): Manufacturer: ACR  Model: ad46  Serial#: 0
[    29.996] (II) fglrx(0): Year: 2006  Week: 42
[    29.996] (II) fglrx(0): EDID Version: 1.3
[    29.996] (II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[    29.996] (II) fglrx(0): Sync:  Separate
[    29.996] (II) fglrx(0): Max Image Size [cm]: horiz.: 34  vert.: 27
[    29.996] (II) fglrx(0): Gamma: 2.20
[    29.996] (II) fglrx(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    29.996] (II) fglrx(0): First detailed timing not preferred mode in violation of standard!
[    29.996] (II) fglrx(0): redX: 0.640 redY: 0.349   greenX: 0.284 greenY: 0.617
[    29.996] (II) fglrx(0): blueX: 0.142 blueY: 0.067   whiteX: 0.313 whiteY: 0.329
[    29.996] (II) fglrx(0): Supported established timings:
[    29.996] (II) fglrx(0): 720x400@70Hz
[    29.996] (II) fglrx(0): 640x480@60Hz
[    29.996] (II) fglrx(0): 640x480@67Hz
[    29.996] (II) fglrx(0): 640x480@72Hz
[    29.996] (II) fglrx(0): 640x480@75Hz
[    29.996] (II) fglrx(0): 800x600@56Hz
[    29.996] (II) fglrx(0): 800x600@60Hz
[    29.996] (II) fglrx(0): 800x600@72Hz
[    29.996] (II) fglrx(0): 800x600@75Hz
[    29.996] (II) fglrx(0): 832x624@75Hz
[    29.996] (II) fglrx(0): 1024x768@60Hz
[    29.996] (II) fglrx(0): 1024x768@70Hz
[    29.996] (II) fglrx(0): 1024x768@75Hz
[    29.996] (II) fglrx(0): 1280x1024@75Hz
[    29.996] (II) fglrx(0): Manufacturer's mask: 0
[    29.996] (II) fglrx(0): Supported detailed timing:
[    29.996] (II) fglrx(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
[    29.996] (II) fglrx(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
[    29.996] (II) fglrx(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[    29.996] (II) fglrx(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 145 MHz
[    29.996] (II) fglrx(0): Serial No: 642052164018
[    29.996] (II) fglrx(0): Monitor name: AL1716
[    29.996] (II) fglrx(0): EDID (in hex):
[    29.996] (II) fglrx(0): 	00ffffffffffff00047246ad00000000
[    29.996] (II) fglrx(0): 	2a10010308221b78e8dc55a359489e24
[    29.996] (II) fglrx(0): 	115054bfef0001010101010101010101
[    29.996] (II) fglrx(0): 	010101010101302a009851002a403070
[    29.996] (II) fglrx(0): 	1300520e1100001e000000fd00384b1e
[    29.996] (II) fglrx(0): 	530e000a202020202020000000ff0036
[    29.996] (II) fglrx(0): 	34323035323136343031380a000000fc
[    29.996] (II) fglrx(0): 	00414c313731360a20202020202000c6
[    29.997] (II) fglrx(0): Printing probed modes for output CRT1
[    29.997] (II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz eP)
[    29.997] (II) fglrx(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    29.997] (II) fglrx(0): Modeline "1280x960"x75.0  135.00  1280 1296 1440 1688  960 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    29.997] (II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1328 1440 1688  960 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    29.997] (II) fglrx(0): Modeline "1280x768"x75.0  135.00  1280 1296 1440 1688  768 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    29.997] (II) fglrx(0): Modeline "1280x768"x60.0  108.00  1280 1328 1440 1688  768 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    29.997] (II) fglrx(0): Modeline "1280x720"x75.0  135.00  1280 1296 1440 1688  720 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    29.997] (II) fglrx(0): Modeline "1280x720"x60.0  108.00  1280 1328 1440 1688  720 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    29.997] (II) fglrx(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    29.997] (II) fglrx(0): Modeline "1024x768"x70.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    29.997] (II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    29.997] (II) fglrx(0): Modeline "800x600"x72.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    29.997] (II) fglrx(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    29.997] (II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    29.997] (II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    29.997] (II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    29.997] (II) fglrx(0): Modeline "640x480"x72.0   31.50  640 656 696 832  480 481 484 520 -hsync -vsync (37.9 kHz e)
[    29.997] (II) fglrx(0): Modeline "640x480"x67.0   27.28  640 664 728 816  480 481 484 499 -hsync +vsync (33.4 kHz e)
[    29.997] (II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    29.997] (II) fglrx(0): EDID for output CRT2
[    29.997] (II) fglrx(0): Output DFP1 disconnected
[    29.997] (II) fglrx(0): Output DFP2 disconnected
[    29.997] (II) fglrx(0): Output DFP3 disconnected
[    29.997] (II) fglrx(0): Output DFP4 disconnected
[    29.997] (II) fglrx(0): Output CRT1 connected
[    29.997] (II) fglrx(0): Output CRT2 disconnected
[    29.997] (II) fglrx(0): Using user preference for initial modes
[    29.997] (II) fglrx(0): Output CRT1 using initial mode 1280x1024
[    29.997] (II) fglrx(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    29.997] (II) fglrx(0): DPI set to (96, 96)
[    29.997] (II) fglrx(0): Eyefinity capable adapter detected.
[    29.997] (II) fglrx(0): Adapter ATI Radeon HD 5700 Series has 5 configurable heads and 1 displays connected.
[    29.997] (==) fglrx(0):  PseudoColor visuals disabled
[    29.997] (II) Loading sub module "ramdac"
[    29.997] (II) LoadModule: "ramdac"
[    29.997] (II) Module "ramdac" already built-in
[    29.997] (==) fglrx(0): NoDRI = NO
[    29.997] (==) fglrx(0): Capabilities: 0x00000000
[    29.997] (==) fglrx(0): CapabilitiesEx: 0x00000000
[    29.997] (==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
[    29.997] (==) fglrx(0): UseFastTLS=0
[    29.997] (II) fglrx(0): Shadow Primary option: ShadowPrimary is enabled
[    29.997] (--) Depth 24 pixmap format is 32 bpp
[    29.999] Loading extension ATIFGLRXDRI
[    29.999] (II) fglrx(0): doing swlDriScreenInit
[    29.999] (II) fglrx(0): swlDriScreenInit for fglrx driver
[    29.999] ukiDynamicMajor: found major device number 250
[    29.999] ukiDynamicMajor: found major device number 250
[    29.999] ukiDynamicMajor: found major device number 250
[    29.999] ukiOpenByBusid: Searching for BusID PCI:2:0:0
[    29.999] ukiOpenDevice: node name is /dev/ati/card0
[    29.999] ukiOpenDevice: open result is 14, (OK)
[    29.999] ukiOpenByBusid: ukiOpenMinor returns 14
[    29.999] ukiOpenByBusid: ukiGetBusid reports PCI:2:0:0
[    29.999] (II) fglrx(0): [uki] DRM interface version 1.0
[    29.999] (II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:2:0:0"
[    29.999] (II) fglrx(0): [uki] added 8192 byte SAREA at 0x2000
[    29.999] (II) fglrx(0): [uki] mapped SAREA 0x2000 to 0x7f35e2809000
[    29.999] (II) fglrx(0): [uki] framebuffer handle = 0x3000
[    29.999] (II) fglrx(0): [uki] added 1 reserved context for kernel
[    30.000] (II) fglrx(0): swlDriScreenInit done
[    30.000] (II) fglrx(0): Kernel Module Version Information:
[    30.000] (II) fglrx(0):     Name: fglrx
[    30.000] (II) fglrx(0):     Version: 9.0.2
[    30.000] (II) fglrx(0):     Date: Sep 20 2012
[    30.000] (II) fglrx(0):     Desc: AMD FireGL DRM kernel module
[    30.000] (II) fglrx(0): Kernel Module version matches driver.
[    30.000] (II) fglrx(0): Kernel Module Build Time Information:
[    30.000] (II) fglrx(0):     Build-Kernel UTS_RELEASE:        3.5.0-20-generic
[    30.000] (II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
[    30.000] (II) fglrx(0):     Build-Kernel __SMP__:            yes
[    30.000] (II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
[    30.000] (II) fglrx(0): [uki] register handle = 0x00004000
[    30.001] (II) fglrx(0): DRI initialization successfull
[    30.001] (II) fglrx(0): FBADPhys: 0xf00000000 FBMappedSize: 0x01068000
[    30.001] (==) fglrx(0): Backing store disabled
[    30.001] Loading extension FGLRXEXTENSION
[    30.001] (**) fglrx(0): DPMS enabled
[    30.001] (II) fglrx(0): Initialized in-driver Xinerama extension
[    30.001] (**) fglrx(0): Textured Video is enabled.
[    30.001] (II) LoadModule: "glesx"
[    30.001] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/glesx.so
[    30.002] (II) Module glesx: vendor="X.Org Foundation"
[    30.002] 	compiled for 1.4.99.906, module version = 1.0.0
[    30.002] Loading extension GLESX
[    30.002] (II) fglrx(0): GLESX enableFlags = 592
[    30.002] (II) fglrx(0): GLESX is enabled
[    30.002] (II) LoadModule: "amdxmm"
[    30.002] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/amdxmm.so
[    30.002] (II) Module amdxmm: vendor="X.Org Foundation"
[    30.002] 	compiled for 1.4.99.906, module version = 2.0.0
[    30.019] Loading extension AMDXVOPL
[    30.019] Loading extension AMDXVBA
[    30.020] (II) fglrx(0): UVD feature is enabled(II) fglrx(0): 
[    30.052] (II) fglrx(0): Composite extension is not loaded
[    30.052] (WW) fglrx(0): Option "VendorName" is not used
[    30.052] (WW) fglrx(0): Option "ModelName" is not used
[    30.052] (WW) fglrx(0): Option "PreferredMode" is not used
[    30.052] (WW) fglrx(0): Option "TargetRefresh" is not used
[    30.052] (WW) fglrx(0): Option "Position" is not used
[    30.052] (WW) fglrx(0): Option "Rotate" is not used
[    30.052] (WW) fglrx(0): Option "Disable" is not used
[    30.052] (II) fglrx(0): X context handle = 0x1
[    30.052] (II) fglrx(0): [DRI] installation complete
[    30.052] (==) fglrx(0): Silken mouse enabled
[    30.053] (==) fglrx(0): Using HW cursor of display infrastructure!
[    30.053] (II) fglrx(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    30.140] (--) RandR disabled
[    30.146] ukiDynamicMajor: found major device number 250
[    30.146] ukiDynamicMajor: found major device number 250
[    30.146] ukiOpenByBusid: Searching for BusID PCI:2:0:0
[    30.146] ukiOpenDevice: node name is /dev/ati/card0
[    30.146] ukiOpenDevice: open result is 15, (OK)
[    30.146] ukiOpenByBusid: ukiOpenMinor returns 15
[    30.146] ukiOpenByBusid: ukiGetBusid reports PCI:2:0:0
[    30.242] (II) AIGLX: Loaded and initialized OpenGL driver(II) GLX: Initialized DRI GL provider for screen 0
[    30.262] (II) fglrx(0): Setting screen physical size to 338 x 270
[    30.287] (II) XKB: reuse xkmfile /var/lib/xkb/server-02D8252E59564A234380F1E5417646A9DB3B7452.xkm
[    30.300] (II) Using input driver 'mouse' for 'Mouse0'
[    30.300] (**) Option "CorePointer"
[    30.300] (**) Mouse0: always reports core events
[    30.300] (**) Option "Protocol" "auto"
[    30.300] (**) Option "Device" "/dev/input/mice"
[    30.300] (II) Mouse0: Setting mouse protocol to "ExplorerPS/2"
[    30.300] (**) Mouse0: Protocol: "auto"
[    30.300] (**) Mouse0: always reports core events
[    30.300] (==) Mouse0: Emulate3Buttons, Emulate3Timeout: 50
[    30.300] (**) Option "ZAxisMapping" "4 5 6 7"
[    30.300] (**) Mouse0: ZAxisMapping: buttons 4, 5, 6 and 7
[    30.300] (**) Mouse0: Buttons: 11
[    30.300] (II) XINPUT: Adding extended input device "Mouse0" (type: MOUSE, id 6)
[    30.300] (**) Mouse0: (accel) keeping acceleration scheme 1
[    30.301] (**) Mouse0: (accel) acceleration profile 0
[    30.301] (**) Mouse0: (accel) acceleration factor: 2.000
[    30.301] (**) Mouse0: (accel) acceleration threshold: 4
[    30.301] (II) Mouse0: Setting mouse protocol to "ExplorerPS/2"
[    30.593] (II) Mouse0: ps2EnableDataReporting: succeeded
[    30.593] (II) Using input driver 'kbd' for 'Keyboard0'
[    30.593] (**) Option "CoreKeyboard"
[    30.593] (**) Keyboard0: always reports core events
[    30.593] (**) Keyboard0: always reports core events
[    30.593] (**) Option "Protocol" "standard"
[    30.593] (**) Option "XkbRules" "base"
[    30.593] (**) Option "XkbModel" "pc105"
[    30.593] (**) Option "XkbLayout" "us"
[    30.593] (II) XINPUT: Adding extended input device "Keyboard0" (type: KEYBOARD, id 7)

```

HEEEEEEEEELP!!!!!!!!!!!!!!:cry::cry::cry::cry::cry::cry::cry:

---

