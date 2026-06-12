---
title: "USB storage problem"
date: 2006-06-22
forum: Hardware &amp; Laptops
---

### Post by andrix on 2006-06-22
Hi.

I've have a PenDrive USB 512 MB.
I've a strange problem  when connect it in Ubuntu Dapper Drake 6.06 (in Ubuntu 5.10 this problem don't ocurr).

The problem is that i connect the pendrive to my laptop, ubuntu automatically reconigze the usb storage and put a new icon on the nautilus.
Everything is ok until here.
But, it disconnect alone and the icon disapper, strangely!!!

I go to /dev and exec ls | grep sda, and show me nothing!

What happen?

Thanks, 
 Andrix.

---

### Post by rowanparker on 2006-06-22
I don't understand "it disconnect alone"???

Are you unmounting it or unplugging it or what?

---

### Post by trucker_jim3000 on 2006-06-23
I'm having this same problem.....

The icon for the device just disappears from the desktop after a few seconds...and any windows that were browsing the drive revert to the home directory

This happens for me on a 512mb flash drive, and a 200gb USB seagate.

both work fine in an XP boot

This is whats going on in dmesg:

**************************************************************************

[17180758.764000] usb 4-1: new high speed USB device using ehci_hcd and address 3
[17180758.988000] scsi1 : SCSI emulation for USB Mass Storage devices
[17180758.988000] usb-storage: device found at 3
[17180758.988000] usb-storage: waiting for device to settle before scanning
[17180763.996000]   Vendor:           Model: USB Flash Memory  Rev: 1.00
[17180763.996000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[17180764.004000] SCSI device sda: 1001472 512-byte hdwr sectors (513 MB)
[17180764.008000] sda: Write Protect is off
[17180764.008000] sda: Mode Sense: 0b 00 00 08
[17180764.008000] sda: assuming drive cache: write through
[17180764.016000] SCSI device sda: 1001472 512-byte hdwr sectors (513 MB)
[17180764.016000] sda: Write Protect is off
[17180764.016000] sda: Mode Sense: 0b 00 00 08
[17180764.016000] sda: assuming drive cache: write through
[17180764.016000]  sda: sda1
[17180764.016000] sd 1:0:0:0: Attached scsi removable disk sda
[17180764.016000] sd 1:0:0:0: Attached scsi generic sg0 type 0
[17180764.016000] usb-storage: device scan complete
[17180764.348000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17180774.684000] hub 4-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[17180774.796000] usb 4-1: reset high speed USB device using ehci_hcd and address 3
[17180774.988000] sd 1:0:0:0: SCSI error: return code = 0x70000
[17180774.988000] end_request: I/O error, dev sda, sector 355963
[17180774.988000] end_request: I/O error, dev sda, sector 355964
[17180779.944000] hub 4-0:1.0: over-current change on port 1
[17180780.048000] usb 4-1: USB disconnect, address 3
[17180780.128000]  1:0:0:0: rejecting I/O to dead device
[17180780.128000] FAT: Directory bread(block 491) failed
[17180780.128000]  1:0:0:0: rejecting I/O to dead device
[17180780.128000] FAT: Directory bread(block 492) failed
[17180780.128000]  1:0:0:0: rejecting I/O to dead device
[17180780.128000] FAT: Directory bread(block 493) failed
[17180780.128000]  1:0:0:0: rejecting I/O to dead device
[17180780.128000] FAT: Directory bread(block 494) failed
[17180780.128000]  1:0:0:0: rejecting I/O to dead device
[17180780.128000] FAT: Directory bread(block 495) failed
[17180780.128000]  1:0:0:0: rejecting I/O to dead device
[17180780.128000] FAT: Directory bread(block 496) failed
[17180780.128000]  1:0:0:0: rejecting I/O to dead device
[17180780.128000] FAT: Directory bread(block 497) failed
[17180780.128000]  1:0:0:0: rejecting I/O to dead device
[17180780.128000] FAT: Directory bread(block 498) failed
[17180780.128000]  1:0:0:0: rejecting I/O to dead device
[17180780.128000] FAT: Directory bread(block 499) failed
[17180780.128000]  1:0:0:0: rejecting I/O to dead device
[17180780.128000] FAT: Directory bread(block 500) failed
[17180780.128000]  1:0:0:0: rejecting I/O to dead device
[17180780.128000] FAT: Directory bread(block 501) failed
[17180780.128000]  1:0:0:0: rejecting I/O to dead device
[17180780.128000] FAT: Directory bread(block 502) failed
[17180780.128000]  1:0:0:0: rejecting I/O to dead device
[17180780.128000] FAT: Directory bread(block 503) failed
[17180780.128000]  1:0:0:0: rejecting I/O to dead device
[17180780.128000] FAT: Directory bread(block 504) failed
[17180780.128000]  1:0:0:0: rejecting I/O to dead device
[17180780.128000] FAT: Directory bread(block 505) failed
[17180780.128000]  1:0:0:0: rejecting I/O to dead device
[17180780.128000] FAT: Directory bread(block 506) failed
[17180780.128000]  1:0:0:0: rejecting I/O to dead device
[17180780.128000] FAT: Directory bread(block 507) failed
[17180780.128000]  1:0:0:0: rejecting I/O to dead device
[17180780.128000] FAT: Directory bread(block 508) failed
[17180780.128000]  1:0:0:0: rejecting I/O to dead device
[17180780.128000] FAT: Directory bread(block 509) failed
[17180780.128000]  1:0:0:0: rejecting I/O to dead device
[17180780.128000] FAT: Directory bread(block 510) failed
[17180780.128000]  1:0:0:0: rejecting I/O to dead device
[17180780.128000] FAT: Directory bread(block 511) failed
[17180780.128000]  1:0:0:0: rejecting I/O to dead device
[17180780.128000] FAT: Directory bread(block 512) failed
[17180780.128000]  1:0:0:0: rejecting I/O to dead device
[17180780.128000] FAT: Directory bread(block 513) failed
[17180780.128000]  1:0:0:0: rejecting I/O to dead device
[17180780.128000] FAT: Directory bread(block 514) failed
[17180780.128000]  1:0:0:0: rejecting I/O to dead device
[17180780.128000] FAT: Directory bread(block 515) failed
[17180780.128000]  1:0:0:0: rejecting I/O to dead device
[17180780.128000] FAT: Directory bread(block 516) failed
[17180780.128000]  1:0:0:0: rejecting I/O to dead device
[17180780.128000] FAT: Directory bread(block 517) failed
[17180780.128000]  1:0:0:0: rejecting I/O to dead device
[17180780.128000] FAT: Directory bread(block 518) failed
[17180780.128000]  1:0:0:0: rejecting I/O to dead device
[17180780.128000] FAT: Directory bread(block 519) failed
[17180780.128000]  1:0:0:0: rejecting I/O to dead device
[17180780.128000] FAT: Directory bread(block 520) failed
[17180780.128000]  1:0:0:0: rejecting I/O to dead device
[17180780.128000] FAT: Directory bread(block 521) failed
[17180780.128000]  1:0:0:0: rejecting I/O to dead device
[17180780.128000] FAT: Directory bread(block 522) failed
[17180780.288000] usb 4-1: new high speed USB device using ehci_hcd and address 4
[17180780.512000] scsi2 : SCSI emulation for USB Mass Storage devices
[17180780.512000] hub 4-0:1.0: over-current change on port 2
[17180780.512000] usb-storage: device found at 4
[17180780.512000] usb-storage: waiting for device to settle before scanning
[17180780.616000] hub 4-0:1.0: over-current change on port 1
[17180780.720000] hub 4-0:1.0: over-current change on port 2
[17180780.824000] hub 4-0:1.0: over-current change on port 1
[17180780.928000] usb 4-1: USB disconnect, address 4
[17180781.168000] usb 4-1: new high speed USB device using ehci_hcd and address 5
[17180781.392000] scsi3 : SCSI emulation for USB Mass Storage devices
[17180781.392000] usb-storage: device found at 5
[17180781.392000] usb-storage: waiting for device to settle before scanning
[17180782.464000] hub 4-0:1.0: over-current change on port 1
[17180782.568000] usb 4-1: USB disconnect, address 5
[17180782.808000] usb 4-1: new high speed USB device using ehci_hcd and address 6
[17180783.032000] scsi4 : SCSI emulation for USB Mass Storage devices
[17180783.032000] hub 4-0:1.0: over-current change on port 2
[17180783.032000] usb-storage: device found at 6
[17180783.032000] usb-storage: waiting for device to settle before scanning
[17180783.220000] hub 4-0:1.0: over-current change on port 1
[17180783.324000] usb 4-1: USB disconnect, address 6
[17180783.564000] usb 4-1: new high speed USB device using ehci_hcd and address 7
[17180783.788000] scsi5 : SCSI emulation for USB Mass Storage devices
[17180783.788000] hub 4-0:1.0: over-current change on port 2
[17180783.788000] usb-storage: device found at 7
[17180783.788000] usb-storage: waiting for device to settle before scanning
[17180783.976000] hub 4-0:1.0: over-current change on port 1
[17180784.080000] usb 4-1: USB disconnect, address 7
[17180784.320000] usb 4-1: new high speed USB device using ehci_hcd and address 8
[17180784.544000] scsi6 : SCSI emulation for USB Mass Storage devices
[17180784.544000] hub 4-0:1.0: over-current change on port 2
[17180784.544000] usb-storage: device found at 8
[17180784.544000] usb-storage: waiting for device to settle before scanning
[17180789.552000]   Vendor:           Model: USB Flash Memory  Rev: 1.00
[17180789.552000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[17180789.560000] SCSI device sda: 1001472 512-byte hdwr sectors (513 MB)
[17180789.560000] sda: Write Protect is off
[17180789.560000] sda: Mode Sense: 0b 00 00 08
[17180789.560000] sda: assuming drive cache: write through
[17180789.568000] SCSI device sda: 1001472 512-byte hdwr sectors (513 MB)
[17180789.568000] sda: Write Protect is off
[17180789.568000] sda: Mode Sense: 0b 00 00 08
[17180789.568000] sda: assuming drive cache: write through
[17180789.568000]  sda: sda1
[17180789.572000] sd 6:0:0:0: Attached scsi removable disk sda
[17180789.572000] sd 6:0:0:0: Attached scsi generic sg0 type 0
[17180789.572000] usb-storage: device scan complete
[17180789.892000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17180802.624000] hub 4-0:1.0: over-current change on port 1
[17180802.728000] usb 4-1: USB disconnect, address 8
[17180802.968000] usb 4-1: new high speed USB device using ehci_hcd and address 9
[17180803.192000] scsi7 : SCSI emulation for USB Mass Storage devices
[17180803.192000] hub 4-0:1.0: over-current change on port 2
[17180803.192000] usb-storage: device found at 9
[17180803.192000] usb-storage: waiting for device to settle before scanning
[17180804.892000] hub 4-0:1.0: over-current change on port 1
[17180804.996000] usb 4-1: USB disconnect, address 9
[17180805.236000] usb 4-1: new high speed USB device using ehci_hcd and address 10
[17180805.460000] scsi8 : SCSI emulation for USB Mass Storage devices
[17180805.460000] usb-storage: device found at 10
[17180805.460000] usb-storage: waiting for device to settle before scanning
[17180810.468000]   Vendor:           Model: USB Flash Memory  Rev: 1.00
[17180810.468000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[17180810.476000] SCSI device sda: 1001472 512-byte hdwr sectors (513 MB)
[17180810.480000] sda: Write Protect is off
[17180810.480000] sda: Mode Sense: 0b 00 00 08
[17180810.480000] sda: assuming drive cache: write through
[17180810.488000] SCSI device sda: 1001472 512-byte hdwr sectors (513 MB)
[17180810.488000] sda: Write Protect is off
[17180810.488000] sda: Mode Sense: 0b 00 00 08
[17180810.488000] sda: assuming drive cache: write through
[17180810.488000]  sda: sda1
[17180810.488000] sd 8:0:0:0: Attached scsi removable disk sda
[17180810.488000] sd 8:0:0:0: Attached scsi generic sg0 type 0
[17180810.488000] usb-storage: device scan complete
[17180810.688000] hub 4-0:1.0: over-current change on port 2
[17180810.784000] sd 8:0:0:0: SCSI error: return code = 0x70000
[17180810.784000] end_request: I/O error, dev sda, sector 64
[17180810.784000] Buffer I/O error on device sda, logical block 8
[17180810.784000] sd 8:0:0:0: SCSI error: return code = 0x70000
[17180810.784000] end_request: I/O error, dev sda, sector 72
[17180810.784000] Buffer I/O error on device sda, logical block 9
[17180810.784000] sd 8:0:0:0: SCSI error: return code = 0x70000
[17180810.784000] end_request: I/O error, dev sda, sector 80
[17180810.784000] Buffer I/O error on device sda, logical block 10
[17180810.784000] sd 8:0:0:0: SCSI error: return code = 0x70000
[17180810.784000] end_request: I/O error, dev sda, sector 88
[17180810.784000] Buffer I/O error on device sda, logical block 11
[17180810.784000] sd 8:0:0:0: SCSI error: return code = 0x70000
[17180810.784000] end_request: I/O error, dev sda, sector 96
[17180810.784000] Buffer I/O error on device sda, logical block 12
[17180810.784000] sd 8:0:0:0: SCSI error: return code = 0x70000
[17180810.784000] end_request: I/O error, dev sda, sector 104
[17180810.784000] Buffer I/O error on device sda, logical block 13
[17180810.784000] sd 8:0:0:0: SCSI error: return code = 0x70000
[17180810.784000] end_request: I/O error, dev sda, sector 112
[17180810.784000] Buffer I/O error on device sda, logical block 14
[17180810.784000] sd 8:0:0:0: SCSI error: return code = 0x70000
[17180810.784000] end_request: I/O error, dev sda, sector 120
[17180810.784000] Buffer I/O error on device sda, logical block 15
[17180810.784000] sd 8:0:0:0: SCSI error: return code = 0x70000
[17180810.784000] end_request: I/O error, dev sda, sector 128
[17180810.784000] Buffer I/O error on device sda, logical block 16
[17180810.788000] sd 8:0:0:0: SCSI error: return code = 0x70000
[17180810.788000] end_request: I/O error, dev sda, sector 136
[17180810.788000] Buffer I/O error on device sda, logical block 17
[17180810.788000] sd 8:0:0:0: SCSI error: return code = 0x70000
[17180810.788000] end_request: I/O error, dev sda, sector 144
[17180810.788000] sd 8:0:0:0: SCSI error: return code = 0x70000
[17180810.788000] end_request: I/O error, dev sda, sector 152
[17180810.788000] sd 8:0:0:0: SCSI error: return code = 0x70000
[17180810.788000] end_request: I/O error, dev sda, sector 160
[17180810.788000] sd 8:0:0:0: SCSI error: return code = 0x70000
[17180810.788000] end_request: I/O error, dev sda, sector 168
[17180810.788000] sd 8:0:0:0: SCSI error: return code = 0x70000
[17180810.788000] end_request: I/O error, dev sda, sector 176
[17180810.788000] sd 8:0:0:0: SCSI error: return code = 0x70000
[17180810.788000] end_request: I/O error, dev sda, sector 184
[17180810.788000] sd 8:0:0:0: SCSI error: return code = 0x70000
[17180810.788000] end_request: I/O error, dev sda, sector 64
[17180810.788000] sda : READ CAPACITY failed.
[17180810.788000] sda : status=0, message=00, host=7, driver=00
[17180810.788000] sda : sense not available.
[17180810.788000] sda: Write Protect is off
[17180810.788000] sda: Mode Sense: 00 00 00 00
[17180810.788000] sda: assuming drive cache: write through
[17180810.792000] usb 4-1: USB disconnect, address 10
[17180810.792000] sda : READ CAPACITY failed.
[17180810.792000] sda : status=0, message=00, host=1, driver=00
[17180810.792000] sda : sense not available.
[17180810.792000]  8:0:0:0: rejecting I/O to dead device
[17180810.792000] sda: Write Protect is off
[17180810.792000] sda: Mode Sense: 00 00 00 00
[17180810.792000] sda: assuming drive cache: write through
[17180810.792000]  sda:<3> 8:0:0:0: rejecting I/O to dead device
[17180810.792000]  8:0:0:0: rejecting I/O to dead device
[17180810.792000]  unable to read partition table
[17180810.792000]  8:0:0:0: rejecting I/O to dead device
[17180814.972000] hub 4-0:1.0: over-current change on port 1
[17180828.076000] hub 4-0:1.0: over-current change on port 1
[17180828.180000] hub 4-0:1.0: over-current change on port 2
[17180834.124000] hub 4-0:1.0: over-current change on port 1
[17180834.228000] hub 4-0:1.0: over-current change on port 2

**************************************************************************

---

### Post by trucker_jim3000 on 2006-06-23
p.s. I also get this error:

[17179704.000000] Driver 'sd' needs updating - please use bus_type methods


I have tried experimenting by lowering my chipset voltage to no avail.


any help would be much appreciated!

---

