---
title: "RC1 wants to remove kubuntu-desktop?"
date: 2005-11-15
forum: General Help
---

### Post by vh1 on 2005-11-15
seems very odd.

early on yesterday I tried updating to RC1 but I got a bunch of 404 errors. now I've noticed they've updated all the packages, so I decided to do an upgrade. it went ahead fine, but  at the inital package listing of what was going to be updated, newly installed, and kept back, I noticed a bunch of packages that were going to be kept back

so after the upgrade I ran `sudo apt-get dist-upgrade` and here's what it reports:
```
The following packages will be REMOVED:
  akode kubuntu-desktop libkcal2a libkdepim1 libkleopatra0a libmimelib1a
The following NEW packages will be installed:
  kdepim-kresources libakode2 libarts1-akode libgnokii2 libkcal2b libkdepim1a libkleopatra1 libkmime2 libmimelib1c2 perl-suid poppler-utils
The following packages will be upgraded:
  akregator juk kaddressbook karm kdegraphics-kfile-plugins kdemultimedia kdenetwork-filesharing kdepim-kio-plugins kdepim-wizards kmail knotes kontact
  korganizer libkpimexchange1 libkpimidentities1
15 upgraded, 11 newly installed, 6 to remove and 0 not upgraded.
Need to get 15.3MB of archives.
After unpacking 8643kB of additional disk space will be used.
```

have I done something wrong?
or should I just wait another day or so to upgrade everything?

---

### Post by daller on 2005-11-15
It doesn't look alarming to me!

kubuntu-desktop is a metapackage, and the removal is not essential to anything...

---

### Post by lerrup on 2005-11-16
and you can  always reinstall it to make sure you get everything when you upgrade to 6.04.;)

---

