---
title: "Dual Monitor not working :("
date: 2010-02-09
forum: Hardware
---

### Post by rbdragonfire on 2010-02-09
Hello,

I have a HP Pavillion dv2000 series laptop with an Intel 945GM graphics card. I have a monitor connected to the laptop. I want to use the external monitor as an extended desktop. However, only one monitor works at a time.

If I boot my computer without the external monitor connected, everything gets displayed in the laptop monitor. If I boot it with the external monitor connected, everything gets displayed there. Each time the other monitor is blank.


If I look in "Display Preferences", it always sees only one monitor - either the laptop monitor or the external (if it is connected). Pressing "Detect Monitors" doesn't display anything on the second monitor (except, it flashes). Checking "Mirror Screens" does nothing either.

Here is my output for ```
inxi -G
```

```
Graphics:  Card Intel Mobile 945GM/GMS 943/940GML Express Integrated Graphics Controller X.Org 1.6.4 Res: 1280x1024@60.0hz 
           GLX Renderer Mesa DRI Intel 945GM GEM 20090712 2009Q2 RC3 x86/MMX/SSE2 GLX Version 1.4 Mesa 7.6

```

This is what my xorg.conf file looks like:

```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"intel"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```


I would be very very thankful if someone can help me out and make this work! :)

---

