---
title: "can't play dvds"
date: 2011-05-29
forum: Hardware
---

### Post by rickc1970 on 2011-05-29
I'm using Ubuntu 10.10 on an Aspire 5734z-4725. I can't play dvd movies. I have tried several but keep getting an i/o error. Any help would be appreciated. i have searched the forum for simliar problems but my problems seems to be a bit different from the ones I have read.

I have the results of 

rick@rick-Aspire-5734Z:~$ sudo lshw -C disk
  *-disk                  
       description: ATA Disk
       product: Hitachi HTS54503
       vendor: Hitachi
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: PB3O
       serial: 100528PBNC04EYG7082S
       size: 298GiB (320GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000260c7
  *-cdrom
       description: DVD-RAM writer
       product: DVD A  DS8A4SH
       vendor: Slimtype
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: CA11
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=open
  *-disk
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/sdb
       size: 3904MiB (4093MB)
       capabilities: partitioned partitioned:dos
rick@rick-Aspire-5734Z:~$

---

### Post by rickc1970 on 2011-05-29
Nevermind...I found how to install medbuntu and some codecs and it worked.

---

