---
title: "Aspire backlight won't switch off with power saving options"
date: 2010-10-25
forum: Hardware
---

### Post by hjaddad on 2010-10-25
I'm having problems with my laptop backlight on my Acer Aspire 5100 running Ubuntu 32bit 10.10: The backlight won't switch off according to power management settings. The display goes black like it should, but the light stays on. 

Command "**xset dpms force off**" works just fine and the light turns off. So does Fn+F5 combination and closing the lid, but I want that light to turn off automatically like it did on win xp.


I actually even tried and edited one of the screensavers to make it execute the command:

/usr/share/applications/screensavers/glblur.desktop 
```
[Desktop Entry]
Name=glblur
Exec=/usr/bin/xset dpms force off
TryExec=/usr/bin/xset
Comment=Turn off backlight
StartupNotify=false
Terminal=false
Type=Application
Categories=GNOME;Screensaver;
OnlyShowIn=GNOME;
```

...and copied all this into */usr/share/applications/desktop.*_*.utf8.cache* as well to make it update the settings. 

But this does not turn off the backlight when the screensaver delay has passed. Screen does slowly fade to black (like with all the screensavers) but the backlight stays on ](*,)


So, 

*** How can I fix the power saving function so that it would also turn off the backlight?**

or

*** How could I set [COLOR="Red"]*xset dpms force off*[/COLOR] to run when the computer has been idle for some time? cron?**

or

*** How can I make [COLOR="#ff0000"]*xset dpms force off*[/COLOR] work from a screensaver file?**


I'm getting really desperate with this.. :(

---

### Post by hjaddad on 2010-10-26
Exactly the same problem with 10.04 here:
[INDENT][http://ubuntuforums.org/showthread.php?t=1481616](http://ubuntuforums.org/showthread.php?t=1481616)[/INDENT]

..but so far my problem hasn't solved itself :sad:

---

### Post by odzk on 2010-10-26
same problem with my acer 3620 any ideas guys?

---

