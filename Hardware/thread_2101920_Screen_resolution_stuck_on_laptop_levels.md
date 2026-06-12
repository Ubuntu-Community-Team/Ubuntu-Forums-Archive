---
title: "Screen resolution stuck on laptop levels"
date: 2013-01-05
forum: Hardware
---

### Post by patman0623 on 2013-01-05
I moved my hard-drive with its Ubuntu installation from my laptop computer into my desktop computer because some of the hardware on the laptop failed.

However, it is stuck on a laptop resolution, and the screen is constantly over-stretched horizontally.

If I try going into "displays" in the setting panel, it does not give me an option to move off of the laptop display, and clicking "detect displays" does nothing.

What can I do?

I've posted my lspci below for reference:

```
$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (int gfx)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 1)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller
00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 3c)
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS880 [Radeon HD 4200]
01:05.1 Audio device: Advanced Micro Devices [AMD] nee ATI RS880 HDMI Audio [Radeon HD 4200 Series]
02:00.0 Network controller: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)

```

---

### Post by Yellow Pasque on 2013-01-05
Post /var/log/Xorg.0.log

---

### Post by patman0623 on 2013-01-05
> **Temüjin said:**
> Post /var/log/Xorg.0.log

```
[    34.857] 
X.Org X Server 1.13.0
Release Date: 2012-09-05
[    34.857] X Protocol Version 11, Revision 0
[    34.857] Build Operating System: Linux 3.2.0-32-generic x86_64 Ubuntu
[    34.857] Current Operating System: Linux patrick-Notebook-Ubuntu 3.5.0-21-generic #32-Ubuntu SMP Tue Dec 11 18:51:59 UTC 2012 x86_64
[    34.857] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-21-generic root=UUID=f2347f51-daec-4ef5-a86b-2d7866993f06 ro quiet splash vt.handoff=7
[    34.857] Build Date: 27 November 2012  07:44:35AM
[    34.857] xorg-server 2:1.13.0-0ubuntu6.1 (For technical support please see http://www.ubuntu.com/support) 
[    34.857] Current version of pixman: 0.26.0
[    34.857] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    34.857] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    34.857] (==) Log file: "/var/log/Xorg.0.log", Time: Thu May 12 22:59:53 2011
[    34.857] (==) Using config file: "/etc/X11/xorg.conf"
[    34.857] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    34.857] (==) No Layout section.  Using the first Screen section.
[    34.857] (**) |-->Screen "Default Screen" (0)
[    34.857] (**) |   |-->Monitor "<default monitor>"
[    34.857] (==) No monitor specified for screen "Default Screen".
	Using a default monitor configuration.
[    34.857] (==) Automatically adding devices
[    34.857] (==) Automatically enabling devices
[    34.857] (==) Automatically adding GPU devices
[    34.857] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    34.857] 	Entry deleted from font path.
[    34.857] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    34.857] 	Entry deleted from font path.
[    34.857] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    34.857] 	Entry deleted from font path.
[    34.858] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    34.858] 	Entry deleted from font path.
[    34.858] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    34.858] 	Entry deleted from font path.
[    34.858] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    34.858] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    34.858] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    34.858] (II) Loader magic: 0x7f1d0f09ac40
[    34.858] (II) Module ABI versions:
[    34.858] 	X.Org ANSI C Emulation: 0.4
[    34.858] 	X.Org Video Driver: 13.0
[    34.858] 	X.Org XInput driver : 18.0
[    34.858] 	X.Org Server Extension : 7.0
[    34.858] (--) PCI:*(0:1:5:0) 1002:9710:103c:2ab1 rev 0, Mem @ 0xd0000000/268435456, 0xfe8f0000/65536, 0xfe900000/1048576, I/O @ 0x0000d000/256
[    34.859] (II) Open ACPI successful (/var/run/acpid.socket)
[    34.859] Initializing built-in extension Generic Event Extension
[    34.859] Initializing built-in extension SHAPE
[    34.859] Initializing built-in extension MIT-SHM
[    34.859] Initializing built-in extension XInputExtension
[    34.859] Initializing built-in extension XTEST
[    34.859] Initializing built-in extension BIG-REQUESTS
[    34.859] Initializing built-in extension SYNC
[    34.859] Initializing built-in extension XKEYBOARD
[    34.859] Initializing built-in extension XC-MISC
[    34.859] Initializing built-in extension SECURITY
[    34.859] Initializing built-in extension XINERAMA
[    34.859] Initializing built-in extension XFIXES
[    34.859] Initializing built-in extension RENDER
[    34.859] Initializing built-in extension RANDR
[    34.859] Initializing built-in extension COMPOSITE
[    34.859] Initializing built-in extension DAMAGE
[    34.859] Initializing built-in extension MIT-SCREEN-SAVER
[    34.859] Initializing built-in extension DOUBLE-BUFFER
[    34.859] Initializing built-in extension RECORD
[    34.859] Initializing built-in extension DPMS
[    34.859] Initializing built-in extension X-Resource
[    34.859] Initializing built-in extension XVideo
[    34.859] Initializing built-in extension XVideo-MotionCompensation
[    34.859] Initializing built-in extension XFree86-VidModeExtension
[    34.859] Initializing built-in extension XFree86-DGA
[    34.859] Initializing built-in extension XFree86-DRI
[    34.859] Initializing built-in extension DRI2
[    34.859] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    34.859] (II) LoadModule: "glx"
[    34.887] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/extensions/libglx.so
[    34.887] (II) Module glx: vendor="Advanced Micro Devices, Inc."
[    34.887] 	compiled for 6.9.0, module version = 1.0.0
[    34.887] Loading extension GLX
[    34.887] (==) Matched fglrx as autoconfigured driver 0
[    34.887] (==) Matched ati as autoconfigured driver 1
[    34.887] (==) Matched vesa as autoconfigured driver 2
[    34.887] (==) Matched modesetting as autoconfigured driver 3
[    34.887] (==) Matched fbdev as autoconfigured driver 4
[    34.887] (==) Assigned the driver to the xf86ConfigLayout
[    34.887] (II) LoadModule: "fglrx"
[    34.887] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/drivers/fglrx_drv.so
[    34.900] (II) Module fglrx: vendor="FireGL - AMD Technologies Inc."
[    34.900] 	compiled for 1.4.99.906, module version = 9.0.2
[    34.900] 	Module class: X.Org Video Driver
[    34.901] (II) Loading sub module "fglrxdrm"
[    34.901] (II) LoadModule: "fglrxdrm"
[    34.901] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/linux/libfglrxdrm.so
[    34.901] (II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
[    34.901] 	compiled for 1.4.99.906, module version = 9.0.2
[    34.901] (II) LoadModule: "ati"
[    34.901] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    34.901] (II) Module ati: vendor="X.Org Foundation"
[    34.901] 	compiled for 1.13.0, module version = 6.99.99
[    34.901] 	Module class: X.Org Video Driver
[    34.901] 	ABI class: X.Org Video Driver, version 13.0
[    34.901] (II) LoadModule: "radeon"
[    34.902] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    34.902] (II) Module radeon: vendor="X.Org Foundation"
[    34.902] 	compiled for 1.13.0, module version = 6.99.99
[    34.902] 	Module class: X.Org Video Driver
[    34.902] 	ABI class: X.Org Video Driver, version 13.0
[    34.902] (II) LoadModule: "vesa"
[    34.902] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    34.902] (II) Module vesa: vendor="X.Org Foundation"
[    34.902] 	compiled for 1.12.99.902, module version = 2.3.2
[    34.902] 	Module class: X.Org Video Driver
[    34.902] 	ABI class: X.Org Video Driver, version 13.0
[    34.902] (II) LoadModule: "modesetting"
[    34.902] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    34.902] (II) Module modesetting: vendor="X.Org Foundation"
[    34.902] 	compiled for 1.13.0, module version = 0.5.0
[    34.902] 	Module class: X.Org Video Driver
[    34.902] 	ABI class: X.Org Video Driver, version 13.0
[    34.902] (II) LoadModule: "fbdev"
[    34.902] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    34.903] (II) Module fbdev: vendor="X.Org Foundation"
[    34.903] 	compiled for 1.12.99.902, module version = 0.4.3
[    34.903] 	Module class: X.Org Video Driver
[    34.903] 	ABI class: X.Org Video Driver, version 13.0
[    34.903] (II) AMD Proprietary Linux Driver Version Identifier:9.00.2
[    34.903] (II) AMD Proprietary Linux Driver Release Identifier: 9.00.11                              
[    34.903] (II) AMD Proprietary Linux Driver Build Date: Sep 20 2012 11:56:16
[    34.903] (II) RADEON: Driver for ATI Radeon chipsets:
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
[    34.905] (II) VESA: driver for VESA chipsets: vesa
[    34.905] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    34.905] (II) FBDEV: driver for framebuffer: fbdev
[    34.905] (++) using VT number 7

[    34.905] (WW) Falling back to old probe method for fglrx
[    34.910] (II) Loading PCS database from /etc/ati/amdpcsdb /etc/ati/amdpcsdb.default
[    35.320] ukiDynamicMajor: failed to open /proc/ati/major
[    35.321] (EE) No supported AMD display adapters were found
[    35.321] (II) [KMS] drm report modesetting isn't supported.
[    35.321] (WW) Falling back to old probe method for modesetting
[    35.321] (EE) open /dev/dri/card0: No such file or directory
[    35.321] (WW) Falling back to old probe method for fbdev
[    35.321] (II) Loading sub module "fbdevhw"
[    35.321] (II) LoadModule: "fbdevhw"
[    35.321] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    35.321] (II) Module fbdevhw: vendor="X.Org Foundation"
[    35.321] 	compiled for 1.13.0, module version = 0.0.2
[    35.321] 	ABI class: X.Org Video Driver, version 13.0
[    35.321] (EE) Screen 0 deleted because of no matching config section.
[    35.321] (II) UnloadModule: "radeon"
[    35.321] (II) Loading sub module "vbe"
[    35.321] (II) LoadModule: "vbe"
[    35.321] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    35.321] (II) Module vbe: vendor="X.Org Foundation"
[    35.321] 	compiled for 1.13.0, module version = 1.1.0
[    35.321] 	ABI class: X.Org Video Driver, version 13.0
[    35.321] (II) Loading sub module "int10"
[    35.321] (II) LoadModule: "int10"
[    35.321] (II) Loading /usr/lib/xorg/modules/libint10.so
[    35.386] (II) Module int10: vendor="X.Org Foundation"
[    35.386] 	compiled for 1.13.0, module version = 1.0.0
[    35.386] 	ABI class: X.Org Video Driver, version 13.0
[    35.386] (II) VESA(0): initializing int10
[    35.390] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    35.391] (II) VESA(0): VESA BIOS detected
[    35.391] (II) VESA(0): VESA VBE Version 3.0
[    35.391] (II) VESA(0): VESA VBE Total Mem: 16384 kB
[    35.391] (II) VESA(0): VESA VBE OEM: ATI ATOMBIOS
[    35.391] (II) VESA(0): VESA VBE OEM Software Rev: 10.94
[    35.391] (II) VESA(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
[    35.391] (II) VESA(0): VESA VBE OEM Product: RS880
[    35.391] (II) VESA(0): VESA VBE OEM Product Rev: 01.00
[    35.463] (II) VESA(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
[    35.463] (**) VESA(0): Depth 24, (--) framebuffer bpp 32
[    35.463] (==) VESA(0): RGB weight 888
[    35.463] (==) VESA(0): Default visual is TrueColor
[    35.463] (==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
[    35.463] (II) Loading sub module "ddc"
[    35.463] (II) LoadModule: "ddc"
[    35.463] (II) Module "ddc" already built-in
[    35.463] (II) VESA VBE DDC supported
[    35.463] (II) VESA VBE DDC Level 2
[    35.463] (II) VESA VBE DDC transfer in appr. 1 sec.
[    35.630] (II) VESA VBE DDC read successfully
[    35.630] (II) Manufacturer: ACR  Model: 1a8  Serial#: 289430725
[    35.630] (II) Year: 2011  Week: 14
[    35.630] (II) EDID Version: 1.3
[    35.630] (II) Digital Display Input
[    35.630] (II) Max Image Size [cm]: horiz.: 44  vert.: 25
[    35.630] (II) Gamma: 2.20
[    35.630] (II) DPMS capabilities: Off
[    35.630] (II) Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    35.630] (II) First detailed timing is preferred mode
[    35.630] (II) redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
[    35.630] (II) blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
[    35.630] (II) Supported established timings:
[    35.630] (II) 720x400@70Hz
[    35.630] (II) 640x480@60Hz
[    35.630] (II) 640x480@67Hz
[    35.630] (II) 640x480@72Hz
[    35.630] (II) 640x480@75Hz
[    35.630] (II) 800x600@56Hz
[    35.630] (II) 800x600@60Hz
[    35.630] (II) 800x600@72Hz
[    35.630] (II) 800x600@75Hz
[    35.630] (II) 832x624@75Hz
[    35.630] (II) 1024x768@60Hz
[    35.630] (II) 1024x768@70Hz
[    35.630] (II) 1024x768@75Hz
[    35.630] (II) 1152x864@75Hz
[    35.630] (II) Manufacturer's mask: 0
[    35.630] (II) Supported standard timings:
[    35.630] (II) #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    35.630] (II) #1: hsize: 1280  vsize 720  refresh: 60  vid: 49281
[    35.630] (II) #2: hsize: 1280  vsize 800  refresh: 60  vid: 129
[    35.630] (II) #3: hsize: 1600  vsize 900  refresh: 60  vid: 49321
[    35.630] (II) Supported detailed timing:
[    35.630] (II) clock: 108.0 MHz   Image Size:  443 x 249 mm
[    35.630] (II) h_active: 1600  h_sync: 1624  h_sync_end 1704 h_blank_end 1800 h_border: 0
[    35.630] (II) v_active: 900  v_sync: 901  v_sync_end 904 v_blanking: 1000 v_border: 0
[    35.630] (II) Ranges: V min: 50 V max: 76 Hz, H min: 30 H max: 80 kHz, PixClock max 165 MHz
[    35.630] (II) Serial No: LP1080064223
[    35.630] (II) Monitor name: Acer P206HL
[    35.630] (II) EDID (in hex):
[    35.630] (II) 	00ffffffffffff000472a801c55c4011
[    35.630] (II) 	0e150103802c19782aee91a3544c9926
[    35.630] (II) 	0f5054bfee80714f81c08100a9c00101
[    35.630] (II) 	010101010101302a40c8608464301850
[    35.630] (II) 	1300bbf91000001e000000fd00324c1e
[    35.630] (II) 	5010000a202020202020000000ff004c
[    35.630] (II) 	50313038303036343232330a000000fc
[    35.630] (II) 	00416365722050323036484c0a2000bd
[    35.630] (II) VESA(0): EDID vendor "ACR", prod id 424
[    35.630] (II) Using EDID range info for horizontal sync
[    35.630] (II) Using EDID range info for vertical refresh
[    35.630] (II) VESA(0): Printing DDC gathered Modelines:
[    35.630] (II) VESA(0): Modeline "1600x900"x0.0  108.00  1600 1624 1704 1800  900 901 904 1000 +hsync +vsync (60.0 kHz eP)
[    35.630] (II) VESA(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    35.630] (II) VESA(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    35.630] (II) VESA(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    35.630] (II) VESA(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    35.630] (II) VESA(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    35.630] (II) VESA(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    35.630] (II) VESA(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    35.630] (II) VESA(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    35.630] (II) VESA(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    35.630] (II) VESA(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    35.630] (II) VESA(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    35.630] (II) VESA(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    35.630] (II) VESA(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    35.630] (II) VESA(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    35.630] (II) VESA(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[    35.630] (II) VESA(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[    35.630] (II) VESA(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[    35.630] (II) VESA(0): Searching for matching VESA mode(s):
[    35.631] Mode: 100 (640x400)
[    35.631] 	ModeAttributes: 0xbb
[    35.631] 	WinAAttributes: 0x7
[    35.631] 	WinBAttributes: 0x0
[    35.631] 	WinGranularity: 64
[    35.631] 	WinSize: 64
[    35.631] 	WinASegment: 0xa000
[    35.631] 	WinBSegment: 0x0
[    35.631] 	WinFuncPtr: 0xc00054b3
[    35.631] 	BytesPerScanline: 640
[    35.631] 	XResolution: 640
[    35.631] 	YResolution: 400
[    35.631] 	XCharSize: 8
[    35.631] 	YCharSize: 16
[    35.631] 	NumberOfPlanes: 1
[    35.631] 	BitsPerPixel: 8
[    35.631] 	NumberOfBanks: 1
[    35.631] 	MemoryModel: 4
[    35.631] 	BankSize: 0
[    35.631] 	NumberOfImages: 63
[    35.631] 	RedMaskSize: 0
[    35.631] 	RedFieldPosition: 0
[    35.631] 	GreenMaskSize: 0
[    35.631] 	GreenFieldPosition: 0
[    35.631] 	BlueMaskSize: 0
[    35.631] 	BlueFieldPosition: 0
[    35.631] 	RsvdMaskSize: 0
[    35.631] 	RsvdFieldPosition: 0
[    35.631] 	DirectColorModeInfo: 0
[    35.631] 	PhysBasePtr: 0xd0000000
[    35.631] 	LinBytesPerScanLine: 640
[    35.631] 	BnkNumberOfImagePages: 63
[    35.631] 	LinNumberOfImagePages: 63
[    35.631] 	LinRedMaskSize: 0
[    35.631] 	LinRedFieldPosition: 0
[    35.631] 	LinGreenMaskSize: 0
[    35.631] 	LinGreenFieldPosition: 0
[    35.631] 	LinBlueMaskSize: 0
[    35.631] 	LinBlueFieldPosition: 0
[    35.631] 	LinRsvdMaskSize: 0
[    35.631] 	LinRsvdFieldPosition: 0
[    35.631] 	MaxPixelClock: 400000000
[    35.632] Mode: 101 (640x480)
[    35.632] 	ModeAttributes: 0xbb
[    35.632] 	WinAAttributes: 0x7
[    35.632] 	WinBAttributes: 0x0
[    35.632] 	WinGranularity: 64
[    35.632] 	WinSize: 64
[    35.632] 	WinASegment: 0xa000
[    35.632] 	WinBSegment: 0x0
[    35.632] 	WinFuncPtr: 0xc00054b3
[    35.632] 	BytesPerScanline: 640
[    35.632] 	XResolution: 640
[    35.632] 	YResolution: 480
[    35.632] 	XCharSize: 8
[    35.632] 	YCharSize: 16
[    35.632] 	NumberOfPlanes: 1
[    35.632] 	BitsPerPixel: 8
[    35.632] 	NumberOfBanks: 1
[    35.632] 	MemoryModel: 4
[    35.632] 	BankSize: 0
[    35.632] 	NumberOfImages: 50
[    35.632] 	RedMaskSize: 0
[    35.632] 	RedFieldPosition: 0
[    35.632] 	GreenMaskSize: 0
[    35.632] 	GreenFieldPosition: 0
[    35.632] 	BlueMaskSize: 0
[    35.632] 	BlueFieldPosition: 0
[    35.632] 	RsvdMaskSize: 0
[    35.632] 	RsvdFieldPosition: 0
[    35.632] 	DirectColorModeInfo: 0
[    35.632] 	PhysBasePtr: 0xd0000000
[    35.632] 	LinBytesPerScanLine: 640
[    35.632] 	BnkNumberOfImagePages: 50
[    35.632] 	LinNumberOfImagePages: 50
[    35.632] 	LinRedMaskSize: 0
[    35.632] 	LinRedFieldPosition: 0
[    35.632] 	LinGreenMaskSize: 0
[    35.632] 	LinGreenFieldPosition: 0
[    35.632] 	LinBlueMaskSize: 0
[    35.632] 	LinBlueFieldPosition: 0
[    35.632] 	LinRsvdMaskSize: 0
[    35.632] 	LinRsvdFieldPosition: 0
[    35.632] 	MaxPixelClock: 400000000
[    35.633] Mode: 103 (800x600)
[    35.633] 	ModeAttributes: 0xbb
[    35.633] 	WinAAttributes: 0x7
[    35.633] 	WinBAttributes: 0x0
[    35.633] 	WinGranularity: 64
[    35.633] 	WinSize: 64
[    35.633] 	WinASegment: 0xa000
[    35.633] 	WinBSegment: 0x0
[    35.633] 	WinFuncPtr: 0xc00054b3
[    35.633] 	BytesPerScanline: 832
[    35.633] 	XResolution: 800
[    35.633] 	YResolution: 600
[    35.633] 	XCharSize: 8
[    35.633] 	YCharSize: 14
[    35.633] 	NumberOfPlanes: 1
[    35.633] 	BitsPerPixel: 8
[    35.633] 	NumberOfBanks: 1
[    35.633] 	MemoryModel: 4
[    35.633] 	BankSize: 0
[    35.633] 	NumberOfImages: 31
[    35.633] 	RedMaskSize: 0
[    35.633] 	RedFieldPosition: 0
[    35.633] 	GreenMaskSize: 0
[    35.633] 	GreenFieldPosition: 0
[    35.633] 	BlueMaskSize: 0
[    35.633] 	BlueFieldPosition: 0
[    35.633] 	RsvdMaskSize: 0
[    35.633] 	RsvdFieldPosition: 0
[    35.633] 	DirectColorModeInfo: 0
[    35.633] 	PhysBasePtr: 0xd0000000
[    35.633] 	LinBytesPerScanLine: 832
[    35.633] 	BnkNumberOfImagePages: 31
[    35.633] 	LinNumberOfImagePages: 31
[    35.633] 	LinRedMaskSize: 0
[    35.633] 	LinRedFieldPosition: 0
[    35.634] 	LinGreenMaskSize: 0
[    35.634] 	LinGreenFieldPosition: 0
[    35.634] 	LinBlueMaskSize: 0
[    35.634] 	LinBlueFieldPosition: 0
[    35.634] 	LinRsvdMaskSize: 0
[    35.634] 	LinRsvdFieldPosition: 0
[    35.634] 	MaxPixelClock: 400000000
[    35.634] Mode: 105 (1024x768)
[    35.635] 	ModeAttributes: 0xbb
[    35.635] 	WinAAttributes: 0x7
[    35.635] 	WinBAttributes: 0x0
[    35.635] 	WinGranularity: 64
[    35.635] 	WinSize: 64
[    35.635] 	WinASegment: 0xa000
[    35.635] 	WinBSegment: 0x0
[    35.635] 	WinFuncPtr: 0xc00054b3
[    35.635] 	BytesPerScanline: 1024
[    35.635] 	XResolution: 1024
[    35.635] 	YResolution: 768
[    35.635] 	XCharSize: 8
[    35.635] 	YCharSize: 16
[    35.635] 	NumberOfPlanes: 1
[    35.635] 	BitsPerPixel: 8
[    35.635] 	NumberOfBanks: 1
[    35.635] 	MemoryModel: 4
[    35.635] 	BankSize: 0
[    35.635] 	NumberOfImages: 18
[    35.635] 	RedMaskSize: 0
[    35.635] 	RedFieldPosition: 0
[    35.635] 	GreenMaskSize: 0
[    35.635] 	GreenFieldPosition: 0
[    35.635] 	BlueMaskSize: 0
[    35.635] 	BlueFieldPosition: 0
[    35.635] 	RsvdMaskSize: 0
[    35.635] 	RsvdFieldPosition: 0
[    35.635] 	DirectColorModeInfo: 0
[    35.635] 	PhysBasePtr: 0xd0000000
[    35.635] 	LinBytesPerScanLine: 1024
[    35.635] 	BnkNumberOfImagePages: 18
[    35.635] 	LinNumberOfImagePages: 18
[    35.635] 	LinRedMaskSize: 0
[    35.635] 	LinRedFieldPosition: 0
[    35.635] 	LinGreenMaskSize: 0
[    35.635] 	LinGreenFieldPosition: 0
[    35.635] 	LinBlueMaskSize: 0
[    35.635] 	LinBlueFieldPosition: 0
[    35.635] 	LinRsvdMaskSize: 0
[    35.635] 	LinRsvdFieldPosition: 0
[    35.635] 	MaxPixelClock: 400000000
[    35.637] Mode: 107 (1280x1024)
[    35.637] 	ModeAttributes: 0xba
[    35.637] 	WinAAttributes: 0x7
[    35.637] 	WinBAttributes: 0x0
[    35.637] 	WinGranularity: 64
[    35.637] 	WinSize: 64
[    35.637] 	WinASegment: 0xa000
[    35.637] 	WinBSegment: 0x0
[    35.637] 	WinFuncPtr: 0xc00054b3
[    35.637] 	BytesPerScanline: 1280
[    35.637] 	XResolution: 1280
[    35.637] 	YResolution: 1024
[    35.637] 	XCharSize: 8
[    35.637] 	YCharSize: 16
[    35.637] 	NumberOfPlanes: 1
[    35.637] 	BitsPerPixel: 8
[    35.637] 	NumberOfBanks: 1
[    35.637] 	MemoryModel: 4
[    35.637] 	BankSize: 0
[    35.637] 	NumberOfImages: 11
[    35.637] 	RedMaskSize: 0
[    35.637] 	RedFieldPosition: 0
[    35.637] 	GreenMaskSize: 0
[    35.637] 	GreenFieldPosition: 0
[    35.637] 	BlueMaskSize: 0
[    35.637] 	BlueFieldPosition: 0
[    35.637] 	RsvdMaskSize: 0
[    35.637] 	RsvdFieldPosition: 0
[    35.637] 	DirectColorModeInfo: 0
[    35.637] 	PhysBasePtr: 0xd0000000
[    35.637] 	LinBytesPerScanLine: 1280
[    35.637] 	BnkNumberOfImagePages: 11
[    35.637] 	LinNumberOfImagePages: 11
[    35.637] 	LinRedMaskSize: 0
[    35.637] 	LinRedFieldPosition: 0
[    35.637] 	LinGreenMaskSize: 0
[    35.637] 	LinGreenFieldPosition: 0
[    35.637] 	LinBlueMaskSize: 0
[    35.637] 	LinBlueFieldPosition: 0
[    35.637] 	LinRsvdMaskSize: 0
[    35.637] 	LinRsvdFieldPosition: 0
[    35.637] 	MaxPixelClock: 400000000
[    35.638] Mode: 111 (640x480)
[    35.638] 	ModeAttributes: 0xbb
[    35.638] 	WinAAttributes: 0x7
[    35.638] 	WinBAttributes: 0x0
[    35.638] 	WinGranularity: 64
[    35.638] 	WinSize: 64
[    35.638] 	WinASegment: 0xa000
[    35.638] 	WinBSegment: 0x0
[    35.638] 	WinFuncPtr: 0xc00054b3
[    35.638] 	BytesPerScanline: 1280
[    35.638] 	XResolution: 640
[    35.638] 	YResolution: 480
[    35.638] 	XCharSize: 8
[    35.638] 	YCharSize: 16
[    35.638] 	NumberOfPlanes: 1
[    35.638] 	BitsPerPixel: 16
[    35.638] 	NumberOfBanks: 1
[    35.638] 	MemoryModel: 6
[    35.638] 	BankSize: 0
[    35.638] 	NumberOfImages: 24
[    35.638] 	RedMaskSize: 5
[    35.638] 	RedFieldPosition: 11
[    35.638] 	GreenMaskSize: 6
[    35.638] 	GreenFieldPosition: 5
[    35.638] 	BlueMaskSize: 5
[    35.638] 	BlueFieldPosition: 0
[    35.638] 	RsvdMaskSize: 0
[    35.638] 	RsvdFieldPosition: 0
[    35.638] 	DirectColorModeInfo: 0
[    35.638] 	PhysBasePtr: 0xd0000000
[    35.638] 	LinBytesPerScanLine: 1280
[    35.638] 	BnkNumberOfImagePages: 24
[    35.638] 	LinNumberOfImagePages: 24
[    35.638] 	LinRedMaskSize: 5
[    35.638] 	LinRedFieldPosition: 11
[    35.638] 	LinGreenMaskSize: 6
[    35.638] 	LinGreenFieldPosition: 5
[    35.638] 	LinBlueMaskSize: 5
[    35.638] 	LinBlueFieldPosition: 0
[    35.638] 	LinRsvdMaskSize: 0
[    35.638] 	LinRsvdFieldPosition: 0
[    35.638] 	MaxPixelClock: 400000000
[    35.639] Mode: 114 (800x600)
[    35.639] 	ModeAttributes: 0xbb
[    35.639] 	WinAAttributes: 0x7
[    35.639] 	WinBAttributes: 0x0
[    35.639] 	WinGranularity: 64
[    35.639] 	WinSize: 64
[    35.639] 	WinASegment: 0xa000
[    35.639] 	WinBSegment: 0x0
[    35.639] 	WinFuncPtr: 0xc00054b3
[    35.639] 	BytesPerScanline: 1600
[    35.639] 	XResolution: 800
[    35.639] 	YResolution: 600
[    35.639] 	XCharSize: 8
[    35.639] 	YCharSize: 14
[    35.639] 	NumberOfPlanes: 1
[    35.639] 	BitsPerPixel: 16
[    35.639] 	NumberOfBanks: 1
[    35.639] 	MemoryModel: 6
[    35.639] 	BankSize: 0
[    35.639] 	NumberOfImages: 16
[    35.639] 	RedMaskSize: 5
[    35.639] 	RedFieldPosition: 11
[    35.639] 	GreenMaskSize: 6
[    35.639] 	GreenFieldPosition: 5
[    35.639] 	BlueMaskSize: 5
[    35.639] 	BlueFieldPosition: 0
[    35.639] 	RsvdMaskSize: 0
[    35.639] 	RsvdFieldPosition: 0
[    35.639] 	DirectColorModeInfo: 0
[    35.639] 	PhysBasePtr: 0xd0000000
[    35.639] 	LinBytesPerScanLine: 1600
[    35.639] 	BnkNumberOfImagePages: 16
[    35.639] 	LinNumberOfImagePages: 16
[    35.639] 	LinRedMaskSize: 5
[    35.639] 	LinRedFieldPosition: 11
[    35.639] 	LinGreenMaskSize: 6
[    35.639] 	LinGreenFieldPosition: 5
[    35.639] 	LinBlueMaskSize: 5
[    35.639] 	LinBlueFieldPosition: 0
[    35.639] 	LinRsvdMaskSize: 0
[    35.639] 	LinRsvdFieldPosition: 0
[    35.639] 	MaxPixelClock: 400000000
[    35.640] Mode: 117 (1024x768)
[    35.640] 	ModeAttributes: 0xbb
[    35.640] 	WinAAttributes: 0x7
[    35.640] 	WinBAttributes: 0x0
[    35.640] 	WinGranularity: 64
[    35.640] 	WinSize: 64
[    35.640] 	WinASegment: 0xa000
[    35.640] 	WinBSegment: 0x0
[    35.640] 	WinFuncPtr: 0xc00054b3
[    35.640] 	BytesPerScanline: 2048
[    35.640] 	XResolution: 1024
[    35.640] 	YResolution: 768
[    35.640] 	XCharSize: 8
[    35.640] 	YCharSize: 16
[    35.640] 	NumberOfPlanes: 1
[    35.640] 	BitsPerPixel: 16
[    35.640] 	NumberOfBanks: 1
[    35.640] 	MemoryModel: 6
[    35.640] 	BankSize: 0
[    35.640] 	NumberOfImages: 9
[    35.640] 	RedMaskSize: 5
[    35.640] 	RedFieldPosition: 11
[    35.640] 	GreenMaskSize: 6
[    35.640] 	GreenFieldPosition: 5
[    35.640] 	BlueMaskSize: 5
[    35.640] 	BlueFieldPosition: 0
[    35.640] 	RsvdMaskSize: 0
[    35.640] 	RsvdFieldPosition: 0
[    35.640] 	DirectColorModeInfo: 0
[    35.640] 	PhysBasePtr: 0xd0000000
[    35.640] 	LinBytesPerScanLine: 2048
[    35.640] 	BnkNumberOfImagePages: 9
[    35.640] 	LinNumberOfImagePages: 9
[    35.640] 	LinRedMaskSize: 5
[    35.640] 	LinRedFieldPosition: 11
[    35.640] 	LinGreenMaskSize: 6
[    35.640] 	LinGreenFieldPosition: 5
[    35.640] 	LinBlueMaskSize: 5
[    35.640] 	LinBlueFieldPosition: 0
[    35.640] 	LinRsvdMaskSize: 0
[    35.640] 	LinRsvdFieldPosition: 0
[    35.640] 	MaxPixelClock: 400000000
[    35.642] Mode: 11a (1280x1024)
[    35.642] 	ModeAttributes: 0xba
[    35.642] 	WinAAttributes: 0x7
[    35.642] 	WinBAttributes: 0x0
[    35.642] 	WinGranularity: 64
[    35.642] 	WinSize: 64
[    35.642] 	WinASegment: 0xa000
[    35.642] 	WinBSegment: 0x0
[    35.642] 	WinFuncPtr: 0xc00054b3
[    35.642] 	BytesPerScanline: 2560
[    35.642] 	XResolution: 1280
[    35.642] 	YResolution: 1024
[    35.642] 	XCharSize: 8
[    35.642] 	YCharSize: 16
[    35.642] 	NumberOfPlanes: 1
[    35.642] 	BitsPerPixel: 16
[    35.642] 	NumberOfBanks: 1
[    35.642] 	MemoryModel: 6
[    35.642] 	BankSize: 0
[    35.642] 	NumberOfImages: 5
[    35.642] 	RedMaskSize: 5
[    35.642] 	RedFieldPosition: 11
[    35.642] 	GreenMaskSize: 6
[    35.642] 	GreenFieldPosition: 5
[    35.642] 	BlueMaskSize: 5
[    35.642] 	BlueFieldPosition: 0
[    35.642] 	RsvdMaskSize: 0
[    35.642] 	RsvdFieldPosition: 0
[    35.642] 	DirectColorModeInfo: 0
[    35.642] 	PhysBasePtr: 0xd0000000
[    35.642] 	LinBytesPerScanLine: 2560
[    35.642] 	BnkNumberOfImagePages: 5
[    35.642] 	LinNumberOfImagePages: 5
[    35.642] 	LinRedMaskSize: 5
[    35.642] 	LinRedFieldPosition: 11
[    35.642] 	LinGreenMaskSize: 6
[    35.642] 	LinGreenFieldPosition: 5
[    35.642] 	LinBlueMaskSize: 5
[    35.642] 	LinBlueFieldPosition: 0
[    35.642] 	LinRsvdMaskSize: 0
[    35.642] 	LinRsvdFieldPosition: 0
[    35.642] 	MaxPixelClock: 400000000
[    35.643] Mode: 10e (320x200)
[    35.643] 	ModeAttributes: 0xbb
[    35.643] 	WinAAttributes: 0x7
[    35.643] 	WinBAttributes: 0x0
[    35.643] 	WinGranularity: 64
[    35.643] 	WinSize: 64
[    35.643] 	WinASegment: 0xa000
[    35.643] 	WinBSegment: 0x0
[    35.643] 	WinFuncPtr: 0xc00054b3
[    35.643] 	BytesPerScanline: 640
[    35.643] 	XResolution: 320
[    35.643] 	YResolution: 200
[    35.643] 	XCharSize: 8
[    35.643] 	YCharSize: 8
[    35.643] 	NumberOfPlanes: 1
[    35.643] 	BitsPerPixel: 16
[    35.643] 	NumberOfBanks: 1
[    35.643] 	MemoryModel: 6
[    35.643] 	BankSize: 0
[    35.643] 	NumberOfImages: 127
[    35.643] 	RedMaskSize: 5
[    35.643] 	RedFieldPosition: 11
[    35.643] 	GreenMaskSize: 6
[    35.643] 	GreenFieldPosition: 5
[    35.643] 	BlueMaskSize: 5
[    35.643] 	BlueFieldPosition: 0
[    35.643] 	RsvdMaskSize: 0
[    35.643] 	RsvdFieldPosition: 0
[    35.643] 	DirectColorModeInfo: 0
[    35.643] 	PhysBasePtr: 0xd0000000
[    35.643] 	LinBytesPerScanLine: 640
[    35.643] 	BnkNumberOfImagePages: 127
[    35.643] 	LinNumberOfImagePages: 127
[    35.643] 	LinRedMaskSize: 5
[    35.643] 	LinRedFieldPosition: 11
[    35.643] 	LinGreenMaskSize: 6
[    35.643] 	LinGreenFieldPosition: 5
[    35.643] 	LinBlueMaskSize: 5
[    35.643] 	LinBlueFieldPosition: 0
[    35.643] 	LinRsvdMaskSize: 0
[    35.643] 	LinRsvdFieldPosition: 0
[    35.644] 	MaxPixelClock: 400000000
[    35.644] *Mode: 120 (320x200)
[    35.644] 	ModeAttributes: 0xbb
[    35.644] 	WinAAttributes: 0x7
[    35.644] 	WinBAttributes: 0x0
[    35.644] 	WinGranularity: 64
[    35.644] 	WinSize: 64
[    35.644] 	WinASegment: 0xa000
[    35.645] 	WinBSegment: 0x0
[    35.645] 	WinFuncPtr: 0xc00054b3
[    35.645] 	BytesPerScanline: 1280
[    35.645] 	XResolution: 320
[    35.645] 	YResolution: 200
[    35.645] 	XCharSize: 8
[    35.645] 	YCharSize: 8
[    35.645] 	NumberOfPlanes: 1
[    35.645] 	BitsPerPixel: 32
[    35.645] 	NumberOfBanks: 1
[    35.645] 	MemoryModel: 6
[    35.645] 	BankSize: 0
[    35.645] 	NumberOfImages: 63
[    35.645] 	RedMaskSize: 8
[    35.645] 	RedFieldPosition: 16
[    35.645] 	GreenMaskSize: 8
[    35.645] 	GreenFieldPosition: 8
[    35.645] 	BlueMaskSize: 8
[    35.645] 	BlueFieldPosition: 0
[    35.645] 	RsvdMaskSize: 0
[    35.645] 	RsvdFieldPosition: 0
[    35.645] 	DirectColorModeInfo: 0
[    35.645] 	PhysBasePtr: 0xd0000000
[    35.645] 	LinBytesPerScanLine: 1280
[    35.645] 	BnkNumberOfImagePages: 63
[    35.645] 	LinNumberOfImagePages: 63
[    35.645] 	LinRedMaskSize: 8
[    35.645] 	LinRedFieldPosition: 16
[    35.645] 	LinGreenMaskSize: 8
[    35.645] 	LinGreenFieldPosition: 8
[    35.645] 	LinBlueMaskSize: 8
[    35.645] 	LinBlueFieldPosition: 0
[    35.645] 	LinRsvdMaskSize: 0
[    35.645] 	LinRsvdFieldPosition: 0
[    35.645] 	MaxPixelClock: 400000000
[    35.646] Mode: 193 (320x240)
[    35.646] 	ModeAttributes: 0xbb
[    35.646] 	WinAAttributes: 0x7
[    35.646] 	WinBAttributes: 0x0
[    35.646] 	WinGranularity: 64
[    35.646] 	WinSize: 64
[    35.646] 	WinASegment: 0xa000
[    35.646] 	WinBSegment: 0x0
[    35.646] 	WinFuncPtr: 0xc00054b3
[    35.646] 	BytesPerScanline: 320
[    35.646] 	XResolution: 320
[    35.646] 	YResolution: 240
[    35.646] 	XCharSize: 8
[    35.646] 	YCharSize: 8
[    35.646] 	NumberOfPlanes: 1
[    35.646] 	BitsPerPixel: 8
[    35.646] 	NumberOfBanks: 1
[    35.646] 	MemoryModel: 4
[    35.646] 	BankSize: 0
[    35.646] 	NumberOfImages: 127
[    35.646] 	RedMaskSize: 0
[    35.646] 	RedFieldPosition: 0
[    35.646] 	GreenMaskSize: 0
[    35.646] 	GreenFieldPosition: 0
[    35.646] 	BlueMaskSize: 0
[    35.646] 	BlueFieldPosition: 0
[    35.646] 	RsvdMaskSize: 0
[    35.646] 	RsvdFieldPosition: 0
[    35.646] 	DirectColorModeInfo: 0
[    35.646] 	PhysBasePtr: 0xd0000000
[    35.646] 	LinBytesPerScanLine: 320
[    35.646] 	BnkNumberOfImagePages: 127
[    35.646] 	LinNumberOfImagePages: 127
[    35.646] 	LinRedMaskSize: 0
[    35.646] 	LinRedFieldPosition: 0
[    35.646] 	LinGreenMaskSize: 0
[    35.646] 	LinGreenFieldPosition: 0
[    35.646] 	LinBlueMaskSize: 0
[    35.646] 	LinBlueFieldPosition: 0
[    35.646] 	LinRsvdMaskSize: 0
[    35.646] 	LinRsvdFieldPosition: 0
[    35.646] 	MaxPixelClock: 400000000
[    35.647] Mode: 195 (320x240)
[    35.647] 	ModeAttributes: 0xbb
[    35.647] 	WinAAttributes: 0x7
[    35.647] 	WinBAttributes: 0x0
[    35.647] 	WinGranularity: 64
[    35.647] 	WinSize: 64
[    35.647] 	WinASegment: 0xa000
[    35.647] 	WinBSegment: 0x0
[    35.647] 	WinFuncPtr: 0xc00054b3
[    35.647] 	BytesPerScanline: 640
[    35.647] 	XResolution: 320
[    35.647] 	YResolution: 240
[    35.647] 	XCharSize: 8
[    35.647] 	YCharSize: 8
[    35.647] 	NumberOfPlanes: 1
[    35.647] 	BitsPerPixel: 16
[    35.647] 	NumberOfBanks: 1
[    35.647] 	MemoryModel: 6
[    35.647] 	BankSize: 0
[    35.647] 	NumberOfImages: 84
[    35.647] 	RedMaskSize: 5
[    35.647] 	RedFieldPosition: 11
[    35.647] 	GreenMaskSize: 6
[    35.647] 	GreenFieldPosition: 5
[    35.647] 	BlueMaskSize: 5
[    35.647] 	BlueFieldPosition: 0
[    35.647] 	RsvdMaskSize: 0
[    35.647] 	RsvdFieldPosition: 0
[    35.647] 	DirectColorModeInfo: 0
[    35.647] 	PhysBasePtr: 0xd0000000
[    35.647] 	LinBytesPerScanLine: 640
[    35.647] 	BnkNumberOfImagePages: 84
[    35.647] 	LinNumberOfImagePages: 84
[    35.647] 	LinRedMaskSize: 5
[    35.647] 	LinRedFieldPosition: 11
[    35.647] 	LinGreenMaskSize: 6
[    35.647] 	LinGreenFieldPosition: 5
[    35.647] 	LinBlueMaskSize: 5
[    35.647] 	LinBlueFieldPosition: 0
[    35.647] 	LinRsvdMaskSize: 0
[    35.647] 	LinRsvdFieldPosition: 0
[    35.647] 	MaxPixelClock: 400000000
[    35.648] *Mode: 196 (320x240)
[    35.648] 	ModeAttributes: 0xbb
[    35.648] 	WinAAttributes: 0x7
[    35.648] 	WinBAttributes: 0x0
[    35.648] 	WinGranularity: 64
[    35.648] 	WinSize: 64
[    35.648] 	WinASegment: 0xa000
[    35.648] 	WinBSegment: 0x0
[    35.648] 	WinFuncPtr: 0xc00054b3
[    35.648] 	BytesPerScanline: 1280
[    35.648] 	XResolution: 320
[    35.648] 	YResolution: 240
[    35.648] 	XCharSize: 8
[    35.648] 	YCharSize: 8
[    35.648] 	NumberOfPlanes: 1
[    35.648] 	BitsPerPixel: 32
[    35.648] 	NumberOfBanks: 1
[    35.648] 	MemoryModel: 6
[    35.648] 	BankSize: 0
[    35.648] 	NumberOfImages: 50
[    35.648] 	RedMaskSize: 8
[    35.648] 	RedFieldPosition: 16
[    35.648] 	GreenMaskSize: 8
[    35.648] 	GreenFieldPosition: 8
[    35.648] 	BlueMaskSize: 8
[    35.648] 	BlueFieldPosition: 0
[    35.648] 	RsvdMaskSize: 0
[    35.648] 	RsvdFieldPosition: 0
[    35.648] 	DirectColorModeInfo: 0
[    35.648] 	PhysBasePtr: 0xd0000000
[    35.648] 	LinBytesPerScanLine: 1280
[    35.648] 	BnkNumberOfImagePages: 50
[    35.648] 	LinNumberOfImagePages: 50
[    35.648] 	LinRedMaskSize: 8
[    35.648] 	LinRedFieldPosition: 16
[    35.648] 	LinGreenMaskSize: 8
[    35.648] 	LinGreenFieldPosition: 8
[    35.648] 	LinBlueMaskSize: 8
[    35.648] 	LinBlueFieldPosition: 0
[    35.648] 	LinRsvdMaskSize: 0
[    35.648] 	LinRsvdFieldPosition: 0
[    35.648] 	MaxPixelClock: 400000000
[    35.649] Mode: 1b3 (512x384)
[    35.649] 	ModeAttributes: 0xbb
[    35.649] 	WinAAttributes: 0x7
[    35.649] 	WinBAttributes: 0x0
[    35.649] 	WinGranularity: 64
[    35.649] 	WinSize: 64
[    35.649] 	WinASegment: 0xa000
[    35.649] 	WinBSegment: 0x0
[    35.649] 	WinFuncPtr: 0xc00054b3
[    35.649] 	BytesPerScanline: 512
[    35.649] 	XResolution: 512
[    35.649] 	YResolution: 384
[    35.649] 	XCharSize: 8
[    35.649] 	YCharSize: 16
[    35.649] 	NumberOfPlanes: 1
[    35.649] 	BitsPerPixel: 8
[    35.649] 	NumberOfBanks: 1
[    35.649] 	MemoryModel: 4
[    35.649] 	BankSize: 0
[    35.649] 	NumberOfImages: 63
[    35.649] 	RedMaskSize: 0
[    35.649] 	RedFieldPosition: 0
[    35.649] 	GreenMaskSize: 0
[    35.649] 	GreenFieldPosition: 0
[    35.649] 	BlueMaskSize: 0
[    35.649] 	BlueFieldPosition: 0
[    35.649] 	RsvdMaskSize: 0
[    35.649] 	RsvdFieldPosition: 0
[    35.649] 	DirectColorModeInfo: 0
[    35.649] 	PhysBasePtr: 0xd0000000
[    35.649] 	LinBytesPerScanLine: 512
[    35.649] 	BnkNumberOfImagePages: 63
[    35.649] 	LinNumberOfImagePages: 63
[    35.649] 	LinRedMaskSize: 0
[    35.649] 	LinRedFieldPosition: 0
[    35.649] 	LinGreenMaskSize: 0
[    35.649] 	LinGreenFieldPosition: 0
[    35.649] 	LinBlueMaskSize: 0
[    35.649] 	LinBlueFieldPosition: 0
[    35.649] 	LinRsvdMaskSize: 0
[    35.649] 	LinRsvdFieldPosition: 0
[    35.649] 	MaxPixelClock: 400000000
[    35.650] Mode: 1b5 (512x384)
[    35.650] 	ModeAttributes: 0xbb
[    35.650] 	WinAAttributes: 0x7
[    35.650] 	WinBAttributes: 0x0
[    35.650] 	WinGranularity: 64
[    35.650] 	WinSize: 64
[    35.650] 	WinASegment: 0xa000
[    35.650] 	WinBSegment: 0x0
[    35.650] 	WinFuncPtr: 0xc00054b3
[    35.650] 	BytesPerScanline: 1024
[    35.650] 	XResolution: 512
[    35.650] 	YResolution: 384
[    35.650] 	XCharSize: 8
[    35.650] 	YCharSize: 16
[    35.650] 	NumberOfPlanes: 1
[    35.650] 	BitsPerPixel: 16
[    35.650] 	NumberOfBanks: 1
[    35.650] 	MemoryModel: 6
[    35.650] 	BankSize: 0
[    35.650] 	NumberOfImages: 35
[    35.650] 	RedMaskSize: 5
[    35.650] 	RedFieldPosition: 11
[    35.650] 	GreenMaskSize: 6
[    35.650] 	GreenFieldPosition: 5
[    35.650] 	BlueMaskSize: 5
[    35.650] 	BlueFieldPosition: 0
[    35.650] 	RsvdMaskSize: 0
[    35.650] 	RsvdFieldPosition: 0
[    35.650] 	DirectColorModeInfo: 0
[    35.650] 	PhysBasePtr: 0xd0000000
[    35.650] 	LinBytesPerScanLine: 1024
[    35.650] 	BnkNumberOfImagePages: 35
[    35.650] 	LinNumberOfImagePages: 35
[    35.650] 	LinRedMaskSize: 5
[    35.650] 	LinRedFieldPosition: 11
[    35.650] 	LinGreenMaskSize: 6
[    35.650] 	LinGreenFieldPosition: 5
[    35.650] 	LinBlueMaskSize: 5
[    35.650] 	LinBlueFieldPosition: 0
[    35.650] 	LinRsvdMaskSize: 0
[    35.650] 	LinRsvdFieldPosition: 0
[    35.650] 	MaxPixelClock: 400000000
[    35.651] *Mode: 1b6 (512x384)
[    35.651] 	ModeAttributes: 0xbb
[    35.651] 	WinAAttributes: 0x7
[    35.651] 	WinBAttributes: 0x0
[    35.651] 	WinGranularity: 64
[    35.651] 	WinSize: 64
[    35.651] 	WinASegment: 0xa000
[    35.651] 	WinBSegment: 0x0
[    35.651] 	WinFuncPtr: 0xc00054b3
[    35.651] 	BytesPerScanline: 2048
[    35.651] 	XResolution: 512
[    35.651] 	YResolution: 384
[    35.651] 	XCharSize: 8
[    35.651] 	YCharSize: 16
[    35.651] 	NumberOfPlanes: 1
[    35.651] 	BitsPerPixel: 32
[    35.651] 	NumberOfBanks: 1
[    35.651] 	MemoryModel: 6
[    35.651] 	BankSize: 0
[    35.651] 	NumberOfImages: 18
[    35.651] 	RedMaskSize: 8
[    35.651] 	RedFieldPosition: 16
[    35.651] 	GreenMaskSize: 8
[    35.651] 	GreenFieldPosition: 8
[    35.651] 	BlueMaskSize: 8
[    35.651] 	BlueFieldPosition: 0
[    35.651] 	RsvdMaskSize: 0
[    35.651] 	RsvdFieldPosition: 0
[    35.651] 	DirectColorModeInfo: 0
[    35.651] 	PhysBasePtr: 0xd0000000
[    35.651] 	LinBytesPerScanLine: 2048
[    35.651] 	BnkNumberOfImagePages: 18
[    35.651] 	LinNumberOfImagePages: 18
[    35.651] 	LinRedMaskSize: 8
[    35.651] 	LinRedFieldPosition: 16
[    35.651] 	LinGreenMaskSize: 8
[    35.651] 	LinGreenFieldPosition: 8
[    35.651] 	LinBlueMaskSize: 8
[    35.651] 	LinBlueFieldPosition: 0
[    35.651] 	LinRsvdMaskSize: 0
[    35.651] 	LinRsvdFieldPosition: 0
[    35.651] 	MaxPixelClock: 400000000
[    35.652] Mode: 1c3 (640x350)
[    35.652] 	ModeAttributes: 0xbb
[    35.652] 	WinAAttributes: 0x7
[    35.652] 	WinBAttributes: 0x0
[    35.652] 	WinGranularity: 64
[    35.652] 	WinSize: 64
[    35.652] 	WinASegment: 0xa000
[    35.652] 	WinBSegment: 0x0
[    35.652] 	WinFuncPtr: 0xc00054b3
[    35.652] 	BytesPerScanline: 640
[    35.652] 	XResolution: 640
[    35.653] 	YResolution: 350
[    35.653] 	XCharSize: 8
[    35.653] 	YCharSize: 14
[    35.653] 	NumberOfPlanes: 1
[    35.653] 	BitsPerPixel: 8
[    35.653] 	NumberOfBanks: 1
[    35.653] 	MemoryModel: 4
[    35.653] 	BankSize: 0
[    35.653] 	NumberOfImages: 63
[    35.653] 	RedMaskSize: 0
[    35.653] 	RedFieldPosition: 0
[    35.653] 	GreenMaskSize: 0
[    35.653] 	GreenFieldPosition: 0
[    35.653] 	BlueMaskSize: 0
[    35.653] 	BlueFieldPosition: 0
[    35.653] 	RsvdMaskSize: 0
[    35.653] 	RsvdFieldPosition: 0
[    35.653] 	DirectColorModeInfo: 0
[    35.653] 	PhysBasePtr: 0xd0000000
[    35.653] 	LinBytesPerScanLine: 640
[    35.653] 	BnkNumberOfImagePages: 63
[    35.653] 	LinNumberOfImagePages: 63
[    35.653] 	LinRedMaskSize: 0
[    35.653] 	LinRedFieldPosition: 0
[    35.653] 	LinGreenMaskSize: 0
[    35.653] 	LinGreenFieldPosition: 0
[    35.653] 	LinBlueMaskSize: 0
[    35.653] 	LinBlueFieldPosition: 0
[    35.653] 	LinRsvdMaskSize: 0
[    35.653] 	LinRsvdFieldPosition: 0
[    35.653] 	MaxPixelClock: 400000000
[    35.654] Mode: 1c5 (640x350)
[    35.654] 	ModeAttributes: 0xbb
[    35.654] 	WinAAttributes: 0x7
[    35.654] 	WinBAttributes: 0x0
[    35.654] 	WinGranularity: 64
[    35.654] 	WinSize: 64
[    35.654] 	WinASegment: 0xa000
[    35.654] 	WinBSegment: 0x0
[    35.654] 	WinFuncPtr: 0xc00054b3
[    35.654] 	BytesPerScanline: 1280
[    35.654] 	XResolution: 640
[    35.654] 	YResolution: 350
[    35.654] 	XCharSize: 8
[    35.654] 	YCharSize: 14
[    35.654] 	NumberOfPlanes: 1
[    35.654] 	BitsPerPixel: 16
[    35.654] 	NumberOfBanks: 1
[    35.654] 	MemoryModel: 6
[    35.654] 	BankSize: 0
[    35.654] 	NumberOfImages: 35
[    35.654] 	RedMaskSize: 5
[    35.654] 	RedFieldPosition: 11
[    35.654] 	GreenMaskSize: 6
[    35.654] 	GreenFieldPosition: 5
[    35.654] 	BlueMaskSize: 5
[    35.654] 	BlueFieldPosition: 0
[    35.654] 	RsvdMaskSize: 0
[    35.654] 	RsvdFieldPosition: 0
[    35.654] 	DirectColorModeInfo: 0
[    35.654] 	PhysBasePtr: 0xd0000000
[    35.654] 	LinBytesPerScanLine: 1280
[    35.654] 	BnkNumberOfImagePages: 35
[    35.654] 	LinNumberOfImagePages: 35
[    35.654] 	LinRedMaskSize: 5
[    35.654] 	LinRedFieldPosition: 11
[    35.654] 	LinGreenMaskSize: 6
[    35.654] 	LinGreenFieldPosition: 5
[    35.654] 	LinBlueMaskSize: 5
[    35.654] 	LinBlueFieldPosition: 0
[    35.654] 	LinRsvdMaskSize: 0
[    35.654] 	LinRsvdFieldPosition: 0
[    35.654] 	MaxPixelClock: 400000000
[    35.655] *Mode: 1c6 (640x350)
[    35.655] 	ModeAttributes: 0xbb
[    35.655] 	WinAAttributes: 0x7
[    35.655] 	WinBAttributes: 0x0
[    35.655] 	WinGranularity: 64
[    35.655] 	WinSize: 64
[    35.655] 	WinASegment: 0xa000
[    35.655] 	WinBSegment: 0x0
[    35.655] 	WinFuncPtr: 0xc00054b3
[    35.655] 	BytesPerScanline: 2560
[    35.655] 	XResolution: 640
[    35.655] 	YResolution: 350
[    35.655] 	XCharSize: 8
[    35.655] 	YCharSize: 14
[    35.655] 	NumberOfPlanes: 1
[    35.655] 	BitsPerPixel: 32
[    35.655] 	NumberOfBanks: 1
[    35.655] 	MemoryModel: 6
[    35.655] 	BankSize: 0
[    35.655] 	NumberOfImages: 17
[    35.655] 	RedMaskSize: 8
[    35.655] 	RedFieldPosition: 16
[    35.655] 	GreenMaskSize: 8
[    35.655] 	GreenFieldPosition: 8
[    35.655] 	BlueMaskSize: 8
[    35.655] 	BlueFieldPosition: 0
[    35.655] 	RsvdMaskSize: 0
[    35.655] 	RsvdFieldPosition: 0
[    35.655] 	DirectColorModeInfo: 0
[    35.655] 	PhysBasePtr: 0xd0000000
[    35.655] 	LinBytesPerScanLine: 2560
[    35.655] 	BnkNumberOfImagePages: 17
[    35.655] 	LinNumberOfImagePages: 17
[    35.655] 	LinRedMaskSize: 8
[    35.655] 	LinRedFieldPosition: 16
[    35.655] 	LinGreenMaskSize: 8
[    35.655] 	LinGreenFieldPosition: 8
[    35.655] 	LinBlueMaskSize: 8
[    35.655] 	LinBlueFieldPosition: 0
[    35.655] 	LinRsvdMaskSize: 0
[    35.655] 	LinRsvdFieldPosition: 0
[    35.655] 	MaxPixelClock: 400000000
[    35.656] Mode: 133 (720x400)
[    35.656] 	ModeAttributes: 0xbb
[    35.656] 	WinAAttributes: 0x7
[    35.656] 	WinBAttributes: 0x0
[    35.656] 	WinGranularity: 64
[    35.656] 	WinSize: 64
[    35.656] 	WinASegment: 0xa000
[    35.656] 	WinBSegment: 0x0
[    35.656] 	WinFuncPtr: 0xc00054b3
[    35.656] 	BytesPerScanline: 768
[    35.656] 	XResolution: 720
[    35.656] 	YResolution: 400
[    35.656] 	XCharSize: 8
[    35.656] 	YCharSize: 16
[    35.656] 	NumberOfPlanes: 1
[    35.656] 	BitsPerPixel: 8
[    35.656] 	NumberOfBanks: 1
[    35.656] 	MemoryModel: 4
[    35.656] 	BankSize: 0
[    35.656] 	NumberOfImages: 50
[    35.656] 	RedMaskSize: 0
[    35.656] 	RedFieldPosition: 0
[    35.656] 	GreenMaskSize: 0
[    35.656] 	GreenFieldPosition: 0
[    35.656] 	BlueMaskSize: 0
[    35.656] 	BlueFieldPosition: 0
[    35.656] 	RsvdMaskSize: 0
[    35.656] 	RsvdFieldPosition: 0
[    35.656] 	DirectColorModeInfo: 0
[    35.656] 	PhysBasePtr: 0xd0000000
[    35.656] 	LinBytesPerScanLine: 768
[    35.656] 	BnkNumberOfImagePages: 50
[    35.656] 	LinNumberOfImagePages: 50
[    35.656] 	LinRedMaskSize: 0
[    35.656] 	LinRedFieldPosition: 0
[    35.656] 	LinGreenMaskSize: 0
[    35.656] 	LinGreenFieldPosition: 0
[    35.656] 	LinBlueMaskSize: 0
[    35.656] 	LinBlueFieldPosition: 0
[    35.656] 	LinRsvdMaskSize: 0
[    35.656] 	LinRsvdFieldPosition: 0
[    35.656] 	MaxPixelClock: 400000000
[    35.657] Mode: 135 (720x400)
[    35.657] 	ModeAttributes: 0xbb
[    35.657] 	WinAAttributes: 0x7
[    35.657] 	WinBAttributes: 0x0
[    35.657] 	WinGranularity: 64
[    35.657] 	WinSize: 64
[    35.657] 	WinASegment: 0xa000
[    35.657] 	WinBSegment: 0x0
[    35.657] 	WinFuncPtr: 0xc00054b3
[    35.657] 	BytesPerScanline: 1472
[    35.657] 	XResolution: 720
[    35.657] 	YResolution: 400
[    35.657] 	XCharSize: 8
[    35.657] 	YCharSize: 16
[    35.657] 	NumberOfPlanes: 1
[    35.657] 	BitsPerPixel: 16
[    35.657] 	NumberOfBanks: 1
[    35.657] 	MemoryModel: 6
[    35.657] 	BankSize: 0
[    35.657] 	NumberOfImages: 27
[    35.657] 	RedMaskSize: 5
[    35.657] 	RedFieldPosition: 11
[    35.657] 	GreenMaskSize: 6
[    35.657] 	GreenFieldPosition: 5
[    35.657] 	BlueMaskSize: 5
[    35.657] 	BlueFieldPosition: 0
[    35.657] 	RsvdMaskSize: 0
[    35.657] 	RsvdFieldPosition: 0
[    35.657] 	DirectColorModeInfo: 0
[    35.657] 	PhysBasePtr: 0xd0000000
[    35.657] 	LinBytesPerScanLine: 1472
[    35.657] 	BnkNumberOfImagePages: 27
[    35.657] 	LinNumberOfImagePages: 27
[    35.657] 	LinRedMaskSize: 5
[    35.657] 	LinRedFieldPosition: 11
[    35.657] 	LinGreenMaskSize: 6
[    35.657] 	LinGreenFieldPosition: 5
[    35.657] 	LinBlueMaskSize: 5
[    35.657] 	LinBlueFieldPosition: 0
[    35.657] 	LinRsvdMaskSize: 0
[    35.657] 	LinRsvdFieldPosition: 0
[    35.657] 	MaxPixelClock: 400000000
[    35.659] *Mode: 136 (720x400)
[    35.659] 	ModeAttributes: 0xbb
[    35.659] 	WinAAttributes: 0x7
[    35.659] 	WinBAttributes: 0x0
[    35.659] 	WinGranularity: 64
[    35.659] 	WinSize: 64
[    35.659] 	WinASegment: 0xa000
[    35.659] 	WinBSegment: 0x0
[    35.659] 	WinFuncPtr: 0xc00054b3
[    35.659] 	BytesPerScanline: 2944
[    35.659] 	XResolution: 720
[    35.659] 	YResolution: 400
[    35.659] 	XCharSize: 8
[    35.659] 	YCharSize: 16
[    35.659] 	NumberOfPlanes: 1
[    35.659] 	BitsPerPixel: 32
[    35.659] 	NumberOfBanks: 1
[    35.659] 	MemoryModel: 6
[    35.659] 	BankSize: 0
[    35.659] 	NumberOfImages: 13
[    35.659] 	RedMaskSize: 8
[    35.659] 	RedFieldPosition: 16
[    35.659] 	GreenMaskSize: 8
[    35.659] 	GreenFieldPosition: 8
[    35.659] 	BlueMaskSize: 8
[    35.659] 	BlueFieldPosition: 0
[    35.659] 	RsvdMaskSize: 0
[    35.659] 	RsvdFieldPosition: 0
[    35.659] 	DirectColorModeInfo: 0
[    35.659] 	PhysBasePtr: 0xd0000000
[    35.659] 	LinBytesPerScanLine: 2944
[    35.659] 	BnkNumberOfImagePages: 13
[    35.659] 	LinNumberOfImagePages: 13
[    35.659] 	LinRedMaskSize: 8
[    35.659] 	LinRedFieldPosition: 16
[    35.659] 	LinGreenMaskSize: 8
[    35.659] 	LinGreenFieldPosition: 8
[    35.659] 	LinBlueMaskSize: 8
[    35.659] 	LinBlueFieldPosition: 0
[    35.659] 	LinRsvdMaskSize: 0
[    35.659] 	LinRsvdFieldPosition: 0
[    35.659] 	MaxPixelClock: 400000000
[    35.660] Mode: 153 (1152x864)
[    35.660] 	ModeAttributes: 0xbb
[    35.660] 	WinAAttributes: 0x7
[    35.660] 	WinBAttributes: 0x0
[    35.660] 	WinGranularity: 64
[    35.660] 	WinSize: 64
[    35.660] 	WinASegment: 0xa000
[    35.660] 	WinBSegment: 0x0
[    35.660] 	WinFuncPtr: 0xc00054b3
[    35.660] 	BytesPerScanline: 1152
[    35.660] 	XResolution: 1152
[    35.660] 	YResolution: 864
[    35.660] 	XCharSize: 8
[    35.660] 	YCharSize: 16
[    35.660] 	NumberOfPlanes: 1
[    35.660] 	BitsPerPixel: 8
[    35.660] 	NumberOfBanks: 1
[    35.660] 	MemoryModel: 4
[    35.660] 	BankSize: 0
[    35.660] 	NumberOfImages: 15
[    35.660] 	RedMaskSize: 0
[    35.660] 	RedFieldPosition: 0
[    35.660] 	GreenMaskSize: 0
[    35.660] 	GreenFieldPosition: 0
[    35.660] 	BlueMaskSize: 0
[    35.660] 	BlueFieldPosition: 0
[    35.660] 	RsvdMaskSize: 0
[    35.660] 	RsvdFieldPosition: 0
[    35.660] 	DirectColorModeInfo: 0
[    35.660] 	PhysBasePtr: 0xd0000000
[    35.660] 	LinBytesPerScanLine: 1152
[    35.660] 	BnkNumberOfImagePages: 15
[    35.660] 	LinNumberOfImagePages: 15
[    35.660] 	LinRedMaskSize: 0
[    35.660] 	LinRedFieldPosition: 0
[    35.660] 	LinGreenMaskSize: 0
[    35.660] 	LinGreenFieldPosition: 0
[    35.660] 	LinBlueMaskSize: 0
[    35.660] 	LinBlueFieldPosition: 0
[    35.660] 	LinRsvdMaskSize: 0
[    35.660] 	LinRsvdFieldPosition: 0
[    35.660] 	MaxPixelClock: 400000000
[    35.661] Mode: 155 (1152x864)
[    35.661] 	ModeAttributes: 0xbb
[    35.661] 	WinAAttributes: 0x7
[    35.661] 	WinBAttributes: 0x0
[    35.661] 	WinGranularity: 64
[    35.661] 	WinSize: 64
[    35.661] 	WinASegment: 0xa000
[    35.661] 	WinBSegment: 0x0
[    35.661] 	WinFuncPtr: 0xc00054b3
[    35.661] 	BytesPerScanline: 2304
[    35.661] 	XResolution: 1152
[    35.661] 	YResolution: 864
[    35.661] 	XCharSize: 8
[    35.661] 	YCharSize: 16
[    35.661] 	NumberOfPlanes: 1
[    35.661] 	BitsPerPixel: 16
[    35.661] 	NumberOfBanks: 1
[    35.661] 	MemoryModel: 6
[    35.661] 	BankSize: 0
[    35.661] 	NumberOfImages: 7
[    35.661] 	RedMaskSize: 5
[    35.661] 	RedFieldPosition: 11
[    35.661] 	GreenMaskSize: 6
[    35.661] 	GreenFieldPosition: 5
[    35.661] 	BlueMaskSize: 5
[    35.661] 	BlueFieldPosition: 0
[    35.661] 	RsvdMaskSize: 0
[    35.661] 	RsvdFieldPosition: 0
[    35.661] 	DirectColorModeInfo: 0
[    35.661] 	PhysBasePtr: 0xd0000000
[    35.661] 	LinBytesPerScanLine: 2304
[    35.661] 	BnkNumberOfImagePages: 7
[    35.661] 	LinNumberOfImagePages: 7
[    35.661] 	LinRedMaskSize: 5
[    35.661] 	LinRedFieldPosition: 11
[    35.661] 	LinGreenMaskSize: 6
[    35.661] 	LinGreenFieldPosition: 5
[    35.661] 	LinBlueMaskSize: 5
[    35.661] 	LinBlueFieldPosition: 0
[    35.661] 	LinRsvdMaskSize: 0
[    35.661] 	LinRsvdFieldPosition: 0
[    35.661] 	MaxPixelClock: 400000000
[    35.662] *Mode: 156 (1152x864)
[    35.662] 	ModeAttributes: 0xbb
[    35.662] 	WinAAttributes: 0x7
[    35.662] 	WinBAttributes: 0x0
[    35.662] 	WinGranularity: 64
[    35.662] 	WinSize: 64
[    35.662] 	WinASegment: 0xa000
[    35.662] 	WinBSegment: 0x0
[    35.662] 	WinFuncPtr: 0xc00054b3
[    35.662] 	BytesPerScanline: 4608
[    35.662] 	XResolution: 1152
[    35.662] 	YResolution: 864
[    35.662] 	XCharSize: 8
[    35.662] 	YCharSize: 16
[    35.662] 	NumberOfPlanes: 1
[    35.662] 	BitsPerPixel: 32
[    35.662] 	NumberOfBanks: 1
[    35.662] 	MemoryModel: 6
[    35.662] 	BankSize: 0
[    35.662] 	NumberOfImages: 3
[    35.662] 	RedMaskSize: 8
[    35.662] 	RedFieldPosition: 16
[    35.662] 	GreenMaskSize: 8
[    35.662] 	GreenFieldPosition: 8
[    35.662] 	BlueMaskSize: 8
[    35.662] 	BlueFieldPosition: 0
[    35.662] 	RsvdMaskSize: 0
[    35.662] 	RsvdFieldPosition: 0
[    35.662] 	DirectColorModeInfo: 0
[    35.662] 	PhysBasePtr: 0xd0000000
[    35.662] 	LinBytesPerScanLine: 4608
[    35.662] 	BnkNumberOfImagePages: 3
[    35.662] 	LinNumberOfImagePages: 3
[    35.662] 	LinRedMaskSize: 8
[    35.662] 	LinRedFieldPosition: 16
[    35.662] 	LinGreenMaskSize: 8
[    35.662] 	LinGreenFieldPosition: 8
[    35.662] 	LinBlueMaskSize: 8
[    35.662] 	LinBlueFieldPosition: 0
[    35.662] 	LinRsvdMaskSize: 0
[    35.662] 	LinRsvdFieldPosition: 0
[    35.662] 	MaxPixelClock: 400000000
[    35.665] Mode: 163 (1280x1024)
[    35.665] 	ModeAttributes: 0xba
[    35.665] 	WinAAttributes: 0x7
[    35.665] 	WinBAttributes: 0x0
[    35.665] 	WinGranularity: 64
[    35.665] 	WinSize: 64
[    35.665] 	WinASegment: 0xa000
[    35.665] 	WinBSegment: 0x0
[    35.665] 	WinFuncPtr: 0xc00054b3
[    35.665] 	BytesPerScanline: 1280
[    35.665] 	XResolution: 1280
[    35.665] 	YResolution: 1024
[    35.665] 	XCharSize: 8
[    35.665] 	YCharSize: 16
[    35.665] 	NumberOfPlanes: 1
[    35.665] 	BitsPerPixel: 8
[    35.665] 	NumberOfBanks: 1
[    35.665] 	MemoryModel: 4
[    35.665] 	BankSize: 0
[    35.665] 	NumberOfImages: 11
[    35.665] 	RedMaskSize: 0
[    35.665] 	RedFieldPosition: 0
[    35.665] 	GreenMaskSize: 0
[    35.665] 	GreenFieldPosition: 0
[    35.665] 	BlueMaskSize: 0
[    35.665] 	BlueFieldPosition: 0
[    35.665] 	RsvdMaskSize: 0
[    35.665] 	RsvdFieldPosition: 0
[    35.665] 	DirectColorModeInfo: 0
[    35.665] 	PhysBasePtr: 0xd0000000
[    35.665] 	LinBytesPerScanLine: 1280
[    35.665] 	BnkNumberOfImagePages: 11
[    35.665] 	LinNumberOfImagePages: 11
[    35.665] 	LinRedMaskSize: 0
[    35.665] 	LinRedFieldPosition: 0
[    35.665] 	LinGreenMaskSize: 0
[    35.665] 	LinGreenFieldPosition: 0
[    35.665] 	LinBlueMaskSize: 0
[    35.665] 	LinBlueFieldPosition: 0
[    35.665] 	LinRsvdMaskSize: 0
[    35.665] 	LinRsvdFieldPosition: 0
[    35.665] 	MaxPixelClock: 400000000
[    35.667] Mode: 165 (1280x1024)
[    35.667] 	ModeAttributes: 0xba
[    35.667] 	WinAAttributes: 0x7
[    35.667] 	WinBAttributes: 0x0
[    35.667] 	WinGranularity: 64
[    35.667] 	WinSize: 64
[    35.667] 	WinASegment: 0xa000
[    35.667] 	WinBSegment: 0x0
[    35.667] 	WinFuncPtr: 0xc00054b3
[    35.667] 	BytesPerScanline: 2560
[    35.667] 	XResolution: 1280
[    35.667] 	YResolution: 1024
[    35.667] 	XCharSize: 8
[    35.667] 	YCharSize: 16
[    35.667] 	NumberOfPlanes: 1
[    35.667] 	BitsPerPixel: 16
[    35.667] 	NumberOfBanks: 1
[    35.667] 	MemoryModel: 6
[    35.667] 	BankSize: 0
[    35.667] 	NumberOfImages: 5
[    35.667] 	RedMaskSize: 5
[    35.667] 	RedFieldPosition: 11
[    35.667] 	GreenMaskSize: 6
[    35.667] 	GreenFieldPosition: 5
[    35.667] 	BlueMaskSize: 5
[    35.667] 	BlueFieldPosition: 0
[    35.667] 	RsvdMaskSize: 0
[    35.667] 	RsvdFieldPosition: 0
[    35.667] 	DirectColorModeInfo: 0
[    35.667] 	PhysBasePtr: 0xd0000000
[    35.667] 	LinBytesPerScanLine: 2560
[    35.667] 	BnkNumberOfImagePages: 5
[    35.667] 	LinNumberOfImagePages: 5
[    35.667] 	LinRedMaskSize: 5
[    35.667] 	LinRedFieldPosition: 11
[    35.667] 	LinGreenMaskSize: 6
[    35.667] 	LinGreenFieldPosition: 5
[    35.667] 	LinBlueMaskSize: 5
[    35.667] 	LinBlueFieldPosition: 0
[    35.667] 	LinRsvdMaskSize: 0
[    35.667] 	LinRsvdFieldPosition: 0
[    35.667] 	MaxPixelClock: 400000000
[    35.669] Mode: 166 (1280x1024)
[    35.669] 	ModeAttributes: 0xba
[    35.669] 	WinAAttributes: 0x7
[    35.669] 	WinBAttributes: 0x0
[    35.669] 	WinGranularity: 64
[    35.669] 	WinSize: 64
[    35.669] 	WinASegment: 0xa000
[    35.669] 	WinBSegment: 0x0
[    35.669] 	WinFuncPtr: 0xc00054b3
[    35.669] 	BytesPerScanline: 5120
[    35.669] 	XResolution: 1280
[    35.669] 	YResolution: 1024
[    35.669] 	XCharSize: 8
[    35.669] 	YCharSize: 16
[    35.669] 	NumberOfPlanes: 1
[    35.669] 	BitsPerPixel: 32
[    35.669] 	NumberOfBanks: 1
[    35.669] 	MemoryModel: 6
[    35.669] 	BankSize: 0
[    35.669] 	NumberOfImages: 2
[    35.669] 	RedMaskSize: 8
[    35.669] 	RedFieldPosition: 16
[    35.669] 	GreenMaskSize: 8
[    35.669] 	GreenFieldPosition: 8
[    35.669] 	BlueMaskSize: 8
[    35.669] 	BlueFieldPosition: 0
[    35.669] 	RsvdMaskSize: 0
[    35.669] 	RsvdFieldPosition: 0
[    35.669] 	DirectColorModeInfo: 0
[    35.669] 	PhysBasePtr: 0xd0000000
[    35.669] 	LinBytesPerScanLine: 5120
[    35.669] 	BnkNumberOfImagePages: 2
[    35.669] 	LinNumberOfImagePages: 2
[    35.669] 	LinRedMaskSize: 8
[    35.669] 	LinRedFieldPosition: 16
[    35.669] 	LinGreenMaskSize: 8
[    35.669] 	LinGreenFieldPosition: 8
[    35.669] 	LinBlueMaskSize: 8
[    35.669] 	LinBlueFieldPosition: 0
[    35.669] 	LinRsvdMaskSize: 0
[    35.669] 	LinRsvdFieldPosition: 0
[    35.669] 	MaxPixelClock: 400000000
[    35.670] *Mode: 121 (640x480)
[    35.670] 	ModeAttributes: 0xbb
[    35.670] 	WinAAttributes: 0x7
[    35.670] 	WinBAttributes: 0x0
[    35.670] 	WinGranularity: 64
[    35.670] 	WinSize: 64
[    35.670] 	WinASegment: 0xa000
[    35.670] 	WinBSegment: 0x0
[    35.670] 	WinFuncPtr: 0xc00054b3
[    35.670] 	BytesPerScanline: 2560
[    35.670] 	XResolution: 640
[    35.670] 	YResolution: 480
[    35.670] 	XCharSize: 8
[    35.670] 	YCharSize: 16
[    35.670] 	NumberOfPlanes: 1
[    35.670] 	BitsPerPixel: 32
[    35.670] 	NumberOfBanks: 1
[    35.670] 	MemoryModel: 6
[    35.670] 	BankSize: 0
[    35.670] 	NumberOfImages: 12
[    35.670] 	RedMaskSize: 8
[    35.670] 	RedFieldPosition: 16
[    35.670] 	GreenMaskSize: 8
[    35.670] 	GreenFieldPosition: 8
[    35.670] 	BlueMaskSize: 8
[    35.670] 	BlueFieldPosition: 0
[    35.670] 	RsvdMaskSize: 0
[    35.670] 	RsvdFieldPosition: 0
[    35.670] 	DirectColorModeInfo: 0
[    35.670] 	PhysBasePtr: 0xd0000000
[    35.670] 	LinBytesPerScanLine: 2560
[    35.670] 	BnkNumberOfImagePages: 12
[    35.670] 	LinNumberOfImagePages: 12
[    35.670] 	LinRedMaskSize: 8
[    35.670] 	LinRedFieldPosition: 16
[    35.670] 	LinGreenMaskSize: 8
[    35.670] 	LinGreenFieldPosition: 8
[    35.670] 	LinBlueMaskSize: 8
[    35.670] 	LinBlueFieldPosition: 0
[    35.670] 	LinRsvdMaskSize: 0
[    35.670] 	LinRsvdFieldPosition: 0
[    35.670] 	MaxPixelClock: 400000000
[    35.671] *Mode: 122 (800x600)
[    35.671] 	ModeAttributes: 0xbb
[    35.671] 	WinAAttributes: 0x7
[    35.671] 	WinBAttributes: 0x0
[    35.671] 	WinGranularity: 64
[    35.671] 	WinSize: 64
[    35.671] 	WinASegment: 0xa000
[    35.671] 	WinBSegment: 0x0
[    35.671] 	WinFuncPtr: 0xc00054b3
[    35.671] 	BytesPerScanline: 3200
[    35.671] 	XResolution: 800
[    35.671] 	YResolution: 600
[    35.671] 	XCharSize: 8
[    35.671] 	YCharSize: 14
[    35.671] 	NumberOfPlanes: 1
[    35.671] 	BitsPerPixel: 32
[    35.671] 	NumberOfBanks: 1
[    35.671] 	MemoryModel: 6
[    35.671] 	BankSize: 0
[    35.671] 	NumberOfImages: 7
[    35.671] 	RedMaskSize: 8
[    35.671] 	RedFieldPosition: 16
[    35.672] 	GreenMaskSize: 8
[    35.672] 	GreenFieldPosition: 8
[    35.672] 	BlueMaskSize: 8
[    35.672] 	BlueFieldPosition: 0
[    35.672] 	RsvdMaskSize: 0
[    35.672] 	RsvdFieldPosition: 0
[    35.672] 	DirectColorModeInfo: 0
[    35.672] 	PhysBasePtr: 0xd0000000
[    35.672] 	LinBytesPerScanLine: 3200
[    35.672] 	BnkNumberOfImagePages: 7
[    35.672] 	LinNumberOfImagePages: 7
[    35.672] 	LinRedMaskSize: 8
[    35.672] 	LinRedFieldPosition: 16
[    35.672] 	LinGreenMaskSize: 8
[    35.672] 	LinGreenFieldPosition: 8
[    35.672] 	LinBlueMaskSize: 8
[    35.672] 	LinBlueFieldPosition: 0
[    35.672] 	LinRsvdMaskSize: 0
[    35.672] 	LinRsvdFieldPosition: 0
[    35.672] 	MaxPixelClock: 400000000
[    35.673] *Mode: 123 (1024x768)
[    35.673] 	ModeAttributes: 0xbb
[    35.673] 	WinAAttributes: 0x7
[    35.673] 	WinBAttributes: 0x0
[    35.673] 	WinGranularity: 64
[    35.673] 	WinSize: 64
[    35.673] 	WinASegment: 0xa000
[    35.673] 	WinBSegment: 0x0
[    35.673] 	WinFuncPtr: 0xc00054b3
[    35.673] 	BytesPerScanline: 4096
[    35.673] 	XResolution: 1024
[    35.673] 	YResolution: 768
[    35.673] 	XCharSize: 8
[    35.673] 	YCharSize: 16
[    35.673] 	NumberOfPlanes: 1
[    35.673] 	BitsPerPixel: 32
[    35.673] 	NumberOfBanks: 1
[    35.673] 	MemoryModel: 6
[    35.673] 	BankSize: 0
[    35.673] 	NumberOfImages: 4
[    35.673] 	RedMaskSize: 8
[    35.673] 	RedFieldPosition: 16
[    35.673] 	GreenMaskSize: 8
[    35.673] 	GreenFieldPosition: 8
[    35.673] 	BlueMaskSize: 8
[    35.673] 	BlueFieldPosition: 0
[    35.673] 	RsvdMaskSize: 0
[    35.673] 	RsvdFieldPosition: 0
[    35.673] 	DirectColorModeInfo: 0
[    35.673] 	PhysBasePtr: 0xd0000000
[    35.673] 	LinBytesPerScanLine: 4096
[    35.673] 	BnkNumberOfImagePages: 4
[    35.673] 	LinNumberOfImagePages: 4
[    35.673] 	LinRedMaskSize: 8
[    35.673] 	LinRedFieldPosition: 16
[    35.673] 	LinGreenMaskSize: 8
[    35.673] 	LinGreenFieldPosition: 8
[    35.673] 	LinBlueMaskSize: 8
[    35.673] 	LinBlueFieldPosition: 0
[    35.673] 	LinRsvdMaskSize: 0
[    35.673] 	LinRsvdFieldPosition: 0
[    35.673] 	MaxPixelClock: 400000000
[    35.675] Mode: 124 (1280x1024)
[    35.675] 	ModeAttributes: 0xba
[    35.675] 	WinAAttributes: 0x7
[    35.675] 	WinBAttributes: 0x0
[    35.675] 	WinGranularity: 64
[    35.675] 	WinSize: 64
[    35.675] 	WinASegment: 0xa000
[    35.675] 	WinBSegment: 0x0
[    35.675] 	WinFuncPtr: 0xc00054b3
[    35.675] 	BytesPerScanline: 5120
[    35.675] 	XResolution: 1280
[    35.675] 	YResolution: 1024
[    35.675] 	XCharSize: 8
[    35.675] 	YCharSize: 16
[    35.675] 	NumberOfPlanes: 1
[    35.675] 	BitsPerPixel: 32
[    35.675] 	NumberOfBanks: 1
[    35.675] 	MemoryModel: 6
[    35.675] 	BankSize: 0
[    35.675] 	NumberOfImages: 2
[    35.675] 	RedMaskSize: 8
[    35.675] 	RedFieldPosition: 16
[    35.675] 	GreenMaskSize: 8
[    35.675] 	GreenFieldPosition: 8
[    35.675] 	BlueMaskSize: 8
[    35.675] 	BlueFieldPosition: 0
[    35.675] 	RsvdMaskSize: 0
[    35.675] 	RsvdFieldPosition: 0
[    35.675] 	DirectColorModeInfo: 0
[    35.675] 	PhysBasePtr: 0xd0000000
[    35.675] 	LinBytesPerScanLine: 5120
[    35.675] 	BnkNumberOfImagePages: 2
[    35.675] 	LinNumberOfImagePages: 2
[    35.675] 	LinRedMaskSize: 8
[    35.675] 	LinRedFieldPosition: 16
[    35.675] 	LinGreenMaskSize: 8
[    35.675] 	LinGreenFieldPosition: 8
[    35.675] 	LinBlueMaskSize: 8
[    35.675] 	LinBlueFieldPosition: 0
[    35.675] 	LinRsvdMaskSize: 0
[    35.675] 	LinRsvdFieldPosition: 0
[    35.675] 	MaxPixelClock: 400000000
[    35.678] Mode: 143 (1400x1050)
[    35.678] 	ModeAttributes: 0xba
[    35.678] 	WinAAttributes: 0x7
[    35.678] 	WinBAttributes: 0x0
[    35.678] 	WinGranularity: 64
[    35.678] 	WinSize: 64
[    35.678] 	WinASegment: 0xa000
[    35.678] 	WinBSegment: 0x0
[    35.678] 	WinFuncPtr: 0xc00054b3
[    35.678] 	BytesPerScanline: 1408
[    35.678] 	XResolution: 1400
[    35.678] 	YResolution: 1050
[    35.678] 	XCharSize: 8
[    35.678] 	YCharSize: 16
[    35.678] 	NumberOfPlanes: 1
[    35.678] 	BitsPerPixel: 8
[    35.678] 	NumberOfBanks: 1
[    35.678] 	MemoryModel: 4
[    35.678] 	BankSize: 0
[    35.678] 	NumberOfImages: 10
[    35.678] 	RedMaskSize: 0
[    35.678] 	RedFieldPosition: 0
[    35.678] 	GreenMaskSize: 0
[    35.678] 	GreenFieldPosition: 0
[    35.678] 	BlueMaskSize: 0
[    35.678] 	BlueFieldPosition: 0
[    35.678] 	RsvdMaskSize: 0
[    35.678] 	RsvdFieldPosition: 0
[    35.678] 	DirectColorModeInfo: 0
[    35.678] 	PhysBasePtr: 0xd0000000
[    35.678] 	LinBytesPerScanLine: 1408
[    35.678] 	BnkNumberOfImagePages: 10
[    35.678] 	LinNumberOfImagePages: 10
[    35.678] 	LinRedMaskSize: 0
[    35.678] 	LinRedFieldPosition: 0
[    35.678] 	LinGreenMaskSize: 0
[    35.678] 	LinGreenFieldPosition: 0
[    35.678] 	LinBlueMaskSize: 0
[    35.678] 	LinBlueFieldPosition: 0
[    35.678] 	LinRsvdMaskSize: 0
[    35.678] 	LinRsvdFieldPosition: 0
[    35.678] 	MaxPixelClock: 400000000
[    35.680] Mode: 145 (1400x1050)
[    35.680] 	ModeAttributes: 0xba
[    35.680] 	WinAAttributes: 0x7
[    35.680] 	WinBAttributes: 0x0
[    35.680] 	WinGranularity: 64
[    35.680] 	WinSize: 64
[    35.680] 	WinASegment: 0xa000
[    35.680] 	WinBSegment: 0x0
[    35.680] 	WinFuncPtr: 0xc00054b3
[    35.680] 	BytesPerScanline: 2816
[    35.680] 	XResolution: 1400
[    35.680] 	YResolution: 1050
[    35.680] 	XCharSize: 8
[    35.680] 	YCharSize: 16
[    35.680] 	NumberOfPlanes: 1
[    35.680] 	BitsPerPixel: 16
[    35.680] 	NumberOfBanks: 1
[    35.680] 	MemoryModel: 6
[    35.680] 	BankSize: 0
[    35.680] 	NumberOfImages: 4
[    35.680] 	RedMaskSize: 5
[    35.680] 	RedFieldPosition: 11
[    35.680] 	GreenMaskSize: 6
[    35.680] 	GreenFieldPosition: 5
[    35.680] 	BlueMaskSize: 5
[    35.680] 	BlueFieldPosition: 0
[    35.680] 	RsvdMaskSize: 0
[    35.680] 	RsvdFieldPosition: 0
[    35.680] 	DirectColorModeInfo: 0
[    35.680] 	PhysBasePtr: 0xd0000000
[    35.680] 	LinBytesPerScanLine: 2816
[    35.680] 	BnkNumberOfImagePages: 4
[    35.680] 	LinNumberOfImagePages: 4
[    35.680] 	LinRedMaskSize: 5
[    35.680] 	LinRedFieldPosition: 11
[    35.680] 	LinGreenMaskSize: 6
[    35.680] 	LinGreenFieldPosition: 5
[    35.680] 	LinBlueMaskSize: 5
[    35.680] 	LinBlueFieldPosition: 0
[    35.680] 	LinRsvdMaskSize: 0
[    35.680] 	LinRsvdFieldPosition: 0
[    35.680] 	MaxPixelClock: 400000000
[    35.683] Mode: 146 (1400x1050)
[    35.683] 	ModeAttributes: 0xba
[    35.683] 	WinAAttributes: 0x7
[    35.683] 	WinBAttributes: 0x0
[    35.683] 	WinGranularity: 64
[    35.683] 	WinSize: 64
[    35.683] 	WinASegment: 0xa000
[    35.683] 	WinBSegment: 0x0
[    35.683] 	WinFuncPtr: 0xc00054b3
[    35.683] 	BytesPerScanline: 5632
[    35.683] 	XResolution: 1400
[    35.683] 	YResolution: 1050
[    35.683] 	XCharSize: 8
[    35.683] 	YCharSize: 16
[    35.683] 	NumberOfPlanes: 1
[    35.683] 	BitsPerPixel: 32
[    35.683] 	NumberOfBanks: 1
[    35.683] 	MemoryModel: 6
[    35.683] 	BankSize: 0
[    35.683] 	NumberOfImages: 1
[    35.683] 	RedMaskSize: 8
[    35.683] 	RedFieldPosition: 16
[    35.683] 	GreenMaskSize: 8
[    35.683] 	GreenFieldPosition: 8
[    35.683] 	BlueMaskSize: 8
[    35.683] 	BlueFieldPosition: 0
[    35.683] 	RsvdMaskSize: 0
[    35.683] 	RsvdFieldPosition: 0
[    35.683] 	DirectColorModeInfo: 0
[    35.683] 	PhysBasePtr: 0xd0000000
[    35.683] 	LinBytesPerScanLine: 5632
[    35.683] 	BnkNumberOfImagePages: 1
[    35.683] 	LinNumberOfImagePages: 1
[    35.683] 	LinRedMaskSize: 8
[    35.683] 	LinRedFieldPosition: 16
[    35.683] 	LinGreenMaskSize: 8
[    35.683] 	LinGreenFieldPosition: 8
[    35.683] 	LinBlueMaskSize: 8
[    35.683] 	LinBlueFieldPosition: 0
[    35.683] 	LinRsvdMaskSize: 0
[    35.683] 	LinRsvdFieldPosition: 0
[    35.683] 	MaxPixelClock: 400000000
[    35.685] Mode: 173 (1600x1200)
[    35.685] 	ModeAttributes: 0xba
[    35.685] 	WinAAttributes: 0x7
[    35.685] 	WinBAttributes: 0x0
[    35.685] 	WinGranularity: 64
[    35.685] 	WinSize: 64
[    35.685] 	WinASegment: 0xa000
[    35.685] 	WinBSegment: 0x0
[    35.685] 	WinFuncPtr: 0xc00054b3
[    35.685] 	BytesPerScanline: 1600
[    35.685] 	XResolution: 1600
[    35.685] 	YResolution: 1200
[    35.685] 	XCharSize: 8
[    35.685] 	YCharSize: 16
[    35.685] 	NumberOfPlanes: 1
[    35.685] 	BitsPerPixel: 8
[    35.685] 	NumberOfBanks: 1
[    35.685] 	MemoryModel: 4
[    35.685] 	BankSize: 0
[    35.685] 	NumberOfImages: 7
[    35.685] 	RedMaskSize: 0
[    35.685] 	RedFieldPosition: 0
[    35.685] 	GreenMaskSize: 0
[    35.685] 	GreenFieldPosition: 0
[    35.685] 	BlueMaskSize: 0
[    35.685] 	BlueFieldPosition: 0
[    35.685] 	RsvdMaskSize: 0
[    35.685] 	RsvdFieldPosition: 0
[    35.685] 	DirectColorModeInfo: 0
[    35.685] 	PhysBasePtr: 0xd0000000
[    35.685] 	LinBytesPerScanLine: 1600
[    35.685] 	BnkNumberOfImagePages: 7
[    35.685] 	LinNumberOfImagePages: 7
[    35.685] 	LinRedMaskSize: 0
[    35.685] 	LinRedFieldPosition: 0
[    35.685] 	LinGreenMaskSize: 0
[    35.685] 	LinGreenFieldPosition: 0
[    35.685] 	LinBlueMaskSize: 0
[    35.685] 	LinBlueFieldPosition: 0
[    35.685] 	LinRsvdMaskSize: 0
[    35.685] 	LinRsvdFieldPosition: 0
[    35.685] 	MaxPixelClock: 400000000
[    35.687] Mode: 175 (1600x1200)
[    35.687] 	ModeAttributes: 0xba
[    35.687] 	WinAAttributes: 0x7
[    35.687] 	WinBAttributes: 0x0
[    35.687] 	WinGranularity: 64
[    35.687] 	WinSize: 64
[    35.687] 	WinASegment: 0xa000
[    35.687] 	WinBSegment: 0x0
[    35.687] 	WinFuncPtr: 0xc00054b3
[    35.687] 	BytesPerScanline: 3200
[    35.687] 	XResolution: 1600
[    35.687] 	YResolution: 1200
[    35.687] 	XCharSize: 8
[    35.687] 	YCharSize: 16
[    35.687] 	NumberOfPlanes: 1
[    35.687] 	BitsPerPixel: 16
[    35.687] 	NumberOfBanks: 1
[    35.687] 	MemoryModel: 6
[    35.687] 	BankSize: 0
[    35.687] 	NumberOfImages: 3
[    35.687] 	RedMaskSize: 5
[    35.687] 	RedFieldPosition: 11
[    35.687] 	GreenMaskSize: 6
[    35.687] 	GreenFieldPosition: 5
[    35.687] 	BlueMaskSize: 5
[    35.687] 	BlueFieldPosition: 0
[    35.687] 	RsvdMaskSize: 0
[    35.687] 	RsvdFieldPosition: 0
[    35.687] 	DirectColorModeInfo: 0
[    35.687] 	PhysBasePtr: 0xd0000000
[    35.687] 	LinBytesPerScanLine: 3200
[    35.687] 	BnkNumberOfImagePages: 3
[    35.687] 	LinNumberOfImagePages: 3
[    35.687] 	LinRedMaskSize: 5
[    35.687] 	LinRedFieldPosition: 11
[    35.687] 	LinGreenMaskSize: 6
[    35.687] 	LinGreenFieldPosition: 5
[    35.687] 	LinBlueMaskSize: 5
[    35.687] 	LinBlueFieldPosition: 0
[    35.687] 	LinRsvdMaskSize: 0
[    35.687] 	LinRsvdFieldPosition: 0
[    35.687] 	MaxPixelClock: 400000000
[    35.690] Mode: 176 (1600x1200)
[    35.690] 	ModeAttributes: 0xba
[    35.690] 	WinAAttributes: 0x7
[    35.690] 	WinBAttributes: 0x0
[    35.690] 	WinGranularity: 64
[    35.690] 	WinSize: 64
[    35.690] 	WinASegment: 0xa000
[    35.690] 	WinBSegment: 0x0
[    35.690] 	WinFuncPtr: 0xc00054b3
[    35.690] 	BytesPerScanline: 6400
[    35.690] 	XResolution: 1600
[    35.690] 	YResolution: 1200
[    35.690] 	XCharSize: 8
[    35.690] 	YCharSize: 16
[    35.690] 	NumberOfPlanes: 1
[    35.690] 	BitsPerPixel: 32
[    35.690] 	NumberOfBanks: 1
[    35.690] 	MemoryModel: 6
[    35.690] 	BankSize: 0
[    35.690] 	NumberOfImages: 1
[    35.690] 	RedMaskSize: 8
[    35.690] 	RedFieldPosition: 16
[    35.690] 	GreenMaskSize: 8
[    35.690] 	GreenFieldPosition: 8
[    35.690] 	BlueMaskSize: 8
[    35.690] 	BlueFieldPosition: 0
[    35.690] 	RsvdMaskSize: 0
[    35.690] 	RsvdFieldPosition: 0
[    35.690] 	DirectColorModeInfo: 0
[    35.690] 	PhysBasePtr: 0xd0000000
[    35.690] 	LinBytesPerScanLine: 6400
[    35.690] 	BnkNumberOfImagePages: 1
[    35.690] 	LinNumberOfImagePages: 1
[    35.690] 	LinRedMaskSize: 8
[    35.690] 	LinRedFieldPosition: 16
[    35.690] 	LinGreenMaskSize: 8
[    35.690] 	LinGreenFieldPosition: 8
[    35.690] 	LinBlueMaskSize: 8
[    35.690] 	LinBlueFieldPosition: 0
[    35.690] 	LinRsvdMaskSize: 0
[    35.690] 	LinRsvdFieldPosition: 0
[    35.690] 	MaxPixelClock: 400000000
[    35.692] Mode: 183 (1792x1344)
[    35.692] 	ModeAttributes: 0xba
[    35.692] 	WinAAttributes: 0x7
[    35.692] 	WinBAttributes: 0x0
[    35.692] 	WinGranularity: 64
[    35.692] 	WinSize: 64
[    35.692] 	WinASegment: 0xa000
[    35.692] 	WinBSegment: 0x0
[    35.692] 	WinFuncPtr: 0xc00054b3
[    35.692] 	BytesPerScanline: 1792
[    35.692] 	XResolution: 1792
[    35.692] 	YResolution: 1344
[    35.692] 	XCharSize: 8
[    35.692] 	YCharSize: 16
[    35.692] 	NumberOfPlanes: 1
[    35.692] 	BitsPerPixel: 8
[    35.692] 	NumberOfBanks: 1
[    35.692] 	MemoryModel: 4
[    35.692] 	BankSize: 0
[    35.692] 	NumberOfImages: 5
[    35.692] 	RedMaskSize: 0
[    35.692] 	RedFieldPosition: 0
[    35.692] 	GreenMaskSize: 0
[    35.692] 	GreenFieldPosition: 0
[    35.692] 	BlueMaskSize: 0
[    35.692] 	BlueFieldPosition: 0
[    35.692] 	RsvdMaskSize: 0
[    35.692] 	RsvdFieldPosition: 0
[    35.692] 	DirectColorModeInfo: 0
[    35.692] 	PhysBasePtr: 0xd0000000
[    35.692] 	LinBytesPerScanLine: 1792
[    35.692] 	BnkNumberOfImagePages: 5
[    35.692] 	LinNumberOfImagePages: 5
[    35.692] 	LinRedMaskSize: 0
[    35.692] 	LinRedFieldPosition: 0
[    35.692] 	LinGreenMaskSize: 0
[    35.692] 	LinGreenFieldPosition: 0
[    35.692] 	LinBlueMaskSize: 0
[    35.692] 	LinBlueFieldPosition: 0
[    35.692] 	LinRsvdMaskSize: 0
[    35.692] 	LinRsvdFieldPosition: 0
[    35.692] 	MaxPixelClock: 400000000
[    35.694] Mode: 185 (1792x1344)
[    35.694] 	ModeAttributes: 0xba
[    35.694] 	WinAAttributes: 0x7
[    35.694] 	WinBAttributes: 0x0
[    35.694] 	WinGranularity: 64
[    35.694] 	WinSize: 64
[    35.694] 	WinASegment: 0xa000
[    35.694] 	WinBSegment: 0x0
[    35.694] 	WinFuncPtr: 0xc00054b3
[    35.694] 	BytesPerScanline: 3584
[    35.694] 	XResolution: 1792
[    35.694] 	YResolution: 1344
[    35.694] 	XCharSize: 8
[    35.694] 	YCharSize: 16
[    35.694] 	NumberOfPlanes: 1
[    35.694] 	BitsPerPixel: 16
[    35.694] 	NumberOfBanks: 1
[    35.694] 	MemoryModel: 6
[    35.694] 	BankSize: 0
[    35.694] 	NumberOfImages: 2
[    35.694] 	RedMaskSize: 5
[    35.694] 	RedFieldPosition: 11
[    35.694] 	GreenMaskSize: 6
[    35.694] 	GreenFieldPosition: 5
[    35.694] 	BlueMaskSize: 5
[    35.694] 	BlueFieldPosition: 0
[    35.694] 	RsvdMaskSize: 0
[    35.694] 	RsvdFieldPosition: 0
[    35.694] 	DirectColorModeInfo: 0
[    35.694] 	PhysBasePtr: 0xd0000000
[    35.694] 	LinBytesPerScanLine: 3584
[    35.694] 	BnkNumberOfImagePages: 2
[    35.694] 	LinNumberOfImagePages: 2
[    35.694] 	LinRedMaskSize: 5
[    35.694] 	LinRedFieldPosition: 11
[    35.694] 	LinGreenMaskSize: 6
[    35.694] 	LinGreenFieldPosition: 5
[    35.694] 	LinBlueMaskSize: 5
[    35.694] 	LinBlueFieldPosition: 0
[    35.694] 	LinRsvdMaskSize: 0
[    35.694] 	LinRsvdFieldPosition: 0
[    35.694] 	MaxPixelClock: 400000000
[    35.696] Mode: 186 (1792x1344)
[    35.696] 	ModeAttributes: 0xba
[    35.696] 	WinAAttributes: 0x7
[    35.696] 	WinBAttributes: 0x0
[    35.696] 	WinGranularity: 64
[    35.696] 	WinSize: 64
[    35.696] 	WinASegment: 0xa000
[    35.696] 	WinBSegment: 0x0
[    35.696] 	WinFuncPtr: 0xc00054b3
[    35.696] 	BytesPerScanline: 7168
[    35.696] 	XResolution: 1792
[    35.696] 	YResolution: 1344
[    35.696] 	XCharSize: 8
[    35.696] 	YCharSize: 16
[    35.696] 	NumberOfPlanes: 1
[    35.696] 	BitsPerPixel: 32
[    35.696] 	NumberOfBanks: 1
[    35.696] 	MemoryModel: 6
[    35.697] 	BankSize: 0
[    35.697] 	NumberOfImages: 1
[    35.697] 	RedMaskSize: 8
[    35.697] 	RedFieldPosition: 16
[    35.697] 	GreenMaskSize: 8
[    35.697] 	GreenFieldPosition: 8
[    35.697] 	BlueMaskSize: 8
[    35.697] 	BlueFieldPosition: 0
[    35.697] 	RsvdMaskSize: 0
[    35.697] 	RsvdFieldPosition: 0
[    35.697] 	DirectColorModeInfo: 0
[    35.697] 	PhysBasePtr: 0xd0000000
[    35.697] 	LinBytesPerScanLine: 7168
[    35.697] 	BnkNumberOfImagePages: 1
[    35.697] 	LinNumberOfImagePages: 1
[    35.697] 	LinRedMaskSize: 8
[    35.697] 	LinRedFieldPosition: 16
[    35.697] 	LinGreenMaskSize: 8
[    35.697] 	LinGreenFieldPosition: 8
[    35.697] 	LinBlueMaskSize: 8
[    35.697] 	LinBlueFieldPosition: 0
[    35.697] 	LinRsvdMaskSize: 0
[    35.697] 	LinRsvdFieldPosition: 0
[    35.697] 	MaxPixelClock: 400000000
[    35.699] Mode: 1d3 (1856x1392)
[    35.699] 	ModeAttributes: 0xba
[    35.699] 	WinAAttributes: 0x7
[    35.699] 	WinBAttributes: 0x0
[    35.699] 	WinGranularity: 64
[    35.699] 	WinSize: 64
[    35.699] 	WinASegment: 0xa000
[    35.699] 	WinBSegment: 0x0
[    35.699] 	WinFuncPtr: 0xc00054b3
[    35.699] 	BytesPerScanline: 1856
[    35.699] 	XResolution: 1856
[    35.699] 	YResolution: 1392
[    35.699] 	XCharSize: 8
[    35.699] 	YCharSize: 16
[    35.699] 	NumberOfPlanes: 1
[    35.699] 	BitsPerPixel: 8
[    35.699] 	NumberOfBanks: 1
[    35.699] 	MemoryModel: 4
[    35.699] 	BankSize: 0
[    35.699] 	NumberOfImages: 5
[    35.699] 	RedMaskSize: 0
[    35.699] 	RedFieldPosition: 0
[    35.699] 	GreenMaskSize: 0
[    35.699] 	GreenFieldPosition: 0
[    35.699] 	BlueMaskSize: 0
[    35.699] 	BlueFieldPosition: 0
[    35.699] 	RsvdMaskSize: 0
[    35.699] 	RsvdFieldPosition: 0
[    35.699] 	DirectColorModeInfo: 0
[    35.699] 	PhysBasePtr: 0xd0000000
[    35.699] 	LinBytesPerScanLine: 1856
[    35.699] 	BnkNumberOfImagePages: 5
[    35.699] 	LinNumberOfImagePages: 5
[    35.699] 	LinRedMaskSize: 0
[    35.699] 	LinRedFieldPosition: 0
[    35.699] 	LinGreenMaskSize: 0
[    35.699] 	LinGreenFieldPosition: 0
[    35.699] 	LinBlueMaskSize: 0
[    35.699] 	LinBlueFieldPosition: 0
[    35.699] 	LinRsvdMaskSize: 0
[    35.699] 	LinRsvdFieldPosition: 0
[    35.699] 	MaxPixelClock: 400000000
[    35.701] Mode: 1d5 (1856x1392)
[    35.701] 	ModeAttributes: 0xba
[    35.701] 	WinAAttributes: 0x7
[    35.701] 	WinBAttributes: 0x0
[    35.701] 	WinGranularity: 64
[    35.701] 	WinSize: 64
[    35.701] 	WinASegment: 0xa000
[    35.701] 	WinBSegment: 0x0
[    35.701] 	WinFuncPtr: 0xc00054b3
[    35.701] 	BytesPerScanline: 3712
[    35.701] 	XResolution: 1856
[    35.701] 	YResolution: 1392
[    35.701] 	XCharSize: 8
[    35.701] 	YCharSize: 16
[    35.701] 	NumberOfPlanes: 1
[    35.701] 	BitsPerPixel: 16
[    35.701] 	NumberOfBanks: 1
[    35.701] 	MemoryModel: 6
[    35.701] 	BankSize: 0
[    35.701] 	NumberOfImages: 2
[    35.701] 	RedMaskSize: 5
[    35.701] 	RedFieldPosition: 11
[    35.701] 	GreenMaskSize: 6
[    35.701] 	GreenFieldPosition: 5
[    35.701] 	BlueMaskSize: 5
[    35.701] 	BlueFieldPosition: 0
[    35.701] 	RsvdMaskSize: 0
[    35.701] 	RsvdFieldPosition: 0
[    35.701] 	DirectColorModeInfo: 0
[    35.701] 	PhysBasePtr: 0xd0000000
[    35.701] 	LinBytesPerScanLine: 3712
[    35.701] 	BnkNumberOfImagePages: 2
[    35.701] 	LinNumberOfImagePages: 2
[    35.701] 	LinRedMaskSize: 5
[    35.701] 	LinRedFieldPosition: 11
[    35.701] 	LinGreenMaskSize: 6
[    35.701] 	LinGreenFieldPosition: 5
[    35.701] 	LinBlueMaskSize: 5
[    35.701] 	LinBlueFieldPosition: 0
[    35.701] 	LinRsvdMaskSize: 0
[    35.701] 	LinRsvdFieldPosition: 0
[    35.701] 	MaxPixelClock: 400000000
[    35.703] Mode: 1d6 (1856x1392)
[    35.703] 	ModeAttributes: 0xba
[    35.703] 	WinAAttributes: 0x7
[    35.703] 	WinBAttributes: 0x0
[    35.703] 	WinGranularity: 64
[    35.703] 	WinSize: 64
[    35.703] 	WinASegment: 0xa000
[    35.703] 	WinBSegment: 0x0
[    35.703] 	WinFuncPtr: 0xc00054b3
[    35.703] 	BytesPerScanline: 7424
[    35.703] 	XResolution: 1856
[    35.703] 	YResolution: 1392
[    35.703] 	XCharSize: 8
[    35.703] 	YCharSize: 16
[    35.703] 	NumberOfPlanes: 1
[    35.703] 	BitsPerPixel: 32
[    35.703] 	NumberOfBanks: 1
[    35.703] 	MemoryModel: 6
[    35.703] 	BankSize: 0
[    35.703] 	NumberOfImages: 1
[    35.703] 	RedMaskSize: 8
[    35.703] 	RedFieldPosition: 16
[    35.703] 	GreenMaskSize: 8
[    35.703] 	GreenFieldPosition: 8
[    35.703] 	BlueMaskSize: 8
[    35.704] 	BlueFieldPosition: 0
[    35.704] 	RsvdMaskSize: 0
[    35.704] 	RsvdFieldPosition: 0
[    35.704] 	DirectColorModeInfo: 0
[    35.704] 	PhysBasePtr: 0xd0000000
[    35.704] 	LinBytesPerScanLine: 7424
[    35.704] 	BnkNumberOfImagePages: 1
[    35.704] 	LinNumberOfImagePages: 1
[    35.704] 	LinRedMaskSize: 8
[    35.704] 	LinRedFieldPosition: 16
[    35.704] 	LinGreenMaskSize: 8
[    35.704] 	LinGreenFieldPosition: 8
[    35.704] 	LinBlueMaskSize: 8
[    35.704] 	LinBlueFieldPosition: 0
[    35.704] 	LinRsvdMaskSize: 0
[    35.704] 	LinRsvdFieldPosition: 0
[    35.704] 	MaxPixelClock: 400000000
[    35.706] Mode: 1e3 (1920x1440)
[    35.706] 	ModeAttributes: 0xba
[    35.706] 	WinAAttributes: 0x7
[    35.706] 	WinBAttributes: 0x0
[    35.706] 	WinGranularity: 64
[    35.706] 	WinSize: 64
[    35.706] 	WinASegment: 0xa000
[    35.706] 	WinBSegment: 0x0
[    35.706] 	WinFuncPtr: 0xc00054b3
[    35.706] 	BytesPerScanline: 1920
[    35.706] 	XResolution: 1920
[    35.706] 	YResolution: 1440
[    35.706] 	XCharSize: 8
[    35.706] 	YCharSize: 16
[    35.706] 	NumberOfPlanes: 1
[    35.706] 	BitsPerPixel: 8
[    35.706] 	NumberOfBanks: 1
[    35.706] 	MemoryModel: 4
[    35.706] 	BankSize: 0
[    35.706] 	NumberOfImages: 4
[    35.706] 	RedMaskSize: 0
[    35.706] 	RedFieldPosition: 0
[    35.706] 	GreenMaskSize: 0
[    35.706] 	GreenFieldPosition: 0
[    35.706] 	BlueMaskSize: 0
[    35.706] 	BlueFieldPosition: 0
[    35.706] 	RsvdMaskSize: 0
[    35.706] 	RsvdFieldPosition: 0
[    35.706] 	DirectColorModeInfo: 0
[    35.706] 	PhysBasePtr: 0xd0000000
[    35.706] 	LinBytesPerScanLine: 1920
[    35.706] 	BnkNumberOfImagePages: 4
[    35.706] 	LinNumberOfImagePages: 4
[    35.706] 	LinRedMaskSize: 0
[    35.706] 	LinRedFieldPosition: 0
[    35.706] 	LinGreenMaskSize: 0
[    35.706] 	LinGreenFieldPosition: 0
[    35.706] 	LinBlueMaskSize: 0
[    35.706] 	LinBlueFieldPosition: 0
[    35.706] 	LinRsvdMaskSize: 0
[    35.706] 	LinRsvdFieldPosition: 0
[    35.706] 	MaxPixelClock: 400000000
[    35.708] Mode: 1e5 (1920x1440)
[    35.708] 	ModeAttributes: 0xba
[    35.708] 	WinAAttributes: 0x7
[    35.708] 	WinBAttributes: 0x0
[    35.708] 	WinGranularity: 64
[    35.708] 	WinSize: 64
[    35.708] 	WinASegment: 0xa000
[    35.708] 	WinBSegment: 0x0
[    35.708] 	WinFuncPtr: 0xc00054b3
[    35.708] 	BytesPerScanline: 3840
[    35.708] 	XResolution: 1920
[    35.708] 	YResolution: 1440
[    35.708] 	XCharSize: 8
[    35.708] 	YCharSize: 16
[    35.708] 	NumberOfPlanes: 1
[    35.708] 	BitsPerPixel: 16
[    35.708] 	NumberOfBanks: 1
[    35.708] 	MemoryModel: 6
[    35.708] 	BankSize: 0
[    35.708] 	NumberOfImages: 2
[    35.708] 	RedMaskSize: 5
[    35.708] 	RedFieldPosition: 11
[    35.708] 	GreenMaskSize: 6
[    35.708] 	GreenFieldPosition: 5
[    35.708] 	BlueMaskSize: 5
[    35.708] 	BlueFieldPosition: 0
[    35.708] 	RsvdMaskSize: 0
[    35.708] 	RsvdFieldPosition: 0
[    35.708] 	DirectColorModeInfo: 0
[    35.708] 	PhysBasePtr: 0xd0000000
[    35.708] 	LinBytesPerScanLine: 3840
[    35.708] 	BnkNumberOfImagePages: 2
[    35.708] 	LinNumberOfImagePages: 2
[    35.708] 	LinRedMaskSize: 5
[    35.708] 	LinRedFieldPosition: 11
[    35.708] 	LinGreenMaskSize: 6
[    35.708] 	LinGreenFieldPosition: 5
[    35.708] 	LinBlueMaskSize: 5
[    35.708] 	LinBlueFieldPosition: 0
[    35.708] 	LinRsvdMaskSize: 0
[    35.708] 	LinRsvdFieldPosition: 0
[    35.708] 	MaxPixelClock: 400000000
[    35.711] Mode: 1e6 (1920x1440)
[    35.711] 	ModeAttributes: 0xba
[    35.711] 	WinAAttributes: 0x7
[    35.711] 	WinBAttributes: 0x0
[    35.711] 	WinGranularity: 64
[    35.711] 	WinSize: 64
[    35.711] 	WinASegment: 0xa000
[    35.711] 	WinBSegment: 0x0
[    35.711] 	WinFuncPtr: 0xc00054b3
[    35.711] 	BytesPerScanline: 7680
[    35.711] 	XResolution: 1920
[    35.711] 	YResolution: 1440
[    35.711] 	XCharSize: 8
[    35.711] 	YCharSize: 16
[    35.711] 	NumberOfPlanes: 1
[    35.711] 	BitsPerPixel: 32
[    35.711] 	NumberOfBanks: 1
[    35.711] 	MemoryModel: 6
[    35.711] 	BankSize: 0
[    35.711] 	NumberOfImages: 1
[    35.711] 	RedMaskSize: 8
[    35.711] 	RedFieldPosition: 16
[    35.711] 	GreenMaskSize: 8
[    35.711] 	GreenFieldPosition: 8
[    35.711] 	BlueMaskSize: 8
[    35.711] 	BlueFieldPosition: 0
[    35.711] 	RsvdMaskSize: 0
[    35.711] 	RsvdFieldPosition: 0
[    35.711] 	DirectColorModeInfo: 0
[    35.711] 	PhysBasePtr: 0xd0000000
[    35.711] 	LinBytesPerScanLine: 7680
[    35.711] 	BnkNumberOfImagePages: 1
[    35.711] 	LinNumberOfImagePages: 1
[    35.711] 	LinRedMaskSize: 8
[    35.711] 	LinRedFieldPosition: 16
[    35.711] 	LinGreenMaskSize: 8
[    35.711] 	LinGreenFieldPosition: 8
[    35.711] 	LinBlueMaskSize: 8
[    35.711] 	LinBlueFieldPosition: 0
[    35.711] 	LinRsvdMaskSize: 0
[    35.711] 	LinRsvdFieldPosition: 0
[    35.711] 	MaxPixelClock: 400000000
[    35.711] 
[    35.711] (II) VESA(0): Total Memory: 256 64KB banks (16384kB)
[    35.711] (II) VESA(0): <default monitor>: Using hsync range of 30.00-80.00 kHz
[    35.711] (II) VESA(0): <default monitor>: Using vrefresh range of 50.00-76.00 Hz
[    35.711] (II) VESA(0): <default monitor>: Using maximum pixel clock of 165.00 MHz
[    35.711] (WW) VESA(0): Unable to estimate virtual size
[    35.711] (II) VESA(0): Not using built-in mode "640x350" (no mode of this name)
[    35.711] (II) VESA(0): Not using built-in mode "512x384" (no mode of this name)
[    35.711] (II) VESA(0): Not using built-in mode "320x240" (no mode of this name)
[    35.711] (II) VESA(0): Not using built-in mode "320x200" (no mode of this name)
[    35.711] (--) VESA(0): Virtual size is 1152x864 (pitch 1152)
[    35.711] (**) VESA(0): *Built-in mode "1152x864"
[    35.711] (**) VESA(0): *Built-in mode "1024x768"
[    35.711] (**) VESA(0): *Built-in mode "800x600"
[    35.711] (**) VESA(0): *Built-in mode "640x480"
[    35.711] (**) VESA(0): *Built-in mode "720x400"
[    35.711] (**) VESA(0): Display dimensions: (440, 250) mm
[    35.711] (**) VESA(0): DPI set to (66, 87)
[    35.711] (**) VESA(0): Using "Shadow Framebuffer"
[    35.711] (II) Loading sub module "shadow"
[    35.711] (II) LoadModule: "shadow"
[    35.712] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    35.724] (II) Module shadow: vendor="X.Org Foundation"
[    35.724] 	compiled for 1.13.0, module version = 1.1.0
[    35.724] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    35.724] (II) Loading sub module "fb"
[    35.724] (II) LoadModule: "fb"
[    35.724] (II) Loading /usr/lib/xorg/modules/libfb.so
[    35.724] (II) Module fb: vendor="X.Org Foundation"
[    35.724] 	compiled for 1.13.0, module version = 1.0.0
[    35.724] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    35.724] (II) UnloadModule: "fglrx"
[    35.724] (II) Unloading fglrx
[    35.724] (II) UnloadSubModule: "fglrxdrm"
[    35.724] (II) Unloading fglrxdrm
[    35.724] (II) UnloadModule: "modesetting"
[    35.724] (II) Unloading modesetting
[    35.724] (II) UnloadModule: "fbdev"
[    35.724] (II) Unloading fbdev
[    35.724] (II) UnloadSubModule: "fbdevhw"
[    35.724] (II) Unloading fbdevhw
[    35.724] (==) Depth 24 pixmap format is 32 bpp
[    35.724] (II) Loading sub module "int10"
[    35.724] (II) LoadModule: "int10"
[    35.725] (II) Loading /usr/lib/xorg/modules/libint10.so
[    35.725] (II) Module int10: vendor="X.Org Foundation"
[    35.725] 	compiled for 1.13.0, module version = 1.0.0
[    35.725] 	ABI class: X.Org Video Driver, version 13.0
[    35.725] (II) VESA(0): initializing int10
[    35.729] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    35.729] (II) VESA(0): VESA BIOS detected
[    35.729] (II) VESA(0): VESA VBE Version 3.0
[    35.729] (II) VESA(0): VESA VBE Total Mem: 16384 kB
[    35.729] (II) VESA(0): VESA VBE OEM: ATI ATOMBIOS
[    35.729] (II) VESA(0): VESA VBE OEM Software Rev: 10.94
[    35.729] (II) VESA(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
[    35.729] (II) VESA(0): VESA VBE OEM Product: RS880
[    35.729] (II) VESA(0): VESA VBE OEM Product Rev: 01.00
[    35.730] (II) VESA(0): virtual address = 0x7f1d085c3000,
	physical address = 0xd0000000, size = 16777216
[    35.738] (II) VESA(0): Setting up VESA Mode 0x156 (1152x864)
[    35.738] (II) VESA(0): VBESetVBEMode failed, mode set without customized refresh.
[    36.066] (==) VESA(0): Default visual is TrueColor
[    36.067] (==) VESA(0): Backing store disabled
[    36.067] (==) VESA(0): DPMS enabled
[    36.067] (==) RandR enabled
[    36.071] (EE) GLX error: Can not get required symbols.
[    36.080] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    36.083] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    36.083] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    36.083] (II) LoadModule: "evdev"
[    36.083] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    36.083] (II) Module evdev: vendor="X.Org Foundation"
[    36.083] 	compiled for 1.13.0, module version = 2.7.3
[    36.083] 	Module class: X.Org XInput Driver
[    36.083] 	ABI class: X.Org XInput driver, version 18.0
[    36.083] (II) Using input driver 'evdev' for 'Power Button'
[    36.083] (**) Power Button: always reports core events
[    36.083] (**) evdev: Power Button: Device: "/dev/input/event1"
[    36.083] (--) evdev: Power Button: Vendor 0 Product 0x1
[    36.083] (--) evdev: Power Button: Found keys
[    36.083] (II) evdev: Power Button: Configuring as keyboard
[    36.083] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    36.083] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    36.083] (**) Option "xkb_rules" "evdev"
[    36.083] (**) Option "xkb_model" "pc105"
[    36.083] (**) Option "xkb_layout" "us"
[    36.084] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    36.084] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    36.084] (II) Using input driver 'evdev' for 'Power Button'
[    36.084] (**) Power Button: always reports core events
[    36.084] (**) evdev: Power Button: Device: "/dev/input/event0"
[    36.084] (--) evdev: Power Button: Vendor 0 Product 0x1
[    36.084] (--) evdev: Power Button: Found keys
[    36.084] (II) evdev: Power Button: Configuring as keyboard
[    36.084] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    36.084] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    36.084] (**) Option "xkb_rules" "evdev"
[    36.084] (**) Option "xkb_model" "pc105"
[    36.084] (**) Option "xkb_layout" "us"
[    36.084] (II) config/udev: Adding input device   USB Keyboard (/dev/input/event2)
[    36.084] (**)   USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    36.084] (II) Using input driver 'evdev' for '  USB Keyboard'
[    36.084] (**)   USB Keyboard: always reports core events
[    36.084] (**) evdev:   USB Keyboard: Device: "/dev/input/event2"
[    36.084] (--) evdev:   USB Keyboard: Vendor 0x4d9 Product 0x1605
[    36.084] (--) evdev:   USB Keyboard: Found keys
[    36.084] (II) evdev:   USB Keyboard: Configuring as keyboard
[    36.084] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb3/3-1/3-1:1.0/input/input2/event2"
[    36.084] (II) XINPUT: Adding extended input device "  USB Keyboard" (type: KEYBOARD, id 8)
[    36.084] (**) Option "xkb_rules" "evdev"
[    36.084] (**) Option "xkb_model" "pc105"
[    36.085] (**) Option "xkb_layout" "us"
[    36.085] (II) config/udev: Adding input device   USB Keyboard (/dev/input/event3)
[    36.085] (**)   USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    36.085] (II) Using input driver 'evdev' for '  USB Keyboard'
[    36.085] (**)   USB Keyboard: always reports core events
[    36.085] (**) evdev:   USB Keyboard: Device: "/dev/input/event3"
[    36.085] (--) evdev:   USB Keyboard: Vendor 0x4d9 Product 0x1605
[    36.085] (--) evdev:   USB Keyboard: Found keys
[    36.085] (II) evdev:   USB Keyboard: Configuring as keyboard
[    36.085] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb3/3-1/3-1:1.1/input/input3/event3"
[    36.085] (II) XINPUT: Adding extended input device "  USB Keyboard" (type: KEYBOARD, id 9)
[    36.085] (**) Option "xkb_rules" "evdev"
[    36.085] (**) Option "xkb_model" "pc105"
[    36.085] (**) Option "xkb_layout" "us"
[    36.085] (II) config/udev: Adding input device Kensington Kensington PocketMouse Pro Laser Wls (/dev/input/event4)
[    36.086] (**) Kensington Kensington PocketMouse Pro Laser Wls: Applying InputClass "evdev pointer catchall"
[    36.086] (II) Using input driver 'evdev' for 'Kensington Kensington PocketMouse Pro Laser Wls'
[    36.086] (**) Kensington Kensington PocketMouse Pro Laser Wls: always reports core events
[    36.086] (**) evdev: Kensington Kensington PocketMouse Pro Laser Wls: Device: "/dev/input/event4"
[    36.086] (--) evdev: Kensington Kensington PocketMouse Pro Laser Wls: Vendor 0x47d Product 0x103f
[    36.086] (--) evdev: Kensington Kensington PocketMouse Pro Laser Wls: Found 3 mouse buttons
[    36.086] (--) evdev: Kensington Kensington PocketMouse Pro Laser Wls: Found scroll wheel(s)
[    36.086] (--) evdev: Kensington Kensington PocketMouse Pro Laser Wls: Found relative axes
[    36.086] (--) evdev: Kensington Kensington PocketMouse Pro Laser Wls: Found x and y relative axes
[    36.086] (II) evdev: Kensington Kensington PocketMouse Pro Laser Wls: Configuring as mouse
[    36.086] (II) evdev: Kensington Kensington PocketMouse Pro Laser Wls: Adding scrollwheel support
[    36.086] (**) evdev: Kensington Kensington PocketMouse Pro Laser Wls: YAxisMapping: buttons 4 and 5
[    36.086] (**) evdev: Kensington Kensington PocketMouse Pro Laser Wls: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    36.086] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb3/3-2/3-2:1.0/input/input4/event4"
[    36.086] (II) XINPUT: Adding extended input device "Kensington Kensington PocketMouse Pro Laser Wls" (type: MOUSE, id 10)
[    36.086] (II) evdev: Kensington Kensington PocketMouse Pro Laser Wls: initialized for relative axes.
[    36.086] (**) Kensington Kensington PocketMouse Pro Laser Wls: (accel) keeping acceleration scheme 1
[    36.086] (**) Kensington Kensington PocketMouse Pro Laser Wls: (accel) acceleration profile 0
[    36.086] (**) Kensington Kensington PocketMouse Pro Laser Wls: (accel) acceleration factor: 2.000
[    36.086] (**) Kensington Kensington PocketMouse Pro Laser Wls: (accel) acceleration threshold: 4
[    36.086] (II) config/udev: Adding input device Kensington Kensington PocketMouse Pro Laser Wls (/dev/input/mouse0)
[    36.086] (II) No input driver specified, ignoring this device.
[    36.086] (II) This device may have been added with another device file.
[    36.086] (II) config/udev: Adding input device HDA ATI SB Line Out CLFE (/dev/input/event10)
[    36.086] (II) No input driver specified, ignoring this device.
[    36.086] (II) This device may have been added with another device file.
[    36.086] (II) config/udev: Adding input device HDA ATI SB Line Out Surround (/dev/input/event11)
[    36.087] (II) No input driver specified, ignoring this device.
[    36.087] (II) This device may have been added with another device file.
[    36.087] (II) config/udev: Adding input device HDA ATI SB Line Out Front (/dev/input/event12)
[    36.087] (II) No input driver specified, ignoring this device.
[    36.087] (II) This device may have been added with another device file.
[    36.087] (II) config/udev: Adding input device HDA ATI SB Line (/dev/input/event5)
[    36.087] (II) No input driver specified, ignoring this device.
[    36.087] (II) This device may have been added with another device file.
[    36.087] (II) config/udev: Adding input device HDA ATI SB Front Mic (/dev/input/event6)
[    36.087] (II) No input driver specified, ignoring this device.
[    36.087] (II) This device may have been added with another device file.
[    36.087] (II) config/udev: Adding input device HDA ATI SB Rear Mic (/dev/input/event7)
[    36.087] (II) No input driver specified, ignoring this device.
[    36.087] (II) This device may have been added with another device file.
[    36.087] (II) config/udev: Adding input device HDA ATI SB Front Headphone (/dev/input/event8)
[    36.087] (II) No input driver specified, ignoring this device.
[    36.087] (II) This device may have been added with another device file.
[    36.088] (II) config/udev: Adding input device HDA ATI SB Line Out Side (/dev/input/event9)
[    36.088] (II) No input driver specified, ignoring this device.
[    36.088] (II) This device may have been added with another device file.
[    37.687] (II) XKB: reuse xkmfile /var/lib/xkb/server-C28582241CA6933AEE84E4C600A451AEF1D7A6E9.xkm
[    37.689] (II) XKB: reuse xkmfile /var/lib/xkb/server-C28582241CA6933AEE84E4C600A451AEF1D7A6E9.xkm
[    37.831] (II) XKB: reuse xkmfile /var/lib/xkb/server-C28582241CA6933AEE84E4C600A451AEF1D7A6E9.xkm
[    37.881] (II) XKB: reuse xkmfile /var/lib/xkb/server-C28582241CA6933AEE84E4C600A451AEF1D7A6E9.xkm
[    38.565] (II) XKB: reuse xkmfile /var/lib/xkb/server-C28582241CA6933AEE84E4C600A451AEF1D7A6E9.xkm
[    38.567] (II) XKB: reuse xkmfile /var/lib/xkb/server-C28582241CA6933AEE84E4C600A451AEF1D7A6E9.xkm
[    38.569] (II) XKB: reuse xkmfile /var/lib/xkb/server-C28582241CA6933AEE84E4C600A451AEF1D7A6E9.xkm
[    38.571] (II) XKB: reuse xkmfile /var/lib/xkb/server-C28582241CA6933AEE84E4C600A451AEF1D7A6E9.xkm
[    38.573] (II) XKB: reuse xkmfile /var/lib/xkb/server-C28582241CA6933AEE84E4C600A451AEF1D7A6E9.xkm
[    38.575] (II) XKB: reuse xkmfile /var/lib/xkb/server-C28582241CA6933AEE84E4C600A451AEF1D7A6E9.xkm
[    38.577] (II) XKB: reuse xkmfile /var/lib/xkb/server-C28582241CA6933AEE84E4C600A451AEF1D7A6E9.xkm
[    38.579] (II) XKB: reuse xkmfile /var/lib/xkb/server-C28582241CA6933AEE84E4C600A451AEF1D7A6E9.xkm
[    38.581] (II) XKB: reuse xkmfile /var/lib/xkb/server-C28582241CA6933AEE84E4C600A451AEF1D7A6E9.xkm
[    38.582] (II) XKB: reuse xkmfile /var/lib/xkb/server-C28582241CA6933AEE84E4C600A451AEF1D7A6E9.xkm
[    38.584] (II) XKB: reuse xkmfile /var/lib/xkb/server-C28582241CA6933AEE84E4C600A451AEF1D7A6E9.xkm
[    38.586] (II) XKB: reuse xkmfile /var/lib/xkb/server-C28582241CA6933AEE84E4C600A451AEF1D7A6E9.xkm
[    38.588] (II) XKB: reuse xkmfile /var/lib/xkb/server-C28582241CA6933AEE84E4C600A451AEF1D7A6E9.xkm
[    38.590] (II) XKB: reuse xkmfile /var/lib/xkb/server-C28582241CA6933AEE84E4C600A451AEF1D7A6E9.xkm
[    38.592] (II) XKB: reuse xkmfile /var/lib/xkb/server-C28582241CA6933AEE84E4C600A451AEF1D7A6E9.xkm
[    38.594] (II) XKB: reuse xkmfile /var/lib/xkb/server-C28582241CA6933AEE84E4C600A451AEF1D7A6E9.xkm
[    38.596] (II) XKB: reuse xkmfile /var/lib/xkb/server-C28582241CA6933AEE84E4C600A451AEF1D7A6E9.xkm
[    53.464] (II) XKB: reuse xkmfile /var/lib/xkb/server-C28582241CA6933AEE84E4C600A451AEF1D7A6E9.xkm
[    58.558] (II) XKB: reuse xkmfile /var/lib/xkb/server-9E270690B65DB945530004394EFD030FCDE588D9.xkm
[    59.432] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[    59.446] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   105.415] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   106.979] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   110.363] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   110.659] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   112.387] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   116.611] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   222.743] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   222.943] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   223.367] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   223.799] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   225.919] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   226.221] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   227.352] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   227.463] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   228.282] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   230.698] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   232.263] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   234.967] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   236.528] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   241.598] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   241.655] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   242.828] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   242.831] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   243.023] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   243.031] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   243.822] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   243.846] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   251.286] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   251.302] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   252.473] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   252.476] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   254.318] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   256.686] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   261.302] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   261.356] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   262.886] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   263.588] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   288.341] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   290.507] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   291.901] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   292.333] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   292.589] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   292.677] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   293.213] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   295.021] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   295.412] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   295.484] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   297.821] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   302.421] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   303.255] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   312.524] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   314.196] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   314.628] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   321.772] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   321.820] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   323.147] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   323.323] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   328.076] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   328.499] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   330.108] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   330.531] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   331.619] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   331.780] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   332.627] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   332.859] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   333.547] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   333.819] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   334.380] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   334.803] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   348.475] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   348.843] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   350.211] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   350.547] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   353.408] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   354.882] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   355.914] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   356.202] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   356.659] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   356.974] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   357.608] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   358.050] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   363.955] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   364.256] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   380.977] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   381.745] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   382.184] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   390.353] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   391.769] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   393.169] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   397.785] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   398.423] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   434.080] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   434.168] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   435.595] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   435.612] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   436.768] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   437.471] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   437.600] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   437.887] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   438.048] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   438.351] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   438.568] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   438.743] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   438.896] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   439.133] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   439.312] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   439.527] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   439.659] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   439.899] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   440.568] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   440.863] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   441.008] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   441.607] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   442.664] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   443.015] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   443.751] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   443.961] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   444.713] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   444.991] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   446.047] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   446.471] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   447.180] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   447.591] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   449.319] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   450.836] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   451.640] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   451.735] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   451.944] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   452.252] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   452.479] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   452.759] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   458.807] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   458.879] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   459.183] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   459.270] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   465.087] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   465.278] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   465.594] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   465.884] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   467.190] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   474.958] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   475.310] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   475.494] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   475.580] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   475.700] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   475.820] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   475.940] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   476.348] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   476.402] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   476.798] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   477.102] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   477.126] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   477.692] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   477.695] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   479.582] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   480.182] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   481.143] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   481.597] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   481.678] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   481.796] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   481.881] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   482.228] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   482.366] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   482.822] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   482.974] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   484.796] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   485.430] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   485.708] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   485.750] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   485.982] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   486.332] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   486.542] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   486.886] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   487.133] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   487.710] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   487.718] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   488.141] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   488.182] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   488.366] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   488.420] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   489.110] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   489.517] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   490.844] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   490.868] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   491.254] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   491.286] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   493.181] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   494.061] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   494.771] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   494.973] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   495.332] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   495.335] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   496.061] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   496.070] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   519.445] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   519.841] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   520.357] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   520.805] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   524.925] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   527.545] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   528.453] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   529.172] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   557.531] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   558.534] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   559.500] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   560.723] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   585.224] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   585.426] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   594.450] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   594.746] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   595.026] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   595.402] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   596.648] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   596.936] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   597.362] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   597.618] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   598.170] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   598.482] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   598.592] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   598.730] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   598.826] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   598.977] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   599.053] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   599.209] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   600.458] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   600.722] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   601.482] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   601.689] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   602.009] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   602.257] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
[   662.416] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CC07C081DD5050B262656DD35921CA8CCCEF335.xkm
```

---

### Post by DoingMyHeadIn on 2013-01-05
HI Guys

Same problem. I am running a nvidia quadro 4000 have updated drivers but the resolution is still on laptop.  Have mesa-utils installed.

---

### Post by Yellow Pasque on 2013-01-05
@patman: you need to remove the fglrx/Catalyst driver. That's what's causing the problem.

---

### Post by patman0623 on 2013-01-06
> **Temüjin said:**
> @patman: you need to remove the fglrx/Catalyst driver. That's what's causing the problem.
Oh, thank you! Now if I remove it, though, when I put the hard drive back in the laptop in a few weeks after I get it fixed, I'm worried it won't display anymore. Is this unfounded?

---

### Post by Yellow Pasque on 2013-01-06
> **patman0623 said:**
> Oh, thank you! Now if I remove it, though, when I put the hard drive back in the laptop in a few weeks after I get it fixed, I'm worried it won't display anymore. Is this unfounded?
Not entirely unfounded, depending on what GPU the laptop has. You could get around this by reinstalling fglrx package right before you transfer the disk.

---

### Post by patman0623 on 2013-01-06
This indeed fixed my problem. Thank you very much, Temüjin!

---

