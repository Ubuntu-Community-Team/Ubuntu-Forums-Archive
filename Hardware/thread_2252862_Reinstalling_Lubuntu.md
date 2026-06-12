---
title: "Reinstalling Lubuntu"
date: 2014-11-15
forum: Hardware
---

### Post by flaymond on 2014-11-15
hey, i got Lubuntu on my pc now. Im try to reiinstall Lubuntu for good reason and failed when in part installing 'bootloader'. I found that FAT32 format solve everything (on articles and supports), but i dont see any FAT32 on my disk (pre-installed) partition settings. There just something similar like W95 FAT32(Failed), W95 FAT32 (LBA)  (Failed),Hidden W95 FAT32(Failed). NTFS and others not working too...I see the FAT32 format is available couple days ago. I don't know how to make it available again. So my question is :

How to enable format of FAT32 on disk (partitioner) so that i can reinstall finely. Any help is greatly appreciated!

---

### Post by sudodus on 2014-11-15
Please see my reply in this link[URL="http://ubuntuforums.org/showthread.php?t=2252833"]

how to install Lubuntu using USB?[/URL]

I suggest you continue with questions and discussion in the same thread instead of creating new threads about the same subject.

*Edit*:

You can use ***gparted*** to create a FAT32 file system on the USB drive. Install it if it is not available.

```
sudo apt-get install gparted
```

But if you use ***mkusb***, you need not format the USB drive.

- Or are you trying to install into an internal drive, and have the 'wrong file system'?

---

