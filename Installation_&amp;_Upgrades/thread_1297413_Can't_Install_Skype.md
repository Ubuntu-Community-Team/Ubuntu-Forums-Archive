---
title: "Can't Install Skype"
date: 2009-10-21
forum: Installation &amp; Upgrades
---

### Post by drjose on 2009-10-21
I get this error when I try and install skype.. Error: Dependency is not satisfiable: libqt4-dbus (>= 4.4.3)

Can someone help this total beginner to Ubuntu.. 

:popcorn:

---

### Post by Partyboi2 on 2009-10-22
Hi, it means you need to install the missing dependency, you can do this by opening a terminal (Applications>Accessories>Terminal) and typing
```
sudo apt-get install libqt4-dbus
``` then try installing skype again.
If you do not want to have to manually install all the dependencies you can add the medibuntu repository to your sources.list and install skype. To do this open a terminal and type
```
sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list \
 --output-document=/etc/apt/sources.list.d/medibuntu.list &&
sudo apt-get -q update &&
sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring &&
sudo apt-get -q update
```[FONT=Arial]Then install skype with[/FONT]
```
sudo apt-get install skype
```

---

