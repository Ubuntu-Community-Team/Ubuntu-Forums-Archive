---
title: "Can't mount cd/dvd combo drive."
date: 2008-09-27
forum: Hardware
---

### Post by Gary13579 on 2008-09-27
ThinkPad X31 + UltraBase X3, using the UltraBay for a CD RW/DVD drive. I used it to install Ubuntu, so I know it's working.

Was trying to install World of Warcraft from a DVD, using Wine. Wine kept giving an error saying it can't launch the installer, so I tried copying a file over. Wouldn't let me. I restarted the notebook, and ever since the drive WILL NOT mount.

/etc/fstab:
```
gary@fluffy:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=49a84520-d68c-4121-bc8d-e278bb75110d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=53cf8cc2-3dae-430a-8250-496ce948047f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

Attempting to mount manually:
```
gary@fluffy:~$ sudo mount /media/cdrom0
[sudo] password for gary: 
mount: No medium found
gary@fluffy:~$ sudo mount /dev/scd0 /media/cdrom0 
mount: No medium found

```

Ubuntu does see the drive, but it will not mount ANY disc. CD, CD-R, DVD, or DVD-R, they all fail. I tested the ubuntu installer disc, and that booted, so it is a software issue, not hardware.

When inserting a DVD, I can hear the drive spin and sometimes click, for quite a while. But Ubuntu will still not mount it. Getting extremely annoyed, having spent 3 hours now working on this (Google brings up NO solutions, but many others have this same problem).

---

### Post by ajmorris on 2008-09-27
hi there,
before troubleshooting your drive in ubuntu, could you please test the drive in another OS? i.e, windows, or simply just a linux live cd, ubuntu or other.

AJ

---

### Post by Gary13579 on 2008-09-27
> **ajmorris said:**
> hi there,
before troubleshooting your drive in ubuntu, could you please test the drive in another OS? i.e, windows, or simply just a linux live cd, ubuntu or other.

> **Gary13579 said:**
> I used it to install Ubuntu, so I know it's working.

> **Gary13579 said:**
> I tested the ubuntu installer disc, and that booted, so it is a software issue, not hardware.

.

---

### Post by Gary13579 on 2008-09-27
Up.

---

### Post by ajmorris on 2008-09-27
ack, sorry was tired when i replied... missed that part

Ok, can you please insert a disc into the drive, and post the output of ```
sudo dmesg
```


AJ

---

