---
title: "Computer not recognizing flash disks"
date: 2007-08-05
forum: Hardware &amp; Laptops
---

### Post by ownaginatious on 2007-08-05
For some reason when I plug flash memory (i.e. SD-Cards and CF-Cards) into either my Sandisk ImageMate 12 in 1, or my epson r300 printer, Ubuntu (7.0.4) simply doesn't recognize them! The strange thing though is that when I do it while Amarok is running it will detect the cards, and suddenly the card shows up in the file browser. Is there some setting that's not working that is supposed to tell ubuntu to auto detect flash memory cards?

Also, for some reason the computer will detect my external harddisk upon plugging it in, which is kind of strange, but I can't seem to write to it (NTFS Partition), and Ubuntu doesn't let me eject it either...

CAn anyone help me with these two problems? It would be greatly appreciated :) Thanks!

---

### Post by VMan on 2007-08-05
Sometimes, my laptop (Toshiba A135-S4467) will not detect a SD card when it is inserted into the built-in reader.  All I have to do is remove it and re-insert it and it will detect it the next time.  I have no clue as to what is causing this.  I don't use the card reader very often so I can't really tell you how often this occurs.

As to your external HD, the external USB HD's must be manually ejected.  Also, Ubuntu 7.04 will not write to NTFS partitions by default.  You have to install a package (don't remember the name) to enable this.  I didn't install it since I didn't need it.  I do remember that the package said it was still experimental.  Hopefully someone who uses it will chime in with the name and configuration details for you.

---

### Post by ownaginatious on 2007-08-05
No matter how many times I plug in, and then unplug the flash cards, they aren't detected :(

---

### Post by jfinkels on 2007-08-05
> **ownaginatious said:**
> For some reason when I plug flash memory (i.e. SD-Cards and CF-Cards) into either my Sandisk ImageMate 12 in 1, or my epson r300 printer, Ubuntu (7.0.4) simply doesn't recognize them! The strange thing though is that when I do it while Amarok is running it will detect the cards, and suddenly the card shows up in the file browser. Is there some setting that's not working that is supposed to tell ubuntu to auto detect flash memory cards?

Also, for some reason the computer will detect my external harddisk upon plugging it in, which is kind of strange, but I can't seem to write to it (NTFS Partition), and Ubuntu doesn't let me eject it either...

CAn anyone help me with these two problems? It would be greatly appreciated :) Thanks!

For NTFS read/write access, you will need to install the NTFS 3G drivers: [http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

---

