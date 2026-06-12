---
title: "Problem upgrading."
date: 2006-01-27
forum: Installation &amp; Upgrades
---

### Post by Iesos on 2006-01-27
Having problem upgrading this morning. When running 
$ sudo apt-get upgrade
This is the last printout in the terminal:

> Removing `diversion of /usr/share/ubuntu-artwork/home/index.html to /usr/share/ubuntu-artwork/home/index-ubuntu.html by kubuntu-docs'
dpkg-divert: rename involves overwriting `/usr/share/ubuntu-artwork/home/index.html' with
  different file `/usr/share/ubuntu-artwork/home/index-ubuntu.html', not alloweddpkg: error processing kubuntu-docs (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 kubuntu-docs
E: Sub-process /usr/bin/dpkg returned an error code (1)

And it doesn't seem to upgrade any of the upgradeable pakages.
Whats the problem and how can I fix it?

---

