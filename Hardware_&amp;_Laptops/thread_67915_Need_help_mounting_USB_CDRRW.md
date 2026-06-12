---
title: "Need help mounting USB CDR/RW"
date: 2005-09-21
forum: Hardware &amp; Laptops
---

### Post by vinoloco on 2005-09-21
Hi all,

I know this is a beginner question so please bear with me or point me to a FAQ where it has been discussed before (couldn't find one yet..)

I have a USB CD burner and I'm attempting to mount it to my system.  I know the OS sees the device:

# lsusb
Bus 001 Device 003:  ID 0c0b:b001 Dura Micro, Inc. (Acomdata)

Now I suppose that I need to modify /etc/fstab and and mount the drive.

Can anybody help me with the syntax of the fstab entry?

Thanks in advance for the help.

   -- vino

---

### Post by banadushi on 2005-09-21
Run `dmesg` from a terminal.  Down near the bottom you will see something along the lines of:
```

usb 4-3: USB disconnect, address 2
usb 4-3: new high speed USB device using ehci_hcd and address 5
scsi4 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 5
usb-storage: waiting for device to settle before scanning
  Vendor: HP        Model: DVD Writer 640v   Rev: EOU5
  Type:   CD-ROM                             ANSI SCSI revision: 00
sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
Attached scsi CD-ROM sr0 at scsi4, channel 0, id 0, lun 0
Attached scsi generic sg0 at scsi4, channel 0, id 0, lun 0,  type 5
usb-storage: device scan complete

```

The important line is:
```

Attached scsi CD-ROM sr0 at scsi4, channel 0, id 0, lun 0

```

So in my case it is being seen as sr0, so an fstab entry would be:
```

/dev/sr0       /mnt/cdrom   udf,iso9660 ro,user,noauto  0       0

```

Have a good one!

Jason

---

