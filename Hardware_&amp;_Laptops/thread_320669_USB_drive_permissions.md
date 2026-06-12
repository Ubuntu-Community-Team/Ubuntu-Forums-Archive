---
title: "USB drive permissions"
date: 2006-12-17
forum: Hardware &amp; Laptops
---

### Post by aklaver on 2006-12-17
I am trying to figure out how to manage permissions for an automounted USB pendrive. I can see it is being managed by the HAL system. The pendrive is ext2. It is mounted as root. A VFAT pendrive I have gets mounted under my user name. How do I tell the automount system to mount my ext2 drive as my user name.? I have read the posts that deal with similiar issues, they generally entail setting up a static entry in /etc/fstab. I am looking for a solution that will work with HAL system.

---

### Post by BrowneR on 2007-01-23
I am also having similar issues with the automount system in that all my external drives are mounted with permissions 700 where i would like 755.

Where are the config files / action scripts located? Is it something to do with udev?

---

