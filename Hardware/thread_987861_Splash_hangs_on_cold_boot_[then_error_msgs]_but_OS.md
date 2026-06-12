---
title: "Splash hangs on cold boot [then error msgs] but OS loads upon restart."
date: 2008-11-20
forum: Hardware
---

### Post by Lars&#1758; on 2008-11-20
On the initial cold boot, after the unsuccessful splash loading, I get errors such as:

/dev/desk/by-uuid " " does not exist. 

" " ata1.01: status: {DRDY}
" " ata1.01: exception Emask " " action frozen.

AND the eventual

Buffer I/O error on device sdb, logical block " "

It seems weird because this only happens on the initial boot after a shutdown - Ubuntu 8.10 loads fine after a restart..but I bet I've done something wrong..hopefully fixable. I'm guessing this is a hardware issue :confused: I have two old ATA harddrives on a 99DellDimensionXPS-T500. *I'm trying to get this old thing tricked-out to be an open source Ubuntu GIS workstation - PLEASE HELP!* I've been fighting this issue for ~9 months now :mad:

here are fstab & /boot/grub/menu.lst

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=3cdbb3f5-a2b9-4210-b88d-31ed30edbd0b /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb1
UUID=848c016b-263e-491f-90da-cd612ab940bd /srv            xfs     relatime        0       2
# /dev/sda2
UUID=7701a999-b2f1-43d9-aaff-05ea7f4f88f9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```


```
title        Ubuntu 8.10, kernel 2.6.27-7-generic
uuid        3cdbb3f5-a2b9-4210-b88d-31ed30edbd0b
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=3cdbb3f5-a2b9-4210-b88d-31ed30edbd0b ro quiet splash
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid        3cdbb3f5-a2b9-4210-b88d-31ed30edbd0b
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=3cdbb3f5-a2b9-4210-b88d-31ed30edbd0b ro  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 8.10, memtest86+
uuid        3cdbb3f5-a2b9-4210-b88d-31ed30edbd0b
kernel        /boot/memtest86+.bin
quiet
```

---

### Post by Lars&#1758; on 2008-12-04
2 week bump...any help would be very much appreciated!

---

### Post by Lars&#1758; on 2008-12-07
A sincere and pleading bump..I desperately need some guidance - "when the student is ready the teacher appears" {?}please

---

### Post by bdoe on 2008-12-07
Honestly, this sounds like impending hard drive failure. If you have a newer drive you don't mind reformatting, try removing your existing drives, slap the newer drive in there, install Ubuntu on that, and see how it behaves over time.

---

### Post by Lars&#1758; on 2008-12-09
so this is from a 1999 Dell. can i only get a few reformats on an HD before expecting hard drive failure?

---

### Post by bdoe on 2008-12-10
> **Lars&#1758 said:**
> so this is from a 1999 Dell. can i only get a few reformats on an HD before expecting hard drive failure?
Getting nine years out of a hard drive is pretty darned good - consider yourself lucky it lasted this long, promptly back up all of your data, and see about replacing the drive before it fails catastrophically.

---

### Post by Lars&#1758; on 2009-02-18
PROBLEM SOLVED:

i believe this was a GRUB error, i simply reformatted, reinstalled :popcorn: now rockin!

---

