---
title: "Monitor Resolution is incorrect after ugrade 12.04 LTS to 14.04 LTS"
date: 2014-04-20
forum: Hardware
---

### Post by djotaku on 2014-04-20
My wife's computer has a 1920x1080 monitor. Post upgrade the only selectable resolution in Display in KDE's System Settings is: 1400x1050.

Here's the relevant I can think of:

```
01:05.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RS780D [Radeon HD 3300]

```

```

dcmesa@toad:~$ cat /var/log/Xorg.0.log
[    10.021] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[    10.021] X Protocol Version 11, Revision 0
[    10.021] Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
[    10.021] Current Operating System: Linux toad 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:11:08 UTC 2014 x86_64
[    10.021] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic root=UUID=519952d9-11ae-45e1-b06f-91cb37749c3f ro quiet splash vt.handoff=7
[    10.021] Build Date: 16 April 2014  01:36:29PM
[    10.021] xorg-server 2:1.15.1-0ubuntu2 (For technical support please see http://www.ubuntu.com/support) 
[    10.021] Current version of pixman: 0.30.2
[    10.021]    Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
[    10.021] Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    10.021] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Apr 20 16:37:22 2014
[    10.026] (==) Using config file: "/etc/X11/xorg.conf"
[    10.026] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    10.055] (==) No Layout section.  Using the first Screen section.
[    10.055] (**) |-->Screen "Default Screen" (0)
[    10.055] (**) |   |-->Monitor "<default monitor>"
[    10.055] (==) No device specified for screen "Default Screen".
        Using the first device section listed.
[    10.055] (**) |   |-->Device "Default Device"
[    10.055] (==) No monitor specified for screen "Default Screen".
        Using a default monitor configuration.
[    10.055] (==) Automatically adding devices
[    10.055] (==) Automatically enabling devices
[    10.055] (==) Automatically adding GPU devices
[    10.081] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    10.081]    Entry deleted from font path.
[    10.093] (==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/100dpi/:unscaled,
        /usr/share/fonts/X11/75dpi/:unscaled,
        /usr/share/fonts/X11/Type1,
        /usr/share/fonts/X11/100dpi,
        /usr/share/fonts/X11/75dpi,
        built-ins
[    10.093] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    10.093] (II) The server relies on udev to provide the list of input devices.
        If no devices become available, reconfigure udev or disable AutoAddDevices.
[    10.093] (II) Loader magic: 0x7f15b3859d60
[    10.093] (II) Module ABI versions:
[    10.093]    X.Org ANSI C Emulation: 0.4
[    10.093]    X.Org Video Driver: 15.0
[    10.093]    X.Org XInput driver : 20.0
[    10.093]    X.Org Server Extension : 8.0
[    10.094] (--) PCI:*(0:1:5:0) 1002:9614:1043:834d rev 0, Mem @ 0xd0000000/268435456, 0xfbde0000/65536, 0xfbc00000/1048576, I/O @ 0x0000c000/256
[    10.094] Initializing built-in extension Generic Event Extension
[    10.094] Initializing built-in extension SHAPE
[    10.094] Initializing built-in extension MIT-SHM
[    10.094] Initializing built-in extension XInputExtension
[    10.094] Initializing built-in extension XTEST
[    10.094] Initializing built-in extension BIG-REQUESTS
[    10.094] Initializing built-in extension SYNC
[    10.094] Initializing built-in extension XKEYBOARD
[    10.094] Initializing built-in extension XC-MISC
[    10.094] Initializing built-in extension SECURITY
[    10.094] Initializing built-in extension XINERAMA
[    10.094] Initializing built-in extension XFIXES
[    10.094] Initializing built-in extension RENDER
[    10.094] Initializing built-in extension RANDR
[    10.094] Initializing built-in extension COMPOSITE
[    10.094] Initializing built-in extension DAMAGE
[    10.094] Initializing built-in extension MIT-SCREEN-SAVER
[    10.094] Initializing built-in extension DOUBLE-BUFFER
[    10.094] Initializing built-in extension RECORD
[    10.094] Initializing built-in extension DPMS
[    10.094] Initializing built-in extension Present
[    10.094] Initializing built-in extension DRI3
[    10.094] Initializing built-in extension X-Resource
[    10.094] Initializing built-in extension XVideo
[    10.094] Initializing built-in extension XVideo-MotionCompensation
[    10.094] Initializing built-in extension SELinux
[    10.094] Initializing built-in extension XFree86-VidModeExtension
[    10.094] Initializing built-in extension XFree86-DGA
[    10.094] Initializing built-in extension XFree86-DRI
[    10.094] Initializing built-in extension DRI2
[    10.094] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    10.094] (WW) "xmir" is not to be loaded by default. Skipping.
[    10.094] (II) LoadModule: "glx"
[    10.095] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/extensions/libglx.so
[    10.107] (II) Module glx: vendor="Advanced Micro Devices, Inc."
[    10.107]    compiled for 6.9.0, module version = 1.0.0
[    10.107] Loading extension GLX
[    10.107] (II) LoadModule: "fglrx"
[    10.108] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so
[    10.202] (II) Module fglrx: vendor="FireGL - AMD Technologies Inc."
[    10.202]    compiled for 1.4.99.906, module version = 13.35.5
[    10.202]    Module class: X.Org Video Driver
[    10.202] (II) Loading sub module "fglrxdrm"
[    10.202] (II) LoadModule: "fglrxdrm"
[    10.202] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    10.216] (II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
[    10.217]    compiled for 1.4.99.906, module version = 13.35.5
[    10.217] (II) AMD Proprietary Linux Driver Version Identifier:13.35.5
[    10.217] (II) AMD Proprietary Linux Driver Release Identifier: UNSUPPORTED-13.35.1005               
[    10.217] (II) AMD Proprietary Linux Driver Build Date: Mar 12 2014 10:32:23
[    10.217] (++) using VT number 7

[    10.217] (WW) Falling back to old probe method for fglrx
[    10.249] (II) Loading PCS database from /etc/ati/amdpcsdb /etc/ati/amdpcsdb.default
[    10.298] ukiDynamicMajor: failed to open /proc/ati/major
[    10.299] (EE) No supported AMD display adapters were found
[    10.299] (EE) No devices detected.
[    10.299] (==) Matched fglrx as autoconfigured driver 0
[    10.299] (==) Matched ati as autoconfigured driver 1
[    10.299] (==) Matched modesetting as autoconfigured driver 2
[    10.299] (==) Matched fbdev as autoconfigured driver 3
[    10.299] (==) Matched vesa as autoconfigured driver 4
[    10.299] (==) Assigned the driver to the xf86ConfigLayout
[    10.299] (II) LoadModule: "fglrx"
[    10.300] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so
[    10.300] (II) Module fglrx: vendor="FireGL - AMD Technologies Inc."
[    10.300]    compiled for 1.4.99.906, module version = 13.35.5
[    10.300]    Module class: X.Org Video Driver
[    10.300] (II) LoadModule: "ati"
[    10.317] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    10.325] (II) Module ati: vendor="X.Org Foundation"
[    10.325]    compiled for 1.15.0, module version = 7.3.0
[    10.325]    Module class: X.Org Video Driver
[    10.325]    ABI class: X.Org Video Driver, version 15.0
[    10.325] (II) LoadModule: "radeon"
[    10.326] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    10.374] (II) Module radeon: vendor="X.Org Foundation"
[    10.374]    compiled for 1.15.0, module version = 7.3.0
[    10.374]    Module class: X.Org Video Driver
[    10.374]    ABI class: X.Org Video Driver, version 15.0
[    10.374] (II) LoadModule: "modesetting"
[    10.374] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    10.379] (II) Module modesetting: vendor="X.Org Foundation"
[    10.379]    compiled for 1.15.0, module version = 0.8.1
[    10.379]    Module class: X.Org Video Driver
[    10.379]    ABI class: X.Org Video Driver, version 15.0
[    10.379] (II) LoadModule: "fbdev"
[    10.380] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    10.386] (II) Module fbdev: vendor="X.Org Foundation"
[    10.386]    compiled for 1.15.0, module version = 0.4.4
[    10.386]    Module class: X.Org Video Driver
[    10.386]    ABI class: X.Org Video Driver, version 15.0
[    10.386] (II) LoadModule: "vesa"
[    10.386] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    10.387] (II) Module vesa: vendor="X.Org Foundation"
[    10.387]    compiled for 1.15.0, module version = 2.3.3
[    10.387]    Module class: X.Org Video Driver
[    10.387]    ABI class: X.Org Video Driver, version 15.0
[    10.387] (II) AMD Proprietary Linux Driver Version Identifier:13.35.5
[    10.387] (II) AMD Proprietary Linux Driver Release Identifier: UNSUPPORTED-13.35.1005               
[    10.387] (II) AMD Proprietary Linux Driver Build Date: Mar 12 2014 10:32:23
[    10.387] (II) RADEON: Driver for ATI Radeon chipsets:
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
[    10.393] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    10.393] (II) FBDEV: driver for framebuffer: fbdev
[    10.393] (II) VESA: driver for VESA chipsets: vesa
[    10.393] (++) using VT number 7

[    10.393] (WW) xf86OpenConsole: setpgid failed: Operation not permitted
[    10.393] (WW) xf86OpenConsole: setsid failed: Operation not permitted
[    10.393] (WW) Falling back to old probe method for fglrx
[    10.393] (II) Loading PCS database from /etc/ati/amdpcsdb /etc/ati/amdpcsdb.default
[    10.430] ukiDynamicMajor: failed to open /proc/ati/major
[    10.430] (EE) No supported AMD display adapters were found
[    10.430] (II) [KMS] drm report modesetting isn't supported.
[    10.430] (EE) open /dev/dri/card0: No such file or directory
[    10.430] (WW) Falling back to old probe method for modesetting
[    10.430] (EE) open /dev/dri/card0: No such file or directory
[    10.430] (II) Loading sub module "fbdevhw"
[    10.430] (II) LoadModule: "fbdevhw"
[    10.440] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    10.442] (II) Module fbdevhw: vendor="X.Org Foundation"
[    10.442]    compiled for 1.15.1, module version = 0.0.2
[    10.442]    ABI class: X.Org Video Driver, version 15.0
[    10.443] (**) FBDEV(2): claimed PCI slot 1@0:5:0
[    10.443] (II) FBDEV(2): using default device
[    10.443] (WW) Falling back to old probe method for vesa
[    10.443] (EE) Screen 0 deleted because of no matching config section.
[    10.443] (II) UnloadModule: "radeon"
[    10.443] (EE) Screen 0 deleted because of no matching config section.
[    10.443] (II) UnloadModule: "modesetting"
[    10.443] (II) FBDEV(0): Creating default Display subsection in Screen section
        "Default Screen" for depth/fbbpp 24/32
[    10.443] (**) FBDEV(0): Depth 24, (--) framebuffer bpp 32
[    10.443] (==) FBDEV(0): RGB weight 888
[    10.443] (==) FBDEV(0): Default visual is TrueColor
[    10.443] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[    10.443] (II) FBDEV(0): hardware: VESA VGA (video memory: 5824kB)
[    10.443] (II) FBDEV(0): checking modes against framebuffer device...
[    10.443] (II) FBDEV(0): checking modes against monitor...
[    10.443] (--) FBDEV(0): Virtual size is 1400x1050 (pitch 1400)
[    10.443] (**) FBDEV(0):  Built-in mode "current": 147.0 MHz, 83.2 kHz, 77.4 Hz
[    10.443] (II) FBDEV(0): Modeline "current"x0.0  147.04  1400 1432 1600 1768  1050 1054 1058 1074 -hsync -vsync -csync (83.2 kHz b)
[    10.443] (==) FBDEV(0): DPI set to (96, 96)
[    10.443] (II) Loading sub module "fb"
[    10.443] (II) LoadModule: "fb"
[    10.443] (II) Loading /usr/lib/xorg/modules/libfb.so
[    10.450] (II) Module fb: vendor="X.Org Foundation"
[    10.450]    compiled for 1.15.1, module version = 1.0.0
[    10.450]    ABI class: X.Org ANSI C Emulation, version 0.4
[    10.450] (**) FBDEV(0): using shadow framebuffer
[    10.450] (II) Loading sub module "shadow"
[    10.450] (II) LoadModule: "shadow"
[    10.450] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    10.474] (II) Module shadow: vendor="X.Org Foundation"
[    10.474]    compiled for 1.15.1, module version = 1.1.0
[    10.474]    ABI class: X.Org ANSI C Emulation, version 0.4
[    10.474] (II) UnloadModule: "fglrx"
[    10.474] (II) Unloading fglrx
[    10.474] (II) UnloadSubModule: "fglrxdrm"
[    10.474] (II) Unloading fglrxdrm
[    10.474] (II) UnloadModule: "vesa"
[    10.474] (II) Unloading vesa
[    10.474] (==) Depth 24 pixmap format is 32 bpp
[    10.474] (EE) FBDEV(0): FBIOBLANK: Invalid argument
[    10.474] (==) FBDEV(0): Backing store enabled
[    10.474] (==) FBDEV(0): DPMS enabled
[    10.474] (==) RandR enabled
[    10.480] (II) SELinux: Disabled on system
[    10.481] (EE) GLX error: Can not get required symbols.
[    10.618] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    10.621] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    10.621] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    10.621] (II) LoadModule: "evdev"
[    10.622] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    10.633] (II) Module evdev: vendor="X.Org Foundation"
[    10.633]    compiled for 1.15.0, module version = 2.8.2
[    10.633]    Module class: X.Org XInput Driver
[    10.633]    ABI class: X.Org XInput driver, version 20.0
[    10.633] (II) Using input driver 'evdev' for 'Power Button'
[    10.633] (**) Power Button: always reports core events
[    10.633] (**) evdev: Power Button: Device: "/dev/input/event1"
[    10.633] (--) evdev: Power Button: Vendor 0 Product 0x1
[    10.633] (--) evdev: Power Button: Found keys
[    10.633] (II) evdev: Power Button: Configuring as keyboard
[    10.633] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    10.633] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    10.633] (**) Option "xkb_rules" "evdev"
[    10.633] (**) Option "xkb_model" "pc105"
[    10.633] (**) Option "xkb_layout" "us"
[    10.634] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    10.634] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    10.634] (II) Using input driver 'evdev' for 'Power Button'
[    10.634] (**) Power Button: always reports core events
[    10.634] (**) evdev: Power Button: Device: "/dev/input/event0"
[    10.634] (--) evdev: Power Button: Vendor 0 Product 0x1
[    10.634] (--) evdev: Power Button: Found keys
[    10.634] (II) evdev: Power Button: Configuring as keyboard
[    10.634] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    10.634] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    10.634] (**) Option "xkb_rules" "evdev"
[    10.634] (**) Option "xkb_model" "pc105"
[    10.634] (**) Option "xkb_layout" "us"
[    10.634] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=3 (/dev/input/event12)
[    10.634] (II) No input driver specified, ignoring this device.
[    10.634] (II) This device may have been added with another device file.
[    10.635] (II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/event3)
[    10.635] (**) Logitech USB-PS/2 Optical Mouse: Applying InputClass "evdev pointer catchall"
[    10.635] (II) Using input driver 'evdev' for 'Logitech USB-PS/2 Optical Mouse'
[    10.635] (**) Logitech USB-PS/2 Optical Mouse: always reports core events
[    10.635] (**) evdev: Logitech USB-PS/2 Optical Mouse: Device: "/dev/input/event3"
[    10.635] (--) evdev: Logitech USB-PS/2 Optical Mouse: Vendor 0x46d Product 0xc03f
[    10.635] (--) evdev: Logitech USB-PS/2 Optical Mouse: Found 8 mouse buttons
[    10.635] (--) evdev: Logitech USB-PS/2 Optical Mouse: Found scroll wheel(s)
[    10.635] (--) evdev: Logitech USB-PS/2 Optical Mouse: Found relative axes
[    10.635] (--) evdev: Logitech USB-PS/2 Optical Mouse: Found x and y relative axes
[    10.635] (II) evdev: Logitech USB-PS/2 Optical Mouse: Configuring as mouse
[    10.635] (II) evdev: Logitech USB-PS/2 Optical Mouse: Adding scrollwheel support
[    10.635] (**) evdev: Logitech USB-PS/2 Optical Mouse: YAxisMapping: buttons 4 and 5
[    10.635] (**) evdev: Logitech USB-PS/2 Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    10.635] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.1/usb4/4-3/4-3:1.0/input/input3/event3"
[    10.635] (II) XINPUT: Adding extended input device "Logitech USB-PS/2 Optical Mouse" (type: MOUSE, id 8)
[    10.635] (II) evdev: Logitech USB-PS/2 Optical Mouse: initialized for relative axes.
[    10.635] (**) Logitech USB-PS/2 Optical Mouse: (accel) keeping acceleration scheme 1
[    10.635] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration profile 0
[    10.635] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration factor: 2.000
[    10.635] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration threshold: 4
[    10.635] (II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/mouse0)
[    10.635] (II) No input driver specified, ignoring this device.
[    10.635] (II) This device may have been added with another device file.
[    10.636] (II) config/udev: Adding input device HDA ATI SB Line Out Side (/dev/input/event5)
[    10.636] (II) No input driver specified, ignoring this device.
[    10.636] (II) This device may have been added with another device file.
[    10.636] (II) config/udev: Adding input device HDA ATI SB Front Headphone (/dev/input/event4)
[    10.636] (II) No input driver specified, ignoring this device.
[    10.636] (II) This device may have been added with another device file.
[    10.636] (II) config/udev: Adding input device HDA ATI SB Rear Mic (/dev/input/event11)
[    10.636] (II) No input driver specified, ignoring this device.
[    10.636] (II) This device may have been added with another device file.
[    10.636] (II) config/udev: Adding input device HDA ATI SB Front Mic (/dev/input/event10)
[    10.636] (II) No input driver specified, ignoring this device.
[    10.636] (II) This device may have been added with another device file.
[    10.637] (II) config/udev: Adding input device HDA ATI SB Line (/dev/input/event9)
[    10.637] (II) No input driver specified, ignoring this device.
[    10.637] (II) This device may have been added with another device file.
[    10.637] (II) config/udev: Adding input device HDA ATI SB Line Out Front (/dev/input/event8)
[    10.637] (II) No input driver specified, ignoring this device.
[    10.637] (II) This device may have been added with another device file.
[    10.637] (II) config/udev: Adding input device HDA ATI SB Line Out Surround (/dev/input/event7)
[    10.637] (II) No input driver specified, ignoring this device.
[    10.637] (II) This device may have been added with another device file.
[    10.637] (II) config/udev: Adding input device HDA ATI SB Line Out CLFE (/dev/input/event6)
[    10.637] (II) No input driver specified, ignoring this device.
[    10.637] (II) This device may have been added with another device file.
[    10.638] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    10.638] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    10.638] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    10.638] (**) AT Translated Set 2 keyboard: always reports core events
[    10.638] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    10.638] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    10.638] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    10.638] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    10.638] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    10.638] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 9)
[    10.638] (**) Option "xkb_rules" "evdev"
[    10.638] (**) Option "xkb_model" "pc105"
[    10.638] (**) Option "xkb_layout" "us"
[    10.643] (EE) FBDEV(0): FBIOBLANK: Invalid argument
[    12.530] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    13.478] (II) XKB: reuse xkmfile /var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm
[    14.209] (EE) FBDEV(0): FBIOBLANK: Invalid argument
[    14.248] (EE) FBDEV(0): FBIOBLANK: Invalid argument


```

```
dcmesa@toad:~$ dmesg
...
[    9.051567] init: Failed to spawn hybrid-gfx main process: unable to execute: No such file or directory
[    9.286297] init: kdm main process (1061) killed by TERM signal
[    9.349787] init: gdm main process (1105) killed by TERM signal
[   10.380292] AMD IOMMUv2 driver by Joerg Roedel <joerg.roedel@amd.com>
[   10.380296] AMD IOMMUv2 functionality not available on this system
[   10.386526] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   10.386531] Disabling lock debugging due to kernel taint
[   10.394365] fglrx: module verification failed: signature and/or  required key missing - tainting kernel
[   10.401138] <6>[fglrx] Maximum main memory to use for locked dma buffers: 1633 MBytes.
[   10.401659] <3>[fglrx:firegl_init_device_list] *ERROR* No supported display adapters were found
[   10.401661] <3>[fglrx:firegl_init_module] *ERROR* firegl_init_devices failed
[   10.535407] <6>[fglrx] Maximum main memory to use for locked dma buffers: 1633 MBytes.
[   10.535905] <3>[fglrx:firegl_init_device_list] *ERROR* No supported display adapters were found
[   10.535908] <3>[fglrx:firegl_init_module] *ERROR* firegl_init_devices failed


```

```
dcmesa@toad:~$ cat /etc/X11/xorg.conf

Section "Screen"
        Identifier      "Default Screen"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Default Device"
        Driver  "fglrx"
EndSection
```


I've spent a good chunk of today googling for answers, but couldn't find anything. Any help would be SUPER awesome!

Thank you!

---

### Post by enginerd22 on 2014-09-14
I performed the same upgrade steps and am having the same problem. AMD graphics card as well:

```
01:05.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RS880 [Radeon HD 4200]
```

Did you ever find a solution?

---

### Post by Carlos_Romero on 2014-09-18
Hi, I'm new with Ubuntu, I have an old Toshiba satellite A105-S101 laptop, Something that convinced me to change my windows XP to Linux was that "linux has better compatibility with old hardware" That was an strong point and advantage over windows 7. Well I decided to install ubuntu 14.04. I like the installer, the options, etc... but when I start ubuntu, 30 seconds later the screen freezes and all stops, only the mouse works. Well searching in google, results that my old ATI RADEON Xpress X300m doesn't have a compatibility driver for ubuntu or any other updated OS. :mad:  There are several tutorials, tweaks, command lines, etc but nothing works for me, so... one more time, can anyone help me with this problem? Thanks!

So

---

### Post by djotaku on 2014-09-21
No, never figured it out.

---

### Post by rodeback on 2015-05-10
I have just upgraded and have exactly the same problem as djotaku, also with a HD3300. Apparently, nobody has a solution for the problem, so, is it possible to roll back the upgrade again to 12.04?

---

