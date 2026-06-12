---
title: "Major problems with phpmyadmin w/ Apache2"
date: 2009-09-17
forum: Installation &amp; Upgrades
---

### Post by ryankask on 2009-09-17
I've been having many problems using phpMyAdmin. After reinstalling the unsupported package several times, I was left with "blank pages." After looking online for other people with similar problems, I see they were able to solve theirs, I was not. 

I decided to install phpmyadmin manually and it turns out that the Apache children that try to run the script are seg faulting (from "tail /var/log/apache2/error.log"):

```

[Thu Sep 17 15:19:28 2009] [notice] child pid 7762 exit signal Segmentation fault (11)
[Thu Sep 17 15:19:31 2009] [notice] child pid 7763 exit signal Segmentation fault (11)
[Thu Sep 17 15:19:40 2009] [notice] child pid 7764 exit signal Segmentation fault (11)

```

What is going on here? Is anyone else having similar problems?

A frusterated dev...

Ryan Kaskel

---

