---
title: "Xrandr screen corruption 1280x720 ASUS X55YA 17.04"
date: 2017-07-22
forum: Hardware
---

### Post by ukbeast on 2017-07-22
My native resolution is 1366x768 and a game I like playing is 1280x720. 
gaps between boxes, text etc.

  xrandr centre fixes it, but I'd like it stretched if possible.

```
 inxi
CPU~Quad  core AMD A6-7310 APU with AMD Radeon R4 Graphics (-MCP-)  speed/max~1200/2000 MHz Kernel~4.12.3-041203-generic x86_64 Up~7:18  Mem~2571.8/6898.7MB HDD~1000.2GB(1.1% used) Procs~182 Client~Shell  inxi~2.3.8  

```

```
[    28.406] (--) Log file renamed from "/var/log/Xorg.pid-1019.log" to "/var/log/Xorg.0.log"
[    28.411] 
X.Org X Server 1.19.3
Release Date: 2017-03-15
[    28.411] X Protocol Version 11, Revision 0
[    28.411] Build Operating System: Linux 4.4.0-70-generic x86_64 Ubuntu
[    28.411] Current Operating System: Linux  4.12.3-041203-generic #201707210343 SMP Fri Jul 21 07:45:26 UTC 2017 x86_64
[    28.411] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.12.3-041203-generic root=UUID=f3e37d21-2685-4bc7-9bda-19f94f33ec03 ro quiet splash vt.handoff=7
[    28.411] Build Date: 28 March 2017  06:16:52AM
[    28.411] xorg-server 2:1.19.3-1ubuntu1 (For technical support please see http://www.ubuntu.com/support) 
[    28.411] Current version of pixman: 0.34.0
[    28.411]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    28.412] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    28.412] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Jul 22 13:56:03 2017
[    28.464] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    28.494] (==) No Layout section.  Using the first Screen section.
[    28.494] (==) No screen section available. Using defaults.
[    28.494] (**) |-->Screen "Default Screen Section" (0)
[    28.494] (**) |   |-->Monitor "<default monitor>"
[    28.514] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    28.514] (==) Automatically adding devices
[    28.514] (==) Automatically enabling devices
[    28.514] (==) Automatically adding GPU devices
[    28.514] (==) Automatically binding GPU devices
[    28.514] (==) Max clients allowed: 256, resource mask: 0x1fffff
[    28.555] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    28.555]     Entry deleted from font path.
[    28.555] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    28.555]     Entry deleted from font path.
[    28.555] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    28.555]     Entry deleted from font path.
[    28.556] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    28.556]     Entry deleted from font path.
[    28.556] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    28.556]     Entry deleted from font path.
[    28.556] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    28.556] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    28.556] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    28.556] (II) Loader magic: 0x940d1f8020
[    28.556] (II) Module ABI versions:
[    28.556]     X.Org ANSI C Emulation: 0.4
[    28.556]     X.Org Video Driver: 23.0
[    28.556]     X.Org XInput driver : 24.1
[    28.556]     X.Org Server Extension : 10.0
[    28.558] (++) using VT number 7

[    28.558] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
[    28.559] (II) xfree86: Adding drm device (/dev/dri/card0)
[    28.563] (--) PCI:*(0:0:1:0) 1002:9851:1043:1b9d rev 64, Mem @ 0xe0000000/268435456, 0xf0000000/8388608, 0xfea00000/262144, I/O @ 0x0000f000/256, BIOS @ 0x????????/131072
[    28.563] (II) LoadModule: "glx"
[    28.612] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    28.802] (II) Module glx: vendor="X.Org Foundation"
[    28.802]     compiled for 1.19.3, module version = 1.0.0
[    28.802]     ABI class: X.Org Server Extension, version 10.0
[    28.802] (II) Applying OutputClass "Radeon" to /dev/dri/card0
[    28.802]     loading driver: radeon
[    28.802] (==) Matched radeon as autoconfigured driver 0
[    28.802] (==) Matched ati as autoconfigured driver 1
[    28.802] (==) Matched ati as autoconfigured driver 2
[    28.802] (==) Matched modesetting as autoconfigured driver 3
[    28.802] (==) Matched fbdev as autoconfigured driver 4
[    28.802] (==) Matched vesa as autoconfigured driver 5
[    28.802] (==) Assigned the driver to the xf86ConfigLayout
[    28.802] (II) LoadModule: "radeon"
[    28.812] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    28.852] (II) Module radeon: vendor="X.Org Foundation"
[    28.852]     compiled for 1.19.3, module version = 7.9.99
[    28.852]     Module class: X.Org Video Driver
[    28.852]     ABI class: X.Org Video Driver, version 23.0
[    28.852] (II) LoadModule: "ati"
[    28.852] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    28.859] (II) Module ati: vendor="X.Org Foundation"
[    28.859]     compiled for 1.19.3, module version = 7.9.99
[    28.859]     Module class: X.Org Video Driver
[    28.859]     ABI class: X.Org Video Driver, version 23.0
[    28.928] (II) LoadModule: "modesetting"
[    28.928] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    28.946] (II) Module modesetting: vendor="X.Org Foundation"
[    28.946]     compiled for 1.19.3, module version = 1.19.3
[    28.946]     Module class: X.Org Video Driver
[    28.946]     ABI class: X.Org Video Driver, version 23.0
[    28.946] (II) LoadModule: "fbdev"
[    28.946] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    28.956] (II) Module fbdev: vendor="X.Org Foundation"
[    28.956]     compiled for 1.19.3, module version = 0.4.4
[    28.956]     Module class: X.Org Video Driver
[    28.956]     ABI class: X.Org Video Driver, version 23.0
[    28.956] (II) LoadModule: "vesa"
[    28.956] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    28.961] (II) Module vesa: vendor="X.Org Foundation"
[    28.961]     compiled for 1.19.3, module version = 2.3.4
[    28.961]     Module class: X.Org Video Driver
[    28.961]     ABI class: X.Org Video Driver, version 23.0
[    28.961] (II) RADEON: Driver for ATI/AMD Radeon chipsets:
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
[    28.969] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    28.969] (II) FBDEV: driver for framebuffer: fbdev
[    28.969] (II) VESA: driver for VESA chipsets: vesa
[    29.005] (II) [KMS] Kernel modesetting enabled.
[    29.005] (WW) Falling back to old probe method for modesetting
[    29.005] (WW) Falling back to old probe method for fbdev
[    29.005] (II) Loading sub module "fbdevhw"
[    29.005] (II) LoadModule: "fbdevhw"
[    29.006] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    29.021] (II) Module fbdevhw: vendor="X.Org Foundation"
[    29.021]     compiled for 1.19.3, module version = 0.0.2
[    29.021]     ABI class: X.Org Video Driver, version 23.0
[    29.022] (WW) Falling back to old probe method for vesa
[    29.022] (II) RADEON(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    29.022] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    29.022] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    29.022] (==) RADEON(0): Default visual is TrueColor
[    29.022] (==) RADEON(0): RGB weight 888
[    29.022] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    29.022] (--) RADEON(0): Chipset: "MULLINS" (ChipID = 0x9851)
[    29.022] (II) Loading sub module "fb"
[    29.022] (II) LoadModule: "fb"
[    29.023] (II) Loading /usr/lib/xorg/modules/libfb.so
[    29.024] (II) Module fb: vendor="X.Org Foundation"
[    29.024]     compiled for 1.19.3, module version = 1.0.0
[    29.024]     ABI class: X.Org ANSI C Emulation, version 0.4
[    29.024] (II) Loading sub module "dri2"
[    29.024] (II) LoadModule: "dri2"
[    29.024] (II) Module "dri2" already built-in
[    29.024] (II) Loading sub module "glamoregl"
[    29.024] (II) LoadModule: "glamoregl"
[    29.034] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[    29.118] (II) Module glamoregl: vendor="X.Org Foundation"
[    29.118]     compiled for 1.19.3, module version = 1.0.0
[    29.118]     ABI class: X.Org ANSI C Emulation, version 0.4
[    29.118] (II) glamor: OpenGL accelerated X.org driver based.
[    31.276] (II) glamor: EGL version 1.5 (DRI2):
[    31.400] (II) RADEON(0): glamor detected, initialising EGL layer.
[    31.414] (II) RADEON(0): KMS Color Tiling: enabled
[    31.414] (II) RADEON(0): KMS Color Tiling 2D: enabled
[    31.414] (==) RADEON(0): TearFree property default: auto
[    31.414] (II) RADEON(0): KMS Pageflipping: enabled
[    31.421] (II) RADEON(0): Output eDP has no monitor section
[    31.463] (II) RADEON(0): Output DisplayPort-0 has no monitor section
[    31.470] (II) RADEON(0): EDID for output eDP
[    31.470] (II) RADEON(0): Manufacturer: CMN  Model: 15ca  Serial#: 0
[    31.470] (II) RADEON(0): Year: 2014  Week: 34
[    31.470] (II) RADEON(0): EDID Version: 1.4
[    31.470] (II) RADEON(0): Digital Display Input
[    31.470] (II) RADEON(0): 6 bits per channel
[    31.470] (II) RADEON(0): Digital interface is DisplayPort
[    31.470] (II) RADEON(0): Max Image Size [cm]: horiz.: 34  vert.: 19
[    31.470] (II) RADEON(0): Gamma: 2.20
[    31.470] (II) RADEON(0): No DPMS capabilities specified
[    31.470] (II) RADEON(0): Supported color encodings: RGB 4:4:4 
[    31.470] (II) RADEON(0): First detailed timing is preferred mode
[    31.470] (II) RADEON(0): Preferred mode is native pixel format and refresh rate
[    31.470] (II) RADEON(0): redX: 0.569 redY: 0.332   greenX: 0.328 greenY: 0.581
[    31.470] (II) RADEON(0): blueX: 0.159 blueY: 0.141   whiteX: 0.313 whiteY: 0.329
[    31.470] (II) RADEON(0): Manufacturer's mask: 0
[    31.470] (II) RADEON(0): Supported detailed timing:
[    31.470] (II) RADEON(0): clock: 76.4 MHz   Image Size:  344 x 193 mm
[    31.470] (II) RADEON(0): h_active: 1366  h_sync: 1434  h_sync_end 1479 h_blank_end 1592 h_border: 0
[    31.470] (II) RADEON(0): v_active: 768  v_sync: 772  v_sync_end 779 v_blanking: 800 v_border: 0
[    31.470] (II) RADEON(0):  N156BGE-E42
[    31.470] (II) RADEON(0):  CMN
[    31.470] (II) RADEON(0):  N156BGE-E42
[    31.470] (II) RADEON(0): EDID (in hex):
[    31.470] (II) RADEON(0):     00ffffffffffff000daeca1500000000
[    31.470] (II) RADEON(0):     221801049522137802c3c59155549428
[    31.471] (II) RADEON(0):     24505400000001010101010101010101
[    31.471] (II) RADEON(0):     010101010101da1d56e250002030442d
[    31.471] (II) RADEON(0):     470058c110000018000000fe004e3135
[    31.471] (II) RADEON(0):     364247452d4534320a20000000fe0043
[    31.471] (II) RADEON(0):     4d4e0a202020202020202020000000fe
[    31.471] (II) RADEON(0):     004e3135364247452d4534320a200055
[    31.471] (II) RADEON(0): Printing probed modes for output eDP
[    31.471] (II) RADEON(0): Modeline "1366x768"x60.0   76.42  1366 1434 1479 1592  768 772 779 800 -hsync -vsync (48.0 kHz eP)
[    31.471] (II) RADEON(0): Modeline "1280x720"x60.0   74.65  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.9 kHz)
[    31.471] (II) RADEON(0): Modeline "1152x768"x59.9   71.95  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.8 kHz)
[    31.471] (II) RADEON(0): Modeline "1024x768"x59.9   63.53  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
[    31.471] (II) RADEON(0): Modeline "800x600"x60.0   38.31  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
[    31.471] (II) RADEON(0): Modeline "848x480"x59.9   31.65  848 872 952 1056  480 483 493 500 -hsync +vsync (30.0 kHz)
[    31.471] (II) RADEON(0): Modeline "720x480"x59.9   26.85  720 744 808 896  480 483 493 500 -hsync +vsync (30.0 kHz)
[    31.471] (II) RADEON(0): Modeline "640x480"x59.9   23.98  640 664 720 800  480 483 487 500 -hsync +vsync (30.0 kHz)
[    31.510] (II) RADEON(0): EDID for output DisplayPort-0
[    31.511] (II) RADEON(0): Output eDP connected
[    31.511] (II) RADEON(0): Output DisplayPort-0 disconnected
[    31.511] (II) RADEON(0): Using exact sizes for initial modes
[    31.511] (II) RADEON(0): Output eDP using initial mode 1366x768 +0+0
[    31.511] (II) RADEON(0): mem size init: gart size :7fb69000 vram size: s:40000000 visible:f4be000
[    31.511] (==) RADEON(0): DPI set to (96, 96)
[    31.511] (==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
[    31.511] (II) Loading sub module "ramdac"
[    31.511] (II) LoadModule: "ramdac"
[    31.511] (II) Module "ramdac" already built-in
[    31.511] (II) UnloadModule: "modesetting"
[    31.511] (II) Unloading modesetting
[    31.511] (II) UnloadModule: "fbdev"
[    31.511] (II) Unloading fbdev
[    31.511] (II) UnloadSubModule: "fbdevhw"
[    31.511] (II) Unloading fbdevhw
[    31.512] (II) UnloadModule: "vesa"
[    31.512] (II) Unloading vesa
[    31.512] (--) Depth 24 pixmap format is 32 bpp
[    31.512] (II) RADEON(0): [DRI2] Setup complete
[    31.512] (II) RADEON(0): [DRI2]   DRI driver: radeonsi
[    31.512] (II) RADEON(0): [DRI2]   VDPAU driver: radeonsi
[    31.512] (II) RADEON(0): Front buffer size: 4224K
[    31.512] (II) RADEON(0): VRAM usage limit set to 221724K
[    31.513] (II) RADEON(0): SYNC extension fences enabled
[    31.514] (II) RADEON(0): Present extension enabled
[    31.514] (==) RADEON(0): DRI3 enabled
[    31.514] (==) RADEON(0): Backing store enabled
[    31.514] (II) RADEON(0): Direct rendering enabled
[    31.839] (II) RADEON(0): Use GLAMOR acceleration.
[    31.839] (II) RADEON(0): Acceleration enabled
[    31.839] (==) RADEON(0): DPMS enabled
[    31.839] (==) RADEON(0): Silken mouse enabled
[    31.839] (II) RADEON(0): Set up textured video (glamor)
[    31.839] (II) RADEON(0): [XvMC] Associated with GLAMOR Textured Video.
[    31.840] (II) RADEON(0): [XvMC] Extension initialized.
[    31.840] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    31.864] (--) RandR disabled
[    31.876] (II) SELinux: Disabled on system
[    31.880] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    31.880] (II) AIGLX: enabled GLX_ARB_create_context
[    31.880] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    31.880] (II) AIGLX: enabled GLX_EXT_create_context_es{,2}_profile
[    31.880] (II) AIGLX: enabled GLX_INTEL_swap_event
[    31.880] (II) AIGLX: enabled GLX_SGI_swap_control
[    31.880] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[    31.880] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[    31.880] (II) AIGLX: enabled GLX_EXT_fbconfig_packed_float
[    31.880] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    31.880] (II) AIGLX: enabled GLX_ARB_create_context_robustness
[    31.884] (II) AIGLX: Loaded and initialized radeonsi
[    31.884] (II) GLX: Initialized DRI2 GL provider for screen 0
[    31.927] (II) RADEON(0): Setting screen physical size to 361 x 203
[    33.103] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    33.103] (**) Power Button: Applying InputClass "libinput keyboard catchall"
[    33.103] (II) LoadModule: "libinput"
[    33.103] (II) Loading /usr/lib/xorg/modules/input/libinput_drv.so
[    33.154] (II) Module libinput: vendor="X.Org Foundation"
[    33.154]     compiled for 1.19.3, module version = 0.25.0
[    33.154]     Module class: X.Org XInput Driver
[    33.154]     ABI class: X.Org XInput driver, version 24.1
[    33.154] (II) Using input driver 'libinput' for 'Power Button'
[    33.154] (**) Power Button: always reports core events
[    33.155] (**) Option "Device" "/dev/input/event3"
[    33.155] (**) Option "_source" "server/udev"
[    33.156] (II) input device 'Power Button', /dev/input/event3 is tagged by udev as: Keyboard
[    33.156] (II) input device 'Power Button', /dev/input/event3 is a keyboard
[    33.180] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    33.180] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    33.180] (**) Option "xkb_model" "pc105"
[    33.180] (**) Option "xkb_layout" "gb"
[    33.251] (II) input device 'Power Button', /dev/input/event3 is tagged by udev as: Keyboard
[    33.251] (II) input device 'Power Button', /dev/input/event3 is a keyboard
[    33.252] (II) config/udev: Adding input device Asus Wireless Radio Control (/dev/input/event7)
[    33.252] (**) Asus Wireless Radio Control: Applying InputClass "libinput keyboard catchall"
[    33.252] (II) Using input driver 'libinput' for 'Asus Wireless Radio Control'
[    33.252] (**) Asus Wireless Radio Control: always reports core events
[    33.252] (**) Option "Device" "/dev/input/event7"
[    33.252] (**) Option "_source" "server/udev"
[    33.253] (II) input device 'Asus Wireless Radio Control', /dev/input/event7 is tagged by udev as: Keyboard
[    33.253] (II) input device 'Asus Wireless Radio Control', /dev/input/event7 is a keyboard
[    33.272] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/ATK4002:00/input/input14/event7"
[    33.272] (II) XINPUT: Adding extended input device "Asus Wireless Radio Control" (type: KEYBOARD, id 7)
[    33.272] (**) Option "xkb_model" "pc105"
[    33.272] (**) Option "xkb_layout" "gb"
[    33.273] (II) input device 'Asus Wireless Radio Control', /dev/input/event7 is tagged by udev as: Keyboard
[    33.273] (II) input device 'Asus Wireless Radio Control', /dev/input/event7 is a keyboard
[    33.275] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    33.275] (**) Video Bus: Applying InputClass "libinput keyboard catchall"
[    33.275] (II) Using input driver 'libinput' for 'Video Bus'
[    33.275] (**) Video Bus: always reports core events
[    33.275] (**) Option "Device" "/dev/input/event5"
[    33.275] (**) Option "_source" "server/udev"
[    33.276] (II) input device 'Video Bus', /dev/input/event5 is tagged by udev as: Keyboard
[    33.276] (II) input device 'Video Bus', /dev/input/event5 is a keyboard
[    33.296] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input8/event5"
[    33.296] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 8)
[    33.296] (**) Option "xkb_model" "pc105"
[    33.296] (**) Option "xkb_layout" "gb"
[    33.298] (II) input device 'Video Bus', /dev/input/event5 is tagged by udev as: Keyboard
[    33.298] (II) input device 'Video Bus', /dev/input/event5 is a keyboard
[    33.299] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    33.299] (**) Power Button: Applying InputClass "libinput keyboard catchall"
[    33.299] (II) Using input driver 'libinput' for 'Power Button'
[    33.299] (**) Power Button: always reports core events
[    33.299] (**) Option "Device" "/dev/input/event0"
[    33.299] (**) Option "_source" "server/udev"
[    33.300] (II) input device 'Power Button', /dev/input/event0 is tagged by udev as: Keyboard
[    33.300] (II) input device 'Power Button', /dev/input/event0 is a keyboard
[    33.320] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    33.320] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 9)
[    33.320] (**) Option "xkb_model" "pc105"
[    33.320] (**) Option "xkb_layout" "gb"
[    33.322] (II) input device 'Power Button', /dev/input/event0 is tagged by udev as: Keyboard
[    33.322] (II) input device 'Power Button', /dev/input/event0 is a keyboard
[    33.323] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[    33.323] (II) No input driver specified, ignoring this device.
[    33.323] (II) This device may have been added with another device file.
[    33.324] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    33.324] (**) Sleep Button: Applying InputClass "libinput keyboard catchall"
[    33.324] (II) Using input driver 'libinput' for 'Sleep Button'
[    33.324] (**) Sleep Button: always reports core events
[    33.324] (**) Option "Device" "/dev/input/event2"
[    33.324] (**) Option "_source" "server/udev"
[    33.325] (II) input device 'Sleep Button', /dev/input/event2 is tagged by udev as: Keyboard
[    33.325] (II) input device 'Sleep Button', /dev/input/event2 is a keyboard
[    33.344] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2/event2"
[    33.344] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 10)
[    33.344] (**) Option "xkb_model" "pc105"
[    33.344] (**) Option "xkb_layout" "gb"
[    33.345] (II) input device 'Sleep Button', /dev/input/event2 is tagged by udev as: Keyboard
[    33.345] (II) input device 'Sleep Button', /dev/input/event2 is a keyboard
[    33.347] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=3 (/dev/input/event9)
[    33.347] (II) No input driver specified, ignoring this device.
[    33.347] (II) This device may have been added with another device file.
[    33.348] (II) config/udev: Adding input device USB Camera (/dev/input/event8)
[    33.348] (**) USB Camera: Applying InputClass "libinput keyboard catchall"
[    33.348] (II) Using input driver 'libinput' for 'USB Camera'
[    33.348] (**) USB Camera: always reports core events
[    33.348] (**) Option "Device" "/dev/input/event8"
[    33.348] (**) Option "_source" "server/udev"
[    33.349] (II) input device 'USB Camera', /dev/input/event8 is tagged by udev as: Keyboard
[    33.349] (II) input device 'USB Camera', /dev/input/event8 is a keyboard
[    33.384] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input15/event8"
[    33.384] (II) XINPUT: Adding extended input device "USB Camera" (type: KEYBOARD, id 11)
[    33.384] (**) Option "xkb_model" "pc105"
[    33.384] (**) Option "xkb_layout" "gb"
[    33.386] (II) input device 'USB Camera', /dev/input/event8 is tagged by udev as: Keyboard
[    33.386] (II) input device 'USB Camera', /dev/input/event8 is a keyboard
[    33.387] (II) config/udev: Adding input device HD-Audio Generic Mic (/dev/input/event10)
[    33.387] (II) No input driver specified, ignoring this device.
[    33.387] (II) This device may have been added with another device file.
[    33.388] (II) config/udev: Adding input device HD-Audio Generic Headphone (/dev/input/event11)
[    33.388] (II) No input driver specified, ignoring this device.
[    33.388] (II) This device may have been added with another device file.
[    33.389] (II) config/udev: Adding input device Asus WMI hotkeys (/dev/input/event12)
[    33.389] (**) Asus WMI hotkeys: Applying InputClass "libinput keyboard catchall"
[    33.389] (II) Using input driver 'libinput' for 'Asus WMI hotkeys'
[    33.389] (**) Asus WMI hotkeys: always reports core events
[    33.389] (**) Option "Device" "/dev/input/event12"
[    33.389] (**) Option "_source" "server/udev"
[    33.390] (II) input device 'Asus WMI hotkeys', /dev/input/event12 is tagged by udev as: Keyboard
[    33.390] (II) input device 'Asus WMI hotkeys', /dev/input/event12 is a keyboard
[    33.408] (**) Option "config_info" "udev:/sys/devices/platform/asus-nb-wmi/input/input19/event12"
[    33.408] (II) XINPUT: Adding extended input device "Asus WMI hotkeys" (type: KEYBOARD, id 12)
[    33.408] (**) Option "xkb_model" "pc105"
[    33.408] (**) Option "xkb_layout" "gb"
[    33.409] (II) input device 'Asus WMI hotkeys', /dev/input/event12 is tagged by udev as: Keyboard
[    33.409] (II) input device 'Asus WMI hotkeys', /dev/input/event12 is a keyboard
[    33.410] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    33.411] (**) AT Translated Set 2 keyboard: Applying InputClass "libinput keyboard catchall"
[    33.411] (II) Using input driver 'libinput' for 'AT Translated Set 2 keyboard'
[    33.411] (**) AT Translated Set 2 keyboard: always reports core events
[    33.411] (**) Option "Device" "/dev/input/event4"
[    33.411] (**) Option "_source" "server/udev"
[    33.412] (II) input device 'AT Translated Set 2 keyboard', /dev/input/event4 is tagged by udev as: Keyboard
[    33.412] (II) input device 'AT Translated Set 2 keyboard', /dev/input/event4 is a keyboard
[    33.432] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    33.432] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 13)
[    33.432] (**) Option "xkb_model" "pc105"
[    33.432] (**) Option "xkb_layout" "gb"
[    33.434] (II) input device 'AT Translated Set 2 keyboard', /dev/input/event4 is tagged by udev as: Keyboard
[    33.434] (II) input device 'AT Translated Set 2 keyboard', /dev/input/event4 is a keyboard
[    33.435] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/event6)
[    33.435] (**) ETPS/2 Elantech Touchpad: Applying InputClass "libinput touchpad catchall"
[    33.435] (**) ETPS/2 Elantech Touchpad: Applying InputClass "touchpad catchall"
[    33.435] (**) ETPS/2 Elantech Touchpad: Applying InputClass "Default clickpad buttons"
[    33.435] (II) LoadModule: "synaptics"
[    33.436] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    33.450] (II) Module synaptics: vendor="X.Org Foundation"
[    33.450]     compiled for 1.19.3, module version = 1.9.0
[    33.450]     Module class: X.Org XInput Driver
[    33.450]     ABI class: X.Org XInput driver, version 24.1
[    33.450] (II) Using input driver 'synaptics' for 'ETPS/2 Elantech Touchpad'
[    33.450] (**) ETPS/2 Elantech Touchpad: always reports core events
[    33.450] (**) Option "Device" "/dev/input/event6"
[    33.488] (II) synaptics: ETPS/2 Elantech Touchpad: found clickpad property
[    33.488] (--) synaptics: ETPS/2 Elantech Touchpad: x-axis range 0 - 3097 (res 31)
[    33.488] (--) synaptics: ETPS/2 Elantech Touchpad: y-axis range 0 - 2119 (res 32)
[    33.488] (--) synaptics: ETPS/2 Elantech Touchpad: pressure range 0 - 255
[    33.488] (--) synaptics: ETPS/2 Elantech Touchpad: finger width range 0 - 15
[    33.488] (--) synaptics: ETPS/2 Elantech Touchpad: buttons: left double triple
[    33.488] (--) synaptics: ETPS/2 Elantech Touchpad: Vendor 0x2 Product 0xe
[    33.489] (**) Option "SoftButtonAreas" "50% 0 82% 0 0 0 0 0"
[    33.489] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[    33.489] (**) ETPS/2 Elantech Touchpad: always reports core events
[    33.520] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio4/input/input13/event6"
[    33.520] (II) XINPUT: Adding extended input device "ETPS/2 Elantech Touchpad" (type: TOUCHPAD, id 14)
[    33.520] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MinSpeed is now constant deceleration 2.5
[    33.520] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MaxSpeed is now 1.75
[    33.520] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) AccelFactor is now 0.053
[    33.521] (**) ETPS/2 Elantech Touchpad: (accel) keeping acceleration scheme 1
[    33.521] (**) ETPS/2 Elantech Touchpad: (accel) acceleration profile 1
[    33.521] (**) ETPS/2 Elantech Touchpad: (accel) acceleration factor: 2.000
[    33.521] (**) ETPS/2 Elantech Touchpad: (accel) acceleration threshold: 4
[    33.521] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[    33.522] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/mouse0)
[    33.523] (**) ETPS/2 Elantech Touchpad: Ignoring device from InputClass "touchpad ignore duplicates"
[    64.265] (II) RADEON(0): EDID vendor "CMN", prod id 5578
[    64.265] (II) RADEON(0): Printing DDC gathered Modelines:
[    64.265] (II) RADEON(0): Modeline "1366x768"x0.0   76.42  1366 1434 1479 1592  768 772 779 800 -hsync -vsync (48.0 kHz eP)
[    73.237] (II) RADEON(0): EDID vendor "CMN", prod id 5578
[    73.237] (II) RADEON(0): Printing DDC gathered Modelines:
[    73.237] (II) RADEON(0): Modeline "1366x768"x0.0   76.42  1366 1434 1479 1592  768 772 779 800 -hsync -vsync (48.0 kHz eP)
[  7281.744] (II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/mouse1)
[  7281.744] (II) No input driver specified, ignoring this device.
[  7281.744] (II) This device may have been added with another device file.
[  7281.799] (II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/event13)
[  7281.799] (**) Logitech USB Optical Mouse: Applying InputClass "libinput pointer catchall"
[  7281.799] (II) Using input driver 'libinput' for 'Logitech USB Optical Mouse'
[  7281.799] (**) Logitech USB Optical Mouse: always reports core events
[  7281.799] (**) Option "Device" "/dev/input/event13"
[  7281.799] (**) Option "_source" "server/udev"
[  7281.848] (II) input device 'Logitech USB Optical Mouse', /dev/input/event13 is tagged by udev as: Mouse
[  7281.849] (II) input device 'Logitech USB Optical Mouse', /dev/input/event13 is a pointer caps
[  7281.884] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:10.0/usb3/3-2/3-2:1.0/0003:046D:C077.0001/input/input20/event13"
[  7281.884] (II) XINPUT: Adding extended input device "Logitech USB Optical Mouse" (type: MOUSE, id 15)
[  7281.886] (**) Option "AccelerationScheme" "none"
[  7281.886] (**) Logitech USB Optical Mouse: (accel) selected scheme none/0
[  7281.886] (**) Logitech USB Optical Mouse: (accel) acceleration factor: 2.000
[  7281.886] (**) Logitech USB Optical Mouse: (accel) acceleration threshold: 4
[  7281.945] (II) input device 'Logitech USB Optical Mouse', /dev/input/event13 is tagged by udev as: Mouse
[  7281.945] (II) input device 'Logitech USB Optical Mouse', /dev/input/event13 is a pointer caps
[ 18664.851] (II) config/udev: removing device Logitech USB Optical Mouse
[ 18664.869] (II) UnloadModule: "libinput"
[ 23073.319] (II) RADEON(0): Allocate new frame buffer 1280x720 stride 1280
[ 23073.320] (II) RADEON(0): VRAM usage limit set to 222069K
[ 23617.755] (II) RADEON(0): Allocate new frame buffer 1366x768 stride 1408
[ 23617.757] (II) RADEON(0): VRAM usage limit set to 221724K
```

[ATTACH=CONFIG]276105[/ATTACH]

---

