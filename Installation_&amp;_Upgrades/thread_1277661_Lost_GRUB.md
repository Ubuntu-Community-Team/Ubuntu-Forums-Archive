---
title: "Lost GRUB"
date: 2009-09-28
forum: Installation &amp; Upgrades
---

### Post by cccc on 2009-09-28
hi

I've lost GRUB during Windows XP installation.
Howto install GRUB again using Ubuntu Live CD?

BTW I'd like to install GRUB on the Ubuntu root partition.

---

### Post by ajgreeny on 2009-09-28
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by cccc on 2009-09-28
```

# sudo mount /dev/sda2 /mnt 
# sudo grub-install --root-directory=/mnt /dev/sda2
```solved this problem.

greetings
cccc

---

