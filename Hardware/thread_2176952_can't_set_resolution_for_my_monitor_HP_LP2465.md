---
title: "can't set resolution for my monitor HP LP2465"
date: 2013-09-26
forum: Hardware
---

### Post by danielsender on 2013-09-26
I posted the issue on "Desktop-Environments" without getting any answer there. Hopefully some wise guru can help me here. Here is the scoop:


[LIST]
[*]Ubuntu 12.04LTS 
[*]video card: NVIDIA GeForce FX 5600 Ultra 
[*]graphic driver: nvidia-173-updates 173.14.37 
[*]monitor: HP LP2465 
[/LIST]

The problem is that I can't set up the resolution beyond 1600x1200, although the monitor is a 1920x1200 and the graphic card is capable to do so. In fact if I boot XP (dual boot), then there is no problem.

These are the steps that I've gone through so far:


[LIST]
[*]me@foo: ~$ cvt 1920 1200 60 
[*]me@foo: ~$ xrandr --newmode "1920x1200_60.00" 193.25 1920 2056 2256 2592 1200 1203 1209 1245 -hsync +vsync 
[*]me@foo: ~$ xrandr --addmode default 1920x1200_60.0 
[/LIST]

So if I now open the "All settings"->"Displays" I can see in the "Resolution" drop-down menu the 1920x1200 option, however when I hit "Apply" it comes with the message:
```

The selected configuration for displays could not be applied
required virtual size does not fit available size: requested=(1920, 1200), minimum=(320, 240), maximum=(1600, 1200)

```
Is there any solution to this? I'm attaching the "Xorg.0.log" file.
```

[    28.055]
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    28.055] X Protocol Version 11, Revision 0
[    28.055] Build Operating System: Linux 2.6.42-37-generic i686 Ubuntu
[    28.055] Current Operating System: Linux grandpa 3.2.0-53-generic #81-Ubuntu SMP Thu Aug 22 21:03:54 UTC 2013 i686
[    28.068] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-53-generic root=UUID=042c75d3-6898-4e36-83de-299b0a729448 ro quiet splash
[    28.068] Build Date: 11 April 2013  01:04:30PM
[    28.068] xorg-server 2:1.11.4-0ubuntu10.13 (For technical support please see http://www.ubuntu.com/support)
[    28.068] Current version of pixman: 0.24.4
[    28.068]    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    28.068] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    28.068] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Sep 26 00:02:20 2013
[    28.069] (==) Using config file: "/etc/X11/xorg.conf"
[    28.069] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    28.082] (==) No Layout section.  Using the first Screen section.
[    28.082] (==) No screen section available. Using defaults.
[    28.082] (**) |-->Screen "Default Screen Section" (0)
[    28.083] (**) |   |-->Monitor "<default monitor>"
[    28.083] (==) No device specified for screen "Default Screen Section".
    Using the first device section listed.
[    28.083] (**) |   |-->Device "Default Device"
[    28.083] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    28.083] (==) Automatically adding devices
[    28.083] (==) Automatically enabling devices
[    28.091] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    28.091]    Entry deleted from font path.
[    28.091] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    28.091]    Entry deleted from font path.
[    28.091] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    28.091]    Entry deleted from font path.
[    28.093] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    28.093]    Entry deleted from font path.
[    28.093] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    28.093]    Entry deleted from font path.
[    28.093] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    28.093] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    28.093] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    28.093] (II) Loader magic: 0x8a45a0
[    28.093] (II) Module ABI versions:
[    28.093]    X.Org ANSI C Emulation: 0.4
[    28.093]    X.Org Video Driver: 11.0
[    28.093]    X.Org XInput driver : 16.0
[    28.093]    X.Org Server Extension : 6.0
[    28.095] (--) PCI:*(0:1:0:0) 10de:0311:0000:0000 rev 161, Mem @ 0xfd000000/16777216, 0xf0000000/134217728, BIOS @ 0x????????/131072
[    28.100] (II) Open ACPI successful (/var/run/acpid.socket)
[    28.100] (II) LoadModule: "extmod"
[    28.123] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    28.123] (II) Module extmod: vendor="X.Org Foundation"
[    28.123]    compiled for 1.11.3, module version = 1.0.0
[    28.123]    Module class: X.Org Server Extension
[    28.123]    ABI class: X.Org Server Extension, version 6.0
[    28.123] (II) Loading extension MIT-SCREEN-SAVER
[    28.123] (II) Loading extension XFree86-VidModeExtension
[    28.123] (II) Loading extension XFree86-DGA
[    28.124] (II) Loading extension DPMS
[    28.124] (II) Loading extension XVideo
[    28.124] (II) Loading extension XVideo-MotionCompensation
[    28.124] (II) Loading extension X-Resource
[    28.124] (II) LoadModule: "dbe"
[    28.125] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    28.125] (II) Module dbe: vendor="X.Org Foundation"
[    28.125]    compiled for 1.11.3, module version = 1.0.0
[    28.125]    Module class: X.Org Server Extension
[    28.125]    ABI class: X.Org Server Extension, version 6.0
[    28.125] (II) Loading extension DOUBLE-BUFFER
[    28.125] (II) LoadModule: "glx"
[    28.126] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/libglx.so
[    28.778] (II) Module glx: vendor="NVIDIA Corporation"
[    28.778]    compiled for 4.0.2, module version = 1.0.0
[    28.778]    Module class: X.Org Server Extension
[    28.778] (II) NVIDIA GLX Module  173.14.37  Wed Mar  6 17:14:50 PST 2013
[    28.778] (II) Loading extension GLX
[    28.778] (II) LoadModule: "record"
[    28.779] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    28.779] (II) Module record: vendor="X.Org Foundation"
[    28.779]    compiled for 1.11.3, module version = 1.13.0
[    28.779]    Module class: X.Org Server Extension
[    28.779]    ABI class: X.Org Server Extension, version 6.0
[    28.779] (II) Loading extension RECORD
[    28.779] (II) LoadModule: "dri"
[    28.795] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    28.795] (II) Module dri: vendor="X.Org Foundation"
[    28.795]    compiled for 1.11.3, module version = 1.0.0
[    28.795]    ABI class: X.Org Server Extension, version 6.0
[    28.795] (II) Loading extension XFree86-DRI
[    28.795] (II) LoadModule: "dri2"
[    28.805] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    28.805] (II) Module dri2: vendor="X.Org Foundation"
[    28.805]    compiled for 1.11.3, module version = 1.2.0
[    28.805]    ABI class: X.Org Server Extension, version 6.0
[    28.805] (II) Loading extension DRI2
[    28.805] (==) Matched nvidia as autoconfigured driver 0
[    28.805] (==) Matched nouveau as autoconfigured driver 1
[    28.805] (==) Matched nv as autoconfigured driver 2
[    28.805] (==) Matched vesa as autoconfigured driver 3
[    28.805] (==) Matched fbdev as autoconfigured driver 4
[    28.805] (==) Assigned the driver to the xf86ConfigLayout
[    28.805] (II) LoadModule: "nvidia"
[    28.806] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    28.834] (II) Module nvidia: vendor="NVIDIA Corporation"
[    28.834]    compiled for 4.0.2, module version = 1.0.0
[    28.834]    Module class: X.Org Video Driver
[    28.841] (II) LoadModule: "nouveau"
[    28.842] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    28.842] (II) Module nouveau: vendor="X.Org Foundation"
[    28.842]    compiled for 1.11.3, module version = 1.0.2
[    28.842]    Module class: X.Org Video Driver
[    28.842]    ABI class: X.Org Video Driver, version 11.0
[    28.843] (II) LoadModule: "nv"
[    28.847] (WW) Warning, couldn't open module nv
[    28.847] (II) UnloadModule: "nv"
[    28.847] (II) Unloading nv
[    28.847] (EE) Failed to load module "nv" (module does not exist, 0)
[    28.847] (II) LoadModule: "vesa"
[    28.852] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    28.852] (II) Module vesa: vendor="X.Org Foundation"
[    28.852]    compiled for 1.11.3, module version = 2.3.0
[    28.852]    Module class: X.Org Video Driver
[    28.852]    ABI class: X.Org Video Driver, version 11.0
[    28.853] (II) LoadModule: "fbdev"
[    28.853] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    28.854] (II) Module fbdev: vendor="X.Org Foundation"
[    28.854]    compiled for 1.11.3, module version = 0.4.2
[    28.854]    ABI class: X.Org Video Driver, version 11.0
[    28.854] (==) Matched nvidia as autoconfigured driver 0
[    28.854] (==) Matched nouveau as autoconfigured driver 1
[    28.854] (==) Matched nv as autoconfigured driver 2
[    28.854] (==) Matched vesa as autoconfigured driver 3
[    28.854] (==) Matched fbdev as autoconfigured driver 4
[    28.854] (==) Assigned the driver to the xf86ConfigLayout
[    28.854] (II) LoadModule: "nvidia"
[    28.854] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    28.854] (II) Module nvidia: vendor="NVIDIA Corporation"
[    28.854]    compiled for 4.0.2, module version = 1.0.0
[    28.854]    Module class: X.Org Video Driver
[    28.854] (II) UnloadModule: "nvidia"
[    28.854] (II) Unloading nvidia
[    28.854] (II) Failed to load module "nvidia" (already loaded, 8825723)
[    28.854] (II) LoadModule: "nouveau"
[    28.855] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    28.855] (II) Module nouveau: vendor="X.Org Foundation"
[    28.855]    compiled for 1.11.3, module version = 1.0.2
[    28.869]    Module class: X.Org Video Driver
[    28.869]    ABI class: X.Org Video Driver, version 11.0
[    28.869] (II) UnloadModule: "nouveau"
[    28.869] (II) Unloading nouveau
[    28.869] (II) Failed to load module "nouveau" (already loaded, 8825723)
[    28.869] (II) LoadModule: "nv"
[    28.870] (WW) Warning, couldn't open module nv
[    28.870] (II) UnloadModule: "nv"
[    28.870] (II) Unloading nv
[    28.870] (EE) Failed to load module "nv" (module does not exist, 0)
[    28.871] (II) LoadModule: "vesa"
[    28.871] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    28.871] (II) Module vesa: vendor="X.Org Foundation"
[    28.871]    compiled for 1.11.3, module version = 2.3.0
[    28.871]    Module class: X.Org Video Driver
[    28.887]    ABI class: X.Org Video Driver, version 11.0
[    28.887] (II) UnloadModule: "vesa"
[    28.887] (II) Unloading vesa
[    28.887] (II) Failed to load module "vesa" (already loaded, 0)
[    28.887] (II) LoadModule: "fbdev"
[    28.888] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    28.888] (II) Module fbdev: vendor="X.Org Foundation"
[    28.888]    compiled for 1.11.3, module version = 0.4.2
[    28.888]    ABI class: X.Org Video Driver, version 11.0
[    28.888] (II) UnloadModule: "fbdev"
[    28.888] (II) Unloading fbdev
[    28.888] (II) Failed to load module "fbdev" (already loaded, 0)
[    28.895] (II) NVIDIA dlloader X Driver  173.14.37  Wed Mar  6 17:02:37 PST 2013
[    28.895] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    28.895] (II) NOUVEAU driver Date:   Wed Sep 12 13:42:43 2012 +0200
[    28.895] (II) NOUVEAU driver for NVIDIA chipset families :
[    28.895]    RIVA TNT        (NV04)
[    28.896]    RIVA TNT2       (NV05)
[    28.896]    GeForce 256     (NV10)
[    28.896]    GeForce 2       (NV11, NV15)
[    28.896]    GeForce 4MX     (NV17, NV18)
[    28.896]    GeForce 3       (NV20)
[    28.896]    GeForce 4Ti     (NV25, NV28)
[    28.896]    GeForce FX      (NV3x)
[    28.896]    GeForce 6       (NV4x)
[    28.896]    GeForce 7       (G7x)
[    28.896]    GeForce 8       (G8x)
[    28.896]    GeForce GTX 200 (NVA0)
[    28.896]    GeForce GTX 400 (NVC0)
[    28.897] (II) VESA: driver for VESA chipsets: vesa
[    28.897] (II) FBDEV: driver for framebuffer: fbdev
[    28.897] (++) using VT number 7
[    28.899] (II) Loading sub module "fb"
[    28.899] (II) LoadModule: "fb"
[    28.900] (II) Loading /usr/lib/xorg/modules/libfb.so
[    28.901] (II) Module fb: vendor="X.Org Foundation"
[    28.901]    compiled for 1.11.3, module version = 1.0.0
[    28.901]    ABI class: X.Org ANSI C Emulation, version 0.4
[    28.901] (II) Loading sub module "wfb"
[    28.901] (II) LoadModule: "wfb"
[    28.902] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    28.914] (II) Module wfb: vendor="X.Org Foundation"
[    28.914]    compiled for 1.11.3, module version = 1.0.0
[    28.914]    ABI class: X.Org ANSI C Emulation, version 0.4
[    28.914] (II) Loading sub module "ramdac"
[    28.914] (II) LoadModule: "ramdac"
[    28.915] (II) Module "ramdac" already built-in
[    28.917] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    28.917] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    28.917] (II) Loading /usr/lib/xorg/modules/libfb.so
[    28.917] (WW) Falling back to old probe method for vesa
[    28.917] (WW) Falling back to old probe method for fbdev
[    28.917] (II) Loading sub module "fbdevhw"
[    28.917] (II) LoadModule: "fbdevhw"
[    28.918] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    28.918] (II) Module fbdevhw: vendor="X.Org Foundation"
[    28.919]    compiled for 1.11.3, module version = 0.0.2
[    28.919]    ABI class: X.Org Video Driver, version 11.0
[    28.919] (EE) open /dev/fb0: No such file or directory
[    28.920] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    28.920] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    28.920] (==) NVIDIA(0): RGB weight 888
[    28.920] (==) NVIDIA(0): Default visual is TrueColor
[    28.920] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    28.921] (**) NVIDIA(0): Option "NoLogo" "True"
[    28.923] (**) NVIDIA(0): Enabling RENDER acceleration
[    28.923] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[    28.923] (II) NVIDIA(0):     enabled.
[    30.181] (II) NVIDIA(0): NVIDIA GPU GeForce FX 5600 Ultra (NV31) at PCI:1:0:0 (GPU-0)
[    30.181] (--) NVIDIA(0): Memory: 131072 kBytes
[    30.181] (--) NVIDIA(0): VideoBIOS: 04.31.20.52.00
[    30.181] (II) NVIDIA(0): Detected AGP rate: 4X
[    30.181] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    30.181] (--) NVIDIA(0): Connected display device(s) on GeForce FX 5600 Ultra at
[    30.181] (--) NVIDIA(0):     PCI:1:0:0:
[    30.181] (--) NVIDIA(0):     HP LP2465 (DFP-0)
[    30.181] (--) NVIDIA(0): HP LP2465 (DFP-0): 140.4 MHz maximum pixel clock
[    30.181] (--) NVIDIA(0): HP LP2465 (DFP-0): Internal Single Link TMDS
[    30.183] (II) NVIDIA(0): Assigned Display Device: DFP-0
[    30.183] (==) NVIDIA(0):
[    30.183] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    30.183] (==) NVIDIA(0):     will be used as the requested mode.
[    30.183] (==) NVIDIA(0):
[    30.183] (II) NVIDIA(0): Validated modes:
[    30.183] (II) NVIDIA(0):     "nvidia-auto-select"
[    30.183] (II) NVIDIA(0): Virtual screen size determined to be 1600 x 1200
[    30.187] (--) NVIDIA(0): DPI set to (78, 92); computed from "UseEdidDpi" X config
[    30.187] (--) NVIDIA(0):     option
[    30.187] (==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
[    30.187] (II) UnloadModule: "nouveau"
[    30.187] (II) Unloading nouveau
[    30.187] (II) UnloadModule: "vesa"
[    30.187] (II) Unloading vesa
[    30.187] (II) UnloadModule: "fbdev"
[    30.187] (II) Unloading fbdev
[    30.187] (II) UnloadModule: "fbdevhw"
[    30.187] (II) Unloading fbdevhw
[    30.187] (--) Depth 24 pixmap format is 32 bpp
[    30.191] (II) NVIDIA(0): Initialized AGP GART.
[    30.206] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[    30.427] (II) Loading extension NV-GLX
[    30.574] (II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
[    30.600] (II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
[    30.600] (==) NVIDIA(0): Backing store disabled
[    30.600] (==) NVIDIA(0): Silken mouse enabled
[    30.601] (==) NVIDIA(0): DPMS enabled
[    30.601] (II) Loading extension NV-CONTROL
[    30.602] (==) RandR enabled
[    30.602] (II) Initializing built-in extension Generic Event Extension
[    30.602] (II) Initializing built-in extension SHAPE
[    30.602] (II) Initializing built-in extension MIT-SHM
[    30.602] (II) Initializing built-in extension XInputExtension
[    30.602] (II) Initializing built-in extension XTEST
[    30.602] (II) Initializing built-in extension BIG-REQUESTS
[    30.602] (II) Initializing built-in extension SYNC
[    30.602] (II) Initializing built-in extension XKEYBOARD
[    30.602] (II) Initializing built-in extension XC-MISC
[    30.603] (II) Initializing built-in extension SECURITY
[    30.603] (II) Initializing built-in extension XINERAMA
[    30.603] (II) Initializing built-in extension XFIXES
[    30.603] (II) Initializing built-in extension RENDER
[    30.603] (II) Initializing built-in extension RANDR
[    30.603] (II) Initializing built-in extension COMPOSITE
[    30.603] (II) Initializing built-in extension DAMAGE
[    30.626] (II) Initializing extension GLX
[    30.693] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    30.704] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    30.704] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    30.704] (II) LoadModule: "evdev"
[    30.706] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    30.706] (II) Module evdev: vendor="X.Org Foundation"
[    30.706]    compiled for 1.11.3, module version = 2.7.0
[    30.706]    Module class: X.Org XInput Driver
[    30.706]    ABI class: X.Org XInput driver, version 16.0
[    30.706] (II) Using input driver 'evdev' for 'Power Button'
[    30.706] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    30.707] (**) Power Button: always reports core events
[    30.707] (**) evdev: Power Button: Device: "/dev/input/event1"
[    30.707] (--) evdev: Power Button: Vendor 0 Product 0x1
[    30.707] (--) evdev: Power Button: Found keys
[    30.707] (II) evdev: Power Button: Configuring as keyboard
[    30.707] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    30.707] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    30.707] (**) Option "xkb_rules" "evdev"
[    30.707] (**) Option "xkb_model" "pc105"
[    30.707] (**) Option "xkb_layout" "us"
[    30.709] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    30.710] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    30.710] (II) Using input driver 'evdev' for 'Power Button'
[    30.710] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    30.710] (**) Power Button: always reports core events
[    30.710] (**) evdev: Power Button: Device: "/dev/input/event0"
[    30.710] (--) evdev: Power Button: Vendor 0 Product 0x1
[    30.710] (--) evdev: Power Button: Found keys
[    30.710] (II) evdev: Power Button: Configuring as keyboard
[    30.710] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    30.710] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    30.710] (**) Option "xkb_rules" "evdev"
[    30.710] (**) Option "xkb_model" "pc105"
[    30.710] (**) Option "xkb_layout" "us"
[    30.713] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event2)
[    30.713] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    30.713] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[    30.713] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    30.713] (**) Logitech USB Receiver: always reports core events
[    30.713] (**) evdev: Logitech USB Receiver: Device: "/dev/input/event2"
[    30.713] (--) evdev: Logitech USB Receiver: Vendor 0x46d Product 0xc505
[    30.713] (--) evdev: Logitech USB Receiver: Found keys
[    30.713] (II) evdev: Logitech USB Receiver: Configuring as keyboard
[    30.713] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1f.2/usb1/1-2/1-2:1.0/input/input2/event2"
[    30.714] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD, id 8)
[    30.714] (**) Option "xkb_rules" "evdev"
[    30.714] (**) Option "xkb_model" "pc105"
[    30.714] (**) Option "xkb_layout" "us"
[    30.716] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event3)
[    30.716] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[    30.717] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    30.717] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[    30.717] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    30.717] (**) Logitech USB Receiver: always reports core events
[    30.717] (**) evdev: Logitech USB Receiver: Device: "/dev/input/event3"
[    30.717] (--) evdev: Logitech USB Receiver: Vendor 0x46d Product 0xc505
[    30.717] (--) evdev: Logitech USB Receiver: Found 20 mouse buttons
[    30.717] (--) evdev: Logitech USB Receiver: Found scroll wheel(s)
[    30.717] (--) evdev: Logitech USB Receiver: Found relative axes
[    30.717] (--) evdev: Logitech USB Receiver: Found x and y relative axes
[    30.717] (--) evdev: Logitech USB Receiver: Found keys
[    30.717] (II) evdev: Logitech USB Receiver: Configuring as mouse
[    30.717] (II) evdev: Logitech USB Receiver: Configuring as keyboard
[    30.717] (II) evdev: Logitech USB Receiver: Adding scrollwheel support
[    30.717] (**) evdev: Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[    30.717] (**) evdev: Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    30.717] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1f.2/usb1/1-2/1-2:1.1/input/input3/event3"
[    30.717] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD, id 9)
[    30.717] (**) Option "xkb_rules" "evdev"
[    30.718] (**) Option "xkb_model" "pc105"
[    30.718] (**) Option "xkb_layout" "us"
[    30.718] (II) evdev: Logitech USB Receiver: initialized for relative axes.
[    30.719] (**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
[    30.719] (**) Logitech USB Receiver: (accel) acceleration profile 0
[    30.719] (**) Logitech USB Receiver: (accel) acceleration factor: 2.000
[    30.719] (**) Logitech USB Receiver: (accel) acceleration threshold: 4
[    30.720] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse0)
[    30.721] (II) No input driver specified, ignoring this device.
[    30.721] (II) This device may have been added with another device file.
[   150.640] (II) XKB: reuse xkmfile /var/lib/xkb/server-03AF3717FF3AB439A4BAABA686CCB40771CDF520.xkm

```

Many thanks in advance,

Daniel

---

### Post by Yellow Pasque on 2013-09-26
That's what's holding you back:
```
[    30.183] (II) NVIDIA(0): Virtual screen size determined to be 1600 x 1200
```
I'm not real familiar with nvidia using xorg.conf, so let's google together...

---

### Post by danielsender on 2013-09-26
> **danielsender said:**
> I posted the issue on "Desktop-Environments" without getting any answer there. Hopefully some wise guru can help me here. Here is the scoop:


[LIST]
[*]Ubuntu 12.04LTS 
[*]video card: NVIDIA GeForce FX 5600 Ultra 
[*]graphic driver: nvidia-173-updates 173.14.37 
[*]monitor: HP LP2465 
[/LIST]

The problem is that I can't set up the resolution beyond 1600x1200, although the monitor is a 1920x1200 and the graphic card is capable to do so. In fact if I boot XP (dual boot), then there is no problem.

These are the steps that I've gone through so far:


[LIST]
[*]me@foo: ~$ cvt 1920 1200 60 
[*]me@foo: ~$ xrandr --newmode "1920x1200_60.00" 193.25 1920 2056 2256 2592 1200 1203 1209 1245 -hsync +vsync 
[*]me@foo: ~$ xrandr --addmode default 1920x1200_60.0 
[/LIST]

So if I now open the "All settings"->"Displays" I can see in the "Resolution" drop-down menu the 1920x1200 option, however when I hit "Apply" it comes with the message:
```

The selected configuration for displays could not be applied
required virtual size does not fit available size: requested=(1920, 1200), minimum=(320, 240), maximum=(1600, 1200)

```
Is there any solution to this? I'm attaching the "Xorg.0.log" file.
```

[    28.055]
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    28.055] X Protocol Version 11, Revision 0
[    28.055] Build Operating System: Linux 2.6.42-37-generic i686 Ubuntu
[    28.055] Current Operating System: Linux grandpa 3.2.0-53-generic #81-Ubuntu SMP Thu Aug 22 21:03:54 UTC 2013 i686
[    28.068] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-53-generic root=UUID=042c75d3-6898-4e36-83de-299b0a729448 ro quiet splash
[    28.068] Build Date: 11 April 2013  01:04:30PM
[    28.068] xorg-server 2:1.11.4-0ubuntu10.13 (For technical support please see http://www.ubuntu.com/support)
[    28.068] Current version of pixman: 0.24.4
[    28.068]    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    28.068] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    28.068] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Sep 26 00:02:20 2013
[    28.069] (==) Using config file: "/etc/X11/xorg.conf"
[    28.069] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    28.082] (==) No Layout section.  Using the first Screen section.
[    28.082] (==) No screen section available. Using defaults.
[    28.082] (**) |-->Screen "Default Screen Section" (0)
[    28.083] (**) |   |-->Monitor "<default monitor>"
[    28.083] (==) No device specified for screen "Default Screen Section".
    Using the first device section listed.
[    28.083] (**) |   |-->Device "Default Device"
[    28.083] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    28.083] (==) Automatically adding devices
[    28.083] (==) Automatically enabling devices
[    28.091] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    28.091]    Entry deleted from font path.
[    28.091] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    28.091]    Entry deleted from font path.
[    28.091] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    28.091]    Entry deleted from font path.
[    28.093] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    28.093]    Entry deleted from font path.
[    28.093] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    28.093]    Entry deleted from font path.
[    28.093] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    28.093] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    28.093] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    28.093] (II) Loader magic: 0x8a45a0
[    28.093] (II) Module ABI versions:
[    28.093]    X.Org ANSI C Emulation: 0.4
[    28.093]    X.Org Video Driver: 11.0
[    28.093]    X.Org XInput driver : 16.0
[    28.093]    X.Org Server Extension : 6.0
[    28.095] (--) PCI:*(0:1:0:0) 10de:0311:0000:0000 rev 161, Mem @ 0xfd000000/16777216, 0xf0000000/134217728, BIOS @ 0x????????/131072
[    28.100] (II) Open ACPI successful (/var/run/acpid.socket)
[    28.100] (II) LoadModule: "extmod"
[    28.123] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    28.123] (II) Module extmod: vendor="X.Org Foundation"
[    28.123]    compiled for 1.11.3, module version = 1.0.0
[    28.123]    Module class: X.Org Server Extension
[    28.123]    ABI class: X.Org Server Extension, version 6.0
[    28.123] (II) Loading extension MIT-SCREEN-SAVER
[    28.123] (II) Loading extension XFree86-VidModeExtension
[    28.123] (II) Loading extension XFree86-DGA
[    28.124] (II) Loading extension DPMS
[    28.124] (II) Loading extension XVideo
[    28.124] (II) Loading extension XVideo-MotionCompensation
[    28.124] (II) Loading extension X-Resource
[    28.124] (II) LoadModule: "dbe"
[    28.125] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    28.125] (II) Module dbe: vendor="X.Org Foundation"
[    28.125]    compiled for 1.11.3, module version = 1.0.0
[    28.125]    Module class: X.Org Server Extension
[    28.125]    ABI class: X.Org Server Extension, version 6.0
[    28.125] (II) Loading extension DOUBLE-BUFFER
[    28.125] (II) LoadModule: "glx"
[    28.126] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/libglx.so
[    28.778] (II) Module glx: vendor="NVIDIA Corporation"
[    28.778]    compiled for 4.0.2, module version = 1.0.0
[    28.778]    Module class: X.Org Server Extension
[    28.778] (II) NVIDIA GLX Module  173.14.37  Wed Mar  6 17:14:50 PST 2013
[    28.778] (II) Loading extension GLX
[    28.778] (II) LoadModule: "record"
[    28.779] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    28.779] (II) Module record: vendor="X.Org Foundation"
[    28.779]    compiled for 1.11.3, module version = 1.13.0
[    28.779]    Module class: X.Org Server Extension
[    28.779]    ABI class: X.Org Server Extension, version 6.0
[    28.779] (II) Loading extension RECORD
[    28.779] (II) LoadModule: "dri"
[    28.795] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    28.795] (II) Module dri: vendor="X.Org Foundation"
[    28.795]    compiled for 1.11.3, module version = 1.0.0
[    28.795]    ABI class: X.Org Server Extension, version 6.0
[    28.795] (II) Loading extension XFree86-DRI
[    28.795] (II) LoadModule: "dri2"
[    28.805] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    28.805] (II) Module dri2: vendor="X.Org Foundation"
[    28.805]    compiled for 1.11.3, module version = 1.2.0
[    28.805]    ABI class: X.Org Server Extension, version 6.0
[    28.805] (II) Loading extension DRI2
[    28.805] (==) Matched nvidia as autoconfigured driver 0
[    28.805] (==) Matched nouveau as autoconfigured driver 1
[    28.805] (==) Matched nv as autoconfigured driver 2
[    28.805] (==) Matched vesa as autoconfigured driver 3
[    28.805] (==) Matched fbdev as autoconfigured driver 4
[    28.805] (==) Assigned the driver to the xf86ConfigLayout
[    28.805] (II) LoadModule: "nvidia"
[    28.806] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    28.834] (II) Module nvidia: vendor="NVIDIA Corporation"
[    28.834]    compiled for 4.0.2, module version = 1.0.0
[    28.834]    Module class: X.Org Video Driver
[    28.841] (II) LoadModule: "nouveau"
[    28.842] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    28.842] (II) Module nouveau: vendor="X.Org Foundation"
[    28.842]    compiled for 1.11.3, module version = 1.0.2
[    28.842]    Module class: X.Org Video Driver
[    28.842]    ABI class: X.Org Video Driver, version 11.0
[    28.843] (II) LoadModule: "nv"
[    28.847] (WW) Warning, couldn't open module nv
[    28.847] (II) UnloadModule: "nv"
[    28.847] (II) Unloading nv
[    28.847] (EE) Failed to load module "nv" (module does not exist, 0)
[    28.847] (II) LoadModule: "vesa"
[    28.852] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    28.852] (II) Module vesa: vendor="X.Org Foundation"
[    28.852]    compiled for 1.11.3, module version = 2.3.0
[    28.852]    Module class: X.Org Video Driver
[    28.852]    ABI class: X.Org Video Driver, version 11.0
[    28.853] (II) LoadModule: "fbdev"
[    28.853] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    28.854] (II) Module fbdev: vendor="X.Org Foundation"
[    28.854]    compiled for 1.11.3, module version = 0.4.2
[    28.854]    ABI class: X.Org Video Driver, version 11.0
[    28.854] (==) Matched nvidia as autoconfigured driver 0
[    28.854] (==) Matched nouveau as autoconfigured driver 1
[    28.854] (==) Matched nv as autoconfigured driver 2
[    28.854] (==) Matched vesa as autoconfigured driver 3
[    28.854] (==) Matched fbdev as autoconfigured driver 4
[    28.854] (==) Assigned the driver to the xf86ConfigLayout
[    28.854] (II) LoadModule: "nvidia"
[    28.854] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    28.854] (II) Module nvidia: vendor="NVIDIA Corporation"
[    28.854]    compiled for 4.0.2, module version = 1.0.0
[    28.854]    Module class: X.Org Video Driver
[    28.854] (II) UnloadModule: "nvidia"
[    28.854] (II) Unloading nvidia
[    28.854] (II) Failed to load module "nvidia" (already loaded, 8825723)
[    28.854] (II) LoadModule: "nouveau"
[    28.855] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    28.855] (II) Module nouveau: vendor="X.Org Foundation"
[    28.855]    compiled for 1.11.3, module version = 1.0.2
[    28.869]    Module class: X.Org Video Driver
[    28.869]    ABI class: X.Org Video Driver, version 11.0
[    28.869] (II) UnloadModule: "nouveau"
[    28.869] (II) Unloading nouveau
[    28.869] (II) Failed to load module "nouveau" (already loaded, 8825723)
[    28.869] (II) LoadModule: "nv"
[    28.870] (WW) Warning, couldn't open module nv
[    28.870] (II) UnloadModule: "nv"
[    28.870] (II) Unloading nv
[    28.870] (EE) Failed to load module "nv" (module does not exist, 0)
[    28.871] (II) LoadModule: "vesa"
[    28.871] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    28.871] (II) Module vesa: vendor="X.Org Foundation"
[    28.871]    compiled for 1.11.3, module version = 2.3.0
[    28.871]    Module class: X.Org Video Driver
[    28.887]    ABI class: X.Org Video Driver, version 11.0
[    28.887] (II) UnloadModule: "vesa"
[    28.887] (II) Unloading vesa
[    28.887] (II) Failed to load module "vesa" (already loaded, 0)
[    28.887] (II) LoadModule: "fbdev"
[    28.888] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    28.888] (II) Module fbdev: vendor="X.Org Foundation"
[    28.888]    compiled for 1.11.3, module version = 0.4.2
[    28.888]    ABI class: X.Org Video Driver, version 11.0
[    28.888] (II) UnloadModule: "fbdev"
[    28.888] (II) Unloading fbdev
[    28.888] (II) Failed to load module "fbdev" (already loaded, 0)
[    28.895] (II) NVIDIA dlloader X Driver  173.14.37  Wed Mar  6 17:02:37 PST 2013
[    28.895] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    28.895] (II) NOUVEAU driver Date:   Wed Sep 12 13:42:43 2012 +0200
[    28.895] (II) NOUVEAU driver for NVIDIA chipset families :
[    28.895]    RIVA TNT        (NV04)
[    28.896]    RIVA TNT2       (NV05)
[    28.896]    GeForce 256     (NV10)
[    28.896]    GeForce 2       (NV11, NV15)
[    28.896]    GeForce 4MX     (NV17, NV18)
[    28.896]    GeForce 3       (NV20)
[    28.896]    GeForce 4Ti     (NV25, NV28)
[    28.896]    GeForce FX      (NV3x)
[    28.896]    GeForce 6       (NV4x)
[    28.896]    GeForce 7       (G7x)
[    28.896]    GeForce 8       (G8x)
[    28.896]    GeForce GTX 200 (NVA0)
[    28.896]    GeForce GTX 400 (NVC0)
[    28.897] (II) VESA: driver for VESA chipsets: vesa
[    28.897] (II) FBDEV: driver for framebuffer: fbdev
[    28.897] (++) using VT number 7
[    28.899] (II) Loading sub module "fb"
[    28.899] (II) LoadModule: "fb"
[    28.900] (II) Loading /usr/lib/xorg/modules/libfb.so
[    28.901] (II) Module fb: vendor="X.Org Foundation"
[    28.901]    compiled for 1.11.3, module version = 1.0.0
[    28.901]    ABI class: X.Org ANSI C Emulation, version 0.4
[    28.901] (II) Loading sub module "wfb"
[    28.901] (II) LoadModule: "wfb"
[    28.902] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    28.914] (II) Module wfb: vendor="X.Org Foundation"
[    28.914]    compiled for 1.11.3, module version = 1.0.0
[    28.914]    ABI class: X.Org ANSI C Emulation, version 0.4
[    28.914] (II) Loading sub module "ramdac"
[    28.914] (II) LoadModule: "ramdac"
[    28.915] (II) Module "ramdac" already built-in
[    28.917] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    28.917] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    28.917] (II) Loading /usr/lib/xorg/modules/libfb.so
[    28.917] (WW) Falling back to old probe method for vesa
[    28.917] (WW) Falling back to old probe method for fbdev
[    28.917] (II) Loading sub module "fbdevhw"
[    28.917] (II) LoadModule: "fbdevhw"
[    28.918] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    28.918] (II) Module fbdevhw: vendor="X.Org Foundation"
[    28.919]    compiled for 1.11.3, module version = 0.0.2
[    28.919]    ABI class: X.Org Video Driver, version 11.0
[    28.919] (EE) open /dev/fb0: No such file or directory
[    28.920] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    28.920] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    28.920] (==) NVIDIA(0): RGB weight 888
[    28.920] (==) NVIDIA(0): Default visual is TrueColor
[    28.920] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    28.921] (**) NVIDIA(0): Option "NoLogo" "True"
[    28.923] (**) NVIDIA(0): Enabling RENDER acceleration
[    28.923] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[    28.923] (II) NVIDIA(0):     enabled.
[    30.181] (II) NVIDIA(0): NVIDIA GPU GeForce FX 5600 Ultra (NV31) at PCI:1:0:0 (GPU-0)
[    30.181] (--) NVIDIA(0): Memory: 131072 kBytes
[    30.181] (--) NVIDIA(0): VideoBIOS: 04.31.20.52.00
[    30.181] (II) NVIDIA(0): Detected AGP rate: 4X
[    30.181] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    30.181] (--) NVIDIA(0): Connected display device(s) on GeForce FX 5600 Ultra at
[    30.181] (--) NVIDIA(0):     PCI:1:0:0:
[    30.181] (--) NVIDIA(0):     HP LP2465 (DFP-0)
[    30.181] (--) NVIDIA(0): HP LP2465 (DFP-0): 140.4 MHz maximum pixel clock
[    30.181] (--) NVIDIA(0): HP LP2465 (DFP-0): Internal Single Link TMDS
[    30.183] (II) NVIDIA(0): Assigned Display Device: DFP-0
[    30.183] (==) NVIDIA(0):
[    30.183] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    30.183] (==) NVIDIA(0):     will be used as the requested mode.
[    30.183] (==) NVIDIA(0):
[    30.183] (II) NVIDIA(0): Validated modes:
[    30.183] (II) NVIDIA(0):     "nvidia-auto-select"
[    30.183] (II) NVIDIA(0): Virtual screen size determined to be 1600 x 1200
[    30.187] (--) NVIDIA(0): DPI set to (78, 92); computed from "UseEdidDpi" X config
[    30.187] (--) NVIDIA(0):     option
[    30.187] (==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
[    30.187] (II) UnloadModule: "nouveau"
[    30.187] (II) Unloading nouveau
[    30.187] (II) UnloadModule: "vesa"
[    30.187] (II) Unloading vesa
[    30.187] (II) UnloadModule: "fbdev"
[    30.187] (II) Unloading fbdev
[    30.187] (II) UnloadModule: "fbdevhw"
[    30.187] (II) Unloading fbdevhw
[    30.187] (--) Depth 24 pixmap format is 32 bpp
[    30.191] (II) NVIDIA(0): Initialized AGP GART.
[    30.206] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[    30.427] (II) Loading extension NV-GLX
[    30.574] (II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
[    30.600] (II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
[    30.600] (==) NVIDIA(0): Backing store disabled
[    30.600] (==) NVIDIA(0): Silken mouse enabled
[    30.601] (==) NVIDIA(0): DPMS enabled
[    30.601] (II) Loading extension NV-CONTROL
[    30.602] (==) RandR enabled
[    30.602] (II) Initializing built-in extension Generic Event Extension
[    30.602] (II) Initializing built-in extension SHAPE
[    30.602] (II) Initializing built-in extension MIT-SHM
[    30.602] (II) Initializing built-in extension XInputExtension
[    30.602] (II) Initializing built-in extension XTEST
[    30.602] (II) Initializing built-in extension BIG-REQUESTS
[    30.602] (II) Initializing built-in extension SYNC
[    30.602] (II) Initializing built-in extension XKEYBOARD
[    30.602] (II) Initializing built-in extension XC-MISC
[    30.603] (II) Initializing built-in extension SECURITY
[    30.603] (II) Initializing built-in extension XINERAMA
[    30.603] (II) Initializing built-in extension XFIXES
[    30.603] (II) Initializing built-in extension RENDER
[    30.603] (II) Initializing built-in extension RANDR
[    30.603] (II) Initializing built-in extension COMPOSITE
[    30.603] (II) Initializing built-in extension DAMAGE
[    30.626] (II) Initializing extension GLX
[    30.693] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    30.704] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    30.704] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    30.704] (II) LoadModule: "evdev"
[    30.706] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    30.706] (II) Module evdev: vendor="X.Org Foundation"
[    30.706]    compiled for 1.11.3, module version = 2.7.0
[    30.706]    Module class: X.Org XInput Driver
[    30.706]    ABI class: X.Org XInput driver, version 16.0
[    30.706] (II) Using input driver 'evdev' for 'Power Button'
[    30.706] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    30.707] (**) Power Button: always reports core events
[    30.707] (**) evdev: Power Button: Device: "/dev/input/event1"
[    30.707] (--) evdev: Power Button: Vendor 0 Product 0x1
[    30.707] (--) evdev: Power Button: Found keys
[    30.707] (II) evdev: Power Button: Configuring as keyboard
[    30.707] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    30.707] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    30.707] (**) Option "xkb_rules" "evdev"
[    30.707] (**) Option "xkb_model" "pc105"
[    30.707] (**) Option "xkb_layout" "us"
[    30.709] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    30.710] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    30.710] (II) Using input driver 'evdev' for 'Power Button'
[    30.710] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    30.710] (**) Power Button: always reports core events
[    30.710] (**) evdev: Power Button: Device: "/dev/input/event0"
[    30.710] (--) evdev: Power Button: Vendor 0 Product 0x1
[    30.710] (--) evdev: Power Button: Found keys
[    30.710] (II) evdev: Power Button: Configuring as keyboard
[    30.710] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    30.710] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    30.710] (**) Option "xkb_rules" "evdev"
[    30.710] (**) Option "xkb_model" "pc105"
[    30.710] (**) Option "xkb_layout" "us"
[    30.713] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event2)
[    30.713] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    30.713] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[    30.713] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    30.713] (**) Logitech USB Receiver: always reports core events
[    30.713] (**) evdev: Logitech USB Receiver: Device: "/dev/input/event2"
[    30.713] (--) evdev: Logitech USB Receiver: Vendor 0x46d Product 0xc505
[    30.713] (--) evdev: Logitech USB Receiver: Found keys
[    30.713] (II) evdev: Logitech USB Receiver: Configuring as keyboard
[    30.713] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1f.2/usb1/1-2/1-2:1.0/input/input2/event2"
[    30.714] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD, id 8)
[    30.714] (**) Option "xkb_rules" "evdev"
[    30.714] (**) Option "xkb_model" "pc105"
[    30.714] (**) Option "xkb_layout" "us"
[    30.716] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event3)
[    30.716] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[    30.717] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    30.717] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[    30.717] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    30.717] (**) Logitech USB Receiver: always reports core events
[    30.717] (**) evdev: Logitech USB Receiver: Device: "/dev/input/event3"
[    30.717] (--) evdev: Logitech USB Receiver: Vendor 0x46d Product 0xc505
[    30.717] (--) evdev: Logitech USB Receiver: Found 20 mouse buttons
[    30.717] (--) evdev: Logitech USB Receiver: Found scroll wheel(s)
[    30.717] (--) evdev: Logitech USB Receiver: Found relative axes
[    30.717] (--) evdev: Logitech USB Receiver: Found x and y relative axes
[    30.717] (--) evdev: Logitech USB Receiver: Found keys
[    30.717] (II) evdev: Logitech USB Receiver: Configuring as mouse
[    30.717] (II) evdev: Logitech USB Receiver: Configuring as keyboard
[    30.717] (II) evdev: Logitech USB Receiver: Adding scrollwheel support
[    30.717] (**) evdev: Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[    30.717] (**) evdev: Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    30.717] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1f.2/usb1/1-2/1-2:1.1/input/input3/event3"
[    30.717] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD, id 9)
[    30.717] (**) Option "xkb_rules" "evdev"
[    30.718] (**) Option "xkb_model" "pc105"
[    30.718] (**) Option "xkb_layout" "us"
[    30.718] (II) evdev: Logitech USB Receiver: initialized for relative axes.
[    30.719] (**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
[    30.719] (**) Logitech USB Receiver: (accel) acceleration profile 0
[    30.719] (**) Logitech USB Receiver: (accel) acceleration factor: 2.000
[    30.719] (**) Logitech USB Receiver: (accel) acceleration threshold: 4
[    30.720] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse0)
[    30.721] (II) No input driver specified, ignoring this device.
[    30.721] (II) This device may have been added with another device file.
[   150.640] (II) XKB: reuse xkmfile /var/lib/xkb/server-03AF3717FF3AB439A4BAABA686CCB40771CDF520.xkm

```

Many thanks in advance,

Daniel

I found the solution, look into: [http://askubuntu.com/questions/186288/how-to-detect-and-configure-an-output-with-xrandr](http://askubuntu.com/questions/186288/how-to-detect-and-configure-an-output-with-xrandr) , where I got the following lines for my xorg.conf:
```

Section "Screen"
     Identifier "My Screen"
    Subsection "Display"
        Virtual 1920 1200
    EndSubSection
EndSection
```

This method does not require to use xrandr, the new resolution will appear in the "Displays" GUI and pressing "Apply" will infact set it properly.

Cheers,

Daniel

---

### Post by Yellow Pasque on 2013-09-26
EDIT: Glad you found the same solution I did (and much faster too since I'm multitasking).

---

### Post by danielsender on 2013-09-29
Actually I just realised that something is not right. The "Display" GUI shows that I have 1920x1200 resolution, but the control in the monitor says that it is receiving 1600x1200, which is consistent with what I'm seeing in the screen, the image is stretched and it slides within the actual screen to "complete" the 1920 pixels in width when I click the left button in the mouse. I don't understand if the entry in the xorg.conf file related with "virtual" is just an allowed resolution but not actually set in the driver. Can someone explain please?

Thanks.

---

