---
title: "Changing /etc/gdm/Init/Default has no effect"
date: 2008-11-01
forum: General Help
---

### Post by wermeulen on 2008-11-01
Upgraded to 8.10 yesterday. I need to add a script to /etc/gdm/Init/Default, to fix my resolution post login. But it appears not to be executed? Where can I trace logging of this, or debug it or something.

Manually start of the script works fine, file and dir are mod 755 so help a newbie please :confused:

Why do I need it? On my setup 1280x1024 resolution is still not being detected and xorg.conf hacking doens't help, see [this]("http://ubuntuforums.org/showthread.php?t=690673") thread for history. My workaround is to put following in a script and call it just before the last exit 0 in /etc/gdm/Init/Default to force my display to proper resolution. Or perhaps I can also do that somewhere else?
```
#!/bin/sh
xrandr --newmode "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync
xrandr --addmode TMDS-1 "1280x1024_60.00"
xrandr --output TMDS-1 --mode "1280x1024_60.00"
```

---

### Post by wermeulen on 2008-11-14
Solved the problem; use Xsession to change your resolution.

Put the code in /etc/X11/Xsession.d/45fixresolution and make it executable. This automatically runs once X11 is started and fixes my resolution before GNOME is started.

---

