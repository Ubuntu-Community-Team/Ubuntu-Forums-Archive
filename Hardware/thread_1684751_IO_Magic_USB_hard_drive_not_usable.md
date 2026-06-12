---
title: "IO Magic USB hard drive not usable"
date: 2011-02-09
forum: Hardware
---

### Post by twistedwire on 2011-02-09
trying to install Ubuntu 10.10 on to an 80 gig IO Magic USB hard drive, but can't get it working. The device works with windows but errors in ubuntu...from cd and an exsisting install. Tried on HP dc7700, nc6400, and an Elite 8000... anyone got any ideas??

Thanks!

dmesg tail:

[2339314.444339] sd 14:0:0:0: [sdb] Attached SCSI disk
[2339345.112068] usb 1-4: reset high speed USB device using ehci_hcd and address 25
[2339360.224067] usb 1-4: device descriptor read/64, error -110
[2339375.440052] usb 1-4: device descriptor read/64, error -110
[2339375.656069] usb 1-4: reset high speed USB device using ehci_hcd and address 25
[2339390.768064] usb 1-4: device descriptor read/64, error -110
[2339405.984064] usb 1-4: device descriptor read/64, error -110
[2339406.200068] usb 1-4: reset high speed USB device using ehci_hcd and address 25
[2339416.612100] usb 1-4: device not accepting address 25, error -110
[2339416.724067] usb 1-4: reset high speed USB device using ehci_hcd and address 25
[2339427.132059] usb 1-4: device not accepting address 25, error -110
[2339427.132120] usb 1-4: USB disconnect, address 25
[2339427.132136] sd 14:0:0:0: Device offlined - not ready after error recovery
[2339427.132149] sd 14:0:0:0: [sdb] Unhandled error code
[2339427.132154] sd 14:0:0:0: [sdb] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
[2339427.132162] sd 14:0:0:0: [sdb] CDB: Read(10): 28 00 09 50 f8 b0 00 00 01 00
[2339427.132184] end_request: I/O error, dev sdb, sector 156301488
[2339427.132192] __ratelimit: 6 callbacks suppressed
[2339427.132198] Buffer I/O error on device sdb, logical block 156301488
[2339427.132254] sd 14:0:0:0: rejecting I/O to offline device
[2339427.257080] usb 1-4: new high speed USB device using ehci_hcd and address 26
[2339442.368064] usb 1-4: device descriptor read/64, error -110
[2339457.584056] usb 1-4: device descriptor read/64, error -110
[2339457.800066] usb 1-4: new high speed USB device using ehci_hcd and address 27
[2339472.912061] usb 1-4: device descriptor read/64, error -110
[2339488.128068] usb 1-4: device descriptor read/64, error -110
[2339488.344058] usb 1-4: new high speed USB device using ehci_hcd and address 28
[2339498.752050] usb 1-4: device not accepting address 28, error -110
[2339498.864066] usb 1-4: new high speed USB device using ehci_hcd and address 29
[2339509.272520] usb 1-4: device not accepting address 29, error -110
[2339509.272549] hub 1-0:1.0: unable to enumerate USB device on port 4
[2339509.664065] usb 3-2: new full speed USB device using uhci_hcd and address 3
[2339524.776074] usb 3-2: device descriptor read/64, error -110
[2339539.993059] usb 3-2: device descriptor read/64, error -110
[2339540.208075] usb 3-2: new full speed USB device using uhci_hcd and address 4
[2339555.320073] usb 3-2: device descriptor read/64, error -110
[2339570.537069] usb 3-2: device descriptor read/64, error -110
[2339570.752048] usb 3-2: new full speed USB device using uhci_hcd and address 5
[2339581.160070] usb 3-2: device not accepting address 5, error -110
[2339581.272059] usb 3-2: new full speed USB device using uhci_hcd and address 6
[2339591.680062] usb 3-2: device not accepting address 6, error -110
[2339591.680091] hub 3-0:1.0: unable to enumerate USB device on port 2

---

### Post by dabl on 2011-02-09
[http://www.linux-usb.org/FAQ.html](http://www.linux-usb.org/FAQ.html)

See "Troubleshooting", #6.

---

### Post by twistedwire on 2011-02-09
Thanks a bunch, I'll check it out!

---

