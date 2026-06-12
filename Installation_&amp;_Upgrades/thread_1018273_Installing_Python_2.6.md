---
title: "Installing Python 2.6"
date: 2008-12-21
forum: Installation &amp; Upgrades
---

### Post by osiris2258 on 2008-12-21
I am working on a project that requires multi-threading. In Python, this is only possible with 2.6 and 3, and due to compatibility concerns (the packages we need to use are still in 2.x code) we are working with 2.6.

The default python in 8.10 is 2.5.2. I have found python 3 in the repos, but I can't find 2.6 anywhere. Is there a package, or do I need to compile from source?

In the event that I need to compile from source, how do I do so? I have heard that Python is very difficult to update.

---

### Post by maximinus_uk on 2008-12-23
Had the same issue, and I found out this:

[https://bugs.launchpad.net/ubuntu/+source/python-defaults/+bug/278230]("https://bugs.launchpad.net/ubuntu/+source/python-defaults/+bug/278230")

and

[http://www.lysium.de/blog/index.php?/archives/229-Installing-Python-2.6-on-Ubuntu-8.04.html]("http://www.lysium.de/blog/index.php?/archives/229-Installing-Python-2.6-on-Ubuntu-8.04.html")

Hope they are of some info.

---

