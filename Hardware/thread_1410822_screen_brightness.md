---
title: "screen brightness"
date: 2010-02-19
forum: Hardware
---

### Post by steffenomak on 2010-02-19
I don't know why but i can't change the screen brightness in ubuntu but it works in windows. I have been searching througout the internet whit google but it haven't been much help.

In any case I tried manuly changing it in /proc/acpo/video/vga/lcdd
but i dont have that folder, insted i have /proc/acpo/video/NGFX/lcd and in the file brightness it says:
not supported. I would really like to be able to change the brightness becouse if i don't the comp eats up the battery to fast.

I have a sony vaio vpccw2s1e

thanks for the help

---

### Post by steffenomak on 2010-02-19
so nobody have had the same problem?

---

### Post by SuaSwe on 2010-02-21
Hi there!

What version of Ubuntu are you using, and what sort of settings do you have in:

System > Preferences > Power Management 

and

Alt+F2 > gconf-editor > apps > gnome-power-management > backlight

?

---

### Post by steffenomak on 2010-02-21
I am using ubuntu 9.10. In System > Preferences > Power Management i cant do much. I cant change the screen brightness, but i can set what happens when I close the lid.

In gconf-editor > apps > gnome-power-management > backlight
it looks like this:

battery_reduced = true
brightness_ac = 100
brigtness_dim_battery = 50
dpms_method_ac = off
dpms_method_battery = off
enable = true
idle_brightness = 30
idle_dim_ac = true
idle_dim_battery = true
idle_dim_time = 10

Just to be on the safe side i will include how my xorg.conf looks like becouse i was forced to change it


Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
	Option "ConnectedMonitor"   "DFP-0,CRT-0"
    	Option "CustomEDID"         "DFP-0:/etc/X11/sony-edid.bin"
EndSection

---

