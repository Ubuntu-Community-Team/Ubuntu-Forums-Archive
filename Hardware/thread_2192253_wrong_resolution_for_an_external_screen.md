---
title: "wrong resolution for an external screen"
date: 2013-12-06
forum: Hardware
---

### Post by boletusatanas on 2013-12-06
Hello everybody,

I have a problem with an external screen 32" linked with HDMI.
I have the last version of UBUNTU, a DELL laptop, a Samsung 20" LCD (no problem with it) linked via VGA and a Thomson LED TV 32" linked via HDMI (with VGA was even worse).
The resolution on the 32" TV is not optimal, I guess, and I cannot find a way to change it. Ubuntu sees this TV as 26" instead of a 32" (as you may see from the below picture).
Is there any chance to increase that resolution?

Thank you in advance for your help.

Matteo
[IMG]http://s22.postimg.org/csxy9dk01/Screenshot_from_2013_12_07_02_04_31.png[/IMG]

---

### Post by boletusatanas on 2013-12-07
Maybe could be helpful the output of the xrandr:

```


boletusatanas@SpartanDell:~$ xrandr
Screen 0: minimum 320 x 200, current 3040 x 1401, maximum 32767 x 32767
LVDS1 connected (normal left inverted right x axis y axis)
   1366x768       60.0 +   40.0  
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 connected 1680x1050+1360+351 (normal left inverted right x axis y axis) 433mm x 271mm
   1680x1050      60.0*+
   1280x1024      75.0     60.0  
   1280x960       60.0  
   1152x864       75.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     60.0  
   720x400        70.1  
HDMI1 connected primary 1360x768+0+0 (normal left inverted right x axis y axis) 580mm x 320mm
   1360x768       60.0*+
   1920x1080      60.0     50.0     59.9     30.0     25.0     24.0     30.0     24.0  
   1920x1080i     60.1     60.1     50.0     60.0  
   1280x1024      75.0  
   1280x720       60.0     50.0     59.9  
   1440x576i      50.1  
   1024x768       75.1     60.0  
   1440x480i      60.1     60.1  
   800x600        75.0     60.3  
   720x576        50.0  
   720x480        60.0     59.9  
   640x480        60.0     59.9  
DP1 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)


```


and the log of Xorg

```


[    19.988] 
X.Org X Server 1.14.3
Release Date: 2013-09-12
[    19.988] X Protocol Version 11, Revision 0
[    19.988] Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
[    19.988] Current Operating System: Linux SpartanDell 3.11.0-14-generic #21-Ubuntu SMP Tue Nov 12 17:04:55 UTC 2013 x86_64
[    19.988] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.11.0-14-generic root=UUID=49323298-3430-4ff2-ae06-968f4171e9b0 ro quiet splash vt.handoff=7
[    19.988] Build Date: 15 October 2013  09:23:37AM
[    19.988] xorg-server 2:1.14.3-3ubuntu2 (For technical support please see http://www.ubuntu.com/support) 
[    19.988] Current version of pixman: 0.30.2
[    19.988]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    19.988] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    19.988] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Dec  7 11:00:44 2013
[    19.995] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    19.995] (==) No Layout section.  Using the first Screen section.
[    19.995] (==) No screen section available. Using defaults.
[    19.995] (**) |-->Screen "Default Screen Section" (0)
[    19.995] (**) |   |-->Monitor "<default monitor>"
[    19.995] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    19.995] (==) Automatically adding devices
[    19.995] (==) Automatically enabling devices
[    19.995] (==) Automatically adding GPU devices
[    19.995] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    19.995]     Entry deleted from font path.
[    19.995] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    19.995]     Entry deleted from font path.
[    19.995] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    19.995]     Entry deleted from font path.
[    19.995] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    19.995]     Entry deleted from font path.
[    19.995] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    19.995]     Entry deleted from font path.
[    19.995] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    19.995] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    19.995] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    19.995] (II) Loader magic: 0x7fef46832d20
[    19.995] (II) Module ABI versions:
[    19.995]     X.Org ANSI C Emulation: 0.4
[    19.995]     X.Org Video Driver: 14.1
[    19.995]     X.Org XInput driver : 19.1
[    19.995]     X.Org Server Extension : 7.0
[    19.995] (II) xfree86: Adding drm device (/dev/dri/card0)
[    19.996] (--) PCI:*(0:0:2:0) 8086:0116:1028:0510 rev 9, Mem @ 0xf6800000/4194304, 0xe0000000/268435456, I/O @ 0x0000f000/64
[    19.996] (II) Open ACPI successful (/var/run/acpid.socket)
[    19.996] Initializing built-in extension Generic Event Extension
[    19.996] Initializing built-in extension SHAPE
[    19.996] Initializing built-in extension MIT-SHM
[    19.996] Initializing built-in extension XInputExtension
[    19.996] Initializing built-in extension XTEST
[    19.996] Initializing built-in extension BIG-REQUESTS
[    19.996] Initializing built-in extension SYNC
[    19.997] Initializing built-in extension XKEYBOARD
[    19.997] Initializing built-in extension XC-MISC
[    19.997] Initializing built-in extension SECURITY
[    19.997] Initializing built-in extension XINERAMA
[    19.997] Initializing built-in extension XFIXES
[    19.997] Initializing built-in extension RENDER
[    19.997] Initializing built-in extension RANDR
[    19.997] Initializing built-in extension COMPOSITE
[    19.997] Initializing built-in extension DAMAGE
[    19.997] Initializing built-in extension MIT-SCREEN-SAVER
[    19.997] Initializing built-in extension DOUBLE-BUFFER
[    19.997] Initializing built-in extension RECORD
[    19.997] Initializing built-in extension DPMS
[    19.997] Initializing built-in extension X-Resource
[    19.997] Initializing built-in extension XVideo
[    19.997] Initializing built-in extension XVideo-MotionCompensation
[    19.997] Initializing built-in extension SELinux
[    19.997] Initializing built-in extension XFree86-VidModeExtension
[    19.997] Initializing built-in extension XFree86-DGA
[    19.997] Initializing built-in extension XFree86-DRI
[    19.997] Initializing built-in extension DRI2
[    19.997] (II) "glx" will be loaded by default.
[    19.997] (WW) "xmir" is not to be loaded by default. Skipping.
[    19.997] (II) LoadModule: "dri2"
[    19.997] (II) Module "dri2" already built-in
[    19.997] (II) LoadModule: "glamoregl"
[    20.140] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[    20.453] (II) Module glamoregl: vendor="X.Org Foundation"
[    20.453]     compiled for 1.14.3, module version = 0.5.1
[    20.453]     ABI class: X.Org ANSI C Emulation, version 0.4
[    20.453] (II) LoadModule: "glx"
[    20.453] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    20.453] (II) Module glx: vendor="X.Org Foundation"
[    20.453]     compiled for 1.14.3, module version = 1.0.0
[    20.453]     ABI class: X.Org Server Extension, version 7.0
[    20.453] (==) AIGLX enabled
[    20.453] Loading extension GLX
[    20.453] (==) Matched intel as autoconfigured driver 0
[    20.453] (==) Matched intel as autoconfigured driver 1
[    20.453] (==) Matched vesa as autoconfigured driver 2
[    20.453] (==) Matched modesetting as autoconfigured driver 3
[    20.453] (==) Matched fbdev as autoconfigured driver 4
[    20.453] (==) Assigned the driver to the xf86ConfigLayout
[    20.453] (II) LoadModule: "intel"
[    20.453] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    20.465] (II) Module intel: vendor="X.Org Foundation"
[    20.465]     compiled for 1.14.3, module version = 2.99.904
[    20.465]     Module class: X.Org Video Driver
[    20.465]     ABI class: X.Org Video Driver, version 14.1
[    20.465] (II) LoadModule: "vesa"
[    20.466] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    20.466] (II) Module vesa: vendor="X.Org Foundation"
[    20.466]     compiled for 1.14.1, module version = 2.3.2
[    20.466]     Module class: X.Org Video Driver
[    20.466]     ABI class: X.Org Video Driver, version 14.1
[    20.466] (II) LoadModule: "modesetting"
[    20.466] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    20.466] (II) Module modesetting: vendor="X.Org Foundation"
[    20.466]     compiled for 1.14.1, module version = 0.8.0
[    20.466]     Module class: X.Org Video Driver
[    20.466]     ABI class: X.Org Video Driver, version 14.1
[    20.466] (II) LoadModule: "fbdev"
[    20.466] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    20.466] (II) Module fbdev: vendor="X.Org Foundation"
[    20.466]     compiled for 1.14.1, module version = 0.4.3
[    20.466]     Module class: X.Org Video Driver
[    20.466]     ABI class: X.Org Video Driver, version 14.1
[    20.466] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43, HD Graphics,
    HD Graphics 2000, HD Graphics 3000, HD Graphics 2500,
    HD Graphics 4000, HD Graphics P4000, HD Graphics 4600,
    HD Graphics 5000, HD Graphics P4600/P4700, Iris(TM) Graphics 5100,
    HD Graphics 4400, HD Graphics 4200, Iris(TM) Pro Graphics 5200
[    20.466] (II) VESA: driver for VESA chipsets: vesa
[    20.466] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    20.466] (II) FBDEV: driver for framebuffer: fbdev
[    20.466] (++) using VT number 7

[    20.466] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.99.904-0ubuntu2 (Timo Aaltonen <tjaalton@ubuntu.com>)
[    20.467] (WW) Falling back to old probe method for vesa
[    20.467] (WW) Falling back to old probe method for modesetting
[    20.467] (WW) Falling back to old probe method for fbdev
[    20.467] (II) Loading sub module "fbdevhw"
[    20.467] (II) LoadModule: "fbdevhw"
[    20.467] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    20.467] (II) Module fbdevhw: vendor="X.Org Foundation"
[    20.467]     compiled for 1.14.3, module version = 0.0.2
[    20.467]     ABI class: X.Org Video Driver, version 14.1
[    20.467] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    20.467] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    20.467] (==) intel(0): RGB weight 888
[    20.467] (==) intel(0): Default visual is TrueColor
[    20.467] (--) intel(0): Integrated Graphics Chipset: Intel(R) HD Graphics 3000
[    20.467] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2, avx
[    20.467] (**) intel(0): Framebuffer tiled
[    20.467] (**) intel(0): Pixmaps tiled
[    20.467] (**) intel(0): "Tear free" disabled
[    20.467] (**) intel(0): Forcing per-crtc-pixmaps? no
[    20.467] (II) intel(0): Output LVDS1 has no monitor section
[    20.467] (--) intel(0): found backlight control interface acpi_video0 (type 'firmware')
[    20.468] (II) intel(0): Output VGA1 has no monitor section
[    20.468] (II) intel(0): Output HDMI1 has no monitor section
[    20.468] (II) intel(0): Output DP1 has no monitor section
[    20.468] (II) intel(0): Output VIRTUAL1 has no monitor section
[    20.468] (--) intel(0): Output VGA1 using initial mode 1680x1050 on pipe 0
[    20.468] (--) intel(0): Output HDMI1 using initial mode 1360x768 on pipe 1
[    20.468] (==) intel(0): DPI set to (96, 96)
[    20.468] (II) Loading sub module "dri2"
[    20.468] (II) LoadModule: "dri2"
[    20.468] (II) Module "dri2" already built-in
[    20.468] (II) UnloadModule: "vesa"
[    20.468] (II) Unloading vesa
[    20.468] (II) UnloadModule: "modesetting"
[    20.468] (II) Unloading modesetting
[    20.468] (II) UnloadModule: "fbdev"
[    20.468] (II) Unloading fbdev
[    20.468] (II) UnloadSubModule: "fbdevhw"
[    20.468] (II) Unloading fbdevhw
[    20.468] (==) Depth 24 pixmap format is 32 bpp
[    20.468] (II) intel(0): SNA initialized with Sandybridge (gen6, gt2) backend
[    20.468] (==) intel(0): Backing store disabled
[    20.468] (==) intel(0): Silken mouse enabled
[    20.468] (II) intel(0): HW Cursor enabled
[    20.468] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    20.468] (==) intel(0): DPMS enabled
[    20.468] (II) intel(0): [DRI2] Setup complete
[    20.468] (II) intel(0): [DRI2]   DRI driver: i965
[    20.468] (II) intel(0): direct rendering: DRI2 Enabled
[    20.468] (==) intel(0): hotplug detection: "enabled"
[    20.468] (--) RandR disabled
[    20.472] (II) SELinux: Disabled on system
[    20.537] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    20.537] (II) AIGLX: enabled GLX_INTEL_swap_event
[    20.537] (II) AIGLX: enabled GLX_ARB_create_context
[    20.537] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    20.537] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    20.537] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    20.537] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    20.537] (II) AIGLX: Loaded and initialized i965
[    20.537] (II) GLX: Initialized DRI2 GL provider for screen 0
[    20.539] (II) intel(0): switch to mode 1680x1050@60.0 on pipe 0 using VGA1, position (0, 0), rotation normal
[    20.560] (II) intel(0): switch to mode 1360x768@60.0 on pipe 1 using HDMI1, position (0, 0), rotation normal
[    20.568] (II) intel(0): Setting screen physical size to 444 x 277
[    20.574] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    20.576] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    20.576] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    20.576] (II) LoadModule: "evdev"
[    20.576] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    20.582] (II) Module evdev: vendor="X.Org Foundation"
[    20.582]     compiled for 1.14.1, module version = 2.7.3
[    20.582]     Module class: X.Org XInput Driver
[    20.582]     ABI class: X.Org XInput driver, version 19.1
[    20.582] (II) Using input driver 'evdev' for 'Power Button'
[    20.582] (**) Power Button: always reports core events
[    20.582] (**) evdev: Power Button: Device: "/dev/input/event3"
[    20.582] (--) evdev: Power Button: Vendor 0 Product 0x1
[    20.582] (--) evdev: Power Button: Found keys
[    20.582] (II) evdev: Power Button: Configuring as keyboard
[    20.582] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    20.582] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    20.582] (**) Option "xkb_rules" "evdev"
[    20.582] (**) Option "xkb_model" "pc105"
[    20.582] (**) Option "xkb_layout" "us"
[    20.582] (II) config/udev: Adding input device Video Bus (/dev/input/event11)
[    20.582] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    20.582] (II) Using input driver 'evdev' for 'Video Bus'
[    20.582] (**) Video Bus: always reports core events
[    20.583] (**) evdev: Video Bus: Device: "/dev/input/event11"
[    20.583] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    20.583] (--) evdev: Video Bus: Found keys
[    20.583] (II) evdev: Video Bus: Configuring as keyboard
[    20.583] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input11/event11"
[    20.583] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    20.583] (**) Option "xkb_rules" "evdev"
[    20.583] (**) Option "xkb_model" "pc105"
[    20.583] (**) Option "xkb_layout" "us"
[    20.583] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    20.583] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    20.583] (II) Using input driver 'evdev' for 'Power Button'
[    20.583] (**) Power Button: always reports core events
[    20.583] (**) evdev: Power Button: Device: "/dev/input/event1"
[    20.583] (--) evdev: Power Button: Vendor 0 Product 0x1
[    20.583] (--) evdev: Power Button: Found keys
[    20.583] (II) evdev: Power Button: Configuring as keyboard
[    20.583] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[    20.583] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    20.583] (**) Option "xkb_rules" "evdev"
[    20.583] (**) Option "xkb_model" "pc105"
[    20.583] (**) Option "xkb_layout" "us"
[    20.583] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    20.583] (II) No input driver specified, ignoring this device.
[    20.583] (II) This device may have been added with another device file.
[    20.583] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    20.583] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    20.583] (II) Using input driver 'evdev' for 'Sleep Button'
[    20.583] (**) Sleep Button: always reports core events
[    20.583] (**) evdev: Sleep Button: Device: "/dev/input/event2"
[    20.584] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    20.584] (--) evdev: Sleep Button: Found keys
[    20.584] (II) evdev: Sleep Button: Configuring as keyboard
[    20.584] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2/event2"
[    20.584] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[    20.584] (**) Option "xkb_rules" "evdev"
[    20.584] (**) Option "xkb_model" "pc105"
[    20.584] (**) Option "xkb_layout" "us"
[    20.584] (II) config/udev: Adding drm device (/dev/dri/card0)
[    20.584] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    20.584] (II) config/udev: Adding input device Laptop_Integrated_Webcam_HD (/dev/input/event9)
[    20.584] (**) Laptop_Integrated_Webcam_HD: Applying InputClass "evdev keyboard catchall"
[    20.584] (II) Using input driver 'evdev' for 'Laptop_Integrated_Webcam_HD'
[    20.584] (**) Laptop_Integrated_Webcam_HD: always reports core events
[    20.584] (**) evdev: Laptop_Integrated_Webcam_HD: Device: "/dev/input/event9"
[    20.584] (--) evdev: Laptop_Integrated_Webcam_HD: Vendor 0x1bcf Product 0x2880
[    20.584] (--) evdev: Laptop_Integrated_Webcam_HD: Found keys
[    20.584] (II) evdev: Laptop_Integrated_Webcam_HD: Configuring as keyboard
[    20.584] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.0/input/input9/event9"
[    20.584] (II) XINPUT: Adding extended input device "Laptop_Integrated_Webcam_HD" (type: KEYBOARD, id 10)
[    20.584] (**) Option "xkb_rules" "evdev"
[    20.584] (**) Option "xkb_model" "pc105"
[    20.584] (**) Option "xkb_layout" "us"
[    20.584] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event12)
[    20.584] (II) No input driver specified, ignoring this device.
[    20.584] (II) This device may have been added with another device file.
[    20.585] (II) config/udev: Adding input device RAPOO RAPOO 2.4G Wireless Device (/dev/input/event5)
[    20.585] (**) RAPOO RAPOO 2.4G Wireless Device: Applying InputClass "evdev keyboard catchall"
[    20.585] (II) Using input driver 'evdev' for 'RAPOO RAPOO 2.4G Wireless Device'
[    20.585] (**) RAPOO RAPOO 2.4G Wireless Device: always reports core events
[    20.585] (**) evdev: RAPOO RAPOO 2.4G Wireless Device: Device: "/dev/input/event5"
[    20.585] (--) evdev: RAPOO RAPOO 2.4G Wireless Device: Vendor 0x24ae Product 0x2000
[    20.585] (--) evdev: RAPOO RAPOO 2.4G Wireless Device: Found keys
[    20.585] (II) evdev: RAPOO RAPOO 2.4G Wireless Device: Configuring as keyboard
[    20.585] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2.2/2-1.2.2:1.0/input/input5/event5"
[    20.585] (II) XINPUT: Adding extended input device "RAPOO RAPOO 2.4G Wireless Device" (type: KEYBOARD, id 11)
[    20.585] (**) Option "xkb_rules" "evdev"
[    20.585] (**) Option "xkb_model" "pc105"
[    20.585] (**) Option "xkb_layout" "us"
[    20.585] (II) config/udev: Adding input device RAPOO RAPOO 2.4G Wireless Device (/dev/input/event6)
[    20.585] (**) RAPOO RAPOO 2.4G Wireless Device: Applying InputClass "evdev pointer catchall"
[    20.585] (**) RAPOO RAPOO 2.4G Wireless Device: Applying InputClass "evdev keyboard catchall"
[    20.585] (II) Using input driver 'evdev' for 'RAPOO RAPOO 2.4G Wireless Device'
[    20.585] (**) RAPOO RAPOO 2.4G Wireless Device: always reports core events
[    20.585] (**) evdev: RAPOO RAPOO 2.4G Wireless Device: Device: "/dev/input/event6"
[    20.585] (--) evdev: RAPOO RAPOO 2.4G Wireless Device: Vendor 0x24ae Product 0x2000
[    20.585] (--) evdev: RAPOO RAPOO 2.4G Wireless Device: Found 9 mouse buttons
[    20.585] (--) evdev: RAPOO RAPOO 2.4G Wireless Device: Found scroll wheel(s)
[    20.585] (--) evdev: RAPOO RAPOO 2.4G Wireless Device: Found relative axes
[    20.585] (--) evdev: RAPOO RAPOO 2.4G Wireless Device: Found x and y relative axes
[    20.585] (--) evdev: RAPOO RAPOO 2.4G Wireless Device: Found absolute axes
[    20.585] (II) evdev: RAPOO RAPOO 2.4G Wireless Device: Forcing absolute x/y axes to exist.
[    20.585] (--) evdev: RAPOO RAPOO 2.4G Wireless Device: Found keys
[    20.585] (II) evdev: RAPOO RAPOO 2.4G Wireless Device: Configuring as mouse
[    20.585] (II) evdev: RAPOO RAPOO 2.4G Wireless Device: Configuring as keyboard
[    20.585] (II) evdev: RAPOO RAPOO 2.4G Wireless Device: Adding scrollwheel support
[    20.585] (**) evdev: RAPOO RAPOO 2.4G Wireless Device: YAxisMapping: buttons 4 and 5
[    20.585] (**) evdev: RAPOO RAPOO 2.4G Wireless Device: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    20.585] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2.2/2-1.2.2:1.1/input/input6/event6"
[    20.585] (II) XINPUT: Adding extended input device "RAPOO RAPOO 2.4G Wireless Device" (type: KEYBOARD, id 12)
[    20.585] (**) Option "xkb_rules" "evdev"
[    20.585] (**) Option "xkb_model" "pc105"
[    20.585] (**) Option "xkb_layout" "us"
[    20.585] (II) evdev: RAPOO RAPOO 2.4G Wireless Device: initialized for relative axes.
[    20.585] (WW) evdev: RAPOO RAPOO 2.4G Wireless Device: ignoring absolute axes.
[    20.586] (**) RAPOO RAPOO 2.4G Wireless Device: (accel) keeping acceleration scheme 1
[    20.586] (**) RAPOO RAPOO 2.4G Wireless Device: (accel) acceleration profile 0
[    20.586] (**) RAPOO RAPOO 2.4G Wireless Device: (accel) acceleration factor: 2.000
[    20.586] (**) RAPOO RAPOO 2.4G Wireless Device: (accel) acceleration threshold: 4
[    20.586] (II) config/udev: Adding input device RAPOO RAPOO 2.4G Wireless Device (/dev/input/mouse0)
[    20.586] (II) No input driver specified, ignoring this device.
[    20.586] (II) This device may have been added with another device file.
[    20.586] (II) config/udev: Adding input device CHESEN PS2 to USB Converter (/dev/input/event7)
[    20.586] (**) CHESEN PS2 to USB Converter: Applying InputClass "evdev keyboard catchall"
[    20.586] (II) Using input driver 'evdev' for 'CHESEN PS2 to USB Converter'
[    20.586] (**) CHESEN PS2 to USB Converter: always reports core events
[    20.586] (**) evdev: CHESEN PS2 to USB Converter: Device: "/dev/input/event7"
[    20.586] (--) evdev: CHESEN PS2 to USB Converter: Vendor 0xa81 Product 0x205
[    20.586] (--) evdev: CHESEN PS2 to USB Converter: Found keys
[    20.586] (II) evdev: CHESEN PS2 to USB Converter: Configuring as keyboard
[    20.586] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2.4/2-1.2.4:1.0/input/input7/event7"
[    20.586] (II) XINPUT: Adding extended input device "CHESEN PS2 to USB Converter" (type: KEYBOARD, id 13)
[    20.586] (**) Option "xkb_rules" "evdev"
[    20.586] (**) Option "xkb_model" "pc105"
[    20.586] (**) Option "xkb_layout" "us"
[    20.586] (II) config/udev: Adding input device CHESEN PS2 to USB Converter (/dev/input/event8)
[    20.586] (**) CHESEN PS2 to USB Converter: Applying InputClass "evdev pointer catchall"
[    20.586] (**) CHESEN PS2 to USB Converter: Applying InputClass "evdev keyboard catchall"
[    20.586] (II) Using input driver 'evdev' for 'CHESEN PS2 to USB Converter'
[    20.586] (**) CHESEN PS2 to USB Converter: always reports core events
[    20.586] (**) evdev: CHESEN PS2 to USB Converter: Device: "/dev/input/event8"
[    20.586] (--) evdev: CHESEN PS2 to USB Converter: Vendor 0xa81 Product 0x205
[    20.586] (--) evdev: CHESEN PS2 to USB Converter: Found 9 mouse buttons
[    20.586] (--) evdev: CHESEN PS2 to USB Converter: Found scroll wheel(s)
[    20.586] (--) evdev: CHESEN PS2 to USB Converter: Found relative axes
[    20.586] (--) evdev: CHESEN PS2 to USB Converter: Found x and y relative axes
[    20.586] (--) evdev: CHESEN PS2 to USB Converter: Found keys
[    20.586] (II) evdev: CHESEN PS2 to USB Converter: Configuring as mouse
[    20.587] (II) evdev: CHESEN PS2 to USB Converter: Configuring as keyboard
[    20.587] (II) evdev: CHESEN PS2 to USB Converter: Adding scrollwheel support
[    20.587] (**) evdev: CHESEN PS2 to USB Converter: YAxisMapping: buttons 4 and 5
[    20.587] (**) evdev: CHESEN PS2 to USB Converter: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    20.587] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2.4/2-1.2.4:1.1/input/input8/event8"
[    20.587] (II) XINPUT: Adding extended input device "CHESEN PS2 to USB Converter" (type: KEYBOARD, id 14)
[    20.587] (**) Option "xkb_rules" "evdev"
[    20.587] (**) Option "xkb_model" "pc105"
[    20.587] (**) Option "xkb_layout" "us"
[    20.587] (II) evdev: CHESEN PS2 to USB Converter: initialized for relative axes.
[    20.587] (**) CHESEN PS2 to USB Converter: (accel) keeping acceleration scheme 1
[    20.587] (**) CHESEN PS2 to USB Converter: (accel) acceleration profile 0
[    20.587] (**) CHESEN PS2 to USB Converter: (accel) acceleration factor: 2.000
[    20.587] (**) CHESEN PS2 to USB Converter: (accel) acceleration threshold: 4
[    20.587] (II) config/udev: Adding input device CHESEN PS2 to USB Converter (/dev/input/mouse1)
[    20.587] (II) No input driver specified, ignoring this device.
[    20.587] (II) This device may have been added with another device file.
[    20.587] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    20.587] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    20.587] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    20.587] (**) AT Translated Set 2 keyboard: always reports core events
[    20.587] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    20.587] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    20.587] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    20.587] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    20.587] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    20.587] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 15)
[    20.587] (**) Option "xkb_rules" "evdev"
[    20.587] (**) Option "xkb_model" "pc105"
[    20.587] (**) Option "xkb_layout" "us"
[    20.588] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event13)
[    20.588] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    20.588] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    20.588] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[    20.588] (II) LoadModule: "synaptics"
[    20.588] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    20.588] (II) Module synaptics: vendor="X.Org Foundation"
[    20.588]     compiled for 1.14.2, module version = 1.7.1
[    20.588]     Module class: X.Org XInput Driver
[    20.588]     ABI class: X.Org XInput driver, version 19.1
[    20.588] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    20.588] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    20.588] (**) Option "Device" "/dev/input/event13"
[    20.608] (II) synaptics: SynPS/2 Synaptics TouchPad: ignoring touch events for semi-multitouch device
[    20.608] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5792 (res 58)
[    20.608] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4970 (res 102)
[    20.608] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    20.608] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    20.608] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    20.608] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    20.608] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    20.608] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    20.620] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input13/event13"
[    20.620] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 16)
[    20.620] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    20.620] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[    20.620] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.036
[    20.620] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    20.620] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    20.620] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    20.620] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    20.620] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    20.620] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse2)
[    20.620] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    20.621] (II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event10)
[    20.621] (**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    20.621] (II) Using input driver 'evdev' for 'Dell WMI hotkeys'
[    20.621] (**) Dell WMI hotkeys: always reports core events
[    20.621] (**) evdev: Dell WMI hotkeys: Device: "/dev/input/event10"
[    20.622] (--) evdev: Dell WMI hotkeys: Vendor 0 Product 0
[    20.622] (--) evdev: Dell WMI hotkeys: Found keys
[    20.622] (II) evdev: Dell WMI hotkeys: Configuring as keyboard
[    20.622] (**) Option "config_info" "udev:/sys/devices/virtual/input/input10/event10"
[    20.622] (II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD, id 17)
[    20.622] (**) Option "xkb_rules" "evdev"
[    20.622] (**) Option "xkb_model" "pc105"
[    20.622] (**) Option "xkb_layout" "us"
[    23.088] (II) intel(0): EDID vendor "TCL", prod id 0
[    23.088] (II) intel(0): Using EDID range info for horizontal sync
[    23.088] (II) intel(0): Using EDID range info for vertical refresh
[    23.088] (II) intel(0): Printing DDC gathered Modelines:
[    23.088] (II) intel(0): Modeline "1360x768"x0.0   85.50  1360 1424 1536 1792  768 771 777 795 -hsync -vsync (47.7 kHz eP)
[    23.088] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    23.088] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz e)
[    23.088] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace -hsync -vsync (33.8 kHz e)
[    23.088] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[    23.088] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    23.088] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    23.088] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    23.088] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    23.088] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    23.088] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    23.088] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[    23.088] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[    23.088] (II) intel(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz e)
[    23.088] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[    23.088] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[    23.088] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    23.088] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz e)
[    23.088] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[    23.088] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (28.1 kHz e)
[    23.088] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (33.8 kHz e)
[    23.088] (II) intel(0): Modeline "2880x480"x0.0  108.00  2880 2944 3192 3432  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    23.556] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    23.633] (II) intel(0): EDID vendor "SAM", prod id 541
[    23.633] (II) intel(0):     EDID quirk: Use +hsync +vsync for detailed timing.
[    23.633] (II) intel(0): Using hsync ranges from config file
[    23.633] (II) intel(0): Using vrefresh ranges from config file
[    23.633] (II) intel(0): Printing DDC gathered Modelines:
[    23.634] (II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 +hsync +vsync (65.3 kHz eP)
[    23.634] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    23.634] (II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    23.634] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    23.634] (II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    23.634] (II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    23.634] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    23.634] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    23.634] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    23.634] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    23.634] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    23.634] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    23.634] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    23.634] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    23.634] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    23.634] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    23.634] (II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[    23.634] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    23.634] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    23.773] (II) intel(0): resizing framebuffer to 3040x1401
[    23.773] (II) intel(0): switch to mode 1680x1050@60.0 on pipe 0 using VGA1, position (0, 0), rotation normal
[    23.796] (II) intel(0): switch to mode 1360x768@60.0 on pipe 1 using HDMI1, position (0, 0), rotation normal
[    23.804] (II) intel(0): switch to mode 1680x1050@60.0 on pipe 0 using VGA1, position (1360, 351), rotation normal
[    24.083] (II) intel(0): EDID vendor "SAM", prod id 541
[    24.083] (II) intel(0):     EDID quirk: Use +hsync +vsync for detailed timing.
[    24.083] (II) intel(0): Using hsync ranges from config file
[    24.083] (II) intel(0): Using vrefresh ranges from config file
[    24.083] (II) intel(0): Printing DDC gathered Modelines:
[    24.083] (II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 +hsync +vsync (65.3 kHz eP)
[    24.083] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    24.083] (II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    24.083] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    24.083] (II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    24.083] (II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    24.083] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    24.083] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    24.083] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    24.083] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    24.083] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    24.083] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    24.083] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    24.083] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    24.083] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    24.083] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    24.083] (II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[    24.083] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    24.083] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    24.579] (II) XKB: reuse xkmfile /var/lib/xkb/server-B984870A7ABF38136B6898D1AC3A1E616A151216.xkm
[    24.588] (II) XKB: reuse xkmfile /var/lib/xkb/server-B984870A7ABF38136B6898D1AC3A1E616A151216.xkm
[    25.073] (II) intel(0): EDID vendor "SAM", prod id 541
[    25.073] (II) intel(0):     EDID quirk: Use +hsync +vsync for detailed timing.
[    25.073] (II) intel(0): Using hsync ranges from config file
[    25.073] (II) intel(0): Using vrefresh ranges from config file
[    25.073] (II) intel(0): Printing DDC gathered Modelines:
[    25.073] (II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 +hsync +vsync (65.3 kHz eP)
[    25.073] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    25.073] (II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    25.073] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    25.073] (II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    25.073] (II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    25.073] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    25.073] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    25.073] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    25.073] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    25.073] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    25.073] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    25.073] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    25.073] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    25.073] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    25.073] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    25.074] (II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[    25.074] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    25.074] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    25.219] (II) intel(0): EDID vendor "SAM", prod id 541
[    25.219] (II) intel(0):     EDID quirk: Use +hsync +vsync for detailed timing.
[    25.219] (II) intel(0): Using hsync ranges from config file
[    25.219] (II) intel(0): Using vrefresh ranges from config file
[    25.219] (II) intel(0): Printing DDC gathered Modelines:
[    25.219] (II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 +hsync +vsync (65.3 kHz eP)
[    25.219] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    25.219] (II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    25.219] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    25.219] (II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    25.219] (II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    25.219] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    25.219] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    25.219] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    25.219] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    25.219] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    25.219] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    25.219] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    25.219] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    25.219] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    25.219] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    25.219] (II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[    25.219] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    25.219] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    28.814] (II) XKB: reuse xkmfile /var/lib/xkb/server-D05A2352B56AE2614B37F68576A62E5406D89CBE.xkm
[    45.161] (II) intel(0): EDID vendor "SAM", prod id 541
[    45.161] (II) intel(0):     EDID quirk: Use +hsync +vsync for detailed timing.
[    45.161] (II) intel(0): Using hsync ranges from config file
[    45.161] (II) intel(0): Using vrefresh ranges from config file
[    45.161] (II) intel(0): Printing DDC gathered Modelines:
[    45.161] (II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 +hsync +vsync (65.3 kHz eP)
[    45.161] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    45.161] (II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    45.161] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    45.161] (II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    45.161] (II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    45.161] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    45.161] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    45.161] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    45.161] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    45.161] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    45.161] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    45.161] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    45.161] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    45.161] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    45.161] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    45.161] (II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[    45.161] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    45.161] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[   266.480] (II) intel(0): EDID vendor "SAM", prod id 541
[   266.480] (II) intel(0):     EDID quirk: Use +hsync +vsync for detailed timing.
[   266.480] (II) intel(0): Using hsync ranges from config file
[   266.480] (II) intel(0): Using vrefresh ranges from config file
[   266.480] (II) intel(0): Printing DDC gathered Modelines:
[   266.480] (II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 +hsync +vsync (65.3 kHz eP)
[   266.480] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   266.480] (II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[   266.480] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   266.480] (II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[   266.480] (II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[   266.480] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   266.480] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   266.480] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   266.480] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   266.480] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[   266.480] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   266.480] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[   266.480] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   266.480] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[   266.480] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   266.480] (II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[   266.480] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   266.480] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[   266.571] (II) intel(0): EDID vendor "SAM", prod id 541
[   266.571] (II) intel(0):     EDID quirk: Use +hsync +vsync for detailed timing.
[   266.571] (II) intel(0): Using hsync ranges from config file
[   266.571] (II) intel(0): Using vrefresh ranges from config file
[   266.571] (II) intel(0): Printing DDC gathered Modelines:
[   266.571] (II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 +hsync +vsync (65.3 kHz eP)
[   266.571] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   266.571] (II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[   266.571] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   266.571] (II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[   266.571] (II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[   266.571] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   266.571] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   266.571] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   266.571] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   266.571] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[   266.571] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   266.571] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[   266.571] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   266.571] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[   266.571] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   266.571] (II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[   266.571] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   266.571] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[  1190.588] (II) intel(0): EDID vendor "SAM", prod id 541
[  1190.588] (II) intel(0):     EDID quirk: Use +hsync +vsync for detailed timing.
[  1190.588] (II) intel(0): Using hsync ranges from config file
[  1190.588] (II) intel(0): Using vrefresh ranges from config file
[  1190.588] (II) intel(0): Printing DDC gathered Modelines:
[  1190.588] (II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 +hsync +vsync (65.3 kHz eP)
[  1190.588] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[  1190.588] (II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[  1190.588] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[  1190.588] (II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[  1190.588] (II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[  1190.588] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[  1190.588] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[  1190.588] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[  1190.588] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[  1190.588] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[  1190.588] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[  1190.588] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[  1190.588] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[  1190.588] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[  1190.588] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[  1190.588] (II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[  1190.589] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[  1190.589] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[  1394.692] (II) intel(0): EDID vendor "SAM", prod id 541
[  1394.693] (II) intel(0):     EDID quirk: Use +hsync +vsync for detailed timing.
[  1394.693] (II) intel(0): Using hsync ranges from config file
[  1394.693] (II) intel(0): Using vrefresh ranges from config file
[  1394.693] (II) intel(0): Printing DDC gathered Modelines:
[  1394.693] (II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 +hsync +vsync (65.3 kHz eP)
[  1394.693] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[  1394.693] (II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[  1394.693] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[  1394.693] (II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[  1394.693] (II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[  1394.693] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[  1394.693] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[  1394.693] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[  1394.693] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[  1394.693] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[  1394.693] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[  1394.693] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[  1394.693] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[  1394.693] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[  1394.693] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[  1394.693] (II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[  1394.693] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[  1394.693] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[ 12006.656] (II) intel(0): EDID vendor "SAM", prod id 541
[ 12006.656] (II) intel(0):     EDID quirk: Use +hsync +vsync for detailed timing.
[ 12006.656] (II) intel(0): Using hsync ranges from config file
[ 12006.656] (II) intel(0): Using vrefresh ranges from config file
[ 12006.656] (II) intel(0): Printing DDC gathered Modelines:
[ 12006.656] (II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 +hsync +vsync (65.3 kHz eP)
[ 12006.656] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[ 12006.656] (II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[ 12006.656] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[ 12006.656] (II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[ 12006.656] (II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[ 12006.656] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[ 12006.656] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[ 12006.656] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[ 12006.656] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[ 12006.656] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[ 12006.656] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[ 12006.656] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[ 12006.656] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[ 12006.656] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[ 12006.656] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[ 12006.656] (II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[ 12006.656] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[ 12006.656] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)


```

---

