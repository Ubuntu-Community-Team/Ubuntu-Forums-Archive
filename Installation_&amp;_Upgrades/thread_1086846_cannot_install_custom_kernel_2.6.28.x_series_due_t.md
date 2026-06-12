---
title: "cannot install custom kernel 2.6.28.x series due to /lib/firmware"
date: 2009-03-04
forum: Installation &amp; Upgrades
---

### Post by graysky on 2009-03-04
When I attempt to install a custom compiled kernel (2.6.28.X) from debs on my system, I get the following error:

[color=blue]dpkg: error processing linux-image-2.6.28.7-em64t_1_amd64.deb (--install):
 trying to overwrite `/lib/firmware/atmsar11.fw', which is also in package linux-image-2.6.27.10-em64t
dpkg-deb: subprocess paste killed by signal (Broken pipe)
[/color]

Here is the complete log:
```
$ sudo dpkg -i linux-image-2.6.28.7-em64t_1_amd64.deb 
[sudo] password for squishy: 
(Reading database ... 144190 files and directories currently installed.)
Unpacking linux-image-2.6.28.7-em64t (from linux-image-2.6.28.7-em64t_1_amd64.deb) ...
Done.
dpkg: error processing linux-image-2.6.28.7-em64t_1_amd64.deb (--install):
 trying to overwrite `/lib/firmware/atmsar11.fw', which is also in package linux-image-2.6.27.10-em64t
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.27.10-em64t
Found kernel: /boot/vmlinuz-2.6.27-11-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Errors were encountered while processing:
 linux-image-2.6.28.7-em64t_1_amd64.deb
```

I know that I can remove my current functional linux-image through dpkg and then I can install the new one, but I'd like to keep both on the system.

[Here](http://technowizah.com/2005/12/debian-how-to-custom-kernel-compile.html) is the guide I have been using to compile a custom kernel on Intrepid.

There is also [this related](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/262783) bug over at launchpad.

---

### Post by x22 on 2009-03-05
dpkg -i --force-overwrite linux-image-whatever

---

### Post by graysky on 2009-03-27
> **x22 said:**
> dpkg -i --force-overwrite linux-image-whatever

...is that safe to do?

---

