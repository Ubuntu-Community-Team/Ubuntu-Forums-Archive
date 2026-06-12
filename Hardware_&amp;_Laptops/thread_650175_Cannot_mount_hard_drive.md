---
title: "Cannot mount hard drive"
date: 2007-12-26
forum: Hardware &amp; Laptops
---

### Post by theycallmetexas on 2007-12-26
In the beginning, I was using Gnome but then I decided I want to try out KDE, just for the fact that I've never used it.

Well, in Gnome I was able to view my second hard drive (which is NTFS), but after I installed KDE and booted into it, I wasn't able to read/write. I get this message:

> hal-storage-fixed-mount-all-options refused uid 1000

Any suggestions?

---

### Post by theycallmetexas on 2007-12-26
oh, nevermind guys, i found a way to fix it.

ntfs-3g was installed
but i had to install ntfs-config, and i got it working.

---

