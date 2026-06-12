---
title: "USB Stick mounted with reduced available space"
date: 2007-05-18
forum: Hardware &amp; Laptops
---

### Post by zeus_ex_machina on 2007-05-18
Hello all. I recently installed Feisty on my machine and I'm still trying to make it work. My main problem is the lack of drivers for my onboard VGA but that's a tale for another thread.

I came here because Ubuntu is incorrectly mounting my USB stick. Specifically, it recognizes it as 1GB  but mounts it as 250MB. The device is formatted as FAT32 to be compatible with all my machines and currently contains about 200MB of data. I have looked into the man pages of mount but i don't see how to change the number of heads/cylinders/sectors which apparently determine size. I did try mounting it with a different blocksize but it cannot be mounted that way, ubuntu gives an error message (invalid mount option). Same thing if i try to mount as usbfs.

What am i doing wrong? Should i just reformat the drive to NTFS?

---

### Post by Kobalt on 2007-05-18
Try to plug out your stick then run ```
sudo rmmod ehci_hcd
```And then plug it back in...

---

