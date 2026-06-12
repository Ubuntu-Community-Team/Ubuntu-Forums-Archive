---
title: "Gparted Live USB &amp; Syslinux"
date: 2008-08-20
forum: General Help
---

### Post by Elcid247 on 2008-08-20
ok ive followed the instructions [here]("http://ubuntuforums.org/showthread.php?t=449741") to make a Gparted Live USB manually since the Gparted Live USB isnt working.

when i boot into my usb, it gives me this error

```
boot:Kernel image not found: linux
```

any ideas?

---

### Post by amitkher on 2008-08-20
Are you sure you recognize your USB device i.e. /dev/sda or /dev/sdb or /dev/sdc etc.?

An output of the following when your USB drive is plugged in will be helpful:
```

sudo /sbin/fdisk -l

```

---

### Post by Elcid247 on 2008-08-20
yep its /dve/sdb1

```
Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9676     3928060    b  W95 FAT32

```

and the syslinux does creat the ldlinux.sys and all the files have been copied correctly

heres the output of ls /media/disk

```
boot.msg  gparted.dat  ldlinux.sys  splash.lss
gparted   gparted.igz  options.msg  syslinux.cfg

```

:confused::confused:

---

### Post by helpman on 2009-08-04
I had the same problem. You need to put the syslinux.cfg into /boot/syslinux/ directory.

---

