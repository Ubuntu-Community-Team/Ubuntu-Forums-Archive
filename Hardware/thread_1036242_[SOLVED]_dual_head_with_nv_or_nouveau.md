---
title: "[SOLVED] dual head with nv or nouveau?"
date: 2009-01-10
forum: Hardware
---

### Post by CHaoSlayeR on 2009-01-10
Hi there,

I've recently thrown those crappy nvidia binary driver to the trash. This is because using my favourite applications such as thunderbird or firefox are all performing very bad. The worst performance I got in thunderbird requiring between 1 and 4 seconds to just select a mail entry in the list.

So I'm now using the nv driver which brings me back very good desktop performance. XV is also performing well. The only problem I have is to get the external monitor attached to this Dell Inspiron 8600 working again. With nvidia twinview it worked as expected and as I heard that nv implements xrandr 1.2 I thought it must be able.

The second display just showed up correctly in the Xorg.0.log but with xrandr it just isn't seen:

```

Screen 0: minimum 640 x 480, current 1280 x 800, maximum 1280 x 800
default connected 1280x800+0+0 0mm x 0mm
   1280x800       60.0*
   1024x768       60.0
   800x600        60.0
   640x480        60.0

```

For the reference here are my machine specs:
[LIST]
[*]Dell Inspiron 8600 Notebook
[*]nVidia Geforce FX 5200 GO 64M
[*]1 GB RAM
[*]Ubuntu 8.10 Intrepid Ibex (fresh install, always up-to-date with repos)
[/LIST]

Thanx in advance,

C]-[aoZ

---

### Post by CHaoSlayeR on 2009-01-11
Funny things are happening with the nv driver.

I wondered myself why the DPI settings are changed and the command xdpyinfo gives me the following output:
```
[...]
screen #0:
  dimensions:    1280x800 pixels (401x303 millimeters)
  resolution:    81x67 dots per inch
[...]
```

The driver somehow *merges* the dimensions of the external CRT monitor with the resolution of the internal LCD display.

Funny but not what it's supposed to be.

Can someone help with this?

C]-[aoZ

---

### Post by CHaoSlayeR on 2009-01-11
Well, after struggling a bit I finally got dual head working with the rather "unsupported" **nouveau** driver. It works just like expected and configuring the xorg.conf for that is just straight forward:
```
Section "ServerLayout"
	Identifier     "Layout0"
	Screen      0  "primary screen" 0 0
EndSection

Section "Device"
	Identifier     "nVidia GeForce FX 5200 GO 64M"
	VendorName     "NVIDIA Corporation"
	BoardName      "GeForce FX Go5200"
	BusID          "PCI:1:0:0"
	Driver         "nouveau"
	Option         "monitor-LVDS-0" "primary"
	Option         "monitor-VGA-0" "secondary"
EndSection

Section "Monitor"
	Identifier     "primary"
	VendorName     "Dell"
	ModelName      "LGP"
	HorizSync       30.0 - 75.0
	VertRefresh     60.0
#	DisplaySize     331 206
	Option         "Position" "1600 400"
	Option         "PreferredMode" "1280x800"
EndSection

Section "Monitor"
	Identifier     "secondary"
	VendorName     "NEC"
	ModelName      "Multisync FE1250+"
	HorizSync       30.0 - 110.0
	VertRefresh     50.0 - 160.0
#	DisplaySize     401 303
	Option         "PreferredMode" "1600x1200"
	Option         "LeftOf" "primary"
EndSection

Section "Screen"
	Identifier     "primary screen"
	Device         "nVidia GeForce FX 5200 GO 64M"
	Monitor        "primary"
	DefaultDepth	24
	SubSection "Display"
		Depth       24
		Virtual    2880 1200
	EndSubSection
EndSection
```

There are still some glitches and small improvements like XV and of course you get no 3D acceleration unless you build from source (I didn't and I don't need it) but in the end at least I can now enjoy a decent KDE4 performance on my old Geforce FX 5200 GO. So I'm happy again :)

For the reference and for comparison to others that want to try this driver too here are some outputs.

xrandr:
```
Screen 0: minimum 320 x 200, current 2880 x 1200, maximum 2880 x 1200                             
VGA-0 connected 1600x1200+0+0 (normal left inverted right x axis y axis) 396mm x 297mm            
   1600x1200      85.0*+   75.0     75.0     70.0     65.0     60.0
   1680x1050      84.9     74.9     69.9     60.0
   1600x1024      60.2
   1400x1050      85.0     74.8     70.0     60.0
   1280x1024      85.0     85.0     75.0     60.0
   1440x900       59.9
   1280x960       85.0     85.0     60.0
   1360x768       59.8
   1152x864      100.0     85.1     85.0     75.0     75.0     75.0     70.0     60.0
   1024x768      120.1     85.0     85.0     75.1     75.0     70.1     60.0     43.5
   960x720       120.0
   928x696       120.1
   896x672       150.1    120.0
   960x600       120.0
   832x624        74.6
   960x540       120.0
   800x600       170.0    150.0    140.0    130.0    120.0     85.0     85.1     72.2     75.0     60.3     56.2
   840x525       170.0    149.9    139.8    120.0    119.8
   800x512       120.3
   700x525       170.2    149.5    140.1    120.0
   640x512       170.0    150.0    120.0
   720x450       119.8
   640x480       170.2    120.0     85.0     75.0     72.8     72.8     75.0     66.7     60.0     59.9
   720x400        87.8     85.0     70.1
   680x384       119.6    119.9
   640x400        85.1
   576x432       200.2    170.3    170.2    150.0    150.0    140.0    120.1
   640x350        85.1
   512x384       170.0    150.1    140.1    120.0     87.1
   416x312       149.3
   400x300       170.5    144.4    150.2    120.6    112.7
   320x240       170.4    145.6    150.0    120.1
   360x200       170.1
   320x200       170.5
   320x175       170.5
LVDS-0 connected 1280x800+1600+400 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       60.1*+
   1024x768       60.0
   800x600        60.3
   640x480        59.9
DVI-D-0 disconnected
```

ddcprobe:
```
vbe: VESA 3.0 detected.
oem: NVIDIA
vendor: NVIDIA Corporation
product: NV34 Board - p136nz Chip Rev
memory: 65536kb
mode: 640x400x256
mode: 640x480x256
mode: 800x600x16
mode: 800x600x256
mode: 1024x768x16
mode: 1024x768x256
mode: 320x200x64k
mode: 320x200x16m
mode: 640x480x64k
mode: 640x480x16m
mode: 800x600x64k
mode: 800x600x16m
mode: 1024x768x64k
mode: 1024x768x16m
edid:
edid: 1 3
id: 61b6
eisa: NEC61b6
serial: 0000304f
manufacture: 40 2001
input: composite sync, sync on green, analog signal.
screensize: 40 30
gamma: 2.200000
dpms: RGB, active off, suspend, standby
timing: 720x400@70 Hz (VGA 640x400, IBM)
timing: 720x400@88 Hz (XGA2)
timing: 640x480@60 Hz (VGA)
timing: 640x480@67 Hz (Mac II, Apple)
timing: 640x480@72 Hz (VESA)
timing: 640x480@75 Hz (VESA)
timing: 800x600@56 Hz (VESA)
timing: 800x600@60 Hz (VESA)
timing: 800x600@72 Hz (VESA)
timing: 800x600@75 Hz (VESA)
timing: 832x624@75 Hz (Mac II)
timing: 1024x768@87 Hz Interlaced (8514A)
timing: 1024x768@60 Hz (VESA)
timing: 1024x768@70 Hz (VESA)
timing: 1024x768@75 Hz (VESA)
timing: 1280x1024@75 (VESA)
ctiming: 800x600@85
ctiming: 1024x768@85
ctiming: 1152x864@75
ctiming: 1280x960@85
ctiming: 1280x1024@85
ctiming: 1600x1200@75
ctiming: 1792x1344@75
ctiming: 1920x1440@72
dtiming: 1600x1200@111
monitorrange: 30-110, 50-160
monitorname: NEC FE1250+
monitorserial: 110112367
```

xdpyinfo:
```
name of display:    :0.0
version number:    11.0
vendor string:    The X.Org Foundation
vendor release number:    10502000
X.Org version: 1.5.2
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
focus:  window 0x2400001, revert to PointerRoot
number of extensions:    31
    BIG-REQUESTS
    DAMAGE
    DOUBLE-BUFFER
    DPMS
    Extended-Visual-Information
    GLX
    MIT-SCREEN-SAVER
    MIT-SHM
    MIT-SUNDRY-NONSTANDARD
    RANDR
    RECORD
    RENDER
    SECURITY
    SGI-GLX
    SHAPE
    SYNC
    TOG-CUP
    X-Resource
    XC-APPGROUP
    XC-MISC
    XFIXES
    XFree86-DGA
    XFree86-DRI
    XFree86-Misc
    XFree86-VidModeExtension
    XINERAMA
    XInputExtension
    XKEYBOARD
    XTEST
    XVideo
    XVideo-MotionCompensation
default screen number:    0
number of screens:    1

screen #0:
  dimensions:    2880x1200 pixels (744x310 millimeters)
  resolution:    98x98 dots per inch
  depths (7):    24, 1, 4, 8, 15, 16, 32
  root window id:    0x124
  depth of root window:    24 planes
  number of colormaps:    minimum 1, maximum 1
  default colormap:    0x20
  default number of colormap cells:    256
  preallocated pixels:    black 0, white 16777215
  options:    backing-store NO, save-unders NO
  largest cursor:    64x64
  current input event mask:    0xfac031
    KeyPressMask             EnterWindowMask          LeaveWindowMask
    KeymapStateMask          ExposureMask             StructureNotifyMask
    SubstructureNotifyMask   SubstructureRedirectMask FocusChangeMask
    PropertyChangeMask       ColormapChangeMask
  number of visuals:    2
  default visual id:  0x21
  visual:
    visual id:    0x21
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x22
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
```

part of lspci -vvnn:
```
01:00.0 VGA compatible controller [0300]: nVidia Corporation NV34M [GeForce FX Go5200 64M] [10de:0324] (rev a1)
        Subsystem: Dell Device [1028:019c]
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop+ ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 32 (1250ns min, 250ns max)
        Interrupt: pin A routed to IRQ 11
        Region 0: Memory at fc000000 (32-bit, non-prefetchable) [size=16M]
        Region 1: Memory at d0000000 (32-bit, prefetchable) [size=256M]
        Expansion ROM at fd000000 [disabled] [size=128K]
        Capabilities: [60] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [44] AGP version 3.0
                Status: RQ=32 Iso- ArqSz=0 Cal=0 SBA+ ITACoh- GART64- HTrans- 64bit- FW+ AGP3- Rate=x1,x2,x4
                Command: RQ=32 ArqSz=0 Cal=0 SBA+ AGP+ GART64- 64bit- FW+ Rate=x4
        Kernel driver in use: nouveau
        Kernel modules: nvidiafb
```

There are some errors and warnings in the Xor.0.log but it does what it should.

C]-[aoZ

---

### Post by anjames on 2010-08-30
I'll have to try this... out of curiosity, what type of machine are you using and will it hibernate with uswsusp? 

Tracking my progress in this thread:
[http://ubuntuforums.org/showthread.php?t=1565093](http://ubuntuforums.org/showthread.php?t=1565093)

---

### Post by CHaoSlayeR on 2010-09-01
Hi anjames,

The machine was a Pentium M 1.4 GHz with 1 GB RAM. I didn't try hibernate at that time and I didn't care as it was running 24x7. But apparently I don't have it anymore so I can't test that on my side.

Sorry,

C]-[aoZ

---

