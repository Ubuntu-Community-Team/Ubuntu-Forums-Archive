---
title: "How do you find your hard drive format?"
date: 2006-11-27
forum: Hardware &amp; Laptops
---

### Post by fxer on 2006-11-27
How can I find out how my hard drive is formatted? Is it ext3, XFS, ReiserFS etc?

---

### Post by mssever on 2006-11-27
Type mount. You'll get a list of all mounted partitions with their mount options, including type. Or, you can look in /etc/fstab.

---

