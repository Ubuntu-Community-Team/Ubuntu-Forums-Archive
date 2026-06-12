---
title: "Card reader read only"
date: 2009-09-10
forum: Hardware
---

### Post by mihaicj on 2009-09-10
I have a Kingston MobileLite card reader with a 4GB SD card with a FAT32 file system. When I plug the reader to my computer the card shows up to be read only. Permissions seem OK, but it says read only file system. How could I get my card to appear read-write?

---

### Post by Fafler on 2009-09-10
I had a cardreader once that didn't detect the read only notch on SD cards correctly. Do you have a MMC card? Are you able to write to it? In that case the solution is to manipulate the switch in the card reader to think all cards are writeable.

EDIT: Come to think of it, the filesystem might just be bad. Try unmounting/mounting from a terminal and look for any errors.

---

### Post by mihaicj on 2009-09-10
I tried to mount it from the command line.
```
mount: block device /dev/sdb1 is write-protected, mounting read-only
```

---

### Post by Fafler on 2009-09-10
That sounds like it thinks it's writeprotected in hardware. There should be a small switch on the cardwreader along the side where the write protect notch is. Try manipulating it with a small object when inserting the card or try masking tape along the side if the card.

---

