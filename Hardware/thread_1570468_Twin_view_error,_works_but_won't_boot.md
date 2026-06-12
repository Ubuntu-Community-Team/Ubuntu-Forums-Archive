---
title: "Twin view error, works but won't boot"
date: 2010-09-08
forum: Hardware
---

### Post by frostig on 2010-09-08
Hi folks!

I have a sort of annoying error going on in my system.

The problem is that I bought a new graphic card and then I downloaded and installed a fresh ubuntu 64-bit system on my computer. I installed all updates available and then the nvidia graphic driver. The problem however, occurs when I have enabled my dual screen (Twin View) and have rebooted my system.

It works perfectly until I reboot it and then it goes into low-graphics mode. However, I was kind of lucky to find this thread: [http://art.ubuntuforums.org/showthread.php?t=1468372](http://art.ubuntuforums.org/showthread.php?t=1468372) and that error :

> Failed to initialize the NVIDIA kernel module. Please see the
system's kernel log for additional error messages and
consult the NVIDIA README for details.
*** Aborting ***
Screen(s) found, but none have a usable configuration. ..is almost the same that I've got.

But if I login to the console and then start my X server it'll work as normal:
> I get the same thing - i think what is happening is that X is starting  before the nvidia driver has fully loaded and initialized the GPU -  instead what I do is exit to a login console, then login and manually  start up gdm:My question is, how can I solve this problem?

Thanks in advice.

---

### Post by frostig on 2010-09-08
I just rebooted my system and it's working now. I have no idea why tho, since my old configuration is still there.. :S

But I guess it's solved now.. :)

---

### Post by frostig on 2010-09-08
Update:

I was wrong apparently. Sometimes when I boot it works fine and sometimes it don't and the nvidia kernel module won't load.

And I thought it was complete :/

---

### Post by realzippy on 2010-09-08
Run

```
sudo nvidia-bug-report.sh
```


and post the created file  (home folder) to get a clue...

---

### Post by frostig on 2010-09-09
> **realzippy said:**
> Run

```
sudo nvidia-bug-report.sh
```and post the created file  (home folder) to get a clue...


> ____________________________________________

Start of NVIDIA bug report log file.  Please include this file
when reporting a graphics driver bug via the nV News NVIDIA
Linux forum (see [www.nvnews.net]("http://www.nvnews.net")) or by sending email to
'linux-bugs@nvidia.com'.

nvidia-bug-report.sh Version: 5522491

Date: Thu Sep  9 14:37:25 CEST 2010
uname: Linux kvant 2.6.32-24-generic #42-Ubuntu SMP Fri Aug 20 14:21:58 UTC 2010 x86_64 GNU/Linux

____________________________________________

/etc/issue
Ubuntu 10.04.1 LTS \n \l


____________________________________________

/etc/debian_version
squeeze/sid

____________________________________________

/var/log/nvidia-installer.log does not exist

____________________________________________

/var/log/Xorg.0.log

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux kvant 2.6.32-24-generic #42-Ubuntu SMP Fri Aug 20 14:21:58 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=904eae1e-3da9-44ba-a36f-ba4094c10c8e ro quiet splash
Build Date: 21 July 2010  01:03:39PM
xorg-server 2:1.7.6-2ubuntu7.3 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.16.4
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Sep  9 14:36:17 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
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
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x7ca300
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:2:0:0) 10de:0ca3:1462:2072 nVidia Corporation GT215 [GeForce GT 240] rev 162, Mem @ 0xfd000000/16777216, 0xc0000000/268435456, 0xdc000000/33554432, I/O @ 0x0000cc00/128, BIOS @ 0x????????/524288
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/extra-modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  195.36.24  Thu Apr 22 19:52:00 PDT 2010
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  195.36.24  Thu Apr 22 19:18:54 PDT 2010
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 02@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules/libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "TwinView" "1"
(**) NVIDIA(0): Option "MetaModes" "CRT: nvidia-auto-select +0+0, DFP: nvidia-auto-select +1280+0"
(**) NVIDIA(0): Option "TwinViewXineramaInfoOrder" "DFP-0"
(**) Sep 09 14:36:18 NVIDIA(0): Enabling RENDER acceleration
(II) Sep 09 14:36:18 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Sep 09 14:36:18 NVIDIA(0):     enabled.
(II) Sep 09 14:36:19 NVIDIA(0): NVIDIA GPU GeForce GT 240 (GT215) at PCI:2:0:0 (GPU-0)
(--) Sep 09 14:36:19 NVIDIA(0): Memory: 524288 kBytes
(--) Sep 09 14:36:19 NVIDIA(0): VideoBIOS: 70.15.27.00.02
(II) Sep 09 14:36:19 NVIDIA(0): Detected PCI Express Link width: 4X
(--) Sep 09 14:36:19 NVIDIA(0): Interlaced video modes are supported on this GPU
(--) Sep 09 14:36:19 NVIDIA(0): Connected display device(s) on GeForce GT 240 at PCI:2:0:0:
(--) Sep 09 14:36:19 NVIDIA(0):     Samsung SyncMaster (CRT-1)
(--) Sep 09 14:36:19 NVIDIA(0):     BenQ G2420HD (DFP-0)
(--) Sep 09 14:36:19 NVIDIA(0): Samsung SyncMaster (CRT-1): 400.0 MHz maximum pixel clock
(--) Sep 09 14:36:19 NVIDIA(0): BenQ G2420HD (DFP-0): 330.0 MHz maximum pixel clock
(--) Sep 09 14:36:19 NVIDIA(0): BenQ G2420HD (DFP-0): Internal Dual Link TMDS
(**) Sep 09 14:36:19 NVIDIA(0): TwinView enabled
(II) Sep 09 14:36:19 NVIDIA(0): Display Devices found referenced in MetaMode: CRT-1, DFP-0
(II) Sep 09 14:36:20 NVIDIA(0): Assigned Display Devices: CRT-1, DFP-0
(II) Sep 09 14:36:20 NVIDIA(0): Validated modes:
(II) Sep 09 14:36:20 NVIDIA(0):    
(II) Sep 09 14:36:20 NVIDIA(0):     "CRT:nvidia-auto-select+0+0,DFP:nvidia-auto-select+1280+0"
(II) Sep 09 14:36:20 NVIDIA(0): Virtual screen size determined to be 3200 x 1080
(--) Sep 09 14:36:20 NVIDIA(0): DPI set to (85, 86); computed from "UseEdidDpi" X config
(--) Sep 09 14:36:20 NVIDIA(0):     option
(==) Sep 09 14:36:20 NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) Sep 09 14:36:20 NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
(II) Sep 09 14:36:20 NVIDIA(0): Initialized GPU GART.
(II) Sep 09 14:36:20 NVIDIA(0): Setting mode
(II) Sep 09 14:36:20 NVIDIA(0):     "CRT:nvidia-auto-select+0+0,DFP:nvidia-auto-select+1280+0"
(II) Loading extension NV-GLX
(II) Sep 09 14:36:20 NVIDIA(0): Initialized OpenGL Acceleration
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) Sep 09 14:36:20 NVIDIA(0): Initialized X Rendering Acceleration
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
(II) Initializing extension GLX
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event1)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.3.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "se"
(II) XKB: reuse xkmfile /var/lib/xkb/server-523B07B557B20588EB459118C97940B7C9FF61EB.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "se"
(II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event4)
(**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event4"
(II) Logitech USB Receiver: Found keys
(II) Logitech USB Receiver: Configuring as keyboard
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "se"
(II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event5)
(**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
(**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event5"
(II) Logitech USB Receiver: Found 20 mouse buttons
(II) Logitech USB Receiver: Found scroll wheel(s)
(II) Logitech USB Receiver: Found relative axes
(II) Logitech USB Receiver: Found x and y relative axes
(II) Logitech USB Receiver: Found absolute axes
(II) Logitech USB Receiver: Found keys
(II) Logitech USB Receiver: Configuring as mouse
(II) Logitech USB Receiver: Configuring as keyboard
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "se"
(II) Logitech USB Receiver: initialized for relative axes.
(WW) Logitech USB Receiver: ignoring absolute axes.
(II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Microsoft  Microsoft Basic Optical Mouse v2.0  (/dev/input/event6)
(**) Microsoft  Microsoft Basic Optical Mouse v2.0 : Applying InputClass "evdev pointer catchall"
(**) Microsoft  Microsoft Basic Optical Mouse v2.0 : always reports core events
(**) Microsoft  Microsoft Basic Optical Mouse v2.0 : Device: "/dev/input/event6"
(II) Microsoft  Microsoft Basic Optical Mouse v2.0 : Found 3 mouse buttons
(II) Microsoft  Microsoft Basic Optical Mouse v2.0 : Found scroll wheel(s)
(II) Microsoft  Microsoft Basic Optical Mouse v2.0 : Found relative axes
(II) Microsoft  Microsoft Basic Optical Mouse v2.0 : Found x and y relative axes
(II) Microsoft  Microsoft Basic Optical Mouse v2.0 : Configuring as mouse
(**) Microsoft  Microsoft Basic Optical Mouse v2.0 : YAxisMapping: buttons 4 and 5
(**) Microsoft  Microsoft Basic Optical Mouse v2.0 : EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Microsoft  Microsoft Basic Optical Mouse v2.0 " (type: MOUSE)
(II) Microsoft  Microsoft Basic Optical Mouse v2.0 : initialized for relative axes.
(II) config/udev: Adding input device Microsoft  Microsoft Basic Optical Mouse v2.0  (/dev/input/mouse2)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "se"
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event2)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Digital PCBeep (/dev/input/event7)
(II) No input driver/identifier specified (ignoring)

____________________________________________

/etc/X11/xorg.conf
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@yellow)  Fri Apr  9 11:51:21 UTC 2010

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder58)  Thu Apr 22 20:35:23 PDT 2010

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
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
    BoardName      "GeForce GT 240"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0, DFP: nvidia-auto-select +1280+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


____________________________________________

/var/log/Xorg.0.log.old

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux kvant 2.6.32-24-generic #42-Ubuntu SMP Fri Aug 20 14:21:58 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=904eae1e-3da9-44ba-a36f-ba4094c10c8e ro quiet splash
Build Date: 21 July 2010  01:03:39PM
xorg-server 2:1.7.6-2ubuntu7.3 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.16.4
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Sep  9 02:17:37 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
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
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x7ca300
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(--) using VT number 8

(--) PCI:*(0:2:0:0) 10de:0ca3:1462:2072 nVidia Corporation GT215 [GeForce GT 240] rev 162, Mem @ 0xfd000000/16777216, 0xc0000000/268435456, 0xdc000000/33554432, I/O @ 0x0000cc00/128, BIOS @ 0x????????/524288
(II) Open ACPI successful (/var/run/acpid.socket)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/extra-modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  195.36.24  Thu Apr 22 19:52:00 PDT 2010
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  195.36.24  Thu Apr 22 19:18:54 PDT 2010
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 02@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules/libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "TwinView" "1"
(**) NVIDIA(0): Option "MetaModes" "CRT: nvidia-auto-select +0+0, DFP: nvidia-auto-select +1280+0"
(**) NVIDIA(0): Option "TwinViewXineramaInfoOrder" "DFP-0"
(**) Sep 09 02:17:38 NVIDIA(0): Enabling RENDER acceleration
(II) Sep 09 02:17:38 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Sep 09 02:17:38 NVIDIA(0):     enabled.
(II) Sep 09 02:17:39 NVIDIA(0): NVIDIA GPU GeForce GT 240 (GT215) at PCI:2:0:0 (GPU-0)
(--) Sep 09 02:17:39 NVIDIA(0): Memory: 524288 kBytes
(--) Sep 09 02:17:39 NVIDIA(0): VideoBIOS: 70.15.27.00.02
(II) Sep 09 02:17:39 NVIDIA(0): Detected PCI Express Link width: 4X
(--) Sep 09 02:17:39 NVIDIA(0): Interlaced video modes are supported on this GPU
(--) Sep 09 02:17:39 NVIDIA(0): Connected display device(s) on GeForce GT 240 at PCI:2:0:0:
(--) Sep 09 02:17:39 NVIDIA(0):     Samsung SyncMaster (CRT-1)
(--) Sep 09 02:17:39 NVIDIA(0):     BenQ G2420HD (DFP-0)
(--) Sep 09 02:17:39 NVIDIA(0): Samsung SyncMaster (CRT-1): 400.0 MHz maximum pixel clock
(--) Sep 09 02:17:39 NVIDIA(0): BenQ G2420HD (DFP-0): 330.0 MHz maximum pixel clock
(--) Sep 09 02:17:39 NVIDIA(0): BenQ G2420HD (DFP-0): Internal Dual Link TMDS
(**) Sep 09 02:17:39 NVIDIA(0): TwinView enabled
(II) Sep 09 02:17:39 NVIDIA(0): Display Devices found referenced in MetaMode: CRT-1, DFP-0
(II) Sep 09 02:17:39 NVIDIA(0): Assigned Display Devices: CRT-1, DFP-0
(II) Sep 09 02:17:39 NVIDIA(0): Validated modes:
(II) Sep 09 02:17:39 NVIDIA(0):    
(II) Sep 09 02:17:39 NVIDIA(0):     "CRT:nvidia-auto-select+0+0,DFP:nvidia-auto-select+1280+0"
(II) Sep 09 02:17:39 NVIDIA(0): Virtual screen size determined to be 3200 x 1080
(--) Sep 09 02:17:39 NVIDIA(0): DPI set to (85, 86); computed from "UseEdidDpi" X config
(--) Sep 09 02:17:39 NVIDIA(0):     option
(==) Sep 09 02:17:39 NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) Sep 09 02:17:39 NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
(II) Sep 09 02:17:39 NVIDIA(0): Initialized GPU GART.
(II) Sep 09 02:17:39 NVIDIA(0): Setting mode
(II) Sep 09 02:17:39 NVIDIA(0):     "CRT:nvidia-auto-select+0+0,DFP:nvidia-auto-select+1280+0"
(II) Loading extension NV-GLX
(II) Sep 09 02:17:39 NVIDIA(0): Initialized OpenGL Acceleration
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) Sep 09 02:17:39 NVIDIA(0): Initialized X Rendering Acceleration
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
(II) Initializing extension GLX
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event1)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.3.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "se"
(II) XKB: reuse xkmfile /var/lib/xkb/server-523B07B557B20588EB459118C97940B7C9FF61EB.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "se"
(II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event4)
(**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event4"
(II) Logitech USB Receiver: Found keys
(II) Logitech USB Receiver: Configuring as keyboard
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "se"
(II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event5)
(**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
(**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event5"
(II) Logitech USB Receiver: Found 20 mouse buttons
(II) Logitech USB Receiver: Found scroll wheel(s)
(II) Logitech USB Receiver: Found relative axes
(II) Logitech USB Receiver: Found x and y relative axes
(II) Logitech USB Receiver: Found absolute axes
(II) Logitech USB Receiver: Found keys
(II) Logitech USB Receiver: Configuring as mouse
(II) Logitech USB Receiver: Configuring as keyboard
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "se"
(II) Logitech USB Receiver: initialized for relative axes.
(WW) Logitech USB Receiver: ignoring absolute axes.
(II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Microsoft  Microsoft Basic Optical Mouse v2.0  (/dev/input/event6)
(**) Microsoft  Microsoft Basic Optical Mouse v2.0 : Applying InputClass "evdev pointer catchall"
(**) Microsoft  Microsoft Basic Optical Mouse v2.0 : always reports core events
(**) Microsoft  Microsoft Basic Optical Mouse v2.0 : Device: "/dev/input/event6"
(II) Microsoft  Microsoft Basic Optical Mouse v2.0 : Found 3 mouse buttons
(II) Microsoft  Microsoft Basic Optical Mouse v2.0 : Found scroll wheel(s)
(II) Microsoft  Microsoft Basic Optical Mouse v2.0 : Found relative axes
(II) Microsoft  Microsoft Basic Optical Mouse v2.0 : Found x and y relative axes
(II) Microsoft  Microsoft Basic Optical Mouse v2.0 : Configuring as mouse
(**) Microsoft  Microsoft Basic Optical Mouse v2.0 : YAxisMapping: buttons 4 and 5
(**) Microsoft  Microsoft Basic Optical Mouse v2.0 : EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Microsoft  Microsoft Basic Optical Mouse v2.0 " (type: MOUSE)
(II) Microsoft  Microsoft Basic Optical Mouse v2.0 : initialized for relative axes.
(II) config/udev: Adding input device Microsoft  Microsoft Basic Optical Mouse v2.0  (/dev/input/mouse2)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Digital PCBeep (/dev/input/event7)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "se"
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event2)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)
(WW) Open ACPI failed (/var/run/acpid.socket) (Connection refused)
(II) Macintosh mouse button emulation: Close
(II) UnloadModule: "evdev"
(II) AT Translated Set 2 keyboard: Close
(II) UnloadModule: "evdev"
(II) Microsoft  Microsoft Basic Optical Mouse v2.0 : Close
(II) UnloadModule: "evdev"
(II) Logitech USB Receiver: Close
(II) UnloadModule: "evdev"
(II) Logitech USB Receiver: Close
(II) UnloadModule: "evdev"
(II) Power Button: Close
(II) UnloadModule: "evdev"
(II) Power Button: Close
(II) UnloadModule: "evdev"
 ddxSigGiveUp: Closing log

____________________________________________

/var/log/Xorg.1.log

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux kvant 2.6.32-24-generic #42-Ubuntu SMP Fri Aug 20 14:21:58 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=904eae1e-3da9-44ba-a36f-ba4094c10c8e ro quiet splash
Build Date: 21 July 2010  01:03:39PM
xorg-server 2:1.7.6-2ubuntu7.3 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.16.4
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Thu Sep  9 02:16:05 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
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
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x7ca300
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(--) using VT number 8

(--) PCI:*(0:2:0:0) 10de:0ca3:1462:2072 nVidia Corporation GT215 [GeForce GT 240] rev 162, Mem @ 0xfd000000/16777216, 0xc0000000/268435456, 0xdc000000/33554432, I/O @ 0x0000cc00/128, BIOS @ 0x????????/524288
(II) Open ACPI successful (/var/run/acpid.socket)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/extra-modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  195.36.24  Thu Apr 22 19:52:00 PDT 2010
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  195.36.24  Thu Apr 22 19:18:54 PDT 2010
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 02@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules/libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "TwinView" "1"
(**) NVIDIA(0): Option "MetaModes" "CRT: nvidia-auto-select +0+0, DFP: nvidia-auto-select +1280+0"
(**) NVIDIA(0): Option "TwinViewXineramaInfoOrder" "DFP-0"
(**) Sep 09 02:16:05 NVIDIA(0): Enabling RENDER acceleration
(II) Sep 09 02:16:05 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Sep 09 02:16:05 NVIDIA(0):     enabled.
(EE) Sep 09 02:16:05 NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the
(EE) Sep 09 02:16:05 NVIDIA(0):     system's kernel log for additional error messages and
(EE) Sep 09 02:16:05 NVIDIA(0):     consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.1.log" for additional information.

 ddxSigGiveUp: Closing log

____________________________________________

/var/log/Xorg.1.log.old

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux kvant 2.6.32-24-generic #42-Ubuntu SMP Fri Aug 20 14:21:58 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=904eae1e-3da9-44ba-a36f-ba4094c10c8e ro quiet splash
Build Date: 21 July 2010  01:03:39PM
xorg-server 2:1.7.6-2ubuntu7.3 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.16.4
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Wed Sep  8 18:54:10 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
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
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x7ca300
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(--) using VT number 8

(--) PCI:*(0:2:0:0) 10de:0ca3:1462:2072 nVidia Corporation GT215 [GeForce GT 240] rev 162, Mem @ 0xfd000000/16777216, 0xc0000000/268435456, 0xdc000000/33554432, I/O @ 0x0000cc00/128, BIOS @ 0x????????/524288
(II) Open ACPI successful (/var/run/acpid.socket)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/extra-modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  195.36.24  Thu Apr 22 19:52:00 PDT 2010
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  195.36.24  Thu Apr 22 19:18:54 PDT 2010
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 02@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules/libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "TwinView" "1"
(**) NVIDIA(0): Option "MetaModes" "CRT: nvidia-auto-select +0+0, DFP: nvidia-auto-select +1280+0"
(**) NVIDIA(0): Option "TwinViewXineramaInfoOrder" "DFP-0"
(**) Sep 08 18:54:10 NVIDIA(0): Enabling RENDER acceleration
(II) Sep 08 18:54:10 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Sep 08 18:54:10 NVIDIA(0):     enabled.
(EE) Sep 08 18:54:10 NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the
(EE) Sep 08 18:54:10 NVIDIA(0):     system's kernel log for additional error messages and
(EE) Sep 08 18:54:10 NVIDIA(0):     consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.1.log" for additional information.

 ddxSigGiveUp: Closing log

____________________________________________

/var/log/Xorg.2.log

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux kvant 2.6.32-24-generic #42-Ubuntu SMP Fri Aug 20 14:21:58 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=904eae1e-3da9-44ba-a36f-ba4094c10c8e ro quiet splash
Build Date: 21 July 2010  01:03:39PM
xorg-server 2:1.7.6-2ubuntu7.3 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.16.4
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.2.log", Time: Thu Sep  9 02:16:05 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
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
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x7ca300
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(--) using VT number 8

(--) PCI:*(0:2:0:0) 10de:0ca3:1462:2072 nVidia Corporation GT215 [GeForce GT 240] rev 162, Mem @ 0xfd000000/16777216, 0xc0000000/268435456, 0xdc000000/33554432, I/O @ 0x0000cc00/128, BIOS @ 0x????????/524288
(II) Open ACPI successful (/var/run/acpid.socket)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/extra-modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  195.36.24  Thu Apr 22 19:52:00 PDT 2010
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  195.36.24  Thu Apr 22 19:18:54 PDT 2010
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 02@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules/libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "TwinView" "1"
(**) NVIDIA(0): Option "MetaModes" "CRT: nvidia-auto-select +0+0, DFP: nvidia-auto-select +1280+0"
(**) NVIDIA(0): Option "TwinViewXineramaInfoOrder" "DFP-0"
(**) Sep 09 02:16:05 NVIDIA(0): Enabling RENDER acceleration
(II) Sep 09 02:16:05 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Sep 09 02:16:05 NVIDIA(0):     enabled.
(EE) Sep 09 02:16:05 NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the
(EE) Sep 09 02:16:05 NVIDIA(0):     system's kernel log for additional error messages and
(EE) Sep 09 02:16:05 NVIDIA(0):     consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.2.log" for additional information.

 ddxSigGiveUp: Closing log

____________________________________________

/var/log/Xorg.2.log.old

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux kvant 2.6.32-24-generic #42-Ubuntu SMP Fri Aug 20 14:21:58 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=904eae1e-3da9-44ba-a36f-ba4094c10c8e ro quiet splash
Build Date: 21 July 2010  01:03:39PM
xorg-server 2:1.7.6-2ubuntu7.3 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.16.4
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.2.log", Time: Wed Sep  8 18:54:10 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
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
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x7ca300
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(--) using VT number 8

(--) PCI:*(0:2:0:0) 10de:0ca3:1462:2072 nVidia Corporation GT215 [GeForce GT 240] rev 162, Mem @ 0xfd000000/16777216, 0xc0000000/268435456, 0xdc000000/33554432, I/O @ 0x0000cc00/128, BIOS @ 0x????????/524288
(II) Open ACPI successful (/var/run/acpid.socket)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/extra-modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  195.36.24  Thu Apr 22 19:52:00 PDT 2010
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  195.36.24  Thu Apr 22 19:18:54 PDT 2010
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 02@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules/libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "TwinView" "1"
(**) NVIDIA(0): Option "MetaModes" "CRT: nvidia-auto-select +0+0, DFP: nvidia-auto-select +1280+0"
(**) NVIDIA(0): Option "TwinViewXineramaInfoOrder" "DFP-0"
(**) Sep 08 18:54:10 NVIDIA(0): Enabling RENDER acceleration
(II) Sep 08 18:54:10 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Sep 08 18:54:10 NVIDIA(0):     enabled.
(EE) Sep 08 18:54:10 NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the
(EE) Sep 08 18:54:10 NVIDIA(0):     system's kernel log for additional error messages and
(EE) Sep 08 18:54:10 NVIDIA(0):     consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.2.log" for additional information.

 ddxSigGiveUp: Closing log

____________________________________________

/var/log/Xorg.3.log

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux kvant 2.6.32-24-generic #42-Ubuntu SMP Fri Aug 20 14:21:58 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=904eae1e-3da9-44ba-a36f-ba4094c10c8e ro quiet splash
Build Date: 21 July 2010  01:03:39PM
xorg-server 2:1.7.6-2ubuntu7.3 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.16.4
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.3.log", Time: Thu Sep  9 02:16:05 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
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
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x7ca300
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(--) using VT number 8

(--) PCI:*(0:2:0:0) 10de:0ca3:1462:2072 nVidia Corporation GT215 [GeForce GT 240] rev 162, Mem @ 0xfd000000/16777216, 0xc0000000/268435456, 0xdc000000/33554432, I/O @ 0x0000cc00/128, BIOS @ 0x????????/524288
(II) Open ACPI successful (/var/run/acpid.socket)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/extra-modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  195.36.24  Thu Apr 22 19:52:00 PDT 2010
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  195.36.24  Thu Apr 22 19:18:54 PDT 2010
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 02@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules/libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "TwinView" "1"
(**) NVIDIA(0): Option "MetaModes" "CRT: nvidia-auto-select +0+0, DFP: nvidia-auto-select +1280+0"
(**) NVIDIA(0): Option "TwinViewXineramaInfoOrder" "DFP-0"
(**) Sep 09 02:16:05 NVIDIA(0): Enabling RENDER acceleration
(II) Sep 09 02:16:05 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Sep 09 02:16:05 NVIDIA(0):     enabled.
(EE) Sep 09 02:16:05 NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the
(EE) Sep 09 02:16:05 NVIDIA(0):     system's kernel log for additional error messages and
(EE) Sep 09 02:16:05 NVIDIA(0):     consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.3.log" for additional information.

 ddxSigGiveUp: Closing log

____________________________________________

/var/log/Xorg.3.log.old

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux kvant 2.6.32-24-generic #42-Ubuntu SMP Fri Aug 20 14:21:58 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=904eae1e-3da9-44ba-a36f-ba4094c10c8e ro quiet splash
Build Date: 21 July 2010  01:03:39PM
xorg-server 2:1.7.6-2ubuntu7.3 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.16.4
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.3.log", Time: Wed Sep  8 18:54:10 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
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
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x7ca300
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(--) using VT number 8

(--) PCI:*(0:2:0:0) 10de:0ca3:1462:2072 nVidia Corporation GT215 [GeForce GT 240] rev 162, Mem @ 0xfd000000/16777216, 0xc0000000/268435456, 0xdc000000/33554432, I/O @ 0x0000cc00/128, BIOS @ 0x????????/524288
(II) Open ACPI successful (/var/run/acpid.socket)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/extra-modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  195.36.24  Thu Apr 22 19:52:00 PDT 2010
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  195.36.24  Thu Apr 22 19:18:54 PDT 2010
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 02@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules/libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "TwinView" "1"
(**) NVIDIA(0): Option "MetaModes" "CRT: nvidia-auto-select +0+0, DFP: nvidia-auto-select +1280+0"
(**) NVIDIA(0): Option "TwinViewXineramaInfoOrder" "DFP-0"
(**) Sep 08 18:54:11 NVIDIA(0): Enabling RENDER acceleration
(II) Sep 08 18:54:11 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Sep 08 18:54:11 NVIDIA(0):     enabled.
(EE) Sep 08 18:54:11 NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the
(EE) Sep 08 18:54:11 NVIDIA(0):     system's kernel log for additional error messages and
(EE) Sep 08 18:54:11 NVIDIA(0):     consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.3.log" for additional information.

 ddxSigGiveUp: Closing log

____________________________________________

/var/log/Xorg.4.log

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux kvant 2.6.32-24-generic #42-Ubuntu SMP Fri Aug 20 14:21:58 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=904eae1e-3da9-44ba-a36f-ba4094c10c8e ro quiet splash
Build Date: 21 July 2010  01:03:39PM
xorg-server 2:1.7.6-2ubuntu7.3 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.16.4
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.4.log", Time: Thu Sep  9 02:16:06 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
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
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x7ca300
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(--) using VT number 8

(--) PCI:*(0:2:0:0) 10de:0ca3:1462:2072 nVidia Corporation GT215 [GeForce GT 240] rev 162, Mem @ 0xfd000000/16777216, 0xc0000000/268435456, 0xdc000000/33554432, I/O @ 0x0000cc00/128, BIOS @ 0x????????/524288
(II) Open ACPI successful (/var/run/acpid.socket)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/extra-modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  195.36.24  Thu Apr 22 19:52:00 PDT 2010
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  195.36.24  Thu Apr 22 19:18:54 PDT 2010
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 02@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules/libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "TwinView" "1"
(**) NVIDIA(0): Option "MetaModes" "CRT: nvidia-auto-select +0+0, DFP: nvidia-auto-select +1280+0"
(**) NVIDIA(0): Option "TwinViewXineramaInfoOrder" "DFP-0"
(**) Sep 09 02:16:06 NVIDIA(0): Enabling RENDER acceleration
(II) Sep 09 02:16:06 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Sep 09 02:16:06 NVIDIA(0):     enabled.
(EE) Sep 09 02:16:06 NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the
(EE) Sep 09 02:16:06 NVIDIA(0):     system's kernel log for additional error messages and
(EE) Sep 09 02:16:06 NVIDIA(0):     consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.4.log" for additional information.

 ddxSigGiveUp: Closing log

____________________________________________

/var/log/Xorg.4.log.old

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux kvant 2.6.32-24-generic #42-Ubuntu SMP Fri Aug 20 14:21:58 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=904eae1e-3da9-44ba-a36f-ba4094c10c8e ro quiet splash
Build Date: 21 July 2010  01:03:39PM
xorg-server 2:1.7.6-2ubuntu7.3 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.16.4
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.4.log", Time: Wed Sep  8 18:54:11 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
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
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x7ca300
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(--) using VT number 8

(--) PCI:*(0:2:0:0) 10de:0ca3:1462:2072 nVidia Corporation GT215 [GeForce GT 240] rev 162, Mem @ 0xfd000000/16777216, 0xc0000000/268435456, 0xdc000000/33554432, I/O @ 0x0000cc00/128, BIOS @ 0x????????/524288
(II) Open ACPI successful (/var/run/acpid.socket)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/extra-modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  195.36.24  Thu Apr 22 19:52:00 PDT 2010
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  195.36.24  Thu Apr 22 19:18:54 PDT 2010
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 02@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules/libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "TwinView" "1"
(**) NVIDIA(0): Option "MetaModes" "CRT: nvidia-auto-select +0+0, DFP: nvidia-auto-select +1280+0"
(**) NVIDIA(0): Option "TwinViewXineramaInfoOrder" "DFP-0"
(**) Sep 08 18:54:11 NVIDIA(0): Enabling RENDER acceleration
(II) Sep 08 18:54:11 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Sep 08 18:54:11 NVIDIA(0):     enabled.
(EE) Sep 08 18:54:11 NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the
(EE) Sep 08 18:54:11 NVIDIA(0):     system's kernel log for additional error messages and
(EE) Sep 08 18:54:11 NVIDIA(0):     consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.4.log" for additional information.

 ddxSigGiveUp: Closing log

____________________________________________

/var/log/Xorg.5.log

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux kvant 2.6.32-24-generic #42-Ubuntu SMP Fri Aug 20 14:21:58 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=904eae1e-3da9-44ba-a36f-ba4094c10c8e ro quiet splash
Build Date: 21 July 2010  01:03:39PM
xorg-server 2:1.7.6-2ubuntu7.3 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.16.4
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.5.log", Time: Thu Sep  9 02:16:06 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
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
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x7ca300
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(--) using VT number 8

(--) PCI:*(0:2:0:0) 10de:0ca3:1462:2072 nVidia Corporation GT215 [GeForce GT 240] rev 162, Mem @ 0xfd000000/16777216, 0xc0000000/268435456, 0xdc000000/33554432, I/O @ 0x0000cc00/128, BIOS @ 0x????????/524288
(II) Open ACPI successful (/var/run/acpid.socket)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/extra-modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  195.36.24  Thu Apr 22 19:52:00 PDT 2010
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  195.36.24  Thu Apr 22 19:18:54 PDT 2010
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 02@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules/libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "TwinView" "1"
(**) NVIDIA(0): Option "MetaModes" "CRT: nvidia-auto-select +0+0, DFP: nvidia-auto-select +1280+0"
(**) NVIDIA(0): Option "TwinViewXineramaInfoOrder" "DFP-0"
(**) Sep 09 02:16:06 NVIDIA(0): Enabling RENDER acceleration
(II) Sep 09 02:16:06 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Sep 09 02:16:06 NVIDIA(0):     enabled.
(EE) Sep 09 02:16:06 NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the
(EE) Sep 09 02:16:06 NVIDIA(0):     system's kernel log for additional error messages and
(EE) Sep 09 02:16:06 NVIDIA(0):     consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.5.log" for additional information.

 ddxSigGiveUp: Closing log

____________________________________________

/var/log/Xorg.5.log.old

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux kvant 2.6.32-24-generic #42-Ubuntu SMP Fri Aug 20 14:21:58 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=904eae1e-3da9-44ba-a36f-ba4094c10c8e ro quiet splash
Build Date: 21 July 2010  01:03:39PM
xorg-server 2:1.7.6-2ubuntu7.3 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.16.4
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.5.log", Time: Wed Sep  8 18:54:11 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
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
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x7ca300
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(--) using VT number 8

(--) PCI:*(0:2:0:0) 10de:0ca3:1462:2072 nVidia Corporation GT215 [GeForce GT 240] rev 162, Mem @ 0xfd000000/16777216, 0xc0000000/268435456, 0xdc000000/33554432, I/O @ 0x0000cc00/128, BIOS @ 0x????????/524288
(II) Open ACPI successful (/var/run/acpid.socket)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/extra-modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  195.36.24  Thu Apr 22 19:52:00 PDT 2010
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  195.36.24  Thu Apr 22 19:18:54 PDT 2010
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 02@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules/libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "TwinView" "1"
(**) NVIDIA(0): Option "MetaModes" "CRT: nvidia-auto-select +0+0, DFP: nvidia-auto-select +1280+0"
(**) NVIDIA(0): Option "TwinViewXineramaInfoOrder" "DFP-0"
(**) Sep 08 18:54:11 NVIDIA(0): Enabling RENDER acceleration
(II) Sep 08 18:54:11 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Sep 08 18:54:11 NVIDIA(0):     enabled.
(EE) Sep 08 18:54:11 NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the
(EE) Sep 08 18:54:11 NVIDIA(0):     system's kernel log for additional error messages and
(EE) Sep 08 18:54:11 NVIDIA(0):     consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.5.log" for additional information.

 ddxSigGiveUp: Closing log

____________________________________________

Skipping ldd output (glxinfo not found)

____________________________________________

/usr/bin/lspci -d "10de:*" -v -xxx

02:00.0 VGA compatible controller: nVidia Corporation GT215 [GeForce GT 240] (rev a2)
    Subsystem: Micro-Star International Co., Ltd. Device 2072
    Flags: bus master, fast devsel, latency 0, IRQ 24
    Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Memory at dc000000 (64-bit, prefetchable) [size=32M]
    I/O ports at cc00 [size=128]
    [virtual] Expansion ROM at fe980000 [disabled] [size=512K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [78] Express Endpoint, MSI 00
    Capabilities: [b4] Vendor Specific Information <?>
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [128] Power Budgeting <?>
    Capabilities: [600] Vendor Specific Information <?>
    Kernel driver in use: nvidia
    Kernel modules: nvidia-current, nvidiafb, nouveau
00: de 10 a3 0c 07 00 10 00 a2 00 00 03 00 00 80 00
10: 00 00 00 fd 0c 00 00 c0 00 00 00 00 0c 00 00 dc
20: 00 00 00 00 01 cc 00 00 00 00 00 00 62 14 72 20
30: 00 00 00 00 60 00 00 00 00 00 00 00 0a 01 00 00
40: 62 14 72 20 00 00 00 00 00 00 00 00 00 00 00 00
50: 01 00 00 00 01 00 00 00 ce d6 23 00 00 00 00 00
60: 01 68 03 00 08 00 00 00 05 78 80 00 00 00 00 00
70: 00 00 00 00 00 00 00 00 10 b4 02 00 e0 8d 2c 01
80: 10 29 00 00 01 4d 05 00 08 01 41 10 00 00 00 00
90: 00 00 00 00 00 00 00 00 00 00 00 00 10 00 00 00
a0: 00 00 00 00 00 00 00 00 01 00 00 00 00 00 00 00
b0: 00 00 00 00 09 00 14 01 00 00 00 00 00 00 00 00
c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

02:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
    Subsystem: Micro-Star International Co., Ltd. Device 2072
    Flags: bus master, fast devsel, latency 0, IRQ 25
    Memory at fe97c000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [78] Express Endpoint, MSI 00
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
00: de 10 e4 0b 06 01 10 00 a1 00 03 04 08 00 80 00
10: 00 c0 97 fe 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 62 14 72 20
30: 00 00 00 00 60 00 00 00 00 00 00 00 0a 02 00 00
40: 62 14 72 20 00 00 00 00 00 00 00 00 00 00 00 00
50: 00 00 00 00 00 00 00 00 ce d6 23 00 00 00 00 00
60: 01 68 03 00 08 00 00 00 05 78 80 00 00 00 00 00
70: 00 00 00 00 00 00 00 00 10 00 02 00 a0 8d 2c 01
80: 10 29 00 00 01 4d 04 00 0b 01 41 10 00 00 00 00
90: 00 00 00 00 00 00 00 00 00 00 00 00 10 00 00 00
a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00


____________________________________________

/usr/bin/lspci -t

-+-[0000:80]---01.0
 \-[0000:00]-+-00.0
             +-00.1
             +-00.2
             +-00.3
             +-00.4
             +-00.5
             +-00.7
             +-01.0-[0000:01]--
             +-02.0-[0000:02]--+-00.0
             |                 \-00.1
             +-0f.0
             +-0f.1
             +-10.0
             +-10.1
             +-10.2
             +-10.3
             +-10.4
             +-11.0
             +-11.7
             +-12.0
             \-13.0

____________________________________________

/usr/sbin/lsusb

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 045e:00cb Microsoft Corp. Basic Optical Mouse v2.0
Bus 002 Device 002: ID 046d:c529 Logitech, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

____________________________________________

/usr/sbin/dmidecode

# dmidecode 2.9
SMBIOS 2.4 present.
24 structures occupying 1194 bytes.
Table at 0x000FB1C0.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
    Vendor: American Megatrends Inc.
    Version: P1.70
    Release Date: 04/24/2007
    Address: 0xF0000
    Runtime Size: 64 kB
    ROM Size: 512 kB
    Characteristics:
        PCI is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        Boot from CD is supported
        Selectable boot is supported
        BIOS ROM is socketed
        EDD is supported
        5.25"/1.2 MB floppy services are supported (int 13h)
        3.5"/720 KB floppy services are supported (int 13h)
        3.5"/2.88 MB floppy services are supported (int 13h)
        Print screen service is supported (int 5h)
        8042 keyboard services are supported (int 9h)
        Serial services are supported (int 14h)
        Printer services are supported (int 17h)
        CGA/mono video services are supported (int 10h)
        ACPI is supported
        USB legacy is supported
        LS-120 boot is supported
        ATAPI Zip drive boot is supported
        BIOS boot specification is supported
        Function key-initiated network boot is supported
        Targeted content distribution is supported
    BIOS Revision: 8.12

Handle 0x0001, DMI type 1, 27 bytes
System Information
    Manufacturer: To Be Filled By O.E.M.
    Product Name: To Be Filled By O.E.M.
    Version: To Be Filled By O.E.M.
    Serial Number: To Be Filled By O.E.M.
    UUID: 00020003-0004-0005-0006-000700080009
    Wake-up Type: Power Switch
    SKU Number: To Be Filled By O.E.M.
    Family: To Be Filled By O.E.M.

Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
    Manufacturer:                       
    Product Name: 4CoreDual-VSTA
    Version:                       
    Serial Number:                       
    Asset Tag:                       
    Features:
        Board is a hosting board
        Board is replaceable
    Location In Chassis:                       
    Chassis Handle: 0x0003
    Type: Motherboard
    Contained Object Handles: 0

Handle 0x0003, DMI type 3, 21 bytes
Chassis Information
    Manufacturer: To Be Filled By O.E.M.
    Type: Desktop
    Lock: Not Present
    Version: To Be Filled By O.E.M.
    Serial Number: To Be Filled By O.E.M.
    Asset Tag: To Be Filled By O.E.M.
    Boot-up State: Safe
    Power Supply State: Safe
    Thermal State: Safe
    Security Status: None
    OEM Information: 0x00000000
    Height: Unspecified
    Number Of Power Cords: 1
    Contained Elements: 0

Handle 0x0004, DMI type 4, 35 bytes
Processor Information
    Socket Designation: CPUSocket
    Type: Central Processor
    Family: Pentium 4
    Manufacturer: Intel            
    ID: 7A 06 01 00 FF FB EB BF
    Signature: Type 0, Family 6, Model 23, Stepping 10
    Flags:
        FPU (Floating-point unit on-chip)
        VME (Virtual mode extension)
        DE (Debugging extension)
        PSE (Page size extension)
        TSC (Time stamp counter)
        MSR (Model specific registers)
        PAE (Physical address extension)
        MCE (Machine check exception)
        CX8 (CMPXCHG8 instruction supported)
        APIC (On-chip APIC hardware supported)
        SEP (Fast system call)
        MTRR (Memory type range registers)
        PGE (Page global enable)
        MCA (Machine check architecture)
        CMOV (Conditional move instruction supported)
        PAT (Page attribute table)
        PSE-36 (36-bit page size extension)
        CLFSH (CLFLUSH instruction supported)
        DS (Debug store)
        ACPI (ACPI supported)
        MMX (MMX technology supported)
        FXSR (Fast floating-point save and restore)
        SSE (Streaming SIMD extensions)
        SSE2 (Streaming SIMD extensions 2)
        SS (Self-snoop)
        HTT (Hyper-threading technology)
        TM (Thermal monitor supported)
        PBE (Pending break enabled)
    Version: Intel(R) Core(TM)2 CPU         E7400  @ 2.80GHz     
    Voltage: 1.1 V
    External Clock: 266 MHz
    Max Speed: 2666 MHz
    Current Speed: 12694 MHz
    Status: Populated, Enabled
    Upgrade: Other
    L1 Cache Handle: 0x0005
    L2 Cache Handle: 0x0006
    L3 Cache Handle: 0x0007
    Serial Number: To Be Filled By O.E.M.
    Asset Tag: To Be Filled By O.E.M.
    Part Number: To Be Filled By O.E.M.

Handle 0x0005, DMI type 7, 19 bytes
Cache Information
    Socket Designation: L1-Cache
    Configuration: Enabled, Not Socketed, Level 1
    Operational Mode: Write Back
    Location: Internal
    Installed Size: 64 KB
    Maximum Size: 64 KB
    Supported SRAM Types:
        Other
    Installed SRAM Type: Other
    Speed: Unknown
    Error Correction Type: Parity
    System Type: Data
    Associativity: 4-way Set-associative

Handle 0x0006, DMI type 7, 19 bytes
Cache Information
    Socket Designation: L2-Cache
    Configuration: Enabled, Not Socketed, Level 2
    Operational Mode: Write Back
    Location: Internal
    Installed Size: 3072 KB
    Maximum Size: 3072 KB
    Supported SRAM Types:
        Other
    Installed SRAM Type: Other
    Speed: Unknown
    Error Correction Type: Single-bit ECC
    System Type: Unified
    Associativity: 4-way Set-associative

Handle 0x0007, DMI type 7, 19 bytes
Cache Information
    Socket Designation: L3-Cache
    Configuration: Disabled, Not Socketed, Level 3
    Operational Mode: Unknown
    Location: Internal
    Installed Size: 0 KB
    Maximum Size: 0 KB
    Supported SRAM Types:
        Unknown
    Installed SRAM Type: Unknown
    Speed: Unknown
    Error Correction Type: Unknown
    System Type: Unknown
    Associativity: Unknown

Handle 0x0008, DMI type 5, 20 bytes
Memory Controller Information
    Error Detecting Method: 64-bit ECC
    Error Correcting Capabilities:
        None
    Supported Interleave: One-way Interleave
    Current Interleave: One-way Interleave
    Maximum Memory Module Size: 2048 MB
    Maximum Total Memory Size: 4096 MB
    Supported Speeds:
        70 ns
        60 ns
    Supported Memory Types:
        DIMM
        SDRAM
    Memory Module Voltage: 3.3 V
    Associated Memory Slots: 2
        0x0009
        0x000A
    Enabled Error Correcting Capabilities:
        None

Handle 0x0009, DMI type 6, 12 bytes
Memory Module Information
    Socket Designation: DIMM0
    Bank Connections: 1 0
    Current Speed: Unknown
    Type: SDRAM
    Installed Size: 512 MB (Single-bank Connection)
    Enabled Size: 512 MB (Single-bank Connection)
    Error Status: OK

Handle 0x000A, DMI type 6, 12 bytes
Memory Module Information
    Socket Designation: DIMM1
    Bank Connections: 3 2
    Current Speed: Unknown
    Type: SDRAM
    Installed Size: 2048 MB (Double-bank Connection)
    Enabled Size: 2048 MB (Double-bank Connection)
    Error Status: OK

Handle 0x000B, DMI type 9, 13 bytes
System Slot Information
    Designation: PCI1
    Type: 32-bit PCI
    Current Usage: Available
    Length: Short
    ID: 1
    Characteristics:
        3.3 V is provided
        Opening is shared
        PME signal is supported

Handle 0x000C, DMI type 9, 13 bytes
System Slot Information
    Designation: PCI2
    Type: 32-bit PCI
    Current Usage: Available
    Length: Short
    ID: 2
    Characteristics:
        3.3 V is provided
        Opening is shared
        PME signal is supported

Handle 0x000D, DMI type 9, 13 bytes
System Slot Information
    Designation: PCI3
    Type: 32-bit PCI
    Current Usage: Available
    Length: Short
    ID: 3
    Characteristics:
        3.3 V is provided
        Opening is shared
        PME signal is supported

Handle 0x000E, DMI type 9, 13 bytes
System Slot Information
    Designation: PCI4
    Type: 32-bit PCI
    Current Usage: Available
    Length: Short
    ID: 4
    Characteristics:
        3.3 V is provided
        Opening is shared
        PME signal is supported

Handle 0x000F, DMI type 9, 13 bytes
System Slot Information
    Designation: PCIE1
    Type: x16 PCI Express
    Current Usage: In Use
    Length: Short
    ID: 17
    Characteristics:
        3.3 V is provided
        Opening is shared
        PME signal is supported

Handle 0x0010, DMI type 16, 15 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: None
    Maximum Capacity: 4 GB
    Error Information Handle: Not Provided
    Number Of Devices: 2

Handle 0x0011, DMI type 19, 15 bytes
Memory Array Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x0009FFFFFFF
    Range Size: 2560 MB
    Physical Array Handle: 0x0010
    Partition Width: 0

Handle 0x0012, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0010
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 512 MB
    Form Factor: DIMM
    Set: None
    Locator: DIMM0
    Bank Locator: BANK0
    Type: SDRAM
    Type Detail: Synchronous
    Speed: Unknown
    Manufacturer: Manufacturer0
    Serial Number: SerNum0
    Asset Tag: AssetTagNum0
    Part Number: PartNum0

Handle 0x0013, DMI type 20, 19 bytes
Memory Device Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x0001FFFFFFF
    Range Size: 512 MB
    Physical Device Handle: 0x0012
    Memory Array Mapped Address Handle: 0x0011
    Partition Row Position: 1
    Interleaved Data Depth: 1

Handle 0x0014, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0010
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 2048 MB
    Form Factor: DIMM
    Set: None
    Locator: DIMM1
    Bank Locator: BANK1
    Type: SDRAM
    Type Detail: Synchronous
    Speed: Unknown
    Manufacturer: Manufacturer1
    Serial Number: SerNum1
    Asset Tag: AssetTagNum1
    Part Number: PartNum1

Handle 0x0015, DMI type 20, 19 bytes
Memory Device Mapped Address
    Starting Address: 0x00020000000
    Ending Address: 0x0009FFFFFFF
    Range Size: 2 GB
    Physical Device Handle: 0x0014
    Memory Array Mapped Address Handle: 0x0011
    Partition Row Position: 1
    Interleaved Data Depth: 1

Handle 0x0016, DMI type 32, 20 bytes
System Boot Information
    Status: No errors detected

Handle 0x0017, DMI type 127, 4 bytes
End Of Table


____________________________________________

/sbin/modinfo nvidia | grep vermagic


____________________________________________

Scanning kernel log files for NVRM messages:

  /var/log/messages:
Sep  8 12:46:14 kvant kernel: [  308.294091] NVRM: The NVIDIA probe routine was not called for 1 device(s).
Sep  8 12:46:14 kvant kernel: [  308.294096] NVRM: This can occur when a driver such as rivafb, nvidiafb or
Sep  8 12:46:14 kvant kernel: [  308.294097] NVRM: rivatv was loaded and obtained ownership of the NVIDIA
Sep  8 12:46:14 kvant kernel: [  308.294099] NVRM: device(s).
Sep  8 12:46:14 kvant kernel: [  308.294102] NVRM: Try unloading the rivafb, nvidiafb or rivatv kernel module
Sep  8 12:46:14 kvant kernel: [  308.294103] NVRM: (and/or reconfigure your kernel without rivafb/nvidiafb
Sep  8 12:46:14 kvant kernel: [  308.294104] NVRM: support), then try loading the NVIDIA kernel module again.
Sep  8 12:46:14 kvant kernel: [  308.294107] NVRM: No NVIDIA graphics adapter probed!
Sep  8 12:47:51 kvant kernel: [    7.254577] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  195.36.24  Thu Apr 22 19:10:14 PDT 2010
Sep  8 12:52:37 kvant kernel: [   15.010427] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  195.36.24  Thu Apr 22 19:10:14 PDT 2010
Sep  8 13:15:20 kvant kernel: [   15.400368] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  195.36.24  Thu Apr 22 19:10:14 PDT 2010
Sep  8 13:28:22 kvant kernel: [   10.980192] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  195.36.24  Thu Apr 22 19:10:14 PDT 2010
Sep  8 13:34:18 kvant kernel: [   17.771424] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  195.36.24  Thu Apr 22 19:10:14 PDT 2010
Sep  8 13:38:16 kvant kernel: [   17.581410] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  195.36.24  Thu Apr 22 19:10:14 PDT 2010
Sep  8 13:43:24 kvant kernel: [   17.521451] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  195.36.24  Thu Apr 22 19:10:14 PDT 2010
Sep  8 13:48:50 kvant kernel: [   17.671404] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  195.36.24  Thu Apr 22 19:10:14 PDT 2010
Sep  8 14:01:48 kvant kernel: [   17.511658] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  195.36.24  Thu Apr 22 19:10:14 PDT 2010
Sep  8 15:50:45 kvant kernel: [    9.381569] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  195.36.24  Thu Apr 22 19:10:14 PDT 2010
Sep  8 16:26:28 kvant kernel: [   12.419432] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  195.36.24  Thu Apr 22 19:10:14 PDT 2010
Sep  8 18:33:30 kvant kernel: [   18.921911] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  195.36.24  Thu Apr 22 19:10:14 PDT 2010
Sep  8 18:54:14 kvant kernel: [   16.440420] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  195.36.24  Thu Apr 22 19:10:14 PDT 2010
Sep  9 02:16:09 kvant kernel: [   16.280370] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  195.36.24  Thu Apr 22 19:10:14 PDT 2010
Sep  9 14:36:15 kvant kernel: [    9.648263] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  195.36.24  Thu Apr 22 19:10:14 PDT 2010
/var/log/kernel.log is not readable

____________________________________________

dmesg:

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-24-generic (buildd@crested) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #42-Ubuntu SMP Fri Aug 20 14:21:58 UTC 2010 (Ubuntu 2.6.32-24.42-generic 2.6.32.15+drm33.5)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=904eae1e-3da9-44ba-a36f-ba4094c10c8e ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e6000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000009ffb0000 (usable)
[    0.000000]  BIOS-e820: 000000009ffb0000 - 000000009ffc0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000009ffc0000 - 000000009fff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000009fff0000 - 00000000a0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x9ffb0 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-DFFFF uncachable
[    0.000000]   E0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FE0000000 write-back
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e6000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000009ffb0000 (usable)
[    0.000000]  modified: 000000009ffb0000 - 000000009ffc0000 (ACPI data)
[    0.000000]  modified: 000000009ffc0000 - 000000009fff0000 (ACPI NVS)
[    0.000000]  modified: 000000009fff0000 - 00000000a0000000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ff780000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-000000009ffb0000
[    0.000000] Warning: NX (Execute Disable) protection missing in CPU or disabled in BIOS!
[    0.000000]  0000000000 - 009fe00000 page 2M
[    0.000000]  009fe00000 - 009ffb0000 page 4k
[    0.000000] kernel direct mapping tables up to 9ffb0000 @ 10000-15000
[    0.000000] RAMDISK: 37286000 - 37fefb91
[    0.000000] ACPI: RSDP 00000000000f7e10 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 000000009ffb0000 00034 (v01 A M I  OEMRSDT  04000724 MSFT 00000097)
[    0.000000] ACPI: FACP 000000009ffb0200 00084 (v02 A M I  OEMFACP  04000724 MSFT 00000097)
[    0.000000] ACPI: DSDT 000000009ffb0450 04AED (v01  4CDVT 4CDVT161 00000161 INTL 02002026)
[    0.000000] ACPI: FACS 000000009ffc0000 00040
[    0.000000] ACPI: APIC 000000009ffb0390 00078 (v01 A M I  OEMAPIC  04000724 MSFT 00000097)
[    0.000000] ACPI: MCFG 000000009ffb0410 0003C (v01 A M I  OEMMCFG  04000724 MSFT 00000097)
[    0.000000] ACPI: OEMB 000000009ffc0040 00051 (v01 A M I  AMI_OEM  04000724 MSFT 00000097)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000009ffb0000
[    0.000000] Bootmem setup node 0 0000000000000000-000000009ffb0000
[    0.000000]   NODE_DATA [0000000000013000 - 0000000000017fff]
[    0.000000]   bootmap [0000000000018000 -  000000000002bff7] pages 14
[    0.000000] (7 early reservations) ==> bootmem [0000000000 - 009ffb0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0001000000 - 0001a2fe64]    TEXT DATA BSS ==> [0001000000 - 0001a2fe64]
[    0.000000]   #3 [0037286000 - 0037fefb91]          RAMDISK ==> [0037286000 - 0037fefb91]
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #5 [0001a30000 - 0001a3012b]              BRK ==> [0001a30000 - 0001a3012b]
[    0.000000]   #6 [0000010000 - 0000013000]          PGTABLE ==> [0000010000 - 0000013000]
[    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
[    0.000000]  [ffffea0000000000-ffffea00023fffff] PMD -> [ffff880002000000-ffff8800043fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00100000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0009ffb0
[    0.000000] On node 0 totalpages: 655167
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 102 pages reserved
[    0.000000]   DMA zone: 3825 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 8903 pages used for memmap
[    0.000000]   DMA32 zone: 642281 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IOAPIC (id[0x03] address[0xfecc0000] gsi_base[24])
[    0.000000] IOAPIC[1]: apic_id 3, version 3, address 0xfecc0000, GSI 24-47
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 48
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e6000
[    0.000000] PM: Registered nosave memory: 00000000000e6000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at a0000000 (gap: a0000000:5ee00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001c00000 s91544 r8192 d23144 u524288
[    0.000000] pcpu-alloc: s91544 r8192 d23144 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 646106
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=904eae1e-3da9-44ba-a36f-ba4094c10c8e ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
[    0.000000] Checking aperture...
[    0.000000] AGP bridge at 00:00:00
[    0.000000] Aperture from AGP @ f8000000 old size 32 MB
[    0.000000] Aperture from AGP @ f8000000 size 64 MB (APSIZE f30)
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 2558932k/2621120k available (5422k kernel code, 452k absent, 61736k reserved, 2979k data, 880k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:4352 nr_irqs:848
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 26214400 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2802.338 MHz processor.
[    0.020011] Calibrating delay loop (skipped), value calculated using timer frequency.. 5604.67 BogoMIPS (lpj=28023380)
[    0.020054] Security Framework initialized
[    0.020086] AppArmor: AppArmor initialized
[    0.020619] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.031488] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.033298] Mount-cache hash table entries: 256
[    0.033522] Initializing cgroup subsys ns
[    0.033530] Initializing cgroup subsys cpuacct
[    0.033535] Initializing cgroup subsys memory
[    0.033546] Initializing cgroup subsys devices
[    0.033549] Initializing cgroup subsys freezer
[    0.033552] Initializing cgroup subsys net_cls
[    0.033581] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.033584] CPU: L2 cache: 3072K
[    0.033589] CPU 0/0x0 -> Node 0
[    0.033591] CPU: Physical Processor ID: 0
[    0.033593] CPU: Processor Core ID: 0
[    0.033598] mce: CPU supports 6 MCE banks
[    0.033610] CPU0: Thermal monitoring enabled (TM1)
[    0.033618] using mwait in idle threads.
[    0.033620] Performance Events: Core2 events, Intel PMU driver.
[    0.033629] ... version:                2
[    0.033631] ... bit width:              40
[    0.033633] ... generic registers:      2
[    0.033635] ... value mask:             000000ffffffffff
[    0.033637] ... max period:             000000007fffffff
[    0.033639] ... fixed-purpose events:   3
[    0.033641] ... event mask:             0000000700000003
[    0.037152] ACPI: Core revision 20090903
[    0.044600] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.044607] ftrace: allocating 22527 entries in 89 pages
[    0.050070] Setting APIC routing to flat
[    0.050556] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.158154] CPU0: Intel(R) Core(TM)2 CPU         E7400  @ 2.80GHz stepping 0a
[    0.160000] Booting processor 1 APIC 0x1 ip 0x6000
[    0.030000] Initializing CPU#1
[    0.030000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.030000] CPU: L2 cache: 3072K
[    0.030000] CPU 1/0x1 -> Node 0
[    0.030000] CPU: Physical Processor ID: 0
[    0.030000] CPU: Processor Core ID: 1
[    0.030000] CPU1: Thermal monitoring enabled (TM1)
[    0.310132] CPU1: Intel(R) Core(TM)2 CPU         E7400  @ 2.80GHz stepping 0a
[    0.310142] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.320025] Brought up 2 CPUs
[    0.320028] Total of 2 processors activated (11209.65 BogoMIPS).
[    0.320816] CPU0 attaching sched-domain:
[    0.320821]  domain 0: span 0-1 level MC
[    0.320824]   groups: 0 1
[    0.320832] CPU1 attaching sched-domain:
[    0.320834]  domain 0: span 0-1 level MC
[    0.320837]   groups: 1 0
[    0.320952] devtmpfs: initialized
[    0.320952] regulator: core version 0.5
[    0.320952] Time: 14:36:06  Date: 09/09/10
[    0.320952] NET: Registered protocol family 16
[    0.320952] Trying to unpack rootfs image as initramfs...
[    0.320952] ACPI: bus type pci registered
[    0.320952] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.320952] PCI: Not using MMCONFIG.
[    0.320952] PCI: Using configuration type 1 for base access
[    0.330131] bio: create slab <bio-0> at 0
[    0.330971] ACPI: EC: Look up EC in DSDT
[    0.334582] ACPI: Executed 1 blocks of module-level executable AML code
[    0.338969] ACPI: Interpreter enabled
[    0.338976] ACPI: (supports S0 S1 S4 S5)
[    0.339002] ACPI: Using IOAPIC for interrupt routing
[    0.339064] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.344470] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.348157] PCI: Using MMCONFIG at e0000000 - efffffff
[    0.356759] ACPI Warning: Incorrect checksum in table [OEMB] - 46, should be 39 (20090903/tbutils-314)
[    0.356894] ACPI: No dock devices found.
[    0.357256] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.357323] pci 0000:00:00.0: reg 10 32bit mmio pref: [0xf8000000-0xfbffffff]
[    0.357901] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.357906] pci 0000:00:02.0: PME# disabled
[    0.357974] pci 0000:00:0f.0: reg 10 io port: [0xe000-0xe007]
[    0.357983] pci 0000:00:0f.0: reg 14 io port: [0xdc00-0xdc03]
[    0.357991] pci 0000:00:0f.0: reg 18 io port: [0xd880-0xd887]
[    0.358000] pci 0000:00:0f.0: reg 1c io port: [0xd800-0xd803]
[    0.358008] pci 0000:00:0f.0: reg 20 io port: [0xd480-0xd48f]
[    0.358017] pci 0000:00:0f.0: reg 24 io port: [0xd000-0xd0ff]
[    0.358111] pci 0000:00:0f.1: reg 20 io port: [0xfc00-0xfc0f]
[    0.358216] pci 0000:00:10.0: reg 20 io port: [0xe080-0xe09f]
[    0.358250] pci 0000:00:10.0: supports D1 D2
[    0.358252] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.358257] pci 0000:00:10.0: PME# disabled
[    0.358321] pci 0000:00:10.1: reg 20 io port: [0xe400-0xe41f]
[    0.358354] pci 0000:00:10.1: supports D1 D2
[    0.358356] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.358361] pci 0000:00:10.1: PME# disabled
[    0.358422] pci 0000:00:10.2: reg 20 io port: [0xe480-0xe49f]
[    0.358455] pci 0000:00:10.2: supports D1 D2
[    0.358458] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.358463] pci 0000:00:10.2: PME# disabled
[    0.358524] pci 0000:00:10.3: reg 20 io port: [0xec00-0xec1f]
[    0.358557] pci 0000:00:10.3: supports D1 D2
[    0.358559] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.358565] pci 0000:00:10.3: PME# disabled
[    0.358607] pci 0000:00:10.4: reg 10 32bit mmio: [0xfebff800-0xfebff8ff]
[    0.358662] pci 0000:00:10.4: supports D1 D2
[    0.358664] pci 0000:00:10.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.358670] pci 0000:00:10.4: PME# disabled
[    0.358893] pci 0000:00:12.0: reg 10 io port: [0xe800-0xe8ff]
[    0.358902] pci 0000:00:12.0: reg 14 32bit mmio: [0xfebffc00-0xfebffcff]
[    0.358952] pci 0000:00:12.0: supports D1 D2
[    0.358955] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.358960] pci 0000:00:12.0: PME# disabled
[    0.359125] pci 0000:00:01.0: bridge 32bit mmio: [0xfc700000-0xfc7fffff]
[    0.359172] pci 0000:02:00.0: reg 10 32bit mmio: [0xfd000000-0xfdffffff]
[    0.359185] pci 0000:02:00.0: reg 14 64bit mmio pref: [0xc0000000-0xcfffffff]
[    0.359200] pci 0000:02:00.0: reg 1c 64bit mmio pref: [0xdc000000-0xddffffff]
[    0.359209] pci 0000:02:00.0: reg 24 io port: [0xcc00-0xcc7f]
[    0.359218] pci 0000:02:00.0: reg 30 32bit mmio pref: [0xfe980000-0xfe9fffff]
[    0.359306] pci 0000:02:00.1: reg 10 32bit mmio: [0xfe97c000-0xfe97ffff]
[    0.359438] pci 0000:00:02.0: bridge io port: [0xc000-0xcfff]
[    0.359443] pci 0000:00:02.0: bridge 32bit mmio: [0xfc800000-0xfe9fffff]
[    0.359448] pci 0000:00:02.0: bridge 32bit mmio pref: [0xbbf00000-0xdfefffff]
[    0.359466] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.359713] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NBPG._PRT]
[    0.359832] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7._PRT]
[    0.374062] ACPI: PCI Root Bridge [PCI1] (0000:80)
[    0.374148] pci 0000:80:01.0: reg 10 64bit mmio: [0xfeafc000-0xfeafffff]
[    0.374203] pci 0000:80:01.0: PME# supported from D0 D3hot D3cold
[    0.374209] pci 0000:80:01.0: PME# disabled
[    0.374275] ACPI: PCI Interrupt Routing Table [\_SB_.PCI1._PRT]
[    0.374495] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.374625] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.374750] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.374875] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.374999] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.375130] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.375256] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.375381] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.375531] vgaarb: device added: PCI:0000:02:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.375536] vgaarb: loaded
[    0.375677] SCSI subsystem initialized
[    0.375798] libata version 3.00 loaded.
[    0.375891] usbcore: registered new interface driver usbfs
[    0.375906] usbcore: registered new interface driver hub
[    0.375941] usbcore: registered new device driver usb
[    0.376112] ACPI: WMI: Mapper loaded
[    0.376114] PCI: Using ACPI for IRQ routing
[    0.376336] NetLabel: Initializing
[    0.376338] NetLabel:  domain hash size = 128
[    0.376340] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.376359] NetLabel:  unlabeled traffic allowed by default
[    0.376421] Switching to clocksource tsc
[    0.376606] AppArmor: AppArmor Filesystem Enabled
[    0.376606] pnp: PnP ACPI init
[    0.376606] ACPI: bus type pnp registered
[    0.377623] pnp: PnP ACPI: found 14 devices
[    0.377626] ACPI: ACPI bus type pnp unregistered
[    0.377643] system 00:07: ioport range 0x295-0x296 has been reserved
[    0.377647] system 00:07: ioport range 0x3e0-0x3e7 has been reserved
[    0.377650] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
[    0.377654] system 00:07: ioport range 0x800-0x87f has been reserved
[    0.377657] system 00:07: ioport range 0x400-0x41f has been reserved
[    0.377661] system 00:07: iomem range 0xfeafc000-0xfeafffff has been reserved
[    0.377665] system 00:07: iomem range 0xffb80000-0xffbfffff has been reserved
[    0.377673] system 00:08: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.377676] system 00:08: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.377684] system 00:0b: iomem range 0xe0000000-0xefffffff has been reserved
[    0.377691] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[    0.377694] system 00:0c: iomem range 0xc0000-0xcffff has been reserved
[    0.377698] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
[    0.377702] system 00:0c: iomem range 0x100000-0x9fffffff could not be reserved
[    0.377705] system 00:0c: iomem range 0xfff80000-0xffffffff has been reserved
[    0.382464] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.382467] pci 0000:00:01.0:   IO window: disabled
[    0.382473] pci 0000:00:01.0:   MEM window: 0xfc700000-0xfc7fffff
[    0.382478] pci 0000:00:01.0:   PREFETCH window: disabled
[    0.382486] pci 0000:00:02.0: PCI bridge, secondary bus 0000:02
[    0.382490] pci 0000:00:02.0:   IO window: 0xc000-0xcfff
[    0.382496] pci 0000:00:02.0:   MEM window: 0xfc800000-0xfe9fffff
[    0.382502] pci 0000:00:02.0:   PREFETCH window: 0xbbf00000-0xdfefffff
[    0.382523] pci 0000:00:01.0: setting latency timer to 64
[    0.382538]   alloc irq_desc for 27 on node -1
[    0.382540]   alloc kstat_irqs on node -1
[    0.382547] pci 0000:00:02.0: PCI INT A -> GSI 27 (level, low) -> IRQ 27
[    0.382552] pci 0000:00:02.0: setting latency timer to 64
[    0.382559] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.382562] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.382565] pci_bus 0000:01: resource 1 mem: [0xfc700000-0xfc7fffff]
[    0.382569] pci_bus 0000:02: resource 0 io:  [0xc000-0xcfff]
[    0.382571] pci_bus 0000:02: resource 1 mem: [0xfc800000-0xfe9fffff]
[    0.382575] pci_bus 0000:02: resource 2 pref mem [0xbbf00000-0xdfefffff]
[    0.382578] pci_bus 0000:80: resource 0 io:  [0x00-0xffff]
[    0.382581] pci_bus 0000:80: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.382631] NET: Registered protocol family 2
[    0.382859] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.384486] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.392297] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.393319] TCP: Hash tables configured (established 524288 bind 65536)
[    0.393322] TCP reno registered
[    0.393568] NET: Registered protocol family 1
[    0.393615] pci 0000:00:01.0: disabling DAC on VIA PCI bridge
[    0.393733] pci 0000:02:00.0: Boot video device
[    0.394059] Scanning for low memory corruption every 60 seconds
[    0.394252] audit: initializing netlink socket (disabled)
[    0.394268] type=2000 audit(1284042966.393:1): initialized
[    0.406713] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.408521] VFS: Disk quotas dquot_6.5.2
[    0.408602] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.409348] fuse init (API version 7.13)
[    0.409457] msgmni has been set to 4997
[    0.409710] alg: No test for stdrng (krng)
[    0.409777] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.409781] io scheduler noop registered
[    0.409783] io scheduler anticipatory registered
[    0.409786] io scheduler deadline registered
[    0.409828] io scheduler cfq registered (default)
[    0.410041]   alloc irq_desc for 48 on node -1
[    0.410043]   alloc kstat_irqs on node -1
[    0.410057] pcieport 0000:00:02.0: irq 48 for MSI/MSI-X
[    0.410068] pcieport 0000:00:02.0: setting latency timer to 64
[    0.410448] aer 0000:00:02.0:pcie02: service driver aer loaded
[    0.410460] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.410472] Firmware did not grant requested _OSC control
[    0.410507] Firmware did not grant requested _OSC control
[    0.410524] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.410677] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.410682] ACPI: Power Button [PWRB]
[    0.410738] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.410742] ACPI: Power Button [PWRF]
[    0.411467] processor LNXCPU:00: registered as cooling_device0
[    0.411791] processor LNXCPU:01: registered as cooling_device1
[    0.417390] Linux agpgart interface v0.103
[    0.417436] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.417544] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.417962] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.419262] brd: module loaded
[    0.419871] loop: module loaded
[    0.419978] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.420157]   alloc irq_desc for 21 on node -1
[    0.420160]   alloc kstat_irqs on node -1
[    0.420169] pata_acpi 0000:00:0f.0: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.420215] pata_acpi 0000:00:0f.0: PCI INT B disabled
[    0.420619] Fixed MDIO Bus: probed
[    0.420662] PPP generic driver version 2.4.2
[    0.420700] tun: Universal TUN/TAP device driver, 1.6
[    0.420702] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.420808] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.420830] ehci_hcd 0000:00:10.4: PCI INT C -> GSI 21 (level, low) -> IRQ 21
[    0.420852] ehci_hcd 0000:00:10.4: EHCI Host Controller
[    0.420894] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 1
[    0.420943] ehci_hcd 0000:00:10.4: irq 21, io mem 0xfebff800
[    0.433439] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00
[    0.433583] usb usb1: configuration #1 chosen from 1 choice
[    0.433620] hub 1-0:1.0: USB hub found
[    0.433632] hub 1-0:1.0: 8 ports detected
[    0.433708] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.433728] uhci_hcd: USB Universal Host Controller Interface driver
[    0.433777]   alloc irq_desc for 20 on node -1
[    0.433779]   alloc kstat_irqs on node -1
[    0.433786] uhci_hcd 0000:00:10.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.433796] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    0.433835] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
[    0.433871] uhci_hcd 0000:00:10.0: irq 20, io base 0x0000e080
[    0.433984] usb usb2: configuration #1 chosen from 1 choice
[    0.434014] hub 2-0:1.0: USB hub found
[    0.434021] hub 2-0:1.0: 2 ports detected
[    0.434077]   alloc irq_desc for 22 on node -1
[    0.434079]   alloc kstat_irqs on node -1
[    0.434085] uhci_hcd 0000:00:10.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    0.434092] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    0.434128] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
[    0.434158] uhci_hcd 0000:00:10.1: irq 22, io base 0x0000e400
[    0.434269] usb usb3: configuration #1 chosen from 1 choice
[    0.434298] hub 3-0:1.0: USB hub found
[    0.434305] hub 3-0:1.0: 2 ports detected
[    0.434361] uhci_hcd 0000:00:10.2: PCI INT C -> GSI 21 (level, low) -> IRQ 21
[    0.434368] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    0.434403] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
[    0.434426] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000e480
[    0.434523] usb usb4: configuration #1 chosen from 1 choice
[    0.434557] hub 4-0:1.0: USB hub found
[    0.434564] hub 4-0:1.0: 2 ports detected
[    0.434614]   alloc irq_desc for 23 on node -1
[    0.434617]   alloc kstat_irqs on node -1
[    0.434621] uhci_hcd 0000:00:10.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.434628] uhci_hcd 0000:00:10.3: UHCI Host Controller
[    0.434683] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 5
[    0.434714] uhci_hcd 0000:00:10.3: irq 23, io base 0x0000ec00
[    0.434812] usb usb5: configuration #1 chosen from 1 choice
[    0.434846] hub 5-0:1.0: USB hub found
[    0.434853] hub 5-0:1.0: 2 ports detected
[    0.434958] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    0.434961] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    0.435112] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.435254] mice: PS/2 mouse device common for all mice
[    0.435384] rtc_cmos 00:02: RTC can wake from S4
[    0.435443] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.435482] rtc0: alarms up to one year, y3k, 114 bytes nvram
[    0.435634] device-mapper: uevent: version 1.0.3
[    0.435771] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    0.435861] device-mapper: multipath: version 1.1.0 loaded
[    0.435865] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.436044] cpuidle: using governor ladder
[    0.436046] cpuidle: using governor menu
[    0.436490] TCP cubic registered
[    0.436650] NET: Registered protocol family 10
[    0.437231] lo: Disabled Privacy Extensions
[    0.437587] NET: Registered protocol family 17
[    0.437727] PM: Resume from disk failed.
[    0.437744] registered taskstats version 1
[    0.438210]   Magic number: 10:758:636
[    0.438325] rtc_cmos 00:02: setting system clock to 2010-09-09 14:36:06 UTC (1284042966)
[    0.438329] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.438331] EDD information not available.
[    0.454933] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.704520] Freeing initrd memory: 13734k freed
[    0.711929] Freeing unused kernel memory: 880k freed
[    0.712425] Write protecting the kernel read-only data: 7696k
[    0.731650] udev: starting version 151
[    0.771866] agpgart: Detected VIA PT880 Ultra chipset
[    0.788364] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[    0.809946] vga16fb: initializing
[    0.809950] vga16fb: mapped to 0xffff8800000a0000
[    0.810025] fb0: VGA16 VGA frame buffer device
[    0.835145] agpgart-via 0000:00:00.0: AGP aperture is 64M @ 0xf8000000
[    0.835191] via-rhine 0000:00:12.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.835949] eth0: VIA Rhine II at 0xfebffc00, 00:19:66:22:a8:d9, IRQ 23.
[    0.836659] eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 45e1.
[    0.837093] sata_via 0000:00:0f.0: version 2.4
[    0.837104] sata_via 0000:00:0f.0: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.837135] sata_via 0000:00:0f.0: routed to hard irq line 5
[    0.850740] scsi0 : sata_via
[    0.859930] Floppy drive(s): fd0 is 1.44M
[    0.861094] scsi1 : sata_via
[    0.862997] ata1: SATA max UDMA/133 cmd 0xe000 ctl 0xdc00 bmdma 0xd480 irq 21
[    0.863001] ata2: SATA max UDMA/133 cmd 0xd880 ctl 0xd800 bmdma 0xd488 irq 21
[    0.863234] pata_via 0000:00:0f.1: version 0.3.4
[    0.863429] scsi2 : pata_via
[    0.863591] scsi3 : pata_via
[    0.865675] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
[    0.865678] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
[    0.877969] FDC 0 is a post-1991 82077
[    1.063461] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.093463] usb 2-1: new full speed USB device using uhci_hcd and address 2
[    1.108971] Console: switching to colour frame buffer device 80x30
[    1.243849] ata1.00: ATA-8: Hitachi HDS721010CLA332, JP4OA39C, max UDMA/133
[    1.243853] ata1.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.283591] usb 2-1: configuration #1 chosen from 1 choice
[    1.284072] ata1.00: configured for UDMA/133
[    1.284191] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HDS72101 JP4O PQ: 0 ANSI: 5
[    1.284351] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.284465] sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.284525] sd 0:0:0:0: [sda] Write Protect is off
[    1.284529] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.284560] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.284729]  sda: sda1 sda2 <
[    1.300215] usbcore: registered new interface driver hiddev
[    1.303255] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:10.0/usb2/2-1/2-1:1.0/input/input4
[    1.303348] generic-usb 0003:046D:C529.0001: input,hidraw0: USB HID v1.11 Keyboard [Logitech USB Receiver] on usb-0000:00:10.0-1/input0
[    1.307774] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:10.0/usb2/2-1/2-1:1.1/input/input5
[    1.307995] generic-usb 0003:046D:C529.0002: input,hiddev96,hidraw1: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:10.0-1/input1
[    1.308023] usbcore: registered new interface driver usbhid
[    1.308026] usbhid: v2.6:USB HID core driver
[    1.310718]  sda5 >
[    1.311058] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.500011] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.570011] usb 2-2: new low speed USB device using uhci_hcd and address 3
[    1.680314] ata2.00: ATA-7: SAMSUNG HD161HJ, JF100-19, max UDMA7
[    1.680318] ata2.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.700323] ata2.00: configured for UDMA/133
[    1.700424] scsi 1:0:0:0: Direct-Access     ATA      SAMSUNG HD161HJ  JF10 PQ: 0 ANSI: 5
[    1.700576] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    1.700604] sd 1:0:0:0: [sdb] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.700797] sd 1:0:0:0: [sdb] Write Protect is off
[    1.700800] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.700831] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.700992]  sdb: sdb1
[    1.708990] sd 1:0:0:0: [sdb] Attached SCSI disk
[    1.751029] usb 2-2: configuration #1 chosen from 1 choice
[    1.777264] input: Microsoft  Microsoft Basic Optical Mouse v2.0  as /devices/pci0000:00/0000:00:10.0/usb2/2-2/2-2:1.0/input/input6
[    1.777366] generic-usb 0003:045E:00CB.0003: input,hidraw2: USB HID v1.11 Mouse [Microsoft  Microsoft Basic Optical Mouse v2.0 ] on usb-0000:00:10.0-2/input0
[    1.890405] ata4.01: ATAPI: _NEC DVD_RW ND-3520A, 1.04, max UDMA/33
[    1.930285] ata4.01: configured for UDMA/33
[    1.932121] scsi 3:0:1:0: CD-ROM            _NEC     DVD_RW ND-3520A  1.04 PQ: 0 ANSI: 5
[    1.935157] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    1.935161] Uniform CD-ROM driver Revision: 3.20
[    1.935274] sr 3:0:1:0: Attached scsi CD-ROM sr0
[    1.935340] sr 3:0:1:0: Attached scsi generic sg2 type 5
[    2.493018] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    2.493024] EXT4-fs (sda1): write access will be enabled during recovery
[    4.067119] EXT4-fs (sda1): recovery complete
[    4.067839] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    6.149367] Adding 7537656k swap on /dev/sda5.  Priority:-1 extents:1 across:7537656k 
[    6.308057] udev: starting version 151
[    7.448103] type=1505 audit(1284035773.502:2):  operation="profile_load" pid=631 name="/sbin/dhclient3"
[    7.448934] type=1505 audit(1284035773.502:3):  operation="profile_load" pid=631 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[    7.449378] type=1505 audit(1284035773.502:4):  operation="profile_load" pid=631 name="/usr/lib/connman/scripts/dhclient-script"
[    8.265221] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    8.887411] nvidia: module license 'NVIDIA' taints kernel.
[    8.887416] Disabling lock debugging due to kernel taint
[    9.409295] parport_pc 00:06: reported by Plug and Play ACPI
[    9.409404] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[    9.417586] lp: driver loaded but no devices found
[    9.491956] lp0: using parport0 (interrupt-driven).
[    9.647830]   alloc irq_desc for 24 on node -1
[    9.647834]   alloc kstat_irqs on node -1
[    9.647844] nvidia 0000:02:00.0: PCI INT A -> GSI 24 (level, low) -> IRQ 24
[    9.647854] nvidia 0000:02:00.0: setting latency timer to 64
[    9.647861] vgaarb: device changed decodes: PCI:0000:02:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[    9.648263] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  195.36.24  Thu Apr 22 19:10:14 PDT 2010
[    9.759279] ppdev: user-space parallel port driver
[   10.600696] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   10.912865] type=1505 audit(1284035776.971:5):  operation="profile_load" pid=945 name="/usr/share/gdm/guest-session/Xsession"
[   10.917855] type=1505 audit(1284035776.971:6):  operation="profile_replace" pid=955 name="/sbin/dhclient3"
[   10.918700] type=1505 audit(1284035776.971:7):  operation="profile_replace" pid=955 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   10.919159] type=1505 audit(1284035776.971:8):  operation="profile_replace" pid=955 name="/usr/lib/connman/scripts/dhclient-script"
[   11.325300]   alloc irq_desc for 25 on node -1
[   11.325304]   alloc kstat_irqs on node -1
[   11.325313] HDA Intel 0000:02:00.1: PCI INT B -> GSI 25 (level, low) -> IRQ 25
[   11.325446] hda_intel: Disable MSI for Nvidia chipset
[   11.325483] HDA Intel 0000:02:00.1: setting latency timer to 64
[   11.325488] HDA Intel 0000:02:00.1: PCI: Disallowing DAC for device
[   11.366079] type=1505 audit(1284035777.421:9):  operation="profile_load" pid=956 name="/usr/bin/evince"
[   11.376911] type=1505 audit(1284035777.431:10):  operation="profile_load" pid=956 name="/usr/bin/evince-previewer"
[   11.383678] type=1505 audit(1284035777.441:11):  operation="profile_load" pid=956 name="/usr/bin/evince-thumbnailer"
[   11.400087] hda-intel: spurious response 0x0:0x0, last cmd=0x0f0000
[   12.420010] hda-intel: azx_get_response timeout, switching to polling mode: last cmd=0x100f0000
[   12.971744] __ratelimit: 9 callbacks suppressed
[   12.971748] do_IRQ: 0.84 No irq handler for vector (irq -1)
[   12.971751] do_IRQ: 0.84 No irq handler for vector (irq -1)
[   13.450018] hda-intel: Codec #1 probe error; disabling it...
[   13.530115] hda-intel: spurious response 0x0:0x0, last cmd=0x0f0000
[   14.540032] hda-intel: Codec #2 probe error; disabling it...
[   15.630039] hda-intel: Codec #3 probe error; disabling it...
[   16.750010] hda_intel: azx_get_response timeout, switching to single_cmd mode: last cmd=0x000f0001
[   16.789516]   alloc irq_desc for 17 on node -1
[   16.789520]   alloc kstat_irqs on node -1
[   16.789529] HDA Intel 0000:80:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   16.789575] HDA Intel 0000:80:01.0: setting latency timer to 64
[   16.789580] HDA Intel 0000:80:01.0: PCI: Disallowing DAC for device
[   16.911046] CPU0 attaching NULL sched-domain.
[   16.911053] CPU1 attaching NULL sched-domain.
[   16.980087] CPU0 attaching sched-domain:
[   16.980092]  domain 0: span 0-1 level MC
[   16.980095]   groups: 0 1
[   16.980102] CPU1 attaching sched-domain:
[   16.980105]  domain 0: span 0-1 level MC
[   16.980108]   groups: 1 0
[   16.985272] hda_codec: ALC888: BIOS auto-probing.
[   16.986671] input: HDA Digital PCBeep as /devices/pci0000:80/0000:80:01.0/input/input7
[   19.108394] CPU0 attaching NULL sched-domain.
[   19.108400] CPU1 attaching NULL sched-domain.
[   19.160082] CPU0 attaching sched-domain:
[   19.160087]  domain 0: span 0-1 level MC
[   19.160090]   groups: 0 1
[   19.160096] CPU1 attaching sched-domain:
[   19.160099]  domain 0: span 0-1 level MC
[   19.160102]   groups: 1 0
[   21.480006] eth0: no IPv6 routers present
[   22.744648] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   28.814689] Intel AES-NI instructions are not detected.
[   28.853868] padlock: VIA PadLock not detected.
____________________________________________

Using built-in specs.
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.4.3-4ubuntu5' --with-bugurl=file:///usr/share/doc/gcc-4.4/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --enable-shared --enable-multiarch --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.4 --program-suffix=-4.4 --enable-nls --enable-clocale=gnu --enable-libstdcxx-debug --enable-plugin --enable-objc-gc --disable-werror --with-arch-32=i486 --with-tune=generic --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) 
____________________________________________

xset -q:

Keyboard Control:
  auto repeat:  on    key click percent:  0    LED mask:  00000000
  XKB indicators:
    00: Caps Lock:   off    01: Num Lock:    off    02: Scroll Lock: off
    03: Compose:     off    04: Kana:        off    05: Sleep:       off
    06: Suspend:     off    07: Mute:        off    08: Misc:        off
    09: Mail:        off    10: Charging:    off    11: Shift Lock:  off
    12: Group 2:     off    13: Mouse Keys:  off
  auto repeat delay:  500    repeat rate:  30
  auto repeating keys:  00ffffffdffffbbf
                        fadfffefffedffff
                        9fffffffffffffff
                        fff7ffffffffffff
  bell percent:  0    bell pitch:  400    bell duration:  100
Pointer Control:
  acceleration:  2/1    threshold:  4
Screen Saver:
  prefer blanking:  yes    allow exposures:  yes
  timeout:  600    cycle:  600
Colors:
  default colormap:  0x20    BlackPixel:  0    WhitePixel:  16777215
Font Path:
  /usr/share/fonts/X11/misc,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:unscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,built-ins
DPMS (Energy Star):
  Standby: 0    Suspend: 0    Off: 0
  DPMS is Enabled
  Monitor is On
____________________________________________

nvidia-settings -q all:


Attributes queryable via kvant:0.0:

  Attribute 'OperatingSystem' (kvant:0.0): 0.
    The valid values for 'OperatingSystem' are in the range 0 - 2
    (inclusive).
    'OperatingSystem' is a read-only attribute.
    'OperatingSystem' can use the following target types: X Screen, GPU.

  Attribute 'NvidiaDriverVersion' (kvant:0.0): 195.36.24 
    'NvidiaDriverVersion' is a string attribute.
    'NvidiaDriverVersion' is a read-only attribute.
    'NvidiaDriverVersion' can use the following target types: X Screen,
    GPU.

  Attribute 'NvControlVersion' (kvant:0.0): 1.22 
    'NvControlVersion' is a string attribute.
    'NvControlVersion' is a read-only attribute.
    'NvControlVersion' can use the following target types: X Screen.

  Attribute 'GLXServerVersion' (kvant:0.0): 1.4 
    'GLXServerVersion' is a string attribute.
    'GLXServerVersion' is a read-only attribute.
    'GLXServerVersion' can use the following target types: X Screen.

  Attribute 'GLXClientVersion' (kvant:0.0): 1.4 
    'GLXClientVersion' is a string attribute.
    'GLXClientVersion' is a read-only attribute.
    'GLXClientVersion' can use the following target types: X Screen.

  Attribute 'OpenGLVersion' (kvant:0.0): 3.2.0 NVIDIA 195.36.24 
    'OpenGLVersion' is a string attribute.
    'OpenGLVersion' is a read-only attribute.
    'OpenGLVersion' can use the following target types: X Screen.

  Attribute 'XRandRVersion' (kvant:0.0): 1.3 
    'XRandRVersion' is a string attribute.
    'XRandRVersion' is a read-only attribute.
    'XRandRVersion' can use the following target types: X Screen.

  Attribute 'XF86VidModeVersion' (kvant:0.0): 2.2 
    'XF86VidModeVersion' is a string attribute.
    'XF86VidModeVersion' is a read-only attribute.
    'XF86VidModeVersion' can use the following target types: X Screen.

  Attribute 'XvVersion' (kvant:0.0): 2.2 
    'XvVersion' is a string attribute.
    'XvVersion' is a read-only attribute.
    'XvVersion' can use the following target types: X Screen.

  Attribute 'TwinView' (kvant:0.0): 1.
    'TwinView' is a boolean attribute; valid values are: 1 (on/true) and 0
    (off/false).
    'TwinView' is a read-only attribute.
    'TwinView' can use the following target types: X Screen.

  Attribute 'ConnectedDisplays' (kvant:0.0): 0x00010002.
    'ConnectedDisplays' is a bitmask attribute.
    'ConnectedDisplays' is a read-only attribute.
    'ConnectedDisplays' can use the following target types: X Screen, GPU.

  Attribute 'EnabledDisplays' (kvant:0.0): 0x00010002.
    'EnabledDisplays' is a bitmask attribute.
    'EnabledDisplays' is a read-only attribute.
    'EnabledDisplays' can use the following target types: X Screen, GPU.

  Attribute 'CursorShadow' (kvant:0.0): 0.
    'CursorShadow' is a boolean attribute; valid values are: 1 (on/true)
    and 0 (off/false).
    'CursorShadow' can use the following target types: X Screen.

  Attribute 'CursorShadowAlpha' (kvant:0.0): 64.
    The valid values for 'CursorShadowAlpha' are in the range 0 - 254
    (inclusive).
    'CursorShadowAlpha' can use the following target types: X Screen.

  Attribute 'CursorShadowRed' (kvant:0.0): 0.
    The valid values for 'CursorShadowRed' are in the range 0 - 255
    (inclusive).
    'CursorShadowRed' can use the following target types: X Screen.

  Attribute 'CursorShadowGreen' (kvant:0.0): 0.
    The valid values for 'CursorShadowGreen' are in the range 0 - 255
    (inclusive).
    'CursorShadowGreen' can use the following target types: X Screen.

  Attribute 'CursorShadowBlue' (kvant:0.0): 0.
    The valid values for 'CursorShadowBlue' are in the range 0 - 255
    (inclusive).
    'CursorShadowBlue' can use the following target types: X Screen.

  Attribute 'CursorShadowXOffset' (kvant:0.0): 4.
    The valid values for 'CursorShadowXOffset' are in the range 0 - 32
    (inclusive).
    'CursorShadowXOffset' can use the following target types: X Screen.

  Attribute 'CursorShadowYOffset' (kvant:0.0): 2.
    The valid values for 'CursorShadowYOffset' are in the range 0 - 32
    (inclusive).
    'CursorShadowYOffset' can use the following target types: X Screen.

  Attribute 'AssociatedDisplays' (kvant:0.0): 0x00010002.
    'AssociatedDisplays' is a bitmask attribute.
    'AssociatedDisplays' can use the following target types: X Screen.

  Attribute 'InitialPixmapPlacement' (kvant:0.0): 2.
    The valid values for 'InitialPixmapPlacement' are in the range 0 - 4
    (inclusive).
    'InitialPixmapPlacement' can use the following target types: X Screen.

  Attribute 'DynamicTwinview' (kvant:0.0): 1.
    'DynamicTwinview' is an integer attribute.
    'DynamicTwinview' is a read-only attribute.
    'DynamicTwinview' can use the following target types: X Screen.

  Attribute 'MultiGpuDisplayOwner' (kvant:0.0): 0.
    'MultiGpuDisplayOwner' is an integer attribute.
    'MultiGpuDisplayOwner' is a read-only attribute.
    'MultiGpuDisplayOwner' can use the following target types: X Screen.

  Attribute 'GlyphCache' (kvant:0.0): 1.
    The valid values for 'GlyphCache' are in the range 0 - 1 (inclusive).
    'GlyphCache' can use the following target types: X Screen.

  Attribute 'Depth30Allowed' (kvant:0.0): 0.
    'Depth30Allowed' is a boolean attribute; valid values are: 1 (on/true)
    and 0 (off/false).
    'Depth30Allowed' is a read-only attribute.
    'Depth30Allowed' can use the following target types: X Screen, GPU.

  Attribute 'NoScanout' (kvant:0.0): 0.
    'NoScanout' is a boolean attribute; valid values are: 1 (on/true) and 0
    (off/false).
    'NoScanout' is a read-only attribute.
    'NoScanout' can use the following target types: X Screen, GPU.

  Attribute 'XServerUniqueId' (kvant:0.0): -1243641724.
    'XServerUniqueId' is a read-only attribute.
    'XServerUniqueId' can use the following target types: X Screen.

  Attribute 'PixmapCache' (kvant:0.0): 1.
    'PixmapCache' is a boolean attribute; valid values are: 1 (on/true) and
    0 (off/false).
    'PixmapCache' can use the following target types: X Screen.

  Attribute 'PixmapCacheRoundSizeKB' (kvant:0.0): 1024.
    The valid values for 'PixmapCacheRoundSizeKB' are in the range 4 -
    1048576 (inclusive).
    'PixmapCacheRoundSizeKB' can use the following target types: X Screen.

  Attribute 'AccelerateTrapezoids' (kvant:0.0): 0.
    'AccelerateTrapezoids' is a boolean attribute; valid values are: 1
    (on/true) and 0 (off/false).
    'AccelerateTrapezoids' can use the following target types: X Screen.

  Attribute 'SyncToVBlank' (kvant:0.0): 0.
    'SyncToVBlank' is a boolean attribute; valid values are: 1 (on/true)
    and 0 (off/false).
    'SyncToVBlank' can use the following target types: X Screen.

  Attribute 'LogAniso' (kvant:0.0): 0.
    The valid values for 'LogAniso' are in the range 0 - 4 (inclusive).
    'LogAniso' can use the following target types: X Screen.

  Attribute 'FSAA' (kvant:0.0): 0.
    Valid values for 'FSAA' are: 0, 1, 5, 7, 8, 9, 10 and 12.
    'FSAA' can use the following target types: X Screen.

  Attribute 'TextureSharpen' (kvant:0.0): 0.
    'TextureSharpen' is a boolean attribute; valid values are: 1 (on/true)
    and 0 (off/false).
    'TextureSharpen' can use the following target types: X Screen.

  Attribute 'AllowFlipping' (kvant:0.0): 1.
    'AllowFlipping' is a boolean attribute; valid values are: 1 (on/true)
    and 0 (off/false).
    'AllowFlipping' can use the following target types: X Screen.

  Attribute 'FSAAAppControlled' (kvant:0.0): 1.
    'FSAAAppControlled' is a boolean attribute; valid values are: 1
    (on/true) and 0 (off/false).
    'FSAAAppControlled' can use the following target types: X Screen.

  Attribute 'LogAnisoAppControlled' (kvant:0.0): 1.
    'LogAnisoAppControlled' is a boolean attribute; valid values are: 1
    (on/true) and 0 (off/false).
    'LogAnisoAppControlled' can use the following target types: X Screen.

  Attribute 'OpenGLImageSettings' (kvant:0.0): 1.
    The valid values for 'OpenGLImageSettings' are in the range 0 - 3
    (inclusive).
    'OpenGLImageSettings' can use the following target types: X Screen.

  Attribute 'FSAAAppEnhanced' (kvant:0.0): 0.
    'FSAAAppEnhanced' is a boolean attribute; valid values are: 1 (on/true)
    and 0 (off/false).
    'FSAAAppEnhanced' can use the following target types: X Screen.

  Attribute 'SliMosaicModeAvailable' (kvant:0.0): 1.
    'SliMosaicModeAvailable' is a boolean attribute; valid values are: 1
    (on/true) and 0 (off/false).
    'SliMosaicModeAvailable' is a read-only attribute.
    'SliMosaicModeAvailable' can use the following target types: X Screen,
    GPU, VCS.

  Attribute 'BusType' (kvant:0.0): 2.
    The valid values for 'BusType' are in the range 0 - 3 (inclusive).
    'BusType' is a read-only attribute.
    'BusType' can use the following target types: X Screen, GPU, SDI Input
    Device.

  Attribute 'VideoRam' (kvant:0.0): 524288.
    'VideoRam' is an integer attribute.
    'VideoRam' is a read-only attribute.
    'VideoRam' can use the following target types: X Screen, GPU.

  Attribute 'Irq' (kvant:0.0): 24.
    'Irq' is an integer attribute.
    'Irq' is a read-only attribute.
    'Irq' can use the following target types: X Screen, GPU, SDI Input
    Device.

  Attribute 'CUDACores' (kvant:0.0): 96.
    'CUDACores' is an integer attribute.
    'CUDACores' is a read-only attribute.
    'CUDACores' can use the following target types: X Screen, GPU.

  Attribute 'GPUMemoryInterface' (kvant:0.0): 128.
    'GPUMemoryInterface' is an integer attribute.
    'GPUMemoryInterface' is a read-only attribute.
    'GPUMemoryInterface' can use the following target types: X Screen,
    GPU.

  Attribute 'GPUCoreTemp' (kvant:0.0): 39.
    'GPUCoreTemp' is an integer attribute.
    'GPUCoreTemp' is a read-only attribute.
    'GPUCoreTemp' can use the following target types: X Screen, GPU.

  Attribute 'GPU2DClockFreqs' (kvant:0.0): 135,135.
    The valid values for 'GPU2DClockFreqs' are in the ranges 33 - 270, 33 -
    162 (inclusive).
    'GPU2DClockFreqs' can use the following target types: X Screen, GPU.

  Attribute 'GPU3DClockFreqs' (kvant:0.0): 550,1800.
    The valid values for 'GPU3DClockFreqs' are in the ranges 137 - 1100,
    450 - 2160 (inclusive).
    'GPU3DClockFreqs' can use the following target types: X Screen, GPU.

  Attribute 'GPUDefault2DClockFreqs' (kvant:0.0): 135,135.
    'GPUDefault2DClockFreqs' is a packed integer attribute.
    'GPUDefault2DClockFreqs' is a read-only attribute.
    'GPUDefault2DClockFreqs' can use the following target types: X Screen,
    GPU.

  Attribute 'GPUDefault3DClockFreqs' (kvant:0.0): 550,1800.
    'GPUDefault3DClockFreqs' is a packed integer attribute.
    'GPUDefault3DClockFreqs' is a read-only attribute.
    'GPUDefault3DClockFreqs' can use the following target types: X Screen,
    GPU.

  Attribute 'GPUCurrentClockFreqs' (kvant:0.0): 550,1800.
    'GPUCurrentClockFreqs' is a packed integer attribute.
    'GPUCurrentClockFreqs' is a read-only attribute.
    'GPUCurrentClockFreqs' can use the following target types: X Screen,
    GPU.

  Attribute 'BusRate' (kvant:0.0): 4.
    The valid values for 'BusRate' are in the range 1 - 16 (inclusive).
    'BusRate' is a read-only attribute.
    'BusRate' can use the following target types: X Screen, GPU, SDI Input
    Device.

  Attribute 'PCIEGen' (kvant:0.0): 1.
    'PCIEGen' is an integer attribute.
    'PCIEGen' is a read-only attribute.
    'PCIEGen' can use the following target types: X Screen, GPU, SDI Input
    Device.

  Attribute 'GPUErrors' (kvant:0.0): 0.
    'GPUErrors' is an integer attribute.
    'GPUErrors' is a read-only attribute.
    'GPUErrors' can use the following target types: X Screen.

  Attribute 'GPUPowerSource' (kvant:0.0): 0.
    'GPUPowerSource' is an integer attribute.
    'GPUPowerSource' is a read-only attribute.
    'GPUPowerSource' can use the following target types: X Screen, GPU.

  Attribute 'GPUCurrentPerfMode' (kvant:0.0): 1.
    'GPUCurrentPerfMode' is an integer attribute.
    'GPUCurrentPerfMode' is a read-only attribute.
    'GPUCurrentPerfMode' can use the following target types: X Screen,
    GPU.

  Attribute 'GPUCurrentPerfLevel' (kvant:0.0): 2.
    'GPUCurrentPerfLevel' is an integer attribute.
    'GPUCurrentPerfLevel' is a read-only attribute.
    'GPUCurrentPerfLevel' can use the following target types: X Screen,
    GPU.

  Attribute 'GPUAdaptiveClockState' (kvant:0.0): 1.
    'GPUAdaptiveClockState' is an integer attribute.
    'GPUAdaptiveClockState' is a read-only attribute.
    'GPUAdaptiveClockState' can use the following target types: X Screen,
    GPU.

  Attribute 'GPUPerfModes' (kvant:0.0): perf=0, nvclock=135, memclock=135 ;
  perf=1, nvclock=405, memclock=324 ; perf=2, nvclock=550, memclock=1800 
    'GPUPerfModes' is a string attribute.
    'GPUPerfModes' is a read-only attribute.
    'GPUPerfModes' can use the following target types: X Screen, GPU.

  Attribute 'ECCSupported' (kvant:0.0): 0.
    'ECCSupported' is a boolean attribute; valid values are: 1 (on/true)
    and 0 (off/false).
    'ECCSupported' is a read-only attribute.
    'ECCSupported' can use the following target types: X Screen, GPU.

  Attribute 'ECCConfigurationSupported' (kvant:0.0): 0.
    'ECCConfigurationSupported' is a boolean attribute; valid values are: 1
    (on/true) and 0 (off/false).
    'ECCConfigurationSupported' is a read-only attribute.
    'ECCConfigurationSupported' can use the following target types: X
    Screen, GPU.

  Attribute 'GvoSupported' (kvant:0.0): 0.
    'GvoSupported' is a boolean attribute; valid values are: 1 (on/true)
    and 0 (off/false).
    'GvoSupported' is a read-only attribute.
    'GvoSupported' can use the following target types: X Screen.

  Attribute 'IsGvoDisplay' (kvant:0.0): 0.
    'IsGvoDisplay' is a boolean attribute; valid values are: 1 (on/true)
    and 0 (off/false).
    'IsGvoDisplay' is a read-only attribute.
    'IsGvoDisplay' can use the following target types: X Screen, GPU.

  Attribute 'DigitalVibrance' (kvant:0.0; display device: CRT-1): 0.
    The valid values for 'DigitalVibrance' are in the range 0 - 1023
    (inclusive).
    'DigitalVibrance' is display device specific.
    'DigitalVibrance' can use the following target types: X Screen, GPU.

  Attribute 'DigitalVibrance' (kvant:0.0; display device: DFP-0): 0.
    The valid values for 'DigitalVibrance' are in the range 0 - 1023
    (inclusive).
    'DigitalVibrance' is display device specific.
    'DigitalVibrance' can use the following target types: X Screen, GPU.

  Attribute 'RefreshRate' (kvant:0.0; display device: CRT-1): 60.02 Hz.
    'RefreshRate' is an integer attribute.
    'RefreshRate' is a read-only attribute.
    'RefreshRate' is display device specific.
    'RefreshRate' can use the following target types: X Screen, GPU.

  Attribute 'RefreshRate' (kvant:0.0; display device: DFP-0): 60.00 Hz.
    'RefreshRate' is an integer attribute.
    'RefreshRate' is a read-only attribute.
    'RefreshRate' is display device specific.
    'RefreshRate' can use the following target types: X Screen, GPU.

  Attribute 'RefreshRate3' (kvant:0.0; display device: CRT-1): 60.020 Hz.
    'RefreshRate3' is an integer attribute.
    'RefreshRate3' is a read-only attribute.
    'RefreshRate3' is display device specific.
    'RefreshRate3' can use the following target types: X Screen, GPU.

  Attribute 'RefreshRate3' (kvant:0.0; display device: DFP-0): 60.000 Hz.
    'RefreshRate3' is an integer attribute.
    'RefreshRate3' is a read-only attribute.
    'RefreshRate3' is display device specific.
    'RefreshRate3' can use the following target types: X Screen, GPU.

  Attribute 'OverscanCompensation' (kvant:0.0; display device: CRT-1): 0.
    The valid values for 'OverscanCompensation' are in the range 0 - 200
    (inclusive).
    'OverscanCompensation' is display device specific.
    'OverscanCompensation' can use the following target types: X Screen,
    GPU.

  Attribute 'OverscanCompensation' (kvant:0.0; display device: DFP-0): 0.
    The valid values for 'OverscanCompensation' are in the range 0 - 200
    (inclusive).
    'OverscanCompensation' is display device specific.
    'OverscanCompensation' can use the following target types: X Screen,
    GPU.

  Attribute 'XVideoTextureBrightness' (kvant:0.0): 0.
    The valid values for 'XVideoTextureBrightness' are in the range -1000 -
    1000 (inclusive).
    'XVideoTextureBrightness' can use the following target types: X
    Screen.

  Attribute 'XVideoTextureContrast' (kvant:0.0): 0.
    The valid values for 'XVideoTextureContrast' are in the range -1000 -
    1000 (inclusive).
    'XVideoTextureContrast' can use the following target types: X Screen.

  Attribute 'XVideoTextureHue' (kvant:0.0): 0.
    The valid values for 'XVideoTextureHue' are in the range -1000 - 1000
    (inclusive).
    'XVideoTextureHue' can use the following target types: X Screen.

  Attribute 'XVideoTextureSaturation' (kvant:0.0): 0.
    The valid values for 'XVideoTextureSaturation' are in the range -1000 -
    1000 (inclusive).
    'XVideoTextureSaturation' can use the following target types: X
    Screen.

  Attribute 'XVideoTextureSyncToVBlank' (kvant:0.0): 1.
    The valid values for 'XVideoTextureSyncToVBlank' are in the range 0 - 1
    (inclusive).
    'XVideoTextureSyncToVBlank' can use the following target types: X
    Screen.

  Attribute 'XVideoSyncToDisplay' (kvant:0.0): 0x00000002.
    'XVideoSyncToDisplay' is a bitmask attribute.
    'XVideoSyncToDisplay' can use the following target types: X Screen.

Attributes queryable via kvant:0[gpu:0]:

  Attribute 'OperatingSystem' (kvant:0[gpu:0]): 0.
    The valid values for 'OperatingSystem' are in the range 0 - 2
    (inclusive).
    'OperatingSystem' is a read-only attribute.
    'OperatingSystem' can use the following target types: X Screen, GPU.

  Attribute 'NvidiaDriverVersion' (kvant:0[gpu:0]): 195.36.24 
    'NvidiaDriverVersion' is a string attribute.
    'NvidiaDriverVersion' is a read-only attribute.
    'NvidiaDriverVersion' can use the following target types: X Screen,
    GPU.

  Attribute 'ConnectedDisplays' (kvant:0[gpu:0]): 0x00010002.
    'ConnectedDisplays' is a bitmask attribute.
    'ConnectedDisplays' is a read-only attribute.
    'ConnectedDisplays' can use the following target types: X Screen, GPU.

  Attribute 'EnabledDisplays' (kvant:0[gpu:0]): 0x00010002.
    'EnabledDisplays' is a bitmask attribute.
    'EnabledDisplays' is a read-only attribute.
    'EnabledDisplays' can use the following target types: X Screen, GPU.

  Attribute 'Depth30Allowed' (kvant:0[gpu:0]): 0.
    'Depth30Allowed' is a boolean attribute; valid values are: 1 (on/true)
    and 0 (off/false).
    'Depth30Allowed' is a read-only attribute.
    'Depth30Allowed' can use the following target types: X Screen, GPU.

  Attribute 'NoScanout' (kvant:0[gpu:0]): 0.
    'NoScanout' is a boolean attribute; valid values are: 1 (on/true) and 0
    (off/false).
    'NoScanout' is a read-only attribute.
    'NoScanout' can use the following target types: X Screen, GPU.

  Attribute 'SliMosaicModeAvailable' (kvant:0[gpu:0]): 1.
    'SliMosaicModeAvailable' is a boolean attribute; valid values are: 1
    (on/true) and 0 (off/false).
    'SliMosaicModeAvailable' is a read-only attribute.
    'SliMosaicModeAvailable' can use the following target types: X Screen,
    GPU, VCS.

  Attribute 'BusType' (kvant:0[gpu:0]): 2.
    The valid values for 'BusType' are in the range 0 - 3 (inclusive).
    'BusType' is a read-only attribute.
    'BusType' can use the following target types: X Screen, GPU, SDI Input
    Device.

  Attribute 'VideoRam' (kvant:0[gpu:0]): 524288.
    'VideoRam' is an integer attribute.
    'VideoRam' is a read-only attribute.
    'VideoRam' can use the following target types: X Screen, GPU.

  Attribute 'Irq' (kvant:0[gpu:0]): 24.
    'Irq' is an integer attribute.
    'Irq' is a read-only attribute.
    'Irq' can use the following target types: X Screen, GPU, SDI Input
    Device.

  Attribute 'CUDACores' (kvant:0[gpu:0]): 96.
    'CUDACores' is an integer attribute.
    'CUDACores' is a read-only attribute.
    'CUDACores' can use the following target types: X Screen, GPU.

  Attribute 'GPUMemoryInterface' (kvant:0[gpu:0]): 128.
    'GPUMemoryInterface' is an integer attribute.
    'GPUMemoryInterface' is a read-only attribute.
    'GPUMemoryInterface' can use the following target types: X Screen,
    GPU.

  Attribute 'GPUCoreTemp' (kvant:0[gpu:0]): 39.
    'GPUCoreTemp' is an integer attribute.
    'GPUCoreTemp' is a read-only attribute.
    'GPUCoreTemp' can use the following target types: X Screen, GPU.

  Attribute 'GPU2DClockFreqs' (kvant:0[gpu:0]): 135,135.
    The valid values for 'GPU2DClockFreqs' are in the ranges 33 - 270, 33 -
    162 (inclusive).
    'GPU2DClockFreqs' can use the following target types: X Screen, GPU.

  Attribute 'GPU3DClockFreqs' (kvant:0[gpu:0]): 550,1800.
    The valid values for 'GPU3DClockFreqs' are in the ranges 137 - 1100,
    450 - 2160 (inclusive).
    'GPU3DClockFreqs' can use the following target types: X Screen, GPU.

  Attribute 'GPUDefault2DClockFreqs' (kvant:0[gpu:0]): 135,135.
    'GPUDefault2DClockFreqs' is a packed integer attribute.
    'GPUDefault2DClockFreqs' is a read-only attribute.
    'GPUDefault2DClockFreqs' can use the following target types: X Screen,
    GPU.

  Attribute 'GPUDefault3DClockFreqs' (kvant:0[gpu:0]): 550,1800.
    'GPUDefault3DClockFreqs' is a packed integer attribute.
    'GPUDefault3DClockFreqs' is a read-only attribute.
    'GPUDefault3DClockFreqs' can use the following target types: X Screen,
    GPU.

  Attribute 'GPUCurrentClockFreqs' (kvant:0[gpu:0]): 550,1800.
    'GPUCurrentClockFreqs' is a packed integer attribute.
    'GPUCurrentClockFreqs' is a read-only attribute.
    'GPUCurrentClockFreqs' can use the following target types: X Screen,
    GPU.

  Attribute 'BusRate' (kvant:0[gpu:0]): 4.
    The valid values for 'BusRate' are in the range 1 - 16 (inclusive).
    'BusRate' is a read-only attribute.
    'BusRate' can use the following target types: X Screen, GPU, SDI Input
    Device.

  Attribute 'PCIDomain' (kvant:0[gpu:0]): 0.
    'PCIDomain' is an integer attribute.
    'PCIDomain' is a read-only attribute.
    'PCIDomain' can use the following target types: GPU, SDI Input Device.

  Attribute 'PCIBus' (kvant:0[gpu:0]): 2.
    'PCIBus' is an integer attribute.
    'PCIBus' is a read-only attribute.
    'PCIBus' can use the following target types: GPU, SDI Input Device.

  Attribute 'PCIDevice' (kvant:0[gpu:0]): 0.
    'PCIDevice' is an integer attribute.
    'PCIDevice' is a read-only attribute.
    'PCIDevice' can use the following target types: GPU, SDI Input Device.

  Attribute 'PCIFunc' (kvant:0[gpu:0]): 0.
    'PCIFunc' is an integer attribute.
    'PCIFunc' is a read-only attribute.
    'PCIFunc' can use the following target types: GPU, SDI Input Device.

  Attribute 'PCIID' (kvant:0[gpu:0]): 4318,3235.
    'PCIID' is a packed integer attribute.
    'PCIID' is a read-only attribute.
    'PCIID' can use the following target types: GPU, SDI Input Device.

  Attribute 'PCIEGen' (kvant:0[gpu:0]): 1.
    'PCIEGen' is an integer attribute.
    'PCIEGen' is a read-only attribute.
    'PCIEGen' can use the following target types: X Screen, GPU, SDI Input
    Device.

  Attribute 'GPUPowerSource' (kvant:0[gpu:0]): 0.
    'GPUPowerSource' is an integer attribute.
    'GPUPowerSource' is a read-only attribute.
    'GPUPowerSource' can use the following target types: X Screen, GPU.

  Attribute 'GPUCurrentPerfMode' (kvant:0[gpu:0]): 1.
    'GPUCurrentPerfMode' is an integer attribute.
    'GPUCurrentPerfMode' is a read-only attribute.
    'GPUCurrentPerfMode' can use the following target types: X Screen,
    GPU.

  Attribute 'GPUCurrentPerfLevel' (kvant:0[gpu:0]): 2.
    'GPUCurrentPerfLevel' is an integer attribute.
    'GPUCurrentPerfLevel' is a read-only attribute.
    'GPUCurrentPerfLevel' can use the following target types: X Screen,
    GPU.

  Attribute 'GPUAdaptiveClockState' (kvant:0[gpu:0]): 1.
    'GPUAdaptiveClockState' is an integer attribute.
    'GPUAdaptiveClockState' is a read-only attribute.
    'GPUAdaptiveClockState' can use the following target types: X Screen,
    GPU.

  Attribute 'GPUPerfModes' (kvant:0[gpu:0]): perf=0, nvclock=135,
  memclock=135 ; perf=1, nvclock=405, memclock=324 ; perf=2, nvclock=550,
  memclock=1800 
    'GPUPerfModes' is a string attribute.
    'GPUPerfModes' is a read-only attribute.
    'GPUPerfModes' can use the following target types: X Screen, GPU.

  Attribute 'GPUPowerMizerMode' (kvant:0[gpu:0]): 0.
    'GPUPowerMizerMode' is an integer attribute.
    'GPUPowerMizerMode' can use the following target types: GPU.

  Attribute 'ECCSupported' (kvant:0[gpu:0]): 0.
    'ECCSupported' is a boolean attribute; valid values are: 1 (on/true)
    and 0 (off/false).
    'ECCSupported' is a read-only attribute.
    'ECCSupported' can use the following target types: X Screen, GPU.

  Attribute 'ECCConfigurationSupported' (kvant:0[gpu:0]): 0.
    'ECCConfigurationSupported' is a boolean attribute; valid values are: 1
    (on/true) and 0 (off/false).
    'ECCConfigurationSupported' is a read-only attribute.
    'ECCConfigurationSupported' can use the following target types: X
    Screen, GPU.

  Attribute 'IsGvoDisplay' (kvant:0[gpu:0]): 0.
    'IsGvoDisplay' is a boolean attribute; valid values are: 1 (on/true)
    and 0 (off/false).
    'IsGvoDisplay' is a read-only attribute.
    'IsGvoDisplay' can use the following target types: X Screen, GPU.

  Attribute 'DigitalVibrance' (kvant:0[gpu:0]; display device: CRT-1): 0.
    The valid values for 'DigitalVibrance' are in the range 0 - 1023
    (inclusive).
    'DigitalVibrance' is display device specific.
    'DigitalVibrance' can use the following target types: X Screen, GPU.

  Attribute 'DigitalVibrance' (kvant:0[gpu:0]; display device: DFP-0): 0.
    The valid values for 'DigitalVibrance' are in the range 0 - 1023
    (inclusive).
    'DigitalVibrance' is display device specific.
    'DigitalVibrance' can use the following target types: X Screen, GPU.

  Attribute 'RefreshRate' (kvant:0[gpu:0]; display device: CRT-1): 60.02
  Hz.
    'RefreshRate' is an integer attribute.
    'RefreshRate' is a read-only attribute.
    'RefreshRate' is display device specific.
    'RefreshRate' can use the following target types: X Screen, GPU.

  Attribute 'RefreshRate' (kvant:0[gpu:0]; display device: DFP-0): 60.00
  Hz.
    'RefreshRate' is an integer attribute.
    'RefreshRate' is a read-only attribute.
    'RefreshRate' is display device specific.
    'RefreshRate' can use the following target types: X Screen, GPU.

  Attribute 'RefreshRate3' (kvant:0[gpu:0]; display device: CRT-1): 60.020
  Hz.
    'RefreshRate3' is an integer attribute.
    'RefreshRate3' is a read-only attribute.
    'RefreshRate3' is display device specific.
    'RefreshRate3' can use the following target types: X Screen, GPU.

  Attribute 'RefreshRate3' (kvant:0[gpu:0]; display device: DFP-0): 60.000
  Hz.
    'RefreshRate3' is an integer attribute.
    'RefreshRate3' is a read-only attribute.
    'RefreshRate3' is display device specific.
    'RefreshRate3' can use the following target types: X Screen, GPU.

  Attribute 'OverscanCompensation' (kvant:0[gpu:0]; display device: CRT-1):
  0.
    The valid values for 'OverscanCompensation' are in the range 0 - 200
    (inclusive).
    'OverscanCompensation' is display device specific.
    'OverscanCompensation' can use the following target types: X Screen,
    GPU.

  Attribute 'OverscanCompensation' (kvant:0[gpu:0]; display device: DFP-0):
  0.
    The valid values for 'OverscanCompensation' are in the range 0 - 200
    (inclusive).
    'OverscanCompensation' is display device specific.
    'OverscanCompensation' can use the following target types: X Screen,
    GPU.

Attributes queryable via kvant:0[fan:0]:

  Attribute 'GPUCurrentFanSpeed' (kvant:0[fan:0]): 35.
    The valid values for 'GPUCurrentFanSpeed' are in the range 0 - 100
    (inclusive).
    'GPUCurrentFanSpeed' can use the following target types: Fan.

  Attribute 'GPUFanControlType' (kvant:0[fan:0]): 2.
    'GPUFanControlType' is an integer attribute.
    'GPUFanControlType' is a read-only attribute.
    'GPUFanControlType' can use the following target types: Fan.

  Attribute 'GPUFanTarget' (kvant:0[fan:0]): 0x00000007.
    'GPUFanTarget' is a bitmask attribute.
    'GPUFanTarget' is a read-only attribute.
    'GPUFanTarget' can use the following target types: Fan.

____________________________________________

/proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=904eae1e-3da9-44ba-a36f-ba4094c10c8e ro quiet splash

____________________________________________

/proc/cpuinfo
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 23
model name    : Intel(R) Core(TM)2 CPU         E7400  @ 2.80GHz
stepping    : 10
cpu MHz        : 2802.338
cache size    : 3072 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm
bogomips    : 5604.67
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 23
model name    : Intel(R) Core(TM)2 CPU         E7400  @ 2.80GHz
stepping    : 10
cpu MHz        : 2802.338
cache size    : 3072 KB
physical id    : 0
siblings    : 2
core id        : 1
cpu cores    : 2
apicid        : 1
initial apicid    : 1
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm
bogomips    : 5604.97
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:


____________________________________________

/proc/interrupts
           CPU0       CPU1       
  0:         28          0   IO-APIC-edge      timer
  1:          8          0   IO-APIC-edge      i8042
  4:          3          0   IO-APIC-edge    
  6:          5          0   IO-APIC-edge      floppy
  7:          0          0   IO-APIC-edge      parport0
  8:          0          0   IO-APIC-edge      rtc0
  9:          0          0   IO-APIC-fasteoi   acpi
 14:          0          0   IO-APIC-edge      pata_via
 15:       1068          0   IO-APIC-edge      pata_via
 17:       1610          0   IO-APIC-fasteoi   HDA Intel
 20:        188       1036   IO-APIC-fasteoi   uhci_hcd:usb2
 21:      13027          0   IO-APIC-fasteoi   ehci_hcd:usb1, uhci_hcd:usb4, sata_via
 22:          0          0   IO-APIC-fasteoi   uhci_hcd:usb3
 23:         44       5428   IO-APIC-fasteoi   uhci_hcd:usb5, eth0
 24:        815          0   IO-APIC-fasteoi   nvidia
 25:          4          0   IO-APIC-fasteoi   HDA Intel
 48:          0          0   PCI-MSI-edge      aerdrv
NMI:          0          0   Non-maskable interrupts
LOC:      12922       6708   Local timer interrupts
SPU:          0          0   Spurious interrupts
PMI:          0          0   Performance monitoring interrupts
PND:          0          0   Performance pending work
RES:       1058        708   Rescheduling interrupts
CAL:        200       2790   Function call interrupts
TLB:       5940       1120   TLB shootdowns
TRM:          0          0   Thermal event interrupts
THR:          0          0   Threshold APIC interrupts
MCE:          0          0   Machine check exceptions
MCP:          1          1   Machine check polls
ERR:          1
MIS:          0

____________________________________________

/proc/meminfo
MemTotal:        2573548 kB
MemFree:         1705472 kB
Buffers:           62236 kB
Cached:           326088 kB
SwapCached:            0 kB
Active:           439192 kB
Inactive:         264972 kB
Active(anon):     321312 kB
Inactive(anon):       16 kB
Active(file):     117880 kB
Inactive(file):   264956 kB
Unevictable:           0 kB
Mlocked:               0 kB
SwapTotal:       7537656 kB
SwapFree:        7537656 kB
Dirty:                 0 kB
Writeback:             0 kB
AnonPages:        315844 kB
Mapped:            98620 kB
Shmem:              5492 kB
Slab:              34572 kB
SReclaimable:      17044 kB
SUnreclaim:        17528 kB
KernelStack:        2240 kB
PageTables:        19056 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     8824428 kB
Committed_AS:     910232 kB
VmallocTotal:   34359738367 kB
VmallocUsed:      335004 kB
VmallocChunk:   34359393772 kB
HardwareCorrupted:     0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:      100032 kB
DirectMap2M:     2521088 kB

____________________________________________

/proc/modules
cryptd 8116 0 - Live 0xffffffffa0b77000
aes_x86_64 7912 253 - Live 0xffffffffa009a000
aes_generic 27607 1 aes_x86_64, Live 0xffffffffa0b6e000
dm_crypt 13043 0 - Live 0xffffffffa007c000
snd_hda_codec_realtek 279040 1 - Live 0xffffffffa0b1b000
binfmt_misc 7960 1 - Live 0xffffffffa0033000
snd_hda_intel 25677 2 - Live 0xffffffffa0cef000
snd_hda_codec 85759 2 snd_hda_codec_realtek,snd_hda_intel, Live 0xffffffffa0ccd000
snd_hwdep 6924 1 snd_hda_codec, Live 0xffffffffa0cc5000
snd_pcm_oss 41394 0 - Live 0xffffffffa0cb3000
snd_mixer_oss 16299 1 snd_pcm_oss, Live 0xffffffffa0ca9000
snd_pcm 87882 3 snd_hda_intel,snd_hda_codec,snd_pcm_oss, Live 0xffffffffa0c87000
snd_seq_dummy 1782 0 - Live 0xffffffffa0c81000
snd_seq_oss 31219 0 - Live 0xffffffffa0c72000
snd_seq_midi 5829 0 - Live 0xffffffffa0c6b000
snd_rawmidi 23420 1 snd_seq_midi, Live 0xffffffffa0c5e000
snd_seq_midi_event 7267 2 snd_seq_oss,snd_seq_midi, Live 0xffffffffa0057000
snd_seq 57481 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event, Live 0xffffffffa0c49000
snd_timer 23649 2 snd_pcm,snd_seq, Live 0xffffffffa0c41000
snd_seq_device 6888 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq, Live 0xffffffffa004a000
ppdev 6375 0 - Live 0xffffffffa003c000
lp 9336 0 - Live 0xffffffffa0021000
snd 71106 16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device, Live 0xffffffffa0c23000
parport_pc 29958 1 - Live 0xffffffffa0c19000
nvidia 10832442 40 - Live 0xffffffffa00c4000 (P)
i2c_viapro 6537 0 - Live 0xffffffffa000c000
soundcore 8052 1 snd, Live 0xffffffffa002a000
shpchp 33711 0 - Live 0xffffffffa00b9000
parport 37160 3 ppdev,lp,parport_pc, Live 0xffffffffa00ad000
joydev 11072 0 - Live 0xffffffffa0017000
snd_page_alloc 8500 2 snd_hda_intel,snd_pcm, Live 0xffffffffa0004000
usbhid 41084 0 - Live 0xffffffffa00a0000
hid 83440 1 usbhid, Live 0xffffffffa0083000
floppy 63156 0 - Live 0xffffffffa006a000
fbcon 39270 71 - Live 0xffffffffa005a000
tileblit 2487 1 fbcon, Live 0xffffffffa0054000
font 8053 1 fbcon, Live 0xffffffffa004d000
bitblit 5811 1 fbcon, Live 0xffffffffa0046000
softcursor 1565 1 bitblit, Live 0xffffffffa0040000
pata_via 9072 0 - Live 0xffffffffa0037000
vga16fb 12757 1 - Live 0xffffffffa002d000
vgastate 9857 1 vga16fb, Live 0xffffffffa0025000
sata_via 9389 2 - Live 0xffffffffa001c000
via_rhine 22496 0 - Live 0xffffffffa000f000
mii 5237 1 via_rhine, Live 0xffffffffa0008000
via_agp 6526 1 - Live 0xffffffffa0000000

____________________________________________

/proc/version
Linux version 2.6.32-24-generic (buildd@crested) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #42-Ubuntu SMP Fri Aug 20 14:21:58 UTC 2010

____________________________________________

/proc/pci does not exist

____________________________________________

/proc/iomem
00000000-0000ffff : reserved
00010000-0009fbff : System RAM
0009fc00-0009ffff : reserved
000c0000-000cffff : pnp 00:0c
000e6000-000fffff : reserved
00100000-9ffaffff : System RAM
  01000000-0154bbd6 : Kernel code
  0154bbd7-018349cf : Kernel data
  0191e000-01a2fe63 : Kernel bss
9ffb0000-9ffbffff : ACPI Tables
9ffc0000-9ffeffff : ACPI Non-volatile Storage
9fff0000-9fffffff : reserved
bbf00000-dfefffff : PCI Bus 0000:02
  c0000000-cfffffff : 0000:02:00.0
  dc000000-ddffffff : 0000:02:00.0
e0000000-efffffff : PCI MMCONFIG 0 [00-ff]
  e0000000-efffffff : pnp 00:0b
f8000000-fbffffff : 0000:00:00.0
fc700000-fc7fffff : PCI Bus 0000:01
fc800000-fe9fffff : PCI Bus 0000:02
  fd000000-fdffffff : 0000:02:00.0
    fd000000-fdffffff : nvidia
  fe97c000-fe97ffff : 0000:02:00.1
    fe97c000-fe97ffff : ICH HD audio
  fe980000-fe9fffff : 0000:02:00.0
feafc000-feafffff : 0000:80:01.0
  feafc000-feafffff : pnp 00:07
    feafc000-feafffff : ICH HD audio
febff800-febff8ff : 0000:00:10.4
  febff800-febff8ff : ehci_hcd
febffc00-febffcff : 0000:00:12.0
  febffc00-febffcff : via-rhine
fec00000-fec00fff : IOAPIC 0
fecc0000-fecc0fff : IOAPIC 1
fee00000-fee00fff : Local APIC
  fee00000-fee00fff : reserved
    fee00000-fee00fff : pnp 00:08
ff780000-ffffffff : reserved
  ffb80000-ffbfffff : pnp 00:07
  fff80000-ffffffff : pnp 00:0c

____________________________________________

/proc/mtrr
reg00: base=0x000000000 (    0MB), size= 2048MB, count=1: write-back
reg01: base=0x080000000 ( 2048MB), size=  512MB, count=1: write-back

____________________________________________

/proc/driver/nvidia/version
NVRM version: NVIDIA UNIX x86_64 Kernel Module  195.36.24  Thu Apr 22 19:10:14 PDT 2010
GCC version:  gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) 

____________________________________________

/proc/driver/nvidia/cards/0
Model:          GeForce GT 240
IRQ:            24
Video BIOS:      70.15.27.00.02
Card Type:      PCI-E
DMA Size:      40 bits
DMA Mask:      0xffffffffff
Bus Location:      02.00.0

____________________________________________

/proc/driver/nvidia/warnings/README
The NVIDIA graphics driver tries to detect potential problems
with the host system and warns about them using the system's
logging mechanisms. Important warning message are also logged
to dedicated text files in this directory.

____________________________________________

/proc/driver/nvidia/registry
EnableVia4x: 0
EnableALiAGP: 0
NvAGP: 3
ReqAGPRate: 15
EnableAGPSBA: 0
EnableAGPFW: 0
Mobile: 4294967295
ResmanDebugLevel: 4294967295
RmLogonRC: 1
ModifyDeviceFiles: 1
DeviceFileUID: 0
DeviceFileGID: 0
DeviceFileMode: 438
RemapLimit: 0
UpdateMemoryTypes: 4294967295
UseVBios: 1
RMEdgeIntrCheck: 1
UsePageAttributeTable: 4294967295
EnableMSI: 0
MapRegistersEarly: 0
RegisterForACPIEvents: 1
RegistryDwords: ""

____________________________________________

/proc/asound/cards
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfe97c000 irq 25
 1 [VT82xx         ]: HDA-Intel - HDA VIA VT82xx
                      HDA VIA VT82xx at 0xfeafc000 irq 17

____________________________________________

/proc/asound/pcm
01-00: ALC888 Analog : ALC888 Analog : playback 1 : capture 1
01-01: ALC888 Digital : ALC888 Digital : playback 1
01-02: ALC888 Analog : ALC888 Analog : capture 1

____________________________________________

/proc/asound/modules
 0 snd_hda_intel
 1 snd_hda_intel

____________________________________________

/proc/asound/devices
  2:        : timer
  3:        : sequencer
  4: [ 0- 0]: hardware dependent
  5: [ 0]   : control
  6: [ 1- 2]: digital audio capture
  7: [ 1- 1]: digital audio playback
  8: [ 1- 0]: digital audio playback
  9: [ 1- 0]: digital audio capture
 10: [ 1- 0]: hardware dependent
 11: [ 1]   : control

____________________________________________

/proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.

____________________________________________

/proc/asound/timers
G0: system timer : 10000.000us (10000000 ticks)
P1-0-0: PCM playback 1-0-0 : SLAVE
P1-0-1: PCM capture 1-0-1 : SLAVE
P1-1-0: PCM playback 1-1-0 : SLAVE
P1-2-1: PCM capture 1-2-1 : SLAVE

____________________________________________

/proc/asound/hwdep
00-00: HDA Codec 0
01-00: HDA Codec 0

____________________________________________

/proc/asound/card0/codec#0
Codec: Generic 0000 ID 0
Address: 0
Function Id: 0x1
Vendor Id: 0x00000000
Subsystem Id: 0x10de0101
Revision Id: 0x100100
No Modem Function Group found
Default PCM:
    rates [0x0]:
    bits [0x0]:
    formats [0x0]:
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x04 [Audio Output] wcaps 0x72b1: 8-Channels Digital Stripe CP
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Unsolicited: tag=00, enabled=0
Node 0x05 [Pin Complex] wcaps 0x407381: 8-Channels Digital CP
  Pincap 0x09000094: OUT Detect HDMI
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x04

____________________________________________

/proc/asound/card1/codec#0
Codec: Realtek ALC888
Address: 0
Function Id: 0x1
Vendor Id: 0x10ec0888
Subsystem Id: 0x18491e01
Revision Id: 0x100001
No Modem Function Group found
Default PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=3, o=0, i=0, unsolicited=1, wake=0
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[2]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x02 [Audio Output] wcaps 0x11: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x03 [Audio Output] wcaps 0x11: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x04 [Audio Output] wcaps 0x11: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x05 [Audio Output] wcaps 0x11: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x06 [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0x1e]: 16 20 24 32
    formats [0x1]: PCM
Node 0x07 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x08 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Amp-In caps: ofs=0x0b, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x1f 0x1f]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0x6]: 16 20
    formats [0x1]: PCM
  Connection: 1
     0x23
Node 0x09 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Amp-In caps: ofs=0x0b, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x00 0x00]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0x6]: 16 20
    formats [0x1]: PCM
  Connection: 1
     0x22
Node 0x0a [Audio Input] wcaps 0x100391: Stereo Digital
  Converter: stream=0, channel=0
  SDI-Select: 0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0x1e]: 16 20 24 32
    formats [0x1]: PCM
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x1f
Node 0x0b [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x88 0x88] [0x80 0x80] [0x87 0x87] [0x80 0x80] [0x19 0x19] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 10
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17
Node 0x0c [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x14 0x14]
  Connection: 2
     0x02 0x0b
Node 0x0d [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x14 0x14]
  Connection: 2
     0x03 0x0b
Node 0x0e [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x14 0x14]
  Connection: 2
     0x04 0x0b
Node 0x0f [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x14 0x14]
  Connection: 2
     0x05 0x0b
Node 0x10 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x11 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x12 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x13 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x14 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000003e: IN OUT HP Detect Trigger
  Pin Default 0x01014010: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Green
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x15 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000003e: IN OUT HP Detect Trigger
  Pin Default 0x01011012: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0x1, Sequence = 0x2
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c 0x0d* 0x0e 0x0f 0x26
Node 0x16 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x00000036: IN OUT Detect Trigger
  Pin Default 0x01016011: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Orange
    DefAssociation = 0x1, Sequence = 0x1
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c 0x0d 0x0e* 0x0f 0x26
Node 0x17 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x00000036: IN OUT Detect Trigger
  Pin Default 0x01012014: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Grey
    DefAssociation = 0x1, Sequence = 0x4
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c 0x0d 0x0e 0x0f* 0x26
Node 0x18 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000373e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x01a19830: [Jack] Mic at Ext Rear
    Conn = 1/8, Color = Pink
    DefAssociation = 0x3, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x19 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000373e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1a [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000373e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x01813031: [Jack] Line In at Ext Rear
    Conn = 1/8, Color = Blue
    DefAssociation = 0x3, Sequence = 0x1
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1b [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000373e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1c [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x9933013f: [Fixed] CD at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0x3, Sequence = 0xf
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
Node 0x1d [Pin Complex] wcaps 0x400000: Mono
  Pincap 0x00000020: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
Node 0x1e [Pin Complex] wcaps 0x400300: Mono Digital
  Pincap 0x00000010: OUT
  Pin Default 0xc144e120: [Both] SPDIF Out at Ext Rear
    Conn = RCA, Color = White
    DefAssociation = 0x2, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x06
Node 0x1f [Pin Complex] wcaps 0x400200: Mono Digital
  Pincap 0x00000020: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
Node 0x20 [Vendor Defined Widget] wcaps 0xf00040: Mono
  Processing caps: benign=0, ncoeff=17
  Processing Coefficient: 0x6000
  Coefficient Index: 0x09
Node 0x21 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x22 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 11
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b
Node 0x23 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 11
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b
Node 0x24 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x25 [Audio Output] wcaps 0x11: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x26 [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 2
     0x25 0x0b

____________________________________________

End of NVIDIA bug report log file.

There you go, most of that doesn't make much sense to me tho. :/

I guess it has to do something with the xorg configuration, but I can't see anything wrong with it. And it works sometimes, that's the odd thing. Maybe the kernel module doesn't load as that guy said?
I don't know how to fix it tho.

---

### Post by realzippy on 2010-09-09
The module seems to load-at least in your last log.
You could try to outcomment (#)  Option "DPMS" in xorg.conf.
You use the 195.xx driver,maybe you should try 256.xx...

cannot find anything wrong in the last logs/xorg.conf
(what NOT means there isn't any).



Edit:
wanted you to attach file,my mistake...

---

### Post by frostig on 2010-09-11
Well yeah, it does sometimes atleast.

I would say 50% of the time it loads up and I can just login as normal. But the rest of the times it starts in low-graphic mode.

I could try that and come back with the results, but I think I may have already tried it with bad results. But I will try it again!

---

