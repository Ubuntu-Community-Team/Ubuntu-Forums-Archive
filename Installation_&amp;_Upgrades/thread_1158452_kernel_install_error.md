---
title: "kernel install error"
date: 2009-05-13
forum: Installation &amp; Upgrades
---

### Post by linux_ocean on 2009-05-13
Hi every body.
I have a problem in installing kernel 2.6.29.2.
I can configure and compile the kernel and after that it create 2 .deb file for install, but when I want to install it, I receive the error bellow:

```
hossein@polaris-desktop:~/kernel_source$ ls
linux-2.6.29.2  linux-2.6.29.2.tar.bz2  linux-headers-2.6.29.2-custom_2.6.29.2-custom-10.00.Custom_amd64.deb  linux-image-2.6.29.2-custom_2.6.29.2-custom-10.00.Custom_amd64.deb
hossein@polaris-desktop:~/kernel_source$ sudo su
[sudo] password for hossein: 
root@polaris-desktop:/home/hossein/kernel_source# dpkg -i linux-image-2.6.29.2-custom_2.6.29.2-custom-10.00.Custom_amd64.deb 
Selecting previously deselected package linux-image-2.6.29.2-custom.
(Reading database ... 194391 files and directories currently installed.)
Unpacking linux-image-2.6.29.2-custom (from linux-image-2.6.29.2-custom_2.6.29.2-custom-10.00.Custom_amd64.deb) ...
Done.
Setting up linux-image-2.6.29.2-custom (2.6.29.2-custom-10.00.Custom) ...
Running depmod.
Finding valid ramdisk creators.
Using mkinitramfs-kpkg to build the ramdisk.
Running postinst hook script update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.29.2-custom
Found kernel: /vmlinuz-2.6.28-12-generic
Found kernel: /vmlinuz-2.6.28-11-generic
Found kernel: /memtest86+.bin
Replacing config file /var/run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
run-parts: executing /etc/kernel/postinst.d/nvidia-common
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 20
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.29.2-custom.postinst line 1186.
dpkg: error processing linux-image-2.6.29.2-custom (--install):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.29.2-custom

```

what's your idea about this problem?
thank you.

---

