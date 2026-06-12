---
title: "usb devices not working when printer turned on"
date: 2008-10-04
forum: Hardware
---

### Post by lastavim on 2008-10-04
Hello,

I have problem with Ubuntu desktop computer. The computer has installed an USB printer and scanner (HP LaserJet M1005) which work correctly. The problem is that no pendrives (or external USB hard drives) are detected when this printer is turned on. When the printer is unpluged the USB devices are working correctly. 

If I have a pendrive mounted and then I connect the printer, the pendrive will be disconnected.

Maybe I will attach something from /var/log/messages


No USB devices are connected at this moment, I'm connecting pendrive:

```
Oct  4 18:58:53 gabinet kernel: [ 3113.348778] usb 4-4: new high speed USB device using ehci_hcd and address 57
Oct  4 18:58:54 gabinet kernel: [ 3113.492938] usb 4-4: configuration #1 chosen from 1 choice
Oct  4 18:58:54 gabinet kernel: [ 3113.574655] scsi7 : SCSI emulation for USB Mass Storage devices
Oct  4 18:58:59 gabinet kernel: [ 3118.611524] scsi 7:0:0:0: Direct-Access     Kingston DataTraveler 2.0 5.00 PQ: 0 ANSI: 0 CCS
Oct  4 18:58:59 gabinet kernel: [ 3118.853188] sd 7:0:0:0: [sdb] 7830528 512-byte hardware sectors (4009 MB)
Oct  4 18:58:59 gabinet kernel: [ 3118.854826] sd 7:0:0:0: [sdb] Write Protect is off
Oct  4 18:58:59 gabinet kernel: [ 3118.859648] sd 7:0:0:0: [sdb] 7830528 512-byte hardware sectors (4009 MB)
Oct  4 18:58:59 gabinet kernel: [ 3118.860810] sd 7:0:0:0: [sdb] Write Protect is off
Oct  4 18:58:59 gabinet kernel: [ 3118.860837]  sdb: sdb1
Oct  4 18:58:59 gabinet kernel: [ 3118.905024] sd 7:0:0:0: [sdb] Attached SCSI removable disk
Oct  4 18:58:59 gabinet kernel: [ 3118.905112] sd 7:0:0:0: Attached scsi generic sg3 type 0
```

Pen drive mounted, now I'm turning on the printer:

```
Oct  4 18:59:41 gabinet kernel: [ 3160.618204] usb 4-1: new high speed USB device using ehci_hcd and address 58
Oct  4 18:59:41 gabinet kernel: [ 3160.751278] usb 4-1: configuration #1 chosen from 1 choice
Oct  4 18:59:41 gabinet kernel: [ 3160.762067] usblp0: USB Bidirectional printer dev 58 if 1 alt 0 proto 2 vid 0x03F0 pid 0x3B17
Oct  4 18:59:42 gabinet kernel: [ 3161.516728] usb 4-4: reset high speed USB device using ehci_hcd and address 57
Oct  4 18:59:42 gabinet kernel: [ 3162.059823] usb 4-4: reset high speed USB device using ehci_hcd and address 57
Oct  4 18:59:43 gabinet kernel: [ 3162.602905] usb 4-4: reset high speed USB device using ehci_hcd and address 57
Oct  4 18:59:43 gabinet kernel: [ 3163.122067] usb 4-4: reset high speed USB device using ehci_hcd and address 57
Oct  4 18:59:44 gabinet kernel: [ 3163.529600] usb 4-4: USB disconnect, address 57
Oct  4 18:59:44 gabinet kernel: [ 3163.538331] sd 7:0:0:0: [sdb] READ CAPACITY failed
Oct  4 18:59:44 gabinet kernel: [ 3163.538339] sd 7:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Oct  4 18:59:44 gabinet kernel: [ 3163.538345] sd 7:0:0:0: [sdb] Sense not available.
Oct  4 18:59:44 gabinet kernel: [ 3163.538375] sd 7:0:0:0: [sdb] Write Protect is off
Oct  4 18:59:44 gabinet kernel: [ 3163.542591] sd 7:0:0:0: [sdb] READ CAPACITY failed
Oct  4 18:59:44 gabinet kernel: [ 3163.542602] sd 7:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Oct  4 18:59:44 gabinet kernel: [ 3163.542608] sd 7:0:0:0: [sdb] Sense not available.
Oct  4 18:59:44 gabinet kernel: [ 3163.542640] sd 7:0:0:0: [sdb] Write Protect is off
Oct  4 18:59:44 gabinet kernel: [ 3163.657186] usb 4-4: new high speed USB device using ehci_hcd and address 59
Oct  4 18:59:44 gabinet kernel: [ 3164.212263] usb 4-4: new high speed USB device using ehci_hcd and address 60
Oct  4 18:59:45 gabinet kernel: [ 3164.755350] usb 4-4: new high speed USB device using ehci_hcd and address 61
Oct  4 18:59:45 gabinet kernel: [ 3165.278456] usb 4-4: new high speed USB device using ehci_hcd and address 62
```

Printer turned on, but we have lost pendrive...
I will disconnect and connect USB pendrive again:
```

Oct  4 19:00:41 gabinet kernel: [ 3220.750299] usb 4-4: new high speed USB device using ehci_hcd and address 63
Oct  4 19:00:41 gabinet kernel: [ 3221.293368] usb 4-4: new high speed USB device using ehci_hcd and address 64
Oct  4 19:00:42 gabinet kernel: [ 3221.836462] usb 4-4: new high speed USB device using ehci_hcd and address 65
Oct  4 19:00:43 gabinet kernel: [ 3222.355598] usb 4-4: new high speed USB device using ehci_hcd and address 66
```

Nothing happens...



Do you have any ideas? Please help :)

Regards,

---

