---
title: "Unable to get native resolution in Ubuntu 8.10 using Lenovo T400"
date: 2009-03-03
forum: Hardware
---

### Post by marcel.zeng on 2009-03-03
My current setup is a T400 laptop plus an external monitor (Samsung 2233SW) plugged to the VGA output. The laptop has an Intel integrated graphics card.

I am able to get extended desktop where the resolution for my external monitor is 1920x1080 and the resolution for my laptop monitor is 1280x800. However, the native resolution for the T400 is 1440x900.

I cannot find an option to change the resolution to 1440x900. Any ideas?

I did try a few things, but none of them worked:
* I followed instructions from [ThinkWiki]("http://www.thinkwiki.org/wiki/Install_Ubuntu_8.10_(Intrepid_Ibex)_on_a_Thinkpad_T400#Internal_LCD_Resolution_F") website.
* running 'xrandr --output LVDS --mode 1440x900' tells me 'xrandr: cannot find mode 1440x900'.

**The following are the details when I run xrandr.**

Screen 0: minimum 320 x 200, current 3200 x 1080, maximum 3200 x 1080
VGA connected 1920x1080+1280+0 (normal left inverted right x axis y axis) 477mm x 268mm
   1920x1080      59.9*+
   1680x1050      60.0     60.0  
   1600x1024      60.2  
   1400x1050      60.0  
   1280x1024      75.0     60.0     60.0  
   1440x900       59.9     60.0  
   1280x960       60.0     60.0  
   1360x768       59.8  
   1280x800       60.0  
   1152x864       75.0     60.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     60.0     59.9  
   720x400        70.1  
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 303mm x 190mm
   1280x800       60.0*+
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
HDMI-1 disconnected (normal left inverted right x axis y axis)
HDMI-2 disconnected (normal left inverted right x axis y axis)

**The following is my xorg.conf.**

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	3200 1080
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

I appreciate any input on this. ;)

---

### Post by Mamaras on 2009-03-13
I have the same problem - can't get the native resolution (1400x900). I also followed the directions on the ThinkWiki Link. 

I have seen many references to turning off switchable graphics in the bios but I don't see that option under Config->Display in my bios menus. I just got the laptop last week, so I don't know if something has changed (bios version 2.07). 

Any help would be much appreciated!

---

### Post by Mamaras on 2009-03-14
Ok - so I've figured out that I only have the intel graphics card on my t400 and not the additional ATI card.  I think the native resolution is 1280x800.

---

### Post by wdli on 2010-02-14
Hi,

I just installed 9.04 on my T400 with only Intel GMA 4500 MHD video chip. But I can only get 1024x768 on my external monitor. Do you have any idea how to improve this?

Thanks.

---

