---
title: "Driver update for Asus X200M touchpad detected as PS/2 Logitech Wheel Mouse?"
date: 2015-08-09
forum: Hardware
---

### Post by Jim_D on 2015-08-09
Hi,

I have a new Asus X200M laptop (k200ma in the stores) with ubuntu 14.04.2 with all updates applied, and the touchpad isn't detected, it's listed as a PS/2 Logitech Wheel Mouse.  The mouse functions work fine (point and click) but there is no "Touchpad" in the Mouse and Touchpad settings and no gestures (like scrolling) are working.

I think this is the same laptop that [**[COLOR=#000000]Skarv[/COLOR]**]("http://ubuntuforums.org/member.php?u=1982168") and [**[COLOR=#000000]Pilot6[/COLOR]**]("http://ubuntuforums.org/member.php?u=1514892") say they have in thread [http://ubuntuforums.org/showthread.php?t=2246117](http://ubuntuforums.org/showthread.php?t=2246117), which sounds as though it has a Focaltech touchpad that requires a kernel update on top of 14.04.

From my X200M - devices:

```

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
U: Uniq=
H: Handlers=kbd event0 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0

I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
U: Uniq=
H: Handlers=event1 
B: PROP=0
B: EV=21
B: SW=1

I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
U: Uniq=
H: Handlers=kbd event2 
B: PROP=0
B: EV=3
B: KEY=4000 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input4
U: Uniq=
H: Handlers=sysrq kbd event4 
B: PROP=0
B: EV=120013
B: KEY=402000000 3803078f800d001 feffffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=7

I: Bus=0011 Vendor=0002 Product=0001 Version=0063
N: Name="PS/2 Logitech Wheel Mouse"
P: Phys=isa0060/serio4/input0
S: Sysfs=/devices/platform/i8042/serio4/input/input12
U: Uniq=
H: Handlers=mouse0 event5 
B: PROP=0
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=3

I: Bus=0003 Vendor=0457 Product=1028 Version=0111
N: Name="USBest Technology SiS HID Touch Controller"
P: Phys=usb-0000:00:14.0-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2:1.0/0003:0457:1028.0001/input/input13
U: Uniq=
H: Handlers=mouse1 event6 
B: PROP=2
B: EV=b
B: KEY=400 0 0 0 0 0
B: ABS=260800000000003

I: Bus=0003 Vendor=04f2 Product=b409 Version=6965
N: Name="USB2.0 HD UVC WebCam"
P: Phys=usb-0000:00:14.0-3/button
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3:1.0/input/input15
U: Uniq=
H: Handlers=kbd event7 
B: PROP=0
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0000 Version=0000
N: Name="Asus WMI hotkeys"
P: Phys=asus-nb-wmi/input0
S: Sysfs=/devices/platform/asus-nb-wmi/input/input16
U: Uniq=
H: Handlers=rfkill kbd event8 
B: PROP=0
B: EV=100013
B: KEY=80000 0 800000000000 0 0 a1606f00900000 8200027800501000 e000000000000 0
B: MSC=10

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input17
U: Uniq=
H: Handlers=kbd event9 
B: PROP=0
B: EV=3
B: KEY=3e000b00000000 0 0 0

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Headphone"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input18
U: Uniq=
H: Handlers=event10 
B: PROP=0
B: EV=21
B: SW=4

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH HDMI/DP,pcm=3"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input19
U: Uniq=
H: Handlers=event11 
B: PROP=0
B: EV=21
B: SW=140

```

xinput:

```

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; USBest Technology SiS HID Touch Controller    id=10    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Logitech Wheel Mouse                   id=14    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; USB2.0 HD UVC WebCam                        id=11    [slave  keyboard (3)]
    &#8627; Asus WMI hotkeys                            id=12    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=13    [slave  keyboard (3)]

```

Xorg.0.log:

```

[    34.541] 
X.Org X Server 1.16.0
Release Date: 2014-07-16
[    34.541] X Protocol Version 11, Revision 0
[    34.541] Build Operating System: Linux 3.2.0-70-generic x86_64 Ubuntu
[    34.541] Current Operating System: Linux magooch 3.16.0-45-generic #60~14.04.1-Ubuntu SMP Fri Jul 24 21:16:23 UTC 2015 x86_64
[    34.541] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.16.0-45-generic.efi.signed root=UUID=7c410e6b-2b73-47a4-8529-65a650e14de8 ro quiet splash vt.handoff=7
[    34.541] Build Date: 12 February 2015  11:11:26PM
[    34.541] xorg-server 2:1.16.0-1ubuntu1.2~trusty2 (For technical support please see http://www.ubuntu.com/support) 
[    34.541] Current version of pixman: 0.30.2
[    34.541]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    34.541] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    34.541] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Aug  8 17:46:33 2015
[    34.579] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    34.580] (==) No Layout section.  Using the first Screen section.
[    34.580] (==) No screen section available. Using defaults.
[    34.580] (**) |-->Screen "Default Screen Section" (0)
[    34.580] (**) |   |-->Monitor "<default monitor>"
[    34.580] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    34.580] (==) Automatically adding devices
[    34.580] (==) Automatically enabling devices
[    34.580] (==) Automatically adding GPU devices
[    34.580] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    34.580]     Entry deleted from font path.
[    34.580] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    34.580]     Entry deleted from font path.
[    34.580] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    34.580]     Entry deleted from font path.
[    34.580] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    34.580]     Entry deleted from font path.
[    34.580] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    34.580]     Entry deleted from font path.
[    34.580] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    34.580] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    34.580] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    34.580] (II) Loader magic: 0x7f0a904f7c80
[    34.580] (II) Module ABI versions:
[    34.580]     X.Org ANSI C Emulation: 0.4
[    34.580]     X.Org Video Driver: 18.0
[    34.581]     X.Org XInput driver : 21.0
[    34.581]     X.Org Server Extension : 8.0
[    34.581] (II) xfree86: Adding drm device (/dev/dri/card0)
[    34.583] (--) PCI:*(0:0:2:0) 8086:0f31:1043:15bd rev 14, Mem @ 0xd0000000/4194304, 0xc0000000/268435456, I/O @ 0x0000f080/8
[    34.583] (II) LoadModule: "glx"
[    34.584] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    34.778] (II) Module glx: vendor="X.Org Foundation"
[    34.778]     compiled for 1.16.0, module version = 1.0.0
[    34.778]     ABI class: X.Org Server Extension, version 8.0
[    34.778] (==) AIGLX enabled
[    34.778] (==) Matched intel as autoconfigured driver 0
[    34.778] (==) Matched intel as autoconfigured driver 1
[    34.778] (==) Matched modesetting as autoconfigured driver 2
[    34.778] (==) Matched fbdev as autoconfigured driver 3
[    34.778] (==) Matched vesa as autoconfigured driver 4
[    34.778] (==) Assigned the driver to the xf86ConfigLayout
[    34.778] (II) LoadModule: "intel"
[    34.779] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    34.839] (II) Module intel: vendor="X.Org Foundation"
[    34.839]     compiled for 1.16.0, module version = 2.99.914
[    34.839]     Module class: X.Org Video Driver
[    34.839]     ABI class: X.Org Video Driver, version 18.0
[    34.839] (II) LoadModule: "modesetting"
[    34.839] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    34.839] (II) Module modesetting: vendor="X.Org Foundation"
[    34.839]     compiled for 1.16.0, module version = 0.9.0
[    34.839]     Module class: X.Org Video Driver
[    34.839]     ABI class: X.Org Video Driver, version 18.0
[    34.839] (II) LoadModule: "fbdev"
[    34.840] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    34.840] (II) Module fbdev: vendor="X.Org Foundation"
[    34.840]     compiled for 1.16.0, module version = 0.4.4
[    34.840]     Module class: X.Org Video Driver
[    34.840]     ABI class: X.Org Video Driver, version 18.0
[    34.840] (II) LoadModule: "vesa"
[    34.840] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    34.840] (II) Module vesa: vendor="X.Org Foundation"
[    34.840]     compiled for 1.16.0, module version = 2.3.3
[    34.840]     Module class: X.Org Video Driver
[    34.840]     ABI class: X.Org Video Driver, version 18.0
[    34.840] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[    34.841] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[    34.841] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[    34.841] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[    34.841] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    34.841] (II) FBDEV: driver for framebuffer: fbdev
[    34.841] (II) VESA: driver for VESA chipsets: vesa
[    34.841] (++) using VT number 7

[    34.841] (II) intel(0): Using Kernel Mode Setting driver: i915, version 1.6.0 20080730
[    34.841] (II) intel(0): SNA compiled: xserver-xorg-video-intel-lts-utopic 2:2.99.914-1~exp1ubuntu4.5~trusty1 (Timo Aaltonen <tjaalton@debian.org>)
[    34.841] (II) intel(0): SNA compiled for use with valgrind
[    34.841] (WW) Falling back to old probe method for modesetting
[    34.842] (WW) Falling back to old probe method for fbdev
[    34.842] (II) Loading sub module "fbdevhw"
[    34.842] (II) LoadModule: "fbdevhw"
[    34.842] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    34.842] (II) Module fbdevhw: vendor="X.Org Foundation"
[    34.842]     compiled for 1.16.0, module version = 0.0.2
[    34.842]     ABI class: X.Org Video Driver, version 18.0
[    34.842] (WW) Falling back to old probe method for vesa
[    34.843] (--) intel(0): Integrated Graphics Chipset: Intel(R) HD Graphics
[    34.843] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2
[    34.843] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    34.843] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    34.843] (==) intel(0): RGB weight 888
[    34.843] (==) intel(0): Default visual is TrueColor
[    34.843] (II) intel(0): Output eDP1 has no monitor section
[    34.843] (--) intel(0): Found backlight control interface intel_backlight (type 'raw') for output eDP1
[    34.843] (II) intel(0): Output VGA1 has no monitor section
[    34.843] (II) intel(0): Output HDMI1 has no monitor section
[    34.843] (II) intel(0): Output DP1 has no monitor section
[    34.843] (II) intel(0): Output HDMI2 has no monitor section
[    34.843] (--) intel(0): Using a maximum size of 256x256 for hardware cursors
[    34.844] (II) intel(0): Output VIRTUAL1 has no monitor section
[    34.844] (--) intel(0): Output eDP1 using initial mode 1366x768 on pipe 0
[    34.844] (==) intel(0): TearFree disabled
[    34.844] (==) intel(0): DPI set to (96, 96)
[    34.844] (II) Loading sub module "dri2"
[    34.844] (II) LoadModule: "dri2"
[    34.844] (II) Module "dri2" already built-in
[    34.844] (II) Loading sub module "present"
[    34.844] (II) LoadModule: "present"
[    34.844] (II) Module "present" already built-in
[    34.844] (II) UnloadModule: "modesetting"
[    34.844] (II) Unloading modesetting
[    34.844] (II) UnloadModule: "fbdev"
[    34.844] (II) Unloading fbdev
[    34.844] (II) UnloadSubModule: "fbdevhw"
[    34.844] (II) Unloading fbdevhw
[    34.844] (II) UnloadModule: "vesa"
[    34.844] (II) Unloading vesa
[    34.844] (==) Depth 24 pixmap format is 32 bpp
[    34.845] (II) intel(0): SNA initialized with Baytrail (gen7) backend
[    34.845] (==) intel(0): Backing store enabled
[    34.845] (==) intel(0): Silken mouse enabled
[    34.845] (II) intel(0): HW Cursor enabled
[    34.845] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    34.845] (==) intel(0): DPMS enabled
[    34.845] (II) intel(0): [DRI2] Setup complete
[    34.845] (II) intel(0): [DRI2]   DRI driver: i965
[    34.845] (II) intel(0): [DRI2]   VDPAU driver: i965
[    34.845] (II) intel(0): direct rendering: DRI2 enabled
[    34.845] (II) intel(0): hardware support for Present enabled
[    34.845] (==) intel(0): display hotplug detection enabled
[    34.845] (--) RandR disabled
[    35.026] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    35.027] (II) AIGLX: enabled GLX_ARB_create_context
[    35.027] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    35.027] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    35.027] (II) AIGLX: enabled GLX_INTEL_swap_event
[    35.027] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    35.027] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[    35.027] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[    35.027] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    35.027] (II) AIGLX: enabled GLX_ARB_create_context_robustness
[    35.027] (II) AIGLX: Loaded and initialized i965
[    35.027] (II) GLX: Initialized DRI2 GL provider for screen 0
[    35.034] (II) intel(0): switch to mode 1366x768@60.0 on eDP1 using pipe 0, position (0, 0), rotation normal, reflection none
[    35.048] (II) intel(0): Setting screen physical size to 361 x 203
[    35.059] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    35.063] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    35.063] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    35.063] (II) LoadModule: "evdev"
[    35.064] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    35.086] (II) Module evdev: vendor="X.Org Foundation"
[    35.086]     compiled for 1.16.0, module version = 2.9.0
[    35.086]     Module class: X.Org XInput Driver
[    35.086]     ABI class: X.Org XInput driver, version 21.0
[    35.086] (II) Using input driver 'evdev' for 'Power Button'
[    35.086] (**) Power Button: always reports core events
[    35.086] (**) evdev: Power Button: Device: "/dev/input/event3"
[    35.086] (--) evdev: Power Button: Vendor 0 Product 0x1
[    35.086] (--) evdev: Power Button: Found keys
[    35.086] (II) evdev: Power Button: Configuring as keyboard
[    35.086] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    35.086] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    35.086] (**) Option "xkb_rules" "evdev"
[    35.086] (**) Option "xkb_model" "pc105"
[    35.086] (**) Option "xkb_layout" "us"
[    35.087] (II) config/udev: Adding input device Video Bus (/dev/input/event9)
[    35.087] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    35.087] (II) Using input driver 'evdev' for 'Video Bus'
[    35.087] (**) Video Bus: always reports core events
[    35.087] (**) evdev: Video Bus: Device: "/dev/input/event9"
[    35.087] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    35.087] (--) evdev: Video Bus: Found keys
[    35.087] (II) evdev: Video Bus: Configuring as keyboard
[    35.087] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input17/event9"
[    35.087] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    35.087] (**) Option "xkb_rules" "evdev"
[    35.087] (**) Option "xkb_model" "pc105"
[    35.087] (**) Option "xkb_layout" "us"
[    35.088] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    35.088] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    35.088] (II) Using input driver 'evdev' for 'Power Button'
[    35.088] (**) Power Button: always reports core events
[    35.088] (**) evdev: Power Button: Device: "/dev/input/event0"
[    35.088] (--) evdev: Power Button: Vendor 0 Product 0x1
[    35.088] (--) evdev: Power Button: Found keys
[    35.088] (II) evdev: Power Button: Configuring as keyboard
[    35.088] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    35.088] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    35.088] (**) Option "xkb_rules" "evdev"
[    35.088] (**) Option "xkb_model" "pc105"
[    35.089] (**) Option "xkb_layout" "us"
[    35.089] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[    35.089] (II) No input driver specified, ignoring this device.
[    35.089] (II) This device may have been added with another device file.
[    35.090] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    35.090] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    35.090] (II) Using input driver 'evdev' for 'Sleep Button'
[    35.090] (**) Sleep Button: always reports core events
[    35.090] (**) evdev: Sleep Button: Device: "/dev/input/event2"
[    35.090] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    35.090] (--) evdev: Sleep Button: Found keys
[    35.090] (II) evdev: Sleep Button: Configuring as keyboard
[    35.090] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2/event2"
[    35.090] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[    35.090] (**) Option "xkb_rules" "evdev"
[    35.090] (**) Option "xkb_model" "pc105"
[    35.090] (**) Option "xkb_layout" "us"
[    35.091] (II) config/udev: Adding input device USBest Technology SiS HID Touch Controller (/dev/input/event6)
[    35.091] (**) USBest Technology SiS HID Touch Controller: Applying InputClass "evdev touchscreen catchall"
[    35.091] (II) Using input driver 'evdev' for 'USBest Technology SiS HID Touch Controller'
[    35.091] (**) USBest Technology SiS HID Touch Controller: always reports core events
[    35.091] (**) evdev: USBest Technology SiS HID Touch Controller: Device: "/dev/input/event6"
[    35.091] (--) evdev: USBest Technology SiS HID Touch Controller: Vendor 0x457 Product 0x1028
[    35.091] (--) evdev: USBest Technology SiS HID Touch Controller: Found absolute axes
[    35.091] (--) evdev: USBest Technology SiS HID Touch Controller: Found absolute multitouch axes
[    35.091] (II) evdev: USBest Technology SiS HID Touch Controller: No buttons found, faking one.
[    35.091] (--) evdev: USBest Technology SiS HID Touch Controller: Found x and y absolute axes
[    35.091] (--) evdev: USBest Technology SiS HID Touch Controller: Found absolute touchscreen
[    35.091] (II) evdev: USBest Technology SiS HID Touch Controller: Configuring as touchscreen
[    35.091] (**) evdev: USBest Technology SiS HID Touch Controller: YAxisMapping: buttons 4 and 5
[    35.091] (**) evdev: USBest Technology SiS HID Touch Controller: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    35.091] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2:1.0/0003:0457:1028.0001/input/input13/event6"
[    35.092] (II) XINPUT: Adding extended input device "USBest Technology SiS HID Touch Controller" (type: TOUCHSCREEN, id 10)
[    35.092] (II) evdev: USBest Technology SiS HID Touch Controller: initialized for absolute axes.
[    35.092] (**) USBest Technology SiS HID Touch Controller: (accel) keeping acceleration scheme 1
[    35.092] (**) USBest Technology SiS HID Touch Controller: (accel) acceleration profile 0
[    35.092] (**) USBest Technology SiS HID Touch Controller: (accel) acceleration factor: 2.000
[    35.092] (**) USBest Technology SiS HID Touch Controller: (accel) acceleration threshold: 4
[    35.093] (II) config/udev: Adding input device USBest Technology SiS HID Touch Controller (/dev/input/mouse1)
[    35.093] (II) No input driver specified, ignoring this device.
[    35.093] (II) This device may have been added with another device file.
[    35.093] (II) config/udev: Adding input device USB2.0 HD UVC WebCam (/dev/input/event7)
[    35.093] (**) USB2.0 HD UVC WebCam: Applying InputClass "evdev keyboard catchall"
[    35.093] (II) Using input driver 'evdev' for 'USB2.0 HD UVC WebCam'
[    35.093] (**) USB2.0 HD UVC WebCam: always reports core events
[    35.093] (**) evdev: USB2.0 HD UVC WebCam: Device: "/dev/input/event7"
[    35.093] (--) evdev: USB2.0 HD UVC WebCam: Vendor 0x4f2 Product 0xb409
[    35.093] (--) evdev: USB2.0 HD UVC WebCam: Found keys
[    35.094] (II) evdev: USB2.0 HD UVC WebCam: Configuring as keyboard
[    35.094] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3:1.0/input/input15/event7"
[    35.094] (II) XINPUT: Adding extended input device "USB2.0 HD UVC WebCam" (type: KEYBOARD, id 11)
[    35.094] (**) Option "xkb_rules" "evdev"
[    35.094] (**) Option "xkb_model" "pc105"
[    35.094] (**) Option "xkb_layout" "us"
[    35.094] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event10)
[    35.094] (II) No input driver specified, ignoring this device.
[    35.094] (II) This device may have been added with another device file.
[    35.095] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event11)
[    35.095] (II) No input driver specified, ignoring this device.
[    35.095] (II) This device may have been added with another device file.
[    35.095] (II) config/udev: Adding input device Asus WMI hotkeys (/dev/input/event8)
[    35.095] (**) Asus WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    35.095] (II) Using input driver 'evdev' for 'Asus WMI hotkeys'
[    35.095] (**) Asus WMI hotkeys: always reports core events
[    35.095] (**) evdev: Asus WMI hotkeys: Device: "/dev/input/event8"
[    35.095] (--) evdev: Asus WMI hotkeys: Vendor 0 Product 0
[    35.095] (--) evdev: Asus WMI hotkeys: Found keys
[    35.095] (II) evdev: Asus WMI hotkeys: Configuring as keyboard
[    35.095] (**) Option "config_info" "udev:/sys/devices/platform/asus-nb-wmi/input/input16/event8"
[    35.096] (II) XINPUT: Adding extended input device "Asus WMI hotkeys" (type: KEYBOARD, id 12)
[    35.096] (**) Option "xkb_rules" "evdev"
[    35.096] (**) Option "xkb_model" "pc105"
[    35.096] (**) Option "xkb_layout" "us"
[    35.096] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    35.096] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    35.096] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    35.096] (**) AT Translated Set 2 keyboard: always reports core events
[    35.097] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    35.097] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    35.097] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    35.097] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    35.097] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    35.097] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 13)
[    35.097] (**) Option "xkb_rules" "evdev"
[    35.097] (**) Option "xkb_model" "pc105"
[    35.097] (**) Option "xkb_layout" "us"
[    35.097] (II) config/udev: Adding input device PS/2 Logitech Wheel Mouse (/dev/input/event5)
[    35.098] (**) PS/2 Logitech Wheel Mouse: Applying InputClass "evdev pointer catchall"
[    35.098] (II) Using input driver 'evdev' for 'PS/2 Logitech Wheel Mouse'
[    35.098] (**) PS/2 Logitech Wheel Mouse: always reports core events
[    35.098] (**) evdev: PS/2 Logitech Wheel Mouse: Device: "/dev/input/event5"
[    35.098] (--) evdev: PS/2 Logitech Wheel Mouse: Vendor 0x2 Product 0x1
[    35.098] (--) evdev: PS/2 Logitech Wheel Mouse: Found 3 mouse buttons
[    35.098] (--) evdev: PS/2 Logitech Wheel Mouse: Found relative axes
[    35.098] (--) evdev: PS/2 Logitech Wheel Mouse: Found x and y relative axes
[    35.098] (II) evdev: PS/2 Logitech Wheel Mouse: Configuring as mouse
[    35.098] (**) evdev: PS/2 Logitech Wheel Mouse: YAxisMapping: buttons 4 and 5
[    35.098] (**) evdev: PS/2 Logitech Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    35.098] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio4/input/input12/event5"
[    35.098] (II) XINPUT: Adding extended input device "PS/2 Logitech Wheel Mouse" (type: MOUSE, id 14)
[    35.098] (II) evdev: PS/2 Logitech Wheel Mouse: initialized for relative axes.
[    35.098] (**) PS/2 Logitech Wheel Mouse: (accel) keeping acceleration scheme 1
[    35.098] (**) PS/2 Logitech Wheel Mouse: (accel) acceleration profile 0
[    35.098] (**) PS/2 Logitech Wheel Mouse: (accel) acceleration factor: 2.000
[    35.098] (**) PS/2 Logitech Wheel Mouse: (accel) acceleration threshold: 4
[    35.099] (II) config/udev: Adding input device PS/2 Logitech Wheel Mouse (/dev/input/mouse0)
[    35.099] (II) No input driver specified, ignoring this device.
[    35.099] (II) This device may have been added with another device file.
[    37.528] (II) intel(0): EDID vendor "CMN", prod id 4400
[    37.528] (II) intel(0): Printing DDC gathered Modelines:
[    37.528] (II) intel(0): Modeline "1366x768"x0.0   76.00  1366 1436 1482 1599  768 771 776 792 -hsync -vsync (47.5 kHz eP)
[    52.226] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    54.894] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    54.915] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    61.064] (II) XKB: reuse xkmfile /var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm

```

dmesg |grep pnp:

```

[    0.261829] pnp: PnP ACPI init
[    0.261942] pnp 00:00: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.262480] pnp 00:03: Plug and Play ACPI device, IDs FLT0102 SYN0a00 SYN0002 PNP0f03 PNP0f13 PNP0f12 (active)
[    0.262572] pnp 00:04: Plug and Play ACPI device, IDs ATK3001 PNP030b (active)
[    0.264529] pnp: PnP ACPI: found 6 devices

```

uname -a:

```

Linux magooch 3.16.0-45-generic #60~14.04.1-Ubuntu SMP Fri Jul 24 21:16:23 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

```

I installed dkms, and "dkms status" has no output.

A later post in that thread from July recommended for 14.04:

```

sudo add-apt-repository ppa:hanipouspilot/focaltech-dkms
sudo apt-get update
sudo apt-get install linux-generic-lts-vivid focaltech-dkms

```

Does it sound like I have a Focaltech touchpad, and that this is why it's not detected / has no Touchpad settings / doesn't recognize gestures?

Are the above PPA packages from ppa:hanipouspilot/focaltech-dkms, linux-generic-lts-vivid and focaltech-dkms, the best way to get the Focaltech touchpad recognized?

Does linux-generic-lts-vivid install a new kernel?  If so, does the original kernel stick around as an option I can select in GRUB, or is the original kernel completely replaced?

Thanks in advance!

Jim

---

### Post by Jim_D on 2015-08-13
I installed the PPA packages:

```

sudo add-apt-repository ppa:hanipouspilot/focaltech-dkms
sudo apt-get update
sudo apt-get install linux-generic-lts-vivid 
(reboot into kernel 3.19 that's now the default)
sudo apt-get install focaltech-dkms

```

Note that I think I had trouble installing linux-generic-lts-vivid and focaltech-dkms in the same command, 
because it would attempt to compile focaltech-dkms under kernel 3.16 and fail.

I think I also had to install the dkms package (from the regular Ubuntu repositories) first.

Touchpad works fine now in 3.19:
- xinput reports Focaltech touchpad
- Touchpad settings are in Mouse & Touchpad
- Two-finger scroll works

The only lingering issue is a "System program problem detected" dialog that pops up when I log in, which I think is apport trying to 
report a problem back to ubuntu.  I have to look more into what that is about.

Thanks to Pilot6 for the PPA, packages, and instructions!

Thanks,
Jim

---

### Post by Jim_D on 2015-08-13
Also, an answer to my own question, after installing the kernel PPA package, 3.19 is the default kernel, but 3.16.0-45 sticks around as an option in grub should it be needed.

---

### Post by dino99 on 2015-08-13
its a good idea to have the latest known working kernel installed , and the latest upgrade; so if you hit some trouble with one, you then still can choose the other to boot with.
'synaptic' is a user friendly app to deal with package: installing/purging/changelog/...

---

