---
title: "HOWTO: 9600 mobility resolution, direct rendering,"
date: 2007-11-08
forum: Hardware &amp; Laptops
---

### Post by Tavorisch on 2007-11-08
I have been dual booting ubuntu 7.04 .. a lso tried gutsy but no luck with some certain parts of madwifi! so back to fesity again, and have direct rendering and 1680x1050 res going without the  The Composite Exension is Diabled error either.... althouhg a little flaky with 1 thing, which is the fade effect (asking you for your keyring)  im guessing its the refresh rate i have it set at that is doing this but, cube effect and wobbly windows works great..
what i did was, I kept the default video drivers when you install feisty, i did install ```
sudo apt-get install xserver-xgl
``` although Im not sure if that has anything to do with it.. So if you do have the ATI Accelerated Graphics Driver enabled in the restricted drivers manager, uncheck that.. go into your xorg.conf by opening up your Terminal, Applications>Accessories>Terminal ```
sudo gedit /etc/X11/xorg.conf
``` make sure your extensions section on the bottom says this,
```
 Section "Extensions"
Option "Composite" "disable"
EndSection
```
if not change it to that!,, now go to your screen sections and add in your resolution! mine looks like this ```

        Section "Screen"
	Identifier	"Default Screen"
	Device		"                                      "
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1680x1050" "1600x1200" "1440x900" "1400x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1680x1050" "1600x1200" "1440x900" "1400x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1680x1050" "1600x1200" "1440x900" "1400x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1680x1050" "1600x1200" "1440x900" "1400x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1680x1050" "1600x1200" "1440x900" "1400x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1680x1050" "1600x1200" "1440x900" "1400x1050" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

``` save and close! restart X(video and desktop part of your linux by,,   Ctrl+Alt+Backspace... login see if that worked.. 
I realize your resolution may be a bit higher or lower than mine just put whateer ur max is in every single sub section like mine. again running 1680x1050
if that doesn't work i would open up terminal again and try ```
sudo dpkg-reconfigure xserver-xorg
```
command.. use tab and enter to go through the reconfiguration, leaving most things at default is fine, except color depth I did 16 bits.. or 16.. and when you get to resoluions or
which things to load under modules use spacebar to enable or disable (the * means enabled, just blank means no.)  hope this helps hope to get some feedback! it got me to the point where I am happy with my Dell inspiron 8600 running linux with that pain in the *** 9600 mobility.

---

