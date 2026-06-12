---
title: "No DisplayPort"
date: 2016-01-22
forum: Hardware
---

### Post by holysword on 2016-01-22
Hello 

After googling a while, I realized that many people had this problem before, but their solution do not seem fitting in my case.
Basically I have a laptop with one DisplayPort (as well as a MiniDisplayPort) to connect external screens. Sadly, it does nothing. The only port that works is the VGA port.

Most people solved this problem yeeeeeeeeeeeeeeeeeaaaaaaaaars ago by using nvidia-settings or whatever, but I don't have an nvidia card.
This is the output of my lshw:
[http://pastebin.com/jL2fTCw0](http://pastebin.com/jL2fTCw0)

The videocard reported in lspci is "Intel Corporation Broadwell-U Integrated Graphics"
Isn't DP yet supported in 14.04's kernel? Or is there something else?
Also, I am using KUbuntu.

---

### Post by matt_symes on 2016-01-25
Hi

> **holysword said:**
> Hello 

After googling a while, I realized that many people had this problem before, but their solution do not seem fitting in my case.
Basically I have a laptop with one DisplayPort (as well as a MiniDisplayPort) to connect external screens. Sadly, it does nothing. The only port that works is the VGA port.

Most people solved this problem yeeeeeeeeeeeeeeeeeaaaaaaaaars ago by using nvidia-settings or whatever, but I don't have an nvidia card.
This is the output of my lshw:
[http://pastebin.com/jL2fTCw0](http://pastebin.com/jL2fTCw0)

The videocard reported in lspci is "Intel Corporation Broadwell-U Integrated Graphics"
Isn't DP yet supported in 14.04's kernel? Or is there something else?
Also, I am using KUbuntu.

What kernel version are you using ?

```
uname -a
```

What does it say in X's log ? Any clues in there ?

```
cat /var/log/Xorg.0.log
```

Kind regards

---

### Post by holysword on 2016-01-25
> **matt_symes said:**
> Hi



What kernel version are you using ?

```
uname -a
```

What does it say in X's log ? Any clues in there ?

```
cat /var/log/Xorg.0.log
```

Kind regards

Here you go:
[http://pastebin.com/7JScBiJu](http://pastebin.com/7JScBiJu)

```

&#9698; hephestus &#9699; ~ $  uname -a
Linux hephestus 3.19.0-47-generic #53~14.04.1-Ubuntu SMP Mon Jan 18 16:09:14 UTC 2016 x86_64 x86_64 x86_64 GNU/
Linux
&#9698; hephestus &#9699; ~ $  cat /var/log/Xorg.0.log
[     5.476]
X.Org X Server 1.17.1
Release Date: 2015-02-10
[     5.476] X Protocol Version 11, Revision 0
[     5.476] Build Operating System: Linux 3.19.0-28-generic x86_64 Ubuntu
[     5.476] Current Operating System: Linux hephestus 3.19.0-47-generic #53~14.04.1-Ubuntu SMP Mon Jan 18 16:0
9:14 UTC 2016 x86_64
[     5.476] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.19.0-47-generic.efi.signed root=UUID=af30835a-2846
-4e0f-bfb4-6771f5fb600b ro quiet splash vt.handoff=7
[     5.476] Build Date: 11 September 2015  10:33:14AM
[     5.476] xorg-server 2:1.17.1-0ubuntu3.1~trusty1 (For technical support please see http://www.ubuntu.com/su
pport)
[     5.476] Current version of pixman: 0.30.2
[     5.476] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[     5.476] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     5.476] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Jan 25 17:18:07 2016
[     5.476] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     5.476] (==) No Layout section.  Using the first Screen section.
[     5.476] (==) No screen section available. Using defaults.
[     5.476] (**) |-->Screen "Default Screen Section" (0)
[     5.476] (**) |   |-->Monitor "<default monitor>"
[     5.476] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[     5.476] (==) Automatically adding devices
[     5.476] (==) Automatically enabling devices
[     5.477] (==) Automatically adding GPU devices
[     5.477] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     5.477] 	Entry deleted from font path.
[     5.477] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     5.477] 	Entry deleted from font path.
[     5.477] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     5.477] 	Entry deleted from font path.
[     5.477] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     5.477] 	Entry deleted from font path.
[     5.477] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     5.477] 	Entry deleted from font path.
[     5.477] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[     5.477] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/
usr/lib/xorg/modules"
[     5.477] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[     5.477] (II) Loader magic: 0x5608a8bb3c60
[     5.477] (II) Module ABI versions:
[     5.477] 	X.Org ANSI C Emulation: 0.4
[     5.477] 	X.Org Video Driver: 19.0
[     5.477] 	X.Org XInput driver : 21.0
[     5.477] 	X.Org Server Extension : 9.0
[     5.477] (II) xfree86: Adding drm device (/dev/dri/card0)
[     5.479] (--) PCI:*(0:0:2:0) 8086:1616:17aa:2223 rev 9, Mem @ 0xf0000000/16777216, 0xe0000000/268435456, I/
O @ 0x00003000/64
[     5.479] (II) LoadModule: "glx"
[     5.480] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[     5.486] (II) Module glx: vendor="X.Org Foundation"
[     5.486] 	compiled for 1.17.1, module version = 1.0.0
[     5.486] 	ABI class: X.Org Server Extension, version 9.0
[     5.486] (==) AIGLX enabled
[     5.486] (==) Matched intel as autoconfigured driver 0
[     5.486] (==) Matched intel as autoconfigured driver 1
[     5.486] (==) Matched modesetting as autoconfigured driver 2
[     5.486] (==) Matched fbdev as autoconfigured driver 3
[     5.486] (==) Matched vesa as autoconfigured driver 4
[     5.486] (==) Assigned the driver to the xf86ConfigLayout
[     5.486] (II) LoadModule: "intel"
[     5.486] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[     5.487] (II) Module intel: vendor="X.Org Foundation"
[     5.487] 	compiled for 1.17.1, module version = 2.99.917
[     5.487] 	Module class: X.Org Video Driver
[     5.487] 	ABI class: X.Org Video Driver, version 19.0
[     5.487] (II) LoadModule: "modesetting"
[     5.487] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[     5.488] (II) Module modesetting: vendor="X.Org Foundation"
[     5.488] 	compiled for 1.17.1, module version = 1.17.1
[     5.488] 	Module class: X.Org Video Driver
[     5.488] 	ABI class: X.Org Video Driver, version 19.0
[     5.488] (II) LoadModule: "fbdev"
[     5.488] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     5.488] (II) Module fbdev: vendor="X.Org Foundation"
[     5.488] 	compiled for 1.17.1, module version = 0.4.4
[     5.488] 	Module class: X.Org Video Driver
[     5.488] 	ABI class: X.Org Video Driver, version 19.0
[     5.488] (II) LoadModule: "vesa"
[     5.488] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     5.488] (II) Module vesa: vendor="X.Org Foundation"
[     5.488] 	compiled for 1.17.1, module version = 2.3.3
[     5.488] 	Module class: X.Org Video Driver
[     5.488] 	ABI class: X.Org Video Driver, version 19.0
[     5.488] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
	i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
	915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
	Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
	GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[     5.488] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[     5.488] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[     5.488] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[     5.488] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[     5.488] (II) FBDEV: driver for framebuffer: fbdev
[     5.488] (II) VESA: driver for VESA chipsets: vesa
[     5.488] (++) using VT number 7

[     5.488] (II) intel(0): Using Kernel Mode Setting driver: i915_bpo, version 1.6.0 20150522
[     5.488] (II) intel(0): SNA compiled: xserver-xorg-video-intel-lts-vivid 2:2.99.917-1~exp1ubuntu2.2~trusty1
 (Timo Aaltonen <tjaalton@debian.org>)
[     5.488] (II) intel(0): SNA compiled for use with valgrind
[     5.489] (WW) Falling back to old probe method for modesetting
[     5.489] (WW) Falling back to old probe method for fbdev
[     5.489] (II) Loading sub module "fbdevhw"
[     5.489] (II) LoadModule: "fbdevhw"
[     5.489] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[     5.489] (II) Module fbdevhw: vendor="X.Org Foundation"
[     5.489] 	compiled for 1.17.1, module version = 0.0.2
[     5.489] 	ABI class: X.Org Video Driver, version 19.0
[     5.489] (WW) Falling back to old probe method for vesa
[     5.489] (--) intel(0): Integrated Graphics Chipset: Intel(R) HD graphics 5500
[     5.489] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2, avx, avx2
[     5.489] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[     5.489] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[     5.489] (==) intel(0): RGB weight 888
[     5.489] (==) intel(0): Default visual is TrueColor
[     5.489] (II) intel(0): Output eDP1 has no monitor section
[     5.489] (--) intel(0): Found backlight control interface intel_backlight (type 'raw') for output eDP1
[     5.489] (II) intel(0): Enabled output eDP1
[     5.489] (II) intel(0): Output DP1 has no monitor section
[     5.489] (II) intel(0): Enabled output DP1
[     5.489] (II) intel(0): Output HDMI1 has no monitor section
[     5.489] (II) intel(0): Enabled output HDMI1
[     5.489] (II) intel(0): Output DP2 has no monitor section
[     5.489] (II) intel(0): Enabled output DP2
[     5.490] (II) intel(0): Output HDMI2 has no monitor section
[     5.490] (II) intel(0): Enabled output HDMI2
[     5.490] (--) intel(0): Using a maximum size of 256x256 for hardware cursors
[     5.490] (II) intel(0): Output VIRTUAL1 has no monitor section
[     5.490] (II) intel(0): Enabled output VIRTUAL1
[     5.490] (--) intel(0): Output eDP1 using initial mode 1920x1080 on pipe 0
[     5.490] (==) intel(0): TearFree disabled
[     5.490] (==) intel(0): DPI set to (96, 96)
[     5.490] (II) Loading sub module "dri2"
[     5.490] (II) LoadModule: "dri2"
[     5.490] (II) Module "dri2" already built-in
[     5.490] (II) Loading sub module "present"
[     5.490] (II) LoadModule: "present"
[     5.490] (II) Module "present" already built-in
[     5.490] (II) UnloadModule: "modesetting"
[     5.490] (II) Unloading modesetting
[     5.490] (II) UnloadModule: "fbdev"
[     5.490] (II) Unloading fbdev
[     5.490] (II) UnloadSubModule: "fbdevhw"
[     5.490] (II) Unloading fbdevhw
[     5.490] (II) UnloadModule: "vesa"
[     5.490] (II) Unloading vesa
[     5.490] (==) Depth 24 pixmap format is 32 bpp
[     5.490] (II) intel(0): SNA initialized with Broadwell backend
[     5.490] (==) intel(0): Backing store enabled
[     5.490] (==) intel(0): Silken mouse enabled
[     5.490] (II) intel(0): HW Cursor enabled
[     5.490] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[     5.490] (==) intel(0): DPMS enabled
[     5.490] (==) intel(0): display hotplug detection enabled
[     5.491] (II) intel(0): [DRI2] Setup complete
[     5.491] (II) intel(0): [DRI2]   DRI driver: i965
[     5.491] (II) intel(0): [DRI2]   VDPAU driver: i965
[     5.491] (II) intel(0): direct rendering: DRI2 enabled
[     5.491] (II) intel(0): hardware support for Present enabled
[     5.491] (--) RandR disabled
[     5.530] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[     5.530] (II) AIGLX: enabled GLX_ARB_create_context
[     5.530] (II) AIGLX: enabled GLX_ARB_create_context_profile
[     5.530] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[     5.530] (II) AIGLX: enabled GLX_INTEL_swap_event
[     5.530] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[     5.530] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[     5.530] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[     5.530] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[     5.530] (II) AIGLX: enabled GLX_ARB_create_context_robustness
[     5.530] (II) AIGLX: Loaded and initialized i965
[     5.530] (II) GLX: Initialized DRI2 GL provider for screen 0
[     5.533] (II) intel(0): switch to mode 1920x1080@60.0 on eDP1 using pipe 0, position (0, 0), rotation norma
l, reflection none
[     5.535] (II) intel(0): Setting screen physical size to 508 x 285
[     5.543] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[     5.545] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[     5.545] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     5.545] (II) LoadModule: "evdev"
[     5.545] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     5.546] (II) Module evdev: vendor="X.Org Foundation"
[     5.546] 	compiled for 1.17.1, module version = 2.9.0
[     5.546] 	Module class: X.Org XInput Driver
[     5.546] 	ABI class: X.Org XInput driver, version 21.0
[     5.546] (II) Using input driver 'evdev' for 'Power Button'
[     5.546] (**) Power Button: always reports core events
[     5.546] (**) evdev: Power Button: Device: "/dev/input/event2"
[     5.546] (--) evdev: Power Button: Vendor 0 Product 0x1
[     5.546] (--) evdev: Power Button: Found keys
[     5.546] (II) evdev: Power Button: Configuring as keyboard
[     5.546] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[     5.546] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[     5.546] (**) Option "xkb_rules" "evdev"
[     5.546] (**) Option "xkb_model" "pc105"
[     5.546] (**) Option "xkb_layout" "us"
[     5.547] (II) config/udev: Adding input device Video Bus (/dev/input/event8)
[     5.547] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[     5.547] (II) Using input driver 'evdev' for 'Video Bus'
[     5.547] (**) Video Bus: always reports core events
[     5.547] (**) evdev: Video Bus: Device: "/dev/input/event8"
[     5.547] (--) evdev: Video Bus: Vendor 0 Product 0x6
[     5.547] (--) evdev: Video Bus: Found keys
[     5.547] (II) evdev: Video Bus: Configuring as keyboard
[     5.547] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/
input10/event8"
[     5.547] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[     5.547] (**) Option "xkb_rules" "evdev"
[     5.547] (**) Option "xkb_model" "pc105"
[     5.547] (**) Option "xkb_layout" "us"
[     5.547] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[     5.547] (II) No input driver specified, ignoring this device.
[     5.547] (II) This device may have been added with another device file.
[     5.548] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[     5.548] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[     5.548] (II) Using input driver 'evdev' for 'Sleep Button'
[     5.548] (**) Sleep Button: always reports core events
[     5.548] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[     5.548] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[     5.548] (--) evdev: Sleep Button: Found keys
[     5.548] (II) evdev: Sleep Button: Configuring as keyboard
[     5.548] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1/event
1"
[     5.548] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 8)
[     5.548] (**) Option "xkb_rules" "evdev"
[     5.548] (**) Option "xkb_model" "pc105"
[     5.548] (**) Option "xkb_layout" "us"
[     5.548] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=3 (/dev/input/event9)
[     5.548] (II) No input driver specified, ignoring this device.
[     5.548] (II) This device may have been added with another device file.
[     5.549] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=7 (/dev/input/event10)
[     5.549] (II) No input driver specified, ignoring this device.
[     5.549] (II) This device may have been added with another device file.
[     5.549] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=8 (/dev/input/event11)
[     5.549] (II) No input driver specified, ignoring this device.
[     5.549] (II) This device may have been added with another device file.
[     5.549] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event5)
[     5.549] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[     5.549] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[     5.549] (**) Logitech USB Receiver: always reports core events
[     5.549] (**) evdev: Logitech USB Receiver: Device: "/dev/input/event5"
[     5.604] (--) evdev: Logitech USB Receiver: Vendor 0x46d Product 0xc531
[     5.604] (--) evdev: Logitech USB Receiver: Found 20 mouse buttons
[     5.604] (--) evdev: Logitech USB Receiver: Found scroll wheel(s)
[     5.604] (--) evdev: Logitech USB Receiver: Found relative axes
[     5.604] (--) evdev: Logitech USB Receiver: Found x and y relative axes
[     5.604] (II) evdev: Logitech USB Receiver: Configuring as mouse
[     5.604] (II) evdev: Logitech USB Receiver: Adding scrollwheel support
[     5.604] (**) evdev: Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[     5.604] (**) evdev: Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTim
eout: 200
[     5.604] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3.4/1-3.4.2/1-3.4.
2:1.0/0003:046D:C531.0001/input/input7/event5"
[     5.604] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: MOUSE, id 9)
[     5.604] (II) evdev: Logitech USB Receiver: initialized for relative axes.
[     5.604] (**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
[     5.604] (**) Logitech USB Receiver: (accel) acceleration profile 0
[     5.604] (**) Logitech USB Receiver: (accel) acceleration factor: 2.000
[     5.604] (**) Logitech USB Receiver: (accel) acceleration threshold: 4
[     5.604] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse1)
[     5.604] (II) No input driver specified, ignoring this device.
[     5.604] (II) This device may have been added with another device file.
[     5.605] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event6)
[     5.605] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[     5.605] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[     5.605] (**) Logitech USB Receiver: always reports core events
[     5.605] (**) evdev: Logitech USB Receiver: Device: "/dev/input/event6"
[     5.605] (--) evdev: Logitech USB Receiver: Vendor 0x46d Product 0xc531
[     5.605] (--) evdev: Logitech USB Receiver: Found 1 mouse buttons
[     5.605] (--) evdev: Logitech USB Receiver: Found scroll wheel(s)
[     5.605] (--) evdev: Logitech USB Receiver: Found relative axes
[     5.605] (II) evdev: Logitech USB Receiver: Forcing relative x/y axes to exist.
[     5.605] (--) evdev: Logitech USB Receiver: Found absolute axes
[     5.605] (II) evdev: Logitech USB Receiver: Forcing absolute x/y axes to exist.
[     5.605] (--) evdev: Logitech USB Receiver: Found keys
[     5.605] (II) evdev: Logitech USB Receiver: Configuring as mouse
[     5.605] (II) evdev: Logitech USB Receiver: Configuring as keyboard
[     5.605] (II) evdev: Logitech USB Receiver: Adding scrollwheel support
[     5.605] (**) evdev: Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[     5.605] (**) evdev: Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTim
eout: 200
[     5.605] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3.4/1-3.4.2/1-3.4.
2:1.1/0003:046D:C531.0002/input/input8/event6"
[     5.605] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD, id 10)
[     5.605] (**) Option "xkb_rules" "evdev"
[     5.605] (**) Option "xkb_model" "pc105"
[     5.605] (**) Option "xkb_layout" "us"
[     5.605] (II) evdev: Logitech USB Receiver: initialized for relative axes.
[     5.605] (WW) evdev: Logitech USB Receiver: ignoring absolute axes.
[     5.605] (**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
[     5.605] (**) Logitech USB Receiver: (accel) acceleration profile 0
[     5.605] (**) Logitech USB Receiver: (accel) acceleration factor: 2.000
[     5.605] (**) Logitech USB Receiver: (accel) acceleration threshold: 4
[     5.605] (II) config/udev: Adding input device Dell Dell USB Entry Keyboard (/dev/input/event7)
[     5.605] (**) Dell Dell USB Entry Keyboard: Applying InputClass "evdev keyboard catchall"
[     5.605] (II) Using input driver 'evdev' for 'Dell Dell USB Entry Keyboard'
[     5.605] (**) Dell Dell USB Entry Keyboard: always reports core events
[     5.605] (**) evdev: Dell Dell USB Entry Keyboard: Device: "/dev/input/event7"
[     5.606] (--) evdev: Dell Dell USB Entry Keyboard: Vendor 0x413c Product 0x2107
[     5.606] (--) evdev: Dell Dell USB Entry Keyboard: Found keys
[     5.606] (II) evdev: Dell Dell USB Entry Keyboard: Configuring as keyboard
[     5.606] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3.4/1-3.4.3/1-3.4.
3:1.0/0003:413C:2107.0003/input/input9/event7"
[     5.606] (II) XINPUT: Adding extended input device "Dell Dell USB Entry Keyboard" (type: KEYBOARD, id 11)
[     5.606] (**) Option "xkb_rules" "evdev"
[     5.606] (**) Option "xkb_model" "pc105"
[     5.606] (**) Option "xkb_layout" "us"
[     5.606] (II) config/udev: Adding input device Integrated Camera (/dev/input/event17)
[     5.606] (**) Integrated Camera: Applying InputClass "evdev keyboard catchall"
[     5.606] (II) Using input driver 'evdev' for 'Integrated Camera'
[     5.606] (**) Integrated Camera: always reports core events
[     5.606] (**) evdev: Integrated Camera: Device: "/dev/input/event17"
[     5.606] (--) evdev: Integrated Camera: Vendor 0x4ca Product 0x703c
[     5.606] (--) evdev: Integrated Camera: Found keys
[     5.606] (II) evdev: Integrated Camera: Configuring as keyboard
[     5.606] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-8/1-8:1.0/input/input1
9/event17"
[     5.606] (II) XINPUT: Adding extended input device "Integrated Camera" (type: KEYBOARD, id 12)
[     5.606] (**) Option "xkb_rules" "evdev"
[     5.606] (**) Option "xkb_model" "pc105"
[     5.606] (**) Option "xkb_layout" "us"
[     5.607] (II) config/udev: Adding input device HDA Intel PCH Dock Mic (/dev/input/event13)
[     5.607] (II) No input driver specified, ignoring this device.
[     5.607] (II) This device may have been added with another device file.
[     5.607] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event14)
[     5.607] (II) No input driver specified, ignoring this device.
[     5.607] (II) This device may have been added with another device file.
[     5.607] (II) config/udev: Adding input device HDA Intel PCH Dock Headphone (/dev/input/event15)
[     5.607] (II) No input driver specified, ignoring this device.
[     5.607] (II) This device may have been added with another device file.
[     5.607] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event16)
[     5.607] (II) No input driver specified, ignoring this device.
[     5.607] (II) This device may have been added with another device file.
[     5.607] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[     5.607] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[     5.607] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[     5.607] (**) AT Translated Set 2 keyboard: always reports core events
[     5.607] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[     5.607] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[     5.607] (--) evdev: AT Translated Set 2 keyboard: Found keys
[     5.607] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[     5.607] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[     5.607] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 13)
[     5.607] (**) Option "xkb_rules" "evdev"
[     5.607] (**) Option "xkb_model" "pc105"
[     5.607] (**) Option "xkb_layout" "us"
[     5.608] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event4)
[     5.608] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[     5.608] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[     5.608] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[     5.608] (II) LoadModule: "synaptics"
[     5.608] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[     5.608] (II) Module synaptics: vendor="X.Org Foundation"
[     5.608] 	compiled for 1.17.1, module version = 1.8.99
[     5.608] 	Module class: X.Org XInput Driver
[     5.608] 	ABI class: X.Org XInput driver, version 21.0
[     5.608] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[     5.608] (**) SynPS/2 Synaptics TouchPad: always reports core events
[     5.608] (**) Option "Device" "/dev/input/event4"
[     5.632] (II) synaptics: SynPS/2 Synaptics TouchPad: found clickpad property
[     5.632] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1266 - 5676 (res 45)
[     5.632] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1096 - 4758 (res 68)
[     5.632] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[     5.632] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[     5.632] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left double triple
[     5.632] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[     5.632] (**) Option "SoftButtonAreas" "50% 0 82% 0 0 0 0 0"
[     5.632] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[     5.632] (**) SynPS/2 Synaptics TouchPad: always reports core events
[     5.664] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input5/event4"
[     5.664] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 14)
[     5.664] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[     5.664] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[     5.664] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.035
[     5.664] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[     5.664] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[     5.664] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[     5.664] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[     5.664] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[     5.664] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[     5.664] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[     5.665] (II) config/udev: Adding input device ThinkPad Extra Buttons (/dev/input/event12)
[     5.665] (**) ThinkPad Extra Buttons: Applying InputClass "evdev keyboard catchall"
[     5.665] (II) Using input driver 'evdev' for 'ThinkPad Extra Buttons'
[     5.665] (**) ThinkPad Extra Buttons: always reports core events
[     5.665] (**) evdev: ThinkPad Extra Buttons: Device: "/dev/input/event12"
[     5.665] (--) evdev: ThinkPad Extra Buttons: Vendor 0x17aa Product 0x5054
[     5.665] (--) evdev: ThinkPad Extra Buttons: Found keys
[     5.665] (II) evdev: ThinkPad Extra Buttons: Configuring as keyboard
[     5.665] (**) Option "config_info" "udev:/sys/devices/platform/thinkpad_acpi/input/input11/event12"
[     5.665] (II) XINPUT: Adding extended input device "ThinkPad Extra Buttons" (type: KEYBOARD, id 15)
[     5.665] (**) Option "xkb_rules" "evdev"
[     5.665] (**) Option "xkb_model" "pc105"
[     5.665] (**) Option "xkb_layout" "us"
[     6.096] (II) config/udev: Adding input device TPPS/2 IBM TrackPoint (/dev/input/mouse2)
[     6.096] (II) No input driver specified, ignoring this device.
[     6.096] (II) This device may have been added with another device file.
[     6.097] (II) config/udev: Adding input device TPPS/2 IBM TrackPoint (/dev/input/event18)
[     6.097] (**) TPPS/2 IBM TrackPoint: Applying InputClass "evdev pointer catchall"
[     6.097] (**) TPPS/2 IBM TrackPoint: Applying InputClass "trackpoint catchall"
[     6.097] (II) Using input driver 'evdev' for 'TPPS/2 IBM TrackPoint'
[     6.097] (**) TPPS/2 IBM TrackPoint: always reports core events
[     6.097] (**) evdev: TPPS/2 IBM TrackPoint: Device: "/dev/input/event18"
[     6.097] (--) evdev: TPPS/2 IBM TrackPoint: Vendor 0x2 Product 0xa
[     6.097] (--) evdev: TPPS/2 IBM TrackPoint: Found 3 mouse buttons
[     6.097] (--) evdev: TPPS/2 IBM TrackPoint: Found relative axes
[     6.097] (--) evdev: TPPS/2 IBM TrackPoint: Found x and y relative axes
[     6.097] (II) evdev: TPPS/2 IBM TrackPoint: Configuring as mouse
[     6.097] (**) Option "Emulate3Buttons" "true"
[     6.097] (**) Option "EmulateWheel" "true"
[     6.097] (**) Option "EmulateWheelButton" "2"
[     6.097] (**) Option "YAxisMapping" "4 5"
[     6.097] (**) evdev: TPPS/2 IBM TrackPoint: YAxisMapping: buttons 4 and 5
[     6.097] (**) Option "XAxisMapping" "6 7"
[     6.097] (**) evdev: TPPS/2 IBM TrackPoint: XAxisMapping: buttons 6 and 7
[     6.097] (**) evdev: TPPS/2 IBM TrackPoint: EmulateWheelButton: 2, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     6.097] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/serio2/input/input6/event18"
[     6.097] (II) XINPUT: Adding extended input device "TPPS/2 IBM TrackPoint" (type: MOUSE, id 16)
[     6.097] (II) evdev: TPPS/2 IBM TrackPoint: initialized for relative axes.
[     6.097] (**) TPPS/2 IBM TrackPoint: (accel) keeping acceleration scheme 1
[     6.097] (**) TPPS/2 IBM TrackPoint: (accel) acceleration profile 0
[     6.097] (**) TPPS/2 IBM TrackPoint: (accel) acceleration factor: 2.000
[     6.097] (**) TPPS/2 IBM TrackPoint: (accel) acceleration threshold: 4
[    15.843] (II) intel(0): EDID vendor "CMN", prod id 5571
[    15.843] (II) intel(0): Printing DDC gathered Modelines:
[    15.843] (II) intel(0): Modeline "1920x1080"x0.0  136.62  1920 1964 1992 2070  1080 1082 1086 1100 -hsync -vsync (66.0 kHz eP)
[    17.049] (II) XKB: reuse xkmfile /var/lib/xkb/server-D378AD8F86E560F712A83EE36E4E5E92C595B9BD.xkm
[    55.344] (II) XKB: reuse xkmfile /var/lib/xkb/server-10A08A0AA82CEFC8E1EF77476F2BD09066F9BB24.xkm
&#9698; hephestus &#9699; ~ $
```

It seems the display port is there alright, but is being ignored. The screen is properly connected and works with the same cables on another computer. Also, bonus:
```
&#9698; hephestus &#9699; ~ $  xrandr
Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 32767 x 32767
eDP1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 344mm x 193mm panning 1920x1080+0+0
   1920x1080      60.0*+   59.9
   1680x1050      60.0     59.9
   1600x1024      60.2
   1400x1050      60.0
   1280x1024      60.0
   1440x900       59.9
   1280x960       60.0
   1360x768       59.8     60.0
   1152x864       60.0
   1024x768       60.0
   800x600        60.3     56.2
   640x480        59.9
DP1 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
HDMI2 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)

```
The only thing I haven't tested was the HDMI port.

---

### Post by matt_symes on 2016-01-25
Hi

Just to get one thing absolutely clear: the external monitor was connected to a display port on your laptop and the monitor switched on, when you ran the xrandr command above and it displayed, as part of its output, this:

```
DP1 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)
```

Kind regards

---

### Post by holysword on 2016-01-26
> **matt_symes said:**
> Hi

Just to get one thing absolutely clear: the external monitor was connected to a display port on your laptop and the monitor switched on, when you ran the xrandr command above and it displayed, as part of its output, this:

```
DP1 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)
```

Kind regards
Yes. Incredible isn't it?
Now, to be totally honest I am using a docking station. The ACTUAL laptop only has a miniDisplayPort, and currently I don't have the cable to test it (though I had it borrowed at some point). I am not 100% sure it will work if I plug it directly.

Checking Lenovo website I found this:
[https://support.lenovo.com/us/en/documents/ht081248](https://support.lenovo.com/us/en/documents/ht081248)

So if there is one of such a bugs, there might be more. I will check it later if there is an update the firmware of the docking station.

---

### Post by matt_symes on 2016-01-28
Hi

> **holysword said:**
> Yes. Incredible isn't it?
Now, to be totally honest I am using a docking station. The ACTUAL laptop only has a miniDisplayPort, and currently I don't have the cable to test it (though I had it borrowed at some point). I am not 100% sure it will work if I plug it directly.

Be very suspicious of the docking station; that it is not the source of the problem.

Beg, borrow or steal a miniDisplayPort cable to eliminate it.

> Checking Lenovo website I found this:
[https://support.lenovo.com/us/en/documents/ht081248](https://support.lenovo.com/us/en/documents/ht081248)

So if there is one of such a bugs, there might be more. I will check it later if there is an update the firmware of the docking station.

Yep :)

Kind regards

---

