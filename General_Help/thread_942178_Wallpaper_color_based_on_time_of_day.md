---
title: "Wallpaper color based on time of day"
date: 2008-10-08
forum: General Help
---

### Post by picopir8 on 2008-10-08
I really like the Fedora wallpapers that change colors throughout the day.  Has anyone got them (or something similar) working in ubuntu?

---

### Post by airtonix on 2008-10-09
i havent seen these wallpapers you mention but i do know that if you use a png wallpaper with transparent areas then you can use the colour settings in the wallpaper choose to create a colour fill for those transparent areas.

I also know that these settings are available for you to change via the gconf, which is able to be manipulated via the command-line.

so by using bash script that is run by cron every half hour or so, your script would output a colour code depending on what hour of the day it is for gconf to change to.

---

### Post by GordonTGopher on 2008-10-09
[http://ubuntuforums.org/showthread.php?t=784881](http://ubuntuforums.org/showthread.php?t=784881) should help you on your way!

Gordon

---

