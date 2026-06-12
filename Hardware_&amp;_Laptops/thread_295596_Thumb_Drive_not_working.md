---
title: "Thumb Drive not working"
date: 2006-11-08
forum: Hardware &amp; Laptops
---

### Post by Rever75 on 2006-11-08
Ok,
   I have a 1Gb thumb drive that no longer is usable in either Linux or Windows. I cannot format the thumb drive in Windows and IO have tried gparted and fdisk to create a new partion on this drive. Here is what i am getting......

#dmesg
> [18304281.592000] usb 3-7: new high speed USB device using ehci_hcd and address 15
[18304281.724000] usb 3-7: configuration #1 chosen from 1 choice
[18304281.724000] scsi11 : SCSI emulation for USB Mass Storage devices
[18304281.724000] usb-storage: device found at 15
[18304281.724000] usb-storage: waiting for device to settle before scanning
[18304286.724000] usb-storage: device scan complete
[18304286.728000]   Vendor: LEXAR     Model: JUMPDRIVE PRO     Rev: 0
[18304286.728000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[18304286.744000] SCSI device sdf: 2014992 512-byte hdwr sectors (1032 MB)
[18304286.744000] sdf: Write Protect is off
[18304286.744000] sdf: Mode Sense: 6b 00 00 00
[18304286.744000] sdf: assuming drive cache: write through
[18304286.756000] SCSI device sdf: 2014992 512-byte hdwr sectors (1032 MB)
[18304286.756000] sdf: Write Protect is off
[18304286.756000] sdf: Mode Sense: 6b 00 00 00
[18304286.756000] sdf: assuming drive cache: write through
[18304286.756000]  sdf: unknown partition table
[18304286.760000] sd 11:0:0:0: Attached scsi removable disk sdf
[18304286.760000] sd 11:0:0:0: Attached scsi generic sg5 type 0

#gparted
> ======================
libparted : 1.7.1
automounting disabled
======================
Unable to open /dev/sdf - unrecognised disk label.
Unable to open /dev/sdf - unrecognised disk label.
Unable to open /dev/sdf - unrecognised disk label.
Unable to open /dev/sdf - unrecognised disk label.
Unable to open /dev/sdf - unrecognised disk label.
Unable to open /dev/sdf - unrecognised disk label.
Unable to open /dev/sdf - unrecognised disk label.


Is there anyway to recover this drive and I do not care about the files on it. Any help would be great worse case I will go buy a new one. 

Rich

---

### Post by Merkwurdigliebe on 2006-11-08
You can try this:

sudo dd if=/dev/zero of=/dev/sdf bs=512 count=1000

(count=1 is often enough, but 1000 should kill both boot sectors)

Use this carefully, make **darned** sure that you are pointing at the USB stick and not a good drive.  This will **zero** any VFAT drive.

Then use fdisk to make a new fat32 LBA partition (Type '0xc')

Then use mkfs.vfat -F 32 /dev/sdf1 to make a filesystem.

mkfs.vfat -F 32 -c /dev/sdf1  will check for bad blocks...

---

### Post by Rever75 on 2006-11-09
Merkwurdigliebe worked like a charm I did not even think about using the dd command. Thanks for the help and saving me some dough mate.

---

