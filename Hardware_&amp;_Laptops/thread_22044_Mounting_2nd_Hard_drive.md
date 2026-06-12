---
title: "Mounting 2nd Hard drive"
date: 2005-03-25
forum: Hardware &amp; Laptops
---

### Post by Dachnaz on 2005-03-25
To be more concise, my problem is not mounting it. My problem is with permissions. How can I set the permissions on this second hard drive so that the first user can write to it? Every time I mount it, no matter how I do it, it claims the owner is 'root.' So I chowned it to the user and although it says I'm the owner it will not let me change permissions or write to it. What's wrong with it?

---

### Post by Psylon on 2005-03-30
[QUOTE=Dachnaz]To be more concise, my problem is not mounting it. My problem is with permissions. How can I set the permissions on this second hard drive so that the first user can write to it? Every time I mount it, no matter how I do it, it claims the owner is 'root.' So I chowned it to the user and although it says I'm the owner it will not let me change permissions or write to it. What's wrong with it?[/QUOTE]

In Debian I do a chown of the mount point AFTER the drive is mounted. I assume that Ubuntu has the same behavior.

zeus:/# ls -ld /local ; mount /dev/hda6 /local ; ls -ld /local
drwxr-xr-x  2 root root 4096 Sep 13  2004 /local
drwxr-xr-x  13 psylon psylon 4096 Mar 27 18:43 /local

Hope that helps...

---

