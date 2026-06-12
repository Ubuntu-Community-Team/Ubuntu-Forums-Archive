---
title: "Canceled LimeWire installation halfway, won't work anymore"
date: 2009-07-15
forum: Installation &amp; Upgrades
---

### Post by Kodaime on 2009-07-15
Halfway through the installation, It slows down a lot so I figure that I'll stop it now and restart my computer and try again. So I force quit (I'm Very new to ubuntu and wanted to try it out...) Restart and when I tried it again This error message came up:

Also, I tried to close all the windows but it didn't work. Hope you can help me out. Thanks in advance. -Kodaime

[http://img403.imageshack.us/img403/8461/screenshotriv.png[IMG]http://img403.imageshack.us/img403/8461/screenshotriv.png[/IMG]]("http://img403.imageshack.us/img403/8461/screenshotriv.png")

---

### Post by Partyboi2 on 2009-07-15
Hi, close the package installer and open a terminal (Applications>Accessories>Terminal) and type
```
sudo dpkg --configure -a
```

---

