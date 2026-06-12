---
title: "Touchpad Config Overridden"
date: 2014-04-22
forum: Hardware
---

### Post by BaridBelMedar on 2014-04-22
In 13.04 I had a config file /etc/X11/xorg.conf.d/touchpad.conf to set TapButton1=1, TapButton2=2, and TapButton3=3. I did the same thing with 14.04, but the settings get overridden. I've tried moving it to /usr/share/X11/xorg.conf.d/ but that didn't work either.

---

### Post by BaridBelMedar on 2014-04-23
If I manually change the settings by doing
> synclient TapButton2=2
synclient TabButton3=3
the new settings get overridden whenever I switch between the desktop and tty1.
Any idea what could be causing this?

---

### Post by BaridBelMedar on 2014-05-02
bump

---

