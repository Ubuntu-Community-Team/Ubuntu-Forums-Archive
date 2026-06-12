---
title: "Trying to get full resolution with ATI 9802 card"
date: 2011-03-03
forum: Hardware
---

### Post by hreichgott on 2011-03-03
Hi,
Just got a new Acer Aspire laptop with an ATI 9802 graphics card.
```
00:01.0 VGA compatible controller: ATI Technologies Inc Device 9802

```
Booted into Windows 7 first to make sure all hardware was in working order. Observed that screen resolution was 1366x768. Then installed Ubuntu 10.10. The only option I have for graphics is 1024x768.
I am using the open source driver. I tried using the proprietary one (fglrx?) and succeeded in getting the full 1366x768, but there was an annoying "AMD Unsupported Hardware" watermark on the bottom of the screen.

I noticed this on the "unofficial Linux ATI page" at [http://wiki.cchtml.com/index.php/Hardware#RADEON_HD](http://wiki.cchtml.com/index.php/Hardware#RADEON_HD)

```

**Radeon (Catalyst Legacy & Open Source) **

 ATI/AMD dropped Catalyst support for these cards in Catalyst 9-4.  These cards are supported with the legacy ATI 9-3 Catalyst release, but  you MUST use a kernel 2.6.28 (or earlier) and Xserver 1.5 (or earlier).  For example, you can use Catalyst 9-3 if you're running Ubuntu 8.04 or  Debian Lenny/5.0. Open source support is good and 3D is still improving. 
 * RS400/RS480 Radeon XPRESS 200(M)/1100 IGP * R300        Radeon 9700PRO/9700/9500PRO/9500/9600TX, FireGL X1/Z1 * R350        Radeon 9800PRO/9800SE/9800, FireGL X2 * R360        Radeon 9800XT * RV350       Radeon 9600PRO/9600SE/9600/9550, M10/M11, FireGL T2 * RV360       Radeon 9600XT * RV370       Radeon X300, M22 * RV380       Radeon X600, M24 * RV410       Radeon X700, M26 PCIE * R420        Radeon X800 AGP * R423/R430   Radeon X800, M28 PCIE * R480/R481   Radeon X850 PCIE/AGP * RS482       Radeon (Xpress) 200 * RV505       Radeon X1300, M52, M62 * RV515       Radeon X1400, M54, M64 * RV516       Radeon X1500 * RV550       Radeon X2300 * R520        Radeon X1800, M58 * RV530/RV560 Radeon X1600/X1650/X1700, M56, M66 * RV570/R580  Radeon X1900/X1950, M68 * RS600/RS690 Radeon (Xpress) X1200/X1250/X1270 * RS740       Radeon X2100 * FireGL T2 (4154) * FireGL V3100 (5B64) * FireGL V3200 (3E54) * FireGL V3300 (5E49) * FireGL V5000 (5E48) * FireGL V5100 (5551) * FireGL V7100 (5550) * FireGL X1 (4E47) * FireGL X2-256/X2-256t (4E4B) * FireGL X3-256 (4A4D) * FireGL Z1 (4147) 
```

It doesn't say 9802 but this is the closest thing on the page to it.
If "open source support is good," presumably I can get 1366x768 somehow?
thanks

---

### Post by Yellow Pasque on 2011-03-03
Post your /var/log/Xorg.0.log

---

### Post by hreichgott on 2011-03-03
```
[    12.872] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    12.872] X Protocol Version 11, Revision 0
[    12.872] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[    12.872] Current Operating System: Linux Data 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 i686
[    12.872] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=8769c21a-9b5e-4e6b-8ddf-22882e559d6e ro quiet splash
[    12.872] Build Date: 16 September 2010  05:39:22PM
[    12.872] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
[    12.872] Current version of pixman: 0.18.4
[    12.872]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    12.872] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    12.873] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Mar  3 19:22:09 2011
[    12.886] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    12.887] (==) No Layout section.  Using the first Screen section.
[    12.887] (==) No screen section available. Using defaults.
[    12.887] (**) |-->Screen "Default Screen Section" (0)
[    12.887] (**) |   |-->Monitor "<default monitor>"
[    12.887] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    12.887] (==) Automatically adding devices
[    12.887] (==) Automatically enabling devices
[    12.890] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    12.890]     Entry deleted from font path.
[    12.890] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    12.890] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    12.890] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    12.890] (II) Loader magic: 0x81f8e00
[    12.890] (II) Module ABI versions:
[    12.890]     X.Org ANSI C Emulation: 0.4
[    12.890]     X.Org Video Driver: 8.0
[    12.890]     X.Org XInput driver : 11.0
[    12.890]     X.Org Server Extension : 4.0
[    12.891] (--) PCI:*(0:0:1:0) 1002:9802:1025:0520 rev 0, Mem @ 0x80000000/268435456, 0x90500000/262144, I/O @ 0x00004000/256
[    12.892] (II) Open ACPI successful (/var/run/acpid.socket)
[    12.893] (II) LoadModule: "extmod"
[    12.904] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    12.904] (II) Module extmod: vendor="X.Org Foundation"
[    12.904]     compiled for 1.9.0, module version = 1.0.0
[    12.904]     Module class: X.Org Server Extension
[    12.904]     ABI class: X.Org Server Extension, version 4.0
[    12.904] (II) Loading extension MIT-SCREEN-SAVER
[    12.904] (II) Loading extension XFree86-VidModeExtension
[    12.904] (II) Loading extension XFree86-DGA
[    12.904] (II) Loading extension DPMS
[    12.904] (II) Loading extension XVideo
[    12.904] (II) Loading extension XVideo-MotionCompensation
[    12.904] (II) Loading extension X-Resource
[    12.904] (II) LoadModule: "dbe"
[    12.905] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    12.905] (II) Module dbe: vendor="X.Org Foundation"
[    12.905]     compiled for 1.9.0, module version = 1.0.0
[    12.905]     Module class: X.Org Server Extension
[    12.905]     ABI class: X.Org Server Extension, version 4.0
[    12.905] (II) Loading extension DOUBLE-BUFFER
[    12.905] (II) LoadModule: "glx"
[    12.906] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    12.906] (II) Module glx: vendor="X.Org Foundation"
[    12.906]     compiled for 1.9.0, module version = 1.0.0
[    12.906]     ABI class: X.Org Server Extension, version 4.0
[    12.906] (==) AIGLX enabled
[    12.906] (II) Loading extension GLX
[    12.906] (II) LoadModule: "record"
[    12.907] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    12.907] (II) Module record: vendor="X.Org Foundation"
[    12.907]     compiled for 1.9.0, module version = 1.13.0
[    12.907]     Module class: X.Org Server Extension
[    12.907]     ABI class: X.Org Server Extension, version 4.0
[    12.907] (II) Loading extension RECORD
[    12.907] (II) LoadModule: "dri"
[    12.907] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    12.908] (II) Module dri: vendor="X.Org Foundation"
[    12.908]     compiled for 1.9.0, module version = 1.0.0
[    12.908]     ABI class: X.Org Server Extension, version 4.0
[    12.908] (II) Loading extension XFree86-DRI
[    12.908] (II) LoadModule: "dri2"
[    12.908] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    12.909] (II) Module dri2: vendor="X.Org Foundation"
[    12.909]     compiled for 1.9.0, module version = 1.2.0
[    12.909]     ABI class: X.Org Server Extension, version 4.0
[    12.909] (II) Loading extension DRI2
[    12.909] (==) Matched ati as autoconfigured driver 0
[    12.909] (==) Matched vesa as autoconfigured driver 1
[    12.909] (==) Matched fbdev as autoconfigured driver 2
[    12.909] (==) Assigned the driver to the xf86ConfigLayout
[    12.909] (II) LoadModule: "ati"
[    12.909] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    12.909] (II) Module ati: vendor="X.Org Foundation"
[    12.909]     compiled for 1.9.0, module version = 6.13.1
[    12.909]     Module class: X.Org Video Driver
[    12.909]     ABI class: X.Org Video Driver, version 8.0
[    12.909] (II) LoadModule: "radeon"
[    12.910] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    12.910] (II) Module radeon: vendor="X.Org Foundation"
[    12.910]     compiled for 1.9.0, module version = 6.13.1
[    12.910]     Module class: X.Org Video Driver
[    12.910]     ABI class: X.Org Video Driver, version 8.0
[    12.910] (II) LoadModule: "vesa"
[    12.910] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    12.911] (II) Module vesa: vendor="X.Org Foundation"
[    12.911]     compiled for 1.8.99.905, module version = 2.3.0
[    12.911]     Module class: X.Org Video Driver
[    12.911]     ABI class: X.Org Video Driver, version 8.0
[    12.911] (II) LoadModule: "fbdev"
[    12.911] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    12.911] (II) Module fbdev: vendor="X.Org Foundation"
[    12.911]     compiled for 1.8.99.905, module version = 0.4.2
[    12.911]     ABI class: X.Org Video Driver, version 8.0
[    12.911] (II) RADEON: Driver for ATI Radeon chipsets:
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
    ATI Radeon 8500 AIW BB (AGP), ATI Radeon 8500 AIW BC (AGP),
    ATI Radeon IGP320M (U1) 4336, ATI Radeon IGP330M/340M/350M (U2) 4337,
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
    ATI Radeon 3000 Graphics, ATI Radeon HD 4200, ATI Radeon 4100,
    ATI Mobility Radeon HD 4200, ATI Mobility Radeon 4100,
    ATI Radeon HD 4290, ATI Radeon HD 4290, CYPRESS,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5900 Series, ATI Radeon HD 5900 Series,
    ATI Mobility Radeon HD 5800 Series,
    ATI Mobility Radeon HD 5800 Series,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
    ATI Radeon HD 5700 Series, ATI Radeon HD 5700 Series,
    ATI Mobility Radeon HD 5000 Series,
    ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5670,
    ATI Radeon HD 5570, ATI Radeon HD 5500 Series, REDWOOD,
    ATI Mobility Radeon HD 5000 Series,
    ATI Mobility Radeon HD 5000 Series, CEDAR, CEDAR, CEDAR,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, CEDAR, ATI Radeon HD 5450,
    CEDAR
[    12.923] (II) VESA: driver for VESA chipsets: vesa
[    12.923] (II) FBDEV: driver for framebuffer: fbdev
[    12.923] (++) using VT number 7

[    12.925] (WW) Falling back to old probe method for fbdev
[    12.925] (II) Loading sub module "fbdevhw"
[    12.925] (II) LoadModule: "fbdevhw"
[    12.925] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    12.925] (II) Module fbdevhw: vendor="X.Org Foundation"
[    12.925]     compiled for 1.9.0, module version = 0.0.2
[    12.925]     ABI class: X.Org Video Driver, version 8.0
[    12.925] (EE) open /dev/fb0: No such file or directory
[    12.925] (II) Loading sub module "vbe"
[    12.925] (II) LoadModule: "vbe"
[    12.926] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    12.926] (II) Module vbe: vendor="X.Org Foundation"
[    12.926]     compiled for 1.9.0, module version = 1.1.0
[    12.926]     ABI class: X.Org Video Driver, version 8.0
[    12.926] (II) Loading sub module "int10"
[    12.926] (II) LoadModule: "int10"
[    12.927] (II) Loading /usr/lib/xorg/modules/libint10.so
[    12.927] (II) Module int10: vendor="X.Org Foundation"
[    12.927]     compiled for 1.9.0, module version = 1.0.0
[    12.927]     ABI class: X.Org Video Driver, version 8.0
[    12.927] (II) VESA(0): initializing int10
[    12.933] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    12.933] (II) VESA(0): VESA BIOS detected
[    12.934] (II) VESA(0): VESA VBE Version 3.0
[    12.934] (II) VESA(0): VESA VBE Total Mem: 16384 kB
[    12.934] (II) VESA(0): VESA VBE OEM: AMD ATOMBIOS
[    12.934] (II) VESA(0): VESA VBE OEM Software Rev: 12.37
[    12.934] (II) VESA(0): VESA VBE OEM Vendor: (C) 1988-2010, AMD Technologies Inc. 
[    12.934] (II) VESA(0): VESA VBE OEM Product: WRESTLER
[    12.934] (II) VESA(0): VESA VBE OEM Product Rev: 01.00
[    13.016] (II) VESA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    13.016] (==) VESA(0): Depth 24, (--) framebuffer bpp 32
[    13.016] (==) VESA(0): RGB weight 888
[    13.016] (==) VESA(0): Default visual is TrueColor
[    13.016] (==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
[    13.016] (II) Loading sub module "ddc"
[    13.016] (II) LoadModule: "ddc"
[    13.016] (II) Module "ddc" already built-in
[    13.016] (II) VESA(0): VESA VBE DDC supported
[    13.016] (II) VESA(0): VESA VBE DDC Level 2
[    13.016] (II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
[    13.303] (II) VESA(0): VESA VBE DDC read successfully
[    13.303] (II) VESA(0): Manufacturer: LGD  Model: 250  Serial#: 0
[    13.303] (II) VESA(0): Year: 2010  Week: 0
[    13.303] (II) VESA(0): EDID Version: 1.3
[    13.303] (II) VESA(0): Digital Display Input
[    13.303] (II) VESA(0): Max Image Size [cm]: horiz.: 35  vert.: 19
[    13.303] (II) VESA(0): Gamma: 2.20
[    13.304] (II) VESA(0): No DPMS capabilities specified
[    13.304] (II) VESA(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    13.304] (II) VESA(0): First detailed timing is preferred mode
[    13.304] (II) VESA(0): redX: 0.612 redY: 0.375   greenX: 0.332 greenY: 0.619
[    13.304] (II) VESA(0): blueX: 0.151 blueY: 0.099   whiteX: 0.313 whiteY: 0.329
[    13.304] (II) VESA(0): Manufacturer's mask: 0
[    13.304] (II) VESA(0): Supported detailed timing:
[    13.304] (II) VESA(0): clock: 72.3 MHz   Image Size:  345 x 194 mm
[    13.304] (II) VESA(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1526 h_border: 0
[    13.304] (II) VESA(0): v_active: 768  v_sync: 771  v_sync_end 776 v_blanking: 790 v_border: 0
[    13.304] (II) VESA(0):  LG Display
[    13.304] (II) VESA(0):  LP156WH2-TLEA
[    13.304] (II) VESA(0): EDID (in hex):
[    13.304] (II) VESA(0):     00ffffffffffff0030e4500200000000
[    13.304] (II) VESA(0):     00140103802313780ac2d59c60559e26
[    13.304] (II) VESA(0):     19505400000001010101010101010101
[    13.304] (II) VESA(0):     0101010101013e1c56a0500016303020
[    13.304] (II) VESA(0):     350059c2100000190000000000000000
[    13.304] (II) VESA(0):     00000000000000000000000000fe004c
[    13.304] (II) VESA(0):     4720446973706c61790a2020000000fe
[    13.304] (II) VESA(0):     004c503135365748322d544c454100fd
[    13.304] (II) VESA(0): EDID vendor "LGD", prod id 592
[    13.304] (II) VESA(0): Printing DDC gathered Modelines:
[    13.304] (II) VESA(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[    13.304] (II) VESA(0): Searching for matching VESA mode(s):
[    13.305] Mode: 100 (640x400)
[    13.305]     ModeAttributes: 0xbb
[    13.305]     WinAAttributes: 0x7
[    13.305]     WinBAttributes: 0x0
[    13.305]     WinGranularity: 64
[    13.306]     WinSize: 64
[    13.306]     WinASegment: 0xa000
[    13.306]     WinBSegment: 0x0
[    13.306]     WinFuncPtr: 0xc0005543
[    13.306]     BytesPerScanline: 640
[    13.306]     XResolution: 640
[    13.306]     YResolution: 400
[    13.306]     XCharSize: 8
[    13.306]     YCharSize: 16
[    13.306]     NumberOfPlanes: 1
[    13.306]     BitsPerPixel: 8
[    13.306]     NumberOfBanks: 1
[    13.306]     MemoryModel: 4
[    13.306]     BankSize: 0
[    13.306]     NumberOfImages: 63
[    13.306]     RedMaskSize: 0
[    13.306]     RedFieldPosition: 0
[    13.306]     GreenMaskSize: 0
[    13.306]     GreenFieldPosition: 0
[    13.306]     BlueMaskSize: 0
[    13.306]     BlueFieldPosition: 0
[    13.306]     RsvdMaskSize: 0
[    13.306]     RsvdFieldPosition: 0
[    13.306]     DirectColorModeInfo: 0
[    13.306]     PhysBasePtr: 0x80000000
[    13.306]     LinBytesPerScanLine: 640
[    13.306]     BnkNumberOfImagePages: 63
[    13.306]     LinNumberOfImagePages: 63
[    13.306]     LinRedMaskSize: 0
[    13.306]     LinRedFieldPosition: 0
[    13.306]     LinGreenMaskSize: 0
[    13.306]     LinGreenFieldPosition: 0
[    13.306]     LinBlueMaskSize: 0
[    13.306]     LinBlueFieldPosition: 0
[    13.306]     LinRsvdMaskSize: 0
[    13.306]     LinRsvdFieldPosition: 0
[    13.306]     MaxPixelClock: 400000000
[    13.307] Mode: 101 (640x480)
[    13.307]     ModeAttributes: 0xbb
[    13.307]     WinAAttributes: 0x7
[    13.307]     WinBAttributes: 0x0
[    13.307]     WinGranularity: 64
[    13.307]     WinSize: 64
[    13.307]     WinASegment: 0xa000
[    13.307]     WinBSegment: 0x0
[    13.307]     WinFuncPtr: 0xc0005543
[    13.307]     BytesPerScanline: 640
[    13.307]     XResolution: 640
[    13.307]     YResolution: 480
[    13.307]     XCharSize: 8
[    13.307]     YCharSize: 16
[    13.307]     NumberOfPlanes: 1
[    13.307]     BitsPerPixel: 8
[    13.307]     NumberOfBanks: 1
[    13.307]     MemoryModel: 4
[    13.307]     BankSize: 0
[    13.307]     NumberOfImages: 50
[    13.307]     RedMaskSize: 0
[    13.307]     RedFieldPosition: 0
[    13.308]     GreenMaskSize: 0
[    13.308]     GreenFieldPosition: 0
[    13.308]     BlueMaskSize: 0
[    13.308]     BlueFieldPosition: 0
[    13.308]     RsvdMaskSize: 0
[    13.308]     RsvdFieldPosition: 0
[    13.308]     DirectColorModeInfo: 0
[    13.308]     PhysBasePtr: 0x80000000
[    13.308]     LinBytesPerScanLine: 640
[    13.308]     BnkNumberOfImagePages: 50
[    13.308]     LinNumberOfImagePages: 50
[    13.308]     LinRedMaskSize: 0
[    13.308]     LinRedFieldPosition: 0
[    13.308]     LinGreenMaskSize: 0
[    13.308]     LinGreenFieldPosition: 0
[    13.308]     LinBlueMaskSize: 0
[    13.308]     LinBlueFieldPosition: 0
[    13.308]     LinRsvdMaskSize: 0
[    13.308]     LinRsvdFieldPosition: 0
[    13.308]     MaxPixelClock: 400000000
[    13.309] Mode: 103 (800x600)
[    13.309]     ModeAttributes: 0xbb
[    13.309]     WinAAttributes: 0x7
[    13.309]     WinBAttributes: 0x0
[    13.309]     WinGranularity: 64
[    13.309]     WinSize: 64
[    13.309]     WinASegment: 0xa000
[    13.309]     WinBSegment: 0x0
[    13.309]     WinFuncPtr: 0xc0005543
[    13.309]     BytesPerScanline: 832
[    13.309]     XResolution: 800
[    13.309]     YResolution: 600
[    13.309]     XCharSize: 8
[    13.309]     YCharSize: 14
[    13.309]     NumberOfPlanes: 1
[    13.309]     BitsPerPixel: 8
[    13.309]     NumberOfBanks: 1
[    13.309]     MemoryModel: 4
[    13.309]     BankSize: 0
[    13.309]     NumberOfImages: 31
[    13.309]     RedMaskSize: 0
[    13.309]     RedFieldPosition: 0
[    13.309]     GreenMaskSize: 0
[    13.309]     GreenFieldPosition: 0
[    13.309]     BlueMaskSize: 0
[    13.309]     BlueFieldPosition: 0
[    13.309]     RsvdMaskSize: 0
[    13.309]     RsvdFieldPosition: 0
[    13.309]     DirectColorModeInfo: 0
[    13.309]     PhysBasePtr: 0x80000000
[    13.310]     LinBytesPerScanLine: 832
[    13.310]     BnkNumberOfImagePages: 31
[    13.310]     LinNumberOfImagePages: 31
[    13.310]     LinRedMaskSize: 0
[    13.310]     LinRedFieldPosition: 0
[    13.310]     LinGreenMaskSize: 0
[    13.310]     LinGreenFieldPosition: 0
[    13.310]     LinBlueMaskSize: 0
[    13.310]     LinBlueFieldPosition: 0
[    13.310]     LinRsvdMaskSize: 0
[    13.310]     LinRsvdFieldPosition: 0
[    13.310]     MaxPixelClock: 400000000
[    13.311] Mode: 105 (1024x768)
[    13.311]     ModeAttributes: 0xbb
[    13.311]     WinAAttributes: 0x7
[    13.311]     WinBAttributes: 0x0
[    13.311]     WinGranularity: 64
[    13.311]     WinSize: 64
[    13.311]     WinASegment: 0xa000
[    13.311]     WinBSegment: 0x0
[    13.311]     WinFuncPtr: 0xc0005543
[    13.311]     BytesPerScanline: 1024
[    13.311]     XResolution: 1024
[    13.311]     YResolution: 768
[    13.311]     XCharSize: 8
[    13.311]     YCharSize: 16
[    13.311]     NumberOfPlanes: 1
[    13.311]     BitsPerPixel: 8
[    13.311]     NumberOfBanks: 1
[    13.311]     MemoryModel: 4
[    13.311]     BankSize: 0
[    13.311]     NumberOfImages: 18
[    13.311]     RedMaskSize: 0
[    13.311]     RedFieldPosition: 0
[    13.311]     GreenMaskSize: 0
[    13.311]     GreenFieldPosition: 0
[    13.311]     BlueMaskSize: 0
[    13.311]     BlueFieldPosition: 0
[    13.311]     RsvdMaskSize: 0
[    13.311]     RsvdFieldPosition: 0
[    13.311]     DirectColorModeInfo: 0
[    13.311]     PhysBasePtr: 0x80000000
[    13.311]     LinBytesPerScanLine: 1024
[    13.311]     BnkNumberOfImagePages: 18
[    13.311]     LinNumberOfImagePages: 18
[    13.311]     LinRedMaskSize: 0
[    13.311]     LinRedFieldPosition: 0
[    13.311]     LinGreenMaskSize: 0
[    13.311]     LinGreenFieldPosition: 0
[    13.311]     LinBlueMaskSize: 0
[    13.311]     LinBlueFieldPosition: 0
[    13.312]     LinRsvdMaskSize: 0
[    13.312]     LinRsvdFieldPosition: 0
[    13.312]     MaxPixelClock: 400000000
[    13.313] Mode: 107 (1280x1024)
[    13.313]     ModeAttributes: 0xba
[    13.313]     WinAAttributes: 0x7
[    13.313]     WinBAttributes: 0x0
[    13.313]     WinGranularity: 64
[    13.313]     WinSize: 64
[    13.313]     WinASegment: 0xa000
[    13.313]     WinBSegment: 0x0
[    13.313]     WinFuncPtr: 0xc0005543
[    13.313]     BytesPerScanline: 1280
[    13.313]     XResolution: 1280
[    13.313]     YResolution: 1024
[    13.313]     XCharSize: 8
[    13.313]     YCharSize: 16
[    13.313]     NumberOfPlanes: 1
[    13.313]     BitsPerPixel: 8
[    13.313]     NumberOfBanks: 1
[    13.313]     MemoryModel: 4
[    13.313]     BankSize: 0
[    13.313]     NumberOfImages: 11
[    13.313]     RedMaskSize: 0
[    13.313]     RedFieldPosition: 0
[    13.313]     GreenMaskSize: 0
[    13.313]     GreenFieldPosition: 0
[    13.313]     BlueMaskSize: 0
[    13.313]     BlueFieldPosition: 0
[    13.313]     RsvdMaskSize: 0
[    13.313]     RsvdFieldPosition: 0
[    13.313]     DirectColorModeInfo: 0
[    13.313]     PhysBasePtr: 0x80000000
[    13.313]     LinBytesPerScanLine: 1280
[    13.313]     BnkNumberOfImagePages: 11
[    13.313]     LinNumberOfImagePages: 11
[    13.313]     LinRedMaskSize: 0
[    13.313]     LinRedFieldPosition: 0
[    13.313]     LinGreenMaskSize: 0
[    13.313]     LinGreenFieldPosition: 0
[    13.313]     LinBlueMaskSize: 0
[    13.313]     LinBlueFieldPosition: 0
[    13.313]     LinRsvdMaskSize: 0
[    13.313]     LinRsvdFieldPosition: 0
[    13.313]     MaxPixelClock: 400000000
[    13.315] Mode: 110 (640x480)
[    13.315]     ModeAttributes: 0xbb
[    13.315]     WinAAttributes: 0x7
[    13.315]     WinBAttributes: 0x0
[    13.315]     WinGranularity: 64
[    13.315]     WinSize: 64
[    13.315]     WinASegment: 0xa000
[    13.315]     WinBSegment: 0x0
[    13.315]     WinFuncPtr: 0xc0005543
[    13.315]     BytesPerScanline: 1280
[    13.315]     XResolution: 640
[    13.315]     YResolution: 480
[    13.315]     XCharSize: 8
[    13.315]     YCharSize: 16
[    13.315]     NumberOfPlanes: 1
[    13.315]     BitsPerPixel: 16
[    13.315]     NumberOfBanks: 1
[    13.315]     MemoryModel: 6
[    13.315]     BankSize: 0
[    13.315]     NumberOfImages: 24
[    13.315]     RedMaskSize: 5
[    13.315]     RedFieldPosition: 10
[    13.315]     GreenMaskSize: 5
[    13.315]     GreenFieldPosition: 5
[    13.315]     BlueMaskSize: 5
[    13.315]     BlueFieldPosition: 0
[    13.315]     RsvdMaskSize: 0
[    13.315]     RsvdFieldPosition: 0
[    13.315]     DirectColorModeInfo: 0
[    13.315]     PhysBasePtr: 0x80000000
[    13.315]     LinBytesPerScanLine: 1280
[    13.315]     BnkNumberOfImagePages: 24
[    13.315]     LinNumberOfImagePages: 24
[    13.315]     LinRedMaskSize: 5
[    13.315]     LinRedFieldPosition: 10
[    13.315]     LinGreenMaskSize: 5
[    13.315]     LinGreenFieldPosition: 5
[    13.315]     LinBlueMaskSize: 5
[    13.315]     LinBlueFieldPosition: 0
[    13.315]     LinRsvdMaskSize: 0
[    13.315]     LinRsvdFieldPosition: 0
[    13.315]     MaxPixelClock: 400000000
[    13.316] Mode: 111 (640x480)
[    13.316]     ModeAttributes: 0xbb
[    13.316]     WinAAttributes: 0x7
[    13.316]     WinBAttributes: 0x0
[    13.316]     WinGranularity: 64
[    13.316]     WinSize: 64
[    13.316]     WinASegment: 0xa000
[    13.316]     WinBSegment: 0x0
[    13.316]     WinFuncPtr: 0xc0005543
[    13.316]     BytesPerScanline: 1280
[    13.316]     XResolution: 640
[    13.316]     YResolution: 480
[    13.316]     XCharSize: 8
[    13.317]     YCharSize: 16
[    13.317]     NumberOfPlanes: 1
[    13.317]     BitsPerPixel: 16
[    13.317]     NumberOfBanks: 1
[    13.317]     MemoryModel: 6
[    13.317]     BankSize: 0
[    13.317]     NumberOfImages: 24
[    13.317]     RedMaskSize: 5
[    13.317]     RedFieldPosition: 11
[    13.317]     GreenMaskSize: 6
[    13.317]     GreenFieldPosition: 5
[    13.317]     BlueMaskSize: 5
[    13.317]     BlueFieldPosition: 0
[    13.317]     RsvdMaskSize: 0
[    13.317]     RsvdFieldPosition: 0
[    13.317]     DirectColorModeInfo: 0
[    13.317]     PhysBasePtr: 0x80000000
[    13.317]     LinBytesPerScanLine: 1280
[    13.317]     BnkNumberOfImagePages: 24
[    13.317]     LinNumberOfImagePages: 24
[    13.317]     LinRedMaskSize: 5
[    13.317]     LinRedFieldPosition: 11
[    13.317]     LinGreenMaskSize: 6
[    13.317]     LinGreenFieldPosition: 5
[    13.317]     LinBlueMaskSize: 5
[    13.317]     LinBlueFieldPosition: 0
[    13.317]     LinRsvdMaskSize: 0
[    13.317]     LinRsvdFieldPosition: 0
[    13.317]     MaxPixelClock: 400000000
[    13.318] Mode: 113 (800x600)
[    13.318]     ModeAttributes: 0xbb
[    13.318]     WinAAttributes: 0x7
[    13.318]     WinBAttributes: 0x0
[    13.318]     WinGranularity: 64
[    13.318]     WinSize: 64
[    13.318]     WinASegment: 0xa000
[    13.318]     WinBSegment: 0x0
[    13.318]     WinFuncPtr: 0xc0005543
[    13.318]     BytesPerScanline: 1600
[    13.318]     XResolution: 800
[    13.318]     YResolution: 600
[    13.318]     XCharSize: 8
[    13.318]     YCharSize: 14
[    13.318]     NumberOfPlanes: 1
[    13.318]     BitsPerPixel: 16
[    13.318]     NumberOfBanks: 1
[    13.318]     MemoryModel: 6
[    13.318]     BankSize: 0
[    13.318]     NumberOfImages: 16
[    13.318]     RedMaskSize: 5
[    13.318]     RedFieldPosition: 10
[    13.318]     GreenMaskSize: 5
[    13.318]     GreenFieldPosition: 5
[    13.318]     BlueMaskSize: 5
[    13.318]     BlueFieldPosition: 0
[    13.318]     RsvdMaskSize: 0
[    13.319]     RsvdFieldPosition: 0
[    13.319]     DirectColorModeInfo: 0
[    13.319]     PhysBasePtr: 0x80000000
[    13.319]     LinBytesPerScanLine: 1600
[    13.319]     BnkNumberOfImagePages: 16
[    13.319]     LinNumberOfImagePages: 16
[    13.319]     LinRedMaskSize: 5
[    13.319]     LinRedFieldPosition: 10
[    13.319]     LinGreenMaskSize: 5
[    13.319]     LinGreenFieldPosition: 5
[    13.319]     LinBlueMaskSize: 5
[    13.319]     LinBlueFieldPosition: 0
[    13.319]     LinRsvdMaskSize: 0
[    13.319]     LinRsvdFieldPosition: 0
[    13.319]     MaxPixelClock: 400000000
[    13.320] Mode: 114 (800x600)
[    13.320]     ModeAttributes: 0xbb
[    13.320]     WinAAttributes: 0x7
[    13.320]     WinBAttributes: 0x0
[    13.320]     WinGranularity: 64
[    13.320]     WinSize: 64
[    13.320]     WinASegment: 0xa000
[    13.320]     WinBSegment: 0x0
[    13.320]     WinFuncPtr: 0xc0005543
[    13.320]     BytesPerScanline: 1600
[    13.320]     XResolution: 800
[    13.320]     YResolution: 600
[    13.320]     XCharSize: 8
[    13.320]     YCharSize: 14
[    13.320]     NumberOfPlanes: 1
[    13.320]     BitsPerPixel: 16
[    13.320]     NumberOfBanks: 1
[    13.320]     MemoryModel: 6
[    13.320]     BankSize: 0
[    13.320]     NumberOfImages: 16
[    13.320]     RedMaskSize: 5
[    13.320]     RedFieldPosition: 11
[    13.320]     GreenMaskSize: 6
[    13.320]     GreenFieldPosition: 5
[    13.320]     BlueMaskSize: 5
[    13.320]     BlueFieldPosition: 0
[    13.320]     RsvdMaskSize: 0
[    13.320]     RsvdFieldPosition: 0
[    13.320]     DirectColorModeInfo: 0
[    13.320]     PhysBasePtr: 0x80000000
[    13.320]     LinBytesPerScanLine: 1600
[    13.320]     BnkNumberOfImagePages: 16
[    13.320]     LinNumberOfImagePages: 16
[    13.320]     LinRedMaskSize: 5
[    13.320]     LinRedFieldPosition: 11
[    13.320]     LinGreenMaskSize: 6
[    13.320]     LinGreenFieldPosition: 5
[    13.320]     LinBlueMaskSize: 5
[    13.320]     LinBlueFieldPosition: 0
[    13.320]     LinRsvdMaskSize: 0
[    13.321]     LinRsvdFieldPosition: 0
[    13.321]     MaxPixelClock: 400000000
[    13.322] Mode: 116 (1024x768)
[    13.322]     ModeAttributes: 0xbb
[    13.322]     WinAAttributes: 0x7
[    13.322]     WinBAttributes: 0x0
[    13.322]     WinGranularity: 64
[    13.322]     WinSize: 64
[    13.322]     WinASegment: 0xa000
[    13.322]     WinBSegment: 0x0
[    13.322]     WinFuncPtr: 0xc0005543
[    13.322]     BytesPerScanline: 2048
[    13.322]     XResolution: 1024
[    13.322]     YResolution: 768
[    13.322]     XCharSize: 8
[    13.322]     YCharSize: 16
[    13.322]     NumberOfPlanes: 1
[    13.322]     BitsPerPixel: 16
[    13.322]     NumberOfBanks: 1
[    13.322]     MemoryModel: 6
[    13.322]     BankSize: 0
[    13.322]     NumberOfImages: 9
[    13.322]     RedMaskSize: 5
[    13.322]     RedFieldPosition: 10
[    13.322]     GreenMaskSize: 5
[    13.322]     GreenFieldPosition: 5
[    13.322]     BlueMaskSize: 5
[    13.322]     BlueFieldPosition: 0
[    13.322]     RsvdMaskSize: 0
[    13.322]     RsvdFieldPosition: 0
[    13.322]     DirectColorModeInfo: 0
[    13.322]     PhysBasePtr: 0x80000000
[    13.322]     LinBytesPerScanLine: 2048
[    13.322]     BnkNumberOfImagePages: 9
[    13.322]     LinNumberOfImagePages: 9
[    13.322]     LinRedMaskSize: 5
[    13.322]     LinRedFieldPosition: 10
[    13.322]     LinGreenMaskSize: 5
[    13.322]     LinGreenFieldPosition: 5
[    13.322]     LinBlueMaskSize: 5
[    13.322]     LinBlueFieldPosition: 0
[    13.322]     LinRsvdMaskSize: 0
[    13.322]     LinRsvdFieldPosition: 0
[    13.322]     MaxPixelClock: 400000000
[    13.324] Mode: 117 (1024x768)
[    13.324]     ModeAttributes: 0xbb
[    13.324]     WinAAttributes: 0x7
[    13.324]     WinBAttributes: 0x0
[    13.324]     WinGranularity: 64
[    13.324]     WinSize: 64
[    13.324]     WinASegment: 0xa000
[    13.324]     WinBSegment: 0x0
[    13.324]     WinFuncPtr: 0xc0005543
[    13.324]     BytesPerScanline: 2048
[    13.324]     XResolution: 1024
[    13.324]     YResolution: 768
[    13.324]     XCharSize: 8
[    13.324]     YCharSize: 16
[    13.324]     NumberOfPlanes: 1
[    13.324]     BitsPerPixel: 16
[    13.324]     NumberOfBanks: 1
[    13.324]     MemoryModel: 6
[    13.324]     BankSize: 0
[    13.324]     NumberOfImages: 9
[    13.324]     RedMaskSize: 5
[    13.324]     RedFieldPosition: 11
[    13.324]     GreenMaskSize: 6
[    13.324]     GreenFieldPosition: 5
[    13.324]     BlueMaskSize: 5
[    13.324]     BlueFieldPosition: 0
[    13.324]     RsvdMaskSize: 0
[    13.324]     RsvdFieldPosition: 0
[    13.324]     DirectColorModeInfo: 0
[    13.324]     PhysBasePtr: 0x80000000
[    13.324]     LinBytesPerScanLine: 2048
[    13.324]     BnkNumberOfImagePages: 9
[    13.324]     LinNumberOfImagePages: 9
[    13.324]     LinRedMaskSize: 5
[    13.324]     LinRedFieldPosition: 11
[    13.324]     LinGreenMaskSize: 6
[    13.324]     LinGreenFieldPosition: 5
[    13.324]     LinBlueMaskSize: 5
[    13.324]     LinBlueFieldPosition: 0
[    13.324]     LinRsvdMaskSize: 0
[    13.324]     LinRsvdFieldPosition: 0
[    13.324]     MaxPixelClock: 400000000
[    13.325] Mode: 119 (1280x1024)
[    13.326]     ModeAttributes: 0xba
[    13.326]     WinAAttributes: 0x7
[    13.326]     WinBAttributes: 0x0
[    13.326]     WinGranularity: 64
[    13.326]     WinSize: 64
[    13.326]     WinASegment: 0xa000
[    13.326]     WinBSegment: 0x0
[    13.326]     WinFuncPtr: 0xc0005543
[    13.326]     BytesPerScanline: 2560
[    13.326]     XResolution: 1280
[    13.326]     YResolution: 1024
[    13.326]     XCharSize: 8
[    13.326]     YCharSize: 16
[    13.326]     NumberOfPlanes: 1
[    13.326]     BitsPerPixel: 16
[    13.326]     NumberOfBanks: 1
[    13.326]     MemoryModel: 6
[    13.326]     BankSize: 0
[    13.326]     NumberOfImages: 5
[    13.326]     RedMaskSize: 5
[    13.326]     RedFieldPosition: 10
[    13.326]     GreenMaskSize: 5
[    13.326]     GreenFieldPosition: 5
[    13.326]     BlueMaskSize: 5
[    13.326]     BlueFieldPosition: 0
[    13.326]     RsvdMaskSize: 0
[    13.326]     RsvdFieldPosition: 0
[    13.326]     DirectColorModeInfo: 0
[    13.326]     PhysBasePtr: 0x80000000
[    13.326]     LinBytesPerScanLine: 2560
[    13.326]     BnkNumberOfImagePages: 5
[    13.326]     LinNumberOfImagePages: 5
[    13.326]     LinRedMaskSize: 5
[    13.326]     LinRedFieldPosition: 10
[    13.326]     LinGreenMaskSize: 5
[    13.326]     LinGreenFieldPosition: 5
[    13.326]     LinBlueMaskSize: 5
[    13.326]     LinBlueFieldPosition: 0
[    13.326]     LinRsvdMaskSize: 0
[    13.326]     LinRsvdFieldPosition: 0
[    13.326]     MaxPixelClock: 400000000
[    13.327] Mode: 11a (1280x1024)
[    13.327]     ModeAttributes: 0xba
[    13.327]     WinAAttributes: 0x7
[    13.327]     WinBAttributes: 0x0
[    13.327]     WinGranularity: 64
[    13.328]     WinSize: 64
[    13.328]     WinASegment: 0xa000
[    13.328]     WinBSegment: 0x0
[    13.328]     WinFuncPtr: 0xc0005543
[    13.328]     BytesPerScanline: 2560
[    13.328]     XResolution: 1280
[    13.328]     YResolution: 1024
[    13.328]     XCharSize: 8
[    13.328]     YCharSize: 16
[    13.328]     NumberOfPlanes: 1
[    13.328]     BitsPerPixel: 16
[    13.328]     NumberOfBanks: 1
[    13.328]     MemoryModel: 6
[    13.328]     BankSize: 0
[    13.328]     NumberOfImages: 5
[    13.328]     RedMaskSize: 5
[    13.328]     RedFieldPosition: 11
[    13.328]     GreenMaskSize: 6
[    13.328]     GreenFieldPosition: 5
[    13.328]     BlueMaskSize: 5
[    13.328]     BlueFieldPosition: 0
[    13.328]     RsvdMaskSize: 0
[    13.328]     RsvdFieldPosition: 0
[    13.328]     DirectColorModeInfo: 0
[    13.328]     PhysBasePtr: 0x80000000
[    13.328]     LinBytesPerScanLine: 2560
[    13.328]     BnkNumberOfImagePages: 5
[    13.328]     LinNumberOfImagePages: 5
[    13.328]     LinRedMaskSize: 5
[    13.328]     LinRedFieldPosition: 11
[    13.328]     LinGreenMaskSize: 6
[    13.328]     LinGreenFieldPosition: 5
[    13.328]     LinBlueMaskSize: 5
[    13.328]     LinBlueFieldPosition: 0
[    13.328]     LinRsvdMaskSize: 0
[    13.328]     LinRsvdFieldPosition: 0
[    13.328]     MaxPixelClock: 400000000
[    13.329] Mode: 10d (320x200)
[    13.329]     ModeAttributes: 0xbb
[    13.329]     WinAAttributes: 0x7
[    13.329]     WinBAttributes: 0x0
[    13.329]     WinGranularity: 64
[    13.329]     WinSize: 64
[    13.329]     WinASegment: 0xa000
[    13.329]     WinBSegment: 0x0
[    13.329]     WinFuncPtr: 0xc0005543
[    13.329]     BytesPerScanline: 640
[    13.329]     XResolution: 320
[    13.329]     YResolution: 200
[    13.329]     XCharSize: 8
[    13.329]     YCharSize: 8
[    13.329]     NumberOfPlanes: 1
[    13.329]     BitsPerPixel: 16
[    13.330]     NumberOfBanks: 1
[    13.330]     MemoryModel: 6
[    13.330]     BankSize: 0
[    13.330]     NumberOfImages: 127
[    13.330]     RedMaskSize: 5
[    13.330]     RedFieldPosition: 10
[    13.330]     GreenMaskSize: 5
[    13.330]     GreenFieldPosition: 5
[    13.330]     BlueMaskSize: 5
[    13.330]     BlueFieldPosition: 0
[    13.330]     RsvdMaskSize: 0
[    13.330]     RsvdFieldPosition: 0
[    13.330]     DirectColorModeInfo: 0
[    13.330]     PhysBasePtr: 0x80000000
[    13.330]     LinBytesPerScanLine: 640
[    13.330]     BnkNumberOfImagePages: 127
[    13.330]     LinNumberOfImagePages: 127
[    13.330]     LinRedMaskSize: 5
[    13.330]     LinRedFieldPosition: 10
[    13.330]     LinGreenMaskSize: 5
[    13.330]     LinGreenFieldPosition: 5
[    13.330]     LinBlueMaskSize: 5
[    13.330]     LinBlueFieldPosition: 0
[    13.330]     LinRsvdMaskSize: 0
[    13.330]     LinRsvdFieldPosition: 0
[    13.330]     MaxPixelClock: 400000000
[    13.331] Mode: 10e (320x200)
[    13.331]     ModeAttributes: 0xbb
[    13.331]     WinAAttributes: 0x7
[    13.331]     WinBAttributes: 0x0
[    13.331]     WinGranularity: 64
[    13.331]     WinSize: 64
[    13.331]     WinASegment: 0xa000
[    13.331]     WinBSegment: 0x0
[    13.331]     WinFuncPtr: 0xc0005543
[    13.331]     BytesPerScanline: 640
[    13.331]     XResolution: 320
[    13.331]     YResolution: 200
[    13.331]     XCharSize: 8
[    13.331]     YCharSize: 8
[    13.331]     NumberOfPlanes: 1
[    13.331]     BitsPerPixel: 16
[    13.331]     NumberOfBanks: 1
[    13.331]     MemoryModel: 6
[    13.331]     BankSize: 0
[    13.331]     NumberOfImages: 127
[    13.331]     RedMaskSize: 5
[    13.331]     RedFieldPosition: 11
[    13.331]     GreenMaskSize: 6
[    13.331]     GreenFieldPosition: 5
[    13.331]     BlueMaskSize: 5
[    13.331]     BlueFieldPosition: 0
[    13.331]     RsvdMaskSize: 0
[    13.331]     RsvdFieldPosition: 0
[    13.331]     DirectColorModeInfo: 0
[    13.332]     PhysBasePtr: 0x80000000
[    13.332]     LinBytesPerScanLine: 640
[    13.332]     BnkNumberOfImagePages: 127
[    13.332]     LinNumberOfImagePages: 127
[    13.332]     LinRedMaskSize: 5
[    13.332]     LinRedFieldPosition: 11
[    13.332]     LinGreenMaskSize: 6
[    13.332]     LinGreenFieldPosition: 5
[    13.332]     LinBlueMaskSize: 5
[    13.332]     LinBlueFieldPosition: 0
[    13.332]     LinRsvdMaskSize: 0
[    13.332]     LinRsvdFieldPosition: 0
[    13.332]     MaxPixelClock: 400000000
[    13.333] *Mode: 120 (320x200)
[    13.333]     ModeAttributes: 0xbb
[    13.333]     WinAAttributes: 0x7
[    13.333]     WinBAttributes: 0x0
[    13.333]     WinGranularity: 64
[    13.333]     WinSize: 64
[    13.333]     WinASegment: 0xa000
[    13.333]     WinBSegment: 0x0
[    13.333]     WinFuncPtr: 0xc0005543
[    13.333]     BytesPerScanline: 1280
[    13.333]     XResolution: 320
[    13.333]     YResolution: 200
[    13.333]     XCharSize: 8
[    13.333]     YCharSize: 8
[    13.333]     NumberOfPlanes: 1
[    13.333]     BitsPerPixel: 32
[    13.333]     NumberOfBanks: 1
[    13.333]     MemoryModel: 6
[    13.333]     BankSize: 0
[    13.333]     NumberOfImages: 63
[    13.333]     RedMaskSize: 8
[    13.333]     RedFieldPosition: 16
[    13.333]     GreenMaskSize: 8
[    13.333]     GreenFieldPosition: 8
[    13.333]     BlueMaskSize: 8
[    13.333]     BlueFieldPosition: 0
[    13.333]     RsvdMaskSize: 0
[    13.333]     RsvdFieldPosition: 0
[    13.333]     DirectColorModeInfo: 0
[    13.333]     PhysBasePtr: 0x80000000
[    13.333]     LinBytesPerScanLine: 1280
[    13.333]     BnkNumberOfImagePages: 63
[    13.333]     LinNumberOfImagePages: 63
[    13.333]     LinRedMaskSize: 8
[    13.333]     LinRedFieldPosition: 16
[    13.333]     LinGreenMaskSize: 8
[    13.333]     LinGreenFieldPosition: 8
[    13.333]     LinBlueMaskSize: 8
[    13.333]     LinBlueFieldPosition: 0
[    13.333]     LinRsvdMaskSize: 0
[    13.333]     LinRsvdFieldPosition: 0
[    13.333]     MaxPixelClock: 400000000
[    13.335] Mode: 193 (320x240)
[    13.335]     ModeAttributes: 0xbb
[    13.335]     WinAAttributes: 0x7
[    13.335]     WinBAttributes: 0x0
[    13.335]     WinGranularity: 64
[    13.335]     WinSize: 64
[    13.335]     WinASegment: 0xa000
[    13.335]     WinBSegment: 0x0
[    13.335]     WinFuncPtr: 0xc0005543
[    13.335]     BytesPerScanline: 320
[    13.335]     XResolution: 320
[    13.335]     YResolution: 240
[    13.335]     XCharSize: 8
[    13.335]     YCharSize: 8
[    13.335]     NumberOfPlanes: 1
[    13.335]     BitsPerPixel: 8
[    13.335]     NumberOfBanks: 1
[    13.335]     MemoryModel: 4
[    13.335]     BankSize: 0
[    13.335]     NumberOfImages: 127
[    13.335]     RedMaskSize: 0
[    13.335]     RedFieldPosition: 0
[    13.335]     GreenMaskSize: 0
[    13.335]     GreenFieldPosition: 0
[    13.335]     BlueMaskSize: 0
[    13.335]     BlueFieldPosition: 0
[    13.335]     RsvdMaskSize: 0
[    13.335]     RsvdFieldPosition: 0
[    13.335]     DirectColorModeInfo: 0
[    13.335]     PhysBasePtr: 0x80000000
[    13.335]     LinBytesPerScanLine: 320
[    13.335]     BnkNumberOfImagePages: 127
[    13.335]     LinNumberOfImagePages: 127
[    13.335]     LinRedMaskSize: 0
[    13.335]     LinRedFieldPosition: 0
[    13.335]     LinGreenMaskSize: 0
[    13.335]     LinGreenFieldPosition: 0
[    13.335]     LinBlueMaskSize: 0
[    13.335]     LinBlueFieldPosition: 0
[    13.335]     LinRsvdMaskSize: 0
[    13.335]     LinRsvdFieldPosition: 0
[    13.335]     MaxPixelClock: 400000000
[    13.337] Mode: 195 (320x240)
[    13.337]     ModeAttributes: 0xbb
[    13.337]     WinAAttributes: 0x7
[    13.337]     WinBAttributes: 0x0
[    13.337]     WinGranularity: 64
[    13.337]     WinSize: 64
[    13.337]     WinASegment: 0xa000
[    13.337]     WinBSegment: 0x0
[    13.337]     WinFuncPtr: 0xc0005543
[    13.337]     BytesPerScanline: 640
[    13.337]     XResolution: 320
[    13.337]     YResolution: 240
[    13.337]     XCharSize: 8
[    13.337]     YCharSize: 8
[    13.337]     NumberOfPlanes: 1
[    13.337]     BitsPerPixel: 16
[    13.337]     NumberOfBanks: 1
[    13.337]     MemoryModel: 6
[    13.337]     BankSize: 0
[    13.337]     NumberOfImages: 84
[    13.337]     RedMaskSize: 5
[    13.337]     RedFieldPosition: 11
[    13.337]     GreenMaskSize: 6
[    13.337]     GreenFieldPosition: 5
[    13.337]     BlueMaskSize: 5
[    13.337]     BlueFieldPosition: 0
[    13.337]     RsvdMaskSize: 0
[    13.337]     RsvdFieldPosition: 0
[    13.337]     DirectColorModeInfo: 0
[    13.337]     PhysBasePtr: 0x80000000
[    13.337]     LinBytesPerScanLine: 640
[    13.337]     BnkNumberOfImagePages: 84
[    13.337]     LinNumberOfImagePages: 84
[    13.337]     LinRedMaskSize: 5
[    13.337]     LinRedFieldPosition: 11
[    13.337]     LinGreenMaskSize: 6
[    13.337]     LinGreenFieldPosition: 5
[    13.337]     LinBlueMaskSize: 5
[    13.337]     LinBlueFieldPosition: 0
[    13.337]     LinRsvdMaskSize: 0
[    13.337]     LinRsvdFieldPosition: 0
[    13.337]     MaxPixelClock: 400000000
[    13.338] *Mode: 196 (320x240)
[    13.338]     ModeAttributes: 0xbb
[    13.338]     WinAAttributes: 0x7
[    13.338]     WinBAttributes: 0x0
[    13.338]     WinGranularity: 64
[    13.338]     WinSize: 64
[    13.338]     WinASegment: 0xa000
[    13.339]     WinBSegment: 0x0
[    13.339]     WinFuncPtr: 0xc0005543
[    13.339]     BytesPerScanline: 1280
[    13.339]     XResolution: 320
[    13.339]     YResolution: 240
[    13.339]     XCharSize: 8
[    13.339]     YCharSize: 8
[    13.339]     NumberOfPlanes: 1
[    13.339]     BitsPerPixel: 32
[    13.339]     NumberOfBanks: 1
[    13.339]     MemoryModel: 6
[    13.339]     BankSize: 0
[    13.339]     NumberOfImages: 50
[    13.339]     RedMaskSize: 8
[    13.339]     RedFieldPosition: 16
[    13.339]     GreenMaskSize: 8
[    13.339]     GreenFieldPosition: 8
[    13.339]     BlueMaskSize: 8
[    13.339]     BlueFieldPosition: 0
[    13.339]     RsvdMaskSize: 0
[    13.339]     RsvdFieldPosition: 0
[    13.339]     DirectColorModeInfo: 0
[    13.339]     PhysBasePtr: 0x80000000
[    13.339]     LinBytesPerScanLine: 1280
[    13.339]     BnkNumberOfImagePages: 50
[    13.339]     LinNumberOfImagePages: 50
[    13.339]     LinRedMaskSize: 8
[    13.339]     LinRedFieldPosition: 16
[    13.339]     LinGreenMaskSize: 8
[    13.339]     LinGreenFieldPosition: 8
[    13.339]     LinBlueMaskSize: 8
[    13.339]     LinBlueFieldPosition: 0
[    13.339]     LinRsvdMaskSize: 0
[    13.339]     LinRsvdFieldPosition: 0
[    13.339]     MaxPixelClock: 400000000
[    13.340] Mode: 1b3 (512x384)
[    13.340]     ModeAttributes: 0xbb
[    13.340]     WinAAttributes: 0x7
[    13.340]     WinBAttributes: 0x0
[    13.340]     WinGranularity: 64
[    13.340]     WinSize: 64
[    13.340]     WinASegment: 0xa000
[    13.340]     WinBSegment: 0x0
[    13.340]     WinFuncPtr: 0xc0005543
[    13.340]     BytesPerScanline: 512
[    13.340]     XResolution: 512
[    13.340]     YResolution: 384
[    13.340]     XCharSize: 8
[    13.340]     YCharSize: 16
[    13.340]     NumberOfPlanes: 1
[    13.340]     BitsPerPixel: 8
[    13.341]     NumberOfBanks: 1
[    13.341]     MemoryModel: 4
[    13.341]     BankSize: 0
[    13.341]     NumberOfImages: 63
[    13.341]     RedMaskSize: 0
[    13.341]     RedFieldPosition: 0
[    13.341]     GreenMaskSize: 0
[    13.341]     GreenFieldPosition: 0
[    13.341]     BlueMaskSize: 0
[    13.341]     BlueFieldPosition: 0
[    13.341]     RsvdMaskSize: 0
[    13.341]     RsvdFieldPosition: 0
[    13.341]     DirectColorModeInfo: 0
[    13.341]     PhysBasePtr: 0x80000000
[    13.341]     LinBytesPerScanLine: 512
[    13.341]     BnkNumberOfImagePages: 63
[    13.341]     LinNumberOfImagePages: 63
[    13.341]     LinRedMaskSize: 0
[    13.341]     LinRedFieldPosition: 0
[    13.341]     LinGreenMaskSize: 0
[    13.341]     LinGreenFieldPosition: 0
[    13.341]     LinBlueMaskSize: 0
[    13.341]     LinBlueFieldPosition: 0
[    13.341]     LinRsvdMaskSize: 0
[    13.341]     LinRsvdFieldPosition: 0
[    13.341]     MaxPixelClock: 400000000
[    13.342] Mode: 1b5 (512x384)
[    13.342]     ModeAttributes: 0xbb
[    13.342]     WinAAttributes: 0x7
[    13.342]     WinBAttributes: 0x0
[    13.342]     WinGranularity: 64
[    13.342]     WinSize: 64
[    13.342]     WinASegment: 0xa000
[    13.342]     WinBSegment: 0x0
[    13.342]     WinFuncPtr: 0xc0005543
[    13.342]     BytesPerScanline: 1024
[    13.342]     XResolution: 512
[    13.342]     YResolution: 384
[    13.342]     XCharSize: 8
[    13.342]     YCharSize: 16
[    13.342]     NumberOfPlanes: 1
[    13.342]     BitsPerPixel: 16
[    13.342]     NumberOfBanks: 1
[    13.342]     MemoryModel: 6
[    13.342]     BankSize: 0
[    13.343]     NumberOfImages: 35
[    13.343]     RedMaskSize: 5
[    13.343]     RedFieldPosition: 11
[    13.343]     GreenMaskSize: 6
[    13.343]     GreenFieldPosition: 5
[    13.343]     BlueMaskSize: 5
[    13.343]     BlueFieldPosition: 0
[    13.343]     RsvdMaskSize: 0
[    13.343]     RsvdFieldPosition: 0
[    13.343]     DirectColorModeInfo: 0
[    13.343]     PhysBasePtr: 0x80000000
[    13.343]     LinBytesPerScanLine: 1024
[    13.343]     BnkNumberOfImagePages: 35
[    13.343]     LinNumberOfImagePages: 35
[    13.343]     LinRedMaskSize: 5
[    13.343]     LinRedFieldPosition: 11
[    13.343]     LinGreenMaskSize: 6
[    13.343]     LinGreenFieldPosition: 5
[    13.343]     LinBlueMaskSize: 5
[    13.343]     LinBlueFieldPosition: 0
[    13.343]     LinRsvdMaskSize: 0
[    13.343]     LinRsvdFieldPosition: 0
[    13.343]     MaxPixelClock: 400000000
[    13.344] *Mode: 1b6 (512x384)
[    13.344]     ModeAttributes: 0xbb
[    13.344]     WinAAttributes: 0x7
[    13.344]     WinBAttributes: 0x0
[    13.344]     WinGranularity: 64
[    13.344]     WinSize: 64
[    13.344]     WinASegment: 0xa000
[    13.344]     WinBSegment: 0x0
[    13.344]     WinFuncPtr: 0xc0005543
[    13.344]     BytesPerScanline: 2048
[    13.344]     XResolution: 512
[    13.344]     YResolution: 384
[    13.344]     XCharSize: 8
[    13.344]     YCharSize: 16
[    13.344]     NumberOfPlanes: 1
[    13.344]     BitsPerPixel: 32
[    13.344]     NumberOfBanks: 1
[    13.344]     MemoryModel: 6
[    13.344]     BankSize: 0
[    13.344]     NumberOfImages: 18
[    13.344]     RedMaskSize: 8
[    13.345]     RedFieldPosition: 16
[    13.345]     GreenMaskSize: 8
[    13.345]     GreenFieldPosition: 8
[    13.345]     BlueMaskSize: 8
[    13.345]     BlueFieldPosition: 0
[    13.345]     RsvdMaskSize: 0
[    13.345]     RsvdFieldPosition: 0
[    13.345]     DirectColorModeInfo: 0
[    13.345]     PhysBasePtr: 0x80000000
[    13.345]     LinBytesPerScanLine: 2048
[    13.345]     BnkNumberOfImagePages: 18
[    13.345]     LinNumberOfImagePages: 18
[    13.345]     LinRedMaskSize: 8
[    13.345]     LinRedFieldPosition: 16
[    13.345]     LinGreenMaskSize: 8
[    13.345]     LinGreenFieldPosition: 8
[    13.345]     LinBlueMaskSize: 8
[    13.345]     LinBlueFieldPosition: 0
[    13.345]     LinRsvdMaskSize: 0
[    13.345]     LinRsvdFieldPosition: 0
[    13.345]     MaxPixelClock: 400000000
[    13.346] Mode: 1c3 (640x350)
[    13.346]     ModeAttributes: 0xbb
[    13.346]     WinAAttributes: 0x7
[    13.346]     WinBAttributes: 0x0
[    13.346]     WinGranularity: 64
[    13.346]     WinSize: 64
[    13.346]     WinASegment: 0xa000
[    13.346]     WinBSegment: 0x0
[    13.346]     WinFuncPtr: 0xc0005543
[    13.346]     BytesPerScanline: 640
[    13.346]     XResolution: 640
[    13.346]     YResolution: 350
[    13.346]     XCharSize: 8
[    13.346]     YCharSize: 14
[    13.346]     NumberOfPlanes: 1
[    13.346]     BitsPerPixel: 8
[    13.346]     NumberOfBanks: 1
[    13.346]     MemoryModel: 4
[    13.346]     BankSize: 0
[    13.346]     NumberOfImages: 63
[    13.346]     RedMaskSize: 0
[    13.346]     RedFieldPosition: 0
[    13.346]     GreenMaskSize: 0
[    13.346]     GreenFieldPosition: 0
[    13.346]     BlueMaskSize: 0
[    13.346]     BlueFieldPosition: 0
[    13.346]     RsvdMaskSize: 0
[    13.346]     RsvdFieldPosition: 0
[    13.346]     DirectColorModeInfo: 0
[    13.346]     PhysBasePtr: 0x80000000
[    13.347]     LinBytesPerScanLine: 640
[    13.347]     BnkNumberOfImagePages: 63
[    13.347]     LinNumberOfImagePages: 63
[    13.347]     LinRedMaskSize: 0
[    13.347]     LinRedFieldPosition: 0
[    13.347]     LinGreenMaskSize: 0
[    13.347]     LinGreenFieldPosition: 0
[    13.347]     LinBlueMaskSize: 0
[    13.347]     LinBlueFieldPosition: 0
[    13.347]     LinRsvdMaskSize: 0
[    13.347]     LinRsvdFieldPosition: 0
[    13.347]     MaxPixelClock: 400000000
[    13.348] Mode: 1c5 (640x350)
[    13.348]     ModeAttributes: 0xbb
[    13.348]     WinAAttributes: 0x7
[    13.348]     WinBAttributes: 0x0
[    13.348]     WinGranularity: 64
[    13.348]     WinSize: 64
[    13.348]     WinASegment: 0xa000
[    13.348]     WinBSegment: 0x0
[    13.348]     WinFuncPtr: 0xc0005543
[    13.348]     BytesPerScanline: 1280
[    13.348]     XResolution: 640
[    13.348]     YResolution: 350
[    13.348]     XCharSize: 8
[    13.348]     YCharSize: 14
[    13.348]     NumberOfPlanes: 1
[    13.348]     BitsPerPixel: 16
[    13.348]     NumberOfBanks: 1
[    13.348]     MemoryModel: 6
[    13.348]     BankSize: 0
[    13.348]     NumberOfImages: 35
[    13.348]     RedMaskSize: 5
[    13.348]     RedFieldPosition: 11
[    13.348]     GreenMaskSize: 6
[    13.348]     GreenFieldPosition: 5
[    13.348]     BlueMaskSize: 5
[    13.348]     BlueFieldPosition: 0
[    13.348]     RsvdMaskSize: 0
[    13.348]     RsvdFieldPosition: 0
[    13.348]     DirectColorModeInfo: 0
[    13.348]     PhysBasePtr: 0x80000000
[    13.348]     LinBytesPerScanLine: 1280
[    13.348]     BnkNumberOfImagePages: 35
[    13.348]     LinNumberOfImagePages: 35
[    13.348]     LinRedMaskSize: 5
[    13.348]     LinRedFieldPosition: 11
[    13.348]     LinGreenMaskSize: 6
[    13.348]     LinGreenFieldPosition: 5
[    13.348]     LinBlueMaskSize: 5
[    13.349]     LinBlueFieldPosition: 0
[    13.349]     LinRsvdMaskSize: 0
[    13.349]     LinRsvdFieldPosition: 0
[    13.349]     MaxPixelClock: 400000000
[    13.350] *Mode: 1c6 (640x350)
[    13.350]     ModeAttributes: 0xbb
[    13.350]     WinAAttributes: 0x7
[    13.350]     WinBAttributes: 0x0
[    13.350]     WinGranularity: 64
[    13.350]     WinSize: 64
[    13.350]     WinASegment: 0xa000
[    13.350]     WinBSegment: 0x0
[    13.350]     WinFuncPtr: 0xc0005543
[    13.350]     BytesPerScanline: 2560
[    13.350]     XResolution: 640
[    13.350]     YResolution: 350
[    13.350]     XCharSize: 8
[    13.350]     YCharSize: 14
[    13.350]     NumberOfPlanes: 1
[    13.350]     BitsPerPixel: 32
[    13.350]     NumberOfBanks: 1
[    13.350]     MemoryModel: 6
[    13.350]     BankSize: 0
[    13.350]     NumberOfImages: 17
[    13.350]     RedMaskSize: 8
[    13.350]     RedFieldPosition: 16
[    13.350]     GreenMaskSize: 8
[    13.350]     GreenFieldPosition: 8
[    13.350]     BlueMaskSize: 8
[    13.350]     BlueFieldPosition: 0
[    13.350]     RsvdMaskSize: 0
[    13.350]     RsvdFieldPosition: 0
[    13.350]     DirectColorModeInfo: 0
[    13.350]     PhysBasePtr: 0x80000000
[    13.350]     LinBytesPerScanLine: 2560
[    13.350]     BnkNumberOfImagePages: 17
[    13.350]     LinNumberOfImagePages: 17
[    13.350]     LinRedMaskSize: 8
[    13.350]     LinRedFieldPosition: 16
[    13.350]     LinGreenMaskSize: 8
[    13.350]     LinGreenFieldPosition: 8
[    13.350]     LinBlueMaskSize: 8
[    13.350]     LinBlueFieldPosition: 0
[    13.350]     LinRsvdMaskSize: 0
[    13.350]     LinRsvdFieldPosition: 0
[    13.350]     MaxPixelClock: 400000000
[    13.352] Mode: 133 (720x400)
[    13.352]     ModeAttributes: 0xbb
[    13.352]     WinAAttributes: 0x7
[    13.352]     WinBAttributes: 0x0
[    13.352]     WinGranularity: 64
[    13.352]     WinSize: 64
[    13.352]     WinASegment: 0xa000
[    13.352]     WinBSegment: 0x0
[    13.352]     WinFuncPtr: 0xc0005543
[    13.352]     BytesPerScanline: 768
[    13.352]     XResolution: 720
[    13.352]     YResolution: 400
[    13.352]     XCharSize: 8
[    13.352]     YCharSize: 16
[    13.352]     NumberOfPlanes: 1
[    13.352]     BitsPerPixel: 8
[    13.352]     NumberOfBanks: 1
[    13.352]     MemoryModel: 4
[    13.352]     BankSize: 0
[    13.352]     NumberOfImages: 50
[    13.352]     RedMaskSize: 0
[    13.352]     RedFieldPosition: 0
[    13.352]     GreenMaskSize: 0
[    13.352]     GreenFieldPosition: 0
[    13.352]     BlueMaskSize: 0
[    13.352]     BlueFieldPosition: 0
[    13.352]     RsvdMaskSize: 0
[    13.352]     RsvdFieldPosition: 0
[    13.352]     DirectColorModeInfo: 0
[    13.352]     PhysBasePtr: 0x80000000
[    13.352]     LinBytesPerScanLine: 768
[    13.352]     BnkNumberOfImagePages: 50
[    13.352]     LinNumberOfImagePages: 50
[    13.352]     LinRedMaskSize: 0
[    13.352]     LinRedFieldPosition: 0
[    13.352]     LinGreenMaskSize: 0
[    13.352]     LinGreenFieldPosition: 0
[    13.352]     LinBlueMaskSize: 0
[    13.352]     LinBlueFieldPosition: 0
[    13.352]     LinRsvdMaskSize: 0
[    13.352]     LinRsvdFieldPosition: 0
[    13.352]     MaxPixelClock: 400000000
[    13.354] Mode: 135 (720x400)
[    13.354]     ModeAttributes: 0xbb
[    13.354]     WinAAttributes: 0x7
[    13.354]     WinBAttributes: 0x0
[    13.354]     WinGranularity: 64
[    13.354]     WinSize: 64
[    13.354]     WinASegment: 0xa000
[    13.354]     WinBSegment: 0x0
[    13.354]     WinFuncPtr: 0xc0005543
[    13.354]     BytesPerScanline: 1472
[    13.354]     XResolution: 720
[    13.354]     YResolution: 400
[    13.354]     XCharSize: 8
[    13.354]     YCharSize: 16
[    13.354]     NumberOfPlanes: 1
[    13.354]     BitsPerPixel: 16
[    13.354]     NumberOfBanks: 1
[    13.354]     MemoryModel: 6
[    13.354]     BankSize: 0
[    13.354]     NumberOfImages: 27
[    13.354]     RedMaskSize: 5
[    13.354]     RedFieldPosition: 11
[    13.354]     GreenMaskSize: 6
[    13.354]     GreenFieldPosition: 5
[    13.354]     BlueMaskSize: 5
[    13.354]     BlueFieldPosition: 0
[    13.354]     RsvdMaskSize: 0
[    13.354]     RsvdFieldPosition: 0
[    13.354]     DirectColorModeInfo: 0
[    13.354]     PhysBasePtr: 0x80000000
[    13.354]     LinBytesPerScanLine: 1472
[    13.354]     BnkNumberOfImagePages: 27
[    13.354]     LinNumberOfImagePages: 27
[    13.354]     LinRedMaskSize: 5
[    13.354]     LinRedFieldPosition: 11
[    13.354]     LinGreenMaskSize: 6
[    13.354]     LinGreenFieldPosition: 5
[    13.354]     LinBlueMaskSize: 5
[    13.354]     LinBlueFieldPosition: 0
[    13.354]     LinRsvdMaskSize: 0
[    13.354]     LinRsvdFieldPosition: 0
[    13.354]     MaxPixelClock: 400000000
[    13.356] *Mode: 136 (720x400)
[    13.356]     ModeAttributes: 0xbb
[    13.356]     WinAAttributes: 0x7
[    13.356]     WinBAttributes: 0x0
[    13.356]     WinGranularity: 64
[    13.356]     WinSize: 64
[    13.356]     WinASegment: 0xa000
[    13.356]     WinBSegment: 0x0
[    13.356]     WinFuncPtr: 0xc0005543
[    13.356]     BytesPerScanline: 2944
[    13.356]     XResolution: 720
[    13.356]     YResolution: 400
[    13.356]     XCharSize: 8
[    13.356]     YCharSize: 16
[    13.356]     NumberOfPlanes: 1
[    13.356]     BitsPerPixel: 32
[    13.356]     NumberOfBanks: 1
[    13.356]     MemoryModel: 6
[    13.356]     BankSize: 0
[    13.356]     NumberOfImages: 13
[    13.356]     RedMaskSize: 8
[    13.356]     RedFieldPosition: 16
[    13.356]     GreenMaskSize: 8
[    13.356]     GreenFieldPosition: 8
[    13.356]     BlueMaskSize: 8
[    13.356]     BlueFieldPosition: 0
[    13.356]     RsvdMaskSize: 0
[    13.356]     RsvdFieldPosition: 0
[    13.356]     DirectColorModeInfo: 0
[    13.356]     PhysBasePtr: 0x80000000
[    13.356]     LinBytesPerScanLine: 2944
[    13.356]     BnkNumberOfImagePages: 13
[    13.356]     LinNumberOfImagePages: 13
[    13.356]     LinRedMaskSize: 8
[    13.356]     LinRedFieldPosition: 16
[    13.356]     LinGreenMaskSize: 8
[    13.356]     LinGreenFieldPosition: 8
[    13.356]     LinBlueMaskSize: 8
[    13.356]     LinBlueFieldPosition: 0
[    13.356]     LinRsvdMaskSize: 0
[    13.356]     LinRsvdFieldPosition: 0
[    13.356]     MaxPixelClock: 400000000
[    13.358] Mode: 153 (1152x864)
[    13.358]     ModeAttributes: 0xba
[    13.358]     WinAAttributes: 0x7
[    13.358]     WinBAttributes: 0x0
[    13.358]     WinGranularity: 64
[    13.358]     WinSize: 64
[    13.358]     WinASegment: 0xa000
[    13.358]     WinBSegment: 0x0
[    13.358]     WinFuncPtr: 0xc0005543
[    13.358]     BytesPerScanline: 1152
[    13.358]     XResolution: 1152
[    13.358]     YResolution: 864
[    13.358]     XCharSize: 8
[    13.358]     YCharSize: 16
[    13.358]     NumberOfPlanes: 1
[    13.358]     BitsPerPixel: 8
[    13.358]     NumberOfBanks: 1
[    13.358]     MemoryModel: 4
[    13.358]     BankSize: 0
[    13.358]     NumberOfImages: 15
[    13.358]     RedMaskSize: 0
[    13.358]     RedFieldPosition: 0
[    13.358]     GreenMaskSize: 0
[    13.358]     GreenFieldPosition: 0
[    13.358]     BlueMaskSize: 0
[    13.358]     BlueFieldPosition: 0
[    13.358]     RsvdMaskSize: 0
[    13.358]     RsvdFieldPosition: 0
[    13.358]     DirectColorModeInfo: 0
[    13.358]     PhysBasePtr: 0x80000000
[    13.358]     LinBytesPerScanLine: 1152
[    13.358]     BnkNumberOfImagePages: 15
[    13.358]     LinNumberOfImagePages: 15
[    13.358]     LinRedMaskSize: 0
[    13.358]     LinRedFieldPosition: 0
[    13.358]     LinGreenMaskSize: 0
[    13.358]     LinGreenFieldPosition: 0
[    13.358]     LinBlueMaskSize: 0
[    13.358]     LinBlueFieldPosition: 0
[    13.358]     LinRsvdMaskSize: 0
[    13.358]     LinRsvdFieldPosition: 0
[    13.358]     MaxPixelClock: 400000000
[    13.360] Mode: 155 (1152x864)
[    13.360]     ModeAttributes: 0xba
[    13.360]     WinAAttributes: 0x7
[    13.360]     WinBAttributes: 0x0
[    13.360]     WinGranularity: 64
[    13.360]     WinSize: 64
[    13.360]     WinASegment: 0xa000
[    13.360]     WinBSegment: 0x0
[    13.360]     WinFuncPtr: 0xc0005543
[    13.360]     BytesPerScanline: 2304
[    13.360]     XResolution: 1152
[    13.360]     YResolution: 864
[    13.360]     XCharSize: 8
[    13.360]     YCharSize: 16
[    13.360]     NumberOfPlanes: 1
[    13.360]     BitsPerPixel: 16
[    13.360]     NumberOfBanks: 1
[    13.360]     MemoryModel: 6
[    13.360]     BankSize: 0
[    13.360]     NumberOfImages: 7
[    13.360]     RedMaskSize: 5
[    13.360]     RedFieldPosition: 11
[    13.360]     GreenMaskSize: 6
[    13.360]     GreenFieldPosition: 5
[    13.360]     BlueMaskSize: 5
[    13.360]     BlueFieldPosition: 0
[    13.360]     RsvdMaskSize: 0
[    13.360]     RsvdFieldPosition: 0
[    13.360]     DirectColorModeInfo: 0
[    13.360]     PhysBasePtr: 0x80000000
[    13.360]     LinBytesPerScanLine: 2304
[    13.360]     BnkNumberOfImagePages: 7
[    13.360]     LinNumberOfImagePages: 7
[    13.360]     LinRedMaskSize: 5
[    13.360]     LinRedFieldPosition: 11
[    13.360]     LinGreenMaskSize: 6
[    13.360]     LinGreenFieldPosition: 5
[    13.360]     LinBlueMaskSize: 5
[    13.360]     LinBlueFieldPosition: 0
[    13.360]     LinRsvdMaskSize: 0
[    13.360]     LinRsvdFieldPosition: 0
[    13.360]     MaxPixelClock: 400000000
[    13.362] Mode: 156 (1152x864)
[    13.362]     ModeAttributes: 0xba
[    13.362]     WinAAttributes: 0x7
[    13.362]     WinBAttributes: 0x0
[    13.362]     WinGranularity: 64
[    13.362]     WinSize: 64
[    13.362]     WinASegment: 0xa000
[    13.362]     WinBSegment: 0x0
[    13.362]     WinFuncPtr: 0xc0005543
[    13.362]     BytesPerScanline: 4608
[    13.362]     XResolution: 1152
[    13.362]     YResolution: 864
[    13.362]     XCharSize: 8
[    13.362]     YCharSize: 16
[    13.362]     NumberOfPlanes: 1
[    13.362]     BitsPerPixel: 32
[    13.362]     NumberOfBanks: 1
[    13.362]     MemoryModel: 6
[    13.362]     BankSize: 0
[    13.362]     NumberOfImages: 3
[    13.362]     RedMaskSize: 8
[    13.362]     RedFieldPosition: 16
[    13.362]     GreenMaskSize: 8
[    13.362]     GreenFieldPosition: 8
[    13.362]     BlueMaskSize: 8
[    13.362]     BlueFieldPosition: 0
[    13.362]     RsvdMaskSize: 0
[    13.362]     RsvdFieldPosition: 0
[    13.362]     DirectColorModeInfo: 0
[    13.362]     PhysBasePtr: 0x80000000
[    13.362]     LinBytesPerScanLine: 4608
[    13.362]     BnkNumberOfImagePages: 3
[    13.362]     LinNumberOfImagePages: 3
[    13.362]     LinRedMaskSize: 8
[    13.362]     LinRedFieldPosition: 16
[    13.362]     LinGreenMaskSize: 8
[    13.362]     LinGreenFieldPosition: 8
[    13.362]     LinBlueMaskSize: 8
[    13.362]     LinBlueFieldPosition: 0
[    13.362]     LinRsvdMaskSize: 0
[    13.362]     LinRsvdFieldPosition: 0
[    13.362]     MaxPixelClock: 400000000
[    13.364] Mode: 163 (1280x960)
[    13.364]     ModeAttributes: 0xba
[    13.364]     WinAAttributes: 0x7
[    13.364]     WinBAttributes: 0x0
[    13.364]     WinGranularity: 64
[    13.364]     WinSize: 64
[    13.364]     WinASegment: 0xa000
[    13.364]     WinBSegment: 0x0
[    13.364]     WinFuncPtr: 0xc0005543
[    13.364]     BytesPerScanline: 1280
[    13.364]     XResolution: 1280
[    13.364]     YResolution: 960
[    13.364]     XCharSize: 8
[    13.364]     YCharSize: 16
[    13.364]     NumberOfPlanes: 1
[    13.364]     BitsPerPixel: 8
[    13.364]     NumberOfBanks: 1
[    13.364]     MemoryModel: 4
[    13.364]     BankSize: 0
[    13.364]     NumberOfImages: 12
[    13.364]     RedMaskSize: 0
[    13.364]     RedFieldPosition: 0
[    13.364]     GreenMaskSize: 0
[    13.364]     GreenFieldPosition: 0
[    13.364]     BlueMaskSize: 0
[    13.364]     BlueFieldPosition: 0
[    13.364]     RsvdMaskSize: 0
[    13.364]     RsvdFieldPosition: 0
[    13.364]     DirectColorModeInfo: 0
[    13.364]     PhysBasePtr: 0x80000000
[    13.364]     LinBytesPerScanLine: 1280
[    13.364]     BnkNumberOfImagePages: 12
[    13.364]     LinNumberOfImagePages: 12
[    13.364]     LinRedMaskSize: 0
[    13.364]     LinRedFieldPosition: 0
[    13.364]     LinGreenMaskSize: 0
[    13.364]     LinGreenFieldPosition: 0
[    13.364]     LinBlueMaskSize: 0
[    13.364]     LinBlueFieldPosition: 0
[    13.364]     LinRsvdMaskSize: 0
[    13.364]     LinRsvdFieldPosition: 0
[    13.364]     MaxPixelClock: 400000000
[    13.366] Mode: 165 (1280x960)
[    13.366]     ModeAttributes: 0xba
[    13.366]     WinAAttributes: 0x7
[    13.366]     WinBAttributes: 0x0
[    13.366]     WinGranularity: 64
[    13.366]     WinSize: 64
[    13.366]     WinASegment: 0xa000
[    13.366]     WinBSegment: 0x0
[    13.366]     WinFuncPtr: 0xc0005543
[    13.366]     BytesPerScanline: 2560
[    13.366]     XResolution: 1280
[    13.366]     YResolution: 960
[    13.366]     XCharSize: 8
[    13.366]     YCharSize: 16
[    13.366]     NumberOfPlanes: 1
[    13.366]     BitsPerPixel: 16
[    13.366]     NumberOfBanks: 1
[    13.366]     MemoryModel: 6
[    13.366]     BankSize: 0
[    13.366]     NumberOfImages: 5
[    13.366]     RedMaskSize: 5
[    13.366]     RedFieldPosition: 11
[    13.366]     GreenMaskSize: 6
[    13.366]     GreenFieldPosition: 5
[    13.366]     BlueMaskSize: 5
[    13.366]     BlueFieldPosition: 0
[    13.366]     RsvdMaskSize: 0
[    13.366]     RsvdFieldPosition: 0
[    13.366]     DirectColorModeInfo: 0
[    13.366]     PhysBasePtr: 0x80000000
[    13.366]     LinBytesPerScanLine: 2560
[    13.366]     BnkNumberOfImagePages: 5
[    13.366]     LinNumberOfImagePages: 5
[    13.366]     LinRedMaskSize: 5
[    13.366]     LinRedFieldPosition: 11
[    13.366]     LinGreenMaskSize: 6
[    13.366]     LinGreenFieldPosition: 5
[    13.366]     LinBlueMaskSize: 5
[    13.366]     LinBlueFieldPosition: 0
[    13.366]     LinRsvdMaskSize: 0
[    13.366]     LinRsvdFieldPosition: 0
[    13.366]     MaxPixelClock: 400000000
[    13.368] Mode: 166 (1280x960)
[    13.368]     ModeAttributes: 0xba
[    13.368]     WinAAttributes: 0x7
[    13.368]     WinBAttributes: 0x0
[    13.368]     WinGranularity: 64
[    13.368]     WinSize: 64
[    13.368]     WinASegment: 0xa000
[    13.368]     WinBSegment: 0x0
[    13.368]     WinFuncPtr: 0xc0005543
[    13.368]     BytesPerScanline: 5120
[    13.368]     XResolution: 1280
[    13.368]     YResolution: 960
[    13.368]     XCharSize: 8
[    13.368]     YCharSize: 16
[    13.368]     NumberOfPlanes: 1
[    13.368]     BitsPerPixel: 32
[    13.368]     NumberOfBanks: 1
[    13.368]     MemoryModel: 6
[    13.368]     BankSize: 0
[    13.368]     NumberOfImages: 2
[    13.368]     RedMaskSize: 8
[    13.368]     RedFieldPosition: 16
[    13.368]     GreenMaskSize: 8
[    13.368]     GreenFieldPosition: 8
[    13.368]     BlueMaskSize: 8
[    13.368]     BlueFieldPosition: 0
[    13.368]     RsvdMaskSize: 0
[    13.368]     RsvdFieldPosition: 0
[    13.368]     DirectColorModeInfo: 0
[    13.368]     PhysBasePtr: 0x80000000
[    13.368]     LinBytesPerScanLine: 5120
[    13.368]     BnkNumberOfImagePages: 2
[    13.368]     LinNumberOfImagePages: 2
[    13.368]     LinRedMaskSize: 8
[    13.368]     LinRedFieldPosition: 16
[    13.368]     LinGreenMaskSize: 8
[    13.368]     LinGreenFieldPosition: 8
[    13.368]     LinBlueMaskSize: 8
[    13.368]     LinBlueFieldPosition: 0
[    13.368]     LinRsvdMaskSize: 0
[    13.368]     LinRsvdFieldPosition: 0
[    13.368]     MaxPixelClock: 400000000
[    13.370] *Mode: 121 (640x480)
[    13.370]     ModeAttributes: 0xbb
[    13.370]     WinAAttributes: 0x7
[    13.370]     WinBAttributes: 0x0
[    13.370]     WinGranularity: 64
[    13.370]     WinSize: 64
[    13.370]     WinASegment: 0xa000
[    13.370]     WinBSegment: 0x0
[    13.370]     WinFuncPtr: 0xc0005543
[    13.370]     BytesPerScanline: 2560
[    13.370]     XResolution: 640
[    13.370]     YResolution: 480
[    13.370]     XCharSize: 8
[    13.370]     YCharSize: 16
[    13.370]     NumberOfPlanes: 1
[    13.370]     BitsPerPixel: 32
[    13.370]     NumberOfBanks: 1
[    13.370]     MemoryModel: 6
[    13.370]     BankSize: 0
[    13.370]     NumberOfImages: 12
[    13.370]     RedMaskSize: 8
[    13.370]     RedFieldPosition: 16
[    13.370]     GreenMaskSize: 8
[    13.370]     GreenFieldPosition: 8
[    13.370]     BlueMaskSize: 8
[    13.370]     BlueFieldPosition: 0
[    13.370]     RsvdMaskSize: 0
[    13.370]     RsvdFieldPosition: 0
[    13.370]     DirectColorModeInfo: 0
[    13.370]     PhysBasePtr: 0x80000000
[    13.370]     LinBytesPerScanLine: 2560
[    13.370]     BnkNumberOfImagePages: 12
[    13.370]     LinNumberOfImagePages: 12
[    13.370]     LinRedMaskSize: 8
[    13.370]     LinRedFieldPosition: 16
[    13.370]     LinGreenMaskSize: 8
[    13.370]     LinGreenFieldPosition: 8
[    13.370]     LinBlueMaskSize: 8
[    13.370]     LinBlueFieldPosition: 0
[    13.370]     LinRsvdMaskSize: 0
[    13.370]     LinRsvdFieldPosition: 0
[    13.370]     MaxPixelClock: 400000000
[    13.372] *Mode: 122 (800x600)
[    13.372]     ModeAttributes: 0xbb
[    13.372]     WinAAttributes: 0x7
[    13.372]     WinBAttributes: 0x0
[    13.372]     WinGranularity: 64
[    13.372]     WinSize: 64
[    13.372]     WinASegment: 0xa000
[    13.372]     WinBSegment: 0x0
[    13.372]     WinFuncPtr: 0xc0005543
[    13.372]     BytesPerScanline: 3200
[    13.372]     XResolution: 800
[    13.372]     YResolution: 600
[    13.372]     XCharSize: 8
[    13.372]     YCharSize: 14
[    13.372]     NumberOfPlanes: 1
[    13.372]     BitsPerPixel: 32
[    13.372]     NumberOfBanks: 1
[    13.372]     MemoryModel: 6
[    13.372]     BankSize: 0
[    13.372]     NumberOfImages: 7
[    13.372]     RedMaskSize: 8
[    13.372]     RedFieldPosition: 16
[    13.372]     GreenMaskSize: 8
[    13.372]     GreenFieldPosition: 8
[    13.372]     BlueMaskSize: 8
[    13.372]     BlueFieldPosition: 0
[    13.372]     RsvdMaskSize: 0
[    13.372]     RsvdFieldPosition: 0
[    13.372]     DirectColorModeInfo: 0
[    13.372]     PhysBasePtr: 0x80000000
[    13.372]     LinBytesPerScanLine: 3200
[    13.372]     BnkNumberOfImagePages: 7
[    13.372]     LinNumberOfImagePages: 7
[    13.372]     LinRedMaskSize: 8
[    13.372]     LinRedFieldPosition: 16
[    13.372]     LinGreenMaskSize: 8
[    13.372]     LinGreenFieldPosition: 8
[    13.372]     LinBlueMaskSize: 8
[    13.372]     LinBlueFieldPosition: 0
[    13.372]     LinRsvdMaskSize: 0
[    13.372]     LinRsvdFieldPosition: 0
[    13.372]     MaxPixelClock: 400000000
[    13.374] *Mode: 123 (1024x768)
[    13.374]     ModeAttributes: 0xbb
[    13.374]     WinAAttributes: 0x7
[    13.374]     WinBAttributes: 0x0
[    13.374]     WinGranularity: 64
[    13.374]     WinSize: 64
[    13.374]     WinASegment: 0xa000
[    13.374]     WinBSegment: 0x0
[    13.374]     WinFuncPtr: 0xc0005543
[    13.374]     BytesPerScanline: 4096
[    13.374]     XResolution: 1024
[    13.374]     YResolution: 768
[    13.374]     XCharSize: 8
[    13.374]     YCharSize: 16
[    13.374]     NumberOfPlanes: 1
[    13.374]     BitsPerPixel: 32
[    13.374]     NumberOfBanks: 1
[    13.374]     MemoryModel: 6
[    13.374]     BankSize: 0
[    13.374]     NumberOfImages: 4
[    13.374]     RedMaskSize: 8
[    13.374]     RedFieldPosition: 16
[    13.374]     GreenMaskSize: 8
[    13.374]     GreenFieldPosition: 8
[    13.374]     BlueMaskSize: 8
[    13.374]     BlueFieldPosition: 0
[    13.374]     RsvdMaskSize: 0
[    13.374]     RsvdFieldPosition: 0
[    13.374]     DirectColorModeInfo: 0
[    13.374]     PhysBasePtr: 0x80000000
[    13.374]     LinBytesPerScanLine: 4096
[    13.374]     BnkNumberOfImagePages: 4
[    13.374]     LinNumberOfImagePages: 4
[    13.374]     LinRedMaskSize: 8
[    13.374]     LinRedFieldPosition: 16
[    13.374]     LinGreenMaskSize: 8
[    13.374]     LinGreenFieldPosition: 8
[    13.374]     LinBlueMaskSize: 8
[    13.374]     LinBlueFieldPosition: 0
[    13.374]     LinRsvdMaskSize: 0
[    13.374]     LinRsvdFieldPosition: 0
[    13.374]     MaxPixelClock: 400000000
[    13.376] Mode: 124 (1280x1024)
[    13.376]     ModeAttributes: 0xba
[    13.376]     WinAAttributes: 0x7
[    13.376]     WinBAttributes: 0x0
[    13.376]     WinGranularity: 64
[    13.376]     WinSize: 64
[    13.376]     WinASegment: 0xa000
[    13.376]     WinBSegment: 0x0
[    13.376]     WinFuncPtr: 0xc0005543
[    13.376]     BytesPerScanline: 5120
[    13.376]     XResolution: 1280
[    13.376]     YResolution: 1024
[    13.376]     XCharSize: 8
[    13.376]     YCharSize: 16
[    13.376]     NumberOfPlanes: 1
[    13.376]     BitsPerPixel: 32
[    13.376]     NumberOfBanks: 1
[    13.376]     MemoryModel: 6
[    13.376]     BankSize: 0
[    13.376]     NumberOfImages: 2
[    13.376]     RedMaskSize: 8
[    13.376]     RedFieldPosition: 16
[    13.376]     GreenMaskSize: 8
[    13.376]     GreenFieldPosition: 8
[    13.376]     BlueMaskSize: 8
[    13.376]     BlueFieldPosition: 0
[    13.376]     RsvdMaskSize: 0
[    13.376]     RsvdFieldPosition: 0
[    13.376]     DirectColorModeInfo: 0
[    13.376]     PhysBasePtr: 0x80000000
[    13.376]     LinBytesPerScanLine: 5120
[    13.376]     BnkNumberOfImagePages: 2
[    13.376]     LinNumberOfImagePages: 2
[    13.376]     LinRedMaskSize: 8
[    13.376]     LinRedFieldPosition: 16
[    13.376]     LinGreenMaskSize: 8
[    13.376]     LinGreenFieldPosition: 8
[    13.376]     LinBlueMaskSize: 8
[    13.376]     LinBlueFieldPosition: 0
[    13.376]     LinRsvdMaskSize: 0
[    13.376]     LinRsvdFieldPosition: 0
[    13.376]     MaxPixelClock: 400000000
[    13.378] Mode: 143 (1400x1050)
[    13.378]     ModeAttributes: 0xba
[    13.378]     WinAAttributes: 0x7
[    13.378]     WinBAttributes: 0x0
[    13.378]     WinGranularity: 64
[    13.378]     WinSize: 64
[    13.378]     WinASegment: 0xa000
[    13.378]     WinBSegment: 0x0
[    13.378]     WinFuncPtr: 0xc0005543
[    13.378]     BytesPerScanline: 1408
[    13.378]     XResolution: 1400
[    13.378]     YResolution: 1050
[    13.378]     XCharSize: 8
[    13.378]     YCharSize: 16
[    13.378]     NumberOfPlanes: 1
[    13.378]     BitsPerPixel: 8
[    13.378]     NumberOfBanks: 1
[    13.378]     MemoryModel: 4
[    13.378]     BankSize: 0
[    13.378]     NumberOfImages: 10
[    13.378]     RedMaskSize: 0
[    13.378]     RedFieldPosition: 0
[    13.378]     GreenMaskSize: 0
[    13.378]     GreenFieldPosition: 0
[    13.378]     BlueMaskSize: 0
[    13.378]     BlueFieldPosition: 0
[    13.378]     RsvdMaskSize: 0
[    13.378]     RsvdFieldPosition: 0
[    13.378]     DirectColorModeInfo: 0
[    13.378]     PhysBasePtr: 0x80000000
[    13.378]     LinBytesPerScanLine: 1408
[    13.378]     BnkNumberOfImagePages: 10
[    13.378]     LinNumberOfImagePages: 10
[    13.378]     LinRedMaskSize: 0
[    13.378]     LinRedFieldPosition: 0
[    13.378]     LinGreenMaskSize: 0
[    13.378]     LinGreenFieldPosition: 0
[    13.378]     LinBlueMaskSize: 0
[    13.378]     LinBlueFieldPosition: 0
[    13.378]     LinRsvdMaskSize: 0
[    13.378]     LinRsvdFieldPosition: 0
[    13.378]     MaxPixelClock: 400000000
[    13.380] Mode: 145 (1400x1050)
[    13.380]     ModeAttributes: 0xba
[    13.380]     WinAAttributes: 0x7
[    13.380]     WinBAttributes: 0x0
[    13.380]     WinGranularity: 64
[    13.380]     WinSize: 64
[    13.380]     WinASegment: 0xa000
[    13.380]     WinBSegment: 0x0
[    13.380]     WinFuncPtr: 0xc0005543
[    13.380]     BytesPerScanline: 2816
[    13.380]     XResolution: 1400
[    13.380]     YResolution: 1050
[    13.380]     XCharSize: 8
[    13.380]     YCharSize: 16
[    13.380]     NumberOfPlanes: 1
[    13.380]     BitsPerPixel: 16
[    13.380]     NumberOfBanks: 1
[    13.380]     MemoryModel: 6
[    13.380]     BankSize: 0
[    13.380]     NumberOfImages: 4
[    13.380]     RedMaskSize: 5
[    13.380]     RedFieldPosition: 11
[    13.380]     GreenMaskSize: 6
[    13.380]     GreenFieldPosition: 5
[    13.380]     BlueMaskSize: 5
[    13.380]     BlueFieldPosition: 0
[    13.380]     RsvdMaskSize: 0
[    13.380]     RsvdFieldPosition: 0
[    13.380]     DirectColorModeInfo: 0
[    13.380]     PhysBasePtr: 0x80000000
[    13.380]     LinBytesPerScanLine: 2816
[    13.380]     BnkNumberOfImagePages: 4
[    13.380]     LinNumberOfImagePages: 4
[    13.380]     LinRedMaskSize: 5
[    13.380]     LinRedFieldPosition: 11
[    13.380]     LinGreenMaskSize: 6
[    13.380]     LinGreenFieldPosition: 5
[    13.380]     LinBlueMaskSize: 5
[    13.380]     LinBlueFieldPosition: 0
[    13.380]     LinRsvdMaskSize: 0
[    13.380]     LinRsvdFieldPosition: 0
[    13.380]     MaxPixelClock: 400000000
[    13.382] Mode: 146 (1400x1050)
[    13.382]     ModeAttributes: 0xba
[    13.382]     WinAAttributes: 0x7
[    13.382]     WinBAttributes: 0x0
[    13.382]     WinGranularity: 64
[    13.382]     WinSize: 64
[    13.382]     WinASegment: 0xa000
[    13.382]     WinBSegment: 0x0
[    13.382]     WinFuncPtr: 0xc0005543
[    13.382]     BytesPerScanline: 5632
[    13.382]     XResolution: 1400
[    13.382]     YResolution: 1050
[    13.382]     XCharSize: 8
[    13.382]     YCharSize: 16
[    13.382]     NumberOfPlanes: 1
[    13.382]     BitsPerPixel: 32
[    13.382]     NumberOfBanks: 1
[    13.382]     MemoryModel: 6
[    13.382]     BankSize: 0
[    13.382]     NumberOfImages: 1
[    13.382]     RedMaskSize: 8
[    13.382]     RedFieldPosition: 16
[    13.382]     GreenMaskSize: 8
[    13.382]     GreenFieldPosition: 8
[    13.382]     BlueMaskSize: 8
[    13.382]     BlueFieldPosition: 0
[    13.382]     RsvdMaskSize: 0
[    13.382]     RsvdFieldPosition: 0
[    13.382]     DirectColorModeInfo: 0
[    13.382]     PhysBasePtr: 0x80000000
[    13.382]     LinBytesPerScanLine: 5632
[    13.382]     BnkNumberOfImagePages: 1
[    13.382]     LinNumberOfImagePages: 1
[    13.382]     LinRedMaskSize: 8
[    13.382]     LinRedFieldPosition: 16
[    13.382]     LinGreenMaskSize: 8
[    13.382]     LinGreenFieldPosition: 8
[    13.382]     LinBlueMaskSize: 8
[    13.382]     LinBlueFieldPosition: 0
[    13.382]     LinRsvdMaskSize: 0
[    13.382]     LinRsvdFieldPosition: 0
[    13.382]     MaxPixelClock: 400000000
[    13.384] Mode: 173 (1600x1200)
[    13.384]     ModeAttributes: 0xba
[    13.384]     WinAAttributes: 0x7
[    13.384]     WinBAttributes: 0x0
[    13.384]     WinGranularity: 64
[    13.384]     WinSize: 64
[    13.384]     WinASegment: 0xa000
[    13.384]     WinBSegment: 0x0
[    13.384]     WinFuncPtr: 0xc0005543
[    13.384]     BytesPerScanline: 1600
[    13.384]     XResolution: 1600
[    13.384]     YResolution: 1200
[    13.384]     XCharSize: 8
[    13.384]     YCharSize: 16
[    13.384]     NumberOfPlanes: 1
[    13.384]     BitsPerPixel: 8
[    13.384]     NumberOfBanks: 1
[    13.384]     MemoryModel: 4
[    13.384]     BankSize: 0
[    13.384]     NumberOfImages: 7
[    13.384]     RedMaskSize: 0
[    13.384]     RedFieldPosition: 0
[    13.384]     GreenMaskSize: 0
[    13.384]     GreenFieldPosition: 0
[    13.384]     BlueMaskSize: 0
[    13.384]     BlueFieldPosition: 0
[    13.384]     RsvdMaskSize: 0
[    13.384]     RsvdFieldPosition: 0
[    13.384]     DirectColorModeInfo: 0
[    13.384]     PhysBasePtr: 0x80000000
[    13.384]     LinBytesPerScanLine: 1600
[    13.384]     BnkNumberOfImagePages: 7
[    13.384]     LinNumberOfImagePages: 7
[    13.384]     LinRedMaskSize: 0
[    13.384]     LinRedFieldPosition: 0
[    13.384]     LinGreenMaskSize: 0
[    13.384]     LinGreenFieldPosition: 0
[    13.384]     LinBlueMaskSize: 0
[    13.384]     LinBlueFieldPosition: 0
[    13.384]     LinRsvdMaskSize: 0
[    13.384]     LinRsvdFieldPosition: 0
[    13.384]     MaxPixelClock: 400000000
[    13.386] Mode: 175 (1600x1200)
[    13.386]     ModeAttributes: 0xba
[    13.386]     WinAAttributes: 0x7
[    13.386]     WinBAttributes: 0x0
[    13.386]     WinGranularity: 64
[    13.386]     WinSize: 64
[    13.386]     WinASegment: 0xa000
[    13.386]     WinBSegment: 0x0
[    13.386]     WinFuncPtr: 0xc0005543
[    13.386]     BytesPerScanline: 3200
[    13.386]     XResolution: 1600
[    13.386]     YResolution: 1200
[    13.386]     XCharSize: 8
[    13.386]     YCharSize: 16
[    13.386]     NumberOfPlanes: 1
[    13.386]     BitsPerPixel: 16
[    13.386]     NumberOfBanks: 1
[    13.386]     MemoryModel: 6
[    13.386]     BankSize: 0
[    13.386]     NumberOfImages: 3
[    13.386]     RedMaskSize: 5
[    13.386]     RedFieldPosition: 11
[    13.386]     GreenMaskSize: 6
[    13.386]     GreenFieldPosition: 5
[    13.386]     BlueMaskSize: 5
[    13.386]     BlueFieldPosition: 0
[    13.386]     RsvdMaskSize: 0
[    13.386]     RsvdFieldPosition: 0
[    13.386]     DirectColorModeInfo: 0
[    13.386]     PhysBasePtr: 0x80000000
[    13.386]     LinBytesPerScanLine: 3200
[    13.386]     BnkNumberOfImagePages: 3
[    13.386]     LinNumberOfImagePages: 3
[    13.386]     LinRedMaskSize: 5
[    13.386]     LinRedFieldPosition: 11
[    13.386]     LinGreenMaskSize: 6
[    13.386]     LinGreenFieldPosition: 5
[    13.386]     LinBlueMaskSize: 5
[    13.386]     LinBlueFieldPosition: 0
[    13.386]     LinRsvdMaskSize: 0
[    13.386]     LinRsvdFieldPosition: 0
[    13.386]     MaxPixelClock: 400000000
[    13.388] Mode: 176 (1600x1200)
[    13.388]     ModeAttributes: 0xba
[    13.388]     WinAAttributes: 0x7
[    13.388]     WinBAttributes: 0x0
[    13.388]     WinGranularity: 64
[    13.388]     WinSize: 64
[    13.388]     WinASegment: 0xa000
[    13.388]     WinBSegment: 0x0
[    13.388]     WinFuncPtr: 0xc0005543
[    13.388]     BytesPerScanline: 6400
[    13.388]     XResolution: 1600
[    13.388]     YResolution: 1200
[    13.388]     XCharSize: 8
[    13.388]     YCharSize: 16
[    13.388]     NumberOfPlanes: 1
[    13.388]     BitsPerPixel: 32
[    13.388]     NumberOfBanks: 1
[    13.388]     MemoryModel: 6
[    13.388]     BankSize: 0
[    13.388]     NumberOfImages: 1
[    13.388]     RedMaskSize: 8
[    13.388]     RedFieldPosition: 16
[    13.388]     GreenMaskSize: 8
[    13.388]     GreenFieldPosition: 8
[    13.388]     BlueMaskSize: 8
[    13.388]     BlueFieldPosition: 0
[    13.388]     RsvdMaskSize: 0
[    13.388]     RsvdFieldPosition: 0
[    13.388]     DirectColorModeInfo: 0
[    13.388]     PhysBasePtr: 0x80000000
[    13.388]     LinBytesPerScanLine: 6400
[    13.388]     BnkNumberOfImagePages: 1
[    13.388]     LinNumberOfImagePages: 1
[    13.388]     LinRedMaskSize: 8
[    13.388]     LinRedFieldPosition: 16
[    13.388]     LinGreenMaskSize: 8
[    13.388]     LinGreenFieldPosition: 8
[    13.388]     LinBlueMaskSize: 8
[    13.388]     LinBlueFieldPosition: 0
[    13.388]     LinRsvdMaskSize: 0
[    13.388]     LinRsvdFieldPosition: 0
[    13.388]     MaxPixelClock: 400000000
[    13.390] Mode: 183 (1792x1344)
[    13.390]     ModeAttributes: 0xba
[    13.390]     WinAAttributes: 0x7
[    13.390]     WinBAttributes: 0x0
[    13.390]     WinGranularity: 64
[    13.390]     WinSize: 64
[    13.390]     WinASegment: 0xa000
[    13.390]     WinBSegment: 0x0
[    13.390]     WinFuncPtr: 0xc0005543
[    13.390]     BytesPerScanline: 1792
[    13.390]     XResolution: 1792
[    13.390]     YResolution: 1344
[    13.390]     XCharSize: 8
[    13.390]     YCharSize: 16
[    13.390]     NumberOfPlanes: 1
[    13.390]     BitsPerPixel: 8
[    13.390]     NumberOfBanks: 1
[    13.390]     MemoryModel: 4
[    13.390]     BankSize: 0
[    13.390]     NumberOfImages: 5
[    13.390]     RedMaskSize: 0
[    13.390]     RedFieldPosition: 0
[    13.390]     GreenMaskSize: 0
[    13.390]     GreenFieldPosition: 0
[    13.390]     BlueMaskSize: 0
[    13.390]     BlueFieldPosition: 0
[    13.390]     RsvdMaskSize: 0
[    13.390]     RsvdFieldPosition: 0
[    13.390]     DirectColorModeInfo: 0
[    13.390]     PhysBasePtr: 0x80000000
[    13.390]     LinBytesPerScanLine: 1792
[    13.390]     BnkNumberOfImagePages: 5
[    13.390]     LinNumberOfImagePages: 5
[    13.390]     LinRedMaskSize: 0
[    13.390]     LinRedFieldPosition: 0
[    13.390]     LinGreenMaskSize: 0
[    13.390]     LinGreenFieldPosition: 0
[    13.390]     LinBlueMaskSize: 0
[    13.390]     LinBlueFieldPosition: 0
[    13.390]     LinRsvdMaskSize: 0
[    13.390]     LinRsvdFieldPosition: 0
[    13.390]     MaxPixelClock: 400000000
[    13.392] Mode: 185 (1792x1344)
[    13.392]     ModeAttributes: 0xba
[    13.392]     WinAAttributes: 0x7
[    13.392]     WinBAttributes: 0x0
[    13.392]     WinGranularity: 64
[    13.392]     WinSize: 64
[    13.392]     WinASegment: 0xa000
[    13.392]     WinBSegment: 0x0
[    13.392]     WinFuncPtr: 0xc0005543
[    13.392]     BytesPerScanline: 3584
[    13.392]     XResolution: 1792
[    13.392]     YResolution: 1344
[    13.392]     XCharSize: 8
[    13.392]     YCharSize: 16
[    13.392]     NumberOfPlanes: 1
[    13.392]     BitsPerPixel: 16
[    13.392]     NumberOfBanks: 1
[    13.392]     MemoryModel: 6
[    13.392]     BankSize: 0
[    13.392]     NumberOfImages: 2
[    13.392]     RedMaskSize: 5
[    13.392]     RedFieldPosition: 11
[    13.392]     GreenMaskSize: 6
[    13.392]     GreenFieldPosition: 5
[    13.392]     BlueMaskSize: 5
[    13.392]     BlueFieldPosition: 0
[    13.392]     RsvdMaskSize: 0
[    13.392]     RsvdFieldPosition: 0
[    13.392]     DirectColorModeInfo: 0
[    13.392]     PhysBasePtr: 0x80000000
[    13.392]     LinBytesPerScanLine: 3584
[    13.392]     BnkNumberOfImagePages: 2
[    13.392]     LinNumberOfImagePages: 2
[    13.392]     LinRedMaskSize: 5
[    13.393]     LinRedFieldPosition: 11
[    13.393]     LinGreenMaskSize: 6
[    13.393]     LinGreenFieldPosition: 5
[    13.393]     LinBlueMaskSize: 5
[    13.393]     LinBlueFieldPosition: 0
[    13.393]     LinRsvdMaskSize: 0
[    13.393]     LinRsvdFieldPosition: 0
[    13.393]     MaxPixelClock: 400000000
[    13.394] Mode: 186 (1792x1344)
[    13.394]     ModeAttributes: 0xba
[    13.394]     WinAAttributes: 0x7
[    13.394]     WinBAttributes: 0x0
[    13.394]     WinGranularity: 64
[    13.394]     WinSize: 64
[    13.394]     WinASegment: 0xa000
[    13.394]     WinBSegment: 0x0
[    13.394]     WinFuncPtr: 0xc0005543
[    13.394]     BytesPerScanline: 7168
[    13.394]     XResolution: 1792
[    13.394]     YResolution: 1344
[    13.394]     XCharSize: 8
[    13.394]     YCharSize: 16
[    13.394]     NumberOfPlanes: 1
[    13.394]     BitsPerPixel: 32
[    13.394]     NumberOfBanks: 1
[    13.394]     MemoryModel: 6
[    13.394]     BankSize: 0
[    13.394]     NumberOfImages: 1
[    13.394]     RedMaskSize: 8
[    13.394]     RedFieldPosition: 16
[    13.394]     GreenMaskSize: 8
[    13.394]     GreenFieldPosition: 8
[    13.394]     BlueMaskSize: 8
[    13.395]     BlueFieldPosition: 0
[    13.395]     RsvdMaskSize: 0
[    13.395]     RsvdFieldPosition: 0
[    13.395]     DirectColorModeInfo: 0
[    13.395]     PhysBasePtr: 0x80000000
[    13.395]     LinBytesPerScanLine: 7168
[    13.395]     BnkNumberOfImagePages: 1
[    13.395]     LinNumberOfImagePages: 1
[    13.395]     LinRedMaskSize: 8
[    13.395]     LinRedFieldPosition: 16
[    13.395]     LinGreenMaskSize: 8
[    13.395]     LinGreenFieldPosition: 8
[    13.395]     LinBlueMaskSize: 8
[    13.395]     LinBlueFieldPosition: 0
[    13.395]     LinRsvdMaskSize: 0
[    13.395]     LinRsvdFieldPosition: 0
[    13.395]     MaxPixelClock: 400000000
[    13.396] Mode: 1d3 (1856x1392)
[    13.396]     ModeAttributes: 0xba
[    13.396]     WinAAttributes: 0x7
[    13.396]     WinBAttributes: 0x0
[    13.396]     WinGranularity: 64
[    13.396]     WinSize: 64
[    13.396]     WinASegment: 0xa000
[    13.396]     WinBSegment: 0x0
[    13.396]     WinFuncPtr: 0xc0005543
[    13.396]     BytesPerScanline: 1856
[    13.396]     XResolution: 1856
[    13.396]     YResolution: 1392
[    13.396]     XCharSize: 8
[    13.396]     YCharSize: 16
[    13.396]     NumberOfPlanes: 1
[    13.396]     BitsPerPixel: 8
[    13.396]     NumberOfBanks: 1
[    13.396]     MemoryModel: 4
[    13.396]     BankSize: 0
[    13.396]     NumberOfImages: 5
[    13.396]     RedMaskSize: 0
[    13.397]     RedFieldPosition: 0
[    13.397]     GreenMaskSize: 0
[    13.397]     GreenFieldPosition: 0
[    13.397]     BlueMaskSize: 0
[    13.397]     BlueFieldPosition: 0
[    13.397]     RsvdMaskSize: 0
[    13.397]     RsvdFieldPosition: 0
[    13.397]     DirectColorModeInfo: 0
[    13.397]     PhysBasePtr: 0x80000000
[    13.397]     LinBytesPerScanLine: 1856
[    13.397]     BnkNumberOfImagePages: 5
[    13.397]     LinNumberOfImagePages: 5
[    13.397]     LinRedMaskSize: 0
[    13.397]     LinRedFieldPosition: 0
[    13.397]     LinGreenMaskSize: 0
[    13.397]     LinGreenFieldPosition: 0
[    13.397]     LinBlueMaskSize: 0
[    13.397]     LinBlueFieldPosition: 0
[    13.397]     LinRsvdMaskSize: 0
[    13.397]     LinRsvdFieldPosition: 0
[    13.397]     MaxPixelClock: 400000000
[    13.398] Mode: 1d5 (1856x1392)
[    13.398]     ModeAttributes: 0xba
[    13.398]     WinAAttributes: 0x7
[    13.398]     WinBAttributes: 0x0
[    13.398]     WinGranularity: 64
[    13.398]     WinSize: 64
[    13.398]     WinASegment: 0xa000
[    13.398]     WinBSegment: 0x0
[    13.398]     WinFuncPtr: 0xc0005543
[    13.398]     BytesPerScanline: 3712
[    13.398]     XResolution: 1856
[    13.398]     YResolution: 1392
[    13.398]     XCharSize: 8
[    13.398]     YCharSize: 16
[    13.398]     NumberOfPlanes: 1
[    13.398]     BitsPerPixel: 16
[    13.398]     NumberOfBanks: 1
[    13.399]     MemoryModel: 6
[    13.399]     BankSize: 0
[    13.399]     NumberOfImages: 2
[    13.399]     RedMaskSize: 5
[    13.399]     RedFieldPosition: 11
[    13.399]     GreenMaskSize: 6
[    13.399]     GreenFieldPosition: 5
[    13.399]     BlueMaskSize: 5
[    13.399]     BlueFieldPosition: 0
[    13.399]     RsvdMaskSize: 0
[    13.399]     RsvdFieldPosition: 0
[    13.399]     DirectColorModeInfo: 0
[    13.399]     PhysBasePtr: 0x80000000
[    13.399]     LinBytesPerScanLine: 3712
[    13.399]     BnkNumberOfImagePages: 2
[    13.399]     LinNumberOfImagePages: 2
[    13.399]     LinRedMaskSize: 5
[    13.399]     LinRedFieldPosition: 11
[    13.399]     LinGreenMaskSize: 6
[    13.399]     LinGreenFieldPosition: 5
[    13.399]     LinBlueMaskSize: 5
[    13.399]     LinBlueFieldPosition: 0
[    13.399]     LinRsvdMaskSize: 0
[    13.399]     LinRsvdFieldPosition: 0
[    13.399]     MaxPixelClock: 400000000
[    13.400] Mode: 1d6 (1856x1392)
[    13.400]     ModeAttributes: 0xba
[    13.400]     WinAAttributes: 0x7
[    13.400]     WinBAttributes: 0x0
[    13.400]     WinGranularity: 64
[    13.400]     WinSize: 64
[    13.400]     WinASegment: 0xa000
[    13.400]     WinBSegment: 0x0
[    13.400]     WinFuncPtr: 0xc0005543
[    13.400]     BytesPerScanline: 7424
[    13.400]     XResolution: 1856
[    13.401]     YResolution: 1392
[    13.401]     XCharSize: 8
[    13.401]     YCharSize: 16
[    13.401]     NumberOfPlanes: 1
[    13.401]     BitsPerPixel: 32
[    13.401]     NumberOfBanks: 1
[    13.401]     MemoryModel: 6
[    13.401]     BankSize: 0
[    13.401]     NumberOfImages: 1
[    13.401]     RedMaskSize: 8
[    13.401]     RedFieldPosition: 16
[    13.401]     GreenMaskSize: 8
[    13.401]     GreenFieldPosition: 8
[    13.401]     BlueMaskSize: 8
[    13.401]     BlueFieldPosition: 0
[    13.401]     RsvdMaskSize: 0
[    13.401]     RsvdFieldPosition: 0
[    13.401]     DirectColorModeInfo: 0
[    13.401]     PhysBasePtr: 0x80000000
[    13.401]     LinBytesPerScanLine: 7424
[    13.401]     BnkNumberOfImagePages: 1
[    13.401]     LinNumberOfImagePages: 1
[    13.401]     LinRedMaskSize: 8
[    13.401]     LinRedFieldPosition: 16
[    13.401]     LinGreenMaskSize: 8
[    13.401]     LinGreenFieldPosition: 8
[    13.401]     LinBlueMaskSize: 8
[    13.401]     LinBlueFieldPosition: 0
[    13.401]     LinRsvdMaskSize: 0
[    13.401]     LinRsvdFieldPosition: 0
[    13.401]     MaxPixelClock: 400000000
[    13.402] Mode: 1e3 (1920x1440)
[    13.402]     ModeAttributes: 0xba
[    13.402]     WinAAttributes: 0x7
[    13.402]     WinBAttributes: 0x0
[    13.402]     WinGranularity: 64
[    13.402]     WinSize: 64
[    13.402]     WinASegment: 0xa000
[    13.403]     WinBSegment: 0x0
[    13.403]     WinFuncPtr: 0xc0005543
[    13.403]     BytesPerScanline: 1920
[    13.403]     XResolution: 1920
[    13.403]     YResolution: 1440
[    13.403]     XCharSize: 8
[    13.403]     YCharSize: 16
[    13.403]     NumberOfPlanes: 1
[    13.403]     BitsPerPixel: 8
[    13.403]     NumberOfBanks: 1
[    13.403]     MemoryModel: 4
[    13.403]     BankSize: 0
[    13.403]     NumberOfImages: 4
[    13.403]     RedMaskSize: 0
[    13.403]     RedFieldPosition: 0
[    13.403]     GreenMaskSize: 0
[    13.403]     GreenFieldPosition: 0
[    13.403]     BlueMaskSize: 0
[    13.403]     BlueFieldPosition: 0
[    13.403]     RsvdMaskSize: 0
[    13.403]     RsvdFieldPosition: 0
[    13.403]     DirectColorModeInfo: 0
[    13.403]     PhysBasePtr: 0x80000000
[    13.403]     LinBytesPerScanLine: 1920
[    13.403]     BnkNumberOfImagePages: 4
[    13.403]     LinNumberOfImagePages: 4
[    13.403]     LinRedMaskSize: 0
[    13.403]     LinRedFieldPosition: 0
[    13.403]     LinGreenMaskSize: 0
[    13.403]     LinGreenFieldPosition: 0
[    13.403]     LinBlueMaskSize: 0
[    13.403]     LinBlueFieldPosition: 0
[    13.403]     LinRsvdMaskSize: 0
[    13.403]     LinRsvdFieldPosition: 0
[    13.403]     MaxPixelClock: 400000000
[    13.404] Mode: 1e5 (1920x1440)
[    13.405]     ModeAttributes: 0xba
[    13.405]     WinAAttributes: 0x7
[    13.405]     WinBAttributes: 0x0
[    13.405]     WinGranularity: 64
[    13.405]     WinSize: 64
[    13.405]     WinASegment: 0xa000
[    13.405]     WinBSegment: 0x0
[    13.405]     WinFuncPtr: 0xc0005543
[    13.405]     BytesPerScanline: 3840
[    13.405]     XResolution: 1920
[    13.405]     YResolution: 1440
[    13.405]     XCharSize: 8
[    13.405]     YCharSize: 16
[    13.405]     NumberOfPlanes: 1
[    13.405]     BitsPerPixel: 16
[    13.405]     NumberOfBanks: 1
[    13.405]     MemoryModel: 6
[    13.405]     BankSize: 0
[    13.405]     NumberOfImages: 2
[    13.405]     RedMaskSize: 5
[    13.405]     RedFieldPosition: 11
[    13.405]     GreenMaskSize: 6
[    13.405]     GreenFieldPosition: 5
[    13.405]     BlueMaskSize: 5
[    13.405]     BlueFieldPosition: 0
[    13.405]     RsvdMaskSize: 0
[    13.405]     RsvdFieldPosition: 0
[    13.405]     DirectColorModeInfo: 0
[    13.405]     PhysBasePtr: 0x80000000
[    13.405]     LinBytesPerScanLine: 3840
[    13.405]     BnkNumberOfImagePages: 2
[    13.405]     LinNumberOfImagePages: 2
[    13.405]     LinRedMaskSize: 5
[    13.405]     LinRedFieldPosition: 11
[    13.405]     LinGreenMaskSize: 6
[    13.405]     LinGreenFieldPosition: 5
[    13.405]     LinBlueMaskSize: 5
[    13.405]     LinBlueFieldPosition: 0
[    13.405]     LinRsvdMaskSize: 0
[    13.405]     LinRsvdFieldPosition: 0
[    13.405]     MaxPixelClock: 400000000
[    13.407] Mode: 1e6 (1920x1440)
[    13.407]     ModeAttributes: 0xba
[    13.407]     WinAAttributes: 0x7
[    13.407]     WinBAttributes: 0x0
[    13.407]     WinGranularity: 64
[    13.407]     WinSize: 64
[    13.407]     WinASegment: 0xa000
[    13.407]     WinBSegment: 0x0
[    13.407]     WinFuncPtr: 0xc0005543
[    13.407]     BytesPerScanline: 7680
[    13.407]     XResolution: 1920
[    13.407]     YResolution: 1440
[    13.407]     XCharSize: 8
[    13.407]     YCharSize: 16
[    13.407]     NumberOfPlanes: 1
[    13.407]     BitsPerPixel: 32
[    13.407]     NumberOfBanks: 1
[    13.407]     MemoryModel: 6
[    13.407]     BankSize: 0
[    13.407]     NumberOfImages: 1
[    13.407]     RedMaskSize: 8
[    13.407]     RedFieldPosition: 16
[    13.407]     GreenMaskSize: 8
[    13.407]     GreenFieldPosition: 8
[    13.407]     BlueMaskSize: 8
[    13.407]     BlueFieldPosition: 0
[    13.407]     RsvdMaskSize: 0
[    13.407]     RsvdFieldPosition: 0
[    13.407]     DirectColorModeInfo: 0
[    13.407]     PhysBasePtr: 0x80000000
[    13.407]     LinBytesPerScanLine: 7680
[    13.407]     BnkNumberOfImagePages: 1
[    13.407]     LinNumberOfImagePages: 1
[    13.407]     LinRedMaskSize: 8
[    13.407]     LinRedFieldPosition: 16
[    13.407]     LinGreenMaskSize: 8
[    13.407]     LinGreenFieldPosition: 8
[    13.407]     LinBlueMaskSize: 8
[    13.407]     LinBlueFieldPosition: 0
[    13.407]     LinRsvdMaskSize: 0
[    13.407]     LinRsvdFieldPosition: 0
[    13.407]     MaxPixelClock: 400000000
[    13.407] 
[    13.407] (II) VESA(0): Total Memory: 256 64KB banks (16384kB)
[    13.407] (II) VESA(0): <default monitor>: Using hsync value of 47.38 kHz
[    13.407] (II) VESA(0): <default monitor>: Using vrefresh value of 59.97 Hz
[    13.407] (WW) VESA(0): Unable to estimate virtual size
[    13.407] (II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
[    13.407] (II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
[    13.407] (II) VESA(0): Not using built-in mode "640x480" (no mode of this name)
[    13.407] (II) VESA(0): Not using built-in mode "720x400" (no mode of this name)
[    13.408] (II) VESA(0): Not using built-in mode "640x350" (no mode of this name)
[    13.408] (II) VESA(0): Not using built-in mode "512x384" (no mode of this name)
[    13.408] (II) VESA(0): Not using built-in mode "320x240" (no mode of this name)
[    13.408] (II) VESA(0): Not using built-in mode "320x200" (no mode of this name)
[    13.408] (WW) VESA(0): No valid modes left. Trying less strict filter...
[    13.408] (II) VESA(0): <default monitor>: Using hsync value of 47.38 kHz
[    13.408] (II) VESA(0): <default monitor>: Using vrefresh value of 59.97 Hz
[    13.408] (WW) VESA(0): Unable to estimate virtual size
[    13.408] (II) VESA(0): Not using built-in mode "800x600" (hsync out of range)
[    13.408] (II) VESA(0): Not using built-in mode "640x480" (hsync out of range)
[    13.408] (II) VESA(0): Not using built-in mode "720x400" (hsync out of range)
[    13.408] (II) VESA(0): Not using built-in mode "640x350" (hsync out of range)
[    13.408] (II) VESA(0): Not using built-in mode "512x384" (hsync out of range)
[    13.408] (II) VESA(0): Not using built-in mode "320x240" (illegal horizontal timings)
[    13.408] (II) VESA(0): Not using built-in mode "320x200" (illegal horizontal timings)
[    13.408] (--) VESA(0): Virtual size is 1024x768 (pitch 1024)
[    13.408] (**) VESA(0): *Built-in mode "1024x768"
[    13.408] (**) VESA(0): Display dimensions: (350, 190) mm
[    13.408] (**) VESA(0): DPI set to (74, 102)
[    13.408] (**) VESA(0): Using "Shadow Framebuffer"
[    13.408] (II) Loading sub module "shadow"
[    13.408] (II) LoadModule: "shadow"
[    13.409] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    13.409] (II) Module shadow: vendor="X.Org Foundation"
[    13.409]     compiled for 1.9.0, module version = 1.1.0
[    13.409]     ABI class: X.Org ANSI C Emulation, version 0.4
[    13.409] (II) Loading sub module "fb"
[    13.409] (II) LoadModule: "fb"
[    13.410] (II) Loading /usr/lib/xorg/modules/libfb.so
[    13.410] (II) Module fb: vendor="X.Org Foundation"
[    13.410]     compiled for 1.9.0, module version = 1.0.0
[    13.410]     ABI class: X.Org ANSI C Emulation, version 0.4
[    13.410] (II) UnloadModule: "radeon"
[    13.410] (II) Unloading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    13.410] (II) UnloadModule: "fbdev"
[    13.410] (II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    13.410] (II) UnloadModule: "fbdevhw"
[    13.410] (II) Unloading /usr/lib/xorg/modules/libfbdevhw.so
[    13.410] (==) Depth 24 pixmap format is 32 bpp
[    13.410] (II) Loading sub module "int10"
[    13.410] (II) LoadModule: "int10"
[    13.411] (II) Reloading /usr/lib/xorg/modules/libint10.so
[    13.411] (II) VESA(0): initializing int10
[    13.417] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    13.417] (II) VESA(0): VESA BIOS detected
[    13.417] (II) VESA(0): VESA VBE Version 3.0
[    13.417] (II) VESA(0): VESA VBE Total Mem: 16384 kB
[    13.417] (II) VESA(0): VESA VBE OEM: AMD ATOMBIOS
[    13.417] (II) VESA(0): VESA VBE OEM Software Rev: 12.37
[    13.417] (II) VESA(0): VESA VBE OEM Vendor: (C) 1988-2010, AMD Technologies Inc. 
[    13.417] (II) VESA(0): VESA VBE OEM Product: WRESTLER
[    13.417] (II) VESA(0): VESA VBE OEM Product Rev: 01.00
[    13.422] (II) VESA(0): virtual address = 0xb65a3000,
    physical address = 0x80000000, size = 16777216
[    13.441] (II) VESA(0): Setting up VESA Mode 0x123 (1024x768)
[    13.758] (==) VESA(0): Default visual is TrueColor
[    13.758] (==) VESA(0): Backing store disabled
[    13.758] (==) VESA(0): DPMS enabled
[    13.758] (==) RandR enabled
[    13.758] (II) Initializing built-in extension Generic Event Extension
[    13.758] (II) Initializing built-in extension SHAPE
[    13.758] (II) Initializing built-in extension MIT-SHM
[    13.758] (II) Initializing built-in extension XInputExtension
[    13.758] (II) Initializing built-in extension XTEST
[    13.758] (II) Initializing built-in extension BIG-REQUESTS
[    13.758] (II) Initializing built-in extension SYNC
[    13.758] (II) Initializing built-in extension XKEYBOARD
[    13.758] (II) Initializing built-in extension XC-MISC
[    13.758] (II) Initializing built-in extension SECURITY
[    13.758] (II) Initializing built-in extension XINERAMA
[    13.758] (II) Initializing built-in extension XFIXES
[    13.758] (II) Initializing built-in extension RENDER
[    13.758] (II) Initializing built-in extension RANDR
[    13.758] (II) Initializing built-in extension COMPOSITE
[    13.758] (II) Initializing built-in extension DAMAGE
[    13.758] (II) Initializing built-in extension GESTURE
[    13.777] (II) AIGLX: Screen 0 is not DRI2 capable
[    13.777] (II) AIGLX: Screen 0 is not DRI capable
[    13.782] (II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
[    13.782] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    13.822] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    13.836] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    13.836] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    13.837] (II) LoadModule: "evdev"
[    13.837] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    13.838] (II) Module evdev: vendor="X.Org Foundation"
[    13.838]     compiled for 1.9.0, module version = 2.3.2
[    13.838]     Module class: X.Org XInput Driver
[    13.838]     ABI class: X.Org XInput driver, version 11.0
[    13.838] (**) Power Button: always reports core events
[    13.838] (**) Power Button: Device: "/dev/input/event3"
[    13.852] (II) Power Button: Found keys
[    13.852] (II) Power Button: Configuring as keyboard
[    13.852] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    13.853] (**) Option "xkb_rules" "evdev"
[    13.853] (**) Option "xkb_model" "pc105"
[    13.853] (**) Option "xkb_layout" "us"
[    13.853] (**) Option "xkb_variant" "dvorak"
[    13.853] (**) Option "xkb_options" "lv3:ralt_switch"
[    13.857] (II) XKB: reuse xkmfile /var/lib/xkb/server-6F86FD73C5E4C040CF174C28CF7A029ECAC10E5B.xkm
[    13.859] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    13.859] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    13.859] (**) Video Bus: always reports core events
[    13.859] (**) Video Bus: Device: "/dev/input/event5"
[    13.864] (II) Video Bus: Found keys
[    13.864] (II) Video Bus: Configuring as keyboard
[    13.864] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    13.864] (**) Option "xkb_rules" "evdev"
[    13.864] (**) Option "xkb_model" "pc105"
[    13.864] (**) Option "xkb_layout" "us"
[    13.864] (**) Option "xkb_variant" "dvorak"
[    13.865] (**) Option "xkb_options" "lv3:ralt_switch"
[    13.868] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    13.868] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    13.868] (**) Power Button: always reports core events
[    13.868] (**) Power Button: Device: "/dev/input/event0"
[    13.872] (II) Power Button: Found keys
[    13.872] (II) Power Button: Configuring as keyboard
[    13.872] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    13.872] (**) Option "xkb_rules" "evdev"
[    13.872] (**) Option "xkb_model" "pc105"
[    13.872] (**) Option "xkb_layout" "us"
[    13.872] (**) Option "xkb_variant" "dvorak"
[    13.872] (**) Option "xkb_options" "lv3:ralt_switch"
[    13.873] (II) config/udev: Adding input device Lid Switch (/dev/input/event2)
[    13.873] (II) No input driver/identifier specified (ignoring)
[    13.874] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    13.874] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    13.874] (**) Sleep Button: always reports core events
[    13.874] (**) Sleep Button: Device: "/dev/input/event1"
[    13.880] (II) Sleep Button: Found keys
[    13.880] (II) Sleep Button: Configuring as keyboard
[    13.880] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    13.880] (**) Option "xkb_rules" "evdev"
[    13.881] (**) Option "xkb_model" "pc105"
[    13.881] (**) Option "xkb_layout" "us"
[    13.881] (**) Option "xkb_variant" "dvorak"
[    13.881] (**) Option "xkb_options" "lv3:ralt_switch"
[    13.886] (II) config/udev: Adding input device 1.3M WebCam (/dev/input/event6)
[    13.886] (**) 1.3M WebCam: Applying InputClass "evdev keyboard catchall"
[    13.886] (**) 1.3M WebCam: always reports core events
[    13.886] (**) 1.3M WebCam: Device: "/dev/input/event6"
[    13.900] (II) 1.3M WebCam: Found keys
[    13.900] (II) 1.3M WebCam: Configuring as keyboard
[    13.900] (II) XINPUT: Adding extended input device "1.3M WebCam" (type: KEYBOARD)
[    13.900] (**) Option "xkb_rules" "evdev"
[    13.901] (**) Option "xkb_model" "pc105"
[    13.901] (**) Option "xkb_layout" "us"
[    13.901] (**) Option "xkb_variant" "dvorak"
[    13.901] (**) Option "xkb_options" "lv3:ralt_switch"
[    13.904] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    13.905] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    13.905] (**) AT Translated Set 2 keyboard: always reports core events
[    13.905] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    13.920] (II) AT Translated Set 2 keyboard: Found keys
[    13.920] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    13.920] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    13.920] (**) Option "xkb_rules" "evdev"
[    13.921] (**) Option "xkb_model" "pc105"
[    13.921] (**) Option "xkb_layout" "us"
[    13.921] (**) Option "xkb_variant" "dvorak"
[    13.921] (**) Option "xkb_options" "lv3:ralt_switch"
[    13.922] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event7)
[    13.922] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    13.922] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    13.922] (II) LoadModule: "synaptics"
[    13.922] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    13.922] (II) Module synaptics: vendor="X.Org Foundation"
[    13.922]     compiled for 1.9.0, module version = 1.2.2
[    13.923]     Module class: X.Org XInput Driver
[    13.923]     ABI class: X.Org XInput driver, version 11.0
[    13.923] (II) Synaptics touchpad driver version 1.2.2
[    13.923] (**) Option "Device" "/dev/input/event7"
[    13.968] (II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5772
[    13.968] (II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 5086
[    13.968] (II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    13.968] (II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
[    13.968] (II) SynPS/2 Synaptics TouchPad: buttons: left right
[    14.000] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    14.000] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    14.016] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    14.016] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    14.017] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
[    14.017] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    14.017] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    14.048] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    14.049] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    14.049] (II) No input driver/identifier specified (ignoring)

```

---

### Post by Yellow Pasque on 2011-03-03
Hmm, it tried to load the radeon driver, but fell back to VESA. You should try the latest drivers from xorg-edgers PPA: [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

### Post by hreichgott on 2011-03-03
Hi,
Thanks for your help. I do already have those drivers installed (xserver-xorg-video-ati and a couple others). How do I tell Ubuntu to use them? They don't show up under the System > Additional Drivers thing.

---

### Post by Yellow Pasque on 2011-03-03
Make an /etc/X11/xorg.conf file with  driver radeon as an option. I'm sorry if tha's not specific, but I'm pretty drunk right now. Hopefully, someone selse can give you more detail if you can't figure it out from googling.

---

### Post by hreichgott on 2011-03-03
I don't know much about xorg.conf but I tried making one as follows
```
Section "Device"
        Identifier  "Default Device"
        Driver      "radeon"
EndSection



```

Rebooted, only got a terminal, no graphics at all!

Can anyone help?

---

### Post by chungrylionMenai on 2012-07-26
i have the same problem, and my ubuntu 10.4 , and im using a AcerView 34e monitor, and the system dont recognize it too... im begin to guessing that maybe the monitor have some to see in the resolution problem, pliz if someone get the solution for the ati 9802 , tell me,  thks

---

### Post by wildmanne39 on 2012-07-26
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

