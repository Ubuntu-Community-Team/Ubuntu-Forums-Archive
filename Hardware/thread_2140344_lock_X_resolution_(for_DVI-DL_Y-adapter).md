---
title: "lock X resolution (for DVI-DL Y-adapter)"
date: 2013-04-29
forum: Hardware
---

### Post by iaw4 on 2013-04-29
right now, 12.10.  soon 13.04.


I use a DVI Dual-Link Y adapter to mirror a 2560x1600 display.  one monitor is an HP LP3065, the other is a Dell 3008wfp. It works quite well most of the time.

unfortunately, at bootup time, only one of the two can be connected.  and every once in a while, after the computer has slept and is re-awakening, it does not.  presumably, the video card ([Radeon HD 5400/6300 Series) is querying the monitor for its resolution and gets the two monitors' information back in garbled form.

so, I would like to take the currently running resolution and lock it.  I believe that /var/log/Xorg.0.log still contains the correct log, and I am getting

```
[ 21709.366] (II) fglrx(0): Printing DDC gathered Modelines:
[ 21709.366] (II) fglrx(0): Modeline "2560x1600"x0.0  268.50  2560 2608 2640 2720  1600 1603 1609 1646 +hsync -vsync (98.7 kHz eP)

```

I am contemplating just sticking this into my /etc/X11/xorg.conf:

```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Modeline    "2560x1600 60.0"  268.50  2560 2608 2640 2720  1600 1603 1609 1646 +hsync -vsync
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes "2560x1600"
	EndSubSection
EndSection

```

is this the right way to do this?  any other suggestions?

---

### Post by ivo-welch on 2013-11-01
the following seems to work:



> ## goes into /usr/share/X11/xorg.conf.d/10-monitor.conf


Section "Monitor"
  Identifier "Monitor0"
  Modeline "2560x1600"   268.00   2560 2608 2640 2720   1600 1603 1609 1646 +hsync +vsync
EndSection


Section "Screen"
  Identifier "Screen0"
  Device "DVI-I-2"
  Option "ModeValidation" "AllowNon60hzmodesDFPModes, NoEDIDDFPMaxSizeCheck, NoVertRefreshCheck, NoHorizSyncCh
eck, NoDFPNativeResolutionCheck, NoMaxSizeCheck, NoMaxPClkCheck, AllowNonEdidModes, NoEdidMaxPClkCheck"
  Monitor "Monitor0"
  DefaultDepth 24
  SubSection "Display"
    Depth 24
    Modes "2560x1600"
  EndSubSection
EndSection




---

