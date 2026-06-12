---
title: "Sata ntfs drive problem"
date: 2005-03-27
forum: Hardware &amp; Laptops
---

### Post by PaTTeX on 2005-03-27
hello guys (sorry for my bad english)

i have a sata drive with ntfs on my system but i can't mount it :/
my fstab:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1 /media/C ntfs ro,umask=0222 0 0
/dev/hdb1  /media/F ntfs ro,umask=0222 0 0
/dev/sda  /media/E ntfs ro,umask=0222 0 0
#/dev/hdb1 /media/F captive-ntfs defaults,noauto 0 0
#/dev/hda1 /media/C captive-ntfs defaults,noauto 0 0
#/dev/sda1 /media/E captive-auto defaults,noauto 0 0
```

```

root@Julien:/home/julien # fdisk -l

Disque /dev/hda: 120.0 Go, 120034123776 octets
255 têtes, 63 secteurs/piste, 14593 cylindres
Unités = cylindres de 16065 * 512 = 8225280 octets

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/hda1   *           1       14592   117210208+   7  HPFS/NTFS

Disque /dev/hdb: 122.9 Go, 122942324736 octets
255 têtes, 63 secteurs/piste, 14946 cylindres
Unités = cylindres de 16065 * 512 = 8225280 octets


[code]root@Julien:/home/julien # mount -a mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

```

root@Julien:/home/julien # dmesg | tail
Nvsound: Unable to change the Record SampleRate 96000, set back to 48000
Nvsound: Unable to change the Record SampleRate 96000, set back to 48000
Nvsound: Unable to change the Record SampleRate 96000, set back to 48000
cdrom: open failed.
cdrom: open failed.
cdrom: open failed.
cdrom: open failed.
NTFS-fs error (device sda): read_ntfs_boot_sector(): Primary boot sector is invalid.
NTFS-fs error (device sda): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
NTFS-fs error (device sda): ntfs_fill_super(): Not an NTFS volume.

```

any idea ?

---

### Post by fackamato on 2005-03-27
sda is a harddrive, sda# are partitoins (sda1, sda2 etc), try using that?

---

