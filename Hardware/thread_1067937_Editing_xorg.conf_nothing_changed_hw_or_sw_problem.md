---
title: "Editing xorg.conf nothing changed hw or sw problem?"
date: 2009-02-12
forum: Hardware
---

### Post by -{Luther}- on 2009-02-12
Hi, first of all sorry for my bad english, I hope (even for me;))you will understand.
I have to ask a very particular question
I use Xubuntu on a old PIII with a (very old) "S3 savage 4 140 TV" video card. I've bought a HP w19ev monitor. I've edited /etc/X11/xorg.conf in order to change resolution from 4:3 to 16:10 that is better for my new monitor  
After being edited nothing changed on the screen it is still 800x600..
This is a part of my xorg.conf
```
Section "Monitor"
	Identifier	"HP w19ev"
	Modeline "960x600"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"HP w19ev"
	Device		"S3 savage 4 SDRAM 140 TV rev 1.2"
	DefaultDepth    24 
	SubSection “Display”
	 Depth        1
	 Modes        “960×600&#8243;
	EndSubSection
	SubSection “Display”
	 Depth        1
	 Modes        “960×600&#8243;
	EndSubSection
	SubSection “Display”
	 Depth        4
	 Modes        “960×600&#8243;
	EndSubSection
	SubSection “Display”
	 Depth        8
	 Modes        “960×600&#8243;
	EndSubSection
	SubSection “Display”
	 Depth        15
	 Modes        “960×600&#8243;
	EndSubSection
	SubSection “Display”
	 Depth        16
	 Modes        “960×600&#8243;
	EndSubSection
	SubSection “Display”
	 Depth        24
	 Modes        “960×600&#8243;
	EndSubSection
	EndSection

	EndSection
``` 
The question is: 
1- is it possible (even forcing) to chage resolution with my videocard?
2- if it is possible, also with a low resolution, how can i do it?

Tnx a lot to all those who will help me..

---

