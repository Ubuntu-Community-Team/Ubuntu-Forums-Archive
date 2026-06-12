---
title: "Lifedrive doesn't mount in Ubuntu 9.10"
date: 2010-01-28
forum: Hardware
---

### Post by ezekiel000 on 2010-01-28
I just got a new Lifedrive (my old one died) and I have done a clean install since I last used a Lifedrive with this PC. I can sync the Lifedrive to Ubuntu using gnome-pilot, but when I switch the Lifedrive to drive mode and plug it into to the PC nothing happens the two internal drives aren't mounted (both fat32 and should just act like a usb mass storage device when in drive mode).

I looked in the system logs and found this in messages:
kernel: [ 8934.130028] usb 1-2: new high speed USB device using ehci_hcd and address 3
kernel: [ 8934.285705] usb 1-2: configuration #1 chosen from 1 choice
kernel: [ 8934.286119] scsi10 : SCSI emulation for USB Mass Storage devices
kernel: [ 8934.286257] usb-storage: device found at 3
kernel: [ 8934.286262] usb-storage: waiting for device to settle before scanning
kernel: [ 8939.281751] usb-storage: device scan complete
kernel: [ 8939.406598] scsi 10:0:0:0: Direct-Access     palmOne, File storage     1.0  PQ: 0 ANSI: 0
kernel: [ 8939.886217] scsi 10:0:0:1: Direct-Access     Toshiba  SD02G            1.0  PQ: 0 ANSI: 0
kernel: [ 8939.886757] sd 10:0:0:0: Attached scsi generic sg2 type 0
kernel: [ 8939.886908] sd 10:0:0:1: Attached scsi generic sg3 type 0
kernel: [ 8939.896592] sd 10:0:0:0: [sdb] 7818112 512-byte logical blocks: (4.00 GB/3.72 GiB)
kernel: [ 8939.898533] sd 10:0:0:1: [sdc] 4022272 512-byte logical blocks: (2.05 GB/1.91 GiB)
kernel: [ 8939.899113] sd 10:0:0:0: [sdb] Write Protect is off
kernel: [ 8939.899119] sd 10:0:0:0: [sdb] Mode Sense: 0f 00 00 00
kernel: [ 8939.899123] sd 10:0:0:0: [sdb] Assuming drive cache: write through
kernel: [ 8939.900075] sd 10:0:0:1: [sdc] Write Protect is off
kernel: [ 8939.900083] sd 10:0:0:1: [sdc] Mode Sense: 0f 00 00 00
kernel: [ 8939.900090] sd 10:0:0:1: [sdc] Assuming drive cache: write through
kernel: [ 8939.904337] sd 10:0:0:1: [sdc] Assuming drive cache: write through
kernel: [ 8939.904346]  sdc: sdc1
kernel: [ 8939.908833] sd 10:0:0:0: [sdb] Assuming drive cache: write through
kernel: [ 8939.908842]  sdb: sdb1
kernel: [ 8939.918834] sd 10:0:0:0: [sdb] Assuming drive cache: write through
kernel: [ 8939.918843] sd 10:0:0:0: [sdb] Attached SCSI removable disk
kernel: [ 8939.919582] sd 10:0:0:1: [sdc] Assuming drive cache: write through
kernel: [ 8939.919590] sd 10:0:0:1: [sdc] Attached SCSI removable disk

Which suggests that nothing is wrong but sdb & sdc aren't created in /dev
so I can't even mount them manually. Any ideas?

I'm running Ubuntu 9.10 amd64.

---

