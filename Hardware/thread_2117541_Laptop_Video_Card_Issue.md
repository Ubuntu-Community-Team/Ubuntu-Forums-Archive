---
title: "Laptop Video Card Issue"
date: 2013-02-18
forum: Hardware
---

### Post by Ericj1186 on 2013-02-18
About a month ago, I took my laptop into the shop to replace a dead charging port. When I got it back, the speakers didn't work, and I knew it was because of a cable that was unplugged. I went back inside and replugged that in, and the sound worked, but I got an error that said video card is unplugged.

I am on Linux, so I ran lspci | grep VGA, and it shows my video card in the list. I updated the video card drivers and rebooted. When I got back to Ubuntu, Unity wouldn't load (as in no launcher displayed and no bar at the top). After trying a few things, the only change I really got was the resolution dropped to 640 X 480, and there are black bars on the sides of the main screen, shrinking it down like wide screen movies. I have purged the drivers and reinstalled them, and that would only change the aspect ratio.

I opened the computer back up, and I do not see a video card to manipulate.
Any ideas?

---

### Post by Yellow Pasque on 2013-02-19
If the video card was "unplugged", how could you see anything that could give you an error? Where did you get that error message?
> I opened the computer back up, and I do not see a video card to manipulate.
They're generally integrated into the motherboard chipset (or the CPU itself).

> I am on Linux, so I ran lspci | grep VGA, and it shows my video card in the list. I updated the video card drivers and rebooted. When I got back to Ubuntu, Unity wouldn't load (as in no launcher displayed and no bar at the top)

You're probably using the wrong driver. Need more info here, like your laptop model (which you should always give when asking for help) and output of lspci command. /var/log/Xorg.0.log may be helpful as well.

---

### Post by Ericj1186 on 2013-02-19
The laptop is an ASUS A53S with a k53SD motherboard.

Output for lspci

```

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: NVIDIA Corporation Device 1058 (rev ff)
03:00.0 Network controller: Intel Corporation Centrino Wireless-N 100
04:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller
05:00.0 Ethernet controller: Atheros Communications Inc. AR8151  v2.0 Gigabit Ethernet (rev c0)

```

Output of Xorg.0.log
```
[    15.105] 
X.Org X Server 1.12.4
Release Date: 2012-08-27
[    15.105] X Protocol Version 11, Revision 0
[    15.105] Build Operating System: Linux 2.6.24-32-xen x86_64 Ubuntu
[    15.105] Current Operating System: Linux eric-K53SD 3.5.0-23-generic #35-Ubuntu SMP Thu Jan 24 13:15:40 UTC 2013 x86_64
[    15.105] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-23-generic root=UUID=27886e28-b9af-482e-b4ae-a5a2950659dc ro quiet splash
[    15.105] Build Date: 05 November 2012  10:00:21AM
[    15.105] xorg-server 3:1.12.4+git20121105-makson1~ppa2 (For technical support please see http://www.ubuntu.com/support) 
[    15.105] Current version of pixman: 0.26.0
[    15.105] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    15.105] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    15.105] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Feb 19 20:02:42 2013
[    15.105] (==) Using config file: "/etc/X11/xorg.conf"
[    15.105] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    15.105] (==) ServerLayout "Layout0"
[    15.105] (**) |-->Screen "Screen0" (0)
[    15.105] (**) |   |-->Monitor "Monitor0"
[    15.105] (**) |   |-->Device "Device0"
[    15.105] (**) |-->Input Device "Keyboard0"
[    15.105] (**) |-->Input Device "Mouse0"
[    15.105] (==) Automatically adding devices
[    15.105] (==) Automatically enabling devices
[    15.105] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    15.105] 	Entry deleted from font path.
[    15.105] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    15.105] 	Entry deleted from font path.
[    15.105] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    15.105] 	Entry deleted from font path.
[    15.105] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    15.105] 	Entry deleted from font path.
[    15.105] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    15.105] 	Entry deleted from font path.
[    15.105] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    15.105] 	Entry deleted from font path.
[    15.105] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    15.105] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    15.105] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    15.105] (WW) Disabling Keyboard0
[    15.105] (WW) Disabling Mouse0
[    15.105] (II) Loader magic: 0x7f2a73dd1b20
[    15.105] (II) Module ABI versions:
[    15.105] 	X.Org ANSI C Emulation: 0.4
[    15.105] 	X.Org Video Driver: 12.2
[    15.105] 	X.Org XInput driver : 16.0
[    15.105] 	X.Org Server Extension : 6.0
[    15.106] (--) PCI:*(0:0:2:0) 8086:0116:1043:1652 rev 9, Mem @ 0xdc400000/4194304, 0xb0000000/268435456, I/O @ 0x0000e000/64
[    15.106] (II) Open ACPI successful (/var/run/acpid.socket)
[    15.106] (II) LoadModule: "extmod"
[    15.106] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    15.106] (II) Module extmod: vendor="X.Org Foundation"
[    15.106] 	compiled for 1.12.4, module version = 1.0.0
[    15.106] 	Module class: X.Org Server Extension
[    15.106] 	ABI class: X.Org Server Extension, version 6.0
[    15.106] (II) Loading extension MIT-SCREEN-SAVER
[    15.106] (II) Loading extension XFree86-VidModeExtension
[    15.106] (II) Loading extension XFree86-DGA
[    15.106] (II) Loading extension DPMS
[    15.106] (II) Loading extension XVideo
[    15.106] (II) Loading extension XVideo-MotionCompensation
[    15.106] (II) Loading extension X-Resource
[    15.106] (II) LoadModule: "dbe"
[    15.106] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    15.106] (II) Module dbe: vendor="X.Org Foundation"
[    15.106] 	compiled for 1.12.4, module version = 1.0.0
[    15.106] 	Module class: X.Org Server Extension
[    15.106] 	ABI class: X.Org Server Extension, version 6.0
[    15.106] (II) Loading extension DOUBLE-BUFFER
[    15.106] (II) LoadModule: "glx"
[    15.106] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    15.112] (II) Module glx: vendor="NVIDIA Corporation"
[    15.112] 	compiled for 4.0.2, module version = 1.0.0
[    15.112] 	Module class: X.Org Server Extension
[    15.112] (II) NVIDIA GLX Module  304.64  Tue Oct 30 11:18:32 PDT 2012
[    15.112] (II) Loading extension GLX
[    15.112] (II) LoadModule: "record"
[    15.113] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    15.113] (II) Module record: vendor="X.Org Foundation"
[    15.113] 	compiled for 1.12.4, module version = 1.13.0
[    15.113] 	Module class: X.Org Server Extension
[    15.113] 	ABI class: X.Org Server Extension, version 6.0
[    15.113] (II) Loading extension RECORD
[    15.113] (II) LoadModule: "dri"
[    15.113] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    15.113] (II) Module dri: vendor="X.Org Foundation"
[    15.113] 	compiled for 1.12.4, module version = 1.0.0
[    15.113] 	ABI class: X.Org Server Extension, version 6.0
[    15.113] (II) Loading extension XFree86-DRI
[    15.113] (II) LoadModule: "dri2"
[    15.113] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    15.113] (II) Module dri2: vendor="X.Org Foundation"
[    15.113] 	compiled for 1.12.4, module version = 1.2.0
[    15.113] 	ABI class: X.Org Server Extension, version 6.0
[    15.113] (II) Loading extension DRI2
[    15.113] (II) LoadModule: "nvidia"
[    15.113] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    15.113] (II) Module nvidia: vendor="NVIDIA Corporation"
[    15.113] 	compiled for 4.0.2, module version = 1.0.0
[    15.113] 	Module class: X.Org Video Driver
[    15.115] (EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
[    15.115] (EE) NVIDIA:     system's kernel log for additional error messages.
[    15.115] (II) UnloadModule: "nvidia"
[    15.115] (II) Unloading nvidia
[    15.115] (EE) Failed to load module "nvidia" (module-specific error, 0)
[    15.115] (==) Matched intel as autoconfigured driver 0
[    15.115] (==) Matched vesa as autoconfigured driver 1
[    15.115] (==) Matched fbdev as autoconfigured driver 2
[    15.115] (==) Assigned the driver to the xf86ConfigLayout
[    15.115] (II) LoadModule: "intel"
[    15.129] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    15.129] (II) Module intel: vendor="X.Org Foundation"
[    15.129] 	compiled for 1.12.3, module version = 2.20.8
[    15.129] 	Module class: X.Org Video Driver
[    15.129] 	ABI class: X.Org Video Driver, version 12.0
[    15.129] (II) LoadModule: "vesa"
[    15.130] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    15.130] (II) Module vesa: vendor="X.Org Foundation"
[    15.130] 	compiled for 1.12.3, module version = 2.3.2
[    15.130] 	Module class: X.Org Video Driver
[    15.130] 	ABI class: X.Org Video Driver, version 12.0
[    15.130] (II) LoadModule: "fbdev"
[    15.130] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    15.130] (II) Module fbdev: vendor="X.Org Foundation"
[    15.130] 	compiled for 1.12.3, module version = 0.4.3
[    15.130] 	Module class: X.Org Video Driver
[    15.130] 	ABI class: X.Org Video Driver, version 12.0
[    15.130] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
	Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
	Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
	Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
	Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server,
	Ivybridge Server (GT2), Haswell Desktop (GT1), Haswell Desktop (GT2),
	Haswell Desktop (GT2+), Haswell Mobile (GT1), Haswell Mobile (GT2),
	Haswell Mobile (GT2+), Haswell Server (GT1), Haswell Server (GT2),
	Haswell Server (GT2+), Haswell SDV Desktop (GT1),
	Haswell SDV Desktop (GT2), Haswell SDV Desktop (GT2+),
	Haswell SDV Mobile (GT1), Haswell SDV Mobile (GT2),
	Haswell SDV Mobile (GT2+), Haswell SDV Server (GT1),
	Haswell SDV Server (GT2), Haswell SDV Server (GT2+),
	Haswell ULT Desktop (GT1), Haswell ULT Desktop (GT2),
	Haswell ULT Desktop (GT2+), Haswell ULT Mobile (GT1),
	Haswell ULT Mobile (GT2), Haswell ULT Mobile (GT2+),
	Haswell ULT Server (GT1), Haswell ULT Server (GT2),
	Haswell ULT Server (GT2+), Haswell CRW Desktop (GT1),
	Haswell CRW Desktop (GT2), Haswell CRW Desktop (GT2+),
	Haswell CRW Mobile (GT1), Haswell CRW Mobile (GT2),
	Haswell CRW Mobile (GT2+), Haswell CRW Server (GT1),
	Haswell CRW Server (GT2), Haswell CRW Server (GT2+),
	ValleyView PO board
[    15.130] (II) VESA: driver for VESA chipsets: vesa
[    15.130] (II) FBDEV: driver for framebuffer: fbdev
[    15.130] (++) using VT number 7

[    15.130] drmOpenDevice: node name is /dev/dri/card0
[    15.130] drmOpenDevice: open result is 8, (OK)
[    15.130] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    15.130] drmOpenDevice: node name is /dev/dri/card0
[    15.130] drmOpenDevice: open result is 8, (OK)
[    15.130] drmOpenByBusid: drmOpenMinor returns 8
[    15.130] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    15.130] (II) intel(0): SNA compiled: xserver-xorg-video-intel 3:2.20.8+git20120928~quantal2 (Tomasz Makarewicz <makson96@gmail.com>)
[    15.130] (WW) Falling back to old probe method for vesa
[    15.130] (WW) Falling back to old probe method for fbdev
[    15.130] (II) Loading sub module "fbdevhw"
[    15.130] (II) LoadModule: "fbdevhw"
[    15.131] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    15.131] (II) Module fbdevhw: vendor="X.Org Foundation"
[    15.131] 	compiled for 1.12.4, module version = 0.0.2
[    15.131] 	ABI class: X.Org Video Driver, version 12.2
[    15.131] drmOpenDevice: node name is /dev/dri/card0
[    15.131] drmOpenDevice: open result is 9, (OK)
[    15.131] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    15.131] drmOpenDevice: node name is /dev/dri/card0
[    15.131] drmOpenDevice: open result is 9, (OK)
[    15.131] drmOpenByBusid: drmOpenMinor returns 9
[    15.131] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    15.131] (**) intel(0): Depth 24, (--) framebuffer bpp 32
[    15.131] (==) intel(0): RGB weight 888
[    15.131] (==) intel(0): Default visual is TrueColor
[    15.131] (--) intel(0): Integrated Graphics Chipset: Intel(R) Sandybridge Mobile (GT2)
[    15.131] (**) intel(0): Framebuffer tiled
[    15.131] (**) intel(0): Pixmaps tiled
[    15.131] (**) intel(0): 3D buffers tiled
[    15.131] (**) intel(0): Throttling enabled
[    15.131] (**) intel(0): Delayed flush enabled
[    15.131] (**) intel(0): "Tear free" disabled
[    15.131] (**) intel(0): Forcing per-crtc-pixmaps? no
[    15.131] (II) intel(0): Output LVDS1 using monitor section Monitor0
[    15.131] (--) intel(0): found backlight control interface acpi_video1 (type 'firmware')
[    15.131] (II) intel(0): Output VGA1 has no monitor section
[    15.144] (II) intel(0): Output HDMI1 has no monitor section
[    15.192] (II) intel(0): Output DP1 has no monitor section
[    15.192] (II) intel(0): EDID for output LVDS1
[    15.192] (II) intel(0): Manufacturer: AUO  Model: 26ec  Serial#: 0
[    15.192] (II) intel(0): Year: 2009  Week: 1
[    15.192] (II) intel(0): EDID Version: 1.3
[    15.192] (II) intel(0): Digital Display Input
[    15.192] (II) intel(0): Max Image Size [cm]: horiz.: 34  vert.: 19
[    15.192] (II) intel(0): Gamma: 2.20
[    15.192] (II) intel(0): No DPMS capabilities specified
[    15.192] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    15.192] (II) intel(0): First detailed timing is preferred mode
[    15.192] (II) intel(0): redX: 0.577 redY: 0.333   greenX: 0.333 greenY: 0.554
[    15.192] (II) intel(0): blueX: 0.161 blueY: 0.144   whiteX: 0.313 whiteY: 0.329
[    15.192] (II) intel(0): Manufacturer's mask: 0
[    15.192] (II) intel(0): Supported detailed timing:
[    15.192] (II) intel(0): clock: 71.8 MHz   Image Size:  344 x 193 mm
[    15.192] (II) intel(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1526 h_border: 0
[    15.192] (II) intel(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 784 v_border: 0
[    15.192] (II) intel(0): Unknown vendor-specific block f
[    15.192] (II) intel(0):  AUO
[    15.192] (II) intel(0):  B156XW02 V6
[    15.192] (II) intel(0): EDID (in hex):
[    15.192] (II) intel(0): 	00ffffffffffff0006afec2600000000
[    15.192] (II) intel(0): 	01130103802213780ad7759355558d29
[    15.192] (II) intel(0): 	24505400000001010101010101010101
[    15.192] (II) intel(0): 	0101010101010c1c56a0500010303020
[    15.192] (II) intel(0): 	360058c1100000180000000f00000000
[    15.192] (II) intel(0): 	00000000000000000020000000fe0041
[    15.192] (II) intel(0): 	554f0a202020202020202020000000fe
[    15.192] (II) intel(0): 	004231353658573032205636200a0065
[    15.192] (II) intel(0): EDID vendor "AUO", prod id 9964
[    15.192] (II) intel(0): Printing DDC gathered Modelines:
[    15.192] (II) intel(0): Modeline "1366x768"x0.0   71.80  1366 1414 1446 1526  768 771 777 784 -hsync -vsync (47.1 kHz eP)
[    15.192] (II) intel(0): Not using mode "1366x768" (hsync out of range)
[    15.192] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    15.192] (II) intel(0): Not using default mode "800x600" (hsync out of range)
[    15.192] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    15.192] (II) intel(0): Not using default mode "800x600" (hsync out of range)
[    15.192] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    15.192] (II) intel(0): Not using default mode "1024x768" (hsync out of range)
[    15.192] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    15.192] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    15.192] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    15.192] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    15.192] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    15.192] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    15.192] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    15.192] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    15.192] (II) intel(0): Not using default mode "1360x768" (hsync out of range)
[    15.192] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    15.192] (II) intel(0): Not using default mode "1360x768" (hsync out of range)
[    15.192] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    15.192] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    15.192] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    15.192] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    15.192] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    15.192] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    15.192] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    15.192] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    15.192] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    15.192] (II) intel(0): Printing probed modes for output LVDS1
[    15.192] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz d)
[    15.192] (II) intel(0): EDID for output VGA1
[    15.208] (II) intel(0): EDID for output HDMI1
[    15.412] (II) intel(0): EDID for output DP1
[    15.412] (II) intel(0): Output LVDS1 connected
[    15.412] (II) intel(0): Output VGA1 disconnected
[    15.412] (II) intel(0): Output HDMI1 disconnected
[    15.412] (II) intel(0): Output DP1 disconnected
[    15.412] (II) intel(0): Using exact sizes for initial modes
[    15.412] (II) intel(0): Output LVDS1 using initial mode 640x480
[    15.412] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    15.412] (**) intel(0): Display dimensions: (340, 190) mm
[    15.412] (**) intel(0): DPI set to (47, 64)
[    15.412] (II) Loading sub module "dri2"
[    15.412] (II) LoadModule: "dri2"
[    15.412] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    15.412] (II) Module dri2: vendor="X.Org Foundation"
[    15.412] 	compiled for 1.12.4, module version = 1.2.0
[    15.412] 	ABI class: X.Org Server Extension, version 6.0
[    15.412] (II) UnloadModule: "vesa"
[    15.412] (II) Unloading vesa
[    15.412] (II) UnloadModule: "fbdev"
[    15.412] (II) Unloading fbdev
[    15.412] (II) UnloadSubModule: "fbdevhw"
[    15.412] (II) Unloading fbdevhw
[    15.412] (==) Depth 24 pixmap format is 32 bpp
[    15.412] (II) intel(0): SNA initialized with SandyBridge backend
[    15.412] (==) intel(0): Backing store disabled
[    15.412] (==) intel(0): Silken mouse enabled
[    15.412] (II) intel(0): HW Cursor enabled
[    15.412] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    15.413] (**) intel(0): DPMS enabled
[    15.413] (II) intel(0): [DRI2] Setup complete
[    15.413] (II) intel(0): [DRI2]   DRI driver: i965
[    15.413] (II) intel(0): direct rendering: DRI2 Enabled
[    15.413] (==) intel(0): hotplug detection: "enabled"
[    15.413] (--) RandR disabled
[    15.413] (II) Initializing built-in extension Generic Event Extension
[    15.413] (II) Initializing built-in extension SHAPE
[    15.413] (II) Initializing built-in extension MIT-SHM
[    15.413] (II) Initializing built-in extension XInputExtension
[    15.413] (II) Initializing built-in extension XTEST
[    15.413] (II) Initializing built-in extension BIG-REQUESTS
[    15.413] (II) Initializing built-in extension SYNC
[    15.413] (II) Initializing built-in extension XKEYBOARD
[    15.413] (II) Initializing built-in extension XC-MISC
[    15.413] (II) Initializing built-in extension SECURITY
[    15.413] (II) Initializing built-in extension XINERAMA
[    15.413] (II) Initializing built-in extension XFIXES
[    15.413] (II) Initializing built-in extension RENDER
[    15.413] (II) Initializing built-in extension RANDR
[    15.413] (II) Initializing built-in extension COMPOSITE
[    15.413] (II) Initializing built-in extension DAMAGE
[    15.414] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
[    15.417] (II) intel(0): switch to mode 640x480 on crtc 3 (pipe 0)
[    15.682] (II) intel(0): Setting screen physical size to 169 x 127
[    15.687] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    15.688] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    15.688] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    15.688] (II) LoadModule: "evdev"
[    15.688] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    15.688] (II) Module evdev: vendor="X.Org Foundation"
[    15.688] 	compiled for 1.12.3, module version = 2.7.0
[    15.688] 	Module class: X.Org XInput Driver
[    15.688] 	ABI class: X.Org XInput driver, version 16.0
[    15.688] (II) Using input driver 'evdev' for 'Power Button'
[    15.689] (**) Power Button: always reports core events
[    15.689] (**) evdev: Power Button: Device: "/dev/input/event2"
[    15.689] (--) evdev: Power Button: Vendor 0 Product 0x1
[    15.689] (--) evdev: Power Button: Found keys
[    15.689] (II) evdev: Power Button: Configuring as keyboard
[    15.689] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    15.689] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    15.689] (**) Option "xkb_rules" "evdev"
[    15.689] (**) Option "xkb_model" "pc105"
[    15.689] (**) Option "xkb_layout" "us"
[    15.689] (II) config/udev: Adding input device Video Bus (/dev/input/event8)
[    15.689] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    15.689] (II) Using input driver 'evdev' for 'Video Bus'
[    15.689] (**) Video Bus: always reports core events
[    15.689] (**) evdev: Video Bus: Device: "/dev/input/event8"
[    15.689] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    15.689] (--) evdev: Video Bus: Found keys
[    15.689] (II) evdev: Video Bus: Configuring as keyboard
[    15.689] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input8/event8"
[    15.689] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    15.689] (**) Option "xkb_rules" "evdev"
[    15.689] (**) Option "xkb_model" "pc105"
[    15.689] (**) Option "xkb_layout" "us"
[    15.689] (II) config/udev: Adding input device Video Bus (/dev/input/event7)
[    15.689] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    15.689] (II) Using input driver 'evdev' for 'Video Bus'
[    15.689] (**) Video Bus: always reports core events
[    15.689] (**) evdev: Video Bus: Device: "/dev/input/event7"
[    15.689] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    15.689] (--) evdev: Video Bus: Found keys
[    15.689] (II) evdev: Video Bus: Configuring as keyboard
[    15.689] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input7/event7"
[    15.689] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 8)
[    15.689] (**) Option "xkb_rules" "evdev"
[    15.689] (**) Option "xkb_model" "pc105"
[    15.689] (**) Option "xkb_layout" "us"
[    15.690] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    15.690] (II) No input driver specified, ignoring this device.
[    15.690] (II) This device may have been added with another device file.
[    15.690] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    15.690] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    15.690] (II) Using input driver 'evdev' for 'Sleep Button'
[    15.690] (**) Sleep Button: always reports core events
[    15.690] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[    15.690] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    15.690] (--) evdev: Sleep Button: Found keys
[    15.690] (II) evdev: Sleep Button: Configuring as keyboard
[    15.690] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1/event1"
[    15.690] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[    15.690] (**) Option "xkb_rules" "evdev"
[    15.690] (**) Option "xkb_model" "pc105"
[    15.690] (**) Option "xkb_layout" "us"
[    15.690] (II) config/udev: Adding input device ASUS USB2.0 WebCam (/dev/input/event4)
[    15.690] (**) ASUS USB2.0 WebCam: Applying InputClass "evdev keyboard catchall"
[    15.690] (II) Using input driver 'evdev' for 'ASUS USB2.0 WebCam'
[    15.690] (**) ASUS USB2.0 WebCam: always reports core events
[    15.690] (**) evdev: ASUS USB2.0 WebCam: Device: "/dev/input/event4"
[    15.690] (--) evdev: ASUS USB2.0 WebCam: Vendor 0x58f Product 0xa014
[    15.690] (--) evdev: ASUS USB2.0 WebCam: Found keys
[    15.690] (II) evdev: ASUS USB2.0 WebCam: Configuring as keyboard
[    15.690] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input4/event4"
[    15.690] (II) XINPUT: Adding extended input device "ASUS USB2.0 WebCam" (type: KEYBOARD, id 10)
[    15.690] (**) Option "xkb_rules" "evdev"
[    15.690] (**) Option "xkb_model" "pc105"
[    15.690] (**) Option "xkb_layout" "us"
[    15.690] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event10)
[    15.691] (II) No input driver specified, ignoring this device.
[    15.691] (II) This device may have been added with another device file.
[    15.691] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event11)
[    15.691] (II) No input driver specified, ignoring this device.
[    15.691] (II) This device may have been added with another device file.
[    15.691] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event9)
[    15.691] (II) No input driver specified, ignoring this device.
[    15.691] (II) This device may have been added with another device file.
[    15.691] (II) config/udev: Adding input device Asus WMI hotkeys (/dev/input/event5)
[    15.691] (**) Asus WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    15.691] (II) Using input driver 'evdev' for 'Asus WMI hotkeys'
[    15.691] (**) Asus WMI hotkeys: always reports core events
[    15.691] (**) evdev: Asus WMI hotkeys: Device: "/dev/input/event5"
[    15.691] (--) evdev: Asus WMI hotkeys: Vendor 0 Product 0
[    15.691] (--) evdev: Asus WMI hotkeys: Found keys
[    15.691] (II) evdev: Asus WMI hotkeys: Configuring as keyboard
[    15.691] (**) Option "config_info" "udev:/sys/devices/platform/asus-nb-wmi/input/input5/event5"
[    15.691] (II) XINPUT: Adding extended input device "Asus WMI hotkeys" (type: KEYBOARD, id 11)
[    15.691] (**) Option "xkb_rules" "evdev"
[    15.691] (**) Option "xkb_model" "pc105"
[    15.691] (**) Option "xkb_layout" "us"
[    15.691] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    15.691] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    15.691] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    15.691] (**) AT Translated Set 2 keyboard: always reports core events
[    15.691] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    15.691] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    15.691] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    15.691] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    15.691] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    15.691] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 12)
[    15.691] (**) Option "xkb_rules" "evdev"
[    15.691] (**) Option "xkb_model" "pc105"
[    15.691] (**) Option "xkb_layout" "us"
[    15.692] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/event6)
[    15.692] (**) ETPS/2 Elantech Touchpad: Applying InputClass "evdev touchpad catchall"
[    15.692] (**) ETPS/2 Elantech Touchpad: Applying InputClass "touchpad catchall"
[    15.692] (**) ETPS/2 Elantech Touchpad: Applying InputClass "Default clickpad buttons"
[    15.692] (II) LoadModule: "synaptics"
[    15.692] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    15.692] (II) Module synaptics: vendor="X.Org Foundation"
[    15.692] 	compiled for 1.12.3, module version = 1.6.99
[    15.692] 	Module class: X.Org XInput Driver
[    15.692] 	ABI class: X.Org XInput driver, version 16.0
[    15.692] (II) Using input driver 'synaptics' for 'ETPS/2 Elantech Touchpad'
[    15.692] (**) ETPS/2 Elantech Touchpad: always reports core events
[    15.692] (**) Option "Device" "/dev/input/event6"
[    15.692] (--) synaptics: ETPS/2 Elantech Touchpad: x-axis range 0 - 2508
[    15.692] (--) synaptics: ETPS/2 Elantech Touchpad: y-axis range 0 - 1320
[    15.692] (--) synaptics: ETPS/2 Elantech Touchpad: pressure range 0 - 255
[    15.692] (--) synaptics: ETPS/2 Elantech Touchpad: finger width range 0 - 15
[    15.692] (--) synaptics: ETPS/2 Elantech Touchpad: buttons: left right double triple
[    15.692] (--) synaptics: ETPS/2 Elantech Touchpad: Vendor 0x2 Product 0xe
[    15.692] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[    15.692] (**) ETPS/2 Elantech Touchpad: always reports core events
[    15.692] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio4/input/input6/event6"
[    15.692] (II) XINPUT: Adding extended input device "ETPS/2 Elantech Touchpad" (type: TOUCHPAD, id 13)
[    15.692] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MinSpeed is now constant deceleration 2.5
[    15.692] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MaxSpeed is now 1.75
[    15.692] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) AccelFactor is now 0.071
[    15.692] (**) ETPS/2 Elantech Touchpad: (accel) keeping acceleration scheme 1
[    15.692] (**) ETPS/2 Elantech Touchpad: (accel) acceleration profile 1
[    15.692] (**) ETPS/2 Elantech Touchpad: (accel) acceleration factor: 2.000
[    15.692] (**) ETPS/2 Elantech Touchpad: (accel) acceleration threshold: 4
[    15.692] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[    15.693] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/mouse0)
[    15.693] (**) ETPS/2 Elantech Touchpad: Ignoring device from InputClass "touchpad ignore duplicates"
[    16.040] (II) intel(0): EDID vendor "AUO", prod id 9964
[    16.040] (II) intel(0): Printing DDC gathered Modelines:
[    16.040] (II) intel(0): Modeline "1366x768"x0.0   71.80  1366 1414 1446 1526  768 771 777 784 -hsync -vsync (47.1 kHz eP)
[    16.644] (II) intel(0): EDID vendor "AUO", prod id 9964
[    16.644] (II) intel(0): Printing DDC gathered Modelines:
[    16.644] (II) intel(0): Modeline "1366x768"x0.0   71.80  1366 1414 1446 1526  768 771 777 784 -hsync -vsync (47.1 kHz eP)
[    24.929] (II) intel(0): EDID vendor "AUO", prod id 9964
[    24.929] (II) intel(0): Printing DDC gathered Modelines:
[    24.929] (II) intel(0): Modeline "1366x768"x0.0   71.80  1366 1414 1446 1526  768 771 777 784 -hsync -vsync (47.1 kHz eP)
[    25.308] (II) intel(0): EDID vendor "AUO", prod id 9964
[    25.308] (II) intel(0): Printing DDC gathered Modelines:
[    25.308] (II) intel(0): Modeline "1366x768"x0.0   71.80  1366 1414 1446 1526  768 771 777 784 -hsync -vsync (47.1 kHz eP)
[    27.121] (II) intel(0): EDID vendor "AUO", prod id 9964
[    27.121] (II) intel(0): Printing DDC gathered Modelines:
[    27.121] (II) intel(0): Modeline "1366x768"x0.0   71.80  1366 1414 1446 1526  768 771 777 784 -hsync -vsync (47.1 kHz eP)
[    46.602] (II) intel(0): EDID vendor "AUO", prod id 9964
[    46.602] (II) intel(0): Printing DDC gathered Modelines:
[    46.602] (II) intel(0): Modeline "1366x768"x0.0   71.80  1366 1414 1446 1526  768 771 777 784 -hsync -vsync (47.1 kHz eP)

```

Thanks for any insight on how to get to the bottom of this.

---

### Post by Yellow Pasque on 2013-02-19
The problem is that you have two GPU's in a hybrid/Optimus setup.
```
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation Device 1058 (rev ff)

```

You need to completely purge the proprietary nvidia driver, and then follow: [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

---

### Post by Ericj1186 on 2013-02-19
I've tried purging the drivers with sudo apt-get purge nvidia-current, and it removes everything, but nothing changes. Are there any other things to try? I'll give Bumblebee a shot though.

EDIT: I ran sudo apt-get purge nvidia current && sudo apt-get purge nvidia-current-updates. One removed about 204MB, so I restarted then ran the Bumblebee installation. I rebooted, and now, I am back to the same screen as before. My screen is still extra large, no top bar, and no launcher.

---

### Post by Yellow Pasque on 2013-02-19
Okay, so remove the Bumblebee stuff and post the Xorg log. Basically, you need to get your laptop to the point where the graphics function normally using the intel GPU before you can worry about installing bumblebee/nvidia drivers.

---

### Post by Ericj1186 on 2013-02-19
Here's the Xorg logs after I purged Bumblebee.

```

[    21.815] 
X.Org X Server 1.12.4
Release Date: 2012-08-27
[    21.815] X Protocol Version 11, Revision 0
[    21.815] Build Operating System: Linux 2.6.24-32-xen x86_64 Ubuntu
[    21.815] Current Operating System: Linux eric-K53SD 3.5.0-23-generic #35-Ubuntu SMP Thu Jan 24 13:15:40 UTC 2013 x86_64
[    21.815] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-23-generic root=UUID=27886e28-b9af-482e-b4ae-a5a2950659dc ro quiet splash
[    21.815] Build Date: 05 November 2012  10:00:21AM
[    21.815] xorg-server 3:1.12.4+git20121105-makson1~ppa2 (For technical support please see http://www.ubuntu.com/support) 
[    21.815] Current version of pixman: 0.26.0
[    21.815] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    21.815] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    21.815] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Feb 19 22:00:56 2013
[    21.894] (==) Using config file: "/etc/X11/xorg.conf"
[    21.894] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    22.022] (==) ServerLayout "Layout0"
[    22.022] (**) |-->Screen "Screen0" (0)
[    22.022] (**) |   |-->Monitor "Monitor0"
[    22.022] (**) |   |-->Device "Device0"
[    22.022] (**) |-->Input Device "Keyboard0"
[    22.022] (**) |-->Input Device "Mouse0"
[    22.022] (==) Automatically adding devices
[    22.022] (==) Automatically enabling devices
[    22.044] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    22.044] 	Entry deleted from font path.
[    22.044] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    22.044] 	Entry deleted from font path.
[    22.044] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    22.044] 	Entry deleted from font path.
[    22.044] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    22.044] 	Entry deleted from font path.
[    22.044] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    22.044] 	Entry deleted from font path.
[    22.044] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    22.044] 	Entry deleted from font path.
[    22.044] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    22.044] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    22.045] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    22.045] (WW) Disabling Keyboard0
[    22.045] (WW) Disabling Mouse0
[    22.045] (II) Loader magic: 0x7f736cc30b20
[    22.045] (II) Module ABI versions:
[    22.045] 	X.Org ANSI C Emulation: 0.4
[    22.045] 	X.Org Video Driver: 12.2
[    22.045] 	X.Org XInput driver : 16.0
[    22.045] 	X.Org Server Extension : 6.0
[    22.045] (--) PCI:*(0:0:2:0) 8086:0116:1043:1652 rev 9, Mem @ 0xdc400000/4194304, 0xb0000000/268435456, I/O @ 0x0000e000/64
[    22.045] (--) PCI: (0:1:0:0) 10de:1058:1043:1652 rev 161, Mem @ 0xdb000000/16777216, 0xc0000000/134217728, 0xc8000000/33554432, I/O @ 0x0000d000/128, BIOS @ 0x????????/524288
[    22.045] (II) Open ACPI successful (/var/run/acpid.socket)
[    22.045] (II) LoadModule: "extmod"
[    22.246] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    22.326] (II) Module extmod: vendor="X.Org Foundation"
[    22.327] 	compiled for 1.12.4, module version = 1.0.0
[    22.327] 	Module class: X.Org Server Extension
[    22.327] 	ABI class: X.Org Server Extension, version 6.0
[    22.327] (II) Loading extension MIT-SCREEN-SAVER
[    22.327] (II) Loading extension XFree86-VidModeExtension
[    22.327] (II) Loading extension XFree86-DGA
[    22.327] (II) Loading extension DPMS
[    22.328] (II) Loading extension XVideo
[    22.328] (II) Loading extension XVideo-MotionCompensation
[    22.328] (II) Loading extension X-Resource
[    22.328] (II) LoadModule: "dbe"
[    22.328] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    22.428] (II) Module dbe: vendor="X.Org Foundation"
[    22.428] 	compiled for 1.12.4, module version = 1.0.0
[    22.428] 	Module class: X.Org Server Extension
[    22.428] 	ABI class: X.Org Server Extension, version 6.0
[    22.428] (II) Loading extension DOUBLE-BUFFER
[    22.428] (II) LoadModule: "glx"
[    22.429] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    24.587] (II) Module glx: vendor="NVIDIA Corporation"
[    24.587] 	compiled for 4.0.2, module version = 1.0.0
[    24.587] 	Module class: X.Org Server Extension
[    24.587] (II) NVIDIA GLX Module  304.64  Tue Oct 30 11:18:32 PDT 2012
[    24.587] (II) Loading extension GLX
[    24.587] (II) LoadModule: "record"
[    24.587] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    24.615] (II) Module record: vendor="X.Org Foundation"
[    24.615] 	compiled for 1.12.4, module version = 1.13.0
[    24.615] 	Module class: X.Org Server Extension
[    24.615] 	ABI class: X.Org Server Extension, version 6.0
[    24.615] (II) Loading extension RECORD
[    24.615] (II) LoadModule: "dri"
[    24.615] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    24.633] (II) Module dri: vendor="X.Org Foundation"
[    24.633] 	compiled for 1.12.4, module version = 1.0.0
[    24.633] 	ABI class: X.Org Server Extension, version 6.0
[    24.633] (II) Loading extension XFree86-DRI
[    24.633] (II) LoadModule: "dri2"
[    24.633] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    24.634] (II) Module dri2: vendor="X.Org Foundation"
[    24.634] 	compiled for 1.12.4, module version = 1.2.0
[    24.634] 	ABI class: X.Org Server Extension, version 6.0
[    24.634] (II) Loading extension DRI2
[    24.634] (II) LoadModule: "nvidia"
[    24.634] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    24.765] (II) Module nvidia: vendor="NVIDIA Corporation"
[    24.765] 	compiled for 4.0.2, module version = 1.0.0
[    24.765] 	Module class: X.Org Video Driver
[    24.791] (II) NVIDIA dlloader X Driver  304.64  Tue Oct 30 10:59:51 PDT 2012
[    24.791] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    24.803] (++) using VT number 7

[    24.803] (EE) No devices detected.
[    24.803] (==) Matched intel as autoconfigured driver 0
[    24.803] (==) Matched vesa as autoconfigured driver 1
[    24.803] (==) Matched fbdev as autoconfigured driver 2
[    24.803] (==) Assigned the driver to the xf86ConfigLayout
[    24.803] (II) LoadModule: "intel"
[    24.803] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    24.840] (II) Module intel: vendor="X.Org Foundation"
[    24.840] 	compiled for 1.12.3, module version = 2.20.8
[    24.840] 	Module class: X.Org Video Driver
[    24.840] 	ABI class: X.Org Video Driver, version 12.0
[    24.840] (II) LoadModule: "vesa"
[    24.840] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    24.852] (II) Module vesa: vendor="X.Org Foundation"
[    24.852] 	compiled for 1.12.3, module version = 2.3.2
[    24.852] 	Module class: X.Org Video Driver
[    24.852] 	ABI class: X.Org Video Driver, version 12.0
[    24.852] (II) LoadModule: "fbdev"
[    24.882] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    24.905] (II) Module fbdev: vendor="X.Org Foundation"
[    24.905] 	compiled for 1.12.3, module version = 0.4.3
[    24.905] 	Module class: X.Org Video Driver
[    24.905] 	ABI class: X.Org Video Driver, version 12.0
[    24.905] (II) NVIDIA dlloader X Driver  304.64  Tue Oct 30 10:59:51 PDT 2012
[    24.905] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    24.905] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
	Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
	Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
	Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
	Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server,
	Ivybridge Server (GT2), Haswell Desktop (GT1), Haswell Desktop (GT2),
	Haswell Desktop (GT2+), Haswell Mobile (GT1), Haswell Mobile (GT2),
	Haswell Mobile (GT2+), Haswell Server (GT1), Haswell Server (GT2),
	Haswell Server (GT2+), Haswell SDV Desktop (GT1),
	Haswell SDV Desktop (GT2), Haswell SDV Desktop (GT2+),
	Haswell SDV Mobile (GT1), Haswell SDV Mobile (GT2),
	Haswell SDV Mobile (GT2+), Haswell SDV Server (GT1),
	Haswell SDV Server (GT2), Haswell SDV Server (GT2+),
	Haswell ULT Desktop (GT1), Haswell ULT Desktop (GT2),
	Haswell ULT Desktop (GT2+), Haswell ULT Mobile (GT1),
	Haswell ULT Mobile (GT2), Haswell ULT Mobile (GT2+),
	Haswell ULT Server (GT1), Haswell ULT Server (GT2),
	Haswell ULT Server (GT2+), Haswell CRW Desktop (GT1),
	Haswell CRW Desktop (GT2), Haswell CRW Desktop (GT2+),
	Haswell CRW Mobile (GT1), Haswell CRW Mobile (GT2),
	Haswell CRW Mobile (GT2+), Haswell CRW Server (GT1),
	Haswell CRW Server (GT2), Haswell CRW Server (GT2+),
	ValleyView PO board
[    24.905] (II) VESA: driver for VESA chipsets: vesa
[    24.905] (II) FBDEV: driver for framebuffer: fbdev
[    24.905] (++) using VT number 7

[    24.905] (WW) xf86OpenConsole: setpgid failed: Operation not permitted
[    24.905] (WW) xf86OpenConsole: setsid failed: Operation not permitted
[    24.905] drmOpenDevice: node name is /dev/dri/card0
[    24.905] drmOpenDevice: open result is 9, (OK)
[    24.905] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    24.905] drmOpenDevice: node name is /dev/dri/card0
[    24.906] drmOpenDevice: open result is 9, (OK)
[    24.906] drmOpenByBusid: drmOpenMinor returns 9
[    24.906] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    24.923] (II) intel(0): SNA compiled: xserver-xorg-video-intel 3:2.20.8+git20120928~quantal2 (Tomasz Makarewicz <makson96@gmail.com>)
[    24.923] (WW) Falling back to old probe method for vesa
[    24.924] (WW) Falling back to old probe method for fbdev
[    24.924] (II) Loading sub module "fbdevhw"
[    24.924] (II) LoadModule: "fbdevhw"
[    24.924] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    24.940] (II) Module fbdevhw: vendor="X.Org Foundation"
[    24.940] 	compiled for 1.12.4, module version = 0.0.2
[    24.940] 	ABI class: X.Org Video Driver, version 12.2
[    24.941] drmOpenDevice: node name is /dev/dri/card0
[    24.941] drmOpenDevice: open result is 10, (OK)
[    24.941] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    24.941] drmOpenDevice: node name is /dev/dri/card0
[    24.941] drmOpenDevice: open result is 10, (OK)
[    24.941] drmOpenByBusid: drmOpenMinor returns 10
[    24.941] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    24.941] (**) intel(0): Depth 24, (--) framebuffer bpp 32
[    24.941] (==) intel(0): RGB weight 888
[    24.941] (==) intel(0): Default visual is TrueColor
[    24.941] (--) intel(0): Integrated Graphics Chipset: Intel(R) Sandybridge Mobile (GT2)
[    24.941] (**) intel(0): Framebuffer tiled
[    24.941] (**) intel(0): Pixmaps tiled
[    24.941] (**) intel(0): 3D buffers tiled
[    24.941] (**) intel(0): Throttling enabled
[    24.941] (**) intel(0): Delayed flush enabled
[    24.941] (**) intel(0): "Tear free" disabled
[    24.941] (**) intel(0): Forcing per-crtc-pixmaps? no
[    24.941] (II) intel(0): Output LVDS1 using monitor section Monitor0
[    24.941] (--) intel(0): found backlight control interface acpi_video1 (type 'firmware')
[    24.941] (II) intel(0): Output VGA1 has no monitor section
[    24.956] (II) intel(0): Output HDMI1 has no monitor section
[    25.004] (II) intel(0): Output DP1 has no monitor section
[    25.004] (II) intel(0): EDID for output LVDS1
[    25.004] (II) intel(0): Manufacturer: AUO  Model: 26ec  Serial#: 0
[    25.004] (II) intel(0): Year: 2009  Week: 1
[    25.004] (II) intel(0): EDID Version: 1.3
[    25.004] (II) intel(0): Digital Display Input
[    25.004] (II) intel(0): Max Image Size [cm]: horiz.: 34  vert.: 19
[    25.004] (II) intel(0): Gamma: 2.20
[    25.004] (II) intel(0): No DPMS capabilities specified
[    25.004] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    25.004] (II) intel(0): First detailed timing is preferred mode
[    25.004] (II) intel(0): redX: 0.577 redY: 0.333   greenX: 0.333 greenY: 0.554
[    25.004] (II) intel(0): blueX: 0.161 blueY: 0.144   whiteX: 0.313 whiteY: 0.329
[    25.004] (II) intel(0): Manufacturer's mask: 0
[    25.004] (II) intel(0): Supported detailed timing:
[    25.004] (II) intel(0): clock: 71.8 MHz   Image Size:  344 x 193 mm
[    25.004] (II) intel(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1526 h_border: 0
[    25.004] (II) intel(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 784 v_border: 0
[    25.004] (II) intel(0): Unknown vendor-specific block f
[    25.004] (II) intel(0):  AUO
[    25.004] (II) intel(0):  B156XW02 V6
[    25.004] (II) intel(0): EDID (in hex):
[    25.004] (II) intel(0): 	00ffffffffffff0006afec2600000000
[    25.004] (II) intel(0): 	01130103802213780ad7759355558d29
[    25.004] (II) intel(0): 	24505400000001010101010101010101
[    25.004] (II) intel(0): 	0101010101010c1c56a0500010303020
[    25.004] (II) intel(0): 	360058c1100000180000000f00000000
[    25.004] (II) intel(0): 	00000000000000000020000000fe0041
[    25.004] (II) intel(0): 	554f0a202020202020202020000000fe
[    25.004] (II) intel(0): 	004231353658573032205636200a0065
[    25.004] (II) intel(0): EDID vendor "AUO", prod id 9964
[    25.004] (II) intel(0): Printing DDC gathered Modelines:
[    25.004] (II) intel(0): Modeline "1366x768"x0.0   71.80  1366 1414 1446 1526  768 771 777 784 -hsync -vsync (47.1 kHz eP)
[    25.004] (II) intel(0): Not using mode "1366x768" (hsync out of range)
[    25.004] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    25.004] (II) intel(0): Not using default mode "800x600" (hsync out of range)
[    25.004] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    25.004] (II) intel(0): Not using default mode "800x600" (hsync out of range)
[    25.004] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    25.004] (II) intel(0): Not using default mode "1024x768" (hsync out of range)
[    25.004] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    25.004] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    25.004] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    25.004] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    25.004] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    25.004] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    25.004] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    25.004] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    25.004] (II) intel(0): Not using default mode "1360x768" (hsync out of range)
[    25.004] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    25.004] (II) intel(0): Not using default mode "1360x768" (hsync out of range)
[    25.004] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    25.004] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    25.004] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    25.004] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    25.004] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    25.004] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    25.004] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    25.004] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    25.004] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    25.004] (II) intel(0): Printing probed modes for output LVDS1
[    25.004] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz d)
[    25.004] (II) intel(0): EDID for output VGA1
[    25.020] (II) intel(0): EDID for output HDMI1
[    25.068] (II) intel(0): EDID for output DP1
[    25.068] (II) intel(0): Output LVDS1 connected
[    25.068] (II) intel(0): Output VGA1 disconnected
[    25.068] (II) intel(0): Output HDMI1 disconnected
[    25.068] (II) intel(0): Output DP1 disconnected
[    25.068] (II) intel(0): Using exact sizes for initial modes
[    25.068] (II) intel(0): Output LVDS1 using initial mode 640x480
[    25.068] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    25.068] (**) intel(0): Display dimensions: (340, 190) mm
[    25.068] (**) intel(0): DPI set to (47, 64)
[    25.068] (II) Loading sub module "dri2"
[    25.068] (II) LoadModule: "dri2"
[    25.068] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    25.068] (II) Module dri2: vendor="X.Org Foundation"
[    25.068] 	compiled for 1.12.4, module version = 1.2.0
[    25.068] 	ABI class: X.Org Server Extension, version 6.0
[    25.068] (II) UnloadModule: "nvidia"
[    25.068] (II) Unloading nvidia
[    25.068] (II) UnloadModule: "vesa"
[    25.068] (II) Unloading vesa
[    25.068] (II) UnloadModule: "fbdev"
[    25.068] (II) Unloading fbdev
[    25.068] (II) UnloadSubModule: "fbdevhw"
[    25.068] (II) Unloading fbdevhw
[    25.068] (==) Depth 24 pixmap format is 32 bpp
[    25.083] (II) intel(0): SNA initialized with SandyBridge backend
[    25.083] (==) intel(0): Backing store disabled
[    25.083] (==) intel(0): Silken mouse enabled
[    25.083] (II) intel(0): HW Cursor enabled
[    25.083] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    25.084] (**) intel(0): DPMS enabled
[    25.085] (II) intel(0): [DRI2] Setup complete
[    25.085] (II) intel(0): [DRI2]   DRI driver: i965
[    25.085] (II) intel(0): direct rendering: DRI2 Enabled
[    25.085] (==) intel(0): hotplug detection: "enabled"
[    25.085] (--) RandR disabled
[    25.085] (II) Initializing built-in extension Generic Event Extension
[    25.085] (II) Initializing built-in extension SHAPE
[    25.085] (II) Initializing built-in extension MIT-SHM
[    25.085] (II) Initializing built-in extension XInputExtension
[    25.085] (II) Initializing built-in extension XTEST
[    25.085] (II) Initializing built-in extension BIG-REQUESTS
[    25.085] (II) Initializing built-in extension SYNC
[    25.085] (II) Initializing built-in extension XKEYBOARD
[    25.085] (II) Initializing built-in extension XC-MISC
[    25.085] (II) Initializing built-in extension SECURITY
[    25.085] (II) Initializing built-in extension XINERAMA
[    25.085] (II) Initializing built-in extension XFIXES
[    25.085] (II) Initializing built-in extension RENDER
[    25.085] (II) Initializing built-in extension RANDR
[    25.085] (II) Initializing built-in extension COMPOSITE
[    25.085] (II) Initializing built-in extension DAMAGE
[    25.104] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
[    25.124] (II) intel(0): switch to mode 640x480 on crtc 3 (pipe 0)
[    25.398] (II) intel(0): Setting screen physical size to 169 x 127
[    25.544] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    25.571] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    25.571] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    25.571] (II) LoadModule: "evdev"
[    25.571] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.612] (II) Module evdev: vendor="X.Org Foundation"
[    25.612] 	compiled for 1.12.3, module version = 2.7.0
[    25.612] 	Module class: X.Org XInput Driver
[    25.612] 	ABI class: X.Org XInput driver, version 16.0
[    25.612] (II) Using input driver 'evdev' for 'Power Button'
[    25.612] (**) Power Button: always reports core events
[    25.612] (**) evdev: Power Button: Device: "/dev/input/event2"
[    25.612] (--) evdev: Power Button: Vendor 0 Product 0x1
[    25.612] (--) evdev: Power Button: Found keys
[    25.612] (II) evdev: Power Button: Configuring as keyboard
[    25.612] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    25.612] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    25.612] (**) Option "xkb_rules" "evdev"
[    25.612] (**) Option "xkb_model" "pc105"
[    25.612] (**) Option "xkb_layout" "us"
[    25.612] (II) config/udev: Adding input device Video Bus (/dev/input/event7)
[    25.612] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    25.612] (II) Using input driver 'evdev' for 'Video Bus'
[    25.612] (**) Video Bus: always reports core events
[    25.612] (**) evdev: Video Bus: Device: "/dev/input/event7"
[    25.612] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    25.612] (--) evdev: Video Bus: Found keys
[    25.612] (II) evdev: Video Bus: Configuring as keyboard
[    25.612] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input7/event7"
[    25.612] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    25.612] (**) Option "xkb_rules" "evdev"
[    25.612] (**) Option "xkb_model" "pc105"
[    25.612] (**) Option "xkb_layout" "us"
[    25.613] (II) config/udev: Adding input device Video Bus (/dev/input/event6)
[    25.613] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    25.613] (II) Using input driver 'evdev' for 'Video Bus'
[    25.613] (**) Video Bus: always reports core events
[    25.613] (**) evdev: Video Bus: Device: "/dev/input/event6"
[    25.613] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    25.613] (--) evdev: Video Bus: Found keys
[    25.613] (II) evdev: Video Bus: Configuring as keyboard
[    25.613] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input6/event6"
[    25.613] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 8)
[    25.613] (**) Option "xkb_rules" "evdev"
[    25.613] (**) Option "xkb_model" "pc105"
[    25.613] (**) Option "xkb_layout" "us"
[    25.613] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    25.613] (II) No input driver specified, ignoring this device.
[    25.613] (II) This device may have been added with another device file.
[    25.613] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    25.613] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    25.613] (II) Using input driver 'evdev' for 'Sleep Button'
[    25.613] (**) Sleep Button: always reports core events
[    25.613] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[    25.613] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    25.613] (--) evdev: Sleep Button: Found keys
[    25.613] (II) evdev: Sleep Button: Configuring as keyboard
[    25.613] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1/event1"
[    25.613] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[    25.613] (**) Option "xkb_rules" "evdev"
[    25.613] (**) Option "xkb_model" "pc105"
[    25.613] (**) Option "xkb_layout" "us"
[    25.613] (II) config/udev: Adding input device ASUS USB2.0 WebCam (/dev/input/event8)
[    25.613] (**) ASUS USB2.0 WebCam: Applying InputClass "evdev keyboard catchall"
[    25.613] (II) Using input driver 'evdev' for 'ASUS USB2.0 WebCam'
[    25.613] (**) ASUS USB2.0 WebCam: always reports core events
[    25.613] (**) evdev: ASUS USB2.0 WebCam: Device: "/dev/input/event8"
[    25.613] (--) evdev: ASUS USB2.0 WebCam: Vendor 0x58f Product 0xa014
[    25.613] (--) evdev: ASUS USB2.0 WebCam: Found keys
[    25.613] (II) evdev: ASUS USB2.0 WebCam: Configuring as keyboard
[    25.613] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input8/event8"
[    25.613] (II) XINPUT: Adding extended input device "ASUS USB2.0 WebCam" (type: KEYBOARD, id 10)
[    25.613] (**) Option "xkb_rules" "evdev"
[    25.613] (**) Option "xkb_model" "pc105"
[    25.614] (**) Option "xkb_layout" "us"
[    25.614] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event10)
[    25.614] (II) No input driver specified, ignoring this device.
[    25.614] (II) This device may have been added with another device file.
[    25.614] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event11)
[    25.614] (II) No input driver specified, ignoring this device.
[    25.614] (II) This device may have been added with another device file.
[    25.614] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event9)
[    25.614] (II) No input driver specified, ignoring this device.
[    25.614] (II) This device may have been added with another device file.
[    25.614] (II) config/udev: Adding input device Asus WMI hotkeys (/dev/input/event4)
[    25.614] (**) Asus WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    25.614] (II) Using input driver 'evdev' for 'Asus WMI hotkeys'
[    25.614] (**) Asus WMI hotkeys: always reports core events
[    25.614] (**) evdev: Asus WMI hotkeys: Device: "/dev/input/event4"
[    25.614] (--) evdev: Asus WMI hotkeys: Vendor 0 Product 0
[    25.614] (--) evdev: Asus WMI hotkeys: Found keys
[    25.614] (II) evdev: Asus WMI hotkeys: Configuring as keyboard
[    25.614] (**) Option "config_info" "udev:/sys/devices/platform/asus-nb-wmi/input/input4/event4"
[    25.614] (II) XINPUT: Adding extended input device "Asus WMI hotkeys" (type: KEYBOARD, id 11)
[    25.614] (**) Option "xkb_rules" "evdev"
[    25.614] (**) Option "xkb_model" "pc105"
[    25.614] (**) Option "xkb_layout" "us"
[    25.615] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    25.615] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    25.615] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    25.615] (**) AT Translated Set 2 keyboard: always reports core events
[    25.615] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    25.615] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    25.615] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    25.615] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    25.615] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    25.615] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 12)
[    25.615] (**) Option "xkb_rules" "evdev"
[    25.615] (**) Option "xkb_model" "pc105"
[    25.615] (**) Option "xkb_layout" "us"
[    25.615] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/event5)
[    25.615] (**) ETPS/2 Elantech Touchpad: Applying InputClass "evdev touchpad catchall"
[    25.615] (**) ETPS/2 Elantech Touchpad: Applying InputClass "touchpad catchall"
[    25.615] (**) ETPS/2 Elantech Touchpad: Applying InputClass "Default clickpad buttons"
[    25.615] (II) LoadModule: "synaptics"
[    25.615] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    25.616] (II) Module synaptics: vendor="X.Org Foundation"
[    25.616] 	compiled for 1.12.3, module version = 1.6.99
[    25.616] 	Module class: X.Org XInput Driver
[    25.616] 	ABI class: X.Org XInput driver, version 16.0
[    25.616] (II) Using input driver 'synaptics' for 'ETPS/2 Elantech Touchpad'
[    25.616] (**) ETPS/2 Elantech Touchpad: always reports core events
[    25.616] (**) Option "Device" "/dev/input/event5"
[    25.616] (--) synaptics: ETPS/2 Elantech Touchpad: x-axis range 0 - 2508
[    25.616] (--) synaptics: ETPS/2 Elantech Touchpad: y-axis range 0 - 1320
[    25.616] (--) synaptics: ETPS/2 Elantech Touchpad: pressure range 0 - 255
[    25.616] (--) synaptics: ETPS/2 Elantech Touchpad: finger width range 0 - 15
[    25.616] (--) synaptics: ETPS/2 Elantech Touchpad: buttons: left right double triple
[    25.616] (--) synaptics: ETPS/2 Elantech Touchpad: Vendor 0x2 Product 0xe
[    25.616] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[    25.616] (**) ETPS/2 Elantech Touchpad: always reports core events
[    25.616] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio4/input/input5/event5"
[    25.616] (II) XINPUT: Adding extended input device "ETPS/2 Elantech Touchpad" (type: TOUCHPAD, id 13)
[    25.616] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MinSpeed is now constant deceleration 2.5
[    25.616] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MaxSpeed is now 1.75
[    25.616] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) AccelFactor is now 0.071
[    25.617] (**) ETPS/2 Elantech Touchpad: (accel) keeping acceleration scheme 1
[    25.617] (**) ETPS/2 Elantech Touchpad: (accel) acceleration profile 1
[    25.617] (**) ETPS/2 Elantech Touchpad: (accel) acceleration factor: 2.000
[    25.617] (**) ETPS/2 Elantech Touchpad: (accel) acceleration threshold: 4
[    25.617] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[    25.617] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/mouse0)
[    25.617] (**) ETPS/2 Elantech Touchpad: Ignoring device from InputClass "touchpad ignore duplicates"
[    30.164] (II) intel(0): EDID vendor "AUO", prod id 9964
[    30.164] (II) intel(0): Printing DDC gathered Modelines:
[    30.164] (II) intel(0): Modeline "1366x768"x0.0   71.80  1366 1414 1446 1526  768 771 777 784 -hsync -vsync (47.1 kHz eP)
[    35.188] (II) intel(0): EDID vendor "AUO", prod id 9964
[    35.188] (II) intel(0): Printing DDC gathered Modelines:
[    35.188] (II) intel(0): Modeline "1366x768"x0.0   71.80  1366 1414 1446 1526  768 771 777 784 -hsync -vsync (47.1 kHz eP)
[    44.024] (II) intel(0): EDID vendor "AUO", prod id 9964
[    44.024] (II) intel(0): Printing DDC gathered Modelines:
[    44.024] (II) intel(0): Modeline "1366x768"x0.0   71.80  1366 1414 1446 1526  768 771 777 784 -hsync -vsync (47.1 kHz eP)
[    44.404] (II) intel(0): EDID vendor "AUO", prod id 9964
[    44.404] (II) intel(0): Printing DDC gathered Modelines:
[    44.405] (II) intel(0): Modeline "1366x768"x0.0   71.80  1366 1414 1446 1526  768 771 777 784 -hsync -vsync (47.1 kHz eP)
[    46.015] (II) intel(0): EDID vendor "AUO", prod id 9964
[    46.015] (II) intel(0): Printing DDC gathered Modelines:
[    46.015] (II) intel(0): Modeline "1366x768"x0.0   71.80  1366 1414 1446 1526  768 771 777 784 -hsync -vsync (47.1 kHz eP)
[    66.271] (II) intel(0): EDID vendor "AUO", prod id 9964
[    66.271] (II) intel(0): Printing DDC gathered Modelines:
[    66.271] (II) intel(0): Modeline "1366x768"x0.0   71.80  1366 1414 1446 1526  768 771 777 784 -hsync -vsync (47.1 kHz eP)


```

---

### Post by Yellow Pasque on 2013-02-19
You still have part of the nvidia driver installed...:
```
[    22.429] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    24.587] (II) Module glx: vendor="NVIDIA Corporation"
[    24.587] 	compiled for 4.0.2, module version = 1.0.0
[    24.587] 	Module class: X.Org Server Extension
[    24.587] (II) NVIDIA GLX Module  304.64  Tue Oct 30 11:18:32 PDT 2012
```

---

### Post by Ericj1186 on 2013-02-20
How do I remove that part?

---

### Post by Yellow Pasque on 2013-02-20
> **Ericj1186 said:**
> How do I remove that part?
It depends on how you installed it... so you tell me. :P

Generally, this helps:
```
sudo apt-get purge nvidia*
sudo apt-get install --reinstall libgl1-mesa-glx xserver-xorg-core
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

If you downloaded a driver straight from nvidia or manually installed the driver, then you'll probably have more work to do.

---

### Post by Ericj1186 on 2013-02-20
I did it via apt-get first, that caused my issues, I removed it via a tutorial and then did it with Nvidia's website, as far as I am aware, THAT is the one installed.

---

### Post by Yellow Pasque on 2013-02-20
I'm not an expert on nvidia cards, but I think this works:
```
sudo nvidia-installer --uninstall
```

---

### Post by Ericj1186 on 2013-02-20
That ran successfully, but when I rebooted only my resolution got better. Still no top bar or Unity launcher.

Xorg.0.log

```

[    20.523] 
X.Org X Server 1.12.4
Release Date: 2012-08-27
[    20.523] X Protocol Version 11, Revision 0
[    20.523] Build Operating System: Linux 2.6.24-32-xen x86_64 Ubuntu
[    20.523] Current Operating System: Linux eric-K53SD 3.5.0-23-generic #35-Ubuntu SMP Thu Jan 24 13:15:40 UTC 2013 x86_64
[    20.523] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-23-generic root=UUID=27886e28-b9af-482e-b4ae-a5a2950659dc ro quiet splash
[    20.523] Build Date: 05 November 2012  10:00:21AM
[    20.523] xorg-server 3:1.12.4+git20121105-makson1~ppa2 (For technical support please see http://www.ubuntu.com/support) 
[    20.523] Current version of pixman: 0.26.0
[    20.523]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    20.523] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    20.523] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Feb 20 20:18:44 2013
[    20.554] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    20.554] (==) No Layout section.  Using the first Screen section.
[    20.554] (==) No screen section available. Using defaults.
[    20.554] (**) |-->Screen "Default Screen Section" (0)
[    20.554] (**) |   |-->Monitor "<default monitor>"
[    20.554] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    20.554] (==) Automatically adding devices
[    20.554] (==) Automatically enabling devices
[    20.554] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    20.554]     Entry deleted from font path.
[    20.554] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    20.554]     Entry deleted from font path.
[    20.554] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    20.554]     Entry deleted from font path.
[    20.554] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    20.554]     Entry deleted from font path.
[    20.554] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    20.554]     Entry deleted from font path.
[    20.554] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    20.554]     Entry deleted from font path.
[    20.554] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    20.554] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    20.554] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    20.554] (II) Loader magic: 0x7f0e1ff02b20
[    20.554] (II) Module ABI versions:
[    20.554]     X.Org ANSI C Emulation: 0.4
[    20.554]     X.Org Video Driver: 12.2
[    20.554]     X.Org XInput driver : 16.0
[    20.554]     X.Org Server Extension : 6.0
[    20.555] (--) PCI:*(0:0:2:0) 8086:0116:1043:1652 rev 9, Mem @ 0xdc400000/4194304, 0xb0000000/268435456, I/O @ 0x0000e000/64
[    20.555] (--) PCI: (0:1:0:0) 10de:1058:1043:1652 rev 161, Mem @ 0xdb000000/16777216, 0xc0000000/134217728, 0xc8000000/33554432, I/O @ 0x0000d000/128, BIOS @ 0x????????/524288
[    20.555] (II) Open ACPI successful (/var/run/acpid.socket)
[    20.555] (II) LoadModule: "extmod"
[    20.555] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    20.555] (II) Module extmod: vendor="X.Org Foundation"
[    20.555]     compiled for 1.12.4, module version = 1.0.0
[    20.555]     Module class: X.Org Server Extension
[    20.555]     ABI class: X.Org Server Extension, version 6.0
[    20.555] (II) Loading extension MIT-SCREEN-SAVER
[    20.555] (II) Loading extension XFree86-VidModeExtension
[    20.555] (II) Loading extension XFree86-DGA
[    20.555] (II) Loading extension DPMS
[    20.555] (II) Loading extension XVideo
[    20.555] (II) Loading extension XVideo-MotionCompensation
[    20.555] (II) Loading extension X-Resource
[    20.555] (II) LoadModule: "dbe"
[    20.555] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    20.555] (II) Module dbe: vendor="X.Org Foundation"
[    20.555]     compiled for 1.12.4, module version = 1.0.0
[    20.555]     Module class: X.Org Server Extension
[    20.555]     ABI class: X.Org Server Extension, version 6.0
[    20.555] (II) Loading extension DOUBLE-BUFFER
[    20.555] (II) LoadModule: "glx"
[    20.555] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    20.561] (II) Module glx: vendor="NVIDIA Corporation"
[    20.561]     compiled for 4.0.2, module version = 1.0.0
[    20.561]     Module class: X.Org Server Extension
[    20.561] (II) NVIDIA GLX Module  304.64  Tue Oct 30 11:18:32 PDT 2012
[    20.561] (II) Loading extension GLX
[    20.561] (II) LoadModule: "record"
[    20.561] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    20.561] (II) Module record: vendor="X.Org Foundation"
[    20.561]     compiled for 1.12.4, module version = 1.13.0
[    20.561]     Module class: X.Org Server Extension
[    20.561]     ABI class: X.Org Server Extension, version 6.0
[    20.561] (II) Loading extension RECORD
[    20.561] (II) LoadModule: "dri"
[    20.561] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    20.562] (II) Module dri: vendor="X.Org Foundation"
[    20.562]     compiled for 1.12.4, module version = 1.0.0
[    20.562]     ABI class: X.Org Server Extension, version 6.0
[    20.562] (II) Loading extension XFree86-DRI
[    20.562] (II) LoadModule: "dri2"
[    20.562] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    20.562] (II) Module dri2: vendor="X.Org Foundation"
[    20.562]     compiled for 1.12.4, module version = 1.2.0
[    20.562]     ABI class: X.Org Server Extension, version 6.0
[    20.562] (II) Loading extension DRI2
[    20.562] (==) Matched intel as autoconfigured driver 0
[    20.562] (==) Matched vesa as autoconfigured driver 1
[    20.562] (==) Matched fbdev as autoconfigured driver 2
[    20.562] (==) Assigned the driver to the xf86ConfigLayout
[    20.562] (II) LoadModule: "intel"
[    20.562] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    20.562] (II) Module intel: vendor="X.Org Foundation"
[    20.562]     compiled for 1.12.3, module version = 2.20.8
[    20.562]     Module class: X.Org Video Driver
[    20.562]     ABI class: X.Org Video Driver, version 12.0
[    20.562] (II) LoadModule: "vesa"
[    20.562] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    20.562] (II) Module vesa: vendor="X.Org Foundation"
[    20.562]     compiled for 1.12.3, module version = 2.3.2
[    20.562]     Module class: X.Org Video Driver
[    20.562]     ABI class: X.Org Video Driver, version 12.0
[    20.562] (II) LoadModule: "fbdev"
[    20.562] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    20.562] (II) Module fbdev: vendor="X.Org Foundation"
[    20.562]     compiled for 1.12.3, module version = 0.4.3
[    20.562]     Module class: X.Org Video Driver
[    20.562]     ABI class: X.Org Video Driver, version 12.0
[    20.562] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
    Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
    Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
    Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
    Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server,
    Ivybridge Server (GT2), Haswell Desktop (GT1), Haswell Desktop (GT2),
    Haswell Desktop (GT2+), Haswell Mobile (GT1), Haswell Mobile (GT2),
    Haswell Mobile (GT2+), Haswell Server (GT1), Haswell Server (GT2),
    Haswell Server (GT2+), Haswell SDV Desktop (GT1),
    Haswell SDV Desktop (GT2), Haswell SDV Desktop (GT2+),
    Haswell SDV Mobile (GT1), Haswell SDV Mobile (GT2),
    Haswell SDV Mobile (GT2+), Haswell SDV Server (GT1),
    Haswell SDV Server (GT2), Haswell SDV Server (GT2+),
    Haswell ULT Desktop (GT1), Haswell ULT Desktop (GT2),
    Haswell ULT Desktop (GT2+), Haswell ULT Mobile (GT1),
    Haswell ULT Mobile (GT2), Haswell ULT Mobile (GT2+),
    Haswell ULT Server (GT1), Haswell ULT Server (GT2),
    Haswell ULT Server (GT2+), Haswell CRW Desktop (GT1),
    Haswell CRW Desktop (GT2), Haswell CRW Desktop (GT2+),
    Haswell CRW Mobile (GT1), Haswell CRW Mobile (GT2),
    Haswell CRW Mobile (GT2+), Haswell CRW Server (GT1),
    Haswell CRW Server (GT2), Haswell CRW Server (GT2+),
    ValleyView PO board
[    20.563] (II) VESA: driver for VESA chipsets: vesa
[    20.563] (II) FBDEV: driver for framebuffer: fbdev
[    20.563] (++) using VT number 7

[    20.563] drmOpenDevice: node name is /dev/dri/card0
[    20.563] drmOpenDevice: open result is 8, (OK)
[    20.563] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    20.563] drmOpenDevice: node name is /dev/dri/card0
[    20.563] drmOpenDevice: open result is 8, (OK)
[    20.563] drmOpenByBusid: drmOpenMinor returns 8
[    20.563] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    20.563] (II) intel(0): SNA compiled: xserver-xorg-video-intel 3:2.20.8+git20120928~quantal2 (Tomasz Makarewicz <makson96@gmail.com>)
[    20.563] (WW) Falling back to old probe method for vesa
[    20.563] (WW) Falling back to old probe method for fbdev
[    20.563] (II) Loading sub module "fbdevhw"
[    20.563] (II) LoadModule: "fbdevhw"
[    20.563] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    20.563] (II) Module fbdevhw: vendor="X.Org Foundation"
[    20.563]     compiled for 1.12.4, module version = 0.0.2
[    20.563]     ABI class: X.Org Video Driver, version 12.2
[    20.563] drmOpenDevice: node name is /dev/dri/card0
[    20.563] drmOpenDevice: open result is 9, (OK)
[    20.563] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    20.563] drmOpenDevice: node name is /dev/dri/card0
[    20.563] drmOpenDevice: open result is 9, (OK)
[    20.563] drmOpenByBusid: drmOpenMinor returns 9
[    20.563] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    20.563] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    20.563] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    20.563] (==) intel(0): RGB weight 888
[    20.563] (==) intel(0): Default visual is TrueColor
[    20.563] (--) intel(0): Integrated Graphics Chipset: Intel(R) Sandybridge Mobile (GT2)
[    20.563] (**) intel(0): Framebuffer tiled
[    20.563] (**) intel(0): Pixmaps tiled
[    20.563] (**) intel(0): 3D buffers tiled
[    20.563] (**) intel(0): Throttling enabled
[    20.563] (**) intel(0): Delayed flush enabled
[    20.563] (**) intel(0): "Tear free" disabled
[    20.563] (**) intel(0): Forcing per-crtc-pixmaps? no
[    20.563] (II) intel(0): Output LVDS1 has no monitor section
[    20.564] (--) intel(0): found backlight control interface acpi_video1 (type 'firmware')
[    20.564] (II) intel(0): Output VGA1 has no monitor section
[    20.580] (II) intel(0): Output HDMI1 has no monitor section
[    20.628] (II) intel(0): Output DP1 has no monitor section
[    20.628] (II) intel(0): EDID for output LVDS1
[    20.628] (II) intel(0): Manufacturer: AUO  Model: 26ec  Serial#: 0
[    20.628] (II) intel(0): Year: 2009  Week: 1
[    20.628] (II) intel(0): EDID Version: 1.3
[    20.628] (II) intel(0): Digital Display Input
[    20.628] (II) intel(0): Max Image Size [cm]: horiz.: 34  vert.: 19
[    20.628] (II) intel(0): Gamma: 2.20
[    20.628] (II) intel(0): No DPMS capabilities specified
[    20.628] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    20.628] (II) intel(0): First detailed timing is preferred mode
[    20.628] (II) intel(0): redX: 0.577 redY: 0.333   greenX: 0.333 greenY: 0.554
[    20.628] (II) intel(0): blueX: 0.161 blueY: 0.144   whiteX: 0.313 whiteY: 0.329
[    20.628] (II) intel(0): Manufacturer's mask: 0
[    20.628] (II) intel(0): Supported detailed timing:
[    20.628] (II) intel(0): clock: 71.8 MHz   Image Size:  344 x 193 mm
[    20.628] (II) intel(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1526 h_border: 0
[    20.628] (II) intel(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 784 v_border: 0
[    20.628] (II) intel(0): Unknown vendor-specific block f
[    20.628] (II) intel(0):  AUO
[    20.628] (II) intel(0):  B156XW02 V6
[    20.628] (II) intel(0): EDID (in hex):
[    20.628] (II) intel(0):     00ffffffffffff0006afec2600000000
[    20.628] (II) intel(0):     01130103802213780ad7759355558d29
[    20.628] (II) intel(0):     24505400000001010101010101010101
[    20.628] (II) intel(0):     0101010101010c1c56a0500010303020
[    20.628] (II) intel(0):     360058c1100000180000000f00000000
[    20.628] (II) intel(0):     00000000000000000020000000fe0041
[    20.628] (II) intel(0):     554f0a202020202020202020000000fe
[    20.628] (II) intel(0):     004231353658573032205636200a0065
[    20.628] (II) intel(0): EDID vendor "AUO", prod id 9964
[    20.628] (II) intel(0): Printing DDC gathered Modelines:
[    20.628] (II) intel(0): Modeline "1366x768"x0.0   71.80  1366 1414 1446 1526  768 771 777 784 -hsync -vsync (47.1 kHz eP)
[    20.628] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    20.628] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    20.628] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    20.628] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    20.628] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    20.628] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    20.628] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    20.628] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    20.628] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    20.628] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    20.628] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    20.628] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    20.628] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    20.628] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    20.628] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    20.628] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    20.628] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    20.628] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    20.628] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    20.628] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    20.628] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    20.628] (II) intel(0): Printing probed modes for output LVDS1
[    20.628] (II) intel(0): Modeline "1366x768"x60.0   71.80  1366 1414 1446 1526  768 771 777 784 -hsync -vsync (47.1 kHz eP)
[    20.628] (II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz d)
[    20.628] (II) intel(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz d)
[    20.628] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz d)
[    20.628] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz d)
[    20.628] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz d)
[    20.628] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz d)
[    20.628] (II) intel(0): EDID for output VGA1
[    20.644] (II) intel(0): EDID for output HDMI1
[    20.692] (II) intel(0): EDID for output DP1
[    20.692] (II) intel(0): Output LVDS1 connected
[    20.692] (II) intel(0): Output VGA1 disconnected
[    20.692] (II) intel(0): Output HDMI1 disconnected
[    20.692] (II) intel(0): Output DP1 disconnected
[    20.692] (II) intel(0): Using exact sizes for initial modes
[    20.692] (II) intel(0): Output LVDS1 using initial mode 1366x768
[    20.692] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    20.692] (**) intel(0): Display dimensions: (340, 190) mm
[    20.692] (**) intel(0): DPI set to (102, 102)
[    20.692] (II) Loading sub module "dri2"
[    20.692] (II) LoadModule: "dri2"
[    20.692] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    20.692] (II) Module dri2: vendor="X.Org Foundation"
[    20.692]     compiled for 1.12.4, module version = 1.2.0
[    20.692]     ABI class: X.Org Server Extension, version 6.0
[    20.692] (II) UnloadModule: "vesa"
[    20.692] (II) Unloading vesa
[    20.692] (II) UnloadModule: "fbdev"
[    20.692] (II) Unloading fbdev
[    20.692] (II) UnloadSubModule: "fbdevhw"
[    20.692] (II) Unloading fbdevhw
[    20.692] (==) Depth 24 pixmap format is 32 bpp
[    20.692] (II) intel(0): SNA initialized with SandyBridge backend
[    20.692] (==) intel(0): Backing store disabled
[    20.692] (==) intel(0): Silken mouse enabled
[    20.692] (II) intel(0): HW Cursor enabled
[    20.692] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    20.693] (==) intel(0): DPMS enabled
[    20.693] (II) intel(0): [DRI2] Setup complete
[    20.693] (II) intel(0): [DRI2]   DRI driver: i965
[    20.693] (II) intel(0): direct rendering: DRI2 Enabled
[    20.693] (==) intel(0): hotplug detection: "enabled"
[    20.693] (--) RandR disabled
[    20.693] (II) Initializing built-in extension Generic Event Extension
[    20.693] (II) Initializing built-in extension SHAPE
[    20.693] (II) Initializing built-in extension MIT-SHM
[    20.693] (II) Initializing built-in extension XInputExtension
[    20.693] (II) Initializing built-in extension XTEST
[    20.693] (II) Initializing built-in extension BIG-REQUESTS
[    20.693] (II) Initializing built-in extension SYNC
[    20.693] (II) Initializing built-in extension XKEYBOARD
[    20.693] (II) Initializing built-in extension XC-MISC
[    20.693] (II) Initializing built-in extension SECURITY
[    20.693] (II) Initializing built-in extension XINERAMA
[    20.693] (II) Initializing built-in extension XFIXES
[    20.693] (II) Initializing built-in extension RENDER
[    20.693] (II) Initializing built-in extension RANDR
[    20.693] (II) Initializing built-in extension COMPOSITE
[    20.693] (II) Initializing built-in extension DAMAGE
[    20.694] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
[    20.697] (II) intel(0): switch to mode 1366x768 on crtc 3 (pipe 0)
[    20.716] (II) intel(0): Setting screen physical size to 361 x 203
[    20.720] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    20.722] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    20.722] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    20.722] (II) LoadModule: "evdev"
[    20.722] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    20.722] (II) Module evdev: vendor="X.Org Foundation"
[    20.722]     compiled for 1.12.3, module version = 2.7.0
[    20.722]     Module class: X.Org XInput Driver
[    20.722]     ABI class: X.Org XInput driver, version 16.0
[    20.722] (II) Using input driver 'evdev' for 'Power Button'
[    20.722] (**) Power Button: always reports core events
[    20.722] (**) evdev: Power Button: Device: "/dev/input/event2"
[    20.722] (--) evdev: Power Button: Vendor 0 Product 0x1
[    20.722] (--) evdev: Power Button: Found keys
[    20.722] (II) evdev: Power Button: Configuring as keyboard
[    20.722] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    20.722] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    20.722] (**) Option "xkb_rules" "evdev"
[    20.722] (**) Option "xkb_model" "pc105"
[    20.722] (**) Option "xkb_layout" "us"
[    20.723] (II) config/udev: Adding input device Video Bus (/dev/input/event8)
[    20.723] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    20.723] (II) Using input driver 'evdev' for 'Video Bus'
[    20.723] (**) Video Bus: always reports core events
[    20.723] (**) evdev: Video Bus: Device: "/dev/input/event8"
[    20.723] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    20.723] (--) evdev: Video Bus: Found keys
[    20.723] (II) evdev: Video Bus: Configuring as keyboard
[    20.723] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input8/event8"
[    20.723] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    20.723] (**) Option "xkb_rules" "evdev"
[    20.723] (**) Option "xkb_model" "pc105"
[    20.723] (**) Option "xkb_layout" "us"
[    20.723] (II) config/udev: Adding input device Video Bus (/dev/input/event7)
[    20.723] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    20.723] (II) Using input driver 'evdev' for 'Video Bus'
[    20.723] (**) Video Bus: always reports core events
[    20.723] (**) evdev: Video Bus: Device: "/dev/input/event7"
[    20.723] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    20.723] (--) evdev: Video Bus: Found keys
[    20.723] (II) evdev: Video Bus: Configuring as keyboard
[    20.723] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input7/event7"
[    20.723] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 8)
[    20.723] (**) Option "xkb_rules" "evdev"
[    20.723] (**) Option "xkb_model" "pc105"
[    20.723] (**) Option "xkb_layout" "us"
[    20.723] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    20.723] (II) No input driver specified, ignoring this device.
[    20.723] (II) This device may have been added with another device file.
[    20.724] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    20.724] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    20.724] (II) Using input driver 'evdev' for 'Sleep Button'
[    20.724] (**) Sleep Button: always reports core events
[    20.724] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[    20.724] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    20.724] (--) evdev: Sleep Button: Found keys
[    20.724] (II) evdev: Sleep Button: Configuring as keyboard
[    20.724] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1/event1"
[    20.724] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[    20.724] (**) Option "xkb_rules" "evdev"
[    20.724] (**) Option "xkb_model" "pc105"
[    20.724] (**) Option "xkb_layout" "us"
[    20.724] (II) config/udev: Adding input device ASUS USB2.0 WebCam (/dev/input/event4)
[    20.724] (**) ASUS USB2.0 WebCam: Applying InputClass "evdev keyboard catchall"
[    20.724] (II) Using input driver 'evdev' for 'ASUS USB2.0 WebCam'
[    20.724] (**) ASUS USB2.0 WebCam: always reports core events
[    20.724] (**) evdev: ASUS USB2.0 WebCam: Device: "/dev/input/event4"
[    20.724] (--) evdev: ASUS USB2.0 WebCam: Vendor 0x58f Product 0xa014
[    20.724] (--) evdev: ASUS USB2.0 WebCam: Found keys
[    20.724] (II) evdev: ASUS USB2.0 WebCam: Configuring as keyboard
[    20.724] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input4/event4"
[    20.724] (II) XINPUT: Adding extended input device "ASUS USB2.0 WebCam" (type: KEYBOARD, id 10)
[    20.724] (**) Option "xkb_rules" "evdev"
[    20.724] (**) Option "xkb_model" "pc105"
[    20.724] (**) Option "xkb_layout" "us"
[    20.724] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event10)
[    20.724] (II) No input driver specified, ignoring this device.
[    20.724] (II) This device may have been added with another device file.
[    20.725] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event11)
[    20.725] (II) No input driver specified, ignoring this device.
[    20.725] (II) This device may have been added with another device file.
[    20.725] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event9)
[    20.725] (II) No input driver specified, ignoring this device.
[    20.725] (II) This device may have been added with another device file.
[    20.725] (II) config/udev: Adding input device Asus WMI hotkeys (/dev/input/event5)
[    20.725] (**) Asus WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    20.725] (II) Using input driver 'evdev' for 'Asus WMI hotkeys'
[    20.725] (**) Asus WMI hotkeys: always reports core events
[    20.725] (**) evdev: Asus WMI hotkeys: Device: "/dev/input/event5"
[    20.725] (--) evdev: Asus WMI hotkeys: Vendor 0 Product 0
[    20.725] (--) evdev: Asus WMI hotkeys: Found keys
[    20.725] (II) evdev: Asus WMI hotkeys: Configuring as keyboard
[    20.725] (**) Option "config_info" "udev:/sys/devices/platform/asus-nb-wmi/input/input5/event5"
[    20.725] (II) XINPUT: Adding extended input device "Asus WMI hotkeys" (type: KEYBOARD, id 11)
[    20.725] (**) Option "xkb_rules" "evdev"
[    20.725] (**) Option "xkb_model" "pc105"
[    20.725] (**) Option "xkb_layout" "us"
[    20.725] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    20.725] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    20.725] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    20.725] (**) AT Translated Set 2 keyboard: always reports core events
[    20.725] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    20.725] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    20.725] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    20.725] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    20.725] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    20.725] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 12)
[    20.725] (**) Option "xkb_rules" "evdev"
[    20.725] (**) Option "xkb_model" "pc105"
[    20.725] (**) Option "xkb_layout" "us"
[    20.726] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/event6)
[    20.726] (**) ETPS/2 Elantech Touchpad: Applying InputClass "evdev touchpad catchall"
[    20.726] (**) ETPS/2 Elantech Touchpad: Applying InputClass "touchpad catchall"
[    20.726] (**) ETPS/2 Elantech Touchpad: Applying InputClass "Default clickpad buttons"
[    20.726] (II) LoadModule: "synaptics"
[    20.726] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    20.726] (II) Module synaptics: vendor="X.Org Foundation"
[    20.726]     compiled for 1.12.3, module version = 1.6.99
[    20.726]     Module class: X.Org XInput Driver
[    20.726]     ABI class: X.Org XInput driver, version 16.0
[    20.726] (II) Using input driver 'synaptics' for 'ETPS/2 Elantech Touchpad'
[    20.726] (**) ETPS/2 Elantech Touchpad: always reports core events
[    20.726] (**) Option "Device" "/dev/input/event6"
[    20.741] (--) synaptics: ETPS/2 Elantech Touchpad: x-axis range 0 - 2508
[    20.741] (--) synaptics: ETPS/2 Elantech Touchpad: y-axis range 0 - 1320
[    20.741] (--) synaptics: ETPS/2 Elantech Touchpad: pressure range 0 - 255
[    20.741] (--) synaptics: ETPS/2 Elantech Touchpad: finger width range 0 - 15
[    20.741] (--) synaptics: ETPS/2 Elantech Touchpad: buttons: left right double triple
[    20.741] (--) synaptics: ETPS/2 Elantech Touchpad: Vendor 0x2 Product 0xe
[    20.741] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[    20.741] (**) ETPS/2 Elantech Touchpad: always reports core events
[    20.744] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio4/input/input6/event6"
[    20.744] (II) XINPUT: Adding extended input device "ETPS/2 Elantech Touchpad" (type: TOUCHPAD, id 13)
[    20.744] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MinSpeed is now constant deceleration 2.5
[    20.744] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MaxSpeed is now 1.75
[    20.744] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) AccelFactor is now 0.071
[    20.744] (**) ETPS/2 Elantech Touchpad: (accel) keeping acceleration scheme 1
[    20.744] (**) ETPS/2 Elantech Touchpad: (accel) acceleration profile 1
[    20.744] (**) ETPS/2 Elantech Touchpad: (accel) acceleration factor: 2.000
[    20.744] (**) ETPS/2 Elantech Touchpad: (accel) acceleration threshold: 4
[    20.744] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[    20.744] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/mouse0)
[    20.744] (**) ETPS/2 Elantech Touchpad: Ignoring device from InputClass "touchpad ignore duplicates"
[    21.284] (II) intel(0): EDID vendor "AUO", prod id 9964
[    21.284] (II) intel(0): Printing DDC gathered Modelines:
[    21.284] (II) intel(0): Modeline "1366x768"x0.0   71.80  1366 1414 1446 1526  768 771 777 784 -hsync -vsync (47.1 kHz eP)
[    21.794] (II) intel(0): EDID vendor "AUO", prod id 9964
[    21.794] (II) intel(0): Printing DDC gathered Modelines:
[    21.794] (II) intel(0): Modeline "1366x768"x0.0   71.80  1366 1414 1446 1526  768 771 777 784 -hsync -vsync (47.1 kHz eP)
[   117.703] (II) intel(0): EDID vendor "AUO", prod id 9964
[   117.703] (II) intel(0): Printing DDC gathered Modelines:
[   117.703] (II) intel(0): Modeline "1366x768"x0.0   71.80  1366 1414 1446 1526  768 771 777 784 -hsync -vsync (47.1 kHz eP)
[   117.946] (II) intel(0): EDID vendor "AUO", prod id 9964
[   117.946] (II) intel(0): Printing DDC gathered Modelines:
[   117.946] (II) intel(0): Modeline "1366x768"x0.0   71.80  1366 1414 1446 1526  768 771 777 784 -hsync -vsync (47.1 kHz eP)
[   118.091] (II) intel(0): EDID vendor "AUO", prod id 9964
[   118.091] (II) intel(0): Printing DDC gathered Modelines:
[   118.091] (II) intel(0): Modeline "1366x768"x0.0   71.80  1366 1414 1446 1526  768 771 777 784 -hsync -vsync (47.1 kHz eP)
[   138.007] (II) intel(0): EDID vendor "AUO", prod id 9964
[   138.007] (II) intel(0): Printing DDC gathered Modelines:
[   138.007] (II) intel(0): Modeline "1366x768"x0.0   71.80  1366 1414 1446 1526  768 771 777 784 -hsync -vsync (47.1 kHz eP)

```

Just in case, Xorg.1.log
```

[   470.364] 
X.Org X Server 1.13.0
Release Date: 2012-09-05
[   470.364] X Protocol Version 11, Revision 0
[   470.364] Build Operating System: Linux 3.2.0-32-generic x86_64 Ubuntu
[   470.364] Current Operating System: Linux eric-K53SD 3.5.0-23-generic #35-Ubuntu SMP Thu Jan 24 13:15:40 UTC 2013 x86_64
[   470.364] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-23-generic root=UUID=27886e28-b9af-482e-b4ae-a5a2950659dc ro quiet splash
[   470.364] Build Date: 27 November 2012  07:44:35AM
[   470.364] xorg-server 2:1.13.0-0ubuntu6.1 (For technical support please see http://www.ubuntu.com/support) 
[   470.364] Current version of pixman: 0.26.0
[   470.364]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[   470.365] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   470.365] (==) Log file: "/var/log/Xorg.1.log", Time: Sat Feb 16 18:49:44 2013
[   470.365] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   470.366] (==) No Layout section.  Using the first Screen section.
[   470.366] (==) No screen section available. Using defaults.
[   470.366] (**) |-->Screen "Default Screen Section" (0)
[   470.366] (**) |   |-->Monitor "<default monitor>"
[   470.366] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[   470.366] (==) Automatically adding devices
[   470.366] (==) Automatically enabling devices
[   470.366] (==) Automatically adding GPU devices
[   470.366] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   470.366]     Entry deleted from font path.
[   470.366] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   470.366]     Entry deleted from font path.
[   470.366] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   470.366]     Entry deleted from font path.
[   470.367] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   470.367]     Entry deleted from font path.
[   470.367] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   470.367]     Entry deleted from font path.
[   470.367] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[   470.367]     Entry deleted from font path.
[   470.367] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[   470.367] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   470.367] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[   470.367] (II) Loader magic: 0x7f72807b6c40
[   470.367] (II) Module ABI versions:
[   470.367]     X.Org ANSI C Emulation: 0.4
[   470.367]     X.Org Video Driver: 13.0
[   470.367]     X.Org XInput driver : 18.0
[   470.367]     X.Org Server Extension : 7.0
[   470.367] (II) config/udev: Adding drm device (/dev/dri/card0)
[   470.370] (--) PCI:*(0:0:2:0) 8086:0116:1043:1652 rev 9, Mem @ 0xdc400000/4194304, 0xb0000000/268435456, I/O @ 0x0000e000/64
[   470.370] (--) PCI: (0:1:0:0) 10de:1058:1043:1652 rev 161, Mem @ 0xdb000000/16777216, 0xc0000000/134217728, 0xc8000000/33554432, I/O @ 0x0000d000/128, BIOS @ 0x????????/524288
[   470.371] (II) Open ACPI successful (/var/run/acpid.socket)
[   470.371] Initializing built-in extension Generic Event Extension
[   470.371] Initializing built-in extension SHAPE
[   470.371] Initializing built-in extension MIT-SHM
[   470.371] Initializing built-in extension XInputExtension
[   470.371] Initializing built-in extension XTEST
[   470.371] Initializing built-in extension BIG-REQUESTS
[   470.371] Initializing built-in extension SYNC
[   470.371] Initializing built-in extension XKEYBOARD
[   470.371] Initializing built-in extension XC-MISC
[   470.371] Initializing built-in extension SECURITY
[   470.371] Initializing built-in extension XINERAMA
[   470.371] Initializing built-in extension XFIXES
[   470.371] Initializing built-in extension RENDER
[   470.371] Initializing built-in extension RANDR
[   470.371] Initializing built-in extension COMPOSITE
[   470.371] Initializing built-in extension DAMAGE
[   470.371] Initializing built-in extension MIT-SCREEN-SAVER
[   470.371] Initializing built-in extension DOUBLE-BUFFER
[   470.371] Initializing built-in extension RECORD
[   470.371] Initializing built-in extension DPMS
[   470.371] Initializing built-in extension X-Resource
[   470.371] Initializing built-in extension XVideo
[   470.371] Initializing built-in extension XVideo-MotionCompensation
[   470.371] Initializing built-in extension XFree86-VidModeExtension
[   470.371] Initializing built-in extension XFree86-DGA
[   470.371] Initializing built-in extension XFree86-DRI
[   470.371] Initializing built-in extension DRI2
[   470.371] (II) LoadModule: "glx"
[   470.371] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[   470.379] (II) Module glx: vendor="NVIDIA Corporation"
[   470.379]     compiled for 4.0.2, module version = 1.0.0
[   470.379]     Module class: X.Org Server Extension
[   470.379] (II) NVIDIA GLX Module  304.64  Tue Oct 30 11:18:32 PDT 2012
[   470.379] Loading extension GLX
[   470.379] (==) Matched intel as autoconfigured driver 0
[   470.379] (==) Matched intel as autoconfigured driver 1
[   470.379] (==) Matched vesa as autoconfigured driver 2
[   470.379] (==) Matched modesetting as autoconfigured driver 3
[   470.379] (==) Matched fbdev as autoconfigured driver 4
[   470.379] (==) Assigned the driver to the xf86ConfigLayout
[   470.379] (II) LoadModule: "intel"
[   470.379] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[   470.379] (II) Module intel: vendor="X.Org Foundation"
[   470.379]     compiled for 1.13.0, module version = 2.20.9
[   470.379]     Module class: X.Org Video Driver
[   470.379]     ABI class: X.Org Video Driver, version 13.0
[   470.379] (II) LoadModule: "vesa"
[   470.379] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   470.379] (II) Module vesa: vendor="X.Org Foundation"
[   470.379]     compiled for 1.12.99.902, module version = 2.3.2
[   470.379]     Module class: X.Org Video Driver
[   470.379]     ABI class: X.Org Video Driver, version 13.0
[   470.379] (II) LoadModule: "modesetting"
[   470.379] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[   470.379] (II) Module modesetting: vendor="X.Org Foundation"
[   470.379]     compiled for 1.13.0, module version = 0.5.0
[   470.379]     Module class: X.Org Video Driver
[   470.379]     ABI class: X.Org Video Driver, version 13.0
[   470.379] (II) LoadModule: "fbdev"
[   470.380] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   470.380] (II) Module fbdev: vendor="X.Org Foundation"
[   470.380]     compiled for 1.12.99.902, module version = 0.4.3
[   470.380]     Module class: X.Org Video Driver
[   470.380]     ABI class: X.Org Video Driver, version 13.0
[   470.380] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
    Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
    Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
    Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
    Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server,
    Ivybridge Server (GT2), Haswell Desktop (GT1), Haswell Desktop (GT2),
    Haswell Desktop (GT2+), Haswell Mobile (GT1), Haswell Mobile (GT2),
    Haswell Mobile (GT2+), Haswell Server (GT1), Haswell Server (GT2),
    Haswell Server (GT2+), Haswell SDV Desktop (GT1),
    Haswell SDV Desktop (GT2), Haswell SDV Desktop (GT2+),
    Haswell SDV Mobile (GT1), Haswell SDV Mobile (GT2),
    Haswell SDV Mobile (GT2+), Haswell SDV Server (GT1),
    Haswell SDV Server (GT2), Haswell SDV Server (GT2+),
    Haswell ULT Desktop (GT1), Haswell ULT Desktop (GT2),
    Haswell ULT Desktop (GT2+), Haswell ULT Mobile (GT1),
    Haswell ULT Mobile (GT2), Haswell ULT Mobile (GT2+),
    Haswell ULT Server (GT1), Haswell ULT Server (GT2),
    Haswell ULT Server (GT2+), Haswell CRW Desktop (GT1),
    Haswell CRW Desktop (GT2), Haswell CRW Desktop (GT2+),
    Haswell CRW Mobile (GT1), Haswell CRW Mobile (GT2),
    Haswell CRW Mobile (GT2+), Haswell CRW Server (GT1),
    Haswell CRW Server (GT2), Haswell CRW Server (GT2+),
    ValleyView PO board
[   470.380] (II) VESA: driver for VESA chipsets: vesa
[   470.380] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[   470.380] (II) FBDEV: driver for framebuffer: fbdev
[   470.380] (++) using VT number 8

[   470.380] (II) intel(0): using device path '/dev/dri/card0'
[   470.380] (WW) Falling back to old probe method for vesa
[   470.380] (WW) Falling back to old probe method for modesetting
[   470.380] (WW) Falling back to old probe method for fbdev
[   470.380] (II) Loading sub module "fbdevhw"
[   470.380] (II) LoadModule: "fbdevhw"
[   470.380] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   470.381] (II) Module fbdevhw: vendor="X.Org Foundation"
[   470.381]     compiled for 1.13.0, module version = 0.0.2
[   470.381]     ABI class: X.Org Video Driver, version 13.0
[   470.381] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[   470.381] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[   470.381] (==) intel(0): RGB weight 888
[   470.381] (==) intel(0): Default visual is TrueColor
[   470.381] (--) intel(0): Integrated Graphics Chipset: Intel(R) Sandybridge Mobile (GT2)
[   470.381] (**) intel(0): Relaxed fencing enabled
[   470.381] (**) intel(0): Wait on SwapBuffers? enabled
[   470.381] (**) intel(0): Triple buffering? enabled
[   470.381] (**) intel(0): Framebuffer tiled
[   470.381] (**) intel(0): Pixmaps tiled
[   470.381] (**) intel(0): 3D buffers tiled
[   470.381] (**) intel(0): SwapBuffers wait enabled
[   470.381] (==) intel(0): video overlay key set to 0x101fe
[   470.381] (II) intel(0): Output LVDS1 has no monitor section
[   470.381] (--) intel(0): found backlight control interface /sys/class/backlight/acpi_video1
[   470.381] (II) intel(0): Output VGA1 has no monitor section
[   470.396] (II) intel(0): Output HDMI1 has no monitor section
[   470.444] (II) intel(0): Output DP1 has no monitor section
[   470.444] (II) intel(0): EDID for output LVDS1
[   470.444] (II) intel(0): Manufacturer: AUO  Model: 26ec  Serial#: 0
[   470.444] (II) intel(0): Year: 2009  Week: 1
[   470.444] (II) intel(0): EDID Version: 1.3
[   470.444] (II) intel(0): Digital Display Input
[   470.444] (II) intel(0): Max Image Size [cm]: horiz.: 34  vert.: 19
[   470.444] (II) intel(0): Gamma: 2.20
[   470.444] (II) intel(0): No DPMS capabilities specified
[   470.444] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[   470.444] (II) intel(0): First detailed timing is preferred mode
[   470.444] (II) intel(0): redX: 0.577 redY: 0.333   greenX: 0.333 greenY: 0.554
[   470.444] (II) intel(0): blueX: 0.161 blueY: 0.144   whiteX: 0.313 whiteY: 0.329
[   470.444] (II) intel(0): Manufacturer's mask: 0
[   470.444] (II) intel(0): Supported detailed timing:
[   470.444] (II) intel(0): clock: 71.8 MHz   Image Size:  344 x 193 mm
[   470.444] (II) intel(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1526 h_border: 0
[   470.444] (II) intel(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 784 v_border: 0
[   470.444] (II) intel(0): Unknown vendor-specific block f
[   470.444] (II) intel(0):  AUO
[   470.444] (II) intel(0):  B156XW02 V6
[   470.444] (II) intel(0): EDID (in hex):
[   470.444] (II) intel(0):     00ffffffffffff0006afec2600000000
[   470.444] (II) intel(0):     01130103802213780ad7759355558d29
[   470.444] (II) intel(0):     24505400000001010101010101010101
[   470.444] (II) intel(0):     0101010101010c1c56a0500010303020
[   470.444] (II) intel(0):     360058c1100000180000000f00000000
[   470.444] (II) intel(0):     00000000000000000020000000fe0041
[   470.444] (II) intel(0):     554f0a202020202020202020000000fe
[   470.444] (II) intel(0):     004231353658573032205636200a0065
[   470.445] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[   470.445] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[   470.445] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[   470.445] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[   470.445] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[   470.445] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[   470.445] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[   470.445] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[   470.445] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[   470.445] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[   470.445] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[   470.445] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[   470.445] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[   470.445] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[   470.445] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[   470.445] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[   470.445] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[   470.445] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[   470.445] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[   470.445] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[   470.445] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[   470.445] (II) intel(0): Printing probed modes for output LVDS1
[   470.445] (II) intel(0): Modeline "1366x768"x60.0   71.80  1366 1414 1446 1526  768 771 777 784 -hsync -vsync (47.1 kHz eP)
[   470.445] (II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz d)
[   470.445] (II) intel(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz d)
[   470.445] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz d)
[   470.445] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz d)
[   470.445] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz d)
[   470.445] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz d)
[   470.445] (II) intel(0): EDID for output VGA1
[   470.460] (II) intel(0): EDID for output HDMI1
[   470.508] (II) intel(0): EDID for output DP1
[   470.508] (II) intel(0): Output LVDS1 connected
[   470.508] (II) intel(0): Output VGA1 disconnected
[   470.508] (II) intel(0): Output HDMI1 disconnected
[   470.508] (II) intel(0): Output DP1 disconnected
[   470.508] (II) intel(0): Using exact sizes for initial modes
[   470.508] (II) intel(0): Output LVDS1 using initial mode 1366x768
[   470.508] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[   470.508] (II) intel(0): Kernel page flipping support detected, enabling
[   470.508] (==) intel(0): DPI set to (96, 96)
[   470.508] (II) Loading sub module "fb"
[   470.508] (II) LoadModule: "fb"
[   470.508] (II) Loading /usr/lib/xorg/modules/libfb.so
[   470.508] (II) Module fb: vendor="X.Org Foundation"
[   470.508]     compiled for 1.13.0, module version = 1.0.0
[   470.508]     ABI class: X.Org ANSI C Emulation, version 0.4
[   470.508] (II) Loading sub module "dri2"
[   470.508] (II) LoadModule: "dri2"
[   470.509] (II) Module "dri2" already built-in
[   470.509] (II) UnloadModule: "vesa"
[   470.509] (II) Unloading vesa
[   470.509] (II) UnloadModule: "modesetting"
[   470.509] (II) Unloading modesetting
[   470.509] (II) UnloadModule: "fbdev"
[   470.509] (II) Unloading fbdev
[   470.509] (II) UnloadSubModule: "fbdevhw"
[   470.509] (II) Unloading fbdevhw
[   470.509] (==) Depth 24 pixmap format is 32 bpp
[   470.509] (II) intel(0): [DRI2] Setup complete
[   470.509] (II) intel(0): [DRI2]   DRI driver: i965
[   470.509] (II) intel(0): Allocated new frame buffer 1408x768 stride 5632, tiled
[   470.511] (II) UXA(0): Driver registered support for the following operations:
[   470.511] (II)         solid
[   470.511] (II)         copy
[   470.511] (II)         composite (RENDER acceleration)
[   470.511] (II)         put_image
[   470.511] (II)         get_image
[   470.511] (==) intel(0): Backing store disabled
[   470.511] (==) intel(0): Silken mouse enabled
[   470.511] (II) intel(0): Initializing HW Cursor
[   470.511] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[   470.513] (==) intel(0): DPMS enabled
[   470.513] (==) intel(0): Intel XvMC decoder enabled
[   470.513] (II) intel(0): Set up textured video
[   470.513] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[   470.513] (II) intel(0): direct rendering: DRI2 Enabled
[   470.513] (==) intel(0): hotplug detection: "enabled"
[   470.536] (--) RandR disabled
[   470.549] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
[   470.549] (II) intel(0): Setting screen physical size to 361 x 203
[   470.556] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   470.557] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[   470.557] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   470.557] (II) LoadModule: "evdev"
[   470.557] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   470.557] (II) Module evdev: vendor="X.Org Foundation"
[   470.557]     compiled for 1.13.0, module version = 2.7.3
[   470.557]     Module class: X.Org XInput Driver
[   470.557]     ABI class: X.Org XInput driver, version 18.0
[   470.557] (II) Using input driver 'evdev' for 'Power Button'
[   470.557] (**) Power Button: always reports core events
[   470.557] (**) evdev: Power Button: Device: "/dev/input/event2"
[   470.557] (--) evdev: Power Button: Vendor 0 Product 0x1
[   470.557] (--) evdev: Power Button: Found keys
[   470.557] (II) evdev: Power Button: Configuring as keyboard
[   470.557] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[   470.557] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[   470.557] (**) Option "xkb_rules" "evdev"
[   470.557] (**) Option "xkb_model" "pc105"
[   470.557] (**) Option "xkb_layout" "us"
[   470.558] (II) config/udev: Adding input device Video Bus (/dev/input/event8)
[   470.558] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[   470.558] (II) Using input driver 'evdev' for 'Video Bus'
[   470.558] (**) Video Bus: always reports core events
[   470.558] (**) evdev: Video Bus: Device: "/dev/input/event8"
[   470.558] (--) evdev: Video Bus: Vendor 0 Product 0x6
[   470.558] (--) evdev: Video Bus: Found keys
[   470.558] (II) evdev: Video Bus: Configuring as keyboard
[   470.558] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input8/event8"
[   470.558] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[   470.558] (**) Option "xkb_rules" "evdev"
[   470.558] (**) Option "xkb_model" "pc105"
[   470.558] (**) Option "xkb_layout" "us"
[   470.558] (II) config/udev: Adding input device Video Bus (/dev/input/event7)
[   470.558] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[   470.558] (II) Using input driver 'evdev' for 'Video Bus'
[   470.558] (**) Video Bus: always reports core events
[   470.558] (**) evdev: Video Bus: Device: "/dev/input/event7"
[   470.558] (--) evdev: Video Bus: Vendor 0 Product 0x6
[   470.558] (--) evdev: Video Bus: Found keys
[   470.558] (II) evdev: Video Bus: Configuring as keyboard
[   470.558] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input7/event7"
[   470.558] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 8)
[   470.558] (**) Option "xkb_rules" "evdev"
[   470.558] (**) Option "xkb_model" "pc105"
[   470.558] (**) Option "xkb_layout" "us"
[   470.558] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[   470.558] (II) No input driver specified, ignoring this device.
[   470.558] (II) This device may have been added with another device file.
[   470.559] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[   470.559] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[   470.559] (II) Using input driver 'evdev' for 'Sleep Button'
[   470.559] (**) Sleep Button: always reports core events
[   470.559] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[   470.559] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[   470.559] (--) evdev: Sleep Button: Found keys
[   470.559] (II) evdev: Sleep Button: Configuring as keyboard
[   470.559] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1/event1"
[   470.559] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[   470.559] (**) Option "xkb_rules" "evdev"
[   470.559] (**) Option "xkb_model" "pc105"
[   470.559] (**) Option "xkb_layout" "us"
[   470.559] (II) config/udev: Adding drm device (/dev/dri/card0)
[   470.559] (II) config/udev: Adding input device ASUS USB2.0 WebCam (/dev/input/event4)
[   470.559] (**) ASUS USB2.0 WebCam: Applying InputClass "evdev keyboard catchall"
[   470.559] (II) Using input driver 'evdev' for 'ASUS USB2.0 WebCam'
[   470.559] (**) ASUS USB2.0 WebCam: always reports core events
[   470.559] (**) evdev: ASUS USB2.0 WebCam: Device: "/dev/input/event4"
[   470.559] (--) evdev: ASUS USB2.0 WebCam: Vendor 0x58f Product 0xa014
[   470.559] (--) evdev: ASUS USB2.0 WebCam: Found keys
[   470.559] (II) evdev: ASUS USB2.0 WebCam: Configuring as keyboard
[   470.559] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input4/event4"
[   470.559] (II) XINPUT: Adding extended input device "ASUS USB2.0 WebCam" (type: KEYBOARD, id 10)
[   470.559] (**) Option "xkb_rules" "evdev"
[   470.559] (**) Option "xkb_model" "pc105"
[   470.559] (**) Option "xkb_layout" "us"
[   470.559] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event10)
[   470.559] (II) No input driver specified, ignoring this device.
[   470.559] (II) This device may have been added with another device file.
[   470.560] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event11)
[   470.560] (II) No input driver specified, ignoring this device.
[   470.560] (II) This device may have been added with another device file.
[   470.560] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event9)
[   470.560] (II) No input driver specified, ignoring this device.
[   470.560] (II) This device may have been added with another device file.
[   470.560] (II) config/udev: Adding input device Asus WMI hotkeys (/dev/input/event5)
[   470.560] (**) Asus WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[   470.560] (II) Using input driver 'evdev' for 'Asus WMI hotkeys'
[   470.560] (**) Asus WMI hotkeys: always reports core events
[   470.560] (**) evdev: Asus WMI hotkeys: Device: "/dev/input/event5"
[   470.560] (--) evdev: Asus WMI hotkeys: Vendor 0 Product 0
[   470.560] (--) evdev: Asus WMI hotkeys: Found keys
[   470.560] (II) evdev: Asus WMI hotkeys: Configuring as keyboard
[   470.560] (**) Option "config_info" "udev:/sys/devices/platform/asus-nb-wmi/input/input5/event5"
[   470.560] (II) XINPUT: Adding extended input device "Asus WMI hotkeys" (type: KEYBOARD, id 11)
[   470.560] (**) Option "xkb_rules" "evdev"
[   470.560] (**) Option "xkb_model" "pc105"
[   470.560] (**) Option "xkb_layout" "us"
[   470.560] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[   470.560] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[   470.560] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[   470.560] (**) AT Translated Set 2 keyboard: always reports core events
[   470.560] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[   470.560] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[   470.560] (--) evdev: AT Translated Set 2 keyboard: Found keys
[   470.560] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[   470.560] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[   470.560] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 12)
[   470.560] (**) Option "xkb_rules" "evdev"
[   470.560] (**) Option "xkb_model" "pc105"
[   470.560] (**) Option "xkb_layout" "us"
[   470.561] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/event6)
[   470.561] (**) ETPS/2 Elantech Touchpad: Applying InputClass "evdev touchpad catchall"
[   470.561] (**) ETPS/2 Elantech Touchpad: Applying InputClass "touchpad catchall"
[   470.561] (**) ETPS/2 Elantech Touchpad: Applying InputClass "Default clickpad buttons"
[   470.561] (II) LoadModule: "synaptics"
[   470.561] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[   470.561] (II) Module synaptics: vendor="X.Org Foundation"
[   470.561]     compiled for 1.12.99.905, module version = 1.6.2
[   470.561]     Module class: X.Org XInput Driver
[   470.561]     ABI class: X.Org XInput driver, version 18.0
[   470.561] (II) Using input driver 'synaptics' for 'ETPS/2 Elantech Touchpad'
[   470.561] (**) ETPS/2 Elantech Touchpad: always reports core events
[   470.561] (**) Option "Device" "/dev/input/event6"
[   470.564] (--) synaptics: ETPS/2 Elantech Touchpad: x-axis range 0 - 2508
[   470.564] (--) synaptics: ETPS/2 Elantech Touchpad: y-axis range 0 - 1320
[   470.564] (--) synaptics: ETPS/2 Elantech Touchpad: pressure range 0 - 255
[   470.564] (--) synaptics: ETPS/2 Elantech Touchpad: finger width range 0 - 15
[   470.564] (--) synaptics: ETPS/2 Elantech Touchpad: buttons: left right double triple
[   470.564] (--) synaptics: ETPS/2 Elantech Touchpad: Vendor 0x2 Product 0xe
[   470.564] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[   470.564] (**) ETPS/2 Elantech Touchpad: always reports core events
[   470.564] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio4/input/input6/event6"
[   470.564] (II) XINPUT: Adding extended input device "ETPS/2 Elantech Touchpad" (type: TOUCHPAD, id 13)
[   470.564] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MinSpeed is now constant deceleration 2.5
[   470.564] (**) synaptics: ETPS/2 Elantech Touchpad: MaxSpeed is now 1.75
[   470.564] (**) synaptics: ETPS/2 Elantech Touchpad: AccelFactor is now 0.071
[   470.565] (**) ETPS/2 Elantech Touchpad: (accel) keeping acceleration scheme 1
[   470.565] (**) ETPS/2 Elantech Touchpad: (accel) acceleration profile 1
[   470.565] (**) ETPS/2 Elantech Touchpad: (accel) acceleration factor: 2.000
[   470.565] (**) ETPS/2 Elantech Touchpad: (accel) acceleration threshold: 4
[   470.565] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[   470.565] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/mouse0)
[   470.565] (**) ETPS/2 Elantech Touchpad: Ignoring device from InputClass "touchpad ignore duplicates"
[   470.997] (II) intel(0): EDID vendor "AUO", prod id 9964
[   470.997] (II) intel(0): Printing DDC gathered Modelines:
[   470.997] (II) intel(0): Modeline "1366x768"x0.0   71.80  1366 1414 1446 1526  768 771 777 784 -hsync -vsync (47.1 kHz eP)
[   471.161] (II) intel(0): EDID vendor "AUO", prod id 9964
[   471.161] (II) intel(0): Printing DDC gathered Modelines:
[   471.161] (II) intel(0): Modeline "1366x768"x0.0   71.80  1366 1414 1446 1526  768 771 777 784 -hsync -vsync (47.1 kHz eP)
[   516.117] (II) UnloadModule: "synaptics"
[   516.117] (II) evdev: AT Translated Set 2 keyboard: Close
[   516.117] (II) UnloadModule: "evdev"
[   516.117] (II) evdev: Asus WMI hotkeys: Close
[   516.117] (II) UnloadModule: "evdev"
[   516.117] (II) evdev: ASUS USB2.0 WebCam: Close
[   516.117] (II) UnloadModule: "evdev"
[   516.118] (II) evdev: Sleep Button: Close
[   516.118] (II) UnloadModule: "evdev"
[   516.118] (II) evdev: Video Bus: Close
[   516.118] (II) UnloadModule: "evdev"
[   516.118] (II) evdev: Video Bus: Close
[   516.118] (II) UnloadModule: "evdev"
[   516.118] (II) evdev: Power Button: Close
[   516.118] (II) UnloadModule: "evdev"
[   516.118] Server terminated successfully (0). Closing log file.

```

---

### Post by Yellow Pasque on 2013-02-20
You still have nvidia stuff littered about on your system.
```
[    20.555] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    20.561] (II) Module glx: vendor="NVIDIA Corporation"
[    20.561]     compiled for 4.0.2, module version = 1.0.0
[    20.561]     Module class: X.Org Server Extension
[    20.561] (II) NVIDIA GLX Module  304.64  Tue Oct 30 11:18:32 PDT 2012

```

I don't know what else to tell you (other than to use .deb packages to install stuff so this kind of thing doesn't happen). I rarely advise reinstall, but it may be the fastest/easiest way to get back to a normal system.

---

