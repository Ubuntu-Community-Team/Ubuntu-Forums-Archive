---
title: "USB drive disappears under 8.1 with 2.6.27-11 kernel"
date: 2009-04-12
forum: Hardware
---

### Post by hypatia_atwrk on 2009-04-12
I have a Maxtor One touch external hard drive (powered), formated as ext3, which is my external backup device.  It ran successfully under earlier versions of Ubuntu, through several upgrades until my Mobo/Graphics died.

The new Mobo prompted me to upgrade to 8.04 (yes, I'm a slacker but this is mainly the household server).  This went fine, everything working including external USB drives.  Sadly graphics card sucked and based on forum comments I upgraded onward to 8.1 and 2.6.27.

Graphics now wonderful.  USB drives less so.  The drive which used to pop up happily as sdc /media/Backup no longer registers properly.   I thought it was just an automount problem and that I could manually mount it but the kernel doesn't seem to pick up the table at all (I have tried hotplugging and rebooting with disk plugged in, also using different USB sockets in case of basic issue in new Mobo). 

The disk itself works fine plugged into other machines, other USB drives are similarly no longer recognised.  USB mouse works.

lsusb output:

> hypatia:/var/log$ lsusb
Bus 001 Device 003: ID 1267:0210 Logic3 / SpectraVideo plc 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 006: ID 0d49:7000 Maxtor OneTouch
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


sudo fdisk -l output showing both the internal HDDs:
> hypatia:/var/log$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006e918

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       13054   104856223+  83  Linux
/dev/sda2           13055       13315     2096482+  82  Linux swap / Solaris
/dev/sda3           13316       38913   205615935   83  Linux

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x425e6da0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241   83  Linux


dmesg output at point where drive is plugged in:
> [60155.295562] usb 2-2: USB disconnect, address 3
[62505.200034] usb 2-4: new high speed USB device using ehci_hcd and address 4
[62505.334089] usb 2-4: configuration #1 chosen from 1 choice
[62598.665742] usb 2-4: USB disconnect, address 4
[64100.015582] Too big adjustment 32
[64100.060292] Too big adjustment 32
[64330.320036] usb 2-2: new high speed USB device using ehci_hcd and address 5
[64330.454208] usb 2-2: configuration #1 chosen from 1 choice
[64703.433919] usb 2-2: USB disconnect, address 5
[64744.968034] usb 2-2: new high speed USB device using ehci_hcd and address 6
[64745.102366] usb 2-2: configuration #1 chosen from 1 choice


I can manually recreate /media/Backup but I can't mount the drive as the kernel doesn't seem to recognise it/  "Too big adjustment 32" is a new message to me and googling seems to associate it with sound rather than USB drives.

I've seen some suggestions for modifying the kernel code directly but I would rather find a work around or official patch that muck around with code I don't fully understand.   I haven't cross posted to the upgrade forum as it seems more hardware related but will if recommended.  Any suggestions for workarounds appreciated!

---

