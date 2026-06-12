---
title: "VAIO TR5 - sound and vision"
date: 2007-03-01
forum: Hardware &amp; Laptops
---

### Post by Belgatom on 2007-03-01
AFter my first experiment on a desktop, I want to Ubuntize my laptop as well. I currently have 2 problems (probably more but let's just see).

First one is simple. I can't find the Horizontal Synch and Vertical Frequency of the monitor to safely change the resolution. Anybody have a suggestion. I need to get it to 1280*768. I know how but need to find specifications. Is there a way to do this safely if you can't get your hands on the exact specs? 

Second: Sound is currently enormously silent. It's existent, I can here the Examples but ever so slightly. This I was only able to find out when using the headphone jack. I have no idea if the built in speakers work. They probably do but are so quiet I can't hear them. 

Some technical info:

Sony PCG-TR5 EB (Japanese model) 
Running Edgy Eft 6.10 installed
Soundcard info : Intel 82801

Any more info needed, just ask.

---

### Post by jblack on 2007-03-01
> **Belgatom said:**
> AFter my first experiment on a desktop, I want to Ubuntize my laptop as well. I currently have 2 problems (probably more but let's just see).

First one is simple. I can't find the Horizontal Synch and Vertical Frequency of the monitor to safely change the resolution. Anybody have a suggestion. I need to get it to 1280*768. I know how but need to find specifications. Is there a way to do this safely if you can't get your hands on the exact specs? 

Second: Sound is currently enormously silent. It's existent, I can here the Examples but ever so slightly. This I was only able to find out when using the headphone jack. I have no idea if the built in speakers work. They probably do but are so quiet I can't hear them. 

Some technical info:

Sony PCG-TR5 EB (Japanese model) 
Running Edgy Eft 6.10 installed
Soundcard info : Intel 82801

Any more info needed, just ask.

To fix the screen resolution. Download and install 915resolution and reboot. To fix the audio, open your sound mixer and uncheck the box for "external amplifier". :)

---

### Post by Belgatom on 2007-03-06
OK, did both things.

INstalled 915resolution but didn't work. I was worried that I had done it wrong so I started all over again en used this : [http://roland-lopez.blogspot.com/2007/03/auto915resolution-ubuntu-resolution-fix.html](http://roland-lopez.blogspot.com/2007/03/auto915resolution-ubuntu-resolution-fix.html)

But no changes. 

Concerning the sound:

The External Amplifier was not checked. Just to make sure, I checked it. Closed the window, then unchecked it again. But no avail. 

Concerning the resolution, this is what I found in my xorg.conf. So it does look like Ubuntu could find that the limit of my resolution is 1280*768. Where do I go now? 


> 
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82852/855GM Integrated Graphics Device"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x768"
	EndSubSection
EndSection


---

