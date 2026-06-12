---
title: "Just installed 11.10 but stuck on 1024 x 768 screen resolution"
date: 2011-11-27
forum: Hardware
---

### Post by PM47 on 2011-11-27
I've just installed Ubuntu 11.10 on a new machine on the bench using an old 1024 x 768 screen. I've now replaced my old desktop with the new machine and connected my LG Flatron monitor which has a native resolution of 1440 x 900. The desktop display setting only offers 1024 x 768 and 800 x 600 resolutions. I've trawled the web looking for how to re-detect the monitor but drawn a blank. I understood Ubuntu detected this sort of hardware change automagically ?

The XRANDR command in terminal displays the following :

Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096
LVDS1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0*+
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  

There doesn't appear to be an XORG.CONF file mentioned in some articles related to this problem.

The BIOS on the new motherboard (Gigabyte GA-D525TUD) offers no video resolution settings even though the display is integrated into the NM10 chipset.

Do I really have to hack the configuration files to sort this out ? If so can some-one please walk me through doing this as I'm not that confident editing config files :-(

Thanks

---

### Post by 2F4U on 2011-11-27
Did you reboot after connecting the new monitor? It is correct that Ubuntu does not have a xorg.conf file. As most current Linux distributions, Ubuntu uses a version of the X server that is capable of automatically detecting the settings, that are most likely correct.
What graphics card do you have in this machine and is the graphics card able to provide the desired resolution. If in doubt, look into /var/log/Xorg.0.log.

---

### Post by PM47 on 2011-11-27
Yes I tried re-booting, it makes no difference.

It's an intel D525 dual core Atom processor with built in GMA3150 graphics which should be able to support up to 2048 x 1536 resolution as far as I can see. 

Here is /var/log/Xorg.0.log.....

[    11.979] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[    11.979] X Protocol Version 11, Revision 0
[    11.979] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[    11.979] Current Operating System: Linux Ubee02 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:25:36 UTC 2011 i686
[    11.979] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-13-generic root=UUID=59715603-1516-4fa4-b188-41da744a98ef ro quiet splash vt.handoff=7
[    11.979] Build Date: 19 October 2011  05:09:41AM
[    11.980] xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    11.980] Current version of pixman: 0.22.2
[    11.980]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    11.980] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    11.980] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Nov 27 15:39:13 2011
[    11.988] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    11.988] (==) No Layout section.  Using the first Screen section.
[    11.988] (==) No screen section available. Using defaults.
[    11.988] (**) |-->Screen "Default Screen Section" (0)
[    11.989] (**) |   |-->Monitor "<default monitor>"
[    11.989] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    11.989] (==) Automatically adding devices
[    11.989] (==) Automatically enabling devices
[    11.989] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    11.989]     Entry deleted from font path.
[    11.989] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    11.990]     Entry deleted from font path.
[    11.990] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    11.990]     Entry deleted from font path.
[    11.990] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    11.990]     Entry deleted from font path.
[    11.990] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    11.990]     Entry deleted from font path.
[    11.990] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    11.990] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    11.990] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    11.990] (II) Loader magic: 0x823ada0
[    11.990] (II) Module ABI versions:
[    11.990]     X.Org ANSI C Emulation: 0.4
[    11.990]     X.Org Video Driver: 10.0
[    11.990]     X.Org XInput driver : 12.3
[    11.990]     X.Org Server Extension : 5.0
[    11.991] (--) PCI:*(0:0:2:0) 8086:a001:1458:d000 rev 2, Mem @ 0xfdf00000/524288, 0xd0000000/268435456, 0xfdd00000/1048576, I/O @ 0x0000ff00/8
[    11.992] (II) Open ACPI successful (/var/run/acpid.socket)
[    11.992] (II) LoadModule: "extmod"
[    12.018] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    12.018] (II) Module extmod: vendor="X.Org Foundation"
[    12.018]     compiled for 1.10.4, module version = 1.0.0
[    12.018]     Module class: X.Org Server Extension
[    12.018]     ABI class: X.Org Server Extension, version 5.0
[    12.018] (II) Loading extension MIT-SCREEN-SAVER
[    12.018] (II) Loading extension XFree86-VidModeExtension
[    12.018] (II) Loading extension XFree86-DGA
[    12.019] (II) Loading extension DPMS
[    12.019] (II) Loading extension XVideo
[    12.019] (II) Loading extension XVideo-MotionCompensation
[    12.019] (II) Loading extension X-Resource
[    12.019] (II) LoadModule: "dbe"
[    12.019] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    12.020] (II) Module dbe: vendor="X.Org Foundation"
[    12.020]     compiled for 1.10.4, module version = 1.0.0
[    12.020]     Module class: X.Org Server Extension
[    12.020]     ABI class: X.Org Server Extension, version 5.0
[    12.020] (II) Loading extension DOUBLE-BUFFER
[    12.020] (II) LoadModule: "glx"
[    12.021] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    12.021] (II) Module glx: vendor="X.Org Foundation"
[    12.021]     compiled for 1.10.4, module version = 1.0.0
[    12.021]     ABI class: X.Org Server Extension, version 5.0
[    12.021] (==) AIGLX enabled
[    12.021] (II) Loading extension GLX
[    12.021] (II) LoadModule: "record"
[    12.022] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    12.022] (II) Module record: vendor="X.Org Foundation"
[    12.022]     compiled for 1.10.4, module version = 1.13.0
[    12.022]     Module class: X.Org Server Extension
[    12.022]     ABI class: X.Org Server Extension, version 5.0
[    12.022] (II) Loading extension RECORD
[    12.023] (II) LoadModule: "dri"
[    12.023] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    12.024] (II) Module dri: vendor="X.Org Foundation"
[    12.024]     compiled for 1.10.4, module version = 1.0.0
[    12.024]     ABI class: X.Org Server Extension, version 5.0
[    12.024] (II) Loading extension XFree86-DRI
[    12.024] (II) LoadModule: "dri2"
[    12.025] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    12.025] (II) Module dri2: vendor="X.Org Foundation"
[    12.025]     compiled for 1.10.4, module version = 1.2.0
[    12.025]     ABI class: X.Org Server Extension, version 5.0
[    12.025] (II) Loading extension DRI2
[    12.025] (==) Matched intel as autoconfigured driver 0
[    12.025] (==) Matched vesa as autoconfigured driver 1
[    12.025] (==) Matched fbdev as autoconfigured driver 2
[    12.025] (==) Assigned the driver to the xf86ConfigLayout
[    12.025] (II) LoadModule: "intel"
[    12.035] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    12.036] (II) Module intel: vendor="X.Org Foundation"
[    12.036]     compiled for 1.10.4, module version = 2.15.901
[    12.036]     Module class: X.Org Video Driver
[    12.036]     ABI class: X.Org Video Driver, version 10.0
[    12.036] (II) LoadModule: "vesa"
[    12.037] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    12.038] (II) Module vesa: vendor="X.Org Foundation"
[    12.038]     compiled for 1.10.2, module version = 2.3.0
[    12.038]     Module class: X.Org Video Driver
[    12.038]     ABI class: X.Org Video Driver, version 10.0
[    12.038] (II) LoadModule: "fbdev"
[    12.039] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    12.039] (II) Module fbdev: vendor="X.Org Foundation"
[    12.039]     compiled for 1.10.0, module version = 0.4.2
[    12.039]     ABI class: X.Org Video Driver, version 10.0
[    12.039] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
    Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
    Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
    Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
    Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server
[    12.041] (II) VESA: driver for VESA chipsets: vesa
[    12.041] (II) FBDEV: driver for framebuffer: fbdev
[    12.041] (++) using VT number 7

[    12.046] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    12.047] (WW) Falling back to old probe method for vesa
[    12.047] (WW) Falling back to old probe method for fbdev
[    12.047] (II) Loading sub module "fbdevhw"
[    12.047] (II) LoadModule: "fbdevhw"
[    12.048] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    12.049] (II) Module fbdevhw: vendor="X.Org Foundation"
[    12.049]     compiled for 1.10.4, module version = 0.0.2
[    12.049]     ABI class: X.Org Video Driver, version 10.0
[    12.049] drmOpenDevice: node name is /dev/dri/card0
[    12.049] drmOpenDevice: open result is 12, (OK)
[    12.049] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    12.049] drmOpenDevice: node name is /dev/dri/card0
[    12.049] drmOpenDevice: open result is 12, (OK)
[    12.049] drmOpenByBusid: drmOpenMinor returns 12
[    12.049] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    12.050] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    12.050] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    12.050] (==) intel(0): RGB weight 888
[    12.050] (==) intel(0): Default visual is TrueColor
[    12.050] (II) intel(0): Integrated Graphics Chipset: Intel(R) Pineview G
[    12.050] (--) intel(0): Chipset: "Pineview G"
[    12.050] (**) intel(0): Relaxed fencing enabled
[    12.050] (**) intel(0): Wait on SwapBuffers? enabled
[    12.050] (**) intel(0): Triple buffering? enabled
[    12.050] (**) intel(0): Framebuffer tiled
[    12.051] (**) intel(0): Pixmaps tiled
[    12.051] (**) intel(0): 3D buffers tiled
[    12.051] (**) intel(0): SwapBuffers wait enabled
[    12.051] (==) intel(0): video overlay key set to 0x101fe
[    12.051] (II) intel(0): Output LVDS1 has no monitor section
[    12.051] (II) intel(0): found backlight control interface /sys/class/backlight/intel_backlight
[    12.277] (II) intel(0): Output VGA1 has no monitor section
[    12.277] (II) intel(0): EDID for output LVDS1
[    12.278] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    12.278] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    12.278] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    12.278] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    12.278] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    12.278] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    12.278] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    12.278] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    12.278] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    12.278] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    12.278] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    12.278] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    12.278] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    12.278] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    12.278] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    12.278] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    12.278] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    12.278] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    12.279] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    12.279] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    12.279] (II) intel(0): Printing probed modes for output LVDS1
[    12.279] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    12.279] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    12.279] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    12.279] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    12.496] (II) intel(0): EDID for output VGA1
[    12.496] (II) intel(0): Printing probed modes for output VGA1
[    12.496] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    12.496] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    12.496] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    12.496] (II) intel(0): Modeline "848x480"x60.0   33.75  848 864 976 1088  480 486 494 517 +hsync +vsync (31.0 kHz)
[    12.496] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 489 492 525 -hsync -vsync (31.5 kHz)
[    12.496] (II) intel(0): Output LVDS1 connected
[    12.496] (II) intel(0): Output VGA1 connected
[    12.496] (II) intel(0): Using exact sizes for initial modes
[    12.497] (II) intel(0): Output LVDS1 using initial mode 1024x768
[    12.497] (II) intel(0): Output VGA1 using initial mode 1024x768
[    12.497] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    12.497] (II) intel(0): Kernel page flipping support detected, enabling
[    12.497] (==) intel(0): DPI set to (96, 96)
[    12.497] (II) Loading sub module "fb"
[    12.497] (II) LoadModule: "fb"
[    12.497] (II) Loading /usr/lib/xorg/modules/libfb.so
[    12.498] (II) Module fb: vendor="X.Org Foundation"
[    12.498]     compiled for 1.10.4, module version = 1.0.0
[    12.498]     ABI class: X.Org ANSI C Emulation, version 0.4
[    12.498] (II) Loading sub module "dri2"
[    12.498] (II) LoadModule: "dri2"
[    12.498] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    12.498] (II) Module dri2: vendor="X.Org Foundation"
[    12.498]     compiled for 1.10.4, module version = 1.2.0
[    12.498]     ABI class: X.Org Server Extension, version 5.0
[    12.498] (II) UnloadModule: "vesa"
[    12.498] (II) Unloading vesa
[    12.498] (II) UnloadModule: "fbdev"
[    12.498] (II) Unloading fbdev
[    12.498] (II) UnloadModule: "fbdevhw"
[    12.498] (II) Unloading fbdevhw
[    12.499] (==) Depth 24 pixmap format is 32 bpp
[    12.499] (II) intel(0): [DRI2] Setup complete
[    12.499] (II) intel(0): [DRI2]   DRI driver: i915
[    12.499] (II) intel(0): Allocated new frame buffer 1024x768 stride 4096, tiled
[    12.499] (II) UXA(0): Driver registered support for the following operations:
[    12.499] (II)         solid
[    12.499] (II)         copy
[    12.499] (II)         composite (RENDER acceleration)
[    12.499] (II)         put_image
[    12.499] (II)         get_image
[    12.499] (==) intel(0): Backing store disabled
[    12.499] (==) intel(0): Silken mouse enabled
[    12.499] (II) intel(0): Initializing HW Cursor
[    12.528] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    12.528] (==) intel(0): DPMS enabled
[    12.528] (==) intel(0): Intel XvMC decoder disabled
[    12.528] (II) intel(0): Set up textured video
[    12.528] (II) intel(0): Set up overlay video
[    12.529] (II) intel(0): direct rendering: DRI2 Enabled
[    12.529] (==) intel(0): hotplug detection: "enabled"
[    12.529] (--) RandR disabled
[    12.529] (II) Initializing built-in extension Generic Event Extension
[    12.529] (II) Initializing built-in extension SHAPE
[    12.529] (II) Initializing built-in extension MIT-SHM
[    12.529] (II) Initializing built-in extension XInputExtension
[    12.529] (II) Initializing built-in extension XTEST
[    12.529] (II) Initializing built-in extension BIG-REQUESTS
[    12.529] (II) Initializing built-in extension SYNC
[    12.529] (II) Initializing built-in extension XKEYBOARD
[    12.529] (II) Initializing built-in extension XC-MISC
[    12.529] (II) Initializing built-in extension SECURITY
[    12.529] (II) Initializing built-in extension XINERAMA
[    12.529] (II) Initializing built-in extension XFIXES
[    12.529] (II) Initializing built-in extension RENDER
[    12.529] (II) Initializing built-in extension RANDR
[    12.530] (II) Initializing built-in extension COMPOSITE
[    12.530] (II) Initializing built-in extension DAMAGE
[    12.530] (II) Initializing built-in extension GESTURE
[    12.556] (II) AIGLX: Trying DRI driver /usr/lib/i386-linux-gnu/dri/i915_dri.so
[    12.567] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    12.567] (II) AIGLX: enabled GLX_INTEL_swap_event
[    12.567] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    12.567] (II) AIGLX: enabled GLX_SGI_make_current_read
[    12.567] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    12.567] (II) AIGLX: Loaded and initialized i915
[    12.567] (II) GLX: Initialized DRI2 GL provider for screen 0
[    12.569] (II) intel(0): Setting screen physical size to 270 x 203
[    12.607] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    12.629] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    12.629] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    12.629] (II) LoadModule: "evdev"
[    12.630] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    12.632] (II) Module evdev: vendor="X.Org Foundation"
[    12.632]     compiled for 1.10.2, module version = 2.6.0
[    12.632]     Module class: X.Org XInput Driver
[    12.632]     ABI class: X.Org XInput driver, version 12.3
[    12.632] (II) Using input driver 'evdev' for 'Power Button'
[    12.632] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    12.632] (**) Power Button: always reports core events
[    12.632] (**) Power Button: Device: "/dev/input/event1"
[    12.632] (--) Power Button: Found keys
[    12.632] (II) Power Button: Configuring as keyboard
[    12.632] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    12.632] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    12.632] (**) Option "xkb_rules" "evdev"
[    12.632] (**) Option "xkb_model" "pc105"
[    12.632] (**) Option "xkb_layout" "gb"
[    12.640] (II) XKB: reuse xkmfile /var/lib/xkb/server-2B4266AA55228AE7D9557A18F1965DBA19850816.xkm
[    12.649] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    12.649] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    12.649] (II) Using input driver 'evdev' for 'Power Button'
[    12.649] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    12.649] (**) Power Button: always reports core events
[    12.649] (**) Power Button: Device: "/dev/input/event0"
[    12.649] (--) Power Button: Found keys
[    12.649] (II) Power Button: Configuring as keyboard
[    12.649] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    12.650] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    12.650] (**) Option "xkb_rules" "evdev"
[    12.650] (**) Option "xkb_model" "pc105"
[    12.650] (**) Option "xkb_layout" "gb"
[    12.668] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    12.668] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    12.668] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    12.668] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    12.668] (**) AT Translated Set 2 keyboard: always reports core events
[    12.668] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    12.668] (--) AT Translated Set 2 keyboard: Found keys
[    12.668] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    12.668] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    12.668] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    12.668] (**) Option "xkb_rules" "evdev"
[    12.669] (**) Option "xkb_model" "pc105"
[    12.669] (**) Option "xkb_layout" "gb"
[    12.670] (II) config/udev: Adding input device PS/2 Logitech Mouse (/dev/input/event3)
[    12.670] (**) PS/2 Logitech Mouse: Applying InputClass "evdev pointer catchall"
[    12.670] (II) Using input driver 'evdev' for 'PS/2 Logitech Mouse'
[    12.670] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    12.670] (**) PS/2 Logitech Mouse: always reports core events
[    12.670] (**) PS/2 Logitech Mouse: Device: "/dev/input/event3"
[    12.670] (--) PS/2 Logitech Mouse: Found 3 mouse buttons
[    12.670] (--) PS/2 Logitech Mouse: Found relative axes
[    12.671] (--) PS/2 Logitech Mouse: Found x and y relative axes
[    12.671] (II) PS/2 Logitech Mouse: Configuring as mouse
[    12.671] (**) PS/2 Logitech Mouse: YAxisMapping: buttons 4 and 5
[    12.671] (**) PS/2 Logitech Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    12.671] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input3/event3"
[    12.671] (II) XINPUT: Adding extended input device "PS/2 Logitech Mouse" (type: MOUSE)
[    12.671] (II) PS/2 Logitech Mouse: initialized for relative axes.
[    12.671] (**) PS/2 Logitech Mouse: (accel) keeping acceleration scheme 1
[    12.671] (**) PS/2 Logitech Mouse: (accel) acceleration profile 0
[    12.671] (**) PS/2 Logitech Mouse: (accel) acceleration factor: 2.000
[    12.671] (**) PS/2 Logitech Mouse: (accel) acceleration threshold: 4
[    12.672] (II) config/udev: Adding input device PS/2 Logitech Mouse (/dev/input/mouse0)
[    12.672] (II) No input driver/identifier specified (ignoring)
[    78.030] (II) XKB: reuse xkmfile /var/lib/xkb/server-5550814D3DE81657FB75A6E398FC443242E652DD.xkm

---

### Post by PM47 on 2011-11-27
Is this possibly what I need :

[http://www.archlinux.org/packages/extra/i686/xf86-video-intel/](http://www.archlinux.org/packages/extra/i686/xf86-video-intel/)

This driver is supposed to support the 'Pineview' boards, which I think is what I have ?

---

### Post by Robertjm on 2011-11-27
Doing this totally from memory as my Ubuntu machine is not working.

ADMININSTRATION-->PREFERENCES-->RESOLUTION-->AUTO DETECT

If that's not it, poke around in that neighborhood. It should force the O/S to probe the video card hardware.

Good luck!!

Robert

---

### Post by PM47 on 2011-11-27
Ok, it's the LG monitor, not the new PC. I have a TV with a VGA input, if I connect that to the new box and just open the 'Displays' dialogue it correctly identifies the TV and allows me to set it to 1440 x 900 resolution, which works fine, I don't even need to click 'Detect Displays'. If I re-connect the LG monitor it reverts to 1024 x 768 and reports the monitor as 'Unknown'.

Question is - which config file(s) do I need to edit to add the 1440 x 900 resolution to the default 1024 x 768 and 800 x 600 currently available ??

---

### Post by trundlenut on 2011-11-27
Sounds like the LG monitor has a duff EDID. From memory I think you can create a Xorg.conf file and get ubuntu to use it.

---

### Post by Robertjm on 2011-11-27
Do a search for your hmonitor model number and xorg.conf

Here's a thread  someone posted on a similar problem and how he resolved it:

[http://ubuntuforums.org/showthread.php?t=1548438]("http://ubuntuforums.org/showthread.php?t=1548438")

---

### Post by PM47 on 2011-11-28
> **trundlenut said:**
> Sounds like the LG monitor has a duff EDID. From memory I think you can create a Xorg.conf file and get ubuntu to use it.

Yes, that appears to be the case, I tried switching to a console using CTRL-ALT-F1 and I get an error message 'EDID checksum is invalid, remainder is 226'. I don't get a login prompt and can only switch back to the GUI. This means I can't use the console if this monitor is connected so my best course of action is to junk the monitor.

Thanks for all your help.

---

### Post by PM47 on 2011-11-28
For anyone reading this thread in the future - the following is a workaround for this problem (seems to be specific to Ubuntu 11.10) :

Create the Xorg.conf file as follows :

CTRL-ALT-F1 to the virtual console and log in

~$ sudo service lightdm stop              (note 'lightdm' not 'gdm' as noted in other posts)
~$ sudo Xorg -configure
~$ sudo mv ~/xorg.conf.new /etc/X11/xorg.conf
~$ sudo service lightdm start

CTRL-ALT-F7 to exit console

In the Terminal type 'cvt 1440 900' and copy the 'ModeLine' displayed

Create a script file (*.sh) containing the following lines :

xrandr --newmode "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
xrandr --addmode VGA1 1440x900_60.00
xrandr --output VGA1 --mode 1440x900_60.00

Add the script as a startup application.

I'm not sure if I needed to create the xorg.conf file or how to make the change permanent instead of using a script file, but it works for me until I replace the LG monitor :-)

---

