---
title: "Installing different distro on Ubuntu 8.10"
date: 2009-03-03
forum: Installation &amp; Upgrades
---

### Post by pablo66 on 2009-03-03
I'd like to try out some other distros. Which distros will allow me to be able to select my installed version of Ubuntu during boot after installing something like Suse?

---

### Post by oldos2er on 2009-03-03
Some distros install grub in a friendly manner, meaning they create menu entries for existing operating systems; and some don't. Some still use lilo. What I usually do in this situation is to not allow other distros to install a bootloader, then after they're installed I add an entry in Ubuntu's menu.lst.

 You could also use software e.g. Virtualbox to install another distro.

---

