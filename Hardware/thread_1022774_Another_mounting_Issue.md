---
title: "Another mounting Issue"
date: 2008-12-27
forum: Hardware
---

### Post by AryanAngel on 2008-12-27
I've read through multiple threads regarding how to mount HDDs on boot but I still can't seem to get mine to work. I have drives sda1, sdb1, sdc1 and I am on sda2. Here is what my fstab looks like in attempt to mount the drives on bootup but no success, the directories do exist:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=dfc560cf-5bd1-40a2-91a3-c6b2ea96be0b /               ext3    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

/dev/sda1 /media/Internal nfs defaults 0 0
/dev/sdb1 /media/Windows nfs defaults 0 0
/dev/sdc1 /media/External nfs defaults 0 0
```

I am however able to mount them fine through the terminal.
```
sudo mount /dev/sda1 /media/Internal
sudo mount /dev/sdb1 /media/Windows
sudo mount /dev/sdc1 /media/External
```

---

### Post by AryanAngel on 2008-12-27
I assume this is an easy problem to fix. Anyone?

---

### Post by taurus on 2008-12-27
Are those ntfs filesystem?  If that's the case, then you forgot a letter **[COLOR="Blue"]t[/COLOR]** in there.

```

/dev/sda1 /media/Internal n**[COLOR="Blue"]t[/COLOR]**fs defaults 0 0
/dev/sdb1 /media/Windows n**[COLOR="Blue"]t[/COLOR]**fs defaults 0 0
/dev/sdc1 /media/External n**[COLOR="Blue"]t[/COLOR]**fs defaults 0 0

```

---

### Post by AryanAngel on 2008-12-28
Thanks for the reply taurus. Yes the are ntfs although I have seen it written both ways and have also tried ntfs instead of nfs with no success. Would not having privileges on boot have any effect?

Edit: I tried once more and it seems to have worked, I'm dumbfounded thanks for stimulating me to try again. :)

---

### Post by pastalavista on 2008-12-28
Try installing ntfs-config```
sudo apt-get install ntfs-config
```. The launcher shows up in Applications>System Tools or run it with```
gksu ntfs-config
```. It's a very simple program but it fixed my Windows drive mount problems. Hope it fixes yours too.

---

### Post by AryanAngel on 2008-12-28
Thanks pastalavista I have done that now.

---

