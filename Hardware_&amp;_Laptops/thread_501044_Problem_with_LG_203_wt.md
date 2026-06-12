---
title: "Problem with LG 203 wt"
date: 2007-07-14
forum: Hardware &amp; Laptops
---

### Post by thiagovent on 2007-07-14
Hi.. 

When i install the ubuntu 7.04 my monitor was a LG 710 Flatron 17". 

But, I buy a LG 203 wt (20.1" wide) and I can't modified the resolution. :(

[http://www.lge.com/products/model/detail/l203wt_1_6.jhtml]("http://www.lge.com/products/model/detail/l203wt_1_6.jhtml")

Please.. help me..




PS: I'm very,  very,  very, dummie :P

---

### Post by w4ett on 2007-07-14
From the terminal type:

sudo dpkg-reconfigure xserver-xorg

Select the resolutions you desire...also autodetect your new monitor settings.  Save and restart X
(Ctrl-Alt_Backspace)

---

### Post by thiagovent on 2007-07-16
thank yout, but this not work

This change the /etc/X11/xorg.conf but not addiction in the resolution selecion

i try too:
# vi /etc/X11/xorg.conf

(...)
Section "Device"
	(...)
	Option "ModeValidation" "NoDFPNativeResolutionCheck"
EndSection


And not work too.

If I try ONLY low resolutions (ex: 640x480, 800x600) the commands work...

---

### Post by w4ett on 2007-07-16
What GFX card do you have and what driver are you using?

---

