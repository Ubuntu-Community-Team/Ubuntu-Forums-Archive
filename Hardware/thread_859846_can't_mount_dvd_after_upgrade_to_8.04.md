---
title: "can't mount dvd after upgrade to 8.04"
date: 2008-07-14
forum: Hardware
---

### Post by bc54 on 2008-07-14
hi. before i upgraded to hardy i was able to mount and watch dvds, but after the upgrade i am unable to even mount dvds. i have installed everything needed to use it, libdvdcss2 and all. i have ubuntu 8.04 and it is a liteonit (?) dvd rom drive. i have another hdd with xubuntu 7.10 on it, and it can mount and play dvds. my /etc/fstab for 8.04-
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=85b2099d-7787-48a4-9145-f4e5c8a00b08 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=10ce73b2-2c4b-4295-9988-11ece4172d80 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

and for 7.10
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdd1
UUID=2f77ebdb-0865-4c59-b598-9686953e4dc0 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdd5
UUID=35eeb2de-04f4-434b-abe3-0c6c63a7f37a none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hda        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

thanks for any help

---

### Post by richardjennings on 2008-07-15
I would try changing:

```
/dev/scd0 /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0
```
&
```
/dev/scd1 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
```

to

```
/dev/scd0 /media/cdrom1 udf,iso9660 user,noauto,exec 0 0
```
&
```
/dev/scd1 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
```

---

### Post by bc54 on 2008-07-15
thats what i was kinda thinking but didn't want to mess anything up and thought'd ask first. i''l give it a shot.

---

### Post by bc54 on 2008-07-15
ok changing the /etc/fstab didn't work, but now my optical show as ready to mount in my panel drive mounter. before they would only appear if i inserted a cd, so i guess the changes did something but didn't fix it. i hope im explaining this right. anything else i should try?
edit- btw the dvd drive is /dev/hda & /media/cdrom1

---

### Post by richardjennings on 2008-07-15
```
sudo mount -a
``` will mount the devices correctly listed in /etc/fstab

are scd0 & scd1 in the /dev/ directory?

```
ls /dev/
``` to look for yourself, or ```
ls /dev/ | grep "scd"
``` to have grep search through them for you.


if they are not in the dev directory, try changing the fstab device names from scd0 & scd1 to hdb & hda, then sudo mount -a

if they are in the dev directory, try removing the two cdrom lines from fstab, then sudo mount -a

---

### Post by bc54 on 2008-07-15
ok. ```
sudo mount -a
``` did nothing so i did the ```
ls /dev/ | grep "scd"
``` and it returned 
```
scd0
scd1

```
so i then changed my fstab to
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=85b2099d-7787-48a4-9145-f4e5c8a00b08 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=10ce73b2-2c4b-4295-9988-11ece4172d80 none            swap    sw              0       0
/dev/hdb           udf,iso9660 user,noauto,exec 0       0
/dev/hda           udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```
then sudo mount -a gave me
```
mount: mount point udf,iso9660 does not exist
mount: mount point udf,iso9660 does not exist
```
also before i changed my fstab, when i inserted a cd into the cd drive my panel mounter made a new cd icon, called CD-ROM DRIVE. the ones before were CD-ROM1 and CD-ROM2. after the fstab change the CD-ROM1 and CD-ROM2 disappeared.
and 1 more thing, my fstab seperates the different sections by spaces, are they supposed to be tabs?

---

### Post by richardjennings on 2008-07-16
what happened when you removed the two cdrom lines from fstab?

---

### Post by bc54 on 2008-07-16
after i removed the cdrom lines it gave me
```
mount: mount point udf,iso9660 does not exist
mount: mount point udf,iso9660 does not exist
```

---

### Post by richardjennings on 2008-07-17
after removing the cdrom lines, your fstab should look like this:

```
 # /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda1
UUID=85b2099d-7787-48a4-9145-f4e5c8a00b08 / ext3 relatime,errors=remount-ro 0 1
# /dev/sda5
UUID=10ce73b2-2c4b-4295-9988-11ece4172d80 none swap sw 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
```

---

### Post by bc54 on 2008-07-18
ok now i removed the cdrom lines and i now i can mount non-encrypted dvds, thanks! encrypted dvds still don't mount but i think i will try to remove then reinstall libdvdcss and all. thanks for the help alot!
Edit- ok not all my non-encrypted dvds (i think their non-encrypted, b/c their homemade, not by me) mount. some are sony dvd+r other are memorex (only info is from inner ring b/c labels)
the 6 sony - 2 mounted, and both seemed to play correctly but little fuzzy (maybe some deinterlace to fix that up) 
the 2 memorex - 1 mounts and the other doesn't; the one that mounts won't play.
i'll retry libdvdcss tommorow & i'll update.
thanks and goodnight (well, for me)

Edit 2- ok about a day later i ran into hard drive problems and bought a new pc, but since dvds mopunted i'lkl call this one solved.

---

