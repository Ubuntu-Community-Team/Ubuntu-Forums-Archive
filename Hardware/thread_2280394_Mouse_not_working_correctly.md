---
title: "Mouse not working correctly"
date: 2015-05-30
forum: Hardware
---

### Post by andre45 on 2015-05-30
I got a weird problem with my mouse. After opening a few windows I'm no more able to click on something. The cursor is still working. I can navigate and close windows with the keyboard.
```
lsusb
```lists it correctly. It's a Cyborg R.A.T 5.
Disconnecting and reconnecting solves the problem till the next reboot.

---

### Post by dino99 on 2015-05-30
which ubuntu flavour is it ? you might find some usefull warnings/errors logged either into xorg.0.log or /var/log/dmesg to help you dig around that issue

---

### Post by andre45 on 2015-05-30
I'm using Ubuntu MATE 14.04LTS

Xorg.0.l0g :
```
[     2.408] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[     2.408] X Protocol Version 11, Revision 0
[     2.408] Build Operating System: Linux 3.2.0-76-generic x86_64 Ubuntu
[     2.408] Current Operating System: Linux andre-desktop 3.16.0-38-generic #52~14.04.1-Ubuntu SMP Fri May 8 09:43:57 UTC 2015 x86_64
[     2.408] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.16.0-38-generic root=UUID=2472998e-a367-4b03-88b2-2f11545bede8 ro nomodeset quiet splash vt.handoff=7
[     2.408] Build Date: 12 February 2015  02:49:29PM
[     2.408] xorg-server 2:1.15.1-0ubuntu2.7 (For technical support please see http://www.ubuntu.com/support) 
[     2.408] Current version of pixman: 0.30.2
[     2.408]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[     2.408] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     2.408] (==) Log file: "/var/log/Xorg.0.log", Time: Sat May 30 15:24:58 2015
[     2.408] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     2.408] (==) No Layout section.  Using the first Screen section.
[     2.408] (==) No screen section available. Using defaults.
[     2.408] (**) |-->Screen "Default Screen Section" (0)
[     2.408] (**) |   |-->Monitor "<default monitor>"
[     2.409] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[     2.409] (==) Automatically adding devices
[     2.409] (==) Automatically enabling devices
[     2.409] (==) Automatically adding GPU devices
[     2.409] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     2.409]     Entry deleted from font path.
[     2.409] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     2.409]     Entry deleted from font path.
[     2.409] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     2.409]     Entry deleted from font path.
[     2.409] (WW) The directory "/usr/share/fonts/X11/Type1" does not exist.
[     2.409]     Entry deleted from font path.
[     2.409] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     2.409]     Entry deleted from font path.
[     2.409] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     2.409]     Entry deleted from font path.
[     2.409] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    built-ins
[     2.409] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     2.409] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[     2.409] (II) Loader magic: 0x7f820c262d40
[     2.409] (II) Module ABI versions:
[     2.409]     X.Org ANSI C Emulation: 0.4
[     2.409]     X.Org Video Driver: 15.0
[     2.409]     X.Org XInput driver : 20.0
[     2.409]     X.Org Server Extension : 8.0
[     2.410] (--) PCI:*(0:1:0:0) 1002:679e:1682:3255 rev 0, Mem @ 0xe0000000/268435456, 0xf7e00000/262144, I/O @ 0x0000e000/256, BIOS @ 0x????????/131072
[     2.410] Initializing built-in extension Generic Event Extension
[     2.410] Initializing built-in extension SHAPE
[     2.410] Initializing built-in extension MIT-SHM
[     2.410] Initializing built-in extension XInputExtension
[     2.410] Initializing built-in extension XTEST
[     2.410] Initializing built-in extension BIG-REQUESTS
[     2.410] Initializing built-in extension SYNC
[     2.410] Initializing built-in extension XKEYBOARD
[     2.410] Initializing built-in extension XC-MISC
[     2.410] Initializing built-in extension SECURITY
[     2.410] Initializing built-in extension XINERAMA
[     2.410] Initializing built-in extension XFIXES
[     2.410] Initializing built-in extension RENDER
[     2.410] Initializing built-in extension RANDR
[     2.410] Initializing built-in extension COMPOSITE
[     2.410] Initializing built-in extension DAMAGE
[     2.410] Initializing built-in extension MIT-SCREEN-SAVER
[     2.410] Initializing built-in extension DOUBLE-BUFFER
[     2.410] Initializing built-in extension RECORD
[     2.410] Initializing built-in extension DPMS
[     2.410] Initializing built-in extension Present
[     2.410] Initializing built-in extension DRI3
[     2.410] Initializing built-in extension X-Resource
[     2.410] Initializing built-in extension XVideo
[     2.410] Initializing built-in extension XVideo-MotionCompensation
[     2.410] Initializing built-in extension SELinux
[     2.410] Initializing built-in extension XFree86-VidModeExtension
[     2.410] Initializing built-in extension XFree86-DGA
[     2.410] Initializing built-in extension XFree86-DRI
[     2.410] Initializing built-in extension DRI2
[     2.410] (II) LoadModule: "glx"
[     2.410] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/extensions/libglx.so
[     2.410] (II) Module glx: vendor="Advanced Micro Devices, Inc."
[     2.410]     compiled for 6.9.0, module version = 1.0.0
[     2.410] Loading extension GLX
[     2.410] (==) Matched fglrx as autoconfigured driver 0
[     2.410] (==) Matched ati as autoconfigured driver 1
[     2.410] (==) Matched modesetting as autoconfigured driver 2
[     2.410] (==) Matched fbdev as autoconfigured driver 3
[     2.410] (==) Matched vesa as autoconfigured driver 4
[     2.410] (==) Assigned the driver to the xf86ConfigLayout
[     2.410] (II) LoadModule: "fglrx"
[     2.411] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so
[     2.430] (II) Module fglrx: vendor="FireGL - AMD Technologies Inc."
[     2.430]     compiled for 1.4.99.906, module version = 15.20.2
[     2.430]     Module class: X.Org Video Driver
[     2.430] (II) Loading sub module "fglrxdrm"
[     2.430] (II) LoadModule: "fglrxdrm"
[     2.431] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/linux/libfglrxdrm.so
[     2.432] (II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
[     2.432]     compiled for 1.4.99.906, module version = 15.20.2
[     2.432] (II) LoadModule: "ati"
[     2.432] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[     2.432] (II) Module ati: vendor="X.Org Foundation"
[     2.432]     compiled for 1.15.1, module version = 7.3.0
[     2.432]     Module class: X.Org Video Driver
[     2.433]     ABI class: X.Org Video Driver, version 15.0
[     2.433] (II) LoadModule: "radeon"
[     2.433] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[     2.434] (II) Module radeon: vendor="X.Org Foundation"
[     2.434]     compiled for 1.15.1, module version = 7.3.0
[     2.434]     Module class: X.Org Video Driver
[     2.434]     ABI class: X.Org Video Driver, version 15.0
[     2.434] (II) LoadModule: "modesetting"
[     2.435] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[     2.435] (II) Module modesetting: vendor="X.Org Foundation"
[     2.435]     compiled for 1.15.0, module version = 0.8.1
[     2.435]     Module class: X.Org Video Driver
[     2.435]     ABI class: X.Org Video Driver, version 15.0
[     2.435] (II) LoadModule: "fbdev"
[     2.435] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     2.435] (II) Module fbdev: vendor="X.Org Foundation"
[     2.435]     compiled for 1.15.0, module version = 0.4.4
[     2.435]     Module class: X.Org Video Driver
[     2.435]     ABI class: X.Org Video Driver, version 15.0
[     2.435] (II) LoadModule: "vesa"
[     2.435] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     2.435] (II) Module vesa: vendor="X.Org Foundation"
[     2.435]     compiled for 1.15.0, module version = 2.3.3
[     2.435]     Module class: X.Org Video Driver
[     2.435]     ABI class: X.Org Video Driver, version 15.0
[     2.435] (II) AMD Proprietary Linux Driver Version Identifier:15.20.2
[     2.435] (II) AMD Proprietary Linux Driver Release Identifier: UNSUPPORTED-15.20.1013               
[     2.435] (II) AMD Proprietary Linux Driver Build Date: Feb 27 2015 03:27:32
[     2.435] (II) RADEON: Driver for ATI Radeon chipsets:
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
[     2.438] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[     2.438] (II) FBDEV: driver for framebuffer: fbdev
[     2.438] (II) VESA: driver for VESA chipsets: vesa
[     2.438] (++) using VT number 7

[     2.438] (WW) Falling back to old probe method for fglrx
[     2.457] (II) Loading PCS database from /etc/ati/amdpcsdb /etc/ati/amdpcsdb.default
[     2.458] ukiDynamicMajor: found major device number 251
[     2.459] (--) Assigning device section with no busID to primary device
[     2.459] (--) Chipset Supported AMD Graphics Processor (0x679E) found
[     2.459] (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
[     2.459] (II) fglrx(0): pEnt->device->identifier=0x7f820bffda97
[     2.459] (WW) Falling back to old probe method for modesetting
[     2.459] (EE) open /dev/dri/card0: No such file or directory
[     2.459] (WW) Falling back to old probe method for fbdev
[     2.459] (II) Loading sub module "fbdevhw"
[     2.459] (II) LoadModule: "fbdevhw"
[     2.460] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[     2.460] (II) Module fbdevhw: vendor="X.Org Foundation"
[     2.460]     compiled for 1.15.1, module version = 0.0.2
[     2.460]     ABI class: X.Org Video Driver, version 15.0
[     2.460] (WW) Falling back to old probe method for vesa
[     2.460] (II) fglrx(0): === [xdl_xs115_atiddxPreInit] === begin
[     2.460] (II) fglrx(0): FB driver is enabled
[     2.460] (II) Loading sub module "vgahw"
[     2.460] (II) LoadModule: "vgahw"
[     2.460] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[     2.460] (II) Module vgahw: vendor="X.Org Foundation"
[     2.460]     compiled for 1.15.1, module version = 0.1.0
[     2.460]     ABI class: X.Org Video Driver, version 15.0
[     2.460] (II) fglrx(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[     2.460] (==) fglrx(0): Depth 24, (==) framebuffer bpp 32
[     2.461] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[     2.461] (==) fglrx(0): Default visual is TrueColor
[     2.461] (==) fglrx(0): RGB weight 888
[     2.461] (II) fglrx(0): Using 8 bits per RGB 
[     2.461] (==) fglrx(0): Buffer Tiling is ON
[     2.461] (II) Loading sub module "fglrxdrm"
[     2.461] (II) LoadModule: "fglrxdrm"
[     2.461] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/linux/libfglrxdrm.so
[     2.461] (II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
[     2.461]     compiled for 1.4.99.906, module version = 15.20.2
[     2.462] ukiDynamicMajor: found major device number 251
[     2.462] ukiDynamicMajor: found major device number 251
[     2.462] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[     2.462] ukiOpenDevice: node name is /dev/ati/card0
[     2.462] ukiOpenDevice: open result is 11, (OK)
[     2.788] ukiOpenByBusid: ukiOpenMinor returns 11
[     2.788] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[     2.788] (**) fglrx(0): NoAccel = NO
[     2.788] (**) fglrx(0): AMD 2D Acceleration Architecture enabled
[     2.788] (--) fglrx(0): Chipset: "AMD Radeon HD 7800 Series" (Chipset = 0x679e)
[     2.788] (--) fglrx(0): (PciSubVendor = 0x1682, PciSubDevice = 0x3255)
[     2.788] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original AMD
[     2.788] (--) fglrx(0): Linear framebuffer (phys) at 0xe0000000
[     2.788] (--) fglrx(0): MMIO registers at 0xf7e00000
[     2.788] (--) fglrx(0): I/O port at 0x0000e000
[     2.788] (==) fglrx(0): ROM-BIOS at 0x000c0000
[     2.788] (II) fglrx(0): AC Adapter is used
[     2.788] (II) fglrx(0): Primary V_BIOS segment is: 0xc000
[     2.789] (II) Loading sub module "vbe"
[     2.789] (II) LoadModule: "vbe"
[     2.789] (II) Loading /usr/lib/xorg/modules/libvbe.so
[     2.789] (II) Module vbe: vendor="X.Org Foundation"
[     2.789]     compiled for 1.15.1, module version = 1.1.0
[     2.789]     ABI class: X.Org Video Driver, version 15.0
[     2.789] (II) fglrx(0): VESA BIOS detected
[     2.789] (II) fglrx(0): VESA VBE Version 3.0
[     2.789] (II) fglrx(0): VESA VBE Total Mem: 16384 kB
[     2.789] (II) fglrx(0): VESA VBE OEM: AMD ATOMBIOS
[     2.789] (II) fglrx(0): VESA VBE OEM Software Rev: 15.30
[     2.789] (II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2010, Advanced Micro Devices, Inc.
[     2.789] (II) fglrx(0): VESA VBE OEM Product: 
[     2.789] (II) fglrx(0): VESA VBE OEM Product Rev: 01.00
[     2.789] (II) fglrx(0): AMD Video BIOS revision 9 or later detected
[     2.789] (--) fglrx(0): Video RAM: 2097152 kByte, Type: GDDR5
[     2.789] (II) fglrx(0): PCIE card detected
[     2.789] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
[     2.789] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[     2.789] (II) fglrx(0): [FB] MC range(MCFBBase = 0xf400000000, MCFBSize = 0x80000000)
[     2.789] (II) fglrx(0): RandR 1.2 support is enabled!
[     2.789] (II) fglrx(0): RandR 1.2 rotation support is enabled!
[     2.790] (II) Loading sub module "fb"
[     2.790] (II) LoadModule: "fb"
[     2.790] (II) Loading /usr/lib/xorg/modules/libfb.so
[     2.790] (II) Module fb: vendor="X.Org Foundation"
[     2.790]     compiled for 1.15.1, module version = 1.0.0
[     2.790]     ABI class: X.Org ANSI C Emulation, version 0.4
[     2.790] (II) fglrx(0): EDID Management option: EDID Management is enabled
[     2.790] (II) Loading sub module "ddc"
[     2.790] (II) LoadModule: "ddc"
[     2.790] (II) Module "ddc" already built-in
[     2.940] (II) fglrx(0): Output DFP1 has no monitor section
[     2.941] (II) fglrx(0): Output DFP2 has no monitor section
[     2.941] (II) fglrx(0): Output DFP3 has no monitor section
[     2.941] (II) fglrx(0): Output DFP4 has no monitor section
[     2.941] (II) fglrx(0): Output DFP5 has no monitor section
[     2.941] (II) fglrx(0): Output DFP6 has no monitor section
[     2.941] (II) fglrx(0): Output DFP7 has no monitor section
[     2.941] (II) fglrx(0): Output DFP8 has no monitor section
[     2.941] (II) fglrx(0): Output DFP9 has no monitor section
[     2.941] (II) fglrx(0): Output DFP10 has no monitor section
[     2.941] (II) fglrx(0): Output DFP11 has no monitor section
[     2.941] (II) fglrx(0): Output CRT1 has no monitor section
[     2.941] (II) Loading sub module "ddc"
[     2.941] (II) LoadModule: "ddc"
[     2.941] (II) Module "ddc" already built-in
[     2.941] (II) fglrx(0): Connected Display0: DFP11
[     2.941] (II) fglrx(0): Display0 EDID data ---------------------------
[     2.941] (II) fglrx(0): Manufacturer: ACI  Model: 2498  Serial#: 16843009
[     2.941] (II) fglrx(0): Year: 2012  Week: 22
[     2.941] (II) fglrx(0): EDID Version: 1.3
[     2.941] (II) fglrx(0): Digital Display Input
[     2.941] (II) fglrx(0): Max Image Size [cm]: horiz.: 53  vert.: 30
[     2.941] (II) fglrx(0): Gamma: 2.20
[     2.941] (II) fglrx(0): DPMS capabilities: StandBy Suspend Off
[     2.941] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[     2.941] (II) fglrx(0): First detailed timing is preferred mode
[     2.941] (II) fglrx(0): redX: 0.650 redY: 0.333   greenX: 0.332 greenY: 0.623
[     2.941] (II) fglrx(0): blueX: 0.157 blueY: 0.053   whiteX: 0.313 whiteY: 0.329
[     2.941] (II) fglrx(0): Supported established timings:
[     2.941] (II) fglrx(0): 720x400@70Hz
[     2.941] (II) fglrx(0): 640x480@60Hz
[     2.941] (II) fglrx(0): 640x480@67Hz
[     2.941] (II) fglrx(0): 640x480@72Hz
[     2.941] (II) fglrx(0): 640x480@75Hz
[     2.941] (II) fglrx(0): 800x600@56Hz
[     2.941] (II) fglrx(0): 800x600@60Hz
[     2.941] (II) fglrx(0): 800x600@72Hz
[     2.941] (II) fglrx(0): 800x600@75Hz
[     2.941] (II) fglrx(0): 832x624@75Hz
[     2.941] (II) fglrx(0): 1024x768@60Hz
[     2.941] (II) fglrx(0): 1024x768@70Hz
[     2.941] (II) fglrx(0): 1024x768@75Hz
[     2.941] (II) fglrx(0): 1280x1024@75Hz
[     2.941] (II) fglrx(0): Manufacturer's mask: 0
[     2.941] (II) fglrx(0): Supported standard timings:
[     2.941] (II) fglrx(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[     2.941] (II) fglrx(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[     2.941] (II) fglrx(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[     2.941] (II) fglrx(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
[     2.941] (II) fglrx(0): #4: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
[     2.941] (II) fglrx(0): #5: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[     2.941] (II) fglrx(0): #6: hsize: 1920  vsize 1080  refresh: 60  vid: 49361
[     2.941] (II) fglrx(0): Supported detailed timing:
[     2.941] (II) fglrx(0): clock: 148.5 MHz   Image Size:  531 x 299 mm
[     2.941] (II) fglrx(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[     2.941] (II) fglrx(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[     2.941] (II) fglrx(0): Ranges: V min: 50 V max: 76 Hz, H min: 30 H max: 83 kHz, PixClock max 175 MHz
[     2.941] (II) fglrx(0): Monitor name: VS248
[     2.941] (II) fglrx(0): Serial No: C5LMQS109639
[     2.941] (II) fglrx(0): EDID (in hex):
[     2.941] (II) fglrx(0):     00ffffffffffff000469982401010101
[     2.941] (II) fglrx(0):     1616010380351e78ea9265a655559f28
[     2.941] (II) fglrx(0):     0d5054bfef00714f818081409500a940
[     2.941] (II) fglrx(0):     b300d1c00101023a801871382d40582c
[     2.941] (II) fglrx(0):     4500132b2100001e000000fd00324c1e
[     2.941] (II) fglrx(0):     5311000a202020202020000000fc0056
[     2.941] (II) fglrx(0):     533234380a20202020202020000000ff
[     2.941] (II) fglrx(0):     0043354c4d51533130393633390a00a3
[     2.941] (II) fglrx(0): End of Display0 EDID data --------------------
[     2.941] (II) fglrx(0): Connected Display1: CRT1
[     2.941] (II) fglrx(0): Display1 EDID data ---------------------------
[     2.941] (II) fglrx(0): Manufacturer: ACI  Model: 19f2  Serial#: 200377
[     2.941] (II) fglrx(0): Year: 2013  Week: 43
[     2.941] (II) fglrx(0): EDID Version: 1.3
[     2.941] (II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[     2.941] (II) fglrx(0): Sync:  Separate
[     2.941] (II) fglrx(0): Max Image Size [cm]: horiz.: 41  vert.: 23
[     2.941] (II) fglrx(0): Gamma: 2.20
[     2.941] (II) fglrx(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[     2.941] (II) fglrx(0): First detailed timing is preferred mode
[     2.941] (II) fglrx(0): redX: 0.644 redY: 0.335   greenX: 0.313 greenY: 0.618
[     2.941] (II) fglrx(0): blueX: 0.153 blueY: 0.059   whiteX: 0.313 whiteY: 0.329
[     2.941] (II) fglrx(0): Supported established timings:
[     2.941] (II) fglrx(0): 720x400@70Hz
[     2.941] (II) fglrx(0): 640x480@60Hz
[     2.941] (II) fglrx(0): 640x480@67Hz
[     2.941] (II) fglrx(0): 640x480@72Hz
[     2.941] (II) fglrx(0): 640x480@75Hz
[     2.941] (II) fglrx(0): 800x600@60Hz
[     2.941] (II) fglrx(0): 800x600@72Hz
[     2.941] (II) fglrx(0): 800x600@75Hz
[     2.941] (II) fglrx(0): 832x624@75Hz
[     2.941] (II) fglrx(0): 1024x768@60Hz
[     2.941] (II) fglrx(0): 1024x768@70Hz
[     2.941] (II) fglrx(0): 1024x768@75Hz
[     2.941] (II) fglrx(0): Manufacturer's mask: 0
[     2.941] (II) fglrx(0): Supported standard timings:
[     2.941] (II) fglrx(0): #0: hsize: 1280  vsize 720  refresh: 60  vid: 49281
[     2.941] (II) fglrx(0): Supported detailed timing:
[     2.941] (II) fglrx(0): clock: 85.5 MHz   Image Size:  410 x 230 mm
[     2.941] (II) fglrx(0): h_active: 1366  h_sync: 1436  h_sync_end 1579 h_blank_end 1792 h_border: 0
[     2.941] (II) fglrx(0): v_active: 768  v_sync: 771  v_sync_end 774 v_blanking: 798 v_border: 0
[     2.941] (II) fglrx(0): Ranges: V min: 50 V max: 75 Hz, H min: 24 H max: 83 kHz, PixClock max 175 MHz
[     2.941] (II) fglrx(0): Monitor name: ASUS VS197
[     2.941] (II) fglrx(0): Serial No: DALMTF200377
[     2.941] (II) fglrx(0): EDID (in hex):
[     2.941] (II) fglrx(0):     00ffffffffffff000469f219b90e0300
[     2.941] (II) fglrx(0):     2b17010308291778eaf545a455509e27
[     2.941] (II) fglrx(0):     0f5054bdee0081c00101010101010101
[     2.941] (II) fglrx(0):     010101010101662156aa51001e30468f
[     2.941] (II) fglrx(0):     33009ae61000001e000000fd00324b18
[     2.941] (II) fglrx(0):     5311000a202020202020000000fc0041
[     2.941] (II) fglrx(0):     5355532056533139370a2020000000ff
[     2.941] (II) fglrx(0):     0044414c4d54463230303337370a0063
[     2.941] (II) fglrx(0): End of Display1 EDID data --------------------
[     2.941] (II) fglrx(0): Dynamic Surface Resizing Enabled
[     2.942] (II) fglrx(0): EDID for output DFP1
[     2.942] (II) fglrx(0): EDID for output DFP2
[     2.942] (II) fglrx(0): EDID for output DFP3
[     2.942] (II) fglrx(0): EDID for output DFP4
[     2.942] (II) fglrx(0): EDID for output DFP5
[     2.942] (II) fglrx(0): EDID for output DFP6
[     2.942] (II) fglrx(0): EDID for output DFP7
[     2.942] (II) fglrx(0): EDID for output DFP8
[     2.942] (II) fglrx(0): EDID for output DFP9
[     2.942] (II) fglrx(0): EDID for output DFP10
[     2.942] (II) fglrx(0): EDID for output DFP11
[     2.942] (II) fglrx(0): Manufacturer: ACI  Model: 2498  Serial#: 16843009
[     2.942] (II) fglrx(0): Year: 2012  Week: 22
[     2.942] (II) fglrx(0): EDID Version: 1.3
[     2.942] (II) fglrx(0): Digital Display Input
[     2.942] (II) fglrx(0): Max Image Size [cm]: horiz.: 53  vert.: 30
[     2.942] (II) fglrx(0): Gamma: 2.20
[     2.942] (II) fglrx(0): DPMS capabilities: StandBy Suspend Off
[     2.942] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[     2.942] (II) fglrx(0): First detailed timing is preferred mode
[     2.942] (II) fglrx(0): redX: 0.650 redY: 0.333   greenX: 0.332 greenY: 0.623
[     2.942] (II) fglrx(0): blueX: 0.157 blueY: 0.053   whiteX: 0.313 whiteY: 0.329
[     2.942] (II) fglrx(0): Supported established timings:
[     2.942] (II) fglrx(0): 720x400@70Hz
[     2.942] (II) fglrx(0): 640x480@60Hz
[     2.942] (II) fglrx(0): 640x480@67Hz
[     2.942] (II) fglrx(0): 640x480@72Hz
[     2.942] (II) fglrx(0): 640x480@75Hz
[     2.942] (II) fglrx(0): 800x600@56Hz
[     2.942] (II) fglrx(0): 800x600@60Hz
[     2.942] (II) fglrx(0): 800x600@72Hz
[     2.942] (II) fglrx(0): 800x600@75Hz
[     2.942] (II) fglrx(0): 832x624@75Hz
[     2.942] (II) fglrx(0): 1024x768@60Hz
[     2.942] (II) fglrx(0): 1024x768@70Hz
[     2.942] (II) fglrx(0): 1024x768@75Hz
[     2.942] (II) fglrx(0): 1280x1024@75Hz
[     2.942] (II) fglrx(0): Manufacturer's mask: 0
[     2.942] (II) fglrx(0): Supported standard timings:
[     2.942] (II) fglrx(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[     2.942] (II) fglrx(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[     2.942] (II) fglrx(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[     2.942] (II) fglrx(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
[     2.942] (II) fglrx(0): #4: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
[     2.942] (II) fglrx(0): #5: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[     2.942] (II) fglrx(0): #6: hsize: 1920  vsize 1080  refresh: 60  vid: 49361
[     2.942] (II) fglrx(0): Supported detailed timing:
[     2.942] (II) fglrx(0): clock: 148.5 MHz   Image Size:  531 x 299 mm
[     2.942] (II) fglrx(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[     2.942] (II) fglrx(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[     2.942] (II) fglrx(0): Ranges: V min: 50 V max: 76 Hz, H min: 30 H max: 83 kHz, PixClock max 175 MHz
[     2.942] (II) fglrx(0): Monitor name: VS248
[     2.942] (II) fglrx(0): Serial No: C5LMQS109639
[     2.942] (II) fglrx(0): EDID (in hex):
[     2.942] (II) fglrx(0):     00ffffffffffff000469982401010101
[     2.942] (II) fglrx(0):     1616010380351e78ea9265a655559f28
[     2.942] (II) fglrx(0):     0d5054bfef00714f818081409500a940
[     2.942] (II) fglrx(0):     b300d1c00101023a801871382d40582c
[     2.942] (II) fglrx(0):     4500132b2100001e000000fd00324c1e
[     2.942] (II) fglrx(0):     5311000a202020202020000000fc0056
[     2.942] (II) fglrx(0):     533234380a20202020202020000000ff
[     2.942] (II) fglrx(0):     0043354c4d51533130393633390a00a3
[     2.942] (II) fglrx(0): Printing probed modes for output DFP11
[     2.942] (II) fglrx(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[     2.942] (II) fglrx(0): Modeline "1680x1050"x60.0  148.50  1680 2008 2052 2200  1050 1084 1089 1125 +hsync +vsync (67.5 kHz e)
[     2.942] (II) fglrx(0): Modeline "1400x1050"x60.0  148.50  1400 2008 2052 2200  1050 1084 1089 1125 +hsync +vsync (67.5 kHz e)
[     2.942] (II) fglrx(0): Modeline "1600x900"x60.0  148.50  1600 2008 2052 2200  900 1084 1089 1125 +hsync +vsync (67.5 kHz e)
[     2.942] (II) fglrx(0): Modeline "1360x1024"x60.0  148.50  1360 2008 2052 2200  1024 1084 1089 1125 +hsync +vsync (67.5 kHz e)
[     2.942] (II) fglrx(0): Modeline "1280x1024"x60.0  148.50  1280 2008 2052 2200  1024 1084 1089 1125 +hsync +vsync (67.5 kHz e)
[     2.942] (II) fglrx(0): Modeline "1440x900"x60.0  148.50  1440 2008 2052 2200  900 1084 1089 1125 +hsync +vsync (67.5 kHz e)
[     2.942] (II) fglrx(0): Modeline "1280x960"x60.0  148.50  1280 2008 2052 2200  960 1084 1089 1125 +hsync +vsync (67.5 kHz e)
[     2.942] (II) fglrx(0): Modeline "1280x900"x60.0  148.50  1280 2008 2052 2200  900 1084 1089 1125 +hsync +vsync (67.5 kHz e)
[     2.942] (II) fglrx(0): Modeline "1360x768"x60.0  148.50  1360 2008 2052 2200  768 1084 1089 1125 +hsync +vsync (67.5 kHz e)
[     2.942] (II) fglrx(0): Modeline "1280x800"x60.0  148.50  1280 2008 2052 2200  800 1084 1089 1125 +hsync +vsync (67.5 kHz e)
[     2.942] (II) fglrx(0): Modeline "1152x864"x60.0  148.50  1152 2008 2052 2200  864 1084 1089 1125 +hsync +vsync (67.5 kHz e)
[     2.943] (II) fglrx(0): Modeline "1280x768"x60.0  148.50  1280 2008 2052 2200  768 1084 1089 1125 +hsync +vsync (67.5 kHz e)
[     2.943] (II) fglrx(0): Modeline "1280x720"x60.0  148.50  1280 2008 2052 2200  720 1084 1089 1125 +hsync +vsync (67.5 kHz e)
[     2.943] (II) fglrx(0): Modeline "1024x768"x60.0  148.50  1024 2008 2052 2200  768 1084 1089 1125 +hsync +vsync (67.5 kHz e)
[     2.943] (II) fglrx(0): Modeline "800x600"x60.0  148.50  800 2008 2052 2200  600 1084 1089 1125 +hsync +vsync (67.5 kHz e)
[     2.943] (II) fglrx(0): Modeline "848x480"x60.0  148.50  848 2008 2052 2200  480 1084 1089 1125 +hsync +vsync (67.5 kHz e)
[     2.943] (II) fglrx(0): Modeline "720x480"x60.0  148.50  720 2008 2052 2200  480 1084 1089 1125 +hsync +vsync (67.5 kHz e)
[     2.943] (II) fglrx(0): Modeline "640x480"x60.0  148.50  640 2008 2052 2200  480 1084 1089 1125 +hsync +vsync (67.5 kHz e)
[     2.943] (II) fglrx(0): EDID for output CRT1
[     2.943] (II) fglrx(0): Manufacturer: ACI  Model: 19f2  Serial#: 200377
[     2.943] (II) fglrx(0): Year: 2013  Week: 43
[     2.943] (II) fglrx(0): EDID Version: 1.3
[     2.943] (II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[     2.943] (II) fglrx(0): Sync:  Separate
[     2.943] (II) fglrx(0): Max Image Size [cm]: horiz.: 41  vert.: 23
[     2.943] (II) fglrx(0): Gamma: 2.20
[     2.943] (II) fglrx(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[     2.943] (II) fglrx(0): First detailed timing is preferred mode
[     2.943] (II) fglrx(0): redX: 0.644 redY: 0.335   greenX: 0.313 greenY: 0.618
[     2.943] (II) fglrx(0): blueX: 0.153 blueY: 0.059   whiteX: 0.313 whiteY: 0.329
[     2.943] (II) fglrx(0): Supported established timings:
[     2.943] (II) fglrx(0): 720x400@70Hz
[     2.943] (II) fglrx(0): 640x480@60Hz
[     2.943] (II) fglrx(0): 640x480@67Hz
[     2.943] (II) fglrx(0): 640x480@72Hz
[     2.943] (II) fglrx(0): 640x480@75Hz
[     2.943] (II) fglrx(0): 800x600@60Hz
[     2.943] (II) fglrx(0): 800x600@72Hz
[     2.943] (II) fglrx(0): 800x600@75Hz
[     2.943] (II) fglrx(0): 832x624@75Hz
[     2.943] (II) fglrx(0): 1024x768@60Hz
[     2.943] (II) fglrx(0): 1024x768@70Hz
[     2.943] (II) fglrx(0): 1024x768@75Hz
[     2.943] (II) fglrx(0): Manufacturer's mask: 0
[     2.943] (II) fglrx(0): Supported standard timings:
[     2.943] (II) fglrx(0): #0: hsize: 1280  vsize 720  refresh: 60  vid: 49281
[     2.943] (II) fglrx(0): Supported detailed timing:
[     2.943] (II) fglrx(0): clock: 85.5 MHz   Image Size:  410 x 230 mm
[     2.943] (II) fglrx(0): h_active: 1366  h_sync: 1436  h_sync_end 1579 h_blank_end 1792 h_border: 0
[     2.943] (II) fglrx(0): v_active: 768  v_sync: 771  v_sync_end 774 v_blanking: 798 v_border: 0
[     2.943] (II) fglrx(0): Ranges: V min: 50 V max: 75 Hz, H min: 24 H max: 83 kHz, PixClock max 175 MHz
[     2.943] (II) fglrx(0): Monitor name: ASUS VS197
[     2.943] (II) fglrx(0): Serial No: DALMTF200377
[     2.943] (II) fglrx(0): EDID (in hex):
[     2.943] (II) fglrx(0):     00ffffffffffff000469f219b90e0300
[     2.943] (II) fglrx(0):     2b17010308291778eaf545a455509e27
[     2.943] (II) fglrx(0):     0f5054bdee0081c00101010101010101
[     2.943] (II) fglrx(0):     010101010101662156aa51001e30468f
[     2.943] (II) fglrx(0):     33009ae61000001e000000fd00324b18
[     2.943] (II) fglrx(0):     5311000a202020202020000000fc0041
[     2.943] (II) fglrx(0):     5355532056533139370a2020000000ff
[     2.943] (II) fglrx(0):     0044414c4d54463230303337370a0063
[     2.943] (II) fglrx(0): Printing probed modes for output CRT1
[     2.943] (II) fglrx(0): Modeline "1366x768"x60.0   85.50  1366 1436 1579 1792  768 771 774 798 +hsync +vsync (47.7 kHz eP)
[     2.943] (II) fglrx(0): Modeline "1360x768"x60.0   85.50  1360 1436 1579 1792  768 771 774 798 +hsync +vsync (47.7 kHz e)
[     2.943] (II) fglrx(0): Modeline "1280x768"x60.0   85.50  1280 1436 1579 1792  768 771 774 798 +hsync +vsync (47.7 kHz e)
[     2.943] (II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[     2.943] (II) fglrx(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[     2.943] (II) fglrx(0): Modeline "1024x768"x70.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[     2.943] (II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[     2.943] (II) fglrx(0): Modeline "800x600"x72.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[     2.943] (II) fglrx(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[     2.943] (II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[     2.943] (II) fglrx(0): Modeline "848x480"x75.0   78.75  848 1040 1136 1312  480 769 772 800 +hsync +vsync (60.0 kHz e)
[     2.943] (II) fglrx(0): Modeline "848x480"x70.0   75.00  848 1048 1184 1328  480 771 777 806 -hsync -vsync (56.5 kHz e)
[     2.943] (II) fglrx(0): Modeline "848x480"x60.0   65.00  848 1048 1184 1344  480 771 777 806 -hsync -vsync (48.4 kHz e)
[     2.943] (II) fglrx(0): Modeline "720x480"x72.0   50.00  720 856 976 1040  480 637 643 666 +hsync +vsync (48.1 kHz e)
[     2.943] (II) fglrx(0): Modeline "720x480"x75.0   49.50  720 816 896 1056  480 601 604 625 +hsync +vsync (46.9 kHz e)
[     2.943] (II) fglrx(0): Modeline "720x480"x60.0   40.00  720 840 968 1056  480 601 605 628 +hsync +vsync (37.9 kHz e)
[     2.943] (II) fglrx(0): Modeline "640x480"x72.0   31.50  640 656 696 832  480 481 484 520 -hsync -vsync (37.9 kHz e)
[     2.943] (II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[     2.943] (II) fglrx(0): Modeline "640x480"x67.0   27.28  640 664 728 816  480 481 484 499 -hsync +vsync (33.4 kHz e)
[     2.943] (II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[     2.943] (II) fglrx(0): Output DFP1 disconnected
[     2.943] (II) fglrx(0): Output DFP2 disconnected
[     2.943] (II) fglrx(0): Output DFP3 disconnected
[     2.943] (II) fglrx(0): Output DFP4 disconnected
[     2.943] (II) fglrx(0): Output DFP5 disconnected
[     2.943] (II) fglrx(0): Output DFP6 disconnected
[     2.943] (II) fglrx(0): Output DFP7 disconnected
[     2.943] (II) fglrx(0): Output DFP8 disconnected
[     2.943] (II) fglrx(0): Output DFP9 disconnected
[     2.943] (II) fglrx(0): Output DFP10 disconnected
[     2.943] (II) fglrx(0): Output DFP11 connected
[     2.943] (II) fglrx(0): Output CRT1 connected
[     2.943] (II) fglrx(0): Using fuzzy aspect match for initial modes
[     2.943] (II) fglrx(0): Output DFP11 using initial mode 1360x768
[     2.943] (II) fglrx(0): Output CRT1 using initial mode 1360x768
[     2.943] (II) fglrx(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[     2.943] (II) fglrx(0): DPI set to (96, 96)
[     2.943] (II) fglrx(0): Eyefinity capable adapter detected.
[     2.943] (II) fglrx(0): Adapter AMD Radeon HD 7800 Series has 6 configurable heads and 2 displays connected.
[     2.943] (==) fglrx(0):  PseudoColor visuals disabled
[     2.943] (II) Loading sub module "ramdac"
[     2.943] (II) LoadModule: "ramdac"
[     2.943] (II) Module "ramdac" already built-in
[     2.943] (==) fglrx(0): NoDRI = NO
[     2.943] (==) fglrx(0): Capabilities: 0x00000000
[     2.943] (==) fglrx(0): CapabilitiesEx: 0x00000000
[     2.943] (==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
[     2.943] (==) fglrx(0): UseFastTLS=0
[     2.943] (II) fglrx(0): Shadow Primary option: ShadowPrimary is enabled
[     2.943] (II) UnloadModule: "radeon"
[     2.943] (II) Unloading radeon
[     2.943] (II) UnloadModule: "modesetting"
[     2.943] (II) Unloading modesetting
[     2.944] (II) UnloadModule: "fbdev"
[     2.944] (II) Unloading fbdev
[     2.944] (II) UnloadSubModule: "fbdevhw"
[     2.944] (II) Unloading fbdevhw
[     2.944] (II) UnloadModule: "vesa"
[     2.944] (II) Unloading vesa
[     2.944] (--) Depth 24 pixmap format is 32 bpp
[     2.946] Loading extension ATIFGLRXDRI
[     2.946] (II) fglrx(0): doing swlDriScreenInit
[     2.946] (II) fglrx(0): swlDriScreenInit for fglrx driver
[     2.946] ukiDynamicMajor: found major device number 251
[     2.946] ukiDynamicMajor: found major device number 251
[     2.946] ukiDynamicMajor: found major device number 251
[     2.946] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[     2.946] ukiOpenDevice: node name is /dev/ati/card0
[     2.946] ukiOpenDevice: open result is 12, (OK)
[     2.946] ukiOpenByBusid: ukiOpenMinor returns 12
[     2.946] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[     2.946] (II) fglrx(0): [uki] DRM interface version 1.0
[     2.946] (II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:1:0:0"
[     2.946] (II) fglrx(0): [uki] added 8192 byte SAREA at 0x2000
[     2.946] (II) fglrx(0): [uki] mapped SAREA 0x2000 to 0x7f820be1c000
[     2.946] (II) fglrx(0): [uki] framebuffer handle = 0x3000
[     2.946] (II) fglrx(0): [uki] added 1 reserved context for kernel
[     2.946] (II) fglrx(0): swlDriScreenInit done
[     2.946] (II) fglrx(0): Kernel Module Version Information:
[     2.946] (II) fglrx(0):     Name: fglrx
[     2.946] (II) fglrx(0):     Version: 15.20.2
[     2.946] (II) fglrx(0):     Date: Feb 27 2015
[     2.946] (II) fglrx(0):     Desc: AMD FireGL DRM kernel module
[     2.946] (II) fglrx(0): Kernel Module version matches driver.
[     2.946] (II) fglrx(0): Kernel Module Build Time Information:
[     2.946] (II) fglrx(0):     Build-Kernel UTS_RELEASE:        3.16.0-38-generic
[     2.946] (II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
[     2.946] (II) fglrx(0):     Build-Kernel __SMP__:            yes
[     2.946] (II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
[     2.946] (II) fglrx(0): [uki] register handle = 0x00004000
[     2.946] (II) fglrx(0): DRI initialization successfull
[     2.948] (II) fglrx(0): FBADPhys: 0xf400000000 FBMappedSize: 0x01080000
[     2.949] (==) fglrx(0): Backing store enabled
[     2.949] Loading extension FGLRXEXTENSION
[     2.949] (==) fglrx(0): DPMS enabled
[     2.950] (II) fglrx(0): Initialized in-driver Xinerama extension
[     2.950] (**) fglrx(0): Textured Video is enabled.
[     2.950] (II) LoadModule: "glesx"
[     2.950] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/glesx.so
[     2.951] (II) Module glesx: vendor="X.Org Foundation"
[     2.951]     compiled for 1.4.99.906, module version = 1.0.0
[     2.951] Loading extension GLESX
[     2.951] (II) fglrx(0): GLESX enableFlags = 8784
[     2.952] (II) fglrx(0): GLESX is enabled
[     2.952] (II) LoadModule: "amdxmm"
[     2.952] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/amdxmm.so
[     2.952] (II) Module amdxmm: vendor="X.Org Foundation"
[     2.952]     compiled for 1.4.99.906, module version = 2.0.0
[     2.966] Loading extension AMDXVOPL
[     2.966] Loading extension AMDXVBA
[     2.967] (II) fglrx(0): UVD feature is enabled(II) fglrx(0): 
[     2.974] (II) fglrx(0): Enable composite support successfully
[     2.974] (II) fglrx(0): X context handle = 0x1
[     2.974] (II) fglrx(0): [DRI] installation complete
[     2.974] (==) fglrx(0): Silken mouse enabled
[     2.974] (==) fglrx(0): Using HW cursor of display infrastructure!
[     2.975] (II) fglrx(0): LPT is disabled by configure option
[     2.975] (II) fglrx(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[     3.183] (--) RandR disabled
[     3.189] (II) SELinux: Disabled on system
[     3.190] ukiDynamicMajor: found major device number 251
[     3.190] ukiDynamicMajor: found major device number 251
[     3.190] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[     3.190] ukiOpenDevice: node name is /dev/ati/card0
[     3.190] ukiOpenDevice: open result is 13, (OK)
[     3.190] ukiOpenByBusid: ukiOpenMinor returns 13
[     3.190] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[     3.190] (EE) AIGLX error: failed to open /usr/X11R6/lib64/modules/dri/fglrx_dri.so, error[/usr/X11R6/lib64/modules/dri/fglrx_dri.so: cannot open shared object file: No such file or directory]
[     3.190] (EE) AIGLX error: failed to open /usr/lib64/dri/fglrx_dri.so, error[/usr/lib64/dri/fglrx_dri.so: cannot open shared object file: No such file or directory]
[     3.190] (EE) AIGLX error: failed to open /usr/X11R6/lib/modules/dri/fglrx_dri.so, error[/usr/X11R6/lib/modules/dri/fglrx_dri.so: cannot open shared object file: No such file or directory]
[     3.194] ukiDynamicMajor: found major device number 251
[     3.194] ukiDynamicMajor: found major device number 251
[     3.194] ukiDynamicMajor: found major device number 251
[     3.194] ukiOpenDevice: node name is /dev/ati/card0
[     3.194] ukiOpenDevice: open result is 14, (OK)
[     3.194] ukiGetBusid returned 'PCI:1:0:0'
[     3.194] ukiOpenDevice: node name is /dev/ati/card1
[     3.194] ukiOpenDevice: open result is -1, (No such device)
[     3.194] ukiOpenDevice: open result is -1, (No such device)
[     3.194] ukiOpenDevice: Open failed
[     3.194] ukiOpenDevice: node name is /dev/ati/card2
[     3.194] ukiOpenDevice: open result is -1, (No such device)
[     3.194] ukiOpenDevice: open result is -1, (No such device)
[     3.194] ukiOpenDevice: Open failed
[     3.194] ukiOpenDevice: node name is /dev/ati/card3
[     3.194] ukiOpenDevice: open result is -1, (No such device)
[     3.194] ukiOpenDevice: open result is -1, (No such device)
[     3.194] ukiOpenDevice: Open failed
[     3.194] ukiOpenDevice: node name is /dev/ati/card4
[     3.194] ukiOpenDevice: open result is -1, (No such device)
[     3.194] ukiOpenDevice: open result is -1, (No such device)
[     3.194] ukiOpenDevice: Open failed
[     3.194] ukiOpenDevice: node name is /dev/ati/card5
[     3.194] ukiOpenDevice: open result is -1, (No such device)
[     3.194] ukiOpenDevice: open result is -1, (No such device)
[     3.194] ukiOpenDevice: Open failed
[     3.194] ukiOpenDevice: node name is /dev/ati/card6
[     3.194] ukiOpenDevice: open result is -1, (No such device)
[     3.194] ukiOpenDevice: open result is -1, (No such device)
[     3.194] ukiOpenDevice: Open failed
[     3.194] ukiOpenDevice: node name is /dev/ati/card7
[     3.194] ukiOpenDevice: open result is -1, (No such device)
[     3.194] ukiOpenDevice: open result is -1, (No such device)
[     3.194] ukiOpenDevice: Open failed
[     3.194] ukiOpenDevice: node name is /dev/ati/card8
[     3.194] ukiOpenDevice: open result is -1, (No such device)
[     3.194] ukiOpenDevice: open result is -1, (No such device)
[     3.194] ukiOpenDevice: Open failed
[     3.194] ukiOpenDevice: node name is /dev/ati/card9
[     3.194] ukiOpenDevice: open result is -1, (No such device)
[     3.194] ukiOpenDevice: open result is -1, (No such device)
[     3.194] ukiOpenDevice: Open failed
[     3.194] ukiOpenDevice: node name is /dev/ati/card10
[     3.194] ukiOpenDevice: open result is -1, (No such device)
[     3.194] ukiOpenDevice: open result is -1, (No such device)
[     3.194] ukiOpenDevice: Open failed
[     3.194] ukiOpenDevice: node name is /dev/ati/card11
[     3.194] ukiOpenDevice: open result is -1, (No such device)
[     3.194] ukiOpenDevice: open result is -1, (No such device)
[     3.194] ukiOpenDevice: Open failed
[     3.194] ukiOpenDevice: node name is /dev/ati/card12
[     3.194] ukiOpenDevice: open result is -1, (No such device)
[     3.194] ukiOpenDevice: open result is -1, (No such device)
[     3.194] ukiOpenDevice: Open failed
[     3.194] ukiOpenDevice: node name is /dev/ati/card13
[     3.194] ukiOpenDevice: open result is -1, (No such device)
[     3.194] ukiOpenDevice: open result is -1, (No such device)
[     3.194] ukiOpenDevice: Open failed
[     3.194] ukiOpenDevice: node name is /dev/ati/card14
[     3.194] ukiOpenDevice: open result is -1, (No such device)
[     3.194] ukiOpenDevice: open result is -1, (No such device)
[     3.194] ukiOpenDevice: Open failed
[     3.194] ukiOpenDevice: node name is /dev/ati/card15
[     3.194] ukiOpenDevice: open result is -1, (No such device)
[     3.194] ukiOpenDevice: open result is -1, (No such device)
[     3.194] ukiOpenDevice: Open failed
[     3.194] ukiDynamicMajor: found major device number 251
[     3.194] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[     3.194] ukiOpenDevice: node name is /dev/ati/card0
[     3.194] ukiOpenDevice: open result is 14, (OK)
[     3.194] ukiOpenByBusid: ukiOpenMinor returns 14
[     3.194] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[     3.226] (II) AIGLX: Loaded and initialized OpenGL driver(II) GLX: Initialized DRI GL provider for screen 0
[     3.226] ukiDynamicMajor: found major device number 251
[     3.226] ukiDynamicMajor: found major device number 251
[     3.227] ukiDynamicMajor: found major device number 251
[     3.227] ukiOpenDevice: node name is /dev/ati/card0
[     3.227] ukiOpenDevice: open result is 15, (OK)
[     3.227] ukiGetBusid returned 'PCI:1:0:0'
[     3.227] ukiOpenDevice: node name is /dev/ati/card1
[     3.227] ukiOpenDevice: open result is -1, (No such device)
[     3.227] ukiOpenDevice: open result is -1, (No such device)
[     3.227] ukiOpenDevice: Open failed
[     3.227] ukiOpenDevice: node name is /dev/ati/card2
[     3.227] ukiOpenDevice: open result is -1, (No such device)
[     3.227] ukiOpenDevice: open result is -1, (No such device)
[     3.227] ukiOpenDevice: Open failed
[     3.227] ukiOpenDevice: node name is /dev/ati/card3
[     3.227] ukiOpenDevice: open result is -1, (No such device)
[     3.227] ukiOpenDevice: open result is -1, (No such device)
[     3.227] ukiOpenDevice: Open failed
[     3.227] ukiOpenDevice: node name is /dev/ati/card4
[     3.227] ukiOpenDevice: open result is -1, (No such device)
[     3.227] ukiOpenDevice: open result is -1, (No such device)
[     3.227] ukiOpenDevice: Open failed
[     3.227] ukiOpenDevice: node name is /dev/ati/card5
[     3.227] ukiOpenDevice: open result is -1, (No such device)
[     3.227] ukiOpenDevice: open result is -1, (No such device)
[     3.227] ukiOpenDevice: Open failed
[     3.227] ukiOpenDevice: node name is /dev/ati/card6
[     3.227] ukiOpenDevice: open result is -1, (No such device)
[     3.227] ukiOpenDevice: open result is -1, (No such device)
[     3.227] ukiOpenDevice: Open failed
[     3.227] ukiOpenDevice: node name is /dev/ati/card7
[     3.227] ukiOpenDevice: open result is -1, (No such device)
[     3.227] ukiOpenDevice: open result is -1, (No such device)
[     3.227] ukiOpenDevice: Open failed
[     3.227] ukiOpenDevice: node name is /dev/ati/card8
[     3.227] ukiOpenDevice: open result is -1, (No such device)
[     3.227] ukiOpenDevice: open result is -1, (No such device)
[     3.227] ukiOpenDevice: Open failed
[     3.227] ukiOpenDevice: node name is /dev/ati/card9
[     3.227] ukiOpenDevice: open result is -1, (No such device)
[     3.227] ukiOpenDevice: open result is -1, (No such device)
[     3.227] ukiOpenDevice: Open failed
[     3.227] ukiOpenDevice: node name is /dev/ati/card10
[     3.227] ukiOpenDevice: open result is -1, (No such device)
[     3.227] ukiOpenDevice: open result is -1, (No such device)
[     3.227] ukiOpenDevice: Open failed
[     3.227] ukiOpenDevice: node name is /dev/ati/card11
[     3.227] ukiOpenDevice: open result is -1, (No such device)
[     3.227] ukiOpenDevice: open result is -1, (No such device)
[     3.227] ukiOpenDevice: Open failed
[     3.227] ukiOpenDevice: node name is /dev/ati/card12
[     3.227] ukiOpenDevice: open result is -1, (No such device)
[     3.227] ukiOpenDevice: open result is -1, (No such device)
[     3.227] ukiOpenDevice: Open failed
[     3.227] ukiOpenDevice: node name is /dev/ati/card13
[     3.227] ukiOpenDevice: open result is -1, (No such device)
[     3.227] ukiOpenDevice: open result is -1, (No such device)
[     3.227] ukiOpenDevice: Open failed
[     3.227] ukiOpenDevice: node name is /dev/ati/card14
[     3.227] ukiOpenDevice: open result is -1, (No such device)
[     3.227] ukiOpenDevice: open result is -1, (No such device)
[     3.227] ukiOpenDevice: Open failed
[     3.227] ukiOpenDevice: node name is /dev/ati/card15
[     3.227] ukiOpenDevice: open result is -1, (No such device)
[     3.227] ukiOpenDevice: open result is -1, (No such device)
[     3.227] ukiOpenDevice: Open failed
[     3.227] ukiDynamicMajor: found major device number 251
[     3.227] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[     3.227] ukiOpenDevice: node name is /dev/ati/card0
[     3.227] ukiOpenDevice: open result is 15, (OK)
[     3.227] ukiOpenByBusid: ukiOpenMinor returns 15
[     3.227] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[     3.233] (II) fglrx(0): OverDrive5 Detected!
[     3.235] (II) fglrx(0): Setting screen physical size to 359 x 203
[     3.240] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[     3.241] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[     3.241] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     3.241] (**) Power Button: Applying InputClass "keyboard defaults"
[     3.241] (II) LoadModule: "evdev"
[     3.242] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     3.242] (II) Module evdev: vendor="X.Org Foundation"
[     3.242]     compiled for 1.15.0, module version = 2.8.2
[     3.242]     Module class: X.Org XInput Driver
[     3.242]     ABI class: X.Org XInput driver, version 20.0
[     3.242] (II) Using input driver 'evdev' for 'Power Button'
[     3.242] (**) Power Button: always reports core events
[     3.242] (**) evdev: Power Button: Device: "/dev/input/event1"
[     3.242] (--) evdev: Power Button: Vendor 0 Product 0x1
[     3.242] (--) evdev: Power Button: Found keys
[     3.242] (II) evdev: Power Button: Configuring as keyboard
[     3.242] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[     3.242] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[     3.242] (**) Option "xkb_rules" "evdev"
[     3.242] (**) Option "xkb_model" "pc105"
[     3.242] (**) Option "xkb_layout" "de"
[     3.242] (**) Option "xkb_options" "terminate:ctrl_alt_bksp"
[     3.243] (II) XKB: reuse xkmfile /var/lib/xkb/server-1BCDDEFD4E35562D3483623A3498B96EFC960598.xkm
[     3.244] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[     3.244] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     3.244] (**) Power Button: Applying InputClass "keyboard defaults"
[     3.244] (II) Using input driver 'evdev' for 'Power Button'
[     3.244] (**) Power Button: always reports core events
[     3.244] (**) evdev: Power Button: Device: "/dev/input/event0"
[     3.244] (--) evdev: Power Button: Vendor 0 Product 0x1
[     3.244] (--) evdev: Power Button: Found keys
[     3.244] (II) evdev: Power Button: Configuring as keyboard
[     3.244] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[     3.244] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[     3.244] (**) Option "xkb_rules" "evdev"
[     3.244] (**) Option "xkb_model" "pc105"
[     3.244] (**) Option "xkb_layout" "de"
[     3.244] (**) Option "xkb_options" "terminate:ctrl_alt_bksp"
[     3.244] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=11 (/dev/input/event7)
[     3.244] (II) No input driver specified, ignoring this device.
[     3.244] (II) This device may have been added with another device file.
[     3.244] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=3 (/dev/input/event2)
[     3.244] (II) No input driver specified, ignoring this device.
[     3.244] (II) This device may have been added with another device file.
[     3.245] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=7 (/dev/input/event3)
[     3.245] (II) No input driver specified, ignoring this device.
[     3.245] (II) This device may have been added with another device file.
[     3.245] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=8 (/dev/input/event4)
[     3.245] (II) No input driver specified, ignoring this device.
[     3.245] (II) This device may have been added with another device file.
[     3.245] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=9 (/dev/input/event5)
[     3.245] (II) No input driver specified, ignoring this device.
[     3.245] (II) This device may have been added with another device file.
[     3.245] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=10 (/dev/input/event6)
[     3.245] (II) No input driver specified, ignoring this device.
[     3.245] (II) This device may have been added with another device file.
[     3.245] (II) config/udev: Adding input device Saitek Cyborg R.A.T.5 Mouse (/dev/input/event15)
[     3.245] (**) Saitek Cyborg R.A.T.5 Mouse: Applying InputClass "evdev pointer catchall"
[     3.245] (II) Using input driver 'evdev' for 'Saitek Cyborg R.A.T.5 Mouse'
[     3.245] (**) Saitek Cyborg R.A.T.5 Mouse: always reports core events
[     3.245] (**) evdev: Saitek Cyborg R.A.T.5 Mouse: Device: "/dev/input/event15"
[     3.245] (--) evdev: Saitek Cyborg R.A.T.5 Mouse: Vendor 0x6a3 Product 0xcc3
[     3.245] (--) evdev: Saitek Cyborg R.A.T.5 Mouse: Found 17 mouse buttons
[     3.245] (--) evdev: Saitek Cyborg R.A.T.5 Mouse: Found scroll wheel(s)
[     3.245] (--) evdev: Saitek Cyborg R.A.T.5 Mouse: Found relative axes
[     3.245] (--) evdev: Saitek Cyborg R.A.T.5 Mouse: Found x and y relative axes
[     3.245] (II) evdev: Saitek Cyborg R.A.T.5 Mouse: Configuring as mouse
[     3.245] (II) evdev: Saitek Cyborg R.A.T.5 Mouse: Adding scrollwheel support
[     3.245] (**) evdev: Saitek Cyborg R.A.T.5 Mouse: YAxisMapping: buttons 4 and 5
[     3.245] (**) evdev: Saitek Cyborg R.A.T.5 Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     3.245] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.0/0003:06A3:0CC3.0001/input/input18/event15"
[     3.245] (II) XINPUT: Adding extended input device "Saitek Cyborg R.A.T.5 Mouse" (type: MOUSE, id 8)
[     3.245] (II) evdev: Saitek Cyborg R.A.T.5 Mouse: initialized for relative axes.
[     3.245] (**) Saitek Cyborg R.A.T.5 Mouse: (accel) keeping acceleration scheme 1
[     3.245] (**) Saitek Cyborg R.A.T.5 Mouse: (accel) acceleration profile 0
[     3.246] (**) Saitek Cyborg R.A.T.5 Mouse: (accel) acceleration factor: 2.000
[     3.246] (**) Saitek Cyborg R.A.T.5 Mouse: (accel) acceleration threshold: 4
[     3.246] (II) config/udev: Adding input device Saitek Cyborg R.A.T.5 Mouse (/dev/input/mouse0)
[     3.246] (II) No input driver specified, ignoring this device.
[     3.246] (II) This device may have been added with another device file.
[     3.246] (II) config/udev: Adding input device HID 046a:010d (/dev/input/event16)
[     3.246] (**) HID 046a:010d: Applying InputClass "evdev keyboard catchall"
[     3.246] (**) HID 046a:010d: Applying InputClass "keyboard defaults"
[     3.246] (II) Using input driver 'evdev' for 'HID 046a:010d'
[     3.246] (**) HID 046a:010d: always reports core events
[     3.246] (**) evdev: HID 046a:010d: Device: "/dev/input/event16"
[     3.246] (--) evdev: HID 046a:010d: Vendor 0x46a Product 0x10d
[     3.246] (--) evdev: HID 046a:010d: Found keys
[     3.246] (II) evdev: HID 046a:010d: Configuring as keyboard
[     3.246] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/0003:046A:010D.0002/input/input19/event16"
[     3.246] (II) XINPUT: Adding extended input device "HID 046a:010d" (type: KEYBOARD, id 9)
[     3.246] (**) Option "xkb_rules" "evdev"
[     3.246] (**) Option "xkb_model" "pc105"
[     3.246] (**) Option "xkb_layout" "de"
[     3.246] (**) Option "xkb_options" "terminate:ctrl_alt_bksp"
[     3.246] (II) config/udev: Adding input device HID 046a:010d (/dev/input/event17)
[     3.246] (**) HID 046a:010d: Applying InputClass "evdev keyboard catchall"
[     3.246] (**) HID 046a:010d: Applying InputClass "keyboard defaults"
[     3.246] (II) Using input driver 'evdev' for 'HID 046a:010d'
[     3.246] (**) HID 046a:010d: always reports core events
[     3.246] (**) evdev: HID 046a:010d: Device: "/dev/input/event17"
[     3.246] (--) evdev: HID 046a:010d: Vendor 0x46a Product 0x10d
[     3.246] (--) evdev: HID 046a:010d: Found 1 mouse buttons
[     3.246] (--) evdev: HID 046a:010d: Found scroll wheel(s)
[     3.246] (--) evdev: HID 046a:010d: Found relative axes
[     3.246] (II) evdev: HID 046a:010d: Forcing relative x/y axes to exist.
[     3.246] (--) evdev: HID 046a:010d: Found absolute axes
[     3.246] (II) evdev: HID 046a:010d: Forcing absolute x/y axes to exist.
[     3.246] (--) evdev: HID 046a:010d: Found keys
[     3.246] (II) evdev: HID 046a:010d: Configuring as mouse
[     3.246] (II) evdev: HID 046a:010d: Configuring as keyboard
[     3.246] (II) evdev: HID 046a:010d: Adding scrollwheel support
[     3.246] (**) evdev: HID 046a:010d: YAxisMapping: buttons 4 and 5
[     3.246] (**) evdev: HID 046a:010d: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     3.246] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.1/0003:046A:010D.0003/input/input20/event17"
[     3.246] (II) XINPUT: Adding extended input device "HID 046a:010d" (type: KEYBOARD, id 10)
[     3.246] (**) Option "xkb_rules" "evdev"
[     3.246] (**) Option "xkb_model" "pc105"
[     3.246] (**) Option "xkb_layout" "de"
[     3.247] (**) Option "xkb_options" "terminate:ctrl_alt_bksp"
[     3.247] (II) evdev: HID 046a:010d: initialized for relative axes.
[     3.247] (WW) evdev: HID 046a:010d: ignoring absolute axes.
[     3.247] (**) HID 046a:010d: (accel) keeping acceleration scheme 1
[     3.247] (**) HID 046a:010d: (accel) acceleration profile 0
[     3.247] (**) HID 046a:010d: (accel) acceleration factor: 2.000
[     3.247] (**) HID 046a:010d: (accel) acceleration threshold: 4
[     3.247] (II) config/udev: Adding input device HDA Intel PCH Front Mic (/dev/input/event8)
[     3.247] (II) No input driver specified, ignoring this device.
[     3.247] (II) This device may have been added with another device file.
[     3.247] (II) config/udev: Adding input device HDA Intel PCH Rear Mic (/dev/input/event9)
[     3.247] (II) No input driver specified, ignoring this device.
[     3.247] (II) This device may have been added with another device file.
[     3.247] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event10)
[     3.247] (II) No input driver specified, ignoring this device.
[     3.247] (II) This device may have been added with another device file.
[     3.247] (II) config/udev: Adding input device HDA Intel PCH Line Out Front (/dev/input/event11)
[     3.247] (II) No input driver specified, ignoring this device.
[     3.247] (II) This device may have been added with another device file.
[     3.248] (II) config/udev: Adding input device HDA Intel PCH Line Out Surround (/dev/input/event12)
[     3.248] (II) No input driver specified, ignoring this device.
[     3.248] (II) This device may have been added with another device file.
[     3.248] (II) config/udev: Adding input device HDA Intel PCH Line Out CLFE (/dev/input/event13)
[     3.248] (II) No input driver specified, ignoring this device.
[     3.248] (II) This device may have been added with another device file.
[     3.248] (II) config/udev: Adding input device HDA Intel PCH Front Headphone (/dev/input/event14)
[     3.248] (II) No input driver specified, ignoring this device.
[     3.248] (II) This device may have been added with another device file.
[     3.251] (II) fglrx(0): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
[    16.717] (II) fglrx(0): EDID vendor "ACI", prod id 6642
[    16.717] (II) fglrx(0): Using EDID range info for horizontal sync
[    16.717] (II) fglrx(0): Using EDID range info for vertical refresh
[    16.717] (II) fglrx(0): Printing DDC gathered Modelines:
[    16.717] (II) fglrx(0): Modeline "1366x768"x0.0   85.50  1366 1436 1579 1792  768 771 774 798 +hsync +vsync (47.7 kHz eP)
[    16.717] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    16.717] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    16.717] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    16.717] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    16.717] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    16.717] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    16.717] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    16.717] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    16.717] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    16.717] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    16.717] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    16.717] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    16.717] (II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[    16.723] (II) fglrx(0): EDID vendor "ACI", prod id 6642
[    16.723] (II) fglrx(0): Using hsync ranges from config file
[    16.723] (II) fglrx(0): Using vrefresh ranges from config file
[    16.723] (II) fglrx(0): Printing DDC gathered Modelines:
[    16.723] (II) fglrx(0): Modeline "1366x768"x0.0   85.50  1366 1436 1579 1792  768 771 774 798 +hsync +vsync (47.7 kHz eP)
[    16.723] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    16.723] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    16.723] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    16.723] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    16.723] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    16.723] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    16.723] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    16.723] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    16.723] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    16.723] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    16.723] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    16.723] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    16.723] (II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[    16.730] (II) fglrx(0): EDID vendor "ACI", prod id 6642
[    16.730] (II) fglrx(0): Using hsync ranges from config file
[    16.730] (II) fglrx(0): Using vrefresh ranges from config file
[    16.730] (II) fglrx(0): Printing DDC gathered Modelines:
[    16.730] (II) fglrx(0): Modeline "1366x768"x0.0   85.50  1366 1436 1579 1792  768 771 774 798 +hsync +vsync (47.7 kHz eP)
[    16.730] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    16.730] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    16.730] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    16.730] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    16.730] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    16.730] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    16.730] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    16.730] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    16.730] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    16.730] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    16.730] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    16.730] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    16.730] (II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[    16.788] (II) fglrx(0): EDID vendor "ACI", prod id 6642
[    16.788] (II) fglrx(0): Using hsync ranges from config file
[    16.788] (II) fglrx(0): Using vrefresh ranges from config file
[    16.788] (II) fglrx(0): Printing DDC gathered Modelines:
[    16.788] (II) fglrx(0): Modeline "1366x768"x0.0   85.50  1366 1436 1579 1792  768 771 774 798 +hsync +vsync (47.7 kHz eP)
[    16.788] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    16.788] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    16.788] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    16.788] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    16.788] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    16.788] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    16.788] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    16.788] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    16.788] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    16.788] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    16.788] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    16.788] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    16.788] (II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[    17.006] (II) fglrx(0): xdl_xs115_atiddxDisplayScreenEnableDisplays
[    17.455] (II) fglrx(0): EDID vendor "ACI", prod id 9368
[    17.455] (II) fglrx(0): Using hsync ranges from config file
[    17.455] (II) fglrx(0): Using vrefresh ranges from config file
[    17.455] (II) fglrx(0): Printing DDC gathered Modelines:
[    17.455] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    17.455] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    17.455] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    17.455] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    17.455] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    17.455] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    17.455] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    17.455] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    17.455] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    17.455] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    17.455] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    17.455] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    17.455] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    17.456] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    17.456] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    17.456] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    17.456] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    17.456] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    17.456] (II) fglrx(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[    17.456] (II) fglrx(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz e)
[    17.456] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[    17.456] (II) fglrx(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[   338.444] (II) config/udev: removing device Saitek Cyborg R.A.T.5 Mouse
[   338.460] (II) evdev: Saitek Cyborg R.A.T.5 Mouse: Close
[   338.460] (II) UnloadModule: "evdev"
[   340.527] (II) config/udev: Adding input device Saitek Cyborg R.A.T.5 Mouse (/dev/input/event15)
[   340.527] (**) Saitek Cyborg R.A.T.5 Mouse: Applying InputClass "evdev pointer catchall"
[   340.527] (II) Using input driver 'evdev' for 'Saitek Cyborg R.A.T.5 Mouse'
[   340.527] (**) Saitek Cyborg R.A.T.5 Mouse: always reports core events
[   340.527] (**) evdev: Saitek Cyborg R.A.T.5 Mouse: Device: "/dev/input/event15"
[   340.527] (--) evdev: Saitek Cyborg R.A.T.5 Mouse: Vendor 0x6a3 Product 0xcc3
[   340.527] (--) evdev: Saitek Cyborg R.A.T.5 Mouse: Found 17 mouse buttons
[   340.527] (--) evdev: Saitek Cyborg R.A.T.5 Mouse: Found scroll wheel(s)
[   340.527] (--) evdev: Saitek Cyborg R.A.T.5 Mouse: Found relative axes
[   340.527] (--) evdev: Saitek Cyborg R.A.T.5 Mouse: Found x and y relative axes
[   340.528] (II) evdev: Saitek Cyborg R.A.T.5 Mouse: Configuring as mouse
[   340.528] (II) evdev: Saitek Cyborg R.A.T.5 Mouse: Adding scrollwheel support
[   340.528] (**) evdev: Saitek Cyborg R.A.T.5 Mouse: YAxisMapping: buttons 4 and 5
[   340.528] (**) evdev: Saitek Cyborg R.A.T.5 Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   340.528] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.0/0003:06A3:0CC3.0004/input/input21/event15"
[   340.528] (II) XINPUT: Adding extended input device "Saitek Cyborg R.A.T.5 Mouse" (type: MOUSE, id 8)
[   340.528] (II) evdev: Saitek Cyborg R.A.T.5 Mouse: initialized for relative axes.
[   340.528] (**) Saitek Cyborg R.A.T.5 Mouse: (accel) keeping acceleration scheme 1
[   340.528] (**) Saitek Cyborg R.A.T.5 Mouse: (accel) acceleration profile 0
[   340.528] (**) Saitek Cyborg R.A.T.5 Mouse: (accel) acceleration factor: 2.000
[   340.528] (**) Saitek Cyborg R.A.T.5 Mouse: (accel) acceleration threshold: 4
[   340.528] (II) config/udev: Adding input device Saitek Cyborg R.A.T.5 Mouse (/dev/input/mouse0)
[   340.528] (II) No input driver specified, ignoring this device.
[   340.528] (II) This device may have been added with another device file.


```

dmesg:
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.16.0-38-generic (buildd@allspice) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #52~14.04.1-Ubuntu SMP Fri May 8 09:43:57 UTC 2015 (Ubuntu 3.16.0-38.52~14.04.1-generic 3.16.7-ckt10)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.16.0-38-generic root=UUID=2472998e-a367-4b03-88b2-2f11545bede8 ro nomodeset quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009d7ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009d800-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000de5a0fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000de5a1000-0x00000000deb18fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000deb19000-0x00000000ded98fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000ded99000-0x00000000ded9dfff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000ded9e000-0x00000000dede0fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000dede1000-0x00000000df547fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000df548000-0x00000000df7f1fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000df7f2000-0x00000000df7fffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed03fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000041dffffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.7 present.
[    0.000000] DMI: To Be Filled By O.E.M. To Be Filled By O.E.M./B75 Pro3-M, BIOS P1.30 04/18/2012
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] AGP: No AGP bridge found
[    0.000000] e820: last_pfn = 0x41e000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-E7FFF uncachable
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask C00000000 write-back
[    0.000000]   1 base 400000000 mask FF0000000 write-back
[    0.000000]   2 base 410000000 mask FF8000000 write-back
[    0.000000]   3 base 418000000 mask FFC000000 write-back
[    0.000000]   4 base 41C000000 mask FFE000000 write-back
[    0.000000]   5 base 0E0000000 mask FE0000000 uncachable
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 16GB, type WB
[    0.000000] reg 1, base: 16GB, range: 256MB, type WB
[    0.000000] reg 2, base: 16640MB, range: 128MB, type WB
[    0.000000] reg 3, base: 16768MB, range: 64MB, type WB
[    0.000000] reg 4, base: 16832MB, range: 32MB, type WB
[    0.000000] reg 5, base: 3584MB, range: 512MB, type UC
[    0.000000] total RAM covered: 16352M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 64M     num_reg: 7      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 512MB, type WB
[    0.000000] reg 3, base: 4GB, range: 4GB, type WB
[    0.000000] reg 4, base: 8GB, range: 8GB, type WB
[    0.000000] reg 5, base: 16GB, range: 512MB, type WB
[    0.000000] reg 6, base: 16864MB, range: 32MB, type UC
[    0.000000] e820: update [mem 0xe0000000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xdf800 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000fccd0-0x000fccdf] mapped at [ffff8800000fccd0]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000097000] 97000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01fbd000, 0x01fbdfff] PGTABLE
[    0.000000] BRK [0x01fbe000, 0x01fbefff] PGTABLE
[    0.000000] BRK [0x01fbf000, 0x01fbffff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x41de00000-0x41dffffff]
[    0.000000]  [mem 0x41de00000-0x41dffffff] page 2M
[    0.000000] BRK [0x01fc0000, 0x01fc0fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x41c000000-0x41ddfffff]
[    0.000000]  [mem 0x41c000000-0x41ddfffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x400000000-0x41bffffff]
[    0.000000]  [mem 0x400000000-0x41bffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0xde5a0fff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0xde3fffff] page 2M
[    0.000000]  [mem 0xde400000-0xde5a0fff] page 4k
[    0.000000] init_memory_mapping: [mem 0xdede1000-0xdf547fff]
[    0.000000]  [mem 0xdede1000-0xdedfffff] page 4k
[    0.000000]  [mem 0xdee00000-0xdf3fffff] page 2M
[    0.000000]  [mem 0xdf400000-0xdf547fff] page 4k
[    0.000000] BRK [0x01fc1000, 0x01fc1fff] PGTABLE
[    0.000000] BRK [0x01fc2000, 0x01fc2fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0xdf7f2000-0xdf7fffff]
[    0.000000]  [mem 0xdf7f2000-0xdf7fffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x100000000-0x3ffffffff]
[    0.000000]  [mem 0x100000000-0x3ffffffff] page 2M
[    0.000000] RAMDISK: [mem 0x35ada000-0x36d64fff]
[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x00000000000F0450 000024 (v02 ALASKA)
[    0.000000] ACPI: XSDT 0x00000000DED80078 000074 (v01 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: FACP 0x00000000DED89908 0000F4 (v04 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: DSDT 0x00000000DED80188 00977E (v02 ALASKA A M I    00000014 INTL 20051117)
[    0.000000] ACPI: FACS 0x00000000DED97F80 000040
[    0.000000] ACPI: APIC 0x00000000DED89A00 000072 (v03 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: MCFG 0x00000000DED89A78 00003C (v01 ALASKA A M I    01072009 MSFT 00000097)
[    0.000000] ACPI: SSDT 0x00000000DED89AB8 0004A6 (v01 Intel_ AoacTabl 00001000 INTL 20091112)
[    0.000000] ACPI: AAFT 0x00000000DED89F60 0000C2 (v01 ALASKA OEMAAFT  01072009 MSFT 00000097)
[    0.000000] ACPI: HPET 0x00000000DED8A028 000038 (v01 ALASKA A M I    01072009 AMI. 00000005)
[    0.000000] ACPI: SSDT 0x00000000DED8A060 00036D (v01 SataRe SataTabl 00001000 INTL 20091112)
[    0.000000] ACPI: SSDT 0x00000000DED8A3D0 0009AA (v01 PmRef  Cpu0Ist  00003000 INTL 20051117)
[    0.000000] ACPI: SSDT 0x00000000DED8AD80 000A92 (v01 PmRef  CpuPm    00003000 INTL 20051117)
[    0.000000] ACPI: ASF! 0x00000000DED8B818 0000A5 (v32 INTEL   HCG     00000001 TFSM 000F4240)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000041dffffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x41dffffff]
[    0.000000]   NODE_DATA [mem 0x41dfea000-0x41dfeefff]
[    0.000000]  [ffffea0000000000-ffffea00107fffff] PMD -> [ffff88040d600000-ffff88041d5fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x41dffffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009cfff]
[    0.000000]   node   0: [mem 0x00100000-0xde5a0fff]
[    0.000000]   node   0: [mem 0xdede1000-0xdf547fff]
[    0.000000]   node   0: [mem 0xdf7f2000-0xdf7fffff]
[    0.000000]   node   0: [mem 0x100000000-0x41dffffff]
[    0.000000] On node 0 totalpages: 4181170
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3996 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14197 pages used for memmap
[    0.000000]   DMA32 zone: 908566 pages, LIFO batch:31
[    0.000000]   Normal zone: 51072 pages used for memmap
[    0.000000]   Normal zone: 3268608 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] smpboot: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: [mem 0x0009d000-0x0009dfff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xde5a1000-0xdeb18fff]
[    0.000000] PM: Registered nosave memory: [mem 0xdeb19000-0xded98fff]
[    0.000000] PM: Registered nosave memory: [mem 0xded99000-0xded9dfff]
[    0.000000] PM: Registered nosave memory: [mem 0xded9e000-0xdede0fff]
[    0.000000] PM: Registered nosave memory: [mem 0xdf548000-0xdf7f1fff]
[    0.000000] PM: Registered nosave memory: [mem 0xdf800000-0xf7ffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf8000000-0xfbffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfc000000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfecfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed00000-0xfed03fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed04000-0xfed1bfff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xfeffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xff000000-0xffffffff]
[    0.000000] e820: [mem 0xdf800000-0xf7ffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 27 pages/cpu @ffff88041dc00000 s81408 r8192 d20992 u524288
[    0.000000] pcpu-alloc: s81408 r8192 d20992 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 4115816
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.16.0-38-generic root=UUID=2472998e-a367-4b03-88b2-2f11545bede8 ro nomodeset quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] AGP: Checking aperture...
[    0.000000] AGP: No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 16360496K/16724680K available (7626K kernel code, 1131K rwdata, 3596K rodata, 1352K init, 1300K bss, 364184K reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
[    0.000000]     Offload RCU callbacks from all CPUs
[    0.000000]     Offload RCU callbacks from CPUs: 0-3.
[    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=16, nr_cpu_ids=4
[    0.000000] NR_IRQS:16640 nr_irqs:712 16
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 67108864 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 3092.968 MHz processor
[    0.000029] Calibrating delay loop (skipped), value calculated using timer frequency.. 6185.93 BogoMIPS (lpj=12371872)
[    0.000031] pid_max: default: 32768 minimum: 301
[    0.000037] ACPI: Core revision 20140424
[    0.005486] ACPI: All ACPI Tables successfully acquired
[    0.009917] Security Framework initialized
[    0.009931] AppArmor: AppArmor initialized
[    0.009932] Yama: becoming mindful.
[    0.010737] Dentry cache hash table entries: 2097152 (order: 12, 16777216 bytes)
[    0.014045] Inode-cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.015513] Mount-cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.015529] Mountpoint-cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.015746] Initializing cgroup subsys memory
[    0.015764] Initializing cgroup subsys devices
[    0.015769] Initializing cgroup subsys freezer
[    0.015771] Initializing cgroup subsys net_cls
[    0.015774] Initializing cgroup subsys blkio
[    0.015777] Initializing cgroup subsys perf_event
[    0.015778] Initializing cgroup subsys net_prio
[    0.015783] Initializing cgroup subsys hugetlb
[    0.015801] CPU: Physical Processor ID: 0
[    0.015802] CPU: Processor Core ID: 0
[    0.015806] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.015806] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.016105] mce: CPU supports 9 MCE banks
[    0.016116] CPU0: Thermal monitoring enabled (TM1)
[    0.016123] Last level iTLB entries: 4KB 512, 2MB 8, 4MB 8
[    0.016123] Last level dTLB entries: 4KB 512, 2MB 32, 4MB 32, 1GB 0
[    0.016123] tlb_flushall_shift: 2
[    0.016237] Freeing SMP alternatives memory: 32K (ffffffff81e6e000 - ffffffff81e76000)
[    0.017202] ftrace: allocating 29244 entries in 115 pages
[    0.029044] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.068718] smpboot: CPU0: Intel(R) Core(TM) i5-3450 CPU @ 3.10GHz (fam: 06, model: 3a, stepping: 09)
[    0.068725] TSC deadline timer enabled
[    0.068744] Performance Events: PEBS fmt1+, 16-deep LBR, IvyBridge events, full-width counters, Intel PMU driver.
[    0.068760] ... version:                3
[    0.068761] ... bit width:              48
[    0.068761] ... generic registers:      8
[    0.068762] ... value mask:             0000ffffffffffff
[    0.068763] ... max period:             0000ffffffffffff
[    0.068764] ... fixed-purpose events:   3
[    0.068764] ... event mask:             00000007000000ff
[    0.070113] x86: Booting SMP configuration:
[    0.070115] .... node  #0, CPUs:      #1
[    0.083586] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.083657]  #2 #3
[    0.110611] x86: Booted up 1 node, 4 CPUs
[    0.110614] smpboot: Total of 4 processors activated (24743.74 BogoMIPS)
[    0.113456] devtmpfs: initialized
[    0.116253] evm: security.selinux
[    0.116254] evm: security.SMACK64
[    0.116255] evm: security.SMACK64EXEC
[    0.116255] evm: security.SMACK64TRANSMUTE
[    0.116256] evm: security.SMACK64MMAP
[    0.116257] evm: security.ima
[    0.116257] evm: security.capability
[    0.116300] PM: Registering ACPI NVS region [mem 0xdeb19000-0xded98fff] (2621440 bytes)
[    0.116327] PM: Registering ACPI NVS region [mem 0xded9e000-0xdede0fff] (274432 bytes)
[    0.116997] pinctrl core: initialized pinctrl subsystem
[    0.117055] regulator-dummy: no parameters
[    0.136924] RTC time: 15:24:56, date: 05/30/15
[    0.136966] NET: Registered protocol family 16
[    0.137089] cpuidle: using governor ladder
[    0.137091] cpuidle: using governor menu
[    0.137135] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.137136] ACPI: bus type PCI registered
[    0.137138] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.137194] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.137196] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.137260] PCI: Using configuration type 1 for base access
[    0.138943] ACPI: Added _OSI(Module Device)
[    0.138945] ACPI: Added _OSI(Processor Device)
[    0.138946] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.138947] ACPI: Added _OSI(Processor Aggregator Device)
[    0.140997] ACPI: Executed 1 blocks of module-level executable AML code
[    0.142896] ACPI: Dynamic OEM Table Load:
[    0.142902] ACPI: SSDT 0xFFFF88040718A000 00083B (v01 PmRef  Cpu0Cst  00003001 INTL 20051117)
[    0.146789] ACPI: Dynamic OEM Table Load:
[    0.146792] ACPI: SSDT 0xFFFF8804071A5000 000303 (v01 PmRef  ApIst    00003000 INTL 20051117)
[    0.150699] ACPI: Dynamic OEM Table Load:
[    0.150702] ACPI: SSDT 0xFFFF88040714F000 000119 (v01 PmRef  ApCst    00003000 INTL 20051117)
[    0.155062] ACPI: Interpreter enabled
[    0.155070] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20140424/hwxface-580)
[    0.155081] ACPI: (supports S0 S1 S3 S4 S5)
[    0.155082] ACPI: Using IOAPIC for interrupt routing
[    0.155122] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.160118] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    0.160122] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.160273] acpi PNP0A08:00: _OSC: platform does not support [PCIeHotplug]
[    0.160359] acpi PNP0A08:00: _OSC: OS now controls [PME AER PCIeCapability]
[    0.160360] acpi PNP0A08:00: FADT indicates ASPM is unsupported, using BIOS configuration
[    0.160807] PCI host bridge to bus 0000:00
[    0.160810] pci_bus 0000:00: root bus resource [bus 00-3e]
[    0.160811] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.160812] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.160814] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.160815] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff]
[    0.160816] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
[    0.160817] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
[    0.160818] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff]
[    0.160820] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000e3fff]
[    0.160821] pci_bus 0000:00: root bus resource [mem 0x000e4000-0x000e7fff]
[    0.160822] pci_bus 0000:00: root bus resource [mem 0xe0000000-0xfeafffff]
[    0.160828] pci 0000:00:00.0: [8086:0150] type 00 class 0x060000
[    0.160897] pci 0000:00:01.0: [8086:0151] type 01 class 0x060400
[    0.160924] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.160957] pci 0000:00:01.0: System wakeup disabled by ACPI
[    0.161010] pci 0000:00:14.0: [8086:1e31] type 00 class 0x0c0330
[    0.161032] pci 0000:00:14.0: reg 0x10: [mem 0xf7f00000-0xf7f0ffff 64bit]
[    0.161102] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    0.161136] pci 0000:00:14.0: System wakeup disabled by ACPI
[    0.161168] pci 0000:00:16.0: [8086:1e3a] type 00 class 0x078000
[    0.161190] pci 0000:00:16.0: reg 0x10: [mem 0xf7f1b000-0xf7f1b00f 64bit]
[    0.161262] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.161335] pci 0000:00:1a.0: [8086:1e2d] type 00 class 0x0c0320
[    0.161355] pci 0000:00:1a.0: reg 0x10: [mem 0xf7f18000-0xf7f183ff]
[    0.161443] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.161488] pci 0000:00:1a.0: System wakeup disabled by ACPI
[    0.161523] pci 0000:00:1b.0: [8086:1e20] type 00 class 0x040300
[    0.161539] pci 0000:00:1b.0: reg 0x10: [mem 0xf7f10000-0xf7f13fff 64bit]
[    0.161612] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.161647] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    0.161682] pci 0000:00:1c.0: [8086:1e10] type 01 class 0x060400
[    0.161816] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.161863] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.161895] pci 0000:00:1c.4: [8086:1e18] type 01 class 0x060400
[    0.161974] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.162012] pci 0000:00:1c.4: System wakeup disabled by ACPI
[    0.162042] pci 0000:00:1c.5: [8086:1e1a] type 01 class 0x060400
[    0.162122] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.162160] pci 0000:00:1c.5: System wakeup disabled by ACPI
[    0.162195] pci 0000:00:1d.0: [8086:1e26] type 00 class 0x0c0320
[    0.162215] pci 0000:00:1d.0: reg 0x10: [mem 0xf7f17000-0xf7f173ff]
[    0.162303] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.162348] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.162377] pci 0000:00:1e.0: [8086:244e] type 01 class 0x060401
[    0.162451] pci 0000:00:1e.0: System wakeup disabled by ACPI
[    0.162482] pci 0000:00:1f.0: [8086:1e49] type 00 class 0x060100
[    0.162644] pci 0000:00:1f.2: [8086:1e02] type 00 class 0x010601
[    0.162662] pci 0000:00:1f.2: reg 0x10: [io  0xf070-0xf077]
[    0.162670] pci 0000:00:1f.2: reg 0x14: [io  0xf060-0xf063]
[    0.162678] pci 0000:00:1f.2: reg 0x18: [io  0xf050-0xf057]
[    0.162685] pci 0000:00:1f.2: reg 0x1c: [io  0xf040-0xf043]
[    0.162693] pci 0000:00:1f.2: reg 0x20: [io  0xf020-0xf03f]
[    0.162701] pci 0000:00:1f.2: reg 0x24: [mem 0xf7f16000-0xf7f167ff]
[    0.162743] pci 0000:00:1f.2: PME# supported from D3hot
[    0.162802] pci 0000:00:1f.3: [8086:1e22] type 00 class 0x0c0500
[    0.162816] pci 0000:00:1f.3: reg 0x10: [mem 0xf7f15000-0xf7f150ff 64bit]
[    0.162837] pci 0000:00:1f.3: reg 0x20: [io  0xf000-0xf01f]
[    0.162935] pci 0000:01:00.0: [1002:679e] type 00 class 0x030000
[    0.162943] pci 0000:01:00.0: reg 0x10: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.162949] pci 0000:01:00.0: reg 0x18: [mem 0xf7e00000-0xf7e3ffff 64bit]
[    0.162953] pci 0000:01:00.0: reg 0x20: [io  0xe000-0xe0ff]
[    0.162960] pci 0000:01:00.0: reg 0x30: [mem 0xf7e40000-0xf7e5ffff pref]
[    0.162985] pci 0000:01:00.0: supports D1 D2
[    0.162987] pci 0000:01:00.0: PME# supported from D1 D2 D3hot
[    0.163021] pci 0000:01:00.1: [1002:aaa0] type 00 class 0x040300
[    0.163029] pci 0000:01:00.1: reg 0x10: [mem 0xf7e60000-0xf7e63fff 64bit]
[    0.163065] pci 0000:01:00.1: supports D1 D2
[    0.170626] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.170630] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.170633] pci 0000:00:01.0:   bridge window [mem 0xf7e00000-0xf7efffff]
[    0.170638] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xefffffff 64bit pref]
[    0.170727] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.170811] pci 0000:03:00.0: [1b21:0612] type 00 class 0x010601
[    0.170832] pci 0000:03:00.0: reg 0x10: [io  0xd050-0xd057]
[    0.170846] pci 0000:03:00.0: reg 0x14: [io  0xd040-0xd043]
[    0.170859] pci 0000:03:00.0: reg 0x18: [io  0xd030-0xd037]
[    0.170872] pci 0000:03:00.0: reg 0x1c: [io  0xd020-0xd023]
[    0.170885] pci 0000:03:00.0: reg 0x20: [io  0xd000-0xd01f]
[    0.170898] pci 0000:03:00.0: reg 0x24: [mem 0xf7d00000-0xf7d001ff]
[    0.178633] pci 0000:00:1c.4: PCI bridge to [bus 03]
[    0.178639] pci 0000:00:1c.4:   bridge window [io  0xd000-0xdfff]
[    0.178644] pci 0000:00:1c.4:   bridge window [mem 0xf7d00000-0xf7dfffff]
[    0.178739] pci 0000:04:00.0: [10ec:8168] type 00 class 0x020000
[    0.178761] pci 0000:04:00.0: reg 0x10: [io  0xc000-0xc0ff]
[    0.178795] pci 0000:04:00.0: reg 0x18: [mem 0xf0004000-0xf0004fff 64bit pref]
[    0.178816] pci 0000:04:00.0: reg 0x20: [mem 0xf0000000-0xf0003fff 64bit pref]
[    0.178925] pci 0000:04:00.0: supports D1 D2
[    0.178926] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.186637] pci 0000:00:1c.5: PCI bridge to [bus 04]
[    0.186643] pci 0000:00:1c.5:   bridge window [io  0xc000-0xcfff]
[    0.186653] pci 0000:00:1c.5:   bridge window [mem 0xf0000000-0xf00fffff 64bit pref]
[    0.186733] pci 0000:00:1e.0: PCI bridge to [bus 05] (subtractive decode)
[    0.186742] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.186743] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.186745] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.186746] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
[    0.186747] pci 0000:00:1e.0:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.186748] pci 0000:00:1e.0:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.186749] pci 0000:00:1e.0:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
[    0.186751] pci 0000:00:1e.0:   bridge window [mem 0x000e0000-0x000e3fff] (subtractive decode)
[    0.186752] pci 0000:00:1e.0:   bridge window [mem 0x000e4000-0x000e7fff] (subtractive decode)
[    0.186753] pci 0000:00:1e.0:   bridge window [mem 0xe0000000-0xfeafffff] (subtractive decode)
[    0.187247] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.187285] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 *10 11 12 14 15)
[    0.187321] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 10 11 12 14 15)
[    0.187356] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 6 10 11 12 14 15)
[    0.187391] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.187426] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.187462] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.187498] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *10 11 12 14 15)
[    0.187584] ACPI: Enabled 4 GPEs in block 00 to 3F
[    0.187652] vgaarb: setting as boot device: PCI:0000:01:00.0
[    0.187653] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.187654] vgaarb: loaded
[    0.187655] vgaarb: bridge control possible 0000:01:00.0
[    0.187836] SCSI subsystem initialized
[    0.187865] libata version 3.00 loaded.
[    0.187884] ACPI: bus type USB registered
[    0.187898] usbcore: registered new interface driver usbfs
[    0.187904] usbcore: registered new interface driver hub
[    0.187919] usbcore: registered new device driver usb
[    0.188007] PCI: Using ACPI for IRQ routing
[    0.189462] PCI: pci_cache_line_size set to 64 bytes
[    0.189509] e820: reserve RAM buffer [mem 0x0009d800-0x0009ffff]
[    0.189511] e820: reserve RAM buffer [mem 0xde5a1000-0xdfffffff]
[    0.189512] e820: reserve RAM buffer [mem 0xdf548000-0xdfffffff]
[    0.189513] e820: reserve RAM buffer [mem 0xdf800000-0xdfffffff]
[    0.189514] e820: reserve RAM buffer [mem 0x41e000000-0x41fffffff]
[    0.189595] NetLabel: Initializing
[    0.189596] NetLabel:  domain hash size = 128
[    0.189597] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.189607] NetLabel:  unlabeled traffic allowed by default
[    0.189657] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.189661] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.191695] Switched to clocksource hpet
[    0.195879] AppArmor: AppArmor Filesystem Enabled
[    0.195906] pnp: PnP ACPI init
[    0.195916] ACPI: bus type PNP registered
[    0.195984] system 00:00: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.195987] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.196046] system 00:01: [io  0x0680-0x069f] has been reserved
[    0.196048] system 00:01: [io  0x0200-0x020f] has been reserved
[    0.196049] system 00:01: [io  0xffff] has been reserved
[    0.196050] system 00:01: [io  0xffff] has been reserved
[    0.196052] system 00:01: [io  0x0400-0x0453] could not be reserved
[    0.196053] system 00:01: [io  0x0458-0x047f] has been reserved
[    0.196054] system 00:01: [io  0x0500-0x057f] has been reserved
[    0.196056] system 00:01: [io  0x164e-0x164f] has been reserved
[    0.196057] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.196080] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.196116] system 00:03: [io  0x0454-0x0457] has been reserved
[    0.196118] system 00:03: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.196173] system 00:04: [io  0x0290-0x029f] has been reserved
[    0.196175] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.196385] pnp 00:05: [dma 3]
[    0.196459] pnp 00:05: Plug and Play ACPI device, IDs PNP0401 (active)
[    0.196598] system 00:06: [io  0x04d0-0x04d1] has been reserved
[    0.196600] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.196710] pnp 00:07: [dma 0 disabled]
[    0.196745] pnp 00:07: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.196905] system 00:08: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.196907] system 00:08: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.196908] system 00:08: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.196910] system 00:08: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.196911] system 00:08: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.196913] system 00:08: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.196914] system 00:08: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.196915] system 00:08: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.196917] system 00:08: [mem 0xff000000-0xffffffff] has been reserved
[    0.196918] system 00:08: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.196920] system 00:08: [mem 0xf0100000-0xf0100fff] has been reserved
[    0.196921] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.197014] pnp: PnP ACPI: found 9 devices
[    0.197015] ACPI: bus type PNP unregistered
[    0.203149] pci 0000:00:1c.0: bridge window [io  0x1000-0x0fff] to [bus 02] add_size 1000
[    0.203152] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 02] add_size 200000
[    0.203153] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff] to [bus 02] add_size 200000
[    0.203178] pci 0000:00:1c.0: res[14]=[mem 0x00100000-0x000fffff] get_res_add_size add_size 200000
[    0.203179] pci 0000:00:1c.0: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.203181] pci 0000:00:1c.0: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.203185] pci 0000:00:1c.0: BAR 14: assigned [mem 0xf0200000-0xf03fffff]
[    0.203190] pci 0000:00:1c.0: BAR 15: assigned [mem 0xf0400000-0xf05fffff 64bit pref]
[    0.203192] pci 0000:00:1c.0: BAR 13: assigned [io  0x2000-0x2fff]
[    0.203194] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.203196] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.203198] pci 0000:00:01.0:   bridge window [mem 0xf7e00000-0xf7efffff]
[    0.203200] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xefffffff 64bit pref]
[    0.203202] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.203205] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.203211] pci 0000:00:1c.0:   bridge window [mem 0xf0200000-0xf03fffff]
[    0.203216] pci 0000:00:1c.0:   bridge window [mem 0xf0400000-0xf05fffff 64bit pref]
[    0.203224] pci 0000:00:1c.4: PCI bridge to [bus 03]
[    0.203227] pci 0000:00:1c.4:   bridge window [io  0xd000-0xdfff]
[    0.203231] pci 0000:00:1c.4:   bridge window [mem 0xf7d00000-0xf7dfffff]
[    0.203239] pci 0000:00:1c.5: PCI bridge to [bus 04]
[    0.203242] pci 0000:00:1c.5:   bridge window [io  0xc000-0xcfff]
[    0.203249] pci 0000:00:1c.5:   bridge window [mem 0xf0000000-0xf00fffff 64bit pref]
[    0.203254] pci 0000:00:1e.0: PCI bridge to [bus 05]
[    0.203265] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.203266] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.203268] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.203269] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.203270] pci_bus 0000:00: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.203271] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.203272] pci_bus 0000:00: resource 10 [mem 0x000dc000-0x000dffff]
[    0.203274] pci_bus 0000:00: resource 11 [mem 0x000e0000-0x000e3fff]
[    0.203275] pci_bus 0000:00: resource 12 [mem 0x000e4000-0x000e7fff]
[    0.203276] pci_bus 0000:00: resource 13 [mem 0xe0000000-0xfeafffff]
[    0.203277] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.203278] pci_bus 0000:01: resource 1 [mem 0xf7e00000-0xf7efffff]
[    0.203280] pci_bus 0000:01: resource 2 [mem 0xe0000000-0xefffffff 64bit pref]
[    0.203281] pci_bus 0000:02: resource 0 [io  0x2000-0x2fff]
[    0.203282] pci_bus 0000:02: resource 1 [mem 0xf0200000-0xf03fffff]
[    0.203284] pci_bus 0000:02: resource 2 [mem 0xf0400000-0xf05fffff 64bit pref]
[    0.203285] pci_bus 0000:03: resource 0 [io  0xd000-0xdfff]
[    0.203286] pci_bus 0000:03: resource 1 [mem 0xf7d00000-0xf7dfffff]
[    0.203288] pci_bus 0000:04: resource 0 [io  0xc000-0xcfff]
[    0.203289] pci_bus 0000:04: resource 2 [mem 0xf0000000-0xf00fffff 64bit pref]
[    0.203290] pci_bus 0000:05: resource 4 [io  0x0000-0x0cf7]
[    0.203291] pci_bus 0000:05: resource 5 [io  0x0d00-0xffff]
[    0.203293] pci_bus 0000:05: resource 6 [mem 0x000a0000-0x000bffff]
[    0.203294] pci_bus 0000:05: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.203295] pci_bus 0000:05: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.203296] pci_bus 0000:05: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.203298] pci_bus 0000:05: resource 10 [mem 0x000dc000-0x000dffff]
[    0.203299] pci_bus 0000:05: resource 11 [mem 0x000e0000-0x000e3fff]
[    0.203300] pci_bus 0000:05: resource 12 [mem 0x000e4000-0x000e7fff]
[    0.203301] pci_bus 0000:05: resource 13 [mem 0xe0000000-0xfeafffff]
[    0.203322] NET: Registered protocol family 2
[    0.203489] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.203675] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.203799] TCP: Hash tables configured (established 131072 bind 65536)
[    0.203811] TCP: reno registered
[    0.203826] UDP hash table entries: 8192 (order: 6, 262144 bytes)
[    0.203871] UDP-Lite hash table entries: 8192 (order: 6, 262144 bytes)
[    0.203928] NET: Registered protocol family 1
[    0.243789] pci 0000:01:00.0: Video device with shadowed ROM
[    0.243797] PCI: CLS 64 bytes, default 64
[    0.243841] Trying to unpack rootfs image as initramfs...
[    0.477205] Freeing initrd memory: 18988K (ffff880035ada000 - ffff880036d65000)
[    0.477247] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.477249] software IO TLB [mem 0xda5a1000-0xde5a1000] (64MB) mapped at [ffff8800da5a1000-ffff8800de5a0fff]
[    0.477417] RAPL PMU detected, hw unit 2^-16 Joules, API unit is 2^-32 Joules, 3 fixed counters 163840 ms ovfl timer
[    0.477455] microcode: CPU0 sig=0x306a9, pf=0x2, revision=0x12
[    0.477462] microcode: CPU1 sig=0x306a9, pf=0x2, revision=0x12
[    0.477468] microcode: CPU2 sig=0x306a9, pf=0x2, revision=0x12
[    0.477474] microcode: CPU3 sig=0x306a9, pf=0x2, revision=0x12
[    0.477517] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.477537] Scanning for low memory corruption every 60 seconds
[    0.477776] futex hash table entries: 1024 (order: 4, 65536 bytes)
[    0.477792] Initialise system trusted keyring
[    0.477813] audit: initializing netlink subsys (disabled)
[    0.477826] audit: type=2000 audit(1432999495.476:1): initialized
[    0.478065] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.479142] zpool: loaded
[    0.479144] zbud: loaded
[    0.479265] VFS: Disk quotas dquot_6.5.2
[    0.479290] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.479624] fuse init (API version 7.23)
[    0.479709] msgmni has been set to 31991
[    0.479754] Key type big_key registered
[    0.480072] Key type asymmetric registered
[    0.480074] Asymmetric key parser 'x509' registered
[    0.480100] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.480134] io scheduler noop registered
[    0.480136] io scheduler deadline registered (default)
[    0.480173] io scheduler cfq registered
[    0.480327] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.480449] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    0.480598] pcieport 0000:00:1c.4: irq 42 for MSI/MSI-X
[    0.480716] pcieport 0000:00:1c.5: irq 43 for MSI/MSI-X
[    0.480790] pcieport 0000:00:01.0: Signaling PME through PCIe PME interrupt
[    0.480792] pci 0000:01:00.0: Signaling PME through PCIe PME interrupt
[    0.480793] pci 0000:01:00.1: Signaling PME through PCIe PME interrupt
[    0.480795] pcie_pme 0000:00:01.0:pcie01: service driver pcie_pme loaded
[    0.480816] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
[    0.480820] pcie_pme 0000:00:1c.0:pcie01: service driver pcie_pme loaded
[    0.480835] pcieport 0000:00:1c.4: Signaling PME through PCIe PME interrupt
[    0.480836] pci 0000:03:00.0: Signaling PME through PCIe PME interrupt
[    0.480840] pcie_pme 0000:00:1c.4:pcie01: service driver pcie_pme loaded
[    0.480855] pcieport 0000:00:1c.5: Signaling PME through PCIe PME interrupt
[    0.480856] pci 0000:04:00.0: Signaling PME through PCIe PME interrupt
[    0.480860] pcie_pme 0000:00:1c.5:pcie01: service driver pcie_pme loaded
[    0.480873] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.480885] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.480921] vesafb: mode is 1920x1080x32, linelength=7680, pages=0
[    0.480922] vesafb: scrolling: redraw
[    0.480923] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[    0.482940] vesafb: framebuffer at 0xe0000000, mapped to 0xffffc90005b80000, using 8128k, total 8128k
[    0.483043] Console: switching to colour frame buffer device 240x67
[    0.483065] fb0: VESA VGA frame buffer device
[    0.483090] intel_idle: MWAIT substates: 0x1120
[    0.483091] intel_idle: v0.4 model 0x3A
[    0.483092] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.483265] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.483268] ACPI: Power Button [PWRB]
[    0.483297] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.483298] ACPI: Power Button [PWRF]
[    0.483453] GHES: HEST is not enabled!
[    0.483530] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.503957] 00:07: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
[    0.505140] Linux agpgart interface v0.103
[    0.506060] brd: module loaded
[    0.506525] loop: module loaded
[    0.506683] libphy: Fixed MDIO Bus: probed
[    0.506686] tun: Universal TUN/TAP device driver, 1.6
[    0.506687] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.506721] PPP generic driver version 2.4.2
[    0.506754] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.506757] ehci-pci: EHCI PCI platform driver
[    0.506847] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    0.506851] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    0.506863] ehci-pci 0000:00:1a.0: debug port 2
[    0.510767] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    0.510784] ehci-pci 0000:00:1a.0: irq 16, io mem 0xf7f18000
[    0.519633] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    0.519662] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.519664] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.519665] usb usb1: Product: EHCI Host Controller
[    0.519666] usb usb1: Manufacturer: Linux 3.16.0-38-generic ehci_hcd
[    0.519667] usb usb1: SerialNumber: 0000:00:1a.0
[    0.519756] hub 1-0:1.0: USB hub found
[    0.519763] hub 1-0:1.0: 2 ports detected
[    0.519919] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    0.519923] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.519934] ehci-pci 0000:00:1d.0: debug port 2
[    0.523823] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    0.523837] ehci-pci 0000:00:1d.0: irq 23, io mem 0xf7f17000
[    0.535657] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    0.535703] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    0.535704] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.535706] usb usb2: Product: EHCI Host Controller
[    0.535707] usb usb2: Manufacturer: Linux 3.16.0-38-generic ehci_hcd
[    0.535708] usb usb2: SerialNumber: 0000:00:1d.0
[    0.535856] hub 2-0:1.0: USB hub found
[    0.535862] hub 2-0:1.0: 2 ports detected
[    0.535957] ehci-platform: EHCI generic platform driver
[    0.535963] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.535967] ohci-pci: OHCI PCI platform driver
[    0.535974] ohci-platform: OHCI generic platform driver
[    0.535979] uhci_hcd: USB Universal Host Controller Interface driver
[    0.536066] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.536070] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
[    0.536160] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    0.536179] xhci_hcd 0000:00:14.0: irq 44 for MSI/MSI-X
[    0.536231] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    0.536232] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.536233] usb usb3: Product: xHCI Host Controller
[    0.536234] usb usb3: Manufacturer: Linux 3.16.0-38-generic xhci_hcd
[    0.536235] usb usb3: SerialNumber: 0000:00:14.0
[    0.536372] hub 3-0:1.0: USB hub found
[    0.536382] hub 3-0:1.0: 4 ports detected
[    0.536633] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.536636] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 4
[    0.536664] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
[    0.536665] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.536666] usb usb4: Product: xHCI Host Controller
[    0.536667] usb usb4: Manufacturer: Linux 3.16.0-38-generic xhci_hcd
[    0.536668] usb usb4: SerialNumber: 0000:00:14.0
[    0.536806] hub 4-0:1.0: USB hub found
[    0.536816] hub 4-0:1.0: 4 ports detected
[    0.537096] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    0.540371] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.540375] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.540555] mousedev: PS/2 mouse device common for all mice
[    0.540761] rtc_cmos 00:02: RTC can wake from S4
[    0.540903] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.540931] rtc_cmos 00:02: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.540980] device-mapper: uevent: version 1.0.3
[    0.541067] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
[    0.541079] Intel P-state driver initializing.
[    0.541088] Intel pstate controlling: cpu 0
[    0.541128] Intel pstate controlling: cpu 1
[    0.541183] Intel pstate controlling: cpu 2
[    0.541200] Intel pstate controlling: cpu 3
[    0.541236] Consider also installing thermald for improved thermal control.
[    0.541243] ledtrig-cpu: registered to indicate activity on CPUs
[    0.541377] TCP: cubic registered
[    0.541523] NET: Registered protocol family 10
[    0.541826] NET: Registered protocol family 17
[    0.541842] Key type dns_resolver registered
[    0.542345] Loading compiled-in X.509 certificates
[    0.543611] Loaded X.509 cert 'Magrathea: Glacier signing key: c284edaccf0b473652c34d23bec356944236e63b'
[    0.543650] registered taskstats version 1
[    0.545527] Key type trusted registered
[    0.548606] Key type encrypted registered
[    0.548611] AppArmor: AppArmor sha1 policy hashing enabled
[    0.548614] ima: No TPM chip found, activating TPM-bypass!
[    0.548633] evm: HMAC attrs: 0x1
[    0.549028]   Magic number: 15:214:438
[    0.549149] rtc_cmos 00:02: setting system clock to 2015-05-30 15:24:56 UTC (1432999496)
[    0.549203] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.549203] EDD information not available.
[    0.549255] PM: Hibernation image not present or could not be loaded.
[    0.549917] Freeing unused kernel memory: 1352K (ffffffff81d1c000 - ffffffff81e6e000)
[    0.549919] Write protecting the kernel read-only data: 12288k
[    0.551019] Freeing unused kernel memory: 556K (ffff880001775000 - ffff880001800000)
[    0.552031] Freeing unused kernel memory: 500K (ffff880001b83000 - ffff880001c00000)
[    0.560220] systemd-udevd[114]: starting version 204
[    0.576222] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    0.576225] ahci 0000:00:1f.2: version 3.0
[    0.576229] r8169 0000:04:00.0: can't disable ASPM; OS doesn't have ASPM control
[    0.576354] ahci 0000:00:1f.2: irq 45 for MSI/MSI-X
[    0.576534] r8169 0000:04:00.0: irq 46 for MSI/MSI-X
[    0.576736] r8169 0000:04:00.0 eth0: RTL8168evl/8111evl at 0xffffc90005b7a000, bc:5f:f4:45:80:ab, XID 0c900800 IRQ 46
[    0.576738] r8169 0000:04:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    0.591652] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x3f impl SATA mode
[    0.591656] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part ems apst 
[    0.632235] scsi0 : ahci
[    0.632471] scsi1 : ahci
[    0.632696] scsi2 : ahci
[    0.632860] scsi3 : ahci
[    0.632954] scsi4 : ahci
[    0.633046] scsi5 : ahci
[    0.633078] ata1: SATA max UDMA/133 abar m2048@0xf7f16000 port 0xf7f16100 irq 45
[    0.633080] ata2: SATA max UDMA/133 abar m2048@0xf7f16000 port 0xf7f16180 irq 45
[    0.633082] ata3: SATA max UDMA/133 abar m2048@0xf7f16000 port 0xf7f16200 irq 45
[    0.633085] ata4: SATA max UDMA/133 abar m2048@0xf7f16000 port 0xf7f16280 irq 45
[    0.633086] ata5: SATA max UDMA/133 abar m2048@0xf7f16000 port 0xf7f16300 irq 45
[    0.633089] ata6: SATA max UDMA/133 abar m2048@0xf7f16000 port 0xf7f16380 irq 45
[    0.633226] ahci 0000:03:00.0: irq 47 for MSI/MSI-X
[    0.633245] ahci 0000:03:00.0: SSS flag set, parallel bus scan disabled
[    0.633296] ahci 0000:03:00.0: AHCI 0001.0200 32 slots 2 ports 6 Gbps 0x3 impl SATA mode
[    0.633298] ahci 0000:03:00.0: flags: 64bit ncq sntf stag led clo pmp pio slum part ccc sxs 
[    0.633524] scsi6 : ahci
[    0.633600] scsi7 : ahci
[    0.633632] ata7: SATA max UDMA/133 abar m512@0xf7d00000 port 0xf7d00100 irq 47
[    0.633635] ata8: SATA max UDMA/133 abar m512@0xf7d00000 port 0xf7d00180 irq 47
[    0.831642] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    0.951573] ata6: SATA link down (SStatus 0 SControl 300)
[    0.951609] ata7: SATA link down (SStatus 0 SControl 300)
[    0.951621] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    0.951639] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    0.951658] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    0.951674] ata4: SATA link down (SStatus 0 SControl 300)
[    0.951692] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    0.952341] ata5.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    0.952346] ata5.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    0.952350] ata5.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    0.952994] ata5.00: ATA-8: ST1000DM003-9YN162, CC4B, max UDMA/133
[    0.952999] ata5.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    0.953267] ata2.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    0.953272] ata2.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    0.953276] ata2.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    0.953668] ata5.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    0.953673] ata5.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    0.953676] ata5.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    0.954256] ata2.00: ATAPI: HL-DT-ST DVDRAM GH24NSC0, LK00, max UDMA/133
[    0.954310] ata5.00: configured for UDMA/133
[    0.954603] ata3.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    0.954607] ata3.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    0.954610] ata3.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    0.954867] ata3.00: ATAPI: ASUS    DRW-24B5ST, 1.00, max UDMA/100
[    0.956150] ata2.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    0.956154] ata2.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    0.956156] ata2.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    0.956404] ata3.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    0.956408] ata3.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    0.956410] ata3.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    0.956666] ata3.00: configured for UDMA/100
[    0.957165] ata2.00: configured for UDMA/133
[    0.963001] ata1.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    0.963005] ata1.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    0.963007] ata1.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    0.963872] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
[    0.963875] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    0.964143] hub 1-1:1.0: USB hub found
[    0.964220] hub 1-1:1.0: 6 ports detected
[    0.973405] ata1.00: ATA-8: OCZ-VERTEX3, 2.22, max UDMA/133
[    0.973408] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    0.983008] ata1.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    0.983013] ata1.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    0.983016] ata1.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    0.993422] ata1.00: configured for UDMA/133
[    0.993599] scsi 0:0:0:0: Direct-Access     ATA      OCZ-VERTEX3      2.22 PQ: 0 ANSI: 5
[    0.993811] sd 0:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[    0.993837] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.993843] sd 0:0:0:0: [sda] Write Protect is off
[    0.993845] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.993855] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.994132]  sda: sda1 sda2
[    0.994319] sd 0:0:0:0: [sda] Attached SCSI disk
[    0.994625] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH24NSC0  LK00 PQ: 0 ANSI: 5
[    1.014476] sr0: scsi3-mmc drive: 48x/12x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.014478] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.014626] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.014682] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.018084] scsi 2:0:0:0: CD-ROM            ASUS     DRW-24B5ST       1.00 PQ: 0 ANSI: 5
[    1.036405] sr1: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.036559] sr 2:0:0:0: Attached scsi CD-ROM sr1
[    1.036670] sr 2:0:0:0: Attached scsi generic sg2 type 5
[    1.036851] scsi 4:0:0:0: Direct-Access     ATA      ST1000DM003-9YN1 CC4B PQ: 0 ANSI: 5
[    1.037127] sd 4:0:0:0: Attached scsi generic sg3 type 0
[    1.037181] sd 4:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.037183] sd 4:0:0:0: [sdb] 4096-byte physical blocks
[    1.037338] sd 4:0:0:0: [sdb] Write Protect is off
[    1.037340] sd 4:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.037374] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.072504]  sdb: sdb1 sdb4 < sdb5 >
[    1.073041] sd 4:0:0:0: [sdb] Attached SCSI disk
[    1.075529] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    1.207961] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
[    1.207966] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.208201] hub 2-1:1.0: USB hub found
[    1.208332] hub 2-1:1.0: 6 ports detected
[    1.355508] ata8: SATA link down (SStatus 0 SControl 300)
[    1.375494] usb 3-2: new high-speed USB device number 2 using xhci_hcd
[    1.395194] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[    1.466235] random: init urandom read with 70 bits of entropy available
[    1.475430] tsc: Refined TSC clocksource calibration: 3092.974 MHz
[    1.485868] init: plymouth-upstart-bridge main process (197) terminated with status 1
[    1.485878] init: plymouth-upstart-bridge main process ended, respawning
[    1.489035] init: plymouth-upstart-bridge main process (207) terminated with status 1
[    1.489043] init: plymouth-upstart-bridge main process ended, respawning
[    1.491194] init: plymouth-upstart-bridge main process (210) terminated with status 1
[    1.491203] init: plymouth-upstart-bridge main process ended, respawning
[    1.492773] init: plymouth-upstart-bridge main process (212) terminated with status 1
[    1.492781] init: plymouth-upstart-bridge main process ended, respawning
[    1.506124] usb 3-2: New USB device found, idVendor=0846, idProduct=9020
[    1.506127] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.506129] usb 3-2: Product: Remote Download Wireless Adapter
[    1.506130] usb 3-2: Manufacturer: Broadcom
[    1.506131] usb 3-2: SerialNumber: 113
[    1.579461] usb 1-1.1: new high-speed USB device number 3 using ehci-pci
[    1.602383] systemd-udevd[327]: starting version 204
[    1.631009] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    1.639339] mei_me 0000:00:16.0: irq 48 for MSI/MSI-X
[    1.648426] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
[    1.653711] parport_pc 00:05: reported by Plug and Play ACPI
[    1.653789] parport0: PC-style at 0x378 (0x778), irq 5, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[    1.661164] AMD IOMMUv2 driver by Joerg Roedel <joerg.roedel@amd.com>
[    1.661166] AMD IOMMUv2 functionality not available on this system
[    1.676159] ACPI Warning: SystemIO range 0x0000000000000428-0x000000000000042f conflicts with OpRegion 0x0000000000000400-0x000000000000047f (\PMIO) (20140424/utaddress-258)
[    1.676165] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    1.676168] ACPI Warning: SystemIO range 0x0000000000000540-0x000000000000054f conflicts with OpRegion 0x0000000000000500-0x000000000000057f (\GPR2) (20140424/utaddress-258)
[    1.676170] ACPI Warning: SystemIO range 0x0000000000000540-0x000000000000054f conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20140424/utaddress-258)
[    1.676172] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    1.676173] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053f conflicts with OpRegion 0x0000000000000500-0x000000000000057f (\GPR2) (20140424/utaddress-258)
[    1.676175] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053f conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20140424/utaddress-258)
[    1.676177] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    1.676178] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052f conflicts with OpRegion 0x0000000000000500-0x000000000000057f (\GPR2) (20140424/utaddress-258)
[    1.676180] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052f conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20140424/utaddress-258)
[    1.676182] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    1.676183] lpc_ich: Resource conflict(s) found affecting gpio_ich
[    1.691727] AVX version of gcm_enc/dec engaged.
[    1.702683] usb 1-1.1: New USB device found, idVendor=05e3, idProduct=0732
[    1.702686] usb 1-1.1: New USB device strings: Mfr=3, Product=4, SerialNumber=5
[    1.702687] usb 1-1.1: Product: USB Reader
[    1.702688] usb 1-1.1: Manufacturer: Genesys
[    1.702689] usb 1-1.1: SerialNumber: 000000008892
[    1.712228] lp: driver loaded but no devices found
[    1.722585] ppdev: user-space parallel port driver
[    1.722698] audit: type=1400 audit(1432992297.669:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=402 comm="apparmor_parser"
[    1.722703] audit: type=1400 audit(1432992297.669:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=402 comm="apparmor_parser"
[    1.722707] audit: type=1400 audit(1432992297.669:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=402 comm="apparmor_parser"
[    1.723020] audit: type=1400 audit(1432992297.669:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=402 comm="apparmor_parser"
[    1.723024] audit: type=1400 audit(1432992297.669:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=402 comm="apparmor_parser"
[    1.723189] audit: type=1400 audit(1432992297.669:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=402 comm="apparmor_parser"
[    1.725763] audit: type=1400 audit(1432992297.673:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/ntpd" pid=439 comm="apparmor_parser"
[    1.731088] intel_rapl: Found RAPL domain package
[    1.731091] intel_rapl: Found RAPL domain core
[    1.749700] snd_hda_intel 0000:00:1b.0: irq 49 for MSI/MSI-X
[    1.749780] snd_hda_intel 0000:01:00.1: Handle VGA-switcheroo audio client
[    1.749782] snd_hda_intel 0000:01:00.1: Force to non-snoop mode
[    1.749798] snd_hda_intel 0000:01:00.1: irq 50 for MSI/MSI-X
[    1.751477] lp0: using parport0 (interrupt-driven).
[    1.771790] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input5
[    1.771840] input: HDA ATI HDMI HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input6
[    1.771886] input: HDA ATI HDMI HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input7
[    1.771943] input: HDA ATI HDMI HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input8
[    1.772001] input: HDA ATI HDMI HDMI/DP,pcm=10 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input9
[    1.772044] input: HDA ATI HDMI HDMI/DP,pcm=11 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input10
[    1.774465] sound hdaudioC0D0: autoconfig: line_outs=3 (0x14/0x15/0x16/0x0/0x0) type:line
[    1.774467] sound hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    1.774469] sound hdaudioC0D0:    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[    1.774470] sound hdaudioC0D0:    mono: mono_out=0x0
[    1.774471] sound hdaudioC0D0:    dig-out=0x1e/0x0
[    1.774472] sound hdaudioC0D0:    inputs:
[    1.774474] sound hdaudioC0D0:      Front Mic=0x19
[    1.774475] sound hdaudioC0D0:      Rear Mic=0x18
[    1.774476] sound hdaudioC0D0:      Line=0x1a
[    1.775544] usb 1-1.5: new full-speed USB device number 4 using ehci-pci
[    1.799682] input: HDA Intel PCH Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[    1.799733] input: HDA Intel PCH Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[    1.799778] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[    1.799826] input: HDA Intel PCH Line Out Front as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[    1.799869] input: HDA Intel PCH Line Out Surround as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
[    1.799911] input: HDA Intel PCH Line Out CLFE as /devices/pci0000:00/0000:00:1b.0/sound/card0/input16
[    1.799954] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input17
[    1.866434] random: nonblocking pool is initialized
[    1.878914] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[    1.878916] Disabling lock debugging due to kernel taint
[    1.882977] fglrx: module verification failed: signature and/or  required key missing - tainting kernel
[    1.903366] <6>[fglrx] Maximum main memory to use for locked dma buffers: 15623 MBytes.
[    1.903475] <6>[fglrx]   vendor: 1002 device: 679e revision: 0 count: 1
[    1.903662] <6>[fglrx] ioport: bar 4, base 0xe000, size: 0x100
[    1.903818] <6>[fglrx] Kernel PAT support is enabled
[    1.903831] <6>[fglrx] module loaded - fglrx 15.20.2 [Feb 27 2015] with 1 minors
[    1.948073] Bluetooth: Core ver 2.19
[    1.948086] NET: Registered protocol family 31
[    1.948087] Bluetooth: HCI device and connection manager initialized
[    1.948093] Bluetooth: HCI socket layer initialized
[    1.948094] Bluetooth: L2CAP socket layer initialized
[    1.948101] Bluetooth: SCO socket layer initialized
[    1.990131] usb 1-1.5: New USB device found, idVendor=06a3, idProduct=0cc3
[    1.990134] usb 1-1.5: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.990135] usb 1-1.5: Product: Cyborg R.A.T.5 Mouse
[    1.990137] usb 1-1.5: Manufacturer: Saitek
[    2.011186] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    2.011188] Bluetooth: BNEP filters: protocol multicast
[    2.011194] Bluetooth: BNEP socket layer initialized
[    2.014463] Bluetooth: RFCOMM TTY layer initialized
[    2.014471] Bluetooth: RFCOMM socket layer initialized
[    2.014474] Bluetooth: RFCOMM ver 1.11
[    2.024125] init: failsafe main process (561) killed by TERM signal
[    2.059361] usb 1-1.6: new low-speed USB device number 5 using ehci-pci
[    2.062011] audit: type=1400 audit(1432992298.009:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=721 comm="apparmor_parser"
[    2.062018] audit: type=1400 audit(1432992298.009:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=721 comm="apparmor_parser"
[    2.106945] init: cups main process (725) killed by HUP signal
[    2.106954] init: cups main process ended, respawning
[    2.164346] usb 1-1.6: New USB device found, idVendor=046a, idProduct=010d
[    2.164348] usb 1-1.6: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.170726] hidraw: raw HID events driver (C) Jiri Kosina
[    2.181221] usb-storage 1-1.1:1.0: USB Mass Storage device detected
[    2.182413] scsi8 : usb-storage 1-1.1:1.0
[    2.182475] usbcore: registered new interface driver usb-storage
[    2.183537] usbcore: registered new interface driver uas
[    2.195827] usbcore: registered new interface driver usbhid
[    2.195830] usbhid: USB HID core driver
[    2.197502] input: Saitek Cyborg R.A.T.5 Mouse as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.0/0003:06A3:0CC3.0001/input/input18
[    2.200171] hid-generic 0003:06A3:0CC3.0001: input,hidraw0: USB HID v1.11 Mouse [Saitek Cyborg R.A.T.5 Mouse] on usb-0000:00:1a.0-1.5/input0
[    2.200474] input: HID 046a:010d as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/0003:046A:010D.0002/input/input19
[    2.200614] hid-generic 0003:046A:010D.0002: input,hidraw1: USB HID v1.11 Keyboard [HID 046a:010d] on usb-0000:00:1a.0-1.6/input0
[    2.202360] input: HID 046a:010d as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.1/0003:046A:010D.0003/input/input20
[    2.202847] hid-generic 0003:046A:010D.0003: input,hidraw2: USB HID v1.11 Device [HID 046a:010d] on usb-0000:00:1a.0-1.6/input1
[    2.235465] usb 2-1.5: new full-speed USB device number 3 using ehci-pci


```

---

### Post by kryten35 on 2015-05-30
This is a possible solution

Replace pluma with the name of the text editor used in your dektop
Terminal
```
gksudo pluma /etc/X11/xorg.config
```
And stick this in it
```
Section "InputClass"
Identifier "Mouse Remap"
MatchProduct "Saitek Cyborg R.A.T.5 Mouse"
MatchDevicePath "/dev/input/event*"
Option "ButtonMapping" "1 2 3 4 5 0 0 8 9 10 11 12 0 0 0 0 0"
EndSection
```

Save the file as xorg.config  in etc/X11  and reboot.If it doesnt work, then go back in and delete it.

---

### Post by andre45 on 2015-06-03
It worked! Thank you!! :)

---

### Post by RobGoss on 2015-06-03
If you found a solution to your problem please mark your thread as** SOLVED **- You can do this by accessing the **Thread Tool** at the top of this post and choose ( SOLVED ) Thanks

---

