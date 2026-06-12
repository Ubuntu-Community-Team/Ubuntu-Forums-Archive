---
title: "usb2ide2cf adapter problem"
date: 2008-07-05
forum: Hardware
---

### Post by Hrundik on 2008-07-05
Hello, I've bougt ide2usb and cf2ide adapters, inserted 1GB CF card and connected the adapters, but it doesn't seem to work.
CF card works OK in my PDA.

May you please help me figure out the problem?

Here is dmesg output:
```

[  690.811202] usb 4-1: new high speed USB device using ehci_hcd and address 6
[  690.862187] usb 4-1: configuration #1 chosen from 1 choice
[  690.881250] scsi5 : SCSI emulation for USB Mass Storage devices
[  690.893137] usb-storage: device found at 6
[  690.893149] usb-storage: waiting for device to settle before scanning
[  692.462874] usb-storage: device scan complete
[  692.464113] scsi 5:0:0:0: Direct-Access     TOSHIBA  THNCF1G02QG(     0811 PQ: 0 ANSI: 0
[  692.466320] sd 5:0:0:0: [sdb] 2000880 512-byte hardware sectors (1024 MB)
[  692.468079] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  692.468095] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  692.469816] sd 5:0:0:0: [sdb] 2000880 512-byte hardware sectors (1024 MB)
[  692.471581] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  692.471597] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  692.471612]  sdb:<6>usb 4-1: reset high speed USB device using ehci_hcd and address 6
[  719.290223] usb 4-1: reset high speed USB device using ehci_hcd and address 6
[  736.345427] usb 4-1: reset high speed USB device using ehci_hcd and address 6
[  746.999735] usb 4-1: reset high speed USB device using ehci_hcd and address 6
[  757.271410] usb 4-1: reset high speed USB device using ehci_hcd and address 6
[  765.897163] usb 4-1: reset high speed USB device using ehci_hcd and address 6
[  765.937034] sd 5:0:0:0: [sdb] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK,SUGGEST_OK
[  765.937056] end_request: I/O error, dev sdb, sector 0
[  765.937066] printk: 4 messages suppressed.
[  765.937074] Buffer I/O error on device sdb, logical block 0
[  774.753514] usb 4-1: reset high speed USB device using ehci_hcd and address 6

```

---

