---
title: "Monitor incorrectly detected with 9.10 upgrade"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by BenRitchie on 2009-10-30
Hi folks. I've just upgraded by Atom 330 (Intel 845G/GZ graphics, Acer x233h 1920x1080 monitor) from 9.04 to 9.10, and i'm now stuck in 1024x768 resolution. Everything was fine with 9.04

Display settings detects the monitor as an Acer 20", which is wrong. Looking at /var/log/Xorg.0.log shows the monitor ID correctly. 

```

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux Atom 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686
Kernel command line: root=UUID=8737c4a0-05f4-4859-8614-436ca67b81ab ro quiet splash 
Build Date: 26 October 2009  05:15:02PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Oct 30 12:21:54 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Configured Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)"
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
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 5.0
    X.Org XInput driver : 4.0
    X.Org Server Extension : 2.0
(II) Loader running on linux
(--) using VT number 7

(--) PCI:*(0:0:2:0) 8086:2772:1297:3166 Intel Corporation 82945G/GZ Integrated Graphics Controller rev 2, Mem @ 0xfdf00000/524288, 0xd0000000/268435456, 0xfdf80000/262144, I/O @ 0x0000ff00/8
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
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
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 2.9.0
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, Clarkdale, Arrandale
(II) Primary Device is: PCI 00@00:02:0
(II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(**) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) 945G
(--) intel(0): Chipset: "945G"
(II) intel(0): Output VGA1 using monitor section Configured Monitor
(II) intel(0): Output DVI1 has no monitor section
(II) intel(0): EDID for output VGA1
(II) intel(0): Manufacturer: ACR  Model: 9c  Serial#: 2222999560
(II) intel(0): Year: 2008  Week: 48
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) intel(0): Sync:  Separate
(II) intel(0): Max Image Size [cm]: horiz.: 44  vert.: 25
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: Off; RGB/Color Display
(II) intel(0): Default color space is primary color space
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) intel(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
(II) intel(0): Supported established timings:
(II) intel(0): 720x400@70Hz
(II) intel(0): 640x480@60Hz
(II) intel(0): 640x480@67Hz
(II) intel(0): 800x600@56Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 1024x768@60Hz
(II) intel(0): 1024x768@70Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
(II) intel(0): #0: hsize: 1920  vsize 1080  refresh: 60  vid: 49361
(II) intel(0): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) intel(0): #2: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) intel(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): #4: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 148.5 MHz   Image Size:  443 x 249 mm
(II) intel(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
(II) intel(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
(II) intel(0): Ranges: V min: 55 V max: 75 Hz, H min: 30 H max: 80 kHz, PixClock max 180 MHz
(II) intel(0): Monitor name: X233H
(II) intel(0): Serial No: LFN0B0043900
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff0004729c0008488084
(II) intel(0):     30120103682c19782eee95a3544c9926
(II) intel(0):     0f5054b30c00d1c0714f810081809500
(II) intel(0):     010101010101023a801871382d40582c
(II) intel(0):     4500bbf910000004000000fd00374b1e
(II) intel(0):     5012000a202020202020000000fc0058
(II) intel(0):     323333480a20202020202020000000ff
(II) intel(0):     004c464e30423030343339303020006f
(II) intel(0): EDID vendor "ACR", prod id 156
(II) intel(0): DDCModeFromDetailedTiming: 1920x1080 Warning: We only handle separate sync.
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): EDID for output DVI1
(II) intel(0): Output VGA1 connected
(II) intel(0): Output DVI1 disconnected
(II) intel(0): Using exact sizes for initial modes
(II) intel(0): Output VGA1 using initial mode 720x400
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(**) intel(0): Display dimensions: (440, 250) mm
(**) intel(0): DPI set to (41, 40)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
(II) intel(0): [DRI2] Setup complete
(**) intel(0): Framebuffer compression disabled
(**) intel(0): Tiling enabled
(**) intel(0): SwapBuffers wait enabled
(==) intel(0): VideoRam: 262144 KB
(II) intel(0): Attempting memory allocation with tiled buffers.
(II) intel(0): Tiled allocation successful.
(II) UXA(0): Driver registered support for the following operations:
(II)         solid
(II)         copy
(II)         composite (RENDER acceleration)
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): No memory allocations
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(**) Option "dpms"
(**) intel(0): DPMS enabled
(==) intel(0): Intel XvMC decoder disabled
(II) intel(0): Set up textured video
(II) intel(0): direct rendering: DRI2 Enabled
(--) RandR disabled
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
(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
(II) AIGLX: Loaded and initialized /usr/lib/dri/i915_dri.so
(II) GLX: Initialized DRI2 GL provider for screen 0
(II) intel(0): Setting screen physical size to 443 x 249
(II) config/hal: Adding input device Microsft Microsoft Wireless Desktop Receiver 3.1
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 2.2.5
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(**) Microsft Microsoft Wireless Desktop Receiver 3.1: always reports core events
(**) Microsft Microsoft Wireless Desktop Receiver 3.1: Device: "/dev/input/event3"
(II) Microsft Microsoft Wireless Desktop Receiver 3.1: Found keys
(II) Microsft Microsoft Wireless Desktop Receiver 3.1: Configuring as keyboard
(II) XINPUT: Adding extended input device "Microsft Microsoft Wireless Desktop Receiver 3.1" (type: KEYBOARD)
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
(II) config/hal: Adding input device Microsft Microsoft Wireless Desktop Receiver 3.1
(**) Microsft Microsoft Wireless Desktop Receiver 3.1: always reports core events
(**) Microsft Microsoft Wireless Desktop Receiver 3.1: Device: "/dev/input/event4"
(II) Microsft Microsoft Wireless Desktop Receiver 3.1: Found 9 mouse buttons
(II) Microsft Microsoft Wireless Desktop Receiver 3.1: Found x and y relative axes
(II) Microsft Microsoft Wireless Desktop Receiver 3.1: Found scroll wheel(s)
(II) Microsft Microsoft Wireless Desktop Receiver 3.1: Found keys
(II) Microsft Microsoft Wireless Desktop Receiver 3.1: Configuring as mouse
(II) Microsft Microsoft Wireless Desktop Receiver 3.1: Configuring as keyboard
(**) Microsft Microsoft Wireless Desktop Receiver 3.1: YAxisMapping: buttons 4 and 5
(**) Microsft Microsoft Wireless Desktop Receiver 3.1: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Microsft Microsoft Wireless Desktop Receiver 3.1" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "gb"
(**) Microsft Microsoft Wireless Desktop Receiver 3.1: (accel) keeping acceleration scheme 1
(**) Microsft Microsoft Wireless Desktop Receiver 3.1: (accel) filter chain progression: 2.00
(**) Microsft Microsoft Wireless Desktop Receiver 3.1: (accel) filter stage 0: 20.00 ms
(**) Microsft Microsoft Wireless Desktop Receiver 3.1: (accel) set acceleration profile 0
(II) Microsft Microsoft Wireless Desktop Receiver 3.1: initialized for relative axes.
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
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
(II) intel(0): EDID for output VGA1
(II) intel(0): Manufacturer: ACR  Model: 9c  Serial#: 2222999560
(II) intel(0): Year: 2008  Week: 48
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) intel(0): Sync:  Separate
(II) intel(0): Max Image Size [cm]: horiz.: 44  vert.: 25
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: Off; RGB/Color Display
(II) intel(0): Default color space is primary color space
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) intel(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
(II) intel(0): Supported established timings:
(II) intel(0): 720x400@70Hz
(II) intel(0): 640x480@60Hz
(II) intel(0): 640x480@67Hz
(II) intel(0): 800x600@56Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 1024x768@60Hz
(II) intel(0): 1024x768@70Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
(II) intel(0): #0: hsize: 1920  vsize 1080  refresh: 60  vid: 49361
(II) intel(0): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) intel(0): #2: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) intel(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): #4: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 148.5 MHz   Image Size:  443 x 249 mm
(II) intel(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
(II) intel(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
(II) intel(0): Ranges: V min: 55 V max: 75 Hz, H min: 30 H max: 80 kHz, PixClock max 180 MHz
(II) intel(0): Monitor name: X233H
(II) intel(0): Serial No: LFN0B0043900
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff0004729c0008488084
(II) intel(0):     30120103682c19782eee95a3544c9926
(II) intel(0):     0f5054b30c00d1c0714f810081809500
(II) intel(0):     010101010101023a801871382d40582c
(II) intel(0):     4500bbf910000004000000fd00374b1e
(II) intel(0):     5012000a202020202020000000fc0058
(II) intel(0):     323333480a20202020202020000000ff
(II) intel(0):     004c464e30423030343339303020006f
(II) intel(0): EDID vendor "ACR", prod id 156
(II) intel(0): DDCModeFromDetailedTiming: 1920x1080 Warning: We only handle separate sync.
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): EDID for output DVI1
(II) intel(0): EDID for output VGA1
(II) intel(0): Manufacturer: ACR  Model: 9c  Serial#: 2222999560
(II) intel(0): Year: 2008  Week: 48
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) intel(0): Sync:  Separate
(II) intel(0): Max Image Size [cm]: horiz.: 44  vert.: 25
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: Off; RGB/Color Display
(II) intel(0): Default color space is primary color space
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) intel(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
(II) intel(0): Supported established timings:
(II) intel(0): 720x400@70Hz
(II) intel(0): 640x480@60Hz
(II) intel(0): 640x480@67Hz
(II) intel(0): 800x600@56Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 1024x768@60Hz
(II) intel(0): 1024x768@70Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
(II) intel(0): #0: hsize: 1920  vsize 1080  refresh: 60  vid: 49361
(II) intel(0): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) intel(0): #2: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) intel(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): #4: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 148.5 MHz   Image Size:  443 x 249 mm
(II) intel(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
(II) intel(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
(II) intel(0): Ranges: V min: 55 V max: 75 Hz, H min: 30 H max: 80 kHz, PixClock max 180 MHz
(II) intel(0): Monitor name: X233H
(II) intel(0): Serial No: LFN0B0043900
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff0004729c0008488084
(II) intel(0):     30120103682c19782eee95a3544c9926
(II) intel(0):     0f5054b30c00d1c0714f810081809500
(II) intel(0):     010101010101023a801871382d40582c
(II) intel(0):     4500bbf910000004000000fd00374b1e
(II) intel(0):     5012000a202020202020000000fc0058
(II) intel(0):     323333480a20202020202020000000ff
(II) intel(0):     004c464e30423030343339303020006f
(II) intel(0): EDID vendor "ACR", prod id 156
(II) intel(0): DDCModeFromDetailedTiming: 1920x1080 Warning: We only handle separate sync.
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): EDID for output DVI1
(II) intel(0): EDID for output VGA1
(II) intel(0): Manufacturer: ACR  Model: 9c  Serial#: 2222999560
(II) intel(0): Year: 2008  Week: 48
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) intel(0): Sync:  Separate
(II) intel(0): Max Image Size [cm]: horiz.: 44  vert.: 25
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: Off; RGB/Color Display
(II) intel(0): Default color space is primary color space
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) intel(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
(II) intel(0): Supported established timings:
(II) intel(0): 720x400@70Hz
(II) intel(0): 640x480@60Hz
(II) intel(0): 640x480@67Hz
(II) intel(0): 800x600@56Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 1024x768@60Hz
(II) intel(0): 1024x768@70Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
(II) intel(0): #0: hsize: 1920  vsize 1080  refresh: 60  vid: 49361
(II) intel(0): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) intel(0): #2: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) intel(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): #4: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 148.5 MHz   Image Size:  443 x 249 mm
(II) intel(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
(II) intel(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
(II) intel(0): Ranges: V min: 55 V max: 75 Hz, H min: 30 H max: 80 kHz, PixClock max 180 MHz
(II) intel(0): Monitor name: X233H
(II) intel(0): Serial No: LFN0B0043900
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff0004729c0008488084
(II) intel(0):     30120103682c19782eee95a3544c9926
(II) intel(0):     0f5054b30c00d1c0714f810081809500
(II) intel(0):     010101010101023a801871382d40582c
(II) intel(0):     4500bbf910000004000000fd00374b1e
(II) intel(0):     5012000a202020202020000000fc0058
(II) intel(0):     323333480a20202020202020000000ff
(II) intel(0):     004c464e30423030343339303020006f
(II) intel(0): EDID vendor "ACR", prod id 156
(II) intel(0): DDCModeFromDetailedTiming: 1920x1080 Warning: We only handle separate sync.
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): EDID for output DVI1
(II) intel(0): EDID for output VGA1
(II) intel(0): Manufacturer: ACR  Model: 9c  Serial#: 2222999560
(II) intel(0): Year: 2008  Week: 48
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) intel(0): Sync:  Separate
(II) intel(0): Max Image Size [cm]: horiz.: 44  vert.: 25
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: Off; RGB/Color Display
(II) intel(0): Default color space is primary color space
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) intel(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
(II) intel(0): Supported established timings:
(II) intel(0): 720x400@70Hz
(II) intel(0): 640x480@60Hz
(II) intel(0): 640x480@67Hz
(II) intel(0): 800x600@56Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 1024x768@60Hz
(II) intel(0): 1024x768@70Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
(II) intel(0): #0: hsize: 1920  vsize 1080  refresh: 60  vid: 49361
(II) intel(0): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) intel(0): #2: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) intel(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): #4: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 148.5 MHz   Image Size:  443 x 249 mm
(II) intel(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
(II) intel(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
(II) intel(0): Ranges: V min: 55 V max: 75 Hz, H min: 30 H max: 80 kHz, PixClock max 180 MHz
(II) intel(0): Monitor name: X233H
(II) intel(0): Serial No: LFN0B0043900
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff0004729c0008488084
(II) intel(0):     30120103682c19782eee95a3544c9926
(II) intel(0):     0f5054b30c00d1c0714f810081809500
(II) intel(0):     010101010101023a801871382d40582c
(II) intel(0):     4500bbf910000004000000fd00374b1e
(II) intel(0):     5012000a202020202020000000fc0058
(II) intel(0):     323333480a20202020202020000000ff
(II) intel(0):     004c464e30423030343339303020006f
(II) intel(0): EDID vendor "ACR", prod id 156
(II) intel(0): DDCModeFromDetailedTiming: 1920x1080 Warning: We only handle separate sync.
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): EDID for output DVI1
(II) intel(0): EDID for output VGA1
(II) intel(0): Manufacturer: ACR  Model: 9c  Serial#: 2222999560
(II) intel(0): Year: 2008  Week: 48
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) intel(0): Sync:  Separate
(II) intel(0): Max Image Size [cm]: horiz.: 44  vert.: 25
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: Off; RGB/Color Display
(II) intel(0): Default color space is primary color space
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) intel(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
(II) intel(0): Supported established timings:
(II) intel(0): 720x400@70Hz
(II) intel(0): 640x480@60Hz
(II) intel(0): 640x480@67Hz
(II) intel(0): 800x600@56Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 1024x768@60Hz
(II) intel(0): 1024x768@70Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
(II) intel(0): #0: hsize: 1920  vsize 1080  refresh: 60  vid: 49361
(II) intel(0): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) intel(0): #2: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) intel(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): #4: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 148.5 MHz   Image Size:  443 x 249 mm
(II) intel(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
(II) intel(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
(II) intel(0): Ranges: V min: 55 V max: 75 Hz, H min: 30 H max: 80 kHz, PixClock max 180 MHz
(II) intel(0): Monitor name: X233H
(II) intel(0): Serial No: LFN0B0043900
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff0004729c0008488084
(II) intel(0):     30120103682c19782eee95a3544c9926
(II) intel(0):     0f5054b30c00d1c0714f810081809500
(II) intel(0):     010101010101023a801871382d40582c
(II) intel(0):     4500bbf910000004000000fd00374b1e
(II) intel(0):     5012000a202020202020000000fc0058
(II) intel(0):     323333480a20202020202020000000ff
(II) intel(0):     004c464e30423030343339303020006f
(II) intel(0): EDID vendor "ACR", prod id 156
(II) intel(0): DDCModeFromDetailedTiming: 1920x1080 Warning: We only handle separate sync.
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): EDID for output DVI1
(II) intel(0): EDID for output VGA1
(II) intel(0): Manufacturer: ACR  Model: 9c  Serial#: 2222999560
(II) intel(0): Year: 2008  Week: 48
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) intel(0): Sync:  Separate
(II) intel(0): Max Image Size [cm]: horiz.: 44  vert.: 25
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: Off; RGB/Color Display
(II) intel(0): Default color space is primary color space
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) intel(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
(II) intel(0): Supported established timings:
(II) intel(0): 720x400@70Hz
(II) intel(0): 640x480@60Hz
(II) intel(0): 640x480@67Hz
(II) intel(0): 800x600@56Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 1024x768@60Hz
(II) intel(0): 1024x768@70Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
(II) intel(0): #0: hsize: 1920  vsize 1080  refresh: 60  vid: 49361
(II) intel(0): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) intel(0): #2: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) intel(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): #4: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 148.5 MHz   Image Size:  443 x 249 mm
(II) intel(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
(II) intel(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
(II) intel(0): Ranges: V min: 55 V max: 75 Hz, H min: 30 H max: 80 kHz, PixClock max 180 MHz
(II) intel(0): Monitor name: X233H
(II) intel(0): Serial No: LFN0B0043900
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff0004729c0008488084
(II) intel(0):     30120103682c19782eee95a3544c9926
(II) intel(0):     0f5054b30c00d1c0714f810081809500
(II) intel(0):     010101010101023a801871382d40582c
(II) intel(0):     4500bbf910000004000000fd00374b1e
(II) intel(0):     5012000a202020202020000000fc0058
(II) intel(0):     323333480a20202020202020000000ff
(II) intel(0):     004c464e30423030343339303020006f
(II) intel(0): EDID vendor "ACR", prod id 156
(II) intel(0): DDCModeFromDetailedTiming: 1920x1080 Warning: We only handle separate sync.
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): EDID for output DVI1
(II) intel(0): Allocate new frame buffer 1024x768 stride 1024
(II) intel(0): EDID for output VGA1
(II) intel(0): Manufacturer: ACR  Model: 9c  Serial#: 2222999560
(II) intel(0): Year: 2008  Week: 48
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) intel(0): Sync:  Separate
(II) intel(0): Max Image Size [cm]: horiz.: 44  vert.: 25
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: Off; RGB/Color Display
(II) intel(0): Default color space is primary color space
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) intel(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
(II) intel(0): Supported established timings:
(II) intel(0): 720x400@70Hz
(II) intel(0): 640x480@60Hz
(II) intel(0): 640x480@67Hz
(II) intel(0): 800x600@56Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 1024x768@60Hz
(II) intel(0): 1024x768@70Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
(II) intel(0): #0: hsize: 1920  vsize 1080  refresh: 60  vid: 49361
(II) intel(0): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) intel(0): #2: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) intel(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): #4: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 148.5 MHz   Image Size:  443 x 249 mm
(II) intel(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
(II) intel(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
(II) intel(0): Ranges: V min: 55 V max: 75 Hz, H min: 30 H max: 80 kHz, PixClock max 180 MHz
(II) intel(0): Monitor name: X233H
(II) intel(0): Serial No: LFN0B0043900
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff0004729c0008488084
(II) intel(0):     30120103682c19782eee95a3544c9926
(II) intel(0):     0f5054b30c00d1c0714f810081809500
(II) intel(0):     010101010101023a801871382d40582c
(II) intel(0):     4500bbf910000004000000fd00374b1e
(II) intel(0):     5012000a202020202020000000fc0058
(II) intel(0):     323333480a20202020202020000000ff
(II) intel(0):     004c464e30423030343339303020006f
(II) intel(0): EDID vendor "ACR", prod id 156
(II) intel(0): DDCModeFromDetailedTiming: 1920x1080 Warning: We only handle separate sync.
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): EDID for output DVI1
(II) intel(0): EDID for output VGA1
(II) intel(0): Manufacturer: ACR  Model: 9c  Serial#: 2222999560
(II) intel(0): Year: 2008  Week: 48
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) intel(0): Sync:  Separate
(II) intel(0): Max Image Size [cm]: horiz.: 44  vert.: 25
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: Off; RGB/Color Display
(II) intel(0): Default color space is primary color space
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) intel(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
(II) intel(0): Supported established timings:
(II) intel(0): 720x400@70Hz
(II) intel(0): 640x480@60Hz
(II) intel(0): 640x480@67Hz
(II) intel(0): 800x600@56Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 1024x768@60Hz
(II) intel(0): 1024x768@70Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
(II) intel(0): #0: hsize: 1920  vsize 1080  refresh: 60  vid: 49361
(II) intel(0): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) intel(0): #2: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) intel(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): #4: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 148.5 MHz   Image Size:  443 x 249 mm
(II) intel(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
(II) intel(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
(II) intel(0): Ranges: V min: 55 V max: 75 Hz, H min: 30 H max: 80 kHz, PixClock max 180 MHz
(II) intel(0): Monitor name: X233H
(II) intel(0): Serial No: LFN0B0043900
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff0004729c0008488084
(II) intel(0):     30120103682c19782eee95a3544c9926
(II) intel(0):     0f5054b30c00d1c0714f810081809500
(II) intel(0):     010101010101023a801871382d40582c
(II) intel(0):     4500bbf910000004000000fd00374b1e
(II) intel(0):     5012000a202020202020000000fc0058
(II) intel(0):     323333480a20202020202020000000ff
(II) intel(0):     004c464e30423030343339303020006f
(II) intel(0): EDID vendor "ACR", prod id 156
(II) intel(0): DDCModeFromDetailedTiming: 1920x1080 Warning: We only handle separate sync.
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): EDID for output DVI1
(II) intel(0): EDID for output VGA1
(II) intel(0): Manufacturer: ACR  Model: 9c  Serial#: 2222999560
(II) intel(0): Year: 2008  Week: 48
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) intel(0): Sync:  Separate
(II) intel(0): Max Image Size [cm]: horiz.: 44  vert.: 25
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: Off; RGB/Color Display
(II) intel(0): Default color space is primary color space
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) intel(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
(II) intel(0): Supported established timings:
(II) intel(0): 720x400@70Hz
(II) intel(0): 640x480@60Hz
(II) intel(0): 640x480@67Hz
(II) intel(0): 800x600@56Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 1024x768@60Hz
(II) intel(0): 1024x768@70Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
(II) intel(0): #0: hsize: 1920  vsize 1080  refresh: 60  vid: 49361
(II) intel(0): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) intel(0): #2: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) intel(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): #4: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 148.5 MHz   Image Size:  443 x 249 mm
(II) intel(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
(II) intel(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
(II) intel(0): Ranges: V min: 55 V max: 75 Hz, H min: 30 H max: 80 kHz, PixClock max 180 MHz
(II) intel(0): Monitor name: X233H
(II) intel(0): Serial No: LFN0B0043900
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff0004729c0008488084
(II) intel(0):     30120103682c19782eee95a3544c9926
(II) intel(0):     0f5054b30c00d1c0714f810081809500
(II) intel(0):     010101010101023a801871382d40582c
(II) intel(0):     4500bbf910000004000000fd00374b1e
(II) intel(0):     5012000a202020202020000000fc0058
(II) intel(0):     323333480a20202020202020000000ff
(II) intel(0):     004c464e30423030343339303020006f
(II) intel(0): EDID vendor "ACR", prod id 156
(II) intel(0): DDCModeFromDetailedTiming: 1920x1080 Warning: We only handle separate sync.
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): EDID for output DVI1
(II) intel(0): EDID for output VGA1
(II) intel(0): Manufacturer: ACR  Model: 9c  Serial#: 2222999560
(II) intel(0): Year: 2008  Week: 48
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) intel(0): Sync:  Separate
(II) intel(0): Max Image Size [cm]: horiz.: 44  vert.: 25
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: Off; RGB/Color Display
(II) intel(0): Default color space is primary color space
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) intel(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
(II) intel(0): Supported established timings:
(II) intel(0): 720x400@70Hz
(II) intel(0): 640x480@60Hz
(II) intel(0): 640x480@67Hz
(II) intel(0): 800x600@56Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 1024x768@60Hz
(II) intel(0): 1024x768@70Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
(II) intel(0): #0: hsize: 1920  vsize 1080  refresh: 60  vid: 49361
(II) intel(0): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) intel(0): #2: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) intel(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): #4: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 148.5 MHz   Image Size:  443 x 249 mm
(II) intel(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
(II) intel(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
(II) intel(0): Ranges: V min: 55 V max: 75 Hz, H min: 30 H max: 80 kHz, PixClock max 180 MHz
(II) intel(0): Monitor name: X233H
(II) intel(0): Serial No: LFN0B0043900
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff0004729c0008488084
(II) intel(0):     30120103682c19782eee95a3544c9926
(II) intel(0):     0f5054b30c00d1c0714f810081809500
(II) intel(0):     010101010101023a801871382d40582c
(II) intel(0):     4500bbf910000004000000fd00374b1e
(II) intel(0):     5012000a202020202020000000fc0058
(II) intel(0):     323333480a20202020202020000000ff
(II) intel(0):     004c464e30423030343339303020006f
(II) intel(0): EDID vendor "ACR", prod id 156
(II) intel(0): DDCModeFromDetailedTiming: 1920x1080 Warning: We only handle separate sync.
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): EDID for output DVI1
(II) intel(0): EDID for output VGA1
(II) intel(0): Manufacturer: ACR  Model: 9c  Serial#: 2222999560
(II) intel(0): Year: 2008  Week: 48
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) intel(0): Sync:  Separate
(II) intel(0): Max Image Size [cm]: horiz.: 44  vert.: 25
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: Off; RGB/Color Display
(II) intel(0): Default color space is primary color space
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) intel(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
(II) intel(0): Supported established timings:
(II) intel(0): 720x400@70Hz
(II) intel(0): 640x480@60Hz
(II) intel(0): 640x480@67Hz
(II) intel(0): 800x600@56Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 1024x768@60Hz
(II) intel(0): 1024x768@70Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
(II) intel(0): #0: hsize: 1920  vsize 1080  refresh: 60  vid: 49361
(II) intel(0): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) intel(0): #2: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) intel(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): #4: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 148.5 MHz   Image Size:  443 x 249 mm
(II) intel(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
(II) intel(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
(II) intel(0): Ranges: V min: 55 V max: 75 Hz, H min: 30 H max: 80 kHz, PixClock max 180 MHz
(II) intel(0): Monitor name: X233H
(II) intel(0): Serial No: LFN0B0043900
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff0004729c0008488084
(II) intel(0):     30120103682c19782eee95a3544c9926
(II) intel(0):     0f5054b30c00d1c0714f810081809500
(II) intel(0):     010101010101023a801871382d40582c
(II) intel(0):     4500bbf910000004000000fd00374b1e
(II) intel(0):     5012000a202020202020000000fc0058
(II) intel(0):     323333480a20202020202020000000ff
(II) intel(0):     004c464e30423030343339303020006f
(II) intel(0): EDID vendor "ACR", prod id 156
(II) intel(0): DDCModeFromDetailedTiming: 1920x1080 Warning: We only handle separate sync.
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): EDID for output DVI1

```The odd thing is that it seems to find the resolution ok:

```

(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync +vsync (67.5 kHz)

```but the final output doesn't list this mode:

```

(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)

```So i'm stuck in the "best available". This is a certain regression from 8.10/9.04 where things worked perfectly

---

### Post by BenRitchie on 2009-10-30
I've just booted with an earlier kernel

```

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux Atom 2.6.28-16-generic #55-Ubuntu SMP Tue Oct 20 19:48:24 UTC 2009 i686

```and the monitor works correctly

```

(II) intel(0): Printing probed modes for output VGA
(II) intel(0): Modeline &quot;1920x1080&quot;x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync +vsync (67.5 kHz)

```(DisplayManager still calls it an Acer 20&quot;, so I think that's unrelated). So it appears to be an issue related to the kernel change between 9.04 and 9.10?


edit: although the resolyution is correct, performance is *extremely* slow, if I change desktop and back again Firefox takes 5 seconds to redraw (no other windows open)

---

### Post by BenRitchie on 2009-11-02
Still struggling with this one, so any suggestions welcome :)

---

### Post by jwang on 2009-11-02
you could try by adding the following parameter : i915.modeset=0 to disable KMS(this works for me!) 

for example, in /boot/grub/menu.lst @line starting with "kernel", if you're using grub, not grub2. See following link for detail:
[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)

---

### Post by BenRitchie on 2009-11-02
Brilliant, that fixes it - thank you!

---

### Post by cecst on 2009-11-02
[Update: an improved fix is described at [http://ubuntuforums.org/showthread.php?t=1318677](http://ubuntuforums.org/showthread.php?t=1318677), that allows use of a wide-screen Viewsonic model VS11756 in 1440x900 mode (16:10 ratio) as well as 1280x960 (4:3 ratio) mode, which the following method does not. However, the method below does not require modification of the /etc/X11/xorg.conf file with the horizontal and vertical frequencies for the specific monitor being used, as the new method does.]

For those with Dell GX620 with Intel Corporation 82945G/GZ Integrated Graphics Controller (for google searches for this problem) where resolution with Ubuntu 9.10 is set to 800x600 maximum after upgrade from 9.04, the following works (do not include the single quote marks when typing what is shown between them below):
  (1) in grub, press 'e' to edit the kernel boot line, then
  (2) select the longest line by scrolling down until it is highlighted, then press
      'e' again, then
  (3) cursor to the end of the line, which should end in 'splash'. 
  (4) Add the word 'nomodeset' at the end of the line.
  (5) Press Enter, then 'b' to reboot.
  (6) If the resolution is what you want (I got 1152x864 (4:3)),
      edit /boot/grub/menu.lst with nano, vi, or etc, and add
        'nomodeset'
      after every occurrence of the word 'splash'
Kudos for this fix to a post in a now-closed discussion group by shadysamir 
(ubuntuforums.org/showthread.php?t=1281651&page=2).

---

