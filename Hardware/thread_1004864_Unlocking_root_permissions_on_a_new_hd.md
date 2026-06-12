---
title: "Unlocking root permissions on a new hd?"
date: 2008-12-07
forum: Hardware
---

### Post by AmunRa on 2008-12-07
The saga continues.  I've got the 500 gb hd formatted, and i can mount it. . . but the permissions are set to root.  Pointers on how to unlock it?

I'm beginning to think that my success with the 500 gb SATA drive was a fluke :\

---

### Post by MarblePanther on 2008-12-07
sudo chmod -R a=rwx /media/"drivepathhere"

---

### Post by AmunRa on 2008-12-07
. . . didn't work

---

### Post by taurus on 2008-12-07
Didn't we just go through this not that long ago?  Can you post the outputs of these commands again?

```
sudo fdisk -l
cat /etc/fstab
df -h
id
```

---

### Post by MarblePanther on 2008-12-07
what are the contents of your /media  ?

---

### Post by AmunRa on 2008-12-07
I think i've solved it.  I just logged in as root and changed the permissions that way.  I left the owner as root (as it's supposed to be i believe) but gave permissions to my admin user and others.  The next step will be to affix the two drives to the mount points i made with mkdir. It's just generating the generic drive-1, drive-2, etc.  Not a necessity, but a cosmetic convenience.

Here's the out puts 

output for sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0008c191

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60045   482311431   83  Linux

Disk /dev/sdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9352    75119908+  83  Linux
/dev/sdb2            9353        9726     3004155    5  Extended
/dev/sdb5            9353        9726     3004123+  82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00086143

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001   83  Linux

output for cat /etc/fstab

cat /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=0f2edef1-302d-461f-8f73-8f365a45c640 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=b5db1447-e272-4b9d-8b90-0cdfaaedad80 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

output for df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1              71G   40G   28G  59% /
varrun                501M   92K  501M   1% /var/run
varlock               501M     0  501M   0% /var/lock
udev                  501M  104K  501M   1% /dev
devshm                501M     0  501M   0% /dev/shm
lrm                   501M   34M  468M   7% /lib/modules/2.6.22-16-generic/volatile

---

