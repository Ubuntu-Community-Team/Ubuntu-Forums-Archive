---
title: "NVIDIA GeForce GT 730m doesn't work properly with nvidia-prime"
date: 2015-03-22
forum: Hardware
---

### Post by Novitk on 2015-03-22
Hi, I use Ubuntu 14.04 LTS. I have a Dell notebook with hybrid video cards, one integrated Intel card and one dedicated NVIDIA GeForce GT 730m card. I've selected the proprietary driver in the repositories (nvidia-331 tested, recommended) but I'm having some problems with nvidia-prime. In theory, I should switch between cards (prime-select nvidia/intel) and just logout and login again. But it doesn't work, video system fails to start when I try to logout and login after switching between cards. I must restart the whole system in order to succesfully switch cards. After the restart:

_When switching to Intel card:_
Everything works just fine, so I can live with the fact that I must restart instead of logout and login when switching to Intel card.

_When switching to NVIDIA card:_
Here is the problem. When I restart, the system is visually all messed up (it seems GTK is not working, icon theme is changed, I get no wallpaper etc). But after the restart, if I logout and login, everything is back to normal. Later, everytime I turn my computer on, I get everything visually messed up again. So everytime I turn my computer on, I have to logout and login in order to fix the visual issues.

What's going on exactly and how do I fix it?

---

### Post by dino99 on 2015-03-22
its known since a while sadly; seems there is no real solution except yours. Maybe choose which card you mainly need and then dont change

---

### Post by Novitk on 2015-03-22
But if I want to mainly use nvidia card, do I really have to logout and login everytime I turn on my computer? I'm ok with the fact that I have to restart the system when switching cards, but I have to logout and login eveytime I turn on my computer when my nvidia card is selected. Every single time I turn my computer on.

---

### Post by Novitk on 2015-03-22
When Intel is selected (everything is fine):

[IMG]http://i.imgur.com/TWpK90R.png[/IMG]


When NVIDIA is selected, everytime I turn on the computer, visual stuff is messed up (icon theme, GTK, wallpaper etc):

[IMG]http://i.imgur.com/eocREI6.png[/IMG]


Then, when I logout and login when NVIDIA is selected, everything comes back to normal. But I have to logout and login **everytime** I turn my computer on:

[IMG]http://i.imgur.com/huYQfrQ.png[/IMG]

---

### Post by Keith_Helms on 2015-03-22
I also have 14.04 and Optimus graphics.  I also get the problem where if I change to the Nvidia GPU using the Nvidia X Server Settings PRIME Profiles option I have to reboot and not just logout and login.  However, once I reboot, everything looks correct and works normally without having to do an extra logout/login.

Are there any error messages under /var/log/Xorg.0.log or /var/log/gpu-manager.log that might give a clue what is going on?

---

### Post by Novitk on 2015-03-24
I would be so happy if restarting was enough :/

/var/log/Xorg.0.log
```
[   757.233] X.Org X Server 1.15.1
Release Date: 2014-04-13
[   757.233] X Protocol Version 11, Revision 0
[   757.233] Build Operating System: Linux 3.2.0-76-generic x86_64 Ubuntu
[   757.233] Current Operating System: Linux hellnatov-mint 3.13.0-37-generic #64-Ubuntu SMP Mon Sep 22 21:28:38 UTC 2014 x86_64
[   757.233] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-37-generic root=UUID=b8190d19-cfbd-433c-a7f0-d3ecc2a73463 ro quiet splash
[   757.233] Build Date: 12 February 2015  02:49:29PM
[   757.233] xorg-server 2:1.15.1-0ubuntu2.7 (For technical support please see http://www.ubuntu.com/support) 
[   757.233] Current version of pixman: 0.30.2
[   757.233] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[   757.233] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   757.233] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Mar 24 11:26:52 2015
[   757.233] (==) Using config file: "/etc/X11/xorg.conf"
[   757.233] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   757.234] (==) ServerLayout "layout"
[   757.234] (**) |-->Screen "nvidia" (0)
[   757.234] (**) |   |-->Monitor "<default monitor>"
[   757.235] (**) |   |-->Device "nvidia"
[   757.235] (==) No monitor specified for screen "nvidia".
	Using a default monitor configuration.
[   757.235] (**) |-->Inactive Device "intel"
[   757.235] (==) Automatically adding devices
[   757.235] (==) Automatically enabling devices
[   757.235] (==) Automatically adding GPU devices
[   757.235] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   757.235] 	Entry deleted from font path.
[   757.235] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   757.235] 	Entry deleted from font path.
[   757.235] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   757.235] 	Entry deleted from font path.
[   757.235] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   757.235] 	Entry deleted from font path.
[   757.235] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   757.235] 	Entry deleted from font path.
[   757.235] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[   757.235] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   757.235] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[   757.235] (II) Loader magic: 0x7f82056abd40
[   757.235] (II) Module ABI versions:
[   757.235] 	X.Org ANSI C Emulation: 0.4
[   757.235] 	X.Org Video Driver: 15.0
[   757.235] 	X.Org XInput driver : 20.0
[   757.235] 	X.Org Server Extension : 8.0
[   757.236] (II) xfree86: Adding drm device (/dev/dri/card1)
[   757.236] (II) xfree86: Adding drm device (/dev/dri/card0)
[   757.238] (--) PCI:*(0:0:2:0) 8086:0166:1028:0591 rev 9, Mem @ 0xf7400000/4194304, 0xd0000000/268435456, I/O @ 0x0000f000/64
[   757.238] (--) PCI: (0:2:0:0) 10de:0fe1:1028:05b2 rev 161, Mem @ 0xf6000000/16777216, 0xe0000000/268435456, 0xf0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[   757.238] Initializing built-in extension Generic Event Extension
[   757.238] Initializing built-in extension SHAPE
[   757.238] Initializing built-in extension MIT-SHM
[   757.238] Initializing built-in extension XInputExtension
[   757.238] Initializing built-in extension XTEST
[   757.238] Initializing built-in extension BIG-REQUESTS
[   757.238] Initializing built-in extension SYNC
[   757.238] Initializing built-in extension XKEYBOARD
[   757.238] Initializing built-in extension XC-MISC
[   757.238] Initializing built-in extension SECURITY
[   757.238] Initializing built-in extension XINERAMA
[   757.238] Initializing built-in extension XFIXES
[   757.238] Initializing built-in extension RENDER
[   757.238] Initializing built-in extension RANDR
[   757.238] Initializing built-in extension COMPOSITE
[   757.239] Initializing built-in extension DAMAGE
[   757.239] Initializing built-in extension MIT-SCREEN-SAVER
[   757.239] Initializing built-in extension DOUBLE-BUFFER
[   757.239] Initializing built-in extension RECORD
[   757.239] Initializing built-in extension DPMS
[   757.239] Initializing built-in extension Present
[   757.239] Initializing built-in extension DRI3
[   757.239] Initializing built-in extension X-Resource
[   757.239] Initializing built-in extension XVideo
[   757.239] Initializing built-in extension XVideo-MotionCompensation
[   757.239] Initializing built-in extension SELinux
[   757.239] Initializing built-in extension XFree86-VidModeExtension
[   757.239] Initializing built-in extension XFree86-DGA
[   757.239] Initializing built-in extension XFree86-DRI
[   757.239] Initializing built-in extension DRI2
[   757.239] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[   757.239] (II) "glx" will be loaded by default.
[   757.239] (WW) "xmir" is not to be loaded by default. Skipping.
[   757.239] (II) LoadModule: "glx"
[   757.239] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[   757.247] (II) Module glx: vendor="NVIDIA Corporation"
[   757.247] 	compiled for 4.0.2, module version = 1.0.0
[   757.247] 	Module class: X.Org Server Extension
[   757.247] (II) NVIDIA GLX Module  331.113  Mon Dec  1 20:24:35 PST 2014
[   757.247] Loading extension GLX
[   757.247] (II) LoadModule: "nvidia"
[   757.247] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[   757.248] (II) Module nvidia: vendor="NVIDIA Corporation"
[   757.248] 	compiled for 4.0.2, module version = 1.0.0
[   757.248] 	Module class: X.Org Video Driver
[   757.248] (II) LoadModule: "modesetting"
[   757.248] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[   757.248] (II) Module modesetting: vendor="X.Org Foundation"
[   757.248] 	compiled for 1.15.0, module version = 0.8.1
[   757.248] 	Module class: X.Org Video Driver
[   757.248] 	ABI class: X.Org Video Driver, version 15.0
[   757.248] (II) NVIDIA dlloader X Driver  331.113  Mon Dec  1 20:01:51 PST 2014
[   757.248] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[   757.248] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[   757.248] (++) using VT number 7


[   757.250] (II) Loading sub module "fb"
[   757.250] (II) LoadModule: "fb"
[   757.251] (II) Loading /usr/lib/xorg/modules/libfb.so
[   757.251] (II) Module fb: vendor="X.Org Foundation"
[   757.251] 	compiled for 1.15.1, module version = 1.0.0
[   757.251] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   757.251] (WW) Unresolved symbol: fbGetGCPrivateKey
[   757.251] (II) Loading sub module "wfb"
[   757.251] (II) LoadModule: "wfb"
[   757.252] (II) Loading /usr/lib/xorg/modules/libwfb.so
[   757.252] (II) Module wfb: vendor="X.Org Foundation"
[   757.252] 	compiled for 1.15.1, module version = 1.0.0
[   757.252] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   757.252] (II) Loading sub module "ramdac"
[   757.252] (II) LoadModule: "ramdac"
[   757.252] (II) Module "ramdac" already built-in
[   757.253] (II) modesetting(G0): using drv /dev/dri/card0
[   757.253] (II) NVIDIA(0): Creating default Display subsection in Screen section
	"nvidia" for depth/fbbpp 24/32
[   757.253] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[   757.253] (==) NVIDIA(0): RGB weight 888
[   757.253] (==) NVIDIA(0): Default visual is TrueColor
[   757.253] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[   757.253] (**) NVIDIA(0): Option "ConstrainCursor" "off"
[   757.253] (**) NVIDIA(0): Option "AllowEmptyInitialConfiguration" "on"
[   757.253] (**) NVIDIA(0): Option "IgnoreDisplayDevices" "CRT"
[   757.253] (**) NVIDIA(0): Enabling 2D acceleration
[   757.372] (II) NVIDIA(GPU-0): Found DRM driver nvidia-drm (20130102)
[   757.373] (II) NVIDIA(0): NVIDIA GPU GeForce GT 730M (GK107) at PCI:2:0:0 (GPU-0)
[   757.373] (--) NVIDIA(0): Memory: 2097152 kBytes
[   757.373] (--) NVIDIA(0): VideoBIOS: 80.07.70.00.1f
[   757.373] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[   757.373] (--) NVIDIA(0): Valid display device(s) on GeForce GT 730M at PCI:2:0:0
[   757.373] (--) NVIDIA(0):     none
[   757.373] (II) NVIDIA(0): Validated MetaModes:
[   757.373] (II) NVIDIA(0):     "NULL"
[   757.373] (II) NVIDIA(0): Virtual screen size determined to be 640 x 480
[   757.373] (WW) NVIDIA(0): Unable to get display device for DPI computation.
[   757.373] (==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
[   757.373] (==) modesetting(G0): Depth 24, (==) framebuffer bpp 32
[   757.373] (==) modesetting(G0): RGB weight 888
[   757.373] (==) modesetting(G0): Default visual is TrueColor
[   757.373] (II) modesetting(G0): ShadowFB: preferred YES, enabled YES
[   757.373] (II) modesetting(G0): Output LVDS-1-0 has no monitor section
[   757.374] (II) modesetting(G0): Output VGA-1-0 has no monitor section
[   757.523] (II) modesetting(G0): Output HDMI-1-0 has no monitor section
[   757.572] (II) modesetting(G0): Output DisplayPort-1-0 has no monitor section
[   757.572] (II) modesetting(G0): EDID for output LVDS-1-0
[   757.572] (II) modesetting(G0): Manufacturer: CMN  Model: 1476  Serial#: 0
[   757.572] (II) modesetting(G0): Year: 2011  Week: 51
[   757.572] (II) modesetting(G0): EDID Version: 1.4
[   757.572] (II) modesetting(G0): Digital Display Input
[   757.572] (II) modesetting(G0): 6 bits per channel
[   757.572] (II) modesetting(G0): Digital interface is undefined
[   757.572] (II) modesetting(G0): Max Image Size [cm]: horiz.: 31  vert.: 17
[   757.572] (II) modesetting(G0): Gamma: 2.20
[   757.572] (II) modesetting(G0): No DPMS capabilities specified
[   757.572] (II) modesetting(G0): Supported color encodings: RGB 4:4:4 
[   757.572] (II) modesetting(G0): First detailed timing is preferred mode
[   757.572] (II) modesetting(G0): Preferred mode is native pixel format and refresh rate
[   757.572] (II) modesetting(G0): redX: 0.590 redY: 0.342   greenX: 0.330 greenY: 0.562
[   757.572] (II) modesetting(G0): blueX: 0.160 blueY: 0.140   whiteX: 0.313 whiteY: 0.329
[   757.572] (II) modesetting(G0): Manufacturer's mask: 0
[   757.572] (II) modesetting(G0): Supported detailed timing:
[   757.572] (II) modesetting(G0): clock: 76.7 MHz   Image Size:  309 x 174 mm
[   757.572] (II) modesetting(G0): h_active: 1366  h_sync: 1399  h_sync_end 1467 h_blank_end 1579 h_border: 0
[   757.572] (II) modesetting(G0): v_active: 768  v_sync: 772  v_sync_end 785 v_blanking: 809 v_border: 0
[   757.572] (II) modesetting(G0): Supported detailed timing:
[   757.572] (II) modesetting(G0): clock: 51.1 MHz   Image Size:  309 x 174 mm
[   757.572] (II) modesetting(G0): h_active: 1366  h_sync: 1399  h_sync_end 1467 h_blank_end 1579 h_border: 0
[   757.572] (II) modesetting(G0): v_active: 768  v_sync: 772  v_sync_end 785 v_blanking: 809 v_border: 0
[   757.572] (II) modesetting(G0):  Y9P7N€141BGE
[   757.572] (II) modesetting(G0): Unknown vendor-specific block 0
[   757.572] (II) modesetting(G0): EDID (in hex):
[   757.572] (II) modesetting(G0): 	00ffffffffffff000dae761400000000
[   757.572] (II) modesetting(G0): 	33150104901f1178022b359757548f29
[   757.572] (II) modesetting(G0): 	23505400000001010101010101010101
[   757.572] (II) modesetting(G0): 	010101010101f21d56d5500029302144
[   757.572] (II) modesetting(G0): 	4d0035ae1000001af71356d550002930
[   757.572] (II) modesetting(G0): 	21444d0035ae1000001a000000fe0059
[   757.572] (II) modesetting(G0): 	3950374e803134314247450a00000000
[   757.572] (II) modesetting(G0): 	00004131940110000001010a20200014
[   757.572] (II) modesetting(G0): Printing probed modes for output LVDS-1-0
[   757.572] (II) modesetting(G0): Modeline "1366x768"x60.0   76.66  1366 1399 1467 1579  768 772 785 809 +hsync -vsync (48.5 kHz eP)
[   757.572] (II) modesetting(G0): Modeline "1366x768"x40.0   51.11  1366 1399 1467 1579  768 772 785 809 +hsync -vsync (32.4 kHz e)
[   757.572] (II) modesetting(G0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz d)
[   757.572] (II) modesetting(G0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz d)
[   757.572] (II) modesetting(G0): Modeline "1024x768"x120.1  133.47  1024 1100 1212 1400  768 768 770 794 doublescan -hsync +vsync (95.3 kHz d)
[   757.572] (II) modesetting(G0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz d)
[   757.572] (II) modesetting(G0): Modeline "960x720"x120.0  117.00  960 1024 1128 1300  720 720 722 750 doublescan -hsync +vsync (90.0 kHz d)
[   757.572] (II) modesetting(G0): Modeline "928x696"x120.1  109.15  928 976 1088 1264  696 696 698 719 doublescan -hsync +vsync (86.4 kHz d)
[   757.572] (II) modesetting(G0): Modeline "896x672"x120.0  102.40  896 960 1060 1224  672 672 674 697 doublescan -hsync +vsync (83.7 kHz d)
[   757.572] (II) modesetting(G0): Modeline "960x600"x120.0   77.00  960 984 1000 1040  600 601 604 617 doublescan +hsync -vsync (74.0 kHz d)
[   757.572] (II) modesetting(G0): Modeline "960x540"x120.0   69.25  960 984 1000 1040  540 541 544 555 doublescan +hsync -vsync (66.6 kHz d)
[   757.572] (II) modesetting(G0): Modeline "800x600"x120.0   81.00  800 832 928 1080  600 600 602 625 doublescan +hsync +vsync (75.0 kHz d)
[   757.572] (II) modesetting(G0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz d)
[   757.572] (II) modesetting(G0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz d)
[   757.572] (II) modesetting(G0): Modeline "840x525"x120.0   73.12  840 892 980 1120  525 526 529 544 doublescan -hsync +vsync (65.3 kHz d)
[   757.572] (II) modesetting(G0): Modeline "840x525"x119.8   59.50  840 864 880 920  525 526 529 540 doublescan +hsync -vsync (64.7 kHz d)
[   757.572] (II) modesetting(G0): Modeline "800x512"x120.3   51.56  800 800 828 832  512 512 514 515 doublescan +hsync +vsync (62.0 kHz d)
[   757.572] (II) modesetting(G0): Modeline "700x525"x120.0   61.00  700 744 820 940  525 526 532 541 doublescan +hsync +vsync (64.9 kHz d)
[   757.572] (II) modesetting(G0): Modeline "640x512"x120.0   54.00  640 664 720 844  512 512 514 533 doublescan +hsync +vsync (64.0 kHz d)
[   757.572] (II) modesetting(G0): Modeline "720x450"x119.8   53.25  720 760 836 952  450 451 454 467 doublescan -hsync +vsync (55.9 kHz d)
[   757.572] (II) modesetting(G0): Modeline "640x480"x120.0   54.00  640 688 744 900  480 480 482 500 doublescan +hsync +vsync (60.0 kHz d)
[   757.572] (II) modesetting(G0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz d)
[   757.572] (II) modesetting(G0): Modeline "680x384"x119.6   42.38  680 716 784 888  384 385 390 399 doublescan -hsync +vsync (47.7 kHz d)
[   757.572] (II) modesetting(G0): Modeline "680x384"x119.9   36.00  680 704 720 760  384 385 390 395 doublescan +hsync -vsync (47.4 kHz d)
[   757.572] (II) modesetting(G0): Modeline "576x432"x120.1   40.81  576 608 668 760  432 432 434 447 doublescan -hsync +vsync (53.7 kHz d)
[   757.572] (II) modesetting(G0): Modeline "512x384"x120.0   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync (48.4 kHz d)
[   757.572] (II) modesetting(G0): Modeline "400x300"x120.6   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz d)
[   757.572] (II) modesetting(G0): Modeline "400x300"x112.7   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (35.2 kHz d)
[   757.572] (II) modesetting(G0): Modeline "320x240"x120.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz d)
[   757.573] (II) modesetting(G0): EDID for output VGA-1-0
[   757.717] (II) modesetting(G0): EDID for output HDMI-1-0
[   757.717] (II) modesetting(G0): Manufacturer: GSM  Model: 56f0  Serial#: 16843009
[   757.717] (II) modesetting(G0): Year: 2011  Week: 1
[   757.717] (II) modesetting(G0): EDID Version: 1.3
[   757.717] (II) modesetting(G0): Digital Display Input
[   757.717] (II) modesetting(G0): Max Image Size [cm]: horiz.: 51  vert.: 29
[   757.717] (II) modesetting(G0): Gamma: 2.20
[   757.717] (II) modesetting(G0): No DPMS capabilities specified
[   757.717] (II) modesetting(G0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[   757.717] (II) modesetting(G0): First detailed timing is preferred mode
[   757.717] (II) modesetting(G0): redX: 0.635 redY: 0.342   greenX: 0.292 greenY: 0.611
[   757.717] (II) modesetting(G0): blueX: 0.147 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
[   757.717] (II) modesetting(G0): Supported established timings:
[   757.717] (II) modesetting(G0): 720x400@70Hz
[   757.717] (II) modesetting(G0): 640x480@60Hz
[   757.717] (II) modesetting(G0): 640x480@75Hz
[   757.717] (II) modesetting(G0): 800x600@56Hz
[   757.717] (II) modesetting(G0): 800x600@60Hz
[   757.717] (II) modesetting(G0): 800x600@75Hz
[   757.717] (II) modesetting(G0): 832x624@75Hz
[   757.717] (II) modesetting(G0): 1024x768@60Hz
[   757.717] (II) modesetting(G0): 1024x768@75Hz
[   757.717] (II) modesetting(G0): 1280x1024@75Hz
[   757.717] (II) modesetting(G0): 1152x864@75Hz
[   757.717] (II) modesetting(G0): Manufacturer's mask: 0
[   757.717] (II) modesetting(G0): Supported standard timings:
[   757.717] (II) modesetting(G0): #0: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[   757.717] (II) modesetting(G0): #1: hsize: 1280  vsize 1024  refresh: 75  vid: 36737
[   757.717] (II) modesetting(G0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[   757.717] (II) modesetting(G0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[   757.717] (II) modesetting(G0): Supported detailed timing:
[   757.717] (II) modesetting(G0): clock: 138.5 MHz   Image Size:  510 x 290 mm
[   757.717] (II) modesetting(G0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
[   757.717] (II) modesetting(G0): v_active: 1080  v_sync: 1083  v_sync_end 1088 v_blanking: 1111 v_border: 0
[   757.717] (II) modesetting(G0): Supported detailed timing:
[   757.717] (II) modesetting(G0): clock: 148.5 MHz   Image Size:  510 x 290 mm
[   757.717] (II) modesetting(G0): h_active: 1920  h_sync: 2003  h_sync_end 2047 h_blank_end 2200 h_border: 0
[   757.717] (II) modesetting(G0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[   757.717] (II) modesetting(G0): Ranges: V min: 56 V max: 61 Hz, H min: 30 H max: 83 kHz, PixClock max 155 MHz
[   757.717] (II) modesetting(G0): Monitor name: W2353
[   757.717] (II) modesetting(G0): Supported detailed timing:
[   757.717] (II) modesetting(G0): clock: 148.5 MHz   Image Size:  510 x 290 mm
[   757.717] (II) modesetting(G0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[   757.717] (II) modesetting(G0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[   757.717] (II) modesetting(G0): Supported detailed timing:
[   757.717] (II) modesetting(G0): clock: 74.2 MHz   Image Size:  510 x 290 mm
[   757.717] (II) modesetting(G0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[   757.717] (II) modesetting(G0): v_active: 540  v_sync: 542  v_sync_end 547 v_blanking: 562 v_border: 0
[   757.717] (II) modesetting(G0): Supported detailed timing:
[   757.717] (II) modesetting(G0): clock: 74.2 MHz   Image Size:  510 x 290 mm
[   757.717] (II) modesetting(G0): h_active: 1280  h_sync: 1390  h_sync_end 1430 h_blank_end 1650 h_border: 0
[   757.717] (II) modesetting(G0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
[   757.717] (II) modesetting(G0): Supported detailed timing:
[   757.717] (II) modesetting(G0): clock: 27.0 MHz   Image Size:  510 x 290 mm
[   757.717] (II) modesetting(G0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
[   757.717] (II) modesetting(G0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
[   757.717] (II) modesetting(G0): Number of EDID sections to follow: 1
[   757.717] (II) modesetting(G0): EDID (in hex):
[   757.717] (II) modesetting(G0): 	00ffffffffffff001e6df05601010101
[   757.717] (II) modesetting(G0): 	0115010380331d780aaec5a2574a9c25
[   757.717] (II) modesetting(G0): 	125054a76b80b300818f8180714f0101
[   757.717] (II) modesetting(G0): 	0101010101011a3680a070381f403020
[   757.717] (II) modesetting(G0): 	3500fe221100001e023a801871382d40
[   757.717] (II) modesetting(G0): 	532c4500fe221100001e000000fd0038
[   757.717] (II) modesetting(G0): 	3d1e530f000a202020202020000000fc
[   757.717] (II) modesetting(G0): 	0057323335330a20202020202020016b
[   757.717] (II) modesetting(G0): 	020321f14e900403011412051f101300
[   757.717] (II) modesetting(G0): 	000000230907078301000065030c0010
[   757.717] (II) modesetting(G0): 	00023a801871382d40582c4500fe2211
[   757.718] (II) modesetting(G0): 	00001e011d8018711c1620582c2500fe
[   757.718] (II) modesetting(G0): 	221100009e011d007251d01e206e2855
[   757.718] (II) modesetting(G0): 	00fe221100001e8c0ad08a20e02d1010
[   757.718] (II) modesetting(G0): 	3e9600fe221100001800000000000000
[   757.718] (II) modesetting(G0): 	000000000000000000000000000000de
[   757.718] (II) modesetting(G0): Printing probed modes for output HDMI-1-0
[   757.718] (II) modesetting(G0): Modeline "1920x1080"x59.9  138.50  1920 1968 2000 2080  1080 1083 1088 1111 +hsync +vsync (66.6 kHz eP)
[   757.718] (II) modesetting(G0): Modeline "1920x1080"x60.0  148.50  1920 2003 2047 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz e)
[   757.718] (II) modesetting(G0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz e)
[   757.718] (II) modesetting(G0): Modeline "1920x1080"x50.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[   757.718] (II) modesetting(G0): Modeline "1920x1080"x59.9  148.35  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.4 kHz e)
[   757.718] (II) modesetting(G0): Modeline "1920x1080i"x60.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[   757.718] (II) modesetting(G0): Modeline "1920x1080i"x50.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz e)
[   757.718] (II) modesetting(G0): Modeline "1920x1080i"x59.9   74.18  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.7 kHz e)
[   757.718] (II) modesetting(G0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[   757.718] (II) modesetting(G0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   757.718] (II) modesetting(G0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   757.718] (II) modesetting(G0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   757.718] (II) modesetting(G0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[   757.718] (II) modesetting(G0): Modeline "1280x720"x50.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[   757.718] (II) modesetting(G0): Modeline "1280x720"x59.9   74.18  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[   757.718] (II) modesetting(G0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz e)
[   757.718] (II) modesetting(G0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   757.718] (II) modesetting(G0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[   757.718] (II) modesetting(G0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   757.718] (II) modesetting(G0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   757.718] (II) modesetting(G0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[   757.718] (II) modesetting(G0): Modeline "720x576"x50.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[   757.718] (II) modesetting(G0): Modeline "720x480"x60.0   27.03  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[   757.718] (II) modesetting(G0): Modeline "720x480"x59.9   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[   757.718] (II) modesetting(G0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   757.718] (II) modesetting(G0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   757.718] (II) modesetting(G0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   757.718] (II) modesetting(G0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   757.768] (II) modesetting(G0): EDID for output DisplayPort-1-0
[   757.768] (II) modesetting(G0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[   757.768] (==) modesetting(G0): DPI set to (96, 96)
[   757.768] (II) Loading sub module "fb"
[   757.768] (II) LoadModule: "fb"
[   757.768] (II) Loading /usr/lib/xorg/modules/libfb.so
[   757.769] (II) Module fb: vendor="X.Org Foundation"
[   757.769] 	compiled for 1.15.1, module version = 1.0.0
[   757.769] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   757.769] (II) Loading sub module "shadow"
[   757.769] (II) LoadModule: "shadow"
[   757.769] (II) Loading /usr/lib/xorg/modules/libshadow.so
[   757.770] (II) Module shadow: vendor="X.Org Foundation"
[   757.770] 	compiled for 1.15.1, module version = 1.1.0
[   757.770] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   757.770] (--) Depth 24 pixmap format is 32 bpp
[   757.770] (==) modesetting(G0): Backing store enabled
[   757.770] (==) modesetting(G0): Silken mouse enabled
[   757.770] (II) modesetting(G0): RandR 1.2 enabled, ignore the following RandR disabled message.
[   757.771] (==) modesetting(G0): DPMS enabled
[   757.771] (WW) modesetting(G0): Option "AllowEmptyInitialConfiguration" is not used
[   757.771] (WW) modesetting(G0): Option "IgnoreDisplayDevices" is not used
[   758.208] (II) NVIDIA: Using 3072.00 MB of virtual memory for indirect memory
[   758.208] (II) NVIDIA:     access.
[   758.216] (II) NVIDIA(0): Setting mode "NULL"
[   758.229] (II) NVIDIA(0): Built-in logo is bigger than the screen.
[   758.229] Loading extension NV-GLX
[   758.232] (==) NVIDIA(0): Disabling shared memory pixmaps
[   758.232] (==) NVIDIA(0): Backing store enabled
[   758.232] (==) NVIDIA(0): Silken mouse enabled
[   758.233] (==) NVIDIA(0): DPMS enabled
[   758.233] Loading extension NV-CONTROL
[   758.233] (II) Loading sub module "dri2"
[   758.233] (II) LoadModule: "dri2"
[   758.233] (II) Module "dri2" already built-in
[   758.233] (II) NVIDIA(0): [DRI2] Setup complete
[   758.233] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[   758.233] (--) RandR disabled
[   758.236] (II) SELinux: Disabled on system
[   758.237] (II) Initializing extension GLX
[   758.237] (II) modesetting(G0): Damage tracking initialized
[   758.246] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   758.248] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[   758.248] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   758.248] (II) LoadModule: "evdev"
[   758.248] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   758.248] (II) Module evdev: vendor="X.Org Foundation"
[   758.248] 	compiled for 1.15.0, module version = 2.8.2
[   758.248] 	Module class: X.Org XInput Driver
[   758.248] 	ABI class: X.Org XInput driver, version 20.0
[   758.248] (II) Using input driver 'evdev' for 'Power Button'
[   758.248] (**) Power Button: always reports core events
[   758.248] (**) evdev: Power Button: Device: "/dev/input/event3"
[   758.248] (--) evdev: Power Button: Vendor 0 Product 0x1
[   758.248] (--) evdev: Power Button: Found keys
[   758.248] (II) evdev: Power Button: Configuring as keyboard
[   758.248] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[   758.248] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[   758.248] (**) Option "xkb_rules" "evdev"
[   758.248] (**) Option "xkb_model" "pc105"
[   758.248] (**) Option "xkb_layout" "br"
[   758.249] (II) XKB: reuse xkmfile /var/lib/xkb/server-A37B2EFB8B2398771EA3BE2A51A1034B516E3F38.xkm
[   758.250] (II) config/udev: Adding input device Video Bus (/dev/input/event9)
[   758.250] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[   758.250] (II) Using input driver 'evdev' for 'Video Bus'
[   758.250] (**) Video Bus: always reports core events
[   758.250] (**) evdev: Video Bus: Device: "/dev/input/event9"
[   758.250] (--) evdev: Video Bus: Vendor 0 Product 0x6
[   758.250] (--) evdev: Video Bus: Found keys
[   758.250] (II) evdev: Video Bus: Configuring as keyboard
[   758.250] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input10/event9"
[   758.250] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[   758.250] (**) Option "xkb_rules" "evdev"
[   758.250] (**) Option "xkb_model" "pc105"
[   758.250] (**) Option "xkb_layout" "br"
[   758.250] (II) config/udev: Adding input device Video Bus (/dev/input/event8)
[   758.250] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[   758.250] (II) Using input driver 'evdev' for 'Video Bus'
[   758.250] (**) Video Bus: always reports core events
[   758.250] (**) evdev: Video Bus: Device: "/dev/input/event8"
[   758.250] (--) evdev: Video Bus: Vendor 0 Product 0x6
[   758.250] (--) evdev: Video Bus: Found keys
[   758.250] (II) evdev: Video Bus: Configuring as keyboard
[   758.250] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1a/LNXVIDEO:00/input/input9/event8"
[   758.250] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 8)
[   758.250] (**) Option "xkb_rules" "evdev"
[   758.250] (**) Option "xkb_model" "pc105"
[   758.250] (**) Option "xkb_layout" "br"
[   758.250] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[   758.250] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   758.250] (II) Using input driver 'evdev' for 'Power Button'
[   758.250] (**) Power Button: always reports core events
[   758.250] (**) evdev: Power Button: Device: "/dev/input/event1"
[   758.250] (--) evdev: Power Button: Vendor 0 Product 0x1
[   758.250] (--) evdev: Power Button: Found keys
[   758.250] (II) evdev: Power Button: Configuring as keyboard
[   758.250] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[   758.250] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 9)
[   758.250] (**) Option "xkb_rules" "evdev"
[   758.250] (**) Option "xkb_model" "pc105"
[   758.250] (**) Option "xkb_layout" "br"
[   758.251] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[   758.251] (II) No input driver specified, ignoring this device.
[   758.251] (II) This device may have been added with another device file.
[   758.251] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[   758.251] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[   758.251] (II) Using input driver 'evdev' for 'Sleep Button'
[   758.251] (**) Sleep Button: always reports core events
[   758.251] (**) evdev: Sleep Button: Device: "/dev/input/event2"
[   758.251] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[   758.251] (--) evdev: Sleep Button: Found keys
[   758.251] (II) evdev: Sleep Button: Configuring as keyboard
[   758.251] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2/event2"
[   758.251] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 10)
[   758.251] (**) Option "xkb_rules" "evdev"
[   758.251] (**) Option "xkb_model" "pc105"
[   758.251] (**) Option "xkb_layout" "br"
[   758.251] (II) config/udev: Adding drm device (/dev/dri/card1) card1 /sys/devices/pci0000:00/0000:00:01.0/0000:02:00.0/drm/card1
[   758.251] (II) config/udev: Ignoring already known drm device (/dev/dri/card1)
[   758.251] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:02.0/drm/card0
[   758.251] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[   758.251] (II) config/udev: Adding input device Microsoft  Microsoft Basic Optical Mouse v2.0  (/dev/input/event6)
[   758.251] (**) Microsoft  Microsoft Basic Optical Mouse v2.0 : Applying InputClass "evdev pointer catchall"
[   758.251] (II) Using input driver 'evdev' for 'Microsoft  Microsoft Basic Optical Mouse v2.0 '
[   758.251] (**) Microsoft  Microsoft Basic Optical Mouse v2.0 : always reports core events
[   758.251] (**) evdev: Microsoft  Microsoft Basic Optical Mouse v2.0 : Device: "/dev/input/event6"
[   758.251] (--) evdev: Microsoft  Microsoft Basic Optical Mouse v2.0 : Vendor 0x45e Product 0xcb
[   758.251] (--) evdev: Microsoft  Microsoft Basic Optical Mouse v2.0 : Found 3 mouse buttons
[   758.251] (--) evdev: Microsoft  Microsoft Basic Optical Mouse v2.0 : Found scroll wheel(s)
[   758.251] (--) evdev: Microsoft  Microsoft Basic Optical Mouse v2.0 : Found relative axes
[   758.251] (--) evdev: Microsoft  Microsoft Basic Optical Mouse v2.0 : Found x and y relative axes
[   758.251] (II) evdev: Microsoft  Microsoft Basic Optical Mouse v2.0 : Configuring as mouse
[   758.251] (II) evdev: Microsoft  Microsoft Basic Optical Mouse v2.0 : Adding scrollwheel support
[   758.251] (**) evdev: Microsoft  Microsoft Basic Optical Mouse v2.0 : YAxisMapping: buttons 4 and 5
[   758.251] (**) evdev: Microsoft  Microsoft Basic Optical Mouse v2.0 : EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   758.251] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1:1.0/input/input7/event6"
[   758.251] (II) XINPUT: Adding extended input device "Microsoft  Microsoft Basic Optical Mouse v2.0 " (type: MOUSE, id 11)
[   758.251] (II) evdev: Microsoft  Microsoft Basic Optical Mouse v2.0 : initialized for relative axes.
[   758.252] (**) Microsoft  Microsoft Basic Optical Mouse v2.0 : (accel) keeping acceleration scheme 1
[   758.252] (**) Microsoft  Microsoft Basic Optical Mouse v2.0 : (accel) acceleration profile 0
[   758.252] (**) Microsoft  Microsoft Basic Optical Mouse v2.0 : (accel) acceleration factor: 2.000
[   758.252] (**) Microsoft  Microsoft Basic Optical Mouse v2.0 : (accel) acceleration threshold: 4
[   758.252] (II) config/udev: Adding input device Microsoft  Microsoft Basic Optical Mouse v2.0  (/dev/input/mouse1)
[   758.252] (II) No input driver specified, ignoring this device.
[   758.252] (II) This device may have been added with another device file.
[   758.252] (II) config/udev: Adding input device USB USB Keykoard (/dev/input/event7)
[   758.252] (**) USB USB Keykoard: Applying InputClass "evdev keyboard catchall"
[   758.252] (II) Using input driver 'evdev' for 'USB USB Keykoard'
[   758.252] (**) USB USB Keykoard: always reports core events
[   758.252] (**) evdev: USB USB Keykoard: Device: "/dev/input/event7"
[   758.252] (--) evdev: USB USB Keykoard: Vendor 0x1a2c Product 0x21
[   758.252] (--) evdev: USB USB Keykoard: Found keys
[   758.252] (II) evdev: USB USB Keykoard: Configuring as keyboard
[   758.252] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-2/3-2:1.0/input/input8/event7"
[   758.252] (II) XINPUT: Adding extended input device "USB USB Keykoard" (type: KEYBOARD, id 12)
[   758.252] (**) Option "xkb_rules" "evdev"
[   758.252] (**) Option "xkb_model" "pc105"
[   758.252] (**) Option "xkb_layout" "br"
[   758.252] (II) config/udev: Adding input device USB USB Keykoard (/dev/input/event10)
[   758.252] (**) USB USB Keykoard: Applying InputClass "evdev keyboard catchall"
[   758.252] (II) Using input driver 'evdev' for 'USB USB Keykoard'
[   758.252] (**) USB USB Keykoard: always reports core events
[   758.252] (**) evdev: USB USB Keykoard: Device: "/dev/input/event10"
[   758.252] (--) evdev: USB USB Keykoard: Vendor 0x1a2c Product 0x21
[   758.252] (--) evdev: USB USB Keykoard: Found 1 mouse buttons
[   758.252] (--) evdev: USB USB Keykoard: Found scroll wheel(s)
[   758.252] (--) evdev: USB USB Keykoard: Found relative axes
[   758.252] (II) evdev: USB USB Keykoard: Forcing relative x/y axes to exist.
[   758.252] (--) evdev: USB USB Keykoard: Found absolute axes
[   758.252] (II) evdev: USB USB Keykoard: Forcing absolute x/y axes to exist.
[   758.252] (--) evdev: USB USB Keykoard: Found keys
[   758.252] (II) evdev: USB USB Keykoard: Configuring as mouse
[   758.252] (II) evdev: USB USB Keykoard: Configuring as keyboard
[   758.252] (II) evdev: USB USB Keykoard: Adding scrollwheel support
[   758.252] (**) evdev: USB USB Keykoard: YAxisMapping: buttons 4 and 5
[   758.252] (**) evdev: USB USB Keykoard: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   758.252] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-2/3-2:1.1/input/input11/event10"
[   758.252] (II) XINPUT: Adding extended input device "USB USB Keykoard" (type: KEYBOARD, id 13)
[   758.252] (**) Option "xkb_rules" "evdev"
[   758.252] (**) Option "xkb_model" "pc105"
[   758.252] (**) Option "xkb_layout" "br"
[   758.253] (II) evdev: USB USB Keykoard: initialized for relative axes.
[   758.253] (WW) evdev: USB USB Keykoard: ignoring absolute axes.
[   758.253] (**) USB USB Keykoard: (accel) keeping acceleration scheme 1
[   758.253] (**) USB USB Keykoard: (accel) acceleration profile 0
[   758.253] (**) USB USB Keykoard: (accel) acceleration factor: 2.000
[   758.253] (**) USB USB Keykoard: (accel) acceleration threshold: 4
[   758.253] (II) config/udev: Adding input device Laptop_Integrated_Webcam_HD (/dev/input/event15)
[   758.253] (**) Laptop_Integrated_Webcam_HD: Applying InputClass "evdev keyboard catchall"
[   758.253] (II) Using input driver 'evdev' for 'Laptop_Integrated_Webcam_HD'
[   758.253] (**) Laptop_Integrated_Webcam_HD: always reports core events
[   758.253] (**) evdev: Laptop_Integrated_Webcam_HD: Device: "/dev/input/event15"
[   758.253] (--) evdev: Laptop_Integrated_Webcam_HD: Vendor 0xc45 Product 0x64af
[   758.253] (--) evdev: Laptop_Integrated_Webcam_HD: Found keys
[   758.253] (II) evdev: Laptop_Integrated_Webcam_HD: Configuring as keyboard
[   758.253] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/input/input17/event15"
[   758.253] (II) XINPUT: Adding extended input device "Laptop_Integrated_Webcam_HD" (type: KEYBOARD, id 14)
[   758.253] (**) Option "xkb_rules" "evdev"
[   758.253] (**) Option "xkb_model" "pc105"
[   758.253] (**) Option "xkb_layout" "br"
[   758.253] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event13)
[   758.253] (II) No input driver specified, ignoring this device.
[   758.253] (II) This device may have been added with another device file.
[   758.253] (II) config/udev: Adding input device HDA Intel PCH Front Headphone (/dev/input/event12)
[   758.253] (II) No input driver specified, ignoring this device.
[   758.253] (II) This device may have been added with another device file.
[   758.253] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event11)
[   758.254] (II) No input driver specified, ignoring this device.
[   758.254] (II) This device may have been added with another device file.
[   758.254] (II) config/udev: Adding input device ELAN Touchscreen (/dev/input/event14)
[   758.254] (**) ELAN Touchscreen: Applying InputClass "evdev touchscreen catchall"
[   758.254] (II) Using input driver 'evdev' for 'ELAN Touchscreen'
[   758.254] (**) ELAN Touchscreen: always reports core events
[   758.254] (**) evdev: ELAN Touchscreen: Device: "/dev/input/event14"
[   758.254] (II) evdev: ELAN Touchscreen: Using mtdev for this device
[   758.254] (--) evdev: ELAN Touchscreen: Vendor 0x4f3 Product 0x3d
[   758.254] (--) evdev: ELAN Touchscreen: Found absolute axes
[   758.254] (--) evdev: ELAN Touchscreen: Found absolute multitouch axes
[   758.254] (II) evdev: ELAN Touchscreen: No buttons found, faking one.
[   758.254] (--) evdev: ELAN Touchscreen: Found x and y absolute axes
[   758.254] (--) evdev: ELAN Touchscreen: Found absolute touchscreen
[   758.254] (II) evdev: ELAN Touchscreen: Configuring as touchscreen
[   758.254] (**) evdev: ELAN Touchscreen: YAxisMapping: buttons 4 and 5
[   758.254] (**) evdev: ELAN Touchscreen: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   758.254] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/input/input15/event14"
[   758.254] (II) XINPUT: Adding extended input device "ELAN Touchscreen" (type: TOUCHSCREEN, id 15)
[   758.254] (II) evdev: ELAN Touchscreen: initialized for absolute axes.
[   758.254] (**) ELAN Touchscreen: (accel) keeping acceleration scheme 1
[   758.254] (**) ELAN Touchscreen: (accel) acceleration profile 0
[   758.254] (**) ELAN Touchscreen: (accel) acceleration factor: 2.000
[   758.254] (**) ELAN Touchscreen: (accel) acceleration threshold: 4
[   758.254] (II) config/udev: Adding input device ELAN Touchscreen (/dev/input/mouse2)
[   758.254] (II) No input driver specified, ignoring this device.
[   758.254] (II) This device may have been added with another device file.
[   758.254] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[   758.254] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[   758.254] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[   758.254] (**) AT Translated Set 2 keyboard: always reports core events
[   758.254] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[   758.254] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[   758.254] (--) evdev: AT Translated Set 2 keyboard: Found keys
[   758.254] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[   758.254] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[   758.254] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 16)
[   758.254] (**) Option "xkb_rules" "evdev"
[   758.254] (**) Option "xkb_model" "pc105"
[   758.254] (**) Option "xkb_layout" "br"
[   758.255] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event5)
[   758.255] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[   758.255] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[   758.255] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[   758.255] (II) LoadModule: "synaptics"
[   758.255] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[   758.255] (II) Module synaptics: vendor="X.Org Foundation"
[   758.255] 	compiled for 1.15.0, module version = 1.7.4
[   758.255] 	Module class: X.Org XInput Driver
[   758.255] 	ABI class: X.Org XInput driver, version 20.0
[   758.255] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[   758.255] (**) SynPS/2 Synaptics TouchPad: always reports core events
[   758.255] (**) Option "Device" "/dev/input/event5"
[   758.276] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5674 (res 44)
[   758.276] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4754 (res 68)
[   758.276] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[   758.276] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[   758.276] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple
[   758.276] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[   758.276] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[   758.276] (**) SynPS/2 Synaptics TouchPad: always reports core events
[   758.288] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input6/event5"
[   758.288] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 17)
[   758.288] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[   758.288] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[   758.288] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.037
[   758.289] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[   758.289] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[   758.289] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[   758.289] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[   758.289] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[   758.290] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[   758.290] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[   758.294] (II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event16)
[   758.294] (**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[   758.294] (II) Using input driver 'evdev' for 'Dell WMI hotkeys'
[   758.294] (**) Dell WMI hotkeys: always reports core events
[   758.294] (**) evdev: Dell WMI hotkeys: Device: "/dev/input/event16"
[   758.294] (--) evdev: Dell WMI hotkeys: Vendor 0 Product 0
[   758.295] (--) evdev: Dell WMI hotkeys: Found keys
[   758.295] (II) evdev: Dell WMI hotkeys: Configuring as keyboard
[   758.295] (**) Option "config_info" "udev:/sys/devices/virtual/input/input18/event16"
[   758.295] (II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD, id 18)
[   758.295] (**) Option "xkb_rules" "evdev"
[   758.295] (**) Option "xkb_model" "pc105"
[   758.295] (**) Option "xkb_layout" "br"
[   758.595] (II) modesetting(G0): EDID vendor "CMN", prod id 5238
[   758.595] (II) modesetting(G0): Printing DDC gathered Modelines:
[   758.595] (II) modesetting(G0): Modeline "1366x768"x0.0   76.66  1366 1399 1467 1579  768 772 785 809 +hsync -vsync (48.5 kHz eP)
[   758.595] (II) modesetting(G0): Modeline "1366x768"x0.0   51.11  1366 1399 1467 1579  768 772 785 809 +hsync -vsync (32.4 kHz e)
[   758.792] reporting 3 4 53 407
[   758.813] have a master to look out for
[   758.830] need to create shared pixmap 1(II) modesetting(G0): EDID vendor "CMN", prod id 5238
[   758.990] (II) modesetting(G0): Printing DDC gathered Modelines:
[   758.991] (II) modesetting(G0): Modeline "1366x768"x0.0   76.66  1366 1399 1467 1579  768 772 785 809 +hsync -vsync (48.5 kHz eP)
[   758.991] (II) modesetting(G0): Modeline "1366x768"x0.0   51.11  1366 1399 1467 1579  768 772 785 809 +hsync -vsync (32.4 kHz e)
[   759.188] reporting 3 4 53 407
[   759.191] (II) modesetting(G0): EDID vendor "CMN", prod id 5238
[   759.191] (II) modesetting(G0): Printing DDC gathered Modelines:
[   759.191] (II) modesetting(G0): Modeline "1366x768"x0.0   76.66  1366 1399 1467 1579  768 772 785 809 +hsync -vsync (48.5 kHz eP)
[   759.191] (II) modesetting(G0): Modeline "1366x768"x0.0   51.11  1366 1399 1467 1579  768 772 785 809 +hsync -vsync (32.4 kHz e)
[   759.388] reporting 3 4 53 407
[   759.390] have a master to look out for
[   759.766] need to create shared pixmap 1(II) modesetting(G0): EDID vendor "CMN", prod id 5238
[   759.785] (II) modesetting(G0): Printing DDC gathered Modelines:
[   759.785] (II) modesetting(G0): Modeline "1366x768"x0.0   76.66  1366 1399 1467 1579  768 772 785 809 +hsync -vsync (48.5 kHz eP)
[   759.785] (II) modesetting(G0): Modeline "1366x768"x0.0   51.11  1366 1399 1467 1579  768 772 785 809 +hsync -vsync (32.4 kHz e)
[   759.984] reporting 3 4 53 407
[   760.006] have a master to look out for
[   760.006] adjust shatters 0 1366
[   760.008] need to create shared pixmap 1(II) XKB: reuse xkmfile /var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm
[   760.965] reporting 3 4 53 407
[   763.827] reporting 3 4 53 407
[   777.041] (II) modesetting(G0): EDID vendor "CMN", prod id 5238
[   777.041] (II) modesetting(G0): Printing DDC gathered Modelines:
[   777.041] (II) modesetting(G0): Modeline "1366x768"x0.0   76.66  1366 1399 1467 1579  768 772 785 809 +hsync -vsync (48.5 kHz eP)
[   777.041] (II) modesetting(G0): Modeline "1366x768"x0.0   51.11  1366 1399 1467 1579  768 772 785 809 +hsync -vsync (32.4 kHz e)
[   777.236] reporting 3 4 53 407
[   777.241] (II) modesetting(G0): EDID vendor "CMN", prod id 5238
[   777.241] (II) modesetting(G0): Printing DDC gathered Modelines:
[   777.241] (II) modesetting(G0): Modeline "1366x768"x0.0   76.66  1366 1399 1467 1579  768 772 785 809 +hsync -vsync (48.5 kHz eP)
[   777.241] (II) modesetting(G0): Modeline "1366x768"x0.0   51.11  1366 1399 1467 1579  768 772 785 809 +hsync -vsync (32.4 kHz e)
[   777.440] reporting 3 4 53 407
[   777.446] (II) modesetting(G0): EDID vendor "CMN", prod id 5238
[   777.446] (II) modesetting(G0): Printing DDC gathered Modelines:
[   777.446] (II) modesetting(G0): Modeline "1366x768"x0.0   76.66  1366 1399 1467 1579  768 772 785 809 +hsync -vsync (48.5 kHz eP)
[   777.446] (II) modesetting(G0): Modeline "1366x768"x0.0   51.11  1366 1399 1467 1579  768 772 785 809 +hsync -vsync (32.4 kHz e)
[   777.644] reporting 3 4 53 407
[   777.671] have a master to look out for
[   777.671] adjust shatters 0 1920
[   777.673] need to create shared pixmap 1(II) modesetting(G0): EDID vendor "CMN", prod id 5238
[   777.835] (II) modesetting(G0): Printing DDC gathered Modelines:
[   777.835] (II) modesetting(G0): Modeline "1366x768"x0.0   76.66  1366 1399 1467 1579  768 772 785 809 +hsync -vsync (48.5 kHz eP)
[   777.835] (II) modesetting(G0): Modeline "1366x768"x0.0   51.11  1366 1399 1467 1579  768 772 785 809 +hsync -vsync (32.4 kHz e)
[   777.948] reporting 3 4 32 232
[   777.980] reporting 3 4 30 218
[   777.981] have a master to look out for
[   777.981] adjust shatters 0 1920
[   778.374] need to create shared pixmap 1(II) modesetting(G0): EDID vendor "CMN", prod id 5238
[   778.392] (II) modesetting(G0): Printing DDC gathered Modelines:
[   778.392] (II) modesetting(G0): Modeline "1366x768"x0.0   76.66  1366 1399 1467 1579  768 772 785 809 +hsync -vsync (48.5 kHz eP)
[   778.392] (II) modesetting(G0): Modeline "1366x768"x0.0   51.11  1366 1399 1467 1579  768 772 785 809 +hsync -vsync (32.4 kHz e)
[   778.424] reporting 3 4 30 218
[   778.425] have a master to look out for
[   778.425] adjust shatters 0 1920
[   778.426] need to create shared pixmap 1reporting 3 4 30 218
[   778.989] reporting 3 4 30 218
[   779.134] (II) XKB: reuse xkmfile /var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm
[   779.228] reporting 3 4 30 218
[   779.292] reporting 3 4 30 218
[   779.316] (II) modesetting(G0): EDID vendor "CMN", prod id 5238
[   779.316] (II) modesetting(G0): Printing DDC gathered Modelines:
[   779.316] (II) modesetting(G0): Modeline "1366x768"x0.0   76.66  1366 1399 1467 1579  768 772 785 809 +hsync -vsync (48.5 kHz eP)
[   779.316] (II) modesetting(G0): Modeline "1366x768"x0.0   51.11  1366 1399 1467 1579  768 772 785 809 +hsync -vsync (32.4 kHz e)
[   779.348] reporting 3 4 30 218
[   779.689] reporting 3 4 30 218
[   779.719] (II) modesetting(G0): EDID vendor "CMN", prod id 5238
[   779.719] (II) modesetting(G0): Printing DDC gathered Modelines:
[   779.719] (II) modesetting(G0): Modeline "1366x768"x0.0   76.66  1366 1399 1467 1579  768 772 785 809 +hsync -vsync (48.5 kHz eP)
[   779.719] (II) modesetting(G0): Modeline "1366x768"x0.0   51.11  1366 1399 1467 1579  768 772 785 809 +hsync -vsync (32.4 kHz e)
[   779.752] reporting 3 4 30 218
[   779.806] reporting 3 4 30 218
[   779.849] (II) modesetting(G0): EDID vendor "CMN", prod id 5238
[   779.849] (II) modesetting(G0): Printing DDC gathered Modelines:
[   779.849] (II) modesetting(G0): Modeline "1366x768"x0.0   76.66  1366 1399 1467 1579  768 772 785 809 +hsync -vsync (48.5 kHz eP)
[   779.849] (II) modesetting(G0): Modeline "1366x768"x0.0   51.11  1366 1399 1467 1579  768 772 785 809 +hsync -vsync (32.4 kHz e)
[   780.140] reporting 3 4 53 407
[   780.140] reporting 3 4 53 407
[   780.140] reporting 3 4 53 407
[   780.145] have a master to look out for
[   780.222] need to create shared pixmap 1have a master to look out for
[   780.252] adjust shatters 0 1920
[   780.641] need to create shared pixmap 1reporting 3 4 53 407
[   780.799] reporting 3 4 53 407
[   780.800] reporting 3 4 53 407
[   780.801] reporting 3 4 53 407
[   780.802] reporting 3 4 53 407
[   780.802] reporting 3 4 53 407
[   780.803] reporting 3 4 53 407
[   780.805] reporting 3 4 53 407
[   780.808] reporting 3 4 53 407
[   780.809] reporting 3 4 53 407
[   780.815] reporting 3 4 53 407
[   780.816] reporting 3 4 53 407
[   780.816] reporting 3 4 53 407
[   780.820] reporting 3 4 53 407
[   780.821] reporting 3 4 53 407
[   780.823] reporting 3 4 53 407
[   780.824] reporting 3 4 53 407
[   780.915] reporting 3 4 53 407
[   780.916] reporting 3 4 53 407
[   780.931] (II) XKB: reuse xkmfile /var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm
[   780.933] reporting 3 4 53 407
[   780.935] reporting 3 4 53 407
[   780.937] reporting 3 4 53 407
[   780.938] (II) XKB: reuse xkmfile /var/lib/xkb/server-3A5E4D0B17D08159967E7ED762B8B99673C83963.xkm
[   780.944] reporting 3 4 53 407
[   781.921] (II) modesetting(G0): EDID vendor "CMN", prod id 5238
[   781.921] (II) modesetting(G0): Printing DDC gathered Modelines:
[   781.921] (II) modesetting(G0): Modeline "1366x768"x0.0   76.66  1366 1399 1467 1579  768 772 785 809 +hsync -vsync (48.5 kHz eP)
[   781.921] (II) modesetting(G0): Modeline "1366x768"x0.0   51.11  1366 1399 1467 1579  768 772 785 809 +hsync -vsync (32.4 kHz e)
[   782.112] reporting 3 4 53 407
[   782.641] (II) modesetting(G0): EDID vendor "GSM", prod id 22256
[   782.642] (II) modesetting(G0): Using hsync ranges from config file
[   782.642] (II) modesetting(G0): Using vrefresh ranges from config file
[   782.642] (II) modesetting(G0): Printing DDC gathered Modelines:
[   782.642] (II) modesetting(G0): Modeline "1920x1080"x0.0  138.50  1920 1968 2000 2080  1080 1083 1088 1111 +hsync +vsync (66.6 kHz eP)
[   782.642] (II) modesetting(G0): Modeline "1920x1080"x0.0  148.50  1920 2003 2047 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz e)
[   782.642] (II) modesetting(G0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz e)
[   782.642] (II) modesetting(G0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[   782.642] (II) modesetting(G0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[   782.642] (II) modesetting(G0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[   782.642] (II) modesetting(G0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   782.642] (II) modesetting(G0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[   782.642] (II) modesetting(G0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   782.642] (II) modesetting(G0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   782.642] (II) modesetting(G0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   782.642] (II) modesetting(G0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   782.642] (II) modesetting(G0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   782.642] (II) modesetting(G0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   782.642] (II) modesetting(G0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[   782.642] (II) modesetting(G0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   782.642] (II) modesetting(G0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   782.642] (II) modesetting(G0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[   782.642] (II) modesetting(G0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   782.642] (II) modesetting(G0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[   782.642] (II) modesetting(G0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[   782.642] (II) modesetting(G0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[   782.642] (II) modesetting(G0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[   782.642] (II) modesetting(G0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[   782.642] (II) modesetting(G0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz e)
[   782.692] reporting 3 4 53 407
[   782.692] reporting 3 4 53 407
[   782.780] reporting 3 4 53 407
[   782.781] reporting 3 4 53 407
[   782.784] reporting 3 4 53 407
[   782.784] reporting 3 4 53 407
[   782.788] reporting 3 4 53 407
[   782.794] reporting 3 4 53 407
[   782.798] reporting 3 4 53 407
[   782.804] reporting 3 4 53 407
[   782.817] (II) XKB: reuse xkmfile /var/lib/xkb/server-E4CA34EE8D7EEBABB4AC7495D24F69EE8D968251.xkm
[   782.824] (II) XKB: reuse xkmfile /var/lib/xkb/server-E4CA34EE8D7EEBABB4AC7495D24F69EE8D968251.xkm
[   782.826] (II) XKB: reuse xkmfile /var/lib/xkb/server-E4CA34EE8D7EEBABB4AC7495D24F69EE8D968251.xkm
[   782.828] (II) XKB: reuse xkmfile /var/lib/xkb/server-E4CA34EE8D7EEBABB4AC7495D24F69EE8D968251.xkm
[   782.830] (II) XKB: reuse xkmfile /var/lib/xkb/server-E4CA34EE8D7EEBABB4AC7495D24F69EE8D968251.xkm
[   782.832] (II) XKB: reuse xkmfile /var/lib/xkb/server-E4CA34EE8D7EEBABB4AC7495D24F69EE8D968251.xkm
[   782.834] (II) XKB: reuse xkmfile /var/lib/xkb/server-E4CA34EE8D7EEBABB4AC7495D24F69EE8D968251.xkm
[   782.836] (II) XKB: reuse xkmfile /var/lib/xkb/server-E4CA34EE8D7EEBABB4AC7495D24F69EE8D968251.xkm
[   782.838] (II) XKB: reuse xkmfile /var/lib/xkb/server-E4CA34EE8D7EEBABB4AC7495D24F69EE8D968251.xkm
[   782.840] (II) XKB: reuse xkmfile /var/lib/xkb/server-E4CA34EE8D7EEBABB4AC7495D24F69EE8D968251.xkm
[   782.842] (II) XKB: reuse xkmfile /var/lib/xkb/server-E4CA34EE8D7EEBABB4AC7495D24F69EE8D968251.xkm
[   782.844] (II) XKB: reuse xkmfile /var/lib/xkb/server-E4CA34EE8D7EEBABB4AC7495D24F69EE8D968251.xkm
[   787.469] reporting 3 4 53 407
[   787.639] reporting 3 4 53 407
[   790.225] (II) XKB: reuse xkmfile /var/lib/xkb/server-E4CA34EE8D7EEBABB4AC7495D24F69EE8D968251.xkm
[   796.663] reporting 3 4 53 407
[   801.668] reporting 3 4 53 407
[   801.855] (II) modesetting(G0): EDID vendor "GSM", prod id 22256
[   801.856] (II) modesetting(G0): Using hsync ranges from config file
[   801.856] (II) modesetting(G0): Using vrefresh ranges from config file
[   801.856] (II) modesetting(G0): Printing DDC gathered Modelines:
[   801.856] (II) modesetting(G0): Modeline "1920x1080"x0.0  138.50  1920 1968 2000 2080  1080 1083 1088 1111 +hsync +vsync (66.6 kHz eP)
[   801.856] (II) modesetting(G0): Modeline "1920x1080"x0.0  148.50  1920 2003 2047 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz e)
[   801.856] (II) modesetting(G0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz e)
[   801.856] (II) modesetting(G0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[   801.856] (II) modesetting(G0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[   801.856] (II) modesetting(G0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[   801.856] (II) modesetting(G0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   801.856] (II) modesetting(G0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[   801.856] (II) modesetting(G0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   801.856] (II) modesetting(G0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   801.856] (II) modesetting(G0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   801.856] (II) modesetting(G0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   801.856] (II) modesetting(G0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   801.856] (II) modesetting(G0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   801.856] (II) modesetting(G0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[   801.856] (II) modesetting(G0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   801.856] (II) modesetting(G0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   801.856] (II) modesetting(G0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[   801.856] (II) modesetting(G0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   801.856] (II) modesetting(G0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[   801.856] (II) modesetting(G0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[   801.856] (II) modesetting(G0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[   801.856] (II) modesetting(G0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[   801.856] (II) modesetting(G0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[   801.856] (II) modesetting(G0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz e)
[   801.904] reporting 3 4 53 407
[   801.905] reporting 3 4 53 407
[   851.311] reporting 3 4 53 407
[   859.631] reporting 3 4 53 407
[   881.582] reporting 3 4 53 407
[   916.529] reporting 3 4 53 407
```

/var/log/gpu-manager.log
```
log_file: /var/log/gpu-manager.loglast_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
Found "/dev/dri/card0", driven by "i915"
output 0:
	LVDS connector
output 1:
	HDMIA connector
Number of connected outputs for /dev/dri/card0: 2
Does it require offloading? yes
grep dmesg status 0
dmesg status 0 == 0? Yes
grep dmesg status 256
dmesg status 256 == 0? No
Is nvidia loaded? yes
Was nvidia unloaded? yes
Is fglrx loaded? no
Was fglrx unloaded? no
Is intel loaded? yes
Is radeon loaded? no
Is nouveau loaded? no
Vendor/Device Id: 8086:166
BusID "PCI:0@0:2:0"
Is boot vga? yes
Vendor/Device Id: 10de:fe1
BusID "PCI:2@0:0:0"
Is boot vga? no
last cards number = 2
Has amd? no
Has intel? yes
Has nvidia? yes
How many cards? 2
Has the system changed? No
main_arch_path x86_64-linux-gnu, other_arch_path i386-linux-gnu
Current alternative: /usr/lib/nvidia-331/ld.so.conf
Is nvidia enabled? yes
Is fglrx enabled? no
Is mesa enabled? no
Is pxpress enabled? no
Is prime enabled? no
Is nvidia available? yes
Is fglrx available? no
Is mesa available? yes
Is pxpress available? no
Is prime available? yes
Intel IGP detected
Intel hybrid system
intel_matches: 1, nvidia_matches: 1, intel_set: 1, nvidia_set: 1 x_options_matches: 3
No need to modify xorg.conf. Path: /etc/X11/xorg.conf
No need to change the current bbswitch status
```

Please, help.

---

### Post by mastablasta on 2015-03-24
at least you get a display :)  mine  (GT 730) is not even optimus and all I get is blank screen.
anyway try with newer driver 340 or 346 (the beta) - xorg edgers PPA has it. just add the ppa and then install nvidia-340 or nvidia-346

---

### Post by Novitk on 2015-03-24
The problem is in the file [B]~/.config/monitors.xml

[/B]After renaming "monitors.xml" to "monitors.xml.bk" and restarting the system with NVIDIA card selected, everything was perfectly fine. But I guess this file was created again (I don't know) because when I restarted, everything was messed up again and I wasn't able to switch between displays (notebook display and monitor display). Why am I having problems with this file and how could I solve it?

---

### Post by Novitk on 2015-03-26
Up... I find the file that's causing the problem, but I have no idea how to solve this :/

---

### Post by Novitk on 2015-03-29
So sad, I can't fix my problem.

---

