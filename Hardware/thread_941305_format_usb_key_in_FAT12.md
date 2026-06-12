---
title: "format usb key in FAT12"
date: 2008-10-08
forum: Hardware
---

### Post by formol on 2008-10-08
hello,

is there anyway to format a usb key into FAT12?

I want to disguised a usb key into a 1.4mb floppy disk.

thank you

---

### Post by Partyboi2 on 2008-10-09
Maybe you could try the mkdosfs. eg.
```
 sudo mkdosfs -F 12 /dev/sdc1
```
change /dev/sdc1 to what ever it is.
You can read more by typing in a terminal
```
man mkdosfs
```

---

