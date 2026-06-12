---
title: "new monitor, new trackball - where to change"
date: 2005-08-05
forum: Hardware &amp; Laptops
---

### Post by yhotg on 2005-08-05
hi i have a new NOC monitor and a new logitech trackball
and couldn't find where to change the setup and configuration.
in the display configuration in kde i have a resolution of 800 x 600
so how to change the monitor model and resolution?
and how to change the type of trakball/mouse?
i had a 3 buttons 2 wheels and now i have a:
4 buttons no wheels (2 buttons r suppoused to replace the wheels - un and down buttons)

so where is the administrator's hardware configuration?

thank u
yhotg

---

### Post by foolsh on 2005-08-21
open a terminal and enter

# sudo apt-get install mdetect
# mdetect

that should take care of your mouse
look here for the video thing

[https://wiki.ubuntu.com/FixVideoResolutionHowto](https://wiki.ubuntu.com/FixVideoResolutionHowto)

---

### Post by foolsh on 2005-08-21
[QUOTE=yhotg]
so where is the administrator's hardware configuration?

thank u
yhotg[/QUOTE]

/etc/X11/xorg.conf is where you'll find the settings for the x window system 

 [-X no administrator here just root  [-X

---

