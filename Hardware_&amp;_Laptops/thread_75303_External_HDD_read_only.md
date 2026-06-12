---
title: "External HDD read only"
date: 2005-10-13
forum: Hardware &amp; Laptops
---

### Post by fut21 on 2005-10-13
I have a external HDD with fat32 filesystem. In hoary, mandriva 2006, SuSE 9.3-10.0 i could read and wright, but in ubuntu breezy badger it`s read only. I cant change it even from root. Anybody have any idea what to do ?

---

### Post by fut21 on 2005-10-14
Are there enyone with a solution.

---

### Post by robenroute on 2005-10-14
Did you put a line in your fstab file for this ext. HDD? If so, what does it look like? If not, you might want to have a line that reads something like:

/dev/sda1    /media/external   vfat   iocharset=utf8,umask=000    0     0

Don't forget to create a directorycalled external under /media! After updating your fstab file you want to 'sudo mount -a', in order to mount this HDD.

God luck.

---

### Post by fut21 on 2005-10-14
It`s still don`t work. Do you have other suggestions ?

---

### Post by fut21 on 2005-10-14
I found the solution. It anybody with the same problem as me, try this:
[http://ubuntuforums.org/showpost.php?p=355988&postcount=8](http://ubuntuforums.org/showpost.php?p=355988&postcount=8)

---

