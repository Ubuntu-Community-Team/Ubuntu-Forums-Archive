---
title: "USB Drive won't mount on USB2 but will on USB1.1"
date: 2008-08-30
forum: Hardware
---

### Post by flick152 on 2008-08-30
Hi all, little usb problem...

I can plug my usb drive into my USB1.1 port and it automounts no problem but it won't automount on USB 2.0 and I can't mount it manually. I have a card reader connected to the same USB 2.0 controller and that works no problem

lspci | grep USB```
root@griffie:/media# lspci | grep USB
00:0e.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:0e.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:0e.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51)
00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
```

lsusb (drive in USB1.1)```
root@griffie:/media# lsusb
Bus 005 Device 003: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 004: ID 067b:2507 Prolific Technology, Inc. PL2507 Hi-speed USB to IDE bridge controller
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 007: ID 0518:0001 EzKEY Corp. USB to PS2 Adaptor v1.09
Bus 003 Device 004: ID 09da:0006 A4 Tech Co., Ltd Optical Mouse WOP-35 / Trust 450L Optical Mouse
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 03f0:0304 Hewlett-Packard DeskJet 810c/812c
Bus 001 Device 001: ID 0000:0000  

```

lsusb (drive in USB2.0)```
root@griffie:/media# lsusb
Bus 005 Device 033: ID 067b:2507 Prolific Technology, Inc. PL2507 Hi-speed USB to IDE bridge controller
Bus 005 Device 032: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 007: ID 0518:0001 EzKEY Corp. USB to PS2 Adaptor v1.09
Bus 003 Device 004: ID 09da:0006 A4 Tech Co., Ltd Optical Mouse WOP-35 / Trust 450L Optical Mouse
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 03f0:0304 Hewlett-Packard DeskJet 810c/812c
Bus 001 Device 001: ID 0000:0000  
root@griffie:/media# 

```

These errors pop-up in ttys when I plug into usb2```
david@griffie:~$
[693789.139107] sd 201:0:0:0: [sdg] Assuming drive cache: write through
[693789.142135] sd 201:0:0:0: [sdg] Assuming drive cache: write through
[693789.389074] Buffer I/O error on device sdg, logical block 0
[693789.389127] Buffer I/O error on device sdg, logical block 1
[693789.389174] Buffer I/O error on device sdg, logical block 2
[693789.389221] Buffer I/O error on device sdg, logical block 3
[693789.389267] Buffer I/O error on device sdg, logical block 4
[693789.389313] Buffer I/O error on device sdg, logical block 5
[693789.389361] Buffer I/O error on device sdg, logical block 6
[693789.389407] Buffer I/O error on device sdg, logical block 7
[693789.389521] Buffer I/O error on device sdg, logical block 0
[693789.389576] Buffer I/O error on device sdg, logical block 1
[693789.389752] ldm_validate_partition_table(): Disk read failed.
sudo screendump >> USBDiskError.txt
```

many thanks for any help

---

### Post by flick152 on 2008-08-30
Little extra info

Plugging in other devices work however such as a mouse works fine

pluggin in an external card reader doesn't work (this is a internal USB card-reader uses a double internal USB connection one for card reader the other for front usb)

(i'll try rebooting with drive plugged in now)

---

### Post by flick152 on 2008-08-30
Tried booting with drive attached to usb2.0 it seemed to work booted into gnome with EXTERNAL on the desktop double clicked....

```
"EXTERNAL" couldn't be found. Perhaps it has recently been deleted.
```

Later pop-up:
```
Unable to mount the volume 'EXTERNAL'
Details
mount: /dev/sdg1 is not a valid block device
```

---

### Post by flick152 on 2008-09-05
bump and some more info.

I can plug a USB1.1 thumbdrive into my USB2 and it'll automount no problem.

---

### Post by flick152 on 2009-02-10
Turns out to be a hardware issue (non usb 2 compliant cable - cheap 2.5" hdd enclosure)

---

