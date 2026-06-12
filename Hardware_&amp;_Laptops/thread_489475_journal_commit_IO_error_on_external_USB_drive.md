---
title: "journal commit I/O error on external USB drive"
date: 2007-07-01
forum: Hardware &amp; Laptops
---

### Post by Keith_Beef on 2007-07-01
Hello, all.

I've noticed an annoying problem since moving from Edgy to Feisty.

I have a small hard disc that I put into an external USB enclosure a couple of years ago. I keep music and some photos on it, on two ext3 filesystems.

Since moving to Feisty, I've noticed that it "disconnects" itself sometimes. I get a message pop up about "unsafe media removal" (or similar), and in a terminal window I see "journal commit I/O error".

The run-up to this, seen by dmesg looks like this:


```
[ 2564.350790] usb 2-3: device descriptor read/64, error -71
[ 2564.562711] usb 2-3: device descriptor read/64, error -71
[ 2564.774625] usb 2-3: reset high speed USB device using ehci_hcd and address 3
[ 2564.886576] usb 2-3: device descriptor read/64, error -71
[ 2639.590265] usb 2-3: reset high speed USB device using ehci_hcd and address 3
[ 2639.702225] usb 2-3: device descriptor read/64, error -71
[ 2639.910148] usb 2-3: device descriptor read/64, error -71
[ 2640.122064] usb 2-3: reset high speed USB device using ehci_hcd and address 3
[ 2640.234024] usb 2-3: device descriptor read/64, error -71
[ 2640.445941] usb 2-3: device descriptor read/64, error -71
[ 2640.657866] usb 2-3: reset high speed USB device using ehci_hcd and address 3
[ 2641.065699] usb 2-3: device not accepting address 3, error -71
[ 2641.177671] usb 2-3: reset high speed USB device using ehci_hcd and address 3
[ 2641.585504] usb 2-3: device not accepting address 3, error -71
[ 2641.585538] usb 2-3: USB disconnect, address 3
[ 2641.586689] sd 3:0:0:0: SCSI error: return code = 0x00010000
[ 2641.586693] end_request: I/O error, dev sda, sector 119506115
[ 2641.586698] Buffer I/O error on device sda5, logical block 4198804
[ 2641.586701] lost page write due to I/O error on sda5
[ 2641.586705] Buffer I/O error on device sda5, logical block 4198805
[ 2641.586707] lost page write due to I/O error on sda5
[ 2641.586710] Buffer I/O error on device sda5, logical block 4198806
[ 2641.586712] lost page write due to I/O error on sda5
[ 2641.586715] Buffer I/O error on device sda5, logical block 4198807
[ 2641.586718] lost page write due to I/O error on sda5
[ 2641.586720] Buffer I/O error on device sda5, logical block 4198808
[ 2641.586723] lost page write due to I/O error on sda5
[ 2641.586725] Buffer I/O error on device sda5, logical block 4198809
[ 2641.586728] lost page write due to I/O error on sda5
[ 2641.586731] Buffer I/O error on device sda5, logical block 4198810
[ 2641.586733] lost page write due to I/O error on sda5
[ 2641.586736] Buffer I/O error on device sda5, logical block 4198811
[ 2641.586738] lost page write due to I/O error on sda5
[ 2641.586741] Buffer I/O error on device sda5, logical block 4198812
[ 2641.586743] lost page write due to I/O error on sda5
[ 2641.586746] Buffer I/O error on device sda5, logical block 4198813
[ 2641.586748] lost page write due to I/O error on sda5
[ 2641.586874] sd 3:0:0:0: SCSI error: return code = 0x00010000
[ 2641.586877] end_request: I/O error, dev sda, sector 119506355
[ 2641.588953] Aborting journal on device sda5.
[ 2641.588967] __journal_remove_journal_head: freeing b_committed_data
[ 2641.589347] Aborting journal on device sda1.
```


Any idea why this is happening, and what I can do to fix it?

---

