---
title: "D800/4200 Go Docked display problems."
date: 2006-08-17
forum: Hardware &amp; Laptops
---

### Post by hangfire on 2006-08-17
Hi,

I've been enjoying Ubuntu 6.06 for the past month on my Dell D800. It was amazing, after several previous distro's failing to recognize the onboard sound, to have the INSTALLER play music for me. The last remaining problem...

My Dell D800/nVidia 4200Go 64MB won't display on the Viewsonic VP201b's DVI when docked on the D/Dock.

I've edited the xorg.conf to add the native 1280x800 WXGA resolution of the laptop screen itself. FN-Ctrl-Alt +/- works OK undocked on both screens (obviously the built-in screen doesn't do 1600x1200 native). 

This is only a problem with the nvidia driver. If I switch to "nv" in xorg.conf, it uses the Viewsonic while docked just fine.

Most things work OK when undocked including running the Viewsonic off of the back of the laptop with the DSUB connector. While undocked, however, FN-F8 (CRT/LCD) will not switch away from the Viewsonic on DSUB, even if I prep it by going to 1280x800. It will only cause it to flicker a moment.

I've browsed ubuntuforums and some other D800 sites. Following advice found here and there, I've uninstalled powernowd and replaced it with cpufreqd. This has improved performance across the board, even when running nv instead of nvidia. 

I set POST_VIDEO to false in /etc/default/acpi-support
I set ENABLE_LAPTOP_MODE=true in /etc/default/acpi-support
I added vga=788 after splash /etc/grub/menu.lst

Thanks in advance.

My xorg.conf:

```

Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
EndSection
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "NVIDIA Corporation NV28 [GeForce4 Ti 4200 Go AGP 8x]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection
Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV28 [GeForce4 Ti 4200 Go AGP 8x]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1600x1200" "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1600x1200" "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1600x1200" "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1600x1200" "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1600x1200" "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1600x1200" "1280x800"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection


```

Most of my Xorg.0.log:

```

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux irad-lt 2.6.15-26-686 #1 SMP PREEMPT Thu Aug 3 0
3:13:28 UTC 2006 i686
Build Date: 16 March 2006
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Aug 17 14:24:37 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "NVIDIA Corporation NV28 [GeForce4 Ti 4200 Go AGP 8x]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(**) |-->Input Device "Synaptics Touchpad"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
        Entry deleted from font path.
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:uns
caled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share
/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/
dirs/TrueType"
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Module ABI versions:
        X.Org ANSI C Emulation: 0.2
        X.Org Video Driver: 0.8
        X.Org XInput driver : 0.5
        X.Org Server Extension : 0.2
        X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        Module class: X.Org Font Renderer
        ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 0.8
(++) using VT number 7
(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,3340 card 0000,0000 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,3341 card 0000,0000 rev 03 class 06,04,00 hdr 01
(II) PCI: 00:1d:0: chip 8086,24c2 card 8086,4541 rev 01 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24c4 card 8086,4541 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,24c7 card 8086,4541 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24cd card 1028,014e rev 01 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev 81 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24cc card 0000,0000 rev 01 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24ca card 8086,4541 rev 01 class 01,01,8a hdr 00
(II) PCI: 00:1f:5: chip 8086,24c5 card 1028,014e rev 01 class 04,01,00 hdr 00
(II) PCI: 00:1f:6: chip 8086,24c6 card 14f1,5422 rev 01 class 07,03,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0286 card 1028,0179 rev a1 class 03,00,00 hdr 00
(II) PCI: 02:00:0: chip 14e4,165d card 1028,865d rev 01 class 02,00,00 hdr 00
(II) PCI: 02:01:0: chip 104c,ac47 card d000,0000 rev 01 class 06,07,00 hdr 82
(II) PCI: 02:01:1: chip 104c,ac4a card d800,0000 rev 01 class 06,07,00 hdr 82
(II) PCI: 02:01:2: chip 104c,802b card 1028,014e rev 00 class 0c,00,10 hdr 80
(II) PCI: 02:01:3: chip 104c,8204 card 1028,014e rev 00 class 08,80,00 hdr 80
(II) PCI: 02:03:0: chip 14e4,4324 card 1028,0001 rev 02 class 02,80,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,7), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
        [0] -1  0       0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:

(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg/modules/linux/libdrm.so
(II) Module drm: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.2
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 0.2
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation

(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
        compiled for 7.0.0, module version = 2.1.0
        Module class: X.Org Font Renderer
        ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
        compiled for 4.0.2, module version = 1.0.8762
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.2
        Module class: X.Org Font Renderer
        ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.1.0
        ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.o
(II) Module nvidia: vendor="NVIDIA Corporation"
        compiled for 4.0.2, module version = 1.0.8762
        Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.1
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.3
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
        compiled for 4.3.99.902, module version = 1.0.0
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.5
(II) Wacom driver level: 47-0.7.2 $
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
        compiled for 4.3.99.902, module version = 1.0.0
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.5
(II) NVIDIA X Driver  1.0-8762  Mon May 15 13:09:21 PDT 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 0.1.0
        ABI class: X.Org Video Driver, version 0.8
(II) resource ranges after xf86ClaimFixedResources() call:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xfafec000 - 0xfafedfff (0x2000) MX[B]
        [5] -1  0       0xfafe8000 - 0xfafebfff (0x4000) MX[B]
        [6] -1  0       0xfafef800 - 0xfafeffff (0x800) MX[B]
        [7] -1  0       0xfaff0000 - 0xfaffffff (0x10000) MX[B]
        [8] -1  0       0xf4fff400 - 0xf4fff4ff (0x100) MX[B]
        [9] -1  0       0xf4fff800 - 0xf4fff9ff (0x200) MX[B]
        [10] -1 0       0x74000000 - 0x740003ff (0x400) MX[B]
        [11] -1 0       0xf4fffc00 - 0xf4ffffff (0x400) MX[B]
        [12] -1 0       0xe8000000 - 0xe7ffffff (0x0) MX[B]O
        [13] -1 0       0xfd000000 - 0xfd01ffff (0x20000) MX[B](B)
        [14] -1 0       0xf0000000 - 0xf3ffffff (0x4000000) MX[B](B)
        [15] -1 0       0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
        [16] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [17] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [18] -1 0       0x0000ecf8 - 0x0000ecff (0x8) IX[B]
        [19] -1 0       0x0000b080 - 0x0000b0ff (0x80) IX[B]
        [20] -1 0       0x0000b400 - 0x0000b4ff (0x100) IX[B]
        [21] -1 0       0x0000bc40 - 0x0000bc7f (0x40) IX[B]
        [22] -1 0       0x0000b800 - 0x0000b8ff (0x100) IX[B]
        [23] -1 0       0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
        [24] -1 0       0x00000374 - 0x00000374 (0x1) IX[B]
        [25] -1 0       0x00000170 - 0x00000170 (0x1) IX[B]
        [26] -1 0       0x000003f4 - 0x000003f4 (0x1) IX[B]
        [27] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[B]
        [28] -1 0       0x0000bf20 - 0x0000bf3f (0x20) IX[B]
        [29] -1 0       0x0000bf40 - 0x0000bf5f (0x20) IX[B]
        [30] -1 0       0x0000bf80 - 0x0000bf9f (0x20) IX[B]
(II) resource ranges after probing:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xfafec000 - 0xfafedfff (0x2000) MX[B]
        [5] -1  0       0xfafe8000 - 0xfafebfff (0x4000) MX[B]
        [6] -1  0       0xfafef800 - 0xfafeffff (0x800) MX[B]
        [7] -1  0       0xfaff0000 - 0xfaffffff (0x10000) MX[B]
        [8] -1  0       0xf4fff400 - 0xf4fff4ff (0x100) MX[B]
        [9] -1  0       0xf4fff800 - 0xf4fff9ff (0x200) MX[B]
        [10] -1 0       0x74000000 - 0x740003ff (0x400) MX[B]
        [11] -1 0       0xf4fffc00 - 0xf4ffffff (0x400) MX[B]
        [12] -1 0       0xe8000000 - 0xe7ffffff (0x0) MX[B]O
        [13] -1 0       0xfd000000 - 0xfd01ffff (0x20000) MX[B](B)
        [14] -1 0       0xf0000000 - 0xf3ffffff (0x4000000) MX[B](B)
        [15] -1 0       0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
        [16] 0  0       0x000a0000 - 0x000affff (0x10000) MS[B]
        [17] 0  0       0x000b0000 - 0x000b7fff (0x8000) MS[B]
        [18] 0  0       0x000b8000 - 0x000bffff (0x8000) MS[B]
        [19] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [20] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [21] -1 0       0x0000ecf8 - 0x0000ecff (0x8) IX[B]
        [22] -1 0       0x0000b080 - 0x0000b0ff (0x80) IX[B]
        [23] -1 0       0x0000b400 - 0x0000b4ff (0x100) IX[B]
        [24] -1 0       0x0000bc40 - 0x0000bc7f (0x40) IX[B]
        [25] -1 0       0x0000b800 - 0x0000b8ff (0x100) IX[B]
        [26] -1 0       0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
        [27] -1 0       0x00000374 - 0x00000374 (0x1) IX[B]
        [28] -1 0       0x00000170 - 0x00000170 (0x1) IX[B]
        [29] -1 0       0x000003f4 - 0x000003f4 (0x1) IX[B]
        [30] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[B]
        [31] -1 0       0x0000bf20 - 0x0000bf3f (0x20) IX[B]
        [32] -1 0       0x0000bf40 - 0x0000bf5f (0x20) IX[B]
        [33] -1 0       0x0000bf80 - 0x0000bf9f (0x20) IX[B]
        [34] 0  0       0x000003b0 - 0x000003bb (0xc) IS[B]
        [35] 0  0       0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): NVIDIA GPU GeForce4 4200 Go at PCI:1:0:0
(--) NVIDIA(0): VideoRAM: 65536 kBytes
(--) NVIDIA(0): VideoBIOS: 04.28.20.31.c1
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce4 4200 Go at PCI:1:0:0:
(--) NVIDIA(0):     ViewSonic VP201b (CRT-0)
(--) NVIDIA(0):     Seiko (DFP-0)
(--) NVIDIA(0): ViewSonic VP201b (CRT-0): 350.0 MHz maximum pixel clock
(--) NVIDIA(0): Seiko (DFP-0): 165.0 MHz maximum pixel clock
(--) NVIDIA(0): Seiko (DFP-0): External Dual Link LVDS
(II) NVIDIA(0): Assigned Display Device: CRT-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1600x1200"
(II) NVIDIA(0):     "1280x800"
(II) NVIDIA(0): Virtual screen size determined to be 1600 x 1200
(--) NVIDIA(0): DPI set to (99, 98); computed from "UseEdidDpi" X config option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
        [0] 0   0       0xf0000000 - 0xf3ffffff (0x4000000) MX[B]
        [1] 0   0       0xfc000000 - 0xfcffffff (0x1000000) MX[B]
        [2] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [3] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [4] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [5] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [6] -1  0       0xfafec000 - 0xfafedfff (0x2000) MX[B]
        [7] -1  0       0xfafe8000 - 0xfafebfff (0x4000) MX[B]
        [8] -1  0       0xfafef800 - 0xfafeffff (0x800) MX[B]
        [9] -1  0       0xfaff0000 - 0xfaffffff (0x10000) MX[B]
        [10] -1 0       0xf4fff400 - 0xf4fff4ff (0x100) MX[B]
        [11] -1 0       0xf4fff800 - 0xf4fff9ff (0x200) MX[B]
        [12] -1 0       0x74000000 - 0x740003ff (0x400) MX[B]
        [13] -1 0       0xf4fffc00 - 0xf4ffffff (0x400) MX[B]
        [14] -1 0       0xe8000000 - 0xe7ffffff (0x0) MX[B]O
        [15] -1 0       0xfd000000 - 0xfd01ffff (0x20000) MX[B](B)
        [16] -1 0       0xf0000000 - 0xf3ffffff (0x4000000) MX[B](B)
        [17] -1 0       0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
        [18] 0  0       0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
        [19] 0  0       0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
        [20] 0  0       0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
        [21] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [22] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [23] -1 0       0x0000ecf8 - 0x0000ecff (0x8) IX[B]
        [24] -1 0       0x0000b080 - 0x0000b0ff (0x80) IX[B]
        [25] -1 0       0x0000b400 - 0x0000b4ff (0x100) IX[B]
        [26] -1 0       0x0000bc40 - 0x0000bc7f (0x40) IX[B]
        [27] -1 0       0x0000b800 - 0x0000b8ff (0x100) IX[B]
        [28] -1 0       0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
        [29] -1 0       0x00000374 - 0x00000374 (0x1) IX[B]
        [30] -1 0       0x00000170 - 0x00000170 (0x1) IX[B]
        [31] -1 0       0x000003f4 - 0x000003f4 (0x1) IX[B]
        [32] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[B]
        [33] -1 0       0x0000bf20 - 0x0000bf3f (0x20) IX[B]
        [34] -1 0       0x0000bf40 - 0x0000bf5f (0x20) IX[B]
        [35] -1 0       0x0000bf80 - 0x0000bf9f (0x20) IX[B]
        [36] 0  0       0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
        [37] 0  0       0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "1600x1200"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
error opening security policy file /etc/X11/xserver/SecurityPolicy
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) Synaptics touchpad driver version 0.14.3
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event2
(**) Option "Device" "/dev/input/event2"
(**) Option "HorizScrollDelta" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Invalid argument
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Invalid argument
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Invalid argument
Synaptics DeviceInit called
SynapticsCtrl called.
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Synaptics DeviceOn called
(--) Synaptics Touchpad touchpad found
(II) NVIDIA(0): Setting mode "1280x800"
(II) NVIDIA(0): Setting mode "1600x1200"
(II) NVIDIA(0): Setting mode "1280x800"

```

---

### Post by hangfire on 2006-08-21
Bump.

---

### Post by hangfire on 2006-08-21
To make the problem crystal clear:

1. When running "nv", the docked system displays OK on an external 1600x1200 monitor mounted on the D/Dock DVI.

2. When running "nvidia", the system display OK through bootup and Linux startup until it should display the nVidia splash screen, then it goes dark.

HF

---

### Post by hangfire on 2006-09-08
Bump.

---

