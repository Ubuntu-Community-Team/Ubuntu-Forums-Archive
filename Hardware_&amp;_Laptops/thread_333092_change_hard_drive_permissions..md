---
title: "change hard drive permissions."
date: 2007-01-06
forum: Hardware &amp; Laptops
---

### Post by brad1150 on 2007-01-06
I mounted a NTFS hard drive while in my user account,I can read files in the hd, but I cant delete them. When I rigth click on the folders it says the owner is root. When I log in as root, it doesnt show the hard drive in the gui, but in terminal it shows the hd and everything in it with ls. How can I change permissions to my normal user account to read adn write. here is my estab:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
# SELF MADE FOR NTF to NiX
/dev/hdb1 /media/hdb1 ntfs users,noauto,uid=1000,gid=0   1000    0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


I followed this guide to mount it: [HTML]http://czarism.com/easy-peasy-mount-ntfs-w-ubuntu-linux[/HTML]

---

### Post by aysiu on 2007-01-06
Try this:
[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

---

### Post by brad1150 on 2007-01-06
How do I find out if I have dapper or edgy? i'm still new to Ubuntu.

---

### Post by taurus on 2007-01-06
One way is to look in /etc/apt/sources.list to see if it has dapper or edgy in there!

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by aysiu on 2007-01-06
Or ```
cat /etc/issue
``` will tell you if it's 6.06 (Dapper) or 6.10 (Edgy).

---

