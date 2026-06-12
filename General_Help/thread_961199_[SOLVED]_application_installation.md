---
title: "[SOLVED] application installation"
date: 2008-10-28
forum: General Help
---

### Post by Firestrider on 2008-10-28
I just installed Linux Mint 5 x64 (based on Ubuntu hardy) and I was wondering the correct way to install Open Office 3.0 and Banshee 1.2

The updated versions are not in the software portal.

---

### Post by eder.apt-get on 2008-10-28
As far as I know, only Mint 6 will have the 3.0 version officially. I´m assuming that you don´t wanna wait till that happen, so take a look here:
[http://www.linuxmint.com/forum/viewtopic.php?f=47&t=17792&p=108942&hilit=openoffice+3.0#p108942](http://www.linuxmint.com/forum/viewtopic.php?f=47&t=17792&p=108942&hilit=openoffice+3.0#p108942)

It might help to install the deb pack.

---

### Post by Firestrider on 2008-10-28
Ok thanks I went to there, downloaded the package, and followed all the terminal commands but when I did sudo dpkg -i *.deb I get the following errors:

dpkg: error processing *.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 *.deb

Ok I got it to dpkg but now I got this error:

dpkg: error processing ooobasis3.0-base_3.0.0-9_i386.deb (--install):
 package architecture (i386) does not match system (amd64)


I guess it will not work with my system and I need a x86 os?

---

### Post by Firestrider on 2008-10-28
Is there anyway to have it install in compatibility ? Or will I have to wait for an x64 Linux version of Openoffice 3

---

