---
title: "multi monitor support?"
date: 2004-10-12
forum: Hardware &amp; Laptops
---

### Post by hoosfoos on 2004-10-12
Is there any chance of multimonitor support appearing in ubuntu?  Is it possible to get a package with Xinerama or iss it not that easy?  My setup works ok (except for nothing on my second display) now and I hate to mess it up if it involves mucking around with X86 config file.

---

### Post by joebaker on 2007-08-09
This is still badly needed.  I don't think we should rely on proprietary ATI or NVIDIA drivers for this functionality.  We have the ability to do multiple monitors in X Windows.  It would be helpful if the developers used the free X drivers  to accomplish the dual headed features that are needed from laptops using free software.  Laptops are a big opportunity here.  Many allow both the LCD and the external monitor jack to operate simultaneously independent from each other.

-Joe Baker

---

### Post by eentonig on 2007-08-09
Gutsy Gibbon is bringin the answer.

---

### Post by leohart on 2007-08-09
For both ATI and nVidia, you should find decent command-line and GUI tools to help you configure your dual-monitor. However, Gutsy is coming quite soon so you might want to camp out for it.

---

### Post by Syke on 2007-08-09
What brand of video card do you have?

Intel: Xinerama and some xorg.conf tweaking and you should be good to go.
Nvidia: Nvidia's drivers have a nice GUI that'll do it all for you.
ATI: I can't talk to you.

One of the chief goals of Gutsy is to fix this complication and provide the GUI config for everyone. Help is coming!

---

### Post by Beuntje on 2007-08-10
For some detailed description on how to make Ubuntu auto detect an external monitor.

[http://ubuntuforums.org/showthread.php?p=3167545#post3167545](http://ubuntuforums.org/showthread.php?p=3167545#post3167545)

---

