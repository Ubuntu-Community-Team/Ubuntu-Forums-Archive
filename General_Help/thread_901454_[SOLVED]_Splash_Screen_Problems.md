---
title: "[SOLVED] Splash Screen Problems"
date: 2008-08-26
forum: General Help
---

### Post by enazguy on 2008-08-26
I'm trying to install a new splash screen in Ubuntu 8.04. I found carbono on Gnomelook and tried to install it using Splash Screen found under System-Preferences-Splash Screen. When i navigate to carbono and try to install it, splash screen quits. What can I do?

---

### Post by raphaelr on 2008-08-27
Try installing the Splash Screen manually.```
cd /etc/alternatives
sudo rm -f usplash-artwork.so
sudo ln -s /usr/lib/yoursplashscreen.so usplash-artwork.so
```

---

### Post by david sousa on 2008-08-27
You can install stratup-manager. It's easier! ;)

follow this link here and the rest of instructions are at gnome-look splash screens pages:

[http://packages.ubuntu.com/gutsy/utils/startupmanager](http://packages.ubuntu.com/gutsy/utils/startupmanager)

---

### Post by enazguy on 2008-08-27
Thanks David Sousa.
Startup Manager worked great and its much easier to manage my splash screens now.

---

