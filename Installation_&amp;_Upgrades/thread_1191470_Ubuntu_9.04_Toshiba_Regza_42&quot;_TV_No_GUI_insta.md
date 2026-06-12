---
title: "Ubuntu 9.04 Toshiba Regza 42&quot; TV No GUI installer"
date: 2009-06-19
forum: Installation &amp; Upgrades
---

### Post by Sean R on 2009-06-19
I had Jaunty installed and everything was working great. Full 1080p resolution on my tv. Rebooted one day, and my gui was gone. Read through the log files and noticed things in xorg.log like "Screens found but none have a usable confiruation", or "No screens found."

Tried reinstalling with Jaunty 64 install cd (same cd that worked before) and no gui installer.

Tried latest LiveCD of Gentoo and no GUI. Same errors as Jaunty gives.

VESA driver works in Jaunty, but crappy resolution. Tried nvidia driver 180 from hardware drivers and no luck. Tried manually installing newest nvidia driver from nvidia.com and no luck.

ddcprobe gives a bunch of resolutions but bottom two lines of output might be of use:
"edid:"
"edidfail"

Windows XP Pro dual boot works perfectly at 1080p resolution.

Hardware:
NVidia 9600 GT Video Card
Toshiba 42" TV (42HL167)
```

Xorg.0.log.....

X.Org X Server 1.6.0

Release Date: 2009-2-25

X Protocol Version 11, Revision 0

Build Operating System: Linux 2.6.24-15-server x86_64 Ubuntu

Current Operating System: Linux sean-desktop 2.6.28-13-generic #44-Ubuntu SMP Tue Jun 2 07:55:09 UTC 2009 x86_64

Build Date: 09 April 2009  02:11:54AM

xorg-server 2:1.6.0-0ubuntu14 (buildd@crested.buildd) 

	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)

	to make sure that you have the latest version.

Markers: (--) probed, (**) from config file, (==) default setting,

	(++) from command line, (!!) notice, (II) informational,

	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.

(==) Log file: "/var/log/Xorg.0.log", Time: Thu Jun 18 21:37:48 2009

(==) Using config file: "/etc/X11/xorg.conf"

(==) ServerLayout "Layout0"

(**) |-->Screen "Screen0" (0)

(**) |   |-->Monitor "Monitor0"

(**) |   |-->Device "Device0"

(**) |-->Input Device "Keyboard0"

(**) |-->Input Device "Mouse0"

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

(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.

(WW) Disabling Keyboard0

(WW) Disabling Mouse0

(II) Loader magic: 0xb40

(II) Module ABI versions:

	X.Org ANSI C Emulation: 0.4

	X.Org Video Driver: 5.0

	X.Org XInput driver : 4.0

	X.Org Server Extension : 2.0

(II) Loader running on linux

(++) using VT number 7



(--) PCI:*(0@1:0:0) nVidia Corporation G94 [GeForce 9600 GT] rev 161, Mem @ 0xfd000000/16777216, 0xd0000000/268435456, 0xfa000000/33554432, I/O @ 0x0000cc00/128, BIOS @ 0x????????/524288

(II) Open ACPI successful (/var/run/acpid.socket)

(II) System resource ranges:

	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]

	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]

	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]

	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]

	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]

	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]

(II) "extmod" will be loaded by default.

(II) "dbe" will be loaded by default.

(II) "glx" will be loaded. This was enabled by default and also specified in the config file.

(II) "record" will be loaded by default.

(II) "dri" will be loaded by default.

(II) "dri2" will be loaded by default.

(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so

dlopen: /usr/lib/xorg/modules/extensions//libglx.so: undefined symbol: _nv000133gl

(EE) Failed to load /usr/lib/xorg/modules/extensions//libglx.so

(II) UnloadModule: "glx"

(EE) Failed to load module "glx" (loader failed, 7)

(II) LoadModule: "extmod"

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so

(II) Module extmod: vendor="X.Org Foundation"

	compiled for 1.6.0, module version = 1.0.0

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

	compiled for 1.6.0, module version = 1.0.0

	Module class: X.Org Server Extension

	ABI class: X.Org Server Extension, version 2.0

(II) Loading extension DOUBLE-BUFFER

(II) LoadModule: "record"

(II) Loading /usr/lib/xorg/modules/extensions//librecord.so

(II) Module record: vendor="X.Org Foundation"

	compiled for 1.6.0, module version = 1.13.0

	Module class: X.Org Server Extension

	ABI class: X.Org Server Extension, version 2.0

(II) Loading extension RECORD

(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so

(II) Module dri: vendor="X.Org Foundation"

	compiled for 1.6.0, module version = 1.0.0

	ABI class: X.Org Server Extension, version 2.0

(II) Loading extension XFree86-DRI

(II) LoadModule: "dri2"

(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so

(II) Module dri2: vendor="X.Org Foundation"

	compiled for 1.6.0, module version = 1.0.0

	ABI class: X.Org Server Extension, version 2.0

(II) Loading extension DRI2

(II) LoadModule: "nvidia"

(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so

(II) Module nvidia: vendor="NVIDIA Corporation"

	compiled for 4.0.2, module version = 1.0.0

	Module class: X.Org Video Driver

(II) NVIDIA dlloader X Driver  173.14.16  Sat Jan 24 19:11:05 PST 2009

(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs

(II) Primary Device is: PCI 01@00:00:0

(II) Loading sub module "fb"

(II) LoadModule: "fb"

(II) Loading /usr/lib/xorg/modules//libfb.so

(II) Module fb: vendor="X.Org Foundation"

	compiled for 1.6.0, module version = 1.0.0

	ABI class: X.Org ANSI C Emulation, version 0.4

(II) Loading sub module "wfb"

(II) LoadModule: "wfb"

(II) Loading /usr/lib/xorg/modules//libwfb.so

(II) Module wfb: vendor="X.Org Foundation"

	compiled for 1.6.0, module version = 1.0.0

	ABI class: X.Org ANSI C Emulation, version 0.4

(II) Loading sub module "ramdac"

(II) LoadModule: "ramdac"

(II) Module "ramdac" already built-in

(II) resource ranges after probing:

	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]

	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]

	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]

	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]

	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]

	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]

(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32

(==) NVIDIA(0): RGB weight 888

(==) NVIDIA(0): Default visual is TrueColor

(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)

(**) NVIDIA(0): Option "NoLogo" "True"

(**) NVIDIA(0): Enabling RENDER acceleration

(EE) NVIDIA(0): Failed to initialize the GLX module; please check in your X

(EE) NVIDIA(0):     log file that the GLX module has been loaded in your X

(EE) NVIDIA(0):     server, and that the module is the NVIDIA GLX module.  If

(EE) NVIDIA(0):     you continue to encounter problems, Please try

(EE) NVIDIA(0):     reinstalling the NVIDIA driver.

(II) NVIDIA(GPU-0): No display devices connected; falling back to: CRT-0

(WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0

(II) NVIDIA(0): NVIDIA GPU GeForce 9600 GT (G94) at PCI:1:0:0 (GPU-0)

(--) NVIDIA(0): Memory: 524288 kBytes

(--) NVIDIA(0): VideoBIOS: 62.94.0d.00.75

(II) NVIDIA(0): Detected PCI Express Link width: 16X

(--) NVIDIA(0): Interlaced video modes are supported on this GPU

(--) NVIDIA(0): Connected display device(s) on GeForce 9600 GT at PCI:1:0:0:

(--) NVIDIA(0):     CRT-0

(--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock

(II) NVIDIA(0): Assigned Display Device: CRT-0

(==) NVIDIA(0): 

(==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"

(==) NVIDIA(0):     will be used as the requested mode.

(==) NVIDIA(0): 

(II) NVIDIA(0): Validated modes:

(II) NVIDIA(0):     "nvidia-auto-select"

(II) NVIDIA(0): Virtual screen size determined to be 1024 x 768

(WW) NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI

(WW) NVIDIA(0):     from CRT-0's EDID.

(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default

(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.

(--) Depth 24 pixmap format is 32 bpp

(II) do I need RAC?  No, I don't.

(II) resource ranges after preInit:

	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]

	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]

	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]

	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]

	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]

	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]

(II) NVIDIA(0): Initialized GPU GART.

(II) NVIDIA(0): Setting mode "nvidia-auto-select"

(II) Loading extension NV-GLX

(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized

(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture

(==) NVIDIA(0): Backing store disabled

(==) NVIDIA(0): Silken mouse enabled

(**) Option "dpms"

(**) NVIDIA(0): DPMS enabled

(II) Loading extension NV-CONTROL

(==) RandR enabled

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

(II) config/hal: Adding input device Microsft Microsoft Wireless Desktop Receiver 3.1

(II) LoadModule: "evdev"

(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so

(II) Module evdev: vendor="X.Org Foundation"

	compiled for 1.6.0, module version = 2.1.1

	Module class: X.Org XInput Driver

	ABI class: X.Org XInput driver, version 4.0

(**) Microsft Microsoft Wireless Desktop Receiver 3.1: always reports core events

(**) Microsft Microsoft Wireless Desktop Receiver 3.1: Device: "/dev/input/event5"

(II) Microsft Microsoft Wireless Desktop Receiver 3.1: Found 6 mouse buttons

(II) Microsft Microsoft Wireless Desktop Receiver 3.1: Found x and y relative axes

(II) Microsft Microsoft Wireless Desktop Receiver 3.1: Found keys

(II) Microsft Microsoft Wireless Desktop Receiver 3.1: Configuring as mouse

(II) Microsft Microsoft Wireless Desktop Receiver 3.1: Configuring as keyboard

(**) Microsft Microsoft Wireless Desktop Receiver 3.1: YAxisMapping: buttons 4 and 5

(**) Microsft Microsoft Wireless Desktop Receiver 3.1: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200

(II) XINPUT: Adding extended input device "Microsft Microsoft Wireless Desktop Receiver 3.1" (type: KEYBOARD)

(**) Option "xkb_rules" "evdev"

(**) Microsft Microsoft Wireless Desktop Receiver 3.1: xkb_rules: "evdev"

(**) Option "xkb_model" "pc105"

(**) Microsft Microsoft Wireless Desktop Receiver 3.1: xkb_model: "pc105"

(**) Option "xkb_layout" "us"

(**) Microsft Microsoft Wireless Desktop Receiver 3.1: xkb_layout: "us"

(**) Microsft Microsoft Wireless Desktop Receiver 3.1: (accel) keeping acceleration scheme 1

(**) Microsft Microsoft Wireless Desktop Receiver 3.1: (accel) filter chain progression: 2.00

(**) Microsft Microsoft Wireless Desktop Receiver 3.1: (accel) filter stage 0: 20.00 ms

(**) Microsft Microsoft Wireless Desktop Receiver 3.1: (accel) set acceleration profile 0

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

(II) config/hal: Adding input device Microsft Microsoft Wireless Desktop Receiver 3.1

(**) Microsft Microsoft Wireless Desktop Receiver 3.1: always reports core events

(**) Microsft Microsoft Wireless Desktop Receiver 3.1: Device: "/dev/input/event4"

(II) Microsft Microsoft Wireless Desktop Receiver 3.1: Found keys

(II) Microsft Microsoft Wireless Desktop Receiver 3.1: Configuring as keyboard

(II) XINPUT: Adding extended input device "Microsft Microsoft Wireless Desktop Receiver 3.1" (type: KEYBOARD)

(**) Option "xkb_rules" "evdev"

(**) Microsft Microsoft Wireless Desktop Receiver 3.1: xkb_rules: "evdev"

(**) Option "xkb_model" "pc105"

(**) Microsft Microsoft Wireless Desktop Receiver 3.1: xkb_model: "pc105"

(**) Option "xkb_layout" "us"

(**) Microsft Microsoft Wireless Desktop Receiver 3.1: xkb_layout: "us"

(II) Open ACPI successful (/var/run/acpid.socket)

(II) NVIDIA(0): Setting mode "nvidia-auto-select"

(II) Microsft Microsoft Wireless Desktop Receiver 3.1: Close

(II) UnloadModule: "evdev"

(II) Macintosh mouse button emulation: Close

(II) UnloadModule: "evdev"

(II) Microsft Microsoft Wireless Desktop Receiver 3.1: Close

(II) UnloadModule: "evdev"

 ddxSigGiveUp: Closing log
```

Does anybody have any ideas? I have been messing with this for over a week now. I have tried another video card (8600GTS) and have the exact same problem. But, I have already ruled out hardware since Windows XP Pro works perfectly.

Very frustrated cause I hate Windows but have to use it for now...

---

### Post by Sean R on 2009-06-21
Problem Solved:

Bad DVI-HDMI cable.

---

### Post by bumparocky on 2009-07-05
can you share your xorg.conf??
I am trying to get one working with HDMI under Linux mint 7

---

### Post by bumparocky on 2009-07-07
in particular , have you run ddcprobe since replacing the cable.

I get the same result for ddcprobe and believe the cable is good since I had it working at one time with a previous release.

---

### Post by spindley on 2010-04-12
> **bumparocky said:**
> can you share your xorg.conf??
I am trying to get one working with HDMI under Linux mint 7

Bumping an old thread.  Did you ever figure this out?  I have a 46" Toshiba Regza (46XV645U), and I can't get any display with drivers installed (Ubuntu 9.10 & 10.04 beta 2).  I've tried both an Nvidia card and an ATI card out to the TV via DVI --> HDMI (cable is tested and is fine), so the problem is obviously something to do with the TV itself.
It seems that people have problems with Toshiba's, but I hope there's some sort of solution out there.  None of the Modelines I've tried have worked so far though.

Thanks.

---

