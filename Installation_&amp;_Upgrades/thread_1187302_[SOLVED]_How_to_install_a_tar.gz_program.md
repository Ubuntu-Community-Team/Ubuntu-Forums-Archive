---
title: "[SOLVED] How to install a tar.gz program"
date: 2009-06-14
forum: Installation &amp; Upgrades
---

### Post by accooper on 2009-06-14
I have downloaded a program call gnome color chooser.  It is a tar.gz file.  How do I install this or is there another program like it (makes it easy to change colors on gnome) that is easier to install?
Please keep it simple.

TIA

:guitar:

Andrew From Texas

---

### Post by 67GTA on 2009-06-14
Check out this tutorial. It has screenshots and movies to help new users understand the different procedures and package types and how to install them.

[http://amitech.50webs.com/installing/index.php.html](http://amitech.50webs.com/installing/index.php.html)

---

### Post by gradinaruvasile on 2009-06-14
> **accooper said:**
> I have downloaded a program call gnome color chooser.  It is a tar.gz file.  How do I install this or is there another program like it (makes it easy to change colors on gnome) that is easier to install?
Please keep it simple.

TIA

:guitar:

Andrew From Texas

There are native ubuntu packages for it:

[https://launchpad.net/~jackthedipper/+archive/ppa]("https://launchpad.net/~jackthedipper/+archive/ppa")

---

### Post by khelben1979 on 2009-06-14
Make sure to be in the right file path and then:
```
./configure
sudo make
sudo make install
```
The above usually works, but sometimes you need to use [scons]("http://en.wikipedia.org/wiki/Scons") and in that case, there's usually an README file in the archive which explains how to do it.

---

### Post by aysiu on 2009-06-14
Forget the .tar.gz file. You can install Gnome Color Chooser through the repositories. More details here:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by accooper on 2009-06-14
Thanks For The Info.  I got it installed!

:guitar:

Andrew From Texas

---

