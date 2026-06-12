---
title: "HELP:  ATI 9500 w/LCD and HDTV on hoary"
date: 2005-01-21
forum: Hardware &amp; Laptops
---

### Post by vettejock99 on 2005-01-21
Greetings all,

I think I have finally found the distro for me.  After trying over a dozen, I saw that the latest Hoary release was out and I jumped on it.  By default, Ubuntu seems to working fine with my ATI 9500 Pro and the LCD monitor hooked to it.  However, I also have an ATI DVI to component adapter on it which goes to my Hitachi HDTV ready TV.  It works fine on Windows XP, but I am desperately trying to move off of that.  

Anyway, I have downloaded the latest ATI driver from the 17th and all other updates via package manager, and I've edited my xorg.conf, but still no go.  All I get on the TV is a black screen.

Does anyone have a working config they can post?  I could also use one point of clarification.  From my experience, the regular D-Sub analog connector is treated as display 0 (primary) and the DVI port is display 1 (secondary) if they are both plugged in.  My linux research seems to state that if the DVI and D-sub are connected, Linux treated the DVI as display 0.  Is this correct? 

Thanks for any help.

Mark

---

### Post by poofyhairguy on 2005-01-21
[QUOTE=vettejock99]Greetings all,

I think I have finally found the distro for me.  After trying over a dozen, I saw that the latest Hoary release was out and I jumped on it.  By default, Ubuntu seems to working fine with my ATI 9500 Pro and the LCD monitor hooked to it.  However, I also have an ATI DVI to component adapter on it which goes to my Hitachi HDTV ready TV.  It works fine on Windows XP, but I am desperately trying to move off of that.  

Anyway, I have downloaded the latest ATI driver from the 17th and all other updates via package manager, and I've edited my xorg.conf, but still no go.  All I get on the TV is a black screen.

Does anyone have a working config they can post?  I could also use one point of clarification.  From my experience, the regular D-Sub analog connector is treated as display 0 (primary) and the DVI port is display 1 (secondary) if they are both plugged in.  My linux research seems to state that if the DVI and D-sub are connected, Linux treated the DVI as display 0.  Is this correct? 

Thanks for any help.

Mark[/QUOTE]


have you installed the atitvout package? Its in the universe.

---

### Post by vettejock99 on 2005-01-21
No, I haven't done that, but I will as soon as I get home tonight.  Does it help with enabling/configuration?

---

### Post by vettejock99 on 2005-01-22
I got atitvout, but when I run it and force it to radeon mode, it just says that it failed to detect the adapter type.  Also, it references sfree86 a lot, but not xorg.  Even if I can get it to work will it help with my xorg.conf?

---

### Post by vettejock99 on 2005-01-23
So, I am still stuck, and one of my original questions remains.  Does Linux treat the device plugged into the analog connector (usually a monitor) as the primary device or the secondary device if both connections are plugged in?

---

