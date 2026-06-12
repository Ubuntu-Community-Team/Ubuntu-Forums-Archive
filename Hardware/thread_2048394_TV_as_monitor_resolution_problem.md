---
title: "TV as monitor resolution problem"
date: 2012-08-26
forum: Hardware
---

### Post by dmizer on 2012-08-26
I'm running Xubuntu 12.04 (upgraded from 10.04 LTS).

My box has an Intel Corporation 82Q963/Q965 Integrated Graphics Controller (rev 02)

I'm using an Orion TV (model DL32.31B) purchased in Japan as my monitor. The TV is connected to my computer via VGA cable. The TV calls for a resolution of 1280x768 at 60Hz. Unfortunately, Ubuntu does not detect this as a valid resolution, so I have to manually add it with xrandr according to these directions here: [https://wiki.ubuntu.com/X/Config/Resolution#Adding_undetected_resolutions](https://wiki.ubuntu.com/X/Config/Resolution#Adding_undetected_resolutions)

I made the change persistent using these directions: [http://www.sudo-juice.com/lightdm-resolution/](http://www.sudo-juice.com/lightdm-resolution/)

Also of potential importance is the fact that cvt and gtf modelines do not agree with each other. The cvt utility does not output the correct frequency in the modeline whereas gtf does (I'm using the gtf output for my modeline since the cvt modeline doesn't work at all).
```
$ cvt 1280 768 60
# 1280x768 [COLOR="red"]59.87[/COLOR] Hz (CVT) hsync: 47.78 kHz; pclk: 79.50 MHz
Modeline "1280x768_60.00"   79.50  1280 1344 1472 1664  768 771 781 798 -hsync +vsync
```
```
$ gtf 1280 768 60

  # 1280x768 @ [COLOR="red"]60.00[/COLOR] Hz (GTF) hsync: 47.70 kHz; pclk: 80.14 MHz
  Modeline "1280x768_60.00"  80.14  1280 1344 1480 1680  768 769 772 795  -HSync +Vsync
```

The problem is, that upon login, I get about a one in 3 or 4 chance of the screen displaying properly. Otherwise, I get this: [http://www.youtube.com/watch?v=qsxyVY9HcI4](http://www.youtube.com/watch?v=qsxyVY9HcI4)

I am at my troubleshooting end, and any help would be deeply appreciated.

---

### Post by dmizer on 2012-08-27
Bump

---

### Post by sffvba[e0rt on 2012-08-27
Hey...

Have a look at [http://ubuntuforums.org/showthread.php?t=1938447&highlight=native](http://ubuntuforums.org/showthread.php?t=1938447&highlight=native) 

Perhaps some of the info their could assist you (I know I could never get xrandr to work for me)...


404

---

### Post by dmizer on 2012-08-31
Lots of really great information there, but I'm still having problems. According to /var/log/Xorg.0.log my TV is sending some information to the video card, but it doesn't include the desired resolution of 1280x768.

```
/etc/X11$ cat /var/log/Xorg.0.log
[    26.220] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    26.220] X Protocol Version 11, Revision 0
[    26.221] Build Operating System: Linux 2.6.42-26-generic i686 Ubuntu
[    26.221] Current Operating System: Linux tokkyu 3.2.0-29-generic #46-Ubuntu SMP Fri Jul 27 17:04:05 UTC 2012 i686
[    26.221] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-29-generic root=UUID=9181bfb9-9605-4f9e-aba1-0dd3548d5c00 ro quiet splash vt.handoff=7
[    26.221] Build Date: 04 August 2012  01:51:24AM
[    26.221] xorg-server 2:1.11.4-0ubuntu10.7 (For technical support please see http://www.ubuntu.com/support) 
[    26.221] Current version of pixman: 0.24.4
[    26.221] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    26.221] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    26.221] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Aug 31 21:59:08 2012
[    26.239] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    26.239] (==) No Layout section.  Using the first Screen section.
[    26.239] (==) No screen section available. Using defaults.
[    26.239] (**) |-->Screen "Default Screen Section" (0)
[    26.240] (**) |   |-->Monitor "<default monitor>"
[    26.240] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    26.240] (==) Automatically adding devices
[    26.240] (==) Automatically enabling devices
[    26.240] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    26.240] 	Entry deleted from font path.
[    26.240] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    26.240] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    26.240] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    26.240] (II) Loader magic: 0xbf35a0
[    26.240] (II) Module ABI versions:
[    26.240] 	X.Org ANSI C Emulation: 0.4
[    26.240] 	X.Org Video Driver: 11.0
[    26.240] 	X.Org XInput driver : 16.0
[    26.240] 	X.Org Server Extension : 6.0
[    26.241] (--) PCI:*(0:0:2:0) 8086:2992:1028:01da rev 2, Mem @ 0xfea00000/1048576, 0xd0000000/268435456, I/O @ 0x0000ecb8/8
[    26.241] (--) PCI: (0:0:2:1) 8086:2993:1028:01da rev 2, Mem @ 0xfeb00000/1048576
[    26.241] (II) Open ACPI successful (/var/run/acpid.socket)
[    26.241] (II) LoadModule: "extmod"
[    26.260] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    26.260] (II) Module extmod: vendor="X.Org Foundation"
[    26.260] 	compiled for 1.11.3, module version = 1.0.0
[    26.260] 	Module class: X.Org Server Extension
[    26.260] 	ABI class: X.Org Server Extension, version 6.0
[    26.260] (II) Loading extension MIT-SCREEN-SAVER
[    26.260] (II) Loading extension XFree86-VidModeExtension
[    26.260] (II) Loading extension XFree86-DGA
[    26.260] (II) Loading extension DPMS
[    26.260] (II) Loading extension XVideo
[    26.260] (II) Loading extension XVideo-MotionCompensation
[    26.260] (II) Loading extension X-Resource
[    26.260] (II) LoadModule: "dbe"
[    26.260] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    26.260] (II) Module dbe: vendor="X.Org Foundation"
[    26.260] 	compiled for 1.11.3, module version = 1.0.0
[    26.260] 	Module class: X.Org Server Extension
[    26.260] 	ABI class: X.Org Server Extension, version 6.0
[    26.260] (II) Loading extension DOUBLE-BUFFER
[    26.260] (II) LoadModule: "glx"
[    26.260] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    26.261] (II) Module glx: vendor="X.Org Foundation"
[    26.261] 	compiled for 1.11.3, module version = 1.0.0
[    26.261] 	ABI class: X.Org Server Extension, version 6.0
[    26.261] (==) AIGLX enabled
[    26.261] (II) Loading extension GLX
[    26.261] (II) LoadModule: "record"
[    26.261] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    26.261] (II) Module record: vendor="X.Org Foundation"
[    26.261] 	compiled for 1.11.3, module version = 1.13.0
[    26.261] 	Module class: X.Org Server Extension
[    26.261] 	ABI class: X.Org Server Extension, version 6.0
[    26.261] (II) Loading extension RECORD
[    26.261] (II) LoadModule: "dri"
[    26.261] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    26.261] (II) Module dri: vendor="X.Org Foundation"
[    26.261] 	compiled for 1.11.3, module version = 1.0.0
[    26.261] 	ABI class: X.Org Server Extension, version 6.0
[    26.261] (II) Loading extension XFree86-DRI
[    26.261] (II) LoadModule: "dri2"
[    26.262] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    26.262] (II) Module dri2: vendor="X.Org Foundation"
[    26.262] 	compiled for 1.11.3, module version = 1.2.0
[    26.262] 	ABI class: X.Org Server Extension, version 6.0
[    26.262] (II) Loading extension DRI2
[    26.262] (==) Matched intel as autoconfigured driver 0
[    26.262] (==) Matched vesa as autoconfigured driver 1
[    26.262] (==) Matched fbdev as autoconfigured driver 2
[    26.262] (==) Assigned the driver to the xf86ConfigLayout
[    26.262] (II) LoadModule: "intel"
[    26.282] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    26.283] (II) Module intel: vendor="X.Org Foundation"
[    26.283] 	compiled for 1.11.3, module version = 2.17.0
[    26.283] 	Module class: X.Org Video Driver
[    26.283] 	ABI class: X.Org Video Driver, version 11.0
[    26.283] (II) LoadModule: "vesa"
[    26.283] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    26.283] (II) Module vesa: vendor="X.Org Foundation"
[    26.283] 	compiled for 1.11.3, module version = 2.3.0
[    26.283] 	Module class: X.Org Video Driver
[    26.283] 	ABI class: X.Org Video Driver, version 11.0
[    26.283] (II) LoadModule: "fbdev"
[    26.284] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    26.284] (II) Module fbdev: vendor="X.Org Foundation"
[    26.284] 	compiled for 1.11.3, module version = 0.4.2
[    26.284] 	ABI class: X.Org Video Driver, version 11.0
[    26.284] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
	Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
	Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
	Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
	Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server
[    26.284] (II) VESA: driver for VESA chipsets: vesa
[    26.284] (II) FBDEV: driver for framebuffer: fbdev
[    26.284] (++) using VT number 7

[    26.286] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    26.286] (WW) Falling back to old probe method for vesa
[    26.286] (WW) Falling back to old probe method for fbdev
[    26.286] (II) Loading sub module "fbdevhw"
[    26.286] (II) LoadModule: "fbdevhw"
[    26.286] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    26.286] (II) Module fbdevhw: vendor="X.Org Foundation"
[    26.286] 	compiled for 1.11.3, module version = 0.0.2
[    26.286] 	ABI class: X.Org Video Driver, version 11.0
[    26.286] drmOpenDevice: node name is /dev/dri/card0
[    26.287] drmOpenDevice: open result is 9, (OK)
[    26.287] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    26.287] drmOpenDevice: node name is /dev/dri/card0
[    26.287] drmOpenDevice: open result is 9, (OK)
[    26.287] drmOpenByBusid: drmOpenMinor returns 9
[    26.287] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    26.287] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    26.287] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    26.287] (==) intel(0): RGB weight 888
[    26.287] (==) intel(0): Default visual is TrueColor
[    26.287] (II) intel(0): Integrated Graphics Chipset: Intel(R) 965Q
[    26.287] (--) intel(0): Chipset: "965Q"
[    26.287] (**) intel(0): Relaxed fencing enabled
[    26.287] (**) intel(0): Wait on SwapBuffers? enabled
[    26.287] (**) intel(0): Triple buffering? enabled
[    26.287] (**) intel(0): Framebuffer tiled
[    26.287] (**) intel(0): Pixmaps tiled
[    26.287] (**) intel(0): 3D buffers tiled
[    26.287] (**) intel(0): SwapBuffers wait enabled
[    26.287] (==) intel(0): video overlay key set to 0x101fe
[    26.293] (II) intel(0): Output VGA1 has no monitor section
[    26.309] (II) intel(0): Output DVI1 has no monitor section
[    26.330] (II) intel(0): EDID for output VGA1
[    26.330] (II) intel(0): Printing probed modes for output VGA1
[    26.330] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    26.330] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    26.330] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    26.330] (II) intel(0): Modeline "848x480"x60.0   33.75  848 864 976 1088  480 486 494 517 +hsync +vsync (31.0 kHz)
[    26.330] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 489 492 525 -hsync -vsync (31.5 kHz)
[    26.350] (II) intel(0): EDID for output DVI1
[    26.350] (II) intel(0): Output VGA1 connected
[    26.350] (II) intel(0): Output DVI1 disconnected
[    26.350] (II) intel(0): Using fuzzy aspect match for initial modes
[    26.350] (II) intel(0): Output VGA1 using initial mode 1024x768
[    26.350] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    26.350] (II) intel(0): Kernel page flipping support detected, enabling
[    26.350] (==) intel(0): DPI set to (96, 96)
[    26.350] (II) Loading sub module "fb"
[    26.350] (II) LoadModule: "fb"
[    26.350] (II) Loading /usr/lib/xorg/modules/libfb.so
[    26.350] (II) Module fb: vendor="X.Org Foundation"
[    26.350] 	compiled for 1.11.3, module version = 1.0.0
[    26.350] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    26.350] (II) Loading sub module "dri2"
[    26.350] (II) LoadModule: "dri2"
[    26.351] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    26.351] (II) Module dri2: vendor="X.Org Foundation"
[    26.351] 	compiled for 1.11.3, module version = 1.2.0
[    26.351] 	ABI class: X.Org Server Extension, version 6.0
[    26.351] (II) UnloadModule: "vesa"
[    26.351] (II) Unloading vesa
[    26.351] (II) UnloadModule: "fbdev"
[    26.351] (II) Unloading fbdev
[    26.351] (II) UnloadModule: "fbdevhw"
[    26.351] (II) Unloading fbdevhw
[    26.351] (==) Depth 24 pixmap format is 32 bpp
[    26.351] (II) intel(0): [DRI2] Setup complete
[    26.351] (II) intel(0): [DRI2]   DRI driver: i965
[    26.351] (II) intel(0): Allocated new frame buffer 1024x768 stride 4096, tiled
[    26.363] (II) UXA(0): Driver registered support for the following operations:
[    26.363] (II)         solid
[    26.363] (II)         copy
[    26.363] (II)         composite (RENDER acceleration)
[    26.363] (II)         put_image
[    26.363] (II)         get_image
[    26.363] (==) intel(0): Backing store disabled
[    26.363] (==) intel(0): Silken mouse enabled
[    26.363] (II) intel(0): Initializing HW Cursor
[    26.376] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    26.376] (==) intel(0): DPMS enabled
[    26.376] (==) intel(0): Intel XvMC decoder enabled
[    26.376] (II) intel(0): Set up textured video
[    26.376] (II) intel(0): Set up overlay video
[    26.376] (II) intel(0): [XvMC] i965_xvmc driver initialized.
[    26.376] (II) intel(0): direct rendering: DRI2 Enabled
[    26.376] (==) intel(0): hotplug detection: "enabled"
[    26.376] (--) RandR disabled
[    26.376] (II) Initializing built-in extension Generic Event Extension
[    26.376] (II) Initializing built-in extension SHAPE
[    26.376] (II) Initializing built-in extension MIT-SHM
[    26.376] (II) Initializing built-in extension XInputExtension
[    26.376] (II) Initializing built-in extension XTEST
[    26.376] (II) Initializing built-in extension BIG-REQUESTS
[    26.376] (II) Initializing built-in extension SYNC
[    26.376] (II) Initializing built-in extension XKEYBOARD
[    26.376] (II) Initializing built-in extension XC-MISC
[    26.376] (II) Initializing built-in extension SECURITY
[    26.376] (II) Initializing built-in extension XINERAMA
[    26.376] (II) Initializing built-in extension XFIXES
[    26.376] (II) Initializing built-in extension RENDER
[    26.376] (II) Initializing built-in extension RANDR
[    26.376] (II) Initializing built-in extension COMPOSITE
[    26.376] (II) Initializing built-in extension DAMAGE
[    26.391] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    26.391] (II) AIGLX: enabled GLX_INTEL_swap_event
[    26.391] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    26.391] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    26.391] (II) AIGLX: Loaded and initialized i965
[    26.391] (II) GLX: Initialized DRI2 GL provider for screen 0
[    26.392] (II) intel(0): Setting screen physical size to 270 x 203
[    26.414] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    26.417] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    26.417] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    26.417] (II) LoadModule: "evdev"
[    26.418] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    26.418] (II) Module evdev: vendor="X.Org Foundation"
[    26.418] 	compiled for 1.11.3, module version = 2.7.0
[    26.418] 	Module class: X.Org XInput Driver
[    26.418] 	ABI class: X.Org XInput driver, version 16.0
[    26.418] (II) Using input driver 'evdev' for 'Power Button'
[    26.418] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    26.418] (**) Power Button: always reports core events
[    26.418] (**) evdev: Power Button: Device: "/dev/input/event1"
[    26.418] (--) evdev: Power Button: Vendor 0 Product 0x1
[    26.418] (--) evdev: Power Button: Found keys
[    26.418] (II) evdev: Power Button: Configuring as keyboard
[    26.418] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    26.418] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    26.418] (**) Option "xkb_rules" "evdev"
[    26.418] (**) Option "xkb_model" "a4techKB21"
[    26.418] (**) Option "xkb_layout" "jp"
[    26.418] (**) Option "xkb_options" "terminate:ctrl_alt_bksp"
[    26.421] (II) XKB: reuse xkmfile /var/lib/xkb/server-A6A8466844A974A0750883734C5319BA9ADA87CE.xkm
[    26.422] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    26.422] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    26.422] (II) Using input driver 'evdev' for 'Power Button'
[    26.422] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    26.422] (**) Power Button: always reports core events
[    26.422] (**) evdev: Power Button: Device: "/dev/input/event0"
[    26.422] (--) evdev: Power Button: Vendor 0 Product 0x1
[    26.422] (--) evdev: Power Button: Found keys
[    26.422] (II) evdev: Power Button: Configuring as keyboard
[    26.422] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    26.422] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    26.422] (**) Option "xkb_rules" "evdev"
[    26.422] (**) Option "xkb_model" "a4techKB21"
[    26.422] (**) Option "xkb_layout" "jp"
[    26.422] (**) Option "xkb_options" "terminate:ctrl_alt_bksp"
[    26.423] (II) config/udev: Adding input device MLK Sanwa 2.4G Wireless Keyboard (/dev/input/event2)
[    26.423] (**) MLK Sanwa 2.4G Wireless Keyboard: Applying InputClass "evdev keyboard catchall"
[    26.423] (II) Using input driver 'evdev' for 'MLK Sanwa 2.4G Wireless Keyboard'
[    26.423] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    26.423] (**) MLK Sanwa 2.4G Wireless Keyboard: always reports core events
[    26.423] (**) evdev: MLK Sanwa 2.4G Wireless Keyboard: Device: "/dev/input/event2"
[    26.423] (--) evdev: MLK Sanwa 2.4G Wireless Keyboard: Vendor 0x4fc Product 0x5d8
[    26.423] (--) evdev: MLK Sanwa 2.4G Wireless Keyboard: Found keys
[    26.423] (II) evdev: MLK Sanwa 2.4G Wireless Keyboard: Configuring as keyboard
[    26.423] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.1/usb4/4-2/4-2:1.0/input/input2/event2"
[    26.423] (II) XINPUT: Adding extended input device "MLK Sanwa 2.4G Wireless Keyboard" (type: KEYBOARD, id 8)
[    26.423] (**) Option "xkb_rules" "evdev"
[    26.423] (**) Option "xkb_model" "a4techKB21"
[    26.423] (**) Option "xkb_layout" "jp"
[    26.423] (**) Option "xkb_options" "terminate:ctrl_alt_bksp"
[    26.424] (II) config/udev: Adding input device MLK Sanwa 2.4G Wireless Keyboard (/dev/input/event3)
[    26.424] (**) MLK Sanwa 2.4G Wireless Keyboard: Applying InputClass "evdev pointer catchall"
[    26.424] (**) MLK Sanwa 2.4G Wireless Keyboard: Applying InputClass "evdev keyboard catchall"
[    26.424] (II) Using input driver 'evdev' for 'MLK Sanwa 2.4G Wireless Keyboard'
[    26.424] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    26.424] (**) MLK Sanwa 2.4G Wireless Keyboard: always reports core events
[    26.424] (**) evdev: MLK Sanwa 2.4G Wireless Keyboard: Device: "/dev/input/event3"
[    26.424] (--) evdev: MLK Sanwa 2.4G Wireless Keyboard: Vendor 0x4fc Product 0x5d8
[    26.424] (--) evdev: MLK Sanwa 2.4G Wireless Keyboard: Found 9 mouse buttons
[    26.424] (--) evdev: MLK Sanwa 2.4G Wireless Keyboard: Found scroll wheel(s)
[    26.424] (--) evdev: MLK Sanwa 2.4G Wireless Keyboard: Found relative axes
[    26.424] (--) evdev: MLK Sanwa 2.4G Wireless Keyboard: Found x and y relative axes
[    26.424] (--) evdev: MLK Sanwa 2.4G Wireless Keyboard: Found absolute axes
[    26.424] (II) evdev: MLK Sanwa 2.4G Wireless Keyboard: Forcing absolute x/y axes to exist.
[    26.424] (--) evdev: MLK Sanwa 2.4G Wireless Keyboard: Found keys
[    26.424] (II) evdev: MLK Sanwa 2.4G Wireless Keyboard: Configuring as mouse
[    26.424] (II) evdev: MLK Sanwa 2.4G Wireless Keyboard: Configuring as keyboard
[    26.424] (II) evdev: MLK Sanwa 2.4G Wireless Keyboard: Adding scrollwheel support
[    26.424] (**) evdev: MLK Sanwa 2.4G Wireless Keyboard: YAxisMapping: buttons 4 and 5
[    26.424] (**) evdev: MLK Sanwa 2.4G Wireless Keyboard: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    26.424] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.1/usb4/4-2/4-2:1.1/input/input3/event3"
[    26.424] (II) XINPUT: Adding extended input device "MLK Sanwa 2.4G Wireless Keyboard" (type: KEYBOARD, id 9)
[    26.424] (**) Option "xkb_rules" "evdev"
[    26.424] (**) Option "xkb_model" "a4techKB21"
[    26.424] (**) Option "xkb_layout" "jp"
[    26.424] (**) Option "xkb_options" "terminate:ctrl_alt_bksp"
[    26.424] (II) evdev: MLK Sanwa 2.4G Wireless Keyboard: initialized for relative axes.
[    26.424] (WW) evdev: MLK Sanwa 2.4G Wireless Keyboard: ignoring absolute axes.
[    26.424] (**) MLK Sanwa 2.4G Wireless Keyboard: (accel) keeping acceleration scheme 1
[    26.424] (**) MLK Sanwa 2.4G Wireless Keyboard: (accel) acceleration profile 0
[    26.425] (**) MLK Sanwa 2.4G Wireless Keyboard: (accel) acceleration factor: 2.000
[    26.425] (**) MLK Sanwa 2.4G Wireless Keyboard: (accel) acceleration threshold: 4
[    26.425] (II) config/udev: Adding input device MLK Sanwa 2.4G Wireless Keyboard (/dev/input/mouse0)
[    26.425] (II) No input driver specified, ignoring this device.
[    26.425] (II) This device may have been added with another device file.
[    48.651] (II) config/udev: Adding input device Logitech Bluetooth Mouse M555b (/dev/input/event4)
[    48.651] (**) Logitech Bluetooth Mouse M555b: Applying InputClass "evdev pointer catchall"
[    48.651] (II) Using input driver 'evdev' for 'Logitech Bluetooth Mouse M555b'
[    48.651] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    48.651] (**) Logitech Bluetooth Mouse M555b: always reports core events
[    48.651] (**) evdev: Logitech Bluetooth Mouse M555b: Device: "/dev/input/event4"
[    48.651] (--) evdev: Logitech Bluetooth Mouse M555b: Vendor 0x46d Product 0xb009
[    48.651] (--) evdev: Logitech Bluetooth Mouse M555b: Found 20 mouse buttons
[    48.651] (--) evdev: Logitech Bluetooth Mouse M555b: Found scroll wheel(s)
[    48.651] (--) evdev: Logitech Bluetooth Mouse M555b: Found relative axes
[    48.651] (--) evdev: Logitech Bluetooth Mouse M555b: Found x and y relative axes
[    48.652] (II) evdev: Logitech Bluetooth Mouse M555b: Configuring as mouse
[    48.652] (II) evdev: Logitech Bluetooth Mouse M555b: Adding scrollwheel support
[    48.652] (**) evdev: Logitech Bluetooth Mouse M555b: YAxisMapping: buttons 4 and 5
[    48.652] (**) evdev: Logitech Bluetooth Mouse M555b: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    48.652] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.0/bluetooth/hci0/hci0:39/input4/event4"
[    48.652] (II) XINPUT: Adding extended input device "Logitech Bluetooth Mouse M555b" (type: MOUSE, id 10)
[    48.652] (II) evdev: Logitech Bluetooth Mouse M555b: initialized for relative axes.
[    48.652] (**) Logitech Bluetooth Mouse M555b: (accel) keeping acceleration scheme 1
[    48.652] (**) Logitech Bluetooth Mouse M555b: (accel) acceleration profile 0
[    48.652] (**) Logitech Bluetooth Mouse M555b: (accel) acceleration factor: 2.000
[    48.652] (**) Logitech Bluetooth Mouse M555b: (accel) acceleration threshold: 4
[    48.655] (II) config/udev: Adding input device Logitech Bluetooth Mouse M555b (/dev/input/mouse1)
[    48.655] (II) No input driver specified, ignoring this device.
[    48.655] (II) This device may have been added with another device file.
```

I am also having trouble getting a custom EDID because I do not have a Windows install and the Linux tool fails in calling the VBE:
```
$ sudo get-edid
get-edid: get-edid version 2.0.0

	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f00 bx=0x0 cx=0x0
	Function supported
	Call successful

	VBE version 300
	VBE string at 0x2110 "Intel(r)Broadwater-G Graphics Chip Accelerated VGA BIOS"

VBE/DDC service about to be called
	Report DDC capabilities

	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f15 bx=0x0 cx=0x0
	Function supported
	Call successful

	Monitor and video card combination does not support DDC1 transfers
	Monitor and video card combination does not support DDC2 transfers
	0 seconds per 128 byte EDID block transfer
	Screen is not blanked during DDC transfer

Reading next EDID block

VBE/DDC service about to be called
	Read EDID

	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
	Function supported
	Call failed

The EDID data should not be trusted as the VBE call failed
Error: output block unchanged
```

Here's the lshw output for my display:
```
$ sudo lshw -c display
  *-display:0             
       description: VGA compatible controller
       product: 82Q963/Q965 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:42 memory:fea00000-feafffff memory:d0000000-dfffffff ioport:ecb8(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: 82Q963/Q965 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:feb00000-febffff
```

Further assistance would be greatly appreciated.

---

