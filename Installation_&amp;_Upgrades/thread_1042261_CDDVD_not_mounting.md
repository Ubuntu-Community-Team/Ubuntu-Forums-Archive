---
title: "CD/DVD not mounting"
date: 2009-01-17
forum: Installation &amp; Upgrades
---

### Post by mohitw on 2009-01-17
I am having ubuntu 8.04 installed on amd 64 bit PC (dual boot with ubuntu and vista). When I put CD in the drive , nothing happens. 

one of the earlier threads mentioned about checking the fstab file. here are the contents when I open that:

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda4
UUID=c439a46e-5b91-4d74-8c57-1c873e06d6cc / ext3 relatime,errors=remount-ro 0 1
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

when I checked /dev for scd0 ..it seems there is no scd0 file.
Please help

( i also tried disabling the CDRom in the BIOS..as some threads earlier mentioned about that..it doesn't work)

---

### Post by hanniph on 2009-01-20
bump! I have same problem and cannot find a solution. 

However, seems like some stuff worked for others:
try to 
comment out your cdrom mount line in /etc/fstab:
```
#/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

```
or 
load kernel with noapic acpi=off option

---

### Post by Sorandal on 2009-01-21
Hi, I have a different laptop, but I also had troubles getting CDs and DVDs to be recognised.  What worked for me is going into the BIOS and changing the SATA mode from "Enhanced" to "compatability".  This worked, but the downside is that vista will not boot in "compatability mode, so you have to change the BIOS setting whenever you switch between vista and ubuntu.

---

