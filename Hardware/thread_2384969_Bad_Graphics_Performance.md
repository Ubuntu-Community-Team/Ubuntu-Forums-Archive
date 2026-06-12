---
title: "Bad Graphics Performance"
date: 2018-02-14
forum: Hardware
---

### Post by maccraft123 on 2018-02-14
I have just installed Lubuntu 16.04 LTS.

I notices a while ago a "llvmpipe" GPU, but i have installed AMD Radeon RX460 2GB, i have installed mesa drivers. On Windows i have around 60FPS capped, but on linux 1-15FPS

---

### Post by maccraft123 on 2018-02-14
Yes, i have done apt update && apt upgrade && apt dist-upgrade
rebooted after it

---

### Post by maccraft123 on 2018-02-14
Apparently graphics vendor shows "VMWare, Inc." :O
I'm running it on *physical* PC

---

### Post by QIII on 2018-02-14
Hello!

Which point release of 16.04 do you have installed?  Have you upgraded the HWE stack?

---

### Post by QIII on 2018-02-14
> **maccraft123 said:**
> Apparently graphics vendor shows "VMWare, Inc." :O
I'm running it on *physical* PC

OK, well *that* is unexpected!

---

### Post by maccraft123 on 2018-02-14
16.04.3 LTS
What is HWE stack?

---

### Post by Yellow Pasque on 2018-02-14
Post the /var/log/Xorg.0.log file.  Use code tags if you copy/paste.

> **QIII said:**
> OK, well *that* is unexpected!

VMWare developed llvmpipe software renderer.

---

### Post by maccraft123 on 2018-02-14
/var/log/Xorg.0.log
```
[   790.358] 
X.Org X Server 1.19.5
Release Date: 2017-10-12
[   790.358] X Protocol Version 11, Revision 0
[   790.358] Build Operating System: Linux 4.4.0-101-generic x86_64 Ubuntu
[   790.358] Current Operating System: Linux maciek-linux 4.13.0-32-generic #35~16.04.1-Ubuntu SMP Thu Jan 25 10:13:43 UTC 2018 x86_64
[   790.358] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.13.0-32-generic root=UUID=12e7c3ba-a6dd-4699-9efc-5df243cce7d2 ro nomodeset quiet splash vt.handoff=7
[   790.358] Build Date: 24 November 2017  09:44:25AM
[   790.358] xorg-server 2:1.19.5-0ubuntu2~16.04.1 (For technical support please see http://www.ubuntu.com/support) 
[   790.358] Current version of pixman: 0.33.6
[   790.358]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[   790.358] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   790.358] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Feb 14 20:36:06 2018
[   790.358] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   790.359] (==) No Layout section.  Using the first Screen section.
[   790.359] (==) No screen section available. Using defaults.
[   790.359] (**) |-->Screen "Default Screen Section" (0)
[   790.359] (**) |   |-->Monitor "<default monitor>"
[   790.359] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[   790.359] (==) Automatically adding devices
[   790.359] (==) Automatically enabling devices
[   790.359] (==) Automatically adding GPU devices
[   790.359] (==) Automatically binding GPU devices
[   790.359] (==) Max clients allowed: 256, resource mask: 0x1fffff
[   790.359] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   790.359]     Entry deleted from font path.
[   790.359] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   790.359]     Entry deleted from font path.
[   790.359] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   790.359]     Entry deleted from font path.
[   790.359] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   790.359]     Entry deleted from font path.
[   790.359] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   790.359]     Entry deleted from font path.
[   790.359] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[   790.359] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   790.359] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[   790.359] (II) Loader magic: 0x55b82e78fe00
[   790.359] (II) Module ABI versions:
[   790.359]     X.Org ANSI C Emulation: 0.4
[   790.359]     X.Org Video Driver: 23.0
[   790.359]     X.Org XInput driver : 24.1
[   790.359]     X.Org Server Extension : 10.0
[   790.360] (++) using VT number 7

[   790.360] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
[   790.361] (--) PCI:*(0:2:0:0) 1002:67ef:1458:22d6 rev 207, Mem @ 0xd0000000/268435456, 0xcfe00000/2097152, 0xfbf80000/262144, I/O @ 0x0000e000/256, BIOS @ 0x????????/131072
[   790.362] (II) LoadModule: "glx"
[   790.362] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   790.363] (II) Module glx: vendor="X.Org Foundation"
[   790.363]     compiled for 1.19.5, module version = 1.0.0
[   790.363]     ABI class: X.Org Server Extension, version 10.0
[   790.363] (==) Matched ati as autoconfigured driver 0
[   790.363] (==) Matched modesetting as autoconfigured driver 1
[   790.363] (==) Matched fbdev as autoconfigured driver 2
[   790.363] (==) Matched vesa as autoconfigured driver 3
[   790.363] (==) Assigned the driver to the xf86ConfigLayout
[   790.363] (II) LoadModule: "ati"
[   790.364] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[   790.364] (II) Module ati: vendor="X.Org Foundation"
[   790.364]     compiled for 1.19.5, module version = 7.10.0
[   790.364]     Module class: X.Org Video Driver
[   790.364]     ABI class: X.Org Video Driver, version 23.0
[   790.434] (II) LoadModule: "radeon"
[   790.435] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[   790.435] (II) Module radeon: vendor="X.Org Foundation"
[   790.435]     compiled for 1.19.5, module version = 7.10.0
[   790.435]     Module class: X.Org Video Driver
[   790.435]     ABI class: X.Org Video Driver, version 23.0
[   790.435] (II) LoadModule: "modesetting"
[   790.435] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[   790.436] (II) Module modesetting: vendor="X.Org Foundation"
[   790.436]     compiled for 1.19.5, module version = 1.19.5
[   790.436]     Module class: X.Org Video Driver
[   790.436]     ABI class: X.Org Video Driver, version 23.0
[   790.436] (II) LoadModule: "fbdev"
[   790.436] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   790.436] (II) Module fbdev: vendor="X.Org Foundation"
[   790.436]     compiled for 1.19.3, module version = 0.4.4
[   790.436]     Module class: X.Org Video Driver
[   790.436]     ABI class: X.Org Video Driver, version 23.0
[   790.436] (II) LoadModule: "vesa"
[   790.437] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   790.437] (II) Module vesa: vendor="X.Org Foundation"
[   790.437]     compiled for 1.19.3, module version = 2.3.4
[   790.437]     Module class: X.Org Video Driver
[   790.437]     ABI class: X.Org Video Driver, version 23.0
[   790.437] (II) RADEON: Driver for ATI/AMD Radeon chipsets:
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
[   790.442] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[   790.442] (II) FBDEV: driver for framebuffer: fbdev
[   790.442] (II) VESA: driver for VESA chipsets: vesa
[   790.461] (EE) open /dev/dri/card0: No such file or directory
[   790.461] (WW) Falling back to old probe method for modesetting
[   790.461] (EE) open /dev/dri/card0: No such file or directory
[   790.461] (II) Loading sub module "fbdevhw"
[   790.461] (II) LoadModule: "fbdevhw"
[   790.462] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   790.462] (II) Module fbdevhw: vendor="X.Org Foundation"
[   790.462]     compiled for 1.19.5, module version = 0.0.2
[   790.462]     ABI class: X.Org Video Driver, version 23.0
[   790.462] (**) FBDEV(1): claimed PCI slot 2@0:0:0
[   790.462] (II) FBDEV(1): using default device
[   790.462] (WW) Falling back to old probe method for vesa
[   790.462] (EE) Screen 0 deleted because of no matching config section.
[   790.462] (II) UnloadModule: "modesetting"
[   790.462] (II) FBDEV(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[   790.462] (==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
[   790.462] (==) FBDEV(0): RGB weight 888
[   790.462] (==) FBDEV(0): Default visual is TrueColor
[   790.462] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[   790.462] (II) FBDEV(0): hardware: VESA VGA (video memory: 4224kB)
[   790.462] (II) FBDEV(0): checking modes against framebuffer device...
[   790.463] (II) FBDEV(0): checking modes against monitor...
[   790.463] (--) FBDEV(0): Virtual size is 1366x768 (pitch 1366)
[   790.463] (**) FBDEV(0):  Built-in mode "current": 104.9 MHz, 60.5 kHz, 76.4 Hz
[   790.463] (II) FBDEV(0): Modeline "current"x0.0  104.92  1366 1398 1566 1734  768 772 776 792 -hsync -vsync -csync (60.5 kHz b)
[   790.463] (==) FBDEV(0): DPI set to (96, 96)
[   790.463] (II) Loading sub module "fb"
[   790.463] (II) LoadModule: "fb"
[   790.463] (II) Loading /usr/lib/xorg/modules/libfb.so
[   790.463] (II) Module fb: vendor="X.Org Foundation"
[   790.463]     compiled for 1.19.5, module version = 1.0.0
[   790.463]     ABI class: X.Org ANSI C Emulation, version 0.4
[   790.463] (**) FBDEV(0): using shadow framebuffer
[   790.463] (II) Loading sub module "shadow"
[   790.463] (II) LoadModule: "shadow"
[   790.463] (II) Loading /usr/lib/xorg/modules/libshadow.so
[   790.463] (II) Module shadow: vendor="X.Org Foundation"
[   790.463]     compiled for 1.19.5, module version = 1.1.0
[   790.463]     ABI class: X.Org ANSI C Emulation, version 0.4
[   790.463] (II) UnloadModule: "radeon"
[   790.464] (II) Unloading radeon
[   790.464] (II) UnloadModule: "vesa"
[   790.464] (II) Unloading vesa
[   790.464] (==) Depth 24 pixmap format is 32 bpp
[   790.464] (II) FBDEV(0): FBIOBLANK: Invalid argument (Screen blanking not supported by kernel - disabling)
[   790.464] (==) FBDEV(0): Backing store enabled
[   790.465] (==) FBDEV(0): DPMS enabled
[   790.465] (==) RandR enabled
[   790.476] (II) SELinux: Disabled on system
[   790.477] (II) AIGLX: Screen 0 is not DRI2 capable
[   790.477] (EE) AIGLX: reverting to software rendering
[   790.511] (II) IGLX: enabled GLX_MESA_copy_sub_buffer
[   790.512] (II) IGLX: Loaded and initialized swrast
[   790.512] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[   790.587] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[   790.587] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   790.587] (II) LoadModule: "evdev"
[   790.587] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   790.588] (II) Module evdev: vendor="X.Org Foundation"
[   790.588]     compiled for 1.19.3, module version = 2.10.5
[   790.588]     Module class: X.Org XInput Driver
[   790.588]     ABI class: X.Org XInput driver, version 24.1
[   790.588] (II) Using input driver 'evdev' for 'Power Button'
[   790.588] (**) Power Button: always reports core events
[   790.588] (**) evdev: Power Button: Device: "/dev/input/event1"
[   790.588] (--) evdev: Power Button: Vendor 0 Product 0x1
[   790.588] (--) evdev: Power Button: Found keys
[   790.588] (II) evdev: Power Button: Configuring as keyboard
[   790.588] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[   790.588] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[   790.588] (**) Option "xkb_rules" "evdev"
[   790.588] (**) Option "xkb_model" "pc105"
[   790.588] (**) Option "xkb_layout" "pl"
[   790.630] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[   790.630] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   790.630] (II) Using input driver 'evdev' for 'Power Button'
[   790.630] (**) Power Button: always reports core events
[   790.630] (**) evdev: Power Button: Device: "/dev/input/event0"
[   790.630] (--) evdev: Power Button: Vendor 0 Product 0x1
[   790.630] (--) evdev: Power Button: Found keys
[   790.630] (II) evdev: Power Button: Configuring as keyboard
[   790.630] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[   790.630] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[   790.630] (**) Option "xkb_rules" "evdev"
[   790.630] (**) Option "xkb_model" "pc105"
[   790.630] (**) Option "xkb_layout" "pl"
[   790.631] (II) config/udev: Adding input device A4TECH USB Device (/dev/input/event2)
[   790.631] (**) A4TECH USB Device: Applying InputClass "evdev keyboard catchall"
[   790.631] (II) Using input driver 'evdev' for 'A4TECH USB Device'
[   790.631] (**) A4TECH USB Device: always reports core events
[   790.631] (**) evdev: A4TECH USB Device: Device: "/dev/input/event2"
[   790.631] (--) evdev: A4TECH USB Device: Vendor 0x9da Product 0x54f
[   790.631] (--) evdev: A4TECH USB Device: Found 1 mouse buttons
[   790.631] (--) evdev: A4TECH USB Device: Found scroll wheel(s)
[   790.631] (--) evdev: A4TECH USB Device: Found relative axes
[   790.631] (II) evdev: A4TECH USB Device: Forcing relative x/y axes to exist.
[   790.631] (--) evdev: A4TECH USB Device: Found absolute axes
[   790.631] (--) evdev: A4TECH USB Device: Found absolute multitouch axes
[   790.631] (--) evdev: A4TECH USB Device: Fake MT device detected
[   790.631] (II) evdev: A4TECH USB Device: Forcing absolute x/y axes to exist.
[   790.631] (--) evdev: A4TECH USB Device: Found keys
[   790.631] (II) evdev: A4TECH USB Device: Configuring as mouse
[   790.631] (II) evdev: A4TECH USB Device: Configuring as keyboard
[   790.631] (II) evdev: A4TECH USB Device: Adding scrollwheel support
[   790.631] (**) evdev: A4TECH USB Device: YAxisMapping: buttons 4 and 5
[   790.631] (**) evdev: A4TECH USB Device: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   790.631] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.0/usb3/3-2/3-2:1.0/0003:09DA:054F.0001/input/input5/event2"
[   790.631] (II) XINPUT: Adding extended input device "A4TECH USB Device" (type: KEYBOARD, id 8)
[   790.631] (**) Option "xkb_rules" "evdev"
[   790.632] (**) Option "xkb_model" "pc105"
[   790.632] (**) Option "xkb_layout" "pl"
[   790.632] (II) evdev: A4TECH USB Device: initialized for relative axes.
[   790.632] (WW) evdev: A4TECH USB Device: ignoring absolute axes.
[   790.632] (**) A4TECH USB Device: (accel) keeping acceleration scheme 1
[   790.632] (**) A4TECH USB Device: (accel) acceleration profile 0
[   790.632] (**) A4TECH USB Device: (accel) acceleration factor: 2.000
[   790.632] (**) A4TECH USB Device: (accel) acceleration threshold: 4
[   790.633] (II) config/udev: Adding input device A4TECH USB Device (/dev/input/event3)
[   790.633] (**) A4TECH USB Device: Applying InputClass "evdev pointer catchall"
[   790.633] (II) Using input driver 'evdev' for 'A4TECH USB Device'
[   790.633] (**) A4TECH USB Device: always reports core events
[   790.633] (**) evdev: A4TECH USB Device: Device: "/dev/input/event3"
[   790.692] (--) evdev: A4TECH USB Device: Vendor 0x9da Product 0x54f
[   790.692] (--) evdev: A4TECH USB Device: Found 20 mouse buttons
[   790.692] (--) evdev: A4TECH USB Device: Found scroll wheel(s)
[   790.692] (--) evdev: A4TECH USB Device: Found relative axes
[   790.692] (--) evdev: A4TECH USB Device: Found x and y relative axes
[   790.692] (II) evdev: A4TECH USB Device: Configuring as mouse
[   790.692] (II) evdev: A4TECH USB Device: Adding scrollwheel support
[   790.692] (**) evdev: A4TECH USB Device: YAxisMapping: buttons 4 and 5
[   790.692] (**) evdev: A4TECH USB Device: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   790.692] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.0/usb3/3-2/3-2:1.1/0003:09DA:054F.0002/input/input6/event3"
[   790.692] (II) XINPUT: Adding extended input device "A4TECH USB Device" (type: MOUSE, id 9)
[   790.692] (II) evdev: A4TECH USB Device: initialized for relative axes.
[   790.693] (**) A4TECH USB Device: (accel) keeping acceleration scheme 1
[   790.693] (**) A4TECH USB Device: (accel) acceleration profile 0
[   790.693] (**) A4TECH USB Device: (accel) acceleration factor: 2.000
[   790.693] (**) A4TECH USB Device: (accel) acceleration threshold: 4
[   790.694] (II) config/udev: Adding input device A4TECH USB Device (/dev/input/mouse0)
[   790.694] (II) No input driver specified, ignoring this device.
[   790.694] (II) This device may have been added with another device file.
[   790.695] (II) config/udev: Adding input device SEM USB Keyboard (/dev/input/event4)
[   790.695] (**) SEM USB Keyboard: Applying InputClass "evdev keyboard catchall"
[   790.695] (II) Using input driver 'evdev' for 'SEM USB Keyboard'
[   790.695] (**) SEM USB Keyboard: always reports core events
[   790.695] (**) evdev: SEM USB Keyboard: Device: "/dev/input/event4"
[   790.695] (--) evdev: SEM USB Keyboard: Vendor 0x1a2c Product 0xe24
[   790.695] (--) evdev: SEM USB Keyboard: Found keys
[   790.695] (II) evdev: SEM USB Keyboard: Configuring as keyboard
[   790.696] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.0/usb3/3-3/3-3:1.0/0003:1A2C:0E24.0003/input/input7/event4"
[   790.696] (II) XINPUT: Adding extended input device "SEM USB Keyboard" (type: KEYBOARD, id 10)
[   790.696] (**) Option "xkb_rules" "evdev"
[   790.696] (**) Option "xkb_model" "pc105"
[   790.696] (**) Option "xkb_layout" "pl"
[   790.698] (II) config/udev: Adding input device SEM USB Keyboard (/dev/input/event5)
[   790.698] (**) SEM USB Keyboard: Applying InputClass "evdev keyboard catchall"
[   790.698] (II) Using input driver 'evdev' for 'SEM USB Keyboard'
[   790.698] (**) SEM USB Keyboard: always reports core events
[   790.698] (**) evdev: SEM USB Keyboard: Device: "/dev/input/event5"
[   790.698] (--) evdev: SEM USB Keyboard: Vendor 0x1a2c Product 0xe24
[   790.698] (--) evdev: SEM USB Keyboard: Found 1 mouse buttons
[   790.698] (--) evdev: SEM USB Keyboard: Found scroll wheel(s)
[   790.698] (--) evdev: SEM USB Keyboard: Found relative axes
[   790.698] (II) evdev: SEM USB Keyboard: Forcing relative x/y axes to exist.
[   790.698] (--) evdev: SEM USB Keyboard: Found absolute axes
[   790.698] (II) evdev: SEM USB Keyboard: Forcing absolute x/y axes to exist.
[   790.698] (--) evdev: SEM USB Keyboard: Found keys
[   790.698] (II) evdev: SEM USB Keyboard: Configuring as mouse
[   790.698] (II) evdev: SEM USB Keyboard: Configuring as keyboard
[   790.698] (II) evdev: SEM USB Keyboard: Adding scrollwheel support
[   790.698] (**) evdev: SEM USB Keyboard: YAxisMapping: buttons 4 and 5
[   790.698] (**) evdev: SEM USB Keyboard: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   790.698] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.0/usb3/3-3/3-3:1.1/0003:1A2C:0E24.0004/input/input8/event5"
[   790.698] (II) XINPUT: Adding extended input device "SEM USB Keyboard" (type: KEYBOARD, id 11)
[   790.698] (**) Option "xkb_rules" "evdev"
[   790.698] (**) Option "xkb_model" "pc105"
[   790.698] (**) Option "xkb_layout" "pl"
[   790.699] (II) evdev: SEM USB Keyboard: initialized for relative axes.
[   790.699] (WW) evdev: SEM USB Keyboard: ignoring absolute axes.
[   790.699] (**) SEM USB Keyboard: (accel) keeping acceleration scheme 1
[   790.699] (**) SEM USB Keyboard: (accel) acceleration profile 0
[   790.699] (**) SEM USB Keyboard: (accel) acceleration factor: 2.000
[   790.699] (**) SEM USB Keyboard: (accel) acceleration threshold: 4
[   790.700] (II) config/udev: Adding input device HDA NVidia Rear Mic (/dev/input/event11)
[   790.700] (II) No input driver specified, ignoring this device.
[   790.700] (II) This device may have been added with another device file.
[   790.701] (II) config/udev: Adding input device HDA NVidia Front Mic (/dev/input/event12)
[   790.701] (II) No input driver specified, ignoring this device.
[   790.701] (II) This device may have been added with another device file.
[   790.702] (II) config/udev: Adding input device HDA NVidia Line (/dev/input/event13)
[   790.702] (II) No input driver specified, ignoring this device.
[   790.702] (II) This device may have been added with another device file.
[   790.703] (II) config/udev: Adding input device HDA NVidia Line Out Front (/dev/input/event14)
[   790.703] (II) No input driver specified, ignoring this device.
[   790.703] (II) This device may have been added with another device file.
[   790.703] (II) config/udev: Adding input device HDA NVidia Line Out Surround (/dev/input/event15)
[   790.703] (II) No input driver specified, ignoring this device.
[   790.703] (II) This device may have been added with another device file.
[   790.704] (II) config/udev: Adding input device HDA NVidia Line Out CLFE (/dev/input/event16)
[   790.704] (II) No input driver specified, ignoring this device.
[   790.704] (II) This device may have been added with another device file.
[   790.705] (II) config/udev: Adding input device HDA NVidia Line Out Side (/dev/input/event17)
[   790.705] (II) No input driver specified, ignoring this device.
[   790.705] (II) This device may have been added with another device file.
[   790.705] (II) config/udev: Adding input device HDA NVidia Front Headphone (/dev/input/event18)
[   790.706] (II) No input driver specified, ignoring this device.
[   790.706] (II) This device may have been added with another device file.
[   790.706] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=7 (/dev/input/event7)
[   790.706] (II) No input driver specified, ignoring this device.
[   790.706] (II) This device may have been added with another device file.
[   790.707] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=8 (/dev/input/event8)
[   790.707] (II) No input driver specified, ignoring this device.
[   790.707] (II) This device may have been added with another device file.
[   790.708] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=9 (/dev/input/event9)
[   790.708] (II) No input driver specified, ignoring this device.
[   790.708] (II) This device may have been added with another device file.
[   790.709] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=10 (/dev/input/event10)
[   790.709] (II) No input driver specified, ignoring this device.
[   790.709] (II) This device may have been added with another device file.
[   790.709] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=3 (/dev/input/event6)
[   790.709] (II) No input driver specified, ignoring this device.
[   790.709] (II) This device may have been added with another device file.


```

---

### Post by Yellow Pasque on 2018-02-14
```
BOOT_IMAGE=/boot/vmlinuz-4.13.0-32-generic root=UUID=12e7c3ba-a6dd-4699-9efc-5df243cce7d2 ro nomodeset quiet splash vt.handoff=7
```

You're booting with nomodeset. Why?

---

### Post by maccraft123 on 2018-02-14
What?
I forgot to put it out :| 
I will boot without this option and post what i will post results

Without it system won't boot up

---

### Post by maccraft123 on 2018-02-14
It doesn't get after grub after removing nomodeset

---

### Post by Yellow Pasque on 2018-02-14
What happens? Can you press Ctrl+Alt+F1 to get to a terminal?

---

### Post by maccraft123 on 2018-02-15
I can't do anything, i will try to update mesa drivers tomorrow

---

### Post by QIII on 2018-02-15
> **Temüjin said:**
> VMWare developed llvmpipe software renderer.

Hmmm...  yet another sticky note for the inside of my skull -- if I can find any room.

---

### Post by maccraft123 on 2018-02-15
After updating mesa and booting with nomodeset still nothing happens :(

lspci | grep VGA

```
02:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Device 67ef (rev cf)
```

dmesg | grep amd

```
[    1.765520] pata_amd 0000:00:06.0: version 0.4.1
[    1.766656] scsi host0: pata_amd
[    1.766783] scsi host1: pata_amd
[    1.844417] [drm:amdgpu_init [amdgpu]] *ERROR* VGACON disables amdgpu kernel modesetting.
[   13.631363] EDAC amd64: Node 0: DRAM ECC disabled.
[   13.631366] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   13.672368] EDAC amd64: Node 0: DRAM ECC disabled.
[   13.672371] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   13.704436] EDAC amd64: Node 0: DRAM ECC disabled.
[   13.704439] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   13.764429] EDAC amd64: Node 0: DRAM ECC disabled.
[   13.764432] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   13.776530] [drm:amdgpu_init [amdgpu]] *ERROR* VGACON disables amdgpu kernel modesetting.
```

dpkg --list | grep mesa

```
ii  libegl1-mesa:amd64                               1:18.1~git180208124100.e843667~x~padoka0        amd64        free implementation of the EGL API -- runtime
ii  libgl1-mesa-dri:amd64                            1:18.1~git180208124100.e843667~x~padoka0        amd64        free implementation of the OpenGL API -- DRI modules
ii  libgl1-mesa-glx:amd64                            1:18.1~git180208124100.e843667~x~padoka0        amd64        free implementation of the OpenGL API -- GLX runtime
ii  libglapi-mesa:amd64                              1:18.1~git180208124100.e843667~x~padoka0        amd64        free implementation of the GL API -- shared library
ii  libglu1-mesa:amd64                               9.0.0-2.1                                       amd64        Mesa OpenGL utility library (GLU)
ii  libwayland-egl1-mesa:amd64                       1:18.1~git180208124100.e843667~x~padoka0        amd64        implementation of the Wayland EGL platform -- runtime
ii  mesa-utils                                       8.3.0-1                                         amd64        Miscellaneous Mesa GL utilities

```

full dmesg
[https://pastebin.com/yfctaZxk](https://pastebin.com/yfctaZxk)
Posted on pastebin becouse it's long

I really want to use open source mesa, not AMDGPU(-PRO)

---

### Post by maccraft123 on 2018-02-15
Updating Ubuntu to 17.10 (My card was released in December 2016), so i hope it will "update it"

---

### Post by maccraft123 on 2018-02-15
Now lspci shows my graphics card as RX460(which it really is), but still doesn't boot without nomodeset

---

### Post by Yellow Pasque on 2018-02-15
Do you see anything on the monitor when booting without nomodeset? What kind of monitor and connection are you using?

---

### Post by maccraft123 on 2018-02-16
I wasn't seeing anything at all.
I have just installed Arch Linux, and mesa drivers on it are working.

---

### Post by nestsh on 2018-03-14
have, I think it has something to do with the refresh rate of your screen mine is 60hz I have the same problem, in my case it gets worse because I'm very new in Linux I install lubuntu and it happens to me that I do not know how to install it if I could only start it in command mode I do not know how to do it because every time I open my screen it only goes out in black the key is to change the Hz I do not know how to do it so I would appreciate your help also every screen has different specifications

---

