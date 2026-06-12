---
title: "[Nvidia] Black screen on Nvidia 970M after reboot"
date: 2015-01-30
forum: Hardware
---

### Post by alexandre19 on 2015-01-30
Hello,

I am encoutering a very peculiar problem on my recent laptop (with hybrid graphics).
After a reboot, it started to show a black screen instead of the usual login screen. TTY was fine, however.
Using the tty to relaunch lightdm didn't work.
After purging my current nvidia drivers (nvidia-343 from xorg-edgers) and installing nvidia-346, i can use "prime-select" to get the login screen with the intel card.
Now, when using the nvidia card, it still shows a black screen. However, i can hear the lightdm chime from the login screen. When closing and reopening the laptop (causing sleep mode), the login screen shows and i can use the computer.
When rebooting, it is the same thing all over again : black screen and sleep mode to get it back.
An interesting thing is that OpenGL code (which used to work) refuses to run when the nvidia card is selected, with the same errors it produces on the intel card.

Thank you.

Edit:
I forgot to mention that i run Ubuntu 14.04 and kernel 3.13.0-44-generic

---

### Post by lotus49 on 2015-01-30
I have **exactly** the same experience with a laptop with an Nvidia 840M card except I was using the nvidia-340 package from xorg-edgers.  There was a recent upgrade to the driver but I think this may have happened after I had the black screen.

The one thing I might add to your description is that the screen is off, not just showing nothing i.e. it is completely black and not emitting any light at all.

---

### Post by alexandre19 on 2015-01-30
Hi lotus,

When did you last update the system and the rebooted ?

I have the issue since this morning (january 30th). I updated yesterday, but did not reboot then.
A colleague has the same issue on the exact same computer, only it showed on january 24th.
He did a "apt-get purge nvidia*" and was able to get a screen back.

---

### Post by alexandre19 on 2015-01-31
Here is the Xorg log right after reboot :

```

[    10.403] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[    10.403] X Protocol Version 11, Revision 0
[    10.403] Build Operating System: Linux 3.2.0-70-generic x86_64 Ubuntu
[    10.403] Current Operating System: Linux alexandre-GS60-2QE 3.13.0-45-generic #74-Ubuntu SMP Tue Jan 13 19:36:28 UTC 2015 x86_64
[    10.403] Kernel command line: BOOT_IMAGE=/vmlinuz-3.13.0-45-generic root=/dev/mapper/ubuntu--vg-root ro quiet splash
[    10.403] Build Date: 10 December 2014  06:15:52PM
[    10.403] xorg-server 2:1.15.1-0ubuntu2.6 (For technical support please see http://www.ubuntu.com/support) 
[    10.403] Current version of pixman: 0.30.2
[    10.403]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    10.403] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    10.403] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Jan 31 11:37:08 2015
[    10.404] (==) Using config file: "/etc/X11/xorg.conf"
[    10.404] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    10.406] (==) ServerLayout "layout"
[    10.406] (**) |-->Screen "nvidia" (0)
[    10.406] (**) |   |-->Monitor "<default monitor>"
[    10.406] (**) |   |-->Device "nvidia"
[    10.406] (==) No monitor specified for screen "nvidia".
    Using a default monitor configuration.
[    10.406] (**) |-->Inactive Device "intel"
[    10.406] (==) Automatically adding devices
[    10.406] (==) Automatically enabling devices
[    10.406] (==) Automatically adding GPU devices
[    10.408] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    10.408]     Entry deleted from font path.
[    10.408] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    10.408]     Entry deleted from font path.
[    10.408] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    10.408]     Entry deleted from font path.
[    10.409] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    10.409]     Entry deleted from font path.
[    10.409] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    10.409]     Entry deleted from font path.
[    10.409] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    10.409] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    10.409] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    10.409] (II) Loader magic: 0x7fa4ab611d40
[    10.409] (II) Module ABI versions:
[    10.409]     X.Org ANSI C Emulation: 0.4
[    10.409]     X.Org Video Driver: 15.0
[    10.409]     X.Org XInput driver : 20.0
[    10.409]     X.Org Server Extension : 8.0
[    10.409] (II) xfree86: Adding drm device (/dev/dri/card1)
[    10.409] (II) xfree86: Adding drm device (/dev/dri/card0)
[    10.410] (--) PCI:*(0:0:2:0) 8086:0416:1462:1102 rev 6, Mem @ 0xf6400000/4194304, 0xd0000000/268435456, I/O @ 0x0000f000/64
[    10.410] (--) PCI: (0:1:0:0) 10de:13d8:1462:1102 rev 161, Mem @ 0xf5000000/16777216, 0xe0000000/268435456, 0xf0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[    10.412] Initializing built-in extension Generic Event Extension
[    10.412] Initializing built-in extension SHAPE
[    10.412] Initializing built-in extension MIT-SHM
[    10.412] Initializing built-in extension XInputExtension
[    10.412] Initializing built-in extension XTEST
[    10.412] Initializing built-in extension BIG-REQUESTS
[    10.412] Initializing built-in extension SYNC
[    10.412] Initializing built-in extension XKEYBOARD
[    10.412] Initializing built-in extension XC-MISC
[    10.412] Initializing built-in extension SECURITY
[    10.412] Initializing built-in extension XINERAMA
[    10.412] Initializing built-in extension XFIXES
[    10.412] Initializing built-in extension RENDER
[    10.412] Initializing built-in extension RANDR
[    10.412] Initializing built-in extension COMPOSITE
[    10.412] Initializing built-in extension DAMAGE
[    10.412] Initializing built-in extension MIT-SCREEN-SAVER
[    10.412] Initializing built-in extension DOUBLE-BUFFER
[    10.412] Initializing built-in extension RECORD
[    10.412] Initializing built-in extension DPMS
[    10.412] Initializing built-in extension Present
[    10.412] Initializing built-in extension DRI3
[    10.412] Initializing built-in extension X-Resource
[    10.412] Initializing built-in extension XVideo
[    10.412] Initializing built-in extension XVideo-MotionCompensation
[    10.412] Initializing built-in extension SELinux
[    10.412] Initializing built-in extension XFree86-VidModeExtension
[    10.412] Initializing built-in extension XFree86-DGA
[    10.412] Initializing built-in extension XFree86-DRI
[    10.412] Initializing built-in extension DRI2
[    10.412] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    10.412] (II) "glx" will be loaded by default.
[    10.412] (WW) "xmir" is not to be loaded by default. Skipping.
[    10.412] (II) LoadModule: "glx"
[    10.413] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    10.490] (II) Module glx: vendor="NVIDIA Corporation"
[    10.490]     compiled for 4.0.2, module version = 1.0.0
[    10.490]     Module class: X.Org Server Extension
[    10.491] (II) NVIDIA GLX Module  346.35  Sat Jan 10 20:53:39 PST 2015
[    10.492] Loading extension GLX
[    10.492] (II) LoadModule: "nvidia"
[    10.492] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    10.498] (II) Module nvidia: vendor="NVIDIA Corporation"
[    10.498]     compiled for 4.0.2, module version = 1.0.0
[    10.498]     Module class: X.Org Video Driver
[    10.498] (II) LoadModule: "intel"
[    10.499] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    10.502] (II) Module intel: vendor="X.Org Foundation"
[    10.502]     compiled for 1.15.1, module version = 2.99.917
[    10.502]     Module class: X.Org Video Driver
[    10.502]     ABI class: X.Org Video Driver, version 15.0
[    10.502] (II) NVIDIA dlloader X Driver  346.35  Sat Jan 10 20:32:18 PST 2015
[    10.502] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    10.502] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[    10.502] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[    10.502] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[    10.502] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[    10.502] (++) using VT number 7

[    10.503] (II) Loading sub module "fb"
[    10.503] (II) LoadModule: "fb"
[    10.505] (II) Loading /usr/lib/xorg/modules/libfb.so
[    10.506] (II) Module fb: vendor="X.Org Foundation"
[    10.506]     compiled for 1.15.1, module version = 1.0.0
[    10.506]     ABI class: X.Org ANSI C Emulation, version 0.4
[    10.506] (II) Loading sub module "wfb"
[    10.506] (II) LoadModule: "wfb"
[    10.506] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    10.507] (II) Module wfb: vendor="X.Org Foundation"
[    10.507]     compiled for 1.15.1, module version = 1.0.0
[    10.507]     ABI class: X.Org ANSI C Emulation, version 0.4
[    10.507] (II) Loading sub module "ramdac"
[    10.507] (II) LoadModule: "ramdac"
[    10.507] (II) Module "ramdac" already built-in
[    10.509] (II) intel(G0): Using Kernel Mode Setting driver: i915, version 1.6.0 20080730
[    10.509] (II) intel(G0): SNA compiled: xserver-xorg-video-intel 2:2.99.917+git20150128.2e7ae760-0ubuntu0sarvatt~trusty (Robert Hooker <sarvatt@ubuntu.com>)
[    10.509] (II) intel(G0): SNA compiled for use with valgrind
[    10.510] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "nvidia" for depth/fbbpp 24/32
[    10.510] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    10.510] (==) NVIDIA(0): RGB weight 888
[    10.510] (==) NVIDIA(0): Default visual is TrueColor
[    10.510] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    10.511] (**) NVIDIA(0): Option "ConstrainCursor" "off"
[    10.511] (**) NVIDIA(0): Option "AllowEmptyInitialConfiguration" "on"
[    10.511] (**) NVIDIA(0): Option "IgnoreDisplayDevices" "CRT"
[    10.511] (**) NVIDIA(0): Enabling 2D acceleration
[    11.500] (II) NVIDIA(GPU-0): Found DRM driver nvidia-drm (20130102)
[    11.501] (II) NVIDIA(0): NVIDIA GPU GeForce GTX 970M (GM204-A) at PCI:1:0:0 (GPU-0)
[    11.501] (--) NVIDIA(0): Memory: 3145728 kBytes
[    11.501] (--) NVIDIA(0): VideoBIOS: 84.04.20.00.0a
[    11.501] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    11.501] (--) NVIDIA(0): Valid display device(s) on GeForce GTX 970M at PCI:1:0:0
[    11.501] (--) NVIDIA(0):     none
[    11.501] (II) NVIDIA(0): Validated MetaModes:
[    11.501] (II) NVIDIA(0):     "NULL"
[    11.501] (II) NVIDIA(0): Virtual screen size determined to be 640 x 480
[    11.501] (WW) NVIDIA(0): Unable to get display device for DPI computation.
[    11.501] (==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
[    11.502] (--) intel(G0): Integrated Graphics Chipset: Intel(R) HD Graphics 4600
[    11.502] (--) intel(G0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2, avx, avx2; using a maximum of 4 threads
[    11.502] (==) intel(G0): Depth 24, (--) framebuffer bpp 32
[    11.502] (==) intel(G0): RGB weight 888
[    11.502] (==) intel(G0): Default visual is TrueColor
[    11.502] (**) intel(G0): Option "AccelMethod" "SNA"
[    11.502] (II) intel(G0): Output eDP1 has no monitor section
[    11.502] (--) intel(G0): Found backlight control interface acpi_video0 (type 'firmware') for output eDP1
[    11.502] (II) intel(G0): Enabled output eDP1
[    11.502] (II) intel(G0): Output VGA1 has no monitor section
[    11.502] (II) intel(G0): Enabled output VGA1
[    11.502] (II) intel(G0): Output DP1 has no monitor section
[    11.502] (II) intel(G0): Enabled output DP1
[    11.502] (II) intel(G0): Output HDMI1 has no monitor section
[    11.502] (II) intel(G0): Enabled output HDMI1
[    11.502] (II) intel(G0): Output HDMI2 has no monitor section
[    11.502] (II) intel(G0): Enabled output HDMI2
[    11.502] (--) intel(G0): Using a maximum size of 64x64 for hardware cursors
[    11.502] (II) intel(G0): Output VIRTUAL1 has no monitor section
[    11.502] (II) intel(G0): Enabled output VIRTUAL1
[    11.502] (==) intel(G0): TearFree disabled
[    11.502] (==) intel(G0): DPI set to (96, 96)
[    11.502] (II) Loading sub module "dri2"
[    11.502] (II) LoadModule: "dri2"
[    11.502] (II) Module "dri2" already built-in
[    11.502] (II) Loading sub module "present"
[    11.502] (II) LoadModule: "present"
[    11.503] (WW) Warning, couldn't open module present
[    11.503] (II) UnloadModule: "present"
[    11.503] (II) Unloading present
[    11.503] (EE) intel: Failed to load module "present" (module does not exist, 0)
[    11.506] (--) Depth 24 pixmap format is 32 bpp
[    11.509] (II) intel(G0): SNA initialized with Haswell (gen7.5, gt2) backend
[    11.509] (==) intel(G0): Backing store enabled
[    11.509] (==) intel(G0): Silken mouse enabled
[    11.509] (II) intel(G0): HW Cursor enabled
[    11.509] (II) intel(G0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    11.509] (==) intel(G0): DPMS enabled
[    11.509] (==) intel(G0): Display hotplug detection enabled
[    11.510] (II) intel(G0): [DRI2] Setup complete
[    11.510] (II) intel(G0): [DRI2]   DRI driver: i965
[    11.510] (II) intel(G0): [DRI2]   VDPAU driver: va_gl
[    11.510] (II) intel(G0): direct rendering: DRI2 enabled
[    11.510] (WW) intel(G0): Option "AllowEmptyInitialConfiguration" is not used
[    11.510] (WW) intel(G0): Option "IgnoreDisplayDevices" is not used
[    11.510] (II) NVIDIA: Using 3072.00 MB of virtual memory for indirect memory
[    11.510] (II) NVIDIA:     access.
[    11.516] (II) NVIDIA(0): Setting mode "NULL"
[    11.529] (II) NVIDIA(0): Built-in logo is bigger than the screen.
[    11.529] Loading extension NV-GLX
[    11.532] (==) NVIDIA(0): Disabling shared memory pixmaps
[    11.532] (==) NVIDIA(0): Backing store enabled
[    11.532] (==) NVIDIA(0): Silken mouse enabled
[    11.532] (==) NVIDIA(0): DPMS enabled
[    11.532] Loading extension NV-CONTROL
[    11.532] (II) Loading sub module "dri2"
[    11.532] (II) LoadModule: "dri2"
[    11.532] (II) Module "dri2" already built-in
[    11.532] (II) NVIDIA(0): [DRI2] Setup complete
[    11.532] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[    11.532] (--) RandR disabled
[    11.536] (II) SELinux: Disabled on system
[    11.536] (II) Initializing extension GLX
[    12.603] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    12.605] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    12.605] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    12.605] (II) LoadModule: "evdev"
[    12.605] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    12.606] (II) Module evdev: vendor="X.Org Foundation"
[    12.606]     compiled for 1.15.0, module version = 2.8.2
[    12.606]     Module class: X.Org XInput Driver
[    12.606]     ABI class: X.Org XInput driver, version 20.0
[    12.606] (II) Using input driver 'evdev' for 'Power Button'
[    12.606] (**) Power Button: always reports core events
[    12.606] (**) evdev: Power Button: Device: "/dev/input/event2"
[    12.606] (--) evdev: Power Button: Vendor 0 Product 0x1
[    12.606] (--) evdev: Power Button: Found keys
[    12.606] (II) evdev: Power Button: Configuring as keyboard
[    12.606] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    12.606] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    12.606] (**) Option "xkb_rules" "evdev"
[    12.606] (**) Option "xkb_model" "pc105"
[    12.606] (**) Option "xkb_layout" "fr"
[    12.608] (II) XKB: reuse xkmfile /var/lib/xkb/server-1CA37FD61409D6C1EDB80880DF2DB1A574556A6A.xkm
[    12.609] (II) config/udev: Adding input device Video Bus (/dev/input/event8)
[    12.609] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    12.609] (II) Using input driver 'evdev' for 'Video Bus'
[    12.609] (**) Video Bus: always reports core events
[    12.609] (**) evdev: Video Bus: Device: "/dev/input/event8"
[    12.609] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    12.609] (--) evdev: Video Bus: Found keys
[    12.609] (II) evdev: Video Bus: Configuring as keyboard
[    12.609] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input9/event8"
[    12.609] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    12.609] (**) Option "xkb_rules" "evdev"
[    12.609] (**) Option "xkb_model" "pc105"
[    12.609] (**) Option "xkb_layout" "fr"
[    12.609] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    12.609] (II) No input driver specified, ignoring this device.
[    12.609] (II) This device may have been added with another device file.
[    12.609] (II) config/udev: Adding input device Video Bus (/dev/input/event7)
[    12.609] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    12.609] (II) Using input driver 'evdev' for 'Video Bus'
[    12.609] (**) Video Bus: always reports core events
[    12.609] (**) evdev: Video Bus: Device: "/dev/input/event7"
[    12.609] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    12.609] (--) evdev: Video Bus: Found keys
[    12.609] (II) evdev: Video Bus: Configuring as keyboard
[    12.609] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:45/LNXVIDEO:00/input/input8/event7"
[    12.609] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 8)
[    12.609] (**) Option "xkb_rules" "evdev"
[    12.609] (**) Option "xkb_model" "pc105"
[    12.609] (**) Option "xkb_layout" "fr"
[    12.610] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    12.610] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    12.610] (II) Using input driver 'evdev' for 'Power Button'
[    12.610] (**) Power Button: always reports core events
[    12.610] (**) evdev: Power Button: Device: "/dev/input/event1"
[    12.610] (--) evdev: Power Button: Vendor 0 Product 0x1
[    12.610] (--) evdev: Power Button: Found keys
[    12.610] (II) evdev: Power Button: Configuring as keyboard
[    12.610] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[    12.610] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 9)
[    12.610] (**) Option "xkb_rules" "evdev"
[    12.610] (**) Option "xkb_model" "pc105"
[    12.610] (**) Option "xkb_layout" "fr"
[    12.610] (II) config/udev: Adding drm device (/dev/dri/card1) card1 /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0/drm/card1
[    12.610] (II) config/udev: Ignoring already known drm device (/dev/dri/card1)
[    12.610] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:02.0/drm/card0
[    12.610] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    12.610] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=3 (/dev/input/event12)
[    12.610] (II) No input driver specified, ignoring this device.
[    12.610] (II) This device may have been added with another device file.
[    12.610] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=7 (/dev/input/event11)
[    12.610] (II) No input driver specified, ignoring this device.
[    12.610] (II) This device may have been added with another device file.
[    12.610] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=8 (/dev/input/event10)
[    12.610] (II) No input driver specified, ignoring this device.
[    12.610] (II) This device may have been added with another device file.
[    12.610] (II) config/udev: Adding input device Logitech G500 (/dev/input/event4)
[    12.610] (**) Logitech G500: Applying InputClass "evdev pointer catchall"
[    12.610] (II) Using input driver 'evdev' for 'Logitech G500'
[    12.610] (**) Logitech G500: always reports core events
[    12.610] (**) evdev: Logitech G500: Device: "/dev/input/event4"
[    12.610] (--) evdev: Logitech G500: Vendor 0x46d Product 0xc068
[    12.610] (--) evdev: Logitech G500: Found 20 mouse buttons
[    12.610] (--) evdev: Logitech G500: Found scroll wheel(s)
[    12.610] (--) evdev: Logitech G500: Found relative axes
[    12.610] (--) evdev: Logitech G500: Found x and y relative axes
[    12.610] (II) evdev: Logitech G500: Configuring as mouse
[    12.611] (II) evdev: Logitech G500: Adding scrollwheel support
[    12.611] (**) evdev: Logitech G500: YAxisMapping: buttons 4 and 5
[    12.611] (**) evdev: Logitech G500: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    12.611] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-2/3-2:1.0/input/input6/event4"
[    12.611] (II) XINPUT: Adding extended input device "Logitech G500" (type: MOUSE, id 10)
[    12.611] (II) evdev: Logitech G500: initialized for relative axes.
[    12.611] (**) Logitech G500: (accel) keeping acceleration scheme 1
[    12.611] (**) Logitech G500: (accel) acceleration profile 0
[    12.611] (**) Logitech G500: (accel) acceleration factor: 2.000
[    12.611] (**) Logitech G500: (accel) acceleration threshold: 4
[    12.611] (II) config/udev: Adding input device Logitech G500 (/dev/input/mouse0)
[    12.611] (II) No input driver specified, ignoring this device.
[    12.611] (II) This device may have been added with another device file.
[    12.611] (II) config/udev: Adding input device Logitech G500 (/dev/input/event5)
[    12.611] (**) Logitech G500: Applying InputClass "evdev keyboard catchall"
[    12.611] (II) Using input driver 'evdev' for 'Logitech G500'
[    12.611] (**) Logitech G500: always reports core events
[    12.611] (**) evdev: Logitech G500: Device: "/dev/input/event5"
[    12.611] (--) evdev: Logitech G500: Vendor 0x46d Product 0xc068
[    12.611] (--) evdev: Logitech G500: Found 1 mouse buttons
[    12.611] (--) evdev: Logitech G500: Found scroll wheel(s)
[    12.611] (--) evdev: Logitech G500: Found relative axes
[    12.611] (II) evdev: Logitech G500: Forcing relative x/y axes to exist.
[    12.611] (--) evdev: Logitech G500: Found absolute axes
[    12.611] (II) evdev: Logitech G500: Forcing absolute x/y axes to exist.
[    12.611] (--) evdev: Logitech G500: Found keys
[    12.611] (II) evdev: Logitech G500: Configuring as mouse
[    12.611] (II) evdev: Logitech G500: Configuring as keyboard
[    12.611] (II) evdev: Logitech G500: Adding scrollwheel support
[    12.611] (**) evdev: Logitech G500: YAxisMapping: buttons 4 and 5
[    12.611] (**) evdev: Logitech G500: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    12.611] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-2/3-2:1.1/input/input7/event5"
[    12.611] (II) XINPUT: Adding extended input device "Logitech G500" (type: KEYBOARD, id 11)
[    12.611] (**) Option "xkb_rules" "evdev"
[    12.611] (**) Option "xkb_model" "pc105"
[    12.611] (**) Option "xkb_layout" "fr"
[    12.611] (II) evdev: Logitech G500: initialized for relative axes.
[    12.611] (WW) evdev: Logitech G500: ignoring absolute axes.
[    12.611] (**) Logitech G500: (accel) keeping acceleration scheme 1
[    12.611] (**) Logitech G500: (accel) acceleration profile 0
[    12.611] (**) Logitech G500: (accel) acceleration factor: 2.000
[    12.611] (**) Logitech G500: (accel) acceleration threshold: 4
[    12.611] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event14)
[    12.611] (II) No input driver specified, ignoring this device.
[    12.611] (II) This device may have been added with another device file.
[    12.611] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event13)
[    12.611] (II) No input driver specified, ignoring this device.
[    12.611] (II) This device may have been added with another device file.
[    12.612] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    12.612] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    12.612] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    12.612] (**) AT Translated Set 2 keyboard: always reports core events
[    12.612] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    12.612] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    12.612] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    12.612] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    12.612] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    12.612] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 12)
[    12.612] (**) Option "xkb_rules" "evdev"
[    12.612] (**) Option "xkb_model" "pc105"
[    12.612] (**) Option "xkb_layout" "fr"
[    12.612] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/event6)
[    12.612] (**) ETPS/2 Elantech Touchpad: Applying InputClass "evdev touchpad catchall"
[    12.612] (**) ETPS/2 Elantech Touchpad: Applying InputClass "touchpad catchall"
[    12.612] (**) ETPS/2 Elantech Touchpad: Applying InputClass "Default clickpad buttons"
[    12.612] (II) LoadModule: "synaptics"
[    12.612] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    12.613] (II) Module synaptics: vendor="X.Org Foundation"
[    12.613]     compiled for 1.15.0, module version = 1.7.4
[    12.613]     Module class: X.Org XInput Driver
[    12.613]     ABI class: X.Org XInput driver, version 20.0
[    12.613] (II) Using input driver 'synaptics' for 'ETPS/2 Elantech Touchpad'
[    12.613] (**) ETPS/2 Elantech Touchpad: always reports core events
[    12.613] (**) Option "Device" "/dev/input/event6"
[    12.640] (II) synaptics: ETPS/2 Elantech Touchpad: found clickpad property
[    12.640] (--) synaptics: ETPS/2 Elantech Touchpad: x-axis range 0 - 3260 (res 33)
[    12.640] (--) synaptics: ETPS/2 Elantech Touchpad: y-axis range 0 - 2119 (res 33)
[    12.640] (--) synaptics: ETPS/2 Elantech Touchpad: pressure range 0 - 255
[    12.640] (--) synaptics: ETPS/2 Elantech Touchpad: finger width range 0 - 15
[    12.640] (--) synaptics: ETPS/2 Elantech Touchpad: buttons: left double triple
[    12.640] (--) synaptics: ETPS/2 Elantech Touchpad: Vendor 0x2 Product 0xe
[    12.640] (**) Option "SoftButtonAreas" "50% 0 82% 0 0 0 0 0"
[    12.640] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[    12.640] (**) ETPS/2 Elantech Touchpad: always reports core events
[    12.652] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input5/event6"
[    12.652] (II) XINPUT: Adding extended input device "ETPS/2 Elantech Touchpad" (type: TOUCHPAD, id 13)
[    12.652] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MinSpeed is now constant deceleration 2.5
[    12.652] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MaxSpeed is now 1.75
[    12.652] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) AccelFactor is now 0.051
[    12.652] (**) ETPS/2 Elantech Touchpad: (accel) keeping acceleration scheme 1
[    12.652] (**) ETPS/2 Elantech Touchpad: (accel) acceleration profile 1
[    12.652] (**) ETPS/2 Elantech Touchpad: (accel) acceleration factor: 2.000
[    12.652] (**) ETPS/2 Elantech Touchpad: (accel) acceleration threshold: 4
[    12.652] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[    12.652] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/mouse1)
[    12.652] (**) ETPS/2 Elantech Touchpad: Ignoring device from InputClass "touchpad ignore duplicates"
[    12.653] (II) config/udev: Adding input device MSI WMI hotkeys (/dev/input/event9)
[    12.653] (**) MSI WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    12.653] (II) Using input driver 'evdev' for 'MSI WMI hotkeys'
[    12.653] (**) MSI WMI hotkeys: always reports core events
[    12.653] (**) evdev: MSI WMI hotkeys: Device: "/dev/input/event9"
[    12.653] (--) evdev: MSI WMI hotkeys: Vendor 0 Product 0
[    12.653] (--) evdev: MSI WMI hotkeys: Found keys
[    12.653] (II) evdev: MSI WMI hotkeys: Configuring as keyboard
[    12.653] (**) Option "config_info" "udev:/sys/devices/virtual/input/input10/event9"
[    12.653] (II) XINPUT: Adding extended input device "MSI WMI hotkeys" (type: KEYBOARD, id 14)
[    12.653] (**) Option "xkb_rules" "evdev"
[    12.653] (**) Option "xkb_model" "pc105"
[    12.653] (**) Option "xkb_layout" "fr"
[    12.655] (II) config/udev: Adding input device Logitech G500 (/dev/input/mouse0)
[    12.655] (II) No input driver specified, ignoring this device.
[    12.655] (II) This device may have been added with another device file.
[    12.655] (WW) config/udev: device Logitech G500 already added. Ignoring.
[    12.655] (WW) config/udev: device Logitech G500 already added. Ignoring.
[    12.697] (II) intel(G0): EDID vendor "MEI", prod id 38562
[    12.697] (II) intel(G0): Using EDID range info for horizontal sync
[    12.697] (II) intel(G0): Using EDID range info for vertical refresh
[    12.697] (II) intel(G0): Printing DDC gathered Modelines:
[    12.697] (II) intel(G0): Modeline "2880x1620"x0.0  302.50  2880 2924 2928 3076  1620 1629 1630 1640 +hsync +vsync (98.3 kHz eP)
[    12.697] (II) intel(G0): Modeline "2880x1620"x0.0  302.50  2880 2924 2928 3076  1620 1629 1630 1967 +hsync +vsync (98.3 kHz e)
[    12.712] reporting 4 6 23 195
[    12.728] have a master to look out for
[    12.728] adjust shatters 0 2880
[    12.731] need to create shared pixmap 1(II) intel(G0): switch to mode 2880x1620@60.0 on eDP1 using pipe 0, position (0, 0), rotation normal, reflection none
[    12.748] reporting 4 6 23 195
[    12.764] reporting 4 6 23 195
[    12.764] have a master to look out for
[    12.765] need to create shared pixmap 1reporting 4 6 23 195
[    12.811] have a master to look out for
[    12.811] adjust shatters 0 2880
[    12.814] need to create shared pixmap 1(II) intel(G0): switch to mode 2880x1620@60.0 on eDP1 using pipe 0, position (0, 0), rotation normal, reflection none
[    12.945] reporting 4 6 23 195
[    13.146] reporting 4 6 23 195
[    13.164] reporting 4 6 23 195
[    13.164] reporting 4 6 23 195
[    13.426] reporting 4 6 23 195
[    13.448] reporting 4 6 23 195
[    13.518] reporting 4 6 23 195
[    13.518] reporting 4 6 23 195
[    13.519] reporting 4 6 23 195
[    13.532] reporting 4 6 23 195
[    13.533] reporting 4 6 23 195
[    13.580] reporting 4 6 23 195
[    13.637] reporting 4 6 23 195
[    16.952] reporting 4 6 23 195
[    16.968] reporting 4 6 23 195
[    23.729] (EE) intel(G0): sna_mode_check: invalid state found on pipe 0, disabling CRTC:3
[    23.760] reporting 4 6 23 195
[    23.824] (II) NVIDIA(0): Setting mode "NULL"
[    23.840] (II) intel(G0): switch to mode 2880x1620@60.0 on eDP1 using pipe 0, position (0, 0), rotation normal, reflection none
[    23.878] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[    31.180] reporting 4 6 23 195
[    31.181] reporting 4 6 23 195
[    31.200] reporting 4 6 23 195
[    31.249] reporting 4 6 23 195
[    31.250] reporting 4 6 23 195
[    31.252] reporting 4 6 23 195
[    31.261] reporting 4 6 23 195
[    31.312] reporting 4 6 23 195
[    31.313] reporting 4 6 23 195
[    31.324] reporting 4 6 23 195
[    31.340] (II) XKB: reuse xkmfile /var/lib/xkb/server-1CA37FD61409D6C1EDB80880DF2DB1A574556A6A.xkm
[    31.362] reporting 4 6 23 195
[    31.416] reporting 4 6 23 195
[    31.434] have a master to look out for
[    31.435] need to create shared pixmap 1have a master to look out for
[    32.469] adjust shatters 0 1920
[    32.471] need to create shared pixmap 1(II) intel(G0): switch to mode 1920x1080@59.9 on eDP1 using pipe 0, position (0, 0), rotation normal, reflection none
[    33.044] reporting 4 6 23 195
[    33.045] reporting 4 6 23 195
[    33.045] reporting 4 6 23 195
[    33.045] reporting 4 6 23 195
[    33.046] reporting 4 6 23 195
[    33.046] reporting 4 6 23 195
[    33.046] reporting 4 6 23 195
[    33.046] reporting 4 6 23 195
[    33.046] reporting 4 6 23 195
[    33.048] reporting 4 6 23 195
[    33.048] reporting 4 6 23 195
[    33.050] reporting 4 6 23 195
[    33.050] reporting 4 6 23 195
[    33.051] reporting 4 6 23 195
[    33.051] reporting 4 6 23 195
[    33.052] reporting 4 6 23 195
[    33.052] reporting 4 6 23 195
[    33.052] reporting 4 6 23 195
[    33.058] reporting 4 6 23 195
[    33.058] reporting 4 6 23 195
[    33.059] reporting 4 6 23 195
[    33.062] reporting 4 6 23 195
[    33.077] reporting 4 6 23 195
[    33.086] reporting 4 6 23 195
[    33.088] reporting 4 6 23 195
[    33.089] reporting 4 6 23 195
[    33.089] reporting 4 6 23 195
[    33.089] reporting 4 6 23 195
[    33.089] reporting 4 6 23 195
[    33.090] reporting 4 6 23 195
[    33.090] reporting 4 6 23 195
[    33.090] reporting 4 6 23 195
[    33.132] reporting 4 6 23 195
[    33.134] reporting 4 6 23 195
[    33.140] reporting 4 6 23 195
[    33.141] reporting 4 6 23 195
[    33.142] reporting 4 6 23 195
[    33.143] reporting 4 6 23 195
[    33.145] reporting 4 6 23 195
[    33.145] reporting 4 6 23 195
[    33.147] reporting 4 6 23 195
[    33.147] reporting 4 6 23 195
[    33.164] reporting 4 6 23 195
[    33.279] reporting 4 6 23 195
[    33.308] (II) XKB: reuse xkmfile /var/lib/xkb/server-4CCA0437B0B5529C7C44C7931A7373D005909F34.xkm
[    33.319] (II) XKB: reuse xkmfile /var/lib/xkb/server-4CCA0437B0B5529C7C44C7931A7373D005909F34.xkm
[    33.343] reporting 4 6 23 195
[    33.344] reporting 4 6 23 195
[    33.356] reporting 4 6 23 195
[    33.356] reporting 4 6 23 195
[    33.358] reporting 4 6 23 195
[    33.516] reporting 4 6 23 195
[    33.535] reporting 4 6 23 195
[    33.542] reporting 4 6 23 195
[    33.608] reporting 4 6 23 195
[    33.624] reporting 4 6 23 195
[    33.626] reporting 4 6 23 195
[    33.692] reporting 4 6 23 195
[    33.772] reporting 4 6 23 195
[    34.364] (II) XKB: reuse xkmfile /var/lib/xkb/server-500973B6F09A52700C4E9B62920EB235C5BB3956.xkm
[    37.065] reporting 4 6 23 195
[    48.214] reporting 4 6 23 195
[    48.216] reporting 4 6 23 195
[    48.373] reporting 4 6 23 195
[    48.385] reporting 4 6 23 195
[    63.229] reporting 4 6 23 195
[    93.239] reporting 4 6 23 195
[   312.764] reporting 4 6 23 195

```

What i find most strange are the lines :
```
[    11.501] (--) NVIDIA(0): Valid display device(s) on GeForce GTX 970M at PCI:1:0:0
[    11.501] (--) NVIDIA(0):     none
[    11.501] (II) NVIDIA(0): Validated MetaModes:
[    11.501] (II) NVIDIA(0):     "NULL"
[    11.501] (II) NVIDIA(0): Virtual screen size determined to be 640 x 480
```

Regarding the OpenGL code issues i mentioned in the opening post, it seems I am to blame for not conforming to the specification.
Until then, the nvidia drivers were pretty forgiving, but this seems to have changed with recent updates.

---

### Post by startas on 2015-01-31
Yes, this problem is general linux problem with nvidia optimus when you are trying to install nvidia prime drivers. However, i was able to get bumblebee with nvidia 343 drivers to work in manjaro linux. Is there a way in ubuntu to install bumblebee with nvidia 346.35 drivers ?

---

### Post by Tim_Hawkins on 2015-02-01
> **alexandre19 said:**
> Here is the Xorg log right after reboot :


Regarding the OpenGL code issues i mentioned in the opening post, it seems I am to blame for not conforming to the specification.
Until then, the nvidia drivers were pretty forgiving, but this seems to have changed with recent updates.

The last kernel update broke this, if you go into the advanced boot menu and choose the last but one kernel to boot with, it works fine. 

I updated this morning and it failed on first reboot. I have an ASUS N500JK with the 970M Optimus.

---

### Post by startas on 2015-02-01
If you need bumblebee, here is a guide : [http://ubuntuforums.org/showthread.php?t=2262882&p=13219529#post13219529](http://ubuntuforums.org/showthread.php?t=2262882&p=13219529#post13219529)

---

