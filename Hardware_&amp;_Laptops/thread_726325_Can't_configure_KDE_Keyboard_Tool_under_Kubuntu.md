---
title: "Can't configure KDE Keyboard Tool under Kubuntu"
date: 2008-03-16
forum: Hardware &amp; Laptops
---

### Post by sakovias on 2008-03-16
I have installed Kubuntu 7.10 on my Dell Inspiron 1420 laptop. In the KDE Keyboard Tool I have enabled two layouts "us" and "ru". Under the tab "Xkb Options" I have chosen "Ctrl+Shift changes group". I cannot switch layout from keyboard, but clicking on icon works fine :confused:

Modifying /etc/X11/xorg.conf as

	Option		"XkbModel"	        "pc104"
	Option		"XkbLayout"	"us,ru(winkeys)"
	Option		"XkbVariant"	"ru"
	Option		"XkbOptions"	"grp:ctrl_shift_toggle,grp_led:scroll"

and uncommenting in /etc/X11/xkb/rules/xfree86 the following lines:

! $nonlatin = am ara ben bd bg bt by cs deva ge gh gr guj guru il \
              in ir iku jp kan kh kr la lao lk mk mm mn mv mal ori pk \
              ru scc sy syr tel th tj tam ua uz

helps to switch from keyboard, however, language icon remains the same.

Are this two approaches working independently?

This issue related to KDE was raised many times, but I do not really understand what is going on. Maybe I should specify another keyboard type or modify another files.

Thank you!

---

### Post by sakovias on 2008-03-17
Something overrided my xorg.conf settings, now I have

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"en,ru(winkeys)"
	Option		"XkbVariant"	"ru"
	Option		"XkbOptions"	"grp:ctrl_shift_toggle,grp_led:scroll"
EndSection

The Ctrl+Shift switch is still not working, moreover the russian layout is not working properly for all the keys.

---

### Post by sakovias on 2008-03-17
Since I was unable to prevent Kontact crashing on load, I've decided to switch from Kubuntu 7.10 to the standart Ubuntu 7.10. I was very surprised how easy it is to customize everything on this distro. So the configuration of two keyboard layouts was not a problem.

The xorg.conf now shows

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Why :confused:

---

