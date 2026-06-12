---
title: "HAL wrong detects parallel HP 2100 on USB port"
date: 2008-09-09
forum: Hardware
---

### Post by pavel.fibich on 2008-09-09
Hello,

I am connecting parallel printer HP LJ 2100 to USB port with cabel reduction. Using Printing form Gnome menu, I find printer connected through HAL (see bellow). Cups uses printer on Unknown device. When start printing some job, printer start reading file (start blink), but let it be (stop blink) without printing job OR print blank papers. Cups shows status for printer:
"Unable to send print file to printer: Input/output error"

I am using HP-LaserJet_2100-pxlmono.ppd

I was trying to test cabel reduction on another pc with win xp and work well.

Scenario:

lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 1a86:7584  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 0458:0036 KYE Systems Corp. (Mouse Systems) 
Bus 001 Device 001: ID 0000:0000

lpinfo -v
network socket
network beh
direct hpfax
direct hp
network http
network ipp
network lpd
direct scsi
direct hal:///org/freedesktop/Hal/devices/usb_device_1a86_7584_noserial_if0_printer_noserial
network smb

tail of dmesg after connecting
[  727.366696] usb 2-2: new full speed USB device using uhci_hcd and address 3
[  727.441675] usb 2-2: configuration #1 chosen from 1 choice
[  727.491553] usblp0: USB Bidirectional printer dev 3 if 0 alt 0 proto 2 vid 0x1A86 pid 0x7584

sudo usb_printerid /dev/usb/lp0
GET_DEVICE_ID string:
... here are some unreadable characters ...

Have you any ideas how to solve this problem? I am trying it for a long time but have no results.

Working on Ubuntu 8.04, Cups 1.3.8.

Pavel

---

### Post by pavel.fibich on 2008-09-11
I try to add new printer with cups using URI: "parallel:/dev/usb/lp0" and it do not help. Again printer start blink, but do not print for a long time anything.
I think there is problem with printer_id that is not correctly recognized. But how to solve it?

---

