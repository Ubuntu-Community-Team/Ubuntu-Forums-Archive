---
title: "Intrepid Ibex (8.10) Live CD boots to terminal"
date: 2009-03-20
forum: Installation &amp; Upgrades
---

### Post by Pyker on 2009-03-20
When I try to boot from the Ubuntu 8.10 Live CD, that I asked to ship to me through the Ubuntu's website, it boots up as usual, saying that everything is OK ```
something....        [OK]
``` but when it goes to load the desktop, it instead brings me the console.

I already tried ```
sudo startx
``` but it returned an error and couldn't start.
I also tried ```
sudo gnome-session
``` but again it returned an error and couldn't start.

Is there a fix for this?

Thanks in advance.

[EDIT] I tried the "Install Ubuntu" option in the CD that I downloaded through torrent today, and it freezes at loading Ubiquity. However, if I press Ctrl+Alt+Del, it acts like it's shutting down but brings me the console. If I type 'ubiquity' at the console, it just says it "Can't open the screen", however if I try that again, it goes nuts, kills tty1 (my console), says that it failed loading Ubiquity and shutsdown the computer.

---

### Post by lemming465 on 2009-03-21
It appears that your video chip isn't supported, at least not by the live desktop CD.  Feed us the output from *sudo lspci -v* and perhaps attach the contents of the /var/log/Xorg.0.log file, and we may be able to diagnose it better.

Sometimes if you use the text-based installer on the *alternate install CD* that will get enough of ubuntu onto the system that you can fix the video, e.g. by installing a restricted binary proprietary driver which does support your video chip.

---

### Post by Pyker on 2009-03-23
Thanks for your reply.

Now I noticed something that I'm not sure whether it's important or not.
It boots to terminal if in the "Boot Options" (F6, I guess), I remove the "quiet splash" options.
If I don't, it loads as normal, but when it reaches "Checking battery state.... [OK]", the screen blinks 3 times and then the computer hangs (all the keys work, the only one that does anything relevant other than outputting to the console is Ctrl+Alt+Del [restarts the computer]).

BTW, my graphics card is an ATI Mobility Radeon HD2400.

Here are the "sudo lspci v-" and "/var/log/Xorg.0.log" after executing "sudo startx":

"/var/log/Xorg.0.log"
```

X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux ubuntu 2.6.27-7-generic #1 SMP Fri Oct 24 06:42:44 UTC 2008 i686
Build Date: 24 October 2008  08:00:16AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Mar 23 20:48:59 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81d9a40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 4.1
	X.Org XInput driver : 2.1
	X.Org Server Extension : 1.1
	X.Org Font Renderer : 0.6
(II) Loader running on linux
(--) using VT number 8

(--) PCI:*(0@1:0:0) ATI Technologies Inc Mobility Radeon HD 2400 rev 0, Mem @ 0xf0000000/0, 0xf8000000/0, I/O @ 0x00009000/0, BIOS @ 0x????????/131072
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[24] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[25] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[26] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[27] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[28] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[29] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(==) AIGLX enabled
(==) Exporting typical set of GLX visuals
(II) Loading extension GLX
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.5.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "record"

(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension RECORD
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
(II) Matched radeon from file name radeon.ids
(==) Matched radeon for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "radeon"

(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 1.5.1, module version = 6.9.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) RADEON: Driver for ATI Radeon chipsets:
	ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X600 (RV380) 3E50 (PCIE),
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
	ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI ATI FireGL V7400,
	ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
	ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
	ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
	ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
	ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
	ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
	ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
	ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
	ATI Radeon 4800 Series, ATI RV610, ATI Radeon HD 2400 XT,
	ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
	ATI RV610, ATI ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
	ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610, ATI RV670,
	ATI Radeon HD3870, ATI Radeon HD3850, ATI RV670,
	ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850, ATI RV630,
	ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
	ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
	ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
	ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
	ATI FireGL V3600, ATI Radeon HD 2600 LE, ATI Radeon HD 3470,
	ATI Radeon HD 3450, ATI Radeon HD 3430, ATI Mobility Radeon HD 3430,
	ATI Mobility Radeon HD 3400 Series, ATI FireMV 2450, ATI FireMV 2260,
	ATI FireMV 2260, ATI ATI Radeon HD 3600 Series,
	ATI ATI Radeon HD 3650 AGP, ATI ATI Radeon HD 3600 PRO,
	ATI ATI Radeon HD 3600 XT, ATI ATI Radeon HD 3600 PRO,
	ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics
(II) Primary Device is: PCI 01@00:00:0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[24] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[25] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[26] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[27] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[28] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[29] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[20] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[21] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[22] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[23] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[24] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[25] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[26] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[27] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[28] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[29] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[30] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[31] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[32] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[33] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[34] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) RADEON(0): MMIO registers at 0x00000000f8000000: size 64KB
(II) RADEON(0): PCI bus 1 card 0 func 0
(II) RADEON(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(==) RADEON(0): Depth 24, (==) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"

(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 4.1
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(--) RADEON(0): Chipset: "ATI Mobility Radeon HD 2400" (ChipID = 0x94c9)
(WW) RADEON(0): R600 support is mostly incomplete and very experimental
(--) RADEON(0): Linear framebuffer at 0x00000000f0000000
(II) RADEON(0): PCIE card detected
(II) RADEON(0): using shadow framebuffer
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"

(II) Loading /usr/lib/xorg/modules//libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.1.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 4.1
(II) RADEON(0): initializing int10
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(II) RADEON(0): ATOM BIOS detected
(II) RADEON(0): ATOM BIOS Rom: 
	SubsystemVendorID: 0x1179 SubsystemID: 0xff00
	IOBaseAddress: 0x9000
	Filename: BR26686.BIN 
	BIOS Bootup Message: 

IALAA M72M GDDR2 128/256M 400m/450e                                         


(II) RADEON(0): Framebuffer space used by Firmware (kb): 20
(II) RADEON(0): Start of VRAM area used by Firmware: 0x7ffb000
(II) RADEON(0): AtomBIOS requests 20kB of VRAM scratch space
(II) RADEON(0): AtomBIOS VRAM scratch base: 0x7ffb000
(II) RADEON(0): Cannot get VRAM scratch space. Allocating in main memory instead
(II) RADEON(0): Default Engine Clock: 440000
(II) RADEON(0): Default Memory Clock: 400000
(II) RADEON(0): Maximum Pixel ClockPLL Frequency Output: 1200000
(II) RADEON(0): Minimum Pixel ClockPLL Frequency Output: 0
(II) RADEON(0): Maximum Pixel ClockPLL Frequency Input: 13500
(II) RADEON(0): Minimum Pixel ClockPLL Frequency Input: 1000
(II) RADEON(0): Maximum Pixel Clock: 400000
(II) RADEON(0): Reference Clock: 27000
(II) RADEON(0): Direct rendering not officially supported on RN50/RS600/R600
(II) RADEON(0): Generation 2 PCI interface, using max accessible memory
(II) RADEON(0): Detected total video RAM=131072K, accessible=131072K (PCI BAR=131072K)
(--) RADEON(0): Mapped VideoRAM: 131072 kByte (64 bit DDR SDRAM)
(II) RADEON(0): Color tiling disabled
(II) RADEON(0): Max desktop size set to 2560x1600
(II) RADEON(0): For a larger or smaller max desktop size, add a Virtual line to your xorg.conf
(II) RADEON(0): If you are having trouble with 3D, reduce the desktop size by adjusting the Virtual line to your xorg.conf
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) RADEON(0): ref_freq: 2700, min_out_pll: 64800, max_out_pll: 120000, min_in_pll: 100, max_in_pll: 1350, xclk: 40000, sclk: 440.000000, mclk: 400.000000
(II) RADEON(0): PLL parameters: rf=2700 rd=12 min=64800 max=120000; xclk=40000
object id 0005 01
src object id 2115 21
record type 1
record type 4
object id 000c 01
src object id 2113 19
record type 1
record type 2
record type 4
object id 000f 01
src object id 2116 22
record type 4
object id 000e 01
src object id 210f 15
record type 1
record type 4
(II) RADEON(0): Output VGA-0 using monitor section Configured Monitor
(II) RADEON(0): I2C bus "VGA-0" initialized.
(II) RADEON(0): Output HDMI-0 has no monitor section
(II) RADEON(0): I2C bus "HDMI-0" initialized.
(II) RADEON(0): Output LVDS has no monitor section
(WW) RADEON(0): LVDS Info:
XRes: 1280, YRes: 800, DotClock: 71000
HBlank: 160, HOverPlus: 48, HSyncWidth: 32
VBlank: 23, VOverPlus: 3, VSyncWidth: 6
(II) RADEON(0): I2C bus "LVDS" initialized.
(II) RADEON(0): Port0:
 Monitor   -- AUTO
 Connector -- VGA
 DAC Type  -- Primary
 TMDS Type -- None
 DDC Type  -- 0x7e40
(II) RADEON(0): Port1:
 Monitor   -- AUTO
 Connector -- HDMI-B
 DAC Type  -- None
 TMDS Type -- Internal
 DDC Type  -- 0x7e50
(II) RADEON(0): Port2:
 Monitor   -- AUTO
 Connector -- LVDS
 DAC Type  -- None
 TMDS Type -- LVTMA
 DDC Type  -- 0xac0
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
Dac detection success
finished output detect: 0
(II) RADEON(0): I2C device "HDMI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "HDMI-0:ddc2" removed.
(II) RADEON(0): Output: HDMI-0, Detected Monitor Type: 0
invalid output device for dac detection
finished output detect: 1
(II) RADEON(0): I2C device "LVDS:ddc2" registered at address 0xA0.
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: LPL  Model: dc00  Serial#: 0
(II) RADEON(0): Year: 2006  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.600 redY: 0.351   greenX: 0.324 greenY: 0.554
(II) RADEON(0): blueX: 0.153 blueY: 0.145   whiteX: 0.312 whiteY: 0.328
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 71.0 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 823 v_border: 0
(WW) RADEON(0): Unknown vendor-specific block 0
(II) RADEON(0):  LGPhilipsLCD
(II) RADEON(0):  LP154WX4-TLD2
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00320c00dc00000000
(II) RADEON(0): 	00100103802115780ab3409959538d27
(II) RADEON(0): 	25505400000001010101010101010101
(II) RADEON(0): 	010101010101bc1b00a0502017303020
(II) RADEON(0): 	36004bcf100000190000000000000000
(II) RADEON(0): 	00000000000000000000000000fe004c
(II) RADEON(0): 	475068696c6970734c43440a000000fe
(II) RADEON(0): 	004c503135345758342d544c44320043
finished output detect: 2
finished all detect
before xf86InitialConfiguration
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): I2C device "HDMI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "HDMI-0:ddc2" removed.
(II) RADEON(0): Output: HDMI-0, Detected Monitor Type: 0
invalid output device for dac detection
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: LPL  Model: dc00  Serial#: 0
(II) RADEON(0): Year: 2006  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.600 redY: 0.351   greenX: 0.324 greenY: 0.554
(II) RADEON(0): blueX: 0.153 blueY: 0.145   whiteX: 0.312 whiteY: 0.328
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 71.0 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 823 v_border: 0
(WW) RADEON(0): Unknown vendor-specific block 0
(II) RADEON(0):  LGPhilipsLCD
(II) RADEON(0):  LP154WX4-TLD2
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00320c00dc00000000
(II) RADEON(0): 	00100103802115780ab3409959538d27
(II) RADEON(0): 	25505400000001010101010101010101
(II) RADEON(0): 	010101010101bc1b00a0502017303020
(II) RADEON(0): 	36004bcf100000190000000000000000
(II) RADEON(0): 	00000000000000000000000000fe004c
(II) RADEON(0): 	475068696c6970734c43440a000000fe
(II) RADEON(0): 	004c503135345758342d544c44320043
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "LPL", prod id 56320
(II) RADEON(0): Output VGA-0 disconnected
(II) RADEON(0): Output HDMI-0 disconnected
(II) RADEON(0): Output LVDS connected
(II) RADEON(0): Using exact sizes for initial modes
(II) RADEON(0): Output LVDS using initial mode 1280x800
after xf86InitialConfiguration
(==) RADEON(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"

(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(==) RADEON(0): No acceleration support available on R600 yet.
(!!) RADEON(0): For information on using the multimedia capabilities
	of this adapter, please see http://gatos.sf.net.
(!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[20] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[21] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[22] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[23] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[24] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[25] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[26] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[27] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[28] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[29] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[30] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[31] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[32] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[33] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[34] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) RADEON(0): RADEONScreenInit f0000000 0 0
Blank CRTC 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
mc fb loc is 00f700f0
(II) RADEON(0): RADEONInitMemoryMap() : 
(II) RADEON(0):   mem_size         : 0x08000000
(II) RADEON(0):   MC_FB_LOCATION   : 0x00f700f0
(II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
(II) RADEON(0): Depth moves disabled by default
(II) RADEON(0): Memory manager initialized to (0,0) (1280,8191)
(II) RADEON(0): Reserved area from (0,1280) to (1280,1282)
(II) RADEON(0): Largest offscreen area available: 1280 x 6909
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x00f700f0 0x00f700f0
(II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
(==) RADEON(0): Backing store disabled
(WW) RADEON(0): Direct rendering disabled
(EE) RADEON(0): Acceleration initialization failed
(II) RADEON(0): Acceleration disabled
(II) RADEON(0): DPMS enabled
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Will use 32 kb for hardware cursor 0 at offset 0x00643000
(II) RADEON(0): Will use 32 kb for hardware cursor 1 at offset 0x00648000
(II) RADEON(0): Largest offscreen area available: 1280 x 6901
Output 68 disable success
Output 66 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
Blank CRTC 0 success
Disable CRTC 0 success
Mode 1280x800 - 1440 823 10
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x00f700f0 0x00f700f0
(II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
freq: 71000000
best_freq: 71015625
best_feedback_div: 505
best_ref_div: 12
best_post_div: 16
(II) RADEON(0): crtc(0) Clock: mode 71000, PLL 71010
(II) RADEON(0): crtc(0) PLL  : refdiv 12, fbdiv 0x1F9(505), pdiv 16
Set CRTC PLL success
Set CRTC Timing success
Not using RMX
scaler 0 setup success
Set CRTC 0 Source success
(EE) RADEON(0):  ParseTable said: CD_INVALID_OPCODE
(II) RADEON(0): Query for AtomBIOS Exec: failed
Output DIG2 setup failed

Backtrace:
0: /usr/bin/X11/X(xf86SigHandler+0x79) [0x80c3009]
1: [0xb809f400]
2: /usr/lib/xorg/modules/drivers//radeon_drv.so [0xb7b37e51]
3: /usr/lib/xorg/modules/drivers//radeon_drv.so [0xb7b377ce]
4: /usr/lib/xorg/modules/drivers//radeon_drv.so [0xb7b36840]
5: /usr/lib/xorg/modules/drivers//radeon_drv.so [0xb7b37a38]
6: /usr/lib/xorg/modules/drivers//radeon_drv.so [0xb7b3b8ee]
7: /usr/lib/xorg/modules/drivers//radeon_drv.so [0xb7b39018]
8: /usr/lib/xorg/modules/drivers//radeon_drv.so [0xb7b39180]
9: /usr/lib/xorg/modules/drivers//radeon_drv.so [0xb7b4f6c1]
10: /usr/lib/xorg/modules/drivers//radeon_drv.so [0xb7b50704]
11: /usr/lib/xorg/modules/drivers//radeon_drv.so [0xb7b30b38]
12: /usr/bin/X11/X(xf86CrtcSetMode+0x5da) [0x80eb42a]
13: /usr/bin/X11/X(xf86SetDesiredModes+0x1af) [0x80eb7df]
14: /usr/lib/xorg/modules/drivers//radeon_drv.so [0xb7b141ea]
15: /usr/bin/X11/X(AddScreen+0x19f) [0x807137f]
16: /usr/bin/X11/X(InitOutput+0x206) [0x80aa536]
17: /usr/bin/X11/X(main+0x279) [0x8071b19]
18: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7ca8685]
19: /usr/bin/X11/X [0x8071101]
Saw signal 11.  Server aborting.
Blank CRTC 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x00f700f0 0x00f700f0
(II) RADEON(0):   MC_AGP_LOCATION  : 0x00000000
(II) RADEON(0): avivo_restore !
Enable CRTC 0 success
Unblank CRTC 0 success
```

"sudo lspci -v"
```
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
	Subsystem: Toshiba America Info Systems Device ff00
	Flags: bus master, 66MHz, medium devsel, latency 64
	Kernel modules: ati-agp

00:02.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Graphics Port 0)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: f8000000-f80fffff
	Prefetchable memory behind bridge: 00000000f0000000-00000000f7ffffff
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [b0] Subsystem: Toshiba America Info Systems Device ff00
	Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
	Capabilities: [100] Virtual Channel <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=08, subordinate=0d, sec-latency=0
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [b0] Subsystem: Toshiba America Info Systems Device ff00
	Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
	Capabilities: [100] Virtual Channel <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0e, subordinate=0e, sec-latency=0
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: f8100000-f81fffff
	Prefetchable memory behind bridge: 000000008c000000-000000008c0fffff
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [b0] Subsystem: Toshiba America Info Systems Device ff00
	Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
	Capabilities: [100] Virtual Channel <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=14, subordinate=14, sec-latency=0
	Memory behind bridge: f8200000-f82fffff
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [b0] Subsystem: Toshiba America Info Systems Device ff00
	Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
	Capabilities: [100] Virtual Channel <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA (prog-if 01)
	Subsystem: Toshiba America Info Systems Device ff00
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
	I/O ports at 8440 [size=8]
	I/O ports at 8434 [size=4]
	I/O ports at 8438 [size=8]
	I/O ports at 8430 [size=4]
	I/O ports at 8400 [size=16]
	Memory at f8609000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [60] Power Management version 2
	Kernel driver in use: ahci
	Kernel modules: ahci

00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0) (prog-if 10)
	Subsystem: Toshiba America Info Systems Device ff00
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at f8604000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1) (prog-if 10)
	Subsystem: Toshiba America Info Systems Device ff00
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at f8605000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2) (prog-if 10)
	Subsystem: Toshiba America Info Systems Device ff00
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at f8606000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3) (prog-if 10)
	Subsystem: Toshiba America Info Systems Device ff00
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at f8607000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4) (prog-if 10)
	Subsystem: Toshiba America Info Systems Device ff00
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at f8608000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI) (prog-if 20)
	Subsystem: Toshiba America Info Systems Device ff00
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at f8609400 (32-bit, non-prefetchable) [size=256]
	Capabilities: [c0] Power Management version 2
	Capabilities: [e4] Debug port: BAR=1 offset=00e0
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
	Subsystem: Toshiba America Info Systems Device ff00
	Flags: 66MHz, medium devsel
	I/O ports at 8410 [size=16]
	Capabilities: [b0] HyperTransport: MSI Mapping Enable- Fixed+
	Kernel driver in use: piix4_smbus
	Kernel modules: i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc SB600 IDE (prog-if 8a [Master SecP PriP])
	Subsystem: Toshiba America Info Systems Device ff00
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 8420 [size=16]
	Kernel driver in use: pata_atiixp
	Kernel modules: pata_atiixp

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
	Subsystem: Toshiba America Info Systems Device ff08
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at f8600000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
	Subsystem: Toshiba America Info Systems Device ff00
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01)
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=1a, subordinate=1e, sec-latency=64
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: f8300000-f83fffff
	Prefetchable memory behind bridge: 88000000-8bffffff

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Flags: fast devsel
	Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Flags: fast devsel
	Capabilities: [f0] Secure device <?>
	Kernel driver in use: k8temp
	Kernel modules: k8temp

01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 2400
	Subsystem: Toshiba America Info Systems Device ff00
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at f0000000 (32-bit, prefetchable) [size=128M]
	I/O ports at 9000 [size=256]
	Memory at f8000000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at f8020000 [disabled] [size=128K]
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Legacy Endpoint, MSI 00
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [100] Vendor Specific Information <?>

01:00.1 Audio device: ATI Technologies Inc RV610 audio device [Radeon HD 2400 PRO]
	Subsystem: ATI Technologies Inc RV610 audio device [Radeon HD 2400 PRO]
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at f8010000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Legacy Endpoint, MSI 00
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [100] Vendor Specific Information <?>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

0e:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
	Subsystem: Toshiba America Info Systems Device ff00
	Flags: bus master, fast devsel, latency 0, IRQ 219
	I/O ports at a000 [size=256]
	Memory at f8100000 (64-bit, non-prefetchable) [size=4K]
	[virtual] Expansion ROM at 8c000000 [disabled] [size=128K]
	Capabilities: [40] Power Management version 2
	Capabilities: [48] Vital Product Data <?>
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [60] Express Endpoint, MSI 00
	Capabilities: [84] Vendor Specific Information <?>
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [12c] Virtual Channel <?>
	Capabilities: [148] Device Serial Number 36-81-ec-10-00-00-00-02
	Capabilities: [154] Power Budgeting <?>
	Kernel driver in use: r8169
	Kernel modules: r8169

14:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: Askey Computer Corp. Device 7096
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at f8200000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: [40] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [60] Express Legacy Endpoint, MSI 00
	Capabilities: [90] MSI-X: Enable- Mask- TabSize=1
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Virtual Channel <?>
	Kernel driver in use: ath_pci
	Kernel modules: ath_pci

1a:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
	Subsystem: Toshiba America Info Systems Device ff00
	Flags: bus master, medium devsel, latency 168, IRQ 20
	Memory at f8300000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=1a, secondary=1b, subordinate=1e, sec-latency=176
	Memory window 0: 88000000-8bfff000 (prefetchable)
	Memory window 1: 90000000-93fff000
	I/O window 0: 00002000-000020ff
	I/O window 1: 00002400-000024ff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

1a:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller (prog-if 10)
	Subsystem: Toshiba America Info Systems Device ff00
	Flags: bus master, medium devsel, latency 64, IRQ 21
	Memory at f8302000 (32-bit, non-prefetchable) [size=2K]
	Memory at f8304000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: ohci1394
	Kernel modules: ohci1394

1a:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
	Subsystem: Toshiba America Info Systems Device ff00
	Flags: bus master, medium devsel, latency 64, IRQ 22
	Memory at f8301000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: tifm_7xx1
	Kernel modules: tifm_7xx1

1a:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller (prog-if 01)
	Subsystem: Toshiba America Info Systems Device ff00
	Flags: bus master, medium devsel, latency 64, IRQ 22
	Memory at f8302800 (32-bit, non-prefetchable) [size=256]
	Capabilities: [80] Power Management version 2
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

```

---

### Post by lemming465 on 2009-03-24
Ok, the open source radeon driver isn't working for you, so maybe it's time to try the closed source ATI driver:```

sudo -i
aptitude install xorg-driver-fglrx
dpkg-reconfigure xserver-xorg
startx
```

---

### Post by Pyker on 2009-03-25
Ok, that also doesn't work. It goes everything perfect until it reaches the startx command (it does the same thing as if I hadn't installed anything).

I feel like we're running out of options... :(

Any more suggestions?

Thank you for spending your time helping me. ;)

---

### Post by lemming465 on 2009-03-25
> **Pyker said:**
> Ok, that also doesn't work... I feel like we're running out of options...

Au contraire, there are quite a few more things yet to try.  For example, we can fiddle with some of the kernel boot parameters, try the plain vesa driver, or try more recent Linux versions such as Fedora 10 (about a month newer than Ubuntu 8.10) or Ubuntu 9.04 (hits beta tomorrow).

Is there a BIOS update for your motherboard?  Check your vendor's support site.  If there is, try installing that.

Next thing to try alternate boot options: modify the kernel line to remove "quiet splash" and add various combinations of *apm=off*, *nolapic*, and *noapic*. Try them one at a time, and try all three at once (separated by spaces).  If all three at once works, see if any can be left out.

For that matter, what is the maker and model of this recalcitrant PC?

You can also try editing /etc/X11/xorg.conf and forcing a specific driver, notably:```

sudo pico /etc/X11/xorg.conf
Section "Device"
	Identifier	"Configured Video Device"
	Driver	"vesa"
EndSection
```

I'm not sure if the ATI binary driver actually got preferred; you could also try *Driver "fglrx"* there.

> Thank you for spending your time helping me. ;)
You're welcome.  The first page of the first Unix manual I ever read (BSD 4.2 Unix, back in '82), suggested that if it was your first time using Unix, bring a friend.  It was wise advice then, and still is today.  Since I don't currently have the time to contribute code to Linux, contributing advice is a good alternative way for me to help the free source community.

---

### Post by Pyker on 2009-03-26
My computer is an Toshiba Satellite A210-1CE. But the problem is that I think it's European only. :(

The curious stuff here is that I didn't had any problem installing Hardy Heron (7.04). And I don't exactly remember, but I guess I installed 8.10 from the Live CD _ONCE_, since 7.04 didn't have support for wide-screen.

I will try to find the page for my computer specs, preferentially on English. ;)

OK, couldn't find the English page for my computer, translating to English by myself (sorry if it has mistakes :)):
```
Processor: AMD Turion 64 X2 Dual-Core TL-60 2.0GHz
RAM Memory: 2GB DDR2 RAM (667 MHz)
Hard drive: 200GB S.M.A.R.T Enabled, 4200rpm
Screen: 15.4" Toshiba TruBrite WXGA TFT High Brightness
Graphics card: ATI Mobility Radeon HD2400 with HyperMemory technology, 128 MB dedicated VRAM (up to 895 MB available via HyperMemory with 2 GB of system memory), DDR Video RAM and DDR system memory combined, 16x PCI Express.

```

The rest of the specs don't really matter, however, if you need any just let me know, or you can try to translate the page at [http://pt.toshib.../]("http://pt.computers.toshiba-europe.com/innovation/jsp/SUPPORTSECTION/discontinuedProductPage.do?service=PT&highlightOption=111593&com.broadvision.session.new=Yes&PRODUCT_ID=150400#0") (although I already tried and failed to translate through Google and Babelfish).

Also, there is no recent BIOS update. All the other updates were already installed.

EDIT:

None of the options you gave me worked. I tried "apm=off nolapic noapic" all at once, no effect, I installed the fglrx driver and edited as you said, no effect. :(

One question: After doing "aptitude install xorg-driver-fglrx", when it says "ldconfig deferred processing is now taking place" (something like that), it says a bunch of lines (15-20) saying "Buffer I/O error, dev sr1, logical block xx", where xx is a number or it says "end_request: I/O error, dev sr1, section xx" (something like that).
Other question: What does the line "Screen(s) found, but none have a usable configuration." really mean? It says that line when I execute "startx" (with user root).

---

### Post by lemming465 on 2009-03-26
I myself have a toshiba satellite A215, but it has a slightly different ATI video chip, which doesn't trip the driver bug you are suffering.  Your Xorg.0.log had > Saw signal 11.  Server aborting.
which indicates an illegal address reference, which is always a bug.

> ... couldn't find the English page for my computer
That's OK, your English is better than my Portugese.  I have a smattering of Spanish, French, German and a hint of Russian, so I can almost read the Portugese.  Well enough to decipher the spec's anyway; your translation looks fine.

> ... there is no recent BIOS update
The support site you linked to had one from July 2008.  Is that the one you are running?  My Toshiba it wouldn't warm boot reliably from Linux until I updated the BIOS, though cold boots were OK, and reboots from Microsoft Vista were OK.

> "Buffer I/O error, dev sr1, logical block xx"
That sounds like a read failure on the CD.  Have you run the CD self-test, and did it pass?  If it was a badly burned CD, with write errors, then things are not likely to work.

Also, the advice I gave for changing the X server mostly applies to disk installs.  If you are still running only from the live CD, it's less effective.

If your CD turns out to be pass the self-test, I'd suggest trying the 9.04 beta live CD instead; it's being released tonight.  It has another 6 months of development and bug fixes in the ATI drivers.  I don't know if you have the bandwidth to download that; if not you might have to wait a month until someone could ship you an actual 9.04 CD.

> What does the line "Screen(s) found, but none have a usable configuration." really mean?
There are basically two ways for the X server to be unable to display stuff.  In your case, it's because the video chip driver is dying.  The more common scenario is that it can't figure out a compatible display mode (screen size and pixel timings); that was a big problem on CRT's in the early 1990's, but is almost never a problem on LCD's today.  In your case the Xorg.0.log feedback > Mode 1280x800 - 1440 823 10
...
freq: 71000000

suggests that the X server thinks it can successfully talk to the display.

---

### Post by Pyker on 2009-03-27
> Have you run the CD self-test, and did it pass?
Yes, both the shipped CD and the downloaded CD passed that test.
I currently am using the shipped live CD, however, I don't think that has anything to do with the rest.

> The support site you linked to had one from July 2008. Is that the one you are running?
Yes, I did found that update, however I need to boot to Windows to install it. :(
I'll update you with more details after I install the BIOS update, tonight (1AM 28/03/2009 GMT -05:00, I guess).

> I'd suggest trying the 9.04 beta live CD instead
Yes, I'll try that. ;) I'll download it tomorrow, since my internet's [Happy Hour]("http://en.wikipedia.org/wiki/Happy_Hour_(disambiguation)") for today has finished.

UPDATE:
The BIOS updated couldn't be installed since the BIOS was already up-to-date. Aparently, I had already installed the update. :)

UPDATE2:
OK, so I tried the beta, and what happens? I can't even get to the console. :(
So this is what happened:
I created a USB startup disk using the .iso of the 9.04 beta (I choosed "Documents and settings will be: Discarded on shutdown..."), and I booted through my USB flash drive.
I selected the English language, Portuguese keymap and started "Try Ubuntu without making any changes to your computer" (with the default boot options). I was presented by the same message I'm always presented (even on my Ubuntu installation: "MP-BIOS bug, aperture ... 4GB"), but then a strange message showed up: "ata1: soft reset failed (device not ready)".
Also, it sometimes locks up when selecting the boot option.
The problem is not this message, but what shows after some debugging ([xx.xxxxx] is the timestamp):
```
[xx.xxxxx] Kjournald starting. Commit interval 5 seconds
[xx.xxxxx] EXT3-fs: mounted filesystem with ordered data mode.
```
It outputs this every 3 seconds. Also, when it outputs this, it accesses my hard drive (don't know why).

Also, I don't know if this is important or not, but after the "ata1: soft reset ..." message, it shows "FAILED to load /lib/..." (I guess it's /lib/).

So, what am I doing wrong? :)

---

### Post by lemming465 on 2009-03-29
> "ata1: soft reset failed (device not ready)"
If you have a an IDE CD drive (not SATA), and booted from a USB stick, this would be normal.

> it sometimes locks up when selecting the boot option
Distressing.  The USB/CD boots usually start from the syslinux boot loader, which like all boot loaders uses BIOS routines to do all its I/O. If there is some kind of incompatibility between the BIOS calls it tries to make and your BIOS it could lock up there. Once the linux kernel is loaded, if things get that far, it has to use its native drivers, and if there are any hardware glitches probing or accessing stuff, it can lock up there too.  This may or may not be the fault of syslinux and linux; there is a lot of flakey hardware out there, and timing bugs on initialization is a typical result of a hardware/firmware bug, which is not something an OS can control. On my Toshiba I sometimes get BIOS lockups before it even gets to the boot loader stage.  Power-cycling it usually gets past that.
> [xx.xxxxx] Kjournald starting. Commit interval 5 seconds
[xx.xxxxx] EXT3-fs: mounted filesystem with ordered data mode.

This is normal for disk filesystems.  With 2.6 kernels "dirty" block buffers from writes are flushed back to disk by a kernel thread; that's what the "kjournald" is, a kernel-based ext3 journal daemon I/O writer thread.  The "ordered data mode" is one of several write-back strategies you can tell an ext3 filesystem to use; it is the default, most common, and usually the best tradeoff between safety and speed (data blocks are written first, then inode and directory metadata is journalled, then metadata is written).

> It outputs this every 3 seconds. Also, when it outputs this, it accesses my hard drive (don't know why).
The every 3 seconds thing sounds like a problem.  The typical reason for a hard drive access on an idle filesystem would be a superblock timestamp update, but that shouldn't be happening that often.
> "FAILED to load /lib/..."
That sounds like the kernel boot process couldn't mount the root filesystem off the USB stick.  Which might have soemthing to do with the disk access; it doesn't know where the bootloader came from, and has to try all the devices it can access until it finds it.  There may be somekind of chipset driver problem interfering with finding the ISO image using the native drivers.

---

### Post by Pyker on 2009-03-30
So, what should I do?

Now I got really lost. :)

---

### Post by lemming465 on 2009-03-30
> So, what should I do? ... Now I got really lost.

I'm sorry to have been so obscure.  Given that the 8.10 and 9.04 Ubuntu live CD's are both messing up for you, the situation is bad.  If you are in the mood to try more experiments, some likely ones would be:

(1) Try a Fedora 10 live CD, and see if it does any better than the Ubuntu ones.

(2) Try the Ubuntu 9.04 beta alternate install CD, do a text-based install, and if the GUI video doesn't work fall back to the VESA driver, by doing *sudo nano /etc/X11/xorg.conf* and editing the Device paragraph to be: ```

Section "Device"
        Identifier      "Configured Video Device"
        Driver  "vesa"
EndSection
```

(3) Try an Ubuntu 8.04.2 live CD, and see if that works.  8.04 is a long term support release, and will get desktop updates until year 2011.

---

### Post by gorucan on 2009-03-30
before installing, press f4 and use mode for guys with acpi problems?

---

### Post by Pyker on 2009-04-02
Okay, so sorry I only got to answer now, but I had some important things to do and couldn't come here.

@gorucan: What "mode for guys with acpi problems" under the F4 menu are you talking about?

@lemming465:
So, after trying with the Jaunty Jackalope live USB disk some more, I found out that the repetitive message that I posted a while ago, about kjournald and disk reading didn't really go on forever.
It stops about 150 seconds after booting.
Then, it shows this (the terminal):
```

BusyBox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu6) built-in shell (ash)
Enter 'help' for a list of built-in commands.
(initramfs)
```
And then, it works exactly like the terminal, except it has no *man* command, and other ones that the terminal has. Also, whatever I type, it always, almost always (except when an error occurres or I'm executing a command), shows that *(initramfs)* string.

Any clue on what initramfs is or what I can do about it?

If I can't solve this problem, I guess I would try the Hardy Heron live disk, since I really want to stay with Ubuntu. :)

Once again, thanks for helping me with this mess. :)

EDIT:
Now I can't even start the live without applying *noapic* and *nolapic*, or it will just freeze the entire computer, with cold booting as being the only solution (still if I boot it again, I have to use those again).

Also, I don't know why this is happening to me, since I installed Intrepid Ibex 64-Bit successfully, with absolutely no boot problems or even installation problems. And currently, I have a dual-boot with Windows Vista and Intrepid Ibex (64-Bit).
I haven't tried booting again with the 64-Bit live CD, to see if it's a problem only with versions better than 8.10, but I will try this now, and then update you.

UPDATE:
The Hardy Heron 64-Bit Live CD does work (with all the default options -- that means, booting through the CD, and starting it up, without editing anything), and just if you want to compare, I've attached a file to this post. That file is the whole */var/log/* folder of the Hardy Heron 64-Bit Live CD.

EDIT2:
I will also be attaching the */var/log/* folder of the Jaunty Jackalope live USB disk, later tonight.

UPDATE2:
Ok, so I couldn't find the */var/log/* folder on the live USB disk, however, I did found */casper.log* and */conf/initramfs.conf*. I attached them to this post.
So, after analizing *casper.log*, here's what I think it might have happened: as I was using a USB startup disk of the Jaunty live CD image, *init* entered in panic and went to the console. Interpret the log by yourself. ;)
I'm burning to a CD, and then re-updating you.

---

### Post by Pyker on 2009-04-02
**SUCCESS!!!!** At last. :D

The Jaunty Jackalope (9.04) Live CD, not the the USB disk, solved my problem.

So, I take the problem was related to 8.10 only.

Anyways, the problem is now solved and I would like to say a big thanks to you (lemming465).

Now I know who I can count on, if I need help. ;)

How can I move from Intrepid Ibex 64Bit to Jaunty Jackalope 32Bit, while maintaining my programs and settings?
Also, how come I can't upgrade to Jaunty through the Update Manager (*update-manager -d* command)?

---

### Post by lemming465 on 2009-04-12
Busybox is a sort of Linux equivalent of the microsoft command.com; it's a minimal shell with lots of built-in functionality.  Because it's much smaller than a full Posix-compliant shell like BASH, it's widely used in initial ramdisks to run the earliest stages of the system boot process, e.g. loading device drivers prior to startingt /sbin/init.  If you get a busybox prompt your boot process is dying at an intermediate stage, after Grub loaded the kernel, but before nearly everything else.
"initramfs" is the initial ramdisk image decompressed into a temporary memory-only filesystem; it's what's provided from the /boot/initrd.img-* files. "initrd" is short for "INITial RamDisk".  If you are even more expert than I on the innards of the Linux kernel and the ubuntu boot process, you may be able to type useful recovery commands at the busybox prompt.  I'd have to do days of research to get to that point, I fear.

The Ubuntu boot process has "casper" attached as a name to many of its stages; I'm not sure why.  Your casper.log.txt file error messages indicate trouble finding the live CD root filesystem image file, which it needs to loopback mount.  Probably this is because of a missing USB driver; it might work if we identified the right one and found the mystical kernel option to force it being loaded earlier.  Booting from CD-R may be an easier solution, as you have found.

> How can I move from Intrepid Ibex 64Bit to Jaunty Jackalope 32Bit, while maintaining my programs and settings?
I'm not sure if there is any way to easily move between 32-bit and 64-bit versions.  It's almost like completely changing the CPU architecture.  In general 64-bit systems (amd64 or x86-64) systems can run 32-bit (i386) programs, but not vice versa.  It's not too hard to re-install on top of an existing system while preserving data files; either copy the files off and then back, or remove the OS directories only (most of the contents of / /var and /usr except maybe /home and /usr/local) using a live CD, and then don't reformat the disk partitions.  You have to take care with the configuration stuff under your home directory (~/.gconf/, ~/.gnome2, ...); there can be compatibility problems moving between versions.  The upgrade process will try to deal with those, but a reinstall won't.

I'm not sure why *"sudo update-manager -d"* isn't offering to do an 8.10 "intrepid ibex" to 9.04 "jaunty jackalope" transition for you; it did for me.  I started migrating a couple of systems back at 9.04 alpha 6; we're still two weeks from the official release, and about about 6 weeks from a fairly-well debugged version.  By default the 8.04 "hardy heron" release with long term support would only upgrade to the next LTS release (projected to be 10.04 next year), but that can be adjusted in the settings.  See if /etc/update-manager/release-upgrades has "Prompt=LTS".

---

### Post by Pyker on 2009-04-18
I installed Intrepid Ibex 64Bit again, recovered my documents from an earlier backup and reinstalled my programs. After that, all went just as usual.
I guess I'll just use Intrepid Ibex until the official Jaunty release comes.

So, once again, thank you for your help. If I have any other problems, I will just post again.

For now, all I can do is wait...

However, I don't yet know what really happened, because my Jaunty 32Bit installation was OK one day, then I turned my computer off for about 1 hour and half and when I turned it back on, it just gave me the same problem that started this thread.

Oh, why why, did I buy this computer? :D

---

