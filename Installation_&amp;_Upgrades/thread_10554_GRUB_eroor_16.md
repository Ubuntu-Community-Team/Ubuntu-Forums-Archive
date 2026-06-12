---
title: "GRUB eroor 16"
date: 2005-01-09
forum: Installation &amp; Upgrades
---

### Post by cafeina on 2005-01-09
I installed successfully Ubuntu 4.10, at the reboot I get GRUB menu, but no matter what I choose, GRUB gives me error 16: inconsistent filesystem structure.  I have the following partitions: 100Mb /boot with ext2, 1Gb swap, 10Gb /home with ReiserFS and remaining space / with ReiserFS.  I had other distros before with the same partition layout and never had problems. What's wrong? 
Also, is there a way to get Ubuntu put Windows to the GRUB menu during the setup?  There was no option for this during install.

---

### Post by feralert on 2005-01-09
Found [this](http://mirrors.usc.edu/pub/gnu/Manuals/grub-0.92/html_node/Stage2-errors.html)  in google:
> 16 : Inconsistent filesystem structure
    This error is returned by the filesystem code to denote an internal error caused by the sanity checks of the filesystem structure on disk not matching what it expects. This is usually caused by a corrupt filesystem or bugs in the code handling it in GRUB.

---

### Post by cafeina on 2005-01-09
I found it too, but there are only very short error descriptions. Bu I need to know how to fix it. Lilo works ok, but Grub no, so I can't install ubuntu. :(

---

