---
title: "OpenGL Issues - Radeon HD 7500"
date: 2012-04-12
forum: Hardware
---

### Post by TkTkUK on 2012-04-12
Hey everyone.

I'm very new to Ubuntu, and linux. I am trying to set up a OpenGL development environment, but before compiling, when entering "glxinfo", came across an issue on this old laptop of mine,

```
name of display: :0
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  14
  Current serial number in output stream:  14

```

So, it doesn't let me compile and even after attempting to install drivers, it isn't doing anything! 

I'm on Ubuntu 11.10, ThinkPad T41 with a 7500 Radeon HD (Supported for 3D graphics fo'sho).

Here is the contents of my Xorg.0.log,

```
[    24.446] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[    24.446] X Protocol Version 11, Revision 0
[    24.446] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[    24.446] Current Operating System: Linux ibm-ThinkPad-T41 3.0.0-17-generic #30-Ubuntu SMP Thu Mar 8 17:34:21 UTC 2012 i686
[    24.446] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-17-generic root=UUID=cd193b95-ac2c-4c20-84fb-d6d9125cd860 ro quiet splash vt.handoff=7
[    24.446] Build Date: 19 October 2011  05:09:41AM
[    24.446] xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see http://www.ubuntu.com/support) 
[    24.446] Current version of pixman: 0.22.2
[    24.446] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    24.446] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    24.446] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Apr 12 18:12:28 2012
[    24.446] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    24.454] (==) No Layout section.  Using the first Screen section.
[    24.454] (==) No screen section available. Using defaults.
[    24.454] (**) |-->Screen "Default Screen Section" (0)
[    24.454] (**) |   |-->Monitor "<default monitor>"
[    24.454] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    24.454] (==) Automatically adding devices
[    24.454] (==) Automatically enabling devices
[    24.455] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    24.455] 	Entry deleted from font path.
[    24.455] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    24.455] 	Entry deleted from font path.
[    24.455] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    24.455] 	Entry deleted from font path.
[    24.455] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    24.455] 	Entry deleted from font path.
[    24.455] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    24.455] 	Entry deleted from font path.
[    24.455] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    24.455] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    24.455] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    24.455] (II) Loader magic: 0x823ada0
[    24.455] (II) Module ABI versions:
[    24.455] 	X.Org ANSI C Emulation: 0.4
[    24.455] 	X.Org Video Driver: 10.0
[    24.455] 	X.Org XInput driver : 12.3
[    24.455] 	X.Org Server Extension : 5.0
[    24.456] (--) PCI:*(0:1:0:0) 1002:4c57:1014:0530 rev 0, Mem @ 0xe0000000/134217728, 0xc0100000/65536, I/O @ 0x00003000/256, BIOS @ 0x????????/131072
[    24.456] (II) Open ACPI successful (/var/run/acpid.socket)
[    24.456] (II) LoadModule: "extmod"
[    24.519] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    24.525] (II) Module extmod: vendor="X.Org Foundation"
[    24.525] 	compiled for 1.10.4, module version = 1.0.0
[    24.525] 	Module class: X.Org Server Extension
[    24.525] 	ABI class: X.Org Server Extension, version 5.0
[    24.525] (II) Loading extension MIT-SCREEN-SAVER
[    24.525] (II) Loading extension XFree86-VidModeExtension
[    24.525] (II) Loading extension XFree86-DGA
[    24.525] (II) Loading extension DPMS
[    24.525] (II) Loading extension XVideo
[    24.525] (II) Loading extension XVideo-MotionCompensation
[    24.525] (II) Loading extension X-Resource
[    24.525] (II) LoadModule: "dbe"
[    24.526] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    24.526] (II) Module dbe: vendor="X.Org Foundation"
[    24.526] 	compiled for 1.10.4, module version = 1.0.0
[    24.526] 	Module class: X.Org Server Extension
[    24.526] 	ABI class: X.Org Server Extension, version 5.0
[    24.526] (II) Loading extension DOUBLE-BUFFER
[    24.526] (II) LoadModule: "glx"
[    24.526] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/modules/extensions/libglx.so
[    24.526] (II) Module glx: vendor="FireGL - AMD Technologies Inc."
[    24.526] 	compiled for 6.9.0, module version = 1.0.0
[    24.527] (II) Loading extension GLX
[    24.527] (II) LoadModule: "record"
[    24.527] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    24.528] (II) Module record: vendor="X.Org Foundation"
[    24.528] 	compiled for 1.10.4, module version = 1.13.0
[    24.528] 	Module class: X.Org Server Extension
[    24.528] 	ABI class: X.Org Server Extension, version 5.0
[    24.528] (II) Loading extension RECORD
[    24.528] (II) LoadModule: "dri"
[    24.528] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    24.528] (II) Module dri: vendor="X.Org Foundation"
[    24.528] 	compiled for 1.10.4, module version = 1.0.0
[    24.528] 	ABI class: X.Org Server Extension, version 5.0
[    24.528] (II) Loading extension XFree86-DRI
[    24.528] (II) LoadModule: "dri2"
[    24.529] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    24.529] (II) Module dri2: vendor="X.Org Foundation"
[    24.529] 	compiled for 1.10.4, module version = 1.2.0
[    24.529] 	ABI class: X.Org Server Extension, version 5.0
[    24.529] (II) Loading extension DRI2
[    24.529] (==) Matched fglrx as autoconfigured driver 0
[    24.529] (==) Matched ati as autoconfigured driver 1
[    24.529] (==) Matched vesa as autoconfigured driver 2
[    24.529] (==) Matched fbdev as autoconfigured driver 3
[    24.529] (==) Assigned the driver to the xf86ConfigLayout
[    24.529] (II) LoadModule: "fglrx"
[    24.529] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so
[    24.560] (II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
[    24.560] 	compiled for 1.4.99.906, module version = 8.88.7
[    24.560] 	Module class: X.Org Video Driver
[    24.561] (II) Loading sub module "fglrxdrm"
[    24.561] (II) LoadModule: "fglrxdrm"
[    24.561] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    24.561] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[    24.561] 	compiled for 1.4.99.906, module version = 8.88.7
[    24.561] (II) LoadModule: "ati"
[    24.562] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    24.562] (II) Module ati: vendor="X.Org Foundation"
[    24.562] 	compiled for 1.10.2.902, module version = 6.14.99
[    24.562] 	Module class: X.Org Video Driver
[    24.562] 	ABI class: X.Org Video Driver, version 10.0
[    24.562] (II) LoadModule: "radeon"
[    24.562] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    24.563] (II) Module radeon: vendor="X.Org Foundation"
[    24.563] 	compiled for 1.10.2.902, module version = 6.14.99
[    24.563] 	Module class: X.Org Video Driver
[    24.563] 	ABI class: X.Org Video Driver, version 10.0
[    24.563] (II) LoadModule: "vesa"
[    24.563] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    24.563] (II) Module vesa: vendor="X.Org Foundation"
[    24.563] 	compiled for 1.10.2, module version = 2.3.0
[    24.563] 	Module class: X.Org Video Driver
[    24.563] 	ABI class: X.Org Video Driver, version 10.0
[    24.563] (II) LoadModule: "fbdev"
[    24.564] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    24.564] (II) Module fbdev: vendor="X.Org Foundation"
[    24.564] 	compiled for 1.10.0, module version = 0.4.2
[    24.564] 	ABI class: X.Org Video Driver, version 10.0
[    24.564] (II) ATI Proprietary Linux Driver Version Identifier:8.88.7
[    24.564] (II) ATI Proprietary Linux Driver Release Identifier: 8.881                                
[    24.564] (II) ATI Proprietary Linux Driver Build Date: Jul 28 2011 17:03:52
[    24.564] (II) RADEON: Driver for ATI Radeon chipsets:
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
	ATI Radeon 3000 Graphics, SUMO, SUMO, SUMO2, SUMO2, SUMO2, SUMO2,
	SUMO, SUMO, SUMO, SUMO, SUMO, ATI Radeon HD 4200, ATI Radeon 4100,
	ATI Mobility Radeon HD 4200, ATI Mobility Radeon 4100,
	ATI Radeon HD 4290, ATI Radeon HD 4250, AMD Radeon HD 6310 Graphics,
	AMD Radeon HD 6310 Graphics, AMD Radeon HD 6250 Graphics,
	AMD Radeon HD 6250 Graphics, AMD Radeon HD 6300 Series Graphics,
	AMD Radeon HD 6200 Series Graphics, CYPRESS,
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
	ATI Radeon HD 5450, CEDAR, CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
	CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN, AMD Radeon HD 6900 Series,
	AMD Radeon HD 6900 Series, CAYMAN, CAYMAN, CAYMAN,
	AMD Radeon HD 6900M Series, Mobility Radeon HD 6000 Series, BARTS,
	BARTS, Mobility Radeon HD 6000 Series,
	Mobility Radeon HD 6000 Series, BARTS, BARTS, BARTS, BARTS,
	AMD Radeon HD 6800 Series, AMD Radeon HD 6800 Series,
	AMD Radeon HD 6700 Series, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
	TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, CAICOS,
	CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
	CAICOS, CAICOS, CAICOS
[    24.568] (II) VESA: driver for VESA chipsets: vesa
[    24.568] (II) FBDEV: driver for framebuffer: fbdev
[    24.568] (++) using VT number 7

[    24.568] (WW) Falling back to old probe method for fglrx
[    24.582] (II) PCS database file /etc/ati/amdpcsdb not found
[    24.582] (II)   Creating PCS database from initial defaults instead
[    24.582] (EE) No supported AMD display adapters were found
[    24.582] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    24.582] (II) [KMS] drm report modesetting isn't supported.
[    24.582] (WW) Falling back to old probe method for vesa
[    24.582] (WW) Falling back to old probe method for fbdev
[    24.582] (II) Loading sub module "fbdevhw"
[    24.582] (II) LoadModule: "fbdevhw"
[    24.583] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    24.583] (II) Module fbdevhw: vendor="X.Org Foundation"
[    24.583] 	compiled for 1.10.4, module version = 0.0.2
[    24.583] 	ABI class: X.Org Video Driver, version 10.0
[    24.583] (II) RADEON(0): TOTO SAYS 00000000c0100000
[    24.583] (II) RADEON(0): MMIO registers at 0x00000000c0100000: size 64KB
[    24.583] (II) RADEON(0): PCI bus 1 card 0 func 0
[    24.583] (II) RADEON(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    24.583] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    24.583] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    24.583] (==) RADEON(0): Default visual is TrueColor
[    24.583] (II) Loading sub module "vgahw"
[    24.583] (II) LoadModule: "vgahw"
[    24.584] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    24.584] (II) Module vgahw: vendor="X.Org Foundation"
[    24.584] 	compiled for 1.10.4, module version = 0.1.0
[    24.584] 	ABI class: X.Org Video Driver, version 10.0
[    24.584] (II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
[    24.584] (==) RADEON(0): RGB weight 888
[    24.584] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    24.584] (--) RADEON(0): Chipset: "ATI Radeon Mobility M7 LW (AGP)" (ChipID = 0x4c57)
[    24.584] (--) RADEON(0): Linear framebuffer at 0x00000000e0000000
[    24.584] (II) RADEON(0): AGP card detected
[    24.584] (II) Loading sub module "int10"
[    24.584] (II) LoadModule: "int10"
[    24.585] (II) Loading /usr/lib/xorg/modules/libint10.so
[    24.585] (II) Module int10: vendor="X.Org Foundation"
[    24.585] 	compiled for 1.10.4, module version = 1.0.0
[    24.585] 	ABI class: X.Org Video Driver, version 10.0
[    24.585] (II) RADEON(0): initializing int10
[    24.586] (II) RADEON(0): Primary V_BIOS segment is: 0xc000
[    24.587] (II) RADEON(0): Legacy BIOS detected
[    24.587] drmOpenDevice: node name is /dev/dri/card0
[    24.595] [drm] failed to load kernel module "radeon"
[    24.595] (EE) RADEON(0): [dri] RADEONDRIGetVersion failed to open the DRM
[dri] Disabling DRI.
[    24.595] (II) RADEON(0): Detected total video RAM=32768K, accessible=65536K (PCI BAR=131072K)
[    24.595] (--) RADEON(0): Mapped VideoRAM: 32768 kByte (64 bit DDR SDRAM)
[    24.595] (II) RADEON(0): Color tiling enabled by default
[    24.595] (II) Loading sub module "ddc"
[    24.595] (II) LoadModule: "ddc"
[    24.595] (II) Module "ddc" already built-in
[    24.595] (II) Loading sub module "i2c"
[    24.595] (II) LoadModule: "i2c"
[    24.595] (II) Module "i2c" already built-in
[    24.595] (II) RADEON(0): ref_freq: 2700, min_out_pll: 12000, max_out_pll: 35000, min_in_pll: 40, max_in_pll: 3000, xclk: 18300, sclk: 260.000000, mclk: 183.000000
[    24.595] (II) RADEON(0): PLL parameters: rf=2700 rd=12 min=12000 max=35000; xclk=18300
[    24.595] (II) RADEON(0): DFP table revision: 2
[    24.595] (II) RADEON(0): Panel ID string: 1024x768                
[    24.595] (II) RADEON(0): Panel Size from BIOS: 1024x768
[    24.595] (II) RADEON(0): BIOS provided dividers will be used.
[    24.595] (WW) RADEON(0): LVDS Info:
XRes: 1024, YRes: 768, DotClock: 65000
HBlank: 320, HOverPlus: 16, HSyncWidth: 136
VBlank: 38, VOverPlus: 2, VSyncWidth: 6
[    24.595] (II) RADEON(0): Output VGA-0 has no monitor section
[    24.595] (II) RADEON(0): I2C bus "VGA-0" initialized.
[    24.595] (II) RADEON(0): Output DVI-0 has no monitor section
[    24.595] (II) RADEON(0): I2C bus "DVI-0" initialized.
[    24.595] (II) RADEON(0): Output LVDS has no monitor section
[    24.595] (II) RADEON(0): Output S-video has no monitor section
[    24.595] (II) RADEON(0): Default TV standard: NTSC
[    24.595] (II) RADEON(0): TV standards supported by chip: NTSC PAL NTSC-J 
[    24.595] (II) RADEON(0): Port0:
[    24.595]   XRANDR name: VGA-0
[    24.595]   Connector: VGA
[    24.595]   CRT1: INTERNAL_DAC1
[    24.595]   DDC reg: 0x60
[    24.595] (II) RADEON(0): Port1:
[    24.595]   XRANDR name: DVI-0
[    24.595]   Connector: DVI-D
[    24.595]   DFP1: INTERNAL_TMDS1
[    24.595]   DDC reg: 0x64
[    24.595] (II) RADEON(0): Port2:
[    24.595]   XRANDR name: LVDS
[    24.595]   Connector: LVDS
[    24.595]   LCD1: INTERNAL_LVDS
[    24.595]   DDC reg: 0x0
[    24.595] (II) RADEON(0): Port3:
[    24.595]   XRANDR name: S-video
[    24.595]   Connector: S-video
[    24.595]   TV1: INTERNAL_DAC2
[    24.595]   DDC reg: 0x0
[    24.595] (II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
[    24.602] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[    24.602] finished output detect: 0
[    24.602] (II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
[    24.606] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
[    24.606] finished output detect: 1
[    24.606] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[    24.606] finished output detect: 2
[    24.606] (II) RADEON(0): Output: S-video, Detected Monitor Type: 0
[    24.606] finished output detect: 3
[    24.606] finished all detect
[    24.612] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[    24.612] (II) RADEON(0): EDID for output VGA-0
[    24.616] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
[    24.616] (II) RADEON(0): EDID for output DVI-0
[    24.616] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[    24.616] (II) RADEON(0): Added native panel mode: 1024x768
[    24.616] (II) RADEON(0): Printing probed modes for output LVDS
[    24.616] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1040 1176 1344  768 770 776 806 (48.4 kHz)
[    24.616] (II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
[    24.616] (II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
[    24.616] (II) RADEON(0): Output: S-video, Detected Monitor Type: 0
[    24.616] (II) RADEON(0): EDID for output S-video
[    24.616] (II) RADEON(0): Output VGA-0 disconnected
[    24.616] (II) RADEON(0): Output DVI-0 disconnected
[    24.616] (II) RADEON(0): Output LVDS connected
[    24.616] (II) RADEON(0): Output S-video disconnected
[    24.616] (II) RADEON(0): Using exact sizes for initial modes
[    24.616] (II) RADEON(0): Output LVDS using initial mode 1024x768
[    24.616] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    24.616] (==) RADEON(0): DPI set to (96, 96)
[    24.616] (II) Loading sub module "fb"
[    24.616] (II) LoadModule: "fb"
[    24.617] (II) Loading /usr/lib/xorg/modules/libfb.so
[    24.617] (II) Module fb: vendor="X.Org Foundation"
[    24.617] 	compiled for 1.10.4, module version = 1.0.0
[    24.617] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    24.617] (II) Loading sub module "ramdac"
[    24.617] (II) LoadModule: "ramdac"
[    24.617] (II) Module "ramdac" already built-in
[    24.617] (==) RADEON(0): Using XAA acceleration architecture
[    24.617] (II) Loading sub module "xaa"
[    24.617] (II) LoadModule: "xaa"
[    24.618] (II) Loading /usr/lib/xorg/modules/libxaa.so
[    24.618] (II) Module xaa: vendor="X.Org Foundation"
[    24.618] 	compiled for 1.10.4, module version = 1.2.1
[    24.618] 	ABI class: X.Org Video Driver, version 10.0
[    24.618] (==) RADEON(0): Assuming overlay scaler buffer width is 1536
[    24.618] (II) RADEON(0): No MM_TABLE found - assuming CARD is not TV-in capable.
[    24.618] (!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
[    24.618] (II) UnloadModule: "fglrx"
[    24.618] (II) Unloading fglrx
[    24.618] (II) UnloadModule: "fglrxdrm"
[    24.618] (II) Unloading fglrxdrm
[    24.618] (II) UnloadModule: "vesa"
[    24.618] (II) Unloading vesa
[    24.618] (II) UnloadModule: "fbdev"
[    24.618] (II) Unloading fbdev
[    24.618] (II) UnloadModule: "fbdevhw"
[    24.618] (II) Unloading fbdevhw
[    24.618] (--) Depth 24 pixmap format is 32 bpp
[    24.618] (II) RADEON(0): RADEONScreenInit e0000000 0 0
[    24.624] Entering TV Save
[    24.624] Save TV timing tables
[    24.624] saveTimingTables: reading timing tables
[    24.624] TV Save done
[    25.624] (II) RADEON(0): Dynamic Power Management Disabled
[    25.624] (II) RADEON(0): RADEONInitMemoryMap() : 
[    25.624] (II) RADEON(0):   mem_size         : 0x04000000
[    25.624] (II) RADEON(0):   MC_FB_LOCATION   : 0xe3ffe000
[    25.624] (II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
[    25.624] (II) RADEON(0): Depth moves disabled by default
[    25.624] (II) RADEON(0): Memory manager initialized to (0,0) (1024,8191)
[    25.624] (II) RADEON(0): Reserved area from (0,1024) to (1024,1026)
[    25.624] (II) RADEON(0): Largest offscreen area available: 1024 x 7165
[    25.624] (II) RADEON(0): RADEONRestoreMemMapRegisters() : 
[    25.624] (II) RADEON(0):   MC_FB_LOCATION   : 0xe3ffe000 0x1fff0000
[    25.624] (II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
[    25.825] (==) RADEON(0): Backing store disabled
[    25.825] (WW) RADEON(0): Direct rendering disabled
[    25.825] (II) RADEON(0): Render acceleration disabled
[    25.825] (II) RADEON(0): Using XFree86 Acceleration Architecture (XAA)
[    25.825] 	Screen to screen bit blits
[    25.825] 	Solid filled rectangles
[    25.825] 	8x8 mono pattern filled rectangles
[    25.825] 	Indirect CPU to Screen color expansion
[    25.825] 	Solid Lines
[    25.825] 	Scanline Image Writes
[    25.825] 	Setting up tile and stipple cache:
[    25.825] 		32 128x128 slots
[    25.825] 		32 256x256 slots
[    25.825] 		16 512x512 slots
[    25.825] (II) RADEON(0): Acceleration enabled
[    25.825] (==) RADEON(0): DPMS enabled
[    25.825] (==) RADEON(0): Silken mouse enabled
[    25.825] (II) RADEON(0): Will use 32 kb for hardware cursor 0 at offset 0x00402000
[    25.825] (II) RADEON(0): Will use 32 kb for hardware cursor 1 at offset 0x00406000
[    25.825] (II) RADEON(0): Largest offscreen area available: 1024 x 7157
[    25.825] (II) RADEON(0): Detected Radeon Mobility M7, disabling multimedia i2c
[    25.825] (II) Loading sub module "theatre_detect"
[    25.825] (II) LoadModule: "theatre_detect"
[    25.826] (II) Loading /usr/lib/xorg/modules/multimedia/theatre_detect_drv.so
[    25.826] (II) Module theatre_detect: vendor="X.Org Foundation"
[    25.826] 	compiled for 1.10.2.902, module version = 1.0.0
[    25.826] 	ABI class: X.Org Video Driver, version 10.0
[    25.826] (II) RADEON(0): no multimedia table present, disabling Rage Theatre.
[    25.826] (II) RADEON(0): Set up overlay video
[    25.826] (II) RADEON(0): Set up textured video
[    25.826] (II) RADEON(0): [XvMC] Associated with Radeon Textured Video.
[    25.826] (II) RADEON(0): [XvMC] Extension initialized.
[    25.851] disable primary dac
[    25.852] disable FP1
[    26.852] disable TV
[    27.852] init memmap
[    27.852] init common
[    27.852] init crtc1
[    27.852] init pll1
[    27.852] restore memmap
[    27.852] (II) RADEON(0): RADEONRestoreMemMapRegisters() : 
[    27.852] (II) RADEON(0):   MC_FB_LOCATION   : 0xe3ffe000 0xe3ffe000
[    27.852] (II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
[    27.952] restore common
[    28.053] restore crtc1
[    28.053] restore pll1
[    28.053] set RMX
[    28.053] set LVDS
[    28.053] enable LVDS
[    29.053] disable primary dac
[    29.053] disable FP1
[    29.053] disable TV
[    29.053] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    29.053] (--) RandR disabled
[    29.053] (II) Initializing built-in extension Generic Event Extension
[    29.053] (II) Initializing built-in extension SHAPE
[    29.053] (II) Initializing built-in extension MIT-SHM
[    29.053] (II) Initializing built-in extension XInputExtension
[    29.053] (II) Initializing built-in extension XTEST
[    29.053] (II) Initializing built-in extension BIG-REQUESTS
[    29.053] (II) Initializing built-in extension SYNC
[    29.053] (II) Initializing built-in extension XKEYBOARD
[    29.053] (II) Initializing built-in extension XC-MISC
[    29.053] (II) Initializing built-in extension SECURITY
[    29.053] (II) Initializing built-in extension XINERAMA
[    29.053] (II) Initializing built-in extension XFIXES
[    29.053] (II) Initializing built-in extension RENDER
[    29.053] (II) Initializing built-in extension RANDR
[    29.053] (II) Initializing built-in extension COMPOSITE
[    29.053] (II) Initializing built-in extension DAMAGE
[    29.053] (II) Initializing built-in extension GESTURE
[    29.059] (EE) GLX error: Can not get required symbols.
[    29.072] (II) RADEON(0): Setting screen physical size to 270 x 203
[    29.128] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    29.141] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    29.141] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    29.141] (II) LoadModule: "evdev"
[    29.141] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.143] (II) Module evdev: vendor="X.Org Foundation"
[    29.143] 	compiled for 1.10.2, module version = 2.6.0
[    29.143] 	Module class: X.Org XInput Driver
[    29.143] 	ABI class: X.Org XInput driver, version 12.3
[    29.143] (II) Using input driver 'evdev' for 'Power Button'
[    29.143] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.143] (**) Power Button: always reports core events
[    29.143] (**) Power Button: Device: "/dev/input/event2"
[    29.143] (--) Power Button: Found keys
[    29.143] (II) Power Button: Configuring as keyboard
[    29.143] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    29.143] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    29.143] (**) Option "xkb_rules" "evdev"
[    29.143] (**) Option "xkb_model" "pc105"
[    29.143] (**) Option "xkb_layout" "gb"
[    29.148] (II) XKB: reuse xkmfile /var/lib/xkb/server-2B4266AA55228AE7D9557A18F1965DBA19850816.xkm
[    29.154] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[    29.154] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    29.154] (II) Using input driver 'evdev' for 'Video Bus'
[    29.154] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.154] (**) Video Bus: always reports core events
[    29.154] (**) Video Bus: Device: "/dev/input/event4"
[    29.154] (--) Video Bus: Found keys
[    29.154] (II) Video Bus: Configuring as keyboard
[    29.154] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:03/LNXVIDEO:00/input/input4/event4"
[    29.154] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    29.154] (**) Option "xkb_rules" "evdev"
[    29.154] (**) Option "xkb_model" "pc105"
[    29.154] (**) Option "xkb_layout" "gb"
[    29.156] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    29.156] (II) No input driver/identifier specified (ignoring)
[    29.156] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    29.157] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    29.157] (II) Using input driver 'evdev' for 'Sleep Button'
[    29.157] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.157] (**) Sleep Button: always reports core events
[    29.157] (**) Sleep Button: Device: "/dev/input/event1"
[    29.157] (--) Sleep Button: Found keys
[    29.157] (II) Sleep Button: Configuring as keyboard
[    29.157] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1/event1"
[    29.157] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    29.157] (**) Option "xkb_rules" "evdev"
[    29.157] (**) Option "xkb_model" "pc105"
[    29.157] (**) Option "xkb_layout" "gb"
[    29.165] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    29.165] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    29.165] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    29.165] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.165] (**) AT Translated Set 2 keyboard: always reports core events
[    29.165] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    29.165] (--) AT Translated Set 2 keyboard: Found keys
[    29.165] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    29.165] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    29.165] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    29.165] (**) Option "xkb_rules" "evdev"
[    29.165] (**) Option "xkb_model" "pc105"
[    29.165] (**) Option "xkb_layout" "gb"
[    29.166] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event5)
[    29.166] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    29.166] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    29.166] (II) LoadModule: "synaptics"
[    29.167] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    29.167] (II) Module synaptics: vendor="X.Org Foundation"
[    29.167] 	compiled for 1.10.4, module version = 1.4.1
[    29.167] 	Module class: X.Org XInput Driver
[    29.167] 	ABI class: X.Org XInput driver, version 12.3
[    29.167] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    29.167] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    29.167] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    29.167] (**) Option "Device" "/dev/input/event5"
[    29.167] (--) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[    29.167] (--) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[    29.167] (--) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    29.167] (--) SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    29.167] (--) SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    29.167] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    29.167] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    29.168] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input5/event5"
[    29.168] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    29.168] (**) SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    29.168] (**) SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[    29.168] (**) SynPS/2 Synaptics TouchPad: AccelFactor is now 0.040
[    29.168] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    29.168] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    29.168] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    29.168] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    29.168] (II) SynPS/2 Synaptics TouchPad: failed to open grail, no gesture support
[    29.168] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    29.168] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    29.168] (II) No input driver/identifier specified (ignoring)
[    29.169] (II) config/udev: Adding input device TPPS/2 IBM TrackPoint (/dev/input/event7)
[    29.169] (**) TPPS/2 IBM TrackPoint: Applying InputClass "evdev pointer catchall"
[    29.169] (**) TPPS/2 IBM TrackPoint: Applying InputClass "trackpoint catchall"
[    29.169] (II) Using input driver 'evdev' for 'TPPS/2 IBM TrackPoint'
[    29.169] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.169] (**) TPPS/2 IBM TrackPoint: always reports core events
[    29.169] (**) TPPS/2 IBM TrackPoint: Device: "/dev/input/event7"
[    29.169] (--) TPPS/2 IBM TrackPoint: Found 3 mouse buttons
[    29.169] (--) TPPS/2 IBM TrackPoint: Found relative axes
[    29.169] (--) TPPS/2 IBM TrackPoint: Found x and y relative axes
[    29.169] (II) TPPS/2 IBM TrackPoint: Configuring as mouse
[    29.169] (**) Option "Emulate3Buttons" "true"
[    29.169] (**) Option "EmulateWheel" "true"
[    29.169] (**) Option "EmulateWheelButton" "2"
[    29.169] (**) Option "YAxisMapping" "4 5"
[    29.169] (**) TPPS/2 IBM TrackPoint: YAxisMapping: buttons 4 and 5
[    29.169] (**) Option "XAxisMapping" "6 7"
[    29.169] (**) TPPS/2 IBM TrackPoint: XAxisMapping: buttons 6 and 7
[    29.169] (**) TPPS/2 IBM TrackPoint: EmulateWheelButton: 2, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    29.169] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/serio2/input/input7/event7"
[    29.169] (II) XINPUT: Adding extended input device "TPPS/2 IBM TrackPoint" (type: MOUSE)
[    29.169] (II) TPPS/2 IBM TrackPoint: initialized for relative axes.
[    29.170] (**) TPPS/2 IBM TrackPoint: (accel) keeping acceleration scheme 1
[    29.170] (**) TPPS/2 IBM TrackPoint: (accel) acceleration profile 0
[    29.170] (**) TPPS/2 IBM TrackPoint: (accel) acceleration factor: 2.000
[    29.170] (**) TPPS/2 IBM TrackPoint: (accel) acceleration threshold: 4
[    29.170] (II) config/udev: Adding input device TPPS/2 IBM TrackPoint (/dev/input/mouse1)
[    29.170] (II) No input driver/identifier specified (ignoring)
[    29.173] (II) config/udev: Adding input device ThinkPad Extra Buttons (/dev/input/event6)
[    29.173] (**) ThinkPad Extra Buttons: Applying InputClass "evdev keyboard catchall"
[    29.173] (II) Using input driver 'evdev' for 'ThinkPad Extra Buttons'
[    29.173] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.173] (**) ThinkPad Extra Buttons: always reports core events
[    29.173] (**) ThinkPad Extra Buttons: Device: "/dev/input/event6"
[    29.173] (--) ThinkPad Extra Buttons: Found keys
[    29.173] (II) ThinkPad Extra Buttons: Configuring as keyboard
[    29.173] (**) Option "config_info" "udev:/sys/devices/platform/thinkpad_acpi/input/input6/event6"
[    29.173] (II) XINPUT: Adding extended input device "ThinkPad Extra Buttons" (type: KEYBOARD)
[    29.173] (**) Option "xkb_rules" "evdev"
[    29.173] (**) Option "xkb_model" "pc105"
[    29.173] (**) Option "xkb_layout" "gb"
[    29.934] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[    29.938] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
[    29.938] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[    29.938] (II) RADEON(0): Added native panel mode: 1024x768
[    29.938] (II) RADEON(0): Output: S-video, Detected Monitor Type: 0
[    34.344] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[    34.348] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
[    34.348] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[    34.348] (II) RADEON(0): Added native panel mode: 1024x768
[    34.348] (II) RADEON(0): Output: S-video, Detected Monitor Type: 0
[   129.867] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[   129.871] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
[   129.871] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[   129.871] (II) RADEON(0): Added native panel mode: 1024x768
[   129.871] (II) RADEON(0): Output: S-video, Detected Monitor Type: 0
[   130.544] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[   130.550] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
[   130.550] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[   130.550] (II) RADEON(0): Added native panel mode: 1024x768
[   130.550] (II) RADEON(0): Output: S-video, Detected Monitor Type: 0
[   130.578] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[   130.582] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
[   130.582] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[   130.582] (II) RADEON(0): Added native panel mode: 1024x768
[   130.582] (II) RADEON(0): Output: S-video, Detected Monitor Type: 0
[   130.770] (II) XKB: reuse xkmfile /var/lib/xkb/server-5550814D3DE81657FB75A6E398FC443242E652DD.xkm
```

Thank you in advance for your help, I'll try my best to follow along. I'm competent with computers, just new to Linux! (I have left the dark-side).

TkTk :)

---

