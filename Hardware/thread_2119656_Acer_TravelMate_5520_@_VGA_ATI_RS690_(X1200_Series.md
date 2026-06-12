---
title: "Acer TravelMate 5520 @ VGA ATI RS690 (X1200 Series) slow GUI"
date: 2013-02-24
forum: Hardware
---

### Post by FreeRide23 on 2013-02-24
Hello, my name is Claus W.

i have installed Ubuntu 12.10 on the Acer TravelMate 5520 and my problem is, that the GUI (graphical User Interface) is very... slow.
It even crashes some time, if i "klick" something to fast, other thing i mentioned is that after installation on boot there was no picture at all... i had to press STRG+ALT+1 (or 2, or 3...) to get to shell, then i can press STRG+ALT+7 again, to come back to GUI picture, there i found back the enter prompt for the passphrase (encryption)....

So... far so well.

My VGA is a ATI RS690 on Gallium 0,4 (Galium !?!?!? wtf) from the X1200 Series

I have shared Memory, in the BIOS i first (at installation) had 64MB, after the GUI problem i switched to 256MB, not much change...

with lspci -vvv i get > 00:01.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS690 PCI to PCI Bridge (Internal gfx) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: f0000000-f01fffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Secondary status: 66MHz+ FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA+ MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel modules: shpchp


my OS is 64 bit, Ubuntu 12.10

i dit search misses google, i dint found a soulution.
i dit search the ati x1200 Series Linux driver, i dint found it.

I have to deliver the laptop a.s.a.p. to my customer... would appreciate help.

Thanks a lot. I am online and u can ask me, i will reply soon.

---

### Post by Yellow Pasque on 2013-02-24
> **FreeRide23 said:**
> My VGA is a ATI RS690 on Gallium 0.4 from the X1200 Series
That is correct.

> i dit search the ati x1200 Series Linux driver, i dint found it.
The correct driver is installed by default. Trying to install any other driver will make things worse.


The 690G is just a slow GPU (I used to have one). There is nothing you can do. However, do post your /var/log/Xorg.0.log just to make sure..

---

### Post by FreeRide23 on 2013-02-24
> **Temüjin said:**
> The correct driver is installed by default. Trying to install any other driver will make things worse. The 690G is just a slow GPU (I used to have one). There is nothing you can do.

Seriously? That should be the "right" driver? Its terribly slow...

And it is a AMD Thurion X2 with 1gig of RAM and 64bit... i have an Celeron Laptop with Ubuntu 12.04 and the Thurion is like slow old woman behind the Celeron... this can not be true...

> **Temüjin said:**
> However, do post your /var/log/Xorg.0.log just to make sure..

The WHOLE!? Its a lot...

as you wish:

```
[ 32.461]
X.Org X Server 1.13.0
Release Date: 2012-09-05
[ 32.461] X Protocol Version 11, Revision 0
[ 32.461] Build Operating System: Linux 3.2.0-32-generic x86_64 Ubuntu
[ 32.461] Current Operating System: Linux dominik-Schleppi 3.5.0-25-generic #38-Ubuntu SMP Mon Feb 18 23:27:42 UTC 2013 x86_64
[ 32.461] Kernel command line: BOOT_IMAGE=/vmlinuz-3.5.0-25-generic root=/dev/mapper/this-root ro quiet splash
[ 32.461] Build Date: 27 November 2012 07:44:35AM
[ 32.461] xorg-server 2:1.13.0-0ubuntu6.1 (For technical support please see http://www.ubuntu.com/support)
[ 32.461] Current version of pixman: 0.26.0
[ 32.461] Before reporting problems, check http://wiki.x.org
to make sure that you have the latest version.
[ 32.461] Markers: (--) probed, (**) from config file, (==) default setting,
(++) from command line, (!!) notice, (II) informational,
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[ 32.461] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Feb 24 16:30:04 2013
[ 32.587] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[ 32.588] (==) No Layout section. Using the first Screen section.
[ 32.588] (==) No screen section available. Using defaults.
[ 32.588] (**) |-->Screen "Default Screen Section" (0)
[ 32.588] (**) | |-->Monitor "<default monitor>"
[ 32.588] (==) No monitor specified for screen "Default Screen Section".
Using a default monitor configuration.
[ 32.588] (==) Automatically adding devices
[ 32.588] (==) Automatically enabling devices
[ 32.588] (==) Automatically adding GPU devices
[ 32.588] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[ 32.588] Entry deleted from font path.
[ 32.588] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[ 32.588] Entry deleted from font path.
[ 32.588] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[ 32.588] Entry deleted from font path.
[ 32.588] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[ 32.588] Entry deleted from font path.
[ 32.588] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[ 32.588] Entry deleted from font path.
[ 32.588] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[ 32.588] Entry deleted from font path.
[ 32.588] (==) FontPath set to:
/usr/share/fonts/X11/misc,
/usr/share/fonts/X11/Type1,
built-ins
[ 32.588] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[ 32.588] (II) The server relies on udev to provide the list of input devices.
If no devices become available, reconfigure udev or disable AutoAddDevices.
[ 32.588] (II) Loader magic: 0x7f0d49557c40
[ 32.588] (II) Module ABI versions:
[ 32.588] X.Org ANSI C Emulation: 0.4
[ 32.588] X.Org Video Driver: 13.0
[ 32.588] X.Org XInput driver : 18.0
[ 32.588] X.Org Server Extension : 7.0
[ 32.589] (II) config/udev: Adding drm device (/dev/dri/card0)
[ 32.591] (--) PCI:*(0:1:5:0) 1002:791f:1025:0124 rev 0, Mem @ 0xd0000000/268435456, 0xf0100000/65536, 0xf0000000/1048576, I/O @ 0x00009000/256
[ 32.591] (II) Open ACPI successful (/var/run/acpid.socket)
[ 32.591] Initializing built-in extension Generic Event Extension
[ 32.591] Initializing built-in extension SHAPE
[ 32.591] Initializing built-in extension MIT-SHM
[ 32.591] Initializing built-in extension XInputExtension
[ 32.591] Initializing built-in extension XTEST
[ 32.591] Initializing built-in extension BIG-REQUESTS
[ 32.591] Initializing built-in extension SYNC
[ 32.591] Initializing built-in extension XKEYBOARD
[ 32.591] Initializing built-in extension XC-MISC
[ 32.591] Initializing built-in extension SECURITY
[ 32.591] Initializing built-in extension XINERAMA
[ 32.591] Initializing built-in extension XFIXES
[ 32.591] Initializing built-in extension RENDER
[ 32.591] Initializing built-in extension RANDR
[ 32.591] Initializing built-in extension COMPOSITE
[ 32.591] Initializing built-in extension DAMAGE
[ 32.591] Initializing built-in extension MIT-SCREEN-SAVER
[ 32.591] Initializing built-in extension DOUBLE-BUFFER
[ 32.591] Initializing built-in extension RECORD
[ 32.591] Initializing built-in extension DPMS
[ 32.591] Initializing built-in extension X-Resource
[ 32.591] Initializing built-in extension XVideo
[ 32.591] Initializing built-in extension XVideo-MotionCompensation
[ 32.591] Initializing built-in extension XFree86-VidModeExtension
[ 32.591] Initializing built-in extension XFree86-DGA
[ 32.591] Initializing built-in extension XFree86-DRI
[ 32.591] Initializing built-in extension DRI2
[ 32.591] (II) LoadModule: "glx"
[ 32.742] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[ 32.742] (II) Module glx: vendor="X.Org Foundation"
[ 32.742] compiled for 1.13.0, module version = 1.0.0
[ 32.742] ABI class: X.Org Server Extension, version 7.0
[ 32.742] (==) AIGLX enabled
[ 32.742] Loading extension GLX
[ 32.742] (==) Matched fglrx as autoconfigured driver 0
[ 32.742] (==) Matched ati as autoconfigured driver 1
[ 32.742] (==) Matched fglrx as autoconfigured driver 2
[ 32.742] (==) Matched ati as autoconfigured driver 3
[ 32.742] (==) Matched vesa as autoconfigured driver 4
[ 32.742] (==) Matched modesetting as autoconfigured driver 5
[ 32.742] (==) Matched fbdev as autoconfigured driver 6
[ 32.743] (==) Assigned the driver to the xf86ConfigLayout
[ 32.743] (II) LoadModule: "fglrx"
[ 32.743] (WW) Warning, couldn't open module fglrx
[ 32.743] (II) UnloadModule: "fglrx"
[ 32.743] (II) Unloading fglrx
[ 32.743] (EE) Failed to load module "fglrx" (module does not exist, 0)
[ 32.743] (II) LoadModule: "ati"
[ 32.743] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[ 32.744] (II) Module ati: vendor="X.Org Foundation"
[ 32.744] compiled for 1.13.0, module version = 6.99.99
[ 32.744] Module class: X.Org Video Driver
[ 32.744] ABI class: X.Org Video Driver, version 13.0
[ 32.744] (II) LoadModule: "radeon"
[ 32.744] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[ 32.744] (II) Module radeon: vendor="X.Org Foundation"
[ 32.744] compiled for 1.13.0, module version = 6.99.99
[ 32.744] Module class: X.Org Video Driver
[ 32.744] ABI class: X.Org Video Driver, version 13.0
[ 32.744] (II) LoadModule: "vesa"
[ 32.745] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[ 32.745] (II) Module vesa: vendor="X.Org Foundation"
[ 32.745] compiled for 1.12.99.902, module version = 2.3.2
[ 32.745] Module class: X.Org Video Driver
[ 32.745] ABI class: X.Org Video Driver, version 13.0
[ 32.745] (II) LoadModule: "modesetting"
[ 32.745] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[ 32.745] (II) Module modesetting: vendor="X.Org Foundation"
[ 32.745] compiled for 1.13.0, module version = 0.5.0
[ 32.745] Module class: X.Org Video Driver
[ 32.745] ABI class: X.Org Video Driver, version 13.0
[ 32.745] (II) LoadModule: "fbdev"
[ 32.746] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[ 32.746] (II) Module fbdev: vendor="X.Org Foundation"
[ 32.746] compiled for 1.12.99.902, module version = 0.4.3
[ 32.746] Module class: X.Org Video Driver
[ 32.746] ABI class: X.Org Video Driver, version 13.0
[ 32.746] (==) Matched fglrx as autoconfigured driver 0
[ 32.746] (==) Matched ati as autoconfigured driver 1
[ 32.746] (==) Matched fglrx as autoconfigured driver 2
[ 32.746] (==) Matched ati as autoconfigured driver 3
[ 32.746] (==) Matched vesa as autoconfigured driver 4
[ 32.746] (==) Matched modesetting as autoconfigured driver 5
[ 32.746] (==) Matched fbdev as autoconfigured driver 6
[ 32.746] (==) Assigned the driver to the xf86ConfigLayout
[ 32.746] (II) LoadModule: "fglrx"
[ 32.746] (WW) Warning, couldn't open module fglrx
[ 32.746] (II) UnloadModule: "fglrx"
[ 32.746] (II) Unloading fglrx
[ 32.746] (EE) Failed to load module "fglrx" (module does not exist, 0)
[ 32.746] (II) LoadModule: "ati"
[ 32.747] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[ 32.747] (II) Module ati: vendor="X.Org Foundation"
[ 32.747] compiled for 1.13.0, module version = 6.99.99
[ 32.747] Module class: X.Org Video Driver
[ 32.747] ABI class: X.Org Video Driver, version 13.0
[ 32.747] (II) LoadModule: "vesa"
[ 32.747] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[ 32.747] (II) Module vesa: vendor="X.Org Foundation"
[ 32.747] compiled for 1.12.99.902, module version = 2.3.2
[ 32.747] Module class: X.Org Video Driver
[ 32.747] ABI class: X.Org Video Driver, version 13.0
[ 32.747] (II) UnloadModule: "vesa"
[ 32.747] (II) Unloading vesa
[ 32.747] (II) Failed to load module "vesa" (already loaded, 0)
[ 32.747] (II) LoadModule: "modesetting"
[ 32.747] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[ 32.748] (II) Module modesetting: vendor="X.Org Foundation"
[ 32.748] compiled for 1.13.0, module version = 0.5.0
[ 32.748] Module class: X.Org Video Driver
[ 32.748] ABI class: X.Org Video Driver, version 13.0
[ 32.748] (II) UnloadModule: "modesetting"
[ 32.748] (II) Unloading modesetting
[ 32.748] (II) Failed to load module "modesetting" (already loaded, 0)
[ 32.748] (II) LoadModule: "fbdev"
[ 32.748] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[ 32.748] (II) Module fbdev: vendor="X.Org Foundation"
[ 32.748] compiled for 1.12.99.902, module version = 0.4.3
[ 32.748] Module class: X.Org Video Driver
[ 32.748] ABI class: X.Org Video Driver, version 13.0
[ 32.748] (II) UnloadModule: "fbdev"
[ 32.748] (II) Unloading fbdev
[ 32.748] (II) Failed to load module "fbdev" (already loaded, 0)
[ 32.748] (II) RADEON: Driver for ATI Radeon chipsets:
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
SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, ATI Radeon HD 4200,
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
ARUBA, ARUBA, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI,
TAHITI, TAHITI, TAHITI, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
PITCAIRN, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
VERDE, VERDE
[ 32.755] (II) VESA: driver for VESA chipsets: vesa
[ 32.755] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[ 32.755] (II) FBDEV: driver for framebuffer: fbdev
[ 32.755] (++) using VT number 7

[ 32.755] (II) [KMS] Kernel modesetting enabled.
[ 32.755] (WW) Falling back to old probe method for vesa
[ 32.755] (WW) Falling back to old probe method for modesetting
[ 32.755] (WW) Falling back to old probe method for fbdev
[ 32.755] (II) Loading sub module "fbdevhw"
[ 32.755] (II) LoadModule: "fbdevhw"
[ 32.755] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[ 32.755] (II) Module fbdevhw: vendor="X.Org Foundation"
[ 32.756] compiled for 1.13.0, module version = 0.0.2
[ 32.756] ABI class: X.Org Video Driver, version 13.0
[ 32.756] (II) RADEON(0): Creating default Display subsection in Screen section
"Default Screen Section" for depth/fbbpp 24/32
[ 32.756] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[ 32.756] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[ 32.756] (==) RADEON(0): Default visual is TrueColor
[ 32.756] (==) RADEON(0): RGB weight 888
[ 32.756] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[ 32.756] (--) RADEON(0): Chipset: "ATI Radeon X1200" (ChipID = 0x791f)
[ 32.756] (II) Loading sub module "dri2"
[ 32.756] (II) LoadModule: "dri2"
[ 32.756] (II) Module "dri2" already built-in
[ 32.756] (II) Loading sub module "exa"
[ 32.756] (II) LoadModule: "exa"
[ 32.756] (II) Loading /usr/lib/xorg/modules/libexa.so
[ 32.756] (II) Module exa: vendor="X.Org Foundation"
[ 32.756] compiled for 1.13.0, module version = 2.6.0
[ 32.756] ABI class: X.Org Video Driver, version 13.0
[ 32.756] (II) RADEON(0): KMS Color Tiling: enabled
[ 32.756] (II) RADEON(0): KMS Pageflipping: enabled
[ 32.756] (II) RADEON(0): SwapBuffers wait for vsync: enabled
[ 32.932] (II) RADEON(0): Output VGA-0 has no monitor section
[ 32.932] (II) RADEON(0): Output LVDS has no monitor section
[ 33.108] (II) RADEON(0): Output S-video has no monitor section
[ 33.284] (II) RADEON(0): EDID for output VGA-0
[ 33.284] (II) RADEON(0): EDID for output LVDS
[ 33.284] (II) RADEON(0): Manufacturer: SEC Model: 4945 Serial#: 0
[ 33.284] (II) RADEON(0): Year: 2007 Week: 0
[ 33.284] (II) RADEON(0): EDID Version: 1.3
[ 33.284] (II) RADEON(0): Digital Display Input
[ 33.284] (II) RADEON(0): Max Image Size [cm]: horiz.: 33 vert.: 21
[ 33.284] (II) RADEON(0): Gamma: 2.20
[ 33.284] (II) RADEON(0): No DPMS capabilities specified
[ 33.284] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4
[ 33.284] (II) RADEON(0): First detailed timing is preferred mode
[ 33.284] (II) RADEON(0): redX: 0.580 redY: 0.340 greenX: 0.310 greenY: 0.550
[ 33.284] (II) RADEON(0): blueX: 0.155 blueY: 0.155 whiteX: 0.313 whiteY: 0.329
[ 33.284] (II) RADEON(0): Manufacturer's mask: 0
[ 33.284] (II) RADEON(0): Supported detailed timing:
[ 33.284] (II) RADEON(0): clock: 68.9 MHz Image Size: 331 x 207 mm
[ 33.284] (II) RADEON(0): h_active: 1280 h_sync: 1296 h_sync_end 1344 h_blank_end 1408 h_border: 0
[ 33.284] (II) RADEON(0): v_active: 800 v_sync: 801 v_sync_end 804 v_blanking: 816 v_border: 0
[ 33.284] (II) RADEON(0): Unknown vendor-specific block f
[ 33.284] (II) RADEON(0): SAMSUNG
[ 33.284] (II) RADEON(0): LTN154XA-L01
[ 33.284] (II) RADEON(0): EDID (in hex):
[ 33.284] (II) RADEON(0): 00ffffffffffff004ca3454900000000
[ 33.284] (II) RADEON(0): 00110103802115780a87f594574f8c27
[ 33.284] (II) RADEON(0): 27505400000001010101010101010101
[ 33.284] (II) RADEON(0): 010101010101ee1a0080502010301030
[ 33.284] (II) RADEON(0): 13004bcf100000190000000f00000000
[ 33.284] (II) RADEON(0): 00000000002387026401000000fe0053
[ 33.284] (II) RADEON(0): 414d53554e470a2020202020000000fe
[ 33.284] (II) RADEON(0): 004c544e31353458412d4c30310a0041
[ 33.284] (II) RADEON(0): Printing probed modes for output LVDS
[ 33.284] (II) RADEON(0): Modeline "1280x800"x60.0 68.94 1280 1296 1344 1408 800 801 804 816 -hsync -vsync (49.0 kHz eP)
[ 33.284] (II) RADEON(0): Modeline "1280x720"x59.9 74.50 1280 1344 1472 1664 720 723 728 748 -hsync +vsync (44.8 kHz)
[ 33.284] (II) RADEON(0): Modeline "1152x768"x59.8 71.75 1152 1216 1328 1504 768 771 781 798 -hsync +vsync (47.7 kHz)
[ 33.284] (II) RADEON(0): Modeline "1024x768"x59.9 63.50 1024 1072 1176 1328 768 771 775 798 -hsync +vsync (47.8 kHz)
[ 33.284] (II) RADEON(0): Modeline "800x600"x59.9 38.25 800 832 912 1024 600 603 607 624 -hsync +vsync (37.4 kHz)
[ 33.284] (II) RADEON(0): Modeline "848x480"x59.7 31.50 848 872 952 1056 480 483 493 500 -hsync +vsync (29.8 kHz)
[ 33.284] (II) RADEON(0): Modeline "720x480"x59.7 26.75 720 744 808 896 480 483 493 500 -hsync +vsync (29.9 kHz)
[ 33.284] (II) RADEON(0): Modeline "640x480"x59.4 23.75 640 664 720 800 480 483 487 500 -hsync +vsync (29.7 kHz)
[ 33.460] (II) RADEON(0): EDID for output S-video
[ 33.460] (II) RADEON(0): Output VGA-0 disconnected
[ 33.460] (II) RADEON(0): Output LVDS connected
[ 33.460] (II) RADEON(0): Output S-video disconnected
[ 33.460] (II) RADEON(0): Using exact sizes for initial modes
[ 33.460] (II) RADEON(0): Output LVDS using initial mode 1280x800
[ 33.460] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[ 33.460] (II) RADEON(0): mem size init: gart size :1fdff000 vram size: s:10000000 visible:fbd8000
[ 33.460] (II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
[ 33.460] (==) RADEON(0): DPI set to (96, 96)
[ 33.460] (II) Loading sub module "fb"
[ 33.460] (II) LoadModule: "fb"
[ 33.460] (II) Loading /usr/lib/xorg/modules/libfb.so
[ 33.460] (II) Module fb: vendor="X.Org Foundation"
[ 33.460] compiled for 1.13.0, module version = 1.0.0
[ 33.461] ABI class: X.Org ANSI C Emulation, version 0.4
[ 33.461] (II) Loading sub module "ramdac"
[ 33.461] (II) LoadModule: "ramdac"
[ 33.461] (II) Module "ramdac" already built-in
[ 33.461] (II) UnloadModule: "vesa"
[ 33.461] (II) Unloading vesa
[ 33.461] (II) UnloadModule: "modesetting"
[ 33.461] (II) Unloading modesetting
[ 33.461] (II) UnloadModule: "fbdev"
[ 33.461] (II) Unloading fbdev
[ 33.461] (II) UnloadSubModule: "fbdevhw"
[ 33.461] (II) Unloading fbdevhw
[ 33.461] (--) Depth 24 pixmap format is 32 bpp
[ 33.461] (II) RADEON(0): [DRI2] Setup complete
[ 33.461] (II) RADEON(0): [DRI2] DRI driver: r300
[ 33.461] (II) RADEON(0): [DRI2] VDPAU driver: r300
[ 33.461] (II) RADEON(0): Front buffer size: 4000K
[ 33.461] (II) RADEON(0): VRAM usage limit set to 228499K
[ 33.461] (==) RADEON(0): Backing store disabled
[ 33.461] (II) RADEON(0): Direct rendering enabled
[ 33.461] (II) RADEON(0): Render acceleration enabled for R300/R400/R500 type cards.
[ 33.461] (II) RADEON(0): Setting EXA maxPitchBytes
[ 33.461] (II) EXA(0): Driver allocated offscreen pixmaps
[ 33.461] (II) EXA(0): Driver registered support for the following operations:
[ 33.461] (II) Solid
[ 33.461] (II) Copy
[ 33.461] (II) Composite (RENDER acceleration)
[ 33.461] (II) UploadToScreen
[ 33.461] (II) DownloadFromScreen
[ 33.461] (II) RADEON(0): Acceleration enabled
[ 33.461] (==) RADEON(0): DPMS enabled
[ 33.461] (==) RADEON(0): Silken mouse enabled
[ 33.462] (II) RADEON(0): Set up textured video
[ 33.462] (II) RADEON(0): [XvMC] Associated with Radeon Textured Video.
[ 33.462] (II) RADEON(0): [XvMC] Extension initialized.
[ 33.462] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[ 33.462] (--) RandR disabled
[ 33.491] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[ 33.492] (II) AIGLX: enabled GLX_INTEL_swap_event
[ 33.492] (II) AIGLX: enabled GLX_ARB_create_context
[ 33.492] (II) AIGLX: enabled GLX_ARB_create_context_profile
[ 33.492] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[ 33.492] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[ 33.492] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[ 33.492] (II) AIGLX: Loaded and initialized r300
[ 33.492] (II) GLX: Initialized DRI2 GL provider for screen 0
[ 33.493] (II) RADEON(0): Setting screen physical size to 338 x 211
[ 33.505] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[ 33.510] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[ 33.510] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[ 33.510] (II) LoadModule: "evdev"
[ 33.510] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 33.510] (II) Module evdev: vendor="X.Org Foundation"
[ 33.510] compiled for 1.13.0, module version = 2.7.3
[ 33.510] Module class: X.Org XInput Driver
[ 33.510] ABI class: X.Org XInput driver, version 18.0
[ 33.510] (II) Using input driver 'evdev' for 'Power Button'
[ 33.510] (**) Power Button: always reports core events
[ 33.511] (**) evdev: Power Button: Device: "/dev/input/event3"
[ 33.511] (--) evdev: Power Button: Vendor 0 Product 0x1
[ 33.511] (--) evdev: Power Button: Found keys
[ 33.511] (II) evdev: Power Button: Configuring as keyboard
[ 33.511] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[ 33.511] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[ 33.511] (**) Option "xkb_rules" "evdev"
[ 33.511] (**) Option "xkb_model" "pc105"
[ 33.511] (**) Option "xkb_layout" "at"
[ 33.513] (II) XKB: reuse xkmfile /var/lib/xkb/server-11CCA49F19D9E93AF6B2C65E09D15B710633D292.xkm
[ 33.514] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[ 33.515] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[ 33.515] (II) Using input driver 'evdev' for 'Video Bus'
[ 33.515] (**) Video Bus: always reports core events
[ 33.515] (**) evdev: Video Bus: Device: "/dev/input/event5"
[ 33.515] (--) evdev: Video Bus: Vendor 0 Product 0x6
[ 33.515] (--) evdev: Video Bus: Found keys
[ 33.515] (II) evdev: Video Bus: Configuring as keyboard
[ 33.515] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1c/LNXVIDEO:01/input/input5/event5"
[ 33.515] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[ 33.515] (**) Option "xkb_rules" "evdev"
[ 33.515] (**) Option "xkb_model" "pc105"
[ 33.515] (**) Option "xkb_layout" "at"
[ 33.515] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[ 33.516] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[ 33.516] (II) Using input driver 'evdev' for 'Power Button'
[ 33.516] (**) Power Button: always reports core events
[ 33.516] (**) evdev: Power Button: Device: "/dev/input/event0"
[ 33.516] (--) evdev: Power Button: Vendor 0 Product 0x1
[ 33.516] (--) evdev: Power Button: Found keys
[ 33.516] (II) evdev: Power Button: Configuring as keyboard
[ 33.516] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[ 33.516] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[ 33.516] (**) Option "xkb_rules" "evdev"
[ 33.516] (**) Option "xkb_model" "pc105"
[ 33.516] (**) Option "xkb_layout" "at"
[ 33.517] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[ 33.517] (II) No input driver specified, ignoring this device.
[ 33.517] (II) This device may have been added with another device file.
[ 33.517] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[ 33.517] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[ 33.517] (II) Using input driver 'evdev' for 'Sleep Button'
[ 33.517] (**) Sleep Button: always reports core events
[ 33.517] (**) evdev: Sleep Button: Device: "/dev/input/event2"
[ 33.517] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[ 33.517] (--) evdev: Sleep Button: Found keys
[ 33.517] (II) evdev: Sleep Button: Configuring as keyboard
[ 33.517] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2/event2"
[ 33.517] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[ 33.517] (**) Option "xkb_rules" "evdev"
[ 33.517] (**) Option "xkb_model" "pc105"
[ 33.517] (**) Option "xkb_layout" "at"
[ 33.518] (II) config/udev: Adding drm device (/dev/dri/card0)
[ 33.518] (II) config/udev: Adding input device USB Mouse (/dev/input/event6)
[ 33.518] (**) USB Mouse: Applying InputClass "evdev pointer catchall"
[ 33.518] (II) Using input driver 'evdev' for 'USB Mouse'
[ 33.518] (**) USB Mouse: always reports core events
[ 33.518] (**) evdev: USB Mouse: Device: "/dev/input/event6"
[ 33.518] (--) evdev: USB Mouse: Vendor 0x5e3 Product 0xb
[ 33.518] (--) evdev: USB Mouse: Found 9 mouse buttons
[ 33.519] (--) evdev: USB Mouse: Found scroll wheel(s)
[ 33.519] (--) evdev: USB Mouse: Found relative axes
[ 33.519] (--) evdev: USB Mouse: Found x and y relative axes
[ 33.519] (II) evdev: USB Mouse: Configuring as mouse
[ 33.519] (II) evdev: USB Mouse: Adding scrollwheel support
[ 33.519] (**) evdev: USB Mouse: YAxisMapping: buttons 4 and 5
[ 33.519] (**) evdev: USB Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[ 33.519] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.2/usb4/4-2/4-2:1.0/input/input6/event6"
[ 33.519] (II) XINPUT: Adding extended input device "USB Mouse" (type: MOUSE, id 10)
[ 33.519] (II) evdev: USB Mouse: initialized for relative axes.
[ 33.519] (**) USB Mouse: (accel) keeping acceleration scheme 1
[ 33.519] (**) USB Mouse: (accel) acceleration profile 0
[ 33.519] (**) USB Mouse: (accel) acceleration factor: 2.000
[ 33.519] (**) USB Mouse: (accel) acceleration threshold: 4
[ 33.519] (II) config/udev: Adding input device USB Mouse (/dev/input/mouse0)
[ 33.520] (II) No input driver specified, ignoring this device.
[ 33.520] (II) This device may have been added with another device file.
[ 33.520] (II) config/udev: Adding input device HDA ATI SB Line (/dev/input/event7)
[ 33.520] (II) No input driver specified, ignoring this device.
[ 33.520] (II) This device may have been added with another device file.
[ 33.520] (II) config/udev: Adding input device HDA ATI SB Mic (/dev/input/event8)
[ 33.520] (II) No input driver specified, ignoring this device.
[ 33.520] (II) This device may have been added with another device file.
[ 33.521] (II) config/udev: Adding input device HDA ATI SB Front Headphone (/dev/input/event9)
[ 33.521] (II) No input driver specified, ignoring this device.
[ 33.521] (II) This device may have been added with another device file.
[ 33.521] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[ 33.521] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[ 33.521] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[ 33.521] (**) AT Translated Set 2 keyboard: always reports core events
[ 33.521] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[ 33.521] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[ 33.521] (--) evdev: AT Translated Set 2 keyboard: Found keys
[ 33.521] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[ 33.521] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[ 33.521] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 11)
[ 33.521] (**) Option "xkb_rules" "evdev"
[ 33.521] (**) Option "xkb_model" "pc105"
[ 33.521] (**) Option "xkb_layout" "at"
[ 33.522] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event11)
[ 33.522] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[ 33.522] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[ 33.522] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[ 33.522] (II) LoadModule: "synaptics"
[ 33.523] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[ 33.523] (II) Module synaptics: vendor="X.Org Foundation"
[ 33.523] compiled for 1.12.99.905, module version = 1.6.2
[ 33.523] Module class: X.Org XInput Driver
[ 33.523] ABI class: X.Org XInput driver, version 18.0
[ 33.523] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[ 33.523] (**) SynPS/2 Synaptics TouchPad: always reports core events
[ 33.523] (**) Option "Device" "/dev/input/event11"
[ 33.528] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[ 33.528] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[ 33.528] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[ 33.528] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[ 33.528] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple scroll-buttons
[ 33.528] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[ 33.528] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[ 33.528] (**) SynPS/2 Synaptics TouchPad: always reports core events
[ 33.528] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio2/input/input11/event11"
[ 33.528] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 12)
[ 33.528] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[ 33.528] (**) synaptics: SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[ 33.528] (**) synaptics: SynPS/2 Synaptics TouchPad: AccelFactor is now 0.040
[ 33.529] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[ 33.529] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[ 33.529] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[ 33.529] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[ 33.529] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[ 33.529] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
[ 33.529] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[ 33.532] (II) config/udev: Adding input device Acer BMA150 accelerometer (/dev/input/event10)
[ 33.532] (II) No input driver specified, ignoring this device.
[ 33.532] (II) This device may have been added with another device file.
[ 33.532] (II) config/udev: Adding input device Acer BMA150 accelerometer (/dev/input/js0)
[ 33.532] (II) No input driver specified, ignoring this device.
[ 33.532] (II) This device may have been added with another device file.
[ 35.284] (II) RADEON(0): EDID vendor "SEC", prod id 18757
[ 35.284] (II) RADEON(0): Printing DDC gathered Modelines:
[ 35.284] (II) RADEON(0): Modeline "1280x800"x0.0 68.94 1280 1296 1344 1408 800 801 804 816 -hsync -vsync (49.0 kHz eP)
[ 36.936] (II) RADEON(0): EDID vendor "SEC", prod id 18757
[ 36.936] (II) RADEON(0): Printing DDC gathered Modelines:
[ 36.936] (II) RADEON(0): Modeline "1280x800"x0.0 68.94 1280 1296 1344 1408 800 801 804 816 -hsync -vsync (49.0 kHz eP)
[ 45.104] (II) RADEON(0): EDID vendor "SEC", prod id 18757
[ 45.104] (II) RADEON(0): Printing DDC gathered Modelines:
[ 45.104] (II) RADEON(0): Modeline "1280x800"x0.0 68.94 1280 1296 1344 1408 800 801 804 816 -hsync -vsync (49.0 kHz eP)
[ 45.860] (II) RADEON(0): EDID vendor "SEC", prod id 18757
[ 45.860] (II) RADEON(0): Printing DDC gathered Modelines:
[ 45.860] (II) RADEON(0): Modeline "1280x800"x0.0 68.94 1280 1296 1344 1408 800 801 804 816 -hsync -vsync (49.0 kHz eP)
[ 46.504] (II) RADEON(0): EDID vendor "SEC", prod id 18757
[ 46.504] (II) RADEON(0): Printing DDC gathered Modelines:
[ 46.504] (II) RADEON(0): Modeline "1280x800"x0.0 68.94 1280 1296 1344 1408 800 801 804 816 -hsync -vsync (49.0 kHz eP)
[ 48.760] (II) RADEON(0): EDID vendor "SEC", prod id 18757
[ 48.760] (II) RADEON(0): Printing DDC gathered Modelines:
[ 48.760] (II) RADEON(0): Modeline "1280x800"x0.0 68.94 1280 1296 1344 1408 800 801 804 816 -hsync -vsync (49.0 kHz eP)
[ 54.446] (II) XKB: reuse xkmfile /var/lib/xkb/server-B1D4F474CAA842C2A43A2A00D988632A8736FEC8.xkm
[ 66.564] (II) RADEON(0): EDID vendor "SEC", prod id 18757
[ 66.564] (II) RADEON(0): Printing DDC gathered Modelines:
[ 66.564] (II) RADEON(0): Modeline "1280x800"x0.0 68.94 1280 1296 1344 1408 800 801 804 816 -hsync -vsync (49.0 kHz eP)
[ 798.501] (II) config/udev: removing device USB Mouse
[ 799.348] (II) evdev: USB Mouse: Close
[ 799.349] (II) UnloadModule: "evdev"
[ 805.638] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/event6)
[ 805.684] (**) USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[ 805.684] (II) Using input driver 'evdev' for 'USB Optical Mouse'
[ 805.684] (**) USB Optical Mouse: always reports core events
[ 805.684] (**) evdev: USB Optical Mouse: Device: "/dev/input/event6"
[ 805.692] (--) evdev: USB Optical Mouse: Vendor 0x192f Product 0x616
[ 805.692] (--) evdev: USB Optical Mouse: Found 9 mouse buttons
[ 805.692] (--) evdev: USB Optical Mouse: Found scroll wheel(s)
[ 805.692] (--) evdev: USB Optical Mouse: Found relative axes
[ 805.692] (--) evdev: USB Optical Mouse: Found x and y relative axes
[ 805.693] (II) evdev: USB Optical Mouse: Configuring as mouse
[ 805.693] (II) evdev: USB Optical Mouse: Adding scrollwheel support
[ 805.693] (**) evdev: USB Optical Mouse: YAxisMapping: buttons 4 and 5
[ 805.693] (**) evdev: USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[ 805.708] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.2/usb4/4-2/4-2:1.0/input/input12/event6"
[ 805.708] (II) XINPUT: Adding extended input device "USB Optical Mouse" (type: MOUSE, id 10)
[ 805.708] (II) evdev: USB Optical Mouse: initialized for relative axes.
[ 805.709] (**) USB Optical Mouse: (accel) keeping acceleration scheme 1
[ 805.709] (**) USB Optical Mouse: (accel) acceleration profile 0
[ 805.710] (**) USB Optical Mouse: (accel) acceleration factor: 2.000
[ 805.710] (**) USB Optical Mouse: (accel) acceleration threshold: 4
[ 805.712] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/mouse0)
[ 805.712] (II) No input driver specified, ignoring this device.
[ 805.712] (II) This device may have been added with another device file.
[ 5470.839] (II) RADEON(0): EDID vendor "SEC", prod id 18757
[ 5470.857] (II) RADEON(0): Printing DDC gathered Modelines:
[ 5470.857] (II) RADEON(0): Modeline "1280x800"x0.0 68.94 1280 1296 1344 1408 800 801 804 816 -hsync -vsync (49.0 kHz eP)
[ 7431.895] (II) RADEON(0): EDID vendor "SEC", prod id 18757
[ 7431.957] (II) RADEON(0): Printing DDC gathered Modelines:
[ 7431.957] (II) RADEON(0): Modeline "1280x800"x0.0 68.94 1280 1296 1344 1408 800 801 804 816 -hsync -vsync (49.0 kHz eP)
[ 7432.560] (II) RADEON(0): EDID vendor "SEC", prod id 18757
[ 7432.560] (II) RADEON(0): Printing DDC gathered Modelines:
[ 7432.560] (II) RADEON(0): Modeline "1280x800"x0.0 68.94 1280 1296 1344 1408 800 801 804 816 -hsync -vsync (49.0 kHz eP)
[ 7433.700] (II) RADEON(0): EDID vendor "SEC", prod id 18757
[ 7433.700] (II) RADEON(0): Printing DDC gathered Modelines:
[ 7433.700] (II) RADEON(0): Modeline "1280x800"x0.0 68.94 1280 1296 1344 1408 800 801 804 816 -hsync -vsync (49.0 kHz eP)
[ 7434.060] (II) RADEON(0): EDID vendor "SEC", prod id 18757
[ 7434.062] (II) RADEON(0): Printing DDC gathered Modelines:
[ 7434.063] (II) RADEON(0): Modeline "1280x800"x0.0 68.94 1280 1296 1344 1408 800 801 804 816 -hsync -vsync (49.0 kHz eP)
[ 7434.580] (II) RADEON(0): EDID vendor "SEC", prod id 18757
[ 7434.580] (II) RADEON(0): Printing DDC gathered Modelines:
[ 7434.580] (II) RADEON(0): Modeline "1280x800"x0.0 68.94 1280 1296 1344 1408 800 801 804 816 -hsync -vsync (49.0 kHz eP)
[ 7440.880] (II) RADEON(0): EDID vendor "SEC", prod id 18757
[ 7440.880] (II) RADEON(0): Printing DDC gathered Modelines:
[ 7440.880] (II) RADEON(0): Modeline "1280x800"x0.0 68.94 1280 1296 1344 1408 800 801 804 816 -hsync -vsync (49.0 kHz eP)
[ 8430.779] (II) RADEON(0): EDID vendor "SEC", prod id 18757
[ 8430.850] (II) RADEON(0): Printing DDC gathered Modelines:
[ 8430.850] (II) RADEON(0): Modeline "1280x800"x0.0 68.94 1280 1296 1344 1408 800 801 804 816 -hsync -vsync (49.0 kHz eP) 
```

---

### Post by Yellow Pasque on 2013-02-24
The log looks fine. I'm not sure what to suggest other than running a lighter desktop (xubuntu).

---

### Post by FreeRide23 on 2013-02-24
hmmm ok... if u say so.

But there is definatly something wrong with this PC!!! Its realy anoying slow.

Are you shure that this is suppose to be so!?

Couse there was an Windows Vista on it bevore, and this was also runing faster then the Ubuntu now...

---

### Post by FreeRide23 on 2013-02-24
Sorry u have to be wrong...

the problem on startup is still there!

There is a BLACK BLANK screen... i have to press STRG+ALT+1 to come to terminal then press STRG+ALT+7 again to come to the GUI, to see the passphrase login...

so the GPU is messed up... somehow. Can u tell me where do i have to digg deeper?

---

### Post by FreeRide23 on 2013-02-24
Update: i found three posible solutions, what is your opinion?

[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.2.3.2&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.2.3.2&lang=English)

[http://support.amd.com/de/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/de/gpudownload/linux/Pages/radeon_linux.aspx)

[http://support.amd.com/de/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/de/gpudownload/linux/Pages/radeon_linux.aspx)

---

### Post by Yellow Pasque on 2013-02-24
> **FreeRide23 said:**
> Update: i found three posible solutions, what is your opinion?

[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.2.3.2&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.2.3.2&lang=English)

[http://support.amd.com/de/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/de/gpudownload/linux/Pages/radeon_linux.aspx)

[http://support.amd.com/de/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/de/gpudownload/linux/Pages/radeon_linux.aspx)
Trying to install any other driver will make things worse...

Only the Catalyst 9.3 supports your card, and it is far too old to work with modern versions of Ununtu

---

### Post by FreeRide23 on 2013-02-24
Ok. Then how do i find out whats wrong with my GUI!?

---

### Post by Yellow Pasque on 2013-02-24
> **FreeRide23 said:**
> Ok. Then how do i find out whats wrong with my GUI!?
I'm out of ideas. Hopefully, someone else has an idea..

---

### Post by FreeRide23 on 2013-02-24
So i did a little testing...


vsync_mode=0 glxgears shows up 296 frames... so this seems to be ok.

i also did a SMAR test on the HDD, but nothing spectacilous there...

I have observed that the problem appears, when some "big" Programms like Ubuntu software center shows up, the windows will be "grayed" and is frozen for almost 5-10 seconds...

Also the boot problem is still there... i have to switch between shell and then GUI with the key combination STRG+ALT+7

I also observed that the appearance of stuff (linke tiped text in the dash) is like slow motion...

I think about what u sayed, can it realy be that this GPU is SOOO SLOW!?

How can i verify that, and not that it is an other problem!?

My problem is, that i committed an friend of mine (the customer) to get to ubuntu, because his pc was not the fastest (win vista with a lot of stuff on it), to look forward to an faster system... and now this... slow as hell and i cant find the cause.

How can i make a display of wich information u need?

Found that i should paste /var/log/syslog

will do when i next time boot (takes, to finish the other stuff)

cya

---

### Post by FreeRide23 on 2013-02-24
Ok so far, i got some progress.

Well the /var/log/syslog is FULL of 

> NetworkManager [990]: <info> (eth0): carrier now OFF (device state 100, deferring action for 4 seconds)
NetworkManager [990]: <info> (eth0): carrier now ON (device state 100)
NetworkManager [990]: <info> (eth0): carrier now OFF (device state 100, deferring action for 4 seconds)
NetworkManager [990]: <info> (eth0): carrier now ON (device state 100)
NetworkManager [990]: <info> (eth0): carrier now OFF (device state 100, deferring action for 4 seconds)
NetworkManager [990]: <info> (eth0): carrier now ON (device state 100)

really full!
I have plugged in an USB-LAN adapter, cause the onboard LAN is probably dead...

can this be the problem!?

---

### Post by FreeRide23 on 2013-02-24
Nope it doesnt solve the problem... still laggy.

I am looking forward to an tool or shell command to clear the syslog, to make an fresh cold reboot to post u some logs... without a lot of crap...

I just read that Ubuntu 12.10 is now without Unity 2D, so i even cannot loggout and login with 2D effects only...

so maybe livmpipe is the cause...

---

### Post by FreeRide23 on 2013-02-24
How can i find out if LLVMpipe is the cause, so i will downgrade to 12.04...

---

### Post by FreeRide23 on 2013-02-24
Seriously not helpful this forum.

Downgradet to 12.04 LTS... deaktivate 3D stuff and go to 2D Unity...

gn8 hf gl

---

### Post by QIII on 2013-02-24
&#65279;Everyone's issues are very important to them and we certainly understand that. Some things are terribly frustrating!

Let me assure you that you are not being ignored.
 
This is a volunteer community of users from all around the world. Not everyone here can answer every question immediately. The person with just the right answer may live in Kolkata and be asleep at the time you post, or in Geneva having dinner with his/her family or Des Moines at work. Sometimes it takes a bit for us to get to the forums and answer questions.
 
So please do not take it as a snub if you question is not answered immediately.
 
Give it 24 hours to make the rounds before bumping. Sometimes an odd bump at 36 hours or something might catch other people in a different time zone at their computers.

---

### Post by Yellow Pasque on 2013-02-24
> **FreeRide23 said:**
> How can i find out if LLVMpipe is the cause, so i will downgrade to 12.04...
That's part of why I had you post Xorg.log (to make sure you did have 3D hardware accel and not llvmpipe).

---

