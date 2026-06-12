---
title: "Slave drive not shown in Computer (Places)"
date: 2005-09-11
forum: Hardware &amp; Laptops
---

### Post by Benzima on 2005-09-11
Ok...I know this can't be that hard but I just can't figure this out. I've read many posts related to my problem but not my exact problem.

I have a slave hard drive that appears in Device Manager, but not in Computer. My slave drive is NTFS and was only used as a back up stogre drive for XP. I'd like to keep those files if I can, put I would like even more for it to at lease just show up under Computer and have access to it. Please help.

Thanxxx in advance.

---

### Post by codejunkie on 2005-09-11
[QUOTE=Benzima]Ok...I know this can't be that hard but I just can't figure this out. I've read many posts related to my problem but not my exact problem.

I have a slave hard drive that appears in Device Manager, but not in Computer. My slave drive is NTFS and was only used as a back up stogre drive for XP. I'd like to keep those files if I can, put I would like even more for it to at lease just show up under Computer and have access to it. Please help.

Thanxxx in advance.[/QUOTE]
if your drive is already mounted and you want to have it show up in computer:/// you have to add the "user" option to the /etc/fstab file like this
example:
```

/dev/hdb1       /media/windows  ntfs    nls=utf8,umask=0222 0       0

```
change that to
```

/dev/hdb1       /media/windows  ntfs    user,nls=utf8,umask=0222 0       0

```
then it will show up in computer hope this helps.

---

### Post by Benzima on 2005-09-12
I try to edit the fstab. First I have to change the permission so that I can edit the file, right? So I open terminal, type and get:

*****
benzima@ubuntu:~$ cd /etc
benzima@ubuntu:/etc$ chmod 664 fstab
chmod: changing permissions of `fstab': Operation not permitted
benzima@ubuntu:/etc$
*****

Arghhhh !!!

Very frustrating to do the simplest things in linux, but I am willing to read, experiment and learn.

---

### Post by codejunkie on 2005-09-12
[QUOTE=Benzima]I try to edit the fstab. First I have to change the permission so that I can edit the file, right? So I open terminal, type and get:

*****
benzima@ubuntu:~$ cd /etc
benzima@ubuntu:/etc$ chmod 664 fstab
chmod: changing permissions of `fstab': Operation not permitted
benzima@ubuntu:/etc$
*****

Arghhhh !!!

Very frustrating to do the simplest things in linux, but I am willing to read, experiment and learn.[/QUOTE]
no you do not need to change permissions on the /etc/fstab to edit it all you have to do is 
```
sudo gedit /etc/fstab
```
if your using gnome or 
```
sudo kate /etc/fstab
``` if your using kde to edit it but if you would open a terminal and run 
```
sudo fdisk -l
```and post the results here also post your /etc/fstab file i will help you set it up.

---

### Post by Benzima on 2005-09-12
I open up a terminal, typed "sudo gedit /etc/fstab" copied and pasted, saved and I got this:

*****
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdb1	/media/windows  ext3    defaults,errors=remount-ro 0       1
/dev/hdb1	/media/windows  ext3    user,defaults,errors=remount-ro 0       1
*****

It showed up in Computer, but when I clicked on it I get the mount error "Unable to mount the selected volume. mount: only root can mount /dev/hdb1 on /media/windows. I opened another session, type cd to get to root, repeat and got the same thing.

Thanxxx for your help.

---

### Post by codejunkie on 2005-09-13
[QUOTE=Benzima]I open up a terminal, typed "sudo gedit /etc/fstab" copied and pasted, saved and I got this:

*****
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdb1	/media/windows  ext3    defaults,errors=remount-ro 0       1
/dev/hdb1	/media/windows  ext3    user,defaults,errors=remount-ro 0       1
*****

It showed up in Computer, but when I clicked on it I get the mount error "Unable to mount the selected volume. mount: only root can mount /dev/hdb1 on /media/windows. I opened another session, type cd to get to root, repeat and got the same thing.

Thanxxx for your help.[/QUOTE]

from what i can make of the fstab file you posted if /dev/hdb1 is your ntfs harddrive
then this is what your /etc/fstab file should look like
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdb1       /media/windows  ntfs    user,nls=utf8,umask=0222 0       0

```
this should fix it.

---

### Post by Benzima on 2005-09-13
That Worked !!!

Thanxxx !!!

---

