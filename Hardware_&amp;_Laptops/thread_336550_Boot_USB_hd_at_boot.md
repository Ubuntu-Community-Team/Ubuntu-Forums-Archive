---
title: "Boot USB hd at boot"
date: 2007-01-11
forum: Hardware &amp; Laptops
---

### Post by jmposey87 on 2007-01-11
I have an external USB hard drive and can mount it using the disks utility in gnome, but I want it to automatically mount when linux boots. 
Here is my fstab
>  /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb4       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0   $
/dev/hdb1       /media/hdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0   $
/dev/hdb3       /media/hdb3     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sda1       /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hdb2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


Sda1 is the drive that I need to mount at boot.  Can someone write me a line for fstab or let me know how to do it?

---

### Post by capitalistpiglet on 2007-01-11
sda1 is already in fstab so it should mount at boot. 
try ```
sudo mount -a
``` while the drive is connected and see if it gives you an error.

---

### Post by jmposey87 on 2007-01-11
I don't know if it matters but I had already enable the drive from the disk utility before viewing fstab.  I can mount the drive, but I have to do it manually everytime through command or disk utility. When i ran "sudo mount -a" i didn't get any feedback from terminal.

---

