---
title: "gallium3d on xubuntu 13.10? how?"
date: 2014-01-03
forum: Hardware
---

### Post by jhay2 on 2014-01-03
Hi .

is it possible on xubuntu? 

actually i have ATI driver

when i installed ubuntu 13.10 
Gallium 3D was already enabled by default so i think gallium is compatible with my laptop

But because of having an old laptop 
With only 512 ram ubuntu with unity was too heavy and run very slowly on my laptop

so i download xubuntu and replace ubuntu with same version 


But gallium was not included on xubuntu 

i try to install it using oibaf ppa 

And then reboot .. 
but gallium3d still not loaded 

what can i do to make gallium 3d works on xubuntu?

---

### Post by grahammechanical on 2014-01-03
Gallium is another name for the Nouveau open source video driver. I use Nouveau on my machine with an Nvidia GT220 and the Details page says that the video driver is Gallium 0.4 on NVA5. The Nvidia code for the GT220 is NVA5.

When you installed Xubuntu did you tick the box to install third party software? That would have installed the proprietary video driver. If we do not tick that box we get the Nouveau driver. You can change to the Nouveau driver by opening the Additional Drivers utility. I am not using Xubuntu so I cannot give you directions.

Another point to keep in mind. Depending on the capabilities of your graphic card you may be able to run full Nouveau but if not you will get a subset of Nouveau called llvmpipe that loads as a fall back mode for lower specification video adapters. The quality of the user experience is acceptable but not terrific. 

Regards.

---

### Post by Yellow Pasque on 2014-01-03
@grahammechanical, Gallium is used by multiple open source drivers for 3D. The user has an old ATI card, so please don't confuse him/her with talk of nouveau and proprietary drivers.

@jhay2: post your /var/log/Xorg.0.log (use code tags)

---

### Post by jhay2 on 2014-01-03
> **Temüjin said:**
> @grahammechanical, Gallium is used by multiple open source drivers for 3D. The user has an old ATI card, so please don't confuse him/her with talk of nouveau and proprietary drivers.

@jhay2: post your /var/log/Xorg.0.log (use code tags)

here it is thanks


```

 cat /var/log/Xorg.0.log
[    33.526] 
X.Org X Server 1.14.3
Release Date: 2013-09-12
[    33.526] X Protocol Version 11, Revision 0
[    33.526] Build Operating System: Linux 2.6.24-32-xen i686 Ubuntu
[    33.526] Current Operating System: Linux xfirebase 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:12:00 UTC 2013 i686
[    33.526] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.11.0-12-generic root=UUID=33b49060-a79f-4ab4-834a-ef3d4271cae6 ro quiet splash vt.handoff=7
[    33.526] Build Date: 11 November 2013  03:39:18PM
[    33.526] xorg-server 2:1.14.3-3ubuntu2+gd~s (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    33.526] Current version of pixman: 0.30.2
[    33.526] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[    33.526] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    33.527] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Jan  4 08:00:40 1980
[    33.555] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    33.556] (==) No Layout section.  Using the first Screen section.
[    33.556] (==) No screen section available. Using defaults.
[    33.556] (**) |-->Screen "Default Screen Section" (0)
[    33.556] (**) |   |-->Monitor "<default monitor>"
[    33.557] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    33.557] (==) Automatically adding devices
[    33.557] (==) Automatically enabling devices
[    33.557] (==) Automatically adding GPU devices
[    33.557] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    33.557] 	Entry deleted from font path.
[    33.557] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    33.557] 	Entry deleted from font path.
[    33.557] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    33.557] 	Entry deleted from font path.
[    33.557] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    33.557] 	Entry deleted from font path.
[    33.557] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    33.557] 	Entry deleted from font path.
[    33.557] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    33.557] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    33.557] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    33.557] (II) Loader magic: 0xb77b86a0
[    33.557] (II) Module ABI versions:
[    33.557] 	X.Org ANSI C Emulation: 0.4
[    33.557] 	X.Org Video Driver: 14.1
[    33.557] 	X.Org XInput driver : 19.1
[    33.557] 	X.Org Server Extension : 7.0
[    33.558] (II) xfree86: Adding drm device (/dev/dri/card0)
[    33.566] (--) PCI:*(0:1:0:0) 1002:4c57:0e11:00b7 rev 0, Mem @ 0x48000000/134217728, 0x40400000/65536, I/O @ 0x00003000/256, BIOS @ 0x????????/131072
[    33.570] (II) Open ACPI successful (/var/run/acpid.socket)
[    33.570] Initializing built-in extension Generic Event Extension
[    33.570] Initializing built-in extension SHAPE
[    33.570] Initializing built-in extension MIT-SHM
[    33.570] Initializing built-in extension XInputExtension
[    33.570] Initializing built-in extension XTEST
[    33.571] Initializing built-in extension BIG-REQUESTS
[    33.571] Initializing built-in extension SYNC
[    33.571] Initializing built-in extension XKEYBOARD
[    33.571] Initializing built-in extension XC-MISC
[    33.571] Initializing built-in extension SECURITY
[    33.571] Initializing built-in extension XINERAMA
[    33.571] Initializing built-in extension XFIXES
[    33.571] Initializing built-in extension RENDER
[    33.571] Initializing built-in extension RANDR
[    33.571] Initializing built-in extension COMPOSITE
[    33.571] Initializing built-in extension DAMAGE
[    33.571] Initializing built-in extension MIT-SCREEN-SAVER
[    33.571] Initializing built-in extension DOUBLE-BUFFER
[    33.571] Initializing built-in extension RECORD
[    33.571] Initializing built-in extension DPMS
[    33.571] Initializing built-in extension X-Resource
[    33.571] Initializing built-in extension XVideo
[    33.571] Initializing built-in extension XVideo-MotionCompensation
[    33.571] Initializing built-in extension SELinux
[    33.571] Initializing built-in extension XFree86-VidModeExtension
[    33.571] Initializing built-in extension XFree86-DGA
[    33.571] Initializing built-in extension XFree86-DRI
[    33.571] Initializing built-in extension DRI2
[    33.571] (II) "glx" will be loaded by default.
[    33.571] (WW) "xmir" is not to be loaded by default. Skipping.
[    33.571] (II) LoadModule: "dri2"
[    33.571] (II) Module "dri2" already built-in
[    33.571] (II) LoadModule: "glamoregl"
[    33.601] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[    34.025] (II) Module glamoregl: vendor="X.Org Foundation"
[    34.025] 	compiled for 1.14.3, module version = 0.5.1
[    34.025] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    34.025] (II) LoadModule: "glx"
[    34.025] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    34.026] (II) Module glx: vendor="X.Org Foundation"
[    34.026] 	compiled for 1.14.3, module version = 1.0.0
[    34.026] 	ABI class: X.Org Server Extension, version 7.0
[    34.026] (==) AIGLX enabled
[    34.026] Loading extension GLX
[    34.026] (==) Matched fglrx as autoconfigured driver 0
[    34.026] (==) Matched ati as autoconfigured driver 1
[    34.026] (==) Matched fglrx as autoconfigured driver 2
[    34.026] (==) Matched ati as autoconfigured driver 3
[    34.026] (==) Matched vesa as autoconfigured driver 4
[    34.026] (==) Matched modesetting as autoconfigured driver 5
[    34.026] (==) Matched fbdev as autoconfigured driver 6
[    34.026] (==) Assigned the driver to the xf86ConfigLayout
[    34.026] (II) LoadModule: "fglrx"
[    34.057] (WW) Warning, couldn't open module fglrx
[    34.057] (II) UnloadModule: "fglrx"
[    34.057] (II) Unloading fglrx
[    34.057] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    34.057] (II) LoadModule: "ati"
[    34.058] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    34.058] (II) Module ati: vendor="X.Org Foundation"
[    34.058] 	compiled for 1.14.3, module version = 7.2.99
[    34.058] 	Module class: X.Org Video Driver
[    34.058] 	ABI class: X.Org Video Driver, version 14.1
[    34.058] (II) LoadModule: "radeon"
[    34.059] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    34.081] (II) Module radeon: vendor="X.Org Foundation"
[    34.081] 	compiled for 1.14.3, module version = 7.2.99
[    34.081] 	Module class: X.Org Video Driver
[    34.081] 	ABI class: X.Org Video Driver, version 14.1
[    34.081] (II) LoadModule: "vesa"
[    34.082] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    34.082] (II) Module vesa: vendor="X.Org Foundation"
[    34.082] 	compiled for 1.14.1, module version = 2.3.2
[    34.082] 	Module class: X.Org Video Driver
[    34.082] 	ABI class: X.Org Video Driver, version 14.1
[    34.082] (II) LoadModule: "modesetting"
[    34.083] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    34.083] (II) Module modesetting: vendor="X.Org Foundation"
[    34.083] 	compiled for 1.14.1, module version = 0.8.0
[    34.083] 	Module class: X.Org Video Driver
[    34.083] 	ABI class: X.Org Video Driver, version 14.1
[    34.083] (II) LoadModule: "fbdev"
[    34.084] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    34.084] (II) Module fbdev: vendor="X.Org Foundation"
[    34.084] 	compiled for 1.14.1, module version = 0.4.3
[    34.084] 	Module class: X.Org Video Driver
[    34.084] 	ABI class: X.Org Video Driver, version 14.1
[    34.084] (==) Matched fglrx as autoconfigured driver 0
[    34.084] (==) Matched ati as autoconfigured driver 1
[    34.084] (==) Matched fglrx as autoconfigured driver 2
[    34.084] (==) Matched ati as autoconfigured driver 3
[    34.084] (==) Matched vesa as autoconfigured driver 4
[    34.084] (==) Matched modesetting as autoconfigured driver 5
[    34.084] (==) Matched fbdev as autoconfigured driver 6
[    34.084] (==) Assigned the driver to the xf86ConfigLayout
[    34.085] (II) LoadModule: "fglrx"
[    34.086] (WW) Warning, couldn't open module fglrx
[    34.086] (II) UnloadModule: "fglrx"
[    34.086] (II) Unloading fglrx
[    34.086] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    34.086] (II) LoadModule: "ati"
[    34.086] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    34.086] (II) Module ati: vendor="X.Org Foundation"
[    34.086] 	compiled for 1.14.3, module version = 7.2.99
[    34.086] 	Module class: X.Org Video Driver
[    34.086] 	ABI class: X.Org Video Driver, version 14.1
[    34.086] (II) LoadModule: "vesa"
[    34.087] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    34.087] (II) Module vesa: vendor="X.Org Foundation"
[    34.087] 	compiled for 1.14.1, module version = 2.3.2
[    34.087] 	Module class: X.Org Video Driver
[    34.087] 	ABI class: X.Org Video Driver, version 14.1
[    34.087] (II) UnloadModule: "vesa"
[    34.087] (II) Unloading vesa
[    34.087] (II) Failed to load module "vesa" (already loaded, 0)
[    34.087] (II) LoadModule: "modesetting"
[    34.087] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    34.088] (II) Module modesetting: vendor="X.Org Foundation"
[    34.088] 	compiled for 1.14.1, module version = 0.8.0
[    34.088] 	Module class: X.Org Video Driver
[    34.088] 	ABI class: X.Org Video Driver, version 14.1
[    34.088] (II) UnloadModule: "modesetting"
[    34.088] (II) Unloading modesetting
[    34.088] (II) Failed to load module "modesetting" (already loaded, 0)
[    34.088] (II) LoadModule: "fbdev"
[    34.088] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    34.088] (II) Module fbdev: vendor="X.Org Foundation"
[    34.088] 	compiled for 1.14.1, module version = 0.4.3
[    34.088] 	Module class: X.Org Video Driver
[    34.088] 	ABI class: X.Org Video Driver, version 14.1
[    34.088] (II) UnloadModule: "fbdev"
[    34.088] (II) Unloading fbdev
[    34.088] (II) Failed to load module "fbdev" (already loaded, 0)
[    34.089] (II) RADEON: Driver for ATI Radeon chipsets:
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
[    34.101] (II) VESA: driver for VESA chipsets: vesa
[    34.101] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    34.101] (II) FBDEV: driver for framebuffer: fbdev
[    34.101] (++) using VT number 7


[    34.101] (II) [KMS] Kernel modesetting enabled.
[    34.101] (WW) Falling back to old probe method for vesa
[    34.102] (WW) Falling back to old probe method for modesetting
[    34.102] (WW) Falling back to old probe method for fbdev
[    34.102] (II) Loading sub module "fbdevhw"
[    34.102] (II) LoadModule: "fbdevhw"
[    34.102] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    34.102] (II) Module fbdevhw: vendor="X.Org Foundation"
[    34.102] 	compiled for 1.14.3, module version = 0.0.2
[    34.102] 	ABI class: X.Org Video Driver, version 14.1
[    34.103] (II) RADEON(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    34.103] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    34.103] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    34.103] (==) RADEON(0): Default visual is TrueColor
[    34.103] (==) RADEON(0): RGB weight 888
[    34.103] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    34.103] (--) RADEON(0): Chipset: "ATI Radeon Mobility M7 LW (AGP)" (ChipID = 0x4c57)
[    34.103] (II) Loading sub module "dri2"
[    34.103] (II) LoadModule: "dri2"
[    34.103] (II) Module "dri2" already built-in
[    34.103] (II) Loading sub module "exa"
[    34.103] (II) LoadModule: "exa"
[    34.104] (II) Loading /usr/lib/xorg/modules/libexa.so
[    34.104] (II) Module exa: vendor="X.Org Foundation"
[    34.104] 	compiled for 1.14.3, module version = 2.6.0
[    34.104] 	ABI class: X.Org Video Driver, version 14.1
[    34.104] (II) RADEON(0): KMS Color Tiling: disabled
[    34.104] (II) RADEON(0): KMS Color Tiling 2D: disabled
[    34.104] (II) RADEON(0): KMS Pageflipping: enabled
[    34.104] (II) RADEON(0): SwapBuffers wait for vsync: enabled
[    34.111] (II) RADEON(0): Output VGA-0 has no monitor section
[    34.113] (II) RADEON(0): Output DVI-0 has no monitor section
[    34.113] (II) RADEON(0): Output LVDS has no monitor section
[    34.119] (II) RADEON(0): Output S-video has no monitor section
[    34.126] (II) RADEON(0): EDID for output VGA-0
[    34.128] (II) RADEON(0): EDID for output DVI-0
[    34.128] (II) RADEON(0): EDID for output LVDS
[    34.128] (II) RADEON(0): Manufacturer: AUO  Model: 1407  Serial#: 317
[    34.128] (II) RADEON(0): Year: 2003  Week: 38
[    34.128] (II) RADEON(0): EDID Version: 1.2
[    34.128] (II) RADEON(0): Digital Display Input
[    34.128] (II) RADEON(0): Max Image Size [cm]: horiz.: 29  vert.: 22
[    34.128] (II) RADEON(0): Gamma: 2.20
[    34.128] (II) RADEON(0): No DPMS capabilities specified
[    34.128] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    34.128] (II) RADEON(0): First detailed timing is preferred mode
[    34.128] (II) RADEON(0): redX: 0.576 redY: 0.327   greenX: 0.300 greenY: 0.555
[    34.128] (II) RADEON(0): blueX: 0.145 blueY: 0.119   whiteX: 0.310 whiteY: 0.329
[    34.128] (II) RADEON(0): Manufacturer's mask: 0
[    34.128] (II) RADEON(0): Supported detailed timing:
[    34.128] (II) RADEON(0): clock: 65.0 MHz   Image Size:  286 x 214 mm
[    34.128] (II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1320 h_border: 0
[    34.128] (II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 803 v_border: 0
[    34.128] (II) RADEON(0):  e
                                      &#65533;P
[    34.128] (II) RADEON(0):  AUQ
[    34.128] (II) RADEON(0): Monitor name: B141XG03
[    34.129] (II) RADEON(0): EDID (in hex):
[    34.129] (II) RADEON(0): 	00ffffffffffff0006af07143d010000
[    34.129] (II) RADEON(0): 	260d0102801d16780abc2593534c8e25
[    34.129] (II) RADEON(0): 	1e4f5400000001010101010101010101
[    34.129] (II) RADEON(0): 	01010101010164190028410023301888
[    34.129] (II) RADEON(0): 	36001ed610000019000000fe00016502
[    34.129] (II) RADEON(0): 	7f011a12120bff025001000000fe0041
[    34.129] (II) RADEON(0): 	555100000000000000000a20000000fc
[    34.129] (II) RADEON(0): 	0042313431584730330000000a20003a
[    34.129] (II) RADEON(0): Printing probed modes for output LVDS
[    34.129] (II) RADEON(0): Modeline "1024x768"x61.3   65.00  1024 1048 1184 1320  768 771 777 803 -hsync -vsync (49.2 kHz eP)
[    34.129] (II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
[    34.129] (II) RADEON(0): Modeline "848x480"x59.7   31.50  848 872 952 1056  480 483 493 500 -hsync +vsync (29.8 kHz)
[    34.129] (II) RADEON(0): Modeline "720x480"x59.7   26.75  720 744 808 896  480 483 493 500 -hsync +vsync (29.9 kHz)
[    34.129] (II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
[    34.135] (II) RADEON(0): EDID for output S-video
[    34.135] (II) RADEON(0): Output VGA-0 disconnected
[    34.135] (II) RADEON(0): Output DVI-0 disconnected
[    34.135] (II) RADEON(0): Output LVDS connected
[    34.135] (II) RADEON(0): Output S-video disconnected
[    34.135] (II) RADEON(0): Using exact sizes for initial modes
[    34.135] (II) RADEON(0): Output LVDS using initial mode 1024x768
[    34.135] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    34.135] (II) RADEON(0): mem size init: gart size :fdff000 vram size: s:2000000 visible:1f00000
[    34.135] (II) RADEON(0): EXA: Driver will not allow EXA pixmaps in VRAM
[    34.135] (==) RADEON(0): DPI set to (96, 96)
[    34.135] (II) Loading sub module "fb"
[    34.135] (II) LoadModule: "fb"
[    34.136] (II) Loading /usr/lib/xorg/modules/libfb.so
[    34.136] (II) Module fb: vendor="X.Org Foundation"
[    34.136] 	compiled for 1.14.3, module version = 1.0.0
[    34.137] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    34.137] (II) Loading sub module "ramdac"
[    34.137] (II) LoadModule: "ramdac"
[    34.137] (II) Module "ramdac" already built-in
[    34.137] (II) UnloadModule: "vesa"
[    34.137] (II) Unloading vesa
[    34.137] (II) UnloadModule: "modesetting"
[    34.137] (II) Unloading modesetting
[    34.137] (II) UnloadModule: "fbdev"
[    34.137] (II) Unloading fbdev
[    34.137] (II) UnloadSubModule: "fbdevhw"
[    34.137] (II) Unloading fbdevhw
[    34.137] (--) Depth 24 pixmap format is 32 bpp
[    34.137] (II) RADEON(0): [DRI2] Setup complete
[    34.137] (II) RADEON(0): [DRI2]   DRI driver: radeon
[    34.137] (II) RADEON(0): [DRI2]   VDPAU driver: radeon
[    34.138] (II) RADEON(0): Front buffer size: 3072K
[    34.138] (II) RADEON(0): VRAM usage limit set to 25776K
[    34.138] (==) RADEON(0): Backing store disabled
[    34.138] (II) RADEON(0): Direct rendering enabled
[    34.138] (II) RADEON(0): Render acceleration enabled for R100 type cards.
[    34.138] (II) EXA(0): Driver allocated offscreen pixmaps
[    34.138] (II) EXA(0): Driver registered support for the following operations:
[    34.138] (II)         Solid
[    34.138] (II)         Copy
[    34.138] (II)         Composite (RENDER acceleration)
[    34.138] (II)         UploadToScreen
[    34.138] (II)         DownloadFromScreen
[    34.138] (II) RADEON(0): Acceleration enabled
[    34.138] (==) RADEON(0): DPMS enabled
[    34.138] (==) RADEON(0): Silken mouse enabled
[    34.139] (II) RADEON(0): Set up textured video
[    34.139] (II) RADEON(0): [XvMC] Associated with Radeon Textured Video.
[    34.139] (II) RADEON(0): [XvMC] Extension initialized.
[    34.139] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    34.139] (--) RandR disabled
[    34.158] (II) SELinux: Disabled on system
[    34.201] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    34.201] (II) AIGLX: enabled GLX_INTEL_swap_event
[    34.201] (II) AIGLX: enabled GLX_ARB_create_context
[    34.201] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    34.201] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    34.201] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    34.201] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    34.202] (II) AIGLX: Loaded and initialized radeon
[    34.202] (II) GLX: Initialized DRI2 GL provider for screen 0
[    34.203] (II) RADEON(0): Setting screen physical size to 270 x 203
[    34.224] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    34.232] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    34.232] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    34.232] (II) LoadModule: "evdev"
[    34.233] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    34.257] (II) Module evdev: vendor="X.Org Foundation"
[    34.257] 	compiled for 1.14.1, module version = 2.7.3
[    34.257] 	Module class: X.Org XInput Driver
[    34.257] 	ABI class: X.Org XInput driver, version 19.1
[    34.257] (II) Using input driver 'evdev' for 'Power Button'
[    34.257] (**) Power Button: always reports core events
[    34.257] (**) evdev: Power Button: Device: "/dev/input/event2"
[    34.257] (--) evdev: Power Button: Vendor 0 Product 0x1
[    34.257] (--) evdev: Power Button: Found keys
[    34.257] (II) evdev: Power Button: Configuring as keyboard
[    34.258] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    34.258] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    34.258] (**) Option "xkb_rules" "evdev"
[    34.258] (**) Option "xkb_model" "pc105"
[    34.258] (**) Option "xkb_layout" "us"
[    34.259] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[    34.259] (II) No input driver specified, ignoring this device.
[    34.259] (II) This device may have been added with another device file.
[    34.260] (II) config/udev: Adding input device Sleep Button (/dev/input/event0)
[    34.260] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    34.260] (II) Using input driver 'evdev' for 'Sleep Button'
[    34.260] (**) Sleep Button: always reports core events
[    34.260] (**) evdev: Sleep Button: Device: "/dev/input/event0"
[    34.260] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    34.260] (--) evdev: Sleep Button: Found keys
[    34.260] (II) evdev: Sleep Button: Configuring as keyboard
[    34.260] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input0/event0"
[    34.260] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 7)
[    34.260] (**) Option "xkb_rules" "evdev"
[    34.260] (**) Option "xkb_model" "pc105"
[    34.260] (**) Option "xkb_layout" "us"
[    34.261] (II) config/udev: Adding drm device (/dev/dri/card0)
[    34.261] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    34.262] (II) config/udev: Adding input device CHESEN USB Keyboard (/dev/input/event4)
[    34.262] (**) CHESEN USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    34.262] (II) Using input driver 'evdev' for 'CHESEN USB Keyboard'
[    34.262] (**) CHESEN USB Keyboard: always reports core events
[    34.262] (**) evdev: CHESEN USB Keyboard: Device: "/dev/input/event4"
[    34.263] (--) evdev: CHESEN USB Keyboard: Vendor 0xa81 Product 0x101
[    34.263] (--) evdev: CHESEN USB Keyboard: Found keys
[    34.263] (II) evdev: CHESEN USB Keyboard: Configuring as keyboard
[    34.263] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1e.0/0000:02:0e.0/usb2/2-1/2-1:1.0/input/input4/event4"
[    34.263] (II) XINPUT: Adding extended input device "CHESEN USB Keyboard" (type: KEYBOARD, id 8)
[    34.263] (**) Option "xkb_rules" "evdev"
[    34.263] (**) Option "xkb_model" "pc105"
[    34.263] (**) Option "xkb_layout" "us"
[    34.264] (II) config/udev: Adding input device CHESEN USB Keyboard (/dev/input/event5)
[    34.264] (**) CHESEN USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    34.264] (II) Using input driver 'evdev' for 'CHESEN USB Keyboard'
[    34.264] (**) CHESEN USB Keyboard: always reports core events
[    34.264] (**) evdev: CHESEN USB Keyboard: Device: "/dev/input/event5"
[    34.265] (--) evdev: CHESEN USB Keyboard: Vendor 0xa81 Product 0x101
[    34.265] (--) evdev: CHESEN USB Keyboard: Found keys
[    34.265] (II) evdev: CHESEN USB Keyboard: Configuring as keyboard
[    34.265] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1e.0/0000:02:0e.0/usb2/2-1/2-1:1.1/input/input5/event5"
[    34.265] (II) XINPUT: Adding extended input device "CHESEN USB Keyboard" (type: KEYBOARD, id 9)
[    34.265] (**) Option "xkb_rules" "evdev"
[    34.265] (**) Option "xkb_model" "pc105"
[    34.265] (**) Option "xkb_layout" "us"
[    34.266] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    34.266] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    34.266] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    34.266] (**) AT Translated Set 2 keyboard: always reports core events
[    34.266] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    34.267] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    34.267] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    34.267] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    34.267] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    34.267] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 10)
[    34.267] (**) Option "xkb_rules" "evdev"
[    34.267] (**) Option "xkb_model" "pc105"
[    34.267] (**) Option "xkb_layout" "us"
[    34.268] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event6)
[    34.268] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    34.268] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    34.268] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[    34.268] (II) LoadModule: "synaptics"
[    34.269] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    34.269] (II) Module synaptics: vendor="X.Org Foundation"
[    34.269] 	compiled for 1.14.2, module version = 1.7.1
[    34.269] 	Module class: X.Org XInput Driver
[    34.269] 	ABI class: X.Org XInput driver, version 19.1
[    34.269] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    34.269] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    34.269] (**) Option "Device" "/dev/input/event6"
[    34.269] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472 (res 84)
[    34.269] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448 (res 99)
[    34.269] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    34.270] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    34.270] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    34.270] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    34.270] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    34.270] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    34.270] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio4/input/input6/event6"
[    34.270] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 11)
[    34.270] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    34.270] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[    34.270] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.040
[    34.270] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    34.270] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    34.270] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    34.270] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    34.270] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    34.271] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    34.271] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    34.272] (II) config/udev: Adding input device TPPS/2 IBM TrackPoint (/dev/input/event7)
[    34.272] (**) TPPS/2 IBM TrackPoint: Applying InputClass "evdev pointer catchall"
[    34.272] (**) TPPS/2 IBM TrackPoint: Applying InputClass "trackpoint catchall"
[    34.272] (II) Using input driver 'evdev' for 'TPPS/2 IBM TrackPoint'
[    34.272] (**) TPPS/2 IBM TrackPoint: always reports core events
[    34.272] (**) evdev: TPPS/2 IBM TrackPoint: Device: "/dev/input/event7"
[    34.273] (--) evdev: TPPS/2 IBM TrackPoint: Vendor 0x2 Product 0xa
[    34.273] (--) evdev: TPPS/2 IBM TrackPoint: Found 3 mouse buttons
[    34.273] (--) evdev: TPPS/2 IBM TrackPoint: Found relative axes
[    34.273] (--) evdev: TPPS/2 IBM TrackPoint: Found x and y relative axes
[    34.273] (II) evdev: TPPS/2 IBM TrackPoint: Configuring as mouse
[    34.273] (**) Option "Emulate3Buttons" "true"
[    34.273] (**) Option "EmulateWheel" "true"
[    34.273] (**) Option "EmulateWheelButton" "2"
[    34.273] (**) Option "YAxisMapping" "4 5"
[    34.273] (**) evdev: TPPS/2 IBM TrackPoint: YAxisMapping: buttons 4 and 5
[    34.273] (**) Option "XAxisMapping" "6 7"
[    34.273] (**) evdev: TPPS/2 IBM TrackPoint: XAxisMapping: buttons 6 and 7
[    34.273] (**) evdev: TPPS/2 IBM TrackPoint: EmulateWheelButton: 2, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    34.273] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio4/serio5/input/input7/event7"
[    34.273] (II) XINPUT: Adding extended input device "TPPS/2 IBM TrackPoint" (type: MOUSE, id 12)
[    34.273] (II) evdev: TPPS/2 IBM TrackPoint: initialized for relative axes.
[    34.274] (**) TPPS/2 IBM TrackPoint: (accel) keeping acceleration scheme 1
[    34.274] (**) TPPS/2 IBM TrackPoint: (accel) acceleration profile 0
[    34.274] (**) TPPS/2 IBM TrackPoint: (accel) acceleration factor: 2.000
[    34.274] (**) TPPS/2 IBM TrackPoint: (accel) acceleration threshold: 4
[    34.274] (II) config/udev: Adding input device TPPS/2 IBM TrackPoint (/dev/input/mouse1)
[    34.274] (II) No input driver specified, ignoring this device.
[    34.274] (II) This device may have been added with another device file.
[    53.928] (II) RADEON(0): EDID vendor "AUO", prod id 5127
[    53.928] (II) RADEON(0): Printing DDC gathered Modelines:
[    53.928] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1320  768 771 777 803 -hsync -vsync (49.2 kHz eP)
[    56.209] (II) RADEON(0): EDID vendor "AUO", prod id 5127
[    56.209] (II) RADEON(0): Printing DDC gathered Modelines:
[    56.209] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1320  768 771 777 803 -hsync -vsync (49.2 kHz eP)
[    56.260] (II) RADEON(0): EDID vendor "AUO", prod id 5127
[    56.260] (II) RADEON(0): Printing DDC gathered Modelines:
[    56.260] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1320  768 771 777 803 -hsync -vsync (49.2 kHz eP)

```

---

### Post by Yellow Pasque on 2014-01-04
Everything looks fine. Check glxinfo just to be sure:
```
sudo apt-get install mesa-utils
glxinfo
```

---

### Post by jhay2 on 2014-01-04
> **Temüjin said:**
> Everything looks fine. Check glxinfo just to be sure:
```
sudo apt-get install mesa-utils
glxinfo
```


i already installed that .. 


heres the output from glxinfo


```

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_multisample, GLX_EXT_create_context_es2_profile, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_INTEL_swap_event, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, GLX_SGI_swap_control
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_create_context_robustness, GLX_ARB_fbconfig_float, 
    GLX_ARB_framebuffer_sRGB, GLX_ARB_get_proc_address, GLX_ARB_multisample, 
    GLX_EXT_create_context_es2_profile, GLX_EXT_fbconfig_packed_float, 
    GLX_EXT_framebuffer_sRGB, GLX_EXT_import_context, 
    GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_INTEL_swap_event, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_query_renderer, 
    GLX_MESA_swap_control, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync
GLX version: 1.4
GLX extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_INTEL_swap_event, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_swap_control, 
    GLX_OML_swap_method, GLX_OML_sync_control, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R100 (RV200 4C57) x86/MMX/SSE2 TCL DRI2
OpenGL version string: 1.3 Mesa 10.1.0-devel (git-eb212c5 saucy-oibaf-ppa)
OpenGL extensions:
    GL_ANGLE_texture_compression_dxt3, GL_ANGLE_texture_compression_dxt5, 
    GL_APPLE_packed_pixels, GL_APPLE_vertex_array_object, 
    GL_ARB_clear_buffer_object, GL_ARB_copy_buffer, GL_ARB_debug_output, 
    GL_ARB_draw_buffers, GL_ARB_get_program_binary, GL_ARB_invalidate_subdata, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_occlusion_query, 
    GL_ARB_robustness, GL_ARB_sampler_objects, GL_ARB_shader_objects, 
    GL_ARB_shading_language_100, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirror_clamp_to_edge, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_rectangle, GL_ARB_texture_storage, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_array_object, GL_ARB_vertex_attrib_binding, 
    GL_ARB_vertex_buffer_object, GL_ARB_window_pos, GL_ATI_draw_buffers, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once, GL_EXT_abgr, 
    GL_EXT_bgra, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, 
    GL_EXT_copy_texture, GL_EXT_draw_range_elements, GL_EXT_fog_coord, 
    GL_EXT_framebuffer_object, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels, GL_EXT_polygon_offset, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_compression_dxt1, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_vertex_array, 
    GL_IBM_multimode_draw_arrays, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_KHR_debug, GL_MESA_window_pos, 
    GL_MESA_ycbcr_texture, GL_NV_blend_square, GL_NV_light_max_exponent, 
    GL_NV_packed_depth_stencil, GL_NV_texgen_reflection, 
    GL_NV_texture_rectangle, GL_OES_EGL_image, GL_OES_read_format, 
    GL_S3_s3tc, GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays


64 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x021 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x022 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0bf 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0c0 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0c1 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0c2 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0c3 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x0c4 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x0c5 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x0c6 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x0c7 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0c8 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0c9 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0ca 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0cb 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0cc 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0cd 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0ce 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0cf 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0d0 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x0d1 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0d2 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x0d3 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x0d4 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x0d5 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x0d6 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x0d7 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x0d8 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x0d9 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x0da 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0db 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x0dc 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x0dd 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0de 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0df 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0e0 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0e1 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x0e2 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x0e3 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x0e4 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x0e5 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0e6 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0e7 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0e8 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0e9 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0ea 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0eb 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0ec 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0ed 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0ee 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x0ef 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0f0 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x0f1 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x0f2 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x0f3 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x0f4 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x0f5 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x0f6 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x0f7 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x0f8 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x0f9 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0fa 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x0fb 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x05e 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None


96 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x05f  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x060  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x061  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x062  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x063  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x064  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x065  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x066  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x067  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x068  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x069  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x06a  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x06b  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x06c  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x06d  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x06e  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x06f 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x070 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x071 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x072 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x073 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x074 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x075 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x076 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x077 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x078 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x079 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x07a 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x07b 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x07c 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x07d 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x07e 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x07f 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x080 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x081 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x082 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x083 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x084 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x085 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x086 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x087 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x088 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x089 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x08a 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x08b 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x08c 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x08d 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x08e 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x08f  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x090  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x091  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x092  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x093  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x094  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x095  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x096  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x097  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x098  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x099  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x09a  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x09b  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x09c  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x09d  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x09e  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x09f 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0a0 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0a1 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0a2 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0a3 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x0a4 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x0a5 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x0a6 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x0a7 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0a8 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0a9 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0aa 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0ab 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0ac 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0ad 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0ae 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0af 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0b0 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x0b1 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0b2 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x0b3 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x0b4 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x0b5 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x0b6 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x0b7 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x0b8 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x0b9 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x0ba 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x0bb 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0bc 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x0bd 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0be 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow

```

---

### Post by jhay2 on 2014-01-04
glxinfo | grep -i opengl


> 
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R100 (RV200 4C57) x86/MMX/SSE2 TCL DRI2
OpenGL version string: 1.3 Mesa 10.1.0-devel (git-eb212c5 saucy-oibaf-ppa)
OpenGL extensions:


not Gallium 0.4 like on ubuntu with unity :(

---

### Post by Yellow Pasque on 2014-01-04
If Unity is telling you that a card that old is running on gallium, it's probably lying to you. As fair as I'm aware, the earliest radeon cards using the r300g gallium 3D driver are the Radeon 9800's. Earlier cards use classic Mesa 3D drivers

---

### Post by mörgæs on 2014-01-04
Jhay2, please use CODE and not QUOTE tags.

---

### Post by Yellow Pasque on 2014-01-04
Also note that gallium vs. classic mesa shouldn't really matter to the user. Intel never hopped on the Gallium3D bandwagon and stuck with classic mesa, and they still have some really good 3D drivers..

---

