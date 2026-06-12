---
title: "Need python2.3-gtk2, but it's no longer available"
date: 2005-11-14
forum: General Help
---

### Post by galamud on 2005-11-14
I tried using the debian package, but here's the result:

>sudo dpkg -i python2.3-gtk2_2.6.3-2_i386.deb
dpkg: regarding python2.3-gtk2_2.6.3-2_i386.deb containing python2.3-gtk2:
 python2.4-gtk2 conflicts with python2.3-gtk2
  python2.3-gtk2 (version 2.6.3-2) is to be installed.
dpkg: error processing python2.3-gtk2_2.6.3-2_i386.deb (--install):
 conflicting packages - not installing python2.3-gtk2
Errors were encountered while processing:
 python2.3-gtk2_2.6.3-2_i386.deb

Is there any way to get this old package on my system?  I need it for development work.  I can't get rid of python2.4-gtk2, because a whole lot of Ubuntu functionality depends on it.

---

