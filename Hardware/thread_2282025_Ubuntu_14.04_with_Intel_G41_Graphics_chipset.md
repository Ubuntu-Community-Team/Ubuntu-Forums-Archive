---
title: "Ubuntu 14.04 with Intel G41 Graphics chipset"
date: 2015-06-11
forum: Hardware
---

### Post by nsathees on 2015-06-11
Ubuntu 14.04 with integrated Intel G41 graphics chip set (Gigabite GA 41M Combo Motherboard)

It was all working fine about a year ago until one day I did update the system as it was always I do when ever the system prompt to do so.

There after my ASUS VH192 monitor started on 1024 X 768 instead of 1366 X 768

I have search many forums and did a lots of things but never got it to work at that resolution again unless I do xrandr add-mode. So I lived with it for about a year. 

Funny but true, some times if I connect my android phone to the USB before stating the system it detects the right resolution 1366 X 768!

After updating to Ubuntu 15.04 I had problem with it. It started to flicker. I also had problem with network Icon disappearing from the task bar once it get disconnected. So I did a fresh install of Ubuntu 14.04 again.

It is not a monitor or cable problem as I tried connecting my Samsung monitor and nothing changed.

I can't install Intel graphics driver as there is a version issue. Tricked it by changing the version in a file as read in forum and ended up reinstalling 14.04 from the beginning. That was a bad advise!

the last thing I tried is [https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers)

under "About this Computer" the graphics is listed correctly. I don't have a xorg.conf file

```
glxinfo | grep render
direct rendering: Yes
    GLX_MESA_multithread_makecurrent, GLX_MESA_query_renderer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_query_renderer, 
OpenGL renderer string: Mesa DRI Intel(R) G41 x86/MMX/SSE2
    GL_NV_conditional_render, GL_NV_depth_clamp, GL_NV_light_max_exponent, 
    GL_OES_element_index_uint, GL_OES_fbo_render_mipmap, 

sudo lshw -c video
  *-display               
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
       resources: irq:40 memory:fd800000-fdbfffff memory:d0000000-dfffffff ioport:ff00(size=8)

xrandr --verbose
Screen 0: minimum 8 x 8, current 1024 x 768, maximum 32767 x 32767
VGA1 connected primary 1024x768+0+0 (0x45) normal (normal left inverted right x axis y axis) 0mm x 0mm
    Identifier: 0x42
    Timestamp:  24687
    Subpixel:   unknown
    Gamma:      1.0:1.0:1.0
    Brightness: 1.0
    Clones:    
    CRTC:       0
    CRTCs:      0 1
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
  1024x768 (0x45)   65.0MHz -HSync -VSync *current
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock   48.4KHz
        v: height  768 start  771 end  777 total  806           clock   60.0Hz
  800x600 (0xa1)   40.0MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock   37.9KHz
        v: height  600 start  601 end  605 total  628           clock   60.3Hz
  800x600 (0xa2)   36.0MHz +HSync +VSync
        h: width   800 start  824 end  896 total 1024 skew    0 clock   35.2KHz
        v: height  600 start  601 end  603 total  625           clock   56.2Hz
  848x480 (0xa3)   33.8MHz +HSync +VSync
        h: width   848 start  864 end  976 total 1088 skew    0 clock   31.0KHz
        v: height  480 start  486 end  494 total  517           clock   60.0Hz
  640x480 (0xa4)   25.2MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  489 end  492 total  525           clock   59.9Hz
VIRTUAL1 disconnected (normal left inverted right x axis y axis)
    Identifier: 0x43
    Timestamp:  24687
    Subpixel:   no subpixels
    Clones:    
    CRTCs:      2
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter:

```
Can anyone out there help me to get the resolution back to 1366 X 768?

I could try to go back and install 12.04 to see if that could fix the problem!

Thank you Ubuntu Geeks!

---

### Post by wildmanne39 on 2015-06-11
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by nsathees on 2015-06-11
Here is my xorg.0.log
```

[    26.685] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[    26.685] X Protocol Version 11, Revision 0
[    26.685] Build Operating System: Linux 3.2.0-75-generic i686 Ubuntu
[    26.685] Current Operating System: Linux sathees 3.19.0-20-generic #20~14.04.1-Ubuntu SMP Sat May 30 00:15:05 UTC 2015 i686
[    26.686] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.19.0-20-generic root=UUID=f8e84d06-9ae6-4021-ac6e-ec1822203995 ro quiet splash vt.handoff=7
[    26.686] Build Date: 12 February 2015  02:49:46PM
[    26.686] xorg-server 2:1.15.1-0ubuntu2.7 (For technical support please see http://www.ubuntu.com/support) 
[    26.686] Current version of pixman: 0.30.2
[    26.686] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    26.686] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    26.686] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Jun 12 06:51:45 2015
[    26.772] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    26.848] (==) No Layout section.  Using the first Screen section.
[    26.848] (==) No screen section available. Using defaults.
[    26.848] (**) |-->Screen "Default Screen Section" (0)
[    26.848] (**) |   |-->Monitor "<default monitor>"
[    26.849] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    26.849] (==) Automatically adding devices
[    26.849] (==) Automatically enabling devices
[    26.849] (==) Automatically adding GPU devices
[    26.878] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    26.878] 	Entry deleted from font path.
[    26.878] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    26.878] 	Entry deleted from font path.
[    26.878] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    26.878] 	Entry deleted from font path.
[    26.883] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    26.883] 	Entry deleted from font path.
[    26.883] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    26.883] 	Entry deleted from font path.
[    26.883] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    26.883] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    26.883] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    26.883] (II) Loader magic: 0xb77e36c0
[    26.883] (II) Module ABI versions:
[    26.883] 	X.Org ANSI C Emulation: 0.4
[    26.883] 	X.Org Video Driver: 15.0
[    26.883] 	X.Org XInput driver : 20.0
[    26.883] 	X.Org Server Extension : 8.0
[    26.883] (II) xfree86: Adding drm device (/dev/dri/card0)
[    26.884] (--) PCI:*(0:0:2:0) 8086:2e32:1458:d000 rev 3, Mem @ 0xfd800000/4194304, 0xd0000000/268435456, I/O @ 0x0000ff00/8
[    26.894] Initializing built-in extension Generic Event Extension
[    26.894] Initializing built-in extension SHAPE
[    26.894] Initializing built-in extension MIT-SHM
[    26.894] Initializing built-in extension XInputExtension
[    26.894] Initializing built-in extension XTEST
[    26.894] Initializing built-in extension BIG-REQUESTS
[    26.894] Initializing built-in extension SYNC
[    26.894] Initializing built-in extension XKEYBOARD
[    26.894] Initializing built-in extension XC-MISC
[    26.894] Initializing built-in extension SECURITY
[    26.894] Initializing built-in extension XINERAMA
[    26.894] Initializing built-in extension XFIXES
[    26.894] Initializing built-in extension RENDER
[    26.894] Initializing built-in extension RANDR
[    26.894] Initializing built-in extension COMPOSITE
[    26.894] Initializing built-in extension DAMAGE
[    26.894] Initializing built-in extension MIT-SCREEN-SAVER
[    26.894] Initializing built-in extension DOUBLE-BUFFER
[    26.894] Initializing built-in extension RECORD
[    26.894] Initializing built-in extension DPMS
[    26.894] Initializing built-in extension Present
[    26.894] Initializing built-in extension DRI3
[    26.894] Initializing built-in extension X-Resource
[    26.894] Initializing built-in extension XVideo
[    26.894] Initializing built-in extension XVideo-MotionCompensation
[    26.894] Initializing built-in extension SELinux
[    26.894] Initializing built-in extension XFree86-VidModeExtension
[    26.894] Initializing built-in extension XFree86-DGA
[    26.894] Initializing built-in extension XFree86-DRI
[    26.894] Initializing built-in extension DRI2
[    26.894] (II) LoadModule: "glx"
[    26.924] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    27.248] (II) Module glx: vendor="X.Org Foundation"
[    27.248] 	compiled for 1.15.1, module version = 1.0.0
[    27.248] 	ABI class: X.Org Server Extension, version 8.0
[    27.248] (==) AIGLX enabled
[    27.248] Loading extension GLX
[    27.248] (==) Matched intel as autoconfigured driver 0
[    27.248] (==) Matched intel as autoconfigured driver 1
[    27.248] (==) Matched modesetting as autoconfigured driver 2
[    27.248] (==) Matched fbdev as autoconfigured driver 3
[    27.248] (==) Matched vesa as autoconfigured driver 4
[    27.248] (==) Assigned the driver to the xf86ConfigLayout
[    27.248] (II) LoadModule: "intel"
[    27.294] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    27.343] (II) Module intel: vendor="X.Org Foundation"
[    27.343] 	compiled for 1.15.1, module version = 2.99.917
[    27.343] 	Module class: X.Org Video Driver
[    27.343] 	ABI class: X.Org Video Driver, version 15.0
[    27.343] (II) LoadModule: "modesetting"
[    27.343] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    27.359] (II) Module modesetting: vendor="X.Org Foundation"
[    27.359] 	compiled for 1.15.0, module version = 0.8.1
[    27.359] 	Module class: X.Org Video Driver
[    27.359] 	ABI class: X.Org Video Driver, version 15.0
[    27.359] (II) LoadModule: "fbdev"
[    27.360] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    27.369] (II) Module fbdev: vendor="X.Org Foundation"
[    27.369] 	compiled for 1.15.0, module version = 0.4.4
[    27.369] 	Module class: X.Org Video Driver
[    27.369] 	ABI class: X.Org Video Driver, version 15.0
[    27.369] (II) LoadModule: "vesa"
[    27.369] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    27.379] (II) Module vesa: vendor="X.Org Foundation"
[    27.379] 	compiled for 1.15.0, module version = 2.3.3
[    27.379] 	Module class: X.Org Video Driver
[    27.379] 	ABI class: X.Org Video Driver, version 15.0
[    27.379] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
	i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
	915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
	Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
	GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[    27.379] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[    27.379] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[    27.379] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[    27.379] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    27.379] (II) FBDEV: driver for framebuffer: fbdev
[    27.379] (II) VESA: driver for VESA chipsets: vesa
[    27.379] (++) using VT number 7


[    27.403] (II) intel(0): Using Kernel Mode Setting driver: i915, version 1.6.0 20141121
[    27.403] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.99.917+git1506111932.f71148~gd~t (Oibaf <fmrummey@gmail.com>)
[    27.403] (II) intel(0): SNA compiled for use with valgrind
[    27.404] (WW) Falling back to old probe method for modesetting
[    27.404] (WW) Falling back to old probe method for fbdev
[    27.404] (II) Loading sub module "fbdevhw"
[    27.404] (II) LoadModule: "fbdevhw"
[    27.404] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    27.426] (II) Module fbdevhw: vendor="X.Org Foundation"
[    27.426] 	compiled for 1.15.1, module version = 0.0.2
[    27.426] 	ABI class: X.Org Video Driver, version 15.0
[    27.426] (WW) Falling back to old probe method for vesa
[    27.427] (--) intel(0): Integrated Graphics Chipset: Intel(R) G41
[    27.427] (--) intel(0): CPU: x86, sse2, sse3, ssse3, sse4.1; using a maximum of 2 threads
[    27.427] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    27.427] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    27.427] (==) intel(0): RGB weight 888
[    27.427] (==) intel(0): Default visual is TrueColor
[    27.427] (II) intel(0): Output VGA1 has no monitor section
[    27.427] (II) intel(0): Enabled output VGA1
[    27.427] (--) intel(0): Using a maximum size of 256x256 for hardware cursors
[    27.427] (II) intel(0): Output VIRTUAL1 has no monitor section
[    27.427] (II) intel(0): Enabled output VIRTUAL1
[    27.427] (--) intel(0): Output VGA1 using initial mode 1024x768 on pipe 0
[    27.427] (==) intel(0): TearFree disabled
[    27.427] (==) intel(0): DPI set to (96, 96)
[    27.427] (II) Loading sub module "dri2"
[    27.427] (II) LoadModule: "dri2"
[    27.427] (II) Module "dri2" already built-in
[    27.427] (II) Loading sub module "present"
[    27.427] (II) LoadModule: "present"
[    27.428] (WW) Warning, couldn't open module present
[    27.428] (II) UnloadModule: "present"
[    27.428] (II) Unloading present
[    27.428] (EE) intel: Failed to load module "present" (module does not exist, 0)
[    27.428] (II) UnloadModule: "modesetting"
[    27.428] (II) Unloading modesetting
[    27.428] (II) UnloadModule: "fbdev"
[    27.428] (II) Unloading fbdev
[    27.428] (II) UnloadSubModule: "fbdevhw"
[    27.428] (II) Unloading fbdevhw
[    27.428] (II) UnloadModule: "vesa"
[    27.428] (II) Unloading vesa
[    27.428] (==) Depth 24 pixmap format is 32 bpp
[    27.454] (II) intel(0): SNA initialized with Eaglelake (gen4.5) backend
[    27.454] (==) intel(0): Backing store enabled
[    27.454] (==) intel(0): Silken mouse enabled
[    27.455] (II) intel(0): HW Cursor enabled
[    27.455] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    27.455] (==) intel(0): DPMS enabled
[    27.455] (==) intel(0): Display hotplug detection enabled
[    27.455] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[    27.455] (II) intel(0): [DRI2] Setup complete
[    27.455] (II) intel(0): [DRI2]   DRI driver: i965
[    27.455] (II) intel(0): [DRI2]   VDPAU driver: va_gl
[    27.455] (II) intel(0): direct rendering: DRI2 enabled
[    27.455] (--) RandR disabled
[    27.465] (II) SELinux: Disabled on system
[    27.678] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    27.678] (II) AIGLX: enabled GLX_ARB_create_context
[    27.678] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    27.678] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    27.678] (II) AIGLX: enabled GLX_INTEL_swap_event
[    27.678] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    27.678] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[    27.678] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[    27.678] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    27.678] (II) AIGLX: Loaded and initialized i965
[    27.678] (II) GLX: Initialized DRI2 GL provider for screen 0
[    27.682] (II) intel(0): switch to mode 1024x768@60.0 on VGA1 using pipe 0, position (0, 0), rotation normal, reflection none
[    27.682] (II) intel(0): Setting screen physical size to 270 x 203
[    27.798] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    27.804] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    27.804] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    27.804] (II) LoadModule: "evdev"
[    27.804] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    27.836] (II) Module evdev: vendor="X.Org Foundation"
[    27.836] 	compiled for 1.15.0, module version = 2.8.2
[    27.836] 	Module class: X.Org XInput Driver
[    27.836] 	ABI class: X.Org XInput driver, version 20.0
[    27.836] (II) Using input driver 'evdev' for 'Power Button'
[    27.836] (**) Power Button: always reports core events
[    27.836] (**) evdev: Power Button: Device: "/dev/input/event1"
[    27.836] (--) evdev: Power Button: Vendor 0 Product 0x1
[    27.837] (--) evdev: Power Button: Found keys
[    27.837] (II) evdev: Power Button: Configuring as keyboard
[    27.837] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    27.837] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    27.837] (**) Option "xkb_rules" "evdev"
[    27.837] (**) Option "xkb_model" "pc105"
[    27.837] (**) Option "xkb_layout" "us"
[    27.837] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    27.837] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    27.837] (II) Using input driver 'evdev' for 'Power Button'
[    27.837] (**) Power Button: always reports core events
[    27.837] (**) evdev: Power Button: Device: "/dev/input/event0"
[    27.837] (--) evdev: Power Button: Vendor 0 Product 0x1
[    27.837] (--) evdev: Power Button: Found keys
[    27.837] (II) evdev: Power Button: Configuring as keyboard
[    27.837] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    27.837] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    27.837] (**) Option "xkb_rules" "evdev"
[    27.837] (**) Option "xkb_model" "pc105"
[    27.837] (**) Option "xkb_layout" "us"
[    27.837] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:02.0/drm/card0
[    27.838] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    27.838] (II) config/udev: Adding input device HDA Intel Rear Mic (/dev/input/event4)
[    27.838] (II) No input driver specified, ignoring this device.
[    27.838] (II) This device may have been added with another device file.
[    27.838] (II) config/udev: Adding input device HDA Intel Front Mic (/dev/input/event5)
[    27.838] (II) No input driver specified, ignoring this device.
[    27.838] (II) This device may have been added with another device file.
[    27.838] (II) config/udev: Adding input device HDA Intel Line (/dev/input/event6)
[    27.838] (II) No input driver specified, ignoring this device.
[    27.838] (II) This device may have been added with another device file.
[    27.839] (II) config/udev: Adding input device HDA Intel Line Out (/dev/input/event7)
[    27.839] (II) No input driver specified, ignoring this device.
[    27.839] (II) This device may have been added with another device file.
[    27.839] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    27.839] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    27.839] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    27.839] (**) AT Translated Set 2 keyboard: always reports core events
[    27.839] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    27.839] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    27.839] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    27.839] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    27.839] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    27.839] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 8)
[    27.839] (**) Option "xkb_rules" "evdev"
[    27.839] (**) Option "xkb_model" "pc105"
[    27.839] (**) Option "xkb_layout" "us"
[    27.840] (II) config/udev: Adding input device ImPS/2 Logitech Wheel Mouse (/dev/input/event3)
[    27.840] (**) ImPS/2 Logitech Wheel Mouse: Applying InputClass "evdev pointer catchall"
[    27.840] (II) Using input driver 'evdev' for 'ImPS/2 Logitech Wheel Mouse'
[    27.840] (**) ImPS/2 Logitech Wheel Mouse: always reports core events
[    27.840] (**) evdev: ImPS/2 Logitech Wheel Mouse: Device: "/dev/input/event3"
[    27.840] (--) evdev: ImPS/2 Logitech Wheel Mouse: Vendor 0x2 Product 0x5
[    27.840] (--) evdev: ImPS/2 Logitech Wheel Mouse: Found 3 mouse buttons
[    27.840] (--) evdev: ImPS/2 Logitech Wheel Mouse: Found scroll wheel(s)
[    27.840] (--) evdev: ImPS/2 Logitech Wheel Mouse: Found relative axes
[    27.840] (--) evdev: ImPS/2 Logitech Wheel Mouse: Found x and y relative axes
[    27.840] (II) evdev: ImPS/2 Logitech Wheel Mouse: Configuring as mouse
[    27.840] (II) evdev: ImPS/2 Logitech Wheel Mouse: Adding scrollwheel support
[    27.840] (**) evdev: ImPS/2 Logitech Wheel Mouse: YAxisMapping: buttons 4 and 5
[    27.840] (**) evdev: ImPS/2 Logitech Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    27.840] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input4/event3"
[    27.840] (II) XINPUT: Adding extended input device "ImPS/2 Logitech Wheel Mouse" (type: MOUSE, id 9)
[    27.840] (II) evdev: ImPS/2 Logitech Wheel Mouse: initialized for relative axes.
[    27.840] (**) ImPS/2 Logitech Wheel Mouse: (accel) keeping acceleration scheme 1
[    27.840] (**) ImPS/2 Logitech Wheel Mouse: (accel) acceleration profile 0
[    27.840] (**) ImPS/2 Logitech Wheel Mouse: (accel) acceleration factor: 2.000
[    27.840] (**) ImPS/2 Logitech Wheel Mouse: (accel) acceleration threshold: 4
[    27.840] (II) config/udev: Adding input device ImPS/2 Logitech Wheel Mouse (/dev/input/mouse0)
[    27.840] (II) No input driver specified, ignoring this device.
[    27.840] (II) This device may have been added with another device file.
[    45.129] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    45.335] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    45.345] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    55.950] (II) XKB: reuse xkmfile /var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm

```

---

### Post by nsathees on 2015-06-11
I am about to compile a 3.19 kernel for Ubuntu 14.04 and see what improvement that brings!

---

