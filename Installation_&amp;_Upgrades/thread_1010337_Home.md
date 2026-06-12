---
title: "Home"
date: 2008-12-13
forum: Installation &amp; Upgrades
---

### Post by Robbyx on 2008-12-13
My fstab says that my home is at 

#/dev/sda2  being new "home"
UUID=45a2e92c-c759-4732-9662-988da7f8ea7b /home  ext3    nodev,nosuid,user_xattr    0       2

How do I  find out which disk is corresponding to the UUID?

Robin

---

### Post by taurus on 2008-12-13
Applications -> Accessories -> Terminal
```
sudo blkid
```

---

