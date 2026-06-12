---
title: "hide unmounted partitions from the places menu and nautilus panel"
date: 2009-06-16
forum: Installation &amp; Upgrades
---

### Post by Gatemaze on 2009-06-16
Hi,

is it possible to hide unmounted partitions from the places menu and nautilus... The only relevant unsolved post I found is:
[http://ubuntuforums.org/showthread.php?p=3210306](http://ubuntuforums.org/showthread.php?p=3210306)
and bug:
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/114359](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/114359)

This post also does not work:
[http://ubuntuforums.org/showthread.php?t=1060256&highlight=removing+partitions+places+menu](http://ubuntuforums.org/showthread.php?t=1060256&highlight=removing+partitions+places+menu)

If I recall well there used to be during installation an option in each partition of "do not show" or something, because my 8.04 installation definitely hides these unmoutned paritions. Where are these "do not show" data kept?

Many thanks.

---

### Post by Gatemaze on 2009-06-16
OK here is a silly way of actually hiding them.

Add to fstab for example unmounted ntfs partition sda1 that you want to hide. In /etc/fstab
```

/dev/sda1 none ntfs-3g defaults 0 0

```

Suggestions welcome.

---

