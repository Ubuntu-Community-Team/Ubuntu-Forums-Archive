---
title: "external hard drive not recognised: Buffer I/O error"
date: 2009-12-27
forum: Hardware
---

### Post by BioGeek on 2009-12-27
Hi all,

The external hard drive which contains all my photos and where I backed-up all my important documents is no longer recognised. It is a three month old 500GB  [Iomage Prestige Desktop Hard Drive]("http://go.iomega.com/en/products/external-hard-drive-desktop/prestige-amp-professional-desktop-series/prestige/?partner=4740#overviewItem_tab").

When I plug it in, it is recognised as a USB device, because it shows up when I type `lsusb`, but `dmesg` gives this error message.

```
[19712.013250] usb 2-2: new high speed USB device using ehci_hcd and address 21
[19712.145347] usb 2-2: configuration #1 chosen from 1 choice
[19712.147214] scsi25 : SCSI emulation for USB Mass Storage devices
[19712.147514] usb-storage: device found at 21
[19712.147519] usb-storage: waiting for device to settle before scanning
[19717.148978] usb-storage: device scan complete
[19717.149527] scsi 25:0:0:0: Direct-Access     ST350082 0AS                   PQ: 0 ANSI: 2 CCS
[19717.151020] sd 25:0:0:0: Attached scsi generic sg2 type 0
[19717.151685] sd 25:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[19717.160402] sd 25:0:0:0: [sdb] Write Protect is off
[19717.160412] sd 25:0:0:0: [sdb] Mode Sense: 34 00 00 00
[19717.160418] sd 25:0:0:0: [sdb] Assuming drive cache: write through
[19717.165685] sd 25:0:0:0: [sdb] Assuming drive cache: write through
[19717.165691]  sdb: sdb1
[19719.171808] sd 25:0:0:0: [sdb] Assuming drive cache: write through
[19719.171818] sd 25:0:0:0: [sdb] Attached SCSI disk
[19737.430998] sd 25:0:0:0: [sdb] Unhandled sense code
[19737.431007] sd 25:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[19737.431016] sd 25:0:0:0: [sdb] Sense Key : Medium Error [current] 
[19737.431027] sd 25:0:0:0: [sdb] Add. Sense: Unrecovered read error
[19737.431038] end_request: I/O error, dev sdb, sector 6160463
[19737.431050] Buffer I/O error on device sdb1, logical block 6160400
[19737.431060] Buffer I/O error on device sdb1, logical block 6160401
[19737.431067] Buffer I/O error on device sdb1, logical block 6160402
[19737.431075] Buffer I/O error on device sdb1, logical block 6160403
[19737.431082] Buffer I/O error on device sdb1, logical block 6160404
[19737.431088] Buffer I/O error on device sdb1, logical block 6160405
[19737.431096] Buffer I/O error on device sdb1, logical block 6160406
[19737.431102] Buffer I/O error on device sdb1, logical block 6160407
[19737.431114] Buffer I/O error on device sdb1, logical block 6160408
[19737.431121] Buffer I/O error on device sdb1, logical block 6160409
```

Neither does the external drive show when I use fdisk:

```
jeroen@phalacrocorax:~$ sudo fdisk -l
[sudo] password for jeroen: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000341ad

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18714   150320173+  83  Linux
/dev/sda2           18715       19457     5968147+   5  Extended
/dev/sda5           18715       19457     5968116   82  Linux swap / Solaris
jeroen@phalacrocorax:~$ 

```

I tried the file recovery programs [testdisk/photorec]("http://www.cgsecurity.org/wiki/TestDisk") and [SpinRite]("http://www.grc.com/sr/spinrite.htm"), but both failed because they couldn't recognize the external harddisk.

Do I have any other options?

---

