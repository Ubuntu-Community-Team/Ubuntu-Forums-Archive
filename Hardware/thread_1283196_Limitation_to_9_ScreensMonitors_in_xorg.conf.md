---
title: "Limitation to 9 Screens/Monitors in xorg.conf?"
date: 2009-10-05
forum: Hardware
---

### Post by MikeTC on 2009-10-05
Hello@all

I'm fighting with the following configuration:

Ubuntu            9.04 x64
Nvidia Driver   185.18.36

Asus P6T6 WS Revolution (3 * PCIE x16)
3 * Nvidia QUADRO NVS 450 (4 DisplayPorts each)
12 * 24" Samsung SyncMaster 2443BW @1920*1200

All graphic boards are detected in lspci:
```
00:00.0 Host bridge: Intel Corporation X58 I/O Hub to ESI Port (rev 12)
00:01.0 PCI bridge: Intel Corporation X58 I/O Hub PCI Express Root Port 1 (rev 12)
00:03.0 PCI bridge: Intel Corporation X58 I/O Hub PCI Express Root Port 3 (rev 12)
00:07.0 PCI bridge: Intel Corporation X58 I/O Hub PCI Express Root Port 7 (rev 12)
00:10.0 PIC: Intel Corporation X58 Physical and Link Layer Registers Port 0 (rev 12)
00:10.1 PIC: Intel Corporation X58 Routing and Protocol Layer Registers Port 0 (rev 12)
00:14.0 PIC: Intel Corporation X58 I/O Hub System Management Registers (rev 12)
00:14.1 PIC: Intel Corporation X58 I/O Hub GPIO and Scratch Pad Registers (rev 12)
00:14.2 PIC: Intel Corporation X58 I/O Hub Control Status and RAS Registers (rev 12)
00:14.3 PIC: Intel Corporation X58 I/O Hub Throttle Registers (rev 12)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 1
00:1c.1 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 2
00:1c.2 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 3
00:1c.3 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 4
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 SATA controller: Intel Corporation 82801JI (ICH10 Family) SATA AHCI Controller
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
02:00.0 PCI bridge: nVidia Corporation Device 05b1 (rev a3)
03:00.0 PCI bridge: nVidia Corporation Device 05b1 (rev a3)
03:02.0 PCI bridge: nVidia Corporation Device 05b1 (rev a3)
04:00.0 PCI bridge: nVidia Corporation PCI express bridge for Quadro Plex S4 / Tesla S870 / Tesla S1070 (rev a3)
05:00.0 PCI bridge: nVidia Corporation PCI express bridge for Quadro Plex S4 / Tesla S870 / Tesla S1070 (rev a3)
05:02.0 PCI bridge: nVidia Corporation PCI express bridge for Quadro Plex S4 / Tesla S870 / Tesla S1070 (rev a3)
06:00.0 3D controller: nVidia Corporation Quadro NVS 450 (rev a1)
07:00.0 VGA compatible controller: nVidia Corporation Quadro NVS 450 (rev a1)
08:00.0 PCI bridge: nVidia Corporation PCI express bridge for Quadro Plex S4 / Tesla S870 / Tesla S1070 (rev a3)
09:00.0 PCI bridge: nVidia Corporation PCI express bridge for Quadro Plex S4 / Tesla S870 / Tesla S1070 (rev a3)
09:02.0 PCI bridge: nVidia Corporation PCI express bridge for Quadro Plex S4 / Tesla S870 / Tesla S1070 (rev a3)
0a:00.0 3D controller: nVidia Corporation Quadro NVS 450 (rev a1)
0b:00.0 VGA compatible controller: nVidia Corporation Quadro NVS 450 (rev a1)
0c:00.0 PCI bridge: nVidia Corporation PCI express bridge for Quadro Plex S4 / Tesla S870 / Tesla S1070 (rev a3)
0d:00.0 PCI bridge: nVidia Corporation PCI express bridge for Quadro Plex S4 / Tesla S870 / Tesla S1070 (rev a3)
0d:02.0 PCI bridge: nVidia Corporation PCI express bridge for Quadro Plex S4 / Tesla S870 / Tesla S1070 (rev a3)
0e:00.0 3D controller: nVidia Corporation Quadro NVS 450 (rev a1)
0f:00.0 VGA compatible controller: nVidia Corporation Quadro NVS 450 (rev a1)
10:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6121 SATA II Controller (rev b2)
11:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
12:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)


```No problem with up to 9 monitors enabled unless I define 10, 11 or 12 monitors in xorg.conf. Various configurations with 9 monitors are testet so all monitors an graphic boards are working correct.

With more than 9 monitors defined Nvidia-Logo appears on displays but Xserver won't start and stops by "Checking battery state" on display. After three retries Xserver starts in low graphic mode for debugging. nothing special in Xorg.0.log except the last line:
```

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-15-server x86_64 Ubuntu
Current Operating System: Linux LCDWall00876 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:48:52 UTC 2009 x86_64
Build Date: 09 April 2009  02:11:54AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@crested.buildd) 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Oct  5 17:50:17 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Screen "Screen1" (1)
(**) |   |-->Monitor "Monitor1"
(**) |   |-->Device "Device1"
(**) |-->Screen "Screen2" (2)
(**) |   |-->Monitor "Monitor2"
(**) |   |-->Device "Device2"
(**) |-->Screen "Screen3" (3)
(**) |   |-->Monitor "Monitor3"
(**) |   |-->Device "Device3"
(**) |-->Screen "Screen4" (4)
(**) |   |-->Monitor "Monitor4"
(**) |   |-->Device "Device4"
(**) |-->Screen "Screen5" (5)
(**) |   |-->Monitor "Monitor5"
(**) |   |-->Device "Device5"
(**) |-->Screen "Screen6" (6)
(**) |   |-->Monitor "Monitor6"
(**) |   |-->Device "Device6"
(**) |-->Screen "Screen7" (7)
(**) |   |-->Monitor "Monitor7"
(**) |   |-->Device "Device7"
(**) |-->Screen "Screen8" (8)
(**) |   |-->Monitor "Monitor8"
(**) |   |-->Device "Device8"
(**) |-->Screen "Screen9" (9)
(**) |   |-->Monitor "Monitor9"
(**) |   |-->Device "Device9"
(**) |-->Screen "Screen10" (10)
(**) |   |-->Monitor "Monitor10"
(**) |   |-->Device "Device10"
(**) |-->Screen "Screen11" (11)
(**) |   |-->Monitor "Monitor11"
(**) |   |-->Device "Device11"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(**) Option "Xinerama" "1"
(==) Automatically adding devices
(==) Automatically enabling devices
(**) Xinerama: enabled
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0xb40
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 5.0
    X.Org XInput driver : 4.0
    X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(!!) More than one possible primary device found
(!!) More than one possible primary device found
(--) PCI:*(0@7:0:0) nVidia Corporation Quadro NVS 450 rev 161, Mem @ 0xd7000000/16777216, 0x70000000/268435456, 0xd4000000/33554432, I/O @ 0x00007c00/128, BIOS @ 0x????????/131072
(--) PCI: (0@11:0:0) nVidia Corporation Quadro NVS 450 rev 161, Mem @ 0xdf000000/16777216, 0x90000000/268435456, 0xdc000000/33554432, I/O @ 0x00009c00/128, BIOS @ 0x????????/131072
(--) PCI: (0@15:0:0) nVidia Corporation Quadro NVS 450 rev 161, Mem @ 0xfa000000/16777216, 0xb0000000/268435456, 0xf8000000/33554432, I/O @ 0x0000bc00/128, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  185.18.36  Fri Aug 14 18:27:24 PDT 2009
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  185.18.36  Fri Aug 14 17:51:02 PDT 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 07@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "TwinView" "0"
(**) NVIDIA(0): Option "MetaModes" "DFP-0: nvidia-auto-select +0+0"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU Quadro NVS 450 (G98GL) at PCI:7:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 62.98.43.00.07
(II) NVIDIA(0): Detected PCI Express Link width: 4X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on Quadro NVS 450 at PCI:7:0:0:
(--) NVIDIA(0):     Samsung SyncMaster (DFP-0)
(--) NVIDIA(0):     Samsung SyncMaster (DFP-1)
(--) NVIDIA(0): Samsung SyncMaster (DFP-0): 165.0 MHz maximum pixel clock
(--) NVIDIA(0): Samsung SyncMaster (DFP-0): Internal Single Link TMDS
(--) NVIDIA(0): Samsung SyncMaster (DFP-1): 165.0 MHz maximum pixel clock
(--) NVIDIA(0): Samsung SyncMaster (DFP-1): Internal Single Link TMDS
(II) NVIDIA(0): Display Device found referenced in MetaMode: DFP-0
(II) NVIDIA(0): Assigned Display Device: DFP-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "DFP-0:nvidia-auto-select+0+0"
(II) NVIDIA(0): Virtual screen size determined to be 1920 x 1200
(--) NVIDIA(0): DPI set to (93, 95); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(**) NVIDIA(1): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(1): RGB weight 888
(==) NVIDIA(1): Default visual is TrueColor
(==) NVIDIA(1): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(1): Option "TwinView" "0"
(**) NVIDIA(1): Option "MetaModes" "DFP-1: nvidia-auto-select +0+0"
(**) NVIDIA(1): Enabling RENDER acceleration
(II) NVIDIA(1): NVIDIA GPU Quadro NVS 450 (G98GL) at PCI:7:0:0 (GPU-0)
(--) NVIDIA(1): Memory: 524288 kBytes
(--) NVIDIA(1): VideoBIOS: 62.98.43.00.07
(II) NVIDIA(1): Detected PCI Express Link width: 4X
(--) NVIDIA(1): Interlaced video modes are supported on this GPU
(--) NVIDIA(1): Connected display device(s) on Quadro NVS 450 at PCI:7:0:0:
(--) NVIDIA(1):     Samsung SyncMaster (DFP-0)
(--) NVIDIA(1):     Samsung SyncMaster (DFP-1)
(--) NVIDIA(1): Samsung SyncMaster (DFP-0): 165.0 MHz maximum pixel clock
(--) NVIDIA(1): Samsung SyncMaster (DFP-0): Internal Single Link TMDS
(--) NVIDIA(1): Samsung SyncMaster (DFP-1): 165.0 MHz maximum pixel clock
(--) NVIDIA(1): Samsung SyncMaster (DFP-1): Internal Single Link TMDS
(II) NVIDIA(1): Display Device found referenced in MetaMode: DFP-1
(II) NVIDIA(1): Assigned Display Device: DFP-1
(II) NVIDIA(1): Validated modes:
(II) NVIDIA(1):     "DFP-1:nvidia-auto-select+0+0"
(II) NVIDIA(1): Virtual screen size determined to be 1920 x 1200
(--) NVIDIA(1): DPI set to (93, 95); computed from "UseEdidDpi" X config
(--) NVIDIA(1):     option
(==) NVIDIA(1): Enabling 32-bit ARGB GLX visuals.
(**) NVIDIA(2): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(2): RGB weight 888
(==) NVIDIA(2): Default visual is TrueColor
(==) NVIDIA(2): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(2): Option "TwinView" "0"
(**) NVIDIA(2): Option "MetaModes" "DFP-0: nvidia-auto-select +0+0"
(**) NVIDIA(2): Enabling RENDER acceleration
(II) NVIDIA(2): NVIDIA GPU Quadro NVS 450 (G98GL) at PCI:6:0:0 (GPU-1)
(--) NVIDIA(2): Memory: 524288 kBytes
(--) NVIDIA(2): VideoBIOS: 62.98.43.00.07
(II) NVIDIA(2): Detected PCI Express Link width: 4X
(--) NVIDIA(2): Interlaced video modes are supported on this GPU
(--) NVIDIA(2): Connected display device(s) on Quadro NVS 450 at PCI:6:0:0:
(--) NVIDIA(2):     Samsung SyncMaster (DFP-0)
(--) NVIDIA(2):     Samsung SyncMaster (DFP-1)
(--) NVIDIA(2): Samsung SyncMaster (DFP-0): 165.0 MHz maximum pixel clock
(--) NVIDIA(2): Samsung SyncMaster (DFP-0): Internal Single Link TMDS
(--) NVIDIA(2): Samsung SyncMaster (DFP-1): 165.0 MHz maximum pixel clock
(--) NVIDIA(2): Samsung SyncMaster (DFP-1): Internal Single Link TMDS
(II) NVIDIA(2): Display Device found referenced in MetaMode: DFP-0
(II) NVIDIA(2): Assigned Display Device: DFP-0
(II) NVIDIA(2): Validated modes:
(II) NVIDIA(2):     "DFP-0:nvidia-auto-select+0+0"
(II) NVIDIA(2): Virtual screen size determined to be 1920 x 1200
(--) NVIDIA(2): DPI set to (93, 95); computed from "UseEdidDpi" X config
(--) NVIDIA(2):     option
(==) NVIDIA(2): Enabling 32-bit ARGB GLX visuals.
(**) NVIDIA(3): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(3): RGB weight 888
(==) NVIDIA(3): Default visual is TrueColor
(==) NVIDIA(3): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(3): Option "TwinView" "0"
(**) NVIDIA(3): Option "MetaModes" "DFP-1: nvidia-auto-select +0+0"
(**) NVIDIA(3): Enabling RENDER acceleration
(II) NVIDIA(3): NVIDIA GPU Quadro NVS 450 (G98GL) at PCI:6:0:0 (GPU-1)
(--) NVIDIA(3): Memory: 524288 kBytes
(--) NVIDIA(3): VideoBIOS: 62.98.43.00.07
(II) NVIDIA(3): Detected PCI Express Link width: 4X
(--) NVIDIA(3): Interlaced video modes are supported on this GPU
(--) NVIDIA(3): Connected display device(s) on Quadro NVS 450 at PCI:6:0:0:
(--) NVIDIA(3):     Samsung SyncMaster (DFP-0)
(--) NVIDIA(3):     Samsung SyncMaster (DFP-1)
(--) NVIDIA(3): Samsung SyncMaster (DFP-0): 165.0 MHz maximum pixel clock
(--) NVIDIA(3): Samsung SyncMaster (DFP-0): Internal Single Link TMDS
(--) NVIDIA(3): Samsung SyncMaster (DFP-1): 165.0 MHz maximum pixel clock
(--) NVIDIA(3): Samsung SyncMaster (DFP-1): Internal Single Link TMDS
(II) NVIDIA(3): Display Device found referenced in MetaMode: DFP-1
(II) NVIDIA(3): Assigned Display Device: DFP-1
(II) NVIDIA(3): Validated modes:
(II) NVIDIA(3):     "DFP-1:nvidia-auto-select+0+0"
(II) NVIDIA(3): Virtual screen size determined to be 1920 x 1200
(--) NVIDIA(3): DPI set to (93, 95); computed from "UseEdidDpi" X config
(--) NVIDIA(3):     option
(==) NVIDIA(3): Enabling 32-bit ARGB GLX visuals.
(**) NVIDIA(4): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(4): RGB weight 888
(==) NVIDIA(4): Default visual is TrueColor
(==) NVIDIA(4): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(4): Option "TwinView" "0"
(**) NVIDIA(4): Option "MetaModes" "DFP-1: nvidia-auto-select +0+0"
(**) NVIDIA(4): Enabling RENDER acceleration
(II) NVIDIA(4): NVIDIA GPU Quadro NVS 450 (G98GL) at PCI:11:0:0 (GPU-2)
(--) NVIDIA(4): Memory: 524288 kBytes
(--) NVIDIA(4): VideoBIOS: 62.98.43.00.07
(II) NVIDIA(4): Detected PCI Express Link width: 4X
(--) NVIDIA(4): Interlaced video modes are supported on this GPU
(--) NVIDIA(4): Connected display device(s) on Quadro NVS 450 at PCI:11:0:0:
(--) NVIDIA(4):     Samsung SyncMaster (DFP-0)
(--) NVIDIA(4):     Samsung SyncMaster (DFP-1)
(--) NVIDIA(4): Samsung SyncMaster (DFP-0): 165.0 MHz maximum pixel clock
(--) NVIDIA(4): Samsung SyncMaster (DFP-0): Internal Single Link TMDS
(--) NVIDIA(4): Samsung SyncMaster (DFP-1): 165.0 MHz maximum pixel clock
(--) NVIDIA(4): Samsung SyncMaster (DFP-1): Internal Single Link TMDS
(II) NVIDIA(4): Display Device found referenced in MetaMode: DFP-1
(II) NVIDIA(4): Assigned Display Device: DFP-1
(II) NVIDIA(4): Validated modes:
(II) NVIDIA(4):     "DFP-1:nvidia-auto-select+0+0"
(II) NVIDIA(4): Virtual screen size determined to be 1920 x 1200
(--) NVIDIA(4): DPI set to (93, 95); computed from "UseEdidDpi" X config
(--) NVIDIA(4):     option
(==) NVIDIA(4): Enabling 32-bit ARGB GLX visuals.
(**) NVIDIA(5): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(5): RGB weight 888
(==) NVIDIA(5): Default visual is TrueColor
(==) NVIDIA(5): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(5): Option "TwinView" "0"
(**) NVIDIA(5): Option "MetaModes" "DFP-1: nvidia-auto-select +0+0"
(**) NVIDIA(5): Enabling RENDER acceleration
(II) NVIDIA(5): NVIDIA GPU Quadro NVS 450 (G98GL) at PCI:11:0:0 (GPU-2)
(--) NVIDIA(5): Memory: 524288 kBytes
(--) NVIDIA(5): VideoBIOS: 62.98.43.00.07
(II) NVIDIA(5): Detected PCI Express Link width: 4X
(--) NVIDIA(5): Interlaced video modes are supported on this GPU
(--) NVIDIA(5): Connected display device(s) on Quadro NVS 450 at PCI:11:0:0:
(--) NVIDIA(5):     Samsung SyncMaster (DFP-0)
(--) NVIDIA(5):     Samsung SyncMaster (DFP-1)
(--) NVIDIA(5): Samsung SyncMaster (DFP-0): 165.0 MHz maximum pixel clock
(--) NVIDIA(5): Samsung SyncMaster (DFP-0): Internal Single Link TMDS
(--) NVIDIA(5): Samsung SyncMaster (DFP-1): 165.0 MHz maximum pixel clock
(--) NVIDIA(5): Samsung SyncMaster (DFP-1): Internal Single Link TMDS
(II) NVIDIA(5): Assigned Display Device: DFP-0
(II) NVIDIA(5): Validated modes:
(II) NVIDIA(5):     "DFP-1:nvidia-auto-select+0+0"
(II) NVIDIA(5): Virtual screen size determined to be 1920 x 1200
(--) NVIDIA(5): DPI set to (93, 95); computed from "UseEdidDpi" X config
(--) NVIDIA(5):     option
(==) NVIDIA(5): Enabling 32-bit ARGB GLX visuals.
(**) NVIDIA(6): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(6): RGB weight 888
(==) NVIDIA(6): Default visual is TrueColor
(==) NVIDIA(6): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(6): Option "TwinView" "0"
(**) NVIDIA(6): Option "MetaModes" "DFP-1: nvidia-auto-select +0+0"
(**) NVIDIA(6): Enabling RENDER acceleration
(II) NVIDIA(6): NVIDIA GPU Quadro NVS 450 (G98GL) at PCI:10:0:0 (GPU-3)
(--) NVIDIA(6): Memory: 524288 kBytes
(--) NVIDIA(6): VideoBIOS: 62.98.43.00.07
(II) NVIDIA(6): Detected PCI Express Link width: 4X
(--) NVIDIA(6): Interlaced video modes are supported on this GPU
(--) NVIDIA(6): Connected display device(s) on Quadro NVS 450 at PCI:10:0:0:
(--) NVIDIA(6):     Samsung SyncMaster (DFP-0)
(--) NVIDIA(6):     Samsung SyncMaster (DFP-1)
(--) NVIDIA(6): Samsung SyncMaster (DFP-0): 165.0 MHz maximum pixel clock
(--) NVIDIA(6): Samsung SyncMaster (DFP-0): Internal Single Link TMDS
(--) NVIDIA(6): Samsung SyncMaster (DFP-1): 165.0 MHz maximum pixel clock
(--) NVIDIA(6): Samsung SyncMaster (DFP-1): Internal Single Link TMDS
(II) NVIDIA(6): Display Device found referenced in MetaMode: DFP-1
(II) NVIDIA(6): Assigned Display Device: DFP-1
(II) NVIDIA(6): Validated modes:
(II) NVIDIA(6):     "DFP-1:nvidia-auto-select+0+0"
(II) NVIDIA(6): Virtual screen size determined to be 1920 x 1200
(--) NVIDIA(6): DPI set to (93, 95); computed from "UseEdidDpi" X config
(--) NVIDIA(6):     option
(==) NVIDIA(6): Enabling 32-bit ARGB GLX visuals.
(**) NVIDIA(7): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(7): RGB weight 888
(==) NVIDIA(7): Default visual is TrueColor
(==) NVIDIA(7): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(7): Option "TwinView" "0"
(**) NVIDIA(7): Option "MetaModes" "DFP-1: nvidia-auto-select +0+0"
(**) NVIDIA(7): Enabling RENDER acceleration
(II) NVIDIA(7): NVIDIA GPU Quadro NVS 450 (G98GL) at PCI:10:0:0 (GPU-3)
(--) NVIDIA(7): Memory: 524288 kBytes
(--) NVIDIA(7): VideoBIOS: 62.98.43.00.07
(II) NVIDIA(7): Detected PCI Express Link width: 4X
(--) NVIDIA(7): Interlaced video modes are supported on this GPU
(--) NVIDIA(7): Connected display device(s) on Quadro NVS 450 at PCI:10:0:0:
(--) NVIDIA(7):     Samsung SyncMaster (DFP-0)
(--) NVIDIA(7):     Samsung SyncMaster (DFP-1)
(--) NVIDIA(7): Samsung SyncMaster (DFP-0): 165.0 MHz maximum pixel clock
(--) NVIDIA(7): Samsung SyncMaster (DFP-0): Internal Single Link TMDS
(--) NVIDIA(7): Samsung SyncMaster (DFP-1): 165.0 MHz maximum pixel clock
(--) NVIDIA(7): Samsung SyncMaster (DFP-1): Internal Single Link TMDS
(II) NVIDIA(7): Assigned Display Device: DFP-0
(II) NVIDIA(7): Validated modes:
(II) NVIDIA(7):     "DFP-1:nvidia-auto-select+0+0"
(II) NVIDIA(7): Virtual screen size determined to be 1920 x 1200
(--) NVIDIA(7): DPI set to (93, 95); computed from "UseEdidDpi" X config
(--) NVIDIA(7):     option
(==) NVIDIA(7): Enabling 32-bit ARGB GLX visuals.
(**) NVIDIA(8): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(8): RGB weight 888
(==) NVIDIA(8): Default visual is TrueColor
(==) NVIDIA(8): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(8): Option "TwinView" "0"
(**) NVIDIA(8): Option "MetaModes" "DFP-1: nvidia-auto-select +0+0"
(**) NVIDIA(8): Enabling RENDER acceleration
(II) NVIDIA(8): NVIDIA GPU Quadro NVS 450 (G98GL) at PCI:15:0:0 (GPU-4)
(--) NVIDIA(8): Memory: 524288 kBytes
(--) NVIDIA(8): VideoBIOS: 62.98.43.00.07
(II) NVIDIA(8): Detected PCI Express Link width: 4X
(--) NVIDIA(8): Interlaced video modes are supported on this GPU
(--) NVIDIA(8): Connected display device(s) on Quadro NVS 450 at PCI:15:0:0:
(--) NVIDIA(8):     Samsung SyncMaster (DFP-0)
(--) NVIDIA(8):     Samsung SyncMaster (DFP-1)
(--) NVIDIA(8): Samsung SyncMaster (DFP-0): 165.0 MHz maximum pixel clock
(--) NVIDIA(8): Samsung SyncMaster (DFP-0): Internal Single Link TMDS
(--) NVIDIA(8): Samsung SyncMaster (DFP-1): 165.0 MHz maximum pixel clock
(--) NVIDIA(8): Samsung SyncMaster (DFP-1): Internal Single Link TMDS
(II) NVIDIA(8): Display Device found referenced in MetaMode: DFP-1
(II) NVIDIA(8): Assigned Display Device: DFP-1
(II) NVIDIA(8): Validated modes:
(II) NVIDIA(8):     "DFP-1:nvidia-auto-select+0+0"
(II) NVIDIA(8): Virtual screen size determined to be 1920 x 1200
(--) NVIDIA(8): DPI set to (93, 95); computed from "UseEdidDpi" X config
(--) NVIDIA(8):     option
(==) NVIDIA(8): Enabling 32-bit ARGB GLX visuals.
(**) NVIDIA(9): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(9): RGB weight 888
(==) NVIDIA(9): Default visual is TrueColor
(==) NVIDIA(9): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(9): Option "TwinView" "0"
(**) NVIDIA(9): Option "MetaModes" "DFP-1: nvidia-auto-select +0+0"
(**) NVIDIA(9): Enabling RENDER acceleration
(II) NVIDIA(9): NVIDIA GPU Quadro NVS 450 (G98GL) at PCI:15:0:0 (GPU-4)
(--) NVIDIA(9): Memory: 524288 kBytes
(--) NVIDIA(9): VideoBIOS: 62.98.43.00.07
(II) NVIDIA(9): Detected PCI Express Link width: 4X
(--) NVIDIA(9): Interlaced video modes are supported on this GPU
(--) NVIDIA(9): Connected display device(s) on Quadro NVS 450 at PCI:15:0:0:
(--) NVIDIA(9):     Samsung SyncMaster (DFP-0)
(--) NVIDIA(9):     Samsung SyncMaster (DFP-1)
(--) NVIDIA(9): Samsung SyncMaster (DFP-0): 165.0 MHz maximum pixel clock
(--) NVIDIA(9): Samsung SyncMaster (DFP-0): Internal Single Link TMDS
(--) NVIDIA(9): Samsung SyncMaster (DFP-1): 165.0 MHz maximum pixel clock
(--) NVIDIA(9): Samsung SyncMaster (DFP-1): Internal Single Link TMDS
(II) NVIDIA(9): Assigned Display Device: DFP-0
(II) NVIDIA(9): Validated modes:
(II) NVIDIA(9):     "DFP-1:nvidia-auto-select+0+0"
(II) NVIDIA(9): Virtual screen size determined to be 1920 x 1200
(--) NVIDIA(9): DPI set to (93, 95); computed from "UseEdidDpi" X config
(--) NVIDIA(9):     option
(==) NVIDIA(9): Enabling 32-bit ARGB GLX visuals.
(**) NVIDIA(10): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(10): RGB weight 888
(==) NVIDIA(10): Default visual is TrueColor
(==) NVIDIA(10): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(10): Option "TwinView" "0"
(**) NVIDIA(10): Option "MetaModes" "DFP-1: nvidia-auto-select +0+0"
(**) NVIDIA(10): Enabling RENDER acceleration
(II) NVIDIA(10): NVIDIA GPU Quadro NVS 450 (G98GL) at PCI:14:0:0 (GPU-5)
(--) NVIDIA(10): Memory: 524288 kBytes
(--) NVIDIA(10): VideoBIOS: 62.98.43.00.07
(II) NVIDIA(10): Detected PCI Express Link width: 4X
(--) NVIDIA(10): Interlaced video modes are supported on this GPU
(--) NVIDIA(10): Connected display device(s) on Quadro NVS 450 at PCI:14:0:0:
(--) NVIDIA(10):     Samsung SyncMaster (DFP-0)
(--) NVIDIA(10):     Samsung SyncMaster (DFP-1)
(--) NVIDIA(10): Samsung SyncMaster (DFP-0): 165.0 MHz maximum pixel clock
(--) NVIDIA(10): Samsung SyncMaster (DFP-0): Internal Single Link TMDS
(--) NVIDIA(10): Samsung SyncMaster (DFP-1): 165.0 MHz maximum pixel clock
(--) NVIDIA(10): Samsung SyncMaster (DFP-1): Internal Single Link TMDS
(II) NVIDIA(10): Display Device found referenced in MetaMode: DFP-1
(II) NVIDIA(10): Assigned Display Device: DFP-1
(II) NVIDIA(10): Validated modes:
(II) NVIDIA(10):     "DFP-1:nvidia-auto-select+0+0"
(II) NVIDIA(10): Virtual screen size determined to be 1920 x 1200
(--) NVIDIA(10): DPI set to (93, 95); computed from "UseEdidDpi" X config
(--) NVIDIA(10):     option
(==) NVIDIA(10): Enabling 32-bit ARGB GLX visuals.
(**) NVIDIA(11): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(11): RGB weight 888
(==) NVIDIA(11): Default visual is TrueColor
(==) NVIDIA(11): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(11): Option "TwinView" "0"
(**) NVIDIA(11): Option "MetaModes" "DFP-1: nvidia-auto-select +0+0"
(**) NVIDIA(11): Enabling RENDER acceleration
(II) NVIDIA(11): NVIDIA GPU Quadro NVS 450 (G98GL) at PCI:14:0:0 (GPU-5)
(--) NVIDIA(11): Memory: 524288 kBytes
(--) NVIDIA(11): VideoBIOS: 62.98.43.00.07
(II) NVIDIA(11): Detected PCI Express Link width: 4X
(--) NVIDIA(11): Interlaced video modes are supported on this GPU
(--) NVIDIA(11): Connected display device(s) on Quadro NVS 450 at PCI:14:0:0:
(--) NVIDIA(11):     Samsung SyncMaster (DFP-0)
(--) NVIDIA(11):     Samsung SyncMaster (DFP-1)
(--) NVIDIA(11): Samsung SyncMaster (DFP-0): 165.0 MHz maximum pixel clock
(--) NVIDIA(11): Samsung SyncMaster (DFP-0): Internal Single Link TMDS
(--) NVIDIA(11): Samsung SyncMaster (DFP-1): 165.0 MHz maximum pixel clock
(--) NVIDIA(11): Samsung SyncMaster (DFP-1): Internal Single Link TMDS
(II) NVIDIA(11): Assigned Display Device: DFP-0
(II) NVIDIA(11): Validated modes:
(II) NVIDIA(11):     "DFP-1:nvidia-auto-select+0+0"
(II) NVIDIA(11): Virtual screen size determined to be 1920 x 1200
(--) NVIDIA(11): DPI set to (93, 95); computed from "UseEdidDpi" X config
(--) NVIDIA(11):     option
(==) NVIDIA(11): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  Yes, I do.
(II) resource ranges after preInit:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Setting mode "DFP-0:nvidia-auto-select+0+0"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) NVIDIA(1): Initialized GPU GART.
(II) NVIDIA(1): Setting mode "DFP-1:nvidia-auto-select+0+0"
(II) NVIDIA(1): NVIDIA 3D Acceleration Architecture Initialized
(==) NVIDIA(1): Disabling shared memory pixmaps
(II) NVIDIA(1): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(1): Backing store disabled
(==) NVIDIA(1): Silken mouse enabled
(II) NVIDIA(1): DPMS enabled
(==) RandR enabled
(II) NVIDIA(2): Initialized GPU GART.
(II) NVIDIA(2): Setting mode "DFP-0:nvidia-auto-select+0+0"
(II) NVIDIA(2): NVIDIA 3D Acceleration Architecture Initialized
(==) NVIDIA(2): Disabling shared memory pixmaps
(II) NVIDIA(2): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(2): Backing store disabled
(==) NVIDIA(2): Silken mouse enabled
(II) NVIDIA(2): DPMS enabled
(==) RandR enabled
(II) NVIDIA(3): Initialized GPU GART.
(II) NVIDIA(3): Setting mode "DFP-1:nvidia-auto-select+0+0"
(II) NVIDIA(3): NVIDIA 3D Acceleration Architecture Initialized
(==) NVIDIA(3): Disabling shared memory pixmaps
(II) NVIDIA(3): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(3): Backing store disabled
(==) NVIDIA(3): Silken mouse enabled
(II) NVIDIA(3): DPMS enabled
(==) RandR enabled
(II) NVIDIA(4): Initialized GPU GART.
(II) NVIDIA(4): Setting mode "DFP-1:nvidia-auto-select+0+0"
(II) NVIDIA(4): NVIDIA 3D Acceleration Architecture Initialized
(==) NVIDIA(4): Disabling shared memory pixmaps
(II) NVIDIA(4): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(4): Backing store disabled
(==) NVIDIA(4): Silken mouse enabled
(II) NVIDIA(4): DPMS enabled
(==) RandR enabled
(II) NVIDIA(5): Initialized GPU GART.
(II) NVIDIA(5): Setting mode "DFP-1:nvidia-auto-select+0+0"
(II) NVIDIA(5): NVIDIA 3D Acceleration Architecture Initialized
(==) NVIDIA(5): Disabling shared memory pixmaps
(II) NVIDIA(5): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(5): Backing store disabled
(==) NVIDIA(5): Silken mouse enabled
(II) NVIDIA(5): DPMS enabled
(==) RandR enabled
(II) NVIDIA(6): Initialized GPU GART.
(II) NVIDIA(6): Setting mode "DFP-1:nvidia-auto-select+0+0"
(II) NVIDIA(6): NVIDIA 3D Acceleration Architecture Initialized
(==) NVIDIA(6): Disabling shared memory pixmaps
(II) NVIDIA(6): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(6): Backing store disabled
(==) NVIDIA(6): Silken mouse enabled
(II) NVIDIA(6): DPMS enabled
(==) RandR enabled
(II) NVIDIA(7): Initialized GPU GART.
(II) NVIDIA(7): Setting mode "DFP-1:nvidia-auto-select+0+0"
(II) NVIDIA(7): NVIDIA 3D Acceleration Architecture Initialized
(==) NVIDIA(7): Disabling shared memory pixmaps
(II) NVIDIA(7): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(7): Backing store disabled
(==) NVIDIA(7): Silken mouse enabled
(II) NVIDIA(7): DPMS enabled
(==) RandR enabled
(II) NVIDIA(8): Initialized GPU GART.
(II) NVIDIA(8): Setting mode "DFP-1:nvidia-auto-select+0+0"
(II) NVIDIA(8): NVIDIA 3D Acceleration Architecture Initialized
(==) NVIDIA(8): Disabling shared memory pixmaps
(II) NVIDIA(8): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(8): Backing store disabled
(==) NVIDIA(8): Silken mouse enabled
(II) NVIDIA(8): DPMS enabled
(==) RandR enabled
(II) NVIDIA(9): Initialized GPU GART.
(II) NVIDIA(9): Setting mode "DFP-1:nvidia-auto-select+0+0"
(II) NVIDIA(9): NVIDIA 3D Acceleration Architecture Initialized
(==) NVIDIA(9): Disabling shared memory pixmaps
(II) NVIDIA(9): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(9): Backing store disabled
(==) NVIDIA(9): Silken mouse enabled
(II) NVIDIA(9): DPMS enabled
(==) RandR enabled
(II) NVIDIA(10): Initialized GPU GART.
(II) NVIDIA(10): Setting mode "DFP-1:nvidia-auto-select+0+0"
(II) NVIDIA(10): NVIDIA 3D Acceleration Architecture Initialized
(==) NVIDIA(10): Disabling shared memory pixmaps
(II) NVIDIA(10): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(10): Backing store disabled
(==) NVIDIA(10): Silken mouse enabled
(II) NVIDIA(10): DPMS enabled
(==) RandR enabled
(II) NVIDIA(11): Initialized GPU GART.
(II) NVIDIA(11): Setting mode "DFP-1:nvidia-auto-select+0+0"
(II) NVIDIA(11): NVIDIA 3D Acceleration Architecture Initialized
(==) NVIDIA(11): Disabling shared memory pixmaps
(II) NVIDIA(11): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(11): Backing store disabled
(==) NVIDIA(11): Silken mouse enabled
(II) NVIDIA(11): DPMS enabled
(==) RandR enabled
(II) Entity 0 shares no resources
(II) Entity 1 shares no resources
(II) Entity 2 shares no resources
(II) Entity 3 shares no resources
(II) Entity 4 shares no resources
(II) Entity 5 shares no resources
(II) Entity 6 shares no resources
(II) Entity 7 shares no resources
(II) Entity 8 shares no resources
(II) Entity 9 shares no resources
(II) Entity 10 shares no resources
(II) Entity 11 shares no resources
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing extension GLX
(II) Screen 0 shares mem & io resources
(II) Screen 1 shares mem & io resources
(II) Screen 2 shares mem & io resources
(II) Screen 3 shares mem & io resources
(II) Screen 4 shares mem & io resources
(II) Screen 5 shares mem & io resources
(II) Screen 6 shares mem & io resources
(II) Screen 7 shares mem & io resources
(II) Screen 8 shares mem & io resources
(II) Screen 9 shares mem & io resources
(II) Screen 10 shares mem & io resources
(II) Screen 11 shares mem & io resources
(II) Screen 0 shares mem & io resources
(II) Screen 1 shares mem & io resources
(II) Screen 2 shares mem & io resources
(II) Screen 3 shares mem & io resources
(II) Screen 4 shares mem & io resources
(II) Screen 5 shares mem & io resources
(II) Screen 6 shares mem & io resources
(II) Screen 7 shares mem & io resources
(II) Screen 8 shares mem & io resources
(II) Screen 9 shares mem & io resources
(II) Screen 10 shares mem & io resources
(II) Screen 11 shares mem & io resources
(II) Screen 0 shares mem & io resources
(II) Screen 1 shares mem & io resources
(II) Screen 2 shares mem & io resources
(II) Screen 3 shares mem & io resources
(II) Screen 4 shares mem & io resources
(II) Screen 5 shares mem & io resources
(II) Screen 6 shares mem & io resources
(II) Screen 7 shares mem & io resources
(II) Screen 8 shares mem & io resources
(II) Screen 9 shares mem & io resources
(II) Screen 10 shares mem & io resources
(II) Screen 11 shares mem & io resources
(II) Screen 0 shares mem & io resources
(II) Screen 1 shares mem & io resources
(II) Screen 2 shares mem & io resources
(II) Screen 3 shares mem & io resources
(II) Screen 4 shares mem & io resources
(II) Screen 5 shares mem & io resources
(II) Screen 6 shares mem & io resources
(II) Screen 7 shares mem & io resources
(II) Screen 8 shares mem & io resources
(II) Screen 9 shares mem & io resources
(II) Screen 10 shares mem & io resources
(II) Screen 11 shares mem & io resources
(II) Screen 0 shares mem & io resources
(II) Screen 1 shares mem & io resources
(II) Screen 2 shares mem & io resources
(II) Screen 3 shares mem & io resources
(II) Screen 4 shares mem & io resources
(II) Screen 5 shares mem & io resources
(II) Screen 6 shares mem & io resources
(II) Screen 7 shares mem & io resources
(II) Screen 8 shares mem & io resources
(II) Screen 9 shares mem & io resources
(II) Screen 10 shares mem & io resources
(II) Screen 11 shares mem & io resources
(II) Screen 0 shares mem & io resources
(II) Screen 1 shares mem & io resources
(II) Screen 2 shares mem & io resources
(II) Screen 3 shares mem & io resources
(II) Screen 4 shares mem & io resources
(II) Screen 5 shares mem & io resources
(II) Screen 6 shares mem & io resources
(II) Screen 7 shares mem & io resources
(II) Screen 8 shares mem & io resources
(II) Screen 9 shares mem & io resources
(II) Screen 10 shares mem & io resources
(II) Screen 11 shares mem & io resources
(II) Screen 0 shares mem & io resources
(II) Screen 1 shares mem & io resources
(II) Screen 2 shares mem & io resources
(II) Screen 3 shares mem & io resources
(II) Screen 4 shares mem & io resources
(II) Screen 5 shares mem & io resources
(II) Screen 6 shares mem & io resources
(II) Screen 7 shares mem & io resources
(II) Screen 8 shares mem & io resources
(II) Screen 9 shares mem & io resources
(II) Screen 10 shares mem & io resources
(II) Screen 11 shares mem & io resources
(II) Screen 0 shares mem & io resources
(II) Screen 1 shares mem & io resources
(II) Screen 2 shares mem & io resources
(II) Screen 3 shares mem & io resources
(II) Screen 4 shares mem & io resources
(II) Screen 5 shares mem & io resources
(II) Screen 6 shares mem & io resources
(II) Screen 7 shares mem & io resources
(II) Screen 8 shares mem & io resources
(II) Screen 9 shares mem & io resources
(II) Screen 10 shares mem & io resources
(II) Screen 11 shares mem & io resources
(II) Screen 0 shares mem & io resources
(II) Screen 1 shares mem & io resources
(II) Screen 2 shares mem & io resources
(II) Screen 3 shares mem & io resources
(II) Screen 4 shares mem & io resources
(II) Screen 5 shares mem & io resources
(II) Screen 6 shares mem & io resources
(II) Screen 7 shares mem & io resources
(II) Screen 8 shares mem & io resources
(II) Screen 9 shares mem & io resources
(II) Screen 10 shares mem & io resources
(II) Screen 11 shares mem & io resources
(II) Screen 0 shares mem & io resources
(II) Screen 1 shares mem & io resources
(II) Screen 2 shares mem & io resources
(II) Screen 3 shares mem & io resources
(II) Screen 4 shares mem & io resources
(II) Screen 5 shares mem & io resources
(II) Screen 6 shares mem & io resources
(II) Screen 7 shares mem & io resources
(II) Screen 8 shares mem & io resources
(II) Screen 9 shares mem & io resources
(II) Screen 10 shares mem & io resources
(II) Screen 11 shares mem & io resources
(II) Screen 0 shares mem & io resources
(II) Screen 1 shares mem & io resources
(II) Screen 2 shares mem & io resources
(II) Screen 3 shares mem & io resources
(II) Screen 4 shares mem & io resources
(II) Screen 5 shares mem & io resources
(II) Screen 6 shares mem & io resources
(II) Screen 7 shares mem & io resources
(II) Screen 8 shares mem & io resources
(II) Screen 9 shares mem & io resources
(II) Screen 10 shares mem & io resources
(II) Screen 11 shares mem & io resources
(II) Screen 0 shares mem & io resources
(II) Screen 1 shares mem & io resources
(II) Screen 2 shares mem & io resources
(II) Screen 3 shares mem & io resources
(II) Screen 4 shares mem & io resources
(II) Screen 5 shares mem & io resources
(II) Screen 6 shares mem & io resources
(II) Screen 7 shares mem & io resources
(II) Screen 8 shares mem & io resources
(II) Screen 9 shares mem & io resources
(II) Screen 10 shares mem & io resources
(II) Screen 11 shares mem & io resources
 ddxSigGiveUp: Closing log

```here my xorg.conf with all 12 monitors defined:
```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@crested)  Sun Feb  1 20:25:37 UTC 2009

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 3600
    Screen      1  "Screen1" Above "Screen0"
    Screen      2  "Screen2" Above "Screen1"
    Screen      3  "Screen3" Above "Screen2"
    Screen      4  "Screen4" RightOf "Screen0"
    Screen      5  "Screen5" RightOf "Screen1"
    Screen      6  "Screen6" RightOf "Screen2"
    Screen      7  "Screen7" RightOf "Screen3"
    Screen      8  "Screen8" RightOf "Screen4"
    Screen      9  "Screen9" RightOf "Screen5"
    Screen      10  "Screen10" RightOf "Screen6"
    Screen      11  "Screen11" RightOf "Screen7"    
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "1"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
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

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 60.0
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 60.0
EndSection

Section "Monitor"
    Identifier     "Monitor2"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 60.0
EndSection

Section "Monitor"
    Identifier     "Monitor3"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 60.0
EndSection

Section "Monitor"
    Identifier     "Monitor4"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 60.0
EndSection

Section "Monitor"
    Identifier     "Monitor5"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 60.0
EndSection

Section "Monitor"
    Identifier     "Monitor6"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 60.0
EndSection

Section "Monitor"
    Identifier     "Monitor7"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 60.0
EndSection

Section "Monitor"
    Identifier     "Monitor8"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 60.0
EndSection

Section "Monitor"
    Identifier     "Monitor9"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 60.0
EndSection

Section "Monitor"
    Identifier     "Monitor10"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 60.0
EndSection

Section "Monitor"
    Identifier     "Monitor11"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 60.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro NVS 450"
    BusID          "PCI:7:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro NVS 450"
    BusID          "PCI:7:0:0"
    Screen          1
EndSection

Section "Device"
    Identifier     "Device2"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro NVS 450"
    BusID          "PCI:6:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device3"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro NVS 450"
    BusID          "PCI:6:0:0"
    Screen          1
EndSection

Section "Device"
    Identifier     "Device4"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro NVS 450"
    BusID          "PCI:11:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device5"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro NVS 450"
    BusID          "PCI:11:0:0"
    Screen          1
EndSection

Section "Device"
    Identifier     "Device6"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro NVS 450"
    BusID          "PCI:10:0:0"
    Screen          0
EndSection
Section "Device"

    Identifier     "Device7"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro NVS 450"
    BusID          "PCI:10:0:0"
    Screen          1
EndSection

Section "Device"
    Identifier     "Device8"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro NVS 450"
    BusID          "PCI:15:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device9"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro NVS 450"
    BusID          "PCI:15:0:0"
    Screen          1
EndSection

Section "Device"
    Identifier     "Device10"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro NVS 450"
    BusID          "PCI:14:0:0"
    Screen          0
EndSection
Section "Device"

    Identifier     "Device11"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro NVS 450"
    BusID          "PCI:14:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-1: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen2"
    Device         "Device2"
    Monitor        "Monitor2"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen3"
    Device         "Device3"
    Monitor        "Monitor3"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-1: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen4"
    Device         "Device4"
    Monitor        "Monitor4"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-1: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen5"
    Device         "Device5"
    Monitor        "Monitor5"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-1: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen6"
    Device         "Device6"
    Monitor        "Monitor6"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-1: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen7"
    Device         "Device7"
    Monitor        "Monitor7"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-1: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen8"
    Device         "Device8"
    Monitor        "Monitor8"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-1: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen9"
    Device         "Device9"
    Monitor        "Monitor9"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-1: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen10"
    Device         "Device10"
    Monitor        "Monitor10"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-1: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen11"
    Device         "Device11"
    Monitor        "Monitor11"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-1: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```I've tested also absolute positioning without success.

Therefore my question: is there a limitation of devices, screens and/or monitors in the xorg.conf file?
Did I something else wrong?


Thanks in advance for your answer!

regards, mike

---

