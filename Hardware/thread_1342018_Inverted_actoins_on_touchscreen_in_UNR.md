---
title: "Inverted actoins on touchscreen in UNR"
date: 2009-11-30
forum: Hardware
---

### Post by matt.beddow on 2009-11-30
Hi
Ive just installed UNR onto my eeepc 701 that i was previously running xp on with a touchscreen.
The recomended drivers from the site I bought the kit off are the eGalaxTouch32 drivers.
This comes with a script to install it but it failed due to the lack of a /etc/X11/xorg.conf file.
I tried adding a blank file and it didnt work.
On another site it recomended I added the xserver-xorg-input-evtouch package then used the touchscreen calibration tool which i did.
This then made my touch screen work to some degree. Up and down works fine but Left and right are inverted (ie when i touch the left the mouse moves right and visa versa)
Anyone got any ideas how to fix it?
Thanks

---

### Post by shihkster1015 on 2010-02-23
when you add an empty xorg.conf, also add a comment line (using the #).
and use the stock calibrator that came with the egalax software

---

