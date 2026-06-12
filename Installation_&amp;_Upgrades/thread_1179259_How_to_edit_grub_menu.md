---
title: "How to edit grub menu"
date: 2009-06-05
forum: Installation &amp; Upgrades
---

### Post by anthonyleamy on 2009-06-05
My grub menu is booting into sda 6 partition instead of sda 5 when I try to access mu other OS

How can I access the grub menu file to change this? Am not sure about the command.Is it....?

sudo edit /boot/grub/menu.lst 

Thanks

---

### Post by merlinus on 2009-06-05
```

gksudo gedit boot/grub/menu.lst

```

---

### Post by dalexnagy on 2009-09-27
The command should read: gksudo gedit /boot/grub/menu.lst

---

