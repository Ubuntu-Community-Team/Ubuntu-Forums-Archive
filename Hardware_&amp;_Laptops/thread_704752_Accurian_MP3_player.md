---
title: "Accurian MP3 player"
date: 2008-02-22
forum: Hardware &amp; Laptops
---

### Post by eqisow on 2008-02-22
I'm trying to make this Accurian (RadioShack) MP3 player work in Ubuntu. It is connected and showing in lsusb as "Bus 003 Device 007: ID 0aa6:9601 Perception Digital, Ltd". I can mount in manually and browse the file contents, but it doesn't mount automatically for some reason. It also doesn't show as a media device under Amarok, probably becuase it wasn't mounted with hal.

---

### Post by jd_miller on 2008-02-22
I'm having a similar problem with my MP3 player.  It used to auto mount in Edgy, but since I installed Gutsy it doesn't.  I have been able to mount it manually, but this isn't ideal.  After connecting it and running dmesg I see this:
```

usb 3-2: new full speed USB device using uhci_hcd and address 2
usb 3-2: configuration #1 chosen from 1 choice
scsi6 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 2
usb-storage: waiting for device to settle before scanning
usb-storage: device scan complete
scsi 6:0:0:0: Direct-Access     SigmaTel MSCN             0100 PQ: 0 ANSI: 4
sd 6:0:0:0: [sdc] 976512 2048-byte hardware sectors (2000 MB)
sd 6:0:0:0: [sdc] Write Protect is off
sd 6:0:0:0: [sdc] Mode Sense: 3e 00 00 00
sd 6:0:0:0: [sdc] Assuming drive cache: write through
sd 6:0:0:0: [sdc] 976512 2048-byte hardware sectors (2000 MB)
sd 6:0:0:0: [sdc] Write Protect is off
sd 6:0:0:0: [sdc] Mode Sense: 3e 00 00 00
sd 6:0:0:0: [sdc] Assuming drive cache: write through
sdc: sdc1
sd 6:0:0:0: [sdc] Attached SCSI removable disk
sd 6:0:0:0: Attached scsi generic sg3 type 0

```

I have seen this type of problem posted other places, so it seems to be a common problem.

---

