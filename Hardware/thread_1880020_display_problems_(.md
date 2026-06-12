---
title: "display problems :("
date: 2011-11-12
forum: Hardware
---

### Post by awyk on 2011-11-12
hi guys, today I decided to install ubuntu after hearing such good things about it, I found a spare computer which was running windows 7 and installed ubuntu on a separate partition however the problem is that the highest resolution I can use is way below the 1680x1050 which I normally use with this monitor is there anything I can do?

[IMG]http://i43.tinypic.com/20j070o.png[/IMG]

---

### Post by MoreOrLess on 2011-11-12
Pastebin your /var/log/Xorg.0.log

---

### Post by awyk on 2011-11-12
[http://pastebin.com/GiMDV624](http://pastebin.com/GiMDV624)
there you go

---

### Post by MoreOrLess on 2011-11-12
I personally don't know much about the nvidia binary driver, but I know this is pretty common:
```
[  4195.015] (WW) NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
[  4195.015] (WW) NVIDIA(0):     from CRT-0's EDID.
```
If you can't figure it out from google, then another nvidia user should be able to help you.

---

### Post by awyk on 2011-11-12
thanks for the help anyway ill be sure to keep you posted :)

edit.
well no luck seems like ill have to google a bit more or wait until someone else can come along.

---

