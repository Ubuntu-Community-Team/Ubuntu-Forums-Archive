---
title: "Configuring Grub"
date: 2008-09-10
forum: General Help
---

### Post by Jiffyman on 2008-09-10
I need some help configuring grub so I can boot an existing  windows installation from a secondary sata drive which is in Native IDE mode. I already have Ubuntu installed on an IDE hard disk.

---

### Post by Pro-reason on 2008-09-11
Please post the output of the following commands (in the terminal):

```

sudo fdisk -l
sudo blkid

```

Use the **#** button in the toolbar to put [noparse]```
...
```[/noparse] tags around it.

---

### Post by caljohnsmith on 2008-09-11
It would also be helpful if you would post your menu.lst:
```
cat /boot/grub/menu.lst
```
We can use that to figure out which HDD you are booting off of, and that will determine how to add windows to Grub's menu.

---

### Post by Nepherte on 2008-09-11
An entry for windows in grub would look something like this:
```
title		Microsoft Windows XP Professional SP3
root		(hd0,0)
savedefault
chainloader	+1
```
You will have to change hd0,0 to the location where windows is installed.

---

