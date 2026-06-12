---
title: "CD Writer"
date: 2004-10-23
forum: Hardware &amp; Laptops
---

### Post by gamehack on 2004-10-23
Hello all,

As I was finishing setting up my Ubuntu installation, only cd-buring remained. But I could manage getting it running, although on other distros I did the same things and everything was fine. Here are some outputs.
dmesg | grep hdc
```

ide1: BM-DMA at 0x8088-0x808f, BIOS settings: hdc:pio, hdd:pio
hdc: HL-DT-STCD-RW/DVD DRIVE GCC-4240N, ATAPI CD/DVD-ROM drive
hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, DMA

```
cat /etc/fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               reiserfs defaults        0       1
/dev/hda4       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda2       /mnt/ntfs-c     ntfs    user,rw,auto,umask=022
/dev/hda3       /mnt/ntfs-d     ntfs    user,rw,auto,umask=022

```
The kernel is 2.6.9 compiled by myself.

Thanks very much

---

