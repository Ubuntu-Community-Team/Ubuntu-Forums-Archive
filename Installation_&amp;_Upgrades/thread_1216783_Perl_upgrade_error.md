---
title: "Perl upgrade error"
date: 2009-07-18
forum: Installation &amp; Upgrades
---

### Post by squawskier on 2009-07-18
Hi, I just got rid of 8.1 and am working on setting up 9.04, and as always, having troubles, lol.  When trying to run updates I am getting the error messages:

"E: /var/cache/apt/archives/linux-image-2.6.28-13-generic_2.6.28-13.45_amd64.deb: subprocess pre-installation script returned error exit status 127"

"E: /var/cache/apt/archives/gnome-applets-data_2.26.1-0ubuntu1_all.deb: corrupted filesystem tarfile - corrupted package archive"

I have tried deleting the package and reinstalling, but doesn't seem to help.  Any ideas?

Thanks!

---

### Post by Partyboi2 on 2009-07-18
Hi, open a terminal and try cleaning out the cache first
```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by squawskier on 2009-07-19
hey, thanks, but I ended up getting frustrated and repartitions/installed :P

---

