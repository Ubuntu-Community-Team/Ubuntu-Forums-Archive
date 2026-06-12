---
title: "Can't copy on USB disk, it is read only"
date: 2009-11-06
forum: Hardware
---

### Post by gpetrov on 2009-11-06
Removable disk inserted in Laptop with ubuntu 9.10 is shown on the desktop but is read only. I cant copy any files on it and i cant change permissions of it. PLS help

---

### Post by Zoot7 on 2009-11-06
Try running this:
```
sudo chmod -R 777 /media/<drive name>
```

Where drive name is the name of the USB drive, that'll enable everybody to be able to read and write from it.

---

