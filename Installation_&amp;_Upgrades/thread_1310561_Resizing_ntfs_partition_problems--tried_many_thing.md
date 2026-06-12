---
title: "Resizing ntfs partition problems--tried many things!"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by Spartachris on 2009-11-01
Even after reading all I could find about it in other threads, I'm having problems resizing a ntfs partition using gparted. What I've got is one hard drive setup like this:

sda1: ntfs (storage, no OS)
sda3: / ext4
sda4: /home ext4
sda2: extended
sda5: linux-swap

sda5 is inside(?) sda2.

What I've done is used a Live CD (9.10 amd64) and made sure I had ntfsprogs and ntfs-3g installed. I've also used

```
sudo swapoff /dev/sda5
```

But no matter, I can resize the ntfs partition. Gparted won't let me do anything to it. I can resize or move the / partition and the /home partition no problem. 

Does anyone know what I can do?

Thanks!

---

