---
title: "Inspiron 600m Sreen Resolution"
date: 2010-11-07
forum: Hardware
---

### Post by thenellt on 2010-11-07
I'm running Ubuntu 10.10 x32 on a Dell Inspiron 600m and I can't get the resolution above 1024 by 768. I tried adding that resolution to xorg.conf but that hasn't changed anything.
Here's my xorg.conf
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
EndSection

Section "Module"
    Load  "dri2"
    Load  "dri"
    Load  "dbe"
    Load  "extmod"
    Load  "glx"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
EndSection

Section "Device"
        Identifier    "Card0"
        Driver        "radeon"
        Option        "EnableDepthMoves"     "True"
        Option        "EnablePageFlip"       "True"
        Option        "DMAForXv"             "True"
        Option        "AccelDFS"             "True"
        Option        "ColorTiling"          "True"
        Option        "RenderAccel"          "True"
        Option        "VGAAccess"            "True"
        Option        "AccelMethod"          "EXA"
        Option        "DRI"                  "True"
        Option        "MigrationHeuristics"  "greedy"
        Option        "TripleBuffer"         "True"
        Option        "EXAOptimizeMigration" "true"
        Option        "EXANoComposite"       "No"
        Option        "BackingStore"         "true"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    Option     "Accel"    "True"
    SubSection "Display"
        Viewport   0 0
        Depth     24
	Modes	"1280x1024_60.00"
    EndSubSection
EndSection

Section "Extensions"
    Option "RENDER" "Enable"
    Option "Composite" "True"
    Option "XVideo" "Enable"
    Option "XINERAMA" "False"
EndSection

Section "DRI"
    Mode        0666
EndSection

---

### Post by thenellt on 2010-11-07
Come on, does anybody around here have experience with manually working with xorg.conf?

---

### Post by Yellow Pasque on 2010-11-07
Post your /var/log/Xorg.0.log
Often, you just need to manually specify the vertrefresh and horizsync if X isn't reading your display's EDID properly.

---

### Post by thenellt on 2010-11-07
Here's my xorg log:```

[    17.683] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    17.683] X Protocol Version 11, Revision 0
[    17.683] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[    17.683] Current Operating System: Linux thenellt-server 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:36:48 UTC 2010 i686
[    17.683] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=b835a5cb-65a6-4c05-8fbf-173f05530205 ro quiet splash
[    17.683] Build Date: 16 September 2010  05:39:22PM
[    17.683] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    17.683] Current version of pixman: 0.18.4
[    17.683] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[    17.683] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    17.683] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Nov  7 10:37:43 2010
[    17.683] (==) Using config file: "/etc/X11/xorg.conf"
[    17.683] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    17.685] (==) ServerLayout "X.org Configured"
[    17.685] (**) |-->Screen "Screen0" (0)
[    17.685] (**) |   |-->Monitor "Monitor0"
[    17.686] (**) |   |-->Device "Card0"
[    17.686] (==) Automatically adding devices
[    17.686] (==) Automatically enabling devices
[    17.686] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    17.686] 	Entry deleted from font path.
[    17.686] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    17.686] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    17.686] (**) Extension "RENDER" is enabled
[    17.686] (**) Extension "Composite" is enabled
[    17.686] (**) Extension "XVideo" is enabled
[    17.686] (**) Extension "XINERAMA" is disabled
[    17.686] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    17.686] (II) Loader magic: 0x81f8e00
[    17.686] (II) Module ABI versions:
[    17.686] 	X.Org ANSI C Emulation: 0.4
[    17.686] 	X.Org Video Driver: 8.0
[    17.686] 	X.Org XInput driver : 11.0
[    17.686] 	X.Org Server Extension : 4.0
[    17.687] (--) PCI:*(0:1:0:0) 1002:4c66:1028:011d rev 2, Mem @ 0xe8000000/134217728, 0xfcff0000/65536, I/O @ 0x0000c000/256, BIOS @ 0x????????/131072
[    17.688] (II) Open ACPI successful (/var/run/acpid.socket)
[    17.688] (II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
[    17.688] (II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
[    17.688] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    17.688] (II) "record" will be loaded by default.
[    17.688] (II) "dri" will be loaded. This was enabled by default and also specified in the config file.
[    17.688] (II) "dri2" will be loaded. This was enabled by default and also specified in the config file.
[    17.688] (II) LoadModule: "dri2"
[    17.713] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    17.713] (II) Module dri2: vendor="X.Org Foundation"
[    17.713] 	compiled for 1.9.0, module version = 1.2.0
[    17.713] 	ABI class: X.Org Server Extension, version 4.0
[    17.713] (II) Loading extension DRI2
[    17.714] (II) LoadModule: "dri"
[    17.714] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    17.714] (II) Module dri: vendor="X.Org Foundation"
[    17.714] 	compiled for 1.9.0, module version = 1.0.0
[    17.714] 	ABI class: X.Org Server Extension, version 4.0
[    17.714] (II) Loading extension XFree86-DRI
[    17.714] (II) LoadModule: "dbe"
[    17.714] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    17.714] (II) Module dbe: vendor="X.Org Foundation"
[    17.714] 	compiled for 1.9.0, module version = 1.0.0
[    17.714] 	Module class: X.Org Server Extension
[    17.714] 	ABI class: X.Org Server Extension, version 4.0
[    17.714] (II) Loading extension DOUBLE-BUFFER
[    17.714] (II) LoadModule: "extmod"
[    17.715] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    17.715] (II) Module extmod: vendor="X.Org Foundation"
[    17.715] 	compiled for 1.9.0, module version = 1.0.0
[    17.715] 	Module class: X.Org Server Extension
[    17.715] 	ABI class: X.Org Server Extension, version 4.0
[    17.715] (II) Loading extension MIT-SCREEN-SAVER
[    17.715] (II) Loading extension XFree86-VidModeExtension
[    17.715] (II) Loading extension XFree86-DGA
[    17.715] (II) Loading extension DPMS
[    17.715] (II) Loading extension XVideo
[    17.715] (II) Loading extension XVideo-MotionCompensation
[    17.715] (II) Loading extension X-Resource
[    17.715] (II) LoadModule: "glx"
[    17.715] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    17.715] (II) Module glx: vendor="X.Org Foundation"
[    17.715] 	compiled for 1.9.0, module version = 1.0.0
[    17.715] 	ABI class: X.Org Server Extension, version 4.0
[    17.715] (==) AIGLX enabled
[    17.715] (II) Loading extension GLX
[    17.715] (II) LoadModule: "record"
[    17.716] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    17.716] (II) Module record: vendor="X.Org Foundation"
[    17.716] 	compiled for 1.9.0, module version = 1.13.0
[    17.716] 	Module class: X.Org Server Extension
[    17.716] 	ABI class: X.Org Server Extension, version 4.0
[    17.716] (II) Loading extension RECORD
[    17.716] (II) LoadModule: "radeon"
[    17.716] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    17.717] (II) Module radeon: vendor="X.Org Foundation"
[    17.717] 	compiled for 1.9.0, module version = 6.13.1
[    17.717] 	Module class: X.Org Video Driver
[    17.717] 	ABI class: X.Org Video Driver, version 8.0
[    17.717] (II) RADEON: Driver for ATI Radeon chipsets:
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
	ATI Radeon 8500 AIW BB (AGP), ATI Radeon 8500 AIW BC (AGP),
	ATI Radeon IGP320M (U1) 4336, ATI Radeon IGP330M/340M/350M (U2) 4337,
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
	ATI Radeon 3000 Graphics, ATI Radeon HD 4200, ATI Radeon 4100,
	ATI Mobility Radeon HD 4200, ATI Mobility Radeon 4100,
	ATI Radeon HD 4290, ATI Radeon HD 4290, CYPRESS,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5900 Series, ATI Radeon HD 5900 Series,
	ATI Mobility Radeon HD 5800 Series,
	ATI Mobility Radeon HD 5800 Series,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
	ATI Radeon HD 5700 Series, ATI Radeon HD 5700 Series,
	ATI Mobility Radeon HD 5000 Series,
	ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5670,
	ATI Radeon HD 5570, ATI Radeon HD 5500 Series, REDWOOD,
	ATI Mobility Radeon HD 5000 Series,
	ATI Mobility Radeon HD 5000 Series, CEDAR, CEDAR, CEDAR,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, CEDAR, ATI Radeon HD 5450,
	CEDAR
[    17.739] (++) using VT number 7

[    17.739] (II) [KMS] Kernel modesetting enabled.
[    17.739] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    17.739] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    17.739] (==) RADEON(0): Default visual is TrueColor
[    17.739] (**) RADEON(0): Option "accel" "True"
[    17.739] (**) RADEON(0): Option "EnablePageFlip" "True"
[    17.739] (**) RADEON(0): Option "AccelDFS" "True"
[    17.739] (**) RADEON(0): Option "ColorTiling" "True"
[    17.739] (**) RADEON(0): Option "RenderAccel" "True"
[    17.739] (**) RADEON(0): Option "AccelMethod" "EXA"
[    17.739] (**) RADEON(0): Option "DRI" "True"
[    17.739] (==) RADEON(0): RGB weight 888
[    17.740] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    17.740] (--) RADEON(0): Chipset: "ATI Radeon Mobility 9000 (M9) Lf (AGP)" (ChipID = 0x4c66)
[    17.740] (II) RADEON(0): AGP card detected
[    17.740] (II) RADEON(0): KMS Color Tiling: enabled
[    17.740] drmOpenDevice: node name is /dev/dri/card0
[    17.740] drmOpenDevice: open result is 9, (OK)
[    17.740] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[    17.740] drmOpenDevice: node name is /dev/dri/card0
[    17.740] drmOpenDevice: open result is 9, (OK)
[    17.740] drmOpenByBusid: drmOpenMinor returns 9
[    17.740] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[    17.750] (II) RADEON(0): Output VGA-0 using monitor section Monitor0
[    17.763] (II) RADEON(0): Output DVI-0 has no monitor section
[    17.763] (II) RADEON(0): Output LVDS has no monitor section
[    17.774] (II) RADEON(0): Output S-video has no monitor section
[    17.785] (II) RADEON(0): EDID for output VGA-0
[    17.805] (II) RADEON(0): EDID for output DVI-0
[    17.805] (II) RADEON(0): EDID for output LVDS
[    17.805] (II) RADEON(0): Not using default mode "640x350" (vrefresh out of range)
[    17.805] (II) RADEON(0): Not using default mode "320x175" (doublescan mode not supported)
[    17.805] (II) RADEON(0): Not using default mode "640x400" (vrefresh out of range)
[    17.805] (II) RADEON(0): Not using default mode "320x200" (doublescan mode not supported)
[    17.805] (II) RADEON(0): Not using default mode "720x400" (vrefresh out of range)
[    17.805] (II) RADEON(0): Not using default mode "360x200" (doublescan mode not supported)
[    17.805] (II) RADEON(0): Not using default mode "320x240" (doublescan mode not supported)
[    17.805] (II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
[    17.805] (II) RADEON(0): Not using default mode "320x240" (doublescan mode not supported)
[    17.805] (II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
[    17.805] (II) RADEON(0): Not using default mode "320x240" (doublescan mode not supported)
[    17.805] (II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
[    17.805] (II) RADEON(0): Not using default mode "320x240" (doublescan mode not supported)
[    17.805] (II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
[    17.805] (II) RADEON(0): Not using default mode "400x300" (doublescan mode not supported)
[    17.805] (II) RADEON(0): Not using default mode "400x300" (doublescan mode not supported)
[    17.805] (II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
[    17.805] (II) RADEON(0): Not using default mode "400x300" (doublescan mode not supported)
[    17.805] (II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
[    17.805] (II) RADEON(0): Not using default mode "400x300" (doublescan mode not supported)
[    17.805] (II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
[    17.805] (II) RADEON(0): Not using default mode "400x300" (doublescan mode not supported)
[    17.805] (II) RADEON(0): Not using default mode "1024x768i" (interlace mode not supported)
[    17.805] (II) RADEON(0): Not using default mode "512x384i" (doublescan mode not supported)
[    17.805] (II) RADEON(0): Not using default mode "512x384" (doublescan mode not supported)
[    17.805] (II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
[    17.805] (II) RADEON(0): Not using default mode "512x384" (doublescan mode not supported)
[    17.805] (II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
[    17.805] (II) RADEON(0): Not using default mode "512x384" (doublescan mode not supported)
[    17.805] (II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
[    17.805] (II) RADEON(0): Not using default mode "512x384" (doublescan mode not supported)
[    17.806] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[    17.806] (II) RADEON(0): Not using default mode "576x432" (doublescan mode not supported)
[    17.806] (II) RADEON(0): Not using default mode "1280x960" (hsync out of range)
[    17.806] (II) RADEON(0): Not using default mode "640x480" (doublescan mode not supported)
[    17.806] (II) RADEON(0): Not using default mode "1280x960" (vrefresh out of range)
[    17.806] (II) RADEON(0): Not using default mode "640x480" (doublescan mode not supported)
[    17.806] (II) RADEON(0): Not using default mode "1280x1024" (hsync out of range)
[    17.806] (II) RADEON(0): Not using default mode "640x512" (doublescan mode not supported)
[    17.806] (II) RADEON(0): Not using default mode "1280x1024" (vrefresh out of range)
[    17.806] (II) RADEON(0): Not using default mode "640x512" (doublescan mode not supported)
[    17.806] (II) RADEON(0): Not using default mode "1280x1024" (vrefresh out of range)
[    17.806] (II) RADEON(0): Not using default mode "640x512" (doublescan mode not supported)
[    17.806] (II) RADEON(0): Not using default mode "1600x1200" (hsync out of range)
[    17.806] (II) RADEON(0): Not using default mode "800x600" (doublescan mode not supported)
[    17.806] (II) RADEON(0): Not using default mode "1600x1200" (vrefresh out of range)
[    17.806] (II) RADEON(0): Not using default mode "800x600" (doublescan mode not supported)
[    17.806] (II) RADEON(0): Not using default mode "1600x1200" (vrefresh out of range)
[    17.806] (II) RADEON(0): Not using default mode "800x600" (doublescan mode not supported)
[    17.806] (II) RADEON(0): Not using default mode "1600x1200" (vrefresh out of range)
[    17.806] (II) RADEON(0): Not using default mode "800x600" (doublescan mode not supported)
[    17.806] (II) RADEON(0): Not using default mode "1600x1200" (vrefresh out of range)
[    17.806] (II) RADEON(0): Not using default mode "800x600" (doublescan mode not supported)
[    17.806] (II) RADEON(0): Not using default mode "1792x1344" (hsync out of range)
[    17.806] (II) RADEON(0): Not using default mode "896x672" (doublescan mode not supported)
[    17.806] (II) RADEON(0): Not using default mode "1792x1344" (vrefresh out of range)
[    17.806] (II) RADEON(0): Not using default mode "896x672" (doublescan mode not supported)
[    17.806] (II) RADEON(0): Not using default mode "1856x1392" (hsync out of range)
[    17.806] (II) RADEON(0): Not using default mode "928x696" (doublescan mode not supported)
[    17.806] (II) RADEON(0): Not using default mode "1856x1392" (vrefresh out of range)
[    17.806] (II) RADEON(0): Not using default mode "928x696" (doublescan mode not supported)
[    17.806] (II) RADEON(0): Not using default mode "1920x1440" (hsync out of range)
[    17.806] (II) RADEON(0): Not using default mode "960x720" (doublescan mode not supported)
[    17.806] (II) RADEON(0): Not using default mode "1920x1440" (vrefresh out of range)
[    17.806] (II) RADEON(0): Not using default mode "960x720" (doublescan mode not supported)
[    17.806] (II) RADEON(0): Not using default mode "832x624" (vrefresh out of range)
[    17.806] (II) RADEON(0): Not using default mode "416x312" (doublescan mode not supported)
[    17.806] (II) RADEON(0): Not using default mode "1152x864" (hsync out of range)
[    17.806] (II) RADEON(0): Not using default mode "576x432" (doublescan mode not supported)
[    17.806] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[    17.806] (II) RADEON(0): Not using default mode "576x432" (doublescan mode not supported)
[    17.806] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[    17.806] (II) RADEON(0): Not using default mode "576x432" (doublescan mode not supported)
[    17.806] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[    17.806] (II) RADEON(0): Not using default mode "576x432" (doublescan mode not supported)
[    17.806] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[    17.806] (II) RADEON(0): Not using default mode "576x432" (doublescan mode not supported)
[    17.806] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[    17.806] (II) RADEON(0): Not using default mode "576x432" (doublescan mode not supported)
[    17.806] (II) RADEON(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
[    17.806] (II) RADEON(0): Not using default mode "680x384" (doublescan mode not supported)
[    17.806] (II) RADEON(0): Not using default mode "680x384" (doublescan mode not supported)
[    17.806] (II) RADEON(0): Not using default mode "1400x1050" (hsync out of range)
[    17.806] (II) RADEON(0): Not using default mode "700x525" (doublescan mode not supported)
[    17.806] (II) RADEON(0): Not using default mode "1400x1050" (vrefresh out of range)
[    17.806] (II) RADEON(0): Not using default mode "700x525" (doublescan mode not supported)
[    17.806] (II) RADEON(0): Not using default mode "1400x1050" (vrefresh out of range)
[    17.806] (II) RADEON(0): Not using default mode "700x525" (doublescan mode not supported)
[    17.806] (II) RADEON(0): Not using default mode "1400x1050" (vrefresh out of range)
[    17.806] (II) RADEON(0): Not using default mode "700x525" (doublescan mode not supported)
[    17.806] (II) RADEON(0): Not using default mode "1440x900" (hsync out of range)
[    17.806] (II) RADEON(0): Not using default mode "720x450" (doublescan mode not supported)
[    17.806] (II) RADEON(0): Not using default mode "1600x1024" (hsync out of range)
[    17.806] (II) RADEON(0): Not using default mode "800x512" (doublescan mode not supported)
[    17.807] (II) RADEON(0): Not using default mode "1680x1050" (hsync out of range)
[    17.807] (II) RADEON(0): Not using default mode "840x525" (doublescan mode not supported)
[    17.807] (II) RADEON(0): Not using default mode "1680x1050" (hsync out of range)
[    17.807] (II) RADEON(0): Not using default mode "840x525" (doublescan mode not supported)
[    17.807] (II) RADEON(0): Not using default mode "1680x1050" (vrefresh out of range)
[    17.807] (II) RADEON(0): Not using default mode "840x525" (doublescan mode not supported)
[    17.807] (II) RADEON(0): Not using default mode "1680x1050" (vrefresh out of range)
[    17.807] (II) RADEON(0): Not using default mode "840x525" (doublescan mode not supported)
[    17.807] (II) RADEON(0): Not using default mode "1680x1050" (vrefresh out of range)
[    17.807] (II) RADEON(0): Not using default mode "840x525" (doublescan mode not supported)
[    17.807] (II) RADEON(0): Not using default mode "1920x1080" (hsync out of range)
[    17.807] (II) RADEON(0): Not using default mode "960x540" (doublescan mode not supported)
[    17.807] (II) RADEON(0): Not using default mode "1920x1200" (hsync out of range)
[    17.807] (II) RADEON(0): Not using default mode "960x600" (doublescan mode not supported)
[    17.807] (II) RADEON(0): Not using default mode "1920x1440" (vrefresh out of range)
[    17.807] (II) RADEON(0): Not using default mode "960x720" (doublescan mode not supported)
[    17.807] (II) RADEON(0): Not using default mode "2048x1536" (hsync out of range)
[    17.807] (II) RADEON(0): Not using default mode "1024x768" (doublescan mode not supported)
[    17.807] (II) RADEON(0): Not using default mode "2048x1536" (vrefresh out of range)
[    17.807] (II) RADEON(0): Not using default mode "1024x768" (doublescan mode not supported)
[    17.807] (II) RADEON(0): Not using default mode "2048x1536" (vrefresh out of range)
[    17.807] (II) RADEON(0): Not using default mode "1024x768" (doublescan mode not supported)
[    17.807] (II) RADEON(0): Printing probed modes for output LVDS
[    17.807] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 (48.4 kHz)
[    17.807] (II) RADEON(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    17.807] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    17.807] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    17.807] (II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
[    17.807] (II) RADEON(0): Modeline "848x480"x59.7   31.50  848 872 952 1056  480 483 493 500 -hsync +vsync (29.8 kHz)
[    17.807] (II) RADEON(0): Modeline "720x480"x59.7   26.75  720 744 808 896  480 483 493 500 -hsync +vsync (29.9 kHz)
[    17.807] (II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    17.807] (II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
[    17.814] (II) RADEON(0): EDID for output S-video
[    17.814] (II) RADEON(0): Output VGA-0 disconnected
[    17.814] (II) RADEON(0): Output DVI-0 disconnected
[    17.814] (II) RADEON(0): Output LVDS connected
[    17.814] (II) RADEON(0): Output S-video disconnected
[    17.814] (II) RADEON(0): Using exact sizes for initial modes
[    17.814] (II) RADEON(0): Output LVDS using initial mode 1024x768
[    17.814] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    17.814] (II) RADEON(0): mem size init: gart size :7dff000 vram size: s:2000000 visible:1f00000
[    17.814] (II) RADEON(0): EXA: Driver will not allow EXA pixmaps in VRAM
[    17.814] (==) RADEON(0): DPI set to (96, 96)
[    17.814] (II) Loading sub module "fb"
[    17.814] (II) LoadModule: "fb"
[    17.815] (II) Loading /usr/lib/xorg/modules/libfb.so
[    17.815] (II) Module fb: vendor="X.Org Foundation"
[    17.815] 	compiled for 1.9.0, module version = 1.0.0
[    17.815] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    17.815] (II) Loading sub module "ramdac"
[    17.815] (II) LoadModule: "ramdac"
[    17.815] (II) Module "ramdac" already built-in
[    17.815] (II) Loading sub module "exa"
[    17.815] (II) LoadModule: "exa"
[    17.815] (II) Loading /usr/lib/xorg/modules/libexa.so
[    17.815] (II) Module exa: vendor="X.Org Foundation"
[    17.815] 	compiled for 1.9.0, module version = 2.5.0
[    17.815] 	ABI class: X.Org Video Driver, version 8.0
[    17.815] (--) Depth 24 pixmap format is 32 bpp
[    17.815] (II) RADEON(0): [DRI2] Setup complete
[    17.815] (II) RADEON(0): [DRI2]   DRI driver: r200
[    17.820] (II) RADEON(0): Front buffer size: 3072K
[    17.820] (II) RADEON(0): VRAM usage limit set to 25804K
[    17.820] (**) RADEON(0): Option "BackingStore" "true"
[    17.820] (**) RADEON(0): Backing store enabled
[    17.820] (II) RADEON(0): Direct rendering enabled
[    17.820] (II) RADEON(0): Render acceleration enabled for R200 type cards.
[    17.820] (II) RADEON(0): Setting EXA maxPitchBytes
[    17.820] (**) RADEON(0): Option "EXANoComposite" "No"
[    17.820] (**) RADEON(0): Option "EXAOptimizeMigration" "true"
[    17.820] (II) EXA(0): Driver allocated offscreen pixmaps
[    17.820] (II) EXA(0): Driver registered support for the following operations:
[    17.820] (II)         Solid
[    17.820] (II)         Copy
[    17.820] (II)         Composite (RENDER acceleration)
[    17.820] (II)         UploadToScreen
[    17.820] (II)         DownloadFromScreen
[    17.820] (II) RADEON(0): Acceleration enabled
[    17.820] (==) RADEON(0): DPMS enabled
[    17.820] (==) RADEON(0): Silken mouse enabled
[    17.820] (II) RADEON(0): Set up textured video
[    17.820] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    17.821] (WW) RADEON(0): Option "EnableDepthMoves" is not used
[    17.821] (WW) RADEON(0): Option "DMAForXv" is not used
[    17.821] (WW) RADEON(0): Option "VGAAccess" is not used
[    17.821] (WW) RADEON(0): Option "MigrationHeuristics" is not used
[    17.821] (WW) RADEON(0): Option "TripleBuffer" is not used
[    17.821] (--) RandR disabled
[    17.821] (II) Initializing built-in extension Generic Event Extension
[    17.821] (II) Initializing built-in extension SHAPE
[    17.821] (II) Initializing built-in extension MIT-SHM
[    17.821] (II) Initializing built-in extension XInputExtension
[    17.821] (II) Initializing built-in extension XTEST
[    17.821] (II) Initializing built-in extension BIG-REQUESTS
[    17.821] (II) Initializing built-in extension SYNC
[    17.821] (II) Initializing built-in extension XKEYBOARD
[    17.821] (II) Initializing built-in extension XC-MISC
[    17.821] (II) Initializing built-in extension SECURITY
[    17.821] (II) Initializing built-in extension XINERAMA
[    17.821] (II) Initializing built-in extension XFIXES
[    17.821] (II) Initializing built-in extension RENDER
[    17.821] (II) Initializing built-in extension RANDR
[    17.821] (II) Initializing built-in extension COMPOSITE
[    17.821] (II) Initializing built-in extension DAMAGE
[    17.821] (II) Initializing built-in extension GESTURE
[    17.860] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    17.860] (II) AIGLX: enabled GLX_INTEL_swap_event
[    17.860] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    17.860] (II) AIGLX: enabled GLX_SGI_make_current_read
[    17.860] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    17.860] (II) AIGLX: Loaded and initialized /usr/lib/dri/r200_dri.so
[    17.860] (II) GLX: Initialized DRI2 GL provider for screen 0
[    17.861] (II) RADEON(0): Setting screen physical size to 270 x 203
[    17.902] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    17.920] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[    17.920] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    17.920] (II) LoadModule: "evdev"
[    17.921] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.921] (II) Module evdev: vendor="X.Org Foundation"
[    17.921] 	compiled for 1.9.0, module version = 2.3.2
[    17.921] 	Module class: X.Org XInput Driver
[    17.921] 	ABI class: X.Org XInput driver, version 11.0
[    17.921] (**) Video Bus: always reports core events
[    17.921] (**) Video Bus: Device: "/dev/input/event4"
[    17.921] (II) Video Bus: Found keys
[    17.921] (II) Video Bus: Configuring as keyboard
[    17.921] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    17.921] (**) Option "xkb_rules" "evdev"
[    17.921] (**) Option "xkb_model" "pc105"
[    17.921] (**) Option "xkb_layout" "us"
[    17.922] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    17.922] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    17.922] (**) Power Button: always reports core events
[    17.922] (**) Power Button: Device: "/dev/input/event1"
[    17.922] (II) Power Button: Found keys
[    17.922] (II) Power Button: Configuring as keyboard
[    17.922] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    17.922] (**) Option "xkb_rules" "evdev"
[    17.922] (**) Option "xkb_model" "pc105"
[    17.922] (**) Option "xkb_layout" "us"
[    17.923] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    17.923] (II) No input driver/identifier specified (ignoring)
[    17.923] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    17.923] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    17.923] (**) Sleep Button: always reports core events
[    17.923] (**) Sleep Button: Device: "/dev/input/event2"
[    17.923] (II) Sleep Button: Found keys
[    17.923] (II) Sleep Button: Configuring as keyboard
[    17.923] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    17.923] (**) Option "xkb_rules" "evdev"
[    17.923] (**) Option "xkb_model" "pc105"
[    17.928] (**) Option "xkb_layout" "us"
[    17.934] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    17.934] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    17.934] (**) AT Translated Set 2 keyboard: always reports core events
[    17.934] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    17.934] (II) AT Translated Set 2 keyboard: Found keys
[    17.934] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    17.934] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    17.934] (**) Option "xkb_rules" "evdev"
[    17.934] (**) Option "xkb_model" "pc105"
[    17.934] (**) Option "xkb_layout" "us"
[    17.934] (II) config/udev: Adding input device PS/2 Mouse (/dev/input/event5)
[    17.934] (**) PS/2 Mouse: Applying InputClass "evdev pointer catchall"
[    17.935] (**) PS/2 Mouse: always reports core events
[    17.935] (**) PS/2 Mouse: Device: "/dev/input/event5"
[    17.935] (II) PS/2 Mouse: Found 3 mouse buttons
[    17.935] (II) PS/2 Mouse: Found relative axes
[    17.935] (II) PS/2 Mouse: Found x and y relative axes
[    17.935] (II) PS/2 Mouse: Configuring as mouse
[    17.935] (**) PS/2 Mouse: YAxisMapping: buttons 4 and 5
[    17.935] (**) PS/2 Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    17.935] (II) XINPUT: Adding extended input device "PS/2 Mouse" (type: MOUSE)
[    17.935] (II) PS/2 Mouse: initialized for relative axes.
[    17.935] (II) config/udev: Adding input device PS/2 Mouse (/dev/input/mouse0)
[    17.935] (II) No input driver/identifier specified (ignoring)
[    17.935] (II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/event6)
[    17.935] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "evdev touchpad catchall"
[    17.935] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "touchpad catchall"
[    17.937] (II) LoadModule: "synaptics"
[    17.937] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    17.937] (II) Module synaptics: vendor="X.Org Foundation"
[    17.937] 	compiled for 1.9.0, module version = 1.2.2
[    17.937] 	Module class: X.Org XInput Driver
[    17.937] 	ABI class: X.Org XInput driver, version 11.0
[    17.937] (II) Synaptics touchpad driver version 1.2.2
[    17.937] (**) Option "Device" "/dev/input/event6"
[    17.937] (II) AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023
[    17.937] (II) AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767
[    17.937] (II) AlpsPS/2 ALPS GlidePoint: pressure range 0 - 127
[    17.937] (II) AlpsPS/2 ALPS GlidePoint: finger width range 0 - 0
[    17.938] (II) AlpsPS/2 ALPS GlidePoint: buttons: left right middle
[    17.938] (--) AlpsPS/2 ALPS GlidePoint: touchpad found
[    17.938] (**) AlpsPS/2 ALPS GlidePoint: always reports core events
[    17.938] (II) XINPUT: Adding extended input device "AlpsPS/2 ALPS GlidePoint" (type: TOUCHPAD)
[    17.938] (**) AlpsPS/2 ALPS GlidePoint: (accel) keeping acceleration scheme 1
[    17.938] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration profile 0
[    17.938] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration factor: 2.000
[    17.938] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration threshold: 4
[    17.938] (--) AlpsPS/2 ALPS GlidePoint: touchpad found
[    17.938] (II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/mouse1)
[    17.938] (II) No input driver/identifier specified (ignoring)
```

---

### Post by Yellow Pasque on 2010-11-08
Specify the vertrefresh and horizsync in Monitor section. The values below are examples. Try to find the specs for your display.
```
Section "Monitor"
Identifier "Monitor0"
HorizSync 30 - 82
VertRefresh 50 - 75 
EndSection
```

Add this line to the Device section:
```
Option "Monitor-LVDS" "Monitor0"
```

---

### Post by thenellt on 2010-11-08
I tried adding this:
 Modeline "1360x768"x59.8 84.75 1360 1432 1568 1776 768 771 781 798 -hsync +vsync
Because that was listed as a supported one in that log file, but that doesn't work (get weird stripy bars and no desktop)
I added the other stuff, but still no luck getting over 1024x768.
This screen is supposed to support 1440x1050, but would be happy with 1280x1024 or 1360xsomething.

---

### Post by Yellow Pasque on 2010-11-08
Can you post an update /var/log/Xorg.0.log (please use [ code ][ /code ] this time)

---

### Post by thenellt on 2010-11-10
```

[    18.253] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    18.253] X Protocol Version 11, Revision 0
[    18.253] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[    18.253] Current Operating System: Linux thenellt-server 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:36:48 UTC 2010 i686
[    18.253] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=b835a5cb-65a6-4c05-8fbf-173f05530205 ro quiet splash
[    18.253] Build Date: 16 September 2010  05:39:22PM
[    18.253] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
[    18.253] Current version of pixman: 0.18.4
[    18.253] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    18.253] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    18.253] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Nov 10 17:18:44 2010
[    18.254] (==) Using config file: "/etc/X11/xorg.conf"
[    18.254] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    18.254] Parse error on line 16 of section Monitor in file /etc/X11/xorg.conf
	ModeLine dotclock expected
[    18.254] (EE) Problem parsing the config file
[    18.254] (EE) Error parsing the config file
[    18.254] 
Fatal server error:
[    18.254] no screens found
[    18.254] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[    18.254] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    18.254] 
[    18.254]  ddxSigGiveUp: Closing log

```

---

### Post by Yellow Pasque on 2010-11-10
> [    18.254] Parse error on line 16 of section Monitor in file /etc/X11/xorg.conf
	ModeLine dotclock expected
[    18.254] (EE) Problem parsing the config file
[    18.254] (EE) Error parsing the config file

So look at line 16 of xorg.conf

---

### Post by thenellt on 2010-11-10
Line 16 is in the monitor section and there currently isn't much in there. I don't know why there's an error.

---

