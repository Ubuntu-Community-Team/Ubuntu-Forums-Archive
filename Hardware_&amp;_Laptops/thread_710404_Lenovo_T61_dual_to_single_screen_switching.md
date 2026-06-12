---
title: "Lenovo T61 dual to single screen switching"
date: 2008-02-28
forum: Hardware &amp; Laptops
---

### Post by cujo on 2008-02-28
Basically my question is the same as this one: [http://ubuntuforums.org/showthread.php?t=274618](http://ubuntuforums.org/showthread.php?t=274618) but that hasn't been addressed in over a year so I'm starting a new thread.

I have a laptop that I hook an external monitor up to when I'm working at home.  However, with it being a laptop, I also like to unhook it from said monitor and use it on the go.  When I'm connected to the 2nd monitor, I use xinerama to span my desktop across both.  This setup has its own xorg.conf file.

When I'm disconnected from that other monitor, I have to use a seperate xorg.conf file.  At the moment that means I have to do a lot of file switching when I plug in/unplug.  Plus I then have to restart X to get the new settings which involves restarting all my programs.

Is there a better way?

---

### Post by Yellow Pasque on 2008-02-28
Use xrandr to do multi-monitor on the fly?
[http://www.thinkwiki.org/wiki/Intel_Graphics_Media_Accelerator_X3100](http://www.thinkwiki.org/wiki/Intel_Graphics_Media_Accelerator_X3100)

---

### Post by 5h4rk on 2008-03-29
I´d like to have the answer for this question too. I´m using nvidia-setting and everything work fine until I unplug the external LCD.

Anyone?

---

