---
title: "SCSI hardisk size vs capacity"
date: 2008-08-21
forum: Hardware
---

### Post by james_mcphail on 2008-08-21
Hello,
I have two hard drives of identical make and model.  I want to copy one to another.  I have installed the first drive and run:
dd if=/dev/sdb of=myimage.iso

When I install 2nd drive, I run out of space while using:
dd if=myimage.iso of=/dev/sdb

output of detail of destination drive from "lshw -C disk":
  *-disk
       description: SCSI Disk
       product: DCAS-32160W
       vendor: IBM
       physical id: 0.4.0
       bus info: scsi@2:0.4.0
       logical name: /dev/sdb
       version: S65A
       serial: F26L7833
       size: 1023MiB (1073MB)
       capacity: 2050MiB (2150MB)
       capabilities: 5400rpm
       configuration: ansiversion=2 signature=00000600

What is going on here?

---

