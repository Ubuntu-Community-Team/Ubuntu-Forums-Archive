---
title: "format on ext. HDD"
date: 2007-11-06
forum: Hardware &amp; Laptops
---

### Post by gtkourounis on 2007-11-06
hi guys, i was just wondering how i should format my new ext HDD so that i can use it fully between my windows xp (family desktop) and my laptop (ubuntu). If you have any sudgestions on what type of format i should use with my external hard drive please let me know.

thanx in advance :)

---

### Post by taurus on 2007-11-06
You have three options:

1.  format it as ntfs filesystem.  Gutsy now comes with ntfs-3g so you can write to it.

2.  format it as vfat/fat32 filesystem.  The only problem is that you cannot write files larger than 4GB to it.

3.  format it as ext3 and then install fs-driver on your windows machines to read that harddrive, [http://www.fs-driver.org/](http://www.fs-driver.org/).

---

### Post by gtkourounis on 2007-11-06
thanx a lot mate :) very helpful

---

