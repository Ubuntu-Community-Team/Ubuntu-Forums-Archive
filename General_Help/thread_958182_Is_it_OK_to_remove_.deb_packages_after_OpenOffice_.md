---
title: "Is it OK to remove .deb packages after OpenOffice 3.0 installation ?"
date: 2008-10-25
forum: General Help
---

### Post by Jags_FL on 2008-10-25
After a successful installation of OpenOffice.org 3.0 on Ubuntu Intrepid RC from this [**OOo tutorial**]("http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68"), 'System Tools' >> 'System Cleaner' lists a lot of OpenOffice.org 3.0 .deb packages as unwanted. 

So is it OK to remove 'em or are there any consequences and if its OK to remove, does it applies to any & all packages system cleaner lists ? (eg: it also lists Nimbus .deb package, a Solaris GNOME theme I installed earlier) 

Many thanks in advance, jags

Edit: screenshot attached

---

### Post by spiderbatdad on 2008-10-25
These are only the packages, the boxes, that held the programs you installed. You can safely throw the packages out, or save them, if you don't want to have to find them again...in the event you want to share them or reinstall them.

---

### Post by sethvath on 2008-10-25
To clean up after your installation of the debs. 

sudo apt-get autoclean
sudo apt-get autoremove

---

### Post by Jags_FL on 2008-10-25
spiderbatdad, sethvath

guys, thanks a lot

---

