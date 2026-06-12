---
title: "Black screen with cursor in Ati Radeon 9550"
date: 2015-02-15
forum: Hardware
---

### Post by venneri2 on 2015-02-15
Hi,

I have used Ubuntu for a long time. Now I have Ubuntu 14.04 and Xubuntu 14.04. Both of them works perfectly after clean install. They load open radeon module and works great. However, after some reboots, suddenly X doesn't load correctly and I loose graphics. When everything worked, lspci -k returned:

01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV350 [Radeon 9550]
    Subsystem: Device 1fd3:4153
    Kernel driver in use: radeon

When I get black screen, output is:

01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV350 [Radeon 9550]
    Subsystem: Device 1fd3:4153
    Kernel driver in use: agpgart-amd64


I don't know why radeon module is not loaded, if I have not changed anything. I only try to configure screen resolution in xorg.conf, but after the black screen I deleted xorg.conf file, but I still got the black screen with blinking cursor. I attach my last Xorg.0.log is:

```

[    25.450] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[    25.450] X Protocol Version 11, Revision 0
[    25.450] Build Operating System: Linux 3.2.0-37-generic i686 Ubuntu
[    25.450] Current Operating System: Linux ubuntu-PC 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:12 UTC 2014 i686
[    25.450] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-32-generic root=UUID=e01f1e08-28ba-4214-82b0-6a811691777f ro quiet splash
[    25.450] Build Date: 16 April 2014  01:40:08PM
[    25.450] xorg-server 2:1.15.1-0ubuntu2 (For technical support please see http://www.ubuntu.com/support) 
[    25.450] Current version of pixman: 0.30.2
[    25.450]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    25.450] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    25.450] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Feb 15 00:19:44 2015
[    25.451] (==) Using config file: "/etc/X11/xorg.conf"
[    25.451] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    25.470] (==) ServerLayout "Default Layout"
[    25.470] (**) |-->Screen "Default Screen" (0)
[    25.470] (**) |   |-->Monitor "Configured Monitor"
[    25.470] (**) |   |-->Device "Radeon9550"
[    25.470] (==) Automatically adding devices
[    25.470] (==) Automatically enabling devices
[    25.470] (==) Automatically adding GPU devices
[    25.470] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    25.470]     Entry deleted from font path.
[    25.470] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    25.470]     Entry deleted from font path.
[    25.470] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    25.470]     Entry deleted from font path.
[    25.470] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    25.470]     Entry deleted from font path.
[    25.470] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    25.470]     Entry deleted from font path.
[    25.470] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    25.470] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    25.470] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    25.470] (II) Loader magic: 0xb77d06c0
[    25.470] (II) Module ABI versions:
[    25.470]     X.Org ANSI C Emulation: 0.4
[    25.470]     X.Org Video Driver: 15.0
[    25.470]     X.Org XInput driver : 20.0
[    25.470]     X.Org Server Extension : 8.0
[    25.472] (--) PCI:*(0:1:0:0) 1002:4153:1fd3:4153 rev 0, Mem @ 0xe0000000/268435456, 0xff5f0000/65536, I/O @ 0x0000c000/256, BIOS @ 0x????????/131072
[    25.472] (--) PCI: (0:1:0:1) 1002:4173:1fd3:4152 rev 0, Mem @ 0xd0000000/268435456, 0xff5e0000/65536
[    25.473] Initializing built-in extension Generic Event Extension
[    25.473] Initializing built-in extension SHAPE
[    25.473] Initializing built-in extension MIT-SHM
[    25.473] Initializing built-in extension XInputExtension
[    25.473] Initializing built-in extension XTEST
[    25.473] Initializing built-in extension BIG-REQUESTS
[    25.473] Initializing built-in extension SYNC
[    25.473] Initializing built-in extension XKEYBOARD
[    25.473] Initializing built-in extension XC-MISC
[    25.473] Initializing built-in extension SECURITY
[    25.473] Initializing built-in extension XINERAMA
[    25.473] Initializing built-in extension XFIXES
[    25.473] Initializing built-in extension RENDER
[    25.473] Initializing built-in extension RANDR
[    25.473] Initializing built-in extension COMPOSITE
[    25.473] Initializing built-in extension DAMAGE
[    25.473] Initializing built-in extension MIT-SCREEN-SAVER
[    25.473] Initializing built-in extension DOUBLE-BUFFER
[    25.473] Initializing built-in extension RECORD
[    25.473] Initializing built-in extension DPMS
[    25.473] Initializing built-in extension Present
[    25.473] Initializing built-in extension DRI3
[    25.473] Initializing built-in extension X-Resource
[    25.473] Initializing built-in extension XVideo
[    25.473] Initializing built-in extension XVideo-MotionCompensation
[    25.473] Initializing built-in extension SELinux
[    25.473] Initializing built-in extension XFree86-VidModeExtension
[    25.473] Initializing built-in extension XFree86-DGA
[    25.473] Initializing built-in extension XFree86-DRI
[    25.473] Initializing built-in extension DRI2
[    25.473] (II) LoadModule: "glx"
[    25.525] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    25.980] (II) Module glx: vendor="X.Org Foundation"
[    25.980]     compiled for 1.15.1, module version = 1.0.0
[    25.980]     ABI class: X.Org Server Extension, version 8.0
[    25.980] (==) AIGLX enabled
[    25.980] Loading extension GLX
[    25.980] (II) LoadModule: "radeon"
[    25.980] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    26.045] (II) Module radeon: vendor="X.Org Foundation"
[    26.045]     compiled for 1.15.1, module version = 7.3.0
[    26.045]     Module class: X.Org Video Driver
[    26.045]     ABI class: X.Org Video Driver, version 15.0
[    26.045] (II) RADEON: Driver for ATI Radeon chipsets:
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
    KABINI, KABINI, KABINI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
    KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
    KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
    HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII,
    HAWAII, HAWAII, HAWAII, HAWAII
[    26.067] (++) using VT number 7

[    26.068] (II) [KMS] drm report modesetting isn't supported.
[    26.068] (EE) Screen 0 deleted because of no matching config section.
[    26.068] (II) UnloadModule: "radeon"
[    26.068] (EE) Device(s) detected, but none match those in the config file.
[    26.068] (==) Matched fglrx as autoconfigured driver 0
[    26.068] (==) Matched ati as autoconfigured driver 1
[    26.068] (==) Matched modesetting as autoconfigured driver 2
[    26.068] (==) Matched fbdev as autoconfigured driver 3
[    26.068] (==) Matched vesa as autoconfigured driver 4
[    26.068] (==) Assigned the driver to the xf86ConfigLayout
[    26.068] (II) LoadModule: "fglrx"
[    26.086] (WW) Warning, couldn't open module fglrx
[    26.086] (II) UnloadModule: "fglrx"
[    26.086] (II) Unloading fglrx
[    26.086] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    26.086] (II) LoadModule: "ati"
[    26.087] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    26.087] (II) Module ati: vendor="X.Org Foundation"
[    26.087]     compiled for 1.15.1, module version = 7.3.0
[    26.087]     Module class: X.Org Video Driver
[    26.087]     ABI class: X.Org Video Driver, version 15.0
[    26.087] (II) LoadModule: "radeon"
[    26.087] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    26.087] (II) Module radeon: vendor="X.Org Foundation"
[    26.087]     compiled for 1.15.1, module version = 7.3.0
[    26.087]     Module class: X.Org Video Driver
[    26.087]     ABI class: X.Org Video Driver, version 15.0
[    26.087] (II) LoadModule: "modesetting"
[    26.087] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    26.088] (II) Module modesetting: vendor="X.Org Foundation"
[    26.088]     compiled for 1.15.0, module version = 0.8.1
[    26.088]     Module class: X.Org Video Driver
[    26.088]     ABI class: X.Org Video Driver, version 15.0
[    26.088] (II) LoadModule: "fbdev"
[    26.088] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    26.088] (II) Module fbdev: vendor="X.Org Foundation"
[    26.088]     compiled for 1.15.0, module version = 0.4.4
[    26.088]     Module class: X.Org Video Driver
[    26.088]     ABI class: X.Org Video Driver, version 15.0
[    26.088] (II) LoadModule: "vesa"
[    26.088] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    26.089] (II) Module vesa: vendor="X.Org Foundation"
[    26.089]     compiled for 1.15.0, module version = 2.3.3
[    26.089]     Module class: X.Org Video Driver
[    26.089]     ABI class: X.Org Video Driver, version 15.0
[    26.089] (II) RADEON: Driver for ATI Radeon chipsets:
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
    KABINI, KABINI, KABINI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
    KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
    KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
    HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII,
    HAWAII, HAWAII, HAWAII, HAWAII
[    26.117] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    26.117] (II) FBDEV: driver for framebuffer: fbdev
[    26.117] (II) VESA: driver for VESA chipsets: vesa
[    26.117] (++) using VT number 7

[    26.117] (WW) xf86OpenConsole: setpgid failed: Operation not permitted
[    26.117] (WW) xf86OpenConsole: setsid failed: Operation not permitted
[    26.118] (II) [KMS] drm report modesetting isn't supported.
[    26.118] (EE) open /dev/dri/card0: No such file or directory
[    26.118] (WW) Falling back to old probe method for modesetting
[    26.118] (EE) open /dev/dri/card0: No such file or directory
[    26.118] (II) Loading sub module "fbdevhw"
[    26.118] (II) LoadModule: "fbdevhw"
[    26.119] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    26.119] (II) Module fbdevhw: vendor="X.Org Foundation"
[    26.119]     compiled for 1.15.1, module version = 0.0.2
[    26.119]     ABI class: X.Org Video Driver, version 15.0
[    26.119] (EE) open /dev/fb0: No such file or directory
[    26.119] (WW) Falling back to old probe method for fbdev
[    26.119] (II) Loading sub module "fbdevhw"
[    26.119] (II) LoadModule: "fbdevhw"
[    26.119] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    26.119] (II) Module fbdevhw: vendor="X.Org Foundation"
[    26.119]     compiled for 1.15.1, module version = 0.0.2
[    26.119]     ABI class: X.Org Video Driver, version 15.0
[    26.119] (EE) open /dev/fb0: No such file or directory
[    26.119] vesa: Ignoring device with a bound kernel driver
[    26.119] (WW) Falling back to old probe method for vesa
[    26.119] (EE) Screen 0 deleted because of no matching config section.
[    26.119] (II) UnloadModule: "radeon"
[    26.119] (EE) Screen 0 deleted because of no matching config section.
[    26.119] (II) UnloadModule: "modesetting"
[    26.119] (EE) Screen 0 deleted because of no matching config section.
[    26.119] (II) UnloadModule: "fbdev"
[    26.123] (II) UnloadSubModule: "fbdevhw"
[    26.123] (EE) Screen 0 deleted because of no matching config section.
[    26.123] (II) UnloadModule: "vesa"
[    26.123] (EE) Device(s) detected, but none match those in the config file.
[    26.123] (EE) 
Fatal server error:
[    26.123] (EE) no screens found(EE) 
[    26.123] (EE) 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[    26.123] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    26.124] (EE) 
[    26.127] (EE) Server terminated with error (1). Closing log file.

```

Thanks in advance,

---

### Post by Yellow Pasque on 2015-02-15
```
(II) [KMS] drm report modesetting isn't supported.
```

^I think I'd look for clues in dmesg about why KMS isn't working.

---

### Post by venneri2 on 2015-02-15
Hi,

I don't know what to look for exactly in dmesg. I've looked for kms, modesetting and drm, and I have not found anything. I attach dmesg output:

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.13.0-32-generic (buildd@roseapple) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #57-Ubuntu SMP Tue Jul 15 03:51:12 UTC 2014 (Ubuntu 3.13.0-32.57-generic 3.13.11.4)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009fbff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009fc00-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e8000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000007ffaffff] usable
[    0.000000] BIOS-e820: [mem 0x000000007ffb0000-0x000000007ffbffff] ACPI data
[    0.000000] BIOS-e820: [mem 0x000000007ffc0000-0x000000007ffeffff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000007fff0000-0x000000007fffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff7c0000-0x00000000ffffffff] reserved
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.3 present.
[    0.000000] DMI:          K8Upgrade-NF3/K8Upgrade-NF3, BIOS P2.10 08/07/2006
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0x7ffb0 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FF80000000 write-back
[    0.000000]   1 disabled
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] initial memory mapped: [mem 0x00000000-0x01ffffff]
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x37800000-0x379fffff]
[    0.000000]  [mem 0x37800000-0x379fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x34000000-0x377fffff]
[    0.000000]  [mem 0x34000000-0x377fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0x33ffffff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x33ffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x37a00000-0x37bfdfff]
[    0.000000]  [mem 0x37a00000-0x37bfdfff] page 4k
[    0.000000] BRK [0x01b8e000, 0x01b8efff] PGTABLE
[    0.000000] RAMDISK: [mem 0x35c3c000-0x36e15fff]
[    0.000000] ACPI: RSDP 000f8710 000014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 7ffb0000 000030 (v01 A M I  OEMRSDT  08000607 MSFT 00000097)
[    0.000000] ACPI: FACP 7ffb0200 000084 (v02 A M I  OEMFACP  08000607 MSFT 00000097)
[    0.000000] ACPI: DSDT 7ffb03f0 003F26 (v01  K8UNF K8UNF201 00000201 INTL 02002026)
[    0.000000] ACPI: FACS 7ffc0000 000040
[    0.000000] ACPI: APIC 7ffb0390 00005C (v01 A M I  OEMAPIC  08000607 MSFT 00000097)
[    0.000000] ACPI: OEMB 7ffc0040 000056 (v01 A M I  AMI_OEM  08000607 MSFT 00000097)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1155MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] BRK [0x01b8f000, 0x01b8ffff] PGTABLE
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   Normal   [mem 0x01000000-0x37bfdfff]
[    0.000000]   HighMem  [mem 0x37bfe000-0x7ffaffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009efff]
[    0.000000]   node   0: [mem 0x00100000-0x7ffaffff]
[    0.000000] On node 0 totalpages: 524110
[    0.000000] free_area_init_node: node 0, pgdat c1997200, node_mem_map f4c3c020
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3998 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 224254 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2312 pages used for memmap
[    0.000000]   HighMem zone: 295858 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: BIOS IRQ0 override ignored.
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] smpboot: Allowing 2 CPUs, 1 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000e7fff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e8000-0x000fffff]
[    0.000000] e820: [mem 0x80000000-0xff7bffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @f7bd6000 s36096 r0 d21248 u57344
[    0.000000] pcpu-alloc: s36096 r0 d21248 u57344 alloc=14*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 522326
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-32-generic root=UUID=e01f1e08-28ba-4214-82b0-6a811691777f ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 4193656 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:0007ffb0)
[    0.000000] Memory: 2044808K/2096440K available (6528K kernel code, 639K rwdata, 2760K rodata, 872K init, 924K bss, 51632K reserved, 1183432K highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff14000 - 0xfffff000   ( 940 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc19b4000 - 0xc1a8e000   ( 872 kB)
[    0.000000]       .data : 0xc1660532 - 0xc19b3e80   (3406 kB)
[    0.000000]       .text : 0xc1000000 - 0xc1660532   (6529 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=8 to nr_cpu_ids=2.
[    0.000000] NR_IRQS:2304 nr_irqs:512 16
[    0.000000] CPU 0 irqstacks, hard=f7008000 soft=f700a000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 1808.905 MHz processor
[    0.000000] tsc: Marking TSC unstable due to TSCs unsynchronized
[    0.004006] Calibrating delay loop (skipped), value calculated using timer frequency.. 3617.81 BogoMIPS (lpj=7235620)
[    0.004011] pid_max: default: 32768 minimum: 301
[    0.004072] Security Framework initialized
[    0.004101] AppArmor: AppArmor initialized
[    0.004103] Yama: becoming mindful.
[    0.004183] Mount-cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.004187] Mountpoint-cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.004507] Initializing cgroup subsys memory
[    0.004519] Initializing cgroup subsys devices
[    0.004522] Initializing cgroup subsys freezer
[    0.004525] Initializing cgroup subsys blkio
[    0.004528] Initializing cgroup subsys perf_event
[    0.004533] Initializing cgroup subsys hugetlb
[    0.004569] mce: CPU supports 5 MCE banks
[    0.004590] Last level iTLB entries: 4KB 512, 2MB 8, 4MB 4
[    0.004590] Last level dTLB entries: 4KB 512, 2MB 8, 4MB 4
[    0.004590] tlb_flushall_shift: 4
[    0.018877] ACPI: Core revision 20131115
[    0.022431] ACPI: All ACPI Tables successfully acquired
[    0.022611] ftrace: allocating 27783 entries in 55 pages
[    0.032154] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.032523] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.073358] smpboot: CPU0: AMD Sempron(tm) Processor 3100+ (fam: 0f, model: 2c, stepping: 02)
[    0.076000] Performance Events: AMD PMU driver.
[    0.076000] ... version:                0
[    0.076000] ... bit width:              48
[    0.076000] ... generic registers:      4
[    0.076000] ... value mask:             0000ffffffffffff
[    0.076000] ... max period:             00007fffffffffff
[    0.076000] ... fixed-purpose events:   0
[    0.076000] ... event mask:             000000000000000f
[    0.076000] x86: Booted up 1 node, 1 CPUs
[    0.076000] smpboot: Total of 1 processors activated (3617.81 BogoMIPS)
[    0.076000] devtmpfs: initialized
[    0.076000] EVM: security.selinux
[    0.076000] EVM: security.SMACK64
[    0.076000] EVM: security.ima
[    0.076000] EVM: security.capability
[    0.076000] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.076000] PM: Registering ACPI NVS region [mem 0x7ffc0000-0x7ffeffff] (196608 bytes)
[    0.076852] pinctrl core: initialized pinctrl subsystem
[    0.076979] regulator-dummy: no parameters
[    0.077014] RTC time:  0:19:19, date: 02/15/15
[    0.077081] NET: Registered protocol family 16
[    0.077293] EISA bus registered
[    0.077296] cpuidle: using governor ladder
[    0.077298] cpuidle: using governor menu
[    0.077305] node 0 link 0: io port [1000, ffffff]
[    0.077309] TOM: 0000000080000000 aka 2048M
[    0.077314] node 0 link 0: mmio [a0000, bffff]
[    0.077318] node 0 link 0: mmio [80000000, fe0bffff]
[    0.077323] bus: [bus 00-ff] on node 0 link 0
[    0.077325] bus: 00 [io  0x0000-0xffff]
[    0.077328] bus: 00 [mem 0x000a0000-0x000bffff]
[    0.077330] bus: 00 [mem 0x80000000-0xfcffffffff]
[    0.077398] ACPI: bus type PCI registered
[    0.077402] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.078269] PCI: Using configuration type 1 for base access
[    0.079941] bio: create slab <bio-0> at 0
[    0.080184] ACPI: Added _OSI(Module Device)
[    0.080187] ACPI: Added _OSI(Processor Device)
[    0.080189] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.080191] ACPI: Added _OSI(Processor Aggregator Device)
[    0.081751] ACPI: Executed 1 blocks of module-level executable AML code
[    0.083223] ACPI: Interpreter enabled
[    0.083238] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)
[    0.083243] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S3_] (20131115/hwxface-580)
[    0.083256] ACPI: (supports S0 S1 S4 S5)
[    0.083259] ACPI: Using IOAPIC for interrupt routing
[    0.083299] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.083418] ACPI: No dock devices found.
[    0.088298] ACPI: Power Resource [ISAV] (on)
[    0.090971] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.090980] acpi PNP0A03:00: _OSC: OS supports [ASPM ClockPM Segments MSI]
[    0.090988] acpi PNP0A03:00: _OSC failed (AE_NOT_FOUND); disabling ASPM
[    0.091114] acpi PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.091118] acpi PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.091121] acpi PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.091124] acpi PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff] (ignored)
[    0.091127] acpi PNP0A03:00: host bridge window [mem 0x80000000-0xffffffff] (ignored)
[    0.091130] PCI: root bus 00: hardware-probed resources
[    0.091136] acpi PNP0A03:00: fail to add MMCONFIG information, can't access extended PCI configuration space under this bridge.
[    0.091268] PCI host bridge to bus 0000:00
[    0.091273] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.091276] pci_bus 0000:00: root bus resource [io  0x0000-0xffff]
[    0.091279] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.091282] pci_bus 0000:00: root bus resource [mem 0x80000000-0xfcffffffff]
[    0.091299] pci 0000:00:00.0: [10de:00e1] type 00 class 0x060000
[    0.091310] pci 0000:00:00.0: reg 0x10: [mem 0xf8000000-0xfbffffff pref]
[    0.091422] pci 0000:00:01.0: [10de:00e0] type 00 class 0x060100
[    0.091517] pci 0000:00:01.1: [10de:00e4] type 00 class 0x0c0500
[    0.091527] pci 0000:00:01.1: reg 0x10: [io  0x5080-0x509f]
[    0.091541] pci 0000:00:01.1: reg 0x20: [io  0x5000-0x503f]
[    0.091547] pci 0000:00:01.1: reg 0x24: [io  0x5040-0x507f]
[    0.091564] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.091637] pci 0000:00:02.0: [10de:00e7] type 00 class 0x0c0310
[    0.091647] pci 0000:00:02.0: reg 0x10: [mem 0xff6ff000-0xff6fffff]
[    0.091677] pci 0000:00:02.0: supports D1 D2
[    0.091680] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.091713] pci 0000:00:02.0: System wakeup disabled by ACPI
[    0.091756] pci 0000:00:02.1: [10de:00e7] type 00 class 0x0c0310
[    0.091766] pci 0000:00:02.1: reg 0x10: [mem 0xff6fe000-0xff6fefff]
[    0.091796] pci 0000:00:02.1: supports D1 D2
[    0.091799] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.091830] pci 0000:00:02.1: System wakeup disabled by ACPI
[    0.091870] pci 0000:00:02.2: [10de:00e8] type 00 class 0x0c0320
[    0.091881] pci 0000:00:02.2: reg 0x10: [mem 0xff6fdc00-0xff6fdcff]
[    0.091917] pci 0000:00:02.2: supports D1 D2
[    0.091920] pci 0000:00:02.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.091974] pci 0000:00:02.2: System wakeup disabled by ACPI
[    0.092035] pci 0000:00:05.0: [10de:00df] type 00 class 0x068000
[    0.092045] pci 0000:00:05.0: reg 0x10: [mem 0xff6fc000-0xff6fcfff]
[    0.092051] pci 0000:00:05.0: reg 0x14: [io  0xec00-0xec07]
[    0.092079] pci 0000:00:05.0: supports D1 D2
[    0.092082] pci 0000:00:05.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.092113] pci 0000:00:05.0: System wakeup disabled by ACPI
[    0.092157] pci 0000:00:06.0: [10de:00ea] type 00 class 0x040100
[    0.092166] pci 0000:00:06.0: reg 0x10: [io  0xe800-0xe8ff]
[    0.092172] pci 0000:00:06.0: reg 0x14: [io  0xe480-0xe4ff]
[    0.092179] pci 0000:00:06.0: reg 0x18: [mem 0xff6fb000-0xff6fbfff]
[    0.092203] pci 0000:00:06.0: supports D1 D2
[    0.092232] pci 0000:00:06.0: System wakeup disabled by ACPI
[    0.092273] pci 0000:00:08.0: [10de:00e5] type 00 class 0x01018a
[    0.092293] pci 0000:00:08.0: reg 0x20: [io  0xffa0-0xffaf]
[    0.092374] pci 0000:00:0a.0: [10de:00e3] type 00 class 0x010185
[    0.092383] pci 0000:00:0a.0: reg 0x10: [io  0x0f80-0x0f87]
[    0.092389] pci 0000:00:0a.0: reg 0x14: [io  0x0f00-0x0f03]
[    0.092395] pci 0000:00:0a.0: reg 0x18: [io  0x0e80-0x0e87]
[    0.092401] pci 0000:00:0a.0: reg 0x1c: [io  0x0e00-0x0e03]
[    0.092407] pci 0000:00:0a.0: reg 0x20: [io  0xd800-0xd80f]
[    0.092413] pci 0000:00:0a.0: reg 0x24: [io  0xd400-0xd47f]
[    0.092488] pci 0000:00:0b.0: [10de:00e2] type 01 class 0x060400
[    0.092567] pci 0000:00:0e.0: [10de:00ed] type 01 class 0x060400
[    0.092608] pci 0000:00:0e.0: System wakeup disabled by ACPI
[    0.092659] pci 0000:00:18.0: [1022:1100] type 00 class 0x060000
[    0.092729] pci 0000:00:18.1: [1022:1101] type 00 class 0x060000
[    0.092796] pci 0000:00:18.2: [1022:1102] type 00 class 0x060000
[    0.092860] pci 0000:00:18.3: [1022:1103] type 00 class 0x060000
[    0.092967] pci 0000:01:00.0: [1002:4153] type 00 class 0x030000
[    0.092984] pci 0000:01:00.0: reg 0x10: [mem 0xe0000000-0xefffffff pref]
[    0.092993] pci 0000:01:00.0: reg 0x14: [io  0xc000-0xc0ff]
[    0.093002] pci 0000:01:00.0: reg 0x18: [mem 0xff5f0000-0xff5fffff]
[    0.093029] pci 0000:01:00.0: reg 0x30: [mem 0xff5c0000-0xff5dffff pref]
[    0.093059] pci 0000:01:00.0: supports D1 D2
[    0.093107] pci 0000:01:00.1: [1002:4173] type 00 class 0x038000
[    0.093121] pci 0000:01:00.1: reg 0x10: [mem 0xd0000000-0xdfffffff pref]
[    0.093131] pci 0000:01:00.1: reg 0x14: [mem 0xff5e0000-0xff5effff]
[    0.093181] pci 0000:01:00.1: supports D1 D2
[    0.093248] pci 0000:00:0b.0: PCI bridge to [bus 01]
[    0.093252] pci 0000:00:0b.0:   bridge window [io  0xa000-0xcfff]
[    0.093257] pci 0000:00:0b.0:   bridge window [mem 0xff500000-0xff5fffff]
[    0.093262] pci 0000:00:0b.0:   bridge window [mem 0xb6b00000-0xf6afffff pref]
[    0.093315] pci 0000:00:0e.0: PCI bridge to [bus 02]
[    0.093326] pci_bus 0000:00: on NUMA node 0
[    0.094227] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *0, disabled.
[    0.094325] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *0, disabled.
[    0.094420] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *0, disabled.
[    0.094519] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *11
[    0.094613] ACPI: PCI Interrupt Link [LNKE] (IRQs 16 17 18 19) *11
[    0.094713] ACPI: PCI Interrupt Link [LUS0] (IRQs 20 21 22) *9
[    0.094804] ACPI: PCI Interrupt Link [LUS1] (IRQs 20 21 22) *5
[    0.094898] ACPI: PCI Interrupt Link [LUS2] (IRQs 20 21 22) *3
[    0.094992] ACPI: PCI Interrupt Link [LKLN] (IRQs 20 21 22) *9
[    0.095082] ACPI: PCI Interrupt Link [LAUI] (IRQs 20 21 22) *9
[    0.095173] ACPI: PCI Interrupt Link [LKMO] (IRQs 20 21 22) *0, disabled.
[    0.095264] ACPI: PCI Interrupt Link [LKSM] (IRQs 20 21 22) *0, disabled.
[    0.095355] ACPI: PCI Interrupt Link [LTID] (IRQs 20 21 22) *10
[    0.095453] ACPI: PCI Interrupt Link [LTIE] (IRQs 20 21 22) *0, disabled.
[    0.095563] ACPI: PCI Interrupt Link [LATA] (IRQs 22) *14
[    0.095649] ACPI: \_SB_.PCI0: notify handler is installed
[    0.095683] Found 1 acpi root devices
[    0.095881] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.095884] vgaarb: loaded
[    0.095886] vgaarb: bridge control possible 0000:01:00.0
[    0.096250] SCSI subsystem initialized
[    0.096330] libata version 3.00 loaded.
[    0.096368] ACPI: bus type USB registered
[    0.096403] usbcore: registered new interface driver usbfs
[    0.096417] usbcore: registered new interface driver hub
[    0.096446] usbcore: registered new device driver usb
[    0.096608] PCI: Using ACPI for IRQ routing
[    0.096612] PCI: pci_cache_line_size set to 64 bytes
[    0.096653] e820: reserve RAM buffer [mem 0x0009fc00-0x0009ffff]
[    0.096660] e820: reserve RAM buffer [mem 0x7ffb0000-0x7fffffff]
[    0.096820] NetLabel: Initializing
[    0.096822] NetLabel:  domain hash size = 128
[    0.096823] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.096841] NetLabel:  unlabeled traffic allowed by default
[    0.097006] Switched to clocksource refined-jiffies
[    0.105214] AppArmor: AppArmor Filesystem Enabled
[    0.105274] pnp: PnP ACPI init
[    0.105297] ACPI: bus type PNP registered
[    0.105445] pnp 00:00: [dma 4]
[    0.105481] pnp 00:00: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.105535] pnp 00:01: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.105569] pnp 00:02: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.105605] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.106136] pnp 00:04: [dma 3]
[    0.106270] pnp 00:04: Plug and Play ACPI device, IDs PNP0401 (active)
[    0.106477] pnp 00:05: Plug and Play ACPI device, IDs PNPb02f (active)
[    0.106726] system 00:06: [io  0x04d0-0x04d1] has been reserved
[    0.106731] system 00:06: [io  0x4000-0x407f] could not be reserved
[    0.106734] system 00:06: [io  0x4080-0x40ff] has been reserved
[    0.106739] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.106826] system 00:07: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.106830] system 00:07: [mem 0xfee00000-0xfeefffff] has been reserved
[    0.106834] system 00:07: [mem 0xff7c0000-0xffffffff] has been reserved
[    0.106838] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.106902] pnp 00:08: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.106982] pnp 00:09: Plug and Play ACPI device, IDs PNP0f03 PNP0f13 (active)
[    0.107204] pnp 00:0a: [dma 0 disabled]
[    0.107278] pnp 00:0a: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.107380] system 00:0b: [io  0x0290-0x029f] has been reserved
[    0.107385] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.107576] system 00:0c: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.107580] system 00:0c: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.107584] system 00:0c: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.107588] system 00:0c: [mem 0x00100000-0x7fffffff] could not be reserved
[    0.107592] system 00:0c: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.107846] pnp: PnP ACPI: found 13 devices
[    0.107848] ACPI: bus type PNP unregistered
[    0.107852] PnPBIOS: Disabled by ACPI PNP
[    0.144343] Switched to clocksource acpi_pm
[    0.144379] pci 0000:00:0b.0: PCI bridge to [bus 01]
[    0.144385] pci 0000:00:0b.0:   bridge window [io  0xa000-0xcfff]
[    0.144392] pci 0000:00:0b.0:   bridge window [mem 0xff500000-0xff5fffff]
[    0.144396] pci 0000:00:0b.0:   bridge window [mem 0xb6b00000-0xf6afffff pref]
[    0.144403] pci 0000:00:0e.0: PCI bridge to [bus 02]
[    0.144411] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
[    0.144414] pci_bus 0000:00: resource 5 [mem 0x000a0000-0x000bffff]
[    0.144417] pci_bus 0000:00: resource 6 [mem 0x80000000-0xfcffffffff]
[    0.144421] pci_bus 0000:01: resource 0 [io  0xa000-0xcfff]
[    0.144424] pci_bus 0000:01: resource 1 [mem 0xff500000-0xff5fffff]
[    0.144427] pci_bus 0000:01: resource 2 [mem 0xb6b00000-0xf6afffff pref]
[    0.144486] NET: Registered protocol family 2
[    0.144746] TCP established hash table entries: 8192 (order: 3, 32768 bytes)
[    0.144776] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.144828] TCP: Hash tables configured (established 8192 bind 8192)
[    0.144890] TCP: reno registered
[    0.144893] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.144907] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.145004] NET: Registered protocol family 1
[    0.145271] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 22
[    0.216211] ACPI: PCI Interrupt Link [LUS1] enabled at IRQ 21
[    0.288203] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 20
[    0.288287] pci 0000:01:00.0: Boot video device
[    0.288293] PCI: CLS 64 bytes, default 64
[    0.288382] Trying to unpack rootfs image as initramfs...
[    0.818144] Freeing initrd memory: 18280K (f5c3c000 - f6e16000)
[    0.818370] microcode: AMD CPU family 0xf not supported
[    0.818373] Scanning for low memory corruption every 60 seconds
[    0.818741] Initialise system trusted keyring
[    0.818805] audit: initializing netlink socket (disabled)
[    0.818822] type=2000 audit(1423959559.815:1): initialized
[    0.850342] bounce pool size: 64 pages
[    0.850362] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.852198] zbud: loaded
[    0.852312] VFS: Disk quotas dquot_6.5.2
[    0.852386] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.853028] fuse init (API version 7.22)
[    0.853139] msgmni has been set to 1718
[    0.853221] Key type big_key registered
[    0.853559] Key type asymmetric registered
[    0.853561] Asymmetric key parser 'x509' registered
[    0.853616] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.853652] io scheduler noop registered
[    0.853654] io scheduler deadline registered (default)
[    0.853691] io scheduler cfq registered
[    0.853867] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.853892] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.853975] ipmi message handler version 39.2
[    0.854081] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.854088] ACPI: Power Button [PWRB]
[    0.854140] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.854144] ACPI: Power Button [PWRF]
[    0.854274] GHES: HEST is not enabled!
[    0.854447] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.874858] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
[    0.874923] isapnp: Scanning for PnP cards...
[    0.969131] Linux agpgart interface v0.103
[    0.969166] agpgart-amd64 0000:00:00.0: AGP bridge [10de/00e1]
[    0.969174] agpgart-amd64 0000:00:00.0: aperture size 4096 MB is not right, using settings from NB
[    0.969180] agpgart-amd64 0000:00:00.0: setting up Nforce3 AGP
[    0.969186] agpgart-amd64 0000:00:00.0: aperture base > 4G
[    0.969211] agpgart-amd64 0000:00:00.0: AGP bridge [10de/00e1]
[    0.969218] agpgart-amd64 0000:00:00.0: aperture size 4096 MB is not right, using settings from NB
[    0.969221] agpgart-amd64 0000:00:00.0: setting up Nforce3 AGP
[    0.969224] agpgart-amd64 0000:00:00.0: aperture base > 4G
[    0.969313] agpgart-amd64 0000:01:00.0: AGP bridge [1002/4153]
[    0.969320] agpgart-amd64 0000:01:00.0: aperture size 4096 MB is not right, using settings from NB
[    0.971682] agpgart-amd64 0000:01:00.0: AGP aperture is 64M @ 0xf8000000
[    0.973487] brd: module loaded
[    0.974406] loop: module loaded
[    0.975129] libphy: Fixed MDIO Bus: probed
[    0.975302] tun: Universal TUN/TAP device driver, 1.6
[    0.975304] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.975372] PPP generic driver version 2.4.2
[    0.975426] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.975433] ehci-pci: EHCI PCI platform driver
[    0.975573] ehci-pci 0000:00:02.2: EHCI Host Controller
[    0.975582] ehci-pci 0000:00:02.2: new USB bus registered, assigned bus number 1
[    0.975593] ehci-pci 0000:00:02.2: debug port 0
[    0.975631] ehci-pci 0000:00:02.2: cache line size of 64 is not supported
[    0.975658] ehci-pci 0000:00:02.2: irq 20, io mem 0xff6fdc00
[    1.019216] ehci-pci 0000:00:02.2: USB 2.0 started, EHCI 1.00
[    1.019278] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.019281] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.019284] usb usb1: Product: EHCI Host Controller
[    1.019287] usb usb1: Manufacturer: Linux 3.13.0-32-generic ehci_hcd
[    1.019290] usb usb1: SerialNumber: 0000:00:02.2
[    1.019438] hub 1-0:1.0: USB hub found
[    1.019448] hub 1-0:1.0: 8 ports detected
[    1.019669] ehci-platform: EHCI generic platform driver
[    1.019686] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.019688] ohci-pci: OHCI PCI platform driver
[    1.019791] ohci-pci 0000:00:02.0: OHCI PCI host controller
[    1.019802] ohci-pci 0000:00:02.0: new USB bus registered, assigned bus number 2
[    1.019837] ohci-pci 0000:00:02.0: irq 22, io mem 0xff6ff000
[    1.108926] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    1.108930] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.108933] usb usb2: Product: OHCI PCI host controller
[    1.108936] usb usb2: Manufacturer: Linux 3.13.0-32-generic ohci_hcd
[    1.108939] usb usb2: SerialNumber: 0000:00:02.0
[    1.109075] hub 2-0:1.0: USB hub found
[    1.109085] hub 2-0:1.0: 4 ports detected
[    1.109285] ohci-pci 0000:00:02.1: OHCI PCI host controller
[    1.109292] ohci-pci 0000:00:02.1: new USB bus registered, assigned bus number 3
[    1.109327] ohci-pci 0000:00:02.1: irq 21, io mem 0xff6fe000
[    1.241745] isapnp: No Plug & Play device found
[    1.241880] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    1.241884] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.241887] usb usb3: Product: OHCI PCI host controller
[    1.241890] usb usb3: Manufacturer: Linux 3.13.0-32-generic ohci_hcd
[    1.241892] usb usb3: SerialNumber: 0000:00:02.1
[    1.242032] hub 3-0:1.0: USB hub found
[    1.242041] hub 3-0:1.0: 4 ports detected
[    1.242183] ohci-platform: OHCI generic platform driver
[    1.242201] uhci_hcd: USB Universal Host Controller Interface driver
[    1.242313] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.245566] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.245575] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.245728] mousedev: PS/2 mouse device common for all mice
[    1.245880] rtc_cmos 00:01: RTC can wake from S4
[    1.246010] rtc_cmos 00:01: rtc core: registered rtc_cmos as rtc0
[    1.246036] rtc_cmos 00:01: alarms up to one year, y3k, 114 bytes nvram
[    1.246147] device-mapper: uevent: version 1.0.3
[    1.246218] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
[    1.246252] platform eisa.0: Probing EISA bus 0
[    1.246256] platform eisa.0: EISA: Cannot allocate resource for mainboard
[    1.246260] platform eisa.0: Cannot allocate resource for EISA slot 1
[    1.246263] platform eisa.0: Cannot allocate resource for EISA slot 2
[    1.246267] platform eisa.0: Cannot allocate resource for EISA slot 3
[    1.246270] platform eisa.0: Cannot allocate resource for EISA slot 4
[    1.246274] platform eisa.0: Cannot allocate resource for EISA slot 5
[    1.246277] platform eisa.0: Cannot allocate resource for EISA slot 6
[    1.246280] platform eisa.0: Cannot allocate resource for EISA slot 7
[    1.246284] platform eisa.0: Cannot allocate resource for EISA slot 8
[    1.246287] platform eisa.0: EISA: Detected 0 cards
[    1.246297] cpufreq-nforce2: No nForce2 chipset.
[    1.246302] ledtrig-cpu: registered to indicate activity on CPUs
[    1.246485] TCP: cubic registered
[    1.246621] NET: Registered protocol family 10
[    1.246884] NET: Registered protocol family 17
[    1.246900] Key type dns_resolver registered
[    1.247093] Using IPI No-Shortcut mode
[    1.247187] Loading compiled-in X.509 certificates
[    1.251977] Loaded X.509 cert 'Magrathea: Glacier signing key: a7fc6590fc4a8d859aaebda2ca5dd04716244fa0'
[    1.251995] registered taskstats version 1
[    1.255275] Key type trusted registered
[    1.258290] Key type encrypted registered
[    1.261316] AppArmor: AppArmor sha1 policy hashing enabled
[    1.261337] IMA: No TPM chip found, activating TPM-bypass!
[    1.261535] regulator-dummy: disabling
[    1.261602]   Magic number: 3:369:304
[    1.261656] tty tty33: hash matches
[    1.261733] rtc_cmos 00:01: setting system clock to 2015-02-15 00:19:20 UTC (1423959560)
[    1.261889] powernow-k8: fid 0xa (1800 MHz), vid 0x6
[    1.261891] powernow-k8: fid 0x2 (1000 MHz), vid 0x12
[    1.261925] powernow-k8: Found 1 AMD Sempron(tm) Processor 3100+ (1 cpu cores) (version 2.20.00)
[    1.261932] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.261934] EDD information not available.
[    1.261966] PM: Hibernation image not present or could not be loaded.
[    1.262979] Freeing unused kernel memory: 872K (c19b4000 - c1a8e000)
[    1.263028] Write protecting the kernel text: 6532k
[    1.263110] Write protecting the kernel read-only data: 2764k
[    1.263112] NX-protecting the kernel data: 5756k
[    1.271392] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    1.288295] systemd-udevd[88]: starting version 204
[    1.359571] pata_amd 0000:00:08.0: version 0.4.1
[    1.375623] scsi0 : pata_amd
[    1.378932] scsi1 : pata_amd
[    1.379021] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    1.379025] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    1.379229] sata_nv 0000:00:0a.0: version 3.5
[    1.379480] ACPI: PCI Interrupt Link [LTID] enabled at IRQ 22
[    1.387306] scsi2 : sata_nv
[    1.390624] scsi3 : sata_nv
[    1.390712] ata3: SATA max UDMA/133 cmd 0xf80 ctl 0xf00 bmdma 0xd800 irq 22
[    1.390716] ata4: SATA max UDMA/133 cmd 0xe80 ctl 0xe00 bmdma 0xd808 irq 22
[    1.390816] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.391046] ACPI: PCI Interrupt Link [LKLN] enabled at IRQ 21
[    1.708263] ata3: SATA link down (SStatus 0 SControl 300)
[    1.757692] ata1.00: HPA detected: current 156299375, native 156301488
[    1.757699] ata1.00: ATA-7: ST380215A, 3.AAC, max UDMA/100
[    1.757702] ata1.00: 156299375 sectors, multi 16: LBA48 
[    1.757710] ata1.01: ATAPI: SONY    CD-RW  CRX175A1, 5YS2, max UDMA/33
[    1.757720] ata1: nv_mode_filter: 0x3f39f&0x3f39f->0x3f39f, BIOS=0x3f000 (0xc6c0c5c6) ACPI=0x3f01f (20:60:0x1f)
[    1.757725] ata1: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc6c0c5c6) ACPI=0x701f (20:60:0x1f)
[    1.790719] input: GenPS/2 Genius Mouse as /devices/platform/i8042/serio1/input/input4
[    1.824116] ata1.00: configured for UDMA/100
[    1.840188] ata1.01: configured for UDMA/33
[    1.840914] scsi 0:0:0:0: Direct-Access     ATA      ST380215A        3.AA PQ: 0 ANSI: 5
[    1.841305] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.841754] scsi 0:0:1:0: CD-ROM            SONY     CD-RW  CRX175A1  5YS2 PQ: 0 ANSI: 5
[    1.842465] sd 0:0:0:0: [sda] 156299375 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    1.842731] sr0: scsi3-mmc drive: 173x/40x writer cd/rw xa/form2 cdda tray
[    1.842735] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.843240] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    1.843415] sr 0:0:1:0: Attached scsi generic sg1 type 5
[    1.843992] sd 0:0:0:0: [sda] Write Protect is off
[    1.843999] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.844103] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.912726] forcedeth 0000:00:05.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:13:8f:e7:a2:b6
[    1.912733] forcedeth 0000:00:05.0: csum timirq lnktim desc-v2
[    1.915303]  sda: sda1 sda2 < sda5 sda6 > sda3 sda4
[    1.915891] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.012301] ata2.00: ATAPI: PIONEER DVD-RW  DVR-109, 1.09, max UDMA/66
[    2.042882] ata2.01: HPA detected: current 390719855, native 390721968
[    2.042887] ata2.01: ATA-7: ST3200827A, 3.AAD, max UDMA/100
[    2.042890] ata2.01: 390719855 sectors, multi 16: LBA48 
[    2.042899] ata2: nv_mode_filter: 0x1f39f&0x1f39f->0x1f39f, BIOS=0x1f000 (0xc6c0c5c6) ACPI=0x1f01f (30:20:0x1f)
[    2.042904] ata2: nv_mode_filter: 0x3f39f&0x3f39f->0x3f39f, BIOS=0x3f000 (0xc6c0c5c6) ACPI=0x3f01f (30:20:0x1f)
[    2.056232] ata2.00: configured for UDMA/66
[    2.117801] ata2.01: configured for UDMA/100
[    2.131235] scsi 1:0:0:0: CD-ROM            PIONEER  DVD-RW  DVR-109  1.09 PQ: 0 ANSI: 5
[    2.142442] sr1: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[    2.142606] sr 1:0:0:0: Attached scsi CD-ROM sr1
[    2.142678] sr 1:0:0:0: Attached scsi generic sg2 type 5
[    2.142839] scsi 1:0:1:0: Direct-Access     ATA      ST3200827A       3.AA PQ: 0 ANSI: 5
[    2.143077] sd 1:0:1:0: Attached scsi generic sg3 type 0
[    2.143571] sd 1:0:1:0: [sdb] 390719855 512-byte logical blocks: (200 GB/186 GiB)
[    2.143645] sd 1:0:1:0: [sdb] Write Protect is off
[    2.143649] sd 1:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    2.143680] sd 1:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.166411]  sdb: sdb1
[    2.166745] sd 1:0:1:0: [sdb] Attached SCSI disk
[    2.452031] ata4: SATA link down (SStatus 0 SControl 300)
[    2.521055] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[    2.521062] ata2.01: BMDMA stat 0x65
[    2.521067] ata2.01: failed command: READ DMA
[    2.521075] ata2.01: cmd c8/00:08:00:00:00/00:00:00:00:00/f0 tag 23 dma 4096 in
[    2.521075]          res d0/d0:d0:d0:d0:d0/00:00:00:00:00/d0 Emask 0x2 (HSM violation)
[    2.521079] ata2.01: status: { Busy }
[    2.521081] ata2.01: error: { ICRC UNC IDNF }
[    2.576031] ata2: soft resetting link
[    2.780307] ata2: nv_mode_filter: 0x1f39f&0x1f39f->0x1f39f, BIOS=0x1f000 (0xc6c0c5c6) ACPI=0x1f01f (30:20:0x1f)
[    2.780317] ata2: nv_mode_filter: 0x3f39f&0x3f39f->0x3f39f, BIOS=0x3f000 (0xc6c0c5c6) ACPI=0x3f01f (30:20:0x1f)
[    2.796230] ata2.00: configured for UDMA/66
[    2.842097] ata2.01: configured for UDMA/100
[    2.842408] ata2: EH complete
[    3.196205] random: nonblocking pool is initialized
[    5.657184] EXT4-fs (sda6): INFO: recovery required on readonly filesystem
[    5.657191] EXT4-fs (sda6): write access will be enabled during recovery
[    5.737802] EXT4-fs (sda6): recovery complete
[    5.745479] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   17.993467] Adding 1535996k swap on /dev/sda4.  Priority:-1 extents:1 across:1535996k FS
[   18.235529] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.518683] systemd-udevd[263]: starting version 204
[   18.780877] lp: driver loaded but no devices found
[   18.813695] ppdev: user-space parallel port driver
[   18.830984] parport_pc 00:04: reported by Plug and Play ACPI
[   18.831087] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   18.867556] i2c i2c-0: nForce2 SMBus adapter at 0x5000
[   18.871075] i2c i2c-1: nForce2 SMBus adapter at 0x5040
[   18.894179] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[   18.928302] lp0: using parport0 (interrupt-driven).
[   19.151297] gameport gameport0: NS558 PnP Gameport is pnp00:05/gameport0, io 0x200, speed 890kHz
[   19.337928] type=1400 audit(1423955978.573:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=343 comm="apparmor_parser"
[   19.337943] type=1400 audit(1423955978.573:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=343 comm="apparmor_parser"
[   19.337950] type=1400 audit(1423955978.573:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=343 comm="apparmor_parser"
[   19.338706] type=1400 audit(1423955978.573:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=343 comm="apparmor_parser"
[   19.338715] type=1400 audit(1423955978.573:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=343 comm="apparmor_parser"
[   19.339093] type=1400 audit(1423955978.573:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=343 comm="apparmor_parser"
[   19.593477] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   20.551252] Bluetooth: Core ver 2.17
[   20.551891] NET: Registered protocol family 31
[   20.551898] Bluetooth: HCI device and connection manager initialized
[   20.551912] Bluetooth: HCI socket layer initialized
[   20.551916] Bluetooth: L2CAP socket layer initialized
[   20.551930] Bluetooth: SCO socket layer initialized
[   20.596174] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   20.596182] Bluetooth: BNEP filters: protocol multicast
[   20.596196] Bluetooth: BNEP socket layer initialized
[   20.661473] type=1400 audit(1423955979.897:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=488 comm="apparmor_parser"
[   20.661487] type=1400 audit(1423955979.897:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=488 comm="apparmor_parser"
[   20.662258] type=1400 audit(1423955979.897:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=488 comm="apparmor_parser"
[   20.683978] Bluetooth: RFCOMM TTY layer initialized
[   20.684063] Bluetooth: RFCOMM socket layer initialized
[   20.684244] Bluetooth: RFCOMM ver 1.11
[   21.057775] init: cups main process (492) killed by HUP signal
[   21.057797] init: cups main process ended, respawning
[   21.775099] ACPI: PCI Interrupt Link [LAUI] enabled at IRQ 20
[   21.988605] init: failsafe main process (537) killed by TERM signal
[   22.128144] intel8x0_measure_ac97_clock: measured 52802 usecs (2592 samples)
[   22.128152] intel8x0: clocking to 46935
[   22.668598] type=1400 audit(1423955981.905:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=683 comm="apparmor_parser"
[   23.077186] init: udev-fallback-graphics main process (739) terminated with status 1
[   25.629880] audit_printk_skb: 102 callbacks suppressed
[   25.629888] type=1400 audit(1423955984.865:46): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cups-browsed" pid=1039 comm="apparmor_parser"
[   27.434770] init: lightdm main process (929) terminated with status 1
[   27.442142] init: plymouth-upstart-bridge main process ended, respawning
[   27.465582] init: plymouth-ready (startup) main process (150) terminated with status 1
[   27.468696] init: plymouth-upstart-bridge main process (1144) terminated with status 1
[   27.468722] init: plymouth-upstart-bridge main process ended, respawning
[   50.846517] type=1400 audit(1423956010.078:47): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=1273 comm="apparmor_parser"
[   50.846534] type=1400 audit(1423956010.078:48): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1273 comm="apparmor_parser"
[   50.847274] type=1400 audit(1423956010.078:49): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1273 comm="apparmor_parser"

```

---

### Post by Yellow Pasque on 2015-02-15
There's not a lot of clues to go on. I will note that your kernel is outdated (3.13.0-32 as opposed to 3.13.0-45).

---

### Post by venneri2 on 2015-02-15
Kernel is outdated because is a clean install. After updated problem remains the same: black screen with blinking cursor.

I attach dmesg and Xorg.0.log after updated, althougth I think that there is not too much difference.


Xorg.0.log
```

[    37.883] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[    37.884] X Protocol Version 11, Revision 0
[    37.884] Build Operating System: Linux 3.2.0-70-generic i686 Ubuntu
[    37.884] Current Operating System: Linux ubuntu-PC 3.13.0-45-generic #74-Ubuntu SMP Tue Jan 13 19:37:48 UTC 2015 i686
[    37.884] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-45-generic root=UUID=e01f1e08-28ba-4214-82b0-6a811691777f ro
[    37.884] Build Date: 10 December 2014  06:16:10PM
[    37.884] xorg-server 2:1.15.1-0ubuntu2.6 (For technical support please see http://www.ubuntu.com/support) 
[    37.884] Current version of pixman: 0.30.2
[    37.884]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    37.884] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    37.884] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Feb 15 21:16:48 2015
[    37.927] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    38.015] (==) No Layout section.  Using the first Screen section.
[    38.015] (==) No screen section available. Using defaults.
[    38.015] (**) |-->Screen "Default Screen Section" (0)
[    38.015] (**) |   |-->Monitor "<default monitor>"
[    38.026] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    38.027] (==) Automatically adding devices
[    38.027] (==) Automatically enabling devices
[    38.027] (==) Automatically adding GPU devices
[    38.111] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    38.111]     Entry deleted from font path.
[    38.111] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    38.111]     Entry deleted from font path.
[    38.111] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    38.111]     Entry deleted from font path.
[    38.121] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    38.121]     Entry deleted from font path.
[    38.121] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    38.121]     Entry deleted from font path.
[    38.121] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    38.121] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    38.121] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    38.121] (II) Loader magic: 0xb77956c0
[    38.121] (II) Module ABI versions:
[    38.121]     X.Org ANSI C Emulation: 0.4
[    38.121]     X.Org Video Driver: 15.0
[    38.121]     X.Org XInput driver : 20.0
[    38.121]     X.Org Server Extension : 8.0
[    38.122] (--) PCI:*(0:1:0:0) 1002:4153:1fd3:4153 rev 0, Mem @ 0xe0000000/268435456, 0xff5f0000/65536, I/O @ 0x0000c000/256, BIOS @ 0x????????/131072
[    38.122] (--) PCI: (0:1:0:1) 1002:4173:1fd3:4152 rev 0, Mem @ 0xd0000000/268435456, 0xff5e0000/65536
[    38.139] Initializing built-in extension Generic Event Extension
[    38.139] Initializing built-in extension SHAPE
[    38.139] Initializing built-in extension MIT-SHM
[    38.139] Initializing built-in extension XInputExtension
[    38.139] Initializing built-in extension XTEST
[    38.139] Initializing built-in extension BIG-REQUESTS
[    38.139] Initializing built-in extension SYNC
[    38.139] Initializing built-in extension XKEYBOARD
[    38.139] Initializing built-in extension XC-MISC
[    38.139] Initializing built-in extension SECURITY
[    38.139] Initializing built-in extension XINERAMA
[    38.139] Initializing built-in extension XFIXES
[    38.139] Initializing built-in extension RENDER
[    38.139] Initializing built-in extension RANDR
[    38.139] Initializing built-in extension COMPOSITE
[    38.139] Initializing built-in extension DAMAGE
[    38.139] Initializing built-in extension MIT-SCREEN-SAVER
[    38.139] Initializing built-in extension DOUBLE-BUFFER
[    38.139] Initializing built-in extension RECORD
[    38.139] Initializing built-in extension DPMS
[    38.139] Initializing built-in extension Present
[    38.139] Initializing built-in extension DRI3
[    38.139] Initializing built-in extension X-Resource
[    38.139] Initializing built-in extension XVideo
[    38.139] Initializing built-in extension XVideo-MotionCompensation
[    38.139] Initializing built-in extension SELinux
[    38.139] Initializing built-in extension XFree86-VidModeExtension
[    38.139] Initializing built-in extension XFree86-DGA
[    38.139] Initializing built-in extension XFree86-DRI
[    38.139] Initializing built-in extension DRI2
[    38.139] (II) LoadModule: "glx"
[    38.178] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    38.455] (II) Module glx: vendor="X.Org Foundation"
[    38.455]     compiled for 1.15.1, module version = 1.0.0
[    38.455]     ABI class: X.Org Server Extension, version 8.0
[    38.456] (==) AIGLX enabled
[    38.456] Loading extension GLX
[    38.456] (==) Matched fglrx as autoconfigured driver 0
[    38.456] (==) Matched ati as autoconfigured driver 1
[    38.456] (==) Matched modesetting as autoconfigured driver 2
[    38.456] (==) Matched fbdev as autoconfigured driver 3
[    38.456] (==) Matched vesa as autoconfigured driver 4
[    38.456] (==) Assigned the driver to the xf86ConfigLayout
[    38.456] (II) LoadModule: "fglrx"
[    38.486] (WW) Warning, couldn't open module fglrx
[    38.487] (II) UnloadModule: "fglrx"
[    38.487] (II) Unloading fglrx
[    38.487] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    38.487] (II) LoadModule: "ati"
[    38.487] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    38.493] (II) Module ati: vendor="X.Org Foundation"
[    38.493]     compiled for 1.15.1, module version = 7.3.0
[    38.493]     Module class: X.Org Video Driver
[    38.493]     ABI class: X.Org Video Driver, version 15.0
[    38.493] (II) LoadModule: "radeon"
[    38.493] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    38.540] (II) Module radeon: vendor="X.Org Foundation"
[    38.540]     compiled for 1.15.1, module version = 7.3.0
[    38.540]     Module class: X.Org Video Driver
[    38.540]     ABI class: X.Org Video Driver, version 15.0
[    38.540] (II) LoadModule: "modesetting"
[    38.540] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    38.550] (II) Module modesetting: vendor="X.Org Foundation"
[    38.550]     compiled for 1.15.0, module version = 0.8.1
[    38.550]     Module class: X.Org Video Driver
[    38.550]     ABI class: X.Org Video Driver, version 15.0
[    38.550] (II) LoadModule: "fbdev"
[    38.551] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    38.551] (II) Module fbdev: vendor="X.Org Foundation"
[    38.551]     compiled for 1.15.0, module version = 0.4.4
[    38.551]     Module class: X.Org Video Driver
[    38.551]     ABI class: X.Org Video Driver, version 15.0
[    38.551] (II) LoadModule: "vesa"
[    38.552] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    38.552] (II) Module vesa: vendor="X.Org Foundation"
[    38.553]     compiled for 1.15.0, module version = 2.3.3
[    38.553]     Module class: X.Org Video Driver
[    38.553]     ABI class: X.Org Video Driver, version 15.0
[    38.553] (==) Matched fglrx as autoconfigured driver 0
[    38.553] (==) Matched ati as autoconfigured driver 1
[    38.553] (==) Matched modesetting as autoconfigured driver 2
[    38.553] (==) Matched fbdev as autoconfigured driver 3
[    38.553] (==) Matched vesa as autoconfigured driver 4
[    38.553] (==) Assigned the driver to the xf86ConfigLayout
[    38.553] (II) LoadModule: "fglrx"
[    38.553] (WW) Warning, couldn't open module fglrx
[    38.553] (II) UnloadModule: "fglrx"
[    38.553] (II) Unloading fglrx
[    38.553] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    38.553] (II) LoadModule: "ati"
[    38.554] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    38.554] (II) Module ati: vendor="X.Org Foundation"
[    38.554]     compiled for 1.15.1, module version = 7.3.0
[    38.554]     Module class: X.Org Video Driver
[    38.554]     ABI class: X.Org Video Driver, version 15.0
[    38.554] (II) LoadModule: "modesetting"
[    38.554] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    38.554] (II) Module modesetting: vendor="X.Org Foundation"
[    38.554]     compiled for 1.15.0, module version = 0.8.1
[    38.554]     Module class: X.Org Video Driver
[    38.554]     ABI class: X.Org Video Driver, version 15.0
[    38.554] (II) UnloadModule: "modesetting"
[    38.554] (II) Unloading modesetting
[    38.554] (II) Failed to load module "modesetting" (already loaded, 0)
[    38.554] (II) LoadModule: "fbdev"
[    38.554] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    38.554] (II) Module fbdev: vendor="X.Org Foundation"
[    38.554]     compiled for 1.15.0, module version = 0.4.4
[    38.554]     Module class: X.Org Video Driver
[    38.554]     ABI class: X.Org Video Driver, version 15.0
[    38.554] (II) UnloadModule: "fbdev"
[    38.554] (II) Unloading fbdev
[    38.555] (II) Failed to load module "fbdev" (already loaded, 0)
[    38.555] (II) LoadModule: "vesa"
[    38.555] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    38.555] (II) Module vesa: vendor="X.Org Foundation"
[    38.555]     compiled for 1.15.0, module version = 2.3.3
[    38.555]     Module class: X.Org Video Driver
[    38.555]     ABI class: X.Org Video Driver, version 15.0
[    38.555] (II) UnloadModule: "vesa"
[    38.555] (II) Unloading vesa
[    38.555] (II) Failed to load module "vesa" (already loaded, 0)
[    38.555] (II) RADEON: Driver for ATI Radeon chipsets:
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
    KABINI, KABINI, KABINI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
    KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
    KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
    HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII,
    HAWAII, HAWAII, HAWAII, HAWAII
[    38.564] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    38.564] (II) FBDEV: driver for framebuffer: fbdev
[    38.564] (II) VESA: driver for VESA chipsets: vesa
[    38.564] (++) using VT number 7

[    38.578] (II) [KMS] drm report modesetting isn't supported.
[    38.578] (EE) open /dev/dri/card0: No such file or directory
[    38.578] (EE) open /dev/dri/card0: No such file or directory
[    38.578] (WW) Falling back to old probe method for modesetting
[    38.578] (EE) open /dev/dri/card0: No such file or directory
[    38.578] (EE) open /dev/dri/card0: No such file or directory
[    38.578] (II) Loading sub module "fbdevhw"
[    38.578] (II) LoadModule: "fbdevhw"
[    38.578] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    38.587] (II) Module fbdevhw: vendor="X.Org Foundation"
[    38.587]     compiled for 1.15.1, module version = 0.0.2
[    38.587]     ABI class: X.Org Video Driver, version 15.0
[    38.587] (EE) open /dev/fb0: No such file or directory
[    38.587] (II) Loading sub module "fbdevhw"
[    38.587] (II) LoadModule: "fbdevhw"
[    38.587] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    38.588] (II) Module fbdevhw: vendor="X.Org Foundation"
[    38.588]     compiled for 1.15.1, module version = 0.0.2
[    38.588]     ABI class: X.Org Video Driver, version 15.0
[    38.588] (EE) open /dev/fb0: No such file or directory
[    38.588] (WW) Falling back to old probe method for fbdev
[    38.588] (II) Loading sub module "fbdevhw"
[    38.588] (II) LoadModule: "fbdevhw"
[    38.588] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    38.588] (II) Module fbdevhw: vendor="X.Org Foundation"
[    38.588]     compiled for 1.15.1, module version = 0.0.2
[    38.588]     ABI class: X.Org Video Driver, version 15.0
[    38.588] (EE) open /dev/fb0: No such file or directory
[    38.588] (EE) open /dev/fb0: No such file or directory
[    38.588] vesa: Ignoring device with a bound kernel driver
[    38.588] (WW) Falling back to old probe method for vesa
[    38.589] (EE) Screen 0 deleted because of no matching config section.
[    38.589] (II) UnloadModule: "radeon"
[    38.589] (EE) Screen 0 deleted because of no matching config section.
[    38.589] (II) UnloadModule: "modesetting"
[    38.589] (EE) Screen 0 deleted because of no matching config section.
[    38.589] (II) UnloadModule: "modesetting"
[    38.589] (EE) Screen 0 deleted because of no matching config section.
[    38.589] (II) UnloadModule: "fbdev"
[    38.589] (II) UnloadSubModule: "fbdevhw"
[    38.589] (EE) Screen 0 deleted because of no matching config section.
[    38.589] (II) UnloadModule: "fbdev"
[    38.589] (II) UnloadSubModule: "fbdevhw"
[    38.589] (II) UnloadSubModule: "fbdevhw"
[    38.589] (EE) Screen 0 deleted because of no matching config section.
[    38.589] (II) UnloadModule: "vesa"
[    38.589] (EE) Device(s) detected, but none match those in the config file.
[    38.589] (EE) 
Fatal server error:
[    38.589] (EE) no screens found(EE) 
[    38.589] (EE) 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[    38.589] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    38.589] (EE) 
[    38.589] (EE) Server terminated with error (1). Closing log file.



```

Dmesg
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.13.0-45-generic (buildd@kissel) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #74-Ubuntu SMP Tue Jan 13 19:37:48 UTC 2015 (Ubuntu 3.13.0-45.74-generic 3.13.11-ckt13)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009fbff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009fc00-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e8000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000007ffaffff] usable
[    0.000000] BIOS-e820: [mem 0x000000007ffb0000-0x000000007ffbffff] ACPI data
[    0.000000] BIOS-e820: [mem 0x000000007ffc0000-0x000000007ffeffff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000007fff0000-0x000000007fffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff7c0000-0x00000000ffffffff] reserved
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.3 present.
[    0.000000] DMI:          K8Upgrade-NF3/K8Upgrade-NF3, BIOS P2.10 08/07/2006
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0x7ffb0 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FF80000000 write-back
[    0.000000]   1 disabled
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] initial memory mapped: [mem 0x00000000-0x01ffffff]
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x37800000-0x379fffff]
[    0.000000]  [mem 0x37800000-0x379fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x34000000-0x377fffff]
[    0.000000]  [mem 0x34000000-0x377fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0x33ffffff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x33ffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x37a00000-0x37bfdfff]
[    0.000000]  [mem 0x37a00000-0x37bfdfff] page 4k
[    0.000000] BRK [0x01b96000, 0x01b96fff] PGTABLE
[    0.000000] RAMDISK: [mem 0x35c22000-0x36e08fff]
[    0.000000] ACPI: RSDP 000f8710 000014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 7ffb0000 000030 (v01 A M I  OEMRSDT  08000607 MSFT 00000097)
[    0.000000] ACPI: FACP 7ffb0200 000084 (v02 A M I  OEMFACP  08000607 MSFT 00000097)
[    0.000000] ACPI: DSDT 7ffb03f0 003F26 (v01  K8UNF K8UNF201 00000201 INTL 02002026)
[    0.000000] ACPI: FACS 7ffc0000 000040
[    0.000000] ACPI: APIC 7ffb0390 00005C (v01 A M I  OEMAPIC  08000607 MSFT 00000097)
[    0.000000] ACPI: OEMB 7ffc0040 000056 (v01 A M I  AMI_OEM  08000607 MSFT 00000097)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1155MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] BRK [0x01b97000, 0x01b97fff] PGTABLE
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   Normal   [mem 0x01000000-0x37bfdfff]
[    0.000000]   HighMem  [mem 0x37bfe000-0x7ffaffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009efff]
[    0.000000]   node   0: [mem 0x00100000-0x7ffaffff]
[    0.000000] On node 0 totalpages: 524110
[    0.000000] free_area_init_node: node 0, pgdat c199d700, node_mem_map f4c22020
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3998 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 224254 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2312 pages used for memmap
[    0.000000]   HighMem zone: 295858 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: BIOS IRQ0 override ignored.
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] smpboot: Allowing 2 CPUs, 1 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000e7fff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e8000-0x000fffff]
[    0.000000] e820: [mem 0x80000000-0xff7bffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @f7bd6000 s36160 r0 d21184 u57344
[    0.000000] pcpu-alloc: s36160 r0 d21184 u57344 alloc=14*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 522326
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-45-generic root=UUID=e01f1e08-28ba-4214-82b0-6a811691777f ro
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 4193656 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:0007ffb0)
[    0.000000] Memory: 2044724K/2096440K available (6547K kernel code, 641K rwdata, 2764K rodata, 876K init, 924K bss, 51716K reserved, 1183432K highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff14000 - 0xfffff000   ( 940 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc19bb000 - 0xc1a96000   ( 876 kB)
[    0.000000]       .data : 0xc1665134 - 0xc19ba580   (3413 kB)
[    0.000000]       .text : 0xc1000000 - 0xc1665134   (6548 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=8 to nr_cpu_ids=2.
[    0.000000] NR_IRQS:2304 nr_irqs:512 16
[    0.000000] CPU 0 irqstacks, hard=f7008000 soft=f700a000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 1808.807 MHz processor
[    0.000000] tsc: Marking TSC unstable due to TSCs unsynchronized
[    0.004052] Calibrating delay loop (skipped), value calculated using timer frequency.. 3617.61 BogoMIPS (lpj=7235228)
[    0.004148] pid_max: default: 32768 minimum: 301
[    0.004253] Security Framework initialized
[    0.004326] AppArmor: AppArmor initialized
[    0.004373] Yama: becoming mindful.
[    0.004497] Mount-cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.004548] Mountpoint-cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.004917] Initializing cgroup subsys memory
[    0.004974] Initializing cgroup subsys devices
[    0.005022] Initializing cgroup subsys freezer
[    0.005071] Initializing cgroup subsys blkio
[    0.005119] Initializing cgroup subsys perf_event
[    0.005168] Initializing cgroup subsys hugetlb
[    0.005250] mce: CPU supports 5 MCE banks
[    0.005316] Last level iTLB entries: 4KB 512, 2MB 8, 4MB 4
[    0.005316] Last level dTLB entries: 4KB 512, 2MB 8, 4MB 4
[    0.005316] tlb_flushall_shift: 4
[    0.019832] ACPI: Core revision 20131115
[    0.023382] ACPI: All ACPI Tables successfully acquired
[    0.023679] ftrace: allocating 27841 entries in 55 pages
[    0.032158] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.032579] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.074579] smpboot: CPU0: AMD Sempron(tm) Processor 3100+ (fam: 0f, model: 2c, stepping: 02)
[    0.076000] Performance Events: AMD PMU driver.
[    0.076000] ... version:                0
[    0.076000] ... bit width:              48
[    0.076000] ... generic registers:      4
[    0.076000] ... value mask:             0000ffffffffffff
[    0.076000] ... max period:             00007fffffffffff
[    0.076000] ... fixed-purpose events:   0
[    0.076000] ... event mask:             000000000000000f
[    0.076000] x86: Booted up 1 node, 1 CPUs
[    0.076000] smpboot: Total of 1 processors activated (3617.61 BogoMIPS)
[    0.076000] devtmpfs: initialized
[    0.076000] EVM: security.selinux
[    0.076000] EVM: security.SMACK64
[    0.076000] EVM: security.ima
[    0.076000] EVM: security.capability
[    0.076000] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.076000] PM: Registering ACPI NVS region [mem 0x7ffc0000-0x7ffeffff] (196608 bytes)
[    0.077685] pinctrl core: initialized pinctrl subsystem
[    0.077864] regulator-dummy: no parameters
[    0.077945] RTC time: 21:16:09, date: 02/15/15
[    0.078057] NET: Registered protocol family 16
[    0.078306] EISA bus registered
[    0.078353] cpuidle: using governor ladder
[    0.078400] cpuidle: using governor menu
[    0.078451] node 0 link 0: io port [1000, ffffff]
[    0.078455] TOM: 0000000080000000 aka 2048M
[    0.078504] node 0 link 0: mmio [a0000, bffff]
[    0.078508] node 0 link 0: mmio [80000000, fe0bffff]
[    0.078513] bus: [bus 00-ff] on node 0 link 0
[    0.078515] bus: 00 [io  0x0000-0xffff]
[    0.078517] bus: 00 [mem 0x000a0000-0x000bffff]
[    0.078520] bus: 00 [mem 0x80000000-0xfcffffffff]
[    0.078572] ACPI: bus type PCI registered
[    0.078621] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.079542] PCI: Using configuration type 1 for base access
[    0.081319] bio: create slab <bio-0> at 0
[    0.081584] ACPI: Added _OSI(Module Device)
[    0.081631] ACPI: Added _OSI(Processor Device)
[    0.081678] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.081725] ACPI: Added _OSI(Processor Aggregator Device)
[    0.083340] ACPI: Executed 1 blocks of module-level executable AML code
[    0.084973] ACPI: Interpreter enabled
[    0.085034] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)
[    0.085164] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S3_] (20131115/hwxface-580)
[    0.085303] ACPI: (supports S0 S1 S4 S5)
[    0.085349] ACPI: Using IOAPIC for interrupt routing
[    0.085438] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.085621] ACPI: No dock devices found.
[    0.090435] ACPI: Power Resource [ISAV] (on)
[    0.093243] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.093298] acpi PNP0A03:00: _OSC: OS supports [ASPM ClockPM Segments MSI]
[    0.093352] acpi PNP0A03:00: _OSC failed (AE_NOT_FOUND); disabling ASPM
[    0.093524] acpi PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.093528] acpi PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.093531] acpi PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.093534] acpi PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff] (ignored)
[    0.093538] acpi PNP0A03:00: host bridge window [mem 0x80000000-0xffffffff] (ignored)
[    0.093541] PCI: root bus 00: hardware-probed resources
[    0.093547] acpi PNP0A03:00: fail to add MMCONFIG information, can't access extended PCI configuration space under this bridge.
[    0.093740] PCI host bridge to bus 0000:00
[    0.093789] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.093837] pci_bus 0000:00: root bus resource [io  0x0000-0xffff]
[    0.093886] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.093936] pci_bus 0000:00: root bus resource [mem 0x80000000-0xfcffffffff]
[    0.093999] pci 0000:00:00.0: [10de:00e1] type 00 class 0x060000
[    0.094009] pci 0000:00:00.0: reg 0x10: [mem 0xf8000000-0xfbffffff pref]
[    0.094123] pci 0000:00:01.0: [10de:00e0] type 00 class 0x060100
[    0.094222] pci 0000:00:01.1: [10de:00e4] type 00 class 0x0c0500
[    0.094231] pci 0000:00:01.1: reg 0x10: [io  0x5080-0x509f]
[    0.094246] pci 0000:00:01.1: reg 0x20: [io  0x5000-0x503f]
[    0.094252] pci 0000:00:01.1: reg 0x24: [io  0x5040-0x507f]
[    0.094269] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.094339] pci 0000:00:02.0: [10de:00e7] type 00 class 0x0c0310
[    0.094349] pci 0000:00:02.0: reg 0x10: [mem 0xff6ff000-0xff6fffff]
[    0.094380] pci 0000:00:02.0: supports D1 D2
[    0.094383] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.094417] pci 0000:00:02.0: System wakeup disabled by ACPI
[    0.094505] pci 0000:00:02.1: [10de:00e7] type 00 class 0x0c0310
[    0.094514] pci 0000:00:02.1: reg 0x10: [mem 0xff6fe000-0xff6fefff]
[    0.094545] pci 0000:00:02.1: supports D1 D2
[    0.094548] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.094581] pci 0000:00:02.1: System wakeup disabled by ACPI
[    0.094671] pci 0000:00:02.2: [10de:00e8] type 00 class 0x0c0320
[    0.094682] pci 0000:00:02.2: reg 0x10: [mem 0xff6fdc00-0xff6fdcff]
[    0.094719] pci 0000:00:02.2: supports D1 D2
[    0.094722] pci 0000:00:02.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.094772] pci 0000:00:02.2: System wakeup disabled by ACPI
[    0.094864] pci 0000:00:05.0: [10de:00df] type 00 class 0x068000
[    0.094873] pci 0000:00:05.0: reg 0x10: [mem 0xff6fc000-0xff6fcfff]
[    0.094879] pci 0000:00:05.0: reg 0x14: [io  0xec00-0xec07]
[    0.094907] pci 0000:00:05.0: supports D1 D2
[    0.094910] pci 0000:00:05.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.094943] pci 0000:00:05.0: System wakeup disabled by ACPI
[    0.095032] pci 0000:00:06.0: [10de:00ea] type 00 class 0x040100
[    0.095042] pci 0000:00:06.0: reg 0x10: [io  0xe800-0xe8ff]
[    0.095048] pci 0000:00:06.0: reg 0x14: [io  0xe480-0xe4ff]
[    0.095054] pci 0000:00:06.0: reg 0x18: [mem 0xff6fb000-0xff6fbfff]
[    0.095079] pci 0000:00:06.0: supports D1 D2
[    0.095110] pci 0000:00:06.0: System wakeup disabled by ACPI
[    0.095200] pci 0000:00:08.0: [10de:00e5] type 00 class 0x01018a
[    0.095220] pci 0000:00:08.0: reg 0x20: [io  0xffa0-0xffaf]
[    0.095299] pci 0000:00:0a.0: [10de:00e3] type 00 class 0x010185
[    0.095308] pci 0000:00:0a.0: reg 0x10: [io  0x0f80-0x0f87]
[    0.095314] pci 0000:00:0a.0: reg 0x14: [io  0x0f00-0x0f03]
[    0.095320] pci 0000:00:0a.0: reg 0x18: [io  0x0e80-0x0e87]
[    0.095326] pci 0000:00:0a.0: reg 0x1c: [io  0x0e00-0x0e03]
[    0.095332] pci 0000:00:0a.0: reg 0x20: [io  0xd800-0xd80f]
[    0.095338] pci 0000:00:0a.0: reg 0x24: [io  0xd400-0xd47f]
[    0.095415] pci 0000:00:0b.0: [10de:00e2] type 01 class 0x060400
[    0.095496] pci 0000:00:0e.0: [10de:00ed] type 01 class 0x060400
[    0.095539] pci 0000:00:0e.0: System wakeup disabled by ACPI
[    0.095637] pci 0000:00:18.0: [1022:1100] type 00 class 0x060000
[    0.095707] pci 0000:00:18.1: [1022:1101] type 00 class 0x060000
[    0.095776] pci 0000:00:18.2: [1022:1102] type 00 class 0x060000
[    0.095840] pci 0000:00:18.3: [1022:1103] type 00 class 0x060000
[    0.095948] pci 0000:01:00.0: [1002:4153] type 00 class 0x030000
[    0.095965] pci 0000:01:00.0: reg 0x10: [mem 0xe0000000-0xefffffff pref]
[    0.095974] pci 0000:01:00.0: reg 0x14: [io  0xc000-0xc0ff]
[    0.095983] pci 0000:01:00.0: reg 0x18: [mem 0xff5f0000-0xff5fffff]
[    0.096023] pci 0000:01:00.0: reg 0x30: [mem 0xff5c0000-0xff5dffff pref]
[    0.096054] pci 0000:01:00.0: supports D1 D2
[    0.096103] pci 0000:01:00.1: [1002:4173] type 00 class 0x038000
[    0.096117] pci 0000:01:00.1: reg 0x10: [mem 0xd0000000-0xdfffffff pref]
[    0.096126] pci 0000:01:00.1: reg 0x14: [mem 0xff5e0000-0xff5effff]
[    0.096177] pci 0000:01:00.1: supports D1 D2
[    0.096244] pci 0000:00:0b.0: PCI bridge to [bus 01]
[    0.097161] pci 0000:00:0b.0:   bridge window [io  0xa000-0xcfff]
[    0.097166] pci 0000:00:0b.0:   bridge window [mem 0xff500000-0xff5fffff]
[    0.097171] pci 0000:00:0b.0:   bridge window [mem 0xb6b00000-0xf6afffff pref]
[    0.097223] pci 0000:00:0e.0: PCI bridge to [bus 02]
[    0.097280] pci_bus 0000:00: on NUMA node 0
[    0.098192] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *0, disabled.
[    0.098615] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *0, disabled.
[    0.099034] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *0, disabled.
[    0.099453] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *11
[    0.099836] ACPI: PCI Interrupt Link [LNKE] (IRQs 16 17 18 19) *11
[    0.100211] ACPI: PCI Interrupt Link [LUS0] (IRQs 20 21 22) *9
[    0.100555] ACPI: PCI Interrupt Link [LUS1] (IRQs 20 21 22) *5
[    0.100904] ACPI: PCI Interrupt Link [LUS2] (IRQs 20 21 22) *3
[    0.101252] ACPI: PCI Interrupt Link [LKLN] (IRQs 20 21 22) *9
[    0.101596] ACPI: PCI Interrupt Link [LAUI] (IRQs 20 21 22) *9
[    0.101942] ACPI: PCI Interrupt Link [LKMO] (IRQs 20 21 22) *0, disabled.
[    0.102322] ACPI: PCI Interrupt Link [LKSM] (IRQs 20 21 22) *0, disabled.
[    0.102702] ACPI: PCI Interrupt Link [LTID] (IRQs 20 21 22) *10
[    0.103055] ACPI: PCI Interrupt Link [LTIE] (IRQs 20 21 22) *0, disabled.
[    0.103454] ACPI: PCI Interrupt Link [LATA] (IRQs 22) *14
[    0.103727] ACPI: \_SB_.PCI0: notify handler is installed
[    0.103763] Found 1 acpi root devices
[    0.103959] vgaarb: setting as boot device: PCI:0000:01:00.0
[    0.104000] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.104004] vgaarb: loaded
[    0.104050] vgaarb: bridge control possible 0000:01:00.0
[    0.104447] SCSI subsystem initialized
[    0.104571] libata version 3.00 loaded.
[    0.104609] ACPI: bus type USB registered
[    0.104687] usbcore: registered new interface driver usbfs
[    0.104746] usbcore: registered new interface driver hub
[    0.104821] usbcore: registered new device driver usb
[    0.105032] PCI: Using ACPI for IRQ routing
[    0.105081] PCI: pci_cache_line_size set to 64 bytes
[    0.105122] e820: reserve RAM buffer [mem 0x0009fc00-0x0009ffff]
[    0.105126] e820: reserve RAM buffer [mem 0x7ffb0000-0x7fffffff]
[    0.105287] NetLabel: Initializing
[    0.105333] NetLabel:  domain hash size = 128
[    0.105379] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.105443] NetLabel:  unlabeled traffic allowed by default
[    0.105636] Switched to clocksource refined-jiffies
[    0.114464] AppArmor: AppArmor Filesystem Enabled
[    0.114574] pnp: PnP ACPI init
[    0.114648] ACPI: bus type PNP registered
[    0.114834] pnp 00:00: [dma 4]
[    0.114867] pnp 00:00: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.114920] pnp 00:01: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.114954] pnp 00:02: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.114989] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.115532] pnp 00:04: [dma 3]
[    0.115672] pnp 00:04: Plug and Play ACPI device, IDs PNP0401 (active)
[    0.115880] pnp 00:05: Plug and Play ACPI device, IDs PNPb02f (active)
[    0.116154] system 00:06: [io  0x04d0-0x04d1] has been reserved
[    0.116206] system 00:06: [io  0x4000-0x407f] could not be reserved
[    0.116256] system 00:06: [io  0x4080-0x40ff] has been reserved
[    0.116307] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.116397] system 00:07: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.116448] system 00:07: [mem 0xfee00000-0xfeefffff] has been reserved
[    0.116498] system 00:07: [mem 0xff7c0000-0xffffffff] has been reserved
[    0.116548] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.116613] pnp 00:08: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.116695] pnp 00:09: Plug and Play ACPI device, IDs PNP0f03 PNP0f13 (active)
[    0.116923] pnp 00:0a: [dma 0 disabled]
[    0.117001] pnp 00:0a: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.117099] system 00:0b: [io  0x0290-0x029f] has been reserved
[    0.117150] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.117342] system 00:0c: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.117392] system 00:0c: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.117443] system 00:0c: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.117493] system 00:0c: [mem 0x00100000-0x7fffffff] could not be reserved
[    0.117544] system 00:0c: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.117801] pnp: PnP ACPI: found 13 devices
[    0.117848] ACPI: bus type PNP unregistered
[    0.117896] PnPBIOS: Disabled by ACPI PNP
[    0.154469] Switched to clocksource acpi_pm
[    0.154552] pci 0000:00:0b.0: PCI bridge to [bus 01]
[    0.154603] pci 0000:00:0b.0:   bridge window [io  0xa000-0xcfff]
[    0.154655] pci 0000:00:0b.0:   bridge window [mem 0xff500000-0xff5fffff]
[    0.154706] pci 0000:00:0b.0:   bridge window [mem 0xb6b00000-0xf6afffff pref]
[    0.154766] pci 0000:00:0e.0: PCI bridge to [bus 02]
[    0.154819] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
[    0.154823] pci_bus 0000:00: resource 5 [mem 0x000a0000-0x000bffff]
[    0.154826] pci_bus 0000:00: resource 6 [mem 0x80000000-0xfcffffffff]
[    0.154830] pci_bus 0000:01: resource 0 [io  0xa000-0xcfff]
[    0.154833] pci_bus 0000:01: resource 1 [mem 0xff500000-0xff5fffff]
[    0.154836] pci_bus 0000:01: resource 2 [mem 0xb6b00000-0xf6afffff pref]
[    0.154899] NET: Registered protocol family 2
[    0.155277] TCP established hash table entries: 8192 (order: 3, 32768 bytes)
[    0.155355] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.155454] TCP: Hash tables configured (established 8192 bind 8192)
[    0.155564] TCP: reno registered
[    0.155612] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.155671] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.155813] NET: Registered protocol family 1
[    0.155813] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 22
[    0.228214] ACPI: PCI Interrupt Link [LUS1] enabled at IRQ 21
[    0.300206] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 20
[    0.300337] pci 0000:01:00.0: Video device with shadowed ROM
[    0.300343] PCI: CLS 64 bytes, default 64
[    0.300428] Trying to unpack rootfs image as initramfs...
[    0.832222] Freeing initrd memory: 18332K (f5c22000 - f6e09000)
[    0.832499] microcode: AMD CPU family 0xf not supported
[    0.832547] Scanning for low memory corruption every 60 seconds
[    0.832970] Initialise system trusted keyring
[    0.833081] audit: initializing netlink socket (disabled)
[    0.833144] type=2000 audit(1424034969.831:1): initialized
[    0.864814] bounce pool size: 64 pages
[    0.864877] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.866775] zbud: loaded
[    0.866942] VFS: Disk quotas dquot_6.5.2
[    0.867059] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.867781] fuse init (API version 7.22)
[    0.867935] msgmni has been set to 1718
[    0.868119] Key type big_key registered
[    0.868513] Key type asymmetric registered
[    0.868561] Asymmetric key parser 'x509' registered
[    0.868664] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.868755] io scheduler noop registered
[    0.868802] io scheduler deadline registered (default)
[    0.868887] io scheduler cfq registered
[    0.869110] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.869181] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.869307] ipmi message handler version 39.2
[    0.869460] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.869522] ACPI: Power Button [PWRB]
[    0.869631] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.869688] ACPI: Power Button [PWRF]
[    0.869896] GHES: HEST is not enabled!
[    0.870071] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.890532] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
[    0.890654] isapnp: Scanning for PnP cards...
[    1.028333] Linux agpgart interface v0.103
[    1.028415] agpgart-amd64 0000:00:00.0: AGP bridge [10de/00e1]
[    1.028468] agpgart-amd64 0000:00:00.0: aperture size 4096 MB is not right, using settings from NB
[    1.028530] agpgart-amd64 0000:00:00.0: setting up Nforce3 AGP
[    1.028580] agpgart-amd64 0000:00:00.0: aperture base > 4G
[    1.028657] agpgart-amd64 0000:00:00.0: AGP bridge [10de/00e1]
[    1.028709] agpgart-amd64 0000:00:00.0: aperture size 4096 MB is not right, using settings from NB
[    1.028766] agpgart-amd64 0000:00:00.0: setting up Nforce3 AGP
[    1.028815] agpgart-amd64 0000:00:00.0: aperture base > 4G
[    1.028948] agpgart-amd64 0000:01:00.0: AGP bridge [1002/4153]
[    1.029000] agpgart-amd64 0000:01:00.0: aperture size 4096 MB is not right, using settings from NB
[    1.031409] agpgart-amd64 0000:01:00.0: AGP aperture is 64M @ 0xf8000000
[    1.033301] brd: module loaded
[    1.034300] loop: module loaded
[    1.035058] libphy: Fixed MDIO Bus: probed
[    1.035268] tun: Universal TUN/TAP device driver, 1.6
[    1.035315] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.035429] PPP generic driver version 2.4.2
[    1.035533] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.035585] ehci-pci: EHCI PCI platform driver
[    1.035767] ehci-pci 0000:00:02.2: EHCI Host Controller
[    1.035822] ehci-pci 0000:00:02.2: new USB bus registered, assigned bus number 1
[    1.035887] ehci-pci 0000:00:02.2: debug port 0
[    1.035969] ehci-pci 0000:00:02.2: cache line size of 64 is not supported
[    1.035997] ehci-pci 0000:00:02.2: irq 20, io mem 0xff6fdc00
[    1.079629] ehci-pci 0000:00:02.2: USB 2.0 started, EHCI 1.00
[    1.079746] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.079796] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.079852] usb usb1: Product: EHCI Host Controller
[    1.079900] usb usb1: Manufacturer: Linux 3.13.0-45-generic ehci_hcd
[    1.079949] usb usb1: SerialNumber: 0000:00:02.2
[    1.080157] hub 1-0:1.0: USB hub found
[    1.080213] hub 1-0:1.0: 8 ports detected
[    1.080494] ehci-platform: EHCI generic platform driver
[    1.080557] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.080605] ohci-pci: OHCI PCI platform driver
[    1.080752] ohci-pci 0000:00:02.0: OHCI PCI host controller
[    1.080809] ohci-pci 0000:00:02.0: new USB bus registered, assigned bus number 2
[    1.080899] ohci-pci 0000:00:02.0: irq 22, io mem 0xff6ff000
[    1.169931] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    1.169982] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.170038] usb usb2: Product: OHCI PCI host controller
[    1.170086] usb usb2: Manufacturer: Linux 3.13.0-45-generic ohci_hcd
[    1.170135] usb usb2: SerialNumber: 0000:00:02.0
[    1.170320] hub 2-0:1.0: USB hub found
[    1.170374] hub 2-0:1.0: 4 ports detected
[    1.170621] ohci-pci 0000:00:02.1: OHCI PCI host controller
[    1.170674] ohci-pci 0000:00:02.1: new USB bus registered, assigned bus number 3
[    1.170761] ohci-pci 0000:00:02.1: irq 21, io mem 0xff6fe000
[    1.257812] isapnp: No Plug & Play device found
[    1.259955] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    1.260019] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.260075] usb usb3: Product: OHCI PCI host controller
[    1.260124] usb usb3: Manufacturer: Linux 3.13.0-45-generic ohci_hcd
[    1.260172] usb usb3: SerialNumber: 0000:00:02.1
[    1.260360] hub 3-0:1.0: USB hub found
[    1.260415] hub 3-0:1.0: 4 ports detected
[    1.260597] ohci-platform: OHCI generic platform driver
[    1.260661] uhci_hcd: USB Universal Host Controller Interface driver
[    1.260823] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.263844] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.263897] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.264122] mousedev: PS/2 mouse device common for all mice
[    1.264321] rtc_cmos 00:01: RTC can wake from S4
[    1.264498] rtc_cmos 00:01: rtc core: registered rtc_cmos as rtc0
[    1.264571] rtc_cmos 00:01: alarms up to one year, y3k, 114 bytes nvram
[    1.264726] device-mapper: uevent: version 1.0.3
[    1.264857] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
[    1.265811] platform eisa.0: Probing EISA bus 0
[    1.265861] platform eisa.0: EISA: Cannot allocate resource for mainboard
[    1.265911] platform eisa.0: Cannot allocate resource for EISA slot 1
[    1.265961] platform eisa.0: Cannot allocate resource for EISA slot 2
[    1.266010] platform eisa.0: Cannot allocate resource for EISA slot 3
[    1.266060] platform eisa.0: Cannot allocate resource for EISA slot 4
[    1.266109] platform eisa.0: Cannot allocate resource for EISA slot 5
[    1.266159] platform eisa.0: Cannot allocate resource for EISA slot 6
[    1.266208] platform eisa.0: Cannot allocate resource for EISA slot 7
[    1.266257] platform eisa.0: Cannot allocate resource for EISA slot 8
[    1.266306] platform eisa.0: EISA: Detected 0 cards
[    1.266362] cpufreq-nforce2: No nForce2 chipset.
[    1.266411] ledtrig-cpu: registered to indicate activity on CPUs
[    1.266649] TCP: cubic registered
[    1.266841] NET: Registered protocol family 10
[    1.267149] NET: Registered protocol family 17
[    1.267209] Key type dns_resolver registered
[    1.267442] Using IPI No-Shortcut mode
[    1.267584] Loading compiled-in X.509 certificates
[    1.272439] Loaded X.509 cert 'Magrathea: Glacier signing key: 3689bf48af502cbafe71e5c25d6c55340b7f13ff'
[    1.272514] registered taskstats version 1
[    1.275894] Key type trusted registered
[    1.278987] Key type encrypted registered
[    1.282101] AppArmor: AppArmor sha1 policy hashing enabled
[    1.282157] IMA: No TPM chip found, activating TPM-bypass!
[    1.282406] regulator-dummy: disabling
[    1.282509]   Magic number: 3:51:298
[    1.282685] rtc_cmos 00:01: setting system clock to 2015-02-15 21:16:11 UTC (1424034971)
[    1.282898] powernow-k8: fid 0xa (1800 MHz), vid 0x6
[    1.282947] powernow-k8: fid 0x2 (1000 MHz), vid 0x12
[    1.283020] powernow-k8: Found 1 AMD Sempron(tm) Processor 3100+ (1 cpu cores) (version 2.20.00)
[    1.283082] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.283130] EDD information not available.
[    1.283212] PM: Hibernation image not present or could not be loaded.
[    1.284307] Freeing unused kernel memory: 876K (c19bb000 - c1a96000)
[    1.284425] Write protecting the kernel text: 6552k
[    1.284553] Write protecting the kernel read-only data: 2768k
[    1.284600] NX-protecting the kernel data: 5736k
[    1.292040] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    1.312349] systemd-udevd[88]: starting version 204
[    1.389531] pata_amd 0000:00:08.0: version 0.4.1
[    1.399432] scsi0 : pata_amd
[    1.402887] scsi1 : pata_amd
[    1.403024] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    1.403074] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    1.403326] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.403608] ACPI: PCI Interrupt Link [LKLN] enabled at IRQ 22
[    1.783159] ata1.00: HPA detected: current 156299375, native 156301488
[    1.783218] ata1.00: ATA-7: ST380215A, 3.AAC, max UDMA/100
[    1.783267] ata1.00: 156299375 sectors, multi 16: LBA48 
[    1.783320] ata1.01: ATAPI: SONY    CD-RW  CRX175A1, 5YS2, max UDMA/33
[    1.783376] ata1: nv_mode_filter: 0x3f39f&0x3f39f->0x3f39f, BIOS=0x3f000 (0xc6c0c5c6) ACPI=0x3f01f (20:60:0x1f)
[    1.783381] ata1: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc6c0c5c6) ACPI=0x701f (20:60:0x1f)
[    1.818494] input: GenPS/2 Genius Mouse as /devices/platform/i8042/serio1/input/input4
[    1.849717] ata1.00: configured for UDMA/100
[    1.864191] ata1.01: configured for UDMA/33
[    1.864948] scsi 0:0:0:0: Direct-Access     ATA      ST380215A        3.AA PQ: 0 ANSI: 5
[    1.865403] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.865902] scsi 0:0:1:0: CD-ROM            SONY     CD-RW  CRX175A1  5YS2 PQ: 0 ANSI: 5
[    1.866672] sd 0:0:0:0: [sda] 156299375 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    1.866937] sr0: scsi3-mmc drive: 13x/40x writer cd/rw xa/form2 cdda tray
[    1.866987] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.867522] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    1.867699] sr 0:0:1:0: Attached scsi generic sg1 type 5
[    1.868406] sd 0:0:0:0: [sda] Write Protect is off
[    1.868461] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.868494] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.928723] forcedeth 0000:00:05.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:13:8f:e7:a2:b6
[    1.928788] forcedeth 0000:00:05.0: csum timirq lnktim desc-v2
[    1.929138] sata_nv 0000:00:0a.0: version 3.5
[    1.929395] ACPI: PCI Interrupt Link [LTID] enabled at IRQ 21
[    1.931196] scsi2 : sata_nv
[    1.931442] scsi3 : sata_nv
[    1.931540] ata3: SATA max UDMA/133 cmd 0xf80 ctl 0xf00 bmdma 0xd800 irq 21
[    1.931590] ata4: SATA max UDMA/133 cmd 0xe80 ctl 0xe00 bmdma 0xd808 irq 21
[    1.940893]  sda: sda1 sda2 < sda5 sda6 > sda3 sda4
[    1.941774] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.040299] ata2.00: ATAPI: PIONEER DVD-RW  DVR-109, 1.09, max UDMA/66
[    2.070534] ata2.01: HPA detected: current 390719855, native 390721968
[    2.070585] ata2.01: ATA-7: ST3200827A, 3.AAD, max UDMA/100
[    2.070633] ata2.01: 390719855 sectors, multi 16: LBA48 
[    2.070688] ata2: nv_mode_filter: 0x1f39f&0x1f39f->0x1f39f, BIOS=0x1f000 (0xc6c0c5c6) ACPI=0x1f01f (30:20:0x1f)
[    2.070693] ata2: nv_mode_filter: 0x3f39f&0x3f39f->0x3f39f, BIOS=0x3f000 (0xc6c0c5c6) ACPI=0x3f01f (30:20:0x1f)
[    2.084232] ata2.00: configured for UDMA/66
[    2.145451] ata2.01: configured for UDMA/100
[    2.158391] scsi 1:0:0:0: CD-ROM            PIONEER  DVD-RW  DVR-109  1.09 PQ: 0 ANSI: 5
[    2.169603] sr1: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[    2.170166] sr 1:0:0:0: Attached scsi CD-ROM sr1
[    2.170343] sr 1:0:0:0: Attached scsi generic sg2 type 5
[    2.170654] scsi 1:0:1:0: Direct-Access     ATA      ST3200827A       3.AA PQ: 0 ANSI: 5
[    2.171030] sd 1:0:1:0: Attached scsi generic sg3 type 0
[    2.171643] sd 1:0:1:0: [sdb] 390719855 512-byte logical blocks: (200 GB/186 GiB)
[    2.171774] sd 1:0:1:0: [sdb] Write Protect is off
[    2.171823] sd 1:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    2.171856] sd 1:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.194069]  sdb: sdb1
[    2.194538] sd 1:0:1:0: [sdb] Attached SCSI disk
[    2.240031] ata3: SATA link down (SStatus 0 SControl 300)
[    2.552025] ata4: SATA link down (SStatus 0 SControl 300)
[    3.433724] random: nonblocking pool is initialized
[    6.021567] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[    8.531980] Adding 1535996k swap on /dev/sda4.  Priority:-1 extents:1 across:1535996k FS
[    9.483938] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    9.806962] systemd-udevd[263]: starting version 204
[   11.014684] lp: driver loaded but no devices found
[   11.151840] ppdev: user-space parallel port driver
[   11.186563] parport_pc 00:04: reported by Plug and Play ACPI
[   11.186670] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   11.284282] lp0: using parport0 (interrupt-driven).
[   13.066657] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[   13.975615] gameport gameport0: NS558 PnP Gameport is pnp00:05/gameport0, io 0x200, speed 890kHz
[   14.186198] i2c i2c-0: nForce2 SMBus adapter at 0x5000
[   14.186448] i2c i2c-1: nForce2 SMBus adapter at 0x5040
[   14.581318] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   16.010913] ACPI: PCI Interrupt Link [LAUI] enabled at IRQ 20
[   16.332048] intel8x0_measure_ac97_clock: measured 54643 usecs (2680 samples)
[   16.332055] intel8x0: clocking to 46977
[   17.660331] type=1400 audit(1424031387.876:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=443 comm="apparmor_parser"
[   17.660345] type=1400 audit(1424031387.876:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=443 comm="apparmor_parser"
[   17.660351] type=1400 audit(1424031387.876:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=443 comm="apparmor_parser"
[   17.661387] type=1400 audit(1424031387.876:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=443 comm="apparmor_parser"
[   17.661396] type=1400 audit(1424031387.876:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=443 comm="apparmor_parser"
[   17.661921] type=1400 audit(1424031387.876:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=443 comm="apparmor_parser"
[   17.663360] type=1400 audit(1424031387.876:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=411 comm="apparmor_parser"
[   17.663375] type=1400 audit(1424031387.876:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=411 comm="apparmor_parser"
[   17.663382] type=1400 audit(1424031387.876:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=411 comm="apparmor_parser"
[   17.664153] type=1400 audit(1424031387.880:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=411 comm="apparmor_parser"
[   19.295617] init: failsafe main process (484) killed by TERM signal
[   22.838572] init: cups main process (657) killed by HUP signal
[   22.838595] init: cups main process ended, respawning
[   23.240585] Bluetooth: Core ver 2.17
[   23.240713] NET: Registered protocol family 31
[   23.240716] Bluetooth: HCI device and connection manager initialized
[   23.242741] Bluetooth: HCI socket layer initialized
[   23.242750] Bluetooth: L2CAP socket layer initialized
[   23.242766] Bluetooth: SCO socket layer initialized
[   23.367057] Bluetooth: RFCOMM TTY layer initialized
[   23.367075] Bluetooth: RFCOMM socket layer initialized
[   23.367098] Bluetooth: RFCOMM ver 1.11
[   23.726628] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   23.726636] Bluetooth: BNEP filters: protocol multicast
[   23.726651] Bluetooth: BNEP socket layer initialized
[   24.506970] audit_printk_skb: 42 callbacks suppressed
[   24.506977] type=1400 audit(1424031394.720:26): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince" pid=659 comm="apparmor_parser"
[   24.506988] type=1400 audit(1424031394.720:27): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=659 comm="apparmor_parser"
[   24.506995] type=1400 audit(1424031394.720:28): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince-previewer" pid=659 comm="apparmor_parser"
[   24.507001] type=1400 audit(1424031394.720:29): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=659 comm="apparmor_parser"
[   24.507008] type=1400 audit(1424031394.720:30): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince-thumbnailer" pid=659 comm="apparmor_parser"
[   24.507014] type=1400 audit(1424031394.720:31): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=659 comm="apparmor_parser"
[   24.513728] type=1400 audit(1424031394.728:32): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="sanitized_helper" pid=659 comm="apparmor_parser"
[   24.513745] type=1400 audit(1424031394.728:33): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/bin/evince-previewer" pid=659 comm="apparmor_parser"
[   24.513752] type=1400 audit(1424031394.728:34): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="sanitized_helper" pid=659 comm="apparmor_parser"
[   24.513759] type=1400 audit(1424031394.728:35): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/bin/evince-thumbnailer" pid=659 comm="apparmor_parser"
[   39.288406] init: lightdm main process (1171) terminated with status 1
[   39.296546] init: plymouth-upstart-bridge main process ended, respawning
[   39.319484] init: plymouth-ready (startup) main process (149) terminated with status 1
[   39.322760] init: plymouth-upstart-bridge main process (1201) terminated with status 1
[   39.322786] init: plymouth-upstart-bridge main process ended, respawning
[   52.480111] audit_printk_skb: 51 callbacks suppressed
[   52.480118] type=1400 audit(1424031422.693:53): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=1302 comm="apparmor_parser"
[   52.480131] type=1400 audit(1424031422.693:54): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1302 comm="apparmor_parser"
[   52.480893] type=1400 audit(1424031422.693:55): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1302 comm="apparmor_parser"

```

---

### Post by venneri2 on 2015-02-17
Hi again !!!

I've reinstall Xubuntu 14.04 again. After install, it works almos perfectly (loads radeon driver, but resolution is not correct). I have updated, and it works as before (loads radeon driver and resolution is not right: 1024x768). After two or three reboots (without configuring or installing anything) when it starts I get a black screen with a blinking cursor. lsmod output indicates that radeon module is loaded, however lspci -k indicates that driver in use is agpgart-amd64.

Why driver in use is agpgart isntead of radeon? What is agpgart? Could anyone give me an idea of what to do, to check, or something? I'm getting crazy. Is this a problem with ati cards? 

Thanks in advance for your help,

---

