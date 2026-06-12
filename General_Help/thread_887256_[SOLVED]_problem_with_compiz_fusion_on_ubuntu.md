---
title: "[SOLVED] problem with compiz fusion on ubuntu"
date: 2008-08-11
forum: General Help
---

### Post by merxx on 2008-08-11
Really new to Ubuntu and just got my new dell laptop 2 days ago with an UBUNTU 8.04 LTS version loaded in it. Trying to install COMPIZ FUSION on Ubuntu  for GNOME and KDE users  using the guide  in 

[http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml](http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml)

but got the following error in the end. Would appreciate help on how fix the problem?


sudo apt-get -y install compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra libcompizconfig-backend-gconf

Reading package lists... Done
Building dependency tree 
Reading state information... Done
compiz is already the newest version.
compiz-gnome is already the newest version.
compiz-fusion-plugins-extra is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
compizconfig-backend-gconf: Conflicts: libcompizconfig-backend-gconf but 0.6.0~git20071003+3v1ubuntu0 is to be installed
E: Broken packages

---

### Post by Crafty Kisses on 2008-08-12
Have you tried installing your video card drivers?

---

### Post by tech0007 on 2008-08-12
The guide is for 7.04 and you have 8.04!  Go back to Software Sources and uncheck the line you added. Then close.  It will reload your sources automatically.  Then open Synaptic Package Manager, search and install 'compiz'.

---

### Post by tuxxy on 2008-08-12
Enable your driver and then enable compiz effects at system > pref > appearance > desktop effects

---

### Post by overdrank on 2008-08-12
moved :)

---

### Post by merxx on 2008-08-12
I got the problem solved through your guidance and direction. Thank you to Codename,tech007,tuxxy and overdrank. 

I found out that 2 programs  (compiz) in the Synaptic Package Manager were not installed/applied.

Thanks again.

---

