---
title: "Update Errors in linux-image"
date: 2009-07-10
forum: Installation &amp; Upgrades
---

### Post by acmeinc on 2009-07-10
I am receiving the below errors when attempting to run updates (update-manager).  I have treid to fix this by running sudo apt-get install -f to no avail.

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
7 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up linux-image-2.6.28-13-generic (2.6.28-13.45) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.28-13-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.28-13-generic
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/vmlinuz-2.6.27-11-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/nvidia-common
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.28-13-generic.postinst line 1002.
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
  PackNo apport report written because the error message indicates its a followup error from a previous failure.
                                No apport report written because the error message indicates its a followup error from a previous failure.
                                                          No apport report written because MaxReports is reached already
                                        No apport report written because MaxReports is reached already
                      age linux-restricted-modules-2.6.28-13-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.28.13.17); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic (= 2.6.28.13.17); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-headers-2.6.28-13-generic (2.6.28-13.45) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.28-13-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.28-13-generic (--configure):
 subprocess post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-2.6.28-13-generic; however:
  Package linux-headers-2.6.28-13-generic is not configured yet.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-2.6.28-13-generic
 linux-restricted-modules-2.6.28-13-generic
 linux-image-generic
 linux-restricted-modules-generic
 linux-generic
 linux-headers-2.6.28-13-generic
 linux-headers-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I even tried sudo apt-get remove'ing each of the above installations, and reinstalling.  Also, no dice.

I believe the problem started when I ran out of space on my drive.  I have since fixed all of the previous errors except this one.  Any ideas?

---

### Post by earthpigg on 2009-07-10
are you still out of space on your hard drive? please post the output of:

df -h

---

