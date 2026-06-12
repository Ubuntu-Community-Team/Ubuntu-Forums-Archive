---
title: "I'm not able to mount my floppy drive in kubuntu 6.06........."
date: 2006-08-16
forum: Hardware &amp; Laptops
---

### Post by flamel2000 on 2006-08-16
Hello there.
I'm absolute newbie to linux.But know sum konsole workings.
I'm not able to mount my floppy drive.The distro i use is kubuntu 6.06 patched by jamuir for vt8251 support in ahci mode.I tried mounting using pmount.Nothing works.i tried editing the fstab.It also dint work.

My fstab looks like this :


i# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda7       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /media/C        ntfs    auto,user,defaults,nls=utf8,umask=007,gi
d=46 0       1
/dev/sda5       /media/D        ntfs    auto,user,defaults,nls=utf8,umask=007,gi
d=46 0       1
/dev/sda6       /media/E        ntfs    auto,user,defaults,nls=utf8,umask=007,gi
d=46 0       1
/dev/sda3       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  vfat    rw,user,noauto  0       0
~



The error shown in konsole is :

einstein@Einstein:~$ pmount /dev/fd0

mount: mount point /media/floppy0 does not exist

Help me wat to do.

Please...........:( :(

---

### Post by meng on 2006-08-16
Have you tried
sudo mkdir /media/floppy0

followed by mounting?

---

### Post by marianlibrarian on 2007-03-21
[I]add the directory
sudo mkdir /media/floppy0

[/I]Open your fstab
sudo gedit /etc/fstab

Add this line:
/dev/fd0/media/floppy0 auto rw,user,noauto 0 0

Save it and return to terminal window.

Type this line:
mount /dev/fd0

Oh and it helps to have a floppy in the drive. ;)

Note: Shouldn't this be something that is done at the time of installation of OS??

---

