---
title: "USB problems"
date: 2007-02-22
forum: Hardware &amp; Laptops
---

### Post by tenchi39 on 2007-02-22
Hi!

My problem is the following:

SD cards in a card reader:

When I try to delete files on an SD card, sometimes the files do not get deleted, sometimes I get read errors. When I try to write to the card, the progress meter finishes way before the actual copy process. When I unmount the device the card reader's led flashes on for some time. The actual content on the card is most of the time incorrect. Some files do not appear, some are corrupted.

HDD in an external USB rack:

When copying from or to the drive, the device (most of the time) gets simply disconnected while the copy process. Unplugging is not enough, I have to power off the rack manually and wait for some time to connect it again or linux doesn't see it at all.

At my workplace it seems to work ok, though it is way slower as it is an old motherboard wirh usb 1.0 or 1.1 only... (1MB/sec max speed)

What is the problem? Please Help me!!!




Hardware: Asrock motherboard, 512MB RAM, Athlon FX 2500+
Software: Kubuntu 6.10 with all updates

---

### Post by rfdeshon on 2007-02-22
How is your card reader connected? Is it USB or builtin? What brand/chipset is it? Have you tried different cards?

Can you please post the output of lsusb with your hard drive enclosure attached?

---

### Post by tenchi39 on 2007-02-22
My HDD is connected through it's cable to the motherboard's usb connector. I also tried a different connector (the one connected to the front of the case) - the results were the same...

lsusb:

Bus 004 Device 006: ID 05e3:0702 Genesys Logic, Inc. USB 2.0 IDE Adapter
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 03f0:0104 Hewlett-Packard DeskJet 880c/970c
Bus 001 Device 005: ID 15d9:0a33  
Bus 001 Device 003: ID 058f:9254 Alcor Micro Corp. Hub
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 04a9:220d Canon, Inc. CanoScan N670U/N676U/LiDE 20
Bus 002 Device 001: ID 0000:0000  

The usb hdd rack is the first line...

I'm pretty sure that nothing is wrong with the card reader or the useb rack as they work well with other machines....

---

### Post by tenchi39 on 2007-02-22
I found this: [http://www.mail-archive.com/linux-usb-users@lists.sourceforge.net/msg15344.html](http://www.mail-archive.com/linux-usb-users@lists.sourceforge.net/msg15344.html)

Seems related...

---

### Post by tenchi39 on 2007-02-22
Just tried to copy, it died at 1.4GB

tail -f /var/log/messages:


Feb 22 22:50:00 kyra kernel: [17188273.532000] EXT3-fs: mounted filesystem with ordered data mode.
Feb 22 22:50:52 kyra kernel: [17188325.148000] usb 4-1: reset high speed USB device using ehci_hcd and address 10
Feb 22 22:51:24 kyra kernel: [17188357.152000] usb 4-1: reset high speed USB device using ehci_hcd and address 10
Feb 22 22:53:31 kyra kernel: [17188484.580000] usb 4-1: reset high speed USB device using ehci_hcd and address 10
Feb 22 22:54:02 kyra kernel: [17188514.876000] usb 4-1: reset high speed USB device using ehci_hcd and address 10
Feb 22 22:54:02 kyra kernel: [17188515.420000] usb 4-1: reset high speed USB device using ehci_hcd and address 10
Feb 22 22:54:03 kyra kernel: [17188515.964000] usb 4-1: reset high speed USB device using ehci_hcd and address 10
Feb 22 22:54:03 kyra kernel: [17188516.484000] usb 4-1: reset high speed USB device using ehci_hcd and address 10
Feb 22 22:54:04 kyra kernel: [17188516.892000] usb 4-1: USB disconnect, address 10
Feb 22 22:54:04 kyra kernel: [17188516.892000] sd 5:0:0:0: scsi: Device offlined - not ready after error recovery
Feb 22 22:54:04 kyra kernel: [17188516.896000] sd 5:0:0:0: SCSI error: return code = 0x10000
Feb 22 22:54:04 kyra kernel: [17188516.896000] end_request: I/O error, dev sda, sector 82375455
Feb 22 22:54:04 kyra kernel: [17188516.896000] lost page write due to I/O error on sda1
Feb 22 22:54:04 kyra kernel: [17188516.896000] sd 5:0:0:0: SCSI error: return code = 0x10000
Feb 22 22:54:04 kyra kernel: [17188516.896000] end_request: I/O error, dev sda, sector 82375519
Feb 22 22:54:04 kyra kernel: [17188516.908000] lost page write due to I/O error on sda1
Feb 22 22:54:04 kyra kernel: [17188517.024000] usb 4-1: new high speed USB device using ehci_hcd and address 11
Feb 22 22:54:04 kyra kernel: [17188517.568000] usb 4-1: new high speed USB device using ehci_hcd and address 12
Feb 22 22:54:05 kyra kernel: [17188518.112000] usb 4-1: new high speed USB device using ehci_hcd and address 13
Feb 22 22:54:05 kyra kernel: [17188518.300000] lost page write due to I/O error on sda1
Feb 22 22:54:05 kyra kernel: [17188518.632000] usb 4-1: new high speed USB device using ehci_hcd and address 14
Feb 22 22:54:19 kyra kernel: [17188531.884000] usb 4-1: new high speed USB device using ehci_hcd and address 15
Feb 22 22:54:19 kyra kernel: [17188532.428000] usb 4-1: new high speed USB device using ehci_hcd and address 16
Feb 22 22:54:20 kyra kernel: [17188532.972000] usb 4-1: new high speed USB device using ehci_hcd and address 17
Feb 22 22:54:20 kyra kernel: [17188533.492000] usb 4-1: new high speed USB device using ehci_hcd and address 18




Before copying, I changed the usb cable to a different one (brand new) and plugged it into a different connector on the motherboard.... (this is why the address of the device changed from 6 to 10)

I don't think that the cable would be the problem :-(

---

### Post by tenchi39 on 2007-02-22
This is the complete log from mount to crash:

tenchi@kyra:~/Desktop$ tail -f /var/log/messages
Feb 22 22:59:34 kyra kernel: [17188846.996000] SCSI device sda: 117231408 512-byte hdwr sectors (60022 MB)
Feb 22 22:59:34 kyra kernel: [17188847.000000] sda: test WP failed, assume Write Enabled
Feb 22 22:59:34 kyra kernel: [17188847.000000]  sda: sda1
Feb 22 22:59:34 kyra kernel: [17188847.012000] sd 6:0:0:0: Attached scsi disk sda
Feb 22 22:59:34 kyra kernel: [17188847.012000] sd 6:0:0:0: Attached scsi generic sg0 type 0
Feb 22 22:59:35 kyra kernel: [17188848.492000] kjournald starting.  Commit interval 5 seconds
Feb 22 22:59:35 kyra kernel: [17188848.492000] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
Feb 22 22:59:35 kyra kernel: [17188848.492000] EXT3 FS on sda1, internal journal
Feb 22 22:59:35 kyra kernel: [17188848.492000] EXT3-fs: recovery complete.
Feb 22 22:59:35 kyra kernel: [17188848.496000] EXT3-fs: mounted filesystem with ordered data mode.
Feb 22 23:03:36 kyra kernel: [17189088.988000] usb 4-1: reset high speed USB device using ehci_hcd and address 19
Feb 22 23:03:36 kyra kernel: [17189089.532000] usb 4-1: reset high speed USB device using ehci_hcd and address 19
Feb 22 23:03:37 kyra kernel: [17189090.076000] usb 4-1: reset high speed USB device using ehci_hcd and address 19
Feb 22 23:03:37 kyra kernel: [17189090.596000] usb 4-1: reset high speed USB device using ehci_hcd and address 19
Feb 22 23:03:38 kyra kernel: [17189091.004000] usb 4-1: USB disconnect, address 19
Feb 22 23:03:38 kyra kernel: [17189091.004000] sd 6:0:0:0: scsi: Device offlined - not ready after error recovery
Feb 22 23:03:38 kyra kernel: [17189091.008000] sd 6:0:0:0: SCSI error: return code = 0x10000
Feb 22 23:03:38 kyra kernel: [17189091.008000] end_request: I/O error, dev sda, sector 82180071
Feb 22 23:03:38 kyra kernel: [17189091.008000] sd 6:0:0:0: SCSI error: return code = 0x10000
Feb 22 23:03:38 kyra kernel: [17189091.008000] end_request: I/O error, dev sda, sector 82180135
Feb 22 23:03:38 kyra kernel: [17189091.008000] lost page write due to I/O error on sda1
Feb 22 23:03:38 kyra kernel: [17189091.008000] lost page write due to I/O error on sda1
Feb 22 23:03:38 kyra kernel: [17189091.120000] usb 4-1: new high speed USB device using ehci_hcd and address 20
Feb 22 23:03:39 kyra kernel: [17189091.664000] usb 4-1: new high speed USB device using ehci_hcd and address 21
Feb 22 23:03:39 kyra kernel: [17189092.208000] usb 4-1: new high speed USB device using ehci_hcd and address 22
Feb 22 23:03:39 kyra kernel: [17189092.256000] lost page write due to I/O error on sda1
Feb 22 23:03:40 kyra kernel: [17189092.728000] usb 4-1: new high speed USB device using ehci_hcd and address 23

---

