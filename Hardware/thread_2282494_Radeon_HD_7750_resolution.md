---
title: "Radeon HD 7750 resolution"
date: 2015-06-14
forum: Hardware
---

### Post by paul213 on 2015-06-14
I know there are dozens of threads about this because I have spent 3 days trying them all!

My screen resolution is 1024x768 and I can add 1366x768 with this:

```
xrandr --newmode "1366x768" 85.499 1366 1436 1579 1792 768 771 774 798 +hsync +vsync 
xrandr --addmode DVI-0 1366x768
```

This works, but I have it enter after every startup. I am using the open source drivers (Gallium) and have tried both proprietary drivers in Ubuntu and the ones from the AMD website, but these just give a blank screen. I have tried numerous xorg.conf settings in **etc/X11** and **etc/X11/xorg.conf.d**. This is the current **etc/X11/xorg.conf.d/xorg.conf** file contents (currently I have also placed this in **etc/X11/xorg.conf.d/vesa.conf**):

```
Section "Device"
    Identifier    "Configured Video Device"
    Driver        "vesa"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
        ModeLine        "1366x768" 85.499 1366 1436 1579 1792 768 771 774 798 +hsync +vsync
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
```

This is a shortened version of my Xorg.0.log file:

```
[    14.511] 
X.Org X Server 1.16.0
Release Date: 2014-07-16
[    14.511] X Protocol Version 11, Revision 0
[    14.511] Build Operating System: Linux 3.2.0-70-generic x86_64 Ubuntu
[    14.511] Current Operating System: Linux homer-u 3.16.0-40-generic #54~14.04.1-Ubuntu SMP Wed Jun 10 17:30:45 UTC 2015 x86_64
[    14.511] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.16.0-40-generic root=UUID=586dc896-8042-41b9-9fff-845dc69d8d1a ro quiet splash vt.handoff=7
[    14.511] Build Date: 12 February 2015  11:11:26PM
[    14.511] xorg-server 2:1.16.0-1ubuntu1.2~trusty2 (For technical support please see http://www.ubuntu.com/support) 
[    14.511] Current version of pixman: 0.30.2
[    14.511]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    14.511] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    14.511] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Jun 14 19:30:03 2015
[    14.548] (==) Using config directory: "/etc/X11/xorg.conf.d"
[    14.548] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    14.556] (==) No Layout section.  Using the first Screen section.
[    14.556] (**) |-->Screen "Default Screen" (0)
[    14.556] (**) |   |-->Monitor "Configured Monitor"
[    14.556] (**) |   |-->Device "Configured Video Device"
[    14.556] (==) Automatically adding devices
[    14.556] (==) Automatically enabling devices
[    14.556] (==) Automatically adding GPU devices
[    14.556] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    14.556]     Entry deleted from font path.

...

[    14.556] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    14.556]     Entry deleted from font path.
[    14.556] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    14.556] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    14.556] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    14.556] (II) Loader magic: 0x7fd5a02e2c80
[    14.556] (II) Module ABI versions:
[    14.556]     X.Org ANSI C Emulation: 0.4
[    14.556]     X.Org Video Driver: 18.0
[    14.556]     X.Org XInput driver : 21.0
[    14.556]     X.Org Server Extension : 8.0
[    14.556] (II) xfree86: Adding drm device (/dev/dri/card0)
[    14.557] (--) PCI:*(0:1:0:0) 1002:683f:174b:e213 rev 0, Mem @ 0xd0000000/268435456, 0xfbec0000/262144, I/O @ 0x0000d000/256, BIOS @ 0x????????/131072
[    14.557] (II) LoadModule: "glx"
[    14.565] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    14.650] (II) Module glx: vendor="X.Org Foundation"
[    14.650]     compiled for 1.16.0, module version = 1.0.0
[    14.650]     ABI class: X.Org Server Extension, version 8.0
[    14.650] (==) AIGLX enabled
[    14.650] (II) LoadModule: "vesa"
[    14.650] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    14.650] (II) Module vesa: vendor="X.Org Foundation"
[    14.650]     compiled for 1.16.0, module version = 2.3.3
[    14.650]     Module class: X.Org Video Driver
[    14.650]     ABI class: X.Org Video Driver, version 18.0
[    14.650] (II) VESA: driver for VESA chipsets: vesa
[    14.650] (++) using VT number 7

[    14.650] vesa: Ignoring device with a bound kernel driver
[    14.650] (WW) Falling back to old probe method for vesa
[    14.650] (EE) Screen 0 deleted because of no matching config section.
[    14.650] (II) UnloadModule: "vesa"
[    14.650] (EE) Device(s) detected, but none match those in the config file.
[    14.650] (==) Matched fglrx as autoconfigured driver 0
[    14.650] (==) Matched ati as autoconfigured driver 1
[    14.650] (==) Matched fglrx as autoconfigured driver 2
[    14.650] (==) Matched ati as autoconfigured driver 3
[    14.650] (==) Matched modesetting as autoconfigured driver 4
[    14.650] (==) Matched fbdev as autoconfigured driver 5
[    14.650] (==) Matched vesa as autoconfigured driver 6
[    14.650] (==) Assigned the driver to the xf86ConfigLayout
[    14.650] (II) LoadModule: "fglrx"
[    14.651] (WW) Warning, couldn't open module fglrx
[    14.651] (II) UnloadModule: "fglrx"
[    14.651] (II) Unloading fglrx
[    14.651] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    14.651] (II) LoadModule: "ati"
[    14.651] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    14.651] (II) Module ati: vendor="X.Org Foundation"
[    14.651]     compiled for 1.16.0, module version = 7.4.0
[    14.651]     Module class: X.Org Video Driver
[    14.651]     ABI class: X.Org Video Driver, version 18.0
[    14.651] (II) LoadModule: "radeon"
[    14.651] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    14.658] (II) Module radeon: vendor="X.Org Foundation"
[    14.658]     compiled for 1.16.0, module version = 7.4.0
[    14.658]     Module class: X.Org Video Driver
[    14.658]     ABI class: X.Org Video Driver, version 18.0
[    14.658] (II) LoadModule: "modesetting"
[    14.658] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    14.658] (II) Module modesetting: vendor="X.Org Foundation"
[    14.658]     compiled for 1.16.0, module version = 0.9.0
[    14.658]     Module class: X.Org Video Driver
[    14.658]     ABI class: X.Org Video Driver, version 18.0
[    14.658] (II) LoadModule: "fbdev"
[    14.658] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    14.659] (II) Module fbdev: vendor="X.Org Foundation"
[    14.659]     compiled for 1.16.0, module version = 0.4.4
[    14.659]     Module class: X.Org Video Driver
[    14.659]     ABI class: X.Org Video Driver, version 18.0
[    14.659] (II) LoadModule: "vesa"
[    14.659] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    14.659] (II) Module vesa: vendor="X.Org Foundation"
[    14.659]     compiled for 1.16.0, module version = 2.3.3
[    14.659]     Module class: X.Org Video Driver
[    14.659]     ABI class: X.Org Video Driver, version 18.0
[    14.659] (II) UnloadModule: "vesa"
[    14.659] (II) Unloading vesa
[    14.659] (II) Failed to load module "vesa" (already loaded, 0)
[    14.659] (II) VESA: driver for VESA chipsets: vesa
[    14.659] (II) RADEON: Driver for ATI Radeon chipsets:

.....

[    14.662] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    14.662] (II) FBDEV: driver for framebuffer: fbdev
[    14.662] (++) using VT number 7

[    14.662] (WW) xf86OpenConsole: setpgid failed: Operation not permitted
[    14.662] (WW) xf86OpenConsole: setsid failed: Operation not permitted
[    14.662] vesa: Ignoring device with a bound kernel driver
[    14.663] (WW) Falling back to old probe method for vesa
[    14.663] (II) [KMS] Kernel modesetting enabled.
[    14.663] (WW) Falling back to old probe method for modesetting
[    14.663] (WW) Falling back to old probe method for fbdev
[    14.663] (II) Loading sub module "fbdevhw"
[    14.663] (II) LoadModule: "fbdevhw"
[    14.663] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    14.663] (II) Module fbdevhw: vendor="X.Org Foundation"
[    14.663]     compiled for 1.16.0, module version = 0.0.2
[    14.663]     ABI class: X.Org Video Driver, version 18.0
[    14.663] (EE) Screen 0 deleted because of no matching config section.
[    14.663] (II) UnloadModule: "vesa"
[    14.663] (II) RADEON(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
[    14.663] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    14.663] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    14.663] (==) RADEON(0): Default visual is TrueColor
[    14.663] (==) RADEON(0): RGB weight 888
[    14.663] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    14.663] (--) RADEON(0): Chipset: "VERDE" (ChipID = 0x683f)
[    14.663] (II) Loading sub module "dri2"
[    14.663] (II) LoadModule: "dri2"
[    14.663] (II) Module "dri2" already built-in
[    14.663] (II) Loading sub module "glamoregl"
[    14.663] (II) LoadModule: "glamoregl"
[    14.663] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[    14.704] (II) Module glamoregl: vendor="X.Org Foundation"
[    14.704]     compiled for 1.16.0, module version = 1.0.0
[    14.704]     ABI class: X.Org ANSI C Emulation, version 0.4
[    14.704] (II) glamor: OpenGL accelerated X.org driver based.
[    15.974] (II) glamor: EGL version 1.4 (DRI2):
[    16.115] (II) RADEON(0): glamor detected, initialising EGL layer.
[    16.115] (II) RADEON(0): KMS Color Tiling: enabled
[    16.115] (II) RADEON(0): KMS Color Tiling 2D: enabled
[    16.115] (II) RADEON(0): KMS Pageflipping: enabled
[    16.115] (II) RADEON(0): SwapBuffers wait for vsync: enabled
[    16.132] (II) RADEON(0): Output DisplayPort-0 using monitor section Configured Monitor
[    16.134] (II) RADEON(0): Output HDMI-0 has no monitor section
[    16.145] (II) RADEON(0): Output DVI-0 has no monitor section
[    16.160] (II) RADEON(0): EDID for output DisplayPort-0
[    16.162] (II) RADEON(0): EDID for output HDMI-0
[    16.173] (II) RADEON(0): EDID for output DVI-0
[    16.173] (II) RADEON(0): Printing probed modes for output DVI-0
[    16.173] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    16.173] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    16.173] (II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    16.173] (II) RADEON(0): Modeline "848x480"x60.0   33.75  848 864 976 1088  480 486 494 517 +hsync +vsync (31.0 kHz e)
[    16.173] (II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 489 492 525 -hsync -vsync (31.5 kHz e)
[    16.173] (II) RADEON(0): Output DisplayPort-0 disconnected
[    16.173] (II) RADEON(0): Output HDMI-0 disconnected
[    16.173] (II) RADEON(0): Output DVI-0 connected
[    16.173] (II) RADEON(0): Using exact sizes for initial modes
[    16.173] (II) RADEON(0): Output DVI-0 using initial mode 1024x768
[    16.173] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    16.173] (II) RADEON(0): mem size init: gart size :3fbde000 vram size: s:40000000 visible:3fcc0000
[    16.173] (==) RADEON(0): DPI set to (96, 96)
[    16.173] (II) Loading sub module "fb"
[    16.173] (II) LoadModule: "fb"
[    16.173] (II) Loading /usr/lib/xorg/modules/libfb.so
[    16.173] (II) Module fb: vendor="X.Org Foundation"
[    16.173]     compiled for 1.16.0, module version = 1.0.0
[    16.173]     ABI class: X.Org ANSI C Emulation, version 0.4
[    16.173] (II) Loading sub module "ramdac"
[    16.173] (II) LoadModule: "ramdac"
[    16.173] (II) Module "ramdac" already built-in
[    16.173] (II) UnloadModule: "modesetting"
[    16.174] (II) Unloading modesetting
[    16.174] (II) UnloadModule: "fbdev"
[    16.174] (II) Unloading fbdev
[    16.174] (II) UnloadSubModule: "fbdevhw"
[    16.174] (II) Unloading fbdevhw
[    16.174] (--) Depth 24 pixmap format is 32 bpp
[    16.174] (II) RADEON(0): [DRI2] Setup complete
[    16.174] (II) RADEON(0): [DRI2]   DRI driver: radeonsi
[    16.174] (II) RADEON(0): [DRI2]   VDPAU driver: radeonsi
[    16.174] (II) RADEON(0): Front buffer size: 3072K
[    16.174] (II) RADEON(0): VRAM usage limit set to 937872K
[    16.174] (==) RADEON(0): Backing store enabled
[    16.174] (II) RADEON(0): Direct rendering enabled
[    16.267] (II) RADEON(0): Use GLAMOR acceleration.
[    16.267] (II) RADEON(0): Acceleration enabled
[    16.267] (==) RADEON(0): DPMS enabled
[    16.267] (==) RADEON(0): Silken mouse enabled
[    16.269] (II) RADEON(0): Set up textured video (glamor)
[    16.269] (II) RADEON(0): [XvMC] Associated with GLAMOR Textured Video.
[    16.269] (II) RADEON(0): [XvMC] Extension initialized.
[    16.269] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    16.269] (--) RandR disabled
[    16.274] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    16.274] (II) AIGLX: enabled GLX_ARB_create_context
[    16.274] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    16.274] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    16.274] (II) AIGLX: enabled GLX_INTEL_swap_event
[    16.274] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    16.274] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[    16.274] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[    16.274] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    16.275] (II) AIGLX: Loaded and initialized radeonsi
[    16.275] (II) GLX: Initialized DRI2 GL provider for screen 0
[    16.488] (II) RADEON(0): Setting screen physical size to 270 x 203
[    16.510] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm

...

[    16.530] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=8 (/dev/input/event7)
[    16.530] (II) No input driver specified, ignoring this device.
[    16.530] (II) This device may have been added with another device file.
[    16.530] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=9 (/dev/input/event8)
[    16.530] (II) No input driver specified, ignoring this device.
[    16.530] (II) This device may have been added with another device file.
[    16.531] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=10 (/dev/input/event9)
[    16.531] (II) No input driver specified, ignoring this device.
[    16.531] (II) This device may have been added with another device file.
[    16.531] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=11 (/dev/input/event10)
[    16.531] (II) No input driver specified, ignoring this device.
[    16.531] (II) This device may have been added with another device file.
[    16.531] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=3 (/dev/input/event5)
[    16.531] (II) No input driver specified, ignoring this device.
[    16.531] (II) This device may have been added with another device file.
[    16.531] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=7 (/dev/input/event6)
[    16.531] (II) No input driver specified, ignoring this device.
[    16.531] (II) This device may have been added with another device file.

...

[   172.071] (WW) RADEON(0): radeon_dri2_flip_event_handler: Pageflip completion event has impossible msc 9329 < target_msc 9330
[   178.772] (WW) RADEON(0): radeon_dri2_flip_event_handler: Pageflip completion event has impossible msc 9730 < target_msc 9731

...

[   728.949] (WW) RADEON(0): radeon_dri2_flip_event_handler: Pageflip completion event has impossible msc 42706 < target_msc 42707
[   816.345] (II) XKB: reuse xkmfile /var/lib/xkb/server-F323E7BAACBC9F9AD7017DF7A7FC84748C049BA4.xkm
[  1558.265] (II) XKB: reuse xkmfile /var/lib/xkb/server-F323E7BAACBC9F9AD7017DF7A7FC84748C049BA4.xkm
[  1605.833] (II) XKB: reuse xkmfile /var/lib/xkb/server-F323E7BAACBC9F9AD7017DF7A7FC84748C049BA4.xkm
[  1605.836] (II) RADEON(0): Allocate new frame buffer 1366x768 stride 1408
[  1605.837] (II) RADEON(0): VRAM usage limit set to 936835K
[  1605.859] (II) XKB: reuse xkmfile /var/lib/xkb/server-F323E7BAACBC9F9AD7017DF7A7FC84748C049BA4.xkm
[  1605.861] (II) XKB: reuse xkmfile /var/lib/xkb/server-F323E7BAACBC9F9AD7017DF7A7FC84748C049BA4.xkm
[  1605.877] (WW) RADEON(0): radeon_dri2_flip_event_handler: Pageflip completion event has impossible msc 95293 < target_msc 95294
[  1605.906] (II) XKB: reuse xkmfile /var/lib/xkb/server-F323E7BAACBC9F9AD7017DF7A7FC84748C049BA4.xkm
[  1620.442] (WW) RADEON(0): radeon_dri2_flip_event_handler: Pageflip completion event has impossible msc 96163 < target_msc 96164
[  1620.725] (WW) RADEON(0): radeon_dri2_flip_event_handler: Pageflip completion event has impossible msc 96179 < target_msc 96180

...

[  2225.873] (WW) RADEON(0): radeon_dri2_flip_event_handler: Pageflip completion event has impossible msc 132277 < target_msc 132278
[  2226.023] (WW) RADEON(0): radeon_dri2_flip_event_handler: Pageflip completion event has impossible msc 132285 < target_msc 132286
[  2230.806] (WW) RADEON(0): radeon_dri2_flip_event_handler: Pageflip completion event has impossible msc 132570 < target_msc 132571
[  2265.958] (II) XKB: reuse xkmfile /var/lib/xkb/server-F323E7BAACBC9F9AD7017DF7A7FC84748C049BA4.xkm
[  2267.897] (II) XKB: reuse xkmfile /var/lib/xkb/server-F323E7BAACBC9F9AD7017DF7A7FC84748C049BA4.xkm
[  2270.399] (II) XKB: reuse xkmfile /var/lib/xkb/server-F323E7BAACBC9F9AD7017DF7A7FC84748C049BA4.xkm
[  2271.119] (II) XKB: reuse xkmfile /var/lib/xkb/server-F323E7BAACBC9F9AD7017DF7A7FC84748C049BA4.xkm
[  2276.268] (WW) RADEON(0): radeon_dri2_flip_event_handler: Pageflip completion event has impossible msc 135286 < target_msc 135287

...

[  3166.375] (WW) RADEON(0): radeon_dri2_flip_event_handler: Pageflip completion event has impossible msc 188323 < target_msc 188324
[  3166.426] (WW) RADEON(0): radeon_dri2_flip_event_handler: Pageflip completion event has impossible msc 188325 < target_msc 188326
[  3178.105] (II) XKB: reuse xkmfile /var/lib/xkb/server-F323E7BAACBC9F9AD7017DF7A7FC84748C049BA4.xkm
[  3181.170] (II) XKB: reuse xkmfile /var/lib/xkb/server-F323E7BAACBC9F9AD7017DF7A7FC84748C049BA4.xkm

...

[  3384.937] (II) XKB: reuse xkmfile /var/lib/xkb/server-F323E7BAACBC9F9AD7017DF7A7FC84748C049BA4.xkm
[  3396.357] (WW) RADEON(0): radeon_dri2_flip_event_handler: Pageflip completion event has impossible msc 202064 < target_msc 202065
[  3425.995] (WW) RADEON(0): radeon_dri2_flip_event_handler: Pageflip completion event has impossible msc 203835 < target_msc 203836
[  3431.154] (II) XKB: reuse xkmfile /var/lib/xkb/server-F323E7BAACBC9F9AD7017DF7A7FC84748C049BA4.xkm

...

[  3829.226] (WW) RADEON(0): radeon_dri2_flip_event_handler: Pageflip completion event has impossible msc 227940 < target_msc 227941

...

[  3978.274] (WW) RADEON(0): radeon_dri2_flip_event_handler: Pageflip completion event has impossible msc 236848 < target_msc 236849
```
Before I give up, does anyone have any further ideas or an example of a xorg.conf file that will work? Thanks.

---

### Post by QIII on 2015-06-15
Hello!

Would you describe exactly what you did to install the proprietary fglrx driver?

---

### Post by Yellow Pasque on 2015-06-15
It looks like X is applying your xorg.conf to the wrong output:
```
[    16.132] (II) RADEON(0): Output DisplayPort-0 using monitor section Configured Monitor
```
I don't know how to fix it off the top of my head, but now you/we have something to google..

---

### Post by Yellow Pasque on 2015-06-15
```
       With RandR 1.2-enabled drivers, monitor sections may be tied to specific outputs of the video card.  Using the name of the output defined by the video driver plus the identifier of a monitor section, one associates a  monitor
       section with an output by adding an option to the Device section in the following format:

       Option "Monitor-outputname" "monitorsection"

       (for example, Option "Monitor-VGA" "VGA monitor" for a VGA output)
```
Your output is called DVI-0
```
Output DVI-0 connected
```

---

### Post by Yellow Pasque on 2015-06-15
So just to be a bit more explicit, you would want the xorg.conf to look like the following:
```
Section "Device"
    Identifier    "Configured Video Device"
    Driver        "radeon"
    Option       "Monitor-DVI-0" "Configured Monitor"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
    ModeLine    "1366x768" 85.499 1366 1436 1579 1792 768 771 774 798 +hsync +vsync
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
```

---

### Post by paul213 on 2015-06-15
[**[COLOR=#000000]Temüjin[/COLOR]**]("http://ubuntuforums.org/member.php?u=327594"),

I have used your xorg.conf and it is working perfectly! Thank you for taking the time to help.

[**[COLOR=#C61919][B]QIII**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=628170")
In answer to your question, I used Software Updater > Additional Drivers > 'Using Video Driver for the AMD graphics accelerators'. There are two versions from fglrx and fglrx-updates. Both of these caused a blank screen at startup. I tried reinstalling a couple of times, but could not get these to work. I am now using the default 'X.Org X server' drivers.

I also downloaded the drivers from AMD's website, I think I double-clicked it to install it. I got a warning about it not being good quality and after restating I got a blank screen again.

Now I wonder if it is worth trying to get the fglrx drivers to work, but at least I can see my screen properly!

Thanks again. :)

---

### Post by trinaldi on 2015-06-15
When I first started using Ubuntu I used fglrx. My laptop has an Intel/AMD Hybrid Graphics system, which is a PITA (to say the least).
Anyway, back in those days, removing xorg.conf always restore the blank screen problem.

Now I only use the open source drivers and so far everything is running perfectly, even Hardware Decoding videos. No tearing, no nothing.
Unfortunately, GL based Windows Composers (such as Mutter) has a slight problem with using the dGPU, but I'm not a gamer, so I don't use it too much.

---

### Post by Yellow Pasque on 2015-06-15
> **paul213 said:**
> I have used your xorg.conf and it is working perfectly! Thank you for taking the time to help.
You're welcome. It's actually a pretty neat trick that I wish I would have known about a while ago (because X doesn't always autodetect properly).

> Now I wonder if it is worth trying to get the fglrx drivers to work, but at least I can see my screen properly!
Probably not, unless you're a gamer or need OpenGL 4.x support for some reason.

---

