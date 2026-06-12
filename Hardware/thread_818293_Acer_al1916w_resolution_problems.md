---
title: "Acer al1916w resolution problems"
date: 2008-06-04
forum: Hardware
---

### Post by jaredavant on 2008-06-04
Hi, I'm a total noob in ubuntu, but I'm loving it so far.  I've been lurking quite a bit but I've learned a ton so far from these forums.

I'm running an Asus P4V8X-MX graphics integrated motherboard, and the Screens and Graphics panel recognizes it as a generic VESA compliant video card.  I just bought an Acer al1916w LCD monitor and I'm having trouble getting anything other than 1024x768.  I can't even get a proper widescreen aspect ratio.  I've changed my xorg.conf file several times, adding a modeline and "1440x900@60".  Nothing works, and I'm not even prompted with the choice of anything but 1024x768, 800x600, or 640x480 in the screens and graphics panel.  All of the threads that I've found by searching deal with intel 915resolution fixes, and nothing I've tried has worked so far.  I really like this monitor and I hope I can use it to it's full potential.  Here is the relevant part of my xorg.conf file - what am I doing wrong?

Section "Monitor"
	Identifier	"Compaq FS740"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1440x900"
	Horizsync	31.5-56.0
	Vertrefresh	56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1440x900@60" 106.5 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Compaq FS740"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1024	768
		Modes		"1440x900@60"  "1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection

Thanks in advance!

---

### Post by jaredavant on 2008-06-04
updated-
I figured out that my integrated graphics card is a VIA unichrome.  I found another thread and ran this command:  

sudo apt-get install xserver-xorg-video-unichrome

and logged out/in.  now I have 1280x1024 - better, but still not the appropriate widescreen ratio.  here is my updated relevant xorg.conf info:



Section "Device"
        Identifier      "Generic Video Card"
        Driver          "vesa"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Acer AL1916W"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Acer AL1916W"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1440x1440" "1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection


I see that my target resolution of 1440x900 is listed, but it's not coming up in the screens and graphics panel.  Again thanks for any help you can give me!

---

