---
title: "i/o error when coping files"
date: 2007-12-07
forum: Hardware &amp; Laptops
---

### Post by ukeewu on 2007-12-07
Error "I/O error" while copying "/home/ukee...5.2.1].mkv".


That is the error message i receive when trying to move files from the laptop to my external hd.  hard drive is ext3......i thought that would cure the i/0 error, but it hasn't


any ideas as to a fix for this??

thank you in advance

---

### Post by ewr2san on 2007-12-10
First see if you can read the file in it's entirety:

dd if="/home/ukee...5.2.1].mkv" of=/dev/null bs=512k

That will read from the file "/home/ukee...5.2.1].mkv" and output it to nothingness. 

If you get a permission denied error reading the file then it's permissions. If it's a bad block in the file then it will go a while then fail.

---

