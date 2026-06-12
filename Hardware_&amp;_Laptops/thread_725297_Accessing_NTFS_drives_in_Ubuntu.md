---
title: "Accessing NTFS drives in Ubuntu"
date: 2008-03-15
forum: Hardware &amp; Laptops
---

### Post by ubuntoexpert on 2008-03-15
How can I find out where my NTFS partition is (like dev/hd1 etc), and how can I then mount it to be accessed in Ubuntu,

---

### Post by sandysandy on 2008-03-15
> **ubuntoexpert said:**
> How can I find out where my NTFS partition is (like dev/hd1 etc), and how can I then mount it to be accessed in Ubuntu,

code is sudo fdisk -lu

regards

---

### Post by taurus on 2008-03-15
Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ntfs-3g
sudo mkdir /media/hda1
sudo mount -t ntfs-3g /dev/hda1 /media/hda1
df -h
```
_Assuming_ /dev/hda1 is where your ntfs partition is.

---

