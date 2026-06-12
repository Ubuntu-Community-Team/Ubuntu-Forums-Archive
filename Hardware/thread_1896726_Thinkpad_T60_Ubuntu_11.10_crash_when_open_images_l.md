---
title: "Thinkpad T60: Ubuntu 11.10 crash when open images larger then 5 MB"
date: 2011-12-17
forum: Hardware
---

### Post by Kandi07 on 2011-12-17
Hi,

I have installed currently on my Thinkpad T60 the new Ubuntu 11.10 32-bit release.
Now, when I try to open a image larger then 5 MB the gnome deskop crash and returns to the logon screen.

Here are my specs:
andreas@laptop:~$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"

Output Xorg.12.log
```
[[  7665.349] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[  7665.349] X Protocol Version 11, Revision 0
[  7665.349] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[  7665.349] Current Operating System: Linux laptop 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686
[  7665.349] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic root=UUID=96ead88c-ebeb-46df-9773-eaa5ff017625 ro quiet splash vt.handoff=7
[  7665.349] Build Date: 29 September 2011  12:48:48AM
[  7665.349] xorg-server 2:1.10.4-1ubuntu4 (For technical support please see http://www.ubuntu.com/support) 
[  7665.350] Current version of pixman: 0.22.2
[  7665.350]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[  7665.350] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  7665.350] (==) Log file: "/var/log/Xorg.11.log", Time: Sat Dec 17 21:45:38 2011
[  7665.350] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  7665.351] (==) No Layout section.  Using the first Screen section.
[  7665.351] (==) No screen section available. Using defaults.
[  7665.351] (**) |-->Screen "Default Screen Section" (0)
[  7665.351] (**) |   |-->Monitor "<default monitor>"
[  7665.351] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[  7665.351] (==) Automatically adding devices
[  7665.351] (==) Automatically enabling devices
[  7665.351] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  7665.351]     Entry deleted from font path.
[  7665.352] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[  7665.352]     Entry deleted from font path.
[  7665.352] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[  7665.352]     Entry deleted from font path.
[  7665.352] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[  7665.352]     Entry deleted from font path.
[  7665.352] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[  7665.352]     Entry deleted from font path.
[  7665.352] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[  7665.352] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[  7665.352] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[  7665.352] (II) Loader magic: 0x823ada0
[  7665.352] (II) Module ABI versions:
[  7665.352]     X.Org ANSI C Emulation: 0.4
[  7665.352]     X.Org Video Driver: 10.0
[  7665.352]     X.Org XInput driver : 12.3
[  7665.352]     X.Org Server Extension : 5.0
[  7665.354] (--) PCI:*(0:1:0:0) 1002:7149:17aa:2005 rev 0, Mem @ 0xd8000000/134217728, 0xee100000/65536, I/O @ 0x00002000/256, BIOS @ 0x????????/131072
[  7665.354] (II) Open ACPI successful (/var/run/acpid.socket)
[  7665.354] (II) LoadModule: "extmod"
[  7665.354] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[  7665.355] (II) Module extmod: vendor="X.Org Foundation"
[  7665.355]     compiled for 1.10.4, module version = 1.0.0
[  7665.355]     Module class: X.Org Server Extension
[  7665.355]     ABI class: X.Org Server Extension, version 5.0
[  7665.355] (II) Loading extension MIT-SCREEN-SAVER
[  7665.355] (II) Loading extension XFree86-VidModeExtension
[  7665.355] (II) Loading extension XFree86-DGA
[  7665.355] (II) Loading extension DPMS
[  7665.355] (II) Loading extension XVideo
[  7665.355] (II) Loading extension XVideo-MotionCompensation
[  7665.355] (II) Loading extension X-Resource
[  7665.355] (II) LoadModule: "dbe"
[  7665.355] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[  7665.355] (II) Module dbe: vendor="X.Org Foundation"
[  7665.355]     compiled for 1.10.4, module version = 1.0.0
[  7665.355]     Module class: X.Org Server Extension
[  7665.355]     ABI class: X.Org Server Extension, version 5.0
[  7665.355] (II) Loading extension DOUBLE-BUFFER
[  7665.355] (II) LoadModule: "glx"
[  7665.356] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[  7665.356] (II) Module glx: vendor="X.Org Foundation"
[  7665.356]     compiled for 1.10.4, module version = 1.0.0
[  7665.356]     ABI class: X.Org Server Extension, version 5.0
[  7665.356] (==) AIGLX enabled
[  7665.356] (II) Loading extension GLX
[  7665.356] (II) LoadModule: "record"
[  7665.357] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[  7665.357] (II) Module record: vendor="X.Org Foundation"
[  7665.357]     compiled for 1.10.4, module version = 1.13.0
[  7665.357]     Module class: X.Org Server Extension
[  7665.357]     ABI class: X.Org Server Extension, version 5.0
[  7665.357] (II) Loading extension RECORD
[  7665.357] (II) LoadModule: "dri"
[  7665.357] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[  7665.358] (II) Module dri: vendor="X.Org Foundation"
[  7665.358]     compiled for 1.10.4, module version = 1.0.0
[  7665.358]     ABI class: X.Org Server Extension, version 5.0
[  7665.358] (II) Loading extension XFree86-DRI
[  7665.358] (II) LoadModule: "dri2"
[  7665.358] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[  7665.358] (II) Module dri2: vendor="X.Org Foundation"
[  7665.358]     compiled for 1.10.4, module version = 1.2.0
[  7665.358]     ABI class: X.Org Server Extension, version 5.0
[  7665.358] (II) Loading extension DRI2
[  7665.358] (==) Matched fglrx as autoconfigured driver 0
[  7665.358] (==) Matched ati as autoconfigured driver 1
[  7665.358] (==) Matched vesa as autoconfigured driver 2
[  7665.358] (==) Matched fbdev as autoconfigured driver 3
[  7665.358] (==) Assigned the driver to the xf86ConfigLayout
[  7665.358] (II) LoadModule: "fglrx"
[  7665.360] (WW) Warning, couldn't open module fglrx
[  7665.360] (II) UnloadModule: "fglrx"
[  7665.360] (II) Unloading fglrx
[  7665.360] (EE) Failed to load module "fglrx" (module does not exist, 0)
[  7665.360] (II) LoadModule: "ati"
[  7665.361] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[  7665.361] (II) Module ati: vendor="X.Org Foundation"
[  7665.361]     compiled for 1.10.2.902, module version = 6.14.99
[  7665.361]     Module class: X.Org Video Driver
[  7665.361]     ABI class: X.Org Video Driver, version 10.0
[  7665.361] (II) LoadModule: "radeon"
[  7665.362] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[  7665.362] (II) Module radeon: vendor="X.Org Foundation"
[  7665.362]     compiled for 1.10.2.902, module version = 6.14.99
[  7665.362]     Module class: X.Org Video Driver
[  7665.362]     ABI class: X.Org Video Driver, version 10.0
[  7665.362] (II) LoadModule: "vesa"
[  7665.363] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[  7665.363] (II) Module vesa: vendor="X.Org Foundation"
[  7665.363]     compiled for 1.10.2, module version = 2.3.0
[  7665.363]     Module class: X.Org Video Driver
[  7665.363]     ABI class: X.Org Video Driver, version 10.0
[  7665.363] (II) LoadModule: "fbdev"
[  7665.364] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[  7665.364] (II) Module fbdev: vendor="X.Org Foundation"
[  7665.364]     compiled for 1.10.0, module version = 0.4.2
[  7665.364]     ABI class: X.Org Video Driver, version 10.0
[  7665.364] (II) RADEON: Driver for ATI Radeon chipsets:
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
[  7665.368] (II) VESA: driver for VESA chipsets: vesa
[  7665.368] (II) FBDEV: driver for framebuffer: fbdev
[  7665.369] (++) using VT number 7

[  7665.369] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[  7665.369] (II) [KMS] Kernel modesetting enabled.
[  7665.369] (WW) Falling back to old probe method for vesa
[  7665.369] (WW) Falling back to old probe method for fbdev
[  7665.369] (II) Loading sub module "fbdevhw"
[  7665.369] (II) LoadModule: "fbdevhw"
[  7665.369] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[  7665.369] (II) Module fbdevhw: vendor="X.Org Foundation"
[  7665.369]     compiled for 1.10.4, module version = 0.0.2
[  7665.369]     ABI class: X.Org Video Driver, version 10.0
[  7665.369] (II) RADEON(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[  7665.369] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[  7665.369] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[  7665.369] (==) RADEON(0): Default visual is TrueColor
[  7665.369] (==) RADEON(0): RGB weight 888
[  7665.369] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[  7665.369] (--) RADEON(0): Chipset: "ATI Mobility Radeon X1300" (ChipID = 0x7149)
[  7665.369] (II) RADEON(0): PCIE card detected
[  7665.369] drmOpenDevice: node name is /dev/dri/card0
[  7665.369] drmOpenDevice: open result is 17, (OK)
[  7665.370] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[  7665.370] drmOpenDevice: node name is /dev/dri/card0
[  7665.370] drmOpenDevice: open result is 17, (OK)
[  7665.370] drmOpenByBusid: drmOpenMinor returns 17
[  7665.370] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[  7665.370] (II) Loading sub module "exa"
[  7665.370] (II) LoadModule: "exa"
[  7665.370] (II) Loading /usr/lib/xorg/modules/libexa.so
[  7665.370] (II) Module exa: vendor="X.Org Foundation"
[  7665.370]     compiled for 1.10.4, module version = 2.5.0
[  7665.370]     ABI class: X.Org Video Driver, version 10.0
[  7665.370] (II) RADEON(0): KMS Color Tiling: enabled
[  7665.370] (II) RADEON(0): KMS Pageflipping: enabled
[  7665.370] (II) RADEON(0): SwapBuffers wait for vsync: enabled
[  7665.420] (II) RADEON(0): Output VGA-0 has no monitor section
[  7665.420] (II) RADEON(0): Output LVDS has no monitor section
[  7665.444] (II) RADEON(0): Output DVI-0 has no monitor section
[  7665.496] (II) RADEON(0): EDID for output VGA-0
[  7665.496] (II) RADEON(0): EDID for output LVDS
[  7665.496] (II) RADEON(0): Manufacturer: LEN  Model: 4022  Serial#: 0
[  7665.496] (II) RADEON(0): Year: 2005  Week: 0
[  7665.496] (II) RADEON(0): EDID Version: 1.3
[  7665.496] (II) RADEON(0): Digital Display Input
[  7665.496] (II) RADEON(0): Max Image Size [cm]: horiz.: 29  vert.: 21
[  7665.496] (II) RADEON(0): Gamma: 2.20
[  7665.496] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off
[  7665.496] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[  7665.496] (II) RADEON(0): First detailed timing is preferred mode
[  7665.496] (II) RADEON(0): redX: 0.590 redY: 0.342   greenX: 0.319 greenY: 0.540
[  7665.496] (II) RADEON(0): blueX: 0.152 blueY: 0.137   whiteX: 0.313 whiteY: 0.329
[  7665.497] (II) RADEON(0): Supported established timings:
[  7665.497] (II) RADEON(0): 640x480@60Hz
[  7665.497] (II) RADEON(0): 800x600@60Hz
[  7665.497] (II) RADEON(0): 1024x768@60Hz
[  7665.497] (II) RADEON(0): Manufacturer's mask: 0
[  7665.497] (II) RADEON(0): Supported standard timings:
[  7665.497] (II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[  7665.497] (II) RADEON(0): Supported detailed timing:
[  7665.497] (II) RADEON(0): clock: 108.0 MHz   Image Size:  286 x 214 mm
[  7665.497] (II) RADEON(0): h_active: 1400  h_sync: 1448  h_sync_end 1560 h_blank_end 1688 h_border: 0
[  7665.497] (II) RADEON(0): v_active: 1050  v_sync: 1051  v_sync_end 1054 v_blanking: 1066 v_border: 0
[  7665.497] (II) RADEON(0): Supported detailed timing:
[  7665.497] (II) RADEON(0): clock: 90.0 MHz   Image Size:  286 x 214 mm
[  7665.497] (II) RADEON(0): h_active: 1400  h_sync: 1448  h_sync_end 1560 h_blank_end 1688 h_border: 0
[  7665.497] (II) RADEON(0): v_active: 1050  v_sync: 1051  v_sync_end 1054 v_blanking: 1066 v_border: 0
[  7665.497] (II) RADEON(0): Unknown vendor-specific block f
[  7665.497] (II) RADEON(0):  LTN141P4-L02
[  7665.497] (II) RADEON(0): EDID (in hex):
[  7665.497] (II) RADEON(0):     00ffffffffffff0030ae224000000000
[  7665.497] (II) RADEON(0):     000f0103801d1578ea2d059757518a27
[  7665.497] (II) RADEON(0):     23505421080081800101010101010101
[  7665.497] (II) RADEON(0):     010101010101302a7820511a10403070
[  7665.497] (II) RADEON(0):     13001ed61000001925237820511a1040
[  7665.497] (II) RADEON(0):     307013001ed6100000190000000f0090
[  7665.497] (II) RADEON(0):     43329043280f01004ca35034000000fe
[  7665.497] (II) RADEON(0):     004c544e31343150342d4c30320a0019
[  7665.497] (II) RADEON(0): Printing probed modes for output LVDS
[  7665.497] (II) RADEON(0): Modeline "1400x1050"x60.0  108.00  1400 1448 1560 1688  1050 1051 1054 1066 -hsync -vsync (64.0 kHz)
[  7665.497] (II) RADEON(0): Modeline "1400x1050"x50.0   89.97  1400 1448 1560 1688  1050 1051 1054 1066 -hsync -vsync (53.3 kHz)
[  7665.497] (II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
[  7665.497] (II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  7665.497] (II) RADEON(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
[  7665.497] (II) RADEON(0): Modeline "1280x854"x59.9   89.25  1280 1352 1480 1680  854 857 867 887 -hsync +vsync (53.1 kHz)
[  7665.498] (II) RADEON(0): Modeline "1280x800"x59.8   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
[  7665.498] (II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
[  7665.498] (II) RADEON(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
[  7665.498] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  7665.498] (II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
[  7665.498] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  7665.498] (II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
[  7665.498] (II) RADEON(0): Modeline "848x480"x59.7   31.50  848 872 952 1056  480 483 493 500 -hsync +vsync (29.8 kHz)
[  7665.498] (II) RADEON(0): Modeline "720x480"x59.7   26.75  720 744 808 896  480 483 493 500 -hsync +vsync (29.9 kHz)
[  7665.498] (II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  7665.498] (II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
[  7665.522] (II) RADEON(0): EDID for output DVI-0
[  7665.522] (II) RADEON(0): Not using default mode "640x350" (vrefresh out of range)
[  7665.522] (II) RADEON(0): Not using default mode "320x175" (vrefresh out of range)
[  7665.522] (II) RADEON(0): Not using default mode "640x400" (vrefresh out of range)
[  7665.522] (II) RADEON(0): Not using default mode "320x200" (vrefresh out of range)
[  7665.522] (II) RADEON(0): Not using default mode "720x400" (vrefresh out of range)
[  7665.522] (II) RADEON(0): Not using default mode "360x200" (vrefresh out of range)
[  7665.522] (II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
[  7665.522] (II) RADEON(0): Not using default mode "320x240" (vrefresh out of range)
[  7665.522] (II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
[  7665.522] (II) RADEON(0): Not using default mode "320x240" (vrefresh out of range)
[  7665.522] (II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
[  7665.522] (II) RADEON(0): Not using default mode "320x240" (vrefresh out of range)
[  7665.522] (II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
[  7665.522] (II) RADEON(0): Not using default mode "400x300" (vrefresh out of range)
[  7665.522] (II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
[  7665.522] (II) RADEON(0): Not using default mode "400x300" (vrefresh out of range)
[  7665.522] (II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
[  7665.522] (II) RADEON(0): Not using default mode "400x300" (vrefresh out of range)
[  7665.522] (II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
[  7665.522] (II) RADEON(0): Not using default mode "400x300" (vrefresh out of range)
[  7665.522] (II) RADEON(0): Not using default mode "1024x768i" (vrefresh out of range)
[  7665.522] (II) RADEON(0): Not using default mode "512x384i" (vrefresh out of range)
[  7665.522] (II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
[  7665.522] (II) RADEON(0): Not using default mode "512x384" (vrefresh out of range)
[  7665.522] (II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
[  7665.522] (II) RADEON(0): Not using default mode "512x384" (vrefresh out of range)
[  7665.522] (II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
[  7665.522] (II) RADEON(0): Not using default mode "512x384" (vrefresh out of range)
[  7665.522] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[  7665.522] (II) RADEON(0): Not using default mode "576x432" (vrefresh out of range)
[  7665.522] (II) RADEON(0): Not using default mode "1280x960" (hsync out of range)
[  7665.522] (II) RADEON(0): Not using default mode "640x480" (hsync out of range)
[  7665.522] (II) RADEON(0): Not using default mode "1280x960" (vrefresh out of range)
[  7665.522] (II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
[  7665.522] (II) RADEON(0): Not using default mode "1280x1024" (hsync out of range)
[  7665.522] (II) RADEON(0): Not using default mode "640x512" (hsync out of range)
[  7665.522] (II) RADEON(0): Not using default mode "1280x1024" (vrefresh out of range)
[  7665.522] (II) RADEON(0): Not using default mode "640x512" (vrefresh out of range)
[  7665.522] (II) RADEON(0): Not using default mode "1280x1024" (vrefresh out of range)
[  7665.522] (II) RADEON(0): Not using default mode "640x512" (vrefresh out of range)
[  7665.522] (II) RADEON(0): Not using default mode "1600x1200" (hsync out of range)
[  7665.522] (II) RADEON(0): Not using default mode "800x600" (hsync out of range)
[  7665.522] (II) RADEON(0): Not using default mode "1600x1200" (vrefresh out of range)
[  7665.522] (II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
[  7665.522] (II) RADEON(0): Not using default mode "1600x1200" (vrefresh out of range)
[  7665.522] (II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
[  7665.523] (II) RADEON(0): Not using default mode "1600x1200" (vrefresh out of range)
[  7665.523] (II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
[  7665.523] (II) RADEON(0): Not using default mode "1600x1200" (vrefresh out of range)
[  7665.523] (II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
[  7665.523] (II) RADEON(0): Not using default mode "1792x1344" (hsync out of range)
[  7665.523] (II) RADEON(0): Not using default mode "896x672" (hsync out of range)
[  7665.523] (II) RADEON(0): Not using default mode "1792x1344" (vrefresh out of range)
[  7665.523] (II) RADEON(0): Not using default mode "896x672" (vrefresh out of range)
[  7665.523] (II) RADEON(0): Not using default mode "1856x1392" (hsync out of range)
[  7665.523] (II) RADEON(0): Not using default mode "928x696" (hsync out of range)
[  7665.523] (II) RADEON(0): Not using default mode "1856x1392" (vrefresh out of range)
[  7665.523] (II) RADEON(0): Not using default mode "928x696" (vrefresh out of range)
[  7665.523] (II) RADEON(0): Not using default mode "1920x1440" (hsync out of range)
[  7665.523] (II) RADEON(0): Not using default mode "960x720" (hsync out of range)
[  7665.523] (II) RADEON(0): Not using default mode "1920x1440" (vrefresh out of range)
[  7665.523] (II) RADEON(0): Not using default mode "960x720" (vrefresh out of range)
[  7665.523] (II) RADEON(0): Not using default mode "832x624" (vrefresh out of range)
[  7665.523] (II) RADEON(0): Not using default mode "416x312" (vrefresh out of range)
[  7665.523] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[  7665.523] (II) RADEON(0): Not using default mode "576x432" (vrefresh out of range)
[  7665.523] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[  7665.523] (II) RADEON(0): Not using default mode "576x432" (vrefresh out of range)
[  7665.523] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[  7665.523] (II) RADEON(0): Not using default mode "576x432" (vrefresh out of range)
[  7665.523] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[  7665.523] (II) RADEON(0): Not using default mode "576x432" (vrefresh out of range)
[  7665.523] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[  7665.523] (II) RADEON(0): Not using default mode "576x432" (vrefresh out of range)
[  7665.523] (II) RADEON(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
[  7665.523] (II) RADEON(0): Not using default mode "1400x1050" (hsync out of range)
[  7665.523] (II) RADEON(0): Not using default mode "700x525" (hsync out of range)
[  7665.523] (II) RADEON(0): Not using default mode "1400x1050" (vrefresh out of range)
[  7665.523] (II) RADEON(0): Not using default mode "700x525" (vrefresh out of range)
[  7665.523] (II) RADEON(0): Not using default mode "1400x1050" (vrefresh out of range)
[  7665.523] (II) RADEON(0): Not using default mode "700x525" (vrefresh out of range)
[  7665.523] (II) RADEON(0): Not using default mode "1400x1050" (vrefresh out of range)
[  7665.523] (II) RADEON(0): Not using default mode "700x525" (vrefresh out of range)
[  7665.523] (II) RADEON(0): Not using default mode "1440x900" (hsync out of range)
[  7665.523] (II) RADEON(0): Not using default mode "720x450" (hsync out of range)
[  7665.523] (II) RADEON(0): Not using default mode "1600x1024" (hsync out of range)
[  7665.523] (II) RADEON(0): Not using default mode "800x512" (hsync out of range)
[  7665.523] (II) RADEON(0): Not using default mode "1680x1050" (hsync out of range)
[  7665.523] (II) RADEON(0): Not using default mode "840x525" (hsync out of range)
[  7665.523] (II) RADEON(0): Not using default mode "1680x1050" (hsync out of range)
[  7665.523] (II) RADEON(0): Not using default mode "840x525" (hsync out of range)
[  7665.523] (II) RADEON(0): Not using default mode "1680x1050" (vrefresh out of range)
[  7665.523] (II) RADEON(0): Not using default mode "840x525" (vrefresh out of range)
[  7665.523] (II) RADEON(0): Not using default mode "1680x1050" (vrefresh out of range)
[  7665.523] (II) RADEON(0): Not using default mode "840x525" (vrefresh out of range)
[  7665.523] (II) RADEON(0): Not using default mode "1680x1050" (vrefresh out of range)
[  7665.523] (II) RADEON(0): Not using default mode "840x525" (vrefresh out of range)
[  7665.523] (II) RADEON(0): Not using default mode "1920x1080" (hsync out of range)
[  7665.523] (II) RADEON(0): Not using default mode "960x540" (hsync out of range)
[  7665.523] (II) RADEON(0): Not using default mode "1920x1200" (hsync out of range)
[  7665.523] (II) RADEON(0): Not using default mode "960x600" (hsync out of range)
[  7665.523] (II) RADEON(0): Not using default mode "1920x1440" (vrefresh out of range)
[  7665.523] (II) RADEON(0): Not using default mode "960x720" (vrefresh out of range)
[  7665.523] (II) RADEON(0): Not using default mode "2048x1536" (hsync out of range)
[  7665.523] (II) RADEON(0): Not using default mode "1024x768" (hsync out of range)
[  7665.523] (II) RADEON(0): Not using default mode "2048x1536" (vrefresh out of range)
[  7665.523] (II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
[  7665.523] (II) RADEON(0): Not using default mode "2048x1536" (vrefresh out of range)
[  7665.523] (II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
[  7665.523] (II) RADEON(0): Printing probed modes for output DVI-0
[  7665.523] (II) RADEON(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[  7665.523] (II) RADEON(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
[  7665.523] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  7665.523] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  7665.523] (II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  7665.523] (II) RADEON(0): Modeline "680x384"x59.8   42.38  680 716 784 888  384 385 390 399 doublescan -hsync +vsync (47.7 kHz)
[  7665.523] (II) RADEON(0): Modeline "680x384"x60.0   36.00  680 704 720 760  384 385 390 395 doublescan +hsync -vsync (47.4 kHz)
[  7665.523] (II) RADEON(0): Modeline "576x432"x60.1   40.81  576 608 668 760  432 432 434 447 doublescan -hsync +vsync (53.7 kHz)
[  7665.523] (II) RADEON(0): Modeline "512x384"x60.0   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync (48.4 kHz)
[  7665.524] (II) RADEON(0): Modeline "400x300"x60.3   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz)
[  7665.524] (II) RADEON(0): Modeline "320x240"x60.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz)
[  7665.524] (II) RADEON(0): Output VGA-0 disconnected
[  7665.524] (II) RADEON(0): Output LVDS connected
[  7665.524] (II) RADEON(0): Output DVI-0 disconnected
[  7665.524] (II) RADEON(0): Using exact sizes for initial modes
[  7665.524] (II) RADEON(0): Output LVDS using initial mode 1400x1050
[  7665.524] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[  7665.524] (II) RADEON(0): mem size init: gart size :1fdff000 vram size: s:4000000 visible:3a1c000
[  7665.524] (II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
[  7665.524] (==) RADEON(0): DPI set to (96, 96)
[  7665.524] (II) Loading sub module "fb"
[  7665.524] (II) LoadModule: "fb"
[  7665.524] (II) Loading /usr/lib/xorg/modules/libfb.so
[  7665.524] (II) Module fb: vendor="X.Org Foundation"
[  7665.524]     compiled for 1.10.4, module version = 1.0.0
[  7665.524]     ABI class: X.Org ANSI C Emulation, version 0.4
[  7665.524] (II) Loading sub module "ramdac"
[  7665.524] (II) LoadModule: "ramdac"
[  7665.524] (II) Module "ramdac" already built-in
[  7665.524] (II) UnloadModule: "vesa"
[  7665.524] (II) Unloading vesa
[  7665.524] (II) UnloadModule: "fbdev"
[  7665.524] (II) Unloading fbdev
[  7665.524] (II) UnloadModule: "fbdevhw"
[  7665.524] (II) Unloading fbdevhw
[  7665.524] (--) Depth 24 pixmap format is 32 bpp
[  7665.524] (II) RADEON(0): [DRI2] Setup complete
[  7665.524] (II) RADEON(0): [DRI2]   DRI driver: r300
[  7665.525] (II) RADEON(0): Front buffer size: 5808K
[  7665.525] (II) RADEON(0): VRAM usage limit set to 48326K
[  7665.525] (==) RADEON(0): Backing store disabled
[  7665.525] (II) RADEON(0): Direct rendering enabled
[  7665.525] (II) RADEON(0): Render acceleration enabled for R300/R400/R500 type cards.
[  7665.525] (II) RADEON(0): Setting EXA maxPitchBytes
[  7665.525] (II) EXA(0): Driver allocated offscreen pixmaps
[  7665.525] (II) EXA(0): Driver registered support for the following operations:
[  7665.525] (II)         Solid
[  7665.525] (II)         Copy
[  7665.525] (II)         Composite (RENDER acceleration)
[  7665.525] (II)         UploadToScreen
[  7665.525] (II)         DownloadFromScreen
[  7665.525] (II) RADEON(0): Acceleration enabled
[  7665.525] (==) RADEON(0): DPMS enabled
[  7665.525] (==) RADEON(0): Silken mouse enabled
[  7665.525] (II) RADEON(0): Set up textured video
[  7665.525] (II) RADEON(0): [XvMC] Associated with Radeon Textured Video.
[  7665.525] (II) RADEON(0): [XvMC] Extension initialized.
[  7665.525] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[  7665.525] (--) RandR disabled
[  7665.525] (II) Initializing built-in extension Generic Event Extension
[  7665.525] (II) Initializing built-in extension SHAPE
[  7665.525] (II) Initializing built-in extension MIT-SHM
[  7665.525] (II) Initializing built-in extension XInputExtension
[  7665.525] (II) Initializing built-in extension XTEST
[  7665.525] (II) Initializing built-in extension BIG-REQUESTS
[  7665.525] (II) Initializing built-in extension SYNC
[  7665.525] (II) Initializing built-in extension XKEYBOARD
[  7665.525] (II) Initializing built-in extension XC-MISC
[  7665.525] (II) Initializing built-in extension SECURITY
[  7665.525] (II) Initializing built-in extension XINERAMA
[  7665.525] (II) Initializing built-in extension XFIXES
[  7665.525] (II) Initializing built-in extension RENDER
[  7665.525] (II) Initializing built-in extension RANDR
[  7665.526] (II) Initializing built-in extension COMPOSITE
[  7665.526] (II) Initializing built-in extension DAMAGE
[  7665.526] (II) Initializing built-in extension GESTURE
[  7665.540] (II) AIGLX: Trying DRI driver /usr/lib/i386-linux-gnu/dri/r300_dri.so
[  7665.553] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[  7665.553] (II) AIGLX: enabled GLX_INTEL_swap_event
[  7665.553] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[  7665.553] (II) AIGLX: enabled GLX_SGI_make_current_read
[  7665.553] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[  7665.553] (II) AIGLX: Loaded and initialized r300
[  7665.553] (II) GLX: Initialized DRI2 GL provider for screen 0
[  7666.024] (II) RADEON(0): Setting screen physical size to 370 x 277
[  7666.040] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[  7666.052] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[  7666.052] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  7666.052] (II) LoadModule: "evdev"
[  7666.052] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  7666.053] (II) Module evdev: vendor="X.Org Foundation"
[  7666.053]     compiled for 1.10.2, module version = 2.6.0
[  7666.053]     Module class: X.Org XInput Driver
[  7666.053]     ABI class: X.Org XInput driver, version 12.3
[  7666.053] (II) Using input driver 'evdev' for 'Power Button'
[  7666.053] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  7666.053] (**) Power Button: always reports core events
[  7666.053] (**) Power Button: Device: "/dev/input/event2"
[  7666.053] (--) Power Button: Found keys
[  7666.053] (II) Power Button: Configuring as keyboard
[  7666.053] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[  7666.053] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[  7666.053] (**) Option "xkb_rules" "evdev"
[  7666.053] (**) Option "xkb_model" "pc105"
[  7666.053] (**) Option "xkb_layout" "us"
[  7666.059] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[  7666.059] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[  7666.059] (II) Using input driver 'evdev' for 'Video Bus'
[  7666.059] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  7666.059] (**) Video Bus: always reports core events
[  7666.059] (**) Video Bus: Device: "/dev/input/event4"
[  7666.059] (--) Video Bus: Found keys
[  7666.059] (II) Video Bus: Configuring as keyboard
[  7666.059] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:05/LNXVIDEO:01/input/input4/event4"
[  7666.059] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[  7666.060] (**) Option "xkb_rules" "evdev"
[  7666.060] (**) Option "xkb_model" "pc105"
[  7666.060] (**) Option "xkb_layout" "us"
[  7666.062] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[  7666.062] (II) No input driver/identifier specified (ignoring)
[  7666.062] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[  7666.062] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[  7666.062] (II) Using input driver 'evdev' for 'Sleep Button'
[  7666.062] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  7666.062] (**) Sleep Button: always reports core events
[  7666.062] (**) Sleep Button: Device: "/dev/input/event1"
[  7666.062] (--) Sleep Button: Found keys
[  7666.062] (II) Sleep Button: Configuring as keyboard
[  7666.062] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1/event1"
[  7666.062] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[  7666.062] (**) Option "xkb_rules" "evdev"
[  7666.063] (**) Option "xkb_model" "pc105"
[  7666.063] (**) Option "xkb_layout" "us"
[  7666.068] (II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/event8)
[  7666.068] (**) Logitech USB-PS/2 Optical Mouse: Applying InputClass "evdev pointer catchall"
[  7666.068] (II) Using input driver 'evdev' for 'Logitech USB-PS/2 Optical Mouse'
[  7666.068] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  7666.068] (**) Logitech USB-PS/2 Optical Mouse: always reports core events
[  7666.068] (**) Logitech USB-PS/2 Optical Mouse: Device: "/dev/input/event8"
[  7666.068] (--) Logitech USB-PS/2 Optical Mouse: Found 3 mouse buttons
[  7666.068] (--) Logitech USB-PS/2 Optical Mouse: Found scroll wheel(s)
[  7666.068] (--) Logitech USB-PS/2 Optical Mouse: Found relative axes
[  7666.068] (--) Logitech USB-PS/2 Optical Mouse: Found x and y relative axes
[  7666.068] (II) Logitech USB-PS/2 Optical Mouse: Configuring as mouse
[  7666.068] (II) Logitech USB-PS/2 Optical Mouse: Adding scrollwheel support
[  7666.068] (**) Logitech USB-PS/2 Optical Mouse: YAxisMapping: buttons 4 and 5
[  7666.068] (**) Logitech USB-PS/2 Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  7666.068] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input8/event8"
[  7666.068] (II) XINPUT: Adding extended input device "Logitech USB-PS/2 Optical Mouse" (type: MOUSE)
[  7666.068] (II) Logitech USB-PS/2 Optical Mouse: initialized for relative axes.
[  7666.068] (**) Logitech USB-PS/2 Optical Mouse: (accel) keeping acceleration scheme 1
[  7666.068] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration profile 0
[  7666.068] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration factor: 2.000
[  7666.068] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration threshold: 4
[  7666.069] (II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/mouse2)
[  7666.069] (II) No input driver/identifier specified (ignoring)
[  7666.074] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[  7666.074] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[  7666.074] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[  7666.074] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  7666.074] (**) AT Translated Set 2 keyboard: always reports core events
[  7666.074] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[  7666.074] (--) AT Translated Set 2 keyboard: Found keys
[  7666.074] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[  7666.074] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[  7666.074] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[  7666.074] (**) Option "xkb_rules" "evdev"
[  7666.074] (**) Option "xkb_model" "pc105"
[  7666.074] (**) Option "xkb_layout" "us"
[  7666.075] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event5)
[  7666.075] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[  7666.075] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[  7666.075] (II) LoadModule: "synaptics"
[  7666.075] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[  7666.076] (II) Module synaptics: vendor="X.Org Foundation"
[  7666.076]     compiled for 1.10.4, module version = 1.4.1
[  7666.076]     Module class: X.Org XInput Driver
[  7666.076]     ABI class: X.Org XInput driver, version 12.3
[  7666.076] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[  7666.076] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[  7666.076] (**) SynPS/2 Synaptics TouchPad: always reports core events
[  7666.076] (**) Option "Device" "/dev/input/event5"
[  7666.076] (--) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[  7666.076] (--) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[  7666.076] (--) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[  7666.076] (--) SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[  7666.076] (--) SynPS/2 Synaptics TouchPad: buttons: left right double triple
[  7666.080] (--) SynPS/2 Synaptics TouchPad: touchpad found
[  7666.080] (**) SynPS/2 Synaptics TouchPad: always reports core events
[  7666.088] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input5/event5"
[  7666.088] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[  7666.088] (**) SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[  7666.088] (**) SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[  7666.088] (**) SynPS/2 Synaptics TouchPad: AccelFactor is now 0.040
[  7666.088] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[  7666.088] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[  7666.088] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[  7666.088] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[  7666.088] (II) SynPS/2 Synaptics TouchPad: failed to open grail, no gesture support
[  7666.088] (--) SynPS/2 Synaptics TouchPad: touchpad found
[  7666.089] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[  7666.089] (II) No input driver/identifier specified (ignoring)
[  7666.089] (II) config/udev: Adding input device TPPS/2 IBM TrackPoint (/dev/input/event7)
[  7666.089] (**) TPPS/2 IBM TrackPoint: Applying InputClass "evdev pointer catchall"
[  7666.089] (**) TPPS/2 IBM TrackPoint: Applying InputClass "trackpoint catchall"
[  7666.089] (II) Using input driver 'evdev' for 'TPPS/2 IBM TrackPoint'
[  7666.089] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  7666.090] (**) TPPS/2 IBM TrackPoint: always reports core events
[  7666.090] (**) TPPS/2 IBM TrackPoint: Device: "/dev/input/event7"
[  7666.090] (--) TPPS/2 IBM TrackPoint: Found 3 mouse buttons
[  7666.090] (--) TPPS/2 IBM TrackPoint: Found relative axes
[  7666.090] (--) TPPS/2 IBM TrackPoint: Found x and y relative axes
[  7666.090] (II) TPPS/2 IBM TrackPoint: Configuring as mouse
[  7666.090] (**) Option "Emulate3Buttons" "true"
[  7666.090] (**) Option "EmulateWheel" "true"
[  7666.090] (**) Option "EmulateWheelButton" "2"
[  7666.090] (**) Option "YAxisMapping" "4 5"
[  7666.090] (**) TPPS/2 IBM TrackPoint: YAxisMapping: buttons 4 and 5
[  7666.090] (**) Option "XAxisMapping" "6 7"
[  7666.090] (**) TPPS/2 IBM TrackPoint: XAxisMapping: buttons 6 and 7
[  7666.090] (**) TPPS/2 IBM TrackPoint: EmulateWheelButton: 2, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  7666.090] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/serio2/input/input7/event7"
[  7666.090] (II) XINPUT: Adding extended input device "TPPS/2 IBM TrackPoint" (type: MOUSE)
[  7666.090] (II) TPPS/2 IBM TrackPoint: initialized for relative axes.
[  7666.090] (**) TPPS/2 IBM TrackPoint: (accel) keeping acceleration scheme 1
[  7666.090] (**) TPPS/2 IBM TrackPoint: (accel) acceleration profile 0
[  7666.090] (**) TPPS/2 IBM TrackPoint: (accel) acceleration factor: 2.000
[  7666.090] (**) TPPS/2 IBM TrackPoint: (accel) acceleration threshold: 4
[  7666.091] (II) config/udev: Adding input device TPPS/2 IBM TrackPoint (/dev/input/mouse1)
[  7666.091] (II) No input driver/identifier specified (ignoring)
[  7666.096] (II) config/udev: Adding input device ThinkPad Extra Buttons (/dev/input/event6)
[  7666.096] (**) ThinkPad Extra Buttons: Applying InputClass "evdev keyboard catchall"
[  7666.096] (II) Using input driver 'evdev' for 'ThinkPad Extra Buttons'
[  7666.096] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  7666.096] (**) ThinkPad Extra Buttons: always reports core events
[  7666.096] (**) ThinkPad Extra Buttons: Device: "/dev/input/event6"
[  7666.097] (--) ThinkPad Extra Buttons: Found keys
[  7666.097] (II) ThinkPad Extra Buttons: Configuring as keyboard
[  7666.097] (**) Option "config_info" "udev:/sys/devices/platform/thinkpad_acpi/input/input6/event6"
[  7666.097] (II) XINPUT: Adding extended input device "ThinkPad Extra Buttons" (type: KEYBOARD)
[  7666.097] (**) Option "xkb_rules" "evdev"
[  7666.097] (**) Option "xkb_model" "pc105"
[  7666.097] (**) Option "xkb_layout" "us"
[  7666.500] (II) RADEON(0): EDID vendor "LEN", prod id 16418
[  7666.500] (II) RADEON(0): Printing DDC gathered Modelines:
[  7666.500] (II) RADEON(0): Modeline "1400x1050"x0.0  108.00  1400 1448 1560 1688  1050 1051 1054 1066 -hsync -vsync (64.0 kHz)
[  7666.500] (II) RADEON(0): Modeline "1400x1050"x0.0   89.97  1400 1448 1560 1688  1050 1051 1054 1066 -hsync -vsync (53.3 kHz)
[  7666.500] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  7666.500] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  7666.500] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  7666.500] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  7666.660] (II) RADEON(0): EDID vendor "LEN", prod id 16418
[  7666.660] (II) RADEON(0): Printing DDC gathered Modelines:
[  7666.660] (II) RADEON(0): Modeline "1400x1050"x0.0  108.00  1400 1448 1560 1688  1050 1051 1054 1066 -hsync -vsync (64.0 kHz)
[  7666.660] (II) RADEON(0): Modeline "1400x1050"x0.0   89.97  1400 1448 1560 1688  1050 1051 1054 1066 -hsync -vsync (53.3 kHz)
[  7666.660] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  7666.660] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  7666.661] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  7666.661] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  7666.816] (II) RADEON(0): EDID vendor "LEN", prod id 16418
[  7666.816] (II) RADEON(0): Printing DDC gathered Modelines:
[  7666.816] (II) RADEON(0): Modeline "1400x1050"x0.0  108.00  1400 1448 1560 1688  1050 1051 1054 1066 -hsync -vsync (64.0 kHz)
[  7666.816] (II) RADEON(0): Modeline "1400x1050"x0.0   89.97  1400 1448 1560 1688  1050 1051 1054 1066 -hsync -vsync (53.3 kHz)
[  7666.816] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  7666.816] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  7666.816] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  7666.816] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  7669.212] (II) AIGLX: Suspending AIGLX clients for VT switch
[  7843.950] (II) Open ACPI successful (/var/run/acpid.socket)
[  7843.950] (II) AIGLX: Resuming AIGLX clients after VT switch
[  7844.000] (II) RADEON(0): EDID vendor "LEN", prod id 16418
[  7844.000] (II) RADEON(0): Printing DDC gathered Modelines:
[  7844.000] (II) RADEON(0): Modeline "1400x1050"x0.0  108.00  1400 1448 1560 1688  1050 1051 1054 1066 -hsync -vsync (64.0 kHz)
[  7844.000] (II) RADEON(0): Modeline "1400x1050"x0.0   89.97  1400 1448 1560 1688  1050 1051 1054 1066 -hsync -vsync (53.3 kHz)
[  7844.000] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  7844.000] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  7844.000] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  7844.000] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  7844.027] (II) SynPS/2 Synaptics TouchPad: failed to open grail, no gesture support
[  7844.027] (--) SynPS/2 Synaptics TouchPad: touchpad found
[  7852.280] (II) RADEON(0): EDID vendor "LEN", prod id 16418
[  7852.280] (II) RADEON(0): Printing DDC gathered Modelines:
[  7852.280] (II) RADEON(0): Modeline "1400x1050"x0.0  108.00  1400 1448 1560 1688  1050 1051 1054 1066 -hsync -vsync (64.0 kHz)
[  7852.280] (II) RADEON(0): Modeline "1400x1050"x0.0   89.97  1400 1448 1560 1688  1050 1051 1054 1066 -hsync -vsync (53.3 kHz)
[  7852.280] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  7852.280] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  7852.280] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  7852.280] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  7852.572] (II) RADEON(0): EDID vendor "LEN", prod id 16418
[  7852.572] (II) RADEON(0): Printing DDC gathered Modelines:
[  7852.572] (II) RADEON(0): Modeline "1400x1050"x0.0  108.00  1400 1448 1560 1688  1050 1051 1054 1066 -hsync -vsync (64.0 kHz)
[  7852.572] (II) RADEON(0): Modeline "1400x1050"x0.0   89.97  1400 1448 1560 1688  1050 1051 1054 1066 -hsync -vsync (53.3 kHz)
[  7852.572] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  7852.572] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  7852.572] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  7852.572] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  7852.768] (II) RADEON(0): EDID vendor "LEN", prod id 16418
[  7852.768] (II) RADEON(0): Printing DDC gathered Modelines:
[  7852.768] (II) RADEON(0): Modeline "1400x1050"x0.0  108.00  1400 1448 1560 1688  1050 1051 1054 1066 -hsync -vsync (64.0 kHz)
[  7852.768] (II) RADEON(0): Modeline "1400x1050"x0.0   89.97  1400 1448 1560 1688  1050 1051 1054 1066 -hsync -vsync (53.3 kHz)
[  7852.768] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  7852.768] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  7852.768] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  7852.768] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  7852.801] (II) XKB: reuse xkmfile /var/lib/xkb/server-A77BBE312A49C9FE89948D38B2A8CB84C3CBB410.xkm
[  7852.871] (II) XKB: reuse xkmfile /var/lib/xkb/server-4A81F11AB84364ED6051FDB779C81EFB320B58BC.xkm
[  7852.876] (II) XKB: reuse xkmfile /var/lib/xkb/server-4A81F11AB84364ED6051FDB779C81EFB320B58BC.xkm
[  7852.887] (II) XKB: reuse xkmfile /var/lib/xkb/server-4A81F11AB84364ED6051FDB779C81EFB320B58BC.xkm
[  7858.304] (II) RADEON(0): EDID vendor "LEN", prod id 16418
[  7858.304] (II) RADEON(0): Printing DDC gathered Modelines:
[  7858.304] (II) RADEON(0): Modeline "1400x1050"x0.0  108.00  1400 1448 1560 1688  1050 1051 1054 1066 -hsync -vsync (64.0 kHz)
[  7858.304] (II) RADEON(0): Modeline "1400x1050"x0.0   89.97  1400 1448 1560 1688  1050 1051 1054 1066 -hsync -vsync (53.3 kHz)
[  7858.304] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  7858.304] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  7858.304] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  7858.304] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  8640.650] (II) XKB: reuse xkmfile /var/lib/xkb/server-4A81F11AB84364ED6051FDB779C81EFB320B58BC.xkm
[  8640.664] (II) XKB: generating xkmfile /var/lib/xkb/server-8AA988DD479FAABEC4FC3CCCF4CC29B4948840B4.xkm
[  8660.375] (II) XKB: reuse xkmfile /var/lib/xkb/server-4A81F11AB84364ED6051FDB779C81EFB320B58BC.xkm
[  8660.507] (II) XKB: generating xkmfile /var/lib/xkb/server-C0761131EB9CB35F53F523514E9E15D6FEC0093A.xkm


```

**If you need further logs please let me know!**

Thank you for your support!

Cheers,
Andi

---

### Post by Kandi07 on 2011-12-18
After a complete Software Update the problem was solved :D

---

