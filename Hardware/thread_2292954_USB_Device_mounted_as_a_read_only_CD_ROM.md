---
title: "USB Device mounted as a read only CD ROM"
date: 2015-09-01
forum: Hardware
---

### Post by Aaruni on 2015-09-01
I have 2 32 GB USB drives, which I got from some educational institute, with study material on them. I no longer need the study material, and would like to use the USB drive for other storage. But the drives are mounted as a read only CD ROM ( on /dev/sr1 ), and I cannot write onto it, or format it. Please help.

---

### Post by sudodus on 2015-09-01
From what you have told us I can only guess if it is possible with methods available to regular users (like you and me). So I suggest that you try to [wipe the first megabyte with mkusb](https://help.ubuntu.com/community/mkusb#Wipe_the_first_megabyte_or_the_whole_device).

If that does not work, the pendrive is probably made read-only from the beginning. I fear that is the case, and the reason why the drives are mounted as a read only CD ROM (on /dev/sr1) and not mounted as read-write mass storage devices (on /dev/sdx1).

---

### Post by efflandt on 2015-09-02
You might web search "sandisk u2 removal" or "sandisk u3 removal". That appears to have a pseudo-cd that is read-only for its Windows encryption software. So when plugging one of those in they usually show both an sd and sr device. Maybe whatever technique removes U2 or U3 could free up whatever makes your devices appear to be read-only sr devices.

Or maybe you could get a clue from whatever shows up at the tail end of **dmesg** when plugging one in.

---

### Post by Aaruni on 2015-09-03
OK, this is what I get in dmesg.

> 
[ 1130.353894] usb 1-1.2: new high-speed USB device number 4 using ehci-pci
[ 1130.448246] usb 1-1.2: New USB device found, idVendor=090c, idProduct=1000
[ 1130.448253] usb 1-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 1130.448257] usb 1-1.2: Product: TrusCont Publisher USB
[ 1130.448260] usb 1-1.2: Manufacturer: TrusCont
[ 1130.448263] usb 1-1.2: SerialNumber: 000000000016b320
[ 1130.448687] usb-storage 1-1.2:1.0: USB Mass Storage device detected
[ 1130.449144] scsi7 : usb-storage 1-1.2:1.0
[ 1132.143088] scsi 7:0:0:0: CD-ROM            General  USB Flash Disk   1100 PQ: 0 ANSI: 2
[ 1132.144461] sr1: scsi3-mmc drive: 0x/0x caddy
[ 1132.144647] sr 7:0:0:0: Attached scsi CD-ROM sr1
[ 1132.144713] sr 7:0:0:0: Attached scsi generic sg2 type 5



---

### Post by Aaruni on 2015-09-03
> **sudodus said:**
> From what you have told us I can only guess if it is possible with methods available to regular users (like you and me). So I suggest that you try to [wipe the first megabyte with mkusb]("https://help.ubuntu.com/community/mkusb#Wipe_the_first_megabyte_or_the_whole_device").

If that does not work, the pendrive is probably made read-only from the beginning. I fear that is the case, and the reason why the drives are mounted as a read only CD ROM (on /dev/sr1) and not mounted as read-write mass storage devices (on /dev/sdx1).

"mkusb" does not even show the drive as an option.

---

### Post by sudodus on 2015-09-03
I'm sorry, but I know no better method. Maybe efflandt's tips will help you find a method to make the pendrives useful.

---

### Post by Aaruni on 2015-09-03
The link to the software from the official page seems dead ( [http://u3.sandisk.com/launchpadremoval.htm](http://u3.sandisk.com/launchpadremoval.htm) ). :( .

---

