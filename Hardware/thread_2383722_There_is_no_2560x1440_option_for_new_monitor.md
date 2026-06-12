---
title: "There is no 2560x1440 option for new monitor"
date: 2018-01-29
forum: Hardware
---

### Post by olegorov on 2018-01-29
Laptop MSI GL62 6QF with Intel Graphics 530 and NVidia GTX960M.
New monitor Samsung C27H711QEI with native resolusion 2560x1440 at 60Hz and HDMI cable.
Windows 10 works with this monitor as expected. But Ubuntu 17.10 shows only FullHD resolution at 60Hz.
With cvt and xrandr I can setup 2560x1440@58Hz (hsync: 86.41 kHz; pclk: 300.00 MHz). This configuration works fine.
But I still don't know:
1. Why I cannot use 60Hz and
2. Where and how to save these settings? (gdm3, xorg.conf, ~/.xprofile ?)

---

### Post by olegorov on 2018-01-29
Xorg.0.log:

```
[    31.169] (--) Log file renamed from "/var/log/Xorg.pid-948.log" to "/var/log/Xorg.0.log"[    31.170] 
X.Org X Server 1.19.5
Release Date: 2017-10-12
[    31.171] X Protocol Version 11, Revision 0
[    31.171] Build Operating System: Linux 4.4.0-97-generic x86_64 Ubuntu
[    31.171] Current Operating System: Linux olegorov-GL62-6QF 4.13.0-32-generic #35-Ubuntu SMP Thu Jan 25 09:13:46 UTC 2018 x86_64
[    31.171] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.13.0-32-generic root=UUID=09ff5372-c682-46f9-84a4-23061a6df7d1 ro quiet splash vt.handoff=7
[    31.171] Build Date: 15 October 2017  05:51:19PM
[    31.171] xorg-server 2:1.19.5-0ubuntu2 (For technical support please see http://www.ubuntu.com/support) 
[    31.171] Current version of pixman: 0.34.0
[    31.171]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    31.171] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    31.171] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Jan 29 08:27:21 2018
[    31.205] (==) Using config file: "/etc/X11/xorg.conf"
[    31.205] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    31.249] (==) ServerLayout "layout"
[    31.249] (**) |-->Screen "nvidia" (0)
[    31.249] (**) |   |-->Monitor "<default monitor>"
[    31.262] (**) |   |-->Device "nvidia"
[    31.262] (**) |   |-->GPUDevice "nvidia"
[    31.262] (==) No monitor specified for screen "nvidia".
    Using a default monitor configuration.
[    31.262] (**) |-->Inactive Device "intel"
[    31.262] (==) Automatically adding devices
[    31.262] (==) Automatically enabling devices
[    31.262] (==) Automatically adding GPU devices
[    31.262] (==) Automatically binding GPU devices
[    31.262] (==) Max clients allowed: 256, resource mask: 0x1fffff
[    31.262] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    31.262]     Entry deleted from font path.
[    31.262] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    31.262]     Entry deleted from font path.
[    31.262] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    31.262]     Entry deleted from font path.
[    31.263] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    31.263]     Entry deleted from font path.
[    31.263] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    31.263]     Entry deleted from font path.
[    31.263] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    31.263] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    31.263] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    31.267] (II) Loader magic: 0x55ece84b5020
[    31.267] (II) Module ABI versions:
[    31.267]     X.Org ANSI C Emulation: 0.4
[    31.267]     X.Org Video Driver: 23.0
[    31.267]     X.Org XInput driver : 24.1
[    31.267]     X.Org Server Extension : 10.0
[    31.269] (++) using VT number 1


[    31.273] (II) systemd-logind: took control of session /org/freedesktop/login1/session/_31
[    31.275] (II) xfree86: Adding drm device (/dev/dri/card0)
[    31.277] (II) systemd-logind: got fd for /dev/dri/card0 226:0 fd 12 paused 0
[    31.277] (II) xfree86: Adding drm device (/dev/dri/card1)
[    31.279] (II) systemd-logind: got fd for /dev/dri/card1 226:1 fd 13 paused 0
[    31.282] (--) PCI:*(0:0:2:0) 8086:191b:1462:115a rev 6, Mem @ 0xdd000000/16777216, 0xb0000000/268435456, I/O @ 0x0000f000/64, BIOS @ 0x????????/131072
[    31.282] (--) PCI: (0:1:0:0) 10de:139b:1462:115a rev 162, Mem @ 0xde000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[    31.282] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    31.282] (II) "glx" will be loaded by default.
[    31.282] (II) LoadModule: "glx"
[    31.325] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    33.502] (II) Module glx: vendor="NVIDIA Corporation"
[    33.502]     compiled for 4.0.2, module version = 1.0.0
[    33.502]     Module class: X.Org Server Extension
[    33.520] (II) NVIDIA GLX Module  384.111  Tue Dec 19 22:51:13 PST 2017
[    33.542] (II) LoadModule: "nvidia"
[    33.543] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    33.853] (II) Module nvidia: vendor="NVIDIA Corporation"
[    33.854]     compiled for 4.0.2, module version = 1.0.0
[    33.854]     Module class: X.Org Video Driver
[    33.880] (II) LoadModule: "modesetting"
[    33.898] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    33.915] (II) Module modesetting: vendor="X.Org Foundation"
[    33.915]     compiled for 1.19.5, module version = 1.19.5
[    33.916]     Module class: X.Org Video Driver
[    33.916]     ABI class: X.Org Video Driver, version 23.0
[    33.916] (II) NVIDIA dlloader X Driver  384.111  Tue Dec 19 22:25:34 PST 2017
[    33.916] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    33.937] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    33.937] (II) systemd-logind: releasing fd for 226:0
[    33.955] (II) Loading sub module "fb"
[    33.955] (II) LoadModule: "fb"
[    33.955] (II) Loading /usr/lib/xorg/modules/libfb.so
[    33.974] (II) Module fb: vendor="X.Org Foundation"
[    33.974]     compiled for 1.19.5, module version = 1.0.0
[    33.974]     ABI class: X.Org ANSI C Emulation, version 0.4
[    33.974] (II) Loading sub module "wfb"
[    33.974] (II) LoadModule: "wfb"
[    33.974] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    33.984] (II) Module wfb: vendor="X.Org Foundation"
[    33.984]     compiled for 1.19.5, module version = 1.0.0
[    33.985]     ABI class: X.Org ANSI C Emulation, version 0.4
[    33.985] (II) Loading sub module "ramdac"
[    33.985] (II) LoadModule: "ramdac"
[    33.985] (II) Module "ramdac" already built-in
[    34.057] (II) modeset(G0): using drv /dev/dri/card1
[    34.057] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "nvidia" for depth/fbbpp 24/32
[    34.057] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    34.057] (==) NVIDIA(0): RGB weight 888
[    34.057] (==) NVIDIA(0): Default visual is TrueColor
[    34.057] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    34.102] (**) NVIDIA(0): Option "ConstrainCursor" "off"
[    34.102] (**) NVIDIA(0): Option "AllowEmptyInitialConfiguration" "on"
[    34.102] (**) NVIDIA(0): Option "IgnoreDisplayDevices" "CRT"
[    34.102] (**) NVIDIA(0): Enabling 2D acceleration
[    34.513] (II) NVIDIA(0): NVIDIA GPU GeForce GTX 960M (GM107-A) at PCI:1:0:0 (GPU-0)
[    34.513] (--) NVIDIA(0): Memory: 2097152 kBytes
[    34.513] (--) NVIDIA(0): VideoBIOS: 82.07.94.00.1c
[    34.513] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    34.513] (II) NVIDIA(0): Validated MetaModes:
[    34.513] (II) NVIDIA(0):     "NULL"
[    34.513] (II) NVIDIA(0): Virtual screen size determined to be 640 x 480
[    34.513] (WW) NVIDIA(0): Unable to get display device for DPI computation.
[    34.513] (==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
[    34.513] (==) modeset(G0): Depth 24, (==) framebuffer bpp 32
[    34.513] (**) modeset(G0): Option "AccelMethod" "None"
[    34.513] (==) modeset(G0): RGB weight 888
[    34.513] (==) modeset(G0): Default visual is TrueColor
[    34.513] (**) modeset(G0): glamor disabled
[    34.513] (II) modeset(G0): ShadowFB: preferred YES, enabled YES
[    34.513] (II) modeset(G0): Double-buffered shadow updates: off
[    34.515] (II) modeset(G0): Output eDP-1-1 has no monitor section
[    34.515] (II) modeset(G0): Output DP-1-1 has no monitor section
[    34.524] (II) modeset(G0): Output HDMI-1-1 has no monitor section
[    34.602] (II) modeset(G0): Output HDMI-1-2 has no monitor section
[    34.604] (II) modeset(G0): EDID for output eDP-1-1
[    34.604] (II) modeset(G0): Manufacturer: CMN  Model: 15d2  Serial#: 0
[    34.604] (II) modeset(G0): Year: 2015  Week: 18
[    34.604] (II) modeset(G0): EDID Version: 1.4
[    34.604] (II) modeset(G0): Digital Display Input
[    34.604] (II) modeset(G0): 6 bits per channel
[    34.604] (II) modeset(G0): Digital interface is DisplayPort
[    34.604] (II) modeset(G0): Max Image Size [cm]: horiz.: 34  vert.: 19
[    34.604] (II) modeset(G0): Gamma: 2.20
[    34.604] (II) modeset(G0): No DPMS capabilities specified
[    34.604] (II) modeset(G0): Supported color encodings: RGB 4:4:4 
[    34.604] (II) modeset(G0): First detailed timing is preferred mode
[    34.604] (II) modeset(G0): Preferred mode is native pixel format and refresh rate
[    34.604] (II) modeset(G0): redX: 0.673 redY: 0.309   greenX: 0.266 greenY: 0.674
[    34.604] (II) modeset(G0): blueX: 0.156 blueY: 0.047   whiteX: 0.313 whiteY: 0.329
[    34.604] (II) modeset(G0): Manufacturer's mask: 0
[    34.604] (II) modeset(G0): Supported detailed timing:
[    34.604] (II) modeset(G0): clock: 152.8 MHz   Image Size:  344 x 193 mm
[    34.604] (II) modeset(G0): h_active: 1920  h_sync: 2020  h_sync_end 2086 h_blank_end 2250 h_border: 0
[    34.604] (II) modeset(G0): v_active: 1080  v_sync: 1086  v_sync_end 1096 v_blanking: 1132 v_border: 0
[    34.604] (II) modeset(G0):  N156HGE-EAL
[    34.604] (II) modeset(G0):  CMN
[    34.604] (II) modeset(G0):  N156HGE-EAL
[    34.604] (II) modeset(G0): EDID (in hex):
[    34.604] (II) modeset(G0):     00ffffffffffff000daed21500000000
[    34.604] (II) modeset(G0):     1219010495221378024205ac4f44ac28
[    34.604] (II) modeset(G0):     0c505400000001010101010101010101
[    34.604] (II) modeset(G0):     010101010101b43b804a713834406442
[    34.604] (II) modeset(G0):     6a0058c110000018000000fe004e3135
[    34.604] (II) modeset(G0):     364847452d45414c0a20000000fe0043
[    34.604] (II) modeset(G0):     4d4e0a202020202020202020000000fe
[    34.604] (II) modeset(G0):     004e3135364847452d45414c0a2000df
[    34.605] (II) modeset(G0): Printing probed modes for output eDP-1-1
[    34.605] (II) modeset(G0): Modeline "1920x1080"x60.0  152.84  1920 2020 2086 2250  1080 1086 1096 1132 -hsync -vsync (67.9 kHz eP)
[    34.605] (II) modeset(G0): Modeline "1920x1080"x59.9  138.50  1920 1968 2000 2080  1080 1083 1088 1111 +hsync -vsync (66.6 kHz d)
[    34.605] (II) modeset(G0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz d)
[    34.605] (II) modeset(G0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz d)
[    34.605] (II) modeset(G0): Modeline "1600x1024"x60.2  103.12  1600 1600 1656 1664  1024 1024 1029 1030 +hsync +vsync (62.0 kHz d)
[    34.605] (II) modeset(G0): Modeline "1400x1050"x60.0  122.00  1400 1488 1640 1880  1050 1052 1064 1082 +hsync +vsync (64.9 kHz d)
[    34.605] (II) modeset(G0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz d)
[    34.605] (II) modeset(G0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz d)
[    34.605] (II) modeset(G0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz d)
[    34.605] (II) modeset(G0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz d)
[    34.605] (II) modeset(G0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz d)
[    34.605] (II) modeset(G0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz d)
[    34.605] (II) modeset(G0): Modeline "1024x768"x120.1  133.47  1024 1100 1212 1400  768 768 770 794 doublescan -hsync +vsync (95.3 kHz d)
[    34.605] (II) modeset(G0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz d)
[    34.605] (II) modeset(G0): Modeline "960x720"x120.0  117.00  960 1024 1128 1300  720 720 722 750 doublescan -hsync +vsync (90.0 kHz d)
[    34.605] (II) modeset(G0): Modeline "928x696"x120.1  109.15  928 976 1088 1264  696 696 698 719 doublescan -hsync +vsync (86.4 kHz d)
[    34.605] (II) modeset(G0): Modeline "896x672"x120.0  102.40  896 960 1060 1224  672 672 674 697 doublescan -hsync +vsync (83.7 kHz d)
[    34.605] (II) modeset(G0): Modeline "960x600"x120.0   77.00  960 984 1000 1040  600 601 604 617 doublescan +hsync -vsync (74.0 kHz d)
[    34.605] (II) modeset(G0): Modeline "960x540"x120.0   69.25  960 984 1000 1040  540 541 544 555 doublescan +hsync -vsync (66.6 kHz d)
[    34.605] (II) modeset(G0): Modeline "800x600"x120.0   81.00  800 832 928 1080  600 600 602 625 doublescan +hsync +vsync (75.0 kHz d)
[    34.605] (II) modeset(G0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz d)
[    34.605] (II) modeset(G0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz d)
[    34.605] (II) modeset(G0): Modeline "840x525"x120.0   73.12  840 892 980 1120  525 526 529 544 doublescan -hsync +vsync (65.3 kHz d)
[    34.605] (II) modeset(G0): Modeline "840x525"x119.8   59.50  840 864 880 920  525 526 529 540 doublescan +hsync -vsync (64.7 kHz d)
[    34.605] (II) modeset(G0): Modeline "800x512"x120.3   51.56  800 800 828 832  512 512 514 515 doublescan +hsync +vsync (62.0 kHz d)
[    34.605] (II) modeset(G0): Modeline "700x525"x120.0   61.00  700 744 820 940  525 526 532 541 doublescan +hsync +vsync (64.9 kHz d)
[    34.605] (II) modeset(G0): Modeline "640x512"x120.0   54.00  640 664 720 844  512 512 514 533 doublescan +hsync +vsync (64.0 kHz d)
[    34.605] (II) modeset(G0): Modeline "720x450"x119.8   53.25  720 760 836 952  450 451 454 467 doublescan -hsync +vsync (55.9 kHz d)
[    34.605] (II) modeset(G0): Modeline "640x480"x120.0   54.00  640 688 744 900  480 480 482 500 doublescan +hsync +vsync (60.0 kHz d)
[    34.605] (II) modeset(G0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz d)
[    34.605] (II) modeset(G0): Modeline "680x384"x119.6   42.38  680 716 784 888  384 385 390 399 doublescan -hsync +vsync (47.7 kHz d)
[    34.605] (II) modeset(G0): Modeline "680x384"x119.9   36.00  680 704 720 760  384 385 390 395 doublescan +hsync -vsync (47.4 kHz d)
[    34.605] (II) modeset(G0): Modeline "576x432"x120.1   40.81  576 608 668 760  432 432 434 447 doublescan -hsync +vsync (53.7 kHz d)
[    34.605] (II) modeset(G0): Modeline "512x384"x120.0   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync (48.4 kHz d)
[    34.605] (II) modeset(G0): Modeline "400x300"x120.6   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz d)
[    34.606] (II) modeset(G0): Modeline "400x300"x112.7   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (35.2 kHz d)
[    34.606] (II) modeset(G0): Modeline "320x240"x120.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz d)
[    34.606] (II) modeset(G0): EDID for output DP-1-1
[    34.614] (II) modeset(G0): EDID for output HDMI-1-1
[    34.697] (II) modeset(G0): EDID for output HDMI-1-2
[    34.697] (II) modeset(G0): Manufacturer: SAM  Model: dd3  Serial#: 810635607
[    34.697] (II) modeset(G0): Year: 2017  Week: 35
[    34.697] (II) modeset(G0): EDID Version: 1.3
[    34.697] (II) modeset(G0): Digital Display Input
[    34.697] (II) modeset(G0): Max Image Size [cm]: horiz.: 60  vert.: 34
[    34.697] (II) modeset(G0): Gamma: 2.20
[    34.697] (II) modeset(G0): DPMS capabilities: Off
[    34.697] (II) modeset(G0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    34.697] (II) modeset(G0): First detailed timing is preferred mode
[    34.697] (II) modeset(G0): redX: 0.662 redY: 0.328   greenX: 0.275 greenY: 0.593
[    34.697] (II) modeset(G0): blueX: 0.135 blueY: 0.124   whiteX: 0.298 whiteY: 0.363
[    34.697] (II) modeset(G0): Supported established timings:
[    34.697] (II) modeset(G0): 720x400@70Hz
[    34.697] (II) modeset(G0): 640x480@60Hz
[    34.697] (II) modeset(G0): 640x480@67Hz
[    34.697] (II) modeset(G0): 640x480@72Hz
[    34.697] (II) modeset(G0): 640x480@75Hz
[    34.697] (II) modeset(G0): 800x600@56Hz
[    34.697] (II) modeset(G0): 800x600@60Hz
[    34.697] (II) modeset(G0): 800x600@72Hz
[    34.697] (II) modeset(G0): 800x600@75Hz
[    34.697] (II) modeset(G0): 832x624@75Hz
[    34.697] (II) modeset(G0): 1024x768@60Hz
[    34.697] (II) modeset(G0): 1024x768@70Hz
[    34.697] (II) modeset(G0): 1024x768@75Hz
[    34.697] (II) modeset(G0): 1280x1024@75Hz
[    34.697] (II) modeset(G0): 1152x864@75Hz
[    34.697] (II) modeset(G0): Manufacturer's mask: 0
[    34.697] (II) modeset(G0): Supported standard timings:
[    34.697] (II) modeset(G0): #0: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[    34.697] (II) modeset(G0): #1: hsize: 1280  vsize 800  refresh: 60  vid: 129
[    34.697] (II) modeset(G0): #2: hsize: 1280  vsize 720  refresh: 60  vid: 49281
[    34.697] (II) modeset(G0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    34.698] (II) modeset(G0): #4: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    34.698] (II) modeset(G0): #5: hsize: 1600  vsize 900  refresh: 60  vid: 49321
[    34.698] (II) modeset(G0): #6: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    34.698] (II) modeset(G0): Supported detailed timing:
[    34.698] (II) modeset(G0): clock: 241.5 MHz   Image Size:  597 x 336 mm
[    34.698] (II) modeset(G0): h_active: 2560  h_sync: 2608  h_sync_end 2640 h_blank_end 2720 h_border: 0
[    34.698] (II) modeset(G0): v_active: 1440  v_sync: 1443  v_sync_end 1448 v_blanking: 1481 v_border: 0
[    34.698] (II) modeset(G0): Ranges: V min: 50 V max: 75 Hz, H min: 27 H max: 89 kHz, PixClock max 255 MHz
[    34.698] (II) modeset(G0): Monitor name: C27H71x
[    34.698] (II) modeset(G0): Serial No: HTHJ800121
[    34.698] (II) modeset(G0): Supported detailed timing:
[    34.698] (II) modeset(G0): clock: 148.5 MHz   Image Size:  597 x 336 mm
[    34.698] (II) modeset(G0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    34.698] (II) modeset(G0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    34.698] (II) modeset(G0): Supported detailed timing:
[    34.698] (II) modeset(G0): clock: 148.5 MHz   Image Size:  597 x 336 mm
[    34.698] (II) modeset(G0): h_active: 1920  h_sync: 2448  h_sync_end 2492 h_blank_end 2640 h_border: 0
[    34.698] (II) modeset(G0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    34.698] (II) modeset(G0): Supported detailed timing:
[    34.698] (II) modeset(G0): clock: 74.2 MHz   Image Size:  597 x 336 mm
[    34.698] (II) modeset(G0): h_active: 1280  h_sync: 1390  h_sync_end 1430 h_blank_end 1650 h_border: 0
[    34.698] (II) modeset(G0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
[    34.698] (II) modeset(G0): Supported detailed timing:
[    34.698] (II) modeset(G0): clock: 74.2 MHz   Image Size:  597 x 336 mm
[    34.698] (II) modeset(G0): h_active: 1280  h_sync: 1720  h_sync_end 1760 h_blank_end 1980 h_border: 0
[    34.698] (II) modeset(G0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
[    34.698] (II) modeset(G0): Supported detailed timing:
[    34.698] (II) modeset(G0): clock: 27.0 MHz   Image Size:  597 x 336 mm
[    34.698] (II) modeset(G0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
[    34.698] (II) modeset(G0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
[    34.698] (II) modeset(G0): Number of EDID sections to follow: 1
[    34.699] (II) modeset(G0): EDID (in hex):
[    34.699] (II) modeset(G0):     00ffffffffffff004c2dd30d57515130
[    34.699] (II) modeset(G0):     231b0103803c22782a8bb4a954469722
[    34.699] (II) modeset(G0):     1f4c5dbfef80b300810081c081809500
[    34.699] (II) modeset(G0):     a9c0714f0101565e00a0a0a029503020
[    34.699] (II) modeset(G0):     350055502100001a000000fd00324b1b
[    34.699] (II) modeset(G0):     5919000a202020202020000000fc0043
[    34.699] (II) modeset(G0):     3237483731780a2020202020000000ff
[    34.699] (II) modeset(G0):     004854484a3830303132310a202001fa
[    34.699] (II) modeset(G0):     020313b146901f0413031267030c0010
[    34.699] (II) modeset(G0):     000032023a801871382d40582c450055
[    34.699] (II) modeset(G0):     502100001e023a80d072382d40102c45
[    34.699] (II) modeset(G0):     8055502100001e011d007251d01e206e
[    34.699] (II) modeset(G0):     28550055502100001e011d00bc52d01e
[    34.699] (II) modeset(G0):     20b828554055502100001e8c0ad08a20
[    34.699] (II) modeset(G0):     e02d10103e9600555021000018000000
[    34.699] (II) modeset(G0):     000000000000000000000000000000ff
[    34.699] (--) modeset(G0): HDMI max TMDS frequency 250000KHz
[    34.699] (II) modeset(G0): Printing probed modes for output HDMI-1-2
[    34.699] (II) modeset(G0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz e)
[    34.699] (II) modeset(G0): Modeline "1920x1080"x50.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    34.699] (II) modeset(G0): Modeline "1920x1080"x59.9  148.35  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.4 kHz e)
[    34.699] (II) modeset(G0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[    34.699] (II) modeset(G0): Modeline "1600x900"x60.0  108.00  1600 1624 1704 1800  900 901 904 1000 +hsync +vsync (60.0 kHz e)
[    34.700] (II) modeset(G0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    34.700] (II) modeset(G0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    34.700] (II) modeset(G0): Modeline "1440x900"x59.9   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[    34.700] (II) modeset(G0): Modeline "1280x800"x59.9   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[    34.700] (II) modeset(G0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    34.700] (II) modeset(G0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    34.700] (II) modeset(G0): Modeline "1280x720"x50.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[    34.700] (II) modeset(G0): Modeline "1280x720"x59.9   74.18  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    34.700] (II) modeset(G0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    34.700] (II) modeset(G0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    34.700] (II) modeset(G0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    34.700] (II) modeset(G0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    34.700] (II) modeset(G0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    34.700] (II) modeset(G0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    34.700] (II) modeset(G0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    34.700] (II) modeset(G0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    34.700] (II) modeset(G0): Modeline "720x576"x50.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[    34.700] (II) modeset(G0): Modeline "720x480"x60.0   27.03  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    34.700] (II) modeset(G0): Modeline "720x480"x59.9   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    34.700] (II) modeset(G0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    34.700] (II) modeset(G0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    34.700] (II) modeset(G0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    34.700] (II) modeset(G0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    34.700] (II) modeset(G0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    34.700] (II) modeset(G0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    34.700] (==) modeset(G0): Using gamma correction (1.0, 1.0, 1.0)
[    34.700] (==) modeset(G0): DPI set to (96, 96)
[    34.700] (II) Loading sub module "fb"
[    34.701] (II) LoadModule: "fb"
[    34.701] (II) Loading /usr/lib/xorg/modules/libfb.so
[    34.701] (II) Module fb: vendor="X.Org Foundation"
[    34.701]     compiled for 1.19.5, module version = 1.0.0
[    34.701]     ABI class: X.Org ANSI C Emulation, version 0.4
[    34.701] (II) Loading sub module "shadow"
[    34.701] (II) LoadModule: "shadow"
[    34.702] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    34.742] (II) Module shadow: vendor="X.Org Foundation"
[    34.742]     compiled for 1.19.5, module version = 1.1.0
[    34.742]     ABI class: X.Org ANSI C Emulation, version 0.4
[    34.742] (--) Depth 24 pixmap format is 32 bpp
[    34.800] (==) modeset(G0): Backing store enabled
[    34.800] (==) modeset(G0): Silken mouse enabled
[    34.800] (II) modeset(G0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    34.930] (==) modeset(G0): DPMS enabled
[    34.930] (WW) modeset(G0): Option "AllowEmptyInitialConfiguration" is not used
[    34.930] (WW) modeset(G0): Option "IgnoreDisplayDevices" is not used
[    34.930] (II) NVIDIA: Using 6144.00 MB of virtual memory for indirect memory
[    34.930] (II) NVIDIA:     access.
[    34.999] (II) NVIDIA(0): Setting mode "NULL"
[    35.033] (==) NVIDIA(0): Disabling shared memory pixmaps
[    35.033] (==) NVIDIA(0): Backing store enabled
[    35.033] (==) NVIDIA(0): Silken mouse enabled
[    35.033] (==) NVIDIA(0): DPMS enabled
[    35.033] (II) Loading sub module "dri2"
[    35.033] (II) LoadModule: "dri2"
[    35.033] (II) Module "dri2" already built-in
[    35.033] (II) NVIDIA(0): [DRI2] Setup complete
[    35.033] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[    35.033] (--) RandR disabled
[    35.046] (II) SELinux: Disabled on system
[    35.047] (II) Initializing extension GLX
[    35.047] (II) Indirect GLX disabled.

[    38.603] (--) modeset(G0): HDMI max TMDS frequency 250000KHz
[    38.620] randr: falling back to unsynchronized pixmap sharing
[    38.865] randr: falling back to unsynchronized pixmap sharing
[    39.008] (--) modeset(G0): HDMI max TMDS frequency 250000KHz
[    45.765] (--) modeset(G0): HDMI max TMDS frequency 250000KHz
[    60.246] (--) modeset(G0): HDMI max TMDS frequency 250000KHz
[  1616.233] (--) modeset(G0): HDMI max TMDS frequency 250000KHz
[  1627.325] (--) modeset(G0): HDMI max TMDS frequency 250000KHz
```

---

### Post by olegorov on 2018-01-29
Ok, ~/.xprofile works. But what's about 60Hz?!

---

### Post by olegorov on 2018-02-19
NVidia driver 390.25 didn't help. But DP-cable helped. Now I have 2560x1440@60Hz without any settings.

---

