---
title: "GRUB error with the new kernel"
date: 2005-11-23
forum: General Help
---

### Post by dodongo on 2005-11-23
After loading all the requisite packages for the new kernel update from a day or two ago, I can't boot the new kernel at all.

GRUB give me "Error 15: File Not Found".  Everywhere else seems to note this is a problem with matching the fstab entries and the location of the kernel in /boot/grub/menu.lst

However, all my kernels are in the same folder, the files do appear to be there, and I can still boot into kernel 2.6.12-9 (just not the new 2.6.12-10).  Here's fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               reiserfs notail,noatime  0       1
/dev/sda3       /home           reiserfs notail,noatime  0       2
/dev/hda1       /media/hda1     reiserfs defaults        0       2
# /dev/hdb1       /media/hdb1     reiserfs defaults        0       2
# /dev/hda5       none            swap    sw              0       0
/dev/sda2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
# /dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

And here's  (a selected portion of) /boot/grub/menu.lst:
```

title           Ubuntu, kernel 2.6.12-10-686-smp 
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.12-10-686-smp root=/dev/sda1 ro quiet splash
initrd          /boot/initrd.img-2.6.12-10-686-smp
savedefault
boot

title           Ubuntu, kernel 2.6.12-10-686-smp (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.12-10-686-smp root=/dev/sda1 ro single
initrd          /boot/initrd.img-2.6.12-10-686-smp
boot

title           Ubuntu, kernel 2.6.12-9-686-smp 
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.12-9-686-smp root=/dev/sda1 ro quiet splash
initrd          /boot/initrd.img-2.6.12-9-686-smp
savedefault
boot

title           Ubuntu, kernel 2.6.12-9-686-smp (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.12-9-686-smp root=/dev/sda1 ro single
initrd          /boot/initrd.img-2.6.12-9-686-smp
boot

```

And for good measure, the contents of /boot:

```
abi-2.6.12-10-686-smp         initrd.img-2.6.12-9-686-smp
abi-2.6.12-9-686-smp          memtest86+.bin
config-2.6.10-5-686-smp       System.map-2.6.10-5-686-smp
config-2.6.12-10-686-smp      System.map-2.6.12-10-686-smp
config-2.6.12-9-686-smp       System.map-2.6.12-9-686-smp
grub                          vmlinuz-2.6.10-5-686-smp
initrd.img-2.6.10-5-686-smp   vmlinuz-2.6.12-10-686-smp
initrd.img-2.6.12-10-686-smp  vmlinuz-2.6.12-9-686-smp

```

Anyone have any ideas what's going wrong?

---

