---
title: "Dell Keyboard stop working after 3-5 minutes"
date: 2008-05-30
forum: Hardware
---

### Post by RRFarFar on 2008-05-30
Hie to everybody,
It seems to me that the constant flow of problems that upgrade brings to users will never stop. Anyway I will continue to use Ubuntu...
HERE IS THE PROBLEM:
After some recent updates coming from Ubuntu repositories I am unable to use my keyboard. The thing is that it stops working after 3-5 minutes after the system boots. Before that I had the problem of layout switching, but solved that long time ago, by manually editing xorg.conf. For my Dell Inspiron 640M I have the following setting in xorg.conf: generic keyboard 105 international, and british english plus russia layouts viat alt-shift. 
Does anyone know what happened??
Thanks to everybody

---

### Post by lisati on 2008-05-30
> **RRFarFar said:**
> Hie to everybody,
It seems to me that the constant flow of problems that upgrade brings to users will never stop. Anyway I will continue to use Ubuntu...
HERE IS THE PROBLEM:
After some recent updates coming from Ubuntu repositories I am unable to use my keyboard. The thing is that it stops working after 3-5 minutes after the system boots. Before that I had the problem of layout switching, but solved that long time ago, by manually editing xorg.conf. For my Dell Inspiron 640M I have the following setting in xorg.conf: generic keyboard 105 international, and british english plus russia layouts viat alt-shift. 
Does anyone know what happened??
Thanks to everybody

Is it the standard keyboard built into the machine or is it a USB keyboard? Sometimes USB keyboards (and mice) need a few tweaks in the settings.

---

### Post by RRFarFar on 2008-05-30
it is a standar keyboard with buttons for Dell MediaDirect in front. It worked before, not its dead((((

---

### Post by RRFarFar on 2008-06-06
Here is my xorg.conf

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb, ru"
	Option 		"XkbVariant" 	",winkeys"
	Option 		"XkbOptions" 	"grp:alt_shift_toggle,grp_led:scroll"
EndSection

Please anybody help, I do not want to install my system once again((((

---

### Post by l4lucas on 2008-11-07
I am having the same problem on my dell studio 17. I have to type this quick before it freezes up again!

---

