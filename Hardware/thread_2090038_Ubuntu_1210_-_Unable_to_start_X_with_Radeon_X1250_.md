---
title: "Ubuntu 12:10 - Unable to start X with Radeon X1250 card"
date: 2012-12-01
forum: Hardware
---

### Post by MrHyde on 2012-12-01
Hi,

My system was working fine till today morning, when I decided to re-boot it after some of the kernel upgrades were applied.  On re-booting, instead of going straight into LightDM, it went to the login screen instead.   In trying to fix this, I removed, installed, removed, installed a number of drivers from fglrx to nvidia and have now screwed up the install even further.  The system is now no longer even showing the login prompt on startup... it is just stuck on the boot sequeunce.  

However, I can ssh into the machine and I still think the problem lies with the graphics drivers and X configuration.  The current state is that I have uninstalled all nvidia drivers as well as proprietary catalyst/fglrx drivers and re-installed some of the x-server-core packages.

Can someone please help me with getting the system back up and running.  Some information that might help in troubleshooting this:

[PHP]
$ sudo lspci | grep VGA
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS690 [Radeon X1200 Series]

[/PHP]

My Xorg.0.log says 
```

[    28.949]
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    28.949] X Protocol Version 11, Revision 0
[    28.949] Build Operating System: Linux 2.6.42-23-generic x86_64 Ubuntu
[    28.949] Current Operating System: Linux duper 3.2.0-33-generic #52-Ubuntu SMP Thu Oct 18 16:29:15 UTC 2012 x86_64
[    28.950] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-33-generic root=UUID=c4bb9b50-7fac-4e2b-9d68-77dd493c01b3 ro quiet splash radeon.audio=1 vt.handoff=7
[    28.950] Build Date: 29 August 2012  12:12:33AM
[    28.950] xorg-server 2:1.11.4-0ubuntu10.8 (For technical support please see http://www.ubuntu.com/support)
[    28.950] Current version of pixman: 0.24.4
[    28.950]    Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
[    28.950] Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    28.950] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Dec  1 17:46:45 2012
[    28.950] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    28.951] (==) No Layout section.  Using the first Screen section.
[    28.951] (==) No screen section available. Using defaults.
[    28.951] (**) |-->Screen "Default Screen Section" (0)
[    28.951] (**) |   |-->Monitor "<default monitor>"
[    28.952] (==) No monitor specified for screen "Default Screen Section".
        Using a default monitor configuration.
[    28.952] (==) Automatically adding devices
[    28.952] (==) Automatically enabling devices
[    28.952] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    28.952]    Entry deleted from font path.
[    28.952] (==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/100dpi/:unscaled,
        /usr/share/fonts/X11/75dpi/:unscaled,
        /usr/share/fonts/X11/Type1,
        /usr/share/fonts/X11/100dpi,
        /usr/share/fonts/X11/75dpi,
        /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
        built-ins
[    28.952] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    28.952] (II) The server relies on udev to provide the list of input devices.
        If no devices become available, reconfigure udev or disable AutoAddDevices.
[    28.952] (II) Loader magic: 0x7f200e5a0b00
[    28.952] (II) Module ABI versions:
[    28.952]    X.Org ANSI C Emulation: 0.4
[    28.952]    X.Org Video Driver: 11.0
[    28.952]    X.Org XInput driver : 16.0
[    28.952]    X.Org Server Extension : 6.0
[    28.955] (--) PCI:*(0:1:5:0) 1002:791e:1458:d001 rev 0, Mem @ 0xd8000000/134217728, 0xfdfe0000/65536, 0xfde00000/1048576, I/O @ 0x0000ee00/256
[    28.955] (II) Open ACPI successful (/var/run/acpid.socket)
[    28.955] (II) LoadModule: "extmod"
[    28.956] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    28.957] (II) Module extmod: vendor="X.Org Foundation"
[    28.957]    compiled for 1.11.3, module version = 1.0.0
[    28.957]    Module class: X.Org Server Extension
[    28.957]    ABI class: X.Org Server Extension, version 6.0
[    28.957] (II) Loading extension MIT-SCREEN-SAVER
[    28.957] (II) Loading extension XFree86-VidModeExtension
[    28.957] (II) Loading extension XFree86-DGA
[    28.957] (II) Loading extension DPMS
[    28.957] (II) Loading extension XVideo
[    28.957] (II) Loading extension XVideo-MotionCompensation
[    28.957] (II) Loading extension X-Resource
[    28.957] (II) LoadModule: "dbe"
[    28.958] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    28.958] (II) Module dbe: vendor="X.Org Foundation"
[    28.958]    compiled for 1.11.3, module version = 1.0.0
[    28.958]    Module class: X.Org Server Extension
[    28.958]    ABI class: X.Org Server Extension, version 6.0
[    28.958] (II) Loading extension DOUBLE-BUFFER
[    28.958] (II) LoadModule: "glx"
[    28.959] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    28.959] (II) Module glx: vendor="X.Org Foundation"
[    28.959]    compiled for 1.11.3, module version = 1.0.0
[    28.959]    ABI class: X.Org Server Extension, version 6.0
[    28.959] (==) AIGLX enabled
[    28.959] (II) Loading extension GLX
[    28.959] (II) LoadModule: "record"
[    28.961] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    28.961] (II) Module record: vendor="X.Org Foundation"
[    28.961]    compiled for 1.11.3, module version = 1.13.0
[    28.961]    Module class: X.Org Server Extension
[    28.961]    ABI class: X.Org Server Extension, version 6.0
[    28.961] (II) Loading extension RECORD
[    28.961] (II) LoadModule: "dri"
[    28.963] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    28.963] (II) Module dri: vendor="X.Org Foundation"
[    28.963]    compiled for 1.11.3, module version = 1.0.0
[    28.963]    ABI class: X.Org Server Extension, version 6.0
[    28.963] (II) Loading extension XFree86-DRI
[    28.963] (II) LoadModule: "dri2"
[    28.964] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    28.964] (II) Module dri2: vendor="X.Org Foundation"
[    28.964]    compiled for 1.11.3, module version = 1.2.0
[    28.964]    ABI class: X.Org Server Extension, version 6.0
[    28.964] (II) Loading extension DRI2
[    28.964] (==) Matched fglrx as autoconfigured driver 0
[    28.965] (==) Matched ati as autoconfigured driver 1
[    28.965] (==) Matched vesa as autoconfigured driver 2
[    28.965] (==) Matched fbdev as autoconfigured driver 3
[    28.965] (==) Assigned the driver to the xf86ConfigLayout
[    28.965] (II) LoadModule: "fglrx"
[    28.966] (WW) Warning, couldn't open module fglrx
[    28.966] (II) UnloadModule: "fglrx"
[    28.966] (II) Unloading fglrx
[    28.966] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    28.966] (II) LoadModule: "ati"
[    28.966] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    28.966] (II) Module ati: vendor="X.Org Foundation"
[    28.966]    compiled for 1.11.3, module version = 6.99.99
[    28.966]    Module class: X.Org Video Driver
[    28.966]    ABI class: X.Org Video Driver, version 11.0
[    28.966] (II) LoadModule: "radeon"
[    28.967] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    28.968] (II) Module radeon: vendor="X.Org Foundation"
[    28.968]    compiled for 1.11.3, module version = 6.99.99
[    28.968]    Module class: X.Org Video Driver
[    28.968]    ABI class: X.Org Video Driver, version 11.0
[    28.968] (II) LoadModule: "vesa"
[    28.968] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    28.968] (II) Module vesa: vendor="X.Org Foundation"
[    28.968]    compiled for 1.11.3, module version = 2.3.0
[    28.968]    Module class: X.Org Video Driver
[    28.968]    ABI class: X.Org Video Driver, version 11.0
[    28.968] (II) LoadModule: "fbdev"
[    28.969] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    28.969] (II) Module fbdev: vendor="X.Org Foundation"
[    28.969]    compiled for 1.11.3, module version = 0.4.2
[    28.969]    ABI class: X.Org Video Driver, version 11.0
[    28.969] (==) Matched fglrx as autoconfigured driver 0
[    28.969] (==) Matched ati as autoconfigured driver 1
[    28.969] (==) Matched vesa as autoconfigured driver 2
[    28.969] (==) Matched fbdev as autoconfigured driver 3
[    28.969] (==) Assigned the driver to the xf86ConfigLayout
[    28.969] (II) LoadModule: "fglrx"
[    28.971] (WW) Warning, couldn't open module fglrx
[    28.971] (II) UnloadModule: "fglrx"
[    28.971] (II) Unloading fglrx
[    28.971] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    28.971] (II) LoadModule: "ati"
[    28.971] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    28.971] (II) Module ati: vendor="X.Org Foundation"
[    28.971]    compiled for 1.11.3, module version = 6.99.99
[    28.971]    Module class: X.Org Video Driver
[    28.971]    ABI class: X.Org Video Driver, version 11.0
[    28.971] (II) LoadModule: "vesa"
[    28.973] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    28.973] (II) Module vesa: vendor="X.Org Foundation"
[    28.973]    compiled for 1.11.3, module version = 2.3.0
[    28.973]    Module class: X.Org Video Driver
[    28.973]    ABI class: X.Org Video Driver, version 11.0
[    28.973] (II) UnloadModule: "vesa"
[    28.973] (II) Unloading vesa
[    28.973] (II) Failed to load module "vesa" (already loaded, 0)
[    28.973] (II) LoadModule: "fbdev"
[    28.973] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    28.973] (II) Module fbdev: vendor="X.Org Foundation"
[    28.973]    compiled for 1.11.3, module version = 0.4.2
[    28.973]    ABI class: X.Org Video Driver, version 11.0
[    28.973] (II) UnloadModule: "fbdev"
[    28.973] (II) Unloading fbdev
[    28.973] (II) Failed to load module "fbdev" (already loaded, 0)
[    28.973] (II) RADEON: Driver for ATI Radeon chipsets:
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
[    28.986] (II) VESA: driver for VESA chipsets: vesa
[    28.986] (II) FBDEV: driver for framebuffer: fbdev
[    28.986] (++) using VT number 7

[    28.986] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    28.986] (II) [KMS] Kernel modesetting enabled.
[    28.986] (WW) Falling back to old probe method for vesa
[    28.986] (WW) Falling back to old probe method for fbdev
[    28.986] (II) Loading sub module "fbdevhw"
[    28.986] (II) LoadModule: "fbdevhw"
[    28.986] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    28.986] (II) Module fbdevhw: vendor="X.Org Foundation"
[    28.986]    compiled for 1.11.3, module version = 0.0.2
[    28.986]    ABI class: X.Org Video Driver, version 11.0
[    28.987] (II) RADEON(0): Creating default Display subsection in Screen section
        "Default Screen Section" for depth/fbbpp 24/32
[    28.987] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    28.987] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    28.987] (==) RADEON(0): Default visual is TrueColor
[    28.987] (==) RADEON(0): RGB weight 888
[    28.987] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    28.987] (--) RADEON(0): Chipset: "ATI Radeon X1200" (ChipID = 0x791e)
[    28.987] drmOpenDevice: node name is /dev/dri/card0
[    28.987] drmOpenDevice: open result is 9, (OK)
[    28.987] drmOpenByBusid: Searching for BusID pci:0000:01:05.0
[    28.987] drmOpenDevice: node name is /dev/dri/card0
[    28.987] drmOpenDevice: open result is 9, (OK)
[    28.987] drmOpenByBusid: drmOpenMinor returns 9
[    28.987] drmOpenByBusid: drmGetBusid reports pci:0000:01:05.0
[    28.987] (II) Loading sub module "dri2"
[    28.987] (II) LoadModule: "dri2"
[    28.987] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    28.987] (II) Module dri2: vendor="X.Org Foundation"
[    28.987]    compiled for 1.11.3, module version = 1.2.0
[    28.987]    ABI class: X.Org Server Extension, version 6.0
[    28.987] (II) Loading sub module "exa"
[    28.987] (II) LoadModule: "exa"
[    28.988] (II) Loading /usr/lib/xorg/modules/libexa.so
[    28.988] (II) Module exa: vendor="X.Org Foundation"
[    28.988]    compiled for 1.11.3, module version = 2.5.0
[    28.988]    ABI class: X.Org Video Driver, version 11.0
[    28.988] (II) RADEON(0): KMS Color Tiling: enabled
[    28.988] (II) RADEON(0): KMS Pageflipping: enabled
[    28.988] (II) RADEON(0): SwapBuffers wait for vsync: enabled
[    29.164] (II) RADEON(0): Output VGA-0 has no monitor section
[    29.340] (II) RADEON(0): Output S-video has no monitor section
[    29.474] (II) RADEON(0): Output HDMI-0 has no monitor section
[    29.652] (II) RADEON(0): EDID for output VGA-0
[    29.828] (II) RADEON(0): EDID for output S-video
[    30.000] (II) RADEON(0): EDID for output HDMI-0
[    30.000] (II) RADEON(0): Manufacturer: SNY  Model: a401  Serial#: 16843009
[    30.000] (II) RADEON(0): Year: 2009  Week: 1
[    30.000] (II) RADEON(0): EDID Version: 1.3
[    30.000] (II) RADEON(0): Digital Display Input
[    30.000] (II) RADEON(0): Max Image Size [cm]: horiz.: 160  vert.: 90
[    30.000] (II) RADEON(0): Gamma: 2.20
[    30.000] (II) RADEON(0): No DPMS capabilities specified
[    30.000] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4
[    30.000] (II) RADEON(0): First detailed timing is preferred mode
[    30.000] (II) RADEON(0): redX: 0.625 redY: 0.340   greenX: 0.280 greenY: 0.595
[    30.000] (II) RADEON(0): blueX: 0.155 blueY: 0.070   whiteX: 0.283 whiteY: 0.298
[    30.000] (II) RADEON(0): Supported established timings:
[    30.000] (II) RADEON(0): 640x480@60Hz
[    30.000] (II) RADEON(0): 800x600@60Hz
[    30.000] (II) RADEON(0): 1024x768@60Hz
[    30.000] (II) RADEON(0): Manufacturer's mask: 0
[    30.000] (II) RADEON(0): Supported standard timings:
[    30.000] (II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    30.000] (II) RADEON(0): Supported detailed timing:
[    30.000] (II) RADEON(0): clock: 148.5 MHz   Image Size:  1600 x 900 mm
[    30.000] (II) RADEON(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    30.000] (II) RADEON(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    30.000] (II) RADEON(0): Supported detailed timing:
[    30.000] (II) RADEON(0): clock: 74.2 MHz   Image Size:  1600 x 900 mm
[    30.000] (II) RADEON(0): h_active: 1280  h_sync: 1390  h_sync_end 1430 h_blank_end 1650 h_border: 0
[    30.000] (II) RADEON(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
[    30.000] (II) RADEON(0): Monitor name: SONY TV
[    30.000] (II) RADEON(0): Ranges: V min: 48 V max: 62 Hz, H min: 14 H max: 70 kHz, PixClock max 155 MHz
[    30.000] (II) RADEON(0): Supported detailed timing:
[    30.000] (II) RADEON(0): clock: 148.5 MHz   Image Size:  1600 x 900 mm
[    30.000] (II) RADEON(0): h_active: 1920  h_sync: 2448  h_sync_end 2492 h_blank_end 2640 h_border: 0
[    30.000] (II) RADEON(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    30.000] (II) RADEON(0): Supported detailed timing:
[    30.000] (II) RADEON(0): clock: 74.2 MHz   Image Size:  1600 x 900 mm
[    30.000] (II) RADEON(0): h_active: 1280  h_sync: 1720  h_sync_end 1760 h_blank_end 1980 h_border: 0
[    30.000] (II) RADEON(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
[    30.000] (II) RADEON(0): Supported detailed timing:
[    30.000] (II) RADEON(0): clock: 74.2 MHz   Image Size:  1600 x 900 mm
[    30.000] (II) RADEON(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    30.000] (II) RADEON(0): v_active: 540  v_sync: 542  v_sync_end 547 v_blanking: 562 v_border: 0
[    30.000] (II) RADEON(0): Supported detailed timing:
[    30.001] (II) RADEON(0): clock: 74.2 MHz   Image Size:  1600 x 900 mm
[    30.001] (II) RADEON(0): h_active: 1920  h_sync: 2448  h_sync_end 2492 h_blank_end 2640 h_border: 0
[    30.001] (II) RADEON(0): v_active: 540  v_sync: 542  v_sync_end 547 v_blanking: 562 v_border: 0
[    30.001] (II) RADEON(0): Number of EDID sections to follow: 1
[    30.001] (II) RADEON(0): EDID (in hex):
[    30.001] (II) RADEON(0):    00ffffffffffff004dd901a401010101
[    30.001] (II) RADEON(0):    0113010380a05a780a0dc9a057479827
[    30.001] (II) RADEON(0):    12484c21080081800101010101010101
[    30.001] (II) RADEON(0):    010101010101023a801871382d40582c
[    30.001] (II) RADEON(0):    450040846300001e011d007251d01e20
[    30.001] (II) RADEON(0):    6e28550040846300001e000000fc0053
[    30.001] (II) RADEON(0):    4f4e592054560a2020202020000000fd
[    30.001] (II) RADEON(0):    00303e0e460f000a2020202020200109
[    30.001] (II) RADEON(0):    02032cf0501f10140513041211161503
[    30.001] (II) RADEON(0):    02070601202609070715075083010000
[    30.001] (II) RADEON(0):    68030c00400080000fe2007b023a80d0
[    30.001] (II) RADEON(0):    72382d40102c458040846300001e011d
[    30.001] (II) RADEON(0):    00bc52d01e20b828554040846300001e
[    30.001] (II) RADEON(0):    011d8018711c1620582c250040846300
[    30.001] (II) RADEON(0):    009e011d80d0721c1620102c25804084
[    30.001] (II) RADEON(0):    6300009e000000000000000000000043
[    30.001] (II) RADEON(0): Printing probed modes for output HDMI-0
[    30.001] (II) RADEON(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    30.001] (II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    30.001] (II) RADEON(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    30.001] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    30.001] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    30.001] (II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    30.001] (II) RADEON(0): Output VGA-0 disconnected
[    30.001] (II) RADEON(0): Output S-video disconnected
[    30.001] (II) RADEON(0): Output HDMI-0 connected
[    30.001] (II) RADEON(0): Using exact sizes for initial modes
[    30.001] (II) RADEON(0): Output HDMI-0 using initial mode 1920x1080
[    30.001] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    30.001] (II) RADEON(0): mem size init: gart size :1fdff000 vram size: s:8000000 visible:77d7000
[    30.001] (II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
[    30.001] (==) RADEON(0): DPI set to (96, 96)
[    30.001] (II) Loading sub module "fb"
[    30.001] (II) LoadModule: "fb"
[    30.004] (II) Loading /usr/lib/xorg/modules/libfb.so
[    30.004] (II) Module fb: vendor="X.Org Foundation"
[    30.004]    compiled for 1.11.3, module version = 1.0.0
[    30.004]    ABI class: X.Org ANSI C Emulation, version 0.4
[    30.004] (II) Loading sub module "ramdac"
[    30.004] (II) LoadModule: "ramdac"
[    30.004] (II) Module "ramdac" already built-in
[    30.004] (II) UnloadModule: "vesa"
[    30.004] (II) Unloading vesa
[    30.004] (II) UnloadModule: "fbdev"
[    30.004] (II) Unloading fbdev
[    30.004] (II) UnloadModule: "fbdevhw"
[    30.004] (II) Unloading fbdevhw
[    30.004] (--) Depth 24 pixmap format is 32 bpp
[    30.004] (II) RADEON(0): [DRI2] Setup complete
[    30.004] (II) RADEON(0): [DRI2]   DRI driver: r300
[    30.004] (II) RADEON(0): [DRI2]   VDPAU driver: r300
[    30.004] (II) RADEON(0): Front buffer size: 8160K
[    30.004] (II) RADEON(0): VRAM usage limit set to 103100K
[    30.004] (==) RADEON(0): Backing store disabled
[    30.004] (II) RADEON(0): Direct rendering enabled
[    30.004] (II) RADEON(0): Render acceleration enabled for R300/R400/R500 type cards.
[    30.004] (II) RADEON(0): Setting EXA maxPitchBytes
[    30.004] (II) EXA(0): Driver allocated offscreen pixmaps
[    30.004] (II) EXA(0): Driver registered support for the following operations:
[    30.004] (II)         Solid
[    30.004] (II)         Copy
[    30.004] (II)         Composite (RENDER acceleration)
[    30.004] (II)         UploadToScreen
[    30.004] (II)         DownloadFromScreen
[    30.004] (II) RADEON(0): Acceleration enabled
[    30.004] (==) RADEON(0): DPMS enabled
[    30.004] (==) RADEON(0): Silken mouse enabled
[    30.005] (II) RADEON(0): Set up textured video
[    30.005] (II) RADEON(0): [XvMC] Associated with Radeon Textured Video.
[    30.005] (II) RADEON(0): [XvMC] Extension initialized.
[    30.005] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    30.005] (--) RandR disabled
[    30.005] (II) Initializing built-in extension Generic Event Extension
[    30.005] (II) Initializing built-in extension SHAPE
[    30.005] (II) Initializing built-in extension MIT-SHM
[    30.005] (II) Initializing built-in extension XInputExtension
[    30.005] (II) Initializing built-in extension XTEST
[    30.005] (II) Initializing built-in extension BIG-REQUESTS
[    30.005] (II) Initializing built-in extension SYNC
[    30.005] (II) Initializing built-in extension XKEYBOARD
[    30.005] (II) Initializing built-in extension XC-MISC
[    30.005] (II) Initializing built-in extension SECURITY
[    30.005] (II) Initializing built-in extension XINERAMA
[    30.005] (II) Initializing built-in extension XFIXES
[    30.005] (II) Initializing built-in extension RENDER
[    30.005] (II) Initializing built-in extension RANDR
[    30.005] (II) Initializing built-in extension COMPOSITE
[    30.005] (II) Initializing built-in extension DAMAGE
[    30.045] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    30.045] (II) AIGLX: enabled GLX_INTEL_swap_event
[    30.045] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    30.045] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    30.046] (II) AIGLX: Loaded and initialized r300
[    30.046] (II) GLX: Initialized DRI2 GL provider for screen 0
[    30.046] (II) RADEON(0): Setting screen physical size to 508 x 285
[    30.085] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    30.091] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    30.091] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    30.091] (II) LoadModule: "evdev"
[    30.092] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    30.092] (II) Module evdev: vendor="X.Org Foundation"
[    30.092]    compiled for 1.11.3, module version = 2.7.0
[    30.092]    Module class: X.Org XInput Driver
[    30.092]    ABI class: X.Org XInput driver, version 16.0
[    30.092] (II) Using input driver 'evdev' for 'Power Button'
[    30.092] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    30.092] (**) Power Button: always reports core events
[    30.092] (**) evdev: Power Button: Device: "/dev/input/event1"
[    30.092] (--) evdev: Power Button: Vendor 0 Product 0x1
[    30.092] (--) evdev: Power Button: Found keys
[    30.092] (II) evdev: Power Button: Configuring as keyboard
[    30.092] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    30.092] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    30.092] (**) Option "xkb_rules" "evdev"
[    30.092] (**) Option "xkb_model" "pc105"
[    30.092] (**) Option "xkb_layout" "us"
[    30.096] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    30.096] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    30.096] (II) Using input driver 'evdev' for 'Power Button'
[    30.096] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    30.097] (**) Power Button: always reports core events
[    30.097] (**) evdev: Power Button: Device: "/dev/input/event0"
[    30.097] (--) evdev: Power Button: Vendor 0 Product 0x1
[    30.097] (--) evdev: Power Button: Found keys
[    30.097] (II) evdev: Power Button: Configuring as keyboard
[    30.097] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    30.097] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    30.097] (**) Option "xkb_rules" "evdev"
[    30.097] (**) Option "xkb_model" "pc105"
[    30.097] (**) Option "xkb_layout" "us"
[    30.098] (II) config/udev: Adding input device Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) (/dev/input/event2)
[    30.098] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Applying InputClass "evdev pointer catchall"
[    30.098] (II) Using input driver 'evdev' for 'Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)'
[    30.098] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    30.098] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): always reports core events
[    30.098] (**) evdev: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Device: "/dev/input/event2"
[    30.098] (--) evdev: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Vendor 0x45e Product 0x40
[    30.098] (--) evdev: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found 3 mouse buttons
[    30.098] (--) evdev: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found scroll wheel(s)
[    30.098] (--) evdev: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found relative axes
[    30.098] (--) evdev: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found x and y relative axes
[    30.098] (II) evdev: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Configuring as mouse
[    30.098] (II) evdev: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Adding scrollwheel support
[    30.098] (**) evdev: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): YAxisMapping: buttons 4 and 5
[    30.098] (**) evdev: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    30.098] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.2/usb5/5-1/5-1:1.0/input/input2/event2"
[    30.098] (II) XINPUT: Adding extended input device "Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)" (type: MOUSE, id 8)
[    30.098] (II) evdev: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): initialized for relative axes.
[    30.098] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): (accel) keeping acceleration scheme 1
[    30.098] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): (accel) acceleration profile 0
[    30.098] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): (accel) acceleration factor: 2.000
[    30.098] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): (accel) acceleration threshold: 4
[    30.099] (II) config/udev: Adding input device Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) (/dev/input/mouse0)
[    30.099] (II) No input driver specified, ignoring this device.
[    30.099] (II) This device may have been added with another device file.
[    30.099] (II) config/udev: Adding input device Microsoft Comfort Curve Keyboard 2000 (/dev/input/event3)
[    30.099] (**) Microsoft Comfort Curve Keyboard 2000: Applying InputClass "evdev keyboard catchall"
[    30.099] (II) Using input driver 'evdev' for 'Microsoft Comfort Curve Keyboard 2000'
[    30.099] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    30.099] (**) Microsoft Comfort Curve Keyboard 2000: always reports core events
[    30.099] (**) evdev: Microsoft Comfort Curve Keyboard 2000: Device: "/dev/input/event3"
[    30.099] (--) evdev: Microsoft Comfort Curve Keyboard 2000: Vendor 0x45e Product 0xdd
[    30.099] (--) evdev: Microsoft Comfort Curve Keyboard 2000: Found keys
[    30.099] (II) evdev: Microsoft Comfort Curve Keyboard 2000: Configuring as keyboard
[    30.100] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.2/usb5/5-2/5-2:1.0/input/input3/event3"
[    30.100] (II) XINPUT: Adding extended input device "Microsoft Comfort Curve Keyboard 2000" (type: KEYBOARD, id 9)
[    30.100] (**) Option "xkb_rules" "evdev"
[    30.100] (**) Option "xkb_model" "pc105"
[    30.100] (**) Option "xkb_layout" "us"
[    30.101] (II) config/udev: Adding input device Microsoft Comfort Curve Keyboard 2000 (/dev/input/event4)
[    30.101] (**) Microsoft Comfort Curve Keyboard 2000: Applying InputClass "evdev keyboard catchall"
[    30.101] (II) Using input driver 'evdev' for 'Microsoft Comfort Curve Keyboard 2000'
[    30.101] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    30.101] (**) Microsoft Comfort Curve Keyboard 2000: always reports core events
[    30.101] (**) evdev: Microsoft Comfort Curve Keyboard 2000: Device: "/dev/input/event4"
[    30.101] (--) evdev: Microsoft Comfort Curve Keyboard 2000: Vendor 0x45e Product 0xdd
[    30.101] (--) evdev: Microsoft Comfort Curve Keyboard 2000: Found 1 mouse buttons
[    30.101] (--) evdev: Microsoft Comfort Curve Keyboard 2000: Found scroll wheel(s)
[    30.101] (--) evdev: Microsoft Comfort Curve Keyboard 2000: Found relative axes
[    30.101] (II) evdev: Microsoft Comfort Curve Keyboard 2000: Forcing relative x/y axes to exist.
[    30.101] (--) evdev: Microsoft Comfort Curve Keyboard 2000: Found absolute axes
[    30.101] (II) evdev: Microsoft Comfort Curve Keyboard 2000: Forcing absolute x/y axes to exist.
[    30.101] (--) evdev: Microsoft Comfort Curve Keyboard 2000: Found keys
[    30.101] (II) evdev: Microsoft Comfort Curve Keyboard 2000: Configuring as mouse
[    30.101] (II) evdev: Microsoft Comfort Curve Keyboard 2000: Configuring as keyboard
[    30.101] (II) evdev: Microsoft Comfort Curve Keyboard 2000: Adding scrollwheel support
[    30.101] (**) evdev: Microsoft Comfort Curve Keyboard 2000: YAxisMapping: buttons 4 and 5
[    30.101] (**) evdev: Microsoft Comfort Curve Keyboard 2000: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    30.101] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.2/usb5/5-2/5-2:1.1/input/input4/event4"
[    30.101] (II) XINPUT: Adding extended input device "Microsoft Comfort Curve Keyboard 2000" (type: KEYBOARD, id 10)
[    30.101] (**) Option "xkb_rules" "evdev"
[    30.101] (**) Option "xkb_model" "pc105"
[    30.101] (**) Option "xkb_layout" "us"
[    30.101] (II) evdev: Microsoft Comfort Curve Keyboard 2000: initialized for relative axes.
[    30.101] (WW) evdev: Microsoft Comfort Curve Keyboard 2000: ignoring absolute axes.
[    30.102] (**) Microsoft Comfort Curve Keyboard 2000: (accel) keeping acceleration scheme 1
[    30.102] (**) Microsoft Comfort Curve Keyboard 2000: (accel) acceleration profile 0
[    30.102] (**) Microsoft Comfort Curve Keyboard 2000: (accel) acceleration factor: 2.000
[    30.102] (**) Microsoft Comfort Curve Keyboard 2000: (accel) acceleration threshold: 4
[    30.102] (II) config/udev: Adding input device iMON Panel, Knob and Mouse(15c2:ffdc) (/dev/input/event5)
[    30.102] (**) iMON Panel, Knob and Mouse(15c2:ffdc): Applying InputClass "evdev pointer catchall"
[    30.102] (**) iMON Panel, Knob and Mouse(15c2:ffdc): Applying InputClass "evdev keyboard catchall"
[    30.102] (II) Using input driver 'evdev' for 'iMON Panel, Knob and Mouse(15c2:ffdc)'
[    30.102] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    30.105] (**) iMON Panel, Knob and Mouse(15c2:ffdc): always reports core events
[    30.105] (**) evdev: iMON Panel, Knob and Mouse(15c2:ffdc): Device: "/dev/input/event5"
[    30.105] (--) evdev: iMON Panel, Knob and Mouse(15c2:ffdc): Vendor 0x15c2 Product 0xffdc
[    30.105] (--) evdev: iMON Panel, Knob and Mouse(15c2:ffdc): Found 3 mouse buttons
[    30.105] (--) evdev: iMON Panel, Knob and Mouse(15c2:ffdc): Found scroll wheel(s)
[    30.105] (--) evdev: iMON Panel, Knob and Mouse(15c2:ffdc): Found relative axes
[    30.105] (--) evdev: iMON Panel, Knob and Mouse(15c2:ffdc): Found x and y relative axes
[    30.105] (--) evdev: iMON Panel, Knob and Mouse(15c2:ffdc): Found keys
[    30.105] (II) evdev: iMON Panel, Knob and Mouse(15c2:ffdc): Configuring as mouse
[    30.105] (II) evdev: iMON Panel, Knob and Mouse(15c2:ffdc): Configuring as keyboard
[    30.105] (II) evdev: iMON Panel, Knob and Mouse(15c2:ffdc): Adding scrollwheel support
[    30.105] (**) evdev: iMON Panel, Knob and Mouse(15c2:ffdc): YAxisMapping: buttons 4 and 5
[    30.105] (**) evdev: iMON Panel, Knob and Mouse(15c2:ffdc): EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    30.105] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.3/usb6/6-1/6-1:1.0/input/input5/event5"
[    30.105] (II) XINPUT: Adding extended input device "iMON Panel, Knob and Mouse(15c2:ffdc)" (type: KEYBOARD, id 11)
[    30.105] (**) Option "xkb_rules" "evdev"
[    30.105] (**) Option "xkb_model" "pc105"
[    30.105] (**) Option "xkb_layout" "us"
[    30.106] (II) evdev: iMON Panel, Knob and Mouse(15c2:ffdc): initialized for relative axes.
[    30.106] (**) iMON Panel, Knob and Mouse(15c2:ffdc): (accel) keeping acceleration scheme 1
[    30.106] (**) iMON Panel, Knob and Mouse(15c2:ffdc): (accel) acceleration profile 0
[    30.106] (**) iMON Panel, Knob and Mouse(15c2:ffdc): (accel) acceleration factor: 2.000
[    30.106] (**) iMON Panel, Knob and Mouse(15c2:ffdc): (accel) acceleration threshold: 4
[    30.107] (II) config/udev: Adding input device iMON Panel, Knob and Mouse(15c2:ffdc) (/dev/input/mouse1)
[    30.107] (II) No input driver specified, ignoring this device.
[    30.107] (II) This device may have been added with another device file.
[    30.107] (II) config/udev: Adding input device iMON Remote (15c2:ffdc) (/dev/input/event14)
[    30.107] (**) iMON Remote (15c2:ffdc): Applying InputClass "evdev keyboard catchall"
[    30.107] (II) Using input driver 'evdev' for 'iMON Remote (15c2:ffdc)'
[    30.107] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    30.107] (**) iMON Remote (15c2:ffdc): always reports core events
[    30.107] (**) evdev: iMON Remote (15c2:ffdc): Device: "/dev/input/event14"
[    30.107] (--) evdev: iMON Remote (15c2:ffdc): Vendor 0x15c2 Product 0xffdc
[    30.107] (--) evdev: iMON Remote (15c2:ffdc): Found keys
[    30.107] (II) evdev: iMON Remote (15c2:ffdc): Configuring as keyboard
[    30.107] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.3/usb6/6-1/6-1:1.0/rc/rc0/input14/event14"
[    30.107] (II) XINPUT: Adding extended input device "iMON Remote (15c2:ffdc)" (type: KEYBOARD, id 12)
[    30.107] (**) Option "xkb_rules" "evdev"
[    30.107] (**) Option "xkb_model" "pc105"
[    30.107] (**) Option "xkb_layout" "us"
[    30.108] (II) config/udev: Adding input device HDA ATI SB Line-Out Side (/dev/input/event10)
[    30.108] (II) No input driver specified, ignoring this device.
[    30.108] (II) This device may have been added with another device file.
[    30.108] (II) config/udev: Adding input device HDA ATI SB Line-Out CLFE (/dev/input/event11)
[    30.109] (II) No input driver specified, ignoring this device.
[    30.109] (II) This device may have been added with another device file.
[    30.109] (II) config/udev: Adding input device HDA ATI SB Line-Out Surround (/dev/input/event12)
[    30.109] (II) No input driver specified, ignoring this device.
[    30.109] (II) This device may have been added with another device file.
[    30.109] (II) config/udev: Adding input device HDA ATI SB Line-Out Front (/dev/input/event13)
[    30.109] (II) No input driver specified, ignoring this device.
[    30.109] (II) This device may have been added with another device file.
[    30.109] (II) config/udev: Adding input device HDA ATI SB Line (/dev/input/event6)
[    30.110] (II) No input driver specified, ignoring this device.
[    30.110] (II) This device may have been added with another device file.
[    30.110] (II) config/udev: Adding input device HDA ATI SB Front Mic (/dev/input/event7)
[    30.110] (II) No input driver specified, ignoring this device.
[    30.110] (II) This device may have been added with another device file.
[    30.110] (II) config/udev: Adding input device HDA ATI SB Rear Mic (/dev/input/event8)
[    30.110] (II) No input driver specified, ignoring this device.
[    30.110] (II) This device may have been added with another device file.
[    30.110] (II) config/udev: Adding input device HDA ATI SB Front Headphone (/dev/input/event9)
[    30.111] (II) No input driver specified, ignoring this device.
[    30.111] (II) This device may have been added with another device file.
[    30.111] (II) config/udev: Adding input device IR-receiver inside an USB DVB receiver (/dev/input/event15)
[    30.111] (**) IR-receiver inside an USB DVB receiver: Applying InputClass "evdev keyboard catchall"
[    30.111] (II) Using input driver 'evdev' for 'IR-receiver inside an USB DVB receiver'
[    30.111] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    30.111] (**) IR-receiver inside an USB DVB receiver: always reports core events
[    30.111] (**) evdev: IR-receiver inside an USB DVB receiver: Device: "/dev/input/event15"
[    30.111] (--) evdev: IR-receiver inside an USB DVB receiver: Vendor 0xfe9 Product 0xdb78
[    30.111] (--) evdev: IR-receiver inside an USB DVB receiver: Found keys
[    30.111] (II) evdev: IR-receiver inside an USB DVB receiver: Configuring as keyboard
[    30.111] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.4/0000:02:07.2/usb2/2-1/input/input15/event15"
[    30.111] (II) XINPUT: Adding extended input device "IR-receiver inside an USB DVB receiver" (type: KEYBOARD, id 13)
[    30.111] (**) Option "xkb_rules" "evdev"
[    30.111] (**) Option "xkb_model" "pc105"
[    30.111] (**) Option "xkb_layout" "us"
[    30.308] (II) evdev: Power Button: Close
[    30.308] (II) UnloadModule: "evdev"
[    30.308] (II) Unloading evdev
[    30.336] (II) evdev: Power Button: Close
[    30.336] (II) UnloadModule: "evdev"
[    30.336] (II) Unloading evdev
[    30.368] (II) evdev: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Close
[    30.368] (II) UnloadModule: "evdev"
[    30.368] (II) Unloading evdev
[    30.400] (II) evdev: Microsoft Comfort Curve Keyboard 2000: Close
[    30.400] (II) UnloadModule: "evdev"
[    30.400] (II) Unloading evdev
[    30.432] (II) evdev: Microsoft Comfort Curve Keyboard 2000: Close
[    30.432] (II) UnloadModule: "evdev"
[    30.432] (II) Unloading evdev
[    30.472] (II) evdev: iMON Panel, Knob and Mouse(15c2:ffdc): Close
[    30.472] (II) UnloadModule: "evdev"
[    30.472] (II) Unloading evdev
[    30.496] (II) evdev: iMON Remote (15c2:ffdc): Close
[    30.496] (II) UnloadModule: "evdev"
[    30.496] (II) Unloading evdev
[    30.536] (II) evdev: IR-receiver inside an USB DVB receiver: Close
[    30.536] (II) UnloadModule: "evdev"
[    30.536] (II) Unloading evdev
[    30.572]  ddxSigGiveUp: Closing log
[    30.572] Server terminated successfully (0). Closing log file.


```

The kern.log file shows:
```

Dec  1 17:46:32 duper kernel: imklog 5.8.6, log source = /proc/kmsg started.
Dec  1 17:46:32 duper kernel: [    0.000000] Initializing cgroup subsys cpuset
Dec  1 17:46:32 duper kernel: [    0.000000] Initializing cgroup subsys cpu
Dec  1 17:46:32 duper kernel: [    0.000000] Linux version 3.2.0-33-generic (buildd@batsu) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #52-Ubuntu SMP Thu Oct 18 16:29:15 UTC 2012 (Ubuntu 3.2.0-33.52-generic 3.2.31)
Dec  1 17:46:32 duper kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-33-generic root=UUID=c4bb9b50-7fac-4e2b-9d68-77dd493c01b3 ro quiet splash radeon.audio=1 vt.handoff=7
Dec  1 17:46:32 duper kernel: [    0.000000] KERNEL supported cpus:
Dec  1 17:46:32 duper kernel: [    0.000000]   Intel GenuineIntel
Dec  1 17:46:32 duper kernel: [    0.000000]   AMD AuthenticAMD
Dec  1 17:46:32 duper kernel: [    0.000000]   Centaur CentaurHauls
Dec  1 17:46:32 duper kernel: [    0.000000] BIOS-provided physical RAM map:
Dec  1 17:46:32 duper kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Dec  1 17:46:32 duper kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Dec  1 17:46:32 duper kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Dec  1 17:46:32 duper kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000cfee0000 (usable)
Dec  1 17:46:32 duper kernel: [    0.000000]  BIOS-e820: 00000000cfee0000 - 00000000cfee3000 (ACPI NVS)
Dec  1 17:46:32 duper kernel: [    0.000000]  BIOS-e820: 00000000cfee3000 - 00000000cfef0000 (ACPI data)
Dec  1 17:46:32 duper kernel: [    0.000000]  BIOS-e820: 00000000cfef0000 - 00000000cff00000 (reserved)
Dec  1 17:46:32 duper kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Dec  1 17:46:32 duper kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Dec  1 17:46:32 duper kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000128000000 (usable)
Dec  1 17:46:32 duper kernel: [    0.000000] NX (Execute Disable) protection: active
Dec  1 17:46:32 duper kernel: [    0.000000] DMI 2.4 present.
Dec  1 17:46:32 duper kernel: [    0.000000] DMI: Gigabyte Technology Co., Ltd. GA-MA69GM-S2H/GA-MA69GM-S2H, BIOS F2 07/27/2007
Dec  1 17:46:32 duper kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Dec  1 17:46:32 duper kernel: [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
Dec  1 17:46:32 duper kernel: [    0.000000] No AGP bridge found
Dec  1 17:46:32 duper kernel: [    0.000000] last_pfn = 0x128000 max_arch_pfn = 0x400000000
Dec  1 17:46:32 duper kernel: [    0.000000] MTRR default type: uncachable
Dec  1 17:46:32 duper kernel: [    0.000000] MTRR fixed ranges enabled:
Dec  1 17:46:32 duper kernel: [    0.000000]   00000-9FFFF write-back
Dec  1 17:46:32 duper kernel: [    0.000000]   A0000-BFFFF uncachable
Dec  1 17:46:32 duper kernel: [    0.000000]   C0000-C7FFF write-protect
Dec  1 17:46:32 duper kernel: [    0.000000]   C8000-FFFFF uncachable
Dec  1 17:46:32 duper kernel: [    0.000000] MTRR variable ranges enabled:
Dec  1 17:46:32 duper kernel: [    0.000000]   0 base 0000000000 mask FF80000000 write-back
Dec  1 17:46:32 duper kernel: [    0.000000]   1 base 0080000000 mask FFC0000000 write-back
Dec  1 17:46:32 duper kernel: [    0.000000]   2 base 00C0000000 mask FFF0000000 write-back
Dec  1 17:46:32 duper kernel: [    0.000000]   3 base 00CFF00000 mask FFFFF00000 uncachable
Dec  1 17:46:32 duper kernel: [    0.000000]   4 base 0100000000 mask FFE0000000 write-back
Dec  1 17:46:32 duper kernel: [    0.000000]   5 base 0120000000 mask FFF8000000 write-back
Dec  1 17:46:32 duper kernel: [    0.000000]   6 disabled
Dec  1 17:46:32 duper kernel: [    0.000000]   7 disabled
Dec  1 17:46:32 duper kernel: [    0.000000] TOM2: 0000000128000000 aka 4736M
Dec  1 17:46:32 duper kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Dec  1 17:46:32 duper kernel: [    0.000000] original variable MTRRs
Dec  1 17:46:32 duper kernel: [    0.000000] reg 0, base: 0GB, range: 2GB, type WB
Dec  1 17:46:32 duper kernel: [    0.000000] reg 1, base: 2GB, range: 1GB, type WB
Dec  1 17:46:32 duper kernel: [    0.000000] reg 2, base: 3GB, range: 256MB, type WB
Dec  1 17:46:32 duper kernel: [    0.000000] reg 3, base: 3327MB, range: 1MB, type UC
Dec  1 17:46:32 duper kernel: [    0.000000] reg 4, base: 4GB, range: 512MB, type WB
Dec  1 17:46:32 duper kernel: [    0.000000] reg 5, base: 4608MB, range: 128MB, type WB
Dec  1 17:46:32 duper kernel: [    0.000000] total RAM covered: 3327M
Dec  1 17:46:32 duper kernel: [    0.000000] Found optimal setting for mtrr clean up
Dec  1 17:46:32 duper kernel: [    0.000000]  gran_size: 64K    chunk_size: 2M  num_reg: 4      lose cover RAM: 0G
Dec  1 17:46:32 duper kernel: [    0.000000] New variable MTRRs
Dec  1 17:46:32 duper kernel: [    0.000000] reg 0, base: 0GB, range: 2GB, type WB
Dec  1 17:46:32 duper kernel: [    0.000000] reg 1, base: 2GB, range: 1GB, type WB
Dec  1 17:46:32 duper kernel: [    0.000000] reg 2, base: 3GB, range: 256MB, type WB
Dec  1 17:46:32 duper kernel: [    0.000000] reg 3, base: 3327MB, range: 1MB, type UC
Dec  1 17:46:32 duper kernel: [    0.000000] e820 update range: 00000000cff00000 - 0000000100000000 (usable) ==> (reserved)
Dec  1 17:46:32 duper kernel: [    0.000000] last_pfn = 0xcfee0 max_arch_pfn = 0x400000000
Dec  1 17:46:32 duper kernel: [    0.000000] found SMP MP-table at [ffff8800000f4fb0] f4fb0
Dec  1 17:46:32 duper kernel: [    0.000000] initial memory mapped : 0 - 20000000
Dec  1 17:46:32 duper kernel: [    0.000000] Base memory trampoline at [ffff88000009a000] 9a000 size 20480
Dec  1 17:46:32 duper kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000cfee0000
Dec  1 17:46:32 duper kernel: [    0.000000]  0000000000 - 00cfe00000 page 2M
Dec  1 17:46:32 duper kernel: [    0.000000]  00cfe00000 - 00cfee0000 page 4k
Dec  1 17:46:32 duper kernel: [    0.000000] kernel direct mapping tables up to cfee0000 @ 1fffa000-20000000
Dec  1 17:46:32 duper kernel: [    0.000000] init_memory_mapping: 0000000100000000-0000000128000000
Dec  1 17:46:32 duper kernel: [    0.000000]  0100000000 - 0128000000 page 2M
Dec  1 17:46:32 duper kernel: [    0.000000] kernel direct mapping tables up to 128000000 @ cfeda000-cfee0000
Dec  1 17:46:32 duper kernel: [    0.000000] RAMDISK: 35eee000 - 36f6f000
Dec  1 17:46:32 duper kernel: [    0.000000] ACPI: RSDP 00000000000f6960 00014 (v00 GBT   )
Dec  1 17:46:32 duper kernel: [    0.000000] ACPI: RSDT 00000000cfee3000 00038 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Dec  1 17:46:32 duper kernel: [    0.000000] ACPI: FACP 00000000cfee3040 00074 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Dec  1 17:46:32 duper kernel: [    0.000000] ACPI: DSDT 00000000cfee30c0 0471E (v01 GBT    GBTUACPI 00001000 MSFT 0100000C)
Dec  1 17:46:32 duper kernel: [    0.000000] ACPI: FACS 00000000cfee0000 00040
Dec  1 17:46:32 duper kernel: [    0.000000] ACPI: SSDT 00000000cfee7880 00206 (v01 PTLTD  POWERNOW 00000001  LTP 00000001)
Dec  1 17:46:32 duper kernel: [    0.000000] ACPI: HPET 00000000cfee7ac0 00038 (v01 GBT    GBTUACPI 42302E31 GBTU 00000098)
Dec  1 17:46:32 duper kernel: [    0.000000] ACPI: MCFG 00000000cfee7b00 0003C (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Dec  1 17:46:32 duper kernel: [    0.000000] ACPI: APIC 00000000cfee7800 00068 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Dec  1 17:46:32 duper kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Dec  1 17:46:32 duper kernel: [    0.000000] Scanning NUMA topology in Northbridge 24
Dec  1 17:46:32 duper kernel: [    0.000000] No NUMA configuration found
Dec  1 17:46:32 duper kernel: [    0.000000] Faking a node at 0000000000000000-0000000128000000
Dec  1 17:46:32 duper kernel: [    0.000000] Initmem setup node 0 0000000000000000-0000000128000000
Dec  1 17:46:32 duper kernel: [    0.000000]   NODE_DATA [0000000127ffb000 - 0000000127ffffff]
Dec  1 17:46:32 duper kernel: [    0.000000]  [ffffea0000000000-ffffea00049fffff] PMD -> [ffff880123800000-ffff8801275fffff] on node 0
Dec  1 17:46:32 duper kernel: [    0.000000] Zone PFN ranges:
Dec  1 17:46:32 duper kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Dec  1 17:46:32 duper kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Dec  1 17:46:32 duper kernel: [    0.000000]   Normal   0x00100000 -> 0x00128000
Dec  1 17:46:32 duper kernel: [    0.000000] Movable zone start PFN for each node
Dec  1 17:46:32 duper kernel: [    0.000000] early_node_map[3] active PFN ranges
Dec  1 17:46:32 duper kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Dec  1 17:46:32 duper kernel: [    0.000000]     0: 0x00000100 -> 0x000cfee0
Dec  1 17:46:32 duper kernel: [    0.000000]     0: 0x00100000 -> 0x00128000
Dec  1 17:46:32 duper kernel: [    0.000000] On node 0 totalpages: 1015407
Dec  1 17:46:32 duper kernel: [    0.000000]   DMA zone: 64 pages used for memmap
Dec  1 17:46:32 duper kernel: [    0.000000]   DMA zone: 5 pages reserved
Dec  1 17:46:32 duper kernel: [    0.000000]   DMA zone: 3914 pages, LIFO batch:0
Dec  1 17:46:32 duper kernel: [    0.000000]   DMA32 zone: 16320 pages used for memmap
Dec  1 17:46:32 duper kernel: [    0.000000]   DMA32 zone: 831264 pages, LIFO batch:31
Dec  1 17:46:32 duper kernel: [    0.000000]   Normal zone: 2560 pages used for memmap
Dec  1 17:46:32 duper kernel: [    0.000000]   Normal zone: 161280 pages, LIFO batch:31
Dec  1 17:46:32 duper kernel: [    0.000000] Detected use of extended apic ids on hypertransport bus
Dec  1 17:46:32 duper kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x4008
Dec  1 17:46:32 duper kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Dec  1 17:46:32 duper kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Dec  1 17:46:32 duper kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Dec  1 17:46:32 duper kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
Dec  1 17:46:32 duper kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
Dec  1 17:46:32 duper kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Dec  1 17:46:32 duper kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
Dec  1 17:46:32 duper kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Dec  1 17:46:32 duper kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Dec  1 17:46:32 duper kernel: [    0.000000] ACPI: IRQ0 used by override.
Dec  1 17:46:32 duper kernel: [    0.000000] ACPI: IRQ2 used by override.
Dec  1 17:46:32 duper kernel: [    0.000000] ACPI: IRQ9 used by override.
Dec  1 17:46:32 duper kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Dec  1 17:46:32 duper kernel: [    0.000000] ACPI: HPET id: 0x10b9a201 base: 0xfed00000
Dec  1 17:46:32 duper kernel: [    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
Dec  1 17:46:32 duper kernel: [    0.000000] nr_irqs_gsi: 40
Dec  1 17:46:32 duper kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Dec  1 17:46:32 duper kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Dec  1 17:46:32 duper kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Dec  1 17:46:32 duper kernel: [    0.000000] PM: Registered nosave memory: 00000000cfee0000 - 00000000cfee3000
Dec  1 17:46:32 duper kernel: [    0.000000] PM: Registered nosave memory: 00000000cfee3000 - 00000000cfef0000
Dec  1 17:46:32 duper kernel: [    0.000000] PM: Registered nosave memory: 00000000cfef0000 - 00000000cff00000
Dec  1 17:46:32 duper kernel: [    0.000000] PM: Registered nosave memory: 00000000cff00000 - 00000000e0000000
Dec  1 17:46:32 duper kernel: [    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
Dec  1 17:46:32 duper kernel: [    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000fec00000
Dec  1 17:46:32 duper kernel: [    0.000000] PM: Registered nosave memory: 00000000fec00000 - 0000000100000000
Dec  1 17:46:32 duper kernel: [    0.000000] Allocating PCI resources starting at cff00000 (gap: cff00000:10100000)
Dec  1 17:46:32 duper kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Dec  1 17:46:32 duper kernel: [    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:2 nr_node_ids:1
Dec  1 17:46:32 duper kernel: [    0.000000] PERCPU: Embedded 28 pages/cpu @ffff880127c00000 s83136 r8192 d23360 u1048576
Dec  1 17:46:32 duper kernel: [    0.000000] pcpu-alloc: s83136 r8192 d23360 u1048576 alloc=1*2097152
Dec  1 17:46:32 duper kernel: [    0.000000] pcpu-alloc: [0] 0 1
Dec  1 17:46:32 duper kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 996458
Dec  1 17:46:32 duper kernel: [    0.000000] Policy zone: Normal
Dec  1 17:46:32 duper kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-33-generic root=UUID=c4bb9b50-7fac-4e2b-9d68-77dd493c01b3 ro quiet splash radeon.audio=1 vt.handoff=7
Dec  1 17:46:32 duper kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Dec  1 17:46:32 duper kernel: [    0.000000] Checking aperture...
Dec  1 17:46:32 duper kernel: [    0.000000] No AGP bridge found
Dec  1 17:46:32 duper kernel: [    0.000000] Node 0: aperture @ 2070000000 size 32 MB
Dec  1 17:46:32 duper kernel: [    0.000000] Aperture beyond 4GB. Ignoring.
Dec  1 17:46:32 duper kernel: [    0.000000] Your BIOS doesn't leave a aperture memory hole
Dec  1 17:46:32 duper kernel: [    0.000000] Please enable the IOMMU option in the BIOS setup
Dec  1 17:46:32 duper kernel: [    0.000000] This costs you 64 MB of RAM
Dec  1 17:46:32 duper kernel: [    0.000000] Mapping aperture over 65536 KB of RAM @ c4000000
Dec  1 17:46:32 duper kernel: [    0.000000] PM: Registered nosave memory: 00000000c4000000 - 00000000c8000000
Dec  1 17:46:32 duper kernel: [    0.000000] Memory: 3833592k/4849664k available (6561k kernel code, 788036k absent, 228036k reserved, 6642k data, 924k init)
Dec  1 17:46:32 duper kernel: [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Dec  1 17:46:32 duper kernel: [    0.000000] Hierarchical RCU implementation.
Dec  1 17:46:32 duper kernel: [    0.000000]    RCU dyntick-idle grace-period acceleration is enabled.
Dec  1 17:46:32 duper kernel: [    0.000000] NR_IRQS:16640 nr_irqs:512 16
Dec  1 17:46:32 duper kernel: [    0.000000] spurious 8259A interrupt: IRQ7.
Dec  1 17:46:32 duper kernel: [    0.000000] vt handoff: transparent VT on vt#7
Dec  1 17:46:32 duper kernel: [    0.000000] Console: colour dummy device 80x25
Dec  1 17:46:32 duper kernel: [    0.000000] console [tty0] enabled
Dec  1 17:46:32 duper kernel: [    0.000000] allocated 32505856 bytes of page_cgroup
Dec  1 17:46:32 duper kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Dec  1 17:46:32 duper kernel: [    0.000000] hpet clockevent registered
Dec  1 17:46:32 duper kernel: [    0.000000] Fast TSC calibration using PIT
Dec  1 17:46:32 duper kernel: [    0.000000] Detected 2104.659 MHz processor.
Dec  1 17:46:32 duper kernel: [    0.000000] Marking TSC unstable due to TSCs unsynchronized
Dec  1 17:46:32 duper kernel: [    0.008007] Calibrating delay loop (skipped), value calculated using timer frequency.. 4209.31 BogoMIPS (lpj=8418636)
Dec  1 17:46:32 duper kernel: [    0.008012] pid_max: default: 32768 minimum: 301
Dec  1 17:46:32 duper kernel: [    0.008043] Security Framework initialized
Dec  1 17:46:32 duper kernel: [    0.008062] AppArmor: AppArmor initialized
Dec  1 17:46:32 duper kernel: [    0.008064] Yama: becoming mindful.
Dec  1 17:46:32 duper kernel: [    0.008502] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
Dec  1 17:46:32 duper kernel: [    0.012128] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
Dec  1 17:46:32 duper kernel: [    0.013456] Mount-cache hash table entries: 256
Dec  1 17:46:32 duper kernel: [    0.013626] Initializing cgroup subsys cpuacct
Dec  1 17:46:32 duper kernel: [    0.013633] Initializing cgroup subsys memory
Dec  1 17:46:32 duper kernel: [    0.013645] Initializing cgroup subsys devices
Dec  1 17:46:32 duper kernel: [    0.013647] Initializing cgroup subsys freezer
Dec  1 17:46:32 duper kernel: [    0.013650] Initializing cgroup subsys blkio
Dec  1 17:46:32 duper kernel: [    0.013657] Initializing cgroup subsys perf_event
Dec  1 17:46:32 duper kernel: [    0.013694] tseg: 00cff00000
Dec  1 17:46:32 duper kernel: [    0.013697] CPU: Physical Processor ID: 0
Dec  1 17:46:32 duper kernel: [    0.013698] CPU: Processor Core ID: 0
Dec  1 17:46:32 duper kernel: [    0.013701] mce: CPU supports 5 MCE banks
Dec  1 17:46:32 duper kernel: [    0.013713] using AMD E400 aware idle routine
Dec  1 17:46:32 duper kernel: [    0.015576] ACPI: Core revision 20110623
Dec  1 17:46:32 duper kernel: [    0.020044] ftrace: allocating 27018 entries in 106 pages
Dec  1 17:46:32 duper kernel: [    0.028730] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Dec  1 17:46:32 duper kernel: [    0.070735] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 4000+ stepping 01
Dec  1 17:46:32 duper kernel: [    0.072003] Performance Events: AMD PMU driver.
Dec  1 17:46:32 duper kernel: [    0.072003] ... version:                0
Dec  1 17:46:32 duper kernel: [    0.072003] ... bit width:              48
Dec  1 17:46:32 duper kernel: [    0.072003] ... generic registers:      4
Dec  1 17:46:32 duper kernel: [    0.072003] ... value mask:             0000ffffffffffff
Dec  1 17:46:32 duper kernel: [    0.072003] ... max period:             00007fffffffffff
Dec  1 17:46:32 duper kernel: [    0.072003] ... fixed-purpose events:   0
Dec  1 17:46:32 duper kernel: [    0.072003] ... event mask:             000000000000000f
Dec  1 17:46:32 duper kernel: [    0.072003] NMI watchdog enabled, takes one hw-pmu counter.
Dec  1 17:46:32 duper kernel: [    0.072003] Booting Node   0, Processors  #1 Ok.
Dec  1 17:46:32 duper kernel: [    0.072003] smpboot cpu 1: start_ip = 9a000
Dec  1 17:46:32 duper kernel: [    0.156061] NMI watchdog enabled, takes one hw-pmu counter.
Dec  1 17:46:32 duper kernel: [    0.156091] Brought up 2 CPUs
Dec  1 17:46:32 duper kernel: [    0.156093] Total of 2 processors activated (8418.92 BogoMIPS).
Dec  1 17:46:32 duper kernel: [    0.156723] devtmpfs: initialized
Dec  1 17:46:32 duper kernel: [    0.158153] EVM: security.selinux
Dec  1 17:46:32 duper kernel: [    0.158155] EVM: security.SMACK64
Dec  1 17:46:32 duper kernel: [    0.158157] EVM: security.capability
Dec  1 17:46:32 duper kernel: [    0.158233] PM: Registering ACPI NVS region at cfee0000 (12288 bytes)
Dec  1 17:46:32 duper kernel: [    0.160137] print_constraints: dummy:
Dec  1 17:46:32 duper kernel: [    0.160170] RTC time:  6:46:16, date: 12/01/12
Dec  1 17:46:32 duper kernel: [    0.160218] NET: Registered protocol family 16
Dec  1 17:46:32 duper kernel: [    0.160290] Trying to unpack rootfs image as initramfs...
Dec  1 17:46:32 duper kernel: [    0.160397] node 0 link 0: io port [d000, ffff]
Dec  1 17:46:32 duper kernel: [    0.160401] TOM: 00000000d8000000 aka 3456M
Dec  1 17:46:32 duper kernel: [    0.160404] node 0 link 0: mmio [a0000, bffff]
Dec  1 17:46:32 duper kernel: [    0.160407] node 0 link 0: mmio [d8000000, dfffffff]
Dec  1 17:46:32 duper kernel: [    0.160410] node 0 link 0: mmio [e0000000, fe02ffff]
Dec  1 17:46:32 duper kernel: [    0.160413] node 0 link 0: mmio [e0000000, efffffff]
Dec  1 17:46:32 duper kernel: [    0.160416] TOM2: 0000000128000000 aka 4736M
Dec  1 17:46:32 duper kernel: [    0.160419] bus: [00, 02] on node 0 link 0
Dec  1 17:46:32 duper kernel: [    0.160422] bus: 00 index 0 [io  0x0000-0xffff]
Dec  1 17:46:32 duper kernel: [    0.160424] bus: 00 index 1 [mem 0x000a0000-0x000bffff]
Dec  1 17:46:32 duper kernel: [    0.160427] bus: 00 index 2 [mem 0xd8000000-0xffffffff]
Dec  1 17:46:32 duper kernel: [    0.160429] bus: 00 index 3 [mem 0x128000000-0xfcffffffff]
Dec  1 17:46:32 duper kernel: [    0.160441] ACPI: bus type pci registered
Dec  1 17:46:32 duper kernel: [    0.160520] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Dec  1 17:46:32 duper kernel: [    0.160524] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
Dec  1 17:46:32 duper kernel: [    0.188004] PCI: Using configuration type 1 for base access
Dec  1 17:46:32 duper kernel: [    0.189489] bio: create slab <bio-0> at 0
Dec  1 17:46:32 duper kernel: [    0.189618] ACPI: Added _OSI(Module Device)
Dec  1 17:46:32 duper kernel: [    0.189620] ACPI: Added _OSI(Processor Device)
Dec  1 17:46:32 duper kernel: [    0.189623] ACPI: Added _OSI(3.0 _SCP Extensions)
Dec  1 17:46:32 duper kernel: [    0.189625] ACPI: Added _OSI(Processor Aggregator Device)
Dec  1 17:46:32 duper kernel: [    0.190317] ACPI: EC: Look up EC in DSDT
Dec  1 17:46:32 duper kernel: [    0.191100] ACPI: Executed 1 blocks of module-level executable AML code
Dec  1 17:46:32 duper kernel: [    0.194988] ACPI: Interpreter enabled
Dec  1 17:46:32 duper kernel: [    0.194994] ACPI: (supports S0 S1 S4 S5)
Dec  1 17:46:32 duper kernel: [    0.195016] ACPI: Using IOAPIC for interrupt routing
Dec  1 17:46:32 duper kernel: [    0.227551] ACPI: No dock devices found.
Dec  1 17:46:32 duper kernel: [    0.227555] HEST: Table not found.
Dec  1 17:46:32 duper kernel: [    0.227560] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
Dec  1 17:46:32 duper kernel: [    0.227645] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Dec  1 17:46:32 duper kernel: [    0.227830] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
Dec  1 17:46:32 duper kernel: [    0.227834] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
Dec  1 17:46:32 duper kernel: [    0.227837] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
Dec  1 17:46:32 duper kernel: [    0.227840] pci_root PNP0A03:00: host bridge window [mem 0x000c0000-0x000dffff] (ignored)
Dec  1 17:46:32 duper kernel: [    0.227843] pci_root PNP0A03:00: host bridge window [mem 0xd8000000-0xfebfffff] (ignored)
Dec  1 17:46:32 duper kernel: [    0.227854] pci 0000:00:00.0: [1002:7910] type 0 class 0x000600
Dec  1 17:46:32 duper kernel: [    0.227884] pci 0000:00:01.0: [1002:7912] type 1 class 0x000604
Dec  1 17:46:32 duper kernel: [    0.227944] pci 0000:00:12.0: [1002:4380] type 0 class 0x000101
Dec  1 17:46:32 duper kernel: [    0.227963] pci 0000:00:12.0: reg 10: [io  0xff00-0xff07]
Dec  1 17:46:32 duper kernel: [    0.227974] pci 0000:00:12.0: reg 14: [io  0xfe00-0xfe03]
Dec  1 17:46:32 duper kernel: [    0.227985] pci 0000:00:12.0: reg 18: [io  0xfd00-0xfd07]
Dec  1 17:46:32 duper kernel: [    0.227996] pci 0000:00:12.0: reg 1c: [io  0xfc00-0xfc03]
Dec  1 17:46:32 duper kernel: [    0.228007] pci 0000:00:12.0: reg 20: [io  0xfb00-0xfb0f]
Dec  1 17:46:32 duper kernel: [    0.228030] pci 0000:00:12.0: reg 24: [mem 0xfe02f000-0xfe02f3ff]
Dec  1 17:46:32 duper kernel: [    0.228053] pci 0000:00:12.0: set SATA to AHCI mode
Dec  1 17:46:32 duper kernel: [    0.228094] pci 0000:00:13.0: [1002:4387] type 0 class 0x000c03
Dec  1 17:46:32 duper kernel: [    0.228109] pci 0000:00:13.0: reg 10: [mem 0xfe02e000-0xfe02efff]
Dec  1 17:46:32 duper kernel: [    0.228186] pci 0000:00:13.1: [1002:4388] type 0 class 0x000c03
Dec  1 17:46:32 duper kernel: [    0.228201] pci 0000:00:13.1: reg 10: [mem 0xfe02d000-0xfe02dfff]
Dec  1 17:46:32 duper kernel: [    0.228273] pci 0000:00:13.2: [1002:4389] type 0 class 0x000c03
Dec  1 17:46:32 duper kernel: [    0.228288] pci 0000:00:13.2: reg 10: [mem 0xfe02c000-0xfe02cfff]
Dec  1 17:46:32 duper kernel: [    0.228360] pci 0000:00:13.3: [1002:438a] type 0 class 0x000c03
Dec  1 17:46:32 duper kernel: [    0.228375] pci 0000:00:13.3: reg 10: [mem 0xfe02b000-0xfe02bfff]
Dec  1 17:46:32 duper kernel: [    0.228447] pci 0000:00:13.4: [1002:438b] type 0 class 0x000c03
Dec  1 17:46:32 duper kernel: [    0.228462] pci 0000:00:13.4: reg 10: [mem 0xfe02a000-0xfe02afff]
Dec  1 17:46:32 duper kernel: [    0.228540] pci 0000:00:13.5: [1002:4386] type 0 class 0x000c03
Dec  1 17:46:32 duper kernel: [    0.228561] pci 0000:00:13.5: reg 10: [mem 0xfe029000-0xfe0290ff]
Dec  1 17:46:32 duper kernel: [    0.228650] pci 0000:00:13.5: supports D1 D2
Dec  1 17:46:32 duper kernel: [    0.228653] pci 0000:00:13.5: PME# supported from D0 D1 D2 D3hot
Dec  1 17:46:32 duper kernel: [    0.228658] pci 0000:00:13.5: PME# disabled
Dec  1 17:46:32 duper kernel: [    0.228683] pci 0000:00:14.0: [1002:4385] type 0 class 0x000c05
Dec  1 17:46:32 duper kernel: [    0.228706] pci 0000:00:14.0: reg 10: [io  0x0b00-0x0b0f]
Dec  1 17:46:32 duper kernel: [    0.228798] pci 0000:00:14.1: [1002:438c] type 0 class 0x000101
Dec  1 17:46:32 duper kernel: [    0.228812] pci 0000:00:14.1: reg 10: [io  0x0000-0x0007]
Dec  1 17:46:32 duper kernel: [    0.228823] pci 0000:00:14.1: reg 14: [io  0x0000-0x0003]
Dec  1 17:46:32 duper kernel: [    0.228834] pci 0000:00:14.1: reg 18: [io  0x0000-0x0007]
Dec  1 17:46:32 duper kernel: [    0.228845] pci 0000:00:14.1: reg 1c: [io  0x0000-0x0003]
Dec  1 17:46:32 duper kernel: [    0.228856] pci 0000:00:14.1: reg 20: [io  0xf900-0xf90f]
Dec  1 17:46:32 duper kernel: [    0.228899] pci 0000:00:14.2: [1002:4383] type 0 class 0x000403
Dec  1 17:46:32 duper kernel: [    0.228923] pci 0000:00:14.2: reg 10: [mem 0xfe024000-0xfe027fff 64bit]
Dec  1 17:46:32 duper kernel: [    0.228995] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
Dec  1 17:46:32 duper kernel: [    0.229000] pci 0000:00:14.2: PME# disabled
Dec  1 17:46:32 duper kernel: [    0.229018] pci 0000:00:14.3: [1002:438d] type 0 class 0x000601
Dec  1 17:46:32 duper kernel: [    0.229099] pci 0000:00:14.4: [1002:4384] type 1 class 0x000604
Dec  1 17:46:32 duper kernel: [    0.229152] pci 0000:00:18.0: [1022:1100] type 0 class 0x000600
Dec  1 17:46:32 duper kernel: [    0.229175] pci 0000:00:18.1: [1022:1101] type 0 class 0x000600
Dec  1 17:46:32 duper kernel: [    0.229192] pci 0000:00:18.2: [1022:1102] type 0 class 0x000600
Dec  1 17:46:32 duper kernel: [    0.229209] pci 0000:00:18.3: [1022:1103] type 0 class 0x000600
Dec  1 17:46:32 duper kernel: [    0.229238] PCI: peer root bus 00 res updated from pci conf
Dec  1 17:46:32 duper kernel: [    0.229263] pci 0000:01:05.0: [1002:791e] type 0 class 0x000300
Dec  1 17:46:32 duper kernel: [    0.229274] pci 0000:01:05.0: reg 10: [mem 0xd8000000-0xdfffffff 64bit pref]
Dec  1 17:46:32 duper kernel: [    0.229281] pci 0000:01:05.0: reg 18: [mem 0xfdfe0000-0xfdfeffff 64bit]
Dec  1 17:46:32 duper kernel: [    0.229286] pci 0000:01:05.0: reg 20: [io  0xee00-0xeeff]
Dec  1 17:46:32 duper kernel: [    0.229291] pci 0000:01:05.0: reg 24: [mem 0xfde00000-0xfdefffff]
Dec  1 17:46:32 duper kernel: [    0.229309] pci 0000:01:05.0: supports D1 D2
Dec  1 17:46:32 duper kernel: [    0.229321] pci 0000:01:05.2: [1002:7919] type 0 class 0x000403
Dec  1 17:46:32 duper kernel: [    0.229331] pci 0000:01:05.2: reg 10: [mem 0xfdffc000-0xfdffffff 64bit]
Dec  1 17:46:32 duper kernel: [    0.229374] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Dec  1 17:46:32 duper kernel: [    0.229378] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
Dec  1 17:46:32 duper kernel: [    0.229381] pci 0000:00:01.0:   bridge window [mem 0xfde00000-0xfdffffff]
Dec  1 17:46:32 duper kernel: [    0.229386] pci 0000:00:01.0:   bridge window [mem 0xd8000000-0xdfffffff 64bit pref]
Dec  1 17:46:32 duper kernel: [    0.229428] pci 0000:02:07.0: [1106:3038] type 0 class 0x000c03
Dec  1 17:46:32 duper kernel: [    0.229494] pci 0000:02:07.0: reg 20: [io  0xdf00-0xdf1f]
Dec  1 17:46:32 duper kernel: [    0.229552] pci 0000:02:07.0: supports D1 D2
Dec  1 17:46:32 duper kernel: [    0.229554] pci 0000:02:07.0: PME# supported from D0 D1 D2 D3hot D3cold
Dec  1 17:46:32 duper kernel: [    0.229560] pci 0000:02:07.0: PME# disabled
Dec  1 17:46:32 duper kernel: [    0.229582] pci 0000:02:07.1: [1106:3038] type 0 class 0x000c03
Dec  1 17:46:32 duper kernel: [    0.229648] pci 0000:02:07.1: reg 20: [io  0xde00-0xde1f]
Dec  1 17:46:32 duper kernel: [    0.229706] pci 0000:02:07.1: supports D1 D2
Dec  1 17:46:32 duper kernel: [    0.229709] pci 0000:02:07.1: PME# supported from D0 D1 D2 D3hot D3cold
Dec  1 17:46:32 duper kernel: [    0.229714] pci 0000:02:07.1: PME# disabled
Dec  1 17:46:32 duper kernel: [    0.229736] pci 0000:02:07.2: [1106:3104] type 0 class 0x000c03
Dec  1 17:46:32 duper kernel: [    0.229759] pci 0000:02:07.2: reg 10: [mem 0xfddff000-0xfddff0ff]
Dec  1 17:46:32 duper kernel: [    0.229861] pci 0000:02:07.2: supports D1 D2
Dec  1 17:46:32 duper kernel: [    0.229863] pci 0000:02:07.2: PME# supported from D0 D1 D2 D3hot D3cold
Dec  1 17:46:32 duper kernel: [    0.229868] pci 0000:02:07.2: PME# disabled
Dec  1 17:46:32 duper kernel: [    0.229910] pci 0000:02:0e.0: [104c:8024] type 0 class 0x000c00
Dec  1 17:46:32 duper kernel: [    0.229934] pci 0000:02:0e.0: reg 10: [mem 0xfddfe000-0xfddfe7ff]
Dec  1 17:46:32 duper kernel: [    0.229948] pci 0000:02:0e.0: reg 14: [mem 0xfddf8000-0xfddfbfff]
Dec  1 17:46:32 duper kernel: [    0.230046] pci 0000:02:0e.0: supports D1 D2
Dec  1 17:46:32 duper kernel: [    0.230048] pci 0000:02:0e.0: PME# supported from D0 D1 D2 D3hot
Dec  1 17:46:32 duper kernel: [    0.230054] pci 0000:02:0e.0: PME# disabled
Dec  1 17:46:32 duper kernel: [    0.230077] pci 0000:02:0f.0: [10ec:8167] type 0 class 0x000200
Dec  1 17:46:32 duper kernel: [    0.230100] pci 0000:02:0f.0: reg 10: [io  0xdc00-0xdcff]
Dec  1 17:46:32 duper kernel: [    0.230113] pci 0000:02:0f.0: reg 14: [mem 0xfddfd000-0xfddfd0ff]
Dec  1 17:46:32 duper kernel: [    0.230169] pci 0000:02:0f.0: reg 30: [mem 0x00000000-0x0001ffff pref]
Dec  1 17:46:32 duper kernel: [    0.230206] pci 0000:02:0f.0: supports D1 D2
Dec  1 17:46:32 duper kernel: [    0.230209] pci 0000:02:0f.0: PME# supported from D1 D2 D3hot D3cold
Dec  1 17:46:32 duper kernel: [    0.230214] pci 0000:02:0f.0: PME# disabled
Dec  1 17:46:32 duper kernel: [    0.230249] pci 0000:00:14.4: PCI bridge to [bus 02-02] (subtractive decode)
Dec  1 17:46:32 duper kernel: [    0.230254] pci 0000:00:14.4:   bridge window [io  0xd000-0xdfff]
Dec  1 17:46:32 duper kernel: [    0.230259] pci 0000:00:14.4:   bridge window [mem 0xfdd00000-0xfddfffff]
Dec  1 17:46:32 duper kernel: [    0.230264] pci 0000:00:14.4:   bridge window [mem 0xfdc00000-0xfdcfffff pref]
Dec  1 17:46:32 duper kernel: [    0.230268] pci 0000:00:14.4:   bridge window [io  0x0000-0xffff] (subtractive decode)
Dec  1 17:46:32 duper kernel: [    0.230271] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
Dec  1 17:46:32 duper kernel: [    0.230274] pci 0000:00:14.4:   bridge window [mem 0xd8000000-0xffffffff] (subtractive decode)
Dec  1 17:46:32 duper kernel: [    0.230277] pci 0000:00:14.4:   bridge window [mem 0x128000000-0xfcffffffff] (subtractive decode)
Dec  1 17:46:32 duper kernel: [    0.230290] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Dec  1 17:46:32 duper kernel: [    0.230510] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
Dec  1 17:46:32 duper kernel: [    0.230618] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
Dec  1 17:46:32 duper kernel: [    0.230662]  pci0000:00: Requesting ACPI _OSC control (0x1d)
Dec  1 17:46:32 duper kernel: [    0.230666]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
Dec  1 17:46:32 duper kernel: [    0.230669] ACPI _OSC control for PCIe not granted, disabling ASPM
Dec  1 17:46:32 duper kernel: [    0.245484] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Dec  1 17:46:32 duper kernel: [    0.245544] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Dec  1 17:46:32 duper kernel: [    0.245604] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Dec  1 17:46:32 duper kernel: [    0.245666] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Dec  1 17:46:32 duper kernel: [    0.245726] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Dec  1 17:46:32 duper kernel: [    0.245785] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Dec  1 17:46:32 duper kernel: [    0.245843] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Dec  1 17:46:32 duper kernel: [    0.245902] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Dec  1 17:46:32 duper kernel: [    0.246078] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
Dec  1 17:46:32 duper kernel: [    0.246085] vgaarb: loaded
Dec  1 17:46:32 duper kernel: [    0.246087] vgaarb: bridge control possible 0000:01:05.0
Dec  1 17:46:32 duper kernel: [    0.246243] i2c-core: driver [aat2870] using legacy suspend method
Dec  1 17:46:32 duper kernel: [    0.246245] i2c-core: driver [aat2870] using legacy resume method
Dec  1 17:46:32 duper kernel: [    0.246356] SCSI subsystem initialized
Dec  1 17:46:32 duper kernel: [    0.246443] libata version 3.00 loaded.
Dec  1 17:46:32 duper kernel: [    0.246523] usbcore: registered new interface driver usbfs
Dec  1 17:46:32 duper kernel: [    0.246540] usbcore: registered new interface driver hub
Dec  1 17:46:32 duper kernel: [    0.246576] usbcore: registered new device driver usb
Dec  1 17:46:32 duper kernel: [    0.246705] PCI: Using ACPI for IRQ routing
Dec  1 17:46:32 duper kernel: [    0.256052] PCI: pci_cache_line_size set to 64 bytes
Dec  1 17:46:32 duper kernel: [    0.256170] reserve RAM buffer: 000000000009f800 - 000000000009ffff
Dec  1 17:46:32 duper kernel: [    0.256173] reserve RAM buffer: 00000000cfee0000 - 00000000cfffffff
Dec  1 17:46:32 duper kernel: [    0.256311] NetLabel: Initializing
Dec  1 17:46:32 duper kernel: [    0.256313] NetLabel:  domain hash size = 128
Dec  1 17:46:32 duper kernel: [    0.256315] NetLabel:  protocols = UNLABELED CIPSOv4
Dec  1 17:46:32 duper kernel: [    0.256332] NetLabel:  unlabeled traffic allowed by default
Dec  1 17:46:32 duper kernel: [    0.256402] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
Dec  1 17:46:32 duper kernel: [    0.256408] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
Dec  1 17:46:32 duper kernel: [    0.258474] Switching to clocksource hpet
Dec  1 17:46:32 duper kernel: [    0.267160] AppArmor: AppArmor Filesystem Enabled
Dec  1 17:46:32 duper kernel: [    0.267203] pnp: PnP ACPI init
Dec  1 17:46:32 duper kernel: [    0.267228] ACPI: bus type pnp registered
Dec  1 17:46:32 duper kernel: [    0.267389] pnp 00:00: [bus 00-ff]
Dec  1 17:46:32 duper kernel: [    0.267392] pnp 00:00: [io  0x0cf8-0x0cff]
Dec  1 17:46:32 duper kernel: [    0.267395] pnp 00:00: [io  0x0000-0x0cf7 window]
Dec  1 17:46:32 duper kernel: [    0.267398] pnp 00:00: [io  0x0d00-0xffff window]
Dec  1 17:46:32 duper kernel: [    0.267404] pnp 00:00: [mem 0x000a0000-0x000bffff window]
Dec  1 17:46:32 duper kernel: [    0.267407] pnp 00:00: [mem 0x000c0000-0x000dffff window]
Dec  1 17:46:32 duper kernel: [    0.267410] pnp 00:00: [mem 0xd8000000-0xfebfffff window]
Dec  1 17:46:32 duper kernel: [    0.267486] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
Dec  1 17:46:32 duper kernel: [    0.267696] pnp 00:01: [io  0x4100-0x411f]
Dec  1 17:46:32 duper kernel: [    0.267699] pnp 00:01: [io  0x0228-0x022f]
Dec  1 17:46:32 duper kernel: [    0.267701] pnp 00:01: [io  0x040b]
Dec  1 17:46:32 duper kernel: [    0.267704] pnp 00:01: [io  0x04d6]
Dec  1 17:46:32 duper kernel: [    0.267706] pnp 00:01: [io  0x0c00-0x0c01]
Dec  1 17:46:32 duper kernel: [    0.267708] pnp 00:01: [io  0x0c14]
Dec  1 17:46:32 duper kernel: [    0.267711] pnp 00:01: [io  0x0c50-0x0c52]
Dec  1 17:46:32 duper kernel: [    0.267713] pnp 00:01: [io  0x0c6c-0x0c6d]
Dec  1 17:46:32 duper kernel: [    0.267715] pnp 00:01: [io  0x0c6f]
Dec  1 17:46:32 duper kernel: [    0.267718] pnp 00:01: [io  0x0cd0-0x0cd1]
Dec  1 17:46:32 duper kernel: [    0.267720] pnp 00:01: [io  0x0cd2-0x0cd3]
Dec  1 17:46:32 duper kernel: [    0.267723] pnp 00:01: [io  0x0cd4-0x0cdf]
Dec  1 17:46:32 duper kernel: [    0.267725] pnp 00:01: [io  0x4000-0x40fe]
Dec  1 17:46:32 duper kernel: [    0.267728] pnp 00:01: [io  0x4210-0x4217]
Dec  1 17:46:32 duper kernel: [    0.267730] pnp 00:01: [io  0x0b10-0x0b1f]
Dec  1 17:46:32 duper kernel: [    0.267732] pnp 00:01: [io  0x0b00-0x0b0f]
Dec  1 17:46:32 duper kernel: [    0.267735] pnp 00:01: [io  0x0070-0x0073]
Dec  1 17:46:32 duper kernel: [    0.267737] pnp 00:01: [io  0x0238-0x023f]
Dec  1 17:46:32 duper kernel: [    0.267740] pnp 00:01: [mem 0x00000000-0x00000fff window]
Dec  1 17:46:32 duper kernel: [    0.267743] pnp 00:01: [mem 0xfee00400-0xfee00fff window]
Dec  1 17:46:32 duper kernel: [    0.267803] pnp 00:01: disabling [mem 0x00000000-0x00000fff window] because it overlaps 0000:02:0f.0 BAR 6 [mem 0x00000000-0x0001ffff pref]
Dec  1 17:46:32 duper kernel: [    0.267855] system 00:01: [io  0x4100-0x411f] has been reserved
Dec  1 17:46:32 duper kernel: [    0.267859] system 00:01: [io  0x0228-0x022f] has been reserved
Dec  1 17:46:32 duper kernel: [    0.267862] system 00:01: [io  0x040b] has been reserved
Dec  1 17:46:32 duper kernel: [    0.267865] system 00:01: [io  0x04d6] has been reserved
Dec  1 17:46:32 duper kernel: [    0.267868] system 00:01: [io  0x0c00-0x0c01] has been reserved
Dec  1 17:46:32 duper kernel: [    0.267871] system 00:01: [io  0x0c14] has been reserved
Dec  1 17:46:32 duper kernel: [    0.267877] system 00:01: [io  0x0c50-0x0c52] has been reserved
Dec  1 17:46:32 duper kernel: [    0.267881] system 00:01: [io  0x0c6c-0x0c6d] has been reserved
Dec  1 17:46:32 duper kernel: [    0.267884] system 00:01: [io  0x0c6f] has been reserved
Dec  1 17:46:32 duper kernel: [    0.267887] system 00:01: [io  0x0cd0-0x0cd1] has been reserved
Dec  1 17:46:32 duper kernel: [    0.267891] system 00:01: [io  0x0cd2-0x0cd3] has been reserved
Dec  1 17:46:32 duper kernel: [    0.267894] system 00:01: [io  0x0cd4-0x0cdf] has been reserved
Dec  1 17:46:32 duper kernel: [    0.267897] system 00:01: [io  0x4000-0x40fe] has been reserved
Dec  1 17:46:32 duper kernel: [    0.267900] system 00:01: [io  0x4210-0x4217] has been reserved
Dec  1 17:46:32 duper kernel: [    0.267904] system 00:01: [io  0x0b10-0x0b1f] has been reserved
Dec  1 17:46:32 duper kernel: [    0.267907] system 00:01: [io  0x0b00-0x0b0f] has been reserved
Dec  1 17:46:32 duper kernel: [    0.267911] system 00:01: [io  0x0238-0x023f] has been reserved
Dec  1 17:46:32 duper kernel: [    0.267915] system 00:01: [mem 0xfee00400-0xfee00fff window] has been reserved
Dec  1 17:46:32 duper kernel: [    0.267920] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
Dec  1 17:46:32 duper kernel: [    0.268103] pnp 00:02: [dma 4]
Dec  1 17:46:32 duper kernel: [    0.268106] pnp 00:02: [io  0x0000-0x000f]
Dec  1 17:46:32 duper kernel: [    0.268109] pnp 00:02: [io  0x0080-0x0090]
Dec  1 17:46:32 duper kernel: [    0.268111] pnp 00:02: [io  0x0094-0x009f]
Dec  1 17:46:32 duper kernel: [    0.268113] pnp 00:02: [io  0x00c0-0x00df]
Dec  1 17:46:32 duper kernel: [    0.268152] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
Dec  1 17:46:32 duper kernel: [    0.268199] pnp 00:03: [irq 0 disabled]
Dec  1 17:46:32 duper kernel: [    0.268216] pnp 00:03: [irq 8]
Dec  1 17:46:32 duper kernel: [    0.268219] pnp 00:03: [mem 0xfed00000-0xfed003ff]
Dec  1 17:46:32 duper kernel: [    0.268261] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
Dec  1 17:46:32 duper kernel: [    0.268300] pnp 00:04: [io  0x0070-0x0073]
Dec  1 17:46:32 duper kernel: [    0.268341] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
Dec  1 17:46:32 duper kernel: [    0.268353] pnp 00:05: [io  0x0061]
Dec  1 17:46:32 duper kernel: [    0.268391] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
Dec  1 17:46:32 duper kernel: [    0.268403] pnp 00:06: [io  0x00f0-0x00ff]
Dec  1 17:46:32 duper kernel: [    0.268414] pnp 00:06: [irq 13]
Dec  1 17:46:32 duper kernel: [    0.268455] pnp 00:06: Plug and Play ACPI device, IDs PNP0c04 (active)
Dec  1 17:46:32 duper kernel: [    0.268500] pnp 00:07: [io  0x0010-0x001f]
Dec  1 17:46:32 duper kernel: [    0.268502] pnp 00:07: [io  0x0022-0x003f]
Dec  1 17:46:32 duper kernel: [    0.268505] pnp 00:07: [io  0x0044-0x005f]
Dec  1 17:46:32 duper kernel: [    0.268507] pnp 00:07: [io  0x0062-0x0063]
Dec  1 17:46:32 duper kernel: [    0.268510] pnp 00:07: [io  0x0065-0x006f]
Dec  1 17:46:32 duper kernel: [    0.268512] pnp 00:07: [io  0x0074-0x007f]
Dec  1 17:46:32 duper kernel: [    0.268514] pnp 00:07: [io  0x0091-0x0093]
Dec  1 17:46:32 duper kernel: [    0.268520] pnp 00:07: [io  0x00a2-0x00bf]
Dec  1 17:46:32 duper kernel: [    0.268522] pnp 00:07: [io  0x00e0-0x00ef]
Dec  1 17:46:32 duper kernel: [    0.268525] pnp 00:07: [io  0x04d0-0x04d1]
Dec  1 17:46:32 duper kernel: [    0.268527] pnp 00:07: [io  0x0220-0x0225]
Dec  1 17:46:32 duper kernel: [    0.268529] pnp 00:07: [io  0x0290-0x0294]
Dec  1 17:46:32 duper kernel: [    0.268609] system 00:07: [io  0x04d0-0x04d1] has been reserved
Dec  1 17:46:32 duper kernel: [    0.268612] system 00:07: [io  0x0220-0x0225] has been reserved
Dec  1 17:46:32 duper kernel: [    0.268615] system 00:07: [io  0x0290-0x0294] has been reserved
Dec  1 17:46:32 duper kernel: [    0.268619] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
Dec  1 17:46:32 duper kernel: [    0.269058] pnp 00:08: [io  0x02f8-0x02ff]
Dec  1 17:46:32 duper kernel: [    0.269068] pnp 00:08: [irq 3]
Dec  1 17:46:32 duper kernel: [    0.269144] pnp 00:08: Plug and Play ACPI device, IDs PNP0501 (active)
Dec  1 17:46:32 duper kernel: [    0.269411] pnp 00:09: [io  0x0378-0x037f]
Dec  1 17:46:32 duper kernel: [    0.269422] pnp 00:09: [irq 7]
Dec  1 17:46:32 duper kernel: [    0.269487] pnp 00:09: Plug and Play ACPI device, IDs PNP0400 (active)
Dec  1 17:46:32 duper kernel: [    0.269654] pnp 00:0a: [mem 0xe0000000-0xefffffff]
Dec  1 17:46:32 duper kernel: [    0.269730] system 00:0a: [mem 0xe0000000-0xefffffff] has been reserved
Dec  1 17:46:32 duper kernel: [    0.269734] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
Dec  1 17:46:32 duper kernel: [    0.269977] pnp 00:0b: [mem 0x000cd600-0x000cffff]
Dec  1 17:46:32 duper kernel: [    0.269980] pnp 00:0b: [mem 0x000f0000-0x000f7fff]
Dec  1 17:46:32 duper kernel: [    0.269983] pnp 00:0b: [mem 0x000f8000-0x000fbfff]
Dec  1 17:46:32 duper kernel: [    0.269986] pnp 00:0b: [mem 0x000fc000-0x000fffff]
Dec  1 17:46:32 duper kernel: [    0.269988] pnp 00:0b: [mem 0xcfee0000-0xcfefffff]
Dec  1 17:46:32 duper kernel: [    0.269991] pnp 00:0b: [mem 0xffff0000-0xffffffff]
Dec  1 17:46:32 duper kernel: [    0.269993] pnp 00:0b: [mem 0x00000000-0x0009ffff]
Dec  1 17:46:32 duper kernel: [    0.269996] pnp 00:0b: [mem 0x00100000-0xcfedffff]
Dec  1 17:46:32 duper kernel: [    0.269999] pnp 00:0b: [mem 0xcfff0000-0xd7feffff]
Dec  1 17:46:32 duper kernel: [    0.270001] pnp 00:0b: [mem 0xfec00000-0xfec00fff]
Dec  1 17:46:32 duper kernel: [    0.270004] pnp 00:0b: [mem 0xfee00000-0xfee00fff]
Dec  1 17:46:32 duper kernel: [    0.270006] pnp 00:0b: [mem 0xfff80000-0xfffeffff]
Dec  1 17:46:32 duper kernel: [    0.270092] system 00:0b: [mem 0x000cd600-0x000cffff] has been reserved
Dec  1 17:46:32 duper kernel: [    0.270096] system 00:0b: [mem 0x000f0000-0x000f7fff] could not be reserved
Dec  1 17:46:32 duper kernel: [    0.270100] system 00:0b: [mem 0x000f8000-0x000fbfff] could not be reserved
Dec  1 17:46:32 duper kernel: [    0.270103] system 00:0b: [mem 0x000fc000-0x000fffff] could not be reserved
Dec  1 17:46:32 duper kernel: [    0.270107] system 00:0b: [mem 0xcfee0000-0xcfefffff] could not be reserved
Dec  1 17:46:32 duper kernel: [    0.270111] system 00:0b: [mem 0xffff0000-0xffffffff] has been reserved
Dec  1 17:46:32 duper kernel: [    0.270114] system 00:0b: [mem 0x00000000-0x0009ffff] could not be reserved
Dec  1 17:46:32 duper kernel: [    0.270118] system 00:0b: [mem 0x00100000-0xcfedffff] could not be reserved
Dec  1 17:46:32 duper kernel: [    0.270122] system 00:0b: [mem 0xcfff0000-0xd7feffff] could not be reserved
Dec  1 17:46:32 duper kernel: [    0.270126] system 00:0b: [mem 0xfec00000-0xfec00fff] could not be reserved
Dec  1 17:46:32 duper kernel: [    0.270130] system 00:0b: [mem 0xfee00000-0xfee00fff] could not be reserved
Dec  1 17:46:32 duper kernel: [    0.270134] system 00:0b: [mem 0xfff80000-0xfffeffff] has been reserved
Dec  1 17:46:32 duper kernel: [    0.270138] system 00:0b: Plug and Play ACPI device, IDs PNP0c01 (active)
Dec  1 17:46:32 duper kernel: [    0.270162] pnp: PnP ACPI: found 12 devices
Dec  1 17:46:32 duper kernel: [    0.270164] ACPI: ACPI bus type pnp unregistered
Dec  1 17:46:32 duper kernel: [    0.277062] PCI: max bus depth: 1 pci_try_num: 2
Dec  1 17:46:32 duper kernel: [    0.277084] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Dec  1 17:46:32 duper kernel: [    0.277088] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
Dec  1 17:46:32 duper kernel: [    0.277092] pci 0000:00:01.0:   bridge window [mem 0xfde00000-0xfdffffff]
Dec  1 17:46:32 duper kernel: [    0.277095] pci 0000:00:01.0:   bridge window [mem 0xd8000000-0xdfffffff 64bit pref]
Dec  1 17:46:32 duper kernel: [    0.277106] pci 0000:02:0f.0: BAR 6: assigned [mem 0xfdc00000-0xfdc1ffff pref]
Dec  1 17:46:32 duper kernel: [    0.277109] pci 0000:00:14.4: PCI bridge to [bus 02-02]
Dec  1 17:46:32 duper kernel: [    0.277113] pci 0000:00:14.4:   bridge window [io  0xd000-0xdfff]
Dec  1 17:46:32 duper kernel: [    0.277119] pci 0000:00:14.4:   bridge window [mem 0xfdd00000-0xfddfffff]
Dec  1 17:46:32 duper kernel: [    0.277124] pci 0000:00:14.4:   bridge window [mem 0xfdc00000-0xfdcfffff pref]
Dec  1 17:46:32 duper kernel: [    0.277144] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
Dec  1 17:46:32 duper kernel: [    0.277146] pci_bus 0000:00: resource 5 [mem 0x000a0000-0x000bffff]
Dec  1 17:46:32 duper kernel: [    0.277149] pci_bus 0000:00: resource 6 [mem 0xd8000000-0xffffffff]
Dec  1 17:46:32 duper kernel: [    0.277152] pci_bus 0000:00: resource 7 [mem 0x128000000-0xfcffffffff]
Dec  1 17:46:32 duper kernel: [    0.277155] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
Dec  1 17:46:32 duper kernel: [    0.277158] pci_bus 0000:01: resource 1 [mem 0xfde00000-0xfdffffff]
Dec  1 17:46:32 duper kernel: [    0.277161] pci_bus 0000:01: resource 2 [mem 0xd8000000-0xdfffffff 64bit pref]
Dec  1 17:46:32 duper kernel: [    0.277164] pci_bus 0000:02: resource 0 [io  0xd000-0xdfff]
Dec  1 17:46:32 duper kernel: [    0.277167] pci_bus 0000:02: resource 1 [mem 0xfdd00000-0xfddfffff]
Dec  1 17:46:32 duper kernel: [    0.277170] pci_bus 0000:02: resource 2 [mem 0xfdc00000-0xfdcfffff pref]
Dec  1 17:46:32 duper kernel: [    0.277173] pci_bus 0000:02: resource 4 [io  0x0000-0xffff]
Dec  1 17:46:32 duper kernel: [    0.277176] pci_bus 0000:02: resource 5 [mem 0x000a0000-0x000bffff]
Dec  1 17:46:32 duper kernel: [    0.277178] pci_bus 0000:02: resource 6 [mem 0xd8000000-0xffffffff]
Dec  1 17:46:32 duper kernel: [    0.277181] pci_bus 0000:02: resource 7 [mem 0x128000000-0xfcffffffff]
Dec  1 17:46:32 duper kernel: [    0.277237] NET: Registered protocol family 2
Dec  1 17:46:32 duper kernel: [    0.277421] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
Dec  1 17:46:32 duper kernel: [    0.279182] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
Dec  1 17:46:32 duper kernel: [    0.283855] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Dec  1 17:46:32 duper kernel: [    0.284430] TCP: Hash tables configured (established 524288 bind 65536)
Dec  1 17:46:32 duper kernel: [    0.284433] TCP reno registered
Dec  1 17:46:32 duper kernel: [    0.284449] UDP hash table entries: 2048 (order: 4, 65536 bytes)
Dec  1 17:46:32 duper kernel: [    0.284501] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
Dec  1 17:46:32 duper kernel: [    0.284649] NET: Registered protocol family 1
Dec  1 17:46:32 duper kernel: [    0.284704] pci 0000:00:13.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec  1 17:46:32 duper kernel: [    0.368035] pci 0000:00:13.0: PCI INT A disabled
Dec  1 17:46:32 duper kernel: [    0.368055] pci 0000:00:13.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Dec  1 17:46:32 duper kernel: [    0.452033] pci 0000:00:13.1: PCI INT B disabled
Dec  1 17:46:32 duper kernel: [    0.452052] pci 0000:00:13.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Dec  1 17:46:32 duper kernel: [    0.536031] pci 0000:00:13.2: PCI INT C disabled
Dec  1 17:46:32 duper kernel: [    0.536041] pci 0000:00:13.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Dec  1 17:46:32 duper kernel: [    0.615079] Freeing initrd memory: 16900k freed
Dec  1 17:46:32 duper kernel: [    0.620029] pci 0000:00:13.3: PCI INT B disabled
Dec  1 17:46:32 duper kernel: [    0.620039] pci 0000:00:13.4: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Dec  1 17:46:32 duper kernel: [    0.704026] pci 0000:00:13.4: PCI INT C disabled
Dec  1 17:46:32 duper kernel: [    0.704046] pci 0000:00:13.5: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Dec  1 17:46:32 duper kernel: [    0.704070] pci 0000:00:13.5: PCI INT D disabled
Dec  1 17:46:32 duper kernel: [    0.704103] pci 0000:01:05.0: Boot video device
Dec  1 17:46:32 duper kernel: [    0.704123] pci 0000:02:07.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Dec  1 17:46:32 duper kernel: [    0.704145] pci 0000:02:07.0: PCI INT A disabled
Dec  1 17:46:32 duper kernel: [    0.704164] pci 0000:02:07.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22
Dec  1 17:46:32 duper kernel: [    0.704185] pci 0000:02:07.1: PCI INT B disabled
Dec  1 17:46:32 duper kernel: [    0.704203] pci 0000:02:07.2: PCI INT C -> GSI 23 (level, low) -> IRQ 23
Dec  1 17:46:32 duper kernel: [    0.704229] pci 0000:02:07.2: PCI INT C disabled
Dec  1 17:46:32 duper kernel: [    0.704241] PCI: CLS 4 bytes, default 64
Dec  1 17:46:32 duper kernel: [    0.705032] PCI-DMA: Disabling AGP.
Dec  1 17:46:32 duper kernel: [    0.705137] PCI-DMA: aperture base @ c4000000 size 65536 KB
Dec  1 17:46:32 duper kernel: [    0.705139] PCI-DMA: using GART IOMMU.
Dec  1 17:46:32 duper kernel: [    0.705144] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
Dec  1 17:46:32 duper kernel: [    0.709323] audit: initializing netlink socket (disabled)
Dec  1 17:46:32 duper kernel: [    0.709340] type=2000 audit(1354344375.704:1): initialized
Dec  1 17:46:32 duper kernel: [    0.736372] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Dec  1 17:46:32 duper kernel: [    0.739507] VFS: Disk quotas dquot_6.5.2
Dec  1 17:46:32 duper kernel: [    0.739585] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Dec  1 17:46:32 duper kernel: [    0.740346] fuse init (API version 7.17)
Dec  1 17:46:32 duper kernel: [    0.740487] msgmni has been set to 7649
Dec  1 17:46:32 duper kernel: [    0.741053] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Dec  1 17:46:32 duper kernel: [    0.741107] io scheduler noop registered
Dec  1 17:46:32 duper kernel: [    0.741109] io scheduler deadline registered
Dec  1 17:46:32 duper kernel: [    0.741159] io scheduler cfq registered (default)
Dec  1 17:46:32 duper kernel: [    0.741366] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Dec  1 17:46:32 duper kernel: [    0.741396] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Dec  1 17:46:32 duper kernel: [    0.741575] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
Dec  1 17:46:32 duper kernel: [    0.741582] ACPI: Power Button [PWRB]
Dec  1 17:46:32 duper kernel: [    0.741647] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Dec  1 17:46:32 duper kernel: [    0.741651] ACPI: Power Button [PWRF]
Dec  1 17:46:32 duper kernel: [    0.743267] ERST: Table is not found!
Dec  1 17:46:32 duper kernel: [    0.743269] GHES: HEST is not enabled!
Dec  1 17:46:32 duper kernel: [    0.743376] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Dec  1 17:46:32 duper kernel: [    0.780483] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Dec  1 17:46:32 duper kernel: [    0.888644] 00:08: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Dec  1 17:46:32 duper kernel: [    0.904392] Linux agpgart interface v0.103
Dec  1 17:46:32 duper kernel: [    0.906453] brd: module loaded
Dec  1 17:46:32 duper kernel: [    0.907593] loop: module loaded
Dec  1 17:46:32 duper kernel: [    0.907814] ahci 0000:00:12.0: version 3.0
Dec  1 17:46:32 duper kernel: [    0.907831] ahci 0000:00:12.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Dec  1 17:46:32 duper kernel: [    0.907880] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit
Dec  1 17:46:32 duper kernel: [    0.907983] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
Dec  1 17:46:32 duper kernel: [    0.907988] ahci 0000:00:12.0: flags: ncq sntf ilck pm led clo pmp pio slum part ccc
Dec  1 17:46:32 duper kernel: [    0.908928] scsi0 : ahci
Dec  1 17:46:32 duper kernel: [    0.909095] scsi1 : ahci
Dec  1 17:46:32 duper kernel: [    0.909186] scsi2 : ahci
Dec  1 17:46:32 duper kernel: [    0.909282] scsi3 : ahci
Dec  1 17:46:32 duper kernel: [    0.909448] ata1: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f100 irq 22
Dec  1 17:46:32 duper kernel: [    0.909453] ata2: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f180 irq 22
Dec  1 17:46:32 duper kernel: [    0.909457] ata3: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f200 irq 22
Dec  1 17:46:32 duper kernel: [    0.909461] ata4: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f280 irq 22
Dec  1 17:46:32 duper kernel: [    0.909672] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec  1 17:46:32 duper kernel: [    0.910245] Fixed MDIO Bus: probed
Dec  1 17:46:32 duper kernel: [    0.910273] tun: Universal TUN/TAP device driver, 1.6
Dec  1 17:46:32 duper kernel: [    0.910275] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Dec  1 17:46:32 duper kernel: [    0.910374] PPP generic driver version 2.4.2
Dec  1 17:46:32 duper kernel: [    0.910557] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Dec  1 17:46:32 duper kernel: [    0.910582] ehci_hcd 0000:00:13.5: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Dec  1 17:46:32 duper kernel: [    0.910609] ehci_hcd 0000:00:13.5: EHCI Host Controller
Dec  1 17:46:32 duper kernel: [    0.910667] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 1
Dec  1 17:46:32 duper kernel: [    0.910700] ehci_hcd 0000:00:13.5: applying AMD SB600/SB700 USB freeze workaround
Dec  1 17:46:32 duper kernel: [    0.910715] ehci_hcd 0000:00:13.5: debug port 1
Dec  1 17:46:32 duper kernel: [    0.910753] ehci_hcd 0000:00:13.5: irq 19, io mem 0xfe029000
Dec  1 17:46:32 duper kernel: [    0.920020] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00
Dec  1 17:46:32 duper kernel: [    0.920213] hub 1-0:1.0: USB hub found
Dec  1 17:46:32 duper kernel: [    0.920218] hub 1-0:1.0: 10 ports detected
Dec  1 17:46:32 duper kernel: [    0.920363] ehci_hcd 0000:02:07.2: PCI INT C -> GSI 23 (level, low) -> IRQ 23
Dec  1 17:46:32 duper kernel: [    0.920384] ehci_hcd 0000:02:07.2: EHCI Host Controller
Dec  1 17:46:32 duper kernel: [    0.920452] ehci_hcd 0000:02:07.2: new USB bus registered, assigned bus number 2
Dec  1 17:46:32 duper kernel: [    0.920511] ehci_hcd 0000:02:07.2: irq 23, io mem 0xfddff000
Dec  1 17:46:32 duper kernel: [    0.932023] ehci_hcd 0000:02:07.2: USB 2.0 started, EHCI 1.00
Dec  1 17:46:32 duper kernel: [    0.932173] hub 2-0:1.0: USB hub found
Dec  1 17:46:32 duper kernel: [    0.932178] hub 2-0:1.0: 4 ports detected
Dec  1 17:46:32 duper kernel: [    0.932284] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Dec  1 17:46:32 duper kernel: [    0.932315] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec  1 17:46:32 duper kernel: [    0.932330] ohci_hcd 0000:00:13.0: OHCI Host Controller
Dec  1 17:46:32 duper kernel: [    0.932392] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 3
Dec  1 17:46:32 duper kernel: [    0.932427] ohci_hcd 0000:00:13.0: irq 16, io mem 0xfe02e000
Dec  1 17:46:32 duper kernel: [    0.992152] hub 3-0:1.0: USB hub found
Dec  1 17:46:32 duper kernel: [    0.992160] hub 3-0:1.0: 2 ports detected
Dec  1 17:46:32 duper kernel: [    0.992264] ohci_hcd 0000:00:13.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Dec  1 17:46:32 duper kernel: [    0.992279] ohci_hcd 0000:00:13.1: OHCI Host Controller
Dec  1 17:46:32 duper kernel: [    0.992339] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 4
Dec  1 17:46:32 duper kernel: [    0.992372] ohci_hcd 0000:00:13.1: irq 17, io mem 0xfe02d000
Dec  1 17:46:32 duper kernel: [    1.052150] hub 4-0:1.0: USB hub found
Dec  1 17:46:32 duper kernel: [    1.052157] hub 4-0:1.0: 2 ports detected
Dec  1 17:46:32 duper kernel: [    1.052257] ohci_hcd 0000:00:13.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Dec  1 17:46:32 duper kernel: [    1.052271] ohci_hcd 0000:00:13.2: OHCI Host Controller
Dec  1 17:46:32 duper kernel: [    1.052334] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 5
Dec  1 17:46:32 duper kernel: [    1.052365] ohci_hcd 0000:00:13.2: irq 18, io mem 0xfe02c000
Dec  1 17:46:32 duper kernel: [    1.112154] hub 5-0:1.0: USB hub found
Dec  1 17:46:32 duper kernel: [    1.112161] hub 5-0:1.0: 2 ports detected
Dec  1 17:46:32 duper kernel: [    1.112261] ohci_hcd 0000:00:13.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Dec  1 17:46:32 duper kernel: [    1.112276] ohci_hcd 0000:00:13.3: OHCI Host Controller
Dec  1 17:46:32 duper kernel: [    1.112338] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 6
Dec  1 17:46:32 duper kernel: [    1.112355] ohci_hcd 0000:00:13.3: irq 17, io mem 0xfe02b000
Dec  1 17:46:32 duper kernel: [    1.172159] hub 6-0:1.0: USB hub found
Dec  1 17:46:32 duper kernel: [    1.172166] hub 6-0:1.0: 2 ports detected
Dec  1 17:46:32 duper kernel: [    1.172266] ohci_hcd 0000:00:13.4: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Dec  1 17:46:32 duper kernel: [    1.172289] ohci_hcd 0000:00:13.4: OHCI Host Controller
Dec  1 17:46:32 duper kernel: [    1.172352] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 7
Dec  1 17:46:32 duper kernel: [    1.172369] ohci_hcd 0000:00:13.4: irq 18, io mem 0xfe02a000
Dec  1 17:46:32 duper kernel: [    1.228058] ata2: SATA link down (SStatus 0 SControl 300)
Dec  1 17:46:32 duper kernel: [    1.228097] ata4: SATA link down (SStatus 0 SControl 300)
Dec  1 17:46:32 duper kernel: [    1.232189] hub 7-0:1.0: USB hub found
Dec  1 17:46:32 duper kernel: [    1.232196] hub 7-0:1.0: 2 ports detected
Dec  1 17:46:32 duper kernel: [    1.232296] uhci_hcd: USB Universal Host Controller Interface driver
Dec  1 17:46:32 duper kernel: [    1.232334] uhci_hcd 0000:02:07.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Dec  1 17:46:32 duper kernel: [    1.232346] uhci_hcd 0000:02:07.0: UHCI Host Controller
Dec  1 17:46:32 duper kernel: [    1.232415] uhci_hcd 0000:02:07.0: new USB bus registered, assigned bus number 8
Dec  1 17:46:32 duper kernel: [    1.232465] uhci_hcd 0000:02:07.0: irq 21, io base 0x0000df00
Dec  1 17:46:32 duper kernel: [    1.232633] hub 8-0:1.0: USB hub found
Dec  1 17:46:32 duper kernel: [    1.232637] hub 8-0:1.0: 2 ports detected
Dec  1 17:46:32 duper kernel: [    1.232739] uhci_hcd 0000:02:07.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22
Dec  1 17:46:32 duper kernel: [    1.232749] uhci_hcd 0000:02:07.1: UHCI Host Controller
Dec  1 17:46:32 duper kernel: [    1.232802] uhci_hcd 0000:02:07.1: new USB bus registered, assigned bus number 9
Dec  1 17:46:32 duper kernel: [    1.232833] uhci_hcd 0000:02:07.1: irq 22, io base 0x0000de00
Dec  1 17:46:32 duper kernel: [    1.232992] hub 9-0:1.0: USB hub found
Dec  1 17:46:32 duper kernel: [    1.232997] hub 9-0:1.0: 2 ports detected
Dec  1 17:46:32 duper kernel: [    1.233176] usbcore: registered new interface driver libusual
Dec  1 17:46:32 duper kernel: [    1.233234] i8042: PNP: No PS/2 controller found. Probing ports directly.
Dec  1 17:46:32 duper kernel: [    1.233656] serio: i8042 KBD port at 0x60,0x64 irq 1
Dec  1 17:46:32 duper kernel: [    1.233662] serio: i8042 AUX port at 0x60,0x64 irq 12
Dec  1 17:46:32 duper kernel: [    1.233816] mousedev: PS/2 mouse device common for all mice
Dec  1 17:46:32 duper kernel: [    1.233987] rtc_cmos 00:04: RTC can wake from S4
Dec  1 17:46:32 duper kernel: [    1.234116] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
Dec  1 17:46:32 duper kernel: [    1.234155] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
Dec  1 17:46:32 duper kernel: [    1.234268] device-mapper: uevent: version 1.0.3
Dec  1 17:46:32 duper kernel: [    1.234361] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
Dec  1 17:46:32 duper kernel: [    1.234371] cpuidle: using governor ladder
Dec  1 17:46:32 duper kernel: [    1.234373] cpuidle: using governor menu
Dec  1 17:46:32 duper kernel: [    1.234375] EFI Variables Facility v0.08 2004-May-17
Dec  1 17:46:32 duper kernel: [    1.234661] TCP cubic registered
Dec  1 17:46:32 duper kernel: [    1.234803] NET: Registered protocol family 10
Dec  1 17:46:32 duper kernel: [    1.235414] NET: Registered protocol family 17
Dec  1 17:46:32 duper kernel: [    1.235419] Registering the dns_resolver key type
Dec  1 17:46:32 duper kernel: [    1.235595] PM: Hibernation image not present or could not be loaded.
Dec  1 17:46:32 duper kernel: [    1.235610] registered taskstats version 1
Dec  1 17:46:32 duper kernel: [    1.245205]   Magic number: 8:979:770
Dec  1 17:46:32 duper kernel: [    1.245322] rtc_cmos 00:04: setting system clock to 2012-12-01 06:46:17 UTC (1354344377)
Dec  1 17:46:32 duper kernel: [    1.245331] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 4000+ (2 cpu cores) (version 2.20.00)
Dec  1 17:46:32 duper kernel: [    1.245375] powernow-k8: fid 0xd (2100 MHz), vid 0xc
Dec  1 17:46:32 duper kernel: [    1.245377] powernow-k8: fid 0xc (2000 MHz), vid 0xd
Dec  1 17:46:32 duper kernel: [    1.245380] powernow-k8: fid 0xa (1800 MHz), vid 0xf
Dec  1 17:46:32 duper kernel: [    1.245382] powernow-k8: fid 0x2 (1000 MHz), vid 0x12
Dec  1 17:46:32 duper kernel: [    1.245442] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Dec  1 17:46:32 duper kernel: [    1.245444] EDD information not available.
Dec  1 17:46:32 duper kernel: [    1.400029] ata3: softreset failed (device not ready)
Dec  1 17:46:32 duper kernel: [    1.400034] ata3: applying PMP SRST workaround and retrying
Dec  1 17:46:32 duper kernel: [    1.400054] ata1: softreset failed (device not ready)
Dec  1 17:46:32 duper kernel: [    1.400058] ata1: applying PMP SRST workaround and retrying
Dec  1 17:46:32 duper kernel: [    1.400064] usb 2-1: new high-speed USB device number 2 using ehci_hcd
Dec  1 17:46:32 duper kernel: [    1.572041] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Dec  1 17:46:32 duper kernel: [    1.572077] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Dec  1 17:46:32 duper kernel: [    1.592531] ata1.00: HPA detected: current 976771055, native 976773168
Dec  1 17:46:32 duper kernel: [    1.592599] ata1.00: ATA-8: SAMSUNG HD501LJ, CR100-10, max UDMA7
Dec  1 17:46:32 duper kernel: [    1.592602] ata1.00: 976771055 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
Dec  1 17:46:32 duper kernel: [    1.592607] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Dec  1 17:46:32 duper kernel: [    1.594634] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Dec  1 17:46:32 duper kernel: [    1.594637] ata1.00: configured for UDMA/133
Dec  1 17:46:32 duper kernel: [    1.594826] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HD501LJ  CR10 PQ: 0 ANSI: 5
Dec  1 17:46:32 duper kernel: [    1.595006] sd 0:0:0:0: [sda] 976771055 512-byte logical blocks: (500 GB/465 GiB)
Dec  1 17:46:32 duper kernel: [    1.595034] sd 0:0:0:0: Attached scsi generic sg0 type 0
Dec  1 17:46:32 duper kernel: [    1.595066] sd 0:0:0:0: [sda] Write Protect is off
Dec  1 17:46:32 duper kernel: [    1.595070] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Dec  1 17:46:32 duper kernel: [    1.595095] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec  1 17:46:32 duper kernel: [    1.600750] ata3.00: HPA detected: current 2930275055, native 2930277168
Dec  1 17:46:32 duper kernel: [    1.600755] ata3.00: ATA-8: ST31500341AS, CC1H, max UDMA/133
Dec  1 17:46:32 duper kernel: [    1.600758] ata3.00: 2930275055 sectors, multi 16: LBA48 NCQ (depth 31/32)
Dec  1 17:46:32 duper kernel: [    1.600762] ata3.00: SB600 AHCI: limiting to 255 sectors per cmd
Dec  1 17:46:32 duper kernel: [    1.615399]  sda: sda1 sda2 sda3
Dec  1 17:46:32 duper kernel: [    1.615867] sd 0:0:0:0: [sda] Attached SCSI disk
Dec  1 17:46:32 duper kernel: [    1.642641] ata3.00: SB600 AHCI: limiting to 255 sectors per cmd
Dec  1 17:46:32 duper kernel: [    1.642644] ata3.00: configured for UDMA/133
Dec  1 17:46:32 duper kernel: [    1.642748] scsi 2:0:0:0: Direct-Access     ATA      ST31500341AS     CC1H PQ: 0 ANSI: 5
Dec  1 17:46:32 duper kernel: [    1.642879] sd 2:0:0:0: [sdb] 2930275055 512-byte logical blocks: (1.50 TB/1.36 TiB)
Dec  1 17:46:32 duper kernel: [    1.642907] sd 2:0:0:0: Attached scsi generic sg1 type 0
Dec  1 17:46:32 duper kernel: [    1.642938] sd 2:0:0:0: [sdb] Write Protect is off
Dec  1 17:46:32 duper kernel: [    1.642942] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Dec  1 17:46:32 duper kernel: [    1.642980] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec  1 17:46:32 duper kernel: [    1.644031] usb 2-2: new high-speed USB device number 3 using ehci_hcd
Dec  1 17:46:32 duper kernel: [    1.686834]  sdb: sdb1 sdb2 < sdb5 >
Dec  1 17:46:32 duper kernel: [    1.687302] sd 2:0:0:0: [sdb] Attached SCSI disk
Dec  1 17:46:32 duper kernel: [    1.689274] Freeing unused kernel memory: 924k freed
Dec  1 17:46:32 duper kernel: [    1.689776] Write protecting the kernel read-only data: 12288k
Dec  1 17:46:32 duper kernel: [    1.696373] Freeing unused kernel memory: 1612k freed
Dec  1 17:46:32 duper kernel: [    1.702026] Freeing unused kernel memory: 1196k freed
Dec  1 17:46:32 duper kernel: [    1.846825] scsi4 : pata_atiixp
Dec  1 17:46:32 duper kernel: [    1.846862] [drm] Initialized drm 1.1.0 20060810
Dec  1 17:46:32 duper kernel: [    1.849457] scsi5 : pata_atiixp
Dec  1 17:46:32 duper kernel: [    1.850198] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf900 irq 14
Dec  1 17:46:32 duper kernel: [    1.850202] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf908 irq 15
Dec  1 17:46:32 duper kernel: [    1.857984] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Dec  1 17:46:32 duper kernel: [    1.858010] r8169 0000:02:0f.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Dec  1 17:46:32 duper kernel: [    1.858039] r8169 0000:02:0f.0: (unregistered net_device): not PCI Express
Dec  1 17:46:32 duper kernel: [    1.858558] r8169 0000:02:0f.0: eth0: RTL8169sc/8110sc at 0xffffc90000612000, 00:1d:7d:93:32:48, XID 18000000 IRQ 23
Dec  1 17:46:32 duper kernel: [    1.858562] r8169 0000:02:0f.0: eth0: jumbo features [frames: 7152 bytes, tx checksumming: ok]
Dec  1 17:46:32 duper kernel: [    1.916044] usb 5-1: new low-speed USB device number 2 using ohci_hcd
Dec  1 17:46:32 duper kernel: [    2.028498] ata5.00: ATAPI: DVDRW   20X20X12X, 6A31, max UDMA/66
Dec  1 17:46:32 duper kernel: [    2.060426] ata5.00: configured for UDMA/66
Dec  1 17:46:32 duper kernel: [    2.062197] scsi 4:0:0:0: CD-ROM            DVDRW    20X20X12X        6A31 PQ: 0 ANSI: 5
Dec  1 17:46:32 duper kernel: [    2.064913] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Dec  1 17:46:32 duper kernel: [    2.064916] cdrom: Uniform CD-ROM driver Revision: 3.20
Dec  1 17:46:32 duper kernel: [    2.065077] sr 4:0:0:0: Attached scsi CD-ROM sr0
Dec  1 17:46:32 duper kernel: [    2.065235] sr 4:0:0:0: Attached scsi generic sg2 type 5
Dec  1 17:46:32 duper kernel: [    2.073502] firewire_ohci 0000:02:0e.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Dec  1 17:46:32 duper kernel: [    2.078227] [drm] radeon defaulting to kernel modesetting.
Dec  1 17:46:32 duper kernel: [    2.078231] [drm] radeon kernel modesetting enabled.
Dec  1 17:46:32 duper kernel: [    2.078328] radeon 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Dec  1 17:46:32 duper kernel: [    2.078584] [drm] initializing kernel modesetting (RS690 0x1002:0x791E 0x1458:0xD001).
Dec  1 17:46:32 duper kernel: [    2.078618] [drm] register mmio base: 0xFDFE0000
Dec  1 17:46:32 duper kernel: [    2.078620] [drm] register mmio size: 65536
Dec  1 17:46:32 duper kernel: [    2.078910] ATOM BIOS: ATI
Dec  1 17:46:32 duper kernel: [    2.078934] radeon 0000:01:05.0: VRAM: 128M 0x00000000D0000000 - 0x00000000D7FFFFFF (128M used)
Dec  1 17:46:32 duper kernel: [    2.078938] radeon 0000:01:05.0: GTT: 512M 0x00000000A0000000 - 0x00000000BFFFFFFF
Dec  1 17:46:32 duper kernel: [    2.078960] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
Dec  1 17:46:32 duper kernel: [    2.078962] [drm] Driver supports precise vblank timestamp query.
Dec  1 17:46:32 duper kernel: [    2.078974] [drm] radeon: irq initialized.
Dec  1 17:46:32 duper kernel: [    2.079359] [drm] Detected VRAM RAM=128M, BAR=128M
Dec  1 17:46:32 duper kernel: [    2.079364] [drm] RAM width 128bits DDR
Dec  1 17:46:32 duper kernel: [    2.079462] [TTM] Zone  kernel: Available graphics memory: 1960088 kiB.
Dec  1 17:46:32 duper kernel: [    2.079464] [TTM] Initializing pool allocator.
Dec  1 17:46:32 duper kernel: [    2.079497] [drm] radeon: 128M of VRAM memory ready
Dec  1 17:46:32 duper kernel: [    2.079500] [drm] radeon: 512M of GTT memory ready.
Dec  1 17:46:32 duper kernel: [    2.079521] [drm] GART: num cpu pages 131072, num gpu pages 131072
Dec  1 17:46:32 duper kernel: [    2.083470] [drm] radeon: 1 quad pipes, 1 z pipes initialized.
Dec  1 17:46:32 duper kernel: [    2.091959] [drm] PCIE GART of 512M enabled (table at 0x00000000CF900000).
Dec  1 17:46:32 duper kernel: [    2.092112] radeon 0000:01:05.0: WB enabled
Dec  1 17:46:32 duper kernel: [    2.092205] [drm] Loading RS690/RS740 Microcode
Dec  1 17:46:32 duper kernel: [    2.096724] [drm] radeon: ring at 0x00000000A0001000
Dec  1 17:46:32 duper kernel: [    2.096745] [drm] ring test succeeded in 1 usecs
Dec  1 17:46:32 duper kernel: [    2.096889] [drm] radeon: ib pool ready.
Dec  1 17:46:32 duper kernel: [    2.096956] [drm] ib test succeeded in 0 usecs
Dec  1 17:46:32 duper kernel: [    2.096958] [drm] Enabling audio support
Dec  1 17:46:32 duper kernel: [    2.097223] [drm] Radeon Display Connectors
Dec  1 17:46:32 duper kernel: [    2.097225] [drm] Connector 0:
Dec  1 17:46:32 duper kernel: [    2.097227] [drm]   VGA
Dec  1 17:46:32 duper kernel: [    2.097230] [drm]   DDC: 0x7e50 0x7e40 0x7e54 0x7e44 0x7e58 0x7e48 0x7e5c 0x7e4c
Dec  1 17:46:32 duper kernel: [    2.097231] [drm]   Encoders:
Dec  1 17:46:32 duper kernel: [    2.097233] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
Dec  1 17:46:32 duper kernel: [    2.097235] [drm] Connector 1:
Dec  1 17:46:32 duper kernel: [    2.097236] [drm]   S-video
Dec  1 17:46:32 duper kernel: [    2.097237] [drm]   Encoders:
Dec  1 17:46:32 duper kernel: [    2.097239] [drm]     TV1: INTERNAL_KLDSCP_DAC1
Dec  1 17:46:32 duper kernel: [    2.097241] [drm] Connector 2:
Dec  1 17:46:32 duper kernel: [    2.097242] [drm]   HDMI-A
Dec  1 17:46:32 duper kernel: [    2.097244] [drm]   DDC: 0x7e40 0x7e50 0x7e44 0x7e54 0x7e48 0x7e58 0x7e4c 0x7e5c
Dec  1 17:46:32 duper kernel: [    2.097246] [drm]   Encoders:
Dec  1 17:46:32 duper kernel: [    2.097248] [drm]     DFP3: INTERNAL_LVTM1
Dec  1 17:46:32 duper kernel: [    2.098521] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:13.2/usb5/5-1/5-1:1.0/input/input2
Dec  1 17:46:32 duper kernel: [    2.098741] generic-usb 0003:045E:0040.0001: input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:13.2-1/input0
Dec  1 17:46:32 duper kernel: [    2.098950] usbcore: registered new interface driver usbhid
Dec  1 17:46:32 duper kernel: [    2.098952] usbhid: USB HID core driver
Dec  1 17:46:32 duper kernel: [    2.128090] firewire_ohci: Added fw-ohci device 0000:02:0e.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x2
Dec  1 17:46:32 duper kernel: [    2.224027] usb 5-2: new low-speed USB device number 3 using ohci_hcd
Dec  1 17:46:32 duper kernel: [    2.392948] [drm] fb mappable at 0xD8040000
Dec  1 17:46:32 duper kernel: [    2.392951] [drm] vram apper at 0xD8000000
Dec  1 17:46:32 duper kernel: [    2.392953] [drm] size 8294400
Dec  1 17:46:32 duper kernel: [    2.392954] [drm] fb depth is 24
Dec  1 17:46:32 duper kernel: [    2.392956] [drm]    pitch is 7680
Dec  1 17:46:32 duper kernel: [    2.393062] fbcon: radeondrmfb (fb0) is primary device
Dec  1 17:46:32 duper kernel: [    2.393157] Console: switching to colour frame buffer device 240x67
Dec  1 17:46:32 duper kernel: [    2.393203] fb0: radeondrmfb frame buffer device
Dec  1 17:46:32 duper kernel: [    2.393205] drm: registered panic notifier
Dec  1 17:46:32 duper kernel: [    2.393213] [drm] Initialized radeon 2.12.0 20080528 for 0000:01:05.0 on minor 0
Dec  1 17:46:32 duper kernel: [    2.420429] input: Microsoft Comfort Curve Keyboard 2000 as /devices/pci0000:00/0000:00:13.2/usb5/5-2/5-2:1.0/input/input3
Dec  1 17:46:32 duper kernel: [    2.420564] generic-usb 0003:045E:00DD.0002: input,hidraw1: USB HID v1.11 Keyboard [Microsoft Comfort Curve Keyboard 2000] on usb-0000:00:13.2-2/input0
Dec  1 17:46:32 duper kernel: [    2.435208] input: Microsoft Comfort Curve Keyboard 2000 as /devices/pci0000:00/0000:00:13.2/usb5/5-2/5-2:1.1/input/input4
Dec  1 17:46:32 duper kernel: [    2.435327] generic-usb 0003:045E:00DD.0003: input,hidraw2: USB HID v1.11 Device [Microsoft Comfort Curve Keyboard 2000] on usb-0000:00:13.2-2/input1
Dec  1 17:46:32 duper kernel: [    2.568039] usb 6-1: new low-speed USB device number 2 using ohci_hcd
Dec  1 17:46:32 duper kernel: [    2.628161] firewire_core: created device fw0: GUID 001a4d0000ecfbfb, S400
Dec  1 17:46:32 duper kernel: [    2.657647] EXT4-fs (sdb1): INFO: recovery required on readonly filesystem
Dec  1 17:46:32 duper kernel: [    2.657652] EXT4-fs (sdb1): write access will be enabled during recovery
Dec  1 17:46:32 duper kernel: [    4.573970] EXT4-fs (sdb1): orphan cleanup on readonly fs
Dec  1 17:46:32 duper kernel: [    4.573988] EXT4-fs (sdb1): ext4_orphan_cleanup: deleting unreferenced inode 3801377
Dec  1 17:46:32 duper kernel: [    4.574068] EXT4-fs (sdb1): ext4_orphan_cleanup: deleting unreferenced inode 3801872
Dec  1 17:46:32 duper kernel: [    4.574112] EXT4-fs (sdb1): ext4_orphan_cleanup: deleting unreferenced inode 3802344
Dec  1 17:46:32 duper kernel: [    4.574304] EXT4-fs (sdb1): 3 orphan inodes deleted
Dec  1 17:46:32 duper kernel: [    4.574307] EXT4-fs (sdb1): recovery complete
Dec  1 17:46:32 duper kernel: [    4.923482] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
Dec  1 17:46:32 duper kernel: [   15.227122] ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec  1 17:46:32 duper kernel: [   15.282548] Adding 2610524k swap on /dev/sdb5.  Priority:-1 extents:1 across:2610524k
Dec  1 17:46:32 duper kernel: [   15.328165] lp: driver loaded but no devices found
Dec  1 17:46:32 duper kernel: [   15.353606] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Dec  1 17:46:32 duper kernel: [   15.466567] parport_pc 00:09: reported by Plug and Play ACPI
Dec  1 17:46:32 duper kernel: [   15.466627] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Dec  1 17:46:32 duper kernel: [   15.513105] EXT4-fs (sdb1): re-mounted. Opts: errors=remount-ro
Dec  1 17:46:32 duper kernel: [   15.567187] lp0: using parport0 (interrupt-driven).
Dec  1 17:46:32 duper kernel: [   15.620200] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
Dec  1 17:46:32 duper kernel: [   15.620692] SP5100 TCO timer: SP5100 TCO WatchDog Timer Driver v0.01
Dec  1 17:46:32 duper kernel: [   15.620777] SP5100 TCO timer: mmio address 0xfec000f0 already in use
Dec  1 17:46:32 duper kernel: [   15.648698] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
Dec  1 17:46:32 duper kernel: [   15.649090] MCE: In-kernel MCE decoding enabled.
Dec  1 17:46:32 duper kernel: [   15.654336] EDAC MC: Ver: 2.1.0
Dec  1 17:46:32 duper kernel: [   15.658235] AMD64 EDAC driver v3.4.0
Dec  1 17:46:32 duper kernel: [   15.658280] EDAC amd64: DRAM ECC disabled.
Dec  1 17:46:32 duper kernel: [   15.658287] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
Dec  1 17:46:32 duper kernel: [   15.658288]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
Dec  1 17:46:32 duper kernel: [   15.658290]  (Note that use of the override may cause unknown side effects.)
Dec  1 17:46:32 duper kernel: [   15.719849] snd_hda_intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec  1 17:46:32 duper kernel: [   15.719856] hda_intel: position_fix set to 1 for device 1458:a022
Dec  1 17:46:32 duper kernel: [   15.749881] input: iMON Panel, Knob and Mouse(15c2:ffdc) as /devices/pci0000:00/0000:00:13.3/usb6/6-1/6-1:1.0/input/input5
Dec  1 17:46:32 duper kernel: [   15.759573] IR NEC protocol handler initialized
Dec  1 17:46:32 duper kernel: [   15.762148] hda_codec: ALC889A: BIOS auto-probing.
Dec  1 17:46:32 duper kernel: [   15.774464] imon 6-1:1.0: 0xffdc iMON VFD, MCE IR (id 0x9e)
Dec  1 17:46:32 duper kernel: [   15.778394] input: HDA ATI SB Line as /devices/pci0000:00/0000:00:14.2/sound/card0/input6
Dec  1 17:46:32 duper kernel: [   15.778587] input: HDA ATI SB Front Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input7
Dec  1 17:46:32 duper kernel: [   15.778911] input: HDA ATI SB Rear Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input8
Dec  1 17:46:32 duper kernel: [   15.779009] input: HDA ATI SB Front Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input9
Dec  1 17:46:32 duper kernel: [   15.779042] IR RC5(x) protocol handler initialized
Dec  1 17:46:32 duper kernel: [   15.779090] input: HDA ATI SB Line-Out Side as /devices/pci0000:00/0000:00:14.2/sound/card0/input10
Dec  1 17:46:32 duper kernel: [   15.779172] input: HDA ATI SB Line-Out CLFE as /devices/pci0000:00/0000:00:14.2/sound/card0/input11
Dec  1 17:46:32 duper kernel: [   15.779253] input: HDA ATI SB Line-Out Surround as /devices/pci0000:00/0000:00:14.2/sound/card0/input12
Dec  1 17:46:32 duper kernel: [   15.779329] input: HDA ATI SB Line-Out Front as /devices/pci0000:00/0000:00:14.2/sound/card0/input13
Dec  1 17:46:32 duper kernel: [   15.779843] snd_hda_intel 0000:01:05.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Dec  1 17:46:32 duper kernel: [   15.779922] snd_hda_intel 0000:01:05.2: irq 40 for MSI/MSI-X
Dec  1 17:46:32 duper kernel: [   15.783068] type=1400 audit(1354344392.030:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=660 comm="apparmor_parser"
Dec  1 17:46:32 duper kernel: [   15.783625] type=1400 audit(1354344392.030:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=660 comm="apparmor_parser"
Dec  1 17:46:32 duper kernel: [   15.783944] type=1400 audit(1354344392.030:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=660 comm="apparmor_parser"
Dec  1 17:46:32 duper kernel: [   15.787434] type=1400 audit(1354344392.034:5): apparmor="STATUS" operation="profile_load" name="/usr/sbin/ntpd" pid=714 comm="apparmor_parser"
Dec  1 17:46:32 duper kernel: [   15.798358] IR RC6 protocol handler initialized
Dec  1 17:46:32 duper kernel: [   15.812204] IR JVC protocol handler initialized
Dec  1 17:46:32 duper kernel: [   15.812395] Registered IR keymap rc-imon-mce
Dec  1 17:46:32 duper kernel: [   15.812537] input: iMON Remote (15c2:ffdc) as /devices/pci0000:00/0000:00:13.3/usb6/6-1/6-1:1.0/rc/rc0/input14
Dec  1 17:46:32 duper kernel: [   15.812605] rc0: iMON Remote (15c2:ffdc) as /devices/pci0000:00/0000:00:13.3/usb6/6-1/6-1:1.0/rc/rc0
Dec  1 17:46:32 duper kernel: [   15.814151] kjournald starting.  Commit interval 5 seconds
Dec  1 17:46:32 duper kernel: [   15.814361] EXT3-fs (sda1): using internal journal
Dec  1 17:46:32 duper kernel: [   15.814368] EXT3-fs (sda1): mounted filesystem with ordered data mode
Dec  1 17:46:32 duper kernel: [   15.827431] IR Sony protocol handler initialized
Dec  1 17:46:32 duper kernel: [   15.830431] r8169 0000:02:0f.0: eth0: link down
Dec  1 17:46:32 duper kernel: [   15.830445] r8169 0000:02:0f.0: eth0: link down
Dec  1 17:46:32 duper kernel: [   15.832786] ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec  1 17:46:32 duper kernel: [   15.836115] IR MCE Keyboard/mouse protocol handler initialized
Dec  1 17:46:32 duper kernel: [   15.836410] imon 6-1:1.0: iMON device (15c2:ffdc, intf0) on usb<6:2> initialized
Dec  1 17:46:32 duper kernel: [   15.836439] usbcore: registered new interface driver imon
Dec  1 17:46:32 duper kernel: [   15.844523] lirc_dev: IR Remote Control driver registered, major 249
Dec  1 17:46:32 duper kernel: [   15.844875] IR LIRC bridge handler initialized
Dec  1 17:46:32 duper kernel: [   15.860502] dvb-usb: found a 'DViCO FusionHDTV DVB-T Dual Digital 4' in warm state.
Dec  1 17:46:32 duper kernel: [   15.865014] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
Dec  1 17:46:32 duper kernel: [   15.893790] DVB: registering new adapter (DViCO FusionHDTV DVB-T Dual Digital 4)
Dec  1 17:46:32 duper kernel: [   15.997675] Bluetooth: Core ver 2.16
Dec  1 17:46:32 duper kernel: [   16.000140] NET: Registered protocol family 31
Dec  1 17:46:32 duper kernel: [   16.000145] Bluetooth: HCI device and connection manager initialized
Dec  1 17:46:32 duper kernel: [   16.000150] Bluetooth: HCI socket layer initialized
Dec  1 17:46:32 duper kernel: [   16.000152] Bluetooth: L2CAP socket layer initialized
Dec  1 17:46:32 duper kernel: [   16.000171] Bluetooth: SCO socket layer initialized
Dec  1 17:46:32 duper kernel: [   16.023668] Bluetooth: RFCOMM TTY layer initialized
Dec  1 17:46:32 duper kernel: [   16.023676] Bluetooth: RFCOMM socket layer initialized
Dec  1 17:46:32 duper kernel: [   16.023678] Bluetooth: RFCOMM ver 1.11
Dec  1 17:46:32 duper kernel: [   16.024380] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Dec  1 17:46:32 duper kernel: [   16.024384] Bluetooth: BNEP filters: protocol multicast
Dec  1 17:46:32 duper kernel: [   16.066373] DVB: registering adapter 0 frontend 0 (Zarlink ZL10353 DVB-T)...
Dec  1 17:46:32 duper kernel: [   16.093029] xc2028 5-0061: creating new instance
Dec  1 17:46:32 duper kernel: [   16.093034] xc2028 5-0061: type set to XCeive xc2028/xc3028 tuner
Dec  1 17:46:32 duper kernel: [   16.095817] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:14.4/0000:02:07.2/usb2/2-1/input/input15
Dec  1 17:46:32 duper kernel: [   16.095885] dvb-usb: schedule remote query interval to 100 msecs.
Dec  1 17:46:32 duper kernel: [   16.097033] dvb-usb: DViCO FusionHDTV DVB-T Dual Digital 4 successfully initialized and connected.
Dec  1 17:46:32 duper kernel: [   16.097062] dvb-usb: found a 'DViCO FusionHDTV DVB-T Dual Digital 4' in warm state.
Dec  1 17:46:32 duper kernel: [   16.097258] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
Dec  1 17:46:32 duper kernel: [   16.128437] DVB: registering new adapter (DViCO FusionHDTV DVB-T Dual Digital 4)
Dec  1 17:46:32 duper kernel: [   16.178231] cxusb: No IR receiver detected on this device.
Dec  1 17:46:32 duper kernel: [   16.178238] DVB: registering adapter 1 frontend 0 (Zarlink ZL10353 DVB-T)...
Dec  1 17:46:32 duper kernel: [   16.178364] xc2028 6-0061: creating new instance
Dec  1 17:46:32 duper kernel: [   16.178367] xc2028 6-0061: type set to XCeive xc2028/xc3028 tuner
Dec  1 17:46:32 duper kernel: [   16.179036] dvb-usb: DViCO FusionHDTV DVB-T Dual Digital 4 successfully initialized and connected.
Dec  1 17:46:32 duper kernel: [   16.179131] usbcore: registered new interface driver dvb_usb_cxusb
Dec  1 17:46:32 duper kernel: [   16.238821] ppdev: user-space parallel port driver
Dec  1 17:46:34 duper kernel: [   18.000782] r8169 0000:02:0f.0: eth0: link up
Dec  1 17:46:34 duper kernel: [   18.001420] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Dec  1 17:46:35 duper kernel: [   18.816027] hda-intel: azx_get_response timeout, switching to polling mode: last cmd=0x000f0000
Dec  1 17:46:36 duper kernel: [   19.820031] hda-intel: No response from codec, disabling MSI: last cmd=0x000f0000
Dec  1 17:46:37 duper kernel: [   20.824017] hda-intel: Codec #0 probe error; disabling it...
Dec  1 17:46:37 duper kernel: [   21.152479] init: failsafe main process (892) killed by TERM signal
Dec  1 17:46:37 duper kernel: [   21.236742] type=1400 audit(1354344397.486:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1103 comm="apparmor_parser"
Dec  1 17:46:37 duper kernel: [   21.237455] type=1400 audit(1354344397.486:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1104 comm="apparmor_parser"
Dec  1 17:46:37 duper kernel: [   21.238089] type=1400 audit(1354344397.486:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1104 comm="apparmor_parser"
Dec  1 17:46:37 duper kernel: [   21.238411] type=1400 audit(1354344397.486:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1104 comm="apparmor_parser"
Dec  1 17:46:37 duper kernel: [   21.243364] type=1400 audit(1354344397.490:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld" pid=1107 comm="apparmor_parser"
Dec  1 17:46:37 duper kernel: [   21.246751] type=1400 audit(1354344397.494:11): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/ntpd" pid=1108 comm="apparmor_parser"
Dec  1 17:46:37 duper kernel: [   21.252260] type=1400 audit(1354344397.502:12): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1110 comm="apparmor_parser"
Dec  1 17:46:37 duper kernel: [   21.252804] type=1400 audit(1354344397.502:13): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1105 comm="apparmor_parser"
Dec  1 17:46:37 duper kernel: [   21.259756] type=1400 audit(1354344397.506:14): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince//launchpad_integration" pid=1105 comm="apparmor_parser"
Dec  1 17:46:37 duper kernel: [   21.261385] type=1400 audit(1354344397.510:15): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince//sanitized_helper" pid=1105 comm="apparmor_parser"
Dec  1 17:46:37 duper kernel: [   21.438028] lirc_imon: module is from the staging directory, the quality is unknown, you have been warned.
Dec  1 17:46:37 duper kernel: [   21.438424] lirc_imon: Driver for SoundGraph iMON MultiMedia IR/Display, v0.8
Dec  1 17:46:37 duper kernel: [   21.438495] usbcore: registered new interface driver lirc_imon
Dec  1 17:46:37 duper kernel: [   21.467987] imon 6-1:1.0: Looks like you're trying to use an IR protocol this device does not support
Dec  1 17:46:37 duper kernel: [   21.467992] imon 6-1:1.0: Unsupported IR protocol specified, overriding to iMON IR protocol
Dec  1 17:46:37 duper kernel: [   21.531099] init: gdm main process (1209) killed by TERM signal
Dec  1 17:46:39 duper kernel: [   22.968026] hda_intel: azx_get_response timeout, switching to single_cmd mode: last cmd=0x00070503
Dec  1 17:46:41 duper kernel: [   25.500960] xc2028 5-0061: Loading 80 firmware images from xc3028-v27.fw, type: xc2028 firmware, ver 2.7
Dec  1 17:46:41 duper kernel: [   25.512330] xc2028 5-0061: Loading firmware for type=BASE F8MHZ (3), id 0000000000000000.
Dec  1 17:46:43 duper kernel: [   26.925877] init: plymouth-upstart-bridge main process (838) killed by TERM signal
Dec  1 17:46:43 duper kernel: [   27.287849] xc2028 5-0061: Loading firmware for type=D2633 DTV7 (90), id 0000000000000000.
Dec  1 17:46:43 duper kernel: [   27.314350] xc2028 5-0061: Loading SCODE for type=DTV6 QAM DTV7 DTV78 DTV8 ZARLINK456 SCODE HAS_IF_4760 (620003e0), id 0000000000000000.
Dec  1 17:46:43 duper kernel: [   27.532268] xc2028 6-0061: Loading 80 firmware images from xc3028-v27.fw, type: xc2028 firmware, ver 2.7
Dec  1 17:46:43 duper kernel: [   27.544405] xc2028 6-0061: Loading firmware for type=BASE F8MHZ (3), id 0000000000000000.
Dec  1 17:46:44 duper kernel: [   28.016027] eth0: no IPv6 routers present
Dec  1 17:46:45 duper kernel: [   29.323658] xc2028 6-0061: Loading firmware for type=D2633 DTV7 (90), id 0000000000000000.
Dec  1 17:46:45 duper kernel: [   29.354038] xc2028 6-0061: Loading SCODE for type=DTV6 QAM DTV7 DTV78 DTV8 ZARLINK456 SCODE HAS_IF_4760 (620003e0), id 0000000000000000.
Dec  1 17:46:46 duper kernel: [   30.577541] init: lightdm main process (1158) terminated with status 1

```

---

### Post by Yellow Pasque on 2012-12-01
Looks to be an issue with lightdm:
```
init: lightdm main process (1158) terminated with status 1
```
If you can ssh into the box, I would try installing another DM.

---

### Post by coldraven on 2012-12-01
I have the same X1250 card as you.
You cannot use the propriety driver from ATI/AMD it does not support Xorg beyond 7.4
See screenshot for my current working setup.

---

### Post by MrHyde on 2012-12-01
> **Temüjin said:**
> Looks to be an issue with lightdm:
```
init: lightdm main process (1158) terminated with status 1
```
If you can ssh into the box, I would try installing another DM.

I think we are on the right track here.  I uninstalled lightdm, which meant it defaulted to gdm. 

Now, on startup, a blank blue screen with a small black terminal on the top left hand side starts up.

Looking at the lightdm logs, I can see the following: 

The only error I can see is that it looks like the session greeter seems to be missing. 

```
[+1.99s] DEBUG: Starting new display for greeter
[+1.99s] DEBUG: Starting local X display
[+1.99s] DEBUG: Using VT 7
[+1.99s] DEBUG: Logging to /var/log/lightdm/x-0.log
[+1.99s] DEBUG: Writing X server authority to /var/run/lightdm/root/:0
[+1.99s] DEBUG: Launching X Server
[+1.99s] DEBUG: Launching process 3663: /usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+1.99s] DEBUG: Waiting for ready signal from X server :0
[+3.34s] DEBUG: Got signal 10 from process 3663
[+3.34s] DEBUG: Got signal from X server :0
[+3.34s] DEBUG: Connecting to XServer :0
[+3.35s] DEBUG: Starting greeter
[+3.35s] DEBUG: Started session 3762 with service 'lightdm', username 'lightdm'
[+3.38s] DEBUG: Session 3762 authentication complete with return value 0: Success
[+3.38s] DEBUG: Greeter authorized
[+3.38s] DEBUG: Logging to /var/log/lightdm/x-0-greeter.log
[+3.38s] DEBUG: Failed to load session file /usr/share/xgreeters/mythbuntu-lightdm-gtk-greeter.desktop: No such file or directory
[+3.38s] DEBUG: Greeter failed to start
[+3.38s] DEBUG: Stopping display
[+3.38s] DEBUG: Session 3762: Sending SIGTERM
[+3.38s] DEBUG: Greeter closed communication channel
[+3.38s] DEBUG: Session 3762 terminated with signal 15
[+3.38s] DEBUG: Greeter quit
[+3.38s] DEBUG: Sending signal 15 to process 3663
[+3.47s] DEBUG: Process 3663 exited with return value 0
[+3.47s] DEBUG: X server stopped
[+3.47s] DEBUG: Removing X server authority /var/run/lightdm/root/:0
[+3.48s] DEBUG: Releasing VT 7
[+3.48s] DEBUG: Display server stopped
[+3.48s] DEBUG: Display stopped
[+3.48s] DEBUG: Stopping X local seat, failed to start a display
[+3.48s] DEBUG: Stopping seat
[+3.48s] DEBUG: Seat stopped
[+3.48s] DEBUG: Required seat has stopped
[+3.48s] DEBUG: Stopping display manager
[+3.48s] DEBUG: Display manager stopped
[+3.48s] DEBUG: Stopping daemon
[+3.48s] DEBUG: Exiting with return value 1

```

---

