---
title: "Cairo Dock Plugins"
date: 2008-08-19
forum: General Help
---

### Post by Eezyville on 2008-08-19
I don't have any. :confused: I installed them and installed the plugins but they're not there. So i check synaptic and searched cairo dock for some. I found "cairo-dock-plugins" and "cairo-dock-plugins-data" and tried to install them but i get an error message. 
> E: /var/cache/apt/archives/cairo-dock-plugins-data_1.6.1.2-repack0-0ubuntu1~gilir2_all.deb: trying to overwrite `/usr/share/locale/fr/LC_MESSAGES/cd-logout.mo', which is also in package cairo-dock-plug-ins
E: /var/cache/apt/archives/cairo-dock-plugins_1.6.1.2-repack0-0ubuntu1~gilir2_amd64.deb: trying to overwrite `/usr/lib/cairo-dock/libcd-terminal.so', which is also in package cairo-dock-plug-ins

Did I do something wrong? 

System: Ubuntu 8.04 amd64bit
hp pavillion dv9000z

---

### Post by fabounet on 2008-08-20
these packages are for testing purpose, so they may be not perfect. But maybe you installed 2 different packages that conflict each other.
I would recommend to uninstall completely CD, and to retry.
if it doesn't work, use the cairo-dock's repository until Ubuntu 8.10 is out.

---

### Post by eggdeng on 2008-08-20
Use Synaptic to remove the packages you installed with it.
You can get .deb packages from
[http://developer.berlios.de/project/...?group_id=8724]("http://developer.berlios.de/project/...?group_id=8724")
The packages you need are
cairo-dock_v1.6.1.2_i686.deb and
cairo-dock-plug-ins_v1.6.1.2_i686.deb
Just download to your desktop, click on the packages and gdebi will do the rest.

---

### Post by IanW on 2008-08-20
Eggdeng, those packages are the 32-bit ones. Eezyville is using Hardy64.

It *is* possible to use them, however, with the help of getlibs.
See the [Cairo-Dock Wiki](http://www.cairo-dock.org/ww_page.php?p=For%2064%20bits%20processor&lang=en) for instructions.

I'm told by the Cairo-Dock developers that their 64-bit guy has been having PC troubles of late, and is still testing builds of 1.6.1.2

---

### Post by Eezyville on 2008-08-20
Thanks alot guys. I'll try these after work and update you on what happened.

---

### Post by gilir on 2008-08-20
You're trying to install 2 deb for the same thing.
You should uninstall all the deb of cairo-dock (sudo apt-get remove cairo-dock*) and install from 1 source, my PPA or Berlioz, but not the 2 at the same time.

---

