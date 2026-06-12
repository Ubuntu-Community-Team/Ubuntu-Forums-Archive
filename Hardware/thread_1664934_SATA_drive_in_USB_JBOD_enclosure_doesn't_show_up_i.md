---
title: "SATA drive in USB JBOD enclosure doesn't show up in /dev"
date: 2011-01-11
forum: Hardware
---

### Post by Gabi Imre on 2011-01-11
I put together a NAS-like device using a 2-slot USB JBOD enclosure and an eBox-3300. I'm using Ubuntu Server 8.04 Hardy as an OS for the eBox. I have two WD EARS drives hat I intend to use in the USB enclosure, one 1TB large, the other 2TB. I managed to install Hardy on the 1TB drive and boot from it. The 2TB drive is preformatted XFS.

My problem is this:
If I add the 2TB drive in the enclosure, it does not show up in /dev in ubuntu. In the device's BIOS, both drives appear just fine with correct IDs, so I'm guessing the problem is with ubuntu.

Any help would be greatly appreciated.

---

### Post by Manyette on 2011-01-11
Does the other (2Tb) drive appear in /media perhaps?

---

### Post by Gabi Imre on 2011-01-11
> **Manyette said:**
> Does the other (2Tb) drive appear in /media perhaps?

Uhm, no, /media only has a cdrom0 which is empty.

---

### Post by Manyette on 2011-01-11
Have you checked System->Administration->Disk Utility to see if it listed there?  I don't have any other ideas, but perhaps someone more knowledgeable will chime in.

---

### Post by Gabi Imre on 2011-01-11
> **Manyette said:**
> Have you checked System->Administration->Disk Utility to see if it listed there?  I don't have any other ideas, but perhaps someone more knowledgeable will chime in.

The system is a command line only install, fdisk -l reports only the first drive on /sda

```
Disk /dev/hdc: 512 MB, 512483328 bytes
255 heads, 63 sectors/track, 62 cylinders, total 1000944 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb031cd4d

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *          63      996029      497983+   6  FAT16

Disk /dev/sda: 1000.2 GB, 1000203804160 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953523055 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00029355

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     7342079     3670016   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2         7342080     8390655      524288   82  Linux swap / Solaris
Partition 2 does not end on cylinder boundary.
/dev/sda3         8390656  1953523054   972566199+  83  Linux
Partition 3 does not end on cylinder boundary.
dev@nasu:/$

```

The 512MB ide device is a built-in flash card.

---

### Post by psusi on 2011-01-11
What do you mean "*the device's* BIOS"?

Also USB enclosures are not very good.  The throughput of USB is limited, and you can't do things like SMART diagnostics on the drive.  Also USB breaks connection with the disk when you suspend, as if you had yanked it without choosing to safely remove it.  Go with an eSATA enclosure instead.

---

### Post by Gabi Imre on 2011-01-11
> **psusi said:**
> What do you mean "*the device's* BIOS"?

Also USB enclosures are not very good.  The throughput of USB is limited, and you can't do things like SMART diagnostics on the drive.  Also USB breaks connection with the disk when you suspend, as if you had yanked it without choosing to safely remove it.  Go with an eSATA enclosure instead.

Ok, let me answer some of your questions:

About the BIOS, I meant the eBox-3300's BIOS reports both HDD's properly.

SMART diagnostics are working for the 1TB drive, with smartmontools and smartctl -d sat.

Unfortunately, the eBox-3300 doesn't have eSATA support, so I had to go with an USB enclosure instead.

Gabriel.

---

### Post by Gabi Imre on 2011-01-12
As a bump, dmesg report regarding usb:

```

[    6.436689] usbcore: registered new interface driver usbfs
[    6.436872] usbcore: registered new interface driver hub
[    6.437094] usbcore: registered new device driver usb
[    6.459581] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    6.486520] ohci_hcd 0000:00:0a.0: OHCI Host Controller
[    6.486862] ohci_hcd 0000:00:0a.0: new USB bus registered, assigned bus number 1
[    6.486978] ohci_hcd 0000:00:0a.0: irq 15, io mem 0xfefb9000
[    6.489590] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    6.489615] Warning! ehci_hcd should always be loaded before uhci_hcd and ohci_hcd, not after
[    6.569726] usb usb1: configuration #1 chosen from 1 choice
[    6.570010] hub 1-0:1.0: USB hub found
[    6.570085] hub 1-0:1.0: 2 ports detected
[    6.571174] ehci_hcd 0000:00:0a.1: EHCI Host Controller
[    6.571359] ehci_hcd 0000:00:0a.1: new USB bus registered, assigned bus number 2
[    6.591827] ehci_hcd 0000:00:0a.1: irq 9, io mem 0xfefbb800
[    6.597783] ehci_hcd 0000:00:0a.1: USB 2.0 started, EHCI 1.00
[    6.598564] usb usb2: configuration #1 chosen from 1 choice
[    6.598850] hub 2-0:1.0: USB hub found
[    6.598927] hub 2-0:1.0: 2 ports detected
[    6.599880] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[    6.600093] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 3
[    6.600204] ohci_hcd 0000:00:0b.0: irq 10, io mem 0xfefba000
[    6.681569] usb usb3: configuration #1 chosen from 1 choice
[    6.681849] hub 3-0:1.0: USB hub found
[    6.681927] hub 3-0:1.0: 2 ports detected
[    6.682919] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[    6.683107] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 4
[    6.703789] ehci_hcd 0000:00:0b.1: irq 11, io mem 0xfefbbc00
[    6.709737] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00
[    6.710521] usb usb4: configuration #1 chosen from 1 choice
[    6.710797] hub 4-0:1.0: USB hub found
[    6.710867] hub 4-0:1.0: 2 ports detected
[    7.117625] usb 1-2: new full speed USB device using ohci_hcd and address 2
[    7.254411] usb 1-2: configuration #1 chosen from 1 choice
[    7.358565] usb 4-1: new high speed USB device using ehci_hcd and address 2
[    7.475627] usb 4-1: configuration #1 chosen from 1 choice
[    9.055042] input: C-Media USB Audio Device    as /devices/pci0000:00/0000:00:0a.0/usb1/1-2/1-2:1.3/input/input2
[    9.055146] generic-usb 0003:0D8C:0008.0001: input: USB HID v1.00 Device [C-Media USB Audio Device   ] on usb-0000:00:0a.0-2/input3
[    9.055294] usbcore: registered new interface driver usbhid
[    9.055327] usbhid: v2.6:USB HID core driver
[    9.066967] Initializing USB Mass Storage driver...
[    9.071497] scsi0 : SCSI emulation for USB Mass Storage devices
[    9.072280] usbcore: registered new interface driver usb-storage
[    9.072317] USB Mass Storage support registered.
[    9.085196] usb-storage: device found at 2
[    9.085226] usb-storage: waiting for device to settle before scanning
[   14.084448] scsi 0:0:0:0: Direct-Access     WDC WD10 EARS-00Y5B1           PQ: 0 ANSI: 2 CCS
[   14.086389] usb-storage: device scan complete
[   14.120377] sd 0:0:0:0: [sda] 1953523055 512-byte hardware sectors: (1.00 TB/931 GiB)
[   14.121729] sd 0:0:0:0: [sda] Write Protect is off
[   14.121765] sd 0:0:0:0: [sda] Mode Sense: 00 38 00 00
[   14.121793] sd 0:0:0:0: [sda] Assuming drive cache: write through
[   14.124359] sd 0:0:0:0: [sda] Assuming drive cache: write through
[   14.124464]  sda: sda1 sda2 sda3
[   14.126487] sd 0:0:0:0: [sda] Attached SCSI disk


```

---

### Post by Gabi Imre on 2011-01-12
Bump.

The enclosure works with both HDDs attached in Win 7 and Ubuntu 10.10. Please, any ideas?

---

