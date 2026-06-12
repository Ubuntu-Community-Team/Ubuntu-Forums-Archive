---
title: "Kernel Upgrade Error"
date: 2009-02-11
forum: Installation &amp; Upgrades
---

### Post by Mechanimal on 2009-02-11
I'm getting an error while trying to upgrade the kernel. At first it wouldn't even go, but after a bit of tweaking it downloads the kernel and goes through all the steps, but in the end it shows:

The following packages will be upgraded:
  linux-image-2.6.24-23-generic
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 18.4MB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main linux-image-2.6.24-23-generic 2.6.24-23.48 [18.4MB]
Fetched 18.4MB in 51s (360kB/s)                                                 
(Reading database ... 124357 files and directories currently installed.)
Preparing to replace linux-image-2.6.24-23-generic 2.6.24-23.46 (using .../linux-image-2.6.24-23-generic_2.6.24-23.48_i386.deb) ...
Done.
Unpacking replacement linux-image-2.6.24-23-generic ...
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.24-23-generic_2.6.24-23.48_i386.deb (--unpack):
 unable to make backup link of `./boot/vmlinuz-2.6.24-23-generic' before installing new version: Operation not permitted
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-23-generic
Found kernel: /boot/vmlinuz-2.6.24-16-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.24-23-generic_2.6.24-23.48_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

