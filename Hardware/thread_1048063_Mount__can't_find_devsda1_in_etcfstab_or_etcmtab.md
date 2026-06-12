---
title: "Mount : can't find /dev/sda1 in etc/fstab or etc/mtab"
date: 2009-01-23
forum: Hardware
---

### Post by hillahilla on 2009-01-23
Hi everyone,

My HDD has two ext3 partitions, /dev/sda1 and /dev/sda6. I've recently re-installed Intrepid, KDE 4.1 on sda6, /sda1 is where I kept all my personal files and wasn't formatted at the time.

After the install, I could still mount /sda1 using

```
sudo mount /dev/sda1 /mnt

```
now today i started the computer and tried to mount /sda1 and i got the infamous error message  :

```
mount : can't find /dev/sda1 in /etc/fstab or /etc/mtab
```

here's my fstab : 
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=61360bbc-d527-47dc-b5a5-f6bf6aa43af7 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=8cf06ae6-4e8b-485a-9cea-b16c51f680c0 none            swap    sw              0       0
# /dev/sda7
UUID=672b1cc8-516c-41ff-bbe8-9b8df82d4d7a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

here's sudo fdisk -l : 

```
Disque /dev/sda: 100.0 Go, 100030242816 octets
255 heads, 63 sectors/track, 12161 cylinders
Units = cylindres of 16065 * 512 = 8225280 bytes
Identifiant disque: 0x90caeefc

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sda1   *           1        5863    47094516   83  Linux
/dev/sda2            5864       12161    50588685    5  Extended
/dev/sda5           11785       12161     3028221   82  Linux swap / Solaris
/dev/sda6            5864       11536    45568309+  83  Linux
/dev/sda7           11537       11784     1992028+  82  Linux swap / Solaris

Les entrées de la table de partitions ne sont pas dans l'ordre du disque

```

What can I do to fix this?

Thank you for your time!

---

