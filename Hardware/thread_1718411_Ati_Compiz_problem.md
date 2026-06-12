---
title: "Ati Compiz problem"
date: 2011-03-31
forum: Hardware
---

### Post by Draven501 on 2011-03-31
Compiz always worked before on my laptop but after a recent update it didn't work. After clicking extra/ normal visual affects in  appearance settings it now says 'Desktop effects could not be enabled' 

My computer has an Ati Mobility Radeon HD 5470 graphics card. It always seemed to work without the Ati Proprietary driver, whenever I enabled it Ubuntu failed to boot so I had to go into recovery mode and disable it

When I type in 'compiz' into a terminal I get this:

```
compiz (core) - Fatal: Software rendering detected.
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

Launching fallback window manager
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x2200003 (Authentica)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x2200003 (Authentica)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
```


Thanks in advance :D

---

### Post by Yellow Pasque on 2011-03-31
Post /var/log/Xorg.0.log to figure out why you have software rendering.

---

### Post by Draven501 on 2011-04-01
Ok here it is... even me, the noob I am can see there is a  problem 

```
[    15.731] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    15.731] X Protocol Version 11, Revision 0
[    15.731] Build Operating System: Linux 2.6.24-28-server x86_64 Ubuntu
[    15.731] Current Operating System: Linux alistair-Aspire-3820 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 02:41:37 UTC 2010 x86_64
[    15.731] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-24-generic root=UUID=9b84a6cc-5612-45b8-b724-771410ddb2ca ro vga=792 splash acpi_osi=Linux quiet splash
[    15.731] Build Date: 09 January 2011  12:14:27PM
[    15.731] xorg-server 2:1.9.0-0ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
[    15.731] Current version of pixman: 0.18.4
[    15.731] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    15.731] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    15.731] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Apr  1 07:55:38 2011
[    15.742] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    15.743] (==) No Layout section.  Using the first Screen section.
[    15.743] (==) No screen section available. Using defaults.
[    15.743] (**) |-->Screen "Default Screen Section" (0)
[    15.743] (**) |   |-->Monitor "<default monitor>"
[    15.743] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    15.743] (==) Automatically adding devices
[    15.743] (==) Automatically enabling devices
[    15.743] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    15.743] 	Entry deleted from font path.
[    15.743] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    15.743] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    15.743] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    15.743] (II) Loader magic: 0x7d17a0
[    15.743] (II) Module ABI versions:
[    15.743] 	X.Org ANSI C Emulation: 0.4
[    15.743] 	X.Org Video Driver: 8.0
[    15.743] 	X.Org XInput driver : 11.0
[    15.743] 	X.Org Server Extension : 4.0
[    15.744] (--) PCI:*(0:2:0:0) 1002:68e0:1025:0364 rev 0, Mem @ 0xd0000000/268435456, 0xcfee0000/131072, I/O @ 0x00002000/256, BIOS @ 0x????????/131072
[    15.744] (II) Open ACPI successful (/var/run/acpid.socket)
[    15.744] (II) LoadModule: "extmod"
[    15.779] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    15.779] (II) Module extmod: vendor="X.Org Foundation"
[    15.779] 	compiled for 1.9.0, module version = 1.0.0
[    15.779] 	Module class: X.Org Server Extension
[    15.779] 	ABI class: X.Org Server Extension, version 4.0
[    15.779] (II) Loading extension MIT-SCREEN-SAVER
[    15.779] (II) Loading extension XFree86-VidModeExtension
[    15.779] (II) Loading extension XFree86-DGA
[    15.779] (II) Loading extension DPMS
[    15.779] (II) Loading extension XVideo
[    15.779] (II) Loading extension XVideo-MotionCompensation
[    15.779] (II) Loading extension X-Resource
[    15.779] (II) LoadModule: "dbe"
[    15.780] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    15.780] (II) Module dbe: vendor="X.Org Foundation"
[    15.780] 	compiled for 1.9.0, module version = 1.0.0
[    15.780] 	Module class: X.Org Server Extension
[    15.780] 	ABI class: X.Org Server Extension, version 4.0
[    15.780] (II) Loading extension DOUBLE-BUFFER
[    15.780] (II) LoadModule: "glx"
[    15.780] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    15.780] (II) Module glx: vendor="X.Org Foundation"
[    15.780] 	compiled for 1.9.0, module version = 1.0.0
[    15.780] 	ABI class: X.Org Server Extension, version 4.0
[    15.780] (==) AIGLX enabled
[    15.780] (II) Loading extension GLX
[    15.780] (II) LoadModule: "record"
[    15.780] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    15.781] (II) Module record: vendor="X.Org Foundation"
[    15.781] 	compiled for 1.9.0, module version = 1.13.0
[    15.781] 	Module class: X.Org Server Extension
[    15.781] 	ABI class: X.Org Server Extension, version 4.0
[    15.781] (II) Loading extension RECORD
[    15.781] (II) LoadModule: "dri"
[    15.781] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    15.781] (II) Module dri: vendor="X.Org Foundation"
[    15.781] 	compiled for 1.9.0, module version = 1.0.0
[    15.781] 	ABI class: X.Org Server Extension, version 4.0
[    15.781] (II) Loading extension XFree86-DRI
[    15.781] (II) LoadModule: "dri2"
[    15.781] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    15.781] (II) Module dri2: vendor="X.Org Foundation"
[    15.781] 	compiled for 1.9.0, module version = 1.2.0
[    15.781] 	ABI class: X.Org Server Extension, version 4.0
[    15.781] (II) Loading extension DRI2
[    15.781] (==) Matched ati as autoconfigured driver 0
[    15.781] (==) Matched vesa as autoconfigured driver 1
[    15.781] (==) Matched fbdev as autoconfigured driver 2
[    15.781] (==) Assigned the driver to the xf86ConfigLayout
[    15.781] (II) LoadModule: "ati"
[    15.781] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    15.782] (II) Module ati: vendor="X.Org Foundation"
[    15.782] 	compiled for 1.9.0, module version = 6.13.1
[    15.782] 	Module class: X.Org Video Driver
[    15.782] 	ABI class: X.Org Video Driver, version 8.0
[    15.782] (II) LoadModule: "radeon"
[    15.782] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    15.782] (II) Module radeon: vendor="X.Org Foundation"
[    15.782] 	compiled for 1.9.0, module version = 6.13.1
[    15.782] 	Module class: X.Org Video Driver
[    15.782] 	ABI class: X.Org Video Driver, version 8.0
[    15.782] (II) LoadModule: "vesa"
[    15.782] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    15.782] (II) Module vesa: vendor="X.Org Foundation"
[    15.782] 	compiled for 1.8.99.905, module version = 2.3.0
[    15.782] 	Module class: X.Org Video Driver
[    15.782] 	ABI class: X.Org Video Driver, version 8.0
[    15.782] (II) LoadModule: "fbdev"
[    15.782] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    15.782] (II) Module fbdev: vendor="X.Org Foundation"
[    15.782] 	compiled for 1.8.99.905, module version = 0.4.2
[    15.782] 	ABI class: X.Org Video Driver, version 8.0
[    15.782] (II) RADEON: Driver for ATI Radeon chipsets:
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
[    15.786] (II) VESA: driver for VESA chipsets: vesa
[    15.786] (II) FBDEV: driver for framebuffer: fbdev
[    15.786] (++) using VT number 7

[    15.786] (II) [KMS] Kernel modesetting enabled.
[    15.786] (WW) Falling back to old probe method for vesa
[    15.786] (WW) Falling back to old probe method for fbdev
[    15.786] (II) Loading sub module "fbdevhw"
[    15.786] (II) LoadModule: "fbdevhw"
[    15.787] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    15.787] (II) Module fbdevhw: vendor="X.Org Foundation"
[    15.787] 	compiled for 1.9.0, module version = 0.0.2
[    15.787] 	ABI class: X.Org Video Driver, version 8.0
[    15.787] (II) RADEON(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    15.787] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    15.787] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    15.787] (==) RADEON(0): Default visual is TrueColor
[    15.787] (==) RADEON(0): RGB weight 888
[    15.787] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    15.787] (--) RADEON(0): Chipset: "ATI Mobility Radeon HD 5000 Series" (ChipID = 0x68e0)
[    15.787] (II) RADEON(0): PCIE card detected
[    15.787] (WW) RADEON(0): Color tiling is not yet supported on R600/R700
[    15.787] (II) RADEON(0): KMS Color Tiling: disabled
[    15.787] drmOpenDevice: node name is /dev/dri/card0
[    15.787] drmOpenDevice: open result is 9, (OK)
[    15.787] drmOpenByBusid: Searching for BusID pci:0000:02:00.0
[    15.787] drmOpenDevice: node name is /dev/dri/card0
[    15.787] drmOpenDevice: open result is 9, (OK)
[    15.787] drmOpenByBusid: drmOpenMinor returns 9
[    15.787] drmOpenByBusid: drmGetBusid reports pci:0000:02:00.0
[    15.791] (II) RADEON(0): Output LVDS has no monitor section
[    15.795] (II) RADEON(0): Output HDMI-0 has no monitor section
[    15.850] (II) RADEON(0): Output VGA-0 has no monitor section
[    15.854] (II) RADEON(0): EDID for output LVDS
[    15.854] (II) RADEON(0): Not using default mode "640x350" (vrefresh out of range)
[    15.854] (II) RADEON(0): Not using default mode "320x175" (doublescan mode not supported)
[    15.854] (II) RADEON(0): Not using default mode "640x400" (vrefresh out of range)
[    15.854] (II) RADEON(0): Not using default mode "320x200" (doublescan mode not supported)
[    15.854] (II) RADEON(0): Not using default mode "720x400" (vrefresh out of range)
[    15.854] (II) RADEON(0): Not using default mode "360x200" (doublescan mode not supported)
[    15.854] (II) RADEON(0): Not using default mode "320x240" (doublescan mode not supported)
[    15.854] (II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
[    15.854] (II) RADEON(0): Not using default mode "320x240" (doublescan mode not supported)
[    15.854] (II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
[    15.854] (II) RADEON(0): Not using default mode "320x240" (doublescan mode not supported)
[    15.854] (II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
[    15.854] (II) RADEON(0): Not using default mode "320x240" (doublescan mode not supported)
[    15.854] (II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
[    15.854] (II) RADEON(0): Not using default mode "400x300" (doublescan mode not supported)
[    15.854] (II) RADEON(0): Not using default mode "400x300" (doublescan mode not supported)
[    15.854] (II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
[    15.854] (II) RADEON(0): Not using default mode "400x300" (doublescan mode not supported)
[    15.854] (II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
[    15.854] (II) RADEON(0): Not using default mode "400x300" (doublescan mode not supported)
[    15.854] (II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
[    15.854] (II) RADEON(0): Not using default mode "400x300" (doublescan mode not supported)
[    15.854] (II) RADEON(0): Not using default mode "1024x768i" (interlace mode not supported)
[    15.854] (II) RADEON(0): Not using default mode "512x384i" (doublescan mode not supported)
[    15.854] (II) RADEON(0): Not using default mode "1024x768" (hsync out of range)
[    15.854] (II) RADEON(0): Not using default mode "512x384" (doublescan mode not supported)
[    15.854] (II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
[    15.854] (II) RADEON(0): Not using default mode "512x384" (doublescan mode not supported)
[    15.854] (II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
[    15.854] (II) RADEON(0): Not using default mode "512x384" (doublescan mode not supported)
[    15.854] (II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
[    15.854] (II) RADEON(0): Not using default mode "512x384" (doublescan mode not supported)
[    15.854] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[    15.854] (II) RADEON(0): Not using default mode "576x432" (doublescan mode not supported)
[    15.854] (II) RADEON(0): Not using default mode "1280x960" (hsync out of range)
[    15.854] (II) RADEON(0): Not using default mode "640x480" (doublescan mode not supported)
[    15.854] (II) RADEON(0): Not using default mode "1280x960" (vrefresh out of range)
[    15.854] (II) RADEON(0): Not using default mode "640x480" (doublescan mode not supported)
[    15.854] (II) RADEON(0): Not using default mode "1280x1024" (hsync out of range)
[    15.854] (II) RADEON(0): Not using default mode "640x512" (doublescan mode not supported)
[    15.854] (II) RADEON(0): Not using default mode "1280x1024" (vrefresh out of range)
[    15.854] (II) RADEON(0): Not using default mode "640x512" (doublescan mode not supported)
[    15.854] (II) RADEON(0): Not using default mode "1280x1024" (vrefresh out of range)
[    15.854] (II) RADEON(0): Not using default mode "640x512" (doublescan mode not supported)
[    15.854] (II) RADEON(0): Not using default mode "1600x1200" (hsync out of range)
[    15.854] (II) RADEON(0): Not using default mode "800x600" (doublescan mode not supported)
[    15.854] (II) RADEON(0): Not using default mode "1600x1200" (vrefresh out of range)
[    15.854] (II) RADEON(0): Not using default mode "800x600" (doublescan mode not supported)
[    15.854] (II) RADEON(0): Not using default mode "1600x1200" (vrefresh out of range)
[    15.854] (II) RADEON(0): Not using default mode "800x600" (doublescan mode not supported)
[    15.854] (II) RADEON(0): Not using default mode "1600x1200" (vrefresh out of range)
[    15.854] (II) RADEON(0): Not using default mode "800x600" (doublescan mode not supported)
[    15.854] (II) RADEON(0): Not using default mode "1600x1200" (vrefresh out of range)
[    15.854] (II) RADEON(0): Not using default mode "800x600" (doublescan mode not supported)
[    15.854] (II) RADEON(0): Not using default mode "1792x1344" (hsync out of range)
[    15.854] (II) RADEON(0): Not using default mode "896x672" (doublescan mode not supported)
[    15.854] (II) RADEON(0): Not using default mode "1792x1344" (vrefresh out of range)
[    15.854] (II) RADEON(0): Not using default mode "896x672" (doublescan mode not supported)
[    15.854] (II) RADEON(0): Not using default mode "1856x1392" (hsync out of range)
[    15.854] (II) RADEON(0): Not using default mode "928x696" (doublescan mode not supported)
[    15.854] (II) RADEON(0): Not using default mode "1856x1392" (vrefresh out of range)
[    15.854] (II) RADEON(0): Not using default mode "928x696" (doublescan mode not supported)
[    15.854] (II) RADEON(0): Not using default mode "1920x1440" (hsync out of range)
[    15.854] (II) RADEON(0): Not using default mode "960x720" (doublescan mode not supported)
[    15.854] (II) RADEON(0): Not using default mode "1920x1440" (vrefresh out of range)
[    15.854] (II) RADEON(0): Not using default mode "960x720" (doublescan mode not supported)
[    15.854] (II) RADEON(0): Not using default mode "832x624" (vrefresh out of range)
[    15.854] (II) RADEON(0): Not using default mode "416x312" (doublescan mode not supported)
[    15.854] (II) RADEON(0): Not using default mode "1152x864" (hsync out of range)
[    15.854] (II) RADEON(0): Not using default mode "576x432" (doublescan mode not supported)
[    15.854] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[    15.854] (II) RADEON(0): Not using default mode "576x432" (doublescan mode not supported)
[    15.854] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[    15.854] (II) RADEON(0): Not using default mode "576x432" (doublescan mode not supported)
[    15.854] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[    15.854] (II) RADEON(0): Not using default mode "576x432" (doublescan mode not supported)
[    15.854] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[    15.854] (II) RADEON(0): Not using default mode "576x432" (doublescan mode not supported)
[    15.854] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[    15.854] (II) RADEON(0): Not using default mode "576x432" (doublescan mode not supported)
[    15.854] (II) RADEON(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
[    15.854] (II) RADEON(0): Not using default mode "680x384" (doublescan mode not supported)
[    15.854] (II) RADEON(0): Not using default mode "680x384" (doublescan mode not supported)
[    15.854] (II) RADEON(0): Not using default mode "1400x1050" (hsync out of range)
[    15.854] (II) RADEON(0): Not using default mode "700x525" (doublescan mode not supported)
[    15.854] (II) RADEON(0): Not using default mode "1400x1050" (vrefresh out of range)
[    15.854] (II) RADEON(0): Not using default mode "700x525" (doublescan mode not supported)
[    15.854] (II) RADEON(0): Not using default mode "1400x1050" (vrefresh out of range)
[    15.854] (II) RADEON(0): Not using default mode "700x525" (doublescan mode not supported)
[    15.854] (II) RADEON(0): Not using default mode "1400x1050" (vrefresh out of range)
[    15.854] (II) RADEON(0): Not using default mode "700x525" (doublescan mode not supported)
[    15.854] (II) RADEON(0): Not using default mode "1440x900" (hsync out of range)
[    15.854] (II) RADEON(0): Not using default mode "720x450" (doublescan mode not supported)
[    15.854] (II) RADEON(0): Not using default mode "1600x1024" (hsync out of range)
[    15.854] (II) RADEON(0): Not using default mode "800x512" (doublescan mode not supported)
[    15.855] (II) RADEON(0): Not using default mode "1680x1050" (hsync out of range)
[    15.855] (II) RADEON(0): Not using default mode "840x525" (doublescan mode not supported)
[    15.855] (II) RADEON(0): Not using default mode "1680x1050" (hsync out of range)
[    15.855] (II) RADEON(0): Not using default mode "840x525" (doublescan mode not supported)
[    15.855] (II) RADEON(0): Not using default mode "1680x1050" (vrefresh out of range)
[    15.855] (II) RADEON(0): Not using default mode "840x525" (doublescan mode not supported)
[    15.855] (II) RADEON(0): Not using default mode "1680x1050" (vrefresh out of range)
[    15.855] (II) RADEON(0): Not using default mode "840x525" (doublescan mode not supported)
[    15.855] (II) RADEON(0): Not using default mode "1680x1050" (vrefresh out of range)
[    15.855] (II) RADEON(0): Not using default mode "840x525" (doublescan mode not supported)
[    15.855] (II) RADEON(0): Not using default mode "1920x1080" (hsync out of range)
[    15.855] (II) RADEON(0): Not using default mode "960x540" (doublescan mode not supported)
[    15.855] (II) RADEON(0): Not using default mode "1920x1200" (hsync out of range)
[    15.855] (II) RADEON(0): Not using default mode "960x600" (doublescan mode not supported)
[    15.855] (II) RADEON(0): Not using default mode "1920x1440" (vrefresh out of range)
[    15.855] (II) RADEON(0): Not using default mode "960x720" (doublescan mode not supported)
[    15.855] (II) RADEON(0): Not using default mode "2048x1536" (hsync out of range)
[    15.855] (II) RADEON(0): Not using default mode "1024x768" (doublescan mode not supported)
[    15.855] (II) RADEON(0): Not using default mode "2048x1536" (vrefresh out of range)
[    15.855] (II) RADEON(0): Not using default mode "1024x768" (doublescan mode not supported)
[    15.855] (II) RADEON(0): Not using default mode "2048x1536" (vrefresh out of range)
[    15.855] (II) RADEON(0): Not using default mode "1024x768" (doublescan mode not supported)
[    15.855] (II) RADEON(0): Printing probed modes for output LVDS
[    15.855] (II) RADEON(0): Modeline "1366x768"x60.0   69.50  1366 1414 1446 1466  768 771 777 790 -hsync -vsync (47.4 kHz)
[    15.855] (II) RADEON(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    15.855] (II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
[    15.855] (II) RADEON(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
[    15.855] (II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
[    15.855] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    15.855] (II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
[    15.855] (II) RADEON(0): Modeline "848x480"x59.7   31.50  848 872 952 1056  480 483 493 500 -hsync +vsync (29.8 kHz)
[    15.855] (II) RADEON(0): Modeline "720x480"x59.7   26.75  720 744 808 896  480 483 493 500 -hsync +vsync (29.9 kHz)
[    15.855] (II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    15.855] (II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
[    15.859] (II) RADEON(0): EDID for output HDMI-0
[    15.913] (II) RADEON(0): EDID for output VGA-0
[    15.914] (II) RADEON(0): Manufacturer: GSM  Model: 578f  Serial#: 257016
[    15.914] (II) RADEON(0): Year: 2010  Week: 9
[    15.914] (II) RADEON(0): EDID Version: 1.3
[    15.914] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[    15.914] (II) RADEON(0): Sync:  Separate
[    15.914] (II) RADEON(0): Max Image Size [cm]: horiz.: 51  vert.: 29
[    15.914] (II) RADEON(0): Gamma: 2.20
[    15.914] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    15.914] (II) RADEON(0): First detailed timing is preferred mode
[    15.914] (II) RADEON(0): redX: 0.628 redY: 0.348   greenX: 0.345 greenY: 0.615
[    15.914] (II) RADEON(0): blueX: 0.153 blueY: 0.057   whiteX: 0.313 whiteY: 0.329
[    15.914] (II) RADEON(0): Supported established timings:
[    15.914] (II) RADEON(0): 720x400@70Hz
[    15.914] (II) RADEON(0): 640x480@60Hz
[    15.914] (II) RADEON(0): 640x480@75Hz
[    15.914] (II) RADEON(0): 800x600@56Hz
[    15.914] (II) RADEON(0): 800x600@60Hz
[    15.914] (II) RADEON(0): 800x600@75Hz
[    15.914] (II) RADEON(0): 832x624@75Hz
[    15.914] (II) RADEON(0): 1024x768@60Hz
[    15.914] (II) RADEON(0): 1024x768@75Hz
[    15.914] (II) RADEON(0): 1280x1024@75Hz
[    15.914] (II) RADEON(0): 1152x864@75Hz
[    15.914] (II) RADEON(0): Manufacturer's mask: 0
[    15.914] (II) RADEON(0): Supported standard timings:
[    15.914] (II) RADEON(0): #0: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[    15.914] (II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    15.914] (II) RADEON(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    15.914] (II) RADEON(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    15.914] (II) RADEON(0): Supported detailed timing:
[    15.914] (II) RADEON(0): clock: 148.5 MHz   Image Size:  510 x 290 mm
[    15.914] (II) RADEON(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    15.914] (II) RADEON(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    15.914] (II) RADEON(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 155 MHz
[    15.914] (II) RADEON(0): Monitor name: E2350
[    15.914] (II) RADEON(0): Serial No: 009NDAY7K016
[    15.914] (II) RADEON(0): EDID (in hex):
[    15.914] (II) RADEON(0): 	00ffffffffffff001e6d8f57f8eb0300
[    15.914] (II) RADEON(0): 	0914010368331d78eac665a059589d27
[    15.914] (II) RADEON(0): 	0e5054a76b80b30081808140714f0101
[    15.914] (II) RADEON(0): 	010101010101023a801871382d40582c
[    15.914] (II) RADEON(0): 	4500fe221100001e000000fd00384b1e
[    15.914] (II) RADEON(0): 	530f000a202020202020000000fc0045
[    15.914] (II) RADEON(0): 	323335300a20202020202020000000ff
[    15.914] (II) RADEON(0): 	003030394e444159374b3031360a000b
[    15.914] (II) RADEON(0): Printing probed modes for output VGA-0
[    15.914] (II) RADEON(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    15.914] (II) RADEON(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[    15.914] (II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    15.914] (II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    15.914] (II) RADEON(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    15.914] (II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    15.914] (II) RADEON(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
[    15.914] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    15.914] (II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    15.914] (II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    15.914] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    15.914] (II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    15.914] (II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    15.914] (II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    15.914] (II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    15.914] (II) RADEON(0): Output LVDS connected
[    15.914] (II) RADEON(0): Output HDMI-0 disconnected
[    15.914] (II) RADEON(0): Output VGA-0 connected
[    15.914] (II) RADEON(0): Using fuzzy aspect match for initial modes
[    15.914] (II) RADEON(0): Output LVDS using initial mode 1024x768
[    15.914] (II) RADEON(0): Output VGA-0 using initial mode 1024x768
[    15.914] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    15.914] (II) RADEON(0): mem size init: gart size :1fdff000 vram size: s:10000000 visible:f7d7000
[    15.914] (II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
[    15.914] (==) RADEON(0): DPI set to (96, 96)
[    15.914] (II) Loading sub module "fb"
[    15.914] (II) LoadModule: "fb"
[    15.914] (II) Loading /usr/lib/xorg/modules/libfb.so
[    15.915] (II) Module fb: vendor="X.Org Foundation"
[    15.915] 	compiled for 1.9.0, module version = 1.0.0
[    15.915] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    15.915] (II) Loading sub module "ramdac"
[    15.915] (II) LoadModule: "ramdac"
[    15.915] (II) Module "ramdac" already built-in
[    15.915] (II) RADEON(0): GPU accel disabled or not working, using shadowfb for KMS
[    15.915] (II) Loading sub module "shadow"
[    15.915] (II) LoadModule: "shadow"
[    15.915] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    15.915] (II) Module shadow: vendor="X.Org Foundation"
[    15.915] 	compiled for 1.9.0, module version = 1.1.0
[    15.915] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    15.915] (II) UnloadModule: "vesa"
[    15.915] (II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    15.915] (II) UnloadModule: "fbdev"
[    15.915] (II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    15.915] (II) UnloadModule: "fbdevhw"
[    15.915] (II) Unloading /usr/lib/xorg/modules/libfbdevhw.so
[    15.915] (--) Depth 24 pixmap format is 32 bpp
[    15.915] (II) RADEON(0): Front buffer size: 3072K
[    15.915] (II) RADEON(0): VRAM usage limit set to 225644K
[    15.915] (==) RADEON(0): Backing store disabled
[    15.915] (WW) RADEON(0): Direct rendering disabled
[    15.915] (II) RADEON(0): Acceleration disabled
[    15.915] (==) RADEON(0): DPMS enabled
[    15.915] (==) RADEON(0): Silken mouse enabled
[    15.915] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    15.915] (--) RandR disabled
[    15.916] (II) Initializing built-in extension Generic Event Extension
[    15.916] (II) Initializing built-in extension SHAPE
[    15.916] (II) Initializing built-in extension MIT-SHM
[    15.916] (II) Initializing built-in extension XInputExtension
[    15.916] (II) Initializing built-in extension XTEST
[    15.916] (II) Initializing built-in extension BIG-REQUESTS
[    15.916] (II) Initializing built-in extension SYNC
[    15.916] (II) Initializing built-in extension XKEYBOARD
[    15.916] (II) Initializing built-in extension XC-MISC
[    15.916] (II) Initializing built-in extension SECURITY
[    15.916] (II) Initializing built-in extension XINERAMA
[    15.916] (II) Initializing built-in extension XFIXES
[    15.916] (II) Initializing built-in extension RENDER
[    15.916] (II) Initializing built-in extension RANDR
[    15.916] (II) Initializing built-in extension COMPOSITE
[    15.916] (II) Initializing built-in extension DAMAGE
[    15.916] (II) Initializing built-in extension GESTURE
[    15.921] (II) AIGLX: Screen 0 is not DRI2 capable
[    15.921] (II) AIGLX: Screen 0 is not DRI capable
[    15.923] (II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
[    15.923] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    17.338] (II) RADEON(0): Setting screen physical size to 270 x 203
[    17.353] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    17.359] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    17.360] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    17.360] (II) LoadModule: "evdev"
[    17.360] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.360] (II) Module evdev: vendor="X.Org Foundation"
[    17.360] 	compiled for 1.9.0, module version = 2.3.2
[    17.360] 	Module class: X.Org XInput Driver
[    17.360] 	ABI class: X.Org XInput driver, version 11.0
[    17.360] (**) Power Button: always reports core events
[    17.360] (**) Power Button: Device: "/dev/input/event2"
[    17.401] (II) Power Button: Found keys
[    17.401] (II) Power Button: Configuring as keyboard
[    17.401] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    17.401] (**) Option "xkb_rules" "evdev"
[    17.401] (**) Option "xkb_model" "pc105"
[    17.401] (**) Option "xkb_layout" "us"
[    17.402] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[    17.402] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    17.402] (**) Video Bus: always reports core events
[    17.402] (**) Video Bus: Device: "/dev/input/event4"
[    17.453] (II) Video Bus: Found keys
[    17.453] (II) Video Bus: Configuring as keyboard
[    17.453] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    17.453] (**) Option "xkb_rules" "evdev"
[    17.453] (**) Option "xkb_model" "pc105"
[    17.453] (**) Option "xkb_layout" "us"
[    17.455] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    17.455] (II) No input driver/identifier specified (ignoring)
[    17.455] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    17.455] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    17.455] (**) Sleep Button: always reports core events
[    17.455] (**) Sleep Button: Device: "/dev/input/event1"
[    17.533] (II) Sleep Button: Found keys
[    17.533] (II) Sleep Button: Configuring as keyboard
[    17.533] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    17.533] (**) Option "xkb_rules" "evdev"
[    17.533] (**) Option "xkb_model" "pc105"
[    17.534] (**) Option "xkb_layout" "us"
[    17.536] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event5)
[    17.536] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    17.536] (**) Logitech USB Receiver: always reports core events
[    17.536] (**) Logitech USB Receiver: Device: "/dev/input/event5"
[    17.611] (II) Logitech USB Receiver: Found keys
[    17.611] (II) Logitech USB Receiver: Configuring as keyboard
[    17.611] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[    17.611] (**) Option "xkb_rules" "evdev"
[    17.611] (**) Option "xkb_model" "pc105"
[    17.611] (**) Option "xkb_layout" "us"
[    17.611] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event6)
[    17.612] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[    17.612] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    17.612] (**) Logitech USB Receiver: always reports core events
[    17.612] (**) Logitech USB Receiver: Device: "/dev/input/event6"
[    17.693] (II) Logitech USB Receiver: Found 12 mouse buttons
[    17.693] (II) Logitech USB Receiver: Found scroll wheel(s)
[    17.693] (II) Logitech USB Receiver: Found relative axes
[    17.693] (II) Logitech USB Receiver: Found x and y relative axes
[    17.693] (II) Logitech USB Receiver: Found absolute axes
[    17.694] (II) evdev-grail: failed to open grail, no gesture support
[    17.694] (II) Logitech USB Receiver: Found keys
[    17.694] (II) Logitech USB Receiver: Configuring as mouse
[    17.694] (II) Logitech USB Receiver: Configuring as keyboard
[    17.694] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[    17.694] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    17.694] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[    17.694] (**) Option "xkb_rules" "evdev"
[    17.694] (**) Option "xkb_model" "pc105"
[    17.694] (**) Option "xkb_layout" "us"
[    17.694] (II) Logitech USB Receiver: initialized for relative axes.
[    17.694] (WW) Logitech USB Receiver: ignoring absolute axes.
[    17.694] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse0)
[    17.694] (II) No input driver/identifier specified (ignoring)
[    17.694] (II) config/udev: Adding input device 1.3M WebCam (/dev/input/event7)
[    17.695] (**) 1.3M WebCam: Applying InputClass "evdev keyboard catchall"
[    17.695] (**) 1.3M WebCam: always reports core events
[    17.695] (**) 1.3M WebCam: Device: "/dev/input/event7"
[    17.773] (II) 1.3M WebCam: Found keys
[    17.773] (II) 1.3M WebCam: Configuring as keyboard
[    17.773] (II) XINPUT: Adding extended input device "1.3M WebCam" (type: KEYBOARD)
[    17.773] (**) Option "xkb_rules" "evdev"
[    17.773] (**) Option "xkb_model" "pc105"
[    17.773] (**) Option "xkb_layout" "us"
[    17.775] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    17.775] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    17.775] (**) AT Translated Set 2 keyboard: always reports core events
[    17.775] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    17.843] (II) AT Translated Set 2 keyboard: Found keys
[    17.843] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    17.843] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    17.843] (**) Option "xkb_rules" "evdev"
[    17.843] (**) Option "xkb_model" "pc105"
[    17.843] (**) Option "xkb_layout" "us"
[    17.844] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event8)
[    17.844] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    17.844] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    17.844] (II) LoadModule: "synaptics"
[    17.844] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    17.844] (II) Module synaptics: vendor="X.Org Foundation"
[    17.844] 	compiled for 1.9.0, module version = 1.2.2
[    17.844] 	Module class: X.Org XInput Driver
[    17.844] 	ABI class: X.Org XInput driver, version 11.0
[    17.844] (II) Synaptics touchpad driver version 1.2.2
[    17.844] (**) Option "Device" "/dev/input/event8"
[    18.093] (II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5822
[    18.096] (II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4766
[    18.096] (II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    18.096] (II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
[    18.096] (II) SynPS/2 Synaptics TouchPad: buttons: left right
[    18.301] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    18.301] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    18.431] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    18.431] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    18.431] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
[    18.431] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    18.431] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    18.751] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    18.751] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
[    18.751] (II) No input driver/identifier specified (ignoring)
[    29.504] (II) RADEON(0): Allocate new frame buffer 1920x1088 stride 1920
[    29.505] (II) RADEON(0): VRAM usage limit set to 221065K
[    90.512] (II) RADEON(0): EDID vendor "GSM", prod id 22415
[    90.512] (II) RADEON(0): Using EDID range info for horizontal sync
[    90.512] (II) RADEON(0): Using EDID range info for vertical refresh
[    90.512] (II) RADEON(0): Printing DDC gathered Modelines:
[    90.512] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    90.512] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    90.512] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    90.512] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    90.512] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    90.512] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    90.512] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    90.512] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    90.512] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    90.512] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    90.512] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    90.512] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    90.512] (II) RADEON(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[    90.512] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    90.512] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[   170.766] (II) RADEON(0): EDID vendor "GSM", prod id 22415
[   170.766] (II) RADEON(0): Using hsync ranges from config file
[   170.766] (II) RADEON(0): Using vrefresh ranges from config file
[   170.766] (II) RADEON(0): Printing DDC gathered Modelines:
[   170.766] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[   170.766] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   170.766] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   170.766] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   170.766] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   170.766] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   170.766] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   170.766] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   170.766] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   170.766] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   170.766] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   170.766] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   170.766] (II) RADEON(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[   170.766] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   170.766] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
```

Thanks again

---

### Post by Yellow Pasque on 2011-04-01
Hmm. Everything looks good until it randomly says:
> (II) RADEON(0): GPU accel disabled or not working, using shadowfb for KMS
I think the next place to look would be:
```
dmesg | grep drm
```

---

