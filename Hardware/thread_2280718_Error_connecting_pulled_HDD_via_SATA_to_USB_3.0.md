---
title: "Error connecting pulled HDD via SATA to USB 3.0"
date: 2015-06-01
forum: Hardware
---

### Post by Triangular_Syntax on 2015-06-01
Hello,

    I have removed a brand new 500 GB Toshiba HDD (with Ubuntu 15.04 installed) from my computer after replacing it with an SSD. I bought a SATA to USB 3.0 cable and I am trying to mount the drive so that I can format it for sale. However, when I plug the drive in I do not getting any kind of spinning or noise suggesting that the drive is powered; though, the SATA to USB 3.0 cable is lighting up as if it is getting power. 

Because I was only going to use the cable once, I bought one of the cheaper cables from eBay (shipped from China), so there is always the chance that the cable is defective. I have attached the dmesg log correlating to the error. Any help is appreciated.

Best regards,
T.S.

---


> [ 8369.969394] usb 2-1: new SuperSpeed USB device number 2 using xhci_hcd
[ 8369.987643] usb 2-1: New USB device found, idVendor=152d, idProduct=0567
[ 8369.987654] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 8369.987660] usb 2-1: Product: USB to ATA/ATAPI Bridge
[ 8369.987665] usb 2-1: Manufacturer: JMicron
[ 8369.987670] usb 2-1: SerialNumber: D310513071200028
[ 8370.028090] usbcore: registered new interface driver usb-storage
[ 8370.045642] scsi host2: uas
[ 8370.049411] scsi 2:0:0:0: Direct-Access     JMicron  Generic          0116 PQ: 0 ANSI: 6
[ 8370.050112] usbcore: registered new interface driver uas
[ 8370.050649] sd 2:0:0:0: Attached scsi generic sg2 type 0
[ 8370.051003] sd 2:0:0:0: [sdb] Spinning up disk...
[ 8371.053951] ........................
[ 8425.114246] sd 2:0:0:0: uas_eh_abort_handler 0 uas-tag 1 inflight: CMD 
[ 8425.114256] sd 2:0:0:0: CDB: 
[ 8425.114261] Test Unit Ready: 00 00 00 00 00 00
[ 8425.114301] scsi host2: uas_eh_bus_reset_handler start
[ 8425.227200] usb 2-1: reset SuperSpeed USB device number 2 using xhci_hcd
[ 8425.244103] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800ad644800
[ 8425.244114] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800ad644848
[ 8425.244120] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800ad644890
[ 8425.244125] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800ad6448d8
[ 8425.245574] scsi host2: uas_eh_bus_reset_handler success
[ 8435.249090] sd 2:0:0:0: uas_eh_abort_handler 0 uas-tag 1 inflight: CMD 
[ 8435.249100] sd 2:0:0:0: CDB: 
[ 8435.249105] Test Unit Ready: 00 00 00 00 00 00
[ 8435.249121] scsi host2: uas_eh_bus_reset_handler start
[ 8435.361372] usb 2-1: reset SuperSpeed USB device number 2 using xhci_hcd
[ 8435.378249] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800ad644800
[ 8435.378260] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800ad644848
[ 8435.378266] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800ad644890
[ 8435.378272] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800ad6448d8
[ 8435.379476] scsi host2: uas_eh_bus_reset_handler success
[ 8435.379489] sd 2:0:0:0: Device offlined - not ready after error recovery
[ 8435.379525] ready
[ 8435.379548] sd 2:0:0:0: rejecting I/O to offline device
[ 8435.379570] sd 2:0:0:0: rejecting I/O to offline device
[ 8435.379586] sd 2:0:0:0: rejecting I/O to offline device
[ 8435.379599] sd 2:0:0:0: [sdb] Read Capacity(16) failed: Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[ 8435.379605] sd 2:0:0:0: [sdb] Sense not available.
[ 8435.379616] sd 2:0:0:0: rejecting I/O to offline device
[ 8435.379631] sd 2:0:0:0: rejecting I/O to offline device
[ 8435.379646] sd 2:0:0:0: rejecting I/O to offline device
[ 8435.379657] sd 2:0:0:0: [sdb] Read Capacity(10) failed: Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[ 8435.379662] sd 2:0:0:0: [sdb] Sense not available.
[ 8435.379674] sd 2:0:0:0: rejecting I/O to offline device
[ 8435.379689] sd 2:0:0:0: rejecting I/O to offline device
[ 8435.379706] sd 2:0:0:0: rejecting I/O to offline device
[ 8435.379717] sd 2:0:0:0: [sdb] Write Protect is off
[ 8435.379724] sd 2:0:0:0: [sdb] Mode Sense: 00 00 00 00
[ 8435.379736] sd 2:0:0:0: rejecting I/O to offline device
[ 8435.379746] sd 2:0:0:0: [sdb] Asking for cache data failed
[ 8435.379751] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 8435.379762] sd 2:0:0:0: rejecting I/O to offline device
[ 8435.381121] sd 2:0:0:0: [sdb] Attached SCSI disk


---

### Post by NoWayWin8 on 2015-06-02
> **Triangular_Syntax said:**
> I do not getting any kind of spinning or noise suggesting that the drive is powered;

Is the drive's power connector plugged in? Sounds like it isn't.

---

### Post by oldfred on 2015-06-02
Some USB ports do not put out enough power for a Hard drive, particularly laptops.
You may need separate power.

Do not go too cheap on a drive caddy. We have seen posts where some do not work with USB3, some do not work with drives over 2TB and other issues. 
And best to have another drive for backup anyway.

---

### Post by Triangular_Syntax on 2015-06-02
[ATTACH=CONFIG]262364[/ATTACH][ATTACH=CONFIG]262365[/ATTACH]
The SATA connector covers up the two (power connector?) pins with a plastic tab. _However, the drive, when connected internally to my desktop didn't have a connector for those two pins either_, just the SATA. Perhaps the internal SATA outputs more power, but again, the seller claimed that USB 3.0 would be enough to power the HDD. I have an HP All-In-One, so I'm not sure if that outputs the correct amount or not. Also, my main backup drive is an SSD. I am just trying to access this one so that I can wipe and sell it.

I could just take the computer apart again, reconnect it internally and wipe it with Ubuntu Live USB and GParted, but that would take away the convenience of using a SATA to USB. :-?

---

### Post by Triangular_Syntax on 2015-06-04
The cause was an error on my part. I tested another HDD (2.5") and it powered on and mounted fine, however, the HDD that I was trying to mount was a 3.5" and apparently needed more power. So, the suggestions by NoWayWin8 and oldfred were correct. Thank you two.

Regards,
T.S.

---

