---
title: "Yet Another DMA DVD Problem"
date: 2007-06-20
forum: Hardware &amp; Laptops
---

### Post by Qbasicer on 2007-06-20
Ok, so I've searched google, to what I think, quite extensively.  Probably the first 8 pages or so.

Anyways, yes, I'm having a problem with a slow DVD drive.  I can currently grip at 1.4x max.  Sometimes, the tracks get garbled up for about 5 seconds, but I contribute that to this problem.

Anyways.
> root@qbasicer-laptop:~# wodim -checkdrive dev=/dev/sr0
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'MATSHITA'
Identification : 'DVD-RAM UJ-841S '
Revision       : '1.60'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO
root@qbasicer-laptop:~# 

hdparam:
> root@qbasicer-laptop:~# hdparm /dev/sr0 

/dev/sr0:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device
root@qbasicer-laptop:~# 

Setting DMA:
> root@qbasicer-laptop:~# hdparm -d1 /dev/sr0 

/dev/sr0:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
root@qbasicer-laptop:~# 

I found a few 'fixes' that involved setting the hdparm config file to force dma=on, but that didn't work.

Suggestions?

OH!  I tried to mount my disk:
> root@qbasicer-laptop:~# mount /dev/cdrom
[mntent]: warning: no final newline at the end of /etc/fstab
mount: block device /dev/cdrom is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/cdrom,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

root@qbasicer-laptop:~#

Also
> root@qbasicer-laptop:~# dmesg |tail
[11406.572000] ata2.00: configured for UDMA/33
[11406.572000] sr 1:0:0:0: SCSI error: return code = 0x08000002
[11406.572000] sr0: Current [descriptor]: sense key: Medium Error
[11406.572000]     Additional sense: Address mark not found for data field
[11406.572000] Descriptor sense data with sense descriptors (in hex):
[11406.572000]         72 03 13 00 00 00 00 0e 09 0c 00 51 00 03 00 00 
[11406.572000]         00 00 00 00 a0 51 
[11406.572000] end_request: I/O error, dev sr0, sector 64
[11406.572000] ata2: EH complete
[11406.572000] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
root@qbasicer-laptop:~# 

---

