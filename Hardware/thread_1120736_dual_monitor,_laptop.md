---
title: "dual monitor, laptop"
date: 2009-04-09
forum: Hardware
---

### Post by ax123man on 2009-04-09
I'm trying to get an external LCD monitor working to the "right-of" my laptop screen. The LCD currently shows up cloned. I tried the gnome "Monitor Resolution Settings" but it always just shows one screen. So I tried using xrandr on the command line:
```

xrandr --output VGA-0 --right-of LVDS

```

and this works. So I set up the script I found at [http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2). When I restart X, at the login screen, VGA-0 is set up "right-of" LVDS. But after logging it, it switches back to cloned. Do I have to disable gnomes "Monitor Resolution Settings" or something?

---

### Post by Sam Lars on 2009-04-10
Are you able to set it up in Gnome's monitor resolution settings?
You could also run that command in a script when you log in.

---

