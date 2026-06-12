---
title: "USB hard disk fails"
date: 2006-10-18
forum: Hardware &amp; Laptops
---

### Post by deb2006 on 2006-10-18
I cannot access my USB hard disk under Dapper at all:

[   71.317245] usb 2-10: new high speed USB device using ehci_hcd and address 10
[   71.323021] scsi5 : SCSI emulation for USB Mass Storage devices
[   72.660325] usb-storage: device found at 10
[   72.660328] usb-storage: waiting for device to settle before scanning
[   73.404218]   Vendor: ST325082  Model: 4A                Rev: 0811
[   73.404230]   Type:   Direct-Access                      ANSI SCSI revision: 00
[   77.166731] usb 2-10: USB disconnect, address 10
[   77.166792] sdc : READ CAPACITY failed.
[   77.166793] sdc : status=0, message=00, host=1, driver=00
[   77.166796] sdc : sense not available.
[   77.166797] sdc: assuming drive cache: write through
[   77.167553] sdc : READ CAPACITY failed.
[   77.167554] sdc : status=0, message=00, host=1, driver=00
[   77.167557] sdc : sense not available.
[   77.167559] sdc: assuming drive cache: write through
[   77.167561]  sdc:<6>sd 5:0:0:0: SCSI error: return code = 0x10000
[   77.167876] end_request: I/O error, dev sdc, sector 0
[   77.167880] Buffer I/O error on device sdc, logical block 0
[   77.167967] sd 5:0:0:0: SCSI error: return code = 0x10000
[   77.167970] end_request: I/O error, dev sdc, sector 0
[   77.167973] Buffer I/O error on device sdc, logical block 0
[   77.167980]  unable to read partition table
[   77.167996] sd 5:0:0:0: Attached scsi disk sdc
[   77.168029] sd 5:0:0:0: Attached scsi generic sg2 type 0
[   77.169640] usb-storage: device scan complete
[   85.688515] usb 2-10: new high speed USB device using ehci_hcd and address 11
[   85.737944] scsi6 : SCSI emulation for USB Mass Storage devices
[   87.075247] usb-storage: device found at 11
[   87.075250] usb-storage: waiting for device to settle before scanning
[   87.819614]   Vendor: ST325082  Model: 4A                Rev: 0811
[   87.819624]   Type:   Direct-Access                      ANSI SCSI revision: 00
[  100.346120] usb 2-10: reset high speed USB device using ehci_hcd and address 11
[  102.474519] usb 2-10: can't restore configuration #1 (error=-110)
[  102.474535] usb 2-10: USB disconnect, address 11
[  102.474569] sd 6:0:0:0: scsi: Device offlined - not ready after error recovery
[  102.474581] sd 6:0:0:0: rejecting I/O to offline device
[  102.474587] sd 6:0:0:0: rejecting I/O to offline device
[  102.474591] sd 6:0:0:0: rejecting I/O to offline device
[  102.474595] sdc : READ CAPACITY failed.
[  102.474596] sdc : status=0, message=00, host=1, driver=00
[  102.474599] sdc : sense not available.
[  102.474601] sdc: assuming drive cache: write through
[  102.474630] sd 6:0:0:0: Attached scsi disk sdc
[  102.474662] sd 6:0:0:0: Attached scsi generic sg2 type 0
[  102.476189] usb-storage: device scan complete
[  102.519440] usb 2-10: new high speed USB device using ehci_hcd and address 12
[  106.730427] usb 2-10: can't set config #1, error -110
[  106.772841] usb 2-10: new high speed USB device using ehci_hcd and address 13
[  111.482026] usb 2-10: unable to read config index 0 descriptor/start
[  111.482031] usb 2-10: can't read configurations, error -110
[  111.524420] usb 2-10: new high speed USB device using ehci_hcd and address 14
[  113.609928] usb 2-10: device descriptor read/all, error -110
[  113.652372] usb 2-10: new high speed USB device using ehci_hcd and address 15
[  115.738299] usb 2-10: unable to read config index 0 descriptor/start
[  115.738304] usb 2-10: can't read configurations, error -110


The hardware should work. The USB port(s) should also work since I am at least using a keyboard and a mouse without problems.

---

