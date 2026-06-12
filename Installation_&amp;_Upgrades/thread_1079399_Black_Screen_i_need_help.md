---
title: "Black Screen i need help"
date: 2009-02-24
forum: Installation &amp; Upgrades
---

### Post by dimensionpr on 2009-02-24
I am trying to install Ubuntu in a ideapad u330 and I get this black screen with this information:

Linux Ubuntu 2.6.27-7-generic #1 SMP fri Oct 24 06:40:41 UTC  2008 x86_64
The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

To access official Ubuntu documentation, please visit:
[http://help.ubuntu.com/](http://help.ubuntu.com/)
ubuntu@ubuntu:~$

---

### Post by bazzer on 2009-03-13
That's the standard login for a computer with no GUI installed (or correctly configured). You can install one by logging in and typing:
```
sudo apt-get install gnome-desktop-environment
```
Let us know how you get on.

---

