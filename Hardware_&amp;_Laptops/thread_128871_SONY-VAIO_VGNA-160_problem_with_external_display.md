---
title: "SONY-VAIO VGNA-160 problem with external display"
date: 2006-02-12
forum: Hardware &amp; Laptops
---

### Post by groban on 2006-02-12
Hi 

i just installed 5.10 in my system. I have this problem. My system comes with  avdock.
when i use the laptop without dock everythnigs fine (sound-display) when i connect the 
dock no sound and i see only a portion of the screen (1200X800 the ATI 1200X1024 the 
external display). 

Any suggestions?

---

### Post by groban on 2006-02-13
This problem solved (other remains see new thread... :( )

I changed /etc/X11/xorg.conf from 1280x800 to 1280x1024 for some
reason it works fine with the external display (the laptop in dock) and
without the dock (laptops display).

Of course when they are working both displays the smaller (laptop)
display only a part of screen (but when you move the mouse it also
moves the screen).

---

