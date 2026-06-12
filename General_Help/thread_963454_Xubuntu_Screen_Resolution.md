---
title: "Xubuntu Screen Resolution"
date: 2008-10-30
forum: General Help
---

### Post by macnyak on 2008-10-30
please help me, the screen resolution of my laptop where i installed Xubuntu 8.04 was i think high. i cannot see all the desktop taskbar, i want it to change to 800x600. How can i do it? please teach me step by steps thanks.


when i click Applications, Settings, Settings Manager, im directed to 

Xfce Settings Manager. when i click Desktop,.. i am directed to Desktop preferences like Appearance, Bahavior, Color Style, First Color, Adjust Brightness.

When I click Display,.. I am directed to Display Preferences, were in i see Gamma Correction, red, green, blue, close, revert, sync sliders, Resolution (default) and theres no option for me to adjust it?????..... 

What shall i do? please help me,.. THanks...

---

### Post by matheos on 2008-11-02
Hi! i got the same problem... my up taskbar was not complete and my bottom one was not in my screen... 
i've add this in my /etc/X11/xorg.conf :

```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	SubSection "Display"
		Depth 24
		Modes		"1440x900" "800x600"    #<------------this line--
	EndSubSection
EndSection
```

my machine is a laptop evrex stepnote va1500v
chipset via vn896 processor via c7-m 1500 mhz

---

