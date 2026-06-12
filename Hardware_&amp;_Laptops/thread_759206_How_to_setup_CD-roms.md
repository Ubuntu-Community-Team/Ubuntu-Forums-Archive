---
title: "How to setup CD-roms ??????"
date: 2008-04-18
forum: Hardware &amp; Laptops
---

### Post by boast on 2008-04-18
what command can I do view where my cdroms are at, and what my fstab line should look like?

or am I doing it right???

```
~$ sudo lshw -C disk
  *-cdrom:0
       description: DVD reader
       product: DVD-ROM SD-616E
       vendor: SAMSUNG
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: F503
       capabilities: removable audio dvd
       configuration: ansiversion=5 status=open
  *-cdrom:1
       description: CD-R/CD-RW writer
       product: CRW-4832AS
       vendor: ASUS
       physical id: 0.1.0
       bus info: scsi@1:0.1.0
       logical name: /dev/cdrom1
       logical name: /dev/scd1
       logical name: /dev/sr1
       version: 0.67
       capabilities: removable audio cd-r cd-rw
       configuration: ansiversion=5 status=open

```

```
/dev/scd0 /media/cdrom0 auto         user,noauto,ro 0 0
/dev/scd1 /media/cdrom1 auto        user,noauto 0 0

```

Because I can not get DVDs to mount

```

~$ sudo mount /dev/scd0
mount: No medium found
~$ sudo mount /dev/scd1
mount: No medium found
```

---

