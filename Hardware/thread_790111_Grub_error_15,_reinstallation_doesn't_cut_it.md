---
title: "Grub error 15, reinstallation doesn't cut it"
date: 2008-05-11
forum: Hardware
---

### Post by PureW on 2008-05-11
Hello there, my problem is that grub won't boot anymore. It just says:
> Grub: loading stage 1.5
Error 15...
Not file missing or anything.

I think it all started yesterday when I booted after accidentally unplugging one harddrive. After plugging it in again it wouldn't boot.

I tried alot of things:
Booting from a livecd and entering the grub-terminal like in alot of tutorials. But I always get error messages not explained in the tutorials. 
The Super Grub Disk but that didn't work either, it said it couldn't find some file.

Eventually I got tired of it all and reinstalled Ubuntu, but the thing is, it still doesn't work! The installation has never caused me problems before on this computer.


menu.lst
> 
default		0
timeout		10
# Alot of commenting removed...

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=2fd2d0c4-411b-42f6-aafe-639970ac309f ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=2fd2d0c4-411b-42f6-aafe-639970ac309f ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows Vista/Longhorn (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

Fstab:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=2fd2d0c4-411b-42f6-aafe-639970ac309f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=8494cf4c-6a8d-4037-b42c-07903127f86b /home           reiserfs relatime        0       2
# /dev/sdb4
UUID=be6230d7-b679-4043-80c1-539b794cc5d7 /media/backup   reiserfs relatime        0       2
# /dev/sdb3
UUID=c2d14e65-9a8a-4398-9018-a7143becca77 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by catnap on 2008-05-11
Grub errors are at [http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html#Stage2-errors](http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html#Stage2-errors)

Hope this helps

---

