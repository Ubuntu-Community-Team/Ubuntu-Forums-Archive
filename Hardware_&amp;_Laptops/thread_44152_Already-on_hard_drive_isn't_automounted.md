---
title: "Already-on hard drive isn't automounted"
date: 2005-06-24
forum: Hardware &amp; Laptops
---

### Post by NeoChaosX on 2005-06-24
Okay, tried this once before, but I'll ask again.

I used to have no problem with my external hard drive and Ubuntu. For about the six months I've been using Ubuntu, it's always been automounted when the OS starts. Whether it's turned on before turning on the computer or rebooting from a Windows session.

Now, the drive will only automount at certain times. When I:

- Turn on the HD before the PC or before booting into Ubuntu
- Have the drive on during a Windows session, then reboot into Linux

the drive does not mount automatically. Is this normal, or is there a way for me to get it automount all the time again?

---

### Post by NeoChaosX on 2005-06-28
So nobody knows what's going on here?

---

### Post by NeoChaosX on 2005-07-16
*bump* Anybody? This is starting to get annoying.

---

### Post by fig_jam_uk on 2005-07-16
can you post a copy of your fstab file?

open console and type

sudo gedit /etc/fstab

the contents of this file

cheers

---

### Post by NeoChaosX on 2005-07-17
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc5       /               reiserfs notail         0       1
/dev/hdc7       /home           reiserfs defaults       0       2
/dev/hdc6       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 ro,user,noauto 0       0
/dev/hdc1       /mnt/windows    ntfs    umask=0222	0	0
/dev/sda1	/mnt/cupil	vfat	umask=0000,user	0	0
```

/dev/sda1 is the external drive. I've tried all sorts of options (utf=,auto,noauto,sync) but none of those seem to get it working like it did before.

---

### Post by fig_jam_uk on 2005-07-17
[QUOTE=NeoChaosX]```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc5       /               reiserfs notail         0       1
/dev/hdc7       /home           reiserfs defaults       0       2
/dev/hdc6       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 ro,user,noauto 0       0
/dev/hdc1       /mnt/windows    ntfs    umask=0222	0	0
/dev/sda1	/mnt/cupil	vfat	umask=0000,user	0	0
```

/dev/sda1 is the external drive. I've tried all sorts of options (utf=,auto,noauto,sync) but none of those seem to get it working like it did before.[/QUOTE]

Hi dont know if this will work but i suppose its worth a try my SATA drives now auto mount upon boot

goto console

chdir /etc/rcS.d   <enter>

sudo ln -s ../init.d/mountall.sh    <enter>

enter password  <enter> then reboot, should hopefully work...

let me know...

---

### Post by NeoChaosX on 2005-07-19
It didn't work.

Coincedentally, during boot-up, I noticed this error message:

> *mount: special device /dev/sda1 does not exist*
I'm sure that this is an indication of a problem, but what it is, I don't know.  :-|

---

### Post by NeoChaosX on 2005-07-19
Okay, think I've figured it out. I changed /etc/fstab so that the line for my external drive is above the line for the CD-ROM, and now the the drive is always auto-mounting at boot. I guess it's the position of the line in the fstab file determines whether it's automounted at start-up.

---

