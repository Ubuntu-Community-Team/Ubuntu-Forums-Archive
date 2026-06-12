---
title: "external monitor not detected xubuntu 14.04.2"
date: 2015-04-19
forum: Hardware
---

### Post by alex370 on 2015-04-19
Hi guys, 

I'm having some problems with ubuntu detecting my external monitor, all worked great just about a week ago when an automatic update seems to broke something, 

Problem : external monitor not detected, sometimes after reboot the monitor is detected but most of the time it's not, today for example after booting it was detected but as soon as i ran xrandr in cli it got off. Tried plug/unplug monitor, disable/reinstall intel driver, reinstall xubuntu, booting with nomodeset, manual configuration of /etc/X11/xorg.conf but none of these seems to work :(

I found the same behavior in Linux Mint 17.1 Rebecca

Hardware configuration :
  Manufacturer: Dell Inc.
    Product Name: Vostro 5470




Current setup :

```
lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
    Subsystem: Dell Device 0615
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 64
    Region 0: Memory at d0000000 (64-bit, non-prefetchable) [size=4M]
    Region 2: Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Region 4: I/O ports at 5000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915

[     5.374] 
X.Org X Server 1.16.0
Release Date: 2014-07-16
[     5.374] X Protocol Version 11, Revision 0
[     5.374] Build Operating System: Linux 3.2.0-70-generic x86_64 Ubuntu
[     5.374] Current Operating System: Linux alex 3.16.0-34-generic #47~14.04.1-Ubuntu SMP Fri Apr 10 17:49:16 UTC 2015 x86_64
[     5.374] Kernel command line:  BOOT_IMAGE=/boot/vmlinuz-3.16.0-34-generic.efi.signed  root=UUID=5cc895a0-0b11-4d8c-8f63-e8ff3214f7f0 ro quiet splash  vt.handoff=7
[     5.374] Build Date: 12 February 2015  11:11:26PM
[     5.374] xorg-server 2:1.16.0-1ubuntu1.2~trusty2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[     5.374] Current version of pixman: 0.30.2
[     5.374]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[     5.374] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     5.374] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Apr 19 10:03:20 2015
[     5.376] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     5.377] (==) No Layout section.  Using the first Screen section.
[     5.377] (==) No screen section available. Using defaults.
[     5.377] (**) |-->Screen "Default Screen Section" (0)
[     5.377] (**) |   |-->Monitor "<default monitor>"
[     5.377] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[     5.377] (==) Automatically adding devices
[     5.377] (==) Automatically enabling devices
[     5.377] (==) Automatically adding GPU devices
[     5.379] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     5.379]     Entry deleted from font path.
[     5.379] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     5.379]     Entry deleted from font path.
[     5.379] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     5.379]     Entry deleted from font path.
[     5.379] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     5.379]     Entry deleted from font path.
[     5.379] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     5.379]     Entry deleted from font path.
[     5.379] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[     5.379] (==) ModulePath set to  "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     5.379] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[     5.379] (II) Loader magic: 0x7f58b6071c80
[     5.379] (II) Module ABI versions:
[     5.380]     X.Org ANSI C Emulation: 0.4
[     5.380]     X.Org Video Driver: 18.0
[     5.380]     X.Org XInput driver : 21.0
[     5.380]     X.Org Server Extension : 8.0
[     5.380] (II) xfree86: Adding drm device (/dev/dri/card0)
[     5.381] (--) PCI:*(0:0:2:0) 8086:0a16:1028:0615 rev 9, Mem @ 0xd0000000/4194304, 0xc0000000/268435456, I/O @ 0x00005000/64
[     5.381] (II) LoadModule: "glx"
[     5.382] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[     5.391] (II) Module glx: vendor="X.Org Foundation"
[     5.391]     compiled for 1.16.0, module version = 1.0.0
[     5.391]     ABI class: X.Org Server Extension, version 8.0
[     5.391] (==) AIGLX enabled
[     5.391] (==) Matched intel as autoconfigured driver 0
[     5.391] (==) Matched intel as autoconfigured driver 1
[     5.391] (==) Matched modesetting as autoconfigured driver 2
[     5.391] (==) Matched fbdev as autoconfigured driver 3
[     5.391] (==) Matched vesa as autoconfigured driver 4
[     5.391] (==) Assigned the driver to the xf86ConfigLayout
[     5.391] (II) LoadModule: "intel"
[     5.393] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[     5.395] (II) Module intel: vendor="X.Org Foundation"
[     5.395]     compiled for 1.16.0, module version = 2.99.914
[     5.395]     Module class: X.Org Video Driver
[     5.395]     ABI class: X.Org Video Driver, version 18.0
[     5.395] (II) LoadModule: "modesetting"
[     5.395] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[     5.398] (II) Module modesetting: vendor="X.Org Foundation"
[     5.398]     compiled for 1.16.0, module version = 0.9.0
[     5.398]     Module class: X.Org Video Driver
[     5.398]     ABI class: X.Org Video Driver, version 18.0
[     5.398] (II) LoadModule: "fbdev"
[     5.398] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     5.399] (II) Module fbdev: vendor="X.Org Foundation"
[     5.399]     compiled for 1.16.0, module version = 0.4.4
[     5.399]     Module class: X.Org Video Driver
[     5.399]     ABI class: X.Org Video Driver, version 18.0
[     5.399] (II) LoadModule: "vesa"
[     5.399] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     5.402] (II) Module vesa: vendor="X.Org Foundation"
[     5.402]     compiled for 1.16.0, module version = 2.3.3
[     5.402]     Module class: X.Org Video Driver
[     5.402]     ABI class: X.Org Video Driver, version 18.0
[     5.402] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[     5.402] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[     5.402] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[     5.402] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[     5.402] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[     5.402] (II) FBDEV: driver for framebuffer: fbdev
[     5.402] (II) VESA: driver for VESA chipsets: vesa
[     5.403] (++) using VT number 7

[     5.403] (II) intel(0): Using Kernel Mode Setting driver: i915, version 1.6.0 20080730
[     5.403] (II) intel(0): SNA compiled:  xserver-xorg-video-intel-lts-utopic 2:2.99.914-1~exp1ubuntu4.2~trusty1  (Maarten Lankhorst <maarten.lankhorst@ubuntu.com>)
[     5.403] (II) intel(0): SNA compiled for use with valgrind
[     5.404] (WW) Falling back to old probe method for modesetting
[     5.404] (WW) Falling back to old probe method for fbdev
[     5.404] (II) Loading sub module "fbdevhw"
[     5.404] (II) LoadModule: "fbdevhw"
[     5.404] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[     5.405] (II) Module fbdevhw: vendor="X.Org Foundation"
[     5.405]     compiled for 1.16.0, module version = 0.0.2
[     5.405]     ABI class: X.Org Video Driver, version 18.0
[     5.405] (WW) Falling back to old probe method for vesa
[     5.406] (--) intel(0): Integrated Graphics Chipset: Intel(R) HD Graphics 4400
[     5.406] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2, avx, avx2
[     5.406] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[     5.406] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[     5.406] (==) intel(0): RGB weight 888
[     5.406] (==) intel(0): Default visual is TrueColor
[     5.406] (II) intel(0): Output eDP1 has no monitor section
[     5.406] (--) intel(0): Found backlight control interface intel_backlight (type 'raw') for output eDP1
[     5.406] (II) intel(0): Output HDMI1 has no monitor section
[     5.406] (--) intel(0): Using a maximum size of 256x256 for hardware cursors
[     5.406] (II) intel(0): Output VIRTUAL1 has no monitor section
[     5.406] (--) intel(0): Output eDP1 using initial mode 1366x768 on pipe 0
[     5.406] (--) intel(0): Output HDMI1 using initial mode 1920x1080 on pipe 1
[     5.406] (==) intel(0): TearFree disabled
[     5.406] (==) intel(0): DPI set to (96, 96)
[     5.406] (II) Loading sub module "dri2"
[     5.406] (II) LoadModule: "dri2"
[     5.406] (II) Module "dri2" already built-in
[     5.406] (II) Loading sub module "present"
[     5.406] (II) LoadModule: "present"
[     5.406] (II) Module "present" already built-in
[     5.508] (II) UnloadModule: "modesetting"
[     5.508] (II) Unloading modesetting
[     5.508] (II) UnloadModule: "fbdev"
[     5.508] (II) Unloading fbdev
[     5.508] (II) UnloadSubModule: "fbdevhw"
[     5.508] (II) Unloading fbdevhw
[     5.508] (II) UnloadModule: "vesa"
[     5.508] (II) Unloading vesa
[     5.508] (==) Depth 24 pixmap format is 32 bpp
[     5.510] (II) intel(0): SNA initialized with Haswell (gen7.5, gt2) backend
[     5.510] (==) intel(0): Backing store enabled
[     5.510] (==) intel(0): Silken mouse enabled
[     5.511] (II) intel(0): HW Cursor enabled
[     5.511] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[     5.511] (==) intel(0): DPMS enabled
[     5.511] (II) intel(0): [DRI2] Setup complete
[     5.511] (II) intel(0): [DRI2]   DRI driver: i965
[     5.511] (II) intel(0): [DRI2]   VDPAU driver: i965
[     5.511] (II) intel(0): direct rendering: DRI2 enabled
[     5.511] (II) intel(0): hardware support for Present enabled
[     5.511] (==) intel(0): display hotplug detection enabled
[     5.511] (--) RandR disabled
[     5.544] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[     5.544] (II) AIGLX: enabled GLX_ARB_create_context
[     5.544] (II) AIGLX: enabled GLX_ARB_create_context_profile
[     5.544] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[     5.544] (II) AIGLX: enabled GLX_INTEL_swap_event
[     5.544] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[     5.544] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[     5.544] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[     5.544] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[     5.544] (II) AIGLX: enabled GLX_ARB_create_context_robustness
[     5.544] (II) AIGLX: Loaded and initialized i965
[     5.544] (II) GLX: Initialized DRI2 GL provider for screen 0
[     5.548] (II) intel(0): switch to mode 1366x768@60.0 on eDP1 using pipe 0, position (0, 0), rotation normal, reflection none
[     5.556] (II) intel(0): switch to mode 1920x1080@60.0 on HDMI1 using  pipe 1, position (0, 0), rotation normal, reflection none
[     5.572] (II) intel(0): Setting screen physical size to 508 x 285
[     5.581] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[     5.586] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[     5.586] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     5.586] (II) LoadModule: "evdev"
[     5.586] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     5.588] (II) Module evdev: vendor="X.Org Foundation"
[     5.588]     compiled for 1.16.0, module version = 2.9.0
[     5.588]     Module class: X.Org XInput Driver
[     5.588]     ABI class: X.Org XInput driver, version 21.0
[     5.588] (II) Using input driver 'evdev' for 'Power Button'
[     5.588] (**) Power Button: always reports core events
[     5.588] (**) evdev: Power Button: Device: "/dev/input/event3"
[     5.588] (--) evdev: Power Button: Vendor 0 Product 0x1
[     5.588] (--) evdev: Power Button: Found keys
[     5.588] (II) evdev: Power Button: Configuring as keyboard
[     5.588] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[     5.588] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[     5.588] (**) Option "xkb_rules" "evdev"
[     5.588] (**) Option "xkb_model" "pc105"
[     5.588] (**) Option "xkb_layout" "us"
[     5.589] (II) config/udev: Adding input device Video Bus (/dev/input/event10)
[     5.589] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[     5.589] (II) Using input driver 'evdev' for 'Video Bus'
[     5.589] (**) Video Bus: always reports core events
[     5.589] (**) evdev: Video Bus: Device: "/dev/input/event10"
[     5.589] (--) evdev: Video Bus: Vendor 0 Product 0x6
[     5.589] (--) evdev: Video Bus: Found keys
[     5.589] (II) evdev: Video Bus: Configuring as keyboard
[     5.589] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input11/event10"
[     5.589] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[     5.589] (**) Option "xkb_rules" "evdev"
[     5.589] (**) Option "xkb_model" "pc105"
[     5.589] (**) Option "xkb_layout" "us"
[     5.589] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[     5.589] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     5.589] (II) Using input driver 'evdev' for 'Power Button'
[     5.589] (**) Power Button: always reports core events
[     5.590] (**) evdev: Power Button: Device: "/dev/input/event0"
[     5.590] (--) evdev: Power Button: Vendor 0 Product 0x1
[     5.590] (--) evdev: Power Button: Found keys
[     5.590] (II) evdev: Power Button: Configuring as keyboard
[     5.590] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[     5.590] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[     5.590] (**) Option "xkb_rules" "evdev"
[     5.590] (**) Option "xkb_model" "pc105"
[     5.590] (**) Option "xkb_layout" "us"
[     5.590] (II) config/udev: Adding input device Lid Switch (/dev/input/event2)
[     5.590] (II) No input driver specified, ignoring this device.
[     5.590] (II) This device may have been added with another device file.
[     5.590] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[     5.590] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[     5.590] (II) Using input driver 'evdev' for 'Sleep Button'
[     5.590] (**) Sleep Button: always reports core events
[     5.590] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[     5.590] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[     5.590] (--) evdev: Sleep Button: Found keys
[     5.590] (II) evdev: Sleep Button: Configuring as keyboard
[     5.590] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1/event1"
[     5.590] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[     5.590] (**) Option "xkb_rules" "evdev"
[     5.590] (**) Option "xkb_model" "pc105"
[     5.590] (**) Option "xkb_layout" "us"
[     5.591] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=3 (/dev/input/event11)
[     5.591] (II) No input driver specified, ignoring this device.
[     5.591] (II) This device may have been added with another device file.
[     5.591] (II) config/udev: Adding input device Chicony Wireless Device (/dev/input/event5)
[     5.591] (**) Chicony Wireless Device: Applying InputClass "evdev keyboard catchall"
[     5.591] (II) Using input driver 'evdev' for 'Chicony Wireless Device'
[     5.591] (**) Chicony Wireless Device: always reports core events
[     5.591] (**) evdev: Chicony Wireless Device: Device: "/dev/input/event5"
[     5.591] (--) evdev: Chicony Wireless Device: Vendor 0x4f2 Product 0x1026
[     5.591] (--) evdev: Chicony Wireless Device: Found keys
[     5.591] (II) evdev: Chicony Wireless Device: Configuring as keyboard
[     5.591] (**) Option "config_info"  "udev:/sys/devices/pci0000:00/0000:00:14.0/usb2/2-1/2-1:1.0/0003:04F2:1026.0001/input/input7/event5"
[     5.591] (II) XINPUT: Adding extended input device "Chicony Wireless Device" (type: KEYBOARD, id 10)
[     5.591] (**) Option "xkb_rules" "evdev"
[     5.591] (**) Option "xkb_model" "pc105"
[     5.591] (**) Option "xkb_layout" "us"
[     5.592] (II) config/udev: Adding input device Chicony Wireless Device (/dev/input/event6)
[     5.592] (**) Chicony Wireless Device: Applying InputClass "evdev keyboard catchall"
[     5.592] (II) Using input driver 'evdev' for 'Chicony Wireless Device'
[     5.592] (**) Chicony Wireless Device: always reports core events
[     5.592] (**) evdev: Chicony Wireless Device: Device: "/dev/input/event6"
[     5.592] (--) evdev: Chicony Wireless Device: Vendor 0x4f2 Product 0x1026
[     5.592] (--) evdev: Chicony Wireless Device: Found 1 mouse buttons
[     5.592] (--) evdev: Chicony Wireless Device: Found scroll wheel(s)
[     5.592] (--) evdev: Chicony Wireless Device: Found relative axes
[     5.592] (II) evdev: Chicony Wireless Device: Forcing relative x/y axes to exist.
[     5.592] (--) evdev: Chicony Wireless Device: Found absolute axes
[     5.592] (II) evdev: Chicony Wireless Device: Forcing absolute x/y axes to exist.
[     5.592] (--) evdev: Chicony Wireless Device: Found keys
[     5.592] (II) evdev: Chicony Wireless Device: Configuring as mouse
[     5.592] (II) evdev: Chicony Wireless Device: Configuring as keyboard
[     5.592] (II) evdev: Chicony Wireless Device: Adding scrollwheel support
[     5.592] (**) evdev: Chicony Wireless Device: YAxisMapping: buttons 4 and 5
[     5.592] (**) evdev: Chicony Wireless Device: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     5.592] (**) Option "config_info"  "udev:/sys/devices/pci0000:00/0000:00:14.0/usb2/2-1/2-1:1.1/0003:04F2:1026.0002/input/input8/event6"
[     5.592] (II) XINPUT: Adding extended input device "Chicony Wireless Device" (type: KEYBOARD, id 11)
[     5.592] (**) Option "xkb_rules" "evdev"
[     5.592] (**) Option "xkb_model" "pc105"
[     5.592] (**) Option "xkb_layout" "us"
[     5.592] (II) evdev: Chicony Wireless Device: initialized for relative axes.
[     5.592] (WW) evdev: Chicony Wireless Device: ignoring absolute axes.
[     5.592] (**) Chicony Wireless Device: (accel) keeping acceleration scheme 1
[     5.592] (**) Chicony Wireless Device: (accel) acceleration profile 0
[     5.592] (**) Chicony Wireless Device: (accel) acceleration factor: 2.000
[     5.592] (**) Chicony Wireless Device: (accel) acceleration threshold: 4
[     5.593] (II) config/udev: Adding input device Chicony Wireless Device (/dev/input/event7)
[     5.593] (**) Chicony Wireless Device: Applying InputClass "evdev pointer catchall"
[     5.593] (II) Using input driver 'evdev' for 'Chicony Wireless Device'
[     5.593] (**) Chicony Wireless Device: always reports core events
[     5.593] (**) evdev: Chicony Wireless Device: Device: "/dev/input/event7"
[     5.593] (--) evdev: Chicony Wireless Device: Vendor 0x4f2 Product 0x1026
[     5.593] (--) evdev: Chicony Wireless Device: Found 3 mouse buttons
[     5.593] (--) evdev: Chicony Wireless Device: Found scroll wheel(s)
[     5.593] (--) evdev: Chicony Wireless Device: Found relative axes
[     5.593] (--) evdev: Chicony Wireless Device: Found x and y relative axes
[     5.593] (II) evdev: Chicony Wireless Device: Configuring as mouse
[     5.593] (II) evdev: Chicony Wireless Device: Adding scrollwheel support
[     5.593] (**) evdev: Chicony Wireless Device: YAxisMapping: buttons 4 and 5
[     5.593] (**) evdev: Chicony Wireless Device: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     5.593] (**) Option "config_info"  "udev:/sys/devices/pci0000:00/0000:00:14.0/usb2/2-1/2-1:1.2/0003:04F2:1026.0003/input/input9/event7"
[     5.593] (II) XINPUT: Adding extended input device "Chicony Wireless Device" (type: MOUSE, id 12)
[     5.593] (II) evdev: Chicony Wireless Device: initialized for relative axes.
[     5.593] (**) Chicony Wireless Device: (accel) keeping acceleration scheme 1
[     5.593] (**) Chicony Wireless Device: (accel) acceleration profile 0
[     5.593] (**) Chicony Wireless Device: (accel) acceleration factor: 2.000
[     5.593] (**) Chicony Wireless Device: (accel) acceleration threshold: 4
[     5.593] (II) config/udev: Adding input device Chicony Wireless Device (/dev/input/mouse0)
[     5.593] (II) No input driver specified, ignoring this device.
[     5.593] (II) This device may have been added with another device file.
[     5.594] (II) config/udev: Adding input device Laptop_Integrated_Webcam_HD (/dev/input/event13)
[     5.594] (**) Laptop_Integrated_Webcam_HD: Applying InputClass "evdev keyboard catchall"
[     5.594] (II) Using input driver 'evdev' for 'Laptop_Integrated_Webcam_HD'
[     5.594] (**) Laptop_Integrated_Webcam_HD: always reports core events
[     5.594] (**) evdev: Laptop_Integrated_Webcam_HD: Device: "/dev/input/event13"
[     5.594] (--) evdev: Laptop_Integrated_Webcam_HD: Vendor 0xc45 Product 0x6500
[     5.594] (--) evdev: Laptop_Integrated_Webcam_HD: Found keys
[     5.594] (II) evdev: Laptop_Integrated_Webcam_HD: Configuring as keyboard
[     5.594] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb2/2-5/2-5:1.0/input/input14/event13"
[     5.594] (II) XINPUT: Adding extended input device "Laptop_Integrated_Webcam_HD" (type: KEYBOARD, id 13)
[     5.594] (**) Option "xkb_rules" "evdev"
[     5.594] (**) Option "xkb_model" "pc105"
[     5.594] (**) Option "xkb_layout" "us"
[     5.594] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event12)
[     5.594] (II) No input driver specified, ignoring this device.
[     5.594] (II) This device may have been added with another device file.
[     5.594] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[     5.594] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[     5.594] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[     5.595] (**) AT Translated Set 2 keyboard: always reports core events
[     5.595] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[     5.595] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[     5.595] (--) evdev: AT Translated Set 2 keyboard: Found keys
[     5.595] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[     5.595] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[     5.595] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 14)
[     5.595] (**) Option "xkb_rules" "evdev"
[     5.595] (**) Option "xkb_model" "pc105"
[     5.595] (**) Option "xkb_layout" "us"
[     5.595] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/event8)
[     5.595] (**) ETPS/2 Elantech Touchpad: Applying InputClass "evdev touchpad catchall"
[     5.595] (**) ETPS/2 Elantech Touchpad: Applying InputClass "touchpad catchall"
[     5.595] (**) ETPS/2 Elantech Touchpad: Applying InputClass "Default clickpad buttons"
[     5.595] (II) LoadModule: "synaptics"
[     5.595] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[     5.596] (II) Module synaptics: vendor="X.Org Foundation"
[     5.596]     compiled for 1.16.0, module version = 1.8.99
[     5.596]     Module class: X.Org XInput Driver
[     5.596]     ABI class: X.Org XInput driver, version 21.0
[     5.596] (II) Using input driver 'synaptics' for 'ETPS/2 Elantech Touchpad'
[     5.596] (**) ETPS/2 Elantech Touchpad: always reports core events
[     5.596] (**) Option "Device" "/dev/input/event8"
[     5.612] (II) synaptics: ETPS/2 Elantech Touchpad: found clickpad property
[     5.612] (--) synaptics: ETPS/2 Elantech Touchpad: x-axis range 0 - 3420 (res 32)
[     5.612] (--) synaptics: ETPS/2 Elantech Touchpad: y-axis range 0 - 2223 (res 31)
[     5.612] (--) synaptics: ETPS/2 Elantech Touchpad: pressure range 0 - 255
[     5.612] (--) synaptics: ETPS/2 Elantech Touchpad: finger width range 0 - 15
[     5.612] (--) synaptics: ETPS/2 Elantech Touchpad: buttons: left double triple
[     5.612] (--) synaptics: ETPS/2 Elantech Touchpad: Vendor 0x2 Product 0xe
[     5.612] (**) Option "SoftButtonAreas" "50% 0 82% 0 0 0 0 0"
[     5.612] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[     5.612] (**) ETPS/2 Elantech Touchpad: always reports core events
[     5.624] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input6/event8"
[     5.624] (II) XINPUT: Adding extended input device "ETPS/2 Elantech Touchpad" (type: TOUCHPAD, id 15)
[     5.624] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MinSpeed is now constant deceleration 2.5
[     5.624] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MaxSpeed is now 1.75
[     5.624] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) AccelFactor is now 0.049
[     5.624] (**) ETPS/2 Elantech Touchpad: (accel) keeping acceleration scheme 1
[     5.624] (**) ETPS/2 Elantech Touchpad: (accel) acceleration profile 1
[     5.624] (**) ETPS/2 Elantech Touchpad: (accel) acceleration factor: 2.000
[     5.624] (**) ETPS/2 Elantech Touchpad: (accel) acceleration threshold: 4
[     5.624] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[     5.624] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/mouse1)
[     5.624] (**) ETPS/2 Elantech Touchpad: Ignoring device from InputClass "touchpad ignore duplicates"
[     5.626] (II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event9)
[     5.626] (**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[     5.626] (II) Using input driver 'evdev' for 'Dell WMI hotkeys'
[     5.626] (**) Dell WMI hotkeys: always reports core events
[     5.626] (**) evdev: Dell WMI hotkeys: Device: "/dev/input/event9"
[     5.626] (--) evdev: Dell WMI hotkeys: Vendor 0 Product 0
[     5.626] (--) evdev: Dell WMI hotkeys: Found keys
[     5.626] (II) evdev: Dell WMI hotkeys: Configuring as keyboard
[     5.626] (**) Option "config_info" "udev:/sys/devices/virtual/input/input10/event9"
[     5.626] (II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD, id 16)
[     5.626] (**) Option "xkb_rules" "evdev"
[     5.626] (**) Option "xkb_model" "pc105"
[     5.626] (**) Option "xkb_layout" "us"
[    25.819] (II) intel(0): EDID vendor "BOE", prod id 1509
[    25.819] (II) intel(0): Printing DDC gathered Modelines:
[    25.819] (II) intel(0): Modeline "1366x768"x0.0   71.40  1366 1414 1446 1488  768 771 777 800 +hsync -vsync (48.0 kHz eP)
[    25.819] (II) intel(0): Modeline "1366x768"x0.0   56.80  1366 1414 1446 1622  768 771 777 876 +hsync -vsync (35.0 kHz e)
```



then after running xrandr in console the external monitor got black and following lines were written to xorg log

```
[  1095.561] (II) intel(0): resizing framebuffer to 1366x768
[  1095.561] (II) intel(0): switch to mode 1366x768@60.0 on eDP1 using pipe 0, position (0, 0), rotation normal, reflection none
```

---

### Post by alex370 on 2015-04-20
Update : I tried connecting TV and it works fine even after reboots, plug/unplug the HDMI cable, the difference is that between laptop and tv it's HDMI to HDMI and between laptop and external monitor it'a HDMI to DVI. I've tried the monitor on another laptop with XBMC ubuntu and it's working fine ....

any ideas?

---

### Post by alex370 on 2015-04-21
After reading a bit about HDMI/DVI and redirecting audio through my external usb only card it seems that my monitor started to work, tried a few reboots,lid open/close and my monitor stays on :). Probably hdmi port on my laptop tried to send audio also and my monitor ( dvi input ) didn't understand.

---

