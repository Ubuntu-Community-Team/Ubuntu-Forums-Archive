---
title: "CMStorm Devastator keyboard doesn't light up ..."
date: 2015-10-15
forum: Hardware
---

### Post by GameGuru on 2015-10-15
When I switched over to Ubuntu I lost the ability to light my keyboard by pressing the Scroll Lock key.  I found a work around of typing "sudo xmodmap -e 'add mod3 = Scroll_Lock'" into Terminal every time I boot but I would like this to happen automatically.  How do I make this happen?

---

### Post by GameGuru on 2015-10-16
Anyone please?

---

### Post by ccanaria on 2016-10-03
> **GameGuru said:**
> Anyone please?

Please refer to: [https://ubuntuforums.org/showthread.php?t=2208222](https://ubuntuforums.org/showthread.php?t=2208222)

[COLOR=#333333][FONT=Ubuntu]*Create file /etc/xdg/autostart/backlight.desktop*[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]*Edit the file so it looks something like this:*[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]*[Desktop Entry]*[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]*Type=Application*[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]*Name=Devastator Backlight*[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]*Exec=xset led 3*[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]*Icon=system-run*[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu][I]X-GNOME-Autostart-enabled=true

HTH.


[/I][/FONT][/COLOR]

---

