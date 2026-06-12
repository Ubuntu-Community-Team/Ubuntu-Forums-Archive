---
title: "No dvd+-r reading, but cdrom and dvd-video yes"
date: 2008-09-21
forum: Hardware
---

### Post by rafanpiro on 2008-09-21
I can't read all of my dvd+-r burned with linux (k3b, brasero, gnomebaker...) but the drive can read cd-audio and dvd-video.

A few months ago my drive stopped recognizing blank dvd's and cd's. Tired of it I've changed that drive and now it recognizes media, but qhe trying to burn a cd-audio it fails. Old Dvd+-r with my divx aren't recognized and I can't mount them either in a terminal.

I've seen a lot of threads but I can't find the same problem.
Drives are ATA and this is hdparm:

[INDENT]/dev/scd0:
 IO_support    =  0 (default) 
16-bit)
 HDIO_GET_UNMASKINTR failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_KEEPSETTINGS failed: Inappropriate ioctl for device
 readonly      =  0 (off)
 readahead     = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device[/INDENT]

lsmod | grep ata : 
[INDENT]root@acer:/etc/default# lsmod | grep ata
pata_amd               14212  3 
sata_nv                27528  5 
ata_generic             8324  0 
pata_acpi               8320  0 
libata                159344  4 pata_amd,sata_nv,ata_generic,pata_acpi
scsi_mod              151436  6 sbp2,sr_mod,sg,sd_mod,usb_storage,libata
[/INDENT]

Athlon 64 3400+, nForce2, 1gb ram, sda (sata drive), sdb (ata drive), scd0 (liteon dvd +-rw), Hardy Heron

Any ideas?
Thanx

---

