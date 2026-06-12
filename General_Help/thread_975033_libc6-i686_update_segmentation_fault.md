---
title: "libc6-i686 update segmentation fault"
date: 2008-11-08
forum: General Help
---

### Post by rsteinmetz70112 on 2008-11-08
Recently I updated my system 8.04 and began receiving these errors.

Tried
# apt-get -f install
# dpkg --configure -a

Same result

Any Ideas what is causing this or how to fix it?

# apt-get -u upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
16 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up libc6-i686 (2.7-10ubuntu4) ...
Segmentation fault
dpkg: error processing libc6-i686 (--configure):
subprocess post-installation script returned error exit status 139

---

