---
title: "Video not working correctly with Matrox card after upgrade"
date: 2012-01-22
forum: Hardware
---

### Post by mo-seph on 2012-01-22
Hi,

I've got a Matrox my Linux box, which worked fine under Karmic:

```

>lspci | grep VGA
01:08.0 VGA compatible controller: Matrox Graphics, Inc. MGA 2064W [Millennium] (rev 01)
```

Now under Oneiric, it can't use the full resolution, the display is really slow, and changing the bitdepth makes it either all black with a pointer, or I get little areas drawn randomly across the screen.

To make it work at all, I've change my xorg.conf, and added a default depth of 16:
```

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth 16
EndSection

```

My /var/log/xorg.0.log is below. It's complaining about memory, but I've had this card working at 1650x1050 in the past with no problems.

Any help appreciated!

```
[403882.693] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[403882.693] X Protocol Version 11, Revision 0
[403882.693] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[403882.694] Current Operating System: Linux moominmamma 3.0.0-14-generic-pae #23-Ubuntu SMP Mon Nov 21 22:07:10 UTC 2011 i686
[403882.694] Kernel command line: root=UUID=46312f9a-e030-4326-9af8-8d8f47783ef7 ro quiet splash 
[403882.694] Build Date: 19 October 2011  05:09:41AM
[403882.694] xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see http://www.ubuntu.com/support) 
[403882.694] Current version of pixman: 0.22.2
[403882.694] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[403882.694] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[403882.694] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Jan 22 12:37:09 2012
[403882.694] (==) Using config file: "/etc/X11/xorg.conf"
[403882.694] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[403882.695] (==) ServerLayout "Default Layout"
[403882.695] (**) |-->Screen "Default Screen" (0)
[403882.695] (**) |   |-->Monitor "Configured Monitor"
[403882.696] (**) |   |-->Device "Configured Video Device"
[403882.696] (==) Automatically adding devices
[403882.696] (==) Automatically enabling devices
[403882.696] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[403882.696] 	Entry deleted from font path.
[403882.696] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[403882.696] 	Entry deleted from font path.
[403882.696] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[403882.696] 	Entry deleted from font path.
[403882.696] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[403882.696] 	Entry deleted from font path.
[403882.696] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[403882.696] 	Entry deleted from font path.
[403882.696] (WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
[403882.696] 	Entry deleted from font path.
[403882.696] 	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType").
[403882.696] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[403882.696] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[403882.696] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[403882.696] (II) Loader magic: 0x823ada0
[403882.696] (II) Module ABI versions:
[403882.697] 	X.Org ANSI C Emulation: 0.4
[403882.697] 	X.Org Video Driver: 10.0
[403882.697] 	X.Org XInput driver : 12.3
[403882.697] 	X.Org Server Extension : 5.0
[403882.698] (--) PCI:*(0:1:8:0) 102b:0519:0000:0000 rev 1, Mem @ 0xfeafc000/16384, 0xfd800000/8388608, BIOS @ 0x????????/65536
[403882.698] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[403882.698] (II) LoadModule: "extmod"
[403882.699] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[403882.699] (II) Module extmod: vendor="X.Org Foundation"
[403882.699] 	compiled for 1.10.4, module version = 1.0.0
[403882.699] 	Module class: X.Org Server Extension
[403882.699] 	ABI class: X.Org Server Extension, version 5.0
[403882.700] (II) Loading extension MIT-SCREEN-SAVER
[403882.700] (II) Loading extension XFree86-VidModeExtension
[403882.700] (II) Loading extension XFree86-DGA
[403882.700] (II) Loading extension DPMS
[403882.700] (II) Loading extension XVideo
[403882.700] (II) Loading extension XVideo-MotionCompensation
[403882.700] (II) Loading extension X-Resource
[403882.700] (II) LoadModule: "dbe"
[403882.700] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[403882.700] (II) Module dbe: vendor="X.Org Foundation"
[403882.700] 	compiled for 1.10.4, module version = 1.0.0
[403882.700] 	Module class: X.Org Server Extension
[403882.701] 	ABI class: X.Org Server Extension, version 5.0
[403882.701] (II) Loading extension DOUBLE-BUFFER
[403882.701] (II) LoadModule: "glx"
[403882.701] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[403882.701] (II) Module glx: vendor="X.Org Foundation"
[403882.701] 	compiled for 1.10.4, module version = 1.0.0
[403882.701] 	ABI class: X.Org Server Extension, version 5.0
[403882.702] (==) AIGLX enabled
[403882.702] (II) Loading extension GLX
[403882.702] (II) LoadModule: "record"
[403882.702] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[403882.702] (II) Module record: vendor="X.Org Foundation"
[403882.702] 	compiled for 1.10.4, module version = 1.13.0
[403882.702] 	Module class: X.Org Server Extension
[403882.702] 	ABI class: X.Org Server Extension, version 5.0
[403882.702] (II) Loading extension RECORD
[403882.702] (II) LoadModule: "dri"
[403882.703] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[403882.703] (II) Module dri: vendor="X.Org Foundation"
[403882.703] 	compiled for 1.10.4, module version = 1.0.0
[403882.703] 	ABI class: X.Org Server Extension, version 5.0
[403882.703] (II) Loading extension XFree86-DRI
[403882.704] (II) LoadModule: "dri2"
[403882.704] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[403882.704] (II) Module dri2: vendor="X.Org Foundation"
[403882.704] 	compiled for 1.10.4, module version = 1.2.0
[403882.705] 	ABI class: X.Org Server Extension, version 5.0
[403882.705] (II) Loading extension DRI2
[403882.705] (==) Matched mga as autoconfigured driver 0
[403882.705] (==) Matched vesa as autoconfigured driver 1
[403882.705] (==) Matched fbdev as autoconfigured driver 2
[403882.705] (==) Assigned the driver to the xf86ConfigLayout
[403882.705] (II) LoadModule: "mga"
[403882.706] (II) Loading /usr/lib/xorg/modules/drivers/mga_drv.so
[403882.706] (II) Module mga: vendor="X.Org Foundation"
[403882.706] 	compiled for 1.10.0, module version = 1.4.13
[403882.706] 	Module class: X.Org Video Driver
[403882.706] 	ABI class: X.Org Video Driver, version 10.0
[403882.706] (II) LoadModule: "vesa"
[403882.707] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[403882.707] (II) Module vesa: vendor="X.Org Foundation"
[403882.707] 	compiled for 1.10.2, module version = 2.3.0
[403882.707] 	Module class: X.Org Video Driver
[403882.707] 	ABI class: X.Org Video Driver, version 10.0
[403882.707] (II) LoadModule: "fbdev"
[403882.708] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[403882.708] (II) Module fbdev: vendor="X.Org Foundation"
[403882.708] 	compiled for 1.10.0, module version = 0.4.2
[403882.708] 	ABI class: X.Org Video Driver, version 10.0
[403882.708] (II) MGA: driver for Matrox chipsets: mga2064w, mga1064sg, mga2164w,
	mga2164w AGP, mgag100, mgag100 PCI, mgag200, mgag200 PCI,
	mgag200 SE A PCI, mgag200 SE B PCI, mgag200 EV Maxim,
	mgag200 ER SH7757, mgag200 eW Nuvoton, mgag200eH, mgag400, mgag550
[403882.709] (II) VESA: driver for VESA chipsets: vesa
[403882.709] (II) FBDEV: driver for framebuffer: fbdev
[403882.709] (--) using VT number 8

[403882.715] (II) Loading /usr/lib/xorg/modules/drivers/mga_drv.so
[403882.715] (WW) Falling back to old probe method for vesa
[403882.715] (WW) Falling back to old probe method for fbdev
[403882.715] (II) Loading sub module "fbdevhw"
[403882.715] (II) LoadModule: "fbdevhw"
[403882.715] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[403882.715] (II) Module fbdevhw: vendor="X.Org Foundation"
[403882.715] 	compiled for 1.10.4, module version = 0.0.2
[403882.715] 	ABI class: X.Org Video Driver, version 10.0
[403882.715] (EE) open /dev/fb0: No such file or directory
[403882.715] (II) Loading sub module "vgahw"
[403882.715] (II) LoadModule: "vgahw"
[403882.715] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[403882.716] (II) Module vgahw: vendor="X.Org Foundation"
[403882.716] 	compiled for 1.10.4, module version = 0.1.0
[403882.716] 	ABI class: X.Org Video Driver, version 10.0
[403882.716] (--) MGA(0): Chipset: "mga2064w"
[403882.716] (--) MGA(0): Linear framebuffer at 0xFD800000
[403882.716] (--) MGA(0): MMIO registers at 0xFEAFC000
[403882.717] (II) MGA(0): MAPPED Framebuffer FD800000 800000 to FFFFFFFFB6ACA000.
[403882.717] (II) MGA(0): UNMAPPING framebuffer 0xFFFFFFFFB6ACA000, 0x800000.
[403882.718] (II) MGA(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 16/16
[403882.718] (**) MGA(0): Depth 16, (--) framebuffer bpp 16
[403882.718] (==) MGA(0): RGB weight 565
[403882.718] (==) MGA(0): Using AGP 1x mode
[403882.718] (==) MGA(0): Using HW cursor
[403882.718] (==) MGA(0): Using XAA acceleration
[403882.719] (--) MGA(0): Video BIOS info block at offset 0x07BC0
[403882.719] (==) MGA(0): VideoRAM: 2048 kByte
[403882.719] (II) Loading sub module "ddc"
[403882.719] (II) LoadModule: "ddc"
[403882.719] (II) Module "ddc" already built-in
[403882.719] (II) Loading sub module "i2c"
[403882.719] (II) LoadModule: "i2c"
[403882.719] (II) Module "i2c" already built-in
[403882.719] (II) MGA(0): MAPPED Framebuffer FD800000 200000 to FFFFFFFFB70CA000.
[403882.719] (II) MGA(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
[403882.720] (II) MGA(0): I2C bus "DDC" initialized.
[403882.720] (II) MGA(0): I2C device "DDC:ddc2" registered at address 0xA0.
[403882.790] (II) MGA(0): I2C monitor info
[403882.790] (II) MGA(0): Manufacturer: GSM  Model: 566a  Serial#: 113178
[403882.791] (II) MGA(0): Year: 2007  Week: 6
[403882.791] (II) MGA(0): EDID Version: 1.3
[403882.791] (II) MGA(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[403882.791] (II) MGA(0): Sync:  Separate  SyncOnGreen
[403882.791] (II) MGA(0): Max Image Size [cm]: horiz.: 49  vert.: 32
[403882.791] (II) MGA(0): Gamma: 2.20
[403882.791] (II) MGA(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[403882.791] (II) MGA(0): First detailed timing is preferred mode
[403882.791] (II) MGA(0): redX: 0.635 redY: 0.342   greenX: 0.292 greenY: 0.611
[403882.791] (II) MGA(0): blueX: 0.147 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
[403882.791] (II) MGA(0): Supported established timings:
[403882.791] (II) MGA(0): 720x400@70Hz
[403882.791] (II) MGA(0): 640x480@60Hz
[403882.791] (II) MGA(0): 640x480@75Hz
[403882.791] (II) MGA(0): 800x600@56Hz
[403882.791] (II) MGA(0): 800x600@60Hz
[403882.791] (II) MGA(0): 800x600@75Hz
[403882.791] (II) MGA(0): 832x624@75Hz
[403882.791] (II) MGA(0): 1024x768@60Hz
[403882.791] (II) MGA(0): 1024x768@75Hz
[403882.791] (II) MGA(0): 1280x1024@75Hz
[403882.791] (II) MGA(0): 1152x864@75Hz
[403882.791] (II) MGA(0): Manufacturer's mask: 0
[403882.791] (II) MGA(0): Supported standard timings:
[403882.791] (II) MGA(0): #0: hsize: 1440  vsize 900  refresh: 75  vid: 3989
[403882.791] (II) MGA(0): #1: hsize: 1440  vsize 900  refresh: 60  vid: 149
[403882.791] (II) MGA(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[403882.791] (II) MGA(0): #3: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[403882.791] (II) MGA(0): #4: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[403882.791] (II) MGA(0): Supported detailed timing:
[403882.791] (II) MGA(0): clock: 119.0 MHz   Image Size:  474 x 296 mm
[403882.791] (II) MGA(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
[403882.791] (II) MGA(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
[403882.791] (II) MGA(0): Supported detailed timing:
[403882.791] (II) MGA(0): clock: 146.2 MHz   Image Size:  474 x 296 mm
[403882.791] (II) MGA(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
[403882.791] (II) MGA(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
[403882.791] (II) MGA(0): Ranges: V min: 56 V max: 75 Hz, H min: 28 H max: 83 kHz, PixClock max 155 MHz
[403882.791] (II) MGA(0): Monitor name: L226W
[403882.791] (II) MGA(0): EDID (in hex):
[403882.791] (II) MGA(0): 	00ffffffffffff001e6d6a561aba0100
[403882.791] (II) MGA(0): 	061101036a312078eaaec5a2574a9c25
[403882.791] (II) MGA(0): 	125054a76b80950f950081808140714f
[403882.791] (II) MGA(0): 	0101010101017c2e90a0601a1e403020
[403882.791] (II) MGA(0): 	3600da281100001a21399030621a2740
[403882.791] (II) MGA(0): 	68b03600da281100001c000000fd0038
[403882.791] (II) MGA(0): 	4b1c530f000a202020202020000000fc
[403882.791] (II) MGA(0): 	004c323236570a202020202020200064
[403882.791] (II) MGA(0): end of monitor info
[403882.793] (II) MGA(0): UNMAPPING framebuffer 0xFFFFFFFFB70CA000, 0x200000.
[403882.793] (II) MGA(0): EDID vendor "GSM", prod id 22122
[403882.793] (II) MGA(0): Using EDID range info for horizontal sync
[403882.793] (II) MGA(0): Using EDID range info for vertical refresh
[403882.793] (II) MGA(0): Printing DDC gathered Modelines:
[403882.793] (II) MGA(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[403882.793] (II) MGA(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[403882.793] (II) MGA(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[403882.793] (II) MGA(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[403882.793] (II) MGA(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[403882.793] (II) MGA(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[403882.793] (II) MGA(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[403882.793] (II) MGA(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[403882.793] (II) MGA(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[403882.793] (II) MGA(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[403882.793] (II) MGA(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[403882.793] (II) MGA(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[403882.793] (II) MGA(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[403882.793] (II) MGA(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[403882.793] (II) MGA(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[403882.793] (II) MGA(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[403882.793] (II) MGA(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[403882.793] (==) MGA(0): Using gamma correction (1.0, 1.0, 1.0)
[403882.793] (==) MGA(0): Min pixel clock is 17 MHz
[403882.793] (--) MGA(0): Max pixel clock is 220 MHz
[403882.793] (--) MGA(0): MCLK used is 60.0 MHz
[403882.793] (II) MGA(0): Configured Monitor: Using hsync range of 28.00-83.00 kHz
[403882.793] (II) MGA(0): Configured Monitor: Using vrefresh range of 56.00-75.00 Hz
[403882.793] (II) MGA(0): Configured Monitor: Using maximum pixel clock of 155.00 MHz
[403882.793] (II) MGA(0): Estimated virtual size for aspect ratio 1.5312 is 1680x1050
[403882.793] (II) MGA(0): Clock range:  17.75 to 220.00 MHz
[403882.793] (II) MGA(0): Not using default mode "640x350" (vrefresh out of range)
[403882.793] (II) MGA(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
[403882.793] (II) MGA(0): Not using default mode "640x400" (vrefresh out of range)
[403882.793] (II) MGA(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
[403882.793] (II) MGA(0): Not using default mode "720x400" (vrefresh out of range)
[403882.793] (II) MGA(0): Not using default mode "360x200" (vrefresh out of range)
[403882.794] (II) MGA(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
[403882.794] (II) MGA(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
[403882.794] (II) MGA(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
[403882.794] (II) MGA(0): Not using default mode "640x480" (vrefresh out of range)
[403882.794] (II) MGA(0): Not using default mode "320x240" (vrefresh out of range)
[403882.794] (II) MGA(0): Not using default mode "800x600" (vrefresh out of range)
[403882.794] (II) MGA(0): Not using default mode "400x300" (vrefresh out of range)
[403882.794] (II) MGA(0): Not using default mode "1024x768i" (vrefresh out of range)
[403882.794] (II) MGA(0): Not using default mode "512x384i" (vrefresh out of range)
[403882.794] (II) MGA(0): Not using default mode "1024x768" (vrefresh out of range)
[403882.794] (II) MGA(0): Not using default mode "512x384" (vrefresh out of range)
[403882.794] (II) MGA(0): Not using default mode "1280x960" (insufficient memory for mode)
[403882.794] (II) MGA(0): Not using default mode "1280x960" (insufficient memory for mode)
[403882.794] (II) MGA(0): Not using default mode "640x480" (hsync out of range)
[403882.794] (II) MGA(0): Not using default mode "1280x1024" (insufficient memory for mode)
[403882.794] (II) MGA(0): Not using default mode "1280x1024" (insufficient memory for mode)
[403882.794] (II) MGA(0): Not using default mode "1280x1024" (insufficient memory for mode)
[403882.794] (II) MGA(0): Not using default mode "640x512" (hsync out of range)
[403882.794] (II) MGA(0): Not using default mode "1600x1200" (insufficient memory for mode)
[403882.794] (II) MGA(0): Not using default mode "1600x1200" (insufficient memory for mode)
[403882.794] (II) MGA(0): Not using default mode "1600x1200" (insufficient memory for mode)
[403882.794] (II) MGA(0): Not using default mode "800x600" (hsync out of range)
[403882.794] (II) MGA(0): Not using default mode "1600x1200" (insufficient memory for mode)
[403882.794] (II) MGA(0): Not using default mode "800x600" (hsync out of range)
[403882.794] (II) MGA(0): Not using default mode "1600x1200" (insufficient memory for mode)
[403882.794] (II) MGA(0): Not using default mode "800x600" (hsync out of range)
[403882.794] (II) MGA(0): Not using default mode "1792x1344" (insufficient memory for mode)
[403882.794] (II) MGA(0): Not using default mode "1792x1344" (insufficient memory for mode)
[403882.794] (II) MGA(0): Not using default mode "896x672" (hsync out of range)
[403882.794] (II) MGA(0): Not using default mode "1856x1392" (insufficient memory for mode)
[403882.794] (II) MGA(0): Not using default mode "928x696" (hsync out of range)
[403882.794] (II) MGA(0): Not using default mode "1856x1392" (insufficient memory for mode)
[403882.794] (II) MGA(0): Not using default mode "928x696" (hsync out of range)
[403882.794] (II) MGA(0): Not using default mode "1920x1440" (insufficient memory for mode)
[403882.794] (II) MGA(0): Not using default mode "960x720" (hsync out of range)
[403882.794] (II) MGA(0): Not using default mode "1920x1440" (insufficient memory for mode)
[403882.794] (II) MGA(0): Not using default mode "960x720" (hsync out of range)
[403882.794] (II) MGA(0): Not using default mode "1152x864" (vrefresh out of range)
[403882.794] (II) MGA(0): Not using default mode "576x432" (vrefresh out of range)
[403882.794] (II) MGA(0): Not using default mode "1152x864" (vrefresh out of range)
[403882.794] (II) MGA(0): Not using default mode "576x432" (vrefresh out of range)
[403882.794] (II) MGA(0): Not using default mode "1152x864" (hsync out of range)
[403882.794] (II) MGA(0): Not using default mode "576x432" (hsync out of range)
[403882.794] (II) MGA(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
[403882.794] (II) MGA(0): Not using default mode "1400x1050" (insufficient memory for mode)
[403882.794] (II) MGA(0): Not using default mode "1400x1050" (insufficient memory for mode)
[403882.794] (II) MGA(0): Not using default mode "1400x1050" (insufficient memory for mode)
[403882.794] (II) MGA(0): Not using default mode "1400x1050" (insufficient memory for mode)
[403882.794] (II) MGA(0): Not using default mode "700x525" (hsync out of range)
[403882.794] (II) MGA(0): Not using default mode "1440x900" (insufficient memory for mode)
[403882.794] (II) MGA(0): Not using default mode "1600x1024" (insufficient memory for mode)
[403882.794] (II) MGA(0): Not using default mode "1680x1050" (insufficient memory for mode)
[403882.794] (II) MGA(0): Not using default mode "1680x1050" (insufficient memory for mode)
[403882.794] (II) MGA(0): Not using default mode "1680x1050" (insufficient memory for mode)
[403882.794] (II) MGA(0): Not using default mode "1680x1050" (insufficient memory for mode)
[403882.794] (II) MGA(0): Not using default mode "1680x1050" (insufficient memory for mode)
[403882.794] (II) MGA(0): Not using default mode "840x525" (hsync out of range)
[403882.794] (II) MGA(0): Not using default mode "1920x1080" (insufficient memory for mode)
[403882.794] (II) MGA(0): Not using default mode "1920x1200" (insufficient memory for mode)
[403882.794] (II) MGA(0): Not using default mode "1920x1440" (insufficient memory for mode)
[403882.794] (II) MGA(0): Not using default mode "960x720" (hsync out of range)
[403882.794] (II) MGA(0): Not using default mode "2048x1536" (insufficient memory for mode)
[403882.794] (II) MGA(0): Not using default mode "1024x768" (hsync out of range)
[403882.794] (II) MGA(0): Not using default mode "2048x1536" (insufficient memory for mode)
[403882.794] (II) MGA(0): Not using default mode "1024x768" (hsync out of range)
[403882.794] (II) MGA(0): Not using default mode "2048x1536" (insufficient memory for mode)
[403882.794] (II) MGA(0): Not using default mode "1024x768" (hsync out of range)
[403882.794] (II) MGA(0): Not using driver mode "1680x1050" (insufficient memory for mode)
[403882.795] (II) MGA(0): Not using driver mode "1680x1050" (insufficient memory for mode)
[403882.795] (II) MGA(0): Not using driver mode "1280x1024" (insufficient memory for mode)
[403882.795] (II) MGA(0): Not using driver mode "1440x900" (insufficient memory for mode)
[403882.795] (II) MGA(0): Not using driver mode "1440x900" (insufficient memory for mode)
[403882.795] (II) MGA(0): Not using driver mode "1280x1024" (insufficient memory for mode)
[403882.795] (II) MGA(0): Not using driver mode "1280x960" (insufficient memory for mode)
[403882.795] (WW) MGA(0): Shrinking virtual size estimate from 1680x1050 to 1152x864
[403882.795] (II) MGA(0): Not using default mode "1360x768" (width too large for virtual size)
[403882.795] (--) MGA(0): Has SDRAM
[403882.795] (--) MGA(0): Virtual size is 1152x864 (pitch 1152)
[403882.795] (**) MGA(0): *Driver mode "1152x864": 108.0 MHz, 67.5 kHz, 75.0 Hz
[403882.795] (II) MGA(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[403882.795] (**) MGA(0): *Default mode "1152x864": 108.0 MHz, 67.5 kHz, 75.0 Hz
[403882.795] (II) MGA(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[403882.795] (**) MGA(0): *Default mode "1152x864": 105.0 MHz, 67.6 kHz, 75.0 Hz
[403882.795] (II) MGA(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.6 kHz)
[403882.795] (**) MGA(0): *Default mode "1152x864": 96.8 MHz, 63.0 kHz, 70.0 Hz
[403882.795] (II) MGA(0): Modeline "1152x864"x70.0   96.77  1152 1224 1344 1536  864 865 868 900 -hsync +vsync (63.0 kHz)
[403882.795] (**) MGA(0): *Default mode "1152x864": 81.6 MHz, 53.7 kHz, 60.0 Hz
[403882.795] (II) MGA(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
[403882.795] (**) MGA(0): *Driver mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
[403882.795] (II) MGA(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[403882.795] (**) MGA(0): *Driver mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
[403882.795] (II) MGA(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[403882.795] (**) MGA(0): *Default mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
[403882.795] (II) MGA(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[403882.795] (**) MGA(0): *Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
[403882.795] (II) MGA(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[403882.795] (**) MGA(0): *Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
[403882.795] (II) MGA(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[403882.795] (**) MGA(0): *Default mode "896x672": 102.4 MHz, 83.7 kHz, 60.0 Hz (D)
[403882.795] (II) MGA(0): Modeline "896x672"x60.0  102.40  896 960 1060 1224  672 672 674 697 doublescan -hsync +vsync (83.7 kHz)
[403882.795] (**) MGA(0): *Driver mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
[403882.795] (II) MGA(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[403882.795] (**) MGA(0): *Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
[403882.795] (II) MGA(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[403882.795] (**) MGA(0): *Driver mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
[403882.795] (II) MGA(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[403882.795] (**) MGA(0): *Driver mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
[403882.795] (II) MGA(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[403882.795] (**) MGA(0): *Driver mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
[403882.795] (II) MGA(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[403882.795] (**) MGA(0): *Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
[403882.795] (II) MGA(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[403882.795] (**) MGA(0): *Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
[403882.795] (II) MGA(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[403882.795] (**) MGA(0): *Default mode "800x600": 87.8 MHz, 81.2 kHz, 65.0 Hz (D)
[403882.795] (II) MGA(0): Modeline "800x600"x65.0   87.75  800 832 928 1080  600 600 602 625 doublescan +hsync +vsync (81.2 kHz)
[403882.796] (**) MGA(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
[403882.796] (II) MGA(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[403882.796] (**) MGA(0): *Default mode "800x600": 81.0 MHz, 75.0 kHz, 60.0 Hz (D)
[403882.796] (II) MGA(0): Modeline "800x600"x60.0   81.00  800 832 928 1080  600 600 602 625 doublescan +hsync +vsync (75.0 kHz)
[403882.796] (**) MGA(0): *Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
[403882.796] (II) MGA(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[403882.796] (**) MGA(0): *Default mode "840x525": 93.5 MHz, 82.3 kHz, 75.0 Hz (D)
[403882.796] (II) MGA(0): Modeline "840x525"x75.0   93.50  840 900 988 1136  525 526 529 549 doublescan -hsync +vsync (82.3 kHz)
[403882.796] (**) MGA(0): *Default mode "840x525": 87.0 MHz, 76.6 kHz, 69.9 Hz (D)
[403882.796] (II) MGA(0): Modeline "840x525"x69.9   87.00  840 900 988 1136  525 526 529 548 doublescan -hsync +vsync (76.6 kHz)
[403882.796] (**) MGA(0): *Default mode "840x525": 73.1 MHz, 65.3 kHz, 60.0 Hz (D)
[403882.796] (II) MGA(0): Modeline "840x525"x60.0   73.12  840 892 980 1120  525 526 529 544 doublescan -hsync +vsync (65.3 kHz)
[403882.796] (**) MGA(0): *Default mode "700x525": 77.9 MHz, 81.5 kHz, 74.8 Hz (D)
[403882.796] (II) MGA(0): Modeline "700x525"x74.8   77.90  700 732 892 956  525 526 532 545 doublescan +hsync +vsync (81.5 kHz)
[403882.796] (**) MGA(0): *Default mode "700x525": 72.5 MHz, 76.5 kHz, 70.1 Hz (D)
[403882.796] (II) MGA(0): Modeline "700x525"x70.1   72.53  700 748 824 948  525 525 527 546 doublescan -hsync +vsync (76.5 kHz)
[403882.796] (**) MGA(0): *Default mode "700x525": 61.0 MHz, 64.9 kHz, 60.0 Hz (D)
[403882.796] (II) MGA(0): Modeline "700x525"x60.0   61.00  700 744 820 940  525 526 532 541 doublescan +hsync +vsync (64.9 kHz)
[403882.796] (**) MGA(0): *Default mode "640x512": 67.5 MHz, 80.0 kHz, 75.0 Hz (D)
[403882.796] (II) MGA(0): Modeline "640x512"x75.0   67.50  640 648 720 844  512 512 514 533 doublescan +hsync +vsync (80.0 kHz)
[403882.796] (**) MGA(0): *Default mode "640x512": 54.0 MHz, 64.0 kHz, 60.0 Hz (D)
[403882.796] (II) MGA(0): Modeline "640x512"x60.0   54.00  640 664 720 844  512 512 514 533 doublescan +hsync +vsync (64.0 kHz)
[403882.796] (**) MGA(0): *Default mode "720x450": 53.2 MHz, 55.9 kHz, 59.9 Hz (D)
[403882.796] (II) MGA(0): Modeline "720x450"x59.9   53.25  720 760 836 952  450 451 454 467 doublescan -hsync +vsync (55.9 kHz)
[403882.796] (**) MGA(0): *Driver mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
[403882.796] (II) MGA(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[403882.796] (**) MGA(0): *Driver mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
[403882.796] (II) MGA(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[403882.796] (**) MGA(0): *Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
[403882.796] (II) MGA(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[403882.796] (**) MGA(0): *Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
[403882.796] (II) MGA(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[403882.796] (**) MGA(0): *Default mode "640x480": 54.0 MHz, 60.0 kHz, 60.0 Hz (D)
[403882.796] (II) MGA(0): Modeline "640x480"x60.0   54.00  640 688 744 900  480 480 482 500 doublescan +hsync +vsync (60.0 kHz)
[403882.796] (**) MGA(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
[403882.796] (II) MGA(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[403882.796] (**) MGA(0): *Driver mode "720x400": 28.3 MHz, 31.5 kHz, 70.1 Hz
[403882.796] (II) MGA(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[403882.796] (**) MGA(0): *Default mode "680x384": 36.0 MHz, 47.4 kHz, 60.0 Hz (D)
[403882.796] (II) MGA(0): Modeline "680x384"x60.0   36.00  680 704 720 760  384 385 390 395 doublescan +hsync -vsync (47.4 kHz)
[403882.796] (**) MGA(0): *Default mode "680x384": 42.4 MHz, 47.7 kHz, 59.8 Hz (D)
[403882.796] (II) MGA(0): Modeline "680x384"x59.8   42.38  680 716 784 888  384 385 390 399 doublescan -hsync +vsync (47.7 kHz)
[403882.796] (**) MGA(0): *Default mode "576x432": 54.0 MHz, 67.5 kHz, 75.0 Hz (D)
[403882.796] (II) MGA(0): Modeline "576x432"x75.0   54.00  576 608 672 800  432 432 434 450 doublescan +hsync +vsync (67.5 kHz)
[403882.796] (**) MGA(0): *Default mode "576x432": 52.5 MHz, 67.6 kHz, 75.0 Hz (D)
[403882.796] (II) MGA(0): Modeline "576x432"x75.0   52.49  576 612 676 776  432 432 434 451 doublescan -hsync +vsync (67.6 kHz)
[403882.796] (**) MGA(0): *Default mode "576x432": 48.4 MHz, 63.0 kHz, 70.0 Hz (D)
[403882.796] (II) MGA(0): Modeline "576x432"x70.0   48.38  576 612 672 768  432 432 434 450 doublescan -hsync +vsync (63.0 kHz)
[403882.796] (**) MGA(0): *Default mode "576x432": 40.8 MHz, 53.7 kHz, 60.1 Hz (D)
[403882.796] (II) MGA(0): Modeline "576x432"x60.1   40.81  576 608 668 760  432 432 434 447 doublescan -hsync +vsync (53.7 kHz)
[403882.796] (**) MGA(0): *Default mode "512x384": 39.4 MHz, 60.0 kHz, 75.0 Hz (D)
[403882.796] (II) MGA(0): Modeline "512x384"x75.0   39.38  512 520 568 656  384 384 386 400 doublescan +hsync +vsync (60.0 kHz)
[403882.796] (**) MGA(0): *Default mode "512x384": 37.5 MHz, 56.5 kHz, 70.1 Hz (D)
[403882.796] (II) MGA(0): Modeline "512x384"x70.1   37.50  512 524 592 664  384 385 388 403 doublescan -hsync -vsync (56.5 kHz)
[403882.796] (**) MGA(0): *Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
[403882.796] (II) MGA(0): Modeline "512x384"x60.0   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync (48.4 kHz)
[403882.796] (**) MGA(0): *Default mode "416x312": 28.6 MHz, 49.7 kHz, 74.7 Hz (D)
[403882.796] (II) MGA(0): Modeline "416x312"x74.7   28.64  416 432 464 576  312 312 314 333 doublescan -hsync -vsync (49.7 kHz)
[403882.797] (**) MGA(0): *Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (D)
[403882.797] (II) MGA(0): Modeline "400x300"x75.1   24.75  400 408 448 528  300 300 302 312 doublescan +hsync +vsync (46.9 kHz)
[403882.797] (**) MGA(0): *Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
[403882.797] (II) MGA(0): Modeline "400x300"x72.2   25.00  400 428 488 520  300 318 321 333 doublescan +hsync +vsync (48.1 kHz)
[403882.797] (**) MGA(0): *Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
[403882.797] (II) MGA(0): Modeline "400x300"x60.3   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz)
[403882.797] (**) MGA(0): *Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
[403882.797] (II) MGA(0): Modeline "400x300"x56.3   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (35.2 kHz)
[403882.797] (**) MGA(0): Display dimensions: (490, 320) mm
[403882.797] (**) MGA(0): DPI set to (59, 68)
[403882.797] (II) MGA(0): YDstOrg is set to 0
[403882.797] (II) Loading sub module "fb"
[403882.797] (II) LoadModule: "fb"
[403882.797] (II) Loading /usr/lib/xorg/modules/libfb.so
[403882.797] (II) Module fb: vendor="X.Org Foundation"
[403882.797] 	compiled for 1.10.4, module version = 1.0.0
[403882.797] 	ABI class: X.Org ANSI C Emulation, version 0.4
[403882.797] (II) Loading sub module "xaa"
[403882.797] (II) LoadModule: "xaa"
[403882.797] (II) Loading /usr/lib/xorg/modules/libxaa.so
[403882.797] (II) Module xaa: vendor="X.Org Foundation"
[403882.797] 	compiled for 1.10.4, module version = 1.2.1
[403882.797] 	ABI class: X.Org Video Driver, version 10.0
[403882.797] (II) Loading sub module "ramdac"
[403882.797] (II) LoadModule: "ramdac"
[403882.797] (II) Module "ramdac" already built-in
[403882.797] (II) UnloadModule: "vesa"
[403882.797] (II) Unloading vesa
[403882.797] (II) UnloadModule: "fbdev"
[403882.797] (II) Unloading fbdev
[403882.797] (II) UnloadModule: "fbdevhw"
[403882.797] (II) Unloading fbdevhw
[403882.798] (II) MGA(0): MAPPED Framebuffer FD800000 200000 to FFFFFFFFB703D000.
[403882.798] (II) MGA(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
[403882.816] (--) MGA(0): 32 DWORD fifo
[403882.828] (==) MGA(0): Default visual is TrueColor
[403882.828] (EE) MGA(0): Static buffer allocation failed, not initializing the DRI
[403882.828] (EE) MGA(0): Need at least 5832 kB video memory at this resolution, bit depth
[403882.828] (II) MGA(0): Using 46 lines for offscreen memory.
[403882.828] (II) MGA(0): Using XFree86 Acceleration Architecture (XAA)
[403882.828] 	Screen to screen bit blits
[403882.828] 	Solid filled rectangles
[403882.828] 	Solid filled trapezoids
[403882.828] 	8x8 mono pattern filled rectangles
[403882.828] 	8x8 mono pattern filled trapezoids
[403882.828] 	Indirect CPU to Screen color expansion
[403882.828] 	Screen to Screen color expansion
[403882.828] 	Solid Lines
[403882.828] 	Dashed Lines
[403882.828] 	Scanline Image Writes
[403882.828] 	Driver provided FillCacheBltRects replacement
[403882.828] 	Setting up tile and stipple cache:
[403882.828] 		9 128x46 slots
[403882.828] (==) MGA(0): Backing store disabled
[403882.828] (==) MGA(0): Silken mouse enabled
[403882.829] (==) MGA(0): DPMS enabled
[403882.829] (WW) MGA(0): Direct rendering disabled
[403882.829] (==) RandR enabled
[403882.829] (II) Initializing built-in extension Generic Event Extension
[403882.829] (II) Initializing built-in extension SHAPE
[403882.829] (II) Initializing built-in extension MIT-SHM
[403882.829] (II) Initializing built-in extension XInputExtension
[403882.829] (II) Initializing built-in extension XTEST
[403882.829] (II) Initializing built-in extension BIG-REQUESTS
[403882.829] (II) Initializing built-in extension SYNC
[403882.829] (II) Initializing built-in extension XKEYBOARD
[403882.829] (II) Initializing built-in extension XC-MISC
[403882.829] (II) Initializing built-in extension SECURITY
[403882.829] (II) Initializing built-in extension XINERAMA
[403882.829] (II) Initializing built-in extension XFIXES
[403882.829] (II) Initializing built-in extension RENDER
[403882.829] (II) Initializing built-in extension RANDR
[403882.829] (II) Initializing built-in extension COMPOSITE
[403882.829] (II) Initializing built-in extension DAMAGE
[403882.829] (II) Initializing built-in extension GESTURE
[403882.838] (II) AIGLX: Screen 0 is not DRI2 capable
[403882.838] (II) AIGLX: Screen 0 is not DRI capable
[403882.838] (II) AIGLX: Trying DRI driver /usr/lib/i386-linux-gnu/dri/swrast_dri.so
[403882.841] (II) AIGLX: Loaded and initialized swrast
[403882.841] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[403882.852] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[403882.861] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[403882.862] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[403882.862] (II) LoadModule: "evdev"
[403882.862] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[403882.863] (II) Module evdev: vendor="X.Org Foundation"
[403882.863] 	compiled for 1.10.2, module version = 2.6.0
[403882.863] 	Module class: X.Org XInput Driver
[403882.863] 	ABI class: X.Org XInput driver, version 12.3
[403882.863] (II) Using input driver 'evdev' for 'Power Button'
[403882.863] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[403882.863] (**) Power Button: always reports core events
[403882.863] (**) Power Button: Device: "/dev/input/event1"
[403882.863] (--) Power Button: Found keys
[403882.863] (II) Power Button: Configuring as keyboard
[403882.863] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[403882.863] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[403882.863] (**) Option "xkb_rules" "evdev"
[403882.863] (**) Option "xkb_model" "pc105"
[403882.863] (**) Option "xkb_layout" "gb"
[403882.863] (**) Option "xkb_options" "lv3:ralt_switch"
[403882.865] (II) XKB: reuse xkmfile /var/lib/xkb/server-884C6C7246E5186E4DB7A4CD26B9F16BE06DFFDC.xkm
[403882.868] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[403882.868] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[403882.868] (II) Using input driver 'evdev' for 'Power Button'
[403882.868] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[403882.868] (**) Power Button: always reports core events
[403882.868] (**) Power Button: Device: "/dev/input/event0"
[403882.868] (--) Power Button: Found keys
[403882.868] (II) Power Button: Configuring as keyboard
[403882.868] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[403882.868] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[403882.868] (**) Option "xkb_rules" "evdev"
[403882.868] (**) Option "xkb_model" "pc105"
[403882.868] (**) Option "xkb_layout" "gb"
[403882.868] (**) Option "xkb_options" "lv3:ralt_switch"
[403882.877] (II) config/udev: Adding input device AT Raw Set 2 keyboard (/dev/input/event2)
[403882.877] (**) AT Raw Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[403882.877] (II) Using input driver 'evdev' for 'AT Raw Set 2 keyboard'
[403882.877] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[403882.877] (**) AT Raw Set 2 keyboard: always reports core events
[403882.877] (**) AT Raw Set 2 keyboard: Device: "/dev/input/event2"
[403882.877] (--) AT Raw Set 2 keyboard: Found keys
[403882.877] (II) AT Raw Set 2 keyboard: Configuring as keyboard
[403882.877] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input2/event2"
[403882.877] (II) XINPUT: Adding extended input device "AT Raw Set 2 keyboard" (type: KEYBOARD)
[403882.877] (**) Option "xkb_rules" "evdev"
[403882.877] (**) Option "xkb_model" "pc105"
[403882.877] (**) Option "xkb_layout" "gb"
[403882.877] (**) Option "xkb_options" "lv3:ralt_switch"
```

---

