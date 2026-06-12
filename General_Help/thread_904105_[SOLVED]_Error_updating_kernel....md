---
title: "[SOLVED] Error updating kernel..."
date: 2008-08-28
forum: General Help
---

### Post by ikno0 on 2008-08-28
I'm a newbie to Ubuntu... I have Ubuntu Hardy 8.04 installed. I have come across the following problem and I have no idea how to solve it... On trying to install the linux-image-2.6.24-19-generic package it gives me the following error:

E: /var/cache/apt/archives/linux-image-2.6.24-19-generic_2.6.24-19.41_i386.deb: unable to make backup link of `./boot/vmlinuz-2.6.24-19-generic' before installing new version

I would really appreciate it if someone could help me out on this one...

---

### Post by cariboo on 2008-08-29
How are you updating the kernel? Maually or Synaptic/Update Manager?

Jim

---

### Post by ikno0 on 2008-08-29
Hi Jim, I have tried both methods but without success. When I do a sudo apt-get install it gives me the following error:

Preparing to replace linux-image-2.6.24-19-generic 2.6.24-19.34 (using .../linux-image-2.6.24-19-generic_2.6.24-19.41_i386.deb) ...
Done.
Unpacking replacement linux-image-2.6.24-19-generic ...
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.24-19-generic_2.6.24-19.41_i386.deb (--unpack):
 unable to make backup link of `./boot/vmlinuz-2.6.24-19-generic' before installing new version: Operation not permitted
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.24-19-generic_2.6.24-19.41_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

When I use the Synaptic Update Manager, it gives me the error message mentioned in my previous post.

---

### Post by ikno0 on 2008-09-02
I found the solution to my problem... Anyone who has the same problem and doesn't know what to do, you can try having a look at the following page:
[https://bugs.launchpad.net/wubi/+bug/252900](https://bugs.launchpad.net/wubi/+bug/252900) My thanks to those who provided the solution in the above-mentioned link.

Jason

---

