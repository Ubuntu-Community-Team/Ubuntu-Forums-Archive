---
title: "Ubuntu 14.04 - Touchpad scrolling and features not working in ASUS X450LN"
date: 2014-08-07
forum: Hardware
---

### Post by miguel-carcamo on 2014-08-07
Hi there folks!

I'm struggling to fix this bug, it's like the system is recognizing the touchpad as a PS/2 Mouse, here are some outs that I got:

devices:
```
I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
U: Uniq=
H: Handlers=event0 
B: PROP=0
B: EV=21
B: SW=1

I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: PROP=0
B: EV=3
B: KEY=4000 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
U: Uniq=
H: Handlers=kbd event2 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input3
U: Uniq=
H: Handlers=sysrq kbd event3 
B: PROP=0
B: EV=120013
B: KEY=402000000 3803078f800d001 feffffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=04f2 Product=b40a Version=6964
N: Name="USB2.0 HD UVC WebCam"
P: Phys=usb-0000:00:14.0-5/button
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb2/2-5/2-5:1.0/input/input9
U: Uniq=
H: Handlers=kbd event8 
B: PROP=0
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0000 Version=0000
N: Name="Asus WMI hotkeys"
P: Phys=asus-nb-wmi/input0
S: Sysfs=/devices/platform/asus-nb-wmi/input/input10
U: Uniq=
H: Handlers=rfkill kbd event9 
B: PROP=0
B: EV=100013
B: KEY=80000 0 800000000000 0 0 a1606f00900000 8200027800501000 e000000000000 0
B: MSC=10

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:06/LNXVIDEO:00/input/input11
U: Uniq=
H: Handlers=kbd event10 
B: PROP=0
B: EV=3
B: KEY=3e000b00000000 0 0 0

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input12
U: Uniq=
H: Handlers=kbd event11 
B: PROP=0
B: EV=3
B: KEY=3e000b00000000 0 0 0

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Headphone"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card1/input14
U: Uniq=
H: Handlers=event12 
B: PROP=0
B: EV=21
B: SW=4

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Mic"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card1/input13
U: Uniq=
H: Handlers=event13 
B: PROP=0
B: EV=21
B: SW=10

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel HDMI HDMI/DP,pcm=8"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:03.0/sound/card0/input17
U: Uniq=
H: Handlers=event14 
B: PROP=0
B: EV=21
B: SW=140

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel HDMI HDMI/DP,pcm=7"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:03.0/sound/card0/input16
U: Uniq=
H: Handlers=event15 
B: PROP=0
B: EV=21
B: SW=140

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel HDMI HDMI/DP,pcm=3"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:03.0/sound/card0/input15
U: Uniq=
H: Handlers=event16 
B: PROP=0
B: EV=21
B: SW=140

I: Bus=0011 Vendor=0002 Product=0001 Version=0000
N: Name="PS/2 Generic Mouse"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input556
U: Uniq=
H: Handlers=mouse0 event4 
B: PROP=0
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=3

```


xinput:
```

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                          id=11    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; USB2.0 HD UVC WebCam                        id=10    [slave  keyboard (3)]
    &#8627; Asus WMI hotkeys                            id=14    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=15    [slave  keyboard (3)]

```
Xorg.0.log
```
[    19.831] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[    19.831] X Protocol Version 11, Revision 0
[    19.831] Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
[    19.831] Current Operating System: Linux miguel-X450LN 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:08 UTC 2014 x86_64
[    19.831] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-32-generic.efi.signed root=UUID=7c476225-d36b-4290-86f4-9ee0770175f2 ro quiet splash
[    19.831] Build Date: 16 April 2014  01:36:29PM
[    19.831] xorg-server 2:1.15.1-0ubuntu2 (For technical support please see http://www.ubuntu.com/support) 
[    19.831] Current version of pixman: 0.30.2
[    19.831]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    19.831] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    19.832] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Aug  7 19:12:45 2014
[    19.867] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    19.894] (==) No Layout section.  Using the first Screen section.
[    19.894] (==) No screen section available. Using defaults.
[    19.894] (**) |-->Screen "Default Screen Section" (0)
[    19.894] (**) |   |-->Monitor "<default monitor>"
[    19.894] (==) No device specified for screen "Default Screen Section".
    Using the first device section listed.
[    19.894] (**) |   |-->Device "card0"
[    19.894] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    19.894] (==) Automatically adding devices
[    19.894] (==) Automatically enabling devices
[    19.894] (==) Automatically adding GPU devices
[    19.894] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    19.894]     Entry deleted from font path.
[    19.894] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    19.894]     Entry deleted from font path.
[    19.894] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    19.894]     Entry deleted from font path.
[    19.894] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    19.894]     Entry deleted from font path.
[    19.894] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    19.894]     Entry deleted from font path.
[    19.894] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    19.894] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    19.894] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    19.894] (II) Loader magic: 0x7f8fd5a45d60
[    19.894] (II) Module ABI versions:
[    19.894]     X.Org ANSI C Emulation: 0.4
[    19.894]     X.Org Video Driver: 15.0
[    19.894]     X.Org XInput driver : 20.0
[    19.894]     X.Org Server Extension : 8.0
[    19.894] (II) xfree86: Adding drm device (/dev/dri/card0)
[    19.895] (--) PCI:*(0:0:2:0) 8086:0a16:1043:13fd rev 9, Mem @ 0xf7400000/4194304, 0xd0000000/268435456, I/O @ 0x0000f000/64
[    19.896] Initializing built-in extension Generic Event Extension
[    19.896] Initializing built-in extension SHAPE
[    19.896] Initializing built-in extension MIT-SHM
[    19.896] Initializing built-in extension XInputExtension
[    19.896] Initializing built-in extension XTEST
[    19.896] Initializing built-in extension BIG-REQUESTS
[    19.896] Initializing built-in extension SYNC
[    19.896] Initializing built-in extension XKEYBOARD
[    19.896] Initializing built-in extension XC-MISC
[    19.896] Initializing built-in extension SECURITY
[    19.896] Initializing built-in extension XINERAMA
[    19.896] Initializing built-in extension XFIXES
[    19.896] Initializing built-in extension RENDER
[    19.896] Initializing built-in extension RANDR
[    19.896] Initializing built-in extension COMPOSITE
[    19.896] Initializing built-in extension DAMAGE
[    19.896] Initializing built-in extension MIT-SCREEN-SAVER
[    19.896] Initializing built-in extension DOUBLE-BUFFER
[    19.896] Initializing built-in extension RECORD
[    19.896] Initializing built-in extension DPMS
[    19.896] Initializing built-in extension Present
[    19.896] Initializing built-in extension DRI3
[    19.896] Initializing built-in extension X-Resource
[    19.896] Initializing built-in extension XVideo
[    19.896] Initializing built-in extension XVideo-MotionCompensation
[    19.896] Initializing built-in extension SELinux
[    19.896] Initializing built-in extension XFree86-VidModeExtension
[    19.896] Initializing built-in extension XFree86-DGA
[    19.896] Initializing built-in extension XFree86-DRI
[    19.896] Initializing built-in extension DRI2
[    19.896] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    19.896] (II) "glx" will be loaded by default.
[    19.896] (WW) "xmir" is not to be loaded by default. Skipping.
[    19.896] (II) LoadModule: "glx"
[    19.909] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    20.073] (II) Module glx: vendor="X.Org Foundation"
[    20.073]     compiled for 1.15.1, module version = 1.0.0
[    20.073]     ABI class: X.Org Server Extension, version 8.0
[    20.073] (==) AIGLX enabled
[    20.073] Loading extension GLX
[    20.073] (II) LoadModule: "intel"
[    20.073] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    20.140] (II) Module intel: vendor="X.Org Foundation"
[    20.140]     compiled for 1.15.0, module version = 2.99.910
[    20.140]     Module class: X.Org Video Driver
[    20.140]     ABI class: X.Org Video Driver, version 15.0
[    20.140] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[    20.141] (II) intel: Driver for Intel(R) HD Graphics: 2000-5000
[    20.141] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100
[    20.141] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200
[    20.141] (++) using VT number 7

[    20.151] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.99.910-0ubuntu1 (Timo Aaltonen <tjaalton@ubuntu.com>)
[    20.161] (--) intel(0): Integrated Graphics Chipset: Intel(R) HD Graphics 4400
[    20.161] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2, avx, avx2
[    20.161] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    20.161] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    20.161] (==) intel(0): RGB weight 888
[    20.161] (==) intel(0): Default visual is TrueColor
[    20.161] (**) intel(0): Option "Backlight" "intel_backlight"
[    20.161] (**) intel(0): Framebuffer tiled
[    20.161] (**) intel(0): Pixmaps tiled
[    20.161] (**) intel(0): "Tear free" disabled
[    20.161] (**) intel(0): Forcing per-crtc-pixmaps? no
[    20.162] (II) intel(0): Output eDP1 has no monitor section
[    20.162] (**) intel(0): found backlight control interface intel_backlight (type 'user')
[    20.162] (II) intel(0): Output DP1 has no monitor section
[    20.162] (II) intel(0): Output HDMI1 has no monitor section
[    20.162] (II) intel(0): Output VIRTUAL1 has no monitor section
[    20.162] (--) intel(0): Output eDP1 using initial mode 1366x768 on pipe 0
[    20.162] (==) intel(0): DPI set to (96, 96)
[    20.162] (II) Loading sub module "dri2"
[    20.162] (II) LoadModule: "dri2"
[    20.162] (II) Module "dri2" already built-in
[    20.162] (==) Depth 24 pixmap format is 32 bpp
[    20.182] (II) intel(0): SNA initialized with Haswell (gen7.5, gt2) backend
[    20.182] (==) intel(0): Backing store enabled
[    20.182] (==) intel(0): Silken mouse enabled
[    20.182] (II) intel(0): HW Cursor enabled
[    20.182] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    20.182] (==) intel(0): DPMS enabled
[    20.182] (II) intel(0): [DRI2] Setup complete
[    20.182] (II) intel(0): [DRI2]   DRI driver: i965
[    20.182] (II) intel(0): [DRI2]   VDPAU driver: i965
[    20.182] (II) intel(0): direct rendering: DRI2 Enabled
[    20.182] (==) intel(0): hotplug detection: "enabled"
[    20.182] (--) RandR disabled
[    20.186] (II) SELinux: Disabled on system
[    20.353] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    20.353] (II) AIGLX: enabled GLX_ARB_create_context
[    20.353] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    20.353] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    20.353] (II) AIGLX: enabled GLX_INTEL_swap_event
[    20.353] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    20.353] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[    20.353] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[    20.353] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    20.353] (II) AIGLX: enabled GLX_ARB_create_context_robustness
[    20.353] (II) AIGLX: Loaded and initialized i965
[    20.353] (II) GLX: Initialized DRI2 GL provider for screen 0
[    20.370] (II) intel(0): switch to mode 1366x768@60.1 on eDP1 using pipe 0, position (0, 0), rotation normal, reflection none
[    20.388] (II) intel(0): Setting screen physical size to 361 x 203
[    20.396] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    20.397] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    20.397] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    20.397] (II) LoadModule: "evdev"
[    20.397] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    20.413] (II) Module evdev: vendor="X.Org Foundation"
[    20.413]     compiled for 1.15.0, module version = 2.8.2
[    20.413]     Module class: X.Org XInput Driver
[    20.413]     ABI class: X.Org XInput driver, version 20.0
[    20.413] (II) Using input driver 'evdev' for 'Power Button'
[    20.413] (**) Power Button: always reports core events
[    20.413] (**) evdev: Power Button: Device: "/dev/input/event2"
[    20.413] (--) evdev: Power Button: Vendor 0 Product 0x1
[    20.413] (--) evdev: Power Button: Found keys
[    20.413] (II) evdev: Power Button: Configuring as keyboard
[    20.413] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    20.413] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    20.413] (**) Option "xkb_rules" "evdev"
[    20.414] (**) Option "xkb_model" "pc105"
[    20.414] (**) Option "xkb_layout" "latam"
[    20.415] (II) XKB: reuse xkmfile /var/lib/xkb/server-D39A7DF07EFAADA1B152E688CBEB9ED49E8BFDBB.xkm
[    20.416] (II) config/udev: Adding input device Video Bus (/dev/input/event11)
[    20.416] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    20.416] (II) Using input driver 'evdev' for 'Video Bus'
[    20.416] (**) Video Bus: always reports core events
[    20.416] (**) evdev: Video Bus: Device: "/dev/input/event11"
[    20.416] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    20.416] (--) evdev: Video Bus: Found keys
[    20.416] (II) evdev: Video Bus: Configuring as keyboard
[    20.416] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input12/event11"
[    20.416] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    20.416] (**) Option "xkb_rules" "evdev"
[    20.416] (**) Option "xkb_model" "pc105"
[    20.416] (**) Option "xkb_layout" "latam"
[    20.416] (II) config/udev: Adding input device Video Bus (/dev/input/event10)
[    20.416] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    20.416] (II) Using input driver 'evdev' for 'Video Bus'
[    20.416] (**) Video Bus: always reports core events
[    20.416] (**) evdev: Video Bus: Device: "/dev/input/event10"
[    20.416] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    20.416] (--) evdev: Video Bus: Found keys
[    20.416] (II) evdev: Video Bus: Configuring as keyboard
[    20.416] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:06/LNXVIDEO:00/input/input11/event10"
[    20.416] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 8)
[    20.416] (**) Option "xkb_rules" "evdev"
[    20.416] (**) Option "xkb_model" "pc105"
[    20.416] (**) Option "xkb_layout" "latam"
[    20.417] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    20.417] (II) No input driver specified, ignoring this device.
[    20.417] (II) This device may have been added with another device file.
[    20.417] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    20.417] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    20.417] (II) Using input driver 'evdev' for 'Sleep Button'
[    20.417] (**) Sleep Button: always reports core events
[    20.417] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[    20.417] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    20.417] (--) evdev: Sleep Button: Found keys
[    20.417] (II) evdev: Sleep Button: Configuring as keyboard
[    20.417] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1/event1"
[    20.417] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[    20.417] (**) Option "xkb_rules" "evdev"
[    20.417] (**) Option "xkb_model" "pc105"
[    20.417] (**) Option "xkb_layout" "latam"
[    20.417] (II) config/udev: Adding drm device (/dev/dri/card0)
[    20.417] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    20.417] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=3 (/dev/input/event16)
[    20.417] (II) No input driver specified, ignoring this device.
[    20.417] (II) This device may have been added with another device file.
[    20.417] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=7 (/dev/input/event15)
[    20.417] (II) No input driver specified, ignoring this device.
[    20.417] (II) This device may have been added with another device file.
[    20.418] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=8 (/dev/input/event14)
[    20.418] (II) No input driver specified, ignoring this device.
[    20.418] (II) This device may have been added with another device file.
[    20.418] (II) config/udev: Adding input device USB2.0 HD UVC WebCam (/dev/input/event8)
[    20.418] (**) USB2.0 HD UVC WebCam: Applying InputClass "evdev keyboard catchall"
[    20.418] (II) Using input driver 'evdev' for 'USB2.0 HD UVC WebCam'
[    20.418] (**) USB2.0 HD UVC WebCam: always reports core events
[    20.418] (**) evdev: USB2.0 HD UVC WebCam: Device: "/dev/input/event8"
[    20.418] (--) evdev: USB2.0 HD UVC WebCam: Vendor 0x4f2 Product 0xb40a
[    20.418] (--) evdev: USB2.0 HD UVC WebCam: Found keys
[    20.418] (II) evdev: USB2.0 HD UVC WebCam: Configuring as keyboard
[    20.418] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb2/2-5/2-5:1.0/input/input9/event8"
[    20.418] (II) XINPUT: Adding extended input device "USB2.0 HD UVC WebCam" (type: KEYBOARD, id 10)
[    20.418] (**) Option "xkb_rules" "evdev"
[    20.418] (**) Option "xkb_model" "pc105"
[    20.418] (**) Option "xkb_layout" "latam"
[    20.418] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event13)
[    20.418] (II) No input driver specified, ignoring this device.
[    20.418] (II) This device may have been added with another device file.
[    20.418] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event12)
[    20.418] (II) No input driver specified, ignoring this device.
[    20.418] (II) This device may have been added with another device file.
[    20.418] (II) config/udev: Adding input device Microsoft Microsoft® Nano Transceiver v1.0 (/dev/input/event4)
[    20.418] (**) Microsoft Microsoft® Nano Transceiver v1.0: Applying InputClass "evdev keyboard catchall"
[    20.418] (II) Using input driver 'evdev' for 'Microsoft Microsoft® Nano Transceiver v1.0'
[    20.418] (**) Microsoft Microsoft® Nano Transceiver v1.0: always reports core events
[    20.418] (**) evdev: Microsoft Microsoft® Nano Transceiver v1.0: Device: "/dev/input/event4"
[    20.419] (--) evdev: Microsoft Microsoft® Nano Transceiver v1.0: Vendor 0x45e Product 0x7b2
[    20.419] (--) evdev: Microsoft Microsoft® Nano Transceiver v1.0: Found keys
[    20.419] (II) evdev: Microsoft Microsoft® Nano Transceiver v1.0: Configuring as keyboard
[    20.419] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.3/1-1.3:1.0/input/input6/event4"
[    20.419] (II) XINPUT: Adding extended input device "Microsoft Microsoft® Nano Transceiver v1.0" (type: KEYBOARD, id 11)
[    20.419] (**) Option "xkb_rules" "evdev"
[    20.419] (**) Option "xkb_model" "pc105"
[    20.419] (**) Option "xkb_layout" "latam"
[    20.419] (II) config/udev: Adding input device Microsoft Microsoft® Nano Transceiver v1.0 (/dev/input/event5)
[    20.419] (**) Microsoft Microsoft® Nano Transceiver v1.0: Applying InputClass "evdev pointer catchall"
[    20.419] (II) Using input driver 'evdev' for 'Microsoft Microsoft® Nano Transceiver v1.0'
[    20.419] (**) Microsoft Microsoft® Nano Transceiver v1.0: always reports core events
[    20.419] (**) evdev: Microsoft Microsoft® Nano Transceiver v1.0: Device: "/dev/input/event5"
[    20.419] (--) evdev: Microsoft Microsoft® Nano Transceiver v1.0: Vendor 0x45e Product 0x7b2
[    20.419] (--) evdev: Microsoft Microsoft® Nano Transceiver v1.0: Found 9 mouse buttons
[    20.419] (--) evdev: Microsoft Microsoft® Nano Transceiver v1.0: Found scroll wheel(s)
[    20.419] (--) evdev: Microsoft Microsoft® Nano Transceiver v1.0: Found relative axes
[    20.419] (--) evdev: Microsoft Microsoft® Nano Transceiver v1.0: Found x and y relative axes
[    20.419] (II) evdev: Microsoft Microsoft® Nano Transceiver v1.0: Configuring as mouse
[    20.419] (II) evdev: Microsoft Microsoft® Nano Transceiver v1.0: Adding scrollwheel support
[    20.419] (**) evdev: Microsoft Microsoft® Nano Transceiver v1.0: YAxisMapping: buttons 4 and 5
[    20.419] (**) evdev: Microsoft Microsoft® Nano Transceiver v1.0: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    20.419] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.3/1-1.3:1.1/input/input7/event5"
[    20.419] (II) XINPUT: Adding extended input device "Microsoft Microsoft® Nano Transceiver v1.0" (type: MOUSE, id 12)
[    20.419] (II) evdev: Microsoft Microsoft® Nano Transceiver v1.0: initialized for relative axes.
[    20.419] (**) Microsoft Microsoft® Nano Transceiver v1.0: (accel) keeping acceleration scheme 1
[    20.419] (**) Microsoft Microsoft® Nano Transceiver v1.0: (accel) acceleration profile 0
[    20.419] (**) Microsoft Microsoft® Nano Transceiver v1.0: (accel) acceleration factor: 2.000
[    20.419] (**) Microsoft Microsoft® Nano Transceiver v1.0: (accel) acceleration threshold: 4
[    20.419] (II) config/udev: Adding input device Microsoft Microsoft® Nano Transceiver v1.0 (/dev/input/mouse0)
[    20.419] (II) No input driver specified, ignoring this device.
[    20.419] (II) This device may have been added with another device file.
[    20.420] (II) config/udev: Adding input device Microsoft Microsoft® Nano Transceiver v1.0 (/dev/input/event6)
[    20.420] (**) Microsoft Microsoft® Nano Transceiver v1.0: Applying InputClass "evdev keyboard catchall"
[    20.420] (II) Using input driver 'evdev' for 'Microsoft Microsoft® Nano Transceiver v1.0'
[    20.420] (**) Microsoft Microsoft® Nano Transceiver v1.0: always reports core events
[    20.420] (**) evdev: Microsoft Microsoft® Nano Transceiver v1.0: Device: "/dev/input/event6"
[    20.420] (II) evdev: Microsoft Microsoft® Nano Transceiver v1.0: Using mtdev for this device
[    20.420] (--) evdev: Microsoft Microsoft® Nano Transceiver v1.0: Vendor 0x45e Product 0x7b2
[    20.420] (--) evdev: Microsoft Microsoft® Nano Transceiver v1.0: Found 1 mouse buttons
[    20.420] (--) evdev: Microsoft Microsoft® Nano Transceiver v1.0: Found scroll wheel(s)
[    20.420] (--) evdev: Microsoft Microsoft® Nano Transceiver v1.0: Found relative axes
[    20.420] (--) evdev: Microsoft Microsoft® Nano Transceiver v1.0: Found absolute axes
[    20.420] (--) evdev: Microsoft Microsoft® Nano Transceiver v1.0: Found absolute multitouch axes
[    20.420] (--) evdev: Microsoft Microsoft® Nano Transceiver v1.0: Found x and y absolute axes
[    20.420] (--) evdev: Microsoft Microsoft® Nano Transceiver v1.0: Found keys
[    20.420] (II) evdev: Microsoft Microsoft® Nano Transceiver v1.0: Forcing relative x/y axes to exist.
[    20.420] (II) evdev: Microsoft Microsoft® Nano Transceiver v1.0: Configuring as mouse
[    20.420] (II) evdev: Microsoft Microsoft® Nano Transceiver v1.0: Configuring as keyboard
[    20.420] (II) evdev: Microsoft Microsoft® Nano Transceiver v1.0: Adding scrollwheel support
[    20.420] (**) evdev: Microsoft Microsoft® Nano Transceiver v1.0: YAxisMapping: buttons 4 and 5
[    20.420] (**) evdev: Microsoft Microsoft® Nano Transceiver v1.0: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    20.420] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.3/1-1.3:1.2/input/input8/event6"
[    20.420] (II) XINPUT: Adding extended input device "Microsoft Microsoft® Nano Transceiver v1.0" (type: KEYBOARD, id 13)
[    20.420] (**) Option "xkb_rules" "evdev"
[    20.420] (**) Option "xkb_model" "pc105"
[    20.420] (**) Option "xkb_layout" "latam"
[    20.420] (II) evdev: Microsoft Microsoft® Nano Transceiver v1.0: initialized for relative axes.
[    20.420] (WW) evdev: Microsoft Microsoft® Nano Transceiver v1.0: ignoring absolute axes.
[    20.420] (**) Microsoft Microsoft® Nano Transceiver v1.0: (accel) keeping acceleration scheme 1
[    20.420] (**) Microsoft Microsoft® Nano Transceiver v1.0: (accel) acceleration profile 0
[    20.420] (**) Microsoft Microsoft® Nano Transceiver v1.0: (accel) acceleration factor: 2.000
[    20.420] (**) Microsoft Microsoft® Nano Transceiver v1.0: (accel) acceleration threshold: 4
[    20.420] (II) config/udev: Adding input device Microsoft Microsoft® Nano Transceiver v1.0 (/dev/input/js0)
[    20.420] (II) No input driver specified, ignoring this device.
[    20.420] (II) This device may have been added with another device file.
[    20.420] (II) config/udev: Adding input device Asus WMI hotkeys (/dev/input/event9)
[    20.420] (**) Asus WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    20.420] (II) Using input driver 'evdev' for 'Asus WMI hotkeys'
[    20.420] (**) Asus WMI hotkeys: always reports core events
[    20.420] (**) evdev: Asus WMI hotkeys: Device: "/dev/input/event9"
[    20.420] (--) evdev: Asus WMI hotkeys: Vendor 0 Product 0
[    20.420] (--) evdev: Asus WMI hotkeys: Found keys
[    20.420] (II) evdev: Asus WMI hotkeys: Configuring as keyboard
[    20.420] (**) Option "config_info" "udev:/sys/devices/platform/asus-nb-wmi/input/input10/event9"
[    20.420] (II) XINPUT: Adding extended input device "Asus WMI hotkeys" (type: KEYBOARD, id 14)
[    20.420] (**) Option "xkb_rules" "evdev"
[    20.420] (**) Option "xkb_model" "pc105"
[    20.420] (**) Option "xkb_layout" "latam"
[    20.421] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    20.421] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    20.421] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    20.421] (**) AT Translated Set 2 keyboard: always reports core events
[    20.421] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    20.421] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    20.421] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    20.421] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    20.421] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    20.421] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 15)
[    20.421] (**) Option "xkb_rules" "evdev"
[    20.421] (**) Option "xkb_model" "pc105"
[    20.421] (**) Option "xkb_layout" "latam"
[    20.421] (II) config/udev: Adding input device PS/2 Logitech Wheel Mouse (/dev/input/event7)
[    20.421] (**) PS/2 Logitech Wheel Mouse: Applying InputClass "evdev pointer catchall"
[    20.421] (II) Using input driver 'evdev' for 'PS/2 Logitech Wheel Mouse'
[    20.421] (**) PS/2 Logitech Wheel Mouse: always reports core events
[    20.421] (**) evdev: PS/2 Logitech Wheel Mouse: Device: "/dev/input/event7"
[    20.421] (--) evdev: PS/2 Logitech Wheel Mouse: Vendor 0x2 Product 0x1
[    20.421] (--) evdev: PS/2 Logitech Wheel Mouse: Found 3 mouse buttons
[    20.421] (--) evdev: PS/2 Logitech Wheel Mouse: Found relative axes
[    20.421] (--) evdev: PS/2 Logitech Wheel Mouse: Found x and y relative axes
[    20.421] (II) evdev: PS/2 Logitech Wheel Mouse: Configuring as mouse
[    20.421] (**) evdev: PS/2 Logitech Wheel Mouse: YAxisMapping: buttons 4 and 5
[    20.421] (**) evdev: PS/2 Logitech Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    20.421] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input5/event7"
[    20.421] (II) XINPUT: Adding extended input device "PS/2 Logitech Wheel Mouse" (type: MOUSE, id 16)
[    20.421] (II) evdev: PS/2 Logitech Wheel Mouse: initialized for relative axes.
[    20.421] (**) PS/2 Logitech Wheel Mouse: (accel) keeping acceleration scheme 1
[    20.421] (**) PS/2 Logitech Wheel Mouse: (accel) acceleration profile 0
[    20.421] (**) PS/2 Logitech Wheel Mouse: (accel) acceleration factor: 2.000
[    20.421] (**) PS/2 Logitech Wheel Mouse: (accel) acceleration threshold: 4
[    20.421] (II) config/udev: Adding input device PS/2 Logitech Wheel Mouse (/dev/input/mouse1)
[    20.421] (II) No input driver specified, ignoring this device.
[    20.421] (II) This device may have been added with another device file.
[    22.175] (II) intel(0): EDID vendor "AUO", prod id 13884
[    22.175] (II) intel(0): Printing DDC gathered Modelines:
[    22.175] (II) intel(0): Modeline "1366x768"x0.0   76.30  1366 1404 1426 1592  768 771 777 798 -hsync -vsync (47.9 kHz eP)
[    28.774] (II) XKB: reuse xkmfile /var/lib/xkb/server-24FF32AE97CE77240647F07462A493FCEC658CA7.xkm
[    28.782] (II) XKB: reuse xkmfile /var/lib/xkb/server-24FF32AE97CE77240647F07462A493FCEC658CA7.xkm
[    29.675] (II) XKB: reuse xkmfile /var/lib/xkb/server-D39A7DF07EFAADA1B152E688CBEB9ED49E8BFDBB.xkm
[    32.348] (II) XKB: reuse xkmfile /var/lib/xkb/server-B1CBD1E8DA710D50B426313517FD7AC2E1FC5733.xkm
[    47.069] (II) config/udev: removing device Microsoft Microsoft® Nano Transceiver v1.0
[    47.088] (II) evdev: Microsoft Microsoft® Nano Transceiver v1.0: Close
[    47.088] (II) UnloadModule: "evdev"
[    47.096] (II) config/udev: removing device Microsoft Microsoft® Nano Transceiver v1.0
[    47.112] (II) evdev: Microsoft Microsoft® Nano Transceiver v1.0: Close
[    47.112] (II) UnloadModule: "evdev"
[    47.140] (II) config/udev: removing device Microsoft Microsoft® Nano Transceiver v1.0
[    47.160] (II) evdev: Microsoft Microsoft® Nano Transceiver v1.0: Close
[    47.160] (II) UnloadModule: "evdev"
[  1598.857] (II) config/udev: removing device PS/2 Logitech Wheel Mouse
[  1598.873] (II) evdev: PS/2 Logitech Wheel Mouse: Close
[  1598.873] (II) UnloadModule: "evdev"
[  1637.534] (II) config/udev: Adding input device PS/2 Generic Mouse (/dev/input/mouse0)
[  1637.534] (II) No input driver specified, ignoring this device.
[  1637.534] (II) This device may have been added with another device file.
[  1637.534] (II) config/udev: Adding input device PS/2 Generic Mouse (/dev/input/event4)
[  1637.534] (**) PS/2 Generic Mouse: Applying InputClass "evdev pointer catchall"
[  1637.534] (II) Using input driver 'evdev' for 'PS/2 Generic Mouse'
[  1637.534] (**) PS/2 Generic Mouse: always reports core events
[  1637.534] (**) evdev: PS/2 Generic Mouse: Device: "/dev/input/event4"
[  1637.534] (--) evdev: PS/2 Generic Mouse: Vendor 0x2 Product 0x1
[  1637.534] (--) evdev: PS/2 Generic Mouse: Found 3 mouse buttons
[  1637.534] (--) evdev: PS/2 Generic Mouse: Found relative axes
[  1637.534] (--) evdev: PS/2 Generic Mouse: Found x and y relative axes
[  1637.535] (II) evdev: PS/2 Generic Mouse: Configuring as mouse
[  1637.535] (**) evdev: PS/2 Generic Mouse: YAxisMapping: buttons 4 and 5
[  1637.535] (**) evdev: PS/2 Generic Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  1637.535] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input556/event4"
[  1637.535] (II) XINPUT: Adding extended input device "PS/2 Generic Mouse" (type: MOUSE, id 11)
[  1637.535] (II) evdev: PS/2 Generic Mouse: initialized for relative axes.
[  1637.535] (**) PS/2 Generic Mouse: (accel) keeping acceleration scheme 1
[  1637.535] (**) PS/2 Generic Mouse: (accel) acceleration profile 0
[  1637.535] (**) PS/2 Generic Mouse: (accel) acceleration factor: 2.000
[  1637.535] (**) PS/2 Generic Mouse: (accel) acceleration threshold: 4
```

Hope you can help me with this.

Cheers!

---

