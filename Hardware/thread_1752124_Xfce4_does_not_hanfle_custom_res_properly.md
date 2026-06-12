---
title: "Xfce4 does not hanfle custom res properly?"
date: 2011-05-07
forum: Hardware
---

### Post by deckoff on 2011-05-07
I managed to makemy machine work in a desired custom resolution 1344X760. When I restart the PC, though, the picture exported to the TV (VGA1) is OK, Xfce4 worksok, but the panels are 1024 pixels wide. On part of the screen only the desktop is shown. All applets are there, and so on, but it just annoys me.
Manually setting lower resolution and then setting the one I want fixes the problem, I might have to do it a few times, though. 
Any ideas how to fix it.
I set 

```
xrandr --newmode "1344x760_60.00" 83.25  1344 1416 1552 1760  760 763 773 790 -hsync +vsync
xrandr --addmode VGA1 "1344x760_60.00"
xrandr --output VGA1 --mode "1344x760_60.00"
```

~/.xprofile , /etc/gdm/Init/Default , and edited my xorg.conf file

---

