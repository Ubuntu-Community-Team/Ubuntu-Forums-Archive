---
title: "Radeon X1270 supported?"
date: 2011-08-07
forum: Hardware
---

### Post by chrf097 on 2011-08-07
I was curious if the X1270 is supported by 11.04 or if I just needed to download drivers, as I tried to install Ubuntu 11.04 but after I log in all I see is the desktop image. No Unity, No Gnome, just the desktop image! Is my graphics card just a fail or does it just need some drivers?

---

### Post by Basher101 on 2011-08-07
Did you try the ubuntu classic session at the login screen?

---

### Post by chrf097 on 2011-08-07
> **Basher101 said:**
> Did you try the ubuntu classic session at the login screen?
No, I just went straight in as I was really eager to use Unity :/ Am I not going to be able to?

---

### Post by Basher101 on 2011-08-07
I dunno.
To change the session, click on your username and dont type in the password yet. Below you will see somewhere *Ubuntu* click on it and choose Ubuntu classic. That will let you login to gnome 2 shell instead of unity. From there you can try to install drivers

---

### Post by chrf097 on 2011-08-07
> **Basher101 said:**
> I dunno.
To change the session, click on your username and dont type in the password yet. Below you will see somewhere *Ubuntu* click on it and choose Ubuntu classic. That will let you login to gnome 2 shell instead of unity. From there you can try to install drivers

Thank you! I'll have to do it in the morning though seeing my Wi-Fi drivers aren't built in either, but oh well on that one haha

---

### Post by superbatlife on 2011-10-24
11.04 not detecting x1270? ATI needs to correct this. I have to lower screen resolution to 680x480 to watch movies without a nagging lag.

---

### Post by Jondice on 2011-12-11
After looking at several docs and forum posts* I've found the best thing to do is use the radeon driver and then somehow run the following once X is running (ubuntu seems to have ditched .xinitrc and .xsession sadly): 

```

#!/bin/sh
xrandr --newmode 1368x768 64.00  1368 1416 1552 1736  768 771 781 792 -hsync +vsync
xrandr --addmode LVDS 1368x768
xrandr --output LVDS --mode 1368x768

```

*Especially:
Arnt's post:
[http://groups.google.com/group/linux.debian.user/browse_thread/thread/160c41db2f09dcad?pli=1](http://groups.google.com/group/linux.debian.user/browse_thread/thread/160c41db2f09dcad?pli=1)
Vacant's post
[https://bbs.archlinux.org/viewtopic.php?pid=958166](https://bbs.archlinux.org/viewtopic.php?pid=958166)

I still find there is occasional graphical corruption, but it is much less frequent.  Definitely it still needs to be fixed if any devs want to work on it.

---

