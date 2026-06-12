---
title: "Ubuntu Intrepid no keyboard or touchpad after suspend"
date: 2009-01-22
forum: Hardware
---

### Post by cygnus8595 on 2009-01-22
I know this topic has come up many times, but I've done some digging and I think I've narrowed down the problem and have an idea where to begin, but my scripting skills aren't up to the task. But first, some background.

I recently got a Compaq Evo N1000v laptop and the first thing I did was install Ubuntu. Almost everything works properly and I'm very pleased, but I'd like to fix the remaining issues it has to make it a perfect OS - specifically, I have issues with WPA wireless and suspend/hibernate. I'll save the wireless for another thread. :)

At first, whenever I tried to suspend or hibernate I'd get a black terminal screen with a flashing cursor and it would take a hard reset to get the computer back to a working state. I tried a few things mentioned in the forums - I made a few minor additions to xorg.conf and acpi-support and installed Ubuntu Tweak and checked the box to stop network manager on suspend or resume, but nothing worked. I finally disconnected my wireless card - a Dell 1450 USB card - and to my surprise hibernate and suspend both worked, at least when it the computer went down.

The next problem happened on resume. I can resume (thaw) from hibernate with no problems, but when I resume from suspend, my touchpad and keyboard don't work and I can't unlock the screen. I have to do a hard reset to get the computer back up and running.

I checked the pm-suspend.log file after both a successful hibernate and an unsuccessful suspend and noticed that the 99video script was throwing an error when resuming from suspend but not when thawing from hibernate, so I know the problem is somewhere in that script or with parameters sent to that script from hal. I haven't troubleshooted the wireless card suspend issue, but I'm less concerned with that as I can just unplug it for now.

I'll post some log files in a little while (I'm not on the laptop now) but if anyone has any suggestions based on what I already mentioned please let me know. I'm not a bad programmer (I write .Net stuff for a living) but I have little to no experience with bash scripts, although I'm willing to help.

---

### Post by cygnus8595 on 2009-01-22
pm_suspend.log after successful hibernate:

```

Initial commandline parameters: --quirk-dpms-on
--quirk-vbestate-restore
--quirk-vbemode-restore
--quirk-vga-mode3
--quirk-vbe-post
--quirk-reset-brightness
Thu Jan 22 08:16:03 MST 2009: Running hooks for hibernate.
/usr/lib/pm-utils/sleep.d/00clear hibernate: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate: success.
/usr/lib/pm-utils/sleep.d/05led hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/10NetworkManager hibernate: success.
/usr/lib/pm-utils/sleep.d/48hid2hci hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/49bluetooth hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/50modules hibernate: success.
/usr/lib/pm-utils/sleep.d/90clock hibernate: Welcome to PulseAudio! Use "help" for usage information.
>>> success.
/usr/lib/pm-utils/sleep.d/94cpufreq hibernate: success.
/usr/lib/pm-utils/sleep.d/95anacron hibernate: success.
/usr/lib/pm-utils/sleep.d/95led hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/96laptop-mode hibernate: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/99video hibernate: success.
Thu Jan 22 08:16:05 MST 2009: performing hibernate
Thu Jan 22 08:17:45 MST 2009: Awake.
Thu Jan 22 08:17:45 MST 2009: Running hooks for thaw
/usr/lib/pm-utils/sleep.d/99video thaw: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video thaw: success.
/usr/lib/pm-utils/sleep.d/96laptop-mode thaw: success.
/usr/lib/pm-utils/sleep.d/95led thaw: not applicable.
/usr/lib/pm-utils/sleep.d/95anacron thaw: success.
/usr/lib/pm-utils/sleep.d/94cpufreq thaw: success.
/usr/lib/pm-utils/sleep.d/90clock thaw: success.
/usr/lib/pm-utils/sleep.d/50modules thaw: success.
/usr/lib/pm-utils/sleep.d/49bluetooth thaw: not applicable.
/usr/lib/pm-utils/sleep.d/48hid2hci thaw: No devices in HID mode found
Returned exit code 1.
/usr/lib/pm-utils/sleep.d/10NetworkManager thaw: success.
/usr/lib/pm-utils/sleep.d/05led thaw: not applicable.
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw: success.
/usr/lib/pm-utils/sleep.d/00clear thaw: success.
Thu Jan 22 08:17:49 MST 2009: Finished.
Welcome to PulseAudio! Use "help" for usage information.
>>> 

```

pm-suspend.log after failed suspend (notice messages after 99video):

```

Initial commandline parameters: --quirk-dpms-on
--quirk-vbestate-restore
--quirk-vbemode-restore
--quirk-vga-mode3
--quirk-vbe-post
--quirk-reset-brightness
Thu Jan 22 08:20:38 MST 2009: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/00clear suspend: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend: success.
/usr/lib/pm-utils/sleep.d/05led suspend: Welcome to PulseAudio! Use "help" for usage information.
>>> not applicable.
/usr/lib/pm-utils/sleep.d/10NetworkManager suspend: success.
/usr/lib/pm-utils/sleep.d/48hid2hci suspend: not applicable.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend: not applicable.
/usr/lib/pm-utils/sleep.d/50modules suspend: success.
/usr/lib/pm-utils/sleep.d/90clock suspend: success.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend: success.
/usr/lib/pm-utils/sleep.d/95anacron suspend: success.
/usr/lib/pm-utils/sleep.d/95led suspend: not applicable.
/usr/lib/pm-utils/sleep.d/96laptop-mode suspend: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video suspend: not applicable.
/usr/lib/pm-utils/sleep.d/99video suspend: Allocated buffer at 0x2010 (base is 0x0)
ES: 0x0201 EBX: 0x0000
success.
Thu Jan 22 08:20:40 MST 2009: performing suspend
Thu Jan 22 08:20:55 MST 2009: Awake.
Thu Jan 22 08:20:55 MST 2009: Running hooks for resume
/usr/lib/pm-utils/sleep.d/99video resume: Function not supported
Function not supported
success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video resume: success.
/usr/lib/pm-utils/sleep.d/96laptop-mode resume: success.
/usr/lib/pm-utils/sleep.d/95led resume: not applicable.
/usr/lib/pm-utils/sleep.d/95anacron resume: success.
/usr/lib/pm-utils/sleep.d/94cpufreq resume: success.
/usr/lib/pm-utils/sleep.d/90clock resume: success.
/usr/lib/pm-utils/sleep.d/50modules resume: success.
/usr/lib/pm-utils/sleep.d/49bluetooth resume: not applicable.
/usr/lib/pm-utils/sleep.d/48hid2hci resume: No devices in HID mode found
Returned exit code 1.
/usr/lib/pm-utils/sleep.d/10NetworkManager resume: success.
/usr/lib/pm-utils/sleep.d/05led resume: not applicable.
/usr/lib/pm-utils/sleep.d/01PulseAudio resume: Welcome to PulseAudio! Use "help" for usage information.
>>> success.
/usr/lib/pm-utils/sleep.d/00clear resume: success.
Thu Jan 22 08:21:02 MST 2009: Finished.

```

I'd be happy to post any more information.

---

### Post by cygnus8595 on 2009-01-22
Xorg.0.log after suspend failure (noticed the two lines about not finding core keyboard or pointing device):

```


X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux UbuntuEvo 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686
Build Date: 24 October 2008  08:00:16AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Jan 22 08:23:26 2009
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
(++) using VT number 7

(--) PCI:*(0@1:0:0) ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500] rev 0, Mem @ 0x48000000/0, 0x40400000/0, I/O @ 0x00003000/0, BIOS @ 0x????????/131072
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
	compiled for 1.5.2, module version = 6.9.0
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
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
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
(II) RADEON(0): MMIO registers at 0x0000000040400000: size 64KB
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
(--) RADEON(0): Chipset: "ATI Radeon Mobility M7 LW (AGP)" (ChipID = 0x4c57)
(--) RADEON(0): Linear framebuffer at 0x0000000048000000
(II) RADEON(0): AGP card detected
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 4.1
(II) RADEON(0): initializing int10
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(II) RADEON(0): Legacy BIOS detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: drmOpenMinor returns 10
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) RADEON(0): [dri] Found DRI library version 1.3.0 and kernel module version 1.29.0
(==) RADEON(0): Page Flipping disabled
(II) RADEON(0): Will try to use DMA for Xv image transfers
(II) RADEON(0): Detected total video RAM=32768K, accessible=65536K (PCI BAR=131072K)
(--) RADEON(0): Mapped VideoRAM: 32768 kByte (64 bit DDR SDRAM)
(II) RADEON(0): Color tiling enabled by default
(II) RADEON(0): Max desktop size set to 2048x1200
(II) RADEON(0): For a larger or smaller max desktop size, add a Virtual line to your xorg.conf
(II) RADEON(0): If you are having trouble with 3D, reduce the desktop size by adjusting the Virtual line to your xorg.conf
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) RADEON(0): ref_freq: 2700, min_out_pll: 12000, max_out_pll: 35000, min_in_pll: 40, max_in_pll: 3000, xclk: 18300, sclk: 183.000000, mclk: 260.000000
(II) RADEON(0): PLL parameters: rf=2700 rd=12 min=12000 max=35000; xclk=18300
(WW) RADEON(0): LCD DDC Info Table found!
(II) RADEON(0): Bios Connector table: 
(II) RADEON(0): Port0: DDCType-0x60, DACType-1, TMDSType-1, ConnectorType-1
(II) RADEON(0): Port4: DDCType-0x6c, DACType-0, TMDSType-0, ConnectorType-7
(II) RADEON(0): Port5: DDCType-0x0, DACType-2, TMDSType-0, ConnectorType-5
(II) RADEON(0): Output VGA-0 using monitor section Configured Monitor
(II) RADEON(0): I2C bus "VGA-0" initialized.
(II) RADEON(0): Output LVDS has no monitor section
(II) RADEON(0): Panel ID string: AUO B141XG03
(II) RADEON(0): Panel Size from BIOS: 1024x768
(II) RADEON(0): BIOS provided dividers will be used.
(WW) RADEON(0): LVDS Info:
XRes: 1024, YRes: 768, DotClock: 65000
HBlank: 296, HOverPlus: 16, HSyncWidth: 136
VBlank: 35, VOverPlus: 3, VSyncWidth: 6
(II) RADEON(0): I2C bus "LVDS" initialized.
(II) RADEON(0): Output S-video has no monitor section
(II) RADEON(0): Default TV standard: NTSC
(II) RADEON(0): TV standards supported by chip: NTSC PAL PAL-M 
(II) RADEON(0): Port0:
 Monitor   -- AUTO
 Connector -- VGA
 DAC Type  -- Primary
 TMDS Type -- None
 DDC Type  -- 0x60
(II) RADEON(0): Port1:
 Monitor   -- AUTO
 Connector -- LVDS
 DAC Type  -- None
 TMDS Type -- None
 DDC Type  -- 0x6c
(II) RADEON(0): Port2:
 Monitor   -- AUTO
 Connector -- STV
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- None
 DDC Type  -- 0x0
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
finished output detect: 0
(II) RADEON(0): I2C device "LVDS:ddc2" registered at address 0xA0.
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: AUO  Model: 1407  Serial#: 1496
(II) RADEON(0): Year: 2002  Week: 30
(II) RADEON(0): EDID Version: 1.2
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 29  vert.: 22
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.576 redY: 0.327   greenX: 0.300 greenY: 0.555
(II) RADEON(0): blueX: 0.145 blueY: 0.119   whiteX: 0.310 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  286 x 214 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1320 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 803 v_border: 0
(II) RADEON(0):  eÿP
(II) RADEON(0):  AUQ
(II) RADEON(0): Monitor name: B141XG03
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0006af0714d8050000
(II) RADEON(0): 	1e0c0102801d16780abc2593534c8e25
(II) RADEON(0): 	1e4f5400000001010101010101010101
(II) RADEON(0): 	01010101010164190028410023301888
(II) RADEON(0): 	36001ed610000019000000fe00016502
(II) RADEON(0): 	7f011a12120bff025001000000fe0041
(II) RADEON(0): 	555100000000000000000a20000000fc
(II) RADEON(0): 	0042313431584730330000000a2000a4
finished output detect: 1
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
finished output detect: 2
finished all detect
before xf86InitialConfiguration
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: AUO  Model: 1407  Serial#: 1496
(II) RADEON(0): Year: 2002  Week: 30
(II) RADEON(0): EDID Version: 1.2
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 29  vert.: 22
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.576 redY: 0.327   greenX: 0.300 greenY: 0.555
(II) RADEON(0): blueX: 0.145 blueY: 0.119   whiteX: 0.310 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  286 x 214 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1320 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 803 v_border: 0
(II) RADEON(0):  eÿP
(II) RADEON(0):  AUQ
(II) RADEON(0): Monitor name: B141XG03
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0006af0714d8050000
(II) RADEON(0): 	1e0c0102801d16780abc2593534c8e25
(II) RADEON(0): 	1e4f5400000001010101010101010101
(II) RADEON(0): 	01010101010164190028410023301888
(II) RADEON(0): 	36001ed610000019000000fe00016502
(II) RADEON(0): 	7f011a12120bff025001000000fe0041
(II) RADEON(0): 	555100000000000000000a20000000fc
(II) RADEON(0): 	0042313431584730330000000a2000a4
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "AUO", prod id 5127
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): Output VGA-0 disconnected
(II) RADEON(0): Output LVDS connected
(II) RADEON(0): Output S-video disconnected
(II) RADEON(0): Using exact sizes for initial modes
(II) RADEON(0): Output LVDS using initial mode 1024x768
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
(==) RADEON(0): Using XAA acceleration architecture
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"

(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.2.0
	ABI class: X.Org Video Driver, version 4.1
(==) RADEON(0): Assuming overlay scaler buffer width is 1536
(II) RADEON(0): No MM_TABLE found - assuming CARD is not TV-in capable.
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
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) RADEON(0): RADEONScreenInit 48000000 0 0
Entering TV Save
Save TV timing tables
saveTimingTables: reading timing tables
TV Save done
(II) RADEON(0): Dynamic Clock Scaling Disabled
(==) RADEON(0): Using 24 bit depth buffer
(II) RADEON(0): RADEONInitMemoryMap() : 
(II) RADEON(0):   mem_size         : 0x04000000
(II) RADEON(0):   MC_FB_LOCATION   : 0x4bff4800
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(II) RADEON(0): Depth moves disabled by default
(II) RADEON(0): Using 8 MB GART aperture
(II) RADEON(0): Using 1 MB for the ring buffer
(II) RADEON(0): Using 2 MB for vertex/indirect buffers
(II) RADEON(0): Using 5 MB for GART textures
(II) RADEON(0): Memory manager initialized to (0,0) (1024,8191)
(II) RADEON(0): Reserved area from (0,1024) to (1024,1026)
(II) RADEON(0): Largest offscreen area available: 1024 x 7165
(II) RADEON(0): Will use front buffer at offset 0x0
(II) RADEON(0): Will use back buffer at offset 0x800000
(II) RADEON(0): Will use depth buffer at offset 0xc00000
(II) RADEON(0): Will use 16384 kb for textures at offset 0x1000000
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: drmOpenMinor returns 10
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) RADEON(0): [drm] Using the DRM lock SAREA also for drawables.
(II) RADEON(0): [drm] framebuffer handle = 0x48000000
(II) RADEON(0): [drm] added 1 reserved context for kernel
(II) RADEON(0): X context handle = 0x1
(II) RADEON(0): [drm] installed DRM signal handler
(==) RADEON(0): Using AGP 4x
(II) RADEON(0): [agp] Mode 0x1f000207 [AGP 0x8086/0x1a30; Card 0x1002/0x4c57]
(II) RADEON(0): [agp] 8192 kB allocated with handle 0x00000001
(II) RADEON(0): [agp] ring handle = 0x60000000
(II) RADEON(0): [agp] Ring mapped at 0xb797c000
(II) RADEON(0): [agp] ring read ptr handle = 0x60101000
(II) RADEON(0): [agp] Ring read ptr mapped at 0xb8039000
(II) RADEON(0): [agp] vertex/indirect buffers handle = 0x60102000
(II) RADEON(0): [agp] Vertex/indirect buffers mapped at 0xb56b2000
(II) RADEON(0): [agp] GART texture map handle = 0x60302000
(II) RADEON(0): [agp] GART Texture map mapped at 0xb51d2000
(II) RADEON(0): [drm] register handle = 0x40400000
(II) RADEON(0): [dri] Visual configs initialized
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x4bff4800 0x1fff0000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(==) RADEON(0): Backing store disabled
(II) RADEON(0): [DRI] installation complete
(II) RADEON(0): [drm] Added 32 65536 byte vertex/indirect buffers
(II) RADEON(0): [drm] Mapped 32 vertex/indirect buffers
(II) RADEON(0): [drm] dma control initialized, using IRQ 11
(II) RADEON(0): [drm] Initialized kernel GART heap manager, 5111808
(WW) RADEON(0): DRI init changed memory map, adjusting ...
(WW) RADEON(0):   MC_FB_LOCATION  was: 0x4bff4800 is: 0x4bff4800
(WW) RADEON(0):   MC_AGP_LOCATION was: 0xffffffc0 is: 0x607f6000
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x4bff4800 0x4bff4800
(II) RADEON(0):   MC_AGP_LOCATION  : 0x607f6000
(II) RADEON(0): Direct rendering enabled
(II) RADEON(0): Render acceleration enabled
(II) RADEON(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Scanline Image Writes
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) RADEON(0): Acceleration enabled
(II) RADEON(0): DPMS enabled
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Will use 32 kb for hardware cursor 0 at offset 0x00402000
(II) RADEON(0): Will use 32 kb for hardware cursor 1 at offset 0x00406000
(II) RADEON(0): Largest offscreen area available: 1024 x 7157
(II) RADEON(0): Detected Radeon Mobility M7, disabling multimedia i2c
(II) Loading sub module "theatre_detect"
(II) LoadModule: "theatre_detect"

(II) Loading /usr/lib/xorg/modules/multimedia//theatre_detect_drv.so
(II) Module theatre_detect: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 4.1
(II) RADEON(0): no multimedia table present, disabling Rage Theatre.
(II) RADEON(0): Set up overlay video
(II) RADEON(0): Set up textured video
init memmap
init common
init crtc1
init pll1
restore memmap
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x4bff4800 0x4bff4800
(II) RADEON(0):   MC_AGP_LOCATION  : 0x607f6000
restore common
restore crtc1
restore pll1
restore LVDS
(II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(WW) RADEON(0): Option "VBERestore" is not used
(--) RandR disabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: drmOpenMinor returns 11
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: enabled GLX_texture_from_pixmap with driver support
(II) AIGLX: Loaded and initialized /usr/lib/dri/radeon_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) RADEON(0): Setting screen physical size to 286 x 214
(II) config/hal: Adding input device Macintosh mouse button emulation
(II) LoadModule: "evdev"

(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 2.0.99
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Configuring as mouse
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device SynPS/2 Synaptics TouchPad
(II) LoadModule: "synaptics"

(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 0.15.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(II) Synaptics touchpad driver version 0.15.2
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(**) Option "Device" "/dev/input/event7"
(**) Option "SHMConfig" "On"
(--) SynPS/2 Synaptics TouchPad touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(--) SynPS/2 Synaptics TouchPad touchpad found
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event1"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) AT Translated Set 2 keyboard: xkb_layout: "us"
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): EDID vendor "AUO", prod id 5127
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1320  768 771 777 803 -hsync -vsync (49.2 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: AUO  Model: 1407  Serial#: 1496
(II) RADEON(0): Year: 2002  Week: 30
(II) RADEON(0): EDID Version: 1.2
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 29  vert.: 22
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.576 redY: 0.327   greenX: 0.300 greenY: 0.555
(II) RADEON(0): blueX: 0.145 blueY: 0.119   whiteX: 0.310 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  286 x 214 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1320 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 803 v_border: 0
(II) RADEON(0):  eÿP
(II) RADEON(0):  AUQ
(II) RADEON(0): Monitor name: B141XG03
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0006af0714d8050000
(II) RADEON(0): 	1e0c0102801d16780abc2593534c8e25
(II) RADEON(0): 	1e4f5400000001010101010101010101
(II) RADEON(0): 	01010101010164190028410023301888
(II) RADEON(0): 	36001ed610000019000000fe00016502
(II) RADEON(0): 	7f011a12120bff025001000000fe0041
(II) RADEON(0): 	555100000000000000000a20000000fc
(II) RADEON(0): 	0042313431584730330000000a2000a4
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "AUO", prod id 5127
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
AUDIT: Thu Jan 22 08:23:36 2009: 5017 X: client 4 rejected from local host ( uid=0 gid=0 pid=5270 )
AUDIT: Thu Jan 22 08:23:40 2009: 5017 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=5276 )
  Auth name: MIT-MAGIC-COOKIE-1 ID: -1
AUDIT: Thu Jan 22 08:23:40 2009: 5017 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=5277 )
  Auth name: MIT-MAGIC-COOKIE-1 ID: -1
AUDIT: Thu Jan 22 08:23:40 2009: 5017 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=5278 )
  Auth name: MIT-MAGIC-COOKIE-1 ID: -1
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): EDID vendor "AUO", prod id 5127
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1320  768 771 777 803 -hsync -vsync (49.2 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: AUO  Model: 1407  Serial#: 1496
(II) RADEON(0): Year: 2002  Week: 30
(II) RADEON(0): EDID Version: 1.2
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 29  vert.: 22
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.576 redY: 0.327   greenX: 0.300 greenY: 0.555
(II) RADEON(0): blueX: 0.145 blueY: 0.119   whiteX: 0.310 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  286 x 214 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1320 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 803 v_border: 0
(II) RADEON(0):  eÿP
(II) RADEON(0):  AUQ
(II) RADEON(0): Monitor name: B141XG03
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0006af0714d8050000
(II) RADEON(0): 	1e0c0102801d16780abc2593534c8e25
(II) RADEON(0): 	1e4f5400000001010101010101010101
(II) RADEON(0): 	01010101010164190028410023301888
(II) RADEON(0): 	36001ed610000019000000fe00016502
(II) RADEON(0): 	7f011a12120bff025001000000fe0041
(II) RADEON(0): 	555100000000000000000a20000000fc
(II) RADEON(0): 	0042313431584730330000000a2000a4
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "AUO", prod id 5127
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): EDID vendor "AUO", prod id 5127
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1320  768 771 777 803 -hsync -vsync (49.2 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: AUO  Model: 1407  Serial#: 1496
(II) RADEON(0): Year: 2002  Week: 30
(II) RADEON(0): EDID Version: 1.2
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 29  vert.: 22
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.576 redY: 0.327   greenX: 0.300 greenY: 0.555
(II) RADEON(0): blueX: 0.145 blueY: 0.119   whiteX: 0.310 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  286 x 214 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1320 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 803 v_border: 0
(II) RADEON(0):  eÿP
(II) RADEON(0):  AUQ
(II) RADEON(0): Monitor name: B141XG03
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0006af0714d8050000
(II) RADEON(0): 	1e0c0102801d16780abc2593534c8e25
(II) RADEON(0): 	1e4f5400000001010101010101010101
(II) RADEON(0): 	01010101010164190028410023301888
(II) RADEON(0): 	36001ed610000019000000fe00016502
(II) RADEON(0): 	7f011a12120bff025001000000fe0041
(II) RADEON(0): 	555100000000000000000a20000000fc
(II) RADEON(0): 	0042313431584730330000000a2000a4
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "AUO", prod id 5127
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): EDID vendor "AUO", prod id 5127
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1320  768 771 777 803 -hsync -vsync (49.2 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: AUO  Model: 1407  Serial#: 1496
(II) RADEON(0): Year: 2002  Week: 30
(II) RADEON(0): EDID Version: 1.2
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 29  vert.: 22
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.576 redY: 0.327   greenX: 0.300 greenY: 0.555
(II) RADEON(0): blueX: 0.145 blueY: 0.119   whiteX: 0.310 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  286 x 214 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1320 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 803 v_border: 0
(II) RADEON(0):  eÿP
(II) RADEON(0):  AUQ
(II) RADEON(0): Monitor name: B141XG03
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0006af0714d8050000
(II) RADEON(0): 	1e0c0102801d16780abc2593534c8e25
(II) RADEON(0): 	1e4f5400000001010101010101010101
(II) RADEON(0): 	01010101010164190028410023301888
(II) RADEON(0): 	36001ed610000019000000fe00016502
(II) RADEON(0): 	7f011a12120bff025001000000fe0041
(II) RADEON(0): 	555100000000000000000a20000000fc
(II) RADEON(0): 	0042313431584730330000000a2000a4
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "AUO", prod id 5127
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): EDID vendor "AUO", prod id 5127
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1320  768 771 777 803 -hsync -vsync (49.2 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: AUO  Model: 1407  Serial#: 1496
(II) RADEON(0): Year: 2002  Week: 30
(II) RADEON(0): EDID Version: 1.2
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 29  vert.: 22
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.576 redY: 0.327   greenX: 0.300 greenY: 0.555
(II) RADEON(0): blueX: 0.145 blueY: 0.119   whiteX: 0.310 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  286 x 214 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1320 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 803 v_border: 0
(II) RADEON(0):  eÿP
(II) RADEON(0):  AUQ
(II) RADEON(0): Monitor name: B141XG03
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0006af0714d8050000
(II) RADEON(0): 	1e0c0102801d16780abc2593534c8e25
(II) RADEON(0): 	1e4f5400000001010101010101010101
(II) RADEON(0): 	01010101010164190028410023301888
(II) RADEON(0): 	36001ed610000019000000fe00016502
(II) RADEON(0): 	7f011a12120bff025001000000fe0041
(II) RADEON(0): 	555100000000000000000a20000000fc
(II) RADEON(0): 	0042313431584730330000000a2000a4
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "AUO", prod id 5127
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): EDID vendor "AUO", prod id 5127
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1320  768 771 777 803 -hsync -vsync (49.2 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: AUO  Model: 1407  Serial#: 1496
(II) RADEON(0): Year: 2002  Week: 30
(II) RADEON(0): EDID Version: 1.2
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 29  vert.: 22
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.576 redY: 0.327   greenX: 0.300 greenY: 0.555
(II) RADEON(0): blueX: 0.145 blueY: 0.119   whiteX: 0.310 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  286 x 214 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1320 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 803 v_border: 0
(II) RADEON(0):  eÿP
(II) RADEON(0):  AUQ
(II) RADEON(0): Monitor name: B141XG03
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0006af0714d8050000
(II) RADEON(0): 	1e0c0102801d16780abc2593534c8e25
(II) RADEON(0): 	1e4f5400000001010101010101010101
(II) RADEON(0): 	01010101010164190028410023301888
(II) RADEON(0): 	36001ed610000019000000fe00016502
(II) RADEON(0): 	7f011a12120bff025001000000fe0041
(II) RADEON(0): 	555100000000000000000a20000000fc
(II) RADEON(0): 	0042313431584730330000000a2000a4
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "AUO", prod id 5127
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0

```

---

### Post by cygnus8595 on 2009-01-22
More updates:

I added these two kernel options to menu.lst I found in another thread but they didn't work:

i8042.reset i8042.nomux

Also, here's the output from /proc/bus/input/devices:

```

     1	I: Bus=0017 Vendor=0001 Product=0001 Version=0100
     2	N: Name="Macintosh mouse button emulation"
     3	P: Phys=
     4	S: Sysfs=/devices/virtual/input/input0
     5	U: Uniq=
     6	H: Handlers=mouse0 event0 
     7	B: EV=7
     8	B: KEY=70000 0 0 0 0 0 0 0 0
     9	B: REL=3
    10	
    11	I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
    12	N: Name="AT Translated Set 2 keyboard"
    13	P: Phys=isa0060/serio0/input0
    14	S: Sysfs=/devices/platform/i8042/serio0/input/input1
    15	U: Uniq=
    16	H: Handlers=kbd event1 
    17	B: EV=120013
    18	B: KEY=4 2000000 3803078 f800d001 feffffdf ffefffff ffffffff fffffffe
    19	B: MSC=10
    20	B: LED=7
    21	
    22	I: Bus=0010 Vendor=001f Product=0001 Version=0100
    23	N: Name="PC Speaker"
    24	P: Phys=isa0061/input0
    25	S: Sysfs=/devices/platform/pcspkr/input/input2
    26	U: Uniq=
    27	H: Handlers=kbd event2 
    28	B: EV=40001
    29	B: SND=6
    30	
    31	I: Bus=0019 Vendor=0000 Product=0002 Version=0000
    32	N: Name="Power Button (FF)"
    33	P: Phys=LNXPWRBN/button/input0
    34	S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
    35	U: Uniq=
    36	H: Handlers=kbd event3 
    37	B: EV=3
    38	B: KEY=100000 0 0 0
    39	
    40	I: Bus=0019 Vendor=0000 Product=0001 Version=0000
    41	N: Name="Power Button (CM)"
    42	P: Phys=PNP0C0C/button/input0
    43	S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
    44	U: Uniq=
    45	H: Handlers=kbd event4 
    46	B: EV=3
    47	B: KEY=100000 0 0 0
    48	
    49	I: Bus=0019 Vendor=0000 Product=0003 Version=0000
    50	N: Name="Sleep Button (CM)"
    51	P: Phys=PNP0C0E/button/input0
    52	S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input5
    53	U: Uniq=
    54	H: Handlers=kbd event5 
    55	B: EV=3
    56	B: KEY=4000 0 0 0 0
    57	
    58	I: Bus=0019 Vendor=0000 Product=0005 Version=0000
    59	N: Name="Lid Switch"
    60	P: Phys=PNP0C0D/button/input0
    61	S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input6
    62	U: Uniq=
    63	H: Handlers=event6 
    64	B: EV=21
    65	B: SW=1
    66	
    67	I: Bus=0011 Vendor=0002 Product=0007 Version=9db1
    68	N: Name="SynPS/2 Synaptics TouchPad"
    69	P: Phys=isa0060/serio4/input0
    70	S: Sysfs=/devices/platform/i8042/serio4/input/input7
    71	U: Uniq=
    72	H: Handlers=mouse1 event7 
    73	B: EV=b
    74	B: KEY=6420 0 7000f 0 0 0 0 0 0 0 0
    75	B: ABS=11000003
    76	

```

---

### Post by cygnus8595 on 2009-01-23
I'm bumping this once to see if there is any help on this. I'll post my acpi-support file later today.

---

### Post by cygnus8595 on 2009-01-23
Would it be an option to try acpi-support for suspend/resume instead of dbus-hal or pm-utils? I can change the option in the acpi-support file.

---

### Post by cygnus8595 on 2009-01-26
OK, it seems like I'm talking to myself in this thread, but I'll add that I changed my acpi-support file to use acpi-support first and it didn't make a difference. Any ideas would be helpful. I'll keep plugging away as well.

---

### Post by linlux on 2009-01-26
I'm pretty new here too ...just had a similar issue with Intrepid on a desktop, it would always freeze with caps and scroll light blinking after 15 mins of inactivity and sometimes when using it. Tried turning off acpi, disabling apic, using rt kernel, upgrading nvidia drivers...nothing worked. This morning I just decided to downgrade to Gutsy, it seems ok so far. Much faster too.

Here's the big thread on Hardy freezing, pretty sure Intrepid has the same problems:
[http://ubuntuforums.org/showthread.php?t=765510](http://ubuntuforums.org/showthread.php?t=765510)

---

### Post by cygnus8595 on 2009-01-27
I checked that thread (and the bug reports linked from there) and they don't seem related to my issue. I haven't had any random crashes at all. I just don't have a working keyboard or mouse after suspend (hibernate works fine). I'm going to create a bug report on this.

---

### Post by cygnus8595 on 2009-01-28
Bug report filed:

[https://bugs.launchpad.net/ubuntu/+bug/322007](https://bugs.launchpad.net/ubuntu/+bug/322007)

---

### Post by PiousRenegade on 2009-01-28
I'm in the same boat as you, cygnus8595. Suspend was just inop until the .27-11 Kernel update. After that, it resumes okay, but without the onboard keyboard and trackpad.

I should point out that I can use an external KB/Mouse, and oddly enough, still use the power management functions on the keyboard - such as brightness and, oddly enough, suspend. However, input into the screen doesn't work.

Looking at /proc/bus/input/devices shows that the entries for the onboard keyboard and mouse are missing. I'm thinking the system just isnt detecting them after suspend. Which leads me to further suspect that they aren't hooked up through USB, since my external KB works fine. 

Maybe some script to reload whatever bus they are on is appropriate?

EDIT: Forgot to mention its a HP dv5-1002nr

---

### Post by cygnus8595 on 2009-01-29
I'm sure it's somewhere in the 99video script, because that's where the difference is in the pm-suspend.log. It shows "Function not supported" twice after that script runs in a resume but not in a thaw from hibernate. Check yours out after a failed resume and see if that same error is there, if you don't mind.

---

### Post by PiousRenegade on 2009-01-29
> **cygnus8595 said:**
> I'm sure it's somewhere in the 99video script, because that's where the difference is in the pm-suspend.log. It shows "Function not supported" twice after that script runs in a resume but not in a thaw from hibernate. Check yours out after a failed resume and see if that same error is there, if you don't mind.

I do not mind. Here ya go:

```
piousrenegade@Oroboros:~$ cat /var/log/pm-suspend.log 
Initial commandline parameters: 
Wed Jan 28 13:22:05 HST 2009: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/00clear suspend: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend: sudo: no passwd entry for 1000!
success.
/usr/lib/pm-utils/sleep.d/05led suspend: not applicable.
/usr/lib/pm-utils/sleep.d/10NetworkManager suspend: success.
/usr/lib/pm-utils/sleep.d/48hid2hci suspend: not applicable.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend: not applicable.
/usr/lib/pm-utils/sleep.d/50modules suspend: success.
/usr/lib/pm-utils/sleep.d/90clock suspend: success.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend: success.
/usr/lib/pm-utils/sleep.d/95anacron suspend: success.
/usr/lib/pm-utils/sleep.d/95led suspend: not applicable.
/usr/lib/pm-utils/sleep.d/96laptop-mode suspend: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video suspend: success.
/usr/lib/pm-utils/sleep.d/99video suspend: success.
Wed Jan 28 13:22:07 HST 2009: performing suspend
Wed Jan 28 15:04:41 HST 2009: Awake.
Wed Jan 28 15:04:41 HST 2009: Running hooks for resume
/usr/lib/pm-utils/sleep.d/99video resume: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video resume: success.
/usr/lib/pm-utils/sleep.d/96laptop-mode resume: Laptop mode enabled, active
success.
/usr/lib/pm-utils/sleep.d/95led resume: not applicable.
/usr/lib/pm-utils/sleep.d/95anacron resume: success.
/usr/lib/pm-utils/sleep.d/94cpufreq resume: success.
/usr/lib/pm-utils/sleep.d/90clock resume: success.
/usr/lib/pm-utils/sleep.d/50modules resume: success.
/usr/lib/pm-utils/sleep.d/49bluetooth resume: not applicable.
/usr/lib/pm-utils/sleep.d/48hid2hci resume: No devices in HID mode found
Returned exit code 1.
/usr/lib/pm-utils/sleep.d/10NetworkManager resume: success.
/usr/lib/pm-utils/sleep.d/05led resume: not applicable.
/usr/lib/pm-utils/sleep.d/01PulseAudio resume: success.
/usr/lib/pm-utils/sleep.d/00clear resume: sudo: no passwd entry for 1000!
success.
Wed Jan 28 15:04:43 HST 2009: Finished.
piousrenegade@Oroboros:~$ 

```

---

### Post by cygnus8595 on 2009-01-29
Crap, I was hoping to see the "Function not supported" error somewhere. I guess 99video isn't the problem.

---

### Post by jmw86069 on 2009-01-31
I'm happy to report that I have been tracking this issue along with you, and have been able to resume from suspend with functional touchpad and keyboard! Prior to then, I could resume from hibernate with no apparent issues, but resume from suspend resulted in a non-functioning keyboard and touchpad.

There are several very relevant threads and bugs still open, however, so I'm surprised you didn't stumble upon potential solutions.

The solution which worked for me was to add "i8042.reset" to the /boot/grub/menu.lst entry which contains stuff like "ro quiet splash" as noted at the bottom of the post here:
[http://ubuntuforums.org/archive/index.php/t-1038898.html](http://ubuntuforums.org/archive/index.php/t-1038898.html)
Fwiw here is my menu.lst entry in total, so you can see where to add "i8042.reset":
```
title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		88b99fce-0f2b-421d-9071-5974649671ce
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=88b99fce-0f2b-421d-9071-5974649671ce ro quiet splash i8042.reset
initrd		/boot/initrd.img-2.6.27-11-generic
quiet
```

There are other threads which suggest tweaks to acpi-support to unbind then bind i8042 for the keyboard and touchpad, but none worked for me. Interesting that hooking a USB keyboard worked fine, as did a USB mouse. When I typed in the commands to unbind/bind, they worked fine and restored a functioning laptop keyboard/touchpad. However I couldn't get them to work in the /etc/acpi/resume.d/ folder as these posts refer:
[http://ubuntuforums.org/showpost.php?p=2690982&postcount=14](http://ubuntuforums.org/showpost.php?p=2690982&postcount=14)
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/23497](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/23497)

Currently, I still have composite and AIGLX disabled, per other posts suggesting those changes are required for suspend/resume. I will definitely be testing various methods of re-enabling desktop effects. I do like the eye-candy, but I would also just appreciate hardware-accelerated everything else! These changes were added to /etc/X11/xorg.conf to disable Composite and AIGLX:
```
Section "Extensions"
        Option        "Composite"        "Disable"
EndSection
Section "ServerFlags"
       Option  "AIGLX" "off" 
EndSection
```

Let me know if adding the "i8042.reset" to your menu.lst entry helps! I may also post to the other threads to see if people find this fix helpful there too. (Can't believe the bug entry has been unresolved for year and a half!)

---

### Post by PiousRenegade on 2009-02-01
> **jmw86069 said:**
> I'm happy to report that I have been tracking this issue along with you, and have been able to resume from suspend with functional touchpad and keyboard! Prior to then, I could resume from hibernate with no apparent issues, but resume from suspend resulted in a non-functioning keyboard and touchpad.

There are several very relevant threads and bugs still open, however, so I'm surprised you didn't stumble upon potential solutions.

The solution which worked for me was to add "i8042.reset" to the /boot/grub/menu.lst entry which contains stuff like "ro quiet splash" as noted at the bottom of the post here:
[http://ubuntuforums.org/archive/index.php/t-1038898.html](http://ubuntuforums.org/archive/index.php/t-1038898.html)
Fwiw here is my menu.lst entry in total, so you can see where to add "i8042.reset":
```
title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		88b99fce-0f2b-421d-9071-5974649671ce
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=88b99fce-0f2b-421d-9071-5974649671ce ro quiet splash i8042.reset
initrd		/boot/initrd.img-2.6.27-11-generic
quiet
```

There are other threads which suggest tweaks to acpi-support to unbind then bind i8042 for the keyboard and touchpad, but none worked for me. Interesting that hooking a USB keyboard worked fine, as did a USB mouse. When I typed in the commands to unbind/bind, they worked fine and restored a functioning laptop keyboard/touchpad. However I couldn't get them to work in the /etc/acpi/resume.d/ folder as these posts refer:
[http://ubuntuforums.org/showpost.php?p=2690982&postcount=14](http://ubuntuforums.org/showpost.php?p=2690982&postcount=14)
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/23497](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/23497)

Currently, I still have composite and AIGLX disabled, per other posts suggesting those changes are required for suspend/resume. I will definitely be testing various methods of re-enabling desktop effects. I do like the eye-candy, but I would also just appreciate hardware-accelerated everything else! These changes were added to /etc/X11/xorg.conf to disable Composite and AIGLX:
```
Section "Extensions"
        Option        "Composite"        "Disable"
EndSection
Section "ServerFlags"
       Option  "AIGLX" "off" 
EndSection
```

Let me know if adding the "i8042.reset" to your menu.lst entry helps! I may also post to the other threads to see if people find this fix helpful there too. (Can't believe the bug entry has been unresolved for year and a half!)

Well it was 100% successful for me. I now have most of the hardware in my shittly little HP craptop working. Just gotta sort out the sound server and skype issues. But that's for another thread!

BTW, I have Compiz running with plenty of eye candy, and running with ATI's drivers. 

I think the i8042.reset solution is just hard to get one's head around. I mean, the LAST place I would think to put a line like that would be in the boot options!

---

### Post by doyouhas on 2009-02-01
I have something interesting to report. This problem is not Linux specific. This same sort of thing happened with my laptop running XP. Maybe it's a problem with certain touchpads?

---

### Post by cygnus8595 on 2009-02-02
I had i8042.reset and i8042.nomux in my menu.lst. I removed i8042.nomux and tried it with the same results - no keyboard or mouse after resume from suspend. The fact that hibernate works perfectly makes this even more frustrating.

---

### Post by cygnus8595 on 2009-02-02
Also, I think the hooks in acpi-support didn't work properly because newer versions of Ubuntu don't use acpi-support but instead use hal and pm-utils for power management. I tried to force Ubuntu to use acpi-support but it didn't work either.

---

### Post by jmw86069 on 2009-02-02
> **PiousRenegade said:**
> BTW, I have Compiz running with plenty of eye candy, and running with ATI's drivers. 

I think the i8042.reset solution is just hard to get one's head around. I mean, the LAST place I would think to put a line like that would be in the boot options!

It's always the LAST place, especially once it works!? :o

BTW I also enabled the Compiz and Emerald eyecandy, and they both work. It's nice to have a laptop with working graphics, wireless network, and power-saving. Of course, I say that after none of those three worked for a few days... possibly the top 3 things a laptop needs!

cygnus, I will take another look at your log files (as if it has any chance of helping!) but for me, I could see that after hibernate, the i8042 lines reloaded somehow, but after suspend, the i8042 lines did not appear. I mean, easier in hindsight I know... but I was looking for serio_raw module which I figured may need reloading. It didn't, but that may be something else to try. (E.g. "sudo rmmod serio_raw && sudo modprobe serio_raw" -- I put both on the same line, you know, cuz I didn't know if it would somehow kill my USB keyboard functionality. SSH would still work though.) I tried reloading HAL ("sudo /etc/init.d/hal restart") but again, that didn't work for me either. For you, ya never know.

---

### Post by cygnus8595 on 2009-02-13
I haven't had much time to work on this. I've decided to wait a few months until 9.04 comes out. It's based on a new kernel, so maybe there's a fix for this problem. If not I'll be updating my bug report and this thread.

---

### Post by fedoraboy on 2009-02-15
I have the same issue... with a few differences.

a) slight hardware differences:
   HP dv7 family.  
   ATI HD 3200 
   most recent drivers from ATI (catalyst 9.1/8.573)
b) no errors whatsoever in pm-suspend.log.  It's all smiles and giggles there.

I do get the same errors in Xorg.0.log:
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.

post back here if you find anything...

---

### Post by jmw86069 on 2009-02-17
fedoraboy, have you tried my suggestion from Page 2, adding "i8042.reset" to the /boot/grub/menu.lst file's kernel options? I have HP dv7 series laptop and it resolved the problem completely for me.

As almost any solution is as randomly solved as the next, I didn't have any trouble at all wrapping my head around it. :-)

If the symptom is the same with other laptops, or with other keyboard/touchpad modules, I would suggest it requires a very similar solution. If not i8042.reset, whatever module handles keyboard/touchpad may have a similar option available. Find out what module handles the keyboard/touchpad, then Google the heck out of it to find what options people have tried?

I noticed the mute quickbar button is red when the laptop is booting up, and returning from Suspend... then it turns white once the relevant module is loaded. I'm wondering if that's the way to find the module that actually knows how to change the color of the mute once pressed (since otherwise it stays white.) hmmm... different issue I know...

---

### Post by jmw86069 on 2009-02-17
cygnus, I don't tend to think 99video is your problem, mostly because you can see video. Your keyboard and touchpad won't work, suggesting to me that's your problem. Have you tried SSH'ing into the box and running this command:
```
sudo rmmod i8042 && sudo modprobe i8042
```
I had to run twice or more sometimes for it to work, but it would work. If it worked, it would confirm module i8042 is affected.

And if so, there was another solution I tried which didn't work for me, but I (hehe) didn't reverse the attempt before applying my i8042.reset fix. In other words, just maybe this attempt works for you, or maybe both changes actually fixed my problem and not just the one.

I created a file in /etc/acpi/suspend.d/ called "20-i8042-input.sh" with this content:
```
#!/bin/sh

# Unbind the AT keyboard interface.
if [ -f /sys/bus/platform/drivers/i8042/unbind ]; then
  echo -n "i8042" > /sys/bus/platform/drivers/i8042/unbind
fi

```

I also created the "antidote" file in /etc/acpi/resume.d/ called "39-i8042-input.sh":
```
#!/bin/sh

# Unbind the AT keyboard interface.
if [ -f /sys/bus/platform/drivers/i8042/unbind ]; then
  echo -n "i8042" > /sys/bus/platform/drivers/i8042/unbind
fi

# Rebind the AT keyboard interface.
if [ -f /sys/bus/platform/drivers/i8042/bind ]; then
  echo -n "i8042" > /sys/bus/platform/drivers/i8042/bind
fi

```

In the latter file, you may not "need" the unbind there again, but there it is in case it helped. For me, I had to SSH and remove and add the i8042 module twice or more before it would work, so this was my way of having the system "try twice."

Interestingly, and this may blow your mind if you care to think about it (some don't)... I removed the 39-i8024-input.sh file from resume.d, but not the 20-i8042-input.sh file from suspend.d. But, uh, I'm like typing on my keyboard n stuff anyway. Duuuude. Maybe the i8042 module just gets in the way of whatever Ubuntu thinks it already knows how to do.

So I'd suggest creating these two files, and for good sport keep the "i8042.reset" option in the /boot/grub/menu.lst file. I'd also suggest double-checking that you're sure you added that option to the correct line, the correct kernel you're actually using. (Sorry to suggest a rookie mistake, but it would be the easiest fix right?)

For me, in the menu.lst file, right underneath ## ## End Default Options ## I have lines that begin with these keywords: "title", "uuid", "kernel", "initrd", and "quiet". I put the option "i8042.reset" at the end of the line that began with "kernel". Sorry if that was a waste of my typing, but ya never know.

---

### Post by fedoraboy on 2009-02-17
> **jmw86069 said:**
> fedoraboy, have you tried my suggestion from Page 2, adding "i8042.reset" to the /boot/grub/menu.lst file's kernel options? I have HP dv7 series laptop and it resolved the problem completely for me.


Doh.  Not only had I not tried it, I totally didn't even see it when I was perusing the thread.

It does fix it for me... though still leaves me absolutely confused.

I don't seem to have an i8042 loaded:
```
lsmod | grep 8042
```
returns nothing.

...and in fact if I modprobe:
```
$ sudo modprobe i8042
FATAL: Module i8042 not found.
```

But if it fixes it, I am not going to argue.

One ubuntu gripe about fixes/tweaks like this is that the apt updates don't seem to merge them in a reasonable fashion.  My memories of fedora with menu.lst changes is that it would carry the changes forward correctly and silently.  (For example, if you had 30 servers with serial consoles, you probably don't want to muck with menu.lst on all of them.)

Now... if I can only sort out why the system crashes on gnome logouts...

---

### Post by jdeslip on 2009-02-17
I have a Dell 1420 laptop and have this problem every fifth or so suspend/resume.  Is the i8042.reset fix just for HPs?  Were you guys having this problem on every single suspend/resume?

I also don't seem to have any errors in pm-suspend.log.

---

### Post by fedoraboy on 2009-02-17
> **jdeslip said:**
> I have a Dell 1420 laptop and have this problem every fifth or so suspend/resume.  Is the i8042.reset fix just for HPs?  Were you guys having this problem on every single suspend/resume?

I also don't seem to have any errors in pm-suspend.log.

I had issues with every single suspend.  On wakeup, it came back to life but lost mouse/kbd.  I could ssh in and it was working fine.

I've probably only tested suspend 2 times since the fix was posted, so if this is every 5th, I'm still screwed. :)

From what I can tell (I was unfamiliar with i8042 until today) this is a pretty common keyboard chipset.  You might try it.  It takes only a few seconds and a reboot.

My i8042 seems to be compiled into the kernel (as opposed to modprobed) so lsmod may or may not tell you anything.  But I can see stuff in /sys/devices/platform/i8042, so I guess that means its there.  :)

---

### Post by jdeslip on 2009-02-17
okay, I tried adding i8042.reset to the kernel line, but it didn't work (if anything made the problem more frequent).

---

### Post by bayvista on 2009-02-17
I have the same problem with an HP Pavillion and 8.10. I'll join this thread.

---

### Post by jmw86069 on 2009-02-17
Okay, I'm not an expert, but I can suggest some things to look into further.
```
cat /proc/bus/input/devices
```
In that file, you should be able to see some reference to the touchpad and keyboard. Here is just the chunk from my machine regarding the keyboard:
```
I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=120013
B: KEY=20000 28 0 0 500402100003 83803078f900d401 feffffdfffefffff ffffffffffffffff
B: MSC=10
B: LED=7
```
Note the "i8042" on the line beginning with "S: Sysfs=...". That should tell you the chipset being used.

I noticed a number of threads from Google when I searched for "i8042 kernel options" or simply "i8042 suspend"... not that they have clear answers... but this problem has been around several years. If it doesn't work for you, I suspect it is very, very close to the solution.

---

### Post by cygnus8595 on 2009-02-18
I'll try to add those scripts and re-add the i8042.reset kernel option, but I'm a little confused on one thing - does Ubuntu use acpi-support or pm-utils to run suspend/resume, or is it a combination of both? I guess I need to learn the exact steps that are taken when suspend/resume is initiated.

---

### Post by cygnus8595 on 2009-02-19
I added the two scripts and tried a suspend/resume, and I still got the same problem. I also have i8042.reset in my kernel options (I put it in the default).

---

### Post by bayvista on 2009-02-20
Re HP Laptop - the i8042 reset does not work for me. Also, tried the AIGLX mod but also no go. The laptop will hibernate OK but sticks on the spalsh screen during restart forcing a power off/on to restart.

I have attached my input devices.

---

### Post by jmw86069 on 2009-02-23
bayvista, from what little I have gleaned from other forums, the i8042.reset workaround is aimed at the Suspend/Resume and not the Hibernate/Resume.  My situation was that hibernate actually worked, but suspend got stuck with no functioning keyboard/mouse.

My setup: I have Ubuntu intrepid (8.10) with kernel 2.6.27-11, and I'm using ATI Catalyst 9.1.  I saw Catalyst 9.2 was released, so I would use that. But it didn't improve suspend over 9.1 from looking at the release notes.  You probably need 8.12 or more recent ATI Catalyst drivers. And make sure you've got "fglrx" in your /etc/X11/xorg.conf file. Or open a terminal and type "fglrxinfo" and hope you only see ATI and not Mesa, and a version number equal or higher than 2.1.8395. (That's what I have for Catalyst 9.1.)

If your hibernation gets stuck -- you may actually be lucky because you may not have a display/hibernation problem, it could just be some other module getting stuck during wakeup. Needle in a haystack finding which one, but check whatever log files you can (a good one is /var/log/kern.log) to watch what stuff gets unloaded before hibernation, and which get stuck during wakeup, show an error, or don't show at all.

Most likely suspects to stall a resume from hibernation? probably wireless or wired network driver, display driver, or another weird component like USB drive, webcam, sound card, etc.  But I do think the evidence exists for you to find it, if that helps. :-)

*EDIT* -- Try unplugging your USB wireless mouse? Maybe that's it? Otherwise, I didn't even ask what video card you had, so if it's not ATI my apologies. Still, update to the latest version for whatever it is if you can.

---

### Post by bayvista on 2009-02-23
Thanks for that. I'll work through it.

OK. Spent some time this morning. It seems that I am using Mesa. Don't know how to change that or do I need to? Display is beautifully clear.

Tried unplugging the wireless mouse. Then tried SUSPEND which worked OK. However, on opening the lid, lights came on but no display. Touchpad and keyboard have no effect. Had to do a power reset.

Had a look at the logs but don't really know what I am looking for. Filtered 'Error' Could not seem to copy/paste messages.

Thanks for trying

---

### Post by postilion on 2009-02-24
Just to help flesh out this thread.  I had the same Suspend/Resume problem with no keyboard upon resume.  I have a Compaq R4000 with Ubuntu 8.10 with kernel 2.27.12.  The i8042.reset fix worked just fine for me.

Thanks for the help!:p

Cheers,
    -nic

---

### Post by dranorter on 2009-03-02
I remember having this problem with my Macbook- except hibernate didn't work at all- but I don't remember what fixed it. I think it was upgrading to Intrepid. And I feel so silly not really remembering 'cuz now here is this new HP tx2z having the same problem and I have no idea what to do.

---

### Post by drmaas on 2009-03-14
> **jmw86069 said:**
> I'm happy to report that I have been tracking this issue along with you, and have been able to resume from suspend with functional touchpad and keyboard! Prior to then, I could resume from hibernate with no apparent issues, but resume from suspend resulted in a non-functioning keyboard and touchpad.

There are several very relevant threads and bugs still open, however, so I'm surprised you didn't stumble upon potential solutions.

The solution which worked for me was to add "i8042.reset" to the /boot/grub/menu.lst entry which contains stuff like "ro quiet splash" as noted at the bottom of the post here:
[http://ubuntuforums.org/archive/index.php/t-1038898.html](http://ubuntuforums.org/archive/index.php/t-1038898.html)
Fwiw here is my menu.lst entry in total, so you can see where to add "i8042.reset":
```
title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		88b99fce-0f2b-421d-9071-5974649671ce
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=88b99fce-0f2b-421d-9071-5974649671ce ro quiet splash i8042.reset
initrd		/boot/initrd.img-2.6.27-11-generic
quiet
```

There are other threads which suggest tweaks to acpi-support to unbind then bind i8042 for the keyboard and touchpad, but none worked for me. Interesting that hooking a USB keyboard worked fine, as did a USB mouse. When I typed in the commands to unbind/bind, they worked fine and restored a functioning laptop keyboard/touchpad. However I couldn't get them to work in the /etc/acpi/resume.d/ folder as these posts refer:
[http://ubuntuforums.org/showpost.php?p=2690982&postcount=14](http://ubuntuforums.org/showpost.php?p=2690982&postcount=14)
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/23497](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/23497)

Currently, I still have composite and AIGLX disabled, per other posts suggesting those changes are required for suspend/resume. I will definitely be testing various methods of re-enabling desktop effects. I do like the eye-candy, but I would also just appreciate hardware-accelerated everything else! These changes were added to /etc/X11/xorg.conf to disable Composite and AIGLX:
```
Section "Extensions"
        Option        "Composite"        "Disable"
EndSection
Section "ServerFlags"
       Option  "AIGLX" "off" 
EndSection
```

Let me know if adding the "i8042.reset" to your menu.lst entry helps! I may also post to the other threads to see if people find this fix helpful there too. (Can't believe the bug entry has been unresolved for year and a half!)

I have an HP Pavilion dv5-1120us running Ubuntu 8.10 x64.  Previously I had to type on the keyboard during resume in order for the built-in keyboard and mousepad to work.  Interestingly, my external usb mouse always worked after resume.  

Adding "i8042.reset" to my grub menu worked perfectly for me.  I can now suspend and resume, and the internal keyboard and mousepad always work.  Thanks for helping!

---

### Post by bayvista on 2009-03-14
I tried both of your suggestions (the i8042 patch and the xorg.conf patch) on my HP DV9000 to no avail. Neither Suspend or Hibernate restarts properly. I'm thinking of trying [www.sf.net/projects/suspend]("www.sf.net/projects/suspend"). Anyone tried this?

---

### Post by GroovyTrucker on 2009-03-30
Good news, if you have a HP dv4-1222nr. I've tested the i8042.reset addition to my boot menu and it works! I love this new laptop and suspend/hibernate not working was just about a show stopper for me. I don't know if sound resets properly WRT volume levels, but at least playback works if you download the new snapshot from alsa-project. Try [INDENT][[COLOR="Sienna"]http://ubuntuforums.org/showthread.php?t=1073090&highlight=snapshot+dv+sound[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1073090&highlight=snapshot+dv+sound")[/INDENT] for *that* solution.\\:D/

---

### Post by fornix on 2009-05-28
The entry in menu.lst worked for me!! 
BTW I am using hp pavilion dv5 and can confirm this solves the issue.

---

### Post by SOULRiDER on 2009-08-10
I have a HP Pavillion DV5 1250us and the GRUB fix didnt do it for me, in fact, my system locks in "Starting up..." when I select the option from GRUB.

Also, im running 9.04.
uname -a gives me
```
Linux SR388 2.6.28-15-generic #48-Ubuntu SMP Wed Jul 29 08:53:35 UTC 2009 x86_64 GNU/Linux
```
Suspend worked fine when I used the Live CD (9.04)

I hope this information may be useful.

---

### Post by carnagex420x on 2009-09-23
I also have a Dell 1420 and added i8042.reset to my boot options with no luck. I also tried changing my suspend mode and got different results each time. I found this thread [http://ubuntuforums.org/showthread.php?t=991404](http://ubuntuforums.org/showthread.php?t=991404), which also mentions [http://ubuntuforums.org/showthread.php?t=437596&highlight=keyboard+suspend](http://ubuntuforums.org/showthread.php?t=437596&highlight=keyboard+suspend). It uses the script mentioned before to unload and reload i8042, and makes the i8042.reset boot option unnecessary. I tried suspending and resuming a couple different ways with and without AC power before and after trying to make it fail. So far 6 w/o a problem. I'm also using "pm-utils" as a suspend option in my acpi-support. HOPE THIS HELPS! Solved for me.

---

