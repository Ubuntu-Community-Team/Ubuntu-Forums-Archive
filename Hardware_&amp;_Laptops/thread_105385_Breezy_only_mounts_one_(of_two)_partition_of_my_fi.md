---
title: "Breezy only mounts one (of two) partition of my firewire-hdd"
date: 2005-12-18
forum: Hardware &amp; Laptops
---

### Post by tschaboo on 2005-12-18
I'm moving from hoary to breezy and have both installed at the same time. When I boot into hoary and my external firewire-hdd (with 2 partitions) is connected 2 directories get mounted in /media:

```
drwx------  11 tschaboo tschaboo 32768 1970-01-01 01:00 ieee1394disk
drwx------   8 tschaboo tschaboo 32768 1970-01-01 01:00 ieee1394disk-1
```

when i start up breezy there is only the first one. i can't access the 2nd partition.

any idea?

---

### Post by tschaboo on 2005-12-18
now none of the 2 partitions is coming up anymore. that's how it looks like in hoary:

```
Dec 19 02:21:27 localhost kernel: ieee1394: Node added: ID:BUS[0-00:1023]  GUID[0050770e000250f1]
Dec 19 02:21:27 localhost kernel: ieee1394: Host added: ID:BUS[0-01:1023]  GUID[00023c0030009f9b]
Dec 19 02:21:27 localhost kernel: ieee1394: unsolicited response packet received - no tlabel match
Dec 19 02:21:27 localhost kernel: scsi0 : SCSI emulation for IEEE-1394 SBP-2 Devices
Dec 19 02:21:27 localhost kernel: ieee1394: sbp2: Logged into SBP-2 device
Dec 19 02:21:27 localhost kernel: ieee1394: Node 0-00:1023: Max speed [S400] - Max payload [2048]
Dec 19 02:21:27 localhost kernel:   Vendor: ST316002  Model: 1A                Rev:
Dec 19 02:21:27 localhost kernel:   Type:   Direct-Access                      ANSI SCSI revision: 06
Dec 19 02:21:27 localhost kernel: SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
Dec 19 02:21:27 localhost kernel: SCSI device sda: drive cache: write through
Dec 19 02:21:27 localhost kernel: SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
Dec 19 02:21:27 localhost kernel: SCSI device sda: drive cache: write through
**Dec 19 02:21:27 localhost kernel:  /dev/scsi/host0/bus0/target0/lun0: p1 < p5 p6 >**
Dec 19 02:21:27 localhost kernel: Attached scsi disk sda at scsi0, channel 0, id 0, lun 0
```

and that's how it looks like in breezy:
```
Dec 19 02:17:21 localhost kernel: [4294697.908000] ieee1394: Node added: ID:BUS[0-00:1023]  GUID[0050770e000250f1]
Dec 19 02:17:21 localhost kernel: [4294697.915000] ieee1394: Host added: ID:BUS[0-01:1023]  GUID[00023c0030009f9b]
Dec 19 02:17:21 localhost kernel: [4294697.915000] ieee1394: unsolicited response packet received - no tlabel match
Dec 19 02:17:21 localhost kernel: [4294697.915000] scsi0 : SCSI emulation for IEEE-1394 SBP-2 Devices
Dec 19 02:17:21 localhost kernel: [4294699.020000] ieee1394: sbp2: Logged into SBP-2 device
Dec 19 02:17:21 localhost kernel: [4294699.020000] ieee1394: Node 0-00:1023: Max speed [S400] - Max payload [2048]
Dec 19 02:17:21 localhost kernel: [4294699.020000]   Vendor: ST316002  Model: 1A                Rev:
Dec 19 02:17:21 localhost kernel: [4294699.020000]   Type:   Direct-Access                      ANSI SCSI revision: 06
Dec 19 02:17:21 localhost kernel: [4294699.198000] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
Dec 19 02:17:21 localhost kernel: [4294699.199000] SCSI device sda: drive cache: write through
**Dec 19 02:17:21 localhost kernel: [4294699.201000] sda : unsupported sector size 935858176.**
Dec 19 02:17:21 localhost kernel: [4294699.201000] SCSI device sda: 0 512-byte hdwr sectors (0 MB)
Dec 19 02:17:21 localhost kernel: [4294699.201000] SCSI device sda: drive cache: write through
Dec 19 02:17:21 localhost kernel: [4294699.201000] Attached scsi disk sda at scsi0, channel 0, id 0, lun 0

```

any idea?

---

