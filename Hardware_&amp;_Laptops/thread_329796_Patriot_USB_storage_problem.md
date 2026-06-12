---
title: "Patriot USB storage problem"
date: 2007-01-02
forum: Hardware &amp; Laptops
---

### Post by Laki on 2007-01-02
Hello.

I'm having problems with Patriot USB storage 2 GB device. I cannot mount it. When I plug it in, red light is flashing on it, and it doesn't stop. I have 6.10 Edgy. This same device is working fine on my laptop with 6.06. 

dmesg:
> [17179651.964000] usb 5-4: new high speed USB device using ehci_hcd and address 2
[17179652.100000] usb 5-4: configuration #1 chosen from 1 choice
[17179652.320000] usbcore: registered new driver libusual
[17179652.416000] Initializing USB Mass Storage driver...
[17179652.416000] scsi0 : SCSI emulation for USB Mass Storage devices
[17179652.420000] usb-storage: device found at 2
[17179652.420000] usb-storage: waiting for device to settle before scanning
[17179652.420000] usbcore: registered new driver usb-storage
[17179652.420000] USB Mass Storage support registered.
[17179657.420000] usb-storage: device scan complete
[17179657.420000]   Vendor:           Model: USB DISK Pro      Rev: PMAP
[17179657.420000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179657.420000]   Vendor:           Model: USB DISK Pro      Rev: PMAP
[17179657.420000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179658.092000] SCSI device sda: 3945472 512-byte hdwr sectors (2020 MB)
[17179658.092000] sda: Write Protect is off
[17179658.092000] sda: Mode Sense: 23 00 00 00
[17179658.092000] sda: assuming drive cache: write through
[17179658.096000] SCSI device sda: 3945472 512-byte hdwr sectors (2020 MB)
[17179658.096000] sda: Write Protect is off
[17179658.096000] sda: Mode Sense: 23 00 00 00
[17179658.096000] sda: assuming drive cache: write through
[17179658.096000]  sda:<6>usb 5-4: reset high speed USB device using ehci_hcd and address 2
[17179691.320000] usb 5-4: device descriptor read/64, error -110
[17179706.536000] usb 5-4: device descriptor read/64, error -110
[17179706.752000] usb 5-4: reset high speed USB device using ehci_hcd and address 2
[17179709.864000] usb 5-4: device descriptor read/64, error -110
[17179725.080000] usb 5-4: device descriptor read/64, error -110
[17179725.296000] usb 5-4: reset high speed USB device using ehci_hcd and address 2
[17179735.704000] usb 5-4: device not accepting address 2, error -110
[17179735.816000] usb 5-4: reset high speed USB device using ehci_hcd and address 2
[17179746.224000] usb 5-4: device not accepting address 2, error -110
[17179746.224000] usb 5-4: USB disconnect, address 2
[17179746.224000] sd 0:0:0:0: scsi: Device offlined - not ready after error recovery
[17179746.228000] sd 0:0:0:0: SCSI error: return code = 0x10000
[17179746.228000] end_request: I/O error, dev sda, sector 0
[17179746.228000] Buffer I/O error on device sda, logical block 0
[17179746.228000] sd 0:0:0:0: rejecting I/O to device being removed
[17179746.228000] Buffer I/O error on device sda, logical block 0
[17179746.228000]  unable to read partition table
[17179746.228000] sd 0:0:0:0: Attached scsi removable disk sda
[17179746.244000] sda : READ CAPACITY failed.
[17179746.244000] sda : status=0, message=00, host=1, driver=00 
[17179746.244000] sda : sense not available. 
[17179746.244000] sda: Write Protect is off
[17179746.244000] sda: Mode Sense: 00 00 00 00
[17179746.244000] sda: assuming drive cache: write through
[17179746.244000] sd 0:0:0:1: Attached scsi removable disk sda
[17179746.356000] usb 5-4: new high speed USB device using ehci_hcd and address 3
[17179749.468000] usb 5-4: device descriptor read/64, error -110
[17179764.684000] usb 5-4: device descriptor read/64, error -110
[17179764.900000] usb 5-4: new high speed USB device using ehci_hcd and address 4
[17179768.012000] usb 5-4: device descriptor read/64, error -110
[17179783.228000] usb 5-4: device descriptor read/64, error -110
[17179783.444000] usb 5-4: new high speed USB device using ehci_hcd and address 5
[17179793.852000] usb 5-4: device not accepting address 5, error -110
[17179793.964000] usb 5-4: new high speed USB device using ehci_hcd and address 6
[17179804.372000] usb 5-4: device not accepting address 6, error -110


lsusb:
> Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 046d:c00e Logitech, Inc. M-BJ69 Optical Wheel Mouse
Bus 001 Device 001: ID 0000:0000  

---

### Post by Laki on 2007-01-02
OK, I solved the problem. I needed to repartition it into one partition only, and everything is working fine now. Security partition must be deleted to work.

---

### Post by bingodeville on 2007-07-26
I just wanted to post that this applies to the Patriot USB Flash Drive 1GB as well.

Within Windows XP, I went to Patriot's website ([http://www.patriotmem.com](http://www.patriotmem.com)) and found and downloaded software named "USB Disk Pro, Version 2.65" within the Flash Support section of the manufacturer's website.

I used this utility to repartition my entire flash drive so that the whole device is Unsecured. This corrected me being unable to mount the usb flash drive within Ubuntu 7.04.

Just posting this info to hopefully help the next person with the same problem find the solution quicker through a Google/Yahoo search.

---

