---
title: "weird usb audio player"
date: 2009-04-20
forum: Hardware
---

### Post by lapubell on 2009-04-20
so my buddies wife bought a weird little audio player that is a rip off of an ipod shuffle.  it's totally a knock off, and it looks just like the little clip ones.

anyways, dmesg says this:

melissa@melissa-laptop:~$ dmesg |tail
[39509.520367] sr0: CDROM not ready.  Make sure there is a disc in the drive.
[39860.272073] usb 7-5: new high speed USB device using ehci_hcd and address 11
[39860.423340] usb 7-5: configuration #1 chosen from 1 choice
[39860.454785] scsi11 : SCSI emulation for USB Mass Storage devices
[39860.457835] usb-storage: device found at 11
[39860.457840] usb-storage: waiting for device to settle before scanning
[39865.456213] usb-storage: device scan complete
[39865.457079] scsi 11:0:0:0: Direct-Access     USB 2.0  Boot Loader           PQ: 0 ANSI: 0 CCS
[39865.504096] sd 11:0:0:0: [sdb] Attached SCSI removable disk
[39865.504463] sd 11:0:0:0: Attached scsi generic sg2 type 0



don't think that is of much help.  but anyway, i can't even look at the device, like cfdisk says that the disk isn't readable.

any ideas on what to do to proceed?
I shouldn't have to say that this thing doesn't mount, and isn't recognizable by anything...

---

### Post by iponeverything on 2009-04-21
what does:

```
sudo fdisk -l /dev/sdb
```

give you?

---

### Post by lapubell on 2009-04-22
absolutly nothing.  there is no partition on this thing to list.  it just returns me to my prompt.  i don't even know if linux knows how to read this thing at all.

---

### Post by Godly on 2009-04-22
How's the tech support supplied with the product? LOL....

---

### Post by lapubell on 2009-04-22
ha!  top notch.

---

