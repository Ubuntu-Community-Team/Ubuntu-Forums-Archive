---
title: "ati x2300 driver"
date: 2011-04-11
forum: Hardware
---

### Post by set4812 on 2011-04-11
I need driver to play wow, in low graphic mode in game i have max 10 fps
my xorg file
> [    20.317] 
X.Org X Server 1.9.2.901 (1.9.3 RC 1)
Release Date: 2010-11-13
[    20.318] X Protocol Version 11, Revision 0
[    20.318] Build Operating System: Linux 2.6.24-28-xen i686 Ubuntu
[    20.318] Current Operating System: Linux set 2.6.35-28-generic #49-Ubuntu SMP Tue Mar 1 14:40:58 UTC 2011 i686
[    20.318] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-28-generic root=UUID=4b009280-e01d-4975-a3ee-8ed1997ea694 ro quiet splash
[    20.318] Build Date: 29 November 2010  03:29:38PM
[    20.318] xorg-server 2:1.9.2.901+git20101129+server-1.9-branch.65f2ab20-0ubuntu0sarvatt2~maverick (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    20.318] Current version of pixman: 0.21.4
[    20.318] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[    20.318] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    20.318] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Apr 11 22:03:40 2011
[    20.328] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    20.328] (==) No Layout section.  Using the first Screen section.
[    20.328] (==) No screen section available. Using defaults.
[    20.329] (**) |-->Screen "Default Screen Section" (0)
[    20.329] (**) |   |-->Monitor "<default monitor>"
[    20.329] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    20.329] (==) Automatically adding devices
[    20.329] (==) Automatically enabling devices
[    20.329] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    20.329] 	Entry deleted from font path.
[    20.329] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    20.329] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    20.329] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    20.329] (II) Loader magic: 0x81fa7c0
[    20.329] (II) Module ABI versions:
[    20.329] 	X.Org ANSI C Emulation: 0.4
[    20.329] 	X.Org Video Driver: 8.0
[    20.329] 	X.Org XInput driver : 11.0
[    20.329] 	X.Org Server Extension : 4.0
[    20.330] (--) PCI:*(0:1:0:0) 1002:718a:1043:1449 rev 0, Mem @ 0xd0000000/134217728, 0xfa9f0000/65536, I/O @ 0x0000a800/256, BIOS @ 0x????????/131072
[    20.330] (II) Open ACPI successful (/var/run/acpid.socket)
[    20.331] (II) LoadModule: "extmod"
[    20.337] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    20.338] (II) Module extmod: vendor="X.Org Foundation"
[    20.338] 	compiled for 1.9.2.901, module version = 1.0.0
[    20.338] 	Module class: X.Org Server Extension
[    20.338] 	ABI class: X.Org Server Extension, version 4.0
[    20.338] (II) Loading extension MIT-SCREEN-SAVER
[    20.338] (II) Loading extension XFree86-VidModeExtension
[    20.338] (II) Loading extension XFree86-DGA
[    20.338] (II) Loading extension DPMS
[    20.338] (II) Loading extension XVideo
[    20.338] (II) Loading extension XVideo-MotionCompensation
[    20.338] (II) Loading extension X-Resource
[    20.338] (II) LoadModule: "dbe"
[    20.338] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    20.338] (II) Module dbe: vendor="X.Org Foundation"
[    20.338] 	compiled for 1.9.2.901, module version = 1.0.0
[    20.338] 	Module class: X.Org Server Extension
[    20.338] 	ABI class: X.Org Server Extension, version 4.0
[    20.338] (II) Loading extension DOUBLE-BUFFER
[    20.338] (II) LoadModule: "glx"
[    20.339] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    20.339] (II) Module glx: vendor="X.Org Foundation"
[    20.339] 	compiled for 1.9.2.901, module version = 1.0.0
[    20.339] 	ABI class: X.Org Server Extension, version 4.0
[    20.339] (==) AIGLX enabled
[    20.339] (II) Loading extension GLX
[    20.339] (II) LoadModule: "record"
[    20.339] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    20.340] (II) Module record: vendor="X.Org Foundation"
[    20.340] 	compiled for 1.9.2.901, module version = 1.13.0
[    20.340] 	Module class: X.Org Server Extension
[    20.340] 	ABI class: X.Org Server Extension, version 4.0
[    20.340] (II) Loading extension RECORD
[    20.340] (II) LoadModule: "dri"
[    20.340] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    20.340] (II) Module dri: vendor="X.Org Foundation"
[    20.340] 	compiled for 1.9.2.901, module version = 1.0.0
[    20.340] 	ABI class: X.Org Server Extension, version 4.0
[    20.340] (II) Loading extension XFree86-DRI
[    20.340] (II) LoadModule: "dri2"
[    20.341] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    20.341] (II) Module dri2: vendor="X.Org Foundation"
[    20.341] 	compiled for 1.9.2.901, module version = 1.2.0
[    20.341] 	ABI class: X.Org Server Extension, version 4.0
[    20.341] (II) Loading extension DRI2
[    20.341] (==) Matched fglrx as autoconfigured driver 0
[    20.341] (==) Matched ati as autoconfigured driver 1
[    20.341] (==) Matched vesa as autoconfigured driver 2
[    20.341] (==) Matched fbdev as autoconfigured driver 3
[    20.341] (==) Assigned the driver to the xf86ConfigLayout
[    20.341] (II) LoadModule: "fglrx"
[    20.342] (WW) Warning, couldn't open module fglrx
[    20.342] (II) UnloadModule: "fglrx"
[    20.342] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    20.343] (II) LoadModule: "ati"
[    20.343] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    20.343] (II) Module ati: vendor="X.Org Foundation"
[    20.343] 	compiled for 1.9.2.901, module version = 6.14.99
[    20.343] 	Module class: X.Org Video Driver
[    20.343] 	ABI class: X.Org Video Driver, version 8.0
[    20.343] (II) LoadModule: "radeon"
[    20.344] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    20.344] (II) Module radeon: vendor="X.Org Foundation"
[    20.344] 	compiled for 1.9.2.901, module version = 6.14.99
[    20.344] 	Module class: X.Org Video Driver
[    20.344] 	ABI class: X.Org Video Driver, version 8.0
[    20.344] (II) LoadModule: "vesa"
[    20.345] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    20.345] (II) Module vesa: vendor="X.Org Foundation"
[    20.345] 	compiled for 1.9.2.901, module version = 2.3.0
[    20.345] 	Module class: X.Org Video Driver
[    20.345] 	ABI class: X.Org Video Driver, version 8.0
[    20.345] (II) LoadModule: "fbdev"
[    20.345] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    20.345] (II) Module fbdev: vendor="X.Org Foundation"
[    20.345] 	compiled for 1.8.99.904, module version = 0.4.2
[    20.346] 	ABI class: X.Org Video Driver, version 8.0
[    20.346] (II) RADEON: Driver for ATI Radeon chipsets:
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
	ATI Radeon HD 4290, ATI Radeon HD 4250, AMD Radeon HD 6310 Graphics,
	AMD Radeon HD 6310 Graphics, AMD Radeon HD 6250 Graphics,
	AMD Radeon HD 6250 Graphics, CYPRESS,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, AMD Firestream 9370,
	AMD Firestream 9350, ATI Radeon HD 5800 Series,
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
	ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon Graphics,
	ATI Mobility Radeon Graphics, CEDAR,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, ATI FirePro 2270, CEDAR,
	ATI Radeon HD 5450, CEDAR, CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
	CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN, AMD Radeon HD 6900 Series,
	AMD Radeon HD 6900 Series, CAYMAN, CAYMAN,
	AMD Radeon HD 6900M Series, Mobility Radeon HD 6000 Series, BARTS,
	BARTS, Mobility Radeon HD 6000 Series,
	Mobility Radeon HD 6000 Series, BARTS, BARTS, BARTS, BARTS,
	AMD Radeon HD 6800 Series, AMD Radeon HD 6800 Series, TURKS, TURKS,
	TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
	TURKS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
	CAICOS, CAICOS, CAICOS, CAICOS
[    20.356] (II) VESA: driver for VESA chipsets: vesa
[    20.356] (II) FBDEV: driver for framebuffer: fbdev
[    20.356] (++) using VT number 7

[    20.356] (II) [KMS] Kernel modesetting enabled.
[    20.356] (WW) Falling back to old probe method for vesa
[    20.356] (WW) Falling back to old probe method for fbdev
[    20.356] (II) Loading sub module "fbdevhw"
[    20.356] (II) LoadModule: "fbdevhw"
[    20.357] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    20.357] (II) Module fbdevhw: vendor="X.Org Foundation"
[    20.357] 	compiled for 1.9.2.901, module version = 0.0.2
[    20.357] 	ABI class: X.Org Video Driver, version 8.0
[    20.357] (II) RADEON(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    20.357] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    20.357] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    20.357] (==) RADEON(0): Default visual is TrueColor
[    20.357] (==) RADEON(0): RGB weight 888
[    20.357] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    20.357] (--) RADEON(0): Chipset: "ATI Mobility Radeon X2300" (ChipID = 0x718a)
[    20.358] (II) RADEON(0): PCIE card detected
[    20.358] drmOpenDevice: node name is /dev/dri/card0
[    20.358] drmOpenDevice: open result is 9, (OK)
[    20.358] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[    20.358] drmOpenDevice: node name is /dev/dri/card0
[    20.358] drmOpenDevice: open result is 9, (OK)
[    20.358] drmOpenByBusid: drmOpenMinor returns 9
[    20.358] drmOpenByBusid: Interface 1.4 failed, trying 1.1
[    20.358] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[    20.358] (II) Loading sub module "exa"
[    20.358] (II) LoadModule: "exa"
[    20.358] (II) Loading /usr/lib/xorg/modules/libexa.so
[    20.358] (II) Module exa: vendor="X.Org Foundation"
[    20.358] 	compiled for 1.9.2.901, module version = 2.5.0
[    20.358] 	ABI class: X.Org Video Driver, version 8.0
[    20.358] (II) RADEON(0): KMS Color Tiling: enabled
[    20.358] (II) RADEON(0): SwapBuffers wait for vsync: enabled
[    20.388] (II) RADEON(0): Output VGA-0 has no monitor section
[    20.388] (II) RADEON(0): Output LVDS has no monitor section
[    20.392] (II) RADEON(0): Output DVI-0 has no monitor section
[    20.427] (II) RADEON(0): EDID for output VGA-0
[    20.427] (II) RADEON(0): EDID for output LVDS
[    20.428] (II) RADEON(0): Manufacturer: LPL  Model: e300  Serial#: 0
[    20.428] (II) RADEON(0): Year: 2006  Week: 0
[    20.428] (II) RADEON(0): EDID Version: 1.3
[    20.428] (II) RADEON(0): Digital Display Input
[    20.428] (II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
[    20.428] (II) RADEON(0): Gamma: 2.20
[    20.428] (II) RADEON(0): No DPMS capabilities specified
[    20.428] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    20.428] (II) RADEON(0): First detailed timing is preferred mode
[    20.428] (II) RADEON(0): redX: 0.600 redY: 0.351   greenX: 0.324 greenY: 0.554
[    20.428] (II) RADEON(0): blueX: 0.153 blueY: 0.145   whiteX: 0.312 whiteY: 0.328
[    20.428] (II) RADEON(0): Manufacturer's mask: 0
[    20.428] (II) RADEON(0): Supported detailed timing:
[    20.428] (II) RADEON(0): clock: 71.0 MHz   Image Size:  331 x 207 mm
[    20.428] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
[    20.428] (II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 823 v_border: 0
[    20.428] (II) RADEON(0):  LGPhilipsLCD
[    20.428] (II) RADEON(0):  LP154WX4-TLC3
[    20.428] (II) RADEON(0): EDID (in hex):
[    20.428] (II) RADEON(0): 	00ffffffffffff00320c00e300000000
[    20.428] (II) RADEON(0): 	00100103802115780ab3409959538d27
[    20.428] (II) RADEON(0): 	25505400000001010101010101010101
[    20.428] (II) RADEON(0): 	010101010101bc1b00a0502017303020
[    20.428] (II) RADEON(0): 	36004bcf100000190000000000000000
[    20.428] (II) RADEON(0): 	00000000000000000000000000fe004c
[    20.428] (II) RADEON(0): 	475068696c6970734c43440a000000fe
[    20.428] (II) RADEON(0): 	004c503135345758342d544c4333003c
[    20.428] (II) RADEON(0): Printing probed modes for output LVDS
[    20.428] (II) RADEON(0): Modeline "1280x800"x59.9   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[    20.428] (II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
[    20.428] (II) RADEON(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
[    20.428] (II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
[    20.428] (II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
[    20.428] (II) RADEON(0): Modeline "848x480"x59.7   31.50  848 872 952 1056  480 483 493 500 -hsync +vsync (29.8 kHz)
[    20.428] (II) RADEON(0): Modeline "720x480"x59.7   26.75  720 744 808 896  480 483 493 500 -hsync +vsync (29.9 kHz)
[    20.428] (II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
[    20.433] (II) RADEON(0): EDID for output DVI-0
[    20.433] (II) RADEON(0): Output VGA-0 disconnected
[    20.433] (II) RADEON(0): Output LVDS connected
[    20.433] (II) RADEON(0): Output DVI-0 disconnected
[    20.433] (II) RADEON(0): Using exact sizes for initial modes
[    20.433] (II) RADEON(0): Output LVDS using initial mode 1280x800
[    20.433] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    20.433] (II) RADEON(0): mem size init: gart size :1fdff000 vram size: s:8000000 visible:7bd8000
[    20.433] (II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
[    20.433] (==) RADEON(0): DPI set to (96, 96)
[    20.433] (II) Loading sub module "fb"
[    20.433] (II) LoadModule: "fb"
[    20.433] (II) Loading /usr/lib/xorg/modules/libfb.so
[    20.433] (II) Module fb: vendor="X.Org Foundation"
[    20.433] 	compiled for 1.9.2.901, module version = 1.0.0
[    20.433] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    20.434] (II) Loading sub module "ramdac"
[    20.434] (II) LoadModule: "ramdac"
[    20.434] (II) Module "ramdac" already built-in
[    20.434] (II) UnloadModule: "vesa"
[    20.434] (II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    20.434] (II) UnloadModule: "fbdev"
[    20.434] (II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    20.434] (II) UnloadModule: "fbdevhw"
[    20.434] (II) Unloading /usr/lib/xorg/modules/libfbdevhw.so
[    20.434] (--) Depth 24 pixmap format is 32 bpp
[    20.434] (II) RADEON(0): [DRI2] Setup complete
[    20.434] (II) RADEON(0): [DRI2]   DRI driver: r300
[    20.434] (II) RADEON(0): Front buffer size: 4000K
[    20.434] (II) RADEON(0): VRAM usage limit set to 110534K
[    20.434] (==) RADEON(0): Backing store disabled
[    20.434] (II) RADEON(0): Direct rendering enabled
[    20.434] (II) RADEON(0): Render acceleration enabled for R300/R400/R500 type cards.
[    20.434] (II) RADEON(0): Setting EXA maxPitchBytes
[    20.434] (II) EXA(0): Driver allocated offscreen pixmaps
[    20.434] (II) EXA(0): Driver registered support for the following operations:
[    20.434] (II)         Solid
[    20.434] (II)         Copy
[    20.434] (II)         Composite (RENDER acceleration)
[    20.434] (II)         UploadToScreen
[    20.434] (II)         DownloadFromScreen
[    20.435] (II) RADEON(0): Acceleration enabled
[    20.435] (==) RADEON(0): DPMS enabled
[    20.435] (==) RADEON(0): Silken mouse enabled
[    20.435] (II) RADEON(0): Set up textured video
[    20.435] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    20.435] (--) RandR disabled
[    20.435] (II) Initializing built-in extension Generic Event Extension
[    20.435] (II) Initializing built-in extension SHAPE
[    20.435] (II) Initializing built-in extension MIT-SHM
[    20.435] (II) Initializing built-in extension XInputExtension
[    20.435] (II) Initializing built-in extension XTEST
[    20.435] (II) Initializing built-in extension BIG-REQUESTS
[    20.435] (II) Initializing built-in extension SYNC
[    20.435] (II) Initializing built-in extension XKEYBOARD
[    20.435] (II) Initializing built-in extension XC-MISC
[    20.435] (II) Initializing built-in extension SECURITY
[    20.435] (II) Initializing built-in extension XINERAMA
[    20.435] (II) Initializing built-in extension XFIXES
[    20.435] (II) Initializing built-in extension RENDER
[    20.435] (II) Initializing built-in extension RANDR
[    20.435] (II) Initializing built-in extension COMPOSITE
[    20.435] (II) Initializing built-in extension DAMAGE
[    20.435] (II) Initializing built-in extension GESTURE
[    20.454] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    20.454] (II) AIGLX: enabled GLX_INTEL_swap_event
[    20.454] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    20.454] (II) AIGLX: enabled GLX_SGI_make_current_read
[    20.454] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    20.455] (II) AIGLX: Loaded and initialized /usr/lib/dri/r300_dri.so
[    20.455] (II) GLX: Initialized DRI2 GL provider for screen 0
[    20.456] (II) RADEON(0): Setting screen physical size to 338 x 211
[    20.484] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    20.496] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    20.496] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    20.496] (II) LoadModule: "evdev"
[    20.497] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    20.497] (II) Module evdev: vendor="X.Org Foundation"
[    20.497] 	compiled for 1.9.2.901, module version = 2.5.99
[    20.497] 	Module class: X.Org XInput Driver
[    20.497] 	ABI class: X.Org XInput driver, version 11.0
[    20.497] (**) Power Button: always reports core events
[    20.497] (**) Power Button: Device: "/dev/input/event3"
[    20.508] (--) Power Button: Found keys
[    20.508] (II) Power Button: Configuring as keyboard
[    20.508] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    20.508] (**) Option "xkb_rules" "evdev"
[    20.508] (**) Option "xkb_model" "pc105"
[    20.508] (**) Option "xkb_layout" "pl"
[    20.511] (II) XKB: reuse xkmfile /var/lib/xkb/server-61818C6B46DD4F01AE1F641F27B555591612208F.xkm
[    20.513] (II) config/udev: Adding input device Video Bus (/dev/input/event7)
[    20.513] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    20.513] (**) Video Bus: always reports core events
[    20.513] (**) Video Bus: Device: "/dev/input/event7"
[    20.528] (--) Video Bus: Found keys
[    20.528] (II) Video Bus: Configuring as keyboard
[    20.528] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    20.528] (**) Option "xkb_rules" "evdev"
[    20.528] (**) Option "xkb_model" "pc105"
[    20.528] (**) Option "xkb_layout" "pl"
[    20.529] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    20.529] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    20.529] (**) Power Button: always reports core events
[    20.529] (**) Power Button: Device: "/dev/input/event1"
[    20.544] (--) Power Button: Found keys
[    20.544] (II) Power Button: Configuring as keyboard
[    20.544] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    20.544] (**) Option "xkb_rules" "evdev"
[    20.544] (**) Option "xkb_model" "pc105"
[    20.544] (**) Option "xkb_layout" "pl"
[    20.544] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    20.544] (II) No input driver/identifier specified (ignoring)
[    20.545] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    20.545] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    20.545] (**) Sleep Button: always reports core events
[    20.545] (**) Sleep Button: Device: "/dev/input/event2"
[    20.560] (--) Sleep Button: Found keys
[    20.560] (II) Sleep Button: Configuring as keyboard
[    20.560] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    20.560] (**) Option "xkb_rules" "evdev"
[    20.560] (**) Option "xkb_model" "pc105"
[    20.560] (**) Option "xkb_layout" "pl"
[    20.563] (II) config/udev: Adding input device A4Tech PS/2+USB Mouse (/dev/input/event5)
[    20.563] (**) A4Tech PS/2+USB Mouse: Applying InputClass "evdev pointer catchall"
[    20.563] (**) A4Tech PS/2+USB Mouse: always reports core events
[    20.563] (**) A4Tech PS/2+USB Mouse: Device: "/dev/input/event5"
[    20.576] (--) A4Tech PS/2+USB Mouse: Found 12 mouse buttons
[    20.576] (--) A4Tech PS/2+USB Mouse: Found scroll wheel(s)
[    20.576] (--) A4Tech PS/2+USB Mouse: Found relative axes
[    20.576] (--) A4Tech PS/2+USB Mouse: Found x and y relative axes
[    20.576] (II) A4Tech PS/2+USB Mouse: Configuring as mouse
[    20.576] (II) A4Tech PS/2+USB Mouse: Adding scrollwheel support
[    20.576] (**) A4Tech PS/2+USB Mouse: YAxisMapping: buttons 4 and 5
[    20.576] (**) A4Tech PS/2+USB Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    20.576] (II) XINPUT: Adding extended input device "A4Tech PS/2+USB Mouse" (type: MOUSE)
[    20.576] (**) A4Tech PS/2+USB Mouse: (accel) keeping acceleration scheme 1
[    20.576] (**) A4Tech PS/2+USB Mouse: (accel) acceleration profile 0
[    20.576] (**) A4Tech PS/2+USB Mouse: (accel) acceleration factor: 2.000
[    20.576] (**) A4Tech PS/2+USB Mouse: (accel) acceleration threshold: 4
[    20.576] (II) A4Tech PS/2+USB Mouse: initialized for relative axes.
[    20.576] (II) config/udev: Adding input device A4Tech PS/2+USB Mouse (/dev/input/mouse0)
[    20.577] (II) No input driver/identifier specified (ignoring)
[    20.582] (II) config/udev: Adding input device Asus Laptop extra buttons (/dev/input/event6)
[    20.582] (**) Asus Laptop extra buttons: Applying InputClass "evdev keyboard catchall"
[    20.582] (**) Asus Laptop extra buttons: always reports core events
[    20.582] (**) Asus Laptop extra buttons: Device: "/dev/input/event6"
[    20.592] (--) Asus Laptop extra buttons: Found keys
[    20.592] (II) Asus Laptop extra buttons: Configuring as keyboard
[    20.592] (II) XINPUT: Adding extended input device "Asus Laptop extra buttons" (type: KEYBOARD)
[    20.592] (**) Option "xkb_rules" "evdev"
[    20.592] (**) Option "xkb_model" "pc105"
[    20.592] (**) Option "xkb_layout" "pl"
[    20.593] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    20.593] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    20.593] (**) AT Translated Set 2 keyboard: always reports core events
[    20.593] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    20.609] (--) AT Translated Set 2 keyboard: Found keys
[    20.609] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    20.609] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    20.609] (**) Option "xkb_rules" "evdev"
[    20.609] (**) Option "xkb_model" "pc105"
[    20.609] (**) Option "xkb_layout" "pl"
[    20.609] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event8)
[    20.610] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    20.610] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    20.610] (II) LoadModule: "synaptics"
[    20.610] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    20.610] (II) Module synaptics: vendor="X.Org Foundation"
[    20.610] 	compiled for 1.8.99.904, module version = 1.2.99
[    20.610] 	Module class: X.Org XInput Driver
[    20.610] 	ABI class: X.Org XInput driver, version 11.0
[    20.610] (II) Synaptics touchpad driver version 1.2.99
[    20.610] (**) Option "Device" "/dev/input/event8"
[    20.657] (--) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[    20.657] (--) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[    20.657] (--) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    20.657] (--) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
[    20.657] (--) SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    20.689] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    20.689] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    20.705] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    20.705] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    20.705] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
[    20.705] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    20.705] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    20.737] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    20.737] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
[    20.737] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    20.737] (II) Synaptics touchpad driver version 1.2.99
[    21.245] (EE) SynPS/2 Synaptics TouchPad no synaptics event device found
[    21.245] (**) Option "Device" "/dev/input/mouse1"
[    21.277] (EE) Query no Synaptics: 6003C8
[    21.277] (--) SynPS/2 Synaptics TouchPad: no supported touchpad found
[    21.277] (EE) SynPS/2 Synaptics TouchPad Unable to query/initialize Synaptics hardware.
[    21.277] (EE) PreInit failed for input device "SynPS/2 Synaptics TouchPad"
[    21.277] (II) UnloadModule: "synaptics"
[    22.068] (II) RADEON(0): EDID vendor "LPL", prod id 58112
[    22.068] (II) RADEON(0): Printing DDC gathered Modelines:
[    22.068] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[    22.108] (II) RADEON(0): EDID vendor "LPL", prod id 58112
[    22.108] (II) RADEON(0): Printing DDC gathered Modelines:
[    22.108] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[    22.152] (II) RADEON(0): EDID vendor "LPL", prod id 58112
[    22.152] (II) RADEON(0): Printing DDC gathered Modelines:
[    22.152] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[    27.204] (II) RADEON(0): EDID vendor "LPL", prod id 58112
[    27.204] (II) RADEON(0): Printing DDC gathered Modelines:
[    27.204] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[    28.040] (II) RADEON(0): EDID vendor "LPL", prod id 58112
[    28.040] (II) RADEON(0): Printing DDC gathered Modelines:
[    28.040] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[   108.076] (II) RADEON(0): EDID vendor "LPL", prod id 58112
[   108.076] (II) RADEON(0): Printing DDC gathered Modelines:
[   108.076] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[   108.112] (II) RADEON(0): EDID vendor "LPL", prod id 58112
[   108.112] (II) RADEON(0): Printing DDC gathered Modelines:
[   108.112] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[   108.417] (II) RADEON(0): EDID vendor "LPL", prod id 58112
[   108.417] (II) RADEON(0): Printing DDC gathered Modelines:
[   108.417] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[   108.501] (II) RADEON(0): EDID vendor "LPL", prod id 58112
[   108.501] (II) RADEON(0): Printing DDC gathered Modelines:
[   108.501] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[   108.577] (II) RADEON(0): EDID vendor "LPL", prod id 58112
[   108.577] (II) RADEON(0): Printing DDC gathered Modelines:
[   108.577] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[   109.128] (II) RADEON(0): EDID vendor "LPL", prod id 58112
[   109.128] (II) RADEON(0): Printing DDC gathered Modelines:
[   109.128] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[  1526.416] (II) RADEON(0): EDID vendor "LPL", prod id 58112
[  1526.416] (II) RADEON(0): Printing DDC gathered Modelines:
[  1526.416] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[  1531.040] (II) RADEON(0): EDID vendor "LPL", prod id 58112
[  1531.040] (II) RADEON(0): Printing DDC gathered Modelines:
[  1531.040] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[  1531.116] (II) RADEON(0): EDID vendor "LPL", prod id 58112
[  1531.116] (II) RADEON(0): Printing DDC gathered Modelines:
[  1531.116] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[  1531.168] (II) RADEON(0): EDID vendor "LPL", prod id 58112
[  1531.168] (II) RADEON(0): Printing DDC gathered Modelines:
[  1531.168] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[  1531.256] (II) RADEON(0): EDID vendor "LPL", prod id 58112
[  1531.256] (II) RADEON(0): Printing DDC gathered Modelines:
[  1531.256] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[  1531.301] (II) RADEON(0): EDID vendor "LPL", prod id 58112
[  1531.301] (II) RADEON(0): Printing DDC gathered Modelines:
[  1531.301] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[  1531.614] (II) RADEON(0): Allocate new frame buffer 1024x768 stride 1024
[  1531.615] (II) RADEON(0): VRAM usage limit set to 111369K
[  1888.376] (II) RADEON(0): EDID vendor "LPL", prod id 58112
[  1888.376] (II) RADEON(0): Printing DDC gathered Modelines:
[  1888.377] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[  1888.437] (II) RADEON(0): EDID vendor "LPL", prod id 58112
[  1888.437] (II) RADEON(0): Printing DDC gathered Modelines:
[  1888.437] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[  1895.389] (II) RADEON(0): EDID vendor "LPL", prod id 58112
[  1895.390] (II) RADEON(0): Printing DDC gathered Modelines:
[  1895.390] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[  1895.710] (II) RADEON(0): Allocate new frame buffer 1280x800 stride 1280
[  1895.714] (II) RADEON(0): VRAM usage limit set to 110534K
[  1896.589] (II) RADEON(0): EDID vendor "LPL", prod id 58112
[  1896.589] (II) RADEON(0): Printing DDC gathered Modelines:
[  1896.589] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[  1896.680] (II) RADEON(0): EDID vendor "LPL", prod id 58112
[  1896.680] (II) RADEON(0): Printing DDC gathered Modelines:
[  1896.680] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[  1896.720] (II) RADEON(0): EDID vendor "LPL", prod id 58112
[  1896.720] (II) RADEON(0): Printing DDC gathered Modelines:
[  1896.720] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[  1896.848] (II) RADEON(0): EDID vendor "LPL", prod id 58112
[  1896.848] (II) RADEON(0): Printing DDC gathered Modelines:
[  1896.848] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[  1896.896] (II) RADEON(0): EDID vendor "LPL", prod id 58112
[  1896.896] (II) RADEON(0): Printing DDC gathered Modelines:
[  1896.897] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[  1896.988] (II) RADEON(0): EDID vendor "LPL", prod id 58112
[  1896.988] (II) RADEON(0): Printing DDC gathered Modelines:
[  1896.989] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[  1964.136] (II) RADEON(0): EDID vendor "LPL", prod id 58112
[  1964.136] (II) RADEON(0): Printing DDC gathered Modelines:
[  1964.136] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[  1964.172] (II) RADEON(0): EDID vendor "LPL", prod id 58112
[  1964.172] (II) RADEON(0): Printing DDC gathered Modelines:
[  1964.172] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[  1964.497] (II) RADEON(0): EDID vendor "LPL", prod id 58112
[  1964.497] (II) RADEON(0): Printing DDC gathered Modelines:
[  1964.497] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[  1964.588] (II) RADEON(0): EDID vendor "LPL", prod id 58112
[  1964.588] (II) RADEON(0): Printing DDC gathered Modelines:
[  1964.588] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[  1964.648] (II) RADEON(0): EDID vendor "LPL", prod id 58112
[  1964.648] (II) RADEON(0): Printing DDC gathered Modelines:
[  1964.648] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[  1965.368] (II) RADEON(0): EDID vendor "LPL", prod id 58112
[  1965.368] (II) RADEON(0): Printing DDC gathered Modelines:
[  1965.368] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)

Please help me fix my driver

---

### Post by mads65 on 2011-04-11
According to [officially supported]("http://wiki.cchtml.com/index.php/Hardware") hardware site, your card (x2300) is only
"*supported with the legacy ATI 9-3 Catalyst release, but you MUST use a kernel 2.6.28 (or earlier) and Xserver 1.5 (or earlier). For example, you can use Catalyst 9-3 if you're running Ubuntu 8.04.*"

Unfortunately, it seems like you either have to stick with your current open source drivers, or
install Ubuntu 8.04 and then install [Catalyst 9-3]("http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English").
Current catalyst version is [11.3]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx").

---

### Post by Yellow Pasque on 2011-04-11
If you installed fglrx/Catalyst, purge it and don't try to install it again (it doesn't support your card anymore):  Run the 6 commands here: [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx)

Next, use the xorg-edgers PPA, which uses r300g 3D driver. It looks like you already did this, but are still using old r300, so I'm confused). I'm not sure how to force r300g and I've been googling for 10 minutes.

EDIT: Oh, I see. You have to install libgl1-mesa-dri-experimental.

---

### Post by set4812 on 2011-04-12
> **Temüjin said:**
> If you installed fglrx/Catalyst, purge it and don't try to install it again (it doesn't support your card anymore):  Run the 6 commands here: [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx)

Next, use the xorg-edgers PPA, which uses r300g 3D driver. It looks like you already did this, but are still using old r300, so I'm confused). I'm not sure how to force r300g and I've been googling for 10 minutes.

EDIT: Oh, I see. You have to install libgl1-mesa-dri-experimental.

1. done 
2. i install libgl1-mesa-dri-experimental but not help.

In wow 1280x800 wow crash in openGL but if openGL is off i have 10-15 fps

---

### Post by mads65 on 2011-04-12
> **temüjin said:**
> if you installed fglrx/catalyst, purge it and  don't try to install it again (it doesn't support your card anymore):   Run the 6 commands here: [http://wiki.cchtml.com/index.php/ubuntu_maverick_installation_guide#removing_catalyst.2ffglrx](http://wiki.cchtml.com/index.php/ubuntu_maverick_installation_guide#removing_catalyst.2ffglrx)

next, use the xorg-edgers ppa, which uses r300g 3d driver. It looks like  you already did this, but are still using old r300, so i'm confused).  I'm not sure how to force r300g and i've been googling for 10 minutes.

Edit: Oh, i see. You have to install libgl1-mesa-dri-experimental.
> **set4812 said:**
> 1. Done 
2. I install libgl1-mesa-dri-experimental but not help.
  :lolflag:

---

