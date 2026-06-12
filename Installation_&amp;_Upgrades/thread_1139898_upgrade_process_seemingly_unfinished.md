---
title: "upgrade process seemingly unfinished"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by macabro22 on 2009-04-27
Hello.

There were errors while updating to Jaunty and I got a message saying i had to manually input into the terminal:

```
louise@Watilla:~$ sudo dpkg --configure -a
Setting up linux-image-2.6.28-11-generic (2.6.28-11.42) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.28-11-generic
cpio: ./bin/udevinfo: Cannot stat: No such file or directory
update-initramfs: failed for /boot/initrd.img-2.6.28-11-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.28-11-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.28-11-generic; however:
  Package linux-image-2.6.28-11-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.28.11.15); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sn9cxxx:
 sn9cxxx depends on linux-image-generic (= 2.6.22.14.21); however:
  Version of linux-image-generic on system is 2.6.28.11.15.
dpkg: error processing sn9cxxx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.28-11-generic:
 linux-restricted-modules-2.6.28-11-generic depends on linux-image-2.6.28-11-generic; however:
  Package linux-image-2.6.28-11-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.28-11-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.28-11-generic; however:
  Package linux-restricted-modules-2.6.28-11-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.28-11-generic
 linux-image-generic
 linux-generic
 sn9cxxx
 linux-restricted-modules-2.6.28-11-generic
 linux-restricted-modules-generic

```

Any clues?]

---

### Post by macabro22 on 2009-04-27
```
cpio: ./bin/udevinfo: Cannot stat: No such file or directory

```

More specifically, how can I solve the error above?

---

### Post by theOtherMarino on 2009-05-21
[http://ubuntuforums.org/showthread.php?t=1147434](http://ubuntuforums.org/showthread.php?t=1147434)

Stuck with the same problem. Any help appreciated.

Marino

---

