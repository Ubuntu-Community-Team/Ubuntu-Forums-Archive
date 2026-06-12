---
title: "How to activate FOSS ATI driver in Maverick?"
date: 2010-10-28
forum: Hardware
---

### Post by Ubuntiac on 2010-10-28
Hi there,

I'm having an odd problem with the FOSS ATI driver seemingly not being enabled after my update from Lucid to Maverick. I have an Xpress 200M card, which is fully supported by the FOSS ATI driver.

```
user@computer:~$ lspci -nn | grep VGA
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS482 [Radeon Xpress 200M] [1002:5975]
```

When I boot though, I get very slow performance and it looks like the system is falling back to software rendering instead of using the GPU as evidenced by:
**glxinfo |grep vendor**
```
server glx vendor string: SGI
client glx vendor string: Mesa Project and SGI
OpenGL vendor string: Mesa Project

```

**glxinfo |grep render**
```
direct rendering: Yes
OpenGL renderer string: Software Rasterizer
    GL_NV_conditional_render, GL_NV_depth_clamp, GL_NV_fragment_program, 
```

**Xorg.0.log**
```
[    16.860] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    16.883] X Protocol Version 11, Revision 0
[    16.883] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[    16.883] Current Operating System: Linux sheryls-joy 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:36:48 UTC 2010 i686
[    16.883] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=8db8c9fc-4067-45dd-8578-4c302b834b59 ro quiet splash nomodeset radeon.modeset=0 video=uvesafb:mode_option=1024x768-24,mtrr=3,scroll=ywrap
[    16.883] Build Date: 16 September 2010  05:39:22PM
[    16.883] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
[    16.883] Current version of pixman: 0.18.4
[    16.883] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    16.883] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    16.883] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Oct 28 02:32:24 2010
[    16.904] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    16.904] (==) No Layout section.  Using the first Screen section.
[    16.904] (==) No screen section available. Using defaults.
[    16.904] (**) |-->Screen "Default Screen Section" (0)
[    16.904] (**) |   |-->Monitor "<default monitor>"
[    16.905] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    16.905] (==) Automatically adding devices
[    16.905] (==) Automatically enabling devices
[    16.905] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    16.905] 	Entry deleted from font path.
[    16.905] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    16.905] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    16.905] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    16.905] (II) Loader magic: 0x81f8e00
[    16.905] (II) Module ABI versions:
[    16.905] 	X.Org ANSI C Emulation: 0.4
[    16.905] 	X.Org Video Driver: 8.0
[    16.905] 	X.Org XInput driver : 11.0
[    16.905] 	X.Org Server Extension : 4.0
[    16.906] (--) PCI:*(0:1:5:0) 1002:5975:1028:01f5 rev 0, Mem @ 0xd4000000/67108864, 0xd0100000/65536, I/O @ 0x00009000/256, BIOS @ 0x????????/131072
[    16.906] (II) Open ACPI successful (/var/run/acpid.socket)
[    16.906] (II) LoadModule: "extmod"
[    16.919] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    16.919] (II) Module extmod: vendor="X.Org Foundation"
[    16.919] 	compiled for 1.9.0, module version = 1.0.0
[    16.919] 	Module class: X.Org Server Extension
[    16.919] 	ABI class: X.Org Server Extension, version 4.0
[    16.919] (II) Loading extension MIT-SCREEN-SAVER
[    16.919] (II) Loading extension XFree86-VidModeExtension
[    16.919] (II) Loading extension XFree86-DGA
[    16.919] (II) Loading extension DPMS
[    16.919] (II) Loading extension XVideo
[    16.919] (II) Loading extension XVideo-MotionCompensation
[    16.919] (II) Loading extension X-Resource
[    16.919] (II) LoadModule: "dbe"
[    16.920] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    16.920] (II) Module dbe: vendor="X.Org Foundation"
[    16.920] 	compiled for 1.9.0, module version = 1.0.0
[    16.920] 	Module class: X.Org Server Extension
[    16.920] 	ABI class: X.Org Server Extension, version 4.0
[    16.920] (II) Loading extension DOUBLE-BUFFER
[    16.920] (II) LoadModule: "glx"
[    16.920] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    16.920] (II) Module glx: vendor="X.Org Foundation"
[    16.920] 	compiled for 1.9.0, module version = 1.0.0
[    16.920] 	ABI class: X.Org Server Extension, version 4.0
[    16.920] (==) AIGLX enabled
[    16.920] (II) Loading extension GLX
[    16.920] (II) LoadModule: "record"
[    16.921] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    16.921] (II) Module record: vendor="X.Org Foundation"
[    16.921] 	compiled for 1.9.0, module version = 1.13.0
[    16.921] 	Module class: X.Org Server Extension
[    16.921] 	ABI class: X.Org Server Extension, version 4.0
[    16.921] (II) Loading extension RECORD
[    16.921] (II) LoadModule: "dri"
[    16.921] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    16.921] (II) Module dri: vendor="X.Org Foundation"
[    16.922] 	compiled for 1.9.0, module version = 1.0.0
[    16.922] 	ABI class: X.Org Server Extension, version 4.0
[    16.922] (II) Loading extension XFree86-DRI
[    16.922] (II) LoadModule: "dri2"
[    16.922] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    16.922] (II) Module dri2: vendor="X.Org Foundation"
[    16.922] 	compiled for 1.9.0, module version = 1.2.0
[    16.922] 	ABI class: X.Org Server Extension, version 4.0
[    16.922] (II) Loading extension DRI2
[    16.922] (==) Matched ati as autoconfigured driver 0
[    16.922] (==) Matched vesa as autoconfigured driver 1
[    16.922] (==) Matched fbdev as autoconfigured driver 2
[    16.922] (==) Assigned the driver to the xf86ConfigLayout
[    16.922] (II) LoadModule: "ati"
[    16.923] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    16.923] (II) Module ati: vendor="X.Org Foundation"
[    16.923] 	compiled for 1.9.0, module version = 6.13.1
[    16.923] 	Module class: X.Org Video Driver
[    16.923] 	ABI class: X.Org Video Driver, version 8.0
[    16.923] (II) LoadModule: "radeon"
[    16.923] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    16.924] (II) Module radeon: vendor="X.Org Foundation"
[    16.924] 	compiled for 1.9.0, module version = 6.13.1
[    16.924] 	Module class: X.Org Video Driver
[    16.924] 	ABI class: X.Org Video Driver, version 8.0
[    16.924] (II) LoadModule: "vesa"
[    16.924] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    16.924] (II) Module vesa: vendor="X.Org Foundation"
[    16.924] 	compiled for 1.8.99.905, module version = 2.3.0
[    16.924] 	Module class: X.Org Video Driver
[    16.924] 	ABI class: X.Org Video Driver, version 8.0
[    16.924] (II) LoadModule: "fbdev"
[    16.925] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    16.925] (II) Module fbdev: vendor="X.Org Foundation"
[    16.925] 	compiled for 1.8.99.905, module version = 0.4.2
[    16.925] 	ABI class: X.Org Video Driver, version 8.0
[    16.925] (II) RADEON: Driver for ATI Radeon chipsets:
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
[    16.931] (II) VESA: driver for VESA chipsets: vesa
[    16.931] (II) FBDEV: driver for framebuffer: fbdev
[    16.931] (++) using VT number 7

[    16.931] (II) [KMS] drm report modesetting isn't supported.
[    16.931] (WW) Falling back to old probe method for vesa
[    16.931] (WW) Falling back to old probe method for fbdev
[    16.932] (II) Loading sub module "fbdevhw"
[    16.932] (II) LoadModule: "fbdevhw"
[    16.932] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    16.932] (II) Module fbdevhw: vendor="X.Org Foundation"
[    16.932] 	compiled for 1.9.0, module version = 0.0.2
[    16.932] 	ABI class: X.Org Video Driver, version 8.0
[    16.933] (II) RADEON(0): TOTO SAYS 00000000d0100000
[    16.933] (II) RADEON(0): MMIO registers at 0x00000000d0100000: size 64KB
[    16.933] (II) RADEON(0): PCI bus 1 card 5 func 0
[    16.933] (II) RADEON(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    16.933] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    16.933] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    16.933] (==) RADEON(0): Default visual is TrueColor
[    16.933] (II) Loading sub module "vgahw"
[    16.933] (II) LoadModule: "vgahw"
[    16.934] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    17.014] (II) Module vgahw: vendor="X.Org Foundation"
[    17.014] 	compiled for 1.9.0, module version = 0.1.0
[    17.014] 	ABI class: X.Org Video Driver, version 8.0
[    17.014] (II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
[    17.014] (==) RADEON(0): RGB weight 888
[    17.014] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    17.014] (--) RADEON(0): Chipset: "ATI Radeon XPRESS 200M 5975 (PCIE)" (ChipID = 0x5975)
[    17.014] (--) RADEON(0): Linear framebuffer at 0x00000000d4000000
[    17.014] (II) RADEON(0): PCI card detected
[    17.014] (II) Loading sub module "int10"
[    17.014] (II) LoadModule: "int10"
[    17.015] (II) Loading /usr/lib/xorg/modules/libint10.so
[    17.195] (II) Module int10: vendor="X.Org Foundation"
[    17.195] 	compiled for 1.9.0, module version = 1.0.0
[    17.195] 	ABI class: X.Org Video Driver, version 8.0
[    17.195] (II) RADEON(0): initializing int10
[    17.196] (II) RADEON(0): Primary V_BIOS segment is: 0xc000
[    17.196] (II) RADEON(0): Legacy BIOS detected
[    17.196] drmOpenDevice: node name is /dev/dri/card0
[    17.196] drmOpenDevice: open result is 12, (OK)
[    17.196] drmOpenByBusid: Searching for BusID pci:0000:01:05.0
[    17.196] drmOpenDevice: node name is /dev/dri/card0
[    17.196] drmOpenDevice: open result is 12, (OK)
[    17.196] drmOpenByBusid: drmOpenMinor returns 12
[    17.196] drmOpenByBusid: drmGetBusid reports pci:0000:01:05.0
[    17.197] (II) RADEON(0): [dri] Found DRI library version 1.3.0 and kernel module version 1.33.0
[    17.197] (II) RADEON(0): Direct rendering experimental on RS400/Xpress 200 enabled
[    17.197] (==) RADEON(0): Page Flipping disabled
[    17.197] (II) RADEON(0): Will try to use DMA for Xv image transfers
[    17.197] (II) RADEON(0): Detected total video RAM=16384K, accessible=65536K (PCI BAR=65536K)
[    17.197] (--) RADEON(0): Mapped VideoRAM: 16384 kByte (128 bit DDR SDRAM)
[    17.197] (II) RADEON(0): Color tiling enabled by default
[    17.197] (II) Loading sub module "ddc"
[    17.197] (II) LoadModule: "ddc"
[    17.197] (II) Module "ddc" already built-in
[    17.197] (II) Loading sub module "i2c"
[    17.197] (II) LoadModule: "i2c"
[    17.197] (II) Module "i2c" already built-in
[    17.197] (II) RADEON(0): ref_freq: 1432, min_out_pll: 20000, max_out_pll: 40000, min_in_pll: 100, max_in_pll: 1350, xclk: 20000, sclk: 400.000000, mclk: 200.000000
[    17.197] (II) RADEON(0): PLL parameters: rf=1432 rd=6 min=20000 max=40000; xclk=20000
[    17.197] (II) RADEON(0): Panel ID string: LPL                     
[    17.197] (II) RADEON(0): Panel Size from BIOS: 1280x800
[    17.197] (II) RADEON(0): BIOS provided dividers will be used.
[    17.197] (WW) RADEON(0): LVDS Info:
XRes: 1280, YRes: 800, DotClock: 75500
HBlank: 232, HOverPlus: 64, HSyncWidth: 48
VBlank: 32, VOverPlus: 3, VSyncWidth: 6
[    17.197] (WW) RADEON(0): LCD DDC Info Table found!
[    17.197] (II) RADEON(0): Output VGA-0 has no monitor section
[    17.197] (II) RADEON(0): I2C bus "VGA-0" initialized.
[    17.197] (II) RADEON(0): Output LVDS has no monitor section
[    17.197] (II) RADEON(0): I2C bus "LVDS" initialized.
[    17.197] (II) RADEON(0): Port0:
[    17.197]   XRANDR name: VGA-0
[    17.207]   Connector: VGA
[    17.207]   CRT1: INTERNAL_DAC2
[    17.207]   DDC reg: 0x68
[    17.207] (II) RADEON(0): Port1:
[    17.208]   XRANDR name: LVDS
[    17.208]   Connector: LVDS
[    17.208]   LCD1: INTERNAL_LVDS
[    17.208]   DDC reg: 0x1a0
[    17.208] (II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
[    17.223] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[    17.225] finished output detect: 0
[    17.225] (II) RADEON(0): I2C device "LVDS:ddc2" registered at address 0xA0.
[    17.285] (II) RADEON(0): EDID for output LVDS
[    17.285] (II) RADEON(0): Manufacturer: LPL  Model: 1001  Serial#: 0
[    17.285] (II) RADEON(0): Year: 2007  Week: 0
[    17.285] (II) RADEON(0): EDID Version: 1.3
[    17.285] (II) RADEON(0): Digital Display Input
[    17.285] (II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
[    17.285] (II) RADEON(0): Gamma: 2.20
[    17.285] (II) RADEON(0): No DPMS capabilities specified
[    17.285] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    17.285] (II) RADEON(0): First detailed timing is preferred mode
[    17.285] (II) RADEON(0): redX: 0.590 redY: 0.344   greenX: 0.323 greenY: 0.534
[    17.285] (II) RADEON(0): blueX: 0.156 blueY: 0.138   whiteX: 0.312 whiteY: 0.328
[    17.285] (II) RADEON(0): Manufacturer's mask: 0
[    17.285] (II) RADEON(0): Supported detailed timing:
[    17.285] (II) RADEON(0): clock: 75.5 MHz   Image Size:  331 x 207 mm
[    17.285] (II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1392 h_blank_end 1512 h_border: 0
[    17.285] (II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 832 v_border: 0
[    17.285] (II) RADEON(0): Supported detailed timing:
[    17.285] (II) RADEON(0): clock: 75.5 MHz   Image Size:  331 x 207 mm
[    17.285] (II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1392 h_blank_end 1512 h_border: 0
[    17.285] (II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 832 v_border: 0
[    17.285] (II) RADEON(0):  FU329
[    17.285] (II) RADEON(0):  $3@Kl&#8221;°Ã
[    17.285] (II) RADEON(0): EDID (in hex):
[    17.285] (II) RADEON(0): 	00ffffffffffff00320c011000000000
[    17.285] (II) RADEON(0): 	00110103802115780a0f109758528828
[    17.285] (II) RADEON(0): 	23505400000001010101010101010101
[    17.285] (II) RADEON(0): 	0101010101017e1d00e8502020304030
[    17.285] (II) RADEON(0): 	36004bcf100000197e1d00e850202030
[    17.285] (II) RADEON(0): 	403036004bcf10000000000000fe0046
[    17.285] (II) RADEON(0): 	55333239003135345730310a000000fe
[    17.286] (II) RADEON(0): 	002433404b6c94b0c301010a20200012
[    17.286] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[    17.286] (II) RADEON(0): EDID data from the display on output: LVDS ----------------------
[    17.286] (II) RADEON(0): Manufacturer: LPL  Model: 1001  Serial#: 0
[    17.286] (II) RADEON(0): Year: 2007  Week: 0
[    17.286] (II) RADEON(0): EDID Version: 1.3
[    17.286] (II) RADEON(0): Digital Display Input
[    17.286] (II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
[    17.286] (II) RADEON(0): Gamma: 2.20
[    17.286] (II) RADEON(0): No DPMS capabilities specified
[    17.286] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    17.286] (II) RADEON(0): First detailed timing is preferred mode
[    17.286] (II) RADEON(0): redX: 0.590 redY: 0.344   greenX: 0.323 greenY: 0.534
[    17.286] (II) RADEON(0): blueX: 0.156 blueY: 0.138   whiteX: 0.312 whiteY: 0.328
[    17.286] (II) RADEON(0): Manufacturer's mask: 0
[    17.286] (II) RADEON(0): Supported detailed timing:
[    17.286] (II) RADEON(0): clock: 75.5 MHz   Image Size:  331 x 207 mm
[    17.286] (II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1392 h_blank_end 1512 h_border: 0
[    17.286] (II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 832 v_border: 0
[    17.286] (II) RADEON(0): Supported detailed timing:
[    17.286] (II) RADEON(0): clock: 75.5 MHz   Image Size:  331 x 207 mm
[    17.286] (II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1392 h_blank_end 1512 h_border: 0
[    17.286] (II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 832 v_border: 0
[    17.286] (II) RADEON(0):  FU329
[    17.286] (II) RADEON(0):  $3@Kl&#8221;°Ã
[    17.286] (II) RADEON(0): EDID (in hex):
[    17.286] (II) RADEON(0): 	00ffffffffffff00320c011000000000
[    17.286] (II) RADEON(0): 	00110103802115780a0f109758528828
[    17.286] (II) RADEON(0): 	23505400000001010101010101010101
[    17.286] (II) RADEON(0): 	0101010101017e1d00e8502020304030
[    17.286] (II) RADEON(0): 	36004bcf100000197e1d00e850202030
[    17.286] (II) RADEON(0): 	403036004bcf10000000000000fe0046
[    17.286] (II) RADEON(0): 	55333239003135345730310a000000fe
[    17.286] (II) RADEON(0): 	002433404b6c94b0c301010a20200012
[    17.286] finished output detect: 1
[    17.286] finished all detect
[    17.301] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[    17.301] (II) RADEON(0): EDID for output VGA-0
[    17.361] (II) RADEON(0): EDID for output LVDS
[    17.361] (II) RADEON(0): Manufacturer: LPL  Model: 1001  Serial#: 0
[    17.361] (II) RADEON(0): Year: 2007  Week: 0
[    17.361] (II) RADEON(0): EDID Version: 1.3
[    17.361] (II) RADEON(0): Digital Display Input
[    17.361] (II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
[    17.361] (II) RADEON(0): Gamma: 2.20
[    17.361] (II) RADEON(0): No DPMS capabilities specified
[    17.361] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    17.361] (II) RADEON(0): First detailed timing is preferred mode
[    17.361] (II) RADEON(0): redX: 0.590 redY: 0.344   greenX: 0.323 greenY: 0.534
[    17.361] (II) RADEON(0): blueX: 0.156 blueY: 0.138   whiteX: 0.312 whiteY: 0.328
[    17.361] (II) RADEON(0): Manufacturer's mask: 0
[    17.361] (II) RADEON(0): Supported detailed timing:
[    17.361] (II) RADEON(0): clock: 75.5 MHz   Image Size:  331 x 207 mm
[    17.361] (II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1392 h_blank_end 1512 h_border: 0
[    17.361] (II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 832 v_border: 0
[    17.361] (II) RADEON(0): Supported detailed timing:
[    17.361] (II) RADEON(0): clock: 75.5 MHz   Image Size:  331 x 207 mm
[    17.361] (II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1392 h_blank_end 1512 h_border: 0
[    17.361] (II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 832 v_border: 0
[    17.361] (II) RADEON(0):  FU329
[    17.361] (II) RADEON(0):  $3@Kl&#8221;°Ã
[    17.361] (II) RADEON(0): EDID (in hex):
[    17.361] (II) RADEON(0): 	00ffffffffffff00320c011000000000
[    17.361] (II) RADEON(0): 	00110103802115780a0f109758528828
[    17.361] (II) RADEON(0): 	23505400000001010101010101010101
[    17.361] (II) RADEON(0): 	0101010101017e1d00e8502020304030
[    17.361] (II) RADEON(0): 	36004bcf100000197e1d00e850202030
[    17.361] (II) RADEON(0): 	403036004bcf10000000000000fe0046
[    17.362] (II) RADEON(0): 	55333239003135345730310a000000fe
[    17.362] (II) RADEON(0): 	002433404b6c94b0c301010a20200012
[    17.362] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[    17.362] (II) RADEON(0): EDID data from the display on output: LVDS ----------------------
[    17.362] (II) RADEON(0): Manufacturer: LPL  Model: 1001  Serial#: 0
[    17.362] (II) RADEON(0): Year: 2007  Week: 0
[    17.362] (II) RADEON(0): EDID Version: 1.3
[    17.362] (II) RADEON(0): Digital Display Input
[    17.362] (II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
[    17.362] (II) RADEON(0): Gamma: 2.20
[    17.362] (II) RADEON(0): No DPMS capabilities specified
[    17.362] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    17.362] (II) RADEON(0): First detailed timing is preferred mode
[    17.362] (II) RADEON(0): redX: 0.590 redY: 0.344   greenX: 0.323 greenY: 0.534
[    17.362] (II) RADEON(0): blueX: 0.156 blueY: 0.138   whiteX: 0.312 whiteY: 0.328
[    17.362] (II) RADEON(0): Manufacturer's mask: 0
[    17.362] (II) RADEON(0): Supported detailed timing:
[    17.362] (II) RADEON(0): clock: 75.5 MHz   Image Size:  331 x 207 mm
[    17.362] (II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1392 h_blank_end 1512 h_border: 0
[    17.362] (II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 832 v_border: 0
[    17.362] (II) RADEON(0): Supported detailed timing:
[    17.362] (II) RADEON(0): clock: 75.5 MHz   Image Size:  331 x 207 mm
[    17.362] (II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1392 h_blank_end 1512 h_border: 0
[    17.362] (II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 832 v_border: 0
[    17.362] (II) RADEON(0):  FU329
[    17.362] (II) RADEON(0):  $3@Kl&#8221;°Ã
[    17.362] (II) RADEON(0): EDID (in hex):
[    17.362] (II) RADEON(0): 	00ffffffffffff00320c011000000000
[    17.362] (II) RADEON(0): 	00110103802115780a0f109758528828
[    17.362] (II) RADEON(0): 	23505400000001010101010101010101
[    17.362] (II) RADEON(0): 	0101010101017e1d00e8502020304030
[    17.362] (II) RADEON(0): 	36004bcf100000197e1d00e850202030
[    17.362] (II) RADEON(0): 	403036004bcf10000000000000fe0046
[    17.362] (II) RADEON(0): 	55333239003135345730310a000000fe
[    17.362] (II) RADEON(0): 	002433404b6c94b0c301010a20200012
[    17.362] (II) RADEON(0): EDID vendor "LPL", prod id 4097
[    17.362] (II) RADEON(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    17.362] (II) RADEON(0): Printing probed modes for output LVDS
[    17.362] (II) RADEON(0): Modeline "1280x800"x60.0   75.50  1280 1344 1392 1512  800 803 809 832 -hsync -vsync (49.9 kHz)
[    17.362] (II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
[    17.362] (II) RADEON(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
[    17.362] (II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
[    17.362] (II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
[    17.362] (II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
[    17.362] (II) RADEON(0): Output VGA-0 disconnected
[    17.362] (II) RADEON(0): Output LVDS connected
[    17.362] (II) RADEON(0): Using exact sizes for initial modes
[    17.362] (II) RADEON(0): Output LVDS using initial mode 1280x800
[    17.362] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    17.362] (==) RADEON(0): DPI set to (96, 96)
[    17.362] (II) Loading sub module "fb"
[    17.362] (II) LoadModule: "fb"
[    17.363] (II) Loading /usr/lib/xorg/modules/libfb.so
[    17.363] (II) Module fb: vendor="X.Org Foundation"
[    17.363] 	compiled for 1.9.0, module version = 1.0.0
[    17.363] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    17.363] (II) Loading sub module "ramdac"
[    17.363] (II) LoadModule: "ramdac"
[    17.363] (II) Module "ramdac" already built-in
[    17.363] (==) RADEON(0): Using XAA acceleration architecture
[    17.363] (II) Loading sub module "xaa"
[    17.363] (II) LoadModule: "xaa"
[    17.364] (II) Loading /usr/lib/xorg/modules/libxaa.so
[    17.641] (II) Module xaa: vendor="X.Org Foundation"
[    17.641] 	compiled for 1.9.0, module version = 1.2.1
[    17.641] 	ABI class: X.Org Video Driver, version 8.0
[    17.641] (==) RADEON(0): Assuming overlay scaler buffer width is 1536
[    17.641] (II) RADEON(0): No MM_TABLE found - assuming CARD is not TV-in capable.
[    17.641] (!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
[    17.641] (II) UnloadModule: "vesa"
[    17.641] (II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    17.641] (II) UnloadModule: "fbdev"
[    17.641] (II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    17.641] (II) UnloadModule: "fbdevhw"
[    17.641] (II) Unloading /usr/lib/xorg/modules/libfbdevhw.so
[    17.641] (--) Depth 24 pixmap format is 32 bpp
[    17.641] (II) RADEON(0): RADEONScreenInit d4000000 0 0
[    17.644] Entering TV Save
[    17.644] Save TV timing tables
[    17.644] saveTimingTables: reading timing tables
[    17.644] TV Save done
[    17.644] disable LVDS
[    17.644] (II) RADEON(0): Dynamic Power Management Disabled
[    17.644] (==) RADEON(0): Using 24 bit depth buffer
[    17.644] (II) RADEON(0): RADEONInitMemoryMap() : 
[    17.644] (II) RADEON(0):   mem_size         : 0x02000000
[    17.644] (II) RADEON(0):   MC_FB_LOCATION   : 0x3fff3f00
[    17.644] (II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
[    17.644] (II) RADEON(0): Depth moves disabled by default
[    17.644] (II) RADEON(0): Using 32 MB GART aperture
[    17.644] (II) RADEON(0): Using 1 MB for the ring buffer
[    17.644] (II) RADEON(0): Using 2 MB for vertex/indirect buffers
[    17.644] (II) RADEON(0): Using 29 MB for GART textures
[    17.644] (II) RADEON(0): Memory manager initialized to (0,0) (1280,3276)
[    17.644] (II) RADEON(0): Reserved area from (0,1280) to (1280,1282)
[    17.644] (II) RADEON(0): Largest offscreen area available: 1280 x 1994
[    17.644] (II) RADEON(0): Will use front buffer at offset 0x0
[    17.644] (II) RADEON(0): Will use back buffer at offset 0x370000
[    17.644] (II) RADEON(0): Will use depth buffer at offset 0x9b0000
[    17.644] (II) RADEON(0): Will use 0 kb for textures at offset 0xff0000
[    17.644] (EE) RADEON(0): Static buffer allocation failed.  Disabling DRI.
[    17.644] (EE) RADEON(0): At least 19200 kB of video memory needed at this resolution and depth.
[    17.644] (II) RADEON(0): RADEONRestoreMemMapRegisters() : 
[    17.644] (II) RADEON(0):   MC_FB_LOCATION   : 0x3fff3f00 0x3fff3f00
[    17.644] (II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
[    17.745] (==) RADEON(0): Backing store disabled
[    17.745] (WW) RADEON(0): Direct rendering disabled
[    17.745] (II) RADEON(0): Render acceleration disabled
[    17.745] (II) RADEON(0): num quad-pipes is 1
[    17.745] (II) RADEON(0): Using XFree86 Acceleration Architecture (XAA)
[    17.745] 	Screen to screen bit blits
[    17.745] 	Solid filled rectangles
[    17.745] 	8x8 mono pattern filled rectangles
[    17.745] 	Indirect CPU to Screen color expansion
[    17.745] 	Solid Lines
[    17.745] 	Scanline Image Writes
[    17.745] 	Setting up tile and stipple cache:
[    17.745] 		32 128x128 slots
[    17.745] 		13 256x256 slots
[    17.745] 		4 512x512 slots
[    17.745] (II) RADEON(0): Acceleration enabled
[    17.745] (==) RADEON(0): DPMS enabled
[    17.745] (==) RADEON(0): Silken mouse enabled
[    17.745] (II) RADEON(0): Will use 32 kb for hardware cursor 0 at offset 0x00642800
[    17.745] (II) RADEON(0): Will use 32 kb for hardware cursor 1 at offset 0x00647800
[    17.745] (II) RADEON(0): Largest offscreen area available: 1280 x 1986
[    17.745] (II) RADEON(0): No video input capabilities detected and no information is provided - disabling multimedia i2c
[    17.745] (II) Loading sub module "theatre_detect"
[    17.745] (II) LoadModule: "theatre_detect"
[    17.746] (II) Loading /usr/lib/xorg/modules/multimedia/theatre_detect_drv.so
[    17.778] (II) Module theatre_detect: vendor="X.Org Foundation"
[    17.778] 	compiled for 1.9.0, module version = 1.0.0
[    17.779] 	ABI class: X.Org Video Driver, version 8.0
[    17.779] (II) RADEON(0): no multimedia table present, disabling Rage Theatre.
[    17.779] (II) RADEON(0): Set up overlay video
[    17.779] (II) RADEON(0): Textured video requires CP on R5xx/R6xx/R7xx/IGP
[    17.792] disable TVDAC
[    17.792] disable LVDS
[    17.792] disable LVDS
[    17.792] init memmap
[    17.792] init common
[    17.792] init crtc1
[    17.792] init pll1
[    17.792] restore memmap
[    17.792] (II) RADEON(0): RADEONRestoreMemMapRegisters() : 
[    17.792] (II) RADEON(0):   MC_FB_LOCATION   : 0x3fff3f00 0x3fff3f00
[    17.792] (II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
[    17.893] restore common
[    17.893] restore crtc1
[    17.893] restore pll1
[    17.893] set RMX
[    17.893] set LVDS
[    17.893] enable LVDS
[    18.393] disable TVDAC
[    18.393] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    18.393] (--) RandR disabled
[    18.393] (II) Initializing built-in extension Generic Event Extension
[    18.393] (II) Initializing built-in extension SHAPE
[    18.393] (II) Initializing built-in extension MIT-SHM
[    18.393] (II) Initializing built-in extension XInputExtension
[    18.393] (II) Initializing built-in extension XTEST
[    18.393] (II) Initializing built-in extension BIG-REQUESTS
[    18.393] (II) Initializing built-in extension SYNC
[    18.393] (II) Initializing built-in extension XKEYBOARD
[    18.393] (II) Initializing built-in extension XC-MISC
[    18.393] (II) Initializing built-in extension SECURITY
[    18.393] (II) Initializing built-in extension XINERAMA
[    18.393] (II) Initializing built-in extension XFIXES
[    18.393] (II) Initializing built-in extension RENDER
[    18.393] (II) Initializing built-in extension RANDR
[    18.393] (II) Initializing built-in extension COMPOSITE
[    18.393] (II) Initializing built-in extension DAMAGE
[    18.393] (II) Initializing built-in extension GESTURE
[    18.407] (II) AIGLX: Screen 0 is not DRI2 capable
[    18.407] (II) AIGLX: Screen 0 is not DRI capable
[    18.479] (II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
[    18.479] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    18.480] (II) RADEON(0): Setting screen physical size to 338 x 211
[    18.508] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    18.520] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    18.520] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    18.520] (II) LoadModule: "evdev"
[    18.521] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.521] (II) Module evdev: vendor="X.Org Foundation"
[    18.521] 	compiled for 1.9.0, module version = 2.3.2
[    18.521] 	Module class: X.Org XInput Driver
[    18.521] 	ABI class: X.Org XInput driver, version 11.0
[    18.521] (**) Power Button: always reports core events
[    18.521] (**) Power Button: Device: "/dev/input/event3"
[    18.533] (II) Power Button: Found keys
[    18.533] (II) Power Button: Configuring as keyboard
[    18.533] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    18.533] (**) Option "xkb_rules" "evdev"
[    18.533] (**) Option "xkb_model" "pc105"
[    18.533] (**) Option "xkb_layout" "us"
[    18.535] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    18.535] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    18.535] (**) Video Bus: always reports core events
[    18.535] (**) Video Bus: Device: "/dev/input/event5"
[    18.549] (II) Video Bus: Found keys
[    18.549] (II) Video Bus: Configuring as keyboard
[    18.549] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    18.549] (**) Option "xkb_rules" "evdev"
[    18.549] (**) Option "xkb_model" "pc105"
[    18.549] (**) Option "xkb_layout" "us"
[    18.549] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    18.549] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    18.550] (**) Power Button: always reports core events
[    18.550] (**) Power Button: Device: "/dev/input/event0"
[    18.565] (II) Power Button: Found keys
[    18.565] (II) Power Button: Configuring as keyboard
[    18.565] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    18.565] (**) Option "xkb_rules" "evdev"
[    18.565] (**) Option "xkb_model" "pc105"
[    18.565] (**) Option "xkb_layout" "us"
[    18.565] (II) config/udev: Adding input device Lid Switch (/dev/input/event2)
[    18.565] (II) No input driver/identifier specified (ignoring)
[    18.566] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    18.566] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    18.566] (**) Sleep Button: always reports core events
[    18.566] (**) Sleep Button: Device: "/dev/input/event1"
[    18.581] (II) Sleep Button: Found keys
[    18.581] (II) Sleep Button: Configuring as keyboard
[    18.581] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    18.581] (**) Option "xkb_rules" "evdev"
[    18.581] (**) Option "xkb_model" "pc105"
[    18.581] (**) Option "xkb_layout" "us"
[    18.584] (II) config/udev: Adding input device Logitech Optical USB Mouse (/dev/input/event6)
[    18.584] (**) Logitech Optical USB Mouse: Applying InputClass "evdev pointer catchall"
[    18.584] (**) Logitech Optical USB Mouse: always reports core events
[    18.584] (**) Logitech Optical USB Mouse: Device: "/dev/input/event6"
[    18.597] (II) Logitech Optical USB Mouse: Found 3 mouse buttons
[    18.597] (II) Logitech Optical USB Mouse: Found scroll wheel(s)
[    18.597] (II) Logitech Optical USB Mouse: Found relative axes
[    18.597] (II) Logitech Optical USB Mouse: Found x and y relative axes
[    18.597] (II) Logitech Optical USB Mouse: Configuring as mouse
[    18.597] (**) Logitech Optical USB Mouse: YAxisMapping: buttons 4 and 5
[    18.597] (**) Logitech Optical USB Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    18.597] (II) XINPUT: Adding extended input device "Logitech Optical USB Mouse" (type: MOUSE)
[    18.597] (II) Logitech Optical USB Mouse: initialized for relative axes.
[    18.597] (II) config/udev: Adding input device Logitech Optical USB Mouse (/dev/input/mouse0)
[    18.597] (II) No input driver/identifier specified (ignoring)
[    18.598] (II) config/udev: Adding input device Microsoft MicrosoftÂ® Digital Media Keyboard 3000 (/dev/input/event7)
[    18.598] (**) Microsoft MicrosoftÂ® Digital Media Keyboard 3000: Applying InputClass "evdev keyboard catchall"
[    18.598] (**) Microsoft MicrosoftÂ® Digital Media Keyboard 3000: always reports core events
[    18.598] (**) Microsoft MicrosoftÂ® Digital Media Keyboard 3000: Device: "/dev/input/event7"
[    18.613] (II) Microsoft MicrosoftÂ® Digital Media Keyboard 3000: Found keys
[    18.613] (II) Microsoft MicrosoftÂ® Digital Media Keyboard 3000: Configuring as keyboard
[    18.613] (II) XINPUT: Adding extended input device "Microsoft MicrosoftÂ® Digital Media Keyboard 3000" (type: KEYBOARD)
[    18.613] (**) Option "xkb_rules" "evdev"
[    18.613] (**) Option "xkb_model" "pc105"
[    18.613] (**) Option "xkb_layout" "us"
[    18.614] (II) config/udev: Adding input device Microsoft MicrosoftÂ® Digital Media Keyboard 3000 (/dev/input/event8)
[    18.614] (**) Microsoft MicrosoftÂ® Digital Media Keyboard 3000: Applying InputClass "evdev keyboard catchall"
[    18.614] (**) Microsoft MicrosoftÂ® Digital Media Keyboard 3000: always reports core events
[    18.614] (**) Microsoft MicrosoftÂ® Digital Media Keyboard 3000: Device: "/dev/input/event8"
[    18.629] (II) Microsoft MicrosoftÂ® Digital Media Keyboard 3000: Found 1 mouse buttons
[    18.629] (II) Microsoft MicrosoftÂ® Digital Media Keyboard 3000: Found scroll wheel(s)
[    18.629] (II) Microsoft MicrosoftÂ® Digital Media Keyboard 3000: Found relative axes
[    18.629] (II) Microsoft MicrosoftÂ® Digital Media Keyboard 3000: Found absolute axes
[    18.629] (II) Microsoft MicrosoftÂ® Digital Media Keyboard 3000: Found x and y absolute axes
[    18.629] (II) Microsoft MicrosoftÂ® Digital Media Keyboard 3000: Found keys
[    18.629] (II) Microsoft MicrosoftÂ® Digital Media Keyboard 3000: Configuring as mouse
[    18.629] (II) Microsoft MicrosoftÂ® Digital Media Keyboard 3000: Configuring as keyboard
[    18.629] (**) Microsoft MicrosoftÂ® Digital Media Keyboard 3000: YAxisMapping: buttons 4 and 5
[    18.629] (**) Microsoft MicrosoftÂ® Digital Media Keyboard 3000: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    18.629] (II) XINPUT: Adding extended input device "Microsoft MicrosoftÂ® Digital Media Keyboard 3000" (type: KEYBOARD)
[    18.629] (**) Option "xkb_rules" "evdev"
[    18.629] (**) Option "xkb_model" "pc105"
[    18.629] (**) Option "xkb_layout" "us"
[    18.629] (EE) Microsoft MicrosoftÂ® Digital Media Keyboard 3000: failed to initialize for relative axes.
[    18.629] (WW) Microsoft MicrosoftÂ® Digital Media Keyboard 3000: found 37 axes, limiting to 36.
[    18.629] (II) Microsoft MicrosoftÂ® Digital Media Keyboard 3000: initialized for absolute axes.
[    18.630] (II) config/udev: Adding input device Microsoft MicrosoftÂ® Digital Media Keyboard 3000 (/dev/input/js0)
[    18.630] (II) No input driver/identifier specified (ignoring)
[    18.632] (II) config/udev: Adding input device HDA ATI SB Mic at Ext Right Jack (/dev/input/event10)
[    18.632] (II) No input driver/identifier specified (ignoring)
[    18.633] (II) config/udev: Adding input device HDA ATI SB HP Out at Ext Right Jack (/dev/input/event11)
[    18.633] (II) No input driver/identifier specified (ignoring)
[    18.634] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    18.634] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    18.634] (**) AT Translated Set 2 keyboard: always reports core events
[    18.634] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    18.645] (II) AT Translated Set 2 keyboard: Found keys
[    18.645] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    18.645] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    18.645] (**) Option "xkb_rules" "evdev"
[    18.645] (**) Option "xkb_model" "pc105"
[    18.645] (**) Option "xkb_layout" "us"
[    18.646] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event12)
[    18.646] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    18.646] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    18.646] (II) LoadModule: "synaptics"
[    18.646] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    18.646] (II) Module synaptics: vendor="X.Org Foundation"
[    18.646] 	compiled for 1.9.0, module version = 1.2.2
[    18.646] 	Module class: X.Org XInput Driver
[    18.646] 	ABI class: X.Org XInput driver, version 11.0
[    18.646] (II) Synaptics touchpad driver version 1.2.2
[    18.646] (**) Option "Device" "/dev/input/event12"
[    18.677] (II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[    18.677] (II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[    18.677] (II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    18.677] (II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
[    18.677] (II) SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    18.709] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    18.709] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    18.725] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    18.725] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    18.725] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
[    18.725] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    18.725] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    18.757] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    18.757] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
[    18.757] (II) No input driver/identifier specified (ignoring)
[    18.761] (II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event9)
[    18.761] (**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    18.761] (**) Dell WMI hotkeys: always reports core events
[    18.761] (**) Dell WMI hotkeys: Device: "/dev/input/event9"
[    18.773] (II) Dell WMI hotkeys: Found keys
[    18.773] (II) Dell WMI hotkeys: Configuring as keyboard
[    18.773] (II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD)
[    18.773] (**) Option "xkb_rules" "evdev"
[    18.773] (**) Option "xkb_model" "pc105"
[    18.773] (**) Option "xkb_layout" "us"
[    23.230] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[    23.289] (II) RADEON(0): EDID vendor "LPL", prod id 4097
[    23.289] (II) RADEON(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    23.289] (II) RADEON(0): Printing DDC gathered Modelines:
[    23.289] (II) RADEON(0): Modeline "1280x800"x0.0   75.50  1280 1344 1392 1512  800 803 809 832 -hsync -vsync (49.9 kHz)
[    23.289] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[    23.289] (II) RADEON(0): EDID data from the display on output: LVDS ----------------------
[    23.289] (II) RADEON(0): Manufacturer: LPL  Model: 1001  Serial#: 0
[    23.289] (II) RADEON(0): Year: 2007  Week: 0
[    23.289] (II) RADEON(0): EDID Version: 1.3
[    23.289] (II) RADEON(0): Digital Display Input
[    23.289] (II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
[    23.289] (II) RADEON(0): Gamma: 2.20
[    23.289] (II) RADEON(0): No DPMS capabilities specified
[    23.290] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    23.290] (II) RADEON(0): First detailed timing is preferred mode
[    23.290] (II) RADEON(0): redX: 0.590 redY: 0.344   greenX: 0.323 greenY: 0.534
[    23.290] (II) RADEON(0): blueX: 0.156 blueY: 0.138   whiteX: 0.312 whiteY: 0.328
[    23.290] (II) RADEON(0): Manufacturer's mask: 0
[    23.290] (II) RADEON(0): Supported detailed timing:
[    23.290] (II) RADEON(0): clock: 75.5 MHz   Image Size:  331 x 207 mm
[    23.290] (II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1392 h_blank_end 1512 h_border: 0
[    23.290] (II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 832 v_border: 0
[    23.290] (II) RADEON(0): Supported detailed timing:
[    23.290] (II) RADEON(0): clock: 75.5 MHz   Image Size:  331 x 207 mm
[    23.290] (II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1392 h_blank_end 1512 h_border: 0
[    23.290] (II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 832 v_border: 0
[    23.290] (II) RADEON(0):  FU329
[    23.290] (II) RADEON(0):  $3@Kl&#8221;°Ã
[    23.290] (II) RADEON(0): EDID (in hex):
[    23.290] (II) RADEON(0): 	00ffffffffffff00320c011000000000
[    23.290] (II) RADEON(0): 	00110103802115780a0f109758528828
[    23.290] (II) RADEON(0): 	23505400000001010101010101010101
[    23.290] (II) RADEON(0): 	0101010101017e1d00e8502020304030
[    23.290] (II) RADEON(0): 	36004bcf100000197e1d00e850202030
[    23.290] (II) RADEON(0): 	403036004bcf10000000000000fe0046
[    23.290] (II) RADEON(0): 	55333239003135345730310a000000fe
[    23.290] (II) RADEON(0): 	002433404b6c94b0c301010a20200012
[    23.290] (II) RADEON(0): EDID vendor "LPL", prod id 4097
[    23.290] (II) RADEON(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    30.497] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[    30.558] (II) RADEON(0): EDID vendor "LPL", prod id 4097
[    30.558] (II) RADEON(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    30.558] (II) RADEON(0): Printing DDC gathered Modelines:
[    30.558] (II) RADEON(0): Modeline "1280x800"x0.0   75.50  1280 1344 1392 1512  800 803 809 832 -hsync -vsync (49.9 kHz)
[    30.558] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[    30.558] (II) RADEON(0): EDID data from the display on output: LVDS ----------------------
[    30.558] (II) RADEON(0): Manufacturer: LPL  Model: 1001  Serial#: 0
[    30.558] (II) RADEON(0): Year: 2007  Week: 0
[    30.558] (II) RADEON(0): EDID Version: 1.3
[    30.558] (II) RADEON(0): Digital Display Input
[    30.559] (II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
[    30.559] (II) RADEON(0): Gamma: 2.20
[    30.559] (II) RADEON(0): No DPMS capabilities specified
[    30.559] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    30.559] (II) RADEON(0): First detailed timing is preferred mode
[    30.559] (II) RADEON(0): redX: 0.590 redY: 0.344   greenX: 0.323 greenY: 0.534
[    30.559] (II) RADEON(0): blueX: 0.156 blueY: 0.138   whiteX: 0.312 whiteY: 0.328
[    30.559] (II) RADEON(0): Manufacturer's mask: 0
[    30.559] (II) RADEON(0): Supported detailed timing:
[    30.559] (II) RADEON(0): clock: 75.5 MHz   Image Size:  331 x 207 mm
[    30.559] (II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1392 h_blank_end 1512 h_border: 0
[    30.559] (II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 832 v_border: 0
[    30.559] (II) RADEON(0): Supported detailed timing:
[    30.559] (II) RADEON(0): clock: 75.5 MHz   Image Size:  331 x 207 mm
[    30.559] (II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1392 h_blank_end 1512 h_border: 0
[    30.559] (II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 832 v_border: 0
[    30.559] (II) RADEON(0):  FU329
[    30.559] (II) RADEON(0):  $3@Kl&#8221;°Ã
[    30.559] (II) RADEON(0): EDID (in hex):
[    30.559] (II) RADEON(0): 	00ffffffffffff00320c011000000000
[    30.559] (II) RADEON(0): 	00110103802115780a0f109758528828
[    30.559] (II) RADEON(0): 	23505400000001010101010101010101
[    30.559] (II) RADEON(0): 	0101010101017e1d00e8502020304030
[    30.559] (II) RADEON(0): 	36004bcf100000197e1d00e850202030
[    30.559] (II) RADEON(0): 	403036004bcf10000000000000fe0046
[    30.559] (II) RADEON(0): 	55333239003135345730310a000000fe
[    30.559] (II) RADEON(0): 	002433404b6c94b0c301010a20200012
[    30.559] (II) RADEON(0): EDID vendor "LPL", prod id 4097
[    30.559] (II) RADEON(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.

```

I've tried reinstalling xserver-xorg-video-ati and xserver-xorg-video-radeon without any improvement and I don't have any xorg.conf, so I'm kinda mystified how to get the ATI driver running...

---

### Post by Ubuntiac on 2010-10-28
Anyone?

The weird thing is, opengl and desktop effects work fine using a live usb syaing that it's using "DRI from the R300 project".

**LiveUSB dmesg:**
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.35-21-generic (buildd@roseapple) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu2) ) #31-Ubuntu SMP Mon Sep 13 22:39:43 UTC 2010 (Ubuntu 2.6.35-21.31-generic 2.6.35.4)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000ce000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003ee70000 (usable)
[    0.000000]  BIOS-e820: 000000003ee70000 - 000000003ee80000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003ee80000 - 000000003ef00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003ef00000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled: non-PAE kernel!
[    0.000000] DMI present.
[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x3ee70 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-E3FFF uncachable
[    0.000000]   E4000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FFC0000000 write-back
[    0.000000]   1 base 003F000000 mask FFFF000000 uncachable
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 0000000000002000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000001000 (reserved)
[    0.000000]  modified: 0000000000001000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009dc00 (usable)
[    0.000000]  modified: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000ce000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000003ee70000 (usable)
[    0.000000]  modified: 000000003ee70000 - 000000003ee80000 (ACPI data)
[    0.000000]  modified: 000000003ee80000 - 000000003ef00000 (ACPI NVS)
[    0.000000]  modified: 000000003ef00000 - 0000000040000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] found SMP MP-table at [c00f8530] f8530
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 15000-1a000
[    0.000000] RAMDISK: 3e391000 - 3ee70000
[    0.000000] Allocated new RAMDISK: 009a5000 - 014830da
[    0.000000] Move RAMDISK from 000000003e391000 - 000000003ee6f0d9 to 009a5000 - 014830d9
[    0.000000] ACPI: RSDP 000f8500 00014 (v00 PTLTD )
[    0.000000] ACPI: RSDT 3ee79575 0003C (v01 DELL    M08     06040000  LTP 00000000)
[    0.000000] ACPI: FACP 3ee7fb90 00074 (v01 ATI    Bowfin   06040000 ATI  000F4240)
[    0.000000] ACPI: DSDT 3ee795b1 065DF (v01    ATI    SB600 06040000 MSFT 03000000)
[    0.000000] ACPI: FACS 3ee90fc0 00040
[    0.000000] ACPI: TCPA 3ee7fc04 00032 (v02 AMD             06040000 PTEC 00000000)
[    0.000000] ACPI: SSDT 3ee7fc36 001C4 (v01 PTLTD  POWERNOW 06040000  LTP 00000001)
[    0.000000] ACPI: APIC 3ee7fdfa 00054 (v01 PTLTD  ? APIC   06040000  LTP 00000000)
[    0.000000] ACPI: MCFG 3ee7fe4e 0003C (v01 PTLTD    MCFG   06040000  LTP 00000000)
[    0.000000] ACPI: SLIC 3ee7fe8a 00176 (v01 DELL    M08     06040000  LTP 00000000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 118MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000001 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0003ee70
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000001 -> 0x00000002
[    0.000000]     0: 0x00000010 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x0003ee70
[    0.000000] On node 0 totalpages: 257534
[    0.000000] free_area_init_node: node 0, pgdat c07ffcc0, node_mem_map c1485020
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3950 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 237 pages used for memmap
[    0.000000]   HighMem zone: 30085 pages, LIFO batch:7
[    0.000000] Using APIC driver default
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] early_res array is doubled to 64 at [16000 - 167ff]
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000ce000
[    0.000000] PM: Registered nosave memory: 00000000000ce000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 40000000:a0000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c2000000 s36416 r0 d20928 u2097152
[    0.000000] pcpu-alloc: s36416 r0 d20928 u2097152 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 255521
[    0.000000] Kernel command line: noprompt cdrom-detect/try-usb=true file=/cdrom/preseed/kubuntu.seed boot=casper maybe-ubiquity initrd=/casper/initrd.lz quiet splash --
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 5152940 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Subtract (50 early reservations)
[    0.000000]   #1 [0000001000 - 0000002000]   EX TRAMPOLINE
[    0.000000]   #2 [0000100000 - 00009a0adc]   TEXT DATA BSS
[    0.000000]   #3 [00009a1000 - 00009a4150]             BRK
[    0.000000]   #4 [00000f8540 - 0000100000]   BIOS reserved
[    0.000000]   #5 [00000f8530 - 00000f8540]    MP-table mpf
[    0.000000]   #6 [000009dc00 - 000009e171]   BIOS reserved
[    0.000000]   #7 [000009e2cd - 00000f8530]   BIOS reserved
[    0.000000]   #8 [000009e171 - 000009e2cd]    MP-table mpc
[    0.000000]   #9 [0000010000 - 0000011000]      TRAMPOLINE
[    0.000000]   #10 [0000011000 - 0000015000]     ACPI WAKEUP
[    0.000000]   #11 [0000015000 - 0000016000]         PGTABLE
[    0.000000]   #12 [00009a5000 - 0001484000]     NEW RAMDISK
[    0.000000]   #13 [0001484000 - 0001485000]         BOOTMEM
[    0.000000]   #14 [0001485000 - 0001c65000]         BOOTMEM
[    0.000000]   #15 [0001c65000 - 0001c65004]         BOOTMEM
[    0.000000]   #16 [0001c65040 - 0001c65100]         BOOTMEM
[    0.000000]   #17 [0001c65100 - 0001c65154]         BOOTMEM
[    0.000000]   #18 [0001c65180 - 0001c68180]         BOOTMEM
[    0.000000]   #19 [0001c68180 - 0001c6818c]         BOOTMEM
[    0.000000]   #20 [0001c681c0 - 0001c687c0]         BOOTMEM
[    0.000000]   #21 [0001c687c0 - 0001c687e7]         BOOTMEM
[    0.000000]   #22 [0001c68800 - 0001c68988]         BOOTMEM
[    0.000000]   #23 [0001c689c0 - 0001c68a00]         BOOTMEM
[    0.000000]   #24 [0001c68a00 - 0001c68a40]         BOOTMEM
[    0.000000]   #25 [0001c68a40 - 0001c68a80]         BOOTMEM
[    0.000000]   #26 [0001c68a80 - 0001c68ac0]         BOOTMEM
[    0.000000]   #27 [0001c68ac0 - 0001c68b00]         BOOTMEM
[    0.000000]   #28 [0001c68b00 - 0001c68b40]         BOOTMEM
[    0.000000]   #29 [0001c68b40 - 0001c68b80]         BOOTMEM
[    0.000000]   #30 [0001c68b80 - 0001c68bc0]         BOOTMEM
[    0.000000]   #31 [0001c68bc0 - 0001c68c00]         BOOTMEM
[    0.000000]   #32 [0001c68c00 - 0001c68c40]         BOOTMEM
[    0.000000]   #33 [0001c68c40 - 0001c68c80]         BOOTMEM
[    0.000000]   #34 [0001c68c80 - 0001c68c90]         BOOTMEM
[    0.000000]   #35 [0001c68cc0 - 0001c68cd0]         BOOTMEM
[    0.000000]   #36 [0001c68d00 - 0001c68d88]         BOOTMEM
[    0.000000]   #37 [0001c68dc0 - 0001c68e48]         BOOTMEM
[    0.000000]   #38 [0002000000 - 000200e000]         BOOTMEM
[    0.000000]   #39 [0002200000 - 000220e000]         BOOTMEM
[    0.000000]   #40 [0001c6ae80 - 0001c6ae84]         BOOTMEM
[    0.000000]   #41 [0001c6aec0 - 0001c6aec4]         BOOTMEM
[    0.000000]   #42 [0001c6af00 - 0001c6af08]         BOOTMEM
[    0.000000]   #43 [0001c6af40 - 0001c6af48]         BOOTMEM
[    0.000000]   #44 [0001c6af80 - 0001c6b028]         BOOTMEM
[    0.000000]   #45 [0001c6b040 - 0001c6b0a8]         BOOTMEM
[    0.000000]   #46 [0001c6b0c0 - 0001c6f0c0]         BOOTMEM
[    0.000000]   #47 [0001c6f0c0 - 0001cef0c0]         BOOTMEM
[    0.000000]   #48 [0001cef0c0 - 0001d2f0c0]         BOOTMEM
[    0.000000]   #49 [000220e000 - 00026f80ac]         BOOTMEM
[    0.000000] Initializing HighMem for node 0 (000377fe:0003ee70)
[    0.000000] Memory: 996100k/1030592k available (4927k kernel code, 34036k reserved, 2337k data, 684k init, 121288k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc0819000 - 0xc08c4000   ( 684 kB)
[    0.000000]       .data : 0xc05cfe4e - 0xc08185e8   (2337 kB)
[    0.000000]       .text : 0xc0100000 - 0xc05cfe4e   (4927 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU-based detection of stalled CPUs is disabled.
[    0.000000] 	Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:512
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1795.822 MHz processor.
[    0.004005] Calibrating delay loop (skipped), value calculated using timer frequency.. 3591.64 BogoMIPS (lpj=7183288)
[    0.004013] pid_max: default: 32768 minimum: 301
[    0.004040] Security Framework initialized
[    0.004070] AppArmor: AppArmor initialized
[    0.004073] Yama: becoming mindful.
[    0.004154] Mount-cache hash table entries: 512
[    0.004326] Initializing cgroup subsys ns
[    0.004332] Initializing cgroup subsys cpuacct
[    0.004339] Initializing cgroup subsys memory
[    0.004351] Initializing cgroup subsys devices
[    0.004355] Initializing cgroup subsys freezer
[    0.004359] Initializing cgroup subsys net_cls
[    0.004390] CPU: Physical Processor ID: 0
[    0.004393] CPU: Processor Core ID: 0
[    0.004399] mce: CPU supports 5 MCE banks
[    0.004412] using C1E aware idle routine
[    0.004422] Performance Events: AMD PMU driver.
[    0.004432] ... version:                0
[    0.004435] ... bit width:              48
[    0.004438] ... generic registers:      4
[    0.004442] ... value mask:             0000ffffffffffff
[    0.004445] ... max period:             00007fffffffffff
[    0.004449] ... fixed-purpose events:   0
[    0.004452] ... event mask:             000000000000000f
[    0.007779] ACPI: Core revision 20100428
[    0.020012] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.020021] ftrace: allocating 21754 entries in 43 pages
[    0.024091] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.024443] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.028000] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[    0.028000] ...trying to set up timer (IRQ0) through the 8259A ...
[    0.028000] ..... (found apic 0 pin 0) ...
[    0.068206] ....... works.
[    0.068208] CPU0: AMD Athlon(tm) 64 X2 Dual-Core Processor TK-55 stepping 01
[    0.072000] Booting Node   0, Processors  #1 Ok.
[    0.008000] Initializing CPU#1
[    0.156072] Brought up 2 CPUs
[    0.156076] Total of 2 processors activated (7183.01 BogoMIPS).
[    0.156070] System has AMD C1E enabled
[    0.156119] Switch to broadcast mode on CPU1
[    0.156325] Switch to broadcast mode on CPU0
[    0.156325] devtmpfs: initialized
[    0.157222] regulator: core version 0.5
[    0.157257] Time: 18:29:23  Date: 10/28/10
[    0.157313] NET: Registered protocol family 16
[    0.157327] Trying to unpack rootfs image as initramfs...
[    0.157475] EISA bus registered
[    0.157482] node 0 link 0: io port [1000, fffff]
[    0.157486] TOM: 0000000040000000 aka 1024M
[    0.157491] node 0 link 0: mmio [d8000000, dfffffff]
[    0.157495] node 0 link 0: mmio [d4000000, d7ffffff]
[    0.157499] node 0 link 0: mmio [a0000, bffff]
[    0.157503] node 0 link 0: mmio [f0000000, ffffffff]
[    0.157506] node 0 link 0: mmio [e0000000, efffffff]
[    0.157510] node 0 link 0: mmio [40000000, d3ffffff]
[    0.157513] bus: [00, ff] on node 0 link 0
[    0.157517] bus: 00 index 0 [io  0x0000-0xffff]
[    0.157521] bus: 00 index 1 [mem 0x40000000-0xefffffff]
[    0.157524] bus: 00 index 2 [mem 0x000a0000-0x000bffff]
[    0.157526] bus: 00 index 3 [mem 0xf0000000-0xffffffff]
[    0.157537] ACPI: bus type pci registered
[    0.157625] PCI: MMCONFIG for domain 0000 [bus 00-09] at [mem 0xe0000000-0xe09fffff] (base 0xe0000000)
[    0.157629] PCI: MMCONFIG at [mem 0xe0000000-0xe09fffff] reserved in E820
[    0.157632] PCI: Using MMCONFIG for extended config space
[    0.157634] PCI: Using configuration type 1 for base access
[    0.158742] bio: create slab <bio-0> at 0
[    0.158742] ACPI: EC: Look up EC in DSDT
[    0.159961] ACPI: BIOS _OSI(Linux) query ignored
[    0.168100] ACPI: Interpreter enabled
[    0.168104] ACPI: (supports S0 S3 S4 S5)
[    0.168126] ACPI: Using IOAPIC for interrupt routing
[    0.170375] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[    0.176253] ACPI: EC: GPE = 0x14, I/O: command/status = 0x66, data = 0x62
[    0.176516] ACPI: No dock devices found.
[    0.176520] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.177618] ACPI Error: Needed type [Reference], found [Device] f701af90 (20100428/exresop-104)
[    0.177627] ACPI Exception: AE_AML_OPERAND_TYPE, While resolving operands for [OpcodeName unavailable] (20100428/dswexec-445)
[    0.177635] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7022dc8), AE_AML_OPERAND_TYPE
[    0.177663] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.178699] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.178699] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d1fff] (ignored)
[    0.178699] pci_root PNP0A08:00: host bridge window [mem 0x000d2000-0x000d3fff] (ignored)
[    0.178699] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d5fff] (ignored)
[    0.178699] pci_root PNP0A08:00: host bridge window [mem 0x000d6000-0x000d7fff] (ignored)
[    0.178699] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000d9fff] (ignored)
[    0.178699] pci_root PNP0A08:00: host bridge window [mem 0x000da000-0x000dbfff] (ignored)
[    0.178699] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000ddfff] (ignored)
[    0.178699] pci_root PNP0A08:00: host bridge window [mem 0x000de000-0x000dffff] (ignored)
[    0.178699] pci_root PNP0A08:00: host bridge window [mem 0x000e0000-0x000e1fff] (ignored)
[    0.178699] pci_root PNP0A08:00: host bridge window [mem 0x000e2000-0x000e3fff] (ignored)
[    0.178699] pci_root PNP0A08:00: host bridge window [mem 0x40000000-0xffffffff] (ignored)
[    0.178699] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.178699] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.178699] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
[    0.178699] pci 0000:00:05.0: PME# disabled
[    0.178699] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.178699] pci 0000:00:06.0: PME# disabled
[    0.178699] pci 0000:00:12.0: reg 10: [io  0x8438-0x843f]
[    0.178699] pci 0000:00:12.0: reg 14: [io  0x8454-0x8457]
[    0.178699] pci 0000:00:12.0: reg 18: [io  0x8430-0x8437]
[    0.178699] pci 0000:00:12.0: reg 1c: [io  0x8450-0x8453]
[    0.178699] pci 0000:00:12.0: reg 20: [io  0x8400-0x840f]
[    0.178699] pci 0000:00:12.0: reg 24: [mem 0xd0004000-0xd00043ff]
[    0.178699] pci 0000:00:12.0: set SATA to AHCI mode
[    0.178699] pci 0000:00:13.0: reg 10: [mem 0xd0005000-0xd0005fff]
[    0.178699] pci 0000:00:13.1: reg 10: [mem 0xd0006000-0xd0006fff]
[    0.178699] pci 0000:00:13.2: reg 10: [mem 0xd0007000-0xd0007fff]
[    0.178699] pci 0000:00:13.3: reg 10: [mem 0xd0008000-0xd0008fff]
[    0.178699] pci 0000:00:13.4: reg 10: [mem 0xd0009000-0xd0009fff]
[    0.178699] pci 0000:00:13.5: reg 10: [mem 0xd0004400-0xd00044ff]
[    0.178699] pci 0000:00:13.5: supports D1 D2
[    0.178699] pci 0000:00:13.5: PME# supported from D0 D1 D2 D3hot
[    0.178699] pci 0000:00:13.5: PME# disabled
[    0.178699] pci 0000:00:14.0: reg 10: [io  0x8410-0x841f]
[    0.178699] pci 0000:00:14.1: reg 10: [io  0x01f0-0x01f7]
[    0.178699] pci 0000:00:14.1: reg 14: [io  0x03f4-0x03f7]
[    0.178699] pci 0000:00:14.1: reg 18: [io  0x0000-0x0007]
[    0.178699] pci 0000:00:14.1: reg 1c: [io  0x0000-0x0003]
[    0.178699] pci 0000:00:14.1: reg 20: [io  0x8420-0x842f]
[    0.178699] pci 0000:00:14.2: reg 10: [mem 0xd0000000-0xd0003fff 64bit]
[    0.178699] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.178699] pci 0000:00:14.2: PME# disabled
[    0.178699] PCI: peer root bus 00 res updated from pci conf
[    0.178699] pci 0000:01:05.0: reg 10: [mem 0xd4000000-0xd7ffffff pref]
[    0.178699] pci 0000:01:05.0: reg 14: [io  0x9000-0x90ff]
[    0.178699] pci 0000:01:05.0: reg 18: [mem 0xd0100000-0xd010ffff]
[    0.178699] pci 0000:01:05.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.178699] pci 0000:01:05.0: supports D1 D2
[    0.178699] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.178699] pci 0000:00:01.0:   bridge window [io  0x9000-0x9fff]
[    0.178699] pci 0000:00:01.0:   bridge window [mem 0xd0100000-0xd01fffff]
[    0.178699] pci 0000:00:01.0:   bridge window [mem 0xd4000000-0xd7ffffff 64bit pref]
[    0.178699] pci 0000:00:05.0: PCI bridge to [bus 02-04]
[    0.178699] pci 0000:00:05.0:   bridge window [io  0x0000-0x0000] (disabled)
[    0.178699] pci 0000:00:05.0:   bridge window [mem 0x00000000-0x000fffff] (disabled)
[    0.178699] pci 0000:00:05.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.178699] pci 0000:05:00.0: reg 10: [mem 0xd0200000-0xd0203fff]
[    0.178699] pci 0000:05:00.0: supports D1 D2
[    0.178699] pci 0000:05:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.178699] pci 0000:00:06.0: PCI bridge to [bus 05-07]
[    0.178699] pci 0000:00:06.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.178699] pci 0000:00:06.0:   bridge window [mem 0xd0200000-0xd02fffff]
[    0.178699] pci 0000:00:06.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.178699] pci 0000:08:00.0: reg 10: [mem 0xd0300000-0xd0301fff]
[    0.178699] pci 0000:08:00.0: supports D1 D2
[    0.178699] pci 0000:08:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.178699] pci 0000:08:00.0: PME# disabled
[    0.178706] pci 0000:08:01.0: reg 10: [mem 0xd0302800-0xd03028ff]
[    0.178776] pci 0000:08:01.0: supports D1 D2
[    0.178778] pci 0000:08:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.178785] pci 0000:08:01.0: PME# disabled
[    0.178828] pci 0000:08:01.1: reg 10: [mem 0xd0302c00-0xd0302cff]
[    0.178898] pci 0000:08:01.1: supports D1 D2
[    0.178901] pci 0000:08:01.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.178907] pci 0000:08:01.1: PME# disabled
[    0.178983] pci 0000:00:14.4: PCI bridge to [bus 08-0a] (subtractive decode)
[    0.178992] pci 0000:00:14.4:   bridge window [io  0xf000-0x0000] (disabled)
[    0.178998] pci 0000:00:14.4:   bridge window [mem 0xd0300000-0xd03fffff]
[    0.179004] pci 0000:00:14.4:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.179008] pci 0000:00:14.4:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.179011] pci 0000:00:14.4:   bridge window [mem 0x40000000-0xefffffff] (subtractive decode)
[    0.179015] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.179019] pci 0000:00:14.4:   bridge window [mem 0xf0000000-0xffffffff] (subtractive decode)
[    0.179034] pci_bus 0000:00: on NUMA node 0
[    0.179039] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.179167] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB5_._PRT]
[    0.179244] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB6_._PRT]
[    0.179362] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.179429] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.179561] ACPI Error: Needed type [Reference], found [Device] f701af90 (20100428/exresop-104)
[    0.179567] ACPI Exception: AE_AML_OPERAND_TYPE, While resolving operands for [OpcodeName unavailable] (20100428/dswexec-445)
[    0.179575] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7022dc8), AE_AML_OPERAND_TYPE
[    0.184403] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[    0.184513] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[    0.184620] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[    0.184727] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[    0.184835] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[    0.184942] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[    0.185049] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[    0.185157] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[    0.185265] ACPI: PCI Interrupt Link [LNKU] (IRQs 3 4 5 7) *0, disabled.
[    0.185304] HEST: Table is not found!
[    0.185423] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
[    0.185429] vgaarb: loaded
[    0.185629] SCSI subsystem initialized
[    0.188000] libata version 3.00 loaded.
[    0.188000] usbcore: registered new interface driver usbfs
[    0.188000] usbcore: registered new interface driver hub
[    0.188000] usbcore: registered new device driver usb
[    0.188000] ACPI: WMI: Mapper loaded
[    0.188000] PCI: Using ACPI for IRQ routing
[    0.188000] PCI: pci_cache_line_size set to 64 bytes
[    0.188000] reserve RAM buffer: 0000000000002000 - 000000000000ffff 
[    0.188000] reserve RAM buffer: 000000000009dc00 - 000000000009ffff 
[    0.188000] reserve RAM buffer: 000000003ee70000 - 000000003fffffff 
[    0.188000] NetLabel: Initializing
[    0.188000] NetLabel:  domain hash size = 128
[    0.188000] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.188000] NetLabel:  unlabeled traffic allowed by default
[    0.198309] AppArmor: AppArmor Filesystem Enabled
[    0.198330] pnp: PnP ACPI init
[    0.198350] ACPI: bus type pnp registered
[    0.200940] pnp 00:09: disabling [mem 0x00000000-0x00000fff] because it overlaps 0000:01:05.0 BAR 6 [mem 0x00000000-0x0001ffff pref]
[    0.204082] pnp: PnP ACPI: found 10 devices
[    0.204084] ACPI: ACPI bus type pnp unregistered
[    0.204088] PnPBIOS: Disabled by ACPI PNP
[    0.204102] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    0.204106] system 00:01: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.204110] system 00:01: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.204119] system 00:08: [io  0x1080] has been reserved
[    0.204123] system 00:08: [io  0x0220-0x022f] has been reserved
[    0.204126] system 00:08: [io  0x040b] has been reserved
[    0.204130] system 00:08: [io  0x04d0-0x04d1] has been reserved
[    0.204133] system 00:08: [io  0x04d6] has been reserved
[    0.204137] system 00:08: [io  0x0530-0x0537] has been reserved
[    0.204140] system 00:08: [io  0x0c00-0x0c01] has been reserved
[    0.204144] system 00:08: [io  0x0c14] has been reserved
[    0.204147] system 00:08: [io  0x0c50-0x0c52] has been reserved
[    0.204150] system 00:08: [io  0x0c6c] has been reserved
[    0.204154] system 00:08: [io  0x0c6f] has been reserved
[    0.204157] system 00:08: [io  0x0cd0-0x0cd3] has been reserved
[    0.204161] system 00:08: [io  0x0cd4-0x0cd5] has been reserved
[    0.204164] system 00:08: [io  0x0cd6-0x0cd7] has been reserved
[    0.204168] system 00:08: [io  0x0cd8-0x0cdf] has been reserved
[    0.204171] system 00:08: [io  0x8000-0x805f] has been reserved
[    0.204175] system 00:08: [io  0x8100-0x81ff window] has been reserved
[    0.204179] system 00:08: [io  0x8200-0x82ff window] has been reserved
[    0.204183] system 00:08: [io  0x0f40-0x0f47] has been reserved
[    0.204186] system 00:08: [io  0x087f] has been reserved
[    0.204193] system 00:09: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.204197] system 00:09: [mem 0xfff00000-0xffffffff] could not be reserved
[    0.204200] system 00:09: [mem 0xc0004800-0xc0004bff] has been reserved
[    0.204204] system 00:09: [mem 0xfed00000-0xfed003ff] has been reserved
[    0.237787] Switching to clocksource acpi_pm
[    2.853226] pci 0000:00:05.0: BAR 14: assigned [mem 0x40000000-0x401fffff]
[    2.853231] pci 0000:00:05.0: BAR 15: assigned [mem 0x40200000-0x403fffff 64bit pref]
[    2.853235] pci 0000:00:06.0: BAR 15: assigned [mem 0x40400000-0x405fffff 64bit pref]
[    2.853241] pci 0000:00:05.0: BAR 13: assigned [io  0x2000-0x2fff]
[    2.853245] pci 0000:00:06.0: BAR 13: assigned [io  0x3000-0x3fff]
[    2.853249] pci 0000:01:05.0: BAR 6: assigned [mem 0xd0120000-0xd013ffff pref]
[    2.853254] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    2.853257] pci 0000:00:01.0:   bridge window [io  0x9000-0x9fff]
[    2.853262] pci 0000:00:01.0:   bridge window [mem 0xd0100000-0xd01fffff]
[    2.853266] pci 0000:00:01.0:   bridge window [mem 0xd4000000-0xd7ffffff 64bit pref]
[    2.853271] pci 0000:00:05.0: PCI bridge to [bus 02-04]
[    2.853274] pci 0000:00:05.0:   bridge window [io  0x2000-0x2fff]
[    2.853279] pci 0000:00:05.0:   bridge window [mem 0x40000000-0x401fffff]
[    2.853283] pci 0000:00:05.0:   bridge window [mem 0x40200000-0x403fffff 64bit pref]
[    2.853288] pci 0000:00:06.0: PCI bridge to [bus 05-07]
[    2.853291] pci 0000:00:06.0:   bridge window [io  0x3000-0x3fff]
[    2.853295] pci 0000:00:06.0:   bridge window [mem 0xd0200000-0xd02fffff]
[    2.853300] pci 0000:00:06.0:   bridge window [mem 0x40400000-0x405fffff 64bit pref]
[    2.853305] pci 0000:00:14.4: PCI bridge to [bus 08-0a]
[    2.853307] pci 0000:00:14.4:   bridge window [io  disabled]
[    2.853315] pci 0000:00:14.4:   bridge window [mem 0xd0300000-0xd03fffff]
[    2.853320] pci 0000:00:14.4:   bridge window [mem pref disabled]
[    2.853342] pci 0000:00:05.0: enabling device (0000 -> 0003)
[    2.853346] pci 0000:00:05.0: setting latency timer to 64
[    2.853354] pci 0000:00:06.0: setting latency timer to 64
[    2.853364] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
[    2.853367] pci_bus 0000:00: resource 5 [mem 0x40000000-0xefffffff]
[    2.853370] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    2.853374] pci_bus 0000:00: resource 7 [mem 0xf0000000-0xffffffff]
[    2.853377] pci_bus 0000:01: resource 0 [io  0x9000-0x9fff]
[    2.853380] pci_bus 0000:01: resource 1 [mem 0xd0100000-0xd01fffff]
[    2.853384] pci_bus 0000:01: resource 2 [mem 0xd4000000-0xd7ffffff 64bit pref]
[    2.853387] pci_bus 0000:02: resource 0 [io  0x2000-0x2fff]
[    2.853390] pci_bus 0000:02: resource 1 [mem 0x40000000-0x401fffff]
[    2.853394] pci_bus 0000:02: resource 2 [mem 0x40200000-0x403fffff 64bit pref]
[    2.853397] pci_bus 0000:05: resource 0 [io  0x3000-0x3fff]
[    2.853400] pci_bus 0000:05: resource 1 [mem 0xd0200000-0xd02fffff]
[    2.853404] pci_bus 0000:05: resource 2 [mem 0x40400000-0x405fffff 64bit pref]
[    2.853407] pci_bus 0000:08: resource 1 [mem 0xd0300000-0xd03fffff]
[    2.853410] pci_bus 0000:08: resource 4 [io  0x0000-0xffff]
[    2.853414] pci_bus 0000:08: resource 5 [mem 0x40000000-0xefffffff]
[    2.853417] pci_bus 0000:08: resource 6 [mem 0x000a0000-0x000bffff]
[    2.853420] pci_bus 0000:08: resource 7 [mem 0xf0000000-0xffffffff]
[    2.853477] NET: Registered protocol family 2
[    2.853561] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    2.853925] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    2.854811] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    2.855243] TCP: Hash tables configured (established 131072 bind 65536)
[    2.855248] TCP reno registered
[    2.855254] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    2.855272] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    2.855398] NET: Registered protocol family 1
[    2.855413] pci 0000:00:00.0: MSI quirk detected; MSI disabled
[    2.855422] pci 0000:00:01.0: MSI quirk detected; subordinate MSI disabled
[    2.855548] pci 0000:01:05.0: Boot video device
[    2.855566] PCI: CLS 32 bytes, default 64
[    2.855849] cpufreq-nforce2: No nForce2 chipset.
[    2.855886] Scanning for low memory corruption every 60 seconds
[    2.858982] audit: initializing netlink socket (disabled)
[    2.858997] type=2000 audit(1288290563.856:1): initialized
[    2.871768] highmem bounce pool size: 64 pages
[    2.871775] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    2.873469] VFS: Disk quotas dquot_6.5.2
[    2.873552] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    2.874259] fuse init (API version 7.14)
[    2.874369] msgmni has been set to 1708
[    2.882230] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    2.882236] io scheduler noop registered
[    2.882239] io scheduler deadline registered
[    2.882258] io scheduler cfq registered (default)
[    2.882419] pcieport 0000:00:05.0: setting latency timer to 64
[    2.882443] pcieport 0000:00:06.0: setting latency timer to 64
[    2.882486] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    2.882515] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    2.883253] ACPI: AC Adapter [ACAD] (on-line)
[    2.883323] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    2.883330] ACPI: Power Button [PWRB]
[    2.883393] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    2.883398] ACPI: Sleep Button [SLPB]
[    2.883446] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input2
[    2.884119] ACPI: Lid Switch [LID]
[    2.884169] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    2.884173] ACPI: Power Button [PWRF]
[    2.884353] ACPI: acpi_idle registered with cpuidle
[    2.884421] ACPI: processor limited to max C-state 1
[    2.889307] thermal LNXTHERM:01: registered as thermal_zone0
[    2.889316] ACPI: Thermal Zone [THRM] (66 C)
[    2.889403] ERST: Table is not found!
[    2.889621] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    2.891205] brd: module loaded
[    2.891814] loop: module loaded
[    2.892159]   alloc irq_desc for 16 on node -1
[    2.892163]   alloc kstat_irqs on node -1
[    2.892175] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.892233] pata_acpi 0000:00:14.1: setting latency timer to 64
[    2.892647] Fixed MDIO Bus: probed
[    2.892690] PPP generic driver version 2.4.2
[    2.892742] tun: Universal TUN/TAP device driver, 1.6
[    2.892744] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    2.892847] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.892870]   alloc irq_desc for 19 on node -1
[    2.892872]   alloc kstat_irqs on node -1
[    2.892878] ehci_hcd 0000:00:13.5: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    2.892907] ehci_hcd 0000:00:13.5: EHCI Host Controller
[    2.892952] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 1
[    2.892985] ehci_hcd 0000:00:13.5: applying AMD SB600/SB700 USB freeze workaround
[    2.893073] ehci_hcd 0000:00:13.5: debug port 1
[    2.893107] ehci_hcd 0000:00:13.5: irq 19, io mem 0xd0004400
[    2.893298] isapnp: Scanning for PnP cards...
[    2.942571] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00
[    2.942760] hub 1-0:1.0: USB hub found
[    2.942767] hub 1-0:1.0: 10 ports detected
[    2.942880] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.942900] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.942921] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    2.942993] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[    2.943025] ohci_hcd 0000:00:13.0: irq 16, io mem 0xd0005000
[    3.030475] hub 2-0:1.0: USB hub found
[    3.030483] hub 2-0:1.0: 2 ports detected
[    3.030550]   alloc irq_desc for 17 on node -1
[    3.030553]   alloc kstat_irqs on node -1
[    3.030560] ohci_hcd 0000:00:13.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    3.030575] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    3.030612] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[    3.030639] ohci_hcd 0000:00:13.1: irq 17, io mem 0xd0006000
[    3.118115] hub 3-0:1.0: USB hub found
[    3.118123] hub 3-0:1.0: 2 ports detected
[    3.118189]   alloc irq_desc for 18 on node -1
[    3.118191]   alloc kstat_irqs on node -1
[    3.118197] ohci_hcd 0000:00:13.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.118211] ohci_hcd 0000:00:13.2: OHCI Host Controller
[    3.118249] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 4
[    3.118277] ohci_hcd 0000:00:13.2: irq 18, io mem 0xd0007000
[    3.205277] hub 4-0:1.0: USB hub found
[    3.205286] hub 4-0:1.0: 2 ports detected
[    3.205354] ohci_hcd 0000:00:13.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    3.205368] ohci_hcd 0000:00:13.3: OHCI Host Controller
[    3.205405] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 5
[    3.205422] ohci_hcd 0000:00:13.3: irq 17, io mem 0xd0008000
[    3.249143] isapnp: No Plug & Play device found
[    3.261250] hub 5-0:1.0: USB hub found
[    3.261260] hub 5-0:1.0: 2 ports detected
[    3.261349] ohci_hcd 0000:00:13.4: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.261373] ohci_hcd 0000:00:13.4: OHCI Host Controller
[    3.261464] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 6
[    3.261489] ohci_hcd 0000:00:13.4: irq 18, io mem 0xd0009000
[    3.266901] Freeing initrd memory: 11132k freed
[    3.316255] hub 6-0:1.0: USB hub found
[    3.316265] hub 6-0:1.0: 2 ports detected
[    3.316355] uhci_hcd: USB Universal Host Controller Interface driver
[    3.316460] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    3.326657] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.326668] serio: i8042 AUX port at 0x60,0x64 irq 12
[    3.326806] mice: PS/2 mouse device common for all mice
[    3.326994] rtc_cmos 00:04: RTC can wake from S4
[    3.327043] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    3.327073] rtc0: alarms up to one month, 114 bytes nvram
[    3.327213] device-mapper: uevent: version 1.0.3
[    3.327424] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    3.327616] device-mapper: multipath: version 1.1.1 loaded
[    3.327620] device-mapper: multipath round-robin: version 1.0.0 loaded
[    3.327802] EISA: Probing bus 0 at eisa.0
[    3.327805] EISA: Cannot allocate resource for mainboard
[    3.327808] Cannot allocate resource for EISA slot 1
[    3.327811] Cannot allocate resource for EISA slot 2
[    3.327813] Cannot allocate resource for EISA slot 3
[    3.327816] Cannot allocate resource for EISA slot 4
[    3.327819] Cannot allocate resource for EISA slot 5
[    3.327822] Cannot allocate resource for EISA slot 6
[    3.327824] Cannot allocate resource for EISA slot 7
[    3.327827] Cannot allocate resource for EISA slot 8
[    3.327830] EISA: Detected 0 cards.
[    3.328055] cpuidle: using governor ladder
[    3.328058] cpuidle: using governor menu
[    3.328414] TCP cubic registered
[    3.328568] NET: Registered protocol family 10
[    3.328988] lo: Disabled Privacy Extensions
[    3.329283] NET: Registered protocol family 17
[    3.329329] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual-Core Processor TK-55 (2 cpu cores) (version 2.20.00)
[    3.329382] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x13
[    3.329386] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0x14
[    3.329389] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x1a
[    3.329470] Using IPI No-Shortcut mode
[    3.329575] PM: Resume from disk failed.
[    3.329590] registered taskstats version 1
[    3.329862]   Magic number: 14:963:494
[    3.329974] rtc_cmos 00:04: setting system clock to 2010-10-28 18:29:26 UTC (1288290566)
[    3.329978] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.329980] EDD information not available.
[    3.330077] Freeing unused kernel memory: 684k freed
[    3.330649] Write protecting the kernel text: 4928k
[    3.330697] Write protecting the kernel read-only data: 1980k
[    3.358520] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    3.361865] udev[81]: starting version 162
[    3.429145] usb 1-7: new high speed USB device using ehci_hcd and address 4
[    3.458462] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[    3.462786] acpi device:1c: registered as cooling_device2
[    3.462917] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1a/LNXVIDEO:00/input/input5
[    3.463217] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[    3.576679] Initializing USB Mass Storage driver...
[    3.576869] scsi0 : usb-storage 1-7:1.0
[    3.577105] usbcore: registered new interface driver usb-storage
[    3.577108] USB Mass Storage support registered.
[    3.637258] ACPI: Battery Slot [BAT1] (battery present)
[    3.642645] Btrfs loaded
[    3.649992] xor: automatically using best checksumming function: pIII_sse
[    3.668015]    pIII_sse  :  5446.000 MB/sec
[    3.668018] xor: using function: pIII_sse (5446.000 MB/sec)
[    3.671458] device-mapper: dm-raid45: initialized v0.2594b
[    3.828063] usb 2-1: new low speed USB device using ohci_hcd and address 2
[    4.086904] usbcore: registered new interface driver hiddev
[    4.095121] input: Logitech Optical USB Mouse as /devices/pci0000:00/0000:00:13.0/usb2/2-1/2-1:1.0/input/input6
[    4.095354] generic-usb 0003:046D:C016.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:13.0-1/input0
[    4.095620] usbcore: registered new interface driver usbhid
[    4.095623] usbhid: USB HID core driver
[    4.100135] scsi1 : pata_atiixp
[    4.104453] sdhci: Secure Digital Host Controller Interface driver
[    4.104458] sdhci: Copyright(c) Pierre Ossman
[    4.108024] sdhci-pci 0000:08:01.0: SDHCI controller found [1180:0822] (rev 19)
[    4.108049]   alloc irq_desc for 20 on node -1
[    4.108051]   alloc kstat_irqs on node -1
[    4.108061] sdhci-pci 0000:08:01.0: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    4.109099] sdhci-pci 0000:08:01.0: Will use DMA mode even though HW doesn't fully claim to support it.
[    4.110052] Linux agpgart interface v0.103
[    4.112023] Registered led device: mmc0::
[    4.112710] b43-pci-bridge 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    4.112723] b43-pci-bridge 0000:05:00.0: setting latency timer to 64
[    4.112752] scsi2 : pata_atiixp
[    4.113565] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x8420 irq 14
[    4.113569] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x8428 irq 15
[    4.116629] ahci 0000:00:12.0: version 3.0
[    4.116653]   alloc irq_desc for 22 on node -1
[    4.116656]   alloc kstat_irqs on node -1
[    4.116665] ahci 0000:00:12.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    4.116712] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit
[    4.116819] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    4.116824] ahci 0000:00:12.0: flags: ncq sntf ilck pm led clo pmp pio slum part ccc 
[    4.117605] scsi3 : ahci
[    4.117816] mmc0: SDHCI controller on PCI [0000:08:01.0] using DMA
[    4.117955] scsi4 : ahci
[    4.118129] scsi5 : ahci
[    4.118248] scsi6 : ahci
[    4.118388] ata3: SATA max UDMA/133 abar m1024@0xd0004000 port 0xd0004100 irq 22
[    4.118394] ata4: SATA max UDMA/133 abar m1024@0xd0004000 port 0xd0004180 irq 22
[    4.118399] ata5: SATA max UDMA/133 abar m1024@0xd0004000 port 0xd0004200 irq 22
[    4.118403] ata6: SATA max UDMA/133 abar m1024@0xd0004000 port 0xd0004280 irq 22
[    4.132076] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x11, vendor 0x4243)
[    4.132087] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0A, vendor 0x4243)
[    4.132096] ssb: Core 2 found: USB 1.1 Host (cc 0x817, rev 0x03, vendor 0x4243)
[    4.132104] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x01, vendor 0x4243)
[    4.143507] [drm] Initialized drm 1.1.0 20060810
[    4.173386] ssb: Sonics Silicon Backplane found on PCI device 0000:05:00.0
[    4.177635]   alloc irq_desc for 21 on node -1
[    4.177640]   alloc kstat_irqs on node -1
[    4.177649] b44 0000:08:00.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    4.196077] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243)
[    4.196086] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243)
[    4.196094] ssb: Core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243)
[    4.236104] ssb: Sonics Silicon Backplane found on PCI device 0000:08:00.0
[    4.236128] b44: b44.c:v2.0
[    4.256944] b44 ssb1:0: eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:1c:23:9a:bc:f5
[    4.260058] usb 3-1: new low speed USB device using ohci_hcd and address 2
[    4.300579] ata1.00: ATAPI: TSSTcorp DVD+/-RW TS-L632H, D200, max UDMA/33
[    4.332526] ata1.00: configured for UDMA/33
[    4.338049] scsi 1:0:0:0: CD-ROM            TSSTcorp DVD+-RW TS-L632H D200 PQ: 0 ANSI: 5
[    4.352818] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    4.352823] Uniform CD-ROM driver Revision: 3.20
[    4.352967] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.353072] sr 1:0:0:0: Attached scsi generic sg0 type 5
[    4.436085] ata5: SATA link down (SStatus 0 SControl 300)
[    4.436112] ata4: SATA link down (SStatus 0 SControl 300)
[    4.436131] ata6: SATA link down (SStatus 0 SControl 300)
[    4.458676] input: Microsoft Microsoft® Digital Media Keyboard 3000 as /devices/pci0000:00/0000:00:13.1/usb3/3-1/3-1:1.0/input/input7
[    4.458806] generic-usb 0003:045E:0730.0002: input,hidraw1: USB HID v1.11 Keyboard [Microsoft Microsoft® Digital Media Keyboard 3000] on usb-0000:00:13.1-1/input0
[    4.477242] input: Microsoft Microsoft® Digital Media Keyboard 3000 as /devices/pci0000:00/0000:00:13.1/usb3/3-1/3-1:1.1/input/input8
[    4.477370] generic-usb 0003:045E:0730.0003: input,hidraw2: USB HID v1.11 Device [Microsoft Microsoft® Digital Media Keyboard 3000] on usb-0000:00:13.1-1/input1
[    4.577055] scsi 0:0:0:0: Direct-Access                               0.00 PQ: 0 ANSI: 2
[    4.577901] sd 0:0:0:0: Attached scsi generic sg1 type 0
[    4.579032] sd 0:0:0:0: [sda] 15794176 512-byte logical blocks: (8.08 GB/7.53 GiB)
[    4.579779] sd 0:0:0:0: [sda] Write Protect is off
[    4.579785] sd 0:0:0:0: [sda] Mode Sense: 00 00 00 00
[    4.579789] sd 0:0:0:0: [sda] Assuming drive cache: write through
[    4.583649] sd 0:0:0:0: [sda] Assuming drive cache: write through
[    4.583659]  sda:
[    4.600049] ata3: softreset failed (device not ready)
[    4.600053] ata3: applying SB600 PMP SRST workaround and retrying
[    4.738321]  sda1
[    4.741571] sd 0:0:0:0: [sda] Assuming drive cache: write through
[    4.741579] sd 0:0:0:0: [sda] Attached SCSI removable disk
[    4.764068] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    5.109795] ata3.00: ATA-8: WDC WD1600BEVS-00VAT0, 11.01A11, max UDMA/133
[    5.109801] ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    5.109827] ata3.00: SB600 AHCI: limiting to 255 sectors per cmd
[    5.111231] ata3.00: SB600 AHCI: limiting to 255 sectors per cmd
[    5.111235] ata3.00: configured for UDMA/133
[    5.124211] scsi 3:0:0:0: Direct-Access     ATA      WDC WD1600BEVS-0 11.0 PQ: 0 ANSI: 5
[    5.124438] sd 3:0:0:0: Attached scsi generic sg2 type 0
[    5.124590] sd 3:0:0:0: [sdb] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    5.124762] sd 3:0:0:0: [sdb] Write Protect is off
[    5.124767] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    5.124835] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.125203]  sdb: sdb1 sdb4 < sdb5 >
[    5.161613] sd 3:0:0:0: [sdb] Attached SCSI disk
[    5.220059] [drm] radeon defaulting to kernel modesetting.
[    5.220064] [drm] radeon kernel modesetting enabled.
[    5.220171] radeon 0000:01:05.0: power state changed by ACPI to D0
[    5.220181] radeon 0000:01:05.0: power state changed by ACPI to D0
[    5.220192] radeon 0000:01:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    5.222336] [drm] initializing kernel modesetting (RS480 0x1002:0x5975).
[    5.222641] [drm] register mmio base: 0xD0100000
[    5.222644] [drm] register mmio size: 65536
[    5.222824] [drm:rs400_gart_adjust_size] *ERROR* Forcing to 32M GART size (because of ASIC bug ?)
[    5.222829] [drm] Generation 2 PCI interface, using max accessible memory
[    5.222835] radeon 0000:01:05.0: VRAM: 16M 0x3F000000 - 0x3FFFFFFF (16M used)
[    5.222839] radeon 0000:01:05.0: GTT: 32M 0x40000000 - 0x41FFFFFF
[    5.222874] [drm] radeon: irq initialized.
[    5.223044] [drm] Detected VRAM RAM=16M, BAR=64M
[    5.223050] [drm] RAM width 128bits DDR
[    5.223155] [TTM] Zone  kernel: Available graphics memory: 443314 kiB.
[    5.223158] [TTM] Zone highmem: Available graphics memory: 503958 kiB.
[    5.223161] [TTM] Initializing pool allocator.
[    5.223190] [drm] radeon: 16M of VRAM memory ready
[    5.223192] [drm] radeon: 32M of GTT memory ready.
[    5.223222] [drm] GART: num cpu pages 8192, num gpu pages 8192
[    5.223980] [drm] radeon: 1 quad pipes, 1 z pipes initialized.
[    5.224625] [drm] Loading R300 Microcode
[    5.227630] [drm] radeon: ring at 0x0000000040000000
[    5.227652] [drm] ring test succeeded in 0 usecs
[    5.227861] [drm] radeon: ib pool ready.
[    5.227933] [drm] ib test succeeded in 0 usecs
[    5.228085] [drm] Panel ID String: LPL                     
[    5.228088] [drm] Panel Size 1280x800
[    5.228146] [drm] Radeon Display Connectors
[    5.228148] [drm] Connector 0:
[    5.228150] [drm]   VGA
[    5.228153] [drm]   DDC: 0x68 0x68 0x68 0x68 0x68 0x68 0x68 0x68
[    5.228155] [drm]   Encoders:
[    5.228157] [drm]     CRT1: INTERNAL_DAC2
[    5.228159] [drm] Connector 1:
[    5.228161] [drm]   LVDS
[    5.228164] [drm]   DDC: 0x198 0x198 0x19c 0x19c 0x1a0 0x1a0 0x1a4 0x1a4
[    5.228166] [drm]   Encoders:
[    5.228168] [drm]     LCD1: INTERNAL_LVDS
[    5.282111] [drm] radeon: power management initialized
[    5.364353] composite sync not supported
[    5.366664] [drm] fb mappable at 0xD4040000
[    5.366666] [drm] vram apper at 0xD4000000
[    5.366668] [drm] size 1024000
[    5.366670] [drm] fb depth is 8
[    5.366672] [drm]    pitch is 1280
[    5.400638] Console: switching to colour frame buffer device 160x50
[    5.403164] fb0: radeondrmfb frame buffer device
[    5.403167] drm: registered panic notifier
[    5.403171] Slow work thread pool: Starting up
[    5.403310] Slow work thread pool: Ready
[    5.403318] [drm] Initialized radeon 2.5.0 20080528 for 0000:01:05.0 on minor 0
[    5.567620] aufs 2-standalone.tree-35-rcN-20100705
[    5.587093] squashfs: version 4.0 (2009/01/31) Phillip Lougher
[   16.966056] Adding 2952188k swap on /dev/sdb5.  Priority:-1 extents:1 across:2952188k 
[   17.045987] udev[1257]: starting version 162
[   17.411453] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.568484] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   17.602433] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   17.623878] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0x8410, revision 0
[   17.712871] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   17.901803] cfg80211: Calling CRDA to update world regulatory domain
[   17.937488] input: Dell WMI hotkeys as /devices/virtual/input/input9
[   18.003453] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[   18.135503] cfg80211: World regulatory domain updated:
[   18.135510]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   18.135515]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.135518]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   18.135522]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   18.135525]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.135529]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.232723] phy0: Selected rate control algorithm 'minstrel'
[   18.233569] Registered led device: b43-phy0::tx
[   18.233593] Registered led device: b43-phy0::rx
[   18.233616] Registered led device: b43-phy0::radio
[   18.233721] Broadcom 43xx driver loaded [ Features: PL, Firmware-ID: FW13 ]
[   18.301038] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x180b1, caps: 0xa04713/0x200000/0x0
[   18.336699] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input10
[   18.406214] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   18.485497] input: HDA ATI SB Mic at Ext Right Jack as /devices/pci0000:00/0000:00:14.2/sound/card0/input11
[   18.485604] input: HDA ATI SB HP Out at Ext Right Jack as /devices/pci0000:00/0000:00:14.2/sound/card0/input12
[   18.876124] lp: driver loaded but no devices found
[   18.918203] ppdev: user-space parallel port driver
[   20.104530] ata3.00: SB600 AHCI: limiting to 255 sectors per cmd
[   20.105977] ata3.00: SB600 AHCI: limiting to 255 sectors per cmd
[   20.105981] ata3.00: configured for UDMA/133
[   20.105988] ata3: EH complete
[   20.402046] composite sync not supported
[   20.431624] composite sync not supported
[   20.805218] b44 ssb1:0: eth0: Link is up at 100 Mbps, full duplex
[   20.805224] b44 ssb1:0: eth0: Flow control is off for TX and off for RX
[   20.805599] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   31.665010] eth0: no IPv6 routers present
[   81.156056] Clocksource tsc unstable (delta = -208887535 ns)
[ 1014.488275] composite sync not supported
[ 1014.512029] composite sync not supported
[ 1019.417269] kded4[4200] general protection ip:10b5714 sp:bffae7d0 error:0 in libQtCore.so.4.7.0[f3b000+290000]
[ 1217.703900] composite sync not supported
[ 1469.700882] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)

```

---

### Post by NightwishFan on 2010-10-29
You might have a Xorg.conf lying around there. Try removing it. The X in X11 is supposed to be capital. If it says no such file, that is also expected.
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

I can help more possibly but I am getting some sleep tonight. So if no-one else helps you out by next time I am on, I will work on this again.

---

### Post by Ubuntiac on 2010-10-29
Thanks NightWishFan,

I tried that and still get software rasteriser. Actually I only ever created xorg.conf to try and fix this problem in the first place.

Anyway here's the current Xorg.0.log without a xorg.conf:

```
[    16.794] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    16.794] X Protocol Version 11, Revision 0
[    16.794] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[    16.794] Current Operating System: Linux sheryls-joy 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:36:48 UTC 2010 i686
[    16.794] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=8db8c9fc-4067-45dd-8578-4c302b834b59 ro quiet splash nomodeset radeon.modeset=0 video=uvesafb:mode_option=1024x768-24,mtrr=3,scroll=ywrap
[    16.794] Build Date: 16 September 2010  05:39:22PM
[    16.794] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
[    16.794] Current version of pixman: 0.18.4
[    16.794] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    16.794] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    16.794] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Oct 29 15:21:00 2010
[    16.795] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    16.795] (==) No Layout section.  Using the first Screen section.
[    16.795] (==) No screen section available. Using defaults.
[    16.795] (**) |-->Screen "Default Screen Section" (0)
[    16.795] (**) |   |-->Monitor "<default monitor>"
[    16.796] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    16.796] (==) Automatically adding devices
[    16.796] (==) Automatically enabling devices
[    16.796] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    16.796] 	Entry deleted from font path.
[    16.796] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    16.796] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    16.796] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    16.796] (II) Loader magic: 0x81f8e00
[    16.796] (II) Module ABI versions:
[    16.796] 	X.Org ANSI C Emulation: 0.4
[    16.796] 	X.Org Video Driver: 8.0
[    16.796] 	X.Org XInput driver : 11.0
[    16.796] 	X.Org Server Extension : 4.0
[    16.797] (--) PCI:*(0:1:5:0) 1002:5975:1028:01f5 rev 0, Mem @ 0xd4000000/67108864, 0xd0100000/65536, I/O @ 0x00009000/256, BIOS @ 0x????????/131072
[    16.798] (II) Open ACPI successful (/var/run/acpid.socket)
[    16.798] (II) LoadModule: "extmod"
[    16.821] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    16.821] (II) Module extmod: vendor="X.Org Foundation"
[    16.821] 	compiled for 1.9.0, module version = 1.0.0
[    16.821] 	Module class: X.Org Server Extension
[    16.821] 	ABI class: X.Org Server Extension, version 4.0
[    16.821] (II) Loading extension MIT-SCREEN-SAVER
[    16.821] (II) Loading extension XFree86-VidModeExtension
[    16.821] (II) Loading extension XFree86-DGA
[    16.821] (II) Loading extension DPMS
[    16.821] (II) Loading extension XVideo
[    16.821] (II) Loading extension XVideo-MotionCompensation
[    16.821] (II) Loading extension X-Resource
[    16.821] (II) LoadModule: "dbe"
[    16.821] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    16.821] (II) Module dbe: vendor="X.Org Foundation"
[    16.821] 	compiled for 1.9.0, module version = 1.0.0
[    16.821] 	Module class: X.Org Server Extension
[    16.821] 	ABI class: X.Org Server Extension, version 4.0
[    16.821] (II) Loading extension DOUBLE-BUFFER
[    16.821] (II) LoadModule: "glx"
[    16.822] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    16.822] (II) Module glx: vendor="X.Org Foundation"
[    16.822] 	compiled for 1.9.0, module version = 1.0.0
[    16.822] 	ABI class: X.Org Server Extension, version 4.0
[    16.822] (==) AIGLX enabled
[    16.822] (II) Loading extension GLX
[    16.822] (II) LoadModule: "record"
[    16.822] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    16.823] (II) Module record: vendor="X.Org Foundation"
[    16.823] 	compiled for 1.9.0, module version = 1.13.0
[    16.823] 	Module class: X.Org Server Extension
[    16.823] 	ABI class: X.Org Server Extension, version 4.0
[    16.823] (II) Loading extension RECORD
[    16.823] (II) LoadModule: "dri"
[    16.823] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    16.823] (II) Module dri: vendor="X.Org Foundation"
[    16.823] 	compiled for 1.9.0, module version = 1.0.0
[    16.823] 	ABI class: X.Org Server Extension, version 4.0
[    16.823] (II) Loading extension XFree86-DRI
[    16.823] (II) LoadModule: "dri2"
[    16.824] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    16.824] (II) Module dri2: vendor="X.Org Foundation"
[    16.824] 	compiled for 1.9.0, module version = 1.2.0
[    16.824] 	ABI class: X.Org Server Extension, version 4.0
[    16.824] (II) Loading extension DRI2
[    16.824] (==) Matched ati as autoconfigured driver 0
[    16.824] (==) Matched vesa as autoconfigured driver 1
[    16.824] (==) Matched fbdev as autoconfigured driver 2
[    16.824] (==) Assigned the driver to the xf86ConfigLayout
[    16.824] (II) LoadModule: "ati"
[    16.824] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    16.824] (II) Module ati: vendor="X.Org Foundation"
[    16.824] 	compiled for 1.9.0, module version = 6.13.1
[    16.825] 	Module class: X.Org Video Driver
[    16.825] 	ABI class: X.Org Video Driver, version 8.0
[    16.825] (II) LoadModule: "radeon"
[    16.825] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    16.825] (II) Module radeon: vendor="X.Org Foundation"
[    16.826] 	compiled for 1.9.0, module version = 6.13.1
[    16.826] 	Module class: X.Org Video Driver
[    16.826] 	ABI class: X.Org Video Driver, version 8.0
[    16.826] (II) LoadModule: "vesa"
[    16.826] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    16.826] (II) Module vesa: vendor="X.Org Foundation"
[    16.826] 	compiled for 1.8.99.905, module version = 2.3.0
[    16.826] 	Module class: X.Org Video Driver
[    16.826] 	ABI class: X.Org Video Driver, version 8.0
[    16.826] (II) LoadModule: "fbdev"
[    16.827] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    16.827] (II) Module fbdev: vendor="X.Org Foundation"
[    16.827] 	compiled for 1.8.99.905, module version = 0.4.2
[    16.827] 	ABI class: X.Org Video Driver, version 8.0
[    16.827] (II) RADEON: Driver for ATI Radeon chipsets:
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
[    16.832] (II) VESA: driver for VESA chipsets: vesa
[    16.832] (II) FBDEV: driver for framebuffer: fbdev
[    16.832] (++) using VT number 7

[    16.833] (II) [KMS] drm report modesetting isn't supported.
[    16.833] (WW) Falling back to old probe method for vesa
[    16.833] (WW) Falling back to old probe method for fbdev
[    16.833] (II) Loading sub module "fbdevhw"
[    16.833] (II) LoadModule: "fbdevhw"
[    16.834] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    16.834] (II) Module fbdevhw: vendor="X.Org Foundation"
[    16.834] 	compiled for 1.9.0, module version = 0.0.2
[    16.834] 	ABI class: X.Org Video Driver, version 8.0
[    16.834] (II) RADEON(0): TOTO SAYS 00000000d0100000
[    16.834] (II) RADEON(0): MMIO registers at 0x00000000d0100000: size 64KB
[    16.834] (II) RADEON(0): PCI bus 1 card 5 func 0
[    16.834] (II) RADEON(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    16.834] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    16.834] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    16.834] (==) RADEON(0): Default visual is TrueColor
[    16.834] (II) Loading sub module "vgahw"
[    16.834] (II) LoadModule: "vgahw"
[    16.835] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    16.900] (II) Module vgahw: vendor="X.Org Foundation"
[    16.901] 	compiled for 1.9.0, module version = 0.1.0
[    16.901] 	ABI class: X.Org Video Driver, version 8.0
[    16.901] (II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
[    16.901] (==) RADEON(0): RGB weight 888
[    16.901] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    16.901] (--) RADEON(0): Chipset: "ATI Radeon XPRESS 200M 5975 (PCIE)" (ChipID = 0x5975)
[    16.901] (--) RADEON(0): Linear framebuffer at 0x00000000d4000000
[    16.901] (II) RADEON(0): PCI card detected
[    16.901] (II) Loading sub module "int10"
[    16.901] (II) LoadModule: "int10"
[    16.902] (II) Loading /usr/lib/xorg/modules/libint10.so
[    16.906] (II) Module int10: vendor="X.Org Foundation"
[    16.906] 	compiled for 1.9.0, module version = 1.0.0
[    16.906] 	ABI class: X.Org Video Driver, version 8.0
[    16.907] (II) RADEON(0): initializing int10
[    16.907] (II) RADEON(0): Primary V_BIOS segment is: 0xc000
[    16.908] (II) RADEON(0): Legacy BIOS detected
[    16.908] drmOpenDevice: node name is /dev/dri/card0
[    16.908] drmOpenDevice: open result is 12, (OK)
[    16.908] drmOpenByBusid: Searching for BusID pci:0000:01:05.0
[    16.908] drmOpenDevice: node name is /dev/dri/card0
[    16.908] drmOpenDevice: open result is 12, (OK)
[    16.908] drmOpenByBusid: drmOpenMinor returns 12
[    16.908] drmOpenByBusid: drmGetBusid reports pci:0000:01:05.0
[    16.908] (II) RADEON(0): [dri] Found DRI library version 1.3.0 and kernel module version 1.33.0
[    16.908] (II) RADEON(0): Direct rendering experimental on RS400/Xpress 200 enabled
[    16.908] (==) RADEON(0): Page Flipping disabled
[    16.908] (II) RADEON(0): Will try to use DMA for Xv image transfers
[    16.908] (II) RADEON(0): Detected total video RAM=16384K, accessible=65536K (PCI BAR=65536K)
[    16.908] (--) RADEON(0): Mapped VideoRAM: 16384 kByte (128 bit DDR SDRAM)
[    16.908] (II) RADEON(0): Color tiling enabled by default
[    16.908] (II) Loading sub module "ddc"
[    16.908] (II) LoadModule: "ddc"
[    16.908] (II) Module "ddc" already built-in
[    16.908] (II) Loading sub module "i2c"
[    16.908] (II) LoadModule: "i2c"
[    16.908] (II) Module "i2c" already built-in
[    16.908] (II) RADEON(0): ref_freq: 1432, min_out_pll: 20000, max_out_pll: 40000, min_in_pll: 100, max_in_pll: 1350, xclk: 20000, sclk: 400.000000, mclk: 200.000000
[    16.908] (II) RADEON(0): PLL parameters: rf=1432 rd=6 min=20000 max=40000; xclk=20000
[    16.908] (II) RADEON(0): Panel ID string: LPL                     
[    16.909] (II) RADEON(0): Panel Size from BIOS: 1280x800
[    16.909] (II) RADEON(0): BIOS provided dividers will be used.
[    16.909] (WW) RADEON(0): LVDS Info:
XRes: 1280, YRes: 800, DotClock: 75500
HBlank: 232, HOverPlus: 64, HSyncWidth: 48
VBlank: 32, VOverPlus: 3, VSyncWidth: 6
[    16.909] (WW) RADEON(0): LCD DDC Info Table found!
[    16.909] (II) RADEON(0): Output VGA-0 has no monitor section
[    16.909] (II) RADEON(0): I2C bus "VGA-0" initialized.
[    16.909] (II) RADEON(0): Output LVDS has no monitor section
[    16.909] (II) RADEON(0): I2C bus "LVDS" initialized.
[    16.909] (II) RADEON(0): Port0:
[    16.909]   XRANDR name: VGA-0
[    16.909]   Connector: VGA
[    16.909]   CRT1: INTERNAL_DAC2
[    16.909]   DDC reg: 0x68
[    16.909] (II) RADEON(0): Port1:
[    16.909]   XRANDR name: LVDS
[    16.909]   Connector: LVDS
[    16.909]   LCD1: INTERNAL_LVDS
[    16.909]   DDC reg: 0x1a0
[    16.909] (II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
[    16.924] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[    16.924] finished output detect: 0
[    16.924] (II) RADEON(0): I2C device "LVDS:ddc2" registered at address 0xA0.
[    16.984] (II) RADEON(0): EDID for output LVDS
[    16.984] (II) RADEON(0): Manufacturer: LPL  Model: 1001  Serial#: 0
[    16.984] (II) RADEON(0): Year: 2007  Week: 0
[    16.984] (II) RADEON(0): EDID Version: 1.3
[    16.984] (II) RADEON(0): Digital Display Input
[    16.984] (II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
[    16.984] (II) RADEON(0): Gamma: 2.20
[    16.984] (II) RADEON(0): No DPMS capabilities specified
[    16.984] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    16.984] (II) RADEON(0): First detailed timing is preferred mode
[    16.984] (II) RADEON(0): redX: 0.590 redY: 0.344   greenX: 0.323 greenY: 0.534
[    16.984] (II) RADEON(0): blueX: 0.156 blueY: 0.138   whiteX: 0.312 whiteY: 0.328
[    16.984] (II) RADEON(0): Manufacturer's mask: 0
[    16.984] (II) RADEON(0): Supported detailed timing:
[    16.984] (II) RADEON(0): clock: 75.5 MHz   Image Size:  331 x 207 mm
[    16.984] (II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1392 h_blank_end 1512 h_border: 0
[    16.984] (II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 832 v_border: 0
[    16.984] (II) RADEON(0): Supported detailed timing:
[    16.984] (II) RADEON(0): clock: 75.5 MHz   Image Size:  331 x 207 mm
[    16.984] (II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1392 h_blank_end 1512 h_border: 0
[    16.984] (II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 832 v_border: 0
[    16.984] (II) RADEON(0):  FU329
[    16.984] (II) RADEON(0):  $3@Kl&#148;°Ã
[    16.984] (II) RADEON(0): EDID (in hex):
[    16.984] (II) RADEON(0): 	00ffffffffffff00320c011000000000
[    16.984] (II) RADEON(0): 	00110103802115780a0f109758528828
[    16.984] (II) RADEON(0): 	23505400000001010101010101010101
[    16.984] (II) RADEON(0): 	0101010101017e1d00e8502020304030
[    16.984] (II) RADEON(0): 	36004bcf100000197e1d00e850202030
[    16.984] (II) RADEON(0): 	403036004bcf10000000000000fe0046
[    16.984] (II) RADEON(0): 	55333239003135345730310a000000fe
[    16.984] (II) RADEON(0): 	002433404b6c94b0c301010a20200012
[    16.984] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[    16.984] (II) RADEON(0): EDID data from the display on output: LVDS ----------------------
[    16.984] (II) RADEON(0): Manufacturer: LPL  Model: 1001  Serial#: 0
[    16.984] (II) RADEON(0): Year: 2007  Week: 0
[    16.985] (II) RADEON(0): EDID Version: 1.3
[    16.985] (II) RADEON(0): Digital Display Input
[    16.985] (II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
[    16.985] (II) RADEON(0): Gamma: 2.20
[    16.985] (II) RADEON(0): No DPMS capabilities specified
[    16.985] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    16.985] (II) RADEON(0): First detailed timing is preferred mode
[    16.985] (II) RADEON(0): redX: 0.590 redY: 0.344   greenX: 0.323 greenY: 0.534
[    16.985] (II) RADEON(0): blueX: 0.156 blueY: 0.138   whiteX: 0.312 whiteY: 0.328
[    16.985] (II) RADEON(0): Manufacturer's mask: 0
[    16.985] (II) RADEON(0): Supported detailed timing:
[    16.985] (II) RADEON(0): clock: 75.5 MHz   Image Size:  331 x 207 mm
[    16.985] (II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1392 h_blank_end 1512 h_border: 0
[    16.985] (II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 832 v_border: 0
[    16.985] (II) RADEON(0): Supported detailed timing:
[    16.985] (II) RADEON(0): clock: 75.5 MHz   Image Size:  331 x 207 mm
[    16.985] (II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1392 h_blank_end 1512 h_border: 0
[    16.985] (II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 832 v_border: 0
[    16.985] (II) RADEON(0):  FU329
[    16.985] (II) RADEON(0):  $3@Kl&#148;°Ã
[    16.985] (II) RADEON(0): EDID (in hex):
[    16.985] (II) RADEON(0): 	00ffffffffffff00320c011000000000
[    16.985] (II) RADEON(0): 	00110103802115780a0f109758528828
[    16.985] (II) RADEON(0): 	23505400000001010101010101010101
[    16.985] (II) RADEON(0): 	0101010101017e1d00e8502020304030
[    16.985] (II) RADEON(0): 	36004bcf100000197e1d00e850202030
[    16.985] (II) RADEON(0): 	403036004bcf10000000000000fe0046
[    16.985] (II) RADEON(0): 	55333239003135345730310a000000fe
[    16.985] (II) RADEON(0): 	002433404b6c94b0c301010a20200012
[    16.985] finished output detect: 1
[    16.985] finished all detect
[    17.000] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[    17.000] (II) RADEON(0): EDID for output VGA-0
[    17.060] (II) RADEON(0): EDID for output LVDS
[    17.060] (II) RADEON(0): Manufacturer: LPL  Model: 1001  Serial#: 0
[    17.060] (II) RADEON(0): Year: 2007  Week: 0
[    17.060] (II) RADEON(0): EDID Version: 1.3
[    17.060] (II) RADEON(0): Digital Display Input
[    17.060] (II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
[    17.060] (II) RADEON(0): Gamma: 2.20
[    17.060] (II) RADEON(0): No DPMS capabilities specified
[    17.060] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    17.060] (II) RADEON(0): First detailed timing is preferred mode
[    17.060] (II) RADEON(0): redX: 0.590 redY: 0.344   greenX: 0.323 greenY: 0.534
[    17.060] (II) RADEON(0): blueX: 0.156 blueY: 0.138   whiteX: 0.312 whiteY: 0.328
[    17.060] (II) RADEON(0): Manufacturer's mask: 0
[    17.060] (II) RADEON(0): Supported detailed timing:
[    17.060] (II) RADEON(0): clock: 75.5 MHz   Image Size:  331 x 207 mm
[    17.060] (II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1392 h_blank_end 1512 h_border: 0
[    17.060] (II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 832 v_border: 0
[    17.060] (II) RADEON(0): Supported detailed timing:
[    17.060] (II) RADEON(0): clock: 75.5 MHz   Image Size:  331 x 207 mm
[    17.060] (II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1392 h_blank_end 1512 h_border: 0
[    17.060] (II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 832 v_border: 0
[    17.060] (II) RADEON(0):  FU329
[    17.060] (II) RADEON(0):  $3@Kl&#148;°Ã
[    17.060] (II) RADEON(0): EDID (in hex):
[    17.060] (II) RADEON(0): 	00ffffffffffff00320c011000000000
[    17.060] (II) RADEON(0): 	00110103802115780a0f109758528828
[    17.060] (II) RADEON(0): 	23505400000001010101010101010101
[    17.060] (II) RADEON(0): 	0101010101017e1d00e8502020304030
[    17.060] (II) RADEON(0): 	36004bcf100000197e1d00e850202030
[    17.060] (II) RADEON(0): 	403036004bcf10000000000000fe0046
[    17.060] (II) RADEON(0): 	55333239003135345730310a000000fe
[    17.060] (II) RADEON(0): 	002433404b6c94b0c301010a20200012
[    17.060] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[    17.060] (II) RADEON(0): EDID data from the display on output: LVDS ----------------------
[    17.060] (II) RADEON(0): Manufacturer: LPL  Model: 1001  Serial#: 0
[    17.060] (II) RADEON(0): Year: 2007  Week: 0
[    17.061] (II) RADEON(0): EDID Version: 1.3
[    17.061] (II) RADEON(0): Digital Display Input
[    17.061] (II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
[    17.061] (II) RADEON(0): Gamma: 2.20
[    17.061] (II) RADEON(0): No DPMS capabilities specified
[    17.061] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    17.061] (II) RADEON(0): First detailed timing is preferred mode
[    17.061] (II) RADEON(0): redX: 0.590 redY: 0.344   greenX: 0.323 greenY: 0.534
[    17.061] (II) RADEON(0): blueX: 0.156 blueY: 0.138   whiteX: 0.312 whiteY: 0.328
[    17.061] (II) RADEON(0): Manufacturer's mask: 0
[    17.061] (II) RADEON(0): Supported detailed timing:
[    17.061] (II) RADEON(0): clock: 75.5 MHz   Image Size:  331 x 207 mm
[    17.061] (II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1392 h_blank_end 1512 h_border: 0
[    17.061] (II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 832 v_border: 0
[    17.061] (II) RADEON(0): Supported detailed timing:
[    17.061] (II) RADEON(0): clock: 75.5 MHz   Image Size:  331 x 207 mm
[    17.061] (II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1392 h_blank_end 1512 h_border: 0
[    17.061] (II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 832 v_border: 0
[    17.061] (II) RADEON(0):  FU329
[    17.061] (II) RADEON(0):  $3@Kl&#148;°Ã
[    17.061] (II) RADEON(0): EDID (in hex):
[    17.061] (II) RADEON(0): 	00ffffffffffff00320c011000000000
[    17.061] (II) RADEON(0): 	00110103802115780a0f109758528828
[    17.061] (II) RADEON(0): 	23505400000001010101010101010101
[    17.061] (II) RADEON(0): 	0101010101017e1d00e8502020304030
[    17.061] (II) RADEON(0): 	36004bcf100000197e1d00e850202030
[    17.061] (II) RADEON(0): 	403036004bcf10000000000000fe0046
[    17.061] (II) RADEON(0): 	55333239003135345730310a000000fe
[    17.061] (II) RADEON(0): 	002433404b6c94b0c301010a20200012
[    17.061] (II) RADEON(0): EDID vendor "LPL", prod id 4097
[    17.061] (II) RADEON(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    17.061] (II) RADEON(0): Printing probed modes for output LVDS
[    17.061] (II) RADEON(0): Modeline "1280x800"x60.0   75.50  1280 1344 1392 1512  800 803 809 832 -hsync -vsync (49.9 kHz)
[    17.061] (II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
[    17.061] (II) RADEON(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
[    17.061] (II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
[    17.061] (II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
[    17.061] (II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
[    17.061] (II) RADEON(0): Output VGA-0 disconnected
[    17.061] (II) RADEON(0): Output LVDS connected
[    17.061] (II) RADEON(0): Using exact sizes for initial modes
[    17.061] (II) RADEON(0): Output LVDS using initial mode 1280x800
[    17.061] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    17.061] (==) RADEON(0): DPI set to (96, 96)
[    17.061] (II) Loading sub module "fb"
[    17.061] (II) LoadModule: "fb"
[    17.062] (II) Loading /usr/lib/xorg/modules/libfb.so
[    17.062] (II) Module fb: vendor="X.Org Foundation"
[    17.062] 	compiled for 1.9.0, module version = 1.0.0
[    17.062] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    17.062] (II) Loading sub module "ramdac"
[    17.062] (II) LoadModule: "ramdac"
[    17.062] (II) Module "ramdac" already built-in
[    17.062] (==) RADEON(0): Using XAA acceleration architecture
[    17.062] (II) Loading sub module "xaa"
[    17.062] (II) LoadModule: "xaa"
[    17.062] (II) Loading /usr/lib/xorg/modules/libxaa.so
[    17.113] (II) Module xaa: vendor="X.Org Foundation"
[    17.113] 	compiled for 1.9.0, module version = 1.2.1
[    17.113] 	ABI class: X.Org Video Driver, version 8.0
[    17.113] (==) RADEON(0): Assuming overlay scaler buffer width is 1536
[    17.113] (II) RADEON(0): No MM_TABLE found - assuming CARD is not TV-in capable.
[    17.113] (!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
[    17.113] (II) UnloadModule: "vesa"
[    17.113] (II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    17.113] (II) UnloadModule: "fbdev"
[    17.113] (II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    17.113] (II) UnloadModule: "fbdevhw"
[    17.113] (II) Unloading /usr/lib/xorg/modules/libfbdevhw.so
[    17.114] (--) Depth 24 pixmap format is 32 bpp
[    17.114] (II) RADEON(0): RADEONScreenInit d4000000 0 0
[    17.116] Entering TV Save
[    17.116] Save TV timing tables
[    17.116] saveTimingTables: reading timing tables
[    17.116] TV Save done
[    17.116] disable LVDS
[    17.116] (II) RADEON(0): Dynamic Power Management Disabled
[    17.116] (==) RADEON(0): Using 24 bit depth buffer
[    17.116] (II) RADEON(0): RADEONInitMemoryMap() : 
[    17.116] (II) RADEON(0):   mem_size         : 0x02000000
[    17.116] (II) RADEON(0):   MC_FB_LOCATION   : 0x3fff3f00
[    17.116] (II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
[    17.116] (II) RADEON(0): Depth moves disabled by default
[    17.117] (II) RADEON(0): Using 32 MB GART aperture
[    17.117] (II) RADEON(0): Using 1 MB for the ring buffer
[    17.117] (II) RADEON(0): Using 2 MB for vertex/indirect buffers
[    17.117] (II) RADEON(0): Using 29 MB for GART textures
[    17.117] (II) RADEON(0): Memory manager initialized to (0,0) (1280,3276)
[    17.117] (II) RADEON(0): Reserved area from (0,1280) to (1280,1282)
[    17.117] (II) RADEON(0): Largest offscreen area available: 1280 x 1994
[    17.117] (II) RADEON(0): Will use front buffer at offset 0x0
[    17.117] (II) RADEON(0): Will use back buffer at offset 0x370000
[    17.117] (II) RADEON(0): Will use depth buffer at offset 0x9b0000
[    17.117] (II) RADEON(0): Will use 0 kb for textures at offset 0xff0000
[    17.117] (EE) RADEON(0): Static buffer allocation failed.  Disabling DRI.
[    17.117] (EE) RADEON(0): At least 19200 kB of video memory needed at this resolution and depth.
[    17.117] (II) RADEON(0): RADEONRestoreMemMapRegisters() : 
[    17.117] (II) RADEON(0):   MC_FB_LOCATION   : 0x3fff3f00 0x3fff3f00
[    17.117] (II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
[    17.217] (==) RADEON(0): Backing store disabled
[    17.217] (WW) RADEON(0): Direct rendering disabled
[    17.217] (II) RADEON(0): Render acceleration disabled
[    17.217] (II) RADEON(0): num quad-pipes is 1
[    17.217] (II) RADEON(0): Using XFree86 Acceleration Architecture (XAA)
[    17.217] 	Screen to screen bit blits
[    17.217] 	Solid filled rectangles
[    17.217] 	8x8 mono pattern filled rectangles
[    17.217] 	Indirect CPU to Screen color expansion
[    17.217] 	Solid Lines
[    17.217] 	Scanline Image Writes
[    17.217] 	Setting up tile and stipple cache:
[    17.217] 		32 128x128 slots
[    17.217] 		13 256x256 slots
[    17.217] 		4 512x512 slots
[    17.217] (II) RADEON(0): Acceleration enabled
[    17.217] (==) RADEON(0): DPMS enabled
[    17.218] (==) RADEON(0): Silken mouse enabled
[    17.218] (II) RADEON(0): Will use 32 kb for hardware cursor 0 at offset 0x00642800
[    17.218] (II) RADEON(0): Will use 32 kb for hardware cursor 1 at offset 0x00647800
[    17.218] (II) RADEON(0): Largest offscreen area available: 1280 x 1986
[    17.218] (II) RADEON(0): No video input capabilities detected and no information is provided - disabling multimedia i2c
[    17.218] (II) Loading sub module "theatre_detect"
[    17.218] (II) LoadModule: "theatre_detect"
[    17.218] (II) Loading /usr/lib/xorg/modules/multimedia/theatre_detect_drv.so
[    17.390] (II) Module theatre_detect: vendor="X.Org Foundation"
[    17.390] 	compiled for 1.9.0, module version = 1.0.0
[    17.390] 	ABI class: X.Org Video Driver, version 8.0
[    17.390] (II) RADEON(0): no multimedia table present, disabling Rage Theatre.
[    17.390] (II) RADEON(0): Set up overlay video
[    17.390] (II) RADEON(0): Textured video requires CP on R5xx/R6xx/R7xx/IGP
[    17.406] disable TVDAC
[    17.406] disable LVDS
[    17.406] disable LVDS
[    17.406] init memmap
[    17.406] init common
[    17.406] init crtc1
[    17.406] init pll1
[    17.406] restore memmap
[    17.406] (II) RADEON(0): RADEONRestoreMemMapRegisters() : 
[    17.406] (II) RADEON(0):   MC_FB_LOCATION   : 0x3fff3f00 0x3fff3f00
[    17.406] (II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
[    17.506] restore common
[    17.524] restore crtc1
[    17.524] restore pll1
[    17.524] set RMX
[    17.524] set LVDS
[    17.524] enable LVDS
[    18.025] disable TVDAC
[    18.025] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    18.025] (--) RandR disabled
[    18.025] (II) Initializing built-in extension Generic Event Extension
[    18.025] (II) Initializing built-in extension SHAPE
[    18.025] (II) Initializing built-in extension MIT-SHM
[    18.025] (II) Initializing built-in extension XInputExtension
[    18.025] (II) Initializing built-in extension XTEST
[    18.025] (II) Initializing built-in extension BIG-REQUESTS
[    18.025] (II) Initializing built-in extension SYNC
[    18.025] (II) Initializing built-in extension XKEYBOARD
[    18.025] (II) Initializing built-in extension XC-MISC
[    18.025] (II) Initializing built-in extension SECURITY
[    18.025] (II) Initializing built-in extension XINERAMA
[    18.025] (II) Initializing built-in extension XFIXES
[    18.025] (II) Initializing built-in extension RENDER
[    18.025] (II) Initializing built-in extension RANDR
[    18.025] (II) Initializing built-in extension COMPOSITE
[    18.025] (II) Initializing built-in extension DAMAGE
[    18.025] (II) Initializing built-in extension GESTURE
[    18.038] (II) AIGLX: Screen 0 is not DRI2 capable
[    18.039] (II) AIGLX: Screen 0 is not DRI capable
[    18.281] (II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
[    18.281] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    18.282] (II) RADEON(0): Setting screen physical size to 338 x 211
[    18.309] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    18.322] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    18.322] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    18.322] (II) LoadModule: "evdev"
[    18.323] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.323] (II) Module evdev: vendor="X.Org Foundation"
[    18.323] 	compiled for 1.9.0, module version = 2.3.2
[    18.323] 	Module class: X.Org XInput Driver
[    18.323] 	ABI class: X.Org XInput driver, version 11.0
[    18.323] (**) Power Button: always reports core events
[    18.323] (**) Power Button: Device: "/dev/input/event3"
[    18.337] (II) Power Button: Found keys
[    18.337] (II) Power Button: Configuring as keyboard
[    18.337] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    18.337] (**) Option "xkb_rules" "evdev"
[    18.337] (**) Option "xkb_model" "pc105"
[    18.337] (**) Option "xkb_layout" "us"
[    18.339] (II) config/udev: Adding input device Video Bus (/dev/input/event8)
[    18.340] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    18.340] (**) Video Bus: always reports core events
[    18.340] (**) Video Bus: Device: "/dev/input/event8"
[    18.352] (II) Video Bus: Found keys
[    18.352] (II) Video Bus: Configuring as keyboard
[    18.352] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    18.352] (**) Option "xkb_rules" "evdev"
[    18.352] (**) Option "xkb_model" "pc105"
[    18.352] (**) Option "xkb_layout" "us"
[    18.353] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    18.353] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    18.353] (**) Power Button: always reports core events
[    18.353] (**) Power Button: Device: "/dev/input/event0"
[    18.353] (II) Power Button: Found keys
[    18.353] (II) Power Button: Configuring as keyboard
[    18.353] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    18.353] (**) Option "xkb_rules" "evdev"
[    18.353] (**) Option "xkb_model" "pc105"
[    18.353] (**) Option "xkb_layout" "us"
[    18.354] (II) config/udev: Adding input device Lid Switch (/dev/input/event2)
[    18.354] (II) No input driver/identifier specified (ignoring)
[    18.354] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    18.354] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    18.354] (**) Sleep Button: always reports core events
[    18.354] (**) Sleep Button: Device: "/dev/input/event1"
[    18.369] (II) Sleep Button: Found keys
[    18.369] (II) Sleep Button: Configuring as keyboard
[    18.369] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    18.369] (**) Option "xkb_rules" "evdev"
[    18.369] (**) Option "xkb_model" "pc105"
[    18.369] (**) Option "xkb_layout" "us"
[    18.372] (II) config/udev: Adding input device Logitech Optical USB Mouse (/dev/input/event5)
[    18.372] (**) Logitech Optical USB Mouse: Applying InputClass "evdev pointer catchall"
[    18.372] (**) Logitech Optical USB Mouse: always reports core events
[    18.372] (**) Logitech Optical USB Mouse: Device: "/dev/input/event5"
[    18.385] (II) Logitech Optical USB Mouse: Found 3 mouse buttons
[    18.428] (II) Logitech Optical USB Mouse: Found scroll wheel(s)
[    18.428] (II) Logitech Optical USB Mouse: Found relative axes
[    18.428] (II) Logitech Optical USB Mouse: Found x and y relative axes
[    18.428] (II) Logitech Optical USB Mouse: Configuring as mouse
[    18.428] (**) Logitech Optical USB Mouse: YAxisMapping: buttons 4 and 5
[    18.428] (**) Logitech Optical USB Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    18.428] (II) XINPUT: Adding extended input device "Logitech Optical USB Mouse" (type: MOUSE)
[    18.428] (II) Logitech Optical USB Mouse: initialized for relative axes.
[    18.428] (II) config/udev: Adding input device Logitech Optical USB Mouse (/dev/input/mouse0)
[    18.428] (II) No input driver/identifier specified (ignoring)
[    18.429] (II) config/udev: Adding input device Microsoft MicrosoftÂ® Digital Media Keyboard 3000 (/dev/input/event6)
[    18.429] (**) Microsoft MicrosoftÂ® Digital Media Keyboard 3000: Applying InputClass "evdev keyboard catchall"
[    18.429] (**) Microsoft MicrosoftÂ® Digital Media Keyboard 3000: always reports core events
[    18.429] (**) Microsoft MicrosoftÂ® Digital Media Keyboard 3000: Device: "/dev/input/event6"
[    18.440] (II) Microsoft MicrosoftÂ® Digital Media Keyboard 3000: Found keys
[    18.440] (II) Microsoft MicrosoftÂ® Digital Media Keyboard 3000: Configuring as keyboard
[    18.440] (II) XINPUT: Adding extended input device "Microsoft MicrosoftÂ® Digital Media Keyboard 3000" (type: KEYBOARD)
[    18.440] (**) Option "xkb_rules" "evdev"
[    18.440] (**) Option "xkb_model" "pc105"
[    18.440] (**) Option "xkb_layout" "us"
[    18.441] (II) config/udev: Adding input device Microsoft MicrosoftÂ® Digital Media Keyboard 3000 (/dev/input/event7)
[    18.441] (**) Microsoft MicrosoftÂ® Digital Media Keyboard 3000: Applying InputClass "evdev keyboard catchall"
[    18.441] (**) Microsoft MicrosoftÂ® Digital Media Keyboard 3000: always reports core events
[    18.441] (**) Microsoft MicrosoftÂ® Digital Media Keyboard 3000: Device: "/dev/input/event7"
[    18.456] (II) Microsoft MicrosoftÂ® Digital Media Keyboard 3000: Found 1 mouse buttons
[    18.456] (II) Microsoft MicrosoftÂ® Digital Media Keyboard 3000: Found scroll wheel(s)
[    18.456] (II) Microsoft MicrosoftÂ® Digital Media Keyboard 3000: Found relative axes
[    18.456] (II) Microsoft MicrosoftÂ® Digital Media Keyboard 3000: Found absolute axes
[    18.456] (II) Microsoft MicrosoftÂ® Digital Media Keyboard 3000: Found x and y absolute axes
[    18.456] (II) Microsoft MicrosoftÂ® Digital Media Keyboard 3000: Found keys
[    18.456] (II) Microsoft MicrosoftÂ® Digital Media Keyboard 3000: Configuring as mouse
[    18.456] (II) Microsoft MicrosoftÂ® Digital Media Keyboard 3000: Configuring as keyboard
[    18.456] (**) Microsoft MicrosoftÂ® Digital Media Keyboard 3000: YAxisMapping: buttons 4 and 5
[    18.456] (**) Microsoft MicrosoftÂ® Digital Media Keyboard 3000: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    18.456] (II) XINPUT: Adding extended input device "Microsoft MicrosoftÂ® Digital Media Keyboard 3000" (type: KEYBOARD)
[    18.456] (**) Option "xkb_rules" "evdev"
[    18.456] (**) Option "xkb_model" "pc105"
[    18.456] (**) Option "xkb_layout" "us"
[    18.456] (EE) Microsoft MicrosoftÂ® Digital Media Keyboard 3000: failed to initialize for relative axes.
[    18.456] (WW) Microsoft MicrosoftÂ® Digital Media Keyboard 3000: found 37 axes, limiting to 36.
[    18.456] (II) Microsoft MicrosoftÂ® Digital Media Keyboard 3000: initialized for absolute axes.
[    18.457] (II) config/udev: Adding input device Microsoft MicrosoftÂ® Digital Media Keyboard 3000 (/dev/input/js0)
[    18.457] (II) No input driver/identifier specified (ignoring)
[    18.459] (II) config/udev: Adding input device HDA ATI SB Mic at Ext Right Jack (/dev/input/event10)
[    18.460] (II) No input driver/identifier specified (ignoring)
[    18.460] (II) config/udev: Adding input device HDA ATI SB HP Out at Ext Right Jack (/dev/input/event11)
[    18.460] (II) No input driver/identifier specified (ignoring)
[    18.461] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    18.461] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    18.461] (**) AT Translated Set 2 keyboard: always reports core events
[    18.461] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    18.476] (II) AT Translated Set 2 keyboard: Found keys
[    18.476] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    18.476] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    18.476] (**) Option "xkb_rules" "evdev"
[    18.476] (**) Option "xkb_model" "pc105"
[    18.476] (**) Option "xkb_layout" "us"
[    18.477] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event12)
[    18.477] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    18.477] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    18.477] (II) LoadModule: "synaptics"
[    18.477] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    18.477] (II) Module synaptics: vendor="X.Org Foundation"
[    18.477] 	compiled for 1.9.0, module version = 1.2.2
[    18.477] 	Module class: X.Org XInput Driver
[    18.477] 	ABI class: X.Org XInput driver, version 11.0
[    18.477] (II) Synaptics touchpad driver version 1.2.2
[    18.477] (**) Option "Device" "/dev/input/event12"
[    18.525] (II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[    18.525] (II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[    18.525] (II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    18.525] (II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
[    18.525] (II) SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    18.557] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    18.557] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    18.573] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    18.573] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    18.573] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
[    18.573] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    18.573] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    18.605] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    18.605] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
[    18.605] (II) No input driver/identifier specified (ignoring)
[    18.609] (II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event9)
[    18.609] (**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    18.610] (**) Dell WMI hotkeys: always reports core events
[    18.610] (**) Dell WMI hotkeys: Device: "/dev/input/event9"
[    18.621] (II) Dell WMI hotkeys: Found keys
[    18.621] (II) Dell WMI hotkeys: Configuring as keyboard
[    18.621] (II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD)
[    18.621] (**) Option "xkb_rules" "evdev"
[    18.621] (**) Option "xkb_model" "pc105"
[    18.621] (**) Option "xkb_layout" "us"
[    24.189] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[    24.258] (II) RADEON(0): EDID vendor "LPL", prod id 4097
[    24.258] (II) RADEON(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    24.258] (II) RADEON(0): Printing DDC gathered Modelines:
[    24.258] (II) RADEON(0): Modeline "1280x800"x0.0   75.50  1280 1344 1392 1512  800 803 809 832 -hsync -vsync (49.9 kHz)
[    24.258] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[    24.258] (II) RADEON(0): EDID data from the display on output: LVDS ----------------------
[    24.258] (II) RADEON(0): Manufacturer: LPL  Model: 1001  Serial#: 0
[    24.258] (II) RADEON(0): Year: 2007  Week: 0
[    24.258] (II) RADEON(0): EDID Version: 1.3
[    24.258] (II) RADEON(0): Digital Display Input
[    24.258] (II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
[    24.258] (II) RADEON(0): Gamma: 2.20
[    24.259] (II) RADEON(0): No DPMS capabilities specified
[    24.259] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    24.259] (II) RADEON(0): First detailed timing is preferred mode
[    24.259] (II) RADEON(0): redX: 0.590 redY: 0.344   greenX: 0.323 greenY: 0.534
[    24.259] (II) RADEON(0): blueX: 0.156 blueY: 0.138   whiteX: 0.312 whiteY: 0.328
[    24.259] (II) RADEON(0): Manufacturer's mask: 0
[    24.259] (II) RADEON(0): Supported detailed timing:
[    24.259] (II) RADEON(0): clock: 75.5 MHz   Image Size:  331 x 207 mm
[    24.259] (II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1392 h_blank_end 1512 h_border: 0
[    24.259] (II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 832 v_border: 0
[    24.259] (II) RADEON(0): Supported detailed timing:
[    24.259] (II) RADEON(0): clock: 75.5 MHz   Image Size:  331 x 207 mm
[    24.259] (II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1392 h_blank_end 1512 h_border: 0
[    24.259] (II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 832 v_border: 0
[    24.259] (II) RADEON(0):  FU329
[    24.259] (II) RADEON(0):  $3@Kl&#148;°Ã
[    24.259] (II) RADEON(0): EDID (in hex):
[    24.259] (II) RADEON(0): 	00ffffffffffff00320c011000000000
[    24.259] (II) RADEON(0): 	00110103802115780a0f109758528828
[    24.259] (II) RADEON(0): 	23505400000001010101010101010101
[    24.259] (II) RADEON(0): 	0101010101017e1d00e8502020304030
[    24.259] (II) RADEON(0): 	36004bcf100000197e1d00e850202030
[    24.259] (II) RADEON(0): 	403036004bcf10000000000000fe0046
[    24.259] (II) RADEON(0): 	55333239003135345730310a000000fe
[    24.259] (II) RADEON(0): 	002433404b6c94b0c301010a20200012
[    24.259] (II) RADEON(0): EDID vendor "LPL", prod id 4097
[    24.259] (II) RADEON(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    33.670] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[    33.801] (II) RADEON(0): EDID vendor "LPL", prod id 4097
[    33.801] (II) RADEON(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    33.801] (II) RADEON(0): Printing DDC gathered Modelines:
[    33.801] (II) RADEON(0): Modeline "1280x800"x0.0   75.50  1280 1344 1392 1512  800 803 809 832 -hsync -vsync (49.9 kHz)
[    33.801] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[    33.801] (II) RADEON(0): EDID data from the display on output: LVDS ----------------------
[    33.801] (II) RADEON(0): Manufacturer: LPL  Model: 1001  Serial#: 0
[    33.801] (II) RADEON(0): Year: 2007  Week: 0
[    33.801] (II) RADEON(0): EDID Version: 1.3
[    33.801] (II) RADEON(0): Digital Display Input
[    33.801] (II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
[    33.801] (II) RADEON(0): Gamma: 2.20
[    33.801] (II) RADEON(0): No DPMS capabilities specified
[    33.801] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    33.801] (II) RADEON(0): First detailed timing is preferred mode
[    33.801] (II) RADEON(0): redX: 0.590 redY: 0.344   greenX: 0.323 greenY: 0.534
[    33.801] (II) RADEON(0): blueX: 0.156 blueY: 0.138   whiteX: 0.312 whiteY: 0.328
[    33.801] (II) RADEON(0): Manufacturer's mask: 0
[    33.801] (II) RADEON(0): Supported detailed timing:
[    33.801] (II) RADEON(0): clock: 75.5 MHz   Image Size:  331 x 207 mm
[    33.801] (II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1392 h_blank_end 1512 h_border: 0
[    33.801] (II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 832 v_border: 0
[    33.801] (II) RADEON(0): Supported detailed timing:
[    33.801] (II) RADEON(0): clock: 75.5 MHz   Image Size:  331 x 207 mm
[    33.801] (II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1392 h_blank_end 1512 h_border: 0
[    33.801] (II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 832 v_border: 0
[    33.802] (II) RADEON(0):  FU329
[    33.802] (II) RADEON(0):  $3@Kl&#148;°Ã
[    33.802] (II) RADEON(0): EDID (in hex):
[    33.802] (II) RADEON(0): 	00ffffffffffff00320c011000000000
[    33.802] (II) RADEON(0): 	00110103802115780a0f109758528828
[    33.802] (II) RADEON(0): 	23505400000001010101010101010101
[    33.802] (II) RADEON(0): 	0101010101017e1d00e8502020304030
[    33.802] (II) RADEON(0): 	36004bcf100000197e1d00e850202030
[    33.802] (II) RADEON(0): 	403036004bcf10000000000000fe0046
[    33.802] (II) RADEON(0): 	55333239003135345730310a000000fe
[    33.802] (II) RADEON(0): 	002433404b6c94b0c301010a20200012
[    33.802] (II) RADEON(0): EDID vendor "LPL", prod id 4097
[    33.802] (II) RADEON(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.

```

Funny, it looks like it *is* loading the ATI driver, but just not openGL for some reason... :/

---

### Post by NightwishFan on 2010-10-29
```
Static buffer allocation failed.  Disabling DRI.
[    17.117] (EE) RADEON(0): At least 19200 kB of video memory needed at this resolution and depth.
[    17.117] (II) RADEON(0): RADEONRestoreMemMapRegisters() : 
[    17.117] (II) RADEON(0):   MC_FB_LOCATION   : 0x3fff3f00 0x3fff3f00
[    17.117] (II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
[    17.217] (==) RADEON(0): Backing store disabled
[    17.217] (WW) RADEON(0): Direct rendering disabled
[    17.217] (II) RADEON(0): Render acceleration disabled
```

To be honest I am fairly baffled, especially if it worked on the live session. Is there an option in recovery mode to reset X. (it is always there one release and not there the next so I have no idea)

---

### Post by phredbull on 2010-10-31
Have you tried enabling KMS?

---

