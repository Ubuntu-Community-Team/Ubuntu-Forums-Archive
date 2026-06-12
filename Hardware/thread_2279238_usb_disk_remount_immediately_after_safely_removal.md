---
title: "usb disk remount immediately after safely removal"
date: 2015-05-22
forum: Hardware
---

### Post by marava1 on 2015-05-22
Hi, I am having this strange issue: one of my external usb disk remount itself immediately after i do the "safely removal".  It does not happen with other usb disks.
All the disks has the same mounting property: nosuid, nodev, nofail, noauto, x-gvfs-show.
Can anybody help me?
I am using 15.04

---

### Post by Vladlenin5000 on 2015-05-22
Is it by any chance a WD Touro? I've been experiencing the same behaviour with that one only, in each and every Ubuntu machine I connect it to.
Sorry, at the moment I have no solution. I just live with it and shutdown the computer before unplugging it in order to avoid issues.

---

### Post by dino99 on 2015-05-22
have you set a /etc/fstab entry for that device ?

---

### Post by Vladlenin5000 on 2015-05-22
> **dino99 said:**
> have you set a /etc/fstab entry for that device ?

No, I didn't (that's the puzzling part). As a matter of fact I never do for external drives.

---

