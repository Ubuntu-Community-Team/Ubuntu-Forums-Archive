---
title: "System Freeze Every Start-Up"
date: 2011-08-15
forum: Hardware
---

### Post by rafanz on 2011-08-15
Hi,

Every Start-Up of Ubuntu Maverick Meerkat (10.10) on my Toshiba
Satellite Laptop, the whole system freezes a few minutes after Logging
in. This is about the time I have to open Firefox (but the problem
occurs even if I do not open any software). SysRq+Alt+REISUB has no
effect so I have to do a hard restart.  This usually fixes the problem
(when I log-in again) but sometimes I have to restart in this manner two
or three times. It may be something to do with my Graphics Card or GUI.
 Once the system has its initial spasm, it is generally over for the day. Maybe it doesn't like to be woken up and is a bit cranky in the morning!

Any suggestions?

Here is my Xorg.0.log file

[  3802.073]
X.Org X Server 1.9.0
Release Date: 2010-08-20
[  3802.073] X Protocol Version 11, Revision 0
[  3802.073] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[  3802.073] Current Operating System: Linux rafa-Satellite-A200  2.6.35-30-generic #56-Ubuntu SMP Mon Jul 11 20:00:22 UTC 2011 i686
[  3802.073] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-30-generic root=UUID=773bb190-033f-4f1c-9b77-a6d9ac32ee46 ro quiet splash
[  3802.073] Build Date: 16 September 2010  05:39:22PM
[  3802.073] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support))
[  3802.073] Current version of pixman: 0.18.4
[  3802.073]    Before reporting problems, check [http://wiki.x.org]("http://wiki.x.org/")
        to make sure that you have the latest version.
[  3802.073] Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  3802.074] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Aug 16 12:53:23 2011
[  3802.074] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  3802.147] (==) No Layout section.  Using the first Screen section.
[  3802.147] (==) No screen section available. Using defaults.
[  3802.147] (**) |-->Screen "Default Screen Section" (0)
[  3802.147] (**) |   |-->Monitor "<default monitor>"
[  3802.147] (==) No monitor specified for screen "Default Screen Section".
        Using a default monitor configuration.
[  3802.147] (==) Automatically adding devices
[  3802.148] (==) Automatically enabling devices
[  3802.149] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  3802.149]    Entry deleted from font path.
[  3802.150] (==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/100dpi/:unscaled,
        /usr/share/fonts/X11/75dpi/:unscaled,
        /usr/share/fonts/X11/Type1,
        /usr/share/fonts/X11/100dpi,
        /usr/share/fonts/X11/75dpi,
        /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
        built-ins
[  3802.150] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[  3802.150] (II) The server relies on udev to provide the list of input devices.
        If no devices become available, reconfigure udev or disable AutoAddDevices.
[  3802.150] (II) Loader magic: 0x81f8e00
[  3802.150] (II) Module ABI versions:
[  3802.150]    X.Org ANSI C Emulation: 0.4
[  3802.150]    X.Org Video Driver: 8.0
[  3802.150]    X.Org XInput driver : 11.0
[  3802.150]    X.Org Server Extension : 4.0
[  3802.152] (--) PCI:*(0:0:2:0) 8086:27a2:1179:ff10 rev 3, Mem @  0xf0a00000/524288, 0xd0000000/268435456, 0xf0b00000/262144, I/O @  0x00001800/8
[  3802.152] (--) PCI: (0:0:2:1) 8086:27a6:1179:ff10 rev 3, Mem @ 0xf0a80000/524288
[  3802.153] (II) Open ACPI successful (/var/run/acpid.socket)
[  3802.153] (II) LoadModule: "extmod"
[  3802.154] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[  3802.154] (II) Module extmod: vendor="X.Org Foundation"
[  3802.154]    compiled for 1.9.0, module version = 1.0.0
[  3802.154]    Module class: X.Org Server Extension
[  3802.154]    ABI class: X.Org Server Extension, version 4.0
[  3802.154] (II) Loading extension MIT-SCREEN-SAVER
[  3802.154] (II) Loading extension XFree86-VidModeExtension
[  3802.154] (II) Loading extension XFree86-DGA
[  3802.154] (II) Loading extension DPMS
[  3802.154] (II) Loading extension XVideo
[  3802.154] (II) Loading extension XVideo-MotionCompensation
[  3802.154] (II) Loading extension X-Resource
[  3802.154] (II) LoadModule: "dbe"
[  3802.155] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[  3802.219] (II) Module dbe: vendor="X.Org Foundation"
[  3802.220]    compiled for 1.9.0, module version = 1.0.0
[  3802.220]    Module class: X.Org Server Extension
[  3802.220]    ABI class: X.Org Server Extension, version 4.0
[  3802.220] (II) Loading extension DOUBLE-BUFFER
[  3802.220] (II) LoadModule: "glx"
[  3802.221] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[  3802.221] (II) Module glx: vendor="X.Org Foundation"
[  3802.221]    compiled for 1.9.0, module version = 1.0.0
[  3802.221]    ABI class: X.Org Server Extension, version 4.0
[  3802.221] (==) AIGLX enabled
[  3802.221] (II) Loading extension GLX
[  3802.221] (II) LoadModule: "record"
[  3802.223] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[  3802.231] (II) Module record: vendor="X.Org Foundation"
[  3802.231]    compiled for 1.9.0, module version = 1.13.0
[  3802.231]    Module class: X.Org Server Extension
[  3802.231]    ABI class: X.Org Server Extension, version 4.0
[  3802.231] (II) Loading extension RECORD
[  3802.231] (II) LoadModule: "dri"
[  3802.232] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[  3802.240] (II) Module dri: vendor="X.Org Foundation"
[  3802.240]    compiled for 1.9.0, module version = 1.0.0
[  3802.240]    ABI class: X.Org Server Extension, version 4.0
[  3802.240] (II) Loading extension XFree86-DRI
[  3802.240] (II) LoadModule: "dri2"
[  3802.242] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[  3802.242] (II) Module dri2: vendor="X.Org Foundation"
[  3802.242]    compiled for 1.9.0, module version = 1.2.0
[  3802.242]    ABI class: X.Org Server Extension, version 4.0
[  3802.242] (II) Loading extension DRI2
[  3802.242] (==) Matched intel as autoconfigured driver 0
[  3802.242] (==) Matched vesa as autoconfigured driver 1
[  3802.242] (==) Matched fbdev as autoconfigured driver 2
[  3802.242] (==) Assigned the driver to the xf86ConfigLayout
[  3802.242] (II) LoadModule: "intel"
[  3802.243] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[  3802.253] (II) Module intel: vendor="X.Org Foundation"
[  3802.253]    compiled for 1.9.0, module version = 2.12.0
[  3802.253]    Module class: X.Org Video Driver
[  3802.253]    ABI class: X.Org Video Driver, version 8.0
[  3802.253] (II) LoadModule: "vesa"
[  3802.254] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[  3802.258] (II) Module vesa: vendor="X.Org Foundation"
[  3802.258]    compiled for 1.8.99.905, module version = 2.3.0
[  3802.258]    Module class: X.Org Video Driver
[  3802.258]    ABI class: X.Org Video Driver, version 8.0
[  3802.258] (II) LoadModule: "fbdev"
[  3802.259] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[  3802.269] (II) Module fbdev: vendor="X.Org Foundation"
[  3802.269]    compiled for 1.8.99.905, module version = 0.4.2
[  3802.269]    ABI class: X.Org Video Driver, version 8.0
[  3802.269] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
        i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
        E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
        965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
        4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
        Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
        Sandybridge, Sandybridge
[  3802.271] (II) VESA: driver for VESA chipsets: vesa
[  3802.271] (II) FBDEV: driver for framebuffer: fbdev
[  3802.271] (--) using VT number 8

[  3802.284] (WW) Falling back to old probe method for vesa
[  3802.284] (WW) Falling back to old probe method for fbdev
[  3802.284] (II) Loading sub module "fbdevhw"
[  3802.284] (II) LoadModule: "fbdevhw"
[  3802.285] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[  3802.333] (II) Module fbdevhw: vendor="X.Org Foundation"
[  3802.334]    compiled for 1.9.0, module version = 0.0.2
[  3802.334]    ABI class: X.Org Video Driver, version 8.0
[  3802.371] drmOpenDevice: node name is /dev/dri/card0
[  3802.372] drmOpenDevice: open result is 9, (OK)
[  3802.372] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[  3802.372] drmOpenDevice: node name is /dev/dri/card0
[  3802.372] drmOpenDevice: open result is 9, (OK)
[  3802.372] drmOpenByBusid: drmOpenMinor returns 9
[  3802.372] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[  3802.372] (II) intel(0): Creating default Display subsection in Screen section
        "Default Screen Section" for depth/fbbpp 24/32
[  3802.372] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[  3802.372] (==) intel(0): RGB weight 888
[  3802.372] (==) intel(0): Default visual is TrueColor
[  3802.372] (II) intel(0): Integrated Graphics Chipset: Intel(R) 945GM
[  3802.372] (--) intel(0): Chipset: "945GM"
[  3802.372] (==) intel(0): video overlay key set to 0x101fe
[  3802.405] (II) intel(0): Output VGA1 has no monitor section
[  3802.405] (II) intel(0): Output LVDS1 has no monitor section
[  3802.405] (II) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
[  3802.692] (II) intel(0): Output TV1 has no monitor section
[  3802.724] (II) intel(0): EDID for output VGA1
[  3802.724] (II) intel(0): EDID for output LVDS1
[  3802.724] (II) intel(0): Manufacturer: SHP  Model: 13ce  Serial#: 0
[  3802.724] (II) intel(0): Year: 1990  Week: 0
[  3802.724] (II) intel(0): EDID Version: 1.3
[  3802.724] (II) intel(0): Digital Display Input
[  3802.724] (II) intel(0): Max Image Size [cm]: horiz.: 33  vert.: 21
[  3802.724] (II) intel(0): Gamma: 2.20
[  3802.724] (II) intel(0): DPMS capabilities: StandBy Suspend
[  3802.724] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4
[  3802.724] (II) intel(0): First detailed timing is preferred mode
[  3802.724] (II) intel(0): redX: 0.000 redY: 0.000   greenX: 0.000 greenY: 0.000
[  3802.724] (II) intel(0): blueX: 0.000 blueY: 0.000   whiteX: 0.000 whiteY: 0.000
[  3802.724] (II) intel(0): Manufacturer's mask: 0
[  3802.724] (II) intel(0): Supported detailed timing:
[  3802.724] (II) intel(0): clock: 71.0 MHz   Image Size:  331 x 207 mm
[  3802.725] (II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
[  3802.725] (II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 823 v_border: 0
[  3802.725] (II) intel(0): EDID (in hex):
[  3802.725] (II) intel(0):     00ffffffffffff004d10ce1300000000
[  3802.725] (II) intel(0):     0000010380211578ca00000000000000
[  3802.725] (II) intel(0):     00000000000001010101010101010101
[  3802.725] (II) intel(0):     010101010101bc1b00a0502017303020
[  3802.725] (II) intel(0):     36004bcf100000190000001000000000
[  3802.725] (II) intel(0):     00000000000000000a20000000100000
[  3802.725] (II) intel(0):     000000000000000000000a2000000010
[  3802.725] (II) intel(0):     004c513135344b314c423143200a0062
[  3802.726] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[  3802.726] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[  3802.726] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[  3802.726] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[  3802.726] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[  3802.726] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[  3802.726] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[  3802.726] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[  3802.726] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[  3802.726] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[  3802.726] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[  3802.726] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[  3802.726] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[  3802.726] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[  3802.726] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[  3802.726] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[  3802.726] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[  3802.726] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[  3802.726] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[  3802.726] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[  3802.726] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[  3802.726] (II) intel(0): Printing probed modes for output LVDS1
[  3802.726] (II) intel(0): Modeline "1280x800"x59.9   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[  3802.727] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  3802.727] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  3802.727] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[  3802.727] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  3803.012] (II) intel(0): EDID for output TV1
[  3803.012] (II) intel(0): Output VGA1 disconnected
[  3803.012] (II) intel(0): Output LVDS1 connected
[  3803.012] (II) intel(0): Output TV1 disconnected
[  3803.012] (II) intel(0): Using exact sizes for initial modes
[  3803.012] (II) intel(0): Output LVDS1 using initial mode 1280x800
[  3803.012] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[  3803.012] (II) intel(0): Kernel page flipping support detected, but forcibly disabled.
[  3803.012] (==) intel(0): DPI set to (96, 96)
[  3803.012] (II) Loading sub module "fb"
[  3803.012] (II) LoadModule: "fb"
[  3803.013] (II) Loading /usr/lib/xorg/modules/libfb.so
[  3803.038] (II) Module fb: vendor="X.Org Foundation"
[  3803.038]    compiled for 1.9.0, module version = 1.0.0
[  3803.038]    ABI class: X.Org ANSI C Emulation, version 0.4
[  3803.038] (II) UnloadModule: "vesa"
[  3803.038] (II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
[  3803.038] (II) UnloadModule: "fbdev"
[  3803.039] (II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[  3803.039] (II) UnloadModule: "fbdevhw"
[  3803.039] (II) Unloading /usr/lib/xorg/modules/libfbdevhw.so
[  3803.039] (==) Depth 24 pixmap format is 32 bpp
[  3803.039] (II) intel(0): [DRI2] Setup complete
[  3803.039] (II) intel(0): [DRI2]   DRI driver: i915
[  3803.039] (**) intel(0): Tiling enabled
[  3803.039] (**) intel(0): SwapBuffers wait enabled
[  3803.039] (==) intel(0): VideoRam: 262144 KB
[  3803.039] (II) intel(0): Allocated new frame buffer 1280x800 stride 8192, tiled
[  3803.039] (II) UXA(0): Driver registered support for the following operations:
[  3803.039] (II)         solid
[  3803.039] (II)         copy
[  3803.039] (II)         composite (RENDER acceleration)
[  3803.039] (II)         put_image
[  3803.039] (II)         get_image
[  3803.039] (==) intel(0): Backing store disabled
[  3803.040] (==) intel(0): Silken mouse enabled
[  3803.040] (II) intel(0): Initializing HW Cursor
[  3803.100] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[  3803.103] (==) intel(0): DPMS enabled
[  3803.103] (==) intel(0): Intel XvMC decoder disabled
[  3803.103] (II) intel(0): Set up textured video
[  3803.103] (II) intel(0): Set up overlay video
[  3803.104] (II) intel(0): direct rendering: DRI2 Enabled
[  3803.104] (--) RandR disabled
[  3803.104] (II) Initializing built-in extension Generic Event Extension
[  3803.104] (II) Initializing built-in extension SHAPE
[  3803.104] (II) Initializing built-in extension MIT-SHM
[  3803.104] (II) Initializing built-in extension XInputExtension
[  3803.104] (II) Initializing built-in extension XTEST
[  3803.104] (II) Initializing built-in extension BIG-REQUESTS
[  3803.104] (II) Initializing built-in extension SYNC
[  3803.104] (II) Initializing built-in extension XKEYBOARD
[  3803.104] (II) Initializing built-in extension XC-MISC
[  3803.104] (II) Initializing built-in extension SECURITY
[  3803.104] (II) Initializing built-in extension XINERAMA
[  3803.104] (II) Initializing built-in extension XFIXES
[  3803.104] (II) Initializing built-in extension RENDER
[  3803.104] (II) Initializing built-in extension RANDR
[  3803.104] (II) Initializing built-in extension COMPOSITE
[  3803.104] (II) Initializing built-in extension DAMAGE
[  3803.104] (II) Initializing built-in extension GESTURE
[  3803.128] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[  3803.128] (II) AIGLX: enabled GLX_INTEL_swap_event
[  3803.128] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[  3803.128] (II) AIGLX: enabled GLX_SGI_make_current_read
[  3803.128] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[  3803.128] (II) AIGLX: Loaded and initialized /usr/lib/dri/i915_dri.so
[  3803.128] (II) GLX: Initialized DRI2 GL provider for screen 0
[  3803.129] (II) intel(0): Setting screen physical size to 338 x 211
[  3803.284] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[  3803.323] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[  3803.323] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  3803.323] (II) LoadModule: "evdev"
[  3803.323] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  3803.364] (II) Module evdev: vendor="X.Org Foundation"
[  3803.364]    compiled for 1.9.0, module version = 2.3.2
[  3803.364]    Module class: X.Org XInput Driver
[  3803.364]    ABI class: X.Org XInput driver, version 11.0
[  3803.364] (**) Power Button: always reports core events
[  3803.364] (**) Power Button: Device: "/dev/input/event2"
[  3803.364] (II) Power Button: Found keys
[  3803.364] (II) Power Button: Configuring as keyboard
[  3803.365] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[  3803.365] (**) Option "xkb_rules" "evdev"
[  3803.365] (**) Option "xkb_model" "pc105"
[  3803.365] (**) Option "xkb_layout" "us"
[  3803.367] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[  3803.367] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[  3803.367] (**) Video Bus: always reports core events
[  3803.367] (**) Video Bus: Device: "/dev/input/event4"
[  3803.377] (II) Video Bus: Found keys
[  3803.377] (II) Video Bus: Configuring as keyboard
[  3803.377] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[  3803.377] (**) Option "xkb_rules" "evdev"
[  3803.377] (**) Option "xkb_model" "pc105"
[  3803.377] (**) Option "xkb_layout" "us"
[  3803.383] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[  3803.383] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  3803.383] (**) Power Button: always reports core events
[  3803.383] (**) Power Button: Device: "/dev/input/event1"
[  3803.393] (II) Power Button: Found keys
[  3803.393] (II) Power Button: Configuring as keyboard
[  3803.393] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[  3803.393] (**) Option "xkb_rules" "evdev"
[  3803.393] (**) Option "xkb_model" "pc105"
[  3803.393] (**) Option "xkb_layout" "us"
[  3803.394] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[  3803.394] (II) No input driver/identifier specified (ignoring)
[  3803.407] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[  3803.407] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[  3803.407] (**) AT Translated Set 2 keyboard: always reports core events
[  3803.407] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[  3803.421] (II) AT Translated Set 2 keyboard: Found keys
[  3803.421] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[  3803.421] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[  3803.421] (**) Option "xkb_rules" "evdev"
[  3803.421] (**) Option "xkb_model" "pc105"
[  3803.421] (**) Option "xkb_layout" "us"
[  3803.422] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event5)
[  3803.422] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[  3803.422] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[  3803.422] (II) LoadModule: "synaptics"
[  3803.423] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[  3803.434] (II) Module synaptics: vendor="X.Org Foundation"
[  3803.434]    compiled for 1.9.0, module version = 1.2.2
[  3803.434]    Module class: X.Org XInput Driver
[  3803.434]    ABI class: X.Org XInput driver, version 11.0
[  3803.434] (II) Synaptics touchpad driver version 1.2.2
[  3803.434] (**) Option "Device" "/dev/input/event5"
[  3803.445] (II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[  3803.445] (II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[  3803.445] (II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[  3803.445] (II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
[  3803.445] (II) SynPS/2 Synaptics TouchPad: buttons: left right double triple
[  3803.448] (--) SynPS/2 Synaptics TouchPad: touchpad found
[  3803.448] (**) SynPS/2 Synaptics TouchPad: always reports core events
[  3803.453] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[  3803.453] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[  3803.453] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
[  3803.453] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[  3803.453] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[  3803.456] (--) SynPS/2 Synaptics TouchPad: touchpad found
[  3803.456] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[  3803.456] (II) No input driver/identifier specified (ignoring)
[  3804.324] (II) intel(0): EDID vendor "SHP", prod id 5070
[  3804.324] (II) intel(0): Printing DDC gathered Modelines:
[  3804.324] (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[  3804.644] (II) intel(0): EDID vendor "SHP", prod id 5070
[  3804.644] (II) intel(0): Printing DDC gathered Modelines:
[  3804.644] (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[  3804.968] (II) intel(0): EDID vendor "SHP", prod id 5070
[  3804.968] (II) intel(0): Printing DDC gathered Modelines:
[  3804.968] (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[  3805.292] (II) intel(0): EDID vendor "SHP", prod id 5070
[  3805.292] (II) intel(0): Printing DDC gathered Modelines:
[  3805.292] (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[  3812.641] (II) intel(0): EDID vendor "SHP", prod id 5070
[  3812.641] (II) intel(0): Printing DDC gathered Modelines:
[  3812.641] (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[  3812.968] (II) intel(0): EDID vendor "SHP", prod id 5070
[  3812.968] (II) intel(0): Printing DDC gathered Modelines:
[  3812.968] (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[  3813.292] (II) intel(0): EDID vendor "SHP", prod id 5070
[  3813.292] (II) intel(0): Printing DDC gathered Modelines:
[  3813.292] (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[  3813.612] (II) intel(0): EDID vendor "SHP", prod id 5070
[  3813.612] (II) intel(0): Printing DDC gathered Modelines:
[  3813.612] (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[  3814.388] (II) intel(0): EDID vendor "SHP", prod id 5070
[  3814.388] (II) intel(0): Printing DDC gathered Modelines:
[  3814.388] (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[  3815.181] (II) intel(0): EDID vendor "SHP", prod id 5070
[  3815.181] (II) intel(0): Printing DDC gathered Modelines:
[  3815.181] (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[  3820.257] (II) intel(0): EDID vendor "SHP", prod id 5070
[  3820.257] (II) intel(0): Printing DDC gathered Modelines:
[  3820.257] (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)

ProblemType: Bug
DistroRelease: Ubuntu 10.10
Package: evince 2.32.0-0ubuntu1.1
ProcVersionSignature: Ubuntu 2.6.35-30.56-generic 2.6.35.13
Uname: Linux 2.6.35-30-generic i686
Architecture: i386
Date: Tue Aug 16 13:01:14 2011
InstallationMedia: Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
ProcEnviron:
 LANG=en_NZ.utf8
 SHELL=/bin/bash
SourcePackage: evince

** Affects: evince (Ubuntu)
     Importance: Undecided
         Status: New


** Tags: apport-bug i386 maverick

---

### Post by TechAlchemist on 2011-08-16
Hi there,

Your Xorg log looks fine to me... When it freezes, can you hit ctrl+alt+f2 and get into a terminal? or is there no response at all?

I'd love to see the output of dmesg, which you can get using the command 'dmesg' from the shell

It'd especially help if you could get it around the time of the hang-up.  However, you could also grab the file /var/log/dmesg.0

Thanks

---

