---
title: "Nvidia kernel modules do not seem to be loading"
date: 2012-12-30
forum: Hardware
---

### Post by bitwaba on 2012-12-30
I've tried installing nvidia-current, nvidia-current-updates, nvidia-experimental-304, and nvidia-experimental-310, and am receiving the same result from all 4. After installing the driver and rebooting and logging in, all that is visible is my desktop background.  The top and side bar are missing, and the screen appears to be in low resolution mode although I can not get to system settings to see what resolution it is using.

Xorg.0.log seems to mention not being able to load the kernel module. Specifically:
> [    14.581] (II) LoadModule: "nvidia"
[    14.581] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    14.632] (II) Module nvidia: vendor="NVIDIA Corporation"
[    14.633]    compiled for 4.0.2, module version = 1.0.0
[    14.633]    Module class: X.Org Video Driver
[    14.655] (EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
[    14.655] (EE) NVIDIA:     system's kernel log for additional error messages.
[    14.655] (II) UnloadModule: "nvidia"
[    14.655] (II) Unloading nvidia
[    14.655] (EE) Failed to load module "nvidia" (module-specific error, 0)


I'm running desktop 12.10.

Thoughts? Suggestions? I'm not really sure how to proceed from here.




```

flowersster@boremachine:~$ lspci | grep -i nvidia
01:00.0 VGA compatible controller: NVIDIA Corporation GF114 [GeForce GTX 560 Ti] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GF114 HDMI Audio Controller (rev a1)

```


Xorg log file below:
```

[    14.161] 
X.Org X Server 1.13.0
Release Date: 2012-09-05
[    14.161] X Protocol Version 11, Revision 0
[    14.161] Build Operating System: Linux 3.2.0-32-generic x86_64 Ubuntu
[    14.161] Current Operating System: Linux boremachine 3.5.0-21-generic #32-Ubuntu SMP Tue Dec 11 18:51:59 UTC 2012 x86_64
[    14.161] Kernel command line: BOOT_IMAGE=/vmlinuz-3.5.0-21-generic root=UUID=6e0c67cd-a442-477e-bd3f-3339aa3c5289 ro quiet splash
[    14.161] Build Date: 27 November 2012  07:44:35AM
[    14.161] xorg-server 2:1.13.0-0ubuntu6.1 (For technical support please see http://www.ubuntu.com/support) 
[    14.161] Current version of pixman: 0.26.0
[    14.161] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    14.161] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    14.161] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Dec 30 21:23:58 2012
[    14.161] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    14.161] (==) No Layout section.  Using the first Screen section.
[    14.161] (==) No screen section available. Using defaults.
[    14.161] (**) |-->Screen "Default Screen Section" (0)
[    14.161] (**) |   |-->Monitor "<default monitor>"
[    14.162] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    14.162] (==) Automatically adding devices
[    14.162] (==) Automatically enabling devices
[    14.162] (==) Automatically adding GPU devices
[    14.162] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    14.162] 	Entry deleted from font path.
[    14.162] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    14.162] 	Entry deleted from font path.
[    14.162] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    14.162] 	Entry deleted from font path.
[    14.162] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    14.162] 	Entry deleted from font path.
[    14.162] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    14.162] 	Entry deleted from font path.
[    14.162] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    14.162] 	Entry deleted from font path.
[    14.162] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    14.162] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    14.162] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    14.162] (II) Loader magic: 0x7f9c0fb7bc40
[    14.162] (II) Module ABI versions:
[    14.162] 	X.Org ANSI C Emulation: 0.4
[    14.162] 	X.Org Video Driver: 13.0
[    14.162] 	X.Org XInput driver : 18.0
[    14.162] 	X.Org Server Extension : 7.0
[    14.163] (--) PCI:*(0:1:0:0) 10de:1200:1462:2384 rev 161, Mem @ 0xf8000000/33554432, 0xe8000000/134217728, 0xf0000000/67108864, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[    14.163] (II) Open ACPI successful (/var/run/acpid.socket)
[    14.163] Initializing built-in extension Generic Event Extension
[    14.163] Initializing built-in extension SHAPE
[    14.163] Initializing built-in extension MIT-SHM
[    14.163] Initializing built-in extension XInputExtension
[    14.163] Initializing built-in extension XTEST
[    14.163] Initializing built-in extension BIG-REQUESTS
[    14.163] Initializing built-in extension SYNC
[    14.163] Initializing built-in extension XKEYBOARD
[    14.163] Initializing built-in extension XC-MISC
[    14.163] Initializing built-in extension SECURITY
[    14.163] Initializing built-in extension XINERAMA
[    14.163] Initializing built-in extension XFIXES
[    14.163] Initializing built-in extension RENDER
[    14.163] Initializing built-in extension RANDR
[    14.163] Initializing built-in extension COMPOSITE
[    14.163] Initializing built-in extension DAMAGE
[    14.163] Initializing built-in extension MIT-SCREEN-SAVER
[    14.163] Initializing built-in extension DOUBLE-BUFFER
[    14.163] Initializing built-in extension RECORD
[    14.163] Initializing built-in extension DPMS
[    14.164] Initializing built-in extension X-Resource
[    14.164] Initializing built-in extension XVideo
[    14.164] Initializing built-in extension XVideo-MotionCompensation
[    14.164] Initializing built-in extension XFree86-VidModeExtension
[    14.164] Initializing built-in extension XFree86-DGA
[    14.164] Initializing built-in extension XFree86-DRI
[    14.164] Initializing built-in extension DRI2
[    14.164] (II) LoadModule: "glx"
[    14.194] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    14.581] (II) Module glx: vendor="NVIDIA Corporation"
[    14.581] 	compiled for 4.0.2, module version = 1.0.0
[    14.581] 	Module class: X.Org Server Extension
[    14.581] (II) NVIDIA GLX Module  310.14  Tue Oct  9 12:14:30 PDT 2012
[    14.581] Loading extension GLX
[    14.581] (==) Matched nvidia as autoconfigured driver 0
[    14.581] (==) Matched nouveau as autoconfigured driver 1
[    14.581] (==) Matched nv as autoconfigured driver 2
[    14.581] (==) Matched vesa as autoconfigured driver 3
[    14.581] (==) Matched modesetting as autoconfigured driver 4
[    14.581] (==) Matched fbdev as autoconfigured driver 5
[    14.581] (==) Assigned the driver to the xf86ConfigLayout
[    14.581] (II) LoadModule: "nvidia"
[    14.581] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    14.632] (II) Module nvidia: vendor="NVIDIA Corporation"
[    14.633] 	compiled for 4.0.2, module version = 1.0.0
[    14.633] 	Module class: X.Org Video Driver
[    14.655] (EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
[    14.655] (EE) NVIDIA:     system's kernel log for additional error messages.
[    14.655] (II) UnloadModule: "nvidia"
[    14.655] (II) Unloading nvidia
[    14.655] (EE) Failed to load module "nvidia" (module-specific error, 0)
[    14.655] (II) LoadModule: "nouveau"
[    14.655] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    14.656] (II) Module nouveau: vendor="X.Org Foundation"
[    14.656] 	compiled for 1.13.0, module version = 1.0.2
[    14.656] 	Module class: X.Org Video Driver
[    14.656] 	ABI class: X.Org Video Driver, version 13.0
[    14.656] (II) LoadModule: "nv"
[    14.656] (WW) Warning, couldn't open module nv
[    14.656] (II) UnloadModule: "nv"
[    14.656] (II) Unloading nv
[    14.656] (EE) Failed to load module "nv" (module does not exist, 0)
[    14.656] (II) LoadModule: "vesa"
[    14.656] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    14.656] (II) Module vesa: vendor="X.Org Foundation"
[    14.656] 	compiled for 1.12.99.902, module version = 2.3.2
[    14.656] 	Module class: X.Org Video Driver
[    14.656] 	ABI class: X.Org Video Driver, version 13.0
[    14.656] (II) LoadModule: "modesetting"
[    14.656] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    14.656] (II) Module modesetting: vendor="X.Org Foundation"
[    14.656] 	compiled for 1.13.0, module version = 0.5.0
[    14.656] 	Module class: X.Org Video Driver
[    14.656] 	ABI class: X.Org Video Driver, version 13.0
[    14.656] (II) LoadModule: "fbdev"
[    14.656] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    14.656] (II) Module fbdev: vendor="X.Org Foundation"
[    14.656] 	compiled for 1.12.99.902, module version = 0.4.3
[    14.656] 	Module class: X.Org Video Driver
[    14.657] 	ABI class: X.Org Video Driver, version 13.0
[    14.657] (==) Matched nvidia as autoconfigured driver 0
[    14.657] (==) Matched nouveau as autoconfigured driver 1
[    14.657] (==) Matched nv as autoconfigured driver 2
[    14.657] (==) Matched vesa as autoconfigured driver 3
[    14.657] (==) Matched modesetting as autoconfigured driver 4
[    14.657] (==) Matched fbdev as autoconfigured driver 5
[    14.657] (==) Assigned the driver to the xf86ConfigLayout
[    14.657] (II) LoadModule: "nvidia"
[    14.657] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    14.657] (II) Module nvidia: vendor="NVIDIA Corporation"
[    14.657] 	compiled for 4.0.2, module version = 1.0.0
[    14.657] 	Module class: X.Org Video Driver
[    14.658] (EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
[    14.658] (EE) NVIDIA:     system's kernel log for additional error messages.
[    14.658] (II) UnloadModule: "nvidia"
[    14.658] (II) Unloading nvidia
[    14.658] (EE) Failed to load module "nvidia" (module-specific error, 0)
[    14.658] (II) LoadModule: "nouveau"
[    14.658] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    14.658] (II) Module nouveau: vendor="X.Org Foundation"
[    14.658] 	compiled for 1.13.0, module version = 1.0.2
[    14.658] 	Module class: X.Org Video Driver
[    14.658] 	ABI class: X.Org Video Driver, version 13.0
[    14.658] (II) UnloadModule: "nouveau"
[    14.658] (II) Unloading nouveau
[    14.658] (II) Failed to load module "nouveau" (already loaded, 0)
[    14.658] (II) LoadModule: "nv"
[    14.658] (WW) Warning, couldn't open module nv
[    14.658] (II) UnloadModule: "nv"
[    14.658] (II) Unloading nv
[    14.658] (EE) Failed to load module "nv" (module does not exist, 0)
[    14.658] (II) LoadModule: "vesa"
[    14.658] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    14.658] (II) Module vesa: vendor="X.Org Foundation"
[    14.658] 	compiled for 1.12.99.902, module version = 2.3.2
[    14.658] 	Module class: X.Org Video Driver
[    14.658] 	ABI class: X.Org Video Driver, version 13.0
[    14.658] (II) UnloadModule: "vesa"
[    14.658] (II) Unloading vesa
[    14.658] (II) Failed to load module "vesa" (already loaded, 0)
[    14.658] (II) LoadModule: "modesetting"
[    14.658] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    14.658] (II) Module modesetting: vendor="X.Org Foundation"
[    14.658] 	compiled for 1.13.0, module version = 0.5.0
[    14.658] 	Module class: X.Org Video Driver
[    14.658] 	ABI class: X.Org Video Driver, version 13.0
[    14.658] (II) UnloadModule: "modesetting"
[    14.658] (II) Unloading modesetting
[    14.658] (II) Failed to load module "modesetting" (already loaded, 0)
[    14.658] (II) LoadModule: "fbdev"
[    14.658] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    14.658] (II) Module fbdev: vendor="X.Org Foundation"
[    14.658] 	compiled for 1.12.99.902, module version = 0.4.3
[    14.658] 	Module class: X.Org Video Driver
[    14.659] 	ABI class: X.Org Video Driver, version 13.0
[    14.659] (II) UnloadModule: "fbdev"
[    14.659] (II) Unloading fbdev
[    14.659] (II) Failed to load module "fbdev" (already loaded, 0)
[    14.659] (II) NOUVEAU driver Date:   Wed Sep 12 13:42:43 2012 +0200
[    14.659] (II) NOUVEAU driver for NVIDIA chipset families :
[    14.659] 	RIVA TNT        (NV04)
[    14.659] 	RIVA TNT2       (NV05)
[    14.659] 	GeForce 256     (NV10)
[    14.659] 	GeForce 2       (NV11, NV15)
[    14.659] 	GeForce 4MX     (NV17, NV18)
[    14.659] 	GeForce 3       (NV20)
[    14.659] 	GeForce 4Ti     (NV25, NV28)
[    14.659] 	GeForce FX      (NV3x)
[    14.659] 	GeForce 6       (NV4x)
[    14.659] 	GeForce 7       (G7x)
[    14.659] 	GeForce 8       (G8x)
[    14.659] 	GeForce GTX 200 (NVA0)
[    14.659] 	GeForce GTX 400 (NVC0)
[    14.659] (II) VESA: driver for VESA chipsets: vesa
[    14.659] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    14.659] (II) FBDEV: driver for framebuffer: fbdev
[    14.659] (++) using VT number 7

[    14.728] (EE) [drm] failed to open device
[    14.796] (EE) [drm] failed to open device
[    14.796] (WW) Falling back to old probe method for modesetting
[    14.796] (EE) open /dev/dri/card0: No such file or directory
[    14.796] (EE) open /dev/dri/card0: No such file or directory
[    14.796] (WW) Falling back to old probe method for fbdev
[    14.796] (II) Loading sub module "fbdevhw"
[    14.796] (II) LoadModule: "fbdevhw"
[    14.796] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    14.796] (II) Module fbdevhw: vendor="X.Org Foundation"
[    14.796] 	compiled for 1.13.0, module version = 0.0.2
[    14.796] 	ABI class: X.Org Video Driver, version 13.0
[    14.796] (EE) open /dev/fb0: No such file or directory
[    14.796] (II) Loading sub module "vbe"
[    14.796] (II) LoadModule: "vbe"
[    14.797] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    14.806] (II) Module vbe: vendor="X.Org Foundation"
[    14.807] 	compiled for 1.13.0, module version = 1.1.0
[    14.807] 	ABI class: X.Org Video Driver, version 13.0
[    14.807] (II) Loading sub module "int10"
[    14.807] (II) LoadModule: "int10"
[    14.807] (II) Loading /usr/lib/xorg/modules/libint10.so
[    14.828] (II) Module int10: vendor="X.Org Foundation"
[    14.828] 	compiled for 1.13.0, module version = 1.0.0
[    14.828] 	ABI class: X.Org Video Driver, version 13.0
[    14.828] (II) VESA(0): initializing int10
[    14.828] (II) VESA(0): Bad V_BIOS checksum
[    14.828] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    14.878] (II) VESA(0): VESA BIOS detected
[    14.878] (II) VESA(0): VESA VBE Version 3.0
[    14.878] (II) VESA(0): VESA VBE Total Mem: 14336 kB
[    14.878] (II) VESA(0): VESA VBE OEM: NVIDIA
[    14.878] (II) VESA(0): VESA VBE OEM Software Rev: 112.36
[    14.878] (II) VESA(0): VESA VBE OEM Vendor: NVIDIA Corporation
[    14.878] (II) VESA(0): VESA VBE OEM Product: GF104B Board - 10400050
[    14.878] (II) VESA(0): VESA VBE OEM Product Rev: Chip Rev   
[    14.970] (II) VESA(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    14.970] (==) VESA(0): Depth 24, (--) framebuffer bpp 32
[    14.970] (==) VESA(0): RGB weight 888
[    14.970] (==) VESA(0): Default visual is TrueColor
[    14.970] (==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
[    14.970] (II) Loading sub module "ddc"
[    14.970] (II) LoadModule: "ddc"
[    14.970] (II) Module "ddc" already built-in
[    14.971] (II) VESA(0): VESA VBE DDC supported
[    14.971] (II) VESA(0): VESA VBE DDC Level 2
[    14.971] (II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
[    15.006] (II) VESA(0): VESA VBE DDC read successfully
[    15.006] (II) VESA(0): Manufacturer: ACI  Model: 22fa  Serial#: 16843009
[    15.006] (II) VESA(0): Year: 2011  Week: 53
[    15.006] (II) VESA(0): EDID Version: 1.3
[    15.006] (II) VESA(0): Digital Display Input
[    15.006] (II) VESA(0): Max Image Size [cm]: horiz.: 48  vert.: 27
[    15.006] (II) VESA(0): Gamma: 2.20
[    15.006] (II) VESA(0): DPMS capabilities: StandBy Suspend Off
[    15.006] (II) VESA(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    15.006] (II) VESA(0): First detailed timing is preferred mode
[    15.006] (II) VESA(0): redX: 0.637 redY: 0.351   greenX: 0.319 greenY: 0.626
[    15.006] (II) VESA(0): blueX: 0.145 blueY: 0.061   whiteX: 0.313 whiteY: 0.329
[    15.006] (II) VESA(0): Supported established timings:
[    15.006] (II) VESA(0): 720x400@70Hz
[    15.006] (II) VESA(0): 640x480@60Hz
[    15.006] (II) VESA(0): 640x480@67Hz
[    15.006] (II) VESA(0): 640x480@72Hz
[    15.006] (II) VESA(0): 640x480@75Hz
[    15.006] (II) VESA(0): 800x600@56Hz
[    15.006] (II) VESA(0): 800x600@60Hz
[    15.006] (II) VESA(0): 800x600@72Hz
[    15.006] (II) VESA(0): 800x600@75Hz
[    15.006] (II) VESA(0): 832x624@75Hz
[    15.006] (II) VESA(0): 1024x768@60Hz
[    15.006] (II) VESA(0): 1024x768@70Hz
[    15.006] (II) VESA(0): 1024x768@75Hz
[    15.006] (II) VESA(0): 1280x1024@75Hz
[    15.006] (II) VESA(0): Manufacturer's mask: 0
[    15.006] (II) VESA(0): Supported standard timings:
[    15.006] (II) VESA(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    15.006] (II) VESA(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    15.006] (II) VESA(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    15.006] (II) VESA(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    15.006] (II) VESA(0): #4: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
[    15.006] (II) VESA(0): #5: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[    15.006] (II) VESA(0): #6: hsize: 1920  vsize 1080  refresh: 60  vid: 49361
[    15.006] (II) VESA(0): Supported detailed timing:
[    15.006] (II) VESA(0): clock: 148.5 MHz   Image Size:  477 x 268 mm
[    15.006] (II) VESA(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    15.006] (II) VESA(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    15.006] (II) VESA(0): Ranges: V min: 50 V max: 76 Hz, H min: 30 H max: 83 kHz, PixClock max 175 MHz
[    15.006] (II) VESA(0): Monitor name: VE228
[    15.006] (II) VESA(0): Serial No: BCLMQS111231
[    15.006] (II) VESA(0): EDID (in hex):
[    15.006] (II) VESA(0): 	00ffffffffffff000469fa2201010101
[    15.006] (II) VESA(0): 	3515010380301b78ea3d25a35951a025
[    15.006] (II) VESA(0): 	0f5054bfef00714f818081409500a940
[    15.006] (II) VESA(0): 	b300d1c00101023a801871382d40582c
[    15.006] (II) VESA(0): 	4500dd0c1100001e000000fd00324c1e
[    15.006] (II) VESA(0): 	5311000a202020202020000000fc0056
[    15.006] (II) VESA(0): 	453232380a20202020202020000000ff
[    15.006] (II) VESA(0): 	0042434c4d51533131313233310a0040
[    15.006] (II) VESA(0): EDID vendor "ACI", prod id 8954
[    15.006] (II) VESA(0): Using EDID range info for horizontal sync
[    15.006] (II) VESA(0): Using EDID range info for vertical refresh
[    15.006] (II) VESA(0): Printing DDC gathered Modelines:
[    15.006] (II) VESA(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    15.006] (II) VESA(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    15.006] (II) VESA(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    15.006] (II) VESA(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    15.006] (II) VESA(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    15.006] (II) VESA(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    15.006] (II) VESA(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    15.006] (II) VESA(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    15.006] (II) VESA(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    15.006] (II) VESA(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    15.006] (II) VESA(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    15.006] (II) VESA(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    15.006] (II) VESA(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    15.006] (II) VESA(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    15.006] (II) VESA(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    15.006] (II) VESA(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    15.006] (II) VESA(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    15.006] (II) VESA(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    15.006] (II) VESA(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[    15.006] (II) VESA(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz e)
[    15.006] (II) VESA(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[    15.006] (II) VESA(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[    15.006] (II) VESA(0): Searching for matching VESA mode(s):
[    15.008] Mode: 100 (640x400)
[    15.008] 	ModeAttributes: 0x3bf
[    15.008] 	WinAAttributes: 0x7
[    15.008] 	WinBAttributes: 0x0
[    15.008] 	WinGranularity: 64
[    15.008] 	WinSize: 64
[    15.008] 	WinASegment: 0xa000
[    15.008] 	WinBSegment: 0x0
[    15.008] 	WinFuncPtr: 0xc000791e
[    15.008] 	BytesPerScanline: 640
[    15.008] 	XResolution: 640
[    15.008] 	YResolution: 400
[    15.008] 	XCharSize: 8
[    15.008] 	YCharSize: 16
[    15.008] 	NumberOfPlanes: 1
[    15.008] 	BitsPerPixel: 8
[    15.008] 	NumberOfBanks: 1
[    15.008] 	MemoryModel: 4
[    15.008] 	BankSize: 0
[    15.008] 	NumberOfImages: 14
[    15.008] 	RedMaskSize: 0
[    15.008] 	RedFieldPosition: 0
[    15.008] 	GreenMaskSize: 0
[    15.008] 	GreenFieldPosition: 0
[    15.008] 	BlueMaskSize: 0
[    15.008] 	BlueFieldPosition: 0
[    15.008] 	RsvdMaskSize: 0
[    15.008] 	RsvdFieldPosition: 0
[    15.008] 	DirectColorModeInfo: 0
[    15.008] 	PhysBasePtr: 0xf1000000
[    15.008] 	LinBytesPerScanLine: 640
[    15.008] 	BnkNumberOfImagePages: 14
[    15.008] 	LinNumberOfImagePages: 14
[    15.008] 	LinRedMaskSize: 0
[    15.008] 	LinRedFieldPosition: 0
[    15.008] 	LinGreenMaskSize: 0
[    15.008] 	LinGreenFieldPosition: 0
[    15.008] 	LinBlueMaskSize: 0
[    15.008] 	LinBlueFieldPosition: 0
[    15.008] 	LinRsvdMaskSize: 0
[    15.008] 	LinRsvdFieldPosition: 0
[    15.008] 	MaxPixelClock: 229500000
[    15.009] Mode: 101 (640x480)
[    15.009] 	ModeAttributes: 0x3bf
[    15.009] 	WinAAttributes: 0x7
[    15.009] 	WinBAttributes: 0x0
[    15.009] 	WinGranularity: 64
[    15.009] 	WinSize: 64
[    15.009] 	WinASegment: 0xa000
[    15.009] 	WinBSegment: 0x0
[    15.009] 	WinFuncPtr: 0xc000791e
[    15.009] 	BytesPerScanline: 640
[    15.009] 	XResolution: 640
[    15.009] 	YResolution: 480
[    15.009] 	XCharSize: 8
[    15.009] 	YCharSize: 16
[    15.009] 	NumberOfPlanes: 1
[    15.009] 	BitsPerPixel: 8
[    15.009] 	NumberOfBanks: 1
[    15.009] 	MemoryModel: 4
[    15.009] 	BankSize: 0
[    15.009] 	NumberOfImages: 10
[    15.009] 	RedMaskSize: 0
[    15.009] 	RedFieldPosition: 0
[    15.009] 	GreenMaskSize: 0
[    15.009] 	GreenFieldPosition: 0
[    15.009] 	BlueMaskSize: 0
[    15.009] 	BlueFieldPosition: 0
[    15.009] 	RsvdMaskSize: 0
[    15.009] 	RsvdFieldPosition: 0
[    15.009] 	DirectColorModeInfo: 0
[    15.009] 	PhysBasePtr: 0xf1000000
[    15.009] 	LinBytesPerScanLine: 640
[    15.009] 	BnkNumberOfImagePages: 10
[    15.009] 	LinNumberOfImagePages: 10
[    15.009] 	LinRedMaskSize: 0
[    15.009] 	LinRedFieldPosition: 0
[    15.009] 	LinGreenMaskSize: 0
[    15.009] 	LinGreenFieldPosition: 0
[    15.009] 	LinBlueMaskSize: 0
[    15.009] 	LinBlueFieldPosition: 0
[    15.009] 	LinRsvdMaskSize: 0
[    15.009] 	LinRsvdFieldPosition: 0
[    15.009] 	MaxPixelClock: 229500000
[    15.011] Mode: 102 (800x600)
[    15.011] 	ModeAttributes: 0x33f
[    15.011] 	WinAAttributes: 0x7
[    15.011] 	WinBAttributes: 0x0
[    15.011] 	WinGranularity: 64
[    15.011] 	WinSize: 64
[    15.011] 	WinASegment: 0xa000
[    15.011] 	WinBSegment: 0x0
[    15.011] 	WinFuncPtr: 0xc000791e
[    15.011] 	BytesPerScanline: 100
[    15.011] 	XResolution: 800
[    15.011] 	YResolution: 600
[    15.011] 	XCharSize: 8
[    15.011] 	YCharSize: 16
[    15.011] 	NumberOfPlanes: 4
[    15.011] 	BitsPerPixel: 4
[    15.011] 	NumberOfBanks: 1
[    15.011] 	MemoryModel: 3
[    15.011] 	BankSize: 0
[    15.011] 	NumberOfImages: 2
[    15.011] 	RedMaskSize: 0
[    15.011] 	RedFieldPosition: 0
[    15.011] 	GreenMaskSize: 0
[    15.011] 	GreenFieldPosition: 0
[    15.011] 	BlueMaskSize: 0
[    15.011] 	BlueFieldPosition: 0
[    15.011] 	RsvdMaskSize: 0
[    15.011] 	RsvdFieldPosition: 0
[    15.011] 	DirectColorModeInfo: 0
[    15.011] 	PhysBasePtr: 0x0
[    15.011] 	LinBytesPerScanLine: 100
[    15.011] 	BnkNumberOfImagePages: 2
[    15.011] 	LinNumberOfImagePages: 2
[    15.011] 	LinRedMaskSize: 0
[    15.011] 	LinRedFieldPosition: 0
[    15.011] 	LinGreenMaskSize: 0
[    15.011] 	LinGreenFieldPosition: 0
[    15.011] 	LinBlueMaskSize: 0
[    15.011] 	LinBlueFieldPosition: 0
[    15.011] 	LinRsvdMaskSize: 0
[    15.011] 	LinRsvdFieldPosition: 0
[    15.011] 	MaxPixelClock: 108500000
[    15.012] Mode: 103 (800x600)
[    15.012] 	ModeAttributes: 0x3bf
[    15.012] 	WinAAttributes: 0x7
[    15.012] 	WinBAttributes: 0x0
[    15.012] 	WinGranularity: 64
[    15.012] 	WinSize: 64
[    15.012] 	WinASegment: 0xa000
[    15.012] 	WinBSegment: 0x0
[    15.012] 	WinFuncPtr: 0xc000791e
[    15.012] 	BytesPerScanline: 800
[    15.012] 	XResolution: 800
[    15.012] 	YResolution: 600
[    15.012] 	XCharSize: 8
[    15.012] 	YCharSize: 16
[    15.012] 	NumberOfPlanes: 1
[    15.012] 	BitsPerPixel: 8
[    15.012] 	NumberOfBanks: 1
[    15.012] 	MemoryModel: 4
[    15.012] 	BankSize: 0
[    15.012] 	NumberOfImages: 6
[    15.012] 	RedMaskSize: 0
[    15.012] 	RedFieldPosition: 0
[    15.012] 	GreenMaskSize: 0
[    15.012] 	GreenFieldPosition: 0
[    15.012] 	BlueMaskSize: 0
[    15.012] 	BlueFieldPosition: 0
[    15.012] 	RsvdMaskSize: 0
[    15.012] 	RsvdFieldPosition: 0
[    15.012] 	DirectColorModeInfo: 0
[    15.012] 	PhysBasePtr: 0xf1000000
[    15.012] 	LinBytesPerScanLine: 800
[    15.012] 	BnkNumberOfImagePages: 6
[    15.012] 	LinNumberOfImagePages: 6
[    15.012] 	LinRedMaskSize: 0
[    15.012] 	LinRedFieldPosition: 0
[    15.012] 	LinGreenMaskSize: 0
[    15.012] 	LinGreenFieldPosition: 0
[    15.012] 	LinBlueMaskSize: 0
[    15.012] 	LinBlueFieldPosition: 0
[    15.012] 	LinRsvdMaskSize: 0
[    15.012] 	LinRsvdFieldPosition: 0
[    15.012] 	MaxPixelClock: 229500000
[    15.014] Mode: 104 (1024x768)
[    15.014] 	ModeAttributes: 0x33f
[    15.014] 	WinAAttributes: 0x7
[    15.014] 	WinBAttributes: 0x0
[    15.014] 	WinGranularity: 64
[    15.014] 	WinSize: 64
[    15.014] 	WinASegment: 0xa000
[    15.014] 	WinBSegment: 0x0
[    15.014] 	WinFuncPtr: 0xc000791e
[    15.014] 	BytesPerScanline: 128
[    15.014] 	XResolution: 1024
[    15.014] 	YResolution: 768
[    15.014] 	XCharSize: 8
[    15.014] 	YCharSize: 16
[    15.014] 	NumberOfPlanes: 4
[    15.014] 	BitsPerPixel: 4
[    15.014] 	NumberOfBanks: 1
[    15.014] 	MemoryModel: 3
[    15.014] 	BankSize: 0
[    15.014] 	NumberOfImages: 1
[    15.014] 	RedMaskSize: 0
[    15.014] 	RedFieldPosition: 0
[    15.014] 	GreenMaskSize: 0
[    15.014] 	GreenFieldPosition: 0
[    15.014] 	BlueMaskSize: 0
[    15.014] 	BlueFieldPosition: 0
[    15.014] 	RsvdMaskSize: 0
[    15.014] 	RsvdFieldPosition: 0
[    15.014] 	DirectColorModeInfo: 0
[    15.014] 	PhysBasePtr: 0x0
[    15.014] 	LinBytesPerScanLine: 128
[    15.014] 	BnkNumberOfImagePages: 1
[    15.014] 	LinNumberOfImagePages: 1
[    15.014] 	LinRedMaskSize: 0
[    15.014] 	LinRedFieldPosition: 0
[    15.014] 	LinGreenMaskSize: 0
[    15.014] 	LinGreenFieldPosition: 0
[    15.014] 	LinBlueMaskSize: 0
[    15.014] 	LinBlueFieldPosition: 0
[    15.014] 	LinRsvdMaskSize: 0
[    15.014] 	LinRsvdFieldPosition: 0
[    15.014] 	MaxPixelClock: 108500000
[    15.015] Mode: 105 (1024x768)
[    15.015] 	ModeAttributes: 0x3bf
[    15.015] 	WinAAttributes: 0x7
[    15.015] 	WinBAttributes: 0x0
[    15.015] 	WinGranularity: 64
[    15.015] 	WinSize: 64
[    15.015] 	WinASegment: 0xa000
[    15.015] 	WinBSegment: 0x0
[    15.015] 	WinFuncPtr: 0xc000791e
[    15.015] 	BytesPerScanline: 1024
[    15.015] 	XResolution: 1024
[    15.015] 	YResolution: 768
[    15.015] 	XCharSize: 8
[    15.015] 	YCharSize: 16
[    15.015] 	NumberOfPlanes: 1
[    15.015] 	BitsPerPixel: 8
[    15.015] 	NumberOfBanks: 1
[    15.015] 	MemoryModel: 4
[    15.015] 	BankSize: 0
[    15.015] 	NumberOfImages: 3
[    15.015] 	RedMaskSize: 0
[    15.015] 	RedFieldPosition: 0
[    15.015] 	GreenMaskSize: 0
[    15.015] 	GreenFieldPosition: 0
[    15.015] 	BlueMaskSize: 0
[    15.015] 	BlueFieldPosition: 0
[    15.015] 	RsvdMaskSize: 0
[    15.015] 	RsvdFieldPosition: 0
[    15.015] 	DirectColorModeInfo: 0
[    15.015] 	PhysBasePtr: 0xf1000000
[    15.015] 	LinBytesPerScanLine: 1024
[    15.015] 	BnkNumberOfImagePages: 3
[    15.015] 	LinNumberOfImagePages: 3
[    15.015] 	LinRedMaskSize: 0
[    15.015] 	LinRedFieldPosition: 0
[    15.015] 	LinGreenMaskSize: 0
[    15.015] 	LinGreenFieldPosition: 0
[    15.015] 	LinBlueMaskSize: 0
[    15.015] 	LinBlueFieldPosition: 0
[    15.015] 	LinRsvdMaskSize: 0
[    15.015] 	LinRsvdFieldPosition: 0
[    15.015] 	MaxPixelClock: 229500000
[    15.017] Mode: 106 (1280x1024)
[    15.017] 	ModeAttributes: 0x33f
[    15.017] 	WinAAttributes: 0x7
[    15.017] 	WinBAttributes: 0x0
[    15.017] 	WinGranularity: 64
[    15.017] 	WinSize: 64
[    15.017] 	WinASegment: 0xa000
[    15.017] 	WinBSegment: 0x0
[    15.017] 	WinFuncPtr: 0xc000791e
[    15.017] 	BytesPerScanline: 160
[    15.017] 	XResolution: 1280
[    15.017] 	YResolution: 1024
[    15.017] 	XCharSize: 8
[    15.017] 	YCharSize: 16
[    15.017] 	NumberOfPlanes: 4
[    15.017] 	BitsPerPixel: 4
[    15.017] 	NumberOfBanks: 1
[    15.017] 	MemoryModel: 3
[    15.017] 	BankSize: 0
[    15.017] 	NumberOfImages: 1
[    15.017] 	RedMaskSize: 0
[    15.017] 	RedFieldPosition: 0
[    15.017] 	GreenMaskSize: 0
[    15.017] 	GreenFieldPosition: 0
[    15.017] 	BlueMaskSize: 0
[    15.017] 	BlueFieldPosition: 0
[    15.017] 	RsvdMaskSize: 0
[    15.017] 	RsvdFieldPosition: 0
[    15.017] 	DirectColorModeInfo: 0
[    15.017] 	PhysBasePtr: 0x0
[    15.017] 	LinBytesPerScanLine: 160
[    15.017] 	BnkNumberOfImagePages: 1
[    15.017] 	LinNumberOfImagePages: 1
[    15.017] 	LinRedMaskSize: 0
[    15.017] 	LinRedFieldPosition: 0
[    15.017] 	LinGreenMaskSize: 0
[    15.017] 	LinGreenFieldPosition: 0
[    15.017] 	LinBlueMaskSize: 0
[    15.017] 	LinBlueFieldPosition: 0
[    15.017] 	LinRsvdMaskSize: 0
[    15.017] 	LinRsvdFieldPosition: 0
[    15.017] 	MaxPixelClock: 108500000
[    15.018] Mode: 107 (1280x1024)
[    15.018] 	ModeAttributes: 0x3bf
[    15.018] 	WinAAttributes: 0x7
[    15.018] 	WinBAttributes: 0x0
[    15.018] 	WinGranularity: 64
[    15.018] 	WinSize: 64
[    15.018] 	WinASegment: 0xa000
[    15.018] 	WinBSegment: 0x0
[    15.018] 	WinFuncPtr: 0xc000791e
[    15.018] 	BytesPerScanline: 1280
[    15.018] 	XResolution: 1280
[    15.018] 	YResolution: 1024
[    15.018] 	XCharSize: 8
[    15.018] 	YCharSize: 16
[    15.018] 	NumberOfPlanes: 1
[    15.018] 	BitsPerPixel: 8
[    15.018] 	NumberOfBanks: 1
[    15.018] 	MemoryModel: 4
[    15.018] 	BankSize: 0
[    15.018] 	NumberOfImages: 1
[    15.018] 	RedMaskSize: 0
[    15.018] 	RedFieldPosition: 0
[    15.018] 	GreenMaskSize: 0
[    15.018] 	GreenFieldPosition: 0
[    15.018] 	BlueMaskSize: 0
[    15.018] 	BlueFieldPosition: 0
[    15.018] 	RsvdMaskSize: 0
[    15.018] 	RsvdFieldPosition: 0
[    15.018] 	DirectColorModeInfo: 0
[    15.018] 	PhysBasePtr: 0xf1000000
[    15.018] 	LinBytesPerScanLine: 1280
[    15.018] 	BnkNumberOfImagePages: 1
[    15.018] 	LinNumberOfImagePages: 1
[    15.018] 	LinRedMaskSize: 0
[    15.018] 	LinRedFieldPosition: 0
[    15.018] 	LinGreenMaskSize: 0
[    15.018] 	LinGreenFieldPosition: 0
[    15.018] 	LinBlueMaskSize: 0
[    15.018] 	LinBlueFieldPosition: 0
[    15.019] 	LinRsvdMaskSize: 0
[    15.019] 	LinRsvdFieldPosition: 0
[    15.019] 	MaxPixelClock: 229500000
[    15.020] Mode: 10e (320x200)
[    15.020] 	ModeAttributes: 0x3bf
[    15.020] 	WinAAttributes: 0x7
[    15.020] 	WinBAttributes: 0x0
[    15.020] 	WinGranularity: 64
[    15.020] 	WinSize: 64
[    15.020] 	WinASegment: 0xa000
[    15.020] 	WinBSegment: 0x0
[    15.020] 	WinFuncPtr: 0xc000791e
[    15.020] 	BytesPerScanline: 640
[    15.020] 	XResolution: 320
[    15.020] 	YResolution: 200
[    15.020] 	XCharSize: 8
[    15.020] 	YCharSize: 8
[    15.020] 	NumberOfPlanes: 1
[    15.020] 	BitsPerPixel: 16
[    15.020] 	NumberOfBanks: 1
[    15.020] 	MemoryModel: 6
[    15.020] 	BankSize: 0
[    15.020] 	NumberOfImages: 30
[    15.020] 	RedMaskSize: 5
[    15.020] 	RedFieldPosition: 11
[    15.020] 	GreenMaskSize: 6
[    15.020] 	GreenFieldPosition: 5
[    15.020] 	BlueMaskSize: 5
[    15.020] 	BlueFieldPosition: 0
[    15.020] 	RsvdMaskSize: 0
[    15.020] 	RsvdFieldPosition: 0
[    15.020] 	DirectColorModeInfo: 0
[    15.020] 	PhysBasePtr: 0xf1000000
[    15.020] 	LinBytesPerScanLine: 640
[    15.020] 	BnkNumberOfImagePages: 30
[    15.020] 	LinNumberOfImagePages: 30
[    15.020] 	LinRedMaskSize: 5
[    15.020] 	LinRedFieldPosition: 11
[    15.020] 	LinGreenMaskSize: 6
[    15.020] 	LinGreenFieldPosition: 5
[    15.020] 	LinBlueMaskSize: 5
[    15.020] 	LinBlueFieldPosition: 0
[    15.020] 	LinRsvdMaskSize: 0
[    15.020] 	LinRsvdFieldPosition: 0
[    15.020] 	MaxPixelClock: 229500000
[    15.021] *Mode: 10f (320x200)
[    15.021] 	ModeAttributes: 0x3bf
[    15.021] 	WinAAttributes: 0x7
[    15.021] 	WinBAttributes: 0x0
[    15.021] 	WinGranularity: 64
[    15.021] 	WinSize: 64
[    15.021] 	WinASegment: 0xa000
[    15.021] 	WinBSegment: 0x0
[    15.021] 	WinFuncPtr: 0xc000791e
[    15.021] 	BytesPerScanline: 1280
[    15.021] 	XResolution: 320
[    15.021] 	YResolution: 200
[    15.021] 	XCharSize: 8
[    15.021] 	YCharSize: 8
[    15.021] 	NumberOfPlanes: 1
[    15.021] 	BitsPerPixel: 32
[    15.021] 	NumberOfBanks: 1
[    15.021] 	MemoryModel: 6
[    15.021] 	BankSize: 0
[    15.021] 	NumberOfImages: 14
[    15.021] 	RedMaskSize: 8
[    15.021] 	RedFieldPosition: 16
[    15.021] 	GreenMaskSize: 8
[    15.021] 	GreenFieldPosition: 8
[    15.021] 	BlueMaskSize: 8
[    15.021] 	BlueFieldPosition: 0
[    15.021] 	RsvdMaskSize: 8
[    15.021] 	RsvdFieldPosition: 24
[    15.021] 	DirectColorModeInfo: 0
[    15.021] 	PhysBasePtr: 0xf1000000
[    15.021] 	LinBytesPerScanLine: 1280
[    15.021] 	BnkNumberOfImagePages: 14
[    15.021] 	LinNumberOfImagePages: 14
[    15.021] 	LinRedMaskSize: 8
[    15.021] 	LinRedFieldPosition: 16
[    15.021] 	LinGreenMaskSize: 8
[    15.021] 	LinGreenFieldPosition: 8
[    15.022] 	LinBlueMaskSize: 8
[    15.022] 	LinBlueFieldPosition: 0
[    15.022] 	LinRsvdMaskSize: 8
[    15.022] 	LinRsvdFieldPosition: 24
[    15.022] 	MaxPixelClock: 229500000
[    15.023] Mode: 111 (640x480)
[    15.023] 	ModeAttributes: 0x3bf
[    15.023] 	WinAAttributes: 0x7
[    15.023] 	WinBAttributes: 0x0
[    15.023] 	WinGranularity: 64
[    15.023] 	WinSize: 64
[    15.023] 	WinASegment: 0xa000
[    15.023] 	WinBSegment: 0x0
[    15.023] 	WinFuncPtr: 0xc000791e
[    15.023] 	BytesPerScanline: 1280
[    15.023] 	XResolution: 640
[    15.023] 	YResolution: 480
[    15.023] 	XCharSize: 8
[    15.023] 	YCharSize: 16
[    15.023] 	NumberOfPlanes: 1
[    15.023] 	BitsPerPixel: 16
[    15.023] 	NumberOfBanks: 1
[    15.023] 	MemoryModel: 6
[    15.023] 	BankSize: 0
[    15.023] 	NumberOfImages: 4
[    15.023] 	RedMaskSize: 5
[    15.023] 	RedFieldPosition: 11
[    15.023] 	GreenMaskSize: 6
[    15.023] 	GreenFieldPosition: 5
[    15.023] 	BlueMaskSize: 5
[    15.023] 	BlueFieldPosition: 0
[    15.023] 	RsvdMaskSize: 0
[    15.023] 	RsvdFieldPosition: 0
[    15.023] 	DirectColorModeInfo: 0
[    15.023] 	PhysBasePtr: 0xf1000000
[    15.023] 	LinBytesPerScanLine: 1280
[    15.023] 	BnkNumberOfImagePages: 4
[    15.023] 	LinNumberOfImagePages: 4
[    15.023] 	LinRedMaskSize: 5
[    15.023] 	LinRedFieldPosition: 11
[    15.023] 	LinGreenMaskSize: 6
[    15.023] 	LinGreenFieldPosition: 5
[    15.023] 	LinBlueMaskSize: 5
[    15.023] 	LinBlueFieldPosition: 0
[    15.023] 	LinRsvdMaskSize: 0
[    15.023] 	LinRsvdFieldPosition: 0
[    15.023] 	MaxPixelClock: 229500000
[    15.024] *Mode: 112 (640x480)
[    15.024] 	ModeAttributes: 0x3bf
[    15.024] 	WinAAttributes: 0x7
[    15.024] 	WinBAttributes: 0x0
[    15.024] 	WinGranularity: 64
[    15.024] 	WinSize: 64
[    15.024] 	WinASegment: 0xa000
[    15.024] 	WinBSegment: 0x0
[    15.024] 	WinFuncPtr: 0xc000791e
[    15.024] 	BytesPerScanline: 2560
[    15.024] 	XResolution: 640
[    15.024] 	YResolution: 480
[    15.024] 	XCharSize: 8
[    15.024] 	YCharSize: 16
[    15.024] 	NumberOfPlanes: 1
[    15.024] 	BitsPerPixel: 32
[    15.024] 	NumberOfBanks: 1
[    15.024] 	MemoryModel: 6
[    15.024] 	BankSize: 0
[    15.024] 	NumberOfImages: 1
[    15.024] 	RedMaskSize: 8
[    15.024] 	RedFieldPosition: 16
[    15.024] 	GreenMaskSize: 8
[    15.024] 	GreenFieldPosition: 8
[    15.024] 	BlueMaskSize: 8
[    15.024] 	BlueFieldPosition: 0
[    15.024] 	RsvdMaskSize: 8
[    15.024] 	RsvdFieldPosition: 24
[    15.024] 	DirectColorModeInfo: 0
[    15.024] 	PhysBasePtr: 0xf1000000
[    15.024] 	LinBytesPerScanLine: 2560
[    15.024] 	BnkNumberOfImagePages: 1
[    15.024] 	LinNumberOfImagePages: 1
[    15.024] 	LinRedMaskSize: 8
[    15.024] 	LinRedFieldPosition: 16
[    15.024] 	LinGreenMaskSize: 8
[    15.025] 	LinGreenFieldPosition: 8
[    15.025] 	LinBlueMaskSize: 8
[    15.025] 	LinBlueFieldPosition: 0
[    15.025] 	LinRsvdMaskSize: 8
[    15.025] 	LinRsvdFieldPosition: 24
[    15.025] 	MaxPixelClock: 229500000
[    15.026] Mode: 114 (800x600)
[    15.026] 	ModeAttributes: 0x3bf
[    15.026] 	WinAAttributes: 0x7
[    15.026] 	WinBAttributes: 0x0
[    15.026] 	WinGranularity: 64
[    15.026] 	WinSize: 64
[    15.026] 	WinASegment: 0xa000
[    15.026] 	WinBSegment: 0x0
[    15.026] 	WinFuncPtr: 0xc000791e
[    15.026] 	BytesPerScanline: 1600
[    15.026] 	XResolution: 800
[    15.026] 	YResolution: 600
[    15.026] 	XCharSize: 8
[    15.026] 	YCharSize: 16
[    15.026] 	NumberOfPlanes: 1
[    15.026] 	BitsPerPixel: 16
[    15.026] 	NumberOfBanks: 1
[    15.026] 	MemoryModel: 6
[    15.026] 	BankSize: 0
[    15.026] 	NumberOfImages: 2
[    15.026] 	RedMaskSize: 5
[    15.026] 	RedFieldPosition: 11
[    15.026] 	GreenMaskSize: 6
[    15.026] 	GreenFieldPosition: 5
[    15.026] 	BlueMaskSize: 5
[    15.026] 	BlueFieldPosition: 0
[    15.026] 	RsvdMaskSize: 0
[    15.026] 	RsvdFieldPosition: 0
[    15.026] 	DirectColorModeInfo: 0
[    15.026] 	PhysBasePtr: 0xf1000000
[    15.026] 	LinBytesPerScanLine: 1600
[    15.026] 	BnkNumberOfImagePages: 2
[    15.026] 	LinNumberOfImagePages: 2
[    15.026] 	LinRedMaskSize: 5
[    15.026] 	LinRedFieldPosition: 11
[    15.026] 	LinGreenMaskSize: 6
[    15.026] 	LinGreenFieldPosition: 5
[    15.026] 	LinBlueMaskSize: 5
[    15.026] 	LinBlueFieldPosition: 0
[    15.026] 	LinRsvdMaskSize: 0
[    15.026] 	LinRsvdFieldPosition: 0
[    15.026] 	MaxPixelClock: 229500000
[    15.027] *Mode: 115 (800x600)
[    15.027] 	ModeAttributes: 0x3bf
[    15.027] 	WinAAttributes: 0x7
[    15.027] 	WinBAttributes: 0x0
[    15.027] 	WinGranularity: 64
[    15.027] 	WinSize: 64
[    15.027] 	WinASegment: 0xa000
[    15.027] 	WinBSegment: 0x0
[    15.027] 	WinFuncPtr: 0xc000791e
[    15.027] 	BytesPerScanline: 3200
[    15.027] 	XResolution: 800
[    15.027] 	YResolution: 600
[    15.027] 	XCharSize: 8
[    15.027] 	YCharSize: 16
[    15.027] 	NumberOfPlanes: 1
[    15.027] 	BitsPerPixel: 32
[    15.027] 	NumberOfBanks: 1
[    15.027] 	MemoryModel: 6
[    15.027] 	BankSize: 0
[    15.027] 	NumberOfImages: 1
[    15.027] 	RedMaskSize: 8
[    15.027] 	RedFieldPosition: 16
[    15.027] 	GreenMaskSize: 8
[    15.027] 	GreenFieldPosition: 8
[    15.027] 	BlueMaskSize: 8
[    15.027] 	BlueFieldPosition: 0
[    15.027] 	RsvdMaskSize: 8
[    15.027] 	RsvdFieldPosition: 24
[    15.027] 	DirectColorModeInfo: 0
[    15.027] 	PhysBasePtr: 0xf1000000
[    15.027] 	LinBytesPerScanLine: 3200
[    15.027] 	BnkNumberOfImagePages: 1
[    15.027] 	LinNumberOfImagePages: 1
[    15.027] 	LinRedMaskSize: 8
[    15.027] 	LinRedFieldPosition: 16
[    15.027] 	LinGreenMaskSize: 8
[    15.028] 	LinGreenFieldPosition: 8
[    15.028] 	LinBlueMaskSize: 8
[    15.028] 	LinBlueFieldPosition: 0
[    15.028] 	LinRsvdMaskSize: 8
[    15.028] 	LinRsvdFieldPosition: 24
[    15.028] 	MaxPixelClock: 229500000
[    15.029] Mode: 117 (1024x768)
[    15.029] 	ModeAttributes: 0x3bf
[    15.029] 	WinAAttributes: 0x7
[    15.029] 	WinBAttributes: 0x0
[    15.029] 	WinGranularity: 64
[    15.029] 	WinSize: 64
[    15.029] 	WinASegment: 0xa000
[    15.029] 	WinBSegment: 0x0
[    15.029] 	WinFuncPtr: 0xc000791e
[    15.029] 	BytesPerScanline: 2048
[    15.029] 	XResolution: 1024
[    15.029] 	YResolution: 768
[    15.029] 	XCharSize: 8
[    15.029] 	YCharSize: 16
[    15.029] 	NumberOfPlanes: 1
[    15.029] 	BitsPerPixel: 16
[    15.029] 	NumberOfBanks: 1
[    15.029] 	MemoryModel: 6
[    15.029] 	BankSize: 0
[    15.029] 	NumberOfImages: 1
[    15.029] 	RedMaskSize: 5
[    15.029] 	RedFieldPosition: 11
[    15.029] 	GreenMaskSize: 6
[    15.029] 	GreenFieldPosition: 5
[    15.029] 	BlueMaskSize: 5
[    15.029] 	BlueFieldPosition: 0
[    15.029] 	RsvdMaskSize: 0
[    15.029] 	RsvdFieldPosition: 0
[    15.029] 	DirectColorModeInfo: 0
[    15.029] 	PhysBasePtr: 0xf1000000
[    15.029] 	LinBytesPerScanLine: 2048
[    15.029] 	BnkNumberOfImagePages: 1
[    15.029] 	LinNumberOfImagePages: 1
[    15.029] 	LinRedMaskSize: 5
[    15.029] 	LinRedFieldPosition: 11
[    15.029] 	LinGreenMaskSize: 6
[    15.029] 	LinGreenFieldPosition: 5
[    15.029] 	LinBlueMaskSize: 5
[    15.029] 	LinBlueFieldPosition: 0
[    15.029] 	LinRsvdMaskSize: 0
[    15.029] 	LinRsvdFieldPosition: 0
[    15.029] 	MaxPixelClock: 229500000
[    15.030] *Mode: 118 (1024x768)
[    15.030] 	ModeAttributes: 0x3bf
[    15.030] 	WinAAttributes: 0x7
[    15.030] 	WinBAttributes: 0x0
[    15.030] 	WinGranularity: 64
[    15.030] 	WinSize: 64
[    15.030] 	WinASegment: 0xa000
[    15.030] 	WinBSegment: 0x0
[    15.030] 	WinFuncPtr: 0xc000791e
[    15.030] 	BytesPerScanline: 4096
[    15.030] 	XResolution: 1024
[    15.030] 	YResolution: 768
[    15.030] 	XCharSize: 8
[    15.030] 	YCharSize: 16
[    15.030] 	NumberOfPlanes: 1
[    15.030] 	BitsPerPixel: 32
[    15.030] 	NumberOfBanks: 1
[    15.030] 	MemoryModel: 6
[    15.030] 	BankSize: 0
[    15.030] 	NumberOfImages: 1
[    15.030] 	RedMaskSize: 8
[    15.030] 	RedFieldPosition: 16
[    15.030] 	GreenMaskSize: 8
[    15.030] 	GreenFieldPosition: 8
[    15.030] 	BlueMaskSize: 8
[    15.030] 	BlueFieldPosition: 0
[    15.030] 	RsvdMaskSize: 8
[    15.030] 	RsvdFieldPosition: 24
[    15.030] 	DirectColorModeInfo: 0
[    15.030] 	PhysBasePtr: 0xf1000000
[    15.031] 	LinBytesPerScanLine: 4096
[    15.031] 	BnkNumberOfImagePages: 1
[    15.031] 	LinNumberOfImagePages: 1
[    15.031] 	LinRedMaskSize: 8
[    15.031] 	LinRedFieldPosition: 16
[    15.031] 	LinGreenMaskSize: 8
[    15.031] 	LinGreenFieldPosition: 8
[    15.031] 	LinBlueMaskSize: 8
[    15.031] 	LinBlueFieldPosition: 0
[    15.031] 	LinRsvdMaskSize: 8
[    15.031] 	LinRsvdFieldPosition: 24
[    15.031] 	MaxPixelClock: 229500000
[    15.032] Mode: 11a (1280x1024)
[    15.032] 	ModeAttributes: 0x3bf
[    15.032] 	WinAAttributes: 0x7
[    15.032] 	WinBAttributes: 0x0
[    15.032] 	WinGranularity: 64
[    15.032] 	WinSize: 64
[    15.032] 	WinASegment: 0xa000
[    15.032] 	WinBSegment: 0x0
[    15.032] 	WinFuncPtr: 0xc000791e
[    15.032] 	BytesPerScanline: 2560
[    15.032] 	XResolution: 1280
[    15.032] 	YResolution: 1024
[    15.032] 	XCharSize: 8
[    15.032] 	YCharSize: 16
[    15.032] 	NumberOfPlanes: 1
[    15.032] 	BitsPerPixel: 16
[    15.032] 	NumberOfBanks: 1
[    15.032] 	MemoryModel: 6
[    15.032] 	BankSize: 0
[    15.032] 	NumberOfImages: 1
[    15.032] 	RedMaskSize: 5
[    15.032] 	RedFieldPosition: 11
[    15.032] 	GreenMaskSize: 6
[    15.032] 	GreenFieldPosition: 5
[    15.032] 	BlueMaskSize: 5
[    15.032] 	BlueFieldPosition: 0
[    15.032] 	RsvdMaskSize: 0
[    15.032] 	RsvdFieldPosition: 0
[    15.032] 	DirectColorModeInfo: 0
[    15.032] 	PhysBasePtr: 0xf1000000
[    15.032] 	LinBytesPerScanLine: 2560
[    15.032] 	BnkNumberOfImagePages: 1
[    15.032] 	LinNumberOfImagePages: 1
[    15.032] 	LinRedMaskSize: 5
[    15.032] 	LinRedFieldPosition: 11
[    15.032] 	LinGreenMaskSize: 6
[    15.032] 	LinGreenFieldPosition: 5
[    15.032] 	LinBlueMaskSize: 5
[    15.032] 	LinBlueFieldPosition: 0
[    15.032] 	LinRsvdMaskSize: 0
[    15.032] 	LinRsvdFieldPosition: 0
[    15.032] 	MaxPixelClock: 229500000
[    15.033] *Mode: 11b (1280x1024)
[    15.033] 	ModeAttributes: 0x3bf
[    15.033] 	WinAAttributes: 0x7
[    15.033] 	WinBAttributes: 0x0
[    15.033] 	WinGranularity: 64
[    15.033] 	WinSize: 64
[    15.033] 	WinASegment: 0xa000
[    15.033] 	WinBSegment: 0x0
[    15.033] 	WinFuncPtr: 0xc000791e
[    15.033] 	BytesPerScanline: 5120
[    15.033] 	XResolution: 1280
[    15.033] 	YResolution: 1024
[    15.033] 	XCharSize: 8
[    15.033] 	YCharSize: 16
[    15.033] 	NumberOfPlanes: 1
[    15.033] 	BitsPerPixel: 32
[    15.033] 	NumberOfBanks: 1
[    15.033] 	MemoryModel: 6
[    15.033] 	BankSize: 0
[    15.033] 	NumberOfImages: 1
[    15.033] 	RedMaskSize: 8
[    15.033] 	RedFieldPosition: 16
[    15.034] 	GreenMaskSize: 8
[    15.034] 	GreenFieldPosition: 8
[    15.034] 	BlueMaskSize: 8
[    15.034] 	BlueFieldPosition: 0
[    15.034] 	RsvdMaskSize: 8
[    15.034] 	RsvdFieldPosition: 24
[    15.034] 	DirectColorModeInfo: 0
[    15.034] 	PhysBasePtr: 0xf1000000
[    15.034] 	LinBytesPerScanLine: 5120
[    15.034] 	BnkNumberOfImagePages: 1
[    15.034] 	LinNumberOfImagePages: 1
[    15.034] 	LinRedMaskSize: 8
[    15.034] 	LinRedFieldPosition: 16
[    15.034] 	LinGreenMaskSize: 8
[    15.034] 	LinGreenFieldPosition: 8
[    15.034] 	LinBlueMaskSize: 8
[    15.034] 	LinBlueFieldPosition: 0
[    15.034] 	LinRsvdMaskSize: 8
[    15.034] 	LinRsvdFieldPosition: 24
[    15.034] 	MaxPixelClock: 229500000
[    15.035] Mode: 130 (320x200)
[    15.035] 	ModeAttributes: 0x3bf
[    15.035] 	WinAAttributes: 0x7
[    15.035] 	WinBAttributes: 0x0
[    15.035] 	WinGranularity: 64
[    15.035] 	WinSize: 64
[    15.035] 	WinASegment: 0xa000
[    15.035] 	WinBSegment: 0x0
[    15.035] 	WinFuncPtr: 0xc000791e
[    15.035] 	BytesPerScanline: 320
[    15.035] 	XResolution: 320
[    15.035] 	YResolution: 200
[    15.035] 	XCharSize: 8
[    15.035] 	YCharSize: 8
[    15.035] 	NumberOfPlanes: 1
[    15.035] 	BitsPerPixel: 8
[    15.035] 	NumberOfBanks: 1
[    15.035] 	MemoryModel: 4
[    15.035] 	BankSize: 0
[    15.035] 	NumberOfImages: 62
[    15.035] 	RedMaskSize: 0
[    15.035] 	RedFieldPosition: 0
[    15.035] 	GreenMaskSize: 0
[    15.035] 	GreenFieldPosition: 0
[    15.035] 	BlueMaskSize: 0
[    15.035] 	BlueFieldPosition: 0
[    15.035] 	RsvdMaskSize: 0
[    15.035] 	RsvdFieldPosition: 0
[    15.035] 	DirectColorModeInfo: 0
[    15.035] 	PhysBasePtr: 0xf1000000
[    15.035] 	LinBytesPerScanLine: 320
[    15.035] 	BnkNumberOfImagePages: 62
[    15.035] 	LinNumberOfImagePages: 62
[    15.035] 	LinRedMaskSize: 0
[    15.035] 	LinRedFieldPosition: 0
[    15.035] 	LinGreenMaskSize: 0
[    15.035] 	LinGreenFieldPosition: 0
[    15.035] 	LinBlueMaskSize: 0
[    15.035] 	LinBlueFieldPosition: 0
[    15.035] 	LinRsvdMaskSize: 0
[    15.035] 	LinRsvdFieldPosition: 0
[    15.035] 	MaxPixelClock: 229500000
[    15.036] Mode: 131 (320x400)
[    15.036] 	ModeAttributes: 0x3bf
[    15.036] 	WinAAttributes: 0x7
[    15.036] 	WinBAttributes: 0x0
[    15.036] 	WinGranularity: 64
[    15.036] 	WinSize: 64
[    15.036] 	WinASegment: 0xa000
[    15.036] 	WinBSegment: 0x0
[    15.036] 	WinFuncPtr: 0xc000791e
[    15.036] 	BytesPerScanline: 320
[    15.036] 	XResolution: 320
[    15.036] 	YResolution: 400
[    15.036] 	XCharSize: 8
[    15.036] 	YCharSize: 16
[    15.036] 	NumberOfPlanes: 1
[    15.036] 	BitsPerPixel: 8
[    15.036] 	NumberOfBanks: 1
[    15.036] 	MemoryModel: 4
[    15.036] 	BankSize: 0
[    15.036] 	NumberOfImages: 30
[    15.036] 	RedMaskSize: 0
[    15.036] 	RedFieldPosition: 0
[    15.036] 	GreenMaskSize: 0
[    15.036] 	GreenFieldPosition: 0
[    15.036] 	BlueMaskSize: 0
[    15.036] 	BlueFieldPosition: 0
[    15.036] 	RsvdMaskSize: 0
[    15.036] 	RsvdFieldPosition: 0
[    15.036] 	DirectColorModeInfo: 0
[    15.036] 	PhysBasePtr: 0xf1000000
[    15.036] 	LinBytesPerScanLine: 320
[    15.036] 	BnkNumberOfImagePages: 30
[    15.036] 	LinNumberOfImagePages: 30
[    15.036] 	LinRedMaskSize: 0
[    15.037] 	LinRedFieldPosition: 0
[    15.037] 	LinGreenMaskSize: 0
[    15.037] 	LinGreenFieldPosition: 0
[    15.037] 	LinBlueMaskSize: 0
[    15.037] 	LinBlueFieldPosition: 0
[    15.037] 	LinRsvdMaskSize: 0
[    15.037] 	LinRsvdFieldPosition: 0
[    15.037] 	MaxPixelClock: 229500000
[    15.038] Mode: 132 (320x400)
[    15.038] 	ModeAttributes: 0x3bf
[    15.038] 	WinAAttributes: 0x7
[    15.038] 	WinBAttributes: 0x0
[    15.038] 	WinGranularity: 64
[    15.038] 	WinSize: 64
[    15.038] 	WinASegment: 0xa000
[    15.038] 	WinBSegment: 0x0
[    15.038] 	WinFuncPtr: 0xc000791e
[    15.038] 	BytesPerScanline: 640
[    15.038] 	XResolution: 320
[    15.038] 	YResolution: 400
[    15.038] 	XCharSize: 8
[    15.038] 	YCharSize: 16
[    15.038] 	NumberOfPlanes: 1
[    15.038] 	BitsPerPixel: 16
[    15.038] 	NumberOfBanks: 1
[    15.038] 	MemoryModel: 6
[    15.038] 	BankSize: 0
[    15.038] 	NumberOfImages: 14
[    15.038] 	RedMaskSize: 5
[    15.038] 	RedFieldPosition: 11
[    15.038] 	GreenMaskSize: 6
[    15.038] 	GreenFieldPosition: 5
[    15.038] 	BlueMaskSize: 5
[    15.038] 	BlueFieldPosition: 0
[    15.038] 	RsvdMaskSize: 0
[    15.038] 	RsvdFieldPosition: 0
[    15.038] 	DirectColorModeInfo: 0
[    15.038] 	PhysBasePtr: 0xf1000000
[    15.038] 	LinBytesPerScanLine: 640
[    15.038] 	BnkNumberOfImagePages: 14
[    15.038] 	LinNumberOfImagePages: 14
[    15.038] 	LinRedMaskSize: 5
[    15.038] 	LinRedFieldPosition: 11
[    15.038] 	LinGreenMaskSize: 6
[    15.038] 	LinGreenFieldPosition: 5
[    15.038] 	LinBlueMaskSize: 5
[    15.038] 	LinBlueFieldPosition: 0
[    15.038] 	LinRsvdMaskSize: 0
[    15.038] 	LinRsvdFieldPosition: 0
[    15.038] 	MaxPixelClock: 229500000
[    15.039] *Mode: 133 (320x400)
[    15.039] 	ModeAttributes: 0x3bf
[    15.039] 	WinAAttributes: 0x7
[    15.039] 	WinBAttributes: 0x0
[    15.039] 	WinGranularity: 64
[    15.039] 	WinSize: 64
[    15.039] 	WinASegment: 0xa000
[    15.039] 	WinBSegment: 0x0
[    15.039] 	WinFuncPtr: 0xc000791e
[    15.039] 	BytesPerScanline: 1280
[    15.039] 	XResolution: 320
[    15.039] 	YResolution: 400
[    15.039] 	XCharSize: 8
[    15.039] 	YCharSize: 16
[    15.039] 	NumberOfPlanes: 1
[    15.039] 	BitsPerPixel: 32
[    15.039] 	NumberOfBanks: 1
[    15.039] 	MemoryModel: 6
[    15.039] 	BankSize: 0
[    15.039] 	NumberOfImages: 6
[    15.039] 	RedMaskSize: 8
[    15.039] 	RedFieldPosition: 16
[    15.039] 	GreenMaskSize: 8
[    15.039] 	GreenFieldPosition: 8
[    15.039] 	BlueMaskSize: 8
[    15.039] 	BlueFieldPosition: 0
[    15.039] 	RsvdMaskSize: 8
[    15.039] 	RsvdFieldPosition: 24
[    15.039] 	DirectColorModeInfo: 0
[    15.039] 	PhysBasePtr: 0xf1000000
[    15.039] 	LinBytesPerScanLine: 1280
[    15.039] 	BnkNumberOfImagePages: 6
[    15.039] 	LinNumberOfImagePages: 6
[    15.039] 	LinRedMaskSize: 8
[    15.039] 	LinRedFieldPosition: 16
[    15.039] 	LinGreenMaskSize: 8
[    15.039] 	LinGreenFieldPosition: 8
[    15.039] 	LinBlueMaskSize: 8
[    15.039] 	LinBlueFieldPosition: 0
[    15.039] 	LinRsvdMaskSize: 8
[    15.039] 	LinRsvdFieldPosition: 24
[    15.039] 	MaxPixelClock: 229500000
[    15.041] Mode: 134 (320x240)
[    15.041] 	ModeAttributes: 0x3bf
[    15.041] 	WinAAttributes: 0x7
[    15.041] 	WinBAttributes: 0x0
[    15.041] 	WinGranularity: 64
[    15.041] 	WinSize: 64
[    15.041] 	WinASegment: 0xa000
[    15.041] 	WinBSegment: 0x0
[    15.041] 	WinFuncPtr: 0xc000791e
[    15.041] 	BytesPerScanline: 320
[    15.041] 	XResolution: 320
[    15.041] 	YResolution: 240
[    15.041] 	XCharSize: 8
[    15.041] 	YCharSize: 8
[    15.041] 	NumberOfPlanes: 1
[    15.041] 	BitsPerPixel: 8
[    15.041] 	NumberOfBanks: 1
[    15.041] 	MemoryModel: 4
[    15.041] 	BankSize: 0
[    15.041] 	NumberOfImages: 30
[    15.041] 	RedMaskSize: 0
[    15.041] 	RedFieldPosition: 0
[    15.041] 	GreenMaskSize: 0
[    15.041] 	GreenFieldPosition: 0
[    15.041] 	BlueMaskSize: 0
[    15.041] 	BlueFieldPosition: 0
[    15.041] 	RsvdMaskSize: 0
[    15.041] 	RsvdFieldPosition: 0
[    15.041] 	DirectColorModeInfo: 0
[    15.041] 	PhysBasePtr: 0xf1000000
[    15.041] 	LinBytesPerScanLine: 320
[    15.041] 	BnkNumberOfImagePages: 30
[    15.041] 	LinNumberOfImagePages: 30
[    15.041] 	LinRedMaskSize: 0
[    15.041] 	LinRedFieldPosition: 0
[    15.041] 	LinGreenMaskSize: 0
[    15.041] 	LinGreenFieldPosition: 0
[    15.041] 	LinBlueMaskSize: 0
[    15.041] 	LinBlueFieldPosition: 0
[    15.041] 	LinRsvdMaskSize: 0
[    15.041] 	LinRsvdFieldPosition: 0
[    15.041] 	MaxPixelClock: 229500000
[    15.042] Mode: 135 (320x240)
[    15.042] 	ModeAttributes: 0x3bf
[    15.042] 	WinAAttributes: 0x7
[    15.042] 	WinBAttributes: 0x0
[    15.042] 	WinGranularity: 64
[    15.042] 	WinSize: 64
[    15.042] 	WinASegment: 0xa000
[    15.042] 	WinBSegment: 0x0
[    15.042] 	WinFuncPtr: 0xc000791e
[    15.042] 	BytesPerScanline: 640
[    15.042] 	XResolution: 320
[    15.042] 	YResolution: 240
[    15.042] 	XCharSize: 8
[    15.042] 	YCharSize: 8
[    15.042] 	NumberOfPlanes: 1
[    15.042] 	BitsPerPixel: 16
[    15.042] 	NumberOfBanks: 1
[    15.042] 	MemoryModel: 6
[    15.042] 	BankSize: 0
[    15.042] 	NumberOfImages: 19
[    15.042] 	RedMaskSize: 5
[    15.042] 	RedFieldPosition: 11
[    15.042] 	GreenMaskSize: 6
[    15.042] 	GreenFieldPosition: 5
[    15.042] 	BlueMaskSize: 5
[    15.042] 	BlueFieldPosition: 0
[    15.042] 	RsvdMaskSize: 0
[    15.042] 	RsvdFieldPosition: 0
[    15.042] 	DirectColorModeInfo: 0
[    15.042] 	PhysBasePtr: 0xf1000000
[    15.042] 	LinBytesPerScanLine: 640
[    15.042] 	BnkNumberOfImagePages: 19
[    15.042] 	LinNumberOfImagePages: 19
[    15.042] 	LinRedMaskSize: 5
[    15.042] 	LinRedFieldPosition: 11
[    15.042] 	LinGreenMaskSize: 6
[    15.042] 	LinGreenFieldPosition: 5
[    15.042] 	LinBlueMaskSize: 5
[    15.042] 	LinBlueFieldPosition: 0
[    15.042] 	LinRsvdMaskSize: 0
[    15.042] 	LinRsvdFieldPosition: 0
[    15.042] 	MaxPixelClock: 229500000
[    15.044] *Mode: 136 (320x240)
[    15.044] 	ModeAttributes: 0x3bf
[    15.044] 	WinAAttributes: 0x7
[    15.044] 	WinBAttributes: 0x0
[    15.044] 	WinGranularity: 64
[    15.044] 	WinSize: 64
[    15.044] 	WinASegment: 0xa000
[    15.044] 	WinBSegment: 0x0
[    15.044] 	WinFuncPtr: 0xc000791e
[    15.044] 	BytesPerScanline: 1280
[    15.044] 	XResolution: 320
[    15.044] 	YResolution: 240
[    15.044] 	XCharSize: 8
[    15.044] 	YCharSize: 8
[    15.044] 	NumberOfPlanes: 1
[    15.044] 	BitsPerPixel: 32
[    15.044] 	NumberOfBanks: 1
[    15.044] 	MemoryModel: 6
[    15.044] 	BankSize: 0
[    15.044] 	NumberOfImages: 10
[    15.044] 	RedMaskSize: 8
[    15.044] 	RedFieldPosition: 16
[    15.044] 	GreenMaskSize: 8
[    15.044] 	GreenFieldPosition: 8
[    15.044] 	BlueMaskSize: 8
[    15.044] 	BlueFieldPosition: 0
[    15.044] 	RsvdMaskSize: 8
[    15.044] 	RsvdFieldPosition: 24
[    15.044] 	DirectColorModeInfo: 0
[    15.044] 	PhysBasePtr: 0xf1000000
[    15.044] 	LinBytesPerScanLine: 1280
[    15.044] 	BnkNumberOfImagePages: 10
[    15.044] 	LinNumberOfImagePages: 10
[    15.044] 	LinRedMaskSize: 8
[    15.044] 	LinRedFieldPosition: 16
[    15.044] 	LinGreenMaskSize: 8
[    15.044] 	LinGreenFieldPosition: 8
[    15.044] 	LinBlueMaskSize: 8
[    15.044] 	LinBlueFieldPosition: 0
[    15.044] 	LinRsvdMaskSize: 8
[    15.044] 	LinRsvdFieldPosition: 24
[    15.044] 	MaxPixelClock: 229500000
[    15.045] Mode: 13d (640x400)
[    15.045] 	ModeAttributes: 0x3bf
[    15.045] 	WinAAttributes: 0x7
[    15.045] 	WinBAttributes: 0x0
[    15.045] 	WinGranularity: 64
[    15.045] 	WinSize: 64
[    15.045] 	WinASegment: 0xa000
[    15.045] 	WinBSegment: 0x0
[    15.045] 	WinFuncPtr: 0xc000791e
[    15.045] 	BytesPerScanline: 1280
[    15.045] 	XResolution: 640
[    15.045] 	YResolution: 400
[    15.045] 	XCharSize: 8
[    15.045] 	YCharSize: 16
[    15.045] 	NumberOfPlanes: 1
[    15.045] 	BitsPerPixel: 16
[    15.045] 	NumberOfBanks: 1
[    15.045] 	MemoryModel: 6
[    15.045] 	BankSize: 0
[    15.045] 	NumberOfImages: 6
[    15.045] 	RedMaskSize: 5
[    15.045] 	RedFieldPosition: 11
[    15.045] 	GreenMaskSize: 6
[    15.045] 	GreenFieldPosition: 5
[    15.045] 	BlueMaskSize: 5
[    15.045] 	BlueFieldPosition: 0
[    15.045] 	RsvdMaskSize: 0
[    15.045] 	RsvdFieldPosition: 0
[    15.045] 	DirectColorModeInfo: 0
[    15.045] 	PhysBasePtr: 0xf1000000
[    15.045] 	LinBytesPerScanLine: 1280
[    15.045] 	BnkNumberOfImagePages: 6
[    15.045] 	LinNumberOfImagePages: 6
[    15.045] 	LinRedMaskSize: 5
[    15.045] 	LinRedFieldPosition: 11
[    15.045] 	LinGreenMaskSize: 6
[    15.045] 	LinGreenFieldPosition: 5
[    15.045] 	LinBlueMaskSize: 5
[    15.045] 	LinBlueFieldPosition: 0
[    15.045] 	LinRsvdMaskSize: 0
[    15.045] 	LinRsvdFieldPosition: 0
[    15.045] 	MaxPixelClock: 229500000
[    15.047] *Mode: 13e (640x400)
[    15.047] 	ModeAttributes: 0x3bf
[    15.047] 	WinAAttributes: 0x7
[    15.047] 	WinBAttributes: 0x0
[    15.047] 	WinGranularity: 64
[    15.047] 	WinSize: 64
[    15.047] 	WinASegment: 0xa000
[    15.047] 	WinBSegment: 0x0
[    15.047] 	WinFuncPtr: 0xc000791e
[    15.047] 	BytesPerScanline: 2560
[    15.047] 	XResolution: 640
[    15.047] 	YResolution: 400
[    15.047] 	XCharSize: 8
[    15.047] 	YCharSize: 16
[    15.047] 	NumberOfPlanes: 1
[    15.047] 	BitsPerPixel: 32
[    15.047] 	NumberOfBanks: 1
[    15.047] 	MemoryModel: 6
[    15.047] 	BankSize: 0
[    15.047] 	NumberOfImages: 2
[    15.047] 	RedMaskSize: 8
[    15.047] 	RedFieldPosition: 16
[    15.047] 	GreenMaskSize: 8
[    15.047] 	GreenFieldPosition: 8
[    15.047] 	BlueMaskSize: 8
[    15.047] 	BlueFieldPosition: 0
[    15.047] 	RsvdMaskSize: 8
[    15.047] 	RsvdFieldPosition: 24
[    15.047] 	DirectColorModeInfo: 0
[    15.047] 	PhysBasePtr: 0xf1000000
[    15.047] 	LinBytesPerScanLine: 2560
[    15.047] 	BnkNumberOfImagePages: 2
[    15.047] 	LinNumberOfImagePages: 2
[    15.047] 	LinRedMaskSize: 8
[    15.047] 	LinRedFieldPosition: 16
[    15.047] 	LinGreenMaskSize: 8
[    15.047] 	LinGreenFieldPosition: 8
[    15.047] 	LinBlueMaskSize: 8
[    15.047] 	LinBlueFieldPosition: 0
[    15.047] 	LinRsvdMaskSize: 8
[    15.047] 	LinRsvdFieldPosition: 24
[    15.047] 	MaxPixelClock: 229500000
[    15.048] Mode: 160 (1280x800)
[    15.048] 	ModeAttributes: 0x3bf
[    15.048] 	WinAAttributes: 0x7
[    15.048] 	WinBAttributes: 0x0
[    15.048] 	WinGranularity: 64
[    15.048] 	WinSize: 64
[    15.048] 	WinASegment: 0xa000
[    15.048] 	WinBSegment: 0x0
[    15.048] 	WinFuncPtr: 0xc000791e
[    15.048] 	BytesPerScanline: 1280
[    15.048] 	XResolution: 1280
[    15.048] 	YResolution: 800
[    15.048] 	XCharSize: 8
[    15.048] 	YCharSize: 16
[    15.048] 	NumberOfPlanes: 1
[    15.048] 	BitsPerPixel: 8
[    15.048] 	NumberOfBanks: 1
[    15.048] 	MemoryModel: 4
[    15.048] 	BankSize: 0
[    15.048] 	NumberOfImages: 2
[    15.048] 	RedMaskSize: 0
[    15.048] 	RedFieldPosition: 0
[    15.048] 	GreenMaskSize: 0
[    15.048] 	GreenFieldPosition: 0
[    15.048] 	BlueMaskSize: 0
[    15.048] 	BlueFieldPosition: 0
[    15.048] 	RsvdMaskSize: 0
[    15.048] 	RsvdFieldPosition: 0
[    15.048] 	DirectColorModeInfo: 0
[    15.048] 	PhysBasePtr: 0xf1000000
[    15.048] 	LinBytesPerScanLine: 1280
[    15.048] 	BnkNumberOfImagePages: 2
[    15.048] 	LinNumberOfImagePages: 2
[    15.048] 	LinRedMaskSize: 0
[    15.048] 	LinRedFieldPosition: 0
[    15.048] 	LinGreenMaskSize: 0
[    15.048] 	LinGreenFieldPosition: 0
[    15.048] 	LinBlueMaskSize: 0
[    15.048] 	LinBlueFieldPosition: 0
[    15.048] 	LinRsvdMaskSize: 0
[    15.048] 	LinRsvdFieldPosition: 0
[    15.048] 	MaxPixelClock: 229500000
[    15.050] *Mode: 161 (1280x800)
[    15.050] 	ModeAttributes: 0x3bf
[    15.050] 	WinAAttributes: 0x7
[    15.050] 	WinBAttributes: 0x0
[    15.050] 	WinGranularity: 64
[    15.050] 	WinSize: 64
[    15.050] 	WinASegment: 0xa000
[    15.050] 	WinBSegment: 0x0
[    15.050] 	WinFuncPtr: 0xc000791e
[    15.050] 	BytesPerScanline: 5120
[    15.050] 	XResolution: 1280
[    15.050] 	YResolution: 800
[    15.050] 	XCharSize: 8
[    15.050] 	YCharSize: 16
[    15.050] 	NumberOfPlanes: 1
[    15.050] 	BitsPerPixel: 32
[    15.050] 	NumberOfBanks: 1
[    15.050] 	MemoryModel: 6
[    15.050] 	BankSize: 0
[    15.050] 	NumberOfImages: 1
[    15.050] 	RedMaskSize: 8
[    15.050] 	RedFieldPosition: 16
[    15.050] 	GreenMaskSize: 8
[    15.050] 	GreenFieldPosition: 8
[    15.050] 	BlueMaskSize: 8
[    15.050] 	BlueFieldPosition: 0
[    15.050] 	RsvdMaskSize: 8
[    15.050] 	RsvdFieldPosition: 24
[    15.050] 	DirectColorModeInfo: 0
[    15.050] 	PhysBasePtr: 0xf1000000
[    15.050] 	LinBytesPerScanLine: 5120
[    15.050] 	BnkNumberOfImagePages: 1
[    15.050] 	LinNumberOfImagePages: 1
[    15.050] 	LinRedMaskSize: 8
[    15.050] 	LinRedFieldPosition: 16
[    15.050] 	LinGreenMaskSize: 8
[    15.050] 	LinGreenFieldPosition: 8
[    15.050] 	LinBlueMaskSize: 8
[    15.050] 	LinBlueFieldPosition: 0
[    15.050] 	LinRsvdMaskSize: 8
[    15.050] 	LinRsvdFieldPosition: 24
[    15.050] 	MaxPixelClock: 229500000
[    15.050] 
[    15.050] (II) VESA(0): Total Memory: 224 64KB banks (14336kB)
[    15.050] (II) VESA(0): <default monitor>: Using hsync range of 30.00-83.00 kHz
[    15.050] (II) VESA(0): <default monitor>: Using vrefresh range of 50.00-76.00 Hz
[    15.050] (II) VESA(0): <default monitor>: Using maximum pixel clock of 175.00 MHz
[    15.050] (WW) VESA(0): Unable to estimate virtual size
[    15.051] (II) VESA(0): Not using built-in mode "1280x800" (no mode of this name)
[    15.052] (II) VESA(0): Not using built-in mode "640x400" (no mode of this name)
[    15.052] (II) VESA(0): Not using built-in mode "320x400" (no mode of this name)
[    15.052] (II) VESA(0): Not using built-in mode "320x240" (no mode of this name)
[    15.052] (II) VESA(0): Not using built-in mode "320x200" (no mode of this name)
[    15.052] (--) VESA(0): Virtual size is 1280x1024 (pitch 1280)
[    15.052] (**) VESA(0): *Built-in mode "1280x1024"
[    15.052] (**) VESA(0): *Built-in mode "1024x768"
[    15.052] (**) VESA(0): *Built-in mode "800x600"
[    15.052] (**) VESA(0): *Built-in mode "640x480"
[    15.052] (**) VESA(0): Display dimensions: (480, 270) mm
[    15.052] (**) VESA(0): DPI set to (67, 96)
[    15.052] (**) VESA(0): Using "Shadow Framebuffer"
[    15.052] (II) Loading sub module "shadow"
[    15.052] (II) LoadModule: "shadow"
[    15.052] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    15.053] (II) Module shadow: vendor="X.Org Foundation"
[    15.053] 	compiled for 1.13.0, module version = 1.1.0
[    15.053] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    15.053] (II) Loading sub module "fb"
[    15.053] (II) LoadModule: "fb"
[    15.053] (II) Loading /usr/lib/xorg/modules/libfb.so
[    15.053] (II) Module fb: vendor="X.Org Foundation"
[    15.053] 	compiled for 1.13.0, module version = 1.0.0
[    15.053] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    15.053] (II) UnloadModule: "modesetting"
[    15.053] (II) Unloading modesetting
[    15.053] (II) UnloadModule: "fbdev"
[    15.053] (II) Unloading fbdev
[    15.053] (II) UnloadSubModule: "fbdevhw"
[    15.053] (II) Unloading fbdevhw
[    15.053] (==) Depth 24 pixmap format is 32 bpp
[    15.053] (II) Loading sub module "int10"
[    15.053] (II) LoadModule: "int10"
[    15.053] (II) Loading /usr/lib/xorg/modules/libint10.so
[    15.053] (II) Module int10: vendor="X.Org Foundation"
[    15.053] 	compiled for 1.13.0, module version = 1.0.0
[    15.053] 	ABI class: X.Org Video Driver, version 13.0
[    15.053] (II) VESA(0): initializing int10
[    15.053] (II) VESA(0): Bad V_BIOS checksum
[    15.053] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    15.105] (II) VESA(0): VESA BIOS detected
[    15.105] (II) VESA(0): VESA VBE Version 3.0
[    15.105] (II) VESA(0): VESA VBE Total Mem: 14336 kB
[    15.105] (II) VESA(0): VESA VBE OEM: NVIDIA
[    15.105] (II) VESA(0): VESA VBE OEM Software Rev: 112.36
[    15.105] (II) VESA(0): VESA VBE OEM Vendor: NVIDIA Corporation
[    15.105] (II) VESA(0): VESA VBE OEM Product: GF104B Board - 10400050
[    15.105] (II) VESA(0): VESA VBE OEM Product Rev: Chip Rev   
[    15.105] (II) VESA(0): virtual address = 0x7f9c07609000,
	physical address = 0xf1000000, size = 14680064
[    15.133] (II) VESA(0): Setting up VESA Mode 0x11B (1280x1024)
[    15.247] (==) VESA(0): Default visual is TrueColor
[    15.247] (==) VESA(0): Backing store disabled
[    15.247] (==) VESA(0): DPMS enabled
[    15.247] (==) RandR enabled
[    15.255] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
[    15.260] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    15.262] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    15.262] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    15.262] (II) LoadModule: "evdev"
[    15.262] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    15.262] (II) Module evdev: vendor="X.Org Foundation"
[    15.262] 	compiled for 1.13.0, module version = 2.7.3
[    15.262] 	Module class: X.Org XInput Driver
[    15.262] 	ABI class: X.Org XInput driver, version 18.0
[    15.262] (II) Using input driver 'evdev' for 'Power Button'
[    15.262] (**) Power Button: always reports core events
[    15.262] (**) evdev: Power Button: Device: "/dev/input/event1"
[    15.262] (--) evdev: Power Button: Vendor 0 Product 0x1
[    15.262] (--) evdev: Power Button: Found keys
[    15.262] (II) evdev: Power Button: Configuring as keyboard
[    15.262] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    15.262] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    15.262] (**) Option "xkb_rules" "evdev"
[    15.262] (**) Option "xkb_model" "pc105"
[    15.262] (**) Option "xkb_layout" "us"
[    15.263] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    15.263] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    15.263] (II) Using input driver 'evdev' for 'Power Button'
[    15.263] (**) Power Button: always reports core events
[    15.263] (**) evdev: Power Button: Device: "/dev/input/event0"
[    15.263] (--) evdev: Power Button: Vendor 0 Product 0x1
[    15.263] (--) evdev: Power Button: Found keys
[    15.263] (II) evdev: Power Button: Configuring as keyboard
[    15.263] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    15.263] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    15.263] (**) Option "xkb_rules" "evdev"
[    15.263] (**) Option "xkb_model" "pc105"
[    15.263] (**) Option "xkb_layout" "us"
[    15.263] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=9 (/dev/input/event10)
[    15.263] (II) No input driver specified, ignoring this device.
[    15.263] (II) This device may have been added with another device file.
[    15.263] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event11)
[    15.263] (II) No input driver specified, ignoring this device.
[    15.263] (II) This device may have been added with another device file.
[    15.263] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event12)
[    15.263] (II) No input driver specified, ignoring this device.
[    15.263] (II) This device may have been added with another device file.
[    15.263] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event13)
[    15.263] (II) No input driver specified, ignoring this device.
[    15.263] (II) This device may have been added with another device file.
[    15.264] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event5)
[    15.264] (II) No input driver specified, ignoring this device.
[    15.264] (II) This device may have been added with another device file.
[    15.264] (II) config/udev: Adding input device HDA Intel PCH Front Mic (/dev/input/event6)
[    15.264] (II) No input driver specified, ignoring this device.
[    15.264] (II) This device may have been added with another device file.
[    15.264] (II) config/udev: Adding input device HDA Intel PCH Rear Mic (/dev/input/event7)
[    15.264] (II) No input driver specified, ignoring this device.
[    15.264] (II) This device may have been added with another device file.
[    15.264] (II) config/udev: Adding input device HDA Intel PCH Front Headphone (/dev/input/event8)
[    15.264] (II) No input driver specified, ignoring this device.
[    15.264] (II) This device may have been added with another device file.
[    15.264] (II) config/udev: Adding input device HDA Intel PCH Line Out (/dev/input/event9)
[    15.264] (II) No input driver specified, ignoring this device.
[    15.264] (II) This device may have been added with another device file.
[    15.264] (II) config/udev: Adding input device Logitech USB Laser Mouse (/dev/input/event3)
[    15.264] (**) Logitech USB Laser Mouse: Applying InputClass "evdev pointer catchall"
[    15.264] (II) Using input driver 'evdev' for 'Logitech USB Laser Mouse'
[    15.264] (**) Logitech USB Laser Mouse: always reports core events
[    15.264] (**) evdev: Logitech USB Laser Mouse: Device: "/dev/input/event3"
[    15.264] (--) evdev: Logitech USB Laser Mouse: Vendor 0x46d Product 0xc069
[    15.264] (--) evdev: Logitech USB Laser Mouse: Found 12 mouse buttons
[    15.264] (--) evdev: Logitech USB Laser Mouse: Found scroll wheel(s)
[    15.264] (--) evdev: Logitech USB Laser Mouse: Found relative axes
[    15.264] (--) evdev: Logitech USB Laser Mouse: Found x and y relative axes
[    15.264] (II) evdev: Logitech USB Laser Mouse: Configuring as mouse
[    15.264] (II) evdev: Logitech USB Laser Mouse: Adding scrollwheel support
[    15.264] (**) evdev: Logitech USB Laser Mouse: YAxisMapping: buttons 4 and 5
[    15.264] (**) evdev: Logitech USB Laser Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    15.264] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.0/input/input3/event3"
[    15.264] (II) XINPUT: Adding extended input device "Logitech USB Laser Mouse" (type: MOUSE, id 8)
[    15.264] (II) evdev: Logitech USB Laser Mouse: initialized for relative axes.
[    15.264] (**) Logitech USB Laser Mouse: (accel) keeping acceleration scheme 1
[    15.265] (**) Logitech USB Laser Mouse: (accel) acceleration profile 0
[    15.265] (**) Logitech USB Laser Mouse: (accel) acceleration factor: 2.000
[    15.265] (**) Logitech USB Laser Mouse: (accel) acceleration threshold: 4
[    15.265] (II) config/udev: Adding input device Logitech USB Laser Mouse (/dev/input/mouse0)
[    15.265] (II) No input driver specified, ignoring this device.
[    15.265] (II) This device may have been added with another device file.
[    15.265] (II) config/udev: Adding input device Eee PC WMI hotkeys (/dev/input/event4)
[    15.265] (**) Eee PC WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    15.265] (II) Using input driver 'evdev' for 'Eee PC WMI hotkeys'
[    15.265] (**) Eee PC WMI hotkeys: always reports core events
[    15.265] (**) evdev: Eee PC WMI hotkeys: Device: "/dev/input/event4"
[    15.265] (--) evdev: Eee PC WMI hotkeys: Vendor 0 Product 0
[    15.265] (--) evdev: Eee PC WMI hotkeys: Found keys
[    15.265] (II) evdev: Eee PC WMI hotkeys: Configuring as keyboard
[    15.265] (**) Option "config_info" "udev:/sys/devices/platform/eeepc-wmi/input/input4/event4"
[    15.265] (II) XINPUT: Adding extended input device "Eee PC WMI hotkeys" (type: KEYBOARD, id 9)
[    15.265] (**) Option "xkb_rules" "evdev"
[    15.265] (**) Option "xkb_model" "pc105"
[    15.265] (**) Option "xkb_layout" "us"
[    15.265] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    15.265] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    15.265] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    15.265] (**) AT Translated Set 2 keyboard: always reports core events
[    15.265] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    15.265] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    15.265] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    15.265] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    15.265] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    15.265] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 10)
[    15.265] (**) Option "xkb_rules" "evdev"
[    15.265] (**) Option "xkb_model" "pc105"
[    15.265] (**) Option "xkb_layout" "us"

```

---

### Post by mc4man on 2012-12-30
Totally remove whatever nvidia- package you now have installed.
Then
```
sudo apt-get install linux-headers-generic
```
When that finishes you can install the nvidia- of your choice & the module will build successfully

info
[http://ubuntuforums.org/showpost.php?p=12304169&postcount=3](http://ubuntuforums.org/showpost.php?p=12304169&postcount=3)

---

### Post by bitwaba on 2012-12-30
You are a great and wise person :)

Worked like a charm. Thanks!

---

