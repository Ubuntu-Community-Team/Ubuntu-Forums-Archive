---
title: "Hardware problems"
date: 2006-02-05
forum: Hardware &amp; Laptops
---

### Post by Kiwinote on 2006-02-05
Hello, 

I have a Samsung SD-606F DVD-player that Ubuntu recognizes, but when I want to play/browse it I get this message:
Warning: device /dev/hdd is already handled by /etc/fstab, supplied label is ignored
mount: No medium found
Error: could not execute pmount


Do you have any advice on what to do?

Thanks,
Kiwinote

---

### Post by ::DoGG:: on 2006-02-05
Can you post yout /etc/fstab file ?? Looks like you have some king of automount package installed or something that already mounted your device in a place putted in /etc/fstab, but your fstab looks like messed u in those lines :D put your /etc/fstab here and i will be glad to help you out.

---

### Post by Kiwinote on 2006-02-05
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>          <options>                          <dump>  <pass>
proc                      /proc                   proc               defaults                               0               0
/dev/hda2             /                          ext3               defaults,errors=remount-ro 0              1
/dev/hda5             none                   swap              sw                                        0               0
/dev/hdc               /media/cdrom0   udf,iso9660   ro,user,noauto                     0               0
/dev/hdd               /media/cdrom1   udf,iso9660   ro,user,noauto                     0               0
/dev/fd0                /media/floppy0    auto              rw,user,noauto                     0               0
/dev/hda1             /media/windows   vfat               iocharset=utf8,umask=000 0              0

There you go,
Kiwinote

//EDIT Tried to changed layout, same file

---

### Post by ::DoGG:: on 2006-02-05
edit Your fstab fiule to look like this:

proc /proc proc defaults 0 0
/dev/hda2 / ext3 defaults,errors=remount-ro 0 1
/dev/hda5 none swap sw 0 0
/dev/hdc    /media/cdrom0   auto   ro,noauto,user,exec   0 0
/dev/hdd    /media/cdrom1   auto   ro,noauto,user,exec   0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
/dev/hda1 /media/windows vfat iocharset=utf8,umask=000 0 0

can You see the contents of the cd you put in the drive ??
can you mount it by
mount /dev/hdc or mount /dev/hdd ??
if so, check the /media/cdrom0 and /media/cdrom1 direcotry can You find it there

---

### Post by mips on 2006-02-05
You should really split your problems across different threads, just makes things easier.

---

### Post by Kiwinote on 2006-02-06
[QUOTE=mips]You should really split your problems across different threads, just makes things easier.[/QUOTE]
Done.

Kiwinote

---

### Post by Kiwinote on 2006-02-06
[QUOTE=::DoGG::]edit Your fstab fiule to look like this:

proc /proc proc defaults 0 0
/dev/hda2 / ext3 defaults,errors=remount-ro 0 1
/dev/hda5 none swap sw 0 0
/dev/hdc    /media/cdrom0   auto   ro,noauto,user,exec   0 0
/dev/hdd    /media/cdrom1   auto   ro,noauto,user,exec   0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
/dev/hda1 /media/windows vfat iocharset=utf8,umask=000 0 0

can You see the contents of the cd you put in the drive ??
can you mount it by
mount /dev/hdc or mount /dev/hdd ??
if so, check the /media/cdrom0 and /media/cdrom1 direcotry can You find it there[/QUOTE]
Thanks, I'll try this when get get back to my own computer.
Thanks
Kiwinote

---

### Post by Kiwinote on 2006-02-07
> can You see the contents of the cd you put in the drive ??
No, it does makes noises as if it's is trying to read it, though and I get the same error as in the beginning.
> can you mount it by mount /dev/hdc or mount /dev/hdd ??
No, I get this error
mount: I could not determine the filesystem type, and none was specified
> if so, check the /media/cdrom0 and /media/cdrom1 direcotry can You find it there
No, also not

Kiwinote

---

### Post by Kiwinote on 2006-02-09
Any Ideas?

---

### Post by Kiwinote on 2006-02-21
When I right-click on the drive and select mount volume,nothing happens until I eject the disc and I get this error(different from error mentioned above):
Warning: device /dev/hdd is already handled by /etc/fstab, supplied label is ignored
mount: I could not determine the filesystem type, and none was specified
Error: could not execute pmount

Kiwinote

---

