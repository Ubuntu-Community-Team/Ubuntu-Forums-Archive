---
title: "OpenOffice 2 Install"
date: 2005-11-26
forum: General Help
---

### Post by canadianwriterman on 2005-11-26
I though I once saw an OpenOffice 2.0 install guide in the Wiki (similar to the one that guides you through the installation of Firesfox 1.5), but I can't seem to find it now. Does anyone know where it is? Thanks.

---

### Post by `GooZ´ on 2005-11-26
Just add the following 2 lines to your /etc/apt/sources.list:
#OpenOffice 2.0 final, not beta like ubuntu repos
deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./

Then do apt-get update

---

### Post by dsjas297 on 2005-11-26
[http://documentation.openoffice.org/setup_guide2/index.html](http://documentation.openoffice.org/setup_guide2/index.html)

That's the setup guide on the Open Ofiice. It says to use dpkg, but it would be far easier to install with the Synaptic package manager.

---

### Post by canadianwriterman on 2005-11-27
[QUOTE=`GooZ´]Just add the following 2 lines to your /etc/apt/sources.list:
#OpenOffice 2.0 final, not beta like ubuntu repos
deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./

Then do apt-get update[/QUOTE]

Thanks, GooZ. Worked perfectly. Actually, as soon as I added the source, Synaptic did an update and install.

---

### Post by dcroal on 2005-12-04
This version of OpenOffice.org 2 does not seem to to pick up all of my fonts, especially Microsoft msttcorefonts.

I had to run the OpenOffice.org Printer-Font admin program manually - /usr/lib/openoffice2/program/spadmin
and add all the fonts from /usr/share/fonts/truetype/msttcorefonts before I could use Arial, Verdana, etc.

FYI.

---

