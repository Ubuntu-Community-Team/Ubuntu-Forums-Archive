---
title: "kubuntu 64 bit webkit?"
date: 2008-08-27
forum: General Help
---

### Post by kristian_nissen on 2008-08-27
Hi, has anyone ever managed to get webkit to run on kubuntu 64 bit version? If yes, I'd like how to, I love kubuntu but still, nothing beats safari :) and I would settle for webkit if possible.

---

### Post by Nepherte on 2008-08-27
I compiled webkit from source on Ubuntu. It's the same procedure for Kubuntu. I used this information: [http://live.gnome.org/WebKitGtk](http://live.gnome.org/WebKitGtk)

You will need a lot of extra required packages. I forget what they were, but when you ./configure webkit, it will tell which ones are missing. Remember to install the -dev packages of the missing required packages, not the regular ones.

Edit: these were the dependencies: [http://trac.webkit.org/wiki/BuildingGtk#Dependencies](http://trac.webkit.org/wiki/BuildingGtk#Dependencies)

---

### Post by kristian_nissen on 2008-10-19
I followed [http://live.gnome.org/WebKitGtk](http://live.gnome.org/WebKitGtk) and got until ./autogen.sh --prefix=/usr/local but it's giving me aclocal: configure.ac: 73: macro `AM_PROG_CC_C_O' not found in library I have Webkit inside /opt/Webkit$

---

