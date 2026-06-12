---
title: "Deleted  X server..help"
date: 2009-03-22
forum: Installation &amp; Upgrades
---

### Post by Errchy on 2009-03-22
Ok, so I'm still new to linux. I've been using Ubuntu 8.10 for a couple of months, and I finally broke it.  I accidentally deleted xserver-xorg and xserver-xorg-core and related files.  How can I reinstall it?  Since i deleted it, it says I need to reinstall it (44 new packages), but since I'm just on the text based linux now I'm a little lost. It said it can't install the packages cause it can't connect to the internet. Is it possible to install X server off of a live cd?

---

### Post by zvacet on 2009-03-22
```
gksudo gedit /etc/apt/sources.list
```

Remove # sign from 

 deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081028)]/ intrepid main restricted

or maybe it is hardy,because I don´t know whitch version you have.But that make no difference.After you removed # sign from begining of line save and close file.

```
sudo apt-get update
```

Now insert live Cd in drive and in terminal

```
sudo apt-get install xserver-xorg  xserver-xorg-core
```

---

