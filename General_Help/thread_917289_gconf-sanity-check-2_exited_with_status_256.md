---
title: "gconf-sanity-check-2 exited with status 256"
date: 2008-09-11
forum: General Help
---

### Post by LittleKoy on 2008-09-11
Hello, I'm using Intrepid right now, but I don't think this is actually version-related. When I try to start Gnome, an error message pops up ans says that "gconf-sanity-check-2 exited with status 256"
Lxde runs fine, but several programs (firefox, any gnome program, etc) shows an error about the configuration.

I already tried doing
```
sudo apt-get remove gconf2 gconf2-common
```
```
sudo rm -rf /etc/gconf 
``` (after doing a backup)
```
sudo apt-get install ubuntu-desktop
```

but nothing changed. I read on launchpad (googling I found 1 result!!!) that a guy solved coping /etc/gconf from another installation.

---

