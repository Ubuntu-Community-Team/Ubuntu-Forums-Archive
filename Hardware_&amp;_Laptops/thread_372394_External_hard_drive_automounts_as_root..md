---
title: "External hard drive automounts as root."
date: 2007-02-28
forum: Hardware &amp; Laptops
---

### Post by jackliddlephysics on 2007-02-28
I have recently bought an external hard drive for my laptop, which I have reformated as ext3.  When its plugged in it is automounted to /media/usbdisk/ and its owned by root

I have tried doing a chmod on this directory to my users permissions but this only changes the permissions of the path /media/usbdisk/ to mine and not the subdirectories.

Any ideas how to make it so it automounts as my user, or another usergroup which I am a member of

Thanks

Jack

---

### Post by kidders on 2007-02-28
Hi there,

Although you *can* technically do this if you really want to, it's not normal practice. Just like internal filesystems, root will tend to be the user that mounts them, but the files & directories *inside* the filesystem can be owned by anyone.

> **jackliddlephysics said:**
> I have tried doing a chmod on this directory to my users permissions but this only changes the permissions of the path /media/usbdisk/ to mine and not the subdirectories.Check out the **-R** switch in chmod's man page.

---

### Post by jackliddlephysics on 2007-02-28
OK

Looking at /media/ that makes sense.

Thanks for your help

---

### Post by kidders on 2007-02-28
No problem. :-)

---

