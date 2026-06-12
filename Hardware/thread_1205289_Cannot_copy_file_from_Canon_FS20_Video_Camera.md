---
title: "Cannot copy file from Canon FS20 Video Camera"
date: 2009-07-05
forum: Hardware
---

### Post by Cyclops_ on 2009-07-05
Hey all,

I'm having trouble getting a file from my USB camera to my computer when putting the camera into USB mode.  Granted, it's a large file... but... well, here's what happens.

I plug the thing in to the USB, and the computer recognizes and mounts it.  We get a flurry of information from tail -f /var/log/messages :

```

Jul  5 18:10:01 desktop kernel: [195981.882500] usb 2-2: USB disconnect, address 25
Jul  5 18:10:09 desktop kernel: [195990.200038] usb 2-2: new high speed USB device using ehci_hcd and address 26
Jul  5 18:10:09 desktop kernel: [195990.353334] usb 2-2: configuration #1 chosen from 1 choice
Jul  5 18:10:09 desktop kernel: [195990.355003] scsi18 : SCSI emulation for USB Mass Storage devices
Jul  5 18:10:14 desktop kernel: [195995.355318] scsi 18:0:0:0: Direct-Access     CANON    FS20             1.00 PQ: 0 ANSI: 2
Jul  5 18:10:14 desktop kernel: [195995.357061] scsi 18:0:0:1: Direct-Access     CANON    FS20             1.00 PQ: 0 ANSI: 2
Jul  5 18:10:14 desktop kernel: [195995.364842] sd 18:0:0:0: [sdc] Attached SCSI removable disk
Jul  5 18:10:14 desktop kernel: [195995.364894] sd 18:0:0:0: Attached scsi generic sg2 type 0
Jul  5 18:10:14 desktop kernel: [195995.381552] sd 18:0:0:1: [sdd] 16055296 512-byte hardware sectors: (8.22 GB/7.65 GiB)
Jul  5 18:10:14 desktop kernel: [195995.385671] sd 18:0:0:1: [sdd] Write Protect is off
Jul  5 18:10:14 desktop kernel: [195995.390688] sd 18:0:0:1: [sdd] 16055296 512-byte hardware sectors: (8.22 GB/7.65 GiB)
Jul  5 18:10:14 desktop kernel: [195995.393169] sd 18:0:0:1: [sdd] Write Protect is off
Jul  5 18:10:14 desktop kernel: [195995.393175]  sdd: sdd1
Jul  5 18:10:14 desktop kernel: [195995.396764] sd 18:0:0:1: [sdd] Attached SCSI disk
Jul  5 18:10:14 desktop kernel: [195995.396817] sd 18:0:0:1: Attached scsi generic sg3 type 0

```


A nautilus window pops up, I navigate to the video, and initialize the transfer.  Before even 100 MB is transferred ( sometimes it gets to 50, sometimes more or less ) the transfer acts like it gets put on pause.   In the meantime, as I watch /var/log/messages, I start getting (over and over for a couple of minutes) the following:

```

Jul  5 18:11:13 desktop kernel: [196054.122734] usb 2-2: reset high speed USB device using ehci_hcd and address 26

```

And then the following flurry:

```

Jul  5 18:12:25 desktop kernel: [196125.552045] usb 2-2: reset high speed USB device using ehci_hcd and address 26
Jul  5 18:12:35 desktop kernel: [196135.941288] usb 2-2: reset high speed USB device using ehci_hcd and address 26
Jul  5 18:12:45 desktop kernel: [196146.211294] sd 18:0:0:1: Device offlined - not ready after error recovery
Jul  5 18:12:45 desktop kernel: [196146.211304] sd 18:0:0:1: [sdd] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK,SUGGEST_OK
Jul  5 18:12:45 desktop kernel: [196146.211330] lost page write due to I/O error on sdd1
Jul  5 18:12:45 desktop kernel: [196146.211339] lost page write due to I/O error on sdd1
Jul  5 18:12:45 desktop kernel: [196146.211354] sd 18:0:0:1: [sdd] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Jul  5 18:12:45 desktop kernel: [196146.211394] usb 2-2: USB disconnect, address 26
Jul  5 18:12:45 desktop kernel: [196146.211830] scsi 18:0:0:0: [sdc] READ CAPACITY failed
Jul  5 18:12:45 desktop kernel: [196146.211832] scsi 18:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Jul  5 18:12:45 desktop kernel: [196146.211834] scsi 18:0:0:0: [sdc] Sense not available.
Jul  5 18:12:45 desktop kernel: [196146.211839] scsi 18:0:0:0: [sdc] Write Protect is off
Jul  5 18:12:45 desktop kernel: [196146.211860] scsi 18:0:0:0: [sdc] READ CAPACITY failed
Jul  5 18:12:45 desktop kernel: [196146.211861] scsi 18:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Jul  5 18:12:45 desktop kernel: [196146.211863] scsi 18:0:0:0: [sdc] Sense not available.
Jul  5 18:12:45 desktop kernel: [196146.211867] scsi 18:0:0:0: [sdc] Write Protect is off

```

And then I get a popup saying there was an input/output error, and the file transfer popup disappears .... and then for a few minutes in the tail -f /var/log/messages, the following:

```

Jul  5 18:12:45 desktop kernel: [196146.351713] usb 2-2: new high speed USB device using ehci_hcd and address 27
Jul  5 18:13:16 desktop kernel: [196176.930027] usb 2-2: new high speed USB device using ehci_hcd and address 28
Jul  5 18:13:47 desktop kernel: [196207.510022] usb 2-2: new high speed USB device using ehci_hcd and address 29
Jul  5 18:13:57 desktop kernel: [196217.900044] usb 2-2: new high speed USB device using ehci_hcd and address 30
Jul  5 18:14:08 desktop kernel: [196228.550024] usb 6-2: new full speed USB device using uhci_hcd and address 15
Jul  5 18:14:38 desktop kernel: [196259.130040] usb 6-2: new full speed USB device using uhci_hcd and address 16
Jul  5 18:15:09 desktop kernel: [196289.710028] usb 6-2: new full speed USB device using uhci_hcd and address 17
Jul  5 18:15:19 desktop kernel: [196300.090039] usb 6-2: new full speed USB device using uhci_hcd and address 18

```

....  And nothing happens after that...

Any help or thoughts on this would be very great!

Thanks in advance!!!

---

### Post by Cyclops_ on 2009-07-06
Another piece to the puzzle: I can upload the videos to the laptop (with the same version of Ubuntu).

---

### Post by googlebot5 on 2009-08-31
Hey

Try another cable. I used a 40cm long and thick cable from my old 2.5" ext HDD and it worked fine. Copied everything from the camera.

Apparently camera is very sensitive to cable length and quality.

Cheers

---

