---
title: "Can't mount DVD, but can mount CD (IDE/SCSI)"
date: 2008-07-29
forum: Hardware
---

### Post by Yoshis88 on 2008-07-29
Hi, I'm working on a problem regarding my dvd-drive for a client in my professors research lab (need to install MATLAB).  I'm trying to get it to recognize dvd media.  I know this is the Ubuntu forums, but this is a Debian box, and we're pulling out our hair trying to get it to work.

From a root terminal and with a data dvd in the drive, when I say,
```
mount /media/cdrom
```
It says
```
mount: No medium found
```

The relevant fstab line is:
/dev/hdb    /media/cdrom    udf,iso9660    user,noauto    0    0

I'm disenclined to believe its a hardware error as I can mount CD-rom's just fine.  It should be noted that there are 3 SCSI drives and 2 IDE drives, and it boots off of the first SCSI drive, though I needed to change the (hd0,2) to (hd0,0) in the menu.lst file (below).

Here is the non-commented lines of my menu.lst
```

default		0
timeout		5
color cyan/blue white/blue

title		Debian GNU/Linux, kernel 2.6.18-5-686
root		(hd0,0)
kernel		/vmlinuz-2.6.18-5-686 root=/dev/sda2 ro 
initrd		/initrd.img-2.6.18-5-686
savedefault

title		Debian GNU/Linux, kernel 2.6.18-5-686 (single-user mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.18-5-686 root=/dev/sda2 ro single
initrd		/initrd.img-2.6.18-5-686
savedefault


```

Any help or pointers would be very greatly appreciated.  Will post any commands wished for.

---

### Post by skelooth on 2008-07-31
Have you tried specifiying the format? I have had issues with Macintosh discs in the past, where the solutin was to comment out the regular cdrom fstab entry and replace it with

/dev/hdb /media/cdrom hfs user,noauto 0 0
or
/dev/hdb /media/cdrom hfsplus user,noauto 0 0

if it's not a mac disc then I have no idea either. Does the disc grind around before giving up?

---

