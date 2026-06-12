---
title: "Ubuntu can't see my 32GB ntfs thumb drive"
date: 2013-12-25
forum: Hardware
---

### Post by danny20 on 2013-12-25
Nothing happens, when plugged. Blkid doesn't see it either. No luck with Disks as well. It's like it isn't there at all. The thumb drive shows up just fine under windows computers. The ubuntu computer finds just fine other (smaller and fat16 drives)
  So, is it the size, is it the file system or maybe the fact that ubuntu runs on macbook pro?

---

### Post by ian-weisser on 2013-12-25
Check the kernel messages in /var/log/dmesg showing that the system detected a plug/unplug.
If detected, they will be the bottom 5-10 lines of the file. You can tell by the timestamp at the beginning of each line.
If you are not sure what the kernel messages mean, then paste the lines here.

---

### Post by electrohandyman501 on 2013-12-25
Ok I have to ask.... I gather you are a working with a Mac? Is the USB port active? can you see anything else plugged into it? are there other ports on the machine to try.

---

### Post by danny20 on 2013-12-25
it's active since it finds just fne other smaller thumb drives that are formatted in FAT

---

### Post by danny20 on 2013-12-28
anyone?

---

### Post by ian-weisser on 2013-12-28
What did /var/log/dmesg show?

---

