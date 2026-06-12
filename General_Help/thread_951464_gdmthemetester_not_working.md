---
title: "gdmthemetester not working"
date: 2008-10-18
forum: General Help
---

### Post by HydroDiOxide on 2008-10-18
I am working on a gdm theme. When I want to try it with gdmthemetester the following happens:

Code:

[me@hip-uncle ~]$ gdmthemetester console Circles

GDM Theme Tester

Be sure to test all the environments:
 console, console-timed, flexi, remote-flexi, xdmcp
Also be sure to test using caps lock


(gdmgreeter:5317): Gdk-WARNING **: cannot open display:

I've tried adding the line below to my /usr/share/gdm/defaults.conf, but that didn't work. Any suggestions?

Xnest=/usr/bin/Xnest -audit 0 -name Xnest

---

