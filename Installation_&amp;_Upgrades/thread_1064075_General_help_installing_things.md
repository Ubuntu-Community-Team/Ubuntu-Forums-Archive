---
title: "General help installing things"
date: 2009-02-08
forum: Installation &amp; Upgrades
---

### Post by OJX on 2009-02-08
Linux noob here, installed ubuntu 8.10 onto my EEEPC1000HA.Installed the kernel that allows wireless/cam to work.
I want to be able to use [this tray:]("http://greg.geekmind.org/eee-control/#download") for my eee pc. I installed it, but its not working well because I forgot to install "Python"


> eee-control is written in Python and therefore requires a few Python modules. These are:

    * pygtk
    * python-dbus
    * python-gconf
    * pynotify
    * python-smbus

How do I uninstall the tray, install these packages, and then reinstall the tray?

Thanks a lot in advanced

P.S. I'm a total noob, I can basically just open the terminal, so can you be specific in your answers please ;)

---

### Post by taurus on 2009-02-08
If you installed it by double-clicking the filename, eee-control_0.8.3_all.deb, you can remove it from a terminal with

Applications -> Accessories -> Terminal
```
sudo dpkg -r eee-control
```

---

### Post by OJX on 2009-02-08
> **taurus said:**
> If you installed it by double-clicking the filename, eee-control_0.8.3_all.deb, you can remove it from a terminal with

Applications -> Accessories -> Terminal
```
sudo dpkg -r eee-control
```

Thanks that worked perfectly
Would you happen to know how to install those python modules?

---

### Post by taurus on 2009-02-08
Try looking for them in synaptic.

---

