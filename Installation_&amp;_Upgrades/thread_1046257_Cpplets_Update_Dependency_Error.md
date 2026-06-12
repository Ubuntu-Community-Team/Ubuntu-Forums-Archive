---
title: "Cpplets Update Dependency Error"
date: 2009-01-21
forum: Installation &amp; Upgrades
---

### Post by dmaris on 2009-01-21
Installed ubuntu 8.04 on another computer from purchased CD.  Then downloaded and installed updates from internet with the following errors.  Are any of these serious and how can I resolve them?

E: capplets-data: subprocess post-installation script returned error exit status 134 
E: gnome-control-center: dependency problems - leaving unconfigured 
E: gnome-panel: dependency problems - leaving unconfigured 
E: gnome-applets: dependency problems - leaving unconfigured 
E: alacarte: dependency problems - leaving unconfigured 
E: nautilus: dependency problems - leaving unconfigured 
E: nautilus-sendto: dependency problems - leaving unconfigured 
E: nautilus-share: dependency problems - leaving unconfigured 

System is working as far as I know.

---

### Post by Partyboi2 on 2009-01-21
Can you open a terminal (Applications>Accessories>Terminal) and try
```
sudo apt-get -f install
sudo dpkg --configure -a
sudo apt-get upgrade 

```
and post back the outputs.

---

