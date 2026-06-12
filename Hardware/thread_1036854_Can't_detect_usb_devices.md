---
title: "Can't detect usb devices"
date: 2009-01-11
forum: Hardware
---

### Post by ueghio on 2009-01-11
Hi guys,it's the first time I write on your forum,and I hope it's the right section..
My problem is that ubuntu (Hardy Heron) doesn't detect my telephone connected through a usb cable...Can anyone help me to mount it please?
This is my fstab file:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	defaults	0	0
#Entry for /dev/sda1 :
UUID=3da7ccdc-e5d4-4dcb-8b90-2b22fac3dc05	/	ext3	relatime,errors=remount-ro	0	1
#Entry for /dev/sda5 :
UUID=6e141a95-000b-4f6f-9192-65737f4887c2	none	swap	sw	0	0
none	/proc/bus/usb	usbfs	devgid=1001,devmode=664	0	0
none	/proc/bus/usb	usbfs	devgid=1001,devmode=664	0	0

#/dev/sdb1	/media/cdrom0	udf,iso9660	user,noauto,exec,utf8	0	0
#/dev/sdc0	/media/cdrom1	udf,iso9660	user,noauto,exec,utf8	0	0
```

and it is what I see when I write *lsusb* on command prompt:
```
gavvi@gavvi-notebook:~$ lsusb
Bus 007 Device 003: ID 04f2:b015 Chicony Electronics Co., Ltd
Bus 007 Device 001: ID 0000:0000 
Bus 006 Device 001: ID 0000:0000 
Bus 005 Device 002: ID 03f0:171d Hewlett-Packard
Bus 005 Device 001: ID 0000:0000 
Bus 004 Device 002: ID 08ff:2580 AuthenTec, Inc.
Bus 004 Device 001: ID 0000:0000 
Bus 003 Device 001: ID 0000:0000 
Bus 002 Device 002: ID 0bb4:0a51 High Tech Computer Corp. SPV C400 / T-Mobile SDA GSM/GPRS Pocket PC
Bus 002 Device 001: ID 0000:0000 
Bus 001 Device 001: ID 0000:0000
```

You are very kind to pray attention (I'm sorry for my English,I write from Italy)
I'm waiting for your answers,regards,Marco..

---

### Post by ueghio on 2009-01-13
Does anybody have suggestion?

---

