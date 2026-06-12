---
title: "China MP4 Player 4GB not mounting in Ubuntu??? but in"
date: 2008-06-06
forum: Hardware
---

### Post by ridshack on 2008-06-06
Hi all,

I got this MP4 player from China that mounts as drive under windows but not in 8.04 Ubuntu. 

I need help understanding how to troubleshoot this type of issue.

an **lsusb** and got:

> Bus 003 Device 010: ID 05cb:1483 PowerVision Technologies, Inc. PV8630 interface (scanners, webcams)
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
Bus 001 Device 001: ID 0000:0000  


I **dmesg** and got:

> [91277.605329] usb 3-3: new high speed USB device using ehci_hcd and address 8
[91277.738306] usb 3-3: configuration #1 chosen from 1 choice
[91277.780020] scsi5 : SCSI emulation for USB Mass Storage devices
[91277.789495] usb-storage: device found at 8
[91277.789503] usb-storage: waiting for device to settle before scanning
[91282.787997] usb-storage: device scan complete
[91282.788978] scsi 5:0:0:0: Direct-Access     RockChip USBDISK  User    1.00 PQ: 0 ANSI: 0 CCS
[91282.789991] scsi 5:0:0:1: Direct-Access     RockChip USBDISK    SD    1.00 PQ: 0 ANSI: 0 CCS
[91282.796494] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[91282.796570] sd 5:0:0:0: Attached scsi generic sg2 type 0
[91282.804143] sd 5:0:0:1: [sdc] Attached SCSI removable disk
[91282.804221] sd 5:0:0:1: Attached scsi generic sg3 type 0
[91283.286716] sd 5:0:0:0: [sdb] 7944192 512-byte hardware sectors (4067 MB)
[91283.399631] usb 3-3: reset high speed USB device using ehci_hcd and address 8
[40554.826213] usb 3-3: reset high speed USB device using ehci_hcd and address 8
[40555.070044] usb 3-3: reset high speed USB device using ehci_hcd and address 8
[40555.313874] usb 3-3: reset high speed USB device using ehci_hcd and address 8
[40555.557711] usb 3-3: reset high speed USB device using ehci_hcd and address 8
[40555.801537] usb 3-3: reset high speed USB device using ehci_hcd and address 8
[91286.301210] sd 5:0:0:0: [sdb] Write Protect is off
[91286.301219] sd 5:0:0:0: [sdb] Mode Sense: 03 00 00 00
[91286.301225] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[91286.306332] sd 5:0:0:0: [sdb] 7944192 512-byte hardware sectors (4067 MB)
[91286.416664] usb 3-3: reset high speed USB device using ehci_hcd and address 8
[91286.660592] usb 3-3: reset high speed USB device using ehci_hcd and address 8
[91286.904520] usb 3-3: reset high speed USB device using ehci_hcd and address 8
[91287.148446] usb 3-3: reset high speed USB device using ehci_hcd and address 8
[91287.392375] usb 3-3: reset high speed USB device using ehci_hcd and address 8
[91287.636302] usb 3-3: reset high speed USB device using ehci_hcd and address 8
[91287.768751] sd 5:0:0:0: [sdb] Write Protect is off
[91287.768761] sd 5:0:0:0: [sdb] Mode Sense: 03 00 00 00
[91287.768767] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[91287.768776]  sdb:<6>usb 3-3: reset high speed USB device using ehci_hcd and address 8


---

### Post by ridshack on 2008-06-07
Update: I found the MP4 player is using a new chipset Rockchip RK2706. It hasnt been out for a matter of months now. And I also found that my player is a pre-OEM Ramos RM970. Which BTW is fantastic.

---

