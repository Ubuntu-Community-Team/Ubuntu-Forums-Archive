---
title: "Ofen Office 3.0"
date: 2008-11-19
forum: General Help
---

### Post by ravindukelum on 2008-11-19
I removed open office default in ubuntu 8.10 and I downloaded open office 3.0 when i'm going to installed those some problem arose so please tell me howto install new open office 3.0.

---

### Post by prshah on 2008-11-19
> **ravindukelum said:**
>  some problem arose so please tell me howto install new open office 3.0.

What problem arose? More details please.

---

### Post by giuspen on 2008-11-19
I wonder how long we will have to wait for openoffice 3 in the repositories... I don't understand why they don't upgrade it.

---

### Post by thestig_992 on 2008-11-19
you might have downloaded the RPM version rather than the DEB. 

I made that mistake XD

---

### Post by volaer on 2008-11-19
Aside from that, as you observed, ubuntu used the Sun Corporation Open Office rather than that of regularly downloaded version in openoffice.org

i don't know what's the exact difference, but I think the difference lies in the extensions...:) it's just a guess.

---

### Post by fooman on 2008-11-19
i updated from the repository awhile back like this:

first open a terminal and type or copy/paste the following:

```
gksudo gedit /etc/apt/sources.list
```

when it opens, add (copy/paste) the following lines to the bottom of the file:

```
##repo for open office3
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
deb-src http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
```

*save*, then close the file and run these 2 commands one at a time:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by scouser73 on 2008-11-19
Here's an excellent tutorial on installing OpenOffice 3.
[http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/](http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/)

---

### Post by giuspen on 2008-11-19
> **scouser73 said:**
> Here's an excellent tutorial on installing OpenOffice 3.
[http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/](http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/)

easier than adding the repositories how the good fooman adviced I think there's nothing

---

### Post by Meow27 on 2008-11-19
this is my favorite guide

[http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by fragos on 2008-11-19
In software source enable backports for updates. I got Open Office 3.0 through the daily update manager process. 2.4 was replaced by 3.0 automatically. If you haven't already, go to medibuntu.org and follow their directions for adding the medibuntu repository. There's lots of great stuff there for multimedia and even access to Google Earth.

---

