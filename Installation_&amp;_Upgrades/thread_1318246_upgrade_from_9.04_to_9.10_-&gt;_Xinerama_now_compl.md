---
title: "upgrade from 9.04 to 9.10 -&gt; Xinerama now completely fails"
date: 2009-11-07
forum: Installation &amp; Upgrades
---

### Post by fvillars on 2009-11-07
While I love Ubuntu, every new upgrade has its own new frustration. In previous vetrsion I have always been able to configure Xinerama without problems. This time I am stumped. I have every trick I know to no avail. In addition the Ctrl-Alt-Bkspc restart does not work nor can it be fixed by anything I have seen posted on this forum...and I have searched exhaustively.

Here is my xorg.conf:

# Xorg configuration created by system-config-display

Section "ServerLayout"
	Identifier     "Layout0"
	Screen      0  "Screen0" 0 0
	Screen      1  "Screen1" RightOf "Screen0"
	InputDevice    "Keyboard0" "CoreKeyboard"
	InputDevice    "Mouse0" "CorePointer"
EndSection


Section "Module"
	Load  "type1"
	Load  "freetype"
	Load  "glx"
	Load  "dbe"
	Load  "extmod"
EndSection

Section "ServerFlags"
	Option	    "Xinerama" "1"
	Option      "XkbOptions" "terminate:ctrl_alt_bksp"
EndSection

Section "InputDevice"

    # generated from default
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "Emulate3Buttons" "yes"
	Option	    "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from data in "/etc/sysconfig/keyboard"
	Identifier  "Keyboard0"
	Driver      "xkb"
	Option	    "XkbLayout" "us"
	Option	    "XkbModel" "pc105"
EndSection

Section "Monitor"

# HorizSync source: edid, VertRefresh source: edid
# Comment all HorizSync and VertSync values to use DDC:
 ### Comment all HorizSync and VertSync values to use DDC:
	Identifier   "Monitor0"
	VendorName   "Hitachi"
	ModelName    "CM2110M"
	HorizSync    15.0 - 93.0
	VertRefresh  56.0 - 75.0
	Gamma        1
	Option	    "DPMS"
EndSection

Section "Monitor"

# HorizSync source: edid, VertRefresh source: edid
# Comment all HorizSync and VertSync values to use DDC:
 ### Comment all HorizSync and VertSync values to use DDC:
	Identifier   "Monitor1"
	VendorName   "Gateway"
	ModelName    "Vivitron21"
	HorizSync    31.0 - 92.0
	VertRefresh  60.0 - 75.0
	Gamma        1
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "Videocard1"
	Driver      "nvidia"
	#VendorName  "NVIDIA Corporation"
	#BoardName   "GeForce 6200"
	#BusID       "PCI:2:9:0"
	#Option      "UseInt10Module" "1"
EndSection

Section "Device"
	Identifier  "Videocard0"
	Driver      "nvidia"
	#VendorName  "Videocard Vendor"
	#BoardName   "nVidia Corporation C51 [GeForce 6150 LE]"
	#BusID       "PCI:0:5:0"
	#Option      "UseInt10Module" "1"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Videocard0"
	Monitor    "Monitor0"
	DefaultDepth     24
	Option	    "metamodes" "1024x768 +0+0; 800x600 +0+0; 640x480 +0+0"
	SubSection "Display"
		Depth     24
		Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen1"
	Device     "Videocard1"
	Monitor    "Monitor1"
	DefaultDepth     24
	Option	    "metamodes" "1024x768 +0+0; 800x600 +0+0; 640x480 +0+0"
	SubSection "Display"
		Depth     24
		Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection



And here is my xorg log:


X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server x86_64 Ubuntu
Current Operating System: Linux Zanadu 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64
Kernel command line: root=UUID=b34eb712-3fcb-4476-a9ff-4d69bb47d84e ro quiet splash noapic
Build Date: 26 October 2009  05:19:56PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Nov  7 11:50:42 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Videocard0"
(**) |-->Screen "Screen1" (1)
(**) |   |-->Monitor "Monitor1"
(**) |   |-->Device "Videocard1"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(**) Option "Xinerama" "1"
(==) Automatically adding devices
(==) Automatically enabling devices
(**) Xinerama: enabled
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
(WW) Disabling Mouse0
(II) Loader magic: 0xb40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0:0:5:0) 10de:0241:103c:2a41 nVidia Corporation C51 [GeForce 6150 LE] rev 162, Mem @ 0xfc000000/16777216, 0xe0000000/268435456, 0xfb000000/16777216, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
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
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "type1"
(WW) Warning, couldn't open module type1
(II) UnloadModule: "type1"
(EE) Failed to load module "type1" (module does not exist, 0)
(II) LoadModule: "freetype"
(WW) Warning, couldn't open module freetype
(II) UnloadModule: "freetype"
(EE) Failed to load module "freetype" (module does not exist, 0)
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  190.42  Tue Oct 20 21:19:30 PDT 2009
(II) Loading extension GLX
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
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
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) LoadModule: "xkb"
(WW) Warning, couldn't open module xkb
(II) UnloadModule: "xkb"
(EE) Failed to load module "xkb" (module does not exist, 0)
(II) NVIDIA dlloader X Driver  190.42  Tue Oct 20 20:42:04 PDT 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 00@00:05:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
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
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(**) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "MetaModes" "1024x768 +0+0; 800x600 +0+0; 640x480 +0+0"
(**) Nov 07 11:50:53 NVIDIA(0): Enabling RENDER acceleration
(II) Nov 07 11:50:54 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Nov 07 11:50:54 NVIDIA(0):     enabled.
(II) Nov 07 11:50:58 NVIDIA(0): NVIDIA GPU GeForce 6150 LE (C51) at PCI:0:5:0 (GPU-0)
(--) Nov 07 11:50:58 NVIDIA(0): Memory: 262144 kBytes
(--) Nov 07 11:50:58 NVIDIA(0): VideoBIOS: 05.51.28.45.83
(--) Nov 07 11:50:58 NVIDIA(0): Interlaced video modes are supported on this GPU
(--) Nov 07 11:50:58 NVIDIA(0): Connected display device(s) on GeForce 6150 LE at PCI:0:5:0:
(--) Nov 07 11:50:58 NVIDIA(0):     Hitachi (CRT-0)
(--) Nov 07 11:50:58 NVIDIA(0): Hitachi (CRT-0): 350.0 MHz maximum pixel clock
(II) Nov 07 11:50:58 NVIDIA(0): Assigned Display Device: CRT-0
(II) Nov 07 11:50:58 NVIDIA(0): Validated modes:
(II) Nov 07 11:50:58 NVIDIA(0):     "1024x768+0+0"
(II) Nov 07 11:50:58 NVIDIA(0):     "800x600+0+0"
(II) Nov 07 11:50:58 NVIDIA(0):     "640x480+0+0"
(II) Nov 07 11:50:58 NVIDIA(0): Virtual screen size determined to be 1024 x 768
(--) Nov 07 11:50:58 NVIDIA(0): DPI set to (65, 65); computed from "UseEdidDpi" X config
(--) Nov 07 11:50:58 NVIDIA(0):     option
(==) Nov 07 11:50:58 NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
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
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) Nov 07 11:50:58 NVIDIA(0): Initialized GPU GART.
(II) Nov 07 11:50:59 NVIDIA(0): Setting mode "1024x768+0+0"
(II) Loading extension NV-GLX
(II) Nov 07 11:50:59 NVIDIA(0): Initialized OpenGL Acceleration
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) Nov 07 11:50:59 NVIDIA(0): Initialized X Rendering Acceleration
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
(II) Initializing extension GLX
(II) LoadModule: "xkb"
(WW) Warning, couldn't open module xkb
(II) UnloadModule: "xkb"
(EE) Failed to load module "xkb" (module does not exist, 0)
(EE) No input driver matching `xkb'
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 2.2.5
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us,fr"
(**) Option "xkb_variant" ","
(**) Option "xkb_options" "grp:alts_toggle,lv3:alt_switch,compose:lwin,terminate:ctrl_alt_bksp"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us,fr"
(**) Option "xkb_variant" ","
(**) Option "xkb_options" "grp:alts_toggle,lv3:alt_switch,compose:lwin,terminate:ctrl_alt_bksp"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us,fr"
(**) Option "xkb_variant" ","
(**) Option "xkb_options" "grp:alts_toggle,lv3:alt_switch,compose:lwin,terminate:ctrl_alt_bksp"
(II) config/hal: Adding input device PS2++ Logitech Mouse
(**) PS2++ Logitech Mouse: always reports core events
(**) PS2++ Logitech Mouse: Device: "/dev/input/event4"
(II) PS2++ Logitech Mouse: Found 8 mouse buttons
(II) PS2++ Logitech Mouse: Found x and y relative axes
(II) PS2++ Logitech Mouse: Configuring as mouse
(**) PS2++ Logitech Mouse: YAxisMapping: buttons 4 and 5
(**) PS2++ Logitech Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "PS2++ Logitech Mouse" (type: MOUSE)
(**) PS2++ Logitech Mouse: (accel) keeping acceleration scheme 1
(**) PS2++ Logitech Mouse: (accel) filter chain progression: 2.00
(**) PS2++ Logitech Mouse: (accel) filter stage 0: 20.00 ms
(**) PS2++ Logitech Mouse: (accel) set acceleration profile 0
(II) PS2++ Logitech Mouse: initialized for relative axes.
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



Note that NVIDIA(0) loads but NVIDIA(1) never does....????Why



When I run lspci the second video card doesn't even show up. This has never happened in previous installations:

frederick@Zanadu:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [GeForce 6150 LE] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTra



Need less to say I would appreciate any advice...and Thanks in advance to anyone who cares to wade through the above mess.

---

