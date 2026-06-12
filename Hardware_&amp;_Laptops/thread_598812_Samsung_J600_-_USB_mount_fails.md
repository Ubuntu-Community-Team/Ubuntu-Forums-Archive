---
title: "Samsung J600 - USB mount fails"
date: 2007-10-31
forum: Hardware &amp; Laptops
---

### Post by Ribs on 2007-10-31
Hi guys,

I'm trying to get a new Samsung J600 phone to connect to my Ubuntu fiesty box. I plug the phone in using a provided USB cable. Ubuntu finds the phone and attempts to mount it:

```
[25275.145407] usb 1-2: new full speed USB device using ohci_hcd and address 3
[25275.369873] usb 1-2: configuration #2 chosen from 1 choice
[25275.464589] rndis_host 1-2:2.1: RNDIS init failed, -110
[25275.464612] rndis_host: probe of 1-2:2.1 failed with error -110
[25275.464671] usb 1-2: device_add(1-2:2.1) --> -110
[25275.466644] cdc_acm 1-2:2.3: ttyACM0: USB ACM device
[25275.478712] scsi7 : SCSI emulation for USB Mass Storage devices
[25275.478811] usb-storage: device found at 3
[25275.478814] usb-storage: waiting for device to settle before scanning
[25280.469808] usb-storage: device scan complete
[25280.477777] scsi 7:0:0:0: Direct-Access     Agere    MMCSD Storage    2.01 PQ: 0 ANSI: 0
[25280.502766] sd 7:0:0:0: Attached scsi removable disk sdb
[25280.502830] sd 7:0:0:0: Attached scsi generic sg2 type 0
```

However, I am unable to mount the phone in the command line. When I go into 'computer' and then double click the newly appeared "Agere MMCSD Storage" icon, I get a error saying "Unable to mount media. There is probably no media in the drive".

This is where I'm stumped. BitPim doesn't work with this phone, and I have no way of moving files to or from the phone now.

Any ideas?

---

### Post by ThrashJazzAssassin on 2007-11-27
Hey Ribs. Have you gotten any further with this?

---

### Post by ThrashJazzAssassin on 2007-11-30
Check this out

[http://samsutools.berlios.de]("http://samsutools.berlios.de")

>  This project develops a set of tools for handling SAMSUNG mobile phones under Linux, FreeBSD, NetBSD and OpenBSD systems.

The tools currently allow you to:

    *
      Transfer photos and videos recorded by your mobile phone camera to your computer.
    *
      Use your mobile phone as an USB disk via a convenient FUSE file system interface.
    *
      Install Java J2ME applications in your mobile phone for free over USB cable.



---

