---
title: "cannot print after the last update (Ubuntu 10.04)"
date: 2013-04-09
forum: Hardware
---

### Post by kwstas on 2013-04-09
hey guys,

yesterday i had an update and after that i cannot print anything not even the test page.

it seems that the printer is correctly recognised and it gets the wake up signal as i push the print button but that's it.

i'm in 10.04 (2.6.32-46-generic)
gnome 2.30.2

XEROX 3100 MFP printer 


here is what i got from [https://wiki.ubuntu.com/DebuggingPrintingProblems](https://wiki.ubuntu.com/DebuggingPrintingProblems)

```
kwstas@kwstas-laptop:~$ lsmod | grep usb
usblp                  10481  0 
usbhid                 36110  0 
hid                    67288  1 usbhid
kwstas@kwstas-laptop:~$ tail -f /var/log/syslog
Apr  9 10:17:02 kwstas-laptop CRON[3189]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr  9 11:17:02 kwstas-laptop CRON[3331]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr  9 12:17:01 kwstas-laptop CRON[3511]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr  9 12:45:25 kwstas-laptop udev-configure-printer: remove /devices/pci0000:00/0000:00:1d.0/usb5/5-1
Apr  9 12:45:25 kwstas-laptop udev-configure-printer: URI of print queue: usb://XEROX/Phaser%203100MFP, normalized: xerox phaser 3100mfp
Apr  9 12:45:25 kwstas-laptop udev-configure-printer: URI of detected printer: usb://XEROX/Phaser%203100MFP, normalized: xerox phaser 3100mfp
Apr  9 12:45:25 kwstas-laptop udev-configure-printer: Queue ipp://localhost:631/printers/-Phaser-3100MFP has matching device URI
Apr  9 12:45:25 kwstas-laptop udev-configure-printer: Disabled printer ipp://localhost:631/printers/-Phaser-3100MFP as the corresponding device was unplugged or turned off
Apr  9 12:45:25 kwstas-laptop udev-configure-printer: URI of print queue: smb://andie-pc/Xerox%20Phaser%203100MFP, normalized: smb andie pc xerox phaser 3100mfp
Apr  9 12:45:25 kwstas-laptop udev-configure-printer: URI of detected printer: usb://XEROX/Phaser%203100MFP, normalized: xerox phaser 3100mfp
Apr  9 12:45:46 kwstas-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.0
Apr  9 12:45:46 kwstas-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb5/5-1
Apr  9 12:45:46 kwstas-laptop udev-configure-printer: Device vendor/product is 0924:3CEE
Apr  9 12:45:46 kwstas-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.0/usb/lp0
Apr  9 12:45:47 kwstas-laptop udev-configure-printer: failed to claim interface
Apr  9 12:45:47 kwstas-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Apr  9 12:45:47 kwstas-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb5/5-1
Apr  9 12:45:47 kwstas-laptop udev-configure-printer: MFG:XEROX MDL: Phaser 3100MFP SERN:- serial:L509077LE413885
Apr  9 12:45:50 kwstas-laptop udev-configure-printer: URI matches without serial number: usb://XEROX/Phaser%203100MFP
Apr  9 12:45:50 kwstas-laptop udev-configure-printer: No serial number URI matches so using those without
Apr  9 12:45:50 kwstas-laptop udev-configure-printer: Consider also queues with "/usb/lp0" or "/usblp0" in their URIs as matching
Apr  9 12:45:50 kwstas-laptop udev-configure-printer: URI of print queue: usb://XEROX/Phaser%203100MFP, normalized: xerox phaser 3100mfp
Apr  9 12:45:50 kwstas-laptop udev-configure-printer: URI of detected printer: usb://XEROX/Phaser%203100MFP, normalized: xerox phaser 3100mfp
Apr  9 12:45:50 kwstas-laptop udev-configure-printer: Queue ipp://localhost:631/printers/-Phaser-3100MFP has matching device URI
Apr  9 12:45:50 kwstas-laptop udev-configure-printer: Re-enabled printer ipp://localhost:631/printers/-Phaser-3100MFP
Apr  9 12:45:50 kwstas-laptop udev-configure-printer: URI of print queue: smb://andie-pc/Xerox%20Phaser%203100MFP, normalized: smb andie pc xerox phaser 3100mfp
Apr  9 12:45:50 kwstas-laptop udev-configure-printer: URI of detected printer: usb://XEROX/Phaser%203100MFP, normalized: xerox phaser 3100mfp
^C
kwstas@kwstas-laptop:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 045e:0083 Microsoft Corp. Basic Optical Mouse
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 0924:3cee Xerox 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 04f2:b160 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
kwstas@kwstas-laptop:~$ ls -l /dev/usb/lp* /dev/bus/usb/*/*
crw-rw-r-- 1 root vboxusers 189,   0 2013-04-09 00:08 /dev/bus/usb/001/001
crw-rw-r-- 1 root vboxusers 189, 128 2013-04-09 00:08 /dev/bus/usb/002/001
crw-rw-r-- 1 root vboxusers 189, 130 2013-04-09 00:08 /dev/bus/usb/002/003
crw-rw-r-- 1 root vboxusers 189, 256 2013-04-09 00:08 /dev/bus/usb/003/001
crw-rw-r-- 1 root vboxusers 189, 384 2013-04-09 00:08 /dev/bus/usb/004/001
crw-rw-r-- 1 root vboxusers 189, 512 2013-04-09 00:08 /dev/bus/usb/005/001
crw-rw-r-- 1 root lp        189, 514 2013-04-09 12:45 /dev/bus/usb/005/003
crw-rw-r-- 1 root vboxusers 189, 640 2013-04-09 00:08 /dev/bus/usb/006/001
crw-rw-r-- 1 root vboxusers 189, 641 2013-04-09 00:08 /dev/bus/usb/006/002
crw-rw-r-- 1 root vboxusers 189, 768 2013-04-09 00:08 /dev/bus/usb/007/001
crw-rw-r-- 1 root vboxusers 189, 896 2013-04-09 00:08 /dev/bus/usb/008/001
crw-rw---- 1 root lp        180,   0 2013-04-09 12:45 /dev/usb/lp0
kwstas@kwstas-laptop:~$ sudo usb_printerid /dev/usb/lp0 
[sudo] password for kwstas: 
GET_DEVICE_ID string:
MFG:XEROX;MDL: Phaser 3100MFP;CMD:AUTOMATIC,PJL,GDI_RL;DES:XEROX Phaser 3100MFP;CLS:PRINTER;VER:v2.07m  ;NS:L509077LE413885;
kwstas@kwstas-laptop:~$ sudo usb_printerid /dev/usb/lp1 
Error: No such file or directory: can't open '/dev/usb/lp1'
kwstas@kwstas-laptop:~$ lpinfo -v
direct scsi
network http
network ipp
network lpd
network socket
direct hp
direct usb://XEROX/Phaser%203100MFP
network smb
network beh
direct hpfax
kwstas@kwstas-laptop:~$ 

```

any help would be much appreciated guys

---

### Post by mörgæs on 2013-04-09
In stead of troubleshooting have you considered a fresh install of Buntu 12.10?
In a month you have to upgrade anyway.

---

