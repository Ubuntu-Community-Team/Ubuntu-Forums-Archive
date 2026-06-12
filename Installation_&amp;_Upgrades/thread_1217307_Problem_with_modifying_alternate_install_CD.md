---
title: "Problem with modifying alternate install CD"
date: 2009-07-19
forum: Installation &amp; Upgrades
---

### Post by teddks on 2009-07-19
I'm trying to create a variant of the alternate install CD with some extra packages included in the default install. I've followed the howto on the wiki (InstallCDCustomization) and I've been able to generate an install CD with my packages in the repository, but even though I have preseed lines to install them by default, they aren't installed.

I know the repository works -- I can go into a shell after the install is complete and add the packages manually. I just can't get them to install by default.

Is there some preseed switch I need to set, or something else I need to do? I'd prefer not doing something brutal like calling a script to chroot into the target installation and install the packages, or modify ubuntu-desktop to install my own meta-package that will pull in my packages, but if I have to, I will.

---

