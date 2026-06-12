---
title: "Ubuntu 13.04 Resolution Problem"
date: 2013-05-27
forum: Hardware
---

### Post by EdgyPowell on 2013-05-27
[CENTER]Hey Ubuntu community, [/CENTER]
I have been struck with this problem for a while now. The maximum resolution on my Ubuntu 13.04 desktop PC goes up to a maximum of 1366x768 whilst the resolution of Windows 7 on my desktop PC goes up to a maximum of 1600x900, so I was just wondering how do I fix this? as it has bothered me for a while since icons and windows seem too big. Thanks Ubuntu community

---

### Post by Yellow Pasque on 2013-05-27
Post your /var/log/Xorg.0.log file

---

### Post by EdgyPowell on 2013-05-27
[    38.293] 
X.Org X Server 1.13.3
Release Date: 2013-03-07
[    38.293] X Protocol Version 11, Revision 0
[    38.293] Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
[    38.293] Current Operating System: Linux Ubuntu-PC 3.8.0-22-generic #33-Ubuntu SMP Thu May 16 15:17:14 UTC 2013 x86_64
[    38.293] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-22-generic root=UUID=93683b35-e9ef-48c5-a99d-93cc2ad497fb ro quiet splash
[    38.293] Build Date: 17 April 2013  10:43:13PM
[    38.293] xorg-server 2:1.13.3-0ubuntu6 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    38.293] Current version of pixman: 0.28.2
[    38.293]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    38.293] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    38.293] (==) Log file: "/var/log/Xorg.0.log", Time: Mon May 27 19:19:32 2013
[    38.326] (==) Using config file: "/etc/X11/xorg.conf"
[    38.326] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    38.625] (==) ServerLayout "Layout0"
[    38.625] (**) |-->Screen "Screen0" (0)
[    38.625] (**) |   |-->Monitor "Monitor0"
[    38.625] (**) |   |-->Device "Device0"
[    38.625] (**) |-->Input Device "Keyboard0"
[    38.625] (**) |-->Input Device "Mouse0"
[    38.626] (**) Option "Xinerama" "0"
[    38.626] (==) Automatically adding devices
[    38.626] (==) Automatically enabling devices
[    38.626] (==) Automatically adding GPU devices
[    38.626] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    38.626]     Entry deleted from font path.
[    38.626] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    38.626]     Entry deleted from font path.
[    38.626] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    38.626]     Entry deleted from font path.
[    38.681] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    38.725]     Entry deleted from font path.
[    38.725] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    38.725]     Entry deleted from font path.
[    38.786] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    38.786]     Entry deleted from font path.
[    38.786] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    38.786] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    38.786] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    38.786] (WW) Disabling Keyboard0
[    38.786] (WW) Disabling Mouse0
[    38.818] (II) Loader magic: 0x7f877d32bd20
[    38.859] (II) Module ABI versions:
[    38.859]     X.Org ANSI C Emulation: 0.4
[    38.859]     X.Org Video Driver: 13.1
[    38.859]     X.Org XInput driver : 18.0
[    38.859]     X.Org Server Extension : 7.0
[    38.860] (--) PCI:*(0:0:13:0) 10de:03d0:1025:0394 rev 162, Mem @ 0xfb000000/16777216, 0xe0000000/268435456, 0xfa000000/16777216, BIOS @ 0x????????/131072
[    38.860] (II) Open ACPI successful (/var/run/acpid.socket)
[    38.860] Initializing built-in extension Generic Event Extension
[    38.860] Initializing built-in extension SHAPE
[    38.860] Initializing built-in extension MIT-SHM
[    38.860] Initializing built-in extension XInputExtension
[    38.860] Initializing built-in extension XTEST
[    38.860] Initializing built-in extension BIG-REQUESTS
[    38.860] Initializing built-in extension SYNC
[    38.860] Initializing built-in extension XKEYBOARD
[    38.860] Initializing built-in extension XC-MISC
[    38.860] Initializing built-in extension SECURITY
[    38.860] Initializing built-in extension XINERAMA
[    38.860] Initializing built-in extension XFIXES
[    38.860] Initializing built-in extension RENDER
[    38.860] Initializing built-in extension RANDR
[    38.860] Initializing built-in extension COMPOSITE
[    38.860] Initializing built-in extension DAMAGE
[    38.860] Initializing built-in extension MIT-SCREEN-SAVER
[    38.860] Initializing built-in extension DOUBLE-BUFFER
[    38.860] Initializing built-in extension RECORD
[    38.860] Initializing built-in extension DPMS
[    38.860] Initializing built-in extension X-Resource
[    38.860] Initializing built-in extension XVideo
[    38.860] Initializing built-in extension XVideo-MotionCompensation
[    38.860] Initializing built-in extension SELinux
[    38.860] Initializing built-in extension XFree86-VidModeExtension
[    38.860] Initializing built-in extension XFree86-DGA
[    38.860] Initializing built-in extension XFree86-DRI
[    38.860] Initializing built-in extension DRI2
[    38.860] (II) LoadModule: "glx"
[    38.978] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    39.793] (II) Module glx: vendor="NVIDIA Corporation"
[    39.793]     compiled for 4.0.2, module version = 1.0.0
[    39.793]     Module class: X.Org Server Extension
[    39.793] (II) NVIDIA GLX Module  304.88  Wed Mar 27 14:46:57 PDT 2013
[    39.793] Loading extension GLX
[    39.793] (II) LoadModule: "nvidia"
[    39.793] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    40.066] (II) Module nvidia: vendor="NVIDIA Corporation"
[    40.066]     compiled for 4.0.2, module version = 1.0.0
[    40.066]     Module class: X.Org Video Driver
[    40.163] (II) NVIDIA dlloader X Driver  304.88  Wed Mar 27 14:28:14 PDT 2013
[    40.163] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    40.182] (++) using VT number 7

[    40.205] (II) Loading sub module "fb"
[    40.205] (II) LoadModule: "fb"
[    40.278] (II) Loading /usr/lib/xorg/modules/libfb.so
[    40.352] (II) Module fb: vendor="X.Org Foundation"
[    40.352]     compiled for 1.13.3, module version = 1.0.0
[    40.352]     ABI class: X.Org ANSI C Emulation, version 0.4
[    40.352] (II) Loading sub module "wfb"
[    40.352] (II) LoadModule: "wfb"
[    40.352] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    40.461] (II) Module wfb: vendor="X.Org Foundation"
[    40.461]     compiled for 1.13.3, module version = 1.0.0
[    40.461]     ABI class: X.Org ANSI C Emulation, version 0.4
[    40.461] (II) Loading sub module "ramdac"
[    40.461] (II) LoadModule: "ramdac"
[    40.461] (II) Module "ramdac" already built-in
[    40.624] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    40.625] (==) NVIDIA(0): RGB weight 888
[    40.625] (==) NVIDIA(0): Default visual is TrueColor
[    40.625] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    40.625] (**) NVIDIA(0): Option "Stereo" "0"
[    40.625] (**) NVIDIA(0): Option "nvidiaXineramaInfoOrder" "CRT-0"
[    40.625] (**) NVIDIA(0): Option "TwinViewXineramaInfoOrder" "CRT-0"
[    40.625] (**) NVIDIA(0): Stereo disabled by request
[    40.625] (**) NVIDIA(0): Option "MetaModes" "1360x768_60_0 +0+0; 1360x768 +0+0; 1360x768_60 +0+0"
[    40.625] (**) NVIDIA(0): Enabling 2D acceleration
[    41.325] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[    41.712] (II) NVIDIA(0): NVIDIA GPU GeForce 6150SE nForce 430 (C61) at PCI:0:13:0
[    41.712] (II) NVIDIA(0):     (GPU-0)
[    41.712] (--) NVIDIA(0): Memory: 524288 kBytes
[    41.712] (--) NVIDIA(0): VideoBIOS: 05.61.32.30.00
[    41.712] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    41.712] (--) NVIDIA(0): Valid display device(s) on GeForce 6150SE nForce 430 at PCI:0:13:0
[    41.712] (--) NVIDIA(0):     CRT-0 (connected)
[    41.712] (--) NVIDIA(0): CRT-0: 350.0 MHz maximum pixel clock
[    41.712] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    41.712] (**) NVIDIA(0):     device CRT-0 (Using EDID frequencies has been enabled on
[    41.712] (**) NVIDIA(0):     all display devices.)
[    41.714] (II) NVIDIA(0): Validated MetaModes:
[    41.714] (II) NVIDIA(0):     "1360x768_60_0+0+0"
[    41.714] (II) NVIDIA(0):     "1360x768+0+0"
[    41.714] (II) NVIDIA(0):     "1360x768_60+0+0"
[    41.714] (II) NVIDIA(0): Virtual screen size determined to be 1360 x 768
[    41.716] (WW) NVIDIA(0): Unable to support custom viewPortOut 1024 x 576 +0 +96
[    41.717] (WW) NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
[    41.717] (WW) NVIDIA(0):     from CRT-0's EDID.
[    41.717] (==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
[    41.717] (--) Depth 24 pixmap format is 32 bpp
[    41.723] (II) NVIDIA(0): Setting mode "1360x768_60_0+0+0"
[    42.075] Loading extension NV-GLX
[    42.369] (==) NVIDIA(0): Disabling shared memory pixmaps
[    42.369] (==) NVIDIA(0): Backing store disabled
[    42.369] (==) NVIDIA(0): Silken mouse enabled
[    42.371] (**) NVIDIA(0): DPMS enabled
[    42.371] Loading extension NV-CONTROL
[    42.372] Loading extension XINERAMA
[    42.372] (WW) NVIDIA(0): Option "TwinView" is not used
[    42.372] (II) Loading sub module "dri2"
[    42.372] (II) LoadModule: "dri2"
[    42.372] (II) Module "dri2" already built-in
[    42.372] (II) NVIDIA(0): [DRI2] Setup complete
[    42.372] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[    42.373] (--) RandR disabled
[    42.393] (II) SELinux: Disabled on system
[    42.408] (II) Initializing extension GLX
[    42.583] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    42.657] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    42.657] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    42.657] (II) LoadModule: "evdev"
[    42.657] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    42.728] (II) Module evdev: vendor="X.Org Foundation"
[    42.728]     compiled for 1.13.3, module version = 2.7.3
[    42.728]     Module class: X.Org XInput Driver
[    42.728]     ABI class: X.Org XInput driver, version 18.0
[    42.728] (II) Using input driver 'evdev' for 'Power Button'
[    42.728] (**) Power Button: always reports core events
[    42.728] (**) evdev: Power Button: Device: "/dev/input/event1"
[    42.728] (--) evdev: Power Button: Vendor 0 Product 0x1
[    42.729] (--) evdev: Power Button: Found keys
[    42.729] (II) evdev: Power Button: Configuring as keyboard
[    42.729] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    42.729] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    42.729] (**) Option "xkb_rules" "evdev"
[    42.729] (**) Option "xkb_model" "pc105"
[    42.729] (**) Option "xkb_layout" "gb"
[    42.729] (**) Option "xkb_variant" "mac"
[    42.734] (II) XKB: reuse xkmfile /var/lib/xkb/server-B0B002130E81C7ED77EB3BB72BA6C24C493AD965.xkm
[    42.747] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    42.747] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    42.747] (II) Using input driver 'evdev' for 'Power Button'
[    42.747] (**) Power Button: always reports core events
[    42.747] (**) evdev: Power Button: Device: "/dev/input/event0"
[    42.747] (--) evdev: Power Button: Vendor 0 Product 0x1
[    42.747] (--) evdev: Power Button: Found keys
[    42.747] (II) evdev: Power Button: Configuring as keyboard
[    42.747] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    42.747] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    42.747] (**) Option "xkb_rules" "evdev"
[    42.747] (**) Option "xkb_model" "pc105"
[    42.747] (**) Option "xkb_layout" "gb"
[    42.747] (**) Option "xkb_variant" "mac"
[    42.747] (II) config/udev: Adding input device  USB OPTICAL MOUSE (/dev/input/event2)
[    42.748] (**)  USB OPTICAL MOUSE: Applying InputClass "evdev pointer catchall"
[    42.748] (II) Using input driver 'evdev' for ' USB OPTICAL MOUSE'
[    42.748] (**)  USB OPTICAL MOUSE: always reports core events
[    42.748] (**) evdev:  USB OPTICAL MOUSE: Device: "/dev/input/event2"
[    42.748] (--) evdev:  USB OPTICAL MOUSE: Vendor 0x15d9 Product 0xa4c
[    42.748] (--) evdev:  USB OPTICAL MOUSE: Found 3 mouse buttons
[    42.748] (--) evdev:  USB OPTICAL MOUSE: Found scroll wheel(s)
[    42.748] (--) evdev:  USB OPTICAL MOUSE: Found relative axes
[    42.748] (--) evdev:  USB OPTICAL MOUSE: Found x and y relative axes
[    42.748] (II) evdev:  USB OPTICAL MOUSE: Configuring as mouse
[    42.748] (II) evdev:  USB OPTICAL MOUSE: Adding scrollwheel support
[    42.748] (**) evdev:  USB OPTICAL MOUSE: YAxisMapping: buttons 4 and 5
[    42.748] (**) evdev:  USB OPTICAL MOUSE: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    42.748] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.0/usb2/2-2/2-2:1.0/input/input2/event2"
[    42.748] (II) XINPUT: Adding extended input device " USB OPTICAL MOUSE" (type: MOUSE, id 8)
[    42.748] (II) evdev:  USB OPTICAL MOUSE: initialized for relative axes.
[    42.748] (**)  USB OPTICAL MOUSE: (accel) keeping acceleration scheme 1
[    42.748] (**)  USB OPTICAL MOUSE: (accel) acceleration profile 0
[    42.748] (**)  USB OPTICAL MOUSE: (accel) acceleration factor: 2.000
[    42.748] (**)  USB OPTICAL MOUSE: (accel) acceleration threshold: 4
[    42.748] (II) config/udev: Adding input device  USB OPTICAL MOUSE (/dev/input/mouse0)
[    42.749] (II) No input driver specified, ignoring this device.
[    42.749] (II) This device may have been added with another device file.
[    42.749] (II) config/udev: Adding input device ov519 (/dev/input/event5)
[    42.749] (**) ov519: Applying InputClass "evdev keyboard catchall"
[    42.749] (II) Using input driver 'evdev' for 'ov519'
[    42.749] (**) ov519: always reports core events
[    42.749] (**) evdev: ov519: Device: "/dev/input/event5"
[    42.749] (--) evdev: ov519: Vendor 0x54c Product 0x155
[    42.749] (--) evdev: ov519: Found keys
[    42.749] (II) evdev: ov519: Configuring as keyboard
[    42.749] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.0/usb2/2-3/input/input5/event5"
[    42.749] (II) XINPUT: Adding extended input device "ov519" (type: KEYBOARD, id 9)
[    42.749] (**) Option "xkb_rules" "evdev"
[    42.749] (**) Option "xkb_model" "pc105"
[    42.749] (**) Option "xkb_layout" "gb"
[    42.749] (**) Option "xkb_variant" "mac"
[    42.750] (II) config/udev: Adding input device GASIA GASIA USB KB Pro (/dev/input/event3)
[    42.750] (**) GASIA GASIA USB KB Pro: Applying InputClass "evdev keyboard catchall"
[    42.750] (II) Using input driver 'evdev' for 'GASIA GASIA USB KB Pro'
[    42.750] (**) GASIA GASIA USB KB Pro: always reports core events
[    42.750] (**) evdev: GASIA GASIA USB KB Pro: Device: "/dev/input/event3"
[    42.750] (--) evdev: GASIA GASIA USB KB Pro: Vendor 0xe8f Product 0x21
[    42.750] (--) evdev: GASIA GASIA USB KB Pro: Found keys
[    42.750] (II) evdev: GASIA GASIA USB KB Pro: Configuring as keyboard
[    42.750] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.0/usb2/2-4/2-4:1.0/input/input3/event3"
[    42.750] (II) XINPUT: Adding extended input device "GASIA GASIA USB KB Pro" (type: KEYBOARD, id 10)
[    42.750] (**) Option "xkb_rules" "evdev"
[    42.750] (**) Option "xkb_model" "pc105"
[    42.750] (**) Option "xkb_layout" "gb"
[    42.750] (**) Option "xkb_variant" "mac"
[    42.750] (II) config/udev: Adding input device GASIA GASIA USB KB Pro (/dev/input/event4)
[    42.750] (**) GASIA GASIA USB KB Pro: Applying InputClass "evdev keyboard catchall"
[    42.751] (II) Using input driver 'evdev' for 'GASIA GASIA USB KB Pro'
[    42.751] (**) GASIA GASIA USB KB Pro: always reports core events
[    42.751] (**) evdev: GASIA GASIA USB KB Pro: Device: "/dev/input/event4"
[    42.751] (--) evdev: GASIA GASIA USB KB Pro: Vendor 0xe8f Product 0x21
[    42.751] (--) evdev: GASIA GASIA USB KB Pro: Found 1 mouse buttons
[    42.751] (--) evdev: GASIA GASIA USB KB Pro: Found scroll wheel(s)
[    42.751] (--) evdev: GASIA GASIA USB KB Pro: Found relative axes
[    42.751] (II) evdev: GASIA GASIA USB KB Pro: Forcing relative x/y axes to exist.
[    42.751] (--) evdev: GASIA GASIA USB KB Pro: Found absolute axes
[    42.751] (II) evdev: GASIA GASIA USB KB Pro: Forcing absolute x/y axes to exist.
[    42.751] (--) evdev: GASIA GASIA USB KB Pro: Found keys
[    42.751] (II) evdev: GASIA GASIA USB KB Pro: Configuring as mouse
[    42.751] (II) evdev: GASIA GASIA USB KB Pro: Configuring as keyboard
[    42.751] (II) evdev: GASIA GASIA USB KB Pro: Adding scrollwheel support
[    42.751] (**) evdev: GASIA GASIA USB KB Pro: YAxisMapping: buttons 4 and 5
[    42.751] (**) evdev: GASIA GASIA USB KB Pro: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    42.751] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.0/usb2/2-4/2-4:1.1/input/input4/event4"
[    42.751] (II) XINPUT: Adding extended input device "GASIA GASIA USB KB Pro" (type: KEYBOARD, id 11)
[    42.751] (**) Option "xkb_rules" "evdev"
[    42.751] (**) Option "xkb_model" "pc105"
[    42.751] (**) Option "xkb_layout" "gb"
[    42.751] (**) Option "xkb_variant" "mac"
[    42.751] (II) evdev: GASIA GASIA USB KB Pro: initialized for relative axes.
[    42.751] (WW) evdev: GASIA GASIA USB KB Pro: ignoring absolute axes.
[    42.751] (**) GASIA GASIA USB KB Pro: (accel) keeping acceleration scheme 1
[    42.751] (**) GASIA GASIA USB KB Pro: (accel) acceleration profile 0
[    42.751] (**) GASIA GASIA USB KB Pro: (accel) acceleration factor: 2.000
[    42.751] (**) GASIA GASIA USB KB Pro: (accel) acceleration threshold: 4
[    42.752] (II) config/udev: Adding input device HDA NVidia Line Out (/dev/input/event10)
[    42.752] (II) No input driver specified, ignoring this device.
[    42.752] (II) This device may have been added with another device file.
[    42.752] (II) config/udev: Adding input device HDA NVidia Line (/dev/input/event6)
[    42.752] (II) No input driver specified, ignoring this device.
[    42.752] (II) This device may have been added with another device file.
[    42.752] (II) config/udev: Adding input device HDA NVidia Rear Mic (/dev/input/event7)
[    42.752] (II) No input driver specified, ignoring this device.
[    42.752] (II) This device may have been added with another device file.
[    42.752] (II) config/udev: Adding input device HDA NVidia Front Mic (/dev/input/event8)
[    42.752] (II) No input driver specified, ignoring this device.
[    42.752] (II) This device may have been added with another device file.
[    42.753] (II) config/udev: Adding input device HDA NVidia Front Headphone (/dev/input/event9)
[    42.753] (II) No input driver specified, ignoring this device.
[    42.753] (II) This device may have been added with another device file.
[    45.455] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[    45.455] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    45.455] (**) NVIDIA(0):     device CRT-0 (Using EDID frequencies has been enabled on
[    45.455] (**) NVIDIA(0):     all display devices.)
[    49.921] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[    49.921] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    49.921] (**) NVIDIA(0):     device CRT-0 (Using EDID frequencies has been enabled on
[    49.921] (**) NVIDIA(0):     all display devices.)
[   114.026] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[   114.026] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   114.026] (**) NVIDIA(0):     device CRT-0 (Using EDID frequencies has been enabled on
[   114.026] (**) NVIDIA(0):     all display devices.)
[   114.397] (II) NVIDIA(0): Setting mode "VGA-0: 1360x768 @1360x768 +0+0"
[   114.682] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[   114.682] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   114.682] (**) NVIDIA(0):     device CRT-0 (Using EDID frequencies has been enabled on
[   114.682] (**) NVIDIA(0):     all display devices.)
[   115.212] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[   115.212] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   115.212] (**) NVIDIA(0):     device CRT-0 (Using EDID frequencies has been enabled on
[   115.212] (**) NVIDIA(0):     all display devices.)
[   115.243] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[   115.243] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   115.243] (**) NVIDIA(0):     device CRT-0 (Using EDID frequencies has been enabled on
[   115.243] (**) NVIDIA(0):     all display devices.)
[   115.259] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[   115.259] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   115.259] (**) NVIDIA(0):     device CRT-0 (Using EDID frequencies has been enabled on
[   115.259] (**) NVIDIA(0):     all display devices.)
[   115.266] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[   115.266] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   115.266] (**) NVIDIA(0):     device CRT-0 (Using EDID frequencies has been enabled on
[   115.266] (**) NVIDIA(0):     all display devices.)
[   115.274] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[   115.274] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   115.274] (**) NVIDIA(0):     device CRT-0 (Using EDID frequencies has been enabled on
[   115.274] (**) NVIDIA(0):     all display devices.)
[   115.285] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[   115.285] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   115.285] (**) NVIDIA(0):     device CRT-0 (Using EDID frequencies has been enabled on
[   115.285] (**) NVIDIA(0):     all display devices.)
[   115.293] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[   115.293] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   115.293] (**) NVIDIA(0):     device CRT-0 (Using EDID frequencies has been enabled on
[   115.293] (**) NVIDIA(0):     all display devices.)
[   115.302] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[   115.302] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   115.302] (**) NVIDIA(0):     device CRT-0 (Using EDID frequencies has been enabled on
[   115.302] (**) NVIDIA(0):     all display devices.)
[   115.310] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[   115.310] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   115.310] (**) NVIDIA(0):     device CRT-0 (Using EDID frequencies has been enabled on
[   115.310] (**) NVIDIA(0):     all display devices.)
[   115.319] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[   115.319] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   115.319] (**) NVIDIA(0):     device CRT-0 (Using EDID frequencies has been enabled on
[   115.319] (**) NVIDIA(0):     all display devices.)
[   115.332] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[   115.332] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   115.332] (**) NVIDIA(0):     device CRT-0 (Using EDID frequencies has been enabled on
[   115.332] (**) NVIDIA(0):     all display devices.)
[   115.340] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[   115.340] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   115.340] (**) NVIDIA(0):     device CRT-0 (Using EDID frequencies has been enabled on
[   115.340] (**) NVIDIA(0):     all display devices.)
[   115.349] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[   115.349] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   115.349] (**) NVIDIA(0):     device CRT-0 (Using EDID frequencies has been enabled on
[   115.349] (**) NVIDIA(0):     all display devices.)
[   115.361] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[   115.361] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   115.361] (**) NVIDIA(0):     device CRT-0 (Using EDID frequencies has been enabled on
[   115.361] (**) NVIDIA(0):     all display devices.)
[   115.374] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[   115.374] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   115.374] (**) NVIDIA(0):     device CRT-0 (Using EDID frequencies has been enabled on
[   115.375] (**) NVIDIA(0):     all display devices.)
[   115.381] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[   115.381] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   115.381] (**) NVIDIA(0):     device CRT-0 (Using EDID frequencies has been enabled on
[   115.381] (**) NVIDIA(0):     all display devices.)
[   115.556] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[   115.556] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   115.556] (**) NVIDIA(0):     device CRT-0 (Using EDID frequencies has been enabled on
[   115.556] (**) NVIDIA(0):     all display devices.)
[   122.912] (II) XKB: reuse xkmfile /var/lib/xkb/server-FB314A17FA3BC5AF3DCF8EC73610AA14AB17F55F.xkm
[   135.230] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[   135.230] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   135.230] (**) NVIDIA(0):     device CRT-0 (Using EDID frequencies has been enabled on
[   135.230] (**) NVIDIA(0):     all display devices.)

---

### Post by Yellow Pasque on 2013-05-27
You should use [ code ][ /code ] blocks for large amounts of text.
As for your issue, I'm not too versed on nvidia config, so hopefully another nvidia user can steer you in the right direction.

---

### Post by EdgyPowell on 2013-05-28
Ok, thanks for your help though.

---

### Post by kansasnoob on 2013-05-28
So it looks like you have an nVidia graphics chip, you can check with:

```
lspci | grep VGA
```

If so I made some notes about an nVidia problem I encountered here:

[http://ubuntuforums.org/showthread.php?t=2134340&page=2&p=12601403#post12601403](http://ubuntuforums.org/showthread.php?t=2134340&page=2&p=12601403#post12601403)

Not certain that will be helpful, but maybe :)

---

### Post by EdgyPowell on 2013-05-28
It hasn't helped, I added the lines correctly as I have checked after restart, but i am still stuck with the resolution :(

---

### Post by kansasnoob on 2013-05-29
> **EdgyPowell said:**
> It hasn't helped, I added the lines correctly as I have checked after restart, but i am still stuck with the resolution :(

OK, then lets start with the full output of these two commands:

```
lspci | grep VGA
```

```
xrandr
```

---

### Post by skvudrms54 on 2013-10-19
follw this link. it will help you.
[http://www.thefourtheye.in/2013/04/ubuntu-screen-custom-resolution.html](http://www.thefourtheye.in/2013/04/ubuntu-screen-custom-resolution.html)


when your computer backs to the previous resolution

register script of terminal command at the startup applications

```
sudo gedit /usr/local/bin/resolutionfix
```

then write on gedit like this 

(this code is just an example. it's different from your computer's code)

[COLOR=#FF0000]xrandr --newmode "1920x1080_60.00" 172.80 1920 2040 2248 2576 1080 1081 1084 1118 -HSync +Vsync [/COLOR][COLOR=#0000FF]&& [/COLOR][COLOR=#FF0000]xrandr --addmode VGA1 "1920x1080_60.00" [/COLOR][COLOR=#0000FF]&& [/COLOR][COLOR=#FF0000]xrandr --output VGA1 --mode "1920x1080_60.00" [/COLOR]

then save it.

next give to the script execution properties

```
sudo chmod +x /usr/local/bin/resolutionfix
```

at last register this script at startup applications

 Name : 
Command :[COLOR=#FF0000]/usr/local/bin/resolutionfix[/COLOR]
Comment :

---

