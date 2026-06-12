---
title: "Unable to install linux-image-2.6.24-23-generic"
date: 2009-04-20
forum: Installation &amp; Upgrades
---

### Post by inhotz on 2009-04-20
**I'm not able to install the linux kernel image linux-image-2.6.24-23-generic. Here are details I receive from synaptic/Update Manager:**

> (Reading database ... 154235 files and directories currently installed.)
Preparing to replace linux-image-2.6.24-23-generic 2.6.24-23.48 (using .../linux-image-2.6.24-23-generic_2.6.24-23.52_i386.deb) ...
Done.
Unpacking replacement linux-image-2.6.24-23-generic ...
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.24-23-generic_2.6.24-23.52-i386.deb (--unpack):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-23-generic
Found kernel: /boot/vmlinuz-2.6.24-22-generic
Found kernel: /boot/vmlinuz-2.6.24-21-generic
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.24-23-generic_2.6.24-23.52_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install. Trying to recover:


**After that the following message pops up:**

> E: /var/cache/apt/archives/linux-image-2.6.24-23-generic_2.6.24-23.52_i386.deb: subprocess dpkg-deb --fsys-tarfile returned error exit status 2
[B]
Can somebody help me here? Any ideas?

Thanks in advance![/B]

---

