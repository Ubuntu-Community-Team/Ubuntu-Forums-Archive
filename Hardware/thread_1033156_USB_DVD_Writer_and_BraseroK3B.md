---
title: "USB DVD Writer and Brasero/K3B"
date: 2009-01-07
forum: Hardware
---

### Post by anandjm on 2009-01-07
I have been facing problems with burning DVDs on a USB DVD Writer in K3B and Brasero. In the case of K3B, the drive ejects the disk and I observe an USB reset, preventing burning of DVDs. Brasero on the other hand detects blank media but says not enough space on the media (0 Size DVD-R). I have no problems burning with Nautilus' CD/DVD Creator. 

The following is my dmesg when I plug in the USB DVD Writer:

[63182.940086] usb 5-3: new high speed USB device using ehci_hcd and address 6
[63183.074945] usb 5-3: configuration #1 chosen from 1 choice
[63183.076332] scsi4 : SCSI emulation for USB Mass Storage devices
[63183.079454] usb-storage: device found at 6
[63183.079463] usb-storage: waiting for device to settle before scanning
[63188.076477] usb-storage: device scan complete
[63188.077811] scsi 4:0:0:0: CD-ROM            HL-DT-ST DVD-RAM GH22NP20 1.02 PQ: 0 ANSI: 0
[63188.085259] sr1: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[63188.087875] sr 4:0:0:0: Attached scsi CD-ROM sr1
[63188.088239] sr 4:0:0:0: Attached scsi generic sg2 type 5
[63222.417059] cdrom: This disc doesn't have any tracks I recognize!
[63222.439499] end_request: I/O error, dev sr1, sector 0
[63222.439513] Buffer I/O error on device sr1, logical block 0
[63222.442244] end_request: I/O error, dev sr1, sector 0
[63222.442255] Buffer I/O error on device sr1, logical block 0


After inserting a blank media:

[63222.417059] cdrom: This disc doesn't have any tracks I recognize!
[63222.439499] end_request: I/O error, dev sr1, sector 0
[63222.439513] Buffer I/O error on device sr1, logical block 0
[63222.442244] end_request: I/O error, dev sr1, sector 0
[63222.442255] Buffer I/O error on device sr1, logical block 0

When using K3B:

[63397.548043] usb 5-3: reset high speed USB device using ehci_hcd and address 6

---

