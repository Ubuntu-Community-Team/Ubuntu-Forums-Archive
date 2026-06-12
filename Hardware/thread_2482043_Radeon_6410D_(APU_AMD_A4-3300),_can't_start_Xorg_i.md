---
title: "Radeon 6410D (APU AMD A4-3300), can't start Xorg in ubuntu 22.10 with radeon driver"
date: 2022-12-17
forum: Hardware
---

### Post by magowiz82 on 2022-12-17
Hi all,
since some years ago I had issues with ubuntu and mine APU, this is the bug report still opened since 2018: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1581799](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1581799) ,
at that time I was able to use X in a decent way using standard vesa driver, having an acceptable screen resolution, so for me was ok to use it like this, without too much detail and without graphic acceleration, in latest version of ubuntu and of linux kernel, things get worst: currently I'm only able to use that environment in a 640x480 resolution.

Mine lspci output:
```

 lspci -vvnn | grep VGA                                                                              sab 17 dic 2022, 17:28:34
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] SuperSumo [Radeon HD 6410D] [1002:9645] (prog-if 00 [VGA controller])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop+ ParErr- Stepping- SERR- FastB2B- DisINTx-
    BridgeCtl: Parity- SERR+ NoISA- VGA- VGA16+ MAbort- >Reset- FastB2B-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    BridgeCtl: Parity- SERR+ NoISA- VGA- VGA16+ MAbort- >Reset- FastB2B-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    BridgeCtl: Parity- SERR+ NoISA- VGA- VGA16+ MAbort- >Reset- FastB2B-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+

```

 here it is last `/var/log/Xorg.0.log`:
```

X.Org X Server 1.21.1.4
X Protocol Version 11, Revision 0
[    96.612] Current Operating System: Linux liano 5.19.0-26-generic #27-Ubuntu SMP PREEMPT_DYNAMIC Wed Nov 23 20:44:15 UTC 2022 x86_64
[    96.612] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-5.19.0-26-generic root=UUID=acd61f09-2fc9-4a54-bf0b-23f0a297d2e4 ro quiet splash vga=792 nomodeset vt.handoff=7
[    96.612] xorg-server 2:21.1.4-2ubuntu1.3 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    96.612] Current version of pixman: 0.40.0
[    96.612]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    96.612] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    96.613] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Dec 17 16:57:42 2022
[    96.613] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    96.614] (==) No Layout section.  Using the first Screen section.
[    96.614] (==) No screen section available. Using defaults.
[    96.614] (**) |-->Screen "Default Screen Section" (0)
[    96.614] (**) |   |-->Monitor "<default monitor>"
[    96.615] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    96.615] (==) Automatically adding devices
[    96.615] (==) Automatically enabling devices
[    96.615] (==) Automatically adding GPU devices
[    96.615] (==) Automatically binding GPU devices
[    96.615] (==) Max clients allowed: 256, resource mask: 0x1fffff
[    96.615] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    96.615]     Entry deleted from font path.
[    96.615] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    96.615]     Entry deleted from font path.
[    96.615] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    96.615]     Entry deleted from font path.
[    96.615] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    96.615]     Entry deleted from font path.
[    96.615] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    96.615]     Entry deleted from font path.
[    96.616] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    96.616] (==) ModulePath set to "/usr/lib/xorg/modules"
[    96.616] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    96.616] (II) Loader magic: 0x55c839214020
[    96.616] (II) Module ABI versions:
[    96.616]     X.Org ANSI C Emulation: 0.4
[    96.616]     X.Org Video Driver: 25.2
[    96.616]     X.Org XInput driver : 24.4
[    96.616]     X.Org Server Extension : 10.0
[    96.619] (++) using VT number 1

[    96.629] (II) systemd-logind: took control of session /org/freedesktop/login1/session/c6
[    96.643] (--) PCI:*(0@0:1:0) 1002:9645:1043:84c8 rev 0, Mem @ 0xc0000000/268435456, 0xfeb00000/262144, I/O @ 0x0000f000/256, BIOS @ 0x????????/131072
[    96.644] (II) LoadModule: "glx"
[    96.646] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    96.650] (II) Module glx: vendor="X.Org Foundation"
[    96.650]     compiled for 1.21.1.4, module version = 1.0.0
[    96.651]     ABI class: X.Org Server Extension, version 10.0
[    96.651] (==) Matched ati as autoconfigured driver 0
[    96.652] (==) Matched modesetting as autoconfigured driver 1
[    96.652] (==) Matched fbdev as autoconfigured driver 2
[    96.653] (==) Matched vesa as autoconfigured driver 3
[    96.653] (==) Assigned the driver to the xf86ConfigLayout
[    96.653] (II) LoadModule: "ati"
[    96.655] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    96.656] (II) Module ati: vendor="X.Org Foundation"
[    96.656]     compiled for 1.21.1.3, module version = 19.1.0
[    96.657]     Module class: X.Org Video Driver
[    96.657]     ABI class: X.Org Video Driver, version 25.2
[    96.737] (II) LoadModule: "radeon"
[    96.739] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    96.741] (II) Module radeon: vendor="X.Org Foundation"
[    96.741]     compiled for 1.21.1.3, module version = 19.1.0
[    96.742]     Module class: X.Org Video Driver
[    96.743]     ABI class: X.Org Video Driver, version 25.2
[    96.743] (II) LoadModule: "modesetting"
[    96.744] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    96.745] (II) Module modesetting: vendor="X.Org Foundation"
[    96.745]     compiled for 1.21.1.4, module version = 1.21.1
[    96.746]     Module class: X.Org Video Driver
[    96.747]     ABI class: X.Org Video Driver, version 25.2
[    96.747] (II) LoadModule: "fbdev"
[    96.748] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    96.749] (II) Module fbdev: vendor="X.Org Foundation"
[    96.749]     compiled for 1.21.1.3, module version = 0.5.0
[    96.750]     Module class: X.Org Video Driver
[    96.751]     ABI class: X.Org Video Driver, version 25.2
[    96.751] (II) LoadModule: "vesa"
[    96.752] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    96.753] (II) Module vesa: vendor="X.Org Foundation"
[    96.754]     compiled for 1.21.1.3, module version = 2.5.0
[    96.754]     Module class: X.Org Video Driver
[    96.755]     ABI class: X.Org Video Driver, version 25.2
[    96.755] (II) RADEON: Driver for ATI/AMD Radeon chipsets:
    ATI Radeon Mobility X600 (M24), ATI FireMV 2400,
    ATI Radeon Mobility X300 (M24), ATI FireGL M24 GL,
    ATI Radeon X600 (RV380), ATI FireGL V3200 (RV380),
    ATI Radeon IGP320 (A3), ATI Radeon IGP330/340/350 (A4),
    ATI Radeon 9500, ATI Radeon 9600TX, ATI FireGL Z1, ATI Radeon 9800SE,
    ATI Radeon 9800, ATI FireGL X2, ATI Radeon 9600, ATI Radeon 9600SE,
    ATI Radeon 9600XT, ATI FireGL T2, ATI Radeon 9650, ATI FireGL RV360,
    ATI Radeon 7000 IGP (A4+), ATI Radeon 8500 AIW,
    ATI Radeon IGP320M (U1), ATI Radeon IGP330M/340M/350M (U2),
    ATI Radeon Mobility 7000 IGP, ATI Radeon 9000/PRO, ATI Radeon 9000,
    ATI Radeon X800 (R420), ATI Radeon X800PRO (R420),
    ATI Radeon X800SE (R420), ATI FireGL X3 (R420),
    ATI Radeon Mobility 9800 (M18), ATI Radeon X800 SE (R420),
    ATI Radeon X800XT (R420), ATI Radeon X800 VE (R420),
    ATI Radeon X850 (R480), ATI Radeon X850 XT (R480),
    ATI Radeon X850 SE (R480), ATI Radeon X850 PRO (R480),
    ATI Radeon X850 XT PE (R480), ATI Radeon Mobility M7,
    ATI Mobility FireGL 7800 M7, ATI Radeon Mobility M6,
    ATI FireGL Mobility 9000 (M9), ATI Radeon Mobility 9000 (M9),
    ATI Radeon 9700 Pro, ATI Radeon 9700/9500Pro, ATI FireGL X1,
    ATI Radeon 9800PRO, ATI Radeon 9800XT,
    ATI Radeon Mobility 9600/9700 (M10/M11),
    ATI Radeon Mobility 9600 (M10), ATI Radeon Mobility 9600 (M11),
    ATI FireGL Mobility T2 (M10), ATI FireGL Mobility T2e (M11),
    ATI Radeon, ATI FireGL 8700/8800, ATI Radeon 8500, ATI Radeon 9100,
    ATI Radeon 7500, ATI Radeon VE/7000, ATI ES1000,
    ATI Radeon Mobility X300 (M22), ATI Radeon Mobility X600 SE (M24C),
    ATI FireGL M22 GL, ATI Radeon X800 (R423), ATI Radeon X800PRO (R423),
    ATI Radeon X800LE (R423), ATI Radeon X800SE (R423),
    ATI Radeon X800 XTP (R430), ATI Radeon X800 XL (R430),
    ATI Radeon X800 SE (R430), ATI Radeon X800 (R430),
    ATI FireGL V7100 (R423), ATI FireGL V5100 (R423),
    ATI FireGL unknown (R423), ATI Mobility FireGL V5000 (M26),
    ATI Mobility Radeon X700 XL (M26), ATI Mobility Radeon X700 (M26),
    ATI Radeon X550XTX, ATI Radeon 9100 IGP (A5),
    ATI Radeon Mobility 9100 IGP (U3), ATI Radeon XPRESS 200,
    ATI Radeon XPRESS 200M, ATI Radeon 9250, ATI Radeon 9200,
    ATI Radeon 9200SE, ATI FireMV 2200, ATI Radeon X300 (RV370),
    ATI Radeon X600 (RV370), ATI Radeon X550 (RV370),
    ATI FireGL V3100 (RV370), ATI FireMV 2200 PCIE (RV370),
    ATI Radeon Mobility 9200 (M9+), ATI Mobility Radeon X800 XT (M28),
    ATI Mobility FireGL V5100 (M28), ATI Mobility Radeon X800 (M28),
    ATI Radeon X850, ATI unknown Radeon / FireGL (R480),
    ATI Radeon X800XT (R423), ATI FireGL V5000 (RV410),
    ATI Radeon X700 XT (RV410), ATI Radeon X700 PRO (RV410),
    ATI Radeon X700 SE (RV410), ATI Radeon X700 (RV410),
    ATI Radeon X1800, ATI Mobility Radeon X1800 XT,
    ATI Mobility Radeon X1800, ATI Mobility FireGL V7200,
    ATI FireGL V7200, ATI FireGL V5300, ATI Mobility FireGL V7100,
    ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
    ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
    ATI Mobility Radeon X1400, ATI Radeon X1550 64-bit,
    ATI Mobility Radeon X1300, ATI Radeon X1300, ATI FireGL V3300,
    ATI FireGL V3350, ATI Mobility Radeon X1450,
    ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
    ATI FireMV 2250, ATI Radeon X1650, ATI Mobility FireGL V5200,
    ATI Mobility Radeon X1600, ATI Radeon X1300 XT/X1600 Pro,
    ATI FireGL V3400, ATI Mobility FireGL V5250,
    ATI Mobility Radeon X1700, ATI Mobility Radeon X1700 XT,
    ATI FireGL V5200, ATI Radeon X2300HD, ATI Mobility Radeon HD 2300,
    ATI Radeon X1950, ATI Radeon X1900, ATI AMD Stream Processor,
    ATI RV560, ATI Mobility Radeon X1900, ATI Radeon X1950 GT, ATI RV570,
    ATI FireGL V7400, ATI Radeon 9100 PRO IGP,
    ATI Radeon Mobility 9200 IGP, ATI Radeon X1200, ATI RS740,
    ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro,
    ATI Radeon HD 2900 GT, ATI FireGL V8650, ATI FireGL V8600,
    ATI FireGL V7600, ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
    ATI Radeon HD 4850 x2, ATI FirePro V8750 (FireGL),
    ATI FirePro V7760 (FireGL), ATI Mobility RADEON HD 4850,
    ATI Mobility RADEON HD 4850 X2, ATI FirePro RV770,
    AMD FireStream 9270, AMD FireStream 9250, ATI FirePro V8700 (FireGL),
    ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
    ATI FirePro M7750, ATI M98, ATI Mobility Radeon HD 4650,
    ATI Radeon RV730 (AGP), ATI Mobility Radeon HD 4670,
    ATI FirePro M5750, ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
    ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
    ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
    ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
    ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
    ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI RV610,
    ATI Radeon HD 2400 XT, ATI Radeon HD 2400 Pro,
    ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000, ATI Radeon HD 2350,
    ATI Mobility Radeon HD 2400 XT, ATI Mobility Radeon HD 2400,
    ATI RADEON E2400, ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
    ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
    ATI Mobility Radeon HD 3850 X2, ATI Mobility Radeon HD 3870,
    ATI Mobility Radeon HD 3870 X2, ATI Radeon HD3870 X2,
    ATI FireGL V7700, ATI Radeon HD3690, AMD Firestream 9170,
    ATI Radeon HD 4550, ATI Radeon RV710, ATI Radeon HD 4350,
    ATI Mobility Radeon 4300 Series, ATI Mobility Radeon 4500 Series,
    ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
    ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
    ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
    ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
    ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
    ATI FireGL V3600, ATI Radeon HD 2600 LE,
    ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
    ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
    ATI Radeon HD 3450, ATI Radeon HD 3430, ATI FirePro V3700,
    ATI FireMV 2450, ATI Radeon HD 3600 Series, ATI Radeon HD 3650 AGP,
    ATI Radeon HD 3600 PRO, ATI Radeon HD 3600 XT,
    ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
    ATI Mobility FireGL V5700, ATI Mobility FireGL V5725,
    ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
    ATI Radeon HD 3300 Graphics, ATI Radeon 3000 Graphics, SUMO, SUMO2,
    ATI Radeon HD 4200, ATI Radeon 4100, ATI Mobility Radeon HD 4200,
    ATI Mobility Radeon 4100, ATI Radeon HD 4290, ATI Radeon HD 4250,
    AMD Radeon HD 6310 Graphics, AMD Radeon HD 6250 Graphics,
    AMD Radeon HD 6300 Series Graphics,
    AMD Radeon HD 6200 Series Graphics, PALM, CYPRESS,
    ATI FirePro (FireGL) Graphics Adapter, AMD Firestream 9370,
    AMD Firestream 9350, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5900 Series, ATI Mobility Radeon HD 5800 Series,
    ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
    ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
    ATI Radeon HD 5670, ATI Radeon HD 5570, ATI Radeon HD 5500 Series,
    REDWOOD, ATI Mobility Radeon Graphics, CEDAR, ATI FirePro 2270,
    ATI Radeon HD 5450, CAYMAN, AMD Radeon HD 6900 Series,
    AMD Radeon HD 6900M Series, Mobility Radeon HD 6000 Series, BARTS,
    AMD Radeon HD 6800 Series, AMD Radeon HD 6700 Series, TURKS, CAICOS,
    ARUBA, TAHITI, PITCAIRN, VERDE, OLAND, HAINAN, BONAIRE, KABINI,
    MULLINS, KAVERI, HAWAII
[    96.788] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    96.788] (II) FBDEV: driver for framebuffer: fbdev
[    96.788] (II) VESA: driver for VESA chipsets: vesa
[    96.788] (II) [KMS] drm report modesetting isn't supported.
[    96.788] (EE) open /dev/dri/card0: No such file or directory
[    96.788] (WW) Falling back to old probe method for modesetting
[    96.788] (EE) open /dev/dri/card0: No such file or directory
[    96.788] (II) Loading sub module "fbdevhw"
[    96.788] (II) LoadModule: "fbdevhw"
[    96.788] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    96.789] (II) Module fbdevhw: vendor="X.Org Foundation"
[    96.789]     compiled for 1.21.1.4, module version = 0.0.2
[    96.789]     ABI class: X.Org Video Driver, version 25.2
[    96.789] (EE) Unable to find a valid framebuffer device
[    96.789] (WW) Falling back to old probe method for fbdev
[    96.789] (II) Loading sub module "fbdevhw"
[    96.789] (II) LoadModule: "fbdevhw"
[    96.789] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    96.789] (II) Module fbdevhw: vendor="X.Org Foundation"
[    96.789]     compiled for 1.21.1.4, module version = 0.0.2
[    96.789]     ABI class: X.Org Video Driver, version 25.2
[    96.789] (II) FBDEV(3): using default device
[    96.789] (EE) Screen 0 deleted because of no matching config section.
[    96.789] (II) UnloadModule: "radeon"
[    96.789] (EE) Screen 0 deleted because of no matching config section.
[    96.789] (II) UnloadModule: "modesetting"
[    96.789] (EE) Screen 0 deleted because of no matching config section.
[    96.789] (II) UnloadModule: "fbdev"
[    96.789] (II) UnloadSubModule: "fbdevhw"
[    96.789] (EE) 
Fatal server error:
[    96.789] (EE) Cannot run in framebuffer mode. Please specify busIDs        for all framebuffer devices
[    96.789] (EE) 
[    96.789] (EE) 
Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[    96.789] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    96.789] (EE) 
[    96.808] (EE) Server terminated with error (1). Closing log file.

```

Please just tell me frankly if there is a way I can use this card in an acceptable way (also without graphic acceleration and using a resolution of at least 1024x768), or if I need to take the dumb way: buy a new video card that works with linux, in this case I accept suggestions to choose a linux-friendly, not-expensive, video card. Please tell me if you need further info (logs, commands output, and so on)

Thanks in advance!
magowiz

---

### Post by mikewhatever on 2022-12-17
So, what happens with the default settings (vga=792 nomodeset removed) on 22.10? Is it static or black screen? Does xserver restart help?

---

### Post by Yellow Pasque on 2022-12-17
```
sudo apt-get remove xserver-xorg-video-fbdev
```

^That should allow the vesa driver to load. Or you could make an xorg.conf file that specifies vesa.

---

### Post by magowiz82 on 2023-01-02
What I tried and which is current status:
1. I removed from grub configuration the settings @mikewhatever told me
2. I uninstalled `xserver-xorg-video-fbdev` like @Yellow Pasque told me
3. I moved my `xorg.conf` to another file, to have an empty one and all automatic configuration

What I get:
- splash screen now runs at a decent resolution
- xorg server starts with static effect
- then starts again correctly but with 640x480 resolution (gdm3/gnome-shell)

How can I try to make a minimal xorg.conf that uses vesa and for example uses a 1024x768? Are there some tiny examples of this?

UPDATE: also using mine `xorg.conf` that is attached I get a resolution of 640x480:
```

Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "Accel"                  # [<bool>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "EnablePageFlip"         # [<bool>]
        #Option     "SubPixelOrder"          # [<str>]
        #Option     "ZaphodHeads"            # <str>
        #Option     "AccelMethod"            # <str>
        #Option     "DRI3"                   # [<bool>]
        #Option     "DRI"                    # <i>
        #Option     "ShadowPrimary"          # [<bool>]
        #Option     "TearFree"               # [<bool>]
        #Option     "DeleteUnusedDP12Displays"     # [<bool>]
        #Option     "VariableRefresh"        # [<bool>]
        #Option     "AsyncFlipSecondaries"     # [<bool>]
    Identifier  "Card0"
    Driver      "vesa"
    BusID       "PCI:0:1:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

```

---

### Post by Yellow Pasque on 2023-01-02
You didn't give an updated Xorg log, so it's hard for me to say what's going wrong. You shouldn't need any xorg.conf at all. Just boot with 'nomodeset' and the vesa driver should be selected automatically if fbdev is not present.

---

### Post by magowiz82 on 2023-01-05
yesI'm sorry about that. Oh you mean with "modeset" passed as kernel argument? I understood the opposite, sorry. Also moving away xorg.conf and putting "nomodeset" as kernel argument I still get low resolution problem.

Here it is the log without xorg.conf and with "nomodeset" as kernel parameter:
[https://paste.ubuntu.com/p/FgySTFpZf3/](https://paste.ubuntu.com/p/FgySTFpZf3/) 

(I had to use paste site because is long)

---

### Post by Yellow Pasque on 2023-01-10
Sorry for late response. I've got life/work things and I haven't been feeling well. But I think this may be the key:
```
[   103.740] (WW) VESA(0): Unable to estimate virtual size
[   103.748] (II) VESA(0): Virtual size is 720x480 (pitch 720)
```

So you'll have to manually specify virtual size. Maybe create a file /etc/X11/xorg.conf.d/00-virtual.conf with:
```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	SubSection	"Display"
		Depth 	24
		Virtual 1680 1050
		Modes  "1680x1050"
	EndSubSection
EndSection
```

---

### Post by magowiz82 on 2023-01-11
> **Yellow Pasque said:**
> Sorry for late response. I've got life/work things and I haven't been feeling well. But I think this may be the key:
```
[   103.740] (WW) VESA(0): Unable to estimate virtual size
[   103.748] (II) VESA(0): Virtual size is 720x480 (pitch 720)
```

So you'll have to manually specify virtual size. Maybe create a file /etc/X11/xorg.conf.d/00-virtual.conf with:
```
Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
    SubSection    "Display"
        Depth     24
        Virtual 1680 1050
        Modes  "1680x1050"
    EndSubSection
EndSection
```

First of all I think I have to thank people every time in an open source community, someone finds time to help me, so you don't have to apologize and I have to say "thanks". I'm also slow responding for the same motivation: work, other things in my life, so I can understand, and I hope you are better now.

I tried to do what you said, creating that file with the content you suggested, unfortunately, now xorg doesn't start at all: I can see only blinking cursor and black screen.

Here it is the log:
```

[   110.703] (--) Log file renamed from "/var/log/Xorg.pid-1631.log" to "/var/log/Xorg.0.log"
[   110.704] 
X.Org X Server 1.21.1.4
X Protocol Version 11, Revision 0
[   110.704] Current Operating System: Linux liano 5.19.0-28-generic #29-Ubuntu SMP PREEMPT_DYNAMIC Thu Dec 15 09:37:06 UTC 2022 x86_64
[   110.704] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-5.19.0-28-generic root=UUID=acd61f09-2fc9-4a54-bf0b-23f0a297d2e4 ro quiet splash nomodeset vt.handoff=7
[   110.705] xorg-server 2:21.1.4-2ubuntu1.3 (For technical support please see http://www.ubuntu.com/support) 
[   110.705] Current version of pixman: 0.40.0
[   110.705]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[   110.705] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   110.706] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Jan 12 00:21:02 2023
[   110.706] (==) Using config directory: "/etc/X11/xorg.conf.d"
[   110.707] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   110.707] (==) No Layout section.  Using the first Screen section.
[   110.707] (**) |-->Screen "Default Screen" (0)
[   110.707] (**) |   |-->Monitor "<default monitor>"
[   110.708] (==) No monitor specified for screen "Default Screen".
    Using a default monitor configuration.
[   110.708] (==) Automatically adding devices
[   110.709] (==) Automatically enabling devices
[   110.709] (==) Automatically adding GPU devices
[   110.709] (==) Automatically binding GPU devices
[   110.709] (==) Max clients allowed: 256, resource mask: 0x1fffff
[   110.710] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   110.710]     Entry deleted from font path.
[   110.710] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   110.710]     Entry deleted from font path.
[   110.710] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   110.710]     Entry deleted from font path.
[   110.711] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   110.711]     Entry deleted from font path.
[   110.711] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   110.711]     Entry deleted from font path.
[   110.711] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[   110.711] (==) ModulePath set to "/usr/lib/xorg/modules"
[   110.712] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[   110.712] (II) Loader magic: 0x55b4faf4a020
[   110.712] (II) Module ABI versions:
[   110.712]     X.Org ANSI C Emulation: 0.4
[   110.712]     X.Org Video Driver: 25.2
[   110.712]     X.Org XInput driver : 24.4
[   110.713]     X.Org Server Extension : 10.0
[   110.715] (++) using VT number 1

[   110.720] (II) systemd-logind: took control of session /org/freedesktop/login1/session/c6
[   110.724] (--) PCI:*(0@0:1:0) 1002:9645:1043:84c8 rev 0, Mem @ 0xc0000000/268435456, 0xfeb00000/262144, I/O @ 0x0000f000/256, BIOS @ 0x????????/131072
[   110.724] (II) LoadModule: "glx"
[   110.725] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   110.727] (II) Module glx: vendor="X.Org Foundation"
[   110.727]     compiled for 1.21.1.4, module version = 1.0.0
[   110.727]     ABI class: X.Org Server Extension, version 10.0
[   110.727] (==) Matched ati as autoconfigured driver 0
[   110.727] (==) Matched modesetting as autoconfigured driver 1
[   110.727] (==) Matched fbdev as autoconfigured driver 2
[   110.728] (==) Matched vesa as autoconfigured driver 3
[   110.728] (==) Assigned the driver to the xf86ConfigLayout
[   110.728] (II) LoadModule: "ati"
[   110.728] (WW) Warning, couldn't open module ati
[   110.729] (EE) Failed to load module "ati" (module does not exist, 0)
[   110.729] (II) LoadModule: "modesetting"
[   110.729] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[   110.730] (II) Module modesetting: vendor="X.Org Foundation"
[   110.730]     compiled for 1.21.1.4, module version = 1.21.1
[   110.730]     Module class: X.Org Video Driver
[   110.730]     ABI class: X.Org Video Driver, version 25.2
[   110.730] (II) LoadModule: "fbdev"
[   110.731] (WW) Warning, couldn't open module fbdev
[   110.731] (EE) Failed to load module "fbdev" (module does not exist, 0)
[   110.731] (II) LoadModule: "vesa"
[   110.731] (WW) Warning, couldn't open module vesa
[   110.732] (EE) Failed to load module "vesa" (module does not exist, 0)
[   110.732] (==) Matched ati as autoconfigured driver 0
[   110.732] (==) Matched modesetting as autoconfigured driver 1
[   110.732] (==) Matched fbdev as autoconfigured driver 2
[   110.732] (==) Matched vesa as autoconfigured driver 3
[   110.732] (==) Assigned the driver to the xf86ConfigLayout
[   110.732] (II) LoadModule: "ati"
[   110.733] (WW) Warning, couldn't open module ati
[   110.733] (EE) Failed to load module "ati" (module does not exist, 0)
[   110.733] (II) LoadModule: "modesetting"
[   110.734] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[   110.734] (II) Module modesetting: vendor="X.Org Foundation"
[   110.734]     compiled for 1.21.1.4, module version = 1.21.1
[   110.734]     Module class: X.Org Video Driver
[   110.735]     ABI class: X.Org Video Driver, version 25.2
[   110.735] (II) UnloadModule: "modesetting"
[   110.735] (II) Unloading modesetting
[   110.735] (II) Failed to load module "modesetting" (already loaded, 0)
[   110.735] (II) LoadModule: "fbdev"
[   110.736] (WW) Warning, couldn't open module fbdev
[   110.736] (EE) Failed to load module "fbdev" (module does not exist, 0)
[   110.736] (II) LoadModule: "vesa"
[   110.736] (WW) Warning, couldn't open module vesa
[   110.737] (EE) Failed to load module "vesa" (module does not exist, 0)
[   110.737] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[   110.738] (EE) open /dev/dri/card0: No such file or directory
[   110.738] (WW) Falling back to old probe method for modesetting
[   110.738] (EE) open /dev/dri/card0: No such file or directory
[   110.738] (EE) Screen 0 deleted because of no matching config section.
[   110.738] (II) UnloadModule: "modesetting"
[   110.739] (EE) Device(s) detected, but none match those in the config file.
[   110.739] (EE) 
Fatal server error:
[   110.739] (EE) no screens found(EE) 
[   110.739] (EE) 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[   110.740] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[   110.740] (EE) 
[   110.755] (EE) Server terminated with error (1). Closing log file.

```

---

### Post by #&amp;thj^% on 2023-01-11
for now see if this will allow you to see your GUI
```
sudo rm -rf  /etc/X11/xorg.conf.d/00-virtual.conf
```
You still have a copy of it here if needed.
Now reboot

---

### Post by magowiz82 on 2023-09-30
> **1fallen said:**
> for now see if this will allow you to see your GUI
```
sudo rm -rf  /etc/X11/xorg.conf.d/00-virtual.conf
```
You still have a copy of it here if needed.
Now reboot

no it didn't worked, I almost gave up with this video card, also reporting a bug on freedesktop.org show to me that kernel people doesn't care too much about mine particular apu/gpu (and this is understandable because we are talking about a GPU with 10 or more years old) or it is hard to fix, I keep mine ubuntu on that computer constantly up to date to see if, in some way, some kernel upgrade will fix it but I doubt about it. I think I will try some live distro to understand if any can run it out of the box, could be funny if, for example, with last ubuntu installation disk this work. :-)

---

### Post by #&amp;thj^% on 2023-09-30
I have it working on Arch with no problems:
```
 inxi -G | grep API
  API: EGL v: 1.5 drivers: nvidia,radeonsi,swrast
  API: OpenGL v: 4.6.0 compat-v: 4.5 vendor: amd mesa v: 23.1.8-arch1.1
inxi -G | grep server
  Display: x11 server: X.Org v: 21.1.8 with: Xwayland v: 23.2.1 driver: X:


```
But the kernel 6.5 breaks X11 on Mantic now. BTW Radeon Pro drivers only support LTS versions.

---

### Post by mikewhatever on 2023-10-01
Ubuntu Mate 20.04 has no issues on AMD A4-3400 with the same Radeon 6410D integrated GPU. Xorg starts and stops, but the machine is too old to use for anything useful.

---

### Post by magowiz82 on 2023-10-01
> **1fallen said:**
> I have it working on Arch with no problems:
```
 inxi -G | grep API
  API: EGL v: 1.5 drivers: nvidia,radeonsi,swrast
  API: OpenGL v: 4.6.0 compat-v: 4.5 vendor: amd mesa v: 23.1.8-arch1.1
inxi -G | grep server
  Display: x11 server: X.Org v: 21.1.8 with: Xwayland v: 23.2.1 driver: X:


```
But the kernel 6.5 breaks X11 on Mantic now. BTW Radeon Pro drivers only support LTS versions.

I'm not sure I understood facts you are telling me, please correct me if I am wrong:
- you are saying that arch works fine with this, good to know, thanks
- you are talking about mantic (new upcoming ubuntu release) and 6.5 kernel: but I'm using ubuntu lunar with kernel 6.2 and it's not working
- Radeon pro drivers only supports LTS versions ?!? Do you mean LTS versions of ubuntu? Which are radeon pro drivers? The ones from kernel radeon module? Otherwise, which others?

Meanwhile I tried also ubuntu live on usb drive on same pc and I got same result I get with mine installed version of ubuntu, so it shouldn't be any configuration issue:
- running try ubuntu I get stuck on static screen
- running low safe graphics mode I got a 640x480 resolution

About 20.04, if it works is ok, but it is going to enter EOL in next 6 months

I'm going to try some live distribution, the 22.04 LTS could be nice if it works, otherwise whatever makes me use my graphic card and hopefully can be used and updated.
I'm listening to any of your kind suggestions, I know I may not know everything about this and I'm open to any other distro/edition even outside ubuntu: arch could be fine.

I think I will try some distribution live on usb pen in order to quickly find what works and what not, tell me if you would use another approach.

Thanks to everyone.

---

### Post by #&amp;thj^% on 2023-10-01
> **magowiz82 said:**
> I'm not sure I understood facts you are telling me, please correct me if I am wrong:
- you are saying that arch works fine with this, good to know, thanks
- you are talking about mantic (new upcoming ubuntu release) and 6.5 kernel: but I'm using ubuntu lunar with kernel 6.2 and it's not working
- Radeon pro drivers only supports LTS versions ?!? Do you mean LTS versions of ubuntu? Which are radeon pro drivers? The ones from kernel radeon module? Otherwise, which others?

Meanwhile I tried also ubuntu live on usb drive on same pc and I got same result I get with mine installed version of ubuntu, so it shouldn't be any configuration issue:
- running try ubuntu I get stuck on static screen
- running low safe graphics mode I got a 640x480 resolution

About 20.04, if it works is ok, but it is going to enter EOL in next 6 months

I'm going to try some live distribution, the 22.04 LTS could be nice if it works, otherwise whatever makes me use my graphic card and hopefully can be used and updated.
I'm listening to any of your kind suggestions, I know I may not know everything about this and I'm open to any other distro/edition even outside ubuntu: arch could be fine.

I think I will try some distribution live on usb pen in order to quickly find what works and what not, tell me if you would use another approach.

Thanks to everyone.
I've not tried the install on 20.4 but 22.04 works partially, meaning it helps just a little more is all.
The kernel amdgpu free driver is lacking the full graphic stack. Nor are they ready to release the full engine just yet. 
They claim it works as good as the Pro Drivers, but that has not been my experience. :(
My first test on this was a very poor score for me, it was around "FPS: 4456 FrameTime: 0.224 ms" that shocked me.
With the Driver:
```
=======================================================
    glmark2 2023.01
=======================================================
    OpenGL Information
    GL_VENDOR:      AMD
    GL_RENDERER:    AMD Radeon Graphics (renoir, LLVM 16.0.6, DRM 3.54, 6.5.5-arch1-1)
    GL_VERSION:     4.6 (Compatibility Profile) Mesa 23.2.1-arch1.1
    Surface Config: buf=32 r=8 g=8 b=8 a=8 depth=24 stencil=0 samples=0
    Surface Size:   800x600 windowed
=======================================================
[build] use-vbo=false: FPS: 8890 FrameTime: 0.112 ms
[build] use-vbo=true: FPS: 10665 FrameTime: 0.094 ms
[texture] texture-filter=nearest: FPS: 8440 FrameTime: 0.118 ms
[texture] texture-filter=linear: FPS: 8422 FrameTime: 0.119 ms
[texture] texture-filter=mipmap: FPS: 7960 FrameTime: 0.126 ms
[shading] shading=gouraud: FPS: 7649 FrameTime: 0.131 ms
[shading] shading=blinn-phong-inf: FPS: 7290 FrameTime: 0.137 ms
[shading] shading=phong: FPS: 7232 FrameTime: 0.138 ms
[shading] shading=cel: FPS: 6921 FrameTime: 0.144 ms
[bump] bump-render=high-poly: FPS: 5069 FrameTime: 0.197 ms
[bump] bump-render=normals: FPS: 10737 FrameTime: 0.093 ms
[bump] bump-render=height: FPS: 11060 FrameTime: 0.090 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 6532 FrameTime: 0.153 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 3082 FrameTime: 0.324 ms
[pulsar] light=false:quads=5:texture=false: FPS: 7548 FrameTime: 0.133 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 3278 FrameTime: 0.305 ms
[desktop] effect=shadow:windows=4: FPS: 6261 FrameTime: 0.160 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 1154 FrameTime: 0.867 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 1975 FrameTime: 0.506 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 1433 FrameTime: 0.698 ms
[ideas] speed=duration: FPS: 5603 FrameTime: 0.178 ms
[jellyfish] <default>: FPS: 4456 FrameTime: 0.224 ms
[terrain] <default>: FPS: 400 FrameTime: 2.505 ms
[shadow] <default>: FPS: 6260 FrameTime: 0.160 ms
[refract] <default>: FPS: 666 FrameTime: 1.502 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 8205 FrameTime: 0.122 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 7721 FrameTime: 0.130 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 7588 FrameTime: 0.132 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 7759 FrameTime: 0.129 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 7643 FrameTime: 0.131 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 7733 FrameTime: 0.129 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 7802 FrameTime: 0.128 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 7755 FrameTime: 0.129 ms
=======================================================
                                  glmark2 Score: 6398 
=======================================================

```
Still not the same as before they opensourced their driver, but little bit better.

***Also I need to correct the fact it breaks X11***, that was my fault I had a bad kernel parameter and a bad "etc/X11/xorg.conf" file.
After fixing those yesterday X11 and Wayland both work now.
IMHO, They really messed up to opensource their driver, without the full graphic stack. (It's just a shame)

---

### Post by magowiz82 on 2023-10-01
just a quick recap to distro from usb I tried: in any case I had poor results: static effect on xorg start or resolution of 640x480:
[LIST]
[*]archlinux, doesn't have gui at all in live disc
[*]so I tried manjaro an archlinux derivate : manjaro-xfce-23.0.2-230919-linux65.iso : static effect both with open source drivers and proprietary ones
[*]slax debian based : slax-64bit-11.6.0.iso, resolution of 640x480
[*]slax slack based: slax-64bit-15.0.1.iso, xorg doesn't start at all
[/LIST]

I'm trying only live usb because I want to be sure that mine card works before trying to install a new distro, and in the meanwhile even for a temporary solution for using that pc at a decent resolution while I found a permanent fix. I think I'm going to try also ubuntu 22.04.

Do you have any live distro to suggest me?

---

### Post by #&amp;thj^% on 2023-10-01
Seems you tried most of the top ones.

 AMD's term for a chip that combines both a CPU and an integrated GPU in a single package.
Is how they word it to me.
These cards or Chips are poorly supported:
[list][*]Raven Ridge: AMD's 2018 line of APUs, including chips named Athlon 2x0GE or 3000G and Ryzen 2x00G, 2x00GE, 2x00H or 2x00U.

[*]Picasso: AMD's 2019 line of APUs, including chips named Athlon 300GE or 300U, and Ryzen 3x00G, 3x00GE, 3x50H or 3x00U. 

[*]Renoir: AMD's 2020 line of APUs, initially including chips named Ryzen 4x00H or 4x00U. [/list]
All of these use Vega graphics.
If you use the Raven Ridge a possible work around is a kernel setting "amdgpu.noretry=0" EDIT: It's been a few years now but this is worth a shot on your live
Trials is "noapic" at boot.
But I've not had to use that kernel setting.

---

### Post by magowiz82 on 2023-10-02
> **1fallen said:**
> Seems you tried most of the top ones.

 AMD's term for a chip that combines both a CPU and an integrated GPU in a single package.
Is how they word it to me.
These cards or Chips are poorly supported:
[LIST]
[*]Raven Ridge: AMD's 2018 line of APUs, including chips named Athlon 2x0GE or 3000G and Ryzen 2x00G, 2x00GE, 2x00H or 2x00U. 
[*]Picasso: AMD's 2019 line of APUs, including chips named Athlon 300GE or 300U, and Ryzen 3x00G, 3x00GE, 3x50H or 3x00U. 
[*]Renoir: AMD's 2020 line of APUs, initially including chips named Ryzen 4x00H or 4x00U. 
[/LIST]
All of these use Vega graphics.
If you use the Raven Ridge a possible work around is a kernel setting "amdgpu.noretry=0" EDIT: It's been a few years now but this is worth a shot on your live
Trials is "noapic" at boot.
But I've not had to use that kernel setting.

Hi 1fallen,
I tried both kernel commandline options (not together, one at time), with no luck.
I have to say that I have an APU older than the one you are listing, mine is : 
```
AMD A4-3300 APU with Radeon(tm) HD Graphics
```
and as you can see here: [https://www.amd.com/en/support/apu/amd-series-processors/amd-a4-series-apu-for-desktops/a4-3300-radeon-hd-6410d](https://www.amd.com/en/support/apu/amd-series-processors/amd-a4-series-apu-for-desktops/a4-3300-radeon-hd-6410d) , latest available driver for linux was released on 2015, so for sure is not compatible with latest distributions/kernels and I have to rely on some opensource driver and settings.

---

### Post by mikewhatever on 2023-10-02
So, I got curious and tested Xubuntu 23.10 beta, kernel 6.5. It worked with the default radeon kernel module. GUI desktop got loaded. There was no need to configure vesa or anything else. OpenGL 4.5 is now supported with mesa 23, as oppesed to Opengl 3.3 before that.
I suspect the problem may not be the GPU, at least not in general. Perhaps your specific GPU or something else is faulty, I am not sure, but it does no look like a common reproducable problem.

---

