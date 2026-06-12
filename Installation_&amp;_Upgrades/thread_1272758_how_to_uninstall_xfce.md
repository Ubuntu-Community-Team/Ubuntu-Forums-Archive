---
title: "how to uninstall xfce"
date: 2009-09-22
forum: Installation &amp; Upgrades
---

### Post by cele on 2009-09-22
How to uninstall xfce enviroment from Ubuntu? I'm using Ubuntu 9.04, and I installed xfce from curiosity. But now i have double applications in menu's.

---

### Post by sisco311 on 2009-09-22
[http://psychocats.net/ubuntu/puregnome]("http://psychocats.net/ubuntu/puregnome")

---

### Post by stlsaint on 2009-09-22
sudo apt-get remove xubuntu-desktop

---

### Post by sisco311 on 2009-09-22
> **stlsaint said:**
> sudo apt-get remove xubuntu-desktop

xubuntu-desktop is a meta-package.

It depends on all of the packages in the Xubuntu desktop system.

Removing it will not remove the actual packages.

---

### Post by raymondh on 2009-09-22
Or you can use synaptic to remove Xubuntu and its' packages.  Or, you can set in sessions GNOME as your default (instead of xfce) though it wont remove the packages.

---

