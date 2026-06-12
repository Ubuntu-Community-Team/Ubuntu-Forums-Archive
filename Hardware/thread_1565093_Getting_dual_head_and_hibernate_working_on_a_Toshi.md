---
title: "Getting dual head and hibernate working on a Toshiba Portege M200 with nouveau"
date: 2010-08-31
forum: Hardware
---

### Post by anjames on 2010-08-31
[ChaoSlayer got dual-head working](http://ubuntuforums.org/showthread.php?p=9786779#post9786779), so I thought I'd give it a try.

I have a Toshiba M200 which hasn't been hibernating on the new 2.6.32-24 kernel, I suspect because of some combination of the vesafb and nouveau drivers. Reverting to the 2.6.31-22 kernel gets me hibernate back (using nvidiafb and nv drivers), but I've never gotten the VGA out to work with it. I'd try the new kernel again, but there's a bug which prevents me from removing vesafb and using nvidiafb, documented:
[http://ubuntuforums.org/showthread.php?t=1508904&page=2](http://ubuntuforums.org/showthread.php?t=1508904&page=2)

My current xorg.conf is pretty basic, with edits only for the wacom tablet:

```
$ cat /etc/X11/xorg.conf
# xorg.conf (X.Org X Window System server configuration file)

Section "Device"
	Identifier	"Configured Video Device"
#	Driver	"nv"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
#  Option        "Device"        "/dev/input/wacom" # USB ONLY?
  Option        "Device"        "/dev/ttyS0"      # SERIAL ONLY
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"           # Tablet PC ONLY
#  Option        "USB"           "on"               # USB ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
#  Option        "Device"        "/dev/input/wacom" # USB ONLY?
  Option        "Device"        "/dev/ttyS0"      # SERIAL ONLY
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"           # Tablet PC ONLY
#  Option        "USB"           "on"               # USB ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
#  Option        "Device"        "/dev/input/wacom" # USB ONLY?
  Option        "Device"        "/dev/ttyS0"      # SERIAL ONLY
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"           # Tablet PC ONLY
#  Option        "USB"           "on"               # USB ONLY
EndSection

```

Pretty limited output from xrandr compared to you:
```
$ xrandr
Screen 0: minimum 800 x 600, current 1280 x 1024, maximum 1280 x 1024
default connected 1280x1024+0+0 0mm x 0mm
   1280x1024      61.0* 
   1024x768       61.0  
   800x600        61.0

```

...probably because my [edid](http://en.wikipedia.org/wiki/Extended_display_identification_data) fails, maybe because for some reason I don't have permissions to run ddcprobe? Could this be causing me problems?
```
$ ddcprobe
mmap /dev/zero: Permission denied
VESA BIOS Extensions not detected.

$ sudo ddcprobe
vbe: VESA 3.0 detected.
oem: NVIDIA
vendor: NVIDIA Corporation
product: NV34 Board - tosh34sf Chip Rev
memory: 32768kb
mode: 640x400x256
mode: 640x480x256
mode: 800x600x16
mode: 800x600x256
mode: 1024x768x16
mode: 1024x768x256
mode: 1280x1024x16
mode: 1280x1024x256
mode: 320x200x64k
mode: 320x200x16m
mode: 640x480x64k
mode: 640x480x16m
mode: 800x600x64k
mode: 800x600x16m
mode: 1024x768x64k
mode: 1024x768x16m
mode: 1280x1024x64k
mode: 1280x1024x16m
Calling INT 0x15 (F000:FEA8)
 EAX is 0x5F15
Calling INT 0x15 (F000:FEA8)
 EAX is 0x5F15
edid: 
edidfail

```

LOTS of output from xdpyinfo! Why do I have 64 visuals when you have only 2?

```
$ xdpyinfo
name of display:    :0.0
version number:    11.0
vendor string:    The X.Org Foundation
vendor release number:    10706000
X.Org version: 1.7.6
maximum request size:  16777212 bytes
motion buffer size:  256
bitmap unit, bit order, padding:    32, LSBFirst, 32
image byte order:    LSBFirst
number of supported pixmap formats:    7
supported pixmap formats:
    depth 1, bits_per_pixel 1, scanline_pad 32
    depth 4, bits_per_pixel 8, scanline_pad 32
    depth 8, bits_per_pixel 8, scanline_pad 32
    depth 15, bits_per_pixel 16, scanline_pad 32
    depth 16, bits_per_pixel 16, scanline_pad 32
    depth 24, bits_per_pixel 32, scanline_pad 32
    depth 32, bits_per_pixel 32, scanline_pad 32
keycode range:    minimum 8, maximum 255
focus:  window 0x2200005, revert to Parent
number of extensions:    27
    BIG-REQUESTS
    Composite
    DAMAGE
    DOUBLE-BUFFER
    DPMS
    DRI2
    GLX
    Generic Event Extension
    MIT-SCREEN-SAVER
    MIT-SHM
    RANDR
    RECORD
    RENDER
    SECURITY
    SGI-GLX
    SHAPE
    SYNC
    X-Resource
    XC-MISC
    XFIXES
    XFree86-DGA
    XFree86-VidModeExtension
    XINERAMA
    XInputExtension
    XKEYBOARD
    XTEST
    XVideo
default screen number:    0
number of screens:    1

screen #0:
  dimensions:    1280x1024 pixels (339x271 millimeters)
  resolution:    96x96 dots per inch
  depths (7):    24, 1, 4, 8, 15, 16, 32
  root window id:    0x101
  depth of root window:    24 planes
  number of colormaps:    minimum 1, maximum 1
  default colormap:    0x20
  default number of colormap cells:    256
  preallocated pixels:    black 0, white 16777215
  options:    backing-store NO, save-unders NO
  largest cursor:    1280x1024
  current input event mask:    0xfac033
    KeyPressMask             KeyReleaseMask           EnterWindowMask          
    LeaveWindowMask          KeymapStateMask          ExposureMask             
    StructureNotifyMask      SubstructureNotifyMask   SubstructureRedirectMask 
    FocusChangeMask          PropertyChangeMask       ColormapChangeMask       
  number of visuals:    64
  default visual id:  0x21
  visual:
    visual id:    0x21
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0xc2
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0xc3
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0xc4
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0xc5
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0xc6
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0xc7
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0xc8
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0xc9
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0xca
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0xcb
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0xcc
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0xcd
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0xce
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0xcf
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0xd0
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0xd1
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0xd2
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0xd3
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0xd4
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0xd5
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0xd6
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0xd7
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0xd8
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0xd9
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0xda
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0xdb
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0xdc
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0xdd
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0xde
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0xdf
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0xe0
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0xe1
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0xe2
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0xe3
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0xe4
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0xe5
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0xe6
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0xe7
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0xe8
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0xe9
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0xea
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0xeb
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0xec
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0xed
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0xee
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0xef
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0xf0
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0xf1
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0xf2
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0xf3
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0xf4
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0xf5
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0xf6
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0xf7
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0xf8
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0xf9
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0xfa
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0xfb
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0xfc
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0xfd
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0xfe
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0xff
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x41
    class:    TrueColor
    depth:    32 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits

```


```
$lspci -vvnn
...
01:00.0 VGA compatible controller [0300]: nVidia Corporation NV34M [GeForce FX Go5200 32M/64M] [10de:0328] (rev a1)
        Subsystem: Toshiba America Info Systems Device [1179:0010]
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 64 (1250ns min, 250ns max)
        Interrupt: pin A routed to IRQ 10
        Region 0: Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
        Region 1: Memory at d0000000 (32-bit, prefetchable) [size=256M]
        Capabilities: <access denied>
        Kernel driver in use: nvidiafb
        Kernel modules: nvidiafb
...

```

Strangely... the xorg log shows that it loads nouveau, then loads nv, then unloads nv. Also it lists one or more modes with 1400x1050, but it throws them all away and reverts to 1280x1024, 1024x768, 800x600. 

Hmm... maybe I need to work on my xorg config.

```
$ cat /var/log/Xorg.0.log
X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux amaterasu 2.6.31-22-generic #63-Ubuntu SMP Wed Aug 18 22:54:26 UTC 2010 i686
Kernel command line: root=UUID=22578c46-436c-4302-b1cd-bba53d865367 ro vga=795 resume=/dev/hda5 
Build Date: 21 July 2010  12:47:34PM
xorg-server 2:1.7.6-2ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Aug 30 09:50:17 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
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
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x81f0e80
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:1:0:0) 10de:0328:1179:0010 nVidia Corporation NV34M [GeForce FX Go5200 32M/64M] rev 161, Mem @ 0xfd000000/16777216, 0xd0000000/268435456
(II) Open ACPI successful (/var/run/acpid.socket)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(==) Matched nouveau as autoconfigured driver 0
(==) Matched nv as autoconfigured driver 1
(==) Matched vesa as autoconfigured driver 2
(==) Matched fbdev as autoconfigured driver 3
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "nouveau"
(II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
(II) Module nouveau: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.0.15
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "nv"
(II) Loading /usr/lib/xorg/modules/drivers/nv_drv.so
(II) Module nv: vendor="X.Org Foundation"
	compiled for 1.7.3.901, module version = 2.1.15
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.4.1
	ABI class: X.Org Video Driver, version 6.0
(II) NOUVEAU driver Date:   Wed Feb 10 18:43:39 2010 +0100
(II) NOUVEAU driver for NVIDIA chipset families :
	RIVA TNT    (NV04)
	RIVA TNT2   (NV05)
	GeForce 256 (NV10)
	GeForce 2   (NV11, NV15)
	GeForce 4MX (NV17, NV18)
	GeForce 3   (NV20)
	GeForce 4Ti (NV25, NV28)
	GeForce FX  (NV3x)
	GeForce 6   (NV4x)
	GeForce 7   (G7x)
	GeForce 8   (G8x)
(II) NOUVEAU driver Date:   Wed Feb 10 18:43:39 2010 +0100
(II) NOUVEAU driver for NVIDIA chipset families :
	RIVA TNT    (NV04)
	RIVA TNT2   (NV05)
	GeForce 256 (NV10)
	GeForce 2   (NV11, NV15)
	GeForce 4MX (NV17, NV18)
	GeForce 3   (NV20)
	GeForce 4Ti (NV25, NV28)
	GeForce FX  (NV3x)
	GeForce 6   (NV4x)
	GeForce 7   (G7x)
	GeForce 8   (G8x)
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 01@00:00:0
drmOpenDevice: node name is /dev/dri/card0
[drm] failed to load kernel module "nouveau"
(EE) [drm] failed to open device
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.0.2
	ABI class: X.Org Video Driver, version 6.0
(WW) VGA arbiter: cannot open kernel arbiter, no multi-card support
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org Video Driver, version 6.0
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Video Driver, version 6.0
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 32768 kB
(II) VESA(0): VESA VBE OEM: NVIDIA
(II) VESA(0): VESA VBE OEM Software Rev: 4.52
(II) VESA(0): VESA VBE OEM Vendor: NVIDIA Corporation
(II) VESA(0): VESA VBE OEM Product: NV34 Board - tosh34sf
(II) VESA(0): VESA VBE OEM Product Rev: Chip Rev   
(II) VESA(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(==) VESA(0): Depth 24, (--) framebuffer bpp 32
(==) VESA(0): RGB weight 888
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) VESA(0): VESA VBE DDC supported
(II) VESA(0): VESA VBE DDC Level none
(II) VESA(0): VESA VBE DDC transfer in appr. 0 sec.
(II) VESA(0): VESA VBE DDC read failed
(II) VESA(0): VESA VBE PanelID read successfully
(II) VESA(0): PanelID returned panel resolution 259x4608
(II) VESA(0): Searching for matching VESA mode(s):
Mode: 100 (640x400)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009caf
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 14
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 14
	LinNumberOfImagePages: 14
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 101 (640x480)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009caf
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 10
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 10
	LinNumberOfImagePages: 10
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 102 (800x600)
	ModeAttributes: 0x31f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009caf
	BytesPerScanline: 100
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 4
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 3
	BankSize: 0
	NumberOfImages: 14
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 100
	BnkNumberOfImagePages: 14
	LinNumberOfImagePages: 14
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 108500000
Mode: 103 (800x600)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009caf
	BytesPerScanline: 800
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 6
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 800
	BnkNumberOfImagePages: 6
	LinNumberOfImagePages: 6
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 104 (1024x768)
	ModeAttributes: 0x31f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009caf
	BytesPerScanline: 128
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 4
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 3
	BankSize: 0
	NumberOfImages: 6
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 128
	BnkNumberOfImagePages: 6
	LinNumberOfImagePages: 6
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 108500000
Mode: 105 (1024x768)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009caf
	BytesPerScanline: 1024
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 3
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 1024
	BnkNumberOfImagePages: 3
	LinNumberOfImagePages: 3
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 106 (1280x1024)
	ModeAttributes: 0x31f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009caf
	BytesPerScanline: 160
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 4
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 3
	BankSize: 0
	NumberOfImages: 3
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 160
	BnkNumberOfImagePages: 3
	LinNumberOfImagePages: 3
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 108500000
Mode: 107 (1280x1024)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009caf
	BytesPerScanline: 1280
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 10e (320x200)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009caf
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 30
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 30
	LinNumberOfImagePages: 30
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 10f (320x200)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009caf
	BytesPerScanline: 1280
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 14
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 14
	LinNumberOfImagePages: 14
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 111 (640x480)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009caf
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 4
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 4
	LinNumberOfImagePages: 4
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 112 (640x480)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009caf
	BytesPerScanline: 2560
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 114 (800x600)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009caf
	BytesPerScanline: 1600
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 2
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 1600
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 115 (800x600)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009caf
	BytesPerScanline: 3200
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 3200
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 117 (1024x768)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009caf
	BytesPerScanline: 2048
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 2048
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 118 (1024x768)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009caf
	BytesPerScanline: 4096
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 4096
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 11a (1280x1024)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009caf
	BytesPerScanline: 2560
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 11b (1280x1024)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009caf
	BytesPerScanline: 5120
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 5120
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 147 (1400x1050)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009caf
	BytesPerScanline: 1400
	XResolution: 1400
	YResolution: 1050
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 1400
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 148 (1400x1050)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009caf
	BytesPerScanline: 2800
	XResolution: 1400
	YResolution: 1050
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 2800
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 160 (1280x800)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009caf
	BytesPerScanline: 1280
	XResolution: 1280
	YResolution: 800
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 2
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000

(II) VESA(0): Total Memory: 512 64KB banks (32768kB)
(II) VESA(0): Configured Monitor: Using hsync range of 31.50-284.25 kHz
(II) VESA(0): Configured Monitor: Using vrefresh range of 56.00-59.98 Hz
(WW) VESA(0): Unable to estimate virtual size
(II) VESA(0): Not using built-in mode "1280x1024" (no mode of this name)
(II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
(II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
(II) VESA(0): Not using built-in mode "640x480" (no mode of this name)
(II) VESA(0): Not using built-in mode "320x200" (no mode of this name)
(WW) VESA(0): No valid modes left. Trying less strict filter...
(II) VESA(0): Configured Monitor: Using hsync range of 31.50-284.25 kHz
(II) VESA(0): Configured Monitor: Using vrefresh range of 56.00-59.98 Hz
(WW) VESA(0): Unable to estimate virtual size
(II) VESA(0): Not using built-in mode "640x480" (hsync out of range)
(II) VESA(0): Not using built-in mode "320x200" (illegal horizontal timings)
(--) VESA(0): Virtual size is 1280x1024 (pitch 1280)
(**) VESA(0): *Built-in mode "1280x1024"
(**) VESA(0): *Built-in mode "1024x768"
(**) VESA(0): *Built-in mode "800x600"
(==) VESA(0): DPI set to (96, 96)
(II) VESA(0): Attempting to use 60Hz refresh for mode "1280x1024" (11b)
(II) VESA(0): Attempting to use 60Hz refresh for mode "1024x768" (118)
(II) VESA(0): Attempting to use 60Hz refresh for mode "800x600" (115)
(**) VESA(0): Using "Shadow Framebuffer"
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules/libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) UnloadModule: "nv"
(II) Unloading /usr/lib/xorg/modules/drivers/nv_drv.so
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux/libfbdevhw.so
(==) Depth 24 pixmap format is 32 bpp
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 32768 kB
(II) VESA(0): VESA VBE OEM: NVIDIA
(II) VESA(0): VESA VBE OEM Software Rev: 4.52
(II) VESA(0): VESA VBE OEM Vendor: NVIDIA Corporation
(II) VESA(0): VESA VBE OEM Product: NV34 Board - tosh34sf
(II) VESA(0): VESA VBE OEM Product Rev: Chip Rev   
(II) VESA(0): virtual address = 0xb56eb000,
	physical address = 0xd0000000, size = 33554432
(II) VESA(0): Setting up VESA Mode 0x11B (1280x1024)
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Backing store disabled
(==) VESA(0): DPMS enabled
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
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.3.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_variant" "dvorak"
(**) Option "xkb_options" "lv3:ralt_switch,grp:alts_toggle"
(II) XKB: reuse xkmfile /var/lib/xkb/server-F41CC3D3342BEB7134BAC87BB203F36646C3D80C.xkm
(II) config/udev: Adding input device Video Bus (/dev/input/event5)
(**) Video Bus: Applying InputClass "evdev keyboard catchall"
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event5"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_variant" "dvorak"
(**) Option "xkb_options" "lv3:ralt_switch,grp:alts_toggle"
(II) config/udev: Adding input device Power Button (/dev/input/event1)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_variant" "dvorak"
(**) Option "xkb_options" "lv3:ralt_switch,grp:alts_toggle"
(II) config/udev: Adding input device Lid Switch (/dev/input/event2)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_variant" "dvorak"
(**) Option "xkb_options" "lv3:ralt_switch,grp:alts_toggle"
(II) config/udev: Adding input device PS/2 Mouse (/dev/input/event7)
(**) PS/2 Mouse: Applying InputClass "evdev pointer catchall"
(**) PS/2 Mouse: always reports core events
(**) PS/2 Mouse: Device: "/dev/input/event7"
(II) PS/2 Mouse: Found 3 mouse buttons
(II) PS/2 Mouse: Found relative axes
(II) PS/2 Mouse: Found x and y relative axes
(II) PS/2 Mouse: Configuring as mouse
(**) PS/2 Mouse: YAxisMapping: buttons 4 and 5
(**) PS/2 Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "PS/2 Mouse" (type: MOUSE)
(II) PS/2 Mouse: initialized for relative axes.
(II) config/udev: Adding input device PS/2 Mouse (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/event8)
(**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "evdev pointer catchall"
(**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "evdev touchpad catchall"
(**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "touchpad catchall"
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(II) Synaptics touchpad driver version 1.2.2
(**) Option "Device" "/dev/input/event8"
(II) AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023
(II) AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767
(II) AlpsPS/2 ALPS GlidePoint: pressure range 0 - 127
(II) AlpsPS/2 ALPS GlidePoint: finger width range 0 - 0
(II) AlpsPS/2 ALPS GlidePoint: buttons: left right middle
(--) AlpsPS/2 ALPS GlidePoint: touchpad found
(**) AlpsPS/2 ALPS GlidePoint: always reports core events
(II) XINPUT: Adding extended input device "AlpsPS/2 ALPS GlidePoint" (type: TOUCHPAD)
(**) AlpsPS/2 ALPS GlidePoint: (accel) keeping acceleration scheme 1
(**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration profile 0
(**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration factor: 2.000
(**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration threshold: 4
(--) AlpsPS/2 ALPS GlidePoint: touchpad found
(II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/mouse2)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device PC Speaker (/dev/input/event6)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Serial Wacom Tablet (/dev/ttyS0)
(**) Serial Wacom Tablet: Applying InputClass "Wacom serial class"
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.10.5
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(**) Option "Device" "/dev/ttyS0"
(II) Serial Wacom Tablet: type not specified, assuming 'stylus'.
(II) Serial Wacom Tablet: other types will be automatically added.
(**) Serial Wacom Tablet: always reports core events
(II) Serial Wacom Tablet: hotplugging dependent devices.
(**) Option "Device" "/dev/ttyS0"
(**) Serial Wacom Tablet eraser: always reports core events
(II) XINPUT: Adding extended input device "Serial Wacom Tablet eraser" (type: ERASER)
(**) Option "StopBits" "1"
(**) Option "DataBits" "8"
(**) Option "Parity" "None"
(**) Option "Vmin" "1"
(**) Option "Vtime" "10"
(**) Option "FlowControl" "Xoff"
(WW) Serial Wacom Tablet eraser: Waited too long for answer (failed after 3 tries).
(WW) Serial Wacom Tablet eraser: Waited too long for answer (failed after 3 tries).
(II) Serial Wacom Tablet eraser: serial tablet id 0x90.
(--) Serial Wacom Tablet eraser: using pressure threshold of 7 for button 1
(--) Serial Wacom Tablet eraser: Wacom General ISDV4 tablet speed=38400 maxX=24570 maxY=18428 maxZ=127 resX=2540 resY=2540  tilt=disabled
(--) Serial Wacom Tablet eraser: top X=0 top Y=0 bottom X=24570 bottom Y=18428 resol X=2540 resol Y=2540
(II) Serial Wacom Tablet: hotplugging completed.
(II) XINPUT: Adding extended input device "Serial Wacom Tablet" (type: STYLUS)
(--) Serial Wacom Tablet: top X=0 top Y=0 bottom X=24570 bottom Y=18428 resol X=2540 resol Y=2540
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event3)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)
(II) Open ACPI successful (/var/run/acpid.socket)
(II) VESA(0): Setting up VESA Mode 0x11B (1280x1024)
(--) AlpsPS/2 ALPS GlidePoint: touchpad found
(**) Option "StopBits" "1"
(**) Option "DataBits" "8"
(**) Option "Parity" "None"
(**) Option "Vmin" "1"
(**) Option "Vtime" "10"
(**) Option "FlowControl" "Xoff"
(WW) Serial Wacom Tablet: Waited too long for answer (failed after 3 tries).
(II) Serial Wacom Tablet: serial tablet id 0x90.
(--) Serial Wacom Tablet: Wacom General ISDV4 tablet speed=38400 maxX=24570 maxY=18428 maxZ=127 resX=2540 resY=2540  tilt=disabled
(--) Serial Wacom Tablet: top X=0 top Y=0 bottom X=24570 bottom Y=18428 resol X=2540 resol Y=2540
(--) Serial Wacom Tablet eraser: top X=0 top Y=0 bottom X=24570 bottom Y=18428 resol X=2540 resol Y=2540
(II) Power Button: Device reopened after 1 attempts.
(II) Video Bus: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II) AT Translated Set 2 keyboard: Device reopened after 1 attempts.
(II) PS/2 Mouse: Device reopened after 1 attempts.
(II) Macintosh mouse button emulation: Device reopened after 1 attempts.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) VESA(0): Setting up VESA Mode 0x11B (1280x1024)
(--) AlpsPS/2 ALPS GlidePoint: touchpad found
(WW) Serial Wacom Tablet: Waited too long for answer (failed after 3 tries).
(WW) Serial Wacom Tablet: Waited too long for answer (failed after 3 tries).
(II) Serial Wacom Tablet: serial tablet id 0x90.
(--) Serial Wacom Tablet: Wacom General ISDV4 tablet speed=38400 maxX=24570 maxY=18428 maxZ=127 resX=2540 resY=2540  tilt=disabled
(--) Serial Wacom Tablet: top X=0 top Y=0 bottom X=24570 bottom Y=18428 resol X=2540 resol Y=2540
(--) Serial Wacom Tablet eraser: top X=0 top Y=0 bottom X=24570 bottom Y=18428 resol X=2540 resol Y=2540
(II) Power Button: Device reopened after 1 attempts.
(II) Video Bus: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II) AT Translated Set 2 keyboard: Device reopened after 1 attempts.
(II) PS/2 Mouse: Device reopened after 1 attempts.
(II) Macintosh mouse button emulation: Device reopened after 1 attempts.

```

fbset output in case that's handy:
```
$ fbset -v -i
Linux Frame Buffer Device Configuration Version 2.1 (23/06/1999)
(C) Copyright 1995-1999 by Geert Uytterhoeven

Opening frame buffer device `/dev/fb0'
Using current video mode from `/dev/fb0'

mode "1400x1050-60"
    # D: 101.010 MHz, H: 64.750 kHz, V: 59.954 Hz
    geometry 1400 1050 1408 23738 8
    timings 9900 80 48 3 23 32 4
    hsync high
    accel true
    rgba 8/0,8/0,8/0,0/0
endmode

Getting further frame buffer information
Frame buffer device information:
    Name        : NV32
    Address     : 0xd0000000
    Size        : 33554432
    Type        : PACKED PIXELS
    Visual      : PSEUDOCOLOR
    XPanStep    : 8
    YPanStep    : 1
    YWrapStep   : 0
    LineLength  : 1408
    MMIO Address: 0xfd000000
    MMIO Size   : 16777216
    Accelerator : nVidia Arch 30

```


And some kernel, distro, and module details in case they come in handy...
```
$ uname -a
Linux amaterasu 2.6.31-22-generic #63-Ubuntu SMP Wed Aug 18 22:54:26 UTC 2010 i686 GNU/Linux

$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.04.1 LTS
Release:	10.04
Codename:	lucid

$ lsmod
Module                  Size  Used by
cdc_acm                16544  0 
aes_i586                8124  0 
aes_generic            27484  1 aes_i586
binfmt_misc             8356  1 
ppdev                   6688  0 
bridge                 47952  0 
stp                     2272  1 bridge
bnep                   12060  2 
dm_crypt               12928  0 
arc4                    1660  2 
ecb                     2524  2 
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
pcmcia                 36808  0 
snd_intel8x0m          13896  0 
snd_intel8x0           30168  3 
ath5k                 124772  0 
mac80211              181140  1 ath5k
led_class               4096  1 ath5k
yenta_socket           24296  1 
ath                     8060  1 ath5k
snd_ac97_codec        101216  2 snd_intel8x0m,snd_intel8x0
rsrc_nonstatic         11644  1 yenta_socket
iTCO_wdt               10944  0 
ac97_bus                1532  1 snd_ac97_codec
btusb                  11856  2 
joydev                 10240  0 
pcmcia_core            36592  3 pcmcia,yenta_socket,rsrc_nonstatic
cfg80211               93052  3 ath5k,mac80211,ath
snd_pcm                75296  4 snd_intel8x0m,snd_intel8x0,snd_ac97_codec
snd_timer              22276  1 snd_pcm
pcspkr                  2332  0 
nvidiafb               42812  1 
fb_ddc                  2076  1 nvidiafb
iTCO_vendor_support     3456  1 iTCO_wdt
i2c_algo_bit            5760  1 nvidiafb
vgastate                9628  1 nvidiafb
lp                      8964  0 
snd                    59204  10 snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_pcm,snd_timer
intel_agp              27676  1 
soundcore               7264  1 snd
shpchp                 32272  0 
parport                35340  2 ppdev,lp
agpgart                34988  1 intel_agp
video                  19380  0 
psmouse                57332  0 
toshiba_acpi           10744  0 
serio_raw               5280  0 
snd_page_alloc          9156  3 snd_intel8x0m,snd_intel8x0,snd_pcm
output                  2780  1 video
dm_raid45              84228  0 
e100                   32292  0 
mii                     5212  1 e100
xor                    15620  1 dm_raid45

```

Other useful tools: read-edid, vbetool

Haven't tinkered much with the new drivers much, maybe they will cooperate with some time...

---

### Post by anjames on 2010-08-31
Working on getting a valid edid:

Looks like get-edid doesn't like my monitor/video card setup for some reason:
```
# get-edid 
get-edid: get-edid version 2.0.0

	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f00 bx=0x0 cx=0x0
	Function supported
	Call successful

	VBE version 300
	VBE string at 0x2110 "NVIDIA"

VBE/DDC service about to be called
	Report DDC capabilities

	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f15 bx=0x0 cx=0x0
	Function supported
	Call successful

	Monitor and video card combination does not support DDC1 transfers
	Monitor and video card combination does not support DDC2 transfers
	0 seconds per 128 byte EDID block transfer
	Screen is not blanked during DDC transfer

Reading next EDID block

VBE/DDC service about to be called
	Read EDID

	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
	Function supported
	Call failed

The EDID data should not be trusted as the VBE call failed
Error: output block unchanged

```

so I'll try the method here: [http://www.nvnews.net/vbulletin/showthread.php?t=81635](http://www.nvnews.net/vbulletin/showthread.php?t=81635)

... looks like that doesn't work since the get-edid is failing. Doh, I should have seen that coming. Fortunately though, nouveau was getting good modes with the 2.6.32 kernel (which I dumped since it wouldn't suspend!):

```
$cat /var/log/Xorg.0.log.old
...
(II) NOUVEAU(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
(--) NOUVEAU(0): Virtual size is 1400x1050 (pitch 1408)
(**) NOUVEAU(0):  Driver mode "1400x1050": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) NOUVEAU(0): Modeline "1400x1050"x60.0  108.00  1400 1448 1560 1688  1050 1051 1054 1066 -hsync -vsync (64.0 kHz)
(**) NOUVEAU(0):  Driver mode "1400x1050": 121.8 MHz (scaled from 0.0 MHz), 65.3 kHz, 60.0 Hz
(II) NOUVEAU(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
(**) NOUVEAU(0):  Driver mode "1280x1024": 109.0 MHz (scaled from 0.0 MHz), 63.7 kHz, 59.9 Hz
(II) NOUVEAU(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(**) NOUVEAU(0):  Driver mode "1280x960": 101.2 MHz (scaled from 0.0 MHz), 59.7 kHz, 59.9 Hz
(II) NOUVEAU(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
(**) NOUVEAU(0):  Driver mode "1152x864": 81.8 MHz (scaled from 0.0 MHz), 53.8 kHz, 60.0 Hz
(II) NOUVEAU(0): Modeline "1152x864"x60.0   81.75  1152 1216 1336 1520  864 867 871 897 -hsync +vsync (53.8 kHz)
(**) NOUVEAU(0):  Driver mode "1024x768": 63.5 MHz (scaled from 0.0 MHz), 47.8 kHz, 59.9 Hz
(II) NOUVEAU(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
(**) NOUVEAU(0):  Driver mode "800x600": 38.2 MHz (scaled from 0.0 MHz), 37.4 kHz, 59.9 Hz
(II) NOUVEAU(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
(**) NOUVEAU(0):  Driver mode "640x480": 23.8 MHz (scaled from 0.0 MHz), 29.7 kHz, 59.4 Hz
(II) NOUVEAU(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
(**) NOUVEAU(0):  Driver mode "720x400": 22.2 MHz (scaled from 0.0 MHz), 24.8 kHz, 59.6 Hz
(II) NOUVEAU(0): Modeline "720x400"x59.6   22.25  720 744 808 896  400 403 413 417 -hsync +vsync (24.8 kHz)
(**) NOUVEAU(0):  Driver mode "640x400": 20.0 MHz (scaled from 0.0 MHz), 25.0 kHz, 60.0 Hz
(II) NOUVEAU(0): Modeline "640x400"x60.0   20.00  640 664 720 800  400 403 409 417 -hsync +vsync (25.0 kHz)
(**) NOUVEAU(0):  Driver mode "640x350": 17.5 MHz (scaled from 0.0 MHz), 21.9 kHz, 59.8 Hz
(II) NOUVEAU(0): Modeline "640x350"x59.8   17.50  640 664 720 800  350 353 363 366 -hsync +vsync (21.9 kHz)
(==) NOUVEAU(0): DPI set to (96, 96)
...

```

---

### Post by anjames on 2010-08-31
Working on the vesafb [problem I had](http://ubuntuforums.org/showthread.php?t=1508904&page=2), I dug through /etc/initramfs-tools and found the following:

```
#
# MODULES: [ most | netboot | dep | list ]
#
# most - Add all framebuffer, acpi, filesystem, and harddrive drivers.
#
# dep - Try and guess which modules to load.
#
# netboot - Add the base modules, network modules, but skip block devices.
#
# list - Only include modules from the 'additional modules' list
#

#MODULES=most # ANJ changed to def to prevent vesafb loading
MODULES=dep 

```

I also added nvidiafb to /etc/initramfs-tools/modules so that it would be loaded (it wasn't otherwise, and vga16fb loaded instead), then I ran 'update-initramfs -uv > update-initramfs.log' before and after those changes so we can appreciate the differences. As you can see the 'most' option pulls in vesafb and many other modules. Setting it to 'dep' reduced the number of modules, and I can still boot just fine. In fact, I can also hibernate!

```
$ diff -y -W 200 ~/update-initramfs_most.log ~/update-initramfs_nvidiafb.log 
Keeping /boot/initrd.img-2.6.32-24-generic.dpkg-bak							Keeping /boot/initrd.img-2.6.32-24-generic.dpkg-bak
update-initramfs: Generating /boot/initrd.img-2.6.32-24-generic						update-initramfs: Generating /boot/initrd.img-2.6.32-24-generic
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/hid/hid.ko				   |	Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/video/vgastate.ko
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/hid/usbhid/usbhid.ko		   |	Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/i2c/algos/i2c-algo-bit.ko
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/hid/hid-a4tech.ko			   |	Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/video/fb_ddc.ko
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/hid/hid-apple.ko			   |	Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/video/nvidia/nvidiafb.ko
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/hid/hid-belkin.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/hid/hid-cherry.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/hid/hid-chicony.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/hid/hid-cypress.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/hid/hid-ezkey.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/hid/hid-gyration.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/input/ff-memless.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/hid/hid-logitech.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/hid/hid-microsoft.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/hid/hid-monterey.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/hid/hid-petalynx.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/hid/hid-pl.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/hid/hid-samsung.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/hid/hid-sony.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/hid/hid-sunplus.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/hid/hid-tmff.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/hid/hid-zpff.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/usb/storage/usb-storage.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/fs/isofs/isofs.ko				   <
Adding module /lib/modules/2.6.32-24-generic/kernel/fs/jfs/jfs.ko				   <
Adding module /lib/modules/2.6.32-24-generic/kernel/net/sunrpc/sunrpc.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/net/sunrpc/auth_gss/auth_rpcgss.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/fs/nfs_common/nfs_acl.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/fs/lockd/lockd.ko				   <
Adding module /lib/modules/2.6.32-24-generic/kernel/fs/nfs/nfs.ko				   <
Adding module /lib/modules/2.6.32-24-generic/kernel/fs/reiserfs/reiserfs.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/lib/crc-itu-t.ko				   <
Adding module /lib/modules/2.6.32-24-generic/kernel/fs/udf/udf.ko				   <
Adding module /lib/modules/2.6.32-24-generic/kernel/fs/exportfs/exportfs.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/fs/xfs/xfs.ko				   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/virtio/virtio.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/virtio/virtio_ring.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/virtio/virtio_pci.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/fs/fat/fat.ko				   <
Adding module /lib/modules/2.6.32-24-generic/kernel/fs/fat/vfat.ko				   <
Adding module /lib/modules/2.6.32-24-generic/kernel/fs/nls/nls_cp437.ko				   <
Adding module /lib/modules/2.6.32-24-generic/kernel/fs/nls/nls_iso8859-1.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/net/mii.ko				   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/net/3c59x.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/net/8139cp.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/net/8139too.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/net/8390.ko				   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/net/atlx/atl1.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/net/atl1e/atl1e.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ssb/ssb.ko				   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/net/b44.ko				   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/net/mdio.ko				   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/net/cxgb3/cxgb3.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/net/defxx.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/net/e100.ko				   <
Adding binary /lib/firmware/2.6.32-24-generic/e100/d102e_ucode.bin				   <
Adding firmware e100/d102e_ucode.bin								   <
Adding binary /lib/firmware/2.6.32-24-generic/e100/d101s_ucode.bin				   <
Adding firmware e100/d101s_ucode.bin								   <
Adding binary /lib/firmware/2.6.32-24-generic/e100/d101m_ucode.bin				   <
Adding firmware e100/d101m_ucode.bin								   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/net/e1000/e1000.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/net/e1000e/e1000e.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/net/epic100.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/net/eql.ko				   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/net/fealnx.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/net/forcedeth.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/net/hp100.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/dca/dca.ko				   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/net/igb/igb.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/net/ipg.ko				   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/net/myri10ge/myri10ge.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/net/natsemi.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/net/ne2k-pci.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/fs/configfs/configfs.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/net/netconsole.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/net/niu.ko				   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/net/ns83820.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/net/pcnet32.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/net/qla3xxx.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/net/r8169.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/net/s2io.ko				   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/net/sis900.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/net/skge.ko				   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/net/sky2.ko				   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/net/starfire.ko			   <
Adding binary /lib/firmware/2.6.32-24-generic/adaptec/starfire_tx.bin				   <
Adding firmware adaptec/starfire_tx.bin								   <
Adding binary /lib/firmware/2.6.32-24-generic/adaptec/starfire_rx.bin				   <
Adding firmware adaptec/starfire_rx.bin								   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/net/sundance.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/net/sungem_phy.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/net/sungem.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/net/sunhme.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/net/tg3.ko				   <
Adding binary /lib/firmware/2.6.32-24-generic/tigon/tg3_tso5.bin				   <
Adding firmware tigon/tg3_tso5.bin								   <
Adding binary /lib/firmware/2.6.32-24-generic/tigon/tg3_tso.bin					   <
Adding firmware tigon/tg3_tso.bin								   <
Adding binary /lib/firmware/2.6.32-24-generic/tigon/tg3.bin					   <
Adding firmware tigon/tg3.bin									   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/net/tlan.ko				   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/net/tulip/de2104x.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/net/tulip/de4x5.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/net/tulip/dmfe.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/net/tulip/tulip.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/net/tulip/winbond-840.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/net/tulip/xircom_cb.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/net/via-rhine.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/lib/crc-ccitt.ko				   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/net/via-velocity.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/net/virtio_net.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/net/yellowfin.ko			   <
Copying module directory kernel/drivers/scsi							   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/ch.ko				   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/aacraid/aacraid.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/u14-34f.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/ibmmca.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/scsi_transport_sas.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/scsi_tgt.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/scsi_transport_fc.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/lpfc/lpfc.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/pmcraid.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/scsi_transport_spi.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/53c700.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/NCR_D700.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/scsi_wait_scan.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/megaraid.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/libsrp.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/3w-xxxx.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/qla2xxx/qla2xxx.ko		   <
Adding binary /lib/firmware/ql2500_fw.bin							   <
Adding firmware ql2500_fw.bin									   <
Adding binary /lib/firmware/ql2400_fw.bin							   <
Adding firmware ql2400_fw.bin									   <
Adding binary /lib/firmware/ql2322_fw.bin							   <
Adding firmware ql2322_fw.bin									   <
Adding binary /lib/firmware/ql2300_fw.bin							   <
Adding firmware ql2300_fw.bin									   <
Adding binary /lib/firmware/ql2200_fw.bin							   <
Adding firmware ql2200_fw.bin									   <
Adding binary /lib/firmware/ql2100_fw.bin							   <
Adding firmware ql2100_fw.bin									   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/pcmcia/pcmcia_core.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/pcmcia/pcmcia.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/pcmcia/aha152x_cs.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/qlogicfas408.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/pcmcia/qlogic_cs.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/pcmcia/nsp_cs.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/pcmcia/sym53c500_cs.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/pcmcia/fdomain_cs.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/parport/parport.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/ppa.ko				   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/fd_mcs.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/pas16.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/tmscsim.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/libfc/libfc.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/qla1280.ko			   <
Adding binary /lib/firmware/2.6.32-24-generic/qlogic/12160.bin					   <
Adding firmware qlogic/12160.bin								   <
Adding binary /lib/firmware/2.6.32-24-generic/qlogic/1280.bin					   <
Adding firmware qlogic/1280.bin									   <
Adding binary /lib/firmware/2.6.32-24-generic/qlogic/1040.bin					   <
Adding firmware qlogic/1040.bin									   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/ultrastor.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/uio/uio.ko				   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/net/cnic.ko				   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/scsi_transport_iscsi.ko	   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/libiscsi.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/bnx2i/bnx2i.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/ips.ko				   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/aha1740.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/raid_class.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/fcoe/libfcoe.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/fcoe/fcoe.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/st.ko				   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/hptiop.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/BusLogic.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/dtc.ko				   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/qla4xxx/qla4xxx.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/gdth.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/g_NCR5380.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/megaraid/megaraid_mm.ko	   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/megaraid/megaraid_mbox.ko	   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/megaraid/megaraid_sas.ko	   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/fdomain.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/sim710.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/dc395x.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/libsas/libsas.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/libiscsi_tcp.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/cxgb3i/cxgb3i.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/osd/libosd.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/osd/osd.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/eata.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/stex.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/initio.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/wd7000.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/aha1542.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/dpt_i2o.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/vmw_pvscsi.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/NCR_Q720_mod.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/dmx3191d.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/device_handler/scsi_dh_hp_sw.ko   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/device_handler/scsi_dh_emc.ko	   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/device_handler/scsi_dh_rdac.ko	   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/device_handler/scsi_dh_alua.ko	   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/ipr.ko				   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/scsi_transport_srp.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/imm.ko				   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/misc/enclosure.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/ses.ko				   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/iscsi_tcp.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/osst.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/bfa/bfa.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/sym53c416.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/t128.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/qlogicfas.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/scsi_debug.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/mvsas/mvsas.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/advansys.ko			   <
Adding binary /lib/firmware/2.6.32-24-generic/advansys/38C1600.bin				   <
Adding firmware advansys/38C1600.bin								   <
Adding binary /lib/firmware/2.6.32-24-generic/advansys/38C0800.bin				   <
Adding firmware advansys/38C0800.bin								   <
Adding binary /lib/firmware/2.6.32-24-generic/advansys/3550.bin					   <
Adding firmware advansys/3550.bin								   <
Adding binary /lib/firmware/2.6.32-24-generic/advansys/mcode.bin				   <
Adding firmware advansys/mcode.bin								   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/NCR53c406a.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/fnic/fnic.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/aic7xxx/aic79xx.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/aic7xxx/aic7xxx.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/aic94xx/aic94xx.ko		   <
Adding binary /lib/firmware/aic94xx-seq.fw							   <
Adding firmware aic94xx-seq.fw									   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/be2iscsi/be2iscsi.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/mpt2sas/mpt2sas.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/sym53c8xx_2/sym53c8xx.ko	   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/g_NCR5380_mmio.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/a100u2w.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/nsp32.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/arcmsr/arcmsr.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/atp870u.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/aha152x.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/3w-9xxx.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/in2000.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/message/fusion/mptbase.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/message/fusion/mptscsih.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/message/fusion/mptfc.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/message/fusion/mptsas.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/message/fusion/mptspi.ko		   <
Copying module directory kernel/drivers/block							   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/block/cciss.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/block/nbd.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/block/sx8.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/block/umem.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/block/floppy.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/block/virtio_blk.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/block/aoe/aoe.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/block/cryptoloop.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/block/DAC960.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/block/paride/paride.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/block/paride/comm.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/block/paride/frpw.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/block/paride/aten.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/block/paride/pg.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/block/paride/friq.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/block/paride/kbic.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/block/paride/on26.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/block/paride/pt.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/block/paride/pf.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/block/paride/pcd.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/block/paride/dstr.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/block/paride/epat.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/block/paride/epia.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/block/paride/fit3.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/block/paride/fit2.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/block/paride/ktti.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/block/paride/on20.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/block/paride/bpck6.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/block/paride/bpck.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/block/paride/pd.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/block/cpqarray.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/block/osdblk.ko			   <
Copying module directory kernel/drivers/usb/storage						   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/usb/storage/ums-sddr55.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/usb/storage/ums-datafab.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/usb/storage/ums-karma.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/usb/storage/ums-cypress.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/usb/storage/ums-usbat.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/usb/storage/ums-alauda.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/usb/storage/ums-onetouch.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/usb/storage/ums-jumpshot.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/usb/storage/ums-freecom.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/usb/storage/ums-sddr09.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/usb/storage/ums-isd200.ko		   <
Copying module directory kernel/drivers/ata							   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ata/pata_ns87410.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ata/pata_legacy.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ata/pata_atp867x.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ata/sata_qstor.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ata/pata_mpiix.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ata/pata_sc1200.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ata/pata_cs5520.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ata/pata_pdc2027x.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ata/sata_sis.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ata/pata_rdc.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ata/pata_ns87415.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ata/pata_netcell.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ata/pata_amd.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ata/sata_mv.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ata/pata_cs5530.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ata/pata_cmd640.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ata/pata_it821x.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ata/pata_qdi.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ata/pata_opti.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ata/pata_jmicron.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ata/pata_winbond.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ata/sata_sil.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ata/pata_cs5535.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ata/pata_marvell.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ata/pata_optidma.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ata/sata_uli.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ata/sata_via.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ata/pata_isapnp.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ata/pata_efar.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ata/sata_sil24.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ata/pata_serverworks.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ata/sata_promise.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ata/sata_vsc.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ata/pata_cs5536.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ata/pata_atiixp.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ata/pata_pdc202xx_old.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ata/pata_rz1000.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ata/pata_radisys.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ata/pata_via.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ata/sata_inic162x.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ata/ahci.ko				   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ata/pata_it8213.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ata/sata_svw.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ata/pata_sl82c105.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ata/sata_sx4.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ata/pata_pcmcia.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ata/pata_cmd64x.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ata/pata_hpt3x2n.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ata/pata_ninja32.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ata/pata_sil680.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ata/pata_hpt37x.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ata/pata_ali.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ata/pata_hpt3x3.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ata/sata_nv.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ata/pata_artop.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ata/pata_oldpiix.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ata/pata_hpt366.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ata/pata_triflex.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ata/pata_cypress.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ata/pata_sch.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/message/i2o/i2o_core.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/message/i2o/i2o_block.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ieee1394/ieee1394.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ieee1394/ohci1394.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/ieee1394/sbp2.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/firewire/firewire-core.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/firewire/firewire-ohci.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/firewire/firewire-sbp2.ko		   <
Adding binary /usr/share/initramfs-tools/init								Adding binary /usr/share/initramfs-tools/init
Adding binary /etc/initramfs-tools/initramfs.conf							Adding binary /etc/initramfs-tools/initramfs.conf
Adding binary /usr/share/initramfs-tools/conf.d/uswsusp							Adding binary /usr/share/initramfs-tools/conf.d/uswsusp
Adding binary /usr/lib/initramfs-tools/bin//busybox							Adding binary /usr/lib/initramfs-tools/bin//busybox
Adding library /lib/libc.so.6										Adding library /lib/libc.so.6
Adding library /lib/ld-linux.so.2									Adding library /lib/ld-linux.so.2
Adding binary /usr/lib/initramfs-tools/bin/wait-for-root						Adding binary /usr/lib/initramfs-tools/bin/wait-for-root
Adding library /lib/libudev.so.0									Adding library /lib/libudev.so.0
Adding binary /sbin/modprobe										Adding binary /sbin/modprobe
Adding binary /sbin/depmod										Adding binary /sbin/depmod
Adding binary /sbin/rmmod										Adding binary /sbin/rmmod
Adding binary /sbin/blkid										Adding binary /sbin/blkid
Adding library /lib/libblkid.so.1									Adding library /lib/libblkid.so.1
Adding library /lib/libuuid.so.1									Adding library /lib/libuuid.so.1
Calling hook brltty											Calling hook brltty
Adding binary /usr/share/brltty/initramfs/brltty.sh							Adding binary /usr/share/brltty/initramfs/brltty.sh
Adding binary /sbin/brltty-setup									Adding binary /sbin/brltty-setup
Calling hook compcache											Calling hook compcache
Calling hook cryptroot											Calling hook cryptroot
Copying module directory kernel/arch/x86/crypto							   <
Adding module /lib/modules/2.6.32-24-generic/kernel/arch/x86/crypto/crc32c-intel.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/crypto/aes_generic.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/arch/x86/crypto/aes-i586.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/crypto/twofish_common.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/arch/x86/crypto/twofish-i586.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/arch/x86/crypto/salsa20-i586.ko		   <
Copying module directory kernel/crypto								   <
Adding module /lib/modules/2.6.32-24-generic/kernel/crypto/sha1_generic.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/crypto/camellia.ko				   <
Adding module /lib/modules/2.6.32-24-generic/kernel/crypto/authenc.ko				   <
Adding module /lib/modules/2.6.32-24-generic/kernel/crypto/crypto_null.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/crypto/seqiv.ko				   <
Adding module /lib/modules/2.6.32-24-generic/kernel/crypto/cryptd.ko				   <
Adding module /lib/modules/2.6.32-24-generic/kernel/crypto/xcbc.ko				   <
Adding module /lib/modules/2.6.32-24-generic/kernel/crypto/salsa20_generic.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/crypto/md4.ko				   <
Adding module /lib/modules/2.6.32-24-generic/kernel/lib/zlib_deflate/zlib_deflate.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/crypto/deflate.ko				   <
Adding module /lib/modules/2.6.32-24-generic/kernel/crypto/cts.ko				   <
Adding module /lib/modules/2.6.32-24-generic/kernel/crypto/rmd256.ko				   <
Adding module /lib/modules/2.6.32-24-generic/kernel/crypto/zlib.ko				   <
Adding module /lib/modules/2.6.32-24-generic/kernel/crypto/crc32c.ko				   <
Adding module /lib/modules/2.6.32-24-generic/kernel/crypto/ansi_cprng.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/crypto/rmd320.ko				   <
Adding module /lib/modules/2.6.32-24-generic/kernel/crypto/wp512.ko				   <
Adding module /lib/modules/2.6.32-24-generic/kernel/lib/lzo/lzo_compress.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/lib/lzo/lzo_decompress.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/crypto/lzo.ko				   <
Adding module /lib/modules/2.6.32-24-generic/kernel/crypto/sha512_generic.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/crypto/rmd128.ko				   <
Adding module /lib/modules/2.6.32-24-generic/kernel/crypto/ccm.ko				   <
Adding module /lib/modules/2.6.32-24-generic/kernel/crypto/tgr192.ko				   <
Adding module /lib/modules/2.6.32-24-generic/kernel/crypto/pcbc.ko				   <
Adding module /lib/modules/2.6.32-24-generic/kernel/crypto/twofish.ko				   <
Adding module /lib/modules/2.6.32-24-generic/kernel/crypto/tea.ko				   <
Adding module /lib/modules/2.6.32-24-generic/kernel/crypto/vmac.ko				   <
Adding module /lib/modules/2.6.32-24-generic/kernel/crypto/xor.ko				   <
Adding module /lib/modules/2.6.32-24-generic/kernel/crypto/async_tx/async_tx.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/crypto/async_tx/async_xor.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/crypto/async_tx/async_memcpy.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/md/raid6_pq.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/crypto/async_tx/async_pq.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/crypto/async_tx/async_raid6_recov.ko	   <
Adding module /lib/modules/2.6.32-24-generic/kernel/crypto/async_tx/raid6test.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/crypto/gf128mul.ko				   <
Adding module /lib/modules/2.6.32-24-generic/kernel/crypto/lrw.ko				   <
Adding module /lib/modules/2.6.32-24-generic/kernel/crypto/seed.ko				   <
Adding module /lib/modules/2.6.32-24-generic/kernel/crypto/ctr.ko				   <
Adding module /lib/modules/2.6.32-24-generic/kernel/crypto/des_generic.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/crypto/anubis.ko				   <
Adding module /lib/modules/2.6.32-24-generic/kernel/crypto/tcrypt.ko				   <
Adding module /lib/modules/2.6.32-24-generic/kernel/crypto/fcrypt.ko				   <
Adding module /lib/modules/2.6.32-24-generic/kernel/crypto/blowfish.ko				   <
Adding module /lib/modules/2.6.32-24-generic/kernel/crypto/serpent.ko				   <
Adding module /lib/modules/2.6.32-24-generic/kernel/crypto/gcm.ko				   <
Adding module /lib/modules/2.6.32-24-generic/kernel/crypto/ghash-generic.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/crypto/xts.ko				   <
Adding module /lib/modules/2.6.32-24-generic/kernel/crypto/sha256_generic.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/crypto/michael_mic.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/crypto/rmd160.ko				   <
Adding module /lib/modules/2.6.32-24-generic/kernel/crypto/cast5.ko				   <
Adding module /lib/modules/2.6.32-24-generic/kernel/crypto/arc4.ko				   <
Adding module /lib/modules/2.6.32-24-generic/kernel/crypto/khazad.ko				   <
Adding module /lib/modules/2.6.32-24-generic/kernel/crypto/cast6.ko				   <
Copying module directory kernel/arch/x86/crypto							   <
Copying module directory kernel/crypto								   <
Copying module directory kernel/arch/x86/crypto							   <
Copying module directory kernel/crypto								   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/md/dm-crypt.ko				Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/md/dm-crypt.ko
Adding binary /sbin/cryptsetup										Adding binary /sbin/cryptsetup
Adding library /lib/libpopt.so.0									Adding library /lib/libpopt.so.0
Adding library /lib/libdevmapper.so.1.02.1								Adding library /lib/libdevmapper.so.1.02.1
Adding library /lib/libgcrypt.so.11									Adding library /lib/libgcrypt.so.11
Adding library /lib/libgpg-error.so.0									Adding library /lib/libgpg-error.so.0
Adding library /lib/libselinux.so.1									Adding library /lib/libselinux.so.1
Adding library /lib/libdl.so.2										Adding library /lib/libdl.so.2
Adding binary /sbin/dmsetup										Adding binary /sbin/dmsetup
Adding binary /lib/cryptsetup/askpass									Adding binary /lib/cryptsetup/askpass
Calling hook dmraid											Calling hook dmraid
												   >	Adding module /lib/modules/2.6.32-24-generic/kernel/crypto/xor.ko
Adding module /lib/modules/2.6.32-24-generic/kernel/ubuntu/dm-raid4-5/dm-raid45.ko			Adding module /lib/modules/2.6.32-24-generic/kernel/ubuntu/dm-raid4-5/dm-raid45.ko
Adding binary /sbin/dmraid										Adding binary /sbin/dmraid
Adding library /lib/libdmraid.so.1.0.0.rc16								Adding library /lib/libdmraid.so.1.0.0.rc16
Adding library /lib/libsepol.so.1									Adding library /lib/libsepol.so.1
Adding binary /sbin/dmraid-activate									Adding binary /sbin/dmraid-activate
Calling hook fixrtc											Calling hook fixrtc
Adding binary /bin/date											Adding binary /bin/date
Adding library /lib/librt.so.1										Adding library /lib/librt.so.1
Adding library /lib/libpthread.so.0									Adding library /lib/libpthread.so.0
Adding binary /sbin/hwclock										Adding binary /sbin/hwclock
Adding binary /sbin/dumpe2fs										Adding binary /sbin/dumpe2fs
Adding library /lib/libext2fs.so.2									Adding library /lib/libext2fs.so.2
Adding library /lib/libcom_err.so.2									Adding library /lib/libcom_err.so.2
Adding library /lib/libe2p.so.2										Adding library /lib/libe2p.so.2
Calling hook framebuffer										Calling hook framebuffer
Copying module directory kernel/drivers/char/agp							Copying module directory kernel/drivers/char/agp
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/char/agp/agpgart.ko				Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/char/agp/agpgart.ko
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/char/agp/via-agp.ko				Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/char/agp/via-agp.ko
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/char/agp/sis-agp.ko				Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/char/agp/sis-agp.ko
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/char/agp/ati-agp.ko				Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/char/agp/ati-agp.ko
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/char/agp/nvidia-agp.ko			Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/char/agp/nvidia-agp.ko
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/char/agp/efficeon-agp.ko			Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/char/agp/efficeon-agp.ko
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/char/agp/ali-agp.ko				Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/char/agp/ali-agp.ko
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/char/agp/intel-agp.ko			Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/char/agp/intel-agp.ko
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/char/agp/amd64-agp.ko			Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/char/agp/amd64-agp.ko
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/char/agp/amd-k7-agp.ko			Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/char/agp/amd-k7-agp.ko
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/char/agp/sworks-agp.ko			Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/char/agp/sworks-agp.ko
Copying module directory kernel/drivers/gpu								Copying module directory kernel/drivers/gpu
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/gpu/drm/drm.ko				Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/gpu/drm/drm.ko
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/video/sis/sisfb.ko				Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/video/sis/sisfb.ko
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/gpu/drm/sis/sis.ko				Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/gpu/drm/sis/sis.ko
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/gpu/drm/r128/r128.ko			Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/gpu/drm/r128/r128.ko
Adding binary /lib/firmware/2.6.32-24-generic/r128/r128_cce.bin						Adding binary /lib/firmware/2.6.32-24-generic/r128/r128_cce.bin
Adding firmware r128/r128_cce.bin									Adding firmware r128/r128_cce.bin
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/gpu/drm/mga/mga.ko				Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/gpu/drm/mga/mga.ko
Adding binary /lib/firmware/2.6.32-24-generic/matrox/g400_warp.fw					Adding binary /lib/firmware/2.6.32-24-generic/matrox/g400_warp.fw
Adding firmware matrox/g400_warp.fw									Adding firmware matrox/g400_warp.fw
Adding binary /lib/firmware/2.6.32-24-generic/matrox/g200_warp.fw					Adding binary /lib/firmware/2.6.32-24-generic/matrox/g200_warp.fw
Adding firmware matrox/g200_warp.fw									Adding firmware matrox/g200_warp.fw
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/gpu/drm/savage/savage.ko			Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/gpu/drm/savage/savage.ko
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/gpu/drm/i810/i810.ko			Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/gpu/drm/i810/i810.ko
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/gpu/drm/ttm/ttm.ko				Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/gpu/drm/ttm/ttm.ko
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/gpu/drm/i830/i830.ko			Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/gpu/drm/i830/i830.ko
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/i2c/algos/i2c-algo-bit.ko		   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/gpu/drm/drm_kms_helper.ko			Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/gpu/drm/drm_kms_helper.ko
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/gpu/drm/radeon/radeon.ko			Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/gpu/drm/radeon/radeon.ko
Adding binary /lib/firmware/2.6.32-24-generic/radeon/R520_cp.bin					Adding binary /lib/firmware/2.6.32-24-generic/radeon/R520_cp.bin
Adding firmware radeon/R520_cp.bin									Adding firmware radeon/R520_cp.bin
Adding binary /lib/firmware/2.6.32-24-generic/radeon/RS600_cp.bin					Adding binary /lib/firmware/2.6.32-24-generic/radeon/RS600_cp.bin
Adding firmware radeon/RS600_cp.bin									Adding firmware radeon/RS600_cp.bin
Adding binary /lib/firmware/2.6.32-24-generic/radeon/RS690_cp.bin					Adding binary /lib/firmware/2.6.32-24-generic/radeon/RS690_cp.bin
Adding firmware radeon/RS690_cp.bin									Adding firmware radeon/RS690_cp.bin
Adding binary /lib/firmware/2.6.32-24-generic/radeon/R420_cp.bin					Adding binary /lib/firmware/2.6.32-24-generic/radeon/R420_cp.bin
Adding firmware radeon/R420_cp.bin									Adding firmware radeon/R420_cp.bin
Adding binary /lib/firmware/2.6.32-24-generic/radeon/R300_cp.bin					Adding binary /lib/firmware/2.6.32-24-generic/radeon/R300_cp.bin
Adding firmware radeon/R300_cp.bin									Adding firmware radeon/R300_cp.bin
Adding binary /lib/firmware/2.6.32-24-generic/radeon/R200_cp.bin					Adding binary /lib/firmware/2.6.32-24-generic/radeon/R200_cp.bin
Adding firmware radeon/R200_cp.bin									Adding firmware radeon/R200_cp.bin
Adding binary /lib/firmware/2.6.32-24-generic/radeon/R100_cp.bin					Adding binary /lib/firmware/2.6.32-24-generic/radeon/R100_cp.bin
Adding firmware radeon/R100_cp.bin									Adding firmware radeon/R100_cp.bin
Adding binary /lib/firmware/2.6.32-24-generic/radeon/RV710_me.bin					Adding binary /lib/firmware/2.6.32-24-generic/radeon/RV710_me.bin
Adding firmware radeon/RV710_me.bin									Adding firmware radeon/RV710_me.bin
Adding binary /lib/firmware/2.6.32-24-generic/radeon/RV710_pfp.bin					Adding binary /lib/firmware/2.6.32-24-generic/radeon/RV710_pfp.bin
Adding firmware radeon/RV710_pfp.bin									Adding firmware radeon/RV710_pfp.bin
Adding binary /lib/firmware/2.6.32-24-generic/radeon/RV730_me.bin					Adding binary /lib/firmware/2.6.32-24-generic/radeon/RV730_me.bin
Adding firmware radeon/RV730_me.bin									Adding firmware radeon/RV730_me.bin
Adding binary /lib/firmware/2.6.32-24-generic/radeon/RV730_pfp.bin					Adding binary /lib/firmware/2.6.32-24-generic/radeon/RV730_pfp.bin
Adding firmware radeon/RV730_pfp.bin									Adding firmware radeon/RV730_pfp.bin
Adding binary /lib/firmware/2.6.32-24-generic/radeon/RV770_me.bin					Adding binary /lib/firmware/2.6.32-24-generic/radeon/RV770_me.bin
Adding firmware radeon/RV770_me.bin									Adding firmware radeon/RV770_me.bin
Adding binary /lib/firmware/2.6.32-24-generic/radeon/RV770_pfp.bin					Adding binary /lib/firmware/2.6.32-24-generic/radeon/RV770_pfp.bin
Adding firmware radeon/RV770_pfp.bin									Adding firmware radeon/RV770_pfp.bin
Adding binary /lib/firmware/2.6.32-24-generic/radeon/RS780_me.bin					Adding binary /lib/firmware/2.6.32-24-generic/radeon/RS780_me.bin
Adding firmware radeon/RS780_me.bin									Adding firmware radeon/RS780_me.bin
Adding binary /lib/firmware/2.6.32-24-generic/radeon/RS780_pfp.bin					Adding binary /lib/firmware/2.6.32-24-generic/radeon/RS780_pfp.bin
Adding firmware radeon/RS780_pfp.bin									Adding firmware radeon/RS780_pfp.bin
Adding binary /lib/firmware/2.6.32-24-generic/radeon/RV670_me.bin					Adding binary /lib/firmware/2.6.32-24-generic/radeon/RV670_me.bin
Adding firmware radeon/RV670_me.bin									Adding firmware radeon/RV670_me.bin
Adding binary /lib/firmware/2.6.32-24-generic/radeon/RV670_pfp.bin					Adding binary /lib/firmware/2.6.32-24-generic/radeon/RV670_pfp.bin
Adding firmware radeon/RV670_pfp.bin									Adding firmware radeon/RV670_pfp.bin
Adding binary /lib/firmware/2.6.32-24-generic/radeon/RV635_me.bin					Adding binary /lib/firmware/2.6.32-24-generic/radeon/RV635_me.bin
Adding firmware radeon/RV635_me.bin									Adding firmware radeon/RV635_me.bin
Adding binary /lib/firmware/2.6.32-24-generic/radeon/RV635_pfp.bin					Adding binary /lib/firmware/2.6.32-24-generic/radeon/RV635_pfp.bin
Adding firmware radeon/RV635_pfp.bin									Adding firmware radeon/RV635_pfp.bin
Adding binary /lib/firmware/2.6.32-24-generic/radeon/RV620_me.bin					Adding binary /lib/firmware/2.6.32-24-generic/radeon/RV620_me.bin
Adding firmware radeon/RV620_me.bin									Adding firmware radeon/RV620_me.bin
Adding binary /lib/firmware/2.6.32-24-generic/radeon/RV620_pfp.bin					Adding binary /lib/firmware/2.6.32-24-generic/radeon/RV620_pfp.bin
Adding firmware radeon/RV620_pfp.bin									Adding firmware radeon/RV620_pfp.bin
Adding binary /lib/firmware/2.6.32-24-generic/radeon/RV630_me.bin					Adding binary /lib/firmware/2.6.32-24-generic/radeon/RV630_me.bin
Adding firmware radeon/RV630_me.bin									Adding firmware radeon/RV630_me.bin
Adding binary /lib/firmware/2.6.32-24-generic/radeon/RV630_pfp.bin					Adding binary /lib/firmware/2.6.32-24-generic/radeon/RV630_pfp.bin
Adding firmware radeon/RV630_pfp.bin									Adding firmware radeon/RV630_pfp.bin
Adding binary /lib/firmware/2.6.32-24-generic/radeon/RV610_me.bin					Adding binary /lib/firmware/2.6.32-24-generic/radeon/RV610_me.bin
Adding firmware radeon/RV610_me.bin									Adding firmware radeon/RV610_me.bin
Adding binary /lib/firmware/2.6.32-24-generic/radeon/RV610_pfp.bin					Adding binary /lib/firmware/2.6.32-24-generic/radeon/RV610_pfp.bin
Adding firmware radeon/RV610_pfp.bin									Adding firmware radeon/RV610_pfp.bin
Adding binary /lib/firmware/2.6.32-24-generic/radeon/R600_me.bin					Adding binary /lib/firmware/2.6.32-24-generic/radeon/R600_me.bin
Adding firmware radeon/R600_me.bin									Adding firmware radeon/R600_me.bin
Adding binary /lib/firmware/2.6.32-24-generic/radeon/R600_pfp.bin					Adding binary /lib/firmware/2.6.32-24-generic/radeon/R600_pfp.bin
Adding firmware radeon/R600_pfp.bin									Adding firmware radeon/R600_pfp.bin
Adding binary /lib/firmware/radeon/R700_rlc.bin								Adding binary /lib/firmware/radeon/R700_rlc.bin
Adding firmware radeon/R700_rlc.bin									Adding firmware radeon/R700_rlc.bin
Adding binary /lib/firmware/radeon/R600_rlc.bin								Adding binary /lib/firmware/radeon/R600_rlc.bin
Adding firmware radeon/R600_rlc.bin									Adding firmware radeon/R600_rlc.bin
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/gpu/drm/via/via.ko				Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/gpu/drm/via/via.ko
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/video/output.ko				Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/video/output.ko
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/acpi/video.ko				Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/acpi/video.ko
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/gpu/drm/i915/i915.ko			Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/gpu/drm/i915/i915.ko
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/gpu/drm/i2c/ch7006.ko			Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/gpu/drm/i2c/ch7006.ko
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/gpu/drm/tdfx/tdfx.ko			Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/gpu/drm/tdfx/tdfx.ko
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/gpu/drm/nouveau/nouveau.ko			Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/gpu/drm/nouveau/nouveau.ko
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/video/console/softcursor.ko			Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/video/console/softcursor.ko
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/video/console/bitblit.ko			Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/video/console/bitblit.ko
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/video/console/font.ko			Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/video/console/font.ko
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/video/console/tileblit.ko			Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/video/console/tileblit.ko
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/video/console/fbcon.ko			Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/video/console/fbcon.ko
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/video/vesafb.ko				Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/video/vesafb.ko
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/video/vgastate.ko			   <
Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/video/vga16fb.ko				Adding module /lib/modules/2.6.32-24-generic/kernel/drivers/video/vga16fb.ko
Calling hook fuse_utils											Calling hook fuse_utils
Adding binary /sbin/mount.fuse										Adding binary /sbin/mount.fuse
Calling hook thermal											Calling hook thermal
Calling hook tuxonice_userui										Calling hook tuxonice_userui
This kernel does not seem to support TuxOnIce user interface, skipping...				This kernel does not seem to support TuxOnIce user interface, skipping...
Calling hook udev											Calling hook udev
Adding binary /usr/bin/pkill										Adding binary /usr/bin/pkill
Adding library /lib/libproc-3.2.8.so									Adding library /lib/libproc-3.2.8.so
Adding binary /sbin/udevd										Adding binary /sbin/udevd
Adding binary /sbin/udevadm										Adding binary /sbin/udevadm
Adding binary /lib/udev/firmware									Adding binary /lib/udev/firmware
Adding binary /lib/udev/ata_id										Adding binary /lib/udev/ata_id
Adding binary /lib/udev/usb_id										Adding binary /lib/udev/usb_id
Adding binary /sbin/blkid										Adding binary /sbin/blkid
Adding binary /lib/udev/scsi_id										Adding binary /lib/udev/scsi_id
Adding binary /lib/udev/path_id										Adding binary /lib/udev/path_id
Adding binary /lib/udev/edd_id										Adding binary /lib/udev/edd_id
Calling hook uswsusp											Calling hook uswsusp
Adding binary /usr/lib/uswsusp/resume									Adding binary /usr/lib/uswsusp/resume
Adding library /usr/lib/liblzo2.so.2									Adding library /usr/lib/liblzo2.so.2
Calling hook cryptpassdev										Calling hook cryptpassdev
Calling hook cryptopensc										Calling hook cryptopensc
Calling hook cryptopenct										Calling hook cryptopenct
Calling hook plymouth											Calling hook plymouth
Adding binary /sbin/plymouthd										Adding binary /sbin/plymouthd
Adding library /lib/libply.so.2										Adding library /lib/libply.so.2
Adding library /lib/libply-splash-core.so.2								Adding library /lib/libply-splash-core.so.2
Adding library /lib/libm.so.6										Adding library /lib/libm.so.6
Adding binary /bin/plymouth										Adding binary /bin/plymouth
Adding binary /lib/plymouth/details.so									Adding binary /lib/plymouth/details.so
Adding binary /lib/plymouth/ubuntu-text.so								Adding binary /lib/plymouth/ubuntu-text.so
Adding binary /lib/plymouth/script.so									Adding binary /lib/plymouth/script.so
Adding library /lib/libply-splash-graphics.so.2								Adding library /lib/libply-splash-graphics.so.2
Adding library /lib/libpng12.so.0									Adding library /lib/libpng12.so.0
Adding library /lib/libz.so.1										Adding library /lib/libz.so.1
Adding binary /lib/plymouth/label.so									Adding binary /lib/plymouth/label.so
Adding library /usr/lib/libpangocairo-1.0.so.0								Adding library /usr/lib/libpangocairo-1.0.so.0
Adding library /usr/lib/libpango-1.0.so.0								Adding library /usr/lib/libpango-1.0.so.0
Adding library /usr/lib/libcairo.so.2									Adding library /usr/lib/libcairo.so.2
Adding library /usr/lib/libgobject-2.0.so.0								Adding library /usr/lib/libgobject-2.0.so.0
Adding library /usr/lib/libgmodule-2.0.so.0								Adding library /usr/lib/libgmodule-2.0.so.0
Adding library /usr/lib/libgthread-2.0.so.0								Adding library /usr/lib/libgthread-2.0.so.0
Adding library /lib/libglib-2.0.so.0									Adding library /lib/libglib-2.0.so.0
Adding library /usr/lib/libpangoft2-1.0.so.0								Adding library /usr/lib/libpangoft2-1.0.so.0
Adding library /usr/lib/libfreetype.so.6								Adding library /usr/lib/libfreetype.so.6
Adding library /usr/lib/libfontconfig.so.1								Adding library /usr/lib/libfontconfig.so.1
Adding library /usr/lib/libpixman-1.so.0								Adding library /usr/lib/libpixman-1.so.0
Adding library /usr/lib/libdirectfb-1.2.so.0								Adding library /usr/lib/libdirectfb-1.2.so.0
Adding library /usr/lib/libfusion-1.2.so.0								Adding library /usr/lib/libfusion-1.2.so.0
Adding library /usr/lib/libdirect-1.2.so.0								Adding library /usr/lib/libdirect-1.2.so.0
Adding library /usr/lib/libxcb-render-util.so.0								Adding library /usr/lib/libxcb-render-util.so.0
Adding library /usr/lib/libxcb-render.so.0								Adding library /usr/lib/libxcb-render.so.0
Adding library /usr/lib/libxcb.so.1									Adding library /usr/lib/libxcb.so.1
Adding library /usr/lib/libXrender.so.1									Adding library /usr/lib/libXrender.so.1
Adding library /usr/lib/libX11.so.6									Adding library /usr/lib/libX11.so.6
Adding library /lib/libpcre.so.3									Adding library /lib/libpcre.so.3
Adding library /lib/libexpat.so.1									Adding library /lib/libexpat.so.1
Adding library /usr/lib/libXau.so.6									Adding library /usr/lib/libXau.so.6
Adding library /usr/lib/libXdmcp.so.6									Adding library /usr/lib/libXdmcp.so.6
Adding binary /lib/plymouth/renderers/frame-buffer.so							Adding binary /lib/plymouth/renderers/frame-buffer.so
Adding binary /lib/plymouth/renderers/drm.so								Adding binary /lib/plymouth/renderers/drm.so
Adding library /lib/libdrm_intel.so.1									Adding library /lib/libdrm_intel.so.1
Adding library /lib/libdrm.so.2										Adding library /lib/libdrm.so.2
Adding library /lib/libdrm_radeon.so.1									Adding library /lib/libdrm_radeon.so.1
Adding library /lib/libdrm_nouveau.so.1									Adding library /lib/libdrm_nouveau.so.1
Adding binary /lib/plymouth/renderers/vga16fb.so							Adding binary /lib/plymouth/renderers/vga16fb.so
Calling hook ntfs_3g											Calling hook ntfs_3g
Adding binary /bin/ntfs-3g										Adding binary /bin/ntfs-3g
Adding library //lib/libfuse.so.2									Adding library //lib/libfuse.so.2
Adding library //lib/libntfs-3g.so.75									Adding library //lib/libntfs-3g.so.75
Calling hook console_setup										Calling hook console_setup
Calling hook kbd											Calling hook kbd
Adding binary /bin/setfont										Adding binary /bin/setfont
Adding binary /bin/kbd_mode										Adding binary /bin/kbd_mode
Adding binary /bin/loadkeys										Adding binary /bin/loadkeys
Calling hook watershed											Calling hook watershed
Adding binary /lib/udev/watershed									Adding binary /lib/udev/watershed
Calling hook dmsetup											Calling hook dmsetup
Building cpio /boot/initrd.img-2.6.32-24-generic.new initramfs						Building cpio /boot/initrd.img-2.6.32-24-generic.new initramfs

```

But can I get dual-head working...

---

### Post by anjames on 2010-08-31
First, created a new xorg.conf with 'Xorg -configure', then I modified ChaoSlayer's xorg.conf to more suit my own system: included my wacom stylus, and resolution specific changes

```
$ cat /etc/X11/xorg.conf
# ANJ modified from `Xorg -configure`
# with ChaoSlayer's dual-head options from: http://ubuntuforums.org/showthread.php?p=9786779#post9786779

Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
#	FontPath     "/usr/share/fonts/X11/cyrillic" #ANJ Commented to avoid warning
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "dbe"
	Load  "dri2"
	Load  "record"
	Load  "dri"
	Load  "glx"
	Load  "extmod"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "InputDevice" # as per https://help.ubuntu.com/community/Wacom
  Identifier    "Stylus0"
  Driver        "wacom"
  Option        "Device"        "/dev/ttyS0"
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4" 
  #Option "Button2" "2"
  #Option "Button3" "3"
  Option	"KeepShape" "on"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
	Option		"DPMS" # VESA Display Power Management Signaling
	Option         "PreferredMode" "1400x1050"
	# ANJ Modelines probed my nouveau added after config
	# also tried http://ubuntuforums.org/showthread.php?t=316985
	#Modeline "1400x1050"  108.00  1400 1448 1560 1688  1050 1051 1054 1066 -hsync -vsync
	#Modeline "1400x1050"  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync
	#Modeline "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
	#Modeline "1280x960"  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync
	#Modeline "1152x864"   81.75  1152 1216 1336 1520  864 867 871 897 -hsync +vsync
	#Modeline "1024x768"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
	#Modeline "800x600"   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync
	#Modeline "640x480"   23.75  640 664 720 800  480 483 487 500 -hsync +vsync
	#Modeline "720x400"   22.25  720 744 808 896  400 403 413 417 -hsync +vsync
	#Modeline "640x400"   20.00  640 664 720 800  400 403 409 417 -hsync +vsync
	#Modeline "640x350"   17.50  640 664 720 800  350 353 363 366 -hsync +vsync
EndSection

Section "Monitor"
	Identifier     "Monitor1"
	HorizSync       30.0 - 110.0
	VertRefresh     50.0 - 160.0
#	DisplaySize     401 303
	Option         "PreferredMode" "1600x1200"
	Option         "RightOf" "Monitor0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "SWcursor"           	# [<bool>]
        #Option     "HWcursor"           	# [<bool>]
        #Option     "NoAccel"            	# [<bool>]
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "VideoKey"           	# <i>
        #Option     "EXAPixmaps"         	# [<bool>]
	Identifier  "Card0"
	Driver      "nouveau"
	VendorName  "nVidia Corporation"
	BoardName   "NV34M [GeForce FX Go5200 32M/64M]"
	BusID       "PCI:1:0:0"
	Option      "monitor-LVDS-0" "primary"
	Option      "monitor-VGA-0" "secondary"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	DefaultDepth	24
	SubSection "Display"
		Depth     24
		Viewport   0 0
		Virtual    3000 1200
	EndSubSection
EndSection

```

so now I sort through Xorg.0.log:
```

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux amaterasu 2.6.32-24-generic #41-Ubuntu SMP Thu Aug 19 01:12:52 UTC 2010 i686
Kernel command line: root=UUID=22578c46-436c-4302-b1cd-bba53d865367 ro resume=/dev/hda5 verbose
Build Date: 21 July 2010  12:47:34PM
xorg-server 2:1.7.6-2ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Aug 31 11:36:33 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "X.org Configured"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Card0"
(**) |-->Input Device "Mouse0"
(**) |-->Input Device "Keyboard0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins,
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(**) ModulePath set to "/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Mouse0
(WW) Disabling Keyboard0
(II) Loader magic: 0x81f0e80
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(--) using VT number 8

(--) PCI:*(0:1:0:0) 10de:0328:1179:0010 nVidia Corporation NV34M [GeForce FX Go5200 32M/64M] rev 161, Mem @ 0xfd000000/16777216, 0xd0000000/268435456
(II) Open ACPI successful (/var/run/acpid.socket)
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded. This was enabled by default and also specified in the config file.
(II) "dri" will be loaded. This was enabled by default and also specified in the config file.
(II) "dri2" will be loaded. This was enabled by default and also specified in the config file.
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "nouveau"
(II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
(II) Module nouveau: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.0.15
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) NOUVEAU driver Date:   Wed Feb 10 18:43:39 2010 +0100
(II) NOUVEAU driver for NVIDIA chipset families :
	RIVA TNT    (NV04)
	RIVA TNT2   (NV05)
	GeForce 256 (NV10)
	GeForce 2   (NV11, NV15)
	GeForce 4MX (NV17, NV18)
	GeForce 3   (NV20)
	GeForce 4Ti (NV25, NV28)
	GeForce FX  (NV3x)
	GeForce 6   (NV4x)
	GeForce 7   (G7x)
	GeForce 8   (G8x)
(II) Primary Device is: PCI 01@00:00:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) [drm] nouveau interface version: 0.0.15
(II) Loading sub module "dri"
(II) LoadModule: "dri"
(II) Reloading /usr/lib/xorg/modules/extensions/libdri.so
(II) NOUVEAU(0): Loaded DRI module
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(--) NOUVEAU(0): Chipset: "NVIDIA NV34"
(**) NOUVEAU(0): Depth 24, (--) framebuffer bpp 32
(==) NOUVEAU(0): RGB weight 888
(==) NOUVEAU(0): Default visual is TrueColor
(==) NOUVEAU(0): Using HW cursor
(II) NOUVEAU(0): Output LVDS-1 using monitor section Monitor0
(**) NOUVEAU(0): Option "PreferredMode" "1400x1050"
(II) NOUVEAU(0): Output VGA-1 has no monitor section
(II) NOUVEAU(0): Output TV-1 has no monitor section
(II) NOUVEAU(0): Output DVI-D-1 has no monitor section
(II) NOUVEAU(0): EDID for output LVDS-1
(II) NOUVEAU(0): Not using default mode "640x350" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "320x175" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "640x400" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "320x200" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "720x400" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "360x200" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "640x480" (unknown reason)
(II) NOUVEAU(0): Not using default mode "320x240" (unknown reason)
(II) NOUVEAU(0): Not using default mode "640x480" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "320x240" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "640x480" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "320x240" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "640x480" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "320x240" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "800x600" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "400x300" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "800x600" (unknown reason)
(II) NOUVEAU(0): Not using default mode "400x300" (unknown reason)
(II) NOUVEAU(0): Not using default mode "800x600" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "400x300" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "800x600" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "400x300" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "800x600" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "400x300" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1024x768" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "512x384" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1024x768" (unknown reason)
(II) NOUVEAU(0): Not using default mode "512x384" (unknown reason)
(II) NOUVEAU(0): Not using default mode "1024x768" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "512x384" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1024x768" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "512x384" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1024x768" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "512x384" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1152x864" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "576x432" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1280x960" (unknown reason)
(II) NOUVEAU(0): Not using default mode "640x480" (unknown reason)
(II) NOUVEAU(0): Not using default mode "1280x960" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "640x480" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1280x1024" (unknown reason)
(II) NOUVEAU(0): Not using default mode "640x512" (unknown reason)
(II) NOUVEAU(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "640x512" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "640x512" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1600x1200" (hsync out of range)
(II) NOUVEAU(0): Not using default mode "800x600" (hsync out of range)
(II) NOUVEAU(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "800x600" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "800x600" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "800x600" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "800x600" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) NOUVEAU(0): Not using default mode "896x672" (hsync out of range)
(II) NOUVEAU(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) NOUVEAU(0): Not using default mode "896x672" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) NOUVEAU(0): Not using default mode "928x696" (hsync out of range)
(II) NOUVEAU(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) NOUVEAU(0): Not using default mode "928x696" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) NOUVEAU(0): Not using default mode "960x720" (hsync out of range)
(II) NOUVEAU(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) NOUVEAU(0): Not using default mode "960x720" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "832x624" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "416x312" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1152x864" (unknown reason)
(II) NOUVEAU(0): Not using default mode "576x432" (unknown reason)
(II) NOUVEAU(0): Not using default mode "1152x864" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "576x432" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1152x864" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "576x432" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1152x864" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "576x432" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1152x864" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "576x432" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1152x864" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "576x432" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) NOUVEAU(0): Not using default mode "680x384" (unknown reason)
(II) NOUVEAU(0): Not using default mode "1360x768" (unknown reason)
(II) NOUVEAU(0): Not using default mode "680x384" (unknown reason)
(II) NOUVEAU(0): Not using default mode "1400x1050" (unknown reason)
(II) NOUVEAU(0): Not using default mode "700x525" (unknown reason)
(II) NOUVEAU(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "700x525" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "700x525" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "700x525" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1440x900" (unknown reason)
(II) NOUVEAU(0): Not using default mode "720x450" (unknown reason)
(II) NOUVEAU(0): Not using default mode "1600x1024" (unknown reason)
(II) NOUVEAU(0): Not using default mode "800x512" (unknown reason)
(II) NOUVEAU(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) NOUVEAU(0): Not using default mode "840x525" (unknown reason)
(II) NOUVEAU(0): Not using default mode "1680x1050" (unknown reason)
(II) NOUVEAU(0): Not using default mode "840x525" (unknown reason)
(II) NOUVEAU(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "840x525" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "840x525" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "840x525" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1920x1080" (hsync out of range)
(II) NOUVEAU(0): Not using default mode "960x540" (hsync out of range)
(II) NOUVEAU(0): Not using default mode "1920x1200" (hsync out of range)
(II) NOUVEAU(0): Not using default mode "960x600" (hsync out of range)
(II) NOUVEAU(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) NOUVEAU(0): Not using default mode "960x720" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) NOUVEAU(0): Not using default mode "1024x768" (hsync out of range)
(II) NOUVEAU(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) NOUVEAU(0): Not using default mode "1024x768" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) NOUVEAU(0): Not using default mode "1024x768" (vrefresh out of range)
(II) NOUVEAU(0): Printing probed modes for output LVDS-1
(II) NOUVEAU(0): Modeline "1400x1050"x60.0  108.00  1400 1448 1560 1688  1050 1051 1054 1066 -hsync -vsync (64.0 kHz)
(II) NOUVEAU(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) NOUVEAU(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x60.0   81.75  1152 1216 1336 1520  864 867 871 897 -hsync +vsync (53.8 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
(II) NOUVEAU(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
(II) NOUVEAU(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
(II) NOUVEAU(0): Modeline "720x400"x59.6   22.25  720 744 808 896  400 403 413 417 -hsync +vsync (24.8 kHz)
(II) NOUVEAU(0): Modeline "640x400"x60.0   20.00  640 664 720 800  400 403 409 417 -hsync +vsync (25.0 kHz)
(II) NOUVEAU(0): Modeline "640x350"x59.8   17.50  640 664 720 800  350 353 363 366 -hsync +vsync (21.9 kHz)
(II) NOUVEAU(0): EDID for output VGA-1
(II) NOUVEAU(0): Manufacturer: DEL  Model: 32b0  Serial#: 1161120594
(II) NOUVEAU(0): Year: 2001  Week: 19
(II) NOUVEAU(0): EDID Version: 1.3
(II) NOUVEAU(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) NOUVEAU(0): Sync:  Separate
(II) NOUVEAU(0): Max Image Size [cm]: horiz.: 32  vert.: 24
(II) NOUVEAU(0): Gamma: 2.27
(II) NOUVEAU(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) NOUVEAU(0): First detailed timing is preferred mode
(II) NOUVEAU(0): redX: 0.645 redY: 0.321   greenX: 0.285 greenY: 0.600
(II) NOUVEAU(0): blueX: 0.142 blueY: 0.057   whiteX: 0.283 whiteY: 0.298
(II) NOUVEAU(0): Supported established timings:
(II) NOUVEAU(0): 720x400@70Hz
(II) NOUVEAU(0): 640x480@60Hz
(II) NOUVEAU(0): 640x480@75Hz
(II) NOUVEAU(0): 800x600@75Hz
(II) NOUVEAU(0): 1024x768@75Hz
(II) NOUVEAU(0): 1280x1024@75Hz
(II) NOUVEAU(0): Manufacturer's mask: 0
(II) NOUVEAU(0): Supported standard timings:
(II) NOUVEAU(0): #0: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) NOUVEAU(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) NOUVEAU(0): #2: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) NOUVEAU(0): #3: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) NOUVEAU(0): Supported detailed timing:
(II) NOUVEAU(0): clock: 94.5 MHz   Image Size:  306 x 230 mm
(II) NOUVEAU(0): h_active: 1024  h_sync: 1072  h_sync_end 1168 h_blank_end 1376 h_border: 0
(II) NOUVEAU(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 808 v_border: 0
(II) NOUVEAU(0): Serial No: 688EN15AE5KR
(II) NOUVEAU(0): Monitor name: DELL M781s
(II) NOUVEAU(0): Ranges: V min: 50 V max: 160 Hz, H min: 30 H max: 85 kHz, PixClock max 170 MHz
(II) NOUVEAU(0): EDID (in hex):
(II) NOUVEAU(0): 	00ffffffffffff0010acb032524b3545
(II) NOUVEAU(0): 	130b01030820187fea1269a552499924
(II) NOUVEAU(0): 	0e484ca44300615945593159a9400101
(II) NOUVEAU(0): 	010101010101ea240060410028303060
(II) NOUVEAU(0): 	130032e61000001e000000ff00363838
(II) NOUVEAU(0): 	454e31354145354b520a000000fc0044
(II) NOUVEAU(0): 	454c4c204d373831730a2020000000fd
(II) NOUVEAU(0): 	0032a01e5511000a20202020202000be
(II) NOUVEAU(0): Printing probed modes for output VGA-1
(II) NOUVEAU(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) NOUVEAU(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x85.0   94.50  1024 1072 1072 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) NOUVEAU(0): Modeline "800x600"x85.1   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) NOUVEAU(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NOUVEAU(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) NOUVEAU(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NOUVEAU(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NOUVEAU(0): EDID for output TV-1
(II) NOUVEAU(0): EDID for output DVI-D-1
(II) NOUVEAU(0): Output LVDS-1 connected
(II) NOUVEAU(0): Output VGA-1 connected
(II) NOUVEAU(0): Output TV-1 disconnected
(II) NOUVEAU(0): Output DVI-D-1 disconnected
(II) NOUVEAU(0): Using user preference for initial modes
(II) NOUVEAU(0): Output LVDS-1 using initial mode 1400x1050
(II) NOUVEAU(0): Output VGA-1 using initial mode 1280x1024
(II) NOUVEAU(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
(--) NOUVEAU(0): Virtual size is 3000x1200 (pitch 3008)
(**) NOUVEAU(0):  Driver mode "1400x1050": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) NOUVEAU(0): Modeline "1400x1050"x60.0  108.00  1400 1448 1560 1688  1050 1051 1054 1066 -hsync -vsync (64.0 kHz)
(**) NOUVEAU(0):  Driver mode "1400x1050": 121.8 MHz (scaled from 0.0 MHz), 65.3 kHz, 60.0 Hz
(II) NOUVEAU(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
(**) NOUVEAU(0):  Driver mode "1280x1024": 109.0 MHz (scaled from 0.0 MHz), 63.7 kHz, 59.9 Hz
(II) NOUVEAU(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(**) NOUVEAU(0):  Driver mode "1280x960": 101.2 MHz (scaled from 0.0 MHz), 59.7 kHz, 59.9 Hz
(II) NOUVEAU(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
(**) NOUVEAU(0):  Driver mode "1152x864": 81.8 MHz (scaled from 0.0 MHz), 53.8 kHz, 60.0 Hz
(II) NOUVEAU(0): Modeline "1152x864"x60.0   81.75  1152 1216 1336 1520  864 867 871 897 -hsync +vsync (53.8 kHz)
(**) NOUVEAU(0):  Driver mode "1024x768": 63.5 MHz (scaled from 0.0 MHz), 47.8 kHz, 59.9 Hz
(II) NOUVEAU(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
(**) NOUVEAU(0):  Driver mode "800x600": 38.2 MHz (scaled from 0.0 MHz), 37.4 kHz, 59.9 Hz
(II) NOUVEAU(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
(**) NOUVEAU(0):  Driver mode "640x480": 23.8 MHz (scaled from 0.0 MHz), 29.7 kHz, 59.4 Hz
(II) NOUVEAU(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
(**) NOUVEAU(0):  Driver mode "720x400": 22.2 MHz (scaled from 0.0 MHz), 24.8 kHz, 59.6 Hz
(II) NOUVEAU(0): Modeline "720x400"x59.6   22.25  720 744 808 896  400 403 413 417 -hsync +vsync (24.8 kHz)
(**) NOUVEAU(0):  Driver mode "640x400": 20.0 MHz (scaled from 0.0 MHz), 25.0 kHz, 60.0 Hz
(II) NOUVEAU(0): Modeline "640x400"x60.0   20.00  640 664 720 800  400 403 409 417 -hsync +vsync (25.0 kHz)
(**) NOUVEAU(0):  Driver mode "640x350": 17.5 MHz (scaled from 0.0 MHz), 21.9 kHz, 59.8 Hz
(II) NOUVEAU(0): Modeline "640x350"x59.8   17.50  640 664 720 800  350 353 363 366 -hsync +vsync (21.9 kHz)
(==) NOUVEAU(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "exa"
(II) LoadModule: "exa"
(II) Loading /usr/lib/xorg/modules/libexa.so
(II) Module exa: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.5.0
	ABI class: X.Org Video Driver, version 6.0
(II) Loading sub module "shadowfb"
(II) LoadModule: "shadowfb"
(II) Loading /usr/lib/xorg/modules/libshadowfb.so
(II) Module shadowfb: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(--) Depth 24 pixmap format is 32 bpp
(II) NOUVEAU(0): Opened GPU channel 1
(II) NOUVEAU(0): [DRI2] Setup complete
(II) NOUVEAU(0): GART: 256MiB available
(II) NOUVEAU(0): GART: Allocated 16MiB as a scratch buffer
(II) EXA(0): Driver allocated offscreen pixmaps
(II) EXA(0): Driver registered support for the following operations:
(II)         Solid
(II)         Copy
(II)         Composite (RENDER acceleration)
(II)         UploadToScreen
(II)         DownloadFromScreen
(==) NOUVEAU(0): Backing store disabled
(==) NOUVEAU(0): Silken mouse enabled
(II) NOUVEAU(0): [XvMC] Associated with NV30 texture adapter.
(II) NOUVEAU(0): [XvMC] Extension initialized.
(II) NOUVEAU(0): NVEnterVT is called.
(**) NOUVEAU(0): DPMS enabled
(II) NOUVEAU(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(WW) NOUVEAU(0): Option "monitor-LVDS-0" is not used
(WW) NOUVEAU(0): Option "monitor-VGA-0" is not used
(WW) NOUVEAU(0): Option "PreferredMode" is not used
(--) RandR disabled
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
(II) AIGLX error: dlopen of /usr/lib/dri/nouveau_dri.so failed (/usr/lib/dri/nouveau_dri.so: cannot open shared object file: No such file or directory)
(II) AIGLX: reverting to software rendering
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(II) NOUVEAU(0): Setting screen physical size to 370 x 277
resize called 1400 1050
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event2)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.3.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event2"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_variant" "dvorak"
(**) Option "xkb_options" "lv3:ralt_switch,grp:alts_toggle"
(II) XKB: reuse xkmfile /var/lib/xkb/server-F41CC3D3342BEB7134BAC87BB203F36646C3D80C.xkm
(II) config/udev: Adding input device Video Bus (/dev/input/event5)
(**) Video Bus: Applying InputClass "evdev keyboard catchall"
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event5"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_variant" "dvorak"
(**) Option "xkb_options" "lv3:ralt_switch,grp:alts_toggle"
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_variant" "dvorak"
(**) Option "xkb_options" "lv3:ralt_switch,grp:alts_toggle"
(II) config/udev: Adding input device Lid Switch (/dev/input/event1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_variant" "dvorak"
(**) Option "xkb_options" "lv3:ralt_switch,grp:alts_toggle"
(II) config/udev: Adding input device PS/2 Mouse (/dev/input/event7)
(**) PS/2 Mouse: Applying InputClass "evdev pointer catchall"
(**) PS/2 Mouse: always reports core events
(**) PS/2 Mouse: Device: "/dev/input/event7"
(II) PS/2 Mouse: Found 3 mouse buttons
(II) PS/2 Mouse: Found relative axes
(II) PS/2 Mouse: Found x and y relative axes
(II) PS/2 Mouse: Configuring as mouse
(**) PS/2 Mouse: YAxisMapping: buttons 4 and 5
(**) PS/2 Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "PS/2 Mouse" (type: MOUSE)
(II) PS/2 Mouse: initialized for relative axes.
(II) config/udev: Adding input device PS/2 Mouse (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/event8)
(**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "evdev pointer catchall"
(**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "evdev touchpad catchall"
(**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "touchpad catchall"
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(II) Synaptics touchpad driver version 1.2.2
(**) Option "Device" "/dev/input/event8"
(II) AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023
(II) AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767
(II) AlpsPS/2 ALPS GlidePoint: pressure range 0 - 127
(II) AlpsPS/2 ALPS GlidePoint: finger width range 0 - 0
(II) AlpsPS/2 ALPS GlidePoint: buttons: left right middle
(--) AlpsPS/2 ALPS GlidePoint: touchpad found
(**) AlpsPS/2 ALPS GlidePoint: always reports core events
(II) XINPUT: Adding extended input device "AlpsPS/2 ALPS GlidePoint" (type: TOUCHPAD)
(**) AlpsPS/2 ALPS GlidePoint: (accel) keeping acceleration scheme 1
(**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration profile 0
(**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration factor: 2.000
(**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration threshold: 4
(--) AlpsPS/2 ALPS GlidePoint: touchpad found
(II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/mouse2)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device PC Speaker (/dev/input/event6)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Serial Wacom Tablet (/dev/ttyS0)
(**) Serial Wacom Tablet: Applying InputClass "Wacom serial class"
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.10.5
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(**) Option "Device" "/dev/ttyS0"
(II) Serial Wacom Tablet: type not specified, assuming 'stylus'.
(II) Serial Wacom Tablet: other types will be automatically added.
(**) Serial Wacom Tablet: always reports core events
(II) Serial Wacom Tablet: hotplugging dependent devices.
(**) Option "Device" "/dev/ttyS0"
(**) Serial Wacom Tablet eraser: always reports core events
(II) XINPUT: Adding extended input device "Serial Wacom Tablet eraser" (type: ERASER)
(**) Option "StopBits" "1"
(**) Option "DataBits" "8"
(**) Option "Parity" "None"
(**) Option "Vmin" "1"
(**) Option "Vtime" "10"
(**) Option "FlowControl" "Xoff"
(WW) Serial Wacom Tablet eraser: Waited too long for answer (failed after 3 tries).
(WW) Serial Wacom Tablet eraser: Waited too long for answer (failed after 3 tries).
(II) Serial Wacom Tablet eraser: serial tablet id 0x90.
(--) Serial Wacom Tablet eraser: using pressure threshold of 7 for button 1
(--) Serial Wacom Tablet eraser: Wacom General ISDV4 tablet speed=38400 maxX=24570 maxY=18428 maxZ=127 resX=2540 resY=2540  tilt=disabled
(--) Serial Wacom Tablet eraser: top X=0 top Y=0 bottom X=24570 bottom Y=18428 resol X=2540 resol Y=2540
(II) Serial Wacom Tablet: hotplugging completed.
(II) XINPUT: Adding extended input device "Serial Wacom Tablet" (type: STYLUS)
(--) Serial Wacom Tablet: top X=0 top Y=0 bottom X=24570 bottom Y=18428 resol X=2540 resol Y=2540
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event3)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)
(II) NOUVEAU(0): NVLeaveVT is called.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) NOUVEAU(0): NVEnterVT is called.
(--) AlpsPS/2 ALPS GlidePoint: touchpad found
(**) Option "StopBits" "1"
(**) Option "DataBits" "8"
(**) Option "Parity" "None"
(**) Option "Vmin" "1"
(**) Option "Vtime" "10"
(**) Option "FlowControl" "Xoff"
(WW) Serial Wacom Tablet: Waited too long for answer (failed after 3 tries).
(WW) Serial Wacom Tablet: Waited too long for answer (failed after 3 tries).
(II) Serial Wacom Tablet: serial tablet id 0x90.
(--) Serial Wacom Tablet: Wacom General ISDV4 tablet speed=38400 maxX=24570 maxY=18428 maxZ=127 resX=2540 resY=2540  tilt=disabled
(--) Serial Wacom Tablet: top X=0 top Y=0 bottom X=24570 bottom Y=18428 resol X=2540 resol Y=2540
(--) Serial Wacom Tablet eraser: top X=0 top Y=0 bottom X=24570 bottom Y=18428 resol X=2540 resol Y=2540
(II) Power Button: Device reopened after 1 attempts.
(II) Video Bus: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II) AT Translated Set 2 keyboard: Device reopened after 1 attempts.
(II) PS/2 Mouse: Device reopened after 1 attempts.
(II) Macintosh mouse button emulation: Device reopened after 1 attempts.
resize called 3000 1200

```

First, now that my external monitor is connected, it shows so and returns EDID:
```
...
(II) NOUVEAU(0): EDID for output VGA-1
(II) NOUVEAU(0): Manufacturer: DEL  Model: 32b0  Serial#: 1161120594
(II) NOUVEAU(0): Year: 2001  Week: 19
(II) NOUVEAU(0): EDID Version: 1.3
(II) NOUVEAU(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) NOUVEAU(0): Sync:  Separate
(II) NOUVEAU(0): Max Image Size [cm]: horiz.: 32  vert.: 24
(II) NOUVEAU(0): Gamma: 2.27
(II) NOUVEAU(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) NOUVEAU(0): First detailed timing is preferred mode
(II) NOUVEAU(0): redX: 0.645 redY: 0.321   greenX: 0.285 greenY: 0.600
(II) NOUVEAU(0): blueX: 0.142 blueY: 0.057   whiteX: 0.283 whiteY: 0.298
(II) NOUVEAU(0): Supported established timings:
(II) NOUVEAU(0): 720x400@70Hz
(II) NOUVEAU(0): 640x480@60Hz
(II) NOUVEAU(0): 640x480@75Hz
(II) NOUVEAU(0): 800x600@75Hz
(II) NOUVEAU(0): 1024x768@75Hz
(II) NOUVEAU(0): 1280x1024@75Hz
(II) NOUVEAU(0): Manufacturer's mask: 0
(II) NOUVEAU(0): Supported standard timings:
(II) NOUVEAU(0): #0: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) NOUVEAU(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) NOUVEAU(0): #2: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) NOUVEAU(0): #3: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) NOUVEAU(0): Supported detailed timing:
(II) NOUVEAU(0): clock: 94.5 MHz   Image Size:  306 x 230 mm
(II) NOUVEAU(0): h_active: 1024  h_sync: 1072  h_sync_end 1168 h_blank_end 1376 h_border: 0
(II) NOUVEAU(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 808 v_border: 0
(II) NOUVEAU(0): Serial No: 688EN15AE5KR
(II) NOUVEAU(0): Monitor name: DELL M781s
(II) NOUVEAU(0): Ranges: V min: 50 V max: 160 Hz, H min: 30 H max: 85 kHz, PixClock max 170 MHz
(II) NOUVEAU(0): EDID (in hex):
(II) NOUVEAU(0): 	00ffffffffffff0010acb032524b3545
(II) NOUVEAU(0): 	130b01030820187fea1269a552499924
(II) NOUVEAU(0): 	0e484ca44300615945593159a9400101
(II) NOUVEAU(0): 	010101010101ea240060410028303060
(II) NOUVEAU(0): 	130032e61000001e000000ff00363838
(II) NOUVEAU(0): 	454e31354145354b520a000000fc0044
(II) NOUVEAU(0): 	454c4c204d373831730a2020000000fd
(II) NOUVEAU(0): 	0032a01e5511000a20202020202000be
(II) NOUVEAU(0): Printing probed modes for output VGA-1
(II) NOUVEAU(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) NOUVEAU(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x85.0   94.50  1024 1072 1072 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) NOUVEAU(0): Modeline "800x600"x85.1   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) NOUVEAU(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NOUVEAU(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) NOUVEAU(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NOUVEAU(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
...
(II) NOUVEAU(0): Output VGA-1 connected
...

```

but there are a couple of interesting warnings, looks like I'm using the wrong names in my config: LVDS-1 instead of LVDS-0, etc
```
(WW) NOUVEAU(0): Option "monitor-LVDS-0" is not used
(WW) NOUVEAU(0): Option "monitor-VGA-0" is not used
(WW) NOUVEAU(0): Option "PreferredMode" is not used
```

That's right, you can't just copy and paste usually! Unfortunately these options 'monitor-...' are not listed in the nouveau manpage, but as usual some googling sorts that out:
from: [http://intellinuxgraphics.org/dualhead.html](http://intellinuxgraphics.org/dualhead.html), with the hopefully correct values for my machine.
```

        # Using the name of the output defined by the video driver plus the identifier of a
        #     monitor section, one associates a monitor section with an output by adding an
        #     option to the Device section in the following format:
        #     Option "Monitor-outputname" "monitor ID"
	Option      "monitor-LVDS-1" "Monitor0"
	Option      "monitor-VGA-1" "Monitor1"

```

Need to restart X to try this!

Note: The gnome display configurator at least detects my external monitor before even restarting X, but there is no output to the display even though it seems like it's configured and X can request EDID. Some communication is not working maybe?

---

### Post by anjames on 2010-08-31
Restarting X caused me some problems: my console froze so I had to hard shutdown (ow), and it came back a bit less than gracefully. But I'm not down and out yet. ;-)

When I rebooted with the monitor plugged in, the external monitor was my primary display and even showed the bios password request, only my LCD wasn't working then.

The xorg.conf line 'Virtual 3000 1200' caused me problems: gdm wasn't displaying on my primary display anymore and the external monitor wasn't displaying either so I couldn't log in.

So strangely: I can get the external monitor working if I have it plugged in during bootup, but then my laptop display doesn't work; the laptop display works fine normally, but external monitor doesn't actually display anything.

I recall some issue with having to turn on the VGA out using toshset...
```
# toshset -video
HCI error: argument required
Video out: internal: LCD

# toshset -video both
HciFeature::query: received an unexpected response for feature Video out: 385

```

So it looks like either toshset doesn't do video anymore in ubuntu (as recently as karmic anyway):
[http://box354.bluehost.com/pipermail/toshset_schwieters.org/2009-November/000001.html](http://box354.bluehost.com/pipermail/toshset_schwieters.org/2009-November/000001.html)

or I might have to run it without X running:
[http://www.jeremythompson.uklinux.net/RH8-0/Display.html](http://www.jeremythompson.uklinux.net/RH8-0/Display.html)

Hopefully I'm not lost now in the moderately working toshiba_acpi/toshset or entirely undocumented tlsup module problems. Goodbye browser for a little while...

---

### Post by anjames on 2010-08-31
Well, I stopped X and got the same error as above from toshset in the console.

The toshset source from sourceforge describes the situation when this error is reported, but I'm not quite prepared to enter those depths just yet...

[http://toshset.sourcearchive.com/documentation/1.72-2/toshset_8cc-source.html](http://toshset.sourcearchive.com/documentation/1.72-2/toshset_8cc-source.html)
[http://toshset.sourcearchive.com/documentation/1.72-2/hci_8c-source.html](http://toshset.sourcearchive.com/documentation/1.72-2/hci_8c-source.html)

Maybe tomorrow.

---

### Post by anjames on 2010-09-07
Feeling refreshed after the labor day weekend I tried just plugging in a monitor on bootup to see how it would work. I had reverted to nv and the 3.6.31 kernel since I could at least hibernate occasionally that way, but this morning I wasn't paying attention and it booted into the default 3.6.32 kernel since I hadn't changed the grub default kernel.

Interestingly enough, the external monitor is working! But my laptop lcd is dark, so I tried using toshset to turn it on, and voila: new error:

```
# toshset -v -lcd 1

SciFeature:action: error setting lcd brightness
	SciSet returned: FAILURE
lcd brightness: super-bright

```

It seems like toshset is getting some consistent replies from the toshiba_acpi module which its not expecting, but it wish it would dump some more debug info! The messages from dmesg don't seem too relevant, but I'll post them anyway for thoroughness:

```
# dmesg | grep toshiba_acpi
[   44.614647] toshiba_acpi: Toshiba Laptop ACPI Extras version 0.19-dev-acpikeys
[   44.614652] toshiba_acpi:     HCI method: \_SB_.VALZ.GHCI
[   44.615652] toshiba_acpi: Toshiba hotkeys are sent as ACPI events
[   44.615656] toshiba_acpi: ktoshkeyd will check 2 times per second
[   44.761718] toshiba_acpi: Dropped 15 keys from the queue on startup

```

After all of this work trying to get things working on my toshiba laptops (2 of them now over the last 10 years!), the bottom line seems to be that a couple of non-standard modifications that toshiba has made to their BIOS, ACPI, and various hardware elements have made their compatibility with linux 'sucky'. Don't get me wrong I can boot ubuntu and it works OK for most things, but suspend isn't working for some reason (again, maybe that's not toshiba's fault!), the external monitor won't work, the SD card reader won't work, and I've had to do some backflips to make their non-standard EDID interface between the monitor and graphics card work. Probably these things would just work if we had some clues, like some documentation of their modified acpi implementation, how the monitor/graphics card EDID works, and the SD card reader, but they haven't been forthcoming about that so far (maybe that will change? this IS 5yr old hardware!). 

Fortunately there is a hand-me-down dual core Dell with my name on it, which hopefully I'll have some better luck on!

PS. The fact that I had not ONE SINGLE reply from another user makes me think that I may be alone in this problem, but that's probably just because I'm the only one working on a 5yr old laptop and maybe everyone else has upgraded to something newer?

Alternatively, maybe this is the world trying to tell me to shut up and finish my thesis already... so I suppose I'll chop this monologue short and get to work. 

Party on ubuntu.

[FONT="Courier New"]_________________________________________________________________
Alex James     [email]anjames@cer.ucsd.edu[/email]   [http://cer.ucsd.edu/~james/](http://cer.ucsd.edu/~james/)
Center for Energy Research                   cell:+1(949)412-7220
University of California, San Diego           fax:+1(858)534-7716
EBU2 room 373      9500 Gilman Drive, La Jolla, CA 92093-0417 USA
_________________________________________________________________[/FONT]

---

### Post by tpinkfloyd on 2012-01-20
Has anyone solved this issue or is it still in the works? Just wondering if it would just be easier to turn my suspend/hibernate off on the Portege M200 or not

---

