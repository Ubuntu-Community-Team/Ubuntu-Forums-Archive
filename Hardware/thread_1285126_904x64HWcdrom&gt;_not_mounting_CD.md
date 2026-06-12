---
title: "904x64:HW:cdrom&gt; not mounting CD"
date: 2009-10-07
forum: Hardware
---

### Post by xerman on 2009-10-07
Hello there,

Today i found this issue on my desktop machine, intel based with ubuntu 904x64.

CD hardware is an LG DVD-RW SuperMulti, listed "lshw" as:```
*-cdrom
                   description: DVD-RAM writer
                   product: DVDRAM GSA-H42N
                   vendor: HL-DT-ST
                   physical id: 0.0.0
                   bus info: scsi@6:0.0.0
                   logical name: /dev/cdrom
                   logical name: /dev/cdrw
                   logical name: /dev/dvd
                   logical name: /dev/dvdrw
                   logical name: /dev/scd0
                   logical name: /dev/sr0
                   version: RL00
                   capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                   configuration: ansiversion=5 status=nodisc

```

This result is produced with a CD in the tray, notice "status=nodisc". In fact there is no disc on the desktop, and there is no disk on the cdrom in the directory tree. CDrom only has 4 pictures in it, 32MB total.

I did gain access to the files by puting the CD on the server machine on a LG DVD-ROM. There had no issues. Server has ubuntu 904x86.

On desktop i did also a "sudo mount -a" and nothing happened.

So i can't understand why in one computer (server) shows up, and on the other (desktop) does not.

Any light on this would be appreciated.

Thanks
Best regards

Xermán

---

