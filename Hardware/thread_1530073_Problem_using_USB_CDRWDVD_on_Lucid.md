---
title: "Problem using USB CDRW/DVD on Lucid"
date: 2010-07-13
forum: Hardware
---

### Post by WongFuChu on 2010-07-13
I removed this old atapi DVD/CDRW drive from this old computer and placed it into  this usb enclosure. I'm trying to get it to work with Ubuntu now. I can  mount it if I add an entry in /etc/fstab. However, it does not  automount. Also, I have problems getting audio CDs to work (I know they  work because I just ripped them in FLAC on my windows desktop). Anyone  have any ideas on what to do?

Here's what I get through dmesg | tail
```

[ 7738.900092] usb 1-3: new high speed USB device using ehci_hcd and address 12
[ 7739.033896] usb 1-3: configuration #1 chosen from 1 choice
[ 7739.035099] scsi11 : SCSI emulation for USB Mass Storage devices
[ 7739.035430] usb-storage: device found at 12
[ 7739.035436] usb-storage: waiting for device to settle before scanning
[ 7744.032545] usb-storage: device scan complete
[ 7744.033483] scsi 11:0:0:0: CD-ROM            TOSHIBA  DVD-ROM SD-R2002 1029 PQ: 0 ANSI: 0
[ 7744.045702] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[ 7744.048401] sr 11:0:0:0: Attached scsi CD-ROM sr0
[ 7744.054456] sr 11:0:0:0: Attached scsi generic sg1 type 5

```

---

### Post by WongFuChu on 2010-07-15
bump...

I had to reinstall Ubuntu because I messed up something crucial to the system (don't really know what, but w/e)

Anways, I still can't get it to mount

I'm using:
```
sudo mount /dev/sr0 /cdrom
```

But I end up with:
```

mount: block device /dev/sr0 is write-protected, mounting read-only
mount: you must specify the filesystem type

```

My /etc/fstab contains:
```

#CDROM
/dev/sr0    /cdrom        udf,iso9660    ro,user,noauto     0     0

```

But it never made a difference

I try 
```
dmesg | tail
```
before and after I plug it into a usb port. I keep pressing it so I can get what happens fully.

Before:
```

[  406.924091] usb 1-4: new high speed USB device using ehci_hcd and address 6
[  407.057988] usb 1-4: configuration #1 chosen from 1 choice
[  407.059078] scsi4 : SCSI emulation for USB Mass Storage devices
[  407.059423] usb-storage: device found at 6
[  407.059429] usb-storage: waiting for device to settle before scanning
[  407.059429] usb-storage: waiting for device to settle before scanning
[  412.057417] usb-storage: device scan complete
[  412.058274] scsi 4:0:0:0: CD-ROM            TOSHIBA  DVD-ROM SD-R2002 1029 PQ: 0 ANSI: 0
[  412.068494] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[  412.070648] sr 4:0:0:0: Attached scsi CD-ROM sr0
[  412.074800] sr 4:0:0:0: Attached scsi generic sg1 type 5

```

After:
```

[  436.571228] ILI
[  436.571234] sr 4:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[  436.571250] sr 4:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[  436.571276] end_request: I/O error, dev sr0, sector 0
[  436.573458] sr 4:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  436.573470] sr 4:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[  436.573481] ILI
[  436.573486] sr 4:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[  436.573500] sr 4:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 04 00 00 00 02 00
[  436.573523] end_request: I/O error, dev sr0, sector 4096

```

And the problem remains for each USB port. I have one more left on my laptop that I haven't used yet. Please help!

---

