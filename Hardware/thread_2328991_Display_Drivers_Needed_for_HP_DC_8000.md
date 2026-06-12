---
title: "Display Drivers Needed for HP DC 8000"
date: 2016-06-26
forum: Hardware
---

### Post by Mir_Ahmed on 2016-06-26
i have installed Ubuntu 15.04 on my machine, but vga display not working correctly please anyone can help me also i have checked HP Drivers website but linux version are not availbe there. thanks

---

### Post by Bashing-om on 2016-06-26
Mir_Ahmed; Hello; Welcome to the forum.

The bad is that release 15.04 is End_Of_Life and has no support. The software repository no longer exists.
Install a current release ( 14.04 - 16.04 )
And in this new install.. IF there is this problem we will then address it .
Obtaining a driver from OEM in 'buntu is the means of last resort, I am sure we have better alternatives if that need arises.

[INDENT][INDENT]help is what we do
[/INDENT][/INDENT]

---

### Post by Mir_Ahmed on 2016-06-26
OKey I am upgrading from 15.04 to 15.10

---

### Post by Bashing-om on 2016-06-26
Mir_Ahmed; K

However, be aware release 15.10 is also a short term release and will soon be End_Of_Life too .

[INDENT][INDENT]it is what it is
[/INDENT][/INDENT]

---

### Post by Mir_Ahmed on 2016-06-26
oh, but i am not able to Directly upgrade from 15.04 to 16.04

Than i will upgrade to latest version once my problems solved.

---

### Post by RobGoss on 2016-06-26
> **Mir_Ahmed said:**
> OKey I am upgrading from 15.04 to 15.10

I recommend installing **16.04** and save your self some time having to ether upgrade later. Ubuntu** 16.04** will have long Term Support until  April 2021, here's a list of supported distributions that you might want to hold on to [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by Mir_Ahmed on 2016-06-26
I have Upgraded to 15.10 but know again upgrading to 16.04 I will contact you, but also same problem for VGA Display still is 1024 by 728 but originally my monitor and system supports 1366 by 768

---

### Post by Bashing-om on 2016-06-26
Mir_Ahmedl Right;

We will look at the hardware and the logs .. when you have completed to release upgrade.
See then id we can find the fault .
-----------------

edit: I am done for this session. I will pick this up tomorrow.


[INDENT][INDENT]we can do that
[/INDENT][/INDENT]

---

### Post by Mir_Ahmed on 2016-06-26
Upqrade COmpleted Still same problem

---

### Post by Bashing-om on 2016-06-27
Mir_Ahmed; OK;

So now let us look and see where the fault lies:
1st is to know the hardware:
Post back - between code tags - the terminal outputs of:
```

lspci -k | grep -EA2 'VGA|3D'

```

Then we want to know what is taking place in the X ( GUI) layer:
```

cat /var/log/Xorg.0.log

```

And what is the status of the driver install:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*
cat /var/log/gpu-manager.log

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

We identify what is, and what should be .. and make it right.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by Mir_Ahmed on 2016-06-29
```
lspci -k | grep -EA2 'VGA|3D'
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
    Subsystem: Hewlett-Packard Company 4 Series Chipset Integrated Graphics Controller
    Kernel driver in use: i915
```

```
cat /var/log/Xorg.0.log
[    26.581] 
X.Org X Server 1.18.3
Release Date: 2016-04-04
[    26.581] X Protocol Version 11, Revision 0
[    26.581] Build Operating System: Linux 3.13.0-86-generic i686 Ubuntu
[    26.581] Current Operating System: Linux bwd-HP-Compaq-8000-Elite-CMT-PC 4.4.0-24-generic #43-Ubuntu SMP Wed Jun 8 19:25:16 UTC 2016 i686
[    26.581] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-24-generic root=UUID=94c420ba-443a-4f78-97d0-d54defad4a9a ro quiet splash vt.handoff=7
[    26.581] Build Date: 18 May 2016  01:07:07AM
[    26.581] xorg-server 2:1.18.3-1ubuntu2.2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    26.581] Current version of pixman: 0.33.6
[    26.581]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    26.581] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    26.581] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Jun 30 07:27:42 2016
[    26.621] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    27.117] (==) No Layout section.  Using the first Screen section.
[    27.117] (==) No screen section available. Using defaults.
[    27.117] (**) |-->Screen "Default Screen Section" (0)
[    27.117] (**) |   |-->Monitor "<default monitor>"
[    27.118] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    27.118] (==) Automatically adding devices
[    27.118] (==) Automatically enabling devices
[    27.118] (==) Automatically adding GPU devices
[    27.118] (==) Max clients allowed: 256, resource mask: 0x1fffff
[    27.118] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    27.118]     Entry deleted from font path.
[    27.118] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    27.118]     Entry deleted from font path.
[    27.118] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    27.118]     Entry deleted from font path.
[    27.118] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    27.118]     Entry deleted from font path.
[    27.118] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    27.118]     Entry deleted from font path.
[    27.118] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    27.118] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    27.118] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    27.118] (II) Loader magic: 0x8034c700
[    27.118] (II) Module ABI versions:
[    27.118]     X.Org ANSI C Emulation: 0.4
[    27.118]     X.Org Video Driver: 20.0
[    27.118]     X.Org XInput driver : 22.1
[    27.118]     X.Org Server Extension : 9.0
[    27.119] (++) using VT number 7

[    27.119] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
[    27.120] (II) xfree86: Adding drm device (/dev/dri/card0)
[    27.121] (--) PCI:*(0:0:2:0) 8086:2e12:103c:3647 rev 3, Mem @ 0xf0000000/4194304, 0xe0000000/268435456, I/O @ 0x00001230/8
[    27.121] (--) PCI: (0:0:2:1) 8086:2e13:103c:3647 rev 3, Mem @ 0xf0400000/1048576
[    27.141] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    27.141] (II) "glx" will be loaded by default.
[    27.141] (II) LoadModule: "glx"
[    27.166] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    27.689] (II) Module glx: vendor="X.Org Foundation"
[    27.689]     compiled for 1.18.3, module version = 1.0.0
[    27.689]     ABI class: X.Org Server Extension, version 9.0
[    27.689] (==) AIGLX enabled
[    27.689] (==) Matched intel as autoconfigured driver 0
[    27.689] (==) Matched intel as autoconfigured driver 1
[    27.689] (==) Matched modesetting as autoconfigured driver 2
[    27.689] (==) Matched fbdev as autoconfigured driver 3
[    27.689] (==) Matched vesa as autoconfigured driver 4
[    27.689] (==) Assigned the driver to the xf86ConfigLayout
[    27.689] (II) LoadModule: "intel"
[    27.689] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    27.816] (II) Module intel: vendor="X.Org Foundation"
[    27.816]     compiled for 1.18.1, module version = 2.99.917
[    27.816]     Module class: X.Org Video Driver
[    27.816]     ABI class: X.Org Video Driver, version 20.0
[    27.816] (II) LoadModule: "modesetting"
[    27.816] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    27.825] (II) Module modesetting: vendor="X.Org Foundation"
[    27.825]     compiled for 1.18.3, module version = 1.18.3
[    27.825]     Module class: X.Org Video Driver
[    27.825]     ABI class: X.Org Video Driver, version 20.0
[    27.825] (II) LoadModule: "fbdev"
[    27.825] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    27.876] (II) Module fbdev: vendor="X.Org Foundation"
[    27.876]     compiled for 1.18.1, module version = 0.4.4
[    27.876]     Module class: X.Org Video Driver
[    27.876]     ABI class: X.Org Video Driver, version 20.0
[    27.876] (II) LoadModule: "vesa"
[    27.876] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    27.989] (II) Module vesa: vendor="X.Org Foundation"
[    27.989]     compiled for 1.18.1, module version = 2.3.4
[    27.989]     Module class: X.Org Video Driver
[    27.989]     ABI class: X.Org Video Driver, version 20.0
[    27.989] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[    27.989] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[    27.989] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[    27.989] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[    27.989] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    27.989] (II) FBDEV: driver for framebuffer: fbdev
[    27.989] (II) VESA: driver for VESA chipsets: vesa
[    28.039] (II) intel(0): Using Kernel Mode Setting driver: i915, version 1.6.0 20151010
[    28.039] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.99.917+git20160325-1ubuntu1 (Timo Aaltonen <tjaalton@debian.org>)
[    28.039] (II) intel(0): SNA compiled for use with valgrind
[    28.091] (WW) Falling back to old probe method for modesetting
[    28.092] (WW) Falling back to old probe method for fbdev
[    28.092] (II) Loading sub module "fbdevhw"
[    28.092] (II) LoadModule: "fbdevhw"
[    28.092] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    28.180] (II) Module fbdevhw: vendor="X.Org Foundation"
[    28.180]     compiled for 1.18.3, module version = 0.0.2
[    28.180]     ABI class: X.Org Video Driver, version 20.0
[    28.180] (WW) Falling back to old probe method for vesa
[    28.230] (--) intel(0): Integrated Graphics Chipset: Intel(R) Q45/Q43
[    28.230] (--) intel(0): CPU: x86, sse2, sse3, ssse3, sse4.1; using a maximum of 2 threads
[    28.230] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    28.230] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    28.230] (==) intel(0): RGB weight 888
[    28.230] (==) intel(0): Default visual is TrueColor
[    28.230] (II) intel(0): Output VGA1 has no monitor section
[    28.230] (II) intel(0): Enabled output VGA1
[    28.230] (II) intel(0): Output HDMI1 has no monitor section
[    28.230] (II) intel(0): Enabled output HDMI1
[    28.230] (II) intel(0): Output DP1 has no monitor section
[    28.230] (II) intel(0): Enabled output DP1
[    28.230] (--) intel(0): Using a maximum size of 256x256 for hardware cursors
[    28.230] (II) intel(0): Output VIRTUAL1 has no monitor section
[    28.230] (II) intel(0): Enabled output VIRTUAL1
[    28.230] (--) intel(0): Output VGA1 using initial mode 1024x768 on pipe 0
[    28.230] (==) intel(0): TearFree disabled
[    28.230] (==) intel(0): DPI set to (96, 96)
[    28.230] (II) Loading sub module "dri2"
[    28.230] (II) LoadModule: "dri2"
[    28.230] (II) Module "dri2" already built-in
[    28.230] (II) Loading sub module "present"
[    28.230] (II) LoadModule: "present"
[    28.230] (II) Module "present" already built-in
[    28.230] (II) UnloadModule: "modesetting"
[    28.230] (II) Unloading modesetting
[    28.230] (II) UnloadModule: "fbdev"
[    28.230] (II) Unloading fbdev
[    28.230] (II) UnloadSubModule: "fbdevhw"
[    28.230] (II) Unloading fbdevhw
[    28.231] (II) UnloadModule: "vesa"
[    28.231] (II) Unloading vesa
[    28.231] (==) Depth 24 pixmap format is 32 bpp
[    28.271] (II) intel(0): SNA initialized with Eaglelake (gen4.5) backend
[    28.271] (==) intel(0): Backing store enabled
[    28.271] (==) intel(0): Silken mouse enabled
[    28.298] (II) intel(0): HW Cursor enabled
[    28.298] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    28.313] (==) intel(0): DPMS enabled
[    28.313] (==) intel(0): Display hotplug detection enabled
[    28.313] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[    28.313] (II) intel(0): [DRI2] Setup complete
[    28.313] (II) intel(0): [DRI2]   DRI driver: i965
[    28.313] (II) intel(0): [DRI2]   VDPAU driver: va_gl
[    28.313] (II) intel(0): direct rendering: DRI2 enabled
[    28.313] (II) intel(0): hardware support for Present enabled
[    28.313] (--) RandR disabled
[    28.321] (II) SELinux: Disabled on system
[    30.380] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    31.082] (II) AIGLX: enabled GLX_ARB_create_context
[    31.082] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    31.082] (II) AIGLX: enabled GLX_EXT_create_context_es{,2}_profile
[    31.082] (II) AIGLX: enabled GLX_INTEL_swap_event
[    31.082] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    31.082] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[    31.082] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[    31.082] (II) AIGLX: enabled GLX_EXT_fbconfig_packed_float
[    31.082] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    31.082] (II) AIGLX: Loaded and initialized i965
[    31.082] (II) GLX: Initialized DRI2 GL provider for screen 0
[    31.086] (II) intel(0): switch to mode 1024x768@60.0 on VGA1 using pipe 0, position (0, 0), rotation normal, reflection none
[    31.086] (II) intel(0): Setting screen physical size to 270 x 203
[    33.732] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    33.732] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    33.732] (II) LoadModule: "evdev"
[    33.732] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    33.809] (II) Module evdev: vendor="X.Org Foundation"
[    33.809]     compiled for 1.18.1, module version = 2.10.1
[    33.809]     Module class: X.Org XInput Driver
[    33.809]     ABI class: X.Org XInput driver, version 22.1
[    33.809] (II) Using input driver 'evdev' for 'Power Button'
[    33.809] (**) Power Button: always reports core events
[    33.809] (**) evdev: Power Button: Device: "/dev/input/event1"
[    33.810] (--) evdev: Power Button: Vendor 0 Product 0x1
[    33.810] (--) evdev: Power Button: Found keys
[    33.810] (II) evdev: Power Button: Configuring as keyboard
[    33.810] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    33.810] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    33.810] (**) Option "xkb_rules" "evdev"
[    33.810] (**) Option "xkb_model" "pc105"
[    33.810] (**) Option "xkb_layout" "us"
[    33.810] (II) config/udev: Adding input device Video Bus (/dev/input/event2)
[    33.810] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    33.810] (II) Using input driver 'evdev' for 'Video Bus'
[    33.810] (**) Video Bus: always reports core events
[    33.810] (**) evdev: Video Bus: Device: "/dev/input/event2"
[    33.810] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    33.810] (--) evdev: Video Bus: Found keys
[    33.810] (II) evdev: Video Bus: Configuring as keyboard
[    33.810] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input5/event2"
[    33.810] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    33.810] (**) Option "xkb_rules" "evdev"
[    33.810] (**) Option "xkb_model" "pc105"
[    33.810] (**) Option "xkb_layout" "us"
[    33.811] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    33.811] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    33.811] (II) Using input driver 'evdev' for 'Power Button'
[    33.811] (**) Power Button: always reports core events
[    33.811] (**) evdev: Power Button: Device: "/dev/input/event0"
[    33.811] (--) evdev: Power Button: Vendor 0 Product 0x1
[    33.811] (--) evdev: Power Button: Found keys
[    33.811] (II) evdev: Power Button: Configuring as keyboard
[    33.811] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    33.811] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    33.811] (**) Option "xkb_rules" "evdev"
[    33.811] (**) Option "xkb_model" "pc105"
[    33.811] (**) Option "xkb_layout" "us"
[    33.812] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/event3)
[    33.812] (**) USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[    33.812] (II) Using input driver 'evdev' for 'USB Optical Mouse'
[    33.812] (**) USB Optical Mouse: always reports core events
[    33.812] (**) evdev: USB Optical Mouse: Device: "/dev/input/event3"
[    33.868] (--) evdev: USB Optical Mouse: Vendor 0x4b3 Product 0x310c
[    33.868] (--) evdev: USB Optical Mouse: Found 3 mouse buttons
[    33.868] (--) evdev: USB Optical Mouse: Found scroll wheel(s)
[    33.868] (--) evdev: USB Optical Mouse: Found relative axes
[    33.868] (--) evdev: USB Optical Mouse: Found x and y relative axes
[    33.868] (II) evdev: USB Optical Mouse: Configuring as mouse
[    33.868] (II) evdev: USB Optical Mouse: Adding scrollwheel support
[    33.868] (**) evdev: USB Optical Mouse: YAxisMapping: buttons 4 and 5
[    33.868] (**) evdev: USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    33.868] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.2/usb5/5-1/5-1:1.0/0003:04B3:310C.0001/input/input6/event3"
[    33.868] (II) XINPUT: Adding extended input device "USB Optical Mouse" (type: MOUSE, id 9)
[    33.868] (II) evdev: USB Optical Mouse: initialized for relative axes.
[    33.868] (**) USB Optical Mouse: (accel) keeping acceleration scheme 1
[    33.868] (**) USB Optical Mouse: (accel) acceleration profile 0
[    33.868] (**) USB Optical Mouse: (accel) acceleration factor: 2.000
[    33.868] (**) USB Optical Mouse: (accel) acceleration threshold: 4
[    33.868] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/mouse0)
[    33.869] (II) No input driver specified, ignoring this device.
[    33.869] (II) This device may have been added with another device file.
[    33.869] (II) config/udev: Adding input device Dell Dell USB Keyboard Hub (/dev/input/event4)
[    33.869] (**) Dell Dell USB Keyboard Hub: Applying InputClass "evdev keyboard catchall"
[    33.869] (II) Using input driver 'evdev' for 'Dell Dell USB Keyboard Hub'
[    33.869] (**) Dell Dell USB Keyboard Hub: always reports core events
[    33.869] (**) evdev: Dell Dell USB Keyboard Hub: Device: "/dev/input/event4"
[    33.869] (--) evdev: Dell Dell USB Keyboard Hub: Vendor 0x413c Product 0x2010
[    33.869] (--) evdev: Dell Dell USB Keyboard Hub: Found keys
[    33.869] (II) evdev: Dell Dell USB Keyboard Hub: Configuring as keyboard
[    33.869] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2.1/5-2.1:1.0/0003:413C:2010.0002/input/input7/event4"
[    33.869] (II) XINPUT: Adding extended input device "Dell Dell USB Keyboard Hub" (type: KEYBOARD, id 10)
[    33.869] (**) Option "xkb_rules" "evdev"
[    33.869] (**) Option "xkb_model" "pc105"
[    33.869] (**) Option "xkb_layout" "us"
[    33.870] (II) config/udev: Adding input device Dell Dell USB Keyboard Hub (/dev/input/event5)
[    33.870] (**) Dell Dell USB Keyboard Hub: Applying InputClass "evdev keyboard catchall"
[    33.870] (II) Using input driver 'evdev' for 'Dell Dell USB Keyboard Hub'
[    33.870] (**) Dell Dell USB Keyboard Hub: always reports core events
[    33.870] (**) evdev: Dell Dell USB Keyboard Hub: Device: "/dev/input/event5"
[    33.870] (--) evdev: Dell Dell USB Keyboard Hub: Vendor 0x413c Product 0x2010
[    33.870] (--) evdev: Dell Dell USB Keyboard Hub: Found absolute axes
[    33.870] (II) evdev: Dell Dell USB Keyboard Hub: Forcing absolute x/y axes to exist.
[    33.870] (--) evdev: Dell Dell USB Keyboard Hub: Found keys
[    33.870] (II) evdev: Dell Dell USB Keyboard Hub: Forcing relative x/y axes to exist.
[    33.870] (II) evdev: Dell Dell USB Keyboard Hub: Configuring as mouse
[    33.870] (II) evdev: Dell Dell USB Keyboard Hub: Configuring as keyboard
[    33.870] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2.1/5-2.1:1.1/0003:413C:2010.0003/input/input8/event5"
[    33.870] (II) XINPUT: Adding extended input device "Dell Dell USB Keyboard Hub" (type: KEYBOARD, id 11)
[    33.870] (**) Option "xkb_rules" "evdev"
[    33.870] (**) Option "xkb_model" "pc105"
[    33.870] (**) Option "xkb_layout" "us"
[    33.870] (II) evdev: Dell Dell USB Keyboard Hub: initialized for absolute axes.
[    33.871] (**) Dell Dell USB Keyboard Hub: (accel) keeping acceleration scheme 1
[    33.871] (**) Dell Dell USB Keyboard Hub: (accel) acceleration profile 0
[    33.871] (**) Dell Dell USB Keyboard Hub: (accel) acceleration factor: 2.000
[    33.871] (**) Dell Dell USB Keyboard Hub: (accel) acceleration threshold: 4
[    33.871] (II) config/udev: Adding input device HDA Intel Mic (/dev/input/event7)
[    33.871] (II) No input driver specified, ignoring this device.
[    33.871] (II) This device may have been added with another device file.
[    33.871] (II) config/udev: Adding input device HDA Intel Line (/dev/input/event8)
[    33.871] (II) No input driver specified, ignoring this device.
[    33.871] (II) This device may have been added with another device file.
[    33.872] (II) config/udev: Adding input device HDA Intel Line Out (/dev/input/event9)
[    33.872] (II) No input driver specified, ignoring this device.
[    33.872] (II) This device may have been added with another device file.
[    33.872] (II) config/udev: Adding input device HDA Intel Front Headphone (/dev/input/event10)
[    33.872] (II) No input driver specified, ignoring this device.
[    33.872] (II) This device may have been added with another device file.
[    33.874] (II) config/udev: Adding input device HP WMI hotkeys (/dev/input/event6)
[    33.874] (**) HP WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    33.874] (II) Using input driver 'evdev' for 'HP WMI hotkeys'
[    33.874] (**) HP WMI hotkeys: always reports core events
[    33.874] (**) evdev: HP WMI hotkeys: Device: "/dev/input/event6"
[    33.874] (--) evdev: HP WMI hotkeys: Vendor 0 Product 0
[    33.874] (--) evdev: HP WMI hotkeys: Found keys
[    33.874] (II) evdev: HP WMI hotkeys: Configuring as keyboard
[    33.874] (**) Option "config_info" "udev:/sys/devices/virtual/input/input9/event6"
[    33.874] (II) XINPUT: Adding extended input device "HP WMI hotkeys" (type: KEYBOARD, id 12)
[    33.874] (**) Option "xkb_rules" "evdev"
[    33.874] (**) Option "xkb_model" "pc105"
[    33.874] (**) Option "xkb_layout" "us"
```

```
cat -n /etc/apt/sources.list
```
```
tail -v -n +1 /etc/apt/sources.list.d/*
```
```
cat /var/log/gpu-manager.log
```

---

### Post by Bashing-om on 2016-06-30
Mir_Ahmed; Morning;

I await the outputs of :
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*
cat /var/log/gpu-manager.log

```

Presently I do not know what to make of the fact that the system, per the log file, sees 2 graphics's sets:
> 
[ 27.121] (--) PCI:*(0:0:2:0) 8086:2e12:103c:3647 rev 3, Mem @ 0xf0000000/4194304, 0xe0000000/268435456, I/O @ 0x00001230/8
[ 27.121] (--) PCI: (0:0:2:1) 8086:2e13:103c:3647 rev 3, Mem @ 0xf0400000/1048576
[ 27.141]

But the output of the 'lspci' only sees the one :
> 
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
Subsystem: Hewlett-Packard Company 4 Series Chipset Integrated Graphics Controller
Kernel driver in use: i915


Nor do I understand the conflict in drivers:
> 
[ 28.039] (II) intel(0): Using Kernel Mode Setting driver: i915, version 1.6.0 20151010
[ 28.313] (II) intel(0): [DRI2] DRI driver: i965
[ 31.082] (II) AIGLX: Loaded and initialized i965


What driver does the system report :
```

sudo lshw -C display

```

[INDENT][INDENT]sometimes I do wonder
[INDENT][INDENT][INDENT]other times, I just do not know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Mir_Ahmed on 2016-07-01
> **Bashing-om said:**
> Mir_Ahmed; Morning;

I await the outputs of :
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*
cat /var/log/gpu-manager.log

```

Presently I do not know what to make of the fact that the system, per the log file, sees 2 graphics's sets:

But the output of the 'lspci' only sees the one :


Nor do I understand the conflict in drivers:


What driver does the system report :
```

sudo lshw -C display

```
sometimes I do wonder other times, I just do not know


```
*-display:0             
       description: VGA compatible controller
       product: 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:32 memory:f0000000-f03fffff memory:e0000000-efffffff ioport:1230(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:f0400000-f04fffff
```

```
~$ cat -n /etc/apt/sources.list
     1    # deb cdrom:[Ubuntu 15.04 _Vivid Vervet_ - Release i386 (20150422)]/ vivid main restricted
     2    
     3    # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
     4    # newer versions of the distribution.
     5    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial main restricted
     6    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial main restricted
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates main restricted
    11    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates main restricted
    12    
    13    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14    ## team. Also, please note that software in universe WILL NOT receive any
    15    ## review or updates from the Ubuntu security team.
    16    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial universe
    17    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial universe
    18    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates universe
    19    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates universe
    20    
    21    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22    ## team, and may not be under a free licence. Please satisfy yourself as to 
    23    ## your rights to use the software. Also, please note that software in 
    24    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    25    ## security team.
    26    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial multiverse
    27    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial multiverse
    28    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates multiverse
    29    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates multiverse
    30    
    31    ## N.B. software from this repository may not have been tested as
    32    ## extensively as that contained in the main release, although it includes
    33    ## newer versions of some applications which may provide useful features.
    34    ## Also, please note that software in backports WILL NOT receive any review
    35    ## or updates from the Ubuntu security team.
    36    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports main restricted universe multiverse
    37    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports main restricted universe multiverse
    38    
    39    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security main restricted
    40    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security main restricted
    41    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security universe
    42    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security universe
    43    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security multiverse
    44    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security multiverse
    45    
    46    ## Uncomment the following two lines to add software from Canonical's
    47    ## 'partner' repository.
    48    ## This software is not part of Ubuntu, but is offered by Canonical and the
    49    ## respective vendors as a service to Ubuntu users.
    50    # deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) vivid partner
    51    # deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) vivid partner
bwd@bwd-HP-Compaq-8000-Elite-CMT-PC:~$ tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/graphics-drivers-ubuntu-ppa-xenial.list <==
deb [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) xenial main
# deb-src [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) xenial main
bwd@bwd-HP-Compaq-8000-Elite-CMT-PC:~$ cat /var/log/gpu-manager.log
log_file: /var/log/gpu-manager.log
last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
can't access /run/u-d-c-nvidia-was-loaded file
can't access /run/u-d-c-fglrx-was-loaded file
Looking for fglrx modules in /lib/modules/4.4.0-28-generic/updates/dkms
Looking for nvidia modules in /lib/modules/4.4.0-28-generic/updates/dkms
Found nvidia module: nvidia_364_drm.ko
Is nvidia loaded? no
Was nvidia unloaded? no
Is nvidia blacklisted? no
Is fglrx loaded? no
Was fglrx unloaded? no
Is fglrx blacklisted? no
Is intel loaded? yes
Is radeon loaded? no
Is radeon blacklisted? no
Is amdgpu loaded? no
Is amdgpu blacklisted? no
Is nouveau loaded? no
Is nouveau blacklisted? yes
Is fglrx kernel module available? no
Is nvidia kernel module available? yes
Vendor/Device Id: 8086:2e12
BusID "PCI:0@0:2:0"
Is boot vga? yes
Vendor/Device Id: 8086:2e13
BusID "PCI:0@0:2:1"
Is boot vga? no
Error: can't access /sys/bus/pci/devices/0000:00:02.1/driver
The device is not bound to any driver. Skipping...
Skipping "/dev/dri/card0", driven by "i915"
Skipping "/dev/dri/card0", driven by "i915"
Skipping "/dev/dri/card0", driven by "i915"
Found "/dev/dri/card0", driven by "i915"
output 0:
    VGA connector
Number of connected outputs for /dev/dri/card0: 1
Does it require offloading? yes
last cards number = 1
Has amd? no
Has intel? yes
Has nvidia? no
How many cards? 1
Has the system changed? No
main_arch_path i386-linux-gnu, other_arch_path x86_64-linux-gnu
Current alternative: /usr/lib/i386-linux-gnu/mesa/ld.so.conf
Current core alternative: (null)
Current egl alternative: /usr/lib/i386-linux-gnu/mesa-egl/ld.so.conf
Is nvidia enabled? no
Is nvidia egl enabled? no
Is fglrx enabled? no
Is mesa enabled? yes
Is mesa egl enabled? yes
Is pxpress enabled? no
Is prime enabled? no
Is prime egl enabled? no
Is nvidia available? yes
Is nvidia egl available? no
Is fglrx available? no
Is fglrx-core available? no
Is mesa available? yes
Is mesa egl available? yes
Is pxpress available? no
Is prime available? yes
Is prime egl available? no
Single card detected
Nothing to do
No change - nothing to do
```

[ATTACH=CONFIG]269878[/ATTACH]

Any one can help most urgent

---

### Post by Bashing-om on 2016-07-01
Mir_Ahmed; Hey !

I see that both chip sets are Intel, why then is a Nvidia driver installed ?
What is the background/reasoning for this ?

Keeping in mind, when all is said and done. might for sure enable the Intel Microcode in " Additional Drivers " .

Upfront; I do not know much about Intel drivers, let's see what we can learn.

[INDENT][INDENT]it is all a process
[/INDENT][/INDENT]

---

### Post by Mir_Ahmed on 2016-07-01
I have installed Nvidia drivers

I am not getting full resuolation of my moniter my monitor supports 1366x768 but know set on 1024x768

I NEED 1366X768 Resolution Display on my monitor

---

### Post by Mir_Ahmed on 2016-07-22
```
~$ lspci -k | grep -EA2 'VGA|3D'
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
    Subsystem: Hewlett-Packard Company 4 Series Chipset Integrated Graphics Controller
    Kernel driver in use: i915
bwd@bwd-HP-Compaq-8000-Elite-CMT-PC:~$ cat /var/log/Xorg.0.log
[    29.633] 
X.Org X Server 1.18.3
Release Date: 2016-04-04
[    29.633] X Protocol Version 11, Revision 0
[    29.633] Build Operating System: Linux 3.13.0-86-generic x86_64 Ubuntu
[    29.633] Current Operating System: Linux bwd-HP-Compaq-8000-Elite-CMT-PC 4.4.0-31-generic #50-Ubuntu SMP Wed Jul 13 00:07:12 UTC 2016 x86_64
[    29.633] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-31-generic root=UUID=a338487a-bd92-4454-83b4-8d7f8146a68f ro quiet splash
[    29.633] Build Date: 18 May 2016  01:07:07AM
[    29.633] xorg-server 2:1.18.3-1ubuntu2.2 (For technical support please see http://www.ubuntu.com/support) 
[    29.633] Current version of pixman: 0.33.6
[    29.633]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    29.633] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    29.633] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Jul 22 22:36:33 2016
[    29.662] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    29.662] (==) No Layout section.  Using the first Screen section.
[    29.662] (==) No screen section available. Using defaults.
[    29.662] (**) |-->Screen "Default Screen Section" (0)
[    29.662] (**) |   |-->Monitor "<default monitor>"
[    29.668] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    29.668] (==) Automatically adding devices
[    29.668] (==) Automatically enabling devices
[    29.668] (==) Automatically adding GPU devices
[    29.668] (==) Max clients allowed: 256, resource mask: 0x1fffff
[    29.668] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    29.668]     Entry deleted from font path.
[    29.668] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    29.668]     Entry deleted from font path.
[    29.668] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    29.668]     Entry deleted from font path.
[    29.668] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    29.668]     Entry deleted from font path.
[    29.668] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    29.668]     Entry deleted from font path.
[    29.668] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    29.668] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    29.668] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    29.669] (II) Loader magic: 0x5595fcae6da0
[    29.669] (II) Module ABI versions:
[    29.669]     X.Org ANSI C Emulation: 0.4
[    29.669]     X.Org Video Driver: 20.0
[    29.669]     X.Org XInput driver : 22.1
[    29.669]     X.Org Server Extension : 9.0
[    29.669] (++) using VT number 7

[    29.669] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
[    29.669] (II) xfree86: Adding drm device (/dev/dri/card0)
[    29.671] (--) PCI:*(0:0:2:0) 8086:2e12:103c:3647 rev 3, Mem @ 0xf0000000/4194304, 0xe0000000/268435456, I/O @ 0x00001230/8
[    29.671] (--) PCI: (0:0:2:1) 8086:2e13:103c:3647 rev 3, Mem @ 0xf0400000/1048576
[    29.671] (II) LoadModule: "glx"
[    29.743] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    30.340] (II) Module glx: vendor="X.Org Foundation"
[    30.340]     compiled for 1.18.3, module version = 1.0.0
[    30.340]     ABI class: X.Org Server Extension, version 9.0
[    30.340] (==) AIGLX enabled
[    30.340] (==) Matched intel as autoconfigured driver 0
[    30.340] (==) Matched intel as autoconfigured driver 1
[    30.340] (==) Matched modesetting as autoconfigured driver 2
[    30.340] (==) Matched fbdev as autoconfigured driver 3
[    30.340] (==) Matched vesa as autoconfigured driver 4
[    30.340] (==) Assigned the driver to the xf86ConfigLayout
[    30.340] (II) LoadModule: "intel"
[    30.340] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    30.430] (II) Module intel: vendor="X.Org Foundation"
[    30.430]     compiled for 1.18.1, module version = 2.99.917
[    30.430]     Module class: X.Org Video Driver
[    30.430]     ABI class: X.Org Video Driver, version 20.0
[    30.430] (II) LoadModule: "modesetting"
[    30.430] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    30.430] (II) Module modesetting: vendor="X.Org Foundation"
[    30.430]     compiled for 1.18.3, module version = 1.18.3
[    30.430]     Module class: X.Org Video Driver
[    30.430]     ABI class: X.Org Video Driver, version 20.0
[    30.430] (II) LoadModule: "fbdev"
[    30.430] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    30.430] (II) Module fbdev: vendor="X.Org Foundation"
[    30.430]     compiled for 1.18.1, module version = 0.4.4
[    30.430]     Module class: X.Org Video Driver
[    30.430]     ABI class: X.Org Video Driver, version 20.0
[    30.430] (II) LoadModule: "vesa"
[    30.430] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    30.430] (II) Module vesa: vendor="X.Org Foundation"
[    30.430]     compiled for 1.18.1, module version = 2.3.4
[    30.430]     Module class: X.Org Video Driver
[    30.430]     ABI class: X.Org Video Driver, version 20.0
[    30.430] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[    30.431] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[    30.431] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[    30.431] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[    30.431] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    30.431] (II) FBDEV: driver for framebuffer: fbdev
[    30.431] (II) VESA: driver for VESA chipsets: vesa
[    30.478] (II) intel(0): Using Kernel Mode Setting driver: i915, version 1.6.0 20151010
[    30.478] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.99.917+git20160325-1ubuntu1 (Timo Aaltonen <tjaalton@debian.org>)
[    30.478] (II) intel(0): SNA compiled for use with valgrind
[    30.514] (WW) Falling back to old probe method for modesetting
[    30.514] (WW) Falling back to old probe method for fbdev
[    30.514] (II) Loading sub module "fbdevhw"
[    30.514] (II) LoadModule: "fbdevhw"
[    30.514] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    30.514] (II) Module fbdevhw: vendor="X.Org Foundation"
[    30.514]     compiled for 1.18.3, module version = 0.0.2
[    30.514]     ABI class: X.Org Video Driver, version 20.0
[    30.514] (WW) Falling back to old probe method for vesa
[    30.531] (--) intel(0): Integrated Graphics Chipset: Intel(R) Q45/Q43
[    30.531] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3, sse4.1; using a maximum of 2 threads
[    30.531] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    30.531] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    30.531] (==) intel(0): RGB weight 888
[    30.531] (==) intel(0): Default visual is TrueColor
[    30.535] (II) intel(0): Output VGA1 has no monitor section
[    30.535] (II) intel(0): Enabled output VGA1
[    30.535] (II) intel(0): Output HDMI1 has no monitor section
[    30.535] (II) intel(0): Enabled output HDMI1
[    30.535] (II) intel(0): Output DP1 has no monitor section
[    30.535] (II) intel(0): Enabled output DP1
[    30.535] (--) intel(0): Using a maximum size of 256x256 for hardware cursors
[    30.535] (II) intel(0): Output VIRTUAL1 has no monitor section
[    30.535] (II) intel(0): Enabled output VIRTUAL1
[    30.535] (--) intel(0): Output VGA1 using initial mode 1024x768 on pipe 0
[    30.535] (==) intel(0): TearFree disabled
[    30.535] (==) intel(0): DPI set to (96, 96)
[    30.535] (II) Loading sub module "dri2"
[    30.535] (II) LoadModule: "dri2"
[    30.535] (II) Module "dri2" already built-in
[    30.535] (II) Loading sub module "present"
[    30.535] (II) LoadModule: "present"
[    30.535] (II) Module "present" already built-in
[    30.535] (II) UnloadModule: "modesetting"
[    30.535] (II) Unloading modesetting
[    30.535] (II) UnloadModule: "fbdev"
[    30.535] (II) Unloading fbdev
[    30.535] (II) UnloadSubModule: "fbdevhw"
[    30.535] (II) Unloading fbdevhw
[    30.535] (II) UnloadModule: "vesa"
[    30.535] (II) Unloading vesa
[    30.535] (==) Depth 24 pixmap format is 32 bpp
[    30.652] (II) intel(0): SNA initialized with Eaglelake (gen4.5) backend
[    30.652] (==) intel(0): Backing store enabled
[    30.652] (==) intel(0): Silken mouse enabled
[    30.740] (II) intel(0): HW Cursor enabled
[    30.740] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    30.763] (==) intel(0): DPMS enabled
[    30.763] (==) intel(0): Display hotplug detection enabled
[    30.763] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[    30.763] (II) intel(0): [DRI2] Setup complete
[    30.763] (II) intel(0): [DRI2]   DRI driver: i965
[    30.763] (II) intel(0): [DRI2]   VDPAU driver: va_gl
[    30.763] (II) intel(0): direct rendering: DRI2 enabled
[    30.763] (II) intel(0): hardware support for Present enabled
[    30.763] (--) RandR disabled
[    30.820] (II) SELinux: Disabled on system
[    31.505] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    31.505] (II) AIGLX: enabled GLX_ARB_create_context
[    31.505] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    31.505] (II) AIGLX: enabled GLX_EXT_create_context_es{,2}_profile
[    31.505] (II) AIGLX: enabled GLX_INTEL_swap_event
[    31.505] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    31.505] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[    31.505] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[    31.505] (II) AIGLX: enabled GLX_EXT_fbconfig_packed_float
[    31.505] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    31.505] (II) AIGLX: Loaded and initialized i965
[    31.505] (II) GLX: Initialized DRI2 GL provider for screen 0
[    31.508] (II) intel(0): switch to mode 1024x768@60.0 on VGA1 using pipe 0, position (0, 0), rotation normal, reflection none
[    31.508] (II) intel(0): Setting screen physical size to 270 x 203
[    31.609] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    31.609] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    31.609] (II) LoadModule: "evdev"
[    31.609] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    31.635] (II) Module evdev: vendor="X.Org Foundation"
[    31.635]     compiled for 1.18.1, module version = 2.10.1
[    31.635]     Module class: X.Org XInput Driver
[    31.635]     ABI class: X.Org XInput driver, version 22.1
[    31.635] (II) Using input driver 'evdev' for 'Power Button'
[    31.635] (**) Power Button: always reports core events
[    31.635] (**) evdev: Power Button: Device: "/dev/input/event1"
[    31.636] (--) evdev: Power Button: Vendor 0 Product 0x1
[    31.636] (--) evdev: Power Button: Found keys
[    31.636] (II) evdev: Power Button: Configuring as keyboard
[    31.636] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    31.636] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    31.636] (**) Option "xkb_rules" "evdev"
[    31.636] (**) Option "xkb_model" "pc105"
[    31.636] (**) Option "xkb_layout" "us"
[    31.636] (II) config/udev: Adding input device Video Bus (/dev/input/event2)
[    31.636] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    31.636] (II) Using input driver 'evdev' for 'Video Bus'
[    31.636] (**) Video Bus: always reports core events
[    31.636] (**) evdev: Video Bus: Device: "/dev/input/event2"
[    31.636] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    31.636] (--) evdev: Video Bus: Found keys
[    31.636] (II) evdev: Video Bus: Configuring as keyboard
[    31.636] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input5/event2"
[    31.636] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    31.636] (**) Option "xkb_rules" "evdev"
[    31.636] (**) Option "xkb_model" "pc105"
[    31.636] (**) Option "xkb_layout" "us"
[    31.637] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    31.637] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    31.637] (II) Using input driver 'evdev' for 'Power Button'
[    31.637] (**) Power Button: always reports core events
[    31.637] (**) evdev: Power Button: Device: "/dev/input/event0"
[    31.637] (--) evdev: Power Button: Vendor 0 Product 0x1
[    31.637] (--) evdev: Power Button: Found keys
[    31.637] (II) evdev: Power Button: Configuring as keyboard
[    31.637] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    31.637] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    31.637] (**) Option "xkb_rules" "evdev"
[    31.637] (**) Option "xkb_model" "pc105"
[    31.637] (**) Option "xkb_layout" "us"
[    31.638] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/event3)
[    31.638] (**) USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[    31.638] (II) Using input driver 'evdev' for 'USB Optical Mouse'
[    31.638] (**) USB Optical Mouse: always reports core events
[    31.638] (**) evdev: USB Optical Mouse: Device: "/dev/input/event3"
[    31.692] (--) evdev: USB Optical Mouse: Vendor 0x4b3 Product 0x310c
[    31.692] (--) evdev: USB Optical Mouse: Found 3 mouse buttons
[    31.692] (--) evdev: USB Optical Mouse: Found scroll wheel(s)
[    31.692] (--) evdev: USB Optical Mouse: Found relative axes
[    31.692] (--) evdev: USB Optical Mouse: Found x and y relative axes
[    31.692] (II) evdev: USB Optical Mouse: Configuring as mouse
[    31.692] (II) evdev: USB Optical Mouse: Adding scrollwheel support
[    31.692] (**) evdev: USB Optical Mouse: YAxisMapping: buttons 4 and 5
[    31.692] (**) evdev: USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    31.692] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.0/0003:04B3:310C.0001/input/input6/event3"
[    31.692] (II) XINPUT: Adding extended input device "USB Optical Mouse" (type: MOUSE, id 9)
[    31.692] (II) evdev: USB Optical Mouse: initialized for relative axes.
[    31.692] (**) USB Optical Mouse: (accel) keeping acceleration scheme 1
[    31.692] (**) USB Optical Mouse: (accel) acceleration profile 0
[    31.692] (**) USB Optical Mouse: (accel) acceleration factor: 2.000
[    31.692] (**) USB Optical Mouse: (accel) acceleration threshold: 4
[    31.692] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/mouse0)
[    31.692] (II) No input driver specified, ignoring this device.
[    31.692] (II) This device may have been added with another device file.
[    31.693] (II) config/udev: Adding input device Dell Dell USB Keyboard Hub (/dev/input/event4)
[    31.693] (**) Dell Dell USB Keyboard Hub: Applying InputClass "evdev keyboard catchall"
[    31.693] (II) Using input driver 'evdev' for 'Dell Dell USB Keyboard Hub'
[    31.693] (**) Dell Dell USB Keyboard Hub: always reports core events
[    31.693] (**) evdev: Dell Dell USB Keyboard Hub: Device: "/dev/input/event4"
[    31.693] (--) evdev: Dell Dell USB Keyboard Hub: Vendor 0x413c Product 0x2010
[    31.693] (--) evdev: Dell Dell USB Keyboard Hub: Found keys
[    31.693] (II) evdev: Dell Dell USB Keyboard Hub: Configuring as keyboard
[    31.693] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.1/usb4/4-2/4-2.1/4-2.1:1.0/0003:413C:2010.0002/input/input7/event4"
[    31.693] (II) XINPUT: Adding extended input device "Dell Dell USB Keyboard Hub" (type: KEYBOARD, id 10)
[    31.693] (**) Option "xkb_rules" "evdev"
[    31.693] (**) Option "xkb_model" "pc105"
[    31.693] (**) Option "xkb_layout" "us"
[    31.694] (II) config/udev: Adding input device Dell Dell USB Keyboard Hub (/dev/input/event5)
[    31.694] (**) Dell Dell USB Keyboard Hub: Applying InputClass "evdev keyboard catchall"
[    31.694] (II) Using input driver 'evdev' for 'Dell Dell USB Keyboard Hub'
[    31.694] (**) Dell Dell USB Keyboard Hub: always reports core events
[    31.694] (**) evdev: Dell Dell USB Keyboard Hub: Device: "/dev/input/event5"
[    31.694] (--) evdev: Dell Dell USB Keyboard Hub: Vendor 0x413c Product 0x2010
[    31.694] (--) evdev: Dell Dell USB Keyboard Hub: Found absolute axes
[    31.694] (II) evdev: Dell Dell USB Keyboard Hub: Forcing absolute x/y axes to exist.
[    31.694] (--) evdev: Dell Dell USB Keyboard Hub: Found keys
[    31.694] (II) evdev: Dell Dell USB Keyboard Hub: Forcing relative x/y axes to exist.
[    31.694] (II) evdev: Dell Dell USB Keyboard Hub: Configuring as mouse
[    31.694] (II) evdev: Dell Dell USB Keyboard Hub: Configuring as keyboard
[    31.694] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.1/usb4/4-2/4-2.1/4-2.1:1.1/0003:413C:2010.0003/input/input8/event5"
[    31.694] (II) XINPUT: Adding extended input device "Dell Dell USB Keyboard Hub" (type: KEYBOARD, id 11)
[    31.694] (**) Option "xkb_rules" "evdev"
[    31.694] (**) Option "xkb_model" "pc105"
[    31.694] (**) Option "xkb_layout" "us"
[    31.694] (II) evdev: Dell Dell USB Keyboard Hub: initialized for absolute axes.
[    31.694] (**) Dell Dell USB Keyboard Hub: (accel) keeping acceleration scheme 1
[    31.694] (**) Dell Dell USB Keyboard Hub: (accel) acceleration profile 0
[    31.694] (**) Dell Dell USB Keyboard Hub: (accel) acceleration factor: 2.000
[    31.694] (**) Dell Dell USB Keyboard Hub: (accel) acceleration threshold: 4
[    31.694] (II) config/udev: Adding input device HDA Intel Line (/dev/input/event7)
[    31.694] (II) No input driver specified, ignoring this device.
[    31.694] (II) This device may have been added with another device file.
[    31.695] (II) config/udev: Adding input device HDA Intel Line Out (/dev/input/event8)
[    31.695] (II) No input driver specified, ignoring this device.
[    31.695] (II) This device may have been added with another device file.
[    31.695] (II) config/udev: Adding input device HDA Intel Front Headphone (/dev/input/event9)
[    31.695] (II) No input driver specified, ignoring this device.
[    31.695] (II) This device may have been added with another device file.
[    31.695] (II) config/udev: Adding input device HDA Intel Mic (/dev/input/event6)
[    31.695] (II) No input driver specified, ignoring this device.
[    31.695] (II) This device may have been added with another device file.
[    31.697] (II) config/udev: Adding input device HP WMI hotkeys (/dev/input/event10)
[    31.697] (**) HP WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    31.697] (II) Using input driver 'evdev' for 'HP WMI hotkeys'
[    31.697] (**) HP WMI hotkeys: always reports core events
[    31.697] (**) evdev: HP WMI hotkeys: Device: "/dev/input/event10"
[    31.697] (--) evdev: HP WMI hotkeys: Vendor 0 Product 0
[    31.697] (--) evdev: HP WMI hotkeys: Found keys
[    31.697] (II) evdev: HP WMI hotkeys: Configuring as keyboard
[    31.697] (**) Option "config_info" "udev:/sys/devices/virtual/input/input13/event10"
[    31.697] (II) XINPUT: Adding extended input device "HP WMI hotkeys" (type: KEYBOARD, id 12)
[    31.697] (**) Option "xkb_rules" "evdev"
[    31.697] (**) Option "xkb_model" "pc105"
[    31.697] (**) Option "xkb_layout" "us"
bwd@bwd-HP-Compaq-8000-Elite-CMT-PC:~$ cat -n /etc/apt/sources.list
     1    #deb cdrom:[Ubuntu 16.04.1 LTS _Xenial Xerus_ - Release amd64 (20160719)]/ xenial main restricted
     2    
     3    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4    # newer versions of the distribution.
     5    deb http://pk.archive.ubuntu.com/ubuntu/ xenial main restricted
     6    # deb-src http://pk.archive.ubuntu.com/ubuntu/ xenial main restricted
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    deb http://pk.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
    11    # deb-src http://pk.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
    12    
    13    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14    ## team, and may not be under a free licence. Please satisfy yourself as to
    15    ## your rights to use the software. Also, please note that software in
    16    ## universe WILL NOT receive any review or updates from the Ubuntu security
    17    ## team.
    18    deb http://pk.archive.ubuntu.com/ubuntu/ xenial universe
    19    # deb-src http://pk.archive.ubuntu.com/ubuntu/ xenial universe
    20    deb http://pk.archive.ubuntu.com/ubuntu/ xenial-updates universe
    21    # deb-src http://pk.archive.ubuntu.com/ubuntu/ xenial-updates universe
    22    
    23    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    24    ## team, and may not be under a free licence. Please satisfy yourself as to 
    25    ## your rights to use the software. Also, please note that software in 
    26    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    27    ## security team.
    28    deb http://pk.archive.ubuntu.com/ubuntu/ xenial multiverse
    29    # deb-src http://pk.archive.ubuntu.com/ubuntu/ xenial multiverse
    30    deb http://pk.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
    31    # deb-src http://pk.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
    32    
    33    ## N.B. software from this repository may not have been tested as
    34    ## extensively as that contained in the main release, although it includes
    35    ## newer versions of some applications which may provide useful features.
    36    ## Also, please note that software in backports WILL NOT receive any review
    37    ## or updates from the Ubuntu security team.
    38    deb http://pk.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
    39    # deb-src http://pk.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
    40    
    41    ## Uncomment the following two lines to add software from Canonical's
    42    ## 'partner' repository.
    43    ## This software is not part of Ubuntu, but is offered by Canonical and the
    44    ## respective vendors as a service to Ubuntu users.
    45    # deb http://archive.canonical.com/ubuntu xenial partner
    46    # deb-src http://archive.canonical.com/ubuntu xenial partner
    47    
    48    deb http://security.ubuntu.com/ubuntu xenial-security main restricted
    49    # deb-src http://security.ubuntu.com/ubuntu xenial-security main restricted
    50    deb http://security.ubuntu.com/ubuntu xenial-security universe
    51    # deb-src http://security.ubuntu.com/ubuntu xenial-security universe
    52    deb http://security.ubuntu.com/ubuntu xenial-security multiverse
    53    # deb-src http://security.ubuntu.com/ubuntu xenial-security multiverse
bwd@bwd-HP-Compaq-8000-Elite-CMT-PC:~$ tail -v -n +1 /etc/apt/sources.list.d/*
tail: cannot open '/etc/apt/sources.list.d/*' for reading: No such file or directory
bwd@bwd-HP-Compaq-8000-Elite-CMT-PC:~$ cat /var/log/gpu-manager.log
log_file: /var/log/gpu-manager.log
last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
can't access /run/u-d-c-nvidia-was-loaded file
can't access /run/u-d-c-fglrx-was-loaded file
Looking for fglrx modules in /lib/modules/4.4.0-31-generic/updates/dkms
Looking for nvidia modules in /lib/modules/4.4.0-31-generic/updates/dkms
Is nvidia loaded? no
Was nvidia unloaded? no
Is nvidia blacklisted? no
Is fglrx loaded? no
Was fglrx unloaded? no
Is fglrx blacklisted? no
Is intel loaded? yes
Is radeon loaded? no
Is radeon blacklisted? no
Is amdgpu loaded? no
Is amdgpu blacklisted? no
Is nouveau loaded? no
Is nouveau blacklisted? no
Is fglrx kernel module available? no
Is nvidia kernel module available? no
Vendor/Device Id: 8086:2e12
BusID "PCI:0@0:2:0"
Is boot vga? yes
Vendor/Device Id: 8086:2e13
BusID "PCI:0@0:2:1"
Is boot vga? no
Error: can't access /sys/bus/pci/devices/0000:00:02.1/driver
The device is not bound to any driver. Skipping...
Skipping "/dev/dri/card0", driven by "i915"
Skipping "/dev/dri/card0", driven by "i915"
Skipping "/dev/dri/card0", driven by "i915"
Found "/dev/dri/card0", driven by "i915"
output 0:
    VGA connector
Number of connected outputs for /dev/dri/card0: 1
Does it require offloading? yes
last cards number = 1
Has amd? no
Has intel? yes
Has nvidia? no
How many cards? 1
Has the system changed? No
main_arch_path x86_64-linux-gnu, other_arch_path i386-linux-gnu
Current alternative: /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf
Current core alternative: (null)
Current egl alternative: /usr/lib/x86_64-linux-gnu/mesa-egl/ld.so.conf
Is nvidia enabled? no
Is nvidia egl enabled? no
Is fglrx enabled? no
Is mesa enabled? yes
Is mesa egl enabled? yes
Is pxpress enabled? no
Is prime enabled? no
Is prime egl enabled? no
Is nvidia available? no
Is nvidia egl available? no
Is fglrx available? no
Is fglrx-core available? no
Is mesa available? yes
Is mesa egl available? yes
Is pxpress available? no
Is prime available? no
Is prime egl available? no
Single card detected
Nothing to do
No change - nothing to do


```

[ATTACH=CONFIG]270275[/ATTACH]

---

