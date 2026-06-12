---
title: "9600 GT overclock"
date: 2011-01-08
forum: Hardware
---

### Post by xXDestroyerGRXx on 2011-01-08
Hello, i enabled the overclock option from the from the xorg file and i try to change mhz clock values and when i click apply the clock go to default settings

Why this is happening ?

---

### Post by cascade9 on 2011-01-08
Try nvclock- 

[http://www.linuxhardware.org/nvclock/](http://www.linuxhardware.org/nvclock/)

---

### Post by xXDestroyerGRXx on 2011-01-08
> **cascade9 said:**
> Try nvclock- 

[http://www.linuxhardware.org/nvclock/](http://www.linuxhardware.org/nvclock/)

I tryed to change with nvclock but when i click change speeds the settings go default!!

That is strange!

---

### Post by Fafler on 2011-01-08
Whats in your /var/log/Xorg.0.log?

---

### Post by cchhrriiss121212 on 2011-01-08
I have the same card and the same problem, here is my log:
```
chris@crunchbang:~$ cat /var/log/Xorg.0.log

X.Org X Server 1.7.7
Release Date: 2010-05-04
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.32.26-dsa-amd64 x86_64 Debian
Current Operating System: Linux crunchbang 2.6.36-2.dmz.5-liquorix-amd64 #1 ZEN SMP PREEMPT Tue Dec 14 20:40:25 CST 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.36-2.dmz.5-liquorix-amd64 root=UUID=77fb4506-c1a8-4007-a4ec-7eaa3a56fc7a ro quiet splash
Build Date: 02 December 2010  01:10:32AM
xorg-server 2:1.7.7-10 (Julien Cristau <jcristau@debian.org>) 
Current version of pixman: 0.16.4
    Before reporting problems, check [http://wiki.x.org]("http://wiki.x.org/")
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Jan  8 13:02:21 2011
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(**) Option "Xinerama" "0"
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
(II) Loader magic: 0x7c7500
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI: (0:0:1:3) 10de:0543:1849:0543 nVidia Corporation MCP67 Co-processor rev 162, Mem @ 0xf9e80000/524288
(--) PCI:*(0:2:0:0) 10de:0622:1682:2365 nVidia Corporation G94 [GeForce 9600 GT] rev 161, Mem @ 0xfd000000/16777216, 0xd0000000/268435456, 0xfa000000/33554432, I/O @ 0x0000ec00/128, BIOS @ 0x????????/524288
(II) Open ACPI successful (/var/run/acpid.socket)
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.7.7, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension SELinux
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  260.19.29  Wed Dec  8 12:24:30 PST 2010
(II) Loading extension GLX
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.7.7, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.7.7, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.7.7, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.7.7, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  260.19.29  Wed Dec  8 12:10:14 PST 2010
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 02@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.7.7, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules/libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
    compiled for 1.7.7, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "TwinView" "0"
(**) NVIDIA(0): Option "MetaModes" "1920x1200_60 +0+0"
(**) Jan 08 13:02:22 NVIDIA(0): Enabling RENDER acceleration
(II) Jan 08 13:02:22 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Jan 08 13:02:22 NVIDIA(0):     enabled.
(II) Jan 08 13:02:23 NVIDIA(0): NVIDIA GPU GeForce 9600 GT (G94) at PCI:2:0:0 (GPU-0)
(--) Jan 08 13:02:23 NVIDIA(0): Memory: 524288 kBytes
(--) Jan 08 13:02:23 NVIDIA(0): VideoBIOS: 62.94.29.00.50
(II) Jan 08 13:02:23 NVIDIA(0): Detected PCI Express Link width: 16X
(--) Jan 08 13:02:23 NVIDIA(0): Interlaced video modes are supported on this GPU
(--) Jan 08 13:02:23 NVIDIA(0): Connected display device(s) on GeForce 9600 GT at PCI:2:0:0
(--) Jan 08 13:02:23 NVIDIA(0):     Samsung SyncMaster (DFP-0)
(--) Jan 08 13:02:23 NVIDIA(0): Samsung SyncMaster (DFP-0): 330.0 MHz maximum pixel clock
(--) Jan 08 13:02:23 NVIDIA(0): Samsung SyncMaster (DFP-0): Internal Dual Link TMDS
(II) Jan 08 13:02:23 NVIDIA(0): Assigned Display Device: DFP-0
(II) Jan 08 13:02:23 NVIDIA(0): Validated modes:
(II) Jan 08 13:02:23 NVIDIA(0):     "1920x1200_60+0+0"
(II) Jan 08 13:02:23 NVIDIA(0): Virtual screen size determined to be 1920 x 1200
(--) Jan 08 13:02:23 NVIDIA(0): DPI set to (93, 95); computed from "UseEdidDpi" X config
(--) Jan 08 13:02:23 NVIDIA(0):     option
(==) Jan 08 13:02:23 NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) Jan 08 13:02:23 NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
(II) Jan 08 13:02:23 NVIDIA(0): Initialized GPU GART.
(II) Jan 08 13:02:23 NVIDIA(0): Setting mode "1920x1200_60+0+0"
(II) Loading extension NV-GLX
(II) Jan 08 13:02:23 NVIDIA(0): Initialized OpenGL Acceleration
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) Jan 08 13:02:24 NVIDIA(0): Initialized X Rendering Acceleration
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
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
SELinux: Disabled on system, not enabling in X server
(II) Initializing extension GLX
(II) config/udev: Adding input device Power Button (/dev/input/event2)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.7.6.901, module version = 2.3.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event2"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "gb"
(II) config/udev: Adding input device Power Button (/dev/input/event1)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "gb"
(II) config/udev: Adding input device Logitech Logitech Dual Action (/dev/input/event3)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Logitech Logitech Dual Action (/dev/input/js0)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Microsoft Microsoft Notebook Receiver v2.0 (/dev/input/event4)
(**) Microsoft Microsoft Notebook Receiver v2.0: Applying InputClass "evdev pointer catchall"
(**) Microsoft Microsoft Notebook Receiver v2.0: always reports core events
(**) Microsoft Microsoft Notebook Receiver v2.0: Device: "/dev/input/event4"
(II) Microsoft Microsoft Notebook Receiver v2.0: Found 9 mouse buttons
(II) Microsoft Microsoft Notebook Receiver v2.0: Found scroll wheel(s)
(II) Microsoft Microsoft Notebook Receiver v2.0: Found relative axes
(II) Microsoft Microsoft Notebook Receiver v2.0: Found x and y relative axes
(II) Microsoft Microsoft Notebook Receiver v2.0: Configuring as mouse
(**) Microsoft Microsoft Notebook Receiver v2.0: YAxisMapping: buttons 4 and 5
(**) Microsoft Microsoft Notebook Receiver v2.0: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Microsoft Microsoft Notebook Receiver v2.0" (type: MOUSE)
(II) Microsoft Microsoft Notebook Receiver v2.0: initialized for relative axes.
(II) config/udev: Adding input device Microsoft Microsoft Notebook Receiver v2.0 (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event0)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event0"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "gb"
(II) config/udev: Adding input device PC Speaker (/dev/input/event5)
(II) No input driver/identifier specified (ignoring)
```

---

### Post by xXDestroyerGRXx on 2011-01-08
```
[    20.866] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    20.866] X Protocol Version 11, Revision 0
[    20.866] Build Operating System: Linux 2.6.24-28-server x86_64 Ubuntu
[    20.866] Current Operating System: Linux alexandros-System-Product-Name 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 02:41:37 UTC 2010 x86_64
[    20.866] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-24-generic root=UUID=f1c0aefb-ad49-4490-8a1d-6304b7323fb6 ro quiet splash nomodeset video=uvesafb:mode_option=1280x1024-24,mtrr=3,scroll=ywrap
[    20.866] Build Date: 23 November 2010  11:54:56PM
[    20.866] xorg-server 2:1.9.0-0ubuntu7.1 (For technical support please see http://www.ubuntu.com/support) 
[    20.866] Current version of pixman: 0.18.4
[    20.866]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    20.866] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    20.867] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Jan  8 16:14:33 2011
[    20.867] (==) Using config file: "/etc/X11/xorg.conf"
[    20.867] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    20.867] (==) No Layout section.  Using the first Screen section.
[    20.867] (**) |-->Screen "Default Screen" (0)
[    20.867] (**) |   |-->Monitor "<default monitor>"
[    20.868] (==) No device specified for screen "Default Screen".
    Using the first device section listed.
[    20.868] (**) |   |-->Device "Default Device"
[    20.868] (==) No monitor specified for screen "Default Screen".
    Using a default monitor configuration.
[    20.868] (==) Automatically adding devices
[    20.868] (==) Automatically enabling devices
[    20.868] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    20.868]     Entry deleted from font path.
[    20.868] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    20.868] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    20.868] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    20.868] (II) Loader magic: 0x7d17a0
[    20.868] (II) Module ABI versions:
[    20.868]     X.Org ANSI C Emulation: 0.4
[    20.868]     X.Org Video Driver: 8.0
[    20.868]     X.Org XInput driver : 11.0
[    20.868]     X.Org Server Extension : 4.0
[    20.870] (--) PCI:*(0:1:0:0) 10de:0622:1458:3480 rev 161, Mem @ 0xc0000000/16777216, 0xa0000000/268435456, 0xdc000000/33554432, I/O @ 0x0000dc00/128, BIOS @ 0x????????/524288
[    20.871] (II) Open ACPI successful (/var/run/acpid.socket)
[    20.871] (II) "extmod" will be loaded by default.
[    20.871] (II) "dbe" will be loaded by default.
[    20.871] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    20.871] (II) "record" will be loaded by default.
[    20.871] (II) "dri" will be loaded by default.
[    20.871] (II) "dri2" will be loaded by default.
[    20.871] (II) LoadModule: "glx"
[    20.872] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    20.894] (II) Module glx: vendor="NVIDIA Corporation"
[    20.894]     compiled for 4.0.2, module version = 1.0.0
[    20.894]     Module class: X.Org Server Extension
[    20.894] (II) NVIDIA GLX Module  260.19.06  Mon Sep 13 04:54:41 PDT 2010
[    20.894] (II) Loading extension GLX
[    20.894] (II) LoadModule: "extmod"
[    20.908] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    20.908] (II) Module extmod: vendor="X.Org Foundation"
[    20.908]     compiled for 1.9.0, module version = 1.0.0
[    20.908]     Module class: X.Org Server Extension
[    20.908]     ABI class: X.Org Server Extension, version 4.0
[    20.908] (II) Loading extension MIT-SCREEN-SAVER
[    20.908] (II) Loading extension XFree86-VidModeExtension
[    20.908] (II) Loading extension XFree86-DGA
[    20.908] (II) Loading extension DPMS
[    20.908] (II) Loading extension XVideo
[    20.908] (II) Loading extension XVideo-MotionCompensation
[    20.908] (II) Loading extension X-Resource
[    20.908] (II) LoadModule: "dbe"
[    20.909] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    20.909] (II) Module dbe: vendor="X.Org Foundation"
[    20.909]     compiled for 1.9.0, module version = 1.0.0
[    20.909]     Module class: X.Org Server Extension
[    20.909]     ABI class: X.Org Server Extension, version 4.0
[    20.909] (II) Loading extension DOUBLE-BUFFER
[    20.909] (II) LoadModule: "record"
[    20.909] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    20.910] (II) Module record: vendor="X.Org Foundation"
[    20.910]     compiled for 1.9.0, module version = 1.13.0
[    20.910]     Module class: X.Org Server Extension
[    20.910]     ABI class: X.Org Server Extension, version 4.0
[    20.910] (II) Loading extension RECORD
[    20.910] (II) LoadModule: "dri"
[    20.910] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    20.910] (II) Module dri: vendor="X.Org Foundation"
[    20.911]     compiled for 1.9.0, module version = 1.0.0
[    20.911]     ABI class: X.Org Server Extension, version 4.0
[    20.911] (II) Loading extension XFree86-DRI
[    20.911] (II) LoadModule: "dri2"
[    20.911] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    20.911] (II) Module dri2: vendor="X.Org Foundation"
[    20.911]     compiled for 1.9.0, module version = 1.2.0
[    20.911]     ABI class: X.Org Server Extension, version 4.0
[    20.911] (II) Loading extension DRI2
[    20.911] (II) LoadModule: "nvidia"
[    20.911] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    20.912] (II) Module nvidia: vendor="NVIDIA Corporation"
[    20.912]     compiled for 4.0.2, module version = 1.0.0
[    20.912]     Module class: X.Org Video Driver
[    20.912] (II) NVIDIA dlloader X Driver  260.19.06  Mon Sep 13 04:31:43 PDT 2010
[    20.912] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    20.912] (++) using VT number 7

[    20.913] (II) Loading sub module "fb"
[    20.913] (II) LoadModule: "fb"
[    20.913] (II) Loading /usr/lib/xorg/modules/libfb.so
[    20.913] (II) Module fb: vendor="X.Org Foundation"
[    20.913]     compiled for 1.9.0, module version = 1.0.0
[    20.913]     ABI class: X.Org ANSI C Emulation, version 0.4
[    20.913] (II) Loading sub module "wfb"
[    20.913] (II) LoadModule: "wfb"
[    20.914] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    20.914] (II) Module wfb: vendor="X.Org Foundation"
[    20.914]     compiled for 1.9.0, module version = 1.0.0
[    20.914]     ABI class: X.Org ANSI C Emulation, version 0.4
[    20.914] (II) Loading sub module "ramdac"
[    20.914] (II) LoadModule: "ramdac"
[    20.914] (II) Module "ramdac" already built-in
[    20.914] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
[    20.914] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    20.914] (==) NVIDIA(0): RGB weight 888
[    20.914] (==) NVIDIA(0): Default visual is TrueColor
[    20.914] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    20.915] (**) NVIDIA(0): Option "NoLogo" "True"
[    20.915] (**) NVIDIA(0): Option "Coolbits" "1"
[    20.915] (**) NVIDIA(0): Enabling RENDER acceleration
[    20.915] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[    20.915] (II) NVIDIA(0):     enabled.
[    22.559] (II) NVIDIA(0): NVIDIA GPU GeForce 9600 GT (G94) at PCI:1:0:0 (GPU-0)
[    22.559] (--) NVIDIA(0): Memory: 524288 kBytes
[    22.559] (--) NVIDIA(0): VideoBIOS: 62.94.11.00.03
[    22.559] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    22.559] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    22.559] (--) NVIDIA(0): Connected display device(s) on GeForce 9600 GT at PCI:1:0:0
[    22.559] (--) NVIDIA(0):     LG Electronics L1919S (CRT-1)
[    22.559] (--) NVIDIA(0): LG Electronics L1919S (CRT-1): 400.0 MHz maximum pixel clock
[    22.639] (II) NVIDIA(0): Assigned Display Device: CRT-1
[    22.639] (==) NVIDIA(0): 
[    22.639] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    22.639] (==) NVIDIA(0):     will be used as the requested mode.
[    22.639] (==) NVIDIA(0): 
[    22.639] (II) NVIDIA(0): Validated modes:
[    22.639] (II) NVIDIA(0):     "nvidia-auto-select"
[    22.639] (II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
[    22.672] (--) NVIDIA(0): DPI set to (85, 86); computed from "UseEdidDpi" X config
[    22.672] (--) NVIDIA(0):     option
[    22.672] (==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
[    22.672] (--) Depth 24 pixmap format is 32 bpp
[    22.672] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    22.673] (II) NVIDIA(0): Initialized GPU GART.
[    22.680] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[    22.704] (II) Loading extension NV-GLX
[    22.739] (II) NVIDIA(0): Initialized OpenGL Acceleration
[    22.747] (==) NVIDIA(0): Disabling shared memory pixmaps
[    22.747] (II) NVIDIA(0): Initialized X Rendering Acceleration
[    22.747] (==) NVIDIA(0): Backing store disabled
[    22.747] (==) NVIDIA(0): Silken mouse enabled
[    22.749] (==) NVIDIA(0): DPMS enabled
[    22.750] (II) Loading extension NV-CONTROL
[    22.750] (II) Loading extension XINERAMA
[    22.750] (II) Loading sub module "dri2"
[    22.750] (II) LoadModule: "dri2"
[    22.751] (II) Reloading /usr/lib/xorg/modules/extensions/libdri2.so
[    22.751] (II) NVIDIA(0): [DRI2] Setup complete
[    22.751] (==) RandR enabled
[    22.751] (II) Initializing built-in extension Generic Event Extension
[    22.751] (II) Initializing built-in extension SHAPE
[    22.751] (II) Initializing built-in extension MIT-SHM
[    22.751] (II) Initializing built-in extension XInputExtension
[    22.751] (II) Initializing built-in extension XTEST
[    22.751] (II) Initializing built-in extension BIG-REQUESTS
[    22.751] (II) Initializing built-in extension SYNC
[    22.751] (II) Initializing built-in extension XKEYBOARD
[    22.751] (II) Initializing built-in extension XC-MISC
[    22.751] (II) Initializing built-in extension SECURITY
[    22.751] (II) Initializing built-in extension XINERAMA
[    22.751] (II) Initializing built-in extension XFIXES
[    22.751] (II) Initializing built-in extension RENDER
[    22.751] (II) Initializing built-in extension RANDR
[    22.751] (II) Initializing built-in extension COMPOSITE
[    22.751] (II) Initializing built-in extension DAMAGE
[    22.751] (II) Initializing built-in extension GESTURE
[    22.751] (II) Initializing extension GLX
[    22.801] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    22.815] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    22.815] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    22.816] (II) LoadModule: "evdev"
[    22.816] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    22.816] (II) Module evdev: vendor="X.Org Foundation"
[    22.817]     compiled for 1.9.0, module version = 2.3.2
[    22.817]     Module class: X.Org XInput Driver
[    22.817]     ABI class: X.Org XInput driver, version 11.0
[    22.817] (**) Power Button: always reports core events
[    22.817] (**) Power Button: Device: "/dev/input/event1"
[    22.860] (II) Power Button: Found keys
[    22.860] (II) Power Button: Configuring as keyboard
[    22.860] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    22.860] (**) Option "xkb_rules" "evdev"
[    22.860] (**) Option "xkb_model" "evdev"
[    22.860] (**) Option "xkb_layout" "us,gr"
[    22.860] (**) Option "xkb_variant" ","
[    22.860] (**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
[    22.863] (II) XKB: reuse xkmfile /var/lib/xkb/server-0784873EABBE2F3F8DCDEC70A37F488F93ECB155.xkm
[    22.866] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    22.866] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    22.866] (**) Power Button: always reports core events
[    22.866] (**) Power Button: Device: "/dev/input/event0"
[    22.900] (II) Power Button: Found keys
[    22.900] (II) Power Button: Configuring as keyboard
[    22.900] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    22.900] (**) Option "xkb_rules" "evdev"
[    22.900] (**) Option "xkb_model" "evdev"
[    22.900] (**) Option "xkb_layout" "us,gr"
[    22.900] (**) Option "xkb_variant" ","
[    22.900] (**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
[    22.902] (II) config/udev: Adding input device Microsoft Comfort Optical Mouse 1000 (/dev/input/event2)
[    22.902] (**) Microsoft Comfort Optical Mouse 1000: Applying InputClass "evdev pointer catchall"
[    22.902] (**) Microsoft Comfort Optical Mouse 1000: always reports core events
[    22.902] (**) Microsoft Comfort Optical Mouse 1000: Device: "/dev/input/event2"
[    22.940] (II) Microsoft Comfort Optical Mouse 1000: Found 3 mouse buttons
[    22.940] (II) Microsoft Comfort Optical Mouse 1000: Found scroll wheel(s)
[    22.940] (II) Microsoft Comfort Optical Mouse 1000: Found relative axes
[    22.940] (II) Microsoft Comfort Optical Mouse 1000: Found x and y relative axes
[    22.940] (II) Microsoft Comfort Optical Mouse 1000: Configuring as mouse
[    22.940] (**) Microsoft Comfort Optical Mouse 1000: YAxisMapping: buttons 4 and 5
[    22.940] (**) Microsoft Comfort Optical Mouse 1000: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    22.940] (II) XINPUT: Adding extended input device "Microsoft Comfort Optical Mouse 1000" (type: MOUSE)
[    22.940] (II) Microsoft Comfort Optical Mouse 1000: initialized for relative axes.
[    22.941] (II) config/udev: Adding input device Microsoft Comfort Optical Mouse 1000 (/dev/input/mouse0)
[    22.941] (II) No input driver/identifier specified (ignoring)
[    22.942] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event3)
[    22.942] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    22.942] (**) Logitech USB Receiver: always reports core events
[    22.942] (**) Logitech USB Receiver: Device: "/dev/input/event3"
[    22.980] (II) Logitech USB Receiver: Found keys
[    22.980] (II) Logitech USB Receiver: Configuring as keyboard
[    22.980] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[    22.980] (**) Option "xkb_rules" "evdev"
[    22.980] (**) Option "xkb_model" "evdev"
[    22.980] (**) Option "xkb_layout" "us,gr"
[    22.980] (**) Option "xkb_variant" ","
[    22.980] (**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
[    22.981] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event4)
[    22.981] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[    22.981] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    22.981] (**) Logitech USB Receiver: always reports core events
[    22.981] (**) Logitech USB Receiver: Device: "/dev/input/event4"
[    23.020] (II) Logitech USB Receiver: Found 20 mouse buttons
[    23.020] (II) Logitech USB Receiver: Found scroll wheel(s)
[    23.020] (II) Logitech USB Receiver: Found relative axes
[    23.020] (II) Logitech USB Receiver: Found x and y relative axes
[    23.020] (II) Logitech USB Receiver: Found absolute axes
[    23.020] (II) evdev-grail: failed to open grail, no gesture support
[    23.020] (II) Logitech USB Receiver: Found keys
[    23.020] (II) Logitech USB Receiver: Configuring as mouse
[    23.020] (II) Logitech USB Receiver: Configuring as keyboard
[    23.020] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[    23.020] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    23.020] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[    23.020] (**) Option "xkb_rules" "evdev"
[    23.020] (**) Option "xkb_model" "evdev"
[    23.020] (**) Option "xkb_layout" "us,gr"
[    23.020] (**) Option "xkb_variant" ","
[    23.020] (**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
[    23.020] (II) Logitech USB Receiver: initialized for relative axes.
[    23.020] (WW) Logitech USB Receiver: ignoring absolute axes.
[    23.021] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse1)
[    23.021] (II) No input driver/identifier specified (ignoring)
[    23.787] (II) NVIDIA(0): Setting mode "1024x768"
[    65.551] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[  2331.995] (II) XKB: reuse xkmfile /var/lib/xkb/server-6B0C086C5A225A83D7F8FF01B9A2DCE28AF5128D.xkm
```

This




offtopic=btw i was born at denmark :D

---

### Post by xXDestroyerGRXx on 2011-01-08
Anyone help me please?

---

### Post by Fafler on 2011-01-08
Is my browser messing around with me or did neither of you include /complete/ logfiles?

I was, by the way, also born in denmark.

---

### Post by xXDestroyerGRXx on 2011-01-08
> **Fafler said:**
> Is my browser messing around with me or did neither of you include /complete/ logfiles?

I was, by the way, also born in denmark.

No i didn't.

---

### Post by JOHNNYG713 on 2011-01-08
Open your BIOS and see if it has an option for overclocking !

---

### Post by cchhrriiss121212 on 2011-01-09
Solved for me. Add this line to xorg.conf under the device section:
    Option "Coolbits" "1"
Now reboot and you can use nvidia-settings to adjust clock speeds for 2d and 3d.

Seems that nvclock is not usable for some cards:
[http://www.overclock.net/linux-unix/463349-oc-gtx-260-ubuntu-nvclock.html](http://www.overclock.net/linux-unix/463349-oc-gtx-260-ubuntu-nvclock.html)

---

### Post by xXDestroyerGRXx on 2011-01-09
> **cchhrriiss121212 said:**
> Solved for me. Add this line to xorg.conf under the device section:
    Option "Coolbits" "1"
Now reboot and you can use nvidia-settings to adjust clock speeds for 2d and 3d.

Seems that nvclock is not usable for some cards:
[http://www.overclock.net/linux-unix/463349-oc-gtx-260-ubuntu-nvclock.html](http://www.overclock.net/linux-unix/463349-oc-gtx-260-ubuntu-nvclock.html)

coolbits is already there



```
Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
        Option "Coolbits" "1"
EndSection

```

---

### Post by cchhrriiss121212 on 2011-01-09
Update:
Using nvidia-settings only allowed me to change the clock speed once, now I am getting the same issue as I had with nv-clock. Better than nothing I suppose.

---

