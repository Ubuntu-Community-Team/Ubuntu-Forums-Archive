---
title: "Problem with getting Acer-family laptop keyboards to work with Kubuntu"
date: 2015-07-21
forum: Hardware
---

### Post by dwhitney67 on 2015-07-21
Hello,

I have two dissimilar laptop computers that are from the Acer-family:  a Gateway and an eMachine.

On both systems, following an installation of Kubuntu 14.04 LTS, the keyboard on both systems does not fully function properly.  Sometimes I am required to press a key multiple times before the character is displayed, in other cases a single press of a key generates multiple characters, and in rare cases it seems that the keyboard works fine.  Obviously these issues present problems when trying to enter a password (which cannot be seen).

I know that the keyboards on both systems work fine; tested under the BIOS (performed keystrokes while entering BIOS password).

Anyhow, if I did not know better, it would almost seem that the problem I am witnessing is related to a keyboard-interrupt issue whilst the Kubuntu OS is in control.

I've tried testing with the "Generic | Generic 101-key PC" and the "Acer | Acer Laptop", but the same problem occurs.

Is there perhaps something that I need to configure within GRUB to get the keyboard to function?  When I booted my eMachine, using the "Acer | Acer Laptop" configuration, Xorg deduced I had a "pc105" keyboard.

-----------

Here's some additional info from the eMachine:


```
# dmesg | grep -i keyboard
[    2.147651] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
```


From /var/log/Xorg.log.0
```

[    24.419] 
X.Org X Server 1.16.0
Release Date: 2014-07-16
[    24.419] X Protocol Version 11, Revision 0
[    24.419] Build Operating System: Linux 3.2.0-70-generic x86_64 Ubuntu
[    24.419] Current Operating System: Linux eMachine 3.16.0-43-generic #58~14.04.1-Ubuntu SMP Mon Jun 22 10:21:20 UTC 2015 x86_64
[    24.419] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.16.0-43-generic root=UUID=d4bff399-10d2-4f90-82ed-176f38977a50 ro quiet splash vt.handoff=7
[    24.419] Build Date: 12 February 2015  11:11:26PM
[    24.419] xorg-server 2:1.16.0-1ubuntu1.2~trusty2 (For technical support please see http://www.ubuntu.com/support) 
[    24.419] Current version of pixman: 0.30.2
[    24.419] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    24.419] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    24.419] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Jul 22 04:39:20 2015
[    24.444] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    24.454] (==) No Layout section.  Using the first Screen section.
[    24.454] (==) No screen section available. Using defaults.
[    24.454] (**) |-->Screen "Default Screen Section" (0)
[    24.454] (**) |   |-->Monitor "<default monitor>"
[    24.454] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    24.454] (==) Automatically adding devices
[    24.454] (==) Automatically enabling devices
[    24.454] (==) Automatically adding GPU devices
[    24.496] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    24.496] 	Entry deleted from font path.
[    24.496] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    24.496] 	Entry deleted from font path.
[    24.496] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    24.496] 	Entry deleted from font path.
[    24.497] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    24.497] 	Entry deleted from font path.
[    24.497] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    24.497] 	Entry deleted from font path.
[    24.497] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    24.497] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    24.497] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    24.497] (II) Loader magic: 0x7eff32307c80
[    24.497] (II) Module ABI versions:
[    24.497] 	X.Org ANSI C Emulation: 0.4
[    24.497] 	X.Org Video Driver: 18.0
[    24.497] 	X.Org XInput driver : 21.0
[    24.497] 	X.Org Server Extension : 8.0
[    24.497] (II) xfree86: Adding drm device (/dev/dri/card0)
[    24.498] (--) PCI:*(0:1:5:0) 1002:9712:1025:0377 rev 0, Mem @ 0xc0000000/268435456, 0xd0100000/65536, 0xd0000000/1048576, I/O @ 0x00009000/256
[    24.498] (II) LoadModule: "glx"
[    24.546] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    24.724] (II) Module glx: vendor="X.Org Foundation"
[    24.724] 	compiled for 1.16.0, module version = 1.0.0
[    24.724] 	ABI class: X.Org Server Extension, version 8.0
[    24.724] (==) AIGLX enabled
[    24.724] (==) Matched fglrx as autoconfigured driver 0
[    24.724] (==) Matched ati as autoconfigured driver 1
[    24.724] (==) Matched fglrx as autoconfigured driver 2
[    24.724] (==) Matched ati as autoconfigured driver 3
[    24.724] (==) Matched modesetting as autoconfigured driver 4
[    24.724] (==) Matched fbdev as autoconfigured driver 5
[    24.724] (==) Matched vesa as autoconfigured driver 6
[    24.724] (==) Assigned the driver to the xf86ConfigLayout
[    24.724] (II) LoadModule: "fglrx"
[    24.736] (WW) Warning, couldn't open module fglrx
[    24.736] (II) UnloadModule: "fglrx"
[    24.736] (II) Unloading fglrx
[    24.736] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    24.736] (II) LoadModule: "ati"
[    24.737] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    24.749] (II) Module ati: vendor="X.Org Foundation"
[    24.749] 	compiled for 1.16.0, module version = 7.4.0
[    24.749] 	Module class: X.Org Video Driver
[    24.749] 	ABI class: X.Org Video Driver, version 18.0
[    24.749] (II) LoadModule: "radeon"
[    24.749] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    24.779] (II) Module radeon: vendor="X.Org Foundation"
[    24.779] 	compiled for 1.16.0, module version = 7.4.0
[    24.779] 	Module class: X.Org Video Driver
[    24.779] 	ABI class: X.Org Video Driver, version 18.0
[    24.779] (II) LoadModule: "modesetting"
[    24.779] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    24.789] (II) Module modesetting: vendor="X.Org Foundation"
[    24.789] 	compiled for 1.16.0, module version = 0.9.0
[    24.789] 	Module class: X.Org Video Driver
[    24.789] 	ABI class: X.Org Video Driver, version 18.0
[    24.789] (II) LoadModule: "fbdev"
[    24.789] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    24.790] (II) Module fbdev: vendor="X.Org Foundation"
[    24.790] 	compiled for 1.16.0, module version = 0.4.4
[    24.790] 	Module class: X.Org Video Driver
[    24.790] 	ABI class: X.Org Video Driver, version 18.0
[    24.790] (II) LoadModule: "vesa"
[    24.790] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    24.794] (II) Module vesa: vendor="X.Org Foundation"
[    24.794] 	compiled for 1.16.0, module version = 2.3.3
[    24.794] 	Module class: X.Org Video Driver
[    24.794] 	ABI class: X.Org Video Driver, version 18.0
[    24.794] (==) Matched fglrx as autoconfigured driver 0
[    24.794] (==) Matched ati as autoconfigured driver 1
[    24.794] (==) Matched fglrx as autoconfigured driver 2
[    24.794] (==) Matched ati as autoconfigured driver 3
[    24.794] (==) Matched modesetting as autoconfigured driver 4
[    24.794] (==) Matched fbdev as autoconfigured driver 5
[    24.794] (==) Matched vesa as autoconfigured driver 6
[    24.794] (==) Assigned the driver to the xf86ConfigLayout
[    24.794] (II) LoadModule: "fglrx"
[    24.795] (WW) Warning, couldn't open module fglrx
[    24.795] (II) UnloadModule: "fglrx"
[    24.795] (II) Unloading fglrx
[    24.795] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    24.795] (II) LoadModule: "ati"
[    24.795] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    24.795] (II) Module ati: vendor="X.Org Foundation"
[    24.795] 	compiled for 1.16.0, module version = 7.4.0
[    24.795] 	Module class: X.Org Video Driver
[    24.795] 	ABI class: X.Org Video Driver, version 18.0
[    24.795] (II) LoadModule: "modesetting"
[    24.795] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    24.795] (II) Module modesetting: vendor="X.Org Foundation"
[    24.795] 	compiled for 1.16.0, module version = 0.9.0
[    24.795] 	Module class: X.Org Video Driver
[    24.795] 	ABI class: X.Org Video Driver, version 18.0
[    24.795] (II) UnloadModule: "modesetting"
[    24.795] (II) Unloading modesetting
[    24.795] (II) Failed to load module "modesetting" (already loaded, 0)
[    24.795] (II) LoadModule: "fbdev"
[    24.795] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    24.795] (II) Module fbdev: vendor="X.Org Foundation"
[    24.795] 	compiled for 1.16.0, module version = 0.4.4
[    24.795] 	Module class: X.Org Video Driver
[    24.795] 	ABI class: X.Org Video Driver, version 18.0
[    24.795] (II) UnloadModule: "fbdev"
[    24.795] (II) Unloading fbdev
[    24.795] (II) Failed to load module "fbdev" (already loaded, 0)
[    24.795] (II) LoadModule: "vesa"
[    24.796] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    24.796] (II) Module vesa: vendor="X.Org Foundation"
[    24.796] 	compiled for 1.16.0, module version = 2.3.3
[    24.796] 	Module class: X.Org Video Driver
[    24.796] 	ABI class: X.Org Video Driver, version 18.0
[    24.796] (II) UnloadModule: "vesa"
[    24.796] (II) Unloading vesa
[    24.796] (II) Failed to load module "vesa" (already loaded, 0)
[    24.796] (II) RADEON: Driver for ATI Radeon chipsets:
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
	SUMO, SUMO, SUMO2, SUMO, SUMO, SUMO, SUMO, SUMO, ATI Radeon HD 4200,
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
	ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
	ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, TAHITI, TAHITI, TAHITI, TAHITI,
	TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI,
	TAHITI, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
	PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
	VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
	VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
	VERDE, VERDE, VERDE, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND,
	OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, HAINAN, HAINAN, HAINAN,
	HAINAN, HAINAN, HAINAN, BONAIRE, BONAIRE, BONAIRE, BONAIRE, BONAIRE,
	BONAIRE, BONAIRE, BONAIRE, KABINI, KABINI, KABINI, KABINI, KABINI,
	KABINI, KABINI, KABINI, KABINI, KABINI, KABINI, KABINI, KABINI,
	KABINI, KABINI, KABINI, MULLINS, MULLINS, MULLINS, MULLINS, MULLINS,
	MULLINS, MULLINS, MULLINS, MULLINS, MULLINS, MULLINS, MULLINS,
	MULLINS, MULLINS, MULLINS, MULLINS, KAVERI, KAVERI, KAVERI, KAVERI,
	KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
	KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
	KAVERI, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII,
	HAWAII, HAWAII, HAWAII, HAWAII, HAWAII
[    24.801] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    24.801] (II) FBDEV: driver for framebuffer: fbdev
[    24.801] (II) VESA: driver for VESA chipsets: vesa
[    24.801] (++) using VT number 7

[    24.815] (II) [KMS] Kernel modesetting enabled.
[    24.815] (WW) Falling back to old probe method for modesetting
[    24.815] (WW) Falling back to old probe method for fbdev
[    24.815] (II) Loading sub module "fbdevhw"
[    24.815] (II) LoadModule: "fbdevhw"
[    24.816] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    24.830] (II) Module fbdevhw: vendor="X.Org Foundation"
[    24.830] 	compiled for 1.16.0, module version = 0.0.2
[    24.830] 	ABI class: X.Org Video Driver, version 18.0
[    24.830] (WW) Falling back to old probe method for vesa
[    24.830] (II) RADEON(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    24.830] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    24.830] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    24.830] (==) RADEON(0): Default visual is TrueColor
[    24.830] (==) RADEON(0): RGB weight 888
[    24.830] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    24.830] (--) RADEON(0): Chipset: "ATI Mobility Radeon HD 4200" (ChipID = 0x9712)
[    24.830] (II) Loading sub module "dri2"
[    24.830] (II) LoadModule: "dri2"
[    24.830] (II) Module "dri2" already built-in
[    24.830] (II) Loading sub module "exa"
[    24.830] (II) LoadModule: "exa"
[    24.830] (II) Loading /usr/lib/xorg/modules/libexa.so
[    24.838] (II) Module exa: vendor="X.Org Foundation"
[    24.838] 	compiled for 1.16.0, module version = 2.6.0
[    24.838] 	ABI class: X.Org Video Driver, version 18.0
[    24.838] (II) RADEON(0): KMS Color Tiling: enabled
[    24.838] (II) RADEON(0): KMS Color Tiling 2D: enabled
[    24.838] (II) RADEON(0): KMS Pageflipping: enabled
[    24.838] (II) RADEON(0): SwapBuffers wait for vsync: enabled
[    24.860] (II) RADEON(0): Output VGA-0 has no monitor section
[    24.860] (II) RADEON(0): Output LVDS has no monitor section
[    24.862] (II) RADEON(0): Output HDMI-0 has no monitor section
[    24.884] (II) RADEON(0): EDID for output VGA-0
[    24.884] (II) RADEON(0): EDID for output LVDS
[    24.884] (II) RADEON(0): Manufacturer: CMO  Model: 1444  Serial#: 0
[    24.884] (II) RADEON(0): Year: 2008  Week: 41
[    24.884] (II) RADEON(0): EDID Version: 1.3
[    24.884] (II) RADEON(0): Digital Display Input
[    24.884] (II) RADEON(0): Max Image Size [cm]: horiz.: 31  vert.: 17
[    24.884] (II) RADEON(0): Gamma: 2.20
[    24.884] (II) RADEON(0): No DPMS capabilities specified
[    24.884] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    24.884] (II) RADEON(0): First detailed timing is preferred mode
[    24.884] (II) RADEON(0): redX: 0.617 redY: 0.344   greenX: 0.327 greenY: 0.587
[    24.884] (II) RADEON(0): blueX: 0.160 blueY: 0.085   whiteX: 0.313 whiteY: 0.329
[    24.884] (II) RADEON(0): Manufacturer's mask: 0
[    24.884] (II) RADEON(0): Supported detailed timing:
[    24.884] (II) RADEON(0): clock: 75.4 MHz   Image Size:  309 x 174 mm
[    24.884] (II) RADEON(0): h_active: 1366  h_sync: 1397  h_sync_end 1462 h_blank_end 1560 h_border: 0
[    24.884] (II) RADEON(0): v_active: 768  v_sync: 772  v_sync_end 784 v_blanking: 806 v_border: 0
[    24.884] (II) RADEON(0):  N140B6-L02
[    24.884] (II) RADEON(0):  CMO
[    24.884] (II) RADEON(0):  N140B6-L02
[    24.884] (II) RADEON(0): EDID (in hex):
[    24.884] (II) RADEON(0): 	00ffffffffffff000daf441400000000
[    24.884] (II) RADEON(0): 	29120103801f11780a0d359e58539629
[    24.884] (II) RADEON(0): 	15505400000001010101010101010101
[    24.884] (II) RADEON(0): 	010101010101781d56c2500026301f41
[    24.884] (II) RADEON(0): 	4c0035ae10000018000000fe004e3134
[    24.884] (II) RADEON(0): 	3042362d4c30320a2020000000fe0043
[    24.884] (II) RADEON(0): 	4d4f0a202020202020202020000000fe
[    24.884] (II) RADEON(0): 	004e31343042362d4c30320a20200061
[    24.884] (II) RADEON(0): Printing probed modes for output LVDS
[    24.884] (II) RADEON(0): Modeline "1366x768"x60.0   75.44  1366 1397 1462 1560  768 772 784 806 -hsync -vsync (48.4 kHz eP)
[    24.884] (II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
[    24.884] (II) RADEON(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
[    24.884] (II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
[    24.884] (II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
[    24.884] (II) RADEON(0): Modeline "848x480"x59.7   31.50  848 872 952 1056  480 483 493 500 -hsync +vsync (29.8 kHz)
[    24.884] (II) RADEON(0): Modeline "720x480"x59.7   26.75  720 744 808 896  480 483 493 500 -hsync +vsync (29.9 kHz)
[    24.884] (II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
[    24.886] (II) RADEON(0): EDID for output HDMI-0
[    24.886] (II) RADEON(0): Output VGA-0 disconnected
[    24.886] (II) RADEON(0): Output LVDS connected
[    24.886] (II) RADEON(0): Output HDMI-0 disconnected
[    24.886] (II) RADEON(0): Using exact sizes for initial modes
[    24.887] (II) RADEON(0): Output LVDS using initial mode 1366x768
[    24.887] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    24.887] (II) RADEON(0): mem size init: gart size :1fdff000 vram size: s:10000000 visible:fba0000
[    24.887] (II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
[    24.887] (==) RADEON(0): DPI set to (96, 96)
[    24.887] (II) Loading sub module "fb"
[    24.887] (II) LoadModule: "fb"
[    24.887] (II) Loading /usr/lib/xorg/modules/libfb.so
[    24.888] (II) Module fb: vendor="X.Org Foundation"
[    24.888] 	compiled for 1.16.0, module version = 1.0.0
[    24.888] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    24.888] (II) Loading sub module "ramdac"
[    24.888] (II) LoadModule: "ramdac"
[    24.888] (II) Module "ramdac" already built-in
[    24.888] (II) UnloadModule: "modesetting"
[    24.888] (II) Unloading modesetting
[    24.888] (II) UnloadModule: "fbdev"
[    24.888] (II) Unloading fbdev
[    24.888] (II) UnloadSubModule: "fbdevhw"
[    24.888] (II) Unloading fbdevhw
[    24.888] (II) UnloadModule: "vesa"
[    24.888] (II) Unloading vesa
[    24.888] (--) Depth 24 pixmap format is 32 bpp
[    24.889] (II) RADEON(0): [DRI2] Setup complete
[    24.889] (II) RADEON(0): [DRI2]   DRI driver: r600
[    24.889] (II) RADEON(0): [DRI2]   VDPAU driver: r600
[    24.889] (II) RADEON(0): Front buffer size: 4128K
[    24.889] (II) RADEON(0): VRAM usage limit set to 228153K
[    24.890] (==) RADEON(0): Backing store enabled
[    24.890] (II) RADEON(0): Direct rendering enabled
[    24.890] (II) EXA(0): Driver allocated offscreen pixmaps
[    24.890] (II) EXA(0): Driver registered support for the following operations:
[    24.890] (II)         Solid
[    24.890] (II)         Copy
[    24.890] (II)         Composite (RENDER acceleration)
[    24.890] (II)         UploadToScreen
[    24.890] (II)         DownloadFromScreen
[    24.890] (II) RADEON(0): Acceleration enabled
[    24.890] (==) RADEON(0): DPMS enabled
[    24.890] (==) RADEON(0): Silken mouse enabled
[    24.891] (II) RADEON(0): Set up textured video
[    24.891] (II) RADEON(0): [XvMC] Associated with Radeon Textured Video.
[    24.891] (II) RADEON(0): [XvMC] Extension initialized.
[    24.891] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    24.891] (--) RandR disabled
[    25.714] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    25.714] (II) AIGLX: enabled GLX_ARB_create_context
[    25.714] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    25.714] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    25.714] (II) AIGLX: enabled GLX_INTEL_swap_event
[    25.714] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    25.714] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[    25.714] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[    25.714] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    25.715] (II) AIGLX: Loaded and initialized r600
[    25.715] (II) GLX: Initialized DRI2 GL provider for screen 0
[    25.788] (II) RADEON(0): Setting screen physical size to 361 x 203
[    25.884] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    25.894] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    25.895] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    25.895] (II) LoadModule: "evdev"
[    25.895] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.934] (II) Module evdev: vendor="X.Org Foundation"
[    25.935] 	compiled for 1.16.0, module version = 2.9.0
[    25.935] 	Module class: X.Org XInput Driver
[    25.935] 	ABI class: X.Org XInput driver, version 21.0
[    25.935] (II) Using input driver 'evdev' for 'Power Button'
[    25.935] (**) Power Button: always reports core events
[    25.935] (**) evdev: Power Button: Device: "/dev/input/event3"
[    25.935] (--) evdev: Power Button: Vendor 0 Product 0x1
[    25.935] (--) evdev: Power Button: Found keys
[    25.935] (II) evdev: Power Button: Configuring as keyboard
[    25.935] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    25.935] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    25.935] (**) Option "xkb_rules" "evdev"
[    25.935] (**) Option "xkb_model" "pc105"
[    25.935] (**) Option "xkb_layout" "us,th"
[    25.935] (**) Option "xkb_variant" ","
[    25.935] (**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
[    25.938] (II) XKB: reuse xkmfile /var/lib/xkb/server-43C7B9EC6478984F821D1424CA8186D46B547861.xkm
[    25.939] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    25.939] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    25.939] (II) Using input driver 'evdev' for 'Video Bus'
[    25.939] (**) Video Bus: always reports core events
[    25.939] (**) evdev: Video Bus: Device: "/dev/input/event5"
[    25.939] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    25.939] (--) evdev: Video Bus: Found keys
[    25.939] (II) evdev: Video Bus: Configuring as keyboard
[    25.939] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:42/LNXVIDEO:02/input/input6/event5"
[    25.939] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    25.939] (**) Option "xkb_rules" "evdev"
[    25.939] (**) Option "xkb_model" "pc105"
[    25.939] (**) Option "xkb_layout" "us,th"
[    25.939] (**) Option "xkb_variant" ","
[    25.939] (**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
[    25.940] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    25.940] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    25.940] (II) Using input driver 'evdev' for 'Power Button'
[    25.940] (**) Power Button: always reports core events
[    25.940] (**) evdev: Power Button: Device: "/dev/input/event0"
[    25.940] (--) evdev: Power Button: Vendor 0 Product 0x1
[    25.940] (--) evdev: Power Button: Found keys
[    25.940] (II) evdev: Power Button: Configuring as keyboard
[    25.940] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    25.940] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    25.940] (**) Option "xkb_rules" "evdev"
[    25.940] (**) Option "xkb_model" "pc105"
[    25.940] (**) Option "xkb_layout" "us,th"
[    25.940] (**) Option "xkb_variant" ","
[    25.940] (**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
[    25.940] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[    25.940] (II) No input driver specified, ignoring this device.
[    25.940] (II) This device may have been added with another device file.
[    25.941] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    25.941] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    25.941] (II) Using input driver 'evdev' for 'Sleep Button'
[    25.941] (**) Sleep Button: always reports core events
[    25.941] (**) evdev: Sleep Button: Device: "/dev/input/event2"
[    25.941] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    25.941] (--) evdev: Sleep Button: Found keys
[    25.941] (II) evdev: Sleep Button: Configuring as keyboard
[    25.941] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2/event2"
[    25.941] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[    25.941] (**) Option "xkb_rules" "evdev"
[    25.941] (**) Option "xkb_model" "pc105"
[    25.941] (**) Option "xkb_layout" "us,th"
[    25.941] (**) Option "xkb_variant" ","
[    25.941] (**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
[    25.942] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=3 (/dev/input/event8)
[    25.942] (II) No input driver specified, ignoring this device.
[    25.942] (II) This device may have been added with another device file.
[    25.942] (II) config/udev: Adding input device 1.3M WebCam (/dev/input/event13)
[    25.942] (**) 1.3M WebCam: Applying InputClass "evdev keyboard catchall"
[    25.942] (II) Using input driver 'evdev' for '1.3M WebCam'
[    25.942] (**) 1.3M WebCam: always reports core events
[    25.942] (**) evdev: 1.3M WebCam: Device: "/dev/input/event13"
[    25.942] (--) evdev: 1.3M WebCam: Vendor 0x4f2 Product 0xb1d8
[    25.942] (--) evdev: 1.3M WebCam: Found keys
[    25.942] (II) evdev: 1.3M WebCam: Configuring as keyboard
[    25.942] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.2/usb2/2-5/2-5:1.0/input/input14/event13"
[    25.942] (II) XINPUT: Adding extended input device "1.3M WebCam" (type: KEYBOARD, id 10)
[    25.942] (**) Option "xkb_rules" "evdev"
[    25.942] (**) Option "xkb_model" "pc105"
[    25.942] (**) Option "xkb_layout" "us,th"
[    25.942] (**) Option "xkb_variant" ","
[    25.942] (**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
[    25.943] (II) config/udev: Adding input device HDA ATI SB Mic (/dev/input/event9)
[    25.943] (II) No input driver specified, ignoring this device.
[    25.943] (II) This device may have been added with another device file.
[    25.943] (II) config/udev: Adding input device HDA ATI SB Headphone (/dev/input/event10)
[    25.943] (II) No input driver specified, ignoring this device.
[    25.943] (II) This device may have been added with another device file.
[    25.943] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    25.943] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    25.943] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    25.943] (**) AT Translated Set 2 keyboard: always reports core events
[    25.943] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    25.944] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    25.944] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    25.944] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    25.944] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    25.944] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 11)
[    25.944] (**) Option "xkb_rules" "evdev"
[    25.944] (**) Option "xkb_model" "pc105"
[    25.944] (**) Option "xkb_layout" "us,th"
[    25.944] (**) Option "xkb_variant" ","
[    25.944] (**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
[    25.944] (II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/event7)
[    25.944] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "evdev touchpad catchall"
[    25.944] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "touchpad catchall"
[    25.944] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "Default clickpad buttons"
[    25.944] (II) LoadModule: "synaptics"
[    25.945] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    25.945] (II) Module synaptics: vendor="X.Org Foundation"
[    25.945] 	compiled for 1.16.0, module version = 1.8.99
[    25.946] 	Module class: X.Org XInput Driver
[    25.946] 	ABI class: X.Org XInput driver, version 21.0
[    25.946] (II) Using input driver 'synaptics' for 'AlpsPS/2 ALPS GlidePoint'
[    25.946] (**) AlpsPS/2 ALPS GlidePoint: always reports core events
[    25.946] (**) Option "Device" "/dev/input/event7"
[    25.960] (II) synaptics: AlpsPS/2 ALPS GlidePoint: ignoring touch events for semi-multitouch device
[    25.960] (--) synaptics: AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 2000 (res 0)
[    25.960] (--) synaptics: AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 1400 (res 0)
[    25.960] (--) synaptics: AlpsPS/2 ALPS GlidePoint: pressure range 0 - 127
[    25.960] (II) synaptics: AlpsPS/2 ALPS GlidePoint: device does not report finger width.
[    25.960] (--) synaptics: AlpsPS/2 ALPS GlidePoint: buttons: left right middle double triple
[    25.960] (--) synaptics: AlpsPS/2 ALPS GlidePoint: Vendor 0x2 Product 0x8
[    25.960] (--) synaptics: AlpsPS/2 ALPS GlidePoint: invalid finger width range.  defaulting to 0 - 15
[    25.960] (--) synaptics: AlpsPS/2 ALPS GlidePoint: touchpad found
[    25.960] (**) AlpsPS/2 ALPS GlidePoint: always reports core events
[    25.972] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input7/event7"
[    25.972] (II) XINPUT: Adding extended input device "AlpsPS/2 ALPS GlidePoint" (type: TOUCHPAD, id 12)
[    25.972] (**) synaptics: AlpsPS/2 ALPS GlidePoint: (accel) MinSpeed is now constant deceleration 2.5
[    25.972] (**) synaptics: AlpsPS/2 ALPS GlidePoint: (accel) MaxSpeed is now 1.75
[    25.972] (**) synaptics: AlpsPS/2 ALPS GlidePoint: (accel) AccelFactor is now 0.082
[    25.972] (**) AlpsPS/2 ALPS GlidePoint: (accel) keeping acceleration scheme 1
[    25.972] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration profile 1
[    25.972] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration factor: 2.000
[    25.972] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration threshold: 4
[    25.972] (--) synaptics: AlpsPS/2 ALPS GlidePoint: touchpad found
[    25.973] (II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/mouse1)
[    25.973] (**) AlpsPS/2 ALPS GlidePoint: Ignoring device from InputClass "touchpad ignore duplicates"
[    25.973] (II) config/udev: Adding input device ALPS PS/2 Device (/dev/input/event6)
[    25.973] (**) ALPS PS/2 Device: Applying InputClass "evdev pointer catchall"
[    25.973] (II) Using input driver 'evdev' for 'ALPS PS/2 Device'
[    25.973] (**) ALPS PS/2 Device: always reports core events
[    25.973] (**) evdev: ALPS PS/2 Device: Device: "/dev/input/event6"
[    25.973] (--) evdev: ALPS PS/2 Device: Vendor 0x2 Product 0x8
[    25.973] (--) evdev: ALPS PS/2 Device: Found 3 mouse buttons
[    25.973] (--) evdev: ALPS PS/2 Device: Found relative axes
[    25.973] (--) evdev: ALPS PS/2 Device: Found x and y relative axes
[    25.973] (II) evdev: ALPS PS/2 Device: Configuring as mouse
[    25.973] (**) evdev: ALPS PS/2 Device: YAxisMapping: buttons 4 and 5
[    25.973] (**) evdev: ALPS PS/2 Device: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    25.973] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input8/event6"
[    25.973] (II) XINPUT: Adding extended input device "ALPS PS/2 Device" (type: MOUSE, id 13)
[    25.973] (II) evdev: ALPS PS/2 Device: initialized for relative axes.
[    25.973] (**) ALPS PS/2 Device: (accel) keeping acceleration scheme 1
[    25.973] (**) ALPS PS/2 Device: (accel) acceleration profile 0
[    25.973] (**) ALPS PS/2 Device: (accel) acceleration factor: 2.000
[    25.973] (**) ALPS PS/2 Device: (accel) acceleration threshold: 4
[    25.974] (II) config/udev: Adding input device ALPS PS/2 Device (/dev/input/mouse0)
[    25.974] (II) No input driver specified, ignoring this device.
[    25.974] (II) This device may have been added with another device file.
[    25.975] (II) config/udev: Adding input device Acer WMI hotkeys (/dev/input/event11)
[    25.975] (**) Acer WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    25.975] (II) Using input driver 'evdev' for 'Acer WMI hotkeys'
[    25.976] (**) Acer WMI hotkeys: always reports core events
[    25.976] (**) evdev: Acer WMI hotkeys: Device: "/dev/input/event11"
[    25.976] (--) evdev: Acer WMI hotkeys: Vendor 0 Product 0
[    25.976] (--) evdev: Acer WMI hotkeys: Found keys
[    25.976] (II) evdev: Acer WMI hotkeys: Configuring as keyboard
[    25.976] (**) Option "config_info" "udev:/sys/devices/virtual/input/input12/event11"
[    25.976] (II) XINPUT: Adding extended input device "Acer WMI hotkeys" (type: KEYBOARD, id 14)
[    25.976] (**) Option "xkb_rules" "evdev"
[    25.976] (**) Option "xkb_model" "pc105"
[    25.976] (**) Option "xkb_layout" "us,th"
[    25.976] (**) Option "xkb_variant" ","
[    25.976] (**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
[    25.976] (II) config/udev: Adding input device Acer BMA150 accelerometer (/dev/input/event12)
[    25.976] (II) No input driver specified, ignoring this device.
[    25.976] (II) This device may have been added with another device file.
[    25.976] (II) config/udev: Adding input device Acer BMA150 accelerometer (/dev/input/js0)
[    25.976] (II) No input driver specified, ignoring this device.
[    25.976] (II) This device may have been added with another device file.
[    36.272] (II) RADEON(0): EDID vendor "CMO", prod id 5188
[    36.272] (II) RADEON(0): Printing DDC gathered Modelines:
[    36.272] (II) RADEON(0): Modeline "1366x768"x0.0   75.44  1366 1397 1462 1560  768 772 784 806 -hsync -vsync (48.4 kHz eP)
[    36.456] (II) RADEON(0): EDID vendor "CMO", prod id 5188
[    36.456] (II) RADEON(0): Printing DDC gathered Modelines:
[    36.456] (II) RADEON(0): Modeline "1366x768"x0.0   75.44  1366 1397 1462 1560  768 772 784 806 -hsync -vsync (48.4 kHz eP)
[    38.178] (II) XKB: reuse xkmfile /var/lib/xkb/server-C91555A6B203C7B55C59872C3D6391EF451B0B49.xkm
[    40.812] (II) RADEON(0): EDID vendor "CMO", prod id 5188
[    40.812] (II) RADEON(0): Printing DDC gathered Modelines:
[    40.812] (II) RADEON(0): Modeline "1366x768"x0.0   75.44  1366 1397 1462 1560  768 772 784 806 -hsync -vsync (48.4 kHz eP)
[    40.852] (II) RADEON(0): EDID vendor "CMO", prod id 5188
[    40.852] (II) RADEON(0): Printing DDC gathered Modelines:
[    40.852] (II) RADEON(0): Modeline "1366x768"x0.0   75.44  1366 1397 1462 1560  768 772 784 806 -hsync -vsync (48.4 kHz eP)
[    43.704] (II) RADEON(0): EDID vendor "CMO", prod id 5188
[    43.704] (II) RADEON(0): Printing DDC gathered Modelines:
[    43.704] (II) RADEON(0): Modeline "1366x768"x0.0   75.44  1366 1397 1462 1560  768 772 784 806 -hsync -vsync (48.4 kHz eP)
[  2535.199] (II) XKB: generating xkmfile /var/lib/xkb/server-42AA8AE636C8E172C007234EDFDD155A8C57DA73.xkm

```

---

