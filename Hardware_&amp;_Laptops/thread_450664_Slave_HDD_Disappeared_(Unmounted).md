---
title: "Slave HDD Disappeared (Unmounted)"
date: 2007-05-21
forum: Hardware &amp; Laptops
---

### Post by darthkorn on 2007-05-21
Hi Guys,

Fairly new to Ubuntu, been using it for a few months, and I've just recently decided to make the full fledged jump the Ubuntu and redo my system.  So I've reformatted my PC and loaded Feisty on it, everything went fine, and when I booted up the first time, my slave HDD that I use for storage (music, pictures, etc...) was there.  I edited some things, updated the system, installed some packages, fixed my xorg.conf (dual monitor suppport still sucks in feisty, but what can you do right?), and everything was going great.  Playing around with VirtualBox, I needed to reboot to get the group membership working properly, but when I came back up, my slave HDD (Fat32) was no where to be seen.  It is in a removeable caddy, and I had a problem before I formatted a few months back when I swapped it for another external, but it eventually came back (I honestly forgot what I ended up doing).

So now, I've rebooted a few times and it just wont come back to me.  My life is on this drive, and I really hate to play around with this much more.  Any ideas on things I can try?  When I try to mount it it tells me that hdb is not in fstab, which makes sense, but dmesg does see it.

Ideas?

EDIT:  I also tried:

sudo mount /dev/hdb5 /media/DOWNLOAD

and I'm getting a mount point does not exist error message.  I must say that alot of this is past my time.  I did alot of this stuff in school, but that was ages ago and with FC3, so I might be a bit rusty and it might be something just overall obvious that I am missing.

EDIT2: Ok, I definitely see it dmesg, I just rebooted to make sure it was the same model, but this is it here:

```
curtis@curtis-desktop:~$ dmesg | grep hdb
[   31.516243]     ide0: BM-DMA at 0xff00-0xff07, BIOS settings: hda:DMA, hdb:DMA
[   32.082246] hdb: WDC WD1600JB-00GVA0, ATA DISK drive
[   33.314012] hdb: max request size: 512KiB
[   33.315283] hdb: 312581808 sectors (160041 MB) w/8192KiB Cache, CHS=19457/255/63, UDMA(100)
[   33.317257] hdb: cache flushes supported
[   33.317299]  hdb: hdb1 < hdb5 >
```

So it is hdb5, but I can't mount it as root for some odd reason.

EDIT3: Ok, geting closer, I think, I created a folder in /media called DOWNLOAD.  I tried: sudo mount -v -t vfat /dev/hdb /media/DOWNLOAD

I got the error:

 ```
curtis@curtis-desktop:~$ sudo mount -v -t vfat /dev/hdb /media/DOWNLOAD
mount: wrong fs type, bad option, bad superblock on /dev/hdb,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

Checking dmesg again I got:

```
curtis@curtis-desktop:~$ dmesg | grep hdb
[   31.516243]     ide0: BM-DMA at 0xff00-0xff07, BIOS settings: hda:DMA, hdb:DMA
[   32.082246] hdb: WDC WD1600JB-00GVA0, ATA DISK drive
[   33.314012] hdb: max request size: 512KiB
[   33.315283] hdb: 312581808 sectors (160041 MB) w/8192KiB Cache, CHS=19457/255/63, UDMA(100)
[   33.317257] hdb: cache flushes supported
[   33.317299]  hdb: hdb1 < hdb5 >
[  723.500809] VFS: Can't find ext3 filesystem on dev hdb.
[  796.997973] NTFS-fs warning (device hdb): is_boot_sector_ntfs(): Invalid boot sector checksum.
[  796.997986] NTFS-fs error (device hdb): read_ntfs_boot_sector(): Primary boot sector is invalid.
[  796.997991] NTFS-fs error (device hdb): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[  796.997995] NTFS-fs error (device hdb): ntfs_fill_super(): Not an NTFS volume.
[  996.288099] VFS: Can't find a valid FAT filesystem on dev hdb.
[ 1178.671055] VFS: Can't find a valid FAT filesystem on dev hdb.
```

Is there something magically wrong with my drive?

---

