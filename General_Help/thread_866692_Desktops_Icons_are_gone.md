---
title: "Desktops Icons are gone"
date: 2008-07-22
forum: General Help
---

### Post by Kiri on 2008-07-22
Sometimes after startup the icons on the desktop fail to appear (there is just a blank desktop). I assume this is something to do with nautilus... but how do I load that desktop icons? 
At the moment I have to resort to restarting X every time it happens.

---

### Post by Gunman1982 on 2008-07-22
For a quicker workaround: press 'alt+F2' and execute 'killall nautilus' that will restart nautilus so you don't have to restart X. But maybe you should look into the logs in /var/log/ if there is any problem. I don't know in which file nautilus writes its logs though.

---

