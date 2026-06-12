---
title: "Feisty: USB HDD - Recognised, but nothing listed in /dev"
date: 2007-10-09
forum: Hardware &amp; Laptops
---

### Post by benlumley on 2007-10-09
Hello, hoping someone can help.

I've got an old dell latitude that I use as a server for a few things at home. I have an external disk connected to it by USB using the onboard USB, which works fine. However, its a bit slow, so I got a USB 2 PC-CARD (PCMCIA). 

And this is where the problem is - disks plugged into the usb 2 card don't appear in /dev, but are recognised and listed in other places, as per the outputs below.

I know the disk I am trying works with linux - the other system it works fine on is linux (edgy).

Probably easiest if i copy paste some things to show whats going on ...

```

$ lsusb
Bus 004 Device 002: ID 059f:0651 LaCie, Ltd 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 05e3:0702 Genesys Logic, Inc. USB 2.0 IDE Adapter
Bus 001 Device 001: ID 0000:0000  

```

there you can see the disk, the Lacie, Ltd one. The other device is the original disk, connected over the onboard USB1. This works fine.

```

$ ls -l /dev | grep sd
crw-rw-rw- 1 root tty       2,  61 2007-10-09 08:51 ptysd
brw-rw---- 1 root plugdev   8,   0 2007-10-09 08:51 sda
brw-rw---- 1 root plugdev   8,   1 2007-10-09 08:51 sda1
crw-rw-rw- 1 root tty       3,  61 2007-10-09 08:51 ttysd
 
```

here you see there is no device (sda is the existing usb disk).

attached is the listing from lshw - you can see the mass storage device is there twice.

```

$ lsmod | grep usb
usb_storage            72128  3 
libusual               17936  1 usb_storage
scsi_mod              142220  4 sg,sd_mod,usb_storage,libata
usbcore               134536  5 ehci_hcd,usb_storage,libusual,uhci_hcd
```

thats lsmod output .....

and this is the end of dmesg following plugging it in ...

```
[  606.470000] usb 4-3: new high speed USB device using ehci_hcd and address 2
[  606.620000] usb 4-3: configuration #1 chosen from 1 choice
[  606.630000] scsi1 : SCSI emulation for USB Mass Storage devices
[  606.630000] usb-storage: device found at 2
[  606.630000] usb-storage: waiting for device to settle before scanning
[  611.630000] usb-storage: device scan complete
[  611.630000] scsi 1:0:0:0: Direct-Access     SEAGATE  ST3250820A       3.AA PQ: 0 ANSI: 2
[  611.630000] SCSI device sdb: 488397168 512-byte hdwr sectors (250059 MB)
[  611.640000] sdb: Write Protect is off
[  611.640000] sdb: Mode Sense: 53 00 00 08
[  611.640000] sdb: assuming drive cache: write through
[  611.640000] SCSI device sdb: 488397168 512-byte hdwr sectors (250059 MB)
[  611.640000] sdb: Write Protect is off
[  611.640000] sdb: Mode Sense: 53 00 00 08
[  611.640000] sdb: assuming drive cache: write through
[  611.640000]  sdb:
```

i think its supposed to do some more stuff here isn't it? 

Hopefully I've given enough info for someone to help - let me know if anything else is needed!

---

### Post by wonton180 on 2007-10-09
your 250GB drive looks like it was recognized fine.  how about using an old school command like "mount" ?

---

### Post by benlumley on 2007-10-09
> **wonton180 said:**
> your 250GB drive looks like it was recognized fine.  how about using an old school command like "mount" ?

what would i mount?

there is no /dev/sd device for it - i have sda which is the regular disk, i was expecting there to be /dev/sdb and /dev/sdb1, which i'd know how to mount ... can i mount it in some other way?

---

### Post by wonton180 on 2007-10-10
if your /dev/ listing is correct, it's not finding the partition table for some reason.  I would confirm with "fdisk /dev/sdb" and use "p" to print the current table.  that's pretty odd if it doesn't show up--especially if the drive works fine (w/ partitions) on another linux system.

---

### Post by benlumley on 2007-10-16
/dev/sdb didn't exist either, so fdisk gave an error when i tried the command above.

I have re-tested the card in another (windows) laptop, which definitely has all the drivers etc as i used it to test the card when I got it, and it worked fine. It looks like it is faulty, as windows doesn't even acknowledge that anything is plugged in. So that probably explains a lot.

---

