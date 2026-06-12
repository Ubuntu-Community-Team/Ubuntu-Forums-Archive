---
title: "Serious issues with radeon HD 6480G running on ASUS AMD A4 3300M chipset"
date: 2012-11-25
forum: Hardware
---

### Post by kenpachiZaraki on 2012-11-25
Original Problem:
 At start up system would hang on login splash screen [never solved it]
        - tried upgrading my driver to the recommended on website [http://www.amd.com](http://www.amd.com) though this just led to more issues and a complete reinstall of ubuntu OS was needed

New found issue with original driver setup after reinstall of Ubuntu OS 
        - trying to us HDMI out with my tv and the X crashes!

here is a look at the Xorg log:
```
[    16.035] 
X.Org X Server 1.13.0
Release Date: 2012-09-05
[    16.035] X Protocol Version 11, Revision 0
[    16.035] Build Operating System: Linux 3.2.0-30-generic x86_64 Ubuntu
[    16.035] Current Operating System: Linux 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:31:23 UTC 2012 x86_64
[    16.035] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-17-generic root=UUID=3fc0ba7c-8518-40dd-a720-2b1e1cbfffb8 ro quiet splash vt.handoff=7

	Using a default monitor configuration.
[    16.062] (==) Automatically adding devices
[    16.062] (==) Automatically enabling devices
[    16.062] (==) Automatically adding GPU devices
[    16.062] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    16.062] 	Entry deleted from font path.
[    16.062] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    16.062] 	Entry deleted from font path.
[    16.062] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    16.062] 	Entry deleted from font path.
[    16.062] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    16.062] 	Entry deleted from font path.
[    16.062] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    16.062] 	Entry deleted from font path.
[    16.062] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    16.062] 	Entry deleted from font path.
[    16.062] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    16.062] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    16.062] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    16.062] (II) Loader magic: 0x7f31737bac40
[    16.062] (II) Module ABI versions:
[    16.062] 	X.Org ANSI C Emulation: 0.4
[    16.062] 	X.Org Video Driver: 13.0
[    16.062] 	X.Org XInput driver : 18.0
[    16.062] 	X.Org Server Extension : 7.0
[    16.063] (II) config/udev: Adding drm device (/dev/dri/card0)
[    16.064] (--) PCI:*(0:0:1:0) 1002:9648:1043:109c rev 0, Mem @ 0xc0000000/268435456, 0xfeb00000/262144, I/O @ 0x0000f000/256
[    16.064] (II) Open ACPI successful (/var/run/acpid.socket)
[    16.064] Initializing built-in extension Generic Event Extension
[    16.064] Initializing built-in extension SHAPE
[    16.064] Initializing built-in extension MIT-SHM
[    16.064] Initializing built-in extension XInputExtension
[    16.064] Initializing built-in extension XTEST
[    16.064] Initializing built-in extension BIG-REQUESTS
[    16.064] Initializing built-in extension SYNC
[    16.064] Initializing built-in extension XKEYBOARD
[    16.064] Initializing built-in extension XC-MISC
[    16.064] Initializing built-in extension SECURITY
[    16.064] Initializing built-in extension XINERAMA
[    16.064] Initializing built-in extension XFIXES
[    16.064] Initializing built-in extension RENDER
[    16.064] Initializing built-in extension RANDR
[    16.064] Initializing built-in extension COMPOSITE
[    16.064] Initializing built-in extension DAMAGE
[    16.064] Initializing built-in extension MIT-SCREEN-SAVER
[    16.064] Initializing built-in extension DOUBLE-BUFFER
[    16.064] Initializing built-in extension RECORD
[    16.064] Initializing built-in extension DPMS
[    16.064] Initializing built-in extension X-Resource
[    16.064] Initializing built-in extension XVideo
[    16.065] Initializing built-in extension XVideo-MotionCompensation
[    16.065] Initializing built-in extension XFree86-VidModeExtension
[    16.065] Initializing built-in extension XFree86-DGA
[    16.065] Initializing built-in extension XFree86-DRI
[    16.065] Initializing built-in extension DRI2
[    16.065] (II) LoadModule: "glx"
[    16.139] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    16.139] (II) Module glx: vendor="X.Org Foundation"
[    16.139] 	compiled for 1.13.0, module version = 1.0.0
[    16.139] 	ABI class: X.Org Server Extension, version 7.0
[    16.139] (==) AIGLX enabled
[    16.139] Loading extension GLX
[    16.139] (==) Matched fglrx as autoconfigured driver 0
[    16.139] (==) Matched ati as autoconfigured driver 1
[    16.139] (==) Matched fglrx as autoconfigured driver 2
[    16.139] (==) Matched ati as autoconfigured driver 3
[    16.139] (==) Matched vesa as autoconfigured driver 4
[    16.139] (==) Matched modesetting as autoconfigured driver 5
[    16.139] (==) Matched fbdev as autoconfigured driver 6
[    16.139] (==) Assigned the driver to the xf86ConfigLayout
[    16.139] (II) LoadModule: "fglrx"
[    16.140] (WW) Warning, couldn't open module fglrx
[    16.140] (II) UnloadModule: "fglrx"
[    16.140] (II) Unloading fglrx
[    16.140] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    16.140] (II) LoadModule: "ati"
[    16.141] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    16.141] (II) Module ati: vendor="X.Org Foundation"
[    16.141] 	compiled for 1.13.0, module version = 6.99.99
[    16.141] 	Module class: X.Org Video Driver
[    16.141] 	ABI class: X.Org Video Driver, version 13.0
[    16.141] (II) LoadModule: "radeon"
[    16.141] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    16.141] (II) Module radeon: vendor="X.Org Foundation"
[    16.141] 	compiled for 1.13.0, module version = 6.99.99
[    16.141] 	Module class: X.Org Video Driver
[    16.141] 	ABI class: X.Org Video Driver, version 13.0
[    16.141] (II) LoadModule: "vesa"
[    16.141] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    16.141] (II) Module vesa: vendor="X.Org Foundation"
[    16.141] 	compiled for 1.12.99.902, module version = 2.3.2
[    16.141] 	Module class: X.Org Video Driver
[    16.141] 	ABI class: X.Org Video Driver, version 13.0
[    16.141] (II) LoadModule: "modesetting"
[    16.142] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    16.142] (II) Module modesetting: vendor="X.Org Foundation"
[    16.142] 	compiled for 1.13.0, module version = 0.5.0
[    16.142] 	Module class: X.Org Video Driver
[    16.142] 	ABI class: X.Org Video Driver, version 13.0
[    16.142] (II) LoadModule: "fbdev"
[    16.142] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    16.142] (II) Module fbdev: vendor="X.Org Foundation"
[    16.142] 	compiled for 1.12.99.902, module version = 0.4.3
[    16.142] 	Module class: X.Org Video Driver
[    16.142] 	ABI class: X.Org Video Driver, version 13.0
[    16.142] (==) Matched fglrx as autoconfigured driver 0
[    16.142] (==) Matched ati as autoconfigured driver 1
[    16.142] (==) Matched fglrx as autoconfigured driver 2
[    16.142] (==) Matched ati as autoconfigured driver 3
[    16.142] (==) Matched vesa as autoconfigured driver 4
[    16.142] (==) Matched modesetting as autoconfigured driver 5
[    16.142] (==) Matched fbdev as autoconfigured driver 6
[    16.142] (==) Assigned the driver to the xf86ConfigLayout
[    16.142] (II) LoadModule: "fglrx"
[    16.142] (WW) Warning, couldn't open module fglrx
[    16.142] (II) UnloadModule: "fglrx"
[    16.142] (II) Unloading fglrx
[    16.142] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    16.142] (II) LoadModule: "ati"
[    16.142] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    16.142] (II) Module ati: vendor="X.Org Foundation"
[    16.142] 	compiled for 1.13.0, module version = 6.99.99
[    16.143] 	Module class: X.Org Video Driver
[    16.143] 	ABI class: X.Org Video Driver, version 13.0
[    16.143] (II) LoadModule: "vesa"
[    16.143] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    16.143] (II) Module vesa: vendor="X.Org Foundation"
[    16.143] 	compiled for 1.12.99.902, module version = 2.3.2
[    16.143] 	Module class: X.Org Video Driver
[    16.143] 	ABI class: X.Org Video Driver, version 13.0
[    16.143] (II) UnloadModule: "vesa"
[    16.143] (II) Unloading vesa
[    16.143] (II) Failed to load module "vesa" (already loaded, 0)
[    16.143] (II) LoadModule: "modesetting"
[    16.143] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    16.143] (II) Module modesetting: vendor="X.Org Foundation"
[    16.143] 	compiled for 1.13.0, module version = 0.5.0
[    16.143] 	Module class: X.Org Video Driver
[    16.143] 	ABI class: X.Org Video Driver, version 13.0
[    16.143] (II) UnloadModule: "modesetting"
[    16.143] (II) Unloading modesetting
[    16.143] (II) Failed to load module "modesetting" (already loaded, 0)
[    16.143] (II) LoadModule: "fbdev"
[    16.143] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    16.143] (II) Module fbdev: vendor="X.Org Foundation"
[    16.143] 	compiled for 1.12.99.902, module version = 0.4.3
[    16.143] 	Module class: X.Org Video Driver
[    16.143] 	ABI class: X.Org Video Driver, version 13.0
[    16.143] (II) UnloadModule: "fbdev"
[    16.143] (II) Unloading fbdev
[    16.143] (II) Failed to load module "fbdev" (already loaded, 0)
[    16.143] (II) RADEON: Driver for ATI Radeon chipsets:
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
[    16.147] (II) VESA: driver for VESA chipsets: vesa
[    16.147] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    16.147] (II) FBDEV: driver for framebuffer: fbdev
[    16.147] (++) using VT number 7

[    16.147] (II) [KMS] Kernel modesetting enabled.
[    16.147] (WW) Falling back to old probe method for vesa
[    16.147] (WW) Falling back to old probe method for modesetting
[    16.147] (WW) Falling back to old probe method for fbdev
[    16.147] (II) Loading sub module "fbdevhw"
[    16.147] (II) LoadModule: "fbdevhw"
[    16.147] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    16.147] (II) Module fbdevhw: vendor="X.Org Foundation"
[    16.147] 	compiled for 1.13.0, module version = 0.0.2
[    16.147] 	ABI class: X.Org Video Driver, version 13.0
[    16.147] (II) RADEON(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    16.147] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    16.147] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    16.147] (==) RADEON(0): Default visual is TrueColor
[    16.147] (==) RADEON(0): RGB weight 888
[    16.147] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    16.147] (--) RADEON(0): Chipset: "SUMO" (ChipID = 0x9648)
[    16.147] (II) Loading sub module "dri2"
[    16.148] (II) LoadModule: "dri2"
[    16.148] (II) Module "dri2" already built-in
[    16.148] (II) Loading sub module "exa"
[    16.148] (II) LoadModule: "exa"
[    16.148] (II) Loading /usr/lib/xorg/modules/libexa.so
[    16.148] (II) Module exa: vendor="X.Org Foundation"
[    16.148] 	compiled for 1.13.0, module version = 2.6.0
[    16.148] 	ABI class: X.Org Video Driver, version 13.0
[    16.148] (II) RADEON(0): KMS Color Tiling: enabled
[    16.148] (II) RADEON(0): KMS Pageflipping: enabled
[    16.148] (II) RADEON(0): SwapBuffers wait for vsync: enabled
[    16.308] (II) RADEON(0): Output VGA-0 has no monitor section
[    16.353] (II) RADEON(0): Output LVDS has no monitor section
[    16.480] (II) RADEON(0): Output HDMI-0 has no monitor section
[    16.641] (II) RADEON(0): EDID for output VGA-0
[    16.680] (II) RADEON(0): EDID for output LVDS
[    16.680] (II) RADEON(0): Manufacturer: CMO  Model: 15a7  Serial#: 0
[    16.680] (II) RADEON(0): Year: 2010  Week: 31
[    16.680] (II) RADEON(0): EDID Version: 1.3
[    16.680] (II) RADEON(0): Digital Display Input
[    16.680] (II) RADEON(0): Max Image Size [cm]: horiz.: 35  vert.: 19
[    16.680] (II) RADEON(0): Gamma: 2.20
[    16.680] (II) RADEON(0): No DPMS capabilities specified
[    16.680] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    16.680] (II) RADEON(0): First detailed timing is preferred mode
[    16.680] (II) RADEON(0): redX: 0.617 redY: 0.340   greenX: 0.320 greenY: 0.598
[    16.680] (II) RADEON(0): blueX: 0.160 blueY: 0.084   whiteX: 0.313 whiteY: 0.329
[    16.680] (II) RADEON(0): Manufacturer's mask: 0
[    16.680] (II) RADEON(0): Supported detailed timing:
[    16.680] (II) RADEON(0): clock: 69.3 MHz   Image Size:  344 x 193 mm
[    16.680] (II) RADEON(0): h_active: 1366  h_sync: 1382  h_sync_end 1416 h_blank_end 1466 h_border: 0
[    16.680] (II) RADEON(0): v_active: 768  v_sync: 770  v_sync_end 776 v_blanking: 788 v_border: 0
[    16.680] (II) RADEON(0):  N156BGE-L21
[    16.681] (II) RADEON(0):  CMO
[    16.681] (II) RADEON(0):  N156BGE-L21
[    16.681] (II) RADEON(0): EDID (in hex):
[    16.681] (II) RADEON(0): 	00ffffffffffff000dafa71500000000
[    16.681] (II) RADEON(0): 	1f140103802313780a00259e57529929
[    16.681] (II) RADEON(0): 	15505400000001010101010101010101
[    16.681] (II) RADEON(0): 	010101010101121b5664500014301022
[    16.681] (II) RADEON(0): 	260058c110000018000000fe004e3135
[    16.681] (II) RADEON(0): 	364247452d4c32310a20000000fe0043
[    16.681] (II) RADEON(0): 	4d4f0a202020202020202020000000fe
[    16.681] (II) RADEON(0): 	004e3135364247452d4c32310a200095
[    16.681] (II) RADEON(0): Printing probed modes for output LVDS
[    16.681] (II) RADEON(0): Modeline "1366x768"x60.0   69.30  1366 1382 1416 1466  768 770 776 788 -hsync -vsync (47.3 kHz eP)
[    16.681] (II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
[    16.681] (II) RADEON(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
[    16.681] (II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
[    16.681] (II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
[    16.681] (II) RADEON(0): Modeline "848x480"x59.7   31.50  848 872 952 1056  480 483 493 500 -hsync +vsync (29.8 kHz)
[    16.681] (II) RADEON(0): Modeline "720x480"x59.7   26.75  720 744 808 896  480 483 493 500 -hsync +vsync (29.9 kHz)
[    16.681] (II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
[    16.808] (II) RADEON(0): EDID for output HDMI-0
[    16.808] (II) RADEON(0): Output VGA-0 disconnected
[    16.808] (II) RADEON(0): Output LVDS connected
[    16.808] (II) RADEON(0): Output HDMI-0 disconnected
[    16.808] (II) RADEON(0): Using exact sizes for initial modes
[    16.808] (II) RADEON(0): Output LVDS using initial mode 1366x768
[    16.808] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    16.808] (II) RADEON(0): mem size init: gart size :1fdff000 vram size: s:20000000 visible:fba0000
[    16.808] (II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
[    16.808] (==) RADEON(0): DPI set to (96, 96)
[    16.808] (II) Loading sub module "fb"
[    16.808] (II) LoadModule: "fb"
[    16.808] (II) Loading /usr/lib/xorg/modules/libfb.so
[    16.808] (II) Module fb: vendor="X.Org Foundation"
[    16.808] 	compiled for 1.13.0, module version = 1.0.0
[    16.808] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    16.808] (II) Loading sub module "ramdac"
[    16.808] (II) LoadModule: "ramdac"
[    16.808] (II) Module "ramdac" already built-in
[    16.808] (II) UnloadModule: "vesa"
[    16.808] (II) Unloading vesa
[    16.808] (II) UnloadModule: "modesetting"
[    16.808] (II) Unloading modesetting
[    16.808] (II) UnloadModule: "fbdev"
[    16.808] (II) Unloading fbdev
[    16.808] (II) UnloadSubModule: "fbdevhw"
[    16.808] (II) Unloading fbdevhw
[    16.808] (--) Depth 24 pixmap format is 32 bpp
[    16.808] (II) RADEON(0): [DRI2] Setup complete
[    16.808] (II) RADEON(0): [DRI2]   DRI driver: r600
[    16.808] (II) RADEON(0): [DRI2]   VDPAU driver: r600
[    16.809] (II) RADEON(0): Front buffer size: 4128K
[    16.809] (II) RADEON(0): VRAM usage limit set to 228182K
[    16.809] (==) RADEON(0): Backing store disabled
[    16.809] (II) RADEON(0): Direct rendering enabled
[    16.809] (II) RADEON(0): Setting EXA maxPitchBytes
[    16.809] (II) EXA(0): Driver allocated offscreen pixmaps
[    16.809] (II) EXA(0): Driver registered support for the following operations:
[    16.809] (II)         Solid
[    16.809] (II)         Copy
[    16.809] (II)         Composite (RENDER acceleration)
[    16.809] (II)         UploadToScreen
[    16.809] (II)         DownloadFromScreen
[    16.809] (II) RADEON(0): Acceleration enabled
[    16.809] (==) RADEON(0): DPMS enabled
[    16.809] (==) RADEON(0): Silken mouse enabled
[    16.809] (II) RADEON(0): Set up textured video
[    16.809] (II) RADEON(0): [XvMC] Associated with Radeon Textured Video.
[    16.809] (II) RADEON(0): [XvMC] Extension initialized.
[    16.809] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    16.809] (--) RandR disabled
[    16.825] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    16.825] (II) AIGLX: enabled GLX_INTEL_swap_event
[    16.825] (II) AIGLX: enabled GLX_ARB_create_context
[    16.825] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    16.825] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    16.825] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    16.825] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    16.825] (II) AIGLX: Loaded and initialized r600
[    16.825] (II) GLX: Initialized DRI2 GL provider for screen 0
[    16.954] (II) RADEON(0): Setting screen physical size to 361 x 203
[    16.963] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    16.966] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    16.966] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    16.966] (II) LoadModule: "evdev"
[    16.966] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.966] (II) Module evdev: vendor="X.Org Foundation"
[    16.966] 	compiled for 1.13.0, module version = 2.7.3
[    16.966] 	Module class: X.Org XInput Driver
[    16.966] 	ABI class: X.Org XInput driver, version 18.0
[    16.966] (II) Using input driver 'evdev' for 'Power Button'
[    16.966] (**) Power Button: always reports core events
[    16.966] (**) evdev: Power Button: Device: "/dev/input/event3"
[    16.966] (--) evdev: Power Button: Vendor 0 Product 0x1
[    16.967] (--) evdev: Power Button: Found keys
[    16.967] (II) evdev: Power Button: Configuring as keyboard
[    16.967] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    16.967] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    16.967] (**) Option "xkb_rules" "evdev"
[    16.967] (**) Option "xkb_model" "pc105"
[    16.967] (**) Option "xkb_layout" "us"
[    16.967] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    16.967] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    16.967] (II) Using input driver 'evdev' for 'Video Bus'
[    16.967] (**) Video Bus: always reports core events
[    16.967] (**) evdev: Video Bus: Device: "/dev/input/event5"
[    16.967] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    16.967] (--) evdev: Video Bus: Found keys
[    16.967] (II) evdev: Video Bus: Configuring as keyboard
[    16.967] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:00/input/input5/event5"
[    16.967] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    16.967] (**) Option "xkb_rules" "evdev"
[    16.967] (**) Option "xkb_model" "pc105"
[    16.967] (**) Option "xkb_layout" "us"
[    16.968] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    16.968] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    16.968] (II) Using input driver 'evdev' for 'Power Button'
[    16.968] (**) Power Button: always reports core events
[    16.968] (**) evdev: Power Button: Device: "/dev/input/event0"
[    16.968] (--) evdev: Power Button: Vendor 0 Product 0x1
[    16.968] (--) evdev: Power Button: Found keys
[    16.968] (II) evdev: Power Button: Configuring as keyboard
[    16.968] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    16.968] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    16.968] (**) Option "xkb_rules" "evdev"
[    16.968] (**) Option "xkb_model" "pc105"
[    16.968] (**) Option "xkb_layout" "us"
[    16.968] (II) config/udev: Adding input device Lid Switch (/dev/input/event2)
[    16.968] (II) No input driver specified, ignoring this device.
[    16.968] (II) This device may have been added with another device file.
[    16.969] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    16.969] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    16.969] (II) Using input driver 'evdev' for 'Sleep Button'
[    16.969] (**) Sleep Button: always reports core events
[    16.969] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[    16.969] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    16.969] (--) evdev: Sleep Button: Found keys
[    16.969] (II) evdev: Sleep Button: Configuring as keyboard
[    16.969] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1/event1"
[    16.969] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[    16.969] (**) Option "xkb_rules" "evdev"
[    16.969] (**) Option "xkb_model" "pc105"
[    16.969] (**) Option "xkb_layout" "us"
[    16.969] (II) config/udev: Adding drm device (/dev/dri/card0)
[    16.970] (II) config/udev: Adding input device HD-Audio Generic HDMI/DP,pcm=3 (/dev/input/event8)
[    16.970] (II) No input driver specified, ignoring this device.
[    16.970] (II) This device may have been added with another device file.
[    16.970] (II) config/udev: Adding input device ASUS USB2.0 WebCam (/dev/input/event6)
[    16.970] (**) ASUS USB2.0 WebCam: Applying InputClass "evdev keyboard catchall"
[    16.970] (II) Using input driver 'evdev' for 'ASUS USB2.0 WebCam'
[    16.970] (**) ASUS USB2.0 WebCam: always reports core events
[    16.970] (**) evdev: ASUS USB2.0 WebCam: Device: "/dev/input/event6"
[    16.970] (--) evdev: ASUS USB2.0 WebCam: Vendor 0x58f Product 0xa016
[    16.970] (--) evdev: ASUS USB2.0 WebCam: Found keys
[    16.970] (II) evdev: ASUS USB2.0 WebCam: Configuring as keyboard
[    16.970] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.2/usb1/1-3/1-3:1.0/input/input6/event6"
[    16.970] (II) XINPUT: Adding extended input device "ASUS USB2.0 WebCam" (type: KEYBOARD, id 10)
[    16.970] (**) Option "xkb_rules" "evdev"
[    16.970] (**) Option "xkb_model" "pc105"
[    16.970] (**) Option "xkb_layout" "us"
[    16.970] (II) config/udev: Adding input device HD-Audio Generic Headphone (/dev/input/event10)
[    16.970] (II) No input driver specified, ignoring this device.
[    16.971] (II) This device may have been added with another device file.
[    16.971] (II) config/udev: Adding input device HD-Audio Generic Mic (/dev/input/event9)
[    16.971] (II) No input driver specified, ignoring this device.
[    16.971] (II) This device may have been added with another device file.
[    16.971] (II) config/udev: Adding input device Asus WMI hotkeys (/dev/input/event7)
[    16.971] (**) Asus WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    16.971] (II) Using input driver 'evdev' for 'Asus WMI hotkeys'
[    16.971] (**) Asus WMI hotkeys: always reports core events
[    16.971] (**) evdev: Asus WMI hotkeys: Device: "/dev/input/event7"
[    16.971] (--) evdev: Asus WMI hotkeys: Vendor 0 Product 0
[    16.971] (--) evdev: Asus WMI hotkeys: Found keys
[    16.971] (II) evdev: Asus WMI hotkeys: Configuring as keyboard
[    16.971] (**) Option "config_info" "udev:/sys/devices/platform/asus-nb-wmi/input/input7/event7"
[    16.971] (II) XINPUT: Adding extended input device "Asus WMI hotkeys" (type: KEYBOARD, id 11)
[    16.971] (**) Option "xkb_rules" "evdev"
[    16.971] (**) Option "xkb_model" "pc105"
[    16.971] (**) Option "xkb_layout" "us"
[    16.972] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    16.972] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    16.972] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    16.972] (**) AT Translated Set 2 keyboard: always reports core events
[    16.972] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    16.972] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    16.972] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    16.972] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    16.972] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    16.972] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 12)
[    16.972] (**) Option "xkb_rules" "evdev"
[    16.972] (**) Option "xkb_model" "pc105"
[    16.972] (**) Option "xkb_layout" "us"
[    16.972] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/event11)
[    16.972] (**) ETPS/2 Elantech Touchpad: Applying InputClass "evdev touchpad catchall"
[    16.972] (**) ETPS/2 Elantech Touchpad: Applying InputClass "touchpad catchall"
[    16.972] (**) ETPS/2 Elantech Touchpad: Applying InputClass "Default clickpad buttons"
[    16.972] (II) LoadModule: "synaptics"
[    16.973] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    16.973] (II) Module synaptics: vendor="X.Org Foundation"
[    16.973] 	compiled for 1.12.99.905, module version = 1.6.2
[    16.973] 	Module class: X.Org XInput Driver
[    16.973] 	ABI class: X.Org XInput driver, version 18.0
[    16.973] (II) Using input driver 'synaptics' for 'ETPS/2 Elantech Touchpad'
[    16.973] (**) ETPS/2 Elantech Touchpad: always reports core events
[    16.973] (**) Option "Device" "/dev/input/event11"
[    16.976] (--) synaptics: ETPS/2 Elantech Touchpad: x-axis range 0 - 2436
[    16.976] (--) synaptics: ETPS/2 Elantech Touchpad: y-axis range 0 - 1044
[    16.976] (--) synaptics: ETPS/2 Elantech Touchpad: pressure range 0 - 255
[    16.976] (--) synaptics: ETPS/2 Elantech Touchpad: finger width range 0 - 15
[    16.976] (--) synaptics: ETPS/2 Elantech Touchpad: buttons: left right double triple
[    16.976] (--) synaptics: ETPS/2 Elantech Touchpad: Vendor 0x2 Product 0xe
[    16.976] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[    16.976] (**) ETPS/2 Elantech Touchpad: always reports core events
[    16.976] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input11/event11"
[    16.976] (II) XINPUT: Adding extended input device "ETPS/2 Elantech Touchpad" (type: TOUCHPAD, id 13)
[    16.976] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MinSpeed is now constant deceleration 2.5
[    16.976] (**) synaptics: ETPS/2 Elantech Touchpad: MaxSpeed is now 1.75
[    16.976] (**) synaptics: ETPS/2 Elantech Touchpad: AccelFactor is now 0.075
[    16.977] (**) ETPS/2 Elantech Touchpad: (accel) keeping acceleration scheme 1
[    16.977] (**) ETPS/2 Elantech Touchpad: (accel) acceleration profile 1
[    16.977] (**) ETPS/2 Elantech Touchpad: (accel) acceleration factor: 2.000
[    16.977] (**) ETPS/2 Elantech Touchpad: (accel) acceleration threshold: 4
[    16.977] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[    16.977] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/mouse0)
[    16.977] (**) ETPS/2 Elantech Touchpad: Ignoring device from InputClass "touchpad ignore duplicates"
[    18.831] (II) RADEON(0): EDID vendor "CMO", prod id 5543
[    18.831] (II) RADEON(0): Printing DDC gathered Modelines:
[    18.831] (II) RADEON(0): Modeline "1366x768"x0.0   69.30  1366 1382 1416 1466  768 770 776 788 -hsync -vsync (47.3 kHz eP)
[    20.690] (II) RADEON(0): EDID vendor "CMO", prod id 5543
[    20.690] (II) RADEON(0): Printing DDC gathered Modelines:
[    20.690] (II) RADEON(0): Modeline "1366x768"x0.0   69.30  1366 1382 1416 1466  768 770 776 788 -hsync -vsync (47.3 kHz eP)
[    41.583] (II) RADEON(0): EDID vendor "CMO", prod id 5543
[    41.583] (II) RADEON(0): Printing DDC gathered Modelines:
[    41.583] (II) RADEON(0): Modeline "1366x768"x0.0   69.30  1366 1382 1416 1466  768 770 776 788 -hsync -vsync (47.3 kHz eP)
[    42.155] (II) RADEON(0): EDID vendor "CMO", prod id 5543
[    42.155] (II) RADEON(0): Printing DDC gathered Modelines:
[    42.155] (II) RADEON(0): Modeline "1366x768"x0.0   69.30  1366 1382 1416 1466  768 770 776 788 -hsync -vsync (47.3 kHz eP)
[    43.395] (II) RADEON(0): EDID vendor "CMO", prod id 5543
[    43.395] (II) RADEON(0): Printing DDC gathered Modelines:
[    43.395] (II) RADEON(0): Modeline "1366x768"x0.0   69.30  1366 1382 1416 1466  768 770 776 788 -hsync -vsync (47.3 kHz eP)
[    45.179] (II) RADEON(0): EDID vendor "CMO", prod id 5543
[    45.179] (II) RADEON(0): Printing DDC gathered Modelines:
[    45.179] (II) RADEON(0): Modeline "1366x768"x0.0   69.30  1366 1382 1416 1466  768 770 776 788 -hsync -vsync (47.3 kHz eP)
[    48.723] (II) RADEON(0): EDID vendor "CMO", prod id 5543
[    48.723] (II) RADEON(0): Printing DDC gathered Modelines:
[    48.723] (II) RADEON(0): Modeline "1366x768"x0.0   69.30  1366 1382 1416 1466  768 770 776 788 -hsync -vsync (47.3 kHz eP)
[    54.812] (II) XKB: reuse xkmfile /var/lib/xkb/server-8C3648A5FD728529D869F46730BE1BC287DB231C.xkm
[  2434.627] (II) RADEON(0): EDID vendor "CMO", prod id 5543
[  2434.627] (II) RADEON(0): Printing DDC gathered Modelines:
[  2434.628] (II) RADEON(0): Modeline "1366x768"x0.0   69.30  1366 1382 1416 1466  768 770 776 788 -hsync -vsync (47.3 kHz eP)
[  5308.079] (II) RADEON(0): EDID vendor "CMO", prod id 5543
[  5308.079] (II) RADEON(0): Printing DDC gathered Modelines:
[  5308.079] (II) RADEON(0): Modeline "1366x768"x0.0   69.30  1366 1382 1416 1466  768 770 776 788 -hsync -vsync (47.3 kHz eP)
[ 23441.959] (II) RADEON(0): EDID vendor "CMO", prod id 5543
[ 23441.959] (II) RADEON(0): Printing DDC gathered Modelines:
[ 23441.959] (II) RADEON(0): Modeline "1366x768"x0.0   69.30  1366 1382 1416 1466  768 770 776 788 -hsync -vsync (47.3 kHz eP)
[ 23444.532] (II) RADEON(0): Allocate new frame buffer 3286x1080 stride 3296
[ 23444.533] (II) RADEON(0): VRAM usage limit set to 219383K
[ 23446.024] (II) RADEON(0): EDID vendor "CMO", prod id 5543
[ 23446.024] (II) RADEON(0): Printing DDC gathered Modelines:
[ 23446.024] (II) RADEON(0): Modeline "1366x768"x0.0   69.30  1366 1382 1416 1466  768 770 776 788 -hsync -vsync (47.3 kHz eP)
[ 23446.202] (II) RADEON(0): Allocate new frame buffer 1366x768 stride 1376
[ 23446.214] (II) RADEON(0): VRAM usage limit set to 228182K
[ 23451.319] (II) RADEON(0): EDID vendor "CMO", prod id 5543
[ 23451.319] (II) RADEON(0): Printing DDC gathered Modelines:
[ 23451.319] (II) RADEON(0): Modeline "1366x768"x0.0   69.30  1366 1382 1416 1466  768 770 776 788 -hsync -vsync (47.3 kHz eP)
[ 23451.483] (II) RADEON(0): Allocate new frame buffer 3286x1080 stride 3296
[ 23451.483] (II) RADEON(0): VRAM usage limit set to 219383K
[ 23481.375] (II) RADEON(0): EDID vendor "CMO", prod id 5543
[ 23481.375] (II) RADEON(0): Printing DDC gathered Modelines:
[ 23481.375] (II) RADEON(0): Modeline "1366x768"x0.0   69.30  1366 1382 1416 1466  768 770 776 788 -hsync -vsync (47.3 kHz eP)
[ 23481.534] (II) RADEON(0): Allocate new frame buffer 1366x768 stride 1376
[ 23481.547] (II) RADEON(0): VRAM usage limit set to 228182K
[ 23482.675] (II) RADEON(0): EDID vendor "CMO", prod id 5543
[ 23482.675] (II) RADEON(0): Printing DDC gathered Modelines:
[ 23482.675] (II) RADEON(0): Modeline "1366x768"x0.0   69.30  1366 1382 1416 1466  768 770 776 788 -hsync -vsync (47.3 kHz eP)
[ 23482.758] (II) RADEON(0): Allocate new frame buffer 3286x1080 stride 3296
[ 23482.759] (II) RADEON(0): VRAM usage limit set to 219383K
[ 23526.999] (II) RADEON(0): EDID vendor "CMO", prod id 5543
[ 23526.999] (II) RADEON(0): Printing DDC gathered Modelines:
[ 23526.999] (II) RADEON(0): Modeline "1366x768"x0.0   69.30  1366 1382 1416 1466  768 770 776 788 -hsync -vsync (47.3 kHz eP)
[ 23527.170] (II) RADEON(0): Allocate new frame buffer 1366x768 stride 1376
[ 23527.183] (II) RADEON(0): VRAM usage limit set to 228182K
(EE) [mi] EQ overflowing.  Additional events will be discarded until existing events are processed.
(EE) 
(EE) Backtrace:
(EE) 0: /usr/bin/X (xorg_backtrace+0x36) [0x7f3173545ac6]
(EE) 1: /usr/bin/X (mieqEnqueue+0x26b) [0x7f3173526eab]
(EE) 2: /usr/bin/X (0x7f317339d000+0x6a492) [0x7f3173407492]
(EE) 3: /usr/bin/X (xf86PostMotionEvent+0xd0) [0x7f3173440690]
(EE) 4: /usr/lib/xorg/modules/input/synaptics_drv.so (0x7f316c65b000+0x50b5) [0x7f316c6600b5]
(EE) 5: /usr/lib/xorg/modules/input/synaptics_drv.so (0x7f316c65b000+0x6fd4) [0x7f316c661fd4]
(EE) 6: /usr/bin/X (0x7f317339d000+0x936c7) [0x7f31734306c7]
(EE) 7: /usr/bin/X (0x7f317339d000+0xbce38) [0x7f3173459e38]
(EE) 8: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7f31726c3000+0xfcb0) [0x7f31726d2cb0]
(EE) 9: /lib/x86_64-linux-gnu/libc.so.6 (ioctl+0x7) [0x7f3171413527]
(EE) 10: /usr/lib/x86_64-linux-gnu/libdrm.so.2 (drmIoctl+0x28) [0x7f31724ba328]
(EE) 11: /usr/lib/x86_64-linux-gnu/libdrm.so.2 (drmCommandWriteRead+0x1c) [0x7f31724bc75c]
(EE) 12: /usr/lib/x86_64-linux-gnu/libdrm_radeon.so.1 (0x7f316fd66000+0x1eb9) [0x7f316fd67eb9]
(EE) 13: /usr/lib/x86_64-linux-gnu/libdrm_radeon.so.1 (0x7f316fd66000+0x20e4) [0x7f316fd680e4]
(EE) 14: /usr/lib/xorg/modules/drivers/radeon_drv.so (0x7f316ff70000+0x32200) [0x7f316ffa2200]
(EE) 15: /usr/lib/xorg/modules/libexa.so (0x7f316f331000+0xb660) [0x7f316f33c660]
(EE) 16: /usr/bin/X (0x7f317339d000+0x198df3) [0x7f3173535df3]
(EE) 17: /usr/bin/X (0x7f317339d000+0xe2780) [0x7f317347f780]
(EE) 18: /usr/bin/X (0x7f317339d000+0x52bca) [0x7f31733efbca]
(EE) 19: /usr/bin/X (0x7f317339d000+0x55a51) [0x7f31733f2a51]
(EE) 20: /usr/bin/X (0x7f317339d000+0x4456a) [0x7f31733e156a]
(EE) 21: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xed) [0x7f317134876d]
(EE) 22: /usr/bin/X (0x7f317339d000+0x448ad) [0x7f31733e18ad]
(EE) 
(EE) [mi] These backtraces from mieqEnqueue may point to a culprit higher up the stack.
(EE) [mi] mieq is *NOT* the cause.  It is a victim.
(EE) [mi] EQ overflow continuing.  100 events have been dropped.
(EE) 
(EE) Backtrace:
(EE) 0: /usr/bin/X (xorg_backtrace+0x36) [0x7f3173545ac6]
(EE) 1: /usr/bin/X (0x7f317339d000+0x6a492) [0x7f3173407492]
(EE) 2: /usr/bin/X (xf86PostMotionEvent+0xd0) [0x7f3173440690]
(EE) 3: /usr/lib/xorg/modules/input/synaptics_drv.so (0x7f316c65b000+0x50b5) [0x7f316c6600b5]
(EE) 4: /usr/lib/xorg/modules/input/synaptics_drv.so (0x7f316c65b000+0x6fd4) [0x7f316c661fd4]
(EE) 5: /usr/bin/X (0x7f317339d000+0x936c7) [0x7f31734306c7]
(EE) 6: /usr/bin/X (0x7f317339d000+0xbce38) [0x7f3173459e38]
(EE) 7: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7f31726c3000+0xfcb0) [0x7f31726d2cb0]
(EE) 8: /lib/x86_64-linux-gnu/libc.so.6 (ioctl+0x7) [0x7f3171413527]
(EE) 9: /usr/lib/x86_64-linux-gnu/libdrm.so.2 (drmIoctl+0x28) [0x7f31724ba328]
(EE) 10: /usr/lib/x86_64-linux-gnu/libdrm.so.2 (drmCommandWriteRead+0x1c) [0x7f31724bc75c]
(EE) 11: /usr/lib/x86_64-linux-gnu/libdrm_radeon.so.1 (0x7f316fd66000+0x1eb9) [0x7f316fd67eb9]
(EE) 12: /usr/lib/x86_64-linux-gnu/libdrm_radeon.so.1 (0x7f316fd66000+0x20e4) [0x7f316fd680e4]
(EE) 13: /usr/lib/xorg/modules/drivers/radeon_drv.so (0x7f316ff70000+0x32200) [0x7f316ffa2200]
(EE) 14: /usr/lib/xorg/modules/libexa.so (0x7f316f331000+0xb660) [0x7f316f33c660]
(EE) 15: /usr/bin/X (0x7f317339d000+0x198df3) [0x7f3173535df3]
(EE) 16: /usr/bin/X (0x7f317339d000+0xe2780) [0x7f317347f780]
(EE) 17: /usr/bin/X (0x7f317339d000+0x52bca) [0x7f31733efbca]
(EE) 18: /usr/bin/X (0x7f317339d000+0x55a51) [0x7f31733f2a51]
(EE) 19: /usr/bin/X (0x7f317339d000+0x4456a) [0x7f31733e156a]
(EE) 20: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xed) [0x7f317134876d]
(EE) 21: /usr/bin/X (0x7f317339d000+0x448ad) [0x7f31733e18ad]
(EE) 
(EE) [mi] EQ overflow continuing.  200 events have been dropped.
(EE) 
(EE) Backtrace:
(EE) 0: /usr/bin/X (xorg_backtrace+0x36) [0x7f3173545ac6]
(EE) 1: /usr/bin/X (0x7f317339d000+0x6a492) [0x7f3173407492]
(EE) 2: /usr/bin/X (xf86PostMotionEvent+0xd0) [0x7f3173440690]
(EE) 3: /usr/lib/xorg/modules/input/synaptics_drv.so (0x7f316c65b000+0x50b5) [0x7f316c6600b5]
(EE) 4: /usr/lib/xorg/modules/input/synaptics_drv.so (0x7f316c65b000+0x6fd4) [0x7f316c661fd4]
(EE) 5: /usr/bin/X (0x7f317339d000+0x936c7) [0x7f31734306c7]
(EE) 6: /usr/bin/X (0x7f317339d000+0xbce38) [0x7f3173459e38]
(EE) 7: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7f31726c3000+0xfcb0) [0x7f31726d2cb0]
(EE) 8: /lib/x86_64-linux-gnu/libc.so.6 (ioctl+0x7) [0x7f3171413527]
(EE) 9: /usr/lib/x86_64-linux-gnu/libdrm.so.2 (drmIoctl+0x28) [0x7f31724ba328]
(EE) 10: /usr/lib/x86_64-linux-gnu/libdrm.so.2 (drmCommandWriteRead+0x1c) [0x7f31724bc75c]
(EE) 11: /usr/lib/x86_64-linux-gnu/libdrm_radeon.so.1 (0x7f316fd66000+0x1eb9) [0x7f316fd67eb9]
(EE) 12: /usr/lib/x86_64-linux-gnu/libdrm_radeon.so.1 (0x7f316fd66000+0x20e4) [0x7f316fd680e4]
(EE) 13: /usr/lib/xorg/modules/drivers/radeon_drv.so (0x7f316ff70000+0x32200) [0x7f316ffa2200]
(EE) 14: /usr/lib/xorg/modules/libexa.so (0x7f316f331000+0xb660) [0x7f316f33c660]
(EE) 15: /usr/bin/X (0x7f317339d000+0x198df3) [0x7f3173535df3]
(EE) 16: /usr/bin/X (0x7f317339d000+0xe2780) [0x7f317347f780]
(EE) 17: /usr/bin/X (0x7f317339d000+0x52bca) [0x7f31733efbca]
(EE) 18: /usr/bin/X (0x7f317339d000+0x55a51) [0x7f31733f2a51]
(EE) 19: /usr/bin/X (0x7f317339d000+0x4456a) [0x7f31733e156a]
(EE) 20: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xed) [0x7f317134876d]
(EE) 21: /usr/bin/X (0x7f317339d000+0x448ad) [0x7f31733e18ad]
(EE) 
(EE) [mi] EQ overflow continuing.  300 events have been dropped.
(EE) 
(EE) Backtrace:
(EE) 0: /usr/bin/X (xorg_backtrace+0x36) [0x7f3173545ac6]
(EE) 1: /usr/bin/X (0x7f317339d000+0x6a492) [0x7f3173407492]
(EE) 2: /usr/bin/X (xf86PostMotionEvent+0xd0) [0x7f3173440690]
(EE) 3: /usr/lib/xorg/modules/input/synaptics_drv.so (0x7f316c65b000+0x50b5) [0x7f316c6600b5]
(EE) 4: /usr/lib/xorg/modules/input/synaptics_drv.so (0x7f316c65b000+0x6fd4) [0x7f316c661fd4]
(EE) 5: /usr/bin/X (0x7f317339d000+0x936c7) [0x7f31734306c7]
(EE) 6: /usr/bin/X (0x7f317339d000+0xbce38) [0x7f3173459e38]
(EE) 7: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7f31726c3000+0xfcb0) [0x7f31726d2cb0]
(EE) 8: /lib/x86_64-linux-gnu/libc.so.6 (ioctl+0x7) [0x7f3171413527]
(EE) 9: /usr/lib/x86_64-linux-gnu/libdrm.so.2 (drmIoctl+0x28) [0x7f31724ba328]
(EE) 10: /usr/lib/x86_64-linux-gnu/libdrm.so.2 (drmCommandWriteRead+0x1c) [0x7f31724bc75c]
(EE) 11: /usr/lib/x86_64-linux-gnu/libdrm_radeon.so.1 (0x7f316fd66000+0x1eb9) [0x7f316fd67eb9]
(EE) 12: /usr/lib/x86_64-linux-gnu/libdrm_radeon.so.1 (0x7f316fd66000+0x20e4) [0x7f316fd680e4]
(EE) 13: /usr/lib/xorg/modules/drivers/radeon_drv.so (0x7f316ff70000+0x32200) [0x7f316ffa2200]
(EE) 14: /usr/lib/xorg/modules/libexa.so (0x7f316f331000+0xb660) [0x7f316f33c660]
(EE) 15: /usr/bin/X (0x7f317339d000+0x198df3) [0x7f3173535df3]
(EE) 16: /usr/bin/X (0x7f317339d000+0xe2780) [0x7f317347f780]
(EE) 17: /usr/bin/X (0x7f317339d000+0x52bca) [0x7f31733efbca]
(EE) 18: /usr/bin/X (0x7f317339d000+0x55a51) [0x7f31733f2a51]
(EE) 19: /usr/bin/X (0x7f317339d000+0x4456a) [0x7f31733e156a]
(EE) 20: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xed) [0x7f317134876d]
(EE) 21: /usr/bin/X (0x7f317339d000+0x448ad) [0x7f31733e18ad]
(EE) 
(EE) [mi] EQ overflow continuing.  400 events have been dropped.
(EE) 
(EE) Backtrace:
(EE) 0: /usr/bin/X (xorg_backtrace+0x36) [0x7f3173545ac6]
(EE) 1: /usr/bin/X (0x7f317339d000+0x6a492) [0x7f3173407492]
(EE) 2: /usr/bin/X (xf86PostMotionEvent+0xd0) [0x7f3173440690]
(EE) 3: /usr/lib/xorg/modules/input/synaptics_drv.so (0x7f316c65b000+0x50b5) [0x7f316c6600b5]
(EE) 4: /usr/lib/xorg/modules/input/synaptics_drv.so (0x7f316c65b000+0x6fd4) [0x7f316c661fd4]
(EE) 5: /usr/bin/X (0x7f317339d000+0x936c7) [0x7f31734306c7]
(EE) 6: /usr/bin/X (0x7f317339d000+0xbce38) [0x7f3173459e38]
(EE) 7: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7f31726c3000+0xfcb0) [0x7f31726d2cb0]
(EE) 8: /lib/x86_64-linux-gnu/libc.so.6 (ioctl+0x7) [0x7f3171413527]
(EE) 9: /usr/lib/x86_64-linux-gnu/libdrm.so.2 (drmIoctl+0x28) [0x7f31724ba328]
(EE) 10: /usr/lib/x86_64-linux-gnu/libdrm.so.2 (drmCommandWriteRead+0x1c) [0x7f31724bc75c]
(EE) 11: /usr/lib/x86_64-linux-gnu/libdrm_radeon.so.1 (0x7f316fd66000+0x1eb9) [0x7f316fd67eb9]
(EE) 12: /usr/lib/x86_64-linux-gnu/libdrm_radeon.so.1 (0x7f316fd66000+0x20e4) [0x7f316fd680e4]
(EE) 13: /usr/lib/xorg/modules/drivers/radeon_drv.so (0x7f316ff70000+0x32200) [0x7f316ffa2200]
(EE) 14: /usr/lib/xorg/modules/libexa.so (0x7f316f331000+0xb660) [0x7f316f33c660]
(EE) 15: /usr/bin/X (0x7f317339d000+0x198df3) [0x7f3173535df3]
(EE) 16: /usr/bin/X (0x7f317339d000+0xe2780) [0x7f317347f780]
(EE) 17: /usr/bin/X (0x7f317339d000+0x52bca) [0x7f31733efbca]
(EE) 18: /usr/bin/X (0x7f317339d000+0x55a51) [0x7f31733f2a51]
(EE) 19: /usr/bin/X (0x7f317339d000+0x4456a) [0x7f31733e156a]
(EE) 20: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xed) [0x7f317134876d]
(EE) 21: /usr/bin/X (0x7f317339d000+0x448ad) [0x7f31733e18ad]
(EE) 
(EE) [mi] EQ overflow continuing.  500 events have been dropped.
(EE) 
(EE) Backtrace:
(EE) 0: /usr/bin/X (xorg_backtrace+0x36) [0x7f3173545ac6]
(EE) 1: /usr/bin/X (0x7f317339d000+0x6a492) [0x7f3173407492]
(EE) 2: /usr/bin/X (xf86PostMotionEvent+0xd0) [0x7f3173440690]
(EE) 3: /usr/lib/xorg/modules/input/synaptics_drv.so (0x7f316c65b000+0x50b5) [0x7f316c6600b5]
(EE) 4: /usr/lib/xorg/modules/input/synaptics_drv.so (0x7f316c65b000+0x6fd4) [0x7f316c661fd4]
(EE) 5: /usr/bin/X (0x7f317339d000+0x936c7) [0x7f31734306c7]
(EE) 6: /usr/bin/X (0x7f317339d000+0xbce38) [0x7f3173459e38]
(EE) 7: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7f31726c3000+0xfcb0) [0x7f31726d2cb0]
(EE) 8: /lib/x86_64-linux-gnu/libc.so.6 (ioctl+0x7) [0x7f3171413527]
(EE) 9: /usr/lib/x86_64-linux-gnu/libdrm.so.2 (drmIoctl+0x28) [0x7f31724ba328]
(EE) 10: /usr/lib/x86_64-linux-gnu/libdrm.so.2 (drmCommandWriteRead+0x1c) [0x7f31724bc75c]
(EE) 11: /usr/lib/x86_64-linux-gnu/libdrm_radeon.so.1 (0x7f316fd66000+0x1eb9) [0x7f316fd67eb9]
(EE) 12: /usr/lib/x86_64-linux-gnu/libdrm_radeon.so.1 (0x7f316fd66000+0x20e4) [0x7f316fd680e4]
(EE) 13: /usr/lib/xorg/modules/drivers/radeon_drv.so (0x7f316ff70000+0x32200) [0x7f316ffa2200]
(EE) 14: /usr/lib/xorg/modules/libexa.so (0x7f316f331000+0xb660) [0x7f316f33c660]
(EE) 15: /usr/bin/X (0x7f317339d000+0x198df3) [0x7f3173535df3]
(EE) 16: /usr/bin/X (0x7f317339d000+0xe2780) [0x7f317347f780]
(EE) 17: /usr/bin/X (0x7f317339d000+0x52bca) [0x7f31733efbca]
(EE) 18: /usr/bin/X (0x7f317339d000+0x55a51) [0x7f31733f2a51]
(EE) 19: /usr/bin/X (0x7f317339d000+0x4456a) [0x7f31733e156a]
(EE) 20: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xed) [0x7f317134876d]
(EE) 21: /usr/bin/X (0x7f317339d000+0x448ad) [0x7f31733e18ad]
(EE) 
(EE) [mi] EQ overflow continuing.  600 events have been dropped.
(EE) 
(EE) Backtrace:
(EE) 0: /usr/bin/X (xorg_backtrace+0x36) [0x7f3173545ac6]
(EE) 1: /usr/bin/X (0x7f317339d000+0x6a492) [0x7f3173407492]
(EE) 2: /usr/bin/X (xf86PostMotionEvent+0xd0) [0x7f3173440690]
(EE) 3: /usr/lib/xorg/modules/input/synaptics_drv.so (0x7f316c65b000+0x50b5) [0x7f316c6600b5]
(EE) 4: /usr/lib/xorg/modules/input/synaptics_drv.so (0x7f316c65b000+0x6fd4) [0x7f316c661fd4]
(EE) 5: /usr/bin/X (0x7f317339d000+0x936c7) [0x7f31734306c7]
(EE) 6: /usr/bin/X (0x7f317339d000+0xbce38) [0x7f3173459e38]
(EE) 7: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7f31726c3000+0xfcb0) [0x7f31726d2cb0]
(EE) 8: /lib/x86_64-linux-gnu/libc.so.6 (ioctl+0x7) [0x7f3171413527]
(EE) 9: /usr/lib/x86_64-linux-gnu/libdrm.so.2 (drmIoctl+0x28) [0x7f31724ba328]
(EE) 10: /usr/lib/x86_64-linux-gnu/libdrm.so.2 (drmCommandWriteRead+0x1c) [0x7f31724bc75c]
(EE) 11: /usr/lib/x86_64-linux-gnu/libdrm_radeon.so.1 (0x7f316fd66000+0x1eb9) [0x7f316fd67eb9]
(EE) 12: /usr/lib/x86_64-linux-gnu/libdrm_radeon.so.1 (0x7f316fd66000+0x20e4) [0x7f316fd680e4]
(EE) 13: /usr/lib/xorg/modules/drivers/radeon_drv.so (0x7f316ff70000+0x32200) [0x7f316ffa2200]
(EE) 14: /usr/lib/xorg/modules/libexa.so (0x7f316f331000+0xb660) [0x7f316f33c660]
(EE) 15: /usr/bin/X (0x7f317339d000+0x198df3) [0x7f3173535df3]
(EE) 16: /usr/bin/X (0x7f317339d000+0xe2780) [0x7f317347f780]
(EE) 17: /usr/bin/X (0x7f317339d000+0x52bca) [0x7f31733efbca]
(EE) 18: /usr/bin/X (0x7f317339d000+0x55a51) [0x7f31733f2a51]
(EE) 19: /usr/bin/X (0x7f317339d000+0x4456a) [0x7f31733e156a]
(EE) 20: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xed) [0x7f317134876d]
(EE) 21: /usr/bin/X (0x7f317339d000+0x448ad) [0x7f31733e18ad]
(EE) 
(EE) [mi] EQ overflow continuing.  700 events have been dropped.
(EE) 
(EE) Backtrace:
(EE) 0: /usr/bin/X (xorg_backtrace+0x36) [0x7f3173545ac6]
(EE) 1: /usr/bin/X (0x7f317339d000+0x6a492) [0x7f3173407492]
(EE) 2: /usr/bin/X (xf86PostMotionEvent+0xd0) [0x7f3173440690]
(EE) 3: /usr/lib/xorg/modules/input/synaptics_drv.so (0x7f316c65b000+0x50b5) [0x7f316c6600b5]
(EE) 4: /usr/lib/xorg/modules/input/synaptics_drv.so (0x7f316c65b000+0x6fd4) [0x7f316c661fd4]
(EE) 5: /usr/bin/X (0x7f317339d000+0x936c7) [0x7f31734306c7]
(EE) 6: /usr/bin/X (0x7f317339d000+0xbce38) [0x7f3173459e38]
(EE) 7: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7f31726c3000+0xfcb0) [0x7f31726d2cb0]
(EE) 8: /lib/x86_64-linux-gnu/libc.so.6 (ioctl+0x7) [0x7f3171413527]
(EE) 9: /usr/lib/x86_64-linux-gnu/libdrm.so.2 (drmIoctl+0x28) [0x7f31724ba328]
(EE) 10: /usr/lib/x86_64-linux-gnu/libdrm.so.2 (drmCommandWriteRead+0x1c) [0x7f31724bc75c]
(EE) 11: /usr/lib/x86_64-linux-gnu/libdrm_radeon.so.1 (0x7f316fd66000+0x1eb9) [0x7f316fd67eb9]
(EE) 12: /usr/lib/x86_64-linux-gnu/libdrm_radeon.so.1 (0x7f316fd66000+0x20e4) [0x7f316fd680e4]
(EE) 13: /usr/lib/xorg/modules/drivers/radeon_drv.so (0x7f316ff70000+0x32200) [0x7f316ffa2200]
(EE) 14: /usr/lib/xorg/modules/libexa.so (0x7f316f331000+0xb660) [0x7f316f33c660]
(EE) 15: /usr/bin/X (0x7f317339d000+0x198df3) [0x7f3173535df3]
(EE) 16: /usr/bin/X (0x7f317339d000+0xe2780) [0x7f317347f780]
(EE) 17: /usr/bin/X (0x7f317339d000+0x52bca) [0x7f31733efbca]
(EE) 18: /usr/bin/X (0x7f317339d000+0x55a51) [0x7f31733f2a51]
(EE) 19: /usr/bin/X (0x7f317339d000+0x4456a) [0x7f31733e156a]
(EE) 20: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xed) [0x7f317134876d]
(EE) 21: /usr/bin/X (0x7f317339d000+0x448ad) [0x7f31733e18ad]
(EE) 
(EE) [mi] EQ overflow continuing.  800 events have been dropped.
(EE) 
(EE) Backtrace:
(EE) 0: /usr/bin/X (xorg_backtrace+0x36) [0x7f3173545ac6]
(EE) 1: /usr/bin/X (0x7f317339d000+0x6a492) [0x7f3173407492]
(EE) 2: /usr/bin/X (xf86PostMotionEvent+0xd0) [0x7f3173440690]
(EE) 3: /usr/lib/xorg/modules/input/synaptics_drv.so (0x7f316c65b000+0x50b5) [0x7f316c6600b5]
(EE) 4: /usr/lib/xorg/modules/input/synaptics_drv.so (0x7f316c65b000+0x6fd4) [0x7f316c661fd4]
(EE) 5: /usr/bin/X (0x7f317339d000+0x936c7) [0x7f31734306c7]
(EE) 6: /usr/bin/X (0x7f317339d000+0xbce38) [0x7f3173459e38]
(EE) 7: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7f31726c3000+0xfcb0) [0x7f31726d2cb0]
(EE) 8: /lib/x86_64-linux-gnu/libc.so.6 (ioctl+0x7) [0x7f3171413527]
(EE) 9: /usr/lib/x86_64-linux-gnu/libdrm.so.2 (drmIoctl+0x28) [0x7f31724ba328]
(EE) 10: /usr/lib/x86_64-linux-gnu/libdrm.so.2 (drmCommandWriteRead+0x1c) [0x7f31724bc75c]
(EE) 11: /usr/lib/x86_64-linux-gnu/libdrm_radeon.so.1 (0x7f316fd66000+0x1eb9) [0x7f316fd67eb9]
(EE) 12: /usr/lib/x86_64-linux-gnu/libdrm_radeon.so.1 (0x7f316fd66000+0x20e4) [0x7f316fd680e4]
(EE) 13: /usr/lib/xorg/modules/drivers/radeon_drv.so (0x7f316ff70000+0x32200) [0x7f316ffa2200]
(EE) 14: /usr/lib/xorg/modules/libexa.so (0x7f316f331000+0xb660) [0x7f316f33c660]
(EE) 15: /usr/bin/X (0x7f317339d000+0x198df3) [0x7f3173535df3]
(EE) 16: /usr/bin/X (0x7f317339d000+0xe2780) [0x7f317347f780]
(EE) 17: /usr/bin/X (0x7f317339d000+0x52bca) [0x7f31733efbca]
(EE) 18: /usr/bin/X (0x7f317339d000+0x55a51) [0x7f31733f2a51]
(EE) 19: /usr/bin/X (0x7f317339d000+0x4456a) [0x7f31733e156a]
(EE) 20: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xed) [0x7f317134876d]
(EE) 21: /usr/bin/X (0x7f317339d000+0x448ad) [0x7f31733e18ad]
(EE) 
(EE) [mi] EQ overflow continuing.  900 events have been dropped.
(EE) 
(EE) Backtrace:
(EE) 0: /usr/bin/X (xorg_backtrace+0x36) [0x7f3173545ac6]
(EE) 1: /usr/bin/X (0x7f317339d000+0x6a492) [0x7f3173407492]
(EE) 2: /usr/bin/X (xf86PostMotionEvent+0xd0) [0x7f3173440690]
(EE) 3: /usr/lib/xorg/modules/input/synaptics_drv.so (0x7f316c65b000+0x50b5) [0x7f316c6600b5]
(EE) 4: /usr/lib/xorg/modules/input/synaptics_drv.so (0x7f316c65b000+0x6fd4) [0x7f316c661fd4]
(EE) 5: /usr/bin/X (0x7f317339d000+0x936c7) [0x7f31734306c7]
(EE) 6: /usr/bin/X (0x7f317339d000+0xbce38) [0x7f3173459e38]
(EE) 7: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7f31726c3000+0xfcb0) [0x7f31726d2cb0]
(EE) 8: /lib/x86_64-linux-gnu/libc.so.6 (ioctl+0x7) [0x7f3171413527]
(EE) 9: /usr/lib/x86_64-linux-gnu/libdrm.so.2 (drmIoctl+0x28) [0x7f31724ba328]
(EE) 10: /usr/lib/x86_64-linux-gnu/libdrm.so.2 (drmCommandWriteRead+0x1c) [0x7f31724bc75c]
(EE) 11: /usr/lib/x86_64-linux-gnu/libdrm_radeon.so.1 (0x7f316fd66000+0x1eb9) [0x7f316fd67eb9]
(EE) 12: /usr/lib/x86_64-linux-gnu/libdrm_radeon.so.1 (0x7f316fd66000+0x20e4) [0x7f316fd680e4]
(EE) 13: /usr/lib/xorg/modules/drivers/radeon_drv.so (0x7f316ff70000+0x32200) [0x7f316ffa2200]
(EE) 14: /usr/lib/xorg/modules/libexa.so (0x7f316f331000+0xb660) [0x7f316f33c660]
(EE) 15: /usr/bin/X (0x7f317339d000+0x198df3) [0x7f3173535df3]
(EE) 16: /usr/bin/X (0x7f317339d000+0xe2780) [0x7f317347f780]
(EE) 17: /usr/bin/X (0x7f317339d000+0x52bca) [0x7f31733efbca]
(EE) 18: /usr/bin/X (0x7f317339d000+0x55a51) [0x7f31733f2a51]
(EE) 19: /usr/bin/X (0x7f317339d000+0x4456a) [0x7f31733e156a]
(EE) 20: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xed) [0x7f317134876d]
(EE) 21: /usr/bin/X (0x7f317339d000+0x448ad) [0x7f31733e18ad]
(EE) 
(EE) [mi] EQ overflow continuing.  1000 events have been dropped.
(EE) [mi] No further overflow reports will be reported until the clog is cleared.
(EE) 
(EE) Backtrace:
(EE) 0: /usr/bin/X (xorg_backtrace+0x36) [0x7f3173545ac6]
(EE) 1: /usr/bin/X (0x7f317339d000+0x6a492) [0x7f3173407492]
(EE) 2: /usr/bin/X (xf86PostMotionEvent+0xd0) [0x7f3173440690]
(EE) 3: /usr/lib/xorg/modules/input/synaptics_drv.so (0x7f316c65b000+0x50b5) [0x7f316c6600b5]
(EE) 4: /usr/lib/xorg/modules/input/synaptics_drv.so (0x7f316c65b000+0x6fd4) [0x7f316c661fd4]
(EE) 5: /usr/bin/X (0x7f317339d000+0x936c7) [0x7f31734306c7]
(EE) 6: /usr/bin/X (0x7f317339d000+0xbce38) [0x7f3173459e38]
(EE) 7: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7f31726c3000+0xfcb0) [0x7f31726d2cb0]
(EE) 8: /lib/x86_64-linux-gnu/libc.so.6 (ioctl+0x7) [0x7f3171413527]
(EE) 9: /usr/lib/x86_64-linux-gnu/libdrm.so.2 (drmIoctl+0x28) [0x7f31724ba328]
(EE) 10: /usr/lib/x86_64-linux-gnu/libdrm.so.2 (drmCommandWriteRead+0x1c) [0x7f31724bc75c]
(EE) 11: /usr/lib/x86_64-linux-gnu/libdrm_radeon.so.1 (0x7f316fd66000+0x1eb9) [0x7f316fd67eb9]
(EE) 12: /usr/lib/x86_64-linux-gnu/libdrm_radeon.so.1 (0x7f316fd66000+0x20e4) [0x7f316fd680e4]
(EE) 13: /usr/lib/xorg/modules/drivers/radeon_drv.so (0x7f316ff70000+0x32200) [0x7f316ffa2200]
(EE) 14: /usr/lib/xorg/modules/libexa.so (0x7f316f331000+0xb660) [0x7f316f33c660]
(EE) 15: /usr/bin/X (0x7f317339d000+0x198df3) [0x7f3173535df3]
(EE) 16: /usr/bin/X (0x7f317339d000+0xe2780) [0x7f317347f780]
(EE) 17: /usr/bin/X (0x7f317339d000+0x52bca) [0x7f31733efbca]
(EE) 18: /usr/bin/X (0x7f317339d000+0x55a51) [0x7f31733f2a51]
(EE) 19: /usr/bin/X (0x7f317339d000+0x4456a) [0x7f31733e156a]
(EE) 20: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xed) [0x7f317134876d]
(EE) 21: /usr/bin/X (0x7f317339d000+0x448ad) [0x7f31733e18ad]
(EE) 
[ 23588.508] [mi] Increasing EQ size to 512 to prevent dropped events.
[ 23588.509] [mi] EQ processing has resumed after 1450 dropped events.
[ 23588.509] [mi] This may be caused my a misbehaving driver monopolizing the server's resources.
[ 23588.711] (II) RADEON(0): EDID vendor "CMO", prod id 5543
[ 23588.711] (II) RADEON(0): Printing DDC gathered Modelines:
[ 23588.711] (II) RADEON(0): Modeline "1366x768"x0.0   69.30  1366 1382 1416 1466  768 770 776 788 -hsync -vsync (47.3 kHz eP)
(EE) [mi] EQ overflowing.  Additional events will be discarded until existing events are processed.
(EE) 
(EE) Backtrace:
(EE) 0: /usr/bin/X (xorg_backtrace+0x36) [0x7f3173545ac6]
(EE) 1: /usr/bin/X (mieqEnqueue+0x26b) [0x7f3173526eab]
(EE) 2: /usr/bin/X (0x7f317339d000+0x6a492) [0x7f3173407492]
(EE) 3: /usr/bin/X (xf86PostMotionEvent+0xd0) [0x7f3173440690]
(EE) 4: /usr/lib/xorg/modules/input/synaptics_drv.so (0x7f316c65b000+0x50b5) [0x7f316c6600b5]
(EE) 5: /usr/lib/xorg/modules/input/synaptics_drv.so (0x7f316c65b000+0x6fd4) [0x7f316c661fd4]
(EE) 6: /usr/bin/X (0x7f317339d000+0x936c7) [0x7f31734306c7]
(EE) 7: /usr/bin/X (0x7f317339d000+0xbce38) [0x7f3173459e38]
(EE) 8: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7f31726c3000+0xfcb0) [0x7f31726d2cb0]
(EE) 9: /lib/x86_64-linux-gnu/libc.so.6 (ioctl+0x7) [0x7f3171413527]
(EE) 10: /usr/lib/x86_64-linux-gnu/libdrm.so.2 (drmIoctl+0x28) [0x7f31724ba328]
(EE) 11: /usr/lib/x86_64-linux-gnu/libdrm.so.2 (drmCommandWriteRead+0x1c) [0x7f31724bc75c]
(EE) 12: /usr/lib/x86_64-linux-gnu/libdrm_radeon.so.1 (0x7f316fd66000+0x1eb9) [0x7f316fd67eb9]
(EE) 13: /usr/lib/x86_64-linux-gnu/libdrm_radeon.so.1 (0x7f316fd66000+0x20e4) [0x7f316fd680e4]
(EE) 14: /usr/lib/xorg/modules/drivers/radeon_drv.so (0x7f316ff70000+0x32200) [0x7f316ffa2200]
(EE) 15: /usr/lib/xorg/modules/libexa.so (0x7f316f331000+0x5bff) [0x7f316f336bff]
(EE) 16: /usr/lib/xorg/modules/libexa.so (0x7f316f331000+0x851a) [0x7f316f33951a]
(EE) 17: /usr/lib/xorg/modules/libexa.so (0x7f316f331000+0x50e1) [0x7f316f3360e1]
(EE) 18: /usr/bin/X (0x7f317339d000+0xe261f) [0x7f317347f61f]
(EE) 19: /usr/bin/X (ChangeWindowAttributes+0x244) [0x7f3173420374]
(EE) 20: /usr/bin/X (0x7f317339d000+0x4ff0d) [0x7f31733ecf0d]
(EE) 21: /usr/bin/X (0x7f317339d000+0x55a51) [0x7f31733f2a51]
(EE) 22: /usr/bin/X (0x7f317339d000+0x4456a) [0x7f31733e156a]
(EE) 23: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xed) [0x7f317134876d]
(EE) 24: /usr/bin/X (0x7f317339d000+0x448ad) [0x7f31733e18ad]
(EE) 
(EE) [mi] These backtraces from mieqEnqueue may point to a culprit higher up the stack.
(EE) [mi] mieq is *NOT* the cause.  It is a victim.
(EE) [mi] EQ overflow continuing.  100 events have been dropped.
(EE) 
(EE) Backtrace:
(EE) 0: /usr/bin/X (xorg_backtrace+0x36) [0x7f3173545ac6]
(EE) 1: /usr/bin/X (0x7f317339d000+0x6a492) [0x7f3173407492]
(EE) 2: /usr/bin/X (xf86PostMotionEvent+0xd0) [0x7f3173440690]
(EE) 3: /usr/lib/xorg/modules/input/synaptics_drv.so (0x7f316c65b000+0x50b5) [0x7f316c6600b5]
(EE) 4: /usr/lib/xorg/modules/input/synaptics_drv.so (0x7f316c65b000+0x6fd4) [0x7f316c661fd4]
(EE) 5: /usr/bin/X (0x7f317339d000+0x936c7) [0x7f31734306c7]
(EE) 6: /usr/bin/X (0x7f317339d000+0xbce38) [0x7f3173459e38]
(EE) 7: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7f31726c3000+0xfcb0) [0x7f31726d2cb0]
(EE) 8: /lib/x86_64-linux-gnu/libc.so.6 (ioctl+0x7) [0x7f3171413527]
(EE) 9: /usr/lib/x86_64-linux-gnu/libdrm.so.2 (drmIoctl+0x28) [0x7f31724ba328]
(EE) 10: /usr/lib/x86_64-linux-gnu/libdrm.so.2 (drmCommandWriteRead+0x1c) [0x7f31724bc75c]
(EE) 11: /usr/lib/x86_64-linux-gnu/libdrm_radeon.so.1 (0x7f316fd66000+0x1eb9) [0x7f316fd67eb9]
(EE) 12: /usr/lib/x86_64-linux-gnu/libdrm_radeon.so.1 (0x7f316fd66000+0x20e4) [0x7f316fd680e4]
(EE) 13: /usr/lib/xorg/modules/drivers/radeon_drv.so (0x7f316ff70000+0x32200) [0x7f316ffa2200]
(EE) 14: /usr/lib/xorg/modules/libexa.so (0x7f316f331000+0x5bff) [0x7f316f336bff]
(EE) 15: /usr/lib/xorg/modules/libexa.so (0x7f316f331000+0x851a) [0x7f316f33951a]
(EE) 16: /usr/lib/xorg/modules/libexa.so (0x7f316f331000+0x50e1) [0x7f316f3360e1]
(EE) 17: /usr/bin/X (0x7f317339d000+0xe261f) [0x7f317347f61f]
(EE) 18: /usr/bin/X (ChangeWindowAttributes+0x244) [0x7f3173420374]
(EE) 19: /usr/bin/X (0x7f317339d000+0x4ff0d) [0x7f31733ecf0d]
(EE) 20: /usr/bin/X (0x7f317339d000+0x55a51) [0x7f31733f2a51]
(EE) 21: /usr/bin/X (0x7f317339d000+0x4456a) [0x7f31733e156a]
(EE) 22: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xed) [0x7f317134876d]
(EE) 23: /usr/bin/X (0x7f317339d000+0x448ad) [0x7f31733e18ad]
(EE) 
[ 23599.432] [mi] Increasing EQ size to 1024 to prevent dropped events.
[ 23599.432] [mi] EQ processing has resumed after 171 dropped events.
[ 23599.432] [mi] This may be caused my a misbehaving driver monopolizing the server's resources.
[ 23660.663] (II) RADEON(0): EDID vendor "CMO", prod id 5543
[ 23660.663] (II) RADEON(0): Printing DDC gathered Modelines:
[ 23660.663] (II) RADEON(0): Modeline "1366x768"x0.0   69.30  1366 1382 1416 1466  768 770 776 788 -hsync -vsync (47.3 kHz eP)
[ 23660.803] (II) AIGLX: Suspending AIGLX clients for VT switch
```

---

