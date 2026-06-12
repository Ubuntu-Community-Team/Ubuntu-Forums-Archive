---
title: "disks not detected after installation"
date: 2007-04-01
forum: Hardware &amp; Laptops
---

### Post by beyti7 on 2007-04-01
I've installed ubuntu edgy clearly but then realized that no sata drives were detected, only the 40gb of IDE was detected and it has the linux(: one of the other drives has windows xp prof.

Some of my friends told me that I missed the ticking operation in the installation to make them detected. Is there any way to make them detected now?like editing fstab or sth?Because they can be seen in the device manager, but not in the file system):

They are full of data and I can't format them): 
Both of them are sata (one of 'em is 80gb and the other is 200gb)

---

### Post by beyti7 on 2007-04-02
Did I open the thread in the wrong place or really there's noone to reply it? ):
please..

---

### Post by taurus on 2007-04-02
What's the output of this command from a terminal?  You probably need to mount your XP partition before you can use or access it.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

