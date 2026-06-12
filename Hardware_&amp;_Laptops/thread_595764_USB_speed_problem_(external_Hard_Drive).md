---
title: "USB speed problem (external Hard Drive)"
date: 2007-10-29
forum: Hardware &amp; Laptops
---

### Post by lordViN on 2007-10-29
copying files from an external USB Hard drive is extremely long, is ridiculous slow,  I think it is not working at USB 2.0 speed, because is very slow and my board supports USB2.0. Reading the forum I found "usbview" but the program is displaying that I'm missing the /proc/bus/usb/devices and that I missing modules. how cant this be? I'm using the Ubuntu server 7.10. the USB is Self powered and is fat32. how can I activate the USB2.0 support?

here is some info:

modules info:

```
 lsmod | grep usb
usb_storage            71744  1 
libusual               17552  1 usb_storage
ide_core              114772  3 usb_storage,ide_cd,via82cxxx
usbcore               136088  5 usb_storage,libusual,ehci_hcd,uhci_hcd
scsi_mod              146828  5 usb_storage,sbp2,sg,sd_mod,libata

```


```
dmesg | grep EHCI
[   29.959250] ehci_hcd 0000:00:10.4: EHCI Host Controller
[   29.959345] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004

```

lsusb

```
 lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 059f:0951 LaCie, Ltd 
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

/var/log/messages

```
Oct 28 20:33:02 Server kernel: [   29.543782] uhci_hcd 0000:00:10.0: UHCI Host Controller
Oct 28 20:33:02 Server kernel: [   29.544213] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
Oct 28 20:33:02 Server kernel: [   29.544249] uhci_hcd 0000:00:10.0: irq 19, io base 0x0000c000
Oct 28 20:33:02 Server kernel: [   29.544436] usb usb1: configuration #1 chosen from 1 choice
Oct 28 20:33:02 Server kernel: [   29.544471] hub 1-0:1.0: USB hub found
Oct 28 20:33:02 Server kernel: [   29.544482] hub 1-0:1.0: 2 ports detected
Oct 28 20:33:02 Server kernel: [   29.647547] ACPI: PCI Interrupt 0000:00:10.1[A] -> GSI 21 (level, low) -> IRQ 19
Oct 28 20:33:02 Server kernel: [   29.647564] uhci_hcd 0000:00:10.1: UHCI Host Controller
Oct 28 20:33:02 Server kernel: [   29.647596] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
Oct 28 20:33:02 Server kernel: [   29.647620] uhci_hcd 0000:00:10.1: irq 19, io base 0x0000c400
Oct 28 20:33:02 Server kernel: [   29.647758] usb usb2: configuration #1 chosen from 1 choice
Oct 28 20:33:02 Server kernel: [   29.647787] hub 2-0:1.0: USB hub found
Oct 28 20:33:02 Server kernel: [   29.647798] hub 2-0:1.0: 2 ports detected
Oct 28 20:33:02 Server kernel: [   29.751294] ACPI: PCI Interrupt 0000:00:10.2[B] -> GSI 21 (level, low) -> IRQ 19
Oct 28 20:33:02 Server kernel: [   29.751306] uhci_hcd 0000:00:10.2: UHCI Host Controller
Oct 28 20:33:02 Server kernel: [   29.751334] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
Oct 28 20:33:02 Server kernel: [   29.751356] uhci_hcd 0000:00:10.2: irq 19, io base 0x0000c800
Oct 28 20:33:02 Server kernel: [   29.751487] usb usb3: configuration #1 chosen from 1 choice
Oct 28 20:33:02 Server kernel: [   29.751520] hub 3-0:1.0: USB hub found
Oct 28 20:33:02 Server kernel: [   29.751531] hub 3-0:1.0: 2 ports detected
Oct 28 20:33:02 Server kernel: [   29.855148] ACPI: PCI Interrupt 0000:00:10.3[B] -> GSI 21 (level, low) -> IRQ 19
Oct 28 20:33:02 Server kernel: [   29.855161] uhci_hcd 0000:00:10.3: UHCI Host Controller
Oct 28 20:33:02 Server kernel: [   29.855188] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
Oct 28 20:33:02 Server kernel: [   29.855213] uhci_hcd 0000:00:10.3: irq 19, io base 0x0000cc00
Oct 28 20:33:02 Server kernel: [   29.855340] usb usb4: configuration #1 chosen from 1 choice
Oct 28 20:33:02 Server kernel: [   29.855369] hub 4-0:1.0: USB hub found
Oct 28 20:33:02 Server kernel: [   29.855380] hub 4-0:1.0: 2 ports detected
Oct 28 20:33:02 Server kernel: [   29.959232] ACPI: PCI Interrupt 0000:00:10.4[C] -> GSI 21 (level, low) -> IRQ 19
Oct 28 20:33:02 Server kernel: [   29.959250] ehci_hcd 0000:00:10.4: EHCI Host Controller
Oct 28 20:33:02 Server kernel: [   29.959283] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
Oct 28 20:33:02 Server kernel: [   29.959338] ehci_hcd 0000:00:10.4: irq 19, io mem 0xdfffbd00
Oct 28 20:33:02 Server kernel: [   29.959345] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Oct 28 20:33:02 Server kernel: [   29.959448] usb usb5: configuration #1 chosen from 1 choice
Oct 28 20:33:02 Server kernel: [   29.959482] hub 5-0:1.0: USB hub found
Oct 28 20:33:02 Server kernel: [   29.959493] hub 5-0:1.0: 8 ports detected

```

```
Oct 28 20:36:40 Server kernel: [  263.303337] usb 3-2: new full speed USB device using uhci_hcd and address 2
Oct 28 20:36:40 Server kernel: [  263.449033] usb 3-2: not running at top speed; connect to a high speed hub
Oct 28 20:36:40 Server kernel: [  263.483102] usb 3-2: configuration #1 chosen from 1 choice
Oct 28 20:36:40 Server kernel: [  263.605577] usbcore: registered new interface driver libusual
Oct 28 20:36:40 Server kernel: [  263.753719] Initializing USB Mass Storage driver...
Oct 28 20:36:40 Server kernel: [  263.758175] scsi2 : SCSI emulation for USB Mass Storage devices
Oct 28 20:36:40 Server kernel: [  263.759226] usbcore: registered new interface driver usb-storage
Oct 28 20:36:40 Server kernel: [  263.759321] USB Mass Storage support registered.
Oct 28 20:36:48 Server kernel: [  271.442600] scsi 2:0:0:0: Direct-Access     SAMSUNG  HD500LJ               PQ: 0 ANSI: 2 CCS
Oct 28 20:36:48 Server kernel: [  271.515422] sd 2:0:0:0: [sdc] 976773168 512-byte hardware sectors (500108 MB)
Oct 28 20:36:48 Server kernel: [  271.518419] sd 2:0:0:0: [sdc] Write Protect is off
Oct 28 20:36:48 Server kernel: [  271.523404] sd 2:0:0:0: [sdc] 976773168 512-byte hardware sectors (500108 MB)
Oct 28 20:36:48 Server kernel: [  271.526400] sd 2:0:0:0: [sdc] Write Protect is off
Oct 28 20:36:48 Server kernel: [  271.526411]  sdc: sdc1
Oct 28 20:36:48 Server kernel: [  271.535483] sd 2:0:0:0: [sdc] Attached SCSI disk
Oct 28 20:36:48 Server kernel: [  271.535535] sd 2:0:0:0: Attached scsi generic sg2 type 0
Oct 28 20:39:29 Server syslogd 1.4.1#21ubuntu3: restart.

```


hdparm (I dont know which one is, sdc or sdc1)

> /dev/sdc:
 Timing cached reads:   586 MB in  2.00 seconds = 292.61 MB/sec
 Timing buffered disk reads:    2 MB in  3.03 seconds = 676.32 kB/sec


> /dev/sdc1:
 Timing cached reads:   590 MB in  2.00 seconds = 294.89 MB/sec
 Timing buffered disk reads:    2 MB in  3.11 seconds = 659.25 kB/sec


---

