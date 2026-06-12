---
title: "Cant Get DVD Rom To Work"
date: 2006-04-30
forum: Hardware &amp; Laptops
---

### Post by Ronnie618 on 2006-04-30
Hi guys im pretty new to linux so ill need some detailed help here, what happened was i had a friend mounted my ntfs hard drives for me on ubuntu but ever since he did that my DVD rom doesnt work it says "Unable To Mount Selected Volume" like i can see it fine when i got to Computer just cant access it, how do i got about fixing this problem?

Thanks

---

### Post by olsonar on 2006-04-30
Would you please post your /etc/fstab file?

---

### Post by Ronnie618 on 2006-04-30
Heres the file for you.


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                     /proc                     proc      defaults        0       0
/dev/hda8            /                            ext3      defaults,errors=remount-ro 0       1
/dev/hda7            /home                   ext3      defaults        0       2
/dev/hda1            /media/hda1         ntfs       defaults,umask=0022        0         0
/dev/hda5            /media/hda5         ntfs       defaults,umask=0022        0         0
/dev/hda6            none            swap    sw                               0       0
/dev/hdb              /media/cdrom0     udf,iso9660 user,noauto      0       0

---

### Post by olsonar on 2006-04-30
Can you mount it as root? run   sudo nautilus   from a terminal and see whether you can access it from there. also, any error messages it gives you when you try to mount it would be helpful.

---

### Post by ptmmatssc on 2006-05-12
I'm having the same problem but when I open up a console and try to run  /etc/fstab , it says permission denied

---

