---
title: "Left over Linux Generic after May-7-2009 Update"
date: 2009-05-07
forum: Installation &amp; Upgrades
---

### Post by fballem on 2009-05-07
I'm running ubuntu 9.04. Did updates this morning (May-7-2009), which gave me the option of doing a partial upgrade.

When I check update manager (System > Applications > Update Manager), I have one application left that's greyed out (screenshot attached).

Any idea what this is about, do I need to do anything about it, and if so, what do I need to do?

Thanks,

---

### Post by fballem on 2009-05-08
Fixed it. The solution for me was to review Software Sources (System > Administration > Software Sources).

On the updates tab, I had originally selected all of the options, including Pre-Released Updates (Jaunty-proposed). I cleared this selection and clicked Close.

I then re-opened Update Manager, and the entry for Linux Generic was removed. I'm assuming that the reason it was greyed out is that it couldn't be installed (missing dependencies that could not be installed).

---

