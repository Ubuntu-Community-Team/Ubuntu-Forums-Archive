---
title: "exporting drivers to another version of ubuntu"
date: 2009-05-28
forum: Installation &amp; Upgrades
---

### Post by skaldyr on 2009-05-28
Im new to ubuntu.

I have a moblin installation with some proprietary drivers for wifi and touch screen.

How can i extract them from the moblin installation, so that i can use them in my next installation of ubuntu or xubuntu?
Im testing defferent version of ubuntu on the machine, to find the best suited. 

Is there a directory where i can find the drivers and then copy them to a usb-key?

---

### Post by markbuntu on 2009-05-28
Moblin is based on Fedora which uses rpm packages. ubuntu uses deb packages. It is possible to convert rpms to debs using alien but there may be other issues. 

The packages themselves are often not saved after installation to save space so you may need to get the packages again. Saved packages are often in /usr/src but may be elsewhere.  If you get the packages again do not install them but save them.

---

### Post by skaldyr on 2009-05-29
The moblin im using is moblin 1 based on ubuntu 8.04.

---

