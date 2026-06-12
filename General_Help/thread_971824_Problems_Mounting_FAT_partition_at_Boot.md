---
title: "Problems Mounting FAT partition at Boot"
date: 2008-11-05
forum: General Help
---

### Post by BigJohnA on 2008-11-05
I have searched for this answer on my own, with no success.

I recently switched from Windows to Ubuntu, and am not too familiar with the linux system. I am trying to mount my windows partitions (two of them on separate drives, /dev/sda1 and /dev/sdb) at boot. 

I have edited /etc/fstab with the following entries:
```

/dev/sda1   /media/68.2G  vfat  isocharset=utf8,umask=000   0       0
/dev/sdb    /media/13G  vfat  isocharset=utf8,umask=000   0       0

```

Obviously, the /media/ paths point to existing locations.

I have tried various iterations of these entries, using UUID, labels, you name it. None of my attempts have resulted in either partitions/drives being mounted at boot. I am not sure what I am doing wrong, it appears this is the appropriate way to proceed. Any help would be appreciated.

---

