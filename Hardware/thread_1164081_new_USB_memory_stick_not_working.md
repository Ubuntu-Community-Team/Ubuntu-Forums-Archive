---
title: "new USB memory stick not working"
date: 2009-05-19
forum: Hardware
---

### Post by Nathan_M on 2009-05-19
Hi,
I just bought a cheap little DV camera which functions like a USB memory stick. I plugged it into a Windows computer at work, and it worked fine (I could get video files from it like a normal USB memory stick), but when I plug it into my Intrepid laptop, it's not recognised. When it's plugged in, an option comes up under the Places menu: "USB Drive" and the tooltip says "Rescan USB Drive".

I plug in the device, then run lsusb:

$ lsusb
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Same as if it wasn't plugged in. Then I click this mystery rescan option and run lsusb again:

~$ lsusb
Bus 005 Device 014: ID 115e:0003  
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Just this one extra option. Any idea how I can get this thing working?

---

### Post by Dark_Stang on 2009-05-19
What type of camera is it?

---

### Post by sedawk on 2009-05-19
Before connecting the USB device do a
```
sudo dmesg -c
```
to clear the message buffer.
Then connect the device, wait 10 seconds and
run
dmesg

The output normally says that a new mass storage was detected and
that it now is drive sdX and has partitions sdX1,sdX2, ...

What is your dmesg output?

---

### Post by Nathan_M on 2009-05-19
> **sedawk said:**
> What is your dmesg output?

Thanks for the reply. I tried that, and it still hasn't recognised the device as it usually does. Here's my dmesg output after the device was connected. Here's my dmesg output:

```
$ dmesg
[ 6800.957049] usb 5-5: new high speed USB device using ehci_hcd and address 18
[ 6801.069043] usb 5-5: device descriptor read/64, error -71
[ 6801.284359] usb 5-5: device descriptor read/64, error -71
[ 6801.501052] usb 5-5: new high speed USB device using ehci_hcd and address 19
[ 6806.645238] usb 5-5: configuration #1 chosen from 1 choice
[ 6806.684165] scsi10 : SCSI emulation for USB Mass Storage devices
[ 6806.696059] usb-storage: device found at 19
[ 6806.696066] usb-storage: waiting for device to settle before scanning
[ 6811.700258] usb-storage: device scan complete
[ 6811.701020] scsi 10:0:0:0: Direct-Access     mini     DV           OPN      PQ: 0 ANSI: 2
[ 6811.748522] sd 10:0:0:0: [sdb] 1009536 4096-byte hardware sectors (4135 MB)
[ 6811.749346] sd 10:0:0:0: [sdb] Write Protect is off
[ 6811.749356] sd 10:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[ 6811.749361] sd 10:0:0:0: [sdb] Assuming drive cache: write through
[ 6811.751527] sd 10:0:0:0: [sdb] 1009536 4096-byte hardware sectors (4135 MB)
[ 6811.752471] sd 10:0:0:0: [sdb] Write Protect is off
[ 6811.752481] sd 10:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[ 6811.752486] sd 10:0:0:0: [sdb] Assuming drive cache: write through
[ 6811.752500]  sdb: unknown partition table
[ 6811.763808] sd 10:0:0:0: [sdb] Attached SCSI removable disk
[ 6811.763979] sd 10:0:0:0: Attached scsi generic sg2 type 0
```

---

### Post by Nathan_M on 2009-05-19
> **Dark_Stang said:**
> What type of camera is it?
Oh, didn't see this the first time. It's just a miniature low-res "MP9" camera that I want to use for mounting on some remote controlled stuff. It uses a codec that VLC can read (in an AVI container), and stores the videos on the flash memory.

---

### Post by Nathan_M on 2009-05-19
After a bit of fishing around, I've found that it is /dev/sdb, so I can mount it from there. Does anyone know how I can do this automatically like any other drive in fstab, with the correct permissions and stuff? If I try to use pmount, it gives "Error: device /dev/sdb is not removable".

---

### Post by sedawk on 2009-05-20
Okay ... as you can see from the dmesg output your device does not
have a partition table. 
So your device doesn't look like a USB-HDD, but a USB-Floppy or
USB-Superfloppy (because it is bigger than a floppy).
(Older computers sometimes required USB-sticks to be formatted as
 "superfloppy" because they could boot from USB-floppy but not
 from USB-HDD).

I'm not sure why your device is not mounted as USB-(super)floppy out
of the box - haven't tried any USB-floppy lately ...
Try to find out about mounting USB-floppies (or troubleshooting those).
I wonder if this is a case where "udev" hacking is needed!
(E.g. forcing the system to believe that the device with ID=...and
 VENDOR=... is a USB-floppy).

---

### Post by Nathan_M on 2009-05-20
> **sedawk said:**
> Okay ... as you can see from the dmesg output your device does not
have a partition table. 
So your device doesn't look like a USB-HDD, but a USB-Floppy or
USB-Superfloppy (because it is bigger than a floppy).
(Older computers sometimes required USB-sticks to be formatted as
 "superfloppy" because they could boot from USB-floppy but not
 from USB-HDD).

I'm not sure why your device is not mounted as USB-(super)floppy out
of the box - haven't tried any USB-floppy lately ...
Try to find out about mounting USB-floppies (or troubleshooting those).
I wonder if this is a case where "udev" hacking is needed!
(E.g. forcing the system to believe that the device with ID=...and
 VENDOR=... is a USB-floppy).

I see. That explains why it's /dev/sdb and not /dev/sdb1. I knew there was something unusual about that, but couldn't quite add it together. I'm at work at the moment, so can't try it, but I presume a modification of this will work: [http://ubuntuforums.org/archive/index.php/t-3687.html](http://ubuntuforums.org/archive/index.php/t-3687.html).

---

