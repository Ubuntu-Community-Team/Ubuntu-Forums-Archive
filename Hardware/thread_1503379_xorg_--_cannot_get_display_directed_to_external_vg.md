---
title: "xorg -- cannot get display directed to external vga LCD monitor"
date: 2010-06-06
forum: Hardware
---

### Post by lxgeek on 2010-06-06
I've spent all day on this so now I'm writing. 

I have a fresh new Lenovo T410s
2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux

I also have an external monitor which I've used with a Lenovo T60 running opensuse 10.3. There's a docking station, too, but I don't think that matters. On the T60 I start the laptop in the docking station with the lid down and the X11 display is directed to the VGA output, thus driving the ext monitor.

I cannot get the same behavior on my T410s running Ubuntu 9.10, even with the same xorg.conf file. I cannot get xrandr to detect the vga monitor and xrandr-style commands like

$xrandr --output VGA --auto

don't work.

([http://promberger.info/linux/2007/12/20/external-monitor-on-thinkpad-x41-running-xubuntu-gutsy/](http://promberger.info/linux/2007/12/20/external-monitor-on-thinkpad-x41-running-xubuntu-gutsy/))

When I do startup the T410s in the docking station with the lid down Ubuntu starts up as if the lid were open. That is: the display is not directed to the vga, and when I open the lid I see a ubuntu splash page. 

I'm inclined to look at solutions such as ([https://wiki.ubuntu.com/HowtoSetupExternalMonitorForIntel915](https://wiki.ubuntu.com/HowtoSetupExternalMonitorForIntel915)) but the intel driver is not working on this computer (T410s). 

I've looked here: ([https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen](https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen)) without luck. 

I've worked closely on ([http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2)), no joy. 

My xrandr -q gives:
Screen 0: minimum 800 x 600, current 1280 x 800, maximum 1280 x 800
default connected 1280x800+0+0 0mm x 0mm
   1280x800        0.0*
   1024x768       61.0
   960x600         0.0
   800x600        61.0

(evidently no vga)

I've tried
$sudo X --configure
with the gdm down but I cannot get it to detect the vga monitor. 

(The monitor is fine, I'm using it now on the T60 to write this). 

Below is my xorg.conf and the associated Xorg.0.log file. Any help is greatly appreciated.
-lxgeek[B]

xorg.conf:[/B]
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"
        Option          "ModeDebug" "true"
EndSection

Section "Monitor"
  Identifier   "Monitor[0]"
  VendorName   "DELL"
  ModelName    "2005FPW (DIGITAL)"
  DisplaySize  431 269
  ModeLine     "1680x1050" 146.2 1680 1784 1968 2256 1050 1051 1054 1087 -hsync -vsync
  HorizSync    30.0-83.0
  VertRefresh  56.0-75.0
  Option       "dpms"
  Option       "CalcAlgorithm" "XServerPool"
  UseModes     "Modes[0]"
EndSection

Section "Modes"
  Identifier   "Modes[0]"
EndSection

Section "Screen"
  DefaultDepth 24
  SubSection "Display"
    Depth      15
    Modes      "1400x1050" "1280x1024" "1024x768" "800x600"
  EndSubSection
  SubSection "Display"
    Depth      16
    Modes      "1400x1050" "1280x1024" "1024x768" "800x600"
  EndSubSection
  SubSection "Display"
    Depth      24
    Modes      "1680x1050" "1152x864" "1024x768" "800x600" "720x400" "640x480"
  EndSubSection
  SubSection "Display"
    Depth      8
    Modes      "1400x1050" "1280x1024" "1024x768" "800x600"
  EndSubSection
  Device       "Configured Video Device"
  Identifier   "Screen[0]"
  Monitor      "Monitor[0]"
EndSection

Section "DRI"
    Group "video"
    Mode 0660
EndSection

**Xorg.0.log**
X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server x86_64 Ubuntu
Current Operating System: Linux DamaskAnalyticsLaptop-002 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=c126e466-8b14-4aac-9ff5-074b1aeb9ca2 ro quiet splash
Build Date: 26 October 2009  05:19:56PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@)
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Jun  6 18:24:26 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Screen[0]" (0)
(**) |   |-->Monitor "Monitor[0]"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
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
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
        If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0xb40
(II) Module ABI versions:
        X.Org ANSI C Emulation: 0.4
        X.Org Video Driver: 5.0
        X.Org XInput driver : 4.0
        X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0:0:2:0) 8086:0046:17aa:21c1 Intel Corporation Arrandale Integrated Graphics Controller rev 2, Mem @ 0xf2000000/4194304, 0xd0000000/268435456, I/O @ 0x00001800/8
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]
        [5] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [6] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [7] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [8] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]
        [9] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [10] -1 0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [11] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [12] -1 0       0xffffffff - 0xffffffff (0x1) MX[B]
        [13] -1 0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [14] -1 0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [15] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [16] -1 0       0xffffffff - 0xffffffff (0x1) MX[B]
        [17] -1 0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [18] -1 0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [19] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [20] -1 0       0xffffffff - 0xffffffff (0x1) MX[B]
        [21] -1 0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [22] -1 0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [23] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [24] -1 0       0xffffffff - 0xffffffff (0x1) MX[B]
        [25] -1 0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [26] -1 0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [27] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [28] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [29] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]
        [30] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [31] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]
        [32] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [33] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]
        [34] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [35] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]
        [36] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [37] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]
        [38] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [39] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]
        [40] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [41] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
        compiled for 1.6.4, module version = 1.0.0
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
        compiled for 1.6.4, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
        compiled for 1.6.4, module version = 1.0.0
        ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
        compiled for 1.6.4, module version = 1.13.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
        compiled for 1.6.4, module version = 1.0.0
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
        compiled for 1.6.4, module version = 1.1.0
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
        compiled for 1.6.3, module version = 2.2.1
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 5.0
(II) VESA: driver for VESA chipsets: vesa
(II) Primary Device is: PCI 00@00:02:0
(II) resource ranges after probing:
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]
        [5] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [6] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [7] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [8] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]
        [9] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [10] -1 0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [11] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [12] -1 0       0xffffffff - 0xffffffff (0x1) MX[B]
        [13] -1 0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [14] -1 0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [15] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [16] -1 0       0xffffffff - 0xffffffff (0x1) MX[B]
        [17] -1 0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [18] -1 0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [19] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [20] -1 0       0xffffffff - 0xffffffff (0x1) MX[B]
        [21] -1 0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [22] -1 0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [23] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [24] -1 0       0xffffffff - 0xffffffff (0x1) MX[B]
        [25] -1 0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [26] -1 0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [27] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [28] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [29] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]
        [30] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [31] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]
        [32] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [33] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]
        [34] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [35] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]
        [36] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [37] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]
        [38] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [39] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]
        [40] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [41] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
        compiled for 1.6.4, module version = 1.1.0
        ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
        compiled for 1.6.4, module version = 1.0.0
        ABI class: X.Org Video Driver, version 5.0
(II) VESA(0): initializing int10
(II) VESA(0): Bad V_BIOS checksum
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 32704 kB
(II) VESA(0): VESA VBE OEM: Intel(R)Ironlake Mobile Graphics Chipset Accelerated VGA BIOS
(II) VESA(0): VESA VBE OEM Software Rev: 1.0
(II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
(II) VESA(0): VESA VBE OEM Product: Intel(R)Ironlake Mobile Graphics Controller
(II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(**) VESA(0): Depth 24, (--) framebuffer bpp 32
(==) VESA(0): RGB weight 888
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) VESA(0): VESA VBE DDC supported
(II) VESA(0): VESA VBE DDC Level 2
(II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
(II) VESA(0): VESA VBE DDC read successfully
(II) VESA(0): Manufacturer: LEN  Model: 4036  Serial#: 0
(II) VESA(0): Year: 2008  Week: 0
(II) VESA(0): EDID Version: 1.3
(II) VESA(0): Digital Display Input
(II) VESA(0): Max Image Size [cm]: horiz.: 30  vert.: 19
(II) VESA(0): Gamma: 2.20
(II) VESA(0): DPMS capabilities: StandBy Suspend Off
(II) VESA(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4
(II) VESA(0): First detailed timing is preferred mode
(II) VESA(0): redX: 0.577 redY: 0.338   greenX: 0.310 greenY: 0.563
(II) VESA(0): blueX: 0.158 blueY: 0.157   whiteX: 0.313 whiteY: 0.329
(II) VESA(0): Manufacturer's mask: 0
(II) VESA(0): Supported detailed timing:
(II) VESA(0): clock: 106.9 MHz   Image Size:  303 x 190 mm
(II) VESA(0): h_active: 1440  h_sync: 1488  h_sync_end 1520 h_blank_end 1924 h_border: 0
(II) VESA(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 926 v_border: 0
(II) VESA(0): Supported detailed timing:
(II) VESA(0): clock: 89.3 MHz   Image Size:  303 x 190 mm
(II) VESA(0): h_active: 1440  h_sync: 1488  h_sync_end 1520 h_blank_end 1740 h_border: 0
(II) VESA(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 1026 v_border: 0
(WW) VESA(0): Unknown vendor-specific block f
(II) VESA(0):  LTN141BT08001
(II) VESA(0): EDID (in hex):
(II) VESA(0):   00ffffffffffff0030ae364000000000
(II) VESA(0):   00120103801e1378eae59593564f9028
(II) VESA(0):   28505400000001010101010101010101
(II) VESA(0):   010101010101c129a0e451841a303020
(II) VESA(0):   36002fbe10000019de22a02c51847e30
(II) VESA(0):   302036002fbe100000190000000f0095
(II) VESA(0):   0a32950a281e09004ca34254000000fe
(II) VESA(0):   004c544e3134314254303830303100cb
(II) VESA(0): EDID vendor "LEN", prod id 16438
(II) VESA(0): Printing DDC gathered Modelines:
(II) VESA(0): Modeline "1440x900"x0.0  106.89  1440 1488 1520 1924  900 903 909 926 -hsync -vsync (55.6 kHz)
(II) VESA(0): Modeline "1440x900"x0.0   89.26  1440 1488 1520 1740  900 903 909 1026 -hsync -vsync (51.3 kHz)
(II) VESA(0): Searching for matching VESA mode(s):
Mode: 160 (768x480)
...
(II) VESA(0): Total Memory: 511 64KB banks (32704kB)
(II) VESA(0): Monitor[0]: Using hsync range of 30.00-83.00 kHz
(II) VESA(0): Monitor[0]: Using vrefresh range of 56.00-75.00 Hz
(II) VESA(0): Not using mode "1680x1050" (no mode of this name)
(II) VESA(0): Not using mode "1152x864" (no mode of this name)
(II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
(II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
(II) VESA(0): Not using mode "720x400" (no mode of this name)
(II) VESA(0): Not using built-in mode "640x480" (no mode of this name)
(II) VESA(0): Not using built-in mode "1280x800" (no mode of this name)
(II) VESA(0): Not using built-in mode "960x600" (no mode of this name)
(II) VESA(0): Not using built-in mode "768x480" (no mode of this name)
(WW) VESA(0): No valid modes left. Trying less strict filter...
(II) VESA(0): Monitor[0]: Using hsync range of 30.00-83.00 kHz
(II) VESA(0): Monitor[0]: Using vrefresh range of 56.00-75.00 Hz
(II) VESA(0): Not using mode "1680x1050" (no mode of this name)
(II) VESA(0): Not using mode "1152x864" (no mode of this name)
(II) VESA(0): Not using mode "720x400" (no mode of this name)
(II) VESA(0): Not using built-in mode "1280x800" (width too large for virtual size)
(--) VESA(0): Virtual size is 1024x768 (pitch 1024)
(**) VESA(0): *Built-in mode "1024x768"
(**) VESA(0): *Built-in mode "800x600"
(**) VESA(0): *Built-in mode "640x480"
(**) VESA(0):  Built-in mode "960x600"
(**) VESA(0):  Built-in mode "768x480"
(**) VESA(0): Display dimensions: (431, 269) mm
(WW) VESA(0): Probed monitor is 300x190 mm, using Displaysize 431x269 mm
(**) VESA(0): DPI set to (60, 72)
(II) VESA(0): Attempting to use 75Hz refresh for mode "1024x768" (118)
(II) VESA(0): Attempting to use 72Hz refresh for mode "800x600" (115)
(II) VESA(0): Attempting to use 73Hz refresh for mode "640x480" (112)
(**) VESA(0): Using "Shadow Framebuffer"
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules//libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
        compiled for 1.6.4, module version = 1.1.0
        ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
        compiled for 1.6.4, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.4
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]
        [5] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [6] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [7] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [8] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]
        [9] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [10] -1 0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [11] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [12] -1 0       0xffffffff - 0xffffffff (0x1) MX[B]
        [13] -1 0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [14] -1 0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [15] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [16] -1 0       0xffffffff - 0xffffffff (0x1) MX[B]
        [17] -1 0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [18] -1 0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [19] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [20] -1 0       0xffffffff - 0xffffffff (0x1) MX[B]
        [21] -1 0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [22] -1 0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [23] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [24] -1 0       0xffffffff - 0xffffffff (0x1) MX[B]
        [25] -1 0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [26] -1 0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [27] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [28] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [29] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]
        [30] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [31] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]
        [32] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [33] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]
        [34] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [35] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]
        [36] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [37] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]
        [38] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [39] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]
        [40] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [41] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) VESA(0): initializing int10
(II) VESA(0): Bad V_BIOS checksum
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 32704 kB
(II) VESA(0): VESA VBE OEM: Intel(R)Ironlake Mobile Graphics Chipset Accelerated VGA BIOS
(II) VESA(0): VESA VBE OEM Software Rev: 1.0
(II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
(II) VESA(0): VESA VBE OEM Product: Intel(R)Ironlake Mobile Graphics Controller
(II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) VESA(0): virtual address = 0x7fb06d4e4000,
        physical address = 0xd0000000, size = 33488896
(II) VESA(0): Setting up VESA Mode 0x118 (1024x768)
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Backing store disabled
(**) Option "dpms"
(**) VESA(0): DPMS enabled
(WW) VESA(0): Option "ModeDebug" is not used
(WW) VESA(0): Option "CalcAlgorithm" is not used
(==) RandR enabled
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
(II) AIGLX: Screen 0 is not DRI2 capable
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(II) config/hal: Adding input device ThinkPad Extra Buttons
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
        compiled for 1.6.4, module version = 2.2.5
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 4.0
(**) ThinkPad Extra Buttons: always reports core events
(**) ThinkPad Extra Buttons: Device: "/dev/input/event5"
(II) ThinkPad Extra Buttons: Found keys
(II) ThinkPad Extra Buttons: Configuring as keyboard
(II) XINPUT: Adding extended input device "ThinkPad Extra Buttons" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Integrated Camera
(**) Integrated Camera: always reports core events
(**) Integrated Camera: Device: "/dev/input/event7"
(II) Integrated Camera: Found keys
(II) Integrated Camera: Configuring as keyboard
(II) XINPUT: Adding extended input device "Integrated Camera" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Sleep Button
(**) Sleep Button: always reports core events
(**) Sleep Button: Device: "/dev/input/event2"
(II) Sleep Button: Found keys
(II) Sleep Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/hal: Adding input device SynPS/2 Synaptics TouchPad
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
        compiled for 1.6.4, module version = 1.1.2
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 4.0
(II) Synaptics touchpad driver version 1.1.2
(**) Option "Device" "/dev/input/event6"
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
(II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
(II) SynPS/2 Synaptics TouchPad: buttons: left right middle
(--) SynPS/2 Synaptics TouchPad: touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
(**) SynPS/2 Synaptics TouchPad: (accel) filter chain progression: 2.00
(**) SynPS/2 Synaptics TouchPad: (accel) filter stage 0: 20.00 ms
(**) SynPS/2 Synaptics TouchPad: (accel) set acceleration profile 0
(--) SynPS/2 Synaptics TouchPad: touchpad found
(II) config/hal: Adding input device TPPS/2 IBM TrackPoint
(**) TPPS/2 IBM TrackPoint: always reports core events
(**) TPPS/2 IBM TrackPoint: Device: "/dev/input/event8"
(II) TPPS/2 IBM TrackPoint: Found 3 mouse buttons
(II) TPPS/2 IBM TrackPoint: Found x and y relative axes
(II) TPPS/2 IBM TrackPoint: Configuring as mouse
(**) TPPS/2 IBM TrackPoint: YAxisMapping: buttons 4 and 5
(**) TPPS/2 IBM TrackPoint: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "TPPS/2 IBM TrackPoint" (type: MOUSE)
(**) TPPS/2 IBM TrackPoint: (accel) keeping acceleration scheme 1
(**) TPPS/2 IBM TrackPoint: (accel) filter chain progression: 2.00
(**) TPPS/2 IBM TrackPoint: (accel) filter stage 0: 20.00 ms
(**) TPPS/2 IBM TrackPoint: (accel) set acceleration profile 0
(II) TPPS/2 IBM TrackPoint: initialized for relative axes.

---

### Post by Allochtoon on 2010-12-11
try  placing a 'layout' section in your xorg.conf

---

