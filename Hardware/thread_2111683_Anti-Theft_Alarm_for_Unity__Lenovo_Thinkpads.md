---
title: "Anti-Theft Alarm for Unity / Lenovo Thinkpads"
date: 2013-02-02
forum: Hardware
---

### Post by jeremybmerrill on 2013-02-02
I built an anti-theft alarm for Lenovo Thinkpads running Ubuntu and Unity.

The alarm uses the Hard Drive Active Protection System present in some Lenovo (and maybe Apple?) laptops. The alarm piggybacks on the HDAPS's accelerometer to detect changes in the laptop's position. When the position changes by more than a given threshold, the alarm beeps loudly. If the position moves a little bit, the alarm gives a small warning beep.

The alarm is an applet for Ubuntu's Unity desktop environment, though it could be trivially adapted to other desktop managers like GNOME, XFCE or KDE. (Ping me if you need help on that.) I use the tp_smapi kernel module to interface with HDAPS.

Check it out on [GitHub]("http://github.com/jeremybmerrill/hdaps_theftalarm") and feel free to let me know if you have pull requests, bugs, or need help installing. If I figure out how to package .debs, I will eventually submit this as a package to Ubuntu's powers-that-be. 

Obviously, it's open source: GPL3 and MIT.

Thanks to Janitha for the [original alarm code]("http://www.janitha.com/archives/136").

---

