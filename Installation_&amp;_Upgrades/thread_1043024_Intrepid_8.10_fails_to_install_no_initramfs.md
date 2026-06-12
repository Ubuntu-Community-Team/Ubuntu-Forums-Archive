---
title: "Intrepid 8.10 fails to install no initramfs"
date: 2009-01-18
forum: Installation &amp; Upgrades
---

### Post by hal8000 on 2009-01-18
The live Intrepid 8.10 CD boots and loads no problem.
When I use the installer, it crashes with an ubiquity error and I've filed a bug report. (Other users have the same bug).


After ubiquity crashes, my partition to install to, /dev/sda11 is mounted with a mountpoint /target

I can browse the contents of /target/boot and see that no initial ramfilesystem or ramdisk is ever created, consequently I cannot boot.

I tried coping the kernel,initramfs and modules from 8.04 to the new 8.10 partition and modifying grub, but that still fails to boot with error 2, bad file descriptor.


As I have multi boot I choose not to install grub at all and modify my existing grub loader.

Using the live CD I note that kernel 2.6.27.7 is in use but when I browse the contents of /boot with the live CD I notice there is only a kernel no initrd or ramfs.

Is the Intrepid kernel monolithic in respect that all file systems required to boot are now contained in the kernel?

Also please could someone who has a working Intrepid system post the following:
ls /boot

cat /boot/grub/menu.lst

This will help me to resolve my problem, thanks in advance.

---

