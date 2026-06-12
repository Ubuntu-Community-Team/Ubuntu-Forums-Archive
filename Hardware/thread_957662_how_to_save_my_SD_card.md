---
title: "how to save my SD card"
date: 2008-10-24
forum: Hardware
---

### Post by govi on 2008-10-24
I made a SD card as a bootable card to install the ubuntu eee. but after the installation, the card can not be read under windows. I can format it and even delete the partition under ubuntu but not under win. how could I make it works under win?

---

### Post by Crandom on 2008-10-24
You need to shrink a partition (using gparted) and then add another one as FAT32. Put the files there that you want to be able to see in windows/mac/*nix.

Alternatively, if you only want to be able to see the files on _one_ windows machine, install this: [Ext2 IFS for Windows](http://www.fs-driver.org/) on your windows pc. It will allow you to read and write to ext2 and ext3 partitions like that you have on your SD card. Be warned, you still won't be able to see your files on other windows pcs where the IFS Drivers have not been installed.

---

