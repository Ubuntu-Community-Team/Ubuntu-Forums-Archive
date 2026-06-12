---
title: "Please help me with disk recovery"
date: 2007-10-01
forum: Hardware &amp; Laptops
---

### Post by Captain Rotundo on 2007-10-01
I have a single 400 GB disk with a ext3 partition that takes the entire disk.  I need either a program that can attempt to read the entire disk copying whatever it can to another disk, or a way to force the partition to mount. 

I can not seem to mount the partition because the needs_recovery flag is set, but the disk is in such bad shape that no writes will succeed, therefore it can never be satisfied and clear the needs_recovery bit.  I don't know if any of the data is still viable on this disk but it is exceedingly important that I recover what I can.

---

### Post by Captain Rotundo on 2007-10-01
ok the data is for the most part good, as photorec is able to pull a lot of stuff off, is there a similar program to photorec that attempts to recover filenames, and perhaps makes an attempt a recovering fragmented files.  Photorec is awesome, but not quite as a robust as a hard disk recovery tool compared to for its original purpose of memory cards.

---

### Post by Captain Rotundo on 2007-10-02
In case someone else find this thread this is what I did:

1. used GNU ddrescue to make an image of the partition that was bad:
  sudo ddrescue /dev/sdb1 disk_image
2. setup the image as a loopback device:
  losetup /dev/loop0 disk_image
3. Check the image for errors:
  fsck -C -p /dev/loop0
4. Mounted the image and removed all the files.

Worked flawlessly.

---

