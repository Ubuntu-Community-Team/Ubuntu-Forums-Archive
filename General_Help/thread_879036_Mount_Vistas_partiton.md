---
title: "Mount Vistas partiton"
date: 2008-08-03
forum: General Help
---

### Post by silasj20 on 2008-08-03
Ill make this short.  I used ubuntu's partitioning tool and accidentally unmounted my vista partition.  Obviously it doesn't show up in grub.  How do i fix that?  Its probably pretty easy but i'm just starting out.  Thanks in advance.

---

### Post by thegodfaza on 2008-08-03
```
sudo mount -t ntfs /dev/something /home/vista
```

Or you can write it back into fstab
```
/dev/sda /home/vista ntfs defaults 0 0
```

And why doesn't it show up in grub?

---

### Post by silasj20 on 2008-08-05
Thanks for your help but that didn't resolve the issue.  When i tried the first suggestion i got a busy error.  When I tired the second option i was unable to modify fstab.  I originally thought I understood the issue but I have no clue now.  Now when i try to mount the partition in Ubuntu it says it cannot mount because the mount point contains newline, G_DIR_SEPARATOR(usually /).

---

### Post by silasj20 on 2008-08-06
bump

---

