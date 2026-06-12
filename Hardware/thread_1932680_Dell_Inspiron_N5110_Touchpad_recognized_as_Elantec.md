---
title: "Dell Inspiron N5110 Touchpad recognized as Elantech PS/2 Mouse"
date: 2012-02-27
forum: Hardware
---

### Post by ahsan101 on 2012-02-27
Hello , just migrated from Windows 7 to the Ubuntu 12.04, feeling much comfortable and tension less.
Only one thing which keeps me annoying is that my touchpad works just like a simple mouse which means no two-finger scrolling etc, tried different methods and guides but still no luck,

here is some of my command's output which might help solving the problem!

```
ahsan@ubuntu: tpconfig
tpconfig
Found Synaptics Touchpad.
Firmware: 8.96 (multiple-byte mode).
``````
ahsan@ubuntu: synclient -l
Couldn't find synaptics properties. No synaptics driver loaded?
``````

ahsan@ubuntu: xinput --list
xinput --list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Elantech Mouse                         id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; Power Button                                id=9    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=10    [slave  keyboard (3)]
    &#8627; Laptop_Integrated_Webcam_HD                 id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                            id=14    [slave  keyboard (3)]
```my recemt Xorg.0.log file contains this: 

```
[    26.374] 
X.Org X Server 1.11.99.903 (1.12.0 RC 3)
Release Date: 2012-02-11
[    26.374] X Protocol Version 11, Revision 0
[    26.374] Build Operating System: Linux 2.6.24-30-xen i686 Ubuntu
[    26.374] Current Operating System: Linux dani 3.2.0-17-generic-pae #27-Ubuntu SMP Fri Feb 24 15:59:25 UTC 2012 i686
[    26.374] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-17-generic-pae root=UUID=b980d316-ea48-422a-8ede-1a327fd8e43f ro splash vga=795 quiet splash vt.handoff=7
[    26.374] Build Date: 25 February 2012  03:05:44PM
[    26.374] xorg-server 2:1.11.99.903+git20120224.38000e7d-0ubuntu0sarvatt (For technical support please see http://www.ubuntu.com/support) 
[    26.374] Current version of pixman: 0.24.4
[    26.374]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    26.374] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    26.374] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Feb 28 09:04:07 2012
[    26.381] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    26.381] (==) No Layout section.  Using the first Screen section.
[    26.381] (==) No screen section available. Using defaults.
[    26.381] (**) |-->Screen "Default Screen Section" (0)
[    26.381] (**) |   |-->Monitor "<default monitor>"
[    26.381] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    26.381] (==) Automatically adding devices
[    26.381] (==) Automatically enabling devices
[    26.381] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    26.381]     Entry deleted from font path.
[    26.381] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    26.381]     Entry deleted from font path.
[    26.381] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    26.381]     Entry deleted from font path.
[    26.381] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    26.381]     Entry deleted from font path.
[    26.381] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    26.381]     Entry deleted from font path.
[    26.422] (WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
[    26.422]     Entry deleted from font path.
[    26.422]     (Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType").
[    26.422] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    26.422] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    26.422] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    26.422] (II) Loader magic: 0xb77a85a0
[    26.422] (II) Module ABI versions:
[    26.422]     X.Org ANSI C Emulation: 0.4
[    26.422]     X.Org Video Driver: 12.0
[    26.422]     X.Org XInput driver : 16.0
[    26.422]     X.Org Server Extension : 6.0
[    26.423] (--) PCI:*(0:0:2:0) 8086:0116:1028:04ca rev 9, Mem @ 0xf6400000/4194304, 0xd0000000/268435456, I/O @ 0x0000f000/64
[    26.423] (--) PCI: (0:1:0:0) 10de:0df5:1028:04ca rev 161, Mem @ 0xf5000000/16777216, 0xe0000000/268435456, 0xf0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[    26.423] (II) Open ACPI successful (/var/run/acpid.socket)
[    26.423] (II) LoadModule: "extmod"
[    26.454] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    26.454] (II) Module extmod: vendor="X.Org Foundation"
[    26.454]     compiled for 1.11.99.903, module version = 1.0.0
[    26.454]     Module class: X.Org Server Extension
[    26.454]     ABI class: X.Org Server Extension, version 6.0
[    26.454] (II) Loading extension MIT-SCREEN-SAVER
[    26.454] (II) Loading extension XFree86-VidModeExtension
[    26.454] (II) Loading extension XFree86-DGA
[    26.454] (II) Loading extension DPMS
[    26.454] (II) Loading extension XVideo
[    26.454] (II) Loading extension XVideo-MotionCompensation
[    26.454] (II) Loading extension X-Resource
[    26.454] (II) LoadModule: "dbe"
[    26.454] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    26.454] (II) Module dbe: vendor="X.Org Foundation"
[    26.454]     compiled for 1.11.99.903, module version = 1.0.0
[    26.454]     Module class: X.Org Server Extension
[    26.454]     ABI class: X.Org Server Extension, version 6.0
[    26.454] (II) Loading extension DOUBLE-BUFFER
[    26.454] (II) LoadModule: "glx"
[    26.455] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    26.455] (II) Module glx: vendor="X.Org Foundation"
[    26.455]     compiled for 1.11.99.903, module version = 1.0.0
[    26.455]     ABI class: X.Org Server Extension, version 6.0
[    26.455] (==) AIGLX enabled
[    26.455] (II) Loading extension GLX
[    26.455] (II) LoadModule: "record"
[    26.455] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    26.455] (II) Module record: vendor="X.Org Foundation"
[    26.455]     compiled for 1.11.99.903, module version = 1.13.0
[    26.455]     Module class: X.Org Server Extension
[    26.455]     ABI class: X.Org Server Extension, version 6.0
[    26.455] (II) Loading extension RECORD
[    26.455] (II) LoadModule: "dri"
[    26.455] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    26.455] (II) Module dri: vendor="X.Org Foundation"
[    26.455]     compiled for 1.11.99.903, module version = 1.0.0
[    26.455]     ABI class: X.Org Server Extension, version 6.0
[    26.455] (II) Loading extension XFree86-DRI
[    26.455] (II) LoadModule: "dri2"
[    26.455] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    26.455] (II) Module dri2: vendor="X.Org Foundation"
[    26.455]     compiled for 1.11.99.903, module version = 1.2.0
[    26.455]     ABI class: X.Org Server Extension, version 6.0
[    26.455] (II) Loading extension DRI2
[    26.455] (==) Matched intel as autoconfigured driver 0
[    26.455] (==) Matched vesa as autoconfigured driver 1
[    26.455] (==) Matched fbdev as autoconfigured driver 2
[    26.455] (==) Assigned the driver to the xf86ConfigLayout
[    26.455] (II) LoadModule: "intel"
[    26.456] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    26.456] (II) Module intel: vendor="X.Org Foundation"
[    26.456]     compiled for 1.11.99.903, module version = 2.17.0
[    26.456]     Module class: X.Org Video Driver
[    26.456]     ABI class: X.Org Video Driver, version 12.0
[    26.456] (II) LoadModule: "vesa"
[    26.456] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    26.456] (II) Module vesa: vendor="X.Org Foundation"
[    26.456]     compiled for 1.11.99.901, module version = 2.3.0
[    26.456]     Module class: X.Org Video Driver
[    26.456]     ABI class: X.Org Video Driver, version 12.0
[    26.456] (II) LoadModule: "fbdev"
[    26.456] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    26.456] (II) Module fbdev: vendor="X.Org Foundation"
[    26.456]     compiled for 1.11.99.901, module version = 0.4.2
[    26.456]     Module class: X.Org Video Driver
[    26.456]     ABI class: X.Org Video Driver, version 12.0
[    26.456] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
    Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
    Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
    Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
    Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server
[    26.456] (II) VESA: driver for VESA chipsets: vesa
[    26.456] (II) FBDEV: driver for framebuffer: fbdev
[    26.456] (++) using VT number 7

[    26.457] (WW) Falling back to old probe method for vesa
[    26.457] (WW) Falling back to old probe method for fbdev
[    26.457] (II) Loading sub module "fbdevhw"
[    26.457] (II) LoadModule: "fbdevhw"
[    26.458] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    26.458] (II) Module fbdevhw: vendor="X.Org Foundation"
[    26.458]     compiled for 1.11.99.903, module version = 0.0.2
[    26.458]     ABI class: X.Org Video Driver, version 12.0
[    26.458] drmOpenDevice: node name is /dev/dri/card0
[    26.458] drmOpenDevice: open result is 12, (OK)
[    26.458] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    26.458] drmOpenDevice: node name is /dev/dri/card0
[    26.458] drmOpenDevice: open result is 12, (OK)
[    26.458] drmOpenByBusid: drmOpenMinor returns 12
[    26.458] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    26.458] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    26.458] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    26.458] (==) intel(0): RGB weight 888
[    26.458] (==) intel(0): Default visual is TrueColor
[    26.458] (II) intel(0): Integrated Graphics Chipset: Intel(R) Sandybridge Mobile (GT2)
[    26.458] (--) intel(0): Chipset: "Sandybridge Mobile (GT2)"
[    26.458] (**) intel(0): Relaxed fencing enabled
[    26.458] (**) intel(0): Wait on SwapBuffers? enabled
[    26.458] (**) intel(0): Triple buffering? enabled
[    26.458] (**) intel(0): Framebuffer tiled
[    26.458] (**) intel(0): Pixmaps tiled
[    26.458] (**) intel(0): 3D buffers tiled
[    26.458] (**) intel(0): SwapBuffers wait enabled
[    26.458] (==) intel(0): video overlay key set to 0x101fe
[    26.458] (II) intel(0): Output LVDS1 has no monitor section
[    26.458] (II) intel(0): found backlight control interface /sys/class/backlight/acpi_video1
[    26.458] (II) intel(0): Output VGA1 has no monitor section
[    26.458] (II) intel(0): EDID for output LVDS1
[    26.458] (II) intel(0): Manufacturer: CMO  Model: 15a4  Serial#: 0
[    26.458] (II) intel(0): Year: 2010  Week: 27
[    26.458] (II) intel(0): EDID Version: 1.3
[    26.458] (II) intel(0): Digital Display Input
[    26.458] (II) intel(0): Max Image Size [cm]: horiz.: 34  vert.: 19
[    26.458] (II) intel(0): Gamma: 2.20
[    26.458] (II) intel(0): No DPMS capabilities specified
[    26.458] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    26.458] (II) intel(0): First detailed timing is preferred mode
[    26.458] (II) intel(0): redX: 0.617 redY: 0.340   greenX: 0.320 greenY: 0.598
[    26.458] (II) intel(0): blueX: 0.160 blueY: 0.084   whiteX: 0.313 whiteY: 0.329
[    26.458] (II) intel(0): Manufacturer's mask: 0
[    26.458] (II) intel(0): Supported detailed timing:
[    26.458] (II) intel(0): clock: 76.8 MHz   Image Size:  344 x 194 mm
[    26.458] (II) intel(0): h_active: 1366  h_sync: 1392  h_sync_end 1448 h_blank_end 1580 h_border: 0
[    26.458] (II) intel(0): v_active: 768  v_sync: 772  v_sync_end 785 v_blanking: 810 v_border: 0
[    26.458] (II) intel(0): Supported detailed timing:
[    26.458] (II) intel(0): clock: 76.8 MHz   Image Size:  344 x 194 mm
[    26.458] (II) intel(0): h_active: 1366  h_sync: 1392  h_sync_end 1448 h_blank_end 1580 h_border: 0
[    26.458] (II) intel(0): v_active: 768  v_sync: 772  v_sync_end 785 v_blanking: 810 v_border: 0
[    26.458] (II) intel(0):  XM5XGN156B6
[    26.458] (II) intel(0): Unknown vendor-specific block 0
[    26.458] (II) intel(0): EDID (in hex):
[    26.458] (II) intel(0):     00ffffffffffff000dafa41500000000
[    26.458] (II) intel(0):     1b140103902213780a00259e57529929
[    26.458] (II) intel(0):     15505400000001010101010101010101
[    26.458] (II) intel(0):     010101010101001e56d650002a301a38
[    26.458] (II) intel(0):     4d0058c21000001a001e56d650002a30
[    26.458] (II) intel(0):     1a384d0058c21000001a000000fe0058
[    26.458] (II) intel(0):     4d355847024e31353642360a00000000
[    26.458] (II) intel(0):     00000000000000000001010a20200041
[    26.458] (II) intel(0): EDID vendor "CMO", prod id 5540
[    26.458] (II) intel(0): Printing DDC gathered Modelines:
[    26.458] (II) intel(0): Modeline "1366x768"x0.0   76.80  1366 1392 1448 1580  768 772 785 810 +hsync -vsync (48.6 kHz eP)
[    26.459] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    26.459] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    26.459] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    26.459] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    26.459] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    26.459] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    26.459] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    26.459] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    26.459] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    26.459] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    26.459] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    26.459] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    26.459] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    26.459] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    26.459] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    26.459] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    26.459] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    26.459] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    26.459] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    26.459] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    26.459] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    26.459] (II) intel(0): Printing probed modes for output LVDS1
[    26.459] (II) intel(0): Modeline "1366x768"x60.0   76.80  1366 1392 1448 1580  768 772 785 810 +hsync -vsync (48.6 kHz eP)
[    26.459] (II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz d)
[    26.459] (II) intel(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz d)
[    26.459] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz d)
[    26.459] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz d)
[    26.459] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz d)
[    26.459] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz d)
[    26.459] (II) intel(0): EDID for output VGA1
[    26.459] (II) intel(0): Output LVDS1 connected
[    26.459] (II) intel(0): Output VGA1 disconnected
[    26.459] (II) intel(0): Using exact sizes for initial modes
[    26.459] (II) intel(0): Output LVDS1 using initial mode 1366x768
[    26.459] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    26.459] (II) intel(0): Kernel page flipping support detected, enabling
[    26.459] (**) intel(0): Display dimensions: (340, 190) mm
[    26.459] (**) intel(0): DPI set to (102, 102)
[    26.459] (II) Loading sub module "fb"
[    26.459] (II) LoadModule: "fb"
[    26.459] (II) Loading /usr/lib/xorg/modules/libfb.so
[    26.459] (II) Module fb: vendor="X.Org Foundation"
[    26.459]     compiled for 1.11.99.903, module version = 1.0.0
[    26.459]     ABI class: X.Org ANSI C Emulation, version 0.4
[    26.459] (II) Loading sub module "dri2"
[    26.459] (II) LoadModule: "dri2"
[    26.459] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    26.459] (II) Module dri2: vendor="X.Org Foundation"
[    26.459]     compiled for 1.11.99.903, module version = 1.2.0
[    26.459]     ABI class: X.Org Server Extension, version 6.0
[    26.459] (II) UnloadModule: "vesa"
[    26.459] (II) Unloading vesa
[    26.459] (II) UnloadModule: "fbdev"
[    26.459] (II) Unloading fbdev
[    26.459] (II) UnloadSubModule: "fbdevhw"
[    26.459] (II) Unloading fbdevhw
[    26.459] (==) Depth 24 pixmap format is 32 bpp
[    26.459] (II) intel(0): [DRI2] Setup complete
[    26.459] (II) intel(0): [DRI2]   DRI driver: i965
[    26.459] (II) intel(0): Allocated new frame buffer 1408x768 stride 5632, tiled
[    26.460] (II) UXA(0): Driver registered support for the following operations:
[    26.460] (II)         solid
[    26.460] (II)         copy
[    26.460] (II)         composite (RENDER acceleration)
[    26.460] (II)         put_image
[    26.460] (II)         get_image
[    26.460] (==) intel(0): Backing store disabled
[    26.460] (==) intel(0): Silken mouse enabled
[    26.460] (II) intel(0): Initializing HW Cursor
[    26.520] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    26.520] (==) intel(0): DPMS enabled
[    26.520] (==) intel(0): Intel XvMC decoder enabled
[    26.520] (II) intel(0): Set up textured video
[    26.520] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[    26.520] (II) intel(0): direct rendering: DRI2 Enabled
[    26.520] (==) intel(0): hotplug detection: "enabled"
[    26.520] (--) RandR disabled
[    26.520] (II) Initializing built-in extension Generic Event Extension
[    26.520] (II) Initializing built-in extension SHAPE
[    26.520] (II) Initializing built-in extension MIT-SHM
[    26.520] (II) Initializing built-in extension XInputExtension
[    26.520] (II) Initializing built-in extension XTEST
[    26.520] (II) Initializing built-in extension BIG-REQUESTS
[    26.520] (II) Initializing built-in extension SYNC
[    26.520] (II) Initializing built-in extension XKEYBOARD
[    26.520] (II) Initializing built-in extension XC-MISC
[    26.520] (II) Initializing built-in extension SECURITY
[    26.520] (II) Initializing built-in extension XINERAMA
[    26.520] (II) Initializing built-in extension XFIXES
[    26.520] (II) Initializing built-in extension RENDER
[    26.520] (II) Initializing built-in extension RANDR
[    26.520] (II) Initializing built-in extension COMPOSITE
[    26.520] (II) Initializing built-in extension DAMAGE
[    26.529] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    26.529] (II) AIGLX: enabled GLX_INTEL_swap_event
[    26.529] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    26.529] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    26.529] (II) AIGLX: Loaded and initialized i965
[    26.529] (II) GLX: Initialized DRI2 GL provider for screen 0
[    26.529] (II) intel(0): Setting screen physical size to 361 x 203
[    26.535] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    26.537] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    26.537] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    26.537] (II) LoadModule: "evdev"
[    26.538] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    26.538] (II) Module evdev: vendor="X.Org Foundation"
[    26.538]     compiled for 1.11.3, module version = 2.6.99
[    26.538]     Module class: X.Org XInput Driver
[    26.538]     ABI class: X.Org XInput driver, version 16.0
[    26.538] (II) Using input driver 'evdev' for 'Power Button'
[    26.538] (**) Power Button: always reports core events
[    26.538] (**) evdev: Power Button: Device: "/dev/input/event3"
[    26.538] (--) evdev: Power Button: Vendor 0 Product 0x1
[    26.538] (--) evdev: Power Button: Found keys
[    26.538] (II) evdev: Power Button: Configuring as keyboard
[    26.538] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    26.538] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    26.538] (**) Option "xkb_rules" "evdev"
[    26.538] (**) Option "xkb_model" "pc105"
[    26.538] (**) Option "xkb_layout" "us"
[    26.538] (II) config/udev: Adding input device Video Bus (/dev/input/event6)
[    26.538] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    26.538] (II) Using input driver 'evdev' for 'Video Bus'
[    26.538] (**) Video Bus: always reports core events
[    26.538] (**) evdev: Video Bus: Device: "/dev/input/event6"
[    26.538] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    26.538] (--) evdev: Video Bus: Found keys
[    26.538] (II) evdev: Video Bus: Configuring as keyboard
[    26.538] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input6/event6"
[    26.538] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    26.538] (**) Option "xkb_rules" "evdev"
[    26.538] (**) Option "xkb_model" "pc105"
[    26.538] (**) Option "xkb_layout" "us"
[    26.539] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    26.539] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    26.539] (II) Using input driver 'evdev' for 'Video Bus'
[    26.539] (**) Video Bus: always reports core events
[    26.539] (**) evdev: Video Bus: Device: "/dev/input/event5"
[    26.539] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    26.539] (--) evdev: Video Bus: Found keys
[    26.539] (II) evdev: Video Bus: Configuring as keyboard
[    26.539] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1b/LNXVIDEO:00/input/input5/event5"
[    26.539] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 8)
[    26.539] (**) Option "xkb_rules" "evdev"
[    26.539] (**) Option "xkb_model" "pc105"
[    26.539] (**) Option "xkb_layout" "us"
[    26.539] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    26.539] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    26.539] (II) Using input driver 'evdev' for 'Power Button'
[    26.539] (**) Power Button: always reports core events
[    26.539] (**) evdev: Power Button: Device: "/dev/input/event1"
[    26.539] (--) evdev: Power Button: Vendor 0 Product 0x1
[    26.539] (--) evdev: Power Button: Found keys
[    26.539] (II) evdev: Power Button: Configuring as keyboard
[    26.539] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[    26.539] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 9)
[    26.539] (**) Option "xkb_rules" "evdev"
[    26.539] (**) Option "xkb_model" "pc105"
[    26.539] (**) Option "xkb_layout" "us"
[    26.540] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    26.540] (II) No input driver specified, ignoring this device.
[    26.540] (II) This device may have been added with another device file.
[    26.540] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    26.540] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    26.540] (II) Using input driver 'evdev' for 'Sleep Button'
[    26.540] (**) Sleep Button: always reports core events
[    26.540] (**) evdev: Sleep Button: Device: "/dev/input/event2"
[    26.540] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    26.540] (--) evdev: Sleep Button: Found keys
[    26.540] (II) evdev: Sleep Button: Configuring as keyboard
[    26.540] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2/event2"
[    26.540] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 10)
[    26.540] (**) Option "xkb_rules" "evdev"
[    26.540] (**) Option "xkb_model" "pc105"
[    26.540] (**) Option "xkb_layout" "us"
[    26.541] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=9 (/dev/input/event11)
[    26.541] (II) No input driver specified, ignoring this device.
[    26.541] (II) This device may have been added with another device file.
[    26.541] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event12)
[    26.541] (II) No input driver specified, ignoring this device.
[    26.541] (II) This device may have been added with another device file.
[    26.541] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event13)
[    26.541] (II) No input driver specified, ignoring this device.
[    26.541] (II) This device may have been added with another device file.
[    26.541] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event14)
[    26.541] (II) No input driver specified, ignoring this device.
[    26.541] (II) This device may have been added with another device file.
[    26.541] (II) config/udev: Adding input device Laptop_Integrated_Webcam_HD (/dev/input/event9)
[    26.541] (**) Laptop_Integrated_Webcam_HD: Applying InputClass "evdev keyboard catchall"
[    26.541] (II) Using input driver 'evdev' for 'Laptop_Integrated_Webcam_HD'
[    26.541] (**) Laptop_Integrated_Webcam_HD: always reports core events
[    26.541] (**) evdev: Laptop_Integrated_Webcam_HD: Device: "/dev/input/event9"
[    26.541] (--) evdev: Laptop_Integrated_Webcam_HD: Vendor 0x1bcf Product 0x2880
[    26.541] (--) evdev: Laptop_Integrated_Webcam_HD: Found keys
[    26.541] (II) evdev: Laptop_Integrated_Webcam_HD: Configuring as keyboard
[    26.541] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.0/input/input9/event9"
[    26.541] (II) XINPUT: Adding extended input device "Laptop_Integrated_Webcam_HD" (type: KEYBOARD, id 11)
[    26.541] (**) Option "xkb_rules" "evdev"
[    26.541] (**) Option "xkb_model" "pc105"
[    26.541] (**) Option "xkb_layout" "us"
[    26.542] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event7)
[    26.542] (II) No input driver specified, ignoring this device.
[    26.542] (II) This device may have been added with another device file.
[    26.542] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event8)
[    26.542] (II) No input driver specified, ignoring this device.
[    26.542] (II) This device may have been added with another device file.
[    26.542] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    26.542] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    26.542] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    26.542] (**) AT Translated Set 2 keyboard: always reports core events
[    26.542] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    26.542] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    26.542] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    26.542] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    26.542] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    26.542] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 12)
[    26.542] (**) Option "xkb_rules" "evdev"
[    26.542] (**) Option "xkb_model" "pc105"
[    26.542] (**) Option "xkb_layout" "us"
[    26.543] (II) config/udev: Adding input device PS/2 Elantech Mouse (/dev/input/event15)
[    26.543] (**) PS/2 Elantech Mouse: Applying InputClass "evdev pointer catchall"
[    26.543] (II) Using input driver 'evdev' for 'PS/2 Elantech Mouse'
[    26.543] (**) PS/2 Elantech Mouse: always reports core events
[    26.543] (**) evdev: PS/2 Elantech Mouse: Device: "/dev/input/event15"
[    26.543] (--) evdev: PS/2 Elantech Mouse: Vendor 0x2 Product 0x1
[    26.543] (--) evdev: PS/2 Elantech Mouse: Found 3 mouse buttons
[    26.543] (--) evdev: PS/2 Elantech Mouse: Found relative axes
[    26.543] (--) evdev: PS/2 Elantech Mouse: Found x and y relative axes
[    26.543] (II) evdev: PS/2 Elantech Mouse: Configuring as mouse
[    26.543] (**) evdev: PS/2 Elantech Mouse: YAxisMapping: buttons 4 and 5
[    26.543] (**) evdev: PS/2 Elantech Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    26.543] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input15/event15"
[    26.543] (II) XINPUT: Adding extended input device "PS/2 Elantech Mouse" (type: MOUSE, id 13)
[    26.543] (II) evdev: PS/2 Elantech Mouse: initialized for relative axes.
[    26.543] (**) PS/2 Elantech Mouse: (accel) keeping acceleration scheme 1
[    26.543] (**) PS/2 Elantech Mouse: (accel) acceleration profile 0
[    26.543] (**) PS/2 Elantech Mouse: (accel) acceleration factor: 2.000
[    26.543] (**) PS/2 Elantech Mouse: (accel) acceleration threshold: 4
[    26.543] (II) config/udev: Adding input device PS/2 Elantech Mouse (/dev/input/mouse0)
[    26.543] (II) No input driver specified, ignoring this device.
[    26.543] (II) This device may have been added with another device file.
[    26.545] (II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event10)
[    26.545] (**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    26.545] (II) Using input driver 'evdev' for 'Dell WMI hotkeys'
[    26.545] (**) Dell WMI hotkeys: always reports core events
[    26.545] (**) evdev: Dell WMI hotkeys: Device: "/dev/input/event10"
[    26.545] (--) evdev: Dell WMI hotkeys: Vendor 0 Product 0
[    26.545] (--) evdev: Dell WMI hotkeys: Found keys
[    26.545] (II) evdev: Dell WMI hotkeys: Configuring as keyboard
[    26.545] (**) Option "config_info" "udev:/sys/devices/virtual/input/input10/event10"
[    26.545] (II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD, id 14)
[    26.545] (**) Option "xkb_rules" "evdev"
[    26.545] (**) Option "xkb_model" "pc105"
[    26.545] (**) Option "xkb_layout" "us"
[    27.624] (II) intel(0): EDID vendor "CMO", prod id 5540
[    27.624] (II) intel(0): Printing DDC gathered Modelines:
[    27.624] (II) intel(0): Modeline "1366x768"x0.0   76.80  1366 1392 1448 1580  768 772 785 810 +hsync -vsync (48.6 kHz eP)
[    30.392] (II) intel(0): EDID vendor "CMO", prod id 5540
[    30.392] (II) intel(0): Printing DDC gathered Modelines:
[    30.392] (II) intel(0): Modeline "1366x768"x0.0   76.80  1366 1392 1448 1580  768 772 785 810 +hsync -vsync (48.6 kHz eP)
[    35.729] (II) intel(0): EDID vendor "CMO", prod id 5540
[    35.729] (II) intel(0): Printing DDC gathered Modelines:
[    35.729] (II) intel(0): Modeline "1366x768"x0.0   76.80  1366 1392 1448 1580  768 772 785 810 +hsync -vsync (48.6 kHz eP)
[    35.846] (II) intel(0): EDID vendor "CMO", prod id 5540
[    35.846] (II) intel(0): Printing DDC gathered Modelines:
[    35.846] (II) intel(0): Modeline "1366x768"x0.0   76.80  1366 1392 1448 1580  768 772 785 810 +hsync -vsync (48.6 kHz eP)
[    36.125] (II) intel(0): EDID vendor "CMO", prod id 5540
[    36.125] (II) intel(0): Printing DDC gathered Modelines:
[    36.125] (II) intel(0): Modeline "1366x768"x0.0   76.80  1366 1392 1448 1580  768 772 785 810 +hsync -vsync (48.6 kHz eP)
[    37.042] (II) XKB: reuse xkmfile /var/lib/xkb/server-03AF3717FF3AB439A4BAABA686CCB40771CDF520.xkm
[    56.157] (II) intel(0): EDID vendor "CMO", prod id 5540
[    56.157] (II) intel(0): Printing DDC gathered Modelines:
[    56.157] (II) intel(0): Modeline "1366x768"x0.0   76.80  1366 1392 1448 1580  768 772 785 810 +hsync -vsync (48.6 kHz eP)
```This is kinda annoying problem , single tap and double tap works , also i have X11-synaptics input drivers also installed, what could be possibly wrong with this?

---

### Post by ahsan101 on 2012-02-28
Many guys out there say Arch Linux seems to solve this problem so i am giving it a try and will post back any good news i will have by than :)

---

### Post by webhasan on 2012-03-17
Did you solve it? I have the same issue.

---

### Post by miz0ooo0 on 2012-04-22
hey there i had the same problem with ubuntu 11,10 64bit (AMD),but i upgraded to ubuntu 12.04 32bit (intel) ,i finally find options for touchpad you can enable or disable 2 fingers scrolling 
concerning this dell i think that the more compatible version is 32 bit  (intel)

---

### Post by DubelBoom on 2012-04-23
I know how to make it recognize your Touchpad as Alps GlidePoint, but then software's as Synaptiks allow only 1 finger. And on settings - Mouse and Touchpad - Touchpad scroll with 2 fingers doesn't work.
I'm still searching for a way to fix this, maybe ubuntu 12.04 will be better at this point.
The fix for now:
1. Download and install this: [http://dl.dropbox.com/u/22680754/psmouse-alps-dkms_0.10_all.deb](http://dl.dropbox.com/u/22680754/psmouse-alps-dkms_0.10_all.deb)
2. open terminal and write:[FONT=monospace]
[/FONT]cd /usr/src/psmouse-alps-0.10/src[FONT=monospace]
[/FONT]3. Now write:[FONT=monospace]
[/FONT]sudo gedit alps.c[FONT=monospace]
[/FONT]4. At the file look for the  [FONT=monospace][/FONT]/* Dell Vostro 1400 */ line, and above it you'll see 0x73 , 0x02 , 0x50, replace the 0x02 with 0x03 and save.
5. At the terminal, make sure your still at "/usr/src/psmouse-alps-0.10/src[FONT=monospace]" and write:
[/FONT]sudo dkms add -m psmouse -v alps-0.10
6. Write:[FONT=monospace]
[/FONT]sudo dkms build -m psmouse -v alps-0.10[FONT=monospace]
[/FONT]7. Write:[FONT=monospace]
[/FONT]sudo dkms install -m psmouse -v alps-0.10

Now reboot, open the terminal again and write "xinput list", you'll see "Alps/PS2 Alps GlidePoint".

ENJOY :D

---

