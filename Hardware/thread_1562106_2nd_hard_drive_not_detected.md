---
title: "2nd hard drive not detected"
date: 2010-08-27
forum: Hardware
---

### Post by marklah on 2010-08-27
Hi,

I have to physical hard drives on my pc. 1 SATA 1 IDE. Ubuntu is installed on the SATA drive. Both drives are detected in the BIOS but I cant see the IDE drive in ubuntu. Any suggestions? Thanks

marklah@marklah-desktop:~$ sudo lshw -c disk
  *-disk                  
       description: ATA Disk
       product: WDC WD2500KS-00M
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: 02.0
       serial: WD-WCANK9810561
       size: 232GiB (250GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=f6daf6da
  *-cdrom
       description: DVD-RAM writer
       product: DRW-24B1ST
       vendor: ASUS
       physical id: 0.1.0
       bus info: scsi@2:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.01
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc

---

