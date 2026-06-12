---
title: "ubunt 8.04 rc webcam"
date: 2008-04-20
forum: Hardware &amp; Laptops
---

### Post by lavinia on 2008-04-20
Hello all. i download ubuntu 8.04 after installed to my laptop. Perfect OS. i love you linux-ubuntu. :)
i have a problem. My webcam does not work  on laptop. 
here my details:

lavinya@lavinya-laptop:~$ hwinfo --usb
...
07: USB 00.0: 0000 Unclassified device
  [Created at usb.122]
  UDI: /org/freedesktop/Hal/devices/usb_device_402_5602_noserial_if0
  Unique ID: Q1jS.qSFQ6Cc6sG8
  Parent ID: 7eqy.m_1kmihIEZE
  SysFS ID: /devices/pci0000:00/0000:00:1a.7/usb6/6-3/6-3:1.0
  SysFS BusID: 6-3:1.0
  Hardware Class: unknown
  Model: "Acer USB2.0 Camera"
  Hotplug: USB
  Vendor: usb 0x0402 "Acer Labs Inc."
  Device: usb 0x5602 "USB2.0 Camera"
  Revision: "1.00"
  Speed: 480 Mbps
  Module Alias: "usb:v0402p5602d0100dc00dsc00dp00icFFiscFFipFF"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #9 (Hub)
...
----

lavinya@lavinya-laptop:~$ lsusb
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 0402:5602 ALi Corp. Video Camera Controller
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 15ca:00c3  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 004: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

Please help me.

---

### Post by linuxwizard on 2008-05-07
Your webcam > Bus 006 Device 002: ID 0402:5602 ALi Corp. Video Camera Controller > is not supported in Linux. You never know maybe in future their will be a driver for it. Good Luck

---

### Post by lavinia on 2008-05-08
Hm... :(

Ok thanks for reply: linuxwizard

---

### Post by Len_C on 2008-05-11
0402:5602 ALi Corp. Video Camera Controller: A driver is currently in development. 

Have a look at [http://www.linuxlaptopwiki.net/wiki/ALi_Corp_M5602](http://www.linuxlaptopwiki.net/wiki/ALi_Corp_M5602) and [https://sourceforge.net/projects/m560x-driver/](https://sourceforge.net/projects/m560x-driver/)

Installation guides: 
[http://atlas.hasselbalch.com/znote6625wd/](http://atlas.hasselbalch.com/znote6625wd/)  (english)
[http://forum.ubuntu-fr.org/viewtopic.php?pid=1739308#p1739308](http://forum.ubuntu-fr.org/viewtopic.php?pid=1739308#p1739308) (french)
[http://www.amilo-forum.de/topic,23311,-Amilo-Xi-2528-Ubuntu-8-04-Kopfhoerer-und-oder-Lautsprecher.html#151564](http://www.amilo-forum.de/topic,23311,-Amilo-Xi-2528-Ubuntu-8-04-Kopfhoerer-und-oder-Lautsprecher.html#151564) (german)

Before beginning the installation procedure you must run

sudo apt-get install build-essential linux-headers-$(uname -r) subversion

---

