---
title: "unable to mount mp4 player teclast/nationite"
date: 2008-08-10
forum: Hardware
---

### Post by rwabel on 2008-08-10
I've purchased a mp4 player from nationite, also called teclast. When pluging it to USB it shortly shows me usb connect and then it doesn't mount. below is the output

> 1673.449121] usb 5-1: new high speed USB device using ehci_hcd and address 5
[ 1673.580790] usb 5-1: configuration #1 chosen from 1 choice
[ 1673.582321] scsi3 : SCSI emulation for USB Mass Storage devices
[ 1673.582938] usb-storage: device found at 5
[ 1673.582944] usb-storage: waiting for device to settle before scanning
[ 1678.575286] usb-storage: device scan complete
[ 1678.575880] scsi 3:0:0:0: Direct-Access S:FLO - M29 USBDISK 1.00 PQ: 0 ANSI: 0
[ 1678.577494] sd 3:0:0:0: [sdb] 15960064 512-byte hardware sectors (8172 MB)
[ 1678.632309] usb 5-1: USB disconnect, address 5
[ 1680.731236] sd 3:0:0:0: [sdb] Write Protect is off
[ 1680.731241] sd 3:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 1680.731244] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 1680.731452] sd 3:0:0:0: [sdb] READ CAPACITY failed
[ 1680.731455] sd 3:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 1680.731461] sd 3:0:0:0: [sdb] Sense not available.
[ 1680.731495] sd 3:0:0:0: [sdb] Write Protect is off
[ 1680.731499] sd 3:0:0:0: [sdb] Mode Sense: 00 00 00 00
[ 1680.731501] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 1680.731664] sd 3:0:0:0: [sdb] READ CAPACITY failed
[ 1680.731667] sd 3:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 1680.731674] sd 3:0:0:0: [sdb] Sense not available.
[ 1680.731707] sd 3:0:0:0: [sdb] Write Protect is off
[ 1680.731711] sd 3:0:0:0: [sdb] Mode Sense: 00 00 00 00
[ 1680.731713] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 1680.731784] sd 3:0:0:0: [sdb] Attached SCSI removable disk
[ 1680.731838] sd 3:0:0:0: Attached scsi generic sg2 type 0

rwabel@ubuntu:~/Desktop/$ lsusb
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 008: ID 0a5c:4503 Broadcom Corp.
Bus 004 Device 007: ID 0a5c:4502 Broadcom Corp.
Bus 004 Device 006: ID 413c:8126 Dell Computer Corp.
Bus 004 Device 002: ID 0a5c:4500 Broadcom Corp.
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 004: ID 046d:c03f Logitech, Inc. UltraX Optical Mouse
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

---

### Post by rwabel on 2008-09-21
same issue on ubuntu 8,10

---

### Post by simonjpo on 2010-11-02
I found this problem was closely related to Rhythmbox; sometimes the drive was detected and available to nautilus, sometimes it was detected and silently dropped.
With Rhythmbox open and playing, the interface froze, the music stopped and would not restart, the process went to sleep and had to be killed from System Monitor.

Similar things happened with Fedora 13.
The problem seems to have gone away now that I have disabled the Rhythmbox portable player plugins.
These are clearly broken(the same for iPod too).
Disable the plugins and you should get basic drag and drop in Nautilus.

---

