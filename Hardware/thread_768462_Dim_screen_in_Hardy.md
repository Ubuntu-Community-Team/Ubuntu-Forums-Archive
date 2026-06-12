---
title: "Dim screen in Hardy"
date: 2008-04-26
forum: Hardware
---

### Post by turnpin on 2008-04-26
Just installed Hardy and my laptop LCD is now very dim.  The brightness is fine while it is booting and drops way down part wy into the graphical part of the boot.

---

### Post by NilsE on 2008-04-26
> **turnpin said:**
> Just installed Hardy and my laptop LCD is now very dim.  The brightness is fine while it is booting and drops way down part wy into the graphical part of the boot.The first recommendation I have is to go into System > Preferences > Power manager and check to see if any of the LCD settings are checked for dimming the display. Then check power manager settings in the Configuration editor under apps > gnome-power-manager for settings there relating to the LCD

---

### Post by turnpin on 2008-04-26
OK thanks, it seems my ambient light sensing was being a bit over-zealous.

I've turned it off for now in gconf-editor app/gnome-power-manager/ambient.

I'll tinker with it to get the levels right later when I get a chance.


UPDATE: it turns out this didn't fix it see next post

---

### Post by turnpin on 2008-04-27
It turns out that there is a [known bug]("https://bugs.launchpad.net/ubuntu/+bug/219463") with my ASUS Z71V.

I used the workaround from [this thread]("http://bbs.archlinux.org/viewtopic.php?id=38935") to set the brightness

---

