---
title: "No more 3d acceleration with ubuntu 11.04 and ati rv710"
date: 2011-07-14
forum: Hardware
---

### Post by Sinner on 2011-07-14
Hi all,

Since I upgraded from 10.10 to 11.04, I have lost 3d acceleration and so have no unity (default session).
I own an ATI radeon 4350 (rv710) gfx card.

Symptom: when I select the Ubuntu session (the default), I only get the wallpaper and the mouse pointer, then nothing happen. I am forced to go a tty1 and kill Xorg then revert to the safe mode gnome session.


It seems that I have exactly the same problem than pontu here:
[http://ubuntuforums.org/showthread.php?p=11043661](http://ubuntuforums.org/showthread.php?p=11043661)

Any help welcome !!

/usr/lib/nux/unity_support_test -p
```

OpenGL vendor string:   X.Org
OpenGL renderer string: Gallium 0.4 on AMD RV710
OpenGL version string:  2.1 Mesa 7.10.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          yes


```


here is my /var/log/Xorg.0.log with open source driver:
```

[   122.626] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[   122.626] X Protocol Version 11, Revision 0
[   122.626] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[   122.626] Current Operating System: Linux desktop 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686
[   122.626] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=0c21be46-cdbf-4834-bca4-f2ae56eec59a ro quiet splash vt.handoff=7
[   122.626] Build Date: 21 May 2011  11:38:35AM
[   122.626] xorg-server 2:1.10.1-1ubuntu1.1 (For technical support please see http://www.ubuntu.com/support) 
[   122.626] Current version of pixman: 0.20.2
[   122.626] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[   122.626] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   122.626] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Jul 13 18:45:16 2011
[   122.626] (==) Using config file: "/etc/X11/xorg.conf"
[   122.626] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   122.627] (==) No Layout section.  Using the first Screen section.
[   122.627] (**) |-->Screen "Default Screen" (0)
[   122.627] (**) |   |-->Monitor "<default monitor>"
[   122.627] (==) No monitor specified for screen "Default Screen".
	Using a default monitor configuration.
[   122.627] (==) Automatically adding devices
[   122.627] (==) Automatically enabling devices
[   122.627] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   122.627] 	Entry deleted from font path.
[   122.627] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   122.627] 	Entry deleted from font path.
[   122.627] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   122.627] 	Entry deleted from font path.
[   122.627] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   122.627] 	Entry deleted from font path.
[   122.627] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   122.627] 	Entry deleted from font path.
[   122.627] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[   122.627] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   122.627] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[   122.627] (II) Loader magic: 0x81ffde0
[   122.627] (II) Module ABI versions:
[   122.627] 	X.Org ANSI C Emulation: 0.4
[   122.627] 	X.Org Video Driver: 10.0
[   122.627] 	X.Org XInput driver : 12.3
[   122.627] 	X.Org Server Extension : 5.0
[   122.629] (--) PCI:*(0:2:0:0) 1002:954f:1043:02a8 rev 0, Mem @ 0xd0000000/268435456, 0xfeae0000/65536, I/O @ 0x0000e000/256, BIOS @ 0x????????/131072
[   122.629] (II) Open ACPI successful (/var/run/acpid.socket)
[   122.629] (II) "extmod" will be loaded by default.
[   122.629] (II) "dbe" will be loaded by default.
[   122.629] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[   122.629] (II) "record" will be loaded by default.
[   122.629] (II) "dri" will be loaded by default.
[   122.629] (II) "dri2" will be loaded by default.
[   122.629] (II) LoadModule: "glx"
[   122.630] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   122.630] (II) Module glx: vendor="X.Org Foundation"
[   122.630] 	compiled for 1.10.1, module version = 1.0.0
[   122.630] 	ABI class: X.Org Server Extension, version 5.0
[   122.630] (==) AIGLX enabled
[   122.630] (II) Loading extension GLX
[   122.630] (II) LoadModule: "extmod"
[   122.630] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   122.630] (II) Module extmod: vendor="X.Org Foundation"
[   122.630] 	compiled for 1.10.1, module version = 1.0.0
[   122.630] 	Module class: X.Org Server Extension
[   122.630] 	ABI class: X.Org Server Extension, version 5.0
[   122.631] (II) Loading extension MIT-SCREEN-SAVER
[   122.631] (II) Loading extension XFree86-VidModeExtension
[   122.631] (II) Loading extension XFree86-DGA
[   122.631] (II) Loading extension DPMS
[   122.631] (II) Loading extension XVideo
[   122.631] (II) Loading extension XVideo-MotionCompensation
[   122.631] (II) Loading extension X-Resource
[   122.631] (II) LoadModule: "dbe"
[   122.631] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   122.631] (II) Module dbe: vendor="X.Org Foundation"
[   122.631] 	compiled for 1.10.1, module version = 1.0.0
[   122.631] 	Module class: X.Org Server Extension
[   122.631] 	ABI class: X.Org Server Extension, version 5.0
[   122.631] (II) Loading extension DOUBLE-BUFFER
[   122.631] (II) LoadModule: "record"
[   122.632] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   122.632] (II) Module record: vendor="X.Org Foundation"
[   122.632] 	compiled for 1.10.1, module version = 1.13.0
[   122.632] 	Module class: X.Org Server Extension
[   122.632] 	ABI class: X.Org Server Extension, version 5.0
[   122.632] (II) Loading extension RECORD
[   122.632] (II) LoadModule: "dri"
[   122.632] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   122.633] (II) Module dri: vendor="X.Org Foundation"
[   122.633] 	compiled for 1.10.1, module version = 1.0.0
[   122.633] 	ABI class: X.Org Server Extension, version 5.0
[   122.633] (II) Loading extension XFree86-DRI
[   122.633] (II) LoadModule: "dri2"
[   122.633] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   122.633] (II) Module dri2: vendor="X.Org Foundation"
[   122.633] 	compiled for 1.10.1, module version = 1.2.0
[   122.633] 	ABI class: X.Org Server Extension, version 5.0
[   122.633] (II) Loading extension DRI2
[   122.633] (==) Matched fglrx as autoconfigured driver 0
[   122.633] (==) Matched ati as autoconfigured driver 1
[   122.633] (==) Matched vesa as autoconfigured driver 2
[   122.633] (==) Matched fbdev as autoconfigured driver 3
[   122.633] (==) Assigned the driver to the xf86ConfigLayout
[   122.633] (II) LoadModule: "fglrx"
[   122.634] (WW) Warning, couldn't open module fglrx
[   122.634] (II) UnloadModule: "fglrx"
[   122.634] (II) Unloading fglrx
[   122.634] (EE) Failed to load module "fglrx" (module does not exist, 0)
[   122.634] (II) LoadModule: "ati"
[   122.634] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[   122.635] (II) Module ati: vendor="X.Org Foundation"
[   122.635] 	compiled for 1.10.1, module version = 6.14.0
[   122.635] 	Module class: X.Org Video Driver
[   122.635] 	ABI class: X.Org Video Driver, version 10.0
[   122.635] (II) LoadModule: "radeon"
[   122.635] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[   122.635] (II) Module radeon: vendor="X.Org Foundation"
[   122.635] 	compiled for 1.10.1, module version = 6.14.0
[   122.635] 	Module class: X.Org Video Driver
[   122.635] 	ABI class: X.Org Video Driver, version 10.0
[   122.635] (II) LoadModule: "vesa"
[   122.636] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   122.636] (II) Module vesa: vendor="X.Org Foundation"
[   122.636] 	compiled for 1.10.0, module version = 2.3.0
[   122.636] 	Module class: X.Org Video Driver
[   122.636] 	ABI class: X.Org Video Driver, version 10.0
[   122.636] (II) LoadModule: "fbdev"
[   122.636] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   122.636] (II) Module fbdev: vendor="X.Org Foundation"
[   122.636] 	compiled for 1.10.0, module version = 0.4.2
[   122.636] 	ABI class: X.Org Video Driver, version 10.0
[   122.636] (II) RADEON: Driver for ATI Radeon chipsets:
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
	ATI Radeon HD 5450, CEDAR, AMD Radeon HD 6900M Series,
	Mobility Radeon HD 6000 Series, BARTS, BARTS,
	Mobility Radeon HD 6000 Series, Mobility Radeon HD 6000 Series,
	BARTS, BARTS, BARTS, BARTS, AMD Radeon HD 6800 Series,
	AMD Radeon HD 6800 Series, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
	TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, CAICOS, CAICOS,
	CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
	CAICOS
[   122.644] (II) VESA: driver for VESA chipsets: vesa
[   122.644] (II) FBDEV: driver for framebuffer: fbdev
[   122.644] (--) using VT number 8

[   122.686] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[   122.686] (II) [KMS] Kernel modesetting enabled.
[   122.686] (WW) Falling back to old probe method for vesa
[   122.686] (WW) Falling back to old probe method for fbdev
[   122.686] (II) Loading sub module "fbdevhw"
[   122.686] (II) LoadModule: "fbdevhw"
[   122.687] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   122.687] (II) Module fbdevhw: vendor="X.Org Foundation"
[   122.687] 	compiled for 1.10.1, module version = 0.0.2
[   122.687] 	ABI class: X.Org Video Driver, version 10.0
[   122.687] (II) RADEON(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
[   122.687] (**) RADEON(0): Depth 24, (--) framebuffer bpp 32
[   122.687] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[   122.687] (==) RADEON(0): Default visual is TrueColor
[   122.687] (==) RADEON(0): RGB weight 888
[   122.687] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[   122.687] (--) RADEON(0): Chipset: "ATI Radeon HD 4350" (ChipID = 0x954f)
[   122.688] (II) RADEON(0): PCIE card detected
[   122.688] drmOpenDevice: node name is /dev/dri/card0
[   122.688] drmOpenDevice: open result is 9, (OK)
[   122.688] drmOpenByBusid: Searching for BusID pci:0000:02:00.0
[   122.688] drmOpenDevice: node name is /dev/dri/card0
[   122.688] drmOpenDevice: open result is 9, (OK)
[   122.688] drmOpenByBusid: drmOpenMinor returns 9
[   122.688] drmOpenByBusid: drmGetBusid reports pci:0000:02:00.0
[   122.688] (II) RADEON(0): KMS Color Tiling: disabled
[   122.688] (II) RADEON(0): KMS Pageflipping: enabled
[   122.688] (II) RADEON(0): SwapBuffers wait for vsync: enabled
[   122.704] (II) RADEON(0): Output VGA-0 has no monitor section
[   122.708] (II) RADEON(0): Output HDMI-0 has no monitor section
[   122.762] (II) RADEON(0): Output DVI-0 has no monitor section
[   122.784] (II) RADEON(0): EDID for output VGA-0
[   122.788] (II) RADEON(0): EDID for output HDMI-0
[   122.843] (II) RADEON(0): EDID for output DVI-0
[   122.843] (II) RADEON(0): Manufacturer: BNQ  Model: 76d5  Serial#: 1866
[   122.843] (II) RADEON(0): Year: 2006  Week: 37
[   122.843] (II) RADEON(0): EDID Version: 1.3
[   122.843] (II) RADEON(0): Digital Display Input
[   122.843] (II) RADEON(0): Max Image Size [cm]: horiz.: 38  vert.: 30
[   122.843] (II) RADEON(0): Gamma: 2.20
[   122.843] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off
[   122.843] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[   122.843] (II) RADEON(0): First detailed timing is preferred mode
[   122.843] (II) RADEON(0): redX: 0.640 redY: 0.340   greenX: 0.290 greenY: 0.610
[   122.843] (II) RADEON(0): blueX: 0.140 blueY: 0.070   whiteX: 0.310 whiteY: 0.330
[   122.843] (II) RADEON(0): Supported established timings:
[   122.843] (II) RADEON(0): 720x400@70Hz
[   122.843] (II) RADEON(0): 640x480@60Hz
[   122.843] (II) RADEON(0): 640x480@67Hz
[   122.843] (II) RADEON(0): 640x480@72Hz
[   122.843] (II) RADEON(0): 640x480@75Hz
[   122.843] (II) RADEON(0): 800x600@60Hz
[   122.843] (II) RADEON(0): 800x600@72Hz
[   122.843] (II) RADEON(0): 800x600@75Hz
[   122.843] (II) RADEON(0): 832x624@75Hz
[   122.843] (II) RADEON(0): 1024x768@60Hz
[   122.843] (II) RADEON(0): 1024x768@70Hz
[   122.843] (II) RADEON(0): 1024x768@75Hz
[   122.843] (II) RADEON(0): 1280x1024@75Hz
[   122.843] (II) RADEON(0): 1152x864@75Hz
[   122.843] (II) RADEON(0): Manufacturer's mask: 0
[   122.843] (II) RADEON(0): Supported standard timings:
[   122.843] (II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[   122.843] (II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[   122.843] (II) RADEON(0): #2: hsize: 1280  vsize 1024  refresh: 72  vid: 35969
[   122.843] (II) RADEON(0): Supported detailed timing:
[   122.843] (II) RADEON(0): clock: 108.0 MHz   Image Size:  376 x 301 mm
[   122.843] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
[   122.843] (II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[   122.843] (II) RADEON(0): Supported detailed timing:
[   122.843] (II) RADEON(0): clock: 25.2 MHz   Image Size:  376 x 301 mm
[   122.843] (II) RADEON(0): h_active: 640  h_sync: 656  h_sync_end 752 h_blank_end 800 h_border: 0
[   122.844] (II) RADEON(0): v_active: 350  v_sync: 387  v_sync_end 389 v_blanking: 449 v_border: 0
[   122.844] (II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 31 H max: 83 kHz, PixClock max 145 MHz
[   122.844] (II) RADEON(0): Monitor name: BenQ FP93GX
[   122.844] (II) RADEON(0): EDID (in hex):
[   122.844] (II) RADEON(0): 	00ffffffffffff0009d1d5764a070000
[   122.844] (II) RADEON(0): 	2510010380261e78eac5c6a3574a9c23
[   122.844] (II) RADEON(0): 	124f54bdef80714f8180818c01010101
[   122.844] (II) RADEON(0): 	010101010101302a009851002a403070
[   122.844] (II) RADEON(0): 	1300782d1100001ed50980a0205e6310
[   122.844] (II) RADEON(0): 	10605208782d1100001a000000fd0038
[   122.844] (II) RADEON(0): 	4c1f530e000a202020202020000000fc
[   122.844] (II) RADEON(0): 	0042656e51204650393347580a200015
[   122.844] (II) RADEON(0): Printing probed modes for output DVI-0
[   122.844] (II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   122.844] (II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   122.844] (II) RADEON(0): Modeline "1280x1024"x72.0  132.84  1280 1368 1504 1728  1024 1025 1028 1067 -hsync +vsync (76.9 kHz)
[   122.844] (II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   122.844] (II) RADEON(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
[   122.844] (II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[   122.844] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   122.844] (II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   122.844] (II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[   122.844] (II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   122.844] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   122.844] (II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
[   122.844] (II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   122.844] (II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[   122.844] (II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   122.844] (II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   122.844] (II) RADEON(0): Modeline "640x350"x70.1   25.17  640 656 752 800  350 357 359 449 +hsync -vsync (31.5 kHz)
[   122.844] (II) RADEON(0): Output VGA-0 disconnected
[   122.844] (II) RADEON(0): Output HDMI-0 disconnected
[   122.844] (II) RADEON(0): Output DVI-0 connected
[   122.844] (II) RADEON(0): Using exact sizes for initial modes
[   122.844] (II) RADEON(0): Output DVI-0 using initial mode 1280x1024
[   122.844] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[   122.844] (II) RADEON(0): mem size init: gart size :1fdff000 vram size: s:20000000 visible:fac0000
[   122.844] (II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
[   122.844] (==) RADEON(0): DPI set to (96, 96)
[   122.844] (II) Loading sub module "fb"
[   122.844] (II) LoadModule: "fb"
[   122.845] (II) Loading /usr/lib/xorg/modules/libfb.so
[   122.845] (II) Module fb: vendor="X.Org Foundation"
[   122.845] 	compiled for 1.10.1, module version = 1.0.0
[   122.845] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   122.845] (II) Loading sub module "ramdac"
[   122.845] (II) LoadModule: "ramdac"
[   122.845] (II) Module "ramdac" already built-in
[   122.845] (II) Loading sub module "exa"
[   122.845] (II) LoadModule: "exa"
[   122.845] (II) Loading /usr/lib/xorg/modules/libexa.so
[   122.845] (II) Module exa: vendor="X.Org Foundation"
[   122.845] 	compiled for 1.10.1, module version = 2.5.0
[   122.845] 	ABI class: X.Org Video Driver, version 10.0
[   122.845] (II) UnloadModule: "vesa"
[   122.845] (II) Unloading vesa
[   122.845] (II) UnloadModule: "fbdev"
[   122.845] (II) Unloading fbdev
[   122.845] (II) UnloadModule: "fbdevhw"
[   122.845] (II) Unloading fbdevhw
[   122.845] (--) Depth 24 pixmap format is 32 bpp
[   122.846] (II) RADEON(0): [DRI2] Setup complete
[   122.846] (II) RADEON(0): [DRI2]   DRI driver: r600
[   122.846] (II) RADEON(0): Front buffer size: 5120K
[   122.846] (II) RADEON(0): VRAM usage limit set to 226483K
[   122.846] (==) RADEON(0): Backing store disabled
[   122.846] (II) RADEON(0): Direct rendering enabled
[   122.846] (II) RADEON(0): Setting EXA maxPitchBytes
[   122.846] (II) EXA(0): Driver allocated offscreen pixmaps
[   122.846] (II) EXA(0): Driver registered support for the following operations:
[   122.846] (II)         Solid
[   122.846] (II)         Copy
[   122.846] (II)         Composite (RENDER acceleration)
[   122.846] (II)         UploadToScreen
[   122.846] (II)         DownloadFromScreen
[   122.846] (II) RADEON(0): Acceleration enabled
[   122.846] (==) RADEON(0): DPMS enabled
[   122.846] (==) RADEON(0): Silken mouse enabled
[   122.846] (II) RADEON(0): Set up textured video
[   122.846] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[   122.846] (--) RandR disabled
[   122.847] (II) Initializing built-in extension Generic Event Extension
[   122.847] (II) Initializing built-in extension SHAPE
[   122.847] (II) Initializing built-in extension MIT-SHM
[   122.847] (II) Initializing built-in extension XInputExtension
[   122.847] (II) Initializing built-in extension XTEST
[   122.847] (II) Initializing built-in extension BIG-REQUESTS
[   122.847] (II) Initializing built-in extension SYNC
[   122.847] (II) Initializing built-in extension XKEYBOARD
[   122.847] (II) Initializing built-in extension XC-MISC
[   122.847] (II) Initializing built-in extension SECURITY
[   122.847] (II) Initializing built-in extension XINERAMA
[   122.847] (II) Initializing built-in extension XFIXES
[   122.847] (II) Initializing built-in extension RENDER
[   122.847] (II) Initializing built-in extension RANDR
[   122.847] (II) Initializing built-in extension COMPOSITE
[   122.847] (II) Initializing built-in extension DAMAGE
[   122.847] (II) Initializing built-in extension GESTURE
[   122.859] (II) AIGLX: Trying DRI driver /usr/lib/dri/r600_dri.so
[   122.863] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[   122.863] (II) AIGLX: enabled GLX_INTEL_swap_event
[   122.863] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[   122.863] (II) AIGLX: enabled GLX_SGI_make_current_read
[   122.863] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[   122.863] (II) AIGLX: Loaded and initialized r600
[   122.863] (II) GLX: Initialized DRI2 GL provider for screen 0
[   122.865] (II) RADEON(0): Setting screen physical size to 338 x 270
[   122.875] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   122.887] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[   122.887] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   122.887] (II) LoadModule: "evdev"
[   122.888] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   122.888] (II) Module evdev: vendor="X.Org Foundation"
[   122.888] 	compiled for 1.10.0.902, module version = 2.6.0
[   122.888] 	Module class: X.Org XInput Driver
[   122.888] 	ABI class: X.Org XInput driver, version 12.3
[   122.888] (II) Using input driver 'evdev' for 'Power Button'
[   122.888] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   122.888] (**) Power Button: always reports core events
[   122.888] (**) Power Button: Device: "/dev/input/event2"
[   122.900] (--) Power Button: Found keys
[   122.900] (II) Power Button: Configuring as keyboard
[   122.900] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[   122.900] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[   122.900] (**) Option "xkb_rules" "evdev"
[   122.900] (**) Option "xkb_model" "pc105"
[   122.900] (**) Option "xkb_layout" "fr"
[   122.900] (**) Option "xkb_variant" "oss"
[   122.903] (II) XKB: reuse xkmfile /var/lib/xkb/server-6CCE7350BC740BB33D520367F4A10E64192A358C.xkm
[   122.906] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[   122.907] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   122.907] (II) Using input driver 'evdev' for 'Power Button'
[   122.907] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   122.907] (**) Power Button: always reports core events
[   122.907] (**) Power Button: Device: "/dev/input/event1"
[   122.920] (--) Power Button: Found keys
[   122.920] (II) Power Button: Configuring as keyboard
[   122.920] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[   122.920] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[   122.920] (**) Option "xkb_rules" "evdev"
[   122.920] (**) Option "xkb_model" "pc105"
[   122.920] (**) Option "xkb_layout" "fr"
[   122.920] (**) Option "xkb_variant" "oss"
[   122.920] (II) config/udev: Adding input device Sleep Button (/dev/input/event0)
[   122.920] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[   122.921] (II) Using input driver 'evdev' for 'Sleep Button'
[   122.921] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   122.921] (**) Sleep Button: always reports core events
[   122.921] (**) Sleep Button: Device: "/dev/input/event0"
[   122.940] (--) Sleep Button: Found keys
[   122.940] (II) Sleep Button: Configuring as keyboard
[   122.940] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input0/event0"
[   122.940] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[   122.940] (**) Option "xkb_rules" "evdev"
[   122.940] (**) Option "xkb_model" "pc105"
[   122.940] (**) Option "xkb_layout" "fr"
[   122.940] (**) Option "xkb_variant" "oss"
[   122.948] (II) config/udev: Adding input device Logitech HID compliant keyboard (/dev/input/event3)
[   122.948] (**) Logitech HID compliant keyboard: Applying InputClass "evdev keyboard catchall"
[   122.948] (II) Using input driver 'evdev' for 'Logitech HID compliant keyboard'
[   122.948] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   122.948] (**) Logitech HID compliant keyboard: always reports core events
[   122.948] (**) Logitech HID compliant keyboard: Device: "/dev/input/event3"
[   122.964] (--) Logitech HID compliant keyboard: Found keys
[   122.964] (II) Logitech HID compliant keyboard: Configuring as keyboard
[   122.964] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:10.1/usb3/3-2/3-2:1.0/input/input3/event3"
[   122.964] (II) XINPUT: Adding extended input device "Logitech HID compliant keyboard" (type: KEYBOARD)
[   122.964] (**) Option "xkb_rules" "evdev"
[   122.964] (**) Option "xkb_model" "pc105"
[   122.964] (**) Option "xkb_layout" "fr"
[   122.964] (**) Option "xkb_variant" "oss"
[   122.965] (II) config/udev: Adding input device Logitech HID compliant keyboard (/dev/input/event4)
[   122.965] (**) Logitech HID compliant keyboard: Applying InputClass "evdev keyboard catchall"
[   122.965] (II) Using input driver 'evdev' for 'Logitech HID compliant keyboard'
[   122.965] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   122.965] (**) Logitech HID compliant keyboard: always reports core events
[   122.965] (**) Logitech HID compliant keyboard: Device: "/dev/input/event4"
[   122.984] (--) Logitech HID compliant keyboard: Found 20 mouse buttons
[   122.984] (--) Logitech HID compliant keyboard: Found keys
[   122.984] (II) Logitech HID compliant keyboard: Configuring as mouse
[   122.984] (II) Logitech HID compliant keyboard: Configuring as keyboard
[   122.984] (**) Logitech HID compliant keyboard: YAxisMapping: buttons 4 and 5
[   122.984] (**) Logitech HID compliant keyboard: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   122.984] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:10.1/usb3/3-2/3-2:1.1/input/input4/event4"
[   122.984] (II) XINPUT: Adding extended input device "Logitech HID compliant keyboard" (type: KEYBOARD)
[   122.984] (**) Option "xkb_rules" "evdev"
[   122.984] (**) Option "xkb_model" "pc105"
[   122.984] (**) Option "xkb_layout" "fr"
[   122.984] (**) Option "xkb_variant" "oss"
[   122.988] (II) config/udev: Adding input device ImExPS/2 Logitech Explorer Mouse (/dev/input/event5)
[   122.988] (**) ImExPS/2 Logitech Explorer Mouse: Applying InputClass "evdev pointer catchall"
[   122.988] (II) Using input driver 'evdev' for 'ImExPS/2 Logitech Explorer Mouse'
[   122.988] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   122.988] (**) ImExPS/2 Logitech Explorer Mouse: always reports core events
[   122.988] (**) ImExPS/2 Logitech Explorer Mouse: Device: "/dev/input/event5"
[   123.000] (--) ImExPS/2 Logitech Explorer Mouse: Found 9 mouse buttons
[   123.000] (--) ImExPS/2 Logitech Explorer Mouse: Found scroll wheel(s)
[   123.000] (--) ImExPS/2 Logitech Explorer Mouse: Found relative axes
[   123.000] (--) ImExPS/2 Logitech Explorer Mouse: Found x and y relative axes
[   123.000] (II) ImExPS/2 Logitech Explorer Mouse: Configuring as mouse
[   123.000] (II) ImExPS/2 Logitech Explorer Mouse: Adding scrollwheel support
[   123.000] (**) ImExPS/2 Logitech Explorer Mouse: YAxisMapping: buttons 4 and 5
[   123.000] (**) ImExPS/2 Logitech Explorer Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   123.000] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input5/event5"
[   123.000] (II) XINPUT: Adding extended input device "ImExPS/2 Logitech Explorer Mouse" (type: MOUSE)
[   123.000] (II) ImExPS/2 Logitech Explorer Mouse: initialized for relative axes.
[   123.000] (**) ImExPS/2 Logitech Explorer Mouse: (accel) keeping acceleration scheme 1
[   123.000] (**) ImExPS/2 Logitech Explorer Mouse: (accel) acceleration profile 0
[   123.000] (**) ImExPS/2 Logitech Explorer Mouse: (accel) acceleration factor: 2.000
[   123.000] (**) ImExPS/2 Logitech Explorer Mouse: (accel) acceleration threshold: 4
[   123.000] (II) config/udev: Adding input device ImExPS/2 Logitech Explorer Mouse (/dev/input/mouse0)
[   123.000] (II) No input driver/identifier specified (ignoring)
[   123.110] (II) RADEON(0): EDID vendor "BNQ", prod id 30421
[   123.111] (II) RADEON(0): Using EDID range info for horizontal sync
[   123.111] (II) RADEON(0): Using EDID range info for vertical refresh
[   123.111] (II) RADEON(0): Printing DDC gathered Modelines:
[   123.111] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   123.111] (II) RADEON(0): Modeline "640x350"x0.0   25.17  640 656 752 800  350 387 389 449 +hsync -vsync (31.5 kHz)
[   123.111] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   123.111] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   123.111] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[   123.111] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[   123.111] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   123.111] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   123.111] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   123.111] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   123.111] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[   123.111] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   123.111] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   123.111] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   123.111] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[   123.111] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   123.111] (II) RADEON(0): Modeline "1280x1024"x72.0  132.75  1280 1368 1504 1728  1024 1025 1028 1067 -hsync +vsync (76.8 kHz)
[   123.402] (II) RADEON(0): EDID vendor "BNQ", prod id 30421
[   123.402] (II) RADEON(0): Using hsync ranges from config file
[   123.403] (II) RADEON(0): Using vrefresh ranges from config file
[   123.403] (II) RADEON(0): Printing DDC gathered Modelines:
[   123.403] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   123.403] (II) RADEON(0): Modeline "640x350"x0.0   25.17  640 656 752 800  350 387 389 449 +hsync -vsync (31.5 kHz)
[   123.403] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   123.403] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   123.403] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[   123.403] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[   123.403] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   123.403] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   123.403] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   123.403] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   123.403] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[   123.403] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   123.403] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   123.403] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   123.403] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[   123.403] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   123.403] (II) RADEON(0): Modeline "1280x1024"x72.0  132.75  1280 1368 1504 1728  1024 1025 1028 1067 -hsync +vsync (76.8 kHz)
[   123.478] (II) RADEON(0): EDID vendor "BNQ", prod id 30421
[   123.478] (II) RADEON(0): Using hsync ranges from config file
[   123.478] (II) RADEON(0): Using vrefresh ranges from config file
[   123.478] (II) RADEON(0): Printing DDC gathered Modelines:
[   123.478] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   123.478] (II) RADEON(0): Modeline "640x350"x0.0   25.17  640 656 752 800  350 387 389 449 +hsync -vsync (31.5 kHz)
[   123.478] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   123.479] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   123.479] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[   123.479] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[   123.479] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   123.479] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   123.479] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   123.479] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   123.479] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[   123.479] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   123.479] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   123.479] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   123.479] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[   123.479] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   123.479] (II) RADEON(0): Modeline "1280x1024"x72.0  132.75  1280 1368 1504 1728  1024 1025 1028 1067 -hsync +vsync (76.8 kHz)
[   123.554] (II) RADEON(0): EDID vendor "BNQ", prod id 30421
[   123.554] (II) RADEON(0): Using hsync ranges from config file
[   123.554] (II) RADEON(0): Using vrefresh ranges from config file
[   123.554] (II) RADEON(0): Printing DDC gathered Modelines:
[   123.554] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   123.554] (II) RADEON(0): Modeline "640x350"x0.0   25.17  640 656 752 800  350 387 389 449 +hsync -vsync (31.5 kHz)
[   123.554] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   123.555] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   123.555] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[   123.555] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[   123.555] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   123.555] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   123.555] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   123.555] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   123.555] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[   123.555] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   123.555] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   123.555] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   123.555] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[   123.555] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   123.555] (II) RADEON(0): Modeline "1280x1024"x72.0  132.75  1280 1368 1504 1728  1024 1025 1028 1067 -hsync +vsync (76.8 kHz)
[   123.630] (II) RADEON(0): EDID vendor "BNQ", prod id 30421
[   123.630] (II) RADEON(0): Using hsync ranges from config file
[   123.630] (II) RADEON(0): Using vrefresh ranges from config file
[   123.631] (II) RADEON(0): Printing DDC gathered Modelines:
[   123.631] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   123.631] (II) RADEON(0): Modeline "640x350"x0.0   25.17  640 656 752 800  350 387 389 449 +hsync -vsync (31.5 kHz)
[   123.631] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   123.631] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   123.631] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[   123.631] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[   123.631] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   123.631] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   123.631] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   123.631] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   123.631] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[   123.631] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   123.631] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   123.631] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   123.631] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[   123.631] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   123.631] (II) RADEON(0): Modeline "1280x1024"x72.0  132.75  1280 1368 1504 1728  1024 1025 1028 1067 -hsync +vsync (76.8 kHz)
[   134.874] (II) RADEON(0): EDID vendor "BNQ", prod id 30421
[   134.874] (II) RADEON(0): Using hsync ranges from config file
[   134.874] (II) RADEON(0): Using vrefresh ranges from config file
[   134.874] (II) RADEON(0): Printing DDC gathered Modelines:
[   134.874] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   134.875] (II) RADEON(0): Modeline "640x350"x0.0   25.17  640 656 752 800  350 387 389 449 +hsync -vsync (31.5 kHz)
[   134.875] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   134.875] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   134.875] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[   134.875] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[   134.875] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   134.875] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   134.875] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   134.875] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   134.875] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[   134.875] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   134.875] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   134.875] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   134.875] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[   134.875] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   134.875] (II) RADEON(0): Modeline "1280x1024"x72.0  132.75  1280 1368 1504 1728  1024 1025 1028 1067 -hsync +vsync (76.8 kHz)
[   134.950] (II) RADEON(0): EDID vendor "BNQ", prod id 30421
[   134.950] (II) RADEON(0): Using hsync ranges from config file
[   134.950] (II) RADEON(0): Using vrefresh ranges from config file
[   134.950] (II) RADEON(0): Printing DDC gathered Modelines:
[   134.950] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   134.950] (II) RADEON(0): Modeline "640x350"x0.0   25.17  640 656 752 800  350 387 389 449 +hsync -vsync (31.5 kHz)
[   134.951] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   134.951] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   134.951] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[   134.951] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[   134.951] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   134.951] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   134.951] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   134.951] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   134.951] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[   134.951] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   134.951] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   134.951] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   134.951] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[   134.951] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   134.951] (II) RADEON(0): Modeline "1280x1024"x72.0  132.75  1280 1368 1504 1728  1024 1025 1028 1067 -hsync +vsync (76.8 kHz)
[   135.027] (II) RADEON(0): EDID vendor "BNQ", prod id 30421
[   135.027] (II) RADEON(0): Using hsync ranges from config file
[   135.027] (II) RADEON(0): Using vrefresh ranges from config file
[   135.027] (II) RADEON(0): Printing DDC gathered Modelines:
[   135.027] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   135.027] (II) RADEON(0): Modeline "640x350"x0.0   25.17  640 656 752 800  350 387 389 449 +hsync -vsync (31.5 kHz)
[   135.027] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   135.027] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   135.027] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[   135.027] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[   135.027] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   135.027] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   135.027] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   135.027] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   135.027] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[   135.027] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   135.027] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   135.027] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   135.027] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[   135.027] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   135.027] (II) RADEON(0): Modeline "1280x1024"x72.0  132.75  1280 1368 1504 1728  1024 1025 1028 1067 -hsync +vsync (76.8 kHz)
[   135.102] (II) RADEON(0): EDID vendor "BNQ", prod id 30421
[   135.102] (II) RADEON(0): Using hsync ranges from config file
[   135.102] (II) RADEON(0): Using vrefresh ranges from config file
[   135.102] (II) RADEON(0): Printing DDC gathered Modelines:
[   135.102] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   135.103] (II) RADEON(0): Modeline "640x350"x0.0   25.17  640 656 752 800  350 387 389 449 +hsync -vsync (31.5 kHz)
[   135.103] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   135.103] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   135.103] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[   135.103] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[   135.103] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   135.103] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   135.103] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   135.103] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   135.103] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[   135.103] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   135.103] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   135.103] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   135.103] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[   135.103] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   135.103] (II) RADEON(0): Modeline "1280x1024"x72.0  132.75  1280 1368 1504 1728  1024 1025 1028 1067 -hsync +vsync (76.8 kHz)
[   140.275] (II) RADEON(0): EDID vendor "BNQ", prod id 30421
[   140.275] (II) RADEON(0): Using hsync ranges from config file
[   140.275] (II) RADEON(0): Using vrefresh ranges from config file
[   140.275] (II) RADEON(0): Printing DDC gathered Modelines:
[   140.275] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   140.275] (II) RADEON(0): Modeline "640x350"x0.0   25.17  640 656 752 800  350 387 389 449 +hsync -vsync (31.5 kHz)
[   140.275] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   140.275] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   140.275] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[   140.275] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[   140.275] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   140.275] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   140.275] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   140.275] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   140.275] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[   140.275] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   140.275] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   140.275] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   140.275] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[   140.275] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   140.275] (II) RADEON(0): Modeline "1280x1024"x72.0  132.75  1280 1368 1504 1728  1024 1025 1028 1067 -hsync +vsync (76.8 kHz)
```

---

### Post by mastablasta on 2011-07-14
> **Sinner said:**
> Hi all,
 
Since I upgraded from 10.10 to 11.04, I have lost 3d acceleration and so have no unity (default session).
I own an ATI radeon 4350 (rv710) gfx card.
 

 
assuming you were are using proprietary drivers for the card, did you First uninstall the drivers under 10.10, upgrade the OS and then install new ones? 
 
if not then that is what you need to do. purge the old drivers and isntall new ones.
 
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

---

### Post by Sinner on 2011-07-14
Hi,

Already done this. I've just done it again > no success.

Then I inslalled the fglrx from system > additional driver menu.
> no success either.

Still get the wallpaper and pointer with nothing else on the screen with Ubuntu session. The gfx display is very slow.

glxgears display the gears but nothing is moving...


here is X log after all of that:
```

[    85.170] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    85.170] X Protocol Version 11, Revision 0
[    85.170] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[    85.170] Current Operating System: Linux desktop 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686
[    85.170] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=0c21be46-cdbf-4834-bca4-f2ae56eec59a ro quiet splash vt.handoff=7
[    85.170] Build Date: 21 May 2011  11:38:35AM
[    85.170] xorg-server 2:1.10.1-1ubuntu1.1 (For technical support please see http://www.ubuntu.com/support) 
[    85.170] Current version of pixman: 0.20.2
[    85.170] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    85.170] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    85.170] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Jul 14 11:38:57 2011
[    85.170] (==) Using config file: "/etc/X11/xorg.conf"
[    85.170] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    85.170] (==) No Layout section.  Using the first Screen section.
[    85.170] (**) |-->Screen "Default Screen" (0)
[    85.170] (**) |   |-->Monitor "<default monitor>"
[    85.171] (==) No monitor specified for screen "Default Screen".
	Using a default monitor configuration.
[    85.171] (==) Automatically adding devices
[    85.171] (==) Automatically enabling devices
[    85.171] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    85.171] 	Entry deleted from font path.
[    85.171] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    85.171] 	Entry deleted from font path.
[    85.171] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    85.171] 	Entry deleted from font path.
[    85.171] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    85.171] 	Entry deleted from font path.
[    85.171] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    85.171] 	Entry deleted from font path.
[    85.171] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    85.171] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    85.171] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    85.171] (II) Loader magic: 0x81ffde0
[    85.171] (II) Module ABI versions:
[    85.171] 	X.Org ANSI C Emulation: 0.4
[    85.171] 	X.Org Video Driver: 10.0
[    85.171] 	X.Org XInput driver : 12.3
[    85.171] 	X.Org Server Extension : 5.0
[    85.175] (--) PCI:*(0:2:0:0) 1002:954f:1043:02a8 rev 0, Mem @ 0xd0000000/268435456, 0xfeae0000/65536, I/O @ 0x0000e000/256, BIOS @ 0x????????/131072
[    85.175] (II) Open ACPI successful (/var/run/acpid.socket)
[    85.175] (II) "extmod" will be loaded by default.
[    85.175] (II) "dbe" will be loaded by default.
[    85.175] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    85.175] (II) "record" will be loaded by default.
[    85.175] (II) "dri" will be loaded by default.
[    85.175] (II) "dri2" will be loaded by default.
[    85.175] (II) LoadModule: "glx"
[    85.176] (II) Loading /usr/lib/xorg/extra-modules/modules/extensions/libglx.so
[    85.176] (II) Module glx: vendor="FireGL - ATI Technologies Inc."
[    85.176] 	compiled for 6.9.0, module version = 1.0.0
[    85.176] (II) Loading extension GLX
[    85.176] (II) LoadModule: "extmod"
[    85.177] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    85.177] (II) Module extmod: vendor="X.Org Foundation"
[    85.177] 	compiled for 1.10.1, module version = 1.0.0
[    85.177] 	Module class: X.Org Server Extension
[    85.177] 	ABI class: X.Org Server Extension, version 5.0
[    85.177] (II) Loading extension MIT-SCREEN-SAVER
[    85.177] (II) Loading extension XFree86-VidModeExtension
[    85.177] (II) Loading extension XFree86-DGA
[    85.177] (II) Loading extension DPMS
[    85.177] (II) Loading extension XVideo
[    85.177] (II) Loading extension XVideo-MotionCompensation
[    85.177] (II) Loading extension X-Resource
[    85.177] (II) LoadModule: "dbe"
[    85.178] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    85.178] (II) Module dbe: vendor="X.Org Foundation"
[    85.178] 	compiled for 1.10.1, module version = 1.0.0
[    85.178] 	Module class: X.Org Server Extension
[    85.178] 	ABI class: X.Org Server Extension, version 5.0
[    85.178] (II) Loading extension DOUBLE-BUFFER
[    85.178] (II) LoadModule: "record"
[    85.179] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    85.179] (II) Module record: vendor="X.Org Foundation"
[    85.179] 	compiled for 1.10.1, module version = 1.13.0
[    85.179] 	Module class: X.Org Server Extension
[    85.179] 	ABI class: X.Org Server Extension, version 5.0
[    85.179] (II) Loading extension RECORD
[    85.179] (II) LoadModule: "dri"
[    85.179] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    85.180] (II) Module dri: vendor="X.Org Foundation"
[    85.180] 	compiled for 1.10.1, module version = 1.0.0
[    85.180] 	ABI class: X.Org Server Extension, version 5.0
[    85.180] (II) Loading extension XFree86-DRI
[    85.180] (II) LoadModule: "dri2"
[    85.180] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    85.180] (II) Module dri2: vendor="X.Org Foundation"
[    85.180] 	compiled for 1.10.1, module version = 1.2.0
[    85.180] 	ABI class: X.Org Server Extension, version 5.0
[    85.180] (II) Loading extension DRI2
[    85.181] (==) Matched fglrx as autoconfigured driver 0
[    85.181] (==) Matched ati as autoconfigured driver 1
[    85.181] (==) Matched vesa as autoconfigured driver 2
[    85.181] (==) Matched fbdev as autoconfigured driver 3
[    85.181] (==) Assigned the driver to the xf86ConfigLayout
[    85.181] (II) LoadModule: "fglrx"
[    85.181] (II) Loading /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so
[    85.208] (II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
[    85.208] 	compiled for 1.4.99.906, module version = 8.84.60
[    85.208] 	Module class: X.Org Video Driver
[    85.209] (II) Loading sub module "fglrxdrm"
[    85.209] (II) LoadModule: "fglrxdrm"
[    85.209] (II) Loading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    85.209] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[    85.209] 	compiled for 1.4.99.906, module version = 8.84.60
[    85.209] (II) LoadModule: "ati"
[    85.209] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    85.210] (II) Module ati: vendor="X.Org Foundation"
[    85.210] 	compiled for 1.10.1, module version = 6.14.0
[    85.210] 	Module class: X.Org Video Driver
[    85.210] 	ABI class: X.Org Video Driver, version 10.0
[    85.210] (II) LoadModule: "radeon"
[    85.210] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    85.211] (II) Module radeon: vendor="X.Org Foundation"
[    85.211] 	compiled for 1.10.1, module version = 6.14.0
[    85.211] 	Module class: X.Org Video Driver
[    85.211] 	ABI class: X.Org Video Driver, version 10.0
[    85.211] (II) LoadModule: "vesa"
[    85.211] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    85.211] (II) Module vesa: vendor="X.Org Foundation"
[    85.211] 	compiled for 1.10.0, module version = 2.3.0
[    85.211] 	Module class: X.Org Video Driver
[    85.211] 	ABI class: X.Org Video Driver, version 10.0
[    85.211] (II) LoadModule: "fbdev"
[    85.212] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    85.212] (II) Module fbdev: vendor="X.Org Foundation"
[    85.212] 	compiled for 1.10.0, module version = 0.4.2
[    85.212] 	ABI class: X.Org Video Driver, version 10.0
[    85.212] (II) ATI Proprietary Linux Driver Version Identifier:8.84.60
[    85.212] (II) ATI Proprietary Linux Driver Release Identifier: 8.84.6                               
[    85.212] (II) ATI Proprietary Linux Driver Build Date: Mar 24 2011 19:27:41
[    85.212] (II) RADEON: Driver for ATI Radeon chipsets:
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
	ATI Radeon HD 5450, CEDAR, AMD Radeon HD 6900M Series,
	Mobility Radeon HD 6000 Series, BARTS, BARTS,
	Mobility Radeon HD 6000 Series, Mobility Radeon HD 6000 Series,
	BARTS, BARTS, BARTS, BARTS, AMD Radeon HD 6800 Series,
	AMD Radeon HD 6800 Series, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
	TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, CAICOS, CAICOS,
	CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
	CAICOS
[    85.220] (II) VESA: driver for VESA chipsets: vesa
[    85.220] (II) FBDEV: driver for framebuffer: fbdev
[    85.220] (--) using VT number 8

[    85.349] (WW) Falling back to old probe method for fglrx
[    85.357] (II) Loading PCS database from /etc/ati/amdpcsdb
[    85.358] (--) Assigning device section with no busID to primary device
[    85.358] (--) Chipset Supported AMD Graphics Processor (0x954F) found
[    85.358] (WW) fglrx: No matching Device section for instance (BusID PCI:0@2:0:1) found
[    85.358] (II) AMD Video driver is running on a device belonging to a group targeted for this release
[    85.358] (II) AMD Video driver is signed
[    85.359] (II) Loading /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so
[    85.359] (II) Loading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    85.359] (II) fglrx(0): pEnt->device->identifier=0x81ec828
[    85.359] (WW) Falling back to old probe method for vesa
[    85.359] (WW) Falling back to old probe method for fbdev
[    85.359] (II) Loading sub module "fbdevhw"
[    85.359] (II) LoadModule: "fbdevhw"
[    85.359] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    85.360] (II) Module fbdevhw: vendor="X.Org Foundation"
[    85.360] 	compiled for 1.10.1, module version = 0.0.2
[    85.360] 	ABI class: X.Org Video Driver, version 10.0
[    85.360] (II) fglrx(0): === [xdl_xs110_atiddxPreInit] === begin
[    85.360] (II) Loading sub module "vgahw"
[    85.360] (II) LoadModule: "vgahw"
[    85.360] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    85.360] (II) Module vgahw: vendor="X.Org Foundation"
[    85.361] 	compiled for 1.10.1, module version = 0.1.0
[    85.361] 	ABI class: X.Org Video Driver, version 10.0
[    85.361] (II) fglrx(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
[    85.361] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[    85.361] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    85.361] (==) fglrx(0): Default visual is TrueColor
[    85.361] (==) fglrx(0): RGB weight 888
[    85.361] (II) fglrx(0): Using 8 bits per RGB 
[    85.361] (==) fglrx(0): Buffer Tiling is ON
[    85.361] (II) Loading sub module "fglrxdrm"
[    85.361] (II) LoadModule: "fglrxdrm"
[    85.361] (II) Loading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    85.361] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[    85.361] 	compiled for 1.4.99.906, module version = 8.84.60
[    85.363] ukiDynamicMajor: found major device number 250
[    85.363] ukiDynamicMajor: found major device number 250
[    85.363] ukiOpenByBusid: Searching for BusID PCI:2:0:0
[    85.363] ukiOpenDevice: node name is /dev/ati/card0
[    85.363] ukiOpenDevice: open result is 11, (OK)
[    85.364] ukiOpenByBusid: ukiOpenMinor returns 11
[    85.364] ukiOpenByBusid: ukiGetBusid reports PCI:2:0:0
[    85.364] (==) fglrx(0): NoAccel = NO
[    85.364] (==) fglrx(0): ATI 2D Acceleration Architecture enabled
[    85.364] (--) fglrx(0): Chipset: "ATI Radeon HD 4300/4500 Series" (Chipset = 0x954f)
[    85.364] (--) fglrx(0): (PciSubVendor = 0x1043, PciSubDevice = 0x02a8)
[    85.364] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
[    85.364] (--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
[    85.364] (--) fglrx(0): MMIO registers at 0xfeae0000
[    85.364] (--) fglrx(0): I/O port at 0x0000e000
[    85.364] (==) fglrx(0): ROM-BIOS at 0x000c0000
[    85.366] (II) fglrx(0): AC Adapter is used
[    85.377] (II) fglrx(0): Primary V_BIOS segment is: 0xc000
[    85.378] (II) Loading sub module "vbe"
[    85.378] (II) LoadModule: "vbe"
[    85.379] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    85.379] (II) Module vbe: vendor="X.Org Foundation"
[    85.379] 	compiled for 1.10.1, module version = 1.1.0
[    85.379] 	ABI class: X.Org Video Driver, version 10.0
[    85.380] (II) fglrx(0): VESA BIOS detected
[    85.380] (II) fglrx(0): VESA VBE Version 3.0
[    85.380] (II) fglrx(0): VESA VBE Total Mem: 16384 kB
[    85.380] (II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
[    85.380] (II) fglrx(0): VESA VBE OEM Software Rev: 11.20
[    85.380] (II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
[    85.380] (II) fglrx(0): VESA VBE OEM Product: RV710
[    85.380] (II) fglrx(0): VESA VBE OEM Product Rev: 01.00
[    85.412] (II) fglrx(0): ATI Video BIOS revision 9 or later detected
[    85.412] (--) fglrx(0): Video RAM: 524288 kByte, Type: DDR2
[    85.412] (II) fglrx(0): PCIE card detected
[    85.412] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
[    85.412] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[    85.414] (II) fglrx(0): Using adapter: 2:0.0.
[    85.415] (II) fglrx(0): [FB] MC range(MCFBBase = 0xf00000000, MCFBSize = 0x20000000)
[    85.416] (II) fglrx(0): Interrupt handler installed at IRQ 66.
[    85.417] (II) fglrx(0): RandR 1.2 support is enabled!
[    85.417] (II) fglrx(0): RandR 1.2 rotation support is enabled!
[    85.417] (==) fglrx(0): Center Mode is disabled 
[    85.417] (II) Loading sub module "fb"
[    85.417] (II) LoadModule: "fb"
[    85.417] (II) Loading /usr/lib/xorg/modules/libfb.so
[    85.417] (II) Module fb: vendor="X.Org Foundation"
[    85.418] 	compiled for 1.10.1, module version = 1.0.0
[    85.418] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    85.418] (II) Loading sub module "ddc"
[    85.418] (II) LoadModule: "ddc"
[    85.418] (II) Module "ddc" already built-in
[    85.891] (II) fglrx(0): Finished Initialize PPLIB!
[    85.894] (II) fglrx(0): Output DFP1 has no monitor section
[    85.894] (II) fglrx(0): Output DFP2 has no monitor section
[    85.894] (II) fglrx(0): Output CRT1 has no monitor section
[    85.894] (II) fglrx(0): Output CRT2 has no monitor section
[    85.894] (II) Loading sub module "ddc"
[    85.894] (II) LoadModule: "ddc"
[    85.894] (II) Module "ddc" already built-in
[    85.894] (II) fglrx(0): Connected Display0: DFP2
[    85.894] (II) fglrx(0): Display0 EDID data ---------------------------
[    85.894] (II) fglrx(0): Manufacturer: BNQ  Model: 76d5  Serial#: 1866
[    85.894] (II) fglrx(0): Year: 2006  Week: 37
[    85.894] (II) fglrx(0): EDID Version: 1.3
[    85.894] (II) fglrx(0): Digital Display Input
[    85.894] (II) fglrx(0): Max Image Size [cm]: horiz.: 38  vert.: 30
[    85.894] (II) fglrx(0): Gamma: 2.20
[    85.894] (II) fglrx(0): DPMS capabilities: StandBy Suspend Off
[    85.894] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    85.894] (II) fglrx(0): First detailed timing is preferred mode
[    85.894] (II) fglrx(0): redX: 0.640 redY: 0.340   greenX: 0.290 greenY: 0.610
[    85.894] (II) fglrx(0): blueX: 0.140 blueY: 0.070   whiteX: 0.310 whiteY: 0.330
[    85.894] (II) fglrx(0): Supported established timings:
[    85.894] (II) fglrx(0): 720x400@70Hz
[    85.894] (II) fglrx(0): 640x480@60Hz
[    85.894] (II) fglrx(0): 640x480@67Hz
[    85.894] (II) fglrx(0): 640x480@72Hz
[    85.894] (II) fglrx(0): 640x480@75Hz
[    85.894] (II) fglrx(0): 800x600@60Hz
[    85.894] (II) fglrx(0): 800x600@72Hz
[    85.894] (II) fglrx(0): 800x600@75Hz
[    85.894] (II) fglrx(0): 832x624@75Hz
[    85.894] (II) fglrx(0): 1024x768@60Hz
[    85.894] (II) fglrx(0): 1024x768@70Hz
[    85.894] (II) fglrx(0): 1024x768@75Hz
[    85.894] (II) fglrx(0): 1280x1024@75Hz
[    85.894] (II) fglrx(0): 1152x864@75Hz
[    85.894] (II) fglrx(0): Manufacturer's mask: 0
[    85.894] (II) fglrx(0): Supported standard timings:
[    85.894] (II) fglrx(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    85.894] (II) fglrx(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    85.894] (II) fglrx(0): #2: hsize: 1280  vsize 1024  refresh: 72  vid: 35969
[    85.894] (II) fglrx(0): Supported detailed timing:
[    85.894] (II) fglrx(0): clock: 108.0 MHz   Image Size:  376 x 301 mm
[    85.894] (II) fglrx(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
[    85.894] (II) fglrx(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[    85.894] (II) fglrx(0): Supported detailed timing:
[    85.894] (II) fglrx(0): clock: 25.2 MHz   Image Size:  376 x 301 mm
[    85.894] (II) fglrx(0): h_active: 640  h_sync: 656  h_sync_end 752 h_blank_end 800 h_border: 0
[    85.895] (II) fglrx(0): v_active: 350  v_sync: 387  v_sync_end 389 v_blanking: 449 v_border: 0
[    85.895] (II) fglrx(0): Ranges: V min: 56 V max: 76 Hz, H min: 31 H max: 83 kHz, PixClock max 145 MHz
[    85.895] (II) fglrx(0): Monitor name: BenQ FP93GX
[    85.895] (II) fglrx(0): EDID (in hex):
[    85.895] (II) fglrx(0): 	00ffffffffffff0009d1d5764a070000
[    85.895] (II) fglrx(0): 	2510010380261e78eac5c6a3574a9c23
[    85.895] (II) fglrx(0): 	124f54bdef80714f8180818c01010101
[    85.895] (II) fglrx(0): 	010101010101302a009851002a403070
[    85.895] (II) fglrx(0): 	1300782d1100001ed50980a0205e6310
[    85.895] (II) fglrx(0): 	10605208782d1100001a000000fd0038
[    85.895] (II) fglrx(0): 	4c1f530e000a202020202020000000fc
[    85.895] (II) fglrx(0): 	0042656e51204650393347580a200015
[    85.895] (II) fglrx(0): End of Display0 EDID data --------------------
[    86.028] (II) fglrx(0): EDID for output DFP1
[    86.028] (II) fglrx(0): EDID for output DFP2
[    86.028] (II) fglrx(0): Manufacturer: BNQ  Model: 76d5  Serial#: 1866
[    86.028] (II) fglrx(0): Year: 2006  Week: 37
[    86.028] (II) fglrx(0): EDID Version: 1.3
[    86.028] (II) fglrx(0): Digital Display Input
[    86.028] (II) fglrx(0): Max Image Size [cm]: horiz.: 38  vert.: 30
[    86.028] (II) fglrx(0): Gamma: 2.20
[    86.028] (II) fglrx(0): DPMS capabilities: StandBy Suspend Off
[    86.028] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    86.028] (II) fglrx(0): First detailed timing is preferred mode
[    86.028] (II) fglrx(0): redX: 0.640 redY: 0.340   greenX: 0.290 greenY: 0.610
[    86.028] (II) fglrx(0): blueX: 0.140 blueY: 0.070   whiteX: 0.310 whiteY: 0.330
[    86.028] (II) fglrx(0): Supported established timings:
[    86.028] (II) fglrx(0): 720x400@70Hz
[    86.029] (II) fglrx(0): 640x480@60Hz
[    86.029] (II) fglrx(0): 640x480@67Hz
[    86.029] (II) fglrx(0): 640x480@72Hz
[    86.029] (II) fglrx(0): 640x480@75Hz
[    86.029] (II) fglrx(0): 800x600@60Hz
[    86.029] (II) fglrx(0): 800x600@72Hz
[    86.029] (II) fglrx(0): 800x600@75Hz
[    86.029] (II) fglrx(0): 832x624@75Hz
[    86.029] (II) fglrx(0): 1024x768@60Hz
[    86.029] (II) fglrx(0): 1024x768@70Hz
[    86.029] (II) fglrx(0): 1024x768@75Hz
[    86.029] (II) fglrx(0): 1280x1024@75Hz
[    86.029] (II) fglrx(0): 1152x864@75Hz
[    86.029] (II) fglrx(0): Manufacturer's mask: 0
[    86.029] (II) fglrx(0): Supported standard timings:
[    86.029] (II) fglrx(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    86.029] (II) fglrx(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    86.029] (II) fglrx(0): #2: hsize: 1280  vsize 1024  refresh: 72  vid: 35969
[    86.029] (II) fglrx(0): Supported detailed timing:
[    86.029] (II) fglrx(0): clock: 108.0 MHz   Image Size:  376 x 301 mm
[    86.029] (II) fglrx(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
[    86.029] (II) fglrx(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[    86.029] (II) fglrx(0): Supported detailed timing:
[    86.029] (II) fglrx(0): clock: 25.2 MHz   Image Size:  376 x 301 mm
[    86.029] (II) fglrx(0): h_active: 640  h_sync: 656  h_sync_end 752 h_blank_end 800 h_border: 0
[    86.029] (II) fglrx(0): v_active: 350  v_sync: 387  v_sync_end 389 v_blanking: 449 v_border: 0
[    86.029] (II) fglrx(0): Ranges: V min: 56 V max: 76 Hz, H min: 31 H max: 83 kHz, PixClock max 145 MHz
[    86.029] (II) fglrx(0): Monitor name: BenQ FP93GX
[    86.029] (II) fglrx(0): EDID (in hex):
[    86.029] (II) fglrx(0): 	00000000782830293a20454449442028
[    86.029] (II) fglrx(0): 	696e20686578293a0a0020204d6f6465
[    86.029] (II) fglrx(0): 	6c3a2025410000000000000078283029
[    86.029] (II) fglrx(0): 	3a2046697273742064657461696c6564
[    86.029] (II) fglrx(0): 	2074696d696e67206973207072656665
[    86.029] (II) fglrx(0): 	72726564206d6f64650a000a00fd0038
[    86.029] (II) fglrx(0): 	4c1f530e390000000000000078283029
[    86.029] (II) fglrx(0): 	3a20537570706f727465642064657461
[    86.029] (II) fglrx(0): Printing probed modes for output DFP2
[    86.029] (II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 -hsync -vsync (64.0 kHz)
[    86.029] (II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 -hsync -vsync (60.0 kHz)
[    86.029] (II) fglrx(0): Modeline "1280x800"x60.0   83.46  1280 1344 1480 1680  800 801 804 828 +hsync -vsync (49.7 kHz)
[    86.029] (II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 +hsync -vsync (53.7 kHz)
[    86.029] (II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 +hsync -vsync (47.8 kHz)
[    86.029] (II) fglrx(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 -hsync -vsync (45.0 kHz)
[    86.029] (II) fglrx(0): Modeline "1152x648"x60.0   59.90  1152 1200 1320 1488  648 649 652 671 +hsync -vsync (40.3 kHz)
[    86.029] (II) fglrx(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 -hsync -vsync (80.0 kHz)
[    86.029] (II) fglrx(0): Modeline "1280x960"x75.0  129.86  1280 1368 1504 1728  960 961 964 1002 +hsync -vsync (75.2 kHz)
[    86.029] (II) fglrx(0): Modeline "1280x800"x75.0  107.21  1280 1360 1496 1712  800 801 804 835 +hsync -vsync (62.6 kHz)
[    86.029] (II) fglrx(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 -hsync -vsync (67.5 kHz)
[    86.029] (II) fglrx(0): Modeline "1280x768"x75.0  102.25  1280 1360 1488 1696  768 771 778 805 +hsync -vsync (60.3 kHz)
[    86.029] (II) fglrx(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 -hsync -vsync (60.0 kHz)
[    86.029] (II) fglrx(0): Modeline "1024x768"x70.0   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync (56.5 kHz)
[    86.029] (II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync (48.4 kHz)
[    86.029] (II) fglrx(0): Modeline "800x600"x72.0   50.00  800 856 976 1040  600 637 643 666 -hsync -vsync (48.1 kHz)
[    86.030] (II) fglrx(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 -hsync -vsync (46.9 kHz)
[    86.030] (II) fglrx(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 +hsync -vsync (43.8 kHz)
[    86.030] (II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 -hsync -vsync (37.9 kHz)
[    86.030] (II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 +hsync -vsync (29.8 kHz)
[    86.030] (II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 +hsync +vsync (37.5 kHz)
[    86.030] (II) fglrx(0): Modeline "640x480"x72.0   31.50  640 656 696 832  480 481 484 520 +hsync +vsync (37.9 kHz)
[    86.030] (II) fglrx(0): Modeline "640x480"x60.0   25.18  640 648 744 800  480 482 484 525 +hsync +vsync (31.5 kHz)
[    86.030] (II) fglrx(0): EDID for output CRT1
[    86.030] (II) fglrx(0): EDID for output CRT2
[    86.030] (II) fglrx(0): Output DFP1 disconnected
[    86.030] (II) fglrx(0): Output DFP2 connected
[    86.030] (II) fglrx(0): Output CRT1 disconnected
[    86.030] (II) fglrx(0): Output CRT2 disconnected
[    86.030] (II) fglrx(0): Using exact sizes for initial modes
[    86.030] (II) fglrx(0): Output DFP2 using initial mode 1280x1024
[    86.030] (II) fglrx(0): DPI set to (96, 96)
[    86.030] (II) fglrx(0): Adapter ATI Radeon HD 4300/4500 Series has 2 configurable heads and 1 displays connected.
[    86.030] (==) fglrx(0):  PseudoColor visuals disabled
[    86.030] (II) Loading sub module "ramdac"
[    86.030] (II) LoadModule: "ramdac"
[    86.030] (II) Module "ramdac" already built-in
[    86.030] (==) fglrx(0): NoDRI = NO
[    86.030] (==) fglrx(0): Capabilities: 0x00000000
[    86.030] (==) fglrx(0): CapabilitiesEx: 0x00000000
[    86.030] (==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
[    86.030] (==) fglrx(0): UseFastTLS=0
[    86.030] (==) fglrx(0): BlockSignalsOnLock=1
[    86.030] (II) UnloadModule: "radeon"
[    86.030] (II) Unloading radeon
[    86.030] (II) UnloadModule: "vesa"
[    86.030] (II) Unloading vesa
[    86.030] (II) UnloadModule: "fbdev"
[    86.030] (II) Unloading fbdev
[    86.030] (II) UnloadModule: "fbdevhw"
[    86.030] (II) Unloading fbdevhw
[    86.030] (--) Depth 24 pixmap format is 32 bpp
[    86.030] (II) Loading extension ATIFGLRXDRI
[    86.031] (II) fglrx(0): doing swlDriScreenInit
[    86.031] (II) fglrx(0): swlDriScreenInit for fglrx driver
[    86.031] ukiDynamicMajor: found major device number 250
[    86.031] ukiDynamicMajor: found major device number 250
[    86.031] ukiDynamicMajor: found major device number 250
[    86.031] ukiOpenByBusid: Searching for BusID PCI:2:0:0
[    86.031] ukiOpenDevice: node name is /dev/ati/card0
[    86.031] ukiOpenDevice: open result is 16, (OK)
[    86.031] ukiOpenByBusid: ukiOpenMinor returns 16
[    86.031] ukiOpenByBusid: ukiGetBusid reports PCI:2:0:0
[    86.031] (II) fglrx(0): [uki] DRM interface version 1.0
[    86.031] (II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:2:0:0"
[    86.031] (II) fglrx(0): [uki] added 8192 byte SAREA at 0x2c2000
[    86.031] (II) fglrx(0): [uki] mapped SAREA 0x2c2000 to 0xb7712000
[    86.031] (II) fglrx(0): [uki] framebuffer handle = 0xd7000
[    86.031] (II) fglrx(0): [uki] added 1 reserved context for kernel
[    86.031] (II) fglrx(0): swlDriScreenInit done
[    86.031] (II) fglrx(0): Kernel Module Version Information:
[    86.031] (II) fglrx(0):     Name: fglrx
[    86.031] (II) fglrx(0):     Version: 8.84.60
[    86.031] (II) fglrx(0):     Date: Mar 24 2011
[    86.031] (II) fglrx(0):     Desc: ATI FireGL DRM kernel module
[    86.031] (II) fglrx(0): Kernel Module version matches driver.
[    86.031] (II) fglrx(0): Kernel Module Build Time Information:
[    86.031] (II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.38-8-generic
[    86.031] (II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
[    86.031] (II) fglrx(0):     Build-Kernel __SMP__:            yes
[    86.031] (II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
[    86.031] (II) fglrx(0): [uki] register handle = 0x000d8000
[    86.033] (II) fglrx(0): DRI initialization successfull
[    86.033] (II) fglrx(0): FBADPhys: 0xf00000000 FBMappedSize: 0x01004000
[    86.034] (==) fglrx(0): Backing store disabled
[    86.034] (II) Loading extension FGLRXEXTENSION
[    86.034] (==) fglrx(0): DPMS enabled
[    86.034] (II) fglrx(0): Initialized in-driver Xinerama extension
[    86.034] (**) fglrx(0): Textured Video is enabled.
[    86.034] (II) LoadModule: "glesx"
[    86.034] (II) Loading /usr/lib/xorg/extra-modules/modules/glesx.so
[    86.036] (II) Module glesx: vendor="X.Org Foundation"
[    86.036] 	compiled for 1.4.99.906, module version = 1.0.0
[    86.036] (II) Loading extension GLESX
[    86.036] (II) fglrx(0): GLESX enableFlags = 528
[    86.036] (II) fglrx(0): GLESX is enabled
[    86.036] (II) LoadModule: "amdxmm"
[    86.036] (II) Loading /usr/lib/xorg/extra-modules/modules/amdxmm.so
[    86.037] (II) Module amdxmm: vendor="X.Org Foundation"
[    86.037] 	compiled for 1.4.99.906, module version = 2.0.0
[    86.037] (II) Loading extension AMDXVOPL
[    86.037] (II) Loading extension AMDXVBA
[    86.039] (II) fglrx(0): UVD feature is enabled(II) fglrx(0): 
[    86.041] (II) fglrx(0): Enable composite support successfully
[    86.041] (II) fglrx(0): X context handle = 0x5
[    86.041] (II) fglrx(0): [DRI] installation complete
[    86.042] (==) fglrx(0): Silken mouse enabled
[    86.043] (==) fglrx(0): Using HW cursor of display infrastructure!
[    86.043] (II) fglrx(0): Disabling in-server RandR and enabling in-driver RandR 1.2.
[    86.638] (--) RandR disabled
[    86.638] (II) Initializing built-in extension Generic Event Extension
[    86.638] (II) Initializing built-in extension SHAPE
[    86.638] (II) Initializing built-in extension MIT-SHM
[    86.638] (II) Initializing built-in extension XInputExtension
[    86.638] (II) Initializing built-in extension XTEST
[    86.638] (II) Initializing built-in extension BIG-REQUESTS
[    86.638] (II) Initializing built-in extension SYNC
[    86.638] (II) Initializing built-in extension XKEYBOARD
[    86.638] (II) Initializing built-in extension XC-MISC
[    86.638] (II) Initializing built-in extension SECURITY
[    86.638] (II) Initializing built-in extension XINERAMA
[    86.638] (II) Initializing built-in extension XFIXES
[    86.638] (II) Initializing built-in extension RENDER
[    86.638] (II) Initializing built-in extension RANDR
[    86.638] (II) Initializing built-in extension COMPOSITE
[    86.638] (II) Initializing built-in extension DAMAGE
[    86.638] (II) Initializing built-in extension GESTURE
[    86.664] ukiDynamicMajor: found major device number 250
[    86.664] ukiDynamicMajor: found major device number 250
[    86.664] ukiOpenByBusid: Searching for BusID PCI:2:0:0
[    86.664] ukiOpenDevice: node name is /dev/ati/card0
[    86.664] ukiOpenDevice: open result is 18, (OK)
[    86.664] ukiOpenByBusid: ukiOpenMinor returns 18
[    86.664] ukiOpenByBusid: ukiGetBusid reports PCI:2:0:0
[    86.778] (II) AIGLX: Loaded and initialized OpenGL driver(II) GLX: Initialized DRI GL provider for screen 0
[    86.778] (II) fglrx(0): Enable the clock gating!
[    86.778] (II) fglrx(0): Setting screen physical size to 338 x 270
[    86.789] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    86.800] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    86.800] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    86.800] (II) LoadModule: "evdev"
[    86.801] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    86.801] (II) Module evdev: vendor="X.Org Foundation"
[    86.801] 	compiled for 1.10.0.902, module version = 2.6.0
[    86.801] 	Module class: X.Org XInput Driver
[    86.801] 	ABI class: X.Org XInput driver, version 12.3
[    86.801] (II) Using input driver 'evdev' for 'Power Button'
[    86.801] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    86.801] (**) Power Button: always reports core events
[    86.801] (**) Power Button: Device: "/dev/input/event2"
[    86.820] (--) Power Button: Found keys
[    86.820] (II) Power Button: Configuring as keyboard
[    86.820] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    86.820] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    86.820] (**) Option "xkb_rules" "evdev"
[    86.820] (**) Option "xkb_model" "pc105"
[    86.820] (**) Option "xkb_layout" "fr"
[    86.820] (**) Option "xkb_variant" "oss"
[    86.823] (II) XKB: reuse xkmfile /var/lib/xkb/server-6CCE7350BC740BB33D520367F4A10E64192A358C.xkm
[    86.826] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    86.826] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    86.826] (II) Using input driver 'evdev' for 'Power Button'
[    86.826] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    86.827] (**) Power Button: always reports core events
[    86.827] (**) Power Button: Device: "/dev/input/event1"
[    86.848] (--) Power Button: Found keys
[    86.848] (II) Power Button: Configuring as keyboard
[    86.848] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[    86.848] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    86.848] (**) Option "xkb_rules" "evdev"
[    86.848] (**) Option "xkb_model" "pc105"
[    86.848] (**) Option "xkb_layout" "fr"
[    86.848] (**) Option "xkb_variant" "oss"
[    86.848] (II) config/udev: Adding input device Sleep Button (/dev/input/event0)
[    86.848] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    86.848] (II) Using input driver 'evdev' for 'Sleep Button'
[    86.848] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    86.848] (**) Sleep Button: always reports core events
[    86.849] (**) Sleep Button: Device: "/dev/input/event0"
[    86.864] (--) Sleep Button: Found keys
[    86.864] (II) Sleep Button: Configuring as keyboard
[    86.864] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input0/event0"
[    86.864] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    86.864] (**) Option "xkb_rules" "evdev"
[    86.864] (**) Option "xkb_model" "pc105"
[    86.864] (**) Option "xkb_layout" "fr"
[    86.864] (**) Option "xkb_variant" "oss"
[    86.871] (II) config/udev: Adding input device Logitech HID compliant keyboard (/dev/input/event3)
[    86.871] (**) Logitech HID compliant keyboard: Applying InputClass "evdev keyboard catchall"
[    86.871] (II) Using input driver 'evdev' for 'Logitech HID compliant keyboard'
[    86.871] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    86.871] (**) Logitech HID compliant keyboard: always reports core events
[    86.871] (**) Logitech HID compliant keyboard: Device: "/dev/input/event3"
[    86.892] (--) Logitech HID compliant keyboard: Found keys
[    86.892] (II) Logitech HID compliant keyboard: Configuring as keyboard
[    86.892] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:10.1/usb3/3-2/3-2:1.0/input/input3/event3"
[    86.892] (II) XINPUT: Adding extended input device "Logitech HID compliant keyboard" (type: KEYBOARD)
[    86.892] (**) Option "xkb_rules" "evdev"
[    86.892] (**) Option "xkb_model" "pc105"
[    86.892] (**) Option "xkb_layout" "fr"
[    86.892] (**) Option "xkb_variant" "oss"
[    86.893] (II) config/udev: Adding input device Logitech HID compliant keyboard (/dev/input/event4)
[    86.893] (**) Logitech HID compliant keyboard: Applying InputClass "evdev keyboard catchall"
[    86.893] (II) Using input driver 'evdev' for 'Logitech HID compliant keyboard'
[    86.893] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    86.893] (**) Logitech HID compliant keyboard: always reports core events
[    86.893] (**) Logitech HID compliant keyboard: Device: "/dev/input/event4"
[    86.908] (--) Logitech HID compliant keyboard: Found 20 mouse buttons
[    86.908] (--) Logitech HID compliant keyboard: Found keys
[    86.908] (II) Logitech HID compliant keyboard: Configuring as mouse
[    86.908] (II) Logitech HID compliant keyboard: Configuring as keyboard
[    86.908] (**) Logitech HID compliant keyboard: YAxisMapping: buttons 4 and 5
[    86.908] (**) Logitech HID compliant keyboard: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    86.908] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:10.1/usb3/3-2/3-2:1.1/input/input4/event4"
[    86.908] (II) XINPUT: Adding extended input device "Logitech HID compliant keyboard" (type: KEYBOARD)
[    86.908] (**) Option "xkb_rules" "evdev"
[    86.908] (**) Option "xkb_model" "pc105"
[    86.908] (**) Option "xkb_layout" "fr"
[    86.908] (**) Option "xkb_variant" "oss"
[    86.912] (II) config/udev: Adding input device ImExPS/2 Logitech Explorer Mouse (/dev/input/event5)
[    86.912] (**) ImExPS/2 Logitech Explorer Mouse: Applying InputClass "evdev pointer catchall"
[    86.912] (II) Using input driver 'evdev' for 'ImExPS/2 Logitech Explorer Mouse'
[    86.912] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    86.912] (**) ImExPS/2 Logitech Explorer Mouse: always reports core events
[    86.912] (**) ImExPS/2 Logitech Explorer Mouse: Device: "/dev/input/event5"
[    86.936] (--) ImExPS/2 Logitech Explorer Mouse: Found 9 mouse buttons
[    86.936] (--) ImExPS/2 Logitech Explorer Mouse: Found scroll wheel(s)
[    86.936] (--) ImExPS/2 Logitech Explorer Mouse: Found relative axes
[    86.936] (--) ImExPS/2 Logitech Explorer Mouse: Found x and y relative axes
[    86.936] (II) ImExPS/2 Logitech Explorer Mouse: Configuring as mouse
[    86.936] (II) ImExPS/2 Logitech Explorer Mouse: Adding scrollwheel support
[    86.936] (**) ImExPS/2 Logitech Explorer Mouse: YAxisMapping: buttons 4 and 5
[    86.936] (**) ImExPS/2 Logitech Explorer Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    86.936] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input5/event5"
[    86.936] (II) XINPUT: Adding extended input device "ImExPS/2 Logitech Explorer Mouse" (type: MOUSE)
[    86.936] (II) ImExPS/2 Logitech Explorer Mouse: initialized for relative axes.
[    86.936] (**) ImExPS/2 Logitech Explorer Mouse: (accel) keeping acceleration scheme 1
[    86.936] (**) ImExPS/2 Logitech Explorer Mouse: (accel) acceleration profile 0
[    86.936] (**) ImExPS/2 Logitech Explorer Mouse: (accel) acceleration factor: 2.000
[    86.936] (**) ImExPS/2 Logitech Explorer Mouse: (accel) acceleration threshold: 4
[    86.936] (II) config/udev: Adding input device ImExPS/2 Logitech Explorer Mouse (/dev/input/mouse0)
[    86.936] (II) No input driver/identifier specified (ignoring)
[    87.035] (II) fglrx(0): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
[    87.099] (II) fglrx(0): EDID vendor "BNQ", prod id 30421
[    87.099] (II) fglrx(0): Using EDID range info for horizontal sync
[    87.100] (II) fglrx(0): Using EDID range info for vertical refresh
[    87.100] (II) fglrx(0): Printing DDC gathered Modelines:
[    87.100] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    87.100] (II) fglrx(0): Modeline "640x350"x0.0   25.17  640 656 752 800  350 387 389 449 +hsync -vsync (31.5 kHz)
[    87.100] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    87.100] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    87.100] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    87.100] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    87.100] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    87.100] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    87.100] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    87.100] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    87.100] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    87.100] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    87.100] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    87.100] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    87.100] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    87.100] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    87.100] (II) fglrx(0): Modeline "1280x1024"x72.0  132.75  1280 1368 1504 1728  1024 1025 1028 1067 -hsync +vsync (76.8 kHz)
[    87.585] (II) fglrx(0): EDID vendor "BNQ", prod id 30421
[    87.585] (II) fglrx(0): Using hsync ranges from config file
[    87.585] (II) fglrx(0): Using vrefresh ranges from config file
[    87.585] (II) fglrx(0): Printing DDC gathered Modelines:
[    87.585] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    87.585] (II) fglrx(0): Modeline "640x350"x0.0   25.17  640 656 752 800  350 387 389 449 +hsync -vsync (31.5 kHz)
[    87.585] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    87.585] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    87.585] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    87.585] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    87.585] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    87.585] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    87.585] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    87.585] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    87.585] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    87.585] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    87.585] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    87.585] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    87.585] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    87.585] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    87.585] (II) fglrx(0): Modeline "1280x1024"x72.0  132.75  1280 1368 1504 1728  1024 1025 1028 1067 -hsync +vsync (76.8 kHz)
[    87.813] (II) fglrx(0): EDID vendor "BNQ", prod id 30421
[    87.813] (II) fglrx(0): Using hsync ranges from config file
[    87.813] (II) fglrx(0): Using vrefresh ranges from config file
[    87.813] (II) fglrx(0): Printing DDC gathered Modelines:
[    87.813] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    87.813] (II) fglrx(0): Modeline "640x350"x0.0   25.17  640 656 752 800  350 387 389 449 +hsync -vsync (31.5 kHz)
[    87.813] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    87.813] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    87.813] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    87.813] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    87.813] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    87.813] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    87.813] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    87.813] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    87.813] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    87.813] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    87.813] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    87.813] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    87.813] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    87.813] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    87.813] (II) fglrx(0): Modeline "1280x1024"x72.0  132.75  1280 1368 1504 1728  1024 1025 1028 1067 -hsync +vsync (76.8 kHz)
[    88.040] (II) fglrx(0): EDID vendor "BNQ", prod id 30421
[    88.040] (II) fglrx(0): Using hsync ranges from config file
[    88.040] (II) fglrx(0): Using vrefresh ranges from config file
[    88.040] (II) fglrx(0): Printing DDC gathered Modelines:
[    88.040] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    88.040] (II) fglrx(0): Modeline "640x350"x0.0   25.17  640 656 752 800  350 387 389 449 +hsync -vsync (31.5 kHz)
[    88.040] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    88.040] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    88.040] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    88.040] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    88.040] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    88.040] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    88.040] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    88.040] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    88.040] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    88.040] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    88.040] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    88.040] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    88.040] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    88.040] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    88.040] (II) fglrx(0): Modeline "1280x1024"x72.0  132.75  1280 1368 1504 1728  1024 1025 1028 1067 -hsync +vsync (76.8 kHz)
[    88.269] (II) fglrx(0): EDID vendor "BNQ", prod id 30421
[    88.269] (II) fglrx(0): Using hsync ranges from config file
[    88.269] (II) fglrx(0): Using vrefresh ranges from config file
[    88.269] (II) fglrx(0): Printing DDC gathered Modelines:
[    88.269] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    88.269] (II) fglrx(0): Modeline "640x350"x0.0   25.17  640 656 752 800  350 387 389 449 +hsync -vsync (31.5 kHz)
[    88.269] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    88.269] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    88.269] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    88.269] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    88.269] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    88.269] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    88.269] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    88.269] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    88.269] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    88.269] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    88.269] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    88.269] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    88.269] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    88.269] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    88.269] (II) fglrx(0): Modeline "1280x1024"x72.0  132.75  1280 1368 1504 1728  1024 1025 1028 1067 -hsync +vsync (76.8 kHz)
[   100.439] (II) fglrx(0): EDID vendor "BNQ", prod id 30421
[   100.439] (II) fglrx(0): Using hsync ranges from config file
[   100.439] (II) fglrx(0): Using vrefresh ranges from config file
[   100.439] (II) fglrx(0): Printing DDC gathered Modelines:
[   100.439] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   100.439] (II) fglrx(0): Modeline "640x350"x0.0   25.17  640 656 752 800  350 387 389 449 +hsync -vsync (31.5 kHz)
[   100.439] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   100.439] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   100.439] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[   100.439] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[   100.439] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   100.439] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   100.439] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   100.439] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   100.439] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[   100.439] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   100.439] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   100.439] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   100.439] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[   100.439] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   100.439] (II) fglrx(0): Modeline "1280x1024"x72.0  132.75  1280 1368 1504 1728  1024 1025 1028 1067 -hsync +vsync (76.8 kHz)
[   100.667] (II) fglrx(0): EDID vendor "BNQ", prod id 30421
[   100.667] (II) fglrx(0): Using hsync ranges from config file
[   100.667] (II) fglrx(0): Using vrefresh ranges from config file
[   100.667] (II) fglrx(0): Printing DDC gathered Modelines:
[   100.667] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   100.667] (II) fglrx(0): Modeline "640x350"x0.0   25.17  640 656 752 800  350 387 389 449 +hsync -vsync (31.5 kHz)
[   100.667] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   100.667] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   100.667] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[   100.667] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[   100.667] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   100.667] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   100.667] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   100.667] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   100.667] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[   100.667] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   100.667] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   100.667] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   100.667] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[   100.667] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   100.667] (II) fglrx(0): Modeline "1280x1024"x72.0  132.75  1280 1368 1504 1728  1024 1025 1028 1067 -hsync +vsync (76.8 kHz)
[   100.894] (II) fglrx(0): EDID vendor "BNQ", prod id 30421
[   100.894] (II) fglrx(0): Using hsync ranges from config file
[   100.894] (II) fglrx(0): Using vrefresh ranges from config file
[   100.894] (II) fglrx(0): Printing DDC gathered Modelines:
[   100.894] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   100.894] (II) fglrx(0): Modeline "640x350"x0.0   25.17  640 656 752 800  350 387 389 449 +hsync -vsync (31.5 kHz)
[   100.894] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   100.894] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   100.894] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[   100.895] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[   100.895] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   100.895] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   100.895] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   100.895] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   100.895] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[   100.895] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   100.895] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   100.895] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   100.895] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[   100.895] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   100.895] (II) fglrx(0): Modeline "1280x1024"x72.0  132.75  1280 1368 1504 1728  1024 1025 1028 1067 -hsync +vsync (76.8 kHz)
[   101.130] (II) fglrx(0): EDID vendor "BNQ", prod id 30421
[   101.130] (II) fglrx(0): Using hsync ranges from config file
[   101.130] (II) fglrx(0): Using vrefresh ranges from config file
[   101.130] (II) fglrx(0): Printing DDC gathered Modelines:
[   101.130] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   101.130] (II) fglrx(0): Modeline "640x350"x0.0   25.17  640 656 752 800  350 387 389 449 +hsync -vsync (31.5 kHz)
[   101.131] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   101.131] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   101.131] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[   101.131] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[   101.131] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   101.131] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   101.131] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   101.131] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   101.131] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[   101.131] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   101.131] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   101.131] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   101.131] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[   101.131] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   101.131] (II) fglrx(0): Modeline "1280x1024"x72.0  132.75  1280 1368 1504 1728  1024 1025 1028 1067 -hsync +vsync (76.8 kHz)
[   107.063] (II) fglrx(0): EDID vendor "BNQ", prod id 30421
[   107.063] (II) fglrx(0): Using hsync ranges from config file
[   107.063] (II) fglrx(0): Using vrefresh ranges from config file
[   107.063] (II) fglrx(0): Printing DDC gathered Modelines:
[   107.063] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   107.063] (II) fglrx(0): Modeline "640x350"x0.0   25.17  640 656 752 800  350 387 389 449 +hsync -vsync (31.5 kHz)
[   107.063] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   107.063] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   107.063] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[   107.063] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[   107.063] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   107.063] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   107.063] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   107.063] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   107.063] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[   107.063] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   107.063] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   107.063] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   107.063] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[   107.063] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   107.063] (II) fglrx(0): Modeline "1280x1024"x72.0  132.75  1280 1368 1504 1728  1024 1025 1028 1067 -hsync +vsync (76.8 kHz)
[   368.990] Warning: LookupWindow()/SecurityLookupWindow() are deprecated.  Please convert your driver/module to use dixLookupWindow().
```

---

### Post by Sinner on 2011-07-14
I have tried to boot from a fresh new burned live cd and I have a black screen when all seems loaded and I should get the desktop.

I also tried to boot the live cd with nomodeset kernel optio with no much more success, the pc just get black screen and I cannot even get the tty1 via ctrl + F1.

(nomodeset option explained here: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

I'm getting mad with this.

---

### Post by Sinner on 2011-07-14
I installed the additional proprietary driver and launch kernel with radeon.modeset=0 nomodeset

then started the 'Ubuntu' session.
I got a black screen, switched to tty1 and try a dmesg, here is the error I see, any advice ?

```

[   36.282609] hda-intel: spurious response 0x0:0x0, last cmd=0x524017
[   36.282630] hda-intel: spurious response 0x50:0x0, last cmd=0x524017
[   36.282651] hda-intel: spurious response 0x0:0x0, last cmd=0x524017
[   36.282671] hda-intel: spurious response 0x4015:0x0, last cmd=0x524017
[   36.282693] hda-intel: spurious response 0x0:0x0, last cmd=0x524017
[   88.287559] [fglrx] IRQ 66 Disabled
[   90.107485] fglrx_pci 0000:02:00.0: irq 66 for MSI/MSI-X
[   90.108452] [fglrx] Firegl kernel thread PID: 1658
[   90.108525] [fglrx] Firegl kernel thread PID: 1659
[   90.108593] [fglrx] Firegl kernel thread PID: 1660
[   90.108890] [fglrx] IRQ 66 Enabled
[   90.721582] [fglrx] Gart USWC size:628 M.
[   90.721586] [fglrx] Gart cacheable size:247 M.
[   90.721592] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   90.721595] [fglrx] Reserved FB block: Unshared offset:fe07000, size:1f9000 
[   90.721598] [fglrx] Reserved FB block: Unshared offset:1fffb000, size:5000 
[   91.546842] [fglrx:fireglAsyncioIntEnableMsgHandler] *ERROR* interrupt source ff000066 is not supported on this hardware (return code = 1)
[  116.289106] [fglrx:fireglAsyncioIntDisableMsgHandler] *ERROR* IRQMGR returned error 1 when trying to disable interrupt source ff000066
[  169.321460] show_signal_msg: 24 callbacks suppressed
[  169.321465] gvfsd-metadata[1854]: segfault at 8 ip 0804c92d sp bfafa5f0 error 4 in gvfsd-metadata[8048000+c000]
[  228.111894] [fglrx:fireglAsyncioIntEnableMsgHandler] *ERROR* interrupt source ff000066 is not supported on this hardware (return code = 1)
[  231.722469] [fglrx:fireglAsyncioIntDisableMsgHandler] *ERROR* IRQMGR returned error 1 when trying to disable interrupt source ff000066
[  312.783641] [fglrx] IRQ 66 Disabled
[  313.078743] fglrx_pci 0000:02:00.0: irq 66 for MSI/MSI-X
[  313.082470] [fglrx] Firegl kernel thread PID: 2166
[  313.083043] [fglrx] Firegl kernel thread PID: 2167
[  313.083130] [fglrx] Firegl kernel thread PID: 2168
[  313.083446] [fglrx] IRQ 66 Enabled
[  314.624802] [fglrx:fireglAsyncioIntEnableMsgHandler] *ERROR* interrupt source ff000066 is not supported on this hardware (return code = 1)
[  327.004152] hda-intel: spurious response 0x4013:0x0, last cmd=0x3a0000
[  327.004171] hda-intel: spurious response 0x0:0x0, last cmd=0x3a0000
[  327.004191] hda-intel: spurious response 0x4013:0x0, last cmd=0x3a0000
[  327.004211] hda-intel: spurious response 0x0:0x0, last cmd=0x3a0000
[  327.004255] hda-intel: spurious response 0x4013:0x0, last cmd=0x3a0000
[  327.004257] hda-intel: spurious response 0x0:0x0, las
```

---

### Post by Sinner on 2011-07-29
Up please !
Anyone to help ?

---

### Post by Sinner on 2011-08-18
Hi all,

Here is the solution:
[https://bbs.archlinux.org/viewtopic.php?id=109132](https://bbs.archlinux.org/viewtopic.php?id=109132)

Good news, adding pci=nomsi to the kernel line, solves the issue completely.

Sinn'

---

### Post by Sinner on 2011-08-26
Performance is not goog that way, so i also removed the fglrx ati proprietary drivers and switched to the open source ones.

With fglrx, glxgears was slow and I also had some more performance issue, display problems.

to swith to open source drivers, follow the instruction here
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:__Need_to_fully_remove_-fglrx_and_reinstall_-ati_from_scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:__Need_to_fully_remove_-fglrx_and_reinstall_-ati_from_scratch)

in compiz settings, I still have the default configuration:
- detect refresh rate checked into composite
- sync to vblanc in opengl

At last get rid of your /etc/X11/xorg.conf by renaming it or simply delete it, you don't need this for X to work.

All is working like a charm like this !

Hope this could help some of you to get the 3d back with radeon hd 4350.

---

### Post by grrowwmn on 2011-08-27
Thanks Sinn. Unfortunately, it didn't work for my Radeon X2100.

:(

---

