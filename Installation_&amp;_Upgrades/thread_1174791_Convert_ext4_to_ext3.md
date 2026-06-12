---
title: "Convert ext4 to ext3"
date: 2009-05-31
forum: Installation &amp; Upgrades
---

### Post by javyn999 on 2009-05-31
I seem to be having a problem with my computer freezing and crashing when I empty large files from the Trash.  Perusing the forums, this seems to be an ext4 issue.  Is there a command that would allow me to convert from ext4 to ext3 file system in Jaunty? 

Thanks!

---

### Post by huwnet on 2009-05-31
Unless you specifically chose not to use extents with ext4, it is not backwards compatible. The only way to go to ext3 is to backup, reformat the partition and then replace the files.

---

