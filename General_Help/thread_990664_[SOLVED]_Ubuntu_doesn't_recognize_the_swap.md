---
title: "[SOLVED] Ubuntu doesn't recognize the swap"
date: 2008-11-22
forum: General Help
---

### Post by L337_K3y5 on 2008-11-22
I just resized my swap from 1.92 gigabytes to 8.03 gigabytes using the 64 bit live CD and now when I boot into Ubuntu and go to system monitor it says it's using 0 bytes (o.o%) of 0 bytes???  I do remember turning the swap off temporarily to upgrade the swap size, but afterwards I appended the swap again to it and reformatted the swap to a Linux-swap.  It should have worked, but the first time I tried it gave my a busy error when it tried to resize the swap to the new size, but it didn't do anything else to it so I tried it again and it worked.  Also, after doing a ext3 check on my Ubuntu partition, whenever I boot instead of the nice loader bar I now get just scrolling white text that says at the top at first something like running at ext3 something or other and it's annoying.  Is there a command line way to affix the swap partition to the Ubuntu partition because somewhere along the way there's no recognition of the swap.

EDIT - The white text says EXT3-fs:  "running as ordered data mode" and it's running on some internal level or command 5 or something like that.

---

### Post by louieb on 2008-11-23
New swap partition = new swap partition UUID. You need to update **/etc/fstab** with the new swap parttions UUID.
to find the new swap partitions ```
use sudo blkid
```

Just wondering why so large a swap partition. The old advice of 2x memory was given when 128MB of memory was a lot.  Unless it s a computer I want to hibernate i use 1/4GB to 1/2GB for swap no matter how how much memory it has.

---

### Post by L337_K3y5 on 2008-11-23
Yeah, I want it to be able to hibernate, and I'm upgrading it to 4gb memory, plus the swap size before was a little bit more low than the ram I have so I had problems with suspend.

---

