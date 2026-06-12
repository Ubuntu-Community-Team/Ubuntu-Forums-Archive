---
title: "Xorg -configure will not run"
date: 2013-01-03
forum: Hardware
---

### Post by eoakes on 2013-01-03
I upgraded from ubuntu 11.04 to 12.04 through 11.10. The only resolution  that now works is 800x600. The display is unknown. The display manger gives an option of 1024X768, but using this, the left part of the desktop is off the display.

I am running the same hardware with freeBSD 8.2 at 1280x768 with no problem.

An earlier thread suggested creating an xorg.conf file with the correct parameters for the Intel graphics. 

I tried to run Xorg -configure after booting into recovery mode. I got an error saying that display 0 was running. Also a line saying to remove a file in /tmp that did not exist to get it to run. I did not think to copy the error message to  a file so I could paste it here, but this is the gist of it.

Any idea why Xorg -configure thinks display 0 is running?  Any suggestion on what to do to get it to run?

Are the ubuntu and freesbd xorg.conf enough alike so that I could copy the one from freebsd into ubuntu and not destroy anything when I try booting ubuntu.? 

Hardware:
> # Intel Core 2 Duo Dual-Core E6300 2.8GHz 1066MHz 2MB Cache Processor

# ASRock G31M-S R2.0 Core 2 Quad/ Intel G31/ FSB 1600(OC)/ DDR2/ A&V&L/
MATX Motherboard

Display on motherboard interface

# 4GB (2X2GB) DDR2-1066 PC2 8500 Dual Channel

# Hitachi / WD 1TB 7200 RPM 32MB CACHE SATA 3.0Gb/s

---

### Post by Yellow Pasque on 2013-01-04
- Delete/backup any xorg.conf you created and restart
- Post the /var/log/Xorg.0.log

---

### Post by eoakes on 2013-01-07
Console Error Message when running Xorg -configure from a terminal as root: 
No /etc/X11/xorg.conf
> root@cedric2-l:/home/eto# Xorg -configure

Fatal server error:
Server is already active for display 0
    If this server is no longer running, remove /tmp/.X0-lock
    and start again.


Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 

 ddxSigGiveUp: Closing log
########################
Dump of /var/log/Xorg.0.log

> [    12.123] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    12.123] X Protocol Version 11, Revision 0
[    12.123] Build Operating System: Linux 2.6.42-26-generic i686 Ubuntu
[    12.123] Current Operating System: Linux cedric2-l 3.2.0-35-generic-pae #55-Ubuntu SMP Wed Dec 5 18:04:39 UTC 2012 i686
[    12.123] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-35-generic-pae root=UUID=34d13e9c-7bf7-4eda-aa21-d9461e6c2e12 ro quiet splash vt.handoff=7
[    12.123] Build Date: 29 August 2012  12:10:05AM
[    12.123] xorg-server 2:1.11.4-0ubuntu10.8 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    12.123] Current version of pixman: 0.24.4
[    12.123]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    12.123] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    12.124] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Jan  7 14:35:58 2013
[    12.135] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    12.136] (==) No Layout section.  Using the first Screen section.
[    12.136] (==) No screen section available. Using defaults.
[    12.136] (**) |-->Screen "Default Screen Section" (0)
[    12.136] (**) |   |-->Monitor "<default monitor>"
[    12.136] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    12.136] (==) Automatically adding devices
[    12.136] (==) Automatically enabling devices
[    12.136] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    12.136]     Entry deleted from font path.
[    12.136] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    12.136] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    12.136] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    12.136] (II) Loader magic: 0xb77065a0
[    12.136] (II) Module ABI versions:
[    12.136]     X.Org ANSI C Emulation: 0.4
[    12.136]     X.Org Video Driver: 11.0
[    12.136]     X.Org XInput driver : 16.0
[    12.136]     X.Org Server Extension : 6.0
[    12.136] (--) PCI:*(0:0:2:0) 8086:29c2:1849:29c2 rev 16, Mem @ 0xfea80000/524288, 0xd0000000/268435456, 0xfe900000/1048576, I/O @ 0x0000dc00/8
[    12.137] (II) Open ACPI successful (/var/run/acpid.socket)
[    12.137] (II) LoadModule: "extmod"
[    12.151] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    12.151] (II) Module extmod: vendor="X.Org Foundation"
[    12.151]     compiled for 1.11.3, module version = 1.0.0
[    12.151]     Module class: X.Org Server Extension
[    12.151]     ABI class: X.Org Server Extension, version 6.0
[    12.151] (II) Loading extension MIT-SCREEN-SAVER
[    12.151] (II) Loading extension XFree86-VidModeExtension
[    12.151] (II) Loading extension XFree86-DGA
[    12.151] (II) Loading extension DPMS
[    12.151] (II) Loading extension XVideo
[    12.151] (II) Loading extension XVideo-MotionCompensation
[    12.151] (II) Loading extension X-Resource
[    12.151] (II) LoadModule: "dbe"
[    12.152] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    12.152] (II) Module dbe: vendor="X.Org Foundation"
[    12.152]     compiled for 1.11.3, module version = 1.0.0
[    12.152]     Module class: X.Org Server Extension
[    12.152]     ABI class: X.Org Server Extension, version 6.0
[    12.152] (II) Loading extension DOUBLE-BUFFER
[    12.152] (II) LoadModule: "glx"
[    12.152] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    12.152] (II) Module glx: vendor="X.Org Foundation"
[    12.152]     compiled for 1.11.3, module version = 1.0.0
[    12.152]     ABI class: X.Org Server Extension, version 6.0
[    12.152] (==) AIGLX enabled
[    12.152] (II) Loading extension GLX
[    12.152] (II) LoadModule: "record"
[    12.152] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    12.152] (II) Module record: vendor="X.Org Foundation"
[    12.152]     compiled for 1.11.3, module version = 1.13.0
[    12.152]     Module class: X.Org Server Extension
[    12.152]     ABI class: X.Org Server Extension, version 6.0
[    12.152] (II) Loading extension RECORD
[    12.152] (II) LoadModule: "dri"
[    12.153] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    12.153] (II) Module dri: vendor="X.Org Foundation"
[    12.153]     compiled for 1.11.3, module version = 1.0.0
[    12.153]     ABI class: X.Org Server Extension, version 6.0
[    12.153] (II) Loading extension XFree86-DRI
[    12.153] (II) LoadModule: "dri2"
[    12.153] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    12.153] (II) Module dri2: vendor="X.Org Foundation"
[    12.153]     compiled for 1.11.3, module version = 1.2.0
[    12.153]     ABI class: X.Org Server Extension, version 6.0
[    12.153] (II) Loading extension DRI2
[    12.153] (==) Matched intel as autoconfigured driver 0
[    12.153] (==) Matched vesa as autoconfigured driver 1
[    12.153] (==) Matched fbdev as autoconfigured driver 2
[    12.153] (==) Assigned the driver to the xf86ConfigLayout
[    12.153] (II) LoadModule: "intel"
[    12.153] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    12.153] (II) Module intel: vendor="X.Org Foundation"
[    12.153]     compiled for 1.11.3, module version = 2.17.0
[    12.153]     Module class: X.Org Video Driver
[    12.153]     ABI class: X.Org Video Driver, version 11.0
[    12.153] (II) LoadModule: "vesa"
[    12.154] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    12.159] (II) Module vesa: vendor="X.Org Foundation"
[    12.159]     compiled for 1.11.3, module version = 2.3.0
[    12.159]     Module class: X.Org Video Driver
[    12.159]     ABI class: X.Org Video Driver, version 11.0
[    12.159] (II) LoadModule: "fbdev"
[    12.159] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    12.159] (II) Module fbdev: vendor="X.Org Foundation"
[    12.159]     compiled for 1.11.3, module version = 0.4.2
[    12.159]     ABI class: X.Org Video Driver, version 11.0
[    12.159] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
    Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
    Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
    Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
    Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server
[    12.160] (II) VESA: driver for VESA chipsets: vesa
[    12.160] (II) FBDEV: driver for framebuffer: fbdev
[    12.160] (++) using VT number 7

[    12.161] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    12.161] (WW) Falling back to old probe method for vesa
[    12.161] (WW) Falling back to old probe method for fbdev
[    12.161] (II) Loading sub module "fbdevhw"
[    12.161] (II) LoadModule: "fbdevhw"
[    12.161] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    12.161] (II) Module fbdevhw: vendor="X.Org Foundation"
[    12.161]     compiled for 1.11.3, module version = 0.0.2
[    12.161]     ABI class: X.Org Video Driver, version 11.0
[    12.162] drmOpenDevice: node name is /dev/dri/card0
[    12.162] drmOpenDevice: open result is 9, (OK)
[    12.162] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    12.162] drmOpenDevice: node name is /dev/dri/card0
[    12.162] drmOpenDevice: open result is 9, (OK)
[    12.162] drmOpenByBusid: drmOpenMinor returns 9
[    12.162] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    12.162] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    12.162] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    12.162] (==) intel(0): RGB weight 888
[    12.162] (==) intel(0): Default visual is TrueColor
[    12.162] (II) intel(0): Integrated Graphics Chipset: Intel(R) G33
[    12.162] (--) intel(0): Chipset: "G33"
[    12.162] (**) intel(0): Relaxed fencing enabled
[    12.162] (**) intel(0): Wait on SwapBuffers? enabled
[    12.162] (**) intel(0): Triple buffering? enabled
[    12.162] (**) intel(0): Framebuffer tiled
[    12.162] (**) intel(0): Pixmaps tiled
[    12.162] (**) intel(0): 3D buffers tiled
[    12.162] (**) intel(0): SwapBuffers wait enabled
[    12.162] (==) intel(0): video overlay key set to 0x101fe
[    12.173] (II) intel(0): Output VGA1 has no monitor section
[    12.181] (II) intel(0): EDID for output VGA1
[    12.182] (II) intel(0): Printing probed modes for output VGA1
[    12.182] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    12.182] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    12.182] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    12.182] (II) intel(0): Modeline "848x480"x60.0   33.75  848 864 976 1088  480 486 494 517 +hsync +vsync (31.0 kHz)
[    12.182] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 489 492 525 -hsync -vsync (31.5 kHz)
[    12.182] (II) intel(0): Output VGA1 connected
[    12.182] (II) intel(0): Using fuzzy aspect match for initial modes
[    12.182] (II) intel(0): Output VGA1 using initial mode 1024x768
[    12.182] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    12.182] (II) intel(0): Kernel page flipping support detected, enabling
[    12.182] (==) intel(0): DPI set to (96, 96)
[    12.182] (II) Loading sub module "fb"
[    12.182] (II) LoadModule: "fb"
[    12.182] (II) Loading /usr/lib/xorg/modules/libfb.so
[    12.182] (II) Module fb: vendor="X.Org Foundation"
[    12.182]     compiled for 1.11.3, module version = 1.0.0
[    12.182]     ABI class: X.Org ANSI C Emulation, version 0.4
[    12.182] (II) Loading sub module "dri2"
[    12.182] (II) LoadModule: "dri2"
[    12.182] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    12.182] (II) Module dri2: vendor="X.Org Foundation"
[    12.182]     compiled for 1.11.3, module version = 1.2.0
[    12.182]     ABI class: X.Org Server Extension, version 6.0
[    12.182] (II) UnloadModule: "vesa"
[    12.182] (II) Unloading vesa
[    12.182] (II) UnloadModule: "fbdev"
[    12.182] (II) Unloading fbdev
[    12.182] (II) UnloadModule: "fbdevhw"
[    12.182] (II) Unloading fbdevhw
[    12.182] (==) Depth 24 pixmap format is 32 bpp
[    12.182] (II) intel(0): [DRI2] Setup complete
[    12.182] (II) intel(0): [DRI2]   DRI driver: i915
[    12.182] (II) intel(0): Allocated new frame buffer 1024x768 stride 4096, tiled
[    12.182] (II) UXA(0): Driver registered support for the following operations:
[    12.183] (II)         solid
[    12.183] (II)         copy
[    12.183] (II)         composite (RENDER acceleration)
[    12.183] (II)         put_image
[    12.183] (II)         get_image
[    12.183] (==) intel(0): Backing store disabled
[    12.183] (==) intel(0): Silken mouse enabled
[    12.183] (II) intel(0): Initializing HW Cursor
[    12.200] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    12.200] (==) intel(0): DPMS enabled
[    12.200] (==) intel(0): Intel XvMC decoder disabled
[    12.200] (II) intel(0): Set up textured video
[    12.200] (II) intel(0): Set up overlay video
[    12.200] (II) intel(0): direct rendering: DRI2 Enabled
[    12.200] (==) intel(0): hotplug detection: "enabled"
[    12.200] (--) RandR disabled
[    12.200] (II) Initializing built-in extension Generic Event Extension
[    12.200] (II) Initializing built-in extension SHAPE
[    12.200] (II) Initializing built-in extension MIT-SHM
[    12.200] (II) Initializing built-in extension XInputExtension
[    12.200] (II) Initializing built-in extension XTEST
[    12.200] (II) Initializing built-in extension BIG-REQUESTS
[    12.200] (II) Initializing built-in extension SYNC
[    12.200] (II) Initializing built-in extension XKEYBOARD
[    12.200] (II) Initializing built-in extension XC-MISC
[    12.200] (II) Initializing built-in extension SECURITY
[    12.200] (II) Initializing built-in extension XINERAMA
[    12.200] (II) Initializing built-in extension XFIXES
[    12.200] (II) Initializing built-in extension RENDER
[    12.200] (II) Initializing built-in extension RANDR
[    12.200] (II) Initializing built-in extension COMPOSITE
[    12.200] (II) Initializing built-in extension DAMAGE
[    12.234] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    12.234] (II) AIGLX: enabled GLX_INTEL_swap_event
[    12.234] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    12.234] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    12.234] (II) AIGLX: Loaded and initialized i915
[    12.234] (II) GLX: Initialized DRI2 GL provider for screen 0
[    12.235] (II) intel(0): Setting screen physical size to 270 x 203
[    12.248] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    12.251] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    12.251] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    12.251] (II) LoadModule: "evdev"
[    12.265] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    12.265] (II) Module evdev: vendor="X.Org Foundation"
[    12.265]     compiled for 1.11.3, module version = 2.7.0
[    12.265]     Module class: X.Org XInput Driver
[    12.265]     ABI class: X.Org XInput driver, version 16.0
[    12.265] (II) Using input driver 'evdev' for 'Power Button'
[    12.265] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    12.265] (**) Power Button: always reports core events
[    12.265] (**) evdev: Power Button: Device: "/dev/input/event1"
[    12.265] (--) evdev: Power Button: Vendor 0 Product 0x1
[    12.265] (--) evdev: Power Button: Found keys
[    12.265] (II) evdev: Power Button: Configuring as keyboard
[    12.265] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    12.265] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    12.265] (**) Option "xkb_rules" "evdev"
[    12.265] (**) Option "xkb_model" "pc105"
[    12.265] (**) Option "xkb_layout" "us"
[    12.266] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    12.266] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    12.266] (II) Using input driver 'evdev' for 'Power Button'
[    12.266] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    12.266] (**) Power Button: always reports core events
[    12.266] (**) evdev: Power Button: Device: "/dev/input/event0"
[    12.266] (--) evdev: Power Button: Vendor 0 Product 0x1
[    12.266] (--) evdev: Power Button: Found keys
[    12.266] (II) evdev: Power Button: Configuring as keyboard
[    12.266] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    12.266] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    12.266] (**) Option "xkb_rules" "evdev"
[    12.266] (**) Option "xkb_model" "pc105"
[    12.266] (**) Option "xkb_layout" "us"
[    12.266] (II) config/udev: Adding input device HDA Intel Line (/dev/input/event3)
[    12.266] (II) No input driver specified, ignoring this device.
[    12.266] (II) This device may have been added with another device file.
[    12.266] (II) config/udev: Adding input device HDA Intel Front Mic (/dev/input/event4)
[    12.267] (II) No input driver specified, ignoring this device.
[    12.267] (II) This device may have been added with another device file.
[    12.267] (II) config/udev: Adding input device HDA Intel Rear Mic (/dev/input/event5)
[    12.267] (II) No input driver specified, ignoring this device.
[    12.267] (II) This device may have been added with another device file.
[    12.267] (II) config/udev: Adding input device HDA Intel Front Headphone (/dev/input/event6)
[    12.267] (II) No input driver specified, ignoring this device.
[    12.267] (II) This device may have been added with another device file.
[    12.267] (II) config/udev: Adding input device HDA Intel Line-Out (/dev/input/event7)
[    12.267] (II) No input driver specified, ignoring this device.
[    12.267] (II) This device may have been added with another device file.
[    12.267] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    12.267] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    12.267] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    12.267] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    12.267] (**) AT Translated Set 2 keyboard: always reports core events
[    12.267] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    12.268] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    12.268] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    12.268] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    12.268] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    12.268] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 8)
[    12.268] (**) Option "xkb_rules" "evdev"
[    12.268] (**) Option "xkb_model" "pc105"
[    12.268] (**) Option "xkb_layout" "us"
[    12.268] (II) config/udev: Adding input device ImExPS/2 Logitech Explorer Mouse (/dev/input/event8)
[    12.268] (**) ImExPS/2 Logitech Explorer Mouse: Applying InputClass "evdev pointer catchall"
[    12.268] (II) Using input driver 'evdev' for 'ImExPS/2 Logitech Explorer Mouse'
[    12.268] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    12.268] (**) ImExPS/2 Logitech Explorer Mouse: always reports core events
[    12.268] (**) evdev: ImExPS/2 Logitech Explorer Mouse: Device: "/dev/input/event8"
[    12.268] (--) evdev: ImExPS/2 Logitech Explorer Mouse: Vendor 0x2 Product 0x6
[    12.268] (--) evdev: ImExPS/2 Logitech Explorer Mouse: Found 9 mouse buttons
[    12.268] (--) evdev: ImExPS/2 Logitech Explorer Mouse: Found scroll wheel(s)
[    12.268] (--) evdev: ImExPS/2 Logitech Explorer Mouse: Found relative axes
[    12.268] (--) evdev: ImExPS/2 Logitech Explorer Mouse: Found x and y relative axes
[    12.268] (II) evdev: ImExPS/2 Logitech Explorer Mouse: Configuring as mouse
[    12.268] (II) evdev: ImExPS/2 Logitech Explorer Mouse: Adding scrollwheel support
[    12.268] (**) evdev: ImExPS/2 Logitech Explorer Mouse: YAxisMapping: buttons 4 and 5
[    12.268] (**) evdev: ImExPS/2 Logitech Explorer Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    12.268] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input8/event8"
[    12.268] (II) XINPUT: Adding extended input device "ImExPS/2 Logitech Explorer Mouse" (type: MOUSE, id 9)
[    12.268] (II) evdev: ImExPS/2 Logitech Explorer Mouse: initialized for relative axes.
[    12.268] (**) ImExPS/2 Logitech Explorer Mouse: (accel) keeping acceleration scheme 1
[    12.268] (**) ImExPS/2 Logitech Explorer Mouse: (accel) acceleration profile 0
[    12.268] (**) ImExPS/2 Logitech Explorer Mouse: (accel) acceleration factor: 2.000
[    12.268] (**) ImExPS/2 Logitech Explorer Mouse: (accel) acceleration threshold: 4
[    12.269] (II) config/udev: Adding input device ImExPS/2 Logitech Explorer Mouse (/dev/input/mouse0)
[    12.269] (II) No input driver specified, ignoring this device.
[    12.269] (II) This device may have been added with another device file.
[    15.264] (II) intel(0): Allocated new frame buffer 832x600 stride 4096, tiled
[    37.839] (II) XKB: reuse xkmfile /var/lib/xkb/server-03AF3717FF3AB439A4BAABA686CCB40771CDF520.xkm


---

### Post by steeldriver on 2013-01-07
If you are just switching to a virtual terminal (Ctrl-Alt-F1 and so on) then that doesn't actually kill the X session on VT7

AFAIK you need to either boot into recovery console so there really is no X server, OR kill it from the console VT e.g. stop lightdm

```

# service lightdm stop
# Xorg -configure
# service lightdm start

```

---

### Post by eoakes on 2013-01-07
When I open a recovery session from either the Grub menu or the Ubuntu login menu the filesystem is read only.  I```
 sudo su
``` and try mount ```
mount -o remount,rw /dev/sdb5
``` and```
 mount -o remount,rw /
``` but neither changes the filesystem to read write.

I have tried to change the init level to single user mode, but both ```
telinit 1
``` and ```
shutdown
``` with no parameters give a bunch of error messages and then a dead session.

I found some discussion on the recovery session having the root filesystem read only, but I could not find a solution.

I can't run ```
Xorg -configure
``` successfully from a recovery session if the filesystem is read only. 

I thought that I had tried to run it from a recovery session, with the same error message I show in my previous reply, but I must have been in a terminal.
Do you have any more suggestions?

---

### Post by steeldriver on 2013-01-08
If you boot into recovery mode, you are already root - there is no need to use 'sudo' or 'sudo su'

In recovery mode, [FONT=Courier New]mount -o remount,rw /[/FONT] should work - what error are you getting, exactly? I've only ever seen it fail in cases where the filesystem is corrupted

Alternatively I already mentioned another way to do it via a virtual terminal

[LIST]
[*]hit Ctrl-Alt-F1 (or F2, F3 etc.)
[*]login with your normal user login (assuming your normal user is a member of sudo)
[*]then
[/LIST]
```

sudo service lightdm stop
sudo Xorg -configure
sudo service lightdm start

```That should write an xorg.conf.new file in your home dir

---

### Post by eoakes on 2013-01-08
Running the commands below I was able to get ```
Xorg -configure
```to run. It displayed an error message line  in the console that does not appear in /var/log/Xorg.0.log. I don't remember for sure, but something about xorg.conf.d, and too many screens.
I have attached the /var/log//Xorg.0.log and the generated /root/xorg.conf.new files rather than coying them into the post.

The console that opened f3 was at a higher resolution and the left side was not on the display. 

There seems to be enough problem with the current installed operating system I have tared it to a external disk and may install ubuntu 12.04 or 12.10 from scratch.  12.04 has long term support, that 12.10 does not. Which would you suggest?


> 
[LIST]
[*]hit Ctrl-Alt-F1 (or F2, F3 etc.)
[*]login with your normal user login (assuming your normal user is a member of sudo)
[*]then
[/LIST]
 	Code:
 	sudo service lightdm stop sudo Xorg -configure sudo service lightdm start


Thanks for you help,
Tom

---

### Post by steeldriver on 2013-01-08
I'm running 12.04 and have found it pretty good at least on my hardware (a couple of Thinkpads and an AMD/ATI HTPC) - I can't really comment on 12.10 as I haven't tried it

---

