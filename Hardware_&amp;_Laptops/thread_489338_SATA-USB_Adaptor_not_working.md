---
title: "SATA-USB Adaptor not working"
date: 2007-07-01
forum: Hardware &amp; Laptops
---

### Post by galeron on 2007-07-01
Hi people,

I recently bought a sata->usb adaptor (sata hard disk to usb connector).

However, it did not mount at all.

When I do a "ls /dev", I only see "sdb", instead of "sdb1" as I had expected.

My "dmesg" looks like this:
```
[ 2159.580000] usb 5-1: new high speed USB device using ehci_hcd and address 6
[ 2159.712000] usb 5-1: configuration #1 chosen from 1 choice
[ 2159.712000] scsi4 : SCSI emulation for USB Mass Storage devices
[ 2159.712000] usb-storage: device found at 6
[ 2159.712000] usb-storage: waiting for device to settle before scanning
[ 2164.712000] usb-storage: device scan complete
[ 2164.712000] scsi 4:0:0:0: Direct-Access                                    PQ: 0 ANSI: 2 CCS
[ 2164.712000] sd 4:0:0:0: Attached scsi disk sdb
[ 2164.712000] sd 4:0:0:0: Attached scsi generic sg2 type 0

```

The controller in question is a JMicron USB to ATA/ATAPI Bridge 152D203380B6

Any help is appreciated!

---

### Post by jhf2442 on 2007-07-11
Hi,

did you find a solution to this ? I have the same problem here !

TIA

---

### Post by galeron on 2007-07-15
Hey,

Yeah, it turns out that it was a hardware error after all. The power brick that came with it was DoA.

Hope this helps :)

---

### Post by jhf2442 on 2007-07-15
Hi,

mostly same problem here :-(

Drive seems to be defect (other drive is working fine, I have access to all partitions), it is also not spinning up in an usb enclosure.
However, I heard the motor start the first time I connected the drive to the adapter, so now I'm not sure if the drive simply died (age is 4+), or if I got a power spike through the AC adapter which killed the electronic parts

So for the other people : adapter is fully supported and should be working out of the box !
In cse of problems, a new disk seems to be detected anyway (I tried it by simply plugging the adapter in the USB port, without any drive connected to it), so this says nothing about the HDD !!!

---

