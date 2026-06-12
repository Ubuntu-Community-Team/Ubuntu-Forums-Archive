---
title: "/etc/fstab problem"
date: 2008-10-24
forum: General Help
---

### Post by Spitphire on 2008-10-24
Why does my fstab show /dev/sdb1 as a cdrom and my fdisk show it has my external hard drive?  This particular box does not even have a cd-rom drive.

When I plug the external hard drive in, it tries to mount it however it is unsuccessul stating "Invalid mount option when attempting to mount the volume 'My Book'."

The drive mounts fine with sudo mount; however i cannot alter any files on the drive as a normal user..

How do i get rid of the cdrom in fstab as well as floppy drive and get things working properly.  I'm afraid to add info to fstab as there is already an entry for /dev/sdb1

Exert from fdisk -l:

```

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfa48b3ed

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001    c  W95 FAT32 (LBA)


```

/etc/fstab:

```

cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=22201a8f-8dd7-45c2-bf3b-0e9b3802d60b /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=85d260e7-bb03-4030-b441-7a9a5d0d87df none            swap    sw              0       0
/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0


```

---

### Post by dabl on 2008-10-24
Open /etc/fstab in your favorite text editor, in root mode, and just insert a "#" in front of the bogus CD ROM mount line, so it reads:

```
# /dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

and save it.

I'm not sure what the "invalid mount" error is, but if you google that and "udev" you'll probably stumble into the correct ballpark for solving it.  :)

---

### Post by Spitphire on 2008-10-24
Well in the last 20 minutes I had a revelation.  I remembered when I installed ubuntu on this particular box I installed it off of a USB drive because the box didn't have a cd-rom. 

I'm speculating during the course of that install it set /dev/sdb1 as cdrom in /etc/fstab so it could install ubuntu.  Now whenever a new USB drive is plugged in, it is unable to mount because of the conflict...

Solution: remove line from /etc/fstab and reboot, what do you think?

-Spit

---

### Post by geirha on 2008-10-24
It's a bug when installing from a usb-stick. The installer thinks it is installing from a cdrom and adds an entry to fstab for the "cdrom".

---

### Post by Spitphire on 2008-10-24
lol, guess we all came to the same conclusion at the same time..

---

### Post by mempman on 2008-10-24
If you are connecting your external hd via usb, try the following command:
```

lsusb

```

also look in:
/dev/disk/by-path/

---

### Post by fahdovski on 2008-10-26
Help me i can't mount my dvd. i think its UDF 2.5 problem:mad:

---

