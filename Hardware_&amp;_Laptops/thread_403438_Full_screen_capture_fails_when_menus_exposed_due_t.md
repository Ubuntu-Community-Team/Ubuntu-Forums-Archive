---
title: "Full screen capture fails when menus exposed due to fn &quot;key+prt scn&quot;"
date: 2007-04-07
forum: Hardware &amp; Laptops
---

### Post by jcronkhite on 2007-04-07
Does anyone know if there is a solution to this?  Basically, I want to perform a screen capture on my full desktop.  However, my print screen button requires the fn key to function.  This works fine so long as I do not expose a panel menu (such as Applications, Places, etc.).  While the menus are down, print screen does not show up.  Strange, huh?  Does anyone else have this issue?  Has anyone else even tried this under these circumstances?

I'm using Feisty fully updated/upgraded on a hp Pavilion zd8205us.  Thanks all for your input!

---

### Post by heimo on 2007-04-07
Hi. I tried it and it behaves just like you described.  If I have Applications menu or Firefox menu open, screenshots with gnome-screenshot (by pressing default shortcut key Print Screen), don't work. Mapping to another key, doesn't solve it. Using Gimps File->Acquire->Screenshot is a workaround. Or using gnome-screenshots --delay switch.
```
gnome-screenshot --delay 5
```


EDIT: Heh, found this one via Google, the same solutions were already suggested on Ubuntuforums:
[http://ubuntuforums.org/showthread.php?t=95648](http://ubuntuforums.org/showthread.php?t=95648)

---

### Post by klytu on 2007-04-10
This was just what I needed, too!

---

