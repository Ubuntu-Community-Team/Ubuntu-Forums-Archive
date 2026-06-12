---
title: "removing old kernel"
date: 2008-11-06
forum: General Help
---

### Post by mathfeel on 2008-11-06
I have been using 2.6.27 pretty stably for a few days, so i decided to remove the older kernel. Most googled article suggests apt-get would do the job, however:
```
$ sudo apt-get remove linux-ubuntu-modules-2.6.24-21-eeepc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-2.6.24-21-eeepc linux-ubuntu-modules-2.6.24-21-eeepc
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 55.4MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 150515 files and directories currently installed.)
Removing linux-image-2.6.24-21-eeepc ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/last-good-boot
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.27-7-eeepc
Found kernel: /boot/memtest86+.bin
Replacing config file /var/run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... done

The link /vmlinuz is a damaged link
Removing symbolic link vmlinuz 
 you may need to re-run your boot loader[grub]
The link /initrd.img is a damaged link
Removing symbolic link initrd.img 
 you may need to re-run your boot loader[grub]
Removing linux-ubuntu-modules-2.6.24-21-eeepc ...
FATAL: Could not open '/boot/System.map-2.6.24-21-eeepc': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.24-21-eeepc
Cannot find /lib/modules/2.6.24-21-eeepc
update-initramfs: failed for /boot/initrd.img-2.6.24-21-eeepc
dpkg: error processing linux-ubuntu-modules-2.6.24-21-eeepc (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.24-21-eeepc
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Is there something wrong with apt-get remove? Why would you want to regenerate initrd.img when *removing* a kernel? Can someone just tell me what kind of "post-removal" things aptitude is trying to do so that I can do it manually?

---

### Post by Daedalian on 2008-11-13
Bump. I'm having exactly the same problem with exactly the same old kernel, and it paralyzed my Ubuntu - I can't delete/install/update anything.

---

### Post by Daedalian on 2008-11-13
alright [this](http://ubuntuforums.org/showthread.php?p=6030467) worked and problem solved, but it seems like a bug...

---

