---
title: "Tearing when items on screen move fast (Probably issue with TV!?)"
date: 2015-08-06
forum: Hardware
---

### Post by malaTG on 2015-08-06
Hi,

I have now tested all the things I can think of and I really need some help! 

My story...

I have a 14.04 multiseat setup (Don't worry I have tested without the multiseat setup and still getting the issue :-)). I have two Nvidia cards, connected to a monitor and to a TV. On the TV I am primarily running Kodi and on the monitor a normal desktop setup. The only problem that I have is tearing when watching movies with too much motion on the TV (No tearing on the monitor for the same movie). This is what I have tried and I still have tearing on the TV

1. Switching the graphic cards between the different displays.
2. Disable the desktop part of the multiseat setup

My setup at this point was as following (Seat 0 is the TV)

lightdm.conf
```

[LightDM]
logind-load-seats=true
logind-check-graphical=true

[Seat:seat0]
xserver-config=/etc/X11/xorg_seat0.conf
autologin-user=xbmc

[Seat:seat-1]
xserver-config=/etc/X11/xorg_seat1.conf
autologin-user=mala

```

xorg_seat_0.conf
```

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600 GT"
#    BusID          "PCI:1:0:0"
    BusID          "PCI:8:0:0"
    Option         "ProbeAllGpus" "FALSE"
    Option	   "TripleBuffer" "TRUE"
EndSection

```

xorg_seat_1.conf
```

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400GS"
#    BusID          "PCI:8:0:0"
    BusID          "PCI:1:0:0"
    Option         "ProbeAllGpus" "FALSE"
EndSection

```

This lead me to believe that I had to setup the TV modelines etc. manually and therefore I consulted my TV manual and got the following values

> 
TV model: Samsung LE37R88BD
Mode: VESA
Resolution: 1360x768
Horisontal frequenzy: 47.712
Vertical frequenzy: 60.015
Pixel clock frequency: 85.800
Sync Polarity: +/+

Going to the site [http://www.arachnoid.com/modelines/]("http://www.arachnoid.com/modelines/") where I can set the resolution and the vertical frequency I got the modeline

```
# 1360x768 @ 60.02 Hz (GTF) hsync: 47.71 kHz; pclk: 84.74 MHz
Modeline "1360x768_60.02" 84.74 1360 1424 1568 1776 768 769 772 795 -HSync +Vsync
```

Looking at it and comparing with the data from the manual the pixel clock frequency and sync polarity looks wrong however I don't know too much about this stuff so figured I would try the modeline. see my new "xorg_seat_0.conf" file below but I still got the tearing. Next thing I tried was too "adjust" the pixel clock frequency and sync polarity according to the manual, see below. Still no effect... I have also attached my log files from the Xorg servers below.

If anyone has ANY idea I would appreciate it a lot!

/Marcus

xorg_seat_0.conf
```
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600 GT"
#    BusID          "PCI:1:0:0"
    BusID          "PCI:8:0:0"
    Option         "ProbeAllGpus" "FALSE"
    Option	   "TripleBuffer" "TRUE"
    Option         "IgnoreEDID" "1"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Samsung"
    ModelName      "LE37R88BD"
    HorizSync       31.5 - 48.3
    VertRefresh     60.0 - 70.0
    # 1360x768 @ 60.02 Hz (GTF) hsync: 47.71 kHz; pclk: 84.74 MHz
    Modeline "1360x768_60.02" 85.80 1360 1424 1568 1776 768 769 772 795 +HSync +Vsync
    Option         "DPMS"
EndSection

Section "Screen"
    Identifier      "Screen0"
    Monitor         "Monitor0"
    Device          "Device0"
    DefaultDepth    24
    SubSection "Display"
        Depth           24
        Modes   "1360x768"
    EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Screen0"
EndSection
```

Xorg.0.log (The TV)
```
[    12.326] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[    12.326] X Protocol Version 11, Revision 0
[    12.326] Build Operating System: Linux 3.13.0-46-generic i686 Ubuntu
[    12.326] Current Operating System: Linux mala-desktop 3.13.0-61-generic #100-Ubuntu SMP Wed Jul 29 11:22:15 UTC 2015 i686
[    12.327] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-61-generic root=UUID=6d870a0d-f66a-4edc-89c3-a698fa0c1aa9 ro quiet splash irqpoll libata.ignore_hpa=1
[    12.327] Build Date: 17 March 2015  03:36:32PM
[    12.327] xorg-server 2:1.15.1-0ubuntu2.7+multiseat0 (For technical support please see http://www.ubuntu.com/support) 
[    12.327] Current version of pixman: 0.30.2
[    12.327] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    12.327] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    12.327] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Aug  6 20:28:41 2015
[    12.329] (++) Using config file: "/etc/X11/xorg_seat0.conf"
[    12.329] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    12.333] (==) ServerLayout "Default Layout"
[    12.333] (**) |-->Screen "Screen0" (0)
[    12.333] (**) |   |-->Monitor "Monitor0"
[    12.333] (**) |   |-->Device "Device0"
[    12.333] (==) Automatically adding devices
[    12.333] (==) Automatically enabling devices
[    12.333] (==) Automatically adding GPU devices
[    12.333] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    12.333] 	Entry deleted from font path.
[    12.333] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	built-ins
[    12.333] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    12.333] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    12.333] (II) Loader magic: 0xb77436c0
[    12.333] (II) Module ABI versions:
[    12.333] 	X.Org ANSI C Emulation: 0.4
[    12.333] 	X.Org Video Driver: 15.0
[    12.333] 	X.Org XInput driver : 20.0
[    12.333] 	X.Org Server Extension : 8.0
[    12.334] (II) xfree86: Adding drm device (/dev/dri/card0)
[    12.334] (II) xfree86: Adding drm device (/dev/dri/card1)
[    12.351] (--) PCI:*(0:1:0:0) 10de:0402:1043:8253 rev 161, Mem @ 0xe6000000/16777216, 0xb0000000/268435456, 0xe4000000/33554432, I/O @ 0x00009000/128, BIOS @ 0x????????/131072
[    12.351] (--) PCI: (0:8:0:0) 10de:10c3:0000:0000 rev 162, Mem @ 0xec000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x0000d000/128, BIOS @ 0x????????/524288
[    12.351] Initializing built-in extension Generic Event Extension
[    12.351] Initializing built-in extension SHAPE
[    12.352] Initializing built-in extension MIT-SHM
[    12.352] Initializing built-in extension XInputExtension
[    12.352] Initializing built-in extension XTEST
[    12.352] Initializing built-in extension BIG-REQUESTS
[    12.352] Initializing built-in extension SYNC
[    12.352] Initializing built-in extension XKEYBOARD
[    12.352] Initializing built-in extension XC-MISC
[    12.352] Initializing built-in extension SECURITY
[    12.352] Initializing built-in extension XINERAMA
[    12.352] Initializing built-in extension XFIXES
[    12.352] Initializing built-in extension RENDER
[    12.352] Initializing built-in extension RANDR
[    12.352] Initializing built-in extension COMPOSITE
[    12.352] Initializing built-in extension DAMAGE
[    12.352] Initializing built-in extension MIT-SCREEN-SAVER
[    12.352] Initializing built-in extension DOUBLE-BUFFER
[    12.352] Initializing built-in extension RECORD
[    12.352] Initializing built-in extension DPMS
[    12.352] Initializing built-in extension Present
[    12.352] Initializing built-in extension DRI3
[    12.352] Initializing built-in extension X-Resource
[    12.352] Initializing built-in extension XVideo
[    12.352] Initializing built-in extension XVideo-MotionCompensation
[    12.352] Initializing built-in extension SELinux
[    12.352] Initializing built-in extension XFree86-VidModeExtension
[    12.352] Initializing built-in extension XFree86-DGA
[    12.352] Initializing built-in extension XFree86-DRI
[    12.352] Initializing built-in extension DRI2
[    12.352] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    12.352] (II) "glx" will be loaded by default.
[    12.352] (WW) "xmir" is not to be loaded by default. Skipping.
[    12.352] (II) LoadModule: "glx"
[    12.353] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/libglx.so
[    12.423] (II) Module glx: vendor="NVIDIA Corporation"
[    12.423] 	compiled for 4.0.2, module version = 1.0.0
[    12.423] 	Module class: X.Org Server Extension
[    12.423] (II) NVIDIA GLX Module  304.125  Mon Dec  1 20:21:57 PST 2014
[    12.423] Loading extension GLX
[    12.423] (II) LoadModule: "nvidia"
[    12.423] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    12.424] (II) Module nvidia: vendor="NVIDIA Corporation"
[    12.424] 	compiled for 4.0.2, module version = 1.0.0
[    12.424] 	Module class: X.Org Video Driver
[    12.425] (II) NVIDIA dlloader X Driver  304.125  Mon Dec  1 19:57:42 PST 2014
[    12.425] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    12.425] (++) using VT number 7

[    12.426] (II) Loading sub module "fb"
[    12.426] (II) LoadModule: "fb"
[    12.426] (II) Loading /usr/lib/xorg/modules/libfb.so
[    12.427] (II) Module fb: vendor="X.Org Foundation"
[    12.427] 	compiled for 1.15.1, module version = 1.0.0
[    12.427] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    12.427] (II) Loading sub module "wfb"
[    12.427] (II) LoadModule: "wfb"
[    12.427] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    12.427] (II) Module wfb: vendor="X.Org Foundation"
[    12.427] 	compiled for 1.15.1, module version = 1.0.0
[    12.427] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    12.427] (II) Loading sub module "ramdac"
[    12.427] (II) LoadModule: "ramdac"
[    12.427] (II) Module "ramdac" already built-in
[    12.428] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    12.428] (==) NVIDIA(0): RGB weight 888
[    12.428] (==) NVIDIA(0): Default visual is TrueColor
[    12.428] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    12.428] (**) NVIDIA(0): Option "TripleBuffer" "TRUE"
[    12.428] (**) NVIDIA(0): Option "ProbeAllGpus" "FALSE"
[    12.428] (**) NVIDIA(0): Enabling 2D acceleration
[    14.733] (II) NVIDIA(GPU-0): Display (SAMSUNG (DFP-0)) does not support NVIDIA 3D Vision
[    14.734] (II) NVIDIA(GPU-0):     stereo.
[    14.858] (II) NVIDIA(0): NVIDIA GPU GeForce 8400GS (GT218) at PCI:8:0:0 (GPU-0)
[    14.858] (--) NVIDIA(0): Memory: 524288 kBytes
[    14.858] (--) NVIDIA(0): VideoBIOS: 70.18.76.00.72
[    14.858] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    14.858] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    14.864] (--) NVIDIA(0): Valid display device(s) on GeForce 8400GS at PCI:8:0:0
[    14.864] (--) NVIDIA(0):     CRT-0
[    14.864] (--) NVIDIA(0):     CRT-1
[    14.864] (--) NVIDIA(0):     SAMSUNG (DFP-0) (connected)
[    14.864] (--) NVIDIA(0):     DFP-1
[    14.864] (--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
[    14.865] (--) NVIDIA(0): CRT-1: 400.0 MHz maximum pixel clock
[    14.865] (--) NVIDIA(0): SAMSUNG (DFP-0): 330.0 MHz maximum pixel clock
[    14.865] (--) NVIDIA(0): SAMSUNG (DFP-0): Internal Dual Link TMDS
[    14.865] (--) NVIDIA(0): DFP-1: 165.0 MHz maximum pixel clock
[    14.865] (--) NVIDIA(0): DFP-1: Internal Single Link TMDS
[    14.865] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    14.865] (**) NVIDIA(0):     device SAMSUNG (DFP-0) (Using EDID frequencies has been
[    14.865] (**) NVIDIA(0):     enabled on all display devices.)
[    14.888] (II) NVIDIA(0): Validated MetaModes:
[    14.888] (II) NVIDIA(0):     "DFP-0:1360x768"
[    14.888] (II) NVIDIA(0): Virtual screen size determined to be 1360 x 768
[    14.928] (--) NVIDIA(0): DPI set to (215, 216); computed from "UseEdidDpi" X config
[    14.928] (--) NVIDIA(0):     option
[    14.928] (--) Depth 24 pixmap format is 32 bpp
[    14.929] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    14.957] (II) NVIDIA(0): Setting mode "DFP-0:1360x768"
[    15.122] Loading extension NV-GLX
[    15.219] (==) NVIDIA(0): Disabling shared memory pixmaps
[    15.219] (==) NVIDIA(0): Backing store enabled
[    15.219] (==) NVIDIA(0): Silken mouse enabled
[    15.220] (**) NVIDIA(0): DPMS enabled
[    15.220] Loading extension NV-CONTROL
[    15.221] Loading extension XINERAMA
[    15.221] (WW) NVIDIA(0): Option "IgnoreEDID" is not used
[    15.221] (II) Loading sub module "dri2"
[    15.221] (II) LoadModule: "dri2"
[    15.221] (II) Module "dri2" already built-in
[    15.221] (II) NVIDIA(0): [DRI2] Setup complete
[    15.221] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[    15.221] (--) RandR disabled
[    15.247] (II) SELinux: Disabled on system
[    15.249] (II) Initializing extension GLX
[    15.364] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    15.387] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    15.387] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    15.387] (II) LoadModule: "evdev"
[    15.387] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    15.387] (II) Module evdev: vendor="X.Org Foundation"
[    15.387] 	compiled for 1.15.0, module version = 2.8.2
[    15.387] 	Module class: X.Org XInput Driver
[    15.396] 	ABI class: X.Org XInput driver, version 20.0
[    15.396] (II) Using input driver 'evdev' for 'Power Button'
[    15.396] (**) Power Button: always reports core events
[    15.396] (**) evdev: Power Button: Device: "/dev/input/event1"
[    15.396] (--) evdev: Power Button: Vendor 0 Product 0x1
[    15.396] (--) evdev: Power Button: Found keys
[    15.396] (II) evdev: Power Button: Configuring as keyboard
[    15.396] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    15.396] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    15.396] (**) Option "xkb_rules" "evdev"
[    15.396] (**) Option "xkb_model" "pc105"
[    15.396] (**) Option "xkb_layout" "se"
[    15.400] (II) XKB: reuse xkmfile /var/lib/xkb/server-523B07B557B20588EB459118C97940B7C9FF61EB.xkm
[    15.401] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    15.401] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    15.401] (II) Using input driver 'evdev' for 'Power Button'
[    15.401] (**) Power Button: always reports core events
[    15.401] (**) evdev: Power Button: Device: "/dev/input/event0"
[    15.401] (--) evdev: Power Button: Vendor 0 Product 0x1
[    15.401] (--) evdev: Power Button: Found keys
[    15.401] (II) evdev: Power Button: Configuring as keyboard
[    15.401] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    15.401] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    15.401] (**) Option "xkb_rules" "evdev"
[    15.401] (**) Option "xkb_model" "pc105"
[    15.402] (**) Option "xkb_layout" "se"
[    15.403] (II) config/udev: Adding input device Logitech Logitech BT Mini-Receiver (/dev/input/event3)
[    15.403] (**) Logitech Logitech BT Mini-Receiver: Applying InputClass "evdev keyboard catchall"
[    15.403] (II) Using input driver 'evdev' for 'Logitech Logitech BT Mini-Receiver'
[    15.403] (**) Logitech Logitech BT Mini-Receiver: always reports core events
[    15.403] (**) evdev: Logitech Logitech BT Mini-Receiver: Device: "/dev/input/event3"
[    15.403] (--) evdev: Logitech Logitech BT Mini-Receiver: Vendor 0x46d Product 0xc71e
[    15.403] (--) evdev: Logitech Logitech BT Mini-Receiver: Found keys
[    15.403] (II) evdev: Logitech Logitech BT Mini-Receiver: Configuring as keyboard
[    15.403] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.2/3-1.2:1.0/input/input6/event3"
[    15.403] (II) XINPUT: Adding extended input device "Logitech Logitech BT Mini-Receiver" (type: KEYBOARD, id 8)
[    15.403] (**) Option "xkb_rules" "evdev"
[    15.403] (**) Option "xkb_model" "pc105"
[    15.403] (**) Option "xkb_layout" "se"
[    15.428] (II) config/udev: Adding input device Logitech Logitech BT Mini-Receiver (/dev/input/event4)
[    15.428] (**) Logitech Logitech BT Mini-Receiver: Applying InputClass "evdev pointer catchall"
[    15.428] (**) Logitech Logitech BT Mini-Receiver: Applying InputClass "evdev keyboard catchall"
[    15.428] (II) Using input driver 'evdev' for 'Logitech Logitech BT Mini-Receiver'
[    15.428] (**) Logitech Logitech BT Mini-Receiver: always reports core events
[    15.428] (**) evdev: Logitech Logitech BT Mini-Receiver: Device: "/dev/input/event4"
[    15.428] (--) evdev: Logitech Logitech BT Mini-Receiver: Vendor 0x46d Product 0xc71f
[    15.428] (--) evdev: Logitech Logitech BT Mini-Receiver: Found 16 mouse buttons
[    15.428] (--) evdev: Logitech Logitech BT Mini-Receiver: Found scroll wheel(s)
[    15.428] (--) evdev: Logitech Logitech BT Mini-Receiver: Found relative axes
[    15.428] (--) evdev: Logitech Logitech BT Mini-Receiver: Found x and y relative axes
[    15.428] (--) evdev: Logitech Logitech BT Mini-Receiver: Found absolute axes
[    15.428] (II) evdev: Logitech Logitech BT Mini-Receiver: Forcing absolute x/y axes to exist.
[    15.428] (--) evdev: Logitech Logitech BT Mini-Receiver: Found keys
[    15.428] (II) evdev: Logitech Logitech BT Mini-Receiver: Configuring as mouse
[    15.428] (II) evdev: Logitech Logitech BT Mini-Receiver: Configuring as keyboard
[    15.428] (II) evdev: Logitech Logitech BT Mini-Receiver: Adding scrollwheel support
[    15.428] (**) evdev: Logitech Logitech BT Mini-Receiver: YAxisMapping: buttons 4 and 5
[    15.428] (**) evdev: Logitech Logitech BT Mini-Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    15.428] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.3/3-1.3:1.0/input/input7/event4"
[    15.429] (II) XINPUT: Adding extended input device "Logitech Logitech BT Mini-Receiver" (type: KEYBOARD, id 9)
[    15.429] (**) Option "xkb_rules" "evdev"
[    15.429] (**) Option "xkb_model" "pc105"
[    15.429] (**) Option "xkb_layout" "se"
[    15.429] (II) evdev: Logitech Logitech BT Mini-Receiver: initialized for relative axes.
[    15.429] (WW) evdev: Logitech Logitech BT Mini-Receiver: ignoring absolute axes.
[    15.429] (**) Logitech Logitech BT Mini-Receiver: (accel) keeping acceleration scheme 1
[    15.429] (**) Logitech Logitech BT Mini-Receiver: (accel) acceleration profile 0
[    15.429] (**) Logitech Logitech BT Mini-Receiver: (accel) acceleration factor: 2.000
[    15.429] (**) Logitech Logitech BT Mini-Receiver: (accel) acceleration threshold: 4
[    15.430] (II) config/udev: Adding input device Logitech Logitech BT Mini-Receiver (/dev/input/mouse0)
[    15.430] (II) No input driver specified, ignoring this device.
[    15.430] (II) This device may have been added with another device file.
[    15.431] (II) config/udev: Adding input device HDA Intel Rear Mic (/dev/input/event14)
[    15.431] (II) No input driver specified, ignoring this device.
[    15.431] (II) This device may have been added with another device file.
[    15.431] (II) config/udev: Adding input device HDA Intel Front Mic (/dev/input/event13)
[    15.431] (II) No input driver specified, ignoring this device.
[    15.431] (II) This device may have been added with another device file.
[    15.444] (II) config/udev: Adding input device HDA Intel Line (/dev/input/event12)
[    15.444] (II) No input driver specified, ignoring this device.
[    15.444] (II) This device may have been added with another device file.
[    15.444] (II) config/udev: Adding input device HDA Intel Line Out Front (/dev/input/event11)
[    15.445] (II) No input driver specified, ignoring this device.
[    15.445] (II) This device may have been added with another device file.
[    15.445] (II) config/udev: Adding input device HDA Intel Line Out Surround (/dev/input/event10)
[    15.445] (II) No input driver specified, ignoring this device.
[    15.445] (II) This device may have been added with another device file.
[    15.445] (II) config/udev: Adding input device HDA Intel Line Out CLFE (/dev/input/event9)
[    15.446] (II) No input driver specified, ignoring this device.
[    15.446] (II) This device may have been added with another device file.
[    15.446] (II) config/udev: Adding input device HDA Intel Line Out Side (/dev/input/event8)
[    15.446] (II) No input driver specified, ignoring this device.
[    15.446] (II) This device may have been added with another device file.
[    15.446] (II) config/udev: Adding input device HDA Intel Front Headphone (/dev/input/event7)
[    15.447] (II) No input driver specified, ignoring this device.
[    15.447] (II) This device may have been added with another device file.
[    15.453] (II) config/udev: Adding input device Budget-CI dvb ir receiver saa7146 (0) (/dev/input/event15)
[    15.453] (**) Budget-CI dvb ir receiver saa7146 (0): Applying InputClass "evdev keyboard catchall"
[    15.453] (II) Using input driver 'evdev' for 'Budget-CI dvb ir receiver saa7146 (0)'
[    15.453] (**) Budget-CI dvb ir receiver saa7146 (0): always reports core events
[    15.453] (**) evdev: Budget-CI dvb ir receiver saa7146 (0): Device: "/dev/input/event15"
[    15.453] (--) evdev: Budget-CI dvb ir receiver saa7146 (0): Vendor 0x13c2 Product 0x101a
[    15.453] (--) evdev: Budget-CI dvb ir receiver saa7146 (0): Found keys
[    15.453] (II) evdev: Budget-CI dvb ir receiver saa7146 (0): Configuring as keyboard
[    15.453] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1e.0/0000:07:01.0/rc/rc0/input18/event15"
[    15.454] (II) XINPUT: Adding extended input device "Budget-CI dvb ir receiver saa7146 (0)" (type: KEYBOARD, id 10)
[    15.454] (**) Option "xkb_rules" "evdev"
[    15.454] (**) Option "xkb_model" "pc105"
[    15.454] (**) Option "xkb_layout" "se"
[    15.455] (II) config/udev: Adding drm device (/dev/dri/card1) card1 /sys/devices/pci0000:00/0000:00:1e.0/0000:07:02.0/0000:08:00.0/drm/card1
[    15.456] (II) config/udev: Ignoring already known drm device (/dev/dri/card1)
[    15.457] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event19)
[    15.457] (II) No input driver specified, ignoring this device.
[    15.457] (II) This device may have been added with another device file.
[    15.458] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event18)
[    15.458] (II) No input driver specified, ignoring this device.
[    15.458] (II) This device may have been added with another device file.
[    15.460] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event17)
[    15.460] (II) No input driver specified, ignoring this device.
[    15.460] (II) This device may have been added with another device file.
[    15.462] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=9 (/dev/input/event16)
[    15.462] (II) No input driver specified, ignoring this device.
[    15.462] (II) This device may have been added with another device file.
[    20.328] (II) NVIDIA(GPU-0): Display (SAMSUNG (DFP-0)) does not support NVIDIA 3D Vision
[    20.328] (II) NVIDIA(GPU-0):     stereo.
[    20.328] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    20.328] (**) NVIDIA(0):     device SAMSUNG (DFP-0) (Using EDID frequencies has been
[    20.328] (**) NVIDIA(0):     enabled on all display devices.)
[    21.266] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    25.161] (II) XKB: reuse xkmfile /var/lib/xkb/server-DC21AD274DC9E7DBF4EDEEA656AE6D12573A7A81.xkm
[    25.300] (II) NVIDIA(GPU-0): Display (SAMSUNG (DFP-0)) does not support NVIDIA 3D Vision
[    25.300] (II) NVIDIA(GPU-0):     stereo.
[    25.300] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    25.300] (**) NVIDIA(0):     device SAMSUNG (DFP-0) (Using EDID frequencies has been
[    25.300] (**) NVIDIA(0):     enabled on all display devices.)
[    25.335] (II) XKB: reuse xkmfile /var/lib/xkb/server-56365E9F5DDB4DE8CA75E8EFEE28D399BFF865B0.xkm
[    25.394] (II) XKB: reuse xkmfile /var/lib/xkb/server-56365E9F5DDB4DE8CA75E8EFEE28D399BFF865B0.xkm
[    25.395] (II) XKB: reuse xkmfile /var/lib/xkb/server-DC21AD274DC9E7DBF4EDEEA656AE6D12573A7A81.xkm
[    25.405] (II) XKB: reuse xkmfile /var/lib/xkb/server-56365E9F5DDB4DE8CA75E8EFEE28D399BFF865B0.xkm
[    25.423] (II) XKB: reuse xkmfile /var/lib/xkb/server-56365E9F5DDB4DE8CA75E8EFEE28D399BFF865B0.xkm
[    25.434] (II) XKB: reuse xkmfile /var/lib/xkb/server-56365E9F5DDB4DE8CA75E8EFEE28D399BFF865B0.xkm
[    25.448] (II) XKB: reuse xkmfile /var/lib/xkb/server-56365E9F5DDB4DE8CA75E8EFEE28D399BFF865B0.xkm
[    25.455] (II) XKB: reuse xkmfile /var/lib/xkb/server-56365E9F5DDB4DE8CA75E8EFEE28D399BFF865B0.xkm
[    25.467] (II) XKB: reuse xkmfile /var/lib/xkb/server-56365E9F5DDB4DE8CA75E8EFEE28D399BFF865B0.xkm
[    25.488] (II) XKB: reuse xkmfile /var/lib/xkb/server-56365E9F5DDB4DE8CA75E8EFEE28D399BFF865B0.xkm
[    25.501] (II) XKB: reuse xkmfile /var/lib/xkb/server-56365E9F5DDB4DE8CA75E8EFEE28D399BFF865B0.xkm
[    25.511] (II) XKB: reuse xkmfile /var/lib/xkb/server-56365E9F5DDB4DE8CA75E8EFEE28D399BFF865B0.xkm
[    25.525] (II) XKB: reuse xkmfile /var/lib/xkb/server-56365E9F5DDB4DE8CA75E8EFEE28D399BFF865B0.xkm
[    25.535] (II) XKB: reuse xkmfile /var/lib/xkb/server-56365E9F5DDB4DE8CA75E8EFEE28D399BFF865B0.xkm
[    25.547] (II) XKB: reuse xkmfile /var/lib/xkb/server-56365E9F5DDB4DE8CA75E8EFEE28D399BFF865B0.xkm
[    25.563] (II) XKB: reuse xkmfile /var/lib/xkb/server-56365E9F5DDB4DE8CA75E8EFEE28D399BFF865B0.xkm
[    27.972] (II) NVIDIA(GPU-0): Display (SAMSUNG (DFP-0)) does not support NVIDIA 3D Vision
[    27.972] (II) NVIDIA(GPU-0):     stereo.
[    27.972] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    27.972] (**) NVIDIA(0):     device SAMSUNG (DFP-0) (Using EDID frequencies has been
[    27.972] (**) NVIDIA(0):     enabled on all display devices.)
[    30.616] (II) NVIDIA(GPU-0): Display (SAMSUNG (DFP-0)) does not support NVIDIA 3D Vision
[    30.616] (II) NVIDIA(GPU-0):     stereo.
[    30.616] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    30.616] (**) NVIDIA(0):     device SAMSUNG (DFP-0) (Using EDID frequencies has been
[    30.616] (**) NVIDIA(0):     enabled on all display devices.)
[    42.184] (II) NVIDIA(GPU-0): Display (SAMSUNG (DFP-0)) does not support NVIDIA 3D Vision
[    42.184] (II) NVIDIA(GPU-0):     stereo.
[    42.184] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    42.184] (**) NVIDIA(0):     device SAMSUNG (DFP-0) (Using EDID frequencies has been
[    42.184] (**) NVIDIA(0):     enabled on all display devices.)
[   132.398] (II) XKB: reuse xkmfile /var/lib/xkb/server-56365E9F5DDB4DE8CA75E8EFEE28D399BFF865B0.xkm
[   136.361] (II) NVIDIA(GPU-0): Display (SAMSUNG (DFP-0)) does not support NVIDIA 3D Vision
[   136.361] (II) NVIDIA(GPU-0):     stereo.
[   136.361] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   136.361] (**) NVIDIA(0):     device SAMSUNG (DFP-0) (Using EDID frequencies has been
[   136.361] (**) NVIDIA(0):     enabled on all display devices.)
[   464.266] (II) NVIDIA(GPU-0): Display (SAMSUNG (DFP-0)) does not support NVIDIA 3D Vision
[   464.266] (II) NVIDIA(GPU-0):     stereo.
[   464.266] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   464.267] (**) NVIDIA(0):     device SAMSUNG (DFP-0) (Using EDID frequencies has been
[   464.267] (**) NVIDIA(0):     enabled on all display devices.)
```

Xorg.1.log (The desktop with no issues)
```
[    12.323] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[    12.323] X Protocol Version 11, Revision 0
[    12.323] Build Operating System: Linux 3.13.0-46-generic i686 Ubuntu
[    12.323] Current Operating System: Linux mala-desktop 3.13.0-61-generic #100-Ubuntu SMP Wed Jul 29 11:22:15 UTC 2015 i686
[    12.323] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-61-generic root=UUID=6d870a0d-f66a-4edc-89c3-a698fa0c1aa9 ro quiet splash irqpoll libata.ignore_hpa=1
[    12.323] Build Date: 17 March 2015  03:36:32PM
[    12.323] xorg-server 2:1.15.1-0ubuntu2.7+multiseat0 (For technical support please see http://www.ubuntu.com/support) 
[    12.323] Current version of pixman: 0.30.2
[    12.325] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    12.325] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    12.325] (==) Log file: "/var/log/Xorg.1.log", Time: Thu Aug  6 20:28:41 2015
[    12.328] (++) Using config file: "/etc/X11/xorg_seat1.conf"
[    12.328] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    12.330] (==) No Layout section.  Using the first Screen section.
[    12.330] (==) No screen section available. Using defaults.
[    12.330] (**) |-->Screen "Default Screen Section" (0)
[    12.330] (**) |   |-->Monitor "<default monitor>"
[    12.330] (==) No device specified for screen "Default Screen Section".
	Using the first device section listed.
[    12.330] (**) |   |-->Device "Device1"
[    12.330] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    12.331] (==) Automatically adding devices
[    12.331] (==) Automatically enabling devices
[    12.331] (==) Automatically adding GPU devices
[    12.331] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    12.331] 	Entry deleted from font path.
[    12.331] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	built-ins
[    12.331] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    12.331] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    12.331] (II) Loader magic: 0xb77976c0
[    12.331] (II) Module ABI versions:
[    12.331] 	X.Org ANSI C Emulation: 0.4
[    12.331] 	X.Org Video Driver: 15.0
[    12.331] 	X.Org XInput driver : 20.0
[    12.331] 	X.Org Server Extension : 8.0
[    12.332] (II) xfree86: Adding drm device (/dev/dri/card0)
[    12.334] Initializing built-in extension Generic Event Extension
[    12.335] Initializing built-in extension SHAPE
[    12.335] Initializing built-in extension MIT-SHM
[    12.335] Initializing built-in extension XInputExtension
[    12.335] Initializing built-in extension XTEST
[    12.335] Initializing built-in extension BIG-REQUESTS
[    12.335] Initializing built-in extension SYNC
[    12.335] Initializing built-in extension XKEYBOARD
[    12.335] Initializing built-in extension XC-MISC
[    12.335] Initializing built-in extension SECURITY
[    12.336] Initializing built-in extension XINERAMA
[    12.336] Initializing built-in extension XFIXES
[    12.336] Initializing built-in extension RENDER
[    12.336] Initializing built-in extension RANDR
[    12.336] Initializing built-in extension COMPOSITE
[    12.336] Initializing built-in extension DAMAGE
[    12.336] Initializing built-in extension MIT-SCREEN-SAVER
[    12.336] Initializing built-in extension DOUBLE-BUFFER
[    12.336] Initializing built-in extension RECORD
[    12.336] Initializing built-in extension DPMS
[    12.336] Initializing built-in extension Present
[    12.336] Initializing built-in extension DRI3
[    12.336] Initializing built-in extension X-Resource
[    12.336] Initializing built-in extension XVideo
[    12.336] Initializing built-in extension XVideo-MotionCompensation
[    12.336] Initializing built-in extension SELinux
[    12.336] Initializing built-in extension XFree86-VidModeExtension
[    12.337] Initializing built-in extension XFree86-DGA
[    12.337] Initializing built-in extension XFree86-DRI
[    12.337] Initializing built-in extension DRI2
[    12.337] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    12.337] (II) "glx" will be loaded by default.
[    12.337] (WW) "xmir" is not to be loaded by default. Skipping.
[    12.337] (II) LoadModule: "glx"
[    12.337] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/libglx.so
[    12.424] (II) Module glx: vendor="NVIDIA Corporation"
[    12.425] 	compiled for 4.0.2, module version = 1.0.0
[    12.426] 	Module class: X.Org Server Extension
[    12.426] (II) NVIDIA GLX Module  304.125  Mon Dec  1 20:21:57 PST 2014
[    12.426] Loading extension GLX
[    12.426] (II) LoadModule: "nvidia"
[    12.426] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    12.426] (II) Module nvidia: vendor="NVIDIA Corporation"
[    12.426] 	compiled for 4.0.2, module version = 1.0.0
[    12.427] 	Module class: X.Org Video Driver
[    12.427] (II) NVIDIA dlloader X Driver  304.125  Mon Dec  1 19:57:42 PST 2014
[    12.427] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    12.427] (II) Loading sub module "fb"
[    12.427] (II) LoadModule: "fb"
[    12.427] (II) Loading /usr/lib/xorg/modules/libfb.so
[    12.429] (II) Module fb: vendor="X.Org Foundation"
[    12.429] 	compiled for 1.15.1, module version = 1.0.0
[    12.429] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    12.429] (II) Loading sub module "wfb"
[    12.429] (II) LoadModule: "wfb"
[    12.430] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    12.432] (II) Module wfb: vendor="X.Org Foundation"
[    12.432] 	compiled for 1.15.1, module version = 1.0.0
[    12.432] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    12.432] (II) Loading sub module "ramdac"
[    12.432] (II) LoadModule: "ramdac"
[    12.432] (II) Module "ramdac" already built-in
[    12.433] (II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    12.433] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    12.433] (==) NVIDIA(0): RGB weight 888
[    12.433] (==) NVIDIA(0): Default visual is TrueColor
[    12.433] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    12.433] (**) NVIDIA(0): Option "ProbeAllGpus" "FALSE"
[    12.433] (**) NVIDIA(0): Enabling 2D acceleration
[    14.850] (II) NVIDIA(GPU-0): Display (DELL U2312HM (DFP-0)) does not support NVIDIA 3D
[    14.850] (II) NVIDIA(GPU-0):     Vision stereo.
[    14.865] (II) NVIDIA(0): NVIDIA GPU GeForce 8600 GT (G84) at PCI:1:0:0 (GPU-0)
[    14.865] (--) NVIDIA(0): Memory: 524288 kBytes
[    14.865] (--) NVIDIA(0): VideoBIOS: 60.84.41.00.00
[    14.865] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    14.865] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    14.876] (--) NVIDIA(0): Valid display device(s) on GeForce 8600 GT at PCI:1:0:0
[    14.880] (--) NVIDIA(0):     CRT-0
[    14.880] (--) NVIDIA(0):     CRT-1
[    14.880] (--) NVIDIA(0):     TV-0
[    14.880] (--) NVIDIA(0):     DELL U2312HM (DFP-0) (connected)
[    14.880] (--) NVIDIA(0):     DFP-1
[    14.880] (--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
[    14.880] (--) NVIDIA(0): CRT-1: 400.0 MHz maximum pixel clock
[    14.880] (--) NVIDIA(0): TV-0: 400.0 MHz maximum pixel clock
[    14.880] (--) NVIDIA(0): TV encoder: Unknown
[    14.880] (--) NVIDIA(0): DELL U2312HM (DFP-0): 330.0 MHz maximum pixel clock
[    14.880] (--) NVIDIA(0): DELL U2312HM (DFP-0): Internal Dual Link TMDS
[    14.880] (--) NVIDIA(0): DFP-1: 330.0 MHz maximum pixel clock
[    14.880] (--) NVIDIA(0): DFP-1: Internal Single Link TMDS
[    14.880] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    14.880] (**) NVIDIA(0):     device DELL U2312HM (DFP-0) (Using EDID frequencies has
[    14.880] (**) NVIDIA(0):     been enabled on all display devices.)
[    14.886] (==) NVIDIA(0): 
[    14.886] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    14.886] (==) NVIDIA(0):     will be used as the requested mode.
[    14.886] (==) NVIDIA(0): 
[    14.891] (II) NVIDIA(0): Validated MetaModes:
[    14.891] (II) NVIDIA(0):     "DFP-0:nvidia-auto-select"
[    14.891] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
[    14.936] (--) NVIDIA(0): DPI set to (95, 94); computed from "UseEdidDpi" X config
[    14.936] (--) NVIDIA(0):     option
[    14.936] (--) Depth 24 pixmap format is 32 bpp
[    14.936] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    14.977] (II) NVIDIA(0): Setting mode "DFP-0:nvidia-auto-select"
[    15.068] Loading extension NV-GLX
[    15.138] (==) NVIDIA(0): Disabling shared memory pixmaps
[    15.138] (==) NVIDIA(0): Backing store enabled
[    15.138] (==) NVIDIA(0): Silken mouse enabled
[    15.139] (==) NVIDIA(0): DPMS enabled
[    15.139] Loading extension NV-CONTROL
[    15.148] Loading extension XINERAMA
[    15.148] (II) Loading sub module "dri2"
[    15.148] (II) LoadModule: "dri2"
[    15.148] (II) Module "dri2" already built-in
[    15.148] (II) NVIDIA(0): [DRI2] Setup complete
[    15.148] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[    15.148] (--) RandR disabled
[    15.177] (II) SELinux: Disabled on system
[    15.179] (II) Initializing extension GLX
[    15.280] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    15.283] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0/drm/card0
[    15.292] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    15.293] (II) config/udev: Adding input device C-Media Electronics Inc.       USB PnP Sound Device (/dev/input/event2)
[    15.293] (**) C-Media Electronics Inc.       USB PnP Sound Device: Applying InputClass "evdev keyboard catchall"
[    15.293] (II) LoadModule: "evdev"
[    15.293] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    15.308] (II) Module evdev: vendor="X.Org Foundation"
[    15.308] 	compiled for 1.15.0, module version = 2.8.2
[    15.308] 	Module class: X.Org XInput Driver
[    15.308] 	ABI class: X.Org XInput driver, version 20.0
[    15.308] (II) Using input driver 'evdev' for 'C-Media Electronics Inc.       USB PnP Sound Device'
[    15.308] (**) C-Media Electronics Inc.       USB PnP Sound Device: always reports core events
[    15.308] (**) evdev: C-Media Electronics Inc.       USB PnP Sound Device: Device: "/dev/input/event2"
[    15.340] (--) evdev: C-Media Electronics Inc.       USB PnP Sound Device: Vendor 0xccd Product 0x77
[    15.340] (--) evdev: C-Media Electronics Inc.       USB PnP Sound Device: Found 1 mouse buttons
[    15.340] (--) evdev: C-Media Electronics Inc.       USB PnP Sound Device: Found keys
[    15.340] (II) evdev: C-Media Electronics Inc.       USB PnP Sound Device: Forcing relative x/y axes to exist.
[    15.340] (II) evdev: C-Media Electronics Inc.       USB PnP Sound Device: Configuring as mouse
[    15.340] (II) evdev: C-Media Electronics Inc.       USB PnP Sound Device: Configuring as keyboard
[    15.340] (**) evdev: C-Media Electronics Inc.       USB PnP Sound Device: YAxisMapping: buttons 4 and 5
[    15.340] (**) evdev: C-Media Electronics Inc.       USB PnP Sound Device: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    15.340] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2:1.3/input/input5/event2"
[    15.340] (II) XINPUT: Adding extended input device "C-Media Electronics Inc.       USB PnP Sound Device" (type: KEYBOARD, id 6)
[    15.340] (**) Option "xkb_rules" "evdev"
[    15.340] (**) Option "xkb_model" "pc105"
[    15.340] (**) Option "xkb_layout" "se"
[    15.344] (II) XKB: reuse xkmfile /var/lib/xkb/server-523B07B557B20588EB459118C97940B7C9FF61EB.xkm
[    15.345] (II) config/udev: Adding input device Logitech Logitech BT Mini-Receiver (/dev/input/event5)
[    15.346] (**) Logitech Logitech BT Mini-Receiver: Applying InputClass "evdev keyboard catchall"
[    15.346] (II) Using input driver 'evdev' for 'Logitech Logitech BT Mini-Receiver'
[    15.346] (**) Logitech Logitech BT Mini-Receiver: always reports core events
[    15.346] (**) evdev: Logitech Logitech BT Mini-Receiver: Device: "/dev/input/event5"
[    15.380] (--) evdev: Logitech Logitech BT Mini-Receiver: Vendor 0x46d Product 0xc70b
[    15.380] (--) evdev: Logitech Logitech BT Mini-Receiver: Found keys
[    15.380] (II) evdev: Logitech Logitech BT Mini-Receiver: Configuring as keyboard
[    15.380] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2.2/6-2.2:1.0/input/input8/event5"
[    15.380] (II) XINPUT: Adding extended input device "Logitech Logitech BT Mini-Receiver" (type: KEYBOARD, id 7)
[    15.380] (**) Option "xkb_rules" "evdev"
[    15.380] (**) Option "xkb_model" "pc105"
[    15.380] (**) Option "xkb_layout" "se"
[    15.381] (II) config/udev: Adding input device Logitech Logitech BT Mini-Receiver (/dev/input/event6)
[    15.381] (**) Logitech Logitech BT Mini-Receiver: Applying InputClass "evdev pointer catchall"
[    15.381] (**) Logitech Logitech BT Mini-Receiver: Applying InputClass "evdev keyboard catchall"
[    15.381] (II) Using input driver 'evdev' for 'Logitech Logitech BT Mini-Receiver'
[    15.381] (**) Logitech Logitech BT Mini-Receiver: always reports core events
[    15.381] (**) evdev: Logitech Logitech BT Mini-Receiver: Device: "/dev/input/event6"
[    15.412] (--) evdev: Logitech Logitech BT Mini-Receiver: Vendor 0x46d Product 0xc70c
[    15.412] (--) evdev: Logitech Logitech BT Mini-Receiver: Found 16 mouse buttons
[    15.412] (--) evdev: Logitech Logitech BT Mini-Receiver: Found scroll wheel(s)
[    15.412] (--) evdev: Logitech Logitech BT Mini-Receiver: Found relative axes
[    15.412] (--) evdev: Logitech Logitech BT Mini-Receiver: Found x and y relative axes
[    15.412] (--) evdev: Logitech Logitech BT Mini-Receiver: Found absolute axes
[    15.412] (II) evdev: Logitech Logitech BT Mini-Receiver: Forcing absolute x/y axes to exist.
[    15.412] (--) evdev: Logitech Logitech BT Mini-Receiver: Found keys
[    15.412] (II) evdev: Logitech Logitech BT Mini-Receiver: Configuring as mouse
[    15.412] (II) evdev: Logitech Logitech BT Mini-Receiver: Configuring as keyboard
[    15.412] (II) evdev: Logitech Logitech BT Mini-Receiver: Adding scrollwheel support
[    15.412] (**) evdev: Logitech Logitech BT Mini-Receiver: YAxisMapping: buttons 4 and 5
[    15.412] (**) evdev: Logitech Logitech BT Mini-Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    15.412] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2.3/6-2.3:1.0/input/input9/event6"
[    15.412] (II) XINPUT: Adding extended input device "Logitech Logitech BT Mini-Receiver" (type: KEYBOARD, id 8)
[    15.412] (**) Option "xkb_rules" "evdev"
[    15.412] (**) Option "xkb_model" "pc105"
[    15.412] (**) Option "xkb_layout" "se"
[    15.412] (II) evdev: Logitech Logitech BT Mini-Receiver: initialized for relative axes.
[    15.412] (WW) evdev: Logitech Logitech BT Mini-Receiver: ignoring absolute axes.
[    15.413] (**) Logitech Logitech BT Mini-Receiver: (accel) keeping acceleration scheme 1
[    15.413] (**) Logitech Logitech BT Mini-Receiver: (accel) acceleration profile 0
[    15.413] (**) Logitech Logitech BT Mini-Receiver: (accel) acceleration factor: 2.000
[    15.413] (**) Logitech Logitech BT Mini-Receiver: (accel) acceleration threshold: 4
[    15.413] (II) config/udev: Adding input device Logitech Logitech BT Mini-Receiver (/dev/input/mouse1)
[    15.414] (II) No input driver specified, ignoring this device.
[    15.414] (II) This device may have been added with another device file.
[    19.951] (II) NVIDIA(GPU-0): Display (DELL U2312HM (DFP-0)) does not support NVIDIA 3D
[    19.951] (II) NVIDIA(GPU-0):     Vision stereo.
[    19.951] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    19.951] (**) NVIDIA(0):     device DELL U2312HM (DFP-0) (Using EDID frequencies has
[    19.951] (**) NVIDIA(0):     been enabled on all display devices.)
[    21.306] (II) XKB: reuse xkmfile /var/lib/xkb/server-523B07B557B20588EB459118C97940B7C9FF61EB.xkm
[    21.910] (II) XKB: reuse xkmfile /var/lib/xkb/server-29B4A8573FEC6CF8C84AFFBD4D6BCEE950C7B976.xkm
[    23.369] (II) XKB: reuse xkmfile /var/lib/xkb/server-DC21AD274DC9E7DBF4EDEEA656AE6D12573A7A81.xkm
[    23.374] (II) XKB: reuse xkmfile /var/lib/xkb/server-56365E9F5DDB4DE8CA75E8EFEE28D399BFF865B0.xkm
[    23.397] (II) XKB: reuse xkmfile /var/lib/xkb/server-56365E9F5DDB4DE8CA75E8EFEE28D399BFF865B0.xkm
[    23.415] (II) XKB: reuse xkmfile /var/lib/xkb/server-56365E9F5DDB4DE8CA75E8EFEE28D399BFF865B0.xkm
[    23.429] (II) XKB: reuse xkmfile /var/lib/xkb/server-56365E9F5DDB4DE8CA75E8EFEE28D399BFF865B0.xkm
[    23.444] (II) XKB: reuse xkmfile /var/lib/xkb/server-56365E9F5DDB4DE8CA75E8EFEE28D399BFF865B0.xkm
[    23.687] (II) XKB: reuse xkmfile /var/lib/xkb/server-DC21AD274DC9E7DBF4EDEEA656AE6D12573A7A81.xkm
[    23.696] (II) XKB: reuse xkmfile /var/lib/xkb/server-56365E9F5DDB4DE8CA75E8EFEE28D399BFF865B0.xkm
[    23.715] (II) XKB: reuse xkmfile /var/lib/xkb/server-56365E9F5DDB4DE8CA75E8EFEE28D399BFF865B0.xkm
[    23.723] (II) XKB: reuse xkmfile /var/lib/xkb/server-56365E9F5DDB4DE8CA75E8EFEE28D399BFF865B0.xkm
[    23.738] (II) XKB: reuse xkmfile /var/lib/xkb/server-56365E9F5DDB4DE8CA75E8EFEE28D399BFF865B0.xkm
[    23.747] (II) XKB: reuse xkmfile /var/lib/xkb/server-56365E9F5DDB4DE8CA75E8EFEE28D399BFF865B0.xkm
[    24.276] (II) NVIDIA(GPU-0): Display (DELL U2312HM (DFP-0)) does not support NVIDIA 3D
[    24.276] (II) NVIDIA(GPU-0):     Vision stereo.
[    24.276] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    24.276] (**) NVIDIA(0):     device DELL U2312HM (DFP-0) (Using EDID frequencies has
[    24.276] (**) NVIDIA(0):     been enabled on all display devices.)
[    24.414] (II) NVIDIA(GPU-0): Display (DELL U2312HM (DFP-0)) does not support NVIDIA 3D
[    24.419] (II) NVIDIA(GPU-0):     Vision stereo.
[    24.419] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    24.419] (**) NVIDIA(0):     device DELL U2312HM (DFP-0) (Using EDID frequencies has
[    24.419] (**) NVIDIA(0):     been enabled on all display devices.)
[    39.228] (II) NVIDIA(GPU-0): Display (DELL U2312HM (DFP-0)) does not support NVIDIA 3D
[    39.228] (II) NVIDIA(GPU-0):     Vision stereo.
[    39.228] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    39.228] (**) NVIDIA(0):     device DELL U2312HM (DFP-0) (Using EDID frequencies has
[    39.228] (**) NVIDIA(0):     been enabled on all display devices.)
[   111.427] (II) XKB: reuse xkmfile /var/lib/xkb/server-56365E9F5DDB4DE8CA75E8EFEE28D399BFF865B0.xkm
```

/Marcus

---

### Post by malaTG on 2015-08-22
bump

---

