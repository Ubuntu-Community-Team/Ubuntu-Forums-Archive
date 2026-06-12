---
title: "left-hand USB mouse + right-hand touchpad in 8.04?"
date: 2009-01-25
forum: Hardware
---

### Post by PeregrinGo on 2009-01-25
Hi all,

I have a Dell XPS m1530 laptop that I have been running Hardy on for about 5 months. I have tendonitis in my right elbow, so I prefer to use a left-hand USB mouse configuration. BUT, when I'm not using the mouse, I want the touchpad to be configured with the regular right-hand configuration. It's a pain if you have to re-configure the mouse settings every time. Does anyone know if you can do the left-hand USB, right-hand touchpad combination???

---

### Post by PeregrinGo on 2009-11-14
Bump

---

### Post by PeregrinGo on 2010-02-03
*bump*

---

### Post by mavicdog on 2011-01-05
> **PeregrinGo said:**
> Hi all,

I have a Dell XPS m1530 laptop that I have been running Hardy on for about 5 months. I have tendonitis in my right elbow, so I prefer to use a left-hand USB mouse configuration. BUT, when I'm not using the mouse, I want the touchpad to be configured with the regular right-hand configuration. It's a pain if you have to re-configure the mouse settings every time. Does anyone know if you can do the left-hand USB, right-hand touchpad combination???


With every "upgrade" I have to reconfigure this. Usually it involves modifying xorg.conf but with the latest 10.10 it just does not work. xorg.conf has nearly disappeared...does anyone know how to do this?

---

### Post by mavicdog on 2011-01-05
Go figure - after 3 weeks of searching I found a workable solution here:
[http://ubuntuforums.org/showthread.php?t=1325508](http://ubuntuforums.org/showthread.php?t=1325508)

just reverse the button mapping for right hand or left hand touchpad.  Keep the USB mouse settings to right or left as desired via the gui tool in preferences.

---

