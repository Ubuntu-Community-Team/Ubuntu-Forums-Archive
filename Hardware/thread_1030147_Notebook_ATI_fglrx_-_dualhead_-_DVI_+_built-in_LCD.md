---
title: "Notebook ATI fglrx - dualhead - DVI + built-in LCD"
date: 2009-01-04
forum: Hardware
---

### Post by pekarna on 2009-01-04
Hello,

* Ubuntu 8.10
* Acer TravelMate 8000
* ATI Mobility Radeon 9700


I'm trying to configure Xorg to have dual-head desktop:

- Samsung LCD 1600x1200 at DVI
- Laptop's built-in LCD 1400x1050.

I've read many how-tos, xorg.conf man page, fglrx man page, ... however, many of them are aimed at CRT monitors, or independent Screens, or to be mirrored or cloned.

ATI drivers are installed.
I have tried to reconfigure xorg using dpkg.

Still, all I am able to achieve is to have external LCD 1600x1200 at VGA and notebook's LCD off. With DVI this does not work.

Is there some how-to for this special case - that is, how to make laptop with ATI split the desktop both to it's display and DVI output?


Thanks, Ondra

----------------

Current xorg.conf:

```
Section "Module"
        Load  "ddc"        # ddc probing of monitor
        Load  "dbe"
        Load  "dri"
        Load  "GLcore"
        Load  "extmod"
        Load  "glx"
        Load  "bitmap"     # bitmap-fonts
        Load  "speedo"
        Load  "type1"
        Load  "freetype"
        Load  "record"
EndSection

Section "DRI"
        Mode 0666
EndSection


Section "Device"
  Identifier "ATIshit1"
  Driver "fglrx"
  Busid "PCI:1:0:0"
  Screen 0
EndSection

Section "Device"
  Identifier "ATIshit2"
  Driver "fglrx"
  Busid "PCI:1:0:0"
  Screen 1
EndSection

Section "Monitor"
	Identifier	"Notebook LCD"
	
        Option "DPMS"
EndSection

Section "Monitor"
	Identifier	"Samsung LCD"
        Option "DPMS"
EndSection


Section "Screen"
  Identifier "Laptop Screen"
  Device "ATIshit1"
  Monitor "Notebook LCD"
  Defaultdepth 24
  SubSection "Display"
  Depth 24
  # Despite not including any more modes, there are many more options in the GUI
  Modes "1400x1050&#8243;
  EndSubSection
EndSection

Section "Screen"
  Identifier "Samsung Screen"
  Device "ATIshit2"
  Monitor "Samsung LCD"
  Defaultdepth 24
  SubSection "Display"
    Depth 24
    Modes "1600x1200&#8243;
  EndSubSection
EndSection


# Enabling the Xinerama caused problems every time -
# but it sounds like getting that working is the last step
# in having true interacting monitors.

#Section "ServerFlags"
# Option "Xinerama" "true"
# Option "DefaultServerLayout" "Default Layout"
#EndSection

Section "ServerLayout"
  Identifier "Default Layout"
  Screen 0 "Laptop Screen" 0 0
  Screen 1 "Samsung Screen" RightOf "Laptop Screen"
  # DualHead means two monitors
  Option "DualHead" "true"
EndSection

```

---

### Post by theDaveTheRave on 2009-01-06
Pekarna,

OK i'm looking at your config, as I would like to do the same thing eventually!

I'm no expert by any means but my thoughts are as follows

the <Busid "PCI:1:0:0"> is the same for both devices, does this not mean that the output is coming from the same place ?

Also you have

<code>

Section "Monitor"
	Identifier	"Notebook LCD"
	
        Option "DPMS"
EndSection

Section "Monitor"
	Identifier	"Samsung LCD"
        Option "DPMS"
EndSection

</code>

will the second not overide the first (or maybe vice versa)?

Looking at my output of <lshw> I have 2 sections with <* display:0> and <*display:1> but both are listed as "unclaimed", 

the physical id are 2 and 2.1 respecively. 

ant the <bus info: pci@0000:00:02.0> <bus info: pci@0000:00:02.1> reflects this also.

How does this compare to yours? maybe you should be using these physical ID's  and the bus info from this output??

YOu are certainly giving me plenty to think about, and I want to get this working soon so as to have a dual screen on my works desktop.

for now though I'm going to have to do some "work" that I get paid for! ;)

David

---

