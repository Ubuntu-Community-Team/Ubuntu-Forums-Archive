---
title: "Display issues on Dell Inspiron 1100"
date: 2014-06-04
forum: Hardware
---

### Post by Mike_Dean on 2014-06-04
Greetings...
I am a (somewhat) new Linux user....I have installed Ubuntu 14.04 on my Dell Inspiron 1100 (2008 model), and have found that the Ubuntu window (along with a couple of other distros I've installed)...
Relevant (I hope) specs):
Processors . . . . . . . . . . . . . . . . . . . . . . . . . . . Intel® Celeron® 4 Processor running at 2.0GHz
Chipset . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . Intel 845GL
Memory. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . Standard: 128MB PC2100 DDR SDRAM; maximum: 512MB PC2100 DDR SDRAM; memory modules
available: 128MB or 256MB SODIMMs
Display . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 14.1" XGA TFT with 1024 x 768 at 16.7 million colours (32-bit colour depth)
15" XGA TFT with 1024 x 768 at 16.7 million colours (32-bit colour depth)
Maximum External Resolution (CRT) . . . . . 1400 x 1050 (SXGA+) at 60Hz
Video . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . Video type – Direct AGP integrated graphics
Video memory – up to 32MB (with 128MB of system memory) or 64MB (with 256MB or more system memory)
From the attached picture, the 14.1 diagonal screen is using about a 7x5.5 inch rectangle, and at a loss to how to get the window to fill the entire screen :confused:
While I'm really desirous of using Ubuntu (or some version of Linux), this stands as a major obstacle

---

### Post by grahammechanical on 2014-06-04
You do not tell us which of the two memory options your machine has. I really does not matter as the maximum of 512MB is close to the minimum and what makes the matter worse is some system memory is being used as video memory. Minimum system memory for Ubuntu is 512MB and in my opinion there should also be 512MB to 1GB of memory on the video adapter.

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

Regards

---

### Post by Mike_Dean on 2014-06-04
Let me look at the system info ... fires up machine....Memory says: 1000.8 MiB (so about a GiB)

---

### Post by Mike_Dean on 2014-06-04
Also: Graphics says Intel 845G/x86/MMX/SSE2 ...  Processor: Intel Celeron CPU 2.00 GHz (32 bit OS)

---

### Post by Yellow Pasque on 2014-06-04
Post the /var/log/Xorg.0.log (use code tags).

---

### Post by ajgreeny on 2014-06-04
With those specs I think you would find either Xubuntu or Lubuntu much faster and useful to you.  I don't think you will ever get ubuntu with unity to run well on that machine, and even if it will run, it's likely to be a bit like wading through treacle, ie very slow and difficult to use.

---

### Post by Mike_Dean on 2014-06-05
OK, once I figure out where to find the log....

---

### Post by Mike_Dean on 2014-06-05
Hope I did this correctly:confused:
```

[    43.175] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[    43.175] X Protocol Version 11, Revision 0
[    43.175] Build Operating System: Linux 3.2.0-37-generic i686 Ubuntu
[    43.175] Current Operating System: Linux mike-Inspiron-1100 3.13.0-27-generic #50-Ubuntu SMP Thu May 15 18:08:16 UTC 2014 i686
[    43.175] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-27-generic root=UUID=30820e29-f25f-41fb-b258-05898cc46247 ro quiet splash vt.handoff=7
[    43.189] Build Date: 16 April 2014  01:40:08PM
[    43.189] xorg-server 2:1.15.1-0ubuntu2 (For technical support please see http://www.ubuntu.com/support) 
[    43.189] Current version of pixman: 0.30.2
[    43.189]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    43.189] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    43.190] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Jun  5 10:21:56 2014
[    43.207] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    43.208] (==) No Layout section.  Using the first Screen section.
[    43.208] (==) No screen section available. Using defaults.
[    43.209] (**) |-->Screen "Default Screen Section" (0)
[    43.209] (**) |   |-->Monitor "<default monitor>"
[    43.209] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    43.209] (==) Automatically adding devices
[    43.209] (==) Automatically enabling devices
[    43.210] (==) Automatically adding GPU devices
[    43.210] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    43.210]     Entry deleted from font path.
[    43.211] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    43.211]     Entry deleted from font path.
[    43.211] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    43.211]     Entry deleted from font path.
[    43.211] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    43.211]     Entry deleted from font path.
[    43.211] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    43.211]     Entry deleted from font path.
[    43.211] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    43.211] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    43.211] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    43.211] (II) Loader magic: 0xb772c6c0
[    43.212] (II) Module ABI versions:
[    43.212]     X.Org ANSI C Emulation: 0.4
[    43.212]     X.Org Video Driver: 15.0
[    43.212]     X.Org XInput driver : 20.0
[    43.212]     X.Org Server Extension : 8.0
[    43.214] (II) xfree86: Adding drm device (/dev/dri/card0)
[    43.219] (--) PCI:*(0:0:2:0) 8086:2562:1028:0149 rev 3, Mem @ 0xe0000000/134217728, 0xf6f80000/524288
[    43.219] Initializing built-in extension Generic Event Extension
[    43.219] Initializing built-in extension SHAPE
[    43.219] Initializing built-in extension MIT-SHM
[    43.219] Initializing built-in extension XInputExtension
[    43.219] Initializing built-in extension XTEST
[    43.220] Initializing built-in extension BIG-REQUESTS
[    43.220] Initializing built-in extension SYNC
[    43.220] Initializing built-in extension XKEYBOARD
[    43.220] Initializing built-in extension XC-MISC
[    43.220] Initializing built-in extension SECURITY
[    43.220] Initializing built-in extension XINERAMA
[    43.220] Initializing built-in extension XFIXES
[    43.220] Initializing built-in extension RENDER
[    43.220] Initializing built-in extension RANDR
[    43.221] Initializing built-in extension COMPOSITE
[    43.221] Initializing built-in extension DAMAGE
[    43.221] Initializing built-in extension MIT-SCREEN-SAVER
[    43.221] Initializing built-in extension DOUBLE-BUFFER
[    43.221] Initializing built-in extension RECORD
[    43.221] Initializing built-in extension DPMS
[    43.221] Initializing built-in extension Present
[    43.222] Initializing built-in extension DRI3
[    43.222] Initializing built-in extension X-Resource
[    43.222] Initializing built-in extension XVideo
[    43.222] Initializing built-in extension XVideo-MotionCompensation
[    43.222] Initializing built-in extension SELinux
[    43.222] Initializing built-in extension XFree86-VidModeExtension
[    43.222] Initializing built-in extension XFree86-DGA
[    43.222] Initializing built-in extension XFree86-DRI
[    43.222] Initializing built-in extension DRI2
[    43.222] (II) LoadModule: "glx"
[    43.241] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    43.419] (II) Module glx: vendor="X.Org Foundation"
[    43.420]     compiled for 1.15.1, module version = 1.0.0
[    43.420]     ABI class: X.Org Server Extension, version 8.0
[    43.420] (==) AIGLX enabled
[    43.420] Loading extension GLX
[    43.420] (==) Matched intel as autoconfigured driver 0
[    43.420] (==) Matched intel as autoconfigured driver 1
[    43.420] (==) Matched modesetting as autoconfigured driver 2
[    43.421] (==) Matched fbdev as autoconfigured driver 3
[    43.421] (==) Matched vesa as autoconfigured driver 4
[    43.421] (==) Assigned the driver to the xf86ConfigLayout
[    43.421] (II) LoadModule: "intel"
[    43.432] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    43.453] (II) Module intel: vendor="X.Org Foundation"
[    43.454]     compiled for 1.15.0, module version = 2.99.910
[    43.454]     Module class: X.Org Video Driver
[    43.454]     ABI class: X.Org Video Driver, version 15.0
[    43.454] (II) LoadModule: "modesetting"
[    43.455] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    43.456] (II) Module modesetting: vendor="X.Org Foundation"
[    43.456]     compiled for 1.15.0, module version = 0.8.1
[    43.456]     Module class: X.Org Video Driver
[    43.456]     ABI class: X.Org Video Driver, version 15.0
[    43.456] (II) LoadModule: "fbdev"
[    43.457] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    43.458] (II) Module fbdev: vendor="X.Org Foundation"
[    43.458]     compiled for 1.15.0, module version = 0.4.4
[    43.458]     Module class: X.Org Video Driver
[    43.458]     ABI class: X.Org Video Driver, version 15.0
[    43.458] (II) LoadModule: "vesa"
[    43.459] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    43.460] (II) Module vesa: vendor="X.Org Foundation"
[    43.460]     compiled for 1.15.0, module version = 2.3.3
[    43.460]     Module class: X.Org Video Driver
[    43.460]     ABI class: X.Org Video Driver, version 15.0
[    43.460] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[    43.463] (II) intel: Driver for Intel(R) HD Graphics: 2000-5000
[    43.463] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100
[    43.463] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200
[    43.463] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    43.463] (II) FBDEV: driver for framebuffer: fbdev
[    43.463] (II) VESA: driver for VESA chipsets: vesa
[    43.463] (++) using VT number 7


[    43.464] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.99.910-0ubuntu1 (Timo Aaltonen <tjaalton@ubuntu.com>)
[    43.465] (WW) Falling back to old probe method for modesetting
[    43.465] (WW) Falling back to old probe method for fbdev
[    43.465] (II) Loading sub module "fbdevhw"
[    43.465] (II) LoadModule: "fbdevhw"
[    43.466] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    43.467] (II) Module fbdevhw: vendor="X.Org Foundation"
[    43.467]     compiled for 1.15.1, module version = 0.0.2
[    43.467]     ABI class: X.Org Video Driver, version 15.0
[    43.467] (WW) Falling back to old probe method for vesa
[    43.470] (--) intel(0): Integrated Graphics Chipset: Intel(R) 845G
[    43.471] (--) intel(0): CPU: x86, sse2
[    43.471] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    43.471] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    43.471] (==) intel(0): RGB weight 888
[    43.471] (==) intel(0): Default visual is TrueColor
[    43.473] (**) intel(0): Framebuffer tiled
[    43.473] (**) intel(0): Pixmaps tiled
[    43.473] (**) intel(0): "Tear free" disabled
[    43.473] (**) intel(0): Forcing per-crtc-pixmaps? no
[    43.473] (II) intel(0): Output LVDS1 has no monitor section
[    43.479] (--) intel(0): found backlight control interface dell_backlight (type 'platform')
[    43.479] (II) intel(0): Output VGA1 has no monitor section
[    43.479] (II) intel(0): Output VIRTUAL1 has no monitor section
[    43.480] (--) intel(0): Output LVDS1 using initial mode 640x480 on pipe 0
[    43.480] (==) intel(0): DPI set to (96, 96)
[    43.480] (II) Loading sub module "dri2"
[    43.480] (II) LoadModule: "dri2"
[    43.480] (II) Module "dri2" already built-in
[    43.481] (II) UnloadModule: "modesetting"
[    43.481] (II) Unloading modesetting
[    43.482] (II) UnloadModule: "fbdev"
[    43.482] (II) Unloading fbdev
[    43.482] (II) UnloadSubModule: "fbdevhw"
[    43.482] (II) Unloading fbdevhw
[    43.482] (II) UnloadModule: "vesa"
[    43.482] (II) Unloading vesa
[    43.483] (==) Depth 24 pixmap format is 32 bpp
[    43.483] (II) intel(0): SNA initialized with Almador (gen2) backend
[    43.483] (==) intel(0): Backing store enabled
[    43.483] (==) intel(0): Silken mouse enabled
[    43.484] (II) intel(0): HW Cursor enabled
[    43.484] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    43.484] (==) intel(0): DPMS enabled
[    43.485] (II) intel(0): Textured video not supported on this hardware
[    43.485] (II) intel(0): [DRI2] Setup complete
[    43.485] (II) intel(0): [DRI2]   DRI driver: i915
[    43.485] (II) intel(0): [DRI2]   VDPAU driver: i915
[    43.485] (II) intel(0): direct rendering: DRI2 Enabled
[    43.485] (==) intel(0): hotplug detection: "enabled"
[    43.486] (--) RandR disabled
[    43.506] (II) SELinux: Disabled on system
[    43.551] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    43.551] (II) AIGLX: enabled GLX_ARB_create_context
[    43.551] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    43.551] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    43.551] (II) AIGLX: enabled GLX_INTEL_swap_event
[    43.552] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    43.552] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[    43.552] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[    43.552] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    43.552] (II) AIGLX: Loaded and initialized i915
[    43.552] (II) GLX: Initialized DRI2 GL provider for screen 0
[    43.561] (II) intel(0): switch to mode 640x480@60.0 on LVDS1 using pipe 0, position (0, 0), rotation normal, reflection none
[    43.598] (II) intel(0): Setting screen physical size to 169 x 126
[    43.629] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    43.642] (II) config/udev: Adding input device Video Bus (/dev/input/event6)
[    43.643] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    43.643] (II) LoadModule: "evdev"
[    43.644] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    43.663] (II) Module evdev: vendor="X.Org Foundation"
[    43.664]     compiled for 1.15.0, module version = 2.8.2
[    43.664]     Module class: X.Org XInput Driver
[    43.664]     ABI class: X.Org XInput driver, version 20.0
[    43.664] (II) Using input driver 'evdev' for 'Video Bus'
[    43.664] (**) Video Bus: always reports core events
[    43.664] (**) evdev: Video Bus: Device: "/dev/input/event6"
[    43.665] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    43.665] (--) evdev: Video Bus: Found keys
[    43.665] (II) evdev: Video Bus: Configuring as keyboard
[    43.665] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input7/event6"
[    43.665] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 6)
[    43.665] (**) Option "xkb_rules" "evdev"
[    43.665] (**) Option "xkb_model" "pc105"
[    43.666] (**) Option "xkb_layout" "us"
[    43.669] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    43.669] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    43.669] (II) Using input driver 'evdev' for 'Power Button'
[    43.669] (**) Power Button: always reports core events
[    43.669] (**) evdev: Power Button: Device: "/dev/input/event1"
[    43.669] (--) evdev: Power Button: Vendor 0 Product 0x1
[    43.669] (--) evdev: Power Button: Found keys
[    43.669] (II) evdev: Power Button: Configuring as keyboard
[    43.670] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[    43.670] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    43.670] (**) Option "xkb_rules" "evdev"
[    43.670] (**) Option "xkb_model" "pc105"
[    43.670] (**) Option "xkb_layout" "us"
[    43.673] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    43.673] (II) No input driver specified, ignoring this device.
[    43.673] (II) This device may have been added with another device file.
[    43.675] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    43.675] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    43.675] (II) Using input driver 'evdev' for 'Sleep Button'
[    43.675] (**) Sleep Button: always reports core events
[    43.675] (**) evdev: Sleep Button: Device: "/dev/input/event2"
[    43.676] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    43.676] (--) evdev: Sleep Button: Found keys
[    43.676] (II) evdev: Sleep Button: Configuring as keyboard
[    43.676] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2/event2"
[    43.676] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 8)
[    43.676] (**) Option "xkb_rules" "evdev"
[    43.676] (**) Option "xkb_model" "pc105"
[    43.676] (**) Option "xkb_layout" "us"
[    43.678] (II) config/udev: Adding drm device (/dev/dri/card0)
[    43.678] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    43.680] (II) config/udev: Adding input device Logitech USB Trackball (/dev/input/event4)
[    43.681] (**) Logitech USB Trackball: Applying InputClass "evdev pointer catchall"
[    43.681] (II) Using input driver 'evdev' for 'Logitech USB Trackball'
[    43.681] (**) Logitech USB Trackball: always reports core events
[    43.681] (**) evdev: Logitech USB Trackball: Device: "/dev/input/event4"
[    43.681] (--) evdev: Logitech USB Trackball: Vendor 0x46d Product 0xc408
[    43.681] (--) evdev: Logitech USB Trackball: Found 9 mouse buttons
[    43.681] (--) evdev: Logitech USB Trackball: Found relative axes
[    43.681] (--) evdev: Logitech USB Trackball: Found x and y relative axes
[    43.682] (II) evdev: Logitech USB Trackball: Configuring as mouse
[    43.682] (**) evdev: Logitech USB Trackball: YAxisMapping: buttons 4 and 5
[    43.682] (**) evdev: Logitech USB Trackball: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    43.682] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-1/1-1.1/1-1.1:1.0/input/input6/event4"
[    43.682] (II) XINPUT: Adding extended input device "Logitech USB Trackball" (type: MOUSE, id 9)
[    43.682] (II) evdev: Logitech USB Trackball: initialized for relative axes.
[    43.683] (**) Logitech USB Trackball: (accel) keeping acceleration scheme 1
[    43.683] (**) Logitech USB Trackball: (accel) acceleration profile 0
[    43.683] (**) Logitech USB Trackball: (accel) acceleration factor: 2.000
[    43.683] (**) Logitech USB Trackball: (accel) acceleration threshold: 4
[    43.685] (II) config/udev: Adding input device Logitech USB Trackball (/dev/input/mouse0)
[    43.686] (II) No input driver specified, ignoring this device.
[    43.686] (II) This device may have been added with another device file.
[    43.688] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    43.688] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    43.688] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    43.688] (**) AT Translated Set 2 keyboard: always reports core events
[    43.688] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    43.689] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    43.689] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    43.689] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    43.689] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    43.689] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 10)
[    43.689] (**) Option "xkb_rules" "evdev"
[    43.689] (**) Option "xkb_model" "pc105"
[    43.689] (**) Option "xkb_layout" "us"
[    43.692] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event5)
[    43.692] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    43.692] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    43.692] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[    43.692] (II) LoadModule: "synaptics"
[    43.693] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    43.694] (II) Module synaptics: vendor="X.Org Foundation"
[    43.694]     compiled for 1.15.0, module version = 1.7.4
[    43.694]     Module class: X.Org XInput Driver
[    43.694]     ABI class: X.Org XInput driver, version 20.0
[    43.694] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    43.694] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    43.695] (**) Option "Device" "/dev/input/event5"
[    43.696] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472 (res 85)
[    43.697] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448 (res 94)
[    43.697] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    43.697] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    43.697] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    43.697] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    43.697] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    43.697] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    43.697] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input5/event5"
[    43.698] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 11)
[    43.698] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    43.698] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[    43.698] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.040
[    43.698] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    43.699] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    43.699] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    43.699] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    43.699] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    43.701] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
[    43.701] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    55.187] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    61.085] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    61.284] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    76.985] (II) XKB: reuse xkmfile /var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm

```

---

### Post by Mike_Dean on 2014-06-05
AJG: Seeing how the current installation is going (real-time slo-mo), I'll give xubunta/lubuntu a go. Thanks.

---

### Post by Yellow Pasque on 2014-06-05
Yes, you posted the log correctly.

Usually, the logs gives more info about trying different resolutions, but in the case of these old intel graphics, it seems the driver only tried 640x480 and stuck with it.
I would try setting some better modes with xrandr (Your output is LVDS1): [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

### Post by Mike_Dean on 2014-06-05
Not faring well in getting the driver to recognize other resolutions (I installed xubuntu, hoping the lighter requirements would enable the system to go faster. It is responding quicker than on "regular" Ubuntu)

Here is the terminal session:

mike@mike-Inspiron-1100:/$ xandr   :oops:
No command 'xandr' found, did you mean:
 Command 'xrandr' from package 'x11-xserver-utils' (main)
xandr: command not found
mike@mike-Inspiron-1100:/$ xrandr
Screen 0: minimum 320 x 200, current 640 x 480, maximum 32767 x 32767
LVDS1 connected 640x480+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   640x480        60.0*+   59.9  
VGA1 unknown connection (normal left inverted right x axis y axis)
   1360x768       59.8  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3 
   640x480        59.9  
VIRTUAL1 disconnected (normal left inverted right x axis y axis)

mike@mike-Inspiron-1100:/$ xrandr --output LVDS1 --mode 1024x768
xrandr: cannot find mode 1024x768

mike@mike-Inspiron-1100:/$ cvt 1024 768 60
# 1024x768 59.92 Hz (CVT 0.79M3) hsync: 47.82 kHz; pclk: 63.50 MHz
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync

mike@mike-Inspiron-1100:/$ xrandr --newmode "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync

X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  27
  Current serial number in output stream:  27

mike@mike-Inspiron-1100:/$ cvt 1360x768 60
# 1360x60 50.43 Hz (CVT) hsync: 3.83 kHz; pclk: 6.50 MHz
Modeline "1360x60_60.00"    6.50  1360 1400 1528 1696  60 63 73 76 -hsync +vsync

mike@mike-Inspiron-1100:/$ xrandr --newmode  "1360x60_60.00"    6.50  1360 1400 1528 1696  60 63 73 76 -hsync +vsync

X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  27
  Current serial number in output stream:  27

:icon_frown::x  So, I'm not sure what to do next....(I have lubuntu among the distros I haven't yet tried, but the shrunken window is an unfriendly precedent)

---

