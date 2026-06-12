---
title: "can't call usb device using lsusb -s XXX:YYY"
date: 2009-01-27
forum: Hardware
---

### Post by MatMan on 2009-01-27
Hi,

this is part of an attempt to mount an (HPFS?) NTFS external USB SATA hdd 320Gb to Intrepid on an HP laptop.

mat@mat-laptop:~$ lsusb
Bus 007 Device 008: ID 152d:2338 JMicron Technology Corp. / JMicron USA Technology Corp. JM20337 Hi-Speed USB to SATA & PATA Combo Bridge
Bus 007 Device 003: ID 04f2:b016 Chicony Electronics Co., Ltd 
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
mat@mat-laptop:~$ lsusb -s 007:008
mat@mat-laptop:~$ lsusb -s 007:003
Bus 007 Device 003: ID 04f2:b016 Chicony Electronics Co., Ltd 
mat@mat-laptop:~$ lsusb -s 006:002
Bus 006 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
mat@mat-laptop:~$ 

note when I call lsusb -s 007:008 no device is returned, but devices are returned for other bus:dev. I can't figure out why.

I have been trying to mount it using fstat, but with no success. 

/dev/sdb and /dev/sdb1 exist, but it refuses to mount. See below if you like:


root@mat-laptop:~# mount -t ntfs /dev/sdb1 /media/usbhdd
NTFS signature is missing.
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
root@mat-laptop:~# mount -t ntfs /dev/sdb /media/usbhdd
NTFS signature is missing.
Failed to mount '/dev/sdb': Invalid argument
The device '/dev/sdb' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
root@mat-laptop:~# mount -t vfat /dev/sdb /media/usbhdd
mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


so in conclusion, I can't access files on my external hdd.

the main questions are:
1. why does lsusb -s 007:008 not return a device?
2. am i going about mounting the wrong way? How embarrassing. it may be as simple as how do i mount an external hdd with data written by windows?

cheers,

matman

---

