---
title: "imagemagick error on upgrade to Hardy"
date: 2008-10-28
forum: General Help
---

### Post by buntu_hugenewbie11 on 2008-10-28
I get a really weird error with imagemagick after upgrading to Hardy-64bit.
I upgraded from gutsy and now when I run 
apt-get upgrade 
I get the following:
(Reading database ... 331249 files and directories currently installed.)
Unpacking imagemagick (from .../imagemagick_7%3a6.3.7.9.dfsg1-2ubuntu1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/imagemagick_7%3a6.3.7.9.dfsg1-2ubuntu1_amd64.deb (--unpack):
 trying to overwrite `/usr/bin/stream', which is also in package vstream
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/imagemagick_7%3a6.3.7.9.dfsg1-2ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

How do I fix this?

---

### Post by ajgreeny on 2008-10-28
Try completely removing (purging) imagemagick from your machine and then re-installing it, perhaps after a reboot.

---

### Post by buntu_hugenewbie11 on 2008-10-28
I tried that but it still has the same issue.
For now I can live without imagemagick or dvdrip but I doubt I can live without them in the future.
This must be a bug no?

---

