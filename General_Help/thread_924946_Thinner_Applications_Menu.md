---
title: "Thinner Applications Menu"
date: 2008-09-20
forum: General Help
---

### Post by Bios Element on 2008-09-20
Ok, so I've seen a few themes that have really thin dropdown menu's and really, the only thing keeping me from using the Human theme with Tango icons is because the menu goes to a scroll for the game menu and such. I figure there's a config file somewhere i can edit, But where? I looked but heck, I could spend all year digging through and not find the right file.

Any ideas?

---

### Post by Bios Element on 2008-09-29
Any thoughts on this? I tried looking through the config files for styles but i couldn't really find anything i could understand enough to tinker with. I don't want to have to keep using any styles besides Human and such but i 'have' to have smaller menu's.

---

### Post by Bios Element on 2008-10-03
Finally found the answer. Add 
```
gtk-icon-sizes = "panel-menu=24,24"
```
To /home/USER/.themes/THEMENAME/gtk-2.0 gtkrc and restart or refresh your theme. Change 24,24 to whatever you like. Personally, I like 12,12.

---

### Post by mr_k on 2008-10-13
i tried what u stated here and dosen't work for me, i find right spot to edit and all but meny still same size and it's icons!

---

