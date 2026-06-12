---
title: "Portable Ubuntu"
date: 2009-09-03
forum: Installation &amp; Upgrades
---

### Post by Gianl09 on 2009-09-03
I have created on a USB drive a nice, persistent version of Ubuntu 9.04 with all my customizations that is portable across various computers I use. The problem is that the USB drive I started with is a 4GB drive and I would like to have more space. Is there a way to copy the whole thing to another (larger) drive and take advantage of the extra space? Thanks

---

### Post by fatbotgw on 2009-09-03
You could use gParted to copy the partition to the other drive.  

You could also just install a fresh copy on the new drive and then copy all the files from the old to the new drive.

---

### Post by ronparent on 2009-09-03
Yes. The simple way is to just copy the partition to the new usb. Use gparted froma a live cd to delete existing partitions from the new usb and leave sufficient unallocated space for the copy. You can use gparted to also copy (or cut) and paste from the old usb to the new. After pasting the partition to the new usb drive then expand the partition to the size you want. You would then setup grub to boot to the new drive (probably in the mbr oof the usb?).

Since you now have a copy, the uuid of the new drive is identical to the original. If you have grub in the mbr of the hard drive it will have no problem finding ubuntu on the new usb.

---

