---
title: "[SOLVED] how to delete my ubuntu partition with gparted?"
date: 2008-08-04
forum: General Help
---

### Post by mahela007 on 2008-08-04
Hello. I have uninstalled grub and now i want to remove the linux partitions on my hard disk. (i have to remove ubuntu because I dont have enough space on my hard disk)
where can i find instruction on how to do this?
I dont have a windows cd.
And none of the linux live cds i have will boot. Is it possible to delete the ubuntu partition and then resize the windows partition with gparted live CD?

---

### Post by geirha on 2008-08-04
It is quite possible to do that with the gparted live CD, yes :)

---

### Post by prshah on 2008-08-04
> **mahela007 said:**
> Hello. I have uninstalled grub and now i want to remove the linux partitions on my hard disk. 

Yes, you can remove them with the gparted (or any other) live CD. Most importantly, when you boot off a live CD, the swap space will be automatically activated. When active, it can't be deleted. Turn it off with ```
sudo swapoff /dev/sdx9
``` (Replace /dev/sdx9 with the actual device for your swap partition).

Or you can do it from Windows; Click Start-Run ```
diskmgmt.msc
``` and then right click-delete your linux/swap partitions.

---

### Post by mahela007 on 2008-08-04
thanks for your responses. Does that mean there should be no problem with windows if the windows partitions are resized?
where can I get instruction on how to do this?

---

### Post by geirha on 2008-08-04
Should is the key word. It works and has been tested alot, but do take backup of your important data. Things can always go wrong. If your computer loses power in the middle of the procedure for instance, you may lose data.

This page shows basic usage of gparted. The GUI is fairly intuitive.
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by mahela007 on 2008-08-04
thanks for your help

---

