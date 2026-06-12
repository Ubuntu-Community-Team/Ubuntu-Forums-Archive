---
title: "[SOLVED] GRUB will not install at end of ubuntu 8.10 install"
date: 2008-12-14
forum: Installation &amp; Upgrades
---

### Post by nodegamra on 2008-12-14
I have the following problem.
I am trying to install Ubuntu 8.10 on a computer with WindowsXP. The installer partitions the disk and goes trough all the install steps. Once it gets to the part that it finds other OS and select to write GRUB it just won't. It gives me a fatal error unable to install grub.

For some reason it wont work I have tried several ways posted in the forums to install GRUB manually but still no luck.

If anyone can help I would greatly appreciate it.

Thanks.

---

### Post by caljohnsmith on 2008-12-14
Unfortunately, having the installer fail when it tries to install Grub is a known bug. One way that many people have circumvented it is to press the "advanced" button near the end of the installation, and choose to have Grub installed to "/dev/sda" or whichever is the drive you are installing Ubuntu to. That is enough to get around the fatal Grub install error for many people. How about giving that a shot and let me know how it goes.

---

### Post by nodegamra on 2008-12-14
Thanks for the info. I gave it a shot and worked like a charm.

---

### Post by caljohnsmith on 2008-12-15
Glad to hear that worked; cheers and have fun with your new Ubuntu install. :)

---

