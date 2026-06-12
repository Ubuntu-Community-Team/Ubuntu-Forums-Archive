---
title: "Problems Upgrading To 9.04"
date: 2009-05-24
forum: Installation &amp; Upgrades
---

### Post by tysonxg on 2009-05-24
Right now i am currently running a beta version of 9.04 and when i try to upgrade via the Update Manager i run into problems...

When i got to System>Adminstration>Update Manger and look for updates i get the following
```
Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Beta i386 (20090324)/dists/jaunty/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Beta i386 (20090324)/dists/jaunty/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.
```

I am not sure what I am doing wrong(im still new to Ubuntu) So any help you have will be appreciated

---

### Post by cariboo on 2009-05-24
Just go to System-->Administration-->Software Sources and uncheck the cdrom in the list.

---

### Post by tysonxg on 2009-05-24
Wow that was simple...Thanks a bunch Cariboo!:D

---

