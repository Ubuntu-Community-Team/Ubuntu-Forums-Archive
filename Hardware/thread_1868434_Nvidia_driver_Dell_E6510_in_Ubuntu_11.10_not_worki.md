---
title: "Nvidia driver Dell E6510 in Ubuntu 11.10 not working"
date: 2011-10-24
forum: Hardware
---

### Post by kodiakz on 2011-10-24
Hello,
I have a fresh install of 11.10 amd64 and try to install nvidia-drivers. I had no problems running them with 10.10. I tried to install both versions from the repo, 273 and 280, and both are not working.

The result of a reboot is just a console view with no prompt. Last message is something python related.

Here is my output from /var/log/Xorg.0.log:
```

[     6.161] (II) Loading extension XFree86-VidModeExtension
[     6.161] (II) Loading extension XFree86-DGA
[     6.161] (II) Loading extension DPMS
[     6.161] (II) Loading extension XVideo
[     6.161] (II) Loading extension XVideo-MotionCompensation
[     6.161] (II) Loading extension X-Resource
[     6.161] (II) LoadModule: "dbe"
[     6.162] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[     6.162] (II) Module dbe: vendor="X.Org Foundation"
[     6.162] 	compiled for 1.10.4, module version = 1.0.0
[     6.162] 	Module class: X.Org Server Extension
[     6.162] 	ABI class: X.Org Server Extension, version 5.0
[     6.162] (II) Loading extension DOUBLE-BUFFER
[     6.162] (II) LoadModule: "glx"
[     6.162] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[     6.162] (II) Module glx: vendor="X.Org Foundation"
[     6.162] 	compiled for 1.10.4, module version = 1.0.0
[     6.162] 	ABI class: X.Org Server Extension, version 5.0
[     6.162] (==) AIGLX enabled
[     6.162] (II) Loading extension GLX
[     6.162] (II) LoadModule: "record"
[     6.163] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[     6.163] (II) Module record: vendor="X.Org Foundation"
[     6.163] 	compiled for 1.10.4, module version = 1.13.0
[     6.163] 	Module class: X.Org Server Extension
[     6.163] 	ABI class: X.Org Server Extension, version 5.0
[     6.163] (II) Loading extension RECORD
[     6.163] (II) LoadModule: "dri"
[     6.163] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[     6.163] (II) Module dri: vendor="X.Org Foundation"
[     6.163] 	compiled for 1.10.4, module version = 1.0.0
[     6.163] 	ABI class: X.Org Server Extension, version 5.0
[     6.163] (II) Loading extension XFree86-DRI
[     6.163] (II) LoadModule: "dri2"
[     6.164] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[     6.164] (II) Module dri2: vendor="X.Org Foundation"
[     6.164] 	compiled for 1.10.4, module version = 1.2.0
[     6.164] 	ABI class: X.Org Server Extension, version 5.0
[     6.164] (II) Loading extension DRI2
[     6.164] (==) Matched nvidia as autoconfigured driver 0
[     6.164] (==) Matched nouveau as autoconfigured driver 1
[     6.164] (==) Matched nv as autoconfigured driver 2
[     6.164] (==) Matched vesa as autoconfigured driver 3
[     6.164] (==) Matched fbdev as autoconfigured driver 4
[     6.164] (==) Assigned the driver to the xf86ConfigLayout
[     6.164] (II) LoadModule: "nvidia"
[     6.166] (WW) Warning, couldn't open module nvidia
[     6.166] (II) UnloadModule: "nvidia"
[     6.166] (II) Unloading nvidia
[     6.166] (EE) Failed to load module "nvidia" (module does not exist, 0)
[     6.166] (II) LoadModule: "nouveau"
[     6.167] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[     6.167] (II) Module nouveau: vendor="X.Org Foundation"
[     6.167] 	compiled for 1.10.1, module version = 0.0.16
[     6.167] 	Module class: X.Org Video Driver
[     6.167] 	ABI class: X.Org Video Driver, version 10.0
[     6.167] (II) LoadModule: "nv"
[     6.168] (WW) Warning, couldn't open module nv
[     6.168] (II) UnloadModule: "nv"
[     6.168] (II) Unloading nv
[     6.168] (EE) Failed to load module "nv" (module does not exist, 0)
[     6.168] (II) LoadModule: "vesa"
[     6.168] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     6.168] (II) Module vesa: vendor="X.Org Foundation"
[     6.168] 	compiled for 1.10.2, module version = 2.3.0
[     6.168] 	Module class: X.Org Video Driver
[     6.168] 	ABI class: X.Org Video Driver, version 10.0
[     6.168] (II) LoadModule: "fbdev"
[     6.168] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     6.168] (II) Module fbdev: vendor="X.Org Foundation"
[     6.168] 	compiled for 1.10.0, module version = 0.4.2
[     6.168] 	ABI class: X.Org Video Driver, version 10.0
[     6.168] (II) NOUVEAU driver Date:   Thu Mar 24 02:13:12 2011 +1000
[     6.168] (II) NOUVEAU driver for NVIDIA chipset families :
[     6.168] 	RIVA TNT        (NV04)
[     6.169] 	RIVA TNT2       (NV05)
[     6.169] 	GeForce 256     (NV10)
[     6.169] 	GeForce 2       (NV11, NV15)
[     6.169] 	GeForce 4MX     (NV17, NV18)
[     6.169] 	GeForce 3       (NV20)
[     6.169] 	GeForce 4Ti     (NV25, NV28)
[     6.169] 	GeForce FX      (NV3x)
[     6.169] 	GeForce 6       (NV4x)
[     6.169] 	GeForce 7       (G7x)
[     6.169] 	GeForce 8       (G8x)
[     6.169] 	GeForce GTX 200 (NVA0)
[     6.169] 	GeForce GTX 400 (NVC0)
[     6.169] (II) VESA: driver for VESA chipsets: vesa
[     6.169] (II) FBDEV: driver for framebuffer: fbdev
[     6.169] (++) using VT number 7

[     6.169] drmOpenDevice: node name is /dev/dri/card0
[     6.169] drmOpenDevice: open result is 11, (OK)
[     6.169] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[     6.169] drmOpenDevice: node name is /dev/dri/card0
[     6.169] drmOpenDevice: open result is 11, (OK)
[     6.169] drmOpenByBusid: drmOpenMinor returns 11
[     6.169] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[     6.169] (II) [drm] nouveau interface version: 0.0.16
[     6.169] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[     6.169] (WW) Falling back to old probe method for vesa
[     6.169] (WW) Falling back to old probe method for fbdev
[     6.169] (II) Loading sub module "fbdevhw"
[     6.169] (II) LoadModule: "fbdevhw"
[     6.170] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[     6.170] (II) Module fbdevhw: vendor="X.Org Foundation"
[     6.170] 	compiled for 1.10.4, module version = 0.0.2
[     6.170] 	ABI class: X.Org Video Driver, version 10.0
[     6.170] (II) Loading sub module "dri"
[     6.170] (II) LoadModule: "dri"
[     6.170] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[     6.170] (II) Module dri: vendor="X.Org Foundation"
[     6.170] 	compiled for 1.10.4, module version = 1.0.0
[     6.170] 	ABI class: X.Org Server Extension, version 5.0
[     6.170] (II) NOUVEAU(0): Loaded DRI module
[     6.170] drmOpenDevice: node name is /dev/dri/card0
[     6.170] drmOpenDevice: open result is 12, (OK)
[     6.170] drmOpenDevice: node name is /dev/dri/card0
[     6.171] drmOpenDevice: open result is 12, (OK)
[     6.171] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[     6.171] drmOpenDevice: node name is /dev/dri/card0
[     6.171] drmOpenDevice: open result is 12, (OK)
[     6.171] drmOpenByBusid: drmOpenMinor returns 12
[     6.171] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[     6.171] (II) [drm] DRM interface version 1.4
[     6.171] (II) [drm] DRM open master succeeded.
[     6.171] (--) NOUVEAU(0): Chipset: "NVIDIA NVa8"
[     6.171] (II) NOUVEAU(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[     6.171] (==) NOUVEAU(0): Depth 24, (--) framebuffer bpp 32
[     6.171] (==) NOUVEAU(0): RGB weight 888
[     6.171] (==) NOUVEAU(0): Default visual is TrueColor
[     6.171] (==) NOUVEAU(0): Using HW cursor
[     6.171] (==) NOUVEAU(0): GLX sync to VBlank disabled.
[     6.171] (==) NOUVEAU(0): Page flipping enabled
[     6.189] (II) NOUVEAU(0): Output eDP-1 has no monitor section
[     6.286] (II) NOUVEAU(0): Output VGA-1 has no monitor section
[     6.476] (II) NOUVEAU(0): Output DP-1 has no monitor section
[     6.668] (II) NOUVEAU(0): Output DP-2 has no monitor section
[     6.686] (II) NOUVEAU(0): EDID for output eDP-1
[     6.686] (II) NOUVEAU(0): Manufacturer: LGD  Model: 0  Serial#: 0
[     6.686] (II) NOUVEAU(0): Year: 2009  Week: 0
[     6.686] (II) NOUVEAU(0): EDID Version: 1.4
[     6.686] (II) NOUVEAU(0): Digital Display Input
[     6.686] (II) NOUVEAU(0): 6 bits per channel
[     6.686] (II) NOUVEAU(0): Digital interface is DisplayPort
[     6.686] (II) NOUVEAU(0): Max Image Size [cm]: horiz.: 34  vert.: 19
[     6.686] (II) NOUVEAU(0): Gamma: 2.20
[     6.686] (II) NOUVEAU(0): No DPMS capabilities specified
[     6.686] (II) NOUVEAU(0): Supported color encodings: RGB 4:4:4 
[     6.686] (II) NOUVEAU(0): First detailed timing is preferred mode
[     6.686] (II) NOUVEAU(0): Preferred mode is native pixel format and refresh rate
[     6.686] (II) NOUVEAU(0): redX: 0.617 redY: 0.349   greenX: 0.313 greenY: 0.595
[     6.686] (II) NOUVEAU(0): blueX: 0.151 blueY: 0.056   whiteX: 0.313 whiteY: 0.329
[     6.686] (II) NOUVEAU(0): Manufacturer's mask: 0
[     6.686] (II) NOUVEAU(0): Supported detailed timing:
[     6.686] (II) NOUVEAU(0): clock: 137.7 MHz   Image Size:  344 x 194 mm
[     6.686] (II) NOUVEAU(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2066 h_border: 0
[     6.686] (II) NOUVEAU(0): v_active: 1080  v_sync: 1083  v_sync_end 1088 v_blanking: 1111 v_border: 0
[     6.686] (II) NOUVEAU(0): Supported detailed timing:
[     6.686] (II) NOUVEAU(0): clock: 92.5 MHz   Image Size:  344 x 194 mm
[     6.686] (II) NOUVEAU(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
[     6.686] (II) NOUVEAU(0): v_active: 1080  v_sync: 1083  v_sync_end 1088 v_blanking: 1111 v_border: 0
[     6.686] (II) NOUVEAU(0):  DH091&#65533;156WF1
[     6.686] (II) NOUVEAU(0): Unknown vendor-specific block 0
[     6.686] (II) NOUVEAU(0): EDID (in hex):
[     6.686] (II) NOUVEAU(0): 	00ffffffffffff0030e4000000000000
[     6.686] (II) NOUVEAU(0): 	00130104952213780215d59e59509826
[     6.686] (II) NOUVEAU(0): 	0e505400000001010101010101010101
[     6.686] (II) NOUVEAU(0): 	010101010101ca35809270381f403020
[     6.686] (II) NOUVEAU(0): 	350058c210000018222480a070381f40
[     6.686] (II) NOUVEAU(0): 	3020350058c210000018000000fe0044
[     6.686] (II) NOUVEAU(0): 	48303931803135365746310a00000000
[     6.686] (II) NOUVEAU(0): 	000041311e0000000009010a202000d6
[     6.686] (II) NOUVEAU(0): EDID vendor "LGD", prod id 0
[     6.686] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[     6.686] (II) NOUVEAU(0): Modeline "1920x1080"x0.0  137.70  1920 1968 2000 2066  1080 1083 1088 1111 -hsync -vsync (66.7 kHz)
[     6.686] (II) NOUVEAU(0): Modeline "1920x1080"x0.0   92.50  1920 1968 2000 2080  1080 1083 1088 1111 -hsync -vsync (44.5 kHz)
[     6.686] (II) NOUVEAU(0): Printing probed modes for output eDP-1
[     6.686] (II) NOUVEAU(0): Modeline "1920x1080"x60.0  137.70  1920 1968 2000 2066  1080 1083 1088 1111 -hsync -vsync (66.7 kHz)
[     6.686] (II) NOUVEAU(0): Modeline "1920x1080"x60.0  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync (67.2 kHz)
[     6.686] (II) NOUVEAU(0): Modeline "1920x1080"x40.0   92.50  1920 1968 2000 2080  1080 1083 1088 1111 -hsync -vsync (44.5 kHz)
[     6.686] (II) NOUVEAU(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[     6.686] (II) NOUVEAU(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
[     6.686] (II) NOUVEAU(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
[     6.686] (II) NOUVEAU(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
[     6.686] (II) NOUVEAU(0): Modeline "1152x864"x60.0   81.75  1152 1216 1336 1520  864 867 871 897 -hsync +vsync (53.8 kHz)
[     6.686] (II) NOUVEAU(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
[     6.686] (II) NOUVEAU(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
[     6.783] (II) NOUVEAU(0): EDID for output VGA-1
[     6.976] (II) NOUVEAU(0): EDID for output DP-1
[     7.168] (II) NOUVEAU(0): EDID for output DP-2
[     7.168] (II) NOUVEAU(0): Output eDP-1 connected
[     7.168] (II) NOUVEAU(0): Output VGA-1 disconnected
[     7.168] (II) NOUVEAU(0): Output DP-1 disconnected
[     7.168] (II) NOUVEAU(0): Output DP-2 disconnected
[     7.168] (II) NOUVEAU(0): Using exact sizes for initial modes
[     7.168] (II) NOUVEAU(0): Output eDP-1 using initial mode 1920x1080
[     7.168] (II) NOUVEAU(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[     7.168] (--) NOUVEAU(0): Virtual size is 1920x1080 (pitch 0)
[     7.168] (**) NOUVEAU(0):  Driver mode "1920x1080": 137.7 MHz (scaled from 0.0 MHz), 66.7 kHz, 60.0 Hz
[     7.168] (II) NOUVEAU(0): Modeline "1920x1080"x60.0  137.70  1920 1968 2000 2066  1080 1083 1088 1111 -hsync -vsync (66.7 kHz)
[     7.168] (**) NOUVEAU(0):  Driver mode "1920x1080": 173.0 MHz (scaled from 0.0 MHz), 67.2 kHz, 60.0 Hz
[     7.168] (II) NOUVEAU(0): Modeline "1920x1080"x60.0  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync (67.2 kHz)
[     7.168] (**) NOUVEAU(0):  Driver mode "1920x1080": 92.5 MHz (scaled from 0.0 MHz), 44.5 kHz, 40.0 Hz
[     7.168] (II) NOUVEAU(0): Modeline "1920x1080"x40.0   92.50  1920 1968 2000 2080  1080 1083 1088 1111 -hsync -vsync (44.5 kHz)
[     7.168] (**) NOUVEAU(0):  Driver mode "1680x1050": 146.2 MHz (scaled from 0.0 MHz), 65.3 kHz, 60.0 Hz
[     7.168] (II) NOUVEAU(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[     7.168] (**) NOUVEAU(0):  Driver mode "1400x1050": 121.8 MHz (scaled from 0.0 MHz), 65.3 kHz, 60.0 Hz
[     7.168] (II) NOUVEAU(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
[     7.168] (**) NOUVEAU(0):  Driver mode "1280x1024": 109.0 MHz (scaled from 0.0 MHz), 63.7 kHz, 59.9 Hz
[     7.168] (II) NOUVEAU(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
[     7.168] (**) NOUVEAU(0):  Driver mode "1280x960": 101.2 MHz (scaled from 0.0 MHz), 59.7 kHz, 59.9 Hz
[     7.168] (II) NOUVEAU(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
[     7.168] (**) NOUVEAU(0):  Driver mode "1152x864": 81.8 MHz (scaled from 0.0 MHz), 53.8 kHz, 60.0 Hz
[     7.168] (II) NOUVEAU(0): Modeline "1152x864"x60.0   81.75  1152 1216 1336 1520  864 867 871 897 -hsync +vsync (53.8 kHz)
[     7.168] (**) NOUVEAU(0):  Driver mode "1024x768": 63.5 MHz (scaled from 0.0 MHz), 47.8 kHz, 59.9 Hz
[     7.168] (II) NOUVEAU(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
[     7.168] (**) NOUVEAU(0):  Driver mode "800x600": 38.2 MHz (scaled from 0.0 MHz), 37.4 kHz, 59.9 Hz
[     7.168] (II) NOUVEAU(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
[     7.168] (**) NOUVEAU(0): Display dimensions: (340, 190) mm
[     7.168] (**) NOUVEAU(0): DPI set to (143, 144)
[     7.168] (II) Loading sub module "fb"
[     7.168] (II) LoadModule: "fb"
[     7.168] (II) Loading /usr/lib/xorg/modules/libfb.so
[     7.168] (II) Module fb: vendor="X.Org Foundation"
[     7.168] 	compiled for 1.10.4, module version = 1.0.0
[     7.168] 	ABI class: X.Org ANSI C Emulation, version 0.4
[     7.169] (II) Loading sub module "exa"
[     7.169] (II) LoadModule: "exa"
[     7.169] (II) Loading /usr/lib/xorg/modules/libexa.so
[     7.169] (II) Module exa: vendor="X.Org Foundation"
[     7.169] 	compiled for 1.10.4, module version = 2.5.0
[     7.169] 	ABI class: X.Org Video Driver, version 10.0
[     7.169] (II) Loading sub module "shadowfb"
[     7.169] (II) LoadModule: "shadowfb"
[     7.169] (II) Loading /usr/lib/xorg/modules/libshadowfb.so
[     7.169] (II) Module shadowfb: vendor="X.Org Foundation"
[     7.169] 	compiled for 1.10.4, module version = 1.0.0
[     7.169] 	ABI class: X.Org ANSI C Emulation, version 0.4
[     7.169] (II) UnloadModule: "vesa"
[     7.169] (II) Unloading vesa
[     7.169] (II) UnloadModule: "fbdev"
[     7.169] (II) Unloading fbdev
[     7.169] (II) UnloadModule: "fbdevhw"
[     7.169] (II) Unloading fbdevhw
[     7.169] (--) Depth 24 pixmap format is 32 bpp
[     7.171] (II) NOUVEAU(0): Opened GPU channel 2
[     7.172] (II) NOUVEAU(0): [DRI2] Setup complete
[     7.172] (II) NOUVEAU(0): [DRI2]   DRI driver: nouveau
[     7.172] (II) NOUVEAU(0): GART: 512MiB available
[     7.174] (II) NOUVEAU(0): GART: Allocated 16MiB as a scratch buffer
[     7.174] (II) EXA(0): Driver allocated offscreen pixmaps
[     7.174] (II) EXA(0): Driver registered support for the following operations:
[     7.174] (II)         Solid
[     7.174] (II)         Copy
[     7.174] (II)         Composite (RENDER acceleration)
[     7.174] (II)         UploadToScreen
[     7.174] (II)         DownloadFromScreen
[     7.174] (==) NOUVEAU(0): Backing store disabled
[     7.174] (==) NOUVEAU(0): Silken mouse enabled
[     7.174] (II) NOUVEAU(0): [XvMC] Associated with Nouveau GeForce 8/9 Textured Video.
[     7.174] (II) NOUVEAU(0): [XvMC] Extension initialized.
[     7.174] (==) NOUVEAU(0): DPMS enabled
[     7.174] (II) NOUVEAU(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[     7.174] (WW) NOUVEAU(0): Option "NoLogo" is not used
[     7.174] (--) RandR disabled
[     7.174] (II) Initializing built-in extension Generic Event Extension
[     7.174] (II) Initializing built-in extension SHAPE
[     7.174] (II) Initializing built-in extension MIT-SHM
[     7.174] (II) Initializing built-in extension XInputExtension
[     7.174] (II) Initializing built-in extension XTEST
[     7.174] (II) Initializing built-in extension BIG-REQUESTS
[     7.174] (II) Initializing built-in extension SYNC
[     7.174] (II) Initializing built-in extension XKEYBOARD
[     7.174] (II) Initializing built-in extension XC-MISC
[     7.174] (II) Initializing built-in extension SECURITY
[     7.174] (II) Initializing built-in extension XINERAMA
[     7.174] (II) Initializing built-in extension XFIXES
[     7.174] (II) Initializing built-in extension RENDER
[     7.174] (II) Initializing built-in extension RANDR
[     7.174] (II) Initializing built-in extension COMPOSITE
[     7.174] (II) Initializing built-in extension DAMAGE
[     7.174] (II) Initializing built-in extension GESTURE
[     7.182] (II) AIGLX: Trying DRI driver /usr/lib/x86_64-linux-gnu/dri/nouveau_dri.so
[     7.195] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[     7.195] (II) AIGLX: enabled GLX_INTEL_swap_event
[     7.195] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[     7.195] (II) AIGLX: enabled GLX_SGI_make_current_read
[     7.195] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[     7.195] (II) AIGLX: Loaded and initialized nouveau
[     7.196] (II) GLX: Initialized DRI2 GL provider for screen 0
[     7.200] (II) NOUVEAU(0): NVEnterVT is called.
[     7.506] (II) NOUVEAU(0): Setting screen physical size to 508 x 285
[     7.506] resize called 1920 1080
[     7.516] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[     7.528] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[     7.528] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     7.528] (II) LoadModule: "evdev"
[     7.529] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     7.529] (II) Module evdev: vendor="X.Org Foundation"
[     7.529] 	compiled for 1.10.2, module version = 2.6.0
[     7.529] 	Module class: X.Org XInput Driver
[     7.529] 	ABI class: X.Org XInput driver, version 12.3
[     7.530] (II) Using input driver 'evdev' for 'Power Button'
[     7.530] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     7.530] (**) Power Button: always reports core events
[     7.530] (**) Power Button: Device: "/dev/input/event3"
[     7.530] (--) Power Button: Found keys
[     7.530] (II) Power Button: Configuring as keyboard
[     7.530] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[     7.530] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[     7.530] (**) Option "xkb_rules" "evdev"
[     7.530] (**) Option "xkb_model" "pc105"
[     7.530] (**) Option "xkb_layout" "de"
[     7.530] (**) Option "xkb_variant" "nodeadkeys"
[     7.532] (II) XKB: reuse xkmfile /var/lib/xkb/server-76D2B5A359D34EEB9BFAEB1701EF70014DF39715.xkm
[     7.534] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[     7.534] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[     7.534] (II) Using input driver 'evdev' for 'Video Bus'
[     7.534] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     7.534] (**) Video Bus: always reports core events
[     7.534] (**) Video Bus: Device: "/dev/input/event5"
[     7.534] (--) Video Bus: Found keys
[     7.534] (II) Video Bus: Configuring as keyboard
[     7.534] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input5/event5"
[     7.534] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[     7.534] (**) Option "xkb_rules" "evdev"
[     7.534] (**) Option "xkb_model" "pc105"
[     7.534] (**) Option "xkb_layout" "de"
[     7.534] (**) Option "xkb_variant" "nodeadkeys"
[     7.541] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[     7.541] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     7.541] (II) Using input driver 'evdev' for 'Power Button'
[     7.541] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     7.541] (**) Power Button: always reports core events
[     7.541] (**) Power Button: Device: "/dev/input/event1"
[     7.541] (--) Power Button: Found keys
[     7.541] (II) Power Button: Configuring as keyboard
[     7.541] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[     7.541] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[     7.541] (**) Option "xkb_rules" "evdev"
[     7.541] (**) Option "xkb_model" "pc105"
[     7.541] (**) Option "xkb_layout" "de"
[     7.541] (**) Option "xkb_variant" "nodeadkeys"
[     7.542] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[     7.542] (II) No input driver/identifier specified (ignoring)
[     7.542] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[     7.542] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[     7.542] (II) Using input driver 'evdev' for 'Sleep Button'
[     7.542] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     7.542] (**) Sleep Button: always reports core events
[     7.542] (**) Sleep Button: Device: "/dev/input/event2"
[     7.542] (--) Sleep Button: Found keys
[     7.542] (II) Sleep Button: Configuring as keyboard
[     7.542] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2/event2"
[     7.542] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[     7.542] (**) Option "xkb_rules" "evdev"
[     7.542] (**) Option "xkb_model" "pc105"
[     7.542] (**) Option "xkb_layout" "de"
[     7.542] (**) Option "xkb_variant" "nodeadkeys"
[     7.544] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=9 (/dev/input/event13)
[     7.544] (II) No input driver/identifier specified (ignoring)
[     7.545] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event14)
[     7.545] (II) No input driver/identifier specified (ignoring)
[     7.545] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event15)
[     7.545] (II) No input driver/identifier specified (ignoring)
[     7.546] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event16)
[     7.546] (II) No input driver/identifier specified (ignoring)
[     7.547] (II) config/udev: Adding input device Laptop_Integrated_Webcam_3M (/dev/input/event6)
[     7.547] (**) Laptop_Integrated_Webcam_3M: Applying InputClass "evdev keyboard catchall"
[     7.547] (II) Using input driver 'evdev' for 'Laptop_Integrated_Webcam_3M'
[     7.547] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     7.547] (**) Laptop_Integrated_Webcam_3M: always reports core events
[     7.547] (**) Laptop_Integrated_Webcam_3M: Device: "/dev/input/event6"
[     7.547] (--) Laptop_Integrated_Webcam_3M: Found keys
[     7.547] (II) Laptop_Integrated_Webcam_3M: Configuring as keyboard
[     7.547] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input6/event6"
[     7.547] (II) XINPUT: Adding extended input device "Laptop_Integrated_Webcam_3M" (type: KEYBOARD)
[     7.547] (**) Option "xkb_rules" "evdev"
[     7.547] (**) Option "xkb_model" "pc105"
[     7.547] (**) Option "xkb_layout" "de"
[     7.547] (**) Option "xkb_variant" "nodeadkeys"
[     7.548] (II) config/udev: Adding input device HDA Intel HP Out at Ext Right Jack (/dev/input/event10)
[     7.548] (II) No input driver/identifier specified (ignoring)
[     7.549] (II) config/udev: Adding input device HDA Intel Mic at Sep Left Jack (/dev/input/event7)
[     7.549] (II) No input driver/identifier specified (ignoring)
[     7.549] (II) config/udev: Adding input device HDA Intel Mic at Ext Right Jack (/dev/input/event8)
[     7.549] (II) No input driver/identifier specified (ignoring)
[     7.549] (II) config/udev: Adding input device HDA Intel Line Out at Sep Left Jack (/dev/input/event9)
[     7.549] (II) No input driver/identifier specified (ignoring)
[     7.555] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[     7.555] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[     7.555] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[     7.555] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     7.555] (**) AT Translated Set 2 keyboard: always reports core events
[     7.555] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[     7.555] (--) AT Translated Set 2 keyboard: Found keys
[     7.555] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[     7.555] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[     7.555] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[     7.555] (**) Option "xkb_rules" "evdev"
[     7.555] (**) Option "xkb_model" "pc105"
[     7.555] (**) Option "xkb_layout" "de"
[     7.555] (**) Option "xkb_variant" "nodeadkeys"
[     7.556] (II) config/udev: Adding input device ImPS/2 ALPS GlidePoint (/dev/input/event12)
[     7.556] (**) ImPS/2 ALPS GlidePoint: Applying InputClass "evdev pointer catchall"
[     7.556] (II) Using input driver 'evdev' for 'ImPS/2 ALPS GlidePoint'
[     7.556] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     7.556] (**) ImPS/2 ALPS GlidePoint: always reports core events
[     7.556] (**) ImPS/2 ALPS GlidePoint: Device: "/dev/input/event12"
[     7.556] (--) ImPS/2 ALPS GlidePoint: Found 3 mouse buttons
[     7.556] (--) ImPS/2 ALPS GlidePoint: Found scroll wheel(s)
[     7.556] (--) ImPS/2 ALPS GlidePoint: Found relative axes
[     7.556] (--) ImPS/2 ALPS GlidePoint: Found x and y relative axes
[     7.556] (II) ImPS/2 ALPS GlidePoint: Configuring as mouse
[     7.556] (II) ImPS/2 ALPS GlidePoint: Adding scrollwheel support
[     7.556] (**) ImPS/2 ALPS GlidePoint: YAxisMapping: buttons 4 and 5
[     7.556] (**) ImPS/2 ALPS GlidePoint: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     7.556] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input12/event12"
[     7.556] (II) XINPUT: Adding extended input device "ImPS/2 ALPS GlidePoint" (type: MOUSE)
[     7.556] (II) ImPS/2 ALPS GlidePoint: initialized for relative axes.
[     7.556] (**) ImPS/2 ALPS GlidePoint: (accel) keeping acceleration scheme 1
[     7.556] (**) ImPS/2 ALPS GlidePoint: (accel) acceleration profile 0
[     7.556] (**) ImPS/2 ALPS GlidePoint: (accel) acceleration factor: 2.000
[     7.556] (**) ImPS/2 ALPS GlidePoint: (accel) acceleration threshold: 4
[     7.557] (II) config/udev: Adding input device ImPS/2 ALPS GlidePoint (/dev/input/mouse0)
[     7.557] (II) No input driver/identifier specified (ignoring)
[     7.561] (II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event11)
[     7.561] (**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[     7.562] (II) Using input driver 'evdev' for 'Dell WMI hotkeys'
[     7.562] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     7.562] (**) Dell WMI hotkeys: always reports core events
[     7.562] (**) Dell WMI hotkeys: Device: "/dev/input/event11"
[     7.562] (--) Dell WMI hotkeys: Found keys
[     7.562] (II) Dell WMI hotkeys: Configuring as keyboard
[     7.562] (**) Option "config_info" "udev:/sys/devices/virtual/input/input11/event11"
[     7.562] (II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD)
[     7.562] (**) Option "xkb_rules" "evdev"
[     7.562] (**) Option "xkb_model" "pc105"
[     7.562] (**) Option "xkb_layout" "de"
[     7.562] (**) Option "xkb_variant" "nodeadkeys"
[     8.240] (II) NOUVEAU(0): EDID vendor "LGD", prod id 0
[     8.240] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[     8.240] (II) NOUVEAU(0): Modeline "1920x1080"x0.0  137.70  1920 1968 2000 2066  1080 1083 1088 1111 -hsync -vsync (66.7 kHz)
[     8.240] (II) NOUVEAU(0): Modeline "1920x1080"x0.0   92.50  1920 1968 2000 2080  1080 1083 1088 1111 -hsync -vsync (44.5 kHz)
[    10.960] (II) NOUVEAU(0): EDID vendor "LGD", prod id 0
[    10.960] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    10.960] (II) NOUVEAU(0): Modeline "1920x1080"x0.0  137.70  1920 1968 2000 2066  1080 1083 1088 1111 -hsync -vsync (66.7 kHz)
[    10.960] (II) NOUVEAU(0): Modeline "1920x1080"x0.0   92.50  1920 1968 2000 2080  1080 1083 1088 1111 -hsync -vsync (44.5 kHz)
[    13.895] (II) NOUVEAU(0): EDID vendor "LGD", prod id 0
[    13.895] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    13.895] (II) NOUVEAU(0): Modeline "1920x1080"x0.0  137.70  1920 1968 2000 2066  1080 1083 1088 1111 -hsync -vsync (66.7 kHz)
[    13.895] (II) NOUVEAU(0): Modeline "1920x1080"x0.0   92.50  1920 1968 2000 2080  1080 1083 1088 1111 -hsync -vsync (44.5 kHz)
[    14.413] resize called 1920 1080
[    14.580] (II) NOUVEAU(0): EDID vendor "LGD", prod id 0
[    14.580] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    14.580] (II) NOUVEAU(0): Modeline "1920x1080"x0.0  137.70  1920 1968 2000 2066  1080 1083 1088 1111 -hsync -vsync (66.7 kHz)
[    14.580] (II) NOUVEAU(0): Modeline "1920x1080"x0.0   92.50  1920 1968 2000 2080  1080 1083 1088 1111 -hsync -vsync (44.5 kHz)
[    15.118] (II) NOUVEAU(0): EDID vendor "LGD", prod id 0
[    15.118] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    15.118] (II) NOUVEAU(0): Modeline "1920x1080"x0.0  137.70  1920 1968 2000 2066  1080 1083 1088 1111 -hsync -vsync (66.7 kHz)
[    15.118] (II) NOUVEAU(0): Modeline "1920x1080"x0.0   92.50  1920 1968 2000 2080  1080 1083 1088 1111 -hsync -vsync (44.5 kHz)
[    17.572] (II) XKB: reuse xkmfile /var/lib/xkb/server-387F861772390103F1E59E3ABD6928760B83259C.xkm
[    22.768] (II) NOUVEAU(0): EDID vendor "LGD", prod id 0
[    22.768] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    22.768] (II) NOUVEAU(0): Modeline "1920x1080"x0.0  137.70  1920 1968 2000 2066  1080 1083 1088 1111 -hsync -vsync (66.7 kHz)
[    22.768] (II) NOUVEAU(0): Modeline "1920x1080"x0.0   92.50  1920 1968 2000 2080  1080 1083 1088 1111 -hsync -vsync (44.5 kHz)
[    46.456] (II) NOUVEAU(0): EDID vendor "LGD", prod id 0
[    46.456] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    46.456] (II) NOUVEAU(0): Modeline "1920x1080"x0.0  137.70  1920 1968 2000 2066  1080 1083 1088 1111 -hsync -vsync (66.7 kHz)
[    46.456] (II) NOUVEAU(0): Modeline "1920x1080"x0.0   92.50  1920 1968 2000 2080  1080 1083 1088 1111 -hsync -vsync (44.5 kHz)
[    46.839] (II) config/udev: Adding input device B16_b_02 USB-PS/2 Optical Mouse (/dev/input/event18)
[    46.839] (**) B16_b_02 USB-PS/2 Optical Mouse: Applying InputClass "evdev pointer catchall"
[    46.839] (II) Using input driver 'evdev' for 'B16_b_02 USB-PS/2 Optical Mouse'
[    46.839] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    46.839] (**) B16_b_02 USB-PS/2 Optical Mouse: always reports core events
[    46.839] (**) B16_b_02 USB-PS/2 Optical Mouse: Device: "/dev/input/event18"
[    46.839] (--) B16_b_02 USB-PS/2 Optical Mouse: Found 12 mouse buttons
[    46.839] (--) B16_b_02 USB-PS/2 Optical Mouse: Found scroll wheel(s)
[    46.840] (--) B16_b_02 USB-PS/2 Optical Mouse: Found relative axes
[    46.840] (--) B16_b_02 USB-PS/2 Optical Mouse: Found x and y relative axes
[    46.840] (II) B16_b_02 USB-PS/2 Optical Mouse: Configuring as mouse
[    46.840] (II) B16_b_02 USB-PS/2 Optical Mouse: Adding scrollwheel support
[    46.840] (**) B16_b_02 USB-PS/2 Optical Mouse: YAxisMapping: buttons 4 and 5
[    46.840] (**) B16_b_02 USB-PS/2 Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    46.840] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0/input/input18/event18"
[    46.840] (II) XINPUT: Adding extended input device "B16_b_02 USB-PS/2 Optical Mouse" (type: MOUSE)
[    46.840] (II) B16_b_02 USB-PS/2 Optical Mouse: initialized for relative axes.
[    46.840] (**) B16_b_02 USB-PS/2 Optical Mouse: (accel) keeping acceleration scheme 1
[    46.840] (**) B16_b_02 USB-PS/2 Optical Mouse: (accel) acceleration profile 0
[    46.840] (**) B16_b_02 USB-PS/2 Optical Mouse: (accel) acceleration factor: 2.000
[    46.840] (**) B16_b_02 USB-PS/2 Optical Mouse: (accel) acceleration threshold: 4
[    46.840] (II) config/udev: Adding input device B16_b_02 USB-PS/2 Optical Mouse (/dev/input/mouse1)
[    46.840] (II) No input driver/identifier specified (ignoring)
[    46.841] (II) config/udev: Adding input device Microsoft Wired Keyboard 400 (/dev/input/event17)
[    46.841] (**) Microsoft Wired Keyboard 400: Applying InputClass "evdev keyboard catchall"
[    46.841] (II) Using input driver 'evdev' for 'Microsoft Wired Keyboard 400'
[    46.841] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    46.841] (**) Microsoft Wired Keyboard 400: always reports core events
[    46.841] (**) Microsoft Wired Keyboard 400: Device: "/dev/input/event17"
[    46.841] (--) Microsoft Wired Keyboard 400: Found keys
[    46.841] (II) Microsoft Wired Keyboard 400: Configuring as keyboard
[    46.841] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2.1/1-1.2.1:1.0/input/input17/event17"
[    46.841] (II) XINPUT: Adding extended input device "Microsoft Wired Keyboard 400" (type: KEYBOARD)
[    46.841] (**) Option "xkb_rules" "evdev"
[    46.841] (**) Option "xkb_model" "pc105"
[    46.841] (**) Option "xkb_layout" "de"
[    46.841] (**) Option "xkb_variant" "nodeadkeys"
[    47.459] (II) XKB: reuse xkmfile /var/lib/xkb/server-387F861772390103F1E59E3ABD6928760B83259C.xkm
[    52.632] (II) XKB: reuse xkmfile /var/lib/xkb/server-387F861772390103F1E59E3ABD6928760B83259C.xkm

```

I hope somebody solved this already :(

---

### Post by kodiakz on 2011-10-24
Here is some kernel related stuff:

```

Oct 24 14:18:34 WNT071 kernel: [    5.862604] HDMI status: Pin=5 Presence_Detect=0 ELD_Valid=0
Oct 24 14:18:35 WNT071 kernel: [    5.894548] HDMI status: Pin=5 Presence_Detect=0 ELD_Valid=0
Oct 24 14:18:35 WNT071 kernel: [    5.926489] HDMI status: Pin=5 Presence_Detect=0 ELD_Valid=0
Oct 24 14:18:35 WNT071 kernel: [    5.958440] HDMI status: Pin=5 Presence_Detect=0 ELD_Valid=0
Oct 24 14:18:35 WNT071 kernel: [    5.974495] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input15
Oct 24 14:18:35 WNT071 kernel: [    5.974578] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input16
Oct 24 14:18:35 WNT071 kernel: [    5.974718] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input17
Oct 24 14:18:35 WNT071 kernel: [    5.974824] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input18
Oct 24 14:18:35 WNT071 kernel: [    6.134795] scsi 6:0:0:0: Direct-Access     Generic  Flash HS-CF      5.39 PQ: 0 ANSI: 0
Oct 24 14:18:35 WNT071 kernel: [    6.138662] scsi 6:0:0:1: Direct-Access     Generic  Flash HS-COMBO   5.39 PQ: 0 ANSI: 0
Oct 24 14:18:35 WNT071 kernel: [    6.253773] [drm] nouveau 0000:01:00.0: unplugged DP-2
Oct 24 14:18:35 WNT071 kernel: [    6.461749] sd 6:0:0:0: Attached scsi generic sg2 type 0
Oct 24 14:18:35 WNT071 kernel: [    6.461851] sd 6:0:0:1: Attached scsi generic sg3 type 0
Oct 24 14:18:35 WNT071 kernel: [    6.500778] [drm] nouveau 0000:01:00.0: plugged DP-2
Oct 24 14:18:35 WNT071 kernel: [    6.511252] [drm] nouveau 0000:01:00.0: unplugged DP-2
Oct 24 14:18:35 WNT071 kernel: [    6.515044] sd 6:0:0:0: [sdb] Attached SCSI removable disk
Oct 24 14:18:35 WNT071 kernel: [    6.519287] sd 6:0:0:1: [sdc] Attached SCSI removable disk
Oct 24 14:18:35 WNT071 kernel: [    6.760427] [drm] nouveau 0000:01:00.0: plugged DP-2
Oct 24 14:18:35 WNT071 kernel: [    6.777426] [drm] nouveau 0000:01:00.0: unplugged DP-2
Oct 24 14:18:36 WNT071 kernel: [    7.003233] Adding 5858300k swap on /dev/mapper/cryptswap1.  Priority:-1 extents:1 across:5858300k 
Oct 24 14:18:36 WNT071 kernel: [    7.025887] [drm] nouveau 0000:01:00.0: plugged DP-2
Oct 24 14:18:36 WNT071 kernel: [    7.708027] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
Oct 24 14:18:36 WNT071 kernel: [    7.710258] EXT4-fs (sda7): re-mounted. Opts: commit=0
Oct 24 14:18:37 WNT071 kernel: [    8.707706] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: None
Oct 24 14:18:37 WNT071 kernel: [    8.708084] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Oct 24 14:18:48 WNT071 kernel: [   19.442944] eth0: no IPv6 routers present
Oct 24 14:20:14 WNT071 kernel: [  105.525599] nvidia: module license 'NVIDIA' taints kernel.
Oct 24 14:20:14 WNT071 kernel: [  105.525604] Disabling lock debugging due to kernel taint
Oct 24 14:20:15 WNT071 kernel: [  105.844466] NVRM: The NVIDIA probe routine was not called for 1 device(s).
Oct 24 14:20:15 WNT071 kernel: [  105.844473] NVRM: This can occur when a driver such as nouveau, rivafb,
Oct 24 14:20:15 WNT071 kernel: [  105.844475] NVRM: nvidiafb, or rivatv was loaded and obtained ownership of
Oct 24 14:20:15 WNT071 kernel: [  105.844478] NVRM: the NVIDIA device(s).
Oct 24 14:20:15 WNT071 kernel: [  105.844483] NVRM: Try unloading the conflicting kernel module (and/or
Oct 24 14:20:15 WNT071 kernel: [  105.844485] NVRM: reconfigure your kernel without the conflicting
Oct 24 14:20:15 WNT071 kernel: [  105.844486] NVRM: driver(s)), then try loading the NVIDIA kernel module
Oct 24 14:20:15 WNT071 kernel: [  105.844489] NVRM: again.
Oct 24 14:20:15 WNT071 kernel: [  105.844492] NVRM: No NVIDIA graphics adapter probed!
Oct 24 14:20:48 WNT071 kernel: Kernel logging (proc) stopped.

```

---

### Post by kodiakz on 2011-10-25
The same problem was posted on aksubuntu [http://askubuntu.com/questions/68220/ubuntu-11-10-wont-boot-with-nvidia-driver-enabled]("http://askubuntu.com/questions/68220/ubuntu-11-10-wont-boot-with-nvidia-driver-enabled")
Screen looks exactly as mine!

---

### Post by kodiakz on 2011-11-02
I tried it again today, hoped something has changed. No progress yet. I followed the advices from [http://askubuntu.com/questions/68220/ubuntu-11-10-wont-boot-with-nvidia-driver-enabled]("http://askubuntu.com/questions/68220/ubuntu-11-10-wont-boot-with-nvidia-driver-enabled") and reinstalled the drivers from ppa:ubuntu-x-swat/x-updates, but stick to the same problem.

jockey shows following:

```

jockey-text --list
kmod:nvidia_current - NVIDIA binary Xorg driver, kernel module and VDPAU library (Proprietary, Disabled, Not in use)
kmod:nvidia_current_updates - NVIDIA binary Xorg driver, kernel module and VDPAU library (Proprietary, Disabled, Not in use)

```

If nividia-current is installed it says enabled, but still not in use.

My graphic card is a NVS 3100M, which is definitely supported by this driver, it did work on 10.10.

Here is the output of my latest trial from  xorg log

```

[     5.411] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[     5.411] X Protocol Version 11, Revision 0
[     5.411] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[     5.411] Current Operating System: Linux WNT071 3.0.0-13-generic #21-Ubuntu SMP Mon Oct 17 20:18:51 UTC 2011 x86_64
[     5.411] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-13-generic root=UUID=ab481f03-379f-497e-b9e6-a1d303f5d667 ro quiet splash vmalloc=192MB vt.handoff=7
[     5.411] Build Date: 19 October 2011  05:21:26AM
[     5.411] xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see http://www.ubuntu.com/support) 
[     5.411] Current version of pixman: 0.22.2
[     5.411] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[     5.411] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     5.411] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Nov  2 17:41:30 2011
[     5.414] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     5.414] (==) No Layout section.  Using the first Screen section.
[     5.414] (==) No screen section available. Using defaults.
[     5.414] (**) |-->Screen "Default Screen Section" (0)
[     5.414] (**) |   |-->Monitor "<default monitor>"
[     5.414] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[     5.414] (==) Automatically adding devices
[     5.414] (==) Automatically enabling devices
[     5.414] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     5.414] 	Entry deleted from font path.
[     5.414] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     5.414] 	Entry deleted from font path.
[     5.414] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     5.414] 	Entry deleted from font path.
[     5.414] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     5.414] 	Entry deleted from font path.
[     5.414] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     5.414] 	Entry deleted from font path.
[     5.414] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[     5.414] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     5.414] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[     5.414] (II) Loader magic: 0x7e0220
[     5.414] (II) Module ABI versions:
[     5.414] 	X.Org ANSI C Emulation: 0.4
[     5.414] 	X.Org Video Driver: 10.0
[     5.414] 	X.Org XInput driver : 12.3
[     5.414] 	X.Org Server Extension : 5.0
[     5.416] (--) PCI:*(0:1:0:0) 10de:0a6c:1028:040b rev 162, Mem @ 0xe2000000/16777216, 0xd0000000/268435456, 0xe0000000/33554432, I/O @ 0x00007000/128, BIOS @ 0x????????/524288
[     5.416] (II) Open ACPI successful (/var/run/acpid.socket)
[     5.416] (II) LoadModule: "extmod"
[     5.429] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[     5.429] (II) Module extmod: vendor="X.Org Foundation"
[     5.429] 	compiled for 1.10.4, module version = 1.0.0
[     5.429] 	Module class: X.Org Server Extension
[     5.429] 	ABI class: X.Org Server Extension, version 5.0
[     5.429] (II) Loading extension MIT-SCREEN-SAVER
[     5.429] (II) Loading extension XFree86-VidModeExtension
[     5.429] (II) Loading extension XFree86-DGA
[     5.429] (II) Loading extension DPMS
[     5.429] (II) Loading extension XVideo
[     5.429] (II) Loading extension XVideo-MotionCompensation
[     5.429] (II) Loading extension X-Resource
[     5.429] (II) LoadModule: "dbe"
[     5.429] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[     5.429] (II) Module dbe: vendor="X.Org Foundation"
[     5.429] 	compiled for 1.10.4, module version = 1.0.0
[     5.429] 	Module class: X.Org Server Extension
[     5.429] 	ABI class: X.Org Server Extension, version 5.0
[     5.429] (II) Loading extension DOUBLE-BUFFER
[     5.429] (II) LoadModule: "glx"
[     5.429] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[     5.579] (II) Module glx: vendor="NVIDIA Corporation"
[     5.580] 	compiled for 4.0.2, module version = 1.0.0
[     5.580] 	Module class: X.Org Server Extension
[     5.580] (II) NVIDIA GLX Module  285.05.09  Fri Sep 23 17:51:24 PDT 2011
[     5.581] (II) Loading extension GLX
[     5.581] (II) LoadModule: "record"
[     5.581] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[     5.581] (II) Module record: vendor="X.Org Foundation"
[     5.581] 	compiled for 1.10.4, module version = 1.13.0
[     5.581] 	Module class: X.Org Server Extension
[     5.581] 	ABI class: X.Org Server Extension, version 5.0
[     5.581] (II) Loading extension RECORD
[     5.581] (II) LoadModule: "dri"
[     5.581] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[     5.582] (II) Module dri: vendor="X.Org Foundation"
[     5.582] 	compiled for 1.10.4, module version = 1.0.0
[     5.582] 	ABI class: X.Org Server Extension, version 5.0
[     5.582] (II) Loading extension XFree86-DRI
[     5.582] (II) LoadModule: "dri2"
[     5.582] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[     5.582] (II) Module dri2: vendor="X.Org Foundation"
[     5.582] 	compiled for 1.10.4, module version = 1.2.0
[     5.582] 	ABI class: X.Org Server Extension, version 5.0
[     5.582] (II) Loading extension DRI2
[     5.582] (==) Matched nvidia as autoconfigured driver 0
[     5.582] (==) Matched nouveau as autoconfigured driver 1
[     5.582] (==) Matched nv as autoconfigured driver 2
[     5.582] (==) Matched vesa as autoconfigured driver 3
[     5.582] (==) Matched fbdev as autoconfigured driver 4
[     5.582] (==) Assigned the driver to the xf86ConfigLayout
[     5.582] (II) LoadModule: "nvidia"
[     5.582] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[     5.592] (II) Module nvidia: vendor="NVIDIA Corporation"
[     5.619] 	compiled for 4.0.2, module version = 1.0.0
[     5.619] 	Module class: X.Org Video Driver
[     5.626] (II) LoadModule: "nouveau"
[     5.627] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[     5.627] (II) Module nouveau: vendor="X.Org Foundation"
[     5.627] 	compiled for 1.10.1, module version = 0.0.16
[     5.627] 	Module class: X.Org Video Driver
[     5.627] 	ABI class: X.Org Video Driver, version 10.0
[     5.627] (II) LoadModule: "nv"
[     5.638] (WW) Warning, couldn't open module nv
[     5.638] (II) UnloadModule: "nv"
[     5.638] (II) Unloading nv
[     5.638] (EE) Failed to load module "nv" (module does not exist, 0)
[     5.638] (II) LoadModule: "vesa"
[     5.639] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     5.639] (II) Module vesa: vendor="X.Org Foundation"
[     5.639] 	compiled for 1.10.2, module version = 2.3.0
[     5.639] 	Module class: X.Org Video Driver
[     5.639] 	ABI class: X.Org Video Driver, version 10.0
[     5.639] (II) LoadModule: "fbdev"
[     5.639] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     5.639] (II) Module fbdev: vendor="X.Org Foundation"
[     5.639] 	compiled for 1.10.0, module version = 0.4.2
[     5.639] 	ABI class: X.Org Video Driver, version 10.0
[     5.639] (II) NVIDIA dlloader X Driver  285.05.09  Fri Sep 23 17:33:35 PDT 2011
[     5.639] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[     5.643] (II) NOUVEAU driver Date:   Thu Mar 24 02:13:12 2011 +1000
[     5.643] (II) NOUVEAU driver for NVIDIA chipset families :
[     5.643] 	RIVA TNT        (NV04)
[     5.643] 	RIVA TNT2       (NV05)
[     5.643] 	GeForce 256     (NV10)
[     5.643] 	GeForce 2       (NV11, NV15)
[     5.646] 	GeForce 4MX     (NV17, NV18)
[     5.646] 	GeForce 3       (NV20)
[     5.646] 	GeForce 4Ti     (NV25, NV28)
[     5.646] 	GeForce FX      (NV3x)
[     5.646] 	GeForce 6       (NV4x)
[     5.646] 	GeForce 7       (G7x)
[     5.646] 	GeForce 8       (G8x)
[     5.646] 	GeForce GTX 200 (NVA0)
[     5.646] 	GeForce GTX 400 (NVC0)
[     5.646] (II) VESA: driver for VESA chipsets: vesa
[     5.646] (II) FBDEV: driver for framebuffer: fbdev
[     5.646] (++) using VT number 7

[     5.653] (II) Loading sub module "fb"
[     5.653] (II) LoadModule: "fb"
[     5.653] (II) Loading /usr/lib/xorg/modules/libfb.so
[     5.653] (II) Module fb: vendor="X.Org Foundation"
[     5.653] 	compiled for 1.10.4, module version = 1.0.0
[     5.653] 	ABI class: X.Org ANSI C Emulation, version 0.4
[     5.653] (II) Loading sub module "wfb"
[     5.653] (II) LoadModule: "wfb"
[     5.654] (II) Loading /usr/lib/xorg/modules/libwfb.so
[     5.663] (II) Module wfb: vendor="X.Org Foundation"
[     5.663] 	compiled for 1.10.4, module version = 1.0.0
[     5.663] 	ABI class: X.Org ANSI C Emulation, version 0.4
[     5.663] (II) Loading sub module "ramdac"
[     5.663] (II) LoadModule: "ramdac"
[     5.663] (II) Module "ramdac" already built-in
[     5.672] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[     5.673] (II) Loading /usr/lib/xorg/modules/libwfb.so
[     5.673] (II) Loading /usr/lib/xorg/modules/libfb.so
[     5.680] (WW) Falling back to old probe method for vesa
[     5.680] (WW) Falling back to old probe method for fbdev
[     5.680] (II) Loading sub module "fbdevhw"
[     5.680] (II) LoadModule: "fbdevhw"
[     5.680] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[     5.680] (II) Module fbdevhw: vendor="X.Org Foundation"
[     5.680] 	compiled for 1.10.4, module version = 0.0.2
[     5.680] 	ABI class: X.Org Video Driver, version 10.0
[     5.680] (II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[     5.680] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[     5.680] (==) NVIDIA(0): RGB weight 888
[     5.680] (==) NVIDIA(0): Default visual is TrueColor
[     5.680] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[     5.833] (EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the
[     5.833] (EE) NVIDIA(0):     system's kernel log for additional error messages and
[     5.833] (EE) NVIDIA(0):     consult the NVIDIA README for details.
[     5.833] (EE) NVIDIA(0):  *** Aborting ***
[     5.833] (II) UnloadModule: "nvidia"
[     5.833] (II) Unloading nvidia
[     5.833] (II) UnloadModule: "wfb"
[     5.833] (II) Unloading wfb
[     5.833] (II) UnloadModule: "fb"
[     5.833] (II) Unloading fb
[     5.833] (EE) Screen(s) found, but none have a usable configuration.
[     5.833] 
Fatal server error:
[     5.833] no screens found
[     5.833] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[     5.833] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[     5.833] 
[     5.834]  ddxSigGiveUp: Closing log

```

I also tried to install the driver from NVidia-ftp, which ends in a similar log-file. Why does it fail to load the f**king driver? Am I the only one having this problem? Please help!!

---

### Post by Alex1331 on 2011-11-12
I made a bug report on launchpad:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/888373](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/888373)

I had no problems with the nvidia drivers in 11.04.
My laptop uses a GeForce 8400M and works great with 11.10, but GeForce GTX 560Ti don't. :(

---

### Post by northd_tech on 2011-11-13
I'm not sure about 11.10, but I was having BUNCHES of trouble getting the 280 and newest? 285 NVIDIA drivers to activate under Lucid Lynx 10.04.3 LTS.  I kept getting some vague message from System > Administration > Hardware Drivers (or alternately **sudo jockey-gtk** under a terminal) about "This driver is activated but not in use" or else "A different version of this driver is in use."

After much consternation and blue-streaked condemnation, I eventually found this blacklist of the module "nvidia_current" in the file **/etc/modprobe.d/blacklist-local.conf**.  In fact, I think that was the only line in the file- no comments where it was generated, who/what generated it- nothing except "blacklist nvidia_current" and the  file was only 25 bytes long.  I added this bit to my ever-expanding collection of NVIDIA and other hardware Linux notes and gave that blacklist file the ol' **sudo rm** treatment.

I also blacklisted the "nvidia" module that I kept seeing under **lsmod | egrep 'nv|nou' **by using this command (to try and force loading of the "nvidia-current" 285.05.09 NVIDIA driver I had been trying to install):

```
gksu gedit /etc/modprobe.d/blacklist.conf
```Then I added these lines to the VERY END of my "blacklist.conf" file, and SAVED, and QUIT **gedit**:

> blacklist nouveau
blacklist lbm-nouveau
blacklist nvidia-173
blacklist nvidia-96
# trying to force loading of "nvidia-current".ko 285.05.09 module
# /lib/modules/2.6.32-35-generic/updates/dkms/nvidia-current.ko
# /var/lib/dkms/nvidia-current/285.05.09/2.6.32-35-generic/x86_64/module/nvidia-current.ko
blacklist nvidia
Strangely enough though, I kept getting an error message about a missing file/module when I tried to run this command to get more infomation about this "nvidia" module shown under **lsmod**:

```
modinfo nvidia
```I also added this to my **/etc/modules** file to force loading of the newer "nvidia-current" module using the command **gksu gedit /etc/modules**:

> # NVIDIA trying to get current build 285.05.09 for effects and acceleration "nvidia-current"
# vs. the nouveau, lbm-nouveau, nvidia-173, nvidia-96 modules
# /lib/modules/2.6.32-35-generic/updates/dkms/nvidia-current.ko
nvidia-current
After restarting both my 2.6.32-35-generic and 2.6.32-34-generic kernels with this new "blacklist nvidia" added and the "nvidia-current" forced under **/etc/modules**, I was finally able to open the "NVIDIA X Server Settings" from System > Administration > NVIDIA X Server Settings or System > Preferences > NVIDIA X Server Settings or else **nvidia-settings** from the terminal. This time, I'm seeing "NVIDIA Driver Verson: 285.05.09" under the "X Server Information" 'tab' at the very top of that window instead of that error message about the NVIDIA driver not being active.

You also might need to play around with some manual editing of the **/etc/X11/xorg.conf** file- I couldn't seem to get the generated file to survive a reboot for some reason when I was trying to use **jockey-gtk** to "Activate" my NVIDIA driver(s) (and that's the graphical program found under System > Administration > Hardware Drivers).

Now **modinfo nvidia** tells me this:

> filename:       /lib/modules/2.6.[COLOR=Black]32-21[/COLOR]-generic/kernel/drivers/video/[COLOR=Red]**nvidia.ko**[/COLOR]
alias:          char-major-195-*
supported:      external
license:        NVIDIA
alias:          pci:v000010DEd00000E00sv*sd*bc04sc80i00*
alias:          pci:v000010DEd00000AA3sv*sd*bc0Bsc40i00*
alias:          pci:v000010DEd*sv*sd*bc03sc02i00*
alias:          pci:v000010DEd*sv*sd*bc03sc00i00*
depends:        
vermagic:       2.6.32-21-generic SMP mod_unload modversions 
parm:           NVreg_EnableVia4x:int
parm:           NVreg_EnableALiAGP:int
parm:           NVreg_ReqAGPRate:int
parm:           NVreg_EnableAGPSBA:int
parm:           NVreg_EnableAGPFW:int
parm:           NVreg_Mobile:int
parm:           NVreg_ResmanDebugLevel:int
parm:           NVreg_RmLogonRC:int
parm:           NVreg_ModifyDeviceFiles:int
parm:           NVreg_DeviceFileUID:int
parm:           NVreg_DeviceFileGID:int
parm:           NVreg_DeviceFileMode:int
parm:           NVreg_RemapLimit:int
parm:           NVreg_UpdateMemoryTypes:int
parm:           NVreg_InitializeSystemMemoryAllocations:int
parm:           NVreg_UseVBios:int
parm:           NVreg_RMEdgeIntrCheck:int
parm:           NVreg_UsePageAttributeTable:int
parm:           NVreg_EnableMSI:int
parm:           NVreg_MapRegistersEarly:int
parm:           NVreg_RegisterForACPIEvents:int
parm:           NVreg_RegistryDwords:charp
parm:           NVreg_RmMsg:charp
parm:           NVreg_NvAGP:int
I'm currently running my "2.6.32-21-generic" kernel, but I believe that the "32-34-generic" and "32-35-generic" kernels were giving me the same behavio(u)r last night.

I seem to have all my Compiz effects, and the NVIDIA X Server Settings works, and most/all of the NVIDIA error messages are gone, so it seems to have mostly worked.  It wasn't the easiest fix or the shortest or cleanest fix, but I like my Ubuntu much better this way.

Earlier, I had tried uninstalling the **nouveau** driver module, but this was before I discovered that "blacklist nvidia-current" in **/etc/modprobe.d/blacklist-local.conf**
and everything seems to be working quite well after I re-installed the nouveau and nouveau firmware stuff from Synaptic.

The key seems to be in making sure you load the "nvidia" module instead of the "nvidia" module that you see under **lsmod | grep nv**. ;)  (I know- they are pretty ambiguous, but if **modinfo nvidia** works instead of an error message, you probably have the 'good' module).  Hurry right off to NVIDIA X Server Settings to confirm, and you should see an "NVIDIA Driver Version" newer than 173 if all has gone well.

I have heard/read that the 10.xx and 11.xx Ubuntu versions just "automatically" select the NVIDIA driver over the open source **nouveau** driver, but that certainly was NOT my experience under 64bit Lucid Lynx 10.04.3 LTS- I needed to manually configure things (and redo the same thing and reboot multiple times) before I was able to get **a working NVIDIA driver on just 1** of my 3 kernels.  Once I figured that out for my "32-21-generic" kernel, it was much easier to fix the other 2 (32-34-generic and 32-35-generic).

---

