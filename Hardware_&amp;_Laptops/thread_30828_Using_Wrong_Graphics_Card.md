---
title: "Using Wrong Graphics Card"
date: 2005-04-30
forum: Hardware &amp; Laptops
---

### Post by Briggzee on 2005-04-30
Hi there.

System:
AMD64 3500
Gigabyte Nforce4 Mother Board.
SLI GeForce 6800 Ultra's  x2

I've just installed Kubuntu 64-Bit and when KDE Starts up, the Screen goes black with a blinking cursor in the Top Left of the screen.

When I plug my monitor into my second graphics card, Hey presto! Its the log in screen for KDE. Previously when I was using Slackware and KDE it didnt seem to have the same problem.

Any suggestions on how I might fix this?

---

### Post by DJ_Max on 2005-04-30
[QUOTE=Briggzee]Hi there.

System:
AMD64 3500
Gigabyte Nforce4 Mother Board.
SLI GeForce 6800 Ultra's  x2

I've just installed Kubuntu 64-Bit and when KDE Starts up, the Screen goes black with a blinking cursor in the Top Left of the screen.

When I plug my monitor into my second graphics card, Hey presto! Its the log in screen for KDE. Previously when I was using Slackware and KDE it didnt seem to have the same problem.

Any suggestions on how I might fix this?[/QUOTE]
 During the install what graphics card did you choose?

---

### Post by Briggzee on 2005-04-30
I dont recall the install ever asking what Graphics card to use.

---

### Post by DJ_Max on 2005-04-30
[QUOTE=Briggzee]I dont recall the install ever asking what Graphics card to use.[/QUOTE]
 I may be thinking of a wrond distro install. :oops: But I remember having a chance to look at an overview f detected hardware.

Open up your Xorg config file, and tell what drivers are loaded /etc/X11/xorg.conf

---

### Post by Briggzee on 2005-04-30
Section "Files"
 FontPath "unix/:7100"   # local font server
 # if the local font server has problems, we can fall back on these
 FontPath "/usr/lib/X11/fonts/misc"
 FontPath "/usr/lib/X11/fonts/cyrillic"
 FontPath "/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
 FontPath "/usr/lib/X11/fonts/Type1"
 FontPath "/usr/lib/X11/fonts/CID"
 FontPath "/usr/lib/X11/fonts/100dpi"
 FontPath "/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
 FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
 FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
 Identifier "Configured Mouse"
 Driver  "mouse"
 Option  "CorePointer"
 Option  "Device"  "/dev/input/mice"
 Option  "Protocol"  "ImPS/2"
 Option  "Emulate3Buttons" "true"
 Option  "ZAxisMapping"  "4 5"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV40 [GeForce 6800 Ultra/GeForce 6800 GT]"
	Driver		"nv"
	BusID		"PCI:4:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-65
	VertRefresh	50-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV40 [GeForce 6800 Ultra/GeForce 6800 GT]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
  Depth  4
  Modes  "1280x1024" "1024x768" "800x600" "640x480"
 EndSubSection
 SubSection "Display"
  Depth  8
  Modes  "1280x1024" "1024x768" "800x600" "640x480"
 EndSubSection
 SubSection "Display"
  Depth  15
  Modes  "1280x1024" "1024x768" "800x600" "640x480"
 EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
 SubSection "Display"
  Depth  24
  Modes  "1280x1024" "1024x768" "800x600" "640x480"
 EndSubSection
EndSection

Section "ServerLayout"
 Identifier "Default Layout"
 Screen  "Default Screen"
 InputDevice "Generic Keyboard"
 InputDevice "Configured Mouse"
EndSection

Section "DRI"
 Mode 0666
EndSection

---

### Post by DJ_Max on 2005-04-30
[QUOTE=Briggzee]Section "Files"
 FontPath "unix/:7100"   # local font server
 # if the local font server has problems, we can fall back on these
 FontPath "/usr/lib/X11/fonts/misc"
 FontPath "/usr/lib/X11/fonts/cyrillic"
 FontPath "/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
 FontPath "/usr/lib/X11/fonts/Type1"
 FontPath "/usr/lib/X11/fonts/CID"
 FontPath "/usr/lib/X11/fonts/100dpi"
 FontPath "/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
 FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
 FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
 Identifier "Configured Mouse"
 Driver  "mouse"
 Option  "CorePointer"
 Option  "Device"  "/dev/input/mice"
 Option  "Protocol"  "ImPS/2"
 Option  "Emulate3Buttons" "true"
 Option  "ZAxisMapping"  "4 5"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV40 [GeForce 6800 Ultra/GeForce 6800 GT]"
	Driver		"nv"
	BusID		"PCI:4:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-65
	VertRefresh	50-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV40 [GeForce 6800 Ultra/GeForce 6800 GT]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
  Depth  4
  Modes  "1280x1024" "1024x768" "800x600" "640x480"
 EndSubSection
 SubSection "Display"
  Depth  8
  Modes  "1280x1024" "1024x768" "800x600" "640x480"
 EndSubSection
 SubSection "Display"
  Depth  15
  Modes  "1280x1024" "1024x768" "800x600" "640x480"
 EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
 SubSection "Display"
  Depth  24
  Modes  "1280x1024" "1024x768" "800x600" "640x480"
 EndSubSection
EndSection

Section "ServerLayout"
 Identifier "Default Layout"
 Screen  "Default Screen"
 InputDevice "Generic Keyboard"
 InputDevice "Configured Mouse"
EndSection

Section "DRI"
 Mode 0666
EndSection[/QUOTE]
 ahh, I didn't see that fact that you have two SLI GeForce 6800 Ultra, is that correct? If so, is there a problem with using the second one? There are a few threads about having two graphic cards

---

### Post by Briggzee on 2005-04-30
That's right. Two of them...  Not exactly the most Linux friendly of hardware. Nforc4 and Dual SLI cards...

As far as I'm aware there's no problem with the second one, its just that I have to use it to display anything other than the console. I'd like ot be able to use the first card instead of having to switch the monitor plug around.

Section "Device"
 Identifier "NVIDIA Corporation NV40 [GeForce 6800 Ultra/GeForce 6800 GT]"
 Driver "nv"
 BusID "PCI:4:0:0"
 EndSection

Would adjust the BusID change anything? Maybe try and get it to use the other card?

---

### Post by DJ_Max on 2005-04-30
Yeah, the bus id is important, so changing it would yeild some results.

---

### Post by Briggzee on 2005-04-30
How would one find the BusID for the other card? Assuming its worth trying.

---

### Post by DJ_Max on 2005-04-30
[QUOTE=Briggzee]How would one find the BusID for the other card? Assuming its worth trying.[/QUOTE]
 Try looking in your /proc/pci file

---

### Post by Briggzee on 2005-04-30
[QUOTE=DJ_Max]Try looking in your /proc/pci file[/QUOTE]
 I checked it, and I cant see anything that might suggest the BusID for the other card.
Here's the results;

Perhaps you may spot something I didnt.
========================

PCI devices found:
  Bus  0, device   0, function  0:
    Memory controller: PCI device 10de:005e (nVidia Corporation) (rev 163).
  Bus  0, device   1, function  0:
    ISA bridge: PCI device 10de:0050 (nVidia Corporation) (rev 163).
  Bus  0, device   1, function  1:
    SMBus: PCI device 10de:0052 (nVidia Corporation) (rev 162).
      IRQ 11.
      Master Capable.  No bursts.  Min Gnt=3.Max Lat=1.
      I/O at 0xe000 [0xe01f].
      I/O at 0x1c00 [0x1c3f].
      I/O at 0x1c40 [0x1c7f].
  Bus  0, device   2, function  0:
    USB Controller: PCI device 10de:005a (nVidia Corporation) (rev 162).
      IRQ 23.
      Master Capable.  No bursts.  Min Gnt=3.Max Lat=1.
      Non-prefetchable 32 bit memory at 0xf8103000 [0xf8103fff].
  Bus  0, device   2, function  1:
    USB Controller: PCI device 10de:005b (nVidia Corporation) (rev 163).
      IRQ 22.
      Master Capable.  No bursts.  Min Gnt=3.Max Lat=1.
      Non-prefetchable 32 bit memory at 0xf8100000 [0xf81000ff].
  Bus  0, device   6, function  0:
    IDE interface: PCI device 10de:0053 (nVidia Corporation) (rev 162).
      Master Capable.  No bursts.  Min Gnt=3.Max Lat=1.
      I/O at 0xf000 [0xf00f].
  Bus  0, device   7, function  0:
    IDE interface: PCI device 10de:0054 (nVidia Corporation) (rev 163).
      IRQ 21.
      Master Capable.  No bursts.  Min Gnt=3.Max Lat=1.
      I/O at 0x9f0 [0x9f7].
      I/O at 0xbf0 [0xbf3].
      I/O at 0x970 [0x977].
      I/O at 0xb70 [0xb73].
      I/O at 0xdc00 [0xdc0f].
      Non-prefetchable 32 bit memory at 0xf8102000 [0xf8102fff].
  Bus  0, device   9, function  0:
    PCI bridge: PCI device 10de:005c (nVidia Corporation) (rev 162).
      Master Capable.  No bursts.  Min Gnt=2.Max Lat=2.
  Bus  0, device  10, function  0:
    Bridge: PCI device 10de:0057 (nVidia Corporation) (rev 163).
      IRQ 20.
      Master Capable.  No bursts.  Min Gnt=1.Max Lat=20.
      Non-prefetchable 32 bit memory at 0xf8104000 [0xf8104fff].
      I/O at 0xe400 [0xe407].
  Bus  0, device  11, function  0:
    PCI bridge: PCI device 10de:005d (nVidia Corporation) (rev 163).
      Master Capable.  No bursts.  Min Gnt=2.
  Bus  0, device  12, function  0:
    PCI bridge: PCI device 10de:005d (nVidia Corporation) (rev 163).
      Master Capable.  No bursts.  Min Gnt=2.
  Bus  0, device  13, function  0:
    PCI bridge: PCI device 10de:005d (nVidia Corporation) (rev 163).
      Master Capable.  No bursts.  Min Gnt=10.
  Bus  0, device  14, function  0:
    PCI bridge: PCI device 10de:005d (nVidia Corporation) (rev 163).
      Master Capable.  No bursts.  Min Gnt=2.
  Bus  0, device  24, function  0:
    Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge (rev 0).
  Bus  0, device  24, function  1:
    Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge (rev 0).
  Bus  0, device  24, function  2:
    Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge (rev 0).
  Bus  0, device  24, function  3:
    Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge (rev 0).
  Bus  1, device   8, function  0:
    Multimedia audio controller: Creative Labs SB Audigy (rev 4).
      IRQ 16.
      Master Capable.  Latency=32.  Min Gnt=2.Max Lat=20.
      I/O at 0xa000 [0xa03f].
  Bus  1, device   8, function  1:
    Input device controller: Creative Labs SB Audigy MIDI/Game port (rev 4).
      Master Capable.  Latency=32.
      I/O at 0xa400 [0xa407].
  Bus  1, device   8, function  2:
    FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 4).
      IRQ 17.
      Master Capable.  Latency=32.  Min Gnt=2.Max Lat=4.
      Non-prefetchable 32 bit memory at 0xf8009000 [0xf80097ff].
      Non-prefetchable 32 bit memory at 0xf8000000 [0xf8003fff].
  Bus  1, device  10, function  0:
    FireWire (IEEE 1394): Texas Instruments TSB82AA2 IEEE-1394b Link Layer Contr
oller (rev 1).
      IRQ 18.
      Master Capable.  Latency=32.  Min Gnt=3.Max Lat=4.
      Non-prefetchable 32 bit memory at 0xf8008000 [0xf80087ff].
      Non-prefetchable 32 bit memory at 0xf8004000 [0xf8007fff].
  Bus  2, device   0, function  0:
    Ethernet controller: PCI device 11ab:4362 (Marvell Technology Group Ltd.) (r                                    ev 25).
      IRQ 17.
      Non-prefetchable 64 bit memory at 0xf1000000 [0xf1003fff].
      I/O at 0xb000 [0xb0ff].
  Bus  4, device   0, function  0:
    VGA compatible controller: PCI device 10de:00f9 (nVidia Corporation) (rev 16                                    2).
      IRQ 5.
      Non-prefetchable 32 bit memory at 0xf5000000 [0xf5ffffff].
      Prefetchable 32 bit memory at 0xd0000000 [0xdfffffff].
      Non-prefetchable 32 bit memory at 0xf6000000 [0xf6ffffff].
  Bus  5, device   0, function  0:
    VGA compatible controller: PCI device 10de:00f9 (nVidia Corporation) (rev 16                                    2).
      IRQ 12.
      Non-prefetchable 32 bit memory at 0xf2000000 [0xf2ffffff].
      Prefetchable 32 bit memory at 0xe0000000 [0xefffffff].
      Non-prefetchable 32 bit memory at 0xf3000000 [0xf3ffffff].
======================================

---

### Post by Briggzee on 2005-04-30
Hehe...
I think I found it after I posted...

Bus 5, device 0, function 0:
 VGA compatible controller: PCI device 10de:00f9 (nVidia Corporation) (rev 16 2).
 IRQ 12.

AND 

Bus 4, device 0, function 0:
 VGA compatible controller: PCI device 10de:00f9 (nVidia Corporation) (rev 16 2).
 IRQ 5.

---

### Post by Briggzee on 2005-04-30
Great Stuff!  \\:D/ 
It loaded up on the correct Graphics Card this time.

Except I've found my USB Mouse no longer works.
Tested PS2 Mouse. Works fine.

I a guessing its a problem with the xorg.conf file again.
Any suggestions?

---

