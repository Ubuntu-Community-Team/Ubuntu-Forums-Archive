---
title: "latitude c800 xorg video tearing issue"
date: 2006-10-19
forum: Hardware &amp; Laptops
---

### Post by soulglo83 on 2006-10-19
Hello!
I recently acquired a dell latitude c800 laptop.  It arrived with win2000 installed, but i found it archaic aside my ubuntu desktop.  I tried puppy linux (which i loved!), zenwalk, ubuntu dapper and edgy, xubuntu edgy, and kubuntu.  Every install I've tried that implements xorg, has had seriously impaired visual output.  Puppy didn't because i opted for xvesa, instead of xorg.  Once the xwindowingsystem starts, and gdm opens, the center of the screen looks like it has a tear running down the center, and the right half redisplays information on the left.  Firefox is even aware that the moniter isn't configured correctly!  instead of consuming my whole desktop, it resizes to the width just right of the tearing, so its almost usable.  This error occurs with the ati driver, and the vesa driver selected.  I'm curious if anyone has any suggestions as to how to trouble shoot this further.  The specs for the laptop are below.

Processor: PIII800
Memory:    192MB
Graphics:  ATi Rage Mobility m4
xorg driver:    "ati"

any help would be greatly appreciated, as i love linux and xorg dearly.  I would hate to have to use a dated windowing system or even worse...

---

### Post by soulglo83 on 2006-10-19
ok after some more tinkering, i realized it was how xorg autodetects the vsync and hsync frequency for my moniter.  i simply updated the following in my /etc/X11/xorg.conf

Section "Monitor"
	Identifier     "Monitor1"
	VendorName "DXS"
	ModelName "DXS:1313"
     HorizSync 30 - 50.0
     VertRefresh 35.5 - 70
     Option "UseEdidFreqs" "1"

EndSection

to:

Section "Monitor"
	Identifier     "Monitor1"
	VendorName "DXS"
	ModelName "DXS:1313"
     HorizSync 60 - 90.0
     VertRefresh 50-70
     Option "UseEdidFreqs" "1"

EndSection

All better now! Im running at 1400x1050 and boy does it look great!

---

### Post by sunfisher on 2007-11-29
Thanks for the great info! I used it to 'fix' my video tearing problem w/ a Dell C800 using ZenWalk 4.8, really helps to get some good solid info.:guitar: I'm rocking now!

---

### Post by epitaph123 on 2008-01-11
My xorg.conf looks different, and I am getting two tears in the bottom right corner of my laptop lcd screen, one goes along the clock @ the bottom taskbar, the other is about 2 inches higher. they run horazontally for about 3 inches off the side

Section "Device"
	Identifier	"ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]"
	Boardname	"ati"
	Busid		"PCI:1:5:0"
	Driver		"fglrx"
	Screen	0
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	640	480
		Modes		"1280x800@60"
	EndSubSection
EndSection




I have to log out & log back on for the tears to go away.

---

