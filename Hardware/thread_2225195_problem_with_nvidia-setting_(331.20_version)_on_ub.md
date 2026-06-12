---
title: "problem with nvidia-setting (331.20 version) on ubuntu 12.04 / Dual monitor problem"
date: 2014-05-20
forum: Hardware
---

### Post by arman2 on 2014-05-20
Hi.

I have recently installed ubuntu 12.04 on my Thinkpad T61 laptop. I am unable to run nvidia-setting command and because of that to have a dual monitor or projector. I just installed the latest option on "restricted driver" window when it suggested me some similar drivers. I have no clue why it is not working. :( whenever I also open "Displays" window under settings to control my other monitors, it can not detect any other display device.

2 days ago it was working for me on ubuntu 12.04 and I had to re-install my OS because of some other issues. Can somebody please help me to resolve this issue?
(I searched similar threads but non of them worked for me.)

This is the output of some related commands in Terminal.
[B]
$ nvidia-settings 
[/B]> 
ERROR: Error querying target relations




ERROR: Error querying target relations




ERROR: Error querying target relations




ERROR: Error querying target relations




ERROR: Error querying target relations


The program 'nvidia-settings' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadRequest (invalid request code or no such operation)'.
  (Details: serial 59 error_code 1 request_code 155 minor_code 29)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)





Here are some output of some commands in my system:

**$sudo dpkg -p nvidia-settings |grep Version**
> 
Version: 331.20-0ubuntu0.0.1




and 

**$  dpkg -l | grep nvidia**

> 
ii  nvidia-173                                 173.14.39-0ubuntu0.0.1              NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-common                              1:0.2.44.2                          Find obsolete NVIDIA drivers
ii  nvidia-settings                            331.20-0ubuntu0.0.1                 Tool for configuring the NVIDIA graphics driver


and 
**cat  /var/log/Xorg.0.log**
```

[    25.309] 
X.Org X Server 1.14.5
Release Date: 2013-12-12
[    25.309] X Protocol Version 11, Revision 0
[    25.309] Build Operating System: Linux 2.6.42-37-generic x86_64 Ubuntu
[    25.309] Current Operating System: Linux xyz 3.11.0-20-generic #35~precise1-Ubuntu SMP Fri May 2 21:32:55 UTC 2014 x86_64
[    25.309] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.11.0-20-generic root=UUID=a62368b9-e1a8-4867-bafc-9601d32f5a83 ro quiet splash vt.handoff=7
[    25.309] Build Date: 06 January 2014  01:37:48PM
[    25.309] xorg-server 2:1.14.5-1ubuntu2~saucy1~precise2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    25.309] Current version of pixman: 0.30.2
[    25.309]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    25.309] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    25.309] (==) Log file: "/var/log/Xorg.0.log", Time: Tue May 20 12:47:19 2014
[    25.388] (==) Using config file: "/etc/X11/xorg.conf"
[    25.388] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    25.428] (==) ServerLayout "Layout0"
[    25.428] (**) |-->Screen "Screen0" (0)
[    25.428] (**) |   |-->Monitor "Monitor0"
[    25.435] (**) |   |-->Device "Device0"
[    25.435] (**) |-->Input Device "Keyboard0"
[    25.435] (**) |-->Input Device "Mouse0"
[    25.435] (==) Automatically adding devices
[    25.435] (==) Automatically enabling devices
[    25.435] (==) Automatically adding GPU devices
[    25.445] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    25.445]     Entry deleted from font path.
[    25.445] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    25.445]     Entry deleted from font path.
[    25.445] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    25.445]     Entry deleted from font path.
[    25.471] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    25.471]     Entry deleted from font path.
[    25.471] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    25.471]     Entry deleted from font path.
[    25.471] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    25.471] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    25.471] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    25.471] (WW) Disabling Keyboard0
[    25.471] (WW) Disabling Mouse0
[    25.486] (II) Loader magic: 0x7f6722f46c20
[    25.486] (II) Module ABI versions:
[    25.486]     X.Org ANSI C Emulation: 0.4
[    25.486]     X.Org Video Driver: 14.1
[    25.486]     X.Org XInput driver : 19.1
[    25.486]     X.Org Server Extension : 7.0
[    25.488] (--) PCI:*(0:1:0:0) 10de:0429:17aa:20d8 rev 161, Mem @ 0xd6000000/16777216, 0xe0000000/268435456, 0xd4000000/33554432, I/O @ 0x00002000/128
[    25.488] (II) Open ACPI successful (/var/run/acpid.socket)
[    25.489] Initializing built-in extension Generic Event Extension
[    25.489] Initializing built-in extension SHAPE
[    25.489] Initializing built-in extension MIT-SHM
[    25.489] Initializing built-in extension XInputExtension
[    25.489] Initializing built-in extension XTEST
[    25.489] Initializing built-in extension BIG-REQUESTS
[    25.489] Initializing built-in extension SYNC
[    25.489] Initializing built-in extension XKEYBOARD
[    25.489] Initializing built-in extension XC-MISC
[    25.489] Initializing built-in extension SECURITY
[    25.489] Initializing built-in extension XINERAMA
[    25.489] Initializing built-in extension XFIXES
[    25.489] Initializing built-in extension RENDER
[    25.489] Initializing built-in extension RANDR
[    25.489] Initializing built-in extension COMPOSITE
[    25.489] Initializing built-in extension DAMAGE
[    25.489] Initializing built-in extension MIT-SCREEN-SAVER
[    25.489] Initializing built-in extension DOUBLE-BUFFER
[    25.489] Initializing built-in extension RECORD
[    25.489] Initializing built-in extension DPMS
[    25.489] Initializing built-in extension X-Resource
[    25.489] Initializing built-in extension XVideo
[    25.489] Initializing built-in extension XVideo-MotionCompensation
[    25.489] Initializing built-in extension XFree86-VidModeExtension
[    25.489] Initializing built-in extension XFree86-DGA
[    25.489] Initializing built-in extension XFree86-DRI
[    25.489] Initializing built-in extension DRI2
[    25.489] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    25.489] (II) "glx" will be loaded by default.
[    25.489] (II) LoadModule: "glx"
[    25.512] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    26.078] (II) Module glx: vendor="NVIDIA Corporation"
[    26.078]     compiled for 4.0.2, module version = 1.0.0
[    26.078]     Module class: X.Org Server Extension
[    26.078] (II) NVIDIA GLX Module  173.14.39  Wed Nov 27 14:44:39 PST 2013
[    26.078] Loading extension GLX
[    26.078] (II) LoadModule: "nvidia"
[    26.078] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    26.190] (II) Module nvidia: vendor="NVIDIA Corporation"
[    26.190]     compiled for 4.0.2, module version = 1.0.0
[    26.190]     Module class: X.Org Video Driver
[    26.228] (II) NVIDIA dlloader X Driver  173.14.39  Wed Nov 27 14:34:40 PST 2013
[    26.228] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    26.228] (++) using VT number 7


[    26.228] (II) Loading sub module "fb"
[    26.229] (II) LoadModule: "fb"
[    26.238] (II) Loading /usr/lib/xorg/modules/libfb.so
[    26.245] (II) Module fb: vendor="X.Org Foundation"
[    26.245]     compiled for 1.14.5, module version = 1.0.0
[    26.245]     ABI class: X.Org ANSI C Emulation, version 0.4
[    26.245] (II) Loading sub module "wfb"
[    26.245] (II) LoadModule: "wfb"
[    26.246] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    26.253] (II) Module wfb: vendor="X.Org Foundation"
[    26.253]     compiled for 1.14.5, module version = 1.0.0
[    26.253]     ABI class: X.Org ANSI C Emulation, version 0.4
[    26.253] (II) Loading sub module "ramdac"
[    26.253] (II) LoadModule: "ramdac"
[    26.253] (II) Module "ramdac" already built-in
[    26.255] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    26.255] (==) NVIDIA(0): RGB weight 888
[    26.255] (==) NVIDIA(0): Default visual is TrueColor
[    26.255] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    26.256] (**) NVIDIA(0): Enabling RENDER acceleration
[    26.256] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[    26.256] (II) NVIDIA(0):     enabled.
[    27.019] (II) NVIDIA(0): NVIDIA GPU Quadro NVS 140M (G86GL) at PCI:1:0:0 (GPU-0)
[    27.019] (--) NVIDIA(0): Memory: 524288 kBytes
[    27.019] (--) NVIDIA(0): VideoBIOS: 60.86.3e.00.00
[    27.019] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    27.019] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    27.019] (--) NVIDIA(0): Connected display device(s) on Quadro NVS 140M at PCI:1:0:0:
[    27.019] (--) NVIDIA(0):     LEN LT2452pwC (CRT-0)
[    27.019] (--) NVIDIA(0):     LEN (DFP-0)
[    27.019] (--) NVIDIA(0): LEN LT2452pwC (CRT-0): 400.0 MHz maximum pixel clock
[    27.019] (--) NVIDIA(0): LEN (DFP-0): 330.0 MHz maximum pixel clock
[    27.019] (--) NVIDIA(0): LEN (DFP-0): Internal Dual Link LVDS
[    27.027] (WW) NVIDIA(0): The EDID for LEN (DFP-0) contradicts itself: mode "1280x800"
[    27.027] (WW) NVIDIA(0):     is specified in the EDID; however, the EDID's valid
[    27.027] (WW) NVIDIA(0):     HorizSync range (41.216-49.305 kHz) would exclude this
[    27.027] (WW) NVIDIA(0):     mode's HorizSync (32.9 kHz); ignoring HorizSync check for
[    27.027] (WW) NVIDIA(0):     mode "1280x800".
[    27.027] (WW) NVIDIA(0): The EDID for LEN (DFP-0) contradicts itself: mode "1280x800"
[    27.027] (WW) NVIDIA(0):     is specified in the EDID; however, the EDID's valid
[    27.027] (WW) NVIDIA(0):     VertRefresh range (50.000-60.000 Hz) would exclude this
[    27.027] (WW) NVIDIA(0):     mode's VertRefresh (39.9 Hz); ignoring VertRefresh check
[    27.027] (WW) NVIDIA(0):     for mode "1280x800".
[    27.028] (WW) NVIDIA(0): The EDID for LEN (DFP-0) contradicts itself: mode "1280x800"
[    27.028] (WW) NVIDIA(0):     is specified in the EDID; however, the EDID's valid
[    27.028] (WW) NVIDIA(0):     HorizSync range (41.216-49.305 kHz) would exclude this
[    27.028] (WW) NVIDIA(0):     mode's HorizSync (32.9 kHz); ignoring HorizSync check for
[    27.028] (WW) NVIDIA(0):     mode "1280x800".
[    27.028] (WW) NVIDIA(0): The EDID for LEN (DFP-0) contradicts itself: mode "1280x800"
[    27.028] (WW) NVIDIA(0):     is specified in the EDID; however, the EDID's valid
[    27.028] (WW) NVIDIA(0):     VertRefresh range (50.000-60.000 Hz) would exclude this
[    27.028] (WW) NVIDIA(0):     mode's VertRefresh (39.9 Hz); ignoring VertRefresh check
[    27.028] (WW) NVIDIA(0):     for mode "1280x800".
[    27.029] (II) NVIDIA(0): Assigned Display Device: DFP-0
[    27.029] (==) NVIDIA(0): 
[    27.029] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    27.029] (==) NVIDIA(0):     will be used as the requested mode.
[    27.029] (==) NVIDIA(0): 
[    27.029] (II) NVIDIA(0): Validated modes:
[    27.029] (II) NVIDIA(0):     "nvidia-auto-select"
[    27.029] (II) NVIDIA(0): Virtual screen size determined to be 1280 x 800
[    27.057] (--) NVIDIA(0): DPI set to (108, 106); computed from "UseEdidDpi" X config
[    27.057] (--) NVIDIA(0):     option
[    27.057] (==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
[    27.057] (--) Depth 24 pixmap format is 32 bpp
[    27.061] (II) NVIDIA(0): Initialized GPU GART.
[    27.062] (WW) NVIDIA(0): Failed to determine power source of the system : Unable to
[    27.062] (WW) NVIDIA(0):     find AC state file under /proc/acpi/ac_adapter/
[    27.071] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[    27.977] Loading extension NV-GLX
[    28.042] (II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
[    28.063] (II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
[    28.063] (==) NVIDIA(0): Backing store disabled
[    28.063] (==) NVIDIA(0): Silken mouse enabled
[    28.076] (**) NVIDIA(0): DPMS enabled
[    28.077] Loading extension NV-CONTROL
[    28.077] (==) RandR enabled
[    28.083] (II) Initializing extension GLX
[    28.357] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    28.403] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    28.403] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    28.403] (II) LoadModule: "evdev"
[    28.403] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    28.438] (II) Module evdev: vendor="X.Org Foundation"
[    28.438]     compiled for 1.14.5, module version = 2.7.3
[    28.438]     Module class: X.Org XInput Driver
[    28.438]     ABI class: X.Org XInput driver, version 19.1
[    28.438] (II) Using input driver 'evdev' for 'Power Button'
[    28.438] (**) Power Button: always reports core events
[    28.438] (**) evdev: Power Button: Device: "/dev/input/event2"
[    28.438] (--) evdev: Power Button: Vendor 0 Product 0x1
[    28.438] (--) evdev: Power Button: Found keys
[    28.438] (II) evdev: Power Button: Configuring as keyboard
[    28.438] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    28.438] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    28.438] (**) Option "xkb_rules" "evdev"
[    28.438] (**) Option "xkb_model" "pc105"
[    28.438] (**) Option "xkb_layout" "us"
[    28.439] (II) config/udev: Adding input device Video Bus (/dev/input/event7)
[    28.439] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    28.439] (II) Using input driver 'evdev' for 'Video Bus'
[    28.439] (**) Video Bus: always reports core events
[    28.439] (**) evdev: Video Bus: Device: "/dev/input/event7"
[    28.439] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    28.439] (--) evdev: Video Bus: Found keys
[    28.439] (II) evdev: Video Bus: Configuring as keyboard
[    28.439] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:05/LNXVIDEO:01/input/input7/event7"
[    28.439] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    28.439] (**) Option "xkb_rules" "evdev"
[    28.439] (**) Option "xkb_model" "pc105"
[    28.439] (**) Option "xkb_layout" "us"
[    28.439] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    28.439] (II) No input driver specified, ignoring this device.
[    28.439] (II) This device may have been added with another device file.
[    28.439] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    28.439] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    28.439] (II) Using input driver 'evdev' for 'Sleep Button'
[    28.439] (**) Sleep Button: always reports core events
[    28.439] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[    28.440] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    28.440] (--) evdev: Sleep Button: Found keys
[    28.440] (II) evdev: Sleep Button: Configuring as keyboard
[    28.440] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1/event1"
[    28.440] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 8)
[    28.440] (**) Option "xkb_rules" "evdev"
[    28.440] (**) Option "xkb_model" "pc105"
[    28.440] (**) Option "xkb_layout" "us"
[    28.440] (II) config/udev: Adding input device Logitech USB Keyboard (/dev/input/event4)
[    28.440] (**) Logitech USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    28.440] (II) Using input driver 'evdev' for 'Logitech USB Keyboard'
[    28.440] (**) Logitech USB Keyboard: always reports core events
[    28.440] (**) evdev: Logitech USB Keyboard: Device: "/dev/input/event4"
[    28.440] (--) evdev: Logitech USB Keyboard: Vendor 0x46d Product 0xc31c
[    28.440] (--) evdev: Logitech USB Keyboard: Found keys
[    28.440] (II) evdev: Logitech USB Keyboard: Configuring as keyboard
[    28.440] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1.2/2-1.2:1.0/input/input4/event4"
[    28.440] (II) XINPUT: Adding extended input device "Logitech USB Keyboard" (type: KEYBOARD, id 9)
[    28.440] (**) Option "xkb_rules" "evdev"
[    28.440] (**) Option "xkb_model" "pc105"
[    28.440] (**) Option "xkb_layout" "us"
[    28.441] (II) config/udev: Adding input device Logitech USB Keyboard (/dev/input/event5)
[    28.441] (**) Logitech USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    28.441] (II) Using input driver 'evdev' for 'Logitech USB Keyboard'
[    28.441] (**) Logitech USB Keyboard: always reports core events
[    28.441] (**) evdev: Logitech USB Keyboard: Device: "/dev/input/event5"
[    28.441] (--) evdev: Logitech USB Keyboard: Vendor 0x46d Product 0xc31c
[    28.441] (--) evdev: Logitech USB Keyboard: Found absolute axes
[    28.441] (II) evdev: Logitech USB Keyboard: Forcing absolute x/y axes to exist.
[    28.441] (--) evdev: Logitech USB Keyboard: Found keys
[    28.441] (II) evdev: Logitech USB Keyboard: Forcing relative x/y axes to exist.
[    28.441] (II) evdev: Logitech USB Keyboard: Configuring as mouse
[    28.441] (II) evdev: Logitech USB Keyboard: Configuring as keyboard
[    28.441] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1.2/2-1.2:1.1/input/input5/event5"
[    28.441] (II) XINPUT: Adding extended input device "Logitech USB Keyboard" (type: KEYBOARD, id 10)
[    28.441] (**) Option "xkb_rules" "evdev"
[    28.441] (**) Option "xkb_model" "pc105"
[    28.441] (**) Option "xkb_layout" "us"
[    28.441] (II) evdev: Logitech USB Keyboard: initialized for absolute axes.
[    28.441] (**) Logitech USB Keyboard: (accel) keeping acceleration scheme 1
[    28.441] (**) Logitech USB Keyboard: (accel) acceleration profile 0
[    28.441] (**) Logitech USB Keyboard: (accel) acceleration factor: 2.000
[    28.441] (**) Logitech USB Keyboard: (accel) acceleration threshold: 4
[    28.441] (II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/event6)
[    28.441] (**) Logitech USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[    28.441] (II) Using input driver 'evdev' for 'Logitech USB Optical Mouse'
[    28.441] (**) Logitech USB Optical Mouse: always reports core events
[    28.441] (**) evdev: Logitech USB Optical Mouse: Device: "/dev/input/event6"
[    28.442] (--) evdev: Logitech USB Optical Mouse: Vendor 0x46d Product 0xc05a
[    28.442] (--) evdev: Logitech USB Optical Mouse: Found 3 mouse buttons
[    28.442] (--) evdev: Logitech USB Optical Mouse: Found scroll wheel(s)
[    28.442] (--) evdev: Logitech USB Optical Mouse: Found relative axes
[    28.442] (--) evdev: Logitech USB Optical Mouse: Found x and y relative axes
[    28.442] (II) evdev: Logitech USB Optical Mouse: Configuring as mouse
[    28.442] (II) evdev: Logitech USB Optical Mouse: Adding scrollwheel support
[    28.442] (**) evdev: Logitech USB Optical Mouse: YAxisMapping: buttons 4 and 5
[    28.442] (**) evdev: Logitech USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    28.442] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1.3/2-1.3:1.0/input/input6/event6"
[    28.442] (II) XINPUT: Adding extended input device "Logitech USB Optical Mouse" (type: MOUSE, id 11)
[    28.442] (II) evdev: Logitech USB Optical Mouse: initialized for relative axes.
[    28.442] (**) Logitech USB Optical Mouse: (accel) keeping acceleration scheme 1
[    28.442] (**) Logitech USB Optical Mouse: (accel) acceleration profile 0
[    28.442] (**) Logitech USB Optical Mouse: (accel) acceleration factor: 2.000
[    28.442] (**) Logitech USB Optical Mouse: (accel) acceleration threshold: 4
[    28.442] (II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/mouse0)
[    28.442] (II) No input driver specified, ignoring this device.
[    28.442] (II) This device may have been added with another device file.
[    28.442] (II) config/udev: Adding input device Integrated Camera (/dev/input/event9)
[    28.442] (**) Integrated Camera: Applying InputClass "evdev keyboard catchall"
[    28.442] (II) Using input driver 'evdev' for 'Integrated Camera'
[    28.442] (**) Integrated Camera: always reports core events
[    28.442] (**) evdev: Integrated Camera: Device: "/dev/input/event9"
[    28.442] (--) evdev: Integrated Camera: Vendor 0x17ef Product 0x1004
[    28.442] (--) evdev: Integrated Camera: Found keys
[    28.442] (II) evdev: Integrated Camera: Configuring as keyboard
[    28.442] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/input/input9/event9"
[    28.442] (II) XINPUT: Adding extended input device "Integrated Camera" (type: KEYBOARD, id 12)
[    28.442] (**) Option "xkb_rules" "evdev"
[    28.443] (**) Option "xkb_model" "pc105"
[    28.443] (**) Option "xkb_layout" "us"
[    28.443] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    28.443] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    28.443] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    28.443] (**) AT Translated Set 2 keyboard: always reports core events
[    28.443] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    28.443] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    28.443] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    28.443] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    28.443] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    28.443] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 13)
[    28.443] (**) Option "xkb_rules" "evdev"
[    28.443] (**) Option "xkb_model" "pc105"
[    28.443] (**) Option "xkb_layout" "us"
[    28.443] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event10)
[    28.443] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    28.444] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    28.444] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[    28.444] (II) LoadModule: "synaptics"
[    28.444] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    28.445] (II) Module synaptics: vendor="X.Org Foundation"
[    28.445]     compiled for 1.14.5, module version = 1.7.1
[    28.445]     Module class: X.Org XInput Driver
[    28.445]     ABI class: X.Org XInput driver, version 19.1
[    28.445] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    28.445] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    28.445] (**) Option "Device" "/dev/input/event10"
[    28.468] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472 (res 93)
[    28.468] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448 (res 125)
[    28.468] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    28.468] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    28.468] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right
[    28.468] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    28.468] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    28.468] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    28.480] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input10/event10"
[    28.480] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 14)
[    28.480] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    28.480] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[    28.480] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.040
[    28.480] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    28.480] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    28.480] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    28.480] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    28.480] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    28.480] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
[    28.480] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    28.480] (II) config/udev: Adding input device TPPS/2 IBM TrackPoint (/dev/input/event11)
[    28.480] (**) TPPS/2 IBM TrackPoint: Applying InputClass "evdev pointer catchall"
[    28.480] (**) TPPS/2 IBM TrackPoint: Applying InputClass "trackpoint catchall"
[    28.480] (II) Using input driver 'evdev' for 'TPPS/2 IBM TrackPoint'
[    28.480] (**) TPPS/2 IBM TrackPoint: always reports core events
[    28.480] (**) evdev: TPPS/2 IBM TrackPoint: Device: "/dev/input/event11"
[    28.480] (--) evdev: TPPS/2 IBM TrackPoint: Vendor 0x2 Product 0xa
[    28.480] (--) evdev: TPPS/2 IBM TrackPoint: Found 3 mouse buttons
[    28.480] (--) evdev: TPPS/2 IBM TrackPoint: Found relative axes
[    28.480] (--) evdev: TPPS/2 IBM TrackPoint: Found x and y relative axes
[    28.480] (II) evdev: TPPS/2 IBM TrackPoint: Configuring as mouse
[    28.480] (**) Option "Emulate3Buttons" "true"
[    28.480] (**) Option "EmulateWheel" "true"
[    28.481] (**) Option "EmulateWheelButton" "2"
[    28.481] (**) Option "YAxisMapping" "4 5"
[    28.481] (**) evdev: TPPS/2 IBM TrackPoint: YAxisMapping: buttons 4 and 5
[    28.481] (**) Option "XAxisMapping" "6 7"
[    28.481] (**) evdev: TPPS/2 IBM TrackPoint: XAxisMapping: buttons 6 and 7
[    28.481] (**) evdev: TPPS/2 IBM TrackPoint: EmulateWheelButton: 2, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    28.481] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/serio2/input/input11/event11"
[    28.481] (II) XINPUT: Adding extended input device "TPPS/2 IBM TrackPoint" (type: MOUSE, id 15)
[    28.481] (II) evdev: TPPS/2 IBM TrackPoint: initialized for relative axes.
[    28.481] (**) TPPS/2 IBM TrackPoint: (accel) keeping acceleration scheme 1
[    28.481] (**) TPPS/2 IBM TrackPoint: (accel) acceleration profile 0
[    28.481] (**) TPPS/2 IBM TrackPoint: (accel) acceleration factor: 2.000
[    28.481] (**) TPPS/2 IBM TrackPoint: (accel) acceleration threshold: 4
[    28.481] (II) config/udev: Adding input device TPPS/2 IBM TrackPoint (/dev/input/mouse2)
[    28.481] (II) No input driver specified, ignoring this device.
[    28.481] (II) This device may have been added with another device file.
[    28.483] (II) config/udev: Adding input device ThinkPad Extra Buttons (/dev/input/event8)
[    28.483] (**) ThinkPad Extra Buttons: Applying InputClass "evdev keyboard catchall"
[    28.483] (II) Using input driver 'evdev' for 'ThinkPad Extra Buttons'
[    28.483] (**) ThinkPad Extra Buttons: always reports core events
[    28.483] (**) evdev: ThinkPad Extra Buttons: Device: "/dev/input/event8"
[    28.483] (--) evdev: ThinkPad Extra Buttons: Vendor 0x17aa Product 0x5054
[    28.483] (--) evdev: ThinkPad Extra Buttons: Found keys
[    28.483] (II) evdev: ThinkPad Extra Buttons: Configuring as keyboard
[    28.483] (**) Option "config_info" "udev:/sys/devices/platform/thinkpad_acpi/input/input8/event8"
[    28.483] (II) XINPUT: Adding extended input device "ThinkPad Extra Buttons" (type: KEYBOARD, id 16)
[    28.483] (**) Option "xkb_rules" "evdev"
[    28.483] (**) Option "xkb_model" "pc105"
[    28.483] (**) Option "xkb_layout" "us"
[    35.135] (II) NVIDIA(0): Setting mode "1280x800_50"
[    45.815] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[    68.407] (II) XKB: reuse xkmfile /var/lib/xkb/server-FD0ED5E58C7B8CFF434EFCCECE775D4CE755114F.xkm
[  2851.033] (II) Open ACPI successful (/var/run/acpid.socket)
[  2851.158] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[  2852.019] (WW) NVIDIA(0): Failed to determine power source of the system : Unable to
[  2852.019] (WW) NVIDIA(0):     find AC state file under /proc/acpi/ac_adapter/
[  2852.197] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found



```

---

### Post by J_Me on 2014-05-20
From your Xorg file> 26.228] (II) NVIDIA dlloader X Driver  173.14.39  Wed Nov 27 14:34:40 PST 2013your using the 173.14.39 driver, you can update them from 'additional drivers' menu.
But I also noticed this> 27.062] (WW) NVIDIA(0): Failed to determine power source of the system : Unable to
[    27.062] (WW) NVIDIA(0):     find AC state file under /proc/acpi/ac_adapter/Which I believe needs to be looked at first before configuring duel monitors. How old is your laptop.

---

### Post by arman2 on 2014-05-21
Thanks for you reply!

1- Actually I had this card running well last week with 12.04 but I had to reinstall it and caused problem. not sure what version was that. I selected the most upper option in the restricted driver window when I wanted to install nVidia driver, because I assumed it is the latest compatible version.

2- My laptop is pretty old. Thinkpad T61 from 2008. My graphic card is nVIDIA Quadro                                  NVS 140M.

which steps you suggest me to take now to resolve the issue?

thanks

---

### Post by J_Me on 2014-05-21
2008 is not so bad, try the driver that says [recommended] next to it and have a look at your xorg file again for errors.

---

