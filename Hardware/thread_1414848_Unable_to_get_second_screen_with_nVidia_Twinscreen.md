---
title: "Unable to get second screen with nVidia Twinscreen setup"
date: 2010-02-24
forum: Hardware
---

### Post by Jonners59 on 2010-02-24
I have been at this for ages.  I have looked through loads of threads, and had some dialogue in other Threads.  In trying to get this working I messed up my video drivers and had to rebuild them, thanks to great help from the forum.  All are fixed now and I am back to where I was at the start.

I have the correct drivers installed, but I ONLY get one screen up.  In the default, built in, low res, I get both, but showing the same image.  I want the two screens to show an extended image.  It works in Windows, and has done so for many years, so I know the card works.

I have tried everything in all the threads and on other forums, but nothing has worked for me.  I even have the nVidia manual which does not help.  Please can someone assist me in getting the settings corrected.

Attached is a screenshot of my nVidia X-Server Settings which shows that the X Server Display has an error

And here is my X.org log:
```

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux BaroniPC 2.6.31-20-generic-pae #57-Ubuntu SMP Mon Feb 8 10:23:59 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-20-generic-pae root=UUID=e8df5503-5425-41e5-8f60-bb05a26d6591 ro quiet splash
Build Date: 14 November 2009  05:48:26PM
xorg-server 2:1.6.4-2ubuntu4.1 (buildd@) 
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Feb 24 07:09:18 2010
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
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 5.0
    X.Org XInput driver : 4.0
    X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0:1:0:0) 10de:0322:1682:203c nVidia Corporation NV34 [GeForce FX 5200] rev 161, Mem @ 0xf2000000/16777216, 0xe0000000/268435456, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [5] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [6] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [7] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [8] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [9] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [10] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [11] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [12] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [13] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [14] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [15] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [16] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [17] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [18] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [19] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [20] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [21] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [22] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [23] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [24] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [25] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [26] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [27] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [28] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [29] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
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
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  173.14.20  Thu Jun 25 19:49:59 PDT 2009
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
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  173.14.20  Thu Jun 25 19:28:52 PDT 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
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
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [5] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [6] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [7] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [8] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [9] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [10] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [11] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [12] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [13] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [14] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [15] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [16] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [17] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [18] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [19] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [20] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [21] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [22] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [23] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [24] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [25] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [26] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [27] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [28] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [29] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce FX 5200 (NV34) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 04.34.20.27.02
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce FX 5200 at PCI:1:0:0:
(--) NVIDIA(0):     Samsung SyncMaster (CRT-0)
(--) NVIDIA(0):     NUL (DFP-0)
(--) NVIDIA(0): Samsung SyncMaster (CRT-0): 350.0 MHz maximum pixel clock
(--) NVIDIA(0): NUL (DFP-0): 135.0 MHz maximum pixel clock
(--) NVIDIA(0): NUL (DFP-0): Internal Single Link TMDS
(II) NVIDIA(0): Assigned Display Device: CRT-0
(==) NVIDIA(0): 
(==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) NVIDIA(0):     will be used as the requested mode.
(==) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(--) NVIDIA(0): DPI set to (85, 86); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [5] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [6] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [7] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [8] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [9] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [10] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [11] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [12] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [13] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [14] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [15] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [16] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [17] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [18] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [19] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [20] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [21] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [22] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [23] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [24] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [25] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [26] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [27] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [28] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [29] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Initialized AGP GART.
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
(II) Initializing extension GLX
(II) config/hal: Adding input device Power Button
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 2.2.5
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "gb"
(II) config/hal: Adding input device ImExPS/2 Generic Explorer Mouse
(**) ImExPS/2 Generic Explorer Mouse: always reports core events
(**) ImExPS/2 Generic Explorer Mouse: Device: "/dev/input/event4"
(II) ImExPS/2 Generic Explorer Mouse: Found 9 mouse buttons
(II) ImExPS/2 Generic Explorer Mouse: Found x and y relative axes
(II) ImExPS/2 Generic Explorer Mouse: Found scroll wheel(s)
(II) ImExPS/2 Generic Explorer Mouse: Configuring as mouse
(**) ImExPS/2 Generic Explorer Mouse: YAxisMapping: buttons 4 and 5
(**) ImExPS/2 Generic Explorer Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "ImExPS/2 Generic Explorer Mouse" (type: MOUSE)
(**) ImExPS/2 Generic Explorer Mouse: (accel) keeping acceleration scheme 1
(**) ImExPS/2 Generic Explorer Mouse: (accel) filter chain progression: 2.00
(**) ImExPS/2 Generic Explorer Mouse: (accel) filter stage 0: 20.00 ms
(**) ImExPS/2 Generic Explorer Mouse: (accel) set acceleration profile 0
(II) ImExPS/2 Generic Explorer Mouse: initialized for relative axes.
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
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
```
(II) Macintosh mouse button emulation: initialized for relative axes.

---

### Post by Jonners59 on 2010-02-24
In addition to below, I have tried to open the config in Terminal as per other threads, but nothing happens.  ALl suggest creating a backup which is the first line
[B] 	> Quote:
 	 	 		 			 				sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak 			 		 	 	 
[/B]Step 2 runs the NVIDIA utility to generate a new xorg.conf file that the utility can actually read.
[B] 	Quote:
 	 	 		 			 				sudo nvidia-xconfig 			 		 	 	 
[/B]Step 3 runs the graphical NVIDIA setup tool as root, so you can actually save your changes.
[B] 	Quote:
 	 	 		 			 				sudo nvidia-settings 			 		 	 	 
[/B]If this does not work then after step 1, do **sudo rm /etc/X11/xorg.conf** to delete your current xorg.conf file. Then run **sudo nvidia-xconfig** and [B]sudo nvidia-settings
---------------------------------------------------------------[/B]
I've** tried all these** countless times and none work, so I opened the folder where the files/logs are stored.  The enclosed screen shot shows what I found.  These configs are just text files, so **could they be manually changed?**

If so** to what?**

Also there seem to be rather a lot of them. ** Should most or all be removed** and start again?

**Bu**t what of the** nVidia X-Server Setting**s which shows that the X Server Display has an error mentioned below?

---

### Post by Jonners59 on 2010-02-25
I reinstalled Ubuntu to fix this....

---

### Post by realzippy on 2010-02-26
Open a terminal,type:

**LANG=C nvidia-settings**

Does it still say:

[I]Failed to query NoScanout for screen0
[/I]

To see content of xorg.conf type

[B]gedit /etc/X11/xorg.conf
[/B]
can you post content?

---

### Post by Jonners59 on 2010-02-26
> **realzippy said:**
> Open a terminal,type:

**LANG=C nvidia-settings**

Does it still say:

*Failed to query NoScanout for screen0*

No, but it did yesterday before I rebuilt everything and after until I made my own config.  It NOW says:
ERROR: Cannot open display 'BaroniPC:0.0'.


ERROR: Unable to assign attribute CursorShadow specified on line 20 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute CursorShadowAlpha specified on line 21 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute CursorShadowRed specified on line 22 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute CursorShadowGreen specified on line 23 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute CursorShadowBlue specified on line 24 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute CursorShadowXOffset specified on line 25 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute CursorShadowYOffset specified on line 26 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute SyncToVBlank specified on line 27 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute LogAniso specified on line 28 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute FSAA specified on line 29 of configuration
       file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute TextureSharpen specified on line 30 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute GammaCorrectedAALines specified on line 31 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute AllowFlipping specified on line 32 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute FSAAAppControlled specified on line 33 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute LogAnisoAppControlled specified on line 34 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute OpenGLImageSettings specified on line 35 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute RedBrightness specified on line 36 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute GreenBrightness specified on line 37 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute BlueBrightness specified on line 38 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute RedContrast specified on line 39 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute GreenContrast specified on line 40 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute BlueContrast specified on line 41 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute RedGamma specified on line 42 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute GreenGamma specified on line 43 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute BlueGamma specified on line 44 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute DigitalVibrance specified on line 45 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute DigitalVibrance specified on line 46 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute ImageSharpening specified on line 47 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute ImageSharpening specified on line 48 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute XVideoTextureSyncToVBlank specified on line
       49 of configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoBlitterSyncToVBlank specified on line
       50 of configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoSyncToDisplay specified on line 51 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).

> **realzippy said:**
> 
To see content of xorg.conf type

[B]gedit /etc/X11/xorg.conf
[/B]
can you post content?
This shows the file I created!!!

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@palmer)  Sun Feb  1 20:21:04 UTC 2009

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5200"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0, DFP: nvidia-auto-select +1280+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---

### Post by realzippy on 2010-02-26
The xorg.conf file should set Desktop as one large screen.Second monitor right of....isn't that what you wanted to achieve?What is the problem?


Sorry,bit confused...

---

### Post by Jonners59 on 2010-02-26
Sorry, Realzippy
I keep loosing windows.  When I am working in a window - Firefox, Evolution, etc, the application just shuts down.  I've seen this before - ANOTHER issue to sort out!

---

### Post by Jackzor on 2010-02-26
All of the xorg.conf file.. just.. move them to a back up folder on your home folder first of all.

Then run sudo nvidia-xconfig 

Then sudo nividia-settings

While that is up, read you xorg file and make sure it is default and correct. and post a new screenshot of the nvidia settings.

---

### Post by Jonners59 on 2010-02-28
> **Jackzor said:**
> 
Then sudo nividia-settings

While that is up, read you xorg file and make sure it is default and correct. and post a new screenshot of the nvidia settings.

It says Command not found....

---

### Post by slamhound on 2010-02-28
I wonder if it is something unique to the 5200.  I have the same card in a computer I'm testing, and I have the exact same symptoms.  It seems that most of the other threads that I've come across with related problems also have this card.  

At one point, I also had the "command not found" for nvidia-xconfig, even though the nvidia drivers were installed (and I've done this many times on earlier systems, so I'm relatively familiar with the process).

I reinstalled with alpha 3 and now I can get nvidia-settings and nvidia-xconfig to run, but I never get the drivers to work correctly.  I have still have the same issue with nvidia-settings as you do.  Hardware drivers show that nvidia-173 is installed but not in use.  I haven't been able to figure out how to get them to be used.

---

### Post by Jonners59 on 2010-02-28
> **slamhound said:**
> I wonder if it is something unique to the 5200.  I have the same card in a computer I'm testing, and I have the exact same symptoms.  It seems that most of the other threads that I've come across with related problems also have this card.  

At one point, I also had the "command not found" for nvidia-xconfig, even though the nvidia drivers were installed (and I've done this many times on earlier systems, so I'm relatively familiar with the process).

I reinstalled with alpha 3 and now I can get nvidia-settings and nvidia-xconfig to run, but I never get the drivers to work correctly.  I have still have the same issue with nvidia-settings as you do.  Hardware drivers show that nvidia-173 is installed but not in use.  I haven't been able to figure out how to get them to be used.

Maybe.  I am not as familiar as most...
I have managed to get mine going now, so not too bother, until it all goes wrong again!

I fudged it by creating my own config.  I copied the original to a safe place, then deleted all the existing conf files - ALL of them and then opened X-Server.  It then created a new one which I set up as I wanted - it still would not save the config, so...  I copied the contents in to one of my copied configs from step 1 and then deleted all the configs again and moved my home created version in to the location where the original was.  Re booted and it worked.  Hope that makes sense.  A real fudge.

---

### Post by daydreamer2025 on 2010-03-02
> **Jonners59 said:**
> Maybe.  I am not as familiar as most...
I have managed to get mine going now, so not too bother, until it all goes wrong again!

I've had similar problems with my system (Geforce 5600 Go laptop). Previous releases, I could have dual TV-out and monitor working perfectly. Upgraded to the latest kernel and had a real fun-time dealing with the "nouveau" driver - it ended up being blacklisted, uninstalling the correct driver - Only the 173xx drivers works with these old cards.
I copied across my old xorg.conf which worked perfectly, but still get that NoScanout warning
(bzflag works perfectly along with my shader based programs).

---

