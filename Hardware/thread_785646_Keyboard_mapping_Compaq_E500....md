---
title: "Keyboard mapping Compaq E500..."
date: 2008-05-07
forum: Hardware
---

### Post by snakedog on 2008-05-07
...I installed Xubuntu 8.04 successfully on this old laptop, an E500 Compaq.  But I having some weird keyboard anomalies that I attribute to my installation of the keyboard.  Currently, it&#347; mapped as US internat&#314;.  As you can see from the contraction in the previous sentence, I got this thing mapped wrong.  Here&#347; (there it is again) the keyboard section of my xorg.conf file: 

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"intl"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

I believe this is 104-key US layout, but not sure.  So under XkbLayout, am I safe changing it to pc104?  And if I was to try a standard US layout, would I delete XkbVariant, or edit intl to standard?  What about the XkbOptions section?  

Any advice on specific edits?  Ie backed it up already.  TIA.

---

