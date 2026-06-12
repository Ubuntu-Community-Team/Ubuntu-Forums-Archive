---
title: "CDRW speed not recgonised"
date: 2006-05-09
forum: Hardware &amp; Laptops
---

### Post by weijie90 on 2006-05-09
Hi,
i have a cdrw (benq crw4824wu) that is connected to a usb 2.0 pci card. when i connect it, dmesg says:

```
usb 1-1: new full speed USB device using uhci_hcd and address 3
[4295687.544000] SCSI subsystem initialized
[4295687.639000] Initializing USB Mass Storage driver...
[4295687.644000] scsi0 : SCSI emulation for USB Mass Storage devices
[4295687.648000] usb-storage: device found at 3
[4295687.648000] usb-storage: waiting for device to settle before scanning[4295687.648000] usbcore: registered new driver usb-storage
[4295687.648000] USB Mass Storage support registered.
[4295692.660000]   Vendor: ATAPI     Model: CD-RW 48X24       Rev: Q.BF
[4295692.660000]   Type:   CD-ROM                             ANSI SCSI revision: 00
[4295692.673000] usb-storage: device scan complete
[4295693.110000] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[4295693.113000] Attached scsi CD-ROM sr0 at scsi0, channel 0, id 0, lun 0[4295693.185000] Attached scsi generic sg0 at scsi0, channel 0, id 0, lun 0,  type 5

```

i think it is working at 4x (usb 1.1?)
how do i solve this problem? thanks!

---

### Post by Sef on 2006-05-09
```
[4295692.660000]   Vendor: ATAPI     Model: CD-RW 48X24       Rev: Q.BF
[4295692.660000]   Type:   CD-ROM                             ANSI SCSI revision: 00
[4295692.673000] usb-storage: device scan complete
[4295693.110000] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[4295693.113000] Attached scsi CD-ROM sr0 at scsi0, channel 0, id 0, lun 0[4295693.185000] Attached scsi generic sg0 at scsi0, channel 0, id 0, lun 0,  type 5
```

It dectects it can run at 48 or at least 24

---

### Post by weijie90 on 2006-05-09
i know this sounds dumb, but i plugged it into the wrong post (a usb 1.1 one)

now theres a new problem: the usb 2.0 pci card isnt working.lspci:

0000:00:00.0 Host bridge: Intel Corp. 82845 845 (Brookdale) Chipset Host Bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. 82845 845 (Brookdale) Chipset AGP Bridge (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 12)
0000:00:1f.0 ISA bridge: Intel Corp. 82801BA ISA Bridge (LPC) (rev 12)
0000:00:1f.1 IDE interface: Intel Corp. 82801BA IDE U100 (rev 12)
0000:00:1f.2 USB Controller: Intel Corp. 82801BA/BAM USB (Hub #1) (rev 12)0000:00:1f.3 SMBus: Intel Corp. 82801BA/BAM SMBus (rev 12)
0000:00:1f.4 USB Controller: Intel Corp. 82801BA/BAM USB (Hub #2) (rev 12)0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801BA/BAM AC'97 Audio (rev 12)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 Pro Ultra TF
0000:02:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

its an ali driver, and i cant find it.

---

