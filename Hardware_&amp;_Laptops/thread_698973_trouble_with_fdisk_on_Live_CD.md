---
title: "trouble with fdisk on Live CD"
date: 2008-02-16
forum: Hardware &amp; Laptops
---

### Post by NFITC1 on 2008-02-16
I'm trying to upgrade my HDD in my lappy and I'm trying to use lfdisk to copy partitions from the internal HDD to a USB mounted HDD. Probably not the most efficient way to do such a thing, but it's easy. I used gparted to partition the USB drive, which seemed to go well. Anyway, since fdisk won't copy from a mounted drive I have to use a Live CD to do it. I had to REpartition the USB drive when I loaded the Live CD. However, when I'm in fdisk via

```
sudo fdisk /dev/sdb
```
I get into the menu just fine, hit 'x' for expert entry, but fdisk doesn't seem to notice that I'm in expert mode. If I hit 'm' it brings up the basic commands. If I hit 'o' for copy it pretends it didn't get any input and lets me select again. If I type something I know isn't an expert command it'll tell me that it's not a valid command and display the basic command menu again. What's wrong with this fdisk?
```
ubuntu@ubuntu:/dev$ fdisk -v
fdisk (util-linux-ng 2.13)
```

What other means might I pursue to get this copied?

---

