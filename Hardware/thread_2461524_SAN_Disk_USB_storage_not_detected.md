---
title: "SAN Disk USB storage not detected"
date: 2021-05-02
forum: Hardware
---

### Post by ttkkss11 on 2021-05-02
Just now the SANDisk USB storage stopped detecting on Ubuntu 20.04 desktop
dmsg shows 
[ 1846.928139] scsi 5:0:0:0: Direct-Access     SanDisk  Ultra            1.00 PQ: 0 ANSI: 6
[ 1846.929072] sd 5:0:0:0: Attached scsi generic sg4 type 0
[ 1846.929454] sd 5:0:0:0: [sdd] 240353280 512-byte logical blocks: (123 GB/115 GiB)
[ 1846.929908] sd 5:0:0:0: [sdd] Write Protect is off
[ 1846.929914] sd 5:0:0:0: [sdd] Mode Sense: 43 00 00 00
[ 1846.930334] sd 5:0:0:0: [sdd] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA

lsusb doesnot shows the device in the list
lspci doesnot shows the device in the list

---

### Post by ttkkss11 on 2021-05-02
[h=2][/h][COLOR=#000000][INDENT]earlier logs before malfunction
------------------------------------------------
[ 384.986452] usb 1-13.4: new high-speed USB device number 7 using xhci_hcd
[ 385.187328] usb 1-13.4: New USB device found, idVendor=0781, idProduct=558a, bcdDevice= 1.00
[ 385.187333] usb 1-13.4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 385.187337] usb 1-13.4: Product: Ultra
[ 385.187340] usb 1-13.4: Manufacturer: SanDisk
[ 385.187343] usb 1-13.4: SerialNumber: 0501614c8cdd1f3fab9f360778b4859750a62757247f03a1a3 e5221cdada221cea7f00000000000000000000593201530018 08108a55810717aabdcc
[ 385.189562] usb-storage 1-13.4:1.0: USB Mass Storage device detected
[ 385.190307] scsi host5: usb-storage 1-13.4:1.0
[ 386.200144] scsi 5:0:0:0: Direct-Access SanDisk Ultra 1.00 PQ: 0 ANSI: 6
[ 386.200387] sd 5:0:0:0: Attached scsi generic sg4 type 0
[ 386.200633] sd 5:0:0:0: [sdd] 240353280 512-byte logical blocks: (123 GB/115 GiB)
[ 386.200961] sd 5:0:0:0: [sdd] Write Protect is off
[ 386.200962] sd 5:0:0:0: [sdd] Mode Sense: 43 00 00 00
[ 386.201324] sd 5:0:0:0: [sdd] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[ 386.233531] sdd:

after malfunction
-----------------------------------------------------------
[ 386.234971] sd 5:0:0:0: [sdd] Attached SCSI removable disk
[ 395.639426] sdd:
[ 395.683201] sd 5:0:0:0: [sdd] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE cmd_age=0s
[ 395.683203] sd 5:0:0:0: [sdd] tag#0 Sense Key : Not Ready [current]
[ 395.683204] sd 5:0:0:0: [sdd] tag#0 Add. Sense: Medium not present
[ 395.683205] sd 5:0:0:0: [sdd] tag#0 CDB: Read(10) 28 00 0e 53 7c 70 00 00 08 00
[ 395.683207] blk_update_request: I/O error, dev sdd, sector 240352368 op 0x0:sad:READ) flags 0x80700 phys_seg 1 prio class 0
[ 395.883376] sd 5:0:0:0: [sdd] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE cmd_age=0s
[ 395.883378] sd 5:0:0:0: [sdd] tag#0 Sense Key : Not Ready [current]
[ 395.883379] sd 5:0:0:0: [sdd] tag#0 Add. Sense: Medium not present
[ 395.883380] sd 5:0:0:0: [sdd] tag#0 CDB: Read(10) 28 00 0e 53 7c 70 00 00 08 00
[ 395.883382] blk_update_request: I/O error, dev sdd, sector 240352368 op 0x0:sad:READ) flags 0x0 phys_seg 1 prio class 0
[ 395.883385] Buffer I/O error on dev sdd, logical block 30044046, async page read
[ 398.489749] usb 1-13.4: USB disconnect, device number 7
[ 402.652679] usb 1-13.4: new high-speed USB device number 8 using xhci_hcd
[ 402.853753] usb 1-13.4: New USB device found, idVendor=0781, idProduct=558a, bcdDevice= 1.00
[ 402.853759] usb 1-13.4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 402.853762] usb 1-13.4: Product: Ultra
[ 402.853765] usb 1-13.4: Manufacturer: SanDisk
[ 402.853769] usb 1-13.4: SerialNumber: 050144ee55de8b1ee706b71728e29749f781daae1ad6718e68 d8ce910c30118c1f100000000000000000000018dffbb3ff0c 09108a55810717aabe28
[ 402.855464] usb-storage 1-13.4:1.0: USB Mass Storage device detected
[ 402.855958] scsi host5: usb-storage 1-13.4:1.0
[ 403.870996] scsi 5:0:0:0: Direct-Access SanDisk Ultra 1.00 PQ: 0 ANSI: 6
[ 403.871365] sd 5:0:0:0: Attached scsi generic sg4 type 0
[ 403.871717] sd 5:0:0:0: [sdd] 240353280 512-byte logical blocks: (123 GB/115 GiB)
[ 403.872007] sd 5:0:0:0: [sdd] Write Protect is off
[ 403.872009] sd 5:0:0:0: [sdd] Mode Sense: 43 00 00 00
[ 403.872305] sd 5:0:0:0: [sdd] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
test@TESTING:~$


it seems like ubuntu failed to mount the device at the end[/INDENT]
[/COLOR]

---

### Post by coffeecat on 2021-05-02
@ttkkss1, I've merged these two posts into one thread as they appear to belong together. They were posted as separate threads. I've also removed the two duplcates of the second post from public view. Please do not post duplicates in different parts of the forum. This causes confusion and dilutes community effort. Thanks.

---

### Post by rbmorse on 2021-05-03
Maybe the device just malfunctioned?  In my experience, the service life of a Sandisk flash memory device is too short to be measured reliably without specialized equipment. 

If you haven't had it very long, call their customer support. They'll usually send a replacement (sometimes upgrade) without much fuss.

---

