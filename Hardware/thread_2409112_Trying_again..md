---
title: "Trying again."
date: 2018-12-27
forum: Hardware
---

### Post by hmorgan1979 on 2018-12-27
I tried to get assistance before and it seems as though the request, after a bit of back ad forth, never got resolved, so here goes:  I have a Toshiba 2TB external hard drive, and an Acer Aspire laptop.  I am currently running Ubuntu Studio 18.10.  My problem runs thusly:  about three months or so ago, everything was fine.  My external hd was working fine with my laptop.  One evening I had unplugged the hd from the laptop because I was going somewhere.  I returned the next day and hooked everything back up.  My hd doesn't show up on my desktop or in the device list.  I have tried with a different usb cable and still nothing.  I ran lsusb and the results are below:

herman@InfernusMaximus666:~$ lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 8087:07dc Intel Corp. 
Bus 001 Device 004: ID 064e:9404 Suyin Corp. 
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 009: ID 0480:d011 Toshiba America Inc Canvio Desk
Bus 001 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


The Toshiba Canvio is the external HD.

Then I unplugged it, plugged it back in and ran  dmesg | tail -n 20.  again, results are below.
$ dmesg | tail -n 20
[ 6933.254573] sd 0:0:0:0: [sda] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 6933.254577] sd 0:0:0:0: [sda] tag#0 Sense Key : Illegal Request [current] 
[ 6933.254580] sd 0:0:0:0: [sda] tag#0 Add. Sense: Invalid field in cdb
[ 6933.254585] sd 0:0:0:0: [sda] tag#0 CDB: Read(16) 88 00 00 00 00 00 00 00 00 04 00 00 00 04 00 00
[ 6933.254587] print_req_error: critical target error, dev sda, sector 4
[ 6933.254593] Buffer I/O error on dev sda, logical block 1, async page read
[ 6933.257004] Dev sda: unable to read RDB block 0
[ 6933.265591]  sda: unable to read partition table
[ 6933.268030] sd 0:0:0:0: [sda] Attached SCSI disk
[ 6963.946893] usb 1-2: USB disconnect, device number 11
[ 6963.950714] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[ 6963.950800] sd 0:0:0:0: [sda] Synchronize Cache(10) failed: Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[ 6969.104671] usb 1-2: new high-speed USB device number 12 using xhci_hcd
[ 6969.234979] usb 1-2: New USB device found, idVendor=0480, idProduct=d011, bcdDevice= 3.16
[ 6969.234983] usb 1-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 6969.234985] usb 1-2: Product: External USB 3.0
[ 6969.234987] usb 1-2: Manufacturer: TOSHIBA
[ 6969.234989] usb 1-2: SerialNumber: 20140831110664
[ 6969.238627] usb-storage 1-2:1.0: USB Mass Storage device detected
[ 6969.242967] scsi host0: usb-storage 1-2:1.0


Again, the Toshiba shows up. This is where everything stands at this point.
Any help would be greatly appreciated.

---

### Post by wildmanne39 on 2018-12-27
Please use your other thread here:

[https://ubuntuforums.org/showthread.php?t=2401868](https://ubuntuforums.org/showthread.php?t=2401868)

If you do not get a reply after twelve hours of your last post you can bump your post to get it on sight of the volunteers.

---

