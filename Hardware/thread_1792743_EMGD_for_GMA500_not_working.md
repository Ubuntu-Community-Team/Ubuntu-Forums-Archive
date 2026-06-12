---
title: "EMGD for GMA500 not working"
date: 2011-06-28
forum: Hardware
---

### Post by tzury on 2011-06-28
The symptom: When system loads, screen is divided into 2 parts, very dark, and icons cannot be recognized and not useful at all.

The only version I have got it working properly is 9.04. Yet, this one is not supported, and I cannot even run apt-get update, let alone install some tools I need.

I have followed the instructions found at [launchpad]("https://launchpad.net/~gma500/+archive/emgd"), tried it on 11.04, 10.10. and 10.04 but with no help.

I have tried to modify the xorg.conf file by hand, but it does not seem to help. 

Given the fact, it is was working smoothly under 9.04, I get the impression it is a tweak away.

Attached is the Xorg.log file which I split into 3 owe to file size limit

---

### Post by tzury on 2011-06-28
adding the logfile inline


[     9.545] 
X.Org X Server 1.9.2.901 (1.9.3 RC 1)
Release Date: 2010-11-13
[     9.545] X Protocol Version 11, Revision 0
[     9.545] Build Operating System: Linux 2.6.24-28-xen i686 Ubuntu
[     9.545] Current Operating System: Linux ubuntu 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686
[     9.545] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=030af04b-cbe6-4b86-a307-002dce0517bb ro quiet splash vt.handoff=7
[     9.546] Build Date: 02 May 2011  11:16:09AM
[     9.546] xorg-server 3:1.10.9-down1.9.2.901.2+git20101129+server-1.9-branch.65f2ab20-0ubuntu0sarvatt2~natty (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[     9.546] Current version of pixman: 0.20.2
[     9.546] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[     9.546] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     9.546] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Jun 28 14:28:27 2011
[     9.548] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     9.550] (==) ServerLayout "Default Layout"
[     9.550] (**) |-->Screen "Screen0" (0)
[     9.550] (**) |   |-->Monitor "LVDS"
[     9.551] (**) |   |-->Device "Intel_EMGD-0"
[     9.551] (==) Automatically adding devices
[     9.551] (==) Automatically enabling devices
[     9.552] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     9.553] 	Entry deleted from font path.
[     9.553] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     9.553] 	Entry deleted from font path.
[     9.553] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     9.553] 	Entry deleted from font path.
[     9.557] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     9.579] 	Entry deleted from font path.
[     9.579] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     9.579] 	Entry deleted from font path.
[     9.585] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[     9.585] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     9.585] (WW) Ignoring unrecognized extension "composite"
[     9.585] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[     9.585] (II) Loader magic: 0x81f9960
[     9.585] (II) Module ABI versions:
[     9.585] 	X.Org ANSI C Emulation: 0.4
[     9.585] 	X.Org Video Driver: 8.0
[     9.585] 	X.Org XInput driver : 11.0
[     9.585] 	X.Org Server Extension : 4.0
[     9.588] (--) PCI:*(0:0:2:0) 8086:8108:4352:9686 rev 7, Mem @ 0xdff80000/524288, 0xd0000000/134217728, 0xdff60000/131072, I/O @ 0x0000e880/8
[     9.589] (II) Open ACPI successful (/var/run/acpid.socket)
[     9.589] (II) LoadModule: "extmod"
[     9.594] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[     9.594] (II) Module extmod: vendor="X.Org Foundation"
[     9.595] 	compiled for 1.9.2.901, module version = 1.0.0
[     9.595] 	Module class: X.Org Server Extension
[     9.595] 	ABI class: X.Org Server Extension, version 4.0
[     9.595] (II) Loading extension MIT-SCREEN-SAVER
[     9.595] (II) Loading extension XFree86-VidModeExtension
[     9.595] (II) Loading extension XFree86-DGA
[     9.595] (II) Loading extension DPMS
[     9.595] (II) Loading extension XVideo
[     9.595] (II) Loading extension XVideo-MotionCompensation
[     9.595] (II) Loading extension X-Resource
[     9.595] (II) LoadModule: "dbe"
[     9.597] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[     9.597] (II) Module dbe: vendor="X.Org Foundation"
[     9.597] 	compiled for 1.9.2.901, module version = 1.0.0
[     9.597] 	Module class: X.Org Server Extension
[     9.597] 	ABI class: X.Org Server Extension, version 4.0
[     9.597] (II) Loading extension DOUBLE-BUFFER
[     9.597] (II) LoadModule: "glx"
[     9.599] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[     9.600] (II) Module glx: vendor="X.Org Foundation"
[     9.600] 	compiled for 1.9.2.901, module version = 1.0.0
[     9.600] 	ABI class: X.Org Server Extension, version 4.0
[     9.600] (==) AIGLX enabled
[     9.600] (II) Loading extension GLX
[     9.600] (II) LoadModule: "record"
[     9.602] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[     9.602] (II) Module record: vendor="X.Org Foundation"
[     9.602] 	compiled for 1.9.2.901, module version = 1.13.0
[     9.602] 	Module class: X.Org Server Extension
[     9.602] 	ABI class: X.Org Server Extension, version 4.0
[     9.602] (II) Loading extension RECORD
[     9.603] (II) LoadModule: "dri"
[     9.604] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[     9.605] (II) Module dri: vendor="X.Org Foundation"
[     9.605] 	compiled for 1.9.2.901, module version = 1.0.0
[     9.605] 	ABI class: X.Org Server Extension, version 4.0
[     9.605] (II) Loading extension XFree86-DRI
[     9.605] (II) LoadModule: "dri2"
[     9.609] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[     9.609] (II) Module dri2: vendor="X.Org Foundation"
[     9.609] 	compiled for 1.9.2.901, module version = 1.2.0
[     9.609] 	ABI class: X.Org Server Extension, version 4.0
[     9.609] (II) Loading extension DRI2
[     9.609] (II) LoadModule: "emgd"
[     9.614] (II) Loading /usr/lib/xorg/modules/drivers/emgd_drv.so
[     9.632] (II) Module emgd: vendor="Intel(R) Corporation"
[     9.632] 	compiled for 1.9.0, module version = 1.6.1952
[     9.632] 	Module class: X.Org Video Driver
[     9.632] 	ABI class: X.Org Video Driver, version 8.0
[     9.632] (II) EMGD: Intel(R) Embedded Media and Graphics Driver version 1.6.1952 for:
	Intel US15W Class
[     9.633] (++) using VT number 7

[     9.633] (II) EMGD(0): Creating default Display subsection in Screen section
	"Screen0" for depth/fbbpp 24/32
[     9.634] (==) EMGD(0): RGB weight 888
[     9.634] (==) EMGD(0): Default visual is TrueColor
[     9.634] drmOpenDevice: node name is /dev/dri/card0
[     9.813] drmOpenByBusid: Searching for BusID PCI:00:00:00
[     9.814] drmOpenDevice: node name is /dev/dri/card0
[     9.814] drmOpenDevice: open result is 9, (OK)
[     9.814] drmOpenByBusid: drmOpenMinor returns 9
[     9.814] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[     9.814] drmOpenDevice: node name is /dev/dri/card1
[     9.822] drmOpenByBusid: drmOpenMinor returns -1
[     9.822] drmOpenDevice: node name is /dev/dri/card2
[     9.827] drmOpenByBusid: drmOpenMinor returns -1
[     9.827] drmOpenDevice: node name is /dev/dri/card3
[     9.832] drmOpenByBusid: drmOpenMinor returns -1
[     9.832] drmOpenDevice: node name is /dev/dri/card4
[     9.837] drmOpenByBusid: drmOpenMinor returns -1
[     9.837] drmOpenDevice: node name is /dev/dri/card5
[     9.842] drmOpenByBusid: drmOpenMinor returns -1
[     9.842] drmOpenDevice: node name is /dev/dri/card6
[     9.847] drmOpenByBusid: drmOpenMinor returns -1
[     9.847] drmOpenDevice: node name is /dev/dri/card7
[     9.852] drmOpenByBusid: drmOpenMinor returns -1
[     9.852] drmOpenDevice: node name is /dev/dri/card8
[     9.857] drmOpenByBusid: drmOpenMinor returns -1
[     9.857] drmOpenDevice: node name is /dev/dri/card9
[     9.862] drmOpenByBusid: drmOpenMinor returns -1
[     9.862] drmOpenDevice: node name is /dev/dri/card10
[     9.867] drmOpenByBusid: drmOpenMinor returns -1
[     9.867] drmOpenDevice: node name is /dev/dri/card11
[     9.872] drmOpenByBusid: drmOpenMinor returns -1
[     9.872] drmOpenDevice: node name is /dev/dri/card12
[     9.877] drmOpenByBusid: drmOpenMinor returns -1
[     9.877] drmOpenDevice: node name is /dev/dri/card13
[     9.882] drmOpenByBusid: drmOpenMinor returns -1
[     9.882] drmOpenDevice: node name is /dev/dri/card14
[     9.886] drmOpenByBusid: drmOpenMinor returns -1
[     9.886] drmOpenDevice: node name is /dev/dri/card15
[     9.891] drmOpenByBusid: drmOpenMinor returns -1
[     9.891] drmOpenDevice: node name is /dev/dri/card0
[     9.891] drmOpenDevice: open result is 9, (OK)
[     9.891] drmOpenDevice: node name is /dev/dri/card0
[     9.892] drmOpenDevice: open result is 9, (OK)
[     9.892] drmGetBusid returned ''
[     9.892] (II) EMGD(0): Chipset: "Intel SCH US15 Chipset"
[     9.892] (II) EMGD(0): Checking for new style options
[     9.892] (II) EMGD(0): Processing version 7.0 options
[     9.892] (II) EMGD(0): Using configuration 1
[     9.892] (II) EMGD(0): Checking for US15 specific configuration.
[     9.892] (II) EMGD(0): Checking for non-chipset specific configuration.
[     9.892] (II) EMGD(0): Option processing done!
[    10.113] (II) EMGD(0): Valid Display Configurations:
[    10.113] (II) EMGD(0):   DC: 0x00000041
[    10.113] (II) EMGD(0):   DC: 0x00000000
[    10.113] (II) EMGD(0): Using Display Configuration 0x00000041
[    10.113] (==) EMGD(0): Depth 24, (--) framebuffer bpp 32
[    10.113] (==) EMGD(0): Using gamma correction (1.0, 1.0, 1.0)
[    10.114] (II) EMGD(0): 34 modes passed validation checks
[    10.114] (--) EMGD(0): Virtual size is 1366x768 (pitch 0)
[    10.114] (**) EMGD(0):  Built-in mode "1366x768": 74.1 MHz (scaled from 0.0 MHz), 44.5 kHz, 60.0 Hz
[    10.114] (II) EMGD(0): Modeline "1366x768"x60.0   74.06  1366 1429 1557 1663  768 768 769 775 +hsync +vsync (44.5 kHz)
[    10.114] (**) EMGD(0):  Built-in mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
[    10.114] (II) EMGD(0): Modeline "1280x1024"x60.0  108.00  1280 1327 1439 1687  1024 1024 1027 1065 +hsync +vsync (64.0 kHz)
[    10.114] (**) EMGD(0):  Built-in mode "1280x960": 108.0 MHz (scaled from 0.0 MHz), 60.0 kHz, 60.0 Hz
[    10.114] (II) EMGD(0): Modeline "1280x960"x60.0  108.00  1280 1375 1487 1799  960 960 963 999 +hsync +vsync (60.0 kHz)
[    10.114] (**) EMGD(0):  Built-in mode "1280x768": 103.0 MHz (scaled from 0.0 MHz), 60.2 kHz, 75.0 Hz
[    10.115] (II) EMGD(0): Modeline "1280x768"x75.0  102.98  1280 1359 1495 1711  768 768 771 801 +vsync (60.2 kHz)
[    10.115] (**) EMGD(0):  Built-in mode "1280x768": 80.1 MHz (scaled from 0.0 MHz), 47.7 kHz, 60.0 Hz
[    10.115] (II) EMGD(0): Modeline "1280x768"x60.0   80.14  1280 1343 1479 1679  768 768 771 794 +vsync (47.7 kHz)
[    10.115] (**) EMGD(0):  Built-in mode "1280x720": 110.0 MHz (scaled from 0.0 MHz), 64.3 kHz, 85.0 Hz
[    10.115] (II) EMGD(0): Modeline "1280x720"x85.0  110.00  1280 1359 1495 1711  720 720 723 755 +vsync (64.3 kHz)
[    10.115] (**) EMGD(0):  Built-in mode "1280x720": 96.0 MHz (scaled from 0.0 MHz), 56.6 kHz, 75.0 Hz
[    10.115] (II) EMGD(0): Modeline "1280x720"x75.0   96.00  1280 1351 1487 1695  720 720 723 751 +vsync (56.6 kHz)
[    10.115] (**) EMGD(0):  Built-in mode "1280x720": 74.5 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
[    10.115] (II) EMGD(0): Modeline "1280x720"x60.0   74.48  1280 1335 1471 1663  720 720 723 745 +vsync (44.8 kHz)
[    10.115] (**) EMGD(0):  Built-in mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
[    10.115] (II) EMGD(0): Modeline "1152x864"x75.0  108.00  1152 1215 1343 1599  864 864 867 899 +hsync +vsync (67.5 kHz)
[    10.115] (**) EMGD(0):  Built-in mode "1152x864": 100.0 MHz (scaled from 0.0 MHz), 65.1 kHz, 72.0 Hz
[    10.115] (II) EMGD(0): Modeline "1152x864"x72.0  100.00  1152 1223 1343 1535  864 864 867 900 +vsync (65.1 kHz)
[    10.115] (**) EMGD(0):  Built-in mode "1152x864": 97.0 MHz (scaled from 0.0 MHz), 63.2 kHz, 70.0 Hz
[    10.115] (II) EMGD(0): Modeline "1152x864"x70.0   97.00  1152 1223 1343 1535  864 864 867 899 +vsync (63.2 kHz)
[    10.115] (**) EMGD(0):  Built-in mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
[    10.115] (II) EMGD(0): Modeline "1152x864"x60.0   81.62  1152 1215 1335 1519  864 864 867 894 +vsync (53.7 kHz)
[    10.116] (**) EMGD(0):  Built-in mode "1024x768": 94.5 MHz (scaled from 0.0 MHz), 68.7 kHz, 85.0 Hz
[    10.116] (II) EMGD(0): Modeline "1024x768"x85.0   94.50  1024 1071 1167 1375  768 768 771 807 +hsync +vsync (68.7 kHz)
[    10.116] (**) EMGD(0):  Built-in mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.1 kHz, 75.0 Hz
[    10.116] (II) EMGD(0): Modeline "1024x768"x75.0   78.75  1024 1039 1135 1311  768 768 771 799 +hsync +vsync (60.1 kHz)
[    10.116] (**) EMGD(0):  Built-in mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
[    10.116] (II) EMGD(0): Modeline "1024x768"x70.0   75.00  1024 1047 1183 1327  768 770 776 805 (56.5 kHz)
[    10.116] (**) EMGD(0):  Built-in mode "960x540": 40.8 MHz (scaled from 0.0 MHz), 33.6 kHz, 60.0 Hz
[    10.116] (II) EMGD(0): Modeline "960x540"x60.0   40.78  960 991 1087 1215  540 540 543 558 +vsync (33.6 kHz)
[    10.116] (**) EMGD(0):  Built-in mode "800x600": 84.0 MHz (scaled from 0.0 MHz), 77.2 kHz, 120.0 Hz
[    10.116] (II) EMGD(0): Modeline "800x600"x120.0   83.95  800 855 943 1087  600 600 603 642 +vsync (77.2 kHz)
[    10.116] (**) EMGD(0):  Built-in mode "800x600": 68.2 MHz (scaled from 0.0 MHz), 63.7 kHz, 100.0 Hz
[    10.116] (II) EMGD(0): Modeline "800x600"x100.0   68.18  800 847 935 1071  600 600 603 635 +vsync (63.7 kHz)
[    10.116] (**) EMGD(0):  Built-in mode "800x600": 56.2 MHz (scaled from 0.0 MHz), 53.7 kHz, 85.0 Hz
[    10.117] (II) EMGD(0): Modeline "800x600"x85.0   56.25  800 831 895 1047  600 600 603 630 +hsync +vsync (53.7 kHz)
[    10.117] (**) EMGD(0):  Built-in mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
[    10.117] (II) EMGD(0): Modeline "800x600"x75.0   49.50  800 815 895 1055  600 600 603 624 +hsync +vsync (46.9 kHz)
[    10.117] (**) EMGD(0):  Built-in mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
[    10.117] (II) EMGD(0): Modeline "800x600"x72.0   50.00  800 855 975 1039  600 636 642 665 +hsync +vsync (48.1 kHz)
[    10.117] (**) EMGD(0):  Built-in mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
[    10.117] (II) EMGD(0): Modeline "800x600"x70.0   45.50  800 839 919 1039  600 600 603 624 +vsync (43.8 kHz)
[    10.117] (**) EMGD(0):  Built-in mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
[    10.117] (II) EMGD(0): Modeline "800x600"x60.0   40.00  800 839 967 1055  600 600 604 627 +hsync +vsync (37.9 kHz)
[    10.117] (**) EMGD(0):  Built-in mode "800x480": 33.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
[    10.117] (II) EMGD(0): Modeline "800x480"x60.0   33.23  800 863 991 1055  480 500 502 524 +vsync (31.5 kHz)
[    10.117] (**) EMGD(0):  Built-in mode "720x576": 27.5 MHz (scaled from 0.0 MHz), 31.8 kHz, 50.0 Hz
[    10.117] (II) EMGD(0): Modeline "720x576"x50.0   27.50  720 732 795 864  576 581 587 625 +vsync (31.8 kHz)
[    10.117] (**) EMGD(0):  Built-in mode "720x480": 27.0 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
[    10.117] (II) EMGD(0): Modeline "720x480"x60.0   27.00  720 735 797 857  480 488 494 524 +vsync (31.5 kHz)
[    10.117] (**) EMGD(0):  Built-in mode "640x480": 52.4 MHz (scaled from 0.0 MHz), 61.9 kHz, 120.0 Hz
[    10.117] (II) EMGD(0): Modeline "640x480"x120.0   52.41  640 679 743 847  480 480 483 514 +vsync (61.9 kHz)
[    10.118] (**) EMGD(0):  Built-in mode "640x480": 43.2 MHz (scaled from 0.0 MHz), 51.0 kHz, 100.0 Hz
[    10.118] (II) EMGD(0): Modeline "640x480"x100.0   43.16  640 679 743 847  480 480 483 508 +vsync (51.0 kHz)
[    10.118] (**) EMGD(0):  Built-in mode "640x480": 36.0 MHz (scaled from 0.0 MHz), 43.3 kHz, 85.0 Hz
[    10.118] (II) EMGD(0): Modeline "640x480"x85.0   36.00  640 695 751 831  480 480 483 508 (43.3 kHz)
[    10.118] (**) EMGD(0):  Built-in mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
[    10.118] (II) EMGD(0): Modeline "640x480"x75.0   31.50  640 655 719 839  480 480 483 499 (37.5 kHz)
[    10.118] (**) EMGD(0):  Built-in mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
[    10.118] (II) EMGD(0): Modeline "640x480"x72.0   31.50  640 663 703 831  480 488 491 519 (37.9 kHz)
[    10.118] (**) EMGD(0):  Built-in mode "640x480": 28.6 MHz (scaled from 0.0 MHz), 35.0 kHz, 70.0 Hz
[    10.118] (II) EMGD(0): Modeline "640x480"x70.0   28.56  640 663 727 815  480 480 483 499 +vsync (35.0 kHz)
[    10.118] (**) EMGD(0):  Built-in mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
[    10.118] (II) EMGD(0): Modeline "640x480"x60.0   25.18  640 655 751 799  480 489 491 524 (31.5 kHz)
[    10.118] (**) EMGD(0):  Built-in mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
[    10.118] (II) EMGD(0): Modeline "1024x768"x60.0   65.00  1024 1047 1183 1343  768 770 776 805 (48.4 kHz)
[    10.118] (==) EMGD(0): DPI set to (96, 96)
[    10.118] (II) Loading sub module "fb"
[    10.118] (II) LoadModule: "fb"
[    10.119] (II) Loading /usr/lib/xorg/modules/libfb.so
[    10.128] (II) Module fb: vendor="X.Org Foundation"
[    10.128] 	compiled for 1.9.2.901, module version = 1.0.0
[    10.128] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    10.128] (II) Loading sub module "ramdac"
[    10.128] (II) LoadModule: "ramdac"
[    10.128] (II) Module "ramdac" already built-in
[    10.128] (II) EMGD(0): General Driver Configuration Options
[    10.128] (II) EMGD(0):   PCF Version:            7.00
[    10.128] (II) EMGD(0):   Configuration ID:       1
[    10.128] (II) EMGD(0): Primary Display Configuration Options
[    10.128] (II) EMGD(0):   VideoRam (Pixmap Cache): 32768
[    10.128] (II) EMGD(0):   PORT AND DISPLAY OPTIONS
[    10.128] (II) EMGD(0):     Port Order:           42000
[    10.128] (II) EMGD(0):     Display Config:       Single
[    10.128] (II) EMGD(0):     Display Detect:       On
[    10.128] (II) EMGD(0):     FB Blend Overlay:     Off
[    10.128] (II) EMGD(0):     Gang DVO:             Off
[    10.128] (II) EMGD(0):     Refresh Rate:         0
[    10.129] (II) EMGD(0):     Clone Width:          0
[    10.129] (II) EMGD(0):     Clone Height:         0
[    10.129] (II) EMGD(0):     Clone Refresh:        0
[    10.129] (II) EMGD(0):   FRAMEBUFFER OPTIONS
[    10.129] (II) EMGD(0):     Shadow FB:            Off
[    10.129] (II) EMGD(0):     Tear FB:              On
[    10.129] (II) EMGD(0):     Resize:               Off
[    10.129] (II) EMGD(0):   FRAMEBUFFER ORIENTATION OPTIONS
[    10.129] (II) EMGD(0):     Rotation:             0 degrees
[    10.129] (II) EMGD(0):     Flip:                 Off
[    10.129] (II) EMGD(0):   HARDWARE ACCELERATION OPTIONS
[    10.129] (II) EMGD(0):     HW 2D Accel:          On
[    10.129] (II) EMGD(0):     HW Cursor:            On
[    10.129] (II) EMGD(0):   XVIDEO OPTIONS
[    10.129] (II) EMGD(0):     XVideo:               On
[    10.129] (II) EMGD(0):     XVideoBlend:          On
[    10.129] (II) EMGD(0):     XVideoMC:             Off
[    10.129] (II) EMGD(0):     XVideoKey:            0xff00ff00
[    10.129] (II) EMGD(0):     Overlay Gamma Red:    0x100
[    10.129] (II) EMGD(0):     Overlay Gamma Green:  0x100
[    10.129] (II) EMGD(0):     Overlay Gamma Blue:   0x100
[    10.129] (II) EMGD(0):     Overlay Brightness:   0x8000
[    10.129] (II) EMGD(0):     Overlay Contrast:     0x8000
[    10.130] (II) EMGD(0):     Overlay Saturation:   0x8000
[    10.130] (II) EMGD(0):     DRI:                  Off
[    10.130] (II) EMGD(0):     DRI2:                 On
[    10.130] (II) EMGD(0):     EDID:                 On
[    10.130] (II) EMGD(0):   QUICKBOOT OPTIONS
[    10.130] (II) EMGD(0):     QuickBoot:            0
[    10.130] (II) EMGD(0):     Seamless:             Off
[    10.130] (II) EMGD(0):     Video Input:          0
[    10.130] (II) EMGD(0):     Splash Screen:        Off
[    10.130] (II) EMGD(0):    INTERRUPT OPTIONS
[    10.130] (II) EMGD(0):      Polling:             Off
[    10.130] (II) EMGD(0):   GLOBAL PER PORT OPTIONS
[    10.130] (II) EMGD(0):   Port 2            (null)
[    10.130] (II) EMGD(0):      Multi-DVO:      Off
[    10.130] (II) EMGD(0):      Rotation:       0 degrees
[    10.130] (II) EMGD(0):      Flip:           Off
[    10.130] (II) EMGD(0):      Centering:      Off
[    10.130] (II) EMGD(0):      RenderScale:    Off
[    10.130] (II) EMGD(0):      EDID:           On
[    10.130] (II) EMGD(0):      EDID Avail:     0x3
[    10.130] (II) EMGD(0):      EDID Not Avail: 0x1
[    10.130] (II) EMGD(0):      PANEL INFORMATION
[    10.130] (II) EMGD(0):         FP width:     0
[    10.130] (II) EMGD(0):         FP height:    0
[    10.131] (II) EMGD(0):         BKLT Enable:  0
[    10.131] (II) EMGD(0):         BKLT Method:  1
[    10.131] (II) EMGD(0):         BKLT T1:      60
[    10.131] (II) EMGD(0):         BKLT T2:      200
[    10.131] (II) EMGD(0):         BKLT T3:      200
[    10.131] (II) EMGD(0):         BKLT T4:      50
[    10.131] (II) EMGD(0):         BKLT T5:      400
[    10.131] (II) EMGD(0):         GPIO Pin VDD: 0
[    10.131] (II) EMGD(0):         GPIO Pin VEE: 0
[    10.131] (II) EMGD(0):         GPIO Pin BKLT:0
[    10.131] (II) EMGD(0):         DVO i2c pin:  0
[    10.131] (II) EMGD(0):         DVO i2c DAB:  0
[    10.131] (II) EMGD(0):         DVO i2c speed:0
[    10.131] (II) EMGD(0):         DVO ddc pin:  0
[    10.131] (II) EMGD(0):         DVO ddc speed:0
[    10.131] (II) EMGD(0):      Number DTD's:   0
[    10.131] (II) EMGD(0):      Number Attr's:  0
[    10.131] (II) EMGD(0):   Port 4            LVDS
[    10.131] (II) EMGD(0):      Multi-DVO:      Off
[    10.131] (II) EMGD(0):      Rotation:       0 degrees
[    10.131] (II) EMGD(0):      Flip:           Off
[    10.131] (II) EMGD(0):      Centering:      Off
[    10.131] (II) EMGD(0):      RenderScale:    Off
[    10.131] (II) EMGD(0):      EDID:           On
[    10.132] (II) EMGD(0):      EDID Avail:     0x3
[    10.132] (II) EMGD(0):      EDID Not Avail: 0x5
[    10.132] (II) EMGD(0):      PANEL INFORMATION
[    10.132] (II) EMGD(0):         FP width:     0
[    10.132] (II) EMGD(0):         FP height:    0
[    10.132] (II) EMGD(0):         BKLT Enable:  0
[    10.132] (II) EMGD(0):         BKLT Method:  0
[    10.132] (II) EMGD(0):         BKLT T1:      0
[    10.132] (II) EMGD(0):         BKLT T2:      0
[    10.132] (II) EMGD(0):         BKLT T3:      0
[    10.132] (II) EMGD(0):         BKLT T4:      0
[    10.132] (II) EMGD(0):         BKLT T5:      0
[    10.132] (II) EMGD(0):         GPIO Pin VDD: 0
[    10.132] (II) EMGD(0):         GPIO Pin VEE: 0
[    10.132] (II) EMGD(0):         GPIO Pin BKLT:0
[    10.132] (II) EMGD(0):         DVO i2c pin:  0
[    10.132] (II) EMGD(0):         DVO i2c DAB:  0
[    10.132] (II) EMGD(0):         DVO i2c speed:0
[    10.132] (II) EMGD(0):         DVO ddc pin:  0
[    10.132] (II) EMGD(0):         DVO ddc speed:0
[    10.132] (II) EMGD(0):      Number DTD's:   0
[    10.132] (II) EMGD(0):      Number Attr's:  1
[    10.133] (==) Depth 24 pixmap format is 32 bpp
[    10.137] drmOpenDevice: node name is /dev/dri/card0
[    10.137] drmOpenDevice: open result is 10, (OK)
[    10.137] drmOpenByBusid: Searching for BusID PCI:00:02:00
[    10.137] drmOpenDevice: node name is /dev/dri/card0
[    10.137] drmOpenDevice: open result is 10, (OK)
[    10.137] drmOpenByBusid: drmOpenMinor returns 10
[    10.137] drmOpenByBusid: Interface 1.4 failed, trying 1.1
[    10.137] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    10.494] drmOpenDevice: node name is /dev/dri/card0
[    10.494] drmOpenDevice: open result is 10, (OK)
[    10.494] drmOpenByBusid: Searching for BusID PCI:00:02:00
[    10.494] drmOpenDevice: node name is /dev/dri/card0
[    10.495] drmOpenDevice: open result is 10, (OK)
[    10.495] drmOpenByBusid: drmOpenMinor returns 10
[    10.495] drmOpenByBusid: Interface 1.4 failed, trying 1.1
[    10.495] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    10.495] drmOpenDevice: node name is /dev/dri/card0
[    10.495] drmOpenDevice: open result is 10, (OK)
[    10.495] drmOpenByBusid: Searching for BusID PCI:00:02:00
[    10.495] drmOpenDevice: node name is /dev/dri/card0
[    10.495] drmOpenDevice: open result is 10, (OK)
[    10.495] drmOpenByBusid: drmOpenMinor returns 10
[    10.495] drmOpenByBusid: Interface 1.4 failed, trying 1.1
[    10.495] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    10.496] drmOpenDevice: node name is /dev/dri/card0
[    10.496] drmOpenDevice: open result is 10, (OK)
[    10.496] drmOpenByBusid: Searching for BusID PCI:00:02:00
[    10.496] drmOpenDevice: node name is /dev/dri/card0
[    10.496] drmOpenDevice: open result is 10, (OK)
[    10.497] drmOpenByBusid: drmOpenMinor returns 10
[    10.497] drmOpenByBusid: Interface 1.4 failed, trying 1.1
[    10.497] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    10.510] drmOpenDevice: node name is /dev/dri/card0
[    10.510] drmOpenDevice: open result is 11, (OK)
[    10.510] drmOpenByBusid: Searching for BusID PCI:00:02:00
[    10.510] drmOpenDevice: node name is /dev/dri/card0
[    10.510] drmOpenDevice: open result is 11, (OK)
[    10.510] drmOpenByBusid: drmOpenMinor returns 11
[    10.510] drmOpenByBusid: Interface 1.4 failed, trying 1.1
[    10.510] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    10.510] drmOpenDevice: node name is /dev/dri/card0
[    10.510] drmOpenDevice: open result is 11, (OK)
[    10.510] drmOpenByBusid: Searching for BusID PCI:00:02:00
[    10.510] drmOpenDevice: node name is /dev/dri/card0
[    10.510] drmOpenDevice: open result is 11, (OK)
[    10.510] drmOpenByBusid: drmOpenMinor returns 11
[    10.510] drmOpenByBusid: Interface 1.4 failed, trying 1.1
[    10.510] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    10.511] drmOpenDevice: node name is /dev/dri/card0
[    10.511] drmOpenDevice: open result is 11, (OK)
[    10.511] drmOpenByBusid: Searching for BusID PCI:00:02:00
[    10.511] drmOpenDevice: node name is /dev/dri/card0
[    10.511] drmOpenDevice: open result is 11, (OK)
[    10.511] drmOpenByBusid: drmOpenMinor returns 11
[    10.511] drmOpenByBusid: Interface 1.4 failed, trying 1.1
[    10.511] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    10.518] (II) EMGD(0): [DRI2] Setup complete
[    10.518] (II) EMGD(0): [DRI2]   DRI driver: emgd
[    10.518] (II) EMGD(0): DRI2 initialization complete.
[    10.527] (II) UXA(0): Driver registered support for the following operations:
[    10.527] (II)         solid
[    10.527] (II)         copy
[    10.527] (II)         composite (RENDER acceleration)
[    10.527] (II) EMGD(0): Video acceleration initialization complete
[    10.528] (==) EMGD(0): Backing store disabled
[    10.545] drmOpenDevice: node name is /dev/dri/card0
[    10.545] drmOpenDevice: open result is 12, (OK)
[    10.545] drmOpenByBusid: Searching for BusID PCI:00:02:00
[    10.545] drmOpenDevice: node name is /dev/dri/card0
[    10.545] drmOpenDevice: open result is 12, (OK)
[    10.545] drmOpenByBusid: drmOpenMinor returns 12
[    10.545] drmOpenByBusid: Interface 1.4 failed, trying 1.1
[    10.545] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    10.545] drmOpenDevice: node name is /dev/dri/card0
[    10.545] drmOpenDevice: open result is 12, (OK)
[    10.546] drmOpenByBusid: Searching for BusID PCI:00:02:00
[    10.546] drmOpenDevice: node name is /dev/dri/card0
[    10.546] drmOpenDevice: open result is 12, (OK)
[    10.546] drmOpenByBusid: drmOpenMinor returns 12
[    10.546] drmOpenByBusid: Interface 1.4 failed, trying 1.1
[    10.546] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    10.551] (II) EMGD(0): Hardware Cursor Initialization complete.
[    10.551] (==) EMGD(0): Silken mouse enabled
[    10.551] (==) EMGD(0): DPMS enabled
[    10.553] (==) RandR enabled
[    10.553] (II) Initializing built-in extension Generic Event Extension
[    10.553] (II) Initializing built-in extension SHAPE
[    10.553] (II) Initializing built-in extension MIT-SHM
[    10.553] (II) Initializing built-in extension XInputExtension
[    10.553] (II) Initializing built-in extension XTEST
[    10.553] (II) Initializing built-in extension BIG-REQUESTS
[    10.553] (II) Initializing built-in extension SYNC
[    10.554] (II) Initializing built-in extension XKEYBOARD
[    10.554] (II) Initializing built-in extension XC-MISC
[    10.554] (II) Initializing built-in extension SECURITY
[    10.554] (II) Initializing built-in extension XINERAMA
[    10.554] (II) Initializing built-in extension XFIXES
[    10.554] (II) Initializing built-in extension RENDER
[    10.554] (II) Initializing built-in extension RANDR
[    10.554] (II) Initializing built-in extension COMPOSITE
[    10.554] (II) Initializing built-in extension DAMAGE
[    10.554] (II) Initializing built-in extension GESTURE
[    10.643] drmOpenDevice: node name is /dev/dri/card0
[    10.643] drmOpenDevice: open result is 12, (OK)
[    10.643] drmOpenByBusid: Searching for BusID PCI:00:02:00
[    10.643] drmOpenDevice: node name is /dev/dri/card0
[    10.643] drmOpenDevice: open result is 12, (OK)
[    10.643] drmOpenByBusid: drmOpenMinor returns 12
[    10.643] drmOpenByBusid: Interface 1.4 failed, trying 1.1
[    10.643] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    10.644] drmOpenDevice: node name is /dev/dri/card0
[    10.644] drmOpenDevice: open result is 12, (OK)
[    10.644] drmOpenByBusid: Searching for BusID PCI:00:02:00
[    10.644] drmOpenDevice: node name is /dev/dri/card0
[    10.644] drmOpenDevice: open result is 12, (OK)
[    10.644] drmOpenByBusid: drmOpenMinor returns 12
[    10.644] drmOpenByBusid: Interface 1.4 failed, trying 1.1
[    10.644] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    10.663] drmOpenDevice: node name is /dev/dri/card0
[    10.664] drmOpenDevice: open result is 12, (OK)
[    10.664] drmOpenByBusid: Searching for BusID PCI:00:02:00
[    10.664] drmOpenDevice: node name is /dev/dri/card0
[    10.664] drmOpenDevice: open result is 12, (OK)
[    10.664] drmOpenByBusid: drmOpenMinor returns 12
[    10.664] drmOpenByBusid: Interface 1.4 failed, trying 1.1
[    10.664] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    10.675] drmOpenDevice: node name is /dev/dri/card0
[    10.676] drmOpenDevice: open result is 13, (OK)
[    10.676] drmOpenByBusid: Searching for BusID PCI:00:02:00
[    10.676] drmOpenDevice: node name is /dev/dri/card0
[    10.676] drmOpenDevice: open result is 13, (OK)
[    10.676] drmOpenByBusid: drmOpenMinor returns 13
[    10.676] drmOpenByBusid: Interface 1.4 failed, trying 1.1
[    10.676] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    10.676] drmOpenDevice: node name is /dev/dri/card0
[    10.676] drmOpenDevice: open result is 13, (OK)
[    10.676] drmOpenByBusid: Searching for BusID PCI:00:02:00
[    10.676] drmOpenDevice: node name is /dev/dri/card0
[    10.677] drmOpenDevice: open result is 13, (OK)
[    10.677] drmOpenByBusid: drmOpenMinor returns 13
[    10.677] drmOpenByBusid: Interface 1.4 failed, trying 1.1
[    10.677] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    10.677] drmOpenDevice: node name is /dev/dri/card0
[    10.677] drmOpenDevice: open result is 13, (OK)
[    10.677] drmOpenByBusid: Searching for BusID PCI:00:02:00
[    10.677] drmOpenDevice: node name is /dev/dri/card0
[    10.677] drmOpenDevice: open result is 13, (OK)
[    10.677] drmOpenByBusid: drmOpenMinor returns 13
[    10.677] drmOpenByBusid: Interface 1.4 failed, trying 1.1
[    10.677] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    10.710] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    10.710] (II) AIGLX: enabled GLX_INTEL_swap_event
[    10.710] (II) AIGLX: enabled GLX_SGI_make_current_read
[    10.710] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    10.710] (II) AIGLX: Loaded and initialized /usr/lib/dri/emgd_dri.so
[    10.710] (II) GLX: Initialized DRI2 GL provider for screen 0
[    10.761] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    10.798] (II) config/udev: Adding input device Video Bus (/dev/input/event3)
[    10.798] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    10.798] (II) LoadModule: "evdev"
[    10.799] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    10.802] (II) Module evdev: vendor="X.Org Foundation"
[    10.802] 	compiled for 1.9.2.901, module version = 2.5.99
[    10.802] 	Module class: X.Org XInput Driver
[    10.802] 	ABI class: X.Org XInput driver, version 11.0
[    10.802] (**) Video Bus: always reports core events
[    10.802] (**) Video Bus: Device: "/dev/input/event3"
[    10.812] (--) Video Bus: Found keys
[    10.812] (II) Video Bus: Configuring as keyboard
[    10.812] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    10.812] (**) Option "xkb_rules" "evdev"
[    10.812] (**) Option "xkb_model" "evdev"
[    10.813] (**) Option "xkb_layout" "us"
[    10.822] (II) XKB: reuse xkmfile /var/lib/xkb/server-D378AD8F86E560F712A83EE36E4E5E92C595B9BD.xkm
[    10.926] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    10.926] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    10.926] (**) Power Button: always reports core events
[    10.926] (**) Power Button: Device: "/dev/input/event0"
[    10.927] (--) Power Button: Found keys
[    10.927] (II) Power Button: Configuring as keyboard
[    10.927] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    10.927] (**) Option "xkb_rules" "evdev"
[    10.927] (**) Option "xkb_model" "evdev"
[    10.927] (**) Option "xkb_layout" "us"
[    10.929] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[    10.929] (II) No input driver/identifier specified (ignoring)
[    10.933] (II) config/udev: Adding input device HDA Intel MID Headphone (/dev/input/event8)
[    10.933] (II) No input driver/identifier specified (ignoring)
[    10.937] (II) config/udev: Adding input device HID 04d9:0499 (/dev/input/event5)
[    10.937] (**) HID 04d9:0499: Applying InputClass "evdev pointer catchall"
[    10.937] (**) HID 04d9:0499: always reports core events
[    10.937] (**) HID 04d9:0499: Device: "/dev/input/event5"
[    10.938] (--) HID 04d9:0499: Found 3 mouse buttons
[    10.938] (--) HID 04d9:0499: Found scroll wheel(s)
[    10.938] (--) HID 04d9:0499: Found relative axes
[    10.938] (--) HID 04d9:0499: Found x and y relative axes
[    10.938] (II) HID 04d9:0499: Configuring as mouse
[    10.938] (II) HID 04d9:0499: Adding scrollwheel support
[    10.938] (**) HID 04d9:0499: YAxisMapping: buttons 4 and 5
[    10.938] (**) HID 04d9:0499: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    10.938] (II) XINPUT: Adding extended input device "HID 04d9:0499" (type: MOUSE)
[    10.938] (**) HID 04d9:0499: (accel) keeping acceleration scheme 1
[    10.938] (**) HID 04d9:0499: (accel) acceleration profile 0
[    10.938] (**) HID 04d9:0499: (accel) acceleration factor: 2.000
[    10.938] (**) HID 04d9:0499: (accel) acceleration threshold: 4
[    10.938] (II) HID 04d9:0499: initialized for relative axes.
[    10.939] (II) config/udev: Adding input device HID 04d9:0499 (/dev/input/mouse0)
[    10.939] (II) No input driver/identifier specified (ignoring)
[    10.942] (II) config/udev: Adding input device Dell Dell QuietKey Keyboard (/dev/input/event4)
[    10.942] (**) Dell Dell QuietKey Keyboard: Applying InputClass "evdev keyboard catchall"
[    10.942] (**) Dell Dell QuietKey Keyboard: always reports core events
[    10.942] (**) Dell Dell QuietKey Keyboard: Device: "/dev/input/event4"
[    10.942] (--) Dell Dell QuietKey Keyboard: Found keys
[    10.943] (II) Dell Dell QuietKey Keyboard: Configuring as keyboard
[    10.943] (II) XINPUT: Adding extended input device "Dell Dell QuietKey Keyboard" (type: KEYBOARD)
[    10.943] (**) Option "xkb_rules" "evdev"
[    10.943] (**) Option "xkb_model" "evdev"
[    10.943] (**) Option "xkb_layout" "us"
[    10.947] (II) config/udev: Adding input device DIALOGUE INC PenMount USB (/dev/input/event6)
[    10.947] (**) DIALOGUE INC PenMount USB: Applying InputClass "evdev pointer catchall"
[    10.947] (**) DIALOGUE INC PenMount USB: always reports core events
[    10.947] (**) DIALOGUE INC PenMount USB: Device: "/dev/input/event6"
[    10.948] (--) DIALOGUE INC PenMount USB: Found 3 mouse buttons
[    10.948] (--) DIALOGUE INC PenMount USB: Found absolute axes
[    10.948] (--) DIALOGUE INC PenMount USB: Found x and y absolute axes
[    10.948] (II) DIALOGUE INC PenMount USB: Configuring as mouse
[    10.948] (**) DIALOGUE INC PenMount USB: YAxisMapping: buttons 4 and 5
[    10.948] (**) DIALOGUE INC PenMount USB: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    10.948] (II) XINPUT: Adding extended input device "DIALOGUE INC PenMount USB" (type: MOUSE)
[    10.948] (II) DIALOGUE INC PenMount USB: initialized for absolute axes.
[    10.949] (II) config/udev: Adding input device DIALOGUE INC PenMount USB (/dev/input/js0)
[    10.949] (II) No input driver/identifier specified (ignoring)
[    10.950] (II) config/udev: Adding input device DIALOGUE INC PenMount USB (/dev/input/mouse1)
[    10.950] (II) No input driver/identifier specified (ignoring)
[    10.959] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    10.959] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    10.959] (**) AT Translated Set 2 keyboard: always reports core events
[    10.959] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    10.959] (--) AT Translated Set 2 keyboard: Found keys
[    10.959] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    10.959] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    10.960] (**) Option "xkb_rules" "evdev"
[    10.960] (**) Option "xkb_model" "evdev"
[    10.960] (**) Option "xkb_layout" "us"
[    10.961] (II) config/udev: Adding input device PS/2 Generic Mouse (/dev/input/event7)
[    10.962] (**) PS/2 Generic Mouse: Applying InputClass "evdev pointer catchall"
[    10.962] (**) PS/2 Generic Mouse: always reports core events
[    10.962] (**) PS/2 Generic Mouse: Device: "/dev/input/event7"
[    10.962] (--) PS/2 Generic Mouse: Found 3 mouse buttons
[    10.962] (--) PS/2 Generic Mouse: Found relative axes
[    10.962] (--) PS/2 Generic Mouse: Found x and y relative axes
[    10.962] (II) PS/2 Generic Mouse: Configuring as mouse
[    10.962] (**) PS/2 Generic Mouse: YAxisMapping: buttons 4 and 5
[    10.962] (**) PS/2 Generic Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    10.962] (II) XINPUT: Adding extended input device "PS/2 Generic Mouse" (type: MOUSE)
[    10.962] (**) PS/2 Generic Mouse: (accel) keeping acceleration scheme 1
[    10.962] (**) PS/2 Generic Mouse: (accel) acceleration profile 0
[    10.962] (**) PS/2 Generic Mouse: (accel) acceleration factor: 2.000
[    10.962] (**) PS/2 Generic Mouse: (accel) acceleration threshold: 4
[    10.963] (II) PS/2 Generic Mouse: initialized for relative axes.
[    10.963] (II) config/udev: Adding input device PS/2 Generic Mouse (/dev/input/mouse2)
[    10.963] (II) No input driver/identifier specified (ignoring)
[   116.301] (II) AIGLX: Suspending AIGLX clients for VT switch

---

