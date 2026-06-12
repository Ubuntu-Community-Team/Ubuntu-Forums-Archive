---
title: "NVidia M1000M GPU problem on Ubuntu 16.04"
date: 2016-05-02
forum: Hardware
---

### Post by i2000s2 on 2016-05-02
I got a new Thinkpad P50 with NVidia M1000M GPU and i7-7600HQ CPU. It has been a long haul to connect to an external monitor with an NVidia graphic driver installed. Finally I found GNOME 3.20 (from a friend) and nvidia-361/364 work to boot up a second monitor, but I found the external screen tears and flickers when the screens turn off for sleep or idle. I have tried a lot of solutions found online, like installing and reinstalling different nvidia drivers, but no luck so far. My ultimate goal is to make the nVidia card work and then install Bumblebee for better GPU management. I hope in the forum, someone can guide me reach the target, or point out to me what caused the problem. Please find the following system information:

```

qxd@qxd-QC5-Ubuntu:~$ dpkg -l nvidia-prime
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  nvidia-prime   0.8.2        amd64        Tools to enable NVIDIA's Prime
qxd@qxd-QC5-Ubuntu:~$ dpkg -l nvidia-settings
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  nvidia-setting 364.15-0ubun amd64        Tool for configuring the NVIDIA g

```

```

qxd@qxd-QC5-Ubuntu:~$ cat /var/log/Xorg.0.log
[  6436.779] 
X.Org X Server 1.18.3
Release Date: 2016-04-04
[  6436.779] X Protocol Version 11, Revision 0
[  6436.779] Build Operating System: Linux 3.13.0-85-generic x86_64 Ubuntu
[  6436.779] Current Operating System: Linux qxd-QC5-Ubuntu 4.6.0-040600rc5-generic #201604242031 SMP Mon Apr 25 00:34:15 UTC 2016 x86_64
[  6436.779] Kernel command line: BOOT_IMAGE=/vmlinuz-4.6.0-040600rc5-generic root=/dev/mapper/ubuntuvg-root ro rootflags=subvol=@ quiet splash vt.handoff=7
[  6436.779] Build Date: 07 April 2016  09:18:50AM
[  6436.779] xorg-server 2:1.18.3-1ubuntu2 (For technical support please see http://www.ubuntu.com/support) 
[  6436.779] Current version of pixman: 0.33.6
[  6436.779]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[  6436.779] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  6436.779] (==) Log file: "/var/log/Xorg.0.log", Time: Mon May  2 20:01:59 2016
[  6436.779] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  6436.779] (==) No Layout section.  Using the first Screen section.
[  6436.779] (==) No screen section available. Using defaults.
[  6436.779] (**) |-->Screen "Default Screen Section" (0)
[  6436.779] (**) |   |-->Monitor "<default monitor>"
[  6436.779] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[  6436.779] (==) Automatically adding devices
[  6436.779] (==) Automatically enabling devices
[  6436.779] (==) Automatically adding GPU devices
[  6436.779] (==) Max clients allowed: 256, resource mask: 0x1fffff
[  6436.779] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  6436.779]     Entry deleted from font path.
[  6436.779] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[  6436.779]     Entry deleted from font path.
[  6436.779] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[  6436.779]     Entry deleted from font path.
[  6436.779] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[  6436.779]     Entry deleted from font path.
[  6436.779] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[  6436.779]     Entry deleted from font path.
[  6436.779] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[  6436.779] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[  6436.779] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[  6436.779] (II) Loader magic: 0x55db6b08cda0
[  6436.779] (II) Module ABI versions:
[  6436.779]     X.Org ANSI C Emulation: 0.4
[  6436.779]     X.Org Video Driver: 20.0
[  6436.779]     X.Org XInput driver : 22.1
[  6436.779]     X.Org Server Extension : 9.0
[  6436.780] (++) using VT number 7


[  6436.780] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
[  6436.780] (II) xfree86: Adding drm device (/dev/dri/card0)
[  6436.781] (II) xfree86: Adding drm device (/dev/dri/card1)
[  6436.782] (--) PCI:*(0:0:2:0) 8086:191b:17aa:222e rev 6, Mem @ 0xc2000000/16777216, 0x60000000/268435456, I/O @ 0x00005000/64, BIOS @ 0x????????/131072
[  6436.782] (--) PCI: (0:1:0:0) 10de:13b1:17aa:222e rev 162, Mem @ 0xc3000000/16777216, 0xb0000000/268435456, 0xc0000000/33554432, I/O @ 0x00004000/128, BIOS @ 0x????????/524288
[  6436.782] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[  6436.782] (II) "glx" will be loaded by default.
[  6436.782] (II) LoadModule: "glx"
[  6436.782] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[  6436.783] (II) Module glx: vendor="X.Org Foundation"
[  6436.783]     compiled for 1.18.3, module version = 1.0.0
[  6436.783]     ABI class: X.Org Server Extension, version 9.0
[  6436.783] (==) AIGLX enabled
[  6436.783] (==) Matched intel as autoconfigured driver 0
[  6436.783] (==) Matched nvidia as autoconfigured driver 1
[  6436.783] (==) Matched nouveau as autoconfigured driver 2
[  6436.783] (==) Matched intel as autoconfigured driver 3
[  6436.783] (==) Matched modesetting as autoconfigured driver 4
[  6436.783] (==) Matched fbdev as autoconfigured driver 5
[  6436.783] (==) Matched vesa as autoconfigured driver 6
[  6436.783] (==) Assigned the driver to the xf86ConfigLayout
[  6436.783] (II) LoadModule: "intel"
[  6436.783] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[  6436.783] (II) Module intel: vendor="X.Org Foundation"
[  6436.783]     compiled for 1.18.1, module version = 2.99.917
[  6436.783]     Module class: X.Org Video Driver
[  6436.783]     ABI class: X.Org Video Driver, version 20.0
[  6436.783] (II) LoadModule: "nvidia"
[  6436.783] (WW) Warning, couldn't open module nvidia
[  6436.783] (II) UnloadModule: "nvidia"
[  6436.783] (II) Unloading nvidia
[  6436.783] (EE) Failed to load module "nvidia" (module does not exist, 0)
[  6436.783] (II) LoadModule: "nouveau"
[  6436.783] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[  6436.783] (II) Module nouveau: vendor="X.Org Foundation"
[  6436.783]     compiled for 1.18.1, module version = 1.0.12
[  6436.783]     Module class: X.Org Video Driver
[  6436.783]     ABI class: X.Org Video Driver, version 20.0
[  6436.783] (II) LoadModule: "modesetting"
[  6436.784] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[  6436.784] (II) Module modesetting: vendor="X.Org Foundation"
[  6436.784]     compiled for 1.18.3, module version = 1.18.3
[  6436.784]     Module class: X.Org Video Driver
[  6436.784]     ABI class: X.Org Video Driver, version 20.0
[  6436.784] (II) LoadModule: "fbdev"
[  6436.784] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[  6436.784] (II) Module fbdev: vendor="X.Org Foundation"
[  6436.784]     compiled for 1.18.1, module version = 0.4.4
[  6436.784]     Module class: X.Org Video Driver
[  6436.784]     ABI class: X.Org Video Driver, version 20.0
[  6436.784] (II) LoadModule: "vesa"
[  6436.784] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[  6436.784] (II) Module vesa: vendor="X.Org Foundation"
[  6436.784]     compiled for 1.18.1, module version = 2.3.4
[  6436.784]     Module class: X.Org Video Driver
[  6436.784]     ABI class: X.Org Video Driver, version 20.0
[  6436.784] (==) Matched intel as autoconfigured driver 0
[  6436.784] (==) Matched nvidia as autoconfigured driver 1
[  6436.784] (==) Matched nouveau as autoconfigured driver 2
[  6436.784] (==) Matched intel as autoconfigured driver 3
[  6436.784] (==) Matched modesetting as autoconfigured driver 4
[  6436.784] (==) Matched fbdev as autoconfigured driver 5
[  6436.784] (==) Matched vesa as autoconfigured driver 6
[  6436.784] (==) Assigned the driver to the xf86ConfigLayout
[  6436.784] (II) LoadModule: "intel"
[  6436.784] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[  6436.784] (II) Module intel: vendor="X.Org Foundation"
[  6436.784]     compiled for 1.18.1, module version = 2.99.917
[  6436.784]     Module class: X.Org Video Driver
[  6436.784]     ABI class: X.Org Video Driver, version 20.0
[  6436.784] (II) UnloadModule: "intel"
[  6436.784] (II) Unloading intel
[  6436.784] (II) Failed to load module "intel" (already loaded, 21979)
[  6436.784] (II) LoadModule: "nvidia"
[  6436.784] (WW) Warning, couldn't open module nvidia
[  6436.784] (II) UnloadModule: "nvidia"
[  6436.784] (II) Unloading nvidia
[  6436.784] (EE) Failed to load module "nvidia" (module does not exist, 0)
[  6436.784] (II) LoadModule: "nouveau"
[  6436.784] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[  6436.784] (II) Module nouveau: vendor="X.Org Foundation"
[  6436.784]     compiled for 1.18.1, module version = 1.0.12
[  6436.784]     Module class: X.Org Video Driver
[  6436.784]     ABI class: X.Org Video Driver, version 20.0
[  6436.784] (II) UnloadModule: "nouveau"
[  6436.784] (II) Unloading nouveau
[  6436.784] (II) Failed to load module "nouveau" (already loaded, 0)
[  6436.784] (II) LoadModule: "modesetting"
[  6436.784] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[  6436.784] (II) Module modesetting: vendor="X.Org Foundation"
[  6436.784]     compiled for 1.18.3, module version = 1.18.3
[  6436.784]     Module class: X.Org Video Driver
[  6436.784]     ABI class: X.Org Video Driver, version 20.0
[  6436.784] (II) UnloadModule: "modesetting"
[  6436.784] (II) Unloading modesetting
[  6436.784] (II) Failed to load module "modesetting" (already loaded, 0)
[  6436.784] (II) LoadModule: "fbdev"
[  6436.784] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[  6436.784] (II) Module fbdev: vendor="X.Org Foundation"
[  6436.784]     compiled for 1.18.1, module version = 0.4.4
[  6436.784]     Module class: X.Org Video Driver
[  6436.784]     ABI class: X.Org Video Driver, version 20.0
[  6436.784] (II) UnloadModule: "fbdev"
[  6436.784] (II) Unloading fbdev
[  6436.784] (II) Failed to load module "fbdev" (already loaded, 0)
[  6436.784] (II) LoadModule: "vesa"
[  6436.784] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[  6436.784] (II) Module vesa: vendor="X.Org Foundation"
[  6436.784]     compiled for 1.18.1, module version = 2.3.4
[  6436.784]     Module class: X.Org Video Driver
[  6436.784]     ABI class: X.Org Video Driver, version 20.0
[  6436.784] (II) UnloadModule: "vesa"
[  6436.784] (II) Unloading vesa
[  6436.784] (II) Failed to load module "vesa" (already loaded, 0)
[  6436.784] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[  6436.785] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[  6436.785] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[  6436.785] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[  6436.785] (II) NOUVEAU driver Date:   Tue Dec 8 15:52:25 2015 +1000
[  6436.785] (II) NOUVEAU driver for NVIDIA chipset families :
[  6436.785]     RIVA TNT        (NV04)
[  6436.785]     RIVA TNT2       (NV05)
[  6436.785]     GeForce 256     (NV10)
[  6436.785]     GeForce 2       (NV11, NV15)
[  6436.785]     GeForce 4MX     (NV17, NV18)
[  6436.785]     GeForce 3       (NV20)
[  6436.785]     GeForce 4Ti     (NV25, NV28)
[  6436.785]     GeForce FX      (NV3x)
[  6436.785]     GeForce 6       (NV4x)
[  6436.785]     GeForce 7       (G7x)
[  6436.785]     GeForce 8       (G8x)
[  6436.785]     GeForce GTX 200 (NVA0)
[  6436.785]     GeForce GTX 400 (NVC0)
[  6436.785] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[  6436.785] (II) FBDEV: driver for framebuffer: fbdev
[  6436.785] (II) VESA: driver for VESA chipsets: vesa
[  6436.785] (II) intel(0): Using Kernel Mode Setting driver: i915, version 1.6.0 20160229
[  6436.785] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.99.917+git20160325-1ubuntu1 (Timo Aaltonen <tjaalton@debian.org>)
[  6436.785] (II) intel(0): SNA compiled for use with valgrind
[  6436.785] (II) [drm] nouveau interface version: 1.3.1
[  6436.785] (EE) Unknown chipset: NV117
[  6436.785] (II) modeset(G0): using drv /dev/dri/card0
[  6436.785] (WW) Falling back to old probe method for fbdev
[  6436.785] (II) Loading sub module "fbdevhw"
[  6436.785] (II) LoadModule: "fbdevhw"
[  6436.785] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[  6436.785] (II) Module fbdevhw: vendor="X.Org Foundation"
[  6436.785]     compiled for 1.18.3, module version = 0.0.2
[  6436.785]     ABI class: X.Org Video Driver, version 20.0
[  6436.785] (WW) Falling back to old probe method for vesa
[  6436.786] (--) intel(0): gen9 engineering sample
[  6436.786] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2, avx, avx2; using a maximum of 4 threads
[  6436.786] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[  6436.786] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[  6436.786] (==) intel(0): RGB weight 888
[  6436.786] (==) intel(0): Default visual is TrueColor
[  6436.787] (II) intel(0): Output eDP1 has no monitor section
[  6436.804] (--) intel(0): Found backlight control interface intel_backlight (type 'raw') for output eDP1
[  6436.804] (II) intel(0): Enabled output eDP1
[  6436.804] (--) intel(0): Using a maximum size of 256x256 for hardware cursors
[  6436.804] (II) intel(0): Output VIRTUAL1 has no monitor section
[  6436.804] (II) intel(0): Enabled output VIRTUAL1
[  6436.804] (--) intel(0): Output eDP1 using initial mode 1920x1080 on pipe 0
[  6436.805] (==) intel(0): TearFree disabled
[  6436.805] (==) intel(0): DPI set to (96, 96)
[  6436.805] (II) Loading sub module "dri2"
[  6436.805] (II) LoadModule: "dri2"
[  6436.805] (II) Module "dri2" already built-in
[  6436.805] (II) Loading sub module "present"
[  6436.805] (II) LoadModule: "present"
[  6436.805] (II) Module "present" already built-in
[  6436.825] (==) modeset(G0): Depth 24, (==) framebuffer bpp 32
[  6436.825] (==) modeset(G0): RGB weight 888
[  6436.825] (==) modeset(G0): Default visual is TrueColor
[  6436.825] (II) Loading sub module "glamoregl"
[  6436.825] (II) LoadModule: "glamoregl"
[  6436.825] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[  6436.829] (II) Module glamoregl: vendor="X.Org Foundation"
[  6436.829]     compiled for 1.18.3, module version = 1.0.0
[  6436.829]     ABI class: X.Org ANSI C Emulation, version 0.4
[  6436.829] (II) glamor: OpenGL accelerated X.org driver based.
[  6436.882] (II) glamor: EGL version 1.4 (DRI2):
[  6436.883] (II) modeset(G0): glamor initialized
[  6437.014] (II) modeset(G0): Output DP-1 has no monitor section
[  6437.076] (II) modeset(G0): Output DP-2 has no monitor section
[  6437.140] (II) modeset(G0): Output DP-3 has no monitor section
[  6437.271] (II) modeset(G0): EDID for output DP-1
[  6437.271] (II) modeset(G0): Manufacturer: DEL  Model: d010  Serial#: 826689612
[  6437.271] (II) modeset(G0): Year: 2006  Week: 41
[  6437.271] (II) modeset(G0): EDID Version: 1.3
[  6437.271] (II) modeset(G0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[  6437.271] (II) modeset(G0): Sync:  Separate
[  6437.271] (II) modeset(G0): Max Image Size [cm]: horiz.: 43  vert.: 27
[  6437.271] (II) modeset(G0): Gamma: 2.20
[  6437.271] (II) modeset(G0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[  6437.271] (II) modeset(G0): Default color space is primary color space
[  6437.271] (II) modeset(G0): First detailed timing is preferred mode
[  6437.271] (II) modeset(G0): redX: 0.635 redY: 0.328   greenX: 0.292 greenY: 0.610
[  6437.271] (II) modeset(G0): blueX: 0.146 blueY: 0.069   whiteX: 0.312 whiteY: 0.328
[  6437.271] (II) modeset(G0): Supported established timings:
[  6437.271] (II) modeset(G0): 720x400@70Hz
[  6437.271] (II) modeset(G0): 640x480@60Hz
[  6437.271] (II) modeset(G0): 640x480@75Hz
[  6437.271] (II) modeset(G0): 800x600@60Hz
[  6437.271] (II) modeset(G0): 800x600@75Hz
[  6437.271] (II) modeset(G0): 1024x768@60Hz
[  6437.271] (II) modeset(G0): 1024x768@75Hz
[  6437.271] (II) modeset(G0): 1280x1024@75Hz
[  6437.271] (II) modeset(G0): Manufacturer's mask: 0
[  6437.271] (II) modeset(G0): Supported standard timings:
[  6437.271] (II) modeset(G0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[  6437.271] (II) modeset(G0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[  6437.271] (II) modeset(G0): #2: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[  6437.271] (II) modeset(G0): Supported detailed timing:
[  6437.271] (II) modeset(G0): clock: 146.2 MHz   Image Size:  430 x 270 mm
[  6437.271] (II) modeset(G0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
[  6437.271] (II) modeset(G0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
[  6437.271] (II) modeset(G0): Serial No: 641806AA1FHL
[  6437.271] (II) modeset(G0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 155 MHz
[  6437.271] (II) modeset(G0): Monitor name: DELL E207WFP
[  6437.271] (II) modeset(G0): EDID (in hex):
[  6437.271] (II) modeset(G0):     00ffffffffffff0010ac10d04c484631
[  6437.271] (II) modeset(G0):     29100103682b1b78ee8db0a2544a9c25
[  6437.271] (II) modeset(G0):     115054a54b00714f8180b30001010101
[  6437.271] (II) modeset(G0):     01010101010121399030621a274068b0
[  6437.271] (II) modeset(G0):     3600ae0e1100001c000000ff00363431
[  6437.271] (II) modeset(G0):     38303641413146484c0a000000fd0038
[  6437.271] (II) modeset(G0):     4b1e530f000a202020202020000000fc
[  6437.271] (II) modeset(G0):     0044454c4c20453230375746500a00ce
[  6437.272] (II) modeset(G0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
[  6437.272] (II) modeset(G0): Printing probed modes for output DP-1
[  6437.272] (II) modeset(G0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz eP)
[  6437.272] (II) modeset(G0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz d)
[  6437.272] (II) modeset(G0): Modeline "1600x1024"x60.2  103.12  1600 1600 1656 1664  1024 1024 1029 1030 +hsync +vsync (62.0 kHz d)
[  6437.272] (II) modeset(G0): Modeline "1400x1050"x74.8  155.80  1400 1464 1784 1912  1050 1052 1064 1090 +hsync +vsync (81.5 kHz d)
[  6437.272] (II) modeset(G0): Modeline "1400x1050"x70.0  145.06  1400 1496 1648 1896  1050 1051 1054 1093 -hsync +vsync (76.5 kHz d)
[  6437.272] (II) modeset(G0): Modeline "1400x1050"x60.0  122.00  1400 1488 1640 1880  1050 1052 1064 1082 +hsync +vsync (64.9 kHz d)
[  6437.272] (II) modeset(G0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[  6437.272] (II) modeset(G0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[  6437.272] (II) modeset(G0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz d)
[  6437.272] (II) modeset(G0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz d)
[  6437.272] (II) modeset(G0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz d)
[  6437.272] (II) modeset(G0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz d)
[  6437.272] (II) modeset(G0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[  6437.272] (II) modeset(G0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.6 kHz d)
[  6437.272] (II) modeset(G0): Modeline "1152x864"x70.0   96.77  1152 1224 1344 1536  864 865 868 900 -hsync +vsync (63.0 kHz d)
[  6437.272] (II) modeset(G0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz d)
[  6437.272] (II) modeset(G0): Modeline "1024x768"x60.0  133.47  1024 1100 1212 1400  768 768 770 794 doublescan -hsync +vsync (95.3 kHz d)
[  6437.272] (II) modeset(G0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[  6437.272] (II) modeset(G0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz d)
[  6437.272] (II) modeset(G0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[  6437.272] (II) modeset(G0): Modeline "960x720"x75.0  148.50  960 1032 1144 1320  720 720 722 750 doublescan -hsync +vsync (112.5 kHz d)
[  6437.272] (II) modeset(G0): Modeline "960x720"x60.0  117.00  960 1024 1128 1300  720 720 722 750 doublescan -hsync +vsync (90.0 kHz d)
[  6437.272] (II) modeset(G0): Modeline "928x696"x75.0  144.00  928 992 1104 1280  696 696 698 750 doublescan -hsync +vsync (112.5 kHz d)
[  6437.272] (II) modeset(G0): Modeline "928x696"x60.1  109.15  928 976 1088 1264  696 696 698 719 doublescan -hsync +vsync (86.4 kHz d)
[  6437.272] (II) modeset(G0): Modeline "896x672"x75.0  130.50  896 944 1052 1228  672 672 674 708 doublescan -hsync +vsync (106.3 kHz d)
[  6437.272] (II) modeset(G0): Modeline "896x672"x60.0  102.40  896 960 1060 1224  672 672 674 697 doublescan -hsync +vsync (83.7 kHz d)
[  6437.272] (II) modeset(G0): Modeline "960x600"x60.0   77.00  960 984 1000 1040  600 601 604 617 doublescan +hsync -vsync (74.0 kHz d)
[  6437.272] (II) modeset(G0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz d)
[  6437.272] (II) modeset(G0): Modeline "960x540"x60.0   69.25  960 984 1000 1040  540 541 544 555 doublescan +hsync -vsync (66.6 kHz d)
[  6437.272] (II) modeset(G0): Modeline "800x600"x75.0  101.25  800 832 928 1080  600 600 602 625 doublescan +hsync +vsync (93.8 kHz d)
[  6437.272] (II) modeset(G0): Modeline "800x600"x70.0   94.50  800 832 928 1080  600 600 602 625 doublescan +hsync +vsync (87.5 kHz d)
[  6437.272] (II) modeset(G0): Modeline "800x600"x65.0   87.75  800 832 928 1080  600 600 602 625 doublescan +hsync +vsync (81.2 kHz d)
[  6437.272] (II) modeset(G0): Modeline "800x600"x60.0   81.00  800 832 928 1080  600 600 602 625 doublescan +hsync +vsync (75.0 kHz d)
[  6437.272] (II) modeset(G0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz d)
[  6437.272] (II) modeset(G0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[  6437.272] (II) modeset(G0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[  6437.272] (II) modeset(G0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz d)
[  6437.272] (II) modeset(G0): Modeline "840x525"x75.0   93.50  840 900 988 1136  525 526 529 549 doublescan -hsync +vsync (82.3 kHz d)
[  6437.272] (II) modeset(G0): Modeline "840x525"x69.9   87.00  840 900 988 1136  525 526 529 548 doublescan -hsync +vsync (76.6 kHz d)
[  6437.272] (II) modeset(G0): Modeline "840x525"x60.0   73.12  840 892 980 1120  525 526 529 544 doublescan -hsync +vsync (65.3 kHz d)
[  6437.272] (II) modeset(G0): Modeline "840x525"x59.9   59.50  840 864 880 920  525 526 529 540 doublescan +hsync -vsync (64.7 kHz d)
[  6437.272] (II) modeset(G0): Modeline "800x512"x60.2   51.56  800 800 828 832  512 512 514 515 doublescan +hsync +vsync (62.0 kHz d)
[  6437.272] (II) modeset(G0): Modeline "700x525"x74.8   77.90  700 732 892 956  525 526 532 545 doublescan +hsync +vsync (81.5 kHz d)
[  6437.272] (II) modeset(G0): Modeline "700x525"x70.1   72.53  700 748 824 948  525 525 527 546 doublescan -hsync +vsync (76.5 kHz d)
[  6437.272] (II) modeset(G0): Modeline "700x525"x60.0   61.00  700 744 820 940  525 526 532 541 doublescan +hsync +vsync (64.9 kHz d)
[  6437.272] (II) modeset(G0): Modeline "640x512"x75.0   67.50  640 648 720 844  512 512 514 533 doublescan +hsync +vsync (80.0 kHz d)
[  6437.272] (II) modeset(G0): Modeline "640x512"x60.0   54.00  640 664 720 844  512 512 514 533 doublescan +hsync +vsync (64.0 kHz d)
[  6437.272] (II) modeset(G0): Modeline "720x450"x59.9   53.25  720 760 836 952  450 451 454 467 doublescan -hsync +vsync (55.9 kHz d)
[  6437.272] (II) modeset(G0): Modeline "640x480"x60.0   54.00  640 688 744 900  480 480 482 500 doublescan +hsync +vsync (60.0 kHz d)
[  6437.272] (II) modeset(G0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[  6437.272] (II) modeset(G0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz d)
[  6437.272] (II) modeset(G0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz d)
[  6437.272] (II) modeset(G0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[  6437.272] (II) modeset(G0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[  6437.272] (II) modeset(G0): Modeline "680x384"x59.8   42.38  680 716 784 888  384 385 390 399 doublescan -hsync +vsync (47.7 kHz d)
[  6437.272] (II) modeset(G0): Modeline "680x384"x60.0   36.00  680 704 720 760  384 385 390 395 doublescan +hsync -vsync (47.4 kHz d)
[  6437.272] (II) modeset(G0): Modeline "576x432"x75.0   54.00  576 608 672 800  432 432 434 450 doublescan +hsync +vsync (67.5 kHz d)
[  6437.272] (II) modeset(G0): Modeline "576x432"x75.0   52.49  576 612 676 776  432 432 434 451 doublescan -hsync +vsync (67.6 kHz d)
[  6437.272] (II) modeset(G0): Modeline "576x432"x70.0   48.38  576 612 672 768  432 432 434 450 doublescan -hsync +vsync (63.0 kHz d)
[  6437.272] (II) modeset(G0): Modeline "576x432"x60.1   40.81  576 608 668 760  432 432 434 447 doublescan -hsync +vsync (53.7 kHz d)
[  6437.272] (II) modeset(G0): Modeline "512x384"x75.0   39.38  512 520 568 656  384 384 386 400 doublescan +hsync +vsync (60.0 kHz d)
[  6437.272] (II) modeset(G0): Modeline "512x384"x70.1   37.50  512 524 592 664  384 385 388 403 doublescan -hsync -vsync (56.5 kHz d)
[  6437.272] (II) modeset(G0): Modeline "512x384"x60.0   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync (48.4 kHz d)
[  6437.272] (II) modeset(G0): Modeline "416x312"x74.7   28.64  416 432 464 576  312 312 314 333 doublescan -hsync -vsync (49.7 kHz d)
[  6437.272] (II) modeset(G0): Modeline "400x300"x72.2   25.00  400 428 488 520  300 318 321 333 doublescan +hsync +vsync (48.1 kHz d)
[  6437.272] (II) modeset(G0): Modeline "400x300"x75.1   24.75  400 408 448 528  300 300 302 312 doublescan +hsync +vsync (46.9 kHz d)
[  6437.272] (II) modeset(G0): Modeline "400x300"x60.3   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz d)
[  6437.272] (II) modeset(G0): Modeline "400x300"x56.3   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (35.2 kHz d)
[  6437.272] (II) modeset(G0): Modeline "320x240"x72.8   15.75  320 332 352 416  240 244 246 260 doublescan -hsync -vsync (37.9 kHz d)
[  6437.272] (II) modeset(G0): Modeline "320x240"x75.0   15.75  320 328 360 420  240 240 242 250 doublescan -hsync -vsync (37.5 kHz d)
[  6437.272] (II) modeset(G0): Modeline "320x240"x60.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz d)
[  6437.336] (II) modeset(G0): EDID for output DP-2
[  6437.400] (II) modeset(G0): EDID for output DP-3
[  6437.400] (II) modeset(G0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[  6437.400] (==) modeset(G0): DPI set to (96, 96)
[  6437.400] (II) Loading sub module "fb"
[  6437.400] (II) LoadModule: "fb"
[  6437.400] (II) Loading /usr/lib/xorg/modules/libfb.so
[  6437.400] (II) Module fb: vendor="X.Org Foundation"
[  6437.400]     compiled for 1.18.3, module version = 1.0.0
[  6437.400]     ABI class: X.Org ANSI C Emulation, version 0.4
[  6437.400] (II) UnloadModule: "fbdev"
[  6437.400] (II) Unloading fbdev
[  6437.400] (II) UnloadSubModule: "fbdevhw"
[  6437.400] (II) Unloading fbdevhw
[  6437.400] (II) UnloadModule: "vesa"
[  6437.400] (II) Unloading vesa
[  6437.400] (==) Depth 24 pixmap format is 32 bpp
[  6437.435] (==) modeset(G0): Backing store enabled
[  6437.435] (==) modeset(G0): Silken mouse enabled
[  6437.435] (II) modeset(G0): RandR 1.2 enabled, ignore the following RandR disabled message.
[  6437.463] (==) modeset(G0): DPMS enabled
[  6437.463] (II) modeset(G0): [DRI2] Setup complete
[  6437.463] (II) modeset(G0): [DRI2]   DRI driver: nouveau
[  6437.463] (II) modeset(G0): [DRI2]   VDPAU driver: nouveau
[  6437.530] (II) intel(0): SNA initialized with generic backend
[  6437.531] (==) intel(0): Backing store enabled
[  6437.531] (==) intel(0): Silken mouse enabled
[  6437.531] (II) intel(0): HW Cursor enabled
[  6437.531] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[  6437.531] (==) intel(0): DPMS enabled
[  6437.531] (==) intel(0): Display hotplug detection enabled
[  6437.531] (II) intel(0): Textured video not supported on this hardware or backend
[  6437.531] (II) intel(0): [DRI2] Setup complete
[  6437.531] (II) intel(0): [DRI2]   DRI driver: i965
[  6437.531] (II) intel(0): [DRI2]   VDPAU driver: va_gl
[  6437.531] (II) intel(0): direct rendering: DRI2 enabled
[  6437.531] (II) intel(0): hardware support for Present enabled
[  6437.531] (--) RandR disabled
[  6437.533] (II) SELinux: Disabled on system
[  6437.537] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[  6437.537] (II) AIGLX: enabled GLX_ARB_create_context
[  6437.537] (II) AIGLX: enabled GLX_ARB_create_context_profile
[  6437.537] (II) AIGLX: enabled GLX_EXT_create_context_es{,2}_profile
[  6437.537] (II) AIGLX: enabled GLX_INTEL_swap_event
[  6437.537] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[  6437.537] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[  6437.537] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[  6437.537] (II) AIGLX: enabled GLX_EXT_fbconfig_packed_float
[  6437.537] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[  6437.537] (II) AIGLX: enabled GLX_ARB_create_context_robustness
[  6437.537] (II) AIGLX: Loaded and initialized i965
[  6437.537] (II) GLX: Initialized DRI2 GL provider for screen 0
[  6437.538] (II) modeset(G0): Damage tracking initialized
[  6437.540] (II) intel(0): switch to mode 1920x1080@60.0 on eDP1 using pipe 0, position (0, 0), rotation normal, reflection none
[  6437.540] (II) intel(0): Setting screen physical size to 508 x 285
[  6437.558] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[  6437.558] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  6437.558] (II) LoadModule: "evdev"
[  6437.559] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  6437.559] (II) Module evdev: vendor="X.Org Foundation"
[  6437.559]     compiled for 1.18.1, module version = 2.10.1
[  6437.559]     Module class: X.Org XInput Driver
[  6437.559]     ABI class: X.Org XInput driver, version 22.1
[  6437.559] (II) Using input driver 'evdev' for 'Power Button'
[  6437.559] (**) Power Button: always reports core events
[  6437.559] (**) evdev: Power Button: Device: "/dev/input/event2"
[  6437.559] (--) evdev: Power Button: Vendor 0 Product 0x1
[  6437.559] (--) evdev: Power Button: Found keys
[  6437.559] (II) evdev: Power Button: Configuring as keyboard
[  6437.559] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[  6437.559] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[  6437.559] (**) Option "xkb_rules" "evdev"
[  6437.559] (**) Option "xkb_model" "pc105"
[  6437.559] (**) Option "xkb_layout" "us"
[  6437.559] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[  6437.559] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[  6437.559] (II) Using input driver 'evdev' for 'Video Bus'
[  6437.559] (**) Video Bus: always reports core events
[  6437.559] (**) evdev: Video Bus: Device: "/dev/input/event5"
[  6437.559] (--) evdev: Video Bus: Vendor 0 Product 0x6
[  6437.559] (--) evdev: Video Bus: Found keys
[  6437.559] (II) evdev: Video Bus: Configuring as keyboard
[  6437.559] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input7/event5"
[  6437.559] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[  6437.559] (**) Option "xkb_rules" "evdev"
[  6437.559] (**) Option "xkb_model" "pc105"
[  6437.559] (**) Option "xkb_layout" "us"
[  6437.559] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[  6437.559] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[  6437.560] (II) Using input driver 'evdev' for 'Video Bus'
[  6437.560] (**) Video Bus: always reports core events
[  6437.560] (**) evdev: Video Bus: Device: "/dev/input/event4"
[  6437.560] (--) evdev: Video Bus: Vendor 0 Product 0x6
[  6437.560] (--) evdev: Video Bus: Found keys
[  6437.560] (II) evdev: Video Bus: Configuring as keyboard
[  6437.560] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input6/event4"
[  6437.560] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 8)
[  6437.560] (**) Option "xkb_rules" "evdev"
[  6437.560] (**) Option "xkb_model" "pc105"
[  6437.560] (**) Option "xkb_layout" "us"
[  6437.560] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[  6437.560] (II) No input driver specified, ignoring this device.
[  6437.560] (II) This device may have been added with another device file.
[  6437.560] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[  6437.560] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[  6437.560] (II) Using input driver 'evdev' for 'Sleep Button'
[  6437.560] (**) Sleep Button: always reports core events
[  6437.560] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[  6437.560] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[  6437.560] (--) evdev: Sleep Button: Found keys
[  6437.560] (II) evdev: Sleep Button: Configuring as keyboard
[  6437.560] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1/event1"
[  6437.560] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[  6437.560] (**) Option "xkb_rules" "evdev"
[  6437.560] (**) Option "xkb_model" "pc105"
[  6437.560] (**) Option "xkb_layout" "us"
[  6437.561] (II) config/udev: Adding input device Wacom Co.,Ltd. Pen and multitouch sensor Finger (/dev/input/event9)
[  6437.561] (**) Wacom Co.,Ltd. Pen and multitouch sensor Finger: Applying InputClass "evdev touchscreen catchall"
[  6437.561] (**) Wacom Co.,Ltd. Pen and multitouch sensor Finger: Applying InputClass "Wacom USB device class"
[  6437.561] (**) Wacom Co.,Ltd. Pen and multitouch sensor Finger: Applying InputClass "Wacom class"
[  6437.561] (II) LoadModule: "wacom"
[  6437.561] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[  6437.561] (II) Module wacom: vendor="X.Org Foundation"
[  6437.561]     compiled for 1.18.1, module version = 0.32.0
[  6437.561]     Module class: X.Org XInput Driver
[  6437.561]     ABI class: X.Org XInput driver, version 22.1
[  6437.561] (II) wacom: Driver for Wacom graphics tablets: PenPartner, Graphire,
    Graphire2 4x5, Graphire2 5x7, Graphire3 4x5, Graphire3 6x8,
    Graphire4 4x5, Graphire4 6x8, BambooFun 4x5, BambooFun 6x8,
    Bamboo1 Medium, Graphire4 6x8 BlueTooth, CTL-460, CTH-461, CTL-660,
    CTL-461/S, Bamboo Touch, CTH-460/K, CTH-461/S, CTH-661/S1, CTH-461/L,
    CTH-661/L, Intuos 4x5, Intuos 6x8, Intuos 9x12, Intuos 12x12,
    Intuos 12x18, PTU600, PL400, PL500, PL600, PL600SX, PL550, PL800,
    PL700, PL510, PL710, DTI520, DTF720, DTF720a, DTF521, DTU1931,
    DTU2231, DTU1631, Intuos2 4x5, Intuos2 6x8, Intuos2 9x12,
    Intuos2 12x12, Intuos2 12x18, Intuos2 6x8 , Volito, PenStation,
    Volito2 4x5, Volito2 2x3, PenPartner2, Bamboo, Bamboo1, Bamboo1 4x6,
    Bamboo1 5x8, Intuos3 4x5, Intuos3 6x8, Intuos3 9x12, Intuos3 12x12,
    Intuos3 12x19, Intuos3 6x11, Intuos3 4x6, Intuos4 4x6, Intuos4 6x9,
    Intuos4 8x13, Intuos4 12x19, Intuos4 WL USB Endpoint,
    Intuos4 WL Bluetooth Endpoint, Intuos5 touch S, Intuos5 touch M,
    Intuos5 touch L, Intuos5 S, Intuos5 M, Intuos Pro S, Intuos Pro M,
    Intuos Pro L, Cintiq 21UX, Cintiq 20WSX, Cintiq 12WX, Cintiq 21UX2,
    Cintiq 24HD, Cintiq 22HD, Cintiq 24HD touch (EMR digitizer),
    Cintiq 13HD, DTK2241, DTH2242, Cintiq 22HDT, TabletPC 0x90,
    TabletPC 0x93, TabletPC 0x97, TabletPC 0x9A, CapPlus  0x9F,
    TabletPC 0xE2, TabletPC 0xE3, TabletPC 0xE5, TabletPC 0xE6,
    TabletPC 0xEC, TabletPC 0xED, TabletPC 0xEF, TabletPC 0x100,
    TabletPC 0x101, TabletPC 0x10D, TabletPC 0x116, TabletPC 0x12C,
    TabletPC 0x4001, TabletPC 0x4004, TabletPC 0x5000, TabletPC 0x5002,
    usb:172f:0024, usb:172f:0025, usb:172f:0026, usb:172f:0027,
    usb:172f:0028, usb:172f:0030, usb:172f:0031, usb:172f:0032,
    usb:172f:0033, usb:172f:0034, usb:172f:0035, usb:172f:0036,
    usb:172f:0037, usb:172f:0038, usb:172f:0039, usb:172f:0051,
    usb:172f:0052, usb:172f:0053, usb:172f:0054, usb:172f:0055,
    usb:172f:0056, usb:172f:0057, usb:172f:0058, usb:172f:0500,
    usb:172f:0501, usb:172f:0502, usb:172f:0503, usb:1b96:0001,
    usb:17ef:6004
[  6437.561] (II) Using input driver 'wacom' for 'Wacom Co.,Ltd. Pen and multitouch sensor Finger'
[  6437.561] (**) Wacom Co.,Ltd. Pen and multitouch sensor Finger: always reports core events
[  6437.561] (**) Option "Device" "/dev/input/event9"
[  6437.616] (EE) Wacom Co.,Ltd. Pen and multitouch sensor Finger: Invalid type 'stylus' for this device.
[  6437.616] (EE) Wacom Co.,Ltd. Pen and multitouch sensor Finger: Invalid type 'eraser' for this device.
[  6437.616] (EE) Wacom Co.,Ltd. Pen and multitouch sensor Finger: Invalid type 'cursor' for this device.
[  6437.616] (II) Wacom Co.,Ltd. Pen and multitouch sensor Finger: type not specified, assuming 'touch'.
[  6437.616] (II) Wacom Co.,Ltd. Pen and multitouch sensor Finger: other types will be automatically added.
[  6437.616] (--) Wacom Co.,Ltd. Pen and multitouch sensor Finger touch: maxX=13768 maxY=7744 maxZ=0 resX=40000 resY=40000 
[  6437.616] (II) Wacom Co.,Ltd. Pen and multitouch sensor Finger touch: hotplugging dependent devices.
[  6437.616] (EE) Wacom Co.,Ltd. Pen and multitouch sensor Finger touch: Invalid type 'stylus' for this device.
[  6437.616] (EE) Wacom Co.,Ltd. Pen and multitouch sensor Finger touch: Invalid type 'eraser' for this device.
[  6437.616] (EE) Wacom Co.,Ltd. Pen and multitouch sensor Finger touch: Invalid type 'cursor' for this device.
[  6437.616] (EE) Wacom Co.,Ltd. Pen and multitouch sensor Finger touch: Invalid type 'pad' for this device.
[  6437.616] (II) Wacom Co.,Ltd. Pen and multitouch sensor Finger touch: hotplugging completed.
[  6437.644] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-10/1-10:1.0/0003:056A:5053.0005/input/input11/event9"
[  6437.644] (II) XINPUT: Adding extended input device "Wacom Co.,Ltd. Pen and multitouch sensor Finger touch" (type: TOUCH, id 10)
[  6437.645] (**) Wacom Co.,Ltd. Pen and multitouch sensor Finger touch: (accel) keeping acceleration scheme 1
[  6437.645] (**) Wacom Co.,Ltd. Pen and multitouch sensor Finger touch: (accel) acceleration profile 0
[  6437.645] (**) Wacom Co.,Ltd. Pen and multitouch sensor Finger touch: (accel) acceleration factor: 2.000
[  6437.645] (**) Wacom Co.,Ltd. Pen and multitouch sensor Finger touch: (accel) acceleration threshold: 4
[  6437.701] (II) config/udev: Adding input device Wacom Co.,Ltd. Pen and multitouch sensor Finger (/dev/input/mouse3)
[  6437.701] (II) No input driver specified, ignoring this device.
[  6437.701] (II) This device may have been added with another device file.
[  6437.702] (II) config/udev: Adding input device Wacom Co.,Ltd. Pen and multitouch sensor Pen (/dev/input/event10)
[  6437.702] (**) Wacom Co.,Ltd. Pen and multitouch sensor Pen: Applying InputClass "evdev tablet catchall"
[  6437.702] (**) Wacom Co.,Ltd. Pen and multitouch sensor Pen: Applying InputClass "Wacom USB device class"
[  6437.702] (**) Wacom Co.,Ltd. Pen and multitouch sensor Pen: Applying InputClass "Wacom class"
[  6437.702] (II) Using input driver 'wacom' for 'Wacom Co.,Ltd. Pen and multitouch sensor Pen'
[  6437.702] (**) Wacom Co.,Ltd. Pen and multitouch sensor Pen: always reports core events
[  6437.702] (**) Option "Device" "/dev/input/event10"
[  6437.756] (II) Wacom Co.,Ltd. Pen and multitouch sensor Pen: type not specified, assuming 'stylus'.
[  6437.756] (II) Wacom Co.,Ltd. Pen and multitouch sensor Pen: other types will be automatically added.
[  6437.756] (--) Wacom Co.,Ltd. Pen and multitouch sensor Pen stylus: using pressure threshold of 27 for button 1
[  6437.756] (--) Wacom Co.,Ltd. Pen and multitouch sensor Pen stylus: maxX=34416 maxY=19359 maxZ=2047 resX=100000 resY=100000  tilt=enabled
[  6437.756] (II) Wacom Co.,Ltd. Pen and multitouch sensor Pen stylus: hotplugging dependent devices.
[  6437.756] (EE) Wacom Co.,Ltd. Pen and multitouch sensor Pen stylus: Invalid type 'cursor' for this device.
[  6437.756] (EE) Wacom Co.,Ltd. Pen and multitouch sensor Pen stylus: Invalid type 'touch' for this device.
[  6437.756] (EE) Wacom Co.,Ltd. Pen and multitouch sensor Pen stylus: Invalid type 'pad' for this device.
[  6437.756] (II) Wacom Co.,Ltd. Pen and multitouch sensor Pen stylus: hotplugging completed.
[  6437.780] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-10/1-10:1.1/0003:056A:5053.0006/input/input13/event10"
[  6437.780] (II) XINPUT: Adding extended input device "Wacom Co.,Ltd. Pen and multitouch sensor Pen stylus" (type: STYLUS, id 11)
[  6437.781] (**) Wacom Co.,Ltd. Pen and multitouch sensor Pen stylus: (accel) keeping acceleration scheme 1
[  6437.781] (**) Wacom Co.,Ltd. Pen and multitouch sensor Pen stylus: (accel) acceleration profile 0
[  6437.781] (**) Wacom Co.,Ltd. Pen and multitouch sensor Pen stylus: (accel) acceleration factor: 2.000
[  6437.781] (**) Wacom Co.,Ltd. Pen and multitouch sensor Pen stylus: (accel) acceleration threshold: 4
[  6437.837] (II) config/udev: Adding input device Wacom Co.,Ltd. Pen and multitouch sensor Pen (/dev/input/mouse4)
[  6437.837] (II) No input driver specified, ignoring this device.
[  6437.837] (II) This device may have been added with another device file.
[  6437.838] (II) config/udev: Adding input device Logitech K750 (/dev/input/event11)
[  6437.838] (**) Logitech K750: Applying InputClass "evdev keyboard catchall"
[  6437.838] (II) Using input driver 'evdev' for 'Logitech K750'
[  6437.838] (**) Logitech K750: always reports core events
[  6437.838] (**) evdev: Logitech K750: Device: "/dev/input/event11"
[  6437.839] (--) evdev: Logitech K750: Vendor 0x46d Product 0x4002
[  6437.839] (--) evdev: Logitech K750: Found 1 mouse buttons
[  6437.839] (--) evdev: Logitech K750: Found scroll wheel(s)
[  6437.839] (--) evdev: Logitech K750: Found relative axes
[  6437.839] (II) evdev: Logitech K750: Forcing relative x/y axes to exist.
[  6437.839] (--) evdev: Logitech K750: Found absolute axes
[  6437.839] (II) evdev: Logitech K750: Forcing absolute x/y axes to exist.
[  6437.839] (--) evdev: Logitech K750: Found keys
[  6437.839] (II) evdev: Logitech K750: Configuring as mouse
[  6437.839] (II) evdev: Logitech K750: Configuring as keyboard
[  6437.839] (II) evdev: Logitech K750: Adding scrollwheel support
[  6437.839] (**) evdev: Logitech K750: YAxisMapping: buttons 4 and 5
[  6437.839] (**) evdev: Logitech K750: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  6437.839] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2:1.2/0003:046D:C52B.0003/0003:046D:4002.0008/input/input16/event11"
[  6437.839] (II) XINPUT: Adding extended input device "Logitech K750" (type: KEYBOARD, id 12)
[  6437.839] (**) Option "xkb_rules" "evdev"
[  6437.839] (**) Option "xkb_model" "pc105"
[  6437.839] (**) Option "xkb_layout" "us"
[  6437.839] (II) evdev: Logitech K750: initialized for relative axes.
[  6437.839] (WW) evdev: Logitech K750: ignoring absolute axes.
[  6437.840] (**) Logitech K750: (accel) keeping acceleration scheme 1
[  6437.840] (**) Logitech K750: (accel) acceleration profile 0
[  6437.840] (**) Logitech K750: (accel) acceleration factor: 2.000
[  6437.840] (**) Logitech K750: (accel) acceleration threshold: 4
[  6437.841] (II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/event8)
[  6437.841] (**) Logitech USB-PS/2 Optical Mouse: Applying InputClass "evdev pointer catchall"
[  6437.841] (II) Using input driver 'evdev' for 'Logitech USB-PS/2 Optical Mouse'
[  6437.841] (**) Logitech USB-PS/2 Optical Mouse: always reports core events
[  6437.841] (**) evdev: Logitech USB-PS/2 Optical Mouse: Device: "/dev/input/event8"
[  6437.896] (--) evdev: Logitech USB-PS/2 Optical Mouse: Vendor 0x46d Product 0xc03d
[  6437.896] (--) evdev: Logitech USB-PS/2 Optical Mouse: Found 3 mouse buttons
[  6437.896] (--) evdev: Logitech USB-PS/2 Optical Mouse: Found scroll wheel(s)
[  6437.896] (--) evdev: Logitech USB-PS/2 Optical Mouse: Found relative axes
[  6437.896] (--) evdev: Logitech USB-PS/2 Optical Mouse: Found x and y relative axes
[  6437.896] (II) evdev: Logitech USB-PS/2 Optical Mouse: Configuring as mouse
[  6437.896] (II) evdev: Logitech USB-PS/2 Optical Mouse: Adding scrollwheel support
[  6437.896] (**) evdev: Logitech USB-PS/2 Optical Mouse: YAxisMapping: buttons 4 and 5
[  6437.896] (**) evdev: Logitech USB-PS/2 Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  6437.896] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-5/1-5:1.0/0003:046D:C03D.0004/input/input9/event8"
[  6437.896] (II) XINPUT: Adding extended input device "Logitech USB-PS/2 Optical Mouse" (type: MOUSE, id 13)
[  6437.896] (II) evdev: Logitech USB-PS/2 Optical Mouse: initialized for relative axes.
[  6437.897] (**) Logitech USB-PS/2 Optical Mouse: (accel) keeping acceleration scheme 1
[  6437.897] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration profile 0
[  6437.897] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration factor: 2.000
[  6437.897] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration threshold: 4
[  6437.898] (II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/mouse2)
[  6437.898] (II) No input driver specified, ignoring this device.
[  6437.898] (II) This device may have been added with another device file.
[  6437.899] (II) config/udev: Adding input device Integrated Camera (/dev/input/event13)
[  6437.899] (**) Integrated Camera: Applying InputClass "evdev keyboard catchall"
[  6437.899] (II) Using input driver 'evdev' for 'Integrated Camera'
[  6437.899] (**) Integrated Camera: always reports core events
[  6437.899] (**) evdev: Integrated Camera: Device: "/dev/input/event13"
[  6437.899] (--) evdev: Integrated Camera: Vendor 0x5986 Product 0x706
[  6437.899] (--) evdev: Integrated Camera: Found keys
[  6437.899] (II) evdev: Integrated Camera: Configuring as keyboard
[  6437.899] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-8/1-8:1.0/input/input18/event13"
[  6437.899] (II) XINPUT: Adding extended input device "Integrated Camera" (type: KEYBOARD, id 14)
[  6437.899] (**) Option "xkb_rules" "evdev"
[  6437.899] (**) Option "xkb_model" "pc105"
[  6437.899] (**) Option "xkb_layout" "us"
[  6437.900] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event14)
[  6437.900] (II) No input driver specified, ignoring this device.
[  6437.900] (II) This device may have been added with another device file.
[  6437.901] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event15)
[  6437.901] (II) No input driver specified, ignoring this device.
[  6437.901] (II) This device may have been added with another device file.
[  6437.901] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[  6437.901] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[  6437.902] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[  6437.902] (**) AT Translated Set 2 keyboard: always reports core events
[  6437.902] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[  6437.902] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[  6437.902] (--) evdev: AT Translated Set 2 keyboard: Found keys
[  6437.902] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[  6437.902] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[  6437.902] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 15)
[  6437.902] (**) Option "xkb_rules" "evdev"
[  6437.902] (**) Option "xkb_model" "pc105"
[  6437.902] (**) Option "xkb_layout" "us"
[  6437.903] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event6)
[  6437.903] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[  6437.903] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchscreen catchall"
[  6437.903] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[  6437.903] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[  6437.903] (II) LoadModule: "synaptics"
[  6437.903] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[  6437.904] (II) Module synaptics: vendor="X.Org Foundation"
[  6437.904]     compiled for 1.18.1, module version = 1.8.2
[  6437.904]     Module class: X.Org XInput Driver
[  6437.904]     ABI class: X.Org XInput driver, version 22.1
[  6437.904] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[  6437.904] (**) SynPS/2 Synaptics TouchPad: always reports core events
[  6437.904] (**) Option "Device" "/dev/input/event6"
[  6437.964] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1266 - 5676 (res 45)
[  6437.964] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1100 - 4754 (res 68)
[  6437.964] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[  6437.964] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[  6437.964] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right middle double triple
[  6437.964] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[  6437.964] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[  6437.964] (**) SynPS/2 Synaptics TouchPad: always reports core events
[  6437.988] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input5/event6"
[  6437.988] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 16)
[  6437.988] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[  6437.988] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[  6437.988] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.035
[  6437.989] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[  6437.989] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[  6437.989] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[  6437.989] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[  6437.989] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[  6437.990] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[  6437.990] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[  6437.990] (II) config/udev: Adding input device TPPS/2 IBM TrackPoint (/dev/input/event7)
[  6437.990] (**) TPPS/2 IBM TrackPoint: Applying InputClass "evdev pointer catchall"
[  6437.990] (**) TPPS/2 IBM TrackPoint: Applying InputClass "trackpoint catchall"
[  6437.990] (II) Using input driver 'evdev' for 'TPPS/2 IBM TrackPoint'
[  6437.990] (**) TPPS/2 IBM TrackPoint: always reports core events
[  6437.990] (**) evdev: TPPS/2 IBM TrackPoint: Device: "/dev/input/event7"
[  6437.991] (--) evdev: TPPS/2 IBM TrackPoint: Vendor 0x2 Product 0xa
[  6437.991] (--) evdev: TPPS/2 IBM TrackPoint: Found 3 mouse buttons
[  6437.991] (--) evdev: TPPS/2 IBM TrackPoint: Found relative axes
[  6437.991] (--) evdev: TPPS/2 IBM TrackPoint: Found x and y relative axes
[  6437.991] (II) evdev: TPPS/2 IBM TrackPoint: Configuring as mouse
[  6437.991] (**) Option "Emulate3Buttons" "true"
[  6437.991] (**) Option "EmulateWheel" "true"
[  6437.991] (**) Option "EmulateWheelButton" "2"
[  6437.991] (**) Option "YAxisMapping" "4 5"
[  6437.991] (**) evdev: TPPS/2 IBM TrackPoint: YAxisMapping: buttons 4 and 5
[  6437.991] (**) Option "XAxisMapping" "6 7"
[  6437.991] (**) evdev: TPPS/2 IBM TrackPoint: XAxisMapping: buttons 6 and 7
[  6437.991] (**) evdev: TPPS/2 IBM TrackPoint: EmulateWheelButton: 2, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  6437.991] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/serio2/input/input8/event7"
[  6437.991] (II) XINPUT: Adding extended input device "TPPS/2 IBM TrackPoint" (type: MOUSE, id 17)
[  6437.991] (II) evdev: TPPS/2 IBM TrackPoint: initialized for relative axes.
[  6437.991] (**) TPPS/2 IBM TrackPoint: (accel) keeping acceleration scheme 1
[  6437.991] (**) TPPS/2 IBM TrackPoint: (accel) acceleration profile 0
[  6437.991] (**) TPPS/2 IBM TrackPoint: (accel) acceleration factor: 2.000
[  6437.991] (**) TPPS/2 IBM TrackPoint: (accel) acceleration threshold: 4
[  6437.992] (II) config/udev: Adding input device TPPS/2 IBM TrackPoint (/dev/input/mouse1)
[  6437.992] (II) No input driver specified, ignoring this device.
[  6437.992] (II) This device may have been added with another device file.
[  6437.995] (II) config/udev: Adding input device ThinkPad Extra Buttons (/dev/input/event12)
[  6437.996] (**) ThinkPad Extra Buttons: Applying InputClass "evdev keyboard catchall"
[  6437.996] (II) Using input driver 'evdev' for 'ThinkPad Extra Buttons'
[  6437.996] (**) ThinkPad Extra Buttons: always reports core events
[  6437.996] (**) evdev: ThinkPad Extra Buttons: Device: "/dev/input/event12"
[  6437.996] (--) evdev: ThinkPad Extra Buttons: Vendor 0x17aa Product 0x5054
[  6437.996] (--) evdev: ThinkPad Extra Buttons: Found keys
[  6437.996] (II) evdev: ThinkPad Extra Buttons: Configuring as keyboard
[  6437.996] (**) Option "config_info" "udev:/sys/devices/platform/thinkpad_acpi/input/input17/event12"
[  6437.996] (II) XINPUT: Adding extended input device "ThinkPad Extra Buttons" (type: KEYBOARD, id 18)
[  6437.996] (**) Option "xkb_rules" "evdev"
[  6437.996] (**) Option "xkb_model" "pc105"
[  6437.996] (**) Option "xkb_layout" "us"
[  6438.007] (**) Wacom Co.,Ltd. Pen and multitouch sensor Pen eraser: Applying InputClass "evdev tablet catchall"
[  6438.007] (**) Wacom Co.,Ltd. Pen and multitouch sensor Pen eraser: Applying InputClass "Wacom USB device class"
[  6438.007] (**) Wacom Co.,Ltd. Pen and multitouch sensor Pen eraser: Applying InputClass "Wacom class"
[  6438.007] (II) Using input driver 'wacom' for 'Wacom Co.,Ltd. Pen and multitouch sensor Pen eraser'
[  6438.007] (**) Wacom Co.,Ltd. Pen and multitouch sensor Pen eraser: always reports core events
[  6438.007] (**) Option "Device" "/dev/input/event10"
[  6438.007] (**) Option "Type" "eraser"
[  6438.007] (--) Wacom Co.,Ltd. Pen and multitouch sensor Pen eraser: maxX=34416 maxY=19359 maxZ=2047 resX=100000 resY=100000  tilt=enabled
[  6438.024] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-10/1-10:1.1/0003:056A:5053.0006/input/input13/event10"
[  6438.024] (II) XINPUT: Adding extended input device "Wacom Co.,Ltd. Pen and multitouch sensor Pen eraser" (type: ERASER, id 19)
[  6438.025] (**) Wacom Co.,Ltd. Pen and multitouch sensor Pen eraser: (accel) keeping acceleration scheme 1
[  6438.025] (**) Wacom Co.,Ltd. Pen and multitouch sensor Pen eraser: (accel) acceleration profile 0
[  6438.025] (**) Wacom Co.,Ltd. Pen and multitouch sensor Pen eraser: (accel) acceleration factor: 2.000
[  6438.025] (**) Wacom Co.,Ltd. Pen and multitouch sensor Pen eraser: (accel) acceleration threshold: 4
[  6438.390] (II) intel(0): EDID vendor "BOE", prod id 1584
[  6438.390] (II) intel(0): Printing DDC gathered Modelines:
[  6438.390] (II) intel(0): Modeline "1920x1080"x0.0  141.40  1920 1968 2000 2142  1080 1083 1089 1100 +hsync -vsync (66.0 kHz eP)
[  6438.524] (II) modeset(G0): EDID vendor "DEL", prod id 53264
[  6438.524] (II) modeset(G0): Using hsync ranges from config file
[  6438.524] (II) modeset(G0): Using vrefresh ranges from config file
[  6438.524] (II) modeset(G0): Printing DDC gathered Modelines:
[  6438.524] (II) modeset(G0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz eP)
[  6438.524] (II) modeset(G0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[  6438.524] (II) modeset(G0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[  6438.524] (II) modeset(G0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[  6438.524] (II) modeset(G0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[  6438.524] (II) modeset(G0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[  6438.524] (II) modeset(G0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[  6438.524] (II) modeset(G0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[  6438.524] (II) modeset(G0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[  6438.524] (II) modeset(G0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[  6438.524] (II) modeset(G0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[  6438.696] (II) intel(0): resizing framebuffer to 3600x1080
[  6438.712] (II) modeset(G0): Allocate new frame buffer 1680x1050 stride
[  6438.820] (II) modeset(G0): Disabling kernel dirty updates, not required.
[  6439.009] (II) modeset(G0): EDID vendor "DEL", prod id 53264
[  6439.009] (II) modeset(G0): Using hsync ranges from config file
[  6439.009] (II) modeset(G0): Using vrefresh ranges from config file
[  6439.009] (II) modeset(G0): Printing DDC gathered Modelines:
[  6439.009] (II) modeset(G0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz eP)
[  6439.009] (II) modeset(G0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[  6439.009] (II) modeset(G0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[  6439.009] (II) modeset(G0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[  6439.009] (II) modeset(G0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[  6439.009] (II) modeset(G0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[  6439.009] (II) modeset(G0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[  6439.009] (II) modeset(G0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[  6439.009] (II) modeset(G0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[  6439.009] (II) modeset(G0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[  6439.009] (II) modeset(G0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[  6445.879] (II) modeset(G0): EDID vendor "DEL", prod id 53264
[  6445.879] (II) modeset(G0): Using hsync ranges from config file
[  6445.879] (II) modeset(G0): Using vrefresh ranges from config file
[  6445.879] (II) modeset(G0): Printing DDC gathered Modelines:
[  6445.879] (II) modeset(G0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz eP)
[  6445.879] (II) modeset(G0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[  6445.879] (II) modeset(G0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[  6445.879] (II) modeset(G0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[  6445.879] (II) modeset(G0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[  6445.879] (II) modeset(G0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[  6445.879] (II) modeset(G0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[  6445.879] (II) modeset(G0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[  6445.879] (II) modeset(G0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[  6445.879] (II) modeset(G0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[  6445.879] (II) modeset(G0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[  6446.047] (II) intel(0): resizing framebuffer to 3600x1110
[  6447.047] (II) modeset(G0): EDID vendor "DEL", prod id 53264
[  6447.047] (II) modeset(G0): Using hsync ranges from config file
[  6447.047] (II) modeset(G0): Using vrefresh ranges from config file
[  6447.047] (II) modeset(G0): Printing DDC gathered Modelines:
[  6447.047] (II) modeset(G0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz eP)
[  6447.047] (II) modeset(G0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[  6447.047] (II) modeset(G0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[  6447.047] (II) modeset(G0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[  6447.047] (II) modeset(G0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[  6447.047] (II) modeset(G0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[  6447.047] (II) modeset(G0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[  6447.047] (II) modeset(G0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[  6447.047] (II) modeset(G0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[  6447.047] (II) modeset(G0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[  6447.047] (II) modeset(G0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)

```

```

qxd@qxd-QC5-Ubuntu:~$ sudo lshw -C display
  *-display               
       description: VGA compatible controller
       product: GM107GLM [Quadro M1000M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:131 memory:c3000000-c3ffffff memory:b0000000-bfffffff memory:c0000000-c1ffffff ioport:4000(size=128) memory:c4000000-c407ffff
  *-display
       description: VGA compatible controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:132 memory:c2000000-c2ffffff memory:60000000-6fffffff ioport:5000(size=64) memory:c0000-dffff

```

I am using the kernel 4.6.0--rc5 for better power management (my P50 workstation has two fans and Skylake CPUs).

---

### Post by Bashing-om on 2016-05-03
i2000s2; Hello;

I will join you in this thread. See what we can do.
You have from the log file:
> 
6436.783] (II) LoadModule: "nvidia"
[  6436.783] (WW) Warning, couldn't open module nvidia
[  6436.783] (II) UnloadModule: "nvidia"
[  6436.783] (II) Unloading nvidia
[  6436.783] (EE) Failed to load module "nvidia" (module does not exist, 0)

Which says in essence that the driver did not build .

So the question is what prevents it from building ?
What might be in conflict ?
post back the outputs of terminal commands:
```

dpkg -l | grep -i nvidia
dkms status
lsmod | grep nvidia

```
Also confirm for me this is a notebook machine and confirm you agree:
[http://www.nvidia.com/download/driverResults.aspx/101423/en-us](http://www.nvidia.com/download/driverResults.aspx/101423/en-us)
that the 361 version is the correct driver for this machine,

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by i2000s2 on 2016-05-03
Thank you, Bashing-om, for joining me! Yes, the driver doesn't seem to be building. I think nvidia-361 is the correct driver for my Thinkpad P50 notebook from the document. Yesterday, I purged the 364 ppa and reinstalled nvidia-settings. Below is the result of running the code you gave to me:

```

qxd@qxd-QC5-Ubuntu:~/Downloads$ dpkg -l | grep -i nvidia
ii  bbswitch-dkms                               0.8-3ubuntu1                                        amd64        Interface for toggling the power on NVIDIA Optimus video cards
ii  libcuda1-361                                361.42-0ubuntu2                                     amd64        NVIDIA CUDA runtime library
ii  nvidia-361                                  361.42-0ubuntu2                                     amd64        NVIDIA binary driver - version 361.42
ii  nvidia-opencl-icd-361                       361.42-0ubuntu2                                     amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                0.8.2                                               amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                             361.42-0ubuntu1                                     amd64        Tool for configuring the NVIDIA graphics driver

```

```

qxd@qxd-QC5-Ubuntu:~/Downloads$ dkms status
bbswitch, 0.8, 4.6.0-040600rc5-generic, x86_64: installed
nvidia-361, 361.42: added
virtualbox, 5.0.18, 4.6.0-040600rc5-generic, x86_64: installed

```

```

qxd@qxd-QC5-Ubuntu:~/Downloads$ lsmod | grep nvidia

```
The last command line didn't yield any output, so the driver is not running?

---

### Post by Bashing-om on 2016-05-03
i2000s2; Hummm ...

No return from " lsmod | grep nvidia" means there is no Nvidia module on the system . Yuk .

So now what gives ? Are the headers installed in order to build the module ?
```

dpkg -l grep linux-

```

Presently, do not know
[INDENT][INDENT]but gotta be a cause
[/INDENT][/INDENT]

---

### Post by i2000s2 on 2016-05-03
Hmm, how can you tell from the headers?

```

qxd@qxd-QC5-Ubuntu:~$ dpkg -l grep linux-
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  grep           2.24-1       amd64        GNU grep, egrep and fgrep
dpkg-query: no packages found matching linux-

```

I think you meant to use a pipe: dpkg -l | grep linux-
So, I also run
```

qxd@qxd-QC5-Ubuntu:~$ dpkg -l | grep linux-
ii  linux-base                                  4.0ubuntu1                                          all          Linux image base package
ii  linux-firmware                              1.157                                               all          Firmware for Linux kernel drivers
ii  linux-generic                               4.4.0.21.22                                         amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.4.0-21                      4.4.0-21.37                                         all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-21-generic              4.4.0-21.37                                         amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.6.0-040600rc5               4.6.0-040600rc5.201604242031                        all          Header files related to Linux kernel version 4.6.0
ii  linux-headers-4.6.0-040600rc5-generic       4.6.0-040600rc5.201604242031                        amd64        Linux kernel headers for version 4.6.0 on 64 bit x86 SMP
ii  linux-headers-generic                       4.4.0.21.22                                         amd64        Generic Linux kernel headers
ii  linux-image-4.4.0-21-generic                4.4.0-21.37                                         amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.6.0-040600rc5-generic         4.6.0-040600rc5.201604242031                        amd64        Linux kernel image for version 4.6.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-21-generic          4.4.0-21.37                                         amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-generic                         4.4.0.21.22                                         amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                        4.4.0-21.37                                         amd64        Linux Kernel Headers for development
ii  linux-signed-generic                        4.4.0.21.22                                         amd64        Complete Signed Generic Linux kernel and headers
ii  linux-signed-image-4.4.0-21-generic         4.4.0-21.37                                         amd64        Signed kernel image generic
ii  linux-signed-image-generic                  4.4.0.21.22                                         amd64        Signed Generic Linux kernel image
ii  linux-sound-base                            1.0.25+dfsg-0ubuntu5                                all          base package for ALSA and OSS sound systems
ii  syslinux-common                             3:6.03+dfsg-11ubuntu1                               all          collection of bootloaders (common)
ii  syslinux-legacy                             2:3.63+dfsg-2ubuntu8                                amd64        Bootloader for Linux/i386 using MS-DOS floppies

```

I am using the 4.6.0-rc5 kernel, as I found 4.4 is not efficient on Power Management on Skylake CPUs and such.

---

### Post by Bashing-om on 2016-05-03
i2000s2; Yeah, Uh Huh;

> 
I am using the 4.6.0-rc5 kernel, as I found 4.4 is not efficient on Power Management on Skylake CPUs and such.

And the header file (linux-headers-4.6.0-040600rc5) is installed . Blows that theory out .

Back to square one, purge and install the driver afresh:
```

sudo apt purge nvidia*
sudo rm /etc/X11/xorg.conf
sudo ubuntu-drivers autoinstall

```
let's see what the system chooses to install. Watching what takes place .. looking for any generated errors .

[INDENT][INDENT]backup 2 yards
[INDENT][INDENT][INDENT]and punt
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by i2000s2 on 2016-05-03
I can confirm two things: 1. I don't have /etc/X11/xorg.conf in my system, or it has been renamed to xorg.conf.failsafe; 2. the system used the nvidia-361.42 driver as I initially used. After purging nvidia driver, the output of the other two commands are below:

```

qxd@qxd-QC5-Ubuntu:~$ sudo rm /etc/X11/xorg.conf
rm: cannot remove '/etc/X11/xorg.conf': No such file or directory
qxd@qxd-QC5-Ubuntu:~$ sudo ubuntu-drivers autoinstall
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  nvidia-opencl-icd-361 nvidia-prime nvidia-settings
The following NEW packages will be installed:
  nvidia-361 nvidia-opencl-icd-361 nvidia-prime nvidia-settings
0 upgraded, 4 newly installed, 0 to remove and 5 not upgraded.
Need to get 0 B/77.5 MB of archives.
After this operation, 339 MB of additional disk space will be used.
Selecting previously unselected package nvidia-361.
(Reading database ... 476611 files and directories currently installed.)
Preparing to unpack .../nvidia-361_361.42-0ubuntu2_amd64.deb ...
Unpacking nvidia-361 (361.42-0ubuntu2) ...
Selecting previously unselected package nvidia-opencl-icd-361.
Preparing to unpack .../nvidia-opencl-icd-361_361.42-0ubuntu2_amd64.deb ...
Unpacking nvidia-opencl-icd-361 (361.42-0ubuntu2) ...
Selecting previously unselected package nvidia-prime.
Preparing to unpack .../nvidia-prime_0.8.2_amd64.deb ...
Unpacking nvidia-prime (0.8.2) ...
Selecting previously unselected package nvidia-settings.
Preparing to unpack .../nvidia-settings_361.42-0ubuntu1_amd64.deb ...
Unpacking nvidia-settings (361.42-0ubuntu1) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
Processing triggers for ureadahead (0.100.0-19) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu3) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Setting up nvidia-361 (361.42-0ubuntu2) ...
update-alternatives: using /usr/lib/nvidia-361/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_EGL.conf (i386-linux-gnu_egl_conf) in auto mode
update-alternatives: using /usr/share/nvidia-361/glamor.conf to provide /usr/share/X11/xorg.conf.d/glamoregl.conf (glamor_conf) in auto mode
INFO:Enable nvidia-361
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
Adding system user `nvidia-persistenced' (UID 124) ...
Adding new group `nvidia-persistenced' (GID 133) ...
Adding new user `nvidia-persistenced' (UID 124) with group `nvidia-persistenced' ...
Not creating home directory `/'.
Loading new nvidia-361-361.42 DKMS files...
First Installation: checking all kernels...
Building only for 4.6.0-040600rc5-generic
Building for architecture x86_64
Building initial module for 4.6.0-040600rc5-generic
**ERROR (dkms apport): kernel package linux-headers-4.6.0-040600rc5-generic is not supported**
**Error! Bad return status for module build on kernel: 4.6.0-040600rc5-generic (x86_64)**
Consult /var/lib/dkms/nvidia-361/361.42/build/make.log for more information.
Setting up nvidia-opencl-icd-361 (361.42-0ubuntu2) ...
Setting up nvidia-prime (0.8.2) ...
Setting up nvidia-settings (361.42-0ubuntu1) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
Processing triggers for ureadahead (0.100.0-19) ...

```
Uh, seems the kernel is not supported to work with the nvidia driver...

Again, as this reinstallation was finished, there is no xorg.conf file in the folder.
```

qxd@qxd-QC5-Ubuntu:~$ ls /etc/X11/
app-defaults             rgb.txt             Xreset      Xsession.d
cursors                  xinit               Xreset.d    Xsession.options
default-display-manager  xkb                 Xresources  xsm
fonts                    xorg.conf.failsafe  Xsession    Xwrapper.config

```

Also, there is an error when I started the Xsession:
```

qxd@qxd-QC5-Ubuntu:~$ cat .xsession-errors
openConnection: connect: No such file or directory
cannot connect to brltty at :0

```
Those are the things I suspected most of... Maybe I need to try a different kernel, if this is the only cause?

---

### Post by Bashing-om on 2016-05-03
i2000s2; Yeah ...

I am of the same:
> 
Maybe I need to try a different kernel, if this is the only cause?

mind ... Can't hurt to try.

purge Nvidia once more
and boot up with the 4.4.0-21 kernel.
```

sudo ubuntu-drivers autoinstall

```

not having the xorg.conf file is expected generally . The use of that file is now depreciated as DKMS does the discovery within the kernel. It has been verified that DKMS is in effect.

reboot to see this effect ... and if acceptable .. reboot to the rc5 and let's see if the rc5 kernel will use the Nvidia driver ???

[INDENT][INDENT]best I know to try and do
[/INDENT][/INDENT]

---

### Post by i2000s2 on 2016-05-03
That sounds  like a better plan than my naive proposal. I will restart right away!

---

### Post by i2000s2 on 2016-05-03
While I am trying out connecting with the second monitor, I got some interesting result:

```

qxd@qxd-QC5-Ubuntu:~$ sudo ubuntu-drivers autoinstall
[sudo] password for qxd: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  nvidia-opencl-icd-361 nvidia-prime nvidia-settings
The following NEW packages will be installed:
  nvidia-361 nvidia-opencl-icd-361 nvidia-prime nvidia-settings
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/77.5 MB of archives.
After this operation, 339 MB of additional disk space will be used.
Selecting previously unselected package nvidia-361.
(Reading database ... 476622 files and directories currently installed.)
Preparing to unpack .../nvidia-361_361.42-0ubuntu2_amd64.deb ...
Unpacking nvidia-361 (361.42-0ubuntu2) ...
Selecting previously unselected package nvidia-opencl-icd-361.
Preparing to unpack .../nvidia-opencl-icd-361_361.42-0ubuntu2_amd64.deb ...
Unpacking nvidia-opencl-icd-361 (361.42-0ubuntu2) ...
Selecting previously unselected package nvidia-prime.
Preparing to unpack .../nvidia-prime_0.8.2_amd64.deb ...
Unpacking nvidia-prime (0.8.2) ...
Selecting previously unselected package nvidia-settings.
Preparing to unpack .../nvidia-settings_361.42-0ubuntu1_amd64.deb ...
Unpacking nvidia-settings (361.42-0ubuntu1) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
Processing triggers for ureadahead (0.100.0-19) ...
ureadahead will be reprofiled on next reboot
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu3) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Setting up nvidia-361 (361.42-0ubuntu2) ...
update-alternatives: using /usr/lib/nvidia-361/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_EGL.conf (i386-linux-gnu_egl_conf) in auto mode
update-alternatives: using /usr/share/nvidia-361/glamor.conf to provide /usr/share/X11/xorg.conf.d/glamoregl.conf (glamor_conf) in auto mode
INFO:Enable nvidia-361
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
Adding system user `nvidia-persistenced' (UID 124) ...
Adding new group `nvidia-persistenced' (GID 133) ...
Adding new user `nvidia-persistenced' (UID 124) with group `nvidia-persistenced' ...
Not creating home directory `/'.
Loading new nvidia-361-361.42 DKMS files...
First Installation: checking all kernels...
Building for 4.4.0-21-generic and 4.6.0-040600rc5-generic
Building for architecture x86_64
Building initial module for 4.4.0-21-generic
Done.


nvidia_361:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.4.0-21-generic/updates/dkms/


nvidia_361_modeset.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.4.0-21-generic/updates/dkms/


nvidia_361_uvm.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.4.0-21-generic/updates/dkms/


depmod....


DKMS: install completed.
Building initial module for 4.6.0-040600rc5-generic
ERROR (dkms apport): kernel package linux-headers-4.6.0-040600rc5-generic is not supported
Error! Bad return status for module build on kernel: 4.6.0-040600rc5-generic (x86_64)
Consult /var/lib/dkms/nvidia-361/361.42/build/make.log for more information.
Setting up nvidia-opencl-icd-361 (361.42-0ubuntu2) ...
Setting up nvidia-prime (0.8.2) ...
Setting up nvidia-settings (361.42-0ubuntu1) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
Processing triggers for ureadahead (0.100.0-19) ...

```

It seem the 4.4 kernel builds while the 4.6 kernel still cannot take it. However, "lsmod | grep nvidia" still returns nothing.

More on the builds

```

qxd@qxd-QC5-Ubuntu:~$ dpkg -l | grep linux-
ii  linux-base                                  4.0ubuntu1                                          all          Linux image base package
ii  linux-firmware                              1.157                                               all          Firmware for Linux kernel drivers
ii  linux-generic                               4.4.0.21.22                                         amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.4.0-21                      4.4.0-21.37                                         all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-21-generic              4.4.0-21.37                                         amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.6.0-040600rc5               4.6.0-040600rc5.201604242031                        all          Header files related to Linux kernel version 4.6.0
ii  linux-headers-4.6.0-040600rc5-generic       4.6.0-040600rc5.201604242031                        amd64        Linux kernel headers for version 4.6.0 on 64 bit x86 SMP
ii  linux-headers-generic                       4.4.0.21.22                                         amd64        Generic Linux kernel headers
ii  linux-image-4.4.0-21-generic                4.4.0-21.37                                         amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.6.0-040600rc5-generic         4.6.0-040600rc5.201604242031                        amd64        Linux kernel image for version 4.6.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-21-generic          4.4.0-21.37                                         amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-generic                         4.4.0.21.22                                         amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                        4.4.0-21.37                                         amd64        Linux Kernel Headers for development
ii  linux-signed-generic                        4.4.0.21.22                                         amd64        Complete Signed Generic Linux kernel and headers
ii  linux-signed-image-4.4.0-21-generic         4.4.0-21.37                                         amd64        Signed kernel image generic
ii  linux-signed-image-generic                  4.4.0.21.22                                         amd64        Signed Generic Linux kernel image
ii  linux-sound-base                            1.0.25+dfsg-0ubuntu5                                all          base package for ALSA and OSS sound systems
ii  syslinux-common                             3:6.03+dfsg-11ubuntu1                               all          collection of bootloaders (common)
ii  syslinux-legacy                             2:3.63+dfsg-2ubuntu8                                amd64        Bootloader for Linux/i386 using MS-DOS floppies

```

I think I forgot to restart Xsession: sudo service lightdm restart...

---

### Post by i2000s2 on 2016-05-03
I got a whole bunch of errors in the TTY1 mode when I was restarting lightdm and the system stuck there. I rebooted with a hot power off. Now 

```

qxd@qxd-QC5-Ubuntu:~$ lsmod | grep nvidia
nvidia_uvm            696320  0
nvidia_modeset        745472  3
nvidia              10076160  60 nvidia_modeset,nvidia_uvm
drm                   360448  8 i915_bpo,drm_kms_helper,nvidia

```
A second monitor is connected... I will check if the tearing/flickering issue is gone when it sleeps and wakes...

We are solving it!

---

### Post by i2000s2 on 2016-05-03
So, after idle sleeping, the screen can come back. The only problem is that when it wakes up, the external screen can only mirrors the primary screen and there is no login window pops up. I have to go to the TTY again to restart the lightdm service. 

Once I login, there was a crash report prompt shown up and asked me if I wanted to report this issue.  I think this is a bug of the kernel and the driver. 

Anyway, I think you have helped me found the culprit and fixed the most annoying problem! I will try out some other newer kernels for better PM support. 

BTW, how can I confirm if the hybrid graphics is using Optimus? I heard this system should be able to switching inbetween NVidia driver and Intel driver automatically and is energy efficient.

---

### Post by Bashing-om on 2016-05-03
i2000s2; Welp;

Hybrid graphics is a horse of of a different color .
Is the integrated GPU enabled in bios ? I see no indication of another graphics set in the log file .With hybrid graphics in use .. that xorg.conf file is required !
Enabling the on-die graphics in bios, Does the system see both sets ?
```

lspci -k | grep -EA2 'VGA|3D'

```
does the kernel see the hardware ?
```

sudo lshw -C display

```

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by i2000s2 on 2016-05-03
Yes, there are two graphic cards, one is the integrated Intel 530 card, the other one is the NVidia Quadro M1000M. So the code seems echoing this fact:

```

qxd@qxd-QC5-Ubuntu:~$ lspci -k | grep -EA2 'VGA|3D'
00:02.0 VGA compatible controller: Intel Corporation Skylake Integrated Graphics (rev 06)
    Subsystem: Lenovo Skylake Integrated Graphics
    Kernel driver in use: i915_bpo
--
01:00.0 VGA compatible controller: NVIDIA Corporation GM107GLM [Quadro M1000M] (rev a2)
    Subsystem: Lenovo GM107GLM [Quadro M1000M]
    Kernel driver in use: nvidia
qxd@qxd-QC5-Ubuntu:~$ sudo lshw -C display
[sudo] password for qxd: 
  *-display               
       description: VGA compatible controller
       product: GM107GLM [Quadro M1000M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:135 memory:c3000000-c3ffffff memory:b0000000-bfffffff memory:c0000000-c1ffffff ioport:4000(size=128) memory:c4000000-c407ffff
  *-display
       description: VGA compatible controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915_bpo latency=0
       resources: irq:131 memory:c2000000-c2ffffff memory:60000000-6fffffff ioport:5000(size=64)

```

And surprisingly, I also got the Xorg.conf file:

```

qxd@qxd-QC5-Ubuntu:~$ ls /etc/X11
app-defaults             xinit               Xreset      Xsession.options
cursors                  xkb                 Xreset.d    xsm
default-display-manager  xorg.conf           Xresources  Xwrapper.config
fonts                    xorg.conf.05032016  Xsession
rgb.txt                  xorg.conf.failsafe  Xsession.d

```

---

### Post by i2000s2 on 2016-05-03
Aha, I also got the nvidia-PRIME work to configure the GPUs. See the attached nvidia-settings window:
[https://www.flickr.com/photos/52606482@N08/26778365156/in/dateposted-public/](https://www.flickr.com/photos/52606482@N08/26778365156/in/dateposted-public/)

---

### Post by i2000s2 on 2016-05-03
Hmmm, a problem found after this installation as half-expected:
Matlab 2016a crashes with the NVidia-361 driver!

```

MATLAB crash file:/home/qxd/matlab_crash_dump.7408-1:




------------------------------------------------------------------------
       Segmentation violation detected at Tue May  3 19:35:03 2016
------------------------------------------------------------------------


Configuration:
  Crash Decoding      : Disabled
  Crash Mode          : continue (default)
  Current Graphics Driver: Unknown hardware 
  Current Visual      : 0x6a (class 4, depth 24)
  Default Encoding    : UTF-8
  GNU C Library       : 2.23 stable
  Host Name           : qxd-QC5-Ubuntu
  MATLAB Architecture : glnxa64
  MATLAB Root         : /home/qxd/Applications/Matlab
  MATLAB Version      : 9.0.0.341360 (R2016a)
  OpenGL              : hardware
  Operating System    : Linux 4.4.0-21-generic #37-Ubuntu SMP Mon Apr 18 18:33:37 UTC 2016 x86_64
  Processor ID        : x86 Family 6 Model 94 Stepping 3, GenuineIntel
  Virtual Machine     : Java 1.7.0_60-b19 with Oracle Corporation Java HotSpot(TM) 64-Bit Server VM mixed mode
  Window System       : The X.Org Foundation (11803000), display :0


Fault Count: 1




Abnormal termination:
Segmentation violation


Register State (from fault):
  RAX = 00007f9fff07adc0  RBX = 0000000000000000
  RCX = 0000000000000001  RDX = 00000000000000a8
  RSP = 00007f9fff07ad90  RBP = 00007f9fdc094590
  RSI = 00007f9fff07ae68  RDI = 00007f9fff07adc0


   R8 = 0000000000000000   R9 = 0000000000000001
  R10 = 00007f9fdc114de0  R11 = 0000000000000000
  R12 = 00007f9fdc37a450  R13 = 00007f9fdc094590
  R14 = 00007f9fdc4338d0  R15 = 00007f9fdc36bf50


  RIP = 00007f9ffdacb24d  EFL = 0000000000010206


   CS = 0033   FS = 0000   GS = 0000


Stack Trace (from fault):
[  0] 0x00007f9ffdacb24d             /usr/lib/nvidia-361/libGLX_nvidia.so.0+00344653




If this problem is reproducible, please submit a Service Request via:
    http://www.mathworks.com/support/contact_us/


A technical support engineer might contact you with further information.


Thank you for your help.

```

---

### Post by Bashing-om on 2016-05-03
i2000s2; Yepper.

Graphics appears to be good now. If you agree:
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

The matlab situation, looks like ya need to be talking to the authors.

[INDENT][INDENT]we do what we can
[INDENT][INDENT][INDENT]with what we have to work with
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by i2000s2 on 2016-05-03
Thank you, Bashing-om! You are very helpful and professional! I wouldn't notice the small error in the driver installation script, that is the biggest lesson I have learned today.

I have basically solved the matlab crashing problem by turning off the opengl support, which is not decent but works. I guess the Optimus technique is working as long as I can choosing GPU drivers freely. I will mark this thread as SOLVED right away! Will be sharing my experience of installing the driver on my machine type later. 

Have a good one!

---

### Post by i2000s2 on 2016-05-03
I just found a patch to the nvidia 361.19 to solve the compatibility issue with kernel 4.6: [https://devtalk.nvidia.com/default/topic/926824/linux/364-1-2-5-won-t-compile-against-latest-kernel-git-tree-patches-for-4-6-0-rc3-included-/2](https://devtalk.nvidia.com/default/topic/926824/linux/364-1-2-5-won-t-compile-against-latest-kernel-git-tree-patches-for-4-6-0-rc3-included-/2)

Now need to figure out how to apply this patch... It could be fixed in the next driver release I guess.

---

### Post by Bashing-om on 2016-05-03
i2000s2; Hold on.

maybe exercise care here as the version installed is " Preparing to unpack .../nvidia-361_361.42-0ubuntu2_amd64.deb ...'
And the patch applies to older versions " 364.1[2,5]  .

Now if ya must .. might try the 364 version driver . You know how now to revert back to 361 if 364 does not work .

[INDENT][INDENT]Hey It is a thought
[INDENT][INDENT]but I was wrong, once
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by i2000s2 on 2016-05-04
Yes, I know how to do it now! I may play around with it later. I have also reported this incompatibility of nvidia-361 driver with the 4.6 kernel to the NVidia developers. Currently, I am working on making the nvidia driver work better with Matlab which I use daily. Hopefully things will look up soon!

---

### Post by Bashing-om on 2016-05-04
i2000s2; Outstanding .

Keep up the good work.

Let us know how it goes.

[INDENT][INDENT]together we can
[/INDENT][/INDENT]

---

### Post by artur20 on 2016-07-25
Hello,

this thread is a wee old now, but it is the only related things that I could find. 

I tried all the recommendations and I believe my nvidia card is found and works, however I can not get rid of screen tearing. By tearing I mean visible waves when scrolling web pages, image failures when watching movies, terminal can't keep up with keeping.
My only solution (for months now) has been to disable Nvidia completely and go into "Power Saving mode", using intel only. This is a bit frustrating because I have this great graphics card in my laptop that I would love to use, but I can not activate. 

I was wondering if I am missing something. I documented my issues here: [https://ubuntuforums.org/showthread.php?t=2327162&p=13500945#post13500945](https://ubuntuforums.org/showthread.php?t=2327162&p=13500945#post13500945) 

If there are any recommendations I haven't tried yet, I would love to give it a shot and get this resolved. 
I have been in contact with dell for weeks now as well and they seem to not have a solution, despite them advertising my laptop as ubuntu-compatible :/ 

Thanks!

---

### Post by i2000s2 on 2016-07-25
> **artur20 said:**
> Hello,

this thread is a wee old now, but it is the only related things that I could find. 

I tried all the recommendations and I believe my nvidia card is found and works, however I can not get rid of screen tearing. By tearing I mean visible waves when scrolling web pages, image failures when watching movies, terminal can't keep up with keeping.
My only solution (for months now) has been to disable Nvidia completely and go into "Power Saving mode", using intel only. This is a bit frustrating because I have this great graphics card in my laptop that I would love to use, but I can not activate. 

I was wondering if I am missing something. I documented my issues here: [https://ubuntuforums.org/showthread.php?t=2327162&p=13500945#post13500945](https://ubuntuforums.org/showthread.php?t=2327162&p=13500945#post13500945) 

If there are any recommendations I haven't tried yet, I would love to give it a shot and get this resolved. 
I have been in contact with dell for weeks now as well and they seem to not have a solution, despite them advertising my laptop as ubuntu-compatible :/ 

Thanks!

I will reply to your original thread. 
In the mean time, in this thread, there are a lot of debugging trick to play around. The purpose is to help you identify what caused the problem. It's good to try them and show your result in your issue tracking thread. Thanks.

---

### Post by timrichardson2 on 2016-12-01
And here am I, some months later trying to see how well the P50 works. I hope you fixed this problem. I have a W520 which has an older version of Optimus, the tearing you describe almost certainly means the nvidia driver is not in use and your session has fallen back to the Nouveau driver, which always works, but suffers from bad performance.

---

### Post by i2000s2 on 2016-12-01
> **timrichardson2 said:**
> And here am I, some months later trying to see how well the P50 works. I hope you fixed this problem. I have a W520 which has an older version of Optimus, the tearing you describe almost certainly means the nvidia driver is not in use and your session has fallen back to the Nouveau driver, which always works, but suffers from bad performance.
With all those trials and fails, the NVidia driver eventually worked on the P50 machine. I hope this can give you some confidence on upgrading your machine if you'd like to :)

---

### Post by artur20 on 2016-12-05
My issue was never the nvidia card not working (as far as I can tell) or the driver not working properly. I think my issue is this: [https://devtalk.nvidia.com/default/topic/775691/linux/vsync-issue-nvidia-prime-ux32vd-with-gt620-m-/7](https://devtalk.nvidia.com/default/topic/775691/linux/vsync-issue-nvidia-prime-ux32vd-with-gt620-m-/7) It simply can't work with the current version of ubuntu. There is a new xorg version out that support optimus cards, however I have yet to find an update guide on how to get kernel + xorg on my ubuntu

---

