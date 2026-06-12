---
title: "installer and partition size"
date: 2009-03-13
forum: Installation &amp; Upgrades
---

### Post by frank_n on 2009-03-13
When trying to install a command line system using an Ubuntu
Alternate CD, I got the infamous debootstrap warning about
corrupt deb libraries, which are not corrupt at all.

Googling did not help, I started experimenting.

At some point, it occurred to me that while I wanted a 8 GB
root partition, typing '8' was actually a request for a 8 MB
partition! After correcting the error, the install
completed.

Suggestion: the installer should impose a lower limit on
partition size.

---

