---
title: "Resolution drop after laptop monitor replaced"
date: 2007-08-20
forum: Hardware &amp; Laptops
---

### Post by rstoya05-lx on 2007-08-20
I have an ATI x1400 card in a Lenovo T60 laptop (wide screen). I've been using the fglrx driver for a few months and my resolution was 1400x1050.  That is until my monitor had to be replaced.  After the IBM technician changed the monitor I started up and since then the max resolution has been 1280x800 no matter what I tried. The technician said he only changed the monitor and didn't touch the card.

I should also mention on Windows XP through VMWare the resolution can go up 1920x1440. 

Here are the relevant sections of my /etc/X11/xorg.conf. Any suggestions would be appreciated. The vertical resolution of 800 is pretty limiting.

```

Section "Device"
	Identifier	"ATI Default Card"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-84
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Default Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1920x1440" "1600x1200" "1400x1050" "1280x1024" "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1920x1440" "1600x1200" "1400x1050" "1280x1024" "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1920x1440" "1600x1200" "1400x1050" "1280x1024" "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1920x1440" "1600x1200" "1400x1050" "1280x1024" "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1920x1440" "1600x1200" "1400x1050" "1280x1024" "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1920x1440" "1600x1200" "1400x1050" "1280x1024" "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

Thanks,
Rossen

---

### Post by Circuit99 on 2007-08-21
Hi,

I suggest that you simple go to 

System>Preferences>Screen Resolutions 

There change resolution to what you want

If you can not do that, you need to find out your monitor


HorizSync	xx-xx  
VertRefresh	xx-xx

These have to be changed to what is stated in monitor manual or manufacture website

Please note the xx-xx are replaced by relevent values

Found in your my /etc/X11/xorg.conf, as this:


Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-84
	VertRefresh	43-60
EndSection


Use inside terminal

gksu gedit /etc/X11/xorg.conf


OR use

ALT+F2 then type

gksu gedit /etc/X11/xorg.conf

in top box, then press run 

If editing xorg does not work then you have manual reconfigure xserver-xorg by the following:

sudo dpkg-reconfigure xserver-xorg

Please use inside a terminal. 

I believe you can use this statement below to update xorg but I'am not sure

sudo dpkg-reconfigure -phigh xserver-xorg



BEFORE YOU DO ANYTHING CHECK OUT THIS THREAD


[http://ubuntuforums.org/showthread.php?p=454217](http://ubuntuforums.org/showthread.php?p=454217)

It is a how to on what you need to do

Good Luck

:popcorn:

---

### Post by rstoya05-lx on 2007-08-21
> **Circuit99 said:**
> 
I suggest that you simple go to 

System>Preferences>Screen Resolutions 


Yes, I've tried that. The screen resolution does not list anything higher than 1280x800.

> **Circuit99 said:**
> 
If you can not do that, you need to find out your monitor

HorizSync	xx-xx  
VertRefresh	xx-xx

These have to be changed to what is stated in monitor manual or manufacture website


I found this command:
```
sudo ddcprobe | less
```

It's supposed to show the HorizSync and VertRefresh values for a monitor if the monitor supports it. Mine doesn't. However, it did tell me that my monitor id is '154W01-TLAC'.

I could not find out the correct HorSync and VertRefresh values for this monitor id. Google searches didn't yield it and the manufacturer's page has a blank table for this monitor:
[http://www.lgphilips-lcd.com/homeContain/jsp/eng/prd/prd301_j_e.jsp?prd=LP154W01](http://www.lgphilips-lcd.com/homeContain/jsp/eng/prd/prd301_j_e.jsp?prd=LP154W01)

However, according to this page listing displays for ThinkPads the native resolution matching my monitor id is 1280x800:
[http://www.thinkwiki.org/wiki/TFT_display](http://www.thinkwiki.org/wiki/TFT_display)

So it looks like I got stuck with an inferior monitor as a result of the monitor replacement. I'm going to call IBM support again. 

Thanks for your help.

---

