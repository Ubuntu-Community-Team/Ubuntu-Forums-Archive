---
title: "Error on Kernel updates?"
date: 2009-07-18
forum: Installation &amp; Upgrades
---

### Post by animaster on 2009-07-18
Hi,
I got this error when updating from 2.6.28-12 to 2.6.28-13.
When I try "sudo apt-get install -f" command, I get the following output:

```
me@laptop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
5 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up linux-image-2.6.28-13-generic (2.6.28-13.45) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.28-13-generic
Segmentation fault
update-initramfs: failed for /boot/initrd.img-2.6.28-13-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.28-13-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.28-13-generic:
 linux-restricted-modules-2.6.28-13-generic depends on linux-image-2.6.28-13-generic; however:
  Package linux-image-2.6.28-13-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.28-13-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.28-13-generic; however:
  Package linux-image-2.6.28-13-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.28-13-generic; however:
  Package linux-restricted-modules-2.6.28-13-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configNo apport report written because the error message indicates its a followup error from a previous failure.
              No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                                        No apport report written because MaxReports is reached already
                         No apport report written because MaxReports is reached already
                                                                                       ure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.28.13.17); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic (= 2.6.28.13.17); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.28-13-generic
 linux-restricted-modules-2.6.28-13-generic
 linux-image-generic
 linux-restricted-modules-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Anyone can help me with this?

Thank you in advance.

---

### Post by stmiller on 2009-07-19
I get that error when trying a new install of 9.04. Tried kubuntu 9.04, ubuntu 9.04, and netinstall CDs of each. :/

Must be a bug.

---

### Post by Hybris71 on 2009-07-21
I have the same issue, and may have installed a restricted-modules kernel earlier on. (So long ago I don't really remember.)

Synaptic, apt-get and so on can't be used, stating I have to run "sudo dpkg --configure -a" manually first.
Attempting this, however, causes a segmentation fault, and results in exactly nothing except "error exit status 1."
As far as I've been able to trace, the segfault seems to happen in update-initramfs, but really happens in mkinitramfs as update-initramfs calls "mkinitramfs -o /boot/initrd.img-2.6.28-13.generic.new 2.6.28-13-generic"

I haven't been able to find the exact spot where things go pear-shaped, but perhaps someone with a little more experience can help me out a little?  ](*,)

---

