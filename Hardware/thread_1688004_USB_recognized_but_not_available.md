---
title: "USB recognized but not available?"
date: 2011-02-14
forum: Hardware
---

### Post by LepeKaname on 2011-02-14
I installed Ubuntu and I'm teaching my mother to use it. Everything is going fine except that her new [USB pendrive]("http://www.pqi.com.tw/product2.asp?oid=19&catE1=19&PROID=385") (8GB - fat32) is not working in Linux (but it works in Windows and Mac).

OS: Kubuntu Lucid kernel: 2.6.32-28-generic

Before and after "lsusb":

> root@desktop:/etc# lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

root@desktop:/etc# lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 3538:0901 Power Quotient International Co., Ltd
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

dmesg:
> 
[ 1061.544029] usb 3-1: new full speed USB device using uhci_hcd and address 2
[ 1061.709572] usb 3-1: configuration #1 chosen from 1 choice
[ 1061.744920] scsi5 : SCSI emulation for USB Mass Storage devices
[ 1061.752290] usb-storage: device found at 2
[ 1061.752297] usb-storage: waiting for device to settle before scanning
[ 1066.753954] usb-storage: device scan complete
[ 1066.756871] scsi 5:0:0:0: Direct-Access-RBC                   PQ: 2 ANSI: 4
[ 1066.763379] scsi 5:0:0:0: Attached scsi generic sg3 type 14

But in "fdisk -l" it is not shown, and not found under /media/:

root@desktop:/etc# fdisk -l

> Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x90789078

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7296    58605088+   7  Linux

fdisk -l /dev/sdb shows: "Unable to open /dev/sdb". As it does not exists.

What else can be done? any help is appreciated.

---

### Post by anglican on 2011-02-15
> **LepeKaname said:**
> I installed Ubuntu and I'm teaching my mother to use it. Everything is going fine except that her new [USB pendrive]("http://www.pqi.com.tw/product2.asp?oid=19&catE1=19&PROID=385") (8GB - fat32) is not working in Linux (but it works in Windows and Mac).

OS: Kubuntu Lucid kernel: 2.6.32-28-generic

Before and after "lsusb":



dmesg:


But in "fdisk -l" it is not shown, and not found under /media/:

root@desktop:/etc# fdisk -l



fdisk -l /dev/sdb shows: "Unable to open /dev/sdb". As it does not exists.

What else can be done? any help is appreciated.Try:
```
sudo apt-get install sg3-utils
sudo sg_map
```which should show the correct device name (if any).

H

---

### Post by LepeKaname on 2011-02-16
**dmesg**
> [    7.249406] scsi 2:0:0:0: Attached scsi generic sg3 type 14

**sg_map**

> /dev/sg0  /dev/sda
/dev/sg1  /dev/scd0
/dev/sg2  /dev/scd1
/dev/sg3

I also tried:
**sg_opcodes /dev/sg3**
> Peripheral device type: simplified direct access device

**sg_modes /dev/sg3**
> inquiry: pass through os error: No such device
/dev/sg3 doesn't respond to a SCSI INQUIRY

**sg_map26 /dev/sg3**
> sg device: /dev/sg3 does not match any other SCSI device

**sg_scan**> 
/dev/sg0: scsi0 channel=0 id=0 lun=0 [em]
/dev/sg1: scsi0 channel=0 id=1 lun=0 [em]
/dev/sg2: scsi1 channel=0 id=1 lun=0 [em]
/dev/sg3: scsi3 channel=0 id=0 lun=0 [em]

Useful?

---

### Post by anglican on 2011-02-16
> **LepeKaname said:**
> 

I also tried:

**sg_opcodes /dev/sg3**
> /dev/sg3

Useful?Not very - to you. This device is not being mapped to a SCSI device which means it cannot be used. Sorry.

H

---

