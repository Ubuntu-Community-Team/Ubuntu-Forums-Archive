---
title: "Ubuntu 12.04 with NV34 (NVidia GeForce Fx5500) dualmonitor wont work."
date: 2013-03-10
forum: Hardware
---

### Post by danman1453 on 2013-03-10
I have tried many things to get this working. I have an LCD monitor attached to each VGA port on the card. It was working as a cloned display. Then it stopped for no apparent reason. My goal is to have a simple virtual desktop. I would like to be able to drag windows from one desktop to the other. I am somewhat of a *nix noob.

Here is my Xorg.0.log:

> [    66.472] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    66.472] X Protocol Version 11, Revision 0
[    66.472] Build Operating System: Linux 2.6.42-34-generic i686 Ubuntu
[    66.472] Current Operating System: Linux dekstop 3.2.0-38-generic #61-Ubuntu SMP Tue Feb 19 12:20:02 UTC 2013 i686
[    66.496] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-38-generic root=UUID=a351602c-efdd-4575-b87e-b3d3266df470 ro quiet splash vt.handoff=7
[    66.497] Build Date: 16 January 2013  11:05:18PM
[    66.497] xorg-server 2:1.11.4-0ubuntu10.11 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    66.497] Current version of pixman: 0.24.4
[    66.497]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    66.497] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    66.497] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Mar  9 23:48:48 2013
[    66.498] (==) Using config file: "/etc/X11/xorg.conf"
[    66.498] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    66.499] (==) ServerLayout "Layout0"
[    66.499] (**) |-->Screen "Screen0" (0)
[    66.499] (**) |   |-->Monitor "Monitor0"
[    66.500] (**) |   |-->Device "Device0"
[    66.500] (**) |-->Screen "Screen1" (1)
[    66.500] (**) |   |-->Monitor "Monitor1"
[    66.529] (**) |   |-->Device "Device1"
[    66.529] (**) |-->Input Device "Keyboard0"
[    66.529] (**) |-->Input Device "Mouse0"
[    66.529] (**) Option "Xinerama" "1"
[    66.529] (==) Automatically adding devices
[    66.529] (==) Automatically enabling devices
[    66.529] (**) Xinerama: enabled
[    66.530] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    66.530]     Entry deleted from font path.
[    66.530] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    66.530]     Entry deleted from font path.
[    66.530] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    66.530]     Entry deleted from font path.
[    66.530] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    66.530]     Entry deleted from font path.
[    66.530] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    66.530]     Entry deleted from font path.
[    66.530] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    66.530] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    66.530] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    66.530] (WW) Disabling Keyboard0
[    66.530] (WW) Disabling Mouse0
[    66.531] (II) Loader magic: 0xba25a0
[    66.531] (II) Module ABI versions:
[    66.531]     X.Org ANSI C Emulation: 0.4
[    66.531]     X.Org Video Driver: 11.0
[    66.531]     X.Org XInput driver : 16.0
[    66.531]     X.Org Server Extension : 6.0
[    66.553] (--) PCI: (0:0:2:0) 8086:2562:1462:5778 rev 3, Mem @ 0xd0000000/134217728, 0xe7000000/524288
[    66.553] (--) PCI:*(0:1:10:0) 10de:0326:0000:0000 rev 161, Mem @ 0xe4000000/16777216, 0xd8000000/134217728, BIOS @ 0x????????/131072
[    66.561] (II) Open ACPI successful (/var/run/acpid.socket)
[    66.561] (II) LoadModule: "extmod"
[    66.563] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    66.564] (II) Module extmod: vendor="X.Org Foundation"
[    66.564]     compiled for 1.11.3, module version = 1.0.0
[    66.564]     Module class: X.Org Server Extension
[    66.564]     ABI class: X.Org Server Extension, version 6.0
[    66.564] (II) Loading extension MIT-SCREEN-SAVER
[    66.564] (II) Loading extension XFree86-VidModeExtension
[    66.564] (II) Loading extension XFree86-DGA
[    66.564] (II) Loading extension DPMS
[    66.564] (II) Loading extension XVideo
[    66.564] (II) Loading extension XVideo-MotionCompensation
[    66.564] (II) Loading extension X-Resource
[    66.564] (II) LoadModule: "dbe"
[    66.585] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    66.586] (II) Module dbe: vendor="X.Org Foundation"
[    66.586]     compiled for 1.11.3, module version = 1.0.0
[    66.586]     Module class: X.Org Server Extension
[    66.586]     ABI class: X.Org Server Extension, version 6.0
[    66.586] (II) Loading extension DOUBLE-BUFFER
[    66.586] (II) LoadModule: "glx"
[    66.586] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/libglx.so
[    66.784] (II) Module glx: vendor="NVIDIA Corporation"
[    66.784]     compiled for 4.0.2, module version = 1.0.0
[    66.784]     Module class: X.Org Server Extension
[    66.784] (II) NVIDIA GLX Module  173.14.36  Tue Sep 11 12:33:25 PDT 2012
[    66.784] (II) Loading extension GLX
[    66.784] (II) LoadModule: "record"
[    66.800] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    66.801] (II) Module record: vendor="X.Org Foundation"
[    66.801]     compiled for 1.11.3, module version = 1.13.0
[    66.801]     Module class: X.Org Server Extension
[    66.801]     ABI class: X.Org Server Extension, version 6.0
[    66.801] (II) Loading extension RECORD
[    66.801] (II) LoadModule: "dri"
[    66.802] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    66.803] (II) Module dri: vendor="X.Org Foundation"
[    66.803]     compiled for 1.11.3, module version = 1.0.0
[    66.803]     ABI class: X.Org Server Extension, version 6.0
[    66.803] (II) Loading extension XFree86-DRI
[    66.803] (II) LoadModule: "dri2"
[    66.804] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    66.821] (II) Module dri2: vendor="X.Org Foundation"
[    66.821]     compiled for 1.11.3, module version = 1.2.0
[    66.821]     ABI class: X.Org Server Extension, version 6.0
[    66.821] (II) Loading extension DRI2
[    66.821] (II) LoadModule: "nvidia"
[    66.821] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    66.823] (II) Module nvidia: vendor="NVIDIA Corporation"
[    66.823]     compiled for 4.0.2, module version = 1.0.0
[    66.823]     Module class: X.Org Video Driver
[    66.823] (II) NVIDIA dlloader X Driver  173.14.36  Tue Sep 11 12:21:22 PDT 2012
[    66.823] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    66.823] (++) using VT number 7


[    66.824] (EE) No devices detected.
[    66.824] (==) Matched nvidia as autoconfigured driver 0
[    66.824] (==) Matched nouveau as autoconfigured driver 1
[    66.824] (==) Matched nv as autoconfigured driver 2
[    66.824] (==) Matched vesa as autoconfigured driver 3
[    66.824] (==) Matched fbdev as autoconfigured driver 4
[    66.824] (==) Assigned the driver to the xf86ConfigLayout
[    66.824] (II) LoadModule: "nvidia"
[    66.824] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    66.824] (II) Module nvidia: vendor="NVIDIA Corporation"
[    66.824]     compiled for 4.0.2, module version = 1.0.0
[    66.824]     Module class: X.Org Video Driver
[    66.824] (II) UnloadModule: "nvidia"
[    66.824] (II) Unloading nvidia
[    66.825] (II) Failed to load module "nvidia" (already loaded, 11962907)
[    66.825] (II) LoadModule: "nouveau"
[    66.826] (WW) Warning, couldn't open module nouveau
[    66.826] (II) UnloadModule: "nouveau"
[    66.826] (II) Unloading nouveau
[    66.826] (EE) Failed to load module "nouveau" (module does not exist, 0)
[    66.826] (II) LoadModule: "nv"
[    66.828] (WW) Warning, couldn't open module nv
[    66.828] (II) UnloadModule: "nv"
[    66.828] (II) Unloading nv
[    66.828] (EE) Failed to load module "nv" (module does not exist, 0)
[    66.828] (II) LoadModule: "vesa"
[    66.845] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    66.845] (II) Module vesa: vendor="X.Org Foundation"
[    66.845]     compiled for 1.11.3, module version = 2.3.0
[    66.845]     Module class: X.Org Video Driver
[    66.845]     ABI class: X.Org Video Driver, version 11.0
[    66.846] (II) LoadModule: "fbdev"
[    66.846] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    66.847] (II) Module fbdev: vendor="X.Org Foundation"
[    66.847]     compiled for 1.11.3, module version = 0.4.2
[    66.847]     ABI class: X.Org Video Driver, version 11.0
[    66.847] (II) NVIDIA dlloader X Driver  173.14.36  Tue Sep 11 12:21:22 PDT 2012
[    66.847] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    66.847] (II) VESA: driver for VESA chipsets: vesa
[    66.847] (II) FBDEV: driver for framebuffer: fbdev
[    66.847] (++) using VT number 7


[    66.847] (WW) xf86OpenConsole: setpgid failed: Operation not permitted
[    66.847] (WW) xf86OpenConsole: setsid failed: Operation not permitted
[    66.865] (WW) Falling back to old probe method for vesa
[    66.865] (WW) Falling back to old probe method for fbdev
[    66.865] (II) Loading sub module "fbdevhw"
[    66.865] (II) LoadModule: "fbdevhw"
[    66.866] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    66.866] (II) Module fbdevhw: vendor="X.Org Foundation"
[    66.866]     compiled for 1.11.3, module version = 0.0.2
[    66.866]     ABI class: X.Org Video Driver, version 11.0
[    66.867] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    66.867] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    66.867] (II) FBDEV(0): using default device
[    66.867] (**) FBDEV(0): Depth 24, (--) framebuffer bpp 32
[    66.867] (==) FBDEV(0): RGB weight 888
[    66.867] (==) FBDEV(0): Default visual is TrueColor
[    66.867] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[    66.867] (II) FBDEV(0): hardware: VESA VGA (video memory: 3072kB)
[    66.867] (II) FBDEV(0): checking modes against framebuffer device...
[    66.868] (II) FBDEV(0): checking modes against monitor...
[    66.868] (--) FBDEV(0): Virtual size is 1024x768 (pitch 1024)
[    66.868] (**) FBDEV(0):  Built-in mode "current": 78.7 MHz, 59.9 kHz, 75.7 Hz
[    66.868] (II) FBDEV(0): Modeline "current"x0.0   78.65  1024 1056 1184 1312  768 772 776 792 -hsync -vsync -csync (59.9 kHz)
[    66.868] (==) FBDEV(0): DPI set to (96, 96)
[    66.868] (II) Loading sub module "fb"
[    66.868] (II) LoadModule: "fb"
[    66.877] (II) Loading /usr/lib/xorg/modules/libfb.so
[    66.877] (II) Module fb: vendor="X.Org Foundation"
[    66.877]     compiled for 1.11.3, module version = 1.0.0
[    66.878]     ABI class: X.Org ANSI C Emulation, version 0.4
[    66.878] (**) FBDEV(0): using shadow framebuffer
[    66.878] (II) Loading sub module "shadow"
[    66.878] (II) LoadModule: "shadow"
[    66.878] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    66.879] (II) Module shadow: vendor="X.Org Foundation"
[    66.879]     compiled for 1.11.3, module version = 1.1.0
[    66.879]     ABI class: X.Org ANSI C Emulation, version 0.4
[    66.879] (II) UnloadModule: "nvidia"
[    66.879] (II) Unloading nvidia
[    66.879] (II) UnloadModule: "vesa"
[    66.879] (II) Unloading vesa
[    66.879] (==) Depth 24 pixmap format is 32 bpp
[    66.880] (EE) FBDEV(0): FBIOBLANK: Invalid argument
[    66.880] (==) FBDEV(0): Backing store disabled
[    66.893] (**) FBDEV(0): DPMS enabled
[    66.893] (==) RandR enabled
[    66.894] (II) Initializing built-in extension Generic Event Extension
[    66.894] (II) Initializing built-in extension SHAPE
[    66.894] (II) Initializing built-in extension MIT-SHM
[    66.894] (II) Initializing built-in extension XInputExtension
[    66.894] (II) Initializing built-in extension XTEST
[    66.894] (II) Initializing built-in extension BIG-REQUESTS
[    66.894] (II) Initializing built-in extension SYNC
[    66.894] (II) Initializing built-in extension XKEYBOARD
[    66.894] (II) Initializing built-in extension XC-MISC
[    66.894] (II) Initializing built-in extension SECURITY
[    66.894] (II) Initializing built-in extension XINERAMA
[    66.894] (II) Initializing built-in extension XFIXES
[    66.894] (II) Initializing built-in extension RENDER
[    66.894] (II) Initializing built-in extension RANDR
[    66.894] (II) Initializing built-in extension COMPOSITE
[    66.894] (II) Initializing built-in extension DAMAGE
[    66.906] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
[    67.016] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    67.128] (II) config/udev: Adding input device Logitech Logitech USB Keyboard (/dev/input/event0)
[    67.128] (**) Logitech Logitech USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    67.128] (II) LoadModule: "evdev"
[    67.137] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    67.138] (II) Module evdev: vendor="X.Org Foundation"
[    67.138]     compiled for 1.11.3, module version = 2.7.0
[    67.138]     Module class: X.Org XInput Driver
[    67.138]     ABI class: X.Org XInput driver, version 16.0
[    67.138] (II) Using input driver 'evdev' for 'Logitech Logitech USB Keyboard'
[    67.138] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    67.138] (**) Logitech Logitech USB Keyboard: always reports core events
[    67.138] (**) evdev: Logitech Logitech USB Keyboard: Device: "/dev/input/event0"
[    67.139] (--) evdev: Logitech Logitech USB Keyboard: Vendor 0x46d Product 0xc315
[    67.139] (--) evdev: Logitech Logitech USB Keyboard: Found keys
[    67.139] (II) evdev: Logitech Logitech USB Keyboard: Configuring as keyboard
[    67.139] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input0/event0"
[    67.139] (II) XINPUT: Adding extended input device "Logitech Logitech USB Keyboard" (type: KEYBOARD, id 6)
[    67.139] (**) Option "xkb_rules" "evdev"
[    67.139] (**) Option "xkb_model" "pc105"
[    67.139] (**) Option "xkb_layout" "us"
[    67.154] (II) config/udev: Adding input device ImExPS/2 Generic Explorer Mouse (/dev/input/event1)
[    67.154] (**) ImExPS/2 Generic Explorer Mouse: Applying InputClass "evdev pointer catchall"
[    67.154] (II) Using input driver 'evdev' for 'ImExPS/2 Generic Explorer Mouse'
[    67.154] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    67.154] (**) ImExPS/2 Generic Explorer Mouse: always reports core events
[    67.154] (**) evdev: ImExPS/2 Generic Explorer Mouse: Device: "/dev/input/event1"
[    67.154] (--) evdev: ImExPS/2 Generic Explorer Mouse: Vendor 0x2 Product 0x6
[    67.155] (--) evdev: ImExPS/2 Generic Explorer Mouse: Found 9 mouse buttons
[    67.155] (--) evdev: ImExPS/2 Generic Explorer Mouse: Found scroll wheel(s)
[    67.155] (--) evdev: ImExPS/2 Generic Explorer Mouse: Found relative axes
[    67.155] (--) evdev: ImExPS/2 Generic Explorer Mouse: Found x and y relative axes
[    67.155] (II) evdev: ImExPS/2 Generic Explorer Mouse: Configuring as mouse
[    67.155] (II) evdev: ImExPS/2 Generic Explorer Mouse: Adding scrollwheel support
[    67.155] (**) evdev: ImExPS/2 Generic Explorer Mouse: YAxisMapping: buttons 4 and 5
[    67.155] (**) evdev: ImExPS/2 Generic Explorer Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    67.155] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input1/event1"
[    67.155] (II) XINPUT: Adding extended input device "ImExPS/2 Generic Explorer Mouse" (type: MOUSE, id 7)
[    67.155] (II) evdev: ImExPS/2 Generic Explorer Mouse: initialized for relative axes.
[    67.156] (**) ImExPS/2 Generic Explorer Mouse: (accel) keeping acceleration scheme 1
[    67.156] (**) ImExPS/2 Generic Explorer Mouse: (accel) acceleration profile 0
[    67.156] (**) ImExPS/2 Generic Explorer Mouse: (accel) acceleration factor: 2.000
[    67.156] (**) ImExPS/2 Generic Explorer Mouse: (accel) acceleration threshold: 4
[    67.172] (II) config/udev: Adding input device ImExPS/2 Generic Explorer Mouse (/dev/input/mouse0)
[    67.172] (II) No input driver specified, ignoring this device.
[    67.172] (II) This device may have been added with another device file.
[    67.351] (EE) FBDEV(0): FBIOBLANK: Invalid argument
[   667.372] (EE) FBDEV(0): FBIOBLANK: Invalid argument
[   667.372] (EE) FBDEV(0): FBIOBLANK: Invalid argument
[   667.378] (EE) FBDEV(0): FBIOBLANK: Invalid argument
[ 25068.241] (EE) FBDEV(0): FBIOBLANK: Invalid argument
[ 25668.178] (EE) FBDEV(0): FBIOBLANK: Invalid argument
[ 25668.178] (EE) FBDEV(0): FBIOBLANK: Invalid argument
[ 25668.183] (EE) FBDEV(0): FBIOBLANK: Invalid argument
[ 38326.162] (EE) FBDEV(0): FBIOBLANK: Invalid argument
[ 38365.624] (II) XKB: reuse xkmfile /var/lib/xkb/server-03AF3717FF3AB439A4BAABA686CCB40771CDF520.xkm
[ 38375.308] (EE) FBDEV(0): FBIOBLANK: Invalid argument
[ 38375.309] (EE) FBDEV(0): FBIOBLANK: Invalid argument




And, here is my xorg.conf:

> 
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@swio-display-x86-rh72-02.nvidia.com)  Tue Sep 11 12:34:48 PDT 2012


# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 295.33  (buildd@zirconium)  Fri Mar 30 13:38:49 UTC 2012


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "1"
EndSection


Section "InputDevice"
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
    ModelName      "DELL E153FP"
    HorizSync       30.0 - 63.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection


Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "DELL E153FP"
    HorizSync       30.0 - 63.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
    # HorizSync source: edid, VertRefresh source: edid
EndSection


Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5500"
    BusID          "?@?:?:?"
    Screen          0
EndSection


Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5500"
    BusID          "?@?:?:?"
    Screen          1
EndSection


Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "CRT-0: nvidia-auto-select +0+0"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "CRT-1: nvidia-auto-select +0+0"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


---

### Post by danman1453 on 2013-03-11
Can someone point me in the right direction on how to interpret the xorg.0.log? I can probably stumble through it from there. Also, is there a recent write-up on the conf files in  /usr/share/X11/xorg.conf.d/?

---

### Post by gnice3d on 2013-05-18
Your twinview is disabled?

---

