---
title: "Having trouble mounting portable hard drive"
date: 2009-02-18
forum: Hardware
---

### Post by LT.Was on 2009-02-18
Can anyone tell me how to force mount my hard drive?

I'll probably have more questions once I get started, as I'm new to Linux.

---

### Post by konqueror7 on 2009-02-18
no one?

well, you could install ntfs-config in the Add/Remove or in the terminal by
```
sudo apt-get install ntfs-config
```

this will allow you to mount ntfs partitions graphically...

or you could try...
```
sudo mount -a
```
this will mount all drives found in the fstab file...

or you could check out this [guide]("http://www.linuxtopia.org/online_books/system_administration_books/ubuntu_starter_guide/ch05.html")

its your choice... ;)

better choose the first one...btw, what version of ubuntu are you using?

---

### Post by LT.Was on 2009-02-18
8.10

---

### Post by konqueror7 on 2009-02-18
ah okay, the first method should work then, i'm also using 8.10...

---

