---
title: "Unable to change default resolution on 8.10"
date: 2008-11-09
forum: General Help
---

### Post by brmaynard on 2008-11-09
I installed a fresh copy of Kubuntu 8.10 and am experiencing issues with my default video resolution.  By default, xserver/KDE are starting with a screen resolution of 1360x768.  My monitor is unable to handle this resolution.  Inside the Display system settings I bumped the resolution down to 1024x768 and everything works great.  Whenever I log out and log back in the desktop resolution appears to go back to 1360x768.  If I try and load the display settings (or krandrtray) the system will freeze 9 times out of 10.  One the rare occasion that display settings doesn't freeze, the desktop will automatically change to a 1024x768 layout with any other intervention on my part (simply starting clicking on the Display icon in settings is enough to get it to change to 1024x768).

How can change X11 so it either defaults to 1024x768?  How do I remove the higher resolutions completely?  I have tried updating the xorg.conf file to add a SubSection "Display" with a 1024x768 mode and that did not work.

xorg.conf:
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

I am using an ATI 9200 video card.

Thanks

---

### Post by nyp4life on 2008-11-09
That makes two of us.. well sort of. My screen starts up at 1152x864 (with a maximum of 1360x768 ) and I cant get it to change at all. The 'Display' option in System Settings leads to nothing.. The option to change size is there but with no values to select.. Just a blank drop-box. I added "Virtual 1680 1050" to my xorg.conf and xrandr output now says the maximum is indeed 1680x1050 but I try "xrandr --size 1680x1050" but still no change. My xorg.conf is almost identical to the one above:

Section "Device"
	Identifier	"Configured Video Device"
	Option		"AccelMethod"	"EXA"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		  Virtual 1680 1050
	EndSubSection
EndSection

and I am using a Radeon x1950 Pro on kubuntu 8.10 (amd64)

---

### Post by aged hippy on 2008-11-09
I have an ATI Radeon 9800 Pro, and to get the resolution to stay as i set it, i used Synaptic to install:
***xserver-xorg-video-ati,*** ***xserver-xorg-video-radeon,*** and ***xorg-driver-fglrx.***

These worked in my case, they _may do so_ in yours....

---

### Post by nyp4life on 2008-11-09
ok i finally got my resolution to work out at 1680x1050. I still cant change it with xrandr or the display settings but here's the xorg.conf that did the magic:

Section "Device"
	Identifier	"Configured Video Device"
	Option		"AccelMethod"	"EXA"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	VendorName	"ACR"
	ModelName	"Acer AL2216W"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	SubSection "Display"
		  Depth		24
		  Modes 	"1680x1050" "1440x1440" "1360x850" "1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
		  Virtual	2048 2048
	EndSubSection
EndSection

brmaynard- try typing the model name of your monitor and 'xorg.conf' in google.. and hopefully it points you to some recommended settings. and if those don't work for you play around with it. i had to delete some of the recommended lines they had but i didn't really change anything. good luck!

---

