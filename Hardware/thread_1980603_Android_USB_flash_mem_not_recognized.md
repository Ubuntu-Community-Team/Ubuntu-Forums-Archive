---
title: "Android USB flash mem not recognized"
date: 2012-05-15
forum: Hardware
---

### Post by ____22 on 2012-05-15
Since this morning, on my PC, I can't activate the USB on Android, (with the USB cable),

It was working before on my PC, and it's still working on other PC (on ubuntu) so it has something to do with my settings.

I have tried on folder options>edit > preferences  > media, and checked always ask everywhere,

but that's strange, when I activate it from the phone, there is Nothing detected in /media

```

tic@mypc20:~$ tail -f /var/log/messages
May 15 12:56:29 mypc20 kernel: [347816.028435] usb 1-5: USB disconnect, address 42
May 15 13:03:24 mypc20 kernel: [348229.956748] usb 1-5: new high speed USB device using ehci_hcd and address 43
May 15 13:03:24 mypc20 kernel: [348230.089782] usb 1-5: configuration #1 chosen from 1 choice
May 15 13:03:24 mypc20 kernel: [348230.090515] scsi47 : SCSI emulation for USB Mass Storage devices
May 15 13:03:29 mypc20 kernel: [348235.077386] scsi 47:0:0:0: Direct-Access     Android  UMS Composite    0001 PQ: 0 ANSI: 2
May 15 13:03:29 mypc20 kernel: [348235.077829] scsi 47:0:0:1: Direct-Access     Android  UMS Composite    0001 PQ: 0 ANSI: 2
May 15 13:03:29 mypc20 kernel: [348235.078376] sd 47:0:0:0: Attached scsi generic sg3 type 0
May 15 13:03:29 mypc20 kernel: [348235.078511] sd 47:0:0:1: Attached scsi generic sg4 type 0
May 15 13:03:29 mypc20 kernel: [348235.081799] sd 47:0:0:0: [sdc] Attached SCSI removable disk
May 15 13:03:29 mypc20 kernel: [348235.082376] sd 47:0:0:1: [sdd] Attached SCSI removable disk
^C
tic@mypc20:~$ lsusb 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 004: ID 093a:2510 Pixart Imaging, Inc. Hama Optical Mouse
Bus 006 Device 003: ID 03f0:0024 Hewlett-Packard KU-0316 Keyboard
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
tic@mypc20:~$ ls /media/
tic@mypc20:~$

```

---

### Post by ____22 on 2012-05-16
up, 
still not working, this seems a common problem for Ubuntu, those USB undetected

---

