---
title: "IBM T23 Screen Resolution"
date: 2005-04-17
forum: Hardware &amp; Laptops
---

### Post by jsmothers on 2005-04-17
I had Warty on my IBM T23 fine, but when I upgraded to Hoary, the screen resolution is lost.  I read some previous post ([http://ubuntuforums.org/archive/index.php/t-21481.html](http://ubuntuforums.org/archive/index.php/t-21481.html)) that said to change the xorg.conf file to get addition resolutions:

Section "Monitor"
Identifier "BuiltinLCD"
VendorName "IBM"
ModelName "Laptop 1024x768"
HorizSync 31.5 - 90.0
VertRefresh 59.0 - 70.0
# Option "dpms"
EndSection

which gave addition resolutions but NONE of them take up the entire screen.  Is this a driver problem?  I figured because it's IBM it would work, especially since Warty worked fine.  What's up?  anyone have any clues?

---

### Post by jsmothers on 2005-04-17
In responding to my own post, I just got the resolution (1400x1050) to work and to take up the whole screen.  I didn't add all the resolutions like the following:

Section "Screen"
	Identifier "Default Screen"
	Device "S3 Inc. SuperSavage IX/C SDR"
	Monitor "BuiltinLCD"
	DefaultDepth 24
	Subsection "Display"
		Depth 24
		Modes "1400x1050" "1280x1024" "1024x768"
	EndSubSection
	Subsection "Display"
		Depth 16
		Modes "1400x1050" "1280x1024" "1024x768"
	EndSubSection
	Subsection "Display"
		Depth 8
		Modes "1024x768"
	EndSubSection
EndSection

I didn't add all the resolutions (especially the 1400x1050) to the Subsection Display Modes.

But I still wonder if I should get specific drives for the video card.  I can tell by the screensaver that something is slower.  For instance, the matrix style screensaver takes about a minutes for the characters dropping to fill up the screen.  It's like sllllllooooowwww motion.

Has anyone out there downloaded the S3 SuperSavage video drives and have them work with xorg and ubuntu?

---

