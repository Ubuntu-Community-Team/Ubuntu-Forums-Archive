---
title: "Broken Files"
date: 2009-08-26
forum: Installation &amp; Upgrades
---

### Post by Khakilang on 2009-08-26
I had an error message when I run update for my update manage. I try several time to install but fail. Some thing look like this.

E: /var/cache/apt/archives/perl-modules_5.10.0-19ubuntu1.1_all.deb: corrupted filesystem tarfile - corrupted package archive
E: /var/cache/apt/archives/perl-doc_5.10.0-19ubuntu1.1_all.deb: corrupted filesystem tarfile - corrupted package archive


I don't what to do and I hope someone can help me.

Thanks!

---

### Post by Partyboi2 on 2009-08-26
Hi, try clearing the cache and upgrading the packages again, open a terminal (Applications>Accessories>Terminal) and
```
sudo apt-get clean
sudo apt-get update && sudo apt-get upgrade
```

---

