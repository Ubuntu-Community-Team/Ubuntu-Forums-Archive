---
title: "Installing Deb packages without root"
date: 2008-08-12
forum: General Help
---

### Post by drew.woods on 2008-08-12
I'm needing to install some deb packages without root .

I have access to my home directory but I am not a sudo user. I am wondering, if I extract the deb package to my home directory ( dpkg --extract [debpackage] ~/ ) ; as well as setting the correct paths, does this have the same effect as apt-get install [debpackage]? 

The reason I am asking is I'm needing to install a library call ia32-lib-gtk.  However  when I extract the deb package I get a whole bunch of other library files, non having a similar name to ia32-lib-gtk. Does apt-get combine these libraries into a single ia32-lib or what?

---

