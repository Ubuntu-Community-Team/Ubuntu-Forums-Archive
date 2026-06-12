---
title: "JFS mount"
date: 2007-03-11
forum: Hardware &amp; Laptops
---

### Post by starling on 2007-03-11
Can someone tell me what i'm doing wrong? I recently formatted my second hard drive with both an NTFS and JFS file system. fdisk -l looks like this:
```
Disk /dev/hdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1           17654       30401   102398310    7  HPFS/NTFS
/dev/hdb2               1       17653   141797691   83  Linux

```

and in my oh so finite knowledge put what's in bold into fstab:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=7337ffe9-ebe3-45a4-907e-d2adef6e2419 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=0A98586D985858F1 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda3
UUID=3bf6413f-281a-46c0-8077-99ce5bf5cf4e none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

[B]/dev/hdb2	/media/media	jfs	defaults,errors=remount-ro	0	0
/dev/hdb1	/media/vids	ntfs	nls=utf8,umask=0222	0       1[/B]

and it worked. briefly. I loaded all my music onto the jfs partition but after restarting it won't mount again :(. I now have the ntfs partition mounted but not the jfs.
Trying to mount manually does this:
```
mark@mark-desktop:~$ sudo mount /dev/hdb2 /media/media/
mount: wrong fs type, bad option, bad superblock on /dev/hdb2,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

What's going on?
Thanks.

---

### Post by starling on 2007-03-12
It's ok everyone, I worked it out myself. That is to say another hour of searching the forums and experimentation led me to [this]("http://www.ubuntuforums.org/showthread.php?t=209345&highlight=how+to+mount+jfs") post and by changing the options from default to rw seems to have stopped the error.

What i can't work out is how it stopped working without me changing anything. It was fine, then it wasn't. Hard drives are fickled things, don't even get me started on jumpers.

---

