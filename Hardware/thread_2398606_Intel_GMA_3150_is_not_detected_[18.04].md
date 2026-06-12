---
title: "Intel GMA 3150 is not detected [18.04]"
date: 2018-08-14
forum: Hardware
---

### Post by boo-deal-nic on 2018-08-14
Can't change screen res higher then 1024x768.

WebGL Report says on old video driver.

WebGL Test:
Hmm.  While your browser seems to support WebGL, it is disabled or  unavailable.
If possible, please ensure that you are running the latest  drivers for your video card.

HardInfo:

-Display-
Resolution        : 1024x768 pixels
Vendor        : The X.Org Foundation
Version        : 1.19.6
Current Display Name        : :0.0
-Monitors-
Monitor 0        : 1024x768 pixels
-OpenGL-
Vendor        : Intel Open Source Technology Center
Renderer        : Mesa DRI Intel(R) Pineview 
Version        : 1.4 Mesa 18.0.5
Direct Rendering        : Yes
-Extensions-
Composite
DAMAGE
DOUBLE-BUFFER
DPMS
DRI2
GLX
Generic Event Extension
MIT-SCREEN-SAVER
MIT-SHM
Present
RANDR
RECORD
RENDER
SECURITY
SGI-GLX
SHAPE
SYNC
X-Resource
XC-MISC
XFIXES
XFree86-DGA
XFree86-VidModeExtension
XINERAMA
XInputExtension
XKEYBOARD
XTEST
XVideo
XVideo-MotionCompensation
default screen number:    0

TERMINAL:

boo@boo-pc:~$ sudo lshw -C video
[sudo] password for boo: 
  *-display                 
       description: VGA compatible controller
       product: Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:f0200000-f027ffff ioport:20c0(size=8) memory:e0000000-efffffff memory:f0100000-f01fffff memory:c0000-dffff

glxgears - WORKS

In windows 7 with drivers everything is OK.
I know Intel's drivers build in ubuntu, but with no effect.

Only thing i found is [https://01.org:](https://01.org:)
[https://01.org/linuxgraphics/downloads/2018q1-intel-graphics-stack-recipe](https://01.org/linuxgraphics/downloads/2018q1-intel-graphics-stack-recipe)
i guess its [Libva - 2.1.0]("https://github.com/01org/libva/releases/download/2.1.0/libva-2.1.0.tar.bz2") but i don't know how to compile it.

The easier way to solve it the better.
xrandr or something is difficult.

i want simple linux... please.

Lubuntu with compton and papirus icon and victory theme is so cute... and still fast.

---

### Post by Yellow Pasque on 2018-08-14
[https://www.phoronix.com/scan.php?page=news_item&px=Mesa-i915-OpenGL-2-Drop](https://www.phoronix.com/scan.php?page=news_item&px=Mesa-i915-OpenGL-2-Drop)

In other words,
```
sudo apt-get install driconf
driconf
```

Check the options for ARB_occlusion_query and ARB_fragment_shader, save the changes and log out/in and check glxinfo. It should report OpenGL 2.1 and hopefully, that will allow WebGL to work. Don't count on a smooth experience if it does work though.

> I guess its Libva - 2.1.0 but i don't know how to compile it.

That seems irrelevant to a WebGL issue.

> Can't change screen res higher then 1024x768.

If it's still not working after making the change above, please copy/paste your /var/log/Xorg.0.log file. Use code tags as it's a lot of text.

---

### Post by boo-deal-nic on 2018-08-17
When driconf starts next window appears:
Could not detect any configurable direct-rendering capable devices. DRIconf will be started in expert mode.
In terminal message:
Screen "0" is not direct rendering capable.
screen driconf
[https://drive.google.com/open?id=136z8mGbUbzPuJQgyDlW59zhXnWL0UsgO](https://drive.google.com/open?id=136z8mGbUbzPuJQgyDlW59zhXnWL0UsgO)

Xorg.0.log

```
[  1496.995] 
X.Org X Server 1.19.6
Release Date: 2017-12-20
[  1496.995] X Protocol Version 11, Revision 0
[  1496.995] Build Operating System: Linux 4.4.0-119-generic x86_64 Ubuntu
[  1496.995] Current Operating System: Linux boo-pc 4.15.0-32-generic #35-Ubuntu SMP Fri Aug 10 17:58:07 UTC 2018 x86_64
[  1496.995] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.15.0-32-generic root=UUID=b50b28d9-ade8-461b-8906-475cda3dae35 ro quiet splash vt.handoff=1
[  1496.995] Build Date: 13 April 2018  08:07:36PM
[  1496.995] xorg-server 2:1.19.6-1ubuntu4 (For technical support please see http://www.ubuntu.com/support) 
[  1496.995] Current version of pixman: 0.34.0
[  1496.996]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[  1496.996] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  1496.996] (==) Log file: "/var/log/Xorg.1.log", Time: Wed Aug 15 19:43:44 2018
[  1496.997] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  1496.997] (==) No Layout section.  Using the first Screen section.
[  1496.997] (==) No screen section available. Using defaults.
[  1496.997] (**) |-->Screen "Default Screen Section" (0)
[  1496.997] (**) |   |-->Monitor "<default monitor>"
[  1496.999] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[  1496.999] (==) Automatically adding devices
[  1496.999] (==) Automatically enabling devices
[  1496.999] (==) Automatically adding GPU devices
[  1496.999] (==) Automatically binding GPU devices
[  1496.999] (==) Max clients allowed: 256, resource mask: 0x1fffff
[  1496.999] (WW) The directory "/usr/share/fonts/X11/misc" does not exist.
[  1496.999]     Entry deleted from font path.
[  1496.999] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  1497.000]     Entry deleted from font path.
[  1497.000] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[  1497.000]     Entry deleted from font path.
[  1497.000] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[  1497.000]     Entry deleted from font path.
[  1497.000] (WW) The directory "/usr/share/fonts/X11/Type1" does not exist.
[  1497.000]     Entry deleted from font path.
[  1497.000] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[  1497.000]     Entry deleted from font path.
[  1497.000] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[  1497.000]     Entry deleted from font path.
[  1497.000] (==) FontPath set to:
    built-ins
[  1497.000] (==) ModulePath set to "/usr/lib/xorg/modules"
[  1497.000] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[  1497.000] (II) Loader magic: 0x55c3cfabf020
[  1497.000] (II) Module ABI versions:
[  1497.000]     X.Org ANSI C Emulation: 0.4
[  1497.000]     X.Org Video Driver: 23.0
[  1497.000]     X.Org XInput driver : 24.1
[  1497.000]     X.Org Server Extension : 10.0
[  1497.002] (++) using VT number 8

[  1497.002] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
[  1497.005] (II) xfree86: Adding drm device (/dev/dri/card0)
[  1497.005] (EE) /dev/dri/card0: failed to set DRM interface version 1.4: Permission denied
[  1497.014] (--) PCI:*(0:0:2:0) 8086:a001:8086:4f4d rev 2, Mem @ 0xf0200000/524288, 0xe0000000/268435456, 0xf0100000/1048576, I/O @ 0x000020c0/8, BIOS @ 0x????????/131072
[  1497.014] (II) LoadModule: "glx"
[  1497.015] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[  1497.018] (II) Module glx: vendor="X.Org Foundation"
[  1497.018]     compiled for 1.19.6, module version = 1.0.0
[  1497.018]     ABI class: X.Org Server Extension, version 10.0
[  1497.019] (==) Matched intel as autoconfigured driver 0
[  1497.019] (==) Matched modesetting as autoconfigured driver 1
[  1497.019] (==) Matched fbdev as autoconfigured driver 2
[  1497.019] (==) Matched vesa as autoconfigured driver 3
[  1497.019] (==) Assigned the driver to the xf86ConfigLayout
[  1497.019] (II) LoadModule: "intel"
[  1497.019] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[  1497.020] (II) Module intel: vendor="X.Org Foundation"
[  1497.020]     compiled for 1.19.5, module version = 2.99.917
[  1497.021]     Module class: X.Org Video Driver
[  1497.021]     ABI class: X.Org Video Driver, version 23.0
[  1497.021] (II) LoadModule: "modesetting"
[  1497.021] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[  1497.021] (II) Module modesetting: vendor="X.Org Foundation"
[  1497.021]     compiled for 1.19.6, module version = 1.19.6
[  1497.022]     Module class: X.Org Video Driver
[  1497.022]     ABI class: X.Org Video Driver, version 23.0
[  1497.022] (II) LoadModule: "fbdev"
[  1497.022] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[  1497.022] (II) Module fbdev: vendor="X.Org Foundation"
[  1497.022]     compiled for 1.19.3, module version = 0.4.4
[  1497.022]     Module class: X.Org Video Driver
[  1497.023]     ABI class: X.Org Video Driver, version 23.0
[  1497.023] (II) LoadModule: "vesa"
[  1497.023] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[  1497.023] (II) Module vesa: vendor="X.Org Foundation"
[  1497.023]     compiled for 1.19.3, module version = 2.3.4
[  1497.023]     Module class: X.Org Video Driver
[  1497.023]     ABI class: X.Org Video Driver, version 23.0
[  1497.023] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[  1497.025] (II) intel: Driver for Intel(R) HD Graphics
[  1497.025] (II) intel: Driver for Intel(R) Iris(TM) Graphics
[  1497.025] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics
[  1497.025] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[  1497.026] (II) FBDEV: driver for framebuffer: fbdev
[  1497.026] (II) VESA: driver for VESA chipsets: vesa
[  1497.256] (II) intel(0): Using Kernel Mode Setting driver: i915, version 1.6.0 20171023
[  1497.256] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.99.917+git20171229-1 (Timo Aaltonen <tjaalton@debian.org>)
[  1497.256] (II) intel(0): SNA compiled for use with valgrind
[  1497.276] (WW) Falling back to old probe method for modesetting
[  1497.276] (WW) Falling back to old probe method for fbdev
[  1497.277] (II) Loading sub module "fbdevhw"
[  1497.277] (II) LoadModule: "fbdevhw"
[  1497.277] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[  1497.278] (II) Module fbdevhw: vendor="X.Org Foundation"
[  1497.278]     compiled for 1.19.6, module version = 0.0.2
[  1497.278]     ABI class: X.Org Video Driver, version 23.0
[  1497.278] (WW) Falling back to old probe method for vesa
[  1497.279] (--) intel(0): Integrated Graphics Chipset: Intel(R) Pineview G
[  1497.279] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3; using a maximum of 2 threads
[  1497.280] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[  1497.280] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[  1497.280] (==) intel(0): RGB weight 888
[  1497.280] (==) intel(0): Default visual is TrueColor
[  1497.281] (II) intel(0): Output VGA1 has no monitor section
[  1497.282] (II) intel(0): Enabled output VGA1
[  1497.282] (--) intel(0): Using a maximum size of 256x256 for hardware cursors
[  1497.283] (II) intel(0): Output VIRTUAL1 has no monitor section
[  1497.283] (II) intel(0): Enabled output VIRTUAL1
[  1497.283] (--) intel(0): Output VGA1 using initial mode 1024x768 on pipe 0
[  1497.283] (==) intel(0): TearFree disabled
[  1497.283] (==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
[  1497.283] (==) intel(0): DPI set to (96, 96)
[  1497.283] (II) Loading sub module "dri3"
[  1497.283] (II) LoadModule: "dri3"
[  1497.284] (II) Module "dri3" already built-in
[  1497.284] (II) Loading sub module "dri2"
[  1497.284] (II) LoadModule: "dri2"
[  1497.284] (II) Module "dri2" already built-in
[  1497.284] (II) Loading sub module "present"
[  1497.284] (II) LoadModule: "present"
[  1497.284] (II) Module "present" already built-in
[  1497.284] (II) UnloadModule: "modesetting"
[  1497.284] (II) Unloading modesetting
[  1497.284] (II) UnloadModule: "fbdev"
[  1497.285] (II) Unloading fbdev
[  1497.285] (II) UnloadSubModule: "fbdevhw"
[  1497.285] (II) Unloading fbdevhw
[  1497.285] (II) UnloadModule: "vesa"
[  1497.285] (II) Unloading vesa
[  1497.286] (==) Depth 24 pixmap format is 32 bpp
[  1497.286] (II) intel(0): SNA initialized with Alviso (gen3) backend
[  1497.286] (==) intel(0): Backing store enabled
[  1497.286] (==) intel(0): Silken mouse enabled
[  1497.286] (II) intel(0): HW Cursor enabled
[  1497.286] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[  1497.287] (==) intel(0): DPMS enabled
[  1497.288] (==) intel(0): Display hotplug detection enabled
[  1497.288] (II) intel(0): [XvMC] i915_xvmc driver initialized.
[  1497.288] (II) intel(0): [DRI2] Setup complete
[  1497.288] (II) intel(0): [DRI2]   DRI driver: i915
[  1497.288] (II) intel(0): [DRI2]   VDPAU driver: va_gl
[  1497.288] (II) intel(0): direct rendering: DRI2 enabled
[  1497.288] (II) intel(0): hardware support for Present enabled
[  1497.288] (--) RandR disabled
[  1497.304] (II) SELinux: Disabled on system
[  1497.332] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[  1497.332] (II) AIGLX: enabled GLX_ARB_create_context
[  1497.332] (II) AIGLX: enabled GLX_ARB_create_context_profile
[  1497.332] (II) AIGLX: enabled GLX_EXT_create_context_es{,2}_profile
[  1497.332] (II) AIGLX: enabled GLX_INTEL_swap_event
[  1497.332] (II) AIGLX: enabled GLX_SGI_swap_control
[  1497.332] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[  1497.332] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[  1497.332] (II) AIGLX: enabled GLX_EXT_fbconfig_packed_float
[  1497.332] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[  1497.333] (II) AIGLX: Loaded and initialized i915
[  1497.333] (II) GLX: Initialized DRI2 GL provider for screen 0
[  1497.342] (II) intel(0): switch to mode 1024x768@60.0 on VGA1 using pipe 0, position (0, 0), rotation normal, reflection none
[  1497.347] (II) intel(0): Setting screen physical size to 270 x 203
[  1497.497] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[  1497.498] (**) Power Button: Applying InputClass "libinput keyboard catchall"
[  1497.498] (II) LoadModule: "libinput"
[  1497.498] (II) Loading /usr/lib/xorg/modules/input/libinput_drv.so
[  1497.504] (II) Module libinput: vendor="X.Org Foundation"
[  1497.504]     compiled for 1.19.6, module version = 0.27.1
[  1497.504]     Module class: X.Org XInput Driver
[  1497.504]     ABI class: X.Org XInput driver, version 24.1
[  1497.505] (II) Using input driver 'libinput' for 'Power Button'
[  1497.505] (**) Power Button: always reports core events
[  1497.505] (**) Option "Device" "/dev/input/event1"
[  1497.505] (**) Option "_source" "server/udev"
[  1497.507] (II) event1  - Power Button: is tagged by udev as: Keyboard
[  1497.507] (II) event1  - Power Button: device is a keyboard
[  1497.507] (II) event1  - Power Button: device removed
[  1497.528] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[  1497.528] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[  1497.528] (**) Option "xkb_model" "pc105"
[  1497.528] (**) Option "xkb_layout" "us"
[  1497.530] (II) event1  - Power Button: is tagged by udev as: Keyboard
[  1497.531] (II) event1  - Power Button: device is a keyboard
[  1497.533] (II) config/udev: Adding input device Sleep Button (/dev/input/event0)
[  1497.533] (**) Sleep Button: Applying InputClass "libinput keyboard catchall"
[  1497.533] (II) Using input driver 'libinput' for 'Sleep Button'
[  1497.533] (**) Sleep Button: always reports core events
[  1497.533] (**) Option "Device" "/dev/input/event0"
[  1497.533] (**) Option "_source" "server/udev"
[  1497.535] (II) event0  - Sleep Button: is tagged by udev as: Keyboard
[  1497.535] (II) event0  - Sleep Button: device is a keyboard
[  1497.535] (II) event0  - Sleep Button: device removed
[  1497.552] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0/event0"
[  1497.552] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 7)
[  1497.552] (**) Option "xkb_model" "pc105"
[  1497.552] (**) Option "xkb_layout" "us"
[  1497.554] (II) event0  - Sleep Button: is tagged by udev as: Keyboard
[  1497.554] (II) event0  - Sleep Button: device is a keyboard
[  1497.555] (II) config/udev: Adding drm device (/dev/dri/card0)
[  1497.555] (II) xfree86: Adding drm device (/dev/dri/card0)
[  1497.555] (EE) /dev/dri/card0: failed to set DRM interface version 1.4: Permission denied
[  1497.557] (II) config/udev: Adding input device HDA Intel Front Mic (/dev/input/event3)
[  1497.557] (II) No input driver specified, ignoring this device.
[  1497.557] (II) This device may have been added with another device file.
[  1497.559] (II) config/udev: Adding input device HDA Intel Rear Mic (/dev/input/event4)
[  1497.559] (II) No input driver specified, ignoring this device.
[  1497.559] (II) This device may have been added with another device file.
[  1497.560] (II) config/udev: Adding input device HDA Intel Line (/dev/input/event5)
[  1497.561] (II) No input driver specified, ignoring this device.
[  1497.561] (II) This device may have been added with another device file.
[  1497.562] (II) config/udev: Adding input device HDA Intel Line Out (/dev/input/event6)
[  1497.562] (II) No input driver specified, ignoring this device.
[  1497.562] (II) This device may have been added with another device file.
[  1497.564] (II) config/udev: Adding input device HDA Intel Front Headphone (/dev/input/event7)
[  1497.564] (II) No input driver specified, ignoring this device.
[  1497.564] (II) This device may have been added with another device file.
[  1497.566] (II) config/udev: Adding input device YSTEK G Mouse (/dev/input/event2)
[  1497.567] (**) YSTEK G Mouse: Applying InputClass "libinput pointer catchall"
[  1497.567] (II) Using input driver 'libinput' for 'YSTEK G Mouse'
[  1497.567] (**) YSTEK G Mouse: always reports core events
[  1497.567] (**) Option "Device" "/dev/input/event2"
[  1497.567] (**) Option "_source" "server/udev"
[  1497.629] (II) event2  - YSTEK G Mouse: is tagged by udev as: Mouse
[  1497.629] (II) event2  - YSTEK G Mouse: device is a pointer
[  1497.629] (II) event2  - YSTEK G Mouse: device removed
[  1497.660] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/0003:276D:1160.0001/input/input2/event2"
[  1497.660] (II) XINPUT: Adding extended input device "YSTEK G Mouse" (type: MOUSE, id 8)
[  1497.661] (**) Option "AccelerationScheme" "none"
[  1497.661] (**) YSTEK G Mouse: (accel) selected scheme none/0
[  1497.661] (**) YSTEK G Mouse: (accel) acceleration factor: 2.000
[  1497.661] (**) YSTEK G Mouse: (accel) acceleration threshold: 4
[  1497.721] (II) event2  - YSTEK G Mouse: is tagged by udev as: Mouse
[  1497.721] (II) event2  - YSTEK G Mouse: device is a pointer
[  1497.724] (II) config/udev: Adding input device YSTEK G Mouse (/dev/input/mouse0)
[  1497.724] (II) No input driver specified, ignoring this device.
[  1497.724] (II) This device may have been added with another device file.
[  1497.727] (II) config/udev: Adding input device USB USB Keykoard (/dev/input/event8)
[  1497.727] (**) USB USB Keykoard: Applying InputClass "libinput keyboard catchall"
[  1497.727] (II) Using input driver 'libinput' for 'USB USB Keykoard'
[  1497.727] (**) USB USB Keykoard: always reports core events
[  1497.727] (**) Option "Device" "/dev/input/event8"
[  1497.727] (**) Option "_source" "server/udev"
[  1497.729] (II) event8  - USB USB Keykoard: is tagged by udev as: Keyboard
[  1497.729] (II) event8  - USB USB Keykoard: device is a keyboard
[  1497.729] (II) event8  - USB USB Keykoard: device removed
[  1497.744] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.0/0003:1C4F:0002.0002/input/input8/event8"
[  1497.744] (II) XINPUT: Adding extended input device "USB USB Keykoard" (type: KEYBOARD, id 9)
[  1497.744] (**) Option "xkb_model" "pc105"
[  1497.744] (**) Option "xkb_layout" "us"
[  1497.747] (II) event8  - USB USB Keykoard: is tagged by udev as: Keyboard
[  1497.747] (II) event8  - USB USB Keykoard: device is a keyboard
[  1497.750] (II) config/udev: Adding input device USB USB Keykoard (/dev/input/event9)
[  1497.750] (**) USB USB Keykoard: Applying InputClass "libinput keyboard catchall"
[  1497.750] (II) Using input driver 'libinput' for 'USB USB Keykoard'
[  1497.750] (**) USB USB Keykoard: always reports core events
[  1497.750] (**) Option "Device" "/dev/input/event9"
[  1497.750] (**) Option "_source" "server/udev"
[  1497.753] (II) event9  - USB USB Keykoard: is tagged by udev as: Keyboard
[  1497.753] (II) event9  - USB USB Keykoard: device is a keyboard
[  1497.753] (II) event9  - USB USB Keykoard: device removed
[  1497.768] (II) libinput: USB USB Keykoard: needs a virtual subdevice
[  1497.768] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.1/0003:1C4F:0002.0003/input/input9/event9"
[  1497.768] (II) XINPUT: Adding extended input device "USB USB Keykoard" (type: MOUSE, id 10)
[  1497.768] (**) Option "AccelerationScheme" "none"
[  1497.769] (**) USB USB Keykoard: (accel) selected scheme none/0
[  1497.769] (**) USB USB Keykoard: (accel) acceleration factor: 2.000
[  1497.769] (**) USB USB Keykoard: (accel) acceleration threshold: 4
[  1497.771] (II) event9  - USB USB Keykoard: is tagged by udev as: Keyboard
[  1497.771] (II) event9  - USB USB Keykoard: device is a keyboard
[  1497.814] (**) USB USB Keykoard: Applying InputClass "libinput keyboard catchall"
[  1497.814] (II) Using input driver 'libinput' for 'USB USB Keykoard'
[  1497.814] (**) USB USB Keykoard: always reports core events
[  1497.814] (**) Option "Device" "/dev/input/event9"
[  1497.814] (**) Option "_source" "_driver/libinput"
[  1497.815] (II) libinput: USB USB Keykoard: is a virtual subdevice
[  1497.815] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.1/0003:1C4F:0002.0003/input/input9/event9"
[  1497.815] (II) XINPUT: Adding extended input device "USB USB Keykoard" (type: KEYBOARD, id 11)
[  1497.815] (**) Option "xkb_model" "pc105"
[  1497.815] (**) Option "xkb_layout" "us"
[  1563.040] (II) event1  - Power Button: device removed
[  1563.067] (II) event0  - Sleep Button: device removed
[  1563.072] (II) event2  - YSTEK G Mouse: device removed
[  1563.096] (II) event8  - USB USB Keykoard: device removed
[  1563.104] (II) event9  - USB USB Keykoard: device removed
[  1563.122] (II) UnloadModule: "libinput"
[  1563.239] (II) UnloadModule: "libinput"
[  1563.239] (II) UnloadModule: "libinput"
[  1563.240] (II) UnloadModule: "libinput"
[  1563.240] (II) UnloadModule: "libinput"
[  1563.240] (II) UnloadModule: "libinput"
[  1563.532] (II) Server terminated successfully (0). Closing log file.
```

---

### Post by boo-deal-nic on 2018-08-18
Well, Assaultcube (shooter game) installed, and it works, so the driver is fine.
I thought webgl is not working because of driver.
Compton is also installed and works fine.
But I don't know how to solve screen res issue.
I forgot to mention, the same thing was with live usb in ubuntu 18.04.
640x480
800x600
1024x768
and no more...

---

### Post by Yellow Pasque on 2018-08-18
```
[  1497.005] (EE) /dev/dri/card0: failed to set DRM interface version 1.4: Permission denied
```
That doesn't seem right, but googling doesn't give me anything except folks with hybrid graphics (intel/nvidia) complaining about it.

I don't see a lot of detailed info about the resolution in the log. It seems to arbitrarily select 1024x768

> xrandr or something is difficult.

It's not that difficult: [https://wiki.ubuntu.com/X/Config/Resolution#Adding_undetected_resolutions](https://wiki.ubuntu.com/X/Config/Resolution#Adding_undetected_resolutions)

What resolution are you trying to achieve? What model laptop is this?

---

### Post by boo-deal-nic on 2018-08-18
ok, i'll try via xrandr.


monitor standart is 1980x1080, but i need only 1280x720
[SIZE=1](i use it for sound media or youtube playback at some distance. Don't wanna watch at small icons)[/SIZE]


it's 8 years old intel's nettop with embeded dual core Atom D510 @1.6MHz shiped with GMA 3150, need this video just for GUI acceleration.


[SIZE=1]for example in win 7 GUI rendering with "aero" through gma 3150 is very smooth, but i love ubuntu :)[/SIZE]
[SIZE=1]for now gui is setted up, smooth shadows, faded out windows, nice theme, fast gui, firefox quantum just flies (and it's on Atom) but resolutuon...[/SIZE]


i'll try that link and post if it helps.

---

### Post by boo-deal-nic on 2018-08-23
ubuntu-mate@ubuntu-mate:~$ cvt 1280 720 60
# 1280x720 59.86 Hz (CVT 0.92M9) hsync: 44.77 kHz; pclk: 74.50 MHz
Modeline "1280x720_60.00"   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync
ubuntu-mate@ubuntu-mate:~$ xrandr --newmode "1280x720_60.00"   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  28
  Current serial number in output stream:  28

---

