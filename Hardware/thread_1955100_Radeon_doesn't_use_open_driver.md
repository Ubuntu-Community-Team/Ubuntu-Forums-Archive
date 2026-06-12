---
title: "Radeon doesn't use open driver"
date: 2012-04-09
forum: Hardware
---

### Post by filippo1 on 2012-04-09
Hello, I just figured out that my radeon mobility 9700 doesn't use the 3d acceleration on lubuntu 11.10.
I tried the command:

LIBGL_DEBUG=verbose glxinfo

and the output says:

OpenGL renderer string: Software Rasterizer

so the 3d acceleration is not in use. How can I ix that?

Thanks to everyone

---

### Post by Paddy Landau on 2012-04-09
I don't know if it can be fixed. I have noticed many people recently posting problems with Radeon. Sorry.

---

### Post by filippo1 on 2012-04-09
well I hope that there is a solution for this, maybe using old catalyst drivers or anything else. 
What about using the old drivers like catalyst 9.2 for older ubuntu versions? would it work?

---

### Post by Mark Phelps on 2012-04-09
Sorry, but your old Radeon card is considered "legacy" by AMD, meaning, they haven't written 3D acceleration drivers for it in years!

The open-source drivers are the ones you should use now -- and they are installed by default.

The last Ubuntu version that supported accelerated 3D drivers was 8.10 -- and you can't use those drivers with more recent Ubuntu versions due to conflicts with the X-server.

---

### Post by filippo1 on 2012-04-10
Thank you for the reply, even if it's a bad one.. now I'll try to focus on the other problem since this one has been "solved".
Thanks again

EDIT: just to be sure, is it correct?
> glxinfo | grep OpenGL
OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string: 2.1 Mesa 7.11
OpenGL shading language version string: 1.20
OpenGL extensions:


---

### Post by Yellow Pasque on 2012-04-10
Post/pastebin your /var/log/Xorg.0.log

---

### Post by filippo1 on 2012-04-10
> [    22.875] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[    22.875] X Protocol Version 11, Revision 0
[    22.875] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[    22.875] Current Operating System: Linux filippo-Aspire-1670 3.0.0-17-generic #30-Ubuntu SMP Thu Mar 8 17:34:21 UTC 2012 i686
[    22.875] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-17-generic root=UUID=564d9d0d-2f36-497d-94c6-fa43d0dc7bae ro quiet splash pcie_apm=force radeon.nomodeset=1 vt.handoff=7
[    22.875] Build Date: 19 October 2011  05:09:41AM
[    22.875] xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    22.875] Current version of pixman: 0.22.2
[    22.875] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[    22.875] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    22.876] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Apr 10 12:36:41 2012
[    22.877] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    22.878] (==) No Layout section.  Using the first Screen section.
[    22.878] (==) No screen section available. Using defaults.
[    22.878] (**) |-->Screen "Default Screen Section" (0)
[    22.878] (**) |   |-->Monitor "<default monitor>"
[    22.879] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    22.879] (==) Automatically adding devices
[    22.879] (==) Automatically enabling devices
[    22.879] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    22.879] 	Entry deleted from font path.
[    22.879] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    22.879] 	Entry deleted from font path.
[    22.879] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    22.879] 	Entry deleted from font path.
[    22.879] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    22.879] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    22.879] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    22.879] (II) Loader magic: 0x823ada0
[    22.879] (II) Module ABI versions:
[    22.879] 	X.Org ANSI C Emulation: 0.4
[    22.879] 	X.Org Video Driver: 10.0
[    22.879] 	X.Org XInput driver : 12.3
[    22.879] 	X.Org Server Extension : 5.0
[    22.880] (--) PCI:*(0:1:5:0) 1002:4e50:1025:0065 rev 0, Mem @ 0xf0000000/134217728, 0xe8100000/65536, I/O @ 0x00009000/256, BIOS @ 0x????????/131072
[    22.881] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    22.881] (II) LoadModule: "extmod"
[    22.905] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    22.905] (II) Module extmod: vendor="X.Org Foundation"
[    22.905] 	compiled for 1.10.4, module version = 1.0.0
[    22.905] 	Module class: X.Org Server Extension
[    22.905] 	ABI class: X.Org Server Extension, version 5.0
[    22.905] (II) Loading extension MIT-SCREEN-SAVER
[    22.905] (II) Loading extension XFree86-VidModeExtension
[    22.905] (II) Loading extension XFree86-DGA
[    22.905] (II) Loading extension DPMS
[    22.906] (II) Loading extension XVideo
[    22.906] (II) Loading extension XVideo-MotionCompensation
[    22.906] (II) Loading extension X-Resource
[    22.906] (II) LoadModule: "dbe"
[    22.906] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    22.906] (II) Module dbe: vendor="X.Org Foundation"
[    22.906] 	compiled for 1.10.4, module version = 1.0.0
[    22.906] 	Module class: X.Org Server Extension
[    22.906] 	ABI class: X.Org Server Extension, version 5.0
[    22.906] (II) Loading extension DOUBLE-BUFFER
[    22.906] (II) LoadModule: "glx"
[    22.907] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    22.907] (II) Module glx: vendor="X.Org Foundation"
[    22.907] 	compiled for 1.10.4, module version = 1.0.0
[    22.907] 	ABI class: X.Org Server Extension, version 5.0
[    22.907] (==) AIGLX enabled
[    22.907] (II) Loading extension GLX
[    22.907] (II) LoadModule: "record"
[    22.908] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    22.908] (II) Module record: vendor="X.Org Foundation"
[    22.908] 	compiled for 1.10.4, module version = 1.13.0
[    22.908] 	Module class: X.Org Server Extension
[    22.908] 	ABI class: X.Org Server Extension, version 5.0
[    22.908] (II) Loading extension RECORD
[    22.908] (II) LoadModule: "dri"
[    22.908] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    22.909] (II) Module dri: vendor="X.Org Foundation"
[    22.909] 	compiled for 1.10.4, module version = 1.0.0
[    22.909] 	ABI class: X.Org Server Extension, version 5.0
[    22.909] (II) Loading extension XFree86-DRI
[    22.909] (II) LoadModule: "dri2"
[    22.909] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    22.910] (II) Module dri2: vendor="X.Org Foundation"
[    22.910] 	compiled for 1.10.4, module version = 1.2.0
[    22.910] 	ABI class: X.Org Server Extension, version 5.0
[    22.910] (II) Loading extension DRI2
[    22.910] (==) Matched fglrx as autoconfigured driver 0
[    22.910] (==) Matched ati as autoconfigured driver 1
[    22.910] (==) Matched vesa as autoconfigured driver 2
[    22.910] (==) Matched fbdev as autoconfigured driver 3
[    22.910] (==) Assigned the driver to the xf86ConfigLayout
[    22.910] (II) LoadModule: "fglrx"
[    22.912] (WW) Warning, couldn't open module fglrx
[    22.912] (II) UnloadModule: "fglrx"
[    22.912] (II) Unloading fglrx
[    22.912] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    22.912] (II) LoadModule: "ati"
[    22.913] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    22.913] (II) Module ati: vendor="X.Org Foundation"
[    22.913] 	compiled for 1.10.2.902, module version = 6.14.99
[    22.913] 	Module class: X.Org Video Driver
[    22.913] 	ABI class: X.Org Video Driver, version 10.0
[    22.913] (II) LoadModule: "radeon"
[    22.914] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    22.914] (II) Module radeon: vendor="X.Org Foundation"
[    22.914] 	compiled for 1.10.2.902, module version = 6.14.99
[    22.914] 	Module class: X.Org Video Driver
[    22.914] 	ABI class: X.Org Video Driver, version 10.0
[    22.914] (II) LoadModule: "vesa"
[    22.915] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    22.915] (II) Module vesa: vendor="X.Org Foundation"
[    22.915] 	compiled for 1.10.2, module version = 2.3.0
[    22.915] 	Module class: X.Org Video Driver
[    22.915] 	ABI class: X.Org Video Driver, version 10.0
[    22.915] (II) LoadModule: "fbdev"
[    22.916] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    22.916] (II) Module fbdev: vendor="X.Org Foundation"
[    22.916] 	compiled for 1.10.0, module version = 0.4.2
[    22.916] 	ABI class: X.Org Video Driver, version 10.0
[    22.916] (II) RADEON: Driver for ATI Radeon chipsets:
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
	ATI Radeon 3000 Graphics, SUMO, SUMO, SUMO2, SUMO2, SUMO2, SUMO2,
	SUMO, SUMO, SUMO, SUMO, SUMO, ATI Radeon HD 4200, ATI Radeon 4100,
	ATI Mobility Radeon HD 4200, ATI Mobility Radeon 4100,
	ATI Radeon HD 4290, ATI Radeon HD 4250, AMD Radeon HD 6310 Graphics,
	AMD Radeon HD 6310 Graphics, AMD Radeon HD 6250 Graphics,
	AMD Radeon HD 6250 Graphics, AMD Radeon HD 6300 Series Graphics,
	AMD Radeon HD 6200 Series Graphics, CYPRESS,
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
	ATI Radeon HD 5450, CEDAR, CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
	CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN, AMD Radeon HD 6900 Series,
	AMD Radeon HD 6900 Series, CAYMAN, CAYMAN, CAYMAN,
	AMD Radeon HD 6900M Series, Mobility Radeon HD 6000 Series, BARTS,
	BARTS, Mobility Radeon HD 6000 Series,
	Mobility Radeon HD 6000 Series, BARTS, BARTS, BARTS, BARTS,
	AMD Radeon HD 6800 Series, AMD Radeon HD 6800 Series,
	AMD Radeon HD 6700 Series, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
	TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, CAICOS,
	CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
	CAICOS, CAICOS, CAICOS
[    22.929] (II) VESA: driver for VESA chipsets: vesa
[    22.929] (II) FBDEV: driver for framebuffer: fbdev
[    22.929] (++) using VT number 7

[    22.930] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    22.930] (II) [KMS] drm report modesetting isn't supported.
[    22.930] (WW) Falling back to old probe method for vesa
[    22.930] (WW) Falling back to old probe method for fbdev
[    22.930] (II) Loading sub module "fbdevhw"
[    22.930] (II) LoadModule: "fbdevhw"
[    22.930] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    22.931] (II) Module fbdevhw: vendor="X.Org Foundation"
[    22.931] 	compiled for 1.10.4, module version = 0.0.2
[    22.931] 	ABI class: X.Org Video Driver, version 10.0
[    22.931] (II) RADEON(0): TOTO SAYS 00000000e8100000
[    22.931] (II) RADEON(0): MMIO registers at 0x00000000e8100000: size 64KB
[    22.931] (II) RADEON(0): PCI bus 1 card 5 func 0
[    22.931] (II) RADEON(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    22.931] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    22.931] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    22.931] (==) RADEON(0): Default visual is TrueColor
[    22.931] (II) Loading sub module "vgahw"
[    22.931] (II) LoadModule: "vgahw"
[    22.933] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    22.934] (II) Module vgahw: vendor="X.Org Foundation"
[    22.934] 	compiled for 1.10.4, module version = 0.1.0
[    22.934] 	ABI class: X.Org Video Driver, version 10.0
[    22.934] (II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
[    22.934] (==) RADEON(0): RGB weight 888
[    22.934] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    22.934] (--) RADEON(0): Chipset: "ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP)" (ChipID = 0x4e50)
[    22.934] (--) RADEON(0): Linear framebuffer at 0x00000000f0000000
[    22.934] (II) RADEON(0): AGP card detected
[    22.935] (II) Loading sub module "int10"
[    22.935] (II) LoadModule: "int10"
[    22.935] (II) Loading /usr/lib/xorg/modules/libint10.so
[    22.936] (II) Module int10: vendor="X.Org Foundation"
[    22.936] 	compiled for 1.10.4, module version = 1.0.0
[    22.936] 	ABI class: X.Org Video Driver, version 10.0
[    22.936] (II) RADEON(0): initializing int10
[    22.937] (II) RADEON(0): Primary V_BIOS segment is: 0xc000
[    22.938] (II) RADEON(0): Legacy BIOS detected
[    22.938] drmOpenDevice: node name is /dev/dri/card0
[    23.008] [drm] failed to load kernel module "radeon"
[    23.008] (EE) RADEON(0): [dri] RADEONDRIGetVersion failed to open the DRM
[dri] Disabling DRI.
[    23.008] (II) RADEON(0): Generation 2 PCI interface, using max accessible memory
[    23.008] (II) RADEON(0): Detected total video RAM=65536K, accessible=131072K (PCI BAR=131072K)
[    23.008] (--) RADEON(0): Mapped VideoRAM: 65536 kByte (128 bit DDR SDRAM)
[    23.008] (II) RADEON(0): Color tiling enabled by default
[    23.008] (II) Loading sub module "ddc"
[    23.008] (II) LoadModule: "ddc"
[    23.008] (II) Module "ddc" already built-in
[    23.008] (II) Loading sub module "i2c"
[    23.008] (II) LoadModule: "i2c"
[    23.008] (II) Module "i2c" already built-in
[    23.009] (II) RADEON(0): ref_freq: 2700, min_out_pll: 20000, max_out_pll: 40000, min_in_pll: 40, max_in_pll: 3000, xclk: 20000, sclk: 390.000000, mclk: 200.000000
[    23.009] (II) RADEON(0): PLL parameters: rf=2700 rd=12 min=20000 max=40000; xclk=20000
[    23.009] (II) RADEON(0): Panel ID string: HTC                     
[    23.009] (II) RADEON(0): Panel Size from BIOS: 1280x800
[    23.009] (II) RADEON(0): BIOS provided dividers will be used.
[    23.009] (WW) RADEON(0): LVDS Info:
XRes: 1280, YRes: 800, DotClock: 71000
HBlank: 160, HOverPlus: 48, HSyncWidth: 32
VBlank: 23, VOverPlus: 2, VSyncWidth: 6
[    23.009] (II) RADEON(0): Output VGA-0 has no monitor section
[    23.009] (II) RADEON(0): I2C bus "VGA-0" initialized.
[    23.009] (II) RADEON(0): Output LVDS has no monitor section
[    23.009] (II) RADEON(0): Output S-video has no monitor section
[    23.009] (II) RADEON(0): Default TV standard: NTSC
[    23.009] (II) RADEON(0): TV standards supported by chip: NTSC PAL 
[    23.009] (II) RADEON(0): Port0:
[    23.009]   XRANDR name: VGA-0
[    23.009]   Connector: VGA
[    23.009]   CRT1: INTERNAL_DAC1
[    23.009]   DDC reg: 0x60
[    23.009] (II) RADEON(0): Port1:
[    23.009]   XRANDR name: LVDS
[    23.009]   Connector: LVDS
[    23.009]   LCD1: INTERNAL_LVDS
[    23.009]   DDC reg: 0x0
[    23.009] (II) RADEON(0): Port2:
[    23.009]   XRANDR name: S-video
[    23.009]   Connector: S-video
[    23.009]   TV1: INTERNAL_DAC2
[    23.009]   DDC reg: 0x0
[    23.009] (II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
[    23.015] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[    23.015] finished output detect: 0
[    23.015] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[    23.015] finished output detect: 1
[    23.015] (II) RADEON(0): Output: S-video, Detected Monitor Type: 0
[    23.015] finished output detect: 2
[    23.015] finished all detect
[    23.021] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[    23.021] (II) RADEON(0): EDID for output VGA-0
[    23.021] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[    23.021] (II) RADEON(0): Added native panel mode: 1280x800
[    23.021] (II) RADEON(0): Printing probed modes for output LVDS
[    23.021] (II) RADEON(0): Modeline "1280x800"x59.9   71.00  1280 1328 1360 1440  800 802 808 823 (49.3 kHz)
[    23.021] (II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
[    23.021] (II) RADEON(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
[    23.021] (II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
[    23.021] (II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
[    23.021] (II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
[    23.021] (II) RADEON(0): Output: S-video, Detected Monitor Type: 0
[    23.021] (II) RADEON(0): EDID for output S-video
[    23.021] (II) RADEON(0): Output VGA-0 disconnected
[    23.021] (II) RADEON(0): Output LVDS connected
[    23.021] (II) RADEON(0): Output S-video disconnected
[    23.022] (II) RADEON(0): Using exact sizes for initial modes
[    23.022] (II) RADEON(0): Output LVDS using initial mode 1280x800
[    23.022] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    23.022] (==) RADEON(0): DPI set to (96, 96)
[    23.022] (II) Loading sub module "fb"
[    23.022] (II) LoadModule: "fb"
[    23.022] (II) Loading /usr/lib/xorg/modules/libfb.so
[    23.022] (II) Module fb: vendor="X.Org Foundation"
[    23.022] 	compiled for 1.10.4, module version = 1.0.0
[    23.023] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    23.023] (II) Loading sub module "ramdac"
[    23.023] (II) LoadModule: "ramdac"
[    23.023] (II) Module "ramdac" already built-in
[    23.023] (==) RADEON(0): Using XAA acceleration architecture
[    23.023] (II) Loading sub module "xaa"
[    23.023] (II) LoadModule: "xaa"
[    23.023] (II) Loading /usr/lib/xorg/modules/libxaa.so
[    23.023] (II) Module xaa: vendor="X.Org Foundation"
[    23.023] 	compiled for 1.10.4, module version = 1.2.1
[    23.023] 	ABI class: X.Org Video Driver, version 10.0
[    23.023] (==) RADEON(0): Assuming overlay scaler buffer width is 1920
[    23.023] (II) RADEON(0): No MM_TABLE found - assuming CARD is not TV-in capable.
[    23.023] (!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
[    23.023] (II) UnloadModule: "vesa"
[    23.023] (II) Unloading vesa
[    23.023] (II) UnloadModule: "fbdev"
[    23.023] (II) Unloading fbdev
[    23.024] (II) UnloadModule: "fbdevhw"
[    23.024] (II) Unloading fbdevhw
[    23.024] (--) Depth 24 pixmap format is 32 bpp
[    23.024] (II) RADEON(0): RADEONScreenInit f0000000 0 0
[    23.041] Entering TV Save
[    23.041] Save TV timing tables
[    23.041] saveTimingTables: reading timing tables
[    23.041] TV Save done
[    24.041] (II) RADEON(0): Dynamic Power Management Disabled
[    24.041] (II) RADEON(0): RADEONInitMemoryMap() : 
[    24.041] (II) RADEON(0):   mem_size         : 0x04000000
[    24.041] (II) RADEON(0):   MC_FB_LOCATION   : 0xf3fff000
[    24.041] (II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
[    24.041] (II) RADEON(0): Depth moves disabled by default
[    24.041] (II) RADEON(0): Memory manager initialized to (0,0) (1280,8191)
[    24.041] (II) RADEON(0): Reserved area from (0,1280) to (1280,1282)
[    24.041] (II) RADEON(0): Largest offscreen area available: 1280 x 6909
[    24.041] (II) RADEON(0): RADEONRestoreMemMapRegisters() : 
[    24.041] (II) RADEON(0):   MC_FB_LOCATION   : 0xf3fff000 0x1fff0000
[    24.041] (II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
[    24.242] (==) RADEON(0): Backing store disabled
[    24.242] (WW) RADEON(0): Direct rendering disabled
[    24.242] (II) RADEON(0): Render acceleration disabled
[    24.242] (II) RADEON(0): num quad-pipes is 1
[    24.242] (II) RADEON(0): Using XFree86 Acceleration Architecture (XAA)
[    24.242] 	Screen to screen bit blits
[    24.242] 	Solid filled rectangles
[    24.242] 	8x8 mono pattern filled rectangles
[    24.242] 	Indirect CPU to Screen color expansion
[    24.242] 	Solid Lines
[    24.242] 	Scanline Image Writes
[    24.242] 	Setting up tile and stipple cache:
[    24.242] 		32 128x128 slots
[    24.242] 		32 256x256 slots
[    24.242] 		16 512x512 slots
[    24.242] (II) RADEON(0): Acceleration enabled
[    24.242] (==) RADEON(0): DPMS enabled
[    24.242] (==) RADEON(0): Silken mouse enabled
[    24.242] (II) RADEON(0): Will use 32 kb for hardware cursor 0 at offset 0x00642800
[    24.242] (II) RADEON(0): Will use 32 kb for hardware cursor 1 at offset 0x00647800
[    24.242] (II) RADEON(0): Largest offscreen area available: 1280 x 6901
[    24.242] (II) RADEON(0): No video input capabilities detected and no information is provided - disabling multimedia i2c
[    24.242] (II) Loading sub module "theatre_detect"
[    24.242] (II) LoadModule: "theatre_detect"
[    24.243] (II) Loading /usr/lib/xorg/modules/multimedia/theatre_detect_drv.so
[    24.243] (II) Module theatre_detect: vendor="X.Org Foundation"
[    24.243] 	compiled for 1.10.2.902, module version = 1.0.0
[    24.243] 	ABI class: X.Org Video Driver, version 10.0
[    24.243] (II) RADEON(0): no multimedia table present, disabling Rage Theatre.
[    24.243] (II) RADEON(0): Set up overlay video
[    24.243] (II) RADEON(0): Set up textured video
[    24.244] (II) RADEON(0): [XvMC] Associated with Radeon Textured Video.
[    24.244] (II) RADEON(0): [XvMC] Extension initialized.
[    24.281] disable primary dac
[    25.281] disable TV
[    26.281] init memmap
[    26.281] init common
[    26.281] init crtc1
[    26.281] init pll1
[    26.281] restore memmap
[    26.281] (II) RADEON(0): RADEONRestoreMemMapRegisters() : 
[    26.281] (II) RADEON(0):   MC_FB_LOCATION   : 0xf3fff000 0xf3fff000
[    26.281] (II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
[    26.381] restore common
[    26.381] restore crtc1
[    26.381] restore pll1
[    26.381] set RMX
[    26.381] set LVDS
[    26.381] enable LVDS
[    27.382] disable primary dac
[    27.382] disable TV
[    27.382] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    27.382] (--) RandR disabled
[    27.382] (II) Initializing built-in extension Generic Event Extension
[    27.382] (II) Initializing built-in extension SHAPE
[    27.382] (II) Initializing built-in extension MIT-SHM
[    27.382] (II) Initializing built-in extension XInputExtension
[    27.382] (II) Initializing built-in extension XTEST
[    27.382] (II) Initializing built-in extension BIG-REQUESTS
[    27.382] (II) Initializing built-in extension SYNC
[    27.382] (II) Initializing built-in extension XKEYBOARD
[    27.382] (II) Initializing built-in extension XC-MISC
[    27.382] (II) Initializing built-in extension SECURITY
[    27.382] (II) Initializing built-in extension XINERAMA
[    27.382] (II) Initializing built-in extension XFIXES
[    27.382] (II) Initializing built-in extension RENDER
[    27.382] (II) Initializing built-in extension RANDR
[    27.382] (II) Initializing built-in extension COMPOSITE
[    27.382] (II) Initializing built-in extension DAMAGE
[    27.382] (II) Initializing built-in extension GESTURE
[    27.396] (II) AIGLX: Screen 0 is not DRI2 capable
[    27.396] (II) AIGLX: Screen 0 is not DRI capable
[    27.397] (II) AIGLX: Trying DRI driver /usr/lib/i386-linux-gnu/dri/swrast_dri.so
[    27.402] (II) AIGLX: Loaded and initialized swrast
[    27.402] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    27.403] (II) RADEON(0): Setting screen physical size to 338 x 211
[    27.428] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    27.443] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    27.443] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    27.443] (II) LoadModule: "evdev"
[    27.443] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    27.445] (II) Module evdev: vendor="X.Org Foundation"
[    27.445] 	compiled for 1.10.2, module version = 2.6.0
[    27.445] 	Module class: X.Org XInput Driver
[    27.445] 	ABI class: X.Org XInput driver, version 12.3
[    27.445] (II) Using input driver 'evdev' for 'Power Button'
[    27.445] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    27.445] (**) Power Button: always reports core events
[    27.445] (**) Power Button: Device: "/dev/input/event2"
[    27.445] (--) Power Button: Found keys
[    27.445] (II) Power Button: Configuring as keyboard
[    27.445] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    27.445] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    27.445] (**) Option "xkb_rules" "evdev"
[    27.445] (**) Option "xkb_model" "pc105"
[    27.445] (**) Option "xkb_layout" "it"
[    27.449] (II) XKB: reuse xkmfile /var/lib/xkb/server-3781FECB9CB8D26EE03343DB2C93394EA704B98F.xkm
[    27.480] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[    27.480] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    27.480] (II) Using input driver 'evdev' for 'Video Bus'
[    27.480] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    27.480] (**) Video Bus: always reports core events
[    27.480] (**) Video Bus: Device: "/dev/input/event4"
[    27.480] (--) Video Bus: Found keys
[    27.481] (II) Video Bus: Configuring as keyboard
[    27.481] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:12/LNXVIDEO:00/input/input4/event4"
[    27.481] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    27.481] (**) Option "xkb_rules" "evdev"
[    27.481] (**) Option "xkb_model" "pc105"
[    27.481] (**) Option "xkb_layout" "it"
[    27.482] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    27.482] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    27.482] (II) Using input driver 'evdev' for 'Power Button'
[    27.482] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    27.482] (**) Power Button: always reports core events
[    27.482] (**) Power Button: Device: "/dev/input/event1"
[    27.482] (--) Power Button: Found keys
[    27.482] (II) Power Button: Configuring as keyboard
[    27.482] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[    27.482] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    27.482] (**) Option "xkb_rules" "evdev"
[    27.482] (**) Option "xkb_model" "pc105"
[    27.482] (**) Option "xkb_layout" "it"
[    27.483] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    27.483] (II) No input driver/identifier specified (ignoring)
[    27.491] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    27.491] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    27.492] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    27.492] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    27.492] (**) AT Translated Set 2 keyboard: always reports core events
[    27.492] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    27.492] (--) AT Translated Set 2 keyboard: Found keys
[    27.492] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    27.492] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    27.492] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    27.492] (**) Option "xkb_rules" "evdev"
[    27.492] (**) Option "xkb_model" "pc105"
[    27.492] (**) Option "xkb_layout" "it"
[    27.493] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event5)
[    27.493] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    27.493] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    27.494] (II) LoadModule: "synaptics"
[    27.494] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    27.494] (II) Module synaptics: vendor="X.Org Foundation"
[    27.494] 	compiled for 1.10.4, module version = 1.4.1
[    27.494] 	Module class: X.Org XInput Driver
[    27.494] 	ABI class: X.Org XInput driver, version 12.3
[    27.494] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    27.494] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    27.494] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    27.494] (**) Option "Device" "/dev/input/event5"
[    27.500] (--) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[    27.500] (--) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[    27.500] (--) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    27.500] (--) SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    27.500] (--) SynPS/2 Synaptics TouchPad: buttons: left right double triple scroll-buttons
[    27.516] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    27.516] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    27.516] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio4/input/input5/event5"
[    27.516] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    27.516] (**) SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    27.516] (**) SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[    27.516] (**) SynPS/2 Synaptics TouchPad: AccelFactor is now 0.040
[    27.516] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    27.516] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    27.516] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    27.516] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    27.517] (II) SynPS/2 Synaptics TouchPad: failed to open grail, no gesture support
[    27.517] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    27.517] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    27.517] (II) No input driver/identifier specified (ignoring)
[    35.155] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[    35.155] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[    35.155] (II) RADEON(0): Added native panel mode: 1280x800
[    35.155] (II) RADEON(0): Output: S-video, Detected Monitor Type: 0
[    35.476] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[    35.476] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[    35.476] (II) RADEON(0): Added native panel mode: 1280x800
[    35.476] (II) RADEON(0): Output: S-video, Detected Monitor Type: 0
[    35.488] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[    35.488] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[    35.488] (II) RADEON(0): Added native panel mode: 1280x800
[    35.488] (II) RADEON(0): Output: S-video, Detected Monitor Type: 0
[    35.547] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[    35.547] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[    35.547] (II) RADEON(0): Added native panel mode: 1280x800
[    35.547] (II) RADEON(0): Output: S-video, Detected Monitor Type: 0
[    35.553] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[    35.553] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[    35.553] (II) RADEON(0): Added native panel mode: 1280x800
[    35.553] (II) RADEON(0): Output: S-video, Detected Monitor Type: 0
[    35.774] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[    35.774] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[    35.774] (II) RADEON(0): Added native panel mode: 1280x800
[    35.774] (II) RADEON(0): Output: S-video, Detected Monitor Type: 0
[    35.780] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[    35.780] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[    35.780] (II) RADEON(0): Added native panel mode: 1280x800
[    35.780] (II) RADEON(0): Output: S-video, Detected Monitor Type: 0[/QUOTE]

---

### Post by filippo1 on 2012-04-13
So is it correct or something is wrong?

---

### Post by Yellow Pasque on 2012-04-13
> [ 23.008] [drm] failed to load kernel module "radeon"
[ 23.008] (EE) RADEON(0): [dri] RADEONDRIGetVersion failed to open the DRM
[dri] Disabling DRI.
That is the issue. The kernel module isn't loading for some reason. What happens when you try to load the module manually?
```
sudo modprobe -v radeon
```

---

### Post by filippo1 on 2012-04-13
It says:

```
insmod /lib/modules/3.0.0-17-generic/kernel/drivers/gpu/drm/radeon/radeon.ko nomodeset=1
FATAL: Error inserting radeon (/lib/modules/3.0.0-17-generic/kernel/drivers/gpu/drm/radeon/radeon.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```in dmesg:

```
[  572.552831] radeon: Unknown parameter `nomodeset'
```

---

### Post by Yellow Pasque on 2012-04-13
> [  572.552831] radeon: Unknown parameter `nomodeset'

The parameter is named modeset. Check your /etc/modprobe.d directory to see what file is trying to set 'nomodeset'.

---

### Post by filippo1 on 2012-04-14
I don't see anything related to radeon in etc/modprobe.d directory. Only these files:
alsa-base.conf
blacklist.conf
blacklist-ath_pci.conf
blacklist-cups-usblp.conf
blacklist-firewire.conf
blacklist-framebuffer.conf
blacklist-modelm.conf
blacklist-oss.conf
blacklist-rare-network.conf
blacklist-watchdog.conf
libpisock9.conf

Do you think that a full reinstall would solve the problem?

---

### Post by Yellow Pasque on 2012-04-14
Look in blacklist.conf and blacklist-framebuffer.conf

---

### Post by filippo1 on 2012-04-15
Finally solved, I reinstalled the radeon driver and now it works. Long story short, this pc has been fixed by a friend of mine, who installed lubuntu and added fglrx, but he didn't know about drivers issues with old cards. Probably fglrx spoiled the open radeon drivers ad the reinstallation just restored it...
Thank you very much for your help, I really appreciate it!

---

### Post by Paddy Landau on 2012-04-15
Whew, that was a long resolution. I'm glad you have it resolved.

Please [mark the thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") to help others with this issue.

---

