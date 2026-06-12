---
title: "Nvidia fail"
date: 2016-07-24
forum: Hardware
---

### Post by Alex36 on 2016-07-24
I'm having trouble getting Nvidia drivers to work right. I can log on to the desktop and browse around, but UHD videos and games run very choppy (I'm testing with a UHD smaple video and 'Talos Principle" via Steam).

Current specs:
Skylake Intel i7-6500U CPU @ 2.50GHz × 4 
GeForce GTX 965M/PCIe/SSE2
16Gb RAM
Graphics-PPA
Nvidia 367.35

Problem:
1 - low FPS/choppy video
2 - wrong desktop scaling on laptop screen


This used to work well:
```
apt-get install nvidia-364
reboot
apt-get install nvidia-352 nvidia-settings
```

---

### Post by Alex36 on 2016-07-25
(yes, I had to install 352 on top of 364, otherwise it didn't work). This got me 40-50fps at QHD resolution back in May.
Now my framerate is 5-10fps, I've tried

```
apt-get purge nvidia*
apt-get install nvidia-364
reboot
apt-get install nvidia-352 nvidia-settings
```

With still 5-10fps.

I've tried:
regular ubuntu-drivers source (kernal panic/crash when booting)
all sorts of nvidia-3XX drivers with no improvement
Nouveau drivers work but are slower, and have trouble with HDMI output, so I would like Nvidia.


What's peculiar is that when I've uninstall virtualbox and rebooted, it was working great (60+fps), but when I rebooted once more it went back to 10fps.
I also tried booting to command line (systemd/unit=multi-user.target; then systemctl isolate graphical.target) - I got >100fps; I quite the game and went back in at it was ~60, and then later ~10fps. I rebooted and did the same commands and from the get-go it was 10fps.


I'm at a loss on how to continue.


Thanks!
Alex

See below for logs:

---

### Post by Alex36 on 2016-07-25
```
 sudo lshw -c video
  *-display               
       description: VGA compatible controller
       product: Sky Lake Integrated Graphics
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915_bpo latency=0
       resources: irq:276 memory:db000000-dbffffff memory:70000000-7fffffff ioport:f000(size=64)
  *-display
       description: 3D controller
       product: GM206M [GeForce GTX 965M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:288 memory:dc000000-dcffffff memory:b0000000-bfffffff memory:c0000000-c1ffffff ioport:e000(size=128) memory:dd000000-dd07ffff

```

```

lsmod |grep nvidia
nvidia_uvm            659456  0
nvidia_drm             45056  1
nvidia_modeset        765952  8 nvidia_drm
drm_kms_helper        147456  2 i915_bpo,nvidia_drm
nvidia              11247616  133 nvidia_modeset,nvidia_uvm
drm                   360448  12 i915_bpo,drm_kms_helper,nvidia_drm
```


```
X.Org X Server 1.18.3
Release Date: 2016-04-04
[     4.055] X Protocol Version 11, Revision 0
[     4.055] Build Operating System: Linux 3.13.0-86-generic x86_64 Ubuntu
[     4.055] Current Operating System: Linux AG-AW13 4.4.0-31-generic #50-Ubuntu SMP Wed Jul 13 00:07:12 UTC 2016 x86_64
[     4.056] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-31-generic root=UUID=6295439d-69f1-42e2-9434-5bd6f7876453 ro quiet splash vt.handoff=7
[     4.056] Build Date: 18 May 2016  01:07:07AM
[     4.056] xorg-server 2:1.18.3-1ubuntu2.2 (For technical support please see http://www.ubuntu.com/support) 
[     4.056] Current version of pixman: 0.33.6
[     4.056] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[     4.056] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     4.056] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Jul 24 19:27:52 2016
[     4.057] (==) Using config file: "/etc/X11/xorg.conf"
[     4.057] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     4.057] (==) ServerLayout "layout"
[     4.057] (**) |-->Screen "nvidia" (0)
[     4.057] (**) |   |-->Monitor "<default monitor>"
[     4.058] (**) |   |-->Device "nvidia"
[     4.058] (**) |   |-->GPUDevice "nvidia"
[     4.058] (==) No monitor specified for screen "nvidia".
	Using a default monitor configuration.
[     4.058] (**) |-->Inactive Device "intel"
[     4.058] (==) Automatically adding devices
[     4.058] (==) Automatically enabling devices
[     4.058] (==) Automatically adding GPU devices
[     4.058] (==) Max clients allowed: 256, resource mask: 0x1fffff
[     4.058] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     4.058] 	Entry deleted from font path.
[     4.058] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     4.058] 	Entry deleted from font path.
[     4.058] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     4.058] 	Entry deleted from font path.
[     4.058] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     4.058] 	Entry deleted from font path.
[     4.058] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     4.058] 	Entry deleted from font path.
[     4.058] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[     4.058] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     4.058] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[     4.058] (II) Loader magic: 0x55d2ee875da0
[     4.058] (II) Module ABI versions:
[     4.058] 	X.Org ANSI C Emulation: 0.4
[     4.058] 	X.Org Video Driver: 20.0
[     4.058] 	X.Org XInput driver : 22.1
[     4.058] 	X.Org Server Extension : 9.0
[     4.059] (++) using VT number 7

[     4.059] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
[     4.059] (II) xfree86: Adding drm device (/dev/dri/card1)
[     4.060] (II) xfree86: Adding drm device (/dev/dri/card0)
[     4.062] (--) PCI:*(0:0:2:0) 8086:1916:1028:0707 rev 7, Mem @ 0xdb000000/16777216, 0x70000000/268435456, I/O @ 0x0000f000/64
[     4.063] (--) PCI: (0:1:0:0) 10de:1427:1028:0707 rev 161, Mem @ 0xdc000000/16777216, 0xb0000000/268435456, 0xc0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[     4.063] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[     4.063] (II) "glx" will be loaded by default.
[     4.063] (II) LoadModule: "glx"
[     4.063] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[     4.117] (II) Module glx: vendor="NVIDIA Corporation"
[     4.117] 	compiled for 4.0.2, module version = 1.0.0
[     4.117] 	Module class: X.Org Server Extension
[     4.117] (II) NVIDIA GLX Module  367.35  Mon Jul 11 22:39:07 PDT 2016
[     4.117] (II) LoadModule: "nvidia"
[     4.117] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[     4.123] (II) Module nvidia: vendor="NVIDIA Corporation"
[     4.123] 	compiled for 4.0.2, module version = 1.0.0
[     4.123] 	Module class: X.Org Video Driver
[     4.123] (II) LoadModule: "modesetting"
[     4.123] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[     4.124] (II) Module modesetting: vendor="X.Org Foundation"
[     4.124] 	compiled for 1.18.3, module version = 1.18.3
[     4.124] 	Module class: X.Org Video Driver
[     4.124] 	ABI class: X.Org Video Driver, version 20.0
[     4.124] (II) NVIDIA dlloader X Driver  367.35  Mon Jul 11 22:14:48 PDT 2016
[     4.124] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[     4.125] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[     4.126] (II) Loading sub module "fb"
[     4.126] (II) LoadModule: "fb"
[     4.126] (II) Loading /usr/lib/xorg/modules/libfb.so
[     4.126] (II) Module fb: vendor="X.Org Foundation"
[     4.126] 	compiled for 1.18.3, module version = 1.0.0
[     4.126] 	ABI class: X.Org ANSI C Emulation, version 0.4
[     4.126] (II) Loading sub module "wfb"
[     4.126] (II) LoadModule: "wfb"
[     4.126] (II) Loading /usr/lib/xorg/modules/libwfb.so
[     4.128] (II) Module wfb: vendor="X.Org Foundation"
[     4.128] 	compiled for 1.18.3, module version = 1.0.0
[     4.128] 	ABI class: X.Org ANSI C Emulation, version 0.4
[     4.128] (II) Loading sub module "ramdac"
[     4.128] (II) LoadModule: "ramdac"
[     4.128] (II) Module "ramdac" already built-in
[     4.130] (II) modeset(G0): using drv /dev/dri/card1
[     4.131] (II) NVIDIA(0): Creating default Display subsection in Screen section
	"nvidia" for depth/fbbpp 24/32
[     4.131] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[     4.131] (==) NVIDIA(0): RGB weight 888
[     4.131] (==) NVIDIA(0): Default visual is TrueColor
[     4.131] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[     4.132] (**) NVIDIA(0): Option "ConstrainCursor" "off"
[     4.132] (**) NVIDIA(0): Option "AllowEmptyInitialConfiguration" "on"
[     4.132] (**) NVIDIA(0): Option "IgnoreDisplayDevices" "CRT"
[     4.132] (**) NVIDIA(0): Enabling 2D acceleration
[     4.447] (--) NVIDIA(0): Valid display device(s) on GPU-0 at PCI:1:0:0
[     4.447] (--) NVIDIA(0):     DFP-0
[     4.447] (--) NVIDIA(0): DFP-0: disconnected
[     4.447] (--) NVIDIA(0): DFP-0: Internal TMDS
[     4.447] (--) NVIDIA(0): DFP-0: 330.0 MHz maximum pixel clock
[     4.447] (--) NVIDIA(0): 
[     4.450] (II) NVIDIA(0): NVIDIA GPU GeForce GTX 965M (GM206-A) at PCI:1:0:0 (GPU-0)
[     4.450] (--) NVIDIA(0): Memory: 4194304 kBytes
[     4.450] (--) NVIDIA(0): VideoBIOS: 84.06.54.00.0a
[     4.450] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[     4.450] (==) NVIDIA(0): 
[     4.450] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[     4.450] (==) NVIDIA(0):     will be used as the requested mode.
[     4.450] (==) NVIDIA(0): 
[     4.450] (--) NVIDIA(0): No enabled display devices found; starting anyway because
[     4.450] (--) NVIDIA(0):     AllowEmptyInitialConfiguration is enabled
[     4.450] (II) NVIDIA(0): Validated MetaModes:
[     4.450] (II) NVIDIA(0):     "NULL"
[     4.450] (II) NVIDIA(0): Virtual screen size determined to be 640 x 480
[     4.453] (WW) NVIDIA(0): Unable to get display device for DPI computation.
[     4.453] (==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
[     4.454] (==) modeset(G0): Depth 24, (==) framebuffer bpp 32
[     4.454] (**) modeset(G0): Option "AccelMethod" "None"
[     4.454] (==) modeset(G0): RGB weight 888
[     4.454] (==) modeset(G0): Default visual is TrueColor
[     4.454] (**) modeset(G0): glamor disabled
[     4.454] (II) modeset(G0): ShadowFB: preferred YES, enabled YES
[     4.454] (II) modeset(G0): Output eDP-1 has no monitor section
[     4.456] (II) modeset(G0): Output DP-1 has no monitor section
[     4.584] (II) modeset(G0): Output HDMI-1 has no monitor section
[     4.586] (II) modeset(G0): Output DP-2 has no monitor section
[     4.712] (II) modeset(G0): Output HDMI-2 has no monitor section
[     4.712] (II) modeset(G0): EDID for output eDP-1
[     4.712] (II) modeset(G0): Manufacturer: SHP  Model: 1421  Serial#: 0
[     4.712] (II) modeset(G0): Year: 2014  Week: 50
[     4.712] (II) modeset(G0): EDID Version: 1.4
[     4.712] (II) modeset(G0): Digital Display Input
[     4.712] (II) modeset(G0): 8 bits per channel
[     4.712] (II) modeset(G0): Digital interface is DisplayPort
[     4.712] (II) modeset(G0): Max Image Size [cm]: horiz.: 29  vert.: 17
[     4.712] (II) modeset(G0): Gamma: 2.20
[     4.712] (II) modeset(G0): No DPMS capabilities specified
[     4.712] (II) modeset(G0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[     4.712] (II) modeset(G0): Default color space is primary color space
[     4.712] (II) modeset(G0): First detailed timing is preferred mode
[     4.712] (II) modeset(G0): Preferred mode is native pixel format and refresh rate
[     4.712] (II) modeset(G0): redX: 0.640 redY: 0.329   greenX: 0.300 greenY: 0.600
[     4.712] (II) modeset(G0): blueX: 0.149 blueY: 0.060   whiteX: 0.312 whiteY: 0.328
[     4.712] (II) modeset(G0): Manufacturer's mask: 0
[     4.712] (II) modeset(G0): Supported detailed timing:
[     4.712] (II) modeset(G0): clock: 373.2 MHz   Image Size:  294 x 165 mm
[     4.712] (II) modeset(G0): h_active: 3200  h_sync: 3248  h_sync_end 3280 h_blank_end 3360 h_border: 0
[     4.712] (II) modeset(G0): v_active: 1800  v_sync: 1803  v_sync_end 1808 v_blanking: 1852 v_border: 0

[     4.712] (II) modeset(G0): Unknown vendor-specific block 0
[     4.712] (II) modeset(G0): EDID (in hex):
[     4.712] (II) modeset(G0): 	00ffffffffffff004d10211400000000
[     4.712] (II) modeset(G0): 	32180104a51d11780ede50a3544c9926
[     4.712] (II) modeset(G0): 	0f505400000001010101010101010101
[     4.712] (II) modeset(G0): 	010101010101cd9180a0c00834703020
[     4.712] (II) modeset(G0): 	350026a5100000180000001000000000
[     4.712] (II) modeset(G0): 	00000000000000000000000000fe0030
[     4.712] (II) modeset(G0): 	35503748854c513133335a3100000000
[     4.712] (II) modeset(G0): 	0002410328001200000b010a2020001b
[     4.712] (II) modeset(G0): Printing probed modes for output eDP-1
[     4.712] (II) modeset(G0): Modeline "3200x1800"x60.0  373.25  3200 3248 3280 3360  1800 1803 1808 1852 -hsync -vsync (111.1 kHz eP)
[     4.712] (II) modeset(G0): Modeline "2048x1536"x60.0  266.95  2048 2200 2424 2800  1536 1537 1540 1589 -hsync +vsync (95.3 kHz d)
[     4.712] (II) modeset(G0): Modeline "1920x1440"x60.0  234.00  1920 2048 2256 2600  1440 1441 1444 1500 -hsync +vsync (90.0 kHz d)
[     4.712] (II) modeset(G0): Modeline "1856x1392"x60.0  218.30  1856 1952 2176 2528  1392 1393 1396 1439 -hsync +vsync (86.4 kHz d)
[     4.712] (II) modeset(G0): Modeline "1792x1344"x60.0  204.80  1792 1920 2120 2448  1344 1345 1348 1394 -hsync +vsync (83.7 kHz d)
[     4.712] (II) modeset(G0): Modeline "1920x1200"x60.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz d)
[     4.712] (II) modeset(G0): Modeline "1920x1080"x59.9  138.50  1920 1968 2000 2080  1080 1083 1088 1111 +hsync -vsync (66.6 kHz d)
[     4.712] (II) modeset(G0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz d)
[     4.712] (II) modeset(G0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz d)
[     4.712] (II) modeset(G0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz d)
[     4.712] (II) modeset(G0): Modeline "1600x1024"x60.2  103.12  1600 1600 1656 1664  1024 1024 1029 1030 +hsync +vsync (62.0 kHz d)
[     4.712] (II) modeset(G0): Modeline "1400x1050"x60.0  122.00  1400 1488 1640 1880  1050 1052 1064 1082 +hsync +vsync (64.9 kHz d)
[     4.712] (II) modeset(G0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz d)
[     4.713] (II) modeset(G0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz d)
[     4.713] (II) modeset(G0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz d)
[     4.713] (II) modeset(G0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz d)
[     4.713] (II) modeset(G0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz d)
[     4.713] (II) modeset(G0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz d)
[     4.713] (II) modeset(G0): Modeline "1024x768"x120.1  133.47  1024 1100 1212 1400  768 768 770 794 doublescan -hsync +vsync (95.3 kHz d)
[     4.713] (II) modeset(G0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz d)
[     4.713] (II) modeset(G0): Modeline "960x720"x120.0  117.00  960 1024 1128 1300  720 720 722 750 doublescan -hsync +vsync (90.0 kHz d)
[     4.713] (II) modeset(G0): Modeline "928x696"x120.1  109.15  928 976 1088 1264  696 696 698 719 doublescan -hsync +vsync (86.4 kHz d)
[     4.713] (II) modeset(G0): Modeline "896x672"x120.0  102.40  896 960 1060 1224  672 672 674 697 doublescan -hsync +vsync (83.7 kHz d)
[     4.713] (II) modeset(G0): Modeline "960x600"x120.0   77.00  960 984 1000 1040  600 601 604 617 doublescan +hsync -vsync (74.0 kHz d)
[     4.713] (II) modeset(G0): Modeline "960x540"x120.0   69.25  960 984 1000 1040  540 541 544 555 doublescan +hsync -vsync (66.6 kHz d)
[     4.713] (II) modeset(G0): Modeline "800x600"x120.0   81.00  800 832 928 1080  600 600 602 625 doublescan +hsync +vsync (75.0 kHz d)
[     4.713] (II) modeset(G0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz d)
[     4.713] (II) modeset(G0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz d)
[     4.713] (II) modeset(G0): Modeline "840x525"x120.0   73.12  840 892 980 1120  525 526 529 544 doublescan -hsync +vsync (65.3 kHz d)
[     4.713] (II) modeset(G0): Modeline "840x525"x119.8   59.50  840 864 880 920  525 526 529 540 doublescan +hsync -vsync (64.7 kHz d)
[     4.713] (II) modeset(G0): Modeline "800x512"x120.3   51.56  800 800 828 832  512 512 514 515 doublescan +hsync +vsync (62.0 kHz d)
[     4.713] (II) modeset(G0): Modeline "700x525"x120.0   61.00  700 744 820 940  525 526 532 541 doublescan +hsync +vsync (64.9 kHz d)
[     4.713] (II) modeset(G0): Modeline "640x512"x120.0   54.00  640 664 720 844  512 512 514 533 doublescan +hsync +vsync (64.0 kHz d)
[     4.713] (II) modeset(G0): Modeline "720x450"x119.8   53.25  720 760 836 952  450 451 454 467 doublescan -hsync +vsync (55.9 kHz d)
[     4.713] (II) modeset(G0): Modeline "640x480"x120.0   54.00  640 688 744 900  480 480 482 500 doublescan +hsync +vsync (60.0 kHz d)
[     4.713] (II) modeset(G0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz d)
[     4.713] (II) modeset(G0): Modeline "680x384"x119.6   42.38  680 716 784 888  384 385 390 399 doublescan -hsync +vsync (47.7 kHz d)
[     4.713] (II) modeset(G0): Modeline "680x384"x119.9   36.00  680 704 720 760  384 385 390 395 doublescan +hsync -vsync (47.4 kHz d)
[     4.713] (II) modeset(G0): Modeline "576x432"x120.1   40.81  576 608 668 760  432 432 434 447 doublescan -hsync +vsync (53.7 kHz d)
[     4.713] (II) modeset(G0): Modeline "512x384"x120.0   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync (48.4 kHz d)
[     4.713] (II) modeset(G0): Modeline "400x300"x120.6   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz d)
[     4.713] (II) modeset(G0): Modeline "400x300"x112.7   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (35.2 kHz d)
[     4.713] (II) modeset(G0): Modeline "320x240"x120.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz d)
[     4.715] (II) modeset(G0): EDID for output DP-1
[     4.860] (II) modeset(G0): EDID for output HDMI-1
[     4.862] (II) modeset(G0): EDID for output DP-2
[     4.992] (II) modeset(G0): EDID for output HDMI-2
[     4.992] (II) modeset(G0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[     4.992] (==) modeset(G0): DPI set to (96, 96)
[     4.992] (II) Loading sub module "fb"
[     4.992] (II) LoadModule: "fb"
[     4.992] (II) Loading /usr/lib/xorg/modules/libfb.so
[     4.992] (II) Module fb: vendor="X.Org Foundation"
[     4.992] 	compiled for 1.18.3, module version = 1.0.0
[     4.992] 	ABI class: X.Org ANSI C Emulation, version 0.4
[     4.992] (II) Loading sub module "shadow"
[     4.992] (II) LoadModule: "shadow"
[     4.992] (II) Loading /usr/lib/xorg/modules/libshadow.so
[     4.996] (II) Module shadow: vendor="X.Org Foundation"
[     4.996] 	compiled for 1.18.3, module version = 1.1.0
[     4.996] 	ABI class: X.Org ANSI C Emulation, version 0.4
[     4.996] (--) Depth 24 pixmap format is 32 bpp
[     4.998] (==) modeset(G0): Backing store enabled
[     4.998] (==) modeset(G0): Silken mouse enabled
[     4.998] (II) modeset(G0): RandR 1.2 enabled, ignore the following RandR disabled message.
[     4.998] (==) modeset(G0): DPMS enabled
[     4.998] (WW) modeset(G0): Option "AllowEmptyInitialConfiguration" is not used
[     4.998] (WW) modeset(G0): Option "IgnoreDisplayDevices" is not used
[     5.267] (II) NVIDIA: Using 12288.00 MB of virtual memory for indirect memory
[     5.267] (II) NVIDIA:     access.
[     5.292] (II) NVIDIA(0): Built-in logo is bigger than the screen.
[     5.292] (II) NVIDIA(0): Setting mode "NULL"
[     5.305] (==) NVIDIA(0): Disabling shared memory pixmaps
[     5.305] (==) NVIDIA(0): Backing store enabled
[     5.306] (==) NVIDIA(0): Silken mouse enabled
[     5.306] (==) NVIDIA(0): DPMS enabled
[     5.306] (II) Loading sub module "dri2"
[     5.306] (II) LoadModule: "dri2"
[     5.306] (II) Module "dri2" already built-in
[     5.306] (II) NVIDIA(0): [DRI2] Setup complete
[     5.306] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[     5.306] (--) RandR disabled
[     5.309] (II) SELinux: Disabled on system
[     5.309] (II) Initializing extension GLX
[     5.309] (II) Indirect GLX disabled.
[     5.310] (II) modeset(G0): Damage tracking initialized
[     5.345] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[     5.345] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     5.345] (II) LoadModule: "evdev"
[     5.346] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     5.347] (II) Module evdev: vendor="X.Org Foundation"
[     5.347] 	compiled for 1.18.1, module version = 2.10.1
[     5.347] 	Module class: X.Org XInput Driver
[     5.347] 	ABI class: X.Org XInput driver, version 22.1
[     5.347] (II) Using input driver 'evdev' for 'Power Button'
[     5.347] (**) Power Button: always reports core events
[     5.347] (**) evdev: Power Button: Device: "/dev/input/event2"
[     5.347] (--) evdev: Power Button: Vendor 0 Product 0x1
[     5.347] (--) evdev: Power Button: Found keys
[     5.347] (II) evdev: Power Button: Configuring as keyboard
[     5.347] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[     5.347] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[     5.347] (**) Option "xkb_rules" "evdev"
[     5.347] (**) Option "xkb_model" "pc105"
[     5.347] (**) Option "xkb_layout" "us"
[     5.347] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[     5.347] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[     5.347] (II) Using input driver 'evdev' for 'Video Bus'
[     5.347] (**) Video Bus: always reports core events
[     5.347] (**) evdev: Video Bus: Device: "/dev/input/event4"
[     5.347] (--) evdev: Video Bus: Vendor 0 Product 0x6
[     5.347] (--) evdev: Video Bus: Found keys
[     5.348] (II) evdev: Video Bus: Configuring as keyboard
[     5.348] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input6/event4"
[     5.348] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[     5.348] (**) Option "xkb_rules" "evdev"
[     5.348] (**) Option "xkb_model" "pc105"
[     5.348] (**) Option "xkb_layout" "us"
[     5.348] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[     5.348] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[     5.348] (II) Using input driver 'evdev' for 'Video Bus'
[     5.348] (**) Video Bus: always reports core events
[     5.348] (**) evdev: Video Bus: Device: "/dev/input/event5"
[     5.348] (--) evdev: Video Bus: Vendor 0 Product 0x6
[     5.348] (--) evdev: Video Bus: Found keys
[     5.348] (II) evdev: Video Bus: Configuring as keyboard
[     5.348] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:22/LNXVIDEO:01/input/input7/event5"
[     5.348] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 8)
[     5.348] (**) Option "xkb_rules" "evdev"
[     5.348] (**) Option "xkb_model" "pc105"
[     5.348] (**) Option "xkb_layout" "us"
[     5.348] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[     5.348] (II) No input driver specified, ignoring this device.
[     5.348] (II) This device may have been added with another device file.
[     5.348] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[     5.348] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     5.348] (II) Using input driver 'evdev' for 'Power Button'
[     5.348] (**) Power Button: always reports core events
[     5.348] (**) evdev: Power Button: Device: "/dev/input/event1"
[     5.348] (--) evdev: Power Button: Vendor 0 Product 0x1
[     5.348] (--) evdev: Power Button: Found keys
[     5.348] (II) evdev: Power Button: Configuring as keyboard
[     5.348] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1/event1"
[     5.348] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 9)
[     5.348] (**) Option "xkb_rules" "evdev"
[     5.348] (**) Option "xkb_model" "pc105"
[     5.348] (**) Option "xkb_layout" "us"
[     5.349] (II) config/udev: Adding input device ELAN Touchscreen (/dev/input/event8)
[     5.349] (**) ELAN Touchscreen: Applying InputClass "evdev touchscreen catchall"
[     5.349] (II) Using input driver 'evdev' for 'ELAN Touchscreen'
[     5.349] (**) ELAN Touchscreen: always reports core events
[     5.349] (**) evdev: ELAN Touchscreen: Device: "/dev/input/event8"
[     5.349] (--) evdev: ELAN Touchscreen: Vendor 0x4f3 Product 0x441
[     5.349] (--) evdev: ELAN Touchscreen: Found absolute axes
[     5.349] (--) evdev: ELAN Touchscreen: Found absolute multitouch axes
[     5.349] (II) evdev: ELAN Touchscreen: No buttons found, faking one.
[     5.349] (--) evdev: ELAN Touchscreen: Found x and y absolute axes
[     5.349] (--) evdev: ELAN Touchscreen: Found absolute touchscreen
[     5.349] (II) evdev: ELAN Touchscreen: Configuring as touchscreen
[     5.349] (**) evdev: ELAN Touchscreen: YAxisMapping: buttons 4 and 5
[     5.349] (**) evdev: ELAN Touchscreen: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     5.349] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-5/1-5:1.0/0003:04F3:0441.0001/input/input9/event8"
[     5.349] (II) XINPUT: Adding extended input device "ELAN Touchscreen" (type: TOUCHSCREEN, id 10)
[     5.349] (II) evdev: ELAN Touchscreen: initialized for absolute axes.
[     5.349] (**) ELAN Touchscreen: (accel) keeping acceleration scheme 1
[     5.349] (**) ELAN Touchscreen: (accel) acceleration profile 0
[     5.349] (**) ELAN Touchscreen: (accel) acceleration factor: 2.000
[     5.349] (**) ELAN Touchscreen: (accel) acceleration threshold: 4
[     5.349] (II) config/udev: Adding input device ELAN Touchscreen (/dev/input/mouse1)
[     5.349] (II) No input driver specified, ignoring this device.
[     5.350] (II) This device may have been added with another device file.
[     5.350] (II) config/udev: Adding input device Integrated_Webcam_FHD (/dev/input/event9)
[     5.350] (**) Integrated_Webcam_FHD: Applying InputClass "evdev keyboard catchall"
[     5.350] (II) Using input driver 'evdev' for 'Integrated_Webcam_FHD'
[     5.350] (**) Integrated_Webcam_FHD: always reports core events
[     5.350] (**) evdev: Integrated_Webcam_FHD: Device: "/dev/input/event9"
[     5.350] (--) evdev: Integrated_Webcam_FHD: Vendor 0xc45 Product 0x6708
[     5.350] (--) evdev: Integrated_Webcam_FHD: Found keys
[     5.350] (II) evdev: Integrated_Webcam_FHD: Configuring as keyboard
[     5.350] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-6/1-6:1.0/input/input11/event9"
[     5.350] (II) XINPUT: Adding extended input device "Integrated_Webcam_FHD" (type: KEYBOARD, id 11)
[     5.350] (**) Option "xkb_rules" "evdev"
[     5.350] (**) Option "xkb_model" "pc105"
[     5.350] (**) Option "xkb_layout" "us"
[     5.350] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event10)
[     5.350] (II) No input driver specified, ignoring this device.
[     5.350] (II) This device may have been added with another device file.
[     5.350] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event11)
[     5.350] (II) No input driver specified, ignoring this device.
[     5.350] (II) This device may have been added with another device file.
[     5.350] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event12)
[     5.350] (II) No input driver specified, ignoring this device.
[     5.350] (II) This device may have been added with another device file.
[     5.351] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=7 (/dev/input/event13)
[     5.351] (II) No input driver specified, ignoring this device.
[     5.351] (II) This device may have been added with another device file.
[     5.351] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=8 (/dev/input/event14)
[     5.351] (II) No input driver specified, ignoring this device.
[     5.351] (II) This device may have been added with another device file.
[     5.351] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[     5.351] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[     5.351] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[     5.351] (**) AT Translated Set 2 keyboard: always reports core events
[     5.351] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[     5.351] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[     5.351] (--) evdev: AT Translated Set 2 keyboard: Found keys
[     5.351] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[     5.351] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[     5.351] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 12)
[     5.351] (**) Option "xkb_rules" "evdev"
[     5.351] (**) Option "xkb_model" "pc105"
[     5.351] (**) Option "xkb_layout" "us"
[     5.351] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event6)
[     5.351] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[     5.351] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchscreen catchall"
[     5.351] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[     5.351] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[     5.351] (II) LoadModule: "synaptics"
[     5.351] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[     5.352] (II) Module synaptics: vendor="X.Org Foundation"
[     5.352] 	compiled for 1.18.1, module version = 1.8.2
[     5.352] 	Module class: X.Org XInput Driver
[     5.352] 	ABI class: X.Org XInput driver, version 22.1
[     5.352] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[     5.352] (**) SynPS/2 Synaptics TouchPad: always reports core events
[     5.352] (**) Option "Device" "/dev/input/event6"
[     5.416] (II) synaptics: SynPS/2 Synaptics TouchPad: found clickpad property
[     5.416] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1282 - 5656 (res 0)
[     5.416] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1160 - 4692 (res 0)
[     5.416] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[     5.416] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[     5.416] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left double triple
[     5.416] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[     5.416] (**) Option "SoftButtonAreas" "50% 0 82% 0 0 0 0 0"
[     5.416] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[     5.416] (**) SynPS/2 Synaptics TouchPad: always reports core events
[     5.448] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input5/event6"
[     5.448] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 13)
[     5.448] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[     5.448] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[     5.448] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.036
[     5.448] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[     5.448] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[     5.448] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[     5.448] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[     5.448] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[     5.448] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[     5.448] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[     5.449] (II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event7)
[     5.449] (**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[     5.449] (II) Using input driver 'evdev' for 'Dell WMI hotkeys'
[     5.449] (**) Dell WMI hotkeys: always reports core events
[     5.449] (**) evdev: Dell WMI hotkeys: Device: "/dev/input/event7"
[     5.449] (--) evdev: Dell WMI hotkeys: Vendor 0 Product 0
[     5.449] (--) evdev: Dell WMI hotkeys: Found keys
[     5.449] (II) evdev: Dell WMI hotkeys: Configuring as keyboard
[     5.449] (**) Option "config_info" "udev:/sys/devices/virtual/input/input8/event7"
[     5.449] (II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD, id 14)
[     5.449] (**) Option "xkb_rules" "evdev"
[     5.449] (**) Option "xkb_model" "pc105"
[     5.449] (**) Option "xkb_layout" "us"
[     5.456] (--) NVIDIA(GPU-0): DFP-0: disconnected
[     5.456] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[     5.456] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[     5.456] (--) NVIDIA(GPU-0): 
[     5.462] (--) NVIDIA(GPU-0): DFP-0: disconnected
[     5.462] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[     5.462] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[     5.462] (--) NVIDIA(GPU-0): 
[     5.462] (--) NVIDIA(GPU-0): DFP-0: disconnected
[     5.462] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[     5.462] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[     5.462] (--) NVIDIA(GPU-0): 
[     5.466] (--) NVIDIA(GPU-0): DFP-0: disconnected
[     5.466] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[     5.466] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[     5.466] (--) NVIDIA(GPU-0): 
[     6.042] (--) NVIDIA(GPU-0): DFP-0: disconnected
[     6.042] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[     6.042] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[     6.042] (--) NVIDIA(GPU-0): 
[     6.042] (--) NVIDIA(GPU-0): DFP-0: disconnected
[     6.042] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[     6.042] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[     6.042] (--) NVIDIA(GPU-0): 
[     6.043] (II) modeset(G0): EDID vendor "SHP", prod id 5153
[     6.043] (II) modeset(G0): Printing DDC gathered Modelines:
[     6.043] (II) modeset(G0): Modeline "3200x1800"x0.0  373.25  3200 3248 3280 3360  1800 1803 1808 1852 -hsync -vsync (111.1 kHz eP)
[    14.834] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    14.834] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[    14.834] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[    14.834] (--) NVIDIA(GPU-0): 
[    14.834] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    14.834] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[    14.834] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[    14.834] (--) NVIDIA(GPU-0): 
[    14.835] (II) modeset(G0): EDID vendor "SHP", prod id 5153
[    14.835] (II) modeset(G0): Printing DDC gathered Modelines:
[    14.835] (II) modeset(G0): Modeline "3200x1800"x0.0  373.25  3200 3248 3280 3360  1800 1803 1808 1852 -hsync -vsync (111.1 kHz eP)
[    15.123] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    15.124] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[    15.124] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[    15.124] (--) NVIDIA(GPU-0): 
[    15.714] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    15.714] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[    15.714] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[    15.714] (--) NVIDIA(GPU-0): 
[    15.714] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    15.714] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[    15.714] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[    15.714] (--) NVIDIA(GPU-0): 
[    15.716] (II) modeset(G0): EDID vendor "SHP", prod id 5153
[    15.716] (II) modeset(G0): Printing DDC gathered Modelines:
[    15.716] (II) modeset(G0): Modeline "3200x1800"x0.0  373.25  3200 3248 3280 3360  1800 1803 1808 1852 -hsync -vsync (111.1 kHz eP)
[    15.975] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    15.975] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[    15.975] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[    15.975] (--) NVIDIA(GPU-0): 
[    15.975] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    15.975] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[    15.975] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[    15.975] (--) NVIDIA(GPU-0): 
[    15.975] (II) modeset(G0): EDID vendor "SHP", prod id 5153
[    15.975] (II) modeset(G0): Printing DDC gathered Modelines:
[    15.975] (II) modeset(G0): Modeline "3200x1800"x0.0  373.25  3200 3248 3280 3360  1800 1803 1808 1852 -hsync -vsync (111.1 kHz eP)
[    16.232] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    16.232] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[    16.232] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[    16.232] (--) NVIDIA(GPU-0): 
[    16.232] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    16.232] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[    16.232] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[    16.232] (--) NVIDIA(GPU-0): 
[    16.233] (II) modeset(G0): EDID vendor "SHP", prod id 5153
[    16.233] (II) modeset(G0): Printing DDC gathered Modelines:
[    16.233] (II) modeset(G0): Modeline "3200x1800"x0.0  373.25  3200 3248 3280 3360  1800 1803 1808 1852 -hsync -vsync (111.1 kHz eP)
[    16.625] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    16.625] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[    16.625] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[    16.625] (--) NVIDIA(GPU-0): 
[    16.625] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    16.625] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[    16.625] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[    16.625] (--) NVIDIA(GPU-0): 
[    16.626] (II) modeset(G0): EDID vendor "SHP", prod id 5153
[    16.626] (II) modeset(G0): Printing DDC gathered Modelines:
[    16.626] (II) modeset(G0): Modeline "3200x1800"x0.0  373.25  3200 3248 3280 3360  1800 1803 1808 1852 -hsync -vsync (111.1 kHz eP)
[    16.924] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    16.924] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[    16.924] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[    16.924] (--) NVIDIA(GPU-0): 
[    16.924] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    16.924] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[    16.924] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[    16.924] (--) NVIDIA(GPU-0): 
[    16.928] (II) modeset(G0): EDID vendor "SHP", prod id 5153
[    16.928] (II) modeset(G0): Printing DDC gathered Modelines:
[    16.928] (II) modeset(G0): Modeline "3200x1800"x0.0  373.25  3200 3248 3280 3360  1800 1803 1808 1852 -hsync -vsync (111.1 kHz eP)
[    17.185] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    17.185] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[    17.185] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[    17.185] (--) NVIDIA(GPU-0): 
[    17.186] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    17.186] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[    17.186] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[    17.186] (--) NVIDIA(GPU-0): 
[    17.186] (II) modeset(G0): EDID vendor "SHP", prod id 5153
[    17.186] (II) modeset(G0): Printing DDC gathered Modelines:
[    17.186] (II) modeset(G0): Modeline "3200x1800"x0.0  373.25  3200 3248 3280 3360  1800 1803 1808 1852 -hsync -vsync (111.1 kHz eP)
[    17.443] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    17.443] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[    17.443] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[    17.443] (--) NVIDIA(GPU-0): 
[    17.443] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    17.443] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[    17.443] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[    17.443] (--) NVIDIA(GPU-0): 
[    17.444] (II) modeset(G0): EDID vendor "SHP", prod id 5153
[    17.444] (II) modeset(G0): Printing DDC gathered Modelines:
[    17.444] (II) modeset(G0): Modeline "3200x1800"x0.0  373.25  3200 3248 3280 3360  1800 1803 1808 1852 -hsync -vsync (111.1 kHz eP)
[    17.704] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    17.704] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[    17.704] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[    17.704] (--) NVIDIA(GPU-0): 
[    17.704] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    17.704] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[    17.704] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[    17.704] (--) NVIDIA(GPU-0): 
[    17.706] (II) modeset(G0): EDID vendor "SHP", prod id 5153
[    17.706] (II) modeset(G0): Printing DDC gathered Modelines:
[    17.706] (II) modeset(G0): Modeline "3200x1800"x0.0  373.25  3200 3248 3280 3360  1800 1803 1808 1852 -hsync -vsync (111.1 kHz eP)
[    17.961] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    17.961] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[    17.961] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[    17.961] (--) NVIDIA(GPU-0): 
[    17.961] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    17.961] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[    17.961] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[    17.961] (--) NVIDIA(GPU-0): 
[    17.961] (II) modeset(G0): EDID vendor "SHP", prod id 5153
[    17.961] (II) modeset(G0): Printing DDC gathered Modelines:
[    17.961] (II) modeset(G0): Modeline "3200x1800"x0.0  373.25  3200 3248 3280 3360  1800 1803 1808 1852 -hsync -vsync (111.1 kHz eP)
[    18.221] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    18.221] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[    18.221] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[    18.221] (--) NVIDIA(GPU-0): 
[    18.221] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    18.221] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[    18.221] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[    18.221] (--) NVIDIA(GPU-0): 
[    18.222] (II) modeset(G0): EDID vendor "SHP", prod id 5153
[    18.222] (II) modeset(G0): Printing DDC gathered Modelines:
[    18.222] (II) modeset(G0): Modeline "3200x1800"x0.0  373.25  3200 3248 3280 3360  1800 1803 1808 1852 -hsync -vsync (111.1 kHz eP)
[    18.481] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    18.481] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[    18.481] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[    18.481] (--) NVIDIA(GPU-0): 
[    18.481] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    18.481] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[    18.481] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[    18.481] (--) NVIDIA(GPU-0): 
[    18.482] (II) modeset(G0): EDID vendor "SHP", prod id 5153
[    18.482] (II) modeset(G0): Printing DDC gathered Modelines:
[    18.482] (II) modeset(G0): Modeline "3200x1800"x0.0  373.25  3200 3248 3280 3360  1800 1803 1808 1852 -hsync -vsync (111.1 kHz eP)
[    18.736] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    18.736] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[    18.736] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[    18.736] (--) NVIDIA(GPU-0): 
[    18.737] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    18.737] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[    18.737] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[    18.737] (--) NVIDIA(GPU-0): 
[    18.737] (II) modeset(G0): EDID vendor "SHP", prod id 5153
[    18.737] (II) modeset(G0): Printing DDC gathered Modelines:
[    18.737] (II) modeset(G0): Modeline "3200x1800"x0.0  373.25  3200 3248 3280 3360  1800 1803 1808 1852 -hsync -vsync (111.1 kHz eP)
[    18.993] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    18.993] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[    18.993] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[    18.993] (--) NVIDIA(GPU-0): 
[    18.993] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    18.993] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[    18.993] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[    18.993] (--) NVIDIA(GPU-0): 
[    18.994] (II) modeset(G0): EDID vendor "SHP", prod id 5153
[    18.994] (II) modeset(G0): Printing DDC gathered Modelines:
[    18.994] (II) modeset(G0): Modeline "3200x1800"x0.0  373.25  3200 3248 3280 3360  1800 1803 1808 1852 -hsync -vsync (111.1 kHz eP)
[    49.345] (II) config/udev: Adding input device Bluetooth Mouse M336/M337/M535 (/dev/input/mouse2)
[    49.345] (II) No input driver specified, ignoring this device.
[    49.345] (II) This device may have been added with another device file.
[    49.401] (II) config/udev: Adding input device Bluetooth Mouse M336/M337/M535 (/dev/input/event15)
[    49.401] (**) Bluetooth Mouse M336/M337/M535: Applying InputClass "evdev pointer catchall"
[    49.401] (**) Bluetooth Mouse M336/M337/M535: Applying InputClass "evdev keyboard catchall"
[    49.401] (II) Using input driver 'evdev' for 'Bluetooth Mouse M336/M337/M535'
[    49.401] (**) Bluetooth Mouse M336/M337/M535: always reports core events
[    49.401] (**) evdev: Bluetooth Mouse M336/M337/M535: Device: "/dev/input/event15"
[    49.401] (--) evdev: Bluetooth Mouse M336/M337/M535: Vendor 0x46d Product 0xb014
[    49.401] (--) evdev: Bluetooth Mouse M336/M337/M535: Found 12 mouse buttons
[    49.401] (--) evdev: Bluetooth Mouse M336/M337/M535: Found scroll wheel(s)
[    49.401] (--) evdev: Bluetooth Mouse M336/M337/M535: Found relative axes
[    49.401] (--) evdev: Bluetooth Mouse M336/M337/M535: Found x and y relative axes
[    49.401] (--) evdev: Bluetooth Mouse M336/M337/M535: Found keys
[    49.401] (II) evdev: Bluetooth Mouse M336/M337/M535: Configuring as mouse
[    49.401] (II) evdev: Bluetooth Mouse M336/M337/M535: Configuring as keyboard
[    49.401] (II) evdev: Bluetooth Mouse M336/M337/M535: Adding scrollwheel support
[    49.401] (**) evdev: Bluetooth Mouse M336/M337/M535: YAxisMapping: buttons 4 and 5
[    49.401] (**) evdev: Bluetooth Mouse M336/M337/M535: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    49.401] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-8/1-8:1.0/bluetooth/hci0/hci0:1/0005:046D:B014.0003/input/input17/event15"
[    49.401] (II) XINPUT: Adding extended input device "Bluetooth Mouse M336/M337/M535" (type: KEYBOARD, id 15)
[    49.401] (**) Option "xkb_rules" "evdev"
[    49.401] (**) Option "xkb_model" "pc105"
[    49.401] (**) Option "xkb_layout" "us"
[    49.401] (WW) Option "xkb_variant" requires a string value
[    49.401] (WW) Option "xkb_options" requires a string value
[    49.401] (II) evdev: Bluetooth Mouse M336/M337/M535: initialized for relative axes.
[    49.402] (**) Bluetooth Mouse M336/M337/M535: (accel) keeping acceleration scheme 1
[    49.402] (**) Bluetooth Mouse M336/M337/M535: (accel) acceleration profile 0
[    49.402] (**) Bluetooth Mouse M336/M337/M535: (accel) acceleration factor: 2.000
[    49.402] (**) Bluetooth Mouse M336/M337/M535: (accel) acceleration threshold: 4
[    67.838] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    67.838] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[    67.838] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[    67.838] (--) NVIDIA(GPU-0): 
[    67.838] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    67.838] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[    67.838] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[    67.838] (--) NVIDIA(GPU-0): 
[    67.839] (II) modeset(G0): EDID vendor "SHP", prod id 5153
[    67.839] (II) modeset(G0): Printing DDC gathered Modelines:
[    67.839] (II) modeset(G0): Modeline "3200x1800"x0.0  373.25  3200 3248 3280 3360  1800 1803 1808 1852 -hsync -vsync (111.1 kHz eP)
[    69.719] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    69.719] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[    69.719] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[    69.719] (--) NVIDIA(GPU-0): 
[    69.719] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    69.719] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[    69.719] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[    69.719] (--) NVIDIA(GPU-0): 
[    69.719] (II) modeset(G0): EDID vendor "SHP", prod id 5153
[    69.719] (II) modeset(G0): Printing DDC gathered Modelines:
[    69.719] (II) modeset(G0): Modeline "3200x1800"x0.0  373.25  3200 3248 3280 3360  1800 1803 1808 1852 -hsync -vsync (111.1 kHz eP)
[    70.570] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    70.570] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[    70.570] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[    70.570] (--) NVIDIA(GPU-0): 
[    70.571] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    70.571] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[    70.571] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[    70.571] (--) NVIDIA(GPU-0): 
[    70.571] (II) modeset(G0): EDID vendor "SHP", prod id 5153
[    70.571] (II) modeset(G0): Printing DDC gathered Modelines:
[    70.571] (II) modeset(G0): Modeline "3200x1800"x0.0  373.25  3200 3248 3280 3360  1800 1803 1808 1852 -hsync -vsync (111.1 kHz eP)
[   107.589] (--) NVIDIA(GPU-0): DFP-0: disconnected
[   107.589] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[   107.589] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[   107.589] (--) NVIDIA(GPU-0): 
[   107.589] (--) NVIDIA(GPU-0): DFP-0: disconnected
[   107.589] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[   107.589] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[   107.589] (--) NVIDIA(GPU-0): 
[   107.589] (II) modeset(G0): EDID vendor "SHP", prod id 5153
[   107.590] (II) modeset(G0): Printing DDC gathered Modelines:
[   107.590] (II) modeset(G0): Modeline "3200x1800"x0.0  373.25  3200 3248 3280 3360  1800 1803 1808 1852 -hsync -vsync (111.1 kHz eP)
```

---

