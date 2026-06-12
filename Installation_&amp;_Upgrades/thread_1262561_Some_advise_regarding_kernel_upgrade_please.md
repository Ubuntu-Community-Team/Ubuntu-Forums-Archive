---
title: "Some advise regarding kernel upgrade please"
date: 2009-09-10
forum: Installation &amp; Upgrades
---

### Post by jhardydj on 2009-09-10
Good-day! Long tory short, my last kernel "upgrade" using the "Ubuntu" way (compiling , then doing dpkg - ....headers..deb ..linux..deb etc) ended up pooching my grub (error 18 - bios cylinder size blah blah).  Most Google searches pointed me to threads saying to boot off livecd , mounting linux to /mnt/root, mounting proc and /dev , and then doing the grub install from chroot /mnt/root .   If you are familiar with these steps, it appears to work for most people, but not for me.  I received no errors and was using the correct partitions (AFAIK). 

Ubuntu 9.04 

my partition is setup as follows:

/dev/sda (hd0) 
/dev/sda1 ext3
/dev/sda2 swap

So i did use root (hd0,0) and setup (hd0) , quit.  no errors.

When I reboot same error 18 (no matter what image I use).

So .. my question is, how can i prevent this before hand at attempting another kernel upgrade, and is there any steps I may be missing when trying to fix it after the fact?

Thank you for you help.

---

