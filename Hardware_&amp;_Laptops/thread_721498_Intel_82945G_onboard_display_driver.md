---
title: "Intel 82945G onboard display driver"
date: 2008-03-11
forum: Hardware &amp; Laptops
---

### Post by Sudheer on 2008-03-11
I've installed Ubuntu Server edition on Acer Veriton Pc having Intel 82945G integrated Graphics card. 
I would like to install GUI on the server.  Please help to do this.

---

### Post by Rocket2DMn on 2008-03-11
If you want the GNOME desktop environment (default for Ubuntu), run
```
sudo apt-get install ubuntu-desktop
```
For KDE, it's "kubuntu-desktop" and for Xfce, it's "xubuntu-desktop".
You should then be able to get to the GUI with
```
startx
```

---

