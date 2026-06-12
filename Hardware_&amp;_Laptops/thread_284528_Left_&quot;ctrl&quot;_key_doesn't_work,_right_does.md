---
title: "Left &quot;ctrl&quot; key doesn't work, right does work"
date: 2006-10-25
forum: Hardware &amp; Laptops
---

### Post by BlueStreak on 2006-10-25
As above, my left ctrl key suddenly doesn't work.  It's likely a hardware problem but is there anything I can check to see if the key isn't mapped correctly or something?  Thanks

---

### Post by nathan30 on 2007-01-01
I'm experiencing the same problem. But my left shift doesn't work either. I installed keytouch to make my trust easy scroll keyboard work, but now i have to deal with this problem. I'm not getting any further with this problem. I know about the xorg.conf file and i changed my keyboard from pc101 tot 102 to 103 and 104 but that doesn't seem to work. Did you find out something about your problem. Is there any direction i have to search?

---

### Post by tweedledee on 2007-01-06
> **nathan30 said:**
> I'm experiencing the same problem. But my left shift doesn't work either. I installed keytouch to make my trust easy scroll keyboard work, but now i have to deal with this problem. I'm not getting any further with this problem. I know about the xorg.conf file and i changed my keyboard from pc101 tot 102 to 103 and 104 but that doesn't seem to work. Did you find out something about your problem. Is there any direction i have to search?

You could try use xmodmap and/or xbindkeys to remap your non-working key to your working key.  First use xev (open a terminal and type "xev", then press the keys and check the output) to see if the system even recognizes the keypress; if it does not, then you may have a problem with your keyboard not being correctly recognized or using the wrong layout.

---

### Post by psychok9 on 2008-05-04
Same problem on Ubuntu 8.04, Wine and World of Warcraft.
Xev say Left control work... but don't work on the game.

---

### Post by daMage on 2008-05-12
I have the same problem. Actually my left shift doesn't work either in WoW... Works fine in other places...

---

### Post by papaganoush on 2008-06-24
I had the same problem but resolved it by going to System -> Preferences -> Mouse and turning off the "Locate Pointer" option.

Papaganoush

---

