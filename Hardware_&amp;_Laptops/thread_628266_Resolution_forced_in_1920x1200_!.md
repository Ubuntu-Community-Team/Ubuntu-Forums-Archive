---
title: "Resolution forced in 1920x1200 !"
date: 2007-12-01
forum: Hardware &amp; Laptops
---

### Post by jb084 on 2007-12-01
Hello.

I'm a french new user of ubuntu, and I met a problem with my screen resolution.

Hardware : 
Barebone Asus TIII P5G965A  Intel G965 Express
2Go RAM
Intel E2180
Samsung 206BW 20" Wide

Since the beginning, Ubuntu (even with the live CD) doesn't want to remain in 1680x1050 : when i put this resolution in the panel, it "outflows" on the sides : I only have the center of my desktop (which is nomal, seen that my screen can't bear 1920x1200 !)

I searched a lot, and with the help of the community, i found in my Xorg.log : 
```
(II) intel(0): Output VGA connected
(II) intel(0): Output VGA using initial mode 1680x1050
(...)
(II) intel(0): [drm] init sarea width,height = 1920 x 1200 (pitch 1920) 
```

NB : The log file (.txt) is available  here : [http://dl.free.fr/hCdEgbTFX/Xorg.txt](http://dl.free.fr/hCdEgbTFX/Xorg.txt)

As far as I can understand this "thing" ;), I get that the system (more accurately, the "drm" module change automatically my resolution in 1920 x 1200 !

I can't figure out why it's doing it ! Now I am in 1280x1024, waiting for improvements, but  the result is crappy !
I really need your help. I must solve this case, and format my XP partition right after :D

Thanks a lot !

---

### Post by jb084 on 2007-12-01
I just found another suspect line

```
(II) intel(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
```

Does it help you ?

---

### Post by xzero1 on 2007-12-01
This link should help:
[http://wiki.x.org/wiki/FAQVideoModes]("http://wiki.x.org/wiki/FAQVideoModes")

---

