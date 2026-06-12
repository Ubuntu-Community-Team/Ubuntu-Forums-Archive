---
title: "update errors"
date: 2009-11-11
forum: Installation &amp; Upgrades
---

### Post by MaD1 on 2009-11-11
hi to all i am having problems updating 9.04 this is what it tells me please help


E: /var/cache/apt/archives/libssl0.9.8_0.9.8g-15ubuntu3.3_i386.deb: corrupted filesystem tarfile - corrupted package archive
E: /var/cache/apt/archives/gnome-applets-data_2.26.1-0ubuntu1_all.deb: corrupted filesystem tarfile - corrupted package archive
E: /var/cache/apt/archives/libgl1-mesa-dri_7.4-0ubuntu3.2_i386.deb: short read in buffer_copy (backend dpkg-deb during `./usr/lib/dri/i810_dri.so')
E: /var/cache/apt/archives/linux-image-2.6.28-16-generic_2.6.28-16.55_i386.deb: corrupted filesystem tarfile - corrupted package archive
E: /var/cache/apt/archives/linux-restricted-modules-2.6.28-16-generic_2.6.28-16.21_i386.deb: short read in buffer_copy (backend dpkg-deb during `./lib/linux-restricted-modules/2.6.28-16-generic/wl/wlc_hybrid.o_shipped_i386')
E: /var/cache/apt/archives/ubuntu-docs_9.04.10_all.deb: short read in buffer_copy (backend dpkg-deb during `./usr/share/gnome/help/serverguide/sv/clustering.xml')
E: /var/cache/apt/archives/libpam-runtime_1.0.1-9ubuntu1.1_all.deb: corrupted filesystem tarfile - corrupted package archive

please help me as complete noob thank

---

### Post by earthpigg on 2009-11-11
hi,

you have reliable high broadband, yes? if not, stop here and let us know.

if so: run these commands and let us know how it works out.
```

sudo apt-get clean
sudo apt-get update
```

edit: here is what we are doing... "sudo apt-get clean" is going to delete everything in /var/cache/apt/archives, where you seem to have several damaged packages. this can be due to your internet connection dying mid-download, or it can be due to the moon and stars aligning in a way that made you unlucky when you tried to update. nothing you did wrong was likely to have caused this - just like a phone conversation sometimes randomly has a bunch of static. you had 'static' during your update, leaving garbage behind. so, we are going to clean it.

"sudo apt-get update" is going to re-download the packages, hopefully the moon and stars are not aligned against you this time and you get a solid update.

---

### Post by MaD1 on 2009-11-12
thank very much i my father helped me with it in this way and will keep it inmind if it does it again

---

