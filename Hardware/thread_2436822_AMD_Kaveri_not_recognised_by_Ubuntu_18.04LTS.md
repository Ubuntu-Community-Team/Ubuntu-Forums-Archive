---
title: "AMD Kaveri not recognised by Ubuntu 18.04LTS"
date: 2020-02-13
forum: Hardware
---

### Post by emseedee on 2020-02-13
Hi, all,

I know that this is similar to several other posts, but none of the other answers seem to work for me.

I have a PC with an AMD A10-7700K CPU, that includes the Kaveri GPU. It also has 8 G RAM, and plenty of disc. I have a new, clean installation of Ubuntu 18.04LTS / 64bit, built from the network installer. At tasksel the only option selected was Ubuntu desktop.

The main problem is that I can't change the display properties - the resolution is fixed (only one option), and I can't set up dual displays. 

Things I know:
1. graphics are being handled by llvmpipe (LLVM 9.0, 128 bits)
2. lspci report a single graphics controller : 
  ```
VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Kaveri [Radeon R7 Graphics]
```

3. lsmod reports that neither radeon nor amdgpu are loaded

4. looking at modprobe:
```
grep -r radeon /etc/modprobe.d
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist radeonfb

```

5 the only relevant line in GRUB is ```
GRUB_CMDLINE_LINUX_DEFAULT="splash quiet"
```

6. Xlog.0.log looks like:
```

[    12.923] (--) Log file renamed from "/var/log/Xorg.pid-1133.log" to "/var/log/Xorg.0.log"
[    12.924] 
X.Org X Server 1.19.6
Release Date: 201-12-20
[    12.924] X Protocol Version 11, Revision 0
[    12.925] Build Operating System: Linux 4.4.0-148-generic x86_64 Ubuntu
[    12.925] Current Operating System: Linux ubuntu 4.15.0-76-generic #86-Ubuntu SMP Fri Jan 17 17:24:28 UTC 2020 x86_64
[    12.925] Kernel command line: BOOT_IMAGE=//vmlinuz root=UUID=24e2000a-5ac2-4962-a135-f8f297705f6a verbose nomodeset
[    12.925] Build Date: 03 June 2019  08:10:35AM
[    12.925] xorg-server 2:1.19.6-1ubuntu4.3 (For technical support please see http://www.ubuntu.com/support) 
[    12.925] Current version of pixman: 0.34.0
[    12.925]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    12.925] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    12.925] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Feb 13 20:57:19 2020
[    12.929] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    12.931] (==) No Layout section.  Using the first Screen section.
[    12.931] (==) No screen section available. Using defaults.
[    12.931] (**) |-->Screen "Default Screen Section" (0)
[    12.931] (**) |   |-->Monitor "<default monitor>"
[    12.932] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    12.932] (==) Automatically adding devices
[    12.932] (==) Automatically enabling devices
[    12.932] (==) Automatically adding GPU devices
[    12.932] (==) Automatically binding GPU devices
[    12.932] (==) Max clients allowed: 256, resource mask: 0x1fffff
[    12.934] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    12.934]     Entry deleted from font path.
[    12.934] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    12.934]     Entry deleted from font path.
[    12.934] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    12.934]     Entry deleted from font path.
[    12.939] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    12.939]     Entry deleted from font path.
[    12.939] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    12.939]     Entry deleted from font path.
[    12.939] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    12.939] (==) ModulePath set to "/usr/lib/xorg/modules"
[    12.939] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    12.940] (II) Loader magic: 0x55ed58874020
[    12.940] (II) Module ABI versions:
[    12.940]     X.Org ANSI C Emulation: 0.4
[    12.940]     X.Org Video Driver: 23.0
[    12.940]     X.Org XInput driver : 24.1
[    12.940]     X.Org Server Extension : 10.0
[    12.941] (++) using VT number 1

[    12.943] (II) systemd-logind: took control of session /org/freedesktop/login1/session/c2
[    12.947] (--) PCI:*(0:0:1:0) 1002:1313:1462:7903 rev 0, Mem @ 0xc0000000/268435456, 0xd0000000/8388608, 0xfeb00000/262144, I/O @ 0x0000f000/256, BIOS @ 0x????????/131072
[    12.947] (II) LoadModule: "glx"
[    12.948] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    12.952] (II) Module glx: vendor="X.Org Foundation"
[    12.952]     compiled for 1.19.6, module version = 1.0.0
[    12.952]     ABI class: X.Org Server Extension, version 10.0
[    12.952] (==) Matched ati as autoconfigured driver 0
[    12.952] (==) Matched modesetting as autoconfigured driver 1
[    12.952] (==) Matched fbdev as autoconfigured driver 2
[    12.952] (==) Matched vesa as autoconfigured driver 3
[    12.952] (==) Assigned the driver to the xf86ConfigLayout
[    12.952] (II) LoadModule: "ati"
[    12.953] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    12.953] (II) Module ati: vendor="X.Org Foundation"
[    12.953]     compiled for 1.19.6, module version = 18.0.1
[    12.953]     Module class: X.Org Video Driver
[    12.953]     ABI class: X.Org Video Driver, version 23.0
[    13.015] (II) LoadModule: "radeon"
[    13.016] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    13.020] (II) Module radeon: vendor="X.Org Foundation"
[    13.020]     compiled for 1.19.6, module version = 18.0.1
[    13.020]     Module class: X.Org Video Driver
[    13.020]     ABI class: X.Org Video Driver, version 23.0
[    13.020] (II) LoadModule: "modesetting"
[    13.021] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    13.022] (II) Module modesetting: vendor="X.Org Foundation"
[    13.022]     compiled for 1.19.6, module version = 1.19.6
[    13.022]     Module class: X.Org Video Driver
[    13.022]     ABI class: X.Org Video Driver, version 23.0
[    13.022] (II) LoadModule: "fbdev"
[    13.022] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    13.023] (II) Module fbdev: vendor="X.Org Foundation"
[    13.023]     compiled for 1.19.3, module version = 0.4.4
[    13.023]     Module class: X.Org Video Driver
[    13.023]     ABI class: X.Org Video Driver, version 23.0
[    13.023] (II) LoadModule: "vesa"
[    13.023] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    13.024] (II) Module vesa: vendor="X.Org Foundation"
[    13.024]     compiled for 1.19.3, module version = 2.3.4
[    13.024]     Module class: X.Org Video Driver
[    13.024]     ABI class: X.Org Video Driver, version 23.0
[    13.024] (II) RADEON: Driver for ATI/AMD Radeon chipsets:
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
[    13.030] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    13.030] (II) FBDEV: driver for framebuffer: fbdev
[    13.030] (II) VESA: driver for VESA chipsets: vesa
[    13.031] (II) [KMS] drm report modesetting isn't supported.
[    13.031] (EE) open /dev/dri/card0: No such file or directory
[    13.031] (WW) Falling back to old probe method for modesetting
[    13.031] (EE) open /dev/dri/card0: No such file or directory
[    13.031] (II) Loading sub module "fbdevhw"
[    13.031] (II) LoadModule: "fbdevhw"
[    13.031] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    13.032] (II) Module fbdevhw: vendor="X.Org Foundation"
[    13.032]     compiled for 1.19.6, module version = 0.0.2
[    13.032]     ABI class: X.Org Video Driver, version 23.0
[    13.033] (**) FBDEV(2): claimed PCI slot 0@0:1:0
[    13.033] (II) FBDEV(2): using default device
[    13.033] (WW) Falling back to old probe method for vesa
[    13.033] (EE) Screen 0 deleted because of no matching config section.
[    13.033] (II) UnloadModule: "radeon"
[    13.033] (EE) Screen 0 deleted because of no matching config section.
[    13.033] (II) UnloadModule: "modesetting"
[    13.033] (II) FBDEV(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    13.033] (==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
[    13.033] (==) FBDEV(0): RGB weight 888
[    13.033] (==) FBDEV(0): Default visual is TrueColor
[    13.033] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[    13.033] (II) FBDEV(0): hardware: EFI VGA (video memory: 3072kB)
[    13.033] (II) FBDEV(0): checking modes against framebuffer device...
[    13.033] (II) FBDEV(0): checking modes against monitor...
[    13.033] (--) FBDEV(0): Virtual size is 1024x768 (pitch 1024)
[    13.033] (**) FBDEV(0):  Built-in mode "current": 78.7 MHz, 59.9 kHz, 75.7 Hz
[    13.033] (II) FBDEV(0): Modeline "current"x0.0   78.65  1024 1056 1184 1312  768 772 776 792 -hsync -vsync -csync (59.9 kHz b)
[    13.033] (==) FBDEV(0): DPI set to (96, 96)
[    13.033] (II) Loading sub module "fb"
[    13.033] (II) LoadModule: "fb"
[    13.033] (II) Loading /usr/lib/xorg/modules/libfb.so
[    13.035] (II) Module fb: vendor="X.Org Foundation"
[    13.035]     compiled for 1.19.6, module version = 1.0.0
[    13.035]     ABI class: X.Org ANSI C Emulation, version 0.4
[    13.035] (**) FBDEV(0): using shadow framebuffer
[    13.035] (II) Loading sub module "shadow"
[    13.035] (II) LoadModule: "shadow"
[    13.035] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    13.036] (II) Module shadow: vendor="X.Org Foundation"
[    13.036]     compiled for 1.19.6, module version = 1.1.0
[    13.036]     ABI class: X.Org ANSI C Emulation, version 0.4
[    13.036] (II) UnloadModule: "vesa"
[    13.036] (II) Unloading vesa
[    13.036] (==) Depth 24 pixmap format is 32 bpp
[    13.036] (II) FBDEV(0): FBIOBLANK: Invalid argument (Screen blanking not supported by kernel - disabling)
[    13.040] (==) FBDEV(0): Backing store enabled
[    13.040] (==) FBDEV(0): DPMS enabled
[    13.041] (==) RandR enabled
[    13.046] (II) SELinux: Disabled on system
[    13.047] (II) AIGLX: Screen 0 is not DRI2 capable
[    13.047] (EE) AIGLX: reverting to software rendering
[    13.411] (II) IGLX: enabled GLX_MESA_copy_sub_buffer
[    13.412] (II) IGLX: Loaded and initialized swrast
[    13.412] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    13.507] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    13.507] (**) Power Button: Applying InputClass "libinput keyboard catchall"
[    13.507] (II) LoadModule: "libinput"
[    13.507] (II) Loading /usr/lib/xorg/modules/input/libinput_drv.so
[    13.510] (II) Module libinput: vendor="X.Org Foundation"
[    13.510]     compiled for 1.19.6, module version = 0.27.1
[    13.510]     Module class: X.Org XInput Driver
[    13.510]     ABI class: X.Org XInput driver, version 24.1
[    13.510] (II) Using input driver 'libinput' for 'Power Button'
[    13.511] (II) systemd-logind: got fd for /dev/input/event1 13:65 fd 22 paused 0
[    13.511] (**) Power Button: always reports core events
[    13.511] (**) Option "Device" "/dev/input/event1"
[    13.511] (**) Option "_source" "server/udev"
[    13.511] (II) event1  - Power Button: is tagged by udev as: Keyboard
[    13.511] (II) event1  - Power Button: device is a keyboard
[    13.511] (II) event1  - Power Button: device removed
[    13.511] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    13.512] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    13.512] (**) Option "xkb_model" "pc105"
[    13.512] (**) Option "xkb_layout" "gb"
[    13.512] (**) Option "xkb_variant" "extd"
[    13.536] (II) event1  - Power Button: is tagged by udev as: Keyboard
[    13.536] (II) event1  - Power Button: device is a keyboard
[    13.537] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[    13.537] (**) Video Bus: Applying InputClass "libinput keyboard catchall"
[    13.537] (II) Using input driver 'libinput' for 'Video Bus'
[    13.538] (II) systemd-logind: got fd for /dev/input/event4 13:68 fd 25 paused 0
[    13.538] (**) Video Bus: always reports core events
[    13.538] (**) Option "Device" "/dev/input/event4"
[    13.538] (**) Option "_source" "server/udev"
[    13.539] (II) event4  - Video Bus: is tagged by udev as: Keyboard
[    13.539] (II) event4  - Video Bus: device is a keyboard
[    13.539] (II) event4  - Video Bus: device removed
[    13.539] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input4/event4"
[    13.539] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    13.539] (**) Option "xkb_model" "pc105"
[    13.539] (**) Option "xkb_layout" "gb"
[    13.539] (**) Option "xkb_variant" "extd"
[    13.540] (II) event4  - Video Bus: is tagged by udev as: Keyboard
[    13.540] (II) event4  - Video Bus: device is a keyboard
[    13.541] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    13.541] (**) Power Button: Applying InputClass "libinput keyboard catchall"
[    13.541] (II) Using input driver 'libinput' for 'Power Button'
[    13.542] (II) systemd-logind: got fd for /dev/input/event0 13:64 fd 26 paused 0
[    13.542] (**) Power Button: always reports core events
[    13.542] (**) Option "Device" "/dev/input/event0"
[    13.542] (**) Option "_source" "server/udev"
[    13.543] (II) event0  - Power Button: is tagged by udev as: Keyboard
[    13.543] (II) event0  - Power Button: device is a keyboard
[    13.543] (II) event0  - Power Button: device removed
[    13.543] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    13.543] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    13.543] (**) Option "xkb_model" "pc105"
[    13.543] (**) Option "xkb_layout" "gb"
[    13.543] (**) Option "xkb_variant" "extd"
[    13.544] (II) event0  - Power Button: is tagged by udev as: Keyboard
[    13.544] (II) event0  - Power Button: device is a keyboard
[    13.544] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=3 (/dev/input/event5)
[    13.544] (II) No input driver specified, ignoring this device.
[    13.544] (II) This device may have been added with another device file.
[    13.545] (II) config/udev: Adding input device Logitech K360 (/dev/input/event2)
[    13.545] (**) Logitech K360: Applying InputClass "libinput keyboard catchall"
[    13.545] (II) Using input driver 'libinput' for 'Logitech K360'
[    13.546] (II) systemd-logind: got fd for /dev/input/event2 13:66 fd 27 paused 0
[    13.546] (**) Logitech K360: always reports core events
[    13.546] (**) Option "Device" "/dev/input/event2"
[    13.546] (**) Option "_source" "server/udev"
[    13.547] (II) event2  - Logitech K360: is tagged by udev as: Keyboard
[    13.547] (II) event2  - Logitech K360: device is a keyboard
[    13.547] (II) event2  - Logitech K360: device removed
[    13.547] (II) libinput: Logitech K360: needs a virtual subdevice
[    13.547] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb3/3-1/3-1:1.2/0003:046D:C52B.0003/0003:046D:4004.0004/input/input2/event2"
[    13.547] (II) XINPUT: Adding extended input device "Logitech K360" (type: MOUSE, id 9)
[    13.547] (**) Option "AccelerationScheme" "none"
[    13.547] (**) Logitech K360: (accel) selected scheme none/0
[    13.547] (**) Logitech K360: (accel) acceleration factor: 2.000
[    13.547] (**) Logitech K360: (accel) acceleration threshold: 4
[    13.548] (II) event2  - Logitech K360: is tagged by udev as: Keyboard
[    13.548] (II) event2  - Logitech K360: device is a keyboard
[    13.548] (II) config/udev: Adding input device Logitech  (/dev/input/event3)
[    13.548] (**) Logitech : Applying InputClass "libinput pointer catchall"
[    13.548] (II) Using input driver 'libinput' for 'Logitech '
[    13.549] (II) systemd-logind: got fd for /dev/input/event3 13:67 fd 28 paused 0
[    13.549] (**) Logitech : always reports core events
[    13.549] (**) Option "Device" "/dev/input/event3"
[    13.549] (**) Option "_source" "server/udev"
[    13.550] (II) event3  - Logitech : is tagged by udev as: Mouse
[    13.550] (II) event3  - Logitech : device is a pointer
[    13.550] (II) event3  - Logitech : device removed
[    13.550] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb3/3-1/3-1:1.2/0003:046D:C52B.0003/0003:046D:4055.0005/input/input3/event3"
[    13.550] (II) XINPUT: Adding extended input device "Logitech " (type: MOUSE, id 10)
[    13.550] (**) Option "AccelerationScheme" "none"
[    13.550] (**) Logitech : (accel) selected scheme none/0
[    13.550] (**) Logitech : (accel) acceleration factor: 2.000
[    13.550] (**) Logitech : (accel) acceleration threshold: 4
[    13.551] (II) event3  - Logitech : is tagged by udev as: Mouse
[    13.551] (II) event3  - Logitech : device is a pointer
[    13.551] (II) config/udev: Adding input device Logitech  (/dev/input/mouse0)
[    13.551] (II) No input driver specified, ignoring this device.
[    13.551] (II) This device may have been added with another device file.
[    13.552] (II) config/udev: Adding input device HD-Audio Generic Line Out Surround (/dev/input/event10)
[    13.552] (II) No input driver specified, ignoring this device.
[    13.552] (II) This device may have been added with another device file.
[    13.552] (II) config/udev: Adding input device HD-Audio Generic Line Out CLFE (/dev/input/event11)
[    13.552] (II) No input driver specified, ignoring this device.
[    13.552] (II) This device may have been added with another device file.
[    13.552] (II) config/udev: Adding input device HD-Audio Generic Line Out Side (/dev/input/event12)
[    13.552] (II) No input driver specified, ignoring this device.
[    13.552] (II) This device may have been added with another device file.
[    13.553] (II) config/udev: Adding input device HD-Audio Generic Front Headphone (/dev/input/event13)
[    13.553] (II) No input driver specified, ignoring this device.
[    13.553] (II) This device may have been added with another device file.
[    13.553] (II) config/udev: Adding input device HD-Audio Generic Front Mic (/dev/input/event6)
[    13.553] (II) No input driver specified, ignoring this device.
[    13.553] (II) This device may have been added with another device file.
[    13.553] (II) config/udev: Adding input device HD-Audio Generic Rear Mic (/dev/input/event7)
[    13.553] (II) No input driver specified, ignoring this device.
[    13.553] (II) This device may have been added with another device file.
[    13.554] (II) config/udev: Adding input device HD-Audio Generic Line (/dev/input/event8)
[    13.554] (II) No input driver specified, ignoring this device.
[    13.554] (II) This device may have been added with another device file.
[    13.554] (II) config/udev: Adding input device HD-Audio Generic Line Out Front (/dev/input/event9)
[    13.554] (II) No input driver specified, ignoring this device.
[    13.554] (II) This device may have been added with another device file.
[    13.559] (**) Logitech K360: Applying InputClass "libinput keyboard catchall"
[    13.559] (II) Using input driver 'libinput' for 'Logitech K360'
[    13.559] (II) systemd-logind: returning pre-existing fd for /dev/input/event2 13:66
[    13.559] (**) Logitech K360: always reports core events
[    13.559] (**) Option "Device" "/dev/input/event2"
[    13.559] (**) Option "_source" "_driver/libinput"
[    13.559] (II) libinput: Logitech K360: is a virtual subdevice
[    13.559] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb3/3-1/3-1:1.2/0003:046D:C52B.0003/0003:046D:4004.0004/input/input2/event2"
[    13.559] (II) XINPUT: Adding extended input device "Logitech K360" (type: KEYBOARD, id 11)
[    13.559] (**) Option "xkb_model" "pc105"
[    13.559] (**) Option "xkb_layout" "gb"
[    13.559] (**) Option "xkb_variant" "extd"
[    25.799] (**) Option "fd" "22"
[    25.804] (II) event1  - Power Button: device removed
[    25.804] (**) Option "fd" "25"
[    25.804] (II) event4  - Video Bus: device removed
[    25.804] (**) Option "fd" "26"
[    25.804] (II) event0  - Power Button: device removed
[    25.805] (**) Option "fd" "27"
[    25.805] (**) Option "fd" "28"
[    25.805] (II) event3  - Logitech : device removed
[    25.805] (**) Option "fd" "27"
[    25.805] (II) event2  - Logitech K360: device removed
[    25.806] (II) systemd-logind: got pause for 13:68
[    25.806] (II) systemd-logind: got pause for 13:64
[    25.806] (II) systemd-logind: got pause for 13:67
[    25.806] (II) systemd-logind: got pause for 13:65
[    25.806] (II) systemd-logind: got pause for 13:66

```

Can anyone explain why the AMD drivers don't load, and what I can do to fix it.

For what it's worth, I had exactly the same problem in 19.10 - went back to 18.04 in the hope that would fix it. Didn't have a problem with Debian.

Mike

---

### Post by Yellow Pasque on 2020-02-13
```
Kernel command line: BOOT_IMAGE=//vmlinuz root=UUID=24e2000a-5ac2-4962-a135-f8f297705f6a verbose nomodeset
```

You're booting with nomodeset. You have to fix that first. Look in /etc/default/grub and also make sure you're not booting in any recovery mode.

---

### Post by emseedee on 2020-02-14
> **Yellow Pasque said:**
> ```
Kernel command line: BOOT_IMAGE=//vmlinuz root=UUID=24e2000a-5ac2-4962-a135-f8f297705f6a verbose nomodeset
```

You're booting with nomodeset. You have to fix that first. Look in /etc/default/grub and also make sure you're not booting in any recovery mode.

Thanks very much - that's fixed it.

This is a dual boot machine with the MBR pointing to Grub2Win, which in turn calls Ubuntu's Grub. For some reason Grub2Win uses "verbose nomodeset" as its default.

---

### Post by Yellow Pasque on 2020-02-14
Good to hear. Please mark thread SOLVED ('Thread Tools' menu above first post) if no further issues.

---

