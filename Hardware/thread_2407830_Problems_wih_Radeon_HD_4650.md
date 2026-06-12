---
title: "Problems wih Radeon HD 4650"
date: 2018-12-10
forum: Hardware
---

### Post by mekschr on 2018-12-10
I have a problem about screen resolution. I have tried different distributions already, all of them have the same problem. My monitor is "Samsung Syncmaster B1930N" and my GPU is "ATI Radeon HD 4650". The problem is that I can't set the resolution to anything except 640x480, 800x600 and 1024x768, according to Samsung's website, my monitor's resolution is 1366x768.

---

### Post by Autodave on 2018-12-10
You may want to look at this and see if your card can be used with this driver.  AMD: [https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)

---

### Post by slickymaster on 2018-12-10
Thread moved to **Hardware** for a better fit

---

### Post by Yellow Pasque on 2018-12-10
Please copy/past the /var/log/Xorg.0.log (use code tags as it's a lot of text)

> You may want to look at this and see if your card can be used with this driver. AMD: [https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)

Dead end. This card is too old to work with a proprietary driver on any modern (i.e. supported) version of Ubuntu. Nowadays, the open-source radeon driver should work better than that old proprietary mess anyways.

---

### Post by mekschr on 2018-12-10
Alright
```
[    43.976] 
X.Org X Server 1.19.6
Release Date: 2017-12-20
[    43.976] X Protocol Version 11, Revision 0
[    43.976] Build Operating System: Linux 4.4.0-138-generic x86_64 Ubuntu
[    43.976] Current Operating System: Linux mekschr-945GCM-S2L 4.15.0-42-generic #45-Ubuntu SMP Thu Nov 15 19:32:57 UTC 2018 x86_64
[    43.976] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.15.0-42-generic root=UUID=40c61ce3-a40d-4864-9371-c6a792b4f9b3 ro quiet splash vt.handoff=1
[    43.976] Build Date: 25 October 2018  04:11:27PM
[    43.976] xorg-server 2:1.19.6-1ubuntu4.2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    43.976] Current version of pixman: 0.34.0
[    43.976]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    43.976] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    43.976] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Dec 10 20:28:54 2018
[    44.083] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    44.215] (==) No Layout section.  Using the first Screen section.
[    44.215] (==) No screen section available. Using defaults.
[    44.215] (**) |-->Screen "Default Screen Section" (0)
[    44.216] (**) |   |-->Monitor "<default monitor>"
[    44.245] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    44.245] (==) Automatically adding devices
[    44.245] (==) Automatically enabling devices
[    44.245] (==) Automatically adding GPU devices
[    44.246] (==) Automatically binding GPU devices
[    44.246] (==) Max clients allowed: 256, resource mask: 0x1fffff
[    44.366] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    44.366]     Entry deleted from font path.
[    44.366] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    44.366]     Entry deleted from font path.
[    44.366] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    44.366]     Entry deleted from font path.
[    44.376] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    44.376]     Entry deleted from font path.
[    44.376] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    44.376]     Entry deleted from font path.
[    44.376] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    44.376] (==) ModulePath set to "/usr/lib/xorg/modules"
[    44.376] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    44.391] (II) Loader magic: 0x5613fb429020
[    44.391] (II) Module ABI versions:
[    44.391]     X.Org ANSI C Emulation: 0.4
[    44.391]     X.Org Video Driver: 23.0
[    44.391]     X.Org XInput driver : 24.1
[    44.391]     X.Org Server Extension : 10.0
[    44.392] (++) using VT number 7

[    44.392] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
[    44.393] (II) xfree86: Adding drm device (/dev/dri/card0)
[    44.397] (--) PCI:*(0:1:0:0) 1002:9498:1002:1002 rev 0, Mem @ 0xd0000000/268435456, 0xe1000000/65536, I/O @ 0x00009000/256, BIOS @ 0x????????/131072
[    44.397] (II) LoadModule: "glx"
[    44.440] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    45.069] (II) Module glx: vendor="X.Org Foundation"
[    45.069]     compiled for 1.19.6, module version = 1.0.0
[    45.069]     ABI class: X.Org Server Extension, version 10.0
[    45.069] (II) Applying OutputClass "Radeon" to /dev/dri/card0
[    45.069]     loading driver: radeon
[    45.069] (==) Matched radeon as autoconfigured driver 0
[    45.069] (==) Matched ati as autoconfigured driver 1
[    45.069] (==) Matched ati as autoconfigured driver 2
[    45.069] (==) Matched modesetting as autoconfigured driver 3
[    45.070] (==) Matched fbdev as autoconfigured driver 4
[    45.070] (==) Matched vesa as autoconfigured driver 5
[    45.070] (==) Assigned the driver to the xf86ConfigLayout
[    45.070] (II) LoadModule: "radeon"
[    45.115] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    45.358] (II) Module radeon: vendor="X.Org Foundation"
[    45.358]     compiled for 1.19.6, module version = 18.0.1
[    45.358]     Module class: X.Org Video Driver
[    45.358]     ABI class: X.Org Video Driver, version 23.0
[    45.358] (II) LoadModule: "ati"
[    45.358] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    45.378] (II) Module ati: vendor="X.Org Foundation"
[    45.378]     compiled for 1.19.6, module version = 18.0.1
[    45.378]     Module class: X.Org Video Driver
[    45.378]     ABI class: X.Org Video Driver, version 23.0
[    45.441] (II) LoadModule: "modesetting"
[    45.442] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    45.476] (II) Module modesetting: vendor="X.Org Foundation"
[    45.476]     compiled for 1.19.6, module version = 1.19.6
[    45.476]     Module class: X.Org Video Driver
[    45.476]     ABI class: X.Org Video Driver, version 23.0
[    45.476] (II) LoadModule: "fbdev"
[    45.477] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    45.514] (II) Module fbdev: vendor="X.Org Foundation"
[    45.514]     compiled for 1.19.3, module version = 0.4.4
[    45.514]     Module class: X.Org Video Driver
[    45.514]     ABI class: X.Org Video Driver, version 23.0
[    45.514] (II) LoadModule: "vesa"
[    45.514] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    45.545] (II) Module vesa: vendor="X.Org Foundation"
[    45.545]     compiled for 1.19.3, module version = 2.3.4
[    45.545]     Module class: X.Org Video Driver
[    45.545]     ABI class: X.Org Video Driver, version 23.0
[    45.545] (II) RADEON: Driver for ATI/AMD Radeon chipsets:
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
[    45.551] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    45.551] (II) FBDEV: driver for framebuffer: fbdev
[    45.551] (II) VESA: driver for VESA chipsets: vesa
[    45.575] (II) [KMS] Kernel modesetting enabled.
[    45.575] (WW) Falling back to old probe method for modesetting
[    45.575] (WW) Falling back to old probe method for fbdev
[    45.575] (II) Loading sub module "fbdevhw"
[    45.575] (II) LoadModule: "fbdevhw"
[    45.575] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    45.618] (II) Module fbdevhw: vendor="X.Org Foundation"
[    45.618]     compiled for 1.19.6, module version = 0.0.2
[    45.618]     ABI class: X.Org Video Driver, version 23.0
[    45.618] (WW) Falling back to old probe method for vesa
[    45.618] (II) RADEON(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    45.618] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    45.618] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    45.618] (==) RADEON(0): Default visual is TrueColor
[    45.618] (==) RADEON(0): RGB weight 888
[    45.618] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    45.618] (--) RADEON(0): Chipset: "ATI RV730 PRO [Radeon HD 4650]" (ChipID = 0x9498)
[    45.619] (II) Loading sub module "fb"
[    45.619] (II) LoadModule: "fb"
[    45.619] (II) Loading /usr/lib/xorg/modules/libfb.so
[    45.682] (II) Module fb: vendor="X.Org Foundation"
[    45.682]     compiled for 1.19.6, module version = 1.0.0
[    45.682]     ABI class: X.Org ANSI C Emulation, version 0.4
[    45.682] (II) Loading sub module "dri2"
[    45.682] (II) LoadModule: "dri2"
[    45.682] (II) Module "dri2" already built-in
[    45.682] (II) Loading sub module "glamoregl"
[    45.682] (II) LoadModule: "glamoregl"
[    45.682] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[    45.836] (II) Module glamoregl: vendor="X.Org Foundation"
[    45.836]     compiled for 1.19.6, module version = 1.0.0
[    45.836]     ABI class: X.Org ANSI C Emulation, version 0.4
[    45.836] (II) glamor: OpenGL accelerated X.org driver based.
[    47.278] (II) glamor: EGL version 1.5 (DRI2):
[    47.346] (II) RADEON(0): glamor detected, initialising EGL layer.
[    47.354] (II) RADEON(0): KMS Color Tiling: enabled
[    47.354] (II) RADEON(0): KMS Color Tiling 2D: enabled
[    47.354] (==) RADEON(0): TearFree property default: auto
[    47.354] (II) RADEON(0): KMS Pageflipping: enabled
[    47.373] (II) RADEON(0): Output DVI-0 has no monitor section
[    47.404] (II) RADEON(0): Output DisplayPort-0 has no monitor section
[    47.436] (II) RADEON(0): Output DisplayPort-1 has no monitor section
[    47.453] (II) RADEON(0): EDID for output DVI-0
[    47.453] (II) RADEON(0): Printing probed modes for output DVI-0
[    47.453] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    47.453] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    47.453] (II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    47.453] (II) RADEON(0): Modeline "848x480"x60.0   33.75  848 864 976 1088  480 486 494 517 +hsync +vsync (31.0 kHz e)
[    47.453] (II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    47.484] (II) RADEON(0): EDID for output DisplayPort-0
[    47.516] (II) RADEON(0): EDID for output DisplayPort-1
[    47.516] (II) RADEON(0): Output DVI-0 connected
[    47.516] (II) RADEON(0): Output DisplayPort-0 disconnected
[    47.516] (II) RADEON(0): Output DisplayPort-1 disconnected
[    47.516] (II) RADEON(0): Using exact sizes for initial modes
[    47.516] (II) RADEON(0): Output DVI-0 using initial mode 1024x768 +0+0
[    47.516] (II) RADEON(0): mem size init: gart size :3fdde000 vram size: s:40000000 visible:f9b3000
[    47.516] (==) RADEON(0): DPI set to (96, 96)
[    47.516] (==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
[    47.516] (II) Loading sub module "ramdac"
[    47.516] (II) LoadModule: "ramdac"
[    47.516] (II) Module "ramdac" already built-in
[    47.516] (II) UnloadModule: "modesetting"
[    47.516] (II) Unloading modesetting
[    47.516] (II) UnloadModule: "fbdev"
[    47.516] (II) Unloading fbdev
[    47.516] (II) UnloadSubModule: "fbdevhw"
[    47.516] (II) Unloading fbdevhw
[    47.516] (II) UnloadModule: "vesa"
[    47.516] (II) Unloading vesa
[    47.516] (--) Depth 24 pixmap format is 32 bpp
[    47.523] (II) RADEON(0): [DRI2] Setup complete
[    47.523] (II) RADEON(0): [DRI2]   DRI driver: r600
[    47.523] (II) RADEON(0): [DRI2]   VDPAU driver: r600
[    47.523] (II) RADEON(0): Front buffer size: 3072K
[    47.523] (II) RADEON(0): VRAM usage limit set to 227329K
[    47.524] (II) RADEON(0): SYNC extension fences enabled
[    47.525] (II) RADEON(0): Present extension enabled
[    47.525] (==) RADEON(0): DRI3 enabled
[    47.525] (==) RADEON(0): Backing store enabled
[    47.525] (II) RADEON(0): Direct rendering enabled
[    47.601] (II) RADEON(0): Use GLAMOR acceleration.
[    47.601] (II) RADEON(0): Acceleration enabled
[    47.601] (==) RADEON(0): DPMS enabled
[    47.601] (==) RADEON(0): Silken mouse enabled
[    47.601] (II) RADEON(0): Set up textured video (glamor)
[    47.601] (II) RADEON(0): [XvMC] Associated with GLAMOR Textured Video.
[    47.601] (II) RADEON(0): [XvMC] Extension initialized.
[    47.601] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    47.602] (--) RandR disabled
[    47.635] (II) SELinux: Disabled on system
[    47.639] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    47.639] (II) AIGLX: enabled GLX_ARB_create_context
[    47.639] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    47.639] (II) AIGLX: enabled GLX_EXT_create_context_es{,2}_profile
[    47.639] (II) AIGLX: enabled GLX_INTEL_swap_event
[    47.639] (II) AIGLX: enabled GLX_SGI_swap_control
[    47.639] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[    47.639] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[    47.639] (II) AIGLX: enabled GLX_EXT_fbconfig_packed_float
[    47.639] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    47.639] (II) AIGLX: enabled GLX_ARB_create_context_robustness
[    47.642] (II) AIGLX: Loaded and initialized r600
[    47.642] (II) GLX: Initialized DRI2 GL provider for screen 0
[    47.662] (II) RADEON(0): Setting screen physical size to 270 x 203
[    47.989] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    47.989] (**) Power Button: Applying InputClass "libinput keyboard catchall"
[    47.989] (II) LoadModule: "libinput"
[    48.011] (II) Loading /usr/lib/xorg/modules/input/libinput_drv.so
[    48.038] (II) Module libinput: vendor="X.Org Foundation"
[    48.039]     compiled for 1.19.6, module version = 0.27.1
[    48.039]     Module class: X.Org XInput Driver
[    48.039]     ABI class: X.Org XInput driver, version 24.1
[    48.039] (II) Using input driver 'libinput' for 'Power Button'
[    48.039] (**) Power Button: always reports core events
[    48.039] (**) Option "Device" "/dev/input/event1"
[    48.039] (**) Option "_source" "server/udev"
[    48.040] (II) event1  - Power Button: is tagged by udev as: Keyboard
[    48.040] (II) event1  - Power Button: device is a keyboard
[    48.040] (II) event1  - Power Button: device removed
[    48.060] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    48.060] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    48.060] (**) Option "xkb_model" "pc105"
[    48.060] (**) Option "xkb_layout" "us"
[    48.061] (II) event1  - Power Button: is tagged by udev as: Keyboard
[    48.061] (II) event1  - Power Button: device is a keyboard
[    48.062] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    48.062] (**) Power Button: Applying InputClass "libinput keyboard catchall"
[    48.062] (II) Using input driver 'libinput' for 'Power Button'
[    48.062] (**) Power Button: always reports core events
[    48.062] (**) Option "Device" "/dev/input/event0"
[    48.062] (**) Option "_source" "server/udev"
[    48.063] (II) event0  - Power Button: is tagged by udev as: Keyboard
[    48.063] (II) event0  - Power Button: device is a keyboard
[    48.063] (II) event0  - Power Button: device removed
[    48.076] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    48.076] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    48.076] (**) Option "xkb_model" "pc105"
[    48.076] (**) Option "xkb_layout" "us"
[    48.077] (II) event0  - Power Button: is tagged by udev as: Keyboard
[    48.077] (II) event0  - Power Button: device is a keyboard
[    48.078] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=3 (/dev/input/event5)
[    48.078] (II) No input driver specified, ignoring this device.
[    48.078] (II) This device may have been added with another device file.
[    48.079] (II) config/udev: Adding input device HDA Intel Line Out (/dev/input/event9)
[    48.079] (II) No input driver specified, ignoring this device.
[    48.079] (II) This device may have been added with another device file.
[    48.080] (II) config/udev: Adding input device HDA Intel Front Headphone (/dev/input/event10)
[    48.080] (II) No input driver specified, ignoring this device.
[    48.080] (II) This device may have been added with another device file.
[    48.081] (II) config/udev: Adding input device HDA Intel Front Mic (/dev/input/event6)
[    48.081] (II) No input driver specified, ignoring this device.
[    48.081] (II) This device may have been added with another device file.
[    48.082] (II) config/udev: Adding input device HDA Intel Rear Mic (/dev/input/event7)
[    48.082] (II) No input driver specified, ignoring this device.
[    48.082] (II) This device may have been added with another device file.
[    48.083] (II) config/udev: Adding input device HDA Intel Line (/dev/input/event8)
[    48.083] (II) No input driver specified, ignoring this device.
[    48.083] (II) This device may have been added with another device file.
[    48.084] (II) config/udev: Adding input device USB USB Keykoard (/dev/input/event2)
[    48.084] (**) USB USB Keykoard: Applying InputClass "libinput keyboard catchall"
[    48.084] (II) Using input driver 'libinput' for 'USB USB Keykoard'
[    48.084] (**) USB USB Keykoard: always reports core events
[    48.084] (**) Option "Device" "/dev/input/event2"
[    48.084] (**) Option "_source" "server/udev"
[    48.085] (II) event2  - USB USB Keykoard: is tagged by udev as: Keyboard
[    48.085] (II) event2  - USB USB Keykoard: device is a keyboard
[    48.086] (II) event2  - USB USB Keykoard: device removed
[    48.104] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/0003:1C4F:0002.0001/input/input3/event2"
[    48.104] (II) XINPUT: Adding extended input device "USB USB Keykoard" (type: KEYBOARD, id 8)
[    48.104] (**) Option "xkb_model" "pc105"
[    48.104] (**) Option "xkb_layout" "us"
[    48.105] (II) event2  - USB USB Keykoard: is tagged by udev as: Keyboard
[    48.105] (II) event2  - USB USB Keykoard: device is a keyboard
[    48.107] (II) config/udev: Adding input device USB USB Keykoard (/dev/input/event3)
[    48.107] (**) USB USB Keykoard: Applying InputClass "libinput keyboard catchall"
[    48.107] (II) Using input driver 'libinput' for 'USB USB Keykoard'
[    48.107] (**) USB USB Keykoard: always reports core events
[    48.107] (**) Option "Device" "/dev/input/event3"
[    48.107] (**) Option "_source" "server/udev"
[    48.108] (II) event3  - USB USB Keykoard: is tagged by udev as: Keyboard
[    48.108] (II) event3  - USB USB Keykoard: device is a keyboard
[    48.109] (II) event3  - USB USB Keykoard: device removed
[    48.128] (II) libinput: USB USB Keykoard: needs a virtual subdevice
[    48.128] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.1/0003:1C4F:0002.0002/input/input4/event3"
[    48.128] (II) XINPUT: Adding extended input device "USB USB Keykoard" (type: MOUSE, id 9)
[    48.128] (**) Option "AccelerationScheme" "none"
[    48.128] (**) USB USB Keykoard: (accel) selected scheme none/0
[    48.128] (**) USB USB Keykoard: (accel) acceleration factor: 2.000
[    48.128] (**) USB USB Keykoard: (accel) acceleration threshold: 4
[    48.129] (II) event3  - USB USB Keykoard: is tagged by udev as: Keyboard
[    48.129] (II) event3  - USB USB Keykoard: device is a keyboard
[    48.131] (II) config/udev: Adding input device USB OPTICAL MOUSE  (/dev/input/event4)
[    48.131] (**) USB OPTICAL MOUSE : Applying InputClass "libinput pointer catchall"
[    48.131] (II) Using input driver 'libinput' for 'USB OPTICAL MOUSE '
[    48.131] (**) USB OPTICAL MOUSE : always reports core events
[    48.131] (**) Option "Device" "/dev/input/event4"
[    48.131] (**) Option "_source" "server/udev"
[    48.188] (II) event4  - USB OPTICAL MOUSE : is tagged by udev as: Mouse
[    48.188] (II) event4  - USB OPTICAL MOUSE : device is a pointer
[    48.188] (II) event4  - USB OPTICAL MOUSE : device removed
[    48.220] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.0/0003:0101:0007.0003/input/input5/event4"
[    48.220] (II) XINPUT: Adding extended input device "USB OPTICAL MOUSE " (type: MOUSE, id 10)
[    48.220] (**) Option "AccelerationScheme" "none"
[    48.220] (**) USB OPTICAL MOUSE : (accel) selected scheme none/0
[    48.220] (**) USB OPTICAL MOUSE : (accel) acceleration factor: 2.000
[    48.220] (**) USB OPTICAL MOUSE : (accel) acceleration threshold: 4
[    48.280] (II) event4  - USB OPTICAL MOUSE : is tagged by udev as: Mouse
[    48.280] (II) event4  - USB OPTICAL MOUSE : device is a pointer
[    48.282] (II) config/udev: Adding input device USB OPTICAL MOUSE  (/dev/input/mouse0)
[    48.282] (II) No input driver specified, ignoring this device.
[    48.282] (II) This device may have been added with another device file.
[    48.296] (**) USB USB Keykoard: Applying InputClass "libinput keyboard catchall"
[    48.296] (II) Using input driver 'libinput' for 'USB USB Keykoard'
[    48.297] (**) USB USB Keykoard: always reports core events
[    48.297] (**) Option "Device" "/dev/input/event3"
[    48.297] (**) Option "_source" "_driver/libinput"
[    48.297] (II) libinput: USB USB Keykoard: is a virtual subdevice
[    48.297] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.1/0003:1C4F:0002.0002/input/input4/event3"
[    48.297] (II) XINPUT: Adding extended input device "USB USB Keykoard" (type: KEYBOARD, id 11)
[    48.297] (**) Option "xkb_model" "pc105"
[    48.297] (**) Option "xkb_layout" "us"

```

---

