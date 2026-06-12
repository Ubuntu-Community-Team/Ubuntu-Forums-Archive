---
title: "Mouse setting"
date: 2005-09-05
forum: Hardware &amp; Laptops
---

### Post by mogh on 2005-09-05
Hello

xev doesnt work with some of my mouse buttons,
the DPI increase, DPI decrease and mouse wheel tilt left&right
-no reaction when i press those.
i use a [logitech G5 laser mouse](http://www.logitech.com/index.cfm/products/details/US/EN,CRID=2142,CONTENTID=10715)

Nothing happens otherwise with the wheel tilts, anywhere. I want to make left tilt work like middle button, etc. But I don't know which numbers they are so I can change it in xmodmap - i suspect the tilts dont work at all.


anyone help?

Edit: I'm sorry for writing this post in such a haste, normally id be more polite.
And yeah Im kinda new to ubuntu.

---

### Post by endy on 2005-09-11
This link here may help, just skip to the section 4, editing the xorg.conf file:

[http://www.linux-gamers.net/modules/wfsection/article.php?articleid=46](http://www.linux-gamers.net/modules/wfsection/article.php?articleid=46)

I use the "evdev" protocol for my Logitech mx510 mouse to get all 10 buttons working properly and use the method outlined in section 6 to have the forward and back buttons on the mouse to work with nautilus. Hopefully this will work for you too :)

I did however have to check "xev" for the mouse button numbers I needed and had to add the absolute path to "xvkbd" in my ~/.xbindkeysrc file after installing xvkbd and xbindkeys.

My example ~/.xbindkeysrc:
```
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
 m:0x0 + b:6
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
 m:0x0 + b:7

```

The relevent section in my xorg.conf:
```
Section "InputDevice"
        Identifier	"Configured Mouse"
        Driver		"mouse"
	Option		"Protocol"		"evdev"
	Option		"Dev Name"		"Logitech USB-PS/2 Optical Mouse"
	Option		"Dev Phys"		"usb-*/input0"
        Option		"Device"		"/dev/input/event0" # (cat /proc/bus/input/devices)
	Option		"Buttons"		"10"
	Option		"ZAxisMapping"		"9 10"
EndSection

```

If you need more help I may write a how to on this because I don't think it's very obvious.

---

### Post by humina on 2005-10-31
I have the same problem as the original poster.  When I try to use my tilt wheel keys, they show up as the same buttons (4 and 5) as my scroll wheel.  I was hoping to change my tilt wheel keys to change browser tabs, but so far I haven't had any luck.  I can get the browser back button to recognize my side button, just not the tilt wheel buttons.

---

