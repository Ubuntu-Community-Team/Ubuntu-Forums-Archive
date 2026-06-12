---
title: "Kernel Compile Fail [trigger_code_fix.bin]"
date: 2009-03-25
forum: Installation &amp; Upgrades
---

### Post by melcron on 2009-03-25
blah@mainframe:/usr/src/linux# cd .. && dpkg -i linux*2.6.29*.deb
Selecting previously deselected package linux-image-2.6.29.
(Reading database ... 128377 files and directories currently installed.)
Unpacking linux-image-2.6.29 (from linux-image-2.6.29_386_amd64.deb) ...
Done.
dpkg: error processing linux-image-2.6.29_386_amd64.deb (--install):
 trying to overwrite `/lib/firmware/kaweth/trigger_code_fix.bin', which is also in package linux-image-2.6.28.8
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.27-11-generic
Found kernel: /boot/vmlinuz-2.6.27-7-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Errors were encountered while processing:
 linux-image-2.6.29_386_amd64.deb

---

### Post by melcron on 2009-03-27
No one else is having this problem compiling their kernel?

---

