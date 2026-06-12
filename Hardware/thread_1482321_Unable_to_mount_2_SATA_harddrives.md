---
title: "Unable to mount 2 SATA harddrives"
date: 2010-05-13
forum: Hardware
---

### Post by ResidentBio on 2010-05-13
I've been trying to mount two harddrives:

*-disk:0
       description: ATA Disk
       product: WDC WD2500JD-75H
       vendor: Western Digital
       physical id: 0.1.0
       bus info: scsi@0:0.1.0
       logical name: /dev/sda
       version: 08.0
       serial: WD-WMAL73025626
       size: 232GiB (250GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=7df31e4a

The two are identical and they used to be in rad MANY years ago. For some reason i'm unable to mount them. 

I used the command $ sudo lshw -C disk, and for some reason the second unit does not appear(should be sdb)

I check in gparted, and there it is, but both show with a yellow triangle with an exclamation mark, which i don't really know what it means. I try to run check, but i get this error:
 dosfsk -a -w -v /dev/sda2
 
 open: no such devices or address

 Then i downloaded mount manager app, and i can see the 2 HD and they show as having isw_raid_member, which confuses me. They are not in raid, and they work without problems in win. So can anyone give me a clue how to proceed plz.

Thanx in advcance

---

