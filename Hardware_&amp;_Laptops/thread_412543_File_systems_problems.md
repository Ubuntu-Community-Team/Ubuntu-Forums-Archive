---
title: "File systems problems?"
date: 2007-04-18
forum: Hardware &amp; Laptops
---

### Post by kevinsun on 2007-04-18
Hi,

Actually I found several problems related to a dual boot PC with Ubuntu and Windows:
1) I used a shared partition with FAT32 and I found that a dir created by Ubuntu won't be able to be read in Windows.
2) A text file modified by Ubuntu won't be able to be opend in windows
3) Ubuntu's fsck will not recognize long file name with Unicode file names

Any idea?
K

---

### Post by rmemm on 2007-04-18
Note, text files in linux use LF line terminators and in windows they are CR-LF.

Rob

---

### Post by rmemm on 2007-04-18
Oh.  To handle text file translation -- there are special mount options to do this automatically, or you can just use notepad2 under windows which understands CR, LF, and CR-LF line termination.

Rob

---

