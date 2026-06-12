---
title: "Help creating a logical partition inside an extended partition"
date: 2009-06-14
forum: Installation &amp; Upgrades
---

### Post by brncao on 2009-06-14
I tried to create a ntfs logical partition (120gb) inside an extended partition using Gparted, but I got an error message. Anyone know why I can't create a logical partition? Image attached*

---

### Post by merlinus on 2009-06-14
Did you click on the unallocated space and try to format it as ntfs?  Also, which version of gparted are you using, the one on the ubuntu cd or the live gparted?  The latter is a later version and may have more options.

---

### Post by brncao on 2009-06-14
I solved it. I had to check "round to cylinders" to get it to work.

---

