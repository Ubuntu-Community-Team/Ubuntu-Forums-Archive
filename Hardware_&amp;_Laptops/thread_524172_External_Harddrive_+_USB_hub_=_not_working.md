---
title: "External Harddrive + USB hub = not working"
date: 2007-08-12
forum: Hardware &amp; Laptops
---

### Post by nulall on 2007-08-12
I feel like I'm missing something obvious here, but I'm still a bit unexperienced with doing much in terms of system diagnostics on ubuntu, so maybe someone can guide me through this...
Basically, my problem is that my external hard drive works perfectly fine when connected (USB 2.0) directly to my computer. My USB hub (Belkin Tunesync) works perfectly fine when connected to my computer and when other devices are connected through it (USB 2.0), and works fine when my iPod is docked on it.
The external has it's own power source and the Tunesync has a powersource (and both are plugged in). I've tried swapping around the USB cord to different ports on the Tunesync and still can't get anything to happen. Also, worth noting, the system won't recognize the USB drive as mounted or even unmounted (doesn't show up in the Computer section), but when I unplugged it once to switch ports, it gave me an unsafe removal error (at least, I think that the message was in response to that).
Any advice?

Thanks,
Neil


PS. I'm running Ubuntu Feisty, with NTFS write support (installed via automatix) and the USB drive is NTFS.

---

### Post by nulall on 2007-08-17
update:

the drive had originally been working when directly connected to the computer, and would not when connected to the usb port. i had tried switching between them several times with the same results repeated. but now, the drive is not even recognized when connected directly to the computer (but it's still recognized fine by my windows system).

please, does *anyone *have any idea what i can do?

---

### Post by Psyklops on 2007-08-17
In a terminal session type sudo tail -f /var/log/messages and leave the window open.

Plug in/turn on your USB drive/hub combo and see what comes up.
You should get something that looks like this:
```

[14319.136000] usb 2-2: new high speed USB device using ehci_hcd and address 6
[14319.268000] usb 2-2: configuration #1 chosen from 1 choice
[14319.268000] hub 2-2:1.0: USB hub found
[14319.272000] hub 2-2:1.0: 4 ports detected
[14326.540000] usb 2-2.4: new high speed USB device using ehci_hcd and address 7
[14326.648000] usb 2-2.4: configuration #1 chosen from 1 choice
[14326.648000] scsi5 : SCSI emulation for USB Mass Storage devices
[14331.648000] scsi 5:0:0:0: Direct-Access     Initio   ST3320620AS      4.36 PQ: 0 ANSI: 0
[14331.656000] SCSI device sdb: 625142448 512-byte hdwr sectors (320073 MB)
[14331.656000] sdb: Write Protect is off
[14331.660000] SCSI device sdb: 625142448 512-byte hdwr sectors (320073 MB)
[14331.660000] sdb: Write Protect is off
[14331.660000]  sdb: sdb1
[14331.672000] sd 5:0:0:0: Attached scsi disk sdb
[14331.672000] sd 5:0:0:0: Attached scsi generic sg1 type 0

```

---

