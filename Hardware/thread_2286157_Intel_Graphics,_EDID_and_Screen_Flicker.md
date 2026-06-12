---
title: "Intel Graphics, EDID and Screen Flicker"
date: 2015-07-10
forum: Hardware
---

### Post by Tom_Furniss on 2015-07-10
Hi! This is my first post so apologies if I'm not getting all the conventions right!

My new laptop screen is flickering badly when the intel i915 driver is used for the sole graphics card (Intel HD 5500) - video here: [https://youtu.be/0ISthkP7L3o](https://youtu.be/0ISthkP7L3o)

When an external monitor (HDMI to Samsung TV) is used, that works perfectly and the intel i915 hardware acceleration is active.  Configuring modesetting=0 or i915.modeset=0 in grub effectively prevents the i915 driver from being used and so Ubuntu falls back on vesa.  In this case the laptop screen flickering goes away, but the hardware acceleration of the Intel driver is not used.  Incidentally, this is how I installed Ubuntu.

I have replicated the problem with Ubuntu 14.04 and 15.04, and with kernel versions from 3.9.0-15 up to a mainline version 4 kernel.  I am now using 15.04 default kernel 3.19.0.22.
I have replicated the problem with the latest intel graphics driver versions from the oibaf ppa.
I have replicated on both UEFI and non-UEFI installs of 15.04.
Using xrandr to dynamically set the resolution to each of the available modes does not seem to affect the flickering (maybe marginal increase/decrease in frequency and extent).
Using xrandr to set modes defined from the EDID data and from cvt likewise has no significant effect.
Creating an xorg.conf with many different device and monitor options and resolutions has not resolved the problem.  Currently no xorg.conf files are being used.

I know that the EDID provided by the monitor is incorrect as the screen size is out by a few mm each way, and I suspect that other EDID content may be incorrect which could be causing my issues, but I'm running out of ideas.  Any thoughts on where to go next?

Additional information below.

Hardware

[LIST]
[*]Screen: 13.3" Matte Full HD IPS LED (1920 x 1080)
[*]Processor: Intel® CoreTM i5 Dual Core Processor i5-5200U (2.20GHz, 2.7GHz Turbo)
[*]Graphics: INTEL® HD GRAPHICS 5500
[/LIST]

Install
[LIST]
[*]UEFI
[*]i915.modeset=0
[*]Ubuntu 15.04
[/LIST]


lshw -c video
```
  *-display
       description: VGA compatible controller
       product: Broadwell-U Integrated Graphics
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:50 memory:b1000000-b1ffffff memory:c0000000-cfffffff ioport:4000(size=64)

```

glxinfo | grep -i vendor
```
server glx vendor string: SGI
client glx vendor string: Mesa Project and SGI
OpenGL vendor string: Intel Open Source Technology Center
```

glxinfo | grep -i render
```
direct rendering: Yes
    GLX_MESA_multithread_makecurrent, GLX_MESA_query_renderer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_query_renderer, 
OpenGL renderer string: Mesa DRI Intel(R) HD Graphics 5500 (Broadwell GT2) 
    GL_ARB_conditional_render_inverted, GL_ARB_conservative_depth, 
    GL_MESA_texture_signed_rgba, GL_NV_conditional_render, GL_NV_depth_clamp, 
    GL_ARB_conditional_render_inverted, GL_ARB_conservative_depth, 
    GL_NV_conditional_render, GL_NV_depth_clamp, GL_NV_light_max_exponent, 
    GL_OES_element_index_uint, GL_OES_fbo_render_mipmap, 
```


get-edid | parse-edid
```
Section "Monitor"
    Identifier ""
    ModelName ""
    VendorName "CMN"
    # Monitor Manufactured week 7 of 2014
    # EDID version 1.4
    # Digital Display
    DisplaySize 290 170
    Gamma 2.20
    Option "DPMS" "false"
    Modeline     "Mode 0" 138.78 1920 1966 1996 2080 1080 1082 1086 1112 -hsync -vsync 
    Modeline     "Mode 1" 92.52 1920 1966 1996 2080 1080 1082 1086 1112 -hsync -vsync 
EndSection

```

cat Xorg.0.log
```
[     5.952] 
X.Org X Server 1.17.1
Release Date: 2015-02-10
[     5.952] X Protocol Version 11, Revision 0
[     5.952] Build Operating System: Linux 3.2.0-61-generic x86_64 Ubuntu
[     5.952] Current Operating System: Linux silver 3.19.0-22-generic #22-Ubuntu SMP Tue Jun 16 17:15:15 UTC 2015 x86_64
[     5.952] Kernel command line: BOOT_IMAGE=/vmlinuz-3.19.0-22-generic.efi.signed root=/dev/mapper/ubuntu--vg-root ro splash quiet i915.modeset=1
[     5.952] Build Date: 19 March 2015  09:26:59AM
[     5.952] xorg-server 2:1.17.1-0ubuntu3 (For technical support please see http://www.ubuntu.com/support) 
[     5.952] Current version of pixman: 0.32.6
[     5.952]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[     5.952] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     5.952] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Jul 10 12:19:33 2015
[     5.952] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     5.953] (==) No Layout section.  Using the first Screen section.
[     5.953] (==) No screen section available. Using defaults.
[     5.953] (**) |-->Screen "Default Screen Section" (0)
[     5.953] (**) |   |-->Monitor "<default monitor>"
[     5.953] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[     5.953] (==) Automatically adding devices
[     5.953] (==) Automatically enabling devices
[     5.953] (==) Automatically adding GPU devices
[     5.953] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     5.953]     Entry deleted from font path.
[     5.953] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     5.953]     Entry deleted from font path.
[     5.953] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     5.953]     Entry deleted from font path.
[     5.953] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     5.953]     Entry deleted from font path.
[     5.953] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     5.953]     Entry deleted from font path.
[     5.953] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[     5.953] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     5.953] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[     5.953] (II) Loader magic: 0x7f47d3948d80
[     5.953] (II) Module ABI versions:
[     5.953]     X.Org ANSI C Emulation: 0.4
[     5.953]     X.Org Video Driver: 19.0
[     5.953]     X.Org XInput driver : 21.0
[     5.953]     X.Org Server Extension : 9.0
[     5.953] (II) xfree86: Adding drm device (/dev/dri/card0)
[     5.954] (--) PCI:*(0:0:2:0) 8086:1616:1991:5591 rev 9, Mem @ 0xb1000000/16777216, 0xc0000000/268435456, I/O @ 0x00004000/64
[     5.954] (II) LoadModule: "glx"
[     5.954] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[     5.962] (II) Module glx: vendor="X.Org Foundation"
[     5.962]     compiled for 1.17.1, module version = 1.0.0
[     5.962]     ABI class: X.Org Server Extension, version 9.0
[     5.962] (==) AIGLX enabled
[     5.962] (==) Matched intel as autoconfigured driver 0
[     5.962] (==) Matched intel as autoconfigured driver 1
[     5.962] (==) Matched modesetting as autoconfigured driver 2
[     5.962] (==) Matched fbdev as autoconfigured driver 3
[     5.962] (==) Matched vesa as autoconfigured driver 4
[     5.962] (==) Assigned the driver to the xf86ConfigLayout
[     5.962] (II) LoadModule: "intel"
[     5.962] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[     5.963] (II) Module intel: vendor="X.Org Foundation"
[     5.963]     compiled for 1.17.1, module version = 2.99.917
[     5.963]     Module class: X.Org Video Driver
[     5.963]     ABI class: X.Org Video Driver, version 19.0
[     5.963] (II) LoadModule: "modesetting"
[     5.963] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[     5.963] (II) Module modesetting: vendor="X.Org Foundation"
[     5.963]     compiled for 1.17.1, module version = 1.17.1
[     5.963]     Module class: X.Org Video Driver
[     5.963]     ABI class: X.Org Video Driver, version 19.0
[     5.963] (II) LoadModule: "fbdev"
[     5.963] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     5.963] (II) Module fbdev: vendor="X.Org Foundation"
[     5.963]     compiled for 1.17.1, module version = 0.4.4
[     5.963]     Module class: X.Org Video Driver
[     5.963]     ABI class: X.Org Video Driver, version 19.0
[     5.963] (II) LoadModule: "vesa"
[     5.963] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     5.963] (II) Module vesa: vendor="X.Org Foundation"
[     5.963]     compiled for 1.17.1, module version = 2.3.3
[     5.963]     Module class: X.Org Video Driver
[     5.963]     ABI class: X.Org Video Driver, version 19.0
[     5.963] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[     5.963] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[     5.963] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[     5.963] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[     5.963] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[     5.963] (II) FBDEV: driver for framebuffer: fbdev
[     5.963] (II) VESA: driver for VESA chipsets: vesa
[     5.963] (++) using VT number 7


[     5.963] (II) intel(0): Using Kernel Mode Setting driver: i915, version 1.6.0 20141121
[     5.963] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.99.917-1~exp1ubuntu2.2 (Alessio Treglia <quadrispro@ubuntu.com>)
[     5.963] (II) intel(0): SNA compiled for use with valgrind
[     5.963] (WW) Falling back to old probe method for modesetting
[     5.963] (WW) Falling back to old probe method for fbdev
[     5.963] (II) Loading sub module "fbdevhw"
[     5.963] (II) LoadModule: "fbdevhw"
[     5.964] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[     5.964] (II) Module fbdevhw: vendor="X.Org Foundation"
[     5.964]     compiled for 1.17.1, module version = 0.0.2
[     5.964]     ABI class: X.Org Video Driver, version 19.0
[     5.965] (WW) Falling back to old probe method for vesa
[     5.965] (--) intel(0): Integrated Graphics Chipset: Intel(R) HD graphics 5500
[     5.965] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2, avx, avx2
[     5.965] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[     5.965] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[     5.965] (==) intel(0): RGB weight 888
[     5.965] (==) intel(0): Default visual is TrueColor
[     5.965] (II) intel(0): Output eDP1 has no monitor section
[     5.965] (--) intel(0): Found backlight control interface intel_backlight (type 'raw') for output eDP1
[     5.965] (II) intel(0): Enabled output eDP1
[     5.965] (II) intel(0): Output HDMI1 has no monitor section
[     5.965] (II) intel(0): Enabled output HDMI1
[     5.965] (--) intel(0): Using a maximum size of 256x256 for hardware cursors
[     5.965] (II) intel(0): Output VIRTUAL1 has no monitor section
[     5.965] (II) intel(0): Enabled output VIRTUAL1
[     5.965] (--) intel(0): Output eDP1 using initial mode 1920x1080 on pipe 0
[     5.965] (==) intel(0): TearFree disabled
[     5.965] (==) intel(0): DPI set to (96, 96)
[     5.965] (II) Loading sub module "dri2"
[     5.965] (II) LoadModule: "dri2"
[     5.965] (II) Module "dri2" already built-in
[     5.965] (II) Loading sub module "present"
[     5.965] (II) LoadModule: "present"
[     5.965] (II) Module "present" already built-in
[     5.980] (II) UnloadModule: "modesetting"
[     5.980] (II) Unloading modesetting
[     5.980] (II) UnloadModule: "fbdev"
[     5.980] (II) Unloading fbdev
[     5.980] (II) UnloadSubModule: "fbdevhw"
[     5.980] (II) Unloading fbdevhw
[     5.980] (II) UnloadModule: "vesa"
[     5.980] (II) Unloading vesa
[     5.980] (==) Depth 24 pixmap format is 32 bpp
[     5.980] (II) intel(0): SNA initialized with Broadwell backend
[     5.980] (==) intel(0): Backing store enabled
[     5.980] (==) intel(0): Silken mouse enabled
[     5.980] (II) intel(0): HW Cursor enabled
[     5.980] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[     5.980] (==) intel(0): DPMS enabled
[     5.980] (==) intel(0): display hotplug detection enabled
[     5.980] (II) intel(0): [DRI2] Setup complete
[     5.980] (II) intel(0): [DRI2]   DRI driver: i965
[     5.980] (II) intel(0): [DRI2]   VDPAU driver: i965
[     5.980] (II) intel(0): direct rendering: DRI2 enabled
[     5.980] (II) intel(0): hardware support for Present enabled
[     5.980] (--) RandR disabled
[     5.984] (II) SELinux: Disabled on system
[     6.016] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[     6.016] (II) AIGLX: enabled GLX_ARB_create_context
[     6.016] (II) AIGLX: enabled GLX_ARB_create_context_profile
[     6.016] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[     6.016] (II) AIGLX: enabled GLX_INTEL_swap_event
[     6.016] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[     6.016] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[     6.016] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[     6.016] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[     6.016] (II) AIGLX: enabled GLX_ARB_create_context_robustness
[     6.016] (II) AIGLX: Loaded and initialized i965
[     6.016] (II) GLX: Initialized DRI2 GL provider for screen 0
[     6.020] (II) intel(0): switch to mode 1920x1080@60.0 on eDP1 using pipe 0, position (0, 0), rotation normal, reflection none
[     6.032] (II) intel(0): Setting screen physical size to 508 x 285
[     6.040] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[     6.043] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[     6.043] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     6.043] (II) LoadModule: "evdev"
[     6.043] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     6.044] (II) Module evdev: vendor="X.Org Foundation"
[     6.044]     compiled for 1.16.0, module version = 2.9.0
[     6.044]     Module class: X.Org XInput Driver
[     6.044]     ABI class: X.Org XInput driver, version 21.0
[     6.044] (II) Using input driver 'evdev' for 'Power Button'
[     6.044] (**) Power Button: always reports core events
[     6.044] (**) evdev: Power Button: Device: "/dev/input/event3"
[     6.044] (--) evdev: Power Button: Vendor 0 Product 0x1
[     6.044] (--) evdev: Power Button: Found keys
[     6.044] (II) evdev: Power Button: Configuring as keyboard
[     6.044] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[     6.044] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[     6.044] (**) Option "xkb_rules" "evdev"
[     6.045] (**) Option "xkb_model" "pc105"
[     6.045] (**) Option "xkb_layout" "gb"
[     6.047] (II) XKB: reuse xkmfile /var/lib/xkb/server-2B4266AA55228AE7D9557A18F1965DBA19850816.xkm
[     6.048] (II) config/udev: Adding input device Video Bus (/dev/input/event7)
[     6.048] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[     6.048] (II) Using input driver 'evdev' for 'Video Bus'
[     6.048] (**) Video Bus: always reports core events
[     6.048] (**) evdev: Video Bus: Device: "/dev/input/event7"
[     6.048] (--) evdev: Video Bus: Vendor 0 Product 0x6
[     6.048] (--) evdev: Video Bus: Found keys
[     6.048] (II) evdev: Video Bus: Configuring as keyboard
[     6.048] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input9/event7"
[     6.048] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[     6.048] (**) Option "xkb_rules" "evdev"
[     6.048] (**) Option "xkb_model" "pc105"
[     6.048] (**) Option "xkb_layout" "gb"
[     6.048] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[     6.048] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     6.048] (II) Using input driver 'evdev' for 'Power Button'
[     6.048] (**) Power Button: always reports core events
[     6.048] (**) evdev: Power Button: Device: "/dev/input/event1"
[     6.048] (--) evdev: Power Button: Vendor 0 Product 0x1
[     6.048] (--) evdev: Power Button: Found keys
[     6.048] (II) evdev: Power Button: Configuring as keyboard
[     6.048] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1/event1"
[     6.048] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[     6.048] (**) Option "xkb_rules" "evdev"
[     6.048] (**) Option "xkb_model" "pc105"
[     6.048] (**) Option "xkb_layout" "gb"
[     6.049] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[     6.049] (II) No input driver specified, ignoring this device.
[     6.049] (II) This device may have been added with another device file.
[     6.049] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[     6.049] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[     6.049] (II) Using input driver 'evdev' for 'Sleep Button'
[     6.049] (**) Sleep Button: always reports core events
[     6.049] (**) evdev: Sleep Button: Device: "/dev/input/event2"
[     6.049] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[     6.049] (--) evdev: Sleep Button: Found keys
[     6.049] (II) evdev: Sleep Button: Configuring as keyboard
[     6.049] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2/event2"
[     6.049] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[     6.049] (**) Option "xkb_rules" "evdev"
[     6.049] (**) Option "xkb_model" "pc105"
[     6.049] (**) Option "xkb_layout" "gb"
[     6.050] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=3 (/dev/input/event8)
[     6.050] (II) No input driver specified, ignoring this device.
[     6.050] (II) This device may have been added with another device file.
[     6.050] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=7 (/dev/input/event9)
[     6.050] (II) No input driver specified, ignoring this device.
[     6.050] (II) This device may have been added with another device file.
[     6.050] (II) config/udev: Adding input device USB 2.0 Camera  (/dev/input/event5)
[     6.050] (**) USB 2.0 Camera : Applying InputClass "evdev keyboard catchall"
[     6.050] (II) Using input driver 'evdev' for 'USB 2.0 Camera '
[     6.050] (**) USB 2.0 Camera : always reports core events
[     6.050] (**) evdev: USB 2.0 Camera : Device: "/dev/input/event5"
[     6.050] (--) evdev: USB 2.0 Camera : Vendor 0x58f Product 0x3822
[     6.050] (--) evdev: USB 2.0 Camera : Found keys
[     6.050] (II) evdev: USB 2.0 Camera : Configuring as keyboard
[     6.050] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-5/1-5:1.0/input/input8/event5"
[     6.050] (II) XINPUT: Adding extended input device "USB 2.0 Camera " (type: KEYBOARD, id 10)
[     6.050] (**) Option "xkb_rules" "evdev"
[     6.050] (**) Option "xkb_model" "pc105"
[     6.050] (**) Option "xkb_layout" "gb"
[     6.051] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event10)
[     6.051] (II) No input driver specified, ignoring this device.
[     6.051] (II) This device may have been added with another device file.
[     6.051] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event11)
[     6.051] (II) No input driver specified, ignoring this device.
[     6.051] (II) This device may have been added with another device file.
[     6.051] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[     6.051] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[     6.051] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[     6.051] (**) AT Translated Set 2 keyboard: always reports core events
[     6.051] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[     6.051] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[     6.051] (--) evdev: AT Translated Set 2 keyboard: Found keys
[     6.051] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[     6.051] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[     6.051] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 11)
[     6.051] (**) Option "xkb_rules" "evdev"
[     6.051] (**) Option "xkb_model" "pc105"
[     6.051] (**) Option "xkb_layout" "gb"
[     6.052] (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/event6)
[     6.052] (**) ImPS/2 Generic Wheel Mouse: Applying InputClass "evdev pointer catchall"
[     6.052] (II) Using input driver 'evdev' for 'ImPS/2 Generic Wheel Mouse'
[     6.052] (**) ImPS/2 Generic Wheel Mouse: always reports core events
[     6.052] (**) evdev: ImPS/2 Generic Wheel Mouse: Device: "/dev/input/event6"
[     6.052] (--) evdev: ImPS/2 Generic Wheel Mouse: Vendor 0x2 Product 0x5
[     6.052] (--) evdev: ImPS/2 Generic Wheel Mouse: Found 3 mouse buttons
[     6.052] (--) evdev: ImPS/2 Generic Wheel Mouse: Found scroll wheel(s)
[     6.052] (--) evdev: ImPS/2 Generic Wheel Mouse: Found relative axes
[     6.052] (--) evdev: ImPS/2 Generic Wheel Mouse: Found x and y relative axes
[     6.052] (II) evdev: ImPS/2 Generic Wheel Mouse: Configuring as mouse
[     6.052] (II) evdev: ImPS/2 Generic Wheel Mouse: Adding scrollwheel support
[     6.052] (**) evdev: ImPS/2 Generic Wheel Mouse: YAxisMapping: buttons 4 and 5
[     6.052] (**) evdev: ImPS/2 Generic Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     6.052] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input7/event6"
[     6.052] (II) XINPUT: Adding extended input device "ImPS/2 Generic Wheel Mouse" (type: MOUSE, id 12)
[     6.052] (II) evdev: ImPS/2 Generic Wheel Mouse: initialized for relative axes.
[     6.052] (**) ImPS/2 Generic Wheel Mouse: (accel) keeping acceleration scheme 1
[     6.052] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration profile 0
[     6.052] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration factor: 2.000
[     6.052] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration threshold: 4
[     6.052] (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/mouse0)
[     6.052] (II) No input driver specified, ignoring this device.
[     6.052] (II) This device may have been added with another device file.
[     6.512] (II) intel(0): EDID vendor "CMN", prod id 4961
[     6.512] (II) intel(0): Printing DDC gathered Modelines:
[     6.512] (II) intel(0): Modeline "1920x1080"x0.0  138.78  1920 1966 1996 2080  1080 1082 1086 1112 -hsync -vsync (66.7 kHz eP)
[     6.512] (II) intel(0): Modeline "1920x1080"x0.0   92.52  1920 1966 1996 2080  1080 1082 1086 1112 -hsync -vsync (44.5 kHz e)
[    17.861] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    18.685] (II) XKB: reuse xkmfile /var/lib/xkb/server-B8CD4FE5A1833D7AB4B402792017A55B628FCF2D.xkm
[    18.699] (II) XKB: reuse xkmfile /var/lib/xkb/server-B8CD4FE5A1833D7AB4B402792017A55B628FCF2D.xkm
[    20.255] (II) XKB: reuse xkmfile /var/lib/xkb/server-5841764B120E02BC6FD78DAB262CEA727EB95BEE.xkm

```

---

### Post by dino99 on 2015-07-10
looks like a frequency issue; but start checking step by step: only the laptop first. journalctl might help finding something usefull to digg around that issue. Then if you have some doubts about edid, there is a new version of edid-decode into the Wily archive.
Is that laptop having something special ? like overclocked or refurbished

maybe boot without "splash quiet i915.modeset=1" to let you see the verbose boot comments. Why 'i915.modeset=1 is added ?

---

### Post by Tom_Furniss on 2015-07-10
Hi Dino, thanks for pointing me to journalctl, I'm playing with it now - particularly the persistent storage option to see the logs from previous boots.

I'm trying to avoid plugging in the external monitor, but there are times when I need to be able to see what I'm doing...  With laptop screen alone the problem persists.  Connecting the monitor, either before boot or after boot, seems to have no impact on the laptop screen flickering.

The laptop isn't anything special.  It's a Lafite 13.3 from PC Specialist in the UK.  I'll remove the "splash and quiet" options.  "i915.modeset=1" is only there to facilitate testing.  The default is "1", so it makes no difference when it is set, but I often switch it off at boot.

edid-decode is providing more detail than get-edid did.  Interestingly telling us that it is, "Missing monitor ranges" from the edid file.

```
tom@silver:~$ cat Documents/Technology/Lafite/logs/edid.bin | edid-decode 
Extracted contents:
header:          00 ff ff ff ff ff ff 00
serial number:   0d ae 61 13 00 00 00 00 07 18
version:         01 04
basic params:    a5 1d 11 78 02
chroma info:     ce 85 a3 57 4e 9d 26 12 50 54
established:     00 00 00
standard:        01 01 01 01 01 01 01 01 01 01 01 01 01 01 01 01
descriptor 1:    36 36 80 a0 70 38 20 40 2e 1e 24 00 25 a5 10 00 00 18
descriptor 2:    24 24 80 a0 70 38 20 40 2e 1e 24 00 25 a5 10 00 00 18
descriptor 3:    00 00 00 fe 00 43 4d 4e 0a 20 20 20 20 20 20 20 20 20
descriptor 4:    00 00 00 fe 00 4e 31 33 33 48 53 45 2d 45 41 33 0a 20
extensions:      00
checksum:        a1


Manufacturer: CMN Model 1361 Serial Number 0
Made week 7 of 2014
EDID version: 1.4
Digital display
8 bits per primary color channel
DisplayPort interface
Maximum image size: 29 cm x 17 cm
Gamma: 2.20
Supported color formats: RGB 4:4:4
First detailed timing is preferred timing
Established timings supported:
Standard timings supported:
Detailed mode: Clock 138.780 MHz, 293 mm x 165 mm
               1920 1966 1996 2080 hborder 0
               1080 1082 1086 1112 vborder 0
               -hsync -vsync
Detailed mode: Clock 92.520 MHz, 293 mm x 165 mm
               1920 1966 1996 2080 hborder 0
               1080 1082 1086 1112 vborder 0
               -hsync -vsync
ASCII string: CMN
         ASCII string: N133HSE-EA3
 Checksum: 0xa1
EDID block does NOT conform to EDID 1.3!
    Missing name descriptor
    Missing monitor ranges
tom@silver:~$
```

Well, journalctl is not showing anything unusual that might be related to this.  As far as I can tell, Linux thinks everything is great - no errors on the i915 driver, no errors for X, just a screen that isn't rendering correctly.

The shop that provided the laptop suggested it might be an LVDS cable issue, but could an LVDS cable issue only affect hardware accelerated graphics?

My next step is to get hold of a copy of the EDID data for a working Lafite 13.3 laptop, to compare it with mine, but any other suggestions are welcome.

---

### Post by dino99 on 2015-07-12
******
EDID block does NOT conform to EDID 1.3!
    Missing name descriptor
    Missing monitor ranges
**********

That PC specialist needs to do its job; its probably the reason of your issue. Request the guaranty if it has not expired, and/or tell him you will file complaint for selling bad hardware integration. Or request an exchange with a new guaranty.

---

### Post by Tom_Furniss on 2015-07-13
I agree with the sentiment, but thought I'd check the standard before getting back to the supplier.  Looks like "monitor ranges", which I assume are "Monitor Range Limits", were renamed to "Display Range Limits" in version 1.4 Release A Revision 2.  In EDID standard 1.3, this parameter was mandatory, but in EDID 1.4 it is not:
> A Display Range Limits Descriptor (which was required in EDID data structure version 1, revision 3) is optional (but recommended) in EDID data structure version 1, revision 4.  Continuous frequency displays (which may support GTF or CVT) are required to include the
Display Range Limit Descriptor.


But how to tell if my screen is a "continuous frequency display"?

Same goes for the Name Descriptor:
> A Display Product Name Descriptor (required in EDID data structure version 1, revision 3) is optional (but recommended) in EDID data structure version 1, revision 4.


So edid-decode is right that the EDID is not 1.3 compliant, it also correctly identifies the EDID version as 1.4, and doesn't make a statement on compliance to that version.  The EDID standard strongly recommends the use of EDID 1.4 over earlier standards for new designs, so it may be that the manufacturer of my screen has just moved to version 1.4.

My source here is a 2006 copy of the standard downloaded from a Taiwanese university ( [ftp://ftp.cis.nctu.edu.tw/pub/csie/Software/X11/private/VeSaSpEcS/VESA_Document_Center_Monitor_Interface/EEDIDrAr2.pdf](ftp://ftp.cis.nctu.edu.tw/pub/csie/Software/X11/private/VeSaSpEcS/VESA_Document_Center_Monitor_Interface/EEDIDrAr2.pdf) ).  Seems that VESA like people to pay for the documentation.

So this *could* be a scenario where the screen is compliant with EDID 1.4, but the intel driver still requires the "Display Range Limits" of version 1.3.  I'm not sure how to prove that without a 1.3 compliant EDID for the screen.

---

### Post by CitadelUniversal on 2015-07-13
Can you enter your bios and change the graphics card display so it uses lets say Nvidia or AMD instead of using the intel graphics, it might be struggling because of two graphics cards conflicting to each other forgive me if I'm wrong. To enter bios is usually F1 or one of the Function keys and there should be a graphics card option in one of the settings.....

---

### Post by Tom_Furniss on 2015-07-13
Hi CidatelUniversal, thanks for joining the discussion.  There is just the one graphics card in the laptop - the integrated graphics on the motherboard.

---

### Post by CitadelUniversal on 2015-07-13
I've re-read the issue which you are having and looked up the model of your laptop, do you have 3D enabled? if not would the 3d acceleration software "Driconf" work for you and hopefully stop the flickering? Have you installed the latest intel graphics card drivers for linux - sometimes the flickering could mean the drivers isn't installed, try installing the graphics card via the additional drivers software and see if the Intel Iris Graphics card is installed or enabled.....

---

### Post by Tom_Furniss on 2015-07-13
I installed driconf, and used it to disable 3d acceleration, then restarted, but the symptoms persist.  "glxinfo | grep render" still shows direct rendering as enabled so I'm not sure the driconf took effect - is there something else I should do?

I suspect that the problem is the combination of graphics card and screen.  I have played a 3D game on the external monitor, using the i915 driver, with no problems at all, so I am comfortable that the graphics card and driver are working well together.  Just not with the laptop screen.

[EDIT] I tried the latest obaif ppa intel drivers and the problem persisted.  As far as I know, because intel open sourced their Linux drivers, there are no proprietary Linux drivers for intel graphics.  The intel i915 driver is being loaded without error, so I think it is installed correctly. [/EDIT]

---

### Post by bradley-m-hart on 2015-07-18
Hi Tom,

I am also having the exact same problem as you with this with the same laptop for pc specialist. The anoying thing is that I got this laptop after reading post from others that it work well with ubuntu. 

Have you had any luck so far trying to solve the problem. What is interesting is my EDID is also saying "Made week 7 of 2014", I wonder if there was a bad batch of montior screens maybe... Seems odd that others are not having this issue.

Have you contacted PC Specialist about this at all?

I have read that it is possible to get the EDID from windows and then copy it over to ubuntu and set it as a custom EDID, have you tried this yet. I think I will give this a go...

---

### Post by Tom_Furniss on 2015-07-19
Hi Bradley

Sorry to hear that you're suffering with this too, but at least now I'm not alone!

I have been in touch with pc specialist support, and they were offered to take the laptop back for repair, but if the issue was found to be software (i.e. not hardware) then they would charge me.  They suggested it could be a loose LVDS cable, but I am sceptical that a loose cable would only affect the screen when the i915 driver is used.  Ultimately they said they didn't support Linux so unless I could recreate the problem on Windows they wouldn't support it.

But it's interesting that you have the problem too.  Suggests that it's not something either one of us is doing obviously wrong, and that it probably is hardware related - either a hardware fault (maybe EDID), or a deficiency in the way Linux handles a legitimate hardware change.  Either way it seems to be the combination of the Linux i915 driver and the Lafite screen that causes the problem.

The options I've been considering now are:
[LIST=1]
[*]**EDID**.  Acquire the EDID content from a Lafite laptop that runs Linux (without problems), and try to apply that to my laptop.  There is a software method of doing this but I don't think the i915 driver supports it, so it would be a high risk attempt to write directly to the monitor.  However my thread on the Linux forum of pc specialist has gone unanswered, as have my private messages to those forum users who have Linux working on their Lafite's.
[*]**Windows**.  Try to recreate the problem on Windows.  I am not convinced that this would help.  Surely this would have been identified before as most users of this model of laptop will use Windows.
[*]**Driver**.  Start a thread in the forum of the group that develop the i915 driver to get their view on whether the driver is the problem rather than the screen.  But first I have to find them...
[*]**Give up**.  I'm really tempted to sell the laptop and start again with something else.  But maybe this is the one chance to give something back to the Linux community that has served me so well for the last decade or more.
[/LIST]

Any other ideas?

I've created a bug report with the intel driver developers.  Let's see what happens next!  [https://bugs.freedesktop.org/show_bug.cgi?id=91393](https://bugs.freedesktop.org/show_bug.cgi?id=91393)

---

### Post by oldfred on 2015-07-19
You  have a very new Intel video chip.

Some with new Intel use a specific X x Y setting for monitor instead of nomodeset.
       Force Intel Video mode as boot parameter in grub menu - Must change to your screen size, not 1280x1024
video=1280x1024-24@60
and if that doesn't work you can try
video=VGA-1:1280x1024-24@60

    Some other settings that older than yours but still newer version of Intel chips needed:
 acpi_osi=Linux  acpi_backlight=vendor
 i915.i915_enable_rc6=1

Intel not only updates video driver, but also kernel & support software. I would only use 15.04 as starting point, but you may need both Oibaf ppa and a kernel ppa.

       Oibaf PPA discusion
 [http://www.phoronix.com/scan.php?page=article&item=ubuntu_1310_oibaf&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1310_oibaf&num=1)
New kernels ppa
[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D](http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D)
Ubuntu Kernel Mainline PPA
[http://www.phoronix.com/scan.php?page=article&item=amd_cat144_hd56&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_cat144_hd56&num=1)
[https://launchpad.net/~kernel-ppa/+archive/ubuntu/pre-proposed](https://launchpad.net/~kernel-ppa/+archive/ubuntu/pre-proposed)

---

### Post by Tom_Furniss on 2015-07-19
Hi oldfred, thanks for your suggestions.

I've tried the different kernel boot parameters in a variety of combinations and the symptoms remain.  The final configuration was:  GRUB_CMDLINE_LINUX_DEFAULT="video=1920x1080-24@60 acpi_osi=Linux acpi_backlight=vendor i915.i915_enable=rc6 drm.debug=0x1e log_buf_len=1M plymouth:debug"

I am currently running the latest intel-drm-nighty kernel (4.2.0-994-generic #201507142205) from the ubuntu mainline repository that you referenced.  I've tried several kernels from 3.15 upwards, both with and without the obaif ppa.  In all cases the symptoms are the same.

Any thoughts on where to go next?

---

### Post by oldfred on 2015-07-19
The suggestions were mostly an OR not an AND.
Not then sure if they conflict? 

Not sure what else to try, only seen various posts on issues, not actually needed any with my system.

Best to just boot to grub menu, use e for edit and scroll to linux line and add/change settings. Then you can experiment before finalizing in grub's standard settings.

But if running newest kernels & drivers, I do not know what to suggest.

This post discusses another Intel chip that has issues.
He is knowledgeable and still had issues.
[http://www.phoronix.com/scan.php?page=news_item&px=Fedora-22-Good-For-5775](http://www.phoronix.com/scan.php?page=news_item&px=Fedora-22-Good-For-5775)
Several other posts on various settings and others on video for different versions of Intel in his forum.
[http://www.phoronix.com/scan.php?page=article&item=intel-celeron-n3050&num=1](http://www.phoronix.com/scan.php?page=article&item=intel-celeron-n3050&num=1)
[http://www.phoronix.com/scan.php?page=article&item=intel-iris-6200&num=1](http://www.phoronix.com/scan.php?page=article&item=intel-iris-6200&num=1)

---

### Post by bradley-m-hart on 2015-07-21
I have managed to extract the EDID from the Windows registry and there are some small differences there with the one shown from Ubuntu. I am going to get linux to override it using drm_kms_helper.edid_firmware=edid/edid.bin and see what happens. I will let you know how it goes. I will try after upgrading to 15.04.

Ok it did not work. I even tried the built in edid "[COLOR=#000000][FONT=sans-serif]edid/1920x1080.bin[/FONT][/COLOR]" and the problem still persists. From the log output it looks like everything was picked up ok. Looks like it is not an issue with the EDID

I am starting to link that this maybe a loose cable. I am going to put a bit of effort into reproducing this Windows, maybe when hardware acceleration is on the a cable get used that wouldn't have before, who knows. The nature of this problem is weird, it is hard to imagine a software error causing this. I find that the severity of it is random too, sometimes it is really bad, other times it is not hardly noticeable, after sometime the screen will just go blank.

I can not replicate this in Windows, I have the Intel drivers installed and everything is working great. So it seems the hardware is fine (no loose cable). The EDID is fine too meaning it must be a problem with the intel linux driver. My plan is to just run Windows for now and use an Ubuntu in a VM for my development activities and hope that one day the driver is fixed :)

---

### Post by Tom_Furniss on 2015-07-23
I still suspect there's something in the EDID that has changed since the last known working versions on Ubuntu, but it is still interesting that the EDID extracted through Windows is different from the EDID extracted through Linux - it's the same screen and EDID after all!

Thanks for putting in the effort to test on Windows too, which does seem to rule out the loose cable theory.  I'll follow up again on the pcspecialist forum and private messages to try to get hold of the last known good EDID.  I'll also see if pcspecialist support will tell me if anything in the hardware changed.

Still no update on the bug report I raised, but I'm hopeful they'll get there in the end.

---

### Post by Tom_Furniss on 2015-07-25
[FONT=arial]pcspecialist support have responded with this statement, "[COLOR=#212121]Nothing has been changed on this chassis it is the same as it was on the date it was released.".

So that at least suggests that there were no major hardware changes, but doesn't rule out minor version changes in the screen from their supplier.[/COLOR][/FONT]

---

### Post by bradley-m-hart on 2015-07-30
Hi Tom,

I am sending the laptop back to get another issue fixed (it keeps turning off when on battery randomly). I have also asked them to look at this thread and check the cable problem too. I will let you know what happens.

---

### Post by tcmreastwood-gmail on 2015-08-06
I've already posted in the pcspecialist forums, but have you tried making your own /etc/X11/xorg.conf and using AccelMethod "uxa" instead of "sna" ? I'm running on my Lafite with no problems since doing that.

---

### Post by Tom_Furniss on 2015-08-08
Unfortunately that doesn't work for me, but it's great that you've seen the problem and fixed it...  I can see from my xorg log that the "uxa" option is picked up, but the flickering is unchanged.  Would you mind posting the output of "lshw -c video"?  I'd also be interested in seeing your boot options.  What version of Ubuntu (and kernel) are you running?

Incidentally, my xorg.conf doesn't seem to be picked up when it's in the /etc/X11 folder, but is picked up when it's in /usr/share/X11/xorg.conf.d/ .

---

### Post by tcmreastwood-gmail on 2015-08-08
That's odd :( - I'm currently not running ubuntu unfortunately - I'm running voidlinux with a 4.1.4 kernel: [https://gist.github.com/anonymous/a5ebb6494cc39516a407](https://gist.github.com/anonymous/a5ebb6494cc39516a407)

---

### Post by freechelmi on 2015-09-16
Hi 

I have the i5 and pentium version of the Lafité ( topstar u731)

The i5 never had this problem but the pentium has it.

---

### Post by laurinehu on 2015-11-08
Hello everybody,

I'm just here to say that I have the same problem with the same laptop, and also no issues......
I do not have many skills in system so I do not understand everything you're saying but what I understand is that there are no issues and we have to wait til the problem will be solved by ubuntu...  ? 

I do not understand why some people on pc specialist told that ubuntu worked without any problem..
It's my working tool and it's been 6 months I'm working on this screen giving me headache :(

Can anyone tell what's new since september ? 

I'm happy not to be alone in this case.. and hope we'll find an issue together.


I'm sorry for my bad english, hope you understand what i'm saying :lolflag:

---

### Post by freechelmi on 2015-11-08
Because some topstar u731 had another screen which does not have this problem ( like the one from february 2015 ) and some from june 2015 have this problem because of another screen provider.

Some engineer at intel works on it and the have isolated the kernel commit which cause this problem, so i'm confident that this might be backported for kernel 4.2 and thus Ubuntu 14.04.4

---

### Post by lorebett on 2015-11-23
> **freechelmi said:**
> Because some topstar u731 had another screen which does not have this problem ( like the one from february 2015 ) and some from june 2015 have this problem because of another screen provider.

Some engineer at intel works on it and the have isolated the kernel commit which cause this problem, so i'm confident that this might be backported for kernel 4.2 and thus Ubuntu 14.04.4

As for today, in ubuntu 15.10, kernel 4.2.0-18, the problem is still there...
Could you please provide a link to the bug related to the kernel commit you're mentioning?

---

### Post by freechelmi on 2015-11-23
There is a new patch that enable to disable the feature that cause this problem 

[https://bugs.freedesktop.org/show_bug.cgi?id=91393](https://bugs.freedesktop.org/show_bug.cgi?id=91393)

---

### Post by lorebett on 2015-11-23
> **freechelmi said:**
> There is a new patch that enable to disable the feature that cause this problem 

[https://bugs.freedesktop.org/show_bug.cgi?id=91393](https://bugs.freedesktop.org/show_bug.cgi?id=91393)

should I install kernel sources or are kernel headers enough to test the patch?

---

### Post by lorebett on 2015-11-24
Some updates. I left a comment on the bug, [https://bugs.freedesktop.org/show_bug.cgi?id=91393#c32](https://bugs.freedesktop.org/show_bug.cgi?id=91393#c32), I can't apply the latest patch to my kernel, but reverting the two commits as mentioned in [https://bugs.freedesktop.org/show_bug.cgi?id=91393#c25](https://bugs.freedesktop.org/show_bug.cgi?id=91393#c25) fixes the flickering problem for me! :KS

---

### Post by scott41 on 2015-11-28
Hi lorebett. If possible could you mention how you managed to revert the commits? Sorry slightly new to using git, i've recently bought the same Lafite laptop and want to run Ubuntu instead of Windows but I can't at the moment as the screen flickering makes it unusable.

---

### Post by lorebett on 2015-12-01
> **scott41 said:**
> Hi lorebett. If possible could you mention how you managed to revert the commits? Sorry slightly new to using git, i've recently bought the same Lafite laptop and want to run Ubuntu instead of Windows but I can't at the moment as the screen flickering makes it unusable.

I've just written a blog post that the details the all procedure:

[http://www.lorenzobettini.it/2015/12/flickering-for-intel-graphic-card-in-linux-4-2/](http://www.lorenzobettini.it/2015/12/flickering-for-intel-graphic-card-in-linux-4-2/)

please let me know if it works for you as well.

---

### Post by Tom_Furniss on 2015-12-12
The patch worked for me - flickering issue finally resolved.

---

### Post by Retna on 2015-12-13
> **Tom_Furniss said:**
> The patch worked for me - flickering issue finally resolved.

Hi Tom,

I have the same screen problem as you did. Which version of Ubuntu did the patch work for you?

---

### Post by Tom_Furniss on 2015-12-13
Hi Retna, I patched kernel version 4.3.0, the drm-intel-next branch.

---

### Post by elizabeth_b on 2016-03-31
Hi, was just about to order the same laptop, when I found this thread.  

I was going to install fedora rather than linux.  The latest version has kernel 4.4.6.  Have you tried that version, does it put all these problems in the past?  Thanks,

---

### Post by Tom_Furniss on 2016-04-01
Hi elizabeth_b

This problem seems to affect a subset of those laptops, and is independent of hardware specification, so you may be lucky or not.  I suspect a specific batch of the laptop screens are exhibiting anomalous behaviour, which the Linux driver isn't handling too well, so I would the problem will likely manifest across distributions.

My laptop graphics are now relatively stable, running a custom kernel with the patches from this thread: [https://bugs.freedesktop.org/show_bug.cgi?id=91393](https://bugs.freedesktop.org/show_bug.cgi?id=91393)

I haven't tried the very latest patches there, but it looks like they should be merged into the kernel over time.

---

