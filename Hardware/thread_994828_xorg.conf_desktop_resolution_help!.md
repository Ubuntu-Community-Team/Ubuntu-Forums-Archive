---
title: "xorg.conf desktop resolution help!"
date: 2008-11-27
forum: Hardware
---

### Post by mpcengineering on 2008-11-27
Hi guys,

I've been researching the correct way to set up xorg.conf to enable a desktop resolution that is not available by default, and it seems pretty easy to get wrong to someone who is new to it like me.  I've basically got to the stage where I need one wiser than myself to cast an eye over what I have done to try and see where I have gone wrong...

Here's the background:  I am trying to setup a laptop with onboard SiS graphics to display a resolution of 1280x800 which is the native resolution of the screen.  There are no SiS drivers I can use and so I am using vesa instead.  I have been reading through the xorg.conf man page and looking at tons of stuff on the net but cant seem to get it to work.  I 'think' I'm on the right lines, but if someone could take a look and tell me what exactly I have to change, that would be great.  Here is my xorg.conf:

```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Option		"DPMS"
	Modeline	"1280x800_60" 83.46  1280 1344 1480 1680  800 801 804 828  -HSync +Vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes	"1280x800_60"
	EndSubSection
EndSection
```

I have generated the modeline using gtf/cvt (the difference between the tools is less than clear to me...) and as far as I am aware the vesa driver tops out at 1280x1024 so this setup in theory is possible.  xwininfo reports a depth of 24 at 800x600 (only this and 640x480 are available currently) and the refresh rate is 60Hz at 800x600.

I'm sure it is just a configuration thing in the xorg.conf, can anyone pinpoint what is wrong in my configuration?

Any help much appreciated!!

Jon

---

### Post by mpcengineering on 2008-11-27
This is in the wrong section isn't it?

---

### Post by camionrouge on 2008-12-18
Hi, I think your problem coud be related to out of range HorizSync. Take a look at your X log file, usually at /var/log/Xorg.O.log for clues. I tried a live cd Xubuntu intrepid in an advent 5421 with sis 771/671 graphics and hit a similar problem. Look through log for sections on vesa. My first vesa block says DDC read failed, which means the screen probe for settings failed, and after the mode section the next vesa block shows the driver uses default values for hsync of 31.5-37.9 (which is wrong) and fails the higher resolution modes with 'hsync out of range' and defaults to low res mode. If this is identified by the log to be your problem you could just specify the rates under 'monitor' with HorizSync 28.0 - 80.0 and VertRefresh 48.0 - 75.0
You could try just adding this to your original xorg.conf If you can find out your specific screen sync rates even better. Look at [https://wiki.ubuntu.com/X/Troubleshooting/Resolution](https://wiki.ubuntu.com/X/Troubleshooting/Resolution) for more info and alternatives. Good Luck.

---

