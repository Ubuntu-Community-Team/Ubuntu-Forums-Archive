---
title: "NVIDIA card Brightness HotKey not working"
date: 2013-11-27
forum: Hardware
---

### Post by aa-hcl on 2013-11-27
Hi, I have got the same problem, I can not change the brightness of the monitor:

- Fn+up or Fn+down keys do NOT work (INTERESTING: they DO work at the BIOS stage and I can set brightness to the required level, for example the minimum level, and this level of brightness will stay after login to ubuntu)
- in the settings menu the slider to change brightness does exist, but it does not change the brightness
- in the command line if I try to set the brightness by something like "echo 20 > /sys/class/backlight/acpi_video0/brightness" (as root) - it does change the value of /sys/class/backlight/acpi_video0/brightness and the value of /sys/class/backlight/acpi_video0/actual_brightness, but it does NOT change the brightness of the monitor

My system is different from the system of original poster:  I have nvidia card.

Initially I thought that the nvidia driver is to blame, but with doing complete uninstall of nvidia driver (by sudo apt-get purge nvidia*) does not solve the problem, without the nvidia driver it is still bnot working.

IMPORTANT detail:  I had the same system working under 13.10 with brightness chaning all working BUT with previous hard drive (which is now nearly dead) - I had a hard drive faulure and had to re-install the systemn from scratch with fresh 13.10 installation. The previous system was wtih fresh 12.10 install and it was then upgraded to 13.04 and then with 13.10. Unfortunately, I did not make a note how I solved the problem when I upgraded to 13.10 from 13.04 - I also had the problem fo not being able to change the brightness.

This means that I do know that my laptop can have the brightness control under ubuntu 13.10

My system details:


```
aa@aa-Latitude-E6530:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.11.0-13-generic root=UUID=c86aca8f-c879-4a03-a76a-7effda7f037d ro quiet splash pcie_aspm=force
```

```
aa@aa-Latitude-E6530:~$ lspci -k | grep -A3 VGA
01:00.0 VGA compatible controller: NVIDIA Corporation GF108GLM [NVS 5200M] (rev a1)
    Subsystem: Dell Device 0535
    Kernel driver in use: nvidia
01:00.1 Audio device: NVIDIA Corporation GF108 High Definition Audio Controller (rev a1)
```

```
aa@aa-Latitude-E6530:~$ for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
/sys/class/backlight/acpi_video0
93
93
100
aa@aa-Latitude-E6530:~$ 
```

```
aa@aa-Latitude-E6530:~$ cat /var/log/Xorg.0.log
[    16.077] 
X.Org X Server 1.14.3
Release Date: 2013-09-12
[    16.077] X Protocol Version 11, Revision 0
[    16.077] Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
[    16.077] Current Operating System: Linux aa-Latitude-E6530 3.11.0-13-generic #20-Ubuntu SMP Wed Oct 23 07:38:26 UTC 2013 x86_64
[    16.077] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.11.0-13-generic root=UUID=c86aca8f-c879-4a03-a76a-7effda7f037d ro quiet splash pcie_aspm=force
[    16.077] Build Date: 15 October 2013  09:23:37AM
[    16.077] xorg-server 2:1.14.3-3ubuntu2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    16.077] Current version of pixman: 0.30.2
[    16.077]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    16.077] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    16.077] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Nov 27 13:21:08 2013
[    16.083] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    16.083] (==) No Layout section.  Using the first Screen section.
[    16.083] (==) No screen section available. Using defaults.
[    16.083] (**) |-->Screen "Default Screen Section" (0)
[    16.083] (**) |   |-->Monitor "<default monitor>"
[    16.083] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    16.083] (==) Automatically adding devices
[    16.083] (==) Automatically enabling devices
[    16.083] (==) Automatically adding GPU devices
[    16.083] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    16.083]     Entry deleted from font path.
[    16.083] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    16.084]     Entry deleted from font path.
[    16.084] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    16.084]     Entry deleted from font path.
[    16.084] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    16.084]     Entry deleted from font path.
[    16.084] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    16.084]     Entry deleted from font path.
[    16.084] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    16.084] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    16.084] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    16.084] (II) Loader magic: 0x7f70a15cbd20
[    16.084] (II) Module ABI versions:
[    16.084]     X.Org ANSI C Emulation: 0.4
[    16.084]     X.Org Video Driver: 14.1
[    16.084]     X.Org XInput driver : 19.1
[    16.084]     X.Org Server Extension : 7.0
[    16.084] (II) xfree86: Adding drm device (/dev/dri/card0)
[    16.085] (--) PCI:*(0:1:0:0) 10de:0dfc:1028:0535 rev 161, Mem @ 0xf5000000/16777216, 0xe0000000/268435456, 0xf0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[    16.085] (II) Open ACPI successful (/var/run/acpid.socket)
[    16.085] Initializing built-in extension Generic Event Extension
[    16.085] Initializing built-in extension SHAPE
[    16.085] Initializing built-in extension MIT-SHM
[    16.085] Initializing built-in extension XInputExtension
[    16.085] Initializing built-in extension XTEST
[    16.085] Initializing built-in extension BIG-REQUESTS
[    16.085] Initializing built-in extension SYNC
[    16.085] Initializing built-in extension XKEYBOARD
[    16.085] Initializing built-in extension XC-MISC
[    16.085] Initializing built-in extension SECURITY
[    16.085] Initializing built-in extension XINERAMA
[    16.085] Initializing built-in extension XFIXES
[    16.085] Initializing built-in extension RENDER
[    16.085] Initializing built-in extension RANDR
[    16.085] Initializing built-in extension COMPOSITE
[    16.085] Initializing built-in extension DAMAGE
[    16.085] Initializing built-in extension MIT-SCREEN-SAVER
[    16.085] Initializing built-in extension DOUBLE-BUFFER
[    16.085] Initializing built-in extension RECORD
[    16.085] Initializing built-in extension DPMS
[    16.085] Initializing built-in extension X-Resource
[    16.085] Initializing built-in extension XVideo
[    16.085] Initializing built-in extension XVideo-MotionCompensation
[    16.085] Initializing built-in extension SELinux
[    16.085] Initializing built-in extension XFree86-VidModeExtension
[    16.085] Initializing built-in extension XFree86-DGA
[    16.085] Initializing built-in extension XFree86-DRI
[    16.085] Initializing built-in extension DRI2
[    16.085] (II) "glx" will be loaded by default.
[    16.085] (WW) "xmir" is not to be loaded by default. Skipping.
[    16.085] (II) LoadModule: "dri2"
[    16.085] (II) Module "dri2" already built-in
[    16.085] (II) LoadModule: "glamoregl"
[    16.118] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[    16.237] (II) Module glamoregl: vendor="X.Org Foundation"
[    16.237]     compiled for 1.14.3, module version = 0.5.1
[    16.237]     ABI class: X.Org ANSI C Emulation, version 0.4
[    16.237] (II) LoadModule: "glx"
[    16.237] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    16.339] (II) Module glx: vendor="NVIDIA Corporation"
[    16.339]     compiled for 4.0.2, module version = 1.0.0
[    16.339]     Module class: X.Org Server Extension
[    16.339] (II) NVIDIA GLX Module  319.60  Wed Sep 25 14:24:11 PDT 2013
[    16.339] Loading extension GLX
[    16.339] (==) Matched nvidia as autoconfigured driver 0
[    16.339] (==) Matched nouveau as autoconfigured driver 1
[    16.339] (==) Matched nvidia as autoconfigured driver 2
[    16.339] (==) Matched nouveau as autoconfigured driver 3
[    16.339] (==) Matched vesa as autoconfigured driver 4
[    16.339] (==) Matched modesetting as autoconfigured driver 5
[    16.339] (==) Matched fbdev as autoconfigured driver 6
[    16.339] (==) Assigned the driver to the xf86ConfigLayout
[    16.339] (II) LoadModule: "nvidia"
[    16.339] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    16.343] (II) Module nvidia: vendor="NVIDIA Corporation"
[    16.343]     compiled for 4.0.2, module version = 1.0.0
[    16.343]     Module class: X.Org Video Driver
[    16.343] (II) LoadModule: "nouveau"
[    16.343] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    16.355] (II) Module nouveau: vendor="X.Org Foundation"
[    16.355]     compiled for 1.14.2.901, module version = 1.0.9
[    16.355]     Module class: X.Org Video Driver
[    16.355]     ABI class: X.Org Video Driver, version 14.1
[    16.355] (II) LoadModule: "vesa"
[    16.355] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    16.356] (II) Module vesa: vendor="X.Org Foundation"
[    16.356]     compiled for 1.14.1, module version = 2.3.2
[    16.356]     Module class: X.Org Video Driver
[    16.356]     ABI class: X.Org Video Driver, version 14.1
[    16.356] (II) LoadModule: "modesetting"
[    16.356] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    16.356] (II) Module modesetting: vendor="X.Org Foundation"
[    16.356]     compiled for 1.14.1, module version = 0.8.0
[    16.356]     Module class: X.Org Video Driver
[    16.356]     ABI class: X.Org Video Driver, version 14.1
[    16.356] (II) LoadModule: "fbdev"
[    16.357] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    16.357] (II) Module fbdev: vendor="X.Org Foundation"
[    16.357]     compiled for 1.14.1, module version = 0.4.3
[    16.357]     Module class: X.Org Video Driver
[    16.357]     ABI class: X.Org Video Driver, version 14.1
[    16.357] (II) NVIDIA dlloader X Driver  319.60  Wed Sep 25 14:04:14 PDT 2013
[    16.357] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    16.357] (II) NOUVEAU driver Date:   Wed Jul 31 10:51:03 2013 +1000
[    16.357] (II) NOUVEAU driver for NVIDIA chipset families :
[    16.357]     RIVA TNT        (NV04)
[    16.357]     RIVA TNT2       (NV05)
[    16.357]     GeForce 256     (NV10)
[    16.357]     GeForce 2       (NV11, NV15)
[    16.357]     GeForce 4MX     (NV17, NV18)
[    16.357]     GeForce 3       (NV20)
[    16.357]     GeForce 4Ti     (NV25, NV28)
[    16.357]     GeForce FX      (NV3x)
[    16.357]     GeForce 6       (NV4x)
[    16.357]     GeForce 7       (G7x)
[    16.358]     GeForce 8       (G8x)
[    16.358]     GeForce GTX 200 (NVA0)
[    16.358]     GeForce GTX 400 (NVC0)
[    16.358] (II) VESA: driver for VESA chipsets: vesa
[    16.358] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    16.358] (II) FBDEV: driver for framebuffer: fbdev
[    16.358] (++) using VT number 7

[    16.368] (II) Loading sub module "fb"
[    16.368] (II) LoadModule: "fb"
[    16.368] (II) Loading /usr/lib/xorg/modules/libfb.so
[    16.368] (II) Module fb: vendor="X.Org Foundation"
[    16.368]     compiled for 1.14.3, module version = 1.0.0
[    16.368]     ABI class: X.Org ANSI C Emulation, version 0.4
[    16.368] (WW) Unresolved symbol: fbGetGCPrivateKey
[    16.368] (II) Loading sub module "wfb"
[    16.368] (II) LoadModule: "wfb"
[    16.369] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    16.369] (II) Module wfb: vendor="X.Org Foundation"
[    16.369]     compiled for 1.14.3, module version = 1.0.0
[    16.369]     ABI class: X.Org ANSI C Emulation, version 0.4
[    16.369] (II) Loading sub module "shadow"
[    16.369] (II) LoadModule: "shadow"
[    16.369] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    16.370] (II) Module shadow: vendor="X.Org Foundation"
[    16.370]     compiled for 1.14.3, module version = 1.1.0
[    16.370]     ABI class: X.Org ANSI C Emulation, version 0.4
[    16.370] (II) Loading sub module "ramdac"
[    16.370] (II) LoadModule: "ramdac"
[    16.370] (II) Module "ramdac" already built-in
[    16.370] (WW) Falling back to old probe method for vesa
[    16.370] (WW) Falling back to old probe method for modesetting
[    16.370] (WW) Falling back to old probe method for fbdev
[    16.370] (II) Loading sub module "fbdevhw"
[    16.370] (II) LoadModule: "fbdevhw"
[    16.370] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    16.371] (II) Module fbdevhw: vendor="X.Org Foundation"
[    16.371]     compiled for 1.14.3, module version = 0.0.2
[    16.371]     ABI class: X.Org Video Driver, version 14.1
[    16.371] (EE) open /dev/fb0: No such file or directory
[    16.371] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    16.371] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    16.371] (==) NVIDIA(0): RGB weight 888
[    16.371] (==) NVIDIA(0): Default visual is TrueColor
[    16.371] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    16.371] (**) NVIDIA(0): Enabling 2D acceleration
[    16.990] (II) NVIDIA(GPU-0): Display (Matrox (CRT-0)) does not support NVIDIA 3D Vision
[    16.990] (II) NVIDIA(GPU-0):     stereo.
[    16.990] (II) NVIDIA(GPU-0): Display (Seiko/Epson (DFP-0)) does not support NVIDIA 3D
[    16.990] (II) NVIDIA(GPU-0):     Vision stereo.
[    17.011] (II) NVIDIA(GPU-0): Display (Idek Iiyama PL2409HD (DFP-1)) does not support NVIDIA
[    17.011] (II) NVIDIA(GPU-0):     3D Vision stereo.
[    17.012] (II) NVIDIA(0): NVIDIA GPU NVS 5200M (GF108) at PCI:1:0:0 (GPU-0)
[    17.012] (--) NVIDIA(0): Memory: 1048576 kBytes
[    17.012] (--) NVIDIA(0): VideoBIOS: 70.08.a8.00.8e
[    17.012] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    17.016] (--) NVIDIA(0): Valid display device(s) on NVS 5200M at PCI:1:0:0
[    17.016] (--) NVIDIA(0):     Matrox (CRT-0) (connected)
[    17.016] (--) NVIDIA(0):     Seiko/Epson (DFP-0) (boot, connected)
[    17.016] (--) NVIDIA(0):     Idek Iiyama PL2409HD (DFP-1) (connected)
[    17.016] (--) NVIDIA(0):     DFP-2
[    17.016] (--) NVIDIA(0):     DFP-3
[    17.016] (--) NVIDIA(0):     DFP-4
[    17.016] (--) NVIDIA(0):     DFP-5
[    17.016] (--) NVIDIA(0): Matrox (CRT-0): 400.0 MHz maximum pixel clock
[    17.016] (--) NVIDIA(0): Seiko/Epson (DFP-0): 330.0 MHz maximum pixel clock
[    17.016] (--) NVIDIA(0): Seiko/Epson (DFP-0): Internal Dual Link LVDS
[    17.016] (--) NVIDIA(0): Idek Iiyama PL2409HD (DFP-1): 165.0 MHz maximum pixel clock
[    17.016] (--) NVIDIA(0): Idek Iiyama PL2409HD (DFP-1): Internal Single Link TMDS
[    17.016] (--) NVIDIA(0): DFP-2: 165.0 MHz maximum pixel clock
[    17.016] (--) NVIDIA(0): DFP-2: Internal Single Link TMDS
[    17.016] (--) NVIDIA(0): DFP-3: 165.0 MHz maximum pixel clock
[    17.016] (--) NVIDIA(0): DFP-3: Internal Single Link TMDS
[    17.016] (--) NVIDIA(0): DFP-4: 480.0 MHz maximum pixel clock
[    17.016] (--) NVIDIA(0): DFP-4: Internal DisplayPort
[    17.016] (--) NVIDIA(0): DFP-5: 480.0 MHz maximum pixel clock
[    17.016] (--) NVIDIA(0): DFP-5: Internal DisplayPort
[    17.016] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    17.016] (**) NVIDIA(0):     device Matrox (CRT-0) (Using EDID frequencies has been
[    17.016] (**) NVIDIA(0):     enabled on all display devices.)
[    17.016] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    17.017] (**) NVIDIA(0):     device Seiko/Epson (DFP-0) (Using EDID frequencies has
[    17.017] (**) NVIDIA(0):     been enabled on all display devices.)
[    17.017] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    17.017] (**) NVIDIA(0):     device Idek Iiyama PL2409HD (DFP-1) (Using EDID
[    17.017] (**) NVIDIA(0):     frequencies has been enabled on all display devices.)
[    17.017] (WW) NVIDIA(GPU-0): The EDID for Idek Iiyama PL2409HD (DFP-1) contradicts itself:
[    17.017] (WW) NVIDIA(GPU-0):     mode "1280x720" is specified in the EDID; however, the
[    17.017] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (56.000-76.000 Hz) would
[    17.017] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    17.017] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "1280x720".
[    17.017] (WW) NVIDIA(GPU-0): The EDID for Idek Iiyama PL2409HD (DFP-1) contradicts itself:
[    17.017] (WW) NVIDIA(GPU-0):     mode "720x576" is specified in the EDID; however, the
[    17.017] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (56.000-76.000 Hz) would
[    17.017] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    17.017] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "720x576".
[    17.017] (WW) NVIDIA(GPU-0): The EDID for Idek Iiyama PL2409HD (DFP-1) contradicts itself:
[    17.017] (WW) NVIDIA(GPU-0):     mode "720x576" is specified in the EDID; however, the
[    17.017] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (56.000-76.000 Hz) would
[    17.017] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    17.017] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "720x576".
[    17.017] (WW) NVIDIA(GPU-0): The EDID for Idek Iiyama PL2409HD (DFP-1) contradicts itself:
[    17.017] (WW) NVIDIA(GPU-0):     mode "1280x720" is specified in the EDID; however, the
[    17.017] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (56.000-76.000 Hz) would
[    17.017] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    17.017] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "1280x720".
[    17.017] (WW) NVIDIA(GPU-0): The EDID for Idek Iiyama PL2409HD (DFP-1) contradicts itself:
[    17.017] (WW) NVIDIA(GPU-0):     mode "480x576" is specified in the EDID; however, the
[    17.017] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (56.000-76.000 Hz) would
[    17.017] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    17.017] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "480x576".
[    17.018] (==) NVIDIA(0): 
[    17.018] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    17.018] (==) NVIDIA(0):     will be used as the requested mode.
[    17.018] (==) NVIDIA(0): 
[    17.018] (II) NVIDIA(0): Validated MetaModes:
[    17.018] (II) NVIDIA(0):     "DFP-0:nvidia-auto-select{},CRT-0:nvidia-auto-select{}"
[    17.018] (II) NVIDIA(0): Virtual screen size determined to be 5760 x 1200
[    18.297] (--) NVIDIA(0): DPI set to (143, 144); computed from "UseEdidDpi" X config
[    18.297] (--) NVIDIA(0):     option
[    18.297] (II) UnloadModule: "nouveau"
[    18.297] (II) Unloading nouveau
[    18.298] (II) UnloadModule: "vesa"
[    18.298] (II) Unloading vesa
[    18.298] (II) UnloadModule: "modesetting"
[    18.298] (II) Unloading modesetting
[    18.298] (II) UnloadModule: "fbdev"
[    18.298] (II) Unloading fbdev
[    18.298] (II) UnloadSubModule: "fbdevhw"
[    18.298] (II) Unloading fbdevhw
[    18.298] (--) Depth 24 pixmap format is 32 bpp
[    18.298] (II) NVIDIA: Using 3072.00 MB of virtual memory for indirect memory
[    18.298] (II) NVIDIA:     access.
[    18.303] (II) NVIDIA(0): Setting mode "DFP-0:nvidia-auto-select{},CRT-0:nvidia-auto-select{}"
[    18.636] Loading extension NV-GLX
[    18.727] (==) NVIDIA(0): Disabling shared memory pixmaps
[    18.727] (==) NVIDIA(0): Backing store disabled
[    18.727] (==) NVIDIA(0): Silken mouse enabled
[    18.727] (==) NVIDIA(0): DPMS enabled
[    18.727] Loading extension NV-CONTROL
[    18.727] Loading extension XINERAMA
[    18.727] (II) Loading sub module "dri2"
[    18.727] (II) LoadModule: "dri2"
[    18.727] (II) Module "dri2" already built-in
[    18.727] (II) NVIDIA(0): [DRI2] Setup complete
[    18.727] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[    18.727] (--) RandR disabled
[    18.730] (II) SELinux: Disabled on system
[    18.730] (II) Initializing extension GLX
[    18.738] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    18.739] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    18.739] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    18.739] (II) LoadModule: "evdev"
[    18.739] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.752] (II) Module evdev: vendor="X.Org Foundation"
[    18.752]     compiled for 1.14.1, module version = 2.7.3
[    18.752]     Module class: X.Org XInput Driver
[    18.752]     ABI class: X.Org XInput driver, version 19.1
[    18.752] (II) Using input driver 'evdev' for 'Power Button'
[    18.752] (**) Power Button: always reports core events
[    18.752] (**) evdev: Power Button: Device: "/dev/input/event3"
[    18.752] (--) evdev: Power Button: Vendor 0 Product 0x1
[    18.752] (--) evdev: Power Button: Found keys
[    18.752] (II) evdev: Power Button: Configuring as keyboard
[    18.752] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    18.752] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    18.752] (**) Option "xkb_rules" "evdev"
[    18.752] (**) Option "xkb_model" "pc105"
[    18.752] (**) Option "xkb_layout" "gb"
[    18.753] (II) XKB: reuse xkmfile /var/lib/xkb/server-2B4266AA55228AE7D9557A18F1965DBA19850816.xkm
[    18.753] (II) config/udev: Adding input device Video Bus (/dev/input/event14)
[    18.753] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    18.753] (II) Using input driver 'evdev' for 'Video Bus'
[    18.753] (**) Video Bus: always reports core events
[    18.753] (**) evdev: Video Bus: Device: "/dev/input/event14"
[    18.753] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    18.753] (--) evdev: Video Bus: Found keys
[    18.753] (II) evdev: Video Bus: Configuring as keyboard
[    18.753] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:15/LNXVIDEO:00/input/input14/event14"
[    18.753] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    18.753] (**) Option "xkb_rules" "evdev"
[    18.753] (**) Option "xkb_model" "pc105"
[    18.753] (**) Option "xkb_layout" "gb"
[    18.753] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    18.753] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    18.753] (II) Using input driver 'evdev' for 'Power Button'
[    18.753] (**) Power Button: always reports core events
[    18.753] (**) evdev: Power Button: Device: "/dev/input/event1"
[    18.753] (--) evdev: Power Button: Vendor 0 Product 0x1
[    18.753] (--) evdev: Power Button: Found keys
[    18.753] (II) evdev: Power Button: Configuring as keyboard
[    18.753] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[    18.753] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    18.753] (**) Option "xkb_rules" "evdev"
[    18.753] (**) Option "xkb_model" "pc105"
[    18.753] (**) Option "xkb_layout" "gb"
[    18.754] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    18.754] (II) No input driver specified, ignoring this device.
[    18.754] (II) This device may have been added with another device file.
[    18.754] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    18.754] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    18.754] (II) Using input driver 'evdev' for 'Sleep Button'
[    18.754] (**) Sleep Button: always reports core events
[    18.754] (**) evdev: Sleep Button: Device: "/dev/input/event2"
[    18.754] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    18.754] (--) evdev: Sleep Button: Found keys
[    18.754] (II) evdev: Sleep Button: Configuring as keyboard
[    18.754] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2/event2"
[    18.754] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[    18.754] (**) Option "xkb_rules" "evdev"
[    18.754] (**) Option "xkb_model" "pc105"
[    18.754] (**) Option "xkb_layout" "gb"
[    18.754] (II) config/udev: Adding drm device (/dev/dri/card0)
[    18.754] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    18.754] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=9 (/dev/input/event15)
[    18.754] (II) No input driver specified, ignoring this device.
[    18.754] (II) This device may have been added with another device file.
[    18.754] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event16)
[    18.754] (II) No input driver specified, ignoring this device.
[    18.754] (II) This device may have been added with another device file.
[    18.754] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event17)
[    18.754] (II) No input driver specified, ignoring this device.
[    18.754] (II) This device may have been added with another device file.
[    18.754] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event18)
[    18.754] (II) No input driver specified, ignoring this device.
[    18.754] (II) This device may have been added with another device file.
[    18.755] (II) config/udev: Adding input device Laptop_Integrated_Webcam_E4HD (/dev/input/event13)
[    18.755] (**) Laptop_Integrated_Webcam_E4HD: Applying InputClass "evdev keyboard catchall"
[    18.755] (II) Using input driver 'evdev' for 'Laptop_Integrated_Webcam_E4HD'
[    18.755] (**) Laptop_Integrated_Webcam_E4HD: always reports core events
[    18.755] (**) evdev: Laptop_Integrated_Webcam_E4HD: Device: "/dev/input/event13"
[    18.755] (--) evdev: Laptop_Integrated_Webcam_E4HD: Vendor 0xc45 Product 0x643f
[    18.755] (--) evdev: Laptop_Integrated_Webcam_E4HD: Found keys
[    18.755] (II) evdev: Laptop_Integrated_Webcam_E4HD: Configuring as keyboard
[    18.755] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.0/input/input13/event13"
[    18.755] (II) XINPUT: Adding extended input device "Laptop_Integrated_Webcam_E4HD" (type: KEYBOARD, id 10)
[    18.755] (**) Option "xkb_rules" "evdev"
[    18.755] (**) Option "xkb_model" "pc105"
[    18.755] (**) Option "xkb_layout" "gb"
[    18.755] (II) config/udev: Adding input device HDA Intel PCH Headset Mic (/dev/input/event10)
[    18.755] (II) No input driver specified, ignoring this device.
[    18.755] (II) This device may have been added with another device file.
[    18.755] (II) config/udev: Adding input device HDA Intel PCH Dock Mic (/dev/input/event11)
[    18.755] (II) No input driver specified, ignoring this device.
[    18.755] (II) This device may have been added with another device file.
[    18.755] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event8)
[    18.755] (II) No input driver specified, ignoring this device.
[    18.755] (II) This device may have been added with another device file.
[    18.755] (II) config/udev: Adding input device HDA Intel PCH Dock Line Out (/dev/input/event9)
[    18.755] (II) No input driver specified, ignoring this device.
[    18.755] (II) This device may have been added with another device file.
[    18.755] (II) config/udev: Adding input device Logitech USB Keyboard (/dev/input/event5)
[    18.755] (**) Logitech USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    18.755] (II) Using input driver 'evdev' for 'Logitech USB Keyboard'
[    18.755] (**) Logitech USB Keyboard: always reports core events
[    18.755] (**) evdev: Logitech USB Keyboard: Device: "/dev/input/event5"
[    18.755] (--) evdev: Logitech USB Keyboard: Vendor 0x46d Product 0xc31d
[    18.755] (--) evdev: Logitech USB Keyboard: Found keys
[    18.755] (II) evdev: Logitech USB Keyboard: Configuring as keyboard
[    18.755] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.7/2-1.7.3/2-1.7.3.3/2-1.7.3.3:1.0/input/input5/event5"
[    18.755] (II) XINPUT: Adding extended input device "Logitech USB Keyboard" (type: KEYBOARD, id 11)
[    18.755] (**) Option "xkb_rules" "evdev"
[    18.755] (**) Option "xkb_model" "pc105"
[    18.755] (**) Option "xkb_layout" "gb"
[    18.756] (II) config/udev: Adding input device Logitech USB Keyboard (/dev/input/event6)
[    18.756] (**) Logitech USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    18.756] (II) Using input driver 'evdev' for 'Logitech USB Keyboard'
[    18.756] (**) Logitech USB Keyboard: always reports core events
[    18.756] (**) evdev: Logitech USB Keyboard: Device: "/dev/input/event6"
[    18.756] (--) evdev: Logitech USB Keyboard: Vendor 0x46d Product 0xc31d
[    18.756] (--) evdev: Logitech USB Keyboard: Found absolute axes
[    18.756] (II) evdev: Logitech USB Keyboard: Forcing absolute x/y axes to exist.
[    18.756] (--) evdev: Logitech USB Keyboard: Found keys
[    18.756] (II) evdev: Logitech USB Keyboard: Forcing relative x/y axes to exist.
[    18.756] (II) evdev: Logitech USB Keyboard: Configuring as mouse
[    18.756] (II) evdev: Logitech USB Keyboard: Configuring as keyboard
[    18.756] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.7/2-1.7.3/2-1.7.3.3/2-1.7.3.3:1.1/input/input6/event6"
[    18.756] (II) XINPUT: Adding extended input device "Logitech USB Keyboard" (type: KEYBOARD, id 12)
[    18.756] (**) Option "xkb_rules" "evdev"
[    18.756] (**) Option "xkb_model" "pc105"
[    18.756] (**) Option "xkb_layout" "gb"
[    18.756] (II) evdev: Logitech USB Keyboard: initialized for absolute axes.
[    18.756] (**) Logitech USB Keyboard: (accel) keeping acceleration scheme 1
[    18.756] (**) Logitech USB Keyboard: (accel) acceleration profile 0
[    18.756] (**) Logitech USB Keyboard: (accel) acceleration factor: 2.000
[    18.756] (**) Logitech USB Keyboard: (accel) acceleration threshold: 4
[    18.756] (II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/event7)
[    18.756] (**) Logitech USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[    18.756] (II) Using input driver 'evdev' for 'Logitech USB Optical Mouse'
[    18.756] (**) Logitech USB Optical Mouse: always reports core events
[    18.756] (**) evdev: Logitech USB Optical Mouse: Device: "/dev/input/event7"
[    18.756] (--) evdev: Logitech USB Optical Mouse: Vendor 0x46d Product 0xc05b
[    18.756] (--) evdev: Logitech USB Optical Mouse: Found 12 mouse buttons
[    18.756] (--) evdev: Logitech USB Optical Mouse: Found scroll wheel(s)
[    18.756] (--) evdev: Logitech USB Optical Mouse: Found relative axes
[    18.756] (--) evdev: Logitech USB Optical Mouse: Found x and y relative axes
[    18.756] (II) evdev: Logitech USB Optical Mouse: Configuring as mouse
[    18.756] (II) evdev: Logitech USB Optical Mouse: Adding scrollwheel support
[    18.756] (**) evdev: Logitech USB Optical Mouse: YAxisMapping: buttons 4 and 5
[    18.756] (**) evdev: Logitech USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    18.756] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.7/2-1.7.3/2-1.7.3.4/2-1.7.3.4:1.0/input/input7/event7"
[    18.756] (II) XINPUT: Adding extended input device "Logitech USB Optical Mouse" (type: MOUSE, id 13)
[    18.756] (II) evdev: Logitech USB Optical Mouse: initialized for relative axes.
[    18.756] (**) Logitech USB Optical Mouse: (accel) keeping acceleration scheme 1
[    18.756] (**) Logitech USB Optical Mouse: (accel) acceleration profile 0
[    18.756] (**) Logitech USB Optical Mouse: (accel) acceleration factor: 2.000
[    18.756] (**) Logitech USB Optical Mouse: (accel) acceleration threshold: 4
[    18.756] (II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/mouse0)
[    18.756] (II) No input driver specified, ignoring this device.
[    18.756] (II) This device may have been added with another device file.
[    18.757] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    18.757] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    18.757] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    18.757] (**) AT Translated Set 2 keyboard: always reports core events
[    18.757] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    18.757] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    18.757] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    18.757] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    18.757] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    18.757] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 14)
[    18.757] (**) Option "xkb_rules" "evdev"
[    18.757] (**) Option "xkb_model" "pc105"
[    18.757] (**) Option "xkb_layout" "gb"
[    18.757] (II) config/udev: Adding input device DualPoint Stick (/dev/input/event19)
[    18.757] (**) DualPoint Stick: Applying InputClass "evdev pointer catchall"
[    18.757] (**) DualPoint Stick: Applying InputClass "trackpoint catchall"
[    18.757] (II) Using input driver 'evdev' for 'DualPoint Stick'
[    18.757] (**) DualPoint Stick: always reports core events
[    18.757] (**) evdev: DualPoint Stick: Device: "/dev/input/event19"
[    18.757] (--) evdev: DualPoint Stick: Vendor 0x2 Product 0x8
[    18.757] (--) evdev: DualPoint Stick: Found 3 mouse buttons
[    18.757] (--) evdev: DualPoint Stick: Found relative axes
[    18.757] (--) evdev: DualPoint Stick: Found x and y relative axes
[    18.757] (II) evdev: DualPoint Stick: Configuring as mouse
[    18.757] (**) Option "Emulate3Buttons" "true"
[    18.757] (**) Option "EmulateWheel" "true"
[    18.757] (**) Option "EmulateWheelButton" "2"
[    18.757] (**) Option "YAxisMapping" "4 5"
[    18.757] (**) evdev: DualPoint Stick: YAxisMapping: buttons 4 and 5
[    18.757] (**) Option "XAxisMapping" "6 7"
[    18.757] (**) evdev: DualPoint Stick: XAxisMapping: buttons 6 and 7
[    18.757] (**) evdev: DualPoint Stick: EmulateWheelButton: 2, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    18.757] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input19/event19"
[    18.757] (II) XINPUT: Adding extended input device "DualPoint Stick" (type: MOUSE, id 15)
[    18.757] (II) evdev: DualPoint Stick: initialized for relative axes.
[    18.757] (**) DualPoint Stick: (accel) keeping acceleration scheme 1
[    18.757] (**) DualPoint Stick: (accel) acceleration profile 0
[    18.757] (**) DualPoint Stick: (accel) acceleration factor: 2.000
[    18.757] (**) DualPoint Stick: (accel) acceleration threshold: 4
[    18.757] (II) config/udev: Adding input device DualPoint Stick (/dev/input/mouse1)
[    18.757] (II) No input driver specified, ignoring this device.
[    18.757] (II) This device may have been added with another device file.
[    18.757] (II) config/udev: Adding input device AlpsPS/2 ALPS DualPoint TouchPad (/dev/input/event20)
[    18.757] (**) AlpsPS/2 ALPS DualPoint TouchPad: Applying InputClass "evdev touchpad catchall"
[    18.757] (**) AlpsPS/2 ALPS DualPoint TouchPad: Applying InputClass "touchpad catchall"
[    18.757] (**) AlpsPS/2 ALPS DualPoint TouchPad: Applying InputClass "Default clickpad buttons"
[    18.757] (II) LoadModule: "synaptics"
[    18.757] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    18.758] (II) Module synaptics: vendor="X.Org Foundation"
[    18.758]     compiled for 1.14.2, module version = 1.7.1
[    18.758]     Module class: X.Org XInput Driver
[    18.758]     ABI class: X.Org XInput driver, version 19.1
[    18.758] (II) Using input driver 'synaptics' for 'AlpsPS/2 ALPS DualPoint TouchPad'
[    18.758] (**) AlpsPS/2 ALPS DualPoint TouchPad: always reports core events
[    18.758] (**) Option "Device" "/dev/input/event20"
[    18.776] (II) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: ignoring touch events for semi-multitouch device
[    18.776] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: x-axis range 0 - 2000 (res 0)
[    18.776] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: y-axis range 0 - 1400 (res 0)
[    18.776] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: pressure range 0 - 127
[    18.776] (II) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: device does not report finger width.
[    18.776] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: buttons: left right middle double triple
[    18.776] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: Vendor 0x2 Product 0x8
[    18.776] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: invalid finger width range.  defaulting to 0 - 15
[    18.776] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: touchpad found
[    18.776] (**) AlpsPS/2 ALPS DualPoint TouchPad: always reports core events
[    18.788] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input20/event20"
[    18.788] (II) XINPUT: Adding extended input device "AlpsPS/2 ALPS DualPoint TouchPad" (type: TOUCHPAD, id 16)
[    18.788] (**) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    18.788] (**) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: (accel) MaxSpeed is now 1.75
[    18.788] (**) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: (accel) AccelFactor is now 0.082
[    18.788] (**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) keeping acceleration scheme 1
[    18.788] (**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) acceleration profile 1
[    18.788] (**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) acceleration factor: 2.000
[    18.788] (**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) acceleration threshold: 4
[    18.788] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: touchpad found
[    18.788] (II) config/udev: Adding input device AlpsPS/2 ALPS DualPoint TouchPad (/dev/input/mouse2)
[    18.788] (**) AlpsPS/2 ALPS DualPoint TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    18.789] (II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event12)
[    18.789] (**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    18.789] (II) Using input driver 'evdev' for 'Dell WMI hotkeys'
[    18.789] (**) Dell WMI hotkeys: always reports core events
[    18.789] (**) evdev: Dell WMI hotkeys: Device: "/dev/input/event12"
[    18.789] (--) evdev: Dell WMI hotkeys: Vendor 0 Product 0
[    18.789] (--) evdev: Dell WMI hotkeys: Found keys
[    18.789] (II) evdev: Dell WMI hotkeys: Configuring as keyboard
[    18.789] (**) Option "config_info" "udev:/sys/devices/virtual/input/input12/event12"
[    18.789] (II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD, id 17)
[    18.789] (**) Option "xkb_rules" "evdev"
[    18.789] (**) Option "xkb_model" "pc105"
[    18.789] (**) Option "xkb_layout" "gb"
[    20.666] (II) NVIDIA(GPU-0): Display (Matrox (CRT-0)) does not support NVIDIA 3D Vision
[    20.666] (II) NVIDIA(GPU-0):     stereo.
[    20.666] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    20.666] (**) NVIDIA(0):     device Matrox (CRT-0) (Using EDID frequencies has been
[    20.666] (**) NVIDIA(0):     enabled on all display devices.)
[    20.667] (II) NVIDIA(GPU-0): Display (Seiko/Epson (DFP-0)) does not support NVIDIA 3D
[    20.667] (II) NVIDIA(GPU-0):     Vision stereo.
[    20.667] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    20.667] (**) NVIDIA(0):     device Seiko/Epson (DFP-0) (Using EDID frequencies has
[    20.667] (**) NVIDIA(0):     been enabled on all display devices.)
[    20.688] (II) NVIDIA(GPU-0): Display (Idek Iiyama PL2409HD (DFP-1)) does not support NVIDIA
[    20.688] (II) NVIDIA(GPU-0):     3D Vision stereo.
[    20.688] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    20.688] (**) NVIDIA(0):     device Idek Iiyama PL2409HD (DFP-1) (Using EDID
[    20.688] (**) NVIDIA(0):     frequencies has been enabled on all display devices.)
[    20.688] (WW) NVIDIA(GPU-0): The EDID for Idek Iiyama PL2409HD (DFP-1) contradicts itself:
[    20.688] (WW) NVIDIA(GPU-0):     mode "1280x720" is specified in the EDID; however, the
[    20.688] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (56.000-76.000 Hz) would
[    20.688] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    20.688] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "1280x720".
[    20.688] (WW) NVIDIA(GPU-0): The EDID for Idek Iiyama PL2409HD (DFP-1) contradicts itself:
[    20.688] (WW) NVIDIA(GPU-0):     mode "720x576" is specified in the EDID; however, the
[    20.688] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (56.000-76.000 Hz) would
[    20.688] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    20.688] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "720x576".
[    20.688] (WW) NVIDIA(GPU-0): The EDID for Idek Iiyama PL2409HD (DFP-1) contradicts itself:
[    20.688] (WW) NVIDIA(GPU-0):     mode "720x576" is specified in the EDID; however, the
[    20.688] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (56.000-76.000 Hz) would
[    20.688] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    20.688] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "720x576".
[    20.688] (WW) NVIDIA(GPU-0): The EDID for Idek Iiyama PL2409HD (DFP-1) contradicts itself:
[    20.688] (WW) NVIDIA(GPU-0):     mode "1280x720" is specified in the EDID; however, the
[    20.688] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (56.000-76.000 Hz) would
[    20.688] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    20.688] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "1280x720".
[    20.688] (WW) NVIDIA(GPU-0): The EDID for Idek Iiyama PL2409HD (DFP-1) contradicts itself:
[    20.688] (WW) NVIDIA(GPU-0):     mode "480x576" is specified in the EDID; however, the
[    20.688] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (56.000-76.000 Hz) would
[    20.688] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    20.688] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "480x576".
[    22.778] (II) NVIDIA(GPU-0): Display (Matrox (CRT-0)) does not support NVIDIA 3D Vision
[    22.778] (II) NVIDIA(GPU-0):     stereo.
[    22.778] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    22.778] (**) NVIDIA(0):     device Matrox (CRT-0) (Using EDID frequencies has been
[    22.778] (**) NVIDIA(0):     enabled on all display devices.)
[    22.779] (II) NVIDIA(GPU-0): Display (Seiko/Epson (DFP-0)) does not support NVIDIA 3D
[    22.779] (II) NVIDIA(GPU-0):     Vision stereo.
[    22.779] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    22.779] (**) NVIDIA(0):     device Seiko/Epson (DFP-0) (Using EDID frequencies has
[    22.779] (**) NVIDIA(0):     been enabled on all display devices.)
[    22.800] (II) NVIDIA(GPU-0): Display (Idek Iiyama PL2409HD (DFP-1)) does not support NVIDIA
[    22.800] (II) NVIDIA(GPU-0):     3D Vision stereo.
[    22.800] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    22.800] (**) NVIDIA(0):     device Idek Iiyama PL2409HD (DFP-1) (Using EDID
[    22.800] (**) NVIDIA(0):     frequencies has been enabled on all display devices.)
[    22.800] (WW) NVIDIA(GPU-0): The EDID for Idek Iiyama PL2409HD (DFP-1) contradicts itself:
[    22.800] (WW) NVIDIA(GPU-0):     mode "1280x720" is specified in the EDID; however, the
[    22.800] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (56.000-76.000 Hz) would
[    22.800] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    22.800] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "1280x720".
[    22.801] (WW) NVIDIA(GPU-0): The EDID for Idek Iiyama PL2409HD (DFP-1) contradicts itself:
[    22.801] (WW) NVIDIA(GPU-0):     mode "720x576" is specified in the EDID; however, the
[    22.801] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (56.000-76.000 Hz) would
[    22.801] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    22.801] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "720x576".
[    22.801] (WW) NVIDIA(GPU-0): The EDID for Idek Iiyama PL2409HD (DFP-1) contradicts itself:
[    22.801] (WW) NVIDIA(GPU-0):     mode "720x576" is specified in the EDID; however, the
[    22.801] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (56.000-76.000 Hz) would
[    22.801] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    22.801] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "720x576".
[    22.801] (WW) NVIDIA(GPU-0): The EDID for Idek Iiyama PL2409HD (DFP-1) contradicts itself:
[    22.801] (WW) NVIDIA(GPU-0):     mode "1280x720" is specified in the EDID; however, the
[    22.801] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (56.000-76.000 Hz) would
[    22.801] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    22.801] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "1280x720".
[    22.801] (WW) NVIDIA(GPU-0): The EDID for Idek Iiyama PL2409HD (DFP-1) contradicts itself:
[    22.801] (WW) NVIDIA(GPU-0):     mode "480x576" is specified in the EDID; however, the
[    22.801] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (56.000-76.000 Hz) would
[    22.801] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    22.801] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "480x576".
[    46.503] (II) NVIDIA(GPU-0): Display (Matrox (CRT-0)) does not support NVIDIA 3D Vision
[    46.503] (II) NVIDIA(GPU-0):     stereo.
[    46.503] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    46.503] (**) NVIDIA(0):     device Matrox (CRT-0) (Using EDID frequencies has been
[    46.503] (**) NVIDIA(0):     enabled on all display devices.)
[    46.503] (II) NVIDIA(GPU-0): Display (Seiko/Epson (DFP-0)) does not support NVIDIA 3D
[    46.503] (II) NVIDIA(GPU-0):     Vision stereo.
[    46.503] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    46.503] (**) NVIDIA(0):     device Seiko/Epson (DFP-0) (Using EDID frequencies has
[    46.503] (**) NVIDIA(0):     been enabled on all display devices.)
[    46.524] (II) NVIDIA(GPU-0): Display (Idek Iiyama PL2409HD (DFP-1)) does not support NVIDIA
[    46.524] (II) NVIDIA(GPU-0):     3D Vision stereo.
[    46.524] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    46.524] (**) NVIDIA(0):     device Idek Iiyama PL2409HD (DFP-1) (Using EDID
[    46.524] (**) NVIDIA(0):     frequencies has been enabled on all display devices.)
[    46.525] (WW) NVIDIA(GPU-0): The EDID for Idek Iiyama PL2409HD (DFP-1) contradicts itself:
[    46.525] (WW) NVIDIA(GPU-0):     mode "1280x720" is specified in the EDID; however, the
[    46.525] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (56.000-76.000 Hz) would
[    46.525] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    46.525] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "1280x720".
[    46.525] (WW) NVIDIA(GPU-0): The EDID for Idek Iiyama PL2409HD (DFP-1) contradicts itself:
[    46.525] (WW) NVIDIA(GPU-0):     mode "720x576" is specified in the EDID; however, the
[    46.525] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (56.000-76.000 Hz) would
[    46.525] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    46.525] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "720x576".
[    46.525] (WW) NVIDIA(GPU-0): The EDID for Idek Iiyama PL2409HD (DFP-1) contradicts itself:
[    46.525] (WW) NVIDIA(GPU-0):     mode "720x576" is specified in the EDID; however, the
[    46.525] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (56.000-76.000 Hz) would
[    46.525] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    46.525] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "720x576".
[    46.525] (WW) NVIDIA(GPU-0): The EDID for Idek Iiyama PL2409HD (DFP-1) contradicts itself:
[    46.525] (WW) NVIDIA(GPU-0):     mode "1280x720" is specified in the EDID; however, the
[    46.525] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (56.000-76.000 Hz) would
[    46.525] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    46.525] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "1280x720".
[    46.525] (WW) NVIDIA(GPU-0): The EDID for Idek Iiyama PL2409HD (DFP-1) contradicts itself:
[    46.525] (WW) NVIDIA(GPU-0):     mode "480x576" is specified in the EDID; however, the
[    46.525] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (56.000-76.000 Hz) would
[    46.525] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    46.525] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "480x576".
[    46.684] (II) NVIDIA(GPU-0): Display (Matrox (CRT-0)) does not support NVIDIA 3D Vision
[    46.684] (II) NVIDIA(GPU-0):     stereo.
[    46.684] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    46.684] (**) NVIDIA(0):     device Matrox (CRT-0) (Using EDID frequencies has been
[    46.684] (**) NVIDIA(0):     enabled on all display devices.)
[    46.685] (II) NVIDIA(GPU-0): Display (Seiko/Epson (DFP-0)) does not support NVIDIA 3D
[    46.685] (II) NVIDIA(GPU-0):     Vision stereo.
[    46.685] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    46.685] (**) NVIDIA(0):     device Seiko/Epson (DFP-0) (Using EDID frequencies has
[    46.685] (**) NVIDIA(0):     been enabled on all display devices.)
[    46.706] (II) NVIDIA(GPU-0): Display (Idek Iiyama PL2409HD (DFP-1)) does not support NVIDIA
[    46.706] (II) NVIDIA(GPU-0):     3D Vision stereo.
[    46.706] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    46.706] (**) NVIDIA(0):     device Idek Iiyama PL2409HD (DFP-1) (Using EDID
[    46.706] (**) NVIDIA(0):     frequencies has been enabled on all display devices.)
[    46.706] (WW) NVIDIA(GPU-0): The EDID for Idek Iiyama PL2409HD (DFP-1) contradicts itself:
[    46.706] (WW) NVIDIA(GPU-0):     mode "1280x720" is specified in the EDID; however, the
[    46.706] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (56.000-76.000 Hz) would
[    46.706] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    46.706] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "1280x720".
[    46.707] (WW) NVIDIA(GPU-0): The EDID for Idek Iiyama PL2409HD (DFP-1) contradicts itself:
[    46.707] (WW) NVIDIA(GPU-0):     mode "720x576" is specified in the EDID; however, the
[    46.707] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (56.000-76.000 Hz) would
[    46.707] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    46.707] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "720x576".
[    46.707] (WW) NVIDIA(GPU-0): The EDID for Idek Iiyama PL2409HD (DFP-1) contradicts itself:
[    46.707] (WW) NVIDIA(GPU-0):     mode "720x576" is specified in the EDID; however, the
[    46.707] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (56.000-76.000 Hz) would
[    46.707] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    46.707] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "720x576".
[    46.707] (WW) NVIDIA(GPU-0): The EDID for Idek Iiyama PL2409HD (DFP-1) contradicts itself:
[    46.707] (WW) NVIDIA(GPU-0):     mode "1280x720" is specified in the EDID; however, the
[    46.707] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (56.000-76.000 Hz) would
[    46.707] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    46.707] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "1280x720".
[    46.707] (WW) NVIDIA(GPU-0): The EDID for Idek Iiyama PL2409HD (DFP-1) contradicts itself:
[    46.707] (WW) NVIDIA(GPU-0):     mode "480x576" is specified in the EDID; however, the
[    46.707] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (56.000-76.000 Hz) would
[    46.707] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    46.707] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "480x576".
[    47.264] (II) XKB: reuse xkmfile /var/lib/xkb/server-B8CD4FE5A1833D7AB4B402792017A55B628FCF2D.xkm
[    47.273] (II) XKB: reuse xkmfile /var/lib/xkb/server-B8CD4FE5A1833D7AB4B402792017A55B628FCF2D.xkm
[    47.998] (II) XKB: reuse xkmfile /var/lib/xkb/server-07844D531AFAE8C05AD2DE44539CA82502952248.xkm
[    58.632] (II) NVIDIA(GPU-0): Display (Matrox (CRT-0)) does not support NVIDIA 3D Vision
[    58.632] (II) NVIDIA(GPU-0):     stereo.
[    58.632] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    58.632] (**) NVIDIA(0):     device Matrox (CRT-0) (Using EDID frequencies has been
[    58.632] (**) NVIDIA(0):     enabled on all display devices.)
[    58.633] (II) NVIDIA(GPU-0): Display (Seiko/Epson (DFP-0)) does not support NVIDIA 3D
[    58.633] (II) NVIDIA(GPU-0):     Vision stereo.
[    58.633] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    58.633] (**) NVIDIA(0):     device Seiko/Epson (DFP-0) (Using EDID frequencies has
[    58.633] (**) NVIDIA(0):     been enabled on all display devices.)
[    58.654] (II) NVIDIA(GPU-0): Display (Idek Iiyama PL2409HD (DFP-1)) does not support NVIDIA
[    58.654] (II) NVIDIA(GPU-0):     3D Vision stereo.
[    58.654] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    58.654] (**) NVIDIA(0):     device Idek Iiyama PL2409HD (DFP-1) (Using EDID
[    58.654] (**) NVIDIA(0):     frequencies has been enabled on all display devices.)
[    58.654] (WW) NVIDIA(GPU-0): The EDID for Idek Iiyama PL2409HD (DFP-1) contradicts itself:
[    58.654] (WW) NVIDIA(GPU-0):     mode "1280x720" is specified in the EDID; however, the
[    58.654] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (56.000-76.000 Hz) would
[    58.654] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    58.654] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "1280x720".
[    58.654] (WW) NVIDIA(GPU-0): The EDID for Idek Iiyama PL2409HD (DFP-1) contradicts itself:
[    58.654] (WW) NVIDIA(GPU-0):     mode "720x576" is specified in the EDID; however, the
[    58.654] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (56.000-76.000 Hz) would
[    58.654] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    58.654] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "720x576".
[    58.654] (WW) NVIDIA(GPU-0): The EDID for Idek Iiyama PL2409HD (DFP-1) contradicts itself:
[    58.654] (WW) NVIDIA(GPU-0):     mode "720x576" is specified in the EDID; however, the
[    58.654] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (56.000-76.000 Hz) would
[    58.654] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    58.654] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "720x576".
[    58.654] (WW) NVIDIA(GPU-0): The EDID for Idek Iiyama PL2409HD (DFP-1) contradicts itself:
[    58.654] (WW) NVIDIA(GPU-0):     mode "1280x720" is specified in the EDID; however, the
[    58.654] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (56.000-76.000 Hz) would
[    58.654] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    58.654] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "1280x720".
[    58.654] (WW) NVIDIA(GPU-0): The EDID for Idek Iiyama PL2409HD (DFP-1) contradicts itself:
[    58.654] (WW) NVIDIA(GPU-0):     mode "480x576" is specified in the EDID; however, the
[    58.654] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (56.000-76.000 Hz) would
[    58.654] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    58.654] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "480x576".
[    69.841] (II) NVIDIA(GPU-0): Display (Matrox (CRT-0)) does not support NVIDIA 3D Vision
[    69.841] (II) NVIDIA(GPU-0):     stereo.
[    69.841] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    69.841] (**) NVIDIA(0):     device Matrox (CRT-0) (Using EDID frequencies has been
[    69.841] (**) NVIDIA(0):     enabled on all display devices.)
[    69.842] (II) NVIDIA(GPU-0): Display (Seiko/Epson (DFP-0)) does not support NVIDIA 3D
[    69.842] (II) NVIDIA(GPU-0):     Vision stereo.
[    69.842] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    69.842] (**) NVIDIA(0):     device Seiko/Epson (DFP-0) (Using EDID frequencies has
[    69.842] (**) NVIDIA(0):     been enabled on all display devices.)
[    69.863] (II) NVIDIA(GPU-0): Display (Idek Iiyama PL2409HD (DFP-1)) does not support NVIDIA
[    69.863] (II) NVIDIA(GPU-0):     3D Vision stereo.
[    69.863] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    69.863] (**) NVIDIA(0):     device Idek Iiyama PL2409HD (DFP-1) (Using EDID
[    69.863] (**) NVIDIA(0):     frequencies has been enabled on all display devices.)
[    69.863] (WW) NVIDIA(GPU-0): The EDID for Idek Iiyama PL2409HD (DFP-1) contradicts itself:
[    69.863] (WW) NVIDIA(GPU-0):     mode "1280x720" is specified in the EDID; however, the
[    69.863] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (56.000-76.000 Hz) would
[    69.863] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    69.863] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "1280x720".
[    69.863] (WW) NVIDIA(GPU-0): The EDID for Idek Iiyama PL2409HD (DFP-1) contradicts itself:
[    69.863] (WW) NVIDIA(GPU-0):     mode "720x576" is specified in the EDID; however, the
[    69.863] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (56.000-76.000 Hz) would
[    69.863] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    69.863] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "720x576".
[    69.863] (WW) NVIDIA(GPU-0): The EDID for Idek Iiyama PL2409HD (DFP-1) contradicts itself:
[    69.863] (WW) NVIDIA(GPU-0):     mode "720x576" is specified in the EDID; however, the
[    69.863] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (56.000-76.000 Hz) would
[    69.863] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    69.864] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "720x576".
[    69.864] (WW) NVIDIA(GPU-0): The EDID for Idek Iiyama PL2409HD (DFP-1) contradicts itself:
[    69.864] (WW) NVIDIA(GPU-0):     mode "1280x720" is specified in the EDID; however, the
[    69.864] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (56.000-76.000 Hz) would
[    69.864] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    69.864] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "1280x720".
[    69.864] (WW) NVIDIA(GPU-0): The EDID for Idek Iiyama PL2409HD (DFP-1) contradicts itself:
[    69.864] (WW) NVIDIA(GPU-0):     mode "480x576" is specified in the EDID; however, the
[    69.864] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (56.000-76.000 Hz) would
[    69.864] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    69.864] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "480x576".
[   130.187] (II) NVIDIA(0): Setting mode "CRT-0:nvidia-auto-select@3840x1200+1920+0,DFP-0:NULL,DFP-1:nvidia-auto-select@1920x1080+0+0"
aa@aa-Latitude-E6530:~$ 
```



I would really appreciate your help!!!

Many thanks!!!!

---

### Post by Toz on 2013-11-27
*Moved post to its own thread and added code tags.*

---

### Post by Toz on 2013-11-27
Doess adding:
```
Option "RegistryDwords" "EnableBrightnessControl=1"
```
...to the "Device" section of you **/etc/X11/xorg.conf** file (and logging out and back in again) return the brightness control for you?

---

### Post by aa-hcl on 2013-11-28
Hi, I have installed 13.10 to a new hard disk on Dell E6530 laptop and I can not change the brightness of the monitor:

- Fn+up or Fn+down keys do NOT work (INTERESTING: they DO work at the BIOS stage and I can set brightness to the required level, for example the minimum level, and this level of brightness will stay after login to ubuntu)
- in the settings menu the slider to change brightness does exist, but it does not change the brightness
- in the command line if I try to set the brightness by something like "echo 20 > /sys/class/backlight/acpi_video0/brightness" (as root) - it does change the value of /sys/class/backlight/acpi_video0/brightness and the value of /sys/class/backlight/acpi_video0/actual_brightness, but it does NOT change the brightness of the monitor

Initially I thought that the nvidia driver is to blame, but with doing complete uninstall of nvidia driver (by sudo apt-get purge nvidia*) does not solve the problem, without the nvidia driver it is still not working.

IMPORTANT detail:  I had the laptop working under 13.10 with brightness changing all working BUT with previous hard drive (which is now nearly dead) - I had a hard drive failure and had to re-install the system from scratch with fresh 13.10 installation. The previous system was with fresh 12.10 install and it was then upgraded to 13.04 and then with 13.10. Unfortunately, I did not make a note how I solved the problem when I upgraded to 13.10 from 13.04 - I also had the problem fo not being able to change the brightness.

This means that I do know that my laptop can have the brightness control under ubuntu 13.10

I would really appreciate your help!!!

Many thanks!!!!

---

### Post by Toz on 2013-11-28
*Duplicate threads merged. I had moved your previous post to its own thread.*

Please have a look at my post #3 and see if it works.

---

### Post by aa-hcl on 2013-11-28
Hi Toz,

thank you very much for your reply.

I have created xorg.conf file using nvidia-settings application and tried to reboot with the line 
Option "RegistryDwords" "EnableBrightnessControl=1"  included (see below). 

Unfortunately, the brightness still does not work.

for information here is the xorg file:

```
aa@aa-Latitude-E6530:~$ cat /etc/X11/xorg.conf
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 319.60  (buildd@komainu)  Wed Oct  2 15:12:10 UTC 2013

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Seiko/Epson"
    HorizSync       53.8 - 66.7
    VertRefresh     40.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "NVS 5200M"
    Option         "RegistryDwords" "EnableBrightnessControl=1"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "Stereo" "0"
    Option         "nvidiaXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

aa@aa-Latitude-E6530:~$ 

 
```

---

### Post by Toz on 2013-11-29
Hmmm, it seems like the nvidia driver is somehow blocking the brightness control. What version of the nvidia driver are you using? 

Can you post back the /var/log/Xorg.0.log again as well as /var/log/dmesg? Like this:
```
pastebinit /var/log/Xorg.0.log
pastebinit /var/log/dmesg
```
...and post back the links that are generated? If you get an error message that pastebinit is not installed, it can be installed via:
```
sudo apt-get install pastebinit
```

Finally, you might want to give the [nvidiabl]("https://github.com/guillaumezin/nvidiabl") module a try - according to the laptops.h file, the E6530 appears to be supported.

---

### Post by aa-hcl on 2013-12-02
Many thanks for your help!

I have installed the pastebinit and here are the links:

aa@aa-Latitude-E6530:~$ pastebinit /var/log/Xorg.0.log
[http://paste.ubuntu.com/6512008/](http://paste.ubuntu.com/6512008/)

aa@aa-Latitude-E6530:~$ pastebinit /var/log/dmesg
[http://paste.ubuntu.com/6512011/](http://paste.ubuntu.com/6512011/)

I am trying to look at nvidiabl now... and will post the result.

I hope the info in the log files will help to understand what is going wrong with the monitor backlight.

---

### Post by aa-hcl on 2013-12-02
Hi,

Installation of the nvidiabl module failed:

```
 aa@aa-Latitude-E6530:~/Downloads$ sudo dpkg -i nvidiabl-dkms_0.85_all.deb 
dpkg-deb: error: `nvidiabl-dkms_0.85_all.deb' is not a debian format archive
dpkg: error processing nvidiabl-dkms_0.85_all.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 nvidiabl-dkms_0.85_all.deb
aa@aa-Latitude-E6530:~/Downloads$  
```

I tried the same wtih 0.84 version and the result is the same.

I then downloaded the source code and tried:

```
 aa@aa-Latitude-E6530:~/Downloads$ sudo dkms ldtarball --archive=nvidiabl-0.85-source-only.dkms.tar.gz build install
tar: This does not look like a tar archive
tar: Skipping to next header
tar: Exiting with failure status due to previous errors
Error! No valid dkms.conf in dkms_source_tree or dkms_binaries_only.
nvidiabl-0.85-source-only.dkms.tar.gz is not a valid DKMS tarball. 
```

I do not know why it can not recognize the *.deb file or the tar.bz files.

---

### Post by Toz on 2013-12-02
I get the same error message when I try to download directly from the Install directory. However, if you "Download ZIP" from the main git page, it will download the zip file from which I extracted the deb file and it was okay.

---

### Post by aa-hcl on 2013-12-03
I managed to install nvidiabl: I downloaded zip and then:

```
 
aa@aa-Latitude-E6530:~/Downloads/nvidiabl-master/install/deb$ sudo dpkg -i nvidiabl-dkms_0.85_all.deb 
[sudo] password for aa: 
Selecting previously unselected package nvidiabl-dkms.
(Reading database ... 364505 files and directories currently installed.)
Unpacking nvidiabl-dkms (from nvidiabl-dkms_0.85_all.deb) ...
Setting up nvidiabl-dkms (0.85) ...
Loading new nvidiabl-0.85 DKMS files...
First Installation: checking all kernels...
Building only for 3.11.0-13-generic
Building for architecture x86_64
Building initial module for 3.11.0-13-generic
Done.

nvidiabl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.11.0-13-generic/updates/dkms/

/etc/modprobe.d/dkms.conf: added '# Prevent conflicts with nvidiabl'
/etc/modprobe.d/dkms.conf: added 'blacklist nvidia_bl'
/etc/modprobe.d/dkms.conf: added 'blacklist nvbacklight'
/etc/modprobe.d/dkms.conf: added 'blacklist mbp_nvidia_bl'
/etc/modprobe.d/dkms.conf: added '# End of entries added for nvidiabl'
depmod.......

DKMS: install completed.
aa@aa-Latitude-E6530:~/Downloads/nvidiabl-master/install/deb$ 


```

I then also added the nvidiabl to the the /etc/modules:

```
 aa@aa-Latitude-E6530:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
# Parameters can be specified after the module name.

# added 03 dec 13 - nvidia backlight driver
nvidiabl

lp
rtc

# Generated by sensors-detect on Fri Nov 22 13:25:46 2013
# Chip drivers
coretemp
aa@aa-Latitude-E6530:~$ 


```

I then rebooted, but brightness still does not work: Fn keys do not work, but I also can not change the brightness through the system settings GUI (brightness slider there can be moved, but this does not change brightness).

I checked that nvidiabl module is installed:

```
 aa@aa-Latitude-E6530:~$ dkms status
nvidia-319-updates, 319.60, 3.11.0-13-generic, x86_64: installed
nvidiabl, 0.85, 3.11.0-13-generic, x86_64: installed
vboxhost, 4.3.2, 3.11.0-13-generic, x86_64: installed


```

The nvidiabl module does not work for me or I did not load it properly. I do not know how to check using dkms what modules are currently loaded.

My only way to change brightness of my laptop screen now is to do it during startup at the moment before the grub menu appears. At this stage the Fn keys are working and I can set the brightness to minimum, for example.

My guess is that it is probably not only the nvidia driver that causes the brightness problem. I tried to remove the nvidia driver completely  ( using dpkg --purge) and use the default ubuntu driver - the brightness control does not work this way as well. Loading from live 13.10 DVD - the brightness also does not work. In earlier ubuntu version (12.10) the brightness works even from the live CD.

Your help will be really appreciated.

---

### Post by Toz on 2013-12-03
The nvidiabl module will only give you access to a manageable backlight interface. You'll need to do some scripting (or use other scripts) to control the brightness. There are some notes about it at the nvidiabl site. You might be able to get it to use the built-in system functionality if it is the only backlight interface available on your system.

With the nvidiabl module loaded:
```
lsmod  |grep nvidiabl
```
...do you now have an nvidiabl (or nvidia_backlight) interface?
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
```
...(please post back the results).

If so, try directly echoing values between 0 and the contents of /sys/class/backlight/<INTERFACE>/max_brightness in to the brightness file. Something like:
```
echo XX | sudo tee /sys/class/backlight/YY/brightness
```
...where XX is a numberical value between 0 and the contents of the associated max_brightness file and YY is the interface (directory) name.

If you need a script, we can create one - I've done others here in the forums.

---

### Post by aa-hcl on 2013-12-03
Hi, it looks like the nvidiabl module is NOT loaded and I guess for this reason i do not have the nvidiabl brightness interface:

```
aa@aa-Latitude-E6530:~$ lsmod | grep nvidia
nvidia               9451814  104 
drm                   296739  2 nvidia
aa@aa-Latitude-E6530:~$ lsmod | grep nvidiabl
aa@aa-Latitude-E6530:~$ for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
/sys/class/backlight/acpi_video0
60
60
100
aa@aa-Latitude-E6530:~$ sudo lsmod | grep nvidiabl
[sudo] password for aa: 
aa@aa-Latitude-E6530:~$ sudo lsmod | grep nvidia
nvidia               9451814  104 
drm                   296739  2 nvidia
aa@aa-Latitude-E6530:~$ 

 
```

 Although I have the nvidiabl line in /etc/modules,  for some reason nvidiabl module is not loaded. How I can make it loaded?

Many thanks!

---

### Post by Toz on 2013-12-03
> **aa-hcl said:**
> Although I have the nvidiabl line in /etc/modules,  for some reason nvidiabl module is not loaded. How I can make it loaded?
Try:
```
sudo modprobe nvidiabl
```
...see if any error messages are displayed.

---

### Post by aa-hcl on 2013-12-03
I tried, it does not work:

```
aa@aa-Latitude-E6530:~$ sudo modprobe nvidiabl
[sudo] password for aa: 
ERROR: could not insert 'nvidiabl': No such device
aa@aa-Latitude-E6530:~$ dkms status
nvidia-319-updates, 319.60, 3.11.0-13-generic, x86_64: installed
nvidiabl, 0.85, 3.11.0-13-generic, x86_64: installed
vboxhost, 4.3.2, 3.11.0-13-generic, x86_64: installed
aa@aa-Latitude-E6530:~$ 

 
```

---

### Post by Toz on 2013-12-03
I wonder if you're being affected by [this]("https://github.com/guillaumezin/nvidiabl/issues/61"). It looks like a missing declare in nvidiabl-gpu.h. You can add it in yourself, but you'll have manually compile the module. I checked the code and it hasn't been added in yet.

---

### Post by aa-hcl on 2013-12-03
You are probably right, I get very similar message as in [https://github.com/guillaumezin/nvidiabl/issues/61:](https://github.com/guillaumezin/nvidiabl/issues/61:)

```

aa@aa-Latitude-E6530:~$ cat /sys/class/dmi/id/sys_vendor
Dell Inc.
aa@aa-Latitude-E6530:~$ cat /sys/class/dmi/id/product_name 
Latitude E6530
aa@aa-Latitude-E6530:~$ cat /var/log/dmesg | grep nvidiabl
[   10.643403] nvidiabl: loading driver version 0.85
[   10.643407] nvidiabl: Dell Inc. - Latitude E6530 model detected in DMI tables
[   10.643411] nvidiabl: No supported Nvidia graphics adapter found
[   10.891382] nvidiabl: loading driver version 0.85
[   10.891383] nvidiabl: Dell Inc. - Latitude E6530 model detected in DMI tables
[   10.891386] nvidiabl: No supported Nvidia graphics adapter found

```

I will try to correct it as you suggest and will post the result.

---

### Post by aa-hcl on 2013-12-03
It WORKS !!!

As you suggested I added the following two lines to the file "nvidiabl-gpu.h"

```
 /* NVS 5200M */
NVIDIABL_DECLARE_GPU_MODEL(0x0dfc, nv5x_driver_data),    

```

I then change in the file "Makefile" the version of nvidiabl to 0.86. (I tried first not changing it, but dkms complained that 0.85 version already exists)
After that I build the module:

```

aa@aa-Latitude-E6530:~$ cd Downloads/nvidiabl-master/
aa@aa-Latitude-E6530:~/Downloads/nvidiabl-master$ make dkms-install
find . \( -name dkms.conf -o -name '.tmp*' -o -name '.*.cmd' -o -name '*.symvers' -o -name '*.order' -o -name '*.markers' -o -name '*.mod.c' -o -name '*.ko' -o -name '*.o' \) -print0 | xargs -0 rm -Rf
sudo mkdir /usr/src/nvidiabl-0.86
[sudo] password for aa: 
sudo cp -rf * /usr/src/nvidiabl-0.86
sudo rm -rf /usr/src/nvidiabl-0.86/.git /usr/src/nvidiabl-0.86/scripts
sudo dkms add build install -m nvidiabl -v 0.86

Creating symlink /var/lib/dkms/nvidiabl/0.86/source ->
                 /usr/src/nvidiabl-0.86

DKMS: add completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=3.11.0-14-generic -C /lib/modules/3.11.0-14-generic/build SUBDIRS=/var/lib/dkms/nvidiabl/0.86/build modules.....
cleaning build area....

DKMS: build completed.

nvidiabl:
Running module version sanity check.
 - Original module
   - This kernel never originally had a module by this name
 - Installation
   - Installing to /lib/modules/3.11.0-14-generic/updates/dkms/

depmod......

DKMS: install completed.

```

I then added the module and checked that it is loaded by 

```
 
aa@aa-Latitude-E6530:~/Downloads/nvidiabl-master$ sudo modprobe nvidiabl
aa@aa-Latitude-E6530:~/Downloads/nvidiabl-master$ lsmod
Module                  Size  Used by
nvidiabl               45584  0 
....

```

After this operation I finally got the nvidiabl interface:

```

aa@aa-Latitude-E6530:~$ for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
/sys/class/backlight/acpi_video0
85
86
100
/sys/class/backlight/nvidia_backlight
83
83
127


```

Now I can change the brightness by typing the following commands as root:

for minimum brightness:

```

 root@aa-Latitude-E6530:/home/aa# echo 0 > /sys/class/backlight/nvidia_backlight/brightness 

```

for maximum brightness:

```

root@aa-Latitude-E6530:/home/aa# echo 100 > /sys/class/backlight/nvidia_backlight/brightness

```

and any values between 0 and 100 will set the brightness accordingly.

The next step will be to create the link between the keys combination (i.e. Fn+up) to change the brightness using the above commands through the corresponding script.

MANY THANKS FOR YOUR HELP!!!!

---

### Post by aa-hcl on 2013-12-03
I marked the thread as solved.

However, it is still an enigma for me why:

- it all (brightness with Fn keys) worked before on the same laptop with 13.10 ubuntu (but not freshly installed - upgraded from 12.10 and 13.04)  with the old (now broken) hard drive (possibly I will be able to find this out if I manage to do "postmortem" examination of the "dead" harddrive)

- why without the nvidia driver installed (i.e. by booting from live CD) the brightness still does not work under 13.10, but works under earlier versions....

Many-many thanks again !!!

---

### Post by Toz on 2013-12-03
> **aa-hcl said:**
> I marked the thread as solved.

However, it is still an enigma for me why:

- it all (brightness with Fn keys) worked before on the same laptop with 13.10 ubuntu (but not freshly installed - upgraded from 12.10 and 13.04)  with the old (now broken) hard drive (possibly I will be able to find this out if I manage to do "postmortem" examination of the "dead" harddrive)
I would think a configuration setting but the only one I know of is the EnableBrightnessControl and we tried that and it didn't work. Maybe there is another setting? If you do postmortem, try to get kernel and driver versions as well.

> - why without the nvidia driver installed (i.e. by booting from live CD) the brightness still does not work under 13.10, but works under earlier versions....
I would guess a kernel issue. Or possibly a kernel and nouveau driver issue. You could open a bug report about this and see if you can get it fixed for the 14.04 LTS release (so you don't need nvidiabl to get access to brightness controls).

---

### Post by Toz on 2013-12-04
> **aa-hcl said:**
> 
After this operation I finally got the nvidiabl interface:

```

aa@aa-Latitude-E6530:~$ for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
/sys/class/backlight/acpi_video0
85
86
100
/sys/class/backlight/nvidia_backlight
83
83
127


```


Just thought of something: does using the **acpi_backlight=vendor** kernel boot parameter remove the acpi_video0 interface and leave you with only the nvidia_backlight one and if so, do the brightness controls work automatically again because there is only one backlight interface recognized by the system?

---

### Post by aa-hcl on 2013-12-09
Hi,

I added **acpi_backlight=vendor** and with the following boot line:

```
aa@aa-Latitude-E6530:~$ cat /proc/cmdline 
BOOT_IMAGE=/boot/vmlinuz-3.11.0-14-generic root=UUID=c86aca8f-c879-4a03-a76a-7effda7f037d ro quiet splash acpi_backlight=vendor

```

I got the dell backlight interface instead of the acpi interface - in addition to nvidiabl:

```

aa@aa-Latitude-E6530:~$ for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
/sys/class/backlight/dell_backlight
15
9
15
/sys/class/backlight/nvidia_backlight
100
100
127

```

The Fn keys do not change brightness as before and in the system settings the brightness can not be changed as well. The only way I can now change the brightness changed is by (100 - for maximum brightness)

```
 
aa@aa-Latitude-E6530:~$ echo 100 | sudo tee /sys/class/backlight/nvidia_backlight/brightness 
100

```

another VERY STRANGE thing:  sometimes I get the brightness changed when I open a new window to firefox: the brightness goes to the default level set by the  BIOS (in this case the value for /sys/class/backlight/nvidia_backlight/brightness was not changed).
However, this did not happen always, so it might be just another error.


I would really welcome any comments!

---

### Post by Toz on 2013-12-09
You should have a module called dell-laptop loaded:
```
lsmod | grep dell
```

Try removing it:
```
sudo modprobe -r dell-laptop
```

If there are no errors, check your backlight interfaces again:
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
```
...and if there is only one (nvidia_backlight), try the function keys/brightness sliders again. (Note: you may have to blacklist the dell-laptop module and restart to test fully).

---

