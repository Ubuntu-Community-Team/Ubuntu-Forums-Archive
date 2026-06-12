---
title: "Dualshock3 / sixaxis in usb mode with 10.10"
date: 2010-10-19
forum: Hardware
---

### Post by tipp98 on 2010-10-19
Since my PC is always on and my PS3 isn't, I use my PC to charge the controller and would like to be able to use the controller while plugged in. I've almost got it but have some calibration issues. The cursor automatically moves to the upper left. When I run jstest the sticks check out with all axis idling at 0 and I have to move it to about 29000xy (according to jstest) to idle the cursor.. Here is my .conf file

```

Section "InputClass"
        Identifier      "DualShock3"
        MatchProduct    "Sony"
        Driver          "joystick"
        Option          "SendCoreEvents" "true"
        Option          "MapAxis3" "mode=relative axis=x"
        Option          "MapAxis4" "mode=relative axis=y"
#...
EndSection
```
What kind of alteration is needed to get it to settle down every time I plug it in?

---

### Post by tipp98 on 2010-10-19
So it appears that it is being registered twice. If I run xinput --list

```
&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB-PS/2 Optical Mouse           id=9    [slave  pointer  (2)]
&#9116;   &#8627; Sony PLAYSTATION(R)3 Controller           id=11   [slave  pointer  (2)]
&#9116;   &#8627; Sony PLAYSTATION(R)3 Controller           id=13   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Power Button                              id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                              id=8    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard              id=10   [slave  keyboard (3)]
    &#8627; Sony PLAYSTATION(R)3 Controller (keys)    id=12   [slave  keyboard (3)]
    &#8627; Sony PLAYSTATION(R)3 Controller (keys)    id=14   [slave  keyboard (3)]

```
When I test them, one spits out a bunch of 0 values at idle and the other only outputs a value when the stick is moved (i.e. the way I have it set up.) So, the question is, how do I prevent xinput from grabbing the duplicate?

---

### Post by tipp98 on 2010-10-19
Here is my Xorg.0.log file, it looks like my InputClass is being applied to both /dev/input/event5 and /dev/input/js0. Odly enough however, although it uses the same options, they behave differently when testing in xinput. Anyway, I'm close, I see the problem, I just don't know how to fix it.

```
[    30.570] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    30.590] X Protocol Version 11, Revision 0
[    30.590] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[    30.590] Current Operating System: Linux xs 2.6.35-22-generic #34-Ubuntu SMP Sun Oct 10 09:24:00 UTC 2010 i686
[    30.590] Kernel command line: root=UUID=61f3ae1d-994e-454d-bbbc-1dd58fd9b517 ro quiet splash 
[    30.590] Build Date: 16 September 2010  05:39:22PM
[    30.590] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
[    30.590] Current version of pixman: 0.18.4
[    30.590] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    30.590] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    30.590] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Oct 19 15:49:47 2010
[    30.611] (==) Using config directory: "/etc/X11/xorg.conf.d"
[    30.611] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    30.632] (==) No Layout section.  Using the first Screen section.
[    30.632] (==) No screen section available. Using defaults.
[    30.632] (**) |-->Screen "Default Screen Section" (0)
[    30.632] (**) |   |-->Monitor "<default monitor>"
[    30.633] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    30.633] (==) Automatically adding devices
[    30.633] (==) Automatically enabling devices
[    30.633] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    30.633] 	Entry deleted from font path.
[    30.633] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    30.633] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    30.633] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    30.633] (II) Loader magic: 0x81f8e00
[    30.633] (II) Module ABI versions:
[    30.633] 	X.Org ANSI C Emulation: 0.4
[    30.633] 	X.Org Video Driver: 8.0
[    30.633] 	X.Org XInput driver : 11.0
[    30.633] 	X.Org Server Extension : 4.0
[    30.635] (--) PCI:*(0:1:0:0) 1002:4150:1002:0002 rev 0, Mem @ 0xc0000000/268435456, 0xe9000000/65536, I/O @ 0x0000c000/256, BIOS @ 0x????????/131072
[    30.635] (--) PCI: (0:1:0:1) 1002:4170:1002:0003 rev 0, Mem @ 0xd0000000/268435456, 0xe9010000/65536
[    30.635] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    30.635] (II) LoadModule: "extmod"
[    30.668] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    30.668] (II) Module extmod: vendor="X.Org Foundation"
[    30.668] 	compiled for 1.9.0, module version = 1.0.0
[    30.668] 	Module class: X.Org Server Extension
[    30.668] 	ABI class: X.Org Server Extension, version 4.0
[    30.668] (II) Loading extension MIT-SCREEN-SAVER
[    30.668] (II) Loading extension XFree86-VidModeExtension
[    30.668] (II) Loading extension XFree86-DGA
[    30.669] (II) Loading extension DPMS
[    30.669] (II) Loading extension XVideo
[    30.669] (II) Loading extension XVideo-MotionCompensation
[    30.669] (II) Loading extension X-Resource
[    30.669] (II) LoadModule: "dbe"
[    30.669] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    30.669] (II) Module dbe: vendor="X.Org Foundation"
[    30.669] 	compiled for 1.9.0, module version = 1.0.0
[    30.669] 	Module class: X.Org Server Extension
[    30.669] 	ABI class: X.Org Server Extension, version 4.0
[    30.669] (II) Loading extension DOUBLE-BUFFER
[    30.669] (II) LoadModule: "glx"
[    30.670] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    30.670] (II) Module glx: vendor="X.Org Foundation"
[    30.670] 	compiled for 1.9.0, module version = 1.0.0
[    30.670] 	ABI class: X.Org Server Extension, version 4.0
[    30.670] (==) AIGLX enabled
[    30.670] (II) Loading extension GLX
[    30.670] (II) LoadModule: "record"
[    30.671] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    30.671] (II) Module record: vendor="X.Org Foundation"
[    30.671] 	compiled for 1.9.0, module version = 1.13.0
[    30.671] 	Module class: X.Org Server Extension
[    30.671] 	ABI class: X.Org Server Extension, version 4.0
[    30.671] (II) Loading extension RECORD
[    30.671] (II) LoadModule: "dri"
[    30.683] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    30.683] (II) Module dri: vendor="X.Org Foundation"
[    30.683] 	compiled for 1.9.0, module version = 1.0.0
[    30.683] 	ABI class: X.Org Server Extension, version 4.0
[    30.683] (II) Loading extension XFree86-DRI
[    30.683] (II) LoadModule: "dri2"
[    30.685] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    30.685] (II) Module dri2: vendor="X.Org Foundation"
[    30.685] 	compiled for 1.9.0, module version = 1.2.0
[    30.685] 	ABI class: X.Org Server Extension, version 4.0
[    30.685] (II) Loading extension DRI2
[    30.685] (==) Matched ati as autoconfigured driver 0
[    30.685] (==) Matched vesa as autoconfigured driver 1
[    30.685] (==) Matched fbdev as autoconfigured driver 2
[    30.685] (==) Assigned the driver to the xf86ConfigLayout
[    30.685] (II) LoadModule: "ati"
[    30.686] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    30.686] (II) Module ati: vendor="X.Org Foundation"
[    30.686] 	compiled for 1.9.0, module version = 6.13.1
[    30.686] 	Module class: X.Org Video Driver
[    30.686] 	ABI class: X.Org Video Driver, version 8.0
[    30.686] (II) LoadModule: "radeon"
[    30.686] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    30.687] (II) Module radeon: vendor="X.Org Foundation"
[    30.687] 	compiled for 1.9.0, module version = 6.13.1
[    30.687] 	Module class: X.Org Video Driver
[    30.687] 	ABI class: X.Org Video Driver, version 8.0
[    30.687] (II) LoadModule: "vesa"
[    30.705] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    30.705] (II) Module vesa: vendor="X.Org Foundation"
[    30.705] 	compiled for 1.8.99.905, module version = 2.3.0
[    30.706] 	Module class: X.Org Video Driver
[    30.706] 	ABI class: X.Org Video Driver, version 8.0
[    30.706] (II) LoadModule: "fbdev"
[    30.706] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    30.706] (II) Module fbdev: vendor="X.Org Foundation"
[    30.706] 	compiled for 1.8.99.905, module version = 0.4.2
[    30.706] 	ABI class: X.Org Video Driver, version 8.0
[    30.706] (II) RADEON: Driver for ATI Radeon chipsets:
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
[    30.715] (II) VESA: driver for VESA chipsets: vesa
[    30.715] (II) FBDEV: driver for framebuffer: fbdev
[    30.715] (++) using VT number 7

[    30.720] (II) [KMS] Kernel modesetting enabled.
[    30.720] (WW) Falling back to old probe method for vesa
[    30.720] (WW) Falling back to old probe method for fbdev
[    30.720] (II) Loading sub module "fbdevhw"
[    30.720] (II) LoadModule: "fbdevhw"
[    30.727] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    30.727] (II) Module fbdevhw: vendor="X.Org Foundation"
[    30.727] 	compiled for 1.9.0, module version = 0.0.2
[    30.727] 	ABI class: X.Org Video Driver, version 8.0
[    30.727] (II) RADEON(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    30.727] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    30.727] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    30.727] (==) RADEON(0): Default visual is TrueColor
[    30.727] (==) RADEON(0): RGB weight 888
[    30.727] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    30.727] (--) RADEON(0): Chipset: "ATI Radeon 9600 AP (AGP)" (ChipID = 0x4150)
[    30.728] (II) RADEON(0): AGP card detected
[    30.728] (II) RADEON(0): KMS Color Tiling: enabled
[    30.728] drmOpenDevice: node name is /dev/dri/card0
[    30.728] drmOpenDevice: open result is 8, (OK)
[    30.728] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[    30.728] drmOpenDevice: node name is /dev/dri/card0
[    30.728] drmOpenDevice: open result is 8, (OK)
[    30.728] drmOpenByBusid: drmOpenMinor returns 8
[    30.728] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[    30.737] (II) RADEON(0): Output VGA-0 has no monitor section
[    30.838] (II) RADEON(0): Output DVI-0 has no monitor section
[    30.875] (II) RADEON(0): Output S-video has no monitor section
[    30.887] (II) RADEON(0): EDID for output VGA-0
[    31.099] (II) RADEON(0): EDID for output DVI-0
[    31.099] (II) RADEON(0): Manufacturer: DEL  Model: 4013  Serial#: 1195721784
[    31.099] (II) RADEON(0): Year: 2006  Week: 38
[    31.099] (II) RADEON(0): EDID Version: 1.3
[    31.099] (II) RADEON(0): Digital Display Input
[    31.099] (II) RADEON(0): Max Image Size [cm]: horiz.: 34  vert.: 27
[    31.099] (II) RADEON(0): Gamma: 2.20
[    31.099] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off
[    31.099] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    31.099] (II) RADEON(0): Default color space is primary color space
[    31.099] (II) RADEON(0): First detailed timing is preferred mode
[    31.099] (II) RADEON(0): redX: 0.635 redY: 0.342   greenX: 0.292 greenY: 0.611
[    31.099] (II) RADEON(0): blueX: 0.147 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
[    31.099] (II) RADEON(0): Supported established timings:
[    31.099] (II) RADEON(0): 720x400@70Hz
[    31.099] (II) RADEON(0): 640x480@60Hz
[    31.099] (II) RADEON(0): 640x480@75Hz
[    31.099] (II) RADEON(0): 800x600@60Hz
[    31.099] (II) RADEON(0): 800x600@75Hz
[    31.099] (II) RADEON(0): 1024x768@60Hz
[    31.099] (II) RADEON(0): 1024x768@75Hz
[    31.099] (II) RADEON(0): 1280x1024@75Hz
[    31.099] (II) RADEON(0): Manufacturer's mask: 0
[    31.099] (II) RADEON(0): Supported standard timings:
[    31.099] (II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    31.099] (II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    31.099] (II) RADEON(0): Supported detailed timing:
[    31.099] (II) RADEON(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
[    31.099] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
[    31.099] (II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[    31.099] (II) RADEON(0): Serial No: CC28069IGED8
[    31.099] (II) RADEON(0): Monitor name: DELL 1707FP
[    31.099] (II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 81 kHz, PixClock max 145 MHz
[    31.099] (II) RADEON(0): EDID (in hex):
[    31.099] (II) RADEON(0): 	00ffffffffffff0010ac134038444547
[    31.099] (II) RADEON(0): 	2610010380221b78eeaec5a2574a9c25
[    31.099] (II) RADEON(0): 	125054a54b00714f8180010101010101
[    31.099] (II) RADEON(0): 	010101010101302a009851002a403070
[    31.099] (II) RADEON(0): 	1300520e1100001e000000ff00434332
[    31.099] (II) RADEON(0): 	3830363949474544380a000000fc0044
[    31.107] (II) RADEON(0): 	454c4c203137303746500a20000000fd
[    31.107] (II) RADEON(0): 	00384c1e510e000a202020202020003c
[    31.107] (II) RADEON(0): Printing probed modes for output DVI-0
[    31.107] (II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    31.107] (II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    31.107] (II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    31.107] (II) RADEON(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
[    31.107] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    31.107] (II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    31.107] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    31.107] (II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    31.107] (II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    31.107] (II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    31.181] (II) RADEON(0): EDID for output S-video
[    31.181] (II) RADEON(0): Output VGA-0 disconnected
[    31.181] (II) RADEON(0): Output DVI-0 connected
[    31.181] (II) RADEON(0): Output S-video disconnected
[    31.181] (II) RADEON(0): Using exact sizes for initial modes
[    31.181] (II) RADEON(0): Output DVI-0 using initial mode 1280x1024
[    31.181] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    31.181] (II) RADEON(0): mem size init: gart size :7dff000 vram size: s:8000000 visible:7ac0000
[    31.181] (II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
[    31.181] (==) RADEON(0): DPI set to (96, 96)
[    31.181] (II) Loading sub module "fb"
[    31.181] (II) LoadModule: "fb"
[    31.182] (II) Loading /usr/lib/xorg/modules/libfb.so
[    31.182] (II) Module fb: vendor="X.Org Foundation"
[    31.182] 	compiled for 1.9.0, module version = 1.0.0
[    31.182] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    31.182] (II) Loading sub module "ramdac"
[    31.182] (II) LoadModule: "ramdac"
[    31.182] (II) Module "ramdac" already built-in
[    31.182] (II) Loading sub module "exa"
[    31.182] (II) LoadModule: "exa"
[    31.183] (II) Loading /usr/lib/xorg/modules/libexa.so
[    31.183] (II) Module exa: vendor="X.Org Foundation"
[    31.183] 	compiled for 1.9.0, module version = 2.5.0
[    31.183] 	ABI class: X.Org Video Driver, version 8.0
[    31.183] (II) UnloadModule: "vesa"
[    31.183] (II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    31.183] (II) UnloadModule: "fbdev"
[    31.183] (II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    31.183] (II) UnloadModule: "fbdevhw"
[    31.183] (II) Unloading /usr/lib/xorg/modules/libfbdevhw.so
[    31.183] (--) Depth 24 pixmap format is 32 bpp
[    31.183] (II) RADEON(0): [DRI2] Setup complete
[    31.183] (II) RADEON(0): [DRI2]   DRI driver: r300
[    31.184] (II) RADEON(0): Front buffer size: 5120K
[    31.184] (II) RADEON(0): VRAM usage limit set to 108518K
[    31.184] (==) RADEON(0): Backing store disabled
[    31.184] (II) RADEON(0): Direct rendering enabled
[    31.184] (II) RADEON(0): Render acceleration enabled for R300/R400/R500 type cards.
[    31.184] (II) RADEON(0): Setting EXA maxPitchBytes
[    31.184] (II) EXA(0): Driver allocated offscreen pixmaps
[    31.184] (II) EXA(0): Driver registered support for the following operations:
[    31.184] (II)         Solid
[    31.184] (II)         Copy
[    31.184] (II)         Composite (RENDER acceleration)
[    31.184] (II)         UploadToScreen
[    31.184] (II)         DownloadFromScreen
[    31.184] (II) RADEON(0): Acceleration enabled
[    31.184] (==) RADEON(0): DPMS enabled
[    31.184] (==) RADEON(0): Silken mouse enabled
[    31.185] (II) RADEON(0): Set up textured video
[    31.185] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    31.185] (--) RandR disabled
[    31.185] (II) Initializing built-in extension Generic Event Extension
[    31.185] (II) Initializing built-in extension SHAPE
[    31.185] (II) Initializing built-in extension MIT-SHM
[    31.185] (II) Initializing built-in extension XInputExtension
[    31.185] (II) Initializing built-in extension XTEST
[    31.185] (II) Initializing built-in extension BIG-REQUESTS
[    31.185] (II) Initializing built-in extension SYNC
[    31.185] (II) Initializing built-in extension XKEYBOARD
[    31.185] (II) Initializing built-in extension XC-MISC
[    31.185] (II) Initializing built-in extension SECURITY
[    31.185] (II) Initializing built-in extension XINERAMA
[    31.185] (II) Initializing built-in extension XFIXES
[    31.185] (II) Initializing built-in extension RENDER
[    31.185] (II) Initializing built-in extension RANDR
[    31.185] (II) Initializing built-in extension COMPOSITE
[    31.185] (II) Initializing built-in extension DAMAGE
[    31.185] (II) Initializing built-in extension GESTURE
[    31.266] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    31.266] (II) AIGLX: enabled GLX_INTEL_swap_event
[    31.266] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    31.266] (II) AIGLX: enabled GLX_SGI_make_current_read
[    31.266] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    31.267] (II) AIGLX: Loaded and initialized /usr/lib/dri/r300_dri.so
[    31.267] (II) GLX: Initialized DRI2 GL provider for screen 0
[    31.268] (II) RADEON(0): Setting screen physical size to 338 x 270
[    31.357] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    31.385] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    31.385] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    31.385] (II) LoadModule: "evdev"
[    31.386] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    31.386] (II) Module evdev: vendor="X.Org Foundation"
[    31.386] 	compiled for 1.9.0, module version = 2.3.2
[    31.386] 	Module class: X.Org XInput Driver
[    31.386] 	ABI class: X.Org XInput driver, version 11.0
[    31.386] (**) Power Button: always reports core events
[    31.386] (**) Power Button: Device: "/dev/input/event2"
[    31.387] (II) Power Button: Found keys
[    31.387] (II) Power Button: Configuring as keyboard
[    31.387] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    31.387] (**) Option "xkb_rules" "evdev"
[    31.387] (**) Option "xkb_model" "pc105"
[    31.387] (**) Option "xkb_layout" "us"
[    31.389] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    31.389] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    31.389] (**) Power Button: always reports core events
[    31.390] (**) Power Button: Device: "/dev/input/event0"
[    31.390] (II) Power Button: Found keys
[    31.390] (II) Power Button: Configuring as keyboard
[    31.390] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    31.390] (**) Option "xkb_rules" "evdev"
[    31.390] (**) Option "xkb_model" "pc105"
[    31.390] (**) Option "xkb_layout" "us"
[    31.391] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    31.391] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    31.391] (**) Sleep Button: always reports core events
[    31.391] (**) Sleep Button: Device: "/dev/input/event1"
[    31.391] (II) Sleep Button: Found keys
[    31.391] (II) Sleep Button: Configuring as keyboard
[    31.391] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    31.391] (**) Option "xkb_rules" "evdev"
[    31.391] (**) Option "xkb_model" "pc105"
[    31.391] (**) Option "xkb_layout" "us"
[    31.394] (II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/event4)
[    31.394] (**) Logitech USB-PS/2 Optical Mouse: Applying InputClass "evdev pointer catchall"
[    31.394] (**) Logitech USB-PS/2 Optical Mouse: always reports core events
[    31.394] (**) Logitech USB-PS/2 Optical Mouse: Device: "/dev/input/event4"
[    31.395] (II) Logitech USB-PS/2 Optical Mouse: Found 12 mouse buttons
[    31.395] (II) Logitech USB-PS/2 Optical Mouse: Found scroll wheel(s)
[    31.395] (II) Logitech USB-PS/2 Optical Mouse: Found relative axes
[    31.395] (II) Logitech USB-PS/2 Optical Mouse: Found x and y relative axes
[    31.395] (II) Logitech USB-PS/2 Optical Mouse: Configuring as mouse
[    31.395] (**) Logitech USB-PS/2 Optical Mouse: YAxisMapping: buttons 4 and 5
[    31.395] (**) Logitech USB-PS/2 Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    31.395] (II) XINPUT: Adding extended input device "Logitech USB-PS/2 Optical Mouse" (type: MOUSE)
[    31.395] (II) Logitech USB-PS/2 Optical Mouse: initialized for relative axes.
[    31.396] (II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/mouse0)
[    31.396] (II) No input driver/identifier specified (ignoring)
[    31.411] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    31.411] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    31.411] (**) AT Translated Set 2 keyboard: always reports core events
[    31.411] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    31.411] (II) AT Translated Set 2 keyboard: Found keys
[    31.411] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    31.411] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    31.411] (**) Option "xkb_rules" "evdev"
[    31.411] (**) Option "xkb_model" "pc105"
[    31.411] (**) Option "xkb_layout" "us"
[    45.920] (II) RADEON(0): EDID vendor "DEL", prod id 16403
[    45.920] (II) RADEON(0): Using EDID range info for horizontal sync
[    45.920] (II) RADEON(0): Using EDID range info for vertical refresh
[    45.920] (II) RADEON(0): Printing DDC gathered Modelines:
[    45.920] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    45.920] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    45.920] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    45.920] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    45.920] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    45.920] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    45.920] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    45.921] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    45.921] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    45.921] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    82.383] (II) RADEON(0): EDID vendor "DEL", prod id 16403
[    82.424] (II) RADEON(0): Using hsync ranges from config file
[    82.424] (II) RADEON(0): Using vrefresh ranges from config file
[    82.424] (II) RADEON(0): Printing DDC gathered Modelines:
[    82.424] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    82.424] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    82.424] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    82.424] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    82.424] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    82.424] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    82.424] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    82.424] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    82.424] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    82.424] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   149.973] (II) config/udev: Adding input device Sony PLAYSTATION(R)3 Controller (/dev/input/event5)
[   149.973] (**) Sony PLAYSTATION(R)3 Controller: Applying InputClass "DualShock3"
[   149.973] (II) LoadModule: "joystick"
[   149.973] (II) Loading /usr/lib/xorg/modules/input/joystick_drv.so
[   149.973] (II) Module joystick: vendor="X.Org Foundation"
[   149.974] 	compiled for 1.8.99.905, module version = 1.5.0
[   149.974] 	Module class: X.Org XInput Driver
[   149.974] 	ABI class: X.Org XInput driver, version 11.0
[   149.974] (**) Option "Device" "/dev/input/event5"
[   149.974] (**) Option "SendCoreEvents" "true"
[   149.974] (**) Sony PLAYSTATION(R)3 Controller: always reports core events
[   149.974] (**) Option "MapButton1" "button=4"
[   149.974] (**) Option "MapButton2" "key=64"
[   149.974] (**) Option "MapButton3" "key=133"
[   149.974] (**) Option "MapButton4" "button=5"
[   149.974] (**) Option "MapButton5" "key=111"
[   149.974] (**) Option "MapButton6" "key=114"
[   149.974] (**) Option "MapButton7" "key=116"
[   149.974] (**) Option "MapButton8" "key=113"
[   149.974] (**) Option "MapButton9" "key=50"
[   149.974] (**) Option "MapButton10" "button=1"
[   149.974] (**) Option "MapButton11" "key=37"
[   149.974] (**) Option "MapButton12" "button=0"
[   149.974] (**) Option "MapButton13" "button=2"
[   149.975] (**) Option "MapButton14" "key=119"
[   149.975] (**) Option "MapButton15" "key=36"
[   149.975] (**) Option "MapButton16" "key=23"
[   149.975] (**) Option "MapAxis1" "none"
[   149.975] (**) Option "MapAxis2" "none"
[   149.975] (**) Option "MapAxis3" "mode=relative axis=.1x"
[   149.975] (**) Option "MapAxis4" "mode=relative axis=.1y"
[   149.975] (**) Option "MapAxis5" "none"
[   149.975] (**) Option "MapAxis6" "none"
[   149.975] (**) Option "SendCoreEvents" "true"
[   149.975] (**) Sony PLAYSTATION(R)3 Controller (keys): always reports core events
[   149.975] (II) XINPUT: Adding extended input device "Sony PLAYSTATION(R)3 Controller" (type: JOYSTICK)
[   149.982] (II) Joystick: Sony PLAYSTATION(R)3 Controller. bus 0x3 vendor 0x54c product 0x268 version 0x111
[   149.982] (II) Joystick: found 27 axes, 19 buttons
[   149.982] (II) XINPUT: Adding extended input device "Sony PLAYSTATION(R)3 Controller (keys)" (type: JOYSTICK)
[   149.986] (II) XKB: reuse xkmfile /var/lib/xkb/server-D378AD8F86E560F712A83EE36E4E5E92C595B9BD.xkm
[   150.014] JOYSTICK: DebugLevel set to 0
[   150.164] (II) config/udev: Adding input device Sony PLAYSTATION(R)3 Controller (/dev/input/js0)
[   150.164] (**) Sony PLAYSTATION(R)3 Controller: Applying InputClass "DualShock3"
[   150.164] (**) Option "Device" "/dev/input/js0"
[   150.164] (**) Option "SendCoreEvents" "true"
[   150.164] (**) Sony PLAYSTATION(R)3 Controller: always reports core events
[   150.164] (**) Option "MapButton1" "button=4"
[   150.164] (**) Option "MapButton2" "key=64"
[   150.164] (**) Option "MapButton3" "key=133"
[   150.164] (**) Option "MapButton4" "button=5"
[   150.164] (**) Option "MapButton5" "key=111"
[   150.165] (**) Option "MapButton6" "key=114"
[   150.165] (**) Option "MapButton7" "key=116"
[   150.165] (**) Option "MapButton8" "key=113"
[   150.165] (**) Option "MapButton9" "key=50"
[   150.165] (**) Option "MapButton10" "button=1"
[   150.165] (**) Option "MapButton11" "key=37"
[   150.165] (**) Option "MapButton12" "button=0"
[   150.165] (**) Option "MapButton13" "button=2"
[   150.165] (**) Option "MapButton14" "key=119"
[   150.165] (**) Option "MapButton15" "key=36"
[   150.165] (**) Option "MapButton16" "key=23"
[   150.165] (**) Option "MapAxis1" "none"
[   150.165] (**) Option "MapAxis2" "none"
[   150.165] (**) Option "MapAxis3" "mode=relative axis=.1x"
[   150.165] (**) Option "MapAxis4" "mode=relative axis=.1y"
[   150.165] (**) Option "MapAxis5" "none"
[   150.165] (**) Option "MapAxis6" "none"
[   150.166] (**) Option "SendCoreEvents" "true"
[   150.166] (**) Sony PLAYSTATION(R)3 Controller (keys): always reports core events
[   150.166] (II) XINPUT: Adding extended input device "Sony PLAYSTATION(R)3 Controller" (type: JOYSTICK)
[   150.166] (EE) Joystick: ioctl EVIOCGVERSION on '/dev/input/js0' failed: Invalid argument
[   150.166] (II) Joystick: Sony PLAYSTATION(R)3 Controller. 28 axes, 19 buttons
[   150.166] (II) XINPUT: Adding extended input device "Sony PLAYSTATION(R)3 Controller (keys)" (type: JOYSTICK)
[   150.166] JOYSTICK: DebugLevel set to 0

```

---

### Post by tipp98 on 2010-10-19
ok, it's whipped. According to my log it seem that js0 had one more axis, probably accounting for the different behavior in xinput :/   I added another match clause to ignore /dev/inpu/js* devices. Seems to be functioning as configured now. Here it is. This goes in /etc/X11/xorg.conf.d/10-dualshock3.conf
```

Section "InputClass"
    Identifier    "DualShock3"
    MatchProduct    "Sony PLAYSTATION(R)3 Controller"
    MatchDevicePath "/dev/input/event*" 
    Driver        "joystick"
    Option "MapAxis1" "mode=relative axis=+1.25zx" # deadzone=500"
    Option "MapAxis2" "mode=relative axis=+1.25zy" # deadzone=500"
    Option "MapAxis3" "mode=relative axis=+1.75x" # deadzone=500"
    Option "MapAxis4" "mode=relative axis=+1.75y" # deadzone=500"
    Option "MapAxis5" "none"
    Option "MapAxis6" "none"

    Option "MapButton1" "key=119"    #Select=delete
    Option "MapButton2" "key=50"    #L3=shift
    Option "MapButton3" "key=133"    #R3=super
    Option "MapButton4" "key=36"    #start=enter
    Option "MapButton5" "key=111"    #up
    Option "MapButton6" "key=114"    #right
    Option "MapButton7" "key=116"    #down
    Option "MapButton8" "key=113"    #left
    Option "MapButton9" "key=64"    #L2=alt
    Option "MapButton10" "button=3    #R2=right click
    Option "MapButton11" "key=37"    #L1=ctrl
    Option "MapButton12" "button=1"    #R1=left click
    Option "MapButton13" "button=2"    #tri=middle click
    Option "MapButton14" "key=9"    #circle=ESC
    Option "MapButton15" "key=65"    #cross=space
    Option "MapButton16" "key=23"    #square=tab
    Option "MapButton17" "none"    #PS=osk/dasher?
EndSection

```

There's just one small thing that bugs me and that is the performance. It doesn't seem responsive to direction changes. For instance, if I move the stick in a smooth circle, it kinda makes the cursor do a square. It just doesn't seem right.

---

### Post by starscalling on 2010-12-02
> **tipp98 said:**
> ok, it's whipped. According to my log it seem that js0 had one more axis, probably accounting for the different behavior in xinput :/   I added another match clause to ignore /dev/inpu/js* devices. Seems to be functioning as configured now. Here it is. This goes in /etc/X11/xorg.conf.d/10-dualshock3.conf
```

Section "InputClass"
    Identifier    "DualShock3"
    MatchProduct    "Sony PLAYSTATION(R)3 Controller"
    MatchDevicePath "/dev/input/event*" 
    Driver        "joystick"
    Option "MapAxis1" "mode=relative axis=+1.25zx" # deadzone=500"
    Option "MapAxis2" "mode=relative axis=+1.25zy" # deadzone=500"
    Option "MapAxis3" "mode=relative axis=+1.75x" # deadzone=500"
    Option "MapAxis4" "mode=relative axis=+1.75y" # deadzone=500"
    Option "MapAxis5" "none"
    Option "MapAxis6" "none"

    Option "MapButton1" "key=119"    #Select=delete
    Option "MapButton2" "key=50"    #L3=shift
    Option "MapButton3" "key=133"    #R3=super
    Option "MapButton4" "key=36"    #start=enter
    Option "MapButton5" "key=111"    #up
    Option "MapButton6" "key=114"    #right
    Option "MapButton7" "key=116"    #down
    Option "MapButton8" "key=113"    #left
    Option "MapButton9" "key=64"    #L2=alt
    Option "MapButton10" "button=3    #R2=right click
    Option "MapButton11" "key=37"    #L1=ctrl
    Option "MapButton12" "button=1"    #R1=left click
    Option "MapButton13" "button=2"    #tri=middle click
    Option "MapButton14" "key=9"    #circle=ESC
    Option "MapButton15" "key=65"    #cross=space
    Option "MapButton16" "key=23"    #square=tab
    Option "MapButton17" "none"    #PS=osk/dasher?
EndSection

```

There's just one small thing that bugs me and that is the performance. It doesn't seem responsive to direction changes. For instance, if I move the stick in a smooth circle, it kinda makes the cursor do a square. It just doesn't seem right.

breaks xorg for me


mmmm

ok without the xorg server bit the above works great.

[http://www.x.org/archive/X11R7.5/doc/man/man4/joystick.4.html](http://www.x.org/archive/X11R7.5/doc/man/man4/joystick.4.html)

has further details on modding the above.

---

