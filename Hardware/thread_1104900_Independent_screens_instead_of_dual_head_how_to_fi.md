---
title: "Independent screens instead of dual head: how to fix?"
date: 2009-03-24
forum: Hardware
---

### Post by puccio on 2009-03-24
Hi,

I would like to have a dual head, with the external monitor screen on the right of my laptop screen, on which I have an ATI X1400 using the **fglrx** driver.

I did:
(1)
sudo dpkg-reconfigure -phigh xserver-xorg

to start from an empty xorg.conf file. In the result almost empty file I specified Driver "fglrx" in the Device section.

(2)
sudo aticonfig --initial=dual-head --screen-layout=right


The problem is that although I can pass from my laptop screen to the monitor screen with the mouse (moving it on the *right*, as expected..), I can't drag application windows!!  

Even more, on the right screen (the monitor) I have again the Gnome application bar on the top (which is strange, I would have expected to have it only on the laptop screen..)

Thanks in advance for any suggestion on how to fix this..
Alessio.

===

Below the xorg.conf file I have at the moment.

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "Default Screen" 0 0
	Screen         "aticonfig-Screen[0]-1" RightOf "Default Screen"
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Monitor"
	Identifier  "aticonfig-Monitor[0]-1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-1"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     24
		Modes    "1280x800@60" "1440x900@60" "1280x720@60" "1600x1024@60" "1280x768@60" "1680x1050@60" "800x600@60" "800x600@56"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-1"
	Device     "aticonfig-Device[0]-1"
	Monitor    "aticonfig-Monitor[0]-1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

---

### Post by puccio on 2009-03-24
Hi,

after some "try & run", I found this configuration which works as I wanted. Comments are welcome..

#####################
# xorg.conf dual head
######################

Section "dri"
  Mode 0666
EndSection 

Section "ServerLayout"
	Identifier  "aticonfig Layout"
	Screen      0 "Default Screen"
	Screen      1 "aticonfig-Screen[0]-1" RightOf "Default Screen"
    Option "Xinerama" "on"
    Option "Clone" "off"
EndSection

Section "Files"
EndSection

Section "Module"
  Load "dbe"
  Load "extmod"
  #Load "fbdevhw"
  Load "glx"
  Load "dri"
  Load "record"
  Load "freetype"
  Load "type1"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier  "aticonfig-Monitor[0]-1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Screen      0
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-1"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     24
		Modes    "1280x800@60" "1440x900@60" "1280x720@60" "1600x1024@60" "1280x768@60" "1680x1050@60" "800x600@60" "800x600@56"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-1"
	Device     "aticonfig-Device[0]-1"
	Monitor    "aticonfig-Monitor[0]-1"
	DefaultDepth     24
    Subsection "Display"
      Depth 24
      Modes "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubsection
EndSection

---

