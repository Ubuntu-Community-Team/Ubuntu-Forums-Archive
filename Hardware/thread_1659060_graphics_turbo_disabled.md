---
title: "graphics turbo disabled?"
date: 2011-01-03
forum: Hardware
---

### Post by RedBluespot on 2011-01-03
Hi!

Everytime I boot up Ubuntu I get a message flashing by split second. This is from my dmesg.log.

[   15.799491] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled

Everything seems to work nice, but I'm curious what to do about this message. It's kinda annoying and I guess it's slowing down my boot up time too.

Thank you!

---

### Post by Fafler on 2011-01-03
Do you even have a Intel graphics device?
```
lspci | grep VGA
```

If it doesn't return anything made by Intel, you can safely ignore the error.

If you do, are you using the correct driver? Try looking at /var/log/Xorg.0.log
It should either use the intel or vesa. If it uses the vesa driver almost everything should still work, but stuff like 3D  accelleration are missing.

---

### Post by ProBook on 2011-02-05
Hi mates :D
first, i'm sorry for my english, then, i'm new & noob in linux world, but I really love it :)

I've an hp ProBook 5320m with ubuntu 10.10 64 bit and I see this message too!

the result of lspci | grep VGA is:
```
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
```

My /var/log/Xorg.0.log is:
```
[    18.284] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    18.284] X Protocol Version 11, Revision 0
[    18.284] Build Operating System: Linux 2.6.24-28-server x86_64 Ubuntu
[    18.284] Current Operating System: Linux ProBook 2.6.35.10mykernel #1 SMP Wed Feb 2 18:54:21 CET 2011 x86_64
[    18.284] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35.10mykernel root=UUID=31fa5ec7-2d48-4b41-b46c-4d96b926f1db ro quiet splash
[    18.284] Build Date: 09 January 2011  12:14:27PM
[    18.284] xorg-server 2:1.9.0-0ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
[    18.284] Current version of pixman: 0.18.4
[    18.284]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    18.284] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    18.284] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Feb  5 21:18:39 2011
[    18.299] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    18.299] (==) No Layout section.  Using the first Screen section.
[    18.299] (==) No screen section available. Using defaults.
[    18.299] (**) |-->Screen "Default Screen Section" (0)
[    18.299] (**) |   |-->Monitor "<default monitor>"
[    18.299] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    18.299] (==) Automatically adding devices
[    18.299] (==) Automatically enabling devices
[    18.299] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    18.299]     Entry deleted from font path.
[    18.299] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    18.299] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    18.299] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    18.299] (II) Loader magic: 0x7d17a0
[    18.299] (II) Module ABI versions:
[    18.299]     X.Org ANSI C Emulation: 0.4
[    18.299]     X.Org Video Driver: 8.0
[    18.299]     X.Org XInput driver : 11.0
[    18.299]     X.Org Server Extension : 4.0
[    18.300] (--) PCI:*(0:0:2:0) 8086:0046:103c:149b rev 2, Mem @ 0xd0000000/4194304, 0xc0000000/268435456, I/O @ 0x00003030/8
[    18.300] (II) Open ACPI successful (/var/run/acpid.socket)
[    18.300] (II) LoadModule: "extmod"
[    18.312] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    18.312] (II) Module extmod: vendor="X.Org Foundation"
[    18.312]     compiled for 1.9.0, module version = 1.0.0
[    18.312]     Module class: X.Org Server Extension
[    18.312]     ABI class: X.Org Server Extension, version 4.0
[    18.312] (II) Loading extension MIT-SCREEN-SAVER
[    18.312] (II) Loading extension XFree86-VidModeExtension
[    18.312] (II) Loading extension XFree86-DGA
[    18.312] (II) Loading extension DPMS
[    18.312] (II) Loading extension XVideo
[    18.312] (II) Loading extension XVideo-MotionCompensation
[    18.312] (II) Loading extension X-Resource
[    18.312] (II) LoadModule: "dbe"
[    18.312] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    18.312] (II) Module dbe: vendor="X.Org Foundation"
[    18.312]     compiled for 1.9.0, module version = 1.0.0
[    18.312]     Module class: X.Org Server Extension
[    18.312]     ABI class: X.Org Server Extension, version 4.0
[    18.312] (II) Loading extension DOUBLE-BUFFER
[    18.312] (II) LoadModule: "glx"
[    18.312] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    18.312] (II) Module glx: vendor="X.Org Foundation"
[    18.312]     compiled for 1.9.0, module version = 1.0.0
[    18.312]     ABI class: X.Org Server Extension, version 4.0
[    18.312] (==) AIGLX enabled
[    18.313] (II) Loading extension GLX
[    18.313] (II) LoadModule: "record"
[    18.313] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    18.313] (II) Module record: vendor="X.Org Foundation"
[    18.313]     compiled for 1.9.0, module version = 1.13.0
[    18.313]     Module class: X.Org Server Extension
[    18.313]     ABI class: X.Org Server Extension, version 4.0
[    18.313] (II) Loading extension RECORD
[    18.313] (II) LoadModule: "dri"
[    18.313] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    18.313] (II) Module dri: vendor="X.Org Foundation"
[    18.313]     compiled for 1.9.0, module version = 1.0.0
[    18.313]     ABI class: X.Org Server Extension, version 4.0
[    18.313] (II) Loading extension XFree86-DRI
[    18.313] (II) LoadModule: "dri2"
[    18.313] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    18.314] (II) Module dri2: vendor="X.Org Foundation"
[    18.314]     compiled for 1.9.0, module version = 1.2.0
[    18.314]     ABI class: X.Org Server Extension, version 4.0
[    18.314] (II) Loading extension DRI2
[    18.314] (==) Matched intel as autoconfigured driver 0
[    18.314] (==) Matched vesa as autoconfigured driver 1
[    18.314] (==) Matched fbdev as autoconfigured driver 2
[    18.314] (==) Assigned the driver to the xf86ConfigLayout
[    18.314] (II) LoadModule: "intel"
[    18.314] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    18.314] (II) Module intel: vendor="X.Org Foundation"
[    18.314]     compiled for 1.9.0, module version = 2.12.0
[    18.314]     Module class: X.Org Video Driver
[    18.314]     ABI class: X.Org Video Driver, version 8.0
[    18.314] (II) LoadModule: "vesa"
[    18.314] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    18.314] (II) Module vesa: vendor="X.Org Foundation"
[    18.314]     compiled for 1.8.99.905, module version = 2.3.0
[    18.314]     Module class: X.Org Video Driver
[    18.314]     ABI class: X.Org Video Driver, version 8.0
[    18.314] (II) LoadModule: "fbdev"
[    18.314] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    18.314] (II) Module fbdev: vendor="X.Org Foundation"
[    18.314]     compiled for 1.8.99.905, module version = 0.4.2
[    18.314]     ABI class: X.Org Video Driver, version 8.0
[    18.314] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
    Sandybridge, Sandybridge
[    18.315] (II) VESA: driver for VESA chipsets: vesa
[    18.315] (II) FBDEV: driver for framebuffer: fbdev
[    18.315] (++) using VT number 7

[    18.315] (WW) Falling back to old probe method for vesa
[    18.315] (WW) Falling back to old probe method for fbdev
[    18.315] (II) Loading sub module "fbdevhw"
[    18.315] (II) LoadModule: "fbdevhw"
[    18.315] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    18.315] (II) Module fbdevhw: vendor="X.Org Foundation"
[    18.315]     compiled for 1.9.0, module version = 0.0.2
[    18.315]     ABI class: X.Org Video Driver, version 8.0
[    18.316] drmOpenDevice: node name is /dev/dri/card0
[    18.317] drmOpenDevice: open result is 9, (OK)
[    18.317] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    18.317] drmOpenDevice: node name is /dev/dri/card0
[    18.317] drmOpenDevice: open result is 9, (OK)
[    18.317] drmOpenByBusid: drmOpenMinor returns 9
[    18.317] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    18.317] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    18.317] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    18.317] (==) intel(0): RGB weight 888
[    18.317] (==) intel(0): Default visual is TrueColor
[    18.317] (II) intel(0): Integrated Graphics Chipset: Intel(R) Arrandale
[    18.317] (--) intel(0): Chipset: "Arrandale"
[    18.317] (==) intel(0): video overlay key set to 0x101fe
[    18.334] (II) intel(0): Output VGA1 has no monitor section
[    18.334] (II) intel(0): Output LVDS1 has no monitor section
[    18.334] (II) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
[    18.335] (II) intel(0): Output DP1 has no monitor section
[    18.344] (II) intel(0): Output HDMI1 has no monitor section
[    18.345] (II) intel(0): Output DP2 has no monitor section
[    18.362] (II) intel(0): EDID for output VGA1
[    18.362] (II) intel(0): EDID for output LVDS1
[    18.362] (II) intel(0): Manufacturer: SEC  Model: 3155  Serial#: 0
[    18.362] (II) intel(0): Year: 2009  Week: 0
[    18.362] (II) intel(0): EDID Version: 1.3
[    18.362] (II) intel(0): Digital Display Input
[    18.362] (II) intel(0): Max Image Size [cm]: horiz.: 31  vert.: 19
[    18.362] (II) intel(0): Gamma: 2.20
[    18.362] (II) intel(0): No DPMS capabilities specified
[    18.362] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    18.362] (II) intel(0): First detailed timing is preferred mode
[    18.362] (II) intel(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
[    18.362] (II) intel(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
[    18.362] (II) intel(0): Manufacturer's mask: 0
[    18.362] (II) intel(0): Supported detailed timing:
[    18.362] (II) intel(0): clock: 69.3 MHz   Image Size:  293 x 165 mm
[    18.362] (II) intel(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1480 h_border: 0
[    18.362] (II) intel(0): v_active: 768  v_sync: 770  v_sync_end 775 v_blanking: 780 v_border: 0
[    18.362] (II) intel(0): Unknown vendor-specific block f
[    18.362] (II) intel(0):  SAMSUNG
[    18.362] (II) intel(0):  133AT16-301
[    18.362] (II) intel(0): EDID (in hex):
[    18.362] (II) intel(0):     00ffffffffffff004ca3553100000000
[    18.362] (II) intel(0):     00130103801f13780a87f594574f8c27
[    18.362] (II) intel(0):     27505400000001010101010101010101
[    18.362] (II) intel(0):     010101010101121b567250000c303020
[    18.362] (II) intel(0):     250025a5100000190000000f00000000
[    18.362] (II) intel(0):     00000000002387026400000000fe0053
[    18.362] (II) intel(0):     414d53554e470a2020202020000000fe
[    18.362] (II) intel(0):     00313333415431362d3330310a2000b8
[    18.363] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    18.363] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    18.363] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    18.363] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    18.363] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    18.363] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    18.363] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    18.363] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    18.363] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    18.363] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    18.363] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    18.363] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    18.363] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    18.363] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    18.363] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    18.363] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    18.363] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    18.363] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    18.363] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    18.363] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    18.363] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    18.363] (II) intel(0): Printing probed modes for output LVDS1
[    18.363] (II) intel(0): Modeline "1366x768"x60.0   69.30  1366 1414 1446 1480  768 770 775 780 -hsync -vsync (46.8 kHz)
[    18.363] (II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    18.363] (II) intel(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz)
[    18.363] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    18.363] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    18.363] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    18.363] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    18.364] (II) intel(0): EDID for output DP1
[    18.373] (II) intel(0): EDID for output HDMI1
[    18.374] (II) intel(0): EDID for output DP2
[    18.374] (II) intel(0): Output VGA1 disconnected
[    18.374] (II) intel(0): Output LVDS1 connected
[    18.374] (II) intel(0): Output DP1 disconnected
[    18.374] (II) intel(0): Output HDMI1 disconnected
[    18.374] (II) intel(0): Output DP2 disconnected
[    18.374] (II) intel(0): Using exact sizes for initial modes
[    18.374] (II) intel(0): Output LVDS1 using initial mode 1366x768
[    18.374] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    18.374] (II) intel(0): Kernel page flipping support detected, but forcibly disabled.
[    18.374] (==) intel(0): DPI set to (96, 96)
[    18.374] (II) Loading sub module "fb"
[    18.374] (II) LoadModule: "fb"
[    18.374] (II) Loading /usr/lib/xorg/modules/libfb.so
[    18.375] (II) Module fb: vendor="X.Org Foundation"
[    18.375]     compiled for 1.9.0, module version = 1.0.0
[    18.375]     ABI class: X.Org ANSI C Emulation, version 0.4
[    18.375] (II) UnloadModule: "vesa"
[    18.375] (II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    18.375] (II) UnloadModule: "fbdev"
[    18.375] (II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    18.375] (II) UnloadModule: "fbdevhw"
[    18.375] (II) Unloading /usr/lib/xorg/modules/libfbdevhw.so
[    18.375] (==) Depth 24 pixmap format is 32 bpp
[    18.375] (II) intel(0): [DRI2] Setup complete
[    18.375] (II) intel(0): [DRI2]   DRI driver: i965
[    18.375] (**) intel(0): Tiling enabled
[    18.375] (**) intel(0): SwapBuffers wait enabled
[    18.375] (==) intel(0): VideoRam: 262144 KB
[    18.375] (II) intel(0): Allocated new frame buffer 1408x768 stride 5632, tiled
[    18.381] (II) UXA(0): Driver registered support for the following operations:
[    18.381] (II)         solid
[    18.381] (II)         copy
[    18.381] (II)         composite (RENDER acceleration)
[    18.381] (II)         put_image
[    18.381] (II)         get_image
[    18.381] (==) intel(0): Backing store disabled
[    18.381] (==) intel(0): Silken mouse enabled
[    18.381] (II) intel(0): Initializing HW Cursor
[    18.415] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    18.416] (==) intel(0): DPMS enabled
[    18.416] (==) intel(0): Intel XvMC decoder enabled
[    18.416] (II) intel(0): Set up textured video
[    18.416] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[    18.417] (II) intel(0): direct rendering: DRI2 Enabled
[    18.417] (--) RandR disabled
[    18.417] (II) Initializing built-in extension Generic Event Extension
[    18.417] (II) Initializing built-in extension SHAPE
[    18.417] (II) Initializing built-in extension MIT-SHM
[    18.417] (II) Initializing built-in extension XInputExtension
[    18.417] (II) Initializing built-in extension XTEST
[    18.417] (II) Initializing built-in extension BIG-REQUESTS
[    18.417] (II) Initializing built-in extension SYNC
[    18.417] (II) Initializing built-in extension XKEYBOARD
[    18.417] (II) Initializing built-in extension XC-MISC
[    18.417] (II) Initializing built-in extension SECURITY
[    18.417] (II) Initializing built-in extension XINERAMA
[    18.417] (II) Initializing built-in extension XFIXES
[    18.417] (II) Initializing built-in extension RENDER
[    18.417] (II) Initializing built-in extension RANDR
[    18.417] (II) Initializing built-in extension COMPOSITE
[    18.417] (II) Initializing built-in extension DAMAGE
[    18.417] (II) Initializing built-in extension GESTURE
[    18.423] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    18.423] (II) AIGLX: enabled GLX_INTEL_swap_event
[    18.423] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    18.423] (II) AIGLX: enabled GLX_SGI_make_current_read
[    18.423] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    18.424] (II) AIGLX: Loaded and initialized /usr/lib/dri/i965_dri.so
[    18.424] (II) GLX: Initialized DRI2 GL provider for screen 0
[    18.424] (II) intel(0): Setting screen physical size to 361 x 203
[    18.436] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    18.442] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    18.442] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    18.442] (II) LoadModule: "evdev"
[    18.442] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.442] (II) Module evdev: vendor="X.Org Foundation"
[    18.442]     compiled for 1.9.0, module version = 2.3.2
[    18.442]     Module class: X.Org XInput Driver
[    18.442]     ABI class: X.Org XInput driver, version 11.0
[    18.442] (**) Power Button: always reports core events
[    18.442] (**) Power Button: Device: "/dev/input/event2"
[    18.448] (II) Power Button: Found keys
[    18.448] (II) Power Button: Configuring as keyboard
[    18.448] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    18.448] (**) Option "xkb_rules" "evdev"
[    18.448] (**) Option "xkb_model" "evdev"
[    18.448] (**) Option "xkb_layout" "it"
[    18.449] (II) XKB: reuse xkmfile /var/lib/xkb/server-35DF0DEC488035CD7337E5EF69F018BFAFADCAC5.xkm
[    18.450] (II) config/udev: Adding input device Video Bus (/dev/input/event10)
[    18.450] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    18.450] (**) Video Bus: always reports core events
[    18.450] (**) Video Bus: Device: "/dev/input/event10"
[    18.456] (II) Video Bus: Found keys
[    18.456] (II) Video Bus: Configuring as keyboard
[    18.456] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    18.456] (**) Option "xkb_rules" "evdev"
[    18.456] (**) Option "xkb_model" "evdev"
[    18.456] (**) Option "xkb_layout" "it"
[    18.457] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[    18.457] (II) No input driver/identifier specified (ignoring)
[    18.457] (II) config/udev: Adding input device Sleep Button (/dev/input/event0)
[    18.457] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    18.457] (**) Sleep Button: always reports core events
[    18.457] (**) Sleep Button: Device: "/dev/input/event0"
[    18.464] (II) Sleep Button: Found keys
[    18.464] (II) Sleep Button: Configuring as keyboard
[    18.464] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    18.464] (**) Option "xkb_rules" "evdev"
[    18.464] (**) Option "xkb_model" "evdev"
[    18.464] (**) Option "xkb_layout" "it"
[    18.465] (II) config/udev: Adding input device HP Webcam [2 MP Fixed] (/dev/input/event4)
[    18.465] (**) HP Webcam [2 MP Fixed]: Applying InputClass "evdev keyboard catchall"
[    18.465] (**) HP Webcam [2 MP Fixed]: always reports core events
[    18.465] (**) HP Webcam [2 MP Fixed]: Device: "/dev/input/event4"
[    18.472] (II) HP Webcam [2 MP Fixed]: Found keys
[    18.472] (II) HP Webcam [2 MP Fixed]: Configuring as keyboard
[    18.472] (II) XINPUT: Adding extended input device "HP Webcam [2 MP Fixed]" (type: KEYBOARD)
[    18.472] (**) Option "xkb_rules" "evdev"
[    18.472] (**) Option "xkb_model" "evdev"
[    18.472] (**) Option "xkb_layout" "it"
[    18.472] (II) config/udev: Adding input device HDA Intel Mic at Ext Right Jack (/dev/input/event8)
[    18.472] (II) No input driver/identifier specified (ignoring)
[    18.473] (II) config/udev: Adding input device HDA Intel HP Out at Ext Right Jack (/dev/input/event9)
[    18.473] (II) No input driver/identifier specified (ignoring)
[    18.474] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    18.474] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    18.474] (**) AT Translated Set 2 keyboard: always reports core events
[    18.474] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    18.480] (II) AT Translated Set 2 keyboard: Found keys
[    18.480] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    18.480] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    18.480] (**) Option "xkb_rules" "evdev"
[    18.480] (**) Option "xkb_model" "evdev"
[    18.480] (**) Option "xkb_layout" "it"
[    18.480] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event7)
[    18.480] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    18.480] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    18.480] (II) LoadModule: "synaptics"
[    18.480] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    18.480] (II) Module synaptics: vendor="X.Org Foundation"
[    18.481]     compiled for 1.9.0, module version = 1.2.2
[    18.481]     Module class: X.Org XInput Driver
[    18.481]     ABI class: X.Org XInput driver, version 11.0
[    18.481] (II) Synaptics touchpad driver version 1.2.2
[    18.481] (**) Option "Device" "/dev/input/event7"
[    18.513] (II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5590
[    18.513] (II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4686
[    18.513] (II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    18.513] (II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
[    18.513] (II) SynPS/2 Synaptics TouchPad: buttons: left right
[    18.549] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    18.549] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    18.565] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    18.565] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    18.565] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
[    18.565] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    18.565] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    18.589] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    18.589] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    18.589] (II) No input driver/identifier specified (ignoring)
[    18.589] (II) config/udev: Adding input device ST LIS3LV02DL Accelerometer (/dev/input/event6)
[    18.589] (II) No input driver/identifier specified (ignoring)
[    18.589] (II) config/udev: Adding input device ST LIS3LV02DL Accelerometer (/dev/input/js0)
[    18.589] (II) No input driver/identifier specified (ignoring)
[    18.591] (II) config/udev: Adding input device HP WMI hotkeys (/dev/input/event5)
[    18.591] (**) HP WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    18.591] (**) HP WMI hotkeys: always reports core events
[    18.591] (**) HP WMI hotkeys: Device: "/dev/input/event5"
[    18.597] (II) HP WMI hotkeys: Found keys
[    18.597] (II) HP WMI hotkeys: Configuring as keyboard
[    18.597] (II) XINPUT: Adding extended input device "HP WMI hotkeys" (type: KEYBOARD)
[    18.597] (**) Option "xkb_rules" "evdev"
[    18.597] (**) Option "xkb_model" "evdev"
[    18.597] (**) Option "xkb_layout" "it"
[    18.790] (II) intel(0): EDID vendor "SEC", prod id 12629
[    18.790] (II) intel(0): Printing DDC gathered Modelines:
[    18.790] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1480  768 770 775 780 -hsync -vsync (46.8 kHz)
[    18.820] (II) intel(0): EDID vendor "SEC", prod id 12629
[    18.820] (II) intel(0): Printing DDC gathered Modelines:
[    18.820] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1480  768 770 775 780 -hsync -vsync (46.8 kHz)
[    18.866] (II) intel(0): EDID vendor "SEC", prod id 12629
[    18.866] (II) intel(0): Printing DDC gathered Modelines:
[    18.866] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1480  768 770 775 780 -hsync -vsync (46.8 kHz)
[    18.895] (II) intel(0): EDID vendor "SEC", prod id 12629
[    18.895] (II) intel(0): Printing DDC gathered Modelines:
[    18.895] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1480  768 770 775 780 -hsync -vsync (46.8 kHz)
[    19.292] (II) intel(0): EDID vendor "SEC", prod id 12629
[    19.292] (II) intel(0): Printing DDC gathered Modelines:
[    19.292] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1480  768 770 775 780 -hsync -vsync (46.8 kHz)
[    25.615] (II) intel(0): EDID vendor "SEC", prod id 12629
[    25.615] (II) intel(0): Printing DDC gathered Modelines:
[    25.615] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1480  768 770 775 780 -hsync -vsync (46.8 kHz)
[    25.645] (II) intel(0): EDID vendor "SEC", prod id 12629
[    25.645] (II) intel(0): Printing DDC gathered Modelines:
[    25.645] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1480  768 770 775 780 -hsync -vsync (46.8 kHz)
[    25.675] (II) intel(0): EDID vendor "SEC", prod id 12629
[    25.675] (II) intel(0): Printing DDC gathered Modelines:
[    25.675] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1480  768 770 775 780 -hsync -vsync (46.8 kHz)
[    25.704] (II) intel(0): EDID vendor "SEC", prod id 12629
[    25.704] (II) intel(0): Printing DDC gathered Modelines:
[    25.704] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1480  768 770 775 780 -hsync -vsync (46.8 kHz)
[    25.780] (II) intel(0): EDID vendor "SEC", prod id 12629
[    25.780] (II) intel(0): Printing DDC gathered Modelines:
[    25.780] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1480  768 770 775 780 -hsync -vsync (46.8 kHz)
[    26.127] (II) intel(0): EDID vendor "SEC", prod id 12629
[    26.127] (II) intel(0): Printing DDC gathered Modelines:
[    26.127] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1480  768 770 775 780 -hsync -vsync (46.8 kHz)
[    30.967] (II) intel(0): EDID vendor "SEC", prod id 12629
[    30.967] (II) intel(0): Printing DDC gathered Modelines:
[    30.967] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1480  768 770 775 780 -hsync -vsync (46.8 kHz)
[   411.140] (II) intel(0): EDID vendor "SEC", prod id 12629
[   411.140] (II) intel(0): Printing DDC gathered Modelines:
[   411.140] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1480  768 770 775 780 -hsync -vsync (46.8 kHz)
```

Is it correct? If I have the vesa driver, how can i enable the correct driver of the intel graphic card?
I'm really sorry about my incompetence :$
hope u can help me :D thx

---

### Post by OpenKOJU on 2011-08-11
same problem in HP-Pavilion g6-1037 tx with ATI Radeon 6470 grahpics...

---

### Post by Imgoing2LearnUbunt2 on 2012-02-27
Hi there, I just made a post about this similar error, only I was using the 3d accelration effects and they were working fine until a reboot. Thats when I noticed the error. I am using a Toshiba Satelite L655. and I do have an Intel chipset family graphics. I am a newbie to ubuntu though so I dont know how to get this driver issue fixed :( I clicked additional hardware but it didnt say anything just that I didnt have any proprietary hardware or drivers?

---

### Post by Imgoing2LearnUbunt2 on 2012-02-27
> **Fafler said:**
> Do you even have a Intel graphics device?
```
lspci | grep VGA
```

If it doesn't return anything made by Intel, you can safely ignore the error.

If you do, are you using the correct driver? Try looking at /var/log/Xorg.0.log
It should either use the intel or vesa. If it uses the vesa driver almost everything should still work, but stuff like 3D  accelleration are missing.

00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02) Thats the output of what you said do.

---

### Post by Imgoing2LearnUbunt2 on 2012-02-27
I tried to get the update like Ive seen on a lot of posts and I found this site. and it says the same thing you did, but I cant do it because after I restarted It wouldnt lad the desktop. It loads all the way up to the soud (ubuntu drums?) and it just stays black.. Im so lost.. am I going to have to reinstall? and lose all my stuff?? :'(

Im using the live USB right now.

---

### Post by Imgoing2LearnUbunt2 on 2012-02-27
Heres that site telling you how to manually enable the intel graphics. I wouldnt really know how to do this even if my comp would load my desktop.. but maybe it will help one of you and then you can help me get mine working :(

[https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus](https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus)

---

