---
title: "Cant upgrade linux-image-2.6.28-12"
date: 2009-05-16
forum: Installation &amp; Upgrades
---

### Post by stuart264 on 2009-05-16
Every Time I try and install or upgrade I get the following error messages, I have tried building dependancies, purging the lists and cache and nothing seems to work at all.......does anyone have any ideas?


> Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-image-2.6.28-12-generic (2.6.28-12.43) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.28-12-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
expr: non-numeric argument
User postinst hook script [/sbin/update-grub] exited with value 2
dpkg: error processing linux-image-2.6.28-12-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.28-12-generic:
 linux-restricted-modules-2.6.28-12-generic depends on linux-image-2.6.28-12-generic; however:
  Package linux-image-2.6.28-12-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.28-12-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.28-12-generic; however:
  Package linux-restricted-modules-2.6.28-12-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                                       Errors were encountered while processing:
 linux-image-2.6.28-12-generic
 linux-restricted-modules-2.6.28-12-generic
 linux-restricted-modules-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by stuart264 on 2009-05-19
Bump.....anyone got an idea?

---

### Post by coffeecat on 2009-05-19
The latest stable version of the kernel for Jaunty is 2.6.28-11.42, so I guess you have the proposed repository enabled, or backports. If proposed, perhaps not all the dependencies are in place yet. Do you have proposed enabled? If so, do you know that's not a good idea, unless you want to help with QA testing?

You might find this a useful read:

[https://help.ubuntu.com/community/UbuntuUpdates](https://help.ubuntu.com/community/UbuntuUpdates)

---

### Post by stuart264 on 2009-05-20
Yes I did, took out proposed and backports from Synaptic and it seems to have done the trick........thanks a lot as I have been struggling with this for days and never realised that was the problem.

---

