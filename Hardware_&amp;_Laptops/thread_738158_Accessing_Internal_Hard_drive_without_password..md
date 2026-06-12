---
title: "Accessing Internal Hard drive without password."
date: 2008-03-28
forum: Hardware &amp; Laptops
---

### Post by Atrus6 on 2008-03-28
I put another HD in my computer yesterday and is their anyway to mount it without having to enter in a password everytime?

---

### Post by gavinjb on 2008-03-28
you should be able to enter an entries in fstab to get the partitions to mount on startup, as I am not at my pc at the moment I cant help with the syntax, but I am sure there is someone which can help, if you know your device names (/dev/sdb1 etc...) then it usually is fairly simple to do, just copy an entry from another drive already mounted created an mount point (usually in /media) and then after saving the fstab file and just run sudo mount -a to mount there and then.

---

### Post by Atrus6 on 2008-03-29
I can find the file, but I don't where to find that particular drives information.  I tried right click and going to properties, while the drive is mounted and not mounted, and I can find what I (think), I am looking for.

---

