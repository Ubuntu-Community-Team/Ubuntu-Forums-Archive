---
title: "completely uninstall ubuntu"
date: 2009-01-27
forum: Installation &amp; Upgrades
---

### Post by uttaran on 2009-01-27
I've a dual boot of ubuntu and windows. I don't want ubuntu since it is not running in my hardware. How can i uninstall it neatly so that i can boot into windows without formatting??????????

---

### Post by aheckler on 2009-01-27
Boot to the Ubuntu LiveCD and use the partition editor to delete Ubuntu's partitions and expand the Windows partition.

---

### Post by oldos2er on 2009-01-27
First thing would be to restore Windows' boot loader, then remove Ubuntu's partition(s).

---

### Post by uttaran on 2009-01-28
how to restore windows boot loader???

---

### Post by Partyboi2 on 2009-01-28
If you are using xp you can boot a xp installation disk and enter recovery, then when at the prompt type
```
fixmbr
```
If you don't have a installation disk you can use [[COLOR=Blue]supergrub[/COLOR]]("http://www.supergrubdisk.org/") to [[COLOR=Blue]restore[/COLOR]]("http://www.supergrubdisk.org/wiki/UninstallGRUB") windows boot loader.

---

