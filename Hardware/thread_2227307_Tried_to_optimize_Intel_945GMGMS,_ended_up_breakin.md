---
title: "Tried to optimize Intel 945GM/GMS, ended up breaking lightdm login"
date: 2014-06-01
forum: Hardware
---

### Post by kjetil-fleten on 2014-06-01
On a laptop with Intel 945GM/GMS and 14.04 64-bit, I had some problems launching a game that should work fine. I believe the graphics driver was not proprly configured. I have tried to install xserver-xorg-video-intel. lshw -c video shows i915 in use, but system info shows "Gallium 0.4 on llvmpipe (LLVM 3.4, 128 bits)". I can no longer log in using lightdm, but have to press Ctrl+Alt+F1, and start with startx.

I have tried to purge lightdm, and reinstall, and also tried sudo dpkg-reconfigure xserver-xorg. So fare no success. Anyone who knows how to make this work properly ?

---

### Post by Yellow Pasque on 2014-06-01
Post /var/log/Xorg.0.log (use code tags).

---

### Post by kjetil-fleten on 2014-06-01
```
hostname@hostname-HP-Compaq-nc6400-EH522AV:~$ cat /var/log/Xorg.0.log
[    32.059] X.Org X Server 1.15.1  Release Date: 2014-04-13
[    32.059] X Protocol Version 11, Revision 0
[    32.059] Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
[    32.059] Current Operating System: Linux marius-HP-Compaq-nc6400-EH522AV 3.13.0-24-generic #47-Ubuntu SMP Fri May 2 23:30:00 UTC 2014 x86_64
[    32.060] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic root=UUID=a8f75d80-8658-453e-ac46-e7551262645b ro quiet splash vt.handoff=7
[    32.060] Build Date: 16 April 2014  01:36:29PM
[    32.060] xorg-server 2:1.15.1-0ubuntu2 (For technical support please see http://www.ubuntu.com/support) 
[    32.060] Current version of pixman: 0.30.2
[    32.060]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    32.060] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    32.060] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Jun  1 19:05:48 2014
[    32.060] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    32.061] (==) No Layout section.  Using the first Screen section.
[    32.061] (==) No screen section available. Using defaults.
[    32.061] (**) |-->Screen "Default Screen Section" (0)
[    32.061] (**) |   |-->Monitor "<default monitor>"
[    32.061] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    32.061] (==) Automatically adding devices
[    32.061] (==) Automatically enabling devices
[    32.061] (==) Automatically adding GPU devices
[    32.061] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    32.061]     Entry deleted from font path.
[    32.061] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    32.061]     Entry deleted from font path.
[    32.061] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    32.061]     Entry deleted from font path.
[    32.061] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    32.061]     Entry deleted from font path.
[    32.061] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    32.061]     Entry deleted from font path.
[    32.061] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    32.061] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    32.061] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    32.061] (II) Loader magic: 0x7fa1fc246d60
[    32.061] (II) Module ABI versions:
[    32.061]     X.Org ANSI C Emulation: 0.4
[    32.061]     X.Org Video Driver: 15.0
[    32.061]     X.Org XInput driver : 20.0
[    32.061]     X.Org Server Extension : 8.0
[    32.062] (II) xfree86: Adding drm device (/dev/dri/card0)
[    32.064] (--) PCI:*(0:0:2:0) 8086:27a2:103c:30ad rev 3, Mem @ 0xf4600000/524288, 0xe0000000/268435456, 0xf4680000/262144, I/O @ 0x00004000/8
[    32.065] (--) PCI: (0:0:2:1) 8086:27a6:103c:30ad rev 3, Mem @ 0xf4700000/524288
[    32.065] Initializing built-in extension Generic Event Extension
[    32.065] Initializing built-in extension SHAPE
[    32.065] Initializing built-in extension MIT-SHM
[    32.065] Initializing built-in extension XInputExtension
[    32.065] Initializing built-in extension XTEST
[    32.065] Initializing built-in extension BIG-REQUESTS
[    32.065] Initializing built-in extension SYNC
[    32.065] Initializing built-in extension XKEYBOARD
[    32.065] Initializing built-in extension XC-MISC
[    32.065] Initializing built-in extension SECURITY
[    32.065] Initializing built-in extension XINERAMA
[    32.065] Initializing built-in extension XFIXES
[    32.065] Initializing built-in extension RENDER
[    32.065] Initializing built-in extension RANDR
[    32.065] Initializing built-in extension COMPOSITE
[    32.065] Initializing built-in extension DAMAGE
[    32.065] Initializing built-in extension MIT-SCREEN-SAVER
[    32.065] Initializing built-in extension DOUBLE-BUFFER
[    32.065] Initializing built-in extension RECORD
[    32.065] Initializing built-in extension DPMS
[    32.065] Initializing built-in extension Present
[    32.065] Initializing built-in extension DRI3
[    32.065] Initializing built-in extension X-Resource
[    32.065] Initializing built-in extension XVideo
[    32.065] Initializing built-in extension XVideo-MotionCompensation
[    32.065] Initializing built-in extension SELinux
[    32.065] Initializing built-in extension XFree86-VidModeExtension
[    32.065] Initializing built-in extension XFree86-DGA
[    32.065] Initializing built-in extension XFree86-DRI
[    32.065] Initializing built-in extension DRI2
[    32.065] (II) LoadModule: "glx"
[    32.066] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    32.068] (II) Module glx: vendor="X.Org Foundation"
[    32.068]     compiled for 1.15.1, module version = 1.0.0
[    32.068]     ABI class: X.Org Server Extension, version 8.0
[    32.068] (==) AIGLX enabled
[    32.068] Loading extension GLX
[    32.068] (==) Matched intel as autoconfigured driver 0
[    32.068] (==) Matched intel as autoconfigured driver 1
[    32.068] (==) Matched modesetting as autoconfigured driver 2
[    32.068] (==) Matched fbdev as autoconfigured driver 3
[    32.068] (==) Matched vesa as autoconfigured driver 4
[    32.068] (==) Assigned the driver to the xf86ConfigLayout
[    32.068] (II) LoadModule: "intel"
[    32.068] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    32.069] (II) Module intel: vendor="X.Org Foundation"
[    32.069]     compiled for 1.15.0, module version = 2.99.910
[    32.069]     Module class: X.Org Video Driver
[    32.069]     ABI class: X.Org Video Driver, version 15.0
[    32.069] (II) LoadModule: "modesetting"
[    32.069] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    32.069] (II) Module modesetting: vendor="X.Org Foundation"
[    32.069]     compiled for 1.15.0, module version = 0.8.1
[    32.069]     Module class: X.Org Video Driver
[    32.069]     ABI class: X.Org Video Driver, version 15.0
[    32.069] (II) LoadModule: "fbdev"
[    32.070] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    32.070] (II) Module fbdev: vendor="X.Org Foundation"
[    32.070]     compiled for 1.15.0, module version = 0.4.4
[    32.070]     Module class: X.Org Video Driver
[    32.070]     ABI class: X.Org Video Driver, version 15.0
[    32.070] (II) LoadModule: "vesa"
[    32.070] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    32.070] (II) Module vesa: vendor="X.Org Foundation"
[    32.070]     compiled for 1.15.0, module version = 2.3.3
[    32.070]     Module class: X.Org Video Driver
[    32.070]     ABI class: X.Org Video Driver, version 15.0
[    32.070] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[    32.071] (II) intel: Driver for Intel(R) HD Graphics: 2000-5000
[    32.071] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100
[    32.071] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200
[    32.071] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    32.071] (II) FBDEV: driver for framebuffer: fbdev
[    32.071] (II) VESA: driver for VESA chipsets: vesa
[    32.071] (++) using VT number 7

[    32.071] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.99.910-0ubuntu1 (Timo Aaltonen <tjaalton@ubuntu.com>)
[    32.072] (WW) Falling back to old probe method for modesetting
[    32.072] (WW) Falling back to old probe method for fbdev
[    32.072] (II) Loading sub module "fbdevhw"
[    32.072] (II) LoadModule: "fbdevhw"
[    32.072] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    32.072] (II) Module fbdevhw: vendor="X.Org Foundation"
[    32.072]     compiled for 1.15.1, module version = 0.0.2
[    32.073]     ABI class: X.Org Video Driver, version 15.0
[    32.073] (WW) Falling back to old probe method for vesa
[    32.073] (--) intel(0): Integrated Graphics Chipset: Intel(R) 945GM
[    32.073] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3
[    32.073] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    32.073] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    32.073] (==) intel(0): RGB weight 888
[    32.073] (==) intel(0): Default visual is TrueColor
[    32.074] (**) intel(0): Framebuffer tiled
[    32.074] (**) intel(0): Pixmaps tiled
[    32.074] (**) intel(0): "Tear free" disabled
[    32.074] (**) intel(0): Forcing per-crtc-pixmaps? no
[    32.074] (II) intel(0): Output LVDS1 has no monitor section
[    32.074] (--) intel(0): found backlight control interface acpi_video0 (type 'firmware')
[    32.074] (II) intel(0): Output VGA1 has no monitor section
[    32.074] (II) intel(0): Output DVI1 has no monitor section
[    32.074] (II) intel(0): Output TV1 has no monitor section
[    32.074] (II) intel(0): Output VIRTUAL1 has no monitor section
[    32.074] (--) intel(0): Output LVDS1 using initial mode 1280x800 on pipe 1
[    32.075] (==) intel(0): DPI set to (96, 96)
[    32.075] (II) Loading sub module "dri2"
[    32.075] (II) LoadModule: "dri2"
[    32.075] (II) Module "dri2" already built-in
[    32.075] (II) UnloadModule: "modesetting"
[    32.075] (II) Unloading modesetting
[    32.075] (II) UnloadModule: "fbdev"
[    32.075] (II) Unloading fbdev
[    32.075] (II) UnloadSubModule: "fbdevhw"
[    32.075] (II) Unloading fbdevhw
[    32.075] (II) UnloadModule: "vesa"
[    32.075] (II) Unloading vesa
[    32.075] (==) Depth 24 pixmap format is 32 bpp
[    32.075] (II) intel(0): SNA initialized with Alviso (gen3) backend
[    32.075] (==) intel(0): Backing store enabled
[    32.075] (==) intel(0): Silken mouse enabled
[    32.075] (II) intel(0): HW Cursor enabled
[    32.076] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    32.076] (==) intel(0): DPMS enabled
[    32.076] (II) intel(0): [XvMC] i915_xvmc driver initialized.
[    32.076] (II) intel(0): [DRI2] Setup complete
[    32.076] (II) intel(0): [DRI2]   DRI driver: i915
[    32.076] (II) intel(0): [DRI2]   VDPAU driver: i915
[    32.076] (II) intel(0): direct rendering: DRI2 Enabled
[    32.076] (==) intel(0): hotplug detection: "enabled"
[    32.076] (--) RandR disabled
[    32.089] (II) SELinux: Disabled on system
[    32.095] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    32.095] (II) AIGLX: enabled GLX_ARB_create_context
[    32.095] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    32.095] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    32.095] (II) AIGLX: enabled GLX_INTEL_swap_event
[    32.095] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    32.095] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[    32.095] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[    32.095] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    32.096] (II) AIGLX: Loaded and initialized i915
[    32.096] (II) GLX: Initialized DRI2 GL provider for screen 0
[    32.105] (II) intel(0): switch to mode 1280x800@59.9 on LVDS1 using pipe 1, position (0, 0), rotation normal, reflection none
[    32.173] (II) intel(0): Setting screen physical size to 338 x 211
[    32.191] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    32.197] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    32.197] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    32.197] (II) LoadModule: "evdev"
[    32.197] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    32.198] (II) Module evdev: vendor="X.Org Foundation"
[    32.198]     compiled for 1.15.0, module version = 2.8.2
[    32.198]     Module class: X.Org XInput Driver
[    32.198]     ABI class: X.Org XInput driver, version 20.0
[    32.198] (II) Using input driver 'evdev' for 'Power Button'
[    32.198] (**) Power Button: always reports core events
[    32.198] (**) evdev: Power Button: Device: "/dev/input/event2"
[    32.198] (--) evdev: Power Button: Vendor 0 Product 0x1
[    32.198] (--) evdev: Power Button: Found keys
[    32.198] (II) evdev: Power Button: Configuring as keyboard
[    32.198] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    32.198] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    32.198] (**) Option "xkb_rules" "evdev"
[    32.198] (**) Option "xkb_model" "pc105"
[    32.198] (**) Option "xkb_layout" "dk"
[    32.204] (II) XKB: reuse xkmfile /var/lib/xkb/server-709407198873F5BF4583E7D562E34285659E3DFF.xkm
[    32.205] (II) config/udev: Adding input device Video Bus (/dev/input/event6)
[    32.205] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    32.205] (II) Using input driver 'evdev' for 'Video Bus'
[    32.205] (**) Video Bus: always reports core events
[    32.205] (**) evdev: Video Bus: Device: "/dev/input/event6"
[    32.205] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    32.205] (--) evdev: Video Bus: Found keys
[    32.205] (II) evdev: Video Bus: Configuring as keyboard
[    32.205] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input13/event6"
[    32.205] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    32.205] (**) Option "xkb_rules" "evdev"
[    32.205] (**) Option "xkb_model" "pc105"
[    32.205] (**) Option "xkb_layout" "dk"
[    32.206] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[    32.206] (II) No input driver specified, ignoring this device.
[    32.206] (II) This device may have been added with another device file.
[    32.207] (II) config/udev: Adding input device Sleep Button (/dev/input/event0)
[    32.207] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    32.207] (II) Using input driver 'evdev' for 'Sleep Button'
[    32.207] (**) Sleep Button: always reports core events
[    32.207] (**) evdev: Sleep Button: Device: "/dev/input/event0"
[    32.207] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    32.207] (--) evdev: Sleep Button: Found keys
[    32.207] (II) evdev: Sleep Button: Configuring as keyboard
[    32.207] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input0/event0"
[    32.207] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 8)
[    32.207] (**) Option "xkb_rules" "evdev"
[    32.207] (**) Option "xkb_model" "pc105"
[    32.207] (**) Option "xkb_layout" "dk"
[    32.207] (II) config/udev: Adding drm device (/dev/dri/card0)
[    32.207] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    32.208] (II) config/udev: Adding input device HDA Intel Mic (/dev/input/event9)
[    32.208] (II) No input driver specified, ignoring this device.
[    32.208] (II) This device may have been added with another device file.
[    32.209] (II) config/udev: Adding input device HDA Intel Line (/dev/input/event8)
[    32.209] (II) No input driver specified, ignoring this device.
[    32.209] (II) This device may have been added with another device file.
[    32.209] (II) config/udev: Adding input device HDA Intel Headphone (/dev/input/event7)
[    32.209] (II) No input driver specified, ignoring this device.
[    32.209] (II) This device may have been added with another device file.
[    32.210] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:1017 (/dev/input/event12)
[    32.210] (**) Logitech Unifying Device. Wireless PID:1017: Applying InputClass "evdev pointer catchall"
[    32.210] (II) Using input driver 'evdev' for 'Logitech Unifying Device. Wireless PID:1017'
[    32.210] (**) Logitech Unifying Device. Wireless PID:1017: always reports core events
[    32.210] (**) evdev: Logitech Unifying Device. Wireless PID:1017: Device: "/dev/input/event12"
[    32.210] (--) evdev: Logitech Unifying Device. Wireless PID:1017: Vendor 0x46d Product 0xc52b
[    32.210] (--) evdev: Logitech Unifying Device. Wireless PID:1017: Found 20 mouse buttons
[    32.210] (--) evdev: Logitech Unifying Device. Wireless PID:1017: Found scroll wheel(s)
[    32.210] (--) evdev: Logitech Unifying Device. Wireless PID:1017: Found relative axes
[    32.210] (--) evdev: Logitech Unifying Device. Wireless PID:1017: Found x and y relative axes
[    32.210] (II) evdev: Logitech Unifying Device. Wireless PID:1017: Configuring as mouse
[    32.210] (II) evdev: Logitech Unifying Device. Wireless PID:1017: Adding scrollwheel support
[    32.210] (**) evdev: Logitech Unifying Device. Wireless PID:1017: YAxisMapping: buttons 4 and 5
[    32.210] (**) evdev: Logitech Unifying Device. Wireless PID:1017: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    32.210] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.2/0003:046D:C52B.0003/input/input19/event12"
[    32.210] (II) XINPUT: Adding extended input device "Logitech Unifying Device. Wireless PID:1017" (type: MOUSE, id 9)
[    32.210] (II) evdev: Logitech Unifying Device. Wireless PID:1017: initialized for relative axes.
[    32.210] (**) Logitech Unifying Device. Wireless PID:1017: (accel) keeping acceleration scheme 1
[    32.210] (**) Logitech Unifying Device. Wireless PID:1017: (accel) acceleration profile 0
[    32.210] (**) Logitech Unifying Device. Wireless PID:1017: (accel) acceleration factor: 2.000
[    32.211] (**) Logitech Unifying Device. Wireless PID:1017: (accel) acceleration threshold: 4
[    32.211] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:1017 (/dev/input/mouse2)
[    32.211] (II) No input driver specified, ignoring this device.
[    32.211] (II) This device may have been added with another device file.
[    32.212] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    32.212] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    32.212] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    32.212] (**) AT Translated Set 2 keyboard: always reports core events
[    32.212] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    32.212] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    32.212] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    32.212] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    32.212] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    32.212] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 10)
[    32.212] (**) Option "xkb_rules" "evdev"
[    32.212] (**) Option "xkb_model" "pc105"
[    32.212] (**) Option "xkb_layout" "dk"
[    32.213] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event4)
[    32.213] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    32.213] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    32.213] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[    32.213] (II) LoadModule: "synaptics"
[    32.213] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    32.213] (II) Module synaptics: vendor="X.Org Foundation"
[    32.213]     compiled for 1.15.0, module version = 1.7.4
[    32.213]     Module class: X.Org XInput Driver
[    32.213]     ABI class: X.Org XInput driver, version 20.0
[    32.213] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    32.213] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    32.213] (**) Option "Device" "/dev/input/event4"
[    32.236] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472 (res 74)
[    32.236] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448 (res 120)
[    32.236] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    32.236] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    32.236] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    32.236] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    32.236] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    32.236] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    32.264] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio4/input/input11/event4"
[    32.264] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 11)
[    32.264] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    32.264] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[    32.264] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.040
[    32.264] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    32.264] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    32.264] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    32.264] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    32.264] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    32.265] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    32.265] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    32.265] (II) config/udev: Adding input device PS/2 Generic Mouse (/dev/input/event5)
[    32.266] (**) PS/2 Generic Mouse: Applying InputClass "evdev pointer catchall"
[    32.266] (II) Using input driver 'evdev' for 'PS/2 Generic Mouse'
[    32.266] (**) PS/2 Generic Mouse: always reports core events
[    32.266] (**) evdev: PS/2 Generic Mouse: Device: "/dev/input/event5"
[    32.266] (--) evdev: PS/2 Generic Mouse: Vendor 0x2 Product 0x1
[    32.266] (--) evdev: PS/2 Generic Mouse: Found 3 mouse buttons
[    32.266] (--) evdev: PS/2 Generic Mouse: Found relative axes
[    32.266] (--) evdev: PS/2 Generic Mouse: Found x and y relative axes
[    32.266] (II) evdev: PS/2 Generic Mouse: Configuring as mouse
[    32.266] (**) evdev: PS/2 Generic Mouse: YAxisMapping: buttons 4 and 5
[    32.266] (**) evdev: PS/2 Generic Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    32.266] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio4/serio5/input/input12/event5"
[    32.266] (II) XINPUT: Adding extended input device "PS/2 Generic Mouse" (type: MOUSE, id 12)
[    32.266] (II) evdev: PS/2 Generic Mouse: initialized for relative axes.
[    32.266] (**) PS/2 Generic Mouse: (accel) keeping acceleration scheme 1
[    32.266] (**) PS/2 Generic Mouse: (accel) acceleration profile 0
[    32.266] (**) PS/2 Generic Mouse: (accel) acceleration factor: 2.000
[    32.266] (**) PS/2 Generic Mouse: (accel) acceleration threshold: 4
[    32.267] (II) config/udev: Adding input device PS/2 Generic Mouse (/dev/input/mouse1)
[    32.267] (II) No input driver specified, ignoring this device.
[    32.267] (II) This device may have been added with another device file.
[    32.267] (II) config/udev: Adding input device ST LIS3LV02DL Accelerometer (/dev/input/event10)
[    32.267] (II) No input driver specified, ignoring this device.
[    32.267] (II) This device may have been added with another device file.
[    32.268] (II) config/udev: Adding input device ST LIS3LV02DL Accelerometer (/dev/input/js0)
[    32.268] (II) No input driver specified, ignoring this device.
[    32.268] (II) This device may have been added with another device file.
[    32.271] (II) config/udev: Adding input device HP WMI hotkeys (/dev/input/event11)
[    32.272] (**) HP WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    32.272] (II) Using input driver 'evdev' for 'HP WMI hotkeys'
[    32.272] (**) HP WMI hotkeys: always reports core events
[    32.272] (**) evdev: HP WMI hotkeys: Device: "/dev/input/event11"
[    32.272] (--) evdev: HP WMI hotkeys: Vendor 0 Product 0
[    32.272] (--) evdev: HP WMI hotkeys: Found keys
[    32.272] (II) evdev: HP WMI hotkeys: Configuring as keyboard
[    32.272] (**) Option "config_info" "udev:/sys/devices/virtual/input/input18/event11"
[    32.272] (II) XINPUT: Adding extended input device "HP WMI hotkeys" (type: KEYBOARD, id 13)
[    32.272] (**) Option "xkb_rules" "evdev"
[    32.272] (**) Option "xkb_model" "pc105"
[    32.272] (**) Option "xkb_layout" "dk"
[    33.416] (II) intel(0): EDID vendor "LPL", prod id 36096
[    33.416] (II) intel(0): Printing DDC gathered Modelines:
[    33.416] (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz eP)
[    42.276] (II) AIGLX: Suspending AIGLX clients for VT switch

```

---

### Post by kjetil-fleten on 2014-06-13
I never found a fix for this, but in the end I repaired the settings from the Ubuntu install media. Thats probably the fastest way if anyone else face this problem. All personal files was kept, and that was most important.

---

