---
title: "External HD, USB works, Firewire doesn't."
date: 2006-10-19
forum: Hardware &amp; Laptops
---

### Post by finalbeta on 2006-10-19
External HD, USB works, Firewire doesn't.

My problem is that I only have USB1.0 on this PC. So I really would like to get firewire to work.
The log below is when I hook the disk up using USB and once using firewire. No idea if this helps.

What can I do to get it to mount using firewire?
> 

Firewire ::
finalbeta@finalbeta-laptop:~$ tail -f -n0 /var/log/messages
Oct 11 00:35:18 finalbeta-laptop kernel: [17180724.748000] scsi2 : SBP-2 IEEE-1394
Oct 11 00:35:18 finalbeta-laptop kernel: [17180725.864000] ieee1394: sbp2: Logged into SBP-2 device
Oct 11 00:35:18 finalbeta-laptop kernel: [17180725.872000]   Vendor: Maxtor 6  Model: L300R0            Rev:     
Oct 11 00:35:18 finalbeta-laptop kernel: [17180725.876000]   Type:   Direct-Access-RBC                  ANSI SCSI revision: 04
Oct 11 00:35:18 finalbeta-laptop kernel: [17180725.904000] SCSI device sda: 586114704 512-byte hdwr sectors (300091 MB)
Oct 11 00:35:18 finalbeta-laptop kernel: [17180725.916000] sda: Write Protect is off
Oct 11 00:35:18 finalbeta-laptop kernel: [17180725.920000] SCSI device sda: drive cache: write back
Oct 11 00:35:18 finalbeta-laptop kernel: [17180725.920000] SCSI device sda: 586114704 512-byte hdwr sectors (300091 MB)
Oct 11 00:35:18 finalbeta-laptop kernel: [17180725.920000] sda: Write Protect is off
Oct 11 00:35:18 finalbeta-laptop kernel: [17180725.920000] SCSI device sda: drive cache: write back
Oct 11 00:35:18 finalbeta-laptop kernel: [17180725.920000]  sda: sda1 < sda5 >
Oct 11 00:35:18 finalbeta-laptop kernel: [17180725.952000] sd 2:0:0:0: Attached scsi disk sda
Oct 11 00:35:18 finalbeta-laptop kernel: [17180725.952000] sd 2:0:0:0: Attached scsi generic sg0 type 14
Oct 11 00:35:47 finalbeta-laptop kernel: [17180757.768000] sd 2:0:0:0: 
Oct 11 00:35:47 finalbeta-laptop kernel: [17180757.768000]         command: Read (10): 28 00 22 ef 66 00 00 00 08 00
Oct 11 00:35:57 finalbeta-laptop kernel: [17180767.768000] sd 2:0:0:0: 
Oct 11 00:35:57 finalbeta-laptop kernel: [17180767.768000]         command: Test Unit Ready: 00 00 00 00 00 00
Oct 11 00:36:08 finalbeta-laptop kernel: [17180777.768000] sd 2:0:0:0: 
Oct 11 00:36:08 finalbeta-laptop kernel: [17180777.768000]         command: Test Unit Ready: 00 00 00 00 00 00
Oct 11 00:36:08 finalbeta-laptop kernel: [17180777.768000] sd 2:0:0:0: scsi: Device offlined - not ready after error recovery
Oct 11 00:36:08 finalbeta-laptop kernel: [17180777.768000] sd 2:0:0:0: SCSI error: return code = 0x50000
Oct 11 00:36:08 finalbeta-laptop kernel: [17180777.768000] end_request: I/O error, dev sda, sector 586114560
Oct 11 00:36:08 finalbeta-laptop kernel: [17180777.768000] printk: 63 messages suppressed.

USB:

Oct 11 00:42:30 finalbeta-laptop kernel: [17181160.880000] usb 2-1: new full speed USB device using uhci_hcd and address 2
Oct 11 00:42:33 finalbeta-laptop kernel: [17181161.044000] usb 2-1: configuration #1 chosen from 1 choice
Oct 11 00:42:36 finalbeta-laptop kernel: [17181163.868000] usbcore: registered new driver libusual
Oct 11 00:42:36 finalbeta-laptop kernel: [17181165.556000] Initializing USB Mass Storage driver...
Oct 11 00:42:36 finalbeta-laptop kernel: [17181165.556000] scsi3 : SCSI emulation for USB Mass Storage devices
Oct 11 00:42:36 finalbeta-laptop kernel: [17181165.556000] usbcore: registered new driver usb-storage
Oct 11 00:42:36 finalbeta-laptop kernel: [17181165.556000] USB Mass Storage support registered.
Oct 11 00:42:40 finalbeta-laptop kernel: [17181170.560000]   Vendor: Maxtor 6  Model: L300R0            Rev:  0 0
Oct 11 00:42:40 finalbeta-laptop kernel: [17181170.560000]   Type:   Direct-Access                      ANSI SCSI revision: 00
Oct 11 00:42:40 finalbeta-laptop kernel: [17181170.588000] SCSI device sda: 586114704 512-byte hdwr sectors (300091 MB)
Oct 11 00:42:40 finalbeta-laptop kernel: [17181170.592000] sda: Write Protect is off
Oct 11 00:42:40 finalbeta-laptop kernel: [17181170.600000] SCSI device sda: 586114704 512-byte hdwr sectors (300091 MB)
Oct 11 00:42:40 finalbeta-laptop kernel: [17181170.604000] sda: Write Protect is off
Oct 11 00:42:40 finalbeta-laptop kernel: [17181170.604000]  sda: sda1 < sda5 >
Oct 11 00:42:40 finalbeta-laptop kernel: [17181170.656000] sd 3:0:0:0: Attached scsi disk sda
Oct 11 00:42:40 finalbeta-laptop kernel: [17181170.656000] sd 3:0:0:0: Attached scsi generic sg0 type 0
Oct 11 00:42:50 finalbeta-laptop kernel: [17181180.648000] kjournald starting.  Commit interval 5 seconds
Oct 11 00:42:50 finalbeta-laptop kernel: [17181180.704000] EXT3 FS on sda5, internal journal
Oct 11 00:42:50 finalbeta-laptop kernel: [17181180.704000] EXT3-fs: mounted filesystem with ordered data mode.


---

### Post by finalbeta on 2006-11-15
What information do I need to post this as a bug? What package should it be filed against?

---

