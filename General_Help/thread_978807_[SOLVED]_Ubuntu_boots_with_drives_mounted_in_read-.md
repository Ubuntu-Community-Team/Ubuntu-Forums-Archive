---
title: "[SOLVED] Ubuntu boots with drives mounted in read-only mode"
date: 2008-11-11
forum: General Help
---

### Post by jvincent08 on 2008-11-11
This is an odd problem that I can't seem to figure out. Just like the title says, Ubuntu (Intrepid) is booting up with the drives mounted as read-only, causing a slew of errors from syslog and probably a few other processes, as well as preventing X from starting. Here's /etc/fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=49b6f578-a680-4181-b4dd-85b812a766f8 /               ext3    relatime,errors=remount-ro0       1
# /dev/sda2
UUID=000c7dd0-e495-493e-8835-ddb140603b60 /boot           ext3    relatime        0       2
# /dev/sdb3
UUID=b0620cd3-3919-41b2-9c01-c1bb074b28e4 /home           ext3    relatime        0       2
# /dev/sdb2
UUID=74856937-905a-48e2-bc27-b9f948e6f06d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```
Everything looks fine there. Here's /boot/grub/menu.lst:
```

title		Ubuntu Studio 8.10, kernel 2.6.27-7-generic
uuid		2e9358a7-fe4f-41ee-8174-9a20299f67f1
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=2e9358a7-fe4f-41ee-8174-9a20299f67f1 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu Studio 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		2e9358a7-fe4f-41ee-8174-9a20299f67f1
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=2e9358a7-fe4f-41ee-8174-9a20299f67f1 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		2e9358a7-fe4f-41ee-8174-9a20299f67f1
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd0,1)
kernel		/vmlinuz-2.6.27-7-generic root=UUID=49b6f578-a680-4181-b4dd-85b812a766f8 ro quiet splash 
initrd		/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,1)
kernel		/vmlinuz-2.6.27-7-generic root=UUID=49b6f578-a680-4181-b4dd-85b812a766f8 ro single 
initrd		/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.10, memtest86+ (on /dev/sdb1)
root		(hd0,1)
kernel		/memtest86+.bin  
savedefault
boot

```
As you can see, I have two Ubuntu installations: Ubuntu Studio and Desktop. Studio starts fine (that's what I'm using right now); Desktop (/dev/sdb1) is the one that's giving me trouble. This is the first time I've rebooted my computer in a long time, so this could be coming from a change I made a while ago that I'm only now seeing the repercussions of. Unfortunately, I can't remember any changes at all (other than installing Studio, but even after that I was still able to switch between Studio and Desktop just fine). Anybody else have any ideas on where I could look?

---

### Post by drs305 on 2008-11-11
Well, one thing in fstab that needs correcting:
```
# /dev/sdb1
UUID=49b6f578-a680-4181-b4dd-85b812a766f8 /               ext3    relatime,**[COLOR="Red"]errors=remount-ro0 [/COLOR]**      1

```

Should be:
```

# /dev/sdb1
UUID=49b6f578-a680-4181-b4dd-85b812a766f8 /               ext3    relatime,**[COLOR="Red"]errors=remount-ro 0[/COLOR]**       1

```

Notice the space. That could be the problem, but even if not should be corrected.

---

### Post by jvincent08 on 2008-11-11
> **drs305 said:**
> Well, one thing in fstab that needs correcting:
```
# /dev/sdb1
UUID=49b6f578-a680-4181-b4dd-85b812a766f8 /               ext3    relatime,**[COLOR="Red"]errors=remount-ro0 [/COLOR]**      1

```

Should be:
```

# /dev/sdb1
UUID=49b6f578-a680-4181-b4dd-85b812a766f8 /               ext3    relatime,**[COLOR="Red"]errors=remount-ro 0[/COLOR]**       1

```

Notice the space. That could be the problem, but even if not should be corrected.

Wow, good catch! Turns out that was the problem. I wonder why that would've caused the drives to be mounted in read-only though? Thanks!

---

### Post by jvincent08 on 2008-11-11
Double post..

---

