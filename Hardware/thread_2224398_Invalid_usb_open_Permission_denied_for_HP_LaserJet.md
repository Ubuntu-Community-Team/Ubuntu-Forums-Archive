---
title: "Invalid usb_open: Permission denied for HP LaserJet P1102"
date: 2014-05-16
forum: Hardware
---

### Post by standa2 on 2014-05-16
I have bought a new printer ''HP LaserJet P1102'' and it does not print on my Ubuntu 10.4.
I installed the latest version of hplip-3.14.4 driver and add printer in it. Everything seems ok, no any error.
Then I run Windows under Virtualbox and after installing drivers, the printer prints OK.

I made some tests with command ''hp-check'' - no errors.
Then print test page with ''hp-testpage''. The problem seems to be in usb permissions:

"D [15/May/2014:21:14:22 +0200] [Job 437] libusb couldn't open USB device /dev/bus/usb/001/003: Permission denied.",
'D [15/May/2014:21:14:22 +0200] [Job 437] libusb requires write access to USB device nodes.',
'D [15/May/2014:21:14:22 +0200] [Job 437] prnt/backend/hp.c 745: ERROR: open device failed stat=12: hp:/usb/HP_LaserJet_Professional_P1102?serial=000000000Q87N3P7PR1a',

Similar messages in /var/log/syslog:
May 14 23:46:48 guru hp[5529]: io/hpmud/musb.c 589: invalid usb_open: Permission denied
May 14 23:46:48 guru hp[5529]: io/hpmud/musb.c 1142: unable to open hp:/usb/HP_LaserJet_Professional_P1102?serial=000000000Q87N3P7PR1a

I have two USB ports:
$ ls -l /dev/bus/usb/001/
crw-rw-r--  1 root vboxusers 189, 0 2014-05-14 23:15 001
crw-rw-r--+ 1 root vboxusers 189, 3 2014-05-14 23:15 004

Printer is connected and recognised:
$ lsusb
Bus 002 Device 002: ID 04b3:3025 IBM Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 03f0:002a Hewlett-Packard 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I know it is somethinq with permissions, but I am not able to fix it. I try to change group name from 'lp' to 'vboxusers' in /etc/udev/rules.d/56-hpmud.rules but it didn't have any effext.
Please, help me. Thanks a lot.

---

### Post by Ubi_one_2014 on 2014-05-17
go to:
[http://127.0.0.1:631](http://127.0.0.1:631)
login, as root, and configure the printer form there.

if that does not work:
apt-get install cups

---

### Post by standa2 on 2014-05-18
I did it and still does not work.

[http://127.0.0.1:631/printers/HP-P1102:](http://127.0.0.1:631/printers/HP-P1102:)
[TABLE]
[TR]
[TH]Description:
[/TH]
[TD]HP-P1102[/TD]
[/TR]
[TR]
[TH]Location:[/TH]
[TD][/TD]
[/TR]
[TR]
[TH]Driver:[/TH]
[TD]HP LaserJet Professional p1102, hpcups 3.14.4, requires proprietary plugin (color)[/TD]
[/TR]
[TR]
[TH]Connection:[/TH]
[TD]hp:/usb/HP_LaserJet_Professional_P1102?serial=000000000Q87N3P7PR1a[/TD]
[/TR]
[TR]
[TH]Defaults:[/TH]
[TD]job-sheets=none, none media=iso_a4_210x297mm[/TD]
[/TR]
[/TABLE]

**Print Test page:**
held since
Sun May 18 21:48:01 2014 
*"/usr/lib/cups/backend/hp failed"*

---

### Post by standa2 on 2014-05-18
From /var/log/syslog:

kernel: [ 2282.420054] usb 1-3: new high speed USB device using ehci_hcd and address 3
kernel: [ 2282.553198] usb 1-3: configuration #1 chosen from 1 choice
logger: loading HP Device 001 003
udev-configure-printer: add /devices/pci0000:00/0000:00:02.1/usb1/1-3/1-3:1.0
udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:02.1/usb1/1-3
udev-configure-printer: Device vendor/product is 03F0:002A
udev-configure-printer: MFG:Hewlett-Packard MDL:HP LaserJet Professional P1102 SERN:- serial:000000000Q87N3P7PR1a
kernel: [ 2282.797616] usblp0: USB Bidirectional printer dev 3 if 0 alt 0 proto 2 vid 0x03F0 pid 0x002A
kernel: [ 2282.797656] usbcore: registered new interface driver usblp
udev-configure-printer: add /devices/pci0000:00/0000:00:02.1/usb1/1-3/1-3:1.0/usb/lp0
kernel: [ 2283.823441] usb 1-3: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
hp[3421]: io/hpmud/musb.c 2073: **Invalid usb_open: Permission denied**
udev-configure-printer: URI matches without serial number: usb://HP/LaserJet%20Professional%20P1102
udev-configure-printer: No serial number URI matches so using those without
udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:02.1/usb1/1-3
udev-configure-printer: URI of print queue: hp:/usb/HP_LaserJet_Professional_P1102?serial=000000000Q87N3P7PR1a, normalized: laserjet professional p1102 serial 000000000q87n3p7pr1a
guru udev-configure-printer: URI of detected printer: usb://HP/LaserJet%20Professional%20P1102, normalized: laserjet professional p1102
udev-configure-printer: Queue ipp://localhost:631/printers/HP-P1102 has matching device URI
udev-configure-printer: Re-enabled printer ipp://localhost:631/printers/HP-P1102
udev-configure-printer: URI of print queue: usb://HP/LaserJet%20Professional%20P1102?serial=000000000Q87N3P7PR1a, normalized: laserjet professional p1102 serial 000000000q87n3p7pr1a
udev-configure-printer: URI of detected printer: usb://HP/LaserJet%20Professional%20P1102, normalized: laserjet professional p1102
udev-configure-printer: Queue ipp://localhost:631/printers/HP_LaserJet_Professional_P1102 has matching device URI
udev-configure-printer: Re-enabled printer ipp://localhost:631/printers/HP_LaserJet_Professional_P1102

If I try print with HPLIB there is:

hp[3497]: io/hpmud/musb.c 589: **invalid usb_open: Permission denied**
hp[3497]: io/hpmud/musb.c 1142: unable to open hp:/usb/HP_LaserJet_Professional_P1102?serial=000000000Q87N3P7PR1a
hp[3497]: prnt/backend/hp.c 745: **ERROR: open device failed** stat=12: hp:/usb/HP_LaserJet_Professional_P1102?serial=000000000Q87N3P7PR1a

---

### Post by standa2 on 2014-05-20
The problem is solved. I update to the latest version of VirtualBox and remove old rule from /etc/udev/rules.d that I had copied there sometime when I needed sorted out a problem with the previous printer under VirtualBox. This caused the group is now set to **lp** and printer works. Originally there was a group *vboxusers* and it led to the problem **Invalid usb_open: Permission denied**.

ls -l /dev/bus/usb/001/
crw-rw-r--  1 root vboxusers 189, 0 2014-05-20 20:36 001
crw-rw-r--+ 1 root lp        189, 7 2014-05-20 22:25 008

Thank you to all participants who considered this problem and tried to find a solution.

---

