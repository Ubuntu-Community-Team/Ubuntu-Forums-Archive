---
title: "trouble installing ati drivers for x1600 laptop"
date: 2006-12-01
forum: Hardware &amp; Laptops
---

### Post by yfrangi on 2006-12-01
Hi,
I've search for this problem but I can't seem to find any solutions to it so I am posting about it here.

I have a Acer Aspire 5112WLMi with
Turion 64 x2 CPU
Radeon Mobility x1600 video card
2 GB RAM

I've installed Ubuntu 6.06 (with the 686 kernel installed after the initial install)

Now I've tried several methods of installing ATI video card drivers including the drivers from the ati website and [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

Each time I do this and restart I get this error:



INVALID IO LOCATION b:0x9000 e:0x90ff corrrecting^G
requesting insufficient memory window!: start 0x9000 end 0x90ff size 0xc0120100

" repeats for locations 0x9400 0x9800 0x9c00

cannot find replacement memory range
fglrx(0) register resource failed
setVBEMode failed
(EE) fglrx(0) preinit failed
(EE) screen(s) foudn but none have a usuable configuration

Fatal server error:
no screens found


I've setup a similar configuration with my desktop and had no problems (9800pro) so i'm at a loss here.

Thanks to anyone who can help.

---

### Post by didobuntu on 2006-12-01
I have the same graphic card in my asus laptop.
Don't install the ati driver. They need to be adapted for ubuntu.

Use instead the fglrx driver that from ubuntu repos. It works fine. Then adapt you /etc/X11/xorg.conf file. Here is mine:

supposing that you are using ubuntu 6.10, if not remove the last Extebsions' section

...
Section "Device"
	Identifier  "ATI Technologies, Inc. ATI Mobility X1600"
	Driver      "fglrx"
	Option	    "UseInternalAGPGART" "no"
	Option	    "DesktopSetup" "single"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "TVFormat" "PAL-N"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. ATI Mobility X1600"
	Monitor    "Generic Monitor"
	Option     "AddARGBGLXVisual" "True"
	Option     "DisableGLXRootClipping"  "True"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1680x1050"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1680x1050"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1680x1050"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1680x1050"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1680x1050"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1680x1050"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "RENDER"  "Enable"
	Option	    "Composite" "disable"
EndSection


Good luck

---

