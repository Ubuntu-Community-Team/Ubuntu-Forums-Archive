---
title: "HDD swap after running XP"
date: 2008-12-02
forum: Hardware
---

### Post by frank.s on 2008-12-02
Hi All,

On my XP/Ubuntu dual boot PC, I have two NTFS volumes mounted in Ubuntu. After I boot XP the mounted volumes swap names the first time I boot Ubuntu. If I restart my PC and boot Ubuntu again, the volumes are swapped back to their original (and desired) names.

I am using Mozilla Thunderbird on both platforms - in Ubuntu I've created a file link to my mail archive on one of the NTFS volumes, and it works fine, except when I have been running XP - very frustrating.

I've used the SuperGrub Boot CD ([http://www.supergrubdisk.org]("http://www.supergrubdisk.org")) to get my dual boot system working, and I used the EASY LIVE SWAP-feature to make both OS's work.

Since I've upgraded to 8.10 the problems began. It worked fine on 8.04. 

Any ideas?

- Frank

Below: fstab, menu.lst and result of fdisk -l


fdisk -l:
```

Disk /dev/sda: 120.0 Gb, 120034123776 byte
255 heads, 63 sectors/track, 14593 cylinders
Units = cylindre of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8dd098d6

    Enhed Opstart   Start         Slut     Blokke   Id  System
/dev/sda1   *           1       14593   117218241    6  FAT16

Disk /dev/sdb: 120.0 Gb, 120034123776 byte
255 heads, 63 sectors/track, 14593 cylinders
Units = cylindre of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0a3fb92d

    Enhed Opstart   Start         Slut     Blokke   Id  System
/dev/sdb1   *           1        7649    61440561    7  HPFS/NTFS
/dev/sdb2            7650        7662      104422+  82  Linux swap / Solaris
/dev/sdb3            7663       14463    54629032+  83  Linux
/dev/sdb4           14464       14593     1044225    f  w95 udvidet (LBA)
/dev/sdb5           14464       14593     1044193+  82  Linux swap / Solaris

```

My menu.lst:
```

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=7a4d92f8-4f97-484f-be86-2b0edfda3100 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

...[irrelevant entries removed]...

title		Microsoft Windoze XP Professional
root		(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

My fstab:
```

proc /proc proc defaults 0 0
# Entry for /dev/sdb3 :
UUID=7a4d92f8-4f97-484f-be86-2b0edfda3100 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sdb2 :
UUID=0217969f-405a-449d-ba51-1f010517423e none swap sw 0 0
# Entry for /dev/sdb5 :
UUID=cc29d72b-f44d-405e-898e-c6b1ce647f97 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
/dev/sda1 /media/Backup ntfs-3g quiet,defaults,locale=en_DK.UTF-8 0 0
/dev/sdb1 /media/disk ntfs-3g quiet,defaults,locale=en_DK.UTF-8 0 0

```

---

