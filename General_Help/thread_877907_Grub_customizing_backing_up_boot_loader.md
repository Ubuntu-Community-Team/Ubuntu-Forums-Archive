---
title: "Grub customizing: backing up boot loader"
date: 2008-08-02
forum: General Help
---

### Post by And6ate9 on 2008-08-02
Hey everyone I would like to know how i can backup the boot loader or boot record before I start cuztomizing grub.

Thank you

---

### Post by caljohnsmith on 2008-08-02
To backup the MBR of HDD "sda" to a file called "boot.mbr":
```
dd if=/dev/sda of=/path/boot.mbr bs=512 count=1
```
Hope that helps. :)

---

