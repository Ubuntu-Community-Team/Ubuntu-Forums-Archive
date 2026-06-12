---
title: "Viewing another Hard Drive"
date: 2005-05-16
forum: Hardware &amp; Laptops
---

### Post by BearnaN on 2005-05-16
ok i got 2 hard drives in my computer and i can only read the one that has Linux installed on it, how can i be able to read the other hard drive, if its even possible.  :-?  :-?  thankz.

---

### Post by nemin on 2005-05-16
[QUOTE=BearnaN]ok i got 2 hard drives in my computer and i can only read the one that has Linux installed on it, how can i be able to read the other hard drive, if its even possible. [/QUOTE]I assume your second harddrive is partitioned already? You'll just need to "mount" the partition(s) on your second HD then, see [http://ubuntuguide.org/4.10/index.html#windows](http://ubuntuguide.org/4.10/index.html#windows) for more information how to do so, when the filesystem is FAT or NTFS, wich is most likely..
If it's not partitioned yet, use `parted` to do so.

---

### Post by BearnaN on 2005-05-16
ok ive done that 

[[IMG]http://img229.echo.cx/img229/9514/screenshot9kw.th.jpg[/IMG]](http://img229.echo.cx/my.php?image=screenshot9kw.jpg)

but where should the hard drive be showing up at?, sorry but im heaps new to linux so yeah :P

---

### Post by nemin on 2005-05-16
[QUOTE=BearnaN]ok ive done that 
[[IMG]http://img229.echo.cx/img229/9514/screenshot9kw.th.jpg[/IMG]](http://img229.echo.cx/my.php?image=screenshot9kw.jpg)
[/QUOTE]
You didn't do it completely right, but you're on the right track:)
You tried to mount '/dev/hda1', you understand? Now, you don't want to mount '/dev/hda1', since that's the partition linux is installed on. You want to mount your second HD, wich is named '/dev/hdb'. When you want to mount the first partition on that, try ```
mount /dev/hdb1 /media/windows
```Though, I think it'd be usefull to first post some more information, like your partition list and the filesystem of the partition you want to mount.

---

### Post by BearnaN on 2005-05-16
THANKZ!! heaps for ur help, one more question though, the 2nd hard drive has a partition so theres like C: and D: how to i mount the D: of the drive? 

sudo mount /dev/hdb2 /media/windows?????

and i want to be able to read and write to the drive, if its possible :D

---

### Post by nemin on 2005-05-16
[QUOTE=BearnaN]THANKZ!! heaps for ur help, one more question though, the 2nd hard drive has a partition so theres like C: and D: how to i mount the D: of the drive? 

sudo mount /dev/hdb2 /media/windows?????[/QUOTE]Almost right, the '/dev/hdb2' is correct at least :) Thouh, you should mount it to another directory, because /media/windows/ is already in use for '/dev/hdb1'.
[QUOTE=BearnaN]
and i want to be able to read and write to the drive, if its possible :D[/QUOTE]That depends on the filesystem of the partition. Writing won't be possible for NTFS partitions. Anyway, try to add 'umask=000' to the mount command, as descriped on the link I sent you in my first post.

---

### Post by BearnaN on 2005-05-16
k  i did that but im getting this error 

" wrong fs type, bad option, bad superblock on /dev/hdb2,
       or too many mounted file systems
       (aren't you trying to mount an extended partition,
       instead of some logical partition inside?)"


:S

---

### Post by nad on 2005-05-16
Try /dev/hdb5 .

Some more info, per post #4, would ceratinly help us help you.

From the command line: parted /dev/hdb print

---

### Post by BearnaN on 2005-05-17
thankz for your help everything is workin awesomely now :D

---

