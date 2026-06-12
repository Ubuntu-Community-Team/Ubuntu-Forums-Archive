---
title: "Grub loader with Windows"
date: 2008-11-09
forum: General Help
---

### Post by LegendofTom on 2008-11-09
So, I recently installed Intrepid over a windows install, and wanted now to put windows on a separate hard drive.  I edited menu.lst, but to no avail.  Now all I receive when I choose my Windows partition at the grub loader is Starting Up...., and nothing more.  Any thoughts?

---

### Post by meierfra. on 2008-11-09
try this for your windows item in menu.lst:

title  Windows
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1


If this does not work, or you need more help post the output of


```
sudo fdisk -l

cat /boot/grub/menu.lst
```

---

### Post by LegendofTom on 2008-11-09
Hey what do you, that did the charm.  Thanks alot.

---

