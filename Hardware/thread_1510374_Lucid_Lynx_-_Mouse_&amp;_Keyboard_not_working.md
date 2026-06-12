---
title: "Lucid Lynx - Mouse &amp; Keyboard not working"
date: 2010-06-15
forum: Hardware
---

### Post by littlboz on 2010-06-15
Upon booting mouse and keyboard work for a short duration, sometimes it works on optimum level though. If I speedily type in my password it will go through and then freeze before logging.

This appears to be a know problem I was wondering if there was a fix [http://www.uluga.ubuntuforums.org/showthread.php?t=1442724](http://www.uluga.ubuntuforums.org/showthread.php?t=1442724)


Edit: My deepest apologies, I forgot that I did not update this computer, I am running on Karmic Koala :-p. My bad.

Still have the problem though

---

### Post by littlboz on 2010-06-17
bump

---

### Post by charismaticjoshi on 2010-10-03
> **littlboz said:**
> Upon booting mouse and keyboard work for a short duration, sometimes it works on optimum level though. If I speedily type in my password it will go through and then freeze before logging.

This appears to be a know problem I was wondering if there was a fix [http://www.uluga.ubuntuforums.org/showthread.php?t=1442724](http://www.uluga.ubuntuforums.org/showthread.php?t=1442724)


Edit: My deepest apologies, I forgot that I did not update this computer, I am running on Karmic Koala :-p. My bad.

Still have the problem though
Even I am facing this problem after upgrading to Ubuntu 10.04. Sometimes it resolves automatically if you wait 2-3 minutes. Some times it gets resolved by "moving between graphical and text shells"  alt+ctrl +F1 and alt+Ctrl+F7. I guess some hung thread!!!!

---

### Post by Unkuiri on 2011-01-16
Have you tried this:

> gconftool -s /desktop/gnome/peripherals/touchpad/touchpad_enabled -t boolean true

killall gnome-session

---

