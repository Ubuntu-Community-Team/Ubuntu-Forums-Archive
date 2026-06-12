---
title: "[SOLVED] Strange desktop with Acer AL1916W, Radeon 9200, 1490x900"
date: 2007-12-28
forum: Hardware &amp; Laptops
---

### Post by silent82 on 2007-12-28
Hello,
please look at the image below.
[IMG]http://www.lorenzoferrara.net/files/radeon-9200_acer-al1916w_1440x900/radeon-9200_acer-al1916w_1440x900.jpg[/IMG]

I've tried many configurations but none worked. 
The mouse can flow all over the screen. If I watch a video inside the gnome desktop it will not show, but if I moove the mediaplayer window outside the gnome desktop, I can see the video (that is while playing). If I maximize a window inside the gnome desktop, the window will fit only the gnome desktop area. If the window is located outside the gnome desktop area and it's maximized, the window will cover the whole screan.

This is my xorg.conf
[http://www.lorenzoferrara.net/files/radeon-9200_acer-al1916w_1440x900/xorg.conf]("http://www.lorenzoferrara.net/files/radeon-9200_acer-al1916w_1440x900/xorg.conf")

I'm using Ubuntu 7.10 on a i386.

Thanks!!

---

### Post by silent82 on 2007-12-28
Sorry, the title shoud be changed to "Strange desktop with Acer AL1916W, Radeon 9200, 1440x900". 1490x900 is wrong.

---

### Post by silent82 on 2007-12-29
SOLVED!
Thanks to the program xrandr, I was able to see that there ware two video output: VGA-0 and LVDS.

So I was able to fix the problem disabling LVDS using xrandr:
```
xrandr --output LVDS --off
```

Since I don't know how to disable permanently LVDS in xorg.conf, I added
```
xrandr --output LVDS --off
```
in the file /etc/gdm/Init/Default, just before
```
exit 0
```

Thanks goes to Ori_B from #xorg channel on freenode.net irc chat! Thanks Ori_B!

---

