---
title: "New to Ubuntu/Linux - Frustrated at Display/Monitor Resolution"
date: 2011-03-30
forum: Hardware
---

### Post by darkufo on 2011-03-30
Hi all,

I'm a new Ubuntu/Linux user and I've just setup my first laptop to use Ubuntu 10.10

However, I've come across an issue and I've done a lot of searching on various forums etc and basically I'm going around in circles. I've had my PC hang already after I tried to create a xorg.conf file. I have since removed the changes I made.

I have a a SIS 771/671 PCIE VIA Display Adapter (rev 10) 

I got this info via the lspci command.

The problem I have is that it's not letting me select a resolution above 1024 * 768. I know it has higher resolutions as when it was a Windows XP and Vista PC I had higher resolutions.

Can someone please try to help put it in simple terms what I need to do. 

There has to be an easier way to set a screen resolution that manually editing cryptic files and knowing refresh rates etc

---

### Post by KegHead on 2011-03-30
Hi!

Have you tries going to System...preferences... monitor and selected resolution?

KegHead

---

### Post by darkufo on 2011-03-30
Yep, that was the first thing I tried.

Does not show any res over 1024*768

Monitor is Unknown and Detect Monitor does nothing

---

### Post by KegHead on 2011-03-30
Hi!

Can you send a screen shot?

KegHead

---

### Post by darkufo on 2011-03-30
It's the same as this one
[http://img87.imageshack.us/i/testll.jpg/sr=1](http://img87.imageshack.us/i/testll.jpg/sr=1)

But my top resolution is 1024 768 and has a refresh of 61

---

### Post by KegHead on 2011-03-30
Hi!

Try setting your refresh rate.

Try setting making default & apply.

KegHead

---

### Post by darkufo on 2011-03-30
Thanks, I'll give that a go when I get home.

Thanks for your help I'll report back later.

---

### Post by KegHead on 2011-03-30
Hi!

This should work:

sudo dpkg-reconfigure xserver-xorg

KegHead

---

### Post by darkufo on 2011-03-31
Thanks everyone. I nearly have this working :)

Below is my xorg.conf file which now lets me get 1280 * 768 although it can go higher as I had it running higher when I had windows.

Also below is my output of what it thinks is my video spec.

# lspci -v -s 00:00.0
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
	Subsystem: Elitegroup Computer Systems Device 5050
	Flags: bus master, medium devsel, latency 32
	Memory at a0000000 (32-bit, non-prefetchable) [size=256M]
	Capabilities: [c0] AGP version 3.5
	Kernel driver in use: agpgart-sis

Can anyone see/advise what I need to change in my xorg.conf to get a 1400*900 resolution.

                                                                     
                                                                     
                                                                     
                                             
> # Xorg configuration created by system-config-display

Section "ServerLayout"
	Identifier     "single head configuration"
	Screen      0  "Screen0" 0 0
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "InputDevice"

# keyboard added by system-config-display
	Identifier  "Keyboard0"
	Driver      "kbd"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
	Option	    "XkbVariant" "intl"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	ModelName    "LCD Panel 1024x768"
	HorizSync    31.5 - 48.0
	VertRefresh  56.0 - 65.0
	Option	    "dpms"
EndSection

Section "Device"
	Identifier  "Videocard0"
	Driver      "vesa"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Videocard0"
	Monitor    "Monitor0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

---

### Post by SeijiSensei on 2011-03-31
> **darkufo said:**
> Can anyone see/advise what I need to change in my xorg.conf to get a 1400*900 resolution.

Try following the procedure outlined in [this posting](http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/how-to-get-widescreen-1280x768-working-on-linux-524319/#post2621585) to generate the proper "ModeLines" for your adapter and monitor combination.  For instance, you could try

```
gtf 1440 900 60
```

to generate a ModeLine for 1440x900 @ 60 Hz.  Put the ModeLine in the Monitor section as that posting describes ("method 2").

---

### Post by darkufo on 2011-03-31
Thanks, I'll give it a go.

---

