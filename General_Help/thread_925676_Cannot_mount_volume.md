---
title: "Cannot mount volume"
date: 2008-09-20
forum: General Help
---

### Post by rjwilsonster on 2008-09-20
Trying to mount my 'os' partition today, I got this message: 
Invalid mount option when attempting to mount the volume 'OS'
Anyone know what I should do to fix it? Or for that matter, what I did to cause it? Also, I've only been a Hardy user since Wednesday.
Thanks

---

### Post by spibou on 2008-09-20
Do **cat /etc/fstab** and post the output.

---

### Post by mb_webguy on 2008-09-20
Keep in mind that Linux is case sensitive.  "OS" and "os" are not the same.

---

### Post by rjwilsonster on 2008-09-20
> **spibou said:**
> Do **cat /etc/fstab** and post the output.

This is what I got.

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=a6a78d1f-ebb0-45fb-b229-90990e6913c2 /               ext3    errors=remount-ro 0       1
# /dev/sda5
UUID=8ee82ef9-2fad-415f-a6e5-6227ccfbfe32 none            swap    sw              0       0
/dev/sda2       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by spibou on 2008-09-21
> **rjwilsonster said:**
> Trying to mount my 'os' partition today, I got this message: 
Invalid mount option when attempting to mount the volume 'OS'

Tell us which steps you went through trying to mount the partition.

---

### Post by BattousaiX on 2008-09-21
Just going to take a wild guess here and say do the following.

```

sudo fdisk -l

```

Then you will want to create the directory to mount to.

```

sudo mkdir /mnt/windows 

```

(or another directory name)

Possibly invalid due to the type, maybe NTFS?  If that's the case I did the following.

```

sudo mount -t ntfs /dev/sdb1 /mnt/windows

```

---

### Post by jepperstone on 2009-03-15
I have a similar issue. I'm using 8.10 and when I go to Places > OS I get the following error: 
> Invalid mount option when attempting to mount the volume 'OS'.

---

