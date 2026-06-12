---
title: "Error starting Xorg with NVIDIA + Intel (SkyLake graphic cards (not hybrid)"
date: 2016-11-08
forum: Hardware
---

### Post by cmartinezcipf on 2016-11-08
Hi,


I have a workstation with two graphic cards: an integrated Intel and a NVIDIA. With Ubuntu 16.04 and NVIDIA everything works fine, but I need to use the Intel one to connect 2 monitors with display port.


To make things sorter, after enabling that card in the BIOS, downloading the Intel Firmware (skl_guc_ver6 and kbl_dmc_ver1, just in case) and using the latest Intel drivers using the tool they provide, I managed to get to the terminal without freezing the computer, but Xorg fails to start. Now the attached data.


Xorg.0.log:

```
[    11.555] 
X.Org X Server 1.18.4
Release Date: 2016-07-19
[    11.555] X Protocol Version 11, Revision 0
[    11.555] Build Operating System: Linux 3.13.0-95-generic x86_64 Ubuntu
[    11.555] Current Operating System: Linux hp02 4.4.0-45-generic #66-Ubuntu SMP Wed Oct 19 14:12:37 UTC 2016 x86_64
[    11.555] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-45-generic.efi.signed root=UUID=394baf2f-29df-45dc-88d4-9d44db542eb5 ro quiet splash vt.handoff=7
[    11.555] Build Date: 14 September 2016  03:33:24PM
[    11.555] xorg-server 2:1.18.4-0ubuntu0.1 (For technical support please see http://www.ubuntu.com/support) 
[    11.555] Current version of pixman: 0.33.6
[    11.555]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    11.555] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    11.555] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Nov  7 16:11:02 2016
[    11.555] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    11.555] (==) No Layout section.  Using the first Screen section.
[    11.555] (==) No screen section available. Using defaults.
[    11.555] (**) |-->Screen "Default Screen Section" (0)
[    11.555] (**) |   |-->Monitor "<default monitor>"
[    11.555] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    11.555] (==) Automatically adding devices
[    11.555] (==) Automatically enabling devices
[    11.555] (==) Automatically adding GPU devices
[    11.555] (==) Max clients allowed: 256, resource mask: 0x1fffff
[    11.555] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    11.555]     Entry deleted from font path.
[    11.555] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    11.555]     Entry deleted from font path.
[    11.555] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    11.555]     Entry deleted from font path.
[    11.555] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    11.555]     Entry deleted from font path.
[    11.555] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    11.555]     Entry deleted from font path.
[    11.555] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    11.555] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    11.555] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    11.555] (II) Loader magic: 0x55daa4c1edc0
[    11.555] (II) Module ABI versions:
[    11.555]     X.Org ANSI C Emulation: 0.4
[    11.555]     X.Org Video Driver: 20.0
[    11.555]     X.Org XInput driver : 22.1
[    11.555]     X.Org Server Extension : 9.0
[    11.556] (++) using VT number 7


[    11.556] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
[    11.556] (II) xfree86: Adding drm device (/dev/dri/card0)
[    11.556] (II) xfree86: Adding drm device (/dev/dri/card1)
[    11.557] (--) PCI: (0:0:2:0) 8086:191d:103c:802f rev 6, Mem @ 0xd0000000/16777216, 0xc0000000/268435456, I/O @ 0x00004000/64
[    11.557] (--) PCI:*(0:1:0:0) 10de:13bb:103c:1098 rev 162, Mem @ 0xd1000000/16777216, 0xa0000000/268435456, 0xb0000000/33554432, I/O @ 0x00003000/128, BIOS @ 0x????????/524288
[    11.557] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    11.557] (II) "glx" will be loaded by default.
[    11.557] (II) LoadModule: "glx"
[    11.557] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    11.559] (II) Module glx: vendor="NVIDIA Corporation"
[    11.559]     compiled for 4.0.2, module version = 1.0.0
[    11.559]     Module class: X.Org Server Extension
[    11.559] (II) NVIDIA GLX Module  367.57  Mon Oct  3 20:28:17 PDT 2016
[    11.559] (==) Matched nvidia as autoconfigured driver 0
[    11.559] (==) Matched nouveau as autoconfigured driver 1
[    11.559] (==) Matched intel as autoconfigured driver 2
[    11.559] (==) Matched nvidia as autoconfigured driver 3
[    11.559] (==) Matched nouveau as autoconfigured driver 4
[    11.559] (==) Matched modesetting as autoconfigured driver 5
[    11.559] (==) Matched fbdev as autoconfigured driver 6
[    11.559] (==) Matched vesa as autoconfigured driver 7
[    11.559] (==) Assigned the driver to the xf86ConfigLayout
[    11.559] (II) LoadModule: "nvidia"
[    11.559] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    11.559] (II) Module nvidia: vendor="NVIDIA Corporation"
[    11.559]     compiled for 4.0.2, module version = 1.0.0
[    11.559]     Module class: X.Org Video Driver
[    11.559] (II) LoadModule: "nouveau"
[    11.559] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    11.559] (II) Module nouveau: vendor="X.Org Foundation"
[    11.559]     compiled for 1.18.1, module version = 1.0.12
[    11.559]     Module class: X.Org Video Driver
[    11.559]     ABI class: X.Org Video Driver, version 20.0
[    11.559] (II) LoadModule: "intel"
[    11.559] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    11.559] (II) Module intel: vendor="X.Org Foundation"
[    11.559]     compiled for 1.18.3, module version = 2.99.917
[    11.559]     Module class: X.Org Video Driver
[    11.559]     ABI class: X.Org Video Driver, version 20.0
[    11.559] (II) LoadModule: "modesetting"
[    11.559] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    11.559] (II) Module modesetting: vendor="X.Org Foundation"
[    11.559]     compiled for 1.18.4, module version = 1.18.4
[    11.559]     Module class: X.Org Video Driver
[    11.559]     ABI class: X.Org Video Driver, version 20.0
[    11.559] (II) LoadModule: "fbdev"
[    11.560] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    11.560] (II) Module fbdev: vendor="X.Org Foundation"
[    11.560]     compiled for 1.18.1, module version = 0.4.4
[    11.560]     Module class: X.Org Video Driver
[    11.560]     ABI class: X.Org Video Driver, version 20.0
[    11.560] (II) LoadModule: "vesa"
[    11.560] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    11.560] (II) Module vesa: vendor="X.Org Foundation"
[    11.560]     compiled for 1.18.1, module version = 2.3.4
[    11.560]     Module class: X.Org Video Driver
[    11.560]     ABI class: X.Org Video Driver, version 20.0
[    11.560] (II) NVIDIA dlloader X Driver  367.57  Mon Oct  3 20:03:48 PDT 2016
[    11.560] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    11.560] (II) NOUVEAU driver Date:   Tue Dec 8 15:52:25 2015 +1000
[    11.560] (II) NOUVEAU driver for NVIDIA chipset families :
[    11.560]     RIVA TNT        (NV04)
[    11.560]     RIVA TNT2       (NV05)
[    11.560]     GeForce 256     (NV10)
[    11.560]     GeForce 2       (NV11, NV15)
[    11.560]     GeForce 4MX     (NV17, NV18)
[    11.560]     GeForce 3       (NV20)
[    11.560]     GeForce 4Ti     (NV25, NV28)
[    11.560]     GeForce FX      (NV3x)
[    11.560]     GeForce 6       (NV4x)
[    11.560]     GeForce 7       (G7x)
[    11.560]     GeForce 8       (G8x)
[    11.560]     GeForce GTX 200 (NVA0)
[    11.560]     GeForce GTX 400 (NVC0)
[    11.560] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[    11.560] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[    11.560] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[    11.560] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[    11.560] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    11.560] (II) FBDEV: driver for framebuffer: fbdev
[    11.560] (II) VESA: driver for VESA chipsets: vesa
[    11.560] (II) Loading sub module "fb"
[    11.560] (II) LoadModule: "fb"
[    11.560] (II) Loading /usr/lib/xorg/modules/libfb.so
[    11.560] (II) Module fb: vendor="X.Org Foundation"
[    11.560]     compiled for 1.18.4, module version = 1.0.0
[    11.560]     ABI class: X.Org ANSI C Emulation, version 0.4
[    11.560] (II) Loading sub module "wfb"
[    11.560] (II) LoadModule: "wfb"
[    11.560] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    11.560] (II) Module wfb: vendor="X.Org Foundation"
[    11.560]     compiled for 1.18.4, module version = 1.0.0
[    11.560]     ABI class: X.Org ANSI C Emulation, version 0.4
[    11.560] (II) Loading sub module "ramdac"
[    11.560] (II) LoadModule: "ramdac"
[    11.560] (II) Module "ramdac" already built-in
[    11.561] (II) intel(G0): Using Kernel Mode Setting driver: i915_bpo, version 1.6.0 20160425
[    11.561] (II) intel(G0): SNA compiled: xserver-xorg-video-intel 2:2.99.917+git20160325-1ubuntu1.1 (Timo Aaltonen <tjaalton@debian.org>)
[    11.561] (II) intel(G0): SNA compiled for use with valgrind
[    11.561] (WW) Falling back to old probe method for modesetting
[    11.561] (WW) Falling back to old probe method for fbdev
[    11.561] (II) Loading sub module "fbdevhw"
[    11.561] (II) LoadModule: "fbdevhw"
[    11.561] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    11.561] (II) Module fbdevhw: vendor="X.Org Foundation"
[    11.561]     compiled for 1.18.4, module version = 0.0.2
[    11.561]     ABI class: X.Org Video Driver, version 20.0
[    11.561] (WW) Falling back to old probe method for vesa
[    11.561] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    11.561] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    11.561] (==) NVIDIA(0): RGB weight 888
[    11.561] (==) NVIDIA(0): Default visual is TrueColor
[    11.561] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    11.561] (**) NVIDIA(0): Enabling 2D acceleration
[    11.980] (--) NVIDIA(0): Valid display device(s) on GPU-0 at PCI:1:0:0
[    11.980] (--) NVIDIA(0):     CRT-0
[    11.980] (--) NVIDIA(0):     DFP-0 (boot)
[    11.980] (--) NVIDIA(0):     DFP-1
[    11.980] (--) NVIDIA(0):     DFP-2
[    11.982] (--) NVIDIA(0): CRT-0: disconnected
[    11.982] (--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
[    11.982] (--) NVIDIA(0): 
[    11.985] (--) NVIDIA(0): DFP-0: disconnected
[    11.985] (--) NVIDIA(0): DFP-0: Internal TMDS
[    11.985] (--) NVIDIA(0): DFP-0: 330.0 MHz maximum pixel clock
[    11.985] (--) NVIDIA(0): 
[    11.985] (--) NVIDIA(0): DFP-1: disconnected
[    11.985] (--) NVIDIA(0): DFP-1: Internal TMDS
[    11.985] (--) NVIDIA(0): DFP-1: 165.0 MHz maximum pixel clock
[    11.985] (--) NVIDIA(0): 
[    11.985] (--) NVIDIA(0): DFP-2: disconnected
[    11.985] (--) NVIDIA(0): DFP-2: Internal DisplayPort
[    11.985] (--) NVIDIA(0): DFP-2: 960.0 MHz maximum pixel clock
[    11.985] (--) NVIDIA(0): 
[    11.986] (II) NVIDIA(0): NVIDIA GPU Quadro K620 (GM107GL-A) at PCI:1:0:0 (GPU-0)
[    11.986] (--) NVIDIA(0): Memory: 2097152 kBytes
[    11.986] (--) NVIDIA(0): VideoBIOS: 82.07.7a.00.13
[    11.986] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    11.986] (EE) NVIDIA(0): Failed to assign any connected display devices to X screen 0. 
[    11.986] (EE) NVIDIA(0):     Set AllowEmptyInitialConfiguration if you want the server
[    11.986] (EE) NVIDIA(0):     to start anyway
[    11.986] (EE) NVIDIA(0): Failing initialization of X screen 0
[    12.360] (II) UnloadModule: "nvidia"
[    12.360] (II) UnloadSubModule: "wfb"
[    12.360] (II) UnloadSubModule: "fb"
[    12.360] (--) intel(G0): gen9 engineering sample
[    12.360] (--) intel(G0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2, avx, avx2; using a maximum of 4 threads
[    12.360] (==) intel(G0): Depth 24, (--) framebuffer bpp 32
[    12.360] (==) intel(G0): RGB weight 888
[    12.360] (==) intel(G0): Default visual is TrueColor
[    12.361] (II) intel(G0): Output HDMI1 has no monitor section
[    12.361] (II) intel(G0): Enabled output HDMI1
[    12.361] (II) intel(G0): Output DP1 has no monitor section
[    12.361] (II) intel(G0): Enabled output DP1
[    12.361] (II) intel(G0): Output HDMI2 has no monitor section
[    12.361] (II) intel(G0): Enabled output HDMI2
[    12.361] (II) intel(G0): Output DP2 has no monitor section
[    12.361] (II) intel(G0): Enabled output DP2
[    12.361] (II) intel(G0): Output HDMI3 has no monitor section
[    12.361] (II) intel(G0): Enabled output HDMI3
[    12.361] (--) intel(G0): Using a maximum size of 256x256 for hardware cursors
[    12.361] (II) intel(G0): Output VIRTUAL1 has no monitor section
[    12.361] (II) intel(G0): Enabled output VIRTUAL1
[    12.361] (II) intel(G0): EDID for output DP1
[    12.362] (II) intel(G0): EDID for output DP2
[    12.362] (II) intel(G0): Manufacturer: HWP  Model: 3283  Serial#: 16843009
[    12.362] (II) intel(G0): Year: 2016  Week: 23
[    12.362] (II) intel(G0): EDID Version: 1.4
[    12.362] (II) intel(G0): Digital Display Input
[    12.362] (II) intel(G0): 8 bits per channel
[    12.362] (II) intel(G0): Digital interface is DisplayPort
[    12.362] (II) intel(G0): Max Image Size [cm]: horiz.: 51  vert.: 29
[    12.362] (II) intel(G0): Gamma: 2.20
[    12.362] (II) intel(G0): DPMS capabilities: Off
[    12.362] (II) intel(G0): Supported color encodings: RGB 4:4:4 
[    12.362] (II) intel(G0): First detailed timing is preferred mode
[    12.362] (II) intel(G0): Preferred mode is native pixel format and refresh rate
[    12.362] (II) intel(G0): redX: 0.655 redY: 0.336   greenX: 0.317 greenY: 0.616
[    12.362] (II) intel(G0): blueX: 0.152 blueY: 0.066   whiteX: 0.313 whiteY: 0.329
[    12.362] (II) intel(G0): Supported established timings:
[    12.362] (II) intel(G0): 640x480@60Hz
[    12.362] (II) intel(G0): 800x600@60Hz
[    12.362] (II) intel(G0): 1024x768@60Hz
[    12.362] (II) intel(G0): Manufacturer's mask: 0
[    12.362] (II) intel(G0): Supported standard timings:
[    12.362] (II) intel(G0): #0: hsize: 1920  vsize 1080  refresh: 60  vid: 49361
[    12.362] (II) intel(G0): #1: hsize: 1280  vsize 720  refresh: 60  vid: 49281
[    12.362] (II) intel(G0): #2: hsize: 1600  vsize 900  refresh: 60  vid: 49321
[    12.362] (II) intel(G0): #3: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[    12.362] (II) intel(G0): #4: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    12.362] (II) intel(G0): #5: hsize: 1280  vsize 800  refresh: 60  vid: 129
[    12.362] (II) intel(G0): #6: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    12.362] (II) intel(G0): Supported detailed timing:
[    12.362] (II) intel(G0): clock: 148.5 MHz   Image Size:  509 x 286 mm
[    12.362] (II) intel(G0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    12.362] (II) intel(G0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    12.362] (II) intel(G0): Ranges: V min: 50 V max: 60 Hz, H min: 30 H max: 80 kHz, PixClock max 175 MHz
[    12.362] (II) intel(G0): Monitor name: HP Z23n
[    12.362] (II) intel(G0): Serial No: 6CM6231MS1
[    12.362] (II) intel(G0): EDID (in hex):
[    12.362] (II) intel(G0):     00ffffffffffff0022f0833201010101
[    12.362] (II) intel(G0):     171a0104a5331d7822c705a756519d27
[    12.362] (II) intel(G0):     115054210800d1c081c0a9c0b3009500
[    12.362] (II) intel(G0):     810081800101023a801871382d40582c
[    12.362] (II) intel(G0):     4500fd1e1100001e000000fd00323c1e
[    12.362] (II) intel(G0):     5011010a202020202020000000fc0048
[    12.362] (II) intel(G0):     50205a32336e0a2020202020000000ff
[    12.362] (II) intel(G0):     0036434d363233314d53310a202000ca
[    12.362] (II) intel(G0): Printing probed modes for output DP2
[    12.362] (II) intel(G0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    12.362] (II) intel(G0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[    12.362] (II) intel(G0): Modeline "1600x900"x60.0  108.00  1600 1624 1704 1800  900 901 904 1000 +hsync +vsync (60.0 kHz e)
[    12.362] (II) intel(G0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    12.362] (II) intel(G0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz e)
[    12.362] (II) intel(G0): Modeline "1280x800"x60.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz e)
[    12.362] (II) intel(G0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    12.362] (II) intel(G0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    12.362] (II) intel(G0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    12.362] (II) intel(G0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    12.488] (II) intel(G0): EDID for output HDMI1
[    12.616] (II) intel(G0): EDID for output HDMI2
[    12.618] (II) intel(G0): EDID for output HDMI3
[    12.618] (II) intel(G0): EDID for output VIRTUAL1
[    12.618] (II) intel(G0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    12.618] (==) intel(G0): TearFree disabled
[    12.618] (==) intel(G0): DPI set to (96, 96)
[    12.618] (II) Loading sub module "dri2"
[    12.618] (II) LoadModule: "dri2"
[    12.618] (II) Module "dri2" already built-in
[    12.618] (II) Loading sub module "present"
[    12.618] (II) LoadModule: "present"
[    12.618] (II) Module "present" already built-in
[    12.618] (EE) Screen(s) found, but none have a usable configuration.
[    12.618] (EE) 
Fatal server error:
[    12.618] (EE) no screens found(EE) 
[    12.618] (EE) 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[    12.618] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    12.618] (EE) 
[    12.620] (EE) Server terminated with error (1). Closing log file.

```

lspci -vnn:
```
00:00.0 Host bridge [0600]: Intel Corporation Sky Lake Host Bridge/DRAM Registers [8086:1918] (rev 07)
    Subsystem: Hewlett-Packard Company Skylake Host Bridge/DRAM Registers [103c:802f]
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: ie31200_edac
    Kernel modules: ie31200_edac


00:01.0 PCI bridge [0604]: Intel Corporation Sky Lake PCIe Controller (x16) [8086:1901] (rev 07) (prog-if 00 [Normal decode])
    Physical Slot: 2
    Flags: bus master, fast devsel, latency 0, IRQ 120
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: d1000000-d20fffff
    Prefetchable memory behind bridge: 00000000a0000000-00000000b1ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp


00:02.0 Display controller [0380]: Intel Corporation Device [8086:191d] (rev 06)
    DeviceName: Onboard IGD
    Subsystem: Hewlett-Packard Company Device [103c:802f]
    Flags: bus master, fast devsel, latency 0, IRQ 124
    Memory at d0000000 (64-bit, non-prefetchable) [size=16M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 4000 [size=64]
    Capabilities: <access denied>
    Kernel driver in use: i915_bpo
    Kernel modules: i915_bpo


00:14.0 USB controller [0c03]: Intel Corporation Sunrise Point-H USB 3.0 xHCI Controller [8086:a12f] (rev 31) (prog-if 30 [XHCI])
    Subsystem: Hewlett-Packard Company Sunrise Point-H USB 3.0 xHCI Controller [103c:802f]
    Flags: bus master, medium devsel, latency 0, IRQ 121
    Memory at d2120000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd


00:14.2 Signal processing controller [1180]: Intel Corporation Sunrise Point-H Thermal subsystem [8086:a131] (rev 31)
    Subsystem: Hewlett-Packard Company Sunrise Point-H Thermal subsystem [103c:802f]
    Flags: fast devsel, IRQ 11
    Memory at d214a000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>


00:16.0 Communication controller [0780]: Intel Corporation Sunrise Point-H CSME HECI #1 [8086:a13a] (rev 31)
    Subsystem: Hewlett-Packard Company Sunrise Point-H CSME HECI [103c:802f]
    Flags: bus master, fast devsel, latency 0, IRQ 125
    Memory at d214b000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: mei_me
    Kernel modules: mei_me


00:16.3 Serial controller [0700]: Intel Corporation Sunrise Point-H KT Redirection [8086:a13d] (rev 31) (prog-if 02 [16550])
    Subsystem: Hewlett-Packard Company Sunrise Point-H KT Redirection [103c:802f]
    Flags: 66MHz, fast devsel, IRQ 19
    I/O ports at 4080 [size=8]
    Memory at d214f000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: serial


00:17.0 RAID bus controller [0104]: Intel Corporation SATA Controller [RAID mode] [8086:2822] (rev 31)
    Subsystem: Hewlett-Packard Company SATA Controller [RAID mode] [103c:802f]
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 122
    Memory at d2148000 (32-bit, non-prefetchable) [size=8K]
    Memory at d214e000 (32-bit, non-prefetchable) [size=256]
    I/O ports at 4088 [size=8]
    I/O ports at 4090 [size=4]
    I/O ports at 4060 [size=32]
    Memory at d214c000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci


00:1f.0 ISA bridge [0601]: Intel Corporation Sunrise Point-H LPC Controller [8086:a149] (rev 31)
    Subsystem: Hewlett-Packard Company Sunrise Point-H LPC Controller [103c:802f]
    Flags: bus master, fast devsel, latency 0


00:1f.2 Memory controller [0580]: Intel Corporation Sunrise Point-H PMC [8086:a121] (rev 31)
    Subsystem: Hewlett-Packard Company Sunrise Point-H PMC [103c:802f]
    Flags: fast devsel
    Memory at d2144000 (32-bit, non-prefetchable) [disabled] [size=16K]


00:1f.3 Audio device [0403]: Intel Corporation Sunrise Point-H HD Audio [8086:a170] (rev 31)
    Subsystem: Hewlett-Packard Company Sunrise Point-H HD Audio [103c:802f]
    Flags: bus master, fast devsel, latency 64, IRQ 126
    Memory at d2140000 (64-bit, non-prefetchable) [size=16K]
    Memory at d2130000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel


00:1f.4 SMBus [0c05]: Intel Corporation Sunrise Point-H SMBus [8086:a123] (rev 31)
    Subsystem: Hewlett-Packard Company Sunrise Point-H SMBus [103c:802f]
    Flags: medium devsel, IRQ 11
    Memory at d214d000 (64-bit, non-prefetchable) [disabled] [size=256]
    I/O ports at efa0 [disabled] [size=32]
    Kernel modules: i2c_i801


00:1f.6 Ethernet controller [0200]: Intel Corporation Ethernet Connection (2) I219-LM [8086:15b7] (rev 31)
    DeviceName: Onboard Lan
    Subsystem: Hewlett-Packard Company Ethernet Connection (2) I219-LM [103c:802f]
    Flags: bus master, fast devsel, latency 0, IRQ 123
    Memory at d2100000 (32-bit, non-prefetchable) [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: e1000e
    Kernel modules: e1000e


01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GM107GL [Quadro K620] [10de:13bb] (rev a2) (prog-if 00 [VGA controller])
    Subsystem: Hewlett-Packard Company GM107GL [Quadro K620] [103c:1098]
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at d1000000 (32-bit, non-prefetchable) [size=16M]
    Memory at a0000000 (64-bit, prefetchable) [size=256M]
    Memory at b0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at 3000 [size=128]
    [virtual] Expansion ROM at d2080000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidiafb, nouveau, nvidia_367, nvidia_367_drm


01:00.1 Audio device [0403]: NVIDIA Corporation Device [10de:0fbc] (rev a1)
    Subsystem: Hewlett-Packard Company Device [103c:1098]
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at d2000000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel



```


lshw -C display:

```
  *-display
       descripción: VGA compatible controller
       producto: GM107GL [Quadro K620]
       fabricante: NVIDIA Corporation
       id físico: 0
       información del bus: pci@0000:01:00.0
       versión: a2
       anchura: 64 bits
       reloj: 33MHz
       capacidades: pm msi pciexpress vga_controller bus_master cap_list rom
       configuración: driver=nvidia latency=0
       recursos: irq:16 memoria:d1000000-d1ffffff memoria:a0000000-afffffff memoria:b0000000-b1ffffff ioport:3000(size=128) memoria:d2080000-d20fffff
  *-display
       descripción: Display controller
       producto: Intel Corporation
       fabricante: Intel Corporation
       id físico: 2
       información del bus: pci@0000:00:02.0
       versión: 06
       anchura: 64 bits
       reloj: 33MHz
       capacidades: pciexpress msi pm bus_master cap_list
       configuración: driver=i915_bpo latency=0
       recursos: irq:124 memoria:d0000000-d0ffffff memoria:c0000000-cfffffff ioport:4000(size=64)



```

lsb_release -a:
```
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial



```

Other things I have tried:

[LIST]
[*]Generating a xorg.conf using 'X -configure' then modifying the default card choosing 'intel' driver and changing the PCI to 'PCI:0:2:0'. This sometimes freezes the computer.
[*]Removing intel driver and try to let modesetting chose. Similar Xorg.0.log output.
[/LIST]


Any ideas of what else could I try to make it work?

Thank you very much.

---

