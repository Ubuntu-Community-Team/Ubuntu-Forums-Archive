---
title: "Just installed Ubuntu 8.04 and it does not recognise my CD drive."
date: 2008-09-08
forum: General Help
---

### Post by Aztlifon on 2008-09-08
I just installed Ubuntu 8.04 on a computer of friends of mine.
I got everything working but now it wont mount the dvd drive.
There are alot of posts out there about this error but I couldnt find any concrete answer in those posts.

This is what I get out of my Fstab.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=5a2d4cee-7528-4178-a4b8-af8bfbf9da3d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=ba7c7b14-e330-4826-bc14-79f8a9171ca8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

I hope someone can help me. Cause its not my own pc.
Greetings,
Aztlifon

---

### Post by Sycron on 2008-09-08
Put a CD in the drive then mount it manually.```
sudo mount /dev/scd0 /mnt && cd /mnt && ls
```

and post the output.

---

### Post by Aztlifon on 2008-09-08
It opens a window with the following text: sudo mount password for venema:
when I typed in the password it just closed the window. ( It also did not show any *s or letters when I typed it in).

I must state that I am a real Ubuntu noob.

---

### Post by Sycron on 2008-09-09
> **Aztlifon said:**
> It opens a window with the following text: sudo mount password for venema:
when I typed in the password it just closed the window. ( It also did not show any *s or letters when I typed it in).

I must state that I am a real Ubuntu noob.

Try```

sudo mount /dev/scd0 /mnt && cd /mnt && nautilus /mnt
```

---

