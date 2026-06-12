---
title: "hard drive troubles"
date: 2007-02-01
forum: Hardware &amp; Laptops
---

### Post by nfoti on 2007-02-01
Hello and thanks in advance for any help. I promised a friend I would look at his laptop hard drive which had crapped out on him. I placed the drive in an usb external enclosure case and attempted to connect it to my computer. The drive will not mount, I suspect the drive may be completely dead but I am open to any and all suggestions. 
When I plug the drive in, it briefly comes to life, powers on and spins. The console displays something to the effect of "Buffer I/O error - Bad superblock" with some extra numbers. If I let the computer sit it will continue to cycle through these messages with the numbers changing. 
Fsck and fdisk both give me errors that they cannot open the device, here is my dmesg output:


[17179695.552000] usb 4-4: new high speed USB device using ehci_hcd and address 2
[17179695.684000] usb 4-4: configuration #1 chosen from 1 choice
[17179695.916000] usbcore: registered new driver libusual
[17179696.028000] SCSI subsystem initialized
[17179696.032000] Initializing USB Mass Storage driver...
[17179696.032000] scsi0 : SCSI emulation for USB Mass Storage devices
[17179696.032000] usbcore: registered new driver usb-storage
[17179696.032000] USB Mass Storage support registered.
[17179696.032000] usb-storage: device found at 2
[17179696.032000] usb-storage: waiting for device to settle before scanning
[17179701.032000] usb-storage: device scan complete
[17179701.032000]   Vendor:           Model:                   Rev: 0000
[17179701.032000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179701.136000] sda : very big device. try to use READ CAPACITY(16).
[17179701.140000] sda : READ CAPACITY(16) failed.
[17179701.140000] sda : status=0, message=00, host=5, driver=00
[17179701.140000] sda : use 0xffffffff as device size
[17179701.140000] SCSI device sda: 4294967296 512-byte hdwr sectors (2199023 MB)
[17179701.140000] sda: Write Protect is off
[17179701.140000] sda: Mode Sense: 27 00 00 00
[17179701.140000] sda: assuming drive cache: write through
[17179701.140000] sda : very big device. try to use READ CAPACITY(16).
[17179701.140000] sda : READ CAPACITY(16) failed.
[17179701.140000] sda : status=0, message=00, host=5, driver=00
[17179701.140000] sda : use 0xffffffff as device size
[17179701.140000] SCSI device sda: 4294967296 512-byte hdwr sectors (2199023 MB)
[17179701.144000] sda: Write Protect is off
[17179701.144000] sda: Mode Sense: 27 00 00 00
[17179701.144000] sda: assuming drive cache: write through
[17179701.144000]  sda:<6>sd 0:0:0:0: SCSI error: return code = 0x8000002
[17179701.164000] sda: Current: sense key: Medium Error
[17179701.164000]     Additional sense: Unrecovered read error
[17179701.164000] end_request: I/O error, dev sda, sector 0
[17179701.164000] Buffer I/O error on device sda, logical block 0
[17179701.180000] sd 0:0:0:0: SCSI error: return code = 0x8000002
[17179701.180000] sda: Current: sense key: Medium Error
[17179701.180000]     Additional sense: Unrecovered read error
[17179701.180000] end_request: I/O error, dev sda, sector 0
[17179701.180000] Buffer I/O error on device sda, logical block 0
[17179701.180000]  unable to read partition table
[17179701.184000] sd 0:0:0:0: Attached scsi disk sda
[17179701.212000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179731.320000] usb 4-4: reset high speed USB device using ehci_hcd and address 2
[17179762.384000] usb 4-4: reset high speed USB device using ehci_hcd and address 2
[17179793.448000] usb 4-4: reset high speed USB device using ehci_hcd and address 2
[17179820.928000] ehci_hcd 0000:00:1d.7: remove, state 1
[17179820.928000] usb usb4: USB disconnect, address 1
[17179820.928000] usb 4-4: USB disconnect, address 2
[17179820.928000] sd 0:0:0:0: SCSI error: return code = 0x70000
[17179820.928000] end_request: I/O error, dev sda, sector 4294967168
[17179820.928000] Buffer I/O error on device sda, logical block 536870896
[17179820.928000] sd 0:0:0:0: SCSI error: return code = 0x70000
[17179820.928000] end_request: I/O error, dev sda, sector 4294967168
[17179820.928000] Buffer I/O error on device sda, logical block 536870896
[17179820.928000] sd 0:0:0:0: SCSI error: return code = 0x70000
[17179820.928000] end_request: I/O error, dev sda, sector 4294967288
[17179820.928000] Buffer I/O error on device sda, logical block 536870911
[17179820.932000] sd 0:0:0:0: SCSI error: return code = 0x10000
[17179820.932000] end_request: I/O error, dev sda, sector 4294967288
[17179820.932000] Buffer I/O error on device sda, logical block 536870911
[17179820.932000] sd 0:0:0:0: rejecting I/O to device being removed
[17179820.932000] Buffer I/O error on device sda, logical block 536870911
[17179820.932000] sd 0:0:0:0: rejecting I/O to device being removed
[17179820.932000] Buffer I/O error on device sda, logical block 536870911
[17179820.932000] sd 0:0:0:0: rejecting I/O to device being removed
[17179820.932000] Buffer I/O error on device sda, logical block 536870911
[17179820.932000] sd 0:0:0:0: rejecting I/O to device being removed
[17179820.932000] Buffer I/O error on device sda, logical block 536870911
[17179820.932000] sd 0:0:0:0: rejecting I/O to device being removed
[17179820.932000] Buffer I/O error on device sda, logical block 536870904
[17179820.932000] sd 0:0:0:0: rejecting I/O to device being removed
[17179820.932000] Buffer I/O error on device sda, logical block 536870904
[17179820.932000] sd 0:0:0:0: rejecting I/O to device being removed
[17179820.932000] sd 0:0:0:0: rejecting I/O to device being removed
[17179820.932000] sd 0:0:0:0: rejecting I/O to device being removed
[17179820.932000] sd 0:0:0:0: rejecting I/O to device being removed
[17179820.932000] sd 0:0:0:0: rejecting I/O to device being removed
[17179820.932000] sd 0:0:0:0: rejecting I/O to device being removed
[17179820.932000] sd 0:0:0:0: rejecting I/O to device being removed
[17179820.932000] sd 0:0:0:0: rejecting I/O to device being removed
[17179820.932000] sd 0:0:0:0: rejecting I/O to device being removed
[17179820.932000] sd 0:0:0:0: rejecting I/O to device being removed
[17179820.932000] sd 0:0:0:0: rejecting I/O to device being removed
[17179820.932000] sd 0:0:0:0: rejecting I/O to device being removed
[17179820.932000] sd 0:0:0:0: rejecting I/O to device being removed
[17179820.932000] sd 0:0:0:0: rejecting I/O to device being removed
[17179820.932000] sd 0:0:0:0: rejecting I/O to device being removed
[17179820.932000] sd 0:0:0:0: rejecting I/O to device being removed
[17179820.932000] sd 0:0:0:0: rejecting I/O to device being removed
[17179820.932000] sd 0:0:0:0: rejecting I/O to device being removed
[17179820.932000] sd 0:0:0:0: rejecting I/O to device being removed
[17179820.932000] sd 0:0:0:0: rejecting I/O to device being removed
[17179820.932000] sd 0:0:0:0: rejecting I/O to device being removed
[17179820.932000] sd 0:0:0:0: rejecting I/O to device being removed
[17179820.932000] sd 0:0:0:0: rejecting I/O to device being removed
[17179820.932000] sd 0:0:0:0: rejecting I/O to device being removed
[17179820.932000] sd 0:0:0:0: rejecting I/O to device being removed
[17179820.932000] sd 0:0:0:0: rejecting I/O to device being removed
[17179820.936000] sd 0:0:0:0: rejecting I/O to device being removed
[17179820.936000] sd 0:0:0:0: rejecting I/O to device being removed
[17179820.936000] sd 0:0:0:0: rejecting I/O to device being removed
[17179820.936000] sd 0:0:0:0: rejecting I/O to device being removed
[17179820.936000] sd 0:0:0:0: rejecting I/O to device being removed
[17179820.936000] sd 0:0:0:0: rejecting I/O to device being removed
[17179821.024000] ehci_hcd 0000:00:1d.7: USB bus 4 deregistered
[17179821.024000] ACPI: PCI interrupt for device 0000:00:1d.7 disabled
[17179821.260000] usb 2-2: new full speed USB device using uhci_hcd and address 2
[17179821.424000] usb 2-2: configuration #1 chosen from 1 choice
[17179821.428000] scsi1 : SCSI emulation for USB Mass Storage devices
[17179821.428000] usb-storage: device found at 2
[17179821.428000] usb-storage: waiting for device to settle before scanning
[17179826.428000] usb-storage: device scan complete
[17179826.432000]   Vendor:           Model:                   Rev: 0000
[17179826.432000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179826.436000] sda : very big device. try to use READ CAPACITY(16).
[17179826.436000] sda : READ CAPACITY(16) failed.
[17179826.436000] sda : status=0, message=00, host=5, driver=00
[17179826.436000] sda : use 0xffffffff as device size
[17179826.436000] SCSI device sda: 4294967296 512-byte hdwr sectors (2199023 MB)
[17179826.440000] sda: Write Protect is off
[17179826.440000] sda: Mode Sense: 27 00 00 00
[17179826.440000] sda: assuming drive cache: write through
[17179826.448000] sda : very big device. try to use READ CAPACITY(16).
[17179826.448000] sda : READ CAPACITY(16) failed.
[17179826.448000] sda : status=0, message=00, host=5, driver=00
[17179826.448000] sda : use 0xffffffff as device size
[17179826.448000] SCSI device sda: 4294967296 512-byte hdwr sectors (2199023 MB)
[17179826.452000] sda: Write Protect is off
[17179826.452000] sda: Mode Sense: 27 00 00 00
[17179826.452000] sda: assuming drive cache: write through
[17179826.452000]  sda:<6>sd 1:0:0:0: SCSI error: return code = 0x8000002
[17179826.508000] sda: Current: sense key: Medium Error
[17179826.508000]     Additional sense: Unrecovered read error
[17179826.508000] end_request: I/O error, dev sda, sector 0
[17179826.508000] printk: 63 messages suppressed.
[17179826.508000] Buffer I/O error on device sda, logical block 0
[17179826.560000] sd 1:0:0:0: SCSI error: return code = 0x8000002
[17179826.560000] sda: Current: sense key: Medium Error
[17179826.560000]     Additional sense: Unrecovered read error
[17179826.560000] end_request: I/O error, dev sda, sector 0
[17179826.560000]  unable to read partition table
[17179826.560000] sd 1:0:0:0: Attached scsi disk sda
[17179826.560000] sd 1:0:0:0: Attached scsi generic sg0 type 0
[17179856.756000] usb 2-2: reset full speed USB device using uhci_hcd and address 2
[17179887.820000] usb 2-2: reset full speed USB device using uhci_hcd and address 2
[17179918.884000] usb 2-2: reset full speed USB device using uhci_hcd and address 2
[17179949.948000] usb 2-2: reset full speed USB device using uhci_hcd and address 2
[17179981.012000] usb 2-2: reset full speed USB device using uhci_hcd and address 2
[17180012.076000] usb 2-2: reset full speed USB device using uhci_hcd and address 2
[17180013.028000] sd 1:0:0:0: SCSI error: return code = 0x50000
[17180013.028000] end_request: I/O error, dev sda, sector 4294967168
[17180013.028000] printk: 1 messages suppressed.
[17180013.028000] Buffer I/O error on device sda, logical block 536870896
[17180043.140000] usb 2-2: reset full speed USB device using uhci_hcd and address 2
[17180074.204000] usb 2-2: reset full speed USB device using uhci_hcd and address 2
[17180105.268000] usb 2-2: reset full speed USB device using uhci_hcd and address 2
[17180136.332000] usb 2-2: reset full speed USB device using uhci_hcd and address 2
[17180167.396000] usb 2-2: reset full speed USB device using uhci_hcd and address 2
[17180198.516000] usb 2-2: reset full speed USB device using uhci_hcd and address 2
[17180199.412000] sd 1:0:0:0: SCSI error: return code = 0x50000
[17180199.412000] end_request: I/O error, dev sda, sector 4294967168
[17180199.412000] Buffer I/O error on device sda, logical block 536870896
[17180229.524000] usb 2-2: reset full speed USB device using uhci_hcd and address 2
[17180260.588000] usb 2-2: reset full speed USB device using uhci_hcd and address 2
[17180291.652000] usb 2-2: reset full speed USB device using uhci_hcd and address 2
[17180305.368000] usb 2-2: USB disconnect, address 2
[17180305.372000]  1:0:0:0: SCSI error: return code = 0x10000
[17180305.372000] end_request: I/O error, dev sda, sector 4294967288
[17180305.372000] Buffer I/O error on device sda, logical block 536870911
[17180305.376000]  1:0:0:0: rejecting I/O to dead device
[17180305.376000] Buffer I/O error on device sda, logical block 536870911
[17180305.376000]  1:0:0:0: rejecting I/O to dead device
[17180305.376000] Buffer I/O error on device sda, logical block 536870911
[17180305.376000]  1:0:0:0: rejecting I/O to dead device
[17180305.376000] Buffer I/O error on device sda, logical block 536870911
[17180305.376000]  1:0:0:0: rejecting I/O to dead device
[17180305.376000] Buffer I/O error on device sda, logical block 536870911
[17180305.376000]  1:0:0:0: rejecting I/O to dead device
[17180305.376000] Buffer I/O error on device sda, logical block 536870911
[17180305.376000]  1:0:0:0: rejecting I/O to dead device
[17180305.376000] Buffer I/O error on device sda, logical block 536870904
[17180305.376000]  1:0:0:0: rejecting I/O to dead device
[17180305.376000] Buffer I/O error on device sda, logical block 536870904
[17180305.376000]  1:0:0:0: rejecting I/O to dead device
[17180305.376000] Buffer I/O error on device sda, logical block 536870910
[17180305.376000]  1:0:0:0: rejecting I/O to dead device
[17180305.376000] Buffer I/O error on device sda, logical block 536870910
[17180305.376000]  1:0:0:0: rejecting I/O to dead device
[17180305.376000]  1:0:0:0: rejecting I/O to dead device
[17180305.376000]  1:0:0:0: rejecting I/O to dead device
[17180305.376000]  1:0:0:0: rejecting I/O to dead device
[17180305.376000]  1:0:0:0: rejecting I/O to dead device
[17180305.376000]  1:0:0:0: rejecting I/O to dead device
[17180305.376000]  1:0:0:0: rejecting I/O to dead device
[17180305.376000]  1:0:0:0: rejecting I/O to dead device
[17180305.376000]  1:0:0:0: rejecting I/O to dead device
[17180305.376000]  1:0:0:0: rejecting I/O to dead device
[17180305.376000]  1:0:0:0: rejecting I/O to dead device
[17180305.376000]  1:0:0:0: rejecting I/O to dead device
[17180305.376000]  1:0:0:0: rejecting I/O to dead device
[17180305.376000]  1:0:0:0: rejecting I/O to dead device
[17180305.376000]  1:0:0:0: rejecting I/O to dead device
[17180305.376000]  1:0:0:0: rejecting I/O to dead device
[17180305.376000]  1:0:0:0: rejecting I/O to dead device
[17180305.376000]  1:0:0:0: rejecting I/O to dead device
[17180305.376000]  1:0:0:0: rejecting I/O to dead device
[17180305.376000]  1:0:0:0: rejecting I/O to dead device
[17180305.376000]  1:0:0:0: rejecting I/O to dead device
[17180305.376000]  1:0:0:0: rejecting I/O to dead device
[17180305.376000]  1:0:0:0: rejecting I/O to dead device
[17180305.376000]  1:0:0:0: rejecting I/O to dead device
[17180305.376000]  1:0:0:0: rejecting I/O to dead device
[17180305.376000]  1:0:0:0: rejecting I/O to dead device
[17180305.376000]  1:0:0:0: rejecting I/O to dead device
[17180305.376000]  1:0:0:0: rejecting I/O to dead device
[17180305.376000]  1:0:0:0: rejecting I/O to dead device
[17180305.376000]  1:0:0:0: rejecting I/O to dead device
[17180347.860000] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex
[17180347.864000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[17180358.040000] eth0: no IPv6 routers present
[17180422.228000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17180422.232000] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex
[17180422.232000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[17180432.540000] eth0: no IPv6 routers present
[17180906.960000] hdc: tray open
[17180906.960000] end_request: I/O error, dev hdc, sector 184
[17180906.960000] printk: 61 messages suppressed.
[17180906.960000] Buffer I/O error on device hdc, logical block 23
[17180906.960000] hdc: tray open
[17180906.960000] end_request: I/O error, dev hdc, sector 192
[17180906.960000] Buffer I/O error on device hdc, logical block 24
[17180906.964000] hdc: tray open
[17180906.964000] end_request: I/O error, dev hdc, sector 200
[17180906.964000] Buffer I/O error on device hdc, logical block 25
[17180906.964000] hdc: tray open
[17180906.964000] end_request: I/O error, dev hdc, sector 208
[17180906.964000] Buffer I/O error on device hdc, logical block 26
[17180906.964000] hdc: tray open
[17180906.964000] end_request: I/O error, dev hdc, sector 216
[17180906.964000] Buffer I/O error on device hdc, logical block 27
[17180906.964000] hdc: tray open
[17180906.964000] end_request: I/O error, dev hdc, sector 224
[17180906.964000] Buffer I/O error on device hdc, logical block 28
[17180906.968000] hdc: tray open
[17180906.968000] end_request: I/O error, dev hdc, sector 232
[17180906.968000] Buffer I/O error on device hdc, logical block 29
[17180906.968000] hdc: tray open
[17180906.968000] end_request: I/O error, dev hdc, sector 240
[17180906.968000] Buffer I/O error on device hdc, logical block 30
[17180906.968000] hdc: tray open
[17180906.968000] end_request: I/O error, dev hdc, sector 248
[17180906.968000] Buffer I/O error on device hdc, logical block 31
[17180906.968000] hdc: tray open
[17180906.968000] end_request: I/O error, dev hdc, sector 256
[17180906.968000] Buffer I/O error on device hdc, logical block 32
[17180906.972000] hdc: tray open
[17180906.972000] end_request: I/O error, dev hdc, sector 264
[17180906.972000] hdc: tray open
[17180906.972000] end_request: I/O error, dev hdc, sector 272
[17180906.972000] hdc: tray open
[17180906.972000] end_request: I/O error, dev hdc, sector 280
[17180906.976000] hdc: tray open
[17180906.976000] end_request: I/O error, dev hdc, sector 288
[17180906.976000] hdc: tray open
[17180906.976000] end_request: I/O error, dev hdc, sector 296
[17180906.976000] hdc: tray open
[17180906.976000] end_request: I/O error, dev hdc, sector 304
[17180906.988000] hdc: tray open
[17180906.988000] end_request: I/O error, dev hdc, sector 64
[17180907.008000] hdc: tray open
[17180907.008000] end_request: I/O error, dev hdc, sector 64
[17180907.060000] hdc: tray open
[17180907.060000] end_request: I/O error, dev hdc, sector 64
[17180907.064000] hdc: tray open
[17180907.064000] end_request: I/O error, dev hdc, sector 64
[17180977.224000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17180977.236000] ISO 9660 Extensions: RRIP_1991A
[17224083.944000] e1000: eth0: e1000_watchdog: NIC Link is Down
[17224618.264000] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex
[17224781.976000] usb 2-2: new full speed USB device using uhci_hcd and address 3
[17224782.140000] usb 2-2: configuration #1 chosen from 1 choice
[17224782.144000] scsi2 : SCSI emulation for USB Mass Storage devices
[17224782.144000] usb-storage: device found at 3
[17224782.144000] usb-storage: waiting for device to settle before scanning
[17224787.144000] usb-storage: device scan complete
[17224787.148000]   Vendor:           Model:                   Rev: 0000
[17224787.148000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17224787.156000] sda : very big device. try to use READ CAPACITY(16).
[17224787.160000] sda : READ CAPACITY(16) failed.
[17224787.160000] sda : status=0, message=00, host=5, driver=00
[17224787.160000] sda : use 0xffffffff as device size
[17224787.160000] SCSI device sda: 4294967296 512-byte hdwr sectors (2199023 MB)
[17224787.164000] sda: Write Protect is off
[17224787.164000] sda: Mode Sense: 27 00 00 00
[17224787.164000] sda: assuming drive cache: write through
[17224787.168000] sda : very big device. try to use READ CAPACITY(16).
[17224787.172000] sda : READ CAPACITY(16) failed.
[17224787.172000] sda : status=0, message=00, host=5, driver=00
[17224787.172000] sda : use 0xffffffff as device size
[17224787.172000] SCSI device sda: 4294967296 512-byte hdwr sectors (2199023 MB)
[17224787.176000] sda: Write Protect is off
[17224787.176000] sda: Mode Sense: 27 00 00 00
[17224787.176000] sda: assuming drive cache: write through
[17224787.176000]  sda:<6>sd 2:0:0:0: SCSI error: return code = 0x8000002
[17224787.232000] sda: Current: sense key: Medium Error
[17224787.232000]     Additional sense: Unrecovered read error
[17224787.232000] end_request: I/O error, dev sda, sector 0
[17224787.232000] printk: 10 messages suppressed.
[17224787.232000] Buffer I/O error on device sda, logical block 0
[17224787.284000] sd 2:0:0:0: SCSI error: return code = 0x8000002
[17224787.284000] sda: Current: sense key: Medium Error
[17224787.284000]     Additional sense: Unrecovered read error
[17224787.284000] end_request: I/O error, dev sda, sector 0
[17224787.284000] Buffer I/O error on device sda, logical block 0
[17224787.284000]  unable to read partition table
[17224787.284000] sd 2:0:0:0: Attached scsi disk sda
[17224787.284000] sd 2:0:0:0: Attached scsi generic sg0 type 0
[17224817.656000] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[17224848.720000] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[17224879.784000] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[17224910.848000] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[17224941.912000] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[17224972.976000] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[17224973.928000] sd 2:0:0:0: SCSI error: return code = 0x50000
[17224973.928000] end_request: I/O error, dev sda, sector 4294967168
[17224973.928000] Buffer I/O error on device sda, logical block 536870896
[17225004.040000] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[17225035.104000] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[17225066.168000] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[17225097.232000] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[17225128.296000] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[17225159.360000] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[17225160.312000] sd 2:0:0:0: SCSI error: return code = 0x50000
[17225160.312000] end_request: I/O error, dev sda, sector 4294967168
[17225160.312000] Buffer I/O error on device sda, logical block 536870896
[17225190.424000] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[17225221.488000] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[17225252.552000] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[17225283.616000] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[17225314.680000] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[17225345.744000] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[17225346.696000] sd 2:0:0:0: SCSI error: return code = 0x50000
[17225346.696000] end_request: I/O error, dev sda, sector 4294967288
[17225346.696000] Buffer I/O error on device sda, logical block 536870911
[17225376.808000] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[17225407.872000] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[17225438.936000] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[17225470.000000] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[17225501.064000] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[17225532.128000] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[17225533.080000] sd 2:0:0:0: SCSI error: return code = 0x50000
[17225533.080000] end_request: I/O error, dev sda, sector 4294967288
[17225533.080000] Buffer I/O error on device sda, logical block 536870911
[17225563.192000] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[17225594.256000] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[17225625.320000] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[17225656.384000] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[17225687.448000] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[17225718.512000] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[17225719.464000] sd 2:0:0:0: SCSI error: return code = 0x50000
[17225719.464000] end_request: I/O error, dev sda, sector 4294967288
[17225719.464000] Buffer I/O error on device sda, logical block 536870911
[17225749.576000] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[17225780.640000] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[17225811.704000] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[17225842.768000] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[17225873.832000] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[17225904.896000] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[17225905.848000] sd 2:0:0:0: SCSI error: return code = 0x50000
[17225905.848000] end_request: I/O error, dev sda, sector 4294967288
[17225905.848000] Buffer I/O error on device sda, logical block 536870911
[17225935.960000] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[17225967.024000] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[17225998.088000] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[17226029.152000] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[17226060.216000] usb 2-2: reset full speed USB device using uhci_hcd and address 3

---

### Post by allwin on 2007-02-01
I've found the external enclosures to be fabulously impossible to get working (for me).  You can try "sudo rmmod ehci_cd" which will cut the speed from USB 2 to USB 1 (slowwww) but might mount it.  Another thing, try booting with it attached.  Try plugging another USB device in the port, dismount that thing, and then plug in the HD.

Sometimes the manufacturer of the enclosure puts new firmware on the web which you can download and use to update the device.  That made things a tad better for me on one of the two enclosures I have here which was dual USB/1394 and finally made the 1394 work.

You could also try the live CD of yet another distro and see if it will mount there...try to choose something not UBUNTU and not Debian based just to make sure you are trying something "different".  Might work on an older live CD of UBUNTU.

These are some things you can try, no guarantees.  Then again maybe the disk is bad.  Have you tried (shudder) windoze?  If you have it there it might mount.  If HD is in ext2 or ext3 format there's plenty of windoze software out there (google time) which can read it.

Good luck.

---

### Post by inCursorated on 2007-02-01
the various sector i/o errors lead me to believe this drive is toast. 

if you're going to try to recover data, you may want to check out [helix]("http://www.e-fense.com/helix/")

---

