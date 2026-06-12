---
title: "Display resolution issues"
date: 2011-06-06
forum: Hardware
---

### Post by klownish on 2011-06-06
I am having an issue with my display (32" panasonic TV (TCL32X1)) connected via HDMI to my nvidia gtx 260 .  I am running 11.04, 64bit  classic.  The issues i am having are, my screen is running off the sides, I cannot see my task bars fully (I can partially see them, so I know they are there).  I have searched and searched for help for this, and have sat on IRC (#ubuntu) looking for help.  I have been told that "xrandr" will fix the issue, but its not, keeps telling me "output "blah" not found, ignoring.  I've tried several different resolutions, same issue.  xrandr --verbose | parse-edid tells me the EDID it is using, is wrong, and not to trust the output.  I have also tried adjusting the /etc/X11/xorg.conf files, and nothing there.  I am out of ideas.  Any help would be greatly appreciated.  (attached is the /var/log/Xorg.0.log, maybe it will help someone figure something out, and also, my *stock* /etc/X11/xorg.conf) 

/var/log/Xorg.0.log
```


[    14.347] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    14.347] X Protocol Version 11, Revision 0
[    14.347] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[    14.347] Current Operating System: Linux klown-desktop 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64
[    14.347] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=30889fa0-b27e-48b1-a8b6-462d862bfd1b ro quiet splash vt.handoff=7
[    14.347] Build Date: 21 May 2011  11:48:41AM
[    14.347] xorg-server 2:1.10.1-1ubuntu1.1 (For technical support please see http://www.ubuntu.com/support) 
[    14.347] Current version of pixman: 0.20.2
[    14.347]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    14.347] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    14.347] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Jun  6 09:13:43 2011
[    14.427] (==) Using config file: "/etc/X11/xorg.conf"
[    14.427] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    14.493] (==) ServerLayout "Layout0"
[    14.493] (**) |-->Screen "Screen0" (0)
[    14.493] (**) |   |-->Monitor "Monitor0"
[    14.494] (**) |   |-->Device "Device0"
[    14.494] (**) |-->Input Device "Keyboard0"
[    14.494] (**) |-->Input Device "Mouse0"
[    14.494] (**) Option "Xinerama" "0"
[    14.494] (==) Automatically adding devices
[    14.494] (==) Automatically enabling devices
[    14.495] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    14.495]     Entry deleted from font path.
[    14.495] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    14.495]     Entry deleted from font path.
[    14.512] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    14.512]     Entry deleted from font path.
[    14.532] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    14.532] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    14.532] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    14.532] (WW) Disabling Keyboard0
[    14.532] (WW) Disabling Mouse0
[    14.532] (II) Loader magic: 0x7e0280
[    14.532] (II) Module ABI versions:
[    14.532]     X.Org ANSI C Emulation: 0.4
[    14.532]     X.Org Video Driver: 10.0
[    14.532]     X.Org XInput driver : 12.3
[    14.532]     X.Org Server Extension : 5.0
[    14.533] (--) PCI:*(0:1:0:0) 10de:05e2:3842:1257 rev 161, Mem @ 0xfd000000/16777216, 0xd0000000/268435456, 0xfa000000/33554432, I/O @ 0x0000a800/128, BIOS @ 0x????????/524288
[    14.533] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    14.533] (II) LoadModule: "extmod"
[    14.620] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    14.645] (II) Module extmod: vendor="X.Org Foundation"
[    14.645]     compiled for 1.10.1, module version = 1.0.0
[    14.645]     Module class: X.Org Server Extension
[    14.645]     ABI class: X.Org Server Extension, version 5.0
[    14.645] (II) Loading extension MIT-SCREEN-SAVER
[    14.645] (II) Loading extension XFree86-VidModeExtension
[    14.645] (II) Loading extension XFree86-DGA
[    14.645] (II) Loading extension DPMS
[    14.645] (II) Loading extension XVideo
[    14.645] (II) Loading extension XVideo-MotionCompensation
[    14.645] (II) Loading extension X-Resource
[    14.645] (II) LoadModule: "dbe"
[    14.645] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    14.646] (II) Module dbe: vendor="X.Org Foundation"
[    14.646]     compiled for 1.10.1, module version = 1.0.0
[    14.646]     Module class: X.Org Server Extension
[    14.646]     ABI class: X.Org Server Extension, version 5.0
[    14.646] (II) Loading extension DOUBLE-BUFFER
[    14.646] (II) LoadModule: "glx"
[    14.646] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    15.779] (II) Module glx: vendor="NVIDIA Corporation"
[    15.788]     compiled for 4.0.2, module version = 1.0.0
[    15.788]     Module class: X.Org Server Extension
[    15.788] (II) NVIDIA GLX Module  270.41.19  Mon May 16 23:48:30 PDT 2011
[    15.788] (II) Loading extension GLX
[    15.788] (II) LoadModule: "record"
[    15.788] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    15.789] (II) Module record: vendor="X.Org Foundation"
[    15.789]     compiled for 1.10.1, module version = 1.13.0
[    15.789]     Module class: X.Org Server Extension
[    15.789]     ABI class: X.Org Server Extension, version 5.0
[    15.789] (II) Loading extension RECORD
[    15.789] (II) LoadModule: "dri"
[    15.789] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    15.790] (II) Module dri: vendor="X.Org Foundation"
[    15.790]     compiled for 1.10.1, module version = 1.0.0
[    15.790]     ABI class: X.Org Server Extension, version 5.0
[    15.790] (II) Loading extension XFree86-DRI
[    15.790] (II) LoadModule: "dri2"
[    15.790] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    15.791] (II) Module dri2: vendor="X.Org Foundation"
[    15.791]     compiled for 1.10.1, module version = 1.2.0
[    15.791]     ABI class: X.Org Server Extension, version 5.0
[    15.791] (II) Loading extension DRI2
[    15.791] (II) LoadModule: "nvidia"
[    15.791] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    15.834] (II) Module nvidia: vendor="NVIDIA Corporation"
[    15.835]     compiled for 4.0.2, module version = 1.0.0
[    15.835]     Module class: X.Org Video Driver
[    15.896] (II) NVIDIA dlloader X Driver  270.41.19  Mon May 16 23:33:35 PDT 2011
[    15.896] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    15.897] (++) using VT number 7

[    15.898] (II) Loading sub module "fb"
[    15.898] (II) LoadModule: "fb"
[    15.898] (II) Loading /usr/lib/xorg/modules/libfb.so
[    15.905] (II) Module fb: vendor="X.Org Foundation"
[    15.905]     compiled for 1.10.1, module version = 1.0.0
[    15.905]     ABI class: X.Org ANSI C Emulation, version 0.4
[    15.905] (II) Loading sub module "wfb"
[    15.905] (II) LoadModule: "wfb"
[    15.905] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    15.918] (II) Module wfb: vendor="X.Org Foundation"
[    15.918]     compiled for 1.10.1, module version = 1.0.0
[    15.918]     ABI class: X.Org ANSI C Emulation, version 0.4
[    15.918] (II) Loading sub module "ramdac"
[    15.918] (II) LoadModule: "ramdac"
[    15.918] (II) Module "ramdac" already built-in
[    15.919] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    15.919] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    15.919] (II) Loading /usr/lib/xorg/modules/libfb.so
[    15.936] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    15.936] (==) NVIDIA(0): RGB weight 888
[    15.936] (==) NVIDIA(0): Default visual is TrueColor
[    15.936] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    15.936] (**) NVIDIA(0): Option "TwinView" "0"
[    15.936] (**) NVIDIA(0): Option "MetaModes" "960x600 +0+0"
[    17.499] (II) NVIDIA(GPU-0): Display (Panasonic-TV (DFP-0)) does not support NVIDIA 3D
[    17.554] (II) NVIDIA(GPU-0):     Vision stereo.
[    17.778] (II) NVIDIA(0): NVIDIA GPU GeForce GTX 260 (GT200) at PCI:1:0:0 (GPU-0)
[    17.778] (--) NVIDIA(0): Memory: 917504 kBytes
[    17.778] (--) NVIDIA(0): VideoBIOS: 62.00.4c.00.50
[    17.778] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    17.778] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    17.778] (--) NVIDIA(0): Connected display device(s) on GeForce GTX 260 at PCI:1:0:0
[    17.778] (--) NVIDIA(0):     Panasonic-TV (DFP-0)
[    17.778] (--) NVIDIA(0): Panasonic-TV (DFP-0): 330.0 MHz maximum pixel clock
[    17.778] (--) NVIDIA(0): Panasonic-TV (DFP-0): Internal Dual Link TMDS
[    17.878] (II) NVIDIA(0): Assigned Display Device: DFP-0
[    17.878] (II) NVIDIA(0): Validated modes:
[    17.878] (II) NVIDIA(0):     "960x600+0+0"
[    17.878] (II) NVIDIA(0): Virtual screen size determined to be 960 x 600
[    17.902] (WW) NVIDIA(0): Panasonic-TV (DFP-0)'s EDID does not contain a maximum image
[    17.902] (WW) NVIDIA(0):     size; cannot compute DPI from Panasonic-TV (DFP-0)'s
[    17.902] (WW) NVIDIA(0):     EDID.
[    17.902] (==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
[    17.902] (--) Depth 24 pixmap format is 32 bpp
[    17.902] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    17.905] (II) NVIDIA(0): Setting mode "960x600+0+0"
[    17.965] (II) Loading extension NV-GLX
[    18.083] (==) NVIDIA(0): Disabling shared memory pixmaps
[    18.084] (==) NVIDIA(0): Backing store disabled
[    18.084] (==) NVIDIA(0): Silken mouse enabled
[    18.085] (**) NVIDIA(0): DPMS enabled
[    18.090] (II) Loading extension NV-CONTROL
[    18.090] (II) Loading extension XINERAMA
[    18.090] (II) Loading sub module "dri2"
[    18.090] (II) LoadModule: "dri2"
[    18.090] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    18.090] (II) Module dri2: vendor="X.Org Foundation"
[    18.090]     compiled for 1.10.1, module version = 1.2.0
[    18.090]     ABI class: X.Org Server Extension, version 5.0
[    18.090] (II) NVIDIA(0): [DRI2] Setup complete
[    18.090] (==) RandR enabled
[    18.090] (II) Initializing built-in extension Generic Event Extension
[    18.090] (II) Initializing built-in extension SHAPE
[    18.090] (II) Initializing built-in extension MIT-SHM
[    18.090] (II) Initializing built-in extension XInputExtension
[    18.090] (II) Initializing built-in extension XTEST
[    18.090] (II) Initializing built-in extension BIG-REQUESTS
[    18.090] (II) Initializing built-in extension SYNC
[    18.090] (II) Initializing built-in extension XKEYBOARD
[    18.090] (II) Initializing built-in extension XC-MISC
[    18.091] (II) Initializing built-in extension SECURITY
[    18.091] (II) Initializing built-in extension XINERAMA
[    18.091] (II) Initializing built-in extension XFIXES
[    18.091] (II) Initializing built-in extension RENDER
[    18.091] (II) Initializing built-in extension RANDR
[    18.091] (II) Initializing built-in extension COMPOSITE
[    18.091] (II) Initializing built-in extension DAMAGE
[    18.091] (II) Initializing built-in extension GESTURE
[    18.092] (II) Initializing extension GLX
[    18.351] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    18.387] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    18.441] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    18.441] (II) LoadModule: "evdev"
[    18.442] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.548] (II) Module evdev: vendor="X.Org Foundation"
[    18.548]     compiled for 1.10.0.902, module version = 2.6.0
[    18.548]     Module class: X.Org XInput Driver
[    18.548]     ABI class: X.Org XInput driver, version 12.3
[    18.548] (II) Using input driver 'evdev' for 'Power Button'
[    18.548] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.548] (**) Power Button: always reports core events
[    18.548] (**) Power Button: Device: "/dev/input/event1"
[    18.580] (--) Power Button: Found keys
[    18.580] (II) Power Button: Configuring as keyboard
[    18.580] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    18.580] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    18.580] (**) Option "xkb_rules" "evdev"
[    18.580] (**) Option "xkb_model" "pc105"
[    18.580] (**) Option "xkb_layout" "us"
[    18.581] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    18.581] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    18.581] (II) Using input driver 'evdev' for 'Power Button'
[    18.581] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.581] (**) Power Button: always reports core events
[    18.582] (**) Power Button: Device: "/dev/input/event0"
[    18.630] (--) Power Button: Found keys
[    18.630] (II) Power Button: Configuring as keyboard
[    18.630] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    18.630] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    18.630] (**) Option "xkb_rules" "evdev"
[    18.630] (**) Option "xkb_model" "pc105"
[    18.630] (**) Option "xkb_layout" "us"
[    18.634] (II) config/udev: Adding input device Yealink usb-p1k (/dev/input/event7)
[    18.634] (**) Yealink usb-p1k: Applying InputClass "evdev keyboard catchall"
[    18.634] (II) Using input driver 'evdev' for 'Yealink usb-p1k'
[    18.634] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.634] (**) Yealink usb-p1k: always reports core events
[    18.634] (**) Yealink usb-p1k: Device: "/dev/input/event7"
[    18.670] (--) Yealink usb-p1k: Found keys
[    18.670] (II) Yealink usb-p1k: Configuring as keyboard
[    18.670] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.1/usb4/4-1/4-1:1.3/input/input7/event7"
[    18.670] (II) XINPUT: Adding extended input device "Yealink usb-p1k" (type: KEYBOARD)
[    18.670] (**) Option "xkb_rules" "evdev"
[    18.670] (**) Option "xkb_model" "pc105"
[    18.670] (**) Option "xkb_layout" "us"
[    18.671] (II) config/udev: Adding input device G15 Gaming Keyboard (/dev/input/event2)
[    18.671] (**) G15 Gaming Keyboard: Applying InputClass "evdev keyboard catchall"
[    18.671] (II) Using input driver 'evdev' for 'G15 Gaming Keyboard'
[    18.671] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.671] (**) G15 Gaming Keyboard: always reports core events
[    18.671] (**) G15 Gaming Keyboard: Device: "/dev/input/event2"
[    18.730] (--) G15 Gaming Keyboard: Found keys
[    18.730] (II) G15 Gaming Keyboard: Configuring as keyboard
[    18.730] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.1/usb4/4-2/4-2.1/4-2.1:1.0/input/input2/event2"
[    18.730] (II) XINPUT: Adding extended input device "G15 Gaming Keyboard" (type: KEYBOARD)
[    18.730] (**) Option "xkb_rules" "evdev"
[    18.730] (**) Option "xkb_model" "pc105"
[    18.730] (**) Option "xkb_layout" "us"
[    18.730] (II) config/udev: Adding input device G15 Gaming Keyboard (/dev/input/event3)
[    18.730] (**) G15 Gaming Keyboard: Applying InputClass "evdev keyboard catchall"
[    18.730] (II) Using input driver 'evdev' for 'G15 Gaming Keyboard'
[    18.730] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.730] (**) G15 Gaming Keyboard: always reports core events
[    18.730] (**) G15 Gaming Keyboard: Device: "/dev/input/event3"
[    18.770] (--) G15 Gaming Keyboard: Found keys
[    18.770] (II) G15 Gaming Keyboard: Configuring as keyboard
[    18.770] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.1/usb4/4-2/4-2.1/4-2.1:1.1/input/input3/event3"
[    18.770] (II) XINPUT: Adding extended input device "G15 Gaming Keyboard" (type: KEYBOARD)
[    18.770] (**) Option "xkb_rules" "evdev"
[    18.770] (**) Option "xkb_model" "pc105"
[    18.770] (**) Option "xkb_layout" "us"
[    18.770] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event4)
[    18.770] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[    18.770] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[    18.770] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.770] (**) Logitech USB Receiver: always reports core events
[    18.770] (**) Logitech USB Receiver: Device: "/dev/input/event4"
[    18.800] (--) Logitech USB Receiver: Found 20 mouse buttons
[    18.800] (--) Logitech USB Receiver: Found scroll wheel(s)
[    18.800] (--) Logitech USB Receiver: Found relative axes
[    18.800] (--) Logitech USB Receiver: Found x and y relative axes
[    18.800] (II) Logitech USB Receiver: Configuring as mouse
[    18.800] (II) Logitech USB Receiver: Adding scrollwheel support
[    18.800] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[    18.800] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    18.800] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.1/usb4/4-2/4-2.3/4-2.3:1.0/input/input4/event4"
[    18.800] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: MOUSE)
[    18.800] (II) Logitech USB Receiver: initialized for relative axes.
[    18.800] (**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
[    18.800] (**) Logitech USB Receiver: (accel) acceleration profile 0
[    18.800] (**) Logitech USB Receiver: (accel) acceleration factor: 2.000
[    18.800] (**) Logitech USB Receiver: (accel) acceleration threshold: 4
[    18.800] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse0)
[    18.800] (II) No input driver/identifier specified (ignoring)
[    18.801] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event5)
[    18.801] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    18.801] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[    18.801] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.801] (**) Logitech USB Receiver: always reports core events
[    18.801] (**) Logitech USB Receiver: Device: "/dev/input/event5"
[    18.830] (--) Logitech USB Receiver: Found 1 mouse buttons
[    18.929] (--) Logitech USB Receiver: Found scroll wheel(s)
[    18.929] (--) Logitech USB Receiver: Found relative axes
[    18.929] (--) Logitech USB Receiver: Found absolute axes
[    18.929] (II) evdev-grail: failed to open grail, no gesture support
[    18.929] (--) Logitech USB Receiver: Found keys
[    18.929] (II) Logitech USB Receiver: Configuring as mouse
[    18.929] (II) Logitech USB Receiver: Configuring as keyboard
[    18.929] (II) Logitech USB Receiver: Adding scrollwheel support
[    18.929] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[    18.929] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    18.929] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.1/usb4/4-2/4-2.3/4-2.3:1.1/input/input5/event5"
[    18.929] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[    18.929] (**) Option "xkb_rules" "evdev"
[    18.929] (**) Option "xkb_model" "pc105"
[    18.929] (**) Option "xkb_layout" "us"
[    18.929] (EE) Logitech USB Receiver: failed to initialize for relative axes.
[    18.929] (II) Logitech USB Receiver: initialized for absolute axes.
[    18.929] (**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
[    18.929] (**) Logitech USB Receiver: (accel) acceleration profile 0
[    18.929] (**) Logitech USB Receiver: (accel) acceleration factor: 2.000
[    18.929] (**) Logitech USB Receiver: (accel) acceleration threshold: 4
[    18.930] (II) config/udev: Adding input device G15 GamePanel LCD (/dev/input/event6)
[    18.930] (**) G15 GamePanel LCD: Applying InputClass "evdev keyboard catchall"
[    18.930] (II) Using input driver 'evdev' for 'G15 GamePanel LCD'
[    18.930] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.930] (**) G15 GamePanel LCD: always reports core events
[    18.930] (**) G15 GamePanel LCD: Device: "/dev/input/event6"
[    18.930] (--) G15 GamePanel LCD: Found keys
[    18.930] (II) G15 GamePanel LCD: Configuring as keyboard
[    18.930] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.1/usb4/4-2/4-2.4/4-2.4:1.0/input/input6/event6"
[    18.930] (II) XINPUT: Adding extended input device "G15 GamePanel LCD" (type: KEYBOARD)
[    18.930] (**) Option "xkb_rules" "evdev"
[    18.930] (**) Option "xkb_model" "pc105"
[    18.930] (**) Option "xkb_layout" "us"
[    18.935] (II) config/udev: Adding input device HDA ATI SB Headphone (/dev/input/event8)
[    18.935] (II) No input driver/identifier specified (ignoring)
[   151.172] (II) NVIDIA(0): Setting mode "960x540"
[   216.400] (II) XKB: generating xkmfile /var/lib/xkb/server-9A8405F3FE0A780485714A4B6DD41909C2CF9F83.xkm
[   237.493] (II) NVIDIA(0): Setting mode "960x540"
[   316.218] (II) NVIDIA(0): Setting mode "DFP-0:1920x1080@1920x1080+0+0"
[   332.284] (II) NVIDIA(0): Setting mode "DFP-0:1920x1080@1920x1080+0+0"
[   341.084] (II) NVIDIA(0): Setting mode "DFP-0:1920x1080@1920x1080+0+0"
[  1588.448] (II) NVIDIA(0): Setting mode "DFP-0:1280x720@1280x720+0+0"


```/etc/X11/xorg.conf
```


# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 270.29  (buildd@allspice)  Fri Feb 25 14:42:07 UTC 2011

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
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Panasonic-TV"
    HorizSync       15.0 - 45.0
    VertRefresh     59.0 - 61.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 260"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "960x600 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


```

---

### Post by ilcapo09 on 2011-06-08
I had a similar issue when I recently bought a 40" LCD TV. Tried what you said and still couldn't get it right.
Then I started fiddling with the TV setup and I found a menu that gave me an option of running it in the native resolution or 16:9 and thats what fixed my screen. Try looking into your tv's menus.

---

### Post by klownish on 2011-06-13
Tried that and no luck.  Anyone got any other ideas?

---

### Post by HermanTheBear on 2011-06-16
I've had similar issues, and I found that this mostly has to do with your TV. There are two fixes, one you could implement through the nVidia control panel, and the other through TV settings. The TV settings are easiest to change, and are more likely a permanent fix. 

Just go to your advanced options menu in the TV, or otherwise find where the option to turn overscan off is. When you find it, turn it to "normal" or off, and that should do the trick.

The other fix involves using the desktop size adjustment in the nVidia control panel, but you'll be setting it to a lower resolution and your computer may reset after rebooting. Try the above fix first, and then the second one.

Also, I just got Ubuntu yesterday so I'm not aware of any fix you can implement through the terminal. If one exists and it works better, then all the more power to that solution. Good luck!

---

