---
title: "mounting media on cdrom and dvdrom"
date: 2004-12-12
forum: Hardware &amp; Laptops
---

### Post by müller on 2004-12-12
hi.
on my last computer (with warty) i only had a cdrom and when i put in a cd
it was automaticly mounted and put on the desktop
now i have (also warty) a cdrom and a dvdrom  and when i put 
a cd in nothing hapens
when i click cdrom1 icon in nautilus it replies:

Unable to mount the selected volume. The volume is probably in a format that cannot be mounted.
mount: wrong fs type, bad option, bad superblock on /dev/hdd,
       or too many mounted file systems

and the same anwser when i try it on hdc

in the terminal i get the same anwser

my fstab is:
proc            /proc           proc    defaults        0       0
/dev/sda1       /               reiserfs defaults        0       1
/dev/sda3       /home           reiserfs defaults        0       2
/dev/sda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdc        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

the hdd is the dvdrom and hdc the cdrom
and a fresh install was made with both devices present

anybody had this problem yet?

---

### Post by müller on 2004-12-18
when i instaled k3b (cd burning program) it recognised my
writer in did meke an image.
and when i put in a cd it was mounted and seen on the desktop

.....well now when i rebooted it doesent mount anymore  :sad: 
but i can see the content of a cd in the k3b brovser

---

### Post by müller on 2004-12-26
Like usualy at Linux you find out the problem and solution by yourself
and after a month i dit too.
Zhe problem was that i removed the rythembox packet and the ubuntu-desktom 
along with it.
Now i installed it back and it works.  :D

---

### Post by müller on 2004-12-26
Like usualy at Linux you find out the problem and solution by yourself
and after a month i dit too.
The problem was that i removed the rythembox package and the ubuntu-desktom 
along with it.
Now i installed it back and it works.  :D

---

