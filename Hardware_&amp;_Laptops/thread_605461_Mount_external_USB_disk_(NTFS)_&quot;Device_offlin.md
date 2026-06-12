---
title: "Mount external USB disk (NTFS): &quot;Device offlined - not ready after error recovery&quot;"
date: 2007-11-07
forum: Hardware &amp; Laptops
---

### Post by cyberco on 2007-11-07
I have an external USB disc (250Gb, NTFS) that Ubuntu won't mount. DMESG gives me:

```
[  869.656000] Initializing USB Mass Storage driver...
[  869.660000] scsi2 : SCSI emulation for USB Mass Storage devices
[  869.660000] usbcore: registered new interface driver usb-storage
[  869.660000] USB Mass Storage support registered.
[  869.660000] usb-storage: device found at 3
[  869.660000] usb-storage: waiting for device to settle before scanning
[  874.660000] usb-storage: device scan complete
[  880.440000] usb 5-6: USB disconnect, address 3
[  880.440000] scsi 2:0:0:0: scsi: Device offlined - not ready after error recovery
```

---

### Post by cyberco on 2007-11-08
I can get the disc working by:

- Turn on the disc
- wait for the disc to settle
- plug in the usb plug (in a new USB port in my case)

dmesg now gives me:

```

[  525.744000] Initializing USB Mass Storage driver...
[  525.744000] scsi2 : SCSI emulation for USB Mass Storage devices
[  525.744000] usb-storage: device found at 4
[  525.744000] usb-storage: waiting for device to settle before scanning
[  525.744000] usbcore: registered new interface driver usb-storage
[  525.744000] USB Mass Storage support registered.
[  530.744000] usb-storage: device scan complete
[  530.744000] scsi 2:0:0:0: Direct-Access     WDC WD32 00JB-00KFA0      0811 PQ: 0 ANSI: 0
[  530.748000] sd 2:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[  530.748000] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  530.748000] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  530.748000] sd 2:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[  530.752000] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  530.752000] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  530.752000]  sdb: sdb1 < sdb5 >
[  530.768000] sd 2:0:0:0: [sdb] Attached SCSI disk
[  530.768000] sd 2:0:0:0: Attached scsi generic sg2 type 0

```

I haven't tested it thoroughly so I'm not sure if it stays working.

---

### Post by cyberco on 2007-11-20
Unfortunately the problem returned. It worked for a while on the new USB port, but after a while the same error reappeared. Here's 'dmesg' after trying four different USB ports (of which none works):

```

[  150.904000] usb 5-1: new high speed USB device using ehci_hcd and address 3
[  151.044000] usb 5-1: configuration #1 chosen from 1 choice
[  151.240000] usbcore: registered new interface driver libusual
[  151.280000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[  151.280000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[  151.304000] Initializing USB Mass Storage driver...
[  151.304000] scsi2 : SCSI emulation for USB Mass Storage devices
[  151.304000] usb-storage: device found at 3
[  151.304000] usb-storage: waiting for device to settle before scanning
[  151.304000] usbcore: registered new interface driver usb-storage
[  151.304000] USB Mass Storage support registered.
[  156.304000] usb-storage: device scan complete
[  162.084000] usb 5-1: USB disconnect, address 3
[  162.084000] scsi 2:0:0:0: scsi: Device offlined - not ready after error recovery
[  542.184000] usb 5-6: new high speed USB device using ehci_hcd and address 4
[  542.324000] usb 5-6: configuration #1 chosen from 1 choice
[  542.324000] scsi3 : SCSI emulation for USB Mass Storage devices
[  542.328000] usb-storage: device found at 4
[  542.328000] usb-storage: waiting for device to settle before scanning
[  547.328000] usb-storage: device scan complete
[  553.108000] usb 5-6: USB disconnect, address 4
[  553.108000] scsi 3:0:0:0: scsi: Device offlined - not ready after error recovery
[  611.060000] usb 5-2: new high speed USB device using ehci_hcd and address 5
[  611.200000] usb 5-2: configuration #1 chosen from 1 choice
[  611.240000] scsi4 : SCSI emulation for USB Mass Storage devices
[  611.240000] usb-storage: device found at 5
[  611.240000] usb-storage: waiting for device to settle before scanning
[  616.240000] usb-storage: device scan complete
[  622.020000] usb 5-2: USB disconnect, address 5
[  622.020000] scsi 4:0:0:0: scsi: Device offlined - not ready after error recovery


```

---

### Post by cyberco on 2007-12-04
Strange, if I wait with plugging in the USB plug but first turn on the disk and wait for 2 minutes and THEN plug it in the disk is recognized correctly. In that case DMESG gives me:

```

[  698.380000] Initializing USB Mass Storage driver...
[  698.380000] scsi2 : SCSI emulation for USB Mass Storage devices
[  698.380000] usb-storage: device found at 3
[  698.380000] usb-storage: waiting for device to settle before scanning
[  698.380000] usbcore: registered new interface driver usb-storage
[  698.380000] USB Mass Storage support registered.
[  703.380000] usb-storage: device scan complete
[  703.380000] scsi 2:0:0:0: Direct-Access     WDC WD32 00JB-00KFA0      0811 PQ: 0 ANSI: 0
[  703.384000] sd 2:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[  703.384000] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  703.384000] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  703.384000] sd 2:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[  703.388000] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  703.388000] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  703.388000]  sdb: sdb1 < sdb5 >
[  703.404000] sd 2:0:0:0: [sdb] Attached SCSI disk
[  703.404000] sd 2:0:0:0: Attached scsi generic sg2 type 0


```

---

### Post by Robstarusa on 2008-01-23
I have the same problem.  Am trying the "2 minute fix".

Does this consistently work?

---

### Post by Daelyn on 2008-01-24
Maxtor 500Gb
MY FINDINGS:

HDD goes to standby after not being used for a while. Unknown time-out/sleep timer.

~ If I connect the USB cable whilst in standby, it will spin up but not be correctly recognized (the "wait to settle" time seems to be too short).

~ If it is accessed after being put in standby (when already connected), it will spin up and be accessed correctly in about 3 seconds.

> What I usually do, if it is disconnected and in standby, is power it down and power it back on and wait five seconds before connecting it (by that time it has spun up and become ready).
> Or, I connect it, let it spin up, disconnect and reconnect. Then it is recognized fine.

---

### Post by ktenney on 2008-01-28
I had this problem, 3 different drives weren't recognized until I
removed the jumper (MA, SL, CS), then they all worked.

Thanks,
Kent

---

### Post by Robstarusa on 2008-01-30
I switched enclosures & this caused it to work 100% of the time :(

---

### Post by bastubis on 2008-02-05
I've got a LaCie mobile USB HD which works on 3 different gutsy machines I've tried it on and any Windows machine I've plugged it into but not on my laptop - a dual boot, it won't mount under Linux or Windows on my dual-boot Inspiron 500m. 

lsusb lists it as:

Bus 004 Device 002: ID 059f:0c41 LaCie, Ltd 

but I'm getting the 'offlined after error' dmesg when gutsy tries to mount it:

[  137.896000] Initializing USB Mass Storage driver...
[  137.896000] scsi2 : SCSI emulation for USB Mass Storage devices
[  137.896000] usb-storage: device found at 2
[  137.896000] usb-storage: waiting for device to settle before scanning
[  137.896000] usbcore: registered new interface driver usb-storage
[  137.900000] USB Mass Storage support registered.
[  142.896000] usb-storage: device scan complete
[  148.508000] usb 4-3: reset high speed USB device using ehci_hcd and address 2
[  158.752000] usb 4-3: reset high speed USB device using ehci_hcd and address 2
[  175.604000] usb 4-3: reset high speed USB device using ehci_hcd and address 2
[  175.852000] usb 4-3: reset high speed USB device using ehci_hcd and address 2
[  186.096000] usb 4-3: reset high speed USB device using ehci_hcd and address 2
[  186.228000] scsi 2:0:0:0: scsi: Device offlined - not ready after error recovery

It has a USB power cable which I tried - this wrecked my partition table by creating a new partition on my primary fixed HD where there wasn't any free space. I flashed the BIOS on the laptop (old BIOS version known for problems mounting some USB devices) but this hasn't made any difference. I've found some discussion of older USB 2.0 devices not working with ehci_hcd but this is pretty new and works under Linux on any other machine. 

It's a mobile device so I'm not about to try putting it in a new case and it doesn't have a power button. 

Ideas welcome!

---

