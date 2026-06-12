---
title: "How install modem without net access?"
date: 2005-09-04
forum: Hardware &amp; Laptops
---

### Post by goldrush on 2005-09-04
Hi all.
Very much a Linux newbie (although an oldie at 70 years old!  :)  
I cannot seem to install the modem modules without net access and apt-get
Case of chicken and egg.
Downloaded sl-modem-modules-*.deb via windows.
Placed it in new directory change to that directory
used dpkg install
appears to install Ok and last line is "setting up sl-modem modules"

Then try gpkg install sl-modem-daemon
Cant find !!!!

Also tried adding the download directory to sources.list and updating apt-get
apt-get then cant find the .deb
Same with trying apt-cdrom ....... not a dedian disk!!

Thanx

---

### Post by az on 2005-09-04
You will need to transfer the sl-modem-daemon package in the same way.  That driver is in two parts:  the modules and the daemon.

---

### Post by goldrush on 2005-09-04
Thanks Azz
Guess I did not think of the obvious, but assumed the daemon was part of the package.
Guess I can put it down to "just another senior moment" :)

---

