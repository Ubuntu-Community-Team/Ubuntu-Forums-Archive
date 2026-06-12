---
title: "Display Drivers"
date: 2012-01-16
forum: Hardware
---

### Post by intr on 2012-01-16
Hi, i've installed ubuntu 11.10 on my netbook, which has intel gma3150 as igp. But where can I get the display drivers for ubuntu?

---

### Post by MoreOrLess on 2012-01-16
They're already installed...

---

### Post by saneearth on 2012-01-16
Yeah, I think your drivers are installed by default. If you are having issues go to the system settings and look at display and make changes. If you have doubts you could click on the additional drivers icon in system settings and see if anything shows up as an available driver that is "non-free".

---

### Post by intr on 2012-01-16
no, in system info the graphics is not identified, no additional drivers for disp[lay is available

---

### Post by intr on 2012-01-16
and I cannot increase the screen resolution which was easily done in windows with the same monitor.

---

### Post by intr on 2012-01-16
and i find that the display brightness doesnt change although I can just slide the brightness seek bar right or left

---

### Post by MoreOrLess on 2012-01-17
> **intr said:**
> and I cannot increase the screen resolution which was easily done in windows with the same monitor.
The sysinfo unidentified is a bug and you don't need "additional drivers" as intel drivers are all open-source.
As for the resolution, post your /var/log/Xorg.0.log file

---

### Post by intr on 2012-01-17
where can I get the /var/log/Xorg.0.log file?

---

### Post by intr on 2012-01-17
sorry Ok, here is this:
-----------------------------------------------------------------------------------------------------------------------------
[    47.448] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[    47.449] X Protocol Version 11, Revision 0
[    47.449] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[    47.449] Current Operating System: Linux ubuntu 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686
[    47.449] Kernel command line: noprompt cdrom-detect/try-usb=true file=/cdrom/preseed/ubuntu.seed boot=casper persistent initrd=/casper/initrd.lz splash -- BOOT_IMAGE=/casper/vmlinuz 
[    47.449] Build Date: 29 September 2011  12:48:48AM
[    47.449] xorg-server 2:1.10.4-1ubuntu4 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    47.449] Current version of pixman: 0.22.2
[    47.449]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    47.449] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    47.449] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Jan 17 14:06:25 2012
[    47.488] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    47.496] (==) No Layout section.  Using the first Screen section.
[    47.496] (==) No screen section available. Using defaults.
[    47.496] (**) |-->Screen "Default Screen Section" (0)
[    47.496] (**) |   |-->Monitor "<default monitor>"
[    47.497] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    47.497] (==) Automatically adding devices
[    47.497] (==) Automatically enabling devices
[    47.515] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    47.515]     Entry deleted from font path.
[    47.515] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    47.515]     Entry deleted from font path.
[    47.515] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    47.515]     Entry deleted from font path.
[    47.518] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    47.518]     Entry deleted from font path.
[    47.518] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    47.518]     Entry deleted from font path.
[    47.528] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    47.528] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    47.528] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    47.528] (II) Loader magic: 0x823ada0
[    47.528] (II) Module ABI versions:
[    47.528]     X.Org ANSI C Emulation: 0.4
[    47.528]     X.Org Video Driver: 10.0
[    47.528]     X.Org XInput driver : 12.3
[    47.528]     X.Org Server Extension : 5.0
[    47.530] (--) PCI:*(0:0:2:0) 8086:a011:144d:c072 rev 2, Mem @ 0xf0300000/524288, 0xd0000000/268435456, 0xf0000000/1048576, I/O @ 0x000018d0/8
[    47.531] (--) PCI: (0:0:2:1) 8086:a012:144d:c072 rev 2, Mem @ 0xf0380000/524288
[    47.531] (II) Open ACPI successful (/var/run/acpid.socket)
[    47.531] (II) LoadModule: "extmod"
[    47.574] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    47.587] (II) Module extmod: vendor="X.Org Foundation"
[    47.587]     compiled for 1.10.4, module version = 1.0.0
[    47.587]     Module class: X.Org Server Extension
[    47.587]     ABI class: X.Org Server Extension, version 5.0
[    47.587] (II) Loading extension MIT-SCREEN-SAVER
[    47.587] (II) Loading extension XFree86-VidModeExtension
[    47.587] (II) Loading extension XFree86-DGA
[    47.587] (II) Loading extension DPMS
[    47.587] (II) Loading extension XVideo
[    47.587] (II) Loading extension XVideo-MotionCompensation
[    47.587] (II) Loading extension X-Resource
[    47.587] (II) LoadModule: "dbe"
[    47.591] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    47.597] (II) Module dbe: vendor="X.Org Foundation"
[    47.597]     compiled for 1.10.4, module version = 1.0.0
[    47.597]     Module class: X.Org Server Extension
[    47.597]     ABI class: X.Org Server Extension, version 5.0
[    47.597] (II) Loading extension DOUBLE-BUFFER
[    47.597] (II) LoadModule: "glx"
[    47.620] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    47.659] (II) Module glx: vendor="X.Org Foundation"
[    47.659]     compiled for 1.10.4, module version = 1.0.0
[    47.659]     ABI class: X.Org Server Extension, version 5.0
[    47.663] (==) AIGLX enabled
[    47.663] (II) Loading extension GLX
[    47.663] (II) LoadModule: "record"
[    47.711] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    47.721] (II) Module record: vendor="X.Org Foundation"
[    47.721]     compiled for 1.10.4, module version = 1.13.0
[    47.721]     Module class: X.Org Server Extension
[    47.721]     ABI class: X.Org Server Extension, version 5.0
[    47.721] (II) Loading extension RECORD
[    47.722] (II) LoadModule: "dri"
[    47.725] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    47.743] (II) Module dri: vendor="X.Org Foundation"
[    47.743]     compiled for 1.10.4, module version = 1.0.0
[    47.743]     ABI class: X.Org Server Extension, version 5.0
[    47.743] (II) Loading extension XFree86-DRI
[    47.743] (II) LoadModule: "dri2"
[    47.747] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    47.747] (II) Module dri2: vendor="X.Org Foundation"
[    47.747]     compiled for 1.10.4, module version = 1.2.0
[    47.747]     ABI class: X.Org Server Extension, version 5.0
[    47.747] (II) Loading extension DRI2
[    47.747] (==) Matched intel as autoconfigured driver 0
[    47.747] (==) Matched vesa as autoconfigured driver 1
[    47.747] (==) Matched fbdev as autoconfigured driver 2
[    47.747] (==) Assigned the driver to the xf86ConfigLayout
[    47.747] (II) LoadModule: "intel"
[    47.748] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    47.784] (II) Module intel: vendor="X.Org Foundation"
[    47.784]     compiled for 1.10.2.902, module version = 2.15.901
[    47.784]     Module class: X.Org Video Driver
[    47.784]     ABI class: X.Org Video Driver, version 10.0
[    47.784] (II) LoadModule: "vesa"
[    47.786] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    47.789] (II) Module vesa: vendor="X.Org Foundation"
[    47.790]     compiled for 1.10.2, module version = 2.3.0
[    47.790]     Module class: X.Org Video Driver
[    47.790]     ABI class: X.Org Video Driver, version 10.0
[    47.790] (II) LoadModule: "fbdev"
[    47.790] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    47.804] (II) Module fbdev: vendor="X.Org Foundation"
[    47.804]     compiled for 1.10.0, module version = 0.4.2
[    47.804]     ABI class: X.Org Video Driver, version 10.0
[    47.804] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
    Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
    Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
    Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
    Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server
[    47.805] (II) VESA: driver for VESA chipsets: vesa
[    47.805] (II) FBDEV: driver for framebuffer: fbdev
[    47.805] (++) using VT number 7

[    47.812] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    47.812] (WW) Falling back to old probe method for vesa
[    47.812] (WW) Falling back to old probe method for fbdev
[    47.812] (II) Loading sub module "fbdevhw"
[    47.812] (II) LoadModule: "fbdevhw"
[    47.831] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    47.844] (II) Module fbdevhw: vendor="X.Org Foundation"
[    47.844]     compiled for 1.10.4, module version = 0.0.2
[    47.844]     ABI class: X.Org Video Driver, version 10.0
[    47.844] drmOpenDevice: node name is /dev/dri/card0
[    47.845] drmOpenDevice: open result is 12, (OK)
[    47.845] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    47.845] drmOpenDevice: node name is /dev/dri/card0
[    47.845] drmOpenDevice: open result is 12, (OK)
[    47.845] drmOpenByBusid: drmOpenMinor returns 12
[    47.845] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    47.845] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    47.845] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    47.845] (==) intel(0): RGB weight 888
[    47.845] (==) intel(0): Default visual is TrueColor
[    47.845] (II) intel(0): Integrated Graphics Chipset: Intel(R) Pineview GM
[    47.845] (--) intel(0): Chipset: "Pineview GM"
[    47.846] (**) intel(0): Relaxed fencing enabled
[    47.846] (**) intel(0): Wait on SwapBuffers? enabled
[    47.846] (**) intel(0): Triple buffering? enabled
[    47.846] (**) intel(0): Framebuffer tiled
[    47.846] (**) intel(0): Pixmaps tiled
[    47.846] (**) intel(0): 3D buffers tiled
[    47.846] (**) intel(0): SwapBuffers wait enabled
[    47.846] (==) intel(0): video overlay key set to 0x101fe
[    47.846] (II) intel(0): Output LVDS1 has no monitor section
[    47.847] (II) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
[    47.880] (II) intel(0): Output VGA1 has no monitor section
[    47.880] (II) intel(0): EDID for output LVDS1
[    47.880] (II) intel(0): Manufacturer: CMO  Model: 1007  Serial#: 0
[    47.880] (II) intel(0): Year: 2009  Week: 3
[    47.880] (II) intel(0): EDID Version: 1.3
[    47.880] (II) intel(0): Digital Display Input
[    47.880] (II) intel(0): Max Image Size [cm]: horiz.: 22  vert.: 12
[    47.880] (II) intel(0): Gamma: 2.20
[    47.880] (II) intel(0): No DPMS capabilities specified
[    47.880] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    47.880] (II) intel(0): First detailed timing is preferred mode
[    47.880] (II) intel(0): redX: 0.565 redY: 0.348   greenX: 0.343 greenY: 0.585
[    47.880] (II) intel(0): blueX: 0.161 blueY: 0.121   whiteX: 0.313 whiteY: 0.329
[    47.880] (II) intel(0): Manufacturer's mask: 0
[    47.881] (II) intel(0): Supported detailed timing:
[    47.881] (II) intel(0): clock: 54.2 MHz   Image Size:  222 x 125 mm
[    47.881] (II) intel(0): h_active: 1024  h_sync: 1133  h_sync_end 1205 h_blank_end 1386 h_border: 0
[    47.881] (II) intel(0): v_active: 600  v_sync: 607  v_sync_end 620 v_blanking: 652 v_border: 0
[    47.881] (II) intel(0):  N101L6-L01
[    47.881] (II) intel(0):  CMO
[    47.881] (II) intel(0):  N101L6-L01
[    47.881] (II) intel(0): EDID (in hex):
[    47.881] (II) intel(0):     00ffffffffffff000daf071000000000
[    47.881] (II) intel(0):     0313010380160c780acf459059579529
[    47.881] (II) intel(0):     1f505400000001010101010101010101
[    47.881] (II) intel(0):     0101010101012c15006a415834206d48
[    47.881] (II) intel(0):     7d00de7d00000018000000fe004e3130
[    47.881] (II) intel(0):     314c362d4c30310a2020000000fe0043
[    47.881] (II) intel(0):     4d4f0a202020202020202020000000fe
[    47.881] (II) intel(0):     004e3130314c362d4c30310a202000c4
[    47.881] (II) intel(0): EDID vendor "CMO", prod id 4103
[    47.881] (II) intel(0): Printing DDC gathered Modelines:
[    47.881] (II) intel(0): Modeline "1024x600"x0.0   54.20  1024 1133 1205 1386  600 607 620 652 -hsync -vsync (39.1 kHz)
[    47.882] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    47.882] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    47.882] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    47.882] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    47.882] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    47.882] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    47.882] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    47.882] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    47.882] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    47.882] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    47.883] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    47.883] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    47.883] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    47.883] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    47.883] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    47.883] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    47.883] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    47.883] (II) intel(0): Printing probed modes for output LVDS1
[    47.883] (II) intel(0): Modeline "1024x600"x60.0   54.20  1024 1133 1205 1386  600 607 620 652 -hsync -vsync (39.1 kHz)
[    47.883] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    47.883] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    47.883] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    47.920] (II) intel(0): EDID for output VGA1
[    47.920] (II) intel(0): Output LVDS1 connected
[    47.920] (II) intel(0): Output VGA1 disconnected
[    47.920] (II) intel(0): Using exact sizes for initial modes
[    47.920] (II) intel(0): Output LVDS1 using initial mode 1024x600
[    47.920] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    47.920] (II) intel(0): Kernel page flipping support detected, enabling
[    47.920] (**) intel(0): Display dimensions: (220, 120) mm
[    47.920] (**) intel(0): DPI set to (118, 126)
[    47.920] (II) Loading sub module "fb"
[    47.920] (II) LoadModule: "fb"
[    47.922] (II) Loading /usr/lib/xorg/modules/libfb.so
[    47.928] (II) Module fb: vendor="X.Org Foundation"
[    47.928]     compiled for 1.10.4, module version = 1.0.0
[    47.928]     ABI class: X.Org ANSI C Emulation, version 0.4
[    47.928] (II) Loading sub module "dri2"
[    47.928] (II) LoadModule: "dri2"
[    47.929] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    47.929] (II) Module dri2: vendor="X.Org Foundation"
[    47.929]     compiled for 1.10.4, module version = 1.2.0
[    47.929]     ABI class: X.Org Server Extension, version 5.0
[    47.929] (II) UnloadModule: "vesa"
[    47.929] (II) Unloading vesa
[    47.929] (II) UnloadModule: "fbdev"
[    47.929] (II) Unloading fbdev
[    47.930] (II) UnloadModule: "fbdevhw"
[    47.930] (II) Unloading fbdevhw
[    47.930] (==) Depth 24 pixmap format is 32 bpp
[    47.930] (II) intel(0): [DRI2] Setup complete
[    47.930] (II) intel(0): [DRI2]   DRI driver: i915
[    47.930] (II) intel(0): Allocated new frame buffer 1024x600 stride 4096, tiled
[    47.953] (II) UXA(0): Driver registered support for the following operations:
[    47.953] (II)         solid
[    47.953] (II)         copy
[    47.953] (II)         composite (RENDER acceleration)
[    47.953] (II)         put_image
[    47.953] (II)         get_image
[    47.953] (==) intel(0): Backing store disabled
[    47.953] (==) intel(0): Silken mouse enabled
[    47.953] (II) intel(0): Initializing HW Cursor
[    47.974] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    47.985] (==) intel(0): DPMS enabled
[    47.985] (==) intel(0): Intel XvMC decoder disabled
[    47.985] (II) intel(0): Set up textured video
[    47.985] (II) intel(0): Set up overlay video
[    47.985] (II) intel(0): direct rendering: DRI2 Enabled
[    47.985] (==) intel(0): hotplug detection: "enabled"
[    47.986] (--) RandR disabled
[    47.986] (II) Initializing built-in extension Generic Event Extension
[    47.986] (II) Initializing built-in extension SHAPE
[    47.986] (II) Initializing built-in extension MIT-SHM
[    47.986] (II) Initializing built-in extension XInputExtension
[    47.986] (II) Initializing built-in extension XTEST
[    47.986] (II) Initializing built-in extension BIG-REQUESTS
[    47.986] (II) Initializing built-in extension SYNC
[    47.986] (II) Initializing built-in extension XKEYBOARD
[    47.986] (II) Initializing built-in extension XC-MISC
[    47.986] (II) Initializing built-in extension SECURITY
[    47.986] (II) Initializing built-in extension XINERAMA
[    47.986] (II) Initializing built-in extension XFIXES
[    47.986] (II) Initializing built-in extension RENDER
[    47.986] (II) Initializing built-in extension RANDR
[    47.986] (II) Initializing built-in extension COMPOSITE
[    47.986] (II) Initializing built-in extension DAMAGE
[    47.986] (II) Initializing built-in extension GESTURE
[    48.029] (II) AIGLX: Trying DRI driver /usr/lib/i386-linux-gnu/dri/i915_dri.so
[    48.256] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    48.256] (II) AIGLX: enabled GLX_INTEL_swap_event
[    48.256] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    48.256] (II) AIGLX: enabled GLX_SGI_make_current_read
[    48.256] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    48.256] (II) AIGLX: Loaded and initialized i915
[    48.256] (II) GLX: Initialized DRI2 GL provider for screen 0
[    48.258] (II) intel(0): Setting screen physical size to 270 x 158
[    48.497] (II) XKB: generating xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    48.978] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    48.978] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    48.979] (II) LoadModule: "evdev"
[    48.981] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    49.070] (II) Module evdev: vendor="X.Org Foundation"
[    49.070]     compiled for 1.10.2, module version = 2.6.0
[    49.070]     Module class: X.Org XInput Driver
[    49.070]     ABI class: X.Org XInput driver, version 12.3
[    49.070] (II) Using input driver 'evdev' for 'Power Button'
[    49.070] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    49.070] (**) Power Button: always reports core events
[    49.070] (**) Power Button: Device: "/dev/input/event3"
[    49.071] (--) Power Button: Found keys
[    49.071] (II) Power Button: Configuring as keyboard
[    49.071] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    49.071] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    49.071] (**) Option "xkb_rules" "evdev"
[    49.071] (**) Option "xkb_model" "pc105"
[    49.071] (**) Option "xkb_layout" "us"
[    49.079] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    49.079] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    49.079] (II) Using input driver 'evdev' for 'Video Bus'
[    49.079] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    49.079] (**) Video Bus: always reports core events
[    49.079] (**) Video Bus: Device: "/dev/input/event5"
[    49.079] (--) Video Bus: Found keys
[    49.079] (II) Video Bus: Configuring as keyboard
[    49.079] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input5/event5"
[    49.079] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    49.079] (**) Option "xkb_rules" "evdev"
[    49.079] (**) Option "xkb_model" "pc105"
[    49.079] (**) Option "xkb_layout" "us"
[    49.159] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    49.159] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    49.159] (II) Using input driver 'evdev' for 'Power Button'
[    49.159] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    49.159] (**) Power Button: always reports core events
[    49.159] (**) Power Button: Device: "/dev/input/event1"
[    49.172] (--) Power Button: Found keys
[    49.172] (II) Power Button: Configuring as keyboard
[    49.172] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[    49.172] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    49.173] (**) Option "xkb_rules" "evdev"
[    49.173] (**) Option "xkb_model" "pc105"
[    49.173] (**) Option "xkb_layout" "us"
[    49.175] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    49.175] (II) No input driver/identifier specified (ignoring)
[    49.177] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    49.177] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    49.177] (II) Using input driver 'evdev' for 'Sleep Button'
[    49.177] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    49.177] (**) Sleep Button: always reports core events
[    49.178] (**) Sleep Button: Device: "/dev/input/event2"
[    49.178] (--) Sleep Button: Found keys
[    49.178] (II) Sleep Button: Configuring as keyboard
[    49.178] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2/event2"
[    49.178] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    49.178] (**) Option "xkb_rules" "evdev"
[    49.178] (**) Option "xkb_model" "pc105"
[    49.178] (**) Option "xkb_layout" "us"
[    49.202] (II) config/udev: Adding input device HDA Intel Headphone (/dev/input/event10)
[    49.202] (II) No input driver/identifier specified (ignoring)
[    49.203] (II) config/udev: Adding input device HDA Intel Mic (/dev/input/event9)
[    49.203] (II) No input driver/identifier specified (ignoring)
[    49.216] (II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/event6)
[    49.216] (**) Logitech USB-PS/2 Optical Mouse: Applying InputClass "evdev pointer catchall"
[    49.216] (II) Using input driver 'evdev' for 'Logitech USB-PS/2 Optical Mouse'
[    49.216] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    49.217] (**) Logitech USB-PS/2 Optical Mouse: always reports core events
[    49.217] (**) Logitech USB-PS/2 Optical Mouse: Device: "/dev/input/event6"
[    49.217] (--) Logitech USB-PS/2 Optical Mouse: Found 3 mouse buttons
[    49.217] (--) Logitech USB-PS/2 Optical Mouse: Found scroll wheel(s)
[    49.217] (--) Logitech USB-PS/2 Optical Mouse: Found relative axes
[    49.217] (--) Logitech USB-PS/2 Optical Mouse: Found x and y relative axes
[    49.217] (II) Logitech USB-PS/2 Optical Mouse: Configuring as mouse
[    49.217] (II) Logitech USB-PS/2 Optical Mouse: Adding scrollwheel support
[    49.217] (**) Logitech USB-PS/2 Optical Mouse: YAxisMapping: buttons 4 and 5
[    49.217] (**) Logitech USB-PS/2 Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    49.217] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input6/event6"
[    49.217] (II) XINPUT: Adding extended input device "Logitech USB-PS/2 Optical Mouse" (type: MOUSE)
[    49.218] (II) Logitech USB-PS/2 Optical Mouse: initialized for relative axes.
[    49.218] (**) Logitech USB-PS/2 Optical Mouse: (accel) keeping acceleration scheme 1
[    49.218] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration profile 0
[    49.218] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration factor: 2.000
[    49.218] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration threshold: 4
[    49.219] (II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/mouse0)
[    49.219] (II) No input driver/identifier specified (ignoring)
[    49.233] (II) config/udev: Adding input device WebCam SCB-0340N (/dev/input/event7)
[    49.233] (**) WebCam SCB-0340N: Applying InputClass "evdev keyboard catchall"
[    49.233] (II) Using input driver 'evdev' for 'WebCam SCB-0340N'
[    49.233] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    49.233] (**) WebCam SCB-0340N: always reports core events
[    49.233] (**) WebCam SCB-0340N: Device: "/dev/input/event7"
[    49.234] (--) WebCam SCB-0340N: Found keys
[    49.234] (II) WebCam SCB-0340N: Configuring as keyboard
[    49.234] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8:1.0/input/input7/event7"
[    49.234] (II) XINPUT: Adding extended input device "WebCam SCB-0340N" (type: KEYBOARD)
[    49.234] (**) Option "xkb_rules" "evdev"
[    49.234] (**) Option "xkb_model" "pc105"
[    49.234] (**) Option "xkb_layout" "us"
[    49.249] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    49.249] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    49.250] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    49.250] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    49.250] (**) AT Translated Set 2 keyboard: always reports core events
[    49.250] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    49.250] (--) AT Translated Set 2 keyboard: Found keys
[    49.250] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    49.250] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    49.250] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    49.250] (**) Option "xkb_rules" "evdev"
[    49.250] (**) Option "xkb_model" "pc105"
[    49.250] (**) Option "xkb_layout" "us"
[    49.253] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/event8)
[    49.253] (**) ETPS/2 Elantech Touchpad: Applying InputClass "evdev touchpad catchall"
[    49.253] (**) ETPS/2 Elantech Touchpad: Applying InputClass "touchpad catchall"
[    49.253] (II) LoadModule: "synaptics"
[    49.255] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    49.264] (II) Module synaptics: vendor="X.Org Foundation"
[    49.264]     compiled for 1.10.4, module version = 1.4.1
[    49.264]     Module class: X.Org XInput Driver
[    49.264]     ABI class: X.Org XInput driver, version 12.3
[    49.264] (II) Using input driver 'synaptics' for 'ETPS/2 Elantech Touchpad'
[    49.264] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    49.264] (**) ETPS/2 Elantech Touchpad: always reports core events
[    49.264] (**) Option "Device" "/dev/input/event8"
[    49.316] (--) ETPS/2 Elantech Touchpad: x-axis range 8 - 1144
[    49.316] (--) ETPS/2 Elantech Touchpad: y-axis range 8 - 760
[    49.316] (--) ETPS/2 Elantech Touchpad: pressure range 0 - 255
[    49.316] (--) ETPS/2 Elantech Touchpad: finger width range 0 - 15
[    49.316] (--) ETPS/2 Elantech Touchpad: buttons: left right double triple
[    49.360] (--) ETPS/2 Elantech Touchpad: touchpad found
[    49.360] (**) ETPS/2 Elantech Touchpad: always reports core events
[    49.420] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input8/event8"
[    49.420] (II) XINPUT: Adding extended input device "ETPS/2 Elantech Touchpad" (type: TOUCHPAD)
[    49.420] (**) ETPS/2 Elantech Touchpad: (accel) MinSpeed is now constant deceleration 2.5
[    49.420] (**) ETPS/2 Elantech Touchpad: MaxSpeed is now 1.75
[    49.420] (**) ETPS/2 Elantech Touchpad: AccelFactor is now 0.147
[    49.420] (**) ETPS/2 Elantech Touchpad: (accel) keeping acceleration scheme 1
[    49.420] (**) ETPS/2 Elantech Touchpad: (accel) acceleration profile 1
[    49.421] (**) ETPS/2 Elantech Touchpad: (accel) acceleration factor: 2.000
[    49.421] (**) ETPS/2 Elantech Touchpad: (accel) acceleration threshold: 4
[    49.440] (--) ETPS/2 Elantech Touchpad: touchpad found
[    49.441] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/mouse1)
[    49.441] (II) No input driver/identifier specified (ignoring)
[    54.814] (II) intel(0): EDID vendor "CMO", prod id 4103
[    54.814] (II) intel(0): Printing DDC gathered Modelines:
[    54.814] (II) intel(0): Modeline "1024x600"x0.0   54.20  1024 1133 1205 1386  600 607 620 652 -hsync -vsync (39.1 kHz)
[    57.390] (II) intel(0): EDID vendor "CMO", prod id 4103
[    57.390] (II) intel(0): Printing DDC gathered Modelines:
[    57.390] (II) intel(0): Modeline "1024x600"x0.0   54.20  1024 1133 1205 1386  600 607 620 652 -hsync -vsync (39.1 kHz)
[    60.710] (II) intel(0): EDID vendor "CMO", prod id 4103
[    60.710] (II) intel(0): Printing DDC gathered Modelines:
[    60.710] (II) intel(0): Modeline "1024x600"x0.0   54.20  1024 1133 1205 1386  600 607 620 652 -hsync -vsync (39.1 kHz)
[    63.750] (II) intel(0): EDID vendor "CMO", prod id 4103
[    63.750] (II) intel(0): Printing DDC gathered Modelines:
[    63.750] (II) intel(0): Modeline "1024x600"x0.0   54.20  1024 1133 1205 1386  600 607 620 652 -hsync -vsync (39.1 kHz)
[    67.152] (II) XKB: generating xkmfile /var/lib/xkb/server-A77BBE312A49C9FE89948D38B2A8CB84C3CBB410.xkm
[   474.427] (II) intel(0): EDID vendor "CMO", prod id 4103
[   474.427] (II) intel(0): Printing DDC gathered Modelines:
[   474.427] (II) intel(0): Modeline "1024x600"x0.0   54.20  1024 1133 1205 1386  600 607 620 652 -hsync -vsync (39.1 kHz)
[   493.410] (II) intel(0): EDID vendor "CMO", prod id 4103
[   493.411] (II) intel(0): Printing DDC gathered Modelines:
[   493.411] (II) intel(0): Modeline "1024x600"x0.0   54.20  1024 1133 1205 1386  600 607 620 652 -hsync -vsync (39.1 kHz)
[   522.134] (II) intel(0): EDID vendor "CMO", prod id 4103
[   522.134] (II) intel(0): Printing DDC gathered Modelines:
[   522.134] (II) intel(0): Modeline "1024x600"x0.0   54.20  1024 1133 1205 1386  600 607 620 652 -hsync -vsync (39.1 kHz)
[  1135.133] (II) intel(0): EDID vendor "CMO", prod id 4103
[  1135.133] (II) intel(0): Printing DDC gathered Modelines:
[  1135.133] (II) intel(0): Modeline "1024x600"x0.0   54.20  1024 1133 1205 1386  600 607 620 652 -hsync -vsync (39.1 kHz)

---

### Post by Mark Phelps on 2012-01-17
That log indicates, as was told you in post #2, that the drivers are already installed.  

This is not MS Windows, where the first thing you do is go rummaging around for driver updates; this is Linux, where the current drivers are installed automatically for you.

---

### Post by intr on 2012-01-17
but my problem is screen resolution, which is stuck between 1024x600 and 800x600, please help...I do it like:
[http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html)
....and this makes the display overflow off the screen.
But I'm quite sure windows 7 could allow it up to 1280x1024

---

