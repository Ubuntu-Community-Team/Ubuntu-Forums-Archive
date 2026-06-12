---
title: "quick question regarding files visable in ubuntu on vista partition"
date: 2009-01-29
forum: Installation &amp; Upgrades
---

### Post by ohmyjibbonjones on 2009-01-29
hey guys,
just about to install ibex 8.10 64bit os on my laptop but i need to keep vista due to my dependence on my ipod =(.
if i make a 10GB partition and install ubuntu on that will i still be able to see my files in my windows partition (235gb) and be able to access them i.e play music,watch movies etc.
also if i download somthing in ubuntu can i save it to my vista partition?
thanks for your time

---

### Post by taurus on 2009-01-29
Yes, you can mount and access your windows partition just fine in Ubuntu.  If your windows partition doesn't mount automatically right after you installed Ubuntu, you can configure it using ntfs-config.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```

---

