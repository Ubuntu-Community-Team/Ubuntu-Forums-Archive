---
title: "Mounting problem, Ubuntu release/archive mirror"
date: 2008-09-16
forum: General Help
---

### Post by marchost on 2008-09-16
Here is my problem. I have a Xen domain with 2 partitions :

/dev/hda : 100GB, free space 95GB (mounted to /)
/dev/hdb : 469GB, free space 15GB (mounted to /var/www/mirrors/)


On /var/www/mirrors I have Ubuntu, Centos & Kernel.org mirrors :

ubuntu/ (+= 300gb)
centos/ (+- 100gb)
pub/ (+- 54GB)

Right now everything works fine but in the event that Ubuntu or Centos get out a new version (such as 8.10 for Ubuntu), I will be out of space on /dev/hdb

This is a live server, I cannot try crazy things and also Xen gives me some limitation on partitioning...

A simple solution would be to use the almost empty /dev/hda for the kernel.org mirror.

How can I use /dev/hda which is mounted under / to be also available ONLY in /var/www/mirrors/pub (dont forget /dev/hdb is mounted under /var/www/mirrors)

So basically, to be clear, what I need :

/var/www/mirrors/ubuntu ---> /dev/hdb
/var/www/mirrors/centos ---> /dev/hdb
/var/www/mirrors/pub ---> /dev/hda

and to keep /dev/hdb mounted under /var/www/mirrors

Any help would be appreciated.

---

### Post by marchost on 2008-09-16
found my answer...

mount --bind /whatever /var/www/mirrors/pub

where /whatever is on /dev/hda

---

