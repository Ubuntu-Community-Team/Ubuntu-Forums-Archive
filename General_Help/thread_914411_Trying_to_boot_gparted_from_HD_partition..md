---
title: "Trying to boot gparted from HD partition."
date: 2008-09-08
forum: General Help
---

### Post by dodle on 2008-09-08
I am trying to boot gparted from a partition on my hard drive.  The partition is formatted as fat.  From Grub, gparted starts to boot but then and endless loop:
```
.
.
.
.
hda: cache flushes supported
 hda: hda1 hda2 hda3
hdc: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache
Uniform CD-ROM driver Revision: 3.20
Done.
Begin: Mounting root file system... ...
Begin: Running /scripts/live-premount ...
Done.
mount: No such device
/init: line 173: cannot open /dev/hdc: No medium found
/init: line 173: cannot open /dev/hdc: No medium found
mount: No such device
/init: line 173: cannot open /dev/hdc: No medium found
/init: line 173: cannot open /dev/hdc: No medium found
mount: No such device
/init: line 173: cannot open /dev/hdc: No medium found
/init: line 173: cannot open /dev/hdc: No medium found
mount: No such device
/init: line 173: cannot open /dev/hdc: No medium found
/init: line 173: cannot open /dev/hdc: No medium found
.
.
.
.
```This continues until I hit "Ctr + c".  This is what I think is the matter, but I don't know how to fix it:  When the system begins loading the initrd1.img, it finds a line that tells it to mount the file system from the CD-ROM (which is not loaded because I am boot from the hard drive).  The reason I am trying to do it this way is because 1.) my CD drive does not work, 2.) I can use a usb CD drive but my bios sucks and can't read gparted livecd from a usb device.  You're probably wondering how I was able to make a separate partition for gparted to begin with.  I used an Ubuntu live cd to create a second partition.  Yes I could just use that cd to do all my partitioning, but if I can get gparted to load from the hard disk that will be much easier than finding my dad's external CD drive, then finding my Ubuntu cd, and waiting for it to load.  Here is my /boot/grub/menu.lst:
> title Gparted v0.3.7
kernel /live/vmlinuz1 root=UUID=42A8BB1DA8BB0E83 boot=live uion=aufs noswap noprompt vga=792 ip=frommedia
initrd /live/initrd1.img
bootDoes anyone know how I can fix this?

---

