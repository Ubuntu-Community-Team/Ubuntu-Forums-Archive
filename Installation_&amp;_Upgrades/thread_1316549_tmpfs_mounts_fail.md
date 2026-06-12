---
title: "tmpfs mounts fail"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by bjlockie on 2009-11-06
I had these but in my /etc/fstab they don't work in 9.10.

tmpfs      /var            tmpfs        defaults           0    0
tmpfs      /var/log        tmpfs        defaults           0    0
tmpfs      /var/log/apt    tmpfs        defaults           0    0
tmpfs      /tmp            tmpfs        defaults           0    0
tmpfs      /var/tmp        tmpfs        defaults           0    0

---

### Post by Lars Noodén on 2009-11-06
What kind of error message is it giving?

There should be something from the last boot regarding mounting filesystems in /var/log/dmesg

---

### Post by bjlockie on 2009-11-10
/var/log/apt didn't exist and the error was "waiting for tmpfs".
I fixed it. :-)

The shortcut menus on the left side are now gone (favourites, accessories, ...) but I was going to ask how to get rid of them. :-)

---

