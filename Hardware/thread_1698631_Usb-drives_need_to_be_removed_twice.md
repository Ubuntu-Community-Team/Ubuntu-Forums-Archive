---
title: "Usb-drives need to be removed twice"
date: 2011-03-02
forum: Hardware
---

### Post by XaRP1Sh87g on 2011-03-02
Hi!?

I'm having a problem with 10.10 atm.
When I connect an usb-disk and choose to 'safely remove' it, the disk will power down but immediately power back on again. Removing it again will power the disk down for good.
I've tried this with 2 very different usb-disks. A modern 1.5TB WD-external drive and an ageing 20GB laptop hdd built into a cheap casing - same results.
Also, I've disabled auto mounting of any filesystems on the disks and I've tried removing when a FS is mounted and when it is not - no difference.
This only happens with ubuntu, other distros work fine, also MS-windows and MacOsX(its a macbook pro 7.1) have no problems with the disks.

I've checked syslog, but apart from the normal stuff there's nothing to be found there, marked the spot where disconnect occurs: 

```
 [34746.050270] usb 1-1: new high speed USB device using ehci_hcd and address 6
 [34746.206072] scsi9 : usb-storage 1-1:1.0
 [34747.202844] scsi 9:0:0:0: Direct-Access     Initio   DK23DA-20        1.06 PQ: 0 ANSI: 0
 [34747.204391] sd 9:0:0:0: Attached scsi generic sg3 type 0
 [34747.205808] sd 9:0:0:0: [sdc] 39070080 512-byte logical blocks: (20.0 GB/18.6 GiB)
 [34747.206831] sd 9:0:0:0: [sdc] Write Protect is off
 [34747.206841] sd 9:0:0:0: [sdc] Mode Sense: 23 00 00 00
 [34747.206848] sd 9:0:0:0: [sdc] Assuming drive cache: write through
 [34747.212296] sd 9:0:0:0: [sdc] Assuming drive cache: write through
 [34747.212313]  sdc: sdc1
 [34747.233638] sd 9:0:0:0: [sdc] Assuming drive cache: write through
 [34747.233650] sd 9:0:0:0: [sdc] Attached SCSI disk
** [34826.780287] usb 1-1: USB disconnect, address 6**
** [34827.200136] usb 3-1: new full speed USB device using ohci_hcd and address 5**
 [34827.415200] usb 3-1: not running at top speed; connect to a high speed hub
 [34827.436440] scsi10 : usb-storage 3-1:1.0
 [34828.439302] scsi 10:0:0:0: Direct-Access     Initio   DK23DA-20        1.06 PQ: 0 ANSI: 0
 [34828.440710] sd 10:0:0:0: Attached scsi generic sg3 type 0
 [34828.453208] sd 10:0:0:0: [sdc] 39070080 512-byte logical blocks: (20.0 GB/18.6 GiB)
 [34828.460190] sd 10:0:0:0: [sdc] Write Protect is off
 [34828.460202] sd 10:0:0:0: [sdc] Mode Sense: 23 00 00 00
 [34828.460208] sd 10:0:0:0: [sdc] Assuming drive cache: write through
 [34828.478166] sd 10:0:0:0: [sdc] Assuming drive cache: write through
 [34828.478187]  sdc: sdc1
 [34829.976174] sd 10:0:0:0: [sdc] Assuming drive cache: write through
 [34829.976188] sd 10:0:0:0: [sdc] Attached SCSI disk
```

Any ideas?

---

### Post by XaRP1Sh87g on 2011-03-03
UPDATE:

This also happens with usb-sticks.

Anyone else having such troubles?

---

