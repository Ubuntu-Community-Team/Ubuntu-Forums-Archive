---
title: "X Error of failed request:  BadRequest (invalid request code or no such operation)"
date: 2013-08-20
forum: Hardware
---

### Post by hailholyghost on 2013-08-20
Hello,

I am trying to run PyMol on Ubuntu 13.04.

However, I get this error:

```
con@con-Inspiron-3521:~$ pymol 
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  22
  Current serial number in output stream:  22
 PyMOL: abrupt program termination.
```

I have found numerous people who have had similar problems ([http://askubuntu.com/questions/175744/x-error-of-failed-request-badrequest-invalid-request-code-or-no-such-operation](http://askubuntu.com/questions/175744/x-error-of-failed-request-badrequest-invalid-request-code-or-no-such-operation) and others)

However, these solutions don't apply for this computer because this has an Intel driver, not ATI or AMD:

```

con@con-Inspiron-3521:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)

```

I also ran here [https://01.org/linuxgraphics/downloads](https://01.org/linuxgraphics/downloads) but after downloading all of these updates, nothing came of it.

Also this solution found here [http://ubuntuforums.org/showthread.php?t=1906654&p=11600468#post11600468](http://ubuntuforums.org/showthread.php?t=1906654&p=11600468#post11600468) did not work:

```
 $ sudo update-alternatives --config x86_64-linux-gnu_gl_conf
$ sudo apt-get install --reinstall libgl1-mesa-dri libgl1-mesa-glx
$ sudo ldconfig 
```

Does anyone know how to fix this?

---

### Post by Yellow Pasque on 2013-08-20
Can you show /var/log/Xorg.0.log (and use the code tags because it's long)?

---

### Post by hailholyghost on 2013-08-20
Hi Temüjin,

thanks for your reply, here it is

```
[    25.921] 
X.Org X Server 1.13.3
Release Date: 2013-03-07
[    25.921] X Protocol Version 11, Revision 0
[    25.921] Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
[    25.921] Current Operating System: Linux con-Inspiron-3521 3.8.0-29-generic #42-Ubuntu SMP Tue Aug 13 19:40:39 UTC 2013 x86_64
[    25.921] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-29-generic root=UUID=317a936b-589f-426a-a4f6-f0bb721604cc ro quiet splash vt.handoff=7
[    25.921] Build Date: 17 April 2013  10:43:13PM
[    25.921] xorg-server 2:1.13.3-0ubuntu6 (For technical support please see http://www.ubuntu.com/support) 
[    25.921] Current version of pixman: 0.28.2
[    25.921] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    25.921] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    25.921] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Aug 20 16:29:57 2013
[    25.961] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    25.962] (==) No Layout section.  Using the first Screen section.
[    25.962] (==) No screen section available. Using defaults.
[    25.962] (**) |-->Screen "Default Screen Section" (0)
[    25.962] (**) |   |-->Monitor "<default monitor>"
[    25.962] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    25.962] (==) Automatically adding devices
[    25.962] (==) Automatically enabling devices
[    25.962] (==) Automatically adding GPU devices
[    25.962] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    25.962] 	Entry deleted from font path.
[    25.962] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    25.962] 	Entry deleted from font path.
[    25.962] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    25.962] 	Entry deleted from font path.
[    25.962] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    25.962] 	Entry deleted from font path.
[    25.962] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	built-ins
[    25.962] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    25.962] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    25.962] (II) Loader magic: 0x7f01c30e3d20
[    25.962] (II) Module ABI versions:
[    25.962] 	X.Org ANSI C Emulation: 0.4
[    25.962] 	X.Org Video Driver: 13.1
[    25.962] 	X.Org XInput driver : 18.0
[    25.962] 	X.Org Server Extension : 7.0
[    25.962] (II) config/udev: Adding drm device (/dev/dri/card0)
[    25.963] (--) PCI:*(0:0:2:0) 8086:0166:1028:0597 rev 9, Mem @ 0xc0000000/4194304, 0xb0000000/268435456, I/O @ 0x00003000/64
[    25.963] (II) Open ACPI successful (/var/run/acpid.socket)
[    25.964] Initializing built-in extension Generic Event Extension
[    25.964] Initializing built-in extension SHAPE
[    25.964] Initializing built-in extension MIT-SHM
[    25.964] Initializing built-in extension XInputExtension
[    25.964] Initializing built-in extension XTEST
[    25.964] Initializing built-in extension BIG-REQUESTS
[    25.964] Initializing built-in extension SYNC
[    25.964] Initializing built-in extension XKEYBOARD
[    25.964] Initializing built-in extension XC-MISC
[    25.964] Initializing built-in extension SECURITY
[    25.964] Initializing built-in extension XINERAMA
[    25.964] Initializing built-in extension XFIXES
[    25.964] Initializing built-in extension RENDER
[    25.964] Initializing built-in extension RANDR
[    25.964] Initializing built-in extension COMPOSITE
[    25.964] Initializing built-in extension DAMAGE
[    25.964] Initializing built-in extension MIT-SCREEN-SAVER
[    25.964] Initializing built-in extension DOUBLE-BUFFER
[    25.964] Initializing built-in extension RECORD
[    25.964] Initializing built-in extension DPMS
[    25.964] Initializing built-in extension X-Resource
[    25.964] Initializing built-in extension XVideo
[    25.964] Initializing built-in extension XVideo-MotionCompensation
[    25.964] Initializing built-in extension SELinux
[    25.964] Initializing built-in extension XFree86-VidModeExtension
[    25.964] Initializing built-in extension XFree86-DGA
[    25.964] Initializing built-in extension XFree86-DRI
[    25.964] Initializing built-in extension DRI2
[    25.964] (II) LoadModule: "glx"
[    26.030] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    26.065] (II) Module glx: vendor="X.Org Foundation"
[    26.065] 	compiled for 1.13.3, module version = 1.0.0
[    26.065] 	ABI class: X.Org Server Extension, version 7.0
[    26.065] (==) AIGLX enabled
[    26.065] Loading extension GLX
[    26.065] (==) Matched intel as autoconfigured driver 0
[    26.065] (==) Matched intel as autoconfigured driver 1
[    26.065] (==) Matched vesa as autoconfigured driver 2
[    26.065] (==) Matched modesetting as autoconfigured driver 3
[    26.065] (==) Matched fbdev as autoconfigured driver 4
[    26.066] (==) Assigned the driver to the xf86ConfigLayout
[    26.066] (II) LoadModule: "intel"
[    26.066] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    26.202] (II) Module intel: vendor="X.Org Foundation"
[    26.203] 	compiled for 1.13.3, module version = 2.21.9
[    26.203] 	Module class: X.Org Video Driver
[    26.203] 	ABI class: X.Org Video Driver, version 13.1
[    26.203] (II) LoadModule: "vesa"
[    26.203] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    26.203] (II) Module vesa: vendor="X.Org Foundation"
[    26.203] 	compiled for 1.12.99.902, module version = 2.3.2
[    26.203] 	Module class: X.Org Video Driver
[    26.203] 	ABI class: X.Org Video Driver, version 13.0
[    26.203] (II) LoadModule: "modesetting"
[    26.203] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    26.203] (II) Module modesetting: vendor="X.Org Foundation"
[    26.203] 	compiled for 1.13.3, module version = 0.7.0
[    26.203] 	Module class: X.Org Video Driver
[    26.203] 	ABI class: X.Org Video Driver, version 13.1
[    26.203] (II) LoadModule: "fbdev"
[    26.203] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    26.203] (II) Module fbdev: vendor="X.Org Foundation"
[    26.203] 	compiled for 1.12.99.902, module version = 0.4.3
[    26.203] 	Module class: X.Org Video Driver
[    26.203] 	ABI class: X.Org Video Driver, version 13.0
[    26.203] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
	Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
	Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
	Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
	Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server,
	Ivybridge Server (GT2), HD Graphics, HD Graphics 4600,
	Haswell Desktop (GT3), HD Graphics, HD Graphics 4600,
	Haswell Mobile (GT3), HD Graphics, HD Graphics P4600/P4700,
	Haswell Server (GT3), Haswell (GT1), Haswell (GT2), Haswell (GT3),
	HD Graphics, Haswell (GT2), Haswell (GT3), Haswell SDV Desktop (GT1),
	Haswell SDV Desktop (GT2), Haswell SDV Desktop (GT3),
	Haswell SDV Mobile (GT1), Haswell SDV Mobile (GT2),
	Haswell SDV Mobile (GT3), Haswell SDV Server (GT1),
	Haswell SDV Server (GT2), Haswell SDV Server (GT3),
	Haswell SDV (GT1), Haswell SDV (GT2), Haswell SDV (GT3),
	Haswell SDV (GT1), Haswell SDV (GT2), Haswell SDV (GT3),
	Haswell ULT Desktop (GT1), Haswell ULT Desktop (GT2),
	Iris(TM) Graphics 5100, HD Graphics, HD Graphics 4400,
	HD Graphics 5000, Haswell ULT Server (GT1), Haswell ULT Server (GT2),
	Iris(TM) Graphics 5100, Haswell ULT (GT1), Haswell ULT (GT2),
	Iris(TM) Graphics 5100, HD Graphics, HD Graphics 4200,
	Iris(TM) Graphics 5100, Haswell CRW Desktop (GT1), HD Graphics 4600,
	Iris(TM) Pro Graphics 5200, Haswell CRW Mobile (GT1),
	HD Graphics 4600, Iris(TM) Pro Graphics 5200,
	Haswell CRW Server (GT1), Haswell CRW Server (GT2),
	Iris(TM) Pro Graphics 5200, Haswell CRW (GT1), Haswell CRW (GT2),
	Iris(TM) Pro Graphics 5200, Haswell CRW (GT1), Haswell CRW (GT2),
	Iris(TM) Pro Graphics 5200, ValleyView PO board
[    26.204] (II) VESA: driver for VESA chipsets: vesa
[    26.204] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    26.204] (II) FBDEV: driver for framebuffer: fbdev
[    26.204] (++) using VT number 7

[    26.206] (WW) Falling back to old probe method for vesa
[    26.207] (WW) Falling back to old probe method for modesetting
[    26.207] (WW) Falling back to old probe method for fbdev
[    26.207] (II) Loading sub module "fbdevhw"
[    26.207] (II) LoadModule: "fbdevhw"
[    26.207] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    26.207] (II) Module fbdevhw: vendor="X.Org Foundation"
[    26.207] 	compiled for 1.13.3, module version = 0.0.2
[    26.207] 	ABI class: X.Org Video Driver, version 13.1
[    26.207] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    26.207] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    26.207] (==) intel(0): RGB weight 888
[    26.207] (==) intel(0): Default visual is TrueColor
[    26.207] (--) intel(0): Integrated Graphics Chipset: Intel(R) Ivybridge Mobile (GT2)
[    26.224] (**) intel(0): Relaxed fencing enabled
[    26.224] (**) intel(0): Wait on SwapBuffers? enabled
[    26.224] (**) intel(0): Triple buffering? enabled
[    26.224] (**) intel(0): Framebuffer tiled
[    26.224] (**) intel(0): Pixmaps tiled
[    26.224] (**) intel(0): 3D buffers tiled
[    26.224] (**) intel(0): SwapBuffers wait enabled
[    26.224] (==) intel(0): video overlay key set to 0x101fe
[    26.224] (II) intel(0): Output LVDS1 has no monitor section
[    26.224] (--) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
[    26.256] (II) intel(0): Output VGA1 has no monitor section
[    26.256] (II) intel(0): Output HDMI1 has no monitor section
[    26.256] (II) intel(0): Output DP1 has no monitor section
[    26.256] (II) intel(0): EDID for output LVDS1
[    26.256] (II) intel(0): Manufacturer: LGD  Model: 3ab  Serial#: 0
[    26.256] (II) intel(0): Year: 2012  Week: 0
[    26.256] (II) intel(0): EDID Version: 1.4
[    26.256] (II) intel(0): Digital Display Input
[    26.256] (II) intel(0): 6 bits per channel
[    26.256] (II) intel(0): Digital interface is undefined
[    26.256] (II) intel(0): Max Image Size [cm]: horiz.: 34  vert.: 19
[    26.256] (II) intel(0): Gamma: 2.20
[    26.256] (II) intel(0): No DPMS capabilities specified
[    26.256] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    26.256] (II) intel(0): First detailed timing is preferred mode
[    26.256] (II) intel(0): Preferred mode is native pixel format and refresh rate
[    26.256] (II) intel(0): redX: 0.578 redY: 0.344   greenX: 0.337 greenY: 0.571
[    26.256] (II) intel(0): blueX: 0.159 blueY: 0.120   whiteX: 0.313 whiteY: 0.329
[    26.256] (II) intel(0): Manufacturer's mask: 0
[    26.256] (II) intel(0): Supported detailed timing:
[    26.256] (II) intel(0): clock: 76.8 MHz   Image Size:  344 x 194 mm
[    26.256] (II) intel(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1618 h_border: 0
[    26.256] (II) intel(0): v_active: 768  v_sync: 771  v_sync_end 776 v_blanking: 790 v_border: 0
[    26.256] (II) intel(0): Supported detailed timing:
[    26.256] (II) intel(0): clock: 51.2 MHz   Image Size:  344 x 194 mm
[    26.256] (II) intel(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1618 h_border: 0
[    26.256] (II) intel(0): v_active: 768  v_sync: 771  v_sync_end 776 v_blanking: 790 v_border: 0
[    26.256] (II) intel(0):  N3KMP\80156WH3
[    26.256] (II) intel(0): Unknown vendor-specific block 0
[    26.256] (II) intel(0): EDID (in hex):
[    26.256] (II) intel(0): 	00ffffffffffff0030e4ab0300000000
[    26.256] (II) intel(0): 	00160104902213780a05f59458569228
[    26.256] (II) intel(0): 	1e505400000001010101010101010101
[    26.256] (II) intel(0): 	010101010101fb1d56fc500016303020
[    26.256] (II) intel(0): 	350058c21000001afc1356fc50001630
[    26.256] (II) intel(0): 	3020350058c21000001a000000fe004e
[    26.256] (II) intel(0): 	334b4d50803135365748330a00000000
[    26.256] (II) intel(0): 	00004131940010000001010a202000d0
[    26.256] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    26.256] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    26.256] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    26.256] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    26.256] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    26.256] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    26.256] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    26.256] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    26.256] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    26.256] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    26.256] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    26.256] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    26.256] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    26.256] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    26.256] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    26.256] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    26.256] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    26.256] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    26.256] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    26.256] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    26.256] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    26.256] (II) intel(0): Printing probed modes for output LVDS1
[    26.256] (II) intel(0): Modeline "1366x768"x60.0   76.75  1366 1414 1446 1618  768 771 776 790 +hsync -vsync (47.4 kHz eP)
[    26.256] (II) intel(0): Modeline "1366x768"x40.0   51.16  1366 1414 1446 1618  768 771 776 790 +hsync -vsync (31.6 kHz e)
[    26.256] (II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz d)
[    26.256] (II) intel(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz d)
[    26.256] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz d)
[    26.256] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz d)
[    26.256] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz d)
[    26.256] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz d)
[    26.288] (II) intel(0): EDID for output VGA1
[    26.288] (II) intel(0): EDID for output HDMI1
[    26.288] (II) intel(0): EDID for output DP1
[    26.288] (II) intel(0): Output LVDS1 connected
[    26.288] (II) intel(0): Output VGA1 disconnected
[    26.288] (II) intel(0): Output HDMI1 disconnected
[    26.288] (II) intel(0): Output DP1 disconnected
[    26.288] (II) intel(0): Using exact sizes for initial modes
[    26.288] (II) intel(0): Output LVDS1 using initial mode 1366x768
[    26.288] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    26.288] (II) intel(0): Kernel page flipping support detected, enabling
[    26.288] (==) intel(0): DPI set to (96, 96)
[    26.288] (II) Loading sub module "fb"
[    26.288] (II) LoadModule: "fb"
[    26.288] (II) Loading /usr/lib/xorg/modules/libfb.so
[    26.434] (II) Module fb: vendor="X.Org Foundation"
[    26.434] 	compiled for 1.13.3, module version = 1.0.0
[    26.434] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    26.434] (II) Loading sub module "dri2"
[    26.434] (II) LoadModule: "dri2"
[    26.434] (II) Module "dri2" already built-in
[    26.434] (II) UnloadModule: "vesa"
[    26.434] (II) Unloading vesa
[    26.434] (II) UnloadModule: "modesetting"
[    26.434] (II) Unloading modesetting
[    26.434] (II) UnloadModule: "fbdev"
[    26.434] (II) Unloading fbdev
[    26.434] (II) UnloadSubModule: "fbdevhw"
[    26.434] (II) Unloading fbdevhw
[    26.434] (==) Depth 24 pixmap format is 32 bpp
[    26.434] (II) intel(0): [DRI2] Setup complete
[    26.434] (II) intel(0): [DRI2]   DRI driver: i965
[    26.434] (II) intel(0): Allocated new frame buffer 1408x768 stride 5632, tiled
[    26.435] (II) UXA(0): Driver registered support for the following operations:
[    26.435] (II)         solid
[    26.435] (II)         copy
[    26.435] (II)         composite (RENDER acceleration)
[    26.435] (II)         put_image
[    26.435] (II)         get_image
[    26.435] (==) intel(0): Backing store disabled
[    26.435] (==) intel(0): Silken mouse enabled
[    26.435] (II) intel(0): Initializing HW Cursor
[    26.435] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    26.435] (==) intel(0): DPMS enabled
[    26.435] (==) intel(0): Intel XvMC decoder enabled
[    26.435] (II) intel(0): Set up textured video
[    26.435] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[    26.435] (II) intel(0): direct rendering: DRI2 Enabled
[    26.435] (==) intel(0): hotplug detection: "enabled"
[    26.452] (--) RandR disabled
[    26.455] (II) SELinux: Disabled on system
[    27.112] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    27.112] (II) AIGLX: enabled GLX_INTEL_swap_event
[    27.112] (II) AIGLX: enabled GLX_ARB_create_context
[    27.112] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    27.112] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    27.112] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    27.113] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    27.113] (II) AIGLX: Loaded and initialized i965
[    27.113] (II) GLX: Initialized DRI2 GL provider for screen 0
[    27.113] (II) intel(0): Setting screen physical size to 361 x 203
[    27.120] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    27.122] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    27.122] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    27.122] (II) LoadModule: "evdev"
[    27.122] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    27.129] (II) Module evdev: vendor="X.Org Foundation"
[    27.129] 	compiled for 1.13.3, module version = 2.7.3
[    27.129] 	Module class: X.Org XInput Driver
[    27.129] 	ABI class: X.Org XInput driver, version 18.0
[    27.129] (II) Using input driver 'evdev' for 'Power Button'
[    27.129] (**) Power Button: always reports core events
[    27.129] (**) evdev: Power Button: Device: "/dev/input/event2"
[    27.130] (--) evdev: Power Button: Vendor 0 Product 0x1
[    27.130] (--) evdev: Power Button: Found keys
[    27.130] (II) evdev: Power Button: Configuring as keyboard
[    27.130] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    27.130] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    27.130] (**) Option "xkb_rules" "evdev"
[    27.130] (**) Option "xkb_model" "pc105"
[    27.130] (**) Option "xkb_layout" "us"
[    27.130] (II) config/udev: Adding input device Video Bus (/dev/input/event10)
[    27.130] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    27.130] (II) Using input driver 'evdev' for 'Video Bus'
[    27.130] (**) Video Bus: always reports core events
[    27.130] (**) evdev: Video Bus: Device: "/dev/input/event10"
[    27.130] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    27.130] (--) evdev: Video Bus: Found keys
[    27.130] (II) evdev: Video Bus: Configuring as keyboard
[    27.130] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input10/event10"
[    27.130] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    27.130] (**) Option "xkb_rules" "evdev"
[    27.130] (**) Option "xkb_model" "pc105"
[    27.130] (**) Option "xkb_layout" "us"
[    27.131] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    27.131] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    27.131] (II) Using input driver 'evdev' for 'Power Button'
[    27.131] (**) Power Button: always reports core events
[    27.131] (**) evdev: Power Button: Device: "/dev/input/event0"
[    27.131] (--) evdev: Power Button: Vendor 0 Product 0x1
[    27.131] (--) evdev: Power Button: Found keys
[    27.131] (II) evdev: Power Button: Configuring as keyboard
[    27.131] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0C:00/input/input0/event0"
[    27.131] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    27.131] (**) Option "xkb_rules" "evdev"
[    27.131] (**) Option "xkb_model" "pc105"
[    27.131] (**) Option "xkb_layout" "us"
[    27.131] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[    27.131] (II) No input driver specified, ignoring this device.
[    27.131] (II) This device may have been added with another device file.
[    27.131] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:02.0/drm/card0
[    27.131] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    27.131] (II) config/udev: Adding input device NOVATEK USB Keyboard (/dev/input/event4)
[    27.131] (**) NOVATEK USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    27.131] (II) Using input driver 'evdev' for 'NOVATEK USB Keyboard'
[    27.131] (**) NOVATEK USB Keyboard: always reports core events
[    27.131] (**) evdev: NOVATEK USB Keyboard: Device: "/dev/input/event4"
[    27.131] (--) evdev: NOVATEK USB Keyboard: Vendor 0x461 Product 0x10
[    27.131] (--) evdev: NOVATEK USB Keyboard: Found keys
[    27.131] (II) evdev: NOVATEK USB Keyboard: Configuring as keyboard
[    27.131] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-3/3-3:1.0/input/input4/event4"
[    27.131] (II) XINPUT: Adding extended input device "NOVATEK USB Keyboard" (type: KEYBOARD, id 9)
[    27.131] (**) Option "xkb_rules" "evdev"
[    27.131] (**) Option "xkb_model" "pc105"
[    27.131] (**) Option "xkb_layout" "us"
[    27.132] (II) config/udev: Adding input device NOVATEK USB Keyboard (/dev/input/event5)
[    27.132] (**) NOVATEK USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    27.132] (II) Using input driver 'evdev' for 'NOVATEK USB Keyboard'
[    27.132] (**) NOVATEK USB Keyboard: always reports core events
[    27.132] (**) evdev: NOVATEK USB Keyboard: Device: "/dev/input/event5"
[    27.132] (--) evdev: NOVATEK USB Keyboard: Vendor 0x461 Product 0x10
[    27.132] (--) evdev: NOVATEK USB Keyboard: Found keys
[    27.132] (II) evdev: NOVATEK USB Keyboard: Configuring as keyboard
[    27.132] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-3/3-3:1.1/input/input5/event5"
[    27.132] (II) XINPUT: Adding extended input device "NOVATEK USB Keyboard" (type: KEYBOARD, id 10)
[    27.132] (**) Option "xkb_rules" "evdev"
[    27.132] (**) Option "xkb_model" "pc105"
[    27.132] (**) Option "xkb_layout" "us"
[    27.132] (II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/event6)
[    27.132] (**) Logitech USB-PS/2 Optical Mouse: Applying InputClass "evdev pointer catchall"
[    27.132] (II) Using input driver 'evdev' for 'Logitech USB-PS/2 Optical Mouse'
[    27.132] (**) Logitech USB-PS/2 Optical Mouse: always reports core events
[    27.132] (**) evdev: Logitech USB-PS/2 Optical Mouse: Device: "/dev/input/event6"
[    27.132] (--) evdev: Logitech USB-PS/2 Optical Mouse: Vendor 0x46d Product 0xc01b
[    27.132] (--) evdev: Logitech USB-PS/2 Optical Mouse: Found 10 mouse buttons
[    27.132] (--) evdev: Logitech USB-PS/2 Optical Mouse: Found scroll wheel(s)
[    27.132] (--) evdev: Logitech USB-PS/2 Optical Mouse: Found relative axes
[    27.132] (--) evdev: Logitech USB-PS/2 Optical Mouse: Found x and y relative axes
[    27.132] (II) evdev: Logitech USB-PS/2 Optical Mouse: Configuring as mouse
[    27.132] (II) evdev: Logitech USB-PS/2 Optical Mouse: Adding scrollwheel support
[    27.132] (**) evdev: Logitech USB-PS/2 Optical Mouse: YAxisMapping: buttons 4 and 5
[    27.132] (**) evdev: Logitech USB-PS/2 Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    27.132] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-4/3-4:1.0/input/input6/event6"
[    27.132] (II) XINPUT: Adding extended input device "Logitech USB-PS/2 Optical Mouse" (type: MOUSE, id 11)
[    27.132] (II) evdev: Logitech USB-PS/2 Optical Mouse: initialized for relative axes.
[    27.132] (**) Logitech USB-PS/2 Optical Mouse: (accel) keeping acceleration scheme 1
[    27.132] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration profile 0
[    27.132] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration factor: 2.000
[    27.132] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration threshold: 4
[    27.133] (II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/mouse0)
[    27.133] (II) No input driver specified, ignoring this device.
[    27.133] (II) This device may have been added with another device file.
[    27.133] (II) config/udev: Adding input device Laptop_Integrated_Webcam_HD (/dev/input/event8)
[    27.133] (**) Laptop_Integrated_Webcam_HD: Applying InputClass "evdev keyboard catchall"
[    27.133] (II) Using input driver 'evdev' for 'Laptop_Integrated_Webcam_HD'
[    27.133] (**) Laptop_Integrated_Webcam_HD: always reports core events
[    27.133] (**) evdev: Laptop_Integrated_Webcam_HD: Device: "/dev/input/event8"
[    27.133] (--) evdev: Laptop_Integrated_Webcam_HD: Vendor 0xc45 Product 0x64ad
[    27.133] (--) evdev: Laptop_Integrated_Webcam_HD: Found keys
[    27.133] (II) evdev: Laptop_Integrated_Webcam_HD: Configuring as keyboard
[    27.133] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input8/event8"
[    27.133] (II) XINPUT: Adding extended input device "Laptop_Integrated_Webcam_HD" (type: KEYBOARD, id 12)
[    27.133] (**) Option "xkb_rules" "evdev"
[    27.133] (**) Option "xkb_model" "pc105"
[    27.133] (**) Option "xkb_layout" "us"
[    27.133] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event11)
[    27.133] (II) No input driver specified, ignoring this device.
[    27.133] (II) This device may have been added with another device file.
[    27.133] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event12)
[    27.133] (II) No input driver specified, ignoring this device.
[    27.133] (II) This device may have been added with another device file.
[    27.133] (II) config/udev: Adding input device HDA Intel PCH Front Headphone (/dev/input/event13)
[    27.134] (II) No input driver specified, ignoring this device.
[    27.134] (II) This device may have been added with another device file.
[    27.134] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    27.134] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    27.134] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    27.134] (**) AT Translated Set 2 keyboard: always reports core events
[    27.134] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    27.134] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    27.134] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    27.134] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    27.134] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    27.134] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 13)
[    27.134] (**) Option "xkb_rules" "evdev"
[    27.134] (**) Option "xkb_model" "pc105"
[    27.134] (**) Option "xkb_layout" "us"
[    27.134] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event9)
[    27.134] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    27.134] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    27.134] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[    27.134] (II) LoadModule: "synaptics"
[    27.134] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    27.134] (II) Module synaptics: vendor="X.Org Foundation"
[    27.134] 	compiled for 1.13.1.901, module version = 1.6.2
[    27.134] 	Module class: X.Org XInput Driver
[    27.134] 	ABI class: X.Org XInput driver, version 18.0
[    27.134] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    27.134] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    27.134] (**) Option "Device" "/dev/input/event9"
[    27.161] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5674
[    27.161] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4754
[    27.161] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    27.161] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    27.161] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    27.161] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    27.161] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    27.161] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    27.161] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input9/event9"
[    27.161] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 14)
[    27.161] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    27.161] (**) synaptics: SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[    27.161] (**) synaptics: SynPS/2 Synaptics TouchPad: AccelFactor is now 0.037
[    27.162] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    27.162] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    27.162] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    27.162] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    27.162] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    27.162] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
[    27.162] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    27.163] (II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event7)
[    27.163] (**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    27.163] (II) Using input driver 'evdev' for 'Dell WMI hotkeys'
[    27.163] (**) Dell WMI hotkeys: always reports core events
[    27.163] (**) evdev: Dell WMI hotkeys: Device: "/dev/input/event7"
[    27.163] (--) evdev: Dell WMI hotkeys: Vendor 0 Product 0
[    27.163] (--) evdev: Dell WMI hotkeys: Found keys
[    27.163] (II) evdev: Dell WMI hotkeys: Configuring as keyboard
[    27.163] (**) Option "config_info" "udev:/sys/devices/virtual/input/input7/event7"
[    27.163] (II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD, id 15)
[    27.163] (**) Option "xkb_rules" "evdev"
[    27.163] (**) Option "xkb_model" "pc105"
[    27.163] (**) Option "xkb_layout" "us"
[    29.139] (II) intel(0): EDID vendor "LGD", prod id 939
[    29.139] (II) intel(0): Printing DDC gathered Modelines:
[    29.139] (II) intel(0): Modeline "1366x768"x0.0   76.75  1366 1414 1446 1618  768 771 776 790 +hsync -vsync (47.4 kHz eP)
[    29.139] (II) intel(0): Modeline "1366x768"x0.0   51.16  1366 1414 1446 1618  768 771 776 790 +hsync -vsync (31.6 kHz e)
[    30.345] (II) intel(0): EDID vendor "LGD", prod id 939
[    30.345] (II) intel(0): Printing DDC gathered Modelines:
[    30.345] (II) intel(0): Modeline "1366x768"x0.0   76.75  1366 1414 1446 1618  768 771 776 790 +hsync -vsync (47.4 kHz eP)
[    30.345] (II) intel(0): Modeline "1366x768"x0.0   51.16  1366 1414 1446 1618  768 771 776 790 +hsync -vsync (31.6 kHz e)
[    51.925] (II) intel(0): EDID vendor "LGD", prod id 939
[    51.925] (II) intel(0): Printing DDC gathered Modelines:
[    51.925] (II) intel(0): Modeline "1366x768"x0.0   76.75  1366 1414 1446 1618  768 771 776 790 +hsync -vsync (47.4 kHz eP)
[    51.925] (II) intel(0): Modeline "1366x768"x0.0   51.16  1366 1414 1446 1618  768 771 776 790 +hsync -vsync (31.6 kHz e)
[    52.155] (II) intel(0): EDID vendor "LGD", prod id 939
[    52.155] (II) intel(0): Printing DDC gathered Modelines:
[    52.155] (II) intel(0): Modeline "1366x768"x0.0   76.75  1366 1414 1446 1618  768 771 776 790 +hsync -vsync (47.4 kHz eP)
[    52.155] (II) intel(0): Modeline "1366x768"x0.0   51.16  1366 1414 1446 1618  768 771 776 790 +hsync -vsync (31.6 kHz e)
[    52.438] (II) XKB: reuse xkmfile /var/lib/xkb/server-8C3648A5FD728529D869F46730BE1BC287DB231C.xkm
[    73.485] (II) intel(0): EDID vendor "LGD", prod id 939
[    73.485] (II) intel(0): Printing DDC gathered Modelines:
[    73.485] (II) intel(0): Modeline "1366x768"x0.0   76.75  1366 1414 1446 1618  768 771 776 790 +hsync -vsync (47.4 kHz eP)
[    73.485] (II) intel(0): Modeline "1366x768"x0.0   51.16  1366 1414 1446 1618  768 771 776 790 +hsync -vsync (31.6 kHz e)
```

---

### Post by Yellow Pasque on 2013-08-21
The log looks good. I'm thinking the issue is with pymol. I tried running it in my Raring VM, and it was okay.

---

### Post by hailholyghost on 2013-08-23
For reasons I do not know, this error is no longer present and I can use PyMol.

Thanks for your help, though!

-Dave

---

