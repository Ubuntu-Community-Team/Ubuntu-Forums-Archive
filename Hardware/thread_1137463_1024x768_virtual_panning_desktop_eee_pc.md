---
title: "1024x768 virtual panning desktop eee pc"
date: 2009-04-25
forum: Hardware
---

### Post by Sheik Yerbouti on 2009-04-25
Hello all,

This is something that I have been struggling with for a long time and never really could get working. I have a Asus eee PC running Jaunty 9.04. It's default resolution is 1024x600. Which is a problem for some games I have installed which want at least 1024x768. On the eee pc under XP you can set virtual resolutions like 1024x768 and it will allow you to play such games. It pans the desktop as you get near the edge of the screen. Now I know that X windows has always had support for panning virtual desktops but damned if I can get it to work with this intel driver.

This Intel driver is the weirdest driver it does not list ANY modes in xorg.conf. It queries the modes via LVDS on startup from the monitor and sets them automagically. Now as neato as that is there does not seem to be a way to control what happens through xorg.conf. So if I ad the syntax Virtual 1024 x 768 in the display section or any other mode info it seems to just get ignored by the driver. I have sorta been able to make a virtual desktop via xrandr and a util called i810pan like this script.

```
/usr/bin/xrandr --newmode "1024x768_60" 64.56 1024 1056 1296 1328 768 783 791 80
7
/usr/bin/xrandr --addmode VGA 1024x768_60
/usr/bin/xrandr --output VGA --mode 1024x768_60
/opt/VGA_Utility/bin/i810pan
```

but it only sorta works the apps don't see it as a valid screen mode and dont use the extra resolution even though the mode changes.

There has got to be an easier way to do this. X windows has historically done virtual desktops brilliantly why is this so hard now?

---

### Post by rbroom on 2009-05-22
Take a look at this thread: [http://ubuntuforums.org/showthread.php?t=1139691&highlight=panning+display](http://ubuntuforums.org/showthread.php?t=1139691&highlight=panning+display)

Which points to this one for the details: [http://ubuntuforums.org/showthread.php?t=1105594](http://ubuntuforums.org/showthread.php?t=1105594)

---

