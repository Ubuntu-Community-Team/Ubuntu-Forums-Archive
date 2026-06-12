---
title: "Hp 6530b (Intel Cantiga) + additional 1920x1080 monitor"
date: 2008-11-25
forum: Hardware
---

### Post by super764 on 2008-11-25
Hello.
Got a new HP 6530b laptop.
I attached a 1920x1080 monitor to the vga out, configured it with the util System->Preferences->Monitor Resolution.

This is my xorg.conf

```
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
	Option		"UseFBDev"		"true"
EndSection
```

Everything was working (but compiz,that is not a problem).

Yesterday i used the laptop for some time, without attaching it to the 2nd screen (I did it several times before not having any problem) and today i got this problem:

- The desktop looks like the image attached(Screnshoot is actually the sum of the 2 desktops),+ in the additional monitor desktop a "right click" doesn't make the contextual menu appear.

- On the left monitor (laptop embedded one) the bottom-panel position is not kept. The panel is restored on top of the bottom panel of the additional monitor every restart (see image).

- Even if I set the appearance preference to show desktop background image "Zoomed" across the desktop, it seems that it is repeated in 1280x960 boxes (= the laptop screen resolution).

I spent hours trying to fix it... i couldn't find a solution.
Any idea, or best ways to configure the scenario? 

Any help would be very appreciated.

---

