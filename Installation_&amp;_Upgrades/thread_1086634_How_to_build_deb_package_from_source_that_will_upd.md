---
title: "How to build deb package from source that will update currently installed package?"
date: 2009-03-04
forum: Installation &amp; Upgrades
---

### Post by oryan_dunn on 2009-03-04
I have looked at several articles on building debs from source:
[http://ubuntuforums.org/showthread.php?t=51003&highlight=checkinstall](http://ubuntuforums.org/showthread.php?t=51003&highlight=checkinstall)
[http://ubuntuforums.org/showthread.php?t=2356](http://ubuntuforums.org/showthread.php?t=2356)
[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

However, it seems most of the guides assume you are installing something that is not available.  I would like to build a package for a program that is in the repos, but just isn't updated.  nspluginwrapper is currently at 0.9.91 in 8.04 ([https://launchpad.net/ubuntu/hardy/+source/nspluginwrapper](https://launchpad.net/ubuntu/hardy/+source/nspluginwrapper)), but I would like to update to 1.2.2 ([http://gwenole.beauchesne.info//en/projects/nspluginwrapper](http://gwenole.beauchesne.info//en/projects/nspluginwrapper)) for some of the fixes it provides.  The only package in the repo that depends on it is mozilla-acroread.  Can I build a deb from the source tarball that will update nspluginwrapper, but not disturb the mozilla-acroread?  Normally, I'd just wipe out what the package manager has and do a make install, but I'd like to stick with doing it the 'proper' ubuntu/debian way.

---

### Post by zvacet on 2009-03-05
[This]("https://help.ubuntu.com/6.10/ubuntu/packagingguide/C/index.html") is good guide if you want to build your packages.

---

