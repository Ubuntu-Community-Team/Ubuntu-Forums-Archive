---
title: "How do I format my mp3 player (need FAT32)?"
date: 2008-04-19
forum: Hardware &amp; Laptops
---

### Post by Alex&amp;Linux on 2008-04-19
Hey guys, my Samsung yp-t9j needs to be formated with FAT32, how would I go about that with Ubuntu?

The problem is that when I remove files, the player doesnt free up space.

---

### Post by ibutho on 2008-04-19
Plugin the device and run dmesg. Dmesg will show you the device and its device name. If the player has been automatically mounted, unmount it and then run mkfs.vfat e.g.
```
sudo umount /dev/sdb1
sudo mkfs.vfat /dev/sdb1

```
Change /dev/sdb1 to your actual device name. Once the process is complete, you can remove the disk and plug it back in.

---

### Post by Alex&amp;Linux on 2008-04-19
Yep, like a charm!
Thanks a lot!

---

