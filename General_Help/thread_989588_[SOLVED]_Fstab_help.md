---
title: "[SOLVED] Fstab help"
date: 2008-11-21
forum: General Help
---

### Post by linuxology on 2008-11-21
Why didn't my sda3 partition mount?  My sdb2 drive mounted fine, but not the 2ndary_108GB partiton.  Here is a copy of the fstab.  Any help would be appreciated.

/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb2 /media/2ndary_250GB ext3 auto,rw,user 0 2
/dev/sda3 /media/2ndary_108GB ext3 auto,rw,user 0 2

---

### Post by bodhi.zazen on 2008-11-21
What happens when you enter :

```
sudo mount -a
``` in a termainal ?

---

### Post by drs305 on 2008-11-21
Have you confirmed that "/media/2ndary_108GB" spelled exactly like that exists?

Please post the results of:
```
sudo fdisk -l
mount | grep /dev/

```

---

### Post by ibuclaw on 2008-11-21
1) Sorry in the event of a possibly dumb question. but are you sure that the filesystem name/type is correct?

```
sudo fdisk -l
```
Just check that the output is correct with the details you are putting in.

2) Does the folder exist in /media ?
```
sudo mkdir /media/2ndary_108GB
```

3) and the command
```
df
```
Will tell you all mount filesystems.

Regards
Iain

---

### Post by linuxology on 2008-11-21
I had to mkdir in /media;  somehow it got deleted

---

