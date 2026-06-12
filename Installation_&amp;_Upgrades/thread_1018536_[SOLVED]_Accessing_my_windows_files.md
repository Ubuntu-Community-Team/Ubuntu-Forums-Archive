---
title: "[SOLVED] Accessing my windows files"
date: 2008-12-22
forum: Installation &amp; Upgrades
---

### Post by themagicmanfromtrent on 2008-12-22
How do I access my windows files from within ubuntu. It doesn't seem too happy to allow me to do this, giving me the following error:

Cannot mount the volume "OS".

---

### Post by taurus on 2008-12-22
Install ntfs-config and use it to configure your ntfs partition.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```
Otherwise, post the outputs of these commands here.

```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by themagicmanfromtrent on 2008-12-23
Perfect thanks!!

---

