---
title: "touchscreen drivers"
date: 2006-09-21
forum: Hardware &amp; Laptops
---

### Post by otherguy on 2006-09-21
I just installed xubuntu (2006-06-01) onto my Fujitsu Stylistic LT c-500. I've used linux a number of times before, but never installed it myself (big step).
Everything seems to be working for the most part other than the touch screen.
I was able to find the drivers [here]("http://linuxslate.com/software.html"), and a guide on how to get the hardware working [here]("http://www.neurath.org/stylistic_lt_c500/Configuration-touchscreen.html"), but I'm having trouble following the guide.

For example, the first part of the instructions say to add something to a startup script "/etc/init.d/setserial" which i dont appear to have on my machine.
Same goes for the directory they suggest copying the drivers into "/usr/X11R6/lib/modules/input/"

Could someone help me through this or link me to some documents that will aid me?

Thanks in advance,
Jim

---

### Post by orengolan on 2007-06-26
I have the same issue. I can't find this folder - /usr/X11R6/lib/modules/input.

this is the link - [http://www.conan.de/](http://www.conan.de/)

---

### Post by Gfiles on 2007-09-22
In Ubuntu the location for the drivers that X will use is "/usr/lib/xorg/modules/input/".

If you need the evtouch drivers this is a good page "http://www.conan.de/lifebook".

---

