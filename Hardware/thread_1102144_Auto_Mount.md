---
title: "Auto Mount?"
date: 2009-03-21
forum: Hardware
---

### Post by chubble10 on 2009-03-21
Is there any way to auto-mount internal hard drives on startup in GNOME?

---

### Post by taurus on 2009-03-21
If you want it to mount each time you boot Ubuntu, you need to add an entry in /etc/fstab.

Which partition and what filesystem you want to automount?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

