---
title: "Can't remount USB thumbdrive"
date: 2007-07-14
forum: Hardware &amp; Laptops
---

### Post by iAlta on 2007-07-14
I unmounted a thumbdrive with umount, but I can't mount it again. 

```
~$ mount /dev/sdc1
mount: can't find /dev/sdc1 in /etc/fstab or /etc/mtab

```

I get the same response with 'mount /dev/sdc'

```
~$ lsusb
Bus 005 Device 002: ID 13fe:1d00 
```

The 'mount' man page is over 1000 lines, I ain't reading that. SSo I was wondering if anyone knew how to use mount and could just tell me what to type in the terminal.

---

### Post by Jussi Kukkonen on 2007-07-14
> The 'mount' man page is over 1000 lines, I ain't reading that.

Fine. But if you had taken at a look, you would have found out that 90% of that man page is just mount options for different filesystems. As a matter of fact just the "Description" part in the beginning would have gotten you started:
```
       The standard form of the mount command, is
              mount -t type device dir
       This  tells the kernel to attach the file system found on device (which
       is of type type) at the directory dir.
```
and:
```
       The file /etc/fstab (see fstab(5)), may contain lines  describing  what
       devices  are  usually  mounted where, using which options. This file is
       used in three ways:
       (clip)

       (ii) When mounting a file system mentioned in  fstab,  it  suffices  to
       give only the device, or only the mount point.

       (iii)  Normally,  only  the superuser can mount file systems.  However,
       when fstab contains the user option on a line, anybody  can  mount  the
       corresponding system.

```

So, points you could have gotten from reading the "description" section:
  * if you have a /etc/fstab entry you can mount things like you tried
  * otherwise you need to be root and you also need to specify the mount directory

---

### Post by iAlta on 2007-07-14
OK, thanks!

So it's:

```
sudo mount -t vfat /dev/sdc1 /mnt/usb
```
?

EDIT:
I get this response: 
```
mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

then I type dmesg | tail, and I get:

```
[34819.339695] FAT: bogus number of reserved sectors
[34819.339704] VFS: Can't find a valid FAT filesystem on dev sdc1.

```

I could've svore I had FAT32 on there.

I followed this how-to: [http://www.damnsmalllinux.org/wiki/index.php/Installing_to_a_USB_Flash_Drive](http://www.damnsmalllinux.org/wiki/index.php/Installing_to_a_USB_Flash_Drive)

EDIT2:
from the howto:
> Create a FAT16 or FAT32 partition on the pendrive: mkfs.vfat -F 32 /dev/sdX1 ("-F 32" will do FAT32; "-F 16" will do FAT16)

from the terminal history:
```
~$ mkfs.vfat -F 32 /dev/sdc1
```

---

