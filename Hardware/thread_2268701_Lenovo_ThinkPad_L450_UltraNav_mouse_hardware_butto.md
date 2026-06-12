---
title: "Lenovo ThinkPad L450: UltraNav mouse hardware buttons do not click but scroll"
date: 2015-03-10
forum: Hardware
---

### Post by abedbyde on 2015-03-10
Hello everyone,
I have a Lenovo ThinkPad L450 with a UltraNav Touchpad 3+2 buttons. You can see in the attached image. The problem is that the three hardware mouse buttons do not work correctly. The two mouse buttons integrated in the touchpad do work.
The left click button scrolls up, the middle button does not do anything and the right click button scrolls down. I have checked the settings in "Mouse and  Touchpad" and "Pointing devices" but I could not get the left and right buttons to do normal mouse clicks and the middle one to enable scrolling.
Does anyone know what to do? 
Thank you very much! :D

---

### Post by georgf-d on 2015-03-12
HI there, 

i got the same Notebook and Arch Linux installed, but the Workaround should be the same:



```


$ sudo rmmod psmouse
$ sudo modprobe psmouse proto=imps


```

If anyone got both Working, the Trackpoint and the Touchpad, let me know...

OK if found a Solutiuon: look over here, it works with my L450: 
[URL="http://vimtips.org/2015/02/20/ubuntu-1410-and-lenovo-thinkpad-x250/"]http://vimtips.org/2015/02/20/ubuntu-1410-and-lenovo-thinkpad-x250/
[/URL]
Regards,

Georg

---

