---
title: "[SOLVED] Cannot mount iAudio MP3 player"
date: 2007-03-09
forum: Hardware &amp; Laptops
---

### Post by Fibonacci on 2007-03-09
Hello,

Just got an iAudio X5 MP3 player, which is supposed to be compatible with GNU/Linux. Granted, when I plugged it in to Knoppix 4.0.2 (kernel 2.6.12) which I was running at the time, it was automagically mounted without a problem; dmesg printed this:
```
usb 4-1: new full speed USB device using uhci_hcd and address 2
scsi2 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 2
usb-storage: waiting for device to settle before scanning
  Vendor: COWON     Model: iAUDIO X5         Rev: 0100
  Type:   Direct-Access                      ANSI SCSI revision: 00
SCSI device sdb: 117210240 512-byte hdwr sectors (60012 MB)
sdb: Write Protect is off
sdb: Mode Sense: 08 00 00 00
sdb: assuming drive cache: write through
SCSI device sdb: 117210240 512-byte hdwr sectors (60012 MB)
sdb: Write Protect is off
sdb: Mode Sense: 08 00 00 00
sdb: assuming drive cache: write through
 sdb: sdb1
Attached scsi removable disk sdb at scsi2, channel 0, id 0, lun 0
usb-storage: device scan complete
```
/var/log/messages appeared to be empty.

Then I rebooted to Ubuntu Edgy (kernel 2.6.17-11-generic), plugged it in, and... couldn't mount it. Not even manually - /dev/sdb didn't even exist. This was the output of dmesg:
```
[17179862.200000] usb 5-7: new high speed USB device using ehci_hcd and address 4
[17179862.400000] usb 5-7: configuration #1 chosen from 1 choice
[17179862.472000] usbcore: registered new driver libusual
[17179862.524000] Initializing USB Mass Storage driver...
[17179862.524000] scsi2 : SCSI emulation for USB Mass Storage devices
[17179862.524000] usb-storage: device found at 4
[17179862.524000] usb-storage: waiting for device to settle before scanning
[17179862.524000] usbcore: registered new driver usb-storage
[17179862.524000] USB Mass Storage support registered.
[17179862.716000] usb 5-7: USB disconnect, address 4
[17179862.956000] usb 5-7: new high speed USB device using ehci_hcd and address 5
```
And this was what I found on /var/log/messages:
```
Mar  9 00:01:55 prower kernel: [17179862.200000] usb 5-7: new high speed USB device using ehci_hcd and address 4
Mar  9 00:01:55 prower kernel: [17179862.400000] usb 5-7: configuration #1 chosen from 1 choice
Mar  9 00:01:55 prower kernel: [17179862.472000] usbcore: registered new driver libusual
Mar  9 00:01:55 prower kernel: [17179862.524000] Initializing USB Mass Storage driver...
Mar  9 00:01:55 prower kernel: [17179862.524000] scsi2 : SCSI emulation for USB Mass Storage devices
Mar  9 00:01:55 prower kernel: [17179862.524000] usbcore: registered new driver usb-storage
Mar  9 00:01:55 prower kernel: [17179862.524000] USB Mass Storage support registered.
Mar  9 00:01:56 prower kernel: [17179862.716000] usb 5-7: USB disconnect, address 4
Mar  9 00:01:56 prower kernel: [17179862.956000] usb 5-7: new high speed USB device using ehci_hcd and address 5
```

Any ideas on what can I do here?

Thanks in advance,

-Fibo

---

### Post by Fibonacci on 2007-03-09
Okay, now I'm getting this from dmesg:
```
[17181097.312000] usb 5-7: new high speed USB device using ehci_hcd and address 4
[17181098.184000] hub 5-0:1.0: Cannot enable port 7.  Maybe the USB cable is bad?
[17181098.296000] usb 5-7: new high speed USB device using ehci_hcd and address 5
[17181099.168000] hub 5-0:1.0: Cannot enable port 7.  Maybe the USB cable is bad?
[17181099.280000] usb 5-7: new high speed USB device using ehci_hcd and address 6
[17181099.688000] usb 5-7: device not accepting address 6, error -71
[17181099.800000] usb 5-7: new high speed USB device using ehci_hcd and address 7
[17181100.208000] usb 5-7: device not accepting address 7, error -71
```

And the iAUDIO says "OK to Disconnect". However, it's still fine on Knoppix.

Any ideas?

Thanks in advance,

-Fibo

---

### Post by Fibonacci on 2007-03-09
I got the same error message on Knoppix 5.1.1 w/ kernel 2.6.19 as I did on Ubuntu Edgy (second message, not first).

Perhaps it's a kernel thing? Anyone has had any luck with iAUDIOs on Ubuntu?

-Fibo

---

### Post by strabes on 2007-03-09
My X5L (when I used to have it) just automagically mounted on edgy. Sorry you're having problems.

---

### Post by Fibonacci on 2007-11-06
The problem I had seems to have been solved by itself with the last upgrade. I suspect it was the kernel upgrade that did it.
I can now read to and write from my iAUDIO, whenever it is connected through the provided sub-pack - connecting it directly works on other OSes, but not in Ubuntu. Not even that did work before, but it does now.

---

