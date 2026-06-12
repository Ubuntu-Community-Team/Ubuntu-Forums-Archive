---
title: "Files missing on my FLASH CARD"
date: 2007-05-22
forum: Hardware &amp; Laptops
---

### Post by xodeus on 2007-05-22
Hi when I transfer files through USB2 to my Phone (SonyEricsson k610), it seems that ubuntu transfers the files  very fast. then when i try to eject the device i get a warning about still writing files. but it never stops an i can't find any files on the device? are there any other way to transfer the files, like on-the-fly?

Ubuntu 7.04
Gnome 2.18.1

---

### Post by taurus on 2007-05-22
You're supposed to unmount it first before you can eject it from your machine.  Ejecting it without unmount first can damage the files and the device too.

---

### Post by xodeus on 2007-05-22
No with eject I mean that I rightclick the icon on desktop and select Eject device...
Then it tells me that it's still writing files. But nothing happens I think.
It never finishes...
No files are present in the folders i choose to copy them to.
Is it possible to transer files in any other way?

---

### Post by taurus on 2007-05-22
You can always try to write or copy files to it from a terminal.

```
cp filename mount_point
ls -la mount_point
sudo umount mount_point
```
Replace the mount_point with the actual mount point of your flash card.

---

### Post by xodeus on 2007-05-22
Will the terminal copy my files on the fly or do the cache trick?

Is the above a hidden thing in gnome that can be changed?

---

### Post by xodeus on 2007-05-23
Found that terminal does the same trick as gnome do. Just copy the files to a strange cache somewhere and transfer the files slowly? But is it possible to see the traffic between the computer and the card?

---

