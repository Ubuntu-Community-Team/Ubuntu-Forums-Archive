---
title: "printing with parallel printer through lpt-&gt;usb cabel"
date: 2009-01-08
forum: Hardware
---

### Post by pavel.fibich on 2009-01-08
Hello,

I am using parallel printer HP LJ 2100 connected to usb port through reduction cabel LPT->USB. Printer is recognized by HAL but do not print.

* working with ubuntu 8.10 with gnome,  2.6.27-9 kernel, cups 1.3.9
* lsusb
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 090c:1000 Feiya Technology Corp. Memory Bar
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 003: ID 1a86:7584  
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
* lpinfo -v
network socket
network beh
direct hpfax
direct hp
network http
network ipp
network lpd
network socket://160.217.214.5
direct scsi
serial serial:/dev/ttyS0?baud=115200
direct hal:///org/freedesktop/Hal/devices/usb_device_1a86_7584_noserial_if0_printer_noserial
network smb
* sudo usb_printerid /dev/usb/lp0
GET_DEVICE_ID string: __there are some unreadable characters in 8 lines __

I added printer with System->Administration->Printing with device uri
  parallel:/dev/usb/lp0
or with 
  hal:///org/freedesktop/Hal/devices/usb_device_1a86_7584_noserial_if0_printer_noserial

Any of choices works.

Have you any ideas how to print?
  
I have the same problem on another computer with older ubuntu see [http://ubuntuforums.org/showthread.php?p=5754757]("http://ubuntuforums.org/showthread.php?p=5754757")

Pavel Fibich

---

### Post by pisapisa on 2012-08-23
sdfg

---

