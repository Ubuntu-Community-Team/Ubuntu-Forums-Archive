---
title: "Problem installing java-package"
date: 2009-06-26
forum: Installation &amp; Upgrades
---

### Post by pf22 on 2009-06-26
When I installed java-package on Ubuntu 9.0.4 desktop,I got the following message asking for a CDROM. I was installing from the Ubuntu repository using 'sudo apt-get install java-package' and should not be asked for /cdrom/.
[INDENT]After this operation, 32.5MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Media change: please insert the disc labeled
 'Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)'
in the drive '/cdrom/' and press enter
[/INDENT]I did the same install another machine a couple of days ago, it worked just fine. 

Is there any apt-get command line option that can work around this problem?

---

### Post by starcraft.man on 2009-06-26
System > Administration > Software Sources. Bottom of the window, untick the box that lists the CD in question. Installing will never again ask you to put it in.

---

### Post by pf22 on 2009-06-26
Thanks. It works!

---

