---
title: "Pendrive Micro 1GB not working after unmount"
date: 2006-09-22
forum: Hardware &amp; Laptops
---

### Post by MarioFrick on 2006-09-22
Hello! :)
Yesterday I bought a 1GB [Pendrive Micro](http://www.pendrive.com/products/pendrivemicro/), which looked very nice and compatible with linux (reading what was written on the box).

I took it home, plugged to my PC running Dapper and nothing happens. I plugged to the laptop with Xp Home and it worked at once (after the usual hw installation).

I noticed the red light of the pendrive is flashing all the time when I connect it to the PC with Dapper, but it's not recognized. So I reloaded Dapper without unplugging the pendrive and, miracle, the pendrive worked perfectly and I can see 2 partitions of the pendrive (it has a shitty 1.44MB partition with a Windows program to encrypt the data).

The problem is: if I plug it with the OS running it doesn't work. And also when I start the OS with the pendrive plugged, it works, but when  I unmount/unplug it won't work again until I restart the OS again.

It's quite a boring thing, and it's a pity since the pendrive is very nice. Do you have any suggestions about it?

Thank you in advance! :)

---

### Post by MarioFrick on 2006-09-23
No one has any idea?

Right now I'm running Slax live CD and the pendrive keeps on not working, but I get no errors on dmesg

```
usb 1-1: new full speed USB device using uhci_hcd and address 2
usb 1-1: configuration #1 chosen from 1 choice
Initializing USB Mass Storage driver...
scsi2 : SCSI emulation for USB Mass Storage devices
usbcore: registered new driver usb-storage
USB Mass Storage support registered.
usb-storage: device found at 2
usb-storage: waiting for device to settle before scanning
  Vendor:           Model: USB DISK Pro      Rev: PMAP
  Type:   Direct-Access                      ANSI SCSI revision: 00
SCSI device sda: 2004992 512-byte hdwr sectors (1027 MB)
sda: Write Protect is off
sda: Mode Sense: 23 00 00 00
sda: assuming drive cache: write through
SCSI device sda: 2004992 512-byte hdwr sectors (1027 MB)
sda: Write Protect is off
sda: Mode Sense: 23 00 00 00
sda: assuming drive cache: write through
 sda:
```

while with Dapper I had many...

---

### Post by ilowman on 2006-10-04
I have the same pendrive and had the same porblems with Knoppix and Kubuntu. I backed up all the data using winXP (which the drive was working fine in) and reformatted the large partition as FAT32. The drive still didn't work properly so I reformatted the smaller (1.44Mb)partition as FAT. The drive then worked on Kubuntu and Knoppix. 

I think the problem was I had formatted the small partition as a system disk in windows and Linux couldn't recognise it. Also when booting the bios would take up to 2 minutes to recognise the smaller partition on the drive, now it's pretty much instant.

---

