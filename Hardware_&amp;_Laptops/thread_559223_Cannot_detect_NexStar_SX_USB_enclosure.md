---
title: "Cannot detect NexStar SX USB enclosure"
date: 2007-09-24
forum: Hardware &amp; Laptops
---

### Post by dalailama on 2007-09-24
My NexStar SX USB enclosure has a MAXTOR 80GB drive inside.

It is detected and automounted by:
a) Debian Etch
b) Windows XP SP2

However it doesn't work on my Ubuntu Breezy Badger (and windows 2000)
Couple of infos:

a) There is an LED light on the NexStar that stays green when connected to the Debian PC. However on the Ubuntu machine, the LED is flashing red & green.

b) The dmesg output on the debian is: (There is no dmesg output when I plugged it into
    the ubuntu machine)

usb 5-1: new high speed USB device using ehci_hcd and address 4
Initializing USB Mass Storage driver...
scsi2 : SCSI emulation for USB Mass Storage devices
usbcore: registered new driver usb-storage
USB Mass Storage support registered.
usb-storage: device found at 4
usb-storage: waiting for device to settle before scanning
  Vendor: MAXTOR S  Model: T980215A          Rev: 3.AL
  Type:   Direct-Access                      ANSI SCSI revision: 00
SCSI device sdb: 156301488 512-byte hdwr sectors (80026 MB)
sdb: assuming drive cache: write through
SCSI device sdb: 156301488 512-byte hdwr sectors (80026 MB)
sdb: assuming drive cache: write through
 sdb: sdb1
sd 2:0:0:0: Attached scsi disk sdb
usb-storage: device scan complete
FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!

c) My ubuntu machine has no problems automounting small thumbdrives e.g. 
Kingston 2MB thumbdrive.

Thanks

Dalai Lama

---

### Post by rubin on 2008-04-01
I am having the same problem with my NexStar SX 2.5" enclosure. No syslog of any kind when its plugged in. Very odd.

Ubuntu 7.10 / linux 2.6.24-3-generic

---

### Post by paxmark1 on 2008-04-27
any luck getting ext3 or ext2 onto nexstar? Seems to only support fat32. Stumped.  Supposedly the chip is linux.  No new firmware versions.  

I used gparted live-cd to set up, 30 GB fat32 first because documentation implied it needed a fat32 partition at beginning, then 30 gb of ntfs and then 220 gb and 220 gb of ext3 and ext2 respectively.  

I did this via the usb.  I couldn't seem to get and transfers between computer and ext3 partition, but figured that it was some silly thing I was doing, hooked it up to network went into 192.168.1.101 gave it the initial password and it only sees the first 30 bg.  Checked firmware version 46, I can't find anything newer.  It is a royal you know what.  

peace, mark

---

