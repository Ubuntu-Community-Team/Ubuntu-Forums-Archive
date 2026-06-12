---
title: "jaunty - errors in terminal"
date: 2009-05-05
forum: Installation &amp; Upgrades
---

### Post by mosaic2s on 2009-05-05
Jaunty installed from CD. Great - no issues. But on to next step, I stumble.

linux@chota-rajan:~$ sudo apt-get install mozilla-thunderbird
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  thunderbird
Suggested packages:
  thunderbird-gnome-support latex-xft-fonts
The following NEW packages will be installed:
  mozilla-thunderbird thunderbird
0 upgraded, 2 newly installed, 0 to remove and 51 not upgraded.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

How to resolve this?

---

### Post by Partyboi2 on 2009-05-05
Hi, make sure that you only have one package manager open at a time eg apt-get, synaptic, dpkg...

---

### Post by mosaic2s on 2009-05-05
Thanks. was getting stuck with video driver installation and thunderbird installation.

---

