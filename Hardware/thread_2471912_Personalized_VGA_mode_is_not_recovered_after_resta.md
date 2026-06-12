---
title: "Personalized VGA mode is not recovered after restart"
date: 2022-02-12
forum: Hardware
---

### Post by jmsanders-9 on 2022-02-12
Hi, I'm new.
I started this thread in [askubuntu]("https://askubuntu.com/questions/1358187/new-vga-display-modes-get-lost-when-i-turn-off-restart-computer") to find a solution to repeating "addmode" for VGA monitor procedure every new Ubuntu start/restart.
Where/How can I make this mode permanent?

---

### Post by #&amp;thj^% on 2022-02-12
It has been a minute since I've had to anything like this, but this worked for me.
```
sudoedit /etc/X11/Xsession.d/45custom_xrandr-settings 
```
And Add your settings:
```
xrandr --newmode "1368x768_60.00"   85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync

xrandr --addmode VGA-1-1 1368x768_60.00
```
Save and exit: If those are still you desired settings
EDIT: Forgot to add "45custom_xrandr-settings" will be the new file name.

---

### Post by jmsanders-9 on 2022-02-13
Thanks!!! it worked super well. :KS

---

