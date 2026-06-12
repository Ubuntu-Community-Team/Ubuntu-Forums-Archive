---
title: "Xinerama Problem with intel 3100"
date: 2007-11-10
forum: Hardware &amp; Laptops
---

### Post by gregorburger on 2007-11-10
Hi guys,

I bought a new notebook with this intel gma 3100. The output works and the resolution is
ok. The problem is that the drivers seems to see another device connected to the notebook
named TV which has a 1024x768 resolution. Therefore my panels and gnome seems to just render into this small resolution. see attachament

A fix to this problem is to disable the TV with:
xrandr --output TV --off 
but its annoying to do that every time. is it possible to deactivate xinerama from within 
xorg.conf? why is the driver seeing another device (TV) which is not connected to the laptop? 

thanks in advance

---

