---
title: "Strange mount behaviour"
date: 2007-04-06
forum: Hardware &amp; Laptops
---

### Post by PsychedelicReaction on 2007-04-06
I got 4 partitions on my hard disk. That's fdisk

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cilindri of 16065 * 512 = 8225280 bytes

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1305    10482381   83  Linux
/dev/sda2            1306        1436     1052257+  82  Linux swap / Solaris
/dev/sda3            1437        2741    10482412+   7  HPFS/NTFS
/dev/sda4            2742       14593    95201190   83  Linux

```

in sda1 there's ubuntu, sda2 is swap, sda3 is ntfs for windows and then in sda4 i store data.

Since the first boot sda4 is not mounted by default, i have to mount it as root and i don't even permissions to execute files.

This is my fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1 -- converted during upgrade to edgy
UUID=1c47fd57-2ae4-49c1-a9bf-6f7037c43b8a / ext3 defaults,errors=remount-ro 0 1
# /dev/sda3 -- converted during upgrade to edgy
UUID=014608C4242A38D5 /media/sda3 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/sda4 -- converted during upgrade to edgy
UUID=82e9f2c6-cc25-4c30-924d-1227c6debde3 /media/sda4 ntfs defaults 0 1
# /dev/sda2 -- converted during upgrade to edgy
UUID=08519694-252a-4591-ad4a-5c19b7c1cd3b none swap sw 0 0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

As you can see sda4 appears as ntfs! I tried to change ntfs to ext3 but i have some errors during the boot. I use Feisty on a Hp Pavilion DV2172 and I never had problems since last format.

---

