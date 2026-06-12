---
title: "DVI output to Flatscreen shows no display"
date: 2010-03-28
forum: Hardware
---

### Post by fubofo on 2010-03-28
Hi guys,

I'm very new to Linux in general. I have recently installed Kubuntu 9.10 and performed a full dist-upgrade and update. I decided to connect the box to my flat screen Philips TV via DVI, using simple onboard ATI 9100. The display gets detected OK in System Settings, but for some reason nothing at all will show onscreen (simply states NO INPUT DETECTED).

I have left my original 17" LCD connected and can see some of the resolutions and settings it gives for the Philips monitor, but I have a feeling its not detecting correctly. I think the TV is either 50hz or 60hz and most options giving to me in system settings are 80hz and 72hz.

I would be greatful if anyone could provide full step-by-step advice on what I should be checking/looking for and how to possibly resolve this.

Regards

---

### Post by efflandt on 2010-03-28
Do you have a model number or video technical specifications of the display?  You have not even said what resolution it is.  DVI should automatically use the native display resolution, but not sure how that works with 2 monitors connected at the same time.  The EDID of my 32" 1080p HDTV apparently identifies it as 52". 

One issue that I ran across when connecting a different DVI display is that boot seemed to hang indefinitely with a black screen after the grub2 menu, unless I disabled "splash" as a boot parameter or corrected /etc/usplash.conf to the native resolution of the display.  So on a bootable USB hard drive, I disabled splash.

Kernel boot parameters are changed for grub2 by editing /etc/default/grub (use sudo to run your editor as root) and then running **sudo update-grub**.

Look through /var/log/Xorg.0.log and see what information it shows for that display.  If you connect it after booting instead of having it on before booting, you may need to log out of X and back in before X sees it.

---

### Post by fubofo on 2010-03-28
I believe this is the TV [Philips 42PF7621D]("http://www.plasma-lcd-crt.com/tvs/manufacturers/pos/philips_42pf7621d/?photo=1").

SCREEN
Resolution	**1366x768**
Image Aspect Ratio	**16:9**
Total Pixels	**1049088**
Pixel Response Time	**8 ms**
Brightness	**550 kcd/m2**
Dynamic Contrast	**4000:1**
Viewing angle	**176°**
Sequential Scanning	**Yes**
Image Optimization	**Yes**
Antiglare Screen	**Yes**

Oh I forgot to mention th connection is using a DVI-HDMI adaptor since the computer has DVI-I and the TV has HDMI (no DVI).

It doesn't seem to be a boot problem. I start up with 17" connected then plug in TV - it shows up in settings fine. I start up with TV plugged in and 17" it shows up in settings fine. There simply seems to be some problem getting the TV to recognise the video signal. No matter what resolution I set it at in settings panel, say 800x600 it just shows NO INPUT DETECTED.

I'll have a look through that /var/log/Xorg.0.log and see what it shows. I take it this is where information gets stored relating to any connected display devices for (k)ubuntu ?

---

### Post by fubofo on 2010-03-28
OK so after rechecking.........

Boot up with ONLY 42" TV connected - will display POST, GRUB and Kubuntu loading screen. goes to NO INPUT straight at the point when login normally shows.

Boot up with both 17" and 42" connected - will display POST, GRUB and Kubuntu loading screen on 17". When comes to login screen 17" goes to sleep and 42" displays NO INPUT.

Boot up with ONLY 17" connected - wil display everything fine and login to desktop. So I connect 42" and a dialogue dispays showing new monitor connected, so I go to configure settings. Settings shows VGA-0 connected (with all relevant display parameters) and DVI-0 connected but disabled. I change to 1024x768 @ 60Hz, clone of VGA-0 hit apply and nothing happens. Click OK, re-open kRandr and still shows disabled. Re-appl settings, click OK and it does same thing???

/var/log/xorg.log (can only be obtained with 42" discconected then connected once logged in - because both monitors shut off if connected at boot)
```

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux iQon 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-20-generic root=UUID=cd99094c-f10e-4282-914b-85d260b01669 ro quiet splash
Build Date: 04 March 2010  09:56:47AM
xorg-server 2:1.6.4-2ubuntu4.2 (buildd@) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Mar 28 22:36:43 2010
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0:1:5:0) 1002:5834:1043:8107 ATI Technologies Inc Radeon 9100 IGP rev 0, Mem @ 0xc0000000/268435456, 0xfda00000/65536, I/O @ 0x0000d000/256, BIOS @ 0x????????/131072
(==) Using default built-in configuration (30 lines)
(==) --- Start of built-in configuration ---
	Section "Device"
		Identifier	"Builtin Default ati Device 0"
		Driver	"ati"
	EndSection
	Section "Screen"
		Identifier	"Builtin Default ati Screen 0"
		Device	"Builtin Default ati Device 0"
	EndSection
	Section "Device"
		Identifier	"Builtin Default vesa Device 0"
		Driver	"vesa"
	EndSection
	Section "Screen"
		Identifier	"Builtin Default vesa Screen 0"
		Device	"Builtin Default vesa Device 0"
	EndSection
	Section "Device"
		Identifier	"Builtin Default fbdev Device 0"
		Driver	"fbdev"
	EndSection
	Section "Screen"
		Identifier	"Builtin Default fbdev Screen 0"
		Device	"Builtin Default fbdev Device 0"
	EndSection
	Section "ServerLayout"
		Identifier	"Builtin Default Layout"
		Screen	"Builtin Default ati Screen 0"
		Screen	"Builtin Default vesa Screen 0"
		Screen	"Builtin Default fbdev Screen 0"
	EndSection
(==) --- End of built-in configuration ---
(==) ServerLayout "Builtin Default Layout"
(**) |-->Screen "Builtin Default ati Screen 0" (0)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default ati Device 0"
(==) No monitor specified for screen "Builtin Default ati Screen 0".
	Using a default monitor configuration.
(**) |-->Screen "Builtin Default vesa Screen 0" (1)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default vesa Device 0"
(==) No monitor specified for screen "Builtin Default vesa Screen 0".
	Using a default monitor configuration.
(**) |-->Screen "Builtin Default fbdev Screen 0" (2)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default fbdev Device 0"
(==) No monitor specified for screen "Builtin Default fbdev Screen 0".
	Using a default monitor configuration.
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 6.12.99
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 6.12.99
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 2.2.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers//fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 0.4.0
	ABI class: X.Org Video Driver, version 5.0
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
	ATI Radeon 4800 Series, ATI Radeon 4800 Series, ATI FirePro M7750,
	ATI M98, ATI M98, ATI M98, ATI Mobility Radeon HD 4650,
	ATI Radeon RV730 (AGP), ATI Mobility Radeon HD 4670,
	ATI FirePro M5750, ATI Radeon RV730 (AGP),
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
	ATI Radeon RV710, ATI Radeon RV710, ATI Radeon HD 4350,
	ATI Mobility Radeon 4300 Series, ATI Mobility Radeon 4500 Series,
	ATI Mobility Radeon 4500 Series, ATI FirePro RG220, ATI RV630,
	ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
	ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
	ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
	ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
	ATI FireGL V3600, ATI Radeon HD 2600 LE,
	ATI Mobility FireGL Graphics Processor, ATI Radeon RV710,
	ATI Radeon HD 3470, ATI Mobility Radeon HD 3430,
	ATI Mobility Radeon HD 3400 Series, ATI Radeon HD 3450,
	ATI Radeon HD 3450, ATI Radeon HD 3430, ATI Radeon HD 3450,
	ATI FirePro V3700, ATI FireMV 2450, ATI FireMV 2260, ATI FireMV 2260,
	ATI Radeon HD 3600 Series, ATI Radeon HD 3650 AGP,
	ATI Radeon HD 3600 PRO, ATI Radeon HD 3600 XT,
	ATI Radeon HD 3600 PRO, ATI Mobility Radeon HD 3650,
	ATI Mobility Radeon HD 3670, ATI Mobility FireGL V5700,
	ATI Mobility FireGL V5725, ATI Radeon HD 3200 Graphics,
	ATI Radeon 3100 Graphics, ATI Radeon HD 3200 Graphics,
	ATI Radeon 3100 Graphics, ATI Radeon HD 3300 Graphics,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3000 Graphics,
	ATI Radeon HD 4200, ATI Radeon 4100, ATI Mobility Radeon HD 4200,
	ATI Mobility Radeon 4100, ATI RS880
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 01@00:05:0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) [KMS] drm report modesetting isn't supported.
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux//libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 0.0.2
	ABI class: X.Org Video Driver, version 5.0
(EE) open /dev/fb0: No such file or directory
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) RADEON(0): Built from git commit 7968e1fb89f6b59d1654df48249bf4b81990c008
(II) RADEON(0): TOTO SAYS 00000000fda00000
(II) RADEON(0): MMIO registers at 0x00000000fda00000: size 64KB
(II) RADEON(0): PCI bus 1 card 5 func 0
(II) RADEON(0): Creating default Display subsection in Screen section
	"Builtin Default ati Screen 0" for depth/fbbpp 24/32
(==) RADEON(0): Depth 24, (--) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 0.1.0
	ABI class: X.Org Video Driver, version 5.0
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(--) RADEON(0): Chipset: "ATI Radeon 9100 IGP (A5) 5834" (ChipID = 0x5834)
(--) RADEON(0): Linear framebuffer at 0x00000000c0000000
(II) RADEON(0): AGP card detected
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Video Driver, version 5.0
(II) RADEON(0): initializing int10
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(II) RADEON(0): Legacy BIOS detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:05.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: drmOpenMinor returns 10
drmOpenByBusid: drmGetBusid reports pci:0000:01:05.0
(II) RADEON(0): [dri] Found DRI library version 1.3.0 and kernel module version 1.31.0
(==) RADEON(0): Page Flipping disabled
(II) RADEON(0): Will try to use DMA for Xv image transfers
(II) RADEON(0): Detected total video RAM=131072K, accessible=131072K (PCI BAR=262144K)
(--) RADEON(0): Mapped VideoRAM: 131072 kByte (128 bit DDR SDRAM)
(II) RADEON(0): Color tiling enabled by default
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) RADEON(0): ref_freq: 1432, min_out_pll: 20000, max_out_pll: 35000, min_in_pll: 100, max_in_pll: 1350, xclk: 16670, sclk: 300.000000, mclk: 166.699997
(II) RADEON(0): PLL parameters: rf=1432 rd=6 min=20000 max=35000; xclk=16670
(WW) RADEON(0): No External TMDS Table found
(II) RADEON(0): I2C bus "DVO" initialized.
(II) RADEON(0): I2C device "DVO:RADEON DVO Controller" registered at address 0x70.
(II) RADEON(0): Output VGA-0 has no monitor section
(II) RADEON(0): I2C bus "VGA-0" initialized.
(II) RADEON(0): Output DVI-0 has no monitor section
(II) RADEON(0): I2C bus "DVI-0" initialized.
(II) RADEON(0): Output S-video has no monitor section
(II) RADEON(0): Default TV standard: NTSC
(II) RADEON(0): TV standards supported by chip: NTSC PAL PAL-M NTSC-J 
(II) RADEON(0): Port0:
  XRANDR name: VGA-0
  Connector: VGA
  CRT1: INTERNAL_DAC2
  DDC reg: 0x60
(II) RADEON(0): Port1:
  XRANDR name: DVI-0
  Connector: DVI-D
  DFP2: INTERNAL_DVO1
  DDC reg: 0x6c
(II) RADEON(0): Port2:
  XRANDR name: S-video
  Connector: S-video
  TV1: INTERNAL_DAC2
  DDC reg: 0x0
(II) RADEON(0): I2C device "VGA-0:E-EDID segment register" registered at address 0x60.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): EDID vendor "PHL", prod id 2080
(II) RADEON(0): Using EDID range info for horizontal sync
(II) RADEON(0): Using EDID range info for vertical refresh
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
finished output detect: 0
(II) RADEON(0): I2C device "DVI-0:E-EDID segment register" registered at address 0x60.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
finished output detect: 1
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
finished output detect: 2
finished all detect
before xf86InitialConfiguration
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
(II) RADEON(0): EDID vendor "PHL", prod id 2080
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
(II) RADEON(0): EDID vendor "PHL", prod id 2080
(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): Output VGA-0 connected
(II) RADEON(0): Output DVI-0 disconnected
(II) RADEON(0): Output S-video disconnected
(II) RADEON(0): Using exact sizes for initial modes
(II) RADEON(0): Output VGA-0 using initial mode 1024x768
(**) RADEON(0): Display dimensions: (300, 230) mm
(**) RADEON(0): DPI set to (86, 113)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(==) RADEON(0): Using EXA acceleration architecture
(II) Loading sub module "exa"
(II) LoadModule: "exa"
(II) Loading /usr/lib/xorg/modules//libexa.so
(II) Module exa: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 2.4.0
	ABI class: X.Org Video Driver, version 5.0
(==) RADEON(0): Assuming overlay scaler buffer width is 1536
(II) RADEON(0): No MM_TABLE found - assuming CARD is not TV-in capable.
(!!) RADEON(0): For information on using the multimedia capabilities
	of this adapter, please see http://gatos.sf.net.
(!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
(II) UnloadModule: "vesa"
(II) Unloading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers//fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux//libfbdevhw.so
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) RADEON(0): RADEONScreenInit c0000000 0 0
Entering TV Save
Save TV timing tables
saveTimingTables: reading timing tables
TV Save done
disable TVDAC
(II) RADEON(0): Dynamic Power Management Disabled
(==) RADEON(0): Using 24 bit depth buffer
(II) RADEON(0): RADEONInitMemoryMap() : 
(II) RADEON(0):   mem_size         : 0x08000000
(II) RADEON(0):   MC_FB_LOCATION   : 0x5fff5800
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(II) RADEON(0): Depth moves disabled by default
(II) RADEON(0): Allocating from a screen of 131072 kb
(II) RADEON(0): Will use 32 kb for hardware cursor 0 at offset 0x00400000
(II) RADEON(0): Will use 32 kb for hardware cursor 1 at offset 0x00404000
(II) RADEON(0): Will use 4096 kb for front buffer at offset 0x00000000
(II) RADEON(0): Will use 4096 kb for back buffer at offset 0x00408000
(II) RADEON(0): Will use 4096 kb for depth buffer at offset 0x00808000
(II) RADEON(0): Will use 58880 kb for textures at offset 0x00c08000
(II) RADEON(0): Will use 59872 kb for X Server offscreen at offset 0x04588000
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:05.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: drmOpenMinor returns 10
drmOpenByBusid: drmGetBusid reports pci:0000:01:05.0
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) RADEON(0): [drm] Using the DRM lock SAREA also for drawables.
(II) RADEON(0): [drm] framebuffer handle = 0xc0000000
(II) RADEON(0): [drm] added 1 reserved context for kernel
(II) RADEON(0): X context handle = 0x1
(II) RADEON(0): [drm] installed DRM signal handler
(==) RADEON(0): Using AGP 8x
(II) RADEON(0): [agp] Mode 0x1f00020a [AGP 0x1002/0x5833; Card 0x1002/0x5834 0x1043/0x8107]
(II) RADEON(0): [agp] 8192 kB allocated with handle 0x00000001
(II) RADEON(0): [agp] ring handle = 0xe0000000
(II) RADEON(0): [agp] Ring mapped at 0xb769a000
(II) RADEON(0): [agp] ring read ptr handle = 0xe0101000
(II) RADEON(0): [agp] Ring read ptr mapped at 0xb7699000
(II) RADEON(0): [agp] vertex/indirect buffers handle = 0xe0102000
(II) RADEON(0): [agp] Vertex/indirect buffers mapped at 0xaf42b000
(II) RADEON(0): [agp] GART texture map handle = 0xe0302000
(II) RADEON(0): [agp] GART Texture map mapped at 0xaef4b000
(II) RADEON(0): [drm] register handle = 0x2fb40000
(II) RADEON(0): [dri] Visual configs initialized
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x5fff5800 0x5fff5800
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(==) RADEON(0): Backing store disabled
(II) RADEON(0): [DRI] installation complete
(II) RADEON(0): [drm] Added 32 65536 byte vertex/indirect buffers
(II) RADEON(0): [drm] Mapped 32 vertex/indirect buffers
(II) RADEON(0): [drm] dma control initialized, using IRQ 16
(II) RADEON(0): [drm] Initialized kernel GART heap manager, 5111808
(WW) RADEON(0): DRI init changed memory map, adjusting ...
(WW) RADEON(0):   MC_FB_LOCATION  was: 0x5fff5800 is: 0x5fff5800
(WW) RADEON(0):   MC_AGP_LOCATION was: 0xffffffc0 is: 0xe07fe000
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x5fff5800 0x5fff5800
(II) RADEON(0):   MC_AGP_LOCATION  : 0xe07fe000
(II) RADEON(0): Direct rendering enabled
(II) RADEON(0): Render acceleration enabled for R200 type cards.
(II) RADEON(0): Setting EXA maxPitchBytes
(II) EXA(0): Offscreen pixmap area of 61308928 bytes
(II) EXA(0): Driver registered support for the following operations:
(II)         Solid
(II)         Copy
(II)         Composite (RENDER acceleration)
(II)         UploadToScreen
(II) RADEON(0): Acceleration enabled
(II) RADEON(0): DPMS enabled
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): No video input capabilities detected and no information is provided - disabling multimedia i2c
(II) Loading sub module "theatre_detect"
(II) LoadModule: "theatre_detect"
(II) Loading /usr/lib/xorg/modules/multimedia//theatre_detect_drv.so
(II) Module theatre_detect: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Video Driver, version 5.0
(II) RADEON(0): no multimedia table present, disabling Rage Theatre.
(II) RADEON(0): Set up overlay video
(II) RADEON(0): Set up textured video
disable TVDAC
disable FP2
disable TV
disable TVDAC
init memmap
init common
init crtc1
init pll1
freq: 65000000
best_freq: 64990769
best_feedback_div: 236
best_frac_feedback_div: 0
best_ref_div: 13
best_post_div: 4
restore memmap
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x5fff5800 0x5fff5800
(II) RADEON(0):   MC_AGP_LOCATION  : 0xe07fe000
restore common
restore crtc1
restore pll1
finished PLL1
set RMX
set TVDAC
enable TVDAC
disable FP2
(II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(--) RandR disabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) AIGLX: Screen 0 is not DRI2 capable
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:05.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: drmOpenMinor returns 11
drmOpenByBusid: drmGetBusid reports pci:0000:01:05.0
(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: enabled GLX_SGI_make_current_read
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: enabled GLX_texture_from_pixmap with driver support
(II) AIGLX: Loaded and initialized /usr/lib/dri/r200_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) RADEON(0): Setting screen physical size to 307 x 230
(II) config/hal: Adding input device ORTEK Smartpad Keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 2.2.5
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) ORTEK Smartpad Keyboard: always reports core events
(**) ORTEK Smartpad Keyboard: Device: "/dev/input/event4"
(II) ORTEK Smartpad Keyboard: Found 9 mouse buttons
(II) ORTEK Smartpad Keyboard: Found x and y relative axes
(II) ORTEK Smartpad Keyboard: Found scroll wheel(s)
(II) ORTEK Smartpad Keyboard: Found keys
(II) ORTEK Smartpad Keyboard: Configuring as mouse
(II) ORTEK Smartpad Keyboard: Configuring as keyboard
(**) ORTEK Smartpad Keyboard: YAxisMapping: buttons 4 and 5
(**) ORTEK Smartpad Keyboard: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "ORTEK Smartpad Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "gb"
(**) ORTEK Smartpad Keyboard: (accel) keeping acceleration scheme 1
(**) ORTEK Smartpad Keyboard: (accel) filter chain progression: 2.00
(**) ORTEK Smartpad Keyboard: (accel) filter stage 0: 20.00 ms
(**) ORTEK Smartpad Keyboard: (accel) set acceleration profile 0
(II) ORTEK Smartpad Keyboard: initialized for relative axes.
(II) config/hal: Adding input device A4Tech RF USB Receiver
(**) A4Tech RF USB Receiver: always reports core events
(**) A4Tech RF USB Receiver: Device: "/dev/input/event6"
(II) A4Tech RF USB Receiver: Found 12 mouse buttons
(II) A4Tech RF USB Receiver: Found x and y relative axes
(II) A4Tech RF USB Receiver: Found scroll wheel(s)
(II) A4Tech RF USB Receiver: Found keys
(II) A4Tech RF USB Receiver: Configuring as mouse
(II) A4Tech RF USB Receiver: Configuring as keyboard
(**) A4Tech RF USB Receiver: YAxisMapping: buttons 4 and 5
(**) A4Tech RF USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "A4Tech RF USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "gb"
(**) A4Tech RF USB Receiver: (accel) keeping acceleration scheme 1
(**) A4Tech RF USB Receiver: (accel) filter chain progression: 2.00
(**) A4Tech RF USB Receiver: (accel) filter stage 0: 20.00 ms
(**) A4Tech RF USB Receiver: (accel) set acceleration profile 0
(II) A4Tech RF USB Receiver: initialized for relative axes.
(II) config/hal: Adding input device A4Tech RF USB Receiver
(**) A4Tech RF USB Receiver: always reports core events
(**) A4Tech RF USB Receiver: Device: "/dev/input/event5"
(II) A4Tech RF USB Receiver: Found keys
(II) A4Tech RF USB Receiver: Configuring as keyboard
(II) XINPUT: Adding extended input device "A4Tech RF USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "gb"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "gb"
(II) config/hal: Adding input device ORTEK Smartpad Keyboard
(**) ORTEK Smartpad Keyboard: always reports core events
(**) ORTEK Smartpad Keyboard: Device: "/dev/input/event3"
(II) ORTEK Smartpad Keyboard: Found keys
(II) ORTEK Smartpad Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "ORTEK Smartpad Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "gb"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "gb"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
(II) RADEON(0): EDID vendor "PHL", prod id 2080
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
(II) RADEON(0): EDID vendor "PHL", prod id 2080
(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
(II) RADEON(0): EDID vendor "PHL", prod id 2080
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
(II) RADEON(0): EDID vendor "PHL", prod id 2080
(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
(II) RADEON(0): EDID vendor "PHL", prod id 2080
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
(II) RADEON(0): EDID vendor "PHL", prod id 2080
(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
(II) RADEON(0): EDID vendor "PHL", prod id 2080
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
(II) RADEON(0): EDID vendor "PHL", prod id 2080
(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Manufacturer: PHL  Model: 4650  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 71  vert.: 40
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.617 redY: 0.334   greenX: 0.283 greenY: 0.590
(II) RADEON(0): blueX: 0.143 blueY: 0.086   whiteX: 0.284 whiteY: 0.295
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 360  refresh: 85  vid: 55601
(II) RADEON(0): #1: hsize: 800  vsize 450  refresh: 85  vid: 55621
(II) RADEON(0): #2: hsize: 1024  vsize 576  refresh: 85  vid: 55649
(II) RADEON(0): #3: hsize: 1152  vsize 648  refresh: 75  vid: 53105
(II) RADEON(0): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.2 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 790 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 25.2 MHz   Image Size:  530 x 398 mm
(II) RADEON(0): h_active: 640  h_sync: 648  h_sync_end 744 h_blank_end 800 h_border: 8
(II) RADEON(0): v_active: 480  v_sync: 482  v_sync_end 484 v_blanking: 525 v_border: 8
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 27.0 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
(II) RADEON(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
(II) RADEON(0): Ranges: V min: 47 V max: 85 Hz, H min: 31 H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c504601010101
(II) RADEON(0): 	2b0f0103804728788a288e9e55489724
(II) RADEON(0): 	16484b256a0031d945d961d971cf81c0
(II) RADEON(0): 	010101010101a91a00a0500016303020
(II) RADEON(0): 	3700c48e21000018d60980a020e02d10
(II) RADEON(0): 	08602200128e210808188c0ad08a20e0
(II) RADEON(0): 	2d10103e9600c48e21000018000000fd
(II) RADEON(0): 	002f551f500e000a2020202020200104
(II) RADEON(0): 	02031a75470103040512931423090707
(II) RADEON(0): 	8301000065030c001000011d007251d0
(II) RADEON(0): 	1e206e285500c48e2100001e011d8018
(II) RADEON(0): 	711c1620582c2500c48e2100009e8c0a
(II) RADEON(0): 	d090204031200c405500c48e21000018
(II) RADEON(0): 	011d00bc52d01e20b8285540c48e2100
(II) RADEON(0): 	001e011d80d0721c1620102c2580c48e
(II) RADEON(0): 	2100009e000000ff0000000000000049
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: PHL  Model: 4650  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 71  vert.: 40
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.617 redY: 0.334   greenX: 0.283 greenY: 0.590
(II) RADEON(0): blueX: 0.143 blueY: 0.086   whiteX: 0.284 whiteY: 0.295
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 360  refresh: 85  vid: 55601
(II) RADEON(0): #1: hsize: 800  vsize 450  refresh: 85  vid: 55621
(II) RADEON(0): #2: hsize: 1024  vsize 576  refresh: 85  vid: 55649
(II) RADEON(0): #3: hsize: 1152  vsize 648  refresh: 75  vid: 53105
(II) RADEON(0): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.2 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 790 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 25.2 MHz   Image Size:  530 x 398 mm
(II) RADEON(0): h_active: 640  h_sync: 648  h_sync_end 744 h_blank_end 800 h_border: 8
(II) RADEON(0): v_active: 480  v_sync: 482  v_sync_end 484 v_blanking: 525 v_border: 8
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 27.0 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
(II) RADEON(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
(II) RADEON(0): Ranges: V min: 47 V max: 85 Hz, H min: 31 H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c504601010101
(II) RADEON(0): 	2b0f0103804728788a288e9e55489724
(II) RADEON(0): 	16484b256a0031d945d961d971cf81c0
(II) RADEON(0): 	010101010101a91a00a0500016303020
(II) RADEON(0): 	3700c48e21000018d60980a020e02d10
(II) RADEON(0): 	08602200128e210808188c0ad08a20e0
(II) RADEON(0): 	2d10103e9600c48e21000018000000fd
(II) RADEON(0): 	002f551f500e000a2020202020200104
(II) RADEON(0): 	02031a75470103040512931423090707
(II) RADEON(0): 	8301000065030c001000011d007251d0
(II) RADEON(0): 	1e206e285500c48e2100001e011d8018
(II) RADEON(0): 	711c1620582c2500c48e2100009e8c0a
(II) RADEON(0): 	d090204031200c405500c48e21000018
(II) RADEON(0): 	011d00bc52d01e20b8285540c48e2100
(II) RADEON(0): 	001e011d80d0721c1620102c2580c48e
(II) RADEON(0): 	2100009e000000ff0000000000000049
(II) RADEON(0): Panel infos found from DDC detailed: 1280x768
(II) RADEON(0): EDID vendor "PHL", prod id 18000
(II) RADEON(0): Not using mode "1280x768" (width too large for virtual size)
(II) RADEON(0): Not using mode "1152x648" (width too large for virtual size)
(II) RADEON(0): Not using mode "1280x720" (width too large for virtual size)
(II) RADEON(0): Printing probed modes for output DVI-0
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x576"x85.0   69.11  1024 1080 1184 1344  576 577 580 605 -hsync +vsync (51.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x450"x85.0   41.81  800 840 920 1040  450 451 454 473 -hsync +vsync (40.2 kHz)
(II) RADEON(0): Modeline "720x480"x59.9   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x60.0   25.18  640 648 744 800  480 482 484 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x360"x85.0   25.77  640 656 720 800  360 361 364 379 -hsync +vsync (32.2 kHz)
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
(II) RADEON(0): EDID vendor "PHL", prod id 2080
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
(II) RADEON(0): EDID vendor "PHL", prod id 2080
(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Manufacturer: PHL  Model: 4650  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 71  vert.: 40
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.617 redY: 0.334   greenX: 0.283 greenY: 0.590
(II) RADEON(0): blueX: 0.143 blueY: 0.086   whiteX: 0.284 whiteY: 0.295
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 360  refresh: 85  vid: 55601
(II) RADEON(0): #1: hsize: 800  vsize 450  refresh: 85  vid: 55621
(II) RADEON(0): #2: hsize: 1024  vsize 576  refresh: 85  vid: 55649
(II) RADEON(0): #3: hsize: 1152  vsize 648  refresh: 75  vid: 53105
(II) RADEON(0): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.2 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 790 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 25.2 MHz   Image Size:  530 x 398 mm
(II) RADEON(0): h_active: 640  h_sync: 648  h_sync_end 744 h_blank_end 800 h_border: 8
(II) RADEON(0): v_active: 480  v_sync: 482  v_sync_end 484 v_blanking: 525 v_border: 8
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 27.0 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
(II) RADEON(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
(II) RADEON(0): Ranges: V min: 47 V max: 85 Hz, H min: 31 H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c504601010101
(II) RADEON(0): 	2b0f0103804728788a288e9e55489724
(II) RADEON(0): 	16484b256a0031d945d961d971cf81c0
(II) RADEON(0): 	010101010101a91a00a0500016303020
(II) RADEON(0): 	3700c48e21000018d60980a020e02d10
(II) RADEON(0): 	08602200128e210808188c0ad08a20e0
(II) RADEON(0): 	2d10103e9600c48e21000018000000fd
(II) RADEON(0): 	002f551f500e000a2020202020200104
(II) RADEON(0): 	02031a75470103040512931423090707
(II) RADEON(0): 	8301000065030c001000011d007251d0
(II) RADEON(0): 	1e206e285500c48e2100001e011d8018
(II) RADEON(0): 	711c1620582c2500c48e2100009e8c0a
(II) RADEON(0): 	d090204031200c405500c48e21000018
(II) RADEON(0): 	011d00bc52d01e20b8285540c48e2100
(II) RADEON(0): 	001e011d80d0721c1620102c2580c48e
(II) RADEON(0): 	2100009e000000ff0000000000000049
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: PHL  Model: 4650  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 71  vert.: 40
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.617 redY: 0.334   greenX: 0.283 greenY: 0.590
(II) RADEON(0): blueX: 0.143 blueY: 0.086   whiteX: 0.284 whiteY: 0.295
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 360  refresh: 85  vid: 55601
(II) RADEON(0): #1: hsize: 800  vsize 450  refresh: 85  vid: 55621
(II) RADEON(0): #2: hsize: 1024  vsize 576  refresh: 85  vid: 55649
(II) RADEON(0): #3: hsize: 1152  vsize 648  refresh: 75  vid: 53105
(II) RADEON(0): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.2 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 790 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 25.2 MHz   Image Size:  530 x 398 mm
(II) RADEON(0): h_active: 640  h_sync: 648  h_sync_end 744 h_blank_end 800 h_border: 8
(II) RADEON(0): v_active: 480  v_sync: 482  v_sync_end 484 v_blanking: 525 v_border: 8
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 27.0 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
(II) RADEON(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
(II) RADEON(0): Ranges: V min: 47 V max: 85 Hz, H min: 31 H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c504601010101
(II) RADEON(0): 	2b0f0103804728788a288e9e55489724
(II) RADEON(0): 	16484b256a0031d945d961d971cf81c0
(II) RADEON(0): 	010101010101a91a00a0500016303020
(II) RADEON(0): 	3700c48e21000018d60980a020e02d10
(II) RADEON(0): 	08602200128e210808188c0ad08a20e0
(II) RADEON(0): 	2d10103e9600c48e21000018000000fd
(II) RADEON(0): 	002f551f500e000a2020202020200104
(II) RADEON(0): 	02031a75470103040512931423090707
(II) RADEON(0): 	8301000065030c001000011d007251d0
(II) RADEON(0): 	1e206e285500c48e2100001e011d8018
(II) RADEON(0): 	711c1620582c2500c48e2100009e8c0a
(II) RADEON(0): 	d090204031200c405500c48e21000018
(II) RADEON(0): 	011d00bc52d01e20b8285540c48e2100
(II) RADEON(0): 	001e011d80d0721c1620102c2580c48e
(II) RADEON(0): 	2100009e000000ff0000000000000049
(II) RADEON(0): EDID vendor "PHL", prod id 18000
(II) RADEON(0): Not using mode "1280x768" (width too large for virtual size)
(II) RADEON(0): Not using mode "1152x648" (width too large for virtual size)
(II) RADEON(0): Not using mode "1280x720" (width too large for virtual size)
(II) RADEON(0): Printing probed modes for output DVI-0
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x576"x85.0   69.11  1024 1080 1184 1344  576 577 580 605 -hsync +vsync (51.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x450"x85.0   41.81  800 840 920 1040  450 451 454 473 -hsync +vsync (40.2 kHz)
(II) RADEON(0): Modeline "720x480"x59.9   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x60.0   25.18  640 648 744 800  480 482 484 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x360"x85.0   25.77  640 656 720 800  360 361 364 379 -hsync +vsync (32.2 kHz)
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
(II) RADEON(0): EDID vendor "PHL", prod id 2080
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
(II) RADEON(0): EDID vendor "PHL", prod id 2080
(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Manufacturer: PHL  Model: 4650  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 71  vert.: 40
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.617 redY: 0.334   greenX: 0.283 greenY: 0.590
(II) RADEON(0): blueX: 0.143 blueY: 0.086   whiteX: 0.284 whiteY: 0.295
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 360  refresh: 85  vid: 55601
(II) RADEON(0): #1: hsize: 800  vsize 450  refresh: 85  vid: 55621
(II) RADEON(0): #2: hsize: 1024  vsize 576  refresh: 85  vid: 55649
(II) RADEON(0): #3: hsize: 1152  vsize 648  refresh: 75  vid: 53105
(II) RADEON(0): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.2 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 790 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 25.2 MHz   Image Size:  530 x 398 mm
(II) RADEON(0): h_active: 640  h_sync: 648  h_sync_end 744 h_blank_end 800 h_border: 8
(II) RADEON(0): v_active: 480  v_sync: 482  v_sync_end 484 v_blanking: 525 v_border: 8
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 27.0 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
(II) RADEON(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
(II) RADEON(0): Ranges: V min: 47 V max: 85 Hz, H min: 31 H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c504601010101
(II) RADEON(0): 	2b0f0103804728788a288e9e55489724
(II) RADEON(0): 	16484b256a0031d945d961d971cf81c0
(II) RADEON(0): 	010101010101a91a00a0500016303020
(II) RADEON(0): 	3700c48e21000018d60980a020e02d10
(II) RADEON(0): 	08602200128e210808188c0ad08a20e0
(II) RADEON(0): 	2d10103e9600c48e21000018000000fd
(II) RADEON(0): 	002f551f500e000a2020202020200104
(II) RADEON(0): 	02031a75470103040512931423090707
(II) RADEON(0): 	8301000065030c001000011d007251d0
(II) RADEON(0): 	1e206e285500c48e2100001e011d8018
(II) RADEON(0): 	711c1620582c2500c48e2100009e8c0a
(II) RADEON(0): 	d090204031200c405500c48e21000018
(II) RADEON(0): 	011d00bc52d01e20b8285540c48e2100
(II) RADEON(0): 	001e011d80d0721c1620102c2580c48e
(II) RADEON(0): 	2100009e000000ff0000000000000049
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: PHL  Model: 4650  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 71  vert.: 40
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.617 redY: 0.334   greenX: 0.283 greenY: 0.590
(II) RADEON(0): blueX: 0.143 blueY: 0.086   whiteX: 0.284 whiteY: 0.295
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 360  refresh: 85  vid: 55601
(II) RADEON(0): #1: hsize: 800  vsize 450  refresh: 85  vid: 55621
(II) RADEON(0): #2: hsize: 1024  vsize 576  refresh: 85  vid: 55649
(II) RADEON(0): #3: hsize: 1152  vsize 648  refresh: 75  vid: 53105
(II) RADEON(0): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.2 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 790 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 25.2 MHz   Image Size:  530 x 398 mm
(II) RADEON(0): h_active: 640  h_sync: 648  h_sync_end 744 h_blank_end 800 h_border: 8
(II) RADEON(0): v_active: 480  v_sync: 482  v_sync_end 484 v_blanking: 525 v_border: 8
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 27.0 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
(II) RADEON(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
(II) RADEON(0): Ranges: V min: 47 V max: 85 Hz, H min: 31 H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c504601010101
(II) RADEON(0): 	2b0f0103804728788a288e9e55489724
(II) RADEON(0): 	16484b256a0031d945d961d971cf81c0
(II) RADEON(0): 	010101010101a91a00a0500016303020
(II) RADEON(0): 	3700c48e21000018d60980a020e02d10
(II) RADEON(0): 	08602200128e210808188c0ad08a20e0
(II) RADEON(0): 	2d10103e9600c48e21000018000000fd
(II) RADEON(0): 	002f551f500e000a2020202020200104
(II) RADEON(0): 	02031a75470103040512931423090707
(II) RADEON(0): 	8301000065030c001000011d007251d0
(II) RADEON(0): 	1e206e285500c48e2100001e011d8018
(II) RADEON(0): 	711c1620582c2500c48e2100009e8c0a
(II) RADEON(0): 	d090204031200c405500c48e21000018
(II) RADEON(0): 	011d00bc52d01e20b8285540c48e2100
(II) RADEON(0): 	001e011d80d0721c1620102c2580c48e
(II) RADEON(0): 	2100009e000000ff0000000000000049
(II) RADEON(0): EDID vendor "PHL", prod id 18000
(II) RADEON(0): Not using mode "1280x768" (width too large for virtual size)
(II) RADEON(0): Not using mode "1152x648" (width too large for virtual size)
(II) RADEON(0): Not using mode "1280x720" (width too large for virtual size)
(II) RADEON(0): Printing probed modes for output DVI-0
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x576"x85.0   69.11  1024 1080 1184 1344  576 577 580 605 -hsync +vsync (51.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x450"x85.0   41.81  800 840 920 1040  450 451 454 473 -hsync +vsync (40.2 kHz)
(II) RADEON(0): Modeline "720x480"x59.9   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x60.0   25.18  640 648 744 800  480 482 484 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x360"x85.0   25.77  640 656 720 800  360 361 364 379 -hsync +vsync (32.2 kHz)
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
(II) RADEON(0): EDID vendor "PHL", prod id 2080
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
(II) RADEON(0): EDID vendor "PHL", prod id 2080
(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Manufacturer: PHL  Model: 4650  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 71  vert.: 40
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.617 redY: 0.334   greenX: 0.283 greenY: 0.590
(II) RADEON(0): blueX: 0.143 blueY: 0.086   whiteX: 0.284 whiteY: 0.295
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 360  refresh: 85  vid: 55601
(II) RADEON(0): #1: hsize: 800  vsize 450  refresh: 85  vid: 55621
(II) RADEON(0): #2: hsize: 1024  vsize 576  refresh: 85  vid: 55649
(II) RADEON(0): #3: hsize: 1152  vsize 648  refresh: 75  vid: 53105
(II) RADEON(0): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.2 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 790 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 25.2 MHz   Image Size:  530 x 398 mm
(II) RADEON(0): h_active: 640  h_sync: 648  h_sync_end 744 h_blank_end 800 h_border: 8
(II) RADEON(0): v_active: 480  v_sync: 482  v_sync_end 484 v_blanking: 525 v_border: 8
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 27.0 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
(II) RADEON(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
(II) RADEON(0): Ranges: V min: 47 V max: 85 Hz, H min: 31 H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c504601010101
(II) RADEON(0): 	2b0f0103804728788a288e9e55489724
(II) RADEON(0): 	16484b256a0031d945d961d971cf81c0
(II) RADEON(0): 	010101010101a91a00a0500016303020
(II) RADEON(0): 	3700c48e21000018d60980a020e02d10
(II) RADEON(0): 	08602200128e210808188c0ad08a20e0
(II) RADEON(0): 	2d10103e9600c48e21000018000000fd
(II) RADEON(0): 	002f551f500e000a2020202020200104
(II) RADEON(0): 	02031a75470103040512931423090707
(II) RADEON(0): 	8301000065030c001000011d007251d0
(II) RADEON(0): 	1e206e285500c48e2100001e011d8018
(II) RADEON(0): 	711c1620582c2500c48e2100009e8c0a
(II) RADEON(0): 	d090204031200c405500c48e21000018
(II) RADEON(0): 	011d00bc52d01e20b8285540c48e2100
(II) RADEON(0): 	001e011d80d0721c1620102c2580c48e
(II) RADEON(0): 	2100009e000000ff0000000000000049
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: PHL  Model: 4650  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 71  vert.: 40
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.617 redY: 0.334   greenX: 0.283 greenY: 0.590
(II) RADEON(0): blueX: 0.143 blueY: 0.086   whiteX: 0.284 whiteY: 0.295
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 360  refresh: 85  vid: 55601
(II) RADEON(0): #1: hsize: 800  vsize 450  refresh: 85  vid: 55621
(II) RADEON(0): #2: hsize: 1024  vsize 576  refresh: 85  vid: 55649
(II) RADEON(0): #3: hsize: 1152  vsize 648  refresh: 75  vid: 53105
(II) RADEON(0): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.2 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 790 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 25.2 MHz   Image Size:  530 x 398 mm
(II) RADEON(0): h_active: 640  h_sync: 648  h_sync_end 744 h_blank_end 800 h_border: 8
(II) RADEON(0): v_active: 480  v_sync: 482  v_sync_end 484 v_blanking: 525 v_border: 8
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 27.0 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
(II) RADEON(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
(II) RADEON(0): Ranges: V min: 47 V max: 85 Hz, H min: 31 H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c504601010101
(II) RADEON(0): 	2b0f0103804728788a288e9e55489724
(II) RADEON(0): 	16484b256a0031d945d961d971cf81c0
(II) RADEON(0): 	010101010101a91a00a0500016303020
(II) RADEON(0): 	3700c48e21000018d60980a020e02d10
(II) RADEON(0): 	08602200128e210808188c0ad08a20e0
(II) RADEON(0): 	2d10103e9600c48e21000018000000fd
(II) RADEON(0): 	002f551f500e000a2020202020200104
(II) RADEON(0): 	02031a75470103040512931423090707
(II) RADEON(0): 	8301000065030c001000011d007251d0
(II) RADEON(0): 	1e206e285500c48e2100001e011d8018
(II) RADEON(0): 	711c1620582c2500c48e2100009e8c0a
(II) RADEON(0): 	d090204031200c405500c48e21000018
(II) RADEON(0): 	011d00bc52d01e20b8285540c48e2100
(II) RADEON(0): 	001e011d80d0721c1620102c2580c48e
(II) RADEON(0): 	2100009e000000ff0000000000000049
(II) RADEON(0): EDID vendor "PHL", prod id 18000
(II) RADEON(0): Not using mode "1280x768" (width too large for virtual size)
(II) RADEON(0): Not using mode "1152x648" (width too large for virtual size)
(II) RADEON(0): Not using mode "1280x720" (width too large for virtual size)
(II) RADEON(0): Printing probed modes for output DVI-0
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x576"x85.0   69.11  1024 1080 1184 1344  576 577 580 605 -hsync +vsync (51.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x450"x85.0   41.81  800 840 920 1040  450 451 454 473 -hsync +vsync (40.2 kHz)
(II) RADEON(0): Modeline "720x480"x59.9   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x60.0   25.18  640 648 744 800  480 482 484 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x360"x85.0   25.77  640 656 720 800  360 361 364 379 -hsync +vsync (32.2 kHz)
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
(II) RADEON(0): EDID vendor "PHL", prod id 2080
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
(II) RADEON(0): EDID vendor "PHL", prod id 2080
(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Manufacturer: PHL  Model: 4650  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 71  vert.: 40
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.617 redY: 0.334   greenX: 0.283 greenY: 0.590
(II) RADEON(0): blueX: 0.143 blueY: 0.086   whiteX: 0.284 whiteY: 0.295
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 360  refresh: 85  vid: 55601
(II) RADEON(0): #1: hsize: 800  vsize 450  refresh: 85  vid: 55621
(II) RADEON(0): #2: hsize: 1024  vsize 576  refresh: 85  vid: 55649
(II) RADEON(0): #3: hsize: 1152  vsize 648  refresh: 75  vid: 53105
(II) RADEON(0): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.2 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 790 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 25.2 MHz   Image Size:  530 x 398 mm
(II) RADEON(0): h_active: 640  h_sync: 648  h_sync_end 744 h_blank_end 800 h_border: 8
(II) RADEON(0): v_active: 480  v_sync: 482  v_sync_end 484 v_blanking: 525 v_border: 8
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 27.0 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
(II) RADEON(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
(II) RADEON(0): Ranges: V min: 47 V max: 85 Hz, H min: 31 H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c504601010101
(II) RADEON(0): 	2b0f0103804728788a288e9e55489724
(II) RADEON(0): 	16484b256a0031d945d961d971cf81c0
(II) RADEON(0): 	010101010101a91a00a0500016303020
(II) RADEON(0): 	3700c48e21000018d60980a020e02d10
(II) RADEON(0): 	08602200128e210808188c0ad08a20e0
(II) RADEON(0): 	2d10103e9600c48e21000018000000fd
(II) RADEON(0): 	002f551f500e000a2020202020200104
(II) RADEON(0): 	02031a75470103040512931423090707
(II) RADEON(0): 	8301000065030c001000011d007251d0
(II) RADEON(0): 	1e206e285500c48e2100001e011d8018
(II) RADEON(0): 	711c1620582c2500c48e2100009e8c0a
(II) RADEON(0): 	d090204031200c405500c48e21000018
(II) RADEON(0): 	011d00bc52d01e20b8285540c48e2100
(II) RADEON(0): 	001e011d80d0721c1620102c2580c48e
(II) RADEON(0): 	2100009e000000ff0000000000000049
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: PHL  Model: 4650  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 71  vert.: 40
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.617 redY: 0.334   greenX: 0.283 greenY: 0.590
(II) RADEON(0): blueX: 0.143 blueY: 0.086   whiteX: 0.284 whiteY: 0.295
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 360  refresh: 85  vid: 55601
(II) RADEON(0): #1: hsize: 800  vsize 450  refresh: 85  vid: 55621
(II) RADEON(0): #2: hsize: 1024  vsize 576  refresh: 85  vid: 55649
(II) RADEON(0): #3: hsize: 1152  vsize 648  refresh: 75  vid: 53105
(II) RADEON(0): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.2 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 790 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 25.2 MHz   Image Size:  530 x 398 mm
(II) RADEON(0): h_active: 640  h_sync: 648  h_sync_end 744 h_blank_end 800 h_border: 8
(II) RADEON(0): v_active: 480  v_sync: 482  v_sync_end 484 v_blanking: 525 v_border: 8
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 27.0 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
(II) RADEON(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
(II) RADEON(0): Ranges: V min: 47 V max: 85 Hz, H min: 31 H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c504601010101
(II) RADEON(0): 	2b0f0103804728788a288e9e55489724
(II) RADEON(0): 	16484b256a0031d945d961d971cf81c0
(II) RADEON(0): 	010101010101a91a00a0500016303020
(II) RADEON(0): 	3700c48e21000018d60980a020e02d10
(II) RADEON(0): 	08602200128e210808188c0ad08a20e0
(II) RADEON(0): 	2d10103e9600c48e21000018000000fd
(II) RADEON(0): 	002f551f500e000a2020202020200104
(II) RADEON(0): 	02031a75470103040512931423090707
(II) RADEON(0): 	8301000065030c001000011d007251d0
(II) RADEON(0): 	1e206e285500c48e2100001e011d8018
(II) RADEON(0): 	711c1620582c2500c48e2100009e8c0a
(II) RADEON(0): 	d090204031200c405500c48e21000018
(II) RADEON(0): 	011d00bc52d01e20b8285540c48e2100
(II) RADEON(0): 	001e011d80d0721c1620102c2580c48e
(II) RADEON(0): 	2100009e000000ff0000000000000049
(II) RADEON(0): EDID vendor "PHL", prod id 18000
(II) RADEON(0): Not using mode "1280x768" (width too large for virtual size)
(II) RADEON(0): Not using mode "1152x648" (width too large for virtual size)
(II) RADEON(0): Not using mode "1280x720" (width too large for virtual size)
(II) RADEON(0): Printing probed modes for output DVI-0
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x576"x85.0   69.11  1024 1080 1184 1344  576 577 580 605 -hsync +vsync (51.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x450"x85.0   41.81  800 840 920 1040  450 451 454 473 -hsync +vsync (40.2 kHz)
(II) RADEON(0): Modeline "720x480"x59.9   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x60.0   25.18  640 648 744 800  480 482 484 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x360"x85.0   25.77  640 656 720 800  360 361 364 379 -hsync +vsync (32.2 kHz)
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
(II) RADEON(0): EDID vendor "PHL", prod id 2080
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
(II) RADEON(0): EDID vendor "PHL", prod id 2080
(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Manufacturer: PHL  Model: 4650  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 71  vert.: 40
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.617 redY: 0.334   greenX: 0.283 greenY: 0.590
(II) RADEON(0): blueX: 0.143 blueY: 0.086   whiteX: 0.284 whiteY: 0.295
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 360  refresh: 85  vid: 55601
(II) RADEON(0): #1: hsize: 800  vsize 450  refresh: 85  vid: 55621
(II) RADEON(0): #2: hsize: 1024  vsize 576  refresh: 85  vid: 55649
(II) RADEON(0): #3: hsize: 1152  vsize 648  refresh: 75  vid: 53105
(II) RADEON(0): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.2 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 790 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 25.2 MHz   Image Size:  530 x 398 mm
(II) RADEON(0): h_active: 640  h_sync: 648  h_sync_end 744 h_blank_end 800 h_border: 8
(II) RADEON(0): v_active: 480  v_sync: 482  v_sync_end 484 v_blanking: 525 v_border: 8
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 27.0 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
(II) RADEON(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
(II) RADEON(0): Ranges: V min: 47 V max: 85 Hz, H min: 31 H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c504601010101
(II) RADEON(0): 	2b0f0103804728788a288e9e55489724
(II) RADEON(0): 	16484b256a0031d945d961d971cf81c0
(II) RADEON(0): 	010101010101a91a00a0500016303020
(II) RADEON(0): 	3700c48e21000018d60980a020e02d10
(II) RADEON(0): 	08602200128e210808188c0ad08a20e0
(II) RADEON(0): 	2d10103e9600c48e21000018000000fd
(II) RADEON(0): 	002f551f500e000a2020202020200104
(II) RADEON(0): 	02031a75470103040512931423090707
(II) RADEON(0): 	8301000065030c001000011d007251d0
(II) RADEON(0): 	1e206e285500c48e2100001e011d8018
(II) RADEON(0): 	711c1620582c2500c48e2100009e8c0a
(II) RADEON(0): 	d090204031200c405500c48e21000018
(II) RADEON(0): 	011d00bc52d01e20b8285540c48e2100
(II) RADEON(0): 	001e011d80d0721c1620102c2580c48e
(II) RADEON(0): 	2100009e000000ff0000000000000049
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: PHL  Model: 4650  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 71  vert.: 40
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.617 redY: 0.334   greenX: 0.283 greenY: 0.590
(II) RADEON(0): blueX: 0.143 blueY: 0.086   whiteX: 0.284 whiteY: 0.295
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 360  refresh: 85  vid: 55601
(II) RADEON(0): #1: hsize: 800  vsize 450  refresh: 85  vid: 55621
(II) RADEON(0): #2: hsize: 1024  vsize 576  refresh: 85  vid: 55649
(II) RADEON(0): #3: hsize: 1152  vsize 648  refresh: 75  vid: 53105
(II) RADEON(0): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.2 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 790 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 25.2 MHz   Image Size:  530 x 398 mm
(II) RADEON(0): h_active: 640  h_sync: 648  h_sync_end 744 h_blank_end 800 h_border: 8
(II) RADEON(0): v_active: 480  v_sync: 482  v_sync_end 484 v_blanking: 525 v_border: 8
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 27.0 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
(II) RADEON(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
(II) RADEON(0): Ranges: V min: 47 V max: 85 Hz, H min: 31 H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c504601010101
(II) RADEON(0): 	2b0f0103804728788a288e9e55489724
(II) RADEON(0): 	16484b256a0031d945d961d971cf81c0
(II) RADEON(0): 	010101010101a91a00a0500016303020
(II) RADEON(0): 	3700c48e21000018d60980a020e02d10
(II) RADEON(0): 	08602200128e210808188c0ad08a20e0
(II) RADEON(0): 	2d10103e9600c48e21000018000000fd
(II) RADEON(0): 	002f551f500e000a2020202020200104
(II) RADEON(0): 	02031a75470103040512931423090707
(II) RADEON(0): 	8301000065030c001000011d007251d0
(II) RADEON(0): 	1e206e285500c48e2100001e011d8018
(II) RADEON(0): 	711c1620582c2500c48e2100009e8c0a
(II) RADEON(0): 	d090204031200c405500c48e21000018
(II) RADEON(0): 	011d00bc52d01e20b8285540c48e2100
(II) RADEON(0): 	001e011d80d0721c1620102c2580c48e
(II) RADEON(0): 	2100009e000000ff0000000000000049
(II) RADEON(0): EDID vendor "PHL", prod id 18000
(II) RADEON(0): Not using mode "1280x768" (width too large for virtual size)
(II) RADEON(0): Not using mode "1152x648" (width too large for virtual size)
(II) RADEON(0): Not using mode "1280x720" (width too large for virtual size)
(II) RADEON(0): Printing probed modes for output DVI-0
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x576"x85.0   69.11  1024 1080 1184 1344  576 577 580 605 -hsync +vsync (51.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x450"x85.0   41.81  800 840 920 1040  450 451 454 473 -hsync +vsync (40.2 kHz)
(II) RADEON(0): Modeline "720x480"x59.9   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x60.0   25.18  640 648 744 800  480 482 484 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x360"x85.0   25.77  640 656 720 800  360 361 364 379 -hsync +vsync (32.2 kHz)
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
(II) RADEON(0): EDID vendor "PHL", prod id 2080
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
(II) RADEON(0): EDID vendor "PHL", prod id 2080
(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Manufacturer: PHL  Model: 4650  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 71  vert.: 40
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.617 redY: 0.334   greenX: 0.283 greenY: 0.590
(II) RADEON(0): blueX: 0.143 blueY: 0.086   whiteX: 0.284 whiteY: 0.295
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 360  refresh: 85  vid: 55601
(II) RADEON(0): #1: hsize: 800  vsize 450  refresh: 85  vid: 55621
(II) RADEON(0): #2: hsize: 1024  vsize 576  refresh: 85  vid: 55649
(II) RADEON(0): #3: hsize: 1152  vsize 648  refresh: 75  vid: 53105
(II) RADEON(0): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.2 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 790 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 25.2 MHz   Image Size:  530 x 398 mm
(II) RADEON(0): h_active: 640  h_sync: 648  h_sync_end 744 h_blank_end 800 h_border: 8
(II) RADEON(0): v_active: 480  v_sync: 482  v_sync_end 484 v_blanking: 525 v_border: 8
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 27.0 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
(II) RADEON(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
(II) RADEON(0): Ranges: V min: 47 V max: 85 Hz, H min: 31 H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c504601010101
(II) RADEON(0): 	2b0f0103804728788a288e9e55489724
(II) RADEON(0): 	16484b256a0031d945d961d971cf81c0
(II) RADEON(0): 	010101010101a91a00a0500016303020
(II) RADEON(0): 	3700c48e21000018d60980a020e02d10
(II) RADEON(0): 	08602200128e210808188c0ad08a20e0
(II) RADEON(0): 	2d10103e9600c48e21000018000000fd
(II) RADEON(0): 	002f551f500e000a2020202020200104
(II) RADEON(0): 	02031a75470103040512931423090707
(II) RADEON(0): 	8301000065030c001000011d007251d0
(II) RADEON(0): 	1e206e285500c48e2100001e011d8018
(II) RADEON(0): 	711c1620582c2500c48e2100009e8c0a
(II) RADEON(0): 	d090204031200c405500c48e21000018
(II) RADEON(0): 	011d00bc52d01e20b8285540c48e2100
(II) RADEON(0): 	001e011d80d0721c1620102c2580c48e
(II) RADEON(0): 	2100009e000000ff0000000000000049
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: PHL  Model: 4650  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 71  vert.: 40
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.617 redY: 0.334   greenX: 0.283 greenY: 0.590
(II) RADEON(0): blueX: 0.143 blueY: 0.086   whiteX: 0.284 whiteY: 0.295
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 360  refresh: 85  vid: 55601
(II) RADEON(0): #1: hsize: 800  vsize 450  refresh: 85  vid: 55621
(II) RADEON(0): #2: hsize: 1024  vsize 576  refresh: 85  vid: 55649
(II) RADEON(0): #3: hsize: 1152  vsize 648  refresh: 75  vid: 53105
(II) RADEON(0): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.2 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 790 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 25.2 MHz   Image Size:  530 x 398 mm
(II) RADEON(0): h_active: 640  h_sync: 648  h_sync_end 744 h_blank_end 800 h_border: 8
(II) RADEON(0): v_active: 480  v_sync: 482  v_sync_end 484 v_blanking: 525 v_border: 8
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 27.0 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
(II) RADEON(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
(II) RADEON(0): Ranges: V min: 47 V max: 85 Hz, H min: 31 H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c504601010101
(II) RADEON(0): 	2b0f0103804728788a288e9e55489724
(II) RADEON(0): 	16484b256a0031d945d961d971cf81c0
(II) RADEON(0): 	010101010101a91a00a0500016303020
(II) RADEON(0): 	3700c48e21000018d60980a020e02d10
(II) RADEON(0): 	08602200128e210808188c0ad08a20e0
(II) RADEON(0): 	2d10103e9600c48e21000018000000fd
(II) RADEON(0): 	002f551f500e000a2020202020200104
(II) RADEON(0): 	02031a75470103040512931423090707
(II) RADEON(0): 	8301000065030c001000011d007251d0
(II) RADEON(0): 	1e206e285500c48e2100001e011d8018
(II) RADEON(0): 	711c1620582c2500c48e2100009e8c0a
(II) RADEON(0): 	d090204031200c405500c48e21000018
(II) RADEON(0): 	011d00bc52d01e20b8285540c48e2100
(II) RADEON(0): 	001e011d80d0721c1620102c2580c48e
(II) RADEON(0): 	2100009e000000ff0000000000000049
(II) RADEON(0): EDID vendor "PHL", prod id 18000
(II) RADEON(0): Not using mode "1280x768" (width too large for virtual size)
(II) RADEON(0): Not using mode "1152x648" (width too large for virtual size)
(II) RADEON(0): Not using mode "1280x720" (width too large for virtual size)
(II) RADEON(0): Printing probed modes for output DVI-0
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x576"x85.0   69.11  1024 1080 1184 1344  576 577 580 605 -hsync +vsync (51.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x450"x85.0   41.81  800 840 920 1040  450 451 454 473 -hsync +vsync (40.2 kHz)
(II) RADEON(0): Modeline "720x480"x59.9   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x60.0   25.18  640 648 744 800  480 482 484 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x360"x85.0   25.77  640 656 720 800  360 361 364 379 -hsync +vsync (32.2 kHz)
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
disable TVDAC
disable FP2
init memmap
init common
init crtc2
init pll2
freq: 65000000
best_freq: 64990769
best_feedback_div: 236
best_frac_feedback_div: 0
best_ref_div: 13
best_post_div: 4
restore memmap
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x5fff5800 0x5fff5800
(II) RADEON(0):   MC_AGP_LOCATION  : 0xe07fe000
restore common
restore crtc2
restore pll2
finished PLL2
set FP2
enable TVDAC
enable FP2
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
(II) RADEON(0): EDID vendor "PHL", prod id 2080
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
(II) RADEON(0): EDID vendor "PHL", prod id 2080
(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Manufacturer: PHL  Model: 4650  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 71  vert.: 40
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.617 redY: 0.334   greenX: 0.283 greenY: 0.590
(II) RADEON(0): blueX: 0.143 blueY: 0.086   whiteX: 0.284 whiteY: 0.295
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 360  refresh: 85  vid: 55601
(II) RADEON(0): #1: hsize: 800  vsize 450  refresh: 85  vid: 55621
(II) RADEON(0): #2: hsize: 1024  vsize 576  refresh: 85  vid: 55649
(II) RADEON(0): #3: hsize: 1152  vsize 648  refresh: 75  vid: 53105
(II) RADEON(0): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.2 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 790 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 25.2 MHz   Image Size:  530 x 398 mm
(II) RADEON(0): h_active: 640  h_sync: 648  h_sync_end 744 h_blank_end 800 h_border: 8
(II) RADEON(0): v_active: 480  v_sync: 482  v_sync_end 484 v_blanking: 525 v_border: 8
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 27.0 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
(II) RADEON(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
(II) RADEON(0): Ranges: V min: 47 V max: 85 Hz, H min: 31 H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c504601010101
(II) RADEON(0): 	2b0f0103804728788a288e9e55489724
(II) RADEON(0): 	16484b256a0031d945d961d971cf81c0
(II) RADEON(0): 	010101010101a91a00a0500016303020
(II) RADEON(0): 	3700c48e21000018d60980a020e02d10
(II) RADEON(0): 	08602200128e210808188c0ad08a20e0
(II) RADEON(0): 	2d10103e9600c48e21000018000000fd
(II) RADEON(0): 	002f551f500e000a2020202020200104
(II) RADEON(0): 	02031a75470103040512931423090707
(II) RADEON(0): 	8301000065030c001000011d007251d0
(II) RADEON(0): 	1e206e285500c48e2100001e011d8018
(II) RADEON(0): 	711c1620582c2500c48e2100009e8c0a
(II) RADEON(0): 	d090204031200c405500c48e21000018
(II) RADEON(0): 	011d00bc52d01e20b8285540c48e2100
(II) RADEON(0): 	001e011d80d0721c1620102c2580c48e
(II) RADEON(0): 	2100009e000000ff0000000000000049
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: PHL  Model: 4650  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 71  vert.: 40
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.617 redY: 0.334   greenX: 0.283 greenY: 0.590
(II) RADEON(0): blueX: 0.143 blueY: 0.086   whiteX: 0.284 whiteY: 0.295
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 360  refresh: 85  vid: 55601
(II) RADEON(0): #1: hsize: 800  vsize 450  refresh: 85  vid: 55621
(II) RADEON(0): #2: hsize: 1024  vsize 576  refresh: 85  vid: 55649
(II) RADEON(0): #3: hsize: 1152  vsize 648  refresh: 75  vid: 53105
(II) RADEON(0): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.2 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 790 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 25.2 MHz   Image Size:  530 x 398 mm
(II) RADEON(0): h_active: 640  h_sync: 648  h_sync_end 744 h_blank_end 800 h_border: 8
(II) RADEON(0): v_active: 480  v_sync: 482  v_sync_end 484 v_blanking: 525 v_border: 8
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 27.0 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
(II) RADEON(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
(II) RADEON(0): Ranges: V min: 47 V max: 85 Hz, H min: 31 H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c504601010101
(II) RADEON(0): 	2b0f0103804728788a288e9e55489724
(II) RADEON(0): 	16484b256a0031d945d961d971cf81c0
(II) RADEON(0): 	010101010101a91a00a0500016303020
(II) RADEON(0): 	3700c48e21000018d60980a020e02d10
(II) RADEON(0): 	08602200128e210808188c0ad08a20e0
(II) RADEON(0): 	2d10103e9600c48e21000018000000fd
(II) RADEON(0): 	002f551f500e000a2020202020200104
(II) RADEON(0): 	02031a75470103040512931423090707
(II) RADEON(0): 	8301000065030c001000011d007251d0
(II) RADEON(0): 	1e206e285500c48e2100001e011d8018
(II) RADEON(0): 	711c1620582c2500c48e2100009e8c0a
(II) RADEON(0): 	d090204031200c405500c48e21000018
(II) RADEON(0): 	011d00bc52d01e20b8285540c48e2100
(II) RADEON(0): 	001e011d80d0721c1620102c2580c48e
(II) RADEON(0): 	2100009e000000ff0000000000000049
(II) RADEON(0): EDID vendor "PHL", prod id 18000
(II) RADEON(0): Not using mode "1280x768" (width too large for virtual size)
(II) RADEON(0): Not using mode "1152x648" (width too large for virtual size)
(II) RADEON(0): Not using mode "1280x720" (width too large for virtual size)
(II) RADEON(0): Printing probed modes for output DVI-0
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x576"x85.0   69.11  1024 1080 1184 1344  576 577 580 605 -hsync +vsync (51.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x450"x85.0   41.81  800 840 920 1040  450 451 454 473 -hsync +vsync (40.2 kHz)
(II) RADEON(0): Modeline "720x480"x59.9   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x60.0   25.18  640 648 744 800  480 482 484 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x360"x85.0   25.77  640 656 720 800  360 361 364 379 -hsync +vsync (32.2 kHz)
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
(II) RADEON(0): EDID vendor "PHL", prod id 2080
(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Manufacturer: PHL  Model: 4650  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 71  vert.: 40
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.617 redY: 0.334   greenX: 0.283 greenY: 0.590
(II) RADEON(0): blueX: 0.143 blueY: 0.086   whiteX: 0.284 whiteY: 0.295
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 360  refresh: 85  vid: 55601
(II) RADEON(0): #1: hsize: 800  vsize 450  refresh: 85  vid: 55621
(II) RADEON(0): #2: hsize: 1024  vsize 576  refresh: 85  vid: 55649
(II) RADEON(0): #3: hsize: 1152  vsize 648  refresh: 75  vid: 53105
(II) RADEON(0): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.2 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 790 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 25.2 MHz   Image Size:  530 x 398 mm
(II) RADEON(0): h_active: 640  h_sync: 648  h_sync_end 744 h_blank_end 800 h_border: 8
(II) RADEON(0): v_active: 480  v_sync: 482  v_sync_end 484 v_blanking: 525 v_border: 8
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 27.0 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
(II) RADEON(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
(II) RADEON(0): Ranges: V min: 47 V max: 85 Hz, H min: 31 H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c504601010101
(II) RADEON(0): 	2b0f0103804728788a288e9e55489724
(II) RADEON(0): 	16484b256a0031d945d961d971cf81c0
(II) RADEON(0): 	010101010101a91a00a0500016303020
(II) RADEON(0): 	3700c48e21000018d60980a020e02d10
(II) RADEON(0): 	08602200128e210808188c0ad08a20e0
(II) RADEON(0): 	2d10103e9600c48e21000018000000fd
(II) RADEON(0): 	002f551f500e000a2020202020200104
(II) RADEON(0): 	02031a75470103040512931423090707
(II) RADEON(0): 	8301000065030c001000011d007251d0
(II) RADEON(0): 	1e206e285500c48e2100001e011d8018
(II) RADEON(0): 	711c1620582c2500c48e2100009e8c0a
(II) RADEON(0): 	d090204031200c405500c48e21000018
(II) RADEON(0): 	011d00bc52d01e20b8285540c48e2100
(II) RADEON(0): 	001e011d80d0721c1620102c2580c48e
(II) RADEON(0): 	2100009e000000ff0000000000000049
(II) RADEON(0): EDID vendor "PHL", prod id 18000
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x768"x0.0   68.25  1280 1328 1360 1440  768 771 778 790 -hsync -vsync (47.4 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 648 744 800  480 482 484 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "640x360"x85.0   25.77  640 656 720 800  360 361 364 379 -hsync +vsync (32.2 kHz)
(II) RADEON(0): Modeline "800x450"x85.0   41.81  800 840 920 1040  450 451 454 473 -hsync +vsync (40.2 kHz)
(II) RADEON(0): Modeline "1024x576"x85.0   69.11  1024 1080 1184 1344  576 577 580 605 -hsync +vsync (51.4 kHz)
(II) RADEON(0): Modeline "1152x648"x75.0   77.18  1152 1216 1336 1520  648 649 652 677 -hsync +vsync (50.8 kHz)
(II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: PHL  Model: 4650  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 71  vert.: 40
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.617 redY: 0.334   greenX: 0.283 greenY: 0.590
(II) RADEON(0): blueX: 0.143 blueY: 0.086   whiteX: 0.284 whiteY: 0.295
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 360  refresh: 85  vid: 55601
(II) RADEON(0): #1: hsize: 800  vsize 450  refresh: 85  vid: 55621
(II) RADEON(0): #2: hsize: 1024  vsize 576  refresh: 85  vid: 55649
(II) RADEON(0): #3: hsize: 1152  vsize 648  refresh: 75  vid: 53105
(II) RADEON(0): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.2 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 790 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 25.2 MHz   Image Size:  530 x 398 mm
(II) RADEON(0): h_active: 640  h_sync: 648  h_sync_end 744 h_blank_end 800 h_border: 8
(II) RADEON(0): v_active: 480  v_sync: 482  v_sync_end 484 v_blanking: 525 v_border: 8
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 27.0 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
(II) RADEON(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
(II) RADEON(0): Ranges: V min: 47 V max: 85 Hz, H min: 31 H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c504601010101
(II) RADEON(0): 	2b0f0103804728788a288e9e55489724
(II) RADEON(0): 	16484b256a0031d945d961d971cf81c0
(II) RADEON(0): 	010101010101a91a00a0500016303020
(II) RADEON(0): 	3700c48e21000018d60980a020e02d10
(II) RADEON(0): 	08602200128e210808188c0ad08a20e0
(II) RADEON(0): 	2d10103e9600c48e21000018000000fd
(II) RADEON(0): 	002f551f500e000a2020202020200104
(II) RADEON(0): 	02031a75470103040512931423090707
(II) RADEON(0): 	8301000065030c001000011d007251d0
(II) RADEON(0): 	1e206e285500c48e2100001e011d8018
(II) RADEON(0): 	711c1620582c2500c48e2100009e8c0a
(II) RADEON(0): 	d090204031200c405500c48e21000018
(II) RADEON(0): 	011d00bc52d01e20b8285540c48e2100
(II) RADEON(0): 	001e011d80d0721c1620102c2580c48e
(II) RADEON(0): 	2100009e000000ff0000000000000049
(II) RADEON(0): EDID vendor "PHL", prod id 18000
(II) RADEON(0): Not using mode "1280x768" (width too large for virtual size)
(II) RADEON(0): Not using mode "1152x648" (width too large for virtual size)
(II) RADEON(0): Not using mode "1280x720" (width too large for virtual size)
(II) RADEON(0): Printing probed modes for output DVI-0
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x576"x85.0   69.11  1024 1080 1184 1344  576 577 580 605 -hsync +vsync (51.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x450"x85.0   41.81  800 840 920 1040  450 451 454 473 -hsync +vsync (40.2 kHz)
(II) RADEON(0): Modeline "720x480"x59.9   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x60.0   25.18  640 648 744 800  480 482 484 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x360"x85.0   25.77  640 656 720 800  360 361 364 379 -hsync +vsync (32.2 kHz)
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
(II) RADEON(0): EDID vendor "PHL", prod id 2080
(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Manufacturer: PHL  Model: 4650  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 71  vert.: 40
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.617 redY: 0.334   greenX: 0.283 greenY: 0.590
(II) RADEON(0): blueX: 0.143 blueY: 0.086   whiteX: 0.284 whiteY: 0.295
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 360  refresh: 85  vid: 55601
(II) RADEON(0): #1: hsize: 800  vsize 450  refresh: 85  vid: 55621
(II) RADEON(0): #2: hsize: 1024  vsize 576  refresh: 85  vid: 55649
(II) RADEON(0): #3: hsize: 1152  vsize 648  refresh: 75  vid: 53105
(II) RADEON(0): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.2 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 790 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 25.2 MHz   Image Size:  530 x 398 mm
(II) RADEON(0): h_active: 640  h_sync: 648  h_sync_end 744 h_blank_end 800 h_border: 8
(II) RADEON(0): v_active: 480  v_sync: 482  v_sync_end 484 v_blanking: 525 v_border: 8
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 27.0 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
(II) RADEON(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
(II) RADEON(0): Ranges: V min: 47 V max: 85 Hz, H min: 31 H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c504601010101
(II) RADEON(0): 	2b0f0103804728788a288e9e55489724
(II) RADEON(0): 	16484b256a0031d945d961d971cf81c0
(II) RADEON(0): 	010101010101a91a00a0500016303020
(II) RADEON(0): 	3700c48e21000018d60980a020e02d10
(II) RADEON(0): 	08602200128e210808188c0ad08a20e0
(II) RADEON(0): 	2d10103e9600c48e21000018000000fd
(II) RADEON(0): 	002f551f500e000a2020202020200104
(II) RADEON(0): 	02031a75470103040512931423090707
(II) RADEON(0): 	8301000065030c001000011d007251d0
(II) RADEON(0): 	1e206e285500c48e2100001e011d8018
(II) RADEON(0): 	711c1620582c2500c48e2100009e8c0a
(II) RADEON(0): 	d090204031200c405500c48e21000018
(II) RADEON(0): 	011d00bc52d01e20b8285540c48e2100
(II) RADEON(0): 	001e011d80d0721c1620102c2580c48e
(II) RADEON(0): 	2100009e000000ff0000000000000049
(II) RADEON(0): EDID vendor "PHL", prod id 18000
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x768"x0.0   68.25  1280 1328 1360 1440  768 771 778 790 -hsync -vsync (47.4 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 648 744 800  480 482 484 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "640x360"x85.0   25.77  640 656 720 800  360 361 364 379 -hsync +vsync (32.2 kHz)
(II) RADEON(0): Modeline "800x450"x85.0   41.81  800 840 920 1040  450 451 454 473 -hsync +vsync (40.2 kHz)
(II) RADEON(0): Modeline "1024x576"x85.0   69.11  1024 1080 1184 1344  576 577 580 605 -hsync +vsync (51.4 kHz)
(II) RADEON(0): Modeline "1152x648"x75.0   77.18  1152 1216 1336 1520  648 649 652 677 -hsync +vsync (50.8 kHz)
(II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: PHL  Model: 4650  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 71  vert.: 40
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.617 redY: 0.334   greenX: 0.283 greenY: 0.590
(II) RADEON(0): blueX: 0.143 blueY: 0.086   whiteX: 0.284 whiteY: 0.295
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 360  refresh: 85  vid: 55601
(II) RADEON(0): #1: hsize: 800  vsize 450  refresh: 85  vid: 55621
(II) RADEON(0): #2: hsize: 1024  vsize 576  refresh: 85  vid: 55649
(II) RADEON(0): #3: hsize: 1152  vsize 648  refresh: 75  vid: 53105
(II) RADEON(0): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.2 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 790 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 25.2 MHz   Image Size:  530 x 398 mm
(II) RADEON(0): h_active: 640  h_sync: 648  h_sync_end 744 h_blank_end 800 h_border: 8
(II) RADEON(0): v_active: 480  v_sync: 482  v_sync_end 484 v_blanking: 525 v_border: 8
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 27.0 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
(II) RADEON(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
(II) RADEON(0): Ranges: V min: 47 V max: 85 Hz, H min: 31 H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c504601010101
(II) RADEON(0): 	2b0f0103804728788a288e9e55489724
(II) RADEON(0): 	16484b256a0031d945d961d971cf81c0
(II) RADEON(0): 	010101010101a91a00a0500016303020
(II) RADEON(0): 	3700c48e21000018d60980a020e02d10
(II) RADEON(0): 	08602200128e210808188c0ad08a20e0
(II) RADEON(0): 	2d10103e9600c48e21000018000000fd
(II) RADEON(0): 	002f551f500e000a2020202020200104
(II) RADEON(0): 	02031a75470103040512931423090707
(II) RADEON(0): 	8301000065030c001000011d007251d0
(II) RADEON(0): 	1e206e285500c48e2100001e011d8018
(II) RADEON(0): 	711c1620582c2500c48e2100009e8c0a
(II) RADEON(0): 	d090204031200c405500c48e21000018
(II) RADEON(0): 	011d00bc52d01e20b8285540c48e2100
(II) RADEON(0): 	001e011d80d0721c1620102c2580c48e
(II) RADEON(0): 	2100009e000000ff0000000000000049
(II) RADEON(0): EDID vendor "PHL", prod id 18000
(II) RADEON(0): Not using mode "1280x768" (width too large for virtual size)
(II) RADEON(0): Not using mode "1152x648" (width too large for virtual size)
(II) RADEON(0): Not using mode "1280x720" (width too large for virtual size)
(II) RADEON(0): Printing probed modes for output DVI-0
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x576"x85.0   69.11  1024 1080 1184 1344  576 577 580 605 -hsync +vsync (51.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x450"x85.0   41.81  800 840 920 1040  450 451 454 473 -hsync +vsync (40.2 kHz)
(II) RADEON(0): Modeline "720x480"x59.9   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x60.0   25.18  640 648 744 800  480 482 484 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x360"x85.0   25.77  640 656 720 800  360 361 364 379 -hsync +vsync (32.2 kHz)
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
(II) RADEON(0): EDID vendor "PHL", prod id 2080
(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Manufacturer: PHL  Model: 4650  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 71  vert.: 40
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.617 redY: 0.334   greenX: 0.283 greenY: 0.590
(II) RADEON(0): blueX: 0.143 blueY: 0.086   whiteX: 0.284 whiteY: 0.295
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 360  refresh: 85  vid: 55601
(II) RADEON(0): #1: hsize: 800  vsize 450  refresh: 85  vid: 55621
(II) RADEON(0): #2: hsize: 1024  vsize 576  refresh: 85  vid: 55649
(II) RADEON(0): #3: hsize: 1152  vsize 648  refresh: 75  vid: 53105
(II) RADEON(0): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.2 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 790 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 25.2 MHz   Image Size:  530 x 398 mm
(II) RADEON(0): h_active: 640  h_sync: 648  h_sync_end 744 h_blank_end 800 h_border: 8
(II) RADEON(0): v_active: 480  v_sync: 482  v_sync_end 484 v_blanking: 525 v_border: 8
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 27.0 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
(II) RADEON(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
(II) RADEON(0): Ranges: V min: 47 V max: 85 Hz, H min: 31 H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c504601010101
(II) RADEON(0): 	2b0f0103804728788a288e9e55489724
(II) RADEON(0): 	16484b256a0031d945d961d971cf81c0
(II) RADEON(0): 	010101010101a91a00a0500016303020
(II) RADEON(0): 	3700c48e21000018d60980a020e02d10
(II) RADEON(0): 	08602200128e210808188c0ad08a20e0
(II) RADEON(0): 	2d10103e9600c48e21000018000000fd
(II) RADEON(0): 	002f551f500e000a2020202020200104
(II) RADEON(0): 	02031a75470103040512931423090707
(II) RADEON(0): 	8301000065030c001000011d007251d0
(II) RADEON(0): 	1e206e285500c48e2100001e011d8018
(II) RADEON(0): 	711c1620582c2500c48e2100009e8c0a
(II) RADEON(0): 	d090204031200c405500c48e21000018
(II) RADEON(0): 	011d00bc52d01e20b8285540c48e2100
(II) RADEON(0): 	001e011d80d0721c1620102c2580c48e
(II) RADEON(0): 	2100009e000000ff0000000000000049
(II) RADEON(0): EDID vendor "PHL", prod id 18000
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x768"x0.0   68.25  1280 1328 1360 1440  768 771 778 790 -hsync -vsync (47.4 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 648 744 800  480 482 484 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "640x360"x85.0   25.77  640 656 720 800  360 361 364 379 -hsync +vsync (32.2 kHz)
(II) RADEON(0): Modeline "800x450"x85.0   41.81  800 840 920 1040  450 451 454 473 -hsync +vsync (40.2 kHz)
(II) RADEON(0): Modeline "1024x576"x85.0   69.11  1024 1080 1184 1344  576 577 580 605 -hsync +vsync (51.4 kHz)
(II) RADEON(0): Modeline "1152x648"x75.0   77.18  1152 1216 1336 1520  648 649 652 677 -hsync +vsync (50.8 kHz)
(II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: PHL  Model: 4650  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 71  vert.: 40
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.617 redY: 0.334   greenX: 0.283 greenY: 0.590
(II) RADEON(0): blueX: 0.143 blueY: 0.086   whiteX: 0.284 whiteY: 0.295
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 360  refresh: 85  vid: 55601
(II) RADEON(0): #1: hsize: 800  vsize 450  refresh: 85  vid: 55621
(II) RADEON(0): #2: hsize: 1024  vsize 576  refresh: 85  vid: 55649
(II) RADEON(0): #3: hsize: 1152  vsize 648  refresh: 75  vid: 53105
(II) RADEON(0): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.2 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 790 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 25.2 MHz   Image Size:  530 x 398 mm
(II) RADEON(0): h_active: 640  h_sync: 648  h_sync_end 744 h_blank_end 800 h_border: 8
(II) RADEON(0): v_active: 480  v_sync: 482  v_sync_end 484 v_blanking: 525 v_border: 8
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 27.0 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
(II) RADEON(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
(II) RADEON(0): Ranges: V min: 47 V max: 85 Hz, H min: 31 H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c504601010101
(II) RADEON(0): 	2b0f0103804728788a288e9e55489724
(II) RADEON(0): 	16484b256a0031d945d961d971cf81c0
(II) RADEON(0): 	010101010101a91a00a0500016303020
(II) RADEON(0): 	3700c48e21000018d60980a020e02d10
(II) RADEON(0): 	08602200128e210808188c0ad08a20e0
(II) RADEON(0): 	2d10103e9600c48e21000018000000fd
(II) RADEON(0): 	002f551f500e000a2020202020200104
(II) RADEON(0): 	02031a75470103040512931423090707
(II) RADEON(0): 	8301000065030c001000011d007251d0
(II) RADEON(0): 	1e206e285500c48e2100001e011d8018
(II) RADEON(0): 	711c1620582c2500c48e2100009e8c0a
(II) RADEON(0): 	d090204031200c405500c48e21000018
(II) RADEON(0): 	011d00bc52d01e20b8285540c48e2100
(II) RADEON(0): 	001e011d80d0721c1620102c2580c48e
(II) RADEON(0): 	2100009e000000ff0000000000000049
(II) RADEON(0): EDID vendor "PHL", prod id 18000
(II) RADEON(0): Not using mode "1280x768" (width too large for virtual size)
(II) RADEON(0): Not using mode "1152x648" (width too large for virtual size)
(II) RADEON(0): Not using mode "1280x720" (width too large for virtual size)
(II) RADEON(0): Printing probed modes for output DVI-0
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x576"x85.0   69.11  1024 1080 1184 1344  576 577 580 605 -hsync +vsync (51.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x450"x85.0   41.81  800 840 920 1040  450 451 454 473 -hsync +vsync (40.2 kHz)
(II) RADEON(0): Modeline "720x480"x59.9   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x60.0   25.18  640 648 744 800  480 482 484 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x360"x85.0   25.77  640 656 720 800  360 361 364 379 -hsync +vsync (32.2 kHz)
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
disable FP2
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
(II) RADEON(0): EDID vendor "PHL", prod id 2080
(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Manufacturer: PHL  Model: 4650  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 71  vert.: 40
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.617 redY: 0.334   greenX: 0.283 greenY: 0.590
(II) RADEON(0): blueX: 0.143 blueY: 0.086   whiteX: 0.284 whiteY: 0.295
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 360  refresh: 85  vid: 55601
(II) RADEON(0): #1: hsize: 800  vsize 450  refresh: 85  vid: 55621
(II) RADEON(0): #2: hsize: 1024  vsize 576  refresh: 85  vid: 55649
(II) RADEON(0): #3: hsize: 1152  vsize 648  refresh: 75  vid: 53105
(II) RADEON(0): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.2 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 790 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 25.2 MHz   Image Size:  530 x 398 mm
(II) RADEON(0): h_active: 640  h_sync: 648  h_sync_end 744 h_blank_end 800 h_border: 8
(II) RADEON(0): v_active: 480  v_sync: 482  v_sync_end 484 v_blanking: 525 v_border: 8
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 27.0 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
(II) RADEON(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
(II) RADEON(0): Ranges: V min: 47 V max: 85 Hz, H min: 31 H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c504601010101
(II) RADEON(0): 	2b0f0103804728788a288e9e55489724
(II) RADEON(0): 	16484b256a0031d945d961d971cf81c0
(II) RADEON(0): 	010101010101a91a00a0500016303020
(II) RADEON(0): 	3700c48e21000018d60980a020e02d10
(II) RADEON(0): 	08602200128e210808188c0ad08a20e0
(II) RADEON(0): 	2d10103e9600c48e21000018000000fd
(II) RADEON(0): 	002f551f500e000a2020202020200104
(II) RADEON(0): 	02031a75470103040512931423090707
(II) RADEON(0): 	8301000065030c001000011d007251d0
(II) RADEON(0): 	1e206e285500c48e2100001e011d8018
(II) RADEON(0): 	711c1620582c2500c48e2100009e8c0a
(II) RADEON(0): 	d090204031200c405500c48e21000018
(II) RADEON(0): 	011d00bc52d01e20b8285540c48e2100
(II) RADEON(0): 	001e011d80d0721c1620102c2580c48e
(II) RADEON(0): 	2100009e000000ff0000000000000049
(II) RADEON(0): EDID vendor "PHL", prod id 18000
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x768"x0.0   68.25  1280 1328 1360 1440  768 771 778 790 -hsync -vsync (47.4 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 648 744 800  480 482 484 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "640x360"x85.0   25.77  640 656 720 800  360 361 364 379 -hsync +vsync (32.2 kHz)
(II) RADEON(0): Modeline "800x450"x85.0   41.81  800 840 920 1040  450 451 454 473 -hsync +vsync (40.2 kHz)
(II) RADEON(0): Modeline "1024x576"x85.0   69.11  1024 1080 1184 1344  576 577 580 605 -hsync +vsync (51.4 kHz)
(II) RADEON(0): Modeline "1152x648"x75.0   77.18  1152 1216 1336 1520  648 649 652 677 -hsync +vsync (50.8 kHz)
(II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: PHL  Model: 4650  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 71  vert.: 40
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.617 redY: 0.334   greenX: 0.283 greenY: 0.590
(II) RADEON(0): blueX: 0.143 blueY: 0.086   whiteX: 0.284 whiteY: 0.295
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 360  refresh: 85  vid: 55601
(II) RADEON(0): #1: hsize: 800  vsize 450  refresh: 85  vid: 55621
(II) RADEON(0): #2: hsize: 1024  vsize 576  refresh: 85  vid: 55649
(II) RADEON(0): #3: hsize: 1152  vsize 648  refresh: 75  vid: 53105
(II) RADEON(0): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.2 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 790 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 25.2 MHz   Image Size:  530 x 398 mm
(II) RADEON(0): h_active: 640  h_sync: 648  h_sync_end 744 h_blank_end 800 h_border: 8
(II) RADEON(0): v_active: 480  v_sync: 482  v_sync_end 484 v_blanking: 525 v_border: 8
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 27.0 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
(II) RADEON(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
(II) RADEON(0): Ranges: V min: 47 V max: 85 Hz, H min: 31 H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c504601010101
(II) RADEON(0): 	2b0f0103804728788a288e9e55489724
(II) RADEON(0): 	16484b256a0031d945d961d971cf81c0
(II) RADEON(0): 	010101010101a91a00a0500016303020
(II) RADEON(0): 	3700c48e21000018d60980a020e02d10
(II) RADEON(0): 	08602200128e210808188c0ad08a20e0
(II) RADEON(0): 	2d10103e9600c48e21000018000000fd
(II) RADEON(0): 	002f551f500e000a2020202020200104
(II) RADEON(0): 	02031a75470103040512931423090707
(II) RADEON(0): 	8301000065030c001000011d007251d0
(II) RADEON(0): 	1e206e285500c48e2100001e011d8018
(II) RADEON(0): 	711c1620582c2500c48e2100009e8c0a
(II) RADEON(0): 	d090204031200c405500c48e21000018
(II) RADEON(0): 	011d00bc52d01e20b8285540c48e2100
(II) RADEON(0): 	001e011d80d0721c1620102c2580c48e
(II) RADEON(0): 	2100009e000000ff0000000000000049
(II) RADEON(0): EDID vendor "PHL", prod id 18000
(II) RADEON(0): Not using mode "1280x768" (width too large for virtual size)
(II) RADEON(0): Not using mode "1152x648" (width too large for virtual size)
(II) RADEON(0): Not using mode "1280x720" (width too large for virtual size)
(II) RADEON(0): Printing probed modes for output DVI-0
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x576"x85.0   69.11  1024 1080 1184 1344  576 577 580 605 -hsync +vsync (51.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x450"x85.0   41.81  800 840 920 1040  450 451 454 473 -hsync +vsync (40.2 kHz)
(II) RADEON(0): Modeline "720x480"x59.9   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x60.0   25.18  640 648 744 800  480 482 484 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x360"x85.0   25.77  640 656 720 800  360 361 364 379 -hsync +vsync (32.2 kHz)
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
(II) RADEON(0): EDID vendor "PHL", prod id 2080
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
(II) RADEON(0): EDID vendor "PHL", prod id 2080
(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Manufacturer: PHL  Model: 4650  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 71  vert.: 40
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.617 redY: 0.334   greenX: 0.283 greenY: 0.590
(II) RADEON(0): blueX: 0.143 blueY: 0.086   whiteX: 0.284 whiteY: 0.295
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 360  refresh: 85  vid: 55601
(II) RADEON(0): #1: hsize: 800  vsize 450  refresh: 85  vid: 55621
(II) RADEON(0): #2: hsize: 1024  vsize 576  refresh: 85  vid: 55649
(II) RADEON(0): #3: hsize: 1152  vsize 648  refresh: 75  vid: 53105
(II) RADEON(0): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.2 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 790 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 25.2 MHz   Image Size:  530 x 398 mm
(II) RADEON(0): h_active: 640  h_sync: 648  h_sync_end 744 h_blank_end 800 h_border: 8
(II) RADEON(0): v_active: 480  v_sync: 482  v_sync_end 484 v_blanking: 525 v_border: 8
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 27.0 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
(II) RADEON(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
(II) RADEON(0): Ranges: V min: 47 V max: 85 Hz, H min: 31 H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c504601010101
(II) RADEON(0): 	2b0f0103804728788a288e9e55489724
(II) RADEON(0): 	16484b256a0031d945d961d971cf81c0
(II) RADEON(0): 	010101010101a91a00a0500016303020
(II) RADEON(0): 	3700c48e21000018d60980a020e02d10
(II) RADEON(0): 	08602200128e210808188c0ad08a20e0
(II) RADEON(0): 	2d10103e9600c48e21000018000000fd
(II) RADEON(0): 	002f551f500e000a2020202020200104
(II) RADEON(0): 	02031a75470103040512931423090707
(II) RADEON(0): 	8301000065030c001000011d007251d0
(II) RADEON(0): 	1e206e285500c48e2100001e011d8018
(II) RADEON(0): 	711c1620582c2500c48e2100009e8c0a
(II) RADEON(0): 	d090204031200c405500c48e21000018
(II) RADEON(0): 	011d00bc52d01e20b8285540c48e2100
(II) RADEON(0): 	001e011d80d0721c1620102c2580c48e
(II) RADEON(0): 	2100009e000000ff0000000000000049
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: PHL  Model: 4650  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 71  vert.: 40
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.617 redY: 0.334   greenX: 0.283 greenY: 0.590
(II) RADEON(0): blueX: 0.143 blueY: 0.086   whiteX: 0.284 whiteY: 0.295
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 360  refresh: 85  vid: 55601
(II) RADEON(0): #1: hsize: 800  vsize 450  refresh: 85  vid: 55621
(II) RADEON(0): #2: hsize: 1024  vsize 576  refresh: 85  vid: 55649
(II) RADEON(0): #3: hsize: 1152  vsize 648  refresh: 75  vid: 53105
(II) RADEON(0): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.2 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 790 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 25.2 MHz   Image Size:  530 x 398 mm
(II) RADEON(0): h_active: 640  h_sync: 648  h_sync_end 744 h_blank_end 800 h_border: 8
(II) RADEON(0): v_active: 480  v_sync: 482  v_sync_end 484 v_blanking: 525 v_border: 8
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 27.0 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
(II) RADEON(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
(II) RADEON(0): Ranges: V min: 47 V max: 85 Hz, H min: 31 H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c504601010101
(II) RADEON(0): 	2b0f0103804728788a288e9e55489724
(II) RADEON(0): 	16484b256a0031d945d961d971cf81c0
(II) RADEON(0): 	010101010101a91a00a0500016303020
(II) RADEON(0): 	3700c48e21000018d60980a020e02d10
(II) RADEON(0): 	08602200128e210808188c0ad08a20e0
(II) RADEON(0): 	2d10103e9600c48e21000018000000fd
(II) RADEON(0): 	002f551f500e000a2020202020200104
(II) RADEON(0): 	02031a75470103040512931423090707
(II) RADEON(0): 	8301000065030c001000011d007251d0
(II) RADEON(0): 	1e206e285500c48e2100001e011d8018
(II) RADEON(0): 	711c1620582c2500c48e2100009e8c0a
(II) RADEON(0): 	d090204031200c405500c48e21000018
(II) RADEON(0): 	011d00bc52d01e20b8285540c48e2100
(II) RADEON(0): 	001e011d80d0721c1620102c2580c48e
(II) RADEON(0): 	2100009e000000ff0000000000000049
(II) RADEON(0): EDID vendor "PHL", prod id 18000
(II) RADEON(0): Not using mode "1280x768" (width too large for virtual size)
(II) RADEON(0): Not using mode "1152x648" (width too large for virtual size)
(II) RADEON(0): Not using mode "1280x720" (width too large for virtual size)
(II) RADEON(0): Printing probed modes for output DVI-0
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x576"x85.0   69.11  1024 1080 1184 1344  576 577 580 605 -hsync +vsync (51.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x450"x85.0   41.81  800 840 920 1040  450 451 454 473 -hsync +vsync (40.2 kHz)
(II) RADEON(0): Modeline "720x480"x59.9   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x60.0   25.18  640 648 744 800  480 482 484 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x360"x85.0   25.77  640 656 720 800  360 361 364 379 -hsync +vsync (32.2 kHz)
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
(II) RADEON(0): EDID vendor "PHL", prod id 2080
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
(II) RADEON(0): EDID vendor "PHL", prod id 2080
(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Manufacturer: PHL  Model: 4650  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 71  vert.: 40
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.617 redY: 0.334   greenX: 0.283 greenY: 0.590
(II) RADEON(0): blueX: 0.143 blueY: 0.086   whiteX: 0.284 whiteY: 0.295
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 360  refresh: 85  vid: 55601
(II) RADEON(0): #1: hsize: 800  vsize 450  refresh: 85  vid: 55621
(II) RADEON(0): #2: hsize: 1024  vsize 576  refresh: 85  vid: 55649
(II) RADEON(0): #3: hsize: 1152  vsize 648  refresh: 75  vid: 53105
(II) RADEON(0): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.2 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 790 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 25.2 MHz   Image Size:  530 x 398 mm
(II) RADEON(0): h_active: 640  h_sync: 648  h_sync_end 744 h_blank_end 800 h_border: 8
(II) RADEON(0): v_active: 480  v_sync: 482  v_sync_end 484 v_blanking: 525 v_border: 8
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 27.0 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
(II) RADEON(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
(II) RADEON(0): Ranges: V min: 47 V max: 85 Hz, H min: 31 H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c504601010101
(II) RADEON(0): 	2b0f0103804728788a288e9e55489724
(II) RADEON(0): 	16484b256a0031d945d961d971cf81c0
(II) RADEON(0): 	010101010101a91a00a0500016303020
(II) RADEON(0): 	3700c48e21000018d60980a020e02d10
(II) RADEON(0): 	08602200128e210808188c0ad08a20e0
(II) RADEON(0): 	2d10103e9600c48e21000018000000fd
(II) RADEON(0): 	002f551f500e000a2020202020200104
(II) RADEON(0): 	02031a75470103040512931423090707
(II) RADEON(0): 	8301000065030c001000011d007251d0
(II) RADEON(0): 	1e206e285500c48e2100001e011d8018
(II) RADEON(0): 	711c1620582c2500c48e2100009e8c0a
(II) RADEON(0): 	d090204031200c405500c48e21000018
(II) RADEON(0): 	011d00bc52d01e20b8285540c48e2100
(II) RADEON(0): 	001e011d80d0721c1620102c2580c48e
(II) RADEON(0): 	2100009e000000ff0000000000000049
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: PHL  Model: 4650  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 71  vert.: 40
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.617 redY: 0.334   greenX: 0.283 greenY: 0.590
(II) RADEON(0): blueX: 0.143 blueY: 0.086   whiteX: 0.284 whiteY: 0.295
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 360  refresh: 85  vid: 55601
(II) RADEON(0): #1: hsize: 800  vsize 450  refresh: 85  vid: 55621
(II) RADEON(0): #2: hsize: 1024  vsize 576  refresh: 85  vid: 55649
(II) RADEON(0): #3: hsize: 1152  vsize 648  refresh: 75  vid: 53105
(II) RADEON(0): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.2 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 790 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 25.2 MHz   Image Size:  530 x 398 mm
(II) RADEON(0): h_active: 640  h_sync: 648  h_sync_end 744 h_blank_end 800 h_border: 8
(II) RADEON(0): v_active: 480  v_sync: 482  v_sync_end 484 v_blanking: 525 v_border: 8
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 27.0 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
(II) RADEON(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
(II) RADEON(0): Ranges: V min: 47 V max: 85 Hz, H min: 31 H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c504601010101
(II) RADEON(0): 	2b0f0103804728788a288e9e55489724
(II) RADEON(0): 	16484b256a0031d945d961d971cf81c0
(II) RADEON(0): 	010101010101a91a00a0500016303020
(II) RADEON(0): 	3700c48e21000018d60980a020e02d10
(II) RADEON(0): 	08602200128e210808188c0ad08a20e0
(II) RADEON(0): 	2d10103e9600c48e21000018000000fd
(II) RADEON(0): 	002f551f500e000a2020202020200104
(II) RADEON(0): 	02031a75470103040512931423090707
(II) RADEON(0): 	8301000065030c001000011d007251d0
(II) RADEON(0): 	1e206e285500c48e2100001e011d8018
(II) RADEON(0): 	711c1620582c2500c48e2100009e8c0a
(II) RADEON(0): 	d090204031200c405500c48e21000018
(II) RADEON(0): 	011d00bc52d01e20b8285540c48e2100
(II) RADEON(0): 	001e011d80d0721c1620102c2580c48e
(II) RADEON(0): 	2100009e000000ff0000000000000049
(II) RADEON(0): EDID vendor "PHL", prod id 18000
(II) RADEON(0): Not using mode "1280x768" (width too large for virtual size)
(II) RADEON(0): Not using mode "1152x648" (width too large for virtual size)
(II) RADEON(0): Not using mode "1280x720" (width too large for virtual size)
(II) RADEON(0): Printing probed modes for output DVI-0
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x576"x85.0   69.11  1024 1080 1184 1344  576 577 580 605 -hsync +vsync (51.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x450"x85.0   41.81  800 840 920 1040  450 451 454 473 -hsync +vsync (40.2 kHz)
(II) RADEON(0): Modeline "720x480"x59.9   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x60.0   25.18  640 648 744 800  480 482 484 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x360"x85.0   25.77  640 656 720 800  360 361 364 379 -hsync +vsync (32.2 kHz)
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
(II) RADEON(0): EDID vendor "PHL", prod id 2080
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
(II) RADEON(0): EDID vendor "PHL", prod id 2080
(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Manufacturer: PHL  Model: 4650  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 71  vert.: 40
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.617 redY: 0.334   greenX: 0.283 greenY: 0.590
(II) RADEON(0): blueX: 0.143 blueY: 0.086   whiteX: 0.284 whiteY: 0.295
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 360  refresh: 85  vid: 55601
(II) RADEON(0): #1: hsize: 800  vsize 450  refresh: 85  vid: 55621
(II) RADEON(0): #2: hsize: 1024  vsize 576  refresh: 85  vid: 55649
(II) RADEON(0): #3: hsize: 1152  vsize 648  refresh: 75  vid: 53105
(II) RADEON(0): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.2 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 790 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 25.2 MHz   Image Size:  530 x 398 mm
(II) RADEON(0): h_active: 640  h_sync: 648  h_sync_end 744 h_blank_end 800 h_border: 8
(II) RADEON(0): v_active: 480  v_sync: 482  v_sync_end 484 v_blanking: 525 v_border: 8
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 27.0 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
(II) RADEON(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
(II) RADEON(0): Ranges: V min: 47 V max: 85 Hz, H min: 31 H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c504601010101
(II) RADEON(0): 	2b0f0103804728788a288e9e55489724
(II) RADEON(0): 	16484b256a0031d945d961d971cf81c0
(II) RADEON(0): 	010101010101a91a00a0500016303020
(II) RADEON(0): 	3700c48e21000018d60980a020e02d10
(II) RADEON(0): 	08602200128e210808188c0ad08a20e0
(II) RADEON(0): 	2d10103e9600c48e21000018000000fd
(II) RADEON(0): 	002f551f500e000a2020202020200104
(II) RADEON(0): 	02031a75470103040512931423090707
(II) RADEON(0): 	8301000065030c001000011d007251d0
(II) RADEON(0): 	1e206e285500c48e2100001e011d8018
(II) RADEON(0): 	711c1620582c2500c48e2100009e8c0a
(II) RADEON(0): 	d090204031200c405500c48e21000018
(II) RADEON(0): 	011d00bc52d01e20b8285540c48e2100
(II) RADEON(0): 	001e011d80d0721c1620102c2580c48e
(II) RADEON(0): 	2100009e000000ff0000000000000049
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: PHL  Model: 4650  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 71  vert.: 40
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.617 redY: 0.334   greenX: 0.283 greenY: 0.590
(II) RADEON(0): blueX: 0.143 blueY: 0.086   whiteX: 0.284 whiteY: 0.295
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 360  refresh: 85  vid: 55601
(II) RADEON(0): #1: hsize: 800  vsize 450  refresh: 85  vid: 55621
(II) RADEON(0): #2: hsize: 1024  vsize 576  refresh: 85  vid: 55649
(II) RADEON(0): #3: hsize: 1152  vsize 648  refresh: 75  vid: 53105
(II) RADEON(0): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.2 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 790 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 25.2 MHz   Image Size:  530 x 398 mm
(II) RADEON(0): h_active: 640  h_sync: 648  h_sync_end 744 h_blank_end 800 h_border: 8
(II) RADEON(0): v_active: 480  v_sync: 482  v_sync_end 484 v_blanking: 525 v_border: 8
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 27.0 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
(II) RADEON(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
(II) RADEON(0): Ranges: V min: 47 V max: 85 Hz, H min: 31 H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c504601010101
(II) RADEON(0): 	2b0f0103804728788a288e9e55489724
(II) RADEON(0): 	16484b256a0031d945d961d971cf81c0
(II) RADEON(0): 	010101010101a91a00a0500016303020
(II) RADEON(0): 	3700c48e21000018d60980a020e02d10
(II) RADEON(0): 	08602200128e210808188c0ad08a20e0
(II) RADEON(0): 	2d10103e9600c48e21000018000000fd
(II) RADEON(0): 	002f551f500e000a2020202020200104
(II) RADEON(0): 	02031a75470103040512931423090707
(II) RADEON(0): 	8301000065030c001000011d007251d0
(II) RADEON(0): 	1e206e285500c48e2100001e011d8018
(II) RADEON(0): 	711c1620582c2500c48e2100009e8c0a
(II) RADEON(0): 	d090204031200c405500c48e21000018
(II) RADEON(0): 	011d00bc52d01e20b8285540c48e2100
(II) RADEON(0): 	001e011d80d0721c1620102c2580c48e
(II) RADEON(0): 	2100009e000000ff0000000000000049
(II) RADEON(0): EDID vendor "PHL", prod id 18000
(II) RADEON(0): Not using mode "1280x768" (width too large for virtual size)
(II) RADEON(0): Not using mode "1152x648" (width too large for virtual size)
(II) RADEON(0): Not using mode "1280x720" (width too large for virtual size)
(II) RADEON(0): Printing probed modes for output DVI-0
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x576"x85.0   69.11  1024 1080 1184 1344  576 577 580 605 -hsync +vsync (51.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x450"x85.0   41.81  800 840 920 1040  450 451 454 473 -hsync +vsync (40.2 kHz)
(II) RADEON(0): Modeline "720x480"x59.9   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x60.0   25.18  640 648 744 800  480 482 484 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x360"x85.0   25.77  640 656 720 800  360 361 364 379 -hsync +vsync (32.2 kHz)
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
(II) RADEON(0): EDID vendor "PHL", prod id 2080
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
(II) RADEON(0): EDID vendor "PHL", prod id 2080
(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Manufacturer: PHL  Model: 4650  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 71  vert.: 40
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.617 redY: 0.334   greenX: 0.283 greenY: 0.590
(II) RADEON(0): blueX: 0.143 blueY: 0.086   whiteX: 0.284 whiteY: 0.295
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 360  refresh: 85  vid: 55601
(II) RADEON(0): #1: hsize: 800  vsize 450  refresh: 85  vid: 55621
(II) RADEON(0): #2: hsize: 1024  vsize 576  refresh: 85  vid: 55649
(II) RADEON(0): #3: hsize: 1152  vsize 648  refresh: 75  vid: 53105
(II) RADEON(0): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.2 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 790 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 25.2 MHz   Image Size:  530 x 398 mm
(II) RADEON(0): h_active: 640  h_sync: 648  h_sync_end 744 h_blank_end 800 h_border: 8
(II) RADEON(0): v_active: 480  v_sync: 482  v_sync_end 484 v_blanking: 525 v_border: 8
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 27.0 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
(II) RADEON(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
(II) RADEON(0): Ranges: V min: 47 V max: 85 Hz, H min: 31 H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c504601010101
(II) RADEON(0): 	2b0f0103804728788a288e9e55489724
(II) RADEON(0): 	16484b256a0031d945d961d971cf81c0
(II) RADEON(0): 	010101010101a91a00a0500016303020
(II) RADEON(0): 	3700c48e21000018d60980a020e02d10
(II) RADEON(0): 	08602200128e210808188c0ad08a20e0
(II) RADEON(0): 	2d10103e9600c48e21000018000000fd
(II) RADEON(0): 	002f551f500e000a2020202020200104
(II) RADEON(0): 	02031a75470103040512931423090707
(II) RADEON(0): 	8301000065030c001000011d007251d0
(II) RADEON(0): 	1e206e285500c48e2100001e011d8018
(II) RADEON(0): 	711c1620582c2500c48e2100009e8c0a
(II) RADEON(0): 	d090204031200c405500c48e21000018
(II) RADEON(0): 	011d00bc52d01e20b8285540c48e2100
(II) RADEON(0): 	001e011d80d0721c1620102c2580c48e
(II) RADEON(0): 	2100009e000000ff0000000000000049
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: PHL  Model: 4650  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 71  vert.: 40
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.617 redY: 0.334   greenX: 0.283 greenY: 0.590
(II) RADEON(0): blueX: 0.143 blueY: 0.086   whiteX: 0.284 whiteY: 0.295
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 360  refresh: 85  vid: 55601
(II) RADEON(0): #1: hsize: 800  vsize 450  refresh: 85  vid: 55621
(II) RADEON(0): #2: hsize: 1024  vsize 576  refresh: 85  vid: 55649
(II) RADEON(0): #3: hsize: 1152  vsize 648  refresh: 75  vid: 53105
(II) RADEON(0): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.2 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 790 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 25.2 MHz   Image Size:  530 x 398 mm
(II) RADEON(0): h_active: 640  h_sync: 648  h_sync_end 744 h_blank_end 800 h_border: 8
(II) RADEON(0): v_active: 480  v_sync: 482  v_sync_end 484 v_blanking: 525 v_border: 8
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 27.0 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
(II) RADEON(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
(II) RADEON(0): Ranges: V min: 47 V max: 85 Hz, H min: 31 H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c504601010101
(II) RADEON(0): 	2b0f0103804728788a288e9e55489724
(II) RADEON(0): 	16484b256a0031d945d961d971cf81c0
(II) RADEON(0): 	010101010101a91a00a0500016303020
(II) RADEON(0): 	3700c48e21000018d60980a020e02d10
(II) RADEON(0): 	08602200128e210808188c0ad08a20e0
(II) RADEON(0): 	2d10103e9600c48e21000018000000fd
(II) RADEON(0): 	002f551f500e000a2020202020200104
(II) RADEON(0): 	02031a75470103040512931423090707
(II) RADEON(0): 	8301000065030c001000011d007251d0
(II) RADEON(0): 	1e206e285500c48e2100001e011d8018
(II) RADEON(0): 	711c1620582c2500c48e2100009e8c0a
(II) RADEON(0): 	d090204031200c405500c48e21000018
(II) RADEON(0): 	011d00bc52d01e20b8285540c48e2100
(II) RADEON(0): 	001e011d80d0721c1620102c2580c48e
(II) RADEON(0): 	2100009e000000ff0000000000000049
(II) RADEON(0): EDID vendor "PHL", prod id 18000
(II) RADEON(0): Not using mode "1280x768" (width too large for virtual size)
(II) RADEON(0): Not using mode "1152x648" (width too large for virtual size)
(II) RADEON(0): Not using mode "1280x720" (width too large for virtual size)
(II) RADEON(0): Printing probed modes for output DVI-0
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x576"x85.0   69.11  1024 1080 1184 1344  576 577 580 605 -hsync +vsync (51.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x450"x85.0   41.81  800 840 920 1040  450 451 454 473 -hsync +vsync (40.2 kHz)
(II) RADEON(0): Modeline "720x480"x59.9   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x60.0   25.18  640 648 744 800  480 482 484 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x360"x85.0   25.77  640 656 720 800  360 361 364 379 -hsync +vsync (32.2 kHz)
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
(II) RADEON(0): EDID vendor "PHL", prod id 2080
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
(II) RADEON(0): EDID vendor "PHL", prod id 2080
(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Manufacturer: PHL  Model: 4650  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 71  vert.: 40
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.617 redY: 0.334   greenX: 0.283 greenY: 0.590
(II) RADEON(0): blueX: 0.143 blueY: 0.086   whiteX: 0.284 whiteY: 0.295
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 360  refresh: 85  vid: 55601
(II) RADEON(0): #1: hsize: 800  vsize 450  refresh: 85  vid: 55621
(II) RADEON(0): #2: hsize: 1024  vsize 576  refresh: 85  vid: 55649
(II) RADEON(0): #3: hsize: 1152  vsize 648  refresh: 75  vid: 53105
(II) RADEON(0): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.2 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 790 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 25.2 MHz   Image Size:  530 x 398 mm
(II) RADEON(0): h_active: 640  h_sync: 648  h_sync_end 744 h_blank_end 800 h_border: 8
(II) RADEON(0): v_active: 480  v_sync: 482  v_sync_end 484 v_blanking: 525 v_border: 8
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 27.0 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
(II) RADEON(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
(II) RADEON(0): Ranges: V min: 47 V max: 85 Hz, H min: 31 H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c504601010101
(II) RADEON(0): 	2b0f0103804728788a288e9e55489724
(II) RADEON(0): 	16484b256a0031d945d961d971cf81c0
(II) RADEON(0): 	010101010101a91a00a0500016303020
(II) RADEON(0): 	3700c48e21000018d60980a020e02d10
(II) RADEON(0): 	08602200128e210808188c0ad08a20e0
(II) RADEON(0): 	2d10103e9600c48e21000018000000fd
(II) RADEON(0): 	002f551f500e000a2020202020200104
(II) RADEON(0): 	02031a75470103040512931423090707
(II) RADEON(0): 	8301000065030c001000011d007251d0
(II) RADEON(0): 	1e206e285500c48e2100001e011d8018
(II) RADEON(0): 	711c1620582c2500c48e2100009e8c0a
(II) RADEON(0): 	d090204031200c405500c48e21000018
(II) RADEON(0): 	011d00bc52d01e20b8285540c48e2100
(II) RADEON(0): 	001e011d80d0721c1620102c2580c48e
(II) RADEON(0): 	2100009e000000ff0000000000000049
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: PHL  Model: 4650  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 71  vert.: 40
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.617 redY: 0.334   greenX: 0.283 greenY: 0.590
(II) RADEON(0): blueX: 0.143 blueY: 0.086   whiteX: 0.284 whiteY: 0.295
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 360  refresh: 85  vid: 55601
(II) RADEON(0): #1: hsize: 800  vsize 450  refresh: 85  vid: 55621
(II) RADEON(0): #2: hsize: 1024  vsize 576  refresh: 85  vid: 55649
(II) RADEON(0): #3: hsize: 1152  vsize 648  refresh: 75  vid: 53105
(II) RADEON(0): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.2 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 790 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 25.2 MHz   Image Size:  530 x 398 mm
(II) RADEON(0): h_active: 640  h_sync: 648  h_sync_end 744 h_blank_end 800 h_border: 8
(II) RADEON(0): v_active: 480  v_sync: 482  v_sync_end 484 v_blanking: 525 v_border: 8
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 27.0 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
(II) RADEON(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
(II) RADEON(0): Ranges: V min: 47 V max: 85 Hz, H min: 31 H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c504601010101
(II) RADEON(0): 	2b0f0103804728788a288e9e55489724
(II) RADEON(0): 	16484b256a0031d945d961d971cf81c0
(II) RADEON(0): 	010101010101a91a00a0500016303020
(II) RADEON(0): 	3700c48e21000018d60980a020e02d10
(II) RADEON(0): 	08602200128e210808188c0ad08a20e0
(II) RADEON(0): 	2d10103e9600c48e21000018000000fd
(II) RADEON(0): 	002f551f500e000a2020202020200104
(II) RADEON(0): 	02031a75470103040512931423090707
(II) RADEON(0): 	8301000065030c001000011d007251d0
(II) RADEON(0): 	1e206e285500c48e2100001e011d8018
(II) RADEON(0): 	711c1620582c2500c48e2100009e8c0a
(II) RADEON(0): 	d090204031200c405500c48e21000018
(II) RADEON(0): 	011d00bc52d01e20b8285540c48e2100
(II) RADEON(0): 	001e011d80d0721c1620102c2580c48e
(II) RADEON(0): 	2100009e000000ff0000000000000049
(II) RADEON(0): EDID vendor "PHL", prod id 18000
(II) RADEON(0): Not using mode "1280x768" (width too large for virtual size)
(II) RADEON(0): Not using mode "1152x648" (width too large for virtual size)
(II) RADEON(0): Not using mode "1280x720" (width too large for virtual size)
(II) RADEON(0): Printing probed modes for output DVI-0
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x576"x85.0   69.11  1024 1080 1184 1344  576 577 580 605 -hsync +vsync (51.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x450"x85.0   41.81  800 840 920 1040  450 451 454 473 -hsync +vsync (40.2 kHz)
(II) RADEON(0): Modeline "720x480"x59.9   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x60.0   25.18  640 648 744 800  480 482 484 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x360"x85.0   25.77  640 656 720 800  360 361 364 379 -hsync +vsync (32.2 kHz)
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
(II) RADEON(0): EDID vendor "PHL", prod id 2080
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
(II) RADEON(0): EDID vendor "PHL", prod id 2080
(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Manufacturer: PHL  Model: 4650  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 71  vert.: 40
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.617 redY: 0.334   greenX: 0.283 greenY: 0.590
(II) RADEON(0): blueX: 0.143 blueY: 0.086   whiteX: 0.284 whiteY: 0.295
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 360  refresh: 85  vid: 55601
(II) RADEON(0): #1: hsize: 800  vsize 450  refresh: 85  vid: 55621
(II) RADEON(0): #2: hsize: 1024  vsize 576  refresh: 85  vid: 55649
(II) RADEON(0): #3: hsize: 1152  vsize 648  refresh: 75  vid: 53105
(II) RADEON(0): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.2 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 790 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 25.2 MHz   Image Size:  530 x 398 mm
(II) RADEON(0): h_active: 640  h_sync: 648  h_sync_end 744 h_blank_end 800 h_border: 8
(II) RADEON(0): v_active: 480  v_sync: 482  v_sync_end 484 v_blanking: 525 v_border: 8
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 27.0 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
(II) RADEON(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
(II) RADEON(0): Ranges: V min: 47 V max: 85 Hz, H min: 31 H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c504601010101
(II) RADEON(0): 	2b0f0103804728788a288e9e55489724
(II) RADEON(0): 	16484b256a0031d945d961d971cf81c0
(II) RADEON(0): 	010101010101a91a00a0500016303020
(II) RADEON(0): 	3700c48e21000018d60980a020e02d10
(II) RADEON(0): 	08602200128e210808188c0ad08a20e0
(II) RADEON(0): 	2d10103e9600c48e21000018000000fd
(II) RADEON(0): 	002f551f500e000a2020202020200104
(II) RADEON(0): 	02031a75470103040512931423090707
(II) RADEON(0): 	8301000065030c001000011d007251d0
(II) RADEON(0): 	1e206e285500c48e2100001e011d8018
(II) RADEON(0): 	711c1620582c2500c48e2100009e8c0a
(II) RADEON(0): 	d090204031200c405500c48e21000018
(II) RADEON(0): 	011d00bc52d01e20b8285540c48e2100
(II) RADEON(0): 	001e011d80d0721c1620102c2580c48e
(II) RADEON(0): 	2100009e000000ff0000000000000049
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: PHL  Model: 4650  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 71  vert.: 40
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.617 redY: 0.334   greenX: 0.283 greenY: 0.590
(II) RADEON(0): blueX: 0.143 blueY: 0.086   whiteX: 0.284 whiteY: 0.295
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 360  refresh: 85  vid: 55601
(II) RADEON(0): #1: hsize: 800  vsize 450  refresh: 85  vid: 55621
(II) RADEON(0): #2: hsize: 1024  vsize 576  refresh: 85  vid: 55649
(II) RADEON(0): #3: hsize: 1152  vsize 648  refresh: 75  vid: 53105
(II) RADEON(0): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.2 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 790 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 25.2 MHz   Image Size:  530 x 398 mm
(II) RADEON(0): h_active: 640  h_sync: 648  h_sync_end 744 h_blank_end 800 h_border: 8
(II) RADEON(0): v_active: 480  v_sync: 482  v_sync_end 484 v_blanking: 525 v_border: 8
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 27.0 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
(II) RADEON(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
(II) RADEON(0): Ranges: V min: 47 V max: 85 Hz, H min: 31 H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c504601010101
(II) RADEON(0): 	2b0f0103804728788a288e9e55489724
(II) RADEON(0): 	16484b256a0031d945d961d971cf81c0
(II) RADEON(0): 	010101010101a91a00a0500016303020
(II) RADEON(0): 	3700c48e21000018d60980a020e02d10
(II) RADEON(0): 	08602200128e210808188c0ad08a20e0
(II) RADEON(0): 	2d10103e9600c48e21000018000000fd
(II) RADEON(0): 	002f551f500e000a2020202020200104
(II) RADEON(0): 	02031a75470103040512931423090707
(II) RADEON(0): 	8301000065030c001000011d007251d0
(II) RADEON(0): 	1e206e285500c48e2100001e011d8018
(II) RADEON(0): 	711c1620582c2500c48e2100009e8c0a
(II) RADEON(0): 	d090204031200c405500c48e21000018
(II) RADEON(0): 	011d00bc52d01e20b8285540c48e2100
(II) RADEON(0): 	001e011d80d0721c1620102c2580c48e
(II) RADEON(0): 	2100009e000000ff0000000000000049
(II) RADEON(0): EDID vendor "PHL", prod id 18000
(II) RADEON(0): Not using mode "1280x768" (width too large for virtual size)
(II) RADEON(0): Not using mode "1152x648" (width too large for virtual size)
(II) RADEON(0): Not using mode "1280x720" (width too large for virtual size)
(II) RADEON(0): Printing probed modes for output DVI-0
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x576"x85.0   69.11  1024 1080 1184 1344  576 577 580 605 -hsync +vsync (51.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x450"x85.0   41.81  800 840 920 1040  450 451 454 473 -hsync +vsync (40.2 kHz)
(II) RADEON(0): Modeline "720x480"x59.9   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x60.0   25.18  640 648 744 800  480 482 484 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x360"x85.0   25.77  640 656 720 800  360 361 364 379 -hsync +vsync (32.2 kHz)
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
(II) ORTEK Smartpad Keyboard: Close
(II) UnloadModule: "evdev"
(II) A4Tech RF USB Receiver: Close
(II) UnloadModule: "evdev"
(II) A4Tech RF USB Receiver: Close
(II) UnloadModule: "evdev"
(II) Power Button: Close
(II) UnloadModule: "evdev"
(II) ORTEK Smartpad Keyboard: Close
(II) UnloadModule: "evdev"
(II) Power Button: Close
(II) UnloadModule: "evdev"
(II) Macintosh mouse button emulation: Close
(II) UnloadModule: "evdev"
disable TVDAC
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x5fff5800 0x5fff5800
(II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
finished PLL2
finished PLL1
Entering Restore TV
Restore TV PLL
Restore TVHV
Restore TV Restarts
Restore Timing Tables
Restore TV standard
Leaving Restore TV
(II) RADEON(0): [drm] removed 1 reserved context for kernel
(II) RADEON(0): [drm] unmapping 8192 bytes of SAREA 0xf806c000 at 0xb779b000
(II) RADEON(0): [drm] Closed DRM master.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) APM registered successfully
(II) RADEON(0): RADEONScreenInit c0000000 0 0
Entering TV Save
Save TV timing tables
saveTimingTables: reading timing tables
TV Save done
disable TVDAC
(II) RADEON(0): Dynamic Power Management Disabled
(==) RADEON(0): Using 24 bit depth buffer
(II) RADEON(0): RADEONInitMemoryMap() : 
(II) RADEON(0):   mem_size         : 0x08000000
(II) RADEON(0):   MC_FB_LOCATION   : 0x5fff5800
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(II) RADEON(0): Depth moves disabled by default
(II) RADEON(0): Allocating from a screen of 131072 kb
(II) RADEON(0): Will use 32 kb for hardware cursor 0 at offset 0x00300000
(II) RADEON(0): Will use 32 kb for hardware cursor 1 at offset 0x00304000
(II) RADEON(0): Will use 3072 kb for front buffer at offset 0x00000000
(II) RADEON(0): Will use 3072 kb for back buffer at offset 0x00308000
(II) RADEON(0): Will use 3072 kb for depth buffer at offset 0x00608000
(II) RADEON(0): Will use 60416 kb for textures at offset 0x00908000
(II) RADEON(0): Will use 61408 kb for X Server offscreen at offset 0x04408000
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:05.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: drmOpenMinor returns 10
drmOpenByBusid: drmGetBusid reports pci:0000:01:05.0
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) RADEON(0): [drm] Using the DRM lock SAREA also for drawables.
(II) RADEON(0): [drm] framebuffer handle = 0xc0000000
(II) RADEON(0): [drm] added 1 reserved context for kernel
(II) RADEON(0): X context handle = 0x1
(II) RADEON(0): [drm] installed DRM signal handler
(==) RADEON(0): Using AGP 8x
(II) RADEON(0): [agp] Mode 0x1f00020a [AGP 0x1002/0x5833; Card 0x1002/0x5834 0x1043/0x8107]
(II) RADEON(0): [agp] 8192 kB allocated with handle 0x00000001
(II) RADEON(0): [agp] ring handle = 0xe0000000
(II) RADEON(0): [agp] Ring mapped at 0xb769a000
(II) RADEON(0): [agp] ring read ptr handle = 0xe0101000
(II) RADEON(0): [agp] Ring read ptr mapped at 0xb7699000
(II) RADEON(0): [agp] vertex/indirect buffers handle = 0xe0102000
(II) RADEON(0): [agp] Vertex/indirect buffers mapped at 0xaf42b000
(II) RADEON(0): [agp] GART texture map handle = 0xe0302000
(II) RADEON(0): [agp] GART Texture map mapped at 0xaef4b000
(II) RADEON(0): [drm] register handle = 0x2fb40000
(II) RADEON(0): [dri] Visual configs initialized
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x5fff5800 0x5fff5800
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(II) RADEON(0): [DRI] installation complete
(II) RADEON(0): [drm] Added 32 65536 byte vertex/indirect buffers
(II) RADEON(0): [drm] Mapped 32 vertex/indirect buffers
(II) RADEON(0): [drm] dma control initialized, using IRQ 16
(II) RADEON(0): [drm] Initialized kernel GART heap manager, 5111808
(WW) RADEON(0): DRI init changed memory map, adjusting ...
(WW) RADEON(0):   MC_FB_LOCATION  was: 0x5fff5800 is: 0x5fff5800
(WW) RADEON(0):   MC_AGP_LOCATION was: 0xffffffc0 is: 0xe07fe000
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x5fff5800 0x5fff5800
(II) RADEON(0):   MC_AGP_LOCATION  : 0xe07fe000
(II) RADEON(0): Direct rendering enabled
(II) RADEON(0): Render acceleration enabled for R200 type cards.
(II) RADEON(0): Setting EXA maxPitchBytes
(II) EXA(0): Offscreen pixmap area of 62881792 bytes
(II) EXA(0): Driver registered support for the following operations:
(II)         Solid
(II)         Copy
(II)         Composite (RENDER acceleration)
(II)         UploadToScreen
(II) RADEON(0): Acceleration enabled
(II) RADEON(0): DPMS enabled
(II) RADEON(0): No video input capabilities detected and no information is provided - disabling multimedia i2c
(II) Loading sub module "theatre_detect"
(II) LoadModule: "theatre_detect"
(II) Reloading /usr/lib/xorg/modules/multimedia//theatre_detect_drv.so
(II) RADEON(0): no multimedia table present, disabling Rage Theatre.
(II) RADEON(0): Set up overlay video
(II) RADEON(0): Set up textured video
disable TVDAC
disable FP2
disable TV
disable TVDAC
init memmap
init common
init crtc1
init pll1
freq: 65000000
best_freq: 64990769
best_feedback_div: 236
best_frac_feedback_div: 0
best_ref_div: 13
best_post_div: 4
restore memmap
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x5fff5800 0x5fff5800
(II) RADEON(0):   MC_AGP_LOCATION  : 0xe07fe000
restore common
restore crtc1
restore pll1
finished PLL1
set RMX
set TVDAC
enable TVDAC
disable FP2
(II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(--) RandR disabled
(II) AIGLX: Screen 0 is not DRI2 capable
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:05.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: drmOpenMinor returns 11
drmOpenByBusid: drmGetBusid reports pci:0000:01:05.0
(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: enabled GLX_SGI_make_current_read
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: enabled GLX_texture_from_pixmap with driver support
(II) AIGLX: Loaded and initialized /usr/lib/dri/r200_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) RADEON(0): Setting screen physical size to 307 x 230
(EE) XKB: No components provided for device Virtual core keyboard
(WW) Couldn't load XKB keymap, falling back to pre-XKB keymap
[config/dbus] couldn't register object path
(II) config/hal: Adding input device ORTEK Smartpad Keyboard
(**) ORTEK Smartpad Keyboard: always reports core events
(**) ORTEK Smartpad Keyboard: Device: "/dev/input/event4"
(II) ORTEK Smartpad Keyboard: Found 9 mouse buttons
(II) ORTEK Smartpad Keyboard: Found x and y relative axes
(II) ORTEK Smartpad Keyboard: Found scroll wheel(s)
(II) ORTEK Smartpad Keyboard: Found keys
(II) ORTEK Smartpad Keyboard: Configuring as mouse
(II) ORTEK Smartpad Keyboard: Configuring as keyboard
(**) ORTEK Smartpad Keyboard: YAxisMapping: buttons 4 and 5
(**) ORTEK Smartpad Keyboard: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "gb"
(**) ORTEK Smartpad Keyboard: (accel) keeping acceleration scheme 1
(**) ORTEK Smartpad Keyboard: (accel) filter chain progression: 2.00
(**) ORTEK Smartpad Keyboard: (accel) filter stage 0: 20.00 ms
(**) ORTEK Smartpad Keyboard: (accel) set acceleration profile 0
(II) ORTEK Smartpad Keyboard: initialized for relative axes.
(II) config/hal: Adding input device A4Tech RF USB Receiver
(**) A4Tech RF USB Receiver: always reports core events
(**) A4Tech RF USB Receiver: Device: "/dev/input/event6"
(II) A4Tech RF USB Receiver: Found 12 mouse buttons
(II) A4Tech RF USB Receiver: Found x and y relative axes
(II) A4Tech RF USB Receiver: Found scroll wheel(s)
(II) A4Tech RF USB Receiver: Found keys
(II) A4Tech RF USB Receiver: Configuring as mouse
(II) A4Tech RF USB Receiver: Configuring as keyboard
(**) A4Tech RF USB Receiver: YAxisMapping: buttons 4 and 5
(**) A4Tech RF USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "gb"
(**) A4Tech RF USB Receiver: (accel) keeping acceleration scheme 1
(**) A4Tech RF USB Receiver: (accel) filter chain progression: 2.00
(**) A4Tech RF USB Receiver: (accel) filter stage 0: 20.00 ms
(**) A4Tech RF USB Receiver: (accel) set acceleration profile 0
(II) A4Tech RF USB Receiver: initialized for relative axes.
(II) config/hal: Adding input device A4Tech RF USB Receiver
(**) A4Tech RF USB Receiver: always reports core events
(**) A4Tech RF USB Receiver: Device: "/dev/input/event5"
(II) A4Tech RF USB Receiver: Found keys
(II) A4Tech RF USB Receiver: Configuring as keyboard
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "gb"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "gb"
(II) config/hal: Adding input device ORTEK Smartpad Keyboard
(**) ORTEK Smartpad Keyboard: always reports core events
(**) ORTEK Smartpad Keyboard: Device: "/dev/input/event3"
(II) ORTEK Smartpad Keyboard: Found keys
(II) ORTEK Smartpad Keyboard: Configuring as keyboard
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "gb"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "gb"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
(II) RADEON(0): EDID vendor "PHL", prod id 2080
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
(II) RADEON(0): EDID vendor "PHL", prod id 2080
(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Manufacturer: PHL  Model: 4650  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 71  vert.: 40
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.617 redY: 0.334   greenX: 0.283 greenY: 0.590
(II) RADEON(0): blueX: 0.143 blueY: 0.086   whiteX: 0.284 whiteY: 0.295
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 360  refresh: 85  vid: 55601
(II) RADEON(0): #1: hsize: 800  vsize 450  refresh: 85  vid: 55621
(II) RADEON(0): #2: hsize: 1024  vsize 576  refresh: 85  vid: 55649
(II) RADEON(0): #3: hsize: 1152  vsize 648  refresh: 75  vid: 53105
(II) RADEON(0): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.2 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 790 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 25.2 MHz   Image Size:  530 x 398 mm
(II) RADEON(0): h_active: 640  h_sync: 648  h_sync_end 744 h_blank_end 800 h_border: 8
(II) RADEON(0): v_active: 480  v_sync: 482  v_sync_end 484 v_blanking: 525 v_border: 8
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 27.0 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
(II) RADEON(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
(II) RADEON(0): Ranges: V min: 47 V max: 85 Hz, H min: 31 H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c504601010101
(II) RADEON(0): 	2b0f0103804728788a288e9e55489724
(II) RADEON(0): 	16484b256a0031d945d961d971cf81c0
(II) RADEON(0): 	010101010101a91a00a0500016303020
(II) RADEON(0): 	3700c48e21000018d60980a020e02d10
(II) RADEON(0): 	08602200128e210808188c0ad08a20e0
(II) RADEON(0): 	2d10103e9600c48e21000018000000fd
(II) RADEON(0): 	002f551f500e000a2020202020200104
(II) RADEON(0): 	02031a75470103040512931423090707
(II) RADEON(0): 	8301000065030c001000011d007251d0
(II) RADEON(0): 	1e206e285500c48e2100001e011d8018
(II) RADEON(0): 	711c1620582c2500c48e2100009e8c0a
(II) RADEON(0): 	d090204031200c405500c48e21000018
(II) RADEON(0): 	011d00bc52d01e20b8285540c48e2100
(II) RADEON(0): 	001e011d80d0721c1620102c2580c48e
(II) RADEON(0): 	2100009e000000ff0000000000000049
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: PHL  Model: 4650  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 71  vert.: 40
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.617 redY: 0.334   greenX: 0.283 greenY: 0.590
(II) RADEON(0): blueX: 0.143 blueY: 0.086   whiteX: 0.284 whiteY: 0.295
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 360  refresh: 85  vid: 55601
(II) RADEON(0): #1: hsize: 800  vsize 450  refresh: 85  vid: 55621
(II) RADEON(0): #2: hsize: 1024  vsize 576  refresh: 85  vid: 55649
(II) RADEON(0): #3: hsize: 1152  vsize 648  refresh: 75  vid: 53105
(II) RADEON(0): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.2 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 790 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 25.2 MHz   Image Size:  530 x 398 mm
(II) RADEON(0): h_active: 640  h_sync: 648  h_sync_end 744 h_blank_end 800 h_border: 8
(II) RADEON(0): v_active: 480  v_sync: 482  v_sync_end 484 v_blanking: 525 v_border: 8
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 27.0 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
(II) RADEON(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
(II) RADEON(0): Ranges: V min: 47 V max: 85 Hz, H min: 31 H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c504601010101
(II) RADEON(0): 	2b0f0103804728788a288e9e55489724
(II) RADEON(0): 	16484b256a0031d945d961d971cf81c0
(II) RADEON(0): 	010101010101a91a00a0500016303020
(II) RADEON(0): 	3700c48e21000018d60980a020e02d10
(II) RADEON(0): 	08602200128e210808188c0ad08a20e0
(II) RADEON(0): 	2d10103e9600c48e21000018000000fd
(II) RADEON(0): 	002f551f500e000a2020202020200104
(II) RADEON(0): 	02031a75470103040512931423090707
(II) RADEON(0): 	8301000065030c001000011d007251d0
(II) RADEON(0): 	1e206e285500c48e2100001e011d8018
(II) RADEON(0): 	711c1620582c2500c48e2100009e8c0a
(II) RADEON(0): 	d090204031200c405500c48e21000018
(II) RADEON(0): 	011d00bc52d01e20b8285540c48e2100
(II) RADEON(0): 	001e011d80d0721c1620102c2580c48e
(II) RADEON(0): 	2100009e000000ff0000000000000049
(II) RADEON(0): EDID vendor "PHL", prod id 18000
(II) RADEON(0): Not using mode "1280x768" (width too large for virtual size)
(II) RADEON(0): Not using mode "1152x648" (width too large for virtual size)
(II) RADEON(0): Not using mode "1280x720" (width too large for virtual size)
(II) RADEON(0): Printing probed modes for output DVI-0
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x576"x85.0   69.11  1024 1080 1184 1344  576 577 580 605 -hsync +vsync (51.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x450"x85.0   41.81  800 840 920 1040  450 451 454 473 -hsync +vsync (40.2 kHz)
(II) RADEON(0): Modeline "720x480"x59.9   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x60.0   25.18  640 648 744 800  480 482 484 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x360"x85.0   25.77  640 656 720 800  360 361 364 379 -hsync +vsync (32.2 kHz)
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
(II) RADEON(0): EDID vendor "PHL", prod id 2080
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
(II) RADEON(0): EDID vendor "PHL", prod id 2080
(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Manufacturer: PHL  Model: 4650  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 71  vert.: 40
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.617 redY: 0.334   greenX: 0.283 greenY: 0.590
(II) RADEON(0): blueX: 0.143 blueY: 0.086   whiteX: 0.284 whiteY: 0.295
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 360  refresh: 85  vid: 55601
(II) RADEON(0): #1: hsize: 800  vsize 450  refresh: 85  vid: 55621
(II) RADEON(0): #2: hsize: 1024  vsize 576  refresh: 85  vid: 55649
(II) RADEON(0): #3: hsize: 1152  vsize 648  refresh: 75  vid: 53105
(II) RADEON(0): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.2 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 790 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 25.2 MHz   Image Size:  530 x 398 mm
(II) RADEON(0): h_active: 640  h_sync: 648  h_sync_end 744 h_blank_end 800 h_border: 8
(II) RADEON(0): v_active: 480  v_sync: 482  v_sync_end 484 v_blanking: 525 v_border: 8
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 27.0 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
(II) RADEON(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
(II) RADEON(0): Ranges: V min: 47 V max: 85 Hz, H min: 31 H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c504601010101
(II) RADEON(0): 	2b0f0103804728788a288e9e55489724
(II) RADEON(0): 	16484b256a0031d945d961d971cf81c0
(II) RADEON(0): 	010101010101a91a00a0500016303020
(II) RADEON(0): 	3700c48e21000018d60980a020e02d10
(II) RADEON(0): 	08602200128e210808188c0ad08a20e0
(II) RADEON(0): 	2d10103e9600c48e21000018000000fd
(II) RADEON(0): 	002f551f500e000a2020202020200104
(II) RADEON(0): 	02031a75470103040512931423090707
(II) RADEON(0): 	8301000065030c001000011d007251d0
(II) RADEON(0): 	1e206e285500c48e2100001e011d8018
(II) RADEON(0): 	711c1620582c2500c48e2100009e8c0a
(II) RADEON(0): 	d090204031200c405500c48e21000018
(II) RADEON(0): 	011d00bc52d01e20b8285540c48e2100
(II) RADEON(0): 	001e011d80d0721c1620102c2580c48e
(II) RADEON(0): 	2100009e000000ff0000000000000049
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: PHL  Model: 4650  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 71  vert.: 40
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.617 redY: 0.334   greenX: 0.283 greenY: 0.590
(II) RADEON(0): blueX: 0.143 blueY: 0.086   whiteX: 0.284 whiteY: 0.295
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 360  refresh: 85  vid: 55601
(II) RADEON(0): #1: hsize: 800  vsize 450  refresh: 85  vid: 55621
(II) RADEON(0): #2: hsize: 1024  vsize 576  refresh: 85  vid: 55649
(II) RADEON(0): #3: hsize: 1152  vsize 648  refresh: 75  vid: 53105
(II) RADEON(0): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.2 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 790 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 25.2 MHz   Image Size:  530 x 398 mm
(II) RADEON(0): h_active: 640  h_sync: 648  h_sync_end 744 h_blank_end 800 h_border: 8
(II) RADEON(0): v_active: 480  v_sync: 482  v_sync_end 484 v_blanking: 525 v_border: 8
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 27.0 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
(II) RADEON(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
(II) RADEON(0): Ranges: V min: 47 V max: 85 Hz, H min: 31 H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c504601010101
(II) RADEON(0): 	2b0f0103804728788a288e9e55489724
(II) RADEON(0): 	16484b256a0031d945d961d971cf81c0
(II) RADEON(0): 	010101010101a91a00a0500016303020
(II) RADEON(0): 	3700c48e21000018d60980a020e02d10
(II) RADEON(0): 	08602200128e210808188c0ad08a20e0
(II) RADEON(0): 	2d10103e9600c48e21000018000000fd
(II) RADEON(0): 	002f551f500e000a2020202020200104
(II) RADEON(0): 	02031a75470103040512931423090707
(II) RADEON(0): 	8301000065030c001000011d007251d0
(II) RADEON(0): 	1e206e285500c48e2100001e011d8018
(II) RADEON(0): 	711c1620582c2500c48e2100009e8c0a
(II) RADEON(0): 	d090204031200c405500c48e21000018
(II) RADEON(0): 	011d00bc52d01e20b8285540c48e2100
(II) RADEON(0): 	001e011d80d0721c1620102c2580c48e
(II) RADEON(0): 	2100009e000000ff0000000000000049
(II) RADEON(0): EDID vendor "PHL", prod id 18000
(II) RADEON(0): Not using mode "1280x768" (width too large for virtual size)
(II) RADEON(0): Not using mode "1152x648" (width too large for virtual size)
(II) RADEON(0): Not using mode "1280x720" (width too large for virtual size)
(II) RADEON(0): Printing probed modes for output DVI-0
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x576"x85.0   69.11  1024 1080 1184 1344  576 577 580 605 -hsync +vsync (51.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x450"x85.0   41.81  800 840 920 1040  450 451 454 473 -hsync +vsync (40.2 kHz)
(II) RADEON(0): Modeline "720x480"x59.9   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x60.0   25.18  640 648 744 800  480 482 484 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x360"x85.0   25.77  640 656 720 800  360 361 364 379 -hsync +vsync (32.2 kHz)
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
(II) RADEON(0): EDID vendor "PHL", prod id 2080
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
(II) RADEON(0): EDID vendor "PHL", prod id 2080
(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Manufacturer: PHL  Model: 4650  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 71  vert.: 40
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.617 redY: 0.334   greenX: 0.283 greenY: 0.590
(II) RADEON(0): blueX: 0.143 blueY: 0.086   whiteX: 0.284 whiteY: 0.295
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 360  refresh: 85  vid: 55601
(II) RADEON(0): #1: hsize: 800  vsize 450  refresh: 85  vid: 55621
(II) RADEON(0): #2: hsize: 1024  vsize 576  refresh: 85  vid: 55649
(II) RADEON(0): #3: hsize: 1152  vsize 648  refresh: 75  vid: 53105
(II) RADEON(0): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.2 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 790 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 25.2 MHz   Image Size:  530 x 398 mm
(II) RADEON(0): h_active: 640  h_sync: 648  h_sync_end 744 h_blank_end 800 h_border: 8
(II) RADEON(0): v_active: 480  v_sync: 482  v_sync_end 484 v_blanking: 525 v_border: 8
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 27.0 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
(II) RADEON(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
(II) RADEON(0): Ranges: V min: 47 V max: 85 Hz, H min: 31 H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c504601010101
(II) RADEON(0): 	2b0f0103804728788a288e9e55489724
(II) RADEON(0): 	16484b256a0031d945d961d971cf81c0
(II) RADEON(0): 	010101010101a91a00a0500016303020
(II) RADEON(0): 	3700c48e21000018d60980a020e02d10
(II) RADEON(0): 	08602200128e210808188c0ad08a20e0
(II) RADEON(0): 	2d10103e9600c48e21000018000000fd
(II) RADEON(0): 	002f551f500e000a2020202020200104
(II) RADEON(0): 	02031a75470103040512931423090707
(II) RADEON(0): 	8301000065030c001000011d007251d0
(II) RADEON(0): 	1e206e285500c48e2100001e011d8018
(II) RADEON(0): 	711c1620582c2500c48e2100009e8c0a
(II) RADEON(0): 	d090204031200c405500c48e21000018
(II) RADEON(0): 	011d00bc52d01e20b8285540c48e2100
(II) RADEON(0): 	001e011d80d0721c1620102c2580c48e
(II) RADEON(0): 	2100009e000000ff0000000000000049
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: PHL  Model: 4650  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 71  vert.: 40
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.617 redY: 0.334   greenX: 0.283 greenY: 0.590
(II) RADEON(0): blueX: 0.143 blueY: 0.086   whiteX: 0.284 whiteY: 0.295
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 360  refresh: 85  vid: 55601
(II) RADEON(0): #1: hsize: 800  vsize 450  refresh: 85  vid: 55621
(II) RADEON(0): #2: hsize: 1024  vsize 576  refresh: 85  vid: 55649
(II) RADEON(0): #3: hsize: 1152  vsize 648  refresh: 75  vid: 53105
(II) RADEON(0): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.2 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 790 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 25.2 MHz   Image Size:  530 x 398 mm
(II) RADEON(0): h_active: 640  h_sync: 648  h_sync_end 744 h_blank_end 800 h_border: 8
(II) RADEON(0): v_active: 480  v_sync: 482  v_sync_end 484 v_blanking: 525 v_border: 8
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 27.0 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
(II) RADEON(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
(II) RADEON(0): Ranges: V min: 47 V max: 85 Hz, H min: 31 H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c504601010101
(II) RADEON(0): 	2b0f0103804728788a288e9e55489724
(II) RADEON(0): 	16484b256a0031d945d961d971cf81c0
(II) RADEON(0): 	010101010101a91a00a0500016303020
(II) RADEON(0): 	3700c48e21000018d60980a020e02d10
(II) RADEON(0): 	08602200128e210808188c0ad08a20e0
(II) RADEON(0): 	2d10103e9600c48e21000018000000fd
(II) RADEON(0): 	002f551f500e000a2020202020200104
(II) RADEON(0): 	02031a75470103040512931423090707
(II) RADEON(0): 	8301000065030c001000011d007251d0
(II) RADEON(0): 	1e206e285500c48e2100001e011d8018
(II) RADEON(0): 	711c1620582c2500c48e2100009e8c0a
(II) RADEON(0): 	d090204031200c405500c48e21000018
(II) RADEON(0): 	011d00bc52d01e20b8285540c48e2100
(II) RADEON(0): 	001e011d80d0721c1620102c2580c48e
(II) RADEON(0): 	2100009e000000ff0000000000000049
(II) RADEON(0): EDID vendor "PHL", prod id 18000
(II) RADEON(0): Not using mode "1280x768" (width too large for virtual size)
(II) RADEON(0): Not using mode "1152x648" (width too large for virtual size)
(II) RADEON(0): Not using mode "1280x720" (width too large for virtual size)
(II) RADEON(0): Printing probed modes for output DVI-0
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x576"x85.0   69.11  1024 1080 1184 1344  576 577 580 605 -hsync +vsync (51.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x450"x85.0   41.81  800 840 920 1040  450 451 454 473 -hsync +vsync (40.2 kHz)
(II) RADEON(0): Modeline "720x480"x59.9   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x60.0   25.18  640 648 744 800  480 482 484 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x360"x85.0   25.77  640 656 720 800  360 361 364 379 -hsync +vsync (32.2 kHz)
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
(II) RADEON(0): EDID vendor "PHL", prod id 2080
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
(II) RADEON(0): EDID vendor "PHL", prod id 2080
(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Manufacturer: PHL  Model: 4650  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 71  vert.: 40
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.617 redY: 0.334   greenX: 0.283 greenY: 0.590
(II) RADEON(0): blueX: 0.143 blueY: 0.086   whiteX: 0.284 whiteY: 0.295
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 360  refresh: 85  vid: 55601
(II) RADEON(0): #1: hsize: 800  vsize 450  refresh: 85  vid: 55621
(II) RADEON(0): #2: hsize: 1024  vsize 576  refresh: 85  vid: 55649
(II) RADEON(0): #3: hsize: 1152  vsize 648  refresh: 75  vid: 53105
(II) RADEON(0): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.2 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 790 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 25.2 MHz   Image Size:  530 x 398 mm
(II) RADEON(0): h_active: 640  h_sync: 648  h_sync_end 744 h_blank_end 800 h_border: 8
(II) RADEON(0): v_active: 480  v_sync: 482  v_sync_end 484 v_blanking: 525 v_border: 8
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 27.0 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
(II) RADEON(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
(II) RADEON(0): Ranges: V min: 47 V max: 85 Hz, H min: 31 H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c504601010101
(II) RADEON(0): 	2b0f0103804728788a288e9e55489724
(II) RADEON(0): 	16484b256a0031d945d961d971cf81c0
(II) RADEON(0): 	010101010101a91a00a0500016303020
(II) RADEON(0): 	3700c48e21000018d60980a020e02d10
(II) RADEON(0): 	08602200128e210808188c0ad08a20e0
(II) RADEON(0): 	2d10103e9600c48e21000018000000fd
(II) RADEON(0): 	002f551f500e000a2020202020200104
(II) RADEON(0): 	02031a75470103040512931423090707
(II) RADEON(0): 	8301000065030c001000011d007251d0
(II) RADEON(0): 	1e206e285500c48e2100001e011d8018
(II) RADEON(0): 	711c1620582c2500c48e2100009e8c0a
(II) RADEON(0): 	d090204031200c405500c48e21000018
(II) RADEON(0): 	011d00bc52d01e20b8285540c48e2100
(II) RADEON(0): 	001e011d80d0721c1620102c2580c48e
(II) RADEON(0): 	2100009e000000ff0000000000000049
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: PHL  Model: 4650  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 71  vert.: 40
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.617 redY: 0.334   greenX: 0.283 greenY: 0.590
(II) RADEON(0): blueX: 0.143 blueY: 0.086   whiteX: 0.284 whiteY: 0.295
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 360  refresh: 85  vid: 55601
(II) RADEON(0): #1: hsize: 800  vsize 450  refresh: 85  vid: 55621
(II) RADEON(0): #2: hsize: 1024  vsize 576  refresh: 85  vid: 55649
(II) RADEON(0): #3: hsize: 1152  vsize 648  refresh: 75  vid: 53105
(II) RADEON(0): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.2 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 790 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 25.2 MHz   Image Size:  530 x 398 mm
(II) RADEON(0): h_active: 640  h_sync: 648  h_sync_end 744 h_blank_end 800 h_border: 8
(II) RADEON(0): v_active: 480  v_sync: 482  v_sync_end 484 v_blanking: 525 v_border: 8
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 27.0 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
(II) RADEON(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
(II) RADEON(0): Ranges: V min: 47 V max: 85 Hz, H min: 31 H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c504601010101
(II) RADEON(0): 	2b0f0103804728788a288e9e55489724
(II) RADEON(0): 	16484b256a0031d945d961d971cf81c0
(II) RADEON(0): 	010101010101a91a00a0500016303020
(II) RADEON(0): 	3700c48e21000018d60980a020e02d10
(II) RADEON(0): 	08602200128e210808188c0ad08a20e0
(II) RADEON(0): 	2d10103e9600c48e21000018000000fd
(II) RADEON(0): 	002f551f500e000a2020202020200104
(II) RADEON(0): 	02031a75470103040512931423090707
(II) RADEON(0): 	8301000065030c001000011d007251d0
(II) RADEON(0): 	1e206e285500c48e2100001e011d8018
(II) RADEON(0): 	711c1620582c2500c48e2100009e8c0a
(II) RADEON(0): 	d090204031200c405500c48e21000018
(II) RADEON(0): 	011d00bc52d01e20b8285540c48e2100
(II) RADEON(0): 	001e011d80d0721c1620102c2580c48e
(II) RADEON(0): 	2100009e000000ff0000000000000049
(II) RADEON(0): EDID vendor "PHL", prod id 18000
(II) RADEON(0): Not using mode "1280x768" (width too large for virtual size)
(II) RADEON(0): Not using mode "1152x648" (width too large for virtual size)
(II) RADEON(0): Not using mode "1280x720" (width too large for virtual size)
(II) RADEON(0): Printing probed modes for output DVI-0
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x576"x85.0   69.11  1024 1080 1184 1344  576 577 580 605 -hsync +vsync (51.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x450"x85.0   41.81  800 840 920 1040  450 451 454 473 -hsync +vsync (40.2 kHz)
(II) RADEON(0): Modeline "720x480"x59.9   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x60.0   25.18  640 648 744 800  480 482 484 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x360"x85.0   25.77  640 656 720 800  360 361 364 379 -hsync +vsync (32.2 kHz)
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
(II) RADEON(0): EDID vendor "PHL", prod id 2080
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
(II) RADEON(0): EDID vendor "PHL", prod id 2080
(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Manufacturer: PHL  Model: 4650  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 71  vert.: 40
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.617 redY: 0.334   greenX: 0.283 greenY: 0.590
(II) RADEON(0): blueX: 0.143 blueY: 0.086   whiteX: 0.284 whiteY: 0.295
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 360  refresh: 85  vid: 55601
(II) RADEON(0): #1: hsize: 800  vsize 450  refresh: 85  vid: 55621
(II) RADEON(0): #2: hsize: 1024  vsize 576  refresh: 85  vid: 55649
(II) RADEON(0): #3: hsize: 1152  vsize 648  refresh: 75  vid: 53105
(II) RADEON(0): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.2 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 790 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 25.2 MHz   Image Size:  530 x 398 mm
(II) RADEON(0): h_active: 640  h_sync: 648  h_sync_end 744 h_blank_end 800 h_border: 8
(II) RADEON(0): v_active: 480  v_sync: 482  v_sync_end 484 v_blanking: 525 v_border: 8
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 27.0 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
(II) RADEON(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
(II) RADEON(0): Ranges: V min: 47 V max: 85 Hz, H min: 31 H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c504601010101
(II) RADEON(0): 	2b0f0103804728788a288e9e55489724
(II) RADEON(0): 	16484b256a0031d945d961d971cf81c0
(II) RADEON(0): 	010101010101a91a00a0500016303020
(II) RADEON(0): 	3700c48e21000018d60980a020e02d10
(II) RADEON(0): 	08602200128e210808188c0ad08a20e0
(II) RADEON(0): 	2d10103e9600c48e21000018000000fd
(II) RADEON(0): 	002f551f500e000a2020202020200104
(II) RADEON(0): 	02031a75470103040512931423090707
(II) RADEON(0): 	8301000065030c001000011d007251d0
(II) RADEON(0): 	1e206e285500c48e2100001e011d8018
(II) RADEON(0): 	711c1620582c2500c48e2100009e8c0a
(II) RADEON(0): 	d090204031200c405500c48e21000018
(II) RADEON(0): 	011d00bc52d01e20b8285540c48e2100
(II) RADEON(0): 	001e011d80d0721c1620102c2580c48e
(II) RADEON(0): 	2100009e000000ff0000000000000049
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: PHL  Model: 4650  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 71  vert.: 40
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.617 redY: 0.334   greenX: 0.283 greenY: 0.590
(II) RADEON(0): blueX: 0.143 blueY: 0.086   whiteX: 0.284 whiteY: 0.295
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 360  refresh: 85  vid: 55601
(II) RADEON(0): #1: hsize: 800  vsize 450  refresh: 85  vid: 55621
(II) RADEON(0): #2: hsize: 1024  vsize 576  refresh: 85  vid: 55649
(II) RADEON(0): #3: hsize: 1152  vsize 648  refresh: 75  vid: 53105
(II) RADEON(0): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.2 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 790 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 25.2 MHz   Image Size:  530 x 398 mm
(II) RADEON(0): h_active: 640  h_sync: 648  h_sync_end 744 h_blank_end 800 h_border: 8
(II) RADEON(0): v_active: 480  v_sync: 482  v_sync_end 484 v_blanking: 525 v_border: 8
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 27.0 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
(II) RADEON(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
(II) RADEON(0): Ranges: V min: 47 V max: 85 Hz, H min: 31 H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c504601010101
(II) RADEON(0): 	2b0f0103804728788a288e9e55489724
(II) RADEON(0): 	16484b256a0031d945d961d971cf81c0
(II) RADEON(0): 	010101010101a91a00a0500016303020
(II) RADEON(0): 	3700c48e21000018d60980a020e02d10
(II) RADEON(0): 	08602200128e210808188c0ad08a20e0
(II) RADEON(0): 	2d10103e9600c48e21000018000000fd
(II) RADEON(0): 	002f551f500e000a2020202020200104
(II) RADEON(0): 	02031a75470103040512931423090707
(II) RADEON(0): 	8301000065030c001000011d007251d0
(II) RADEON(0): 	1e206e285500c48e2100001e011d8018
(II) RADEON(0): 	711c1620582c2500c48e2100009e8c0a
(II) RADEON(0): 	d090204031200c405500c48e21000018
(II) RADEON(0): 	011d00bc52d01e20b8285540c48e2100
(II) RADEON(0): 	001e011d80d0721c1620102c2580c48e
(II) RADEON(0): 	2100009e000000ff0000000000000049
(II) RADEON(0): EDID vendor "PHL", prod id 18000
(II) RADEON(0): Not using mode "1280x768" (width too large for virtual size)
(II) RADEON(0): Not using mode "1152x648" (width too large for virtual size)
(II) RADEON(0): Not using mode "1280x720" (width too large for virtual size)
(II) RADEON(0): Printing probed modes for output DVI-0
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x576"x85.0   69.11  1024 1080 1184 1344  576 577 580 605 -hsync +vsync (51.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x450"x85.0   41.81  800 840 920 1040  450 451 454 473 -hsync +vsync (40.2 kHz)
(II) RADEON(0): Modeline "720x480"x59.9   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x60.0   25.18  640 648 744 800  480 482 484 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x360"x85.0   25.77  640 656 720 800  360 361 364 379 -hsync +vsync (32.2 kHz)
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
(II) RADEON(0): EDID vendor "PHL", prod id 2080
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
(II) RADEON(0): EDID vendor "PHL", prod id 2080
(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Manufacturer: PHL  Model: 4650  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 71  vert.: 40
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.617 redY: 0.334   greenX: 0.283 greenY: 0.590
(II) RADEON(0): blueX: 0.143 blueY: 0.086   whiteX: 0.284 whiteY: 0.295
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 360  refresh: 85  vid: 55601
(II) RADEON(0): #1: hsize: 800  vsize 450  refresh: 85  vid: 55621
(II) RADEON(0): #2: hsize: 1024  vsize 576  refresh: 85  vid: 55649
(II) RADEON(0): #3: hsize: 1152  vsize 648  refresh: 75  vid: 53105
(II) RADEON(0): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.2 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 790 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 25.2 MHz   Image Size:  530 x 398 mm
(II) RADEON(0): h_active: 640  h_sync: 648  h_sync_end 744 h_blank_end 800 h_border: 8
(II) RADEON(0): v_active: 480  v_sync: 482  v_sync_end 484 v_blanking: 525 v_border: 8
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 27.0 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
(II) RADEON(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
(II) RADEON(0): Ranges: V min: 47 V max: 85 Hz, H min: 31 H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c504601010101
(II) RADEON(0): 	2b0f0103804728788a288e9e55489724
(II) RADEON(0): 	16484b256a0031d945d961d971cf81c0
(II) RADEON(0): 	010101010101a91a00a0500016303020
(II) RADEON(0): 	3700c48e21000018d60980a020e02d10
(II) RADEON(0): 	08602200128e210808188c0ad08a20e0
(II) RADEON(0): 	2d10103e9600c48e21000018000000fd
(II) RADEON(0): 	002f551f500e000a2020202020200104
(II) RADEON(0): 	02031a75470103040512931423090707
(II) RADEON(0): 	8301000065030c001000011d007251d0
(II) RADEON(0): 	1e206e285500c48e2100001e011d8018
(II) RADEON(0): 	711c1620582c2500c48e2100009e8c0a
(II) RADEON(0): 	d090204031200c405500c48e21000018
(II) RADEON(0): 	011d00bc52d01e20b8285540c48e2100
(II) RADEON(0): 	001e011d80d0721c1620102c2580c48e
(II) RADEON(0): 	2100009e000000ff0000000000000049
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: PHL  Model: 4650  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 71  vert.: 40
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.617 redY: 0.334   greenX: 0.283 greenY: 0.590
(II) RADEON(0): blueX: 0.143 blueY: 0.086   whiteX: 0.284 whiteY: 0.295
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 360  refresh: 85  vid: 55601
(II) RADEON(0): #1: hsize: 800  vsize 450  refresh: 85  vid: 55621
(II) RADEON(0): #2: hsize: 1024  vsize 576  refresh: 85  vid: 55649
(II) RADEON(0): #3: hsize: 1152  vsize 648  refresh: 75  vid: 53105
(II) RADEON(0): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.2 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 790 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 25.2 MHz   Image Size:  530 x 398 mm
(II) RADEON(0): h_active: 640  h_sync: 648  h_sync_end 744 h_blank_end 800 h_border: 8
(II) RADEON(0): v_active: 480  v_sync: 482  v_sync_end 484 v_blanking: 525 v_border: 8
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 27.0 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
(II) RADEON(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
(II) RADEON(0): Ranges: V min: 47 V max: 85 Hz, H min: 31 H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c504601010101
(II) RADEON(0): 	2b0f0103804728788a288e9e55489724
(II) RADEON(0): 	16484b256a0031d945d961d971cf81c0
(II) RADEON(0): 	010101010101a91a00a0500016303020
(II) RADEON(0): 	3700c48e21000018d60980a020e02d10
(II) RADEON(0): 	08602200128e210808188c0ad08a20e0
(II) RADEON(0): 	2d10103e9600c48e21000018000000fd
(II) RADEON(0): 	002f551f500e000a2020202020200104
(II) RADEON(0): 	02031a75470103040512931423090707
(II) RADEON(0): 	8301000065030c001000011d007251d0
(II) RADEON(0): 	1e206e285500c48e2100001e011d8018
(II) RADEON(0): 	711c1620582c2500c48e2100009e8c0a
(II) RADEON(0): 	d090204031200c405500c48e21000018
(II) RADEON(0): 	011d00bc52d01e20b8285540c48e2100
(II) RADEON(0): 	001e011d80d0721c1620102c2580c48e
(II) RADEON(0): 	2100009e000000ff0000000000000049
(II) RADEON(0): EDID vendor "PHL", prod id 18000
(II) RADEON(0): Not using mode "1280x768" (width too large for virtual size)
(II) RADEON(0): Not using mode "1152x648" (width too large for virtual size)
(II) RADEON(0): Not using mode "1280x720" (width too large for virtual size)
(II) RADEON(0): Printing probed modes for output DVI-0
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x576"x85.0   69.11  1024 1080 1184 1344  576 577 580 605 -hsync +vsync (51.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x450"x85.0   41.81  800 840 920 1040  450 451 454 473 -hsync +vsync (40.2 kHz)
(II) RADEON(0): Modeline "720x480"x59.9   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x60.0   25.18  640 648 744 800  480 482 484 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x360"x85.0   25.77  640 656 720 800  360 361 364 379 -hsync +vsync (32.2 kHz)
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
disable TVDAC
disable FP2
init memmap
init common
init crtc2
init pll2
freq: 78750000
best_freq: 78760000
best_feedback_div: 44
best_frac_feedback_div: 0
best_ref_div: 2
best_post_div: 4
restore memmap
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x5fff5800 0x5fff5800
(II) RADEON(0):   MC_AGP_LOCATION  : 0xe07fe000
restore common
restore crtc2
restore pll2
finished PLL2
set FP2
enable TVDAC
enable FP2
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
(II) RADEON(0): EDID vendor "PHL", prod id 2080
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
(II) RADEON(0): EDID vendor "PHL", prod id 2080
(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Manufacturer: PHL  Model: 4650  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 71  vert.: 40
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.617 redY: 0.334   greenX: 0.283 greenY: 0.590
(II) RADEON(0): blueX: 0.143 blueY: 0.086   whiteX: 0.284 whiteY: 0.295
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 360  refresh: 85  vid: 55601
(II) RADEON(0): #1: hsize: 800  vsize 450  refresh: 85  vid: 55621
(II) RADEON(0): #2: hsize: 1024  vsize 576  refresh: 85  vid: 55649
(II) RADEON(0): #3: hsize: 1152  vsize 648  refresh: 75  vid: 53105
(II) RADEON(0): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.2 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 790 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 25.2 MHz   Image Size:  530 x 398 mm
(II) RADEON(0): h_active: 640  h_sync: 648  h_sync_end 744 h_blank_end 800 h_border: 8
(II) RADEON(0): v_active: 480  v_sync: 482  v_sync_end 484 v_blanking: 525 v_border: 8
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 27.0 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
(II) RADEON(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
(II) RADEON(0): Ranges: V min: 47 V max: 85 Hz, H min: 31 H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c504601010101
(II) RADEON(0): 	2b0f0103804728788a288e9e55489724
(II) RADEON(0): 	16484b256a0031d945d961d971cf81c0
(II) RADEON(0): 	010101010101a91a00a0500016303020
(II) RADEON(0): 	3700c48e21000018d60980a020e02d10
(II) RADEON(0): 	08602200128e210808188c0ad08a20e0
(II) RADEON(0): 	2d10103e9600c48e21000018000000fd
(II) RADEON(0): 	002f551f500e000a2020202020200104
(II) RADEON(0): 	02031a75470103040512931423090707
(II) RADEON(0): 	8301000065030c001000011d007251d0
(II) RADEON(0): 	1e206e285500c48e2100001e011d8018
(II) RADEON(0): 	711c1620582c2500c48e2100009e8c0a
(II) RADEON(0): 	d090204031200c405500c48e21000018
(II) RADEON(0): 	011d00bc52d01e20b8285540c48e2100
(II) RADEON(0): 	001e011d80d0721c1620102c2580c48e
(II) RADEON(0): 	2100009e000000ff0000000000000049
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: PHL  Model: 4650  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 71  vert.: 40
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.617 redY: 0.334   greenX: 0.283 greenY: 0.590
(II) RADEON(0): blueX: 0.143 blueY: 0.086   whiteX: 0.284 whiteY: 0.295
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 360  refresh: 85  vid: 55601
(II) RADEON(0): #1: hsize: 800  vsize 450  refresh: 85  vid: 55621
(II) RADEON(0): #2: hsize: 1024  vsize 576  refresh: 85  vid: 55649
(II) RADEON(0): #3: hsize: 1152  vsize 648  refresh: 75  vid: 53105
(II) RADEON(0): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.2 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 790 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 25.2 MHz   Image Size:  530 x 398 mm
(II) RADEON(0): h_active: 640  h_sync: 648  h_sync_end 744 h_blank_end 800 h_border: 8
(II) RADEON(0): v_active: 480  v_sync: 482  v_sync_end 484 v_blanking: 525 v_border: 8
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 27.0 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
(II) RADEON(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
(II) RADEON(0): Ranges: V min: 47 V max: 85 Hz, H min: 31 H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c504601010101
(II) RADEON(0): 	2b0f0103804728788a288e9e55489724
(II) RADEON(0): 	16484b256a0031d945d961d971cf81c0
(II) RADEON(0): 	010101010101a91a00a0500016303020
(II) RADEON(0): 	3700c48e21000018d60980a020e02d10
(II) RADEON(0): 	08602200128e210808188c0ad08a20e0
(II) RADEON(0): 	2d10103e9600c48e21000018000000fd
(II) RADEON(0): 	002f551f500e000a2020202020200104
(II) RADEON(0): 	02031a75470103040512931423090707
(II) RADEON(0): 	8301000065030c001000011d007251d0
(II) RADEON(0): 	1e206e285500c48e2100001e011d8018
(II) RADEON(0): 	711c1620582c2500c48e2100009e8c0a
(II) RADEON(0): 	d090204031200c405500c48e21000018
(II) RADEON(0): 	011d00bc52d01e20b8285540c48e2100
(II) RADEON(0): 	001e011d80d0721c1620102c2580c48e
(II) RADEON(0): 	2100009e000000ff0000000000000049
(II) RADEON(0): EDID vendor "PHL", prod id 18000
(II) RADEON(0): Not using mode "1280x768" (width too large for virtual size)
(II) RADEON(0): Not using mode "1152x648" (width too large for virtual size)
(II) RADEON(0): Not using mode "1280x720" (width too large for virtual size)
(II) RADEON(0): Printing probed modes for output DVI-0
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x576"x85.0   69.11  1024 1080 1184 1344  576 577 580 605 -hsync +vsync (51.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x450"x85.0   41.81  800 840 920 1040  450 451 454 473 -hsync +vsync (40.2 kHz)
(II) RADEON(0): Modeline "720x480"x59.9   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x60.0   25.18  640 648 744 800  480 482 484 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x360"x85.0   25.77  640 656 720 800  360 361 364 379 -hsync +vsync (32.2 kHz)
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
(II) RADEON(0): EDID vendor "PHL", prod id 2080
(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Manufacturer: PHL  Model: 4650  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 71  vert.: 40
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.617 redY: 0.334   greenX: 0.283 greenY: 0.590
(II) RADEON(0): blueX: 0.143 blueY: 0.086   whiteX: 0.284 whiteY: 0.295
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 360  refresh: 85  vid: 55601
(II) RADEON(0): #1: hsize: 800  vsize 450  refresh: 85  vid: 55621
(II) RADEON(0): #2: hsize: 1024  vsize 576  refresh: 85  vid: 55649
(II) RADEON(0): #3: hsize: 1152  vsize 648  refresh: 75  vid: 53105
(II) RADEON(0): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.2 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 790 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 25.2 MHz   Image Size:  530 x 398 mm
(II) RADEON(0): h_active: 640  h_sync: 648  h_sync_end 744 h_blank_end 800 h_border: 8
(II) RADEON(0): v_active: 480  v_sync: 482  v_sync_end 484 v_blanking: 525 v_border: 8
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 27.0 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
(II) RADEON(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
(II) RADEON(0): Ranges: V min: 47 V max: 85 Hz, H min: 31 H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c504601010101
(II) RADEON(0): 	2b0f0103804728788a288e9e55489724
(II) RADEON(0): 	16484b256a0031d945d961d971cf81c0
(II) RADEON(0): 	010101010101a91a00a0500016303020
(II) RADEON(0): 	3700c48e21000018d60980a020e02d10
(II) RADEON(0): 	08602200128e210808188c0ad08a20e0
(II) RADEON(0): 	2d10103e9600c48e21000018000000fd
(II) RADEON(0): 	002f551f500e000a2020202020200104
(II) RADEON(0): 	02031a75470103040512931423090707
(II) RADEON(0): 	8301000065030c001000011d007251d0
(II) RADEON(0): 	1e206e285500c48e2100001e011d8018
(II) RADEON(0): 	711c1620582c2500c48e2100009e8c0a
(II) RADEON(0): 	d090204031200c405500c48e21000018
(II) RADEON(0): 	011d00bc52d01e20b8285540c48e2100
(II) RADEON(0): 	001e011d80d0721c1620102c2580c48e
(II) RADEON(0): 	2100009e000000ff0000000000000049
(II) RADEON(0): EDID vendor "PHL", prod id 18000
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x768"x0.0   68.25  1280 1328 1360 1440  768 771 778 790 -hsync -vsync (47.4 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 648 744 800  480 482 484 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "640x360"x85.0   25.77  640 656 720 800  360 361 364 379 -hsync +vsync (32.2 kHz)
(II) RADEON(0): Modeline "800x450"x85.0   41.81  800 840 920 1040  450 451 454 473 -hsync +vsync (40.2 kHz)
(II) RADEON(0): Modeline "1024x576"x85.0   69.11  1024 1080 1184 1344  576 577 580 605 -hsync +vsync (51.4 kHz)
(II) RADEON(0): Modeline "1152x648"x75.0   77.18  1152 1216 1336 1520  648 649 652 677 -hsync +vsync (50.8 kHz)
(II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: PHL  Model: 4650  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 71  vert.: 40
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.617 redY: 0.334   greenX: 0.283 greenY: 0.590
(II) RADEON(0): blueX: 0.143 blueY: 0.086   whiteX: 0.284 whiteY: 0.295
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 360  refresh: 85  vid: 55601
(II) RADEON(0): #1: hsize: 800  vsize 450  refresh: 85  vid: 55621
(II) RADEON(0): #2: hsize: 1024  vsize 576  refresh: 85  vid: 55649
(II) RADEON(0): #3: hsize: 1152  vsize 648  refresh: 75  vid: 53105
(II) RADEON(0): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.2 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 790 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 25.2 MHz   Image Size:  530 x 398 mm
(II) RADEON(0): h_active: 640  h_sync: 648  h_sync_end 744 h_blank_end 800 h_border: 8
(II) RADEON(0): v_active: 480  v_sync: 482  v_sync_end 484 v_blanking: 525 v_border: 8
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 27.0 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
(II) RADEON(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
(II) RADEON(0): Ranges: V min: 47 V max: 85 Hz, H min: 31 H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c504601010101
(II) RADEON(0): 	2b0f0103804728788a288e9e55489724
(II) RADEON(0): 	16484b256a0031d945d961d971cf81c0
(II) RADEON(0): 	010101010101a91a00a0500016303020
(II) RADEON(0): 	3700c48e21000018d60980a020e02d10
(II) RADEON(0): 	08602200128e210808188c0ad08a20e0
(II) RADEON(0): 	2d10103e9600c48e21000018000000fd
(II) RADEON(0): 	002f551f500e000a2020202020200104
(II) RADEON(0): 	02031a75470103040512931423090707
(II) RADEON(0): 	8301000065030c001000011d007251d0
(II) RADEON(0): 	1e206e285500c48e2100001e011d8018
(II) RADEON(0): 	711c1620582c2500c48e2100009e8c0a
(II) RADEON(0): 	d090204031200c405500c48e21000018
(II) RADEON(0): 	011d00bc52d01e20b8285540c48e2100
(II) RADEON(0): 	001e011d80d0721c1620102c2580c48e
(II) RADEON(0): 	2100009e000000ff0000000000000049
(II) RADEON(0): EDID vendor "PHL", prod id 18000
(II) RADEON(0): Not using mode "1280x768" (width too large for virtual size)
(II) RADEON(0): Not using mode "1152x648" (width too large for virtual size)
(II) RADEON(0): Not using mode "1280x720" (width too large for virtual size)
(II) RADEON(0): Printing probed modes for output DVI-0
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x576"x85.0   69.11  1024 1080 1184 1344  576 577 580 605 -hsync +vsync (51.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x450"x85.0   41.81  800 840 920 1040  450 451 454 473 -hsync +vsync (40.2 kHz)
(II) RADEON(0): Modeline "720x480"x59.9   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x60.0   25.18  640 648 744 800  480 482 484 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x360"x85.0   25.77  640 656 720 800  360 361 364 379 -hsync +vsync (32.2 kHz)
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
(II) RADEON(0): EDID vendor "PHL", prod id 2080
(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Manufacturer: PHL  Model: 4650  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 71  vert.: 40
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.617 redY: 0.334   greenX: 0.283 greenY: 0.590
(II) RADEON(0): blueX: 0.143 blueY: 0.086   whiteX: 0.284 whiteY: 0.295
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 360  refresh: 85  vid: 55601
(II) RADEON(0): #1: hsize: 800  vsize 450  refresh: 85  vid: 55621
(II) RADEON(0): #2: hsize: 1024  vsize 576  refresh: 85  vid: 55649
(II) RADEON(0): #3: hsize: 1152  vsize 648  refresh: 75  vid: 53105
(II) RADEON(0): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.2 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 790 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 25.2 MHz   Image Size:  530 x 398 mm
(II) RADEON(0): h_active: 640  h_sync: 648  h_sync_end 744 h_blank_end 800 h_border: 8
(II) RADEON(0): v_active: 480  v_sync: 482  v_sync_end 484 v_blanking: 525 v_border: 8
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 27.0 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
(II) RADEON(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
(II) RADEON(0): Ranges: V min: 47 V max: 85 Hz, H min: 31 H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c504601010101
(II) RADEON(0): 	2b0f0103804728788a288e9e55489724
(II) RADEON(0): 	16484b256a0031d945d961d971cf81c0
(II) RADEON(0): 	010101010101a91a00a0500016303020
(II) RADEON(0): 	3700c48e21000018d60980a020e02d10
(II) RADEON(0): 	08602200128e210808188c0ad08a20e0
(II) RADEON(0): 	2d10103e9600c48e21000018000000fd
(II) RADEON(0): 	002f551f500e000a2020202020200104
(II) RADEON(0): 	02031a75470103040512931423090707
(II) RADEON(0): 	8301000065030c001000011d007251d0
(II) RADEON(0): 	1e206e285500c48e2100001e011d8018
(II) RADEON(0): 	711c1620582c2500c48e2100009e8c0a
(II) RADEON(0): 	d090204031200c405500c48e21000018
(II) RADEON(0): 	011d00bc52d01e20b8285540c48e2100
(II) RADEON(0): 	001e011d80d0721c1620102c2580c48e
(II) RADEON(0): 	2100009e000000ff0000000000000049
(II) RADEON(0): EDID vendor "PHL", prod id 18000
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x768"x0.0   68.25  1280 1328 1360 1440  768 771 778 790 -hsync -vsync (47.4 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 648 744 800  480 482 484 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "640x360"x85.0   25.77  640 656 720 800  360 361 364 379 -hsync +vsync (32.2 kHz)
(II) RADEON(0): Modeline "800x450"x85.0   41.81  800 840 920 1040  450 451 454 473 -hsync +vsync (40.2 kHz)
(II) RADEON(0): Modeline "1024x576"x85.0   69.11  1024 1080 1184 1344  576 577 580 605 -hsync +vsync (51.4 kHz)
(II) RADEON(0): Modeline "1152x648"x75.0   77.18  1152 1216 1336 1520  648 649 652 677 -hsync +vsync (50.8 kHz)
(II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: PHL  Model: 4650  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 71  vert.: 40
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.617 redY: 0.334   greenX: 0.283 greenY: 0.590
(II) RADEON(0): blueX: 0.143 blueY: 0.086   whiteX: 0.284 whiteY: 0.295
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 360  refresh: 85  vid: 55601
(II) RADEON(0): #1: hsize: 800  vsize 450  refresh: 85  vid: 55621
(II) RADEON(0): #2: hsize: 1024  vsize 576  refresh: 85  vid: 55649
(II) RADEON(0): #3: hsize: 1152  vsize 648  refresh: 75  vid: 53105
(II) RADEON(0): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.2 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 790 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 25.2 MHz   Image Size:  530 x 398 mm
(II) RADEON(0): h_active: 640  h_sync: 648  h_sync_end 744 h_blank_end 800 h_border: 8
(II) RADEON(0): v_active: 480  v_sync: 482  v_sync_end 484 v_blanking: 525 v_border: 8
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 27.0 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
(II) RADEON(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
(II) RADEON(0): Ranges: V min: 47 V max: 85 Hz, H min: 31 H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c504601010101
(II) RADEON(0): 	2b0f0103804728788a288e9e55489724
(II) RADEON(0): 	16484b256a0031d945d961d971cf81c0
(II) RADEON(0): 	010101010101a91a00a0500016303020
(II) RADEON(0): 	3700c48e21000018d60980a020e02d10
(II) RADEON(0): 	08602200128e210808188c0ad08a20e0
(II) RADEON(0): 	2d10103e9600c48e21000018000000fd
(II) RADEON(0): 	002f551f500e000a2020202020200104
(II) RADEON(0): 	02031a75470103040512931423090707
(II) RADEON(0): 	8301000065030c001000011d007251d0
(II) RADEON(0): 	1e206e285500c48e2100001e011d8018
(II) RADEON(0): 	711c1620582c2500c48e2100009e8c0a
(II) RADEON(0): 	d090204031200c405500c48e21000018
(II) RADEON(0): 	011d00bc52d01e20b8285540c48e2100
(II) RADEON(0): 	001e011d80d0721c1620102c2580c48e
(II) RADEON(0): 	2100009e000000ff0000000000000049
(II) RADEON(0): EDID vendor "PHL", prod id 18000
(II) RADEON(0): Not using mode "1280x768" (width too large for virtual size)
(II) RADEON(0): Not using mode "1152x648" (width too large for virtual size)
(II) RADEON(0): Not using mode "1280x720" (width too large for virtual size)
(II) RADEON(0): Printing probed modes for output DVI-0
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x576"x85.0   69.11  1024 1080 1184 1344  576 577 580 605 -hsync +vsync (51.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x450"x85.0   41.81  800 840 920 1040  450 451 454 473 -hsync +vsync (40.2 kHz)
(II) RADEON(0): Modeline "720x480"x59.9   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x60.0   25.18  640 648 744 800  480 482 484 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x360"x85.0   25.77  640 656 720 800  360 361 364 379 -hsync +vsync (32.2 kHz)
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
(II) RADEON(0): EDID vendor "PHL", prod id 2080
(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Manufacturer: PHL  Model: 4650  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 71  vert.: 40
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.617 redY: 0.334   greenX: 0.283 greenY: 0.590
(II) RADEON(0): blueX: 0.143 blueY: 0.086   whiteX: 0.284 whiteY: 0.295
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 360  refresh: 85  vid: 55601
(II) RADEON(0): #1: hsize: 800  vsize 450  refresh: 85  vid: 55621
(II) RADEON(0): #2: hsize: 1024  vsize 576  refresh: 85  vid: 55649
(II) RADEON(0): #3: hsize: 1152  vsize 648  refresh: 75  vid: 53105
(II) RADEON(0): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.2 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 790 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 25.2 MHz   Image Size:  530 x 398 mm
(II) RADEON(0): h_active: 640  h_sync: 648  h_sync_end 744 h_blank_end 800 h_border: 8
(II) RADEON(0): v_active: 480  v_sync: 482  v_sync_end 484 v_blanking: 525 v_border: 8
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 27.0 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
(II) RADEON(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
(II) RADEON(0): Ranges: V min: 47 V max: 85 Hz, H min: 31 H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c504601010101
(II) RADEON(0): 	2b0f0103804728788a288e9e55489724
(II) RADEON(0): 	16484b256a0031d945d961d971cf81c0
(II) RADEON(0): 	010101010101a91a00a0500016303020
(II) RADEON(0): 	3700c48e21000018d60980a020e02d10
(II) RADEON(0): 	08602200128e210808188c0ad08a20e0
(II) RADEON(0): 	2d10103e9600c48e21000018000000fd
(II) RADEON(0): 	002f551f500e000a2020202020200104
(II) RADEON(0): 	02031a75470103040512931423090707
(II) RADEON(0): 	8301000065030c001000011d007251d0
(II) RADEON(0): 	1e206e285500c48e2100001e011d8018
(II) RADEON(0): 	711c1620582c2500c48e2100009e8c0a
(II) RADEON(0): 	d090204031200c405500c48e21000018
(II) RADEON(0): 	011d00bc52d01e20b8285540c48e2100
(II) RADEON(0): 	001e011d80d0721c1620102c2580c48e
(II) RADEON(0): 	2100009e000000ff0000000000000049
(II) RADEON(0): EDID vendor "PHL", prod id 18000
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x768"x0.0   68.25  1280 1328 1360 1440  768 771 778 790 -hsync -vsync (47.4 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 648 744 800  480 482 484 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "640x360"x85.0   25.77  640 656 720 800  360 361 364 379 -hsync +vsync (32.2 kHz)
(II) RADEON(0): Modeline "800x450"x85.0   41.81  800 840 920 1040  450 451 454 473 -hsync +vsync (40.2 kHz)
(II) RADEON(0): Modeline "1024x576"x85.0   69.11  1024 1080 1184 1344  576 577 580 605 -hsync +vsync (51.4 kHz)
(II) RADEON(0): Modeline "1152x648"x75.0   77.18  1152 1216 1336 1520  648 649 652 677 -hsync +vsync (50.8 kHz)
(II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: PHL  Model: 4650  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 71  vert.: 40
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.617 redY: 0.334   greenX: 0.283 greenY: 0.590
(II) RADEON(0): blueX: 0.143 blueY: 0.086   whiteX: 0.284 whiteY: 0.295
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 360  refresh: 85  vid: 55601
(II) RADEON(0): #1: hsize: 800  vsize 450  refresh: 85  vid: 55621
(II) RADEON(0): #2: hsize: 1024  vsize 576  refresh: 85  vid: 55649
(II) RADEON(0): #3: hsize: 1152  vsize 648  refresh: 75  vid: 53105
(II) RADEON(0): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.2 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 790 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 25.2 MHz   Image Size:  530 x 398 mm
(II) RADEON(0): h_active: 640  h_sync: 648  h_sync_end 744 h_blank_end 800 h_border: 8
(II) RADEON(0): v_active: 480  v_sync: 482  v_sync_end 484 v_blanking: 525 v_border: 8
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 27.0 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
(II) RADEON(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
(II) RADEON(0): Ranges: V min: 47 V max: 85 Hz, H min: 31 H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c504601010101
(II) RADEON(0): 	2b0f0103804728788a288e9e55489724
(II) RADEON(0): 	16484b256a0031d945d961d971cf81c0
(II) RADEON(0): 	010101010101a91a00a0500016303020
(II) RADEON(0): 	3700c48e21000018d60980a020e02d10
(II) RADEON(0): 	08602200128e210808188c0ad08a20e0
(II) RADEON(0): 	2d10103e9600c48e21000018000000fd
(II) RADEON(0): 	002f551f500e000a2020202020200104
(II) RADEON(0): 	02031a75470103040512931423090707
(II) RADEON(0): 	8301000065030c001000011d007251d0
(II) RADEON(0): 	1e206e285500c48e2100001e011d8018
(II) RADEON(0): 	711c1620582c2500c48e2100009e8c0a
(II) RADEON(0): 	d090204031200c405500c48e21000018
(II) RADEON(0): 	011d00bc52d01e20b8285540c48e2100
(II) RADEON(0): 	001e011d80d0721c1620102c2580c48e
(II) RADEON(0): 	2100009e000000ff0000000000000049
(II) RADEON(0): EDID vendor "PHL", prod id 18000
(II) RADEON(0): Not using mode "1280x768" (width too large for virtual size)
(II) RADEON(0): Not using mode "1152x648" (width too large for virtual size)
(II) RADEON(0): Not using mode "1280x720" (width too large for virtual size)
(II) RADEON(0): Printing probed modes for output DVI-0
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x576"x85.0   69.11  1024 1080 1184 1344  576 577 580 605 -hsync +vsync (51.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x450"x85.0   41.81  800 840 920 1040  450 451 454 473 -hsync +vsync (40.2 kHz)
(II) RADEON(0): Modeline "720x480"x59.9   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x60.0   25.18  640 648 744 800  480 482 484 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x360"x85.0   25.77  640 656 720 800  360 361 364 379 -hsync +vsync (32.2 kHz)
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
disable FP2
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
(II) RADEON(0): EDID vendor "PHL", prod id 2080
(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Manufacturer: PHL  Model: 4650  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 71  vert.: 40
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.617 redY: 0.334   greenX: 0.283 greenY: 0.590
(II) RADEON(0): blueX: 0.143 blueY: 0.086   whiteX: 0.284 whiteY: 0.295
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 360  refresh: 85  vid: 55601
(II) RADEON(0): #1: hsize: 800  vsize 450  refresh: 85  vid: 55621
(II) RADEON(0): #2: hsize: 1024  vsize 576  refresh: 85  vid: 55649
(II) RADEON(0): #3: hsize: 1152  vsize 648  refresh: 75  vid: 53105
(II) RADEON(0): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.2 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 790 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 25.2 MHz   Image Size:  530 x 398 mm
(II) RADEON(0): h_active: 640  h_sync: 648  h_sync_end 744 h_blank_end 800 h_border: 8
(II) RADEON(0): v_active: 480  v_sync: 482  v_sync_end 484 v_blanking: 525 v_border: 8
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 27.0 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
(II) RADEON(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
(II) RADEON(0): Ranges: V min: 47 V max: 85 Hz, H min: 31 H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c504601010101
(II) RADEON(0): 	2b0f0103804728788a288e9e55489724
(II) RADEON(0): 	16484b256a0031d945d961d971cf81c0
(II) RADEON(0): 	010101010101a91a00a0500016303020
(II) RADEON(0): 	3700c48e21000018d60980a020e02d10
(II) RADEON(0): 	08602200128e210808188c0ad08a20e0
(II) RADEON(0): 	2d10103e9600c48e21000018000000fd
(II) RADEON(0): 	002f551f500e000a2020202020200104
(II) RADEON(0): 	02031a75470103040512931423090707
(II) RADEON(0): 	8301000065030c001000011d007251d0
(II) RADEON(0): 	1e206e285500c48e2100001e011d8018
(II) RADEON(0): 	711c1620582c2500c48e2100009e8c0a
(II) RADEON(0): 	d090204031200c405500c48e21000018
(II) RADEON(0): 	011d00bc52d01e20b8285540c48e2100
(II) RADEON(0): 	001e011d80d0721c1620102c2580c48e
(II) RADEON(0): 	2100009e000000ff0000000000000049
(II) RADEON(0): EDID vendor "PHL", prod id 18000
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x768"x0.0   68.25  1280 1328 1360 1440  768 771 778 790 -hsync -vsync (47.4 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 648 744 800  480 482 484 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "640x360"x85.0   25.77  640 656 720 800  360 361 364 379 -hsync +vsync (32.2 kHz)
(II) RADEON(0): Modeline "800x450"x85.0   41.81  800 840 920 1040  450 451 454 473 -hsync +vsync (40.2 kHz)
(II) RADEON(0): Modeline "1024x576"x85.0   69.11  1024 1080 1184 1344  576 577 580 605 -hsync +vsync (51.4 kHz)
(II) RADEON(0): Modeline "1152x648"x75.0   77.18  1152 1216 1336 1520  648 649 652 677 -hsync +vsync (50.8 kHz)
(II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: PHL  Model: 4650  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 71  vert.: 40
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.617 redY: 0.334   greenX: 0.283 greenY: 0.590
(II) RADEON(0): blueX: 0.143 blueY: 0.086   whiteX: 0.284 whiteY: 0.295
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 360  refresh: 85  vid: 55601
(II) RADEON(0): #1: hsize: 800  vsize 450  refresh: 85  vid: 55621
(II) RADEON(0): #2: hsize: 1024  vsize 576  refresh: 85  vid: 55649
(II) RADEON(0): #3: hsize: 1152  vsize 648  refresh: 75  vid: 53105
(II) RADEON(0): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.2 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 790 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 25.2 MHz   Image Size:  530 x 398 mm
(II) RADEON(0): h_active: 640  h_sync: 648  h_sync_end 744 h_blank_end 800 h_border: 8
(II) RADEON(0): v_active: 480  v_sync: 482  v_sync_end 484 v_blanking: 525 v_border: 8
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 27.0 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
(II) RADEON(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
(II) RADEON(0): Ranges: V min: 47 V max: 85 Hz, H min: 31 H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c504601010101
(II) RADEON(0): 	2b0f0103804728788a288e9e55489724
(II) RADEON(0): 	16484b256a0031d945d961d971cf81c0
(II) RADEON(0): 	010101010101a91a00a0500016303020
(II) RADEON(0): 	3700c48e21000018d60980a020e02d10
(II) RADEON(0): 	08602200128e210808188c0ad08a20e0
(II) RADEON(0): 	2d10103e9600c48e21000018000000fd
(II) RADEON(0): 	002f551f500e000a2020202020200104
(II) RADEON(0): 	02031a75470103040512931423090707
(II) RADEON(0): 	8301000065030c001000011d007251d0
(II) RADEON(0): 	1e206e285500c48e2100001e011d8018
(II) RADEON(0): 	711c1620582c2500c48e2100009e8c0a
(II) RADEON(0): 	d090204031200c405500c48e21000018
(II) RADEON(0): 	011d00bc52d01e20b8285540c48e2100
(II) RADEON(0): 	001e011d80d0721c1620102c2580c48e
(II) RADEON(0): 	2100009e000000ff0000000000000049
(II) RADEON(0): EDID vendor "PHL", prod id 18000
(II) RADEON(0): Not using mode "1280x768" (width too large for virtual size)
(II) RADEON(0): Not using mode "1152x648" (width too large for virtual size)
(II) RADEON(0): Not using mode "1280x720" (width too large for virtual size)
(II) RADEON(0): Printing probed modes for output DVI-0
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x576"x85.0   69.11  1024 1080 1184 1344  576 577 580 605 -hsync +vsync (51.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x450"x85.0   41.81  800 840 920 1040  450 451 454 473 -hsync +vsync (40.2 kHz)
(II) RADEON(0): Modeline "720x480"x59.9   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x60.0   25.18  640 648 744 800  480 482 484 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x360"x85.0   25.77  640 656 720 800  360 361 364 379 -hsync +vsync (32.2 kHz)
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
(II) RADEON(0): EDID vendor "PHL", prod id 2080
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
(II) RADEON(0): EDID vendor "PHL", prod id 2080
(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Manufacturer: PHL  Model: 4650  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 71  vert.: 40
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.617 redY: 0.334   greenX: 0.283 greenY: 0.590
(II) RADEON(0): blueX: 0.143 blueY: 0.086   whiteX: 0.284 whiteY: 0.295
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 360  refresh: 85  vid: 55601
(II) RADEON(0): #1: hsize: 800  vsize 450  refresh: 85  vid: 55621
(II) RADEON(0): #2: hsize: 1024  vsize 576  refresh: 85  vid: 55649
(II) RADEON(0): #3: hsize: 1152  vsize 648  refresh: 75  vid: 53105
(II) RADEON(0): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.2 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 790 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 25.2 MHz   Image Size:  530 x 398 mm
(II) RADEON(0): h_active: 640  h_sync: 648  h_sync_end 744 h_blank_end 800 h_border: 8
(II) RADEON(0): v_active: 480  v_sync: 482  v_sync_end 484 v_blanking: 525 v_border: 8
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 27.0 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
(II) RADEON(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
(II) RADEON(0): Ranges: V min: 47 V max: 85 Hz, H min: 31 H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c504601010101
(II) RADEON(0): 	2b0f0103804728788a288e9e55489724
(II) RADEON(0): 	16484b256a0031d945d961d971cf81c0
(II) RADEON(0): 	010101010101a91a00a0500016303020
(II) RADEON(0): 	3700c48e21000018d60980a020e02d10
(II) RADEON(0): 	08602200128e210808188c0ad08a20e0
(II) RADEON(0): 	2d10103e9600c48e21000018000000fd
(II) RADEON(0): 	002f551f500e000a2020202020200104
(II) RADEON(0): 	02031a75470103040512931423090707
(II) RADEON(0): 	8301000065030c001000011d007251d0
(II) RADEON(0): 	1e206e285500c48e2100001e011d8018
(II) RADEON(0): 	711c1620582c2500c48e2100009e8c0a
(II) RADEON(0): 	d090204031200c405500c48e21000018
(II) RADEON(0): 	011d00bc52d01e20b8285540c48e2100
(II) RADEON(0): 	001e011d80d0721c1620102c2580c48e
(II) RADEON(0): 	2100009e000000ff0000000000000049
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: PHL  Model: 4650  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 71  vert.: 40
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.617 redY: 0.334   greenX: 0.283 greenY: 0.590
(II) RADEON(0): blueX: 0.143 blueY: 0.086   whiteX: 0.284 whiteY: 0.295
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 360  refresh: 85  vid: 55601
(II) RADEON(0): #1: hsize: 800  vsize 450  refresh: 85  vid: 55621
(II) RADEON(0): #2: hsize: 1024  vsize 576  refresh: 85  vid: 55649
(II) RADEON(0): #3: hsize: 1152  vsize 648  refresh: 75  vid: 53105
(II) RADEON(0): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.2 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 790 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 25.2 MHz   Image Size:  530 x 398 mm
(II) RADEON(0): h_active: 640  h_sync: 648  h_sync_end 744 h_blank_end 800 h_border: 8
(II) RADEON(0): v_active: 480  v_sync: 482  v_sync_end 484 v_blanking: 525 v_border: 8
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 27.0 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
(II) RADEON(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
(II) RADEON(0): Ranges: V min: 47 V max: 85 Hz, H min: 31 H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c504601010101
(II) RADEON(0): 	2b0f0103804728788a288e9e55489724
(II) RADEON(0): 	16484b256a0031d945d961d971cf81c0
(II) RADEON(0): 	010101010101a91a00a0500016303020
(II) RADEON(0): 	3700c48e21000018d60980a020e02d10
(II) RADEON(0): 	08602200128e210808188c0ad08a20e0
(II) RADEON(0): 	2d10103e9600c48e21000018000000fd
(II) RADEON(0): 	002f551f500e000a2020202020200104
(II) RADEON(0): 	02031a75470103040512931423090707
(II) RADEON(0): 	8301000065030c001000011d007251d0
(II) RADEON(0): 	1e206e285500c48e2100001e011d8018
(II) RADEON(0): 	711c1620582c2500c48e2100009e8c0a
(II) RADEON(0): 	d090204031200c405500c48e21000018
(II) RADEON(0): 	011d00bc52d01e20b8285540c48e2100
(II) RADEON(0): 	001e011d80d0721c1620102c2580c48e
(II) RADEON(0): 	2100009e000000ff0000000000000049
(II) RADEON(0): EDID vendor "PHL", prod id 18000
(II) RADEON(0): Not using mode "1280x768" (width too large for virtual size)
(II) RADEON(0): Not using mode "1152x648" (width too large for virtual size)
(II) RADEON(0): Not using mode "1280x720" (width too large for virtual size)
(II) RADEON(0): Printing probed modes for output DVI-0
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x576"x85.0   69.11  1024 1080 1184 1344  576 577 580 605 -hsync +vsync (51.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x450"x85.0   41.81  800 840 920 1040  450 451 454 473 -hsync +vsync (40.2 kHz)
(II) RADEON(0): Modeline "720x480"x59.9   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x60.0   25.18  640 648 744 800  480 482 484 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x360"x85.0   25.77  640 656 720 800  360 361 364 379 -hsync +vsync (32.2 kHz)
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
(II) RADEON(0): EDID vendor "PHL", prod id 2080
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
(II) RADEON(0): EDID vendor "PHL", prod id 2080
(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Manufacturer: PHL  Model: 4650  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 71  vert.: 40
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.617 redY: 0.334   greenX: 0.283 greenY: 0.590
(II) RADEON(0): blueX: 0.143 blueY: 0.086   whiteX: 0.284 whiteY: 0.295
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 360  refresh: 85  vid: 55601
(II) RADEON(0): #1: hsize: 800  vsize 450  refresh: 85  vid: 55621
(II) RADEON(0): #2: hsize: 1024  vsize 576  refresh: 85  vid: 55649
(II) RADEON(0): #3: hsize: 1152  vsize 648  refresh: 75  vid: 53105
(II) RADEON(0): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.2 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 790 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 25.2 MHz   Image Size:  530 x 398 mm
(II) RADEON(0): h_active: 640  h_sync: 648  h_sync_end 744 h_blank_end 800 h_border: 8
(II) RADEON(0): v_active: 480  v_sync: 482  v_sync_end 484 v_blanking: 525 v_border: 8
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 27.0 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
(II) RADEON(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
(II) RADEON(0): Ranges: V min: 47 V max: 85 Hz, H min: 31 H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c504601010101
(II) RADEON(0): 	2b0f0103804728788a288e9e55489724
(II) RADEON(0): 	16484b256a0031d945d961d971cf81c0
(II) RADEON(0): 	010101010101a91a00a0500016303020
(II) RADEON(0): 	3700c48e21000018d60980a020e02d10
(II) RADEON(0): 	08602200128e210808188c0ad08a20e0
(II) RADEON(0): 	2d10103e9600c48e21000018000000fd
(II) RADEON(0): 	002f551f500e000a2020202020200104
(II) RADEON(0): 	02031a75470103040512931423090707
(II) RADEON(0): 	8301000065030c001000011d007251d0
(II) RADEON(0): 	1e206e285500c48e2100001e011d8018
(II) RADEON(0): 	711c1620582c2500c48e2100009e8c0a
(II) RADEON(0): 	d090204031200c405500c48e21000018
(II) RADEON(0): 	011d00bc52d01e20b8285540c48e2100
(II) RADEON(0): 	001e011d80d0721c1620102c2580c48e
(II) RADEON(0): 	2100009e000000ff0000000000000049
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: PHL  Model: 4650  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 71  vert.: 40
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.617 redY: 0.334   greenX: 0.283 greenY: 0.590
(II) RADEON(0): blueX: 0.143 blueY: 0.086   whiteX: 0.284 whiteY: 0.295
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 360  refresh: 85  vid: 55601
(II) RADEON(0): #1: hsize: 800  vsize 450  refresh: 85  vid: 55621
(II) RADEON(0): #2: hsize: 1024  vsize 576  refresh: 85  vid: 55649
(II) RADEON(0): #3: hsize: 1152  vsize 648  refresh: 75  vid: 53105
(II) RADEON(0): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.2 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 790 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 25.2 MHz   Image Size:  530 x 398 mm
(II) RADEON(0): h_active: 640  h_sync: 648  h_sync_end 744 h_blank_end 800 h_border: 8
(II) RADEON(0): v_active: 480  v_sync: 482  v_sync_end 484 v_blanking: 525 v_border: 8
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 27.0 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
(II) RADEON(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
(II) RADEON(0): Ranges: V min: 47 V max: 85 Hz, H min: 31 H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c504601010101
(II) RADEON(0): 	2b0f0103804728788a288e9e55489724
(II) RADEON(0): 	16484b256a0031d945d961d971cf81c0
(II) RADEON(0): 	010101010101a91a00a0500016303020
(II) RADEON(0): 	3700c48e21000018d60980a020e02d10
(II) RADEON(0): 	08602200128e210808188c0ad08a20e0
(II) RADEON(0): 	2d10103e9600c48e21000018000000fd
(II) RADEON(0): 	002f551f500e000a2020202020200104
(II) RADEON(0): 	02031a75470103040512931423090707
(II) RADEON(0): 	8301000065030c001000011d007251d0
(II) RADEON(0): 	1e206e285500c48e2100001e011d8018
(II) RADEON(0): 	711c1620582c2500c48e2100009e8c0a
(II) RADEON(0): 	d090204031200c405500c48e21000018
(II) RADEON(0): 	011d00bc52d01e20b8285540c48e2100
(II) RADEON(0): 	001e011d80d0721c1620102c2580c48e
(II) RADEON(0): 	2100009e000000ff0000000000000049
(II) RADEON(0): EDID vendor "PHL", prod id 18000
(II) RADEON(0): Not using mode "1280x768" (width too large for virtual size)
(II) RADEON(0): Not using mode "1152x648" (width too large for virtual size)
(II) RADEON(0): Not using mode "1280x720" (width too large for virtual size)
(II) RADEON(0): Printing probed modes for output DVI-0
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x576"x85.0   69.11  1024 1080 1184 1344  576 577 580 605 -hsync +vsync (51.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x450"x85.0   41.81  800 840 920 1040  450 451 454 473 -hsync +vsync (40.2 kHz)
(II) RADEON(0): Modeline "720x480"x59.9   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x60.0   25.18  640 648 744 800  480 482 484 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x360"x85.0   25.77  640 656 720 800  360 361 364 379 -hsync +vsync (32.2 kHz)
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
(II) RADEON(0): EDID vendor "PHL", prod id 2080
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
(II) RADEON(0): EDID vendor "PHL", prod id 2080
(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Manufacturer: PHL  Model: 4650  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 71  vert.: 40
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.617 redY: 0.334   greenX: 0.283 greenY: 0.590
(II) RADEON(0): blueX: 0.143 blueY: 0.086   whiteX: 0.284 whiteY: 0.295
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 360  refresh: 85  vid: 55601
(II) RADEON(0): #1: hsize: 800  vsize 450  refresh: 85  vid: 55621
(II) RADEON(0): #2: hsize: 1024  vsize 576  refresh: 85  vid: 55649
(II) RADEON(0): #3: hsize: 1152  vsize 648  refresh: 75  vid: 53105
(II) RADEON(0): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.2 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 790 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 25.2 MHz   Image Size:  530 x 398 mm
(II) RADEON(0): h_active: 640  h_sync: 648  h_sync_end 744 h_blank_end 800 h_border: 8
(II) RADEON(0): v_active: 480  v_sync: 482  v_sync_end 484 v_blanking: 525 v_border: 8
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 27.0 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
(II) RADEON(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
(II) RADEON(0): Ranges: V min: 47 V max: 85 Hz, H min: 31 H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c504601010101
(II) RADEON(0): 	2b0f0103804728788a288e9e55489724
(II) RADEON(0): 	16484b256a0031d945d961d971cf81c0
(II) RADEON(0): 	010101010101a91a00a0500016303020
(II) RADEON(0): 	3700c48e21000018d60980a020e02d10
(II) RADEON(0): 	08602200128e210808188c0ad08a20e0
(II) RADEON(0): 	2d10103e9600c48e21000018000000fd
(II) RADEON(0): 	002f551f500e000a2020202020200104
(II) RADEON(0): 	02031a75470103040512931423090707
(II) RADEON(0): 	8301000065030c001000011d007251d0
(II) RADEON(0): 	1e206e285500c48e2100001e011d8018
(II) RADEON(0): 	711c1620582c2500c48e2100009e8c0a
(II) RADEON(0): 	d090204031200c405500c48e21000018
(II) RADEON(0): 	011d00bc52d01e20b8285540c48e2100
(II) RADEON(0): 	001e011d80d0721c1620102c2580c48e
(II) RADEON(0): 	2100009e000000ff0000000000000049
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: PHL  Model: 4650  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 71  vert.: 40
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.617 redY: 0.334   greenX: 0.283 greenY: 0.590
(II) RADEON(0): blueX: 0.143 blueY: 0.086   whiteX: 0.284 whiteY: 0.295
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 360  refresh: 85  vid: 55601
(II) RADEON(0): #1: hsize: 800  vsize 450  refresh: 85  vid: 55621
(II) RADEON(0): #2: hsize: 1024  vsize 576  refresh: 85  vid: 55649
(II) RADEON(0): #3: hsize: 1152  vsize 648  refresh: 75  vid: 53105
(II) RADEON(0): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.2 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 790 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 25.2 MHz   Image Size:  530 x 398 mm
(II) RADEON(0): h_active: 640  h_sync: 648  h_sync_end 744 h_blank_end 800 h_border: 8
(II) RADEON(0): v_active: 480  v_sync: 482  v_sync_end 484 v_blanking: 525 v_border: 8
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 27.0 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
(II) RADEON(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
(II) RADEON(0): Ranges: V min: 47 V max: 85 Hz, H min: 31 H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c504601010101
(II) RADEON(0): 	2b0f0103804728788a288e9e55489724
(II) RADEON(0): 	16484b256a0031d945d961d971cf81c0
(II) RADEON(0): 	010101010101a91a00a0500016303020
(II) RADEON(0): 	3700c48e21000018d60980a020e02d10
(II) RADEON(0): 	08602200128e210808188c0ad08a20e0
(II) RADEON(0): 	2d10103e9600c48e21000018000000fd
(II) RADEON(0): 	002f551f500e000a2020202020200104
(II) RADEON(0): 	02031a75470103040512931423090707
(II) RADEON(0): 	8301000065030c001000011d007251d0
(II) RADEON(0): 	1e206e285500c48e2100001e011d8018
(II) RADEON(0): 	711c1620582c2500c48e2100009e8c0a
(II) RADEON(0): 	d090204031200c405500c48e21000018
(II) RADEON(0): 	011d00bc52d01e20b8285540c48e2100
(II) RADEON(0): 	001e011d80d0721c1620102c2580c48e
(II) RADEON(0): 	2100009e000000ff0000000000000049
(II) RADEON(0): EDID vendor "PHL", prod id 18000
(II) RADEON(0): Not using mode "1280x768" (width too large for virtual size)
(II) RADEON(0): Not using mode "1152x648" (width too large for virtual size)
(II) RADEON(0): Not using mode "1280x720" (width too large for virtual size)
(II) RADEON(0): Printing probed modes for output DVI-0
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x576"x85.0   69.11  1024 1080 1184 1344  576 577 580 605 -hsync +vsync (51.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x450"x85.0   41.81  800 840 920 1040  450 451 454 473 -hsync +vsync (40.2 kHz)
(II) RADEON(0): Modeline "720x480"x59.9   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x60.0   25.18  640 648 744 800  480 482 484 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x360"x85.0   25.77  640 656 720 800  360 361 364 379 -hsync +vsync (32.2 kHz)
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
(II) RADEON(0): EDID vendor "PHL", prod id 2080
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: PHL  Model: 820  Serial#: 51137
(II) RADEON(0): Year: 2004  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.347   greenX: 0.309 greenY: 0.583
(II) RADEON(0): blueX: 0.150 blueY: 0.088   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Serial No:  CX  051137
(II) RADEON(0): Monitor name: Philips 150S
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 63 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c2008c1c70000
(II) RADEON(0): 	2b0e01030e1e1778eab1a5a1584f9526
(II) RADEON(0): 	165054bfee0001010101010101010101
(II) RADEON(0): 	01010101010164190040410026301888
(II) RADEON(0): 	360033e610000018000000ff00204358
(II) RADEON(0): 	20203035313133370a20000000fc0050
(II) RADEON(0): 	68696c69707320313530530a000000fd
(II) RADEON(0): 	00384c1e3f08000a20202020202000ff
(II) RADEON(0): EDID vendor "PHL", prod id 2080
(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Manufacturer: PHL  Model: 4650  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 71  vert.: 40
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.617 redY: 0.334   greenX: 0.283 greenY: 0.590
(II) RADEON(0): blueX: 0.143 blueY: 0.086   whiteX: 0.284 whiteY: 0.295
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 360  refresh: 85  vid: 55601
(II) RADEON(0): #1: hsize: 800  vsize 450  refresh: 85  vid: 55621
(II) RADEON(0): #2: hsize: 1024  vsize 576  refresh: 85  vid: 55649
(II) RADEON(0): #3: hsize: 1152  vsize 648  refresh: 75  vid: 53105
(II) RADEON(0): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.2 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 790 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 25.2 MHz   Image Size:  530 x 398 mm
(II) RADEON(0): h_active: 640  h_sync: 648  h_sync_end 744 h_blank_end 800 h_border: 8
(II) RADEON(0): v_active: 480  v_sync: 482  v_sync_end 484 v_blanking: 525 v_border: 8
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 27.0 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
(II) RADEON(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
(II) RADEON(0): Ranges: V min: 47 V max: 85 Hz, H min: 31 H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c504601010101
(II) RADEON(0): 	2b0f0103804728788a288e9e55489724
(II) RADEON(0): 	16484b256a0031d945d961d971cf81c0
(II) RADEON(0): 	010101010101a91a00a0500016303020
(II) RADEON(0): 	3700c48e21000018d60980a020e02d10
(II) RADEON(0): 	08602200128e210808188c0ad08a20e0
(II) RADEON(0): 	2d10103e9600c48e21000018000000fd
(II) RADEON(0): 	002f551f500e000a2020202020200104
(II) RADEON(0): 	02031a75470103040512931423090707
(II) RADEON(0): 	8301000065030c001000011d007251d0
(II) RADEON(0): 	1e206e285500c48e2100001e011d8018
(II) RADEON(0): 	711c1620582c2500c48e2100009e8c0a
(II) RADEON(0): 	d090204031200c405500c48e21000018
(II) RADEON(0): 	011d00bc52d01e20b8285540c48e2100
(II) RADEON(0): 	001e011d80d0721c1620102c2580c48e
(II) RADEON(0): 	2100009e000000ff0000000000000049
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: PHL  Model: 4650  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 71  vert.: 40
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.617 redY: 0.334   greenX: 0.283 greenY: 0.590
(II) RADEON(0): blueX: 0.143 blueY: 0.086   whiteX: 0.284 whiteY: 0.295
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 640  vsize 360  refresh: 85  vid: 55601
(II) RADEON(0): #1: hsize: 800  vsize 450  refresh: 85  vid: 55621
(II) RADEON(0): #2: hsize: 1024  vsize 576  refresh: 85  vid: 55649
(II) RADEON(0): #3: hsize: 1152  vsize 648  refresh: 75  vid: 53105
(II) RADEON(0): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.2 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 790 v_border: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 25.2 MHz   Image Size:  530 x 398 mm
(II) RADEON(0): h_active: 640  h_sync: 648  h_sync_end 744 h_blank_end 800 h_border: 8
(II) RADEON(0): v_active: 480  v_sync: 482  v_sync_end 484 v_blanking: 525 v_border: 8
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 27.0 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
(II) RADEON(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
(II) RADEON(0): Ranges: V min: 47 V max: 85 Hz, H min: 31 H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c504601010101
(II) RADEON(0): 	2b0f0103804728788a288e9e55489724
(II) RADEON(0): 	16484b256a0031d945d961d971cf81c0
(II) RADEON(0): 	010101010101a91a00a0500016303020
(II) RADEON(0): 	3700c48e21000018d60980a020e02d10
(II) RADEON(0): 	08602200128e210808188c0ad08a20e0
(II) RADEON(0): 	2d10103e9600c48e21000018000000fd
(II) RADEON(0): 	002f551f500e000a2020202020200104
(II) RADEON(0): 	02031a75470103040512931423090707
(II) RADEON(0): 	8301000065030c001000011d007251d0
(II) RADEON(0): 	1e206e285500c48e2100001e011d8018
(II) RADEON(0): 	711c1620582c2500c48e2100009e8c0a
(II) RADEON(0): 	d090204031200c405500c48e21000018
(II) RADEON(0): 	011d00bc52d01e20b8285540c48e2100
(II) RADEON(0): 	001e011d80d0721c1620102c2580c48e
(II) RADEON(0): 	2100009e000000ff0000000000000049
(II) RADEON(0): EDID vendor "PHL", prod id 18000
(II) RADEON(0): Not using mode "1280x768" (width too large for virtual size)
(II) RADEON(0): Not using mode "1152x648" (width too large for virtual size)
(II) RADEON(0): Not using mode "1280x720" (width too large for virtual size)
(II) RADEON(0): Printing probed modes for output DVI-0
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x576"x85.0   69.11  1024 1080 1184 1344  576 577 580 605 -hsync +vsync (51.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x450"x85.0   41.81  800 840 920 1040  450 451 454 473 -hsync +vsync (40.2 kHz)
(II) RADEON(0): Modeline "720x480"x59.9   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x60.0   25.18  640 648 744 800  480 482 484 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x360"x85.0   25.77  640 656 720 800  360 361 364 379 -hsync +vsync (32.2 kHz)
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video

```

---

