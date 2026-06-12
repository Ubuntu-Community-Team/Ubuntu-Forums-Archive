---
title: "Radeon driver does not load after upgrade to 17.10"
date: 2018-01-13
forum: Hardware
---

### Post by lamerman on 2018-01-13
The radeon module stopped loading after system updated from 17.04 to 17.10. My videocard is

```

lspci -k | grep -EA3 'VGA' 
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Curacao XT / Trinidad XT [Radeon R7 370 / R9 270X/370X]
        Subsystem: ASUSTeK Computer Inc. Curacao XT / Trinidad XT [Radeon R7 370 / R9 270X/370X]
        Kernel modules: radeon, amdgpu
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Cape Verde/Pitcairn HDMI Audio [Radeon HD 7700/7800 Series]

```

```
uname -a
Linux lamerman 4.13.0-25-generic #29-Ubuntu SMP Mon Jan 8 21:14:41 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

```

As I can see, the error is

```
[     6.653] (EE) open /dev/dri/card0: No such file or directory

```

Xorg log:


```
[     6.559] (--) Log file renamed from "/var/log/Xorg.pid-983.log" to "/var/log/Xorg.0.log"
[     6.561] 
X.Org X Server 1.19.5
Release Date: 2017-10-12
[     6.561] X Protocol Version 11, Revision 0
[     6.561] Build Operating System: Linux 4.4.0-97-generic x86_64 Ubuntu
[     6.561] Current Operating System: Linux lamerman 4.13.0-25-generic #29-Ubuntu SMP Mon Jan 8 21:14:41 UTC 2018 x86_64
[     6.561] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.13.0-25-generic root=UUID=741f8cd5-0b39-4848-bad4-10c99d66c417 ro quiet splash vt.handoff=7
[     6.561] Build Date: 15 October 2017  05:51:19PM
[     6.561] xorg-server 2:1.19.5-0ubuntu2 (For technical support please see http://www.ubuntu.com/support) 
[     6.561] Current version of pixman: 0.34.0
[     6.561]    Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
[     6.561] Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     6.561] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Jan 13 08:23:56 2018
[     6.562] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     6.567] (==) No Layout section.  Using the first Screen section.
[     6.567] (==) No screen section available. Using defaults.
[     6.567] (**) |-->Screen "Default Screen Section" (0)
[     6.567] (**) |   |-->Monitor "<default monitor>"
[     6.568] (==) No monitor specified for screen "Default Screen Section".
        Using a default monitor configuration.
[     6.568] (==) Automatically adding devices
[     6.568] (==) Automatically enabling devices
[     6.568] (==) Automatically adding GPU devices
[     6.568] (==) Automatically binding GPU devices
[     6.568] (==) Max clients allowed: 256, resource mask: 0x1fffff
[     6.571] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     6.571]    Entry deleted from font path.
[     6.571] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     6.571]    Entry deleted from font path.
[     6.571] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     6.571]    Entry deleted from font path.
[     6.571] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     6.571]    Entry deleted from font path.
[     6.571] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     6.571]    Entry deleted from font path.
[     6.571] (==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/Type1,
        built-ins
[     6.571] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     6.571] (II) The server relies on udev to provide the list of input devices.
        If no devices become available, reconfigure udev or disable AutoAddDevices.
[     6.571] (II) Loader magic: 0x55af13fbf020
[     6.571] (II) Module ABI versions:
[     6.571]    X.Org ANSI C Emulation: 0.4
[     6.571]    X.Org Video Driver: 23.0
[     6.571]    X.Org XInput driver : 24.1
[     6.571]    X.Org Server Extension : 10.0
[     6.572] (++) using VT number 7


[     6.572] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
[     6.573] (--) PCI:*(0:1:0:0) 1002:6810:1043:04a1 rev 0, Mem @ 0xd0000000/268435456, 0xfe980000/262144, I/O @ 0x0000b000/256, BIOS @ 0x????????/131072
[     6.573] (II) LoadModule: "glx"
[     6.574] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[     6.581] (II) Module glx: vendor="X.Org Foundation"
[     6.581]    compiled for 1.19.5, module version = 1.0.0
[     6.581]    ABI class: X.Org Server Extension, version 10.0
[     6.581] (==) Matched ati as autoconfigured driver 0
[     6.581] (==) Matched modesetting as autoconfigured driver 1
[     6.581] (==) Matched fbdev as autoconfigured driver 2
[     6.581] (==) Matched vesa as autoconfigured driver 3
[     6.581] (==) Assigned the driver to the xf86ConfigLayout
[     6.581] (II) LoadModule: "ati"
[     6.581] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[     6.581] (II) Module ati: vendor="X.Org Foundation"
[     6.581]    compiled for 1.19.3, module version = 7.10.0
[     6.581]    Module class: X.Org Video Driver
[     6.581]    ABI class: X.Org Video Driver, version 23.0
[     6.644] (II) LoadModule: "radeon"
[     6.645] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[     6.648] (II) Module radeon: vendor="X.Org Foundation"
[     6.648]    compiled for 1.19.3, module version = 7.10.0
[     6.648]    Module class: X.Org Video Driver
[     6.648]    ABI class: X.Org Video Driver, version 23.0
[     6.648] (II) LoadModule: "modesetting"
[     6.649] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[     6.649] (II) Module modesetting: vendor="X.Org Foundation"
[     6.649]    compiled for 1.19.5, module version = 1.19.5
[     6.649]    Module class: X.Org Video Driver
[     6.649]    ABI class: X.Org Video Driver, version 23.0
[     6.649] (II) LoadModule: "fbdev"
[     6.649] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     6.650] (II) Module fbdev: vendor="X.Org Foundation"
[     6.650]    compiled for 1.19.3, module version = 0.4.4
[     6.650]    Module class: X.Org Video Driver
[     6.650]    ABI class: X.Org Video Driver, version 23.0
[     6.650] (II) LoadModule: "vesa"
[     6.650] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     6.650] (II) Module vesa: vendor="X.Org Foundation"
[     6.650]    compiled for 1.19.3, module version = 2.3.4
[     6.650]    Module class: X.Org Video Driver
[     6.650]    ABI class: X.Org Video Driver, version 23.0
[     6.650] (II) RADEON: Driver for ATI/AMD Radeon chipsets:
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
[     6.652] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[     6.652] (II) FBDEV: driver for framebuffer: fbdev
[     6.652] (II) VESA: driver for VESA chipsets: vesa
[     6.653] (II) [KMS] drm report modesetting isn't supported.
[     6.653] (EE) open /dev/dri/card0: No such file or directory
[     6.653] (WW) Falling back to old probe method for modesetting
[     6.653] (EE) open /dev/dri/card0: No such file or directory
[     6.653] (II) Loading sub module "fbdevhw"
[     6.653] (II) LoadModule: "fbdevhw"
[     6.653] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[     6.653] (II) Module fbdevhw: vendor="X.Org Foundation"
[     6.653]    compiled for 1.19.5, module version = 0.0.2
[     6.653]    ABI class: X.Org Video Driver, version 23.0
[     6.653] (**) FBDEV(2): claimed PCI slot 1@0:0:0
[     6.653] (II) FBDEV(2): using default device
[     6.653] (WW) Falling back to old probe method for vesa
[     6.653] (EE) Screen 0 deleted because of no matching config section.
[     6.653] (II) UnloadModule: "radeon"
[     6.653] (EE) Screen 0 deleted because of no matching config section.
[     6.653] (II) UnloadModule: "modesetting"
[     6.653] (II) FBDEV(0): Creating default Display subsection in Screen section
        "Default Screen Section" for depth/fbbpp 24/32
[     6.653] (==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
[     6.653] (==) FBDEV(0): RGB weight 888
[     6.653] (==) FBDEV(0): Default visual is TrueColor
[     6.653] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[     6.653] (II) FBDEV(0): hardware: VESA VGA (video memory: 14400kB)
[     6.653] (II) FBDEV(0): checking modes against framebuffer device...
[     6.653] (II) FBDEV(0): checking modes against monitor...
[     6.653] (--) FBDEV(0): Virtual size is 2560x1440 (pitch 2560)
[     6.653] (**) FBDEV(0):  Built-in mode "current": 368.7 MHz, 135.6 kHz, 92.6 Hz
[     6.653] (II) FBDEV(0): Modeline "current"x0.0  368.73  2560 2592 2656 2720  1440 1444 1448 1464 -hsync -vsync -csync (135.6 kHz b)
[     6.653] (==) FBDEV(0): DPI set to (96, 96)
[     6.653] (II) Loading sub module "fb"
[     6.653] (II) LoadModule: "fb"
[     6.653] (II) Loading /usr/lib/xorg/modules/libfb.so
[     6.654] (II) Module fb: vendor="X.Org Foundation"
[     6.654]    compiled for 1.19.5, module version = 1.0.0
[     6.654]    ABI class: X.Org ANSI C Emulation, version 0.4
[     6.654] (**) FBDEV(0): using shadow framebuffer
[     6.654] (II) Loading sub module "shadow"
[     6.654] (II) LoadModule: "shadow"
[     6.654] (II) Loading /usr/lib/xorg/modules/libshadow.so
[     6.655] (II) Module shadow: vendor="X.Org Foundation"
[     6.655]    compiled for 1.19.5, module version = 1.1.0
[     6.655]    ABI class: X.Org ANSI C Emulation, version 0.4
[     6.655] (II) UnloadModule: "vesa"
[     6.655] (II) Unloading vesa
[     6.655] (==) Depth 24 pixmap format is 32 bpp
[     6.655] (II) FBDEV(0): FBIOBLANK: Invalid argument (Screen blanking not supported by kernel - disabling)
[     6.656] (==) FBDEV(0): Backing store enabled
[     6.657] (==) FBDEV(0): DPMS enabled
[     6.657] (==) RandR enabled
[     6.660] (II) SELinux: Disabled on system
[     6.660] (II) AIGLX: Screen 0 is not DRI2 capable
[     6.660] (EE) AIGLX: reverting to software rendering
[     6.787] (II) IGLX: enabled GLX_MESA_copy_sub_buffer
[     6.788] (II) IGLX: Loaded and initialized swrast
[     6.788] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[     6.839] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[     6.839] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     6.839] (**) Power Button: Applying InputClass "libinput keyboard catchall"
[     6.839] (II) LoadModule: "libinput"
[     6.839] (II) Loading /usr/lib/xorg/modules/input/libinput_drv.so
[     6.843] (II) Module libinput: vendor="X.Org Foundation"
[     6.843]    compiled for 1.19.3, module version = 0.25.0
[     6.843]    Module class: X.Org XInput Driver
[     6.843]    ABI class: X.Org XInput driver, version 24.1
[     6.843] (II) Using input driver 'libinput' for 'Power Button'
[     6.843] (**) Power Button: always reports core events
[     6.843] (**) Option "Device" "/dev/input/event1"
[     6.843] (**) Option "_source" "server/udev"
[     6.843] (II) event1  - (II) Power Button: (II) is tagged by udev as: Keyboard
[     6.843] (II) event1  - (II) Power Button: (II) device is a keyboard
[     6.843] (II) event1  - (II) Power Button: (II) device removed
[     6.868] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[     6.868] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[     6.868] (**) Option "xkb_model" "pc105"
[     6.868] (**) Option "xkb_layout" "us,ru"
[     6.868] (**) Option "xkb_variant" ","
[     6.868] (**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
[     6.889] (II) event1  - (II) Power Button: (II) is tagged by udev as: Keyboard
[     6.889] (II) event1  - (II) Power Button: (II) device is a keyboard
[     6.889] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[     6.889] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     6.889] (**) Power Button: Applying InputClass "libinput keyboard catchall"
[     6.889] (II) Using input driver 'libinput' for 'Power Button'
[     6.889] (**) Power Button: always reports core events
[     6.889] (**) Option "Device" "/dev/input/event0"
[     6.889] (**) Option "_source" "server/udev"
[     6.889] (II) event0  - (II) Power Button: (II) is tagged by udev as: Keyboard
[     6.889] (II) event0  - (II) Power Button: (II) device is a keyboard
[     6.889] (II) event0  - (II) Power Button: (II) device removed
[     6.920] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[     6.920] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[     6.920] (**) Option "xkb_model" "pc105"
[     6.920] (**) Option "xkb_layout" "us,ru"
[     6.920] (**) Option "xkb_variant" ","
[     6.920] (**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
[     6.920] (II) event0  - (II) Power Button: (II) is tagged by udev as: Keyboard
[     6.920] (II) event0  - (II) Power Button: (II) device is a keyboard
[     6.920] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=11 (/dev/input/event10)
[     6.920] (II) No input driver specified, ignoring this device.
[     6.920] (II) This device may have been added with another device file.
[     6.921] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=3 (/dev/input/event5)
[     6.921] (II) No input driver specified, ignoring this device.
[     6.921] (II) This device may have been added with another device file.
[     6.921] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=7 (/dev/input/event6)
[     6.921] (II) No input driver specified, ignoring this device.
[     6.921] (II) This device may have been added with another device file.
[     6.921] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=8 (/dev/input/event7)
[     6.921] (II) No input driver specified, ignoring this device.
[     6.921] (II) This device may have been added with another device file.
[     6.921] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=9 (/dev/input/event8)
[     6.921] (II) No input driver specified, ignoring this device.
[     6.921] (II) This device may have been added with another device file.
[     6.922] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=10 (/dev/input/event9)
[     6.922] (II) No input driver specified, ignoring this device.
[     6.922] (II) This device may have been added with another device file.
[     6.922] (II) config/udev: Adding input device A4TECH USB Device (/dev/input/event3)
[     6.922] (**) A4TECH USB Device: Applying InputClass "evdev keyboard catchall"
[     6.922] (**) A4TECH USB Device: Applying InputClass "libinput keyboard catchall"
[     6.922] (II) Using input driver 'libinput' for 'A4TECH USB Device'
[     6.922] (**) A4TECH USB Device: always reports core events
[     6.922] (**) Option "Device" "/dev/input/event3"
[     6.922] (**) Option "_source" "server/udev"
[     6.922] (II) event3  - (II) A4TECH USB Device: (II) is tagged by udev as: Keyboard
[     6.922] (II) event3  - (II) A4TECH USB Device: (II) device is a keyboard
[     6.922] (II) event3  - (II) A4TECH USB Device: (II) device removed
[     6.940] (II) libinput: A4TECH USB Device: needs a virtual subdevice
[     6.940] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.2/usb1/1-4/1-4.3/1-4.3:1.0/0003:09DA:9090.0002/input/input3/event3"
[     6.940] (II) XINPUT: Adding extended input device "A4TECH USB Device" (type: MOUSE, id 8)
[     6.940] (**) Option "AccelerationScheme" "none"
[     6.940] (**) A4TECH USB Device: (accel) selected scheme none/0
[     6.940] (**) A4TECH USB Device: (accel) acceleration factor: 2.000
[     6.940] (**) A4TECH USB Device: (accel) acceleration threshold: 4
[     6.940] (II) event3  - (II) A4TECH USB Device: (II) is tagged by udev as: Keyboard
[     6.940] (II) event3  - (II) A4TECH USB Device: (II) device is a keyboard
[     6.941] (II) config/udev: Adding input device A4TECH USB Device (/dev/input/event4)
[     6.941] (**) A4TECH USB Device: Applying InputClass "evdev pointer catchall"
[     6.941] (**) A4TECH USB Device: Applying InputClass "libinput pointer catchall"
[     6.941] (II) Using input driver 'libinput' for 'A4TECH USB Device'
[     6.941] (**) A4TECH USB Device: always reports core events
[     6.941] (**) Option "Device" "/dev/input/event4"
[     6.941] (**) Option "_source" "server/udev"
[     7.000] (II) event4  - (II) A4TECH USB Device: (II) is tagged by udev as: Mouse
[     7.000] (II) event4  - (II) A4TECH USB Device: (II) device is a pointer
[     7.000] (II) event4  - (II) A4TECH USB Device: (II) device removed
[     7.032] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.2/usb1/1-4/1-4.3/1-4.3:1.1/0003:09DA:9090.0003/input/input4/event4"
[     7.032] (II) XINPUT: Adding extended input device "A4TECH USB Device" (type: MOUSE, id 9)
[     7.032] (**) Option "AccelerationScheme" "none"
[     7.032] (**) A4TECH USB Device: (accel) selected scheme none/0
[     7.032] (**) A4TECH USB Device: (accel) acceleration factor: 2.000
[     7.032] (**) A4TECH USB Device: (accel) acceleration threshold: 4
[     7.092] (II) event4  - (II) A4TECH USB Device: (II) is tagged by udev as: Mouse
[     7.092] (II) event4  - (II) A4TECH USB Device: (II) device is a pointer
[     7.092] (II) config/udev: Adding input device A4TECH USB Device (/dev/input/mouse0)
[     7.092] (II) No input driver specified, ignoring this device.
[     7.092] (II) This device may have been added with another device file.
[     7.092] (II) config/udev: Adding input device HDA ATI SB Front Mic (/dev/input/event11)
[     7.092] (II) No input driver specified, ignoring this device.
[     7.092] (II) This device may have been added with another device file.
[     7.093] (II) config/udev: Adding input device HDA ATI SB Rear Mic (/dev/input/event12)
[     7.093] (II) No input driver specified, ignoring this device.
[     7.093] (II) This device may have been added with another device file.
[     7.093] (II) config/udev: Adding input device HDA ATI SB Line (/dev/input/event13)
[     7.093] (II) No input driver specified, ignoring this device.
[     7.093] (II) This device may have been added with another device file.
[     7.093] (II) config/udev: Adding input device HDA ATI SB Line Out (/dev/input/event14)
[     7.093] (II) No input driver specified, ignoring this device.
[     7.093] (II) This device may have been added with another device file.
[     7.093] (II) config/udev: Adding input device HDA ATI SB Front Headphone (/dev/input/event15)
[     7.093] (II) No input driver specified, ignoring this device.
[     7.093] (II) This device may have been added with another device file.
[     7.094] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[     7.094] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[     7.094] (**) AT Translated Set 2 keyboard: Applying InputClass "libinput keyboard catchall"
[     7.094] (II) Using input driver 'libinput' for 'AT Translated Set 2 keyboard'
[     7.094] (**) AT Translated Set 2 keyboard: always reports core events
[     7.094] (**) Option "Device" "/dev/input/event2"
[     7.094] (**) Option "_source" "server/udev"
[     7.094] (II) event2  - (II) AT Translated Set 2 keyboard: (II) is tagged by udev as: Keyboard
[     7.094] (II) event2  - (II) AT Translated Set 2 keyboard: (II) device is a keyboard
[     7.094] (II) event2  - (II) AT Translated Set 2 keyboard: (II) device removed
[     7.108] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"




```

What could be wrong?

---

### Post by QIII on 2018-01-14
Hello!

Would you please post the results of 

```
lsmod | grep amdgpu
```

If your card has recently been added to AMD's supported hardware, amdgpu may be present while radeon is not.

---

### Post by lamerman on 2018-01-14
I reinstalled 17.10 from scratch and the radeon driver started to work properly. I remember that after upgrade I had the amdgpu module running and radeon not. The amdgpu module does not support my card.
Currently on a working system I have them both running.

---

